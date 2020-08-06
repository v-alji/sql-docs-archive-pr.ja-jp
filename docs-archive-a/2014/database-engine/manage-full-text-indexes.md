---
title: フルテキストインデックスの管理 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
ms.assetid: 28ff17dc-172b-4ac4-853f-990b5dc02fd1
author: rothja
ms.author: jroth
ms.openlocfilehash: 92eb3669930407b359b8eeed4d3df2e802bdacdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645781"
---
# <a name="manage-full-text-indexes"></a><span data-ttu-id="dd3a6-102">フルテキスト インデックスの管理</span><span class="sxs-lookup"><span data-stu-id="dd3a6-102">Manage Full-Text Indexes</span></span>
     
##  <a name="viewing-and-changing-the-properties-of-a-full-text-index"></a><a name="view"></a><span data-ttu-id="dd3a6-103">フルテキストインデックスのプロパティの表示と変更</span><span class="sxs-lookup"><span data-stu-id="dd3a6-103">Viewing and Changing the Properties of a Full-Text Index</span></span>  
  
#### <a name="to-view-or-change-the-properties-of-a-full-text-index-in-management-studio"></a><span data-ttu-id="dd3a6-104">Management Studio でフルテキスト インデックスのプロパティを表示または変更するには</span><span class="sxs-lookup"><span data-stu-id="dd3a6-104">To view or change the properties of a full-text index in Management Studio</span></span>  
  
1.  <span data-ttu-id="dd3a6-105">オブジェクト エクスプローラーで、サーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-105">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="dd3a6-106">**[データベース]** を展開し、フルテキスト インデックスを含むデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-106">Expand **Databases**, and then expand the database that contains the full-text index.</span></span>  
  
3.  <span data-ttu-id="dd3a6-107">**[テーブル]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-107">Expand **Tables**.</span></span>  
  
4.  <span data-ttu-id="dd3a6-108">フルテキスト インデックスが定義されているテーブルを右クリックし、 **[フルテキスト インデックス]** コンテキスト メニューの **[フルテキスト インデックス]** をクリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-108">Right-click the table on which the full-text index is defined, select **Full-Text index**, and on the **Full-Text index** context menu, click **Properties**.</span></span> <span data-ttu-id="dd3a6-109">**[フルテキスト インデックスのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-109">This opens the **Full-text index Properties** dialog box.</span></span>  
  
