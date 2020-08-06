---
title: 階層内のメンバーを移動する (マスターデータサービス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services], moving members
- explicit hierarchies, moving members
- derived hierarchies, moving members
- members [Master Data Services], moving
ms.assetid: 049c9a15-89c1-478c-8438-028fffc9e187
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 37167f76b965197dbf8e37e365778395ec640d38
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639552"
---
# <a name="move-members-within-a-hierarchy-master-data-services"></a><span data-ttu-id="c5c6e-102">階層内のメンバーを移動する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c5c6e-102">Move Members within a Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="c5c6e-103">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で、階層内のメンバーを移動してその場所または親割り当てを変更します。</span><span class="sxs-lookup"><span data-stu-id="c5c6e-103">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], move members within a hierarchy to change their location or parent assignment.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c5c6e-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="c5c6e-104">Prerequisites</span></span>  
 <span data-ttu-id="c5c6e-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="c5c6e-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="c5c6e-106">**[エクスプローラー]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="c5c6e-106">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="c5c6e-107">明示的階層の場合は、エンティティに対する**更新**権限が最低限必要です。</span><span class="sxs-lookup"><span data-stu-id="c5c6e-107">For explicit hierarchies, you must have a minimum of **Update** permission to the entity.</span></span>  
  
-   <span data-ttu-id="c5c6e-108">派生階層の場合、モデルと、階層で使用されるドメインベースの属性を**更新**する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5c6e-108">For derived hierarchies, you must have a minimum of **Update** to the model and to any domain-based attributes used in the hierarchy.</span></span>  
  
### <a name="to-move-members-within-a-hierarchy"></a><span data-ttu-id="c5c6e-109">階層内のメンバーを移動するには</span><span class="sxs-lookup"><span data-stu-id="c5c6e-109">To move members within a hierarchy</span></span>  
  
1.  <span data-ttu-id="c5c6e-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のホーム ページで、 **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="c5c6e-110">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="c5c6e-111">**[バージョン]** ボックスの一覧からバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="c5c6e-111">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="c5c6e-112">**[エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5c6e-112">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="c5c6e-113">メニューバーの [**階層**] をポイントし、[ *hierarchy_name*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5c6e-113">From the menu bar, point to **Hierarchies** and click *hierarchy_name*.</span></span>  
  
5.  <span data-ttu-id="c5c6e-114">階層がツリー構造で表示されている [**階層**] ペインで、移動する各メンバーのチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="c5c6e-114">In the **Hierarchy** pane, where the hierarchy is displayed in a tree structure, click the check box for each member you want to move.</span></span>  
  
6.  <span data-ttu-id="c5c6e-115">**階層**ペインの上部にある [**切り取り**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5c6e-115">At the top of the **Hierarchy** pane, click **Cut**.</span></span>  
  
7.  <span data-ttu-id="c5c6e-116">[**階層**] ペインで、メンバーの移動先となるメンバーのチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="c5c6e-116">In the **Hierarchy** pane, click the check box for the member you want to move the members to.</span></span>  
  
8.  <span data-ttu-id="c5c6e-117">[**貼り付け**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5c6e-117">Click **Paste**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c5c6e-118">派生階層では、メンバーは同じレベルにのみ移動できます。</span><span class="sxs-lookup"><span data-stu-id="c5c6e-118">In derived hierarchies, you can move members to the same level only.</span></span> <span data-ttu-id="c5c6e-119">また、メンバーの並べ替え順序は変更できません。</span><span class="sxs-lookup"><span data-stu-id="c5c6e-119">Also, you cannot change the sort order of members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5c6e-120">参照</span><span class="sxs-lookup"><span data-stu-id="c5c6e-120">See Also</span></span>  
 <span data-ttu-id="c5c6e-121">[ステージングプロセス &#40;マスターデータサービスを使用して明示的階層メンバーを移動する&#41;](add-update-and-delete-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="c5c6e-121">[Move Explicit Hierarchy Members by Using the Staging Process &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md) </span></span>  
 <span data-ttu-id="c5c6e-122">[派生階層 &#40;マスターデータサービス&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="c5c6e-122">[Derived Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md) </span></span>  
 [<span data-ttu-id="c5c6e-123">明示的階層 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c5c6e-123">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
