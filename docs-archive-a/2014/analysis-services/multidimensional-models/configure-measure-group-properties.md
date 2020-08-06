---
title: メジャーグループのプロパティの構成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- properties [Analysis Services], measure groups
ms.assetid: fa66bdb6-60b8-413c-ac2a-00e4d09f60a2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 03dad3d8ee33ea8a78b08f9a354d0db3d177198c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737111"
---
# <a name="configure-measure-group-properties"></a><span data-ttu-id="73b37-102">メジャー グループのプロパティの構成</span><span class="sxs-lookup"><span data-stu-id="73b37-102">Configure Measure Group Properties</span></span>
  <span data-ttu-id="73b37-103">メジャー グループには、メジャー グループの動作を定義できるプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="73b37-103">Measures groups have properties that enable you to define how measure groups function.</span></span>  
  
## <a name="measure-group-properties"></a><span data-ttu-id="73b37-104">メジャー グループのプロパティ</span><span class="sxs-lookup"><span data-stu-id="73b37-104">Measure Group Properties</span></span>  
 <span data-ttu-id="73b37-105">メジャー グループのプロパティは、メジャー グループ全体の動作を指定し、メジャー グループ内のメジャーの特定プロパティの既定の動作を決定します。</span><span class="sxs-lookup"><span data-stu-id="73b37-105">Measure group properties determine behaviors for the entire measure group and set the default behaviors for certain properties of measures within a measure group.</span></span>  
  
