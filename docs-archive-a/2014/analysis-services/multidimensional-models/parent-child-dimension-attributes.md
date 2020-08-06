---
title: 親子階層の属性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data members [Analysis Services]
- nonleaf members
- MembersWithDataCaption property
- members [Analysis Services]
- members [Analysis Services], data
- leaf members
- parent-child dimensions [Analysis Services]
- MembersWithData property
ms.assetid: 249971cc-4bcd-44f1-8241-bdacc04d3d38
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5c4a7e8ba43ac8ede0bd60409f84a6fa233ce182
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714630"
---
# <a name="attributes-in-parent-child-hierarchies"></a><span data-ttu-id="b0504-102">親子階層の属性</span><span class="sxs-lookup"><span data-stu-id="b0504-102">Attributes in Parent-Child Hierarchies</span></span>
  <span data-ttu-id="b0504-103">では [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 、通常、ディメンションのメンバーのコンテンツに関して一般的な想定が行われます。</span><span class="sxs-lookup"><span data-stu-id="b0504-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], a general assumption is usually made about the content of members in a dimension.</span></span> <span data-ttu-id="b0504-104">リーフ メンバーには、基になるデータ ソースから直接派生したデータが含まれ、非リーフ メンバーには、子メンバーで実行した集計から算出したデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b0504-104">Leaf members contain data derived directly from underlying data sources; nonleaf members contain data derived from aggregations performed on child members.</span></span>  
  
 <span data-ttu-id="b0504-105">ただし、親子階層では、一部の非リーフ メンバーに、子メンバーから取得したデータだけでなく、基になるデータ ソースから取得したデータも含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="b0504-105">In a parent-child hierarchy, however, some nonleaf members may also have data derived from underlying data sources, in addition to data aggregated from child members.</span></span> <span data-ttu-id="b0504-106">親子階層の非リーフ メンバーの場合、基になるファクト テーブル データを含む特殊なシステム生成の子メンバーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b0504-106">For these nonleaf members in a parent-child hierarchy, special system-generated child members are created that contain the underlying fact table data.</span></span> <span data-ttu-id="b0504-107">これらの子メンバーは *データ メンバー*と呼ばれ、非リーフ メンバーの子孫から計算される集計値に依存しない、非リーフ メンバーに直接関係付けられた値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b0504-107">Referred to as *data members*, they contain a value directly associated with a nonleaf member that is independent of the summary value calculated from the descendants of the nonleaf member.</span></span>  
  
 <span data-ttu-id="b0504-108">データ メンバーは、親子階層を持つディメンションでのみ使用でき、親属性によって許可される場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0504-108">Data members are available only to dimensions with parent-child hierarchies, and are visible only if allowed by the parent attribute.</span></span> <span data-ttu-id="b0504-109">ディメンション デザイナーを使用すると、データ メンバーの表示を制御できます。</span><span class="sxs-lookup"><span data-stu-id="b0504-109">You can use Dimension Designer to control the visibility of data members.</span></span> <span data-ttu-id="b0504-110">データ メンバーを公開するには、親属性の `MembersWithData` プロパティを `NonLeafDataVisible.` に設定します。親属性に含まれているデータ メンバーを非表示にするには、親属性の `MembersWithData` プロパティを `NonLeafDataHidden` に設定します。</span><span class="sxs-lookup"><span data-stu-id="b0504-110">To expose data members, set the `MembersWithData` property for the parent attribute to `NonLeafDataVisible.` To hide data members contained by the parent attribute, set the `MembersWithData` property on the parent attribute to `NonLeafDataHidden`.</span></span>  
  
 <span data-ttu-id="b0504-111">この設定により、非リーフ メンバーの通常の集計動作がオーバーライドされることはありません。データ メンバーは、常に集計の目的で子メンバーとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b0504-111">This setting does not override the normal aggregation behavior for nonleaf members; the data member is always included as a child member for the purposes of aggregation.</span></span> <span data-ttu-id="b0504-112">ただし、カスタム ロールアップ式を使用して通常の集計動作をオーバーライドすることはできます。</span><span class="sxs-lookup"><span data-stu-id="b0504-112">However, a custom rollup formula can be used to override the normal aggregation behavior.</span></span> <span data-ttu-id="b0504-113">多次元式 (MDX) の[DataMember](/sql/mdx/datamember-mdx)関数を使用すると、プロパティの値に関係なく、関連付けられているデータメンバーの値にアクセスでき `MembersWithData` ます。</span><span class="sxs-lookup"><span data-stu-id="b0504-113">The Multidimensional Expressions (MDX) [DataMember](/sql/mdx/datamember-mdx) function gives you the ability to access the value of the associated data member regardless of the value of the `MembersWithData` property.</span></span>  
  
 <span data-ttu-id="b0504-114">親属性の `MembersWithDataCaption` プロパティを使用すると、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] で名前付けテンプレートを使用してデータ メンバーのメンバー名を生成できます。</span><span class="sxs-lookup"><span data-stu-id="b0504-114">The `MembersWithDataCaption` property of the parent attribute provides [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] with the naming template used to generate member names for data members.</span></span>  
  
