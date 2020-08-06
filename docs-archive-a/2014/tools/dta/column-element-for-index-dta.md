---
title: Index の Column 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Column element
ms.assetid: ba9fac20-26bd-4333-940e-842c15241b46
author: stevestein
ms.author: sstein
ms.openlocfilehash: 67853dc7d1193d3a0f80e56023846bc55a20bdaa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711362"
---
# <a name="column-element-for-index-dta"></a><span data-ttu-id="de5d2-102">Index の Column 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="de5d2-102">Column Element for Index (DTA)</span></span>
  <span data-ttu-id="de5d2-103">ユーザー指定の構成で、インデックスを作成する列を指定します。</span><span class="sxs-lookup"><span data-stu-id="de5d2-103">Specifies the columns on which the index is created for a user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de5d2-104">構文</span><span class="sxs-lookup"><span data-stu-id="de5d2-104">Syntax</span></span>  
  
```  
  
<Create>  
  <Index>  
    <Name>...</Name>  
    <Column [Type | SortOrder]>  
     ...code removed here...  
     </Column>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="de5d2-105">要素の属性</span><span class="sxs-lookup"><span data-stu-id="de5d2-105">Element Attributes</span></span>  
  
|<span data-ttu-id="de5d2-106">Column の属性</span><span class="sxs-lookup"><span data-stu-id="de5d2-106">Column Attribute</span></span>|<span data-ttu-id="de5d2-107">説明</span><span class="sxs-lookup"><span data-stu-id="de5d2-107">Description</span></span>|  
|----------------------|-----------------|  
|`Type`|<span data-ttu-id="de5d2-108">省略可能。</span><span class="sxs-lookup"><span data-stu-id="de5d2-108">Optional.</span></span> <span data-ttu-id="de5d2-109">インデックスの列の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="de5d2-109">Specifies the index column type.</span></span> <span data-ttu-id="de5d2-110">この属性を指定するには **string** データ型を使用します。指定できる値は次のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="de5d2-110">Use a **string** data type to specify this attribute with one of the following allowed values:</span></span><br /><br /> <span data-ttu-id="de5d2-111">`KeyColumn`:</span><span class="sxs-lookup"><span data-stu-id="de5d2-111">`KeyColumn`:</span></span><br />                  <span data-ttu-id="de5d2-112">列がインデックス キーによって参照されていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="de5d2-112">Specifies that the column is referenced by an index key.</span></span> <span data-ttu-id="de5d2-113">この属性を設定するには、以下の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="de5d2-113">Use the following syntax to set this attribute:</span></span><br />`<Column Type="KeyColumn">`<br /><span data-ttu-id="de5d2-114">キー列の詳細については、「 [クラスター化インデックスと非クラスター化インデックスの概念](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de5d2-114">For more information about key columns, see [Clustered and Nonclustered Indexes Described](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md).</span></span><br /><br /> <span data-ttu-id="de5d2-115">`IncludedColumn`: 列が (キー列ではなく) 付加列であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="de5d2-115">`IncludedColumn`: Specifies that the column is an included column (instead of a key column).</span></span> <span data-ttu-id="de5d2-116">この属性を設定するには、以下の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="de5d2-116">Use the following syntax to set this attribute:</span></span><br />`<Column Type="IncludedColumn">`<br /><span data-ttu-id="de5d2-117">付加列の詳細については、「 [付加列インデックスの作成](../../relational-databases/indexes/create-indexes-with-included-columns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de5d2-117">For more information about included columns, see [Create Indexes with Included Columns](../../relational-databases/indexes/create-indexes-with-included-columns.md).</span></span>|  
|`SortOrder`|<span data-ttu-id="de5d2-118">省略可能。</span><span class="sxs-lookup"><span data-stu-id="de5d2-118">Optional.</span></span> <span data-ttu-id="de5d2-119">列の並べ替え順を指定します。</span><span class="sxs-lookup"><span data-stu-id="de5d2-119">Specifies the sorting order of the column.</span></span> <span data-ttu-id="de5d2-120">**string** データ型を使用して、 **"Ascending"** または **"Descending"** の並べ替え順のいずれかを以下のように指定します。</span><span class="sxs-lookup"><span data-stu-id="de5d2-120">Use a **string** data type to specify either an **"Ascending"** or **"Descending"** sorting order as follows:</span></span><br /><br /> `<Column SortOrder="Ascending">`|  
  
## <a name="element-characteristics"></a><span data-ttu-id="de5d2-121">要素の特性</span><span class="sxs-lookup"><span data-stu-id="de5d2-121">Element Characteristics</span></span>  
  
|<span data-ttu-id="de5d2-122">特徴</span><span class="sxs-lookup"><span data-stu-id="de5d2-122">Characteristic</span></span>|<span data-ttu-id="de5d2-123">説明</span><span class="sxs-lookup"><span data-stu-id="de5d2-123">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="de5d2-124">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="de5d2-124">**Data type and length**</span></span>|<span data-ttu-id="de5d2-125">[なし] :</span><span class="sxs-lookup"><span data-stu-id="de5d2-125">None.</span></span>|  
|<span data-ttu-id="de5d2-126">**既定値**</span><span class="sxs-lookup"><span data-stu-id="de5d2-126">**Default value**</span></span>|<span data-ttu-id="de5d2-127">[なし] :</span><span class="sxs-lookup"><span data-stu-id="de5d2-127">None.</span></span>|  
|<span data-ttu-id="de5d2-128">**個数**</span><span class="sxs-lookup"><span data-stu-id="de5d2-128">**Occurrence**</span></span>|<span data-ttu-id="de5d2-129">`Index` 要素につき 1024 列まで指定できます。</span><span class="sxs-lookup"><span data-stu-id="de5d2-129">Can specify up to 1024 columns for the `Index` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="de5d2-130">要素の関係</span><span class="sxs-lookup"><span data-stu-id="de5d2-130">Element Relationships</span></span>  
  
|<span data-ttu-id="de5d2-131">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="de5d2-131">Relationship</span></span>|<span data-ttu-id="de5d2-132">要素</span><span class="sxs-lookup"><span data-stu-id="de5d2-132">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="de5d2-133">**親要素**</span><span class="sxs-lookup"><span data-stu-id="de5d2-133">**Parent element**</span></span>|[<span data-ttu-id="de5d2-134">Index 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="de5d2-134">Index Element &#40;DTA&#41;</span></span>](index-element-dta.md)|  
|<span data-ttu-id="de5d2-135">**子要素**</span><span class="sxs-lookup"><span data-stu-id="de5d2-135">**Child elements**</span></span>|[<span data-ttu-id="de5d2-136">Column の Name 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="de5d2-136">Name Element for Column &#40;DTA&#41;</span></span>](name-element-for-column-dta.md)|  
  
## <a name="example"></a><span data-ttu-id="de5d2-137">例</span><span class="sxs-lookup"><span data-stu-id="de5d2-137">Example</span></span>  
 <span data-ttu-id="de5d2-138">この要素の使用例については、「[ユーザー指定の構成を指定した XML 入力ファイルのサンプル &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de5d2-138">For a usage example of this element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de5d2-139">参照</span><span class="sxs-lookup"><span data-stu-id="de5d2-139">See Also</span></span>  
 [<span data-ttu-id="de5d2-140">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="de5d2-140">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
