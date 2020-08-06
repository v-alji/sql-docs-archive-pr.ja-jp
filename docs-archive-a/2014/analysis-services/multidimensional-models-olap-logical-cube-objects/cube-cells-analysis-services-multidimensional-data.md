---
title: キューブセル (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storing data [Analysis Services], cells
- hierarchies [Analysis Services], cells
- OLAP objects [Analysis Services], cells
- data members [Analysis Services]
- cubes [Analysis Services], cells
- empty cells [Analysis Services]
- nonleaf members
- cubes [Analysis Services], examples
- storage [Analysis Services], cells
- nonleaf cells
- calculated cells [Analysis Services]
- dimensions [Analysis Services], cells
- cells [Analysis Services]
- leaf members
- leaf cells
ms.assetid: 9945773c-a43b-40d4-91cf-3d2ebc90bca5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0b55e940f75319a965fb1441520a7e16ce7ab2f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632777"
---
# <a name="cube-cells-analysis-services---multidimensional-data"></a><span data-ttu-id="abfbe-102">キューブ セル (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="abfbe-102">Cube Cells (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="abfbe-103">キューブはメジャー グループとディメンションで編成されたセルで構成されています。</span><span class="sxs-lookup"><span data-stu-id="abfbe-103">A cube is composed of cells, organized by measure groups and dimensions.</span></span> <span data-ttu-id="abfbe-104">セルは、キューブ内の各ディメンションの 1 メンバーのキューブ内の論理的な一意の交差部分を表します。</span><span class="sxs-lookup"><span data-stu-id="abfbe-104">A cell represents the unique logical intersection in a cube of one member from every dimension in the cube.</span></span> <span data-ttu-id="abfbe-105">たとえば、次のダイアグラムで示すキューブには、Source、Route、Time という 3 つのディメンションで編成された 2 つのメジャーを持つメジャー グループが 1 つ含まれています。</span><span class="sxs-lookup"><span data-stu-id="abfbe-105">For example, the cube described by the following diagram contains one measure group that has two measures, organized along three dimensions named Source, Route, and Time.</span></span>  
  
 <span data-ttu-id="abfbe-106">![1 つのセルを示すキューブ図](../../analysis-services/dev-guide/media/as-cubeintro5.gif "1 つのセルを示すキューブ図")</span><span class="sxs-lookup"><span data-stu-id="abfbe-106">![Cube diagram identifying a single cell](../../analysis-services/dev-guide/media/as-cubeintro5.gif "Cube diagram identifying a single cell")</span></span>  
  
 <span data-ttu-id="abfbe-107">このダイアグラムの 1 つの影付きセルは、次のメンバーの交差部分です。</span><span class="sxs-lookup"><span data-stu-id="abfbe-107">The single shaded cell in this diagram is the intersection of the following members:</span></span>  
  
-   <span data-ttu-id="abfbe-108">Route ディメンションの air メンバー</span><span class="sxs-lookup"><span data-stu-id="abfbe-108">The air member of the Route dimension.</span></span>  
  
-   <span data-ttu-id="abfbe-109">Source ディメンションの Africa メンバー</span><span class="sxs-lookup"><span data-stu-id="abfbe-109">The Africa member of the Source dimension.</span></span>  
  
-   <span data-ttu-id="abfbe-110">Time ディメンションの 4th quarter メンバー</span><span class="sxs-lookup"><span data-stu-id="abfbe-110">The 4th quarter member of the Time dimension.</span></span>  
  
-   <span data-ttu-id="abfbe-111">Packages メジャー</span><span class="sxs-lookup"><span data-stu-id="abfbe-111">The Packages measure.</span></span>  
  
## <a name="leaf-and-nonleaf-cells"></a><span data-ttu-id="abfbe-112">リーフ セルと非リーフ セル</span><span class="sxs-lookup"><span data-stu-id="abfbe-112">Leaf and Nonleaf Cells</span></span>  
 <span data-ttu-id="abfbe-113">キューブ内のセルの値は複数の方法で取得できます。</span><span class="sxs-lookup"><span data-stu-id="abfbe-113">The value for a cell in a cube can be obtained in one of several ways.</span></span> <span data-ttu-id="abfbe-114">前の例では、セルを識別するために使用されるすべてのメンバーが*リーフメンバー*であるため、セルの値をキューブのファクトテーブルから直接取得できます。</span><span class="sxs-lookup"><span data-stu-id="abfbe-114">In the previous example, the value in the cell can be directly retrieved from the fact table of the cube, because all the members used to identify that cell are *leaf members*.</span></span> <span data-ttu-id="abfbe-115">階層的にはリーフ メンバーに子メンバーはなく、通常はディメンション テーブルの 1 つのレコードを参照しています。</span><span class="sxs-lookup"><span data-stu-id="abfbe-115">A leaf member has no child members, hierarchically speaking, and typically references a single record in a dimension table.</span></span> <span data-ttu-id="abfbe-116">この種類のセルは、*リーフセル*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="abfbe-116">This kind of cell is referred to as a *leaf cell*.</span></span>  
  
 <span data-ttu-id="abfbe-117">ただし、*非リーフメンバー*を使用してセルを識別することもできます。</span><span class="sxs-lookup"><span data-stu-id="abfbe-117">However, a cell can also be identified by using *nonleaf members*.</span></span> <span data-ttu-id="abfbe-118">非リーフ メンバーとは、1 つ以上の子メンバーを持っているメンバーです。</span><span class="sxs-lookup"><span data-stu-id="abfbe-118">A nonleaf member is a member that has one or more child members.</span></span> <span data-ttu-id="abfbe-119">この場合、セルの値は通常、非リーフ メンバーに関連付けられている子メンバーの集計から取得されます。</span><span class="sxs-lookup"><span data-stu-id="abfbe-119">In this case, the value of the cell is typically derived from the aggregation of child members associated with the nonleaf member.</span></span> <span data-ttu-id="abfbe-120">たとえば、次のメンバーとディメンションの交差部分では、集計によって値が指定されるセルを参照します。</span><span class="sxs-lookup"><span data-stu-id="abfbe-120">For example, the intersection of the following members and dimensions refers to a cell whose value is supplied by aggregation:</span></span>  
  
-   <span data-ttu-id="abfbe-121">Route ディメンションの air メンバー</span><span class="sxs-lookup"><span data-stu-id="abfbe-121">The air member of the Route dimension.</span></span>  
  
-   <span data-ttu-id="abfbe-122">Source ディメンションの Africa メンバー</span><span class="sxs-lookup"><span data-stu-id="abfbe-122">The Africa member of the Source dimension.</span></span>  
  
-   <span data-ttu-id="abfbe-123">Time ディメンションの 2nd half メンバー</span><span class="sxs-lookup"><span data-stu-id="abfbe-123">The 2nd half member of the Time dimension.</span></span>  
  
-   <span data-ttu-id="abfbe-124">Packages メンバー</span><span class="sxs-lookup"><span data-stu-id="abfbe-124">The Packages member.</span></span>  
  
 <span data-ttu-id="abfbe-125">Time ディメンションの 2nd half メンバーは非リーフ メンバーです。</span><span class="sxs-lookup"><span data-stu-id="abfbe-125">The 2nd half member of the Time dimension is a nonleaf member.</span></span> <span data-ttu-id="abfbe-126">そのため、次のダイアグラムに示すように、2nd half メンバーに関連付けられているすべての値を集計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="abfbe-126">Therefore, all of values associated with it must be aggregated values, as shown in the following diagram.</span></span>  
  
 <span data-ttu-id="abfbe-127">![下半期メンバーの第 3 四半期セルおよび第 4 四半期セル](../../analysis-services/dev-guide/media/as-cubeintro6.gif "下半期メンバーの第 3 四半期セルおよび第 4 四半期セル")</span><span class="sxs-lookup"><span data-stu-id="abfbe-127">![3rd and 4th quarter cells for 2nd half member](../../analysis-services/dev-guide/media/as-cubeintro6.gif "3rd and 4th quarter cells for 2nd half member")</span></span>  
  
 <span data-ttu-id="abfbe-128">3rd quarter と 4th quarter の各メンバーの集計が合計であると仮定すると、指定したセルの値は、前のダイアグラムの影付きリーフ セルすべてを合計した 400 です。</span><span class="sxs-lookup"><span data-stu-id="abfbe-128">Assuming the aggregations for the 3rd quarter and 4th quarter members are summations, the value of the specified cell is 400, which is the total of all of the leaf cells shaded in the previous diagram.</span></span> <span data-ttu-id="abfbe-129">セルの値は、他のセルの集計から取得されるので、指定されたセルは*非リーフセル*と見なされます。</span><span class="sxs-lookup"><span data-stu-id="abfbe-129">Because the value of the cell is derived from the aggregation of other cells, the specified cell is considered a *nonleaf cell*.</span></span>  
  
 <span data-ttu-id="abfbe-130">カスタム メンバーだけでなくカスタム ロールアップやメンバー グループも使用しているメンバーのセルの値も、同様に取得されます。</span><span class="sxs-lookup"><span data-stu-id="abfbe-130">The cell values derived for members that use custom rollups and member groups, in addition to custom members, are handled similarly.</span></span> <span data-ttu-id="abfbe-131">ただし、計算されるメンバーのセルの値は、計算されるメンバーの定義に使用した多次元式 (MDX) 式に完全に基づいて取得されるため、場合によっては、実際のセル データは関係しないこともあります。</span><span class="sxs-lookup"><span data-stu-id="abfbe-131">However, cell values derived for calculated members are based completely on the Multidimensional Expressions (MDX) expression used to define the calculated member; in some cases, there may be no actual cell data involved.</span></span> <span data-ttu-id="abfbe-132">詳細については、「[親子ディメンションのカスタムロールアップ演算子](../multidimensional-models/parent-child-dimension-attributes-custom-rollup-operators.md)」、「[カスタムメンバー式の定義](../multidimensional-models/attribute-properties-define-custom-member-formulas.md)」、および「[計算](../multidimensional-models-olap-logical-cube-objects/calculations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abfbe-132">For more information, see [Custom Rollup Operators in Parent-Child Dimensions](../multidimensional-models/parent-child-dimension-attributes-custom-rollup-operators.md), [Define Custom Member Formulas](../multidimensional-models/attribute-properties-define-custom-member-formulas.md), and [Calculations](../multidimensional-models-olap-logical-cube-objects/calculations.md).</span></span>  
  
## <a name="empty-cells"></a><span data-ttu-id="abfbe-133">空のセル</span><span class="sxs-lookup"><span data-stu-id="abfbe-133">Empty Cells</span></span>  
 <span data-ttu-id="abfbe-134">キューブ内のすべてのセルに値が必要なわけではありません。キューブには、データのない交差部分もあります。</span><span class="sxs-lookup"><span data-stu-id="abfbe-134">It is not required that every cell in a cube contain a value; there can be intersections in a cube that have no data.</span></span> <span data-ttu-id="abfbe-135">このような交差部分は空のセルと呼ばれ、キューブ内にしばしば発生します。これは、キューブ内にメジャーを持つディメンション属性のすべての交差部分に、ファクト テーブル内の対応するレコードが含まれているとは限らないからです。</span><span class="sxs-lookup"><span data-stu-id="abfbe-135">These intersections, called empty cells, frequently occur in cubes because not every intersection of a dimension attribute with a measure within a cube contains a corresponding record in a fact table.</span></span> <span data-ttu-id="abfbe-136">キューブ内のセルの合計数に対するキューブ内の空のセルの比率は、一般にキューブの*密度*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="abfbe-136">The ratio of empty cells in a cube to the total number of cells in a cube is frequently referred to as the *sparsity* of a cube.</span></span>  
  
 <span data-ttu-id="abfbe-137">たとえば、次のダイアグラムに示すキューブは、このトピックの他の例に似ていますが、</span><span class="sxs-lookup"><span data-stu-id="abfbe-137">For example, the structure of the cube shown in the following diagram is similar to other examples in this topic.</span></span> <span data-ttu-id="abfbe-138">この例では、第 3 四半期の Africa または第 4 四半期の Australia への air による出荷が含まれていません。</span><span class="sxs-lookup"><span data-stu-id="abfbe-138">However, in this example, there were no air shipments to Africa for the third quarter or to Australia for the fourth quarter.</span></span> <span data-ttu-id="abfbe-139">これらのディメンションとメジャーの交差部分に対応するデータはファクト テーブルにありません。そのため、この交差部分にあるセルは空になります。</span><span class="sxs-lookup"><span data-stu-id="abfbe-139">There is no data in the fact table to support the intersections of those dimensions and measures; therefore the cells at those intersections are empty.</span></span>  
  
 <span data-ttu-id="abfbe-140">![空のセルを示すキューブ図](../../analysis-services/dev-guide/media/as-cubeintro7.gif "空のセルを示すキューブ図")</span><span class="sxs-lookup"><span data-stu-id="abfbe-140">![Cube diagram identifying empty cells](../../analysis-services/dev-guide/media/as-cubeintro7.gif "Cube diagram identifying empty cells")</span></span>  
  
 <span data-ttu-id="abfbe-141">では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、空のセルは特殊な品質を持つセルです。</span><span class="sxs-lookup"><span data-stu-id="abfbe-141">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], an empty cell is a cell that has special qualities.</span></span> <span data-ttu-id="abfbe-142">空のセルは、相互結合、カウントなどの結果を非対称にできるため、多くの MDX 関数は、計算のために空のセルを無視する機能を提供しています。</span><span class="sxs-lookup"><span data-stu-id="abfbe-142">Because empty cells can skew the results of crossjoins, counts, and so on, many MDX functions supply the ability to ignore empty cells for the purposes of calculation.</span></span> <span data-ttu-id="abfbe-143">詳細については、「 [mdx&#41; 参照 &#40;の多次元式](/sql/mdx/multidimensional-expressions-mdx-reference)」および「 [mdx &#40;Analysis Services&#41;の主要概念](../multidimensional-models/key-concepts-in-mdx-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abfbe-143">For more information, see [Multidimensional Expressions &#40;MDX&#41; Reference](/sql/mdx/multidimensional-expressions-mdx-reference), and [Key Concepts in MDX &#40;Analysis Services&#41;](../multidimensional-models/key-concepts-in-mdx-analysis-services.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="abfbe-144">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="abfbe-144">Security</span></span>  
 <span data-ttu-id="abfbe-145">セル データへのアクセスは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のロール レベルで管理され、MDX 式を使用して細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="abfbe-145">Access to cell data is managed in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] at the role level, and can be finely controlled by using MDX expressions.</span></span> <span data-ttu-id="abfbe-146">詳細については、「[ディメンションデータへのカスタムアクセス権の付与 &#40;Analysis Services&#41;](../multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md)」および「[セルデータへのカスタムアクセス権の付与 &#40;Analysis Services&#41;](../multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abfbe-146">For more information, see [Grant custom access to dimension data &#40;Analysis Services&#41;](../multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md), and [Grant custom access to cell data &#40;Analysis Services&#41;](../multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abfbe-147">参照</span><span class="sxs-lookup"><span data-stu-id="abfbe-147">See Also</span></span>  
 <span data-ttu-id="abfbe-148">[Cube Storage &#40;Analysis Services-多次元データ&#41;](../multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="abfbe-148">[Cube Storage &#40;Analysis Services - Multidimensional Data&#41;](../multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="abfbe-149">集計と集計デザイン</span><span class="sxs-lookup"><span data-stu-id="abfbe-149">Aggregations and Aggregation Designs</span></span>](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
