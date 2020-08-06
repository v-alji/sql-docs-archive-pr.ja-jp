---
title: バナー要素 (ssbdiagnose) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- banner element
- XML output file format [ssbdiagnose], banner element
- ssbdiagnose
ms.assetid: cc6cd49a-acf0-4cfb-8c6a-554692b89de2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 13238ac4ef1745dea4fbf3392484ac6137c09df1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742725"
---
# <a name="banner-element-ssbdiagnose"></a><span data-ttu-id="e02d9-102">Banner 要素 (ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="e02d9-102">Banner Element (ssbdiagnose)</span></span>
  <span data-ttu-id="e02d9-103">**ssbdiagnose** の出力 XML ファイルを生成したユーティリティを示します。</span><span class="sxs-lookup"><span data-stu-id="e02d9-103">Identifies which utility generated the **ssbdiagnose** output XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e02d9-104">構文</span><span class="sxs-lookup"><span data-stu-id="e02d9-104">Syntax</span></span>  
  
```  
  
<Banner  
    title="..."   
    product="..."   
    version="..." />  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="e02d9-105">要素の属性</span><span class="sxs-lookup"><span data-stu-id="e02d9-105">Element Attributes</span></span>  
  
|<span data-ttu-id="e02d9-106">Attribute</span><span class="sxs-lookup"><span data-stu-id="e02d9-106">Attribute</span></span>|<span data-ttu-id="e02d9-107">説明</span><span class="sxs-lookup"><span data-stu-id="e02d9-107">Description</span></span>|  
|---------------|-----------------|  
|`title`|<span data-ttu-id="e02d9-108">**ssbdiagnose** の XML 出力ファイルを生成したユーティリティを示します。</span><span class="sxs-lookup"><span data-stu-id="e02d9-108">Identifies the utility that generated the **ssbdiagnose** XML output file.</span></span>|  
|`product`|<span data-ttu-id="e02d9-109">**ssbdiagnose** の XML 出力ファイルを生成した製品を示します。</span><span class="sxs-lookup"><span data-stu-id="e02d9-109">Identifies the product that generated the **ssbdiagnose** XML output file.</span></span>|  
|`version`|<span data-ttu-id="e02d9-110">XML 出力ファイルを生成したユーティリティのバージョンを示します。</span><span class="sxs-lookup"><span data-stu-id="e02d9-110">Identifies which version of the utility generated the XML output file.</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="e02d9-111">要素の特性</span><span class="sxs-lookup"><span data-stu-id="e02d9-111">Element Characteristics</span></span>  
  
|<span data-ttu-id="e02d9-112">特徴</span><span class="sxs-lookup"><span data-stu-id="e02d9-112">Characteristic</span></span>|<span data-ttu-id="e02d9-113">説明</span><span class="sxs-lookup"><span data-stu-id="e02d9-113">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e02d9-114">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="e02d9-114">**Data type and length**</span></span>|<span data-ttu-id="e02d9-115">[なし] :</span><span class="sxs-lookup"><span data-stu-id="e02d9-115">None.</span></span>|  
|<span data-ttu-id="e02d9-116">**既定値**</span><span class="sxs-lookup"><span data-stu-id="e02d9-116">**Default value**</span></span>|<span data-ttu-id="e02d9-117">[なし] :</span><span class="sxs-lookup"><span data-stu-id="e02d9-117">None.</span></span>|  
|<span data-ttu-id="e02d9-118">**個数**</span><span class="sxs-lookup"><span data-stu-id="e02d9-118">**Occurrence**</span></span>|<span data-ttu-id="e02d9-119">**ssbdiagnose** の出力 XML ファイルにつき 1 個。</span><span class="sxs-lookup"><span data-stu-id="e02d9-119">Occurs once per **ssbdiagnose** output XML file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="e02d9-120">要素の関係</span><span class="sxs-lookup"><span data-stu-id="e02d9-120">Element Relationships</span></span>  
  
|<span data-ttu-id="e02d9-121">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="e02d9-121">Relationship</span></span>|<span data-ttu-id="e02d9-122">要素</span><span class="sxs-lookup"><span data-stu-id="e02d9-122">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="e02d9-123">**親要素**</span><span class="sxs-lookup"><span data-stu-id="e02d9-123">**Parent element**</span></span>|[<span data-ttu-id="e02d9-124">DiagnosticInformation 要素 &#40;ssbdiagnose&#41;</span><span class="sxs-lookup"><span data-stu-id="e02d9-124">DiagnosticInformation Element &#40;ssbdiagnose&#41;</span></span>](diagnosticinformation-element-ssbdiagnose.md)|  
|<span data-ttu-id="e02d9-125">**子要素**</span><span class="sxs-lookup"><span data-stu-id="e02d9-125">**Child elements**</span></span>|<span data-ttu-id="e02d9-126">[なし] :</span><span class="sxs-lookup"><span data-stu-id="e02d9-126">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e02d9-127">例</span><span class="sxs-lookup"><span data-stu-id="e02d9-127">Example</span></span>  
 <span data-ttu-id="e02d9-128">バナー要素の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e02d9-128">This is an example of a banner element.</span></span>  
  
```  
<Banner title="Service Broker Diagnostics Utility" product="Microsoft SQL Server" version="10.0.1073.0" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="e02d9-129">参照</span><span class="sxs-lookup"><span data-stu-id="e02d9-129">See Also</span></span>  
 [<span data-ttu-id="e02d9-130">ssbdiagnose ユーティリティ &#40;Service Broker&#41;</span><span class="sxs-lookup"><span data-stu-id="e02d9-130">ssbdiagnose Utility &#40;Service Broker&#41;</span></span>](ssbdiagnose-utility-service-broker.md)  
  
  