5.  <span data-ttu-id="dd3a6-110">**[ページの選択]** ペインでは、次のいずれかのページを選択できます。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-110">In the **Select a page** pane, you can select any of the following pages:</span></span>  
  
    |<span data-ttu-id="dd3a6-111">ページ</span><span class="sxs-lookup"><span data-stu-id="dd3a6-111">Page</span></span>|<span data-ttu-id="dd3a6-112">説明</span><span class="sxs-lookup"><span data-stu-id="dd3a6-112">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="dd3a6-113">**全般**</span><span class="sxs-lookup"><span data-stu-id="dd3a6-113">**General**</span></span>|<span data-ttu-id="dd3a6-114">フルテキスト インデックスの基本的なプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-114">Displays basic properties of the full-text index.</span></span> <span data-ttu-id="dd3a6-115">これには、いくつかの変更可能なプロパティと、データベース名、テーブル名、フルテキスト キー列の名前など多数の変更不可能なプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-115">These include several modifiable properties and a number of unchangeable properties such as database name, table name, and the name of full-text key column.</span></span> <span data-ttu-id="dd3a6-116">変更可能なプロパティは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-116">The modifiable properties are:</span></span><br /><br /> <span data-ttu-id="dd3a6-117">**フルテキスト インデックス ストップリスト**</span><span class="sxs-lookup"><span data-stu-id="dd3a6-117">**Full-Text Index Stoplist**</span></span><br /><br /> <span data-ttu-id="dd3a6-118">**フルテキスト インデックス有効**</span><span class="sxs-lookup"><span data-stu-id="dd3a6-118">**Full-Text Indexing Enabled**</span></span><br /><br /> <span data-ttu-id="dd3a6-119">**変更の追跡**</span><span class="sxs-lookup"><span data-stu-id="dd3a6-119">**Change Tracking**</span></span><br /><br /> <span data-ttu-id="dd3a6-120">**検索プロパティ リスト**</span><span class="sxs-lookup"><span data-stu-id="dd3a6-120">**Search Property List**</span></span><br /><br /> <br /><br /> <span data-ttu-id="dd3a6-121">詳細については、「 [フルテキスト インデックス プロパティ &#40;[全般] ページ&#41;](full-text-index-properties-general-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-121">For more information, see [Full-Text Index Properties &#40;General Page&#41;](full-text-index-properties-general-page.md).</span></span>|  
    |<span data-ttu-id="dd3a6-122">**[列]**</span><span class="sxs-lookup"><span data-stu-id="dd3a6-122">**Columns**</span></span>|<span data-ttu-id="dd3a6-123">フルテキスト インデックスを作成できるテーブル列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-123">Displays the table columns that are available for full-text indexing.</span></span> <span data-ttu-id="dd3a6-124">選択した列にフルテキスト インデックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-124">The selected column or columns are full-text indexed.</span></span> <span data-ttu-id="dd3a6-125">フルテキスト インデックスに含める列はいくつでも選択できます。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-125">You can select as many of the available columns as you want to include in the full-text index.</span></span> <span data-ttu-id="dd3a6-126">詳細については、「 [フルテキスト インデックス プロパティ &#40;[列] ページ&#41;](../../2014/database-engine/full-text-index-properties-columns-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-126">For more information, see [Full-Text Index Properties &#40;Columns Page&#41;](../../2014/database-engine/full-text-index-properties-columns-page.md).</span></span>|  
    |<span data-ttu-id="dd3a6-127">**スケジュール**</span><span class="sxs-lookup"><span data-stu-id="dd3a6-127">**Schedules**</span></span>|<span data-ttu-id="dd3a6-128">このページでは、フルテキスト インデックスを作成するためのテーブルの増分作成を開始する SQL Server エージェント ジョブのスケジュールを作成または管理できます。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-128">Use this page to create or manage schedules for a SQL Server Agent job that starts an incremental table population for the full-text index populations.</span></span> <span data-ttu-id="dd3a6-129">詳細については、「 [フルテキスト インデックスの作成](../relational-databases/indexes/indexes.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-129">For more information, see [Populate Full-Text Indexes](../relational-databases/indexes/indexes.md).</span></span><br /><br /> <span data-ttu-id="dd3a6-130"><strong> \* \* 重要 \* : \* </strong> [**フルテキストインデックスのプロパティ**] ダイアログボックスを閉じると、新しく作成されたスケジュールが SQL Server エージェントジョブに関連付けられます ( *database_name*でテーブルの増分作成を開始します)。*table_name*)。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-130"><strong>\*\* Important \*\*</strong> After you exit the **Full-Text Index Properties** dialog box, any newly created schedule is associated with a SQL Server Agent job (Start Incremental Table Population on *database_name*.*table_name*).</span></span>|  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)] <span data-ttu-id="dd3a6-131">をクリックして変更を保存し、 **[フルテキスト インデックスのプロパティ]** ダイアログ ボックスを終了します。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-131">to save any changes and exit the **Full-text index Properties** dialog box.</span></span>  
  
##  <a name="viewing-the-properties-of-indexed-tables-and-columns"></a><a name="props"></a><span data-ttu-id="dd3a6-132">インデックス付きテーブルと列のプロパティの表示</span><span class="sxs-lookup"><span data-stu-id="dd3a6-132">Viewing the Properties of Indexed Tables and Columns</span></span>  
 <span data-ttu-id="dd3a6-133">OBJECTPROPERTYEX など、[!INCLUDE[tsql](../includes/tsql-md.md)] 関数の中には、さまざまなフルテキスト インデックス プロパティの値を取得できるものがあります。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-133">Several [!INCLUDE[tsql](../includes/tsql-md.md)] functions such as OBJECTPROPERTYEX can be used to obtain the value of various full-text indexing properties.</span></span> <span data-ttu-id="dd3a6-134">この情報は、フルテキスト検索の管理およびトラブルシューティングに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-134">This information is useful for administering and troubleshooting full-text search.</span></span>  
  
 <span data-ttu-id="dd3a6-135">次の表に、インデックスが作成されたテーブルおよび列に関連したフルテキスト プロパティと、それに関連する [!INCLUDE[tsql](../includes/tsql-md.md)] 関数の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-135">The following table lists the full-text properties related to indexed tables and columns and their related [!INCLUDE[tsql](../includes/tsql-md.md)] functions.</span></span>  
  
|<span data-ttu-id="dd3a6-136">プロパティ</span><span class="sxs-lookup"><span data-stu-id="dd3a6-136">Property</span></span>|<span data-ttu-id="dd3a6-137">説明</span><span class="sxs-lookup"><span data-stu-id="dd3a6-137">Description</span></span>|<span data-ttu-id="dd3a6-138">機能</span><span class="sxs-lookup"><span data-stu-id="dd3a6-138">Function</span></span>|  
|--------------|-----------------|--------------|  
|`FullTextTypeColumn`|<span data-ttu-id="dd3a6-139">列のドキュメント型情報を保持する、テーブル内の TYPE COLUMN。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-139">TYPE COLUMN in the table that holds the document type information of the column.</span></span>|[<span data-ttu-id="dd3a6-140">COLUMNPROPERTY</span><span class="sxs-lookup"><span data-stu-id="dd3a6-140">COLUMNPROPERTY</span></span>](/sql/t-sql/functions/columnproperty-transact-sql)|  
|`IsFulltextIndexed`|<span data-ttu-id="dd3a6-141">列に対してフルテキスト インデックスを作成できるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-141">Whether a column has been enabled for full-text indexing.</span></span>|<span data-ttu-id="dd3a6-142">COLUMNPROPERTY</span><span class="sxs-lookup"><span data-stu-id="dd3a6-142">COLUMNPROPERTY</span></span>|  
|`IsFulltextKey`|<span data-ttu-id="dd3a6-143">インデックスがテーブルのフルテキスト キーであるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-143">Whether the index is the full-text key for a table.</span></span>|[<span data-ttu-id="dd3a6-144">INDEXPROPERTY</span><span class="sxs-lookup"><span data-stu-id="dd3a6-144">INDEXPROPERTY</span></span>](/sql/t-sql/functions/indexproperty-transact-sql)|  
|<span data-ttu-id="dd3a6-145">**TableFulltextBackgroundUpdateIndexOn**</span><span class="sxs-lookup"><span data-stu-id="dd3a6-145">**TableFulltextBackgroundUpdateIndexOn**</span></span>|<span data-ttu-id="dd3a6-146">テーブルがフルテキスト インデックスをバックグラウンドで更新できるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-146">Whether a table has full-text background update indexing.</span></span>|[<span data-ttu-id="dd3a6-147">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="dd3a6-147">OBJECTPROPERTYEX</span></span>](/sql/t-sql/functions/objectproperty-transact-sql)|  
|`TableFulltextCatalogId`|<span data-ttu-id="dd3a6-148">テーブルのフルテキスト インデックス データが存在する、フルテキスト カタログ ID。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-148">Full-text catalog ID in which the full-text index data for the table resides.</span></span>|<span data-ttu-id="dd3a6-149">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="dd3a6-149">OBJECTPROPERTYEX</span></span>|  
|`TableFulltextChangeTrackingOn`|<span data-ttu-id="dd3a6-150">テーブルでフルテキストの変更の追跡が有効になっているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-150">Whether a table has full-text change-tracking enabled.</span></span>|<span data-ttu-id="dd3a6-151">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="dd3a6-151">OBJECTPROPERTYEX</span></span>|  
|`TableFulltextDocsProcessed`|<span data-ttu-id="dd3a6-152">フルテキスト インデックス作成の開始以降に処理された行の数。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-152">Number of rows processed since the start of full-text indexing.</span></span>|<span data-ttu-id="dd3a6-153">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="dd3a6-153">OBJECTPROPERTYEX</span></span>|  
|<span data-ttu-id="dd3a6-154">**TableFulltextFailCount**</span><span class="sxs-lookup"><span data-stu-id="dd3a6-154">**TableFulltextFailCount**</span></span>|<span data-ttu-id="dd3a6-155">フルテキスト検索によるインデックスが設定されなかった行数。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-155">Number of rows Full-Text Search did not index.</span></span>|<span data-ttu-id="dd3a6-156">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="dd3a6-156">OBJECTPROPERTYEX</span></span>|  
|<span data-ttu-id="dd3a6-157">**TableFulltextItemCount**</span><span class="sxs-lookup"><span data-stu-id="dd3a6-157">**TableFulltextItemCount**</span></span>|<span data-ttu-id="dd3a6-158">フルテキスト インデックスが正常に設定された行数。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-158">Number of rows that were successfully full-text indexed.</span></span>|<span data-ttu-id="dd3a6-159">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="dd3a6-159">OBJECTPROPERTYEX</span></span>|  
|`TableFulltextKeyColumn`|<span data-ttu-id="dd3a6-160">一意なフルテキスト キー列の列 ID。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-160">The column ID of the full-text unique key column.</span></span>|<span data-ttu-id="dd3a6-161">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="dd3a6-161">OBJECTPROPERTYEX</span></span>|  
|`TableFullTextMergeStatus`|<span data-ttu-id="dd3a6-162">現在マージ中のフルテキスト インデックスがテーブルにあるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-162">Whether a table that has a full-text index is currently in merging.</span></span>|<span data-ttu-id="dd3a6-163">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="dd3a6-163">OBJECTPROPERTYEX</span></span>|  
|<span data-ttu-id="dd3a6-164">**TableFulltextPendingChanges**</span><span class="sxs-lookup"><span data-stu-id="dd3a6-164">**TableFulltextPendingChanges**</span></span>|<span data-ttu-id="dd3a6-165">変更の追跡が処理されていないエントリ数。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-165">Number of pending change tracking entries to process.</span></span>|<span data-ttu-id="dd3a6-166">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="dd3a6-166">OBJECTPROPERTYEX</span></span>|  
|`TableFulltextPopulateStatus`|<span data-ttu-id="dd3a6-167">フルテキスト テーブルの作成状態。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-167">Population status of a full-text table.</span></span>|<span data-ttu-id="dd3a6-168">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="dd3a6-168">OBJECTPROPERTYEX</span></span>|  
|`TableHasActiveFulltextIndex`|<span data-ttu-id="dd3a6-169">テーブルが有効なフルテキスト インデックスを持っているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-169">Whether a table has an active full-text index.</span></span>|<span data-ttu-id="dd3a6-170">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="dd3a6-170">OBJECTPROPERTYEX</span></span>|  
  
##  <a name="getting-information-about-the-full-text-key-column"></a><a name="key"></a><span data-ttu-id="dd3a6-171">フルテキストキー列に関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="dd3a6-171">Getting Information about the Full-Text Key Column</span></span>  
 <span data-ttu-id="dd3a6-172">通常、行セット値関数 CONTAINSTABLE または FREETEXTTABLE の結果をベース テーブルと結合します。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-172">Typically, the result of CONTAINSTABLE or FREETEXTTABLE rowset-valued functions need to be joined with the base table.</span></span> <span data-ttu-id="dd3a6-173">その場合、一意なキー列の名前を把握している必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-173">In such cases, you need to know the unique key column name.</span></span> <span data-ttu-id="dd3a6-174">一意のインデックスがフルテキスト キーとして使用されているかどうかを調査したり、フルテキスト キー列の識別子を取得したりできます。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-174">You can inquire whether a given unique index is used as the full-text key, and you can obtain the identifier of the full-text key column.</span></span>  
  
#### <a name="to-inquire-whether-a-given-unique-index-is-used-as-the-full-text-key-column"></a><span data-ttu-id="dd3a6-175">一意のインデックスがフルテキスト キー列として使用されているかどうかを調査するには</span><span class="sxs-lookup"><span data-stu-id="dd3a6-175">To inquire whether a given unique index is used as the full-text key column</span></span>  
  
1.  <span data-ttu-id="dd3a6-176">[SELECT](/sql/t-sql/queries/select-transact-sql) ステートメントを使用して、 [INDEXPROPERTY](/sql/t-sql/functions/indexproperty-transact-sql) 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-176">Use a [SELECT](/sql/t-sql/queries/select-transact-sql) statement to call the [INDEXPROPERTY](/sql/t-sql/functions/indexproperty-transact-sql) function.</span></span> <span data-ttu-id="dd3a6-177">関数呼び出しでは、OBJECT_ID 関数を使用してテーブルの名前 (*table_name*) をテーブル ID に変換し、テーブルに一意のインデックスの名前を指定して、次のようにインデックスのプロパティを指定し `IsFulltextKey` ます。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-177">In the function call use the OBJECT_ID function to convert the name of the table (*table_name*) into the table ID, specify the name of a unique index for the table, and specify the `IsFulltextKey` index property, as follows:</span></span>  
  
    ```  
    SELECT INDEXPROPERTY( OBJECT_ID('table_name'), 'index_name',  'IsFulltextKey' );  
    ```  
  
     <span data-ttu-id="dd3a6-178">このステートメントでは、このインデックスを使用してフルテキスト キー列の一意性を確保している場合には 1 が返され、そうでない場合には 0 が返されます。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-178">This statement returns 1 if the index is used to enforce uniqueness of the full-text key column and 0 if it is not.</span></span>  
  
 <span data-ttu-id="dd3a6-179">**例**</span><span class="sxs-lookup"><span data-stu-id="dd3a6-179">**Example**</span></span>  
  
 <span data-ttu-id="dd3a6-180">次の例では、フルテキスト キー列の一意性を確保するために `PK_Document_DocumentID` インデックスが使用されているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-180">The following example inquires whether the `PK_Document_DocumentID` index is used to enforce the uniqueness of the full-text key column, as follows:</span></span>  
  
```  
USE AdventureWorks  
GO  
SELECT INDEXPROPERTY ( OBJECT_ID('Production.Document'), 'PK_Document_DocumentID',  'IsFulltextKey' )  
```  
  
 <span data-ttu-id="dd3a6-181">`PK_Document_DocumentID` インデックスを使用してフルテキスト キー列の一意性が確保されている場合には 1 が返されます。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-181">This example returns 1 if the `PK_Document_DocumentID` index is used to enforce uniqueness of the full-text key column.</span></span> <span data-ttu-id="dd3a6-182">それ以外のときは 0 または NULL が返されます。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-182">Otherwise, it returns 0 or NULL.</span></span> <span data-ttu-id="dd3a6-183">NULL は、無効なインデックス名が使用されている、インデックス名がテーブルに対応していない、テーブルが存在しないなどを意味します。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-183">NULL implies you are using an invalid index name, the index name does not correspond to the table, the table does not exist, or so forth.</span></span>  
  
#### <a name="to-find-the-identifier-of-the-full-text-key-column"></a><span data-ttu-id="dd3a6-184">フルテキスト キー列の識別子を検索するには</span><span class="sxs-lookup"><span data-stu-id="dd3a6-184">To find the identifier of the full-text key column</span></span>  
  
1.  <span data-ttu-id="dd3a6-185">フルテキスト処理に対応する各テーブルには、テーブルの行を一意にするための列があります ("*一意なキー列*")。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-185">Each full-text enabled table has a column that is used to enforce unique rows for the table (the *unique\*\*key column*).</span></span> <span data-ttu-id="dd3a6-186">OBJECTPROPERTYEX 関数で取得できる `TableFulltextKeyColumn` プロパティには、この一意なキー列の列 ID が格納されます。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-186">The `TableFulltextKeyColumn` property, obtained from the OBJECTPROPERTYEX function, contains the column ID of the unique key column.</span></span>  
  
     <span data-ttu-id="dd3a6-187">この識別子を取得するには、SELECT ステートメントで OBJECTPROPERTYEX 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-187">To obtain this identifier, you can use a SELECT statement to call the OBJECTPROPERTYEX function.</span></span> <span data-ttu-id="dd3a6-188">OBJECT_ID 関数を使用してテーブルの名前 (*table_name*) をテーブル ID に変換し、次のようにプロパティを指定し `TableFulltextKeyColumn` ます。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-188">Use the OBJECT_ID function to convert the name of the table (*table_name*) into the table ID and specify the `TableFulltextKeyColumn` property, as follows:</span></span>  
  
    ```  
    SELECT OBJECTPROPERTYEX(OBJECT_ID( 'table_name'), 'TableFulltextKeyColumn' ) AS 'Column Identifier';  
    ```  
  
 <span data-ttu-id="dd3a6-189">**使用例**</span><span class="sxs-lookup"><span data-stu-id="dd3a6-189">**Examples**</span></span>  
  
 <span data-ttu-id="dd3a6-190">次の例では、フルテキスト キー列の識別子または NULL が返されます。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-190">The following example returns the identifier of the full-text key column or NULL.</span></span> <span data-ttu-id="dd3a6-191">NULL は、無効なインデックス名が使用されている、インデックス名がテーブルに対応していない、テーブルが存在しないなどを意味します。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-191">NULL implies that you are using an invalid index name, the index name does not correspond to the table, the table does not exist, or so forth.</span></span>  
  
```  
USE AdventureWorks;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID('Production.Document'), 'TableFulltextKeyColumn');  
GO  
```  
  
 <span data-ttu-id="dd3a6-192">次の例は、一意のキー列の識別子からその列の名前を取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-192">The following example shows how to use the identifier of the unique key column to obtain the name of the column.</span></span>  
  
```  
USE AdventureWorks;  
GO  
DECLARE @key_column sysname  
SET @key_column = Col_Name(Object_Id('Production.Document'),  
ObjectProperty(Object_id('Production.Document'),  
'TableFulltextKeyColumn')   
)  
SELECT @key_column AS 'Unique Key Column';  
GO  
```  
  
 <span data-ttu-id="dd3a6-193">この例では、 `Unique Key Column`という名前の結果セット列が返され、Document テーブルの一意のキー列の名前 DocumentID を含む単一行が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-193">This example returns a result set column named `Unique Key Column`, which displays a single row containing the name of the unique key column of the Document table, DocumentID.</span></span> <span data-ttu-id="dd3a6-194">このクエリに無効なインデックス名が使用されている、インデックス名がテーブルに対応していない、テーブルが存在しないなどの場合には、NULL が返されます。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-194">Note that if this query contained an invalid index name, the index name did not correspond to the table, the table did not exist, and so forth, it would return NULL.</span></span>  
  
##  <a name="disabling-or-re-enabling-a-table-for-full-text-indexing"></a><a name="disable"></a><span data-ttu-id="dd3a6-195">テーブルのフルテキストインデックスの無効化または再有効化</span><span class="sxs-lookup"><span data-stu-id="dd3a6-195">Disabling or Re-enabling a Table for Full-Text Indexing</span></span>  
 <span data-ttu-id="dd3a6-196">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]では、既定によりユーザーが作成したすべてのデータベースでフルテキストが有効になります。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-196">In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], all user-created databases are full-text enabled by default.</span></span> <span data-ttu-id="dd3a6-197">さらに、個々のテーブルに対してフルテキスト インデックスを作成し、これに列を追加すると、その時点で、このテーブルでは自動的にフルテキスト インデックスが有効になります。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-197">Additionally, an individual table is automatically enabled for full-text indexing as soon as a full-text index is created on it and a column is added to the index.</span></span> <span data-ttu-id="dd3a6-198">フルテキスト インデックスから最後の列を削除すると、このテーブルでは自動的にフルテキスト インデックスが無効になります。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-198">A table is automatically disabled for full-text indexing when the last column is dropped from its full-text index.</span></span>  
  
 <span data-ttu-id="dd3a6-199">フルテキスト インデックスのあるテーブルでは、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を使用して手動でフルテキスト インデックスを無効にしたり、再度有効にしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-199">On a table that has a full-text index, you can manually disable or re-enable a table for full-text indexing using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-enable-a-table-for-full-text-indexing"></a><span data-ttu-id="dd3a6-200">テーブルでフルテキスト インデックスを有効にするには</span><span class="sxs-lookup"><span data-stu-id="dd3a6-200">To enable a table for full-text indexing</span></span>  
  
