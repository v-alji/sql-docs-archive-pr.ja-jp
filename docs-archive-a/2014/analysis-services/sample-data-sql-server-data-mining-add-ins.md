---
title: サンプルデータ (SQL Server データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- holdout
- testing cases
- training cases
- partitioning data [data mining]
- mining models, testing
ms.assetid: 35907ae6-887f-4cb3-a750-cff3d7683d90
author: minewiskan
ms.author: owend
ms.openlocfilehash: 17da9a42f4d76f5c271d5b225cf897a8ac2e97ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633385"
---
# <a name="sample-data-sql-server-data-mining-add-ins"></a><span data-ttu-id="00d89-102">サンプル データ (SQL Server データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="00d89-102">Sample Data (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="00d89-103">![[データ マイニング] リボンの、データのパーティション分割ウィザード](media/dmc-partition.gif "[データ マイニング] リボンの、データのパーティション分割ウィザード")</span><span class="sxs-lookup"><span data-stu-id="00d89-103">![Partition Data wizard in Data Mining ribbon](media/dmc-partition.gif "Partition Data wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="00d89-104">**サンプルデータ**ウィザードを使用すると、ソースデータを2つのセットに簡単に分割できます。1つはモデルの構築 (トレーニング) 用で、もう1つはモデルのテスト用です。</span><span class="sxs-lookup"><span data-stu-id="00d89-104">The **Sample Data** wizard makes it easy to divide your source data into two sets, one for building (training) the model and one for testing the model.</span></span> <span data-ttu-id="00d89-105">このウィザードでは、ターゲットをより的確に表す新しいデータ セットを作成するために、データをサンプリングし直すこともできます。</span><span class="sxs-lookup"><span data-stu-id="00d89-105">This wizard also provides an option for resampling the data to build a new data set that better represents your target.</span></span>  
  
 <span data-ttu-id="00d89-106">モデルのトレーニングとテストのために適切なデータを作成する作業は、データ マイニングの重要な部分ですが、適切なツールがないと面倒になりがちです。</span><span class="sxs-lookup"><span data-stu-id="00d89-106">Creating the right kind of data for training and testing your models is an important part of data mining, but one that can be tedious without the right tools.</span></span> <span data-ttu-id="00d89-107">ウィザードは、階層化されたサンプリングを実行して、トレーニング セットとテスト セットが均衡化されるようにします。</span><span class="sxs-lookup"><span data-stu-id="00d89-107">The wizard performs stratified sampling to make sure that training and testing sets are well balanced.</span></span>  
  
## <a name="random-sampling-and-oversampling"></a><span data-ttu-id="00d89-108">ランダム サンプリングとオーバーサンプリング</span><span class="sxs-lookup"><span data-stu-id="00d89-108">Random Sampling and Oversampling</span></span>  
 <span data-ttu-id="00d89-109">.</span><span class="sxs-lookup"><span data-stu-id="00d89-109">.</span></span> <span data-ttu-id="00d89-110">モデルのテストに使用するデータが、モデルの作成に使用するデータにほぼ相当するようにする方法としては、ランダム サンプリングが最も適しています。</span><span class="sxs-lookup"><span data-stu-id="00d89-110">Random sampling is the best way to ensure that the data you use for testing a model fairly represents the data that you use for creating the model.</span></span> <span data-ttu-id="00d89-111">Excel または外部データ ソースに格納されているデータを、ランダムにサンプリングすることができます。</span><span class="sxs-lookup"><span data-stu-id="00d89-111">You can randomly sample data that is stored in Excel or in an external data source</span></span>  
  
 <span data-ttu-id="00d89-112">ランダムサンプリングオプションを使用する場合、**サンプルデータ**ウィザードでは、トレーニングデータセットとテストデータセットが自動的に作成され、後で参照できるように別々の Excel ワークシートに出力されます。</span><span class="sxs-lookup"><span data-stu-id="00d89-112">If you use the random sampling option, the **Sample Data** wizard automatically creates training and test data sets and outputs them into separate Excel worksheets for later reference.</span></span>  
  
 <span data-ttu-id="00d89-113">データが外部データソースではなく Excel ブックに格納されている場合は、*オーバーサンプリング*を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="00d89-113">If your data is stored in an Excel workbook, and not an external data source, you also have the option to use *oversampling*.</span></span> <span data-ttu-id="00d89-114">このオプションを使用する場合は、データ内にほとんど出現しないターゲット値を指定します。すると、ウィザードはターゲット値を多く含む均衡化されたセットを収集します。</span><span class="sxs-lookup"><span data-stu-id="00d89-114">With this option, you specify a target value that might be scarce in your data, and the wizard will collect a balanced set that includes more of the target value.</span></span> <span data-ttu-id="00d89-115">目標の割合を達成するか、または一定の行数を作成するように、ウィザードに指示できます。</span><span class="sxs-lookup"><span data-stu-id="00d89-115">You can direct the wizard to achieve a targeted percentage, or to create a certain number of rows.</span></span>  
  
 <span data-ttu-id="00d89-116">オーバーサンプリングオプションを使用した場合、**サンプルデータ**ウィザードでは、新しく均衡が取れたサンプルデータを含む新しいワークシートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="00d89-116">If you use the oversampling option, the **Sample Data** wizard creates a new worksheet that contains the newly balanced sample data.</span></span>  
  
## <a name="using-the-sample-data-wizard"></a><span data-ttu-id="00d89-117">サンプル データ ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="00d89-117">Using the Sample Data Wizard</span></span>  
  
#### <a name="to-separate-data-into-training-and-testing-sets"></a><span data-ttu-id="00d89-118">データをトレーニング セットとテスト セットに分割するには</span><span class="sxs-lookup"><span data-stu-id="00d89-118">To separate data into training and testing sets</span></span>  
  
1.  <span data-ttu-id="00d89-119">[**データマイニング**] リボンで、[**サンプルデータ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="00d89-119">In the **Data Mining** ribbon, click **Sample Data**.</span></span>  
  
2.  <span data-ttu-id="00d89-120">[**ソースデータの選択**] ページで、パーティション分割する**データ**を Excel の範囲またはテーブルに含めるか、外部データソースに含めるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="00d89-120">On the **Select Source Data** page, specify whether the **data** that you want to partition is in an Excel range or table, or in an external data source.</span></span>  
  
3.  <span data-ttu-id="00d89-121">[**サンプリングの種類の選択**] ページで、ランダムサンプリングによってトレーニングデータセットとテストデータセットを作成するか、オーバーサンプリングによって新しいデータセットを作成するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="00d89-121">On the **Select Sampling Type** page, specify whether you want to create training and test data sets by random sampling, or create a new data set by oversampling.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="00d89-122">外部データ ソースを使用する場合は、ランダム サンプリング オプションのみを選択できます。</span><span class="sxs-lookup"><span data-stu-id="00d89-122">If you are using an external data source, only the random sampling option is available.</span></span> <span data-ttu-id="00d89-123">外部データでオーバーサンプリングを使用する場合は、Excel のデータ接続を使用して Excel ブックにデータをインポートしたうえで、サンプル データ ウィザードを使用します。</span><span class="sxs-lookup"><span data-stu-id="00d89-123">If you want to use oversampling with external data, you can import the data to an Excel workbook by using an Excel data connection, and then use the Sample Data wizard.</span></span>  
  
4.  <span data-ttu-id="00d89-124">選択したサンプリング方法固有のオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="00d89-124">Set options specific to the sampling method that you selected.</span></span>  
  
    -   <span data-ttu-id="00d89-125">ランダム サンプリングの場合は、テストに使用する元のデータの割合を指定するか、テスト データ セットで使用する合計行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="00d89-125">For random sampling, specify either a percentage of the original data to use for testing, or the total number of rows to use in the test data set.</span></span>  
  
    -   <span data-ttu-id="00d89-126">オーバーサンプリングの場合は、重点を置く列と値を選択します。</span><span class="sxs-lookup"><span data-stu-id="00d89-126">For oversampling, select the column and value that you want to emphasize.</span></span> <span data-ttu-id="00d89-127">次に、新しいデータ セットの合計行数を指定し、新しいデータ セットでターゲット値を含んでいる必要がある行の割合を指定します。</span><span class="sxs-lookup"><span data-stu-id="00d89-127">Then, specify the total number of rows in the new data set, and the percentage of rows in the new data set that should include the target value.</span></span>  
  
         <span data-ttu-id="00d89-128">オーバーサンプリングのターゲット値は、不連続値でなければなりません。連続する数値データをオーバーサンプリングすることはできません。</span><span class="sxs-lookup"><span data-stu-id="00d89-128">The target value for oversampling must be a discrete value; you cannot oversample continuous numeric data.</span></span>  
  
5.  <span data-ttu-id="00d89-129">[**完了] ページ**で、新しいデータセットの既定の名前をそのまま使用するか、新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="00d89-129">On the **Finish page**, accept the default names for the new data sets, or type a new name.</span></span>  
  
     <span data-ttu-id="00d89-130">ウィザードによって、各データ セット用の新しいワークシートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="00d89-130">The wizard creates new worksheets for each set of data.</span></span>  
  
 <span data-ttu-id="00d89-131">Excel 用のデータ マイニング クライアントのほとんどのウィザードでは、データをトレーニング セットとテスト セットにランダムに分割できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="00d89-131">Most of the wizards in the Data Mining Client for Excel also provide an option to randomly separate your data into training and testing sets.</span></span> <span data-ttu-id="00d89-132">ただし、これらのウィザードを使用した場合は、データが同じワークシート (または他のデータ ソース) にそのまま保持され、特定の行がテスト ケースかトレーニング ケースかを示す情報が内部に格納されます。</span><span class="sxs-lookup"><span data-stu-id="00d89-132">However, if you use the wizards, your data stays in the same worksheet (or other data source), and the information about whether a particular row is a test case or training case is stored internally.</span></span> <span data-ttu-id="00d89-133">これに対し、**サンプルデータ**ウィザードを使用すると、テストデータとトレーニングデータが別々のワークシートに出力され、簡単に参照できるようになります。</span><span class="sxs-lookup"><span data-stu-id="00d89-133">In contrast, when you use the **Sample Data** wizard, the testing and training data are output to separate worksheets for easy reference.</span></span>  
  
## <a name="related-options"></a><span data-ttu-id="00d89-134">関連オプション</span><span class="sxs-lookup"><span data-stu-id="00d89-134">Related Options</span></span>  
 <span data-ttu-id="00d89-135">ウィザードに従って処理するときは、次のオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="00d89-135">As you progress through the wizard, you will have these options:</span></span>  
  
|<span data-ttu-id="00d89-136">Options</span><span class="sxs-lookup"><span data-stu-id="00d89-136">Options</span></span>|<span data-ttu-id="00d89-137">説明</span><span class="sxs-lookup"><span data-stu-id="00d89-137">Comments</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="00d89-138">[ソース データの選択] ダイアログ ボックス (Excel 用のデータ マイニング クライアント)</span><span class="sxs-lookup"><span data-stu-id="00d89-138">Select Source Data Dialog Box (Data Mining Client for Excel)</span></span>|<span data-ttu-id="00d89-139">データが保存されている Excel 範囲またはテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="00d89-139">Select an Excel range or table that contains the data.</span></span> <span data-ttu-id="00d89-140">外部データを使用する場合、リレーショナル データも使用できますが、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のデータ ソースに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="00d89-140">If you want to use external data, the data can be relational, but it must be included in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span> <span data-ttu-id="00d89-141">T</span><span class="sxs-lookup"><span data-stu-id="00d89-141">T</span></span>|  
|<span data-ttu-id="00d89-142">[サンプリングの種類の選択] ページ (Excel 用のデータ マイニング クライアント)</span><span class="sxs-lookup"><span data-stu-id="00d89-142">Select Sampling Type Page (Data Mining Client for Excel)</span></span>|<span data-ttu-id="00d89-143">外部データソースを使用する場合、ランダムサンプリングオプションの使用に制限されます。</span><span class="sxs-lookup"><span data-stu-id="00d89-143">If you use an external data source, you are limited to using the random sampling option.</span></span> <span data-ttu-id="00d89-144">また、[**行数**] オプションを使用して、最終的なデータセットに作成する行の数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00d89-144">Also, you must specify the number of rows to create in the final data set, by using the **Row count** option.</span></span> <span data-ttu-id="00d89-145">ソース データの割合を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="00d89-145">You cannot specify a percentage of the source data.</span></span>|  
|<span data-ttu-id="00d89-146">[ランダム サンプリング] ページ (Excel 用のデータ マイニング クライアント)</span><span class="sxs-lookup"><span data-stu-id="00d89-146">Random Sampling Page (Data Mining Client for Excel)</span></span>|<span data-ttu-id="00d89-147">割合または数を指定して、ソースから行をコピーできます。</span><span class="sxs-lookup"><span data-stu-id="00d89-147">You can copy a percentage of rows from the source, or a specific number of rows.</span></span>|  
|<span data-ttu-id="00d89-148">[オーバーサンプリング] ページ (Excel 用のデータ マイニング クライアント)</span><span class="sxs-lookup"><span data-stu-id="00d89-148">Oversampling Page (Data Mining Client for Excel)</span></span>|<span data-ttu-id="00d89-149">**ターゲットの状態**</span><span class="sxs-lookup"><span data-stu-id="00d89-149">**Target state**</span></span><br /><br /> <span data-ttu-id="00d89-150">元のデータ セットでの出現率が低い値を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="00d89-150">Select a value from the list that is underrepresented in the original data set.</span></span> <span data-ttu-id="00d89-151">オーバーサンプリングによって、この状態を含むデータ行の割合が高くなります。</span><span class="sxs-lookup"><span data-stu-id="00d89-151">Oversampling will increase the proportion of data rows that include this state.</span></span><br /><br /> <span data-ttu-id="00d89-152">**サンプル サイズ**</span><span class="sxs-lookup"><span data-stu-id="00d89-152">**Sample size**</span></span><br /><br /> <span data-ttu-id="00d89-153">抽出する行数の合計を選択します。</span><span class="sxs-lookup"><span data-stu-id="00d89-153">Select the total number of rows to extract.</span></span> <span data-ttu-id="00d89-154">この値は、最終的なデータ セットのサイズを表します。</span><span class="sxs-lookup"><span data-stu-id="00d89-154">This value represents the size of the final data set.</span></span>|  
  
## <a name="other-sampling-options"></a><span data-ttu-id="00d89-155">その他のサンプリング オプション</span><span class="sxs-lookup"><span data-stu-id="00d89-155">Other Sampling Options</span></span>  
 <span data-ttu-id="00d89-156">このウィザードのサンプリング オプションが目的に合わない場合は、SQL Server Integration Services (SSIS) のサンプリング変換を使用して、複数のデータ ソースから行をサンプリングできます。</span><span class="sxs-lookup"><span data-stu-id="00d89-156">If the sampling options in this wizard do not meet your needs, you can use the sampling transformation in SQL Server Integration Services (SSIS) to sample rows from multiple data sources.</span></span>  
  
 <span data-ttu-id="00d89-157">詳細については、「[行サンプリング変換](../integration-services/data-flow/transformations/row-sampling-transformation.md)」および「[比率サンプリング変換](../integration-services/data-flow/transformations/percentage-sampling-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00d89-157">For more information, see [Row Sampling Transformation](../integration-services/data-flow/transformations/row-sampling-transformation.md) and [Percentage Sampling Transformation](../integration-services/data-flow/transformations/percentage-sampling-transformation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d89-158">参照</span><span class="sxs-lookup"><span data-stu-id="00d89-158">See Also</span></span>  
 [<span data-ttu-id="00d89-159">データ マイニングの準備のチェック リスト</span><span class="sxs-lookup"><span data-stu-id="00d89-159">Checklist of Preparation for Data Mining</span></span>](checklist-of-preparation-for-data-mining.md)  
  
  
