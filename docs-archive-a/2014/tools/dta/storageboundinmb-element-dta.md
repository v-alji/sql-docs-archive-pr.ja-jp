---
title: StorageBoundInMB 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- StorageBoundInMB element
ms.assetid: a8374910-bf68-4edb-b464-53a3a705e7f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: ea49b0af981b8f8d96efb087033d8f1466364c76
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720666"
---
# <a name="storageboundinmb-element-dta"></a><span data-ttu-id="8c2a6-102">StorageBoundInMB 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="8c2a6-102">StorageBoundInMB Element (DTA)</span></span>
  <span data-ttu-id="8c2a6-103">データベース エンジン チューニング アドバイザーのチューニング推奨設定 (インデックスとパーティション分割のセット) で使用できる最大容量を MB 単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="8c2a6-103">Specifies the maximum space in megabytes that can be consumed by the Database Engine Tuning Advisor tuning recommendation (index and partitioning set).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c2a6-104">構文</span><span class="sxs-lookup"><span data-stu-id="8c2a6-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <StorageBoundInMB>...</ StorageBoundInMB >  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="8c2a6-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="8c2a6-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="8c2a6-106">特徴</span><span class="sxs-lookup"><span data-stu-id="8c2a6-106">Characteristic</span></span>|<span data-ttu-id="8c2a6-107">説明</span><span class="sxs-lookup"><span data-stu-id="8c2a6-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="8c2a6-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="8c2a6-108">**Data type and length**</span></span>|<span data-ttu-id="8c2a6-109">`unsignedInt`、長さは無制限です。</span><span class="sxs-lookup"><span data-stu-id="8c2a6-109">`unsignedInt`, unlimited length.</span></span>|  
|<span data-ttu-id="8c2a6-110">**既定値**</span><span class="sxs-lookup"><span data-stu-id="8c2a6-110">**Default value**</span></span>|<span data-ttu-id="8c2a6-111">[なし] :</span><span class="sxs-lookup"><span data-stu-id="8c2a6-111">None.</span></span>|  
|<span data-ttu-id="8c2a6-112">**個数**</span><span class="sxs-lookup"><span data-stu-id="8c2a6-112">**Occurrence**</span></span>|<span data-ttu-id="8c2a6-113">省略可能。</span><span class="sxs-lookup"><span data-stu-id="8c2a6-113">Optional.</span></span> <span data-ttu-id="8c2a6-114">`TuningOptions` 要素に 1 回だけ使用できます。</span><span class="sxs-lookup"><span data-stu-id="8c2a6-114">Can only be used once for the `TuningOptions` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="8c2a6-115">要素の関係</span><span class="sxs-lookup"><span data-stu-id="8c2a6-115">Element Relationships</span></span>  
  
|<span data-ttu-id="8c2a6-116">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="8c2a6-116">Relationship</span></span>|<span data-ttu-id="8c2a6-117">要素</span><span class="sxs-lookup"><span data-stu-id="8c2a6-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="8c2a6-118">**親要素**</span><span class="sxs-lookup"><span data-stu-id="8c2a6-118">**Parent element**</span></span>|[<span data-ttu-id="8c2a6-119">TuningOptions 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="8c2a6-119">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="8c2a6-120">**子要素**</span><span class="sxs-lookup"><span data-stu-id="8c2a6-120">**Child elements**</span></span>|<span data-ttu-id="8c2a6-121">なし</span><span class="sxs-lookup"><span data-stu-id="8c2a6-121">None</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c2a6-122">解説</span><span class="sxs-lookup"><span data-stu-id="8c2a6-122">Remarks</span></span>  
 <span data-ttu-id="8c2a6-123">複数のデータベースをチューニングする場合は、すべてのデータベースの推奨設定が容量計算の対象になります。</span><span class="sxs-lookup"><span data-stu-id="8c2a6-123">When multiple databases are tuned, recommendations for all databases are considered for the space calculation.</span></span> <span data-ttu-id="8c2a6-124">データベース エンジン チューニング アドバイザーは、既定で以下の記憶領域サイズのうちの小さい方を使用します。</span><span class="sxs-lookup"><span data-stu-id="8c2a6-124">By default, Database Engine Tuning Advisor assumes the smaller of the following storage sizes:</span></span>  
  
-   <span data-ttu-id="8c2a6-125">現在の生データのサイズの 3 倍 (テーブルのヒープとクラスター化インデックスの合計サイズも含まれる)</span><span class="sxs-lookup"><span data-stu-id="8c2a6-125">Three times the current raw data size, which includes the total size of heaps and clustered indexes on tables.</span></span>  
  
-   <span data-ttu-id="8c2a6-126">アタッチ先のすべてのディスク ドライブの空き容量に生データのサイズを加算した値</span><span class="sxs-lookup"><span data-stu-id="8c2a6-126">The free space on all attached disk drives plus the raw data size.</span></span>  
  
 <span data-ttu-id="8c2a6-127">既定の記憶領域サイズには、非クラスター化インデックスとインデックス付きビューは含まれません。</span><span class="sxs-lookup"><span data-stu-id="8c2a6-127">The default storage size does not include nonclustered indexes and indexed views.</span></span>  
  
 <span data-ttu-id="8c2a6-128">`StorageBoundInMB` 要素に指定した値が実際のディスク容量のサイズを超えている場合は、データベース エンジン チューニング アドバイザーからエラーが返されますが、チューニング自体は続行されます。</span><span class="sxs-lookup"><span data-stu-id="8c2a6-128">If the value specified for the `StorageBoundInMB` element exceeds the actual disk space, Database Engine Tuning Advisor returns an error, but continues tuning.</span></span> <span data-ttu-id="8c2a6-129">チューニングの完了後に、推奨設定を実装することにした場合はディスク容量を追加できます。</span><span class="sxs-lookup"><span data-stu-id="8c2a6-129">After tuning is complete, you can add disk space if you decide to implement the recommendation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c2a6-130">例</span><span class="sxs-lookup"><span data-stu-id="8c2a6-130">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="8c2a6-131">説明</span><span class="sxs-lookup"><span data-stu-id="8c2a6-131">Description</span></span>  
 <span data-ttu-id="8c2a6-132">次のコード例では、チューニングの推奨設定で使用できる最大ディスク領域として 1500 MB の制限を設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8c2a6-132">The following code example shows how to set a limit of 1500 megabytes as the maximum disk space that a tuning recommendation can consume:</span></span>  
  
## <a name="code"></a><span data-ttu-id="8c2a6-133">コード</span><span class="sxs-lookup"><span data-stu-id="8c2a6-133">Code</span></span>  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <StorageBoundInMB>1500</StorageBoundInMB>  
...code removed here...  
</DTAInput>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c2a6-134">参照</span><span class="sxs-lookup"><span data-stu-id="8c2a6-134">See Also</span></span>  
 [<span data-ttu-id="8c2a6-135">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="8c2a6-135">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
