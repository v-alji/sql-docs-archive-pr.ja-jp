---
title: 付加列インデックスの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index size [SQL Server]
- index keys [SQL Server]
- index columns [SQL Server]
- size [SQL Server], indexes
- key columns [SQL Server]
- included columns
- nonclustered indexes [SQL Server], included columns
- designing indexes [SQL Server], included columns
- nonkey columns
ms.assetid: d198648d-fea5-416d-9f30-f9d4aebbf4ec
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e5a464f9791ea635236069555647229bf1f0d79e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740950"
---
# <a name="create-indexes-with-included-columns"></a><span data-ttu-id="1b247-102">付加列インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="1b247-102">Create Indexes with Included Columns</span></span>
  <span data-ttu-id="1b247-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用し、付加列 (非キー列) を追加して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]の非クラスター化インデックスの機能を拡張する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b247-103">This topic describes how to add included (or nonkey) columns to extend the functionality of nonclustered indexes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="1b247-104">非キー列を含めることにより、より多くのクエリをカバーする非クラスター化インデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1b247-104">By including nonkey columns, you can create nonclustered indexes that cover more queries.</span></span> <span data-ttu-id="1b247-105">これは、非キー列には次の利点があるためです。</span><span class="sxs-lookup"><span data-stu-id="1b247-105">This is because the nonkey columns have the following benefits:</span></span>  
  
-   <span data-ttu-id="1b247-106">非キー列には、インデックス キー列として許可されていないデータ型を設定できる。</span><span class="sxs-lookup"><span data-stu-id="1b247-106">They can be data types not allowed as index key columns.</span></span>  
  
