---
title: 'レッスン 3: メジャー、属性、および階層の変更 |Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 17d243cb-9bfb-43d7-8e6f-4d601fd62150
author: minewiskan
ms.author: owend
ms.openlocfilehash: c410136540a0ba85d50fbabc8b2d3c52be1823f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642390"
---
# <a name="lesson-3-modifying-measures-attributes-and-hierarchies"></a><span data-ttu-id="fbcce-102">レッスン 3:メジャー、属性、および階層の修正</span><span class="sxs-lookup"><span data-stu-id="fbcce-102">Lesson 3: Modifying Measures, Attributes and Hierarchies</span></span>
  <span data-ttu-id="fbcce-103">前のレッスンでは、最初のキューブを定義しました。次は、このキューブをさらに使いやすくしましょう。</span><span class="sxs-lookup"><span data-stu-id="fbcce-103">After defining your initial cube, you are ready to improve the usefulness and friendliness of the cube.</span></span> <span data-ttu-id="fbcce-104">そのためには、特定のメジャーに書式を適用し、計算やリレーションシップを定義して、さまざまなレベルでのナビゲーションと集計をサポートする階層を追加します。</span><span class="sxs-lookup"><span data-stu-id="fbcce-104">You can do this by adding hierarchies that support navigation and aggregation at various levels, by applying formats to specific measure, and by defining calculations and relationships.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fbcce-105">このチュートリアルの各レッスンの操作内容が反映されたプロジェクトを、オンラインで入手できます。</span><span class="sxs-lookup"><span data-stu-id="fbcce-105">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="fbcce-106">途中のレッスンから開始する場合は、前のレッスンの操作内容が反映されたプロジェクトを作業の開始点として使用できます。</span><span class="sxs-lookup"><span data-stu-id="fbcce-106">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="fbcce-107">このチュートリアルのサンプル プロジェクトをダウンロードするには、[ここ](https://go.microsoft.com/fwlink/?LinkID=221866) をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="fbcce-107">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 <span data-ttu-id="fbcce-108">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fbcce-108">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="fbcce-109">メジャーの変更</span><span class="sxs-lookup"><span data-stu-id="fbcce-109">Modifying Measures</span></span>](lesson-3-1-modifying-measures.md)  
 <span data-ttu-id="fbcce-110">この実習では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブの通貨メジャーと比率メジャーの書式プロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="fbcce-110">In this task, you specify formatting properties for the currency and percentage measures in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>  
  
 [<span data-ttu-id="fbcce-111">Customer ディメンションの変更</span><span class="sxs-lookup"><span data-stu-id="fbcce-111">Modifying the Customer Dimension</span></span>](lesson-3-2-modifying-the-customer-dimension.md)  
 <span data-ttu-id="fbcce-112">この実習では、ユーザー階層の定義および名前付き計算の作成を行います。さらに、名前付き計算を使用する属性を修正し、属性とユーザー階層を表示フォルダーにグループ化します。</span><span class="sxs-lookup"><span data-stu-id="fbcce-112">In this task, you define a user hierarchy, create named calculations, modify attributes to use named calculations, and group attributes and user hierarchies into display folders.</span></span>  
  
 [<span data-ttu-id="fbcce-113">Product ディメンションの変更</span><span class="sxs-lookup"><span data-stu-id="fbcce-113">Modifying the Product Dimension</span></span>](lesson-3-3-modifying-the-product-dimension.md)  
 <span data-ttu-id="fbcce-114">この実習では、ユーザー階層の定義、名前付き計算の作成、All メンバー名の定義、および表示フォルダーの定義を行います。</span><span class="sxs-lookup"><span data-stu-id="fbcce-114">In this task, you define a user hierarchy, create named calculations, define the All member name, and define display folders.</span></span>  
  
 [<span data-ttu-id="fbcce-115">Date ディメンションの変更</span><span class="sxs-lookup"><span data-stu-id="fbcce-115">Modifying the Date Dimension</span></span>](lesson-3-4-modifying-the-date-dimension.md)  
 <span data-ttu-id="fbcce-116">この実習では、ユーザー階層を定義し、属性のメンバー名を変更します。また、複合キーを使用して一意な属性メンバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="fbcce-116">In this task, you define a user hierarchy, modify attribute member names, and use composite keys to specify unique attribute members.</span></span>  
  
 [<span data-ttu-id="fbcce-117">配置したキューブの表示</span><span class="sxs-lookup"><span data-stu-id="fbcce-117">Browsing the Deployed Cube</span></span>](lesson-3-5-browsing-the-deployed-cube.md)  
 <span data-ttu-id="fbcce-118">この実習では、キューブ デザイナーのブラウザーを使用してキューブ データを表示します。</span><span class="sxs-lookup"><span data-stu-id="fbcce-118">In this task, you browse cube data by using the browser in Cube Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbcce-119">参照</span><span class="sxs-lookup"><span data-stu-id="fbcce-119">See Also</span></span>  
 <span data-ttu-id="fbcce-120">[Analysis Services チュートリアルのシナリオ](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="fbcce-120">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 [<span data-ttu-id="fbcce-121">多次元モデリング (Adventure Works チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="fbcce-121">Multidimensional Modeling &#40;Adventure Works Tutorial&#41;</span></span>](multidimensional-modeling-adventure-works-tutorial.md)  
  
  
