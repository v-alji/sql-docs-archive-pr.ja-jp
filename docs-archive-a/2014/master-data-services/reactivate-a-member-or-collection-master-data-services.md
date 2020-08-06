---
title: メンバーまたはコレクションを再アクティブ化する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], reactivating
- consolidated members [Master Data Services], reactivating
- reactivating members [Master Data Services]
- members [Master Data Services], reactivating
- reactivating collections [Master Data Services]
- leaf members [Master Data Services], reactivating
ms.assetid: bb4884c0-3658-4763-92d1-636804278b1c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c449a5a277128bbca6ae24e848bcf12cb0881968
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643456"
---
# <a name="reactivate-a-member-or-collection-master-data-services"></a><span data-ttu-id="26dad-102">メンバーまたはコレクションを再アクティブ化する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="26dad-102">Reactivate a Member or Collection (Master Data Services)</span></span>
  <span data-ttu-id="26dad-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、次のいずれかの状態にあったメンバーを再アクティブ化できます。</span><span class="sxs-lookup"><span data-stu-id="26dad-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can reactivate a member that was either:</span></span>  
  
-   <span data-ttu-id="26dad-104">ステージング処理によって非アクティブにされた。</span><span class="sxs-lookup"><span data-stu-id="26dad-104">Deactivated by the staging process.</span></span>  
  
-   <span data-ttu-id="26dad-105">MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]で削除された。</span><span class="sxs-lookup"><span data-stu-id="26dad-105">Deleted in the MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].</span></span>  
  
-   <span data-ttu-id="26dad-106">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションで削除された。</span><span class="sxs-lookup"><span data-stu-id="26dad-106">Deleted in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
 <span data-ttu-id="26dad-107">メンバーを再アクティブ化すると、階層およびコレクションのメンバーの属性とメンバーシップが復元されます。</span><span class="sxs-lookup"><span data-stu-id="26dad-107">When you reactivate a member, its attributes and its membership in hierarchies and collections are restored.</span></span>  
  
 <span data-ttu-id="26dad-108">また、コレクションを再アクティブ化することもできます。</span><span class="sxs-lookup"><span data-stu-id="26dad-108">You can also reactivate collections.</span></span> <span data-ttu-id="26dad-109">その場合、コレクションの属性と、コレクションに属するメンバーが復元されます。</span><span class="sxs-lookup"><span data-stu-id="26dad-109">When you do, the collection's attributes and the members that belong to the collection are restored.</span></span>  
  
 <span data-ttu-id="26dad-110">メンバーまたはコレクションを再アクティブ化すると、以前のトランザクションがすべて復元されます。</span><span class="sxs-lookup"><span data-stu-id="26dad-110">When either a collection or member is reactivated, all previous transactions are restored.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="26dad-111">前提条件</span><span class="sxs-lookup"><span data-stu-id="26dad-111">Prerequisites</span></span>  
 <span data-ttu-id="26dad-112">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="26dad-112">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="26dad-113">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]の **[バージョン管理]** 機能領域に対する権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="26dad-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], you must have permission to the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="26dad-114">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="26dad-114">You must be a model administrator.</span></span> <span data-ttu-id="26dad-115">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26dad-115">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-reactivate-a-member-or-collection"></a><span data-ttu-id="26dad-116">メンバーまたはコレクションを再アクティブ化するには</span><span class="sxs-lookup"><span data-stu-id="26dad-116">To reactivate a member or collection</span></span>  
  
1.  <span data-ttu-id="26dad-117">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ホーム ページで、 **[バージョン管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="26dad-117">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="26dad-118">メニュー バーの **[トランザクション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="26dad-118">On the menu bar, click **Transactions**.</span></span>  
  
3.  <span data-ttu-id="26dad-119">**[トランザクション]** ページで、 **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="26dad-119">On the **Transactions** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="26dad-120">**[バージョン]** ボックスの一覧からバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="26dad-120">From the **Version** list, select a version.</span></span>  
  
5.  <span data-ttu-id="26dad-121">**[トランザクション]** ペインで、再アクティブ化するメンバーまたはコレクションの行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="26dad-121">In the **Transactions** pane, click the row for the member or collection you want to reactivate.</span></span> <span data-ttu-id="26dad-122">この行の **[以前の値]** 列に **[アクティブ]** 、 **[新しい値]** 列に **[非アクティブ]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="26dad-122">This row should have **Active** displayed in the **Prior Value** column and **De-Activated** in the **New Value** column.</span></span>  
  
6.  <span data-ttu-id="26dad-123">**[トランザクションの破棄]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="26dad-123">Click **Reverse Transaction**.</span></span>  
  
7.  <span data-ttu-id="26dad-124">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="26dad-124">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="26dad-125">**[新しい値]** 列に **[アクティブ]** と表示され、新しいトランザクションが追加されます。</span><span class="sxs-lookup"><span data-stu-id="26dad-125">A new transaction is added, showing **Active** in the **New Value** column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26dad-126">参照</span><span class="sxs-lookup"><span data-stu-id="26dad-126">See Also</span></span>  
 <span data-ttu-id="26dad-127">[ステージング処理を使用したメンバーの非アクティブ化または削除 &#40;マスターデータサービス&#41;](add-update-and-delete-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="26dad-127">[Deactivate or Delete Members by Using the Staging Process &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md) </span></span>  
 <span data-ttu-id="26dad-128">[マスターデータサービス &#40;のメンバーまたはコレクションを削除&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="26dad-128">[Delete a Member or Collection &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md) </span></span>  
 <span data-ttu-id="26dad-129">[メンバー &#40;マスターデータサービス&#41;](../../2014/master-data-services/members-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="26dad-129">[Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span></span>  
 [<span data-ttu-id="26dad-130">コレクション (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="26dad-130">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)  
  
  
