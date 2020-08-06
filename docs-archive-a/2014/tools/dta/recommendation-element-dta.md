---
title: 推奨要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Recommendation element
ms.assetid: 679ea535-865a-4633-a4d3-5b3090515158
author: stevestein
ms.author: sstein
ms.openlocfilehash: b4eb54a106d67f0217a2604b2d08754d0d2c0765
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632871"
---
# <a name="recommendation-element-dta"></a><span data-ttu-id="2a80f-102">Recommendation 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="2a80f-102">Recommendation Element (DTA)</span></span>
  <span data-ttu-id="2a80f-103">ユーザー指定の構成の一部である仮想インデックスについての情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2a80f-103">Contains information about the hypothetical indexes that are part of a user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a80f-104">構文</span><span class="sxs-lookup"><span data-stu-id="2a80f-104">Syntax</span></span>  
  
```  
  
<Configuration>  
    ...code removed here...  
    <Table>  
      <Name>...</Name>  
      <Recommendation>  
      ...code removed here...  
      </Recommendation>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="2a80f-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="2a80f-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="2a80f-106">特徴</span><span class="sxs-lookup"><span data-stu-id="2a80f-106">Characteristic</span></span>|<span data-ttu-id="2a80f-107">説明</span><span class="sxs-lookup"><span data-stu-id="2a80f-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="2a80f-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="2a80f-108">**Data type and length**</span></span>|<span data-ttu-id="2a80f-109">[なし] :</span><span class="sxs-lookup"><span data-stu-id="2a80f-109">None.</span></span>|  
|<span data-ttu-id="2a80f-110">**既定値**</span><span class="sxs-lookup"><span data-stu-id="2a80f-110">**Default value**</span></span>|<span data-ttu-id="2a80f-111">[なし] :</span><span class="sxs-lookup"><span data-stu-id="2a80f-111">None.</span></span>|  
|<span data-ttu-id="2a80f-112">**個数**</span><span class="sxs-lookup"><span data-stu-id="2a80f-112">**Occurrence**</span></span>|<span data-ttu-id="2a80f-113">省略可能。</span><span class="sxs-lookup"><span data-stu-id="2a80f-113">Optional.</span></span> <span data-ttu-id="2a80f-114">`Table` 要素につき 1 回使用できます。</span><span class="sxs-lookup"><span data-stu-id="2a80f-114">Can use once for each `Table` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="2a80f-115">要素の関係</span><span class="sxs-lookup"><span data-stu-id="2a80f-115">Element Relationships</span></span>  
  
|<span data-ttu-id="2a80f-116">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="2a80f-116">Relationship</span></span>|<span data-ttu-id="2a80f-117">要素</span><span class="sxs-lookup"><span data-stu-id="2a80f-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="2a80f-118">**親要素**</span><span class="sxs-lookup"><span data-stu-id="2a80f-118">**Parent element**</span></span>|[<span data-ttu-id="2a80f-119">Schema の Table 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="2a80f-119">Table Element for Schema &#40;DTA&#41;</span></span>](table-element-for-schema-dta.md)|  
|<span data-ttu-id="2a80f-120">**子要素**</span><span class="sxs-lookup"><span data-stu-id="2a80f-120">**Child elements**</span></span>|[<span data-ttu-id="2a80f-121">Create 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="2a80f-121">Create Element &#40;DTA&#41;</span></span>](create-element-dta.md)<br /><br /> <span data-ttu-id="2a80f-122">`Drop` 要素。</span><span class="sxs-lookup"><span data-stu-id="2a80f-122">`Drop` element.</span></span> <span data-ttu-id="2a80f-123">詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](https://go.microsoft.com/fwlink/?linkid=43100)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a80f-123">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a80f-124">解説</span><span class="sxs-lookup"><span data-stu-id="2a80f-124">Remarks</span></span>  
 <span data-ttu-id="2a80f-125">この要素は、データベース エンジン チューニング アドバイザー XML スキーマの **RecommendationTypecomplexType** の名前です。</span><span class="sxs-lookup"><span data-stu-id="2a80f-125">This element is of the **RecommendationTypecomplexType** name in the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="2a80f-126">仮想的な構成でのインデックスを指定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="2a80f-126">It is used to specify indexes for a hypothetical configuration.</span></span> <span data-ttu-id="2a80f-127">この `Recommendation` 要素を、パーティション分割を指定するための `RecommendationPType` やビューを指定するための `RecommendationViewType` という他の種類の要素と混同しないでください。</span><span class="sxs-lookup"><span data-stu-id="2a80f-127">Do not confuse this `Recommendation` element with the other types that can be used to specify partitioning (`RecommendationPType`) or views (`RecommendationViewType`).</span></span> <span data-ttu-id="2a80f-128">これらの要素の種類の詳細については `Recommendation` 、「[データベースエンジンチューニングアドバイザー XML スキーマ](https://go.microsoft.com/fwlink/?linkid=43100)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a80f-128">For information about these other `Recommendation` element types, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a80f-129">例</span><span class="sxs-lookup"><span data-stu-id="2a80f-129">Example</span></span>  
 <span data-ttu-id="2a80f-130">この要素の使用例については、「[ユーザー指定の構成を指定した XML 入力ファイルのサンプル &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a80f-130">For a usage example of this element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a80f-131">参照</span><span class="sxs-lookup"><span data-stu-id="2a80f-131">See Also</span></span>  
 [<span data-ttu-id="2a80f-132">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="2a80f-132">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
