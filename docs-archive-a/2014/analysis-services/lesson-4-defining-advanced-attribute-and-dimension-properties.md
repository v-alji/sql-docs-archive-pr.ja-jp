---
title: 'レッスン 4: 高度な属性とディメンションのプロパティの定義 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0e86b9be-e47d-4bb4-87eb-136ff3a61aef
author: minewiskan
ms.author: owend
ms.openlocfilehash: deb2d9c40ad5024f6cc4ba6e9148df41a168c6e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718867"
---
# <a name="lesson-4-defining-advanced-attribute-and-dimension-properties"></a><span data-ttu-id="89f59-102">レッスン 4:高度な属性およびディメンションのプロパティの定義</span><span class="sxs-lookup"><span data-stu-id="89f59-102">Lesson 4: Defining Advanced Attribute and Dimension Properties</span></span>
  <span data-ttu-id="89f59-103">このレッスンでは、属性、属性階層、およびディメンションの高度なプロパティをいくつか取り上げ、その使用方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="89f59-103">In this lesson, you will learn how to use some of the advanced properties of attributes, attribute hierarchies, and dimension properties.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="89f59-104">このレッスンでは、このチュートリアルの最初の 3 つのレッスンで作成した [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトの改良版を使用します。</span><span class="sxs-lookup"><span data-stu-id="89f59-104">This lesson is based on an enhanced version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project that you completed in the first three lessons of this tutorial.</span></span> <span data-ttu-id="89f59-105">このレッスンの最初の実習では、このレッスンで使用する適切なサンプル プロジェクトの場所を示し、このプロジェクトが最初の 3 つのレッスンで作成したプロジェクトと異なる点を説明します。</span><span class="sxs-lookup"><span data-stu-id="89f59-105">The first task in this lesson describes where to locate the appropriate sample project to use for the lesson, and the difference between this project and the project that you created in the first three lessons.</span></span>  
  
 <span data-ttu-id="89f59-106">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="89f59-106">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="89f59-107">Analysis Services チュートリアル プロジェクトの修正バージョンの使用</span><span class="sxs-lookup"><span data-stu-id="89f59-107">Using a Modified Version of the Analysis Services Tutorial Project</span></span>](lesson-4-1-using-a-modified-version-of-the-analysis-services-tutorial-project.md)  
 <span data-ttu-id="89f59-108">ここでは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトの修正バージョンを開き、内容を確認して、配置します。このプロジェクトには、複数のメジャー グループと追加ディメンションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="89f59-108">In this task, you open, review, and deploy a modified version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project, which has multiple measure groups and additional dimensions.</span></span>  
  
 [<span data-ttu-id="89f59-109">親子階層の親属性プロパティの定義</span><span class="sxs-lookup"><span data-stu-id="89f59-109">Defining Parent Attribute Properties in a Parent-Child Hierarchy</span></span>](lesson-4-2-defining-parent-attribute-properties-in-a-parent-child-hierarchy.md)  
 <span data-ttu-id="89f59-110">ここでは、親子ディメンションのレベル名を定義し、親メンバーに関連付けられているデータの表示、または非表示を指定します。</span><span class="sxs-lookup"><span data-stu-id="89f59-110">In this task, you define level names in a parent-child dimension and specify whether data related to parent members is displayed.</span></span> <span data-ttu-id="89f59-111">詳細については、「親子階層の親子[階層](multidimensional-models/parent-child-dimension.md)と[属性](multidimensional-models/parent-child-dimension-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89f59-111">For more information, see [Parent-Child Hierarchy](multidimensional-models/parent-child-dimension.md) and [Attributes in Parent-Child Hierarchies](multidimensional-models/parent-child-dimension-attributes.md).</span></span>  
  
 [<span data-ttu-id="89f59-112">属性メンバーの自動的なグループ化</span><span class="sxs-lookup"><span data-stu-id="89f59-112">Automatically Grouping Attribute Members</span></span>](lesson-4-3-automatically-grouping-attribute-members.md)  
 <span data-ttu-id="89f59-113">ここでは、属性階層内のメンバーの配置に基づいて、属性メンバーのグループを自動的に作成します。</span><span class="sxs-lookup"><span data-stu-id="89f59-113">In this task, you automatically create groupings of attribute members based on the distribution of the members within the attribute hierarchy.</span></span> <span data-ttu-id="89f59-114">詳細については、[「属性メンバーのグループ化 (分離)](multidimensional-models/attribute-properties-group-attribute-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89f59-114">For more information, see [Group Attribute Members &#40;Discretization&#41;](multidimensional-models/attribute-properties-group-attribute-members.md).</span></span>  
  
 [<span data-ttu-id="89f59-115">属性階層の非表示化と無効化</span><span class="sxs-lookup"><span data-stu-id="89f59-115">Hiding and Disabling Attribute Hierarchies</span></span>](lesson-4-4-hiding-and-disabling-attribute-hierarchies.md)  
 <span data-ttu-id="89f59-116">ここでは、属性階層を無効にし、非表示にする方法と、そのタイミングについて学習します。</span><span class="sxs-lookup"><span data-stu-id="89f59-116">In this task, you learn how and when to disable or hide attribute hierarchies.</span></span>  
  
 [<span data-ttu-id="89f59-117">2 次属性に基づく属性メンバーの並べ替え</span><span class="sxs-lookup"><span data-stu-id="89f59-117">Sorting Attribute Members Based on a Secondary Attribute</span></span>](lesson-4-5-sorting-attribute-members-based-on-a-secondary-attribute.md)  
 <span data-ttu-id="89f59-118">ここでは、2 次属性に基づいて、ディメンションを目的の順序で並べ替える方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="89f59-118">In this task, you learn how to sort dimension members based on a secondary attribute, to achieve the sort order that you want.</span></span>  
  
 [<span data-ttu-id="89f59-119">ユーザー定義階層の属性間での属性リレーションシップの指定</span><span class="sxs-lookup"><span data-stu-id="89f59-119">Specifying Attribute Relationships Between Attributes in a User-Defined Hierarchy</span></span>](4-6-specifying-attribute-relationships-in-user-defined-hierarchy.md)  
 <span data-ttu-id="89f59-120">ここでは、属性のメンバーのプロパティを定義する方法と、プロパティ間の集計リレーションシップを指定する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="89f59-120">In this task, you learn how to define member properties for attributes and to specify aggregation relationships between them.</span></span> <span data-ttu-id="89f59-121">詳細については、「[属性リレーションシップの定義](multidimensional-models/attribute-relationships-define.md)」および「[ユーザー階層のプロパティ](multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89f59-121">For more information, see [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md) and [User Hierarchy Properties](multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md).</span></span>  
  
 [<span data-ttu-id="89f59-122">不明なメンバーと NULL 処理のプロパティの定義</span><span class="sxs-lookup"><span data-stu-id="89f59-122">Defining the Unknown Member and Null Processing Properties</span></span>](lesson-4-7-defining-the-unknown-member-and-null-processing-properties.md)  
 <span data-ttu-id="89f59-123">この実習では、UnknownMember プロパティと UnknownMemberName プロパティを構成し、null ディメンション メンバーによって発生するエラー状況を処理します。</span><span class="sxs-lookup"><span data-stu-id="89f59-123">In this task, you configure the UnknownMember and UnknownMemberName properties to handle error conditions caused by null dimension members.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="89f59-124">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="89f59-124">Next Lesson</span></span>  
 [<span data-ttu-id="89f59-125">レッスン 5: ディメンションおよびメジャー グループ間のリレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="89f59-125">Lesson 5: Defining Relationships Between Dimensions and Measure Groups</span></span>](lesson-5-defining-relationships-between-dimensions-and-measure-groups.md)  
  
## <a name="see-also"></a><span data-ttu-id="89f59-126">参照</span><span class="sxs-lookup"><span data-stu-id="89f59-126">See Also</span></span>  
 <span data-ttu-id="89f59-127">[Analysis Services チュートリアルのシナリオ](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="89f59-127">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="89f59-128">[Adventure Works チュートリアル &#40;の多次元モデリング&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="89f59-128">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 [<span data-ttu-id="89f59-129">多次元モデル内のディメンション</span><span class="sxs-lookup"><span data-stu-id="89f59-129">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
