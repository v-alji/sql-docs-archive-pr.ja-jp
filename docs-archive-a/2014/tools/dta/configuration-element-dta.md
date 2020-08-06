---
title: Configuration 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Configuration element
ms.assetid: 1478e56f-57c4-4441-bac9-1ac91453839b
author: stevestein
ms.author: sstein
ms.openlocfilehash: d11938d9a9a694f994a3ea977022a393cbae23d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711358"
---
# <a name="configuration-element-dta"></a><span data-ttu-id="45d69-102">Configuration 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="45d69-102">Configuration Element (DTA)</span></span>
  <span data-ttu-id="45d69-103">ワークロードのチューニング時にデータベース エンジン チューニング アドバイザーが分析する、既存の仮想物理設計構造から成るユーザー指定の構成を指定します。</span><span class="sxs-lookup"><span data-stu-id="45d69-103">Specifies a user-specified configuration consisting of existing and hypothetical physical design structures for the Database Engine Tuning Advisor to analyze when tuning a workload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45d69-104">構文</span><span class="sxs-lookup"><span data-stu-id="45d69-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
    <Server>...</Server>  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions  
    <Configuration [SpecificationMode="Relative" | "Absolute"]>  
    ...code removed here...  
    </Configuration>  
</DTAInput>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="45d69-105">要素の属性</span><span class="sxs-lookup"><span data-stu-id="45d69-105">Element Attributes</span></span>  
  
|<span data-ttu-id="45d69-106">Configuration の属性</span><span class="sxs-lookup"><span data-stu-id="45d69-106">Configuration Attribute</span></span>|<span data-ttu-id="45d69-107">説明</span><span class="sxs-lookup"><span data-stu-id="45d69-107">Description</span></span>|  
|-----------------------------|-----------------|  
|`SpecificationMode`|<span data-ttu-id="45d69-108">省略可能。</span><span class="sxs-lookup"><span data-stu-id="45d69-108">Optional.</span></span> <span data-ttu-id="45d69-109">データベース エンジン チューニング アドバイザーが、指定された構成を既存の構成との関連で分析を行うか、それともまったく新しい独立した構成として分析を行うかを指定します。</span><span class="sxs-lookup"><span data-stu-id="45d69-109">Specifies whether Database Engine Tuning Advisor should analyze the specified configuration in relation to the current existing configuration, or as a completely new, standalone one.</span></span> <span data-ttu-id="45d69-110">この属性を指定するには **string** データ型を使用します。指定できる値は次のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="45d69-110">Use a **string** data type to specify this attribute with one of the following allowed values:</span></span><br /><br /> <span data-ttu-id="45d69-111">`Relative`:</span><span class="sxs-lookup"><span data-stu-id="45d69-111">`Relative`:</span></span> <br />                  <span data-ttu-id="45d69-112">指定された構成を、チューニングしているデータベースにある物理設計構造の現在の既存構成 (インデックス、インデックス付きビュー、パーティション) との関連で評価します。</span><span class="sxs-lookup"><span data-stu-id="45d69-112">Evaluates the specified configuration in relation to the current existing configuration of physical design structures (indexes, indexed views, partitioning) in the database that is being tuned.</span></span> <span data-ttu-id="45d69-113">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="45d69-113">For example:</span></span> <br />`<Configuration SpecificationMode="Relative">`<br /><br /> <span data-ttu-id="45d69-114">`Absolute`:</span><span class="sxs-lookup"><span data-stu-id="45d69-114">`Absolute`:</span></span> <br />                  <span data-ttu-id="45d69-115">指定された構成を、独立した構成として評価します。</span><span class="sxs-lookup"><span data-stu-id="45d69-115">Evaluates the specified configuration as a standalone configuration.</span></span> <span data-ttu-id="45d69-116">Absolute が指定されると、データベース エンジン チューニング アドバイザーは既存の構成を考慮しません。</span><span class="sxs-lookup"><span data-stu-id="45d69-116">When Absolute is specified, Database Engine Tuning Advisor does not consider the existing configuration.</span></span> <span data-ttu-id="45d69-117">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="45d69-117">For example:</span></span><br />`<Configuration SpecificationMode="Absolute">`|  
  
## <a name="element-characteristics"></a><span data-ttu-id="45d69-118">要素の特性</span><span class="sxs-lookup"><span data-stu-id="45d69-118">Element Characteristics</span></span>  
  
|<span data-ttu-id="45d69-119">特徴</span><span class="sxs-lookup"><span data-stu-id="45d69-119">Characteristic</span></span>|<span data-ttu-id="45d69-120">説明</span><span class="sxs-lookup"><span data-stu-id="45d69-120">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="45d69-121">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="45d69-121">**Data type and length**</span></span>|<span data-ttu-id="45d69-122">[なし] :</span><span class="sxs-lookup"><span data-stu-id="45d69-122">None.</span></span>|  
|<span data-ttu-id="45d69-123">**既定値**</span><span class="sxs-lookup"><span data-stu-id="45d69-123">**Default value**</span></span>|<span data-ttu-id="45d69-124">[なし] :</span><span class="sxs-lookup"><span data-stu-id="45d69-124">None.</span></span>|  
|<span data-ttu-id="45d69-125">**個数**</span><span class="sxs-lookup"><span data-stu-id="45d69-125">**Occurrence**</span></span>|<span data-ttu-id="45d69-126">省略可能。</span><span class="sxs-lookup"><span data-stu-id="45d69-126">Optional.</span></span> <span data-ttu-id="45d69-127">`DTAInput` 要素につき 1 回使用できます。</span><span class="sxs-lookup"><span data-stu-id="45d69-127">Can use once for each `DTAInput` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="45d69-128">要素の関係</span><span class="sxs-lookup"><span data-stu-id="45d69-128">Element Relationships</span></span>  
  
|<span data-ttu-id="45d69-129">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="45d69-129">Relationship</span></span>|<span data-ttu-id="45d69-130">要素</span><span class="sxs-lookup"><span data-stu-id="45d69-130">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="45d69-131">**親要素**</span><span class="sxs-lookup"><span data-stu-id="45d69-131">**Parent element**</span></span>|[<span data-ttu-id="45d69-132">DTAInput 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="45d69-132">DTAInput Element &#40;DTA&#41;</span></span>](dtainput-element-dta.md)|  
|<span data-ttu-id="45d69-133">**子要素**</span><span class="sxs-lookup"><span data-stu-id="45d69-133">**Child elements**</span></span>|[<span data-ttu-id="45d69-134">Configuration の Server 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="45d69-134">Server Element for Configuration &#40;DTA&#41;</span></span>](server-element-for-configuration-dta.md)|  
  
## <a name="example"></a><span data-ttu-id="45d69-135">例</span><span class="sxs-lookup"><span data-stu-id="45d69-135">Example</span></span>  
 <span data-ttu-id="45d69-136">この要素の使用例については、「[ユーザー指定の構成を指定した XML 入力ファイルのサンプル &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45d69-136">For a usage example of this element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45d69-137">参照</span><span class="sxs-lookup"><span data-stu-id="45d69-137">See Also</span></span>  
 [<span data-ttu-id="45d69-138">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="45d69-138">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
