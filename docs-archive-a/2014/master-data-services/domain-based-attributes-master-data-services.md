---
title: ドメインベースの属性 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- domain-based attributes [Master Data Services], about domain-based attributes
- domain-based attributes [Master Data Services]
- attributes [Master Data Services], domain-based attributes
ms.assetid: df6f33ff-97f6-466c-af74-9780b2247473
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9182974923848d49ed3e9ecfb58a14949784a2c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646178"
---
# <a name="domain-based-attributes-master-data-services"></a><span data-ttu-id="a8a39-102">ドメインベースの属性 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="a8a39-102">Domain-Based Attributes (Master Data Services)</span></span>
  <span data-ttu-id="a8a39-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でのドメイン ベースの属性とは、別のエンティティからのメンバーによって値が設定される属性です。</span><span class="sxs-lookup"><span data-stu-id="a8a39-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a domain-based attribute is an attribute with values that are populated by members from another entity.</span></span> <span data-ttu-id="a8a39-104">ドメイン ベースの属性によって、ユーザーが無効な属性値を入力することを防止できることから、ドメイン ベースの属性は制約リストと考えることもできます。</span><span class="sxs-lookup"><span data-stu-id="a8a39-104">You can think of a domain-based attribute as a constrained list; domain-based attributes prevent users from entering attribute values that are not valid.</span></span> <span data-ttu-id="a8a39-105">属性値を選択するには、ユーザーは一覧から選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8a39-105">To select an attribute value, the user must pick from a list.</span></span>

## <a name="domain-based-attribute-example"></a><span data-ttu-id="a8a39-106">ドメイン ベースの属性の例</span><span class="sxs-lookup"><span data-stu-id="a8a39-106">Domain-Based Attribute Example</span></span>
 <span data-ttu-id="a8a39-107">次の図では、Product エンティティに Subcategory というドメイン ベースの属性があります。</span><span class="sxs-lookup"><span data-stu-id="a8a39-107">In the following image, the Product entity has a domain-based attribute called Subcategory.</span></span> <span data-ttu-id="a8a39-108">Subcategory 属性は Subcategory エンティティの値によって設定されます。</span><span class="sxs-lookup"><span data-stu-id="a8a39-108">The Subcategory attribute is populated by values from the Subcategory entity.</span></span>

 <span data-ttu-id="a8a39-109">Subcategory エンティティには Category というドメイン ベースの属性があります。</span><span class="sxs-lookup"><span data-stu-id="a8a39-109">The Subcategory entity has a domain-based attribute called Category.</span></span> <span data-ttu-id="a8a39-110">Category 属性は Category エンティティの値によって設定されます。</span><span class="sxs-lookup"><span data-stu-id="a8a39-110">The Category attribute is populated by values from the Category entity.</span></span>

 <span data-ttu-id="a8a39-111">![エンティティ内のドメイン ベースの属性](../../2014/master-data-services/media/mds-conc-domain-based-attribute-conceptual.gif "エンティティ内のドメイン ベースの属性")</span><span class="sxs-lookup"><span data-stu-id="a8a39-111">![Domain-Based Attributes in an Entity](../../2014/master-data-services/media/mds-conc-domain-based-attribute-conceptual.gif "Domain-Based Attributes in an Entity")</span></span>

## <a name="use-same-entity-for-multiple-domain-based-attributes"></a><span data-ttu-id="a8a39-112">複数のドメイン ベースの属性に同じエンティティを使用する</span><span class="sxs-lookup"><span data-stu-id="a8a39-112">Use Same Entity for Multiple Domain-Based Attributes</span></span>
 <span data-ttu-id="a8a39-113">複数のエンティティのドメイン ベースの属性として同じエンティティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a8a39-113">You can use the same entity as a domain-based attribute of multiple entities.</span></span> <span data-ttu-id="a8a39-114">たとえば、Yes、No、および Maybe というメンバーを持つ YesNoIndicator という名前のエンティティを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a8a39-114">For example, you can create an entity called YesNoIndicator with the members: Yes, No, and Maybe.</span></span> <span data-ttu-id="a8a39-115">InStock というドメイン ベースの属性を作成して、YesNoIndicator エンティティをソースとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="a8a39-115">You can create a domain-based attribute named InStock and use the YesNoIndicator entity as the source.</span></span> <span data-ttu-id="a8a39-116">また、Approved という別のドメイン ベースの属性を作成し、YesNoIndicator エンティティをソースとして使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a8a39-116">You can also create another domain-based attribute named Approved and use the YesNoIndicator entity as a source.</span></span> <span data-ttu-id="a8a39-117">YesNoIndicator エンティティのメンバーのリストからユーザーによる選択を行う場合は、エンティティをドメイン ベースの属性として使用できます。</span><span class="sxs-lookup"><span data-stu-id="a8a39-117">Any time you want users to choose from a list of the YesNoIndicator entity's members, you can use the entity as a domain-based attribute.</span></span>

## <a name="domain-based-attributes-form-derived-hierarchies"></a><span data-ttu-id="a8a39-118">ドメイン ベースの属性による派生階層の形成</span><span class="sxs-lookup"><span data-stu-id="a8a39-118">Domain-Based Attributes Form Derived Hierarchies</span></span>
 <span data-ttu-id="a8a39-119">ドメイン ベースの属性のリレーションシップは、派生階層の基盤となります。</span><span class="sxs-lookup"><span data-stu-id="a8a39-119">Domain-based attribute relationships are the basis for derived hierarchies.</span></span> <span data-ttu-id="a8a39-120">詳細については、「 [派生階層 (マスター データ サービス)](derived-hierarchies-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8a39-120">For more information, see [Derived Hierarchies &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md).</span></span>

## <a name="related-tasks"></a><span data-ttu-id="a8a39-121">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="a8a39-121">Related Tasks</span></span>

|<span data-ttu-id="a8a39-122">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="a8a39-122">Task Description</span></span>|<span data-ttu-id="a8a39-123">トピック</span><span class="sxs-lookup"><span data-stu-id="a8a39-123">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="a8a39-124">既存のエンティティを元にして新しいドメインベースの属性を作成する。</span><span class="sxs-lookup"><span data-stu-id="a8a39-124">Create a new domain-based attribute that is sourced from an existing entity.</span></span>|[<span data-ttu-id="a8a39-125">ドメイン ベースの属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="a8a39-125">Create a Domain-Based Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)|
|<span data-ttu-id="a8a39-126">新規エンティティを作成する。</span><span class="sxs-lookup"><span data-stu-id="a8a39-126">Create a new entity.</span></span>|[<span data-ttu-id="a8a39-127">エンティティを作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="a8a39-127">Create an Entity &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-entity-master-data-services.md)|

## <a name="related-content"></a><span data-ttu-id="a8a39-128">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="a8a39-128">Related Content</span></span>

-   [<span data-ttu-id="a8a39-129">派生階層 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="a8a39-129">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](derived-hierarchies-master-data-services.md)

-   [<span data-ttu-id="a8a39-130">属性 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="a8a39-130">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)

-   [<span data-ttu-id="a8a39-131">エンティティ (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="a8a39-131">Entities &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/entities-master-data-services.md)


