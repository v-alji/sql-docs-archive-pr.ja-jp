---
title: マイニングモデルからケースデータへのドリルスルー |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- drillthrough [Analysis Services]
ms.assetid: b4d3f350-e543-4ea9-b3a2-b4f7c0a9ae27
author: minewiskan
ms.author: owend
ms.openlocfilehash: 74129c44fc92984a767a79c579a495084ae68754
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644224"
---
# <a name="drill-through-to-case-data-from-a-mining-model"></a><span data-ttu-id="80c6c-102">マイニング モデルからケース データへのドリルスルー</span><span class="sxs-lookup"><span data-stu-id="80c6c-102">Drill Through to Case Data from a Mining Model</span></span>
  <span data-ttu-id="80c6c-103">モデル ケースへのドリルスルーを許可するようにマイニング モデルが構成されている場合は、モデルの参照時に、モデルの作成に使用されたケースに関する詳細情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="80c6c-103">If a mining model has been configured to let you drill through to model cases, when you browse the model, you can retrieve detailed information about the cases that were used to create the model.</span></span> <span data-ttu-id="80c6c-104">さらに、基になるマイニング構造が、構造ケースへのドリルスルーを許可するように構成されており、ユーザーが適切な権限を持っている場合は、マイニング構造から情報を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="80c6c-104">Moreover, if the underlying mining structure has been configured to allow drillthrough to structure cases, and you have the appropriate permissions, you can return information from the mining structure.</span></span> <span data-ttu-id="80c6c-105">これには、マイニング モデルに含まれていない列を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="80c6c-105">This can include columns that were not included in the mining model.</span></span>  
  
 <span data-ttu-id="80c6c-106">基になるデータへのドリルスルーがマイニング構造で許可されておらず、マイニング モデルでは許可されている場合、モデル ケースの情報は表示できますが、マイニング構造の情報は表示できません。</span><span class="sxs-lookup"><span data-stu-id="80c6c-106">If the mining structure does not allow you to drill through to the underlying data, but the mining model does, you can view information from the model cases, but not from the mining structure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="80c6c-107">`AllowDrillthrough` プロパティを `True` に設定することで、既存のマイニング モデルにドリルスルー機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="80c6c-107">You can add the ability to drillthrough on an existing mining model by setting the property `AllowDrillthrough` to `True`.</span></span> <span data-ttu-id="80c6c-108">ただし、ドリルスルーを有効にした後、ケース データを表示する前にモデルを再処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80c6c-108">However, after you enable drillthrough, the model must be reprocessed before you can see the case data.</span></span> <span data-ttu-id="80c6c-109">詳細については、「 [Enable Drillthrough for a Mining Model](enable-drillthrough-for-a-mining-model.md)」(マイニング モデルのドリルスルーの有効化) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80c6c-109">For more information, see [Enable Drillthrough for a Mining Model](enable-drillthrough-for-a-mining-model.md).</span></span>  
  
 <span data-ttu-id="80c6c-110">使用するビューアーの種類に応じて、次に示す方法で、ドリルスルーするノードを選択できます。</span><span class="sxs-lookup"><span data-stu-id="80c6c-110">Depending on the type of viewer you are using, you can select the node for drillthrough in the following ways:</span></span>  
  
