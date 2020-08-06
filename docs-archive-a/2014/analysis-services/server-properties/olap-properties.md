---
title: OLAP のプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- AggregationPerfLog property
- DefaultPageSizeForProp property
- UseSinglePassForDimSecurityAutoExist property
- DeepCompressValue property
- CacheRowsetRows property
- Income property
- AggregationNewAlgo property
- MemoryAdjustFactor property
- DimensionLatencyAccuracy property
- InitialBonus property
- DefaultPageSizeForDataHeader property
- MaxCPUUsage property
- DistinctBuffer property
- PartitionLatencyAccuracy property
- MaxRetries property
- UseDataCacheRegistryMultiplyKey property
- ConvertDeletedToUnknown property
- DatabaseConnectionPoolMax property
- DataFileInitEnabled property
- DefaultPageSizeForHash property
- MaxRolapOrConditions property
- UseDataCacheFreeLastPageMemory property
- OLAP [Analysis Services], properties
- MapHandleAlgorithm property
- IndexBuildEnabled property
- MaxObjectsInParallel property
- IgnoreNullRolapRows property
- DimensionPropertyCacheSize property
- DefaultRefreshInterval property
- CheckDistinctRecordSortOrder property
- BufferMemoryLimit property
- EnableTableGrouping property
- ExpressNonEmptyUseEnabled property
- CopyLinkedDataCacheAndRegistry property
- UseDataSlice property
- MemoryLimitErrorEnabled property
- Enabled property
- EnableRolapOptimization property
- DatabaseConnectionPoolTimeout property
- UseDataCacheRegistryHashTable property
- AggregationsBuildEnabled property
- Tax property
- DatabaseConnectionPoolGeneralTimeout property
- DefaultPageSizeForString property
- DatabaseConnectionPoolConnectTimeout property
- MinimumBalance property
- OptimizeSchema property
- UseCalculationCacheRegistry property
- MaxTableDepth property
- DataSliceInitEnabled property
- PrefetchLowerGranularities property
- UseVBANet property
- BufferRecordLimit property
- DefaultPageSizeForIndexHeader property
- MaximumBalance property
- CalculationCacheRegistryMaxIterations property
- DefaultDrillthroughMaxRows property
- IndexBuildThreshold property
- UseDataCacheRegistry property
- MemoryAdjustConst property
- ApplyIntersect property
- IndexFileInitEnabled property
- CacheRowsetToDisk property
- DataCacheRegistryMaxIterations property
- AllowSEFiltering property
- ForceMultiPass property
- ApplySubtract property
- IndexUseEnabled property
- AggregationsUseEnabled property
- DataPlacementOptimization property
- UseMaterializedIterators property
- CacheRecordLimit property
- ROLAPDimensionProcessingEffort property
- DefaultPageSizeForIndex property
- EnableRolapDimQueryTableGrouping property
- DimensionPropertyKeyCache property
- SleepIntervalSecs property
- DefaultPageSizeForData property
- MapFormatMask property
- CalculationEvaluationPolicy property
- AggregationMemoryLimitMin property
- RecordsReportGranularity property
- MemoryLimit property
- AggregationMemoryLimitMax property
ms.assetid: 06eb0d78-96c0-42ff-b759-f4c794597c8d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2eb89d318bfdb78935eb4d9f202db11b978c59b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640270"
---
# <a name="olap-properties"></a><span data-ttu-id="37b16-102">OLAP のプロパティ</span><span class="sxs-lookup"><span data-stu-id="37b16-102">OLAP Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="37b16-103">では、次の表に示す OLAP サーバー プロパティがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="37b16-103">supports the OLAP server properties listed in the following tables.</span></span> <span data-ttu-id="37b16-104">その他のサーバー プロパティとその設定方法の詳細については、「 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37b16-104">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="37b16-105">**適用対象:** 多次元サーバーモードのみ</span><span class="sxs-lookup"><span data-stu-id="37b16-105">**Applies to:** Multidimensional server mode only</span></span>  
  
