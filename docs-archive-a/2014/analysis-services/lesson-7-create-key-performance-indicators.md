---
title: 'レッスン 8: 主要業績評価指標を作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a6c8ac2b-64ba-456f-b418-7bf0afe145d1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3beaab8a34844ecbd633eb5fabbacf37edfede2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714709"
---
# <a name="lesson-8-create-key-performance-indicators"></a><span data-ttu-id="840e3-102">レッスン 8: 主要業績評価指標を作成する</span><span class="sxs-lookup"><span data-stu-id="840e3-102">Lesson 8: Create Key Performance Indicators</span></span>
  <span data-ttu-id="840e3-103">このレッスンでは、主要業績評価指標 (KPI) を作成します。</span><span class="sxs-lookup"><span data-stu-id="840e3-103">In this lesson, you will create Key Performance Indicators (KPIs).</span></span> <span data-ttu-id="840e3-104">KPI は、値のパフォーマンスを測定するために使用されます。パフォーマンスは、 *"ベース"* メジャーと *"ターゲット"* 値の対比によって定義されます (メジャーまたは絶対値によっても定義できます)。</span><span class="sxs-lookup"><span data-stu-id="840e3-104">KPIs are used to gauge performance of a value, defined by a *Base* measure, against a *Target* value, also defined by a measure or by an absolute value.</span></span> <span data-ttu-id="840e3-105">レポート用のクライアント アプリケーションでは､KPI はビジネスのプロが事業の成功の摘要を理解したり､傾向を把握したりする容易で迅速な手段になります｡</span><span class="sxs-lookup"><span data-stu-id="840e3-105">In reporting client applications, KPIs can provide business professionals a quick and easy way to understand a summary of business success or to identify trends.</span></span> <span data-ttu-id="840e3-106">詳細については、[「KPI (SSAS テーブル)」](tabular-models/kpis-ssas-tabular.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="840e3-106">To learn more, see [KPIs &#40;SSAS Tabular&#41;](tabular-models/kpis-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="840e3-107">このレッスンの推定所要時間: **15 分**</span><span class="sxs-lookup"><span data-stu-id="840e3-107">Estimated time to complete this lesson: **15 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="840e3-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="840e3-108">Prerequisites</span></span>  
 <span data-ttu-id="840e3-109">このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="840e3-109">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="840e3-110">このレッスンの実習を行う前に、前のレッスン [「レッスン 7: メジャーの作成」](lesson-6-create-measures.md)を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="840e3-110">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 7: Create Measures](lesson-6-create-measures.md).</span></span>  
  
## <a name="create-key-performance-indicators"></a><span data-ttu-id="840e3-111">主要業績評価指標を作成する</span><span class="sxs-lookup"><span data-stu-id="840e3-111">Create Key Performance Indicators</span></span>  
  
#### <a name="to-create-an-internet-current-quarter-sales-performance-kpi"></a><span data-ttu-id="840e3-112">Internet Current Quarter Sales Performance KPI を作成するには</span><span class="sxs-lookup"><span data-stu-id="840e3-112">To create an Internet Current Quarter Sales Performance KPI</span></span>  
  
1.  <span data-ttu-id="840e3-113">モデル デザイナーで、[ **Internet Sales** ] テーブル (タブ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="840e3-113">In the model designer, click the **Internet Sales** table (tab).</span></span>  
  
2.  <span data-ttu-id="840e3-114">メジャー グリッドで、空のセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="840e3-114">In the measure grid, click an empty cell.</span></span>  
  
3.  <span data-ttu-id="840e3-115">テーブルの上の数式バーに次の式を入力します｡</span><span class="sxs-lookup"><span data-stu-id="840e3-115">In the formula bar, above the table, type the following formula:</span></span>  
  
     `Internet Current Quarter Sales Performance :=IFERROR([Internet Current Quarter Sales]/[Internet Previous Quarter Sales Proportion to QTD],BLANK())`  
  
     <span data-ttu-id="840e3-116">数式の入力が終了したら、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="840e3-116">When you have finished building the formula, press ENTER.</span></span>  
  
     <span data-ttu-id="840e3-117">このメジャーは、KPI のベース メジャーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="840e3-117">This measure will serve as the Base measure for the KPI.</span></span>  
  
4.  <span data-ttu-id="840e3-118">メジャー グリッドで、 **Internet Current Quarter Sales Performance** メジャーを右クリックし、[ **KPI の作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="840e3-118">In the measure grid, right-click the **Internet Current Quarter Sales Performance** measure, and then click **Create KPI**.</span></span>  
  
     <span data-ttu-id="840e3-119">[ **主要業績評価指標** ] ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="840e3-119">The **Key Performance Indicator** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="840e3-120">[ **主要業績評価指標** ] ダイアログ ボックスの [ **ターゲット値の定義**] で、[ **絶対値** ] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="840e3-120">In the **Key Performance Indicator** dialog box, in **Define Target Value**, select the **Absolute Value** option.</span></span>  
  
6.  <span data-ttu-id="840e3-121">[**絶対値**] フィールドに「」と入力し、enter `1.1` キーを押します。</span><span class="sxs-lookup"><span data-stu-id="840e3-121">In the **Absolute Value** field, type `1.1`, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="840e3-122">[**状態のしきい値の定義**] で、左 (下) のスライダーフィールドに「」と入力し、 `1` 右 (高) のスライダーフィールドに「」と入力し `1.07` ます。</span><span class="sxs-lookup"><span data-stu-id="840e3-122">In **Define Status Thresholds**, in the left (low) slider field, type `1`, and then in the right (high) slider field, type `1.07`.</span></span>  
  
8.  <span data-ttu-id="840e3-123">[ **アイコンのスタイルの選択**] で、ひし形 (赤)、三角形 (黄)、円 (緑) のアイコンの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="840e3-123">In **Select Icon Style**, select the diamond (red), triangle (yellow), circle (green) icon type.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="840e3-124">使用可能なアイコン スタイルの下には [ **説明** ] という展開可能フィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="840e3-124">Notice the **Descriptions** expandable field below the available icon styles.</span></span> <span data-ttu-id="840e3-125">各種の KPI 要素に対する説明を入力することで、それらをクライアント アプリケーションで識別しやすくすることができます。</span><span class="sxs-lookup"><span data-stu-id="840e3-125">You can type descriptions for the various KPI elements to make them more identifiable in client applications.</span></span>  
  
9. <span data-ttu-id="840e3-126">[ **OK** ] をクリックして KPI の作成を完了します。</span><span class="sxs-lookup"><span data-stu-id="840e3-126">Click **OK** to complete the KPI.</span></span>  
  
     <span data-ttu-id="840e3-127">メジャー グリッドで、 **Internet Current Quarter Sales Performance** メジャーの横にアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="840e3-127">In the measure grid, notice the icon next to the **Internet Current Quarter Sales Performance** measure.</span></span> <span data-ttu-id="840e3-128">このアイコンは、そのメジャーが KPI のベース値として機能することを示します。</span><span class="sxs-lookup"><span data-stu-id="840e3-128">This icon indicates that this measure serves as a Base value for a KPI.</span></span>  
  
#### <a name="to-create-an-internet-current-quarter-margin-performance-kpi"></a><span data-ttu-id="840e3-129">Internet Current Quarter Margin Performance KPI を作成するには</span><span class="sxs-lookup"><span data-stu-id="840e3-129">To create an Internet Current Quarter Margin Performance KPI</span></span>  
  
1.  <span data-ttu-id="840e3-130">**Internet Sales** テーブルのメジャー グリッドで、空のセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="840e3-130">In the measure grid for the **Internet Sales** table, click an empty cell.</span></span>  
  
2.  <span data-ttu-id="840e3-131">テーブルの上の数式バーに次の式を入力します｡</span><span class="sxs-lookup"><span data-stu-id="840e3-131">In the formula bar, above the table, type the following formula:</span></span>  
  
     `Internet Current Quarter Margin Performance :=IF([Internet Previous Quarter Margin Proportion to QTD]<>0,([Internet Current Quarter Margin]-[Internet Previous Quarter Margin Proportion to QTD])/[Internet Previous Quarter Margin Proportion to QTD],BLANK())`  
  
     <span data-ttu-id="840e3-132">数式の入力が終了したら、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="840e3-132">When you have finished building the formula, press ENTER.</span></span>  
  
3.  <span data-ttu-id="840e3-133">メジャー グリッドで、 **Internet Current Quarter Margin Performance** メジャーを右クリックし、[ **KPI の作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="840e3-133">In the measure grid, right-click the **Internet Current Quarter Margin Performance** measure, and then click **Create KPI**.</span></span>  
  
4.  <span data-ttu-id="840e3-134">[ **主要業績評価指標** ] ダイアログ ボックスの [ **ターゲット値の定義**] で、[ **絶対値** ] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="840e3-134">In the **Key Performance Indicator** dialog box, in **Define Target Value**, select the **Absolute Value** option.</span></span>  
  
5.  <span data-ttu-id="840e3-135">[**絶対値**] フィールドに「」と入力 `1.25` します。</span><span class="sxs-lookup"><span data-stu-id="840e3-135">In the **Absolute Value** field, type `1.25`.</span></span>  
  
6.  <span data-ttu-id="840e3-136">[ **ステータスのしきい値の定義**] で、左 (下) のスライダー フィールドをスライドして「 **0.8**」と表示させ、右 (上) のスライダー フィールドをスライドして「 **1.03**」と表示させます。</span><span class="sxs-lookup"><span data-stu-id="840e3-136">In **Define Status Thresholds**, slide the left (low) slider field until the field displays **0.8**, and then slide the right (high) slider field, until the field displays **1.03**.</span></span>  
  
7.  <span data-ttu-id="840e3-137">**[Select Icon Style]** で､アイコン タイプとして菱形 (赤)､三角形 (黄色)､円 (緑) を選択し､**[OK]** をクリックします｡</span><span class="sxs-lookup"><span data-stu-id="840e3-137">In **Select Icon Style**, select the diamond (red), triangle (yellow), circle (green) icon type, and then click **OK**.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="840e3-138">次の手順</span><span class="sxs-lookup"><span data-stu-id="840e3-138">Next Step</span></span>  
 <span data-ttu-id="840e3-139">このチュートリアルを続行するには、次のレッスン [「レッスン 9: パースペクティブの作成」](lesson-8-create-perspectives.md)に進んでください。</span><span class="sxs-lookup"><span data-stu-id="840e3-139">To continue this tutorial, go to the next lesson: [Lesson 9: Create Perspectives](lesson-8-create-perspectives.md).</span></span>  
  
  
