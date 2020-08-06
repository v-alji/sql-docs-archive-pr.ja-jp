---
title: TuningOptions 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TuningOptions element
ms.assetid: 58a22ba1-8e03-411f-bd46-85e4540f217a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2fab1c55c9d036424142b2692e8335ea65c22340
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720624"
---
# <a name="tuningoptions-element-dta"></a><span data-ttu-id="2dac1-102">TuningOptions 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="2dac1-102">TuningOptions Element (DTA)</span></span>
  <span data-ttu-id="2dac1-103">特定のチューニング セッションのチューニング オプションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2dac1-103">Contains the tuning options for a specific tuning session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dac1-104">構文</span><span class="sxs-lookup"><span data-stu-id="2dac1-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="2dac1-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="2dac1-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="2dac1-106">特徴</span><span class="sxs-lookup"><span data-stu-id="2dac1-106">Characteristic</span></span>|<span data-ttu-id="2dac1-107">説明</span><span class="sxs-lookup"><span data-stu-id="2dac1-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="2dac1-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="2dac1-108">**Data type and length**</span></span>|<span data-ttu-id="2dac1-109">[なし] :</span><span class="sxs-lookup"><span data-stu-id="2dac1-109">None.</span></span>|  
|<span data-ttu-id="2dac1-110">**既定値**</span><span class="sxs-lookup"><span data-stu-id="2dac1-110">**Default value**</span></span>|<span data-ttu-id="2dac1-111">[なし] :</span><span class="sxs-lookup"><span data-stu-id="2dac1-111">None.</span></span>|  
|<span data-ttu-id="2dac1-112">**個数**</span><span class="sxs-lookup"><span data-stu-id="2dac1-112">**Occurrence**</span></span>|<span data-ttu-id="2dac1-113">省略可能。</span><span class="sxs-lookup"><span data-stu-id="2dac1-113">Optional.</span></span> <span data-ttu-id="2dac1-114">使用する場合は、`DTAInput` 要素につき 1 回使用できます。</span><span class="sxs-lookup"><span data-stu-id="2dac1-114">If used, can only be used once for each `DTAInput` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="2dac1-115">要素の関係</span><span class="sxs-lookup"><span data-stu-id="2dac1-115">Element Relationships</span></span>  
  
