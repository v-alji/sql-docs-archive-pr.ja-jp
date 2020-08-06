---
title: 属性グループを作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services], creating
- creating attribute groups [Master Data Services]
ms.assetid: 798c325e-e8d8-412a-b02e-118f2741d1c7
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fbd95869082ea0a73f3abea092163c4705e4da5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736469"
---
# <a name="create-an-attribute-group-master-data-services"></a><span data-ttu-id="eed9c-102">属性グループを作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="eed9c-102">Create an Attribute Group (Master Data Services)</span></span>
  <span data-ttu-id="eed9c-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、 **[エクスプローラー]** グリッドの個々のタブに属性を表示する場合、属性グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="eed9c-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create attribute groups when you want to display attributes on individual tabs in the **Explorer** grid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eed9c-104">属性グループを作成すると、作成者以外のすべてのユーザーに対して自動的に非表示に設定されます。</span><span class="sxs-lookup"><span data-stu-id="eed9c-104">When you create an attribute group, it is automatically hidden from all users except the one who created it.</span></span> <span data-ttu-id="eed9c-105">グループを表示する方法の詳細については、「 [属性グループのユーザーへの表示 (マスター データ サービス)](make-an-attribute-group-visible-to-users-master-data-services.md)機能領域のグリッドの上部にタブとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="eed9c-105">For more information about making the group visible, see [Make an Attribute Group Visible to Users &#40;Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="eed9c-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="eed9c-106">Prerequisites</span></span>  
 <span data-ttu-id="eed9c-107">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="eed9c-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="eed9c-108">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="eed9c-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="eed9c-109">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="eed9c-109">You must be a model administrator.</span></span> <span data-ttu-id="eed9c-110">詳細については、「[管理者 &#40;マスターデータサービス&#41;](../../2014/master-data-services/administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eed9c-110">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="eed9c-111">少なくとも 1 つの属性が必要です。</span><span class="sxs-lookup"><span data-stu-id="eed9c-111">At least one attribute must exist.</span></span> <span data-ttu-id="eed9c-112">詳細については、「 [テキスト属性を作成する (マスター データ サービス)](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eed9c-112">For more information, see [Create a Text Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md).</span></span>  
  
### <a name="to-create-an-attribute-group"></a><span data-ttu-id="eed9c-113">属性グループを作成するには</span><span class="sxs-lookup"><span data-stu-id="eed9c-113">To create an attribute group</span></span>  
  
1.  <span data-ttu-id="eed9c-114">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eed9c-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="eed9c-115">[**モデルビュー** ] ページのメニューバーから [**管理**] をポイントし、[**属性グループ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eed9c-115">On the **Model View** page, from the menu bar, point to **Manage** and click **Attribute Groups**.</span></span>  
  
3.  <span data-ttu-id="eed9c-116">**[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="eed9c-116">From the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="eed9c-117">**[エンティティ]** の一覧からエンティティを選択します。</span><span class="sxs-lookup"><span data-stu-id="eed9c-117">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="eed9c-118">**[リーフ グループ]**、 **[統合グループ]**、または **[コレクション グループ]** をクリックして、リーフ メンバー、統合メンバー、またはコレクションの属性グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="eed9c-118">Click **Leaf Groups**, **Consolidated Groups**, or **Collection Groups** to create an attribute group of leaf members, consolidated members, or collections respectively.</span></span>  
  
6.  <span data-ttu-id="eed9c-119">[**属性グループの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eed9c-119">Click **Add attribute group**.</span></span>  
  
7.  <span data-ttu-id="eed9c-120">[**リーフグループ名**] ボックスに、グループの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="eed9c-120">In the **Leaf group name** box, type a name for the group.</span></span> <span data-ttu-id="eed9c-121">これは、**エクスプローラー**のタブに表示される名前です。</span><span class="sxs-lookup"><span data-stu-id="eed9c-121">This is the name displayed on the tab in **Explorer**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eed9c-122">手順 5. で [**統合グループ**] または [**コレクショングループ**] を選択した場合、このボックスはそれぞれ [**統合グループ名**] または [**コレクショングループ名**] になります。</span><span class="sxs-lookup"><span data-stu-id="eed9c-122">If you selected **Consolidated Groups** or **Collection Groups** in step 5, this box is **Consolidated group name** or **Collection group name**, respectively.</span></span>  
  
8.  <span data-ttu-id="eed9c-123">**[グループの保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eed9c-123">Click **Save group**.</span></span>  
  
9. <span data-ttu-id="eed9c-124">グループのフォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="eed9c-124">Expand the folder for the group.</span></span>  
  
10. <span data-ttu-id="eed9c-125">**[属性]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eed9c-125">Click **Attributes**.</span></span>  
  
11. <span data-ttu-id="eed9c-126">[**選択したアイテムの編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eed9c-126">Click **Edit selected item**.</span></span>  
  
12. <span data-ttu-id="eed9c-127">**使用可能な**ボックスの [属性] をクリックし、[**追加**] 矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eed9c-127">Click attributes in the **Available** box and click the **Add** arrow.</span></span> <span data-ttu-id="eed9c-128">すべてを追加するには、 **[すべて追加]** 矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eed9c-128">To add all, click the **Add All** arrow.</span></span>  
  
13. <span data-ttu-id="eed9c-129">必要に応じて、**上**矢印と**下**矢印をクリックして、属性の順序を左から右に変更します。</span><span class="sxs-lookup"><span data-stu-id="eed9c-129">Optionally, click the **Up** and **Down** arrows to change the left-to-right order of the attributes.</span></span>  
  
14. <span data-ttu-id="eed9c-130">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eed9c-130">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="eed9c-131">次の手順</span><span class="sxs-lookup"><span data-stu-id="eed9c-131">Next Steps</span></span>  
  
-   [<span data-ttu-id="eed9c-132">属性グループのユーザーへの表示 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="eed9c-132">Make an Attribute Group Visible to Users &#40;Master Data Services&#41;</span></span>](make-an-attribute-group-visible-to-users-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="eed9c-133">参照</span><span class="sxs-lookup"><span data-stu-id="eed9c-133">See Also</span></span>  
 <span data-ttu-id="eed9c-134">[属性グループ &#40;マスターデータサービス&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="eed9c-134">[Attribute Groups &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span></span>  
 <span data-ttu-id="eed9c-135">[属性 &#40;マスターデータサービス&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="eed9c-135">[Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="eed9c-136">[属性グループ名を変更する &#40;マスターデータサービス&#41;](../../2014/master-data-services/change-an-attribute-group-name-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="eed9c-136">[Change an Attribute Group Name &#40;Master Data Services&#41;](../../2014/master-data-services/change-an-attribute-group-name-master-data-services.md) </span></span>  
 <span data-ttu-id="eed9c-137">[属性グループ &#40;マスターデータサービスの削除&#41;](../../2014/master-data-services/delete-an-attribute-group-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="eed9c-137">[Delete an Attribute Group &#40;Master Data Services&#41;](../../2014/master-data-services/delete-an-attribute-group-master-data-services.md) </span></span>  
 <span data-ttu-id="eed9c-138">[リーフアクセス許可 &#40;マスターデータサービス&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="eed9c-138">[Leaf Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="eed9c-139">統合アクセス許可 &#40;マスターデータサービス&#41;</span><span class="sxs-lookup"><span data-stu-id="eed9c-139">Consolidated Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/consolidated-permissions-master-data-services.md)  
  
  
