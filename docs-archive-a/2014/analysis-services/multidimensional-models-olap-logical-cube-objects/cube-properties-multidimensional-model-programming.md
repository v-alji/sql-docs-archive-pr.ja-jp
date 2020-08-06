---
title: キューブのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Collation property
- ID property
- ErrorConfiguration property
- cubes [Analysis Services], properties
- Description property
- DefaultMeasure property
- ProcessingMode property
- AggregationPrefix property
- EstimatedRows property
- Visible property
- StorageLocation property
- StorageMode property
- ScriptErrorHandlingMode property
- Source property
- ScriptCacheProcessingMode property
- Language property
- Name property
- properties [Analysis Services], cubes
- ProcessingPriority property
- ProactiveCaching property
ms.assetid: 72ca3387-620d-4473-8e23-7fe1f2b3d5bf
author: minewiskan
ms.author: owend
ms.openlocfilehash: 27d4202774107795eaddf76c27e21010d534d977
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632768"
---
# <a name="cube-properties"></a><span data-ttu-id="147e1-102">キューブ プロパティ</span><span class="sxs-lookup"><span data-stu-id="147e1-102">Cube Properties</span></span>
  <span data-ttu-id="147e1-103">キューブには、キューブ全体の動作に影響するように設定できる多数のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="147e1-103">Cubes have a number of properties that you can set to affect cube-wide behavior.</span></span> <span data-ttu-id="147e1-104">次の表は、これらのプロパティについてまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="147e1-104">These properties are summarized in the following table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="147e1-105">キューブの作成時に自動的に設定され、変更できないプロパティもあります。</span><span class="sxs-lookup"><span data-stu-id="147e1-105">Some properties are set automatically when the cube is created and cannot be changed.</span></span>  
  
 <span data-ttu-id="147e1-106">キューブのプロパティを設定する方法の詳細については、「[キューブデザイナー &#40;Analysis Services-多次元データ&#41;](../cube-designer-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="147e1-106">For more information about how to set cube properties, see [Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](../cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
|<span data-ttu-id="147e1-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="147e1-107">Property</span></span>|<span data-ttu-id="147e1-108">説明</span><span class="sxs-lookup"><span data-stu-id="147e1-108">Description</span></span>|  
|--------------|-----------------|  
|`AggregationPrefix`|<span data-ttu-id="147e1-109">集計名に使用する共通のプレフィックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="147e1-109">Specifies the common prefix that is used for aggregation names.</span></span>|  
|`Collation`|<span data-ttu-id="147e1-110">Latin1_General_C1_AS のように、アンダースコアで区切られたロケール識別子 (LCID) と比較フラグを指定します。</span><span class="sxs-lookup"><span data-stu-id="147e1-110">Specifies the locale identifier (LCID) and the comparison flag, separated by an underscore: for example, Latin1_General_C1_AS.</span></span>|  
|`DefaultMeasure`|<span data-ttu-id="147e1-111">キューブの既定のメジャーを定義する多次元式 (MDX) 式を保持します。</span><span class="sxs-lookup"><span data-stu-id="147e1-111">Contains a Multidimensional Expressions (MDX) expression that defines the default measure for the cube.</span></span>|  
|`Description`|<span data-ttu-id="147e1-112">キューブの説明を指定します。クライアント アプリケーションに公開できます。</span><span class="sxs-lookup"><span data-stu-id="147e1-112">Provides a description of the cube, which may be exposed in client applications.</span></span>|  
|`ErrorConfiguration`|<span data-ttu-id="147e1-113">重複するキー、不明なキー、エラーの制限、エラー検出時のアクション、エラー ログ ファイル、および NULL キーを処理するための、構成可能なエラー処理設定を保持します。</span><span class="sxs-lookup"><span data-stu-id="147e1-113">Contains configurable error handling settings for handling of duplicate keys, unknown keys, error limits, action upon error detection, error log file, and null key handling.</span></span>|  
|`EstimatedRows`|<span data-ttu-id="147e1-114">キューブ内の予測行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="147e1-114">Specifies the number of estimated rows in the cube.</span></span>|  
|`ID`|<span data-ttu-id="147e1-115">キューブの一意識別子 (ID) を保持します。</span><span class="sxs-lookup"><span data-stu-id="147e1-115">Contains the unique identifier (ID) of the cube.</span></span>|  
|`Language`|<span data-ttu-id="147e1-116">キューブの既定の言語識別子を指定します。</span><span class="sxs-lookup"><span data-stu-id="147e1-116">Specifies the default language identifier of the cube.</span></span>|  
|`Name`|<span data-ttu-id="147e1-117">キューブの表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="147e1-117">Specifies the user-friendly name of the cube.</span></span>|  
|`ProactiveCaching`|<span data-ttu-id="147e1-118">キューブのプロアクティブ キャッシュ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="147e1-118">Defines proactive cache settings for the cube.</span></span>|  
|`ProcessingMode`|<span data-ttu-id="147e1-119">インデックス作成と集計を処理中に行うか、処理後に行うかを指定します。</span><span class="sxs-lookup"><span data-stu-id="147e1-119">Indicates whether indexing and aggregating should occur during or after processing.</span></span> <span data-ttu-id="147e1-120">オプションは、**標準**または `lazy` です。</span><span class="sxs-lookup"><span data-stu-id="147e1-120">Options are **regular** or `lazy`.</span></span>|  
|`ProcessingPriority`|<span data-ttu-id="147e1-121">レイジー集計やインデックス作成など、バックグラウンド操作中のキューブの処理の優先度を決定します。</span><span class="sxs-lookup"><span data-stu-id="147e1-121">Determines the processing priority of the cube during background operations, such as lazy aggregations and indexing.</span></span> <span data-ttu-id="147e1-122">既定値は**0**です。</span><span class="sxs-lookup"><span data-stu-id="147e1-122">The default value is **0**.</span></span>|  
|`ScriptCacheProcessingMode`|<span data-ttu-id="147e1-123">スクリプト キャッシュのビルドを処理中に行うか、処理後に行うかを指定します。</span><span class="sxs-lookup"><span data-stu-id="147e1-123">Indicates whether the script cache should be built during or after processing.</span></span> <span data-ttu-id="147e1-124">オプションは、 **regular**および `lazy` です。</span><span class="sxs-lookup"><span data-stu-id="147e1-124">Options are **regular** and `lazy`.</span></span>|  
|`ScriptErrorHandlingMode`|<span data-ttu-id="147e1-125">エラー処理を決定します。</span><span class="sxs-lookup"><span data-stu-id="147e1-125">Determines error handling.</span></span> <span data-ttu-id="147e1-126">オプションは `IgnoreNone` またはです。`IgnoreAll`</span><span class="sxs-lookup"><span data-stu-id="147e1-126">Options are `IgnoreNone` or `IgnoreAll`</span></span>|  
|`Source`|<span data-ttu-id="147e1-127">キューブに使用するデータ ソース ビューを表示します。</span><span class="sxs-lookup"><span data-stu-id="147e1-127">Displays the data source view used for the cube.</span></span>|  
|`StorageLocation`|<span data-ttu-id="147e1-128">キューブのファイル システムでのストレージ場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="147e1-128">Specifies the file system storage location for the cube.</span></span> <span data-ttu-id="147e1-129">指定しない場合は、キューブ オブジェクトが含まれているデータベースから場所が継承されます。</span><span class="sxs-lookup"><span data-stu-id="147e1-129">If none is specified, the location is inherited from the database that contains the cube object.</span></span>|  
|`StorageMode`|<span data-ttu-id="147e1-130">キューブのストレージ モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="147e1-130">Specifies the storage mode for the cube.</span></span> <span data-ttu-id="147e1-131">値は `MOLAP` 、、 `ROLAP` またはです。`HOLAP``.`</span><span class="sxs-lookup"><span data-stu-id="147e1-131">Values are `MOLAP`, `ROLAP`, or `HOLAP``.`</span></span>|  
|`Visible`|<span data-ttu-id="147e1-132">キューブを表示するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="147e1-132">Determines the visibility of the cube.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="147e1-133">Null 値やその他のデータの整合性の問題を扱う場合の ErrorConfiguration プロパティの値の設定の詳細については、「 [Analysis Services 2005 でのデータ整合性の問題の処理](https://go.microsoft.com/fwlink/?LinkId=81891)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="147e1-133">For more information about setting values for the ErrorConfiguration property when working with null values and other data integrity issues, see [Handling Data Integrity Issues in Analysis Services 2005](https://go.microsoft.com/fwlink/?LinkId=81891).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="147e1-134">参照</span><span class="sxs-lookup"><span data-stu-id="147e1-134">See Also</span></span>  
 [<span data-ttu-id="147e1-135">&#40;パーティションのプロアクティブキャッシュ&#41;</span><span class="sxs-lookup"><span data-stu-id="147e1-135">Proactive Caching &#40;Partitions&#41;</span></span>](partitions-proactive-caching.md)  
  
  
