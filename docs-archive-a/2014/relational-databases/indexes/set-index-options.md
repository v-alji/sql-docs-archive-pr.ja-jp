---
title: インデックス オプションの設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- ALLOW_ROW_LOCKS option
- SORT_IN_TEMPDB option
- DROP_EXISTING clause
- large data, indexes
- PAD_INDEX
- STATISTICS_NORECOMPUTE
- MAXDOP index option, setting
- index options [SQL Server]
- MAXDOP index option
- IGNORE_DUP_KEY option
- ALLOW_PAGE_LOCKS option
- ONLINE
ms.assetid: 7969af33-e94c-41f7-ab89-9d9a2747cd5c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9f2d7f0bbbf0d152d3f510ae9ddbe3168634ef96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739961"
---
# <a name="set-index-options"></a><span data-ttu-id="0bb24-102">インデックス オプションの設定</span><span class="sxs-lookup"><span data-stu-id="0bb24-102">Set Index Options</span></span>
  <span data-ttu-id="0bb24-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] におけるインデックスのプロパティを、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0bb24-103">This topic describes how to modify the properties of an index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="0bb24-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="0bb24-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0bb24-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="0bb24-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0bb24-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="0bb24-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0bb24-107">Security</span><span class="sxs-lookup"><span data-stu-id="0bb24-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0bb24-108">**以下を使用してインデックスのプロパティを変更するには:**</span><span class="sxs-lookup"><span data-stu-id="0bb24-108">**To modify the properties of an index, using:**</span></span>  
  
     [<span data-ttu-id="0bb24-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0bb24-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0bb24-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0bb24-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0bb24-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="0bb24-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0bb24-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="0bb24-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="0bb24-113">ALTER INDEX ステートメントに SET 句を使用することによって、ALLOW_PAGE_LOCKS、ALLOW_ROW_LOCKS、IGNORE_DUP_KEY、および STATISTICS_NORECOMPUTE の各オプションが直ちにインデックスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="0bb24-113">The following options are immediately applied to the index by using the SET clause in the ALTER INDEX statement: ALLOW_PAGE_LOCKS, ALLOW_ROW_LOCKS, IGNORE_DUP_KEY, and STATISTICS_NORECOMPUTE.</span></span>  
  
-   <span data-ttu-id="0bb24-114">ALTER INDEX REBUILD または CREATE INDEX WITH DROP_EXISTING を使用してインデックスを再構築するときは、次の各オプションを設定できます:PAD_INDEX、FILLFACTOR、SORT_IN_TEMPDB、IGNORE_DUP_KEY、STATISTICS_NORECOMPUTE、ONLINE、ALLOW_ROW_LOCKS、ALLOW_PAGE_LOCKS、MAXDOP、DROP_EXISTING (CREATE INDEX のみ)。</span><span class="sxs-lookup"><span data-stu-id="0bb24-114">The following options can be set when you rebuild an index by using either ALTER INDEX REBUILD or CREATE INDEX WITH DROP_EXISTING: PAD_INDEX, FILLFACTOR, SORT_IN_TEMPDB, IGNORE_DUP_KEY, STATISTICS_NORECOMPUTE, ONLINE, ALLOW_ROW_LOCKS, ALLOW_PAGE_LOCKS, MAXDOP, and DROP_EXISTING (CREATE INDEX only).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0bb24-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="0bb24-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0bb24-116">Permissions</span><span class="sxs-lookup"><span data-stu-id="0bb24-116">Permissions</span></span>  
 <span data-ttu-id="0bb24-117">テーブルまたはビューに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="0bb24-117">Requires ALTER permission on the table or view.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0bb24-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="0bb24-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-the-properties-of-an-index-in-table-designer"></a><span data-ttu-id="0bb24-119">インデックスのプロパティをテーブル デザイナーで変更するには</span><span class="sxs-lookup"><span data-stu-id="0bb24-119">To modify the properties of an index in Table Designer</span></span>  
  
1.  <span data-ttu-id="0bb24-120">オブジェクト エクスプローラーで、インデックスのプロパティの変更対象となるテーブルが格納されているデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="0bb24-120">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to modify an index's properties.</span></span>  
  
2.  <span data-ttu-id="0bb24-121">プラス記号をクリックして **[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="0bb24-121">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="0bb24-122">インデックスのプロパティを変更するテーブルを右クリックし、 **[デザイン]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0bb24-122">Right-click the table on which you want to modify an index's properties and select **Design**.</span></span>  
  
4.  <span data-ttu-id="0bb24-123">**[テーブル デザイナー]** メニューの **[インデックス/キー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0bb24-123">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="0bb24-124">変更するインデックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="0bb24-124">Select the index that you want to modify.</span></span> <span data-ttu-id="0bb24-125">対応するプロパティがメイン グリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0bb24-125">Its properties will show up in the main grid.</span></span>  
  
6.  <span data-ttu-id="0bb24-126">該当するプロパティの設定を変更してインデックスをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="0bb24-126">Change the settings of any and all properties to customize the index.</span></span>  
  
7.  <span data-ttu-id="0bb24-127">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0bb24-127">Click **Close**.</span></span>  
  
8.  <span data-ttu-id="0bb24-128">**ファイル** メニューの **table_name**_を保存_を選びます。</span><span class="sxs-lookup"><span data-stu-id="0bb24-128">On the **File** menu, select **Save**_table_name_.</span></span>  
  
#### <a name="to-modify-the-properties-of-an-index-in-object-explorer"></a><span data-ttu-id="0bb24-129">インデックスのプロパティをオブジェクト エクスプローラーで変更するには</span><span class="sxs-lookup"><span data-stu-id="0bb24-129">To modify the properties of an index in Object Explorer</span></span>  
  
1.  <span data-ttu-id="0bb24-130">オブジェクト エクスプローラーで、インデックスのプロパティの変更対象となるテーブルが格納されているデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="0bb24-130">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to modify an index's properties.</span></span>  
  
2.  <span data-ttu-id="0bb24-131">プラス記号をクリックして **[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="0bb24-131">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="0bb24-132">インデックスのプロパティを変更するテーブルのプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="0bb24-132">Click the plus sign to expand the table on which you want to modify an index's properties.</span></span>  
  
4.  <span data-ttu-id="0bb24-133">プラス記号をクリックして **[インデックス]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="0bb24-133">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="0bb24-134">プロパティを変更するインデックスを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0bb24-134">Right-click the index of which you want to modify the properties and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="0bb24-135">**[ページの選択]** の **[オプション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0bb24-135">Under **Select a page**, select **Options**.</span></span>  
  
7.  <span data-ttu-id="0bb24-136">該当するプロパティの設定を変更してインデックスをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="0bb24-136">Change the settings of any and all properties to customize the index.</span></span>  
  
8.  <span data-ttu-id="0bb24-137">インデックス列の位置を追加、削除、または変更するには、[**インデックスのプロパティ -** _index_name_] ダイアログ ボックスから **[全般]** ページを選択します。</span><span class="sxs-lookup"><span data-stu-id="0bb24-137">To add, remove, or change the position of an index column, select the **General** page from the **Index Properties -** _index_name_ dialog box.</span></span> <span data-ttu-id="0bb24-138">詳細については、「 [Index Properties F1 Help](index-properties-f1-help.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0bb24-138">For more information, see [Index Properties F1 Help](index-properties-f1-help.md)</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0bb24-139">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="0bb24-139">Using Transact-SQL</span></span>  
  
#### <a name="to-see-the-properties-of-all-the-indexes-in-a-table"></a><span data-ttu-id="0bb24-140">テーブル内のすべてのインデックスのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="0bb24-140">To see the properties of all the indexes in a table</span></span>  
  
1.  <span data-ttu-id="0bb24-141">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="0bb24-141">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0bb24-142">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0bb24-142">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0bb24-143">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0bb24-143">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT i.name AS index_name,   
        i.type_desc,   
        i.is_unique,   
        ds.type_desc AS filegroup_or_partition_scheme,   
        ds.name AS filegroup_or_partition_scheme_name,   
        i.ignore_dup_key,   
        i.is_primary_key,   
        i.is_unique_constraint,   
        i.fill_factor,   
        i.is_padded,   
        i.is_disabled,   
        i.allow_row_locks,   
        i.allow_page_locks,   
        i.has_filter,   
        i.filter_definition  
    FROM sys.indexes AS i  
       INNER JOIN sys.data_spaces AS ds ON i.data_space_id = ds.data_space_id  
    WHERE is_hypothetical = 0 AND i.index_id <> 0   
       AND i.object_id = OBJECT_ID('HumanResources.Employee');   
    GO  
  
    ```  
  
#### <a name="to-set-the-properties-of-an-index"></a><span data-ttu-id="0bb24-144">インデックスのプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="0bb24-144">To set the properties of an index</span></span>  
  
1.  <span data-ttu-id="0bb24-145">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="0bb24-145">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0bb24-146">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0bb24-146">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0bb24-147">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0bb24-147">Copy and paste the following examples into the query window and click **Execute**.</span></span>  
  
     [!code-sql[IndexDDL#AlterIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex4)]  
  
     [!code-sql[IndexDDL#AlterIndex2](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex2)]  
  
 <span data-ttu-id="0bb24-148">詳細については、「[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bb24-148">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
  
