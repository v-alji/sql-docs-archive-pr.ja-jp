---
title: 'レッスン 6: 計算の定義 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e0a1e354-e879-4eb8-bb2b-6c3809e32cb6
author: minewiskan
ms.author: owend
ms.openlocfilehash: e0b3f7e925a11146204dc6c55e9ddd6820ecb802
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639741"
---
# <a name="lesson-6-defining-calculations"></a><span data-ttu-id="d2b69-102">レッスン 6: 計算の定義</span><span class="sxs-lookup"><span data-stu-id="d2b69-102">Lesson 6: Defining Calculations</span></span>
  <span data-ttu-id="d2b69-103">このレッスンでは、多次元式 (MDX) の式またはスクリプトである計算を定義する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="d2b69-103">In this lesson, you learn to define calculations, which are Multidimensional Expressions (MDX) expressions or scripts.</span></span> <span data-ttu-id="d2b69-104">計算を使用すると、計算されるメンバーや名前付きセットを定義できます。また、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] キューブの機能を拡張するさまざまなスクリプト コマンドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="d2b69-104">Calculations enable you to define calculated members, named sets, and execute other script commands to extend the capabilities of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube.</span></span> <span data-ttu-id="d2b69-105">たとえば、サブキューブを定義し、計算をサブキューブ内のセルに割り当てるスクリプト コマンドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="d2b69-105">For example, you can run a script command to define a subcube and then assign a calculation to the cells in the subcube.</span></span>  
  
 <span data-ttu-id="d2b69-106">新しい計算をキューブ デザイナーで定義すると、その計算はキューブ デザイナーの **[計算]** タブの **[スクリプト オーガナイザー]** ペインに追加され、特定の計算の種類に対応するフィールドが **計算式** ペインの計算フォームに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d2b69-106">When you define a new calculation in Cube Designer, the calculation is added to the **Script Organizer** pane of the **Calculations** tab of Cube Designer, and the fields for the particular calculation type are displayed in a calculations form in the **Calculation Expressions** pane.</span></span> <span data-ttu-id="d2b69-107">複数の計算は、 **[スクリプト オーガナイザー]** ペイン内に表示されている順番で実行されます。</span><span class="sxs-lookup"><span data-stu-id="d2b69-107">Calculations are executed in the order in which they are listed in the **Script Organizer** pane.</span></span> <span data-ttu-id="d2b69-108">計算の順序を変えるには、特定の計算を右クリックして **[上へ移動]** または **[下へ移動]** をクリックします。または、特定の計算をクリックし、 **[計算]** タブのツール バーにある **[上へ移動]** または **[下へ移動]** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2b69-108">You can reorder the calculations by right-clicking on a particular calculation and then selecting **Move Up** or **Move Down**, or by clicking a particular calculation and then using the **Move Up** or **Move Down** icons on the toolbar of the **Calculations** tab.</span></span>  
  
 <span data-ttu-id="d2b69-109">**[計算]** タブでは、 **計算式** ペイン内の次のビューを使用して、新しい計算の追加や、既存の計算の表示または編集を行えます。</span><span class="sxs-lookup"><span data-stu-id="d2b69-109">On the **Calculations** tab, you can add new calculations and view or edit existing calculations in the following views in the **Calculation Expressions** pane:</span></span>  
  
-   <span data-ttu-id="d2b69-110">フォーム ビュー。</span><span class="sxs-lookup"><span data-stu-id="d2b69-110">Form view.</span></span> <span data-ttu-id="d2b69-111">このビューには、1 つのコマンドの式とプロパティがグラフィック形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="d2b69-111">This view shows the expressions and properties for a single command in a graphical format.</span></span> <span data-ttu-id="d2b69-112">MDX スクリプトを編集する場合は、式ボックスがフォーム ビューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d2b69-112">When you edit an MDX script, an expression box fills the Form view.</span></span>  
  
