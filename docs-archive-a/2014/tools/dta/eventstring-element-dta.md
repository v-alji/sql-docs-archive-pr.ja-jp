---
title: EventString 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- EventString element
ms.assetid: f76c37b4-2f6e-4274-8ee2-87e89d98e8a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 981cd0be06fd0972426fcb2fa67b0c4143cf9178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737315"
---
# <a name="eventstring-element-dta"></a><span data-ttu-id="e1faf-102">EventString 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="e1faf-102">EventString Element (DTA)</span></span>
  <span data-ttu-id="e1faf-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ワークロードを XML 入力ファイルで直接指定します。</span><span class="sxs-lookup"><span data-stu-id="e1faf-103">Specifies a [!INCLUDE[tsql](../../includes/tsql-md.md)] script workload directly in the XML input file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1faf-104">構文</span><span class="sxs-lookup"><span data-stu-id="e1faf-104">Syntax</span></span>  
  
```  
  
<Workload>  
    <EventString Weight="...">  
    ...code removed here...  
    </EventString>  
</Workload>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="e1faf-105">要素の属性</span><span class="sxs-lookup"><span data-stu-id="e1faf-105">Element Attributes</span></span>  
  
|<span data-ttu-id="e1faf-106">属性</span><span class="sxs-lookup"><span data-stu-id="e1faf-106">Attribute</span></span>|<span data-ttu-id="e1faf-107">説明</span><span class="sxs-lookup"><span data-stu-id="e1faf-107">Description</span></span>|  
|---------------|-----------------|  
|`Weight`|<span data-ttu-id="e1faf-108">省略可能。</span><span class="sxs-lookup"><span data-stu-id="e1faf-108">Optional.</span></span> <span data-ttu-id="e1faf-109">対象のイベントに関するクエリの重み係数 (重要度の係数) を指定します。</span><span class="sxs-lookup"><span data-stu-id="e1faf-109">Specifies the query weight factor (a factor of importance) for the specified event.</span></span> <span data-ttu-id="e1faf-110">重み係数の指定には、`float` データ型を使用します。</span><span class="sxs-lookup"><span data-stu-id="e1faf-110">Use a `float` data type to specify the weight.</span></span> <span data-ttu-id="e1faf-111">たとえば、`Weight`="100.01" のようにします。</span><span class="sxs-lookup"><span data-stu-id="e1faf-111">For example, `Weight`="100.01".</span></span> <span data-ttu-id="e1faf-112">`Weight` に指定できる最小値は「0」です。</span><span class="sxs-lookup"><span data-stu-id="e1faf-112">The minimum value you can specify for `Weight` is "0".</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="e1faf-113">要素の特性</span><span class="sxs-lookup"><span data-stu-id="e1faf-113">Element Characteristics</span></span>  
  
|<span data-ttu-id="e1faf-114">特徴</span><span class="sxs-lookup"><span data-stu-id="e1faf-114">Characteristic</span></span>|<span data-ttu-id="e1faf-115">説明</span><span class="sxs-lookup"><span data-stu-id="e1faf-115">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e1faf-116">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="e1faf-116">**Data type and length**</span></span>|<span data-ttu-id="e1faf-117">`string`、長さは無制限です。</span><span class="sxs-lookup"><span data-stu-id="e1faf-117">`string`, length is unlimited.</span></span>|  
|<span data-ttu-id="e1faf-118">**既定値**</span><span class="sxs-lookup"><span data-stu-id="e1faf-118">**Default value**</span></span>|<span data-ttu-id="e1faf-119">[なし] :</span><span class="sxs-lookup"><span data-stu-id="e1faf-119">None.</span></span>|  
|<span data-ttu-id="e1faf-120">**個数**</span><span class="sxs-lookup"><span data-stu-id="e1faf-120">**Occurrence**</span></span>|<span data-ttu-id="e1faf-121">他の種類のワークロードが指定されていない場合は、1 回の出現が必要です。</span><span class="sxs-lookup"><span data-stu-id="e1faf-121">Required once if no other type of workload is specified.</span></span> <span data-ttu-id="e1faf-122">`EventString` 親要素に対しては、`File`、`Database`、または `Workload` 子要素を指定する必要がありますが、使用できるのは 1 種類だけです。</span><span class="sxs-lookup"><span data-stu-id="e1faf-122">You must specify an `EventString`, a `File`, or a `Database` child element for the `Workload` parent, but only one type can be used.</span></span> <span data-ttu-id="e1faf-123">たとえば、`EventString` 要素を使用してワークロードを指定した場合は、同じ XML 入力ファイル内でワークロードを `File` 要素で指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="e1faf-123">For example, if you specify a workload with the `EventString` element, then you cannot also specify a workload with the `File` element in the same XML input file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="e1faf-124">要素の関係</span><span class="sxs-lookup"><span data-stu-id="e1faf-124">Element Relationships</span></span>  
  
|<span data-ttu-id="e1faf-125">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="e1faf-125">Relationship</span></span>|<span data-ttu-id="e1faf-126">要素</span><span class="sxs-lookup"><span data-stu-id="e1faf-126">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="e1faf-127">**親要素**</span><span class="sxs-lookup"><span data-stu-id="e1faf-127">**Parent element**</span></span>|[<span data-ttu-id="e1faf-128">Workload 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="e1faf-128">Workload Element &#40;DTA&#41;</span></span>](workload-element-dta.md)|  
|<span data-ttu-id="e1faf-129">**子要素**</span><span class="sxs-lookup"><span data-stu-id="e1faf-129">**Child elements**</span></span>|<span data-ttu-id="e1faf-130">[なし] :</span><span class="sxs-lookup"><span data-stu-id="e1faf-130">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e1faf-131">例</span><span class="sxs-lookup"><span data-stu-id="e1faf-131">Example</span></span>  
 <span data-ttu-id="e1faf-132">この要素の使用例については、「[インライン ワークロードを使用した XML 入力ファイルのサンプル &#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1faf-132">For a usage example of this element, see the [XML Input File Sample with Inline Workload &#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md) .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1faf-133">参照</span><span class="sxs-lookup"><span data-stu-id="e1faf-133">See Also</span></span>  
 [<span data-ttu-id="e1faf-134">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="e1faf-134">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