|<span data-ttu-id="73b37-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="73b37-106">Property</span></span>|<span data-ttu-id="73b37-107">定義</span><span class="sxs-lookup"><span data-stu-id="73b37-107">Definition</span></span>|  
|--------------|----------------|  
|`AggregationPrefix`|<span data-ttu-id="73b37-108">ROLAP ストレージに適用されます。</span><span class="sxs-lookup"><span data-stu-id="73b37-108">Applies to ROLAP storage.</span></span> <span data-ttu-id="73b37-109">このメジャー グループに関連付けられているパーティションの集計の格納に使用する SQL Server のインデックス付きビューに、共通のプレフィックスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="73b37-109">Assigns a common prefix to the indexed views in SQL Server, used to store aggregations for the partitions associated with this measure group.</span></span>|  
|`DataAggregation`|<span data-ttu-id="73b37-110">このプロパティは、将来使用するために予約済みであり、現在のところ何も効果がありません。</span><span class="sxs-lookup"><span data-stu-id="73b37-110">This property is reserved for future use and currently has no effect.</span></span> <span data-ttu-id="73b37-111">そのため、この設定を変更しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="73b37-111">Therefore, it is recommended that you do not modify this setting.</span></span>|  
|`Description`|<span data-ttu-id="73b37-112">このプロパティを使用すると、メジャー グループを文書化することができます。</span><span class="sxs-lookup"><span data-stu-id="73b37-112">You can use this property to document the measure group.</span></span>|  
|`ErrorConfiguration`|<span data-ttu-id="73b37-113">重複するキー、不明なキー、NULL キー、エラーの制限、エラー検出時のアクション、およびエラー ログ ファイルを処理するための、構成可能なエラー処理設定です。</span><span class="sxs-lookup"><span data-stu-id="73b37-113">Configurable error handling settings for handling of duplicate keys, unknown keys, null keys, error limits, action upon error detection, and the error log file.</span></span> <span data-ttu-id="73b37-114">「[キューブ、パーティション、およびディメンションに関する処理のエラー構成 &#40;SSAS - 多次元&#41;](error-configuration-for-cube-partition-and-dimension-processing.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="73b37-114">See [Error Configuration for Cube, Partition, and Dimension Processing &#40;SSAS - Multidimensional&#41;](error-configuration-for-cube-partition-and-dimension-processing.md).</span></span>|  
|`EstimatedRows`|<span data-ttu-id="73b37-115">ファクト テーブルの推定行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="73b37-115">Specifies the estimated number of rows in the fact table.</span></span>|  
|`EstimatedSize`|<span data-ttu-id="73b37-116">メジャー グループの推定サイズを指定します (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="73b37-116">Specifies the estimated size (in bytes) of the measure group.</span></span>|  
|`ID`|<span data-ttu-id="73b37-117">オブジェクト識別子を指定します。</span><span class="sxs-lookup"><span data-stu-id="73b37-117">Specifies the identifier of the object.</span></span>|  
|`IgnoreUnrelatedDimensions`|<span data-ttu-id="73b37-118">メジャー グループに関連付けられていないディメンションのメンバーがクエリに含まれているときに、関連付けられていないディメンションをトップ レベルに強制するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="73b37-118">Determines whether unrelated dimensions are forced to their top level when members of dimensions that are unrelated to the measure group are included in a query.</span></span> <span data-ttu-id="73b37-119">既定の設定は `True` です。</span><span class="sxs-lookup"><span data-stu-id="73b37-119">Default setting is `True`.</span></span>|  
|`Name`|<span data-ttu-id="73b37-120">メジャーの名前。</span><span class="sxs-lookup"><span data-stu-id="73b37-120">Name of the measure.</span></span> <span data-ttu-id="73b37-121">このプロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="73b37-121">This property is read-only.</span></span>|  
|`ProactiveCaching`|<span data-ttu-id="73b37-122">重複するキー、不明なキー、NULL キー、エラーの制限、エラー検出時のアクション、およびエラー ログ ファイルを処理するための、構成可能なエラー処理設定です。</span><span class="sxs-lookup"><span data-stu-id="73b37-122">Configurable error handling settings for handling of duplicate keys, unknown keys, null keys, error limits, action upon error detection, and the error log file.</span></span>|  
|`ProcessingMode`|<span data-ttu-id="73b37-123">インデックス作成と集計を処理中に行うか、処理後に行うかを指定します。</span><span class="sxs-lookup"><span data-stu-id="73b37-123">Indicates whether indexing and aggregating should occur during or after processing.</span></span> <span data-ttu-id="73b37-124">オプションは Regular または LazyAggregations です。</span><span class="sxs-lookup"><span data-stu-id="73b37-124">Options are Regular and LazyAggregations.</span></span> <span data-ttu-id="73b37-125">LazyAggregations を使用すると、バック グラウンド タスクとして集計を実行できます。</span><span class="sxs-lookup"><span data-stu-id="73b37-125">LazyAggregations can be used to run aggregation as a background task.</span></span>|  
|`ProcessingPriority`|<span data-ttu-id="73b37-126">レイジー集計やインデックス作成など、バックグラウンド操作中のキューブの処理の優先度を決定します。</span><span class="sxs-lookup"><span data-stu-id="73b37-126">Determines the processing priority of the cube during background operations, such as lazy aggregations and indexing.</span></span> <span data-ttu-id="73b37-127">既定値は**0**です。</span><span class="sxs-lookup"><span data-stu-id="73b37-127">The default value is **0**.</span></span>|  
|`StorageLocation`|<span data-ttu-id="73b37-128">メジャー グループのファイル システム ストレージの場所です。</span><span class="sxs-lookup"><span data-stu-id="73b37-128">The file system storage location for the measure group.</span></span> <span data-ttu-id="73b37-129">指定しなければ、ストレージの場所はメジャー グループが含まれているキューブから継承されます。</span><span class="sxs-lookup"><span data-stu-id="73b37-129">If none is specified, the location is inherited from the cube that contains the measure group.</span></span>|  
|`StorageMode`|<span data-ttu-id="73b37-130">メジャー グループのストレージ モードです。</span><span class="sxs-lookup"><span data-stu-id="73b37-130">The storage mode for the measure group.</span></span> <span data-ttu-id="73b37-131">使用できる値は MOLAP、ROLAP、または HOLAP です。</span><span class="sxs-lookup"><span data-stu-id="73b37-131">Available values are MOLAP, ROLAP, or HOLAP.</span></span>|  
|`Type`|<span data-ttu-id="73b37-132">メジャー グループの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="73b37-132">Specifies the type of the measure group.</span></span>|  
  
  