## <a name="memory"></a><span data-ttu-id="37b16-106">メモリ</span><span class="sxs-lookup"><span data-stu-id="37b16-106">Memory</span></span>  
 `DefaultPageSizeForData`  
 <span data-ttu-id="37b16-107">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-107">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DefaultPageSizeForDataHeader`  
 <span data-ttu-id="37b16-108">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-108">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DefaultPageSizeForIndex`  
 <span data-ttu-id="37b16-109">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-109">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DefaultPageSizeForIndexHeader`  
 <span data-ttu-id="37b16-110">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-110">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DefaultPageSizeForString`  
 <span data-ttu-id="37b16-111">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-111">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DefaultPageSizeForHash`  
 <span data-ttu-id="37b16-112">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-112">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DefaultPageSizeForProp`  
 <span data-ttu-id="37b16-113">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-113">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="lazyprocessing"></a><span data-ttu-id="37b16-114">レイジー処理</span><span class="sxs-lookup"><span data-stu-id="37b16-114">LazyProcessing</span></span>  
 `Enabled`  
 <span data-ttu-id="37b16-115">レイジー集計処理が有効かどうかを示すブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-115">A Boolean property that specifies whether lazy aggregation processing is enabled.</span></span>  
  
 `SleepIntervalSecs`  
 <span data-ttu-id="37b16-116">保留中のレイジー処理ジョブがあるかどうかをサーバーが確認する間隔を秒単位で定義する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-116">A signed 32-bit integer property that defines the interval, in seconds, that the server checks whether there are lazy processing jobs pending.</span></span>  
  
 `MaxCPUUsage`  
 <span data-ttu-id="37b16-117">レイジー処理の最大 CPU 使用量を比率として定義する、符号付き 64 ビット倍精度浮動小数点数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-117">A signed 64-bit double-precision floating-point number property that defines maximum CPU usage for lazy processing, expressed as a percentage.</span></span> <span data-ttu-id="37b16-118">サーバーは、スナップショットに基づいて平均 CPU 使用量を監視します。</span><span class="sxs-lookup"><span data-stu-id="37b16-118">The server monitors average CPU use based on snapshots.</span></span> <span data-ttu-id="37b16-119">CPU が瞬間的にこのしきい値を超えるのは正常な動作です。</span><span class="sxs-lookup"><span data-stu-id="37b16-119">It is normal behavior for the CPU to spike above this threshold.</span></span>  
  
 <span data-ttu-id="37b16-120">このプロパティの既定値は 0.5 であり、CPU の最大 50% がレイジー処理に充てられることを示します。</span><span class="sxs-lookup"><span data-stu-id="37b16-120">The default value for this property is 0.5, indicating a maximum of 50% of the CPU will be devoted to lazy processing.</span></span>  
  
 `MaxObjectsInParallel`  
 <span data-ttu-id="37b16-121">並列レイジー処理を実行できるパーティションの最大数を指定する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-121">A signed 32-bit integer property that specifies the maximum number of partitions that can be lazily processed in parallel.</span></span>  
  
 `MaxRetries`  
 <span data-ttu-id="37b16-122">レイジー処理が失敗した場合にエラーが発生する前にイベントでの再試行の回数を定義する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-122">A signed 32-bit integer property that defines the number of retries in the event that lazy processing fails before an error is raised.</span></span>  
  
