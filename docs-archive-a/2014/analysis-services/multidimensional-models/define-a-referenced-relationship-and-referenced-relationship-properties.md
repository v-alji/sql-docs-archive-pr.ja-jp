---
title: 参照リレーションシップと参照リレーションシップのプロパティの定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- referenced dimension relationship
- relationships [Analysis Services], referenced dimensions
ms.assetid: 5bb44b41-635b-4398-8fe9-0bfbb142553e
author: minewiskan
ms.author: owend
ms.openlocfilehash: a84cf2ed95ab3660c5a6b3c039dc58351dc43264
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715809"
---
# <a name="define-a-referenced-relationship-and-referenced-relationship-properties"></a><span data-ttu-id="a5adf-102">参照リレーションシップと参照リレーションシップのプロパティの定義</span><span class="sxs-lookup"><span data-stu-id="a5adf-102">Define a Referenced Relationship and Referenced Relationship Properties</span></span>
  <span data-ttu-id="a5adf-103">参照ディメンションのリレーションシップは、キューブ デザイナーの **[ディメンションの使用法]** タブで定義します。</span><span class="sxs-lookup"><span data-stu-id="a5adf-103">A reference dimension relationship is defined on the **Dimension Usage** tab of Cube Designer.</span></span> <span data-ttu-id="a5adf-104">参照ディメンションのリレーションシップを定義するには、以下を指定します。</span><span class="sxs-lookup"><span data-stu-id="a5adf-104">The reference dimension relationship is defined by specifying the following:</span></span>  
  
-   <span data-ttu-id="a5adf-105">結合先の中間ディメンション。</span><span class="sxs-lookup"><span data-stu-id="a5adf-105">The intermediate dimension to which to join.</span></span> <span data-ttu-id="a5adf-106">標準ディメンションまたは別の参照ディメンションを指定します。</span><span class="sxs-lookup"><span data-stu-id="a5adf-106">This can be a regular dimension or another reference dimension.</span></span>  
  
-   <span data-ttu-id="a5adf-107">ディメンションがメジャー グループについての集計に使用できる最も低いレベルを定義する参照ディメンション属性。</span><span class="sxs-lookup"><span data-stu-id="a5adf-107">A reference dimension attribute that defines the lowest level that the dimension is available for aggregation with regard to the measure group.</span></span>  
  
-   <span data-ttu-id="a5adf-108">参照ディメンション属性に対応する中間ディメンションの (外部キー) 属性。</span><span class="sxs-lookup"><span data-stu-id="a5adf-108">The (foreign key) attribute in the intermediate dimension that corresponds to the reference dimension attribute.</span></span>  
  
 <span data-ttu-id="a5adf-109">通常、参照ディメンションをファクト テーブルにリンクする列は参照ディメンションのキー属性ですが、この列を中間ディメンションの属性として定義する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="a5adf-109">Notice that the column that links the reference dimension to the fact table, which is generally the key attribute in the reference dimension, must also be defined as an attribute in the intermediate dimension.</span></span> <span data-ttu-id="a5adf-110">参照ディメンションのチェーンを作成する場合は、まず、チェーンの最初のディメンションとメジャー グループ間に標準のリレーションシップを作成します。</span><span class="sxs-lookup"><span data-stu-id="a5adf-110">When you create a chain of reference dimensions, start by creating the regular relationship between the first dimension in the chain and the measure group.</span></span> <span data-ttu-id="a5adf-111">次に、追加の各参照リレーションシップを順に作成します。</span><span class="sxs-lookup"><span data-stu-id="a5adf-111">Then create each additional referenced relationship in order.</span></span> <span data-ttu-id="a5adf-112">参照リレーションシップは、メジャー グループとのリレーションシップが既にあるディメンションに対してのみ作成できます。</span><span class="sxs-lookup"><span data-stu-id="a5adf-112">A referenced relationship can only be made to a dimension that has an existing relationship to the measure group.</span></span>  
  
 <span data-ttu-id="a5adf-113">参照ディメンションのリレーションシップを作成すると、ディメンション属性のリンクが既定で具体化されます。</span><span class="sxs-lookup"><span data-stu-id="a5adf-113">When you create a reference dimension relationship, the dimension attribute link is materialized by default.</span></span> <span data-ttu-id="a5adf-114">ディメンション属性のリンクを具体化すると、各行のファクト テーブルおよび参照ディメンション間のリンクの値が具体化され、処理中にディメンションの MOLAP 構造に格納されます。</span><span class="sxs-lookup"><span data-stu-id="a5adf-114">Materializing a dimension attribute link causes the value of the link between the fact table and the reference dimension for each row to be materialized, or stored, in the MOLAP structure for the dimension during processing.</span></span> <span data-ttu-id="a5adf-115">この操作を行うと、処理パフォーマンスやストレージの要件にわずかに影響しますが、クエリ パフォーマンスの向上を図ることができます。</span><span class="sxs-lookup"><span data-stu-id="a5adf-115">This will have a minor effect on processing performance and storage requirements, but will improve query performance.</span></span>  
  
 <span data-ttu-id="a5adf-116">参照ディメンションでは、参照ディメンションと参照ディメンションのメイン テーブルに対応するメジャー グループ間のリレーションシップを定義する属性を特定することにより、粒度が指定されます。</span><span class="sxs-lookup"><span data-stu-id="a5adf-116">In a reference dimension, granularity is specified by identifying the attribute that defines the relationship between a reference dimension and the measure group corresponding to the main table of the dimension.</span></span> <span data-ttu-id="a5adf-117">複数の参照ディメンションを連結すると、最も外側のディメンションからメジャー グループまでのリレーションシップが参照によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="a5adf-117">When multiple reference dimensions are chained together, the references define the relationship from the outermost dimension to the measure group.</span></span>  
  
  
