---
title: Configuration の Server 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: da9ff870-9cfd-42fe-994b-7b9292681f7d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 88182cdad2e7313f0910a106ee37d727d840bfed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643053"
---
# <a name="server-element-for-configuration-dta"></a><span data-ttu-id="0f097-102">Configuration の Server 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="0f097-102">Server Element for Configuration (DTA)</span></span>
  <span data-ttu-id="0f097-103">データベース エンジン チューニング アドバイザーで仮想的な構成 (`Configuration` 要素で指定する構成) を評価する対象のサーバーの識別情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0f097-103">Contains the identifying information for the server where you want Database Engine Tuning Advisor to evaluate the hypothetical configuration (specified by the `Configuration` element).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f097-104">構文</span><span class="sxs-lookup"><span data-stu-id="0f097-104">Syntax</span></span>  
  
```  
  
<Configuration>  
    <Server>  
...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="0f097-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="0f097-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="0f097-106">特徴</span><span class="sxs-lookup"><span data-stu-id="0f097-106">Characteristic</span></span>|<span data-ttu-id="0f097-107">説明</span><span class="sxs-lookup"><span data-stu-id="0f097-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="0f097-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="0f097-108">**Data type and length**</span></span>|<span data-ttu-id="0f097-109">[なし] :</span><span class="sxs-lookup"><span data-stu-id="0f097-109">None.</span></span>|  
|<span data-ttu-id="0f097-110">**既定値**</span><span class="sxs-lookup"><span data-stu-id="0f097-110">**Default value**</span></span>|<span data-ttu-id="0f097-111">[なし] :</span><span class="sxs-lookup"><span data-stu-id="0f097-111">None.</span></span>|  
|<span data-ttu-id="0f097-112">**個数**</span><span class="sxs-lookup"><span data-stu-id="0f097-112">**Occurrence**</span></span>|<span data-ttu-id="0f097-113">必須。`Configuration` 要素につき 1 個。</span><span class="sxs-lookup"><span data-stu-id="0f097-113">Required once per `Configuration` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="0f097-114">要素の関係</span><span class="sxs-lookup"><span data-stu-id="0f097-114">Element Relationships</span></span>  
  
|<span data-ttu-id="0f097-115">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="0f097-115">Relationship</span></span>|<span data-ttu-id="0f097-116">要素</span><span class="sxs-lookup"><span data-stu-id="0f097-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="0f097-117">**親要素**</span><span class="sxs-lookup"><span data-stu-id="0f097-117">**Parent element**</span></span>|[<span data-ttu-id="0f097-118">Configuration 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f097-118">Configuration Element &#40;DTA&#41;</span></span>](configuration-element-dta.md)|  
|<span data-ttu-id="0f097-119">**子要素**</span><span class="sxs-lookup"><span data-stu-id="0f097-119">**Child elements**</span></span>|[<span data-ttu-id="0f097-120">Server の Name 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f097-120">Name Element for Server &#40;DTA&#41;</span></span>](name-element-for-server-dta.md)<br /><br /> [<span data-ttu-id="0f097-121">Configuration の Database 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f097-121">Database Element for Configuration &#40;DTA&#41;</span></span>](database-element-for-configuration-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="0f097-122">解説</span><span class="sxs-lookup"><span data-stu-id="0f097-122">Remarks</span></span>  
 <span data-ttu-id="0f097-123">要素に指定できる要素は1つだけ `Server` `Configuration` です。</span><span class="sxs-lookup"><span data-stu-id="0f097-123">You can specify only one `Server` element for the `Configuration` element.</span></span> <span data-ttu-id="0f097-124">この要素は、 **データベース エンジン チューニング アドバイザー XML スキーマ** の [ServerTypecomplexType](https://go.microsoft.com/fwlink/?linkid=43100)の名前です。</span><span class="sxs-lookup"><span data-stu-id="0f097-124">This element is of the **ServerTypecomplexType** name in the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span> <span data-ttu-id="0f097-125">この `Server` 要素を `DTAInput` 要素の子要素と混同しないでください。</span><span class="sxs-lookup"><span data-stu-id="0f097-125">Do not confuse this `Server` element with the one that is the child of the `DTAInput` element.</span></span> <span data-ttu-id="0f097-126">詳しくは、「[Server 要素 &#40;DTA&#41;](server-element-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f097-126">For more information, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f097-127">例</span><span class="sxs-lookup"><span data-stu-id="0f097-127">Example</span></span>  
 <span data-ttu-id="0f097-128">使用例については、「[ユーザー指定の構成を指定した XML 入力ファイルのサンプル &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f097-128">For a usage example, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f097-129">参照</span><span class="sxs-lookup"><span data-stu-id="0f097-129">See Also</span></span>  
 [<span data-ttu-id="0f097-130">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="0f097-130">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
