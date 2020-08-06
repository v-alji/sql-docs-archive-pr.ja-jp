---
title: index create memory サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- index create memory option
ms.assetid: 3d722d9b-bada-4bf5-a9d7-bfc556bb4915
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6cd0aeb93d3fb68089338335068fdaaae19919fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715698"
---
# <a name="configure-the-index-create-memory-server-configuration-option"></a><span data-ttu-id="b3b80-102">index create memory サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="b3b80-102">Configure the index create memory Server Configuration Option</span></span>
  <span data-ttu-id="b3b80-103">このトピックでは、 **で** または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] index create memory [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b3b80-103">This topic describes how to configure the **index create memory** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="b3b80-104">**index create memory** オプションは、インデックス作成用として最初に割り当てられる最大メモリ容量を制御します。</span><span class="sxs-lookup"><span data-stu-id="b3b80-104">The **index create memory** option controls the maximum amount of memory initially allocated for creating indexes.</span></span> <span data-ttu-id="b3b80-105">このオプションの既定値は 0 (自己構成) です。</span><span class="sxs-lookup"><span data-stu-id="b3b80-105">The default value for this option is 0 (self-configuring).</span></span> <span data-ttu-id="b3b80-106">その後、インデックスを作成するためにより多くのメモリが必要になった場合、メモリ容量を確保できるのであれば、サーバーはそのメモリを使用します。したがって、使用メモリ容量がこのオプションの設定値を超えることになります。</span><span class="sxs-lookup"><span data-stu-id="b3b80-106">If more memory is later needed for index creation and the memory is available, the server will use it; thereby, exceeding the setting of this option.</span></span> <span data-ttu-id="b3b80-107">追加メモリを確保できない場合は、既に割り当てられているメモリを使用してインデックス作成が続行されます。</span><span class="sxs-lookup"><span data-stu-id="b3b80-107">If additional memory is not available, the index creation will continue using the memory already allocated.</span></span>  
  
 <span data-ttu-id="b3b80-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="b3b80-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b3b80-109">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="b3b80-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b3b80-110">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="b3b80-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b3b80-111">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="b3b80-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="b3b80-112">Security</span><span class="sxs-lookup"><span data-stu-id="b3b80-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b3b80-113">**以下を使用して index create memory オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="b3b80-113">**To configure the index create memory option, using:**</span></span>  
  
     [<span data-ttu-id="b3b80-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b3b80-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b3b80-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b3b80-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="b3b80-116">**補足情報:** [index create memory オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="b3b80-116">**Follow Up:**  [After you configure the index create memory option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b3b80-117">はじめに</span><span class="sxs-lookup"><span data-stu-id="b3b80-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b3b80-118">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="b3b80-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="b3b80-119">**min memory per query** オプションの設定は、**index create memory** オプションよりも優先順位が高くなります。</span><span class="sxs-lookup"><span data-stu-id="b3b80-119">The setting of the **min memory per query** option has precedence over the **index create memory** option.</span></span> <span data-ttu-id="b3b80-120">両方のオプションを変更し、 **index create memory** の設定値を **min memory per query**より小さくした場合は、警告メッセージが表示されます。ただし、値はそのまま設定されます。</span><span class="sxs-lookup"><span data-stu-id="b3b80-120">If you change both options and the **index create memory** is less than **min memory per query**, you receive a warning message, but the value is set.</span></span> <span data-ttu-id="b3b80-121">クエリ実行中にも同様の警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b3b80-121">During query execution, you receive a similar warning.</span></span>  
  
-   <span data-ttu-id="b3b80-122">パーティション テーブルとパーティション インデックスを使用する場合、パーティション インデックスが未整理であったり、並列処理の頻度が高かったりすると、インデックスの作成に必要な最小メモリ容量が大幅に増加します。</span><span class="sxs-lookup"><span data-stu-id="b3b80-122">When using partitioned tables and indexes, the minimum memory requirements for index creation may increase significantly if there are non-aligned partitioned indexes and a high degree of parallelism.</span></span> <span data-ttu-id="b3b80-123">このオプションを使用して、1 回のインデックス作成操作ですべてのインデックス パーティションに最初に割り当てられる合計メモリ容量を指定できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="b3b80-123">This option controls the total initial amount of memory allocated for all index partitions in a single index creation operation.</span></span> <span data-ttu-id="b3b80-124">このオプションで指定したメモリ容量が、クエリの実行に必要となる最小メモリ容量より小さい場合は、クエリの実行が中止され、エラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b3b80-124">The query will terminate with an error message if the amount set by this option is less than the minimum required to run the query.</span></span>  
  
-   <span data-ttu-id="b3b80-125">このオプションの実行値は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているオペレーティング システムおよびハードウェア プラットフォームで実際に確保できるメモリ容量を超えることはありません。</span><span class="sxs-lookup"><span data-stu-id="b3b80-125">The run value for this option will not exceed the actual amount of memory that can be used for the operating system and hardware platform on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span> <span data-ttu-id="b3b80-126">32 ビット オペレーティング システムの場合、実行値は 3 GB より小さくなります。</span><span class="sxs-lookup"><span data-stu-id="b3b80-126">On 32-bit operating systems, the run value will be less than 3 gigabytes (GB).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="b3b80-127">推奨事項</span><span class="sxs-lookup"><span data-stu-id="b3b80-127">Recommendations</span></span>  
  
-   <span data-ttu-id="b3b80-128">このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術者だけが変更するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="b3b80-128">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="b3b80-129">**index create memory** オプションは自動的に設定されるので、通常は調整する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="b3b80-129">The **index create memory** option is self-configuring and usually works without requiring adjustment.</span></span> <span data-ttu-id="b3b80-130">ただし、インデックスを正常に作成できない場合は、必要に応じて、このオプションの値を実行値より大きくしてください。</span><span class="sxs-lookup"><span data-stu-id="b3b80-130">However, if you experience difficulties creating indexes, consider increasing the value of this option from its run value.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b3b80-131">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="b3b80-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b3b80-132">Permissions</span><span class="sxs-lookup"><span data-stu-id="b3b80-132">Permissions</span></span>  
 <span data-ttu-id="b3b80-133">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="b3b80-133">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="b3b80-134">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3b80-134">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="b3b80-135">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="b3b80-135">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b3b80-136">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="b3b80-136">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-index-create-memory-option"></a><span data-ttu-id="b3b80-137">index create memory オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="b3b80-137">To configure the index create memory option</span></span>  
  
1.  <span data-ttu-id="b3b80-138">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3b80-138">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="b3b80-139">**[メモリ]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3b80-139">Click the **Memory** node.</span></span>  
  
3.  <span data-ttu-id="b3b80-140">**[インデックス作成メモリ]** で、index create memory オプションの目的の値を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="b3b80-140">Under **Index creation memory**, type or select the desired value for the index create memory option.</span></span>  
  
     <span data-ttu-id="b3b80-141">**index create memory** オプションは、インデックス作成時の並べ替えに使用するメモリの量を制御する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="b3b80-141">Use the **index create memory** option to control the amount of memory used by index creation sorts.</span></span> <span data-ttu-id="b3b80-142">**index create memory** オプションは自動構成型で、ほとんどの場合、調整を行わなくても機能します。</span><span class="sxs-lookup"><span data-stu-id="b3b80-142">The **index create memory** option is self-configuring and should work in most cases without requiring adjustment.</span></span> <span data-ttu-id="b3b80-143">ただし、インデックスを正常に作成できない場合は、必要に応じて、このオプションの値を実行値より大きくしてください。</span><span class="sxs-lookup"><span data-stu-id="b3b80-143">However, if you experience difficulties creating indexes, consider increasing the value of this option from its run value.</span></span> <span data-ttu-id="b3b80-144">クエリの並べ替えは、 **min memory per query** オプションを使用して制御します。</span><span class="sxs-lookup"><span data-stu-id="b3b80-144">Query sorts are controlled through the **min memory per query** option.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b3b80-145">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="b3b80-145">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-index-create-memory-option"></a><span data-ttu-id="b3b80-146">index create memory オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="b3b80-146">To configure the index create memory option</span></span>  
  
1.  <span data-ttu-id="b3b80-147">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="b3b80-147">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b3b80-148">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3b80-148">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b3b80-149">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3b80-149">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="b3b80-150">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して、 `index create memory` オプションの値を `4096`に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b3b80-150">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `index create memory` option to `4096`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
EXEC sp_configure 'index create memory', 4096  
GO  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="b3b80-151">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3b80-151">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-index-create-memory-option"></a><a name="FollowUp"></a><span data-ttu-id="b3b80-152">補足情報: index create memory オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="b3b80-152">Follow Up: After you configure the index create memory option</span></span>  
 <span data-ttu-id="b3b80-153">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="b3b80-153">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3b80-154">参照</span><span class="sxs-lookup"><span data-stu-id="b3b80-154">See Also</span></span>  
 <span data-ttu-id="b3b80-155">[sys.configurations &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b3b80-155">[sys.configurations &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) </span></span>  
 <span data-ttu-id="b3b80-156">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b3b80-156">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="b3b80-157">[サーバー メモリに関するサーバー構成オプション](server-memory-server-configuration-options.md) </span><span class="sxs-lookup"><span data-stu-id="b3b80-157">[Server Memory Server Configuration Options](server-memory-server-configuration-options.md) </span></span>  
 <span data-ttu-id="b3b80-158">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b3b80-158">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="b3b80-159">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b3b80-159">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
