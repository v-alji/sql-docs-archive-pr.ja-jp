---
title: Index の Filegroup 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Filegroup element [DTA]
ms.assetid: 7078d2fb-fa77-44fc-beb3-c095088fcb85
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5ed8ea723d6c0798b93e16411ee47d6e956c6c22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720660"
---
# <a name="filegroup-element-for-index-dta"></a><span data-ttu-id="a795d-102">Index の Filegroup 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="a795d-102">Filegroup Element for Index (DTA)</span></span>
  <span data-ttu-id="a795d-103">ユーザー指定の構成で、インデックスを作成するファイル グループを指定します。</span><span class="sxs-lookup"><span data-stu-id="a795d-103">Specifies the filegroup on which the index is to be created for a user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a795d-104">構文</span><span class="sxs-lookup"><span data-stu-id="a795d-104">Syntax</span></span>  
  
```  
  
<Index>  
  <Name>...</Name>  
  <Column>  
    <Name>...</Name>  
  <Filegroup>...</Filegroup>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="a795d-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="a795d-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="a795d-106">特徴</span><span class="sxs-lookup"><span data-stu-id="a795d-106">Characteristic</span></span>|<span data-ttu-id="a795d-107">説明</span><span class="sxs-lookup"><span data-stu-id="a795d-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="a795d-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="a795d-108">**Data type and length**</span></span>|<span data-ttu-id="a795d-109">`string`、長さは無制限です。</span><span class="sxs-lookup"><span data-stu-id="a795d-109">`string`, unlimited length.</span></span>|  
|<span data-ttu-id="a795d-110">**既定値**</span><span class="sxs-lookup"><span data-stu-id="a795d-110">**Default value**</span></span>|<span data-ttu-id="a795d-111">[なし] :</span><span class="sxs-lookup"><span data-stu-id="a795d-111">None.</span></span>|  
|<span data-ttu-id="a795d-112">**個数**</span><span class="sxs-lookup"><span data-stu-id="a795d-112">**Occurrence**</span></span>|<span data-ttu-id="a795d-113">省略可能。</span><span class="sxs-lookup"><span data-stu-id="a795d-113">Optional.</span></span> <span data-ttu-id="a795d-114">`Index` 要素につき 1 回使用できます。</span><span class="sxs-lookup"><span data-stu-id="a795d-114">Can use once for each `Index` element.</span></span> <span data-ttu-id="a795d-115">この要素は、`PartitionScheme` 要素に `PartitionColumn` および `Index` 要素が指定されている場合には使用できません。 </span><span class="sxs-lookup"><span data-stu-id="a795d-115">This element cannot be used if the `PartitionScheme` and `PartitionColumn` elements are specified for the `Index` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="a795d-116">要素の関係</span><span class="sxs-lookup"><span data-stu-id="a795d-116">Element Relationships</span></span>  
  
|<span data-ttu-id="a795d-117">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="a795d-117">Relationship</span></span>|<span data-ttu-id="a795d-118">要素</span><span class="sxs-lookup"><span data-stu-id="a795d-118">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="a795d-119">**親要素**</span><span class="sxs-lookup"><span data-stu-id="a795d-119">**Parent element**</span></span>|[<span data-ttu-id="a795d-120">Index 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="a795d-120">Index Element &#40;DTA&#41;</span></span>](index-element-dta.md)|  
|<span data-ttu-id="a795d-121">**子要素**</span><span class="sxs-lookup"><span data-stu-id="a795d-121">**Child elements**</span></span>|<span data-ttu-id="a795d-122">[なし] :</span><span class="sxs-lookup"><span data-stu-id="a795d-122">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a795d-123">例</span><span class="sxs-lookup"><span data-stu-id="a795d-123">Example</span></span>  
 <span data-ttu-id="a795d-124">この要素の使用例については、「[ユーザー指定の構成を指定した XML 入力ファイルのサンプル &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a795d-124">For a usage example of this element, see [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a795d-125">参照</span><span class="sxs-lookup"><span data-stu-id="a795d-125">See Also</span></span>  
 [<span data-ttu-id="a795d-126">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="a795d-126">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