## <a name="using-data-members"></a><span data-ttu-id="b0504-115">データ メンバーの使用</span><span class="sxs-lookup"><span data-stu-id="b0504-115">Using Data Members</span></span>  
 <span data-ttu-id="b0504-116">データ メンバーは、親子階層を持つ組織ディメンションに従ってメジャーを集計する際に便利です。</span><span class="sxs-lookup"><span data-stu-id="b0504-116">Data members are useful when aggregating measures along organizational dimensions that have parent-child hierarchies.</span></span> <span data-ttu-id="b0504-117">たとえば、次の図は、製品の総売上高を表す 3 つのレベルを持つディメンションを示しています。</span><span class="sxs-lookup"><span data-stu-id="b0504-117">For example, the following diagram shows a dimension that has three levels, representing the gross sales volume of products.</span></span> <span data-ttu-id="b0504-118">最初のレベルは、全販売員の総売上高を示します。</span><span class="sxs-lookup"><span data-stu-id="b0504-118">The first level shows the gross sales volume for all salespersons.</span></span> <span data-ttu-id="b0504-119">第 2 のレベルには営業責任者別にグループ化された全販売担当者の総売上高が含まれ、第 3 のレベルには販売員別にグループ化された全販売担当者の総売上高が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b0504-119">The second level contains the gross sales volume for all sales staff grouped by sales manager, and the third level contains the gross sales volume for all sales staff grouped by salesperson.</span></span>  
  
 <span data-ttu-id="b0504-120">![3 つのレベルから成る総売上高ディメンション](../media/agdatamember1.gif "3 つのレベルから成る総売上高ディメンション")</span><span class="sxs-lookup"><span data-stu-id="b0504-120">![Gross sales volume dimension with three levels](../media/agdatamember1.gif "Gross sales volume dimension with three levels")</span></span>  
  
 <span data-ttu-id="b0504-121">通常、Sales Manager 1 メンバーの値は、Salesperson 1 メンバーと Salesperson 2 メンバーの値を集計することによって取得されます。</span><span class="sxs-lookup"><span data-stu-id="b0504-121">Ordinarily, the value of the Sales Manager 1 member would be derived by aggregating the values of the Salesperson 1 and Salesperson 2 members.</span></span> <span data-ttu-id="b0504-122">ただし、Sales Manager 1 も製品を販売でき、Sales Manager 1 に関連した総売上が存在する場合もあるため、このメンバーにはファクト テーブルから取得したデータも格納されていることがあります。</span><span class="sxs-lookup"><span data-stu-id="b0504-122">However, because Sales Manager 1 also can sell products, that member may also contain data derived from the fact table, because there may be gross sales associated with Sales Manager 1.</span></span>  
  
 <span data-ttu-id="b0504-123">さらに、各販売担当者メンバーの個々の歩合は異なることがあります。</span><span class="sxs-lookup"><span data-stu-id="b0504-123">Moreover, the individual commissions for each sales staff member can vary.</span></span> <span data-ttu-id="b0504-124">この場合、販売員による総売上の合計ではなく、2 つの異なる尺度を使用して営業責任者の個々の総売上に対する歩合が計算されます。</span><span class="sxs-lookup"><span data-stu-id="b0504-124">In this case, two different scales are used to compute commissions for the individual gross sales of the sales managers, as opposed to the total of gross sales generated by their salespersons.</span></span> <span data-ttu-id="b0504-125">そのため、非リーフ メンバーの基になるファクト テーブル データにアクセスできることが重要になります。</span><span class="sxs-lookup"><span data-stu-id="b0504-125">Therefore, it is important to be able to access the underlying fact table data for nonleaf members.</span></span> <span data-ttu-id="b0504-126">MDX の `DataMember` 関数を使用すると、Sales Manager 1 メンバーの個々の総売上高を取得することができ、カスタム ロールアップ式を使用すると、Sales Manager 1 メンバーの集計値からデータ メンバーを除外できます。これにより、そのメンバーに関連付けられた販売員の総売上高が得られます。</span><span class="sxs-lookup"><span data-stu-id="b0504-126">The MDX `DataMember` function can be used to retrieve the individual gross sales volume of the Sales Manager 1 member, and a custom rollup expression can be used to exclude the data member from the aggregated value of the Sales Manager 1 member, providing the gross sales volume of the salespersons associated with that member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0504-127">参照</span><span class="sxs-lookup"><span data-stu-id="b0504-127">See Also</span></span>  
 <span data-ttu-id="b0504-128">[ディメンションの属性のプロパティのリファレンス](dimension-attribute-properties-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b0504-128">[Dimension Attribute Properties Reference](dimension-attribute-properties-reference.md) </span></span>  
 [<span data-ttu-id="b0504-129">親子階層</span><span class="sxs-lookup"><span data-stu-id="b0504-129">Parent-Child Hierarchy</span></span>](parent-child-dimension.md)  
  
  
