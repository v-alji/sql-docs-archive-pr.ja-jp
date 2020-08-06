---
title: 結合を使用したクエリ (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [Visual Database Tools]
- View Designer, joins
- table joins [SQL Server]
- multiple table joins
- Visual Database Tools [SQL Server], queries
- Query Designer [SQL Server], joins
- joins [SQL Server], queries
ms.assetid: 8f068207-d777-4e64-8c4c-d821f0ddb450
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9d0053e6786d96508be8a87347cdc0b19975a3fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713673"
---
# <a name="query-with-joins-visual-database-tools"></a><span data-ttu-id="9b08d-102">結合を使用したクエリ (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9b08d-102">Query with Joins (Visual Database Tools)</span></span>
  <span data-ttu-id="9b08d-103">クエリ結果には、複数のテーブルまたはテーブル値オブジェクトのデータを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="9b08d-103">A query result can include data from multiple tables or table-valued objects.</span></span> <span data-ttu-id="9b08d-104">複数のテーブル値オブジェクトのデータを結合するには、SQL の JOIN 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="9b08d-104">To combine data from multiple table-valued objects, you use the JOIN operation from SQL.</span></span>  
  
 <span data-ttu-id="9b08d-105">複数のテーブルを使用するクエリを作成する方法の詳細については、次の各トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b08d-105">For information about creating queries using multiple tables, see the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b08d-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9b08d-106">In This Section</span></span>  
 [<span data-ttu-id="9b08d-107">結合演算子の変更 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9b08d-107">Modify Join Operators &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
 <span data-ttu-id="9b08d-108">テーブルを等号 (=) 以外の演算子で結合する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="9b08d-108">Specify that tables should be joined using an operator other than equal (=).</span></span>  
  
 [<span data-ttu-id="9b08d-109">クエリおよびビュー デザイナーでの結合の表示方法 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9b08d-109">How the Query and View Designer Represents Joins &#40;Visual Database Tools&#41;</span></span>](how-the-query-and-view-designer-represents-joins-visual-database-tools.md)  
 <span data-ttu-id="9b08d-110">ダイアグラム ペインに表示される結合のグラフィック記号について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b08d-110">Explains the graphic representation of the join as you see it in the Diagram pane.</span></span>  
  
 [<span data-ttu-id="9b08d-111">テーブルの自動結合 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9b08d-111">Join Tables Automatically &#40;Visual Database Tools&#41;</span></span>](join-tables-automatically-visual-database-tools.md)  
 <span data-ttu-id="9b08d-112">テーブルを結合すべきかどうかをクエリおよびビュー デザイナーを使用して判断する手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="9b08d-112">Steps for allowing the Query and View Designer determine if tables should be joined.</span></span>  
  
 [<span data-ttu-id="9b08d-113">手動でのテーブルの結合 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9b08d-113">Join Tables Manually &#40;Visual Database Tools&#41;</span></span>](join-tables-manually-visual-database-tools.md)  
 <span data-ttu-id="9b08d-114">ダイアグラム ペインを使用して手動で結合を行う手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="9b08d-114">Steps for creating a join manually in the Diagram pane.</span></span>  
  
 [<span data-ttu-id="9b08d-115">複数の列でテーブルを結合する (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9b08d-115">Join Tables on Multiple Columns &#40;Visual Database Tools&#41;</span></span>](join-tables-on-multiple-columns-visual-database-tools.md)  
 <span data-ttu-id="9b08d-116">各テーブルに複数の条件を指定して、それらのテーブルを結合する手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="9b08d-116">Steps for joining tables with multiple criteria for each table.</span></span>  
  
 [<span data-ttu-id="9b08d-117">外部結合の作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9b08d-117">Create Outer Joins &#40;Visual Database Tools&#41;</span></span>](create-outer-joins-visual-database-tools.md)  
 <span data-ttu-id="9b08d-118">一致する行が対応するテーブルにない場合でも、結合したテーブルにはその行を含める方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="9b08d-118">Specify that joined tables should include rows even when they do not match rows in the corresponding table.</span></span>  
  
 [<span data-ttu-id="9b08d-119">結合の削除 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9b08d-119">Remove Joins &#40;Visual Database Tools&#41;</span></span>](remove-joins-visual-database-tools.md)  
 <span data-ttu-id="9b08d-120">テーブル間の結合を削除する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b08d-120">Steps for removing a join between tables.</span></span>  
  
 [<span data-ttu-id="9b08d-121">自己結合の自動作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9b08d-121">Create Self-Joins Automatically &#40;Visual Database Tools&#41;</span></span>](create-self-joins-automatically-visual-database-tools.md)  
 <span data-ttu-id="9b08d-122">クエリおよびビュー デザイナーで自己結合を作成する手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="9b08d-122">Steps for allowing the Query and View Designer to create a self-join.</span></span>  
  
 [<span data-ttu-id="9b08d-123">自己結合の手動作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9b08d-123">Create Self-Joins Manually &#40;Visual Database Tools&#41;</span></span>](create-self-joins-manually-visual-database-tools.md)  
 <span data-ttu-id="9b08d-124">結合を使用して、1 つのテーブルの中のデータのサブセットを検索する手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="9b08d-124">Steps for using a join to find subsets of data within a single table.</span></span>  
  
 [<span data-ttu-id="9b08d-125">結合のプロパティの表示 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9b08d-125">View Join Properties &#40;Visual Database Tools&#41;</span></span>](view-join-properties-visual-database-tools.md)  
 <span data-ttu-id="9b08d-126">結合のプロパティの表示手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="9b08d-126">Steps for viewing the properties of a join.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9b08d-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b08d-127">Related Sections</span></span>  
 [<span data-ttu-id="9b08d-128">クエリの種類 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9b08d-128">Types of Queries &#40;Visual Database Tools&#41;</span></span>](types-of-queries-visual-database-tools.md)  
 <span data-ttu-id="9b08d-129">サポートされているクエリ型を説明するトピックへのリンクが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9b08d-129">Provides links to topics describing the supported query types.</span></span>  
  
 [<span data-ttu-id="9b08d-130">クエリに関する基本操作の実行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9b08d-130">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
 <span data-ttu-id="9b08d-131">最も一般的なクエリ タスクに関するトピックへのリンクが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9b08d-131">Provides links to topics covering the most common query tasks.</span></span>  
  
 [<span data-ttu-id="9b08d-132">検索基準の指定 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9b08d-132">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
 <span data-ttu-id="9b08d-133">各種の検索条件とそれらの使用方法に関するトピックへのリンクが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9b08d-133">Provides links to topics covering the various kinds of search criteria and how to use them.</span></span>  
  
  
