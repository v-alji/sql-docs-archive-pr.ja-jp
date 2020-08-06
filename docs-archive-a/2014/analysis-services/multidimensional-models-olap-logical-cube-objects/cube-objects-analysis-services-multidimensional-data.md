---
title: Cube オブジェクト (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- cubes [Analysis Services], objects
ms.assetid: 5cee362e-3f95-4467-bc6c-29b1518ecbf3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0e6dfb75be696ab26893e668b99dc36c7340f86c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641904"
---
# <a name="cube-objects-analysis-services---multidimensional-data"></a><span data-ttu-id="316dc-102">Cube オブジェクト (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="316dc-102">Cube Objects (Analysis Services - Multidimensional Data)</span></span>
    
## <a name="introducing-cube-objects"></a><span data-ttu-id="316dc-103">Cube オブジェクトの導入</span><span class="sxs-lookup"><span data-stu-id="316dc-103">Introducing Cube Objects</span></span>  
 <span data-ttu-id="316dc-104">簡単な <xref:Microsoft.AnalysisServices.Cube> オブジェクトは、基本情報、ディメンション、およびメジャー グループで構成されます。</span><span class="sxs-lookup"><span data-stu-id="316dc-104">A simple <xref:Microsoft.AnalysisServices.Cube> object is composed of: basic information, dimensions, and measure groups.</span></span> <span data-ttu-id="316dc-105">基本情報には、キューブの名前、キューブの既定のメジャー、データ ソース、ストレージ モードなどが含まれます。</span><span class="sxs-lookup"><span data-stu-id="316dc-105">Basic information includes the name of the cube, the default measure of the cube, the data source, the storage mode, and others.</span></span>  
  
 <span data-ttu-id="316dc-106">Dimensions コレクションには、データベースのディメンション コレクションのキューブで使用される、実際のディメンションのセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="316dc-106">The Dimensions collection contains the actual set of dimensions used in the cube from the database dimensions colection.</span></span> <span data-ttu-id="316dc-107">すべてのディメンションは、キューブ内で参照される前に、データベースのディメンション コレクション内で定義されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="316dc-107">All dimensions have to be defined in the dimensions collection of the database before being referenced in the cube.</span></span> <span data-ttu-id="316dc-108">プライベートディメンションは、では使用できません [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="316dc-108">Private dimensions are not available in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="316dc-109">メジャー グループは、キューブ内のメジャーのセットです。</span><span class="sxs-lookup"><span data-stu-id="316dc-109">Measure groups are sets of measures in the cube.</span></span> <span data-ttu-id="316dc-110">メジャー グループは、共通のデータ ソース ビューと共通のディメンション セットを持つ、メジャーのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="316dc-110">A measure group is a collection of measures that have a common data source view and a common set of dimensions.</span></span> <span data-ttu-id="316dc-111">メジャー グループは、メジャーの処理単位です。メジャー グループは個別に処理されてから参照できます。</span><span class="sxs-lookup"><span data-stu-id="316dc-111">A measure group is the unit of process for measures; measure groups can be processed individually and then browsed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="316dc-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="316dc-112">In this section</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="316dc-113">トピック</span><span class="sxs-lookup"><span data-stu-id="316dc-113">Topic</span></span>||  
|[<span data-ttu-id="316dc-114">アクション &#40;Analysis Services - 多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="316dc-114">Actions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../multidimensional-models/actions-analysis-services-multidimensional-data.md)||  
|[<span data-ttu-id="316dc-115">集計と集計デザイン</span><span class="sxs-lookup"><span data-stu-id="316dc-115">Aggregations and Aggregation Designs</span></span>](aggregations-and-aggregation-designs.md)||  
|[<span data-ttu-id="316dc-116">計算</span><span class="sxs-lookup"><span data-stu-id="316dc-116">Calculations</span></span>](calculations.md)||  
|[<span data-ttu-id="316dc-117">キューブセル &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="316dc-117">Cube Cells &#40;Analysis Services - Multidimensional Data&#41;</span></span>](cube-cells-analysis-services-multidimensional-data.md)||  
|[<span data-ttu-id="316dc-118">キューブ プロパティ</span><span class="sxs-lookup"><span data-stu-id="316dc-118">Cube Properties</span></span>](cube-properties-multidimensional-model-programming.md)||  
|[<span data-ttu-id="316dc-119">Cube Storage &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="316dc-119">Cube Storage &#40;Analysis Services - Multidimensional Data&#41;</span></span>](cube-storage-analysis-services-multidimensional-data.md)||  
|[<span data-ttu-id="316dc-120">キューブの翻訳</span><span class="sxs-lookup"><span data-stu-id="316dc-120">Cube Translations</span></span>](cube-translations.md)||  
|[<span data-ttu-id="316dc-121">ディメンション リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="316dc-121">Dimension Relationships</span></span>](dimension-relationships.md)||  
|[<span data-ttu-id="316dc-122">多次元モデルの主要業績評価指標 &#40;KPI&#41;</span><span class="sxs-lookup"><span data-stu-id="316dc-122">Key Performance Indicators &#40;KPIs&#41; in Multidimensional Models</span></span>](../multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)||  
|[<span data-ttu-id="316dc-123">メジャーおよびメジャー グループ</span><span class="sxs-lookup"><span data-stu-id="316dc-123">Measures and Measure Groups</span></span>](../multidimensional-models/measures-and-measure-groups.md)||  
|[<span data-ttu-id="316dc-124">パーティション (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="316dc-124">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](partitions-analysis-services-multidimensional-data.md)||  
|[<span data-ttu-id="316dc-125">パースペクティブ</span><span class="sxs-lookup"><span data-stu-id="316dc-125">Perspectives</span></span>](perspectives.md)||  
  
  
