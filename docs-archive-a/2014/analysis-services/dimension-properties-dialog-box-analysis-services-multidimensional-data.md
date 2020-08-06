---
title: '[ディメンションのプロパティ] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.dimensionproperties.f1
helpviewer_keywords:
- Dimension Properties dialog box
ms.assetid: 7235d443-b2ce-4c53-b2eb-abceb28394bb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0523220c76c11280165bc825c5c00c5eb9e23be6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645901"
---
# <a name="dimension-properties-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="afa3a-102">[ディメンションのプロパティ] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="afa3a-102">Dimension Properties Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="afa3a-103">**の** [ディメンションのプロパティ] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースのディメンションのプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="afa3a-103">Use the **Dimension Properties** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to set the properties of a dimension in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="afa3a-104">**[ディメンションのプロパティ]** ダイアログ ボックスを表示するには、オブジェクト エクスプローラーでディメンションを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="afa3a-104">You can display the **Dimension Properties** dialog box by right-clicking a dimension in Object Explorer and selecting **Properties**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="afa3a-105">Options</span><span class="sxs-lookup"><span data-stu-id="afa3a-105">Options</span></span>  
  
|<span data-ttu-id="afa3a-106">期間</span><span class="sxs-lookup"><span data-stu-id="afa3a-106">Term</span></span>|<span data-ttu-id="afa3a-107">定義</span><span class="sxs-lookup"><span data-stu-id="afa3a-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="afa3a-108">**名前**</span><span class="sxs-lookup"><span data-stu-id="afa3a-108">**Name**</span></span>|<span data-ttu-id="afa3a-109">ディメンションの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="afa3a-109">Displays the name of the dimension.</span></span>|  
|<span data-ttu-id="afa3a-110">**ID**</span><span class="sxs-lookup"><span data-stu-id="afa3a-110">**ID**</span></span>|<span data-ttu-id="afa3a-111">ディメンションの識別子を表示します。</span><span class="sxs-lookup"><span data-stu-id="afa3a-111">Displays the identifier of the dimension.</span></span>|  
|<span data-ttu-id="afa3a-112">**説明**</span><span class="sxs-lookup"><span data-stu-id="afa3a-112">**Description**</span></span>|<span data-ttu-id="afa3a-113">ディメンションの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="afa3a-113">Displays the description of the dimension.</span></span>|  
|<span data-ttu-id="afa3a-114">**[タイムスタンプの作成]**</span><span class="sxs-lookup"><span data-stu-id="afa3a-114">**Create Timestamp**</span></span>|<span data-ttu-id="afa3a-115">ディメンションが作成された日時を表示します。</span><span class="sxs-lookup"><span data-stu-id="afa3a-115">Displays the date and time the dimension was created.</span></span>|  
|<span data-ttu-id="afa3a-116">**[スキーマの最終更新]**</span><span class="sxs-lookup"><span data-stu-id="afa3a-116">**Last Schema Update**</span></span>|<span data-ttu-id="afa3a-117">ディメンションのメタデータが最後に更新された日時を表示します。</span><span class="sxs-lookup"><span data-stu-id="afa3a-117">Displays the date and time the metadata for the dimension was last updated.</span></span>|  
|<span data-ttu-id="afa3a-118">**[処理モード]**</span><span class="sxs-lookup"><span data-stu-id="afa3a-118">**Processing Mode**</span></span>|<span data-ttu-id="afa3a-119">ディメンションに対して使用する処理モードを選択します。</span><span class="sxs-lookup"><span data-stu-id="afa3a-119">Select the processing mode to use for the dimension.</span></span> <span data-ttu-id="afa3a-120">このプロパティの値の詳細については、「<xref:Microsoft.AnalysisServices.Dimension.ProcessingMode%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afa3a-120">For more information about the values for this property, see <xref:Microsoft.AnalysisServices.Dimension.ProcessingMode%2A>.</span></span>|  
|<span data-ttu-id="afa3a-121">**State**</span><span class="sxs-lookup"><span data-stu-id="afa3a-121">**State**</span></span>|<span data-ttu-id="afa3a-122">ディメンションの処理状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="afa3a-122">Displays the processing state of the dimension.</span></span> <span data-ttu-id="afa3a-123">このプロパティの値の詳細については、「<xref:Microsoft.AnalysisServices.ProcessableMajorObject.State%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afa3a-123">For more information about the values for this property, see <xref:Microsoft.AnalysisServices.ProcessableMajorObject.State%2A>.</span></span>|  
|<span data-ttu-id="afa3a-124">**[最終処理]**</span><span class="sxs-lookup"><span data-stu-id="afa3a-124">**Last Processed**</span></span>|<span data-ttu-id="afa3a-125">ディメンションが最後に処理された日時を表示します。</span><span class="sxs-lookup"><span data-stu-id="afa3a-125">Displays the date and time the dimension was last processed.</span></span>|  
|<span data-ttu-id="afa3a-126">**[現在のストレージ モード]**</span><span class="sxs-lookup"><span data-stu-id="afa3a-126">**Current Storage Mode**</span></span>|<span data-ttu-id="afa3a-127">ディメンションの現在のストレージ モードを表示します。</span><span class="sxs-lookup"><span data-stu-id="afa3a-127">Displays the current storage mode for the dimension.</span></span> <span data-ttu-id="afa3a-128">このプロパティの値の詳細については、「<xref:Microsoft.AnalysisServices.Dimension.CurrentStorageMode%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afa3a-128">For more information about the values for this property, see <xref:Microsoft.AnalysisServices.Dimension.CurrentStorageMode%2A>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="afa3a-129">参照</span><span class="sxs-lookup"><span data-stu-id="afa3a-129">See Also</span></span>  
 <span data-ttu-id="afa3a-130">[多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="afa3a-130">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="afa3a-131">ディメンション &#40;Analysis Services - 多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="afa3a-131">Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