## <a name="processplan"></a><span data-ttu-id="37b16-123">プロセス プラン</span><span class="sxs-lookup"><span data-stu-id="37b16-123">ProcessPlan</span></span>  
 `CacheRowsetRows`  
 <span data-ttu-id="37b16-124">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-124">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `CacheRowsetToDisk`  
 <span data-ttu-id="37b16-125">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-125">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DistinctBuffer`  
 <span data-ttu-id="37b16-126">個別のカウントに使用される内部バッファーのサイズを定義する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-126">A signed 32-bit integer property that defines the size of an internal buffer used for distinct counts.</span></span> <span data-ttu-id="37b16-127">メモリ使用量を犠牲にして個別のカウントの処理を高速化するには、この値を大きくします。</span><span class="sxs-lookup"><span data-stu-id="37b16-127">Increase this value to speed up distinct count processing at the cost of memory use.</span></span>  
  
 `EnableRolapDimQueryTableGrouping`  
 <span data-ttu-id="37b16-128">テーブルのグループ化が ROLAP ディメンションに対して有効かどうかを指定するブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-128">A Boolean property that specifies whether table grouping is enabled for ROLAP dimensions.</span></span> <span data-ttu-id="37b16-129">True の場合、実行時に ROLAP ディメンションをクエリすると、属性ごとに別々にクエリされるのではなく、ROLAP ディメンション テーブル全体が一度にクエリされます。</span><span class="sxs-lookup"><span data-stu-id="37b16-129">If True, when querying ROLAP dimensions at runtime, entire ROLAP dimension tables are queried at once, as opposed to separate queries for each attribute.</span></span>  
  
 `EnableTableGrouping`  
 <span data-ttu-id="37b16-130">テーブルのグループ化が有効かどうかを指定するブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-130">A Boolean property that specifies whether table grouping is enabled.</span></span> <span data-ttu-id="37b16-131">True の場合、ディメンションを処理すると、属性ごとに別々にクエリされるのではなく、ディメンション テーブル全体が一度にクエリされます。</span><span class="sxs-lookup"><span data-stu-id="37b16-131">If True, when processing dimensions, entire dimension tables are queried at once, as opposed to separate queries for each attribute.</span></span>  
  
 `ForceMultiPass`  
 <span data-ttu-id="37b16-132">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-132">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MaxTableDepth`  
 <span data-ttu-id="37b16-133">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-133">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryAdjustConst`  
 <span data-ttu-id="37b16-134">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-134">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryAdjustFactor`  
 <span data-ttu-id="37b16-135">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-135">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryLimit`  
 <span data-ttu-id="37b16-136">処理に充てるメモリの最大量を定義する、符号付き 64 ビット倍精度浮動小数点数のプロパティです。物理メモリの比率として表されます。</span><span class="sxs-lookup"><span data-stu-id="37b16-136">A signed 64-bit double-precision floating-point number property that defines the maximum amount of memory to be devoted to processing, expressed as a percentage of physical memory.</span></span>  
  
 <span data-ttu-id="37b16-137">このプロパティの既定値は 65 であり、物理メモリの最大 65% がキューブおよびディメンションの処理に充てられることを示します。</span><span class="sxs-lookup"><span data-stu-id="37b16-137">The default value for this property is 65, indicating that 65% of physical memory may be devoted to cube and dimension processing.</span></span>  
  
 `MemoryLimitErrorEnabled`  
 <span data-ttu-id="37b16-138">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-138">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `OptimizeSchema`  
 <span data-ttu-id="37b16-139">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-139">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="proactivecaching"></a><span data-ttu-id="37b16-140">プロアクティブ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="37b16-140">ProactiveCaching</span></span>  
 `DefaultRefreshInterval`  
 <span data-ttu-id="37b16-141">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-141">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DimensionLatencyAccuracy`  
 <span data-ttu-id="37b16-142">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-142">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `PartitionLatencyAccuracy`  
 <span data-ttu-id="37b16-143">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-143">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="process"></a><span data-ttu-id="37b16-144">Process</span><span class="sxs-lookup"><span data-stu-id="37b16-144">Process</span></span>  
 `AggregationMemoryLimitMax`  
 <span data-ttu-id="37b16-145">集計処理に充てることができるメモリの最大量を定義する、符号付き 64 ビット倍精度浮動小数点数のプロパティです。物理メモリの比率として表されます。</span><span class="sxs-lookup"><span data-stu-id="37b16-145">A signed 64-bit double-precision floating-point number property that defines the maximum amount of memory that can be devoted to aggregation processing, expressed as a percentage of physical memory.</span></span>  
  
 <span data-ttu-id="37b16-146">このプロパティの既定値は 80 であり、物理メモリの最大 80% が集計処理に充てられることを示します。</span><span class="sxs-lookup"><span data-stu-id="37b16-146">The default value for this property is 80, indicating that 80% of physical memory may be devoted to aggregation processing.</span></span>  
  
 `AggregationMemoryLimitMin`  
 <span data-ttu-id="37b16-147">集計処理に充てることができるメモリの最小量を定義する、符号付き 64 ビット倍精度浮動小数点数のプロパティです。物理メモリの比率として表されます。</span><span class="sxs-lookup"><span data-stu-id="37b16-147">A signed 64-bit double-precision floating-point number property that defines the minimum amount of memory that can be devoted to aggregation processing, expressed as a percentage of physical memory.</span></span> <span data-ttu-id="37b16-148">値を大きくすると、メモリ使用量を犠牲にして集計処理を高速化できます。</span><span class="sxs-lookup"><span data-stu-id="37b16-148">A larger value may speed up aggregation processing at the cost of memory usage.</span></span>  
  
 <span data-ttu-id="37b16-149">このプロパティの既定値は 10 であり、物理メモリの最小 10% が集計処理に充てられることを示します。</span><span class="sxs-lookup"><span data-stu-id="37b16-149">The default value for this property is 10, indicating that minimally 10% of physical memory will be devoted to aggregation processing.</span></span>  
  
 `AggregationNewAlgo`  
 <span data-ttu-id="37b16-150">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-150">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `AggregationPerfLog2`  
 <span data-ttu-id="37b16-151">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-151">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `AggregationsBuildEnabled`  
 <span data-ttu-id="37b16-152">集計の作成が有効かどうかを指定するブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-152">A Boolean property that specifies whether aggregation building is enabled.</span></span> <span data-ttu-id="37b16-153">これは、集計のデザインを変更することなく集計の作成のベンチマークを行うメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="37b16-153">This is a mechanism to benchmark aggregation building without changing aggregation design.</span></span>  
  
 `BufferMemoryLimit`  
 <span data-ttu-id="37b16-154">処理バッファー メモリの制限を定義する、符号付き 64 ビット倍精度浮動小数点数のプロパティです。物理メモリの比率として表されます。</span><span class="sxs-lookup"><span data-stu-id="37b16-154">A signed 64-bit double-precision floating-point number property that defines the processing buffer memory limit, expressed as a percent of physical memory.</span></span>  
  
 <span data-ttu-id="37b16-155">このプロパティの既定値は 60 であり、物理メモリの最大 60% がバッファー メモリに使用されることを示します。</span><span class="sxs-lookup"><span data-stu-id="37b16-155">The default value for this property is 60, which indicates that up to 60% of physical memory can be used for buffer memory.</span></span>  
  
 `BufferRecordLimit`  
 <span data-ttu-id="37b16-156">処理時にバッファーできるレコードの数を定義する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-156">A signed 32-bit integer property that defines the number of records that can be buffered during processing.</span></span>  
  
 <span data-ttu-id="37b16-157">このプロパティの既定値は 1048576 (レコード) です。</span><span class="sxs-lookup"><span data-stu-id="37b16-157">The default value for this property is 1048576 (records).</span></span>  
  
 `CacheRecordLimit`  
 <span data-ttu-id="37b16-158">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-158">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `CheckDistinctRecordSortOrder`  
 <span data-ttu-id="37b16-159">パーティションの処理時に個別のカウント クエリの結果の並べ替え順に意味があるかどうかを定義するブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-159">A Boolean property that defines if the sort order for the results of a distinct count query are meaningful when processing partitions.</span></span> <span data-ttu-id="37b16-160">True の場合、並べ替え順に意味はなく、サーバーによる "確認" が必要であることを示します。</span><span class="sxs-lookup"><span data-stu-id="37b16-160">True indicates the sort order is not meaningful and must be "checked" by the server.</span></span> <span data-ttu-id="37b16-161">個別のカウント メジャーを使用してパーティションを処理すると、クエリは並べ替え順に従って SQL に送信されます。</span><span class="sxs-lookup"><span data-stu-id="37b16-161">When processing partitions with distinct count measure, query sent to SQL with order-by.</span></span> <span data-ttu-id="37b16-162">処理を高速化するには False に設定してください。</span><span class="sxs-lookup"><span data-stu-id="37b16-162">Set to false to speed up processing.</span></span>  
  
 <span data-ttu-id="37b16-163">このプロパティの既定値は True であり、並べ替え順に意味がなく、確認が必要であることを示します。</span><span class="sxs-lookup"><span data-stu-id="37b16-163">The default value for this property is True, which indicates that the sort order is not meaningful and must be checked.</span></span>  
  
 `DatabaseConnectionPoolConnectTimeout`  
 <span data-ttu-id="37b16-164">新しい接続を開くときのタイムアウトを秒単位で指定する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-164">A signed 32-bit integer property that specifies timeout when opening a new connection in seconds.</span></span>  
  
 `DatabaseConnectionPoolGeneralTimeout`  
 <span data-ttu-id="37b16-165">外部 OLEDB 接続で使用するデータベース接続タイムアウトを秒単位で指定する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-165">A signed 32-bit integer property that specifies database connection timeout for use with external OLEDB connections in seconds.</span></span>  
  
 `DatabaseConnectionPoolMax`  
 <span data-ttu-id="37b16-166">プールされるデータベース接続の最大数を指定する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-166">A signed 32-bit integer property that specifies the maximum number of pooled database connections.</span></span>  
  
 <span data-ttu-id="37b16-167">このプロパティの既定値は 50 (接続) です。</span><span class="sxs-lookup"><span data-stu-id="37b16-167">The default value for this property is 50 (connections).</span></span>  
  
 `DatabaseConnectionPoolTimeout`  
 <span data-ttu-id="37b16-168">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-168">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataFileInitEnabled`  
 <span data-ttu-id="37b16-169">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-169">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataPlacementOptimization`  
 <span data-ttu-id="37b16-170">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-170">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataSliceInitEnabled`  
 <span data-ttu-id="37b16-171">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-171">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DeepCompressValue`  
 <span data-ttu-id="37b16-172">数値を圧縮して有効桁数を少なくすることができるかどうかを指定する、Double データ型のメジャーに適用されるブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-172">A Boolean property applying to measures with Double data type that specifies whether numbers can be compressed, causing a loss in numeric precision.</span></span> <span data-ttu-id="37b16-173">値が False の場合は、圧縮が行われず、有効桁数は少なくならないことを示します。</span><span class="sxs-lookup"><span data-stu-id="37b16-173">A value of False indicates no compression and no precision loss.</span></span>  
  
 <span data-ttu-id="37b16-174">このプロパティの既定値は True であり、圧縮が有効で、有効桁数が少なくなることを示します。</span><span class="sxs-lookup"><span data-stu-id="37b16-174">The default value for this property is True, which indicates that compression is enabled and precision will be lost.</span></span>  
  
 `DimensionPropertyKeyCache`  
 <span data-ttu-id="37b16-175">ディメンション プロパティ キーがキャッシュされるかどうかを指定するブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-175">A Boolean property that specifies whether dimension property keys are cached.</span></span> <span data-ttu-id="37b16-176">キーが一意でない場合は、True に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37b16-176">Must be set to True if keys are non-unique.</span></span>  
  
 `IndexBuildEnabled`  
 <span data-ttu-id="37b16-177">処理時にインデックスが作成されるかどうかを指定するブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-177">A Boolean property that specifies whether indexes are built upon processing.</span></span> <span data-ttu-id="37b16-178">このプロパティは、ベンチマークおよび情報提供を目的としています。</span><span class="sxs-lookup"><span data-stu-id="37b16-178">This property is for benchmarking and informational purposes.</span></span>  
  
 `IndexBuildThreshold`  
 <span data-ttu-id="37b16-179">パーティションに対してインデックスが作成されなくなる下限の行数しきい値を指定する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-179">A signed 32-bit integer property that specifies a row count threshold below which indexes will not be built for partitions.</span></span>  
  
 <span data-ttu-id="37b16-180">このプロパティの既定値は 4096 (行) です。</span><span class="sxs-lookup"><span data-stu-id="37b16-180">The default value for this property is 4096 (rows).</span></span>  
  
 `IndexFileInitEnabled`  
 <span data-ttu-id="37b16-181">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-181">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MapFormatMask`  
 <span data-ttu-id="37b16-182">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-182">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `RecordsReportGranularity`  
 <span data-ttu-id="37b16-183">処理時にサーバーがトレース イベントを記録する頻度を行単位で指定する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-183">A signed 32-bit integer property that specifies how often the server records Trace events during processing, in rows.</span></span>  
  
 <span data-ttu-id="37b16-184">このプロパティの既定値は 1000 であり、1,000 行ごとにトレース イベントがログ記録されることを示します。</span><span class="sxs-lookup"><span data-stu-id="37b16-184">The default value for this property is 1000, which indicates that a Trace event is logged once every 1000 rows.</span></span>  
  
 `ROLAPDimensionProcessingEffort`  
 <span data-ttu-id="37b16-185">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-185">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="query"></a><span data-ttu-id="37b16-186">クエリ</span><span class="sxs-lookup"><span data-stu-id="37b16-186">Query</span></span>  
 `AggregationsUseEnabled`  
 <span data-ttu-id="37b16-187">保存されている集計が実行時に使用されるかどうかを定義するブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-187">A Boolean property that defines whether stored aggregations are used at runtime.</span></span> <span data-ttu-id="37b16-188">このプロパティでは、情報提供およびベンチマークの目的で、集計のデザインを変更したり再処理したりせずに集計を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="37b16-188">This property allows aggregations to be disabled without changing the aggregation design or re-processing, for informational and benchmarking purposes.</span></span>  
  
 <span data-ttu-id="37b16-189">このプロパティの既定値は True であり、集計が有効であることを示します。</span><span class="sxs-lookup"><span data-stu-id="37b16-189">The default value for this property is True, indicating that aggregations are enabled.</span></span>  
  
 `AllowSEFiltering`  
 <span data-ttu-id="37b16-190">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-190">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `CalculationCacheRegistryMaxIterations`  
 <span data-ttu-id="37b16-191">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-191">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `CalculationEvaluationPolicy`  
 <span data-ttu-id="37b16-192">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-192">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ConvertDeletedToUnknown`  
 <span data-ttu-id="37b16-193">削除されたディメンション メンバーが不明なメンバーに変換されるかどうかを指定するブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-193">A Boolean property that specifies whether deleted dimension members are converted to Unknown member.</span></span>  
  
 `CopyLinkedDataCacheAndRegistry`  
 <span data-ttu-id="37b16-194">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-194">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCacheRegistryMaxIterations`  
 <span data-ttu-id="37b16-195">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-195">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DefaultDrillthroughMaxRows`  
 <span data-ttu-id="37b16-196">ドリルスルー クエリから返される行の最大数を指定する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-196">A signed 32-bit integer property that specifies the maximum number of rows that will return from a drill-through query.</span></span>  
  
 <span data-ttu-id="37b16-197">このプロパティの既定値は 10000 (行) です。</span><span class="sxs-lookup"><span data-stu-id="37b16-197">The default value for this property is 10000 (rows).</span></span>  
  
 `DimensionPropertyCacheSize`  
 <span data-ttu-id="37b16-198">クエリで使用するディメンション メンバーをキャッシュするために使用されるメモリ量 (バイト単位) を指定する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-198">A signed 32-bit integer property that specifies the amount of memory (in bytes) used to cache dimension members used in a query.</span></span>  
  
 <span data-ttu-id="37b16-199">既定値は、属性階層ごと、およびアクティブなクエリごとに 4,000,000 バイト (4 MB) です。</span><span class="sxs-lookup"><span data-stu-id="37b16-199">The default is 4,000,000 bytes (or 4 MB) per attribute hierarchy, per active query.</span></span> <span data-ttu-id="37b16-200">既定値は、一般的な階層を持つソリューションにとってバランスのとれたキャッシュ サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="37b16-200">The default value provides a well-balanced cache size for solutions having typical hierarchies.</span></span> <span data-ttu-id="37b16-201">ただし、非常に多くのメンバー (数百万単位) を持つディメンションや多層構造のディメンションの場合は、この値を大きくするとパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="37b16-201">However, dimensions with a very large number of members (in the millions) or deep hierarchies perform better if you increase this value.</span></span>  
  
 <span data-ttu-id="37b16-202">キャッシュ サイズを大きくする場合の暗黙的な影響:</span><span class="sxs-lookup"><span data-stu-id="37b16-202">Implications of increasing cache size:</span></span>  
  
