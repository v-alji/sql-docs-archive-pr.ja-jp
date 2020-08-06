---
title: Column の Name 要素 (DTA) |Microsoft Docs
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
ms.assetid: f93b61de-01fe-4237-ada4-f1e481550564
author: stevestein
ms.author: sstein
ms.openlocfilehash: fad3d9a86a7c5db6b6a7503dc90b5a1540e3618b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711310"
---
# <a name="name-element-for-column-dta"></a><span data-ttu-id="86c48-102">Column の Name 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="86c48-102">Name Element for Column (DTA)</span></span>
  <span data-ttu-id="86c48-103">ユーザー指定の構成におけるインデックス列の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="86c48-103">Specifies the name for an index column in a user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86c48-104">構文</span><span class="sxs-lookup"><span data-stu-id="86c48-104">Syntax</span></span>  
  
```  
  
<Index>  
    <Column>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="86c48-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="86c48-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="86c48-106">特徴</span><span class="sxs-lookup"><span data-stu-id="86c48-106">Characteristic</span></span>|<span data-ttu-id="86c48-107">説明</span><span class="sxs-lookup"><span data-stu-id="86c48-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="86c48-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="86c48-108">**Data type and length**</span></span>|<span data-ttu-id="86c48-109">`string`、長さは無制限です。</span><span class="sxs-lookup"><span data-stu-id="86c48-109">`string`, unlimited length.</span></span>|  
|<span data-ttu-id="86c48-110">**既定値**</span><span class="sxs-lookup"><span data-stu-id="86c48-110">**Default value**</span></span>|<span data-ttu-id="86c48-111">[なし] :</span><span class="sxs-lookup"><span data-stu-id="86c48-111">None.</span></span>|  
|<span data-ttu-id="86c48-112">**個数**</span><span class="sxs-lookup"><span data-stu-id="86c48-112">**Occurrence**</span></span>|<span data-ttu-id="86c48-113">`Column` 要素につき 1 回の出現が必要です。</span><span class="sxs-lookup"><span data-stu-id="86c48-113">Required once for each `Column` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="86c48-114">要素の関係</span><span class="sxs-lookup"><span data-stu-id="86c48-114">Element Relationships</span></span>  
  
|<span data-ttu-id="86c48-115">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="86c48-115">Relationship</span></span>|<span data-ttu-id="86c48-116">要素</span><span class="sxs-lookup"><span data-stu-id="86c48-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="86c48-117">**親要素**</span><span class="sxs-lookup"><span data-stu-id="86c48-117">**Parent element**</span></span>|[<span data-ttu-id="86c48-118">Index の Column 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="86c48-118">Column Element for Index &#40;DTA&#41;</span></span>](column-element-for-index-dta.md)|  
|<span data-ttu-id="86c48-119">**子要素**</span><span class="sxs-lookup"><span data-stu-id="86c48-119">**Child elements**</span></span>|<span data-ttu-id="86c48-120">[なし] :</span><span class="sxs-lookup"><span data-stu-id="86c48-120">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="86c48-121">例</span><span class="sxs-lookup"><span data-stu-id="86c48-121">Example</span></span>  
 <span data-ttu-id="86c48-122">この要素の使用例については、「[ユーザー指定の構成を指定した XML 入力ファイルのサンプル &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86c48-122">For a usage example of this element, see [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c48-123">参照</span><span class="sxs-lookup"><span data-stu-id="86c48-123">See Also</span></span>  
 [<span data-ttu-id="86c48-124">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="86c48-124">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
