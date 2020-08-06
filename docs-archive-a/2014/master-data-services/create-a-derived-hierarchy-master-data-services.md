---
title: 派生階層を作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies, creating
- creating derived hierarchies [Master Data Services]
ms.assetid: fec653c4-11cc-46a2-8dd8-b605341ebb40
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 20469ad30222e43a3104503cc32187c2e6512743
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716393"
---
# <a name="create-a-derived-hierarchy-master-data-services"></a><span data-ttu-id="2cc41-102">派生階層を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="2cc41-102">Create a Derived Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="2cc41-103">正しいレベルにメンバーが確実に存在するレベル ベースの階層が必要な場合、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、派生階層を作成します。</span><span class="sxs-lookup"><span data-stu-id="2cc41-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a derived hierarchy when you want a level-based hierarchy that ensures that members exist at the correct level.</span></span> <span data-ttu-id="2cc41-104">派生階層は、モデル内に存在するドメイン ベースの属性のリレーションシップに基づきます。</span><span class="sxs-lookup"><span data-stu-id="2cc41-104">Derived hierarchies are based on the domain-based attribute relationships that exist in a model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2cc41-105">ドメイン ベースの属性値がメンバーに対して存在しない場合、メンバーは派生階層に含まれません。</span><span class="sxs-lookup"><span data-stu-id="2cc41-105">If a domain-based attribute value doesn't exist for a member, the member is not included in the derived hierarchy.</span></span> <span data-ttu-id="2cc41-106">すべてのメンバーのドメイン ベースの属性値を要求するには、「[属性値を要求する (マスター データ サービス)](require-attribute-values-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cc41-106">See [Require Attribute Values &#40;Master Data Services&#41;](require-attribute-values-master-data-services.md) to require a domain-based attribute value for all members.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2cc41-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="2cc41-107">Prerequisites</span></span>  
 <span data-ttu-id="2cc41-108">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="2cc41-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="2cc41-109">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="2cc41-109">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="2cc41-110">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cc41-110">You must be a model administrator.</span></span> <span data-ttu-id="2cc41-111">詳細については、「[管理者 &#40;マスターデータサービス&#41;](../../2014/master-data-services/administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cc41-111">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-a-derived-hierarchy"></a><span data-ttu-id="2cc41-112">派生階層を作成するには</span><span class="sxs-lookup"><span data-stu-id="2cc41-112">To create a derived hierarchy</span></span>  
  
1.  <span data-ttu-id="2cc41-113">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cc41-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="2cc41-114">[**モデルビュー** ] ページのメニューバーから [**管理**] をポイントし、[**派生階層**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cc41-114">On the **Model View** page, from the menu bar, point to **Manage** and click **Derived Hierarchies**.</span></span>  
  
3.  <span data-ttu-id="2cc41-115">**[派生階層のメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="2cc41-115">On the **Derived Hierarchy Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="2cc41-116">[**派生階層の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cc41-116">Click **Add derived hierarchy**.</span></span>  
  
5.  <span data-ttu-id="2cc41-117">**[派生階層の追加]** ページの **[派生階層名]** ボックスに階層の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="2cc41-117">On the **Add Derived Hierarchy** page, in the **Derived hierarchy name** box, type a name for the hierarchy.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="2cc41-118">名前は、たとえば **"カテゴリに含まれるサブカテゴリに含まれる製品"** のように、階層のレベルがわかる形式にします。</span><span class="sxs-lookup"><span data-stu-id="2cc41-118">Use a name that describes the levels in the hierarchy, for example **Product to Subcategory to Category**.</span></span>  
  
6.  <span data-ttu-id="2cc41-119">**[派生階層の保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cc41-119">Click **Save derived hierarchy**.</span></span>  
  
7.  <span data-ttu-id="2cc41-120">[**派生階層の編集**] ページの [**使用できるエンティティと階層**] ペインで、エンティティまたは階層をクリックし、[**現在のレベル**] ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="2cc41-120">On the **Edit Derived Hierarchy** page, in the **Available Entities and Hierarchies** pane, click an entity or hierarchy and drag it to the **Current Levels** pane.</span></span>  
  
8.  <span data-ttu-id="2cc41-121">その他のエンティティまたは階層をドラッグして、階層を完成させます。</span><span class="sxs-lookup"><span data-stu-id="2cc41-121">Continue dragging entities or hierarchies until your hierarchy is complete.</span></span>  
  
9. <span data-ttu-id="2cc41-122">**[戻る]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cc41-122">Click **Back**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cc41-123">参照</span><span class="sxs-lookup"><span data-stu-id="2cc41-123">See Also</span></span>  
 <span data-ttu-id="2cc41-124">[派生階層 &#40;マスターデータサービス&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="2cc41-124">[Derived Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md) </span></span>  
 <span data-ttu-id="2cc41-125">[明示的なキャップを持つ派生階層 &#40;マスターデータサービス&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="2cc41-125">[Derived Hierarchies with Explicit Caps &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md) </span></span>  
 [<span data-ttu-id="2cc41-126">ドメインベースの属性 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="2cc41-126">Domain-Based Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/domain-based-attributes-master-data-services.md)  
  
  
