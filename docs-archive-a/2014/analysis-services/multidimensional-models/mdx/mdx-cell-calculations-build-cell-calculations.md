---
title: MDX でのセル計算の作成 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculated cells [MDX]
- queries [MDX], cell calculations
- cells [MDX]
- MDX [Analysis Services], calculations
- calculation subcubes [MDX]
- calculated values [MDX]
- Multidimensional Expressions [Analysis Services], cell calculations
ms.assetid: 068aea63-d419-4791-a960-3d74e76f808e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9ab3219850c49c2ec16a12aab3ba7db67e9a8721
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718783"
---
# <a name="building-cell-calculations-in-mdx-mdx"></a><span data-ttu-id="ef663-102">MDX でのセル計算の作成 (MDX)</span><span class="sxs-lookup"><span data-stu-id="ef663-102">Building Cell Calculations in MDX (MDX)</span></span>
  <span data-ttu-id="ef663-103">多次元式 (MDX) では、計算されるメンバー、カスタム ロールアップ、およびカスタム メンバーなど、計算値を生成するための多数のツールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef663-103">Multidimensional Expressions (MDX) provides you with a number of tools for generating calculated values, such as calculated members, custom rollups, and custom members.</span></span> <span data-ttu-id="ef663-104">しかし、これらの機能を使用して特定のセル セットや、さらには単一セルに影響を与えるのは困難です。</span><span class="sxs-lookup"><span data-stu-id="ef663-104">However, using these features to affect a specific set of cells, or a single cell for that matter, would be difficult.</span></span>  
  
 <span data-ttu-id="ef663-105">セルに対して個別に計算値を生成するには、MDX の計算されるセル機能を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef663-105">To generated calculated values for specifically for cells, you need to use the calculated cells feature in MDX.</span></span> <span data-ttu-id="ef663-106">計算されるセルを使用すると、 *計算サブキューブ*と呼ばれる特定のセル スライスを定義し、計算サブキューブ内のすべてのセルに個別に式を適用できます。</span><span class="sxs-lookup"><span data-stu-id="ef663-106">Calculated cells let you define a specific slice of cells, called a *calculation subcube*, and apply a formula to each and every cell within the calculation subcube, subject to an optional condition that can be applied to each cell.</span></span>  
  
 <span data-ttu-id="ef663-107">計算されるセルでは、KPI で使用されるゴールシーク数式や推測分析の式などの複雑な機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef663-107">Calculated cells also offer complex functionality, such as goal-seeking formulas, as used in KPIs, or speculative analysis formulas.</span></span> <span data-ttu-id="ef663-108">このレベルの機能は、パス順序の特定の [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] パスに計算式を適用し、計算されるセルを使用して再帰的なパスを作成できるようにする、のパス順序機能から取得します。</span><span class="sxs-lookup"><span data-stu-id="ef663-108">This level of functionality comes from the pass order feature in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] that allows recursive passes to be made with calculated cells, with calculation formulas applied at specific passes in the pass order.</span></span> <span data-ttu-id="ef663-109">パス順序の詳細については、「[パス順序と解決順序の概要 (MDX)](mdx-data-manipulation-understanding-pass-order-and-solve-order.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef663-109">For more information on pass order, see [Understanding Pass Order and Solve Order &#40;MDX&#41;](mdx-data-manipulation-understanding-pass-order-and-solve-order.md).</span></span>  
  
 <span data-ttu-id="ef663-110">計算されるセルは、作成の有効範囲の点で、名前付きセットと計算されるメンバーの両方に似ています。計算されるセルは、セッションまたは 1 回のクエリの有効期限に合わせて一時的に作成することも、キューブの一部としてグローバルに使用可能にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ef663-110">In terms of creation scope, calculated cells are similar to both named sets and calculated members in that calculated cells can be temporarily created for the lifetime of either a session or a single query, or made globally available as part of a cube:</span></span>  
  
-   <span data-ttu-id="ef663-111">**クエリ スコープ** MDX クエリの一部として定義する、計算されるセルを作成する場合 (つまり、スコープをそのクエリに限定する場合) は、WITH キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="ef663-111">**Query-scoped** To create a calculated cell that is defined as part of an MDX query, and therefore whose scope is limited to the query, you use the WITH keyword.</span></span> <span data-ttu-id="ef663-112">その計算されるセルは、MDX の SELECT ステートメントの中で使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef663-112">You can then use the calculated cell within an MDX SELECT statement.</span></span> <span data-ttu-id="ef663-113">この方法では、`WITH` キーワードを使用して作成した計算されるセルを、SELECT ステートメントを修正せずに変更できます。</span><span class="sxs-lookup"><span data-stu-id="ef663-113">Using this approach, the calculated cell created by using the `WITH` keyword can be changed without disturbing the SELECT statement.</span></span>  
  
     <span data-ttu-id="ef663-114">WITH キーワードを使用して計算されるメンバーを作成する方法の詳細については、「 [クエリ スコープのセル計算の作成 (MDX)](../../multidimensional-models-olap-logical-cube-objects/calculations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef663-114">For more information about how to use the WITH keyword to create calculated members, see [Creating Query-Scoped Cell Calculations &#40;MDX&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md).</span></span>  
  
-   <span data-ttu-id="ef663-115">**セッション スコープ** クエリのコンテキストよりも広いスコープを設定して計算されるセルを作成する場合 (つまり、スコープを MDX セッションの有効期間全体とする場合) は、CREATE CELL CALCULATION または ALTER CUBE ステートメントのいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="ef663-115">**Session-scoped** To create a calculated member whose scope is wider than the context of the query, that is, whose scope is the lifetime of the MDX session, you use either the CREATE CELL CALCULATION or ALTER CUBE statement.</span></span>  
  
     <span data-ttu-id="ef663-116">CREATE CELL CALCULATION または ALTER CUBE ステートメントを使用してセッションでの計算されるセルを作成する方法の詳細については、「 [セッション スコープの計算されるセルの作成](mdx-cell-calculations-session-scoped-calculated-cells.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef663-116">For more information about how to use either the CREATE CELL CALCULATION or ALTER CUBE statement to create calculated cells in a session, see [Creating Session-Scoped Calculated Cells](mdx-cell-calculations-session-scoped-calculated-cells.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef663-117">参照</span><span class="sxs-lookup"><span data-stu-id="ef663-117">See Also</span></span>  
 <span data-ttu-id="ef663-118">[ALTER CUBE ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-definition-alter-cube) </span><span class="sxs-lookup"><span data-stu-id="ef663-118">[ALTER CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-alter-cube) </span></span>  
 <span data-ttu-id="ef663-119">[CREATE CELL CALCULATION ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-cell-calculation) </span><span class="sxs-lookup"><span data-stu-id="ef663-119">[CREATE CELL CALCULATION Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-cell-calculation) </span></span>  
 <span data-ttu-id="ef663-120">[MDX&#41;&#40;クエリスコープのセル計算を作成する](../../multidimensional-models-olap-logical-cube-objects/calculations.md) </span><span class="sxs-lookup"><span data-stu-id="ef663-120">[Creating Query-Scoped Cell Calculations &#40;MDX&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md) </span></span>  
 [<span data-ttu-id="ef663-121">MDX クエリの基礎 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ef663-121">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
