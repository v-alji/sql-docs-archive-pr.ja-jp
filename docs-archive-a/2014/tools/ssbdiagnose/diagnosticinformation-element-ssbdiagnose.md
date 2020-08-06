---
title: DiagnosticInformation 要素 (ssbdiagnose) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose], diagnosticinformation element
- diagnosticinformation element
- ssbdiagnose
ms.assetid: 0cfda544-542c-4cf4-86d2-8031c91b10f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 92d76a065c24ddc1fc8d85989ed3202308571951
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633711"
---
# <a name="diagnosticinformation-element-ssbdiagnose"></a><span data-ttu-id="2cf43-102">DiagnosticInformation 要素 (ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="2cf43-102">DiagnosticInformation Element (ssbdiagnose)</span></span>
  <span data-ttu-id="2cf43-103">**DiagnosticInformation** 要素には、ユーティリティによって検出された診断情報を報告するすべての要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2cf43-103">The **DiagnosticInformation** element contains all elements that report the diagnostic information found by the utility.</span></span> <span data-ttu-id="2cf43-104">**DiagnosticInformation** は、 **ssbdiagnostic** XML 出力ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="2cf43-104">**DiagnosticInformation** is the root element of a **ssbdiagnostic** XML output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cf43-105">構文</span><span class="sxs-lookup"><span data-stu-id="2cf43-105">Syntax</span></span>  
  
```  
  
<DiagnosticInformation>   
    ...   
</DiagnosticInformation>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="2cf43-106">要素の属性</span><span class="sxs-lookup"><span data-stu-id="2cf43-106">Element Attributes</span></span>  
  
|<span data-ttu-id="2cf43-107">属性</span><span class="sxs-lookup"><span data-stu-id="2cf43-107">Attribute</span></span>|<span data-ttu-id="2cf43-108">説明</span><span class="sxs-lookup"><span data-stu-id="2cf43-108">Description</span></span>|  
|---------------|-----------------|  
|`None`|<span data-ttu-id="2cf43-109">該当なし</span><span class="sxs-lookup"><span data-stu-id="2cf43-109">N/A</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="2cf43-110">要素の特性</span><span class="sxs-lookup"><span data-stu-id="2cf43-110">Element Characteristics</span></span>  
  
|<span data-ttu-id="2cf43-111">特徴</span><span class="sxs-lookup"><span data-stu-id="2cf43-111">Characteristic</span></span>|<span data-ttu-id="2cf43-112">説明</span><span class="sxs-lookup"><span data-stu-id="2cf43-112">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="2cf43-113">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="2cf43-113">**Data type and length**</span></span>|<span data-ttu-id="2cf43-114">[なし] :</span><span class="sxs-lookup"><span data-stu-id="2cf43-114">None.</span></span>|  
|<span data-ttu-id="2cf43-115">**既定値**</span><span class="sxs-lookup"><span data-stu-id="2cf43-115">**Default value**</span></span>|<span data-ttu-id="2cf43-116">[なし] :</span><span class="sxs-lookup"><span data-stu-id="2cf43-116">None.</span></span>|  
|<span data-ttu-id="2cf43-117">**個数**</span><span class="sxs-lookup"><span data-stu-id="2cf43-117">**Occurrence**</span></span>|<span data-ttu-id="2cf43-118">**ssbdiagnose** XML 出力ファイルごとに 1 つ。</span><span class="sxs-lookup"><span data-stu-id="2cf43-118">Once per **ssbdiagnose** XML output file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="2cf43-119">要素の関係</span><span class="sxs-lookup"><span data-stu-id="2cf43-119">Element Relationships</span></span>  
  
|<span data-ttu-id="2cf43-120">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="2cf43-120">Relationship</span></span>|<span data-ttu-id="2cf43-121">要素</span><span class="sxs-lookup"><span data-stu-id="2cf43-121">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="2cf43-122">**親要素**</span><span class="sxs-lookup"><span data-stu-id="2cf43-122">**Parent element**</span></span>|<span data-ttu-id="2cf43-123">[なし] :</span><span class="sxs-lookup"><span data-stu-id="2cf43-123">None.</span></span>|  
|<span data-ttu-id="2cf43-124">**子要素**</span><span class="sxs-lookup"><span data-stu-id="2cf43-124">**Child elements**</span></span>|[<span data-ttu-id="2cf43-125">Banner 要素 &#40;ssbdiagnose&#41;</span><span class="sxs-lookup"><span data-stu-id="2cf43-125">Banner Element &#40;ssbdiagnose&#41;</span></span>](banner-element-ssbdiagnose.md)<br /><br /> [<span data-ttu-id="2cf43-126">Issue 要素 &#40;ssbdiagnose&#41;</span><span class="sxs-lookup"><span data-stu-id="2cf43-126">Issue Element &#40;ssbdiagnose&#41;</span></span>](issue-element-ssbdiagnose.md)|  
  
## <a name="remarks"></a><span data-ttu-id="2cf43-127">解説</span><span class="sxs-lookup"><span data-stu-id="2cf43-127">Remarks</span></span>  
 <span data-ttu-id="2cf43-128">XML 名前空間の詳細については、 [MSDN Library の「](https://go.microsoft.com/fwlink/?LinkId=7341) XML ドキュメントにおける名前空間 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cf43-128">For more information about XML namespaces, see [Namespaces in an XML Document](https://go.microsoft.com/fwlink/?LinkId=7341) in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN Library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cf43-129">参照</span><span class="sxs-lookup"><span data-stu-id="2cf43-129">See Also</span></span>  
 [<span data-ttu-id="2cf43-130">ssbdiagnose ユーティリティ &#40;Service Broker&#41;</span><span class="sxs-lookup"><span data-stu-id="2cf43-130">ssbdiagnose Utility &#40;Service Broker&#41;</span></span>](ssbdiagnose-utility-service-broker.md)  
  
  
