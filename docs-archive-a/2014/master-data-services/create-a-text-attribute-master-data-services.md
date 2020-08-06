---
title: テキスト属性を作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], creating text attributes
- creating text attributes [Master Data Services]
ms.assetid: cd8b57de-364d-42a3-9273-c1c6b992bb40
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c0f44e0e6c6e3df49b6a3746648ee46a23a7a3ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646200"
---
# <a name="create-a-text-attribute-master-data-services"></a><span data-ttu-id="80067-102">テキスト属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="80067-102">Create a Text Attribute (Master Data Services)</span></span>
  <span data-ttu-id="80067-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、ユーザーに属性値としてテキスト文字列を入力させる場合、テキスト属性を作成します。</span><span class="sxs-lookup"><span data-stu-id="80067-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a text attribute when you want users to enter a text string as an attribute value.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="80067-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="80067-104">Prerequisites</span></span>  
 <span data-ttu-id="80067-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="80067-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="80067-106">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="80067-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="80067-107">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="80067-107">You must be a model administrator.</span></span> <span data-ttu-id="80067-108">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80067-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="80067-109">属性を作成するエンティティが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80067-109">An entity must exist to create the attribute for.</span></span> <span data-ttu-id="80067-110">詳細については、「[エンティティを作成する (マスター データ サービス)](../../2014/master-data-services/create-an-entity-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80067-110">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-create-a-text-attribute"></a><span data-ttu-id="80067-111">テキスト属性を作成するには</span><span class="sxs-lookup"><span data-stu-id="80067-111">To create a text attribute</span></span>  
  
1.  <span data-ttu-id="80067-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80067-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="80067-113">**[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[エンティティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80067-113">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="80067-114">**[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="80067-114">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="80067-115">属性を作成するエンティティの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="80067-115">Select the row for the entity that you want to create an attribute for.</span></span>  
  
5.  <span data-ttu-id="80067-116">**[選択したエンティティの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80067-116">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="80067-117">**[エンティティの編集]** ページで、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="80067-117">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="80067-118">リーフ メンバーの属性の場合は、 **[リーフ メンバー属性]** ペインで **[リーフ属性の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80067-118">If the attribute is for leaf members, in the **Leaf member attributes** pane, click **Add leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="80067-119">統合メンバーの属性の場合は、 **[統合メンバー属性]** ペインで **[統合属性の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80067-119">If the attribute is for consolidated members, in the **Consolidated member attributes** pane, click **Add consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="80067-120">コレクションの属性の場合は、 **[コレクション属性]** ペインで **[コレクション属性の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80067-120">If the attribute is for collections, in the **Collection attributes** pane, click **Add collection attribute**.</span></span>  
  
7.  <span data-ttu-id="80067-121">**[属性の追加]** ページで **[自由形式]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="80067-121">On the **Add Attribute** page, select the **Free-form** option.</span></span>  
  
8.  <span data-ttu-id="80067-122">**[名前]** ボックスに属性の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="80067-122">In the **Name** box, type a name for the attribute.</span></span> <span data-ttu-id="80067-123">属性名として使用しない単語の一覧については、「[予約語 &#40;マスターデータサービス&#41;](../../2014/master-data-services/reserved-words-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80067-123">For a list of words that should not be used as attribute names, see [Reserved Words &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="80067-124">**[ピクセル幅の表示]** ボックスに、 **[エクスプローラー]** グリッドに表示する属性列の幅を入力します。</span><span class="sxs-lookup"><span data-stu-id="80067-124">In the **Display pixel width** box, type the width of the attribute column to be displayed in the **Explorer** grid.</span></span>  
  
10. <span data-ttu-id="80067-125">**[データ型]** ボックスの一覧から **[Text]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="80067-125">From the **Data type** list, select **Text**.</span></span>  
  
11. <span data-ttu-id="80067-126">**[長さ]** ボックスに、許可する文字の最大数を入力します。</span><span class="sxs-lookup"><span data-stu-id="80067-126">In the **Length** box, type the maximum number of characters allowed.</span></span>  
  
12. <span data-ttu-id="80067-127">必要に応じて、 **[変更の追跡を有効化]** を選択して、属性のグループに対する変更を追跡します。</span><span class="sxs-lookup"><span data-stu-id="80067-127">Optionally, select **Enable change tracking** to track changes to groups of attributes.</span></span> <span data-ttu-id="80067-128">詳細については、「[変更の追跡グループに属性を追加する方法 (マスター データ サービス)](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80067-128">For more information, see [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).</span></span>  
  
13. <span data-ttu-id="80067-129">**[属性の保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80067-129">Click **Save attribute**.</span></span>  
  
14. <span data-ttu-id="80067-130">**[エンティティのメンテナンス]** ページで **[エンティティの保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80067-130">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80067-131">参照</span><span class="sxs-lookup"><span data-stu-id="80067-131">See Also</span></span>  
 <span data-ttu-id="80067-132">[属性 &#40;マスターデータサービス&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="80067-132">[Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="80067-133">[属性名を変更する &#40;マスターデータサービス&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="80067-133">[Change an Attribute Name &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span></span>  
 <span data-ttu-id="80067-134">[ドメインベースの属性 &#40;マスターデータサービスを作成&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="80067-134">[Create a Domain-Based Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="80067-135">ファイル属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="80067-135">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
  
