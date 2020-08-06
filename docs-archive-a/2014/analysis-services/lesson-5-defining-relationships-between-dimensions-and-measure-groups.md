---
title: 'レッスン 5: ディメンションとメジャーグループ間のリレーションシップの定義 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 31aeb271-47a1-433b-a8a5-120bcb4584d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6dbdf20e64e3cd8adc751b69122a380d7b3b3648
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639755"
---
# <a name="lesson-5-defining-relationships-between-dimensions-and-measure-groups"></a><span data-ttu-id="9c1b1-102">レッスン 5: ディメンションおよびメジャー グループ間のリレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="9c1b1-102">Lesson 5: Defining Relationships Between Dimensions and Measure Groups</span></span>
  <span data-ttu-id="9c1b1-103">このチュートリアルの前のレッスンでは、キューブに追加したデータベース ディメンションを、1 つ以上のキューブ ディメンションの基準として使用できることを学習しました。</span><span class="sxs-lookup"><span data-stu-id="9c1b1-103">In the previous lessons in this tutorial, you learned that database dimensions added to a cube can be used as the basis for one or more cube dimensions.</span></span> <span data-ttu-id="9c1b1-104">このレッスンでは、キューブ ディメンションとメジャー グループの間に各種のリレーションシップを定義し、これらのリレーションシップのプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="9c1b1-104">In this lesson, you learn to define different types of relationships between cube dimensions and measure groups, and to specify the properties of these relationships.</span></span>  
  
 <span data-ttu-id="9c1b1-105">詳細については、「 [ディメンション リレーションシップ](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c1b1-105">For more information, see [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9c1b1-106">このチュートリアルの各レッスンの操作内容が反映されたプロジェクトを、オンラインで入手できます。</span><span class="sxs-lookup"><span data-stu-id="9c1b1-106">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="9c1b1-107">途中のレッスンから開始する場合は、前のレッスンの操作内容が反映されたプロジェクトを作業の開始点として使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c1b1-107">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="9c1b1-108">このチュートリアルのサンプル プロジェクトをダウンロードするには、[ここ](https://go.microsoft.com/fwlink/?LinkID=221866) をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="9c1b1-108">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 <span data-ttu-id="9c1b1-109">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9c1b1-109">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="9c1b1-110">参照リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="9c1b1-110">Defining a Referenced Relationship</span></span>](lesson-5-1-defining-a-referenced-relationship.md)  
 <span data-ttu-id="9c1b1-111">ここでは、主キーと外部キーのリレーションシップを介して直接リンクされているディメンションを使用して、ディメンションをファクトテーブルに間接的にリンクする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9c1b1-111">In this task, you learn to link a dimension to a fact table indirectly through a dimension that is linked directly through a primary key-foreign key relationship.</span></span>  
  
 [<span data-ttu-id="9c1b1-112">ファクト リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="9c1b1-112">Defining a Fact Relationship</span></span>](lesson-5-2-defining-a-fact-relationship.md)  
 <span data-ttu-id="9c1b1-113">ここでは、ファクト テーブルのデータに基づいてディメンションを定義する方法を学習します。また、ディメンション リレーションシップをファクト リレーションシップとして定義する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="9c1b1-113">In this task, you learn to define a dimension based on data in the fact table, and to define the dimension relationship as a fact relationship.</span></span>  
  
 [<span data-ttu-id="9c1b1-114">多対多関係の定義</span><span class="sxs-lookup"><span data-stu-id="9c1b1-114">Defining a Many-to-Many Relationship</span></span>](lesson-5-3-defining-a-many-to-many-relationship.md)  
 <span data-ttu-id="9c1b1-115">ここでは、ディメンション テーブルとファクト テーブルの間に存在する多対多リレーションシップの定義を使用し、ファクトを複数のディメンション メンバーに関連付ける方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="9c1b1-115">In this task, you learn to relate a fact to multiple dimension members through the definition of a many-to-many relationship between dimension tables and fact tables.</span></span>  
  
 [<span data-ttu-id="9c1b1-116">メジャー グループでのディメンション粒度の定義</span><span class="sxs-lookup"><span data-stu-id="9c1b1-116">Defining Dimension Granularity within a Measure Group</span></span>](lesson-5-4-defining-dimension-granularity-within-a-measure-group.md)  
 <span data-ttu-id="9c1b1-117">ここでは、特定のメジャー グループに対し、ディメンションの粒度を定義する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="9c1b1-117">In this task, you learn to modify the granularity of a dimension for a specific measure group.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="9c1b1-118">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="9c1b1-118">Next Lesson</span></span>  
 [<span data-ttu-id="9c1b1-119">レッスン 6: 計算の定義</span><span class="sxs-lookup"><span data-stu-id="9c1b1-119">Lesson 6: Defining Calculations</span></span>](lesson-6-defining-calculations.md)  
  
## <a name="see-also"></a><span data-ttu-id="9c1b1-120">参照</span><span class="sxs-lookup"><span data-stu-id="9c1b1-120">See Also</span></span>  
 <span data-ttu-id="9c1b1-121">[Analysis Services チュートリアルのシナリオ](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="9c1b1-121">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="9c1b1-122">[Adventure Works チュートリアル &#40;の多次元モデリング&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="9c1b1-122">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 [<span data-ttu-id="9c1b1-123">ディメンション リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="9c1b1-123">Dimension Relationships</span></span>](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)  
  
  
