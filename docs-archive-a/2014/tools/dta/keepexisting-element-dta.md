---
title: KeepExisting 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- KeepExisting element
ms.assetid: e67aae61-d06d-4a03-85ba-6516c3502dce
author: stevestein
ms.author: sstein
ms.openlocfilehash: cde9b3091b75f55e4b9c79137853fbd7d4e0daf9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719232"
---
# <a name="keepexisting-element-dta"></a><span data-ttu-id="e6c57-102">KeepExisting 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="e6c57-102">KeepExisting Element (DTA)</span></span>
  <span data-ttu-id="e6c57-103">データベース エンジン チューニング アドバイザーが、推奨設定を生成するときに保持しなければならない物理設計構造 (インデックス、インデックス付きビュー、パーティション分割) を指定します。</span><span class="sxs-lookup"><span data-stu-id="e6c57-103">Specifies the physical design structures (indexes, indexed views, or partitioning) that Database Engine Tuning Advisor must retain when generating its recommendation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6c57-104">構文</span><span class="sxs-lookup"><span data-stu-id="e6c57-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <KeepExisting>...</KeepExisting>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="e6c57-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="e6c57-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="e6c57-106">特徴</span><span class="sxs-lookup"><span data-stu-id="e6c57-106">Characteristic</span></span>|<span data-ttu-id="e6c57-107">説明</span><span class="sxs-lookup"><span data-stu-id="e6c57-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e6c57-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="e6c57-108">**Data type and length**</span></span>|<span data-ttu-id="e6c57-109">`string`。長さの制限は、サーバーによって決まります。</span><span class="sxs-lookup"><span data-stu-id="e6c57-109">`string`, length limit enforced by the server.</span></span>|  
|<span data-ttu-id="e6c57-110">**指定できる値**</span><span class="sxs-lookup"><span data-stu-id="e6c57-110">**Allowed values**</span></span>|<span data-ttu-id="e6c57-111">**NONE**</span><span class="sxs-lookup"><span data-stu-id="e6c57-111">**NONE**</span></span><br /> <span data-ttu-id="e6c57-112">既存の構造を保持しません。</span><span class="sxs-lookup"><span data-stu-id="e6c57-112">No existing structures.</span></span><br /><br /> <span data-ttu-id="e6c57-113">**ALL**</span><span class="sxs-lookup"><span data-stu-id="e6c57-113">**ALL**</span></span><br /> <span data-ttu-id="e6c57-114">既存の構造をすべて保持します。</span><span class="sxs-lookup"><span data-stu-id="e6c57-114">All existing structures.</span></span><br /><br /> <span data-ttu-id="e6c57-115">**ALIGNED**</span><span class="sxs-lookup"><span data-stu-id="e6c57-115">**ALIGNED**</span></span><br /> <span data-ttu-id="e6c57-116">パーティションで固定された構造をすべて保持します。</span><span class="sxs-lookup"><span data-stu-id="e6c57-116">All partition-aligned structures.</span></span><br /><br /> <span data-ttu-id="e6c57-117">**CL_IDX**</span><span class="sxs-lookup"><span data-stu-id="e6c57-117">**CL_IDX**</span></span><br /> <span data-ttu-id="e6c57-118">テーブルのクラスター化インデックスをすべて保持します。</span><span class="sxs-lookup"><span data-stu-id="e6c57-118">All clustered indexes on tables.</span></span><br /><br /> <span data-ttu-id="e6c57-119">**IDX**</span><span class="sxs-lookup"><span data-stu-id="e6c57-119">**IDX**</span></span><br /> <span data-ttu-id="e6c57-120">テーブルのクラスター化インデックスと非クラスター化インデックスをすべて保持します。</span><span class="sxs-lookup"><span data-stu-id="e6c57-120">All clustered and nonclustered indexes on tables.</span></span><br /><br /> <span data-ttu-id="e6c57-121">この要素では、上記の値のいずれか 1 つを使用してください。</span><span class="sxs-lookup"><span data-stu-id="e6c57-121">Use only one of these values with this element.</span></span>|  
|<span data-ttu-id="e6c57-122">**既定値**</span><span class="sxs-lookup"><span data-stu-id="e6c57-122">**Default value**</span></span>|<span data-ttu-id="e6c57-123">[なし] :</span><span class="sxs-lookup"><span data-stu-id="e6c57-123">None.</span></span>|  
|<span data-ttu-id="e6c57-124">**個数**</span><span class="sxs-lookup"><span data-stu-id="e6c57-124">**Occurrence**</span></span>|<span data-ttu-id="e6c57-125">省略可能。</span><span class="sxs-lookup"><span data-stu-id="e6c57-125">Optional.</span></span> <span data-ttu-id="e6c57-126">`TuningOptions` 要素につき 1 回だけ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e6c57-126">Can use only once for each `TuningOptions` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="e6c57-127">要素の関係</span><span class="sxs-lookup"><span data-stu-id="e6c57-127">Element Relationships</span></span>  
  
|<span data-ttu-id="e6c57-128">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="e6c57-128">Relationship</span></span>|<span data-ttu-id="e6c57-129">要素</span><span class="sxs-lookup"><span data-stu-id="e6c57-129">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="e6c57-130">**親要素**</span><span class="sxs-lookup"><span data-stu-id="e6c57-130">**Parent element**</span></span>|[<span data-ttu-id="e6c57-131">TuningOptions 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="e6c57-131">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="e6c57-132">**子要素**</span><span class="sxs-lookup"><span data-stu-id="e6c57-132">**Child elements**</span></span>|<span data-ttu-id="e6c57-133">[なし] :</span><span class="sxs-lookup"><span data-stu-id="e6c57-133">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e6c57-134">例</span><span class="sxs-lookup"><span data-stu-id="e6c57-134">Example</span></span>  
 <span data-ttu-id="e6c57-135">この要素の使用例については、「[XML 入力ファイルの簡単なサンプル &#40;DTA&#41;](simple-xml-input-file-sample-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6c57-135">For a usage example of this element, see the [Simple XML Input File Sample &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6c57-136">参照</span><span class="sxs-lookup"><span data-stu-id="e6c57-136">See Also</span></span>  
 [<span data-ttu-id="e6c57-137">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="e6c57-137">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
