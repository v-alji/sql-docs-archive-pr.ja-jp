---
title: 再帰型階層 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- recursive hierarchies [Master Data Services]
- hierarchies [Master Data Services], recursive hierarchies
ms.assetid: 9408c6ea-d9c4-4a0b-8a1b-1457fb6944af
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3c149d500ce1499ad36247d5e32bb6f2d55b4250
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644500"
---
# <a name="recursive-hierarchies-master-data-services"></a><span data-ttu-id="6a925-102">再帰型階層 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="6a925-102">Recursive Hierarchies (Master Data Services)</span></span>
  <span data-ttu-id="6a925-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]の再帰型階層は、再帰リレーションシップを含む派生階層です。</span><span class="sxs-lookup"><span data-stu-id="6a925-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a recursive hierarchy is a derived hierarchy that includes a recursive relationship.</span></span> <span data-ttu-id="6a925-104">再帰リレーションシップは、エンティティ自体に基づくドメインベースの属性がエンティティにある場合に存在します。</span><span class="sxs-lookup"><span data-stu-id="6a925-104">A recursive relationship exists when an entity has a domain-based attribute based on the entity itself.</span></span>

## <a name="recursive-hierarchy-example"></a><span data-ttu-id="6a925-105">再帰型階層の例</span><span class="sxs-lookup"><span data-stu-id="6a925-105">Recursive Hierarchy Example</span></span>
 <span data-ttu-id="6a925-106">再帰型階層の典型的な例は、組織構造です。</span><span class="sxs-lookup"><span data-stu-id="6a925-106">A typical recursive hierarchy example is an organizational structure.</span></span> <span data-ttu-id="6a925-107">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、Manager というドメイン ベースの属性を持つ Employee エンティティを作成します。</span><span class="sxs-lookup"><span data-stu-id="6a925-107">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you would do this by creating an Employee entity with a domain-based attribute called Manager.</span></span> <span data-ttu-id="6a925-108">Manager 属性は、従業員 (employee) のリストから設定されます。</span><span class="sxs-lookup"><span data-stu-id="6a925-108">The Manager attribute is populated from the list of employees.</span></span> <span data-ttu-id="6a925-109">このサンプル組織では、すべての従業員がマネージャーである可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6a925-109">In this sample organization, all employees can be managers.</span></span>

 <span data-ttu-id="6a925-110">![mds_conc_recursive_table_w_data](../../2014/master-data-services/media/mds-conc-recursive-table-w-data.gif "mds_conc_recursive_table_w_data")</span><span class="sxs-lookup"><span data-stu-id="6a925-110">![mds_conc_recursive_table_w_data](../../2014/master-data-services/media/mds-conc-recursive-table-w-data.gif "mds_conc_recursive_table_w_data")</span></span>

 <span data-ttu-id="6a925-111">Employee エンティティおよびドメイン ベースの Manager 属性の間のリレーションシップを強調表示する派生階層を作成できます。</span><span class="sxs-lookup"><span data-stu-id="6a925-111">You can create a derived hierarchy that highlights the relationship between the Employee entity and the Manager domain-based attribute.</span></span>

 <span data-ttu-id="6a925-112">![mds_conc_recursive_UI_structure](../../2014/master-data-services/media/mds-conc-recursive-ui-structure.gif "mds_conc_recursive_UI_structure")</span><span class="sxs-lookup"><span data-stu-id="6a925-112">![mds_conc_recursive_UI_structure](../../2014/master-data-services/media/mds-conc-recursive-ui-structure.gif "mds_conc_recursive_UI_structure")</span></span>

 <span data-ttu-id="6a925-113">階層内の各メンバーを一度だけ含めるために、Null リレーションシップをアンカーできます。</span><span class="sxs-lookup"><span data-stu-id="6a925-113">To include each member in the hierarchy only once, you can anchor null relationships.</span></span> <span data-ttu-id="6a925-114">その場合、空白のドメイン ベースの属性値を持つメンバーが階層の最上位レベルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a925-114">When you do, members with blank domain-based attribute values are displayed at the top level of the hierarchy.</span></span>

 <span data-ttu-id="6a925-115">![mds_conc_recursive_UI_example_anchored](../../2014/master-data-services/media/mds-conc-recursive-ui-example-anchored.gif "mds_conc_recursive_UI_example_anchored")</span><span class="sxs-lookup"><span data-stu-id="6a925-115">![mds_conc_recursive_UI_example_anchored](../../2014/master-data-services/media/mds-conc-recursive-ui-example-anchored.gif "mds_conc_recursive_UI_example_anchored")</span></span>

 <span data-ttu-id="6a925-116">Null リレーションシップをアンカーしない場合、メンバーは複数回含まれます。</span><span class="sxs-lookup"><span data-stu-id="6a925-116">If you do not anchor null relationships, members are included multiple times.</span></span> <span data-ttu-id="6a925-117">すべてのメンバーは最上位レベルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a925-117">All members are displayed at the top level.</span></span> <span data-ttu-id="6a925-118">すべてのメンバーは、それらが属性であるメンバーの下にも表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a925-118">They are also displayed under members of which they are attributes.</span></span>

 <span data-ttu-id="6a925-119">![mds_conc_recursive_UI_example_nonanchored](../../2014/master-data-services/media/mds-conc-recursive-ui-example-nonanchored.gif "mds_conc_recursive_UI_example_nonanchored")</span><span class="sxs-lookup"><span data-stu-id="6a925-119">![mds_conc_recursive_UI_example_nonanchored](../../2014/master-data-services/media/mds-conc-recursive-ui-example-nonanchored.gif "mds_conc_recursive_UI_example_nonanchored")</span></span>

 <span data-ttu-id="6a925-120">この例では、Marcia は最上位レベルにあります。</span><span class="sxs-lookup"><span data-stu-id="6a925-120">In this example, Marcia is at the top level.</span></span> <span data-ttu-id="6a925-121">Marcia はその他の Employee メンバーのドメイン ベースの属性値として使用されていないので、Marcia はいずれの従業員のマネージャーでもありません。</span><span class="sxs-lookup"><span data-stu-id="6a925-121">She is not the manager of any employees because she is not used as a domain-based attribute value for any other Employee members.</span></span> <span data-ttu-id="6a925-122">対照的に、Marcia には Manager 属性値として Robert が設定されているので、Robert の下にレベルがあります。</span><span class="sxs-lookup"><span data-stu-id="6a925-122">Robert, in contrast, has a level beneath him because Marcia has Robert as her Manager attribute value.</span></span>

