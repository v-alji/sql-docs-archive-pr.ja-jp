---
title: コールセンターモデルの予測の作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5be0cec7-f639-4eeb-835e-e3204ae619e9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c2d402fb9f6509292442f31f85478b0612a45d56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633713"
---
# <a name="creating-predictions-for-the-call-center-models-intermediate-data-mining-tutorial"></a><span data-ttu-id="83e90-102">コール センター モデルの予測の作成 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="83e90-102">Creating Predictions for the Call Center Models (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="83e90-103">シフト、オペレーターの数、電話、およびサービス グレードの間の相互作用について学習した後は、ビジネス分析および計画に使用できる予測クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="83e90-103">Now that you have learned something about the interactions between shifts, the number of operators, calls, and service grade, you are ready to create some prediction queries that can be used in business analysis and planning.</span></span> <span data-ttu-id="83e90-104">最初に、調査モデルに対していくつかの予測を作成していくつかの仮定をテストします。</span><span class="sxs-lookup"><span data-stu-id="83e90-104">You will first create some predictions on the exploratory model to test some assumptions.</span></span> <span data-ttu-id="83e90-105">次に、ロジスティック回帰モデルを使用して一括予測を作成します。</span><span class="sxs-lookup"><span data-stu-id="83e90-105">Next, you will create bulk predictions by using the logistic regression model.</span></span>  
  
 <span data-ttu-id="83e90-106">このレッスンでは、予測クエリの概念を理解していることを前提にしています。</span><span class="sxs-lookup"><span data-stu-id="83e90-106">This lesson assumes that you are already familiar with the concept of prediction queries.</span></span>  
  
## <a name="creating-predictions-using-the-neural-network-model"></a><span data-ttu-id="83e90-107">ニューラル ネットワーク モデルを使用した予測の作成</span><span class="sxs-lookup"><span data-stu-id="83e90-107">Creating Predictions using the Neural Network Model</span></span>  
 <span data-ttu-id="83e90-108">次の例では、探索用に作成されたニューラル ネットワーク モデルを使用して単一予測を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="83e90-108">The following example demonstrates how to make a singleton prediction using the neural network model that was created for exploration.</span></span> <span data-ttu-id="83e90-109">単一予測は、異なる値を試してモデルでの影響を確認するのに優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="83e90-109">Singleton predictions are a good way to try out different values to see the effect in the model.</span></span> <span data-ttu-id="83e90-110">このシナリオでは、6 人の経験を積んだオペレーターが勤務している場合の深夜シフトのサービス グレードを予測します (曜日は指定しません)。</span><span class="sxs-lookup"><span data-stu-id="83e90-110">In this scenario, you will predict the service grade for the midnight shift (no day of the week specified) if six experienced operators are on duty.</span></span>  
  
#### <a name="to-create-a-singleton-query-by-using-the-neural-network-model"></a><span data-ttu-id="83e90-111">ニューラル ネットワーク モデルを使用して単一クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="83e90-111">To create a singleton query by using the neural network model</span></span>  
  
1.  <span data-ttu-id="83e90-112">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で、使用するモデルが含まれているソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="83e90-112">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution that contains the model that you want to use.</span></span>  
  