|<span data-ttu-id="80c6c-111">ビューアー名</span><span class="sxs-lookup"><span data-stu-id="80c6c-111">Viewer name</span></span>|<span data-ttu-id="80c6c-112">ペイン名またはタブ名</span><span class="sxs-lookup"><span data-stu-id="80c6c-112">Pane or tab name</span></span>|<span data-ttu-id="80c6c-113">選択するノード</span><span class="sxs-lookup"><span data-stu-id="80c6c-113">Select node</span></span>|  
|-----------------|----------------------|-----------------|  
|<span data-ttu-id="80c6c-114">**Microsoft ツリー ビューアー**</span><span class="sxs-lookup"><span data-stu-id="80c6c-114">**Microsoft Tree Viewer**</span></span>|<span data-ttu-id="80c6c-115">[**デシジョンツリー** ] タブ</span><span class="sxs-lookup"><span data-stu-id="80c6c-115">**Decision Tree** tab</span></span>|<span data-ttu-id="80c6c-116">ツリー ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="80c6c-116">Click a tree node.</span></span><br /><br /> <span data-ttu-id="80c6c-117">**メモ**ノードではドリルスルーを使用しないで `All` ください。結果が返されるまでに非常に長い時間がかかる場合があるためです。</span><span class="sxs-lookup"><span data-stu-id="80c6c-117">**Note** Avoid using drillthrough on the `All` node, because it may take a very long time to return results.</span></span>|  
|<span data-ttu-id="80c6c-118">**Microsoft クラスター ビューアー**</span><span class="sxs-lookup"><span data-stu-id="80c6c-118">**Microsoft Cluster Viewer**</span></span>|<span data-ttu-id="80c6c-119">**クラスター ダイアグラム**</span><span class="sxs-lookup"><span data-stu-id="80c6c-119">**Cluster Diagram**</span></span>|<span data-ttu-id="80c6c-120">クラスター ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="80c6c-120">Click a cluster node.</span></span>|  
|<span data-ttu-id="80c6c-121">**Microsoft クラスター ビューアー**</span><span class="sxs-lookup"><span data-stu-id="80c6c-121">**Microsoft Cluster Viewer**</span></span>|<span data-ttu-id="80c6c-122">**クラスターのプロファイル**</span><span class="sxs-lookup"><span data-stu-id="80c6c-122">**Cluster Profiles**</span></span>|<span data-ttu-id="80c6c-123">クラスター列内の任意の場所をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80c6c-123">Click anywhere in cluster column.</span></span>|  
|<span data-ttu-id="80c6c-124">**Microsoft アソシエーション ビューアー**</span><span class="sxs-lookup"><span data-stu-id="80c6c-124">**Microsoft Association Viewer**</span></span>|<span data-ttu-id="80c6c-125">[**規則**] タブ</span><span class="sxs-lookup"><span data-stu-id="80c6c-125">**Rules** tab</span></span>|<span data-ttu-id="80c6c-126">一連のルールを含む行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80c6c-126">Click a row that contains a set of rules.</span></span>|  
|<span data-ttu-id="80c6c-127">**Microsoft アソシエーション ビューアー**</span><span class="sxs-lookup"><span data-stu-id="80c6c-127">**Microsoft Association Viewer**</span></span>|<span data-ttu-id="80c6c-128">**[アイテムセット]** タブ</span><span class="sxs-lookup"><span data-stu-id="80c6c-128">**Itemsets** tab</span></span>|<span data-ttu-id="80c6c-129">アイテムセットを含む行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80c6c-129">Click a row that contains an itemset.</span></span>|  
|<span data-ttu-id="80c6c-130">**Microsoft シーケンス クラスター ビューアー**</span><span class="sxs-lookup"><span data-stu-id="80c6c-130">**Microsoft Sequence Clustering Viewer**</span></span>|<span data-ttu-id="80c6c-131">[**規則**] タブ</span><span class="sxs-lookup"><span data-stu-id="80c6c-131">**Rules** tab</span></span>|<span data-ttu-id="80c6c-132">一連のルールを含む行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80c6c-132">Click a row that contains a set of rules.</span></span>|  
|<span data-ttu-id="80c6c-133">**Microsoft シーケンス クラスター ビューアー**</span><span class="sxs-lookup"><span data-stu-id="80c6c-133">**Microsoft Sequence Clustering Viewer**</span></span>|<span data-ttu-id="80c6c-134">**[アイテムセット]** タブ</span><span class="sxs-lookup"><span data-stu-id="80c6c-134">**Itemsets** tab</span></span>|<span data-ttu-id="80c6c-135">アイテムセットを含む行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80c6c-135">Click a row that contains an itemset.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="80c6c-136">ドリルスルーを使用できないモデルもあります。</span><span class="sxs-lookup"><span data-stu-id="80c6c-136">Some models cannot use drillthrough.</span></span> <span data-ttu-id="80c6c-137">ドリルスルーを使用できるかどうかは、モデルの作成に使用したアルゴリズムによって異なります。</span><span class="sxs-lookup"><span data-stu-id="80c6c-137">The ability to use drillthrough depends on the algorithm that was used to create the model.</span></span> <span data-ttu-id="80c6c-138">ドリルスルーをサポートするマイニング モデルの種類の一覧については、「 [ドリルスルー クエリ &#40;データ マイニング&#41;](drillthrough-queries-data-mining.md)に設定することで、既存のマイニング モデルにドリルスルー機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="80c6c-138">For a list of the mining model types that support drillthrough, see [Drillthrough Queries &#40;Data Mining&#41;](drillthrough-queries-data-mining.md).</span></span>  
  
### <a name="to-view-drillthrough-data-from-a-mining-model"></a><span data-ttu-id="80c6c-139">マイニング モデルからのドリルスルー データを表示するには</span><span class="sxs-lookup"><span data-stu-id="80c6c-139">To view drillthrough data from a mining model</span></span>  
  
1.  <span data-ttu-id="80c6c-140">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のマイニング モデルを含むマイニング構造を開きます。</span><span class="sxs-lookup"><span data-stu-id="80c6c-140">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the mining structure that contains the mining model you want.</span></span>  
  
2.  <span data-ttu-id="80c6c-141">データ マイニング デザイナーで、 **[マイニング モデル ビューアー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="80c6c-141">In Data Mining Designer, click the **Mining Model Viewer** tab.</span></span>  
  
3.  <span data-ttu-id="80c6c-142">**[マイニング モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="80c6c-142">Select the model from the **Mining Model** drop-down list.</span></span>  
  
4.  <span data-ttu-id="80c6c-143">**[ビューアー]** ボックスの一覧からビューアーを選択し、特定のノードを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="80c6c-143">Select a viewer from the **Viewer** drop-down list, and right-click the specific node.</span></span>  
  
5.  <span data-ttu-id="80c6c-144">**[ドリルスルー]** を選択してから、 **[モデル列のみ]** または **[モデル列および構造列]** を選択します。 **[ドリルスルー]** ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="80c6c-144">Select **Drill Through**, and then select either **Models Columns Only**, or **Model and Structure Columns** to open the **Drill Through** window.</span></span>  
  
6.  <span data-ttu-id="80c6c-145">データをクリップボードにコピーするには、テーブル内の任意の行を右クリックして **[すべてコピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80c6c-145">To copy the data to the Clipboard, right-click any row in the table, and select **Copy All**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80c6c-146">参照</span><span class="sxs-lookup"><span data-stu-id="80c6c-146">See Also</span></span>  
 [<span data-ttu-id="80c6c-147">ドリルスルー クエリ (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="80c6c-147">Drillthrough Queries &#40;Data Mining&#41;</span></span>](drillthrough-queries-data-mining.md)  
  
  