-   <span data-ttu-id="37b16-203">ディメンション キャッシュでより多くのメモリを使用できるようにすると、メモリ使用率のコストが増加します。</span><span class="sxs-lookup"><span data-stu-id="37b16-203">Memory utilization costs increase when you allow more memory to be used by the dimension cache.</span></span> <span data-ttu-id="37b16-204">実際の使用率は、実行されるクエリによって異なります。</span><span class="sxs-lookup"><span data-stu-id="37b16-204">Actual usage depends on query execution.</span></span> <span data-ttu-id="37b16-205">すべてのクエリが、許容される最大量のメモリを使用するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="37b16-205">Not all queries will use the allowable maximum.</span></span>  
  
     <span data-ttu-id="37b16-206">これらのキャッシュによって使用されるメモリは縮小不能と見なされ、 **[TotalMemoryLimit]** を計算するときはその中に含まれることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="37b16-206">Note that the memory used by these caches is considered nonshrinkable and will be included when accounting against the **TotalMemoryLimit**.</span></span>  
  
-   <span data-ttu-id="37b16-207">サーバー上のすべてのデータベースに影響します。</span><span class="sxs-lookup"><span data-stu-id="37b16-207">Affects all databases on the server.</span></span> <span data-ttu-id="37b16-208">**DimensionPropertyCachesize** は、サーバー全体のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-208">**DimensionPropertyCachesize** is a server-wide property.</span></span> <span data-ttu-id="37b16-209">このプロパティを変更すると、現在のインスタンスで実行されているすべてのデータベースに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="37b16-209">Changing this property affects all databases running on the current instance.</span></span>  
  
 <span data-ttu-id="37b16-210">ディメンション キャッシュの要件を推定する方法:</span><span class="sxs-lookup"><span data-stu-id="37b16-210">Approach for estimating dimension cache requirements:</span></span>  
  
