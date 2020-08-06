---
title: Database の Name 要素 (DTA) |Microsoft Docs
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
ms.assetid: e871c4fa-3b57-46cf-b4f8-e3be86f92dc4
author: stevestein
ms.author: sstein
ms.openlocfilehash: c692e31b9175bf05dcfb0504ea79e98cbb82f36b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711298"
---
# <a name="name-element-for-database-dta"></a><span data-ttu-id="ca062-102">Database の Name 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="ca062-102">Name Element for Database (DTA)</span></span>
  <span data-ttu-id="ca062-103">チューニングするデータベースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="ca062-103">Specifies the name of a database that you want to tune.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca062-104">構文</span><span class="sxs-lookup"><span data-stu-id="ca062-104">Syntax</span></span>  
  
```  
  
<Server>  
    <Database>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="ca062-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="ca062-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="ca062-106">特徴</span><span class="sxs-lookup"><span data-stu-id="ca062-106">Characteristic</span></span>|<span data-ttu-id="ca062-107">説明</span><span class="sxs-lookup"><span data-stu-id="ca062-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ca062-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="ca062-108">**Data type and length**</span></span>|<span data-ttu-id="ca062-109">`string`、長さは無制限です。</span><span class="sxs-lookup"><span data-stu-id="ca062-109">`string`, unlimited length.</span></span>|  
|<span data-ttu-id="ca062-110">**既定値**</span><span class="sxs-lookup"><span data-stu-id="ca062-110">**Default value**</span></span>|<span data-ttu-id="ca062-111">[なし] :</span><span class="sxs-lookup"><span data-stu-id="ca062-111">None.</span></span>|  
|<span data-ttu-id="ca062-112">**個数**</span><span class="sxs-lookup"><span data-stu-id="ca062-112">**Occurrence**</span></span>|<span data-ttu-id="ca062-113">必須。`Database` 要素につき 1 個。</span><span class="sxs-lookup"><span data-stu-id="ca062-113">Required once per `Database` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="ca062-114">要素の関係</span><span class="sxs-lookup"><span data-stu-id="ca062-114">Element Relationships</span></span>  
  
|<span data-ttu-id="ca062-115">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="ca062-115">Relationship</span></span>|<span data-ttu-id="ca062-116">要素</span><span class="sxs-lookup"><span data-stu-id="ca062-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="ca062-117">**親要素**</span><span class="sxs-lookup"><span data-stu-id="ca062-117">**Parent element**</span></span>|[<span data-ttu-id="ca062-118">Server の Database 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="ca062-118">Database Element for Server &#40;DTA&#41;</span></span>](database-element-for-server-dta.md)|  
|<span data-ttu-id="ca062-119">**子要素**</span><span class="sxs-lookup"><span data-stu-id="ca062-119">**Child elements**</span></span>|<span data-ttu-id="ca062-120">[なし] :</span><span class="sxs-lookup"><span data-stu-id="ca062-120">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ca062-121">例</span><span class="sxs-lookup"><span data-stu-id="ca062-121">Example</span></span>  
 <span data-ttu-id="ca062-122">この要素の使用例については、「[Server 要素 &#40;DTA&#41;](server-element-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca062-122">For a usage example of this element, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca062-123">参照</span><span class="sxs-lookup"><span data-stu-id="ca062-123">See Also</span></span>  
 [<span data-ttu-id="ca062-124">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="ca062-124">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
