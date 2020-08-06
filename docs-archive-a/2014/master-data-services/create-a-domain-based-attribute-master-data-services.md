---
title: ドメイン ベースの属性を作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- domain-based attributes [Master Data Services], creating
- creating domain-based attributes [Master Data Services]
- attributes [Master Data Services], creating domain-based attributes
ms.assetid: 11c31c9f-e6cc-47b7-b76a-d691f84c93c6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 51c0f44bb76ae2ad4c25987ed5e5ee144a18c739
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633191"
---
# <a name="create-a-domain-based-attribute-master-data-services"></a><span data-ttu-id="f4be7-102">ドメイン ベースの属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="f4be7-102">Create a Domain-Based Attribute (Master Data Services)</span></span>
  <span data-ttu-id="f4be7-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でドメイン ベースの属性を作成して、属性の値にエンティティのメンバーを設定します。</span><span class="sxs-lookup"><span data-stu-id="f4be7-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a domain-based attribute to populate an attribute's values with members from an entity.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f4be7-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="f4be7-104">Prerequisites</span></span>  
 <span data-ttu-id="f4be7-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="f4be7-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="f4be7-106">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="f4be7-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="f4be7-107">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4be7-107">You must be a model administrator.</span></span> <span data-ttu-id="f4be7-108">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4be7-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="f4be7-109">属性値のソースとして使用する 1 つのエンティティが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4be7-109">An entity must exist to use as the source of the attribute values.</span></span> <span data-ttu-id="f4be7-110">たとえば、Color エンティティに基づくドメイン ベースの属性を作成するには、最初に Color エンティティを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4be7-110">For example, to create a domain-based attribute based on the Color entity, you must first create the Color entity.</span></span> <span data-ttu-id="f4be7-111">詳細については、「[エンティティを作成する (マスター データ サービス)](../../2014/master-data-services/create-an-entity-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4be7-111">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="f4be7-112">属性を作成するエンティティが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4be7-112">An entity must exist to create the attribute for.</span></span> <span data-ttu-id="f4be7-113">詳細については、「[エンティティを作成する (マスター データ サービス)](../../2014/master-data-services/create-an-entity-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4be7-113">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-create-a-domain-based-attribute"></a><span data-ttu-id="f4be7-114">ドメイン ベースの属性を作成するには</span><span class="sxs-lookup"><span data-stu-id="f4be7-114">To create a domain-based attribute</span></span>  
  
1.  <span data-ttu-id="f4be7-115">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f4be7-115">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="f4be7-116">**[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[エンティティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f4be7-116">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="f4be7-117">**[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="f4be7-117">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="f4be7-118">属性を作成するエンティティの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="f4be7-118">Select the row for the entity that you want to create an attribute for.</span></span>  
  
5.  <span data-ttu-id="f4be7-119">**[選択したエンティティの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f4be7-119">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="f4be7-120">**[エンティティの編集]** ページで、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="f4be7-120">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="f4be7-121">リーフ メンバーの属性の場合は、 **[リーフ メンバー属性]** ペインで **[リーフ属性の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f4be7-121">If the attribute is for leaf members, in the **Leaf member attributes** pane, click **Add leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="f4be7-122">統合メンバーの属性の場合は、 **[統合メンバー属性]** ペインで **[統合属性の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f4be7-122">If the attribute is for consolidated members, in the **Consolidated member attributes** pane, click **Add consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="f4be7-123">コレクションの属性の場合は、 **[コレクション属性]** ペインで **[コレクション属性の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f4be7-123">If the attribute is for collections, in the **Collection attributes** pane, click **Add collection attribute**.</span></span>  
  
7.  <span data-ttu-id="f4be7-124">[**属性の追加**] ページで、[**ドメインベース**] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="f4be7-124">On the **Add Attribute** page, select the **Domain-based** option.</span></span>  
  
8.  <span data-ttu-id="f4be7-125">**[名前]** ボックスに属性の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="f4be7-125">In the **Name** box, type a name for the attribute.</span></span> <span data-ttu-id="f4be7-126">この名前は、属性値のソースとして使用するエンティティの名前と同じである必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f4be7-126">It does not have to be the same name as the entity that you use for the source of the attribute values.</span></span>  
  
9. <span data-ttu-id="f4be7-127">**[ピクセル幅の表示]** ボックスに、 **[エクスプローラー]** グリッドに表示する属性列の幅を入力します。</span><span class="sxs-lookup"><span data-stu-id="f4be7-127">In the **Display pixel width** box, type the width of the attribute column to be displayed in the **Explorer** grid.</span></span>  
  
10. <span data-ttu-id="f4be7-128">[**エンティティ**] ボックスの一覧から、属性値を設定するために使用するエンティティを選択します。</span><span class="sxs-lookup"><span data-stu-id="f4be7-128">From the **Entity** list, choose the entity to be used to populate the attribute values.</span></span>  
  
11. <span data-ttu-id="f4be7-129">省略可能。</span><span class="sxs-lookup"><span data-stu-id="f4be7-129">Optional.</span></span> <span data-ttu-id="f4be7-130">**[変更の追跡を有効化]** を選択して、属性のグループに対する変更を追跡します。</span><span class="sxs-lookup"><span data-stu-id="f4be7-130">Select **Enable change tracking** to track changes to groups of attributes.</span></span> <span data-ttu-id="f4be7-131">詳細については、「[変更の追跡グループに属性を追加する方法 (マスター データ サービス)](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4be7-131">For more information, see [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).</span></span>  
  
12. <span data-ttu-id="f4be7-132">**[属性の保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f4be7-132">Click **Save attribute**.</span></span>  
  
13. <span data-ttu-id="f4be7-133">**[エンティティのメンテナンス]** ページで **[エンティティの保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f4be7-133">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4be7-134">参照</span><span class="sxs-lookup"><span data-stu-id="f4be7-134">See Also</span></span>  
 <span data-ttu-id="f4be7-135">[ドメインベースの属性 &#40;マスターデータサービス&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f4be7-135">[Domain-Based Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="f4be7-136">[派生階層 &#40;マスターデータサービスを作成し&#41;](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f4be7-136">[Create a Derived Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md) </span></span>  
 <span data-ttu-id="f4be7-137">[属性名を変更する &#40;マスターデータサービス&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f4be7-137">[Change an Attribute Name &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span></span>  
 [<span data-ttu-id="f4be7-138">属性を削除する &#40;マスター データ サービス&#41;</span><span class="sxs-lookup"><span data-stu-id="f4be7-138">Delete an Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-attribute-master-data-services.md)  
  
  
