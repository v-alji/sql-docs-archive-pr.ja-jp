---
title: 値の挿入クエリの作成 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting values
- queries [SQL Server], types
- adding values
- row additions [SQL Server], Insert Values query
- inserting rows
- Insert Values query
- adding rows
- table values [SQL Server]
ms.assetid: 2d4b2f6d-cc09-434b-8a0e-ccce40628064
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2fc71b0148ee8a7e92c517fe75b56c329b3c88f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714962"
---
# <a name="create-insert-values-queries-visual-database-tools"></a><span data-ttu-id="46d3b-102">値の挿入クエリの作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="46d3b-102">Create Insert Values Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="46d3b-103">値の挿入クエリを使用すると、現在のテーブルに新しい行を作成できます。</span><span class="sxs-lookup"><span data-stu-id="46d3b-103">You can create a new row in the current table using an Insert Values query.</span></span> <span data-ttu-id="46d3b-104">値の挿入クエリを作成するときは、次の項目を指定します。</span><span class="sxs-lookup"><span data-stu-id="46d3b-104">When you create an Insert Values query, you specify:</span></span>  
  
-   <span data-ttu-id="46d3b-105">行を追加するデータベース テーブル</span><span class="sxs-lookup"><span data-stu-id="46d3b-105">The database table to add the row to.</span></span>  
  
-   <span data-ttu-id="46d3b-106">内容を追加する列</span><span class="sxs-lookup"><span data-stu-id="46d3b-106">The columns whose contents you want to add.</span></span>  
  
-   <span data-ttu-id="46d3b-107">各列に挿入する値または式</span><span class="sxs-lookup"><span data-stu-id="46d3b-107">The value or expression to insert into the individual columns.</span></span>  
  
 <span data-ttu-id="46d3b-108">たとえば、次のクエリでは、書名、種類、出版社、価格の値を指定した行を `titles` テーブルに追加します。</span><span class="sxs-lookup"><span data-stu-id="46d3b-108">For example, the following query adds a row to the `titles` table, specifying values for the title, type, publisher, and price:</span></span>  
  
```  
INSERT INTO titles  
         (title_id, title, type, pub_id, price)  
VALUES   ('BU9876', 'Creating Web Pages', 'business', '1389', '29.99')  
```  
  
 <span data-ttu-id="46d3b-109">値の挿入クエリを作成すると、新しい行の挿入に使用できるオプション (列名および挿入値) だけが抽出条件ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="46d3b-109">When you create an Insert Values query, the Criteria pane changes to reflect the only options available for inserting a new row: the column name and the value to insert.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="46d3b-110">値の挿入クエリの実行アクションを元に戻すことはできません。</span><span class="sxs-lookup"><span data-stu-id="46d3b-110">You cannot undo the action of executing an Insert Values query.</span></span> <span data-ttu-id="46d3b-111">念のため、クエリを実行する前にデータをバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="46d3b-111">As a precaution, back up your data before executing the query.</span></span>  
  
### <a name="to-create-an-insert-values-query"></a><span data-ttu-id="46d3b-112">値の挿入クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="46d3b-112">To create an Insert Values query</span></span>  
  
1.  <span data-ttu-id="46d3b-113">更新するテーブルをダイアグラム ペインに追加します。</span><span class="sxs-lookup"><span data-stu-id="46d3b-113">Add the table you want to update to the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="46d3b-114">**[クエリ デザイナー]** メニューの **[クエリ タイプの変更]** をポイントし、 **[値の挿入]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46d3b-114">From the **Query Designer** menu point to **Change Type**, and then click **Insert Values**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="46d3b-115">値の挿入クエリを開始した時点でダイアグラム ペインに複数のテーブルが表示されている場合、更新するテーブルの名前を要求する [[値の挿入先のテーブル選択] ダイアログ ボックス](visual-database-tools.md) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="46d3b-115">If more than one table is displayed in the Diagram pane when you start the Insert Values query, the Query and View Designer displays the [Choose Target Table for Insert Values Dialog Box](visual-database-tools.md) to prompt you for the name of the table to update.</span></span>  
  
3.  <span data-ttu-id="46d3b-116">ダイアグラム ペインで、新しい値を指定する各列のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="46d3b-116">In the Diagram pane, click the check box for each column for which you want to supply new values.</span></span> <span data-ttu-id="46d3b-117">クリックした列が抽出条件ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="46d3b-117">Those columns will show in the Criteria pane.</span></span> <span data-ttu-id="46d3b-118">クエリに追加された列だけが更新されます。</span><span class="sxs-lookup"><span data-stu-id="46d3b-118">Columns will be updated only if you add them to the query.</span></span>  
  
4.  <span data-ttu-id="46d3b-119">抽出条件ペインの **[新しい値]** 列に列の新しい値を入力します。</span><span class="sxs-lookup"><span data-stu-id="46d3b-119">In the **New Value** column of the Criteria pane, enter the new value for the column.</span></span> <span data-ttu-id="46d3b-120">リテラル値、列名、または式を入力できます。</span><span class="sxs-lookup"><span data-stu-id="46d3b-120">You can enter literal values, column names, or expressions.</span></span> <span data-ttu-id="46d3b-121">更新する列のデータ型と一致する値か、互換性のある値を入力してください。</span><span class="sxs-lookup"><span data-stu-id="46d3b-121">The value must match (or be compatible with) the data type of the column you are updating.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="46d3b-122">クエリおよびビュー デザイナーは、値の長さが挿入する列の長さの範囲内であるかどうかをチェックできません。</span><span class="sxs-lookup"><span data-stu-id="46d3b-122">The Query and View Designer cannot check that a value fits within the length of the column you are inserting.</span></span> <span data-ttu-id="46d3b-123">指定した値が長すぎる場合、予告なしに切り捨てられることがあります。</span><span class="sxs-lookup"><span data-stu-id="46d3b-123">If you provide a value that is too long, it might be truncated without warning.</span></span> <span data-ttu-id="46d3b-124">たとえば、 `name` 列の長さが 20 文字である場合に 25 文字の挿入値を指定すると、最後の 5 文字は切り捨てられることがあります。</span><span class="sxs-lookup"><span data-stu-id="46d3b-124">For example, if a `name` column is 20 characters long but you specify an insert value of 25 characters, the last 5 characters might be truncated.</span></span>  
  
 <span data-ttu-id="46d3b-125">値の挿入クエリを実行しても、 [結果ペイン](results-pane-visual-database-tools.md)には結果が表示されません。</span><span class="sxs-lookup"><span data-stu-id="46d3b-125">When you execute an Insert Values query, no results are reported in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="46d3b-126">代わりに、変更された行数を示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="46d3b-126">Instead, a message appears indicating how many rows were changed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46d3b-127">参照</span><span class="sxs-lookup"><span data-stu-id="46d3b-127">See Also</span></span>  
 <span data-ttu-id="46d3b-128">[Visual Database Tools &#40;サポートされているクエリの種類&#41;](supported-query-types-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="46d3b-128">[Supported Query Types &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md) </span></span>  
 <span data-ttu-id="46d3b-129">[クエリおよびビューのデザイン方法に関するトピック &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="46d3b-129">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="46d3b-130">クエリに関する基本操作の実行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="46d3b-130">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
