---
title: max degree of parallelism サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- parallel queries [SQL Server]
- processors [SQL Server], parallel queries
- number of processors for parallel queries
- max degree of parallelism option
ms.assetid: 86b65bf1-a6a1-4670-afc0-cdfad1558032
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 824dc837142acc4a0898cb04b4a8687bc5be4043
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642308"
---
# <a name="configure-the-max-degree-of-parallelism-server-configuration-option"></a><span data-ttu-id="2f289-102">max degree of parallelism サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="2f289-102">Configure the max degree of parallelism Server Configuration Option</span></span>
  <span data-ttu-id="2f289-103">このトピック `max degree of parallelism` で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、またはを使用して、のサーバー構成オプションを構成する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="2f289-103">This topic describes how to configure the `max degree of parallelism` server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="2f289-104">複数のマイクロプロセッサまたは CPU が搭載されているコンピューター上で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを実行するときは、並列処理の最適な程度、つまり各並列プラン実行で 1 つのステートメントを実行するために使用するプロセッサの数が検出されます。</span><span class="sxs-lookup"><span data-stu-id="2f289-104">When an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs on a computer that has more than one microprocessor or CPU, it detects the best degree of parallelism, that is, the number of processors employed to run a single statement, for each parallel plan execution.</span></span> <span data-ttu-id="2f289-105">`max degree of parallelism` オプションを使用すると、並列プラン実行で使用するプロセッサの数を制限できます。</span><span class="sxs-lookup"><span data-stu-id="2f289-105">You can use the `max degree of parallelism` option to limit the number of processors to use in parallel plan execution.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="2f289-106">では、クエリ、インデックスデータ定義言語 (DDL) 操作、および静的およびキーセットドリブンカーソルの作成に対して並列実行プランを検討します。</span><span class="sxs-lookup"><span data-stu-id="2f289-106">considers parallel execution plans for queries, index data definition language (DDL) operations, and static and keyset-driven cursor population.</span></span>  
  
 <span data-ttu-id="2f289-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="2f289-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2f289-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="2f289-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2f289-109">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="2f289-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2f289-110">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="2f289-110">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="2f289-111">Security</span><span class="sxs-lookup"><span data-stu-id="2f289-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2f289-112">**以下を使用して max degree of parallelism オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="2f289-112">**To configure the max degree of parallelism option, using:**</span></span>  
  
     [<span data-ttu-id="2f289-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2f289-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2f289-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2f289-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="2f289-115">**補足情報:**  [並列処理の最大限度オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="2f289-115">**Follow Up:**  [After you configure the max degree of parallelism option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2f289-116">はじめに</span><span class="sxs-lookup"><span data-stu-id="2f289-116">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2f289-117">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="2f289-117">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="2f289-118">affinity mask オプションを既定値に設定していないと、対称型多重処理 (SMP) システムで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が使用できるプロセッサの数が制限されることがあります。</span><span class="sxs-lookup"><span data-stu-id="2f289-118">If the affinity mask option is not set to the default, it may restrict the number of processors available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on symmetric multiprocessing (SMP) systems.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="2f289-119">推奨事項</span><span class="sxs-lookup"><span data-stu-id="2f289-119">Recommendations</span></span>  
  
-   <span data-ttu-id="2f289-120">このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術者だけが変更するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="2f289-120">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="2f289-121">サーバーで並列処理の最大限度を特定できるようにするには、このオプションを 0 (既定値) に設定します。</span><span class="sxs-lookup"><span data-stu-id="2f289-121">To enable the server to determine the maximum degree of parallelism, set this option to 0, the default value.</span></span> <span data-ttu-id="2f289-122">並列処理の最大限度を 0 に設定すると、使用可能なすべてのプロセッサ (最大 64 プロセッサ) を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が使用できます。</span><span class="sxs-lookup"><span data-stu-id="2f289-122">Setting maximum degree of parallelism to 0 allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use all the available processors up to 64 processors.</span></span> <span data-ttu-id="2f289-123">並列プランの生成を中止するには、`max degree of parallelism` を 1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="2f289-123">To suppress parallel plan generation, set `max degree of parallelism` to 1.</span></span> <span data-ttu-id="2f289-124">1 つのクエリ実行で使用できるプロセッサ コアの最大数を指定するには、値を 1 ～ 32,767 に設定します。</span><span class="sxs-lookup"><span data-stu-id="2f289-124">Set the value to a number from 1 to 32,767 to specify the maximum number of processor cores that can be used by a single query execution.</span></span> <span data-ttu-id="2f289-125">使用可能なプロセッサ数よりも多い値を指定すると、実際に使用可能なプロセッサ数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2f289-125">If a value greater than the number of available processors is specified, the actual number of available processors is used.</span></span> <span data-ttu-id="2f289-126">コンピューターにプロセッサが 1 つしか搭載されていない場合、`max degree of parallelism` の値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="2f289-126">If the computer has only one processor, the `max degree of parallelism` value is ignored.</span></span>  
  
-   <span data-ttu-id="2f289-127">クエリ ステートメントに MAXDOP クエリ ヒントを指定して、クエリの max degree of parallelism 値をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="2f289-127">You can override the max degree of parallelism value in queries by specifying the MAXDOP query hint in the query statement.</span></span> <span data-ttu-id="2f289-128">詳細については、「[クエリ ヒント &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f289-128">For more information, see [Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query).</span></span>  
  
-   <span data-ttu-id="2f289-129">インデックスを作成または再構築したり、クラスター化インデックスを削除するインデックス操作には、リソースを集中して使用するものがあります。</span><span class="sxs-lookup"><span data-stu-id="2f289-129">Index operations that create or rebuild an index, or that drop a clustered index, can be resource intensive.</span></span> <span data-ttu-id="2f289-130">インデックス ステートメントの MAXDOP インデックス オプションを指定して、インデックス操作の max degree of parallelism 値をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="2f289-130">You can override the max degree of parallelism value for index operations by specifying the MAXDOP index option in the index statement.</span></span> <span data-ttu-id="2f289-131">MAXDOP 値は実行時にステートメントに適用され、インデックス メタデータには保存されません。</span><span class="sxs-lookup"><span data-stu-id="2f289-131">The MAXDOP value is applied to the statement at execution time and is not stored in the index metadata.</span></span> <span data-ttu-id="2f289-132">詳細については、「 [並列インデックス操作の構成](../../relational-databases/indexes/configure-parallel-index-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f289-132">For more information, see [Configure Parallel Index Operations](../../relational-databases/indexes/configure-parallel-index-operations.md).</span></span>  
  
-   <span data-ttu-id="2f289-133">クエリおよびインデックスの操作だけでなく、このオプションも DBCC CHECKTABLE、DBCC CHECKDB、および DBCC CHECKFILEGROUP の並列処理を制御します。</span><span class="sxs-lookup"><span data-stu-id="2f289-133">In addition to queries and index operations, this option also controls the parallelism of DBCC CHECKTABLE, DBCC CHECKDB, and DBCC CHECKFILEGROUP.</span></span> <span data-ttu-id="2f289-134">トレース フラグ 2528 を使用して、これらのステートメントの並列実行プランを無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="2f289-134">You can disable parallel execution plans for these statements by using trace flag 2528.</span></span> <span data-ttu-id="2f289-135">詳細については、「[トレース フラグ &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f289-135">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2f289-136">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2f289-136">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2f289-137">Permissions</span><span class="sxs-lookup"><span data-stu-id="2f289-137">Permissions</span></span>  
 <span data-ttu-id="2f289-138">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="2f289-138">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="2f289-139">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f289-139">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="2f289-140">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="2f289-140">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2f289-141">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="2f289-141">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-max-degree-of-parallelism-option"></a><span data-ttu-id="2f289-142">max degree of parallelism オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="2f289-142">To configure the max degree of parallelism option</span></span>  
  
1.  <span data-ttu-id="2f289-143">**オブジェクト エクスプローラー**で、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f289-143">In **Object Explorer**, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="2f289-144">**[詳細設定]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f289-144">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="2f289-145">**[並列処理の最大限度]** ボックスで、並列プランの実行で使用するプロセッサの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="2f289-145">In the **Max Degree of Parallelism** box, select the maximum number of processors to use in parallel plan execution.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2f289-146">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="2f289-146">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-max-degree-of-parallelism-option"></a><span data-ttu-id="2f289-147">max degree of parallelism オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="2f289-147">To configure the max degree of parallelism option</span></span>  
  
1.  <span data-ttu-id="2f289-148">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="2f289-148">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2f289-149">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f289-149">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2f289-150">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f289-150">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="2f289-151">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して、 `max degree of parallelism` オプションを `8`に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2f289-151">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the `max degree of parallelism` option to `8`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO   
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
EXEC sp_configure 'max degree of parallelism', 8;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
```  
  
 <span data-ttu-id="2f289-152">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f289-152">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-max-degree-of-parallelism-option"></a><a name="FollowUp"></a><span data-ttu-id="2f289-153">補足情報: max degree of parallelism オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="2f289-153">Follow Up: After you configure the max degree of parallelism option</span></span>  
 <span data-ttu-id="2f289-154">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="2f289-154">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f289-155">参照</span><span class="sxs-lookup"><span data-stu-id="2f289-155">See Also</span></span>  
 <span data-ttu-id="2f289-156">[affinity mask サーバー構成オプション](affinity-mask-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="2f289-156">[affinity mask Server Configuration Option](affinity-mask-server-configuration-option.md) </span></span>  
 <span data-ttu-id="2f289-157">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2f289-157">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="2f289-158">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2f289-158">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="2f289-159">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2f289-159">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="2f289-160">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2f289-160">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="2f289-161">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2f289-161">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 <span data-ttu-id="2f289-162">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2f289-162">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 <span data-ttu-id="2f289-163">[DBCC CHECKTABLE &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2f289-163">[DBCC CHECKTABLE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql) </span></span>  
 <span data-ttu-id="2f289-164">[DBCC CHECKDB &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2f289-164">[DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span></span>  
 <span data-ttu-id="2f289-165">[DBCC CHECKFILEGROUP &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkfilegroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2f289-165">[DBCC CHECKFILEGROUP &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkfilegroup-transact-sql) </span></span>  
 <span data-ttu-id="2f289-166">[並列インデックス操作の構成](../../relational-databases/indexes/configure-parallel-index-operations.md) </span><span class="sxs-lookup"><span data-stu-id="2f289-166">[Configure Parallel Index Operations](../../relational-databases/indexes/configure-parallel-index-operations.md) </span></span>  
 <span data-ttu-id="2f289-167">[クエリ ヒント &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span><span class="sxs-lookup"><span data-stu-id="2f289-167">[Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span></span>  
 [<span data-ttu-id="2f289-168">インデックス オプションの設定</span><span class="sxs-lookup"><span data-stu-id="2f289-168">Set Index Options</span></span>](../../relational-databases/indexes/set-index-options.md)  
  
  
