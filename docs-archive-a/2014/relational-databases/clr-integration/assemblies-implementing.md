---
title: アセンブリの実装 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], implementing
ms.assetid: c228d7bf-a906-4f37-a057-5d464d962ff8
author: rothja
ms.author: jroth
ms.openlocfilehash: 3cb3818ed644eede3cf4f2c256a0dcb94ec58c3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720061"
---
# <a name="implementing-assemblies"></a><span data-ttu-id="1fe25-102">アセンブリの実装</span><span class="sxs-lookup"><span data-stu-id="1fe25-102">Implementing Assemblies</span></span>
  <span data-ttu-id="1fe25-103">このトピックでは、データベースにアセンブリを実装し、それらのアセンブリを使用して作業するのに役立つ次の情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="1fe25-103">This topic provides information about the following areas to help you implement and work with assemblies in the database:</span></span>  
  
-   <span data-ttu-id="1fe25-104">アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="1fe25-104">Creating assemblies</span></span>  
  
-   <span data-ttu-id="1fe25-105">アセンブリの変更</span><span class="sxs-lookup"><span data-stu-id="1fe25-105">Modifying assemblies</span></span>  
  
-   <span data-ttu-id="1fe25-106">アセンブリの削除、無効化、および有効化</span><span class="sxs-lookup"><span data-stu-id="1fe25-106">Dropping, disabling, and enabling assemblies</span></span>  
  
-   <span data-ttu-id="1fe25-107">アセンブリバージョンの管理</span><span class="sxs-lookup"><span data-stu-id="1fe25-107">Managing assembly versions</span></span>  
  
