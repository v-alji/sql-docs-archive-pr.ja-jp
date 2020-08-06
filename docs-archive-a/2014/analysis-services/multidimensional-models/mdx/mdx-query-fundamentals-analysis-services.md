---
title: MDX クエリの基礎 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- statements [MDX]
- Multidimensional Expressions [Analysis Services], statements
- Multidimensional Expressions [Analysis Services], queries
- MDX [Analysis Services], statements
- MDX queries [Analysis Services]
- MDX [Analysis Services], queries
- queries [MDX]
ms.assetid: a560383b-bb58-472e-95f5-65d03d8ea08b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1a2a9a4f564bc33cc7a1b41a1a4c766c7a76a2cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643577"
---
# <a name="mdx-query-fundamentals-analysis-services"></a><span data-ttu-id="f8e87-102">MDX クエリの基礎 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="f8e87-102">MDX Query Fundamentals (Analysis Services)</span></span>
  <span data-ttu-id="f8e87-103">多次元式 (MDX) を使用すれば、多次元オブジェクト (たとえばキューブ) をクエリして、キューブ データが格納された多次元セル セットを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="f8e87-103">Multidimensional Expressions (MDX) lets you query multidimensional objects, such as cubes, and return multidimensional cellsets that contain the cube's data.</span></span> <span data-ttu-id="f8e87-104">このトピックとサブトピックでは、MDX クエリの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="f8e87-104">This topic and its subtopics provide an overview of MDX queries.</span></span>  
  
 <span data-ttu-id="f8e87-105">以下のトピックでは、MDX クエリとクエリが作成するセル セットについて、および基本的な MDX 構文の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="f8e87-105">The following topics describe MDX queries and the cellsets they produce, and provide more detailed information about basic MDX syntax.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f8e87-106">MDX クエリおよび計算に関連するパフォーマンスの問題の詳細については、「 [SQL Server 2005 Analysis Services パフォーマンスガイド](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide)」の「効率的な Mdx の記述」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8e87-106">For more information about performance issues related to MDX queries and calculations, see the section "Writing Efficient MDX" in the [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f8e87-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f8e87-107">In This Section</span></span>  
  
|<span data-ttu-id="f8e87-108">トピック</span><span class="sxs-lookup"><span data-stu-id="f8e87-108">Topic</span></span>|<span data-ttu-id="f8e87-109">説明</span><span class="sxs-lookup"><span data-stu-id="f8e87-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f8e87-110">MDX の基本的なクエリ &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="f8e87-110">The Basic MDX Query &#40;MDX&#41;</span></span>](mdx-query-the-basic-query.md)|<span data-ttu-id="f8e87-111">MDX SELECT ステートメントの基本的な構文について説明します。</span><span class="sxs-lookup"><span data-stu-id="f8e87-111">Provides basic syntax information for the MDX SELECT statement.</span></span>|  
|[<span data-ttu-id="f8e87-112">クエリ軸とスライサー軸によるクエリの制限 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="f8e87-112">Restricting the Query with Query and Slicer Axes &#40;MDX&#41;</span></span>](mdx-query-and-slicer-axes-restricting-the-query.md)|<span data-ttu-id="f8e87-113">クエリ軸とスライサー軸、およびそれらを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f8e87-113">Describes what query and slicer axes are and how to specify them.</span></span>|  
|[<span data-ttu-id="f8e87-114">クエリ内のキューブ コンテキストの確立 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="f8e87-114">Establishing Cube Context in a Query &#40;MDX&#41;</span></span>](establishing-cube-context-in-a-query-mdx.md)|<span data-ttu-id="f8e87-115">MDX SELECT ステートメントでの FROM 句の用途を説明します。</span><span class="sxs-lookup"><span data-stu-id="f8e87-115">Provides a description of the purpose of the FROM clause in an MDX SELECT statement.</span></span>|  
|[<span data-ttu-id="f8e87-116">MDX での名前付きセットの作成 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="f8e87-116">Building Named Sets in MDX &#40;MDX&#41;</span></span>](mdx-named-sets-building-named-sets.md)|<span data-ttu-id="f8e87-117">MDX での名前付きセットの用途と、名前付きセットを MDX クエリ内で作成および使用するために必要なテクニックについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f8e87-117">Describes the purpose of named sets in MDX, and the techniques needed to create and use them in MDX queries.</span></span>|  
|[<span data-ttu-id="f8e87-118">MDX での計算されるメンバーの作成 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="f8e87-118">Building Calculated Members in MDX &#40;MDX&#41;</span></span>](mdx-calculated-members-building-calculated-members.md)|<span data-ttu-id="f8e87-119">MDX での計算されるメンバーに関する情報と、計算されるメンバーを MDX 式内で作成および使用するために必要なテクニックについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f8e87-119">Provides information about calculated members in MDX, including the techniques needed to create and use them in MDX expressions.</span></span>|  
|[<span data-ttu-id="f8e87-120">MDX でのセル計算の作成 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="f8e87-120">Building Cell Calculations in MDX &#40;MDX&#41;</span></span>](../../multidimensional-models-olap-logical-cube-objects/calculations.md)|<span data-ttu-id="f8e87-121">計算されるセルを作成および使用する処理の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="f8e87-121">Details the process of creating and using calculated cells.</span></span>|  
|[<span data-ttu-id="f8e87-122">プロパティ値の作成および使用 (MDX)</span><span class="sxs-lookup"><span data-stu-id="f8e87-122">Creating and Using Property Values &#40;MDX&#41;</span></span>](../../creating-and-using-property-values-mdx.md)|<span data-ttu-id="f8e87-123">ディメンション、レベル、メンバー、およびセルの各プロパティの作成時および使用時の処理の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="f8e87-123">Details the process of creating and using dimension, level, member, and cell properties.</span></span>|  
|[<span data-ttu-id="f8e87-124">データの操作 (MDX)</span><span class="sxs-lookup"><span data-stu-id="f8e87-124">Manipulating Data &#40;MDX&#41;</span></span>](mdx-data-manipulation-manipulating-data.md)|<span data-ttu-id="f8e87-125">ドリルスルーとロールアップを使ったデータ操作の基礎について、および MDX でのパス順序と解決順序について説明します。</span><span class="sxs-lookup"><span data-stu-id="f8e87-125">Describes the basics behind manipulating data using drillthrough and rollup, and also describes pass order and solve order in MDX.</span></span>|  
|[<span data-ttu-id="f8e87-126">データの変更 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="f8e87-126">Modifying Data &#40;MDX&#41;</span></span>](mdx-data-modification-modifying-data.md)|<span data-ttu-id="f8e87-127">書き戻しを使って多次元データを一時的または永続的に変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f8e87-127">Describes how to use writebacks to temporarily or permanently change multidimensional data.</span></span>|  
|[<span data-ttu-id="f8e87-128">変数とパラメーターの使用 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="f8e87-128">Using Variables and Parameters &#40;MDX&#41;</span></span>](using-variables-and-parameters-mdx.md)|<span data-ttu-id="f8e87-129">MDX クエリ内での変数およびパラメーターの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f8e87-129">Describes how to use variables and parameters within MDX queries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f8e87-130">参照</span><span class="sxs-lookup"><span data-stu-id="f8e87-130">See Also</span></span>  
 [<span data-ttu-id="f8e87-131">多次元式 &#40;MDX&#41; リファレンス</span><span class="sxs-lookup"><span data-stu-id="f8e87-131">Multidimensional Expressions &#40;MDX&#41; Reference</span></span>](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
