---
title: オンラインでのインデックス操作の実行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index online operations [SQL Server]
- online index operations
- ONLINE option
ms.assetid: 1e43537c-bf67-4db3-9908-3cb45c6fdaa1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4d09bd99a0eaec5fdb433bd8c33351d7622957a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645052"
---
# <a name="perform-index-operations-online"></a><span data-ttu-id="ea7dc-102">オンラインでのインデックス操作の実行</span><span class="sxs-lookup"><span data-stu-id="ea7dc-102">Perform Index Operations Online</span></span>
  <span data-ttu-id="ea7dc-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、インデックスをオンラインで作成、再構築、または削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-103">This topic describes how to create, rebuild, or drop indexes online in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ea7dc-104">ONLINE オプションにより、このようなインデックス操作中に、基になるテーブルやクラスター化インデックス データ、および関連付けられた任意の非クラスター化インデックスへの同時ユーザー アクセスが可能になります。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-104">The ONLINE option allows concurrent user access to the underlying table or clustered index data and any associated nonclustered indexes during these index operations.</span></span> <span data-ttu-id="ea7dc-105">たとえば、あるユーザーがクラスター化インデックスを再構築している最中に、そのユーザーと他のユーザーが基になるデータの更新やクエリを続行できます。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-105">For example, while a clustered index is being rebuilt by one user, that user and others can continue to update and query the underlying data.</span></span> <span data-ttu-id="ea7dc-106">クラスター化インデックスの構築や再構築などのデータ定義言語 (DDL) 操作をオフラインで実行するときは、これらの操作により、基になるデータや関連付けられたインデックスに排他ロックがかけられます。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-106">When you perform data definition language (DDL) operations offline, such as building or rebuilding a clustered index; these operations hold exclusive locks on the underlying data and associated indexes.</span></span> <span data-ttu-id="ea7dc-107">このため、インデックス操作が完了するまで、基になるデータの変更やクエリを実行できません。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-107">This prevents modifications and queries to the underlying data until the index operation is complete.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ea7dc-108">オンラインでのインデックス操作は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-108">Online index operations are not available in every [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] edition.</span></span> <span data-ttu-id="ea7dc-109">詳しくは「 [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-109">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="ea7dc-110">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="ea7dc-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ea7dc-111">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="ea7dc-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ea7dc-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="ea7dc-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ea7dc-113">Security</span><span class="sxs-lookup"><span data-stu-id="ea7dc-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ea7dc-114">**インデックスをオンラインで再構築するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="ea7dc-114">**To rebuild an index online, using:**</span></span>  
  
     [<span data-ttu-id="ea7dc-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ea7dc-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ea7dc-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ea7dc-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ea7dc-117">はじめに</span><span class="sxs-lookup"><span data-stu-id="ea7dc-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ea7dc-118">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="ea7dc-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="ea7dc-119">1 日 24 時間、週 7 日間、常時稼動のビジネス環境では、オンラインでのインデックス操作を実行することをお勧めします。このような環境では、インデックスの操作中に、ユーザーが同時に操作できることが必要不可欠です。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-119">We recommend performing online index operations for business environments that operate 24 hours a day, seven days a week, in which the need for concurrent user activity during index operations is vital.</span></span>  
  
-   <span data-ttu-id="ea7dc-120">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで、ONLINE オプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-120">The ONLINE option is available in the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
    -   [<span data-ttu-id="ea7dc-121">CREATE INDEX</span><span class="sxs-lookup"><span data-stu-id="ea7dc-121">CREATE INDEX</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
    -   [<span data-ttu-id="ea7dc-122">ALTER INDEX</span><span class="sxs-lookup"><span data-stu-id="ea7dc-122">ALTER INDEX</span></span>](/sql/t-sql/statements/alter-index-transact-sql)  
  
    -   [<span data-ttu-id="ea7dc-123">DROP INDEX</span><span class="sxs-lookup"><span data-stu-id="ea7dc-123">DROP INDEX</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
    -   <span data-ttu-id="ea7dc-124">[ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) (CLUSTERED インデックス オプションが指定されている UNIQUE 制約または PRIMARY KEY 制約を追加または削除するため)</span><span class="sxs-lookup"><span data-stu-id="ea7dc-124">[ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) (To add or drop UNIQUE or PRIMARY KEY constraints with CLUSTERED index option)</span></span>  
  
-   <span data-ttu-id="ea7dc-125">オンラインでのインデックスの作成、再構築、または削除に関する制限と制約については、「 [オンライン インデックス操作のガイドライン](guidelines-for-online-index-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-125">For more limitations and restrictions concerning creating, rebuilding, or dropping indexes online, see [Guidelines for Online Index Operations](guidelines-for-online-index-operations.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ea7dc-126">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ea7dc-126">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ea7dc-127">Permissions</span><span class="sxs-lookup"><span data-stu-id="ea7dc-127">Permissions</span></span>  
 <span data-ttu-id="ea7dc-128">テーブルまたはビューに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-128">Requires ALTER permission on the table or view.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ea7dc-129">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="ea7dc-129">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rebuild-an-index-online"></a><span data-ttu-id="ea7dc-130">インデックスをオンラインで再構築するには</span><span class="sxs-lookup"><span data-stu-id="ea7dc-130">To rebuild an index online</span></span>  
  
1.  <span data-ttu-id="ea7dc-131">オブジェクト エクスプローラーで、インデックスをオンラインで再構築するテーブルが格納されているデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-131">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to rebuild an index online.</span></span>  
  
2.  <span data-ttu-id="ea7dc-132">**[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-132">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="ea7dc-133">プラス記号をクリックして、オンラインでインデックスを再構築するテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-133">Click the plus sign to expand the table on which you want to rebuild an index online.</span></span>  
  
4.  <span data-ttu-id="ea7dc-134">**[インデックス]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-134">Expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="ea7dc-135">オンラインで再構築するインデックスを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-135">Right-click the index that you want to rebuild online and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="ea7dc-136">**[ページの選択]** の **[オプション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-136">Under **Select a page**, select **Options**.</span></span>  
  
7.  <span data-ttu-id="ea7dc-137">**[DML のオンライン処理を許可する]** を選択し、一覧から **[True]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-137">Select **Allow online DML processing**, and then select **True** from the list.</span></span>  
  
8.  <span data-ttu-id="ea7dc-138">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-138">Click **OK**.</span></span>  
  
9. <span data-ttu-id="ea7dc-139">オンラインで再構築するインデックスを右クリックし、 **[再構築]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-139">Right-click the index that you want to rebuild online and select **Rebuild**.</span></span>  
  
10. <span data-ttu-id="ea7dc-140">**[インデックスの再構築]** ダイアログ ボックスで、 **[再構築するインデックス]** グリッドに目的のインデックスが表示されていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-140">In the **Rebuild Indexes** dialog box, verify that the correct index is in the **Indexes to rebuild** grid and click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ea7dc-141">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="ea7dc-141">Using Transact-SQL</span></span>  
  
#### <a name="to-create-rebuild-or-drop-an-index-online"></a><span data-ttu-id="ea7dc-142">インデックスをオンラインで作成、再構築、または削除するには</span><span class="sxs-lookup"><span data-stu-id="ea7dc-142">To create, rebuild, or drop an index online</span></span>  
  
1.  <span data-ttu-id="ea7dc-143">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-143">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ea7dc-144">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-144">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ea7dc-145">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-145">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ea7dc-146">この例では、既存のインデックスをオンラインで再構築します。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-146">The example rebuilds an existing online</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER INDEX AK_Employee_NationalIDNumber ON HumanResources.Employee  
    REBUILD WITH (ONLINE = ON);  
    GO  
    ```  
  
     <span data-ttu-id="ea7dc-147">次の例では、クラスター化インデックスをオンラインで削除し、 `NewGroup` 句を使用することで、結果のテーブル (ヒープ) をファイル グループ `MOVE TO` に移動します。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-147">The following example deletes a clustered index online and moves the resulting table (heap) to the filegroup `NewGroup` by using the `MOVE TO` clause.</span></span> <span data-ttu-id="ea7dc-148">移動の前後で `sys.indexes`、 `sys.tables`、および `sys.filegroups` カタログ ビューを参照し、ファイル グループ内のインデックスとテーブルの配置を確認します。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-148">The `sys.indexes`, `sys.tables`, and `sys.filegroups` catalog views are queried to verify the index and table placement in the filegroups before and after the move.</span></span>  
  
     [!code-sql[IndexDDL#DropIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/dropindex.sql#dropindex4)]  
  
 <span data-ttu-id="ea7dc-149">詳細については、「[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea7dc-149">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
  
