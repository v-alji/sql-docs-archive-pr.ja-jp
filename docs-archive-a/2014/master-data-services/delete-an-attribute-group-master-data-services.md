---
title: 属性グループを削除する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting attribute groups [Master Data Services]
- attribute groups [Master Data Services], deleting
ms.assetid: f915e89b-629d-4725-aea6-a7f051978244
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 833c5cf327034b25d68af123a1fc134372bd6f10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645148"
---
# <a name="delete-an-attribute-group-master-data-services"></a><span data-ttu-id="b2665-102">属性グループを削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="b2665-102">Delete an Attribute Group (Master Data Services)</span></span>
  <span data-ttu-id="b2665-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、 **の** [エクスプローラー] [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]機能領域にタブを表示する必要がなくなった属性グループを削除します。</span><span class="sxs-lookup"><span data-stu-id="b2665-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete an attribute group when you no longer need the tab to display in the **Explorer** functional area of [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
-   <span data-ttu-id="b2665-104">**注** 属性グループが存在する場合、いずれの属性グループにも属さない属性は **[エクスプローラー]** に表示されません。</span><span class="sxs-lookup"><span data-stu-id="b2665-104">**Note** When attribute groups exist, attributes that do not belong to an attribute group are not displayed in **Explorer**.</span></span> <span data-ttu-id="b2665-105">属性グループが存在しない場合、すべての属性が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2665-105">When no attribute groups exist, all attributes are displayed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b2665-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="b2665-106">Prerequisites</span></span>  
 <span data-ttu-id="b2665-107">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="b2665-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="b2665-108">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="b2665-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="b2665-109">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2665-109">You must be a model administrator.</span></span> <span data-ttu-id="b2665-110">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2665-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-an-attribute-group"></a><span data-ttu-id="b2665-111">属性グループを削除するには</span><span class="sxs-lookup"><span data-stu-id="b2665-111">To delete an attribute group</span></span>  
  
1.  <span data-ttu-id="b2665-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2665-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="b2665-113">[**モデルビュー** ] ページのメニューバーから [**管理**] をポイントし、[**属性グループ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2665-113">On the **Model View** page, from the menu bar, point to **Manage** and click **Attribute Groups**.</span></span>  
  
3.  <span data-ttu-id="b2665-114">**[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b2665-114">From the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="b2665-115">**[エンティティ]** の一覧からエンティティを選択します。</span><span class="sxs-lookup"><span data-stu-id="b2665-115">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="b2665-116">削除するグループの種類に応じて、[**リーフグループ**]、[**統合グループ**]、または [**コレクショングループ**] をプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="b2665-116">Click the plus sign to expand **Leaf Groups**, **Consolidated Groups**, or **Collection Groups**, depending on the type of group you want to delete.</span></span>  
  
6.  <span data-ttu-id="b2665-117">削除する属性グループをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2665-117">Click the attribute group you want to delete.</span></span>  
  
7.  <span data-ttu-id="b2665-118">[**選択したグループの削除**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2665-118">Click **Delete selected group**.</span></span>  
  
8.  <span data-ttu-id="b2665-119">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2665-119">In the confirmation dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="b2665-120">追加の確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2665-120">In the additional confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2665-121">参照</span><span class="sxs-lookup"><span data-stu-id="b2665-121">See Also</span></span>  
 <span data-ttu-id="b2665-122">[属性グループ &#40;マスターデータサービス&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="b2665-122">[Attribute Groups &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span></span>  
 [<span data-ttu-id="b2665-123">属性グループを作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="b2665-123">Create an Attribute Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)  
  
  
