---
title: Table の Name 要素 (DTA) |Microsoft Docs
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
ms.assetid: 422a755f-ee52-4863-b1aa-f4ef1b8fd0bb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8fa8481cf8990fb63995abcb6300cd9a352c859a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643061"
---
# <a name="name-element-for-table-dta"></a><span data-ttu-id="d30e3-102">Table の Name 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="d30e3-102">Name Element for Table (DTA)</span></span>
  <span data-ttu-id="d30e3-103">チューニングのためのテーブル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="d30e3-103">Specifies a table name for tuning.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d30e3-104">構文</span><span class="sxs-lookup"><span data-stu-id="d30e3-104">Syntax</span></span>  
  
```  
  
<Schema>  
    <Table>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="d30e3-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="d30e3-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="d30e3-106">特徴</span><span class="sxs-lookup"><span data-stu-id="d30e3-106">Characteristic</span></span>|<span data-ttu-id="d30e3-107">説明</span><span class="sxs-lookup"><span data-stu-id="d30e3-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d30e3-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="d30e3-108">**Data type and length**</span></span>|<span data-ttu-id="d30e3-109">`string`、1 ～ 255 文字。</span><span class="sxs-lookup"><span data-stu-id="d30e3-109">`string`, between 1 and 255 characters.</span></span>|  
|<span data-ttu-id="d30e3-110">**既定値**</span><span class="sxs-lookup"><span data-stu-id="d30e3-110">**Default value**</span></span>|<span data-ttu-id="d30e3-111">[なし] :</span><span class="sxs-lookup"><span data-stu-id="d30e3-111">None.</span></span>|  
|<span data-ttu-id="d30e3-112">**個数**</span><span class="sxs-lookup"><span data-stu-id="d30e3-112">**Occurrence**</span></span>|<span data-ttu-id="d30e3-113">必須。</span><span class="sxs-lookup"><span data-stu-id="d30e3-113">Required.</span></span> <span data-ttu-id="d30e3-114">各要素につき1回 `Table` 。</span><span class="sxs-lookup"><span data-stu-id="d30e3-114">Once for each `Table` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="d30e3-115">要素の関係</span><span class="sxs-lookup"><span data-stu-id="d30e3-115">Element Relationships</span></span>  
  
|<span data-ttu-id="d30e3-116">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="d30e3-116">Relationship</span></span>|<span data-ttu-id="d30e3-117">要素</span><span class="sxs-lookup"><span data-stu-id="d30e3-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="d30e3-118">**親要素**</span><span class="sxs-lookup"><span data-stu-id="d30e3-118">**Parent element**</span></span>|[<span data-ttu-id="d30e3-119">Schema の Table 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="d30e3-119">Table Element for Schema &#40;DTA&#41;</span></span>](table-element-for-schema-dta.md)|  
|<span data-ttu-id="d30e3-120">**子要素**</span><span class="sxs-lookup"><span data-stu-id="d30e3-120">**Child elements**</span></span>|<span data-ttu-id="d30e3-121">[なし] :</span><span class="sxs-lookup"><span data-stu-id="d30e3-121">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d30e3-122">例</span><span class="sxs-lookup"><span data-stu-id="d30e3-122">Example</span></span>  
 <span data-ttu-id="d30e3-123">使用例については、「[Server 要素 &#40;DTA&#41;](server-element-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d30e3-123">For a usage example, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d30e3-124">参照</span><span class="sxs-lookup"><span data-stu-id="d30e3-124">See Also</span></span>  
 [<span data-ttu-id="d30e3-125">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="d30e3-125">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
