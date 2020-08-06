---
title: DropOnlyMode 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DropOnlyMode element
ms.assetid: 80960676-7581-4074-889b-80ee665963dd
author: stevestein
ms.author: sstein
ms.openlocfilehash: b274dc394a933308cf2161cc271d09b8391900c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711325"
---
# <a name="droponlymode-element-dta"></a><span data-ttu-id="45701-102">DropOnlyMode 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="45701-102">DropOnlyMode Element (DTA)</span></span>
  <span data-ttu-id="45701-103">データベース エンジン チューニング アドバイザーのチューニング セッションで、既存のインデックス、インデックス付きビュー、パーティションの削除だけを対象にすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="45701-103">Specifies that Database Engine Tuning Advisor should only consider dropping existing indexes, indexed views, or partitions during the tuning session.</span></span> <span data-ttu-id="45701-104">このチューニング オプションを指定すると、新しい物理設計構造は考慮の対象になりません。</span><span class="sxs-lookup"><span data-stu-id="45701-104">No new physical design structures are considered when this tuning option is specified.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45701-105">構文</span><span class="sxs-lookup"><span data-stu-id="45701-105">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <DropOnlyMode>...</DropOnlyMode>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="45701-106">要素の特性</span><span class="sxs-lookup"><span data-stu-id="45701-106">Element Characteristics</span></span>  
  
|<span data-ttu-id="45701-107">特徴</span><span class="sxs-lookup"><span data-stu-id="45701-107">Characteristic</span></span>|<span data-ttu-id="45701-108">説明</span><span class="sxs-lookup"><span data-stu-id="45701-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="45701-109">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="45701-109">**Data type and length**</span></span>|<span data-ttu-id="45701-110">[なし] :</span><span class="sxs-lookup"><span data-stu-id="45701-110">None.</span></span>|  
|<span data-ttu-id="45701-111">**既定値**</span><span class="sxs-lookup"><span data-stu-id="45701-111">**Default value**</span></span>|<span data-ttu-id="45701-112">[なし] :</span><span class="sxs-lookup"><span data-stu-id="45701-112">None.</span></span>|  
|<span data-ttu-id="45701-113">**個数**</span><span class="sxs-lookup"><span data-stu-id="45701-113">**Occurrence**</span></span>|<span data-ttu-id="45701-114">省略可能。</span><span class="sxs-lookup"><span data-stu-id="45701-114">Optional.</span></span> <span data-ttu-id="45701-115">`TuningOptions` 要素につき 1 回だけ使用できます。</span><span class="sxs-lookup"><span data-stu-id="45701-115">Can use only once for each `TuningOptions` element.</span></span> <span data-ttu-id="45701-116">`TuningOptions` 要素内で以下の要素を指定する場合には使用できません。</span><span class="sxs-lookup"><span data-stu-id="45701-116">Cannot be used if the following elements are specified in the `TuningOptions` element:</span></span><br /><br /> [<span data-ttu-id="45701-117">FeatureSet 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="45701-117">FeatureSet Element &#40;DTA&#41;</span></span>](featureset-element-dta.md)<br /><br /> [<span data-ttu-id="45701-118">Partitioning 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="45701-118">Partitioning Element &#40;DTA&#41;</span></span>](partitioning-element-dta.md)<br /><br /> <span data-ttu-id="45701-119">[KeepExisting 要素 &#40;DTA&#41;](keepexisting-element-dta.md) が **ALL** に設定されている</span><span class="sxs-lookup"><span data-stu-id="45701-119">[KeepExisting Element &#40;DTA&#41;](keepexisting-element-dta.md) is set to **ALL**</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="45701-120">要素の関係</span><span class="sxs-lookup"><span data-stu-id="45701-120">Element Relationships</span></span>  
  
|<span data-ttu-id="45701-121">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="45701-121">Relationship</span></span>|<span data-ttu-id="45701-122">要素</span><span class="sxs-lookup"><span data-stu-id="45701-122">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="45701-123">**親要素**</span><span class="sxs-lookup"><span data-stu-id="45701-123">**Parent element**</span></span>|[<span data-ttu-id="45701-124">TuningOptions 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="45701-124">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="45701-125">**子要素**</span><span class="sxs-lookup"><span data-stu-id="45701-125">**Child elements**</span></span>|<span data-ttu-id="45701-126">[なし] :</span><span class="sxs-lookup"><span data-stu-id="45701-126">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="45701-127">例</span><span class="sxs-lookup"><span data-stu-id="45701-127">Example</span></span>  
 <span data-ttu-id="45701-128">次の例は、データベース エンジン チューニング アドバイザーの XML 入力ファイルの、`TuningOptions` が指定された `DropOnlyMode` セクションを示しています。</span><span class="sxs-lookup"><span data-stu-id="45701-128">The following example shows the `TuningOptions` section of a Database Engine Tuning Advisor XML input file where the `DropOnlyMode` is specified.</span></span> <span data-ttu-id="45701-129">この例では、チューニング時間は 24 時間 (1440 分) に制限されており、既存のクラスター化インデックスおよび非クラスター化インデックスはすべて削除することが検討されます。</span><span class="sxs-lookup"><span data-stu-id="45701-129">In this example the tuning time is limited to 24 hours (1440 minutes) and all existing clustered and nonclustered indexes will be considered for dropping:</span></span>  
  
```xml  
<TuningOptions  
  <TuningTimeInMin>1440</Name>  
  <KeepExisting>ALIGNED</KeepExisting>  
  <DropOnlyMode />  
</TuningOptions>  
```  
  
## <a name="see-also"></a><span data-ttu-id="45701-130">参照</span><span class="sxs-lookup"><span data-stu-id="45701-130">See Also</span></span>  
 [<span data-ttu-id="45701-131">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="45701-131">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
