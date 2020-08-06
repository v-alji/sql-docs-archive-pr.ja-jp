---
title: Schema の Table 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Table element [DTA]
ms.assetid: a59e8319-05d1-47f3-af39-7d970ab8e7dc
author: stevestein
ms.author: sstein
ms.openlocfilehash: dd444b1da99b22e0259dc1f50818c1763b7052ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720654"
---
# <a name="table-element-for-schema-dta"></a><span data-ttu-id="cae08-102">Schema の Table 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="cae08-102">Table Element for Schema (DTA)</span></span>
  <span data-ttu-id="cae08-103">チューニングの対象にするテーブルを指定します。</span><span class="sxs-lookup"><span data-stu-id="cae08-103">Specifies the table for tuning.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cae08-104">構文</span><span class="sxs-lookup"><span data-stu-id="cae08-104">Syntax</span></span>  
  
```  
  
<Schema>  
...code removed here...  
    <Table>...</Table>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="cae08-105">要素の属性</span><span class="sxs-lookup"><span data-stu-id="cae08-105">Element Attributes</span></span>  
  
|<span data-ttu-id="cae08-106">属性</span><span class="sxs-lookup"><span data-stu-id="cae08-106">Attribute</span></span>|<span data-ttu-id="cae08-107">説明</span><span class="sxs-lookup"><span data-stu-id="cae08-107">Description</span></span>|  
|---------------|-----------------|  
|`NumberOfRows`|<span data-ttu-id="cae08-108">省略可能。</span><span class="sxs-lookup"><span data-stu-id="cae08-108">Optional.</span></span> <span data-ttu-id="cae08-109">さまざまなサイズのテーブルのシミュレーションを行うための整数です。</span><span class="sxs-lookup"><span data-stu-id="cae08-109">Integer that allows you to simulate tables of different sizes.</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="cae08-110">要素の特性</span><span class="sxs-lookup"><span data-stu-id="cae08-110">Element Characteristics</span></span>  
  
|<span data-ttu-id="cae08-111">特徴</span><span class="sxs-lookup"><span data-stu-id="cae08-111">Characteristic</span></span>|<span data-ttu-id="cae08-112">説明</span><span class="sxs-lookup"><span data-stu-id="cae08-112">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="cae08-113">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="cae08-113">**Data type and length**</span></span>|<span data-ttu-id="cae08-114">**string**、1 ～ 255 文字。</span><span class="sxs-lookup"><span data-stu-id="cae08-114">**string**, between 1 and 255 characters.</span></span>|  
|<span data-ttu-id="cae08-115">**既定値**</span><span class="sxs-lookup"><span data-stu-id="cae08-115">**Default value**</span></span>|<span data-ttu-id="cae08-116">[なし] :</span><span class="sxs-lookup"><span data-stu-id="cae08-116">None.</span></span>|  
|<span data-ttu-id="cae08-117">**個数**</span><span class="sxs-lookup"><span data-stu-id="cae08-117">**Occurrence**</span></span>|<span data-ttu-id="cae08-118">省略可能。</span><span class="sxs-lookup"><span data-stu-id="cae08-118">Optional.</span></span> <span data-ttu-id="cae08-119">ワークロードに応じて任意の数のテーブルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="cae08-119">List as many tables as appropriate for your workload.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="cae08-120">要素の関係</span><span class="sxs-lookup"><span data-stu-id="cae08-120">Element Relationships</span></span>  
  
|<span data-ttu-id="cae08-121">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="cae08-121">Relationship</span></span>|<span data-ttu-id="cae08-122">要素</span><span class="sxs-lookup"><span data-stu-id="cae08-122">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="cae08-123">**親要素**</span><span class="sxs-lookup"><span data-stu-id="cae08-123">**Parent element**</span></span>|[<span data-ttu-id="cae08-124">Database の Schema 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="cae08-124">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)|  
|<span data-ttu-id="cae08-125">**子要素**</span><span class="sxs-lookup"><span data-stu-id="cae08-125">**Child elements**</span></span>|[<span data-ttu-id="cae08-126">Table の Name 要素 (DTA) &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="cae08-126">Name Element for Table &#40;DTA&#41;</span></span>](name-element-for-table-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="cae08-127">解説</span><span class="sxs-lookup"><span data-stu-id="cae08-127">Remarks</span></span>  
 <span data-ttu-id="cae08-128">`Table` 要素を指定しない場合、データベース エンジン チューニング アドバイザーでは、指定されているデータベースのすべてのテーブルがチューニング対象と見なされます。</span><span class="sxs-lookup"><span data-stu-id="cae08-128">If you do not specify a `Table` element, Database Engine Tuning Advisor will assume all tables on the specified database can be tuned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cae08-129">例</span><span class="sxs-lookup"><span data-stu-id="cae08-129">Example</span></span>  
 <span data-ttu-id="cae08-130">使用例については、「[Server 要素 &#40;DTA&#41;](server-element-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cae08-130">For a usage example, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cae08-131">参照</span><span class="sxs-lookup"><span data-stu-id="cae08-131">See Also</span></span>  
 [<span data-ttu-id="cae08-132">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="cae08-132">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
