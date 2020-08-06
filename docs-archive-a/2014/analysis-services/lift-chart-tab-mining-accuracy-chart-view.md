---
title: '[リフトチャート] タブ ([マイニング精度チャート] ビュー)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.liftchart.f1
ms.assetid: f1674e2e-d38e-40c7-b8d1-5585ce9a0168
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7cdad01ff3549140bf4fed606b1e8f9eaed10dac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743577"
---
# <a name="lift-chart-tab-mining-accuracy-chart-view"></a><span data-ttu-id="becd6-102">[リフト チャート] タブ ([マイニング精度チャート] ビュー)</span><span class="sxs-lookup"><span data-stu-id="becd6-102">Lift Chart Tab (Mining Accuracy Chart View)</span></span>
  <span data-ttu-id="becd6-103">**[リフト チャート]** ペインを使用すると、選択されたマイニング構造に含まれている、選択されたすべてのマイニング モデルを比較するグラフを表示できます。</span><span class="sxs-lookup"><span data-stu-id="becd6-103">Use the **Lift Chart** pane to view a chart that compares all the selected mining models in the selected mining structure.</span></span>  
  
 <span data-ttu-id="becd6-104">不連続属性を予測するモデルの場合、リフト チャートまたは利益チャートを表示できます。</span><span class="sxs-lookup"><span data-stu-id="becd6-104">If the model predicts a discrete attribute, the pane can display either a lift chart or a profit chart.</span></span> <span data-ttu-id="becd6-105">リフト チャートの詳細については、「[リフト チャート &#40;Analysis Services - データ マイニング&#41;](data-mining/lift-chart-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="becd6-105">For information about lift charts, see [Lift Chart &#40;Analysis Services - Data Mining&#41;](data-mining/lift-chart-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="becd6-106">利益チャートを作成するには、予測される利益に加えて、マイニング モデルの推奨事項を実装するコストに関する追加情報を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="becd6-106">To create a profit chart, you must provide additional information about the cost of implementing the recommendations of the mining model, as well as the expected return.</span></span> <span data-ttu-id="becd6-107">詳細については、「[利益チャート (Analysis Services - データ マイニング)](data-mining/profit-chart-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="becd6-107">For more information, see [Profit Chart &#40;Analysis Services - Data Mining&#41;](data-mining/profit-chart-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="becd6-108">連続属性を予測するモデルの場合、散布図グラフが表示されます。</span><span class="sxs-lookup"><span data-stu-id="becd6-108">If the model predicts a continuous attribute, the pane will display a scatter plot graph.</span></span>  
  
 <span data-ttu-id="becd6-109">マイニング モデルの精度の測定方法に関する一般的な情報については、「[リフト チャート &#40;Analysis Services - データ マイニング&#41;](data-mining/lift-chart-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="becd6-109">For general information about methods of measuring the accuracy of a mining model, see [Lift Chart &#40;Analysis Services - Data Mining&#41;](data-mining/lift-chart-analysis-services-data-mining.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="becd6-110">Options</span><span class="sxs-lookup"><span data-stu-id="becd6-110">Options</span></span>  
 <span data-ttu-id="becd6-111">**[グラフの種類]**</span><span class="sxs-lookup"><span data-stu-id="becd6-111">**Chart Type**</span></span>  
 <span data-ttu-id="becd6-112">ビューアーに表示するグラフの種類を設定します。</span><span class="sxs-lookup"><span data-stu-id="becd6-112">Sets the type of chart to display in the viewer.</span></span> <span data-ttu-id="becd6-113">**[リフト チャート]** または **[利益チャート]** のいずれかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="becd6-113">You can select either **Lift Chart** or **Profit Chart**.</span></span>  
  
 <span data-ttu-id="becd6-114">**設定**</span><span class="sxs-lookup"><span data-stu-id="becd6-114">**Settings**</span></span>  
 <span data-ttu-id="becd6-115">利益チャートの構成に使用できる **[利益チャートの設定]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="becd6-115">Opens the **Profit Chart Settings** dialog box, which you can use to configure a profit chart.</span></span>  
  
 <span data-ttu-id="becd6-116">利益チャートは、 **[列マッピング]** タブで連続した予測可能列が選択されている場合は、使用できません。</span><span class="sxs-lookup"><span data-stu-id="becd6-116">The profit chart is not available if a continuous predictable column was selected in the **Column Mapping** tab.</span></span>  
  
 <span data-ttu-id="becd6-117">**コピー**</span><span class="sxs-lookup"><span data-stu-id="becd6-117">**Copy**</span></span>  
 <span data-ttu-id="becd6-118">グラフをクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="becd6-118">Copies the chart to the Clipboard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="becd6-119">参照</span><span class="sxs-lookup"><span data-stu-id="becd6-119">See Also</span></span>  
 <span data-ttu-id="becd6-120">[マイニング精度チャートデザイナー &#40;データマイニング&#41;](mining-accuracy-chart-designer-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="becd6-120">[Mining Accuracy Chart Designer &#40;Data Mining&#41;](mining-accuracy-chart-designer-data-mining.md) </span></span>  
 <span data-ttu-id="becd6-121">[テストと検証のタスクと操作方法 &#40;データマイニング&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="becd6-121">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 [<span data-ttu-id="becd6-122">テストおよび検証 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="becd6-122">Testing and Validation &#40;Data Mining&#41;</span></span>](data-mining/testing-and-validation-data-mining.md)  
  
  
