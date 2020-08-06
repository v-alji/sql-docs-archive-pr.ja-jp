---
title: 'レッスン 7: 主要業績評価指標 (Kpi) の定義 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 36d53770-294f-43ab-8850-15d5351ff60c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 87df6fd91a66505f124144cafd9a44c6e5e70e85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714706"
---
# <a name="lesson-7-defining-key-performance-indicators-kpis"></a><span data-ttu-id="f193f-102">レッスン 7: 主要業績評価指標 (KPI) の定義</span><span class="sxs-lookup"><span data-stu-id="f193f-102">Lesson 7: Defining Key Performance Indicators (KPIs)</span></span>
  <span data-ttu-id="f193f-103">このレッスンでは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトで主要業績評価指標 (KPI) を定義する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="f193f-103">In this lesson, you learn to define Key Performance Indicators (KPIs) in your [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="f193f-104">KPI は、ビジネスを測定するサーバー側の計算を定義するためのフレームワークを提供します。また、KPI を使用すれば、結果の情報を表示する方法を標準化できます。</span><span class="sxs-lookup"><span data-stu-id="f193f-104">KPIs provide a framework for defining server-side calculations that measure your business, and they standardize how the resulting information is displayed.</span></span> <span data-ttu-id="f193f-105">KPI は、データ アクセス API や [!INCLUDE[msCoName](../includes/msconame-md.md)] ツール、またはサード パーティのツールを使用して、レポート、ポータル、およびダッシュボードに表示できます。</span><span class="sxs-lookup"><span data-stu-id="f193f-105">KPIs can be displayed in reports, portals, and dashboards, through data access APIs, and through [!INCLUDE[msCoName](../includes/msconame-md.md)] tools and third-party tools.</span></span> <span data-ttu-id="f193f-106">KPI は、通常のメジャーおよび他の多次元式 (MDX) に関するメタデータ ラッパーです。</span><span class="sxs-lookup"><span data-stu-id="f193f-106">KPIs are metadata wrappers around regular measures and other Multidimensional Expressions (MDX) expressions.</span></span> <span data-ttu-id="f193f-107">詳細については、「 [多次元モデルの主要業績評価指標 &#40;KPI&#41;](multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f193f-107">For more information, see [Key Performance Indicators &#40;KPIs&#41; in Multidimensional Models](multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f193f-108">このチュートリアルの各レッスンの操作内容が反映されたプロジェクトを、オンラインで入手できます。</span><span class="sxs-lookup"><span data-stu-id="f193f-108">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="f193f-109">途中のレッスンから開始する場合は、前のレッスンの操作内容が反映されたプロジェクトを作業の開始点として使用できます。</span><span class="sxs-lookup"><span data-stu-id="f193f-109">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="f193f-110">このチュートリアルのサンプル プロジェクトをダウンロードするには、[ここ](https://go.microsoft.com/fwlink/?LinkID=221866) をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="f193f-110">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 <span data-ttu-id="f193f-111">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f193f-111">This lesson contains the following task:</span></span>  
  
 [<span data-ttu-id="f193f-112">KPI の定義と表示</span><span class="sxs-lookup"><span data-stu-id="f193f-112">Defining and Browsing KPIs</span></span>](lesson-7-1-defining-and-browsing-kpis.md)  
 <span data-ttu-id="f193f-113">この作業では、フォーム ビューで KPI を定義してから、ブラウザー ビューに切り替え、その KPI を使用してキューブ データを表示します。</span><span class="sxs-lookup"><span data-stu-id="f193f-113">In this task, you define KPIs in the Form view and then switch to the Browser view to browse the cube data by using the KPIs.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="f193f-114">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="f193f-114">Next Lesson</span></span>  
 [<span data-ttu-id="f193f-115">レッスン 8: アクションの定義</span><span class="sxs-lookup"><span data-stu-id="f193f-115">Lesson 8: Defining Actions</span></span>](lesson-8-defining-actions.md)  
  
## <a name="see-also"></a><span data-ttu-id="f193f-116">参照</span><span class="sxs-lookup"><span data-stu-id="f193f-116">See Also</span></span>  
 <span data-ttu-id="f193f-117">[Analysis Services チュートリアルのシナリオ](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="f193f-117">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="f193f-118">[Adventure Works チュートリアル &#40;の多次元モデリング&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="f193f-118">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 [<span data-ttu-id="f193f-119">多次元モデルの主要業績評価指標 &#40;KPI&#41;</span><span class="sxs-lookup"><span data-stu-id="f193f-119">Key Performance Indicators &#40;KPIs&#41; in Multidimensional Models</span></span>](multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)  
  
  
