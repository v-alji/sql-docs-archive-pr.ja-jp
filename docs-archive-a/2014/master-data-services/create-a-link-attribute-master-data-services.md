---
title: リンク属性を作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], creating link attributes
- creating link attributes [Master Data Services]
ms.assetid: e6658e9c-5b08-4b8d-b556-17ec2dd041d2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4770d7904371c10dc6720e8d3d7f28ca797d9b80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645719"
---
# <a name="create-a-link-attribute-master-data-services"></a><span data-ttu-id="a2feb-102">リンク属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="a2feb-102">Create a Link Attribute (Master Data Services)</span></span>
  <span data-ttu-id="a2feb-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] でユーザーに属性値としてハイパーリンク (`http://www.contoso.com` など) を入力させる場合、リンク属性を作成します。</span><span class="sxs-lookup"><span data-stu-id="a2feb-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a link attribute when you want users to enter a hyperlink as an attribute value, such as `http://www.contoso.com`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a2feb-104">ユーザーがリンク属性の値を入力するとき、文字列は **http://** で始まる必要があり、そうでないとエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a2feb-104">When users enter a value for a link attribute, the string must begin with **http://** or an error will be displayed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a2feb-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="a2feb-105">Prerequisites</span></span>  
 <span data-ttu-id="a2feb-106">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="a2feb-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="a2feb-107">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="a2feb-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="a2feb-108">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2feb-108">You must be a model administrator.</span></span> <span data-ttu-id="a2feb-109">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2feb-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="a2feb-110">属性を作成するエンティティが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2feb-110">An entity must exist to create the attribute for.</span></span> <span data-ttu-id="a2feb-111">詳細については、「[エンティティを作成する (マスター データ サービス)](../../2014/master-data-services/create-an-entity-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2feb-111">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-create-a-link-attribute"></a><span data-ttu-id="a2feb-112">リンク属性を作成するには</span><span class="sxs-lookup"><span data-stu-id="a2feb-112">To create a link attribute</span></span>  
  
1.  <span data-ttu-id="a2feb-113">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2feb-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="a2feb-114">**[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[エンティティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2feb-114">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="a2feb-115">**[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="a2feb-115">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="a2feb-116">属性を作成するエンティティの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="a2feb-116">Select the row for the entity that you want to create an attribute for.</span></span>  
  
5.  <span data-ttu-id="a2feb-117">**[選択したエンティティの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2feb-117">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="a2feb-118">**[エンティティの編集]** ページで、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="a2feb-118">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="a2feb-119">リーフ メンバーの属性の場合は、 **[リーフ メンバー属性]** ペインで **[リーフ属性の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2feb-119">If the attribute is for leaf members, in the **Leaf member attributes** pane, click **Add leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="a2feb-120">統合メンバーの属性の場合は、 **[統合メンバー属性]** ペインで **[統合属性の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2feb-120">If the attribute is for consolidated members, in the **Consolidated member attributes** pane, click **Add consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="a2feb-121">コレクションの属性の場合は、 **[コレクション属性]** ペインで **[コレクション属性の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2feb-121">If the attribute is for collections, in the **Collection attributes** pane, click **Add collection attribute**.</span></span>  
  
7.  <span data-ttu-id="a2feb-122">**[属性の追加]** ページで **[自由形式]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="a2feb-122">On the **Add Attribute** page, select the **Free-form** option.</span></span>  
  
8.  <span data-ttu-id="a2feb-123">**[名前]** ボックスに属性の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="a2feb-123">In the **Name** box, type a name for the attribute.</span></span> <span data-ttu-id="a2feb-124">属性名として使用しない単語の一覧については、「[予約語 &#40;マスターデータサービス&#41;](../../2014/master-data-services/reserved-words-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2feb-124">For a list of words that should not be used as attribute names, see [Reserved Words &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="a2feb-125">**[ピクセル幅の表示]** ボックスに、 **[エクスプローラー]** グリッドに表示する属性列の幅を入力します。</span><span class="sxs-lookup"><span data-stu-id="a2feb-125">In the **Display pixel width** box, type the width of the attribute column to be displayed in the **Explorer** grid.</span></span>  
  
10. <span data-ttu-id="a2feb-126">**[データ型]** ボックスの一覧から **[リンク]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a2feb-126">From the **Data type** list, select **Link**.</span></span>  
  
11. <span data-ttu-id="a2feb-127">**[長さ]** ボックスに、許可する文字の最大数を入力します。</span><span class="sxs-lookup"><span data-stu-id="a2feb-127">In the **Length** box, type the maximum number of characters allowed.</span></span>  
  
12. <span data-ttu-id="a2feb-128">必要に応じて、 **[変更の追跡を有効化]** を選択して、属性のグループに対する変更を追跡します。</span><span class="sxs-lookup"><span data-stu-id="a2feb-128">Optionally, select **Enable change tracking** to track changes to groups of attributes.</span></span> <span data-ttu-id="a2feb-129">詳細については、「[変更の追跡グループに属性を追加する方法 (マスター データ サービス)](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2feb-129">For more information, see [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).</span></span>  
  
13. <span data-ttu-id="a2feb-130">**[属性の保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2feb-130">Click **Save attribute**.</span></span>  
  
14. <span data-ttu-id="a2feb-131">**[エンティティのメンテナンス]** ページで **[エンティティの保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2feb-131">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2feb-132">参照</span><span class="sxs-lookup"><span data-stu-id="a2feb-132">See Also</span></span>  
 <span data-ttu-id="a2feb-133">[属性 &#40;マスターデータサービス&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="a2feb-133">[Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="a2feb-134">[属性名を変更する &#40;マスターデータサービス&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="a2feb-134">[Change an Attribute Name &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span></span>  
 <span data-ttu-id="a2feb-135">[ドメインベースの属性 &#40;マスターデータサービスを作成&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="a2feb-135">[Create a Domain-Based Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="a2feb-136">ファイル属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="a2feb-136">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
  
