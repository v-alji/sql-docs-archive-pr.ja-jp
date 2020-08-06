---
title: リソース ガバナーを使用してバックアップの圧縮による CPU 使用率を制限する方法 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup compression [SQL Server], Resource Governor
- backup compression [SQL Server], CPU usage
- compression [SQL Server], backup compression
- backups [SQL Server], compression
- Resource Governor, backup compression
ms.assetid: 01796551-578d-4425-9b9e-d87210f7ba72
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 19a95cfa5c6780fbdf71ae58bd141aa9aa351efa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742313"
---
# <a name="use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql"></a><span data-ttu-id="03c09-102">リソース ガバナーを使用してバックアップの圧縮による CPU 使用率を制限する方法 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="03c09-102">Use Resource Governor to Limit CPU Usage by Backup Compression (Transact-SQL)</span></span>
  <span data-ttu-id="03c09-103">既定の設定では、圧縮を使用してバックアップを行うと CPU 使用率が著しく増加し、圧縮処理に CPU が追加で消費されるために、同時に実行中の操作が悪影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="03c09-103">By default, backing up using compression significantly increases CPU usage, and the additional CPU consumed by the compression process can adversely impact concurrent operations.</span></span> <span data-ttu-id="03c09-104">このため、CPU の競合が発生したときは、[リソース ガバナー](../resource-governor/resource-governor.md) によって CPU 使用率が制限されるセッションで、優先度の低い圧縮されたバックアップを作成することが必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="03c09-104">Therefore, you might want to create a low-priority compressed backup in a session whose CPU usage is limited by[Resource Governor](../resource-governor/resource-governor.md) when CPU contention occurs.</span></span> <span data-ttu-id="03c09-105">このトピックでは、このような場合に CPU 使用率を制限するリソース ガバナー ワークロード グループに、特定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザーのセッションをマップしてそれらのセッションを分類するシナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="03c09-105">This topic presents a scenario that classifies the sessions of a particular [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user by mapping them to a Resource Governor workload group that limits CPU usage in such cases.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="03c09-106">所定のリソース ガバナーのシナリオでは、セッションの分類が、ユーザー名、アプリケーション名、または接続を区別できるその他の要素に基づいて行われます。</span><span class="sxs-lookup"><span data-stu-id="03c09-106">In a given Resource Governor scenario, session classification might be based on a user name, an application name, or anything else that can differentiate a connection.</span></span> <span data-ttu-id="03c09-107">詳細については、「 [Resource Governor Classifier Function](../resource-governor/resource-governor-classifier-function.md) 」および「 [Resource Governor Workload Group](../resource-governor/resource-governor-workload-group.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03c09-107">For more information, see [Resource Governor Classifier Function](../resource-governor/resource-governor-classifier-function.md) and [Resource Governor Workload Group](../resource-governor/resource-governor-workload-group.md).</span></span>  
  
##  <a name="this-topic-contains-the-following-set-of-scenarios-which-are-presented-in-sequence"></a><a name="Top"></a> <span data-ttu-id="03c09-108">このトピックでは、一連のシナリオを以下の順序で取り上げます。</span><span class="sxs-lookup"><span data-stu-id="03c09-108">This topic contains the following set of scenarios, which are presented in sequence:</span></span>  
  
1.  [<span data-ttu-id="03c09-109">優先度の低い操作を行うためのログインとユーザーの設定</span><span class="sxs-lookup"><span data-stu-id="03c09-109">Setting Up a Login and User for Low-Priority Operations</span></span>](#setup_login_and_user)  
  
2.  [<span data-ttu-id="03c09-110">CPU 使用率を制限するためのリソース ガバナーの構成</span><span class="sxs-lookup"><span data-stu-id="03c09-110">Configuring Resource Governor to Limit CPU Usage</span></span>](#configure_RG)  
  
3.  [<span data-ttu-id="03c09-111">現在のセッションの分類の確認 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="03c09-111">Verifying the Classification of the Current Session (Transact-SQL)</span></span>](#verifying)  
  
4.  [<span data-ttu-id="03c09-112">CPU が制限されているセッションを使用したバックアップの圧縮</span><span class="sxs-lookup"><span data-stu-id="03c09-112">Compressing Backups Using a Session with Limited CPU</span></span>](#creating_compressed_backup)  
  
##  <a name="setting-up-a-login-and-user-for-low-priority-operations"></a><a name="setup_login_and_user"></a> <span data-ttu-id="03c09-113">優先度の低い操作を行うためのログインとユーザーの設定</span><span class="sxs-lookup"><span data-stu-id="03c09-113">Setting Up a Login and User for Low-Priority Operations</span></span>  
 <span data-ttu-id="03c09-114">このトピックのシナリオには、優先度の低い [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインおよびユーザーが必要です。</span><span class="sxs-lookup"><span data-stu-id="03c09-114">The scenario in this topic requires a low-priority [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and user.</span></span> <span data-ttu-id="03c09-115">ユーザー名は、このログインで実行されるセッションを分類し、CPU 使用率を制限するリソース ガバナー ワークロード グループにセッションをルーティングするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="03c09-115">The user name will be used to classify sessions running in the login and route them to a Resource Governor workload group that limits CPU usage.</span></span>  
  
 <span data-ttu-id="03c09-116">以下では、この目的でログインとユーザーを設定する手順について説明した後に、[!INCLUDE[tsql](../../includes/tsql-md.md)] の例「例 A :ログインとユーザーの設定 (Transact-SQL)」を説明します。</span><span class="sxs-lookup"><span data-stu-id="03c09-116">The following procedure describes the steps for setting up a login and user for this purpose, followed by a [!INCLUDE[tsql](../../includes/tsql-md.md)] example, "Example A: Setting Up a Login and User (Transact-SQL)."</span></span>  
  
### <a name="to-set-up-a-login-and-database-user-for-classifying-sessions"></a><span data-ttu-id="03c09-117">セッションを分類するためにログインとデータベース ユーザーを設定するには</span><span class="sxs-lookup"><span data-stu-id="03c09-117">To set up a login and database user for classifying sessions</span></span>  
  
1.  <span data-ttu-id="03c09-118">優先度の低い圧縮されたバックアップを作成するための [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="03c09-118">Create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login for creating low-priority compressed backups.</span></span>  
  
     <span data-ttu-id="03c09-119">**ログインを作成するには**</span><span class="sxs-lookup"><span data-stu-id="03c09-119">**To create a login**</span></span>  
  
    -   [<span data-ttu-id="03c09-120">ログインの作成</span><span class="sxs-lookup"><span data-stu-id="03c09-120">Create a Login</span></span>](../security/authentication-access/create-a-login.md)  
  
    -   [<span data-ttu-id="03c09-121">CREATE LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="03c09-121">CREATE LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-login-transact-sql)  
  
2.  <span data-ttu-id="03c09-122">必要に応じて、このログインに VIEW SERVER STATE 権限を付与します。</span><span class="sxs-lookup"><span data-stu-id="03c09-122">Optionally, grant VIEW SERVER STATE to this login.</span></span>  
  
    -   [<span data-ttu-id="03c09-123">GRANT (システム オブジェクトの権限の許可) &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="03c09-123">GRANT System Object Permissions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/grant-system-object-permissions-transact-sql)  
  
     <span data-ttu-id="03c09-124">詳細については、「[GRANT (データベース プリンシパルの権限の許可) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-principal-permissions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03c09-124">For more information, see [GRANT Database Principal Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-principal-permissions-transact-sql).</span></span>  
  
3.  <span data-ttu-id="03c09-125">このログインに対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザーを作成します。</span><span class="sxs-lookup"><span data-stu-id="03c09-125">Create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user for this login.</span></span>  
  
     <span data-ttu-id="03c09-126">**ユーザーを作成するには**</span><span class="sxs-lookup"><span data-stu-id="03c09-126">**To create a user**</span></span>  
  
    -   [<span data-ttu-id="03c09-127">データベース ユーザーの作成</span><span class="sxs-lookup"><span data-stu-id="03c09-127">Create a Database User</span></span>](../security/authentication-access/create-a-database-user.md)  
  
    -   [<span data-ttu-id="03c09-128">CREATE USER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="03c09-128">CREATE USER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-user-transact-sql)  
  
4.  <span data-ttu-id="03c09-129">このログインおよびユーザーのセッションで特定のデータベースをバックアップできるようにするには、対象となるデータベースの db_backupoperator データベース ロールにこのユーザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="03c09-129">To enable sessions of this login and user to back up a given database, add the user to the db_backupoperator database role of that database.</span></span> <span data-ttu-id="03c09-130">この作業は、このユーザーがバックアップするデータベースごとに行います。</span><span class="sxs-lookup"><span data-stu-id="03c09-130">Do this for each database that this user will back up.</span></span> <span data-ttu-id="03c09-131">必要に応じて、このユーザーを他の固定データベース ロールに追加します。</span><span class="sxs-lookup"><span data-stu-id="03c09-131">Optionally, add the user to other fixed database roles.</span></span>  
  
     <span data-ttu-id="03c09-132">**固定データベース ロールにユーザーを追加するには**</span><span class="sxs-lookup"><span data-stu-id="03c09-132">**To add a user to a fixed database role**</span></span>  
  
    -   [<span data-ttu-id="03c09-133">sp_addrolemember &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="03c09-133">sp_addrolemember &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql)  
  
     <span data-ttu-id="03c09-134">詳細については、「[GRANT (データベース プリンシパルの権限の許可) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-principal-permissions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03c09-134">For more information, see [GRANT Database Principal Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-principal-permissions-transact-sql).</span></span>  
  
### <a name="example-a-setting-up-a-login-and-user-transact-sql"></a><span data-ttu-id="03c09-135">例 A:ログインとユーザーの設定 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="03c09-135">Example A: Setting Up a Login and User (Transact-SQL)</span></span>  
 <span data-ttu-id="03c09-136">次の例は、優先度の低いバックアップ用に新しい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインおよびユーザーを作成する場合にのみ該当します。</span><span class="sxs-lookup"><span data-stu-id="03c09-136">The following example is relevant only if you choose to create a new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and user for low-priority backups.</span></span> <span data-ttu-id="03c09-137">既存のログインとユーザーで適切なものがあれば、それを使用してもかまいません。</span><span class="sxs-lookup"><span data-stu-id="03c09-137">Alternatively, you can use an existing login and user, if an appropriate one exists.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="03c09-138">次の例では、サンプルのログインとユーザー名 *domain_name*`\MAX_CPU`を使用しています。</span><span class="sxs-lookup"><span data-stu-id="03c09-138">The following example uses a sample login and user name, *domain_name*`\MAX_CPU`.</span></span> <span data-ttu-id="03c09-139">この名前を、優先度の低い圧縮されたバックアップを作成する際に使用する予定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインおよびユーザーの名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="03c09-139">Replace these with the names of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and user that you plan to use when creating your low-priority compressed backups.</span></span>  
  
 <span data-ttu-id="03c09-140">この例では、Windows アカウント *domain_name*`\MAX_CPU` にログインを作成し、このログインに VIEW SERVER STATE 権限を付与します。</span><span class="sxs-lookup"><span data-stu-id="03c09-140">This example creates a login for the *domain_name*`\MAX_CPU` Windows account and then grants VIEW SERVER STATE permission to the login.</span></span> <span data-ttu-id="03c09-141">この権限によって、リソース ガバナーでログインのセッションがどのように分類されるかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="03c09-141">This permission enables you to verify the Resource Governor classification of sessions of the login.</span></span> <span data-ttu-id="03c09-142">次にこの例では、 *domain_name*`\MAX_CPU` のユーザーを作成し、このユーザーを [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] サンプル データベースの db_backupoperator 固定データベース ロールに追加します。</span><span class="sxs-lookup"><span data-stu-id="03c09-142">The example then creates a user for *domain_name*`\MAX_CPU` and adds it to the db_backupoperator fixed database role for the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="03c09-143">このユーザー名は、リソース ガバナーの分類子関数で使用されます。</span><span class="sxs-lookup"><span data-stu-id="03c09-143">This user name will be used by the Resource Governor classifier function.</span></span>  
  
```sql  
-- Create a SQL Server login for low-priority operations  
USE master;  
CREATE LOGIN [domain_name\MAX_CPU] FROM WINDOWS;  
GRANT VIEW SERVER STATE TO [domain_name\MAX_CPU];  
GO  
-- Create a SQL Server user in AdventureWorks2012 for this login  
USE AdventureWorks2012;  
CREATE USER [domain_name\MAX_CPU] FOR LOGIN [domain_name\MAX_CPU];  
EXEC sp_addrolemember 'db_backupoperator', 'domain_name\MAX_CPU';  
GO  
  
```  
  
 [<span data-ttu-id="03c09-144">&#91;先頭に戻る&#93;</span><span class="sxs-lookup"><span data-stu-id="03c09-144">&#91;Top&#93;</span></span>](#Top)  
  
##  <a name="configuring-resource-governor-to-limit-cpu-usage"></a><a name="configure_RG"></a> <span data-ttu-id="03c09-145">CPU 使用率を制限するためのリソース ガバナーの構成</span><span class="sxs-lookup"><span data-stu-id="03c09-145">Configuring Resource Governor to Limit CPU Usage</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="03c09-146">リソース ガバナーが有効になっていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="03c09-146">Ensure that Resource Governor is enabled.</span></span> <span data-ttu-id="03c09-147">詳細については、「 [リソース ガバナーの有効化](../resource-governor/enable-resource-governor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03c09-147">For more information, see [Enable Resource Governor](../resource-governor/enable-resource-governor.md).</span></span>  
  
 <span data-ttu-id="03c09-148">このリソース ガバナーのシナリオでは、次の基本的な手順で構成が行われます。</span><span class="sxs-lookup"><span data-stu-id="03c09-148">In this Resource Governor scenario, configuration comprises the following basic steps:</span></span>  
  
1.  <span data-ttu-id="03c09-149">リソース ガバナーのリソース プールを作成し、CPU の競合が発生したときにリソース プール内の要求に割り当てられる最大平均 CPU 帯域幅を制限するように構成します。</span><span class="sxs-lookup"><span data-stu-id="03c09-149">Create and configure a Resource Governor resource pool that limits the maximum average CPU bandwidth that will be given to requests in the resource pool when CPU contention occurs.</span></span>  
  
2.  <span data-ttu-id="03c09-150">このプールを使用するリソース ガバナー ワークロード グループを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="03c09-150">Create and configure a Resource Governor workload group that uses this pool.</span></span>  
  
3.  <span data-ttu-id="03c09-151">ユーザー定義関数 (UDF) である *分類子関数*を作成します。リソース ガバナーは、この関数の戻り値を使用してセッションを分類し、適切なワークロード グループにセッションがルーティングされるようにします。</span><span class="sxs-lookup"><span data-stu-id="03c09-151">Create a *classifier function*, which is a user-defined function (UDF) whose return values are used by Resource Governor for classifying sessions so that they are routed to the appropriate workload group.</span></span>  
  
4.  <span data-ttu-id="03c09-152">分類子関数をリソース ガバナーに登録します。</span><span class="sxs-lookup"><span data-stu-id="03c09-152">Register the classifier function with Resource Governor.</span></span>  
  
5.  <span data-ttu-id="03c09-153">リソース ガバナーのメモリ内の構成に変更を適用します。</span><span class="sxs-lookup"><span data-stu-id="03c09-153">Apply the changes to the Resource Governor in-memory configuration.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="03c09-154">リソース ガバナーのリソース プール、ワークロード グループ、および分類の詳細については、「 [リソース ガバナー](../resource-governor/resource-governor.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="03c09-154">For information about Resource Governor resource pools, workload groups, and classification, see [Resource Governor](../resource-governor/resource-governor.md).</span></span>  
  
 <span data-ttu-id="03c09-155">上記の手順で使用する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントについては、「CPU 使用率を制限するようにリソース ガバナーを構成するには」で説明し、その後に [!INCLUDE[tsql](../../includes/tsql-md.md)] の例を示します。</span><span class="sxs-lookup"><span data-stu-id="03c09-155">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statements for these steps are described in the procedure, "To configure Resource Governor for limiting CPU usage," which is followed by a [!INCLUDE[tsql](../../includes/tsql-md.md)] example of the procedure.</span></span>  
  
 <span data-ttu-id="03c09-156">**リソース ガバナーを構成するには (SQL Server Management Studio)**</span><span class="sxs-lookup"><span data-stu-id="03c09-156">**To configure Resource Governor (SQL Server Management Studio)**</span></span>  
  
-   [<span data-ttu-id="03c09-157">テンプレートを使用してリソース ガバナーを構成する</span><span class="sxs-lookup"><span data-stu-id="03c09-157">Configure Resource Governor Using a Template</span></span>](../resource-governor/configure-resource-governor-using-a-template.md)  
  
-   [<span data-ttu-id="03c09-158">リソース プールの作成</span><span class="sxs-lookup"><span data-stu-id="03c09-158">Create a Resource Pool</span></span>](../resource-governor/create-a-resource-pool.md)  
  
-   [<span data-ttu-id="03c09-159">ワークロード グループの作成</span><span class="sxs-lookup"><span data-stu-id="03c09-159">Create a Workload Group</span></span>](../resource-governor/create-a-workload-group.md)  
  
### <a name="to-configure-resource-governor-for-limiting-cpu-usage-transact-sql"></a><span data-ttu-id="03c09-160">CPU 使用率を制限するようにリソース ガバナーを構成するには (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="03c09-160">To configure Resource Governor for limiting CPU usage (Transact-SQL)</span></span>  
  
1.  <span data-ttu-id="03c09-161">[CREATE RESOURCE POOL](/sql/t-sql/statements/create-resource-pool-transact-sql) ステートメントを実行してリソース プールを作成します。</span><span class="sxs-lookup"><span data-stu-id="03c09-161">Issue a [CREATE RESOURCE POOL](/sql/t-sql/statements/create-resource-pool-transact-sql) statement to create a resource pool.</span></span> <span data-ttu-id="03c09-162">この手順の例では、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="03c09-162">The example for this procedure uses the following syntax:</span></span>  
  
     <span data-ttu-id="03c09-163">*CREATE RESOURCE POOL pool_name* WITH ( MAX_CPU_PERCENT = *value* );</span><span class="sxs-lookup"><span data-stu-id="03c09-163">*CREATE RESOURCE POOL pool_name* WITH ( MAX_CPU_PERCENT = *value* );</span></span>  
  
     <span data-ttu-id="03c09-164">*Value* は、最大平均 CPU 帯域幅の割合を示す 1 ～ 100 の整数です。</span><span class="sxs-lookup"><span data-stu-id="03c09-164">*Value* is an integer from 1 to 100 that indicates the percentage of maximum average CPU bandwidth.</span></span> <span data-ttu-id="03c09-165">適切な値は環境によって異なります。</span><span class="sxs-lookup"><span data-stu-id="03c09-165">The appropriate value depends on your environment.</span></span> <span data-ttu-id="03c09-166">わかりやすいように、このトピックの例では 20% (MAX_CPU_PERCENT = 20) を使用します。</span><span class="sxs-lookup"><span data-stu-id="03c09-166">For the purpose of illustration, the example in this topic uses 20%  percent (MAX_CPU_PERCENT = 20.)</span></span>  
  
2.  <span data-ttu-id="03c09-167">[CREATE WORKLOAD GROUP](/sql/t-sql/statements/create-workload-group-transact-sql) ステートメントを実行して、CPU 使用率を制限する優先度の低い操作用にワークロード グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="03c09-167">Issue a [CREATE WORKLOAD GROUP](/sql/t-sql/statements/create-workload-group-transact-sql) statement to create a workload group for low-priority operations whose CPU usage you want to govern.</span></span> <span data-ttu-id="03c09-168">この手順の例では、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="03c09-168">The example for this procedure uses the following syntax:</span></span>  
  
     <span data-ttu-id="03c09-169">CREATE WORKLOAD GROUP *group_name* USING *pool_name*;</span><span class="sxs-lookup"><span data-stu-id="03c09-169">CREATE WORKLOAD GROUP *group_name* USING *pool_name*;</span></span>  
  
3.  <span data-ttu-id="03c09-170">[CREATE FUNCTION](/sql/t-sql/statements/create-function-transact-sql) ステートメントを実行して、前の手順で作成したワークロード グループを優先度の低いログインのユーザーにマップする分類子関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="03c09-170">Issue a [CREATE FUNCTION](/sql/t-sql/statements/create-function-transact-sql) statement to create a classifier function that maps the workload group created in the preceding step to the user of the low-priority login.</span></span> <span data-ttu-id="03c09-171">この手順の例では、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="03c09-171">The example for this procedure uses the following syntax:</span></span>  
  
     <span data-ttu-id="03c09-172">CREATE FUNCTION [*schema_name*.]*function_name*() RETURNS sysname</span><span class="sxs-lookup"><span data-stu-id="03c09-172">CREATE FUNCTION [*schema_name*.]*function_name*() RETURNS sysname</span></span>  
  
     <span data-ttu-id="03c09-173">WITH SCHEMABINDING</span><span class="sxs-lookup"><span data-stu-id="03c09-173">WITH SCHEMABINDING</span></span>  
  
     <span data-ttu-id="03c09-174">AS</span><span class="sxs-lookup"><span data-stu-id="03c09-174">AS</span></span>  
  
     <span data-ttu-id="03c09-175">BEGIN</span><span class="sxs-lookup"><span data-stu-id="03c09-175">BEGIN</span></span>  
  
     <span data-ttu-id="03c09-176">DECLARE @workload_group_name AS *sysname*</span><span class="sxs-lookup"><span data-stu-id="03c09-176">DECLARE @workload_group_name AS *sysname*</span></span>  
  
     <span data-ttu-id="03c09-177">IF (SUSER_NAME() = '*user_of_low_priority_login*')</span><span class="sxs-lookup"><span data-stu-id="03c09-177">IF (SUSER_NAME() = '*user_of_low_priority_login*')</span></span>  
  
     <span data-ttu-id="03c09-178">SET @workload_group_name = '*workload_group_name*'</span><span class="sxs-lookup"><span data-stu-id="03c09-178">SET @workload_group_name = '*workload_group_name*'</span></span>  
  
     <span data-ttu-id="03c09-179">RETURN @workload_group_name</span><span class="sxs-lookup"><span data-stu-id="03c09-179">RETURN @workload_group_name</span></span>  
  
     <span data-ttu-id="03c09-180">End</span><span class="sxs-lookup"><span data-stu-id="03c09-180">END</span></span>  
  
     <span data-ttu-id="03c09-181">この CREATE FUNCTION ステートメントのコンポーネントの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="03c09-181">For information about the components of this CREATE FUNCTION statement, see:</span></span>  
  
    -   [<span data-ttu-id="03c09-182">DECLARE @local_variable &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="03c09-182">DECLARE @local_variable &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/declare-local-variable-transact-sql)  
  
    -   [<span data-ttu-id="03c09-183">SUSER_SNAME &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="03c09-183">SUSER_SNAME &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/suser-sname-transact-sql)  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="03c09-184">SUSER_NAME は、分類子関数で使用できるシステム関数の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="03c09-184">SUSER_NAME is just one of several system functions that can be used in a classifier function.</span></span> <span data-ttu-id="03c09-185">詳細については、「 [ユーザー定義の分類子関数の作成とテスト](../resource-governor/create-and-test-a-classifier-user-defined-function.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03c09-185">For more information, see [Create and Test a Classifier User-Defined Function](../resource-governor/create-and-test-a-classifier-user-defined-function.md).</span></span>  
  
    -   <span data-ttu-id="03c09-186">[SET @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/set-local-variable-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="03c09-186">[SET @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/set-local-variable-transact-sql).</span></span>  
  
4.  <span data-ttu-id="03c09-187">[ALTER RESOURCE GOVERNOR](/sql/t-sql/statements/alter-resource-governor-transact-sql) ステートメントを実行して、分類子関数をリソース ガバナーに登録します。</span><span class="sxs-lookup"><span data-stu-id="03c09-187">Issue an [ALTER RESOURCE GOVERNOR](/sql/t-sql/statements/alter-resource-governor-transact-sql) statement to register the classifier function with Resource Governor.</span></span> <span data-ttu-id="03c09-188">この手順の例では、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="03c09-188">The example for this procedure uses the following syntax:</span></span>  
  
     <span data-ttu-id="03c09-189">ALTER RESOURCE GOVERNOR WITH (CLASSIFIER_FUNCTION = *schema_name*.*function_name*);</span><span class="sxs-lookup"><span data-stu-id="03c09-189">ALTER RESOURCE GOVERNOR WITH (CLASSIFIER_FUNCTION = *schema_name*.*function_name*);</span></span>  
  
5.  <span data-ttu-id="03c09-190">次のように 2 回目の ALTER RESOURCE GOVERNOR ステートメントを実行して、リソース ガバナーのメモリ内の構成に変更を適用します。</span><span class="sxs-lookup"><span data-stu-id="03c09-190">Issue a second ALTER RESOURCE GOVERNOR statement to apply the changes to the Resource Governor in-memory configuration, as follows:</span></span>  
  
    ```  
    ALTER RESOURCE GOVERNOR RECONFIGURE;  
    ```  
  
### <a name="example-b-configuring-resource-governor-transact-sql"></a><span data-ttu-id="03c09-191">例 B:Resource Governor の構成 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="03c09-191">Example B: Configuring Resource Governor (Transact-SQL)</span></span>  
 <span data-ttu-id="03c09-192">次の例では、以下の手順を 1 つのトランザクションで実行します。</span><span class="sxs-lookup"><span data-stu-id="03c09-192">The following example performs the following steps within a single transaction:</span></span>  
  
1.  <span data-ttu-id="03c09-193">`pMAX_CPU_PERCENT_20` リソース プールを作成します。</span><span class="sxs-lookup"><span data-stu-id="03c09-193">Creates the `pMAX_CPU_PERCENT_20` resource pool.</span></span>  
  
2.  <span data-ttu-id="03c09-194">`gMAX_CPU_PERCENT_20` ワークロード グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="03c09-194">Creates the `gMAX_CPU_PERCENT_20` workload group.</span></span>  
  
3.  <span data-ttu-id="03c09-195">前の例で作成したユーザー名を使用する `rgclassifier_MAX_CPU()` 分類子関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="03c09-195">Creates the `rgclassifier_MAX_CPU()` classifier function, which uses the user name created in the preceding example.</span></span>  
  
4.  <span data-ttu-id="03c09-196">分類子関数をリソース ガバナーに登録します。</span><span class="sxs-lookup"><span data-stu-id="03c09-196">Registers the classifier function with Resource Governor.</span></span>  
  
 <span data-ttu-id="03c09-197">この例では、トランザクションをコミットした後に、ALTER WORKLOAD GROUP または ALTER RESOURCE POOL ステートメントで要求された構成の変更が適用されます。</span><span class="sxs-lookup"><span data-stu-id="03c09-197">After committing the transaction, the example applies the configuration changes requested in the ALTER WORKLOAD GROUP or ALTER RESOURCE POOL statements.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="03c09-198">次の例では、「例 A: ログインとユーザーの設定 (Transact-SQL)」で作成したサンプルの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザーのユーザー名*domain_name*`\MAX_CPU` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="03c09-198">The following example uses the user name of the sample [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user created in "Example A: Setting Up a Login and User (Transact-SQL)," *domain_name*`\MAX_CPU`.</span></span> <span data-ttu-id="03c09-199">この名前を、優先度の低い圧縮されたバックアップを作成する際に使用する予定のログインのユーザーの名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="03c09-199">Replace this with the name of the user of the login that you plan to use for creating low-priority compressed backups.</span></span>  
  
```sql  
-- Configure Resource Governor.  
BEGIN TRAN  
USE master;  
-- Create a resource pool that sets the MAX_CPU_PERCENT to 20%.   
CREATE RESOURCE POOL pMAX_CPU_PERCENT_20  
   WITH  
      (MAX_CPU_PERCENT = 20);  
GO  
-- Create a workload group to use this pool.   
CREATE WORKLOAD GROUP gMAX_CPU_PERCENT_20  
USING pMAX_CPU_PERCENT_20;  
GO  
-- Create a classification function.  
-- Note that any request that does not get classified goes into   
-- the 'Default' group.  
CREATE FUNCTION dbo.rgclassifier_MAX_CPU() RETURNS sysname   
WITH SCHEMABINDING  
AS  
BEGIN  
    DECLARE @workload_group_name AS sysname  
      IF (SUSER_NAME() = 'domain_name\MAX_CPU')  
          SET @workload_group_name = 'gMAX_CPU_PERCENT_20'  
    RETURN @workload_group_name  
END;  
GO  
  
-- Register the classifier function with Resource Governor.  
ALTER RESOURCE GOVERNOR WITH (CLASSIFIER_FUNCTION= dbo.rgclassifier_MAX_CPU);  
COMMIT TRAN;  
GO  
-- Start Resource Governor  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
  
```  
  
 [<span data-ttu-id="03c09-200">&#91;先頭に戻る&#93;</span><span class="sxs-lookup"><span data-stu-id="03c09-200">&#91;Top&#93;</span></span>](#Top)  
  
##  <a name="verifying-the-classification-of-the-current-session-transact-sql"></a><a name="verifying"></a> <span data-ttu-id="03c09-201">現在のセッションの分類の確認 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="03c09-201">Verifying the Classification of the Current Session (Transact-SQL)</span></span>  
 <span data-ttu-id="03c09-202">必要に応じて、分類子関数で指定したユーザーとしてログインし、オブジェクト エクスプローラーで次の [SELECT](/sql/t-sql/queries/select-transact-sql) ステートメントを実行してセッションの分類を確認します。</span><span class="sxs-lookup"><span data-stu-id="03c09-202">Optionally, log in as the user that you specified in your classifier function, and verify the session classification by issuing the following [SELECT](/sql/t-sql/queries/select-transact-sql) statement in Object Explorer:</span></span>  
  
```sql  
USE master;  
SELECT sess.session_id, sess.login_name, sess.group_id, grps.name   
FROM sys.dm_exec_sessions AS sess   
JOIN sys.dm_resource_governor_workload_groups AS grps   
    ON sess.group_id = grps.group_id  
WHERE session_id > 50;  
GO  
```  
  
 <span data-ttu-id="03c09-203">結果ペインの **[名前]** 列に、分類子関数で指定したワークロード グループ名のセッションが 1 つ以上表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="03c09-203">In the results pane, the **name** column should list one or more sessions for the workload-group name that you specified in your classifier function.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="03c09-204">この SELECT ステートメントで呼び出される動的管理ビューの詳細については、「[sys.dm_exec_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql)」および「[sys.dm_resource_governor_workload_groups &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="03c09-204">For information about the dynamic management views called by this SELECT statement, see [sys.dm_exec_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) and [sys.dm_resource_governor_workload_groups &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql).</span></span>  
  
 [<span data-ttu-id="03c09-205">&#91;先頭に戻る&#93;</span><span class="sxs-lookup"><span data-stu-id="03c09-205">&#91;Top&#93;</span></span>](#Top)  
  
##  <a name="compressing-backups-using-a-session-with-limited-cpu"></a><a name="creating_compressed_backup"></a> <span data-ttu-id="03c09-206">CPU が制限されているセッションを使用したバックアップの圧縮</span><span class="sxs-lookup"><span data-stu-id="03c09-206">Compressing Backups Using a Session with Limited CPU</span></span>  
 <span data-ttu-id="03c09-207">最大 CPU が制限されているセッションで圧縮されたバックアップを作成するには、分類子関数で指定したユーザーでログインします。</span><span class="sxs-lookup"><span data-stu-id="03c09-207">To create a compressed backup in a session with a limited maximum CPU, log in as the user specified in your classifier function.</span></span> <span data-ttu-id="03c09-208">バックアップコマンドで、WITH COMPRESSION () を指定するか、 [!INCLUDE[tsql](../../includes/tsql-md.md)] [**バックアップを圧縮**する] () を選択し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="03c09-208">In your backup command, either specify WITH COMPRESSION ([!INCLUDE[tsql](../../includes/tsql-md.md)]) or select **Compress backup** ([!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]).</span></span> <span data-ttu-id="03c09-209">圧縮されたデータベース バックアップを作成する方法については、「[データベースの完全バックアップの作成 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="03c09-209">To create a compressed database backup, see [Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).</span></span>  
  
### <a name="example-c-creating-a-compressed-backup-transact-sql"></a><span data-ttu-id="03c09-210">例 C: 圧縮されたバックアップの作成 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="03c09-210">Example C: Creating a Compressed Backup (Transact-SQL)</span></span>  
 <span data-ttu-id="03c09-211">次に示す [BACKUP](/sql/t-sql/statements/backup-transact-sql) の例では、 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] データベースの圧縮された完全バックアップを、新たな形式のバックアップ ファイル `Z:\SQLServerBackups\AdvWorksData.bak`に作成します。</span><span class="sxs-lookup"><span data-stu-id="03c09-211">The following [BACKUP](/sql/t-sql/statements/backup-transact-sql) example creates a compressed full backup of the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database in a newly formatted backup file, `Z:\SQLServerBackups\AdvWorksData.bak`.</span></span>  
  
```sql  
--Run backup statement in the gBackup session.  
BACKUP DATABASE AdventureWorks2012 TO DISK='Z:\SQLServerBackups\AdvWorksData.bak'   
WITH   
   FORMAT,   
   MEDIADESCRIPTION='AdventureWorks2012 Compressed Data Backups'  
   DESCRIPTION='First database backup on AdventureWorks2012 Compressed Data Backups media set'  
   COMPRESSION;  
GO  
```  
  
 [<span data-ttu-id="03c09-212">&#91;先頭に戻る&#93;</span><span class="sxs-lookup"><span data-stu-id="03c09-212">&#91;Top&#93;</span></span>](#Top)  
  
## <a name="see-also"></a><span data-ttu-id="03c09-213">参照</span><span class="sxs-lookup"><span data-stu-id="03c09-213">See Also</span></span>  
 <span data-ttu-id="03c09-214">[ユーザー定義の分類子関数の作成とテスト](../resource-governor/create-and-test-a-classifier-user-defined-function.md) </span><span class="sxs-lookup"><span data-stu-id="03c09-214">[Create and Test a Classifier User-Defined Function](../resource-governor/create-and-test-a-classifier-user-defined-function.md) </span></span>  
 [<span data-ttu-id="03c09-215">リソース ガバナー</span><span class="sxs-lookup"><span data-stu-id="03c09-215">Resource Governor</span></span>](../resource-governor/resource-governor.md)  
  
  
