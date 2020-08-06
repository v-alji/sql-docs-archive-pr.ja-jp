---
title: 多次元モデルのキューブ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OLAP objects [Analysis Services], cubes
- cubes [Analysis Services], about cubes
- cubes [Analysis Services]
- OLAP [Analysis Services], cubes
ms.assetid: e0f7acf3-4b07-41fc-a5fc-ac30b4a56c54
author: minewiskan
ms.author: owend
ms.openlocfilehash: 372bb8075b232ff8fbf8a54facf9bc065e6763a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741418"
---
# <a name="cubes-in-multidimensional-models"></a><span data-ttu-id="a263a-102">多次元モデルのキューブ</span><span class="sxs-lookup"><span data-stu-id="a263a-102">Cubes in Multidimensional Models</span></span>
  <span data-ttu-id="a263a-103">キューブは、分析目的の情報を含む多次元構造です。キューブの主な構成要素はディメンションとメジャーです。</span><span class="sxs-lookup"><span data-stu-id="a263a-103">A cube is a multidimensional structure that contains information for analytical purposes; the main constituents of a cube are dimensions and measures.</span></span> <span data-ttu-id="a263a-104">ディメンションでは、スライスおよびダイス化に使用するキューブの構造が定義され、メジャーによってエンド ユーザーが必要とする集計された数値が用意されます。</span><span class="sxs-lookup"><span data-stu-id="a263a-104">Dimensions define the structure of the cube that you use to slice and dice over, and measures provide aggregated numerical values of interest to the end user.</span></span> <span data-ttu-id="a263a-105">論理構造としてキューブを使用すると、クライアント アプリケーションでは、キューブ内のセルに含まれているかのようにメジャーの値を取得できます。セルは、考えられるすべての集約値に対して定義されます。</span><span class="sxs-lookup"><span data-stu-id="a263a-105">As a logical structure, a cube allows a client application to retrieve values, of measures, as if they were contained in cells in the cube; cells are defined for every possible summarized value.</span></span> <span data-ttu-id="a263a-106">キューブのセルは、ディメンションのメンバーの交差領域によって定義され、その交差領域のメジャーの集計値を含みます。</span><span class="sxs-lookup"><span data-stu-id="a263a-106">A cell, in the cube, is defined by the intersection of dimension members and contains the aggregated values of the measures at that specific intersection.</span></span>  
  
## <a name="benefits-of-using-cubes"></a><span data-ttu-id="a263a-107">キューブを使用する利点</span><span class="sxs-lookup"><span data-stu-id="a263a-107">Benefits of Using Cubes</span></span>  
 <span data-ttu-id="a263a-108">キューブでは、分析用のすべての関連データが格納されている単一の場所が提供されます。</span><span class="sxs-lookup"><span data-stu-id="a263a-108">A cube provides a single place where all related data, for analysis, is stored.</span></span>  
  
## <a name="components-of-cubes"></a><span data-ttu-id="a263a-109">キューブのコンポーネント</span><span class="sxs-lookup"><span data-stu-id="a263a-109">Components of Cubes</span></span>  
 <span data-ttu-id="a263a-110">キューブは次の要素から構成されます。</span><span class="sxs-lookup"><span data-stu-id="a263a-110">A cube is composed of:</span></span>  
  
