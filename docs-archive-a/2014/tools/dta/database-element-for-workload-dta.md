---
title: ワークロードの Database 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: 112fca2a-37e5-4162-b2e7-b56eb8ab0c6f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2774bc7ed981c84c966a394c95347208cbc6d656
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711337"
---
# <a name="database-element-for-workload-dta"></a><span data-ttu-id="8731a-102">Workload の Database 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="8731a-102">Database Element for Workload (DTA)</span></span>
  <span data-ttu-id="8731a-103">ワークロード トレース テーブルのあるデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="8731a-103">Specifies the database where the workload trace table is located.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8731a-104">構文</span><span class="sxs-lookup"><span data-stu-id="8731a-104">Syntax</span></span>  
  
```  
  
<Workload>  
  <Database>  
   ...code removed here...  
  </Database>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="8731a-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="8731a-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="8731a-106">特徴</span><span class="sxs-lookup"><span data-stu-id="8731a-106">Characteristic</span></span>|<span data-ttu-id="8731a-107">説明</span><span class="sxs-lookup"><span data-stu-id="8731a-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="8731a-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="8731a-108">**Data type and length**</span></span>|<span data-ttu-id="8731a-109">[なし] :</span><span class="sxs-lookup"><span data-stu-id="8731a-109">None.</span></span>|  
|<span data-ttu-id="8731a-110">**既定値**</span><span class="sxs-lookup"><span data-stu-id="8731a-110">**Default value**</span></span>|<span data-ttu-id="8731a-111">[なし] :</span><span class="sxs-lookup"><span data-stu-id="8731a-111">None.</span></span>|  
|<span data-ttu-id="8731a-112">**個数**</span><span class="sxs-lookup"><span data-stu-id="8731a-112">**Occurrence**</span></span>|<span data-ttu-id="8731a-113">他の種類のワークロードが指定されていない場合は、1 回の出現が必要です。</span><span class="sxs-lookup"><span data-stu-id="8731a-113">Required once if no other type of workload is specified.</span></span> <span data-ttu-id="8731a-114">`EventString` 親要素に対しては、`File`、`Database`、または `Workload` 子要素を指定する必要がありますが、使用できるのは 1 種類だけです。</span><span class="sxs-lookup"><span data-stu-id="8731a-114">You must specify an `EventString`, a `File`, or a `Database` child element for the `Workload` parent, but only one type can be used.</span></span> <span data-ttu-id="8731a-115">たとえば、ワークロードを `Database` 要素で指定した場合、同じ XML 入力ファイル内でワークロードを `File` 要素で指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="8731a-115">For example, if you specify a workload with the `Database` element, you cannot also specify a workload with the `File` element in the same XML input file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="8731a-116">要素の関係</span><span class="sxs-lookup"><span data-stu-id="8731a-116">Element Relationships</span></span>  
  
|<span data-ttu-id="8731a-117">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="8731a-117">Relationship</span></span>|<span data-ttu-id="8731a-118">要素</span><span class="sxs-lookup"><span data-stu-id="8731a-118">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="8731a-119">**親要素**</span><span class="sxs-lookup"><span data-stu-id="8731a-119">**Parent element**</span></span>|[<span data-ttu-id="8731a-120">Workload 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="8731a-120">Workload Element &#40;DTA&#41;</span></span>](workload-element-dta.md)|  
|<span data-ttu-id="8731a-121">**子要素**</span><span class="sxs-lookup"><span data-stu-id="8731a-121">**Child elements**</span></span>|[<span data-ttu-id="8731a-122">Database の Name 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="8731a-122">Name Element for Database &#40;DTA&#41;</span></span>](name-element-for-database-dta.md)<br /><br /> [<span data-ttu-id="8731a-123">Database の Schema 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="8731a-123">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="8731a-124">解説</span><span class="sxs-lookup"><span data-stu-id="8731a-124">Remarks</span></span>  
 <span data-ttu-id="8731a-125">この要素は、データベース エンジン チューニング アドバイザー XML スキーマの **DatabaseDetailsTypecomplexType** の名前です。</span><span class="sxs-lookup"><span data-stu-id="8731a-125">This element is of the **DatabaseDetailsTypecomplexType** name in the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="8731a-126">この `Database` 要素を、ルートの親要素が `Configuration` 要素である他の要素と混同しないでください。</span><span class="sxs-lookup"><span data-stu-id="8731a-126">Do not confuse this `Database` element with the one whose root parent is the `Configuration` element.</span></span> <span data-ttu-id="8731a-127">(「[Configuration の Database 要素 &#40;DTA&#41;](database-element-for-configuration-dta.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="8731a-127">(See [Database Element for Configuration &#40;DTA&#41;](database-element-for-configuration-dta.md).)</span></span>  
  
## <a name="example"></a><span data-ttu-id="8731a-128">例</span><span class="sxs-lookup"><span data-stu-id="8731a-128">Example</span></span>  
 <span data-ttu-id="8731a-129">この要素の使用例につい `Database` ては、「[ワークロード要素 &#40;DTA&#41;](workload-element-dta.md)」のコード例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8731a-129">For a usage example of this `Database` element, see the code example in [Workload Element &#40;DTA&#41;](workload-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8731a-130">参照</span><span class="sxs-lookup"><span data-stu-id="8731a-130">See Also</span></span>  
 [<span data-ttu-id="8731a-131">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="8731a-131">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
