---
title: コールセンターデータ用のデータソースビューの追加 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a448e7e4-dbd1-4d31-90bc-4d4a1c23b352
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6d3d9aa3153b39b9ef7f4a92af20e0e8791780bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720570"
---
# <a name="adding-a-data-source-view-for-call-center-data-intermediate-data-mining-tutorial"></a><span data-ttu-id="89416-102">コール センター データ用のデータ ソース ビューの追加 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="89416-102">Adding a Data Source View for Call Center Data (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="89416-103">ここでは、コール センター データへのアクセスに使用するデータ ソース ビューを追加します。</span><span class="sxs-lookup"><span data-stu-id="89416-103">In this task, you add a data source view that will be used to access the call center data.</span></span> <span data-ttu-id="89416-104">最初に調査用のニューラル ネットワーク モデルを構築し、その後、提案作成用のロジスティック回帰モデルを構築します。どちらのモデルにも、同じデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="89416-104">The same data will be used to build both the initial neural network model for exploration, and the logistic regression model that you will use to make recommendations.</span></span>  
  
 <span data-ttu-id="89416-105">さらに、データ ソース ビュー デザイナーを使用して曜日の列を追加します。</span><span class="sxs-lookup"><span data-stu-id="89416-105">You will also use the Data Source View Designer to add a column for the day of the week.</span></span> <span data-ttu-id="89416-106">これは、ソース データによってコール センター データを日付別に追跡していますが、問い合わせ件数とサービス品質にはどちらも、週末か平日かによって定期的なパターンがあることが経験上わかっているためです。</span><span class="sxs-lookup"><span data-stu-id="89416-106">That is because, although the source data tracks call center data by dates, your experience tells you that there are recurring patterns both in terms of call volume and service quality, depending on whether the day is a weekend or a weekday.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="89416-107">手順</span><span class="sxs-lookup"><span data-stu-id="89416-107">Procedures</span></span>  
  
#### <a name="to-add-a-data-source-view"></a><span data-ttu-id="89416-108">データ ソース ビューを追加するには</span><span class="sxs-lookup"><span data-stu-id="89416-108">To add a data source view</span></span>  
  
