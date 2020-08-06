---
title: TestServer 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TestServer element
ms.assetid: caa3547a-2cd5-47ad-ace2-a36752835cfe
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8d1f1fadf76a43caca262652254e8a778602183c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720655"
---
# <a name="testserver-element-dta"></a><span data-ttu-id="2b72c-102">TestServer 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="2b72c-102">TestServer Element (DTA)</span></span>
  <span data-ttu-id="2b72c-103">実稼働サーバーのチューニング時に使用するテスト サーバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="2b72c-103">Specifies the test server to use when tuning a production server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b72c-104">構文</span><span class="sxs-lookup"><span data-stu-id="2b72c-104">Syntax</span></span>  
  
```  
  
<TuningOptions>  
  <TestServer>...</TestServer>  
   ...code removed here...  
</TuningOptions>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="2b72c-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="2b72c-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="2b72c-106">特徴</span><span class="sxs-lookup"><span data-stu-id="2b72c-106">Characteristic</span></span>|<span data-ttu-id="2b72c-107">説明</span><span class="sxs-lookup"><span data-stu-id="2b72c-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="2b72c-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="2b72c-108">**Data type and length**</span></span>|<span data-ttu-id="2b72c-109">**string**、長さは無制限です。</span><span class="sxs-lookup"><span data-stu-id="2b72c-109">**string**, unlimited length.</span></span>|  
|<span data-ttu-id="2b72c-110">**既定値**</span><span class="sxs-lookup"><span data-stu-id="2b72c-110">**Default value**</span></span>|<span data-ttu-id="2b72c-111">[なし] :</span><span class="sxs-lookup"><span data-stu-id="2b72c-111">None.</span></span>|  
|<span data-ttu-id="2b72c-112">**個数**</span><span class="sxs-lookup"><span data-stu-id="2b72c-112">**Occurrence**</span></span>|<span data-ttu-id="2b72c-113">省略可能。</span><span class="sxs-lookup"><span data-stu-id="2b72c-113">Optional.</span></span> <span data-ttu-id="2b72c-114">`TuningOptions` 要素につき 1 回使用できます。</span><span class="sxs-lookup"><span data-stu-id="2b72c-114">Can use once for each `TuningOptions` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="2b72c-115">要素の関係</span><span class="sxs-lookup"><span data-stu-id="2b72c-115">Element Relationships</span></span>  
  
|<span data-ttu-id="2b72c-116">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="2b72c-116">Relationship</span></span>|<span data-ttu-id="2b72c-117">要素</span><span class="sxs-lookup"><span data-stu-id="2b72c-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="2b72c-118">**親要素**</span><span class="sxs-lookup"><span data-stu-id="2b72c-118">**Parent element**</span></span>|[<span data-ttu-id="2b72c-119">TuningOptions 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="2b72c-119">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="2b72c-120">**子要素**</span><span class="sxs-lookup"><span data-stu-id="2b72c-120">**Child elements**</span></span>|<span data-ttu-id="2b72c-121">[なし] :</span><span class="sxs-lookup"><span data-stu-id="2b72c-121">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2b72c-122">例</span><span class="sxs-lookup"><span data-stu-id="2b72c-122">Example</span></span>  
 <span data-ttu-id="2b72c-123">この要素の使用例では、次を参照してください。 [実稼働サーバーのチューニング負荷を軽減](../../relational-databases/performance/reduce-the-production-server-tuning-load.md)します。</span><span class="sxs-lookup"><span data-stu-id="2b72c-123">For a usage example of this element, see [Reduce the Production Server Tuning Load](../../relational-databases/performance/reduce-the-production-server-tuning-load.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b72c-124">参照</span><span class="sxs-lookup"><span data-stu-id="2b72c-124">See Also</span></span>  
 [<span data-ttu-id="2b72c-125">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="2b72c-125">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
