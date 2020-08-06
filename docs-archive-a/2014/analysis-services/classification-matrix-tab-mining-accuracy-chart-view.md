---
title: '[分類マトリックス] タブ ([マイニング精度チャート] ビュー)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.confusionmatrix.f1
ms.assetid: 85d5a047-d656-41e0-8a31-400271c2a620
author: minewiskan
ms.author: owend
ms.openlocfilehash: d202d552b25095d0d0845ff64f9c0e289f7bba0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633531"
---
# <a name="classification-matrix-tab-mining-accuracy-chart-view"></a><span data-ttu-id="afa78-102">[分類マトリックス] タブ ([マイニング精度チャート] ビュー)</span><span class="sxs-lookup"><span data-stu-id="afa78-102">Classification Matrix Tab (Mining Accuracy Chart View)</span></span>
  <span data-ttu-id="afa78-103">[**分類マトリックス**] タブには、[**列マッピング**] タブの [モデル] グリッドで選択した各モデルの分類マトリックスが表示されます。分類マトリックスは、[**列マッピング**] タブで選択された予測可能列が連続していない場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="afa78-103">The **Classification Matrix** tab displays a classification matrix for each model selected in the models grid on the **Column Mapping** tab. The classification matrix is only available if the predictable column that is selected in the **Column Mapping** tab is not continuous.</span></span> <span data-ttu-id="afa78-104">[**分類マトリックス**] タブの詳細については、「[データマイニング&#41;のテストおよび検証 &#40;](data-mining/testing-and-validation-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afa78-104">For a more detailed description of the **Classification Matrix** tab, see [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="afa78-105">Options</span><span class="sxs-lookup"><span data-stu-id="afa78-105">Options</span></span>  
 <span data-ttu-id="afa78-106">**コピー**</span><span class="sxs-lookup"><span data-stu-id="afa78-106">**Copy**</span></span>  
 <span data-ttu-id="afa78-107">各分類マトリックスの内容をクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="afa78-107">Copies the content of each classification matrix to the clipboard.</span></span>  
  
 <span data-ttu-id="afa78-108">**\<model>のカウント\< predictable column>**</span><span class="sxs-lookup"><span data-stu-id="afa78-108">**Counts for \<model> on \< predictable column>**</span></span>  
 <span data-ttu-id="afa78-109">マイニング構造内の各マイニング モデルの分類マトリックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="afa78-109">Displays a classification matrix for each mining model in the mining structure.</span></span> <span data-ttu-id="afa78-110">このマトリックスには次の列があります。</span><span class="sxs-lookup"><span data-stu-id="afa78-110">The matrix contains the following columns:</span></span>  
  
|<span data-ttu-id="afa78-111">値</span><span class="sxs-lookup"><span data-stu-id="afa78-111">Value</span></span>|<span data-ttu-id="afa78-112">説明</span><span class="sxs-lookup"><span data-stu-id="afa78-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="afa78-113">**[予測]**</span><span class="sxs-lookup"><span data-stu-id="afa78-113">**Predicted**</span></span>|<span data-ttu-id="afa78-114">予測可能列の各状態の行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="afa78-114">Contains a row for each state of the predictable column.</span></span>|  
|<span data-ttu-id="afa78-115">**\<states>100**</span><span class="sxs-lookup"><span data-stu-id="afa78-115">**\<states> (actual)**</span></span>|<span data-ttu-id="afa78-116">予測可能列の各状態の列です。</span><span class="sxs-lookup"><span data-stu-id="afa78-116">A column for each state in the predictable column.</span></span> <span data-ttu-id="afa78-117">行と列の状態が対応している場合、セルには、データベース内に状態が存在する実際の回数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="afa78-117">If the state of the row and the column correspond, the cell represents the actual number of times the state exists in the database.</span></span> <span data-ttu-id="afa78-118">対応しない場合、セルには予測のエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="afa78-118">If they do not correspond, the cell represents the error of the prediction.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="afa78-119">参照</span><span class="sxs-lookup"><span data-stu-id="afa78-119">See Also</span></span>  
 <span data-ttu-id="afa78-120">[マイニング精度チャートデザイナー &#40;データマイニング&#41;](mining-accuracy-chart-designer-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="afa78-120">[Mining Accuracy Chart Designer &#40;Data Mining&#41;](mining-accuracy-chart-designer-data-mining.md) </span></span>  
 <span data-ttu-id="afa78-121">[テストと検証のタスクと操作方法 &#40;データマイニング&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="afa78-121">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 [<span data-ttu-id="afa78-122">テストおよび検証 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="afa78-122">Testing and Validation &#40;Data Mining&#41;</span></span>](data-mining/testing-and-validation-data-mining.md)  
  
  
