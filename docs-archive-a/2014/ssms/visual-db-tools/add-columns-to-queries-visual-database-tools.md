---
title: クエリへの列の追加 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting columns
- columns [SQL Server], adding
- queries [SQL Server], columns
- adding columns
ms.assetid: 82f3ba72-3d72-4fb1-8179-2a953a782787
author: stevestein
ms.author: sstein
ms.openlocfilehash: 49c6e575eea2d4437be1f16b400ca22120471fcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634224"
---
# <a name="add-columns-to-queries-visual-database-tools"></a><span data-ttu-id="8916e-102">クエリへの列の追加 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="8916e-102">Add Columns to Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="8916e-103">クエリで列を使用するには、クエリに列を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8916e-103">To use a column in a query, you must add it to the query.</span></span> <span data-ttu-id="8916e-104">列の追加は、クエリ出力に列を追加する場合、列を並べ替える場合、列の内容を検索する場合、または列の内容を集計する場合に行います。</span><span class="sxs-lookup"><span data-stu-id="8916e-104">You might add a column to display it in query output, to use it for sorting, to search the contents of the column, or to summarize its contents.</span></span> <span data-ttu-id="8916e-105">クエリで使用する列のうち、クエリを実行したときに結果ペインに含める列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8916e-105">You can decide which of the columns you use in the query are included in the results pane when the query is run.</span></span> <span data-ttu-id="8916e-106">詳細については、「 [クエリ結果からの列の削除 (Visual Database Tools)](visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8916e-106">For more information see [Remove Columns from Query Results &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8916e-107">列のデータ型をクエリおよびビュー デザイナーに表示するには、 **ダイアグラム ペイン** でテーブルまたはテーブル値オブジェクトを選択して、プロパティ ウィンドウの [列一覧] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8916e-107">To view the data type of a column in Query and View Designer; select the table or table-valued object in the **Diagram Pane** and in the properties window click Column List.</span></span> <span data-ttu-id="8916e-108">次に省略記号 ( **[...]** ) をクリックすると、 **[列一覧]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="8916e-108">Then click the **ellipses (...)** to open the **Column List** dialog box.</span></span>  
  
 <span data-ttu-id="8916e-109">クエリで列を使用する場合は、リテラル、演算子、および関数に組み合わせて式にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8916e-109">Wherever you use a column in a query, you can also use an expression that can consist of any combination of columns, literals, operators, and functions.</span></span>  
  
### <a name="to-add-an-individual-column"></a><span data-ttu-id="8916e-110">列を個別に追加するには</span><span class="sxs-lookup"><span data-stu-id="8916e-110">To add an individual column</span></span>  
  
-   <span data-ttu-id="8916e-111">**ダイアグラム ペイン**で、追加する列の横のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="8916e-111">In the **Diagram Pane**, select the check box next to the column that you want to include.</span></span>  
  
     <span data-ttu-id="8916e-112">または</span><span class="sxs-lookup"><span data-stu-id="8916e-112">-or-</span></span>  
  
-   <span data-ttu-id="8916e-113">**抽出条件ペイン**で、最初の空白のグリッド行に移動し、 **[列]** 列のフィールドをクリックして、ドロップダウン リストの列名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8916e-113">In the **Criteria Pane**, move to the first blank grid row, click the field in the **Column** column, and select a column name from the drop-down list.</span></span>  
  
### <a name="to-add-all-columns-for-one-table-or-table-valued-object"></a><span data-ttu-id="8916e-114">1 つのテーブルまたはテーブル値オブジェクトの列をすべて追加するには</span><span class="sxs-lookup"><span data-stu-id="8916e-114">To add all columns for one table or table-valued object</span></span>  
  
-   <span data-ttu-id="8916e-115">**ダイアグラムペイン**で、[ \*\* \* (すべての列)\*\*] の横にあるチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="8916e-115">In the **Diagram Pane**, select the check box next to **\*(All Columns)**.</span></span>  
  
### <a name="to-add-all-columns-for-all-tables-and-table-structured-objects"></a><span data-ttu-id="8916e-116">すべてのテーブルおよびテーブル構造オブジェクトの列をすべて追加するには</span><span class="sxs-lookup"><span data-stu-id="8916e-116">To add all columns for all tables and table-structured objects</span></span>  
  
1.  <span data-ttu-id="8916e-117">**テーブル操作ペイン** の結合線が選択されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="8916e-117">Make sure no join lines in the **Table Operations Pane** are selected.</span></span>  
  
2.  <span data-ttu-id="8916e-118">デザイン ウィンドウの空の領域を右クリックし、ショートカット メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8916e-118">Right-click in the empty space of the Design window and choose **Properties** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="8916e-119">プロパティ ウィンドウの **[すべての列を出力]** をクリックして、ドロップダウン リストの **[はい]** または **[いいえ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8916e-119">In the Properties window click **Output all columns** and choose **Yes** or **No** from the dropdown list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8916e-120">参照</span><span class="sxs-lookup"><span data-stu-id="8916e-120">See Also</span></span>  
 <span data-ttu-id="8916e-121">[Visual Database Tools&#41;&#40;クエリ結果から列を削除する](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="8916e-121">[Remove Columns from Query Results &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="8916e-122">[クエリからの列の削除 &#40;Visual Database Tools&#41;](remove-columns-from-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="8916e-122">[Remove Columns from Queries &#40;Visual Database Tools&#41;](remove-columns-from-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="8916e-123">[Visual Database Tools &#40;検索条件を指定し&#41;](specify-search-criteria-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="8916e-123">[Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md) </span></span>  
 <span data-ttu-id="8916e-124">[Visual Database Tools &#40;クエリ結果の概要&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="8916e-124">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="8916e-125">クエリに関する基本操作の実行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="8916e-125">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