1.  <span data-ttu-id="37b16-211">最初はサイズを大幅に増やして、ディメンション キャッシュのサイズを増やしたときに利点が得られるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="37b16-211">Start by increasing the size by a large number to determine whether there is a benefit to increasing the dimension cache size.</span></span> <span data-ttu-id="37b16-212">たとえば、最初のステップとして既定値を倍にすることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="37b16-212">For example, you might want to double the default value as an initial step.</span></span>  
  
2.  <span data-ttu-id="37b16-213">パフォーマンスが向上することが明らかになった場合は、パフォーマンスとメモリ使用率の間で適切なバランスに達するまで、値を徐々に小さくします。</span><span class="sxs-lookup"><span data-stu-id="37b16-213">If a performance improvement is evident, incrementally reduce the value until you reach a balance between performance and memory utilization.</span></span>  
  
 `ExpressNonEmptyUseEnabled`  
 <span data-ttu-id="37b16-214">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-214">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `IgnoreNullRolapRows`  
 <span data-ttu-id="37b16-215">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-215">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `IndexUseEnabled`  
 <span data-ttu-id="37b16-216">インデックスが実行時に使用されるかどうかを定義するブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-216">A Boolean property that defines whether indexes are used at runtime.</span></span> <span data-ttu-id="37b16-217">このプロパティは、情報提供およびベンチマークを目的としています。</span><span class="sxs-lookup"><span data-stu-id="37b16-217">This property is for informational and benchmarking purposes.</span></span>  
  
 `MapHandleAlgorithm`  
 <span data-ttu-id="37b16-218">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-218">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MaxRolapOrConditions`  
 <span data-ttu-id="37b16-219">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-219">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `UseCalculationCacheRegistry`  
 <span data-ttu-id="37b16-220">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-220">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `UseDataCacheFreeLastPageMemory`  
 <span data-ttu-id="37b16-221">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-221">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `UseDataCacheRegistry`  
 <span data-ttu-id="37b16-222">データ キャッシュ レジストリを有効にするかどうかを指定するブール型プロパティです。ここでは、計算された結果ではなく、クエリ結果がキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="37b16-222">A Boolean property that specifies whether to enable the data cache registry, where query results are cached (though not calculated results).</span></span>  
  
 `UseDataCacheRegistryHashTable`  
 <span data-ttu-id="37b16-223">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-223">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `UseDataCacheRegistryMultiplyKey`  
 <span data-ttu-id="37b16-224">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-224">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `UseDataSlice`  
 <span data-ttu-id="37b16-225">クエリ最適化の実行時にパーティション データ スライスを使用するかどうかを定義するブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-225">A Boolean property that defines whether to use partition data slices at runtime for query optimization.</span></span> <span data-ttu-id="37b16-226">このプロパティは、ベンチマークおよび情報提供を目的としています。</span><span class="sxs-lookup"><span data-stu-id="37b16-226">This property is for benchmarking and informational purposes.</span></span>  
  
 `UseMaterializedIterators`  
 <span data-ttu-id="37b16-227">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-227">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `UseSinglePassForDimSecurityAutoExist`  
 <span data-ttu-id="37b16-228">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-228">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `UseVBANet`  
 <span data-ttu-id="37b16-229">ユーザー定義関数に VBA .net アセンブリを使用するかどうかを定義するブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="37b16-229">A Boolean property that defines whether to use the VBA .net assembly for user-defined functions.</span></span>  
  
 `CalculationPrefetchLocality\ ApplyIntersect`  
 <span data-ttu-id="37b16-230">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-230">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `CalculationPrefetchLocality\ ApplySubtract`  
 <span data-ttu-id="37b16-231">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-231">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `CalculationPrefetchLocality\ PrefetchLowerGranularities`  
 <span data-ttu-id="37b16-232">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-232">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\  CachedPageAlloc\ Income`  
 <span data-ttu-id="37b16-233">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-233">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\  CachedPageAlloc\ InitialBonus`  
 <span data-ttu-id="37b16-234">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-234">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\  CachedPageAlloc\ MaximumBalance`  
 <span data-ttu-id="37b16-235">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-235">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\  CachedPageAlloc\ MinimumBalance`  
 <span data-ttu-id="37b16-236">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-236">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\  CachedPageAlloc\ Tax`  
 <span data-ttu-id="37b16-237">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-237">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\CellStore\ Income`  
 <span data-ttu-id="37b16-238">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-238">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\CellStore\ InitialBonus`  
 <span data-ttu-id="37b16-239">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-239">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\CellStore\ MaximumBalance`  
 <span data-ttu-id="37b16-240">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-240">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\CellStore\ MinimumBalance`  
 <span data-ttu-id="37b16-241">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-241">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\CellStore\ Tax`  
 <span data-ttu-id="37b16-242">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-242">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\ MemoryModel \ Income`  
 <span data-ttu-id="37b16-243">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-243">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\ MemoryModel \ InitialBonus`  
 <span data-ttu-id="37b16-244">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-244">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\ MemoryModel \ MaximumBalance`  
 <span data-ttu-id="37b16-245">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-245">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\ MemoryModel \ MinimumBalance`  
 <span data-ttu-id="37b16-246">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-246">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\ MemoryModel\ Tax`  
 <span data-ttu-id="37b16-247">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-247">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="jobs"></a><span data-ttu-id="37b16-248">ジョブ</span><span class="sxs-lookup"><span data-stu-id="37b16-248">Jobs</span></span>  
 `ProcessAggregation\ MemoryModel\ Income`  
 <span data-ttu-id="37b16-249">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-249">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ MemoryModel\ InitialBonus`  
 <span data-ttu-id="37b16-250">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-250">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ MemoryModel\ MaximumBalance`  
 <span data-ttu-id="37b16-251">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-251">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ MemoryModel\ MinimumBalance`  
 <span data-ttu-id="37b16-252">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-252">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ MemoryModel\ Tax`  
 <span data-ttu-id="37b16-253">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-253">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ ProcessPartition\ Income`  
 <span data-ttu-id="37b16-254">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-254">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ ProcessPartition \ InitialBonus`  
 <span data-ttu-id="37b16-255">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-255">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ ProcessPartition \ MaximumBalance`  
 <span data-ttu-id="37b16-256">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-256">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ ProcessPartition \ MinimumBalance`  
 <span data-ttu-id="37b16-257">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-257">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ ProcessPartition \ Tax`  
 <span data-ttu-id="37b16-258">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-258">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ ProcessProperty\ Income`  
 <span data-ttu-id="37b16-259">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-259">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ ProcessProperty\ InitialBonus`  
 <span data-ttu-id="37b16-260">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-260">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ ProcessProperty\ MaximumBalance`  
 <span data-ttu-id="37b16-261">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-261">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ ProcessProperty\ MinimumBalance`  
 <span data-ttu-id="37b16-262">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-262">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ ProcessProperty\ Tax`  
 <span data-ttu-id="37b16-263">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="37b16-263">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37b16-264">参照</span><span class="sxs-lookup"><span data-stu-id="37b16-264">See Also</span></span>  
 <span data-ttu-id="37b16-265">[Analysis Services でのサーバープロパティの構成](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="37b16-265">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="37b16-266">Analysis Services インスタンスのサーバー モードの決定</span><span class="sxs-lookup"><span data-stu-id="37b16-266">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
