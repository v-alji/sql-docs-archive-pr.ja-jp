---
title: 属性を削除する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], deleting
- deleting attributes [Master Data Services]
ms.assetid: ec3e66f7-0e35-43d7-a80d-64899948ebfe
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 96db56dac9356b1131e722fc7f6b779c93305bb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712098"
---
# <a name="delete-an-attribute-master-data-services"></a><span data-ttu-id="78219-102">属性を削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="78219-102">Delete an Attribute (Master Data Services)</span></span>
  <span data-ttu-id="78219-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、属性とそれに関連付けられたすべての属性値を完全に削除するには、属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="78219-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete an attribute when you want to permanently delete the attribute and all associated attribute values.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="78219-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="78219-104">Prerequisites</span></span>  
 <span data-ttu-id="78219-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="78219-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="78219-106">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="78219-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="78219-107">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="78219-107">You must be a model administrator.</span></span> <span data-ttu-id="78219-108">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78219-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-an-attribute"></a><span data-ttu-id="78219-109">属性を削除するには</span><span class="sxs-lookup"><span data-stu-id="78219-109">To delete an attribute</span></span>  
  
1.  <span data-ttu-id="78219-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="78219-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="78219-111">**[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[エンティティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="78219-111">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="78219-112">**[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="78219-112">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="78219-113">削除する属性を含むエンティティの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="78219-113">Select the row for the entity that contains the attribute you want to delete.</span></span>  
  
5.  <span data-ttu-id="78219-114">**[選択したエンティティの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="78219-114">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="78219-115">[**エンティティの編集**] ページで、削除する属性をクリックします。</span><span class="sxs-lookup"><span data-stu-id="78219-115">On the **Edit Entity** page, click the attribute you want to delete.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="78219-116">Name 属性または Code 属性を削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="78219-116">You cannot delete the Name or Code attributes.</span></span>  
  
7.  <span data-ttu-id="78219-117">[**選択した属性の削除**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="78219-117">Click **Delete selected attribute**.</span></span>  
  
8.  <span data-ttu-id="78219-118">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="78219-118">In the confirmation dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="78219-119">追加の確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="78219-119">In the additional confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78219-120">参照</span><span class="sxs-lookup"><span data-stu-id="78219-120">See Also</span></span>  
 <span data-ttu-id="78219-121">[属性 &#40;マスターデータサービス&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="78219-121">[Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="78219-122">[ドメインベースの属性 &#40;マスターデータサービス&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="78219-122">[Domain-Based Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="78219-123">[テキスト属性 &#40;マスターデータサービスを作成し&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="78219-123">[Create a Text Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="78219-124">ドメイン ベースの属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="78219-124">Create a Domain-Based Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
  
