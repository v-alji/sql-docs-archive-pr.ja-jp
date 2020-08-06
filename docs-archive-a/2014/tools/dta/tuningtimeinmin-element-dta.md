---
title: TuningTimeInMin 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TuningTimeInMin element
ms.assetid: 4973d9ac-20fd-4ac3-bc9f-5d60e39fdb7d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4dae3fe4e9ac3126f43ec017c34d2bc548fda6d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720619"
---
# <a name="tuningtimeinmin-element-dta"></a><span data-ttu-id="9d235-102">TuningTimeInMin 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="9d235-102">TuningTimeInMin Element (DTA)</span></span>
  <span data-ttu-id="9d235-103">チューニング セッションの最大の長さを分単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="9d235-103">Specifies the maximum length of a tuning session in minutes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d235-104">構文</span><span class="sxs-lookup"><span data-stu-id="9d235-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <TuningTimeInMin>...</TuningTimeInMin>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="9d235-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="9d235-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="9d235-106">特徴</span><span class="sxs-lookup"><span data-stu-id="9d235-106">Characteristic</span></span>|<span data-ttu-id="9d235-107">説明</span><span class="sxs-lookup"><span data-stu-id="9d235-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="9d235-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="9d235-108">**Data type and length**</span></span>|<span data-ttu-id="9d235-109">`unsignedInt`、長さは無制限です。</span><span class="sxs-lookup"><span data-stu-id="9d235-109">`unsignedInt`, unlimited length.</span></span>|  
|<span data-ttu-id="9d235-110">**既定値**</span><span class="sxs-lookup"><span data-stu-id="9d235-110">**Default value**</span></span>|<span data-ttu-id="9d235-111">480 分 (8 時間)。</span><span class="sxs-lookup"><span data-stu-id="9d235-111">480 minutes (8 hours).</span></span>|  
|<span data-ttu-id="9d235-112">**個数**</span><span class="sxs-lookup"><span data-stu-id="9d235-112">**Occurrence**</span></span>|<span data-ttu-id="9d235-113">`NumberOfEvents` 要素に値が指定されていない限り、必須です。</span><span class="sxs-lookup"><span data-stu-id="9d235-113">Required unless a value has been specified for the `NumberOfEvents` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="9d235-114">要素の関係</span><span class="sxs-lookup"><span data-stu-id="9d235-114">Element Relationships</span></span>  
  
|<span data-ttu-id="9d235-115">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="9d235-115">Relationship</span></span>|<span data-ttu-id="9d235-116">要素</span><span class="sxs-lookup"><span data-stu-id="9d235-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="9d235-117">**親要素**</span><span class="sxs-lookup"><span data-stu-id="9d235-117">**Parent element**</span></span>|[<span data-ttu-id="9d235-118">TuningOptions 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="9d235-118">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="9d235-119">**子要素**</span><span class="sxs-lookup"><span data-stu-id="9d235-119">**Child elements**</span></span>|<span data-ttu-id="9d235-120">なし</span><span class="sxs-lookup"><span data-stu-id="9d235-120">None</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9d235-121">例</span><span class="sxs-lookup"><span data-stu-id="9d235-121">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="9d235-122">説明</span><span class="sxs-lookup"><span data-stu-id="9d235-122">Description</span></span>  
 <span data-ttu-id="9d235-123">次のコード例は、最大チューニング時間を 12 時間に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9d235-123">The following code example shows how to set 12 hours as the maximum tuning time:</span></span>  
  
## <a name="code"></a><span data-ttu-id="9d235-124">コード</span><span class="sxs-lookup"><span data-stu-id="9d235-124">Code</span></span>  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <TuningTimeInMin>720</TuningTimeInMin>  
...code removed here...  
</DTAInput>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d235-125">参照</span><span class="sxs-lookup"><span data-stu-id="9d235-125">See Also</span></span>  
 [<span data-ttu-id="9d235-126">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="9d235-126">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
