---
title: 属性グループのユーザーへの表示 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b2f6cc27-dbc9-4f3f-961e-e81e76375248
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 309ad0392cd717d4a8a11470621144ef9e604fd9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631133"
---
# <a name="make-an-attribute-group-visible-to-users-master-data-services"></a><span data-ttu-id="cd9c5-102">属性グループのユーザーへの表示 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="cd9c5-102">Make an Attribute Group Visible to Users (Master Data Services)</span></span>
  <span data-ttu-id="cd9c5-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、 **[エクスプローラー]** 機能領域のグリッドの上部にタブを表示させる場合は、ユーザーまたはグループに対して属性グループを表示します。</span><span class="sxs-lookup"><span data-stu-id="cd9c5-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], make an attribute group visible to users or groups when you want users to have tabs above the grid in the **Explorer** functional area.</span></span>  
  
 <span data-ttu-id="cd9c5-104">属性グループを作成すると、作成者以外のすべてのユーザーに対して自動的に非表示に設定されます。</span><span class="sxs-lookup"><span data-stu-id="cd9c5-104">When you create an attribute group, it is automatically hidden from all users except the one who created it.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cd9c5-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="cd9c5-105">Prerequisites</span></span>  
 <span data-ttu-id="cd9c5-106">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="cd9c5-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="cd9c5-107">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="cd9c5-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="cd9c5-108">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd9c5-108">You must be a model administrator.</span></span> <span data-ttu-id="cd9c5-109">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd9c5-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="cd9c5-110">少なくとも 1 つの属性グループが必要です。</span><span class="sxs-lookup"><span data-stu-id="cd9c5-110">At least one attribute group must exist.</span></span> <span data-ttu-id="cd9c5-111">詳細については、「 [属性グループを作成する (マスター データ サービス)](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd9c5-111">For more information, see [Create an Attribute Group &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-attribute-group-master-data-services.md).</span></span>  
  
### <a name="to-make-an-attribute-group-visible-to-users"></a><span data-ttu-id="cd9c5-112">属性グループをユーザーに表示するには</span><span class="sxs-lookup"><span data-stu-id="cd9c5-112">To make an attribute group visible to users</span></span>  
  
1.  <span data-ttu-id="cd9c5-113">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd9c5-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="cd9c5-114">[**モデルビュー** ] ページのメニューバーから [**管理**] をポイントし、[**属性グループ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd9c5-114">On the **Model View** page, from the menu bar, point to **Manage** and click **Attribute Groups**.</span></span>  
  
3.  <span data-ttu-id="cd9c5-115">**[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="cd9c5-115">From the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="cd9c5-116">**[エンティティ]** の一覧からエンティティを選択します。</span><span class="sxs-lookup"><span data-stu-id="cd9c5-116">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="cd9c5-117">表示するグループの種類に応じて、プラス記号をクリックして [**リーフグループ**]、[**統合グループ**]、または [**コレクショングループ**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="cd9c5-117">Click the plus sign to expand **Leaf Groups**, **Consolidated Groups**, or **Collection Groups**, depending on the type of group you want to make visible.</span></span>  
  
6.  <span data-ttu-id="cd9c5-118">プラス記号をクリックして、表示するグループを展開します。</span><span class="sxs-lookup"><span data-stu-id="cd9c5-118">Click the plus sign to expand the group you want to make visible.</span></span>  
  
7.  <span data-ttu-id="cd9c5-119">グループをユーザーとグループのどちらに表示するかに応じて、[**ユーザー** ] または [**グループ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd9c5-119">Click either **Users** or **Groups**, depending on whether you are making the group visible to a user or a group.</span></span>  
  
8.  <span data-ttu-id="cd9c5-120">[**選択したアイテムの編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd9c5-120">Click **Edit selected item**.</span></span>  
  
9. <span data-ttu-id="cd9c5-121">**使用可能な**ボックスで [ユーザーまたはグループ] をクリックし、[**追加**] 矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd9c5-121">Click users or groups in the **Available** box and click the **Add** arrow.</span></span> <span data-ttu-id="cd9c5-122">すべてを追加するには、 **[すべて追加]** 矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd9c5-122">To add all, click the **Add All** arrow.</span></span>  
  
10. <span data-ttu-id="cd9c5-123">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd9c5-123">Click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd9c5-124">参照</span><span class="sxs-lookup"><span data-stu-id="cd9c5-124">See Also</span></span>  
 <span data-ttu-id="cd9c5-125">[属性グループ &#40;マスターデータサービス&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cd9c5-125">[Attribute Groups &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span></span>  
 [<span data-ttu-id="cd9c5-126">属性グループを作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="cd9c5-126">Create an Attribute Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)  
  
  
