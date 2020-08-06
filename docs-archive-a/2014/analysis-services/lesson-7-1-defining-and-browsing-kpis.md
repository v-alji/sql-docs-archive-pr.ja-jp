---
title: Kpi の定義と参照 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 648b9a02-1278-4f11-b940-6f0de6a4042d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44febe6c6c5d432f0cdee43e8eaaa3401c54a2c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714721"
---
# <a name="defining-and-browsing-kpis"></a><span data-ttu-id="b1d12-102">KPI の定義と表示</span><span class="sxs-lookup"><span data-stu-id="b1d12-102">Defining and Browsing KPIs</span></span>
  <span data-ttu-id="b1d12-103">主要業績評価指標 (KPI) を定義するには、まず、KPI の名前と、KPI に関連するメジャー グループを定義します。</span><span class="sxs-lookup"><span data-stu-id="b1d12-103">To define key performance indicators (KPIs), you first define a KPI name and the measure group to which the KPI is associated.</span></span> <span data-ttu-id="b1d12-104">すべてのメジャー グループ、または単一のメジャー グループを KPI に関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="b1d12-104">A KPI can be associated with all measure groups or with a single measure group.</span></span> <span data-ttu-id="b1d12-105">その後、KPI の次のような要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="b1d12-105">You then define the following elements of the KPI:</span></span>

-   <span data-ttu-id="b1d12-106">値式</span><span class="sxs-lookup"><span data-stu-id="b1d12-106">The value expression</span></span>

     <span data-ttu-id="b1d12-107">値式とは、物理的メジャー (売上高など)、計算されるメジャー (利益など)、または KPI 内で多次元式 (MDX) を使用して定義される計算です。</span><span class="sxs-lookup"><span data-stu-id="b1d12-107">A value expression is a physical measure such as Sales, a calculated measure such as Profit, or a calculation that is defined within the KPI by using a Multidimensional Expressions (MDX) expression.</span></span>

-   <span data-ttu-id="b1d12-108">目標式</span><span class="sxs-lookup"><span data-stu-id="b1d12-108">The goal expression</span></span>

     <span data-ttu-id="b1d12-109">目標式とは、値、または値に解決される MDX 式です。目標式では、値式が定義するメジャーのターゲットを定義します。</span><span class="sxs-lookup"><span data-stu-id="b1d12-109">A goal expression is a value, or an MDX expression that resolves to a value, that defines the target for the measure that the value expression defines.</span></span> <span data-ttu-id="b1d12-110">たとえば、企業の経営層が目標とする売上または利益の増加額を目標式にすることができます。</span><span class="sxs-lookup"><span data-stu-id="b1d12-110">For example, a goal expression could be the amount by which the business managers of a company want to increase sales or profit.</span></span>

