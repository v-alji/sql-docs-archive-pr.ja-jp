---
title: インデックスと制約の有効化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- indexes [SQL Server], enabling
- nonclustered indexes [SQL Server], enabling a disabled index
- index enabling [SQL Server]
- disabled indexes [SQL Server], how to enable
- constraints [SQL Server], enabling
- clustered indexes, enabling disabled indexes
ms.assetid: c55c8865-322e-4ab0-ba04-ea1f56735353
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4d4e79689b80a40d00958fa557fe51df2adf9c14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645068"
---
# <a name="enable-indexes-and-constraints"></a><span data-ttu-id="68c0d-102">インデックスと制約の有効化</span><span class="sxs-lookup"><span data-stu-id="68c0d-102">Enable Indexes and Constraints</span></span>
  <span data-ttu-id="68c0d-103">このトピックでは、無効にされている [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインデックスを、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して有効にする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-103">This topic describes how to enable a disabled index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="68c0d-104">無効にされたインデックスは、再構築されるか削除されるまで無効な状態のままとなります。</span><span class="sxs-lookup"><span data-stu-id="68c0d-104">After an index is disabled, it remains in a disabled state until it is rebuilt or dropped</span></span>  
  
 <span data-ttu-id="68c0d-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="68c0d-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="68c0d-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="68c0d-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="68c0d-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="68c0d-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="68c0d-108">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="68c0d-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="68c0d-109">**以下を使用して無効なインデックスを有効にするには:**</span><span class="sxs-lookup"><span data-stu-id="68c0d-109">**To enable a disabled index, using:**</span></span>  
  
     [<span data-ttu-id="68c0d-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="68c0d-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="68c0d-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="68c0d-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="68c0d-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="68c0d-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="68c0d-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="68c0d-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="68c0d-114">インデックスの再構築後、インデックスを無効にしたために無効になった制約を手動で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="68c0d-114">After rebuilding the index, any constraints that were disabled because of disabling the index must be manually enabled.</span></span> <span data-ttu-id="68c0d-115">PRIMARY KEY 制約と UNIQUE 制約については、関連するインデックスを再構築すると有効になります。</span><span class="sxs-lookup"><span data-stu-id="68c0d-115">PRIMARY KEY and UNIQUE constraints are enabled by rebuilding the associated index.</span></span> <span data-ttu-id="68c0d-116">このインデックスを再構築しないと、PRIMARY KEY 制約や UNIQUE 制約を参照する FOREIGN KEY 制約を有効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="68c0d-116">This index must be rebuilt (enabled) before you can enable FOREIGN KEY constraints that reference the PRIMARY KEY or UNIQUE constraint.</span></span> <span data-ttu-id="68c0d-117">FOREIGN KEY 制約を有効にするには、ALTER TABLE CHECK CONSTRAINT ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-117">FOREIGN KEY constraints are enabled by using the ALTER TABLE CHECK CONSTRAINT statement.</span></span>  
  
-   <span data-ttu-id="68c0d-118">ONLINE オプションが ON に設定されている場合、無効化されたクラスター化インデックスを再構築することはできません。</span><span class="sxs-lookup"><span data-stu-id="68c0d-118">Rebuilding a disabled clustered index cannot be performed when the ONLINE option is set to ON.</span></span>  
  
-   <span data-ttu-id="68c0d-119">クラスター化インデックスが無効または有効で、非クラスター化インデックスが無効になっている場合、クラスター化インデックスの操作により、無効化された非クラスター化インデックスには、次のような影響があります。</span><span class="sxs-lookup"><span data-stu-id="68c0d-119">When the clustered index is disabled or enabled and the nonclustered index is disabled, the clustered index action has the following results on the disabled nonclustered index.</span></span>  
  
    |<span data-ttu-id="68c0d-120">クラスター化インデックスの操作</span><span class="sxs-lookup"><span data-stu-id="68c0d-120">Clustered Index Action</span></span>|<span data-ttu-id="68c0d-121">無効化された非クラスター化インデックス</span><span class="sxs-lookup"><span data-stu-id="68c0d-121">Disabled Nonclustered Index ...</span></span>|  
    |----------------------------|-----------------------------------|  
    |<span data-ttu-id="68c0d-122">ALTER INDEX REBUILD</span><span class="sxs-lookup"><span data-stu-id="68c0d-122">ALTER INDEX REBUILD.</span></span>|<span data-ttu-id="68c0d-123">無効化されたままです。</span><span class="sxs-lookup"><span data-stu-id="68c0d-123">Remains disabled.</span></span>|  
    |<span data-ttu-id="68c0d-124">ALTER INDEX ALL REBUILD</span><span class="sxs-lookup"><span data-stu-id="68c0d-124">ALTER INDEX ALL REBUILD.</span></span>|<span data-ttu-id="68c0d-125">再構築され、有効になります。</span><span class="sxs-lookup"><span data-stu-id="68c0d-125">Is rebuilt and enabled.</span></span>|  
    |<span data-ttu-id="68c0d-126">DROP INDEX</span><span class="sxs-lookup"><span data-stu-id="68c0d-126">DROP INDEX.</span></span>|<span data-ttu-id="68c0d-127">無効化されたままです。</span><span class="sxs-lookup"><span data-stu-id="68c0d-127">Remains disabled.</span></span>|  
    |<span data-ttu-id="68c0d-128">CREATE INDEX WITH DROP_EXISTING</span><span class="sxs-lookup"><span data-stu-id="68c0d-128">CREATE INDEX WITH DROP_EXISTING.</span></span>|<span data-ttu-id="68c0d-129">無効化されたままです。</span><span class="sxs-lookup"><span data-stu-id="68c0d-129">Remains disabled.</span></span>|  
  
     <span data-ttu-id="68c0d-130">新しいクラスター化インデックスの作成操作による影響は ALTER INDEX ALL REBUILD と同じです。</span><span class="sxs-lookup"><span data-stu-id="68c0d-130">Creating a new clustered index, behaves the same as ALTER INDEX ALL REBUILD.</span></span>  
  
-   <span data-ttu-id="68c0d-131">クラスター化インデックスに関連付けられらている非クラスター化インデックスに対して実行できる操作は、これらのインデックスの状態が無効であるか有効であるかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="68c0d-131">Allowed actions on nonclustered indexes associated with a clustered index depend on the state, whether disabled or enabled, of both index types.</span></span> <span data-ttu-id="68c0d-132">次の表に、非クラスター化インデックスに対して実行できる操作を示します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-132">The following table summarizes the allowed actions on nonclustered indexes.</span></span>  
  
    |<span data-ttu-id="68c0d-133">非クラスター化インデックスの操作</span><span class="sxs-lookup"><span data-stu-id="68c0d-133">Nonclustered Index Action</span></span>|<span data-ttu-id="68c0d-134">クラスター化インデックスと非クラスター化インデックスの両方が無効な場合</span><span class="sxs-lookup"><span data-stu-id="68c0d-134">When both the clustered and nonclustered indexes are disabled.</span></span>|<span data-ttu-id="68c0d-135">クラスター化インデックスが有効で、非クラスター化インデックスが無効または有効な場合</span><span class="sxs-lookup"><span data-stu-id="68c0d-135">When the clustered index is enabled and the nonclustered index is in either state.</span></span>|  
    |-------------------------------|--------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
    |<span data-ttu-id="68c0d-136">ALTER INDEX REBUILD</span><span class="sxs-lookup"><span data-stu-id="68c0d-136">ALTER INDEX REBUILD.</span></span>|<span data-ttu-id="68c0d-137">操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-137">The action fails.</span></span>|<span data-ttu-id="68c0d-138">操作は成功します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-138">The action succeeds.</span></span>|  
    |<span data-ttu-id="68c0d-139">DROP INDEX</span><span class="sxs-lookup"><span data-stu-id="68c0d-139">DROP INDEX.</span></span>|<span data-ttu-id="68c0d-140">操作は成功します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-140">The action succeeds.</span></span>|<span data-ttu-id="68c0d-141">操作は成功します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-141">The action succeeds.</span></span>|  
    |<span data-ttu-id="68c0d-142">CREATE INDEX WITH DROP_EXISTING</span><span class="sxs-lookup"><span data-stu-id="68c0d-142">CREATE INDEX WITH DROP_EXISTING.</span></span>|<span data-ttu-id="68c0d-143">操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-143">The action fails.</span></span>|<span data-ttu-id="68c0d-144">操作は成功します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-144">The action succeeds.</span></span>|  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="68c0d-145">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="68c0d-145">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="68c0d-146">Permissions</span><span class="sxs-lookup"><span data-stu-id="68c0d-146">Permissions</span></span>  
 <span data-ttu-id="68c0d-147">テーブルまたはビューに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="68c0d-147">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="68c0d-148">DBCC DBREINDEX を使用している場合、ユーザーはテーブルを所有しているか、 **sysadmin** 固定サーバー ロールのメンバーであるか、 **db_ddladmin** 固定データベース ロールおよび **db_owner** 固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="68c0d-148">If using DBCC DBREINDEX, eser must either own the table or be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="68c0d-149">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="68c0d-149">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-enable-a-disabled-index"></a><span data-ttu-id="68c0d-150">無効なインデックスを有効にするには</span><span class="sxs-lookup"><span data-stu-id="68c0d-150">To enable a disabled index</span></span>  
  
1.  <span data-ttu-id="68c0d-151">オブジェクト エクスプローラーで、インデックスを有効にするテーブルが格納されているデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-151">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to enable an index.</span></span>  
  
2.  <span data-ttu-id="68c0d-152">プラス記号をクリックして **[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-152">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="68c0d-153">プラス記号をクリックして、インデックスを有効にするテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-153">Click the plus sign to expand the table on which you want to enable an index.</span></span>  
  
4.  <span data-ttu-id="68c0d-154">プラス記号をクリックして **[インデックス]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-154">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="68c0d-155">有効にするインデックスを右クリックし、 **[再構築]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-155">Right-click the index you want to enable and select **Rebuild**.</span></span>  
  
6.  <span data-ttu-id="68c0d-156">**[インデックスの再構築]** ダイアログ ボックスで、 **[再構築するインデックス]** グリッドに目的のインデックスが表示されていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68c0d-156">In the **Rebuild Indexes** dialog box, verify that the correct index is in the **Indexes to rebuild** grid and click **OK**.</span></span>  
  
#### <a name="to-enable-all-indexes-on-a-table"></a><span data-ttu-id="68c0d-157">テーブルのすべてのインデックスを有効にするには</span><span class="sxs-lookup"><span data-stu-id="68c0d-157">To enable all indexes on a table</span></span>  
  
1.  <span data-ttu-id="68c0d-158">オブジェクト エクスプローラーで、インデックスを有効にするテーブルが格納されているデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-158">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to enable the indexes.</span></span>  
  
2.  <span data-ttu-id="68c0d-159">プラス記号をクリックして **[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-159">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="68c0d-160">プラス記号をクリックして、インデックスを有効にするテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-160">Click the plus sign to expand the table on which you want to enable the indexes.</span></span>  
  
4.  <span data-ttu-id="68c0d-161">**[インデックス]** フォルダーを右クリックし、 **[すべて再構築]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-161">Right-click the **Indexes** folder and select **Rebuild All**.</span></span>  
  
5.  <span data-ttu-id="68c0d-162">**[インデックスの再構築]** ダイアログ ボックスで、 **[再構築するインデックス]** グリッドに目的のインデックスが表示されていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68c0d-162">In the **Rebuild Indexes** dialog box, verify that the correct indexes are in the **Indexes to rebuild** grid and click **OK**.</span></span> <span data-ttu-id="68c0d-163">**[再構築するインデックス]** グリッドからインデックスを削除するには、インデックスを選択し、Del キーを押します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-163">To remove an index from the **Indexes to rebuild** grid, select the index and then press the Delete key.</span></span>  
  
 <span data-ttu-id="68c0d-164">**[インデックスの再構築]** ダイアログ ボックスには、次の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="68c0d-164">The following information is available in the **Rebuild Indexes** dialog box:</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="68c0d-165">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="68c0d-165">Using Transact-SQL</span></span>  
  
#### <a name="to-enable-a-disabled-index-using-alter-index"></a><span data-ttu-id="68c0d-166">無効にされたインデックスを ALTER INDEX を使用して有効にするには</span><span class="sxs-lookup"><span data-stu-id="68c0d-166">To enable a disabled index using ALTER INDEX</span></span>  
  
1.  <span data-ttu-id="68c0d-167">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-167">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="68c0d-168">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68c0d-168">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="68c0d-169">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68c0d-169">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Enables the IX_Employee_OrganizationLevel_OrganizationNode index  
    -- on the HumanResources.Employee table.  
  
    ALTER INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
    REBUILD;   
    GO  
    ```  
  
#### <a name="to-enable-a-disabled-index-using-create-index"></a><span data-ttu-id="68c0d-170">無効にされたインデックスを CREATE INDEX を使用して有効にするには</span><span class="sxs-lookup"><span data-stu-id="68c0d-170">To enable a disabled index using CREATE INDEX</span></span>  
  
1.  <span data-ttu-id="68c0d-171">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-171">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="68c0d-172">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68c0d-172">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="68c0d-173">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68c0d-173">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- re-creates the IX_Employee_OrganizationLevel_OrganizationNode index  
    -- on the HumanResources.Employee table  
    -- using the OrganizationLevel and OrganizationNode columns  
    -- and then deletes the existing IX_Employee_OrganizationLevel_OrganizationNode index  
    CREATE INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
       (OrganizationLevel, OrganizationNode)  
    WITH (DROP_EXISTING = ON);  
    GO  
    ```  
  
#### <a name="to-enable-a-disabled-index-using-dbcc-dbreindex"></a><span data-ttu-id="68c0d-174">無効にされたインデックスを DBCC DBREINDEX を使用して有効にするには</span><span class="sxs-lookup"><span data-stu-id="68c0d-174">To enable a disabled index using DBCC DBREINDEX</span></span>  
  
1.  <span data-ttu-id="68c0d-175">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-175">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="68c0d-176">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68c0d-176">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="68c0d-177">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68c0d-177">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- enables the IX_Employee_OrganizationLevel_OrganizationNode index  
    -- on the HumanResources.Employee table  
    DBCC DBREINDEX ("HumanResources.Employee", IX_Employee_OrganizationLevel_OrganizationNode);  
    GO  
    ```  
  
#### <a name="to-enable-all-indexes-on-a-table-using-alter-index"></a><span data-ttu-id="68c0d-178">テーブル上のすべてのインデックスを ALTER INDEX を使用して有効にするには</span><span class="sxs-lookup"><span data-stu-id="68c0d-178">To enable all indexes on a table using ALTER INDEX</span></span>  
  
1.  <span data-ttu-id="68c0d-179">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-179">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="68c0d-180">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68c0d-180">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="68c0d-181">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68c0d-181">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- enables all indexes  
    -- on the HumanResources.Employee table  
    ALTER INDEX ALL ON HumanResources.Employee  
    REBUILD;  
    GO  
    ```  
  
#### <a name="to-enable-all-indexes-on-a-table-using-dbcc-dbreindex"></a><span data-ttu-id="68c0d-182">テーブル上のすべてのインデックスを DBCC DBREINDEX を使用して有効にするには</span><span class="sxs-lookup"><span data-stu-id="68c0d-182">To enable all indexes on a table using DBCC DBREINDEX</span></span>  
  
1.  <span data-ttu-id="68c0d-183">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="68c0d-183">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="68c0d-184">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68c0d-184">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="68c0d-185">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68c0d-185">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- enables all indexes  
    -- on the HumanResources.Employee table  
    DBCC DBREINDEX ("HumanResources.Employee", " ");  
    GO  
    ```  
  
 <span data-ttu-id="68c0d-186">詳細については、「[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)」、「[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)」、および「[DBCC DBREINDEX &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68c0d-186">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql), [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql), and [DBCC DBREINDEX &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql).</span></span>  
  
  
