---
title: 予測構造とモデルの作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5f55cbf6-0db4-4cb4-a0f5-e27441873d4f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d77b15a9a8efe9a9c6faec49a2274ee182706992
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711209"
---
# <a name="creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="7ffa7-102">Forecasting 構造およびモデルの作成 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="7ffa7-102">Creating a Forecasting Structure and Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="7ffa7-103">次に、データ マイニング ウィザードを使用して、先ほど作成したデータ ソース ビューに基づく新しいマイニング構造とマイニング モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-103">Next, you will use the Data Mining Wizard to create a new mining structure and mining model based on the data source view that you just created.</span></span> <span data-ttu-id="7ffa7-104">この作業では、マイニング モデルで [!INCLUDE[msCoName](../includes/msconame-md.md)] タイム シリーズ アルゴリズムが使用されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-104">In this task you will specify that the mining model should use the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm.</span></span>  
  
### <a name="to-create-a-forecasting-mining-structure"></a><span data-ttu-id="7ffa7-105">予測マイニング構造を作成するには</span><span class="sxs-lookup"><span data-stu-id="7ffa7-105">To create a forecasting mining structure</span></span>  
  
1.  <span data-ttu-id="7ffa7-106">のソリューションエクスプローラーで [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 、[**マイニング構造**] を右クリックし、[**新しいマイニング構造**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-106">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], right-click **Mining Structures** and select **New Mining Structure**.</span></span>  
  
2.  <span data-ttu-id="7ffa7-107">**[データ マイニング ウィザードへようこそ]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-107">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="7ffa7-108">[**定義方法の選択**] ページで、[**既存のリレーショナルデータベースまたはデータウェアハウスから**] が選択されていることを確認し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-108">On the **Select the Definition Method** page, verify that **From existing relational database or data warehouse** is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="7ffa7-109">[**データマイニング構造の作成**] ページの [**使用するデータマイニング技法を指定**してください] で、[ **Microsoft タイムシリーズ**] を選択し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-109">On the **Create the Data Mining Structure** page, under **Which data mining technique do you want to use?**, select **Microsoft Time Series**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="7ffa7-110">[**データソースビューの選択**] ページの [**使用できるデータソースビュー**] で、[ **salesbyregion**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-110">On the **Select Data Source View** page, under **Available data source views**, select **SalesByRegion**.</span></span>  
  
6.  <span data-ttu-id="7ffa7-111">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-111">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="7ffa7-112">[**テーブルの種類の指定**] ページで、vTimeSeries テーブルの [**ケース**] 列のチェックボックスがオンになっていることを確認し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-112">On the **Specify Table Types** page, ensure that the check box in the **Case** column for the vTimeSeries table is selected, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="7ffa7-113">[**トレーニングデータの指定**] ページで、modelregion 列と reportingdate 列の [**キー** ] 列のチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-113">On the **Specify the Training Data** page, select the check boxes in the **Key** column for the ModelRegion and ReportingDate columns.</span></span>  
  
     <span data-ttu-id="7ffa7-114">ReportingDate は既定でオンになります。これは、データ ソース ビューを作成したときに、この列を論理主キーとして指定したためです。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-114">ReportingDate should be selected by default, because you specified this column as the logical primary key when you created the data source view.</span></span> <span data-ttu-id="7ffa7-115">ModelRegion を 2 つ目のキーとして追加することで、このフィールドに表示されるモデルと領域の組み合わせごとに別々の時系列を作成するようにアルゴリズムに指示します。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-115">By adding ModelRegion as a second key, you are telling the algorithm to create a separate time series for each combination of model and region listed in this field.</span></span>  
  
9. <span data-ttu-id="7ffa7-116">Quantity 列の**入力**列と**予測可能**列のチェックボックスをオンにし、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-116">Select the check boxes in the **Input** and **Predictable** columns for the Quantity, column, and then click **Next**.</span></span>  
  
     <span data-ttu-id="7ffa7-117">[**予測可能**] を選択すると、この列のデータに対して予測を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-117">By selecting **Predictable**, you indicate that you want to create forecasts on the data in this column.</span></span> <span data-ttu-id="7ffa7-118">ただし、過去のデータに基づく予測にする必要があるため、列を入力として追加する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-118">However, because you want to base the forecasts on past data, you must also add the column as an input.</span></span>  
  
10. <span data-ttu-id="7ffa7-119">[列の**コンテンツおよびデータ型の指定**] ページで、選択内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-119">On the page **Specify Columns' Content and Data Type**, review the selections.</span></span>  
  
     <span data-ttu-id="7ffa7-120">ModelRegion 列は**キー**列として指定され、reportingdate 列は自動的に**key Time**列として指定されます。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-120">The ModelRegion column is designated as a **Key** column and the ReportingDate column is automatically designated as a **Key Time** column.</span></span> <span data-ttu-id="7ffa7-121">キーの種類ごとにキーを 1 つだけ指定できます。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-121">You can have only one of each type of key.</span></span>  
  
11. <span data-ttu-id="7ffa7-122">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-122">Click **Next**.</span></span>  
  
12. <span data-ttu-id="7ffa7-123">[**ウィザードの完了**] ページで、[**マイニング構造名**] に「」と入力 `Forecasting` します。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-123">On the **Completing the Wizard** page, for **Mining structure name**, type `Forecasting`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7ffa7-124">時系列モデルでは、ドリルスルーを有効にするオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-124">The option to enable drillthrough is not available for time series models.</span></span>  
  
13. <span data-ttu-id="7ffa7-125">[**マイニングモデル名**] に「」と入力し、[ `Forecasting` **完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-125">In **Mining model name**, type `Forecasting`, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="7ffa7-126">データマイニングデザイナーが開き、作成した `Forecasting` マイニング構造が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ffa7-126">Data Mining Designer opens to display the `Forecasting` mining structure that you just created.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="7ffa7-127">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="7ffa7-127">Next Task in Lesson</span></span>  
 [<span data-ttu-id="7ffa7-128">中間データマイニングチュートリアル &#40;予測構造の変更&#41;</span><span class="sxs-lookup"><span data-stu-id="7ffa7-128">Modifying the Forecasting Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/modifying-the-forecasting-structure-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="7ffa7-129">参照</span><span class="sxs-lookup"><span data-stu-id="7ffa7-129">See Also</span></span>  
 <span data-ttu-id="7ffa7-130">[データマイニングデザイナー](../../2014/analysis-services/data-mining/data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="7ffa7-130">[Data Mining Designer](../../2014/analysis-services/data-mining/data-mining-designer.md) </span></span>  
 [<span data-ttu-id="7ffa7-131">Microsoft Time Series アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="7ffa7-131">Microsoft Time Series Algorithm</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
