---
title: カスタム式を使用した値の集計または集計 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- summarizing query results
- custom expressions to aggregate values [SQL Server]
ms.assetid: 34130ac1-0106-4766-b324-acb0b7bb6f6e
author: stevestein
ms.author: sstein
ms.openlocfilehash: b9f03f82842178a68c8a3d04ebc1bd738c0ab0b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720721"
---
# <a name="summarize-or-aggregate-values-using-custom-expressions-visual-database-tools"></a><span data-ttu-id="532b4-102">カスタム式を使用して値を要約または集計する (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="532b4-102">Summarize or Aggregate Values Using Custom Expressions (Visual Database Tools)</span></span>
  <span data-ttu-id="532b4-103">集計関数を使用してデータを集計するだけでなく、カスタム式を作成して集計値を求めることもできます。</span><span class="sxs-lookup"><span data-stu-id="532b4-103">In addition to using aggregate functions to aggregate data, you can create custom expressions to produce aggregate values.</span></span> <span data-ttu-id="532b4-104">カスタム式は、集計クエリのどこでも集計関数の代わりに使用できます。</span><span class="sxs-lookup"><span data-stu-id="532b4-104">You can use custom expressions in place of aggregate functions anywhere in an aggregate query.</span></span>  
  
 <span data-ttu-id="532b4-105">たとえば、 `titles` テーブルでは、平均価格を表示するだけでなく、値下げした場合の平均価格を表示するクエリも作成できます。</span><span class="sxs-lookup"><span data-stu-id="532b4-105">For example, in the `titles` table you might want to create a query that shows not just the average price, but what the average price would be if it were discounted.</span></span>  
  
 <span data-ttu-id="532b4-106">テーブルの一部の行だけに関連する計算を式で使用することはできません。式の計算時には集計値だけを使用できるため、集計値に基づく式を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="532b4-106">You cannot include an expression that is based on calculations involving only individual rows in the table; the expression must be based on an aggregate value, because only the aggregate values are available at the time the expression is calculated.</span></span>  
  
### <a name="to-specify-a-custom-expression-for-a-summary-value"></a><span data-ttu-id="532b4-107">集計値にカスタム式を指定するには</span><span class="sxs-lookup"><span data-stu-id="532b4-107">To specify a custom expression for a summary value</span></span>  
  
1.  <span data-ttu-id="532b4-108">検索するグループを指定します。</span><span class="sxs-lookup"><span data-stu-id="532b4-108">Specify the groups for your query.</span></span> <span data-ttu-id="532b4-109">詳しくは、「[クエリ結果内の行のグループ化 (Visual Database Tools)](visual-database-tools.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="532b4-109">For details, see [Group Rows in Query Results &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
2.  <span data-ttu-id="532b4-110">抽出条件ペインの空白行に移動し、 **[列]** 列に式を入力します。</span><span class="sxs-lookup"><span data-stu-id="532b4-110">Move to a blank row of the Criteria pane, and then type the expression in the **Columns** column.</span></span>  
  
     <span data-ttu-id="532b4-111">クエリ出力にわかりやすい列ヘッダーを作成できるように、[クエリおよびビュー デザイナー](query-and-view-designer-tools-visual-database-tools.md)により、式に列の別名が自動的に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="532b4-111">The [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) automatically assigns a column alias to the expression to create a useful column heading in query output.</span></span> <span data-ttu-id="532b4-112">詳細については、「[列の別名の作成 (Visual Database Tools)](create-column-aliases-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="532b4-112">For more details, see [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
3.  <span data-ttu-id="532b4-113">式の **[グループ化]** 列で、 **[式]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="532b4-113">In the **Group By** column for the expression, select **Expression**.</span></span>  
  
4.  <span data-ttu-id="532b4-114">クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="532b4-114">Run the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="532b4-115">参照</span><span class="sxs-lookup"><span data-stu-id="532b4-115">See Also</span></span>  
 <span data-ttu-id="532b4-116">[クエリ結果の並べ替えとグループ化 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="532b4-116">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="532b4-117">クエリ結果の要約 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="532b4-117">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
  
  
