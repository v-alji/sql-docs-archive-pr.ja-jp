---
title: FeatureSet 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- FeatureSet element
ms.assetid: f2070c53-4a5c-4c11-ac38-96ee200c84f0
author: stevestein
ms.author: sstein
ms.openlocfilehash: d36c28b24a56ef2dcdf69578fb7e8c196306a416
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737285"
---
# <a name="featureset-element-dta"></a><span data-ttu-id="f544b-102">FeatureSet 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="f544b-102">FeatureSet Element (DTA)</span></span>
  <span data-ttu-id="f544b-103">データベース エンジン チューニング アドバイザーでの分析時に使用する物理設計構造 (インデックス、インデックス付きビュー) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f544b-103">Contains the physical design structures (indexes or indexed views) that you would like Database Engine Tuning Advisor to use during analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f544b-104">構文</span><span class="sxs-lookup"><span data-stu-id="f544b-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <FeatureSet>...</FeatureSet>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="f544b-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="f544b-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="f544b-106">特徴</span><span class="sxs-lookup"><span data-stu-id="f544b-106">Characteristic</span></span>|<span data-ttu-id="f544b-107">説明</span><span class="sxs-lookup"><span data-stu-id="f544b-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="f544b-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="f544b-108">**Data type and length**</span></span>|<span data-ttu-id="f544b-109">`string`。最大長はありません。</span><span class="sxs-lookup"><span data-stu-id="f544b-109">`string`, no maximum length.</span></span>|  
|<span data-ttu-id="f544b-110">**指定できる値**</span><span class="sxs-lookup"><span data-stu-id="f544b-110">**Allowed values**</span></span>|<span data-ttu-id="f544b-111">**IDX_IV**</span><span class="sxs-lookup"><span data-stu-id="f544b-111">**IDX_IV**</span></span><br /> <span data-ttu-id="f544b-112">インデックスおよびインデックス付きビュー。</span><span class="sxs-lookup"><span data-stu-id="f544b-112">Indexes and indexed views.</span></span><br /><br /> <span data-ttu-id="f544b-113">**IDX**</span><span class="sxs-lookup"><span data-stu-id="f544b-113">**IDX**</span></span><br /> <span data-ttu-id="f544b-114">インデックスのみ。</span><span class="sxs-lookup"><span data-stu-id="f544b-114">Indexes only.</span></span><br /><br /> <span data-ttu-id="f544b-115">**IV**</span><span class="sxs-lookup"><span data-stu-id="f544b-115">**IV**</span></span><br /> <span data-ttu-id="f544b-116">インデックス付きビューのみ。</span><span class="sxs-lookup"><span data-stu-id="f544b-116">Indexed views only.</span></span><br /><br /> <span data-ttu-id="f544b-117">**NCL_IDX**</span><span class="sxs-lookup"><span data-stu-id="f544b-117">**NCL_IDX**</span></span><br /> <span data-ttu-id="f544b-118">非クラスター化インデックスのみ。</span><span class="sxs-lookup"><span data-stu-id="f544b-118">Nonclustered indexes only.</span></span><br /><br /> <span data-ttu-id="f544b-119">この要素では、上記の値のいずれか 1 つを使用してください。</span><span class="sxs-lookup"><span data-stu-id="f544b-119">Use one of these values with this element.</span></span>|  
|<span data-ttu-id="f544b-120">**既定値**</span><span class="sxs-lookup"><span data-stu-id="f544b-120">**Default value**</span></span>|<span data-ttu-id="f544b-121">**IDX**</span><span class="sxs-lookup"><span data-stu-id="f544b-121">**IDX**</span></span>|  
|<span data-ttu-id="f544b-122">**個数**</span><span class="sxs-lookup"><span data-stu-id="f544b-122">**Occurrence**</span></span>|<span data-ttu-id="f544b-123">要素 `TuningOptions` が使用されている場合を除き、各要素につき1回の出現が必要です `DropOnlyMode` 。</span><span class="sxs-lookup"><span data-stu-id="f544b-123">Required once for each `TuningOptions` element, unless the `DropOnlyMode` element is used.</span></span> <span data-ttu-id="f544b-124">`DropOnlyMode` を使用している場合は、`FeatureSet` を使用できません。</span><span class="sxs-lookup"><span data-stu-id="f544b-124">If `DropOnlyMode` is used, you cannot use `FeatureSet`.</span></span> <span data-ttu-id="f544b-125">これらの要素を同時に指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="f544b-125">These elements are mutually exclusive.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="f544b-126">要素の関係</span><span class="sxs-lookup"><span data-stu-id="f544b-126">Element Relationships</span></span>  
  
|<span data-ttu-id="f544b-127">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="f544b-127">Relationship</span></span>|<span data-ttu-id="f544b-128">要素</span><span class="sxs-lookup"><span data-stu-id="f544b-128">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="f544b-129">**親要素**</span><span class="sxs-lookup"><span data-stu-id="f544b-129">**Parent element**</span></span>|[<span data-ttu-id="f544b-130">TuningOptions 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="f544b-130">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="f544b-131">**子要素**</span><span class="sxs-lookup"><span data-stu-id="f544b-131">**Child elements**</span></span>|<span data-ttu-id="f544b-132">[なし] :</span><span class="sxs-lookup"><span data-stu-id="f544b-132">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f544b-133">例</span><span class="sxs-lookup"><span data-stu-id="f544b-133">Example</span></span>  
 <span data-ttu-id="f544b-134">この要素の使用例については、「[XML 入力ファイルの簡単なサンプル &#40;DTA&#41;](simple-xml-input-file-sample-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f544b-134">For a usage example of this element, see the [Simple XML Input File Sample &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f544b-135">参照</span><span class="sxs-lookup"><span data-stu-id="f544b-135">See Also</span></span>  
 [<span data-ttu-id="f544b-136">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="f544b-136">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
