---
title: DTAInput 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DTAInput element
ms.assetid: 40c19abf-ded5-43de-be96-5b43b1b81b03
author: stevestein
ms.author: sstein
ms.openlocfilehash: e7d2ff380a4ae1595e50aae472efc5fb4ac72efe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712677"
---
# <a name="dtainput-element-dta"></a><span data-ttu-id="8064d-102">DTAInput 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="8064d-102">DTAInput Element (DTA)</span></span>
  <span data-ttu-id="8064d-103">データベース エンジン チューニング アドバイザーに対する XML 入力の定義が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8064d-103">Contains the definition of XML input for Database Engine Tuning Advisor.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8064d-104">構文</span><span class="sxs-lookup"><span data-stu-id="8064d-104">Syntax</span></span>  
  
```  
  
<DTAXML>  
    <DTAInput>  
    ...code removed here...  
    </DTAInput>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="8064d-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="8064d-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="8064d-106">特性</span><span class="sxs-lookup"><span data-stu-id="8064d-106">Characteristics</span></span>|<span data-ttu-id="8064d-107">説明</span><span class="sxs-lookup"><span data-stu-id="8064d-107">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="8064d-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="8064d-108">**Data type and length**</span></span>|<span data-ttu-id="8064d-109">[なし] :</span><span class="sxs-lookup"><span data-stu-id="8064d-109">None.</span></span>|  
|<span data-ttu-id="8064d-110">**既定値**</span><span class="sxs-lookup"><span data-stu-id="8064d-110">**Default value**</span></span>|<span data-ttu-id="8064d-111">[なし] :</span><span class="sxs-lookup"><span data-stu-id="8064d-111">None.</span></span>|  
|<span data-ttu-id="8064d-112">**個数**</span><span class="sxs-lookup"><span data-stu-id="8064d-112">**Occurrence**</span></span>|<span data-ttu-id="8064d-113">**DTAXML** 要素につき 1 回 (省略可)。</span><span class="sxs-lookup"><span data-stu-id="8064d-113">Optional once per **DTAXML** element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="8064d-114">要素の関係</span><span class="sxs-lookup"><span data-stu-id="8064d-114">Element Relationships</span></span>  
  
|<span data-ttu-id="8064d-115">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="8064d-115">Relationship</span></span>|<span data-ttu-id="8064d-116">要素</span><span class="sxs-lookup"><span data-stu-id="8064d-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="8064d-117">**親要素**</span><span class="sxs-lookup"><span data-stu-id="8064d-117">**Parent element**</span></span>|[<span data-ttu-id="8064d-118">DTAXML 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="8064d-118">DTAXML Element &#40;DTA&#41;</span></span>](dtaxml-element-dta.md)|  
|<span data-ttu-id="8064d-119">**子要素**</span><span class="sxs-lookup"><span data-stu-id="8064d-119">**Child elements**</span></span>|[<span data-ttu-id="8064d-120">Server 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="8064d-120">Server Element &#40;DTA&#41;</span></span>](server-element-dta.md)<br /><br /> [<span data-ttu-id="8064d-121">Workload 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="8064d-121">Workload Element &#40;DTA&#41;</span></span>](workload-element-dta.md)<br /><br /> [<span data-ttu-id="8064d-122">TuningOptions 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="8064d-122">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)<br /><br /> [<span data-ttu-id="8064d-123">Configuration 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="8064d-123">Configuration Element &#40;DTA&#41;</span></span>](configuration-element-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="8064d-124">解説</span><span class="sxs-lookup"><span data-stu-id="8064d-124">Remarks</span></span>  
 <span data-ttu-id="8064d-125">この要素は、データベース エンジン チューニング アドバイザーの入力スキーマ階層のルートです。</span><span class="sxs-lookup"><span data-stu-id="8064d-125">This element is the root of the Database Engine Tuning Advisor input schema hierarchy.</span></span> <span data-ttu-id="8064d-126">データベース エンジン チューニング アドバイザーへの入力としては、チューニング対象のデータベースのサーバー、ワークロード、チューニング オプション、ユーザー指定の構成などを指定した引数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8064d-126">Input to Database Engine Tuning Advisor can be arguments that specify the servers whose databases you want to tune, workloads, tuning options, or a user-specified configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8064d-127">例</span><span class="sxs-lookup"><span data-stu-id="8064d-127">Example</span></span>  
 <span data-ttu-id="8064d-128">**DTAInput** 要素の使用例については、「[XML 入力ファイルの簡単なサンプル &#40;DTA&#41;](simple-xml-input-file-sample-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8064d-128">For a usage example of the **DTAInput** element, see [Simple XML Input File Sample &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8064d-129">参照</span><span class="sxs-lookup"><span data-stu-id="8064d-129">See Also</span></span>  
 [<span data-ttu-id="8064d-130">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="8064d-130">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