1.  <span data-ttu-id="89416-109">**ソリューション エクスプローラー**で **[データ ソース ビュー]** を右クリックし、 **[新しいデータ ソース ビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89416-109">In **Solution Explorer**, right-click **Data Source Views**, and select **New Data Source View**.</span></span>  
  
     <span data-ttu-id="89416-110">データ ソース ビュー ウィザードが開きます。</span><span class="sxs-lookup"><span data-stu-id="89416-110">The Data Source View Wizard opens.</span></span>  
  
2.  <span data-ttu-id="89416-111">**[データ ソース ビュー ウィザードへようこそ]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89416-111">On the **Welcome to the Data Source View Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="89416-112">[**データソースの選択**] ページの [**リレーショナルデータソース**] で、 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] データソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="89416-112">On the **Select a Data Source** page, under **Relational data sources**, select the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] data source.</span></span> <span data-ttu-id="89416-113">このデータソースがない場合は、「[基本的なデータマイニングチュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89416-113">If you do not have this data source, see [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md).</span></span> <span data-ttu-id="89416-114">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89416-114">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="89416-115">[**テーブルとビューの選択**] ページで、次のテーブルを選択し、右矢印をクリックしてデータソースビューに追加します。</span><span class="sxs-lookup"><span data-stu-id="89416-115">On the **Select Tables and Views** page, select the following table and then click the right arrow to add it to the data source view:</span></span>  
  
    -   <span data-ttu-id="89416-116">**FactCallCenter (dbo)**</span><span class="sxs-lookup"><span data-stu-id="89416-116">**FactCallCenter (dbo)**</span></span>  
  
    -   <span data-ttu-id="89416-117">**DimDate**</span><span class="sxs-lookup"><span data-stu-id="89416-117">**DimDate**</span></span>  
  
5.  <span data-ttu-id="89416-118">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89416-118">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="89416-119">既定では、[**ウィザードの完了**] ページにはという名前のデータソースビューが [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] あります。</span><span class="sxs-lookup"><span data-stu-id="89416-119">On the **Completing the Wizard** page, by default the data source view is named [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].</span></span> <span data-ttu-id="89416-120">名前を**Callcenter**に変更し、[**完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89416-120">Change the name to **CallCenter**, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="89416-121">データソースビューデザイナーが開き、 **Callcenter**データソースビューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="89416-121">Data Source View Designer opens to display the **CallCenter** data source view.</span></span>  
  
7.  <span data-ttu-id="89416-122">[データソースビュー] ペイン内を右クリックし、[**テーブルの追加と削除**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89416-122">Right-click inside the Data Source View pane, and select **Add/Remove Tables**.</span></span> <span data-ttu-id="89416-123">テーブル**DimDate**を選択し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89416-123">Select the table, **DimDate** and click **OK**.</span></span>  
  
     <span data-ttu-id="89416-124">各テーブルの列の間にリレーションシップが自動的に追加され `DateKey` ます。</span><span class="sxs-lookup"><span data-stu-id="89416-124">A relationship should be automatically added between the `DateKey` columns in each table.</span></span> <span data-ttu-id="89416-125">このリレーションシップを使用して、 **DimDate**テーブルから列**EnglishDayNameOfWeek**を取得し、モデルで使用します。</span><span class="sxs-lookup"><span data-stu-id="89416-125">You will use this relationship to get the column, **EnglishDayNameOfWeek**, from the **DimDate** table and use it in your model.</span></span>  
  
8.  <span data-ttu-id="89416-126">データソースビューデザイナーで、 **FactCallCenter**テーブルを右クリックし、[**新しい名前付き計算**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89416-126">In the Data Source View designer, right-click the table, **FactCallCenter**, and select **New Named Calculation**.</span></span>  
  
     <span data-ttu-id="89416-127">[**名前付き計算の作成**] ダイアログボックスで、次の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="89416-127">In the **Create Named Calculation** dialog box, type the following values:</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="89416-128">**列名**</span><span class="sxs-lookup"><span data-stu-id="89416-128">**Column name**</span></span>|<span data-ttu-id="89416-129">DayOfWeek</span><span class="sxs-lookup"><span data-stu-id="89416-129">DayOfWeek</span></span>|  
    |<span data-ttu-id="89416-130">**説明**</span><span class="sxs-lookup"><span data-stu-id="89416-130">**Description**</span></span>|<span data-ttu-id="89416-131">DimDate テーブルから曜日を取得。</span><span class="sxs-lookup"><span data-stu-id="89416-131">Get day of week from DimDate table</span></span>|  
    |<span data-ttu-id="89416-132">**[式]**</span><span class="sxs-lookup"><span data-stu-id="89416-132">**Expression**</span></span>|`(SELECT EnglishDayNameOfWeek AS DayOfWeek FROM DimDate where FactCallCenter.DateKey = DimDate.DateKey)`|  
  
     <span data-ttu-id="89416-133">式によって必要なデータが作成されることを確認するには、 **FactCallCenter**テーブルを右クリックし、[**データの探索**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="89416-133">To verify that the expression creates the data you need, right-click the table **FactCallCenter**, and then select **Explore Data**.</span></span>  
  
9. <span data-ttu-id="89416-134">データ マイニングでの使用方法を理解するために、使用可能なデータを少し時間をかけて確認します。</span><span class="sxs-lookup"><span data-stu-id="89416-134">Take a minute to review the data that is available, so that you can understand how it is used in data mining:</span></span>  
  
|<span data-ttu-id="89416-135">列名</span><span class="sxs-lookup"><span data-stu-id="89416-135">Column name</span></span>|<span data-ttu-id="89416-136">内容</span><span class="sxs-lookup"><span data-stu-id="89416-136">Contains</span></span>|  
|-----------------|--------------|  
|<span data-ttu-id="89416-137">FactCallCenterID</span><span class="sxs-lookup"><span data-stu-id="89416-137">FactCallCenterID</span></span>|<span data-ttu-id="89416-138">データ ウェアハウスにデータがインポートされたときに作成される任意のキー。</span><span class="sxs-lookup"><span data-stu-id="89416-138">An arbitrary key created when the data was imported to the data warehouse.</span></span><br /><br /> <span data-ttu-id="89416-139">この列は一意のレコードを識別する列で、データ マイニング モデルのケース キーとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="89416-139">This column identifies unique records and should be used as the case key for the data mining model.</span></span>|  
|<span data-ttu-id="89416-140">DateKey</span><span class="sxs-lookup"><span data-stu-id="89416-140">DateKey</span></span>|<span data-ttu-id="89416-141">コール センター業務の日付 (整数値)。</span><span class="sxs-lookup"><span data-stu-id="89416-141">The date of the call center operation, expressed as an integer.</span></span> <span data-ttu-id="89416-142">データ ウェアハウスでは日付のキーに整数がよく使用されますが、日付の値でグループ化する場合は、日付/時刻の形式で日付を取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="89416-142">Integer date keys are often used in data warehouses, but you might want to obtain the date in date/time format if you were going to group by date values.</span></span><br /><br /> <span data-ttu-id="89416-143">ベンダーからは日々、シフトごとに別個のレポートが提供されるため、日付は一意ではありません。</span><span class="sxs-lookup"><span data-stu-id="89416-143">Note that dates are not unique because the vendor provides a separate report for each shift in each day of operation.</span></span>|  
|<span data-ttu-id="89416-144">WageType</span><span class="sxs-lookup"><span data-stu-id="89416-144">WageType</span></span>|<span data-ttu-id="89416-145">曜日が平日、週末、または休日であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="89416-145">Indicates whether the day was a weekday, a weekend, or a holiday.</span></span><br /><br /> <span data-ttu-id="89416-146">週末と平日の顧客サービスの品質に違いがある可能性があるため、この列を入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="89416-146">It is possible that there is a difference in quality of customer service on weekends vs. weekdays so you will use this column as an input.</span></span>|  
|<span data-ttu-id="89416-147">シフト</span><span class="sxs-lookup"><span data-stu-id="89416-147">Shift</span></span>|<span data-ttu-id="89416-148">問い合わせが記録されるシフトを示します。</span><span class="sxs-lookup"><span data-stu-id="89416-148">Indicates the shift for which calls are recorded.</span></span> <span data-ttu-id="89416-149">このコール センターでは、1 日の労働時間が、AM、PM1、PM2、Midnight の 4 つのシフトに分かれています。</span><span class="sxs-lookup"><span data-stu-id="89416-149">This call center divides the working day into four shifts: AM, PM1, PM2, and Midnight.</span></span><br /><br /> <span data-ttu-id="89416-150">カスタマー サービスの質がシフトによって異なる可能性があるため、この列を入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="89416-150">It is possible that the shift influences the quality of customer service so you will use this as an input.</span></span>|  
|<span data-ttu-id="89416-151">LevelOneOperators</span><span class="sxs-lookup"><span data-stu-id="89416-151">LevelOneOperators</span></span>|<span data-ttu-id="89416-152">関税におけるレベル1演算子の数を示します。</span><span class="sxs-lookup"><span data-stu-id="89416-152">Indicates the number of Level 1 operators on duty.</span></span><br /><br /> <span data-ttu-id="89416-153">コール センターの従業員のレベルはレベル 1 から始まるため、このレベルの従業員は経験が浅い従業員です。</span><span class="sxs-lookup"><span data-stu-id="89416-153">Call center employees start at Level 1 so these employees are less experienced.</span></span>|  
|<span data-ttu-id="89416-154">LevelTwoOperators</span><span class="sxs-lookup"><span data-stu-id="89416-154">LevelTwoOperators</span></span>|<span data-ttu-id="89416-155">勤務しているレベル 2 オペレーターの人数を示します。</span><span class="sxs-lookup"><span data-stu-id="89416-155">Indicates the number of Level 2 operators on duty.</span></span><br /><br /> <span data-ttu-id="89416-156">従業員は、レベル2のオペレーターとして限定するために、特定の数のサービス時間をログに記録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89416-156">An employee must log a certain number of service hours to qualify as a Level 2 operator.</span></span>|  
|<span data-ttu-id="89416-157">TotalOperators</span><span class="sxs-lookup"><span data-stu-id="89416-157">TotalOperators</span></span>|<span data-ttu-id="89416-158">シフト中に勤務しているオペレーターの人数の合計。</span><span class="sxs-lookup"><span data-stu-id="89416-158">The total number of operators present during the shift.</span></span>|  
|<span data-ttu-id="89416-159">呼び出し</span><span class="sxs-lookup"><span data-stu-id="89416-159">Calls</span></span>|<span data-ttu-id="89416-160">シフト中に受けた問い合わせの件数。</span><span class="sxs-lookup"><span data-stu-id="89416-160">Number of calls received during the shift.</span></span>|  
|<span data-ttu-id="89416-161">AutomaticResponses</span><span class="sxs-lookup"><span data-stu-id="89416-161">AutomaticResponses</span></span>|<span data-ttu-id="89416-162">完全に自動呼処理 (対話型音声応答、IVR) によって処理された問い合わせの件数。</span><span class="sxs-lookup"><span data-stu-id="89416-162">The number of calls that were handled entirely by automated call processing (Interactive Voice Response, or IVR).</span></span>|  
|<span data-ttu-id="89416-163">Orders</span><span class="sxs-lookup"><span data-stu-id="89416-163">Orders</span></span>|<span data-ttu-id="89416-164">問い合わせの結果として発生した注文の件数。</span><span class="sxs-lookup"><span data-stu-id="89416-164">The number of orders that resulted from calls.</span></span>|  
|<span data-ttu-id="89416-165">IssuesRaised</span><span class="sxs-lookup"><span data-stu-id="89416-165">IssuesRaised</span></span>|<span data-ttu-id="89416-166">問い合わせによって発生した、フォローアップが必要な案件の件数。</span><span class="sxs-lookup"><span data-stu-id="89416-166">The number of issues requiring follow-up that were generated by calls.</span></span>|  
|<span data-ttu-id="89416-167">AverageTimePerIssue</span><span class="sxs-lookup"><span data-stu-id="89416-167">AverageTimePerIssue</span></span>|<span data-ttu-id="89416-168">問い合わせの電話への応対に要した平均時間。</span><span class="sxs-lookup"><span data-stu-id="89416-168">The average time required to respond to an incoming call.</span></span>|  
|<span data-ttu-id="89416-169">ServiceGrade</span><span class="sxs-lookup"><span data-stu-id="89416-169">ServiceGrade</span></span>|<span data-ttu-id="89416-170">サービスの一般品質を示すメトリック。シフト全体の*破棄率*として測定されます。</span><span class="sxs-lookup"><span data-stu-id="89416-170">A metric that indicates the general quality of service, measured as the *abandon rate* for the entire shift.</span></span> <span data-ttu-id="89416-171">電話放棄呼率が高いほど、顧客の満足度が低下し、注文の機会を失う可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="89416-171">The higher the abandon rate, the more likely it is that customers are dissatisfied and that potential orders are being lost.</span></span>|  
  
 <span data-ttu-id="89416-172">データには、1つの日付列 `WageType` (、 **DayOfWeek**、、) に基づく4つの異なる列が含まれていることに注意して `Shift` `DateKey` ください。</span><span class="sxs-lookup"><span data-stu-id="89416-172">Note that the data includes four different columns that are based on a single date column: `WageType`, **DayOfWeek**, `Shift`, and `DateKey`.</span></span> <span data-ttu-id="89416-173">通常、データ マイニングでは、同じデータから派生する列を複数使用することはお勧めしません。それらの値の間の関連が強すぎて、他のパターンがわかりにくくなることがあるからです。</span><span class="sxs-lookup"><span data-stu-id="89416-173">Ordinarily in data mining it is not a good idea to use multiple columns that are derived from the same data, as the values correlate with each other too strongly and can obscure other patterns.</span></span>  
  
 <span data-ttu-id="89416-174">ただし、 `DateKey` 一意の値が多数含まれているため、モデルではを使用しません。</span><span class="sxs-lookup"><span data-stu-id="89416-174">However, we will not use `DateKey` in the model because it contains too many unique values.</span></span> <span data-ttu-id="89416-175">と Dayofweek の間に直接的な関係はありません `Shift` **DayOfWeek** `WageType` 。および**dayofweek**は部分的にのみ関連しています。</span><span class="sxs-lookup"><span data-stu-id="89416-175">There is no direct relationship between `Shift` and **DayOfWeek**, and `WageType` and **DayOfWeek** are only partly related.</span></span> <span data-ttu-id="89416-176">共線性について気にかかる場合は、使用可能なすべての列を使用して構造を作成し、モデルごとに無視する列を変えて影響をテストしてみてください。</span><span class="sxs-lookup"><span data-stu-id="89416-176">If you were worried about collinearity, you could create the structure using all of the available columns, and then ignore different columns in each model and test the effect.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="89416-177">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="89416-177">Next Task in Lesson</span></span>  
 [<span data-ttu-id="89416-178">「中級者向けデータマイニングチュートリアル &#40;ニューラルネットワーク構造とモデルの作成」チュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="89416-178">Creating a Neural Network Structure and Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="89416-179">参照</span><span class="sxs-lookup"><span data-stu-id="89416-179">See Also</span></span>  
 [<span data-ttu-id="89416-180">多次元モデル内のデータ ソース ビュー</span><span class="sxs-lookup"><span data-stu-id="89416-180">Data Source Views in Multidimensional Models</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)  
  
  
