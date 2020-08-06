---
title: 検索条件の指定 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- choosing search criteria
- search conditions [SQL Server], specifying
- search criteria [SQL Server], specifying conditions
ms.assetid: 18e2c759-68ec-4efe-b208-2f73418cd9bd
author: stevestein
ms.author: sstein
ms.openlocfilehash: aa5dab8326de079c385a3a508bc1b01b1ee1247d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640314"
---
# <a name="specify-search-conditions-visual-database-tools"></a><span data-ttu-id="d075a-102">検索条件の指定 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="d075a-102">Specify Search Conditions (Visual Database Tools)</span></span>
  <span data-ttu-id="d075a-103">検索条件を指定することによって、クエリで表示されるデータ行を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d075a-103">You can specify the data rows that appear in your query by specifying search conditions.</span></span> <span data-ttu-id="d075a-104">たとえば、 `employee` テーブルに対してクエリを実行する場合、特定の地域で勤務している従業員だけを検索するようにクエリで指定できます。</span><span class="sxs-lookup"><span data-stu-id="d075a-104">For example, if you are querying an `employee` table, you can specify that you want to find only the employees who work in a particular region.</span></span>  
  
 <span data-ttu-id="d075a-105">検索条件は式で指定します。</span><span class="sxs-lookup"><span data-stu-id="d075a-105">You specify search conditions using an expression.</span></span> <span data-ttu-id="d075a-106">一般に、式は演算子および検索値で構成されています。</span><span class="sxs-lookup"><span data-stu-id="d075a-106">Most commonly the expression consists of an operator and a search value.</span></span> <span data-ttu-id="d075a-107">たとえば、特定の販売地域の従業員を検索するには、 `region` 列に対して次のように検索条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="d075a-107">For example, to find employees in a particular sales region, you might specify the following search criterion for the `region` column:</span></span>  
  
```  
='UK'  
```  
  
> [!NOTE]  
>  <span data-ttu-id="d075a-108">複数のテーブルを使用する場合、クエリおよびビュー デザイナーは各検索条件をチェックして、作成された比較が結合文になるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="d075a-108">If you are working with multiple tables, the Query and View Designer examines each search condition to determine whether the comparison you are making results in a join.</span></span> <span data-ttu-id="d075a-109">比較が結合になる場合、クエリおよびビュー デザイナーは自動的に検索条件を結合に変換します。</span><span class="sxs-lookup"><span data-stu-id="d075a-109">If so, the Query and View Designer automatically converts the search condition into a join.</span></span> <span data-ttu-id="d075a-110">詳細については、「[テーブルの自動結合 (Visual Database Tools)](visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d075a-110">For more information, see [Join Tables Automatically &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
### <a name="to-specify-search-conditions"></a><span data-ttu-id="d075a-111">検索条件を指定するには</span><span class="sxs-lookup"><span data-stu-id="d075a-111">To specify search conditions</span></span>  
  
1.  <span data-ttu-id="d075a-112">検索条件で使用する列または式を追加していない場合は、列または式を抽出条件ペインに追加します。</span><span class="sxs-lookup"><span data-stu-id="d075a-112">If you have not done so already, add the columns or expressions that you want to use within your search condition to the Criteria pane.</span></span>  
  
     <span data-ttu-id="d075a-113">選択クエリを作成し、検索列または検索式をクエリ出力に表示しない場合は、各検索列または検索式に該当する **[出力]** 列をオフにして、出力列から削除します。</span><span class="sxs-lookup"><span data-stu-id="d075a-113">If you are creating a Select query and do not want the search columns or expressions to appear in the query output, clear the **Output** column for each search column or expression to remove them as output columns.</span></span>  
  
2.  <span data-ttu-id="d075a-114">検索するデータ列または式を含む行を見つけ、 **[フィルター]** 列に検索条件を入力します。</span><span class="sxs-lookup"><span data-stu-id="d075a-114">Locate the row containing the data column or expression to search, and then in the **Filter** column, enter a search condition.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d075a-115">演算子を入力しない場合、等値演算子 "=" が自動的に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="d075a-115">If you do not enter an operator, the Query and View Designer automatically inserts the equality operator "=".</span></span>  
  
 <span data-ttu-id="d075a-116">クエリおよびビュー デザイナーは、WHERE 句を追加または変更して、 [SQL ペイン](sql-pane-visual-database-tools.md) の SQL ステートメントを更新します。</span><span class="sxs-lookup"><span data-stu-id="d075a-116">The Query and View Designer updates the SQL statement in the [SQL Pane](sql-pane-visual-database-tools.md) by adding or modifying the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d075a-117">参照</span><span class="sxs-lookup"><span data-stu-id="d075a-117">See Also</span></span>  
 <span data-ttu-id="d075a-118">[Visual Database Tools &#40;検索値を入力するための規則&#41;](rules-for-entering-search-values-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d075a-118">[Rules for Entering Search Values &#40;Visual Database Tools&#41;](rules-for-entering-search-values-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="d075a-119">検索基準の指定 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="d075a-119">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
