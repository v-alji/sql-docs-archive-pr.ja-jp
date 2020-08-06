---
title: ディメンション処理変換先 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dimensionprocessingdest.f1
helpviewer_keywords:
- Dimension Processing destination
- loading dimensions
- destinations [Integration Services], Dimension Processing
- dimensions [Analysis Services], processing
ms.assetid: 4c49bb95-7259-42f4-a785-bb6aaf5f8566
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 61cde87ac4fa5fcb1352491d787674447dd404b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633950"
---
# <a name="dimension-processing-destination"></a><span data-ttu-id="b2929-102">ディメンション処理変換先</span><span class="sxs-lookup"><span data-stu-id="b2929-102">Dimension Processing Destination</span></span>
  <span data-ttu-id="b2929-103">ディメンション処理変換先では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のディメンションが読み込まれ処理されます。</span><span class="sxs-lookup"><span data-stu-id="b2929-103">The Dimension Processing destination loads and processes an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dimension.</span></span> <span data-ttu-id="b2929-104">ディメンションの詳細については、「[ディメンション (Analysis Services - 多次元データ)](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2929-104">For more information about dimensions, see [Dimensions &#40;Analysis Services - Multidimensional Data&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data).</span></span>  
  
 <span data-ttu-id="b2929-105">ディメンション処理変換先には、次の機能が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b2929-105">The Dimension Processing destination includes the following features:</span></span>  
  
-   <span data-ttu-id="b2929-106">増分処理、完全処理、または更新処理を実行するオプション。</span><span class="sxs-lookup"><span data-stu-id="b2929-106">Options to perform incremental, full, or update processing.</span></span>  
  
-   <span data-ttu-id="b2929-107">エラー構成。ディメンション処理がエラーを無視するか、または指定した数のエラー発生後に停止するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b2929-107">Error configuration, to specify whether dimension processing ignores errors or stops after a specified number of errors.</span></span>  
  
-   <span data-ttu-id="b2929-108">ディメンション テーブルの列への入力列のマッピング</span><span class="sxs-lookup"><span data-stu-id="b2929-108">Mapping of input columns to columns in dimension tables.</span></span>  
  
 <span data-ttu-id="b2929-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトの処理に関する詳細については、「[処理オプションと設定 (Analysis Services)](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2929-109">For more information about processing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects, see [Processing Options and Settings &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services).</span></span>  
  
## <a name="configuration-of-the-dimension-processing-destination"></a><span data-ttu-id="b2929-110">ディメンション処理変換先の構成</span><span class="sxs-lookup"><span data-stu-id="b2929-110">Configuration of the Dimension Processing Destination</span></span>  
 <span data-ttu-id="b2929-111">ディメンション処理変換先は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 接続マネージャーを接続して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクト、または、変換先が処理するディメンションを含む [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="b2929-111">The Dimension Processing destination uses an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to connect to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the dimensions the destination processes.</span></span> <span data-ttu-id="b2929-112">詳しくは、「 [Analysis Services 接続マネージャー](../connection-manager/analysis-services-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b2929-112">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
 <span data-ttu-id="b2929-113">この変換先は 1 つの入力をとります。</span><span class="sxs-lookup"><span data-stu-id="b2929-113">This destination has one input.</span></span> <span data-ttu-id="b2929-114">エラー出力はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="b2929-114">It does not support an error output.</span></span>  
  
 <span data-ttu-id="b2929-115">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="b2929-115">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="b2929-116">**[ディメンション処理変換先エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2929-116">For more information about the properties that you can set in the **Dimension Processing Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="b2929-117">[ディメンション処理変換先エディター ([接続マネージャー] ページ)](../dimension-processing-destination-editor-connection-manager-page.md)</span><span class="sxs-lookup"><span data-stu-id="b2929-117">[Dimension Processing Destination Editor &#40;Connection Manager Page&#41;](../dimension-processing-destination-editor-connection-manager-page.md)</span></span>  
  
-   <span data-ttu-id="b2929-118">[ディメンション処理変換先エディター ([マッピング] ページ)](../dimension-processing-destination-editor-mappings-page.md)</span><span class="sxs-lookup"><span data-stu-id="b2929-118">[Dimension Processing Destination Editor &#40;Mappings Page&#41;](../dimension-processing-destination-editor-mappings-page.md)</span></span>  
  
-   <span data-ttu-id="b2929-119">[ディメンション処理変換先エディター &#40;[詳細設定] ページ&#41;](../dimension-processing-destination-editor-advanced-page.md)</span><span class="sxs-lookup"><span data-stu-id="b2929-119">[Dimension Processing Destination Editor &#40;Advanced Page&#41;](../dimension-processing-destination-editor-advanced-page.md)</span></span>  
  
 <span data-ttu-id="b2929-120">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="b2929-120">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="b2929-121">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2929-121">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topic:</span></span>  
  
-   [<span data-ttu-id="b2929-122">Common Properties</span><span class="sxs-lookup"><span data-stu-id="b2929-122">Common Properties</span></span>](../common-properties.md)  
  
 <span data-ttu-id="b2929-123">データ フロー コンポーネントのプロパティの設定方法については、「 [データ フロー コンポーネントのプロパティを設定する](set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2929-123">For more information about how to set the properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2929-124">参照</span><span class="sxs-lookup"><span data-stu-id="b2929-124">See Also</span></span>  
 <span data-ttu-id="b2929-125">[データ フロー](data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="b2929-125">[Data Flow](data-flow.md) </span></span>  
 [<span data-ttu-id="b2929-126">Integration Services の変換</span><span class="sxs-lookup"><span data-stu-id="b2929-126">Integration Services Transformations</span></span>](transformations/integration-services-transformations.md)  
  
  
