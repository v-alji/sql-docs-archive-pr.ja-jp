---
title: 変更の追跡グループに属性を追加する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- change tracking groups [Master Data Services]
- attributes [Master Data Services], change tracking groups
- change tracking groups [Master Data Services], adding attributes
ms.assetid: e153eb5f-70ca-4c6f-89d8-1f937ed3917d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c8a13dad3ca886668c96c1886f8cd238d9adad9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645159"
---
# <a name="add-attributes-to-a-change-tracking-group-master-data-services"></a><span data-ttu-id="d22d3-102">変更の追跡グループに属性を追加する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="d22d3-102">Add Attributes to a Change Tracking Group (Master Data Services)</span></span>
  <span data-ttu-id="d22d3-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で属性の値に対する変更を追跡する場合、変更の追跡グループに属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="d22d3-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], add attributes to a change tracking group when you want to track changes to the attribute's values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d22d3-104">変更の追跡グループに属性を追加した後に属性の値が変更されると、属性は [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースで変更済みとしてフラグが付けられます。</span><span class="sxs-lookup"><span data-stu-id="d22d3-104">After you add an attribute to a change tracking group, when values for the attribute change, the attribute is flagged as changed in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="d22d3-105">変更に基づいてアクションを実行するビジネス ルールを作成します。</span><span class="sxs-lookup"><span data-stu-id="d22d3-105">Create a business rule to take action based on the change.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d22d3-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="d22d3-106">Prerequisites</span></span>  
 <span data-ttu-id="d22d3-107">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="d22d3-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="d22d3-108">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="d22d3-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="d22d3-109">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d22d3-109">You must be a model administrator.</span></span> <span data-ttu-id="d22d3-110">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d22d3-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="d22d3-111">変更の追跡グループに追加する属性が存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d22d3-111">Attributes must exist to add to the change tracking group.</span></span> <span data-ttu-id="d22d3-112">詳細については、「 [テキスト属性を作成する (マスター データ サービス)](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d22d3-112">For more information, see [Create a Text Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md).</span></span>  
  
### <a name="to-add-attributes-to-a-change-tracking-group"></a><span data-ttu-id="d22d3-113">属性を変更の追跡グループに追加するには</span><span class="sxs-lookup"><span data-stu-id="d22d3-113">To add attributes to a change tracking group</span></span>  
  
1.  <span data-ttu-id="d22d3-114">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22d3-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="d22d3-115">[**モデルエクスプローラー** ] ページのメニューバーから [**管理**] をポイントし、[**エンティティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22d3-115">On the **Model Explorer** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="d22d3-116">**[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="d22d3-116">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="d22d3-117">属性値を追跡するエンティティの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="d22d3-117">Select the row for the entity that you want to track attribute values for.</span></span>  
  
5.  <span data-ttu-id="d22d3-118">**[選択したエンティティの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22d3-118">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="d22d3-119">**[エンティティの編集]** ページで、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d22d3-119">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="d22d3-120">リーフメンバーの属性の場合は、[**リーフ属性**] ペインで属性を選択し、[**リーフ属性の編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22d3-120">If the attribute is for leaf members, in the **Leaf attributes** pane, select the attribute and click **Edit leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="d22d3-121">統合メンバーの属性の場合は、[**統合属性**] ペインで属性を選択し、[**統合属性の編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22d3-121">If the attribute is for consolidated members, in the **Consolidated attributes** pane, select the attribute and click **Edit consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="d22d3-122">コレクションの属性の場合は、[**コレクション属性**] ペインで属性を選択し、[**コレクション属性の編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22d3-122">If the attribute is for collections, in the **Collection attributes** pane, select the attribute and click **Edit collection attribute**.</span></span>  
  
7.  <span data-ttu-id="d22d3-123">**[変更の追跡の有効化]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="d22d3-123">Select the **Enable change tracking** check box.</span></span>  
  
8.  <span data-ttu-id="d22d3-124">**[変更の追跡グループ]** ボックスにグループの番号を入力します。</span><span class="sxs-lookup"><span data-stu-id="d22d3-124">In the **Change tracking group** box, type a number for the group.</span></span>  
  
9. <span data-ttu-id="d22d3-125">**[属性の保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22d3-125">Click **Save attribute**.</span></span>  
  
10. <span data-ttu-id="d22d3-126">**[エンティティのメンテナンス]** ページで **[エンティティの保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22d3-126">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
11. <span data-ttu-id="d22d3-127">グループに含めるすべての属性に対して、この手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="d22d3-127">Repeat this procedure for all attributes you want to include in the group.</span></span> <span data-ttu-id="d22d3-128">グループ内の各属性に対して同じ変更の追跡グループの番号を使用します。</span><span class="sxs-lookup"><span data-stu-id="d22d3-128">Use the same change tracking group number for each attribute in the group.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d22d3-129">次の手順</span><span class="sxs-lookup"><span data-stu-id="d22d3-129">Next Steps</span></span>  
  
-   [<span data-ttu-id="d22d3-130">属性値の変更に基づいてアクションを開始する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="d22d3-130">Initiate Actions Based on Attribute Value Changes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="d22d3-131">参照</span><span class="sxs-lookup"><span data-stu-id="d22d3-131">See Also</span></span>  
 <span data-ttu-id="d22d3-132">[テキスト属性 &#40;マスターデータサービスを作成し&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d22d3-132">[Create a Text Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="d22d3-133">ドメイン ベースの属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="d22d3-133">Create a Domain-Based Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
  
