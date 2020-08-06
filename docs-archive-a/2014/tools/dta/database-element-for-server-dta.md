---
title: Server の Database 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: 5cd9a87a-af4b-45f3-8c18-f7fd7e7d3064
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9a48d255898eff6bd780f8edf2c8d2da7229b0ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711333"
---
# <a name="database-element-for-server-dta"></a><span data-ttu-id="65f14-102">Server の Database 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="65f14-102">Database Element for Server (DTA)</span></span>
  <span data-ttu-id="65f14-103">特定のサーバーにあるチューニング対象のデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="65f14-103">Specifies the database you want to tune on a specific server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65f14-104">構文</span><span class="sxs-lookup"><span data-stu-id="65f14-104">Syntax</span></span>  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="65f14-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="65f14-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="65f14-106">特徴</span><span class="sxs-lookup"><span data-stu-id="65f14-106">Characteristic</span></span>|<span data-ttu-id="65f14-107">説明</span><span class="sxs-lookup"><span data-stu-id="65f14-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="65f14-108">データ型と長さ</span><span class="sxs-lookup"><span data-stu-id="65f14-108">Data type and length</span></span>|<span data-ttu-id="65f14-109">[なし] :</span><span class="sxs-lookup"><span data-stu-id="65f14-109">None.</span></span>|  
|<span data-ttu-id="65f14-110">既定値</span><span class="sxs-lookup"><span data-stu-id="65f14-110">Default value</span></span>|<span data-ttu-id="65f14-111">[なし] :</span><span class="sxs-lookup"><span data-stu-id="65f14-111">None.</span></span>|  
|<span data-ttu-id="65f14-112">個数</span><span class="sxs-lookup"><span data-stu-id="65f14-112">Occurrence</span></span>|<span data-ttu-id="65f14-113">`Server` 要素につき 1 回以上の出現が必要です。</span><span class="sxs-lookup"><span data-stu-id="65f14-113">Required one or more times per `Server` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="65f14-114">要素の関係</span><span class="sxs-lookup"><span data-stu-id="65f14-114">Element Relationships</span></span>  
  
|<span data-ttu-id="65f14-115">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="65f14-115">Relationship</span></span>|<span data-ttu-id="65f14-116">要素</span><span class="sxs-lookup"><span data-stu-id="65f14-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="65f14-117">親要素</span><span class="sxs-lookup"><span data-stu-id="65f14-117">Parent element</span></span>|[<span data-ttu-id="65f14-118">Server 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="65f14-118">Server Element &#40;DTA&#41;</span></span>](server-element-dta.md)|  
|<span data-ttu-id="65f14-119">子要素</span><span class="sxs-lookup"><span data-stu-id="65f14-119">Child elements</span></span>|[<span data-ttu-id="65f14-120">Database の Name 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="65f14-120">Name Element for Database &#40;DTA&#41;</span></span>](name-element-for-database-dta.md)<br /><br /> [<span data-ttu-id="65f14-121">Database の Schema 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="65f14-121">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="65f14-122">解説</span><span class="sxs-lookup"><span data-stu-id="65f14-122">Remarks</span></span>  
 <span data-ttu-id="65f14-123">この要素は、データベース エンジン チューニング アドバイザー XML スキーマの **DatabaseDetailsTypecomplexType** の名前です。</span><span class="sxs-lookup"><span data-stu-id="65f14-123">This element is of the **DatabaseDetailsTypecomplexType** name in the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="65f14-124">この `Database` 要素を、ルートの親要素が `Configuration` 要素である他の要素と混同しないでください。</span><span class="sxs-lookup"><span data-stu-id="65f14-124">Do not confuse this `Database` element with the one whose root parent is the `Configuration` element.</span></span> <span data-ttu-id="65f14-125">詳細については、「[Configuration の Database 要素 &#40;DTA&#41;](database-element-for-configuration-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65f14-125">For more information, see [Database Element for Configuration &#40;DTA&#41;](database-element-for-configuration-dta.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="65f14-126">例</span><span class="sxs-lookup"><span data-stu-id="65f14-126">Example</span></span>  
 <span data-ttu-id="65f14-127">要素の使用例につい `Database` ては、「 [Server ELEMENT &#40;DTA&#41;](server-element-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65f14-127">For a usage example of the `Database` element, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65f14-128">参照</span><span class="sxs-lookup"><span data-stu-id="65f14-128">See Also</span></span>  
 [<span data-ttu-id="65f14-129">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="65f14-129">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
