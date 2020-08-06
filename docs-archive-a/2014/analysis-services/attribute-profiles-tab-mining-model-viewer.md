---
title: '[属性のプロファイル] タブ (マイニングモデルビューアー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.profiles.f1
ms.assetid: 17c7e7ae-273c-4a6b-9a35-e8b9b8e65999
author: minewiskan
ms.author: owend
ms.openlocfilehash: 61c81b95f030bf1a69aed165bd64e58ff9af8339
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633624"
---
# <a name="attribute-profiles-tab-mining-model-viewer"></a><span data-ttu-id="a03b2-102">[属性のプロファイル] タブ (マイニング モデル ビューアー)</span><span class="sxs-lookup"><span data-stu-id="a03b2-102">Attribute Profiles Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="a03b2-103">Naive Bayes モデルにおける入力値の分布と、結果の属性の状態との関係を確認するには、 **[属性のプロファイル]** タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-103">Use the **Attribute Profiles** tab to see how the distribution of input values in a Naive Bayes model state contribute to each state of the outcome attribute.</span></span> <span data-ttu-id="a03b2-104">値の分布はカラー ヒストグラムで表示され、すべての分布は値を簡単に比較できるように表形式で提示されます。</span><span class="sxs-lookup"><span data-stu-id="a03b2-104">The distribution of values is shown as a colored histogram, all distributions presented in a tabular format, to make it easier to compare values.</span></span>  
  
 <span data-ttu-id="a03b2-105">**詳細:** [Microsoft Naive Bayes アルゴリズム](data-mining/microsoft-naive-bayes-algorithm.md)、 [Microsoft Naive Bayes ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="a03b2-105">**For More Information:** [Microsoft Naive Bayes Algorithm](data-mining/microsoft-naive-bayes-algorithm.md), [Browse a Model Using the Microsoft Naive Bayes Viewer](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="a03b2-106">Options</span><span class="sxs-lookup"><span data-stu-id="a03b2-106">Options</span></span>  
 <span data-ttu-id="a03b2-107">**[ビューアーのコンテンツを最新状態に更新]**</span><span class="sxs-lookup"><span data-stu-id="a03b2-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="a03b2-108">ビューアーにマイニング モデルを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="a03b2-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="a03b2-109">**[マイニング モデル]**</span><span class="sxs-lookup"><span data-stu-id="a03b2-109">**Mining Model**</span></span>  
 <span data-ttu-id="a03b2-110">現在のマイニング構造に含まれているマイニング モデルから、表示するものを選択します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-110">Choose a mining model to view, from those in the current mining structure.</span></span> <span data-ttu-id="a03b2-111">関連付けられているビューアーが開き、マイニング モデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a03b2-111">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="a03b2-112">**Viewer**</span><span class="sxs-lookup"><span data-stu-id="a03b2-112">**Viewer**</span></span>  
 <span data-ttu-id="a03b2-113">選択したマイニング モデルを調べるために使用するビューアーを選択します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-113">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="a03b2-114">各マイニング モデル用に用意されているカスタム ビューアー、または [!INCLUDE[msCoName](../includes/msconame-md.md)] マイニング コンテンツ ビューアーを選択できます。</span><span class="sxs-lookup"><span data-stu-id="a03b2-114">You can choose the custom viewer provided for each mining model, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="a03b2-115">可能な場合プラグイン ビューアーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a03b2-115">You can also use plug-in viewers if they are available.</span></span>  
  
 <span data-ttu-id="a03b2-116">**[凡例の表示]**</span><span class="sxs-lookup"><span data-stu-id="a03b2-116">**Show Legend**</span></span>  
 <span data-ttu-id="a03b2-117">**[状態]** 列の値と分布図で使用される色の対応を示すキーを表示するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-117">Select this option to display a key that matches each value in **States** to one of the colors used in the distribution chart.</span></span>  
  
 <span data-ttu-id="a03b2-118">**ヒストグラムバー**</span><span class="sxs-lookup"><span data-stu-id="a03b2-118">**Histogram bars**</span></span>  
 <span data-ttu-id="a03b2-119">ヒストグラムに含めるバーの数を選択します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-119">Select how many bars to include in the histogram.</span></span> <span data-ttu-id="a03b2-120">選択したバーの数よりも多くのバーが存在する場合、重要度が最も高いバーが保持され、それ以外のバーは **[その他]** にまとめられます。</span><span class="sxs-lookup"><span data-stu-id="a03b2-120">If more bars exist than you choose to display, the bars of highest importance are retained, and the remaining bars are grouped together into **Other**.</span></span>  
  
 <span data-ttu-id="a03b2-121">**[予測可能]**</span><span class="sxs-lookup"><span data-stu-id="a03b2-121">**Predictable**</span></span>  
 <span data-ttu-id="a03b2-122">マイニング モデルの予測可能な列を選択します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-122">Select a predictable column from the mining model.</span></span>  
  
 <span data-ttu-id="a03b2-123">**属性のプロファイル**</span><span class="sxs-lookup"><span data-stu-id="a03b2-123">**Attribute Profiles**</span></span>  
 <span data-ttu-id="a03b2-124">表には次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a03b2-124">The table contains the following columns:</span></span>  
  
|<span data-ttu-id="a03b2-125">値</span><span class="sxs-lookup"><span data-stu-id="a03b2-125">Value</span></span>|<span data-ttu-id="a03b2-126">説明</span><span class="sxs-lookup"><span data-stu-id="a03b2-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a03b2-127">**属性**</span><span class="sxs-lookup"><span data-stu-id="a03b2-127">**Attributes**</span></span>|<span data-ttu-id="a03b2-128">マイニング モデルに含まれているマイニング モデル列が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="a03b2-128">Lists the mining model columns contained within the mining model.</span></span>|  
|<span data-ttu-id="a03b2-129">**状態**</span><span class="sxs-lookup"><span data-stu-id="a03b2-129">**States**</span></span>|<span data-ttu-id="a03b2-130">対応する属性の行の色が表す状態を説明するオプションの列です。</span><span class="sxs-lookup"><span data-stu-id="a03b2-130">An optional column that describes what state the color in the corresponding row of attributes represents.</span></span> <span data-ttu-id="a03b2-131">追加または削除するには、 **[凡例の表示]** チェック ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-131">Add or remove by using the **Show Legend** check box.</span></span>|  
|<span data-ttu-id="a03b2-132">**作成**</span><span class="sxs-lookup"><span data-stu-id="a03b2-132">**Population**</span></span>|<span data-ttu-id="a03b2-133">データセット全体における属性の分布が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a03b2-133">Displays the distribution of the attribute across the whole dataset.</span></span>|  
|<span data-ttu-id="a03b2-134">**予測可能な属性状態の列**</span><span class="sxs-lookup"><span data-stu-id="a03b2-134">**Column for states of predictable attribute**</span></span>|<span data-ttu-id="a03b2-135">予測可能な列の各状態を表す列が表示されます。各行が、モデル内の入力属性に対応しています。</span><span class="sxs-lookup"><span data-stu-id="a03b2-135">Displays a column for each state of the predictable column, with each row corresponding to an input attribute in the model.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a03b2-136">参照</span><span class="sxs-lookup"><span data-stu-id="a03b2-136">See Also</span></span>  
 <span data-ttu-id="a03b2-137">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="a03b2-137">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="a03b2-138">[データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="a03b2-138">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="a03b2-139">データ マイニング モデル ビューアー</span><span class="sxs-lookup"><span data-stu-id="a03b2-139">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
