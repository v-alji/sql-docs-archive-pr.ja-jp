---
title: テストと検証のタスクと操作方法 (データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Accuracy Chart [Analysis Services]
- predictive modeling [Analysis Services]
- mining structures [Analysis Services], predictive modeling
- Mining Accuracy Chart [Analysis Services], how-to topics
- mining models [Analysis Services], predictive modeling
- predictive accuracy [data mining]
ms.assetid: 3a0b4dc9-5b64-4be1-aa5f-6ff26f43dbf8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 10844a7d39e49ab595eb25bb56ed3f4f5d415565
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644699"
---
# <a name="testing-and-validation-tasks-and-how-tos-data-mining"></a><span data-ttu-id="99735-102">テスト、検証タスク、および操作方法 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="99735-102">Testing and Validation Tasks and How-tos (Data Mining)</span></span>
  <span data-ttu-id="99735-103">**のデータ マイニング デザイナーの** [マイニング精度チャート] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] タブを使用すると、マイニング構造内のマイニング モデルの予測精度を比較できます。</span><span class="sxs-lookup"><span data-stu-id="99735-103">You can use the **Mining Accuracy Chart** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to compare the predictive accuracy of the mining models in your mining structure.</span></span>  
  
 <span data-ttu-id="99735-104">次の 4 種類のグラフを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="99735-104">You can create four kinds of charts:</span></span>  
  
-   <span data-ttu-id="99735-105">リフト チャート</span><span class="sxs-lookup"><span data-stu-id="99735-105">Lift chart</span></span>  
  
-   <span data-ttu-id="99735-106">利益チャート</span><span class="sxs-lookup"><span data-stu-id="99735-106">Profit chart</span></span>  
  
-   <span data-ttu-id="99735-107">分類マトリックス</span><span class="sxs-lookup"><span data-stu-id="99735-107">Classification matrix</span></span>  
  
-   <span data-ttu-id="99735-108">クロス検証レポート</span><span class="sxs-lookup"><span data-stu-id="99735-108">Cross-validation report</span></span>  
  
 <span data-ttu-id="99735-109">最初の 3 つのグラフでは、 **[入力の選択]** タブを使用して、グラフの生成に使用するデータを定義します。</span><span class="sxs-lookup"><span data-stu-id="99735-109">The first three charts use the **Input Selection** tab to define the data that is used for generating the chart.</span></span>  
  
 <span data-ttu-id="99735-110">クロス検証グラフは、[**クロス検証**] タブで使用できる追加の入力を使用して作成されます。詳細については、「[相互検証 &#40;Analysis Services データマイニング&#41;](cross-validation-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99735-110">The Cross-validation chart is created by using additional inputs, available on the **Cross-Validation** tab. For more information, see [Cross-Validation &#40;Analysis Services - Data Mining&#41;](cross-validation-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="99735-111">マイニング精度チャートの使用方法の詳細については、「[テストおよび検証 (データ マイニング)](testing-and-validation-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99735-111">For more information about how to use the mining accuracy chart, see [Testing and Validation &#40;Data Mining&#41;](testing-and-validation-data-mining.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="99735-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="99735-112">In This Section</span></span>  
  
-   [<span data-ttu-id="99735-113">リフト チャート、利益チャート、または分類マトリックスの作成</span><span class="sxs-lookup"><span data-stu-id="99735-113">Create a Lift Chart, Profit Chart, or Classification Matrix</span></span>](create-a-lift-chart-profit-chart-or-classification-matrix.md)  
  
-   [<span data-ttu-id="99735-114">クロス検証レポートの作成</span><span class="sxs-lookup"><span data-stu-id="99735-114">Create a Cross-Validation Report</span></span>](create-a-cross-validation-report.md)  
  
-   [<span data-ttu-id="99735-115">モデルのテスト データの選択およびマップ</span><span class="sxs-lookup"><span data-stu-id="99735-115">Choose and Map Model Testing Data</span></span>](choose-and-map-model-testing-data.md)  
  
-   [<span data-ttu-id="99735-116">モデルのテスト データへのフィルターの適用</span><span class="sxs-lookup"><span data-stu-id="99735-116">Apply Filters to Model Testing Data</span></span>](apply-filters-to-model-testing-data.md)  
  
-   [<span data-ttu-id="99735-117">マイニング モデルのテストに使用する列の選択</span><span class="sxs-lookup"><span data-stu-id="99735-117">Choose the Column to Use for Testing a Mining Model</span></span>](choose-the-column-to-use-for-testing-a-mining-model.md)  
  
-   [<span data-ttu-id="99735-118">入れ子になったテーブルのデータを精度チャートの入力として使用する方法</span><span class="sxs-lookup"><span data-stu-id="99735-118">Using Nested Table Data as an Input for an Accuracy Chart</span></span>](using-nested-table-data-as-an-input-for-an-accuracy-chart.md)  
  
  
