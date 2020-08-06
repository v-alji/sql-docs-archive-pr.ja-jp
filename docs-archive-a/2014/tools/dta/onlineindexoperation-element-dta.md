---
title: オンラインの Indexoperation 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- OnlineIndexOperation element
ms.assetid: 7c5614cd-09aa-4a59-9591-347aa7d36473
author: stevestein
ms.author: sstein
ms.openlocfilehash: 48943c1b31d7a0a24ae939050d44494476e50034
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643060"
---
# <a name="onlineindexoperation-element-dta"></a><span data-ttu-id="8f78c-102">OnlineIndexOperation 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="8f78c-102">OnlineIndexOperation Element (DTA)</span></span>
  <span data-ttu-id="8f78c-103">データベース エンジン チューニング アドバイザーによって推奨されるインデックス、インデックス付きビュー、またはパーティションがオンラインで作成可能かどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="8f78c-103">Specifies whether the indexes, indexed views, or partitions that Database Engine Tuning Advisor recommends can be created online.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f78c-104">構文</span><span class="sxs-lookup"><span data-stu-id="8f78c-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <OnlineIndexOperation>...</OnlineIndexOperation>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="8f78c-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="8f78c-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="8f78c-106">特徴</span><span class="sxs-lookup"><span data-stu-id="8f78c-106">Characteristic</span></span>|<span data-ttu-id="8f78c-107">説明</span><span class="sxs-lookup"><span data-stu-id="8f78c-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="8f78c-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="8f78c-108">**Data type and length**</span></span>|<span data-ttu-id="8f78c-109">`string`。最大長はありません。</span><span class="sxs-lookup"><span data-stu-id="8f78c-109">`string`, no maximum length.</span></span>|  
|<span data-ttu-id="8f78c-110">**指定できる値**</span><span class="sxs-lookup"><span data-stu-id="8f78c-110">**Allowed values**</span></span>|<span data-ttu-id="8f78c-111">**OFF**</span><span class="sxs-lookup"><span data-stu-id="8f78c-111">**OFF**</span></span><br /> <span data-ttu-id="8f78c-112">推奨される物理デザイン構造をオンラインで作成しません。</span><span class="sxs-lookup"><span data-stu-id="8f78c-112">No recommended physical design structures can be created online.</span></span><br /><br /> <span data-ttu-id="8f78c-113">**ON**</span><span class="sxs-lookup"><span data-stu-id="8f78c-113">**ON**</span></span><br /> <span data-ttu-id="8f78c-114">推奨される物理デザイン構造をすべてオンラインで作成します。</span><span class="sxs-lookup"><span data-stu-id="8f78c-114">All recommended physical design structures can be created online.</span></span><br /><br /> <span data-ttu-id="8f78c-115">**混合**</span><span class="sxs-lookup"><span data-stu-id="8f78c-115">**MIXED**</span></span><br /> <span data-ttu-id="8f78c-116">データベース エンジン チューニング アドバイザーは、可能な場合にオンラインで作成できる物理デザイン構造を推奨します。</span><span class="sxs-lookup"><span data-stu-id="8f78c-116">Database Engine Tuning Advisor attempts to recommend physical design structures that can be created online when possible.</span></span><br /><br /> <span data-ttu-id="8f78c-117">この要素では、上記の値のいずれか 1 つを使用してください。</span><span class="sxs-lookup"><span data-stu-id="8f78c-117">Use one of these values with this element.</span></span> <span data-ttu-id="8f78c-118">インデックスがオンラインで作成される場合は、オブジェクト定義に **ONLINE = ON** が追加されます。</span><span class="sxs-lookup"><span data-stu-id="8f78c-118">If indexes are created online, the keyword **ONLINE = ON** is appended to its object definition.</span></span>|  
|<span data-ttu-id="8f78c-119">**既定値**</span><span class="sxs-lookup"><span data-stu-id="8f78c-119">**Default value**</span></span>|<span data-ttu-id="8f78c-120">[なし] :</span><span class="sxs-lookup"><span data-stu-id="8f78c-120">None.</span></span>|  
|<span data-ttu-id="8f78c-121">**個数**</span><span class="sxs-lookup"><span data-stu-id="8f78c-121">**Occurrence**</span></span>|<span data-ttu-id="8f78c-122">省略可能。</span><span class="sxs-lookup"><span data-stu-id="8f78c-122">Optional.</span></span> <span data-ttu-id="8f78c-123">使用する場合は、`TuningOptions` 要素に 1 回使用できます。</span><span class="sxs-lookup"><span data-stu-id="8f78c-123">If used, can only be used once for the `TuningOptions` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="8f78c-124">要素の関係</span><span class="sxs-lookup"><span data-stu-id="8f78c-124">Element Relationships</span></span>  
  
|<span data-ttu-id="8f78c-125">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="8f78c-125">Relationship</span></span>|<span data-ttu-id="8f78c-126">要素</span><span class="sxs-lookup"><span data-stu-id="8f78c-126">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="8f78c-127">**親要素**</span><span class="sxs-lookup"><span data-stu-id="8f78c-127">**Parent element**</span></span>|[<span data-ttu-id="8f78c-128">TuningOptions 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="8f78c-128">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="8f78c-129">**子要素**</span><span class="sxs-lookup"><span data-stu-id="8f78c-129">**Child elements**</span></span>|<span data-ttu-id="8f78c-130">[なし] :</span><span class="sxs-lookup"><span data-stu-id="8f78c-130">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8f78c-131">例</span><span class="sxs-lookup"><span data-stu-id="8f78c-131">Example</span></span>  
 <span data-ttu-id="8f78c-132">この要素の使用例については、「[XML 入力ファイルの簡単なサンプル &#40;DTA&#41;](simple-xml-input-file-sample-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f78c-132">For a usage example of this element, see the [Simple XML Input File Sample &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f78c-133">参照</span><span class="sxs-lookup"><span data-stu-id="8f78c-133">See Also</span></span>  
 [<span data-ttu-id="8f78c-134">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="8f78c-134">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