-   <span data-ttu-id="1b247-107">インデックス キー列の数やインデックス キーのサイズを計算するときに、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] では非キー列が考慮されない。</span><span class="sxs-lookup"><span data-stu-id="1b247-107">They are not considered by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] when calculating the number of index key columns or index key size.</span></span>  
  
 <span data-ttu-id="1b247-108">クエリ内のすべての列が、キー列または非キー列としてインデックスに含まれるているとき、非キー列を含むインデックスにより、クエリ パフォーマンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="1b247-108">An index with nonkey columns can significantly improve query performance when all columns in the query are included in the index either as key or nonkey columns.</span></span> <span data-ttu-id="1b247-109">クエリ オプティマイザーではインデックス内のすべての列値を参照できるので、テーブルやクラスター化インデックスのデータにアクセスすることがなく、ディスク I/O 操作が少なくて済むため、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="1b247-109">Performance gains are achieved because the query optimizer can locate all the column values within the index; table or clustered index data is not accessed resulting in fewer disk I/O operations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1b247-110">クエリによって参照されるすべての列がインデックスに含まれているときは、一般的に、そのインデックスは *クエリをカバーしている*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="1b247-110">When an index contains all the columns referenced by a query it is typically referred to as *covering the query*.</span></span>  
  
 <span data-ttu-id="1b247-111">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="1b247-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1b247-112">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="1b247-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1b247-113">設計に関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="1b247-113">Design Recommendations</span></span>](#DesignRecs)  
  
     [<span data-ttu-id="1b247-114">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="1b247-114">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1b247-115">Security</span><span class="sxs-lookup"><span data-stu-id="1b247-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1b247-116">**以下を使用して非キー列を含むインデックスを作成するには:**</span><span class="sxs-lookup"><span data-stu-id="1b247-116">**To create an index with nonkey columns, using:**</span></span>  
  
     [<span data-ttu-id="1b247-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1b247-117">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1b247-118">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1b247-118">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1b247-119">はじめに</span><span class="sxs-lookup"><span data-stu-id="1b247-119">Before You Begin</span></span>  
  
###  <a name="design-recommendations"></a><a name="DesignRecs"></a> <span data-ttu-id="1b247-120">設計上の推奨事項</span><span class="sxs-lookup"><span data-stu-id="1b247-120">Design Recommendations</span></span>  
  
-   <span data-ttu-id="1b247-121">検索や参照に使用される列のみがキー列になるように、大きなサイズのインデックス キーを使用して、非クラスター化インデックスを設計し直します。</span><span class="sxs-lookup"><span data-stu-id="1b247-121">Redesign nonclustered indexes with a large index key size so that only columns used for searching and lookups are key columns.</span></span> <span data-ttu-id="1b247-122">クエリをカバーする他のすべての列を非キー列にします。</span><span class="sxs-lookup"><span data-stu-id="1b247-122">Make all other columns that cover the query into nonkey columns.</span></span> <span data-ttu-id="1b247-123">その結果、クエリをカバーするために必要なすべての列を含むことができますが、インデックス キー自体は小さく、効率的です。</span><span class="sxs-lookup"><span data-stu-id="1b247-123">In this way, you will have all columns needed to cover the query, but the index key itself is small and efficient.</span></span>  
  
-   <span data-ttu-id="1b247-124">非クラスター化インデックスに非キー列を含め、現在のインデックス サイズの制限 (最大 16 個のキー列と最大 900 バイトのインデックス キーのサイズ) を超えないようにします。</span><span class="sxs-lookup"><span data-stu-id="1b247-124">Include nonkey columns in a nonclustered index to avoid exceeding the current index size limitations of a maximum of 16 key columns and a maximum index key size of 900 bytes.</span></span> <span data-ttu-id="1b247-125">インデックス キー列の数やインデックス キーのサイズを計算するときに、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] では非キー列が考慮されません。</span><span class="sxs-lookup"><span data-stu-id="1b247-125">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] does not consider nonkey columns when calculating the number of index key columns or index key size.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1b247-126">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="1b247-126">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="1b247-127">非キー列を定義できるのは、クラスター化されていないインデックスだけです。</span><span class="sxs-lookup"><span data-stu-id="1b247-127">Nonkey columns can only be defined on nonclustered indexes.</span></span>  
  
-   <span data-ttu-id="1b247-128">`text`、`ntext`、および `image` を除くすべてのデータ型は、非キー列として使用できます。</span><span class="sxs-lookup"><span data-stu-id="1b247-128">All data types except `text`, `ntext`, and `image` can be used as nonkey columns.</span></span>  
  
-   <span data-ttu-id="1b247-129">決定的な計算列は、正確かどうかに関係なく、非キー列にすることができます。</span><span class="sxs-lookup"><span data-stu-id="1b247-129">Computed columns that are deterministic and either precise or imprecise can be nonkey columns.</span></span> <span data-ttu-id="1b247-130">詳細については、「 [計算列のインデックス](indexes-on-computed-columns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b247-130">For more information, see [Indexes on Computed Columns](indexes-on-computed-columns.md).</span></span>  
  
-   <span data-ttu-id="1b247-131">計算列が `image`、`ntext`、および `text` の各データ型から派生している場合は、計算列のデータ型が非キー インデックス列として許可されている限り、非キー列にできます。</span><span class="sxs-lookup"><span data-stu-id="1b247-131">Computed columns derived from `image`, `ntext`, and `text` data types can be nonkey columns as long as the computed column data type is allowed as a nonkey index column.</span></span>  
  
-   <span data-ttu-id="1b247-132">インデックスを先に削除しない限り、非キー列をテーブルから削除できません。</span><span class="sxs-lookup"><span data-stu-id="1b247-132">Nonkey columns cannot be dropped from a table unless that table's index is dropped first.</span></span>  
  
-   <span data-ttu-id="1b247-133">次の操作以外に、非キー列は変更できません。</span><span class="sxs-lookup"><span data-stu-id="1b247-133">Nonkey columns cannot be changed, except to do the following:</span></span>  
  
    -   <span data-ttu-id="1b247-134">列の NULL 値の許容を NOT NULL から NULL に変更する。</span><span class="sxs-lookup"><span data-stu-id="1b247-134">Change the nullability of the column from NOT NULL to NULL.</span></span>  
  
    -   <span data-ttu-id="1b247-135">`varchar`、`nvarchar`、または `varbinary` の各列の長さを拡張する。</span><span class="sxs-lookup"><span data-stu-id="1b247-135">Increase the length of `varchar`, `nvarchar`, or `varbinary` columns.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1b247-136">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1b247-136">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1b247-137">Permissions</span><span class="sxs-lookup"><span data-stu-id="1b247-137">Permissions</span></span>  
 <span data-ttu-id="1b247-138">テーブルまたはビューに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="1b247-138">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="1b247-139">実行するには、 **sysadmin** 固定サーバー ロール、または **db_ddladmin** 固定データベース ロールおよび **db_owner** 固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b247-139">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1b247-140">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="1b247-140">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-an-index-with-nonkey-columns"></a><span data-ttu-id="1b247-141">非キー列を含むインデックスを作成するには</span><span class="sxs-lookup"><span data-stu-id="1b247-141">To create an index with nonkey columns</span></span>  
  
1.  <span data-ttu-id="1b247-142">オブジェクト エクスプローラーで、非キー列を含むインデックスの作成先となるテーブルが格納されているデータベースを、プラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="1b247-142">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to create an index with nonkey columns.</span></span>  
  
2.  <span data-ttu-id="1b247-143">プラス記号をクリックして **[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="1b247-143">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="1b247-144">プラス記号をクリックして、非キー列を含むインデックスの作成先となるテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="1b247-144">Click the plus sign to expand the table on which you want to create an index with nonkey columns.</span></span>  
  
4.  <span data-ttu-id="1b247-145">**[インデックス]** フォルダーを右クリックし、 **[新しいインデックス]** をポイントし、 **[非クラスター化インデックス]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b247-145">Right-click the **Indexes** folder, point to **New Index**, and select **Non-Clustered Index...**.</span></span>  
  
5.  <span data-ttu-id="1b247-146">**[新しいインデックス]** ダイアログ ボックスの **[全般]** ページで、 **[インデックス名]** ボックスに新しいインデックスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="1b247-146">In the **New Index** dialog box, on the **General** page, enter the name of the new index in the **Index name** box.</span></span>  
  
6.  <span data-ttu-id="1b247-147">**[インデックス キー列]** タブで、 **[追加...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b247-147">Under the **Index key columns** tab, click **Add...**.</span></span>  
  
7.  <span data-ttu-id="1b247-148">[Table_name**から列を選択**_table_name_ ] ダイアログボックスで、インデックスに追加するテーブル列のチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="1b247-148">In the **Select Columns from**_table_name_ dialog box, select the check box or check boxes of the table column or columns to be added to the index.</span></span>  
  
8.  <span data-ttu-id="1b247-149">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b247-149">Click **OK**.</span></span>  
  
9. <span data-ttu-id="1b247-150">**[付加列]** タブで、 **[追加...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b247-150">Under the **Included columns** tab, click **Add...**.</span></span>  
  
10. <span data-ttu-id="1b247-151">[Table_name**から列を選択**_table_name_ ] ダイアログボックスで、非キー列としてインデックスに追加するテーブル列のチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="1b247-151">In the **Select Columns from**_table_name_ dialog box, select the check box or check boxes of the table column or columns to be added to the index as nonkey columns.</span></span>  
  
11. <span data-ttu-id="1b247-152">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b247-152">Click **OK**.</span></span>  
  
12. <span data-ttu-id="1b247-153">**[新しいインデックス]** ダイアログ ボックスで、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b247-153">In the **New Index** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1b247-154">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="1b247-154">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-index-with-nonkey-columns"></a><span data-ttu-id="1b247-155">非キー列を含むインデックスを作成するには</span><span class="sxs-lookup"><span data-stu-id="1b247-155">To create an index with nonkey columns</span></span>  
  
1.  <span data-ttu-id="1b247-156">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="1b247-156">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1b247-157">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b247-157">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1b247-158">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b247-158">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Creates a nonclustered index on the Person.Address table with four included (nonkey) columns.   
    -- index key column is PostalCode and the nonkey columns are  
    -- AddressLine1, AddressLine2, City, and StateProvinceID.  
    CREATE NONCLUSTERED INDEX IX_Address_PostalCode  
    ON Person.Address (PostalCode)  
    INCLUDE (AddressLine1, AddressLine2, City, StateProvinceID);  
    GO  
    ```  
  
 <span data-ttu-id="1b247-159">詳細については、「[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b247-159">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
