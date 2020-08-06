---
title: 明示的なキャップを持つ派生階層 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services], derived hierarchies with explicit caps
- explicit hierarchies, derived hierarchies with explicit caps
- derived hierarchies, derived hierarchies with explicit caps
ms.assetid: 6a82ff66-c137-4757-99bb-787d189b4295
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d2460ddf098f0547c2876dd9689f5d2bf9b461a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633181"
---
# <a name="derived-hierarchies-with-explicit-caps-master-data-services"></a><span data-ttu-id="0c994-102">明示的なキャップを持つ派生階層 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0c994-102">Derived Hierarchies with Explicit Caps (Master Data Services)</span></span>
  <span data-ttu-id="0c994-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]の、派生階層の最上位レベルとして使用される明示的階層のレベルは、明示的なキャップを持つ派生階層と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="0c994-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], when the levels from an explicit hierarchy are used as the top levels of a derived hierarchy, this is called a derived hierarchy with an explicit cap.</span></span>

 <span data-ttu-id="0c994-104">明示的階層は、派生階層の最上位のエンティティと同じエンティティに基づく必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c994-104">The explicit hierarchy must be based on the same entity as the entity at the top of the derived hierarchy.</span></span>

 <span data-ttu-id="0c994-105">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のユーザー インターフェイス (UI) で明示的階層を派生階層の最上位にドラッグして、この種類の階層を作成します。</span><span class="sxs-lookup"><span data-stu-id="0c994-105">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface (UI), you create this type of hierarchy by dragging an explicit hierarchy to the top of a derived hierarchy.</span></span>

 <span data-ttu-id="0c994-106">![mds_conc_explicit_cap_UI_structure](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-structure.gif "mds_conc_explicit_cap_UI_structure")</span><span class="sxs-lookup"><span data-stu-id="0c994-106">![mds_conc_explicit_cap_UI_structure](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-structure.gif "mds_conc_explicit_cap_UI_structure")</span></span>

## <a name="derived-hierarchy-with-explicit-cap-example"></a><span data-ttu-id="0c994-107">明示的なキャップを持つ派生階層の例</span><span class="sxs-lookup"><span data-stu-id="0c994-107">Derived Hierarchy with Explicit Cap Example</span></span>
 <span data-ttu-id="0c994-108">この例では、明示的階層のメンバーは Subcategory エンティティのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="0c994-108">In this example, the members in the explicit hierarchy are from the Subcategory entity.</span></span> <span data-ttu-id="0c994-109">派生階層の最上位レベルのメンバーも Subcategory エンティティのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="0c994-109">In the derived hierarchy, the top-level members are also from the Subcategory entity.</span></span>

 <span data-ttu-id="0c994-110">![mds_conc_explicit_cap_UI_example](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-example.gif "mds_conc_explicit_cap_UI_example")</span><span class="sxs-lookup"><span data-stu-id="0c994-110">![mds_conc_explicit_cap_UI_example](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-example.gif "mds_conc_explicit_cap_UI_example")</span></span>

 <span data-ttu-id="0c994-111">明示的階層を派生階層の最上位で使用することにより、派生階層は不規則になります。</span><span class="sxs-lookup"><span data-stu-id="0c994-111">By using the explicit hierarchy at the top of a derived hierarchy, the derived hierarchy becomes ragged.</span></span>

## <a name="rules"></a><span data-ttu-id="0c994-112">ルール</span><span class="sxs-lookup"><span data-stu-id="0c994-112">Rules</span></span>

-   <span data-ttu-id="0c994-113">明示的キャップを持つ 1 つの派生階層に設定できる明示的階層は 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="0c994-113">You cannot have more than one explicit hierarchy in a derived hierarchy with explicit cap.</span></span>

-   <span data-ttu-id="0c994-114">同じ明示的階層を複数の派生階層のキャップとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="0c994-114">You can use the same explicit hierarchy as a cap for multiple derived hierarchies.</span></span>

-   <span data-ttu-id="0c994-115">明示的なキャップを持つ派生階層に階層メンバーの権限を割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="0c994-115">You cannot assign hierarchy member permissions to derived hierarchies with explicit caps.</span></span> <span data-ttu-id="0c994-116">権限を明示的階層または派生階層に個々に割り当てた場合、権限は両方の階層に影響します。</span><span class="sxs-lookup"><span data-stu-id="0c994-116">If you assign permissions to either the explicit hierarchy or the derived hierarchy individually, the permissions affect both hierarchies.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="0c994-117">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="0c994-117">Related Tasks</span></span>

|<span data-ttu-id="0c994-118">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="0c994-118">Task Description</span></span>|<span data-ttu-id="0c994-119">トピック</span><span class="sxs-lookup"><span data-stu-id="0c994-119">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="0c994-120">派生階層を作成する。</span><span class="sxs-lookup"><span data-stu-id="0c994-120">Create a derived hierarchy.</span></span>|[<span data-ttu-id="0c994-121">派生階層を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="0c994-121">Create a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](create-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="0c994-122">明示的階層を作成する。</span><span class="sxs-lookup"><span data-stu-id="0c994-122">Create an explicit hierarchy.</span></span>|[<span data-ttu-id="0c994-123">明示的階層を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="0c994-123">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)|
|<span data-ttu-id="0c994-124">既存の派生階層を削除する。</span><span class="sxs-lookup"><span data-stu-id="0c994-124">Delete an existing derived hierarchy.</span></span>|[<span data-ttu-id="0c994-125">派生階層を削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="0c994-125">Delete a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-derived-hierarchy-master-data-services.md)|
|||

## <a name="related-content"></a><span data-ttu-id="0c994-126">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="0c994-126">Related Content</span></span>

-   [<span data-ttu-id="0c994-127">派生階層 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="0c994-127">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)

-   [<span data-ttu-id="0c994-128">明示的階層 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="0c994-128">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)


