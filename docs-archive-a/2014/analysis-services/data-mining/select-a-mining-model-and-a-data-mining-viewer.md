---
title: マイニングモデルとデータマイニングビューアーの選択 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Model Viewer [Analysis Services], types
ms.assetid: 3e5fb89d-3ab8-4d2e-9926-feeb38c02d3f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 152d0140f72300730375d5a6069f38f4efffc240
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639788"
---
# <a name="select-a-mining-model-and-a-data-mining-viewer"></a><span data-ttu-id="67263-102">マイニング モデルとデータ マイニング ビューアーの選択</span><span class="sxs-lookup"><span data-stu-id="67263-102">Select a Mining Model and a Data Mining Viewer</span></span>
  <span data-ttu-id="67263-103">マイニング モデルは、データ マイニング デザイナーの **[マイニング モデル ビューアー]** タブにあるいずれかのビューアーを使用して調べることができます。</span><span class="sxs-lookup"><span data-stu-id="67263-103">You can explore a mining model by using one of the viewers on the **Mining Model Viewer** tab of Data Mining Designer.</span></span> <span data-ttu-id="67263-104">簡単にモデルを切り替えることや使用するビューアーを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="67263-104">You can easily switch between models, or change the viewer that is used.</span></span>  
  
-   <span data-ttu-id="67263-105">**のデータ マイニング デザイナーの** [マイニング モデル ビューアー] **タブにある** [マイニング モデル] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ボックスには、現在のマイニング構造にあるマイニング モデルすべての一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="67263-105">The **Mining Model** drop-down list box on the **Mining Model Viewer** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] contains a list of all the mining models that are in the current mining structure.</span></span>  
  
-   <span data-ttu-id="67263-106">カスタム ビューアーはモデルの種類ごとに用意されています。</span><span class="sxs-lookup"><span data-stu-id="67263-106">Custom viewers are provided for each type of model.</span></span> <span data-ttu-id="67263-107">すべてのカスタム ビューアーの概要については、「[マイニング モデル ビューアー (データ マイニング モデル デザイナー)](../mining-model-viewers-data-mining-model-designer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67263-107">For an overview of all the custom viewers, see [Mining Model Viewers &#40;Data Mining Model Designer&#41;](../mining-model-viewers-data-mining-model-designer.md).</span></span> <span data-ttu-id="67263-108">カスタム ビューアーを使用してモデルについて理解する方法のチュートリアルについては、「[レッスン 4: 絞り込みメール配信モデルの検証 (基本的なデータ マイニング チュートリアル)](../../tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67263-108">For a walkthrough of how to use the custom viewers to understand a model, see [Lesson 4: Exploring the Targeted Mailing Models &#40;Basic Data Mining Tutorial&#41;](../../tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md).</span></span>  
  
-   <span data-ttu-id="67263-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用コンテンツ ビューアーでは、アルゴリズムで検出されたパターンの表示に、ノードをツリー状に表現する標準的な方法が使用されます。</span><span class="sxs-lookup"><span data-stu-id="67263-109">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Viewer shows the patterns discovered by the algorithm in a standard representation of nodes in a tree.</span></span> <span data-ttu-id="67263-110">汎用のツリー ビューにはモデルのすべての内容が詳細に表示されますが、解釈が難しくなります。</span><span class="sxs-lookup"><span data-stu-id="67263-110">Although the generic tree view shows all the content for the model in rich detail, it is more difficult to interpret.</span></span> <span data-ttu-id="67263-111">詳細については、「 [Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="67263-111">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span></span>  
  
### <a name="to-select-a-viewer-type"></a><span data-ttu-id="67263-112">ビューアーの種類を選択するには</span><span class="sxs-lookup"><span data-stu-id="67263-112">To select a viewer type</span></span>  
  
-   <span data-ttu-id="67263-113">作成した特定の種類のモデルに対して用意されているビューアーを選択するには、 **[マイニング モデル ビューアー]** タブの上部にある **[ビューアー]** ボックスの一覧を使用します。</span><span class="sxs-lookup"><span data-stu-id="67263-113">Select the viewer that is provided for the specific type of model that you created, using the **Viewer** list at the top of the **Mining Model Viewer** tab.</span></span>  
  
-   <span data-ttu-id="67263-114">または、 **[Microsoft 汎用マイニング コンテンツ ビューアー]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="67263-114">Or, use the **Microsoft Generic Mining Content Viewer**</span></span>  
  
### <a name="to-select-a-mining-model-to-view"></a><span data-ttu-id="67263-115">表示するマイニング モデルを選択するには</span><span class="sxs-lookup"><span data-stu-id="67263-115">To select a mining model to view</span></span>  
  
-   <span data-ttu-id="67263-116">データ マイニング デザイナーの **[マイニング モデル ビューアー]** タブで、表示するマイニング モデルを **[マイニング モデル]** ボックスの一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="67263-116">On the **Mining Model Viewer** tab in Data Mining Designer, select the mining model that you want to view from the **Mining Model** list.</span></span>  
  
 <span data-ttu-id="67263-117">選択したマイニング モデルが、そのモデルの種類に対して用意されているビューアーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="67263-117">The selected mining model opens in the viewer that is provided for that model type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67263-118">参照</span><span class="sxs-lookup"><span data-stu-id="67263-118">See Also</span></span>  
 [<span data-ttu-id="67263-119">マイニング モデル ビューアーのタスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="67263-119">Mining Model Viewer Tasks and How-tos</span></span>](mining-model-viewer-tasks-and-how-tos.md)  
  
  