## <a name="rules"></a><span data-ttu-id="6a925-123">ルール</span><span class="sxs-lookup"><span data-stu-id="6a925-123">Rules</span></span>

-   <span data-ttu-id="6a925-124">1 つの派生階層に複数の再帰リレーションシップを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="6a925-124">A derived hierarchy cannot contain more than one recursive relationship.</span></span> <span data-ttu-id="6a925-125">ただし、他の派生リレーションシップを含めることはできます (たとえば、"マネージャーと従業員" という再帰リレーションシップに、"国とマネージャー" および "従業員と店舗" というリレーションシップを含めることもできます)。</span><span class="sxs-lookup"><span data-stu-id="6a925-125">It can, however, have other derived relationships (for example, a derived hierarchy that contains a recursive Manager to Employee relationship can also have Country to Manager and Employee to Store relationships).</span></span>

-   <span data-ttu-id="6a925-126">( **[階層メンバー]** タブで) メンバー権限を再帰的階層のメンバーに割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="6a925-126">You cannot assign member permissions (on the **Hierarchy Members** tab) to members in a recursive hierarchy.</span></span>

-   <span data-ttu-id="6a925-127">再帰的階層は循環リレーションシップを含むことはできません。</span><span class="sxs-lookup"><span data-stu-id="6a925-127">Recursive hierarchies cannot include circular relationships.</span></span> <span data-ttu-id="6a925-128">たとえば、Sandeep が Katherine のマネージャーである場合、Katherine を Sandeep のマネージャーにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="6a925-128">For example, Katherine cannot be Sandeep's manager if Sandeep is her manager.</span></span> <span data-ttu-id="6a925-129">また、Katherine は Katherine 自身のマネージャーになることもできません。</span><span class="sxs-lookup"><span data-stu-id="6a925-129">Also, Katherine cannot manage herself.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="6a925-130">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="6a925-130">Related Tasks</span></span>

|<span data-ttu-id="6a925-131">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="6a925-131">Task Description</span></span>|<span data-ttu-id="6a925-132">トピック</span><span class="sxs-lookup"><span data-stu-id="6a925-132">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="6a925-133">派生階層を作成する。</span><span class="sxs-lookup"><span data-stu-id="6a925-133">Create a derived hierarchy.</span></span>|[<span data-ttu-id="6a925-134">派生階層を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="6a925-134">Create a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](create-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="6a925-135">既存の派生階層の名前を変更する。</span><span class="sxs-lookup"><span data-stu-id="6a925-135">Change the name of an existing derived hierarchy.</span></span>|[<span data-ttu-id="6a925-136">派生階層名を変更する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="6a925-136">Change a Derived Hierarchy Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-derived-hierarchy-name-master-data-services.md)|
|<span data-ttu-id="6a925-137">既存の派生階層を削除する。</span><span class="sxs-lookup"><span data-stu-id="6a925-137">Delete an existing derived hierarchy.</span></span>|[<span data-ttu-id="6a925-138">派生階層を削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="6a925-138">Delete a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-derived-hierarchy-master-data-services.md)|

## <a name="related-content"></a><span data-ttu-id="6a925-139">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="6a925-139">Related Content</span></span>

-   [<span data-ttu-id="6a925-140">ドメインベースの属性 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="6a925-140">Domain-Based Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/domain-based-attributes-master-data-services.md)

-   [<span data-ttu-id="6a925-141">派生階層 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="6a925-141">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)