1.  <span data-ttu-id="dd3a6-201">サーバー グループを展開し、 **[データベース]** を展開して、フルテキスト インデックスを有効にするテーブルを含むデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-201">Expand the server group, expand **Databases**, and expand the database that contains the table you want to enable for full-text indexing.</span></span>  
  
2.  <span data-ttu-id="dd3a6-202">**[テーブル]** を展開し、フルテキスト インデックスを無効または再度有効にするテーブルを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-202">Expand **Tables**, and right-click the table that you want to disable or re-enable for full-text indexing.</span></span>  
  
3.  <span data-ttu-id="dd3a6-203">**[フルテキスト インデックス]** を選択し、 **[フルテキスト インデックスを無効化]** または **[フルテキスト インデックスを有効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-203">Select **Full-Text index**, and then click **Disable Full-Text index** or **Enable Full-Text index**.</span></span>  
  
##  <a name="removing-a-full-text-index-from-a-table"></a><a name="remove"></a><span data-ttu-id="dd3a6-204">テーブルからフルテキストインデックスを削除する</span><span class="sxs-lookup"><span data-stu-id="dd3a6-204">Removing a Full-Text Index from a Table</span></span>  
  
#### <a name="to-remove-a-full-text-index-from-a-table"></a><span data-ttu-id="dd3a6-205">テーブルからフルテキスト インデックスを削除するには</span><span class="sxs-lookup"><span data-stu-id="dd3a6-205">To remove a full-text index from a table</span></span>  
  
1.  <span data-ttu-id="dd3a6-206">オブジェクト エクスプローラーで、削除するフルテキスト インデックスが含まれているテーブルを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-206">In Object Explorer, right-click the table that has the full-text index that you want to delete.</span></span>  
  
2.  <span data-ttu-id="dd3a6-207">**[フルテキスト インデックスの削除]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-207">Select **Delete Full-Text index**.</span></span>  
  
3.  <span data-ttu-id="dd3a6-208">フルテキスト インデックスの削除を確認するメッセージが表示されたら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd3a6-208">When prompted, click **OK** to confirm that you want to delete the full-text index.</span></span>  
  
  
