---
title: 属性グループ名を変更する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services], changing name
ms.assetid: 79510fcf-4c83-4426-bdd4-15b4170ecfbd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 99278302ddda4b05a302b6edd5d724ab49ca5c0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718381"
---
# <a name="change-an-attribute-group-name-master-data-services"></a><span data-ttu-id="68f84-102">属性グループ名を変更する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="68f84-102">Change an Attribute Group Name (Master Data Services)</span></span>
  <span data-ttu-id="68f84-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、属性グループ名を変更できます。</span><span class="sxs-lookup"><span data-stu-id="68f84-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can change the name of an attribute group.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="68f84-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="68f84-104">Prerequisites</span></span>  
 <span data-ttu-id="68f84-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="68f84-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="68f84-106">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="68f84-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="68f84-107">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="68f84-107">You must be a model administrator.</span></span> <span data-ttu-id="68f84-108">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68f84-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-change-an-attribute-group-name"></a><span data-ttu-id="68f84-109">属性グループ名を変更するには</span><span class="sxs-lookup"><span data-stu-id="68f84-109">To change an attribute group name</span></span>  
  
1.  <span data-ttu-id="68f84-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68f84-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="68f84-111">[**モデルビュー** ] ページのメニューバーから [**管理**] をポイントし、[**属性グループ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68f84-111">On the **Model View** page, from the menu bar, point to **Manage** and click **Attribute Groups**.</span></span>  
  
3.  <span data-ttu-id="68f84-112">**[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="68f84-112">From the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="68f84-113">**[エンティティ]** の一覧からエンティティを選択します。</span><span class="sxs-lookup"><span data-stu-id="68f84-113">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="68f84-114">更新するグループの種類に応じて、プラス記号をクリックして [**リーフグループ**]、[**統合グループ**]、または [**コレクショングループ**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="68f84-114">Click the plus sign to expand **Leaf Groups**, **Consolidated Groups**, or **Collection Groups**, depending on the type of group you want to update.</span></span>  
  
6.  <span data-ttu-id="68f84-115">変更する属性グループの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68f84-115">Click the name of the attribute group with the name you want to change.</span></span>  
  
7.  <span data-ttu-id="68f84-116">[**選択したアイテムの編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68f84-116">Click **Edit selected item**.</span></span>  
  
8.  <span data-ttu-id="68f84-117">[**リーフグループ名**] ボックス、[**統合グループ名**] ボックス、または [**コレクショングループ名**] ボックスに、属性グループの更新後の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="68f84-117">In the **Leaf group name** box, **Consolidated group name** box, or **Collection group name** box, type the updated name of the attribute group.</span></span>  
  
9. <span data-ttu-id="68f84-118">**[グループの保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68f84-118">Click **Save group**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68f84-119">参照</span><span class="sxs-lookup"><span data-stu-id="68f84-119">See Also</span></span>  
 <span data-ttu-id="68f84-120">[属性グループ &#40;マスターデータサービス&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="68f84-120">[Attribute Groups &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span></span>  
 <span data-ttu-id="68f84-121">[属性グループ &#40;マスターデータサービスを作成し&#41;](../../2014/master-data-services/create-an-attribute-group-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="68f84-121">[Create an Attribute Group &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-attribute-group-master-data-services.md) </span></span>  
 [<span data-ttu-id="68f84-122">属性グループを削除する &#40;マスター データ サービス&#41;</span><span class="sxs-lookup"><span data-stu-id="68f84-122">Delete an Attribute Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-attribute-group-master-data-services.md)  
  
  
