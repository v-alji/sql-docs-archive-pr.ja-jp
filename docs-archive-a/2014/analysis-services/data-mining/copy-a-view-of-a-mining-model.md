---
title: マイニングモデルのビューをコピーする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clipboards [data mining]
- Mining Model Viewer [Analysis Services], clipboards
- copying mining models to clipboard
ms.assetid: 768372db-e5b4-4990-b459-03d854fd9a6d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 36d4d372bd235cd1cc0c043ff98151091e242269
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711166"
---
# <a name="copy-a-view-of-a-mining-model"></a><span data-ttu-id="3abcb-102">マイニング モデルの表示のコピー</span><span class="sxs-lookup"><span data-stu-id="3abcb-102">Copy a View of a Mining Model</span></span>
  <span data-ttu-id="3abcb-103">**のデータ マイニング デザイナーの** [マイニング モデル ビューアー] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] タブでは、マイニング モデルの種類ごとに異なるビューアーを使用します。</span><span class="sxs-lookup"><span data-stu-id="3abcb-103">The **Mining Model Viewer** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] uses a separate viewer for each type of mining model.</span></span> <span data-ttu-id="3abcb-104">これらのビューアーの一部には、コンテンツをクリップボードにコピーし、そこからドキュメントやイメージ操作ソフトウェアに貼り付けるためのコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="3abcb-104">Several of the viewers have components from which you can copy the contents to the Clipboard, and from there paste the contents into a document or into image manipulation software.</span></span> <span data-ttu-id="3abcb-105">この機能は次のコンポーネントで使用可能です。</span><span class="sxs-lookup"><span data-stu-id="3abcb-105">The following components make this functionality available:</span></span>  
  
-   <span data-ttu-id="3abcb-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスター ビューアーのクラスター ダイアグラムと [!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター ビューアー</span><span class="sxs-lookup"><span data-stu-id="3abcb-106">Cluster Diagram in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster Viewer</span></span>  
  
-   <span data-ttu-id="3abcb-107">[!INCLUDE[msCoName](../../includes/msconame-md.md)] ツリー ビューアーのデシジョン ツリーと [!INCLUDE[msCoName](../../includes/msconame-md.md)] タイム シリーズ ビューアー</span><span class="sxs-lookup"><span data-stu-id="3abcb-107">Decision Tree in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tree Viewer and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series Viewer</span></span>  
  
