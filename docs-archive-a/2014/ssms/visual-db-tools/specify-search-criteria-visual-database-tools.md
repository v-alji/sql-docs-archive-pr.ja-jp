---
title: 検索基準の指定 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Query Designer [SQL Server], Criteria pane
- queries [Visual Database Tools]
- criteria for search conditions
- search conditions [SQL Server], search criteria
- View Designer, Criteria pane
- row return limitations [SQL Server]
- Criteria pane
- restricting rows returned
- search criteria [SQL Server]
- Visual Database Tools [SQL Server], queries
- limiting rows returned
ms.assetid: 25fb4e31-6dbf-4cf6-8e47-0dd0998c836c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 258aceb348ed3bcd7d4d19201a0169b53b54d711
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640313"
---
# <a name="specify-search-criteria-visual-database-tools"></a><span data-ttu-id="437e0-102">検索基準の指定 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="437e0-102">Specify Search Criteria (Visual Database Tools)</span></span>
  <span data-ttu-id="437e0-103">検索基準を使用すると、クエリによって返される行数を制限できます。</span><span class="sxs-lookup"><span data-stu-id="437e0-103">You can use search criteria to restrict the number of rows returned by a query.</span></span>  
  
 <span data-ttu-id="437e0-104">検索基準の作成手順の詳細については、次の表の各トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="437e0-104">For details about the particular steps to creating search criteria, refer to the topics listed in the following table.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="437e0-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="437e0-105">In This Section</span></span>  
 [<span data-ttu-id="437e0-106">検索値を入力するときの規則 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="437e0-106">Rules for Entering Search Values &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
 <span data-ttu-id="437e0-107">テキスト、数値、日付、または論理値の入力方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="437e0-107">Explains how to enter text, numbers, dates, or logical values.</span></span>  
  
 [<span data-ttu-id="437e0-108">抽出条件ペインで検索条件を組み合わせる場合の規則 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="437e0-108">Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;</span></span>](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md)  
 <span data-ttu-id="437e0-109">AND 演算子および OR 演算子の使用の背景にある概念を説明します。</span><span class="sxs-lookup"><span data-stu-id="437e0-109">Explains the concepts behind using the AND and OR operators.</span></span>  
  
 [<span data-ttu-id="437e0-110">検索条件の指定 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="437e0-110">Specify Search Conditions &#40;Visual Database Tools&#41;</span></span>](specify-search-conditions-visual-database-tools.md)  
 <span data-ttu-id="437e0-111">必要なデータが得られるように検索基準を選択するための基礎知識を説明します。</span><span class="sxs-lookup"><span data-stu-id="437e0-111">Explains the basics of choosing search criteria to get just the data you want.</span></span>  
  
 [<span data-ttu-id="437e0-112">1 つの列に対して複数の検索条件を指定する (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="437e0-112">Specify Multiple Search Conditions for One Column &#40;Visual Database Tools&#41;</span></span>](specify-multiple-search-conditions-for-one-column-visual-database-tools.md)  
 <span data-ttu-id="437e0-113">同じデータ列に対して複数の検索条件を作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="437e0-113">Explains how to create multiple search conditions to the same data column.</span></span>  
  
 [<span data-ttu-id="437e0-114">複数の列に対して複数の検索条件を指定する (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="437e0-114">Specify Multiple Search Conditions for Multiple Columns &#40;Visual Database Tools&#41;</span></span>](specify-multiple-search-conditions-for-multiple-columns-visual-database-tools.md)  
 <span data-ttu-id="437e0-115">クエリの検索条件の一部として複数のデータ列を指定する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="437e0-115">Explains how to include several data columns as part of the search condition for a query.</span></span>  
  
 [<span data-ttu-id="437e0-116">クエリでの TOP 句の指定 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="437e0-116">Specify the TOP Clause in Queries &#40;Visual Database Tools&#41;</span></span>](specify-the-top-clause-in-queries-visual-database-tools.md)  
 <span data-ttu-id="437e0-117">指定した数または割合の行だけを返す方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="437e0-117">Explains how to have only a given number or percentage of rows returned.</span></span>  
  
 [<span data-ttu-id="437e0-118">同一クエリ内で HAVING 句および WHERE 句を使用する (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="437e0-118">Use HAVING and WHERE Clauses in the Same Query &#40;Visual Database Tools&#41;</span></span>](use-having-and-where-clauses-in-the-same-query-visual-database-tools.md)  
 <span data-ttu-id="437e0-119">この 2 つの句を 1 つのクエリで両方使用する方法と理由を説明します。</span><span class="sxs-lookup"><span data-stu-id="437e0-119">Explains how and why to use both of these clauses in a query.</span></span>  
  
 [<span data-ttu-id="437e0-120">値の一致しない行を選択する方法 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="437e0-120">Select Rows That Do Not Match a Value &#40;Visual Database Tools&#41;</span></span>](select-rows-that-do-not-match-a-value-visual-database-tools.md)  
 <span data-ttu-id="437e0-121">指定した列の値が、クエリ ステートメントで指定した値と一致しない行をすべて返す方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="437e0-121">Explains how to return all rows where the value of a give column does not match the value you provide in the query statement.</span></span>  
  
 [<span data-ttu-id="437e0-122">行を含めるまたは除外する (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="437e0-122">Include or Exclude Rows &#40;Visual Database Tools&#41;</span></span>](include-or-exclude-rows-visual-database-tools.md)  
 <span data-ttu-id="437e0-123">クエリで使用される句と演算子の背景にある概念を説明します。</span><span class="sxs-lookup"><span data-stu-id="437e0-123">Explains the concepts behind clauses and operators used in queries.</span></span>  
  
 [<span data-ttu-id="437e0-124">重複する行の除外 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="437e0-124">Exclude Duplicate Rows &#40;Visual Database Tools&#41;</span></span>](exclude-duplicate-rows-visual-database-tools.md)  
 <span data-ttu-id="437e0-125">選択クエリの結果で重複している行をフィルター処理する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="437e0-125">Explains how to filter duplicate rows out of Select queries.</span></span>  
  
 [<span data-ttu-id="437e0-126">AND が優先する場合の条件を結合する (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="437e0-126">Combine Conditions When AND Has Precedence &#40;Visual Database Tools&#41;</span></span>](combine-conditions-when-and-has-precedence-visual-database-tools.md)  
 <span data-ttu-id="437e0-127">クエリ結果をフィルター処理するために AND 演算子を使用する理由と方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="437e0-127">Explains why and how to use the AND operator to filter query results.</span></span>  
  
 [<span data-ttu-id="437e0-128">OR が優先する場合の条件を結合する (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="437e0-128">Combine Conditions When OR Has Precedence &#40;Visual Database Tools&#41;</span></span>](combine-conditions-when-or-has-precedence-visual-database-tools.md)  
 <span data-ttu-id="437e0-129">クエリ結果をフィルター処理するために OR 演算子を使用する理由と方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="437e0-129">Explains why and how to use the OR operator to filter query results.</span></span>  
  
 [<span data-ttu-id="437e0-130">サブクエリの作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="437e0-130">Create Subqueries &#40;Visual Database Tools&#41;</span></span>](create-subqueries-visual-database-tools.md)  
 <span data-ttu-id="437e0-131">サブクエリまたは入れ子になったクエリを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="437e0-131">Explains how to create subqueries, or nested queries.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="437e0-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="437e0-132">Related Sections</span></span>  
 [<span data-ttu-id="437e0-133">クエリに関する基本操作の実行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="437e0-133">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
 <span data-ttu-id="437e0-134">リンクが掲載されており、リンク先には最も一般的な問い合わせタスクの手順についてのトピックが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="437e0-134">Provides links to topics with steps for the most common querying tasks.</span></span>  
  
 [<span data-ttu-id="437e0-135">クエリの種類 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="437e0-135">Types of Queries &#40;Visual Database Tools&#41;</span></span>](types-of-queries-visual-database-tools.md)  
 <span data-ttu-id="437e0-136">リンクが掲載されており、リンク先にはサポートされているクエリの種類を解説するトピックが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="437e0-136">Provides links to topics explaining the supported query types.</span></span>  
  
 [<span data-ttu-id="437e0-137">クエリ結果の並べ替えおよびグループ化 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="437e0-137">Sort and Group Query Results &#40;Visual Database Tools&#41;</span></span>](sort-and-group-query-results-visual-database-tools.md)  
 <span data-ttu-id="437e0-138">リンクが掲載されており、リンク先にはクエリの結果を並べ替えおよびグループ化する手順に関するトピックが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="437e0-138">Provides links to topics with steps for sorting and grouping the results of a query.</span></span>  
  
 [<span data-ttu-id="437e0-139">クエリ結果の要約 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="437e0-139">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
 <span data-ttu-id="437e0-140">リンクが掲載されており、リンク先には NULL 列および数値以外の列を含む、結果の集計の手順に関するトピックが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="437e0-140">Provides links to topics with steps for summarizing results, including NULL and Nonnumeric columns.</span></span>  
  
 [<span data-ttu-id="437e0-141">クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="437e0-141">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
 <span data-ttu-id="437e0-142">クエリおよびビュー デザイナーを使用してクエリとビューで実行できる作業に関する、トピックとセクションへのリンクが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="437e0-142">Provides links to topics and sections covering work you can do in queries and views using the Query and View Designer.</span></span>  
  
  
