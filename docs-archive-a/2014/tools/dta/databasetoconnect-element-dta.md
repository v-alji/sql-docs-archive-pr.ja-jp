---
title: DatabaseToConnect 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DatabaseToConnect element
ms.assetid: 65153a66-3aee-4429-99b7-0816ac23c285
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4c21b36319e4007264677d499b84964c7cb5ea7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711329"
---
# <a name="databasetoconnect-element-dta"></a><span data-ttu-id="3ee78-102">DatabaseToConnect 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="3ee78-102">DatabaseToConnect Element (DTA)</span></span>
  <span data-ttu-id="3ee78-103">データベース エンジン チューニング アドバイザーがワークロードのチューニング時に最初に接続するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="3ee78-103">Specifies the first database to which Database Engine Tuning Advisor connects when tuning a workload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ee78-104">構文</span><span class="sxs-lookup"><span data-stu-id="3ee78-104">Syntax</span></span>  
  
```  
  
    <TuningOptions>  
...code removed here...  
      <DatabaseToConnect>...</DatabaseToConnect>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="3ee78-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="3ee78-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="3ee78-106">特徴</span><span class="sxs-lookup"><span data-stu-id="3ee78-106">Characteristic</span></span>|<span data-ttu-id="3ee78-107">説明</span><span class="sxs-lookup"><span data-stu-id="3ee78-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="3ee78-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="3ee78-108">**Data type and length**</span></span>|<span data-ttu-id="3ee78-109">`string`、長さは無制限です。</span><span class="sxs-lookup"><span data-stu-id="3ee78-109">`string`, unlimited length.</span></span>|  
|<span data-ttu-id="3ee78-110">**既定値**</span><span class="sxs-lookup"><span data-stu-id="3ee78-110">**Default value**</span></span>|<span data-ttu-id="3ee78-111">[なし] :</span><span class="sxs-lookup"><span data-stu-id="3ee78-111">None.</span></span>|  
|<span data-ttu-id="3ee78-112">**個数**</span><span class="sxs-lookup"><span data-stu-id="3ee78-112">**Occurrence**</span></span>|<span data-ttu-id="3ee78-113">省略可能。</span><span class="sxs-lookup"><span data-stu-id="3ee78-113">Optional.</span></span> <span data-ttu-id="3ee78-114">`TuningOptions` 要素につき 1 回使用できます。</span><span class="sxs-lookup"><span data-stu-id="3ee78-114">Can use once for each `TuningOptions` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="3ee78-115">要素の関係</span><span class="sxs-lookup"><span data-stu-id="3ee78-115">Element Relationships</span></span>  
  
|<span data-ttu-id="3ee78-116">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="3ee78-116">Relationship</span></span>|<span data-ttu-id="3ee78-117">要素</span><span class="sxs-lookup"><span data-stu-id="3ee78-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="3ee78-118">**親要素**</span><span class="sxs-lookup"><span data-stu-id="3ee78-118">**Parent element**</span></span>|[<span data-ttu-id="3ee78-119">TuningOptions 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="3ee78-119">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="3ee78-120">**子要素**</span><span class="sxs-lookup"><span data-stu-id="3ee78-120">**Child elements**</span></span>|<span data-ttu-id="3ee78-121">なし</span><span class="sxs-lookup"><span data-stu-id="3ee78-121">None</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ee78-122">解説</span><span class="sxs-lookup"><span data-stu-id="3ee78-122">Remarks</span></span>  
 <span data-ttu-id="3ee78-123">`DatabaseToConnect` は、データベース エンジン チューニング アドバイザーがチューニング セッションの開始時に最初に接続するデータベースの名前を指定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="3ee78-123">Use `DatabaseToConnect` to specify the name of the first database to which you want Database Engine Tuning Advisor to connect when it starts the tuning session.</span></span> <span data-ttu-id="3ee78-124">この要素では、データベースを 1 つだけ指定できます。</span><span class="sxs-lookup"><span data-stu-id="3ee78-124">You can specify only one database with this element.</span></span> <span data-ttu-id="3ee78-125">複数のデータベース名が指定されていると、データベース エンジン チューニング アドバイザーはエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="3ee78-125">If multiple database names are specified, Database Engine Tuning Advisor returns an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ee78-126">例</span><span class="sxs-lookup"><span data-stu-id="3ee78-126">Example</span></span>  
 <span data-ttu-id="3ee78-127">使用例については、「[インライン ワークロードを指定した XML 入力ファイルのサンプル &#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ee78-127">For a usage example, see the [XML Input File Sample with Inline Workload &#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ee78-128">参照</span><span class="sxs-lookup"><span data-stu-id="3ee78-128">See Also</span></span>  
 [<span data-ttu-id="3ee78-129">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="3ee78-129">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
