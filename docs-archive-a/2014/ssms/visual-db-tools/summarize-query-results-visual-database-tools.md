---
title: クエリ結果の要約 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- summarizing query results
- queries [SQL Server], results
- aggregate queries [SQL Server]
ms.assetid: c9e15350-ed57-4d95-814d-815fbebfd86b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 08713be2d4439e520df07ec5efd6cb761a78a994
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720720"
---
# <a name="summarize-query-results-visual-database-tools"></a><span data-ttu-id="147a5-102">クエリ結果の要約 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="147a5-102">Summarize Query Results (Visual Database Tools)</span></span>
  <span data-ttu-id="147a5-103">集計クエリを作成するときには、一定の論理原則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="147a5-103">When you create aggregate queries, certain logical principles apply.</span></span> <span data-ttu-id="147a5-104">たとえば、サマリ クエリでは個別の行の内容は表示できません。</span><span class="sxs-lookup"><span data-stu-id="147a5-104">For example, you cannot display the contents of individual rows in a summary query.</span></span> <span data-ttu-id="147a5-105">クエリおよびビュー デザイナーでは、 [ダイアグラム ペイン](visual-database-tools.md) および [抽出条件ペイン](criteria-pane-visual-database-tools.md) を使用してこのような原則に従い、作業を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="147a5-105">The Query and View Designer helps you comply with these principles in the way the [Diagram pane](visual-database-tools.md) and [Criteria pane](criteria-pane-visual-database-tools.md) behave.</span></span>  
  
 <span data-ttu-id="147a5-106">集計クエリの原則やクエリおよびビュー デザイナーの動作を理解することによって、論理的に正しい集計クエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="147a5-106">By understanding the principles of aggregate queries and the Query and View Designer's behavior, you can create logically correct aggregate queries.</span></span> <span data-ttu-id="147a5-107">オーバーライドする原則は、集計クエリで作成できるのは集計情報だけであるということです。</span><span class="sxs-lookup"><span data-stu-id="147a5-107">The overriding principle is that aggregate queries can result only in summary information.</span></span> <span data-ttu-id="147a5-108">したがって、次に示す原則のほとんどは、集計クエリ内で個別のデータ列を参照する方法を示したものです。</span><span class="sxs-lookup"><span data-stu-id="147a5-108">Thus, most of the principles that follow describe the ways that you can reference individual data columns within an aggregate query.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="147a5-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="147a5-109">In This Section</span></span>  
 [<span data-ttu-id="147a5-110">集計クエリにおける列の使用 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="147a5-110">Work with Columns in Aggregate Queries &#40;Visual Database Tools&#41;</span></span>](work-with-columns-in-aggregate-queries-visual-database-tools.md)  
 <span data-ttu-id="147a5-111">GROUP BY 句、WHERE 句、および HAVING 句を使用して、列のグループ化と集計に関する概念を説明します。</span><span class="sxs-lookup"><span data-stu-id="147a5-111">Describes concepts about grouping and summarizing columns with the GROUP BY, WHERE, and HAVING clauses.</span></span>  
  
 [<span data-ttu-id="147a5-112">テーブルの行数のカウント (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="147a5-112">Count Rows in a Table &#40;Visual Database Tools&#41;</span></span>](count-rows-in-a-table-visual-database-tools.md)  
 <span data-ttu-id="147a5-113">テーブル内の行数、または一連の基準を満たすテーブル内の行数をカウントする手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="147a5-113">Provides steps for counting the number of rows in a table or the number of rows in a table that meet a set of criteria.</span></span>  
  
 [<span data-ttu-id="147a5-114">テーブルにあるすべての行の値の要約または集計 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="147a5-114">Summarize or Aggregate Values for All Rows in a Table &#40;Visual Database Tools&#41;</span></span>](summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools.md)  
 <span data-ttu-id="147a5-115">グループ化された一連の行ではなく、すべての行を集計する手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="147a5-115">Provides steps for summarizing all rows rather than for a set of grouped rows.</span></span>  
  
 [<span data-ttu-id="147a5-116">カスタム式を使用して値を要約または集計する (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="147a5-116">Summarize or Aggregate Values Using Custom Expressions &#40;Visual Database Tools&#41;</span></span>](summarize-or-aggregate-values-using-custom-expressions-visual-database-tools.md)  
 <span data-ttu-id="147a5-117">定義済みの句を使用するのではなく、集計または集約用の式を使用する手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="147a5-117">Provides steps for using expressions to summarize or aggregate rather than using the predefined clauses.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="147a5-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="147a5-118">Related Sections</span></span>  
 [<span data-ttu-id="147a5-119">クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="147a5-119">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
 <span data-ttu-id="147a5-120">クエリおよびビュー デザイナーの使用方法を説明するトピックへのリンクが用意されています。</span><span class="sxs-lookup"><span data-stu-id="147a5-120">Provides links to topics covering how to use the Query and View Designer.</span></span>  
  
  
