---
title: Server の Name 要素 (DTA) |Microsoft Docs
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
ms.assetid: 4c94754d-6d62-4357-8ce7-f107ebf90c71
author: stevestein
ms.author: sstein
ms.openlocfilehash: 202258c3c87f8a35d1ee30b19880f5e9423fa394
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643064"
---
# <a name="name-element-for-server-dta"></a><span data-ttu-id="218fb-102">Server の Name 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="218fb-102">Name Element for Server (DTA)</span></span>
  <span data-ttu-id="218fb-103">チューニングするデータベースが置かれているサーバーの名前が含まれます。</span><span class="sxs-lookup"><span data-stu-id="218fb-103">Contains the name of the server where the databases you want to tune reside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="218fb-104">構文</span><span class="sxs-lookup"><span data-stu-id="218fb-104">Syntax</span></span>  
  
```  
  
...code removed here...  
<Server>  
    <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="218fb-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="218fb-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="218fb-106">特徴</span><span class="sxs-lookup"><span data-stu-id="218fb-106">Characteristic</span></span>|<span data-ttu-id="218fb-107">説明</span><span class="sxs-lookup"><span data-stu-id="218fb-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="218fb-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="218fb-108">**Data type and length**</span></span>|<span data-ttu-id="218fb-109">`string`、1 ～ 255 文字。</span><span class="sxs-lookup"><span data-stu-id="218fb-109">`string`, between 1 and 255 characters.</span></span>|  
|<span data-ttu-id="218fb-110">**既定値**</span><span class="sxs-lookup"><span data-stu-id="218fb-110">**Default value**</span></span>|<span data-ttu-id="218fb-111">[なし] :</span><span class="sxs-lookup"><span data-stu-id="218fb-111">None.</span></span>|  
|<span data-ttu-id="218fb-112">**個数**</span><span class="sxs-lookup"><span data-stu-id="218fb-112">**Occurrence**</span></span>|<span data-ttu-id="218fb-113">**Server** 要素につき 1 回の出現が必要です。</span><span class="sxs-lookup"><span data-stu-id="218fb-113">Required once per **Server** element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="218fb-114">要素の関係</span><span class="sxs-lookup"><span data-stu-id="218fb-114">Element Relationships</span></span>  
  
|<span data-ttu-id="218fb-115">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="218fb-115">Relationship</span></span>|<span data-ttu-id="218fb-116">要素</span><span class="sxs-lookup"><span data-stu-id="218fb-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="218fb-117">**親要素**</span><span class="sxs-lookup"><span data-stu-id="218fb-117">**Parent element**</span></span>|[<span data-ttu-id="218fb-118">Server 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="218fb-118">Server Element &#40;DTA&#41;</span></span>](server-element-dta.md)|  
|<span data-ttu-id="218fb-119">**子要素**</span><span class="sxs-lookup"><span data-stu-id="218fb-119">**Child elements**</span></span>|<span data-ttu-id="218fb-120">[なし] :</span><span class="sxs-lookup"><span data-stu-id="218fb-120">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="218fb-121">例</span><span class="sxs-lookup"><span data-stu-id="218fb-121">Example</span></span>  
 <span data-ttu-id="218fb-122">この **Name** 要素の使用例については、「 [Server 要素 &#40;DTA&#41;](server-element-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="218fb-122">For an example of how this **Name** element is used, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="218fb-123">参照</span><span class="sxs-lookup"><span data-stu-id="218fb-123">See Also</span></span>  
 [<span data-ttu-id="218fb-124">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="218fb-124">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