-   <span data-ttu-id="b1d12-111">状態式</span><span class="sxs-lookup"><span data-stu-id="b1d12-111">The status expression</span></span>

     <span data-ttu-id="b1d12-112">状態式とは、目標式と比較した値式の現在の状態を評価するために [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で使用される MDX 式です。</span><span class="sxs-lookup"><span data-stu-id="b1d12-112">A status expression is an MDX expression that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses to evaluate the current status of the value expression compared to the goal expression.</span></span> <span data-ttu-id="b1d12-113">目標式は -1 ～ +1 の範囲で正規化された値です (-1 は非常に悪い、+1 は非常に良い)。</span><span class="sxs-lookup"><span data-stu-id="b1d12-113">A goal expression is a normalized value in the range of -1 to +1, where -1 is very bad, and +1 is very good.</span></span> <span data-ttu-id="b1d12-114">状態式では、目標式と比べた値式の状態を簡単に判別できるようにグラフィックが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1d12-114">The status expression displays a graphic to help you easily determine the status of the value expression compared to the goal expression.</span></span>

-   <span data-ttu-id="b1d12-115">傾向式</span><span class="sxs-lookup"><span data-stu-id="b1d12-115">The trend expression</span></span>

     <span data-ttu-id="b1d12-116">傾向式とは、目標式と比較した値式の現在の傾向を評価するために [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で使用される MDX 式です。</span><span class="sxs-lookup"><span data-stu-id="b1d12-116">A trend expression is an MDX expression that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses to evaluate the current trend of the value expression compared to the goal expression.</span></span> <span data-ttu-id="b1d12-117">傾向式を使用すれば、目標式と比べて値式が改善しているか、それとも悪化しているかをビジネス ユーザーがすばやく判別できます。</span><span class="sxs-lookup"><span data-stu-id="b1d12-117">The trend expression helps the business user to quickly determine whether the value expression is becoming better or worse relative to the goal expression.</span></span> <span data-ttu-id="b1d12-118">いずれか 1 つのグラフィックを傾向式に関連付けることで、ビジネス ユーザーは傾向をすばやく把握できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b1d12-118">You can associate one of several graphics with the trend expression to help business users be able to quickly understand the trend.</span></span>

 <span data-ttu-id="b1d12-119">これらの KPI 要素の定義に加えて、いくつかの KPI プロパティも定義します。</span><span class="sxs-lookup"><span data-stu-id="b1d12-119">In addition to these elements that you define for a KPI, you also define several properties of a KPI.</span></span> <span data-ttu-id="b1d12-120">定義するプロパティには、表示フォルダー、親 KPI (他の KPI から計算される KPI の場合)、現在の時間メンバー (存在する場合)、KPI の重み (存在する場合)、KPI についての説明などがあります。</span><span class="sxs-lookup"><span data-stu-id="b1d12-120">These properties include a display folder, a parent KPI if the KPI is computed from other KPIs, the current time member if there is one, the weight of the KPI if it has one, and a description of the KPI.</span></span>

> [!NOTE]
>  <span data-ttu-id="b1d12-121">KPI の詳しいサンプルについては、[計算ツール] ペインの [テンプレート] タブの KPI サンプル、または **Adventure Works DW 2012** サンプル データ ウェアハウスの KPI サンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1d12-121">For more examples of KPIs, see the KPI examples on the Templates tab in the Calculation Tools pane or in the examples in the **Adventure Works DW 2012** sample data warehouse.</span></span> <span data-ttu-id="b1d12-122">このデータベースのインストールの詳細については、「 [Analysis Services 多次元モデリング チュートリアル用のサンプル データおよびプロジェクトのインストール](install-sample-data-and-projects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1d12-122">For more information about how to install this database, see [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md).</span></span>

 <span data-ttu-id="b1d12-123">このレッスンの実習では、KPI を [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクト内で定義した後、これらの KPI を使用して [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブを表示します。</span><span class="sxs-lookup"><span data-stu-id="b1d12-123">In the task in this lesson, you define  KPIs in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project, and you then browse the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube by using these KPIs.</span></span> <span data-ttu-id="b1d12-124">次の KPI を定義します。</span><span class="sxs-lookup"><span data-stu-id="b1d12-124">You will define the following KPIs:</span></span>

-   <span data-ttu-id="b1d12-125">Reseller Revenue</span><span class="sxs-lookup"><span data-stu-id="b1d12-125">Reseller Revenue</span></span>

     <span data-ttu-id="b1d12-126">この KPI を使用して、再販業者の実際の売上高を販売ノルマと比較し、売上高が目標にどれだけ近いか、どのような傾向で目標を達成しつつあるかを計測します。</span><span class="sxs-lookup"><span data-stu-id="b1d12-126">This KPI is used to measure how actual reseller sales compare to sales quotas for reseller sales, how close the sales are to the goal, and what the trend is toward reaching the goal.</span></span>

-   <span data-ttu-id="b1d12-127">Product Gross Profit Margin</span><span class="sxs-lookup"><span data-stu-id="b1d12-127">Product Gross Profit Margin</span></span>

     <span data-ttu-id="b1d12-128">この KPI を使用して、各製品カテゴリの売上総利益率がその具体目標値にどれだけ近いか、およびこの目標の達成傾向を判断します。</span><span class="sxs-lookup"><span data-stu-id="b1d12-128">This KPI is used to determine how close the gross profit margin is for each product category to a specified goal for each product category, and also to determine the trend toward reaching this goal.</span></span>

## <a name="defining-the-reseller-revenue-kpi"></a><span data-ttu-id="b1d12-129">Reseller Revenue KPI の定義</span><span class="sxs-lookup"><span data-stu-id="b1d12-129">Defining the Reseller Revenue KPI</span></span>

1.  <span data-ttu-id="b1d12-130">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーを開いて、 **[KPI]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1d12-130">Open Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **KPIs** tab.</span></span>

     <span data-ttu-id="b1d12-131">**[KPI]** タブにはいくつかのペインがあります。</span><span class="sxs-lookup"><span data-stu-id="b1d12-131">The **KPIs** tab includes several panes.</span></span> <span data-ttu-id="b1d12-132">タブの左側には **[KPI オーガナイザー]** ペインと **[計算ツール]** ペインがあります。</span><span class="sxs-lookup"><span data-stu-id="b1d12-132">On the left side of the tab are the **KPI Organizer** pane and the **Calculation Tools** pane.</span></span> <span data-ttu-id="b1d12-133">**[KPI オーガナイザー]** ペインで KPI を選択すると、その KPI の詳細が中央の表示ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1d12-133">The display pane in the middle of the tab contains the details of the KPI that is selected in the **KPI Organizer** pane.</span></span>

     <span data-ttu-id="b1d12-134">次の図は、キューブ デザイナーの **[KPI]** タブを示しています。</span><span class="sxs-lookup"><span data-stu-id="b1d12-134">The following image shows the **KPIs** tab of Cube Designer.</span></span>

     <span data-ttu-id="b1d12-135">![キューブ デザイナーの [KPI] タブ](../../2014/tutorials/media/l7-kpi-1.gif "キューブ デザイナーの [KPI] タブ")</span><span class="sxs-lookup"><span data-stu-id="b1d12-135">![KPIs tab of Cube Designer](../../2014/tutorials/media/l7-kpi-1.gif "KPIs tab of Cube Designer")</span></span>

2.  <span data-ttu-id="b1d12-136">**[KPI]** タブのツール バーで **[新しい KPI]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1d12-136">On the toolbar of the **KPIs** tab, click the **New KPI** button.</span></span>

     <span data-ttu-id="b1d12-137">次の図のように、空白の KPI テンプレートが表示ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1d12-137">A blank KPI template appears in the display pane, as shown in the following image.</span></span>

     <span data-ttu-id="b1d12-138">![表示ペインの空白の KPI テンプレート](../../2014/tutorials/media/l7-kpi-2.gif "表示ペインの空白の KPI テンプレート")</span><span class="sxs-lookup"><span data-stu-id="b1d12-138">![Blank KPI template in display pane](../../2014/tutorials/media/l7-kpi-2.gif "Blank KPI template in display pane")</span></span>

3.  <span data-ttu-id="b1d12-139">[**名前**] ボックスに「 `Reseller Revenue` 」と入力し、[**関連付けられているメジャーグループ**] ボックスの一覧で [**再販業者の売上**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b1d12-139">In the **Name** box, type `Reseller Revenue`, and then select **Reseller Sales** in the **Associated measure group** list.</span></span>

4.  <span data-ttu-id="b1d12-140">**[計算ツール]** ペインの **[メタデータ]** タブで、 **[Measures]**、 **[Reseller Sales]** の順に展開します。次に、 **Reseller Sales-Sales Amount** メジャーを **[値式]** ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="b1d12-140">On the **Metadata** tab in the **Calculation Tools** pane, expand **Measures**, expand **Reseller Sales**, and then drag the **Reseller Sales-Sales Amount** measure to the **Value Expression** box.</span></span>

5.  <span data-ttu-id="b1d12-141">**[計算ツール]** ペインの **[メタデータ]** タブで、 **[Measures]**、 **[Sales Quotas]** の順に展開します。次に、 **Sales Amount Quota** メジャーを **[目標式]** ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="b1d12-141">On the **Metadata** tab in the **Calculation Tools** pane, expand **Measures**, expand **Sales Quotas**, and then drag the **Sales Amount Quota** measure to the **Goal Expression** box.</span></span>

6.  <span data-ttu-id="b1d12-142">**[状態インジケーター]** ボックスの一覧で **[ゲージ]** が選択されていることを確認します。次に、以下の MDX 式を **[状態式]** ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="b1d12-142">Verify that **Gauge** is selected in the **Status indicator** list, and then type the following MDX expression in the **Status expression** box:</span></span>

    ```
    Case
     When 
      KpiValue("Reseller Revenue")/KpiGoal("Reseller Revenue")>=.95
       Then 1
     When
      KpiValue("Reseller Revenue")/KpiGoal("Reseller Revenue")<.95
       And 
      KpiValue("Reseller Revenue")/KpiGoal("Reseller Revenue")>=.85
       Then 0
      Else-1
    End
    ```

     <span data-ttu-id="b1d12-143">この MDX 式は、目標達成度を評価する基になります。</span><span class="sxs-lookup"><span data-stu-id="b1d12-143">This MDX expression provides the basis for evaluating the progress toward the goal.</span></span> <span data-ttu-id="b1d12-144">この MDX 式では、再販業者の実際の売上が目標の 85% を超えていれば、選択されたグラフィックを値 0 を使用して設定します。</span><span class="sxs-lookup"><span data-stu-id="b1d12-144">In this MDX expression, if actual reseller sales are more than 85 percent of the goal, a value of 0 is used to populate the chosen graphic.</span></span> <span data-ttu-id="b1d12-145">グラフィックとしてゲージが選択されているため、ゲージ内のポインターは空と満杯の中間を指します。</span><span class="sxs-lookup"><span data-stu-id="b1d12-145">Because a gauge is the chosen graphic, the pointer in the gauge will be half-way between empty and full.</span></span> <span data-ttu-id="b1d12-146">再販業者の実際の売上が 90% を超えている場合、ゲージ上のポインターは空から満杯に向かって 3/4 の位置に示されます。</span><span class="sxs-lookup"><span data-stu-id="b1d12-146">If actual reseller sales are more the 90 percent, the pointer on the gauge will be three-fourths of the way between empty and full.</span></span>

7.  <span data-ttu-id="b1d12-147">**[傾向インジケーター]** ボックスの一覧で **[標準の矢印]** が選択されていることを確認します。次に、以下の式を **[傾向式]** ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="b1d12-147">Verify that **Standard arrow** is selected in the **Trend indicator** list, and then type the following expression in the **Trend expression** box:</span></span>

    ```
    Case
     When IsEmpty
      (ParallelPeriod
       ([Date].[Calendar Date].[Calendar Year],1,
           [Date].[Calendar Date].CurrentMember))
      Then 0  
     When  (
      KpiValue("Reseller Revenue") - 
       (KpiValue("Reseller Revenue"), 
        ParallelPeriod
         ([Date].[Calendar Date].[Calendar Year],1,
           [Date].[Calendar Date].CurrentMember))
          /
          (KpiValue ("Reseller Revenue"),
           ParallelPeriod
            ([Date].[Calendar Date].[Calendar Year],1,
             [Date].[Calendar Date].CurrentMember)))
           >=.02
      Then 1
       When(
        KpiValue("Reseller Revenue") - 
         (KpiValue ( "Reseller Revenue" ),
          ParallelPeriod
           ([Date].[Calendar Date].[Calendar Year],1,
            [Date].[Calendar Date].CurrentMember))
           /
            (KpiValue("Reseller Revenue"),
             ParallelPeriod
              ([Date].[Calendar Date].[Calendar Year],1,
                [Date].[Calendar Date].CurrentMember)))
            <=.02
      Then -1
       Else 0
    End
    ```

     <span data-ttu-id="b1d12-148">この MDX 式は、定義された目標がどのように達成されつつあるかの傾向を評価する基になります。</span><span class="sxs-lookup"><span data-stu-id="b1d12-148">This MDX expression provides the basis for evaluating the trend toward achieving the defined goal.</span></span>

## <a name="browsing-the-cube-by-using-the-reseller-revenue-kpi"></a><span data-ttu-id="b1d12-149">Reseller Revenue KPI を使用したキューブの表示</span><span class="sxs-lookup"><span data-stu-id="b1d12-149">Browsing the Cube by Using the Reseller Revenue KPI</span></span>

1.  <span data-ttu-id="b1d12-150">**の** [ビルド] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]メニューで、 **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1d12-150">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Service Tutorial**.</span></span>

2.  <span data-ttu-id="b1d12-151">配置が正常に完了したら、 **[KPI]** タブのツール バーの **[ブラウザー ビュー]** ボタンをクリックし、 **[再接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1d12-151">When deployment has successfully completed, on the toolbar of the **KPIs** tab, click the **Browser View** button, and then click **Reconnect**.</span></span>

     <span data-ttu-id="b1d12-152">各ディメンションの既定のメンバーの値に基づき、状態ゲージおよび傾向ゲージが再販業者の売上の **[KPI ブラウザー]** ペインに表示され、それと共に値と目標の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1d12-152">The status and trend gauges are displayed in the **KPI Browser** pane for reseller sales based on the values for the default member of each dimension, together with the value for the value and the goal.</span></span> <span data-ttu-id="b1d12-153">現時点では、どのディメンションのどのメンバーも既定のメンバーとしてまだ定義されていないため、各ディメンションの既定のメンバーは全レベルの全メンバーです。</span><span class="sxs-lookup"><span data-stu-id="b1d12-153">The default member of each dimension is the All member of the All level, because you have not defined any other member of any dimension as the default member.</span></span>

3.  <span data-ttu-id="b1d12-154">[フィルター] ペインで、 **[ディメンション]** ボックスの一覧の **[Sales Territory]** をクリックし、 **[階層]** ボックスの一覧の **[Sales Territories]** をクリックし、 **[演算子]** ボックスの一覧の **[等しい]** をクリックします。次に、 **[フィルター式]** ボックスの一覧で **[North America]** チェック ボックスをオンにし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1d12-154">In the filter pane, select **Sales Territory** in the **Dimension** list, select **Sales Territories** in the **Hierarchy** list, select **Equal** in the **Operator** list, select the **North America** check box in the **Filter Expression** list, and then click **OK**.</span></span>

4.  <span data-ttu-id="b1d12-155">**[フィルター]** ペインの次の行で、 **[ディメンション]** ボックスの一覧の **[Date]** をクリックし、 **[階層]** ボックスの一覧の **[Calendar Date]** をクリックし、 **[演算子]** ボックスの一覧の **[等しい]** をクリックします。次に、 **[フィルター式]** ボックスの一覧で **[Q3 CY 2007]** チェック ボックスをオンにし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1d12-155">In the next row in the **Filter** pane, select **Date** in the **Dimension** list, select **Calendar Date** in the **Hierarchy** list, select **Equal** in the **Operator** list, select the **Q3 CY 2007** check box in the **Filter Expression** list, and then click **OK**.</span></span>

5.  <span data-ttu-id="b1d12-156">**[KPI ブラウザー]** ペイン内の任意の場所をクリックすると、 **Reseller Revenue KPI**の値が更新されます。</span><span class="sxs-lookup"><span data-stu-id="b1d12-156">Click anywhere in the **KPI Browser** pane to update the values for the **Reseller Revenue KPI**.</span></span>

     <span data-ttu-id="b1d12-157">KPI の **[値]**、 **[目標]**、および **[状態]** セクションに新しい期間の値が反映されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="b1d12-157">Notice that the **Value**, **Goal**, and **Status** sections of the KPI reflect the values for the new time period</span></span>

## <a name="defining-the-product-gross-profit-margin-kpi"></a><span data-ttu-id="b1d12-158">Product Gross Profit Margin KPI の定義</span><span class="sxs-lookup"><span data-stu-id="b1d12-158">Defining the Product Gross Profit Margin KPI</span></span>

1.  <span data-ttu-id="b1d12-159">**[KPI]** タブのツール バーの **[フォーム ビュー]** ボタンをクリックして、 **[新しい KPI]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1d12-159">Click the **Form View** button on the toolbar of the **KPIs** tab, and then click the **New KPI** button.</span></span>

2.  <span data-ttu-id="b1d12-160">[**名前**] ボックスに「 `Product Gross Profit Margin` 」と入力し、[関連付けられている **\<All>** **メジャーグループ**] ボックスの一覧にが表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b1d12-160">In the **Name** box, type `Product Gross Profit Margin`, and then verify that **\<All>** appears in the **Associated measure group** list.</span></span>

3.  <span data-ttu-id="b1d12-161">**[計算ツール]** ペインの **[メタデータ]** タブで、 **Total GPM** メジャーを **[値式]** ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="b1d12-161">In the **Metadata** tab in the **Calculation Tools** pane, drag the **Total GPM** measure to the **Value Expression** box.</span></span>

4.  <span data-ttu-id="b1d12-162">**[目標式]** ボックスに、次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="b1d12-162">In the **Goal Expression** box, type the following expression:</span></span>

    ```
    Case
        When [Product].[Category].CurrentMember Is
          [Product].[Category].[Accessories]
        Then .40                 
        When [Product].[Category].CurrentMember 
          Is [Product].[Category].[Bikes]
        Then .12                
        When [Product].[Category].CurrentMember Is
          [Product].[Category].[Clothing]
        Then .20
        When [Product].[Category].CurrentMember Is
          [Product].[Category].[Components]
        Then .10
        Else .12            
    End
    ```

5.  <span data-ttu-id="b1d12-163">**[状態インジケーター]** ボックスの一覧で **[シリンダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1d12-163">In the **Status indicator** list, select **Cylinder**.</span></span>

6.  <span data-ttu-id="b1d12-164">以下の MDX 式を **[状態式]** ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="b1d12-164">Type the following MDX expression in the **Status expression** box:</span></span>

    ```
    Case
        When KpiValue( "Product Gross Profit Margin" ) / 
             KpiGoal ( "Product Gross Profit Margin" ) >= .90
        Then 1
        When KpiValue( "Product Gross Profit Margin" ) / 
             KpiGoal ( "Product Gross Profit Margin" ) <  .90
             And 
             KpiValue( "Product Gross Profit Margin" ) / 
             KpiGoal ( "Product Gross Profit Margin" ) >= .80
        Then 0
        Else -1
    End
    ```

     <span data-ttu-id="b1d12-165">この MDX 式は、目標達成度を評価する基になります。</span><span class="sxs-lookup"><span data-stu-id="b1d12-165">This MDX expression provides the basis for evaluating the progress toward the goal.</span></span>

7.  <span data-ttu-id="b1d12-166">**[傾向インジケーター]** ボックスの一覧で **[標準の矢印]** が選択されていることを確認します。次に、以下の MDX 式を **[傾向式]** ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="b1d12-166">Verify that **Standard arrow** is selected in the **Trend indicator** list, and then type the following MDX expression in the **Trend expression** box:</span></span>

    ```
    Case
    When IsEmpty
      (ParallelPeriod
       ([Date].[Calendar Date].[Calendar Year],1,
           [Date].[Calendar Date].CurrentMember))
      Then 0  
       When VBA!Abs
        (
          KpiValue( "Product Gross Profit Margin" ) - 
           (
             KpiValue ( "Product Gross Profit Margin" ),
              ParallelPeriod
              ( 
                [Date].[ Calendar Date].[ Calendar Year],
                1,
                [Date].[ Calendar Date].CurrentMember
              )
            ) /
            (
              KpiValue ( "Product Gross Profit Margin" ),
              ParallelPeriod
              ( 
                [Date].[ Calendar Date].[ Calendar Year],
                1,
                [Date].[ Calendar Date].CurrentMember
              )
            )  
          ) <=.02
      Then 0
      When KpiValue( "Product Gross Profit Margin" ) - 
           (
             KpiValue ( "Product Gross Profit Margin" ),
             ParallelPeriod
             ( 
               [Date].[ Calendar Date].[ Calendar Year],
               1,
               [Date].[ Calendar Date].CurrentMember
             )
           ) /
           (
             KpiValue ( "Product Gross Profit Margin" ),
             ParallelPeriod
             ( 
               [Date].[Calendar Date].[Calendar Year],
               1,
               [Date].[Calendar Date].CurrentMember
             )
           )  >.02
      Then 1
      Else -1
    End
    ```

     <span data-ttu-id="b1d12-167">この MDX 式は、定義された目標がどのように達成されつつあるかの傾向を評価する基になります。</span><span class="sxs-lookup"><span data-stu-id="b1d12-167">This MDX expression provides the basis for evaluating the trend toward achieving the defined goal.</span></span>

## <a name="browsing-the-cube-by-using-the-total-gross-profit-margin-kpi"></a><span data-ttu-id="b1d12-168">Total Gross Profit Margin KPI を使用したキューブの表示</span><span class="sxs-lookup"><span data-stu-id="b1d12-168">Browsing the Cube by Using the Total Gross Profit Margin KPI</span></span>

1.  <span data-ttu-id="b1d12-169">**[ビルド]** メニューで、 **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1d12-169">On the **Build** menu, click **Deploy Analysis Service Tutorial**.</span></span>

2.  <span data-ttu-id="b1d12-170">配置が正常に完了したら、 **[KPI]** タブのツール バーの **[再接続]** をクリックして、 **[ブラウザー ビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1d12-170">When deployment has successfully completed, click **Reconnect** on the toolbar of the **KPIs** tab, and then click **Browser View**.</span></span>

     <span data-ttu-id="b1d12-171">`Product Gross Profit Margin`Kpi が表示され、 **Q3 CY 2007**と**北米**販売区域の kpi 値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1d12-171">The `Product Gross Profit Margin` KPI appears and displays the KPI value for **Q3 CY 2007** and the **North America** sales territory.</span></span>

3.  <span data-ttu-id="b1d12-172">**[フィルター]** ペインで、 **[ディメンション]** ボックスの一覧の **[Product]** をクリックし、 **[階層]** ボックスの一覧の **[Category]** をクリックし、 **[演算子]** ボックスの一覧の **[等しい]** をクリックします。次に、 **[フィルター式]** ボックスの一覧で **[Bikes]** チェック ボックスをオンにし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1d12-172">In the **Filter** pane, select **Product** in the **Dimension** list, select **Category** in the **Hierarchy** list, select **Equal** in the **Operator** list, and then select **Bikes** in the **Filter Expression** list, and then click **OK**.</span></span>

     <span data-ttu-id="b1d12-173">Q3 CY 2007 の North America における小売店のバイクの売上総利益率が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1d12-173">The gross profit margin for the sale of Bikes by resellers in North America in Q3 CY 2007 appears.</span></span>

## <a name="next-lesson"></a><span data-ttu-id="b1d12-174">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="b1d12-174">Next Lesson</span></span>
 [<span data-ttu-id="b1d12-175">レッスン 8: アクションの定義</span><span class="sxs-lookup"><span data-stu-id="b1d12-175">Lesson 8: Defining Actions</span></span>](lesson-8-defining-actions.md)


