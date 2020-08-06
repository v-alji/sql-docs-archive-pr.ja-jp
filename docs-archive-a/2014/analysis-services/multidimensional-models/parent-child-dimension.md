---
title: 親子階層 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], parent-child
- dimensions [Analysis Services], parent-child
- parent attributes [Analysis Services]
- data members [Analysis Services]
- hierarchies [Analysis Services], multilevel
- self-joins
- self-referencing relationships
- members [Analysis Services], data
- parent-child dimensions [Analysis Services]
ms.assetid: 4657f5dc-d88e-48d2-a448-08f79bc89546
author: minewiskan
ms.author: owend
ms.openlocfilehash: b08641e9ba17e6ad2e2f4112e01073d448aa8564
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742618"
---
# <a name="parent-child-hierarchy"></a><span data-ttu-id="91f01-102">親子階層</span><span class="sxs-lookup"><span data-stu-id="91f01-102">Parent-Child Hierarchy</span></span>
  <span data-ttu-id="91f01-103">親子階層は、親属性を含んでいる標準ディメンションにある階層です。</span><span class="sxs-lookup"><span data-stu-id="91f01-103">A parent-child hierarchy is a hierarchy in a standard dimension that contains a parent attribute.</span></span> <span data-ttu-id="91f01-104">親属性は、ディメンション メイン テーブル内の *自己参照型リレーションシップ*または *自己結合*を記述します。</span><span class="sxs-lookup"><span data-stu-id="91f01-104">A parent attribute describes a *self-referencing relationship*, or *self-join*, within a dimension main table.</span></span> <span data-ttu-id="91f01-105">親子階層は 1 つの親属性から構築されます。</span><span class="sxs-lookup"><span data-stu-id="91f01-105">Parent-child hierarchies are constructed from a single parent attribute.</span></span> <span data-ttu-id="91f01-106">親子階層に存在するレベルは、親属性に関連付けられているメンバー間の親子リレーションシップに基づいているので、1 つの親子階層に割り当てられるレベルは 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="91f01-106">Only one level is assigned to a parent-child hierarchy, because the levels present in the hierarchy are drawn from the parent-child relationships between members associated with the parent attribute.</span></span> <span data-ttu-id="91f01-107">親子階層内でのメンバーの位置は、親属性の `KeyColumns` プロパティおよび `RootMemberIf` プロパティで決まります。一方、レベル内でのメンバーの位置は、親属性の `OrderBy` プロパティで決まります。</span><span class="sxs-lookup"><span data-stu-id="91f01-107">The position of a member in a parent-child hierarchy is determined by the `KeyColumns` and `RootMemberIf` properties of the parent attribute, whereas the position of a member in a level is determined by the `OrderBy` property of the parent attribute.</span></span> <span data-ttu-id="91f01-108">属性のプロパティの詳細については、「 [属性と属性階層](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91f01-108">For more information about attribute properties, see [Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).</span></span>  
  
 <span data-ttu-id="91f01-109">親子階層のレベル間に親子リレーションシップがあることにより、一部の非リーフ メンバーには、子メンバーから集計したデータだけでなく、基になるデータ ソースから派生したデータが含まれる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="91f01-109">Because of parent-child relationships between levels in a parent-child hierarchy, some nonleaf members can also have data derived from underlying data sources, in addition to data aggregated from child members.</span></span>  
  
## <a name="dimension-schema"></a><span data-ttu-id="91f01-110">ディメンション スキーマ</span><span class="sxs-lookup"><span data-stu-id="91f01-110">Dimension Schema</span></span>  
 <span data-ttu-id="91f01-111">親子階層のディメンション スキーマは、ディメンション メイン テーブルに存在する自己参照型リレーションシップに依存します。</span><span class="sxs-lookup"><span data-stu-id="91f01-111">The dimension schema of a parent-child hierarchy depends on a self-referencing relationship present on the dimension main table.</span></span> <span data-ttu-id="91f01-112">たとえば、次の図は、 **サンプル データベースの** DimOrganization [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] ディメンション メイン テーブルを示しています。</span><span class="sxs-lookup"><span data-stu-id="91f01-112">For example, the following diagram illustrates the **DimOrganization** dimension main table in the [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] sample database.</span></span>  
  
 <span data-ttu-id="91f01-113">![DimOrganization テーブルの自己参照による結合](../dev-guide/media/dimorganization.gif "DimOrganization テーブルの自己参照による結合")</span><span class="sxs-lookup"><span data-stu-id="91f01-113">![Self-referencing join in DimOrganization table](../dev-guide/media/dimorganization.gif "Self-referencing join in DimOrganization table")</span></span>  
  
 <span data-ttu-id="91f01-114">このディメンション テーブルでは、 **ParentOrganizationKey** 列に **OrganizationKey** 主キー列との外部キー リレーションシップがあります。</span><span class="sxs-lookup"><span data-stu-id="91f01-114">In this dimension table, the **ParentOrganizationKey** column has a foreign key relationship with the **OrganizationKey** primary key column.</span></span> <span data-ttu-id="91f01-115">つまり、このテーブル内の各レコードは、親子リレーションシップによりテーブル内の別のレコードと関連している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="91f01-115">In other words, each record in this table can be related through a parent-child relationship with another record in the table.</span></span> <span data-ttu-id="91f01-116">この種の自己結合は、通常、部署内の従業員の管理構造などの組織エンティティ データを表すために使用します。</span><span class="sxs-lookup"><span data-stu-id="91f01-116">This kind of self-join is generally used to represent organization entity data, such as the management structure of employees in a department.</span></span>  
  
## <a name="hierarchies-and-levels"></a><span data-ttu-id="91f01-117">階層とレベル</span><span class="sxs-lookup"><span data-stu-id="91f01-117">Hierarchies and Levels</span></span>  
 <span data-ttu-id="91f01-118">親子リレーションシップのないディメンションは、属性をグループ化したり順序付けたりすることにより、階層を構築します。</span><span class="sxs-lookup"><span data-stu-id="91f01-118">Dimensions that do not have a parent-child relationship construct hierarchies by grouping and ordering attributes.</span></span> <span data-ttu-id="91f01-119">これらのディメンションは、階層のレベル名を属性名から取得します。</span><span class="sxs-lookup"><span data-stu-id="91f01-119">These dimensions derive the level names for their hierarchies from the attribute names.</span></span>  
  
 <span data-ttu-id="91f01-120">ただし、親子ディメンションは、ディメンション メイン テーブルに格納されているデータを調べ、テーブル内のレコード間の親子リレーションシップを評価することにより、親子階層を構築します。</span><span class="sxs-lookup"><span data-stu-id="91f01-120">However, parent-child dimensions construct parent-child hierarchies by examining the data that the dimension main table contains, and then evaluating the parent-child relationships between the records in the table.</span></span> <span data-ttu-id="91f01-121">親子階層の詳細については、「 [ユーザー階層](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91f01-121">For more information about parent-child hierarchies, see [User Hierarchies](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md).</span></span>  
  
 <span data-ttu-id="91f01-122">親子階層内のレベルの名前は、階層の作成に使用された属性からは派生しません。</span><span class="sxs-lookup"><span data-stu-id="91f01-122">Parent-child hierarchies do not derive the names for the levels in a parent-child hierarchy from the attributes that are used to create the hierarchy.</span></span> <span data-ttu-id="91f01-123">代わりに、これらのディメンションでは、名前付けテンプレートを使用して、レベル名が自動的に作成されます。これは、属性が属性階層を生成する方法を制御する親属性のレベルで指定できる文字列式です。</span><span class="sxs-lookup"><span data-stu-id="91f01-123">Instead, these dimensions create level names automatically by using a naming template-a string expression you can specify at the level of the parent attribute that controls how the attribute generates the attribute hierarchy.</span></span> <span data-ttu-id="91f01-124">親属性用の名前付けテンプレートの設定方法の詳細については、「 [属性と属性階層](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91f01-124">For more information about how to set the naming template for a parent attribute, see [Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).</span></span>  
  
## <a name="data-members"></a><span data-ttu-id="91f01-125">データ メンバー</span><span class="sxs-lookup"><span data-stu-id="91f01-125">Data Members</span></span>  
 <span data-ttu-id="91f01-126">通常、ディメンションのリーフ メンバーには基になるデータ ソースから直接派生したデータが含まれ、非リーフ メンバーには子メンバーに対して実行した集計から派生したデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="91f01-126">Typically, leaf members in a dimension contain data derived directly from underlying data sources, whereas nonleaf members contain data derived from aggregations performed on child members.</span></span>  
  
 <span data-ttu-id="91f01-127">ただし、親子階層では、一部の非リーフ メンバーに、子メンバーから集計されたデータだけでなく、基になるデータ ソースから派生したデータも含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="91f01-127">However, parent-child hierarchies might have some nonleaf members whose data is derived from underlying data sources, in addition to data aggregated from child members.</span></span> <span data-ttu-id="91f01-128">親子階層の非リーフ メンバーの場合、基になるファクト テーブル データを含む特殊なシステム生成の子メンバーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="91f01-128">For these nonleaf members in a parent-child hierarchy, special system-generated child members can be created that contain the underlying fact table data.</span></span> <span data-ttu-id="91f01-129">*データ メンバー*と呼ばれるこれらの特殊な子メンバーには、非リーフ メンバーに直接関係付けられた、非リーフ メンバーの子孫から計算される集計値に依存しない値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="91f01-129">Referred to as *data members*, these special child members contain a value that is directly associated with a nonleaf member and is independent of the summary value calculated from the descendants of the nonleaf member.</span></span> <span data-ttu-id="91f01-130">データ メンバーの詳細については、「 [親子階層の属性](parent-child-dimension-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91f01-130">For more information about data members, see [Attributes in Parent-Child Hierarchies](parent-child-dimension-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91f01-131">参照</span><span class="sxs-lookup"><span data-stu-id="91f01-131">See Also</span></span>  
 <span data-ttu-id="91f01-132">[親子階層の属性](parent-child-dimension-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="91f01-132">[Attributes in Parent-Child Hierarchies](parent-child-dimension-attributes.md) </span></span>  
 [<span data-ttu-id="91f01-133">データベース ディメンション プロパティ</span><span class="sxs-lookup"><span data-stu-id="91f01-133">Database Dimension Properties</span></span>](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties.md)  
  
  
