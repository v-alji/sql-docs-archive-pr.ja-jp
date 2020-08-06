---
title: Configuration の Database 要素 (DTA) |Microsoft Docs
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
ms.assetid: e91ba243-6cc9-457a-8f5a-134f3c71ae69
author: stevestein
ms.author: sstein
ms.openlocfilehash: 69ce1a0ac9912907f6d22916dd6243621e0778db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711334"
---
# <a name="database-element-for-configuration-dta"></a><span data-ttu-id="927f9-102">Configuration の Database 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="927f9-102">Database Element for Configuration (DTA)</span></span>
  <span data-ttu-id="927f9-103">データベース エンジン チューニング アドバイザーで仮想的な構成 (`Configuration` 要素で指定する構成) を評価するときの対象のデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="927f9-103">Specifies the database against which you want the Database Engine Tuning Advisor to evaluate the hypothetical configuration (specified by the `Configuration` element).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="927f9-104">構文</span><span class="sxs-lookup"><span data-stu-id="927f9-104">Syntax</span></span>  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="927f9-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="927f9-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="927f9-106">特徴</span><span class="sxs-lookup"><span data-stu-id="927f9-106">Characteristic</span></span>|<span data-ttu-id="927f9-107">説明</span><span class="sxs-lookup"><span data-stu-id="927f9-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="927f9-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="927f9-108">**Data type and length**</span></span>|<span data-ttu-id="927f9-109">[なし] :</span><span class="sxs-lookup"><span data-stu-id="927f9-109">None.</span></span>|  
|<span data-ttu-id="927f9-110">**既定値**</span><span class="sxs-lookup"><span data-stu-id="927f9-110">**Default value**</span></span>|<span data-ttu-id="927f9-111">[なし] :</span><span class="sxs-lookup"><span data-stu-id="927f9-111">None.</span></span>|  
|<span data-ttu-id="927f9-112">**個数**</span><span class="sxs-lookup"><span data-stu-id="927f9-112">**Occurrence**</span></span>|<span data-ttu-id="927f9-113">`Server` 要素につき 1 回以上の出現が必要です。</span><span class="sxs-lookup"><span data-stu-id="927f9-113">Required one or more times per `Server` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="927f9-114">要素の関係</span><span class="sxs-lookup"><span data-stu-id="927f9-114">Element Relationships</span></span>  
  
|<span data-ttu-id="927f9-115">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="927f9-115">Relationship</span></span>|<span data-ttu-id="927f9-116">要素</span><span class="sxs-lookup"><span data-stu-id="927f9-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="927f9-117">**親要素**</span><span class="sxs-lookup"><span data-stu-id="927f9-117">**Parent element**</span></span>|[<span data-ttu-id="927f9-118">Configuration の Server 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="927f9-118">Server Element for Configuration &#40;DTA&#41;</span></span>](server-element-for-configuration-dta.md)|  
|<span data-ttu-id="927f9-119">**子要素**</span><span class="sxs-lookup"><span data-stu-id="927f9-119">**Child elements**</span></span>|[<span data-ttu-id="927f9-120">Database の Name 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="927f9-120">Name Element for Database &#40;DTA&#41;</span></span>](name-element-for-database-dta.md)<br /><br /> [<span data-ttu-id="927f9-121">Database の Schema 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="927f9-121">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)<br /><br /> [<span data-ttu-id="927f9-122">Recommendation 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="927f9-122">Recommendation Element &#40;DTA&#41;</span></span>](recommendation-element-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="927f9-123">解説</span><span class="sxs-lookup"><span data-stu-id="927f9-123">Remarks</span></span>  
 <span data-ttu-id="927f9-124">この要素は、データベース エンジン チューニング アドバイザー XML スキーマの **DatabaseTypecomplexType** の名前です。</span><span class="sxs-lookup"><span data-stu-id="927f9-124">This element is of the **DatabaseTypecomplexType** name in the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="927f9-125">この `Database` 要素を、ルートの親要素が `Server` 要素である (XML 入力ファイルの最上位に記述する) 同じ名前の要素と混同しないでください。</span><span class="sxs-lookup"><span data-stu-id="927f9-125">Do not confuse this `Database` element with the one whose root parent is the `Server` element, which occurs at the top of the XML input file.</span></span> <span data-ttu-id="927f9-126">詳細については、「[Server の Database 要素 &#40;DTA&#41;](database-element-for-server-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="927f9-126">For more information, see [Database Element for Server &#40;DTA&#41;](database-element-for-server-dta.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="927f9-127">例</span><span class="sxs-lookup"><span data-stu-id="927f9-127">Example</span></span>  
 <span data-ttu-id="927f9-128">この要素の使用例につい `Database` ては、「[ユーザー指定の構成を使用した XML 入力ファイルのサンプル &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="927f9-128">For a usage example of this `Database` element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="927f9-129">参照</span><span class="sxs-lookup"><span data-stu-id="927f9-129">See Also</span></span>  
 [<span data-ttu-id="927f9-130">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="927f9-130">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
