---
title: 数値属性を作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], creating number attributes
- creating number attributes [Master Data Services]
ms.assetid: c0dbb6d8-ba78-485a-a40d-6d5cb7e75d0a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bb9302c0b585c21410a6a764dc2e6dac845c6299
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631135"
---
# <a name="create-a-numeric-attribute-master-data-services"></a><span data-ttu-id="01345-102">数値属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="01345-102">Create a Numeric Attribute (Master Data Services)</span></span>
  <span data-ttu-id="01345-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、ユーザーにより属性値として数値が入力される場合は、数値属性を作成します。</span><span class="sxs-lookup"><span data-stu-id="01345-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a numeric attribute when you want users to enter a number as an attribute value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="01345-104">数値属性には制限があります。</span><span class="sxs-lookup"><span data-stu-id="01345-104">Numeric attributes have limitations.</span></span> <span data-ttu-id="01345-105">詳細については、「 [属性 (マスター データ サービス)](attributes-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01345-105">For more information, see [Attributes &#40;Master Data Services&#41;](attributes-master-data-services.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="01345-106">[前提条件]</span><span class="sxs-lookup"><span data-stu-id="01345-106">Prerequisites</span></span>  
 <span data-ttu-id="01345-107">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="01345-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="01345-108">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="01345-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="01345-109">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="01345-109">You must be a model administrator.</span></span> <span data-ttu-id="01345-110">詳細については、「[管理者 &#40;マスターデータサービス&#41;](../../2014/master-data-services/administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01345-110">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="01345-111">属性を作成するエンティティが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01345-111">An entity must exist to create the attribute for.</span></span> <span data-ttu-id="01345-112">詳細については、「[エンティティを作成する (マスター データ サービス)](../../2014/master-data-services/create-an-entity-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01345-112">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-create-a-numeric-attribute"></a><span data-ttu-id="01345-113">数値属性を作成するには</span><span class="sxs-lookup"><span data-stu-id="01345-113">To create a numeric attribute</span></span>  
  
1.  <span data-ttu-id="01345-114">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="01345-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="01345-115">**[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[エンティティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="01345-115">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="01345-116">**[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="01345-116">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="01345-117">属性を作成するエンティティの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="01345-117">Select the row for the entity that you want to create an attribute for.</span></span>  
  
5.  <span data-ttu-id="01345-118">**[選択したエンティティの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="01345-118">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="01345-119">**[エンティティの編集]** ページで、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="01345-119">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="01345-120">リーフ メンバーの属性の場合は、 **[リーフ メンバー属性]** ペインで **[リーフ属性の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="01345-120">If the attribute is for leaf members, in the **Leaf member attributes** pane, click **Add leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="01345-121">統合メンバーの属性の場合は、 **[統合メンバー属性]** ペインで **[統合属性の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="01345-121">If the attribute is for consolidated members, in the **Consolidated member attributes** pane, click **Add consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="01345-122">コレクションの属性の場合は、 **[コレクション属性]** ペインで **[コレクション属性の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="01345-122">If the attribute is for collections, in the **Collection attributes** pane, click **Add collection attribute**.</span></span>  
  
7.  <span data-ttu-id="01345-123">**[属性の追加]** ページで **[自由形式]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="01345-123">On the **Add Attribute** page, select the **Free-form** option.</span></span>  
  
8.  <span data-ttu-id="01345-124">**[名前]** ボックスに属性の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="01345-124">In the **Name** box, type a name for the attribute.</span></span> <span data-ttu-id="01345-125">属性名として使用しない単語の一覧については、「[予約語 &#40;マスターデータサービス&#41;](../../2014/master-data-services/reserved-words-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01345-125">For a list of words that should not be used as attribute names, see [Reserved Words &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="01345-126">**[ピクセル幅の表示]** ボックスに、 **[エクスプローラー]** グリッドに表示する属性列の幅を入力します。</span><span class="sxs-lookup"><span data-stu-id="01345-126">In the **Display pixel width** box, type the width of the attribute column to be displayed in the **Explorer** grid.</span></span>  
  
10. <span data-ttu-id="01345-127">**[データ型]** ボックスの一覧から **[Number]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="01345-127">From the **Data type** list, select **Number**.</span></span>  
  
11. <span data-ttu-id="01345-128">**[10 進]** ボックスに、小数点の後に入力できる数字の桁数を入力します。</span><span class="sxs-lookup"><span data-stu-id="01345-128">In the **Decimals** box, type the number of numbers that can be entered after a decimal.</span></span>  
  
12. <span data-ttu-id="01345-129">[**定型入力**] ボックスの一覧から、負の数値の形式を選択します。</span><span class="sxs-lookup"><span data-stu-id="01345-129">From the **Input mask** list, select a format for negative numbers.</span></span>  
  
13. <span data-ttu-id="01345-130">必要に応じて、 **[変更の追跡を有効化]** を選択して、属性のグループに対する変更を追跡します。</span><span class="sxs-lookup"><span data-stu-id="01345-130">Optionally, select **Enable change tracking** to track changes to groups of attributes.</span></span> <span data-ttu-id="01345-131">詳細については、「 [変更の追跡グループに属性を追加する (マスター データ サービス)](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01345-131">See [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) for more information.</span></span>  
  
14. <span data-ttu-id="01345-132">**[属性の保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="01345-132">Click **Save attribute**.</span></span>  
  
15. <span data-ttu-id="01345-133">**[エンティティのメンテナンス]** ページで **[エンティティの保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="01345-133">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01345-134">参照</span><span class="sxs-lookup"><span data-stu-id="01345-134">See Also</span></span>  
 <span data-ttu-id="01345-135">[属性 &#40;マスターデータサービス&#41;](attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="01345-135">[Attributes &#40;Master Data Services&#41;](attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="01345-136">[属性名を変更する &#40;マスターデータサービス&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="01345-136">[Change an Attribute Name &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span></span>  
 <span data-ttu-id="01345-137">[ドメインベースの属性 &#40;マスターデータサービスを作成&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="01345-137">[Create a Domain-Based Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="01345-138">ファイル属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="01345-138">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
  