2.  <span data-ttu-id="83e90-113">データマイニングデザイナーで、[**マイニングモデル予測**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="83e90-113">In Data Mining Designer, click the **Mining Model Prediction** tab.</span></span>  
  
3.  <span data-ttu-id="83e90-114">[**マイニングモデル**] ペインで、[**モデルの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83e90-114">In the **Mining Model** pane, click **Select Model**.</span></span>  
  
4.  <span data-ttu-id="83e90-115">**[マイニングモデルの選択**] ダイアログボックスには、マイニング構造の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="83e90-115">The **Select Mining Model** dialog box shows a list of mining structures.</span></span> <span data-ttu-id="83e90-116">マイニング構造を展開して、その構造に関連付けられているマイニング モデルの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="83e90-116">Expand the mining structure to view a list of mining models associated with that structure.</span></span>  
  
5.  <span data-ttu-id="83e90-117">マイニング構造 Call Center Default を展開し、Call Center - LR という名前のニューラル ネットワーク モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="83e90-117">Expand the mining structure Call Center Default, and select the neural network model, Call Center - LR.</span></span>  
  
6.  <span data-ttu-id="83e90-118">**[マイニング モデル]** メニューの **[単一クエリ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="83e90-118">From the **Mining Model** menu, select **Singleton Query**.</span></span>  
  
     <span data-ttu-id="83e90-119">[**単一クエリ入力**] ダイアログボックスが表示され、マイニングモデルの列にマップされた列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="83e90-119">The **Singleton Query Input** dialog box appears, with columns mapped to the columns in the mining model.</span></span>  
  
7.  <span data-ttu-id="83e90-120">[**単一クエリ入力**] ダイアログボックスで、[シフト] の行をクリックし、[*深夜*] を選択します。</span><span class="sxs-lookup"><span data-stu-id="83e90-120">In the **Singleton Query Input** dialog box, click the row for Shift, and then select *midnight*.</span></span>  
  
8.  <span data-ttu-id="83e90-121">Lvl 2 演算子の行をクリックし、「」と入力し `6` ます。</span><span class="sxs-lookup"><span data-stu-id="83e90-121">Click the row for Lvl 2 Operators, and type `6`.</span></span>  
  
9. <span data-ttu-id="83e90-122">[**マイニングモデル予測**] タブの下半分で、グリッドの最初の行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83e90-122">In the bottom half of the **Mining Model Prediction** tab, click the first row in the grid.</span></span>  
  
10. <span data-ttu-id="83e90-123">[**基**になる列] で、下矢印をクリックし、[**予測関数**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="83e90-123">In the **Source** column, click the down arrow, and select **Prediction function**.</span></span> <span data-ttu-id="83e90-124">[**フィールド]** 列で、[ **PredictHistogram**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="83e90-124">In the **Field** column, select **PredictHistogram**.</span></span>  
  
     <span data-ttu-id="83e90-125">この予測関数で使用できる引数の一覧は、[**条件と引数**] ボックスに自動的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="83e90-125">A list of arguments that you can use with this prediction function automatically appears in the **Criteria/Arguments** box.</span></span>  
  
11. <span data-ttu-id="83e90-126">[**マイニングモデル**] ペインの列の一覧から servicegrade 列を [**条件と引数**] ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="83e90-126">Drag the ServiceGrade column from the list of columns in the **Mining Model** pane to the **Criteria/Arguments** box.</span></span>  
  
     <span data-ttu-id="83e90-127">列の名前が自動的に引数として挿入されます。</span><span class="sxs-lookup"><span data-stu-id="83e90-127">The name of the column is automatically inserted as the argument.</span></span> <span data-ttu-id="83e90-128">このテキスト ボックスには、任意の予測可能属性の列を選択してドラッグできます。</span><span class="sxs-lookup"><span data-stu-id="83e90-128">You can choose any predictable attribute column to drag into this text box.</span></span>  
  
12. <span data-ttu-id="83e90-129">予測クエリビルダーの上隅にある [**クエリ結果ビューに切り替え**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="83e90-129">Click the button **Switch to query results view**, in the upper corner of the Prediction Query Builder.</span></span>  
  
 <span data-ttu-id="83e90-130">期待される結果には、これらの入力が与えられたときのサービス グレードごとの予測される値と、それぞれの予測に対するサポートおよび確率値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="83e90-130">The expected results contain the possible predicted values for each service grade given these inputs, together with support and probability values for each prediction.</span></span> <span data-ttu-id="83e90-131">いつでもデザイン ビューに戻って入力の変更や追加を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="83e90-131">You can return to design view at any time and change the inputs, or add more inputs.</span></span>  
  
## <a name="creating-predictions-by-using-a-logistic-regression-model"></a><span data-ttu-id="83e90-132">ロジスティック回帰モデルを使用した予測の作成</span><span class="sxs-lookup"><span data-stu-id="83e90-132">Creating Predictions by using a Logistic Regression Model</span></span>  
 <span data-ttu-id="83e90-133">ビジネスの問題に関連する属性がわかっている場合は、ロジスティック回帰モデルを使用して、一部の属性を変更した場合の効果を予測できます。</span><span class="sxs-lookup"><span data-stu-id="83e90-133">If you already know the attributes that are relevant to the business problem, you can use a logistic regression model to predict the effect of making changes in some attributes.</span></span> <span data-ttu-id="83e90-134">ロジスティック回帰は、通常、独立変数の変化に基づいた予測のために使用される統計手法です。たとえば財務スコアリングにおいて、顧客の人口統計に基づいて顧客の行動を予測するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="83e90-134">Logistic regression is a statistical method that is commonly used to make predictions based on changes in independent variables: for example, it is used in financial scoring, to predict customer behavior based on customer demographics.</span></span>  
  
 <span data-ttu-id="83e90-135">ここでは、予測に使用するデータ ソースの作成方法について説明した後、ビジネス上の疑問に回答するのに役立つ予測を作成します。</span><span class="sxs-lookup"><span data-stu-id="83e90-135">In this task, you will learn how to create a data source that will be used for predictions, and then make predictions to help answer several business questions.</span></span>  
  
### <a name="generating-data-used-for-bulk-prediction"></a><span data-ttu-id="83e90-136">一括予測に使用するデータの生成</span><span class="sxs-lookup"><span data-stu-id="83e90-136">Generating Data used for Bulk Prediction</span></span>  
 <span data-ttu-id="83e90-137">入力データを提供する方法はいくつかあります。たとえば、スプレッドシートから人員配置レベルをインポートし、そのデータをモデルで実行して翌月のサービス品質を予測できます。</span><span class="sxs-lookup"><span data-stu-id="83e90-137">There are many ways to provide input data: for example, you might import staffing levels from a spreadsheet, and run that data through the model to predict service quality for the next month.</span></span>  
  
 <span data-ttu-id="83e90-138">このレッスンでは、データ ソース ビュー デザイナーを使用して名前付きクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="83e90-138">In this lesson, you will use the Data Source View designer to create a named query.</span></span> <span data-ttu-id="83e90-139">この名前付きクエリは、スケジュールのシフトごとにスタッフでの最大オペレーター数、受け付けられた問い合わせの最小数、生成された案件の平均数を計算するカスタム Transact-SQL ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="83e90-139">This named query is a custom Transact-SQL statement that for each shift on the schedule calculates the maximum number of operators on staff, the minimum calls received, and the average number of issues that are generated.</span></span> <span data-ttu-id="83e90-140">その後、そのデータをマイニング モデルに結合して、今後の一連の日付についての予測を行います。</span><span class="sxs-lookup"><span data-stu-id="83e90-140">You will then join that data to a mining model to make predictions about a series of upcoming dates.</span></span>  
  
##### <a name="to-generate-input-data-for-a-bulk-prediction-query"></a><span data-ttu-id="83e90-141">一括予測クエリの入力データを生成するには</span><span class="sxs-lookup"><span data-stu-id="83e90-141">To generate input data for a bulk prediction query</span></span>  
  
1.  <span data-ttu-id="83e90-142">ソリューションエクスプローラーで、[**データソースビュー**] を右クリックし、[**新しいデータソースビュー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83e90-142">In Solution Explorer, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="83e90-143">データソースビューウィザードで、データソースとしてを選択し、 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] [**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83e90-143">In the Data Source View wizard, select [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] as the data source, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="83e90-144">[**テーブルとビューの選択**] ページで、テーブルを選択せずに [**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83e90-144">On the **Select Tables and Views** page, click **Next** without selecting any tables.</span></span>  
  
4.  <span data-ttu-id="83e90-145">[**ウィザードの完了**] ページで、名前として「」を入力し `Shifts` ます。</span><span class="sxs-lookup"><span data-stu-id="83e90-145">On the **Completing the Wizard** page, type the name, `Shifts`.</span></span>  
  
     <span data-ttu-id="83e90-146">この名前は、データ ソース ビューの名前としてソリューション エクスプローラーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="83e90-146">This name will appear in Solution Explorer as the name of the data source view.</span></span>  
  
5.  <span data-ttu-id="83e90-147">空のデザインペインを右クリックし、[**新しい名前付きクエリ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="83e90-147">Right-click the empty design pane, then select **New Named Query**.</span></span>  
  
6.  <span data-ttu-id="83e90-148">[名前**付きクエリの作成**] ダイアログボックスの [**名前**] に「」と入力 `Shifts for Call Center` します。</span><span class="sxs-lookup"><span data-stu-id="83e90-148">In the **Create Named Query** dialog box, for **Name**, type `Shifts for Call Center`.</span></span>  
  
     <span data-ttu-id="83e90-149">この名前は、名前付きクエリの名前としてデータ ソース ビュー デザイナーにのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="83e90-149">This name will appear in Data Source View designer only as the name of the named query.</span></span>  
  
7.  <span data-ttu-id="83e90-150">次のクエリ ステートメントを、ダイアログ ボックスの下部の SQL テキスト ペインに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="83e90-150">Paste the following query statement into the SQL text pane in the lower half of the dialog box.</span></span>  
  
    ```  
    SELECT DISTINCT WageType, Shift,   
    AVG(Orders) as AvgOrders, MIN(Orders) as MinOrders, MAX(Orders) as MaxOrders,  
    AVG(Calls) as AvgCalls, MIN(Calls) as MinCalls, MAX(Calls) as MaxCalls,  
    AVG(LevelTwoOperators) as AvgOperators, MIN(LevelTwoOperators) as MinOperators, MAX(LevelTwoOperators) as MaxOperators,  
    AVG(IssuesRaised) as AvgIssues, MIN(IssuesRaised) as MinIssues, MAX(IssuesRaised) as MaxIssues  
    FROM dbo.FactCallCenter  
    GROUP BY Shift, WageType  
    ```  
  
8.  <span data-ttu-id="83e90-151">デザインペインで、テーブルを右クリックし、[コールセンター] の [データの**探索**] を選択して、t-sql クエリによって返されたデータをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="83e90-151">In the design pane, right-click the table, Shifts for Call Center, and select **Explore Data** to preview the data as returned by the T-SQL query.</span></span>  
  
9. <span data-ttu-id="83e90-152">タブを右クリックし、[ **dsv (デザイン)** ] をクリックします。次に、[**保存**] をクリックして、新しいデータソースビューの定義を保存します。</span><span class="sxs-lookup"><span data-stu-id="83e90-152">Right-click the tab, **Shifts.dsv (Design),** and then click **Save** to save the new data source view definition.</span></span>  
  
### <a name="predicting-service-metrics-for-each-shift"></a><span data-ttu-id="83e90-153">各シフトのサービス メトリックスの予測</span><span class="sxs-lookup"><span data-stu-id="83e90-153">Predicting Service Metrics for Each Shift</span></span>  
 <span data-ttu-id="83e90-154">シフトごとの値を生成した後は、作成したロジスティック回帰モデルの入力としてこれらの値を使用して、ビジネス プランニングで使用できる複数の予測を生成します。</span><span class="sxs-lookup"><span data-stu-id="83e90-154">Now that you have generated some values for each shift, you will use those values as input to the logistic regression model that you built, to generate some predictions that can be used in business planning.</span></span>  
  
##### <a name="to-use-the-new-dsv-as-input-to-a-prediction-query"></a><span data-ttu-id="83e90-155">新しい DSV を予測クエリへの入力として使用するには</span><span class="sxs-lookup"><span data-stu-id="83e90-155">To use the new DSV as input to a prediction query</span></span>  
  
1.  <span data-ttu-id="83e90-156">データマイニングデザイナーで、[**マイニングモデル予測**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="83e90-156">In Data Mining Designer, click the **Mining Model Prediction** tab.</span></span>  
  
2.  <span data-ttu-id="83e90-157">[**マイニングモデル**] ペインで、[**モデルの選択**] をクリックし、使用可能なモデルの一覧から [Call Center-LR] を選択します。</span><span class="sxs-lookup"><span data-stu-id="83e90-157">In the **Mining Model** pane, click **Select Model**, and choose Call Center - LR from the list of available models.</span></span>  
  
3.  <span data-ttu-id="83e90-158">[**マイニングモデル**] メニューの [**単一クエリ**] オプションをオフにします。</span><span class="sxs-lookup"><span data-stu-id="83e90-158">From the **Mining Model** menu, clear the option, **Singleton Query**.</span></span> <span data-ttu-id="83e90-159">単一クエリ入力が失われる旨の警告が出力されます。</span><span class="sxs-lookup"><span data-stu-id="83e90-159">A warning tells you that the singleton query inputs will be lost.</span></span> <span data-ttu-id="83e90-160">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83e90-160">Click **OK**.</span></span>  
  
     <span data-ttu-id="83e90-161">[**単一クエリ入力**] ダイアログボックスは、 **[入力テーブルの選択**] ダイアログボックスで置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="83e90-161">The **Singleton Query Input** dialog box is replaced with the **Select Input Table(s)** dialog box.</span></span>  
  
4.  <span data-ttu-id="83e90-162">**[ケース テーブルの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83e90-162">Click **Select Case Table**.</span></span>  
  
5.  <span data-ttu-id="83e90-163">**[テーブルの選択**] ダイアログボックスで、データソースの一覧から [シフト] を選択します。</span><span class="sxs-lookup"><span data-stu-id="83e90-163">In the **Select Table** dialog box, selectShifts from the list of data sources.</span></span> <span data-ttu-id="83e90-164">[**テーブル名またはビュー名**] の一覧で、[コールセンターのシフト (自動的に選択される場合があります)] を選択し、[OK] をクリックし**ます。**</span><span class="sxs-lookup"><span data-stu-id="83e90-164">In the **Table/View name** list, select Shifts for Call Center (it might be automatically selected), and then click **OK.**</span></span>  
  
     <span data-ttu-id="83e90-165">[**マイニングモデル予測**] デザイン画面が更新され、入力データおよびモデルの列の名前とデータ型に基づいて作成されたマッピングが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83e90-165">The **Mining Model Prediction** design surface is updated to show mappings that are created based on the names and data types of columns in the input data and in the model.</span></span>  
  
6.  <span data-ttu-id="83e90-166">結合線の1つを右クリックし、[**接続の変更**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="83e90-166">Right-click one of the join lines, and then select **Modify Connections**.</span></span>  
  
     <span data-ttu-id="83e90-167">このダイアログ ボックスでは、マップされている列とマップされていない列を正確に確認できます。</span><span class="sxs-lookup"><span data-stu-id="83e90-167">In this dialog box, you can see exactly which columns are mapped and which are not.</span></span> <span data-ttu-id="83e90-168">マイニング モデルには、Calls、Orders、IssuesRaised、および LvlTwoOperators の列が含まれています。これらの列は、ソース データ内のこれらの列に基づいて作成した任意の集計にマップできます。</span><span class="sxs-lookup"><span data-stu-id="83e90-168">The mining model contains columns for Calls, Orders, IssuesRaised, and LvlTwoOperators, which you can map to any of the aggregates that you created based on these columns in the source data.</span></span> <span data-ttu-id="83e90-169">このシナリオでは、平均値にマップします。</span><span class="sxs-lookup"><span data-stu-id="83e90-169">In this scenario, you will map to the averages.</span></span>  
  
7.  <span data-ttu-id="83e90-170">[Level2 Operators] の横にある空のセルをクリックし、[ **Call Center. AvgOperators] の [シフト**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="83e90-170">Click the empty cell next to LevelTwoOperators, and select **Shifts for Call Center.AvgOperators**.</span></span>  
  
8.  <span data-ttu-id="83e90-171">[呼び出し] の横にある空のセルをクリックし、[ **Call Center. AvgCalls] の [シフト**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="83e90-171">Click the empty cell next to Calls, select **Shifts for Call Center.AvgCalls**.</span></span> <span data-ttu-id="83e90-172">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83e90-172">and then click **OK**.</span></span>  
  
##### <a name="to-create-the-predictions-for-each-shift"></a><span data-ttu-id="83e90-173">各シフトの予測を作成するには</span><span class="sxs-lookup"><span data-stu-id="83e90-173">To create the predictions for each shift</span></span>  
  
1.  <span data-ttu-id="83e90-174">**予測クエリビルダー**の下半分にあるグリッドで、[**ソース**] の下の空のセルをクリックし、[コールセンターのシフト] を選択します。</span><span class="sxs-lookup"><span data-stu-id="83e90-174">In the grid at the bottom half of the **Prediction Query Builder**, click the empty cell under **Source,** and then select Shifts for Call Center.</span></span>  
  
2.  <span data-ttu-id="83e90-175">[**フィールド**] の下の空のセルで、[Shift] を選択します。</span><span class="sxs-lookup"><span data-stu-id="83e90-175">In the empty cell under **Field**, select Shift.</span></span>  
  
3.  <span data-ttu-id="83e90-176">グリッド内の次の空白行をクリックします。上の手順を繰り返して、WageType の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="83e90-176">Click the next empty line in the grid and repeat the procedure described above to add another row for WageType.</span></span>  
  
4.  <span data-ttu-id="83e90-177">グリッドの次の空白行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83e90-177">Click the next empty line in the grid.</span></span> <span data-ttu-id="83e90-178">[**基**になる列] で、[**予測関数**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="83e90-178">In the **Source** column, select **Prediction Function**.</span></span> <span data-ttu-id="83e90-179">[**フィールド]** 列で [**予測**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="83e90-179">In the **Field** column, select **Predict**.</span></span>  
  
5.  <span data-ttu-id="83e90-180">[**マイニングモデル**] ペインから [servicegrade] 列をグリッドにドラッグし、[**条件と引数**] セルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="83e90-180">Drag the column ServiceGrade from the **Mining Model** pane down to the grid, and into the **Criteria/Argument** cell.</span></span> <span data-ttu-id="83e90-181">[**エイリアス**] フィールドに「予測された**サービスグレード**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="83e90-181">In the **Alias** field, type **Predicted Service Grade**.</span></span>  
  
6.  <span data-ttu-id="83e90-182">グリッドの次の空白行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83e90-182">Click the next empty line in the grid.</span></span> <span data-ttu-id="83e90-183">[**基**になる列] で、[**予測関数**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="83e90-183">In the **Source** column, select **Prediction Function**.</span></span> <span data-ttu-id="83e90-184">[**フィールド]** 列で、[ **predictprobability**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="83e90-184">In the **Field** column, select **PredictProbability**.</span></span>  
  
7.  <span data-ttu-id="83e90-185">[**マイニングモデル**] ペインから [servicegrade] 列をグリッドにドラッグし、[**条件と引数**] セルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="83e90-185">Drag the column ServiceGrade from the **Mining Model** pane down to the grid, and into the **Criteria/Argument** cell.</span></span> <span data-ttu-id="83e90-186">[**エイリアス**] フィールドに「 **Probability**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="83e90-186">In the **Alias** field, type **Probability**.</span></span>  
  
8.  <span data-ttu-id="83e90-187">[**クエリ結果ビューに切り替え**] をクリックすると、予測が表示されます。</span><span class="sxs-lookup"><span data-stu-id="83e90-187">Click **Switch to query result view** to view the predictions.</span></span>  
  
 <span data-ttu-id="83e90-188">次の表に、各シフトのサンプルの結果を示します。</span><span class="sxs-lookup"><span data-stu-id="83e90-188">The following table shows sample results for each shift.</span></span>  
  
|<span data-ttu-id="83e90-189">シフト</span><span class="sxs-lookup"><span data-stu-id="83e90-189">Shift</span></span>|<span data-ttu-id="83e90-190">WageType</span><span class="sxs-lookup"><span data-stu-id="83e90-190">WageType</span></span>|<span data-ttu-id="83e90-191">Predicted Service Grade</span><span class="sxs-lookup"><span data-stu-id="83e90-191">Predicted Service Grade</span></span>|<span data-ttu-id="83e90-192">確率</span><span class="sxs-lookup"><span data-stu-id="83e90-192">Probability</span></span>|  
|-----------|--------------|-----------------------------|-----------------|  
|<span data-ttu-id="83e90-193">AM</span><span class="sxs-lookup"><span data-stu-id="83e90-193">AM</span></span>|<span data-ttu-id="83e90-194">holiday</span><span class="sxs-lookup"><span data-stu-id="83e90-194">holiday</span></span>|<span data-ttu-id="83e90-195">0.165</span><span class="sxs-lookup"><span data-stu-id="83e90-195">0.165</span></span>|<span data-ttu-id="83e90-196">0.377520666</span><span class="sxs-lookup"><span data-stu-id="83e90-196">0.377520666</span></span>|  
|<span data-ttu-id="83e90-197">midnight</span><span class="sxs-lookup"><span data-stu-id="83e90-197">midnight</span></span>|<span data-ttu-id="83e90-198">holiday</span><span class="sxs-lookup"><span data-stu-id="83e90-198">holiday</span></span>|<span data-ttu-id="83e90-199">0.105</span><span class="sxs-lookup"><span data-stu-id="83e90-199">0.105</span></span>|<span data-ttu-id="83e90-200">0.364105573</span><span class="sxs-lookup"><span data-stu-id="83e90-200">0.364105573</span></span>|  
|<span data-ttu-id="83e90-201">PM1</span><span class="sxs-lookup"><span data-stu-id="83e90-201">PM1</span></span>|<span data-ttu-id="83e90-202">holiday</span><span class="sxs-lookup"><span data-stu-id="83e90-202">holiday</span></span>|<span data-ttu-id="83e90-203">0.165</span><span class="sxs-lookup"><span data-stu-id="83e90-203">0.165</span></span>|<span data-ttu-id="83e90-204">0.40056055</span><span class="sxs-lookup"><span data-stu-id="83e90-204">0.40056055</span></span>|  
|<span data-ttu-id="83e90-205">PM2</span><span class="sxs-lookup"><span data-stu-id="83e90-205">PM2</span></span>|<span data-ttu-id="83e90-206">holiday</span><span class="sxs-lookup"><span data-stu-id="83e90-206">holiday</span></span>|<span data-ttu-id="83e90-207">0.165</span><span class="sxs-lookup"><span data-stu-id="83e90-207">0.165</span></span>|<span data-ttu-id="83e90-208">0.338532973</span><span class="sxs-lookup"><span data-stu-id="83e90-208">0.338532973</span></span>|  
|<span data-ttu-id="83e90-209">AM</span><span class="sxs-lookup"><span data-stu-id="83e90-209">AM</span></span>|<span data-ttu-id="83e90-210">weekday</span><span class="sxs-lookup"><span data-stu-id="83e90-210">weekday</span></span>|<span data-ttu-id="83e90-211">0.165</span><span class="sxs-lookup"><span data-stu-id="83e90-211">0.165</span></span>|<span data-ttu-id="83e90-212">0.370847617</span><span class="sxs-lookup"><span data-stu-id="83e90-212">0.370847617</span></span>|  
|<span data-ttu-id="83e90-213">midnight</span><span class="sxs-lookup"><span data-stu-id="83e90-213">midnight</span></span>|<span data-ttu-id="83e90-214">weekday</span><span class="sxs-lookup"><span data-stu-id="83e90-214">weekday</span></span>|<span data-ttu-id="83e90-215">0.08</span><span class="sxs-lookup"><span data-stu-id="83e90-215">0.08</span></span>|<span data-ttu-id="83e90-216">0.352999173</span><span class="sxs-lookup"><span data-stu-id="83e90-216">0.352999173</span></span>|  
|<span data-ttu-id="83e90-217">PM1</span><span class="sxs-lookup"><span data-stu-id="83e90-217">PM1</span></span>|<span data-ttu-id="83e90-218">weekday</span><span class="sxs-lookup"><span data-stu-id="83e90-218">weekday</span></span>|<span data-ttu-id="83e90-219">0.165</span><span class="sxs-lookup"><span data-stu-id="83e90-219">0.165</span></span>|<span data-ttu-id="83e90-220">0.317419177</span><span class="sxs-lookup"><span data-stu-id="83e90-220">0.317419177</span></span>|  
|<span data-ttu-id="83e90-221">PM2</span><span class="sxs-lookup"><span data-stu-id="83e90-221">PM2</span></span>|<span data-ttu-id="83e90-222">weekday</span><span class="sxs-lookup"><span data-stu-id="83e90-222">weekday</span></span>|<span data-ttu-id="83e90-223">0.105</span><span class="sxs-lookup"><span data-stu-id="83e90-223">0.105</span></span>|<span data-ttu-id="83e90-224">0.311672027</span><span class="sxs-lookup"><span data-stu-id="83e90-224">0.311672027</span></span>|  
  
### <a name="predicting-the-effect-of-reduced-response-time-on-service-grade"></a><span data-ttu-id="83e90-225">短縮された応答時間のサービス グレードへの影響の予測</span><span class="sxs-lookup"><span data-stu-id="83e90-225">Predicting the Effect of Reduced Response Time on Service Grade</span></span>  
 <span data-ttu-id="83e90-226">これまで、それぞれのシフトに対してなんらかの平均値を生成し、これらの値をロジスティック回帰モデルへの入力として使用しました。</span><span class="sxs-lookup"><span data-stu-id="83e90-226">You generated some average values for each shift, and used those values as input to the logistic regression model.</span></span> <span data-ttu-id="83e90-227">ただし、電話放棄呼率を 0.00 ～ 0.05 の範囲に抑えるというビジネス目標からすれば、この結果は期待の持てるものではありません。</span><span class="sxs-lookup"><span data-stu-id="83e90-227">However, given that the business objective is to keep abandon rate within the range 0.00-0.05, the results are not encouraging.</span></span>  
  
 <span data-ttu-id="83e90-228">したがって、オペレーション チームは、サービス グレードに対して応答時間が大きく影響することを明らかにした元のモデルに基づいて、問い合わせに対する平均応答時間を短縮した場合にサービス品質が向上するかどうかを評価するための予測を作成することを決定しました。</span><span class="sxs-lookup"><span data-stu-id="83e90-228">Therefore, based on the original model, which showed a strong influence of response time on service grade, the Operations team decides to run some predictions to assess whether reducing the average time for responding to calls might improve service quality.</span></span> <span data-ttu-id="83e90-229">たとえば、問い合わせに対する応答時間を現在の 90% または 80% に短縮した場合、サービス グレードの値はどうなるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="83e90-229">For example, if you cut the call response time to 90 percent or even to 80 percent of the current call response time, what would happen to service grade values?</span></span>  
  
 <span data-ttu-id="83e90-230">各シフトの平均応答時間を計算するデータ ソース ビュー (DSV) を作成して、その平均応答時間の 80% または 90% を計算する列を追加するのは簡単です。</span><span class="sxs-lookup"><span data-stu-id="83e90-230">It is easy to create a data source view (DSV) that calculates the average response times for each shift, and then add columns that calculate 80% or 90% of the average response time.</span></span> <span data-ttu-id="83e90-231">次に、DSV をモデルへの入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="83e90-231">You can then use the DSV as input to the model.</span></span>  
  
 <span data-ttu-id="83e90-232">ここでは詳細な手順は示しませんが、応答時間を現在の応答時間の 80% または 90% に短縮したときのサービス グレードに対する影響の比較を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="83e90-232">Although the exact steps are not shown here, the following table compares the effects on service grade when you reduce response times to 80% or to 90% of current response times.</span></span>  
  
 <span data-ttu-id="83e90-233">これらの結果から、対象のシフトではサービス品質を改善するために現在の割合の 90% に応答時間を短縮する必要があると結論づけることができます。</span><span class="sxs-lookup"><span data-stu-id="83e90-233">From these results, you might conclude that on targeted shifts you should reduce the response time to 90 percent of the current rate in order to improve service quality.</span></span>  
  
|<span data-ttu-id="83e90-234">シフト、賃金、日</span><span class="sxs-lookup"><span data-stu-id="83e90-234">Shift, wage, and day</span></span>|<span data-ttu-id="83e90-235">現在の平均応答時間で予測したサービス品質</span><span class="sxs-lookup"><span data-stu-id="83e90-235">Predicted service quality with current average response time</span></span>|<span data-ttu-id="83e90-236">90% 短縮した応答時間で予測したサービス品質</span><span class="sxs-lookup"><span data-stu-id="83e90-236">Predicted service quality with 90 percent reduction in response time</span></span>|<span data-ttu-id="83e90-237">80% 短縮した応答時間で予測したサービス品質</span><span class="sxs-lookup"><span data-stu-id="83e90-237">Predicted service quality with 80 percent reduction in response time</span></span>|  
|--------------------------|------------------------------------------------------------------|--------------------------------------------------------------------------|--------------------------------------------------------------------------|  
|<span data-ttu-id="83e90-238">休日の午前</span><span class="sxs-lookup"><span data-stu-id="83e90-238">Holiday AM</span></span>|<span data-ttu-id="83e90-239">0.165</span><span class="sxs-lookup"><span data-stu-id="83e90-239">0.165</span></span>|<span data-ttu-id="83e90-240">0.05</span><span class="sxs-lookup"><span data-stu-id="83e90-240">0.05</span></span>|<span data-ttu-id="83e90-241">0.05</span><span class="sxs-lookup"><span data-stu-id="83e90-241">0.05</span></span>|  
|<span data-ttu-id="83e90-242">休日の午後 1</span><span class="sxs-lookup"><span data-stu-id="83e90-242">Holiday PM1</span></span>|<span data-ttu-id="83e90-243">0.05</span><span class="sxs-lookup"><span data-stu-id="83e90-243">0.05</span></span>|<span data-ttu-id="83e90-244">0.05</span><span class="sxs-lookup"><span data-stu-id="83e90-244">0.05</span></span>|<span data-ttu-id="83e90-245">0.05</span><span class="sxs-lookup"><span data-stu-id="83e90-245">0.05</span></span>|  
|<span data-ttu-id="83e90-246">休日の深夜</span><span class="sxs-lookup"><span data-stu-id="83e90-246">Holiday Midnight</span></span>|<span data-ttu-id="83e90-247">0.165</span><span class="sxs-lookup"><span data-stu-id="83e90-247">0.165</span></span>|<span data-ttu-id="83e90-248">0.05</span><span class="sxs-lookup"><span data-stu-id="83e90-248">0.05</span></span>|<span data-ttu-id="83e90-249">0.05</span><span class="sxs-lookup"><span data-stu-id="83e90-249">0.05</span></span>|  
  
 <span data-ttu-id="83e90-250">これ以外にも、このモデルに対してさまざまな予測クエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="83e90-250">There are a variety of other prediction queries that you can create on this model.</span></span> <span data-ttu-id="83e90-251">たとえば、特定のサービスレベルを満たすために必要な演算子の数を予測したり、特定の数の着信呼び出しに応答したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="83e90-251">For example, you could predict how many operators are required to meet a certain service level or to respond to a certain number of incoming calls.</span></span> <span data-ttu-id="83e90-252">ロジスティック回帰モデルには複数の出力を含めることができるため、数多くの別個のモデルを作成する必要なく、異なる独立変数を試してさまざまな結果を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="83e90-252">Because you can include multiple outputs in a logistic regression model, it is easy to experiment with different independent variables and outcomes without having to create many separate models.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83e90-253">解説</span><span class="sxs-lookup"><span data-stu-id="83e90-253">Remarks</span></span>  
 <span data-ttu-id="83e90-254">Excel 2007 用データマイニングアドインにはロジスティック回帰ウィザードが用意されています。これにより、特定のシフトのターゲットレベルへのサービスグレードを向上させるために必要な Level 2 演算子の数など、複雑な質問に簡単に回答できるようになります。</span><span class="sxs-lookup"><span data-stu-id="83e90-254">The Data Mining Add-Ins for Excel 2007 provide logistic regression wizards that make it easy to answer complex questions, such as how many Level Two Operators would be required to improve service grade to a target level for a specific shift.</span></span> <span data-ttu-id="83e90-255">データマイニングアドインは無料でダウンロードでき、ニューラルネットワークまたはロジスティック回帰アルゴリズムに基づいたウィザードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="83e90-255">The data mining add-ins are a free download, and include wizards that are based on the neural network or logistic regression algorithms.</span></span> <span data-ttu-id="83e90-256">詳細については、次のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="83e90-256">For more information, see the following links:</span></span>  
  
-   <span data-ttu-id="83e90-257">[Office 2007 用データマイニングアドインの SQL Server 2005](https://www.microsoft.com/sql/technologies/dm/addins.mspx): ゴールシークと What If シナリオ分析</span><span class="sxs-lookup"><span data-stu-id="83e90-257">[SQL Server 2005 Data Mining Add-Ins for Office 2007](https://www.microsoft.com/sql/technologies/dm/addins.mspx): Goal Seek and What If Scenario Analysis</span></span>  
  
-   <span data-ttu-id="83e90-258">[Office 2007 用の SQL Server 2008 データマイニングアドイン](https://go.microsoft.com/fwlink/?LinkID=117790): ゴールシークシナリオ分析、What If シナリオ分析、および予測計算</span><span class="sxs-lookup"><span data-stu-id="83e90-258">[SQL Server 2008 Data Mining Add-Ins for Office 2007](https://go.microsoft.com/fwlink/?LinkID=117790): Goal Seek Scenario Analysis, What If Scenario Analysis, and Prediction Calculator</span></span>  
  
## <a name="conclusion"></a><span data-ttu-id="83e90-259">まとめ</span><span class="sxs-lookup"><span data-stu-id="83e90-259">Conclusion</span></span>  
 <span data-ttu-id="83e90-260">ここでは、Microsoft ニューラル ネットワーク アルゴリズムおよび Microsoft ロジスティック回帰アルゴリズムに基づいたマイニング モデルを作成、カスタマイズ、および解釈する方法について説明しました。</span><span class="sxs-lookup"><span data-stu-id="83e90-260">You have learned to create, customize, and interpret mining models that are based on the Microsoft Neural Network algorithm and the Microsoft Logistic Regression algorithm.</span></span> <span data-ttu-id="83e90-261">これらの種類のモデルは非常に高度であり、あらゆる分析が可能であるため、複雑であり、習得するのが困難です。</span><span class="sxs-lookup"><span data-stu-id="83e90-261">These model types are sophisticated and permit almost infinite variety in analysis, and therefore can be complex and difficult to master.</span></span>  
  
 <span data-ttu-id="83e90-262">ただし、これらのアルゴリズムは、要素の多くの組み合わせを反復処理して最も強い相関関係を自動的に識別し、Transact-SQL または PowerPivot を使用したデータの手動調査では発見することが非常に困難な考察の統計的サポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="83e90-262">However, these algorithms can iterate through many combinations of factors and automatically identify the strongest correlations, providing statistical support for insights that would be very difficult to discover through manual exploration of data using Transact-SQL or even PowerPivot.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83e90-263">参照</span><span class="sxs-lookup"><span data-stu-id="83e90-263">See Also</span></span>  
 <span data-ttu-id="83e90-264">[ロジスティック回帰モデルのクエリ例](../../2014/analysis-services/data-mining/logistic-regression-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="83e90-264">[Logistic Regression Model Query Examples](../../2014/analysis-services/data-mining/logistic-regression-model-query-examples.md) </span></span>  
 <span data-ttu-id="83e90-265">[Microsoft ロジスティック回帰アルゴリズム](../../2014/analysis-services/data-mining/microsoft-logistic-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="83e90-265">[Microsoft Logistic Regression Algorithm](../../2014/analysis-services/data-mining/microsoft-logistic-regression-algorithm.md) </span></span>  
 <span data-ttu-id="83e90-266">[Microsoft ニューラルネットワークアルゴリズム](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="83e90-266">[Microsoft Neural Network Algorithm](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm.md) </span></span>  
 [<span data-ttu-id="83e90-267">Neural Network Model Query Examples</span><span class="sxs-lookup"><span data-stu-id="83e90-267">Neural Network Model Query Examples</span></span>](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md)  
  
  
