---
title: パーティション処理変換先 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partitionprocessingdest.f1
helpviewer_keywords:
- partitions [Analysis Services], processing
- Partition Processing destination [Integration Services]
- destinations [Integration Services], Partition Processing
ms.assetid: 36c592ff-3f78-4a58-b496-31c1c8eee131
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d32306328f7a0575e55397d5209b4767d0cf1bd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633930"
---
# <a name="partition-processing-destination"></a><span data-ttu-id="d7c53-102">パーティション処理変換先</span><span class="sxs-lookup"><span data-stu-id="d7c53-102">Partition Processing Destination</span></span>
  <span data-ttu-id="d7c53-103">パーティション処理変換先では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のパーティションが読み込まれ処理されます。</span><span class="sxs-lookup"><span data-stu-id="d7c53-103">The Partition Processing destination loads and processes an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] partition.</span></span> <span data-ttu-id="d7c53-104">パーティションの詳細については、「[パーティション (Analysis Services - 多次元データ)](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7c53-104">For more information about partitions, see [Partitions &#40;Analysis Services - Multidimensional Data&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data).</span></span>  
  
 <span data-ttu-id="d7c53-105">パーティション処理変換先には、次の機能が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d7c53-105">The Partition Processing destination includes the following features:</span></span>  
  
-   <span data-ttu-id="d7c53-106">増分処理、完全処理、または更新処理を実行するオプション。</span><span class="sxs-lookup"><span data-stu-id="d7c53-106">Options to perform incremental, full, or update processing.</span></span>  
  
-   <span data-ttu-id="d7c53-107">エラー構成。処理中のエラーを無視するか、またはエラーが指定した回数に達した場合、処理を停止するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d7c53-107">Error configuration, to specify whether processing ignores errors or stops after a specified number of errors.</span></span>  
  
-   <span data-ttu-id="d7c53-108">パーティション分割列への入力列のマッピング。</span><span class="sxs-lookup"><span data-stu-id="d7c53-108">Mapping of input columns to partition columns.</span></span>  
  
 <span data-ttu-id="d7c53-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトの処理に関する詳細については、「[処理オプションと設定 (Analysis Services)](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7c53-109">For more information about processing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects, see [Processing Options and Settings &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d7c53-110">ここで説明されているタスクは、Analysis Services テーブル モデルには適用されません。</span><span class="sxs-lookup"><span data-stu-id="d7c53-110">Tasks described here do not apply to Analysis Services tabular models.</span></span>  <span data-ttu-id="d7c53-111">テーブル モデルで入力列をパーティション列にマップすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d7c53-111">You cannot map input columns to partition columns for tabular models.</span></span> <span data-ttu-id="d7c53-112">代わりに Analysis Services DDL 実行タスク [Analysis Services Execute DDL Task](../control-flow/analysis-services-execute-ddl-task.md) を使用してパーティションを処理することができます。</span><span class="sxs-lookup"><span data-stu-id="d7c53-112">You can instead use the Analysis Services Execute DDL task [Analysis Services Execute DDL Task](../control-flow/analysis-services-execute-ddl-task.md) to process the partition.</span></span>  
  
## <a name="configuration-of-the-partition-processing-destination"></a><span data-ttu-id="d7c53-113">パーティション処理変換先の構成</span><span class="sxs-lookup"><span data-stu-id="d7c53-113">Configuration of the Partition Processing Destination</span></span>  
 <span data-ttu-id="d7c53-114">パーティション処理変換先は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 接続マネージャーを接続して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクト、または変換先が処理するキューブとパーティションを含む [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d7c53-114">The Partition Processing destination uses an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to connect to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the cubes and partitions the destination processes.</span></span> <span data-ttu-id="d7c53-115">詳しくは、「 [Analysis Services 接続マネージャー](../connection-manager/analysis-services-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d7c53-115">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
 <span data-ttu-id="d7c53-116">この変換先は 1 つの入力をとります。</span><span class="sxs-lookup"><span data-stu-id="d7c53-116">This destination has one input.</span></span> <span data-ttu-id="d7c53-117">エラー出力はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d7c53-117">It does not support an error output.</span></span>  
  
 <span data-ttu-id="d7c53-118">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="d7c53-118">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="d7c53-119">**[パーティション処理変換先エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7c53-119">For more information about the properties that you can set in the Partition Processing **Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="d7c53-120">[[パーティション処理変換先エディター] &#40;[接続マネージャー] ページ&#41;](../partition-processing-destination-editor-connection-manager-page.md)</span><span class="sxs-lookup"><span data-stu-id="d7c53-120">[Partition Processing Destination Editor &#40;Connection Manager Page&#41;](../partition-processing-destination-editor-connection-manager-page.md)</span></span>  
  
-   <span data-ttu-id="d7c53-121">[パーティション処理変換先エディター ([マッピング] ページ)](../partition-processing-destination-editor-mappings-page.md)</span><span class="sxs-lookup"><span data-stu-id="d7c53-121">[Partition Processing Destination Editor &#40;Mappings Page&#41;](../partition-processing-destination-editor-mappings-page.md)</span></span>  
  
-   <span data-ttu-id="d7c53-122">[[パーティション処理変換先エディター] &#40;[詳細設定] ページ&#41;](../partition-processing-destination-editor-advanced-page.md)</span><span class="sxs-lookup"><span data-stu-id="d7c53-122">[Partition Processing Destination Editor &#40;Advanced Page&#41;](../partition-processing-destination-editor-advanced-page.md)</span></span>  
  
 <span data-ttu-id="d7c53-123">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="d7c53-123">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="d7c53-124">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7c53-124">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d7c53-125">Common Properties</span><span class="sxs-lookup"><span data-stu-id="d7c53-125">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="d7c53-126">パーティション処理変換先のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="d7c53-126">Partition Processing Destination Custom Properties</span></span>](partition-processing-destination-custom-properties.md)  
  
 <span data-ttu-id="d7c53-127">データ フロー コンポーネントのプロパティの設定方法については、「 [データ フロー コンポーネントのプロパティを設定する](set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7c53-127">For more information about how to set the properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