-   <span data-ttu-id="3abcb-108">[!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター ビューアーの状態遷移</span><span class="sxs-lookup"><span data-stu-id="3abcb-108">State Transitions in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster Viewer</span></span>  
  
-   <span data-ttu-id="3abcb-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション ルール ビューアーの依存関係ネットワーク、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes ビューアー、および [!INCLUDE[msCoName](../../includes/msconame-md.md)] ツリー ビューアー</span><span class="sxs-lookup"><span data-stu-id="3abcb-109">Dependency Network in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules Viewer, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer, and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tree Viewer</span></span>  
  
-   <span data-ttu-id="3abcb-110">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用コンテンツ ツリー ビューアーの [ノードの詳細] ペインにあるマイニング モデル コンテンツ</span><span class="sxs-lookup"><span data-stu-id="3abcb-110">Mining model content, from the Node Details pane of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree Viewer</span></span>  
  
 <span data-ttu-id="3abcb-111">マイニング モデル全体の表現をコピーすることも、ビューアーで表示している部分のみをコピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="3abcb-111">You can copy the complete representation of the mining model, or just the part that is visible in the viewer.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="3abcb-112">ビューアーを使用してモデルをコピーする場合、新しいモデル オブジェクトは作成されません。</span><span class="sxs-lookup"><span data-stu-id="3abcb-112">When you copy a model using the viewer, it does not create a new model object.</span></span> <span data-ttu-id="3abcb-113">新しいモデルを作成するには、ウィザードまたはデータ マイニング デザイナーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3abcb-113">To create a new model, you must use either the wizard, or the Data Mining Designer,.</span></span> <span data-ttu-id="3abcb-114">詳細については、「 [マイニング モデルのコピーの作成](make-a-copy-of-a-mining-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3abcb-114">For more information, see [Make a Copy of a Mining Model](make-a-copy-of-a-mining-model.md).</span></span>  
  
### <a name="to-copy-the-complete-model-to-the-clipboard"></a><span data-ttu-id="3abcb-115">モデル全体をクリップボードにコピーするには</span><span class="sxs-lookup"><span data-stu-id="3abcb-115">To copy the complete model to the Clipboard</span></span>  
  
1.  <span data-ttu-id="3abcb-116">**[マイニング モデル ビューアー]** タブの **[マイニング モデル]** リストで、表示するマイニング モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="3abcb-116">From the **Mining Model** list on the **Mining Model Viewer** tab, select the mining model that you want to view.</span></span>  
  
2.  <span data-ttu-id="3abcb-117">**[依存関係ネットワーク]** タブなど、適切なタブを選択してから、そのタブのツール バーで **[グラフ全体のコピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3abcb-117">Select the appropriate tab, such as the **Dependency Network** tab, and then click **Copy Entire Graph** on the toolbar of that tab.</span></span>  
  
### <a name="to-copy-the-visible-piece-of-the-model-to-the-clipboard"></a><span data-ttu-id="3abcb-118">モデルの表示部分のみをクリップボードにコピーするには</span><span class="sxs-lookup"><span data-stu-id="3abcb-118">To copy the visible piece of the model to the Clipboard</span></span>  
  
1.  <span data-ttu-id="3abcb-119">**[マイニング モデル ビューアー]** タブの **[マイニング モデル]** リストで、表示するマイニング モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="3abcb-119">From the **Mining Model** list on the **Mining Model Viewer** tab, select the mining model that you want to view.</span></span>  
  
2.  <span data-ttu-id="3abcb-120">**[依存関係ネットワーク]** タブなど、適切なタブを選択し、モデルを拡大または縮小して、希望のレベルで表示します。</span><span class="sxs-lookup"><span data-stu-id="3abcb-120">Select the appropriate tab, such as the **Dependency Network** tab, and then zoom in or out to view the model at the level that you want.</span></span>  
  
3.  <span data-ttu-id="3abcb-121">選択したタブのツール バーで **[グラフ ビューのコピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3abcb-121">Click **Copy Graph View** on the toolbar of the selected tab.</span></span>  
  
### <a name="to-copy-the-mining-model-content-to-the-clipboard"></a><span data-ttu-id="3abcb-122">マイニング モデル内容をクリップボードにコピーするには</span><span class="sxs-lookup"><span data-stu-id="3abcb-122">To copy the mining model content to the Clipboard</span></span>  
  
1.  <span data-ttu-id="3abcb-123">**[マイニング モデル ビューアー]** タブの **[マイニング モデル]** リストで、表示するマイニング モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="3abcb-123">From the **Mining Model** list on the **Mining Model Viewer** tab, select the mining model that you want to view.</span></span>  
  
2.  <span data-ttu-id="3abcb-124">**[ビューアー]** ボックスの一覧で **[Microsoft 汎用コンテンツ ツリー ビューアー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3abcb-124">From the **Viewer** drop-down list, select **Microsoft Generic Content Tree Viewer**.</span></span>  
  
3.  <span data-ttu-id="3abcb-125">**[ノードのキャプション (一意の ID)]** ペインでノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3abcb-125">In the **Node Caption (Unique ID)** pane, click a node.</span></span>  
  
4.  <span data-ttu-id="3abcb-126">**[ノードの詳細]** ペインを右クリックし、 **[すべて選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3abcb-126">Right-click the **Node Details** pane and then select **Select All**.</span></span>  
  
5.  <span data-ttu-id="3abcb-127">**[ノードの詳細]** ペインをもう一度右クリックし、 **[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3abcb-127">Right-click the **Node Details** pane again and select **Copy**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3abcb-128">参照</span><span class="sxs-lookup"><span data-stu-id="3abcb-128">See Also</span></span>  
 [<span data-ttu-id="3abcb-129">マイニング モデル ビューアーのタスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="3abcb-129">Mining Model Viewer Tasks and How-tos</span></span>](mining-model-viewer-tasks-and-how-tos.md)  
  
  