-   <span data-ttu-id="d2b69-113">スクリプト ビュー。</span><span class="sxs-lookup"><span data-stu-id="d2b69-113">Script view.</span></span> <span data-ttu-id="d2b69-114">このビューでは、すべての計算スクリプトがコード エディター内に表示されます。これを使用して、計算スクリプトを簡単に変更できます。</span><span class="sxs-lookup"><span data-stu-id="d2b69-114">This view displays all calculation scripts in a code editor, which lets you easily change the calculation scripts.</span></span> <span data-ttu-id="d2b69-115">**計算式** ペインがスクリプト ビューになっているとき、 **[スクリプト オーガナイザー]** は非表示になります。</span><span class="sxs-lookup"><span data-stu-id="d2b69-115">When the **Calculation Expressions** pane is in Script view, the **Script Organizer** is hidden.</span></span> <span data-ttu-id="d2b69-116">スクリプト ビューには、色分け表示、かっこの対応、オートコンプリート、MDX コード領域などの機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="d2b69-116">The Script view provides color coding, parenthesis matching, auto-complete, and MDX code regions.</span></span> <span data-ttu-id="d2b69-117">MDX コード領域は展開や折りたたみが可能なので、容易に編集を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="d2b69-117">You can expand or collapse the MDX code regions to make editing easier.</span></span>  
  
 <span data-ttu-id="d2b69-118">**計算式** ペイン内でこれらのビューを切り替えるには、 **[計算]** タブのツール バーの **[フォーム ビュー]** または **[スクリプト ビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2b69-118">To switch between these views in the **Calculation Expressions** pane, click **Form View** or **Script View** on the toolbar of the **Calculations** tab.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d2b69-119">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] がいずれかの計算の構文エラーを検出した場合、スクリプト ビュー内でエラーを修正するまでは、フォーム ビューが表示されません。</span><span class="sxs-lookup"><span data-stu-id="d2b69-119">If [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] detects a syntax error in any calculation, the Form view will not display until the error is corrected in the Script view.</span></span>  
  
 <span data-ttu-id="d2b69-120">また、ビジネス インテリジェンス ウィザードを使用して特定の計算をキューブに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="d2b69-120">You can also use the Business Intelligence Wizard to add certain calculations to a cube.</span></span> <span data-ttu-id="d2b69-121">たとえば、このウィザードを使ってタイム インテリジェンスをキューブに追加できます。タイム インテリジェンスでは、期間対日付、移動平均、前期比成長率など、時間に関連した計算されるメンバーを定義します。</span><span class="sxs-lookup"><span data-stu-id="d2b69-121">For example, you can use this wizard to add time intelligence to a cube, which means defining calculated members for time-related calculations such as period-to-date, moving averages, or period over period growth.</span></span> <span data-ttu-id="d2b69-122">詳細については、「 [ビジネス インテリジェンス ウィザードを使用したタイム インテリジェンス計算の定義](multidimensional-models/define-time-intelligence-calculations-using-the-business-intelligence-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2b69-122">For more information, see [Define Time Intelligence Calculations using the Business Intelligence Wizard](multidimensional-models/define-time-intelligence-calculations-using-the-business-intelligence-wizard.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d2b69-123">**[計算]** タブでは、計算スクリプトは CALCULATE コマンドで始まります。</span><span class="sxs-lookup"><span data-stu-id="d2b69-123">On the **Calculations** tab, the calculation script starts with the CALCULATE command.</span></span> <span data-ttu-id="d2b69-124">CALCULATE コマンドはキューブ内のセルの集計を制御します。キューブ セルの集計方法を手動で指定する場合のみ、このコマンドを編集してください。</span><span class="sxs-lookup"><span data-stu-id="d2b69-124">The CALCULATE command controls the aggregation of the cells in the cube and you should edit this command only if you intend to manually specify how the cube cells should be aggregated.</span></span>  
  
 <span data-ttu-id="d2b69-125">詳細については、「 [計算](multidimensional-models-olap-logical-cube-objects/calculations.md)」および「 [多次元モデルの計算](multidimensional-models/calculations-in-multidimensional-models.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2b69-125">For more information, see [Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md), and [Calculations in Multidimensional Models](multidimensional-models/calculations-in-multidimensional-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d2b69-126">このチュートリアルの各レッスンの操作内容が反映されたプロジェクトを、オンラインで入手できます。</span><span class="sxs-lookup"><span data-stu-id="d2b69-126">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="d2b69-127">途中のレッスンから開始する場合は、前のレッスンの操作内容が反映されたプロジェクトを作業の開始点として使用できます。</span><span class="sxs-lookup"><span data-stu-id="d2b69-127">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="d2b69-128">このチュートリアルのサンプル プロジェクトをダウンロードするには、[ここ](https://go.microsoft.com/fwlink/?LinkID=221866) をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="d2b69-128">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 <span data-ttu-id="d2b69-129">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d2b69-129">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="d2b69-130">計算されるメンバーの定義</span><span class="sxs-lookup"><span data-stu-id="d2b69-130">Defining Calculated Members</span></span>](lesson-6-1-defining-calculated-members.md)  
 <span data-ttu-id="d2b69-131">ここでは、計算されるメンバーを定義する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="d2b69-131">In this task, you learn to define calculated members.</span></span>  
  
 [<span data-ttu-id="d2b69-132">名前付きセットの定義</span><span class="sxs-lookup"><span data-stu-id="d2b69-132">Defining Named Sets</span></span>](lesson-6-2-defining-named-sets.md)  
 <span data-ttu-id="d2b69-133">この作業では、名前付きセットを定義する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="d2b69-133">In this task, you learn to define named sets.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="d2b69-134">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="d2b69-134">Next Lesson</span></span>  
 [<span data-ttu-id="d2b69-135">レッスン 7: 主要業績評価指標 (KPI) の定義</span><span class="sxs-lookup"><span data-stu-id="d2b69-135">Lesson 7: Defining Key Performance Indicators &#40;KPIs&#41;</span></span>](lesson-7-defining-key-performance-indicators-kpis.md)  
  
## <a name="see-also"></a><span data-ttu-id="d2b69-136">参照</span><span class="sxs-lookup"><span data-stu-id="d2b69-136">See Also</span></span>  
 <span data-ttu-id="d2b69-137">[Analysis Services チュートリアルのシナリオ](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="d2b69-137">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="d2b69-138">[Adventure Works チュートリアル &#40;の多次元モデリング&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="d2b69-138">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 <span data-ttu-id="d2b69-139">[名前付きセットの作成](multidimensional-models/create-named-sets.md) </span><span class="sxs-lookup"><span data-stu-id="d2b69-139">[Create Named Sets](multidimensional-models/create-named-sets.md) </span></span>  
 [<span data-ttu-id="d2b69-140">計算されるメンバーの作成</span><span class="sxs-lookup"><span data-stu-id="d2b69-140">Create Calculated Members</span></span>](multidimensional-models/create-calculated-members.md)  
  
  