|<span data-ttu-id="a263a-111">要素</span><span class="sxs-lookup"><span data-stu-id="a263a-111">Element</span></span>|<span data-ttu-id="a263a-112">説明</span><span class="sxs-lookup"><span data-stu-id="a263a-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a263a-113">Dimensions</span><span class="sxs-lookup"><span data-stu-id="a263a-113">Dimensions</span></span>|[<span data-ttu-id="a263a-114">多次元モデル内のディメンション</span><span class="sxs-lookup"><span data-stu-id="a263a-114">Dimensions in Multidimensional Models</span></span>](dimensions-in-multidimensional-models.md)|  
|<span data-ttu-id="a263a-115">メジャーおよびメジャー グループ</span><span class="sxs-lookup"><span data-stu-id="a263a-115">Measures and Measure Groups</span></span>|[<span data-ttu-id="a263a-116">多次元モデル内のメジャーおよびメジャー グループの作成</span><span class="sxs-lookup"><span data-stu-id="a263a-116">Create Measures and Measure Groups in Multidimensional Models</span></span>](create-measures-and-measure-groups-in-multidimensional-models.md)|  
|<span data-ttu-id="a263a-117">メジャー グループ</span><span class="sxs-lookup"><span data-stu-id="a263a-117">Partitions</span></span>|[<span data-ttu-id="a263a-118">多次元モデル内のパーティション</span><span class="sxs-lookup"><span data-stu-id="a263a-118">Partitions in Multidimensional Models</span></span>](partitions-in-multidimensional-models.md)|  
|<span data-ttu-id="a263a-119">パースペクティブ</span><span class="sxs-lookup"><span data-stu-id="a263a-119">Perspectives</span></span>|[<span data-ttu-id="a263a-120">多次元モデルのパースペクティブ</span><span class="sxs-lookup"><span data-stu-id="a263a-120">Perspectives in Multidimensional Models</span></span>](perspectives-in-multidimensional-models.md)|  
|<span data-ttu-id="a263a-121">階層</span><span class="sxs-lookup"><span data-stu-id="a263a-121">Hierarchies</span></span>|[<span data-ttu-id="a263a-122">ユーザー定義階層の作成</span><span class="sxs-lookup"><span data-stu-id="a263a-122">Create User-Defined Hierarchies</span></span>](user-defined-hierarchies-create.md)|  
|<span data-ttu-id="a263a-123">操作</span><span class="sxs-lookup"><span data-stu-id="a263a-123">Actions</span></span>|[<span data-ttu-id="a263a-124">多次元モデルのアクション</span><span class="sxs-lookup"><span data-stu-id="a263a-124">Actions in Multidimensional Models</span></span>](actions-in-multidimensional-models.md)|  
|<span data-ttu-id="a263a-125">主要業績評価指標 (KPI)</span><span class="sxs-lookup"><span data-stu-id="a263a-125">Key Performance Indicators (KPI)</span></span>|[<span data-ttu-id="a263a-126">多次元モデルの主要業績評価指標 &#40;KPI&#41;</span><span class="sxs-lookup"><span data-stu-id="a263a-126">Key Performance Indicators &#40;KPIs&#41; in Multidimensional Models</span></span>](key-performance-indicators-kpis-in-multidimensional-models.md)|  
|<span data-ttu-id="a263a-127">計算</span><span class="sxs-lookup"><span data-stu-id="a263a-127">Calculations</span></span>|[<span data-ttu-id="a263a-128">多次元モデルの計算</span><span class="sxs-lookup"><span data-stu-id="a263a-128">Calculations in Multidimensional Models</span></span>](calculations-in-multidimensional-models.md)|  
|<span data-ttu-id="a263a-129">翻訳</span><span class="sxs-lookup"><span data-stu-id="a263a-129">Translations</span></span>|[<span data-ttu-id="a263a-130">多次元モデルの翻訳</span><span class="sxs-lookup"><span data-stu-id="a263a-130">Translations in Multidimensional Models</span></span>](translations-in-multidimensional-models-analysis-services.md)|  
  
## <a name="related-tasks"></a><span data-ttu-id="a263a-131">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="a263a-131">Related Tasks</span></span>  
  
|<span data-ttu-id="a263a-132">トピック</span><span class="sxs-lookup"><span data-stu-id="a263a-132">Topic</span></span>|<span data-ttu-id="a263a-133">説明</span><span class="sxs-lookup"><span data-stu-id="a263a-133">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a263a-134">キューブ ウィザードを使用したキューブの作成</span><span class="sxs-lookup"><span data-stu-id="a263a-134">Create a Cube Using the Cube Wizard</span></span>](create-a-cube-using-the-cube-wizard.md)|<span data-ttu-id="a263a-135">キューブ ウィザードを使用して、キューブ、ディメンション、ディメンション属性、ユーザー定義階層を定義する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a263a-135">Describes how to use the Cube Wizard to define a cube, dimensions, dimension attributes, and user-defined hierarchies.</span></span>|  
|[<span data-ttu-id="a263a-136">多次元モデル内のメジャーおよびメジャー グループの作成</span><span class="sxs-lookup"><span data-stu-id="a263a-136">Create Measures and Measure Groups in Multidimensional Models</span></span>](create-measures-and-measure-groups-in-multidimensional-models.md)|<span data-ttu-id="a263a-137">メジャー グループを定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a263a-137">Describes how to define measure groups.</span></span>|  
|[<span data-ttu-id="a263a-138">多次元モデルの計算</span><span class="sxs-lookup"><span data-stu-id="a263a-138">Calculations in Multidimensional Models</span></span>](calculations-in-multidimensional-models.md)|<span data-ttu-id="a263a-139">MDX スクリプトで計算を定義して構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a263a-139">Describes how to define and configure a calculation in an MDX script.</span></span>|  
|[<span data-ttu-id="a263a-140">多次元モデルのアクション</span><span class="sxs-lookup"><span data-stu-id="a263a-140">Actions in Multidimensional Models</span></span>](actions-in-multidimensional-models.md)|<span data-ttu-id="a263a-141">アクションを定義して構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a263a-141">Describes how to define and configure an action.</span></span>|  
|[<span data-ttu-id="a263a-142">多次元モデルのパースペクティブ</span><span class="sxs-lookup"><span data-stu-id="a263a-142">Perspectives in Multidimensional Models</span></span>](perspectives-in-multidimensional-models.md)|<span data-ttu-id="a263a-143">パースペクティブを定義して構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a263a-143">Describes how to define and configure a perspective.</span></span>|  
|[<span data-ttu-id="a263a-144">ストアドプロシージャの定義</span><span class="sxs-lookup"><span data-stu-id="a263a-144">Defining Stored Procedures</span></span>](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)|<span data-ttu-id="a263a-145">ストアド プロシージャを操作する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a263a-145">Describes how to work with stored procedures.</span></span>|  
  
  
