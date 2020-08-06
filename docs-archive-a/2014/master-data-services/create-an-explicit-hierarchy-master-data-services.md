---
title: 明示的階層を作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating explicit hierarchies [Master Data Services]
- explicit hierarchies, creating
ms.assetid: ba768393-6990-4eda-8cb0-d58cb3cfc2e2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: aebf95e68f210fe5a573aed092231670c10fa188
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642843"
---
# <a name="create-an-explicit-hierarchy-master-data-services"></a><span data-ttu-id="92a6c-102">明示的階層を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="92a6c-102">Create an Explicit Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="92a6c-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で任意のレベルでメンバーが存在できる不規則階層が必要な場合、明示的階層を作成します。</span><span class="sxs-lookup"><span data-stu-id="92a6c-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create an explicit hierarchy when you need a ragged hierarchy in which members can exist at any level.</span></span> <span data-ttu-id="92a6c-104">明示的階層には、1 つのエンティティのメンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="92a6c-104">Explicit hierarchies contain members from a single entity.</span></span>  
  
 <span data-ttu-id="92a6c-105">明示的階層を作成したら、 **[エクスプローラー]** 機能領域で明示的階層にメンバーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="92a6c-105">After you create an explicit hierarchy, you can add members to it in the **Explorer** functional area.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="92a6c-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="92a6c-106">Prerequisites</span></span>  
 <span data-ttu-id="92a6c-107">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="92a6c-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="92a6c-108">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="92a6c-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="92a6c-109">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="92a6c-109">You must be a model administrator.</span></span> <span data-ttu-id="92a6c-110">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92a6c-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="92a6c-111">エンティティは、明示的階層およびコレクションに対して有効化されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="92a6c-111">The entity must be enabled for explicit hierarchies and collections.</span></span> <span data-ttu-id="92a6c-112">詳細については、「[明示的階層とコレクションのエンティティの有効化 &#40;マスターデータサービス&#41;](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92a6c-112">For more information, see [Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).</span></span>  
  
### <a name="to-create-an-explicit-hierarchy"></a><span data-ttu-id="92a6c-113">明示的階層を作成するには</span><span class="sxs-lookup"><span data-stu-id="92a6c-113">To create an explicit hierarchy</span></span>  
  
1.  <span data-ttu-id="92a6c-114">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="92a6c-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="92a6c-115">**[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[エンティティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="92a6c-115">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="92a6c-116">**[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="92a6c-116">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="92a6c-117">明示的階層を作成するエンティティの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="92a6c-117">Select the row for the entity that you want to create an explicit hierarchy for.</span></span>  
  
5.  <span data-ttu-id="92a6c-118">**[選択したエンティティの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="92a6c-118">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="92a6c-119">[**エンティティの編集**] ページの [**明示的階層**] ペインで、[**明示的階層の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="92a6c-119">On the **Edit Entity** page, in the **Explicit hierarchies** pane, click **Add explicit hierarchy**.</span></span>  
  
7.  <span data-ttu-id="92a6c-120">[**明示的階層の追加**] ページの [**明示的階層名**] ボックスに、階層の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="92a6c-120">On the **Add Explicit Hierarchy** page, in the **Explicit hierarchy name** box, type a name for the hierarchy.</span></span>  
  
8.  <span data-ttu-id="92a6c-121">必要に応じて、 **[必須階層]** チェック ボックスをオフにして、任意の階層として明示的階層を作成します。</span><span class="sxs-lookup"><span data-stu-id="92a6c-121">Optionally, clear the **Mandatory hierarchy** check box to create the hierarchy as a non-mandatory hierarchy.</span></span> <span data-ttu-id="92a6c-122">階層の種類の詳細については、「 [明示的階層 (マスター データ サービス)](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92a6c-122">For more information about hierarchy types, see [Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="92a6c-123">[**階層の保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="92a6c-123">Click **Save hierarchy**.</span></span>  
  
10. <span data-ttu-id="92a6c-124">[**エンティティの編集**] ページで、[**エンティティの保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="92a6c-124">On the **Edit Entity** page, click **Save entity**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="92a6c-125">次の手順</span><span class="sxs-lookup"><span data-stu-id="92a6c-125">Next Steps</span></span>  
  
-   [<span data-ttu-id="92a6c-126">統合メンバーを作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="92a6c-126">Create a Consolidated Member &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md)  
  
-   [<span data-ttu-id="92a6c-127">階層内のメンバーを移動する &#40;マスターデータサービス&#41;</span><span class="sxs-lookup"><span data-stu-id="92a6c-127">Move Members within a Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="92a6c-128">参照</span><span class="sxs-lookup"><span data-stu-id="92a6c-128">See Also</span></span>  
 <span data-ttu-id="92a6c-129">[明示的階層 &#40;マスターデータサービス&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="92a6c-129">[Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span></span>  
 <span data-ttu-id="92a6c-130">[明示的なキャップを持つ派生階層 &#40;マスターデータサービス&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="92a6c-130">[Derived Hierarchies with Explicit Caps &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md) </span></span>  
 [<span data-ttu-id="92a6c-131">明示的階層名を変更する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="92a6c-131">Change an Explicit Hierarchy Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)  
  
  
