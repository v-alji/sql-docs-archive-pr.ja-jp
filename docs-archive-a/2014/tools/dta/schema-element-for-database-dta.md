---
title: Database の Schema 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Schema element
ms.assetid: d932e59c-953f-4ab4-934d-b6baf344835c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7653177878f3a832abd2d1ca266bc5feb17b9a29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632870"
---
# <a name="schema-element-for-database-dta"></a><span data-ttu-id="9c74b-102">Database の Schema 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="9c74b-102">Schema Element for Database (DTA)</span></span>
  <span data-ttu-id="9c74b-103">チューニングするデータベースのスキーマを指定します。</span><span class="sxs-lookup"><span data-stu-id="9c74b-103">Specifies the schema of the database that you want to tune.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c74b-104">構文</span><span class="sxs-lookup"><span data-stu-id="9c74b-104">Syntax</span></span>  
  
```  
  
<Database>  
...code removed here...  
    <Schema>...</Schema>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="9c74b-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="9c74b-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="9c74b-106">特徴</span><span class="sxs-lookup"><span data-stu-id="9c74b-106">Characteristic</span></span>|<span data-ttu-id="9c74b-107">説明</span><span class="sxs-lookup"><span data-stu-id="9c74b-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="9c74b-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="9c74b-108">**Data type and length**</span></span>|<span data-ttu-id="9c74b-109">[なし] :</span><span class="sxs-lookup"><span data-stu-id="9c74b-109">None.</span></span>|  
|<span data-ttu-id="9c74b-110">**既定値**</span><span class="sxs-lookup"><span data-stu-id="9c74b-110">**Default value**</span></span>|<span data-ttu-id="9c74b-111">[なし] :</span><span class="sxs-lookup"><span data-stu-id="9c74b-111">None.</span></span>|  
|<span data-ttu-id="9c74b-112">**個数**</span><span class="sxs-lookup"><span data-stu-id="9c74b-112">**Occurrence**</span></span>|<span data-ttu-id="9c74b-113">**Server** 要素の下に指定する **Database** 要素につき 1 回の出現が必要です。</span><span class="sxs-lookup"><span data-stu-id="9c74b-113">Required once for the **Database** element that is specified under the **Server** element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="9c74b-114">要素の関係</span><span class="sxs-lookup"><span data-stu-id="9c74b-114">Element Relationships</span></span>  
  
|<span data-ttu-id="9c74b-115">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="9c74b-115">Relationship</span></span>|<span data-ttu-id="9c74b-116">要素</span><span class="sxs-lookup"><span data-stu-id="9c74b-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="9c74b-117">**親要素**</span><span class="sxs-lookup"><span data-stu-id="9c74b-117">**Parent element**</span></span>|[<span data-ttu-id="9c74b-118">Server の Database 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="9c74b-118">Database Element for Server &#40;DTA&#41;</span></span>](database-element-for-server-dta.md)|  
|<span data-ttu-id="9c74b-119">**子要素**</span><span class="sxs-lookup"><span data-stu-id="9c74b-119">**Child elements**</span></span>|[<span data-ttu-id="9c74b-120">Schema の Name 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="9c74b-120">Name Element for Schema &#40;DTA&#41;</span></span>](name-element-for-schema-dta.md)<br /><br /> [<span data-ttu-id="9c74b-121">Schema の Table 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="9c74b-121">Table Element for Schema &#40;DTA&#41;</span></span>](table-element-for-schema-dta.md)|  
  
## <a name="example"></a><span data-ttu-id="9c74b-122">例</span><span class="sxs-lookup"><span data-stu-id="9c74b-122">Example</span></span>  
 <span data-ttu-id="9c74b-123">この要素の使用例については、「[Server 要素 &#40;DTA&#41;](server-element-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c74b-123">For a usage example of this element, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c74b-124">参照</span><span class="sxs-lookup"><span data-stu-id="9c74b-124">See Also</span></span>  
 [<span data-ttu-id="9c74b-125">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="9c74b-125">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
