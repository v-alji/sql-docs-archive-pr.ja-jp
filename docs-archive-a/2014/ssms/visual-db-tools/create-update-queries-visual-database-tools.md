---
title: 更新クエリの作成 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- tables [SQL Server], updating
- queries [SQL Server], types
- Update query
- updating tables
ms.assetid: 178b7b75-8078-4e61-b2a8-4719b9d8033d
author: stevestein
ms.author: sstein
ms.openlocfilehash: bbea575d544875dba73de923474cc11bbcb46a9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641952"
---
# <a name="create-update-queries-visual-database-tools"></a><span data-ttu-id="3cd01-102">更新クエリの作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="3cd01-102">Create Update Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="3cd01-103">更新クエリを使用すると、複数行の内容を一度に変更できます。</span><span class="sxs-lookup"><span data-stu-id="3cd01-103">You can change the contents of multiple rows in one operation by using an Update query.</span></span> <span data-ttu-id="3cd01-104">たとえば、 `titles` テーブルで更新クエリを使用すると、特定の出版社から出版されているすべての本の価格に、10% 加算するような処理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3cd01-104">For example, in a `titles` table you can use an Update query to add 10% to the price of all books for a particular publisher.</span></span>  
  
 <span data-ttu-id="3cd01-105">更新クエリを作成するときは、次の項目を指定します。</span><span class="sxs-lookup"><span data-stu-id="3cd01-105">When you create an Update query, you specify:</span></span>  
  
-   <span data-ttu-id="3cd01-106">更新するテーブル</span><span class="sxs-lookup"><span data-stu-id="3cd01-106">The table to update.</span></span>  
  
-   <span data-ttu-id="3cd01-107">内容を更新する列</span><span class="sxs-lookup"><span data-stu-id="3cd01-107">The columns whose contents you want to update.</span></span>  
  
-   <span data-ttu-id="3cd01-108">各列の更新に使用する値または式</span><span class="sxs-lookup"><span data-stu-id="3cd01-108">The value or expression to use to update the individual columns.</span></span>  
  
-   <span data-ttu-id="3cd01-109">更新する行を指定する検索条件</span><span class="sxs-lookup"><span data-stu-id="3cd01-109">Search conditions to define the rows you want to update.</span></span>  
  
 <span data-ttu-id="3cd01-110">たとえば、次のクエリは、特定の出版社から出版されているすべての本の価格に 10% 加算して `titles` テーブルを更新します。</span><span class="sxs-lookup"><span data-stu-id="3cd01-110">For example, the following query updates the `titles` table by adding 10% to the price of all titles for one publisher:</span></span>  
  
```  
UPDATE titles  
SET price = price * 1.1  
WHERE (pub_id = '0766')  
```  
  
> [!CAUTION]  
>  <span data-ttu-id="3cd01-111">更新クエリの実行アクションを元に戻すことはできません。</span><span class="sxs-lookup"><span data-stu-id="3cd01-111">You cannot undo the action of executing an Update query.</span></span> <span data-ttu-id="3cd01-112">念のため、クエリを実行する前にデータをバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="3cd01-112">As a precaution, back up your data before executing the query.</span></span>  
  
### <a name="to-create-an-update-query"></a><span data-ttu-id="3cd01-113">更新クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="3cd01-113">To create an Update query</span></span>  
  
