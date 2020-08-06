---
title: 属性リレーションシップのプロパティの構成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- flexible relationships (Analysis Services)
- attributes [Analysis Services], relationships
- relationships [Analysis Services], attributes
- properties [Analysis Services], attribute relationships
- rigid relationships (Analysis Services)
ms.assetid: fce511af-66d7-42fc-bb3a-6c516f16b10e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 241fa2af16377fd2cacf657ec6f99c5ca4bd0c53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632170"
---
# <a name="configure-attribute-relationship-properties"></a><span data-ttu-id="dc91f-102">属性リレーションシップのプロパティの構成</span><span class="sxs-lookup"><span data-stu-id="dc91f-102">Configure Attribute Relationship Properties</span></span>
  <span data-ttu-id="dc91f-103">次の表で、属性リレーションシップのプロパティの一覧およびその説明を示します。</span><span class="sxs-lookup"><span data-stu-id="dc91f-103">The following table lists and describes the properties of an attribute relationship.</span></span>  
  
|<span data-ttu-id="dc91f-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="dc91f-104">Property</span></span>|<span data-ttu-id="dc91f-105">説明</span><span class="sxs-lookup"><span data-stu-id="dc91f-105">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="dc91f-106">属性</span><span class="sxs-lookup"><span data-stu-id="dc91f-106">Attribute</span></span>|<span data-ttu-id="dc91f-107">属性の名前を示します。</span><span class="sxs-lookup"><span data-stu-id="dc91f-107">Contains the name of the attribute.</span></span>|  
|<span data-ttu-id="dc91f-108">カーディナリティ</span><span class="sxs-lookup"><span data-stu-id="dc91f-108">Cardinality</span></span>|<span data-ttu-id="dc91f-109">リレーションシップのカーディナリティを示します。</span><span class="sxs-lookup"><span data-stu-id="dc91f-109">Indicates the cardinality of the relationship.</span></span> <span data-ttu-id="dc91f-110">値は、多対一リレーションシップの場合は Many、一対一リレーションシップの場合は One です。</span><span class="sxs-lookup"><span data-stu-id="dc91f-110">Values are Many, for a many to one relationship, or One, for a one to one relationship.</span></span> <span data-ttu-id="dc91f-111">既定値は Many です。</span><span class="sxs-lookup"><span data-stu-id="dc91f-111">Default value is Many.</span></span> <span data-ttu-id="dc91f-112">では [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、カーディナリティプロパティは効果がありません。その使用は将来の実装のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="dc91f-112">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the cardinality property has no effect - its use is reserved for a future implementation.</span></span>|  
|<span data-ttu-id="dc91f-113">名前</span><span class="sxs-lookup"><span data-stu-id="dc91f-113">Name</span></span>|<span data-ttu-id="dc91f-114">属性のよく似た名前を示します。</span><span class="sxs-lookup"><span data-stu-id="dc91f-114">Contains the friendly name of the attribute.</span></span>|  
|<span data-ttu-id="dc91f-115">RelationshipType</span><span class="sxs-lookup"><span data-stu-id="dc91f-115">RelationshipType</span></span>|<span data-ttu-id="dc91f-116">メンバーのリレーションシップが時間を経て変化するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="dc91f-116">Indicates whether member relationships change over time.</span></span> <span data-ttu-id="dc91f-117">値が Rigid の場合、メンバー間のリレーションシップが時間を経て変化しないことを意味し、値が Flexible の場合は、メンバー間のリレーションシップが時間を経て変化することを意味します。</span><span class="sxs-lookup"><span data-stu-id="dc91f-117">Values are Rigid, which means that relationships between members do not change over time, or Flexible, which means that relationships between members change over time.</span></span> <span data-ttu-id="dc91f-118">既定では Flexible です。</span><span class="sxs-lookup"><span data-stu-id="dc91f-118">Default is Flexible.</span></span> <span data-ttu-id="dc91f-119">リレーションシップを Flexible に定義すると、集計は削除され、増分更新の一部として再計算されます (新しいメンバーだけが追加された場合、集計は削除されません)。</span><span class="sxs-lookup"><span data-stu-id="dc91f-119">If you define a relationship as flexible, aggregations are dropped and recomputed as part of an incremental update (they will not be dropped if only new members are added).</span></span> <span data-ttu-id="dc91f-120">リレーションシップを Rigid に定義すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではディメンションが増分更新されたときの集計が維持されます。</span><span class="sxs-lookup"><span data-stu-id="dc91f-120">If you define a relationship as rigid, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] retains aggregations when the dimension is incrementally updated.</span></span> <span data-ttu-id="dc91f-121">Rigid に定義されているリレーションシップが実際に変化した場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では増分処理時にエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="dc91f-121">If a relationship that is defined as rigid actually changes, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] generates an error during incremental processing.</span></span> <span data-ttu-id="dc91f-122">適切なリレーションシップとリレーションシップのプロパティを指定すると、クエリ パフォーマンスと処理パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="dc91f-122">Specifying the appropriate relationships and relationship properties increases query and processing performance.</span></span>|  
|<span data-ttu-id="dc91f-123">Visible</span><span class="sxs-lookup"><span data-stu-id="dc91f-123">Visible</span></span>|<span data-ttu-id="dc91f-124">属性リレーションシップの表示を決めます。</span><span class="sxs-lookup"><span data-stu-id="dc91f-124">Determines the visibility of the attribute relationship.</span></span> <span data-ttu-id="dc91f-125">値は True または False です。</span><span class="sxs-lookup"><span data-stu-id="dc91f-125">Values are True or False.</span></span> <span data-ttu-id="dc91f-126">既定値は True です。</span><span class="sxs-lookup"><span data-stu-id="dc91f-126">Default is True.</span></span>|  
  
  