## <a name="creating-assemblies"></a><span data-ttu-id="1fe25-108">アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="1fe25-108">Creating Assemblies</span></span>  
 <span data-ttu-id="1fe25-109">アセンブリの作成は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY ステートメントを使用し、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ではアセンブリ支援エディターを使用して行います。</span><span class="sxs-lookup"><span data-stu-id="1fe25-109">Assemblies are created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY statement, or in the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the Assembly Assisted Editor.</span></span> <span data-ttu-id="1fe25-110">さらに、で SQL Server プロジェクトを配置すると、プロジェクトに指定された [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] データベースにアセンブリが登録されます。</span><span class="sxs-lookup"><span data-stu-id="1fe25-110">Additionally, deploying a SQL Server Project in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] registers an assembly in the database that was specified for the project.</span></span> <span data-ttu-id="1fe25-111">詳細については、「 [CLR データベース オブジェクトの配置](deploying-clr-database-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fe25-111">For more information, see [Deploying CLR Database Objects](deploying-clr-database-objects.md).</span></span>  
  
 <span data-ttu-id="1fe25-112">**Transact-SQL を使用してアセンブリを作成するには**</span><span class="sxs-lookup"><span data-stu-id="1fe25-112">**To create an assembly by using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="1fe25-113">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1fe25-113">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-assembly-transact-sql)  
  
 <span data-ttu-id="1fe25-114">**SQL Server Management Studio を使用してアセンブリを作成するには**</span><span class="sxs-lookup"><span data-stu-id="1fe25-114">**To create an assembly by using SQL Server Management Studio**</span></span>  
  
-   <span data-ttu-id="1fe25-115">[[アセンブリのプロパティ] &#40;[全般] ページ&#41;](assemblies-properties.md)</span><span class="sxs-lookup"><span data-stu-id="1fe25-115">[Assembly Properties &#40;General Page&#41;](assemblies-properties.md)</span></span>  
  
## <a name="modifying-assemblies"></a><span data-ttu-id="1fe25-116">アセンブリの変更</span><span class="sxs-lookup"><span data-stu-id="1fe25-116">Modifying Assemblies</span></span>  
 <span data-ttu-id="1fe25-117">アセンブリの変更は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY ステートメントを使用し、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ではアセンブリ支援エディターを使用して行います。</span><span class="sxs-lookup"><span data-stu-id="1fe25-117">Assemblies are modified in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY statement or in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the Assembly Assisted Editor.</span></span> <span data-ttu-id="1fe25-118">次の操作を行うと、アセンブリを変更できます。</span><span class="sxs-lookup"><span data-stu-id="1fe25-118">You can modify an assembly when you want to do the following:</span></span>  
  
-   <span data-ttu-id="1fe25-119">アセンブリの新しいバージョンのバイナリをアップロードして、アセンブリの実装を変更します。</span><span class="sxs-lookup"><span data-stu-id="1fe25-119">Change the implementation of the assembly by uploading a newer version of the binaries of the assembly.</span></span> <span data-ttu-id="1fe25-120">詳細については、このトピックで後述[する「アセンブリバージョンの管理](#_managing)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fe25-120">For more information, see [Managing Assembly Versions](#_managing) later in this topic.</span></span>  
  
-   <span data-ttu-id="1fe25-121">アセンブリの権限セットを変更します。</span><span class="sxs-lookup"><span data-stu-id="1fe25-121">Change the permission set of the assembly.</span></span> <span data-ttu-id="1fe25-122">詳細については、「[アセンブリのデザイン](../../relational-databases/clr-integration/assemblies-designing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fe25-122">For more information, see [Designing Assemblies](../../relational-databases/clr-integration/assemblies-designing.md).</span></span>  
  
-   <span data-ttu-id="1fe25-123">アセンブリの表示設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="1fe25-123">Change the visibility of the assembly.</span></span> <span data-ttu-id="1fe25-124">表示されるアセンブリは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で参照できます。</span><span class="sxs-lookup"><span data-stu-id="1fe25-124">Visible assemblies are available for referencing in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1fe25-125">表示されないアセンブリは、データベースにアップロードされている場合でも参照できません。</span><span class="sxs-lookup"><span data-stu-id="1fe25-125">Nonvisible assemblies are not available, even if they have been uploaded in the database.</span></span> <span data-ttu-id="1fe25-126">既定では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにアップロードされたアセンブリは表示されます。</span><span class="sxs-lookup"><span data-stu-id="1fe25-126">By default, assemblies uploaded to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are visible.</span></span>  
  
-   <span data-ttu-id="1fe25-127">アセンブリに関連付けられているデバッグ ファイルやソース ファイルを追加または削除します。</span><span class="sxs-lookup"><span data-stu-id="1fe25-127">Add or drop a debug or source file associated with the assembly.</span></span>  
  
 <span data-ttu-id="1fe25-128">**Transact-SQL を使用してアセンブリを変更するには**</span><span class="sxs-lookup"><span data-stu-id="1fe25-128">**To modify an assembly by using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="1fe25-129">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1fe25-129">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
 <span data-ttu-id="1fe25-130">**SQL Server Management Studio を使用してアセンブリを変更するには**</span><span class="sxs-lookup"><span data-stu-id="1fe25-130">**To modify an assembly by using SQL Server Management Studio**</span></span>  
  
-   <span data-ttu-id="1fe25-131">[[アセンブリのプロパティ] &#40;[全般] ページ&#41;](assemblies-properties.md)</span><span class="sxs-lookup"><span data-stu-id="1fe25-131">[Assembly Properties &#40;General Page&#41;](assemblies-properties.md)</span></span>  
  
## <a name="dropping-disabling-and-enabling-assemblies"></a><span data-ttu-id="1fe25-132">アセンブリの削除、無効化、および有効化</span><span class="sxs-lookup"><span data-stu-id="1fe25-132">Dropping, Disabling, and Enabling Assemblies</span></span>  
 <span data-ttu-id="1fe25-133">アセンブリの削除は、[!INCLUDE[tsql](../../includes/tsql-md.md)] DROP ASSEMBLY ステートメントまたは [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して行います。</span><span class="sxs-lookup"><span data-stu-id="1fe25-133">Assemblies are dropped by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] DROP ASSEMBLY statement or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="1fe25-134">**Transact-SQL を使用してアセンブリを削除するには**</span><span class="sxs-lookup"><span data-stu-id="1fe25-134">**To drop an assembly by using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="1fe25-135">DROP ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1fe25-135">DROP ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 <span data-ttu-id="1fe25-136">**SQL Server Management Studio を使用してアセンブリを削除するには**</span><span class="sxs-lookup"><span data-stu-id="1fe25-136">**To drop an assembly by using SQL Server Management Studio**</span></span>  
  
-   <span data-ttu-id="1fe25-137">[[オブジェクトの削除]](../../ssms/object/delete-objects.md)</span><span class="sxs-lookup"><span data-stu-id="1fe25-137">[Delete Objects](../../ssms/object/delete-objects.md)</span></span>  
  
 <span data-ttu-id="1fe25-138">既定では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で作成されたアセンブリがすべて実行できない状態になっています。</span><span class="sxs-lookup"><span data-stu-id="1fe25-138">By default, all assemblies that are created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are disabled from executing.</span></span> <span data-ttu-id="1fe25-139">**Sp_configure**システムストアドプロシージャの**clr enabled**オプションを使用して、でアップロードされるすべてのアセンブリの実行を無効または有効にすることができ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="1fe25-139">You can use the **clr enabled** option of the **sp_configure** system stored procedure to disable or enable the execution of all assemblies that are uploaded in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1fe25-140">アセンブリの実行を無効にすると、CLR (共通言語ランタイム) 関数、ストアド プロシージャ、トリガー、集計、およびユーザー定義型を実行できなくなり、現在実行されている場合は停止されます。</span><span class="sxs-lookup"><span data-stu-id="1fe25-140">Disabling assembly execution prevents common language runtime (CLR) functions, stored procedures, triggers, aggregates, and user-defined types from executing, and stops those that are currently executing.</span></span> <span data-ttu-id="1fe25-141">アセンブリの実行を無効にしても、アセンブリを作成、変更、または削除する機能は無効になりません。</span><span class="sxs-lookup"><span data-stu-id="1fe25-141">Disabling assembly execution does not disable the ability to create, alter, or drop assemblies.</span></span> <span data-ttu-id="1fe25-142">詳細については、「 [clr Enabled サーバー構成オプション](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fe25-142">For more information, see [clr enabled Server Configuration Option](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="1fe25-143">**アセンブリの実行を無効および有効にするには**</span><span class="sxs-lookup"><span data-stu-id="1fe25-143">**To disable and enable assembly execution**</span></span>  
  
-   [<span data-ttu-id="1fe25-144">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1fe25-144">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
##  <a name="managing-assembly-versions"></a><a name="_managing"></a><span data-ttu-id="1fe25-145">アセンブリバージョンの管理</span><span class="sxs-lookup"><span data-stu-id="1fe25-145">Managing Assembly Versions</span></span>  
 <span data-ttu-id="1fe25-146">アセンブリを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにアップロードすると、そのアセンブリはデータベース システム カタログ内に格納され、管理されます。</span><span class="sxs-lookup"><span data-stu-id="1fe25-146">When an assembly is uploaded to an instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the assembly is stored and managed within the database system catalogs.</span></span> <span data-ttu-id="1fe25-147">でアセンブリの定義に加えられた変更は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データベースカタログに格納されているアセンブリに反映される必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fe25-147">Any changes made to the definition of the assembly in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] should be propagated to the assembly that is stored in the database catalog.</span></span>  
  
 <span data-ttu-id="1fe25-148">アセンブリを変更する必要がある場合は、ALTER ASSEMBLY ステートメントを実行してデータベース内のアセンブリを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fe25-148">When you have to modify an assembly, you must issue an ALTER ASSEMBLY statement to update the assembly in the database.</span></span> <span data-ttu-id="1fe25-149">これにより、アセンブリの実装を保持している [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] モジュールの最新のコピーにアセンブリが更新されます。</span><span class="sxs-lookup"><span data-stu-id="1fe25-149">This will update the assembly to the latest copy of [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] modules holding its implementation.</span></span>  
  
 <span data-ttu-id="1fe25-150">ALTER ASSEMBLY ステートメントの WITH UNCHECKED DATA 句は、データベース内の永続化されたデータが依存しているアセンブリも最新状態に更新するように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に指示します。</span><span class="sxs-lookup"><span data-stu-id="1fe25-150">The WITH UNCHECKED DATA clause of the ALTER ASSEMBLY statement instructs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to refresh even those assemblies upon which persisted data in the database is dependent.</span></span> <span data-ttu-id="1fe25-151">具体的には、次のいずれかが存在する場合、WITH UNCHECKED DATA を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fe25-151">Specifically, you must specify WITH UNCHECKED DATA if any of the following exist:</span></span>  
  
-   <span data-ttu-id="1fe25-152">[!INCLUDE[tsql](../../includes/tsql-md.md)] の関数またはメソッドによってアセンブリ内のメソッドを直接または間接的に参照する、永続化された計算列。</span><span class="sxs-lookup"><span data-stu-id="1fe25-152">Persisted computed columns that reference methods in the assembly, either directly, or indirectly, through [!INCLUDE[tsql](../../includes/tsql-md.md)] functions or methods.</span></span>  
  
-   <span data-ttu-id="1fe25-153">アセンブリに依存する CLR ユーザー定義型の列と、**UserDefined** (非**ネイティブ**) シリアル化形式を実装する型の列。</span><span class="sxs-lookup"><span data-stu-id="1fe25-153">Columns of a CLR user-defined type that depend on the assembly, and the type implements a **UserDefined** (non-**Native**) serialization format.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="1fe25-154">WITH UNCHECKED DATA を指定せず、新しいバージョンのアセンブリによってテーブルの既存のデータ、インデックス、または他の固有サイトに影響が生じる場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では ALTER ASSEMBLY の実行回避が試みられます。</span><span class="sxs-lookup"><span data-stu-id="1fe25-154">If WITH UNCHECKED DATA is not specified, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tries to prevent ALTER ASSEMBLY from executing if the new assembly version affects existing data in tables, indexes, or other persistent sites.</span></span> <span data-ttu-id="1fe25-155">ただし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、CLR アセンブリの更新時に、計算列、インデックス、インデックス付きビュー、または式が、基になるルーチンや型と一致することは保証されません。</span><span class="sxs-lookup"><span data-stu-id="1fe25-155">However, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not guarantee that computed columns, indexes, indexed views, or expressions will be consistent with the underlying routines and types when the CLR assembly is updated.</span></span> <span data-ttu-id="1fe25-156">ALTER ASSEMBLY を実行する場合は、式の結果とアセンブリ内の式に基づく値との間に不一致が生じないように注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fe25-156">Be careful when you execute ALTER ASSEMBLY to make sure that there is no mismatch between the result of an expression and a value that is based on that expression stored in the assembly.</span></span>  
  
 <span data-ttu-id="1fe25-157">WITH UNCHECKED DATA 句を使用して ALTER ASSEMBLY を実行できるのは、 **db_owner**および**db_ddlowner**固定データベースロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="1fe25-157">Only members of the **db_owner** and **db_ddlowner** fixed database role can execute run ALTER ASSEMBLY by using the WITH UNCHECKED DATA clause.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1fe25-158">は、テーブル内に未チェック データがある状態でアセンブリが変更されたというメッセージを Windows アプリケーション イベント ログに記録します。</span><span class="sxs-lookup"><span data-stu-id="1fe25-158">posts a message to the Windows application event log that the assembly has been modified with unchecked data in the tables.</span></span> <span data-ttu-id="1fe25-159">さらに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、そのアセンブリに依存するデータを含んでいるすべてのテーブルに、未チェック データを含むテーブルであるというマークを付けます。</span><span class="sxs-lookup"><span data-stu-id="1fe25-159">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] then marks any tables that contain data dependent on the assembly as having unchecked data.</span></span> <span data-ttu-id="1fe25-160">行カタログビューの**has_unchecked_assembly_data**列には、チェックされていないデータを含むテーブルの場合は値1、未チェックデータを含まないテーブルの場合は0が格納され**ます。**</span><span class="sxs-lookup"><span data-stu-id="1fe25-160">The **has_unchecked_assembly_data** column of the **sys.tables** catalog view contains the value 1 for tables that contain unchecked data, and 0 for tables without unchecked data.</span></span>  
  
 <span data-ttu-id="1fe25-161">未チェック データの整合性を解決するには、未チェック データを含む各テーブルに対して DBCC CHECKTABLE を実行します。</span><span class="sxs-lookup"><span data-stu-id="1fe25-161">To resolve the integrity of unchecked data, run DBCC CHECKTABLE against each table that has unchecked data.</span></span> <span data-ttu-id="1fe25-162">DBCC CHECKTABLE が失敗した場合、無効なテーブル行を削除するか、問題を解決できるようにアセンブリ コードを変更して、新たな ALTER ASSEMBLY ステートメントを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fe25-162">If DBCC CHECKTABLE fails, you must either delete the table rows that are not valid or modify the assembly code to address problems, and then issue additional ALTER ASSEMBLY statements.</span></span>  
  
 <span data-ttu-id="1fe25-163">ALTER ASSEMBLY ではアセンブリのバージョンが変更されます。</span><span class="sxs-lookup"><span data-stu-id="1fe25-163">ALTER ASSEMBLY changes the assembly version.</span></span> <span data-ttu-id="1fe25-164">アセンブリのカルチャと公開キートークンは変わりません。SQL Server では、同じ名前、カルチャ、公開キーを持つアセンブリの異なるバージョンを登録することはできません。</span><span class="sxs-lookup"><span data-stu-id="1fe25-164">The culture and public key token of the assembly remain the same.SQL Server does not allow registering different versions of an assembly with the same name, culture and public key.</span></span>  
  
### <a name="interactions-with-computer-wide-policy-for-version-binding"></a><span data-ttu-id="1fe25-165">バージョン バインディングでのコンピューター全体のポリシーとの相互作用</span><span class="sxs-lookup"><span data-stu-id="1fe25-165">Interactions with Computer-wide Policy for Version Binding</span></span>  
 <span data-ttu-id="1fe25-166">パブリッシャー ポリシーまたはコンピューター全体の管理者ポリシーを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に格納されているアセンブリへの参照を特定のバージョンにリダイレクトする場合、次のいずれかを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fe25-166">If references to assemblies stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are redirected to specific versions by using publisher policy or computer-wide administrator policy, you must do either of the following:</span></span>  
  
-   <span data-ttu-id="1fe25-167">リダイレクト先の新しいバージョンがデータベースに格納されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1fe25-167">Make sure the new version to which this redirection is made is in the database.</span></span>  
  
-   <span data-ttu-id="1fe25-168">すべてのステートメントをコンピューターの外部ポリシー ファイルまたはパブリッシャー ポリシーに変更して、データベースに格納されている特定のバージョンがステートメントによって参照されるようにします。</span><span class="sxs-lookup"><span data-stu-id="1fe25-168">Modify any statements to the external policy files of the computer or publisher policy to make sure that they reference the specific version that is in the database.</span></span>  
  
 <span data-ttu-id="1fe25-169">上記のいずれかの操作を実行しないと、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに新しいアセンブリのバージョンをロードできません。</span><span class="sxs-lookup"><span data-stu-id="1fe25-169">Otherwise, an attempt to load a new assembly version to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will fail.</span></span>  
  
 <span data-ttu-id="1fe25-170">**アセンブリのバージョンを更新するには**</span><span class="sxs-lookup"><span data-stu-id="1fe25-170">**To update the version of an assembly**</span></span>  
  
-   [<span data-ttu-id="1fe25-171">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1fe25-171">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="1fe25-172">参照</span><span class="sxs-lookup"><span data-stu-id="1fe25-172">See Also</span></span>  
 <span data-ttu-id="1fe25-173">[アセンブリ &#40;データベースエンジン&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="1fe25-173">[Assemblies &#40;Database Engine&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span></span>  
 [<span data-ttu-id="1fe25-174">アセンブリについての情報の取得</span><span class="sxs-lookup"><span data-stu-id="1fe25-174">Getting Information About Assemblies</span></span>](../../relational-databases/clr-integration/assemblies-getting-information.md)  
  
  