|<span data-ttu-id="2dac1-116">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="2dac1-116">Relationship</span></span>|<span data-ttu-id="2dac1-117">要素</span><span class="sxs-lookup"><span data-stu-id="2dac1-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="2dac1-118">**親要素**</span><span class="sxs-lookup"><span data-stu-id="2dac1-118">**Parent element**</span></span>|[<span data-ttu-id="2dac1-119">DTAInput 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="2dac1-119">DTAInput Element &#40;DTA&#41;</span></span>](dtainput-element-dta.md)|  
|<span data-ttu-id="2dac1-120">**子要素**</span><span class="sxs-lookup"><span data-stu-id="2dac1-120">**Child elements**</span></span>|<span data-ttu-id="2dac1-121">`ReportSet` 要素。</span><span class="sxs-lookup"><span data-stu-id="2dac1-121">`ReportSet` element.</span></span> <span data-ttu-id="2dac1-122">詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](https://go.microsoft.com/fwlink/?linkid=43100)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2dac1-122">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> <span data-ttu-id="2dac1-123">`TuningLogTable` 要素。</span><span class="sxs-lookup"><span data-stu-id="2dac1-123">`TuningLogTable` element.</span></span> <span data-ttu-id="2dac1-124">詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](https://go.microsoft.com/fwlink/?linkid=43100)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2dac1-124">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> <span data-ttu-id="2dac1-125">`NumberOfEvents` 要素。</span><span class="sxs-lookup"><span data-stu-id="2dac1-125">`NumberOfEvents` element.</span></span> <span data-ttu-id="2dac1-126">詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](https://go.microsoft.com/fwlink/?linkid=43100)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2dac1-126">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> [<span data-ttu-id="2dac1-127">TuningTimeInMin 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="2dac1-127">TuningTimeInMin Element &#40;DTA&#41;</span></span>](tuningtimeinmin-element-dta.md)<br /><br /> [<span data-ttu-id="2dac1-128">StorageBoundInMB 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="2dac1-128">StorageBoundInMB Element &#40;DTA&#41;</span></span>](storageboundinmb-element-dta.md)<br /><br /> <span data-ttu-id="2dac1-129">`MaxKeyColumnsInIndex` 要素。</span><span class="sxs-lookup"><span data-stu-id="2dac1-129">`MaxKeyColumnsInIndex` element.</span></span> <span data-ttu-id="2dac1-130">詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](https://go.microsoft.com/fwlink/?linkid=43100)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2dac1-130">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> <span data-ttu-id="2dac1-131">`MaxColumnsInIndex` 要素。</span><span class="sxs-lookup"><span data-stu-id="2dac1-131">`MaxColumnsInIndex` element.</span></span> <span data-ttu-id="2dac1-132">詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](https://go.microsoft.com/fwlink/?linkid=43100)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2dac1-132">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> <span data-ttu-id="2dac1-133">`MinPercentageImprovement` 要素。</span><span class="sxs-lookup"><span data-stu-id="2dac1-133">`MinPercentageImprovement` element.</span></span> <span data-ttu-id="2dac1-134">詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](https://go.microsoft.com/fwlink/?linkid=43100)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2dac1-134">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100)</span></span><br /><br /> [<span data-ttu-id="2dac1-135">TestServer 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="2dac1-135">TestServer Element &#40;DTA&#41;</span></span>](server-element-dta.md)<br /><br /> [<span data-ttu-id="2dac1-136">FeatureSet 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="2dac1-136">FeatureSet Element &#40;DTA&#41;</span></span>](featureset-element-dta.md)<br /><br /> [<span data-ttu-id="2dac1-137">Partitioning 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="2dac1-137">Partitioning Element &#40;DTA&#41;</span></span>](partitioning-element-dta.md)<br /><br /> [<span data-ttu-id="2dac1-138">DropOnlyMode 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="2dac1-138">DropOnlyMode Element &#40;DTA&#41;</span></span>](droponlymode-element-dta.md)<br /><br /> [<span data-ttu-id="2dac1-139">KeepExisting 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="2dac1-139">KeepExisting Element &#40;DTA&#41;</span></span>](keepexisting-element-dta.md)<br /><br /> [<span data-ttu-id="2dac1-140">OnlineIndexOperation 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="2dac1-140">OnlineIndexOperation Element &#40;DTA&#41;</span></span>](onlineindexoperation-element-dta.md)<br /><br /> [<span data-ttu-id="2dac1-141">DatabaseToConnect 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="2dac1-141">DatabaseToConnect Element &#40;DTA&#41;</span></span>](databasetoconnect-element-dta.md)<br /><br /> <span data-ttu-id="2dac1-142">`IgnoreConstantsInWorkload` 要素。</span><span class="sxs-lookup"><span data-stu-id="2dac1-142">`IgnoreConstantsInWorkload` element.</span></span> <span data-ttu-id="2dac1-143">詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](https://go.microsoft.com/fwlink/?linkid=43100)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2dac1-143">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> <span data-ttu-id="2dac1-144">`RetainShellDB` 要素。</span><span class="sxs-lookup"><span data-stu-id="2dac1-144">`RetainShellDB` element.</span></span> <span data-ttu-id="2dac1-145">詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](https://go.microsoft.com/fwlink/?linkid=43100)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2dac1-145">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2dac1-146">例</span><span class="sxs-lookup"><span data-stu-id="2dac1-146">Example</span></span>  
 <span data-ttu-id="2dac1-147">要素の例につい `TuningOptions` ては、「 [XML 入力ファイルのサンプル &#40;DTA&#41;](xml-input-file-samples-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2dac1-147">For examples of the `TuningOptions` element, see the [XML Input File Samples &#40;DTA&#41;](xml-input-file-samples-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dac1-148">参照</span><span class="sxs-lookup"><span data-stu-id="2dac1-148">See Also</span></span>  
 [<span data-ttu-id="2dac1-149">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="2dac1-149">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
