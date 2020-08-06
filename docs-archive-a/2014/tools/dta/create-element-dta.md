---
title: Create 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Create element (DTA)
ms.assetid: 9d076c90-f933-45f4-b6d9-447793f6528b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 407f16c3898e56cd393e36c39ed799b83e0092ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711338"
---
# <a name="create-element-dta"></a><span data-ttu-id="d07e8-102">Create 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="d07e8-102">Create Element (DTA)</span></span>
  <span data-ttu-id="d07e8-103">ユーザー指定の構成内のインデックス、統計、ヒープ構造に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d07e8-103">Contains information about the indexes, statistics, or heap structures in a user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d07e8-104">構文</span><span class="sxs-lookup"><span data-stu-id="d07e8-104">Syntax</span></span>  
  
```  
  
<Recommendation>  
    <Create>  
    ...code removed here...  
    </Create>  
</Recommendation>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="d07e8-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="d07e8-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="d07e8-106">特徴</span><span class="sxs-lookup"><span data-stu-id="d07e8-106">Characteristic</span></span>|<span data-ttu-id="d07e8-107">説明</span><span class="sxs-lookup"><span data-stu-id="d07e8-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d07e8-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="d07e8-108">**Data type and length**</span></span>|<span data-ttu-id="d07e8-109">[なし] :</span><span class="sxs-lookup"><span data-stu-id="d07e8-109">None.</span></span>|  
|<span data-ttu-id="d07e8-110">**既定値**</span><span class="sxs-lookup"><span data-stu-id="d07e8-110">**Default value**</span></span>|<span data-ttu-id="d07e8-111">[なし] :</span><span class="sxs-lookup"><span data-stu-id="d07e8-111">None.</span></span>|  
|<span data-ttu-id="d07e8-112">**個数**</span><span class="sxs-lookup"><span data-stu-id="d07e8-112">**Occurrence**</span></span>|<span data-ttu-id="d07e8-113">物理デザイン構造の各種類 (インデックス、統計、ヒープ構造) につき 1 回の出現が必要です。</span><span class="sxs-lookup"><span data-stu-id="d07e8-113">Required once for each physical design structure type (indexes, statistics, or heap structures).</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="d07e8-114">要素の関係</span><span class="sxs-lookup"><span data-stu-id="d07e8-114">Element Relationships</span></span>  
  
|<span data-ttu-id="d07e8-115">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="d07e8-115">Relationship</span></span>|<span data-ttu-id="d07e8-116">要素</span><span class="sxs-lookup"><span data-stu-id="d07e8-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="d07e8-117">**親要素**</span><span class="sxs-lookup"><span data-stu-id="d07e8-117">**Parent element**</span></span>|[<span data-ttu-id="d07e8-118">Recommendation 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="d07e8-118">Recommendation Element &#40;DTA&#41;</span></span>](recommendation-element-dta.md)|  
|<span data-ttu-id="d07e8-119">**子要素**</span><span class="sxs-lookup"><span data-stu-id="d07e8-119">**Child elements**</span></span>|[<span data-ttu-id="d07e8-120">Index 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="d07e8-120">Index Element &#40;DTA&#41;</span></span>](index-element-dta.md)<br /><br /> <span data-ttu-id="d07e8-121">`Statistics`要素 (詳細については[データベースエンジンチューニングアドバイザー XML スキーマ](https://schemas.microsoft.com/sqlserver/)を参照してください)</span><span class="sxs-lookup"><span data-stu-id="d07e8-121">`Statistics` Element (see [Database Engine Tuning Advisor XML schema](https://schemas.microsoft.com/sqlserver/) for information)</span></span><br /><br /> <span data-ttu-id="d07e8-122">`Heap`要素 (詳細については[データベースエンジンチューニングアドバイザー XML スキーマ](https://schemas.microsoft.com/sqlserver/)を参照してください)</span><span class="sxs-lookup"><span data-stu-id="d07e8-122">`Heap` Element (see [Database Engine Tuning Advisor XML schema](https://schemas.microsoft.com/sqlserver/) for information)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d07e8-123">解説</span><span class="sxs-lookup"><span data-stu-id="d07e8-123">Remarks</span></span>  
 <span data-ttu-id="d07e8-124">この要素は、データベース エンジン チューニング アドバイザー XML スキーマの **CreateTypecomplexType** の名前です。</span><span class="sxs-lookup"><span data-stu-id="d07e8-124">This element is of the **CreateTypecomplexType** name in the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="d07e8-125">ユーザー指定の構成でインデックス、統計、ヒープ構造を作成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="d07e8-125">It is used to create indexes, statistics, and heap structures for a user-specified configuration.</span></span> <span data-ttu-id="d07e8-126">この `Create` 要素を、ビューを作成するための `CreateViewType` やパーティション分割を作成するための `CreatePType` という他の種類の要素と混同しないでください。</span><span class="sxs-lookup"><span data-stu-id="d07e8-126">Do not confuse this `Create` element with the other types that can be used to create views (`CreateViewType`) or partitioning (`CreatePType`).</span></span> <span data-ttu-id="d07e8-127">これらの他の要素の種類の詳細については、[データベースエンジンチューニングアドバイザー XML スキーマ](https://schemas.microsoft.com/sqlserver/)を参照してください `Create` 。</span><span class="sxs-lookup"><span data-stu-id="d07e8-127">Refer to the [Database Engine Tuning Advisor XML schema](https://schemas.microsoft.com/sqlserver/) for information about these other `Create` element types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d07e8-128">例</span><span class="sxs-lookup"><span data-stu-id="d07e8-128">Example</span></span>  
 <span data-ttu-id="d07e8-129">この要素の使用例については、「[ユーザー指定の構成を指定した XML 入力ファイルのサンプル &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d07e8-129">For a usage example of this element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d07e8-130">参照</span><span class="sxs-lookup"><span data-stu-id="d07e8-130">See Also</span></span>  
 [<span data-ttu-id="d07e8-131">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="d07e8-131">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
