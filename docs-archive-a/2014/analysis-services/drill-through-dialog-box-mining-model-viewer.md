---
title: '[ドリルスルー] ダイアログボックス (マイニングモデルビューアー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.drillthrough.f1
ms.assetid: 42b78399-143d-4f44-90e0-b545ffb79e10
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1b00c62017de5a26c4507a04aeaf59aba7522146
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644210"
---
# <a name="drill-through-dialog-box-mining-model-viewer"></a><span data-ttu-id="8b741-102">[ドリルスルー] ダイアログ ボックス (マイニング モデル ビューアー)</span><span class="sxs-lookup"><span data-stu-id="8b741-102">Drill Through Dialog Box (Mining Model Viewer)</span></span>
  <span data-ttu-id="8b741-103">データ マイニング デザイナーの **[マイニング モデル ビューアー]** タブを使用してマイニング モデルを表示する場合、モデルでドリルスルーが有効になっていれば、ケース データに関する詳細をドリルスルーできます。</span><span class="sxs-lookup"><span data-stu-id="8b741-103">When you view a mining model by using the **Mining Model Viewer** tab of Data Mining Designer, you can drill through into details about the case data, provided the model has drillthrough enabled.</span></span> <span data-ttu-id="8b741-104">さらに、基になるマイニング構造でドリルスルーが有効になっていれば、マイニング構造の列がマイニング モデルに含まれていない場合でも、それらの列を表示できます。</span><span class="sxs-lookup"><span data-stu-id="8b741-104">Moreover, if the underlying mining structure has drillthrough enabled, you can also see columns in the mining structure, even if those columns were not included in the mining model.</span></span> <span data-ttu-id="8b741-105">列リストでは、構造列に "Structure." というプレフィックスが付きます</span><span class="sxs-lookup"><span data-stu-id="8b741-105">In the column list, the structure columns are prefixed by the "Structure."</span></span> <span data-ttu-id="8b741-106">[ラベル]。</span><span class="sxs-lookup"><span data-stu-id="8b741-106">label.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8b741-107">既存のマイニング構造のドリルスルーを有効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="8b741-107">You cannot enable drillthrough on an existing mining structure.</span></span> <span data-ttu-id="8b741-108">代わりに、マイニング構造を再作成し、作成中にドリルスルーを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b741-108">Instead, you must re-create the mining structure and enable drillthrough during the creation process.</span></span>  
  
 <span data-ttu-id="8b741-109">ドリルスルーをサポートする各マイニングモデルビューアーからケースデータにアクセスする方法の詳細については、 **「** [マイニングモデルからのケースデータへのドリル](data-mining/drill-through-to-case-data-from-a-mining-model.md)スルー」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b741-109">For information about how to access case data from each of the mining model viewers that support drillthrough, **see** [Drill Through to Case Data from a Mining Model](data-mining/drill-through-to-case-data-from-a-mining-model.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8b741-110">Options</span><span class="sxs-lookup"><span data-stu-id="8b741-110">Options</span></span>  
 <span data-ttu-id="8b741-111">**[分類先のケース]**</span><span class="sxs-lookup"><span data-stu-id="8b741-111">**Cases Classified To**</span></span>  
 <span data-ttu-id="8b741-112">選択したノードに含まれるルール、アイテムセット、およびクラスターの定義を表示します。</span><span class="sxs-lookup"><span data-stu-id="8b741-112">Displays the definition of the rule, itemset, and cluster that are contained in the selected node.</span></span>  
  
 <span data-ttu-id="8b741-113">**[列リスト]**</span><span class="sxs-lookup"><span data-stu-id="8b741-113">**Column list**</span></span>  
 <span data-ttu-id="8b741-114">モデル内の列と、構造列を表示します。</span><span class="sxs-lookup"><span data-stu-id="8b741-114">Displays the columns in the model, followed by the structure columns.</span></span>  
  
 <span data-ttu-id="8b741-115">**注** 構造列は、マイニング構造でドリルスルーが有効であり、 **[モデルおよび構造列]** オプションを選択している場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="8b741-115">**Note** Structure columns are displayed only if drillthrough is enabled on the mining structure, and if you selected the option, **Model and Structure Columns**.</span></span> <span data-ttu-id="8b741-116">さらに、これらの列を表示するには、マイニング モデルとマイニング構造の両方に対するドリルスルー権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b741-116">Moreover, you must have drillthrough permissions on both the mining model and the mining structure to view the columns.</span></span>  
  
 <span data-ttu-id="8b741-117">モデルに含まれていない構造列は、\*\*構造体 \<column name> \*\*として表示されます。</span><span class="sxs-lookup"><span data-stu-id="8b741-117">Structure columns that are not included in the model appear as **Structure.\<column name>**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8b741-118">列グリッドの任意の部分を右クリックして **[すべてコピー]** を選択すると、ドリルスルー データをタブ区切り形式でクリップボードにコピーできます。</span><span class="sxs-lookup"><span data-stu-id="8b741-118">You can right-click anywhere in the column grid and select **Copy All** to copy the drillthrough data, in tab-delimited format, to the Clipboard.</span></span> <span data-ttu-id="8b741-119">コピーしたデータには、ケース データのみが含まれ、ノード定義は含まれません。</span><span class="sxs-lookup"><span data-stu-id="8b741-119">The copied data includes only the case data, not the node definition.</span></span>  
  
 <span data-ttu-id="8b741-120">**[再生]**</span><span class="sxs-lookup"><span data-stu-id="8b741-120">**Play**</span></span>  
 <span data-ttu-id="8b741-121">データを更新するには、緑色の矢印ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b741-121">Click the green arrow button to refresh the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b741-122">参照</span><span class="sxs-lookup"><span data-stu-id="8b741-122">See Also</span></span>  
 <span data-ttu-id="8b741-123">[データマイニング &#40;のドリルスルークエリ&#41;](data-mining/drillthrough-queries-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="8b741-123">[Drillthrough Queries &#40;Data Mining&#41;](data-mining/drillthrough-queries-data-mining.md) </span></span>  
 <span data-ttu-id="8b741-124">[データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="8b741-124">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="8b741-125">マイニング モデル ビューアーのタスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="8b741-125">Mining Model Viewer Tasks and How-tos</span></span>](data-mining/mining-model-viewer-tasks-and-how-tos.md)  
  
  
