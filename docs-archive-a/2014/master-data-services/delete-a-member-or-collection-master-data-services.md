---
title: メンバーまたはコレクションを削除する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], deleting
- leaf members [Master Data Services], deleting
- deleting members [Master Data Services]
- members [Master Data Services], deleting
- consolidated members [Master Data Services], deleting
ms.assetid: 519130a7-4226-4d71-9124-d2ee0ce7e5bd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9b248750c0e755c3fc9e32d45068c754e64957b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712101"
---
# <a name="delete-a-member-or-collection-master-data-services"></a><span data-ttu-id="805b6-102">メンバーまたはコレクションを削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="805b6-102">Delete a Member or Collection (Master Data Services)</span></span>
  <span data-ttu-id="805b6-103">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で、不要になったメンバーまたはコレクションを削除します。</span><span class="sxs-lookup"><span data-stu-id="805b6-103">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], delete a member or collection when you no longer need it.</span></span> <span data-ttu-id="805b6-104">複数のメンバーを一括で削除する場合は、代わりにステージング処理を使用します。</span><span class="sxs-lookup"><span data-stu-id="805b6-104">If you want to delete members in bulk, use the staging process instead.</span></span> <span data-ttu-id="805b6-105">詳細については、「 [&#40;マスターデータサービス&#41;のステージング処理を使用したメンバーの非アクティブ化または削除](add-update-and-delete-data-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="805b6-105">For more information, see [Deactivate or Delete Members by Using the Staging Process &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="805b6-106">別のメンバーのドメイン ベースの属性値として使用されているメンバーは削除できません。</span><span class="sxs-lookup"><span data-stu-id="805b6-106">You cannot delete a member if it is used as a domain-based attribute value for another member.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="805b6-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="805b6-107">Prerequisites</span></span>  
 <span data-ttu-id="805b6-108">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="805b6-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="805b6-109">**[エクスプローラー]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="805b6-109">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="805b6-110">メンバーの場合は、メンバーを削除するリーフモデルオブジェクトに対する**更新**権限が最低限必要です。</span><span class="sxs-lookup"><span data-stu-id="805b6-110">For members, you must have a minimum of **Update** permission to the leaf model object you are deleting a member from.</span></span>  
  
-   <span data-ttu-id="805b6-111">コレクションの場合は、削除するリーフ コレクション オブジェクトに対する **更新** 権限が最低限必要です。</span><span class="sxs-lookup"><span data-stu-id="805b6-111">For collections, you must have a minimum of **Update** permission to the leaf collection object you are deleting.</span></span>  
  
### <a name="to-delete-a-member-or-collection"></a><span data-ttu-id="805b6-112">メンバーまたはコレクションを削除するには</span><span class="sxs-lookup"><span data-stu-id="805b6-112">To delete a member or collection</span></span>  
  
1.  <span data-ttu-id="805b6-113">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のホーム ページで、 **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="805b6-113">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="805b6-114">**[バージョン]** ボックスの一覧からバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="805b6-114">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="805b6-115">**[エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="805b6-115">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="805b6-116">次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="805b6-116">To delete:</span></span>  
  
    -   <span data-ttu-id="805b6-117">リーフ メンバーを削除するには、メニュー バーの **[エンティティ]** をポイントして、メンバーを含むエンティティの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="805b6-117">A leaf member, from the menu bar, point to **Entities** and click the name of the entity that contains the member.</span></span>  
  
    -   <span data-ttu-id="805b6-118">統合メンバーを削除するには、メニュー バーの **[階層]** をポイントして、メンバーを含む階層の名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="805b6-118">A consolidated member, from the menu bar, point to **Hierarchies** and click the name of the hierarchy that contains the member.</span></span> <span data-ttu-id="805b6-119">階層内で、メンバーが含まれているノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="805b6-119">Then click the node in the hierarchy that contains the member.</span></span>  
  
    -   <span data-ttu-id="805b6-120">コレクションを削除するには、メニュー バーの **[コレクション]** をポイントして、コレクションを含むエンティティの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="805b6-120">A collection, from the menu bar, point to **Collections** and click the name of the entity that contains the collection.</span></span>  
  
5.  <span data-ttu-id="805b6-121">グリッドで、削除するメンバーまたはコレクションの行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="805b6-121">In the grid, click the row of the member or collection you want to delete.</span></span>  
  
6.  <span data-ttu-id="805b6-122">**[メンバーの削除]**、 **[削除]**、または **[コレクションの削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="805b6-122">Click **Delete Member**, **Delete**, or **Delete Collection**.</span></span>  
  
7.  <span data-ttu-id="805b6-123">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="805b6-123">In the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="805b6-124">参照</span><span class="sxs-lookup"><span data-stu-id="805b6-124">See Also</span></span>  
 <span data-ttu-id="805b6-125">[メンバーまたはコレクションを再アクティブ化する &#40;マスターデータサービス&#41;](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="805b6-125">[Reactivate a Member or Collection &#40;Master Data Services&#41;](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md) </span></span>  
 <span data-ttu-id="805b6-126">[メンバー &#40;マスターデータサービス&#41;](../../2014/master-data-services/members-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="805b6-126">[Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span></span>  
 [<span data-ttu-id="805b6-127">コレクション (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="805b6-127">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)  
  
  
