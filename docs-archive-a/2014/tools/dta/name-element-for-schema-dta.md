---
title: Schema の Name 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Name element
ms.assetid: 014e4854-fed2-454b-8557-5f7c5bb6b17a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 678a6d58b35b25be2aed6d91fcae7ceb2640bdcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719185"
---
# <a name="name-element-for-schema-dta"></a><span data-ttu-id="fce33-102">Schema の Name 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="fce33-102">Name Element for Schema (DTA)</span></span>
  <span data-ttu-id="fce33-103">スキーマの名前が入ります。</span><span class="sxs-lookup"><span data-stu-id="fce33-103">Contains name of the schema.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fce33-104">構文</span><span class="sxs-lookup"><span data-stu-id="fce33-104">Syntax</span></span>  
  
```  
  
<Database>  
...code removed here  
    <Schema>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="fce33-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="fce33-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="fce33-106">特徴</span><span class="sxs-lookup"><span data-stu-id="fce33-106">Characteristic</span></span>|<span data-ttu-id="fce33-107">説明</span><span class="sxs-lookup"><span data-stu-id="fce33-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="fce33-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="fce33-108">**Data type and length**</span></span>|<span data-ttu-id="fce33-109">`string`(1 ~ 255 文字)</span><span class="sxs-lookup"><span data-stu-id="fce33-109">`string`, between 1 and 255 characters</span></span>|  
|<span data-ttu-id="fce33-110">**既定値**</span><span class="sxs-lookup"><span data-stu-id="fce33-110">**Default value**</span></span>|<span data-ttu-id="fce33-111">[なし] :</span><span class="sxs-lookup"><span data-stu-id="fce33-111">None.</span></span>|  
|<span data-ttu-id="fce33-112">**個数**</span><span class="sxs-lookup"><span data-stu-id="fce33-112">**Occurrence**</span></span>|<span data-ttu-id="fce33-113">**Schema** 要素につき 1 回の出現が必要です。</span><span class="sxs-lookup"><span data-stu-id="fce33-113">Required once per **Schema** element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="fce33-114">要素の関係</span><span class="sxs-lookup"><span data-stu-id="fce33-114">Element Relationships</span></span>  
  
|<span data-ttu-id="fce33-115">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="fce33-115">Relationship</span></span>|<span data-ttu-id="fce33-116">要素</span><span class="sxs-lookup"><span data-stu-id="fce33-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="fce33-117">**親要素**</span><span class="sxs-lookup"><span data-stu-id="fce33-117">**Parent element**</span></span>|[<span data-ttu-id="fce33-118">Database の Schema 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="fce33-118">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)|  
|<span data-ttu-id="fce33-119">**子要素**</span><span class="sxs-lookup"><span data-stu-id="fce33-119">**Child elements**</span></span>|<span data-ttu-id="fce33-120">[なし] :</span><span class="sxs-lookup"><span data-stu-id="fce33-120">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fce33-121">例</span><span class="sxs-lookup"><span data-stu-id="fce33-121">Example</span></span>  
 <span data-ttu-id="fce33-122">この要素の使用例については、「[Server 要素 &#40;DTA&#41;](server-element-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fce33-122">For a usage example of this element, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fce33-123">参照</span><span class="sxs-lookup"><span data-stu-id="fce33-123">See Also</span></span>  
 [<span data-ttu-id="fce33-124">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="fce33-124">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
