---
title: データ マイニング モデル トレーニング変換先 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingmodeltrainingdest.f1
helpviewer_keywords:
- destinations [Integration Services], Data Mining Model Training
- Data Mining Model Training destination
- mining models [Analysis Services], training
- training mining models
ms.assetid: 6bc8cbe2-46af-4f7b-93d6-86779313c9d7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e101a7e374f16b12b3a5aa30a49dbecd2632f06f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641793"
---
# <a name="data-mining-model-training-destination"></a><span data-ttu-id="a257a-102">データ マイニング モデル トレーニング変換先</span><span class="sxs-lookup"><span data-stu-id="a257a-102">Data Mining Model Training Destination</span></span>
  <span data-ttu-id="a257a-103">データ マイニング モデル トレーニング変換先は、変換先が受け取るデータをデータ マイニング モデル アルゴリズムに渡すことにより、データ マイニング モデルのトレーニングを行います。</span><span class="sxs-lookup"><span data-stu-id="a257a-103">The Data Mining Model Training destination trains data mining models by passing the data that the destination receives through the data mining model algorithms.</span></span> <span data-ttu-id="a257a-104">複数のデータ マイニング モデルが同じデータ マイニング構造に基づいて構築されている場合は、1 つの変換先を使用してトレーニングできます。</span><span class="sxs-lookup"><span data-stu-id="a257a-104">Multiple data mining models can be trained by one destination if the models are built on the same data mining structure.</span></span> <span data-ttu-id="a257a-105">詳細については、「 [マイニング構造列](https://docs.microsoft.com/analysis-services/data-mining/mining-structure-columns) 」と「 [マイニング モデル列](https://docs.microsoft.com/analysis-services/data-mining/mining-model-columns)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a257a-105">For more information, see [Mining Structure Columns](https://docs.microsoft.com/analysis-services/data-mining/mining-structure-columns) and [Mining Model Columns](https://docs.microsoft.com/analysis-services/data-mining/mining-model-columns).</span></span>  
  
## <a name="configuration-of-the-data-mining-model-training-destination"></a><span data-ttu-id="a257a-106">データ マイニング モデル トレーニング変換先の構成</span><span class="sxs-lookup"><span data-stu-id="a257a-106">Configuration of the Data Mining Model Training Destination</span></span>  
 <span data-ttu-id="a257a-107">対象になる構造とその構造に基づいて構築されているモデルのケース レベル列で、コンテンツの種類が KEY TIME または KEY SEQUENCE の列がある場合、入力データをその列で並べ替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="a257a-107">If a case level column of the target structure and the models built on the structure has the content type KEY TIME or KEY SEQUENCE, the input data must be sorted on that column.</span></span> <span data-ttu-id="a257a-108">たとえば、Microsoft Time Series アルゴリズムを使用して構築されたモデルでは、コンテンツの種類に KEY TIME が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a257a-108">For example, models built using the Microsoft Time Series algorithm use the content type KEY TIME.</span></span> <span data-ttu-id="a257a-109">入力データが並べ替えられていない場合、そのモデルの処理が失敗する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a257a-109">If input data is not sorted, the processing of the model may fail.</span></span> <span data-ttu-id="a257a-110">データを並べ替える必要がある場合、データ フロー内で事前に並べ替え変換を使用してデータを並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="a257a-110">If the data requires sorting, you can use a Sort transformation earlier in the data flow to sort the data.</span></span> <span data-ttu-id="a257a-111">コンテンツの種類が KEY である列には、この要件は適用されません。</span><span class="sxs-lookup"><span data-stu-id="a257a-111">This requirement does not apply to columns with the KEY content type.</span></span> <span data-ttu-id="a257a-112">詳細については、「[コンテンツの種類 (データ マイニング)](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining)」と「[並べ替え変換](transformations/sort-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a257a-112">For more information, see [Content Types &#40;Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining) and [Sort Transformation](transformations/sort-transformation.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a257a-113">データ マイニング モデル トレーニング変換先への入力は、並べ替えられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a257a-113">The input to the Data Mining Model training destination must be sorted.</span></span> <span data-ttu-id="a257a-114">データを並べ替えるため、データ フロー内のデータ マイニング モデル トレーニング変換先の上流に、並べ替え変換を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a257a-114">To sort the data, you can include a Sort destination upstream from the Data Mining Model Training destination in the data flow.</span></span> <span data-ttu-id="a257a-115">詳細については、「 [Sort Transformation](transformations/sort-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a257a-115">For more information, see [Sort Transformation](transformations/sort-transformation.md).</span></span>  
  
 <span data-ttu-id="a257a-116">この変換先は 1 つの入力をとりますが、出力はありません。</span><span class="sxs-lookup"><span data-stu-id="a257a-116">This destination has one input and no output.</span></span>  
  
 <span data-ttu-id="a257a-117">データ マイニング モデル トレーニング変換先では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 接続マネージャーの使用により、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクト、または変換先によってトレーニングされるマイニング構造とマイニング モデルを含む [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスへの接続が行われます。</span><span class="sxs-lookup"><span data-stu-id="a257a-117">The Data Mining Model Training destination uses an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to connect to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the mining structure and mining models that the destination trains.</span></span> <span data-ttu-id="a257a-118">詳しくは、「 [Analysis Services 接続マネージャー](../connection-manager/analysis-services-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a257a-118">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
 <span data-ttu-id="a257a-119">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="a257a-119">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="a257a-120">**[データ マイニング モデル トレーニング エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a257a-120">For more information about the properties that you can set in the **Data Mining Model Training Editor** dialog box, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="a257a-121">[データ マイニング モデル トレーニング エディター ([接続] タブ)](../data-mining-model-training-editor-connection-tab.md)</span><span class="sxs-lookup"><span data-stu-id="a257a-121">[Data Mining Model Training Editor &#40;Connection Tab&#41;](../data-mining-model-training-editor-connection-tab.md)</span></span>  
  
-   <span data-ttu-id="a257a-122">[データ マイニング モデル トレーニング エディター([列] タブ)](../data-mining-model-training-editor-columns-tab.md)</span><span class="sxs-lookup"><span data-stu-id="a257a-122">[Data Mining Model Training Editor &#40;Columns Tab&#41;](../data-mining-model-training-editor-columns-tab.md)</span></span>  
  
 <span data-ttu-id="a257a-123">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="a257a-123">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="a257a-124">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a257a-124">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="a257a-125">Common Properties</span><span class="sxs-lookup"><span data-stu-id="a257a-125">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="a257a-126">データ マイニング モデル トレーニング変換先のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="a257a-126">Data Mining Model Training Destination Custom Properties</span></span>](data-mining-model-training-destination-custom-properties.md)  
  
 <span data-ttu-id="a257a-127">プロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a257a-127">For more information about how to set properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
