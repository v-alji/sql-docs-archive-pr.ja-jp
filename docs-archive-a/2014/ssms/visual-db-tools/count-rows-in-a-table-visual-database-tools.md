---
title: テーブルの行数のカウント (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- totals [SQL Server], row counts
- row counts [SQL Server]
- column values [SQL Server]
- number of rows
- number of values
- counting rows
ms.assetid: dda4296a-1d16-4e77-8d6f-e295f6dd4e87
author: stevestein
ms.author: sstein
ms.openlocfilehash: f6dca92fb955b776f56d9b51f28b1a486b89f18f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715897"
---
# <a name="count-rows-in-a-table-visual-database-tools"></a><span data-ttu-id="c4d33-102">テーブルの行数のカウント (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c4d33-102">Count Rows in a Table (Visual Database Tools)</span></span>
  <span data-ttu-id="c4d33-103">テーブルの行数をカウントすることにより、次の内容を確認できます。</span><span class="sxs-lookup"><span data-stu-id="c4d33-103">You can count rows in a table to determine:</span></span>  
  
-   <span data-ttu-id="c4d33-104">テーブルの行の総数。たとえば、 `titles` テーブルの本の総数を確認できます。</span><span class="sxs-lookup"><span data-stu-id="c4d33-104">The total number of rows in a table, for example, a count of all the books in a `titles` table.</span></span>  
  
-   <span data-ttu-id="c4d33-105">テーブルで特定の条件を満たす行の数。たとえば、 `titles` テーブルの本のうち、ある出版社の本の数を確認できます。</span><span class="sxs-lookup"><span data-stu-id="c4d33-105">The number of rows in a table that meet a specific condition, for example, the number of books by one publisher in a `titles` table.</span></span>  
  
-   <span data-ttu-id="c4d33-106">特定の列の値の数。</span><span class="sxs-lookup"><span data-stu-id="c4d33-106">The number of values in a particular column.</span></span>  
  
 <span data-ttu-id="c4d33-107">列の値をカウントするとき、NULL はカウントされません。</span><span class="sxs-lookup"><span data-stu-id="c4d33-107">When you count values in a column, nulls are not included in the count.</span></span> <span data-ttu-id="c4d33-108">たとえば、 `titles` テーブルの本のうち、 `advance` 列に値のある本の数をカウントできます。</span><span class="sxs-lookup"><span data-stu-id="c4d33-108">For example, you might count the number of books in a `titles` table that have values in the `advance` column.</span></span> <span data-ttu-id="c4d33-109">既定では、一意の値だけでなく、すべての値がカウントされます。</span><span class="sxs-lookup"><span data-stu-id="c4d33-109">By default, the count includes all values, not just unique values.</span></span>  
  
 <span data-ttu-id="c4d33-110">上記の 3 種類のカウント手順はほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="c4d33-110">The procedures for all three types of counts are similar.</span></span>  
  
### <a name="to-count-all-the-rows-in-a-table"></a><span data-ttu-id="c4d33-111">テーブルの行の総数をカウントするには</span><span class="sxs-lookup"><span data-stu-id="c4d33-111">To count all the rows in a table</span></span>  
  
1.  <span data-ttu-id="c4d33-112">集計するテーブルが、既にダイアグラム ペインに存在していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c4d33-112">Be sure the table you want to summarize is already present in the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="c4d33-113">ダイアグラム ペインの背景を右クリックし、ショートカット メニューの **[グループ化を追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c4d33-113">Right-click the background of the Diagram pane, then choose **Add Group By** from the shortcut menu.</span></span> <span data-ttu-id="c4d33-114">[クエリおよびビュー デザイナー](visual-database-tools.md) により、抽出条件ペインのグリッドに **[グループ化]** 列が追加されます。</span><span class="sxs-lookup"><span data-stu-id="c4d33-114">The [Query and View Designer](visual-database-tools.md) adds a **Group By** column to the grid in the Criteria pane.</span></span>  
  
3.  <span data-ttu-id="c4d33-115">テーブルまたはテーブル値オブジェクトを表す四角形の\*\* \* (すべての列)\*\* を選択します。</span><span class="sxs-lookup"><span data-stu-id="c4d33-115">Select **\* (All Columns)** in the rectangle representing the table or table-valued object.</span></span>  
  
     <span data-ttu-id="c4d33-116">クエリおよびビュー デザイナーにより、抽出条件ペインの **[グループ化]** 列に **[カウント]** という語句が自動的に入力され、集計する列に列の別名が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="c4d33-116">The Query and View Designer automatically fills the term **Count** into the **Group By** column in the Criteria pane and assigns a column alias to the column you are summarizing.</span></span> <span data-ttu-id="c4d33-117">この自動的に割り当てられた別名は、わかりやすい名前に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="c4d33-117">You can replace this automatically generated alias with a more meaningful one.</span></span> <span data-ttu-id="c4d33-118">詳細については、「[列の別名の作成 (Visual Database Tools)](create-column-aliases-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4d33-118">For more details, see [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
4.  <span data-ttu-id="c4d33-119">クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="c4d33-119">Run the query.</span></span>  
  
### <a name="to-count-all-the-rows-that-meet-a-condition"></a><span data-ttu-id="c4d33-120">条件を満たす行の総数をカウントするには</span><span class="sxs-lookup"><span data-stu-id="c4d33-120">To count all the rows that meet a condition</span></span>  
  
1.  <span data-ttu-id="c4d33-121">集計するテーブルが、既にダイアグラム ペインに存在していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c4d33-121">Be sure the table you want to summarize is already present in the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="c4d33-122">ダイアグラム ペインの背景を右クリックし、ショートカット メニューの **[グループ化を追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c4d33-122">Right-click the background of the Diagram pane, then choose **Add Group By** from the shortcut menu.</span></span> <span data-ttu-id="c4d33-123">クエリおよびビュー デザイナーにより、抽出条件ペインのグリッドに **[グループ化]** 列が追加されます。</span><span class="sxs-lookup"><span data-stu-id="c4d33-123">The Query and View Designer adds a **Group By** column to the grid in the Criteria pane.</span></span>  
  
3.  <span data-ttu-id="c4d33-124">テーブルまたはテーブル構造オブジェクトを表す四角形の [ \*\* \* (すべての列)\*\* ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c4d33-124">Select **\*(All Columns)** in the rectangle representing the table or table-structured object.</span></span>  
  
     <span data-ttu-id="c4d33-125">クエリおよびビュー デザイナーにより、抽出条件ペインの **[グループ化]** 列に **[カウント]** という語句が自動的に入力され、集計する列に列の別名が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="c4d33-125">The Query and View Designer automatically fills the term **Count** into the **Group By** column in the Criteria pane and assigns a column alias to the column you are summarizing.</span></span> <span data-ttu-id="c4d33-126">クエリ出力に表示する列ヘッダーをわかりやすくするには、「[列の別名の作成 (Visual Database Tools)](create-column-aliases-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4d33-126">To create a more useful column heading in query output, see [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
4.  <span data-ttu-id="c4d33-127">検索するデータ列を追加し、 **[出力]** 列のチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="c4d33-127">Add the data column that you want to search, and then clear the check box in the **Output** column.</span></span>  
  
     <span data-ttu-id="c4d33-128">クエリおよびビュー デザイナーにより、グリッドの **[グループ化]** 列に **[グループ化]** という語句が自動的に入力されます。</span><span class="sxs-lookup"><span data-stu-id="c4d33-128">The Query and View Designer automatically fills the term **Group By** into the **Group By** column of the grid.</span></span>  
  
5.  <span data-ttu-id="c4d33-129">**[グループ化]** 列の **[グループ化]** を **[Where 条件]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="c4d33-129">Change **Group By** in the **Group By** column to **Where**.</span></span>  
  
6.  <span data-ttu-id="c4d33-130">検索するデータ列の **[フィルター]** 列に検索条件を入力します。</span><span class="sxs-lookup"><span data-stu-id="c4d33-130">In the **Filter** column for the data column to search, enter the search condition.</span></span>  
  
7.  <span data-ttu-id="c4d33-131">クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="c4d33-131">Run the query.</span></span>  
  
### <a name="to-count-the-values-in-a-column"></a><span data-ttu-id="c4d33-132">列の値をカウントするには</span><span class="sxs-lookup"><span data-stu-id="c4d33-132">To count the values in a column</span></span>  
  
1.  <span data-ttu-id="c4d33-133">集計するテーブルが、既にダイアグラム ペインに存在していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c4d33-133">Be sure the table you want to summarize is already present in the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="c4d33-134">ダイアグラム ペインの背景を右クリックし、ショートカット メニューの **[グループ化を追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c4d33-134">Right-click the background of the Diagram pane, then choose **Add Group By** from the shortcut menu.</span></span> <span data-ttu-id="c4d33-135">クエリおよびビュー デザイナーにより、抽出条件ペインのグリッドに **[グループ化]** 列が追加されます。</span><span class="sxs-lookup"><span data-stu-id="c4d33-135">The Query and View Designer adds a **Group By** column to the grid in the Criteria pane.</span></span>  
  
3.  <span data-ttu-id="c4d33-136">カウントする列を抽出条件ペインに追加します。</span><span class="sxs-lookup"><span data-stu-id="c4d33-136">Add the column that you want to count to the Criteria pane.</span></span>  
  
     <span data-ttu-id="c4d33-137">クエリおよびビュー デザイナーにより、グリッドの **[グループ化]** 列に **[グループ化]** という語句が自動的に入力されます。</span><span class="sxs-lookup"><span data-stu-id="c4d33-137">The Query and View Designer automatically fills the term **Group By** into the **Group By** column of the grid.</span></span>  
  
4.  <span data-ttu-id="c4d33-138">**[グループ化]** 列の **[グループ化]** を **[カウント]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="c4d33-138">Change **Group By** in the **Group By** column to **Count**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c4d33-139">一意の値だけをカウントする場合は、 **[個別のカウント]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c4d33-139">To count only unique values, choose **Count Distinct**.</span></span>  
  
5.  <span data-ttu-id="c4d33-140">クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="c4d33-140">Run the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4d33-141">参照</span><span class="sxs-lookup"><span data-stu-id="c4d33-141">See Also</span></span>  
 <span data-ttu-id="c4d33-142">[クエリ結果の並べ替えとグループ化 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="c4d33-142">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="c4d33-143">クエリ結果の要約 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c4d33-143">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
  
  
