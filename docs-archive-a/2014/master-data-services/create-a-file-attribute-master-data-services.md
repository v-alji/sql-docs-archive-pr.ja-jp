---
title: ファイル属性を作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating file attributes [Master Data Services]
- attributes [Master Data Services], creating file attributes
ms.assetid: d224886b-2ef1-4658-8b01-2213cc4b8df6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f4f6e2f10a830d089d1d217f7cf54d0b8557add9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633190"
---
# <a name="create-a-file-attribute-master-data-services"></a><span data-ttu-id="772ca-102">ファイル属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="772ca-102">Create a File Attribute (Master Data Services)</span></span>
  <span data-ttu-id="772ca-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でファイル属性を作成して、ファイルで属性値を設定します。</span><span class="sxs-lookup"><span data-stu-id="772ca-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a file attribute to populate attribute values with files.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="772ca-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="772ca-104">Prerequisites</span></span>  
 <span data-ttu-id="772ca-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="772ca-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="772ca-106">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="772ca-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="772ca-107">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="772ca-107">You must be a model administrator.</span></span> <span data-ttu-id="772ca-108">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="772ca-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="772ca-109">属性を作成するエンティティが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="772ca-109">An entity must exist to create the attribute for.</span></span> <span data-ttu-id="772ca-110">詳細については、「[エンティティを作成する (マスター データ サービス)](../../2014/master-data-services/create-an-entity-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="772ca-110">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-create-a-file-attribute"></a><span data-ttu-id="772ca-111">ファイル属性を作成するには</span><span class="sxs-lookup"><span data-stu-id="772ca-111">To create a file attribute</span></span>  
  
1.  <span data-ttu-id="772ca-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ca-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="772ca-113">**[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[エンティティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ca-113">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="772ca-114">**[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="772ca-114">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="772ca-115">属性を作成するエンティティの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="772ca-115">Select the row for the entity that you want to create an attribute for.</span></span>  
  
5.  <span data-ttu-id="772ca-116">**[選択したエンティティの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ca-116">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="772ca-117">**[エンティティの編集]** ページで、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="772ca-117">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="772ca-118">リーフ メンバーの属性の場合は、 **[リーフ メンバー属性]** ペインで **[リーフ属性の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ca-118">If the attribute is for leaf members, in the **Leaf member attributes** pane, click **Add leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="772ca-119">統合メンバーの属性の場合は、 **[統合メンバー属性]** ペインで **[統合属性の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ca-119">If the attribute is for consolidated members, in the **Consolidated member attributes** pane, click **Add consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="772ca-120">コレクションの属性の場合は、 **[コレクション属性]** ペインで **[コレクション属性の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ca-120">If the attribute is for collections, in the **Collection attributes** pane, click **Add collection attribute**.</span></span>  
  
7.  <span data-ttu-id="772ca-121">[**属性の追加**] ページで、[**ファイル**] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="772ca-121">On the **Add Attribute** page, select the **File** option.</span></span>  
  
8.  <span data-ttu-id="772ca-122">**[名前]** ボックスに属性の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="772ca-122">In the **Name** box, type a name for the attribute.</span></span> <span data-ttu-id="772ca-123">属性名として使用しない単語の一覧については、「[予約語 &#40;マスターデータサービス&#41;](../../2014/master-data-services/reserved-words-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="772ca-123">For a list of words that should not be used as attribute names, see [Reserved Words &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="772ca-124">**[ピクセル幅の表示]** ボックスに、 **[エクスプローラー]** グリッドに表示する属性列の幅を入力します。</span><span class="sxs-lookup"><span data-stu-id="772ca-124">In the **Display pixel width** box, type the width of the attribute column to be displayed in the **Explorer** grid.</span></span>  
  
10. <span data-ttu-id="772ca-125">[**ファイル拡張子**] ボックスの一覧で、ユーザーがアップロードできるファイルの種類を1つ以上選択するか、既定値 (\*.) のままにして \* すべてのファイルの種類を許可します。</span><span class="sxs-lookup"><span data-stu-id="772ca-125">From the **File extension** list, select one or more file types that a user can upload, or leave the default (\*.\*) to allow all file types.</span></span>  
  
11. <span data-ttu-id="772ca-126">必要に応じて、 **[変更の追跡を有効化]** を選択して、属性のグループに対する変更を追跡します。</span><span class="sxs-lookup"><span data-stu-id="772ca-126">Optionally, select **Enable change tracking** to track changes to groups of attributes.</span></span> <span data-ttu-id="772ca-127">詳細については、「[変更の追跡グループに属性を追加する方法 (マスター データ サービス)](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="772ca-127">For more information, see [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).</span></span>  
  
12. <span data-ttu-id="772ca-128">**[属性の保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ca-128">Click **Save attribute**.</span></span>  
  
13. <span data-ttu-id="772ca-129">**[エンティティのメンテナンス]** ページで **[エンティティの保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ca-129">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="772ca-130">参照</span><span class="sxs-lookup"><span data-stu-id="772ca-130">See Also</span></span>  
 <span data-ttu-id="772ca-131">[属性 &#40;マスターデータサービス&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="772ca-131">[Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="772ca-132">[属性名を変更する &#40;マスターデータサービス&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="772ca-132">[Change an Attribute Name &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span></span>  
 <span data-ttu-id="772ca-133">[ドメインベースの属性 &#40;マスターデータサービスを作成&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="772ca-133">[Create a Domain-Based Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="772ca-134">テキスト属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="772ca-134">Create a Text Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)  
  
  
