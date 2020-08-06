---
title: 属性リレーションシップの定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Analysis Services], relationships
- relationships [Analysis Services], attributes
ms.assetid: 9184d344-e96d-4025-ad6f-3f75129746df
author: minewiskan
ms.author: owend
ms.openlocfilehash: a694c68a55de2533c4ce7791d3be865008b6321f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632162"
---
# <a name="define-attribute-relationships"></a><span data-ttu-id="9e446-102">属性リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="9e446-102">Define Attribute Relationships</span></span>
  <span data-ttu-id="9e446-103">で [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、属性はディメンションの基本的な構成要素です。</span><span class="sxs-lookup"><span data-stu-id="9e446-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], attributes are the fundamental building block of a dimension.</span></span> <span data-ttu-id="9e446-104">ディメンションには、属性リレーションシップに基づいて構成される一連の属性が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9e446-104">A dimension contains a set of attributes that are organized based on attribute relationships.</span></span>  
  
 <span data-ttu-id="9e446-105">ディメンションに含まれるテーブルごとに、テーブルのキー属性をそのテーブルの別の属性に関連付ける属性リレーションシップがあります。</span><span class="sxs-lookup"><span data-stu-id="9e446-105">For each table included in a dimension, there is an attribute relationship that relates the table's key attribute to other attributes from that table.</span></span> <span data-ttu-id="9e446-106">このリレーションシップは、ディメンションの作成時に作成します。</span><span class="sxs-lookup"><span data-stu-id="9e446-106">You create this relationship when you create the dimension.</span></span>  
  
 <span data-ttu-id="9e446-107">属性リレーションシップには、次の利点があります。</span><span class="sxs-lookup"><span data-stu-id="9e446-107">An attribute relationship provides the following advantages:</span></span>  
  
-   <span data-ttu-id="9e446-108">ディメンション処理に必要なメモリの量が減少します。</span><span class="sxs-lookup"><span data-stu-id="9e446-108">Reduces the amount of memory needed for dimension processing.</span></span> <span data-ttu-id="9e446-109">これにより、ディメンション、パーティション、およびクエリの処理速度が上がります。</span><span class="sxs-lookup"><span data-stu-id="9e446-109">This speeds up dimension, partition, and query processing.</span></span>  
  
-   <span data-ttu-id="9e446-110">ストレージへのアクセスが高速になり、実行プランがより適切に最適化されるため、クエリ パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="9e446-110">Increases query performance because storage access is faster and execution plans are better optimized.</span></span>  
  
-   <span data-ttu-id="9e446-111">ユーザー定義階層がリレーションシップのパスに沿って定義されている場合、集計デザイン アルゴリズムによってより効果的な集計が選択されます。</span><span class="sxs-lookup"><span data-stu-id="9e446-111">Results in the selection of more effective aggregates by the aggregation design algorithms, provided that user-defined hierarchies have been defined along the relationship paths.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9e446-112">属性リレーションシップの定義と構成の重要性および影響の詳細については、「 [SQL Server 2005 Analysis Services パフォーマンスガイド](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide)」の「クエリパフォーマンスの向上」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e446-112">For more information about the importance and implications of defining and configuring attribute relationships, see the section, "Enhancing query performance," in the [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).</span></span>  
  
## <a name="attribute-relationship-considerations"></a><span data-ttu-id="9e446-113">属性リレーションシップに関する注意点</span><span class="sxs-lookup"><span data-stu-id="9e446-113">Attribute Relationship Considerations</span></span>  
 <span data-ttu-id="9e446-114">基になるデータで属性リレーションシップがサポートされる場合、属性間で一意の属性リレーションシップを定義することも必要です。</span><span class="sxs-lookup"><span data-stu-id="9e446-114">When the underlying data supports it, you should also define unique attribute relationships between attributes.</span></span> <span data-ttu-id="9e446-115">一意の属性リレーションシップを定義するには、ディメンション デザイナーの **[属性リレーションシップ]** タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="9e446-115">To define unique attribute relationships, use the **Attribute Relationships** tab of Dimension Designer.</span></span>  
  
 <span data-ttu-id="9e446-116">基になるリレーションシップがある属性には、その関連属性を基準とした一意なキーが必要です。</span><span class="sxs-lookup"><span data-stu-id="9e446-116">Any attribute that has an outgoing relationship must have a unique key relative to its related attribute.</span></span> <span data-ttu-id="9e446-117">つまり、基になる属性のメンバーによって、関連属性のメンバーが 1 つだけ識別される必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e446-117">In other words, a member in a source attribute must identify one and only one member in a related attribute.</span></span> <span data-ttu-id="9e446-118">たとえば、市区町村 -> 都道府県のリレーションシップを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="9e446-118">For example, consider the relationship, City -> State.</span></span> <span data-ttu-id="9e446-119">このリレーションシップでは、基になる属性が市区町村、関連属性が都道府県です。</span><span class="sxs-lookup"><span data-stu-id="9e446-119">In this relationship, the source attribute is City and the related attribute is State.</span></span> <span data-ttu-id="9e446-120">Source 属性は "many" 側で、関連側は多対一リレーションシップの "一" 側です。</span><span class="sxs-lookup"><span data-stu-id="9e446-120">The source attribute is the "many" side and the related side is the "one" side of the many-to-one relationship.</span></span> <span data-ttu-id="9e446-121">基になる属性のキーは、市区町村 + 都道府県です。</span><span class="sxs-lookup"><span data-stu-id="9e446-121">The key for the source attribute would be City + State.</span></span> <span data-ttu-id="9e446-122">詳細については、「 [属性リレーションシップの作成、変更、または削除](attribute-relationships-create-modify-or-delete-relationship.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e446-122">For more information, see [Create, Modify, or Delete an Attribute Relationship](attribute-relationships-create-modify-or-delete-relationship.md).</span></span>  
  
 <span data-ttu-id="9e446-123">属性リレーションシップのプロパティの詳細については、「 [属性リレーションシップのプロパティの構成](attribute-relationships-configure-attribute-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e446-123">For more information about properties of an attribute relationship, see [Configure Attribute Relationship Properties](attribute-relationships-configure-attribute-properties.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e446-124">属性リレーションシップを正しく定義しないと、クエリ結果が無効になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9e446-124">Defining attribute relationships incorrectly can cause invalid query results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e446-125">参照</span><span class="sxs-lookup"><span data-stu-id="9e446-125">See Also</span></span>  
 <span data-ttu-id="9e446-126">[のディメンション デザイナーでは、[ディメンション構造] ビューの](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)</span><span class="sxs-lookup"><span data-stu-id="9e446-126">[Attribute Relationships](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)</span></span>  
  
  