1.  <span data-ttu-id="3cd01-114">更新するテーブルをダイアグラム ペインに追加します。</span><span class="sxs-lookup"><span data-stu-id="3cd01-114">Add the table you want to update to the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="3cd01-115">**[クエリ デザイナー]** メニューの **[クエリ タイプの変更]** をポイントし、 **[更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cd01-115">From the **Query Designer** menu point to **Change Type**, and then click **Update**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3cd01-116">更新クエリを開始した時点でダイアグラム ペインに複数のテーブルが表示されている場合、更新するテーブルの名前を要求する [[値の挿入先のテーブル選択] ダイアログ ボックス](visual-database-tools.md) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3cd01-116">If more than one table is displayed in the Diagram pane when you start the Update query, the Query and View Designer displays the [Choose Target Table for Insert Values Dialog Box](visual-database-tools.md) to prompt you for the name of the table to update.</span></span>  
  
3.  <span data-ttu-id="3cd01-117">ダイアグラム ペインで、新しい値を指定する各列のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="3cd01-117">In the Diagram pane, click the check box for each column for which you want to supply new values.</span></span> <span data-ttu-id="3cd01-118">クリックした列が抽出条件ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3cd01-118">Those columns will show in the Criteria pane.</span></span> <span data-ttu-id="3cd01-119">クエリに追加された列だけが更新されます。</span><span class="sxs-lookup"><span data-stu-id="3cd01-119">Columns will be updated only if you add them to the query.</span></span>  
  
4.  <span data-ttu-id="3cd01-120">抽出条件ペインの **[新しい値]** 列に列の更新値を入力します。</span><span class="sxs-lookup"><span data-stu-id="3cd01-120">In the **New Value** column of the Criteria pane, enter the update value for the column.</span></span> <span data-ttu-id="3cd01-121">リテラル値、列名、または式を入力できます。</span><span class="sxs-lookup"><span data-stu-id="3cd01-121">You can enter literal values, column names, or expressions.</span></span> <span data-ttu-id="3cd01-122">更新する列のデータ型と一致する値か、互換性のある値を入力してください。</span><span class="sxs-lookup"><span data-stu-id="3cd01-122">The value must match (or be compatible with) the data type of the column you are updating.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="3cd01-123">クエリおよびビュー デザイナーは、値の長さが更新する列の長さの範囲内であるかどうかをチェックできません。</span><span class="sxs-lookup"><span data-stu-id="3cd01-123">The Query and View Designer cannot check that a value fits within the length of the column you are updating.</span></span> <span data-ttu-id="3cd01-124">指定した値が長すぎる場合、予告なしに切り捨てられることがあります。</span><span class="sxs-lookup"><span data-stu-id="3cd01-124">If you provide a value that is too long, it might be truncated without warning.</span></span> <span data-ttu-id="3cd01-125">たとえば、 `name` 列の長さが 20 文字である場合に 25 文字の更新値を指定すると、最後の 5 文字は切り捨てられることがあります。</span><span class="sxs-lookup"><span data-stu-id="3cd01-125">For example, if a `name` column is 20 characters long but you specify an update value of 25 characters, the last 5 characters might be truncated.</span></span>  
  
5.  <span data-ttu-id="3cd01-126">更新する行を定義するために、 **[フィルター]** 列に検索条件を入力します。</span><span class="sxs-lookup"><span data-stu-id="3cd01-126">Define the rows to update by entering search conditions in the **Filter** column.</span></span> <span data-ttu-id="3cd01-127">詳細については、「[検索基準の指定 (Visual Database Tools)](specify-search-criteria-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3cd01-127">For details, see [Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md).</span></span>  
  
     <span data-ttu-id="3cd01-128">検索条件を指定しない場合は、指定されたテーブルのすべての行が更新されます。</span><span class="sxs-lookup"><span data-stu-id="3cd01-128">If you do not specify a search condition, all rows in the specified table will be updated.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3cd01-129">検索条件に使用する列を抽出条件ペインに追加すると、更新される列のリストにこの列も追加されます。</span><span class="sxs-lookup"><span data-stu-id="3cd01-129">When you add a column to the Criteria pane for use in a search condition, the Query and View Designer also adds it to the list of columns to be updated.</span></span> <span data-ttu-id="3cd01-130">検索条件としては使用するが更新しない場合は、テーブルまたはテーブル値オブジェクトを示す四角形内の列名の横のチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="3cd01-130">If you want to use a column for a search condition but not update it, clear the check box next to the column name in the rectangle representing the table or table-valued object.</span></span>  
  
 <span data-ttu-id="3cd01-131">更新クエリを実行しても、 [結果ペイン](results-pane-visual-database-tools.md)には結果が表示されません。</span><span class="sxs-lookup"><span data-stu-id="3cd01-131">When you execute an Update query, no results are reported in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="3cd01-132">代わりに、変更された行数を示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3cd01-132">Instead, a message appears indicating how many rows were changed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cd01-133">参照</span><span class="sxs-lookup"><span data-stu-id="3cd01-133">See Also</span></span>  
 <span data-ttu-id="3cd01-134">[Visual Database Tools &#40;サポートされているクエリの種類&#41;](supported-query-types-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3cd01-134">[Supported Query Types &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md) </span></span>  
 <span data-ttu-id="3cd01-135">[クエリおよびビューのデザイン方法に関するトピック &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3cd01-135">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="3cd01-136">クエリに関する基本操作の実行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="3cd01-136">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
