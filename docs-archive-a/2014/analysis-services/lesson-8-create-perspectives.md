---
title: 'レッスン 9: パースペクティブの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 55b0f0d0-1cdf-4876-9c3d-d0c848be3f5d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 417b6a4d3b16857f48bcc2f39dc8ec4c010a2b10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739007"
---
# <a name="lesson-9-create-perspectives"></a><span data-ttu-id="092ec-102">レッスン 9: パースペクティブを作成する</span><span class="sxs-lookup"><span data-stu-id="092ec-102">Lesson 9: Create Perspectives</span></span>
  <span data-ttu-id="092ec-103">このレッスンでは、Internet Sales パースペクティブを作成します。</span><span class="sxs-lookup"><span data-stu-id="092ec-103">In this lesson, you will create an Internet Sales perspective.</span></span> <span data-ttu-id="092ec-104">パースペクティブでは、表示可能なモデルのサブセットを定義して、集中的、ビジネス固有またはアプリケーション固有のビューポイントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="092ec-104">A perspective defines a viewable subset of a model that provides focused, business-specific, or application-specific viewpoints.</span></span> <span data-ttu-id="092ec-105">パースペクティブを使用してモデルに接続すると、そのパースペクティブ内に定義されたモデル オブジェクト (テーブル、列、メジャー、階層、および KPI) のみがフィールドとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="092ec-105">When a user connects to a model using a perspective, they see only those model objects (tables, columns, measures, hierarchies, and KPIs) as fields defined in that perspective.</span></span>  
  
 <span data-ttu-id="092ec-106">このレッスンで作成する Internet Sales パースペクティブでは、Customer テーブル オブジェクトが除外されます。</span><span class="sxs-lookup"><span data-stu-id="092ec-106">The Internet Sales perspective you create in this lesson will exclude the Customer table object.</span></span> <span data-ttu-id="092ec-107">特定のオブジェクトをビューから除外するパースペクティブを作成した場合、そのオブジェクトはモデル内に依然として存在しますが、レポート クライアントのフィールドの一覧には表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="092ec-107">When you create a perspective that excludes certain objects from view, that object still exists in the model; however, it is not visible in a reporting client field list.</span></span> <span data-ttu-id="092ec-108">計算列とメジャーは、パースペクティブに含まれているかどうかに関係なく、除外されたデータ オブジェクトに基づく計算を引き続き実行できます。</span><span class="sxs-lookup"><span data-stu-id="092ec-108">Calculated columns and measures either included in a perspective or not can still calculate from object data that is excluded.</span></span>  
  
 <span data-ttu-id="092ec-109">このレッスンの目的は、パースペクティブの作成方法を知ることと、テーブル モデル作成ツールに慣れることです。</span><span class="sxs-lookup"><span data-stu-id="092ec-109">The purpose of this lesson is to describe how to create perspectives and become familiar with the tabular model authoring tools.</span></span> <span data-ttu-id="092ec-110">後でこのモデルにテーブルを追加する場合は、追加のパースペクティブを作成して、モデルに対する異なるビューポイント (Inventory や Sales Force など) を定義できます。</span><span class="sxs-lookup"><span data-stu-id="092ec-110">If you later expand this model to include additional tables, you can create additional perspectives to define different viewpoints of the model, for example, Inventory and Sales Force.</span></span>  
  
 <span data-ttu-id="092ec-111">詳細については、「[パースペクティブ (SSAS テーブル)](tabular-models/perspectives-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="092ec-111">To learn more, see [Perspectives &#40;SSAS Tabular&#41;](tabular-models/perspectives-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="092ec-112">このレッスンの推定所要時間: **5 分**</span><span class="sxs-lookup"><span data-stu-id="092ec-112">Estimated time to complete this lesson: **5 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="092ec-113">前提条件</span><span class="sxs-lookup"><span data-stu-id="092ec-113">Prerequisites</span></span>  
 <span data-ttu-id="092ec-114">このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="092ec-114">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="092ec-115">このレッスンの実習を行う前に、前のレッスン「 [レッスン 8: 主要業績評価指標の作成](lesson-7-create-key-performance-indicators.md)」を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="092ec-115">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 8: Create Key Performance Indicators](lesson-7-create-key-performance-indicators.md).</span></span>  
  
## <a name="create-perspectives"></a><span data-ttu-id="092ec-116">パースペクティブを作成する</span><span class="sxs-lookup"><span data-stu-id="092ec-116">Create Perspectives</span></span>  
  
#### <a name="to-create-an-internet-sales-perspective"></a><span data-ttu-id="092ec-117">Internet Sales パースペクティブを作成するには</span><span class="sxs-lookup"><span data-stu-id="092ec-117">To create an Internet Sales perspective</span></span>  
  
1.  <span data-ttu-id="092ec-118">モデルデザイナーで、[**モデル**] メニューをクリックし、[**パースペクティブ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="092ec-118">In the model designer, click the **Model** menu, and then click **Perspectives**.</span></span>  
  
2.  <span data-ttu-id="092ec-119">**[パースペクティブ]** ダイアログ ボックスで、 **[新しいパースペクティブ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="092ec-119">In the **Perspectives** dialog box, click **New Perspective**.</span></span>  
  
3.  <span data-ttu-id="092ec-120">パースペクティブの名前を変更するには、[**新しいパースペクティブ 1** ] 列見出しをダブルクリックし、「」と入力し `Internet Sales` ます。</span><span class="sxs-lookup"><span data-stu-id="092ec-120">To rename the perspective, double-click the **New Perspective 1** column heading, and then type `Internet Sales`.</span></span>  
  
4.  <span data-ttu-id="092ec-121">[**フィールド**] で、 **Date**、 **Geography**、 **Product**、 **product Category**、 **product サブカテゴリ**、およびの各テーブルを選択し `Internet Sales` ます。</span><span class="sxs-lookup"><span data-stu-id="092ec-121">In **Fields**, select the following tables **Date**, **Geography**, **Product**, **Product Category**, **Product Subcategory**, and `Internet Sales`.</span></span>  
  
     <span data-ttu-id="092ec-122">Customer テーブルおよびそのすべての列をこのパースペクティブから除外したことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="092ec-122">Notice you excluded the Customer table and all of its columns from this perspective.</span></span> <span data-ttu-id="092ec-123">後ほど、レッスン 12 で、"Excel で分析" 機能を使用してこのパースペクティブをテストします。</span><span class="sxs-lookup"><span data-stu-id="092ec-123">Later, in Lesson 12, you will use the Analyze in Excel feature to test this perspective.</span></span> <span data-ttu-id="092ec-124">Excel ピボットテーブルのフィールドの一覧には、Customer テーブルを除く各テーブルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="092ec-124">The Excel PivotTable Field List will include each table except the Customer table.</span></span>  
  
5.  <span data-ttu-id="092ec-125">選択内容を確認し、 **Customer** テーブルがオフになっていることを確認して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="092ec-125">Verify your selections, making sure the **Customer** table is not checked, and then click **OK**</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="092ec-126">次の手順</span><span class="sxs-lookup"><span data-stu-id="092ec-126">Next Steps</span></span>  
 <span data-ttu-id="092ec-127">このチュートリアルを続行するには、次のレッスン「 [レッスン 10: 階層の作成](lesson-9-create-hierarchies.md)」に進んでください。</span><span class="sxs-lookup"><span data-stu-id="092ec-127">To continue this tutorial, go to the next lesson: [Lesson 10: Create Hierarchies](lesson-9-create-hierarchies.md).</span></span>  
  
  
