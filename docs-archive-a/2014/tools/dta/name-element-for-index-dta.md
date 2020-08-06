---
title: Index の Name 要素 (DTA) |Microsoft Docs
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
ms.assetid: 2300e9cf-f0a8-49e6-b1f5-45ffe03ccb5f
author: stevestein
ms.author: sstein
ms.openlocfilehash: a878923a3d483fae5ad6b55421a2b286f15ceb29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740609"
---
# <a name="name-element-for-index-dta"></a><span data-ttu-id="9f4e8-102">Index の Name 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="9f4e8-102">Name Element for Index (DTA)</span></span>
  <span data-ttu-id="9f4e8-103">ユーザー指定の構成におけるインデックスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="9f4e8-103">Specifies a name for an index in the user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f4e8-104">構文</span><span class="sxs-lookup"><span data-stu-id="9f4e8-104">Syntax</span></span>  
  
```  
  
<Create>  
    <Index>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="9f4e8-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="9f4e8-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="9f4e8-106">特徴</span><span class="sxs-lookup"><span data-stu-id="9f4e8-106">Characteristic</span></span>|<span data-ttu-id="9f4e8-107">説明</span><span class="sxs-lookup"><span data-stu-id="9f4e8-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="9f4e8-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="9f4e8-108">**Data type and length**</span></span>|<span data-ttu-id="9f4e8-109">`string`、長さは無制限です。</span><span class="sxs-lookup"><span data-stu-id="9f4e8-109">`string`, unlimited length.</span></span>|  
|<span data-ttu-id="9f4e8-110">**既定値**</span><span class="sxs-lookup"><span data-stu-id="9f4e8-110">**Default value**</span></span>|<span data-ttu-id="9f4e8-111">[なし] :</span><span class="sxs-lookup"><span data-stu-id="9f4e8-111">None.</span></span>|  
|<span data-ttu-id="9f4e8-112">**個数**</span><span class="sxs-lookup"><span data-stu-id="9f4e8-112">**Occurrence**</span></span>|<span data-ttu-id="9f4e8-113">`Index` 要素につき 1 回の出現が必要です。</span><span class="sxs-lookup"><span data-stu-id="9f4e8-113">Required once for each `Index` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="9f4e8-114">要素の関係</span><span class="sxs-lookup"><span data-stu-id="9f4e8-114">Element Relationships</span></span>  
  
|<span data-ttu-id="9f4e8-115">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="9f4e8-115">Relationship</span></span>|<span data-ttu-id="9f4e8-116">要素</span><span class="sxs-lookup"><span data-stu-id="9f4e8-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="9f4e8-117">**親要素**</span><span class="sxs-lookup"><span data-stu-id="9f4e8-117">**Parent element**</span></span>|[<span data-ttu-id="9f4e8-118">Index 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="9f4e8-118">Index Element &#40;DTA&#41;</span></span>](index-element-dta.md)|  
|<span data-ttu-id="9f4e8-119">**子要素**</span><span class="sxs-lookup"><span data-stu-id="9f4e8-119">**Child elements**</span></span>|<span data-ttu-id="9f4e8-120">[なし] :</span><span class="sxs-lookup"><span data-stu-id="9f4e8-120">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9f4e8-121">例</span><span class="sxs-lookup"><span data-stu-id="9f4e8-121">Example</span></span>  
 <span data-ttu-id="9f4e8-122">この要素の使用例については、「[ユーザー指定の構成を指定した XML 入力ファイルのサンプル &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f4e8-122">For a usage example of this element, see [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f4e8-123">参照</span><span class="sxs-lookup"><span data-stu-id="9f4e8-123">See Also</span></span>  
 [<span data-ttu-id="9f4e8-124">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="9f4e8-124">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
