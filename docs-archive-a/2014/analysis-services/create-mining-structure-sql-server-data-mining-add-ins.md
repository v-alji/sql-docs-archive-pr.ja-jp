---
title: マイニング構造の作成 (SQL Server データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures, creating
ms.assetid: b8b1eedc-4d6d-4429-a578-e629ec573934
author: minewiskan
ms.author: owend
ms.openlocfilehash: c75712a893c6271da291693f46771aa71263280e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634743"
---
# <a name="create-mining-structure-sql-server-data-mining-add-ins"></a><span data-ttu-id="32613-102">マイニング構造の作成 (SQL Server データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="32613-102">Create Mining Structure (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="32613-103">![[データ マイニング] リボンの [マイニング構造の作成] ボタン](media/dmc-createstruct.gif "[データ マイニング] リボンの [マイニング構造の作成] ボタン")</span><span class="sxs-lookup"><span data-stu-id="32613-103">![Create Mining Structure button, Data Mining ribbon](media/dmc-createstruct.gif "Create Mining Structure button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="32613-104">モデルを作成することなく、分析に使用するデータセットを作成する場合は、**データモデリング**グループの **[詳細**設定] オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="32613-104">Use the **Advanced** option in the **Data Modeling** group when you want to create a data set used for analysis without necessarily creating a model.</span></span> <span data-ttu-id="32613-105">この方法は、さまざまなアルゴリズムをテストする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="32613-105">This is useful when you want to experiment with different algorithms.</span></span>  
  
 <span data-ttu-id="32613-106">マイニング構造を作成したら、[[構造へのモデルの追加](add-model-to-structure-data-mining-add-ins-for-excel.md)] ウィザードを使用して、その構造に基づくモデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="32613-106">After you have created the mining structure, use the [Add Model to Structure](add-model-to-structure-data-mining-add-ins-for-excel.md) wizard to create a model based on that structure.</span></span> <span data-ttu-id="32613-107">**データマイニング詳細クエリエディター**を使用して、新しいモデルを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="32613-107">You can also create new models by using the **Data Mining Advanced Query Editor**.</span></span>  
  
 <span data-ttu-id="32613-108">また、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] でサポートされているがウィザードでは使用できない、線形回帰、シーケンス クラスターなどの高度なアルゴリズムやカスタム アルゴリズムを使用してモデルを作成する場合に、このオプションを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="32613-108">You can also use this option when you intend to build models using one of the advanced algorithms, which are supported by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] but not available through a wizard, such as linear regression or sequence clustering, or if you are using a custom algorithm.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="32613-109">マイニング構造を作成すると、すべてのモデルの検証に使用できる、ランダムに選択されるテスト データを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="32613-109">When you create the mining structure, you can also establish a randomly selected testing data set that you can use to validate all your models.</span></span> <span data-ttu-id="32613-110">この方法は、共通のデータセットに対するモデルの精度を簡単に比較できるため便利です。</span><span class="sxs-lookup"><span data-stu-id="32613-110">This is handy because you can easily compare model accuracy against a common data set.</span></span> <span data-ttu-id="32613-111">オプションを選択し、**データをトレーニングセットとテストセットに分割**し、テスト用に予約するデータの適切な割合を指定します。通常は約30% です。</span><span class="sxs-lookup"><span data-stu-id="32613-111">Just select the option, **Split data into training and testing sets** and specify an appropriate percentage of data to reserve for testing, usually around 30 percent.</span></span>  
  
## <a name="use-the-wizard-to-create-a-mining-structure"></a><span data-ttu-id="32613-112">ウィザードを使用したマイニング構造の作成</span><span class="sxs-lookup"><span data-stu-id="32613-112">Use the wizard to create a mining structure</span></span>  
  
1.  <span data-ttu-id="32613-113">[**データマイニング**] リボンで、[**詳細設定**] をクリックし、[**構造の作成**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="32613-113">In the **Data Mining** ribbon, click **Advanced**, and select **Create Structure**.</span></span>  
  
2.  <span data-ttu-id="32613-114">**[ソースデータの選択**] ダイアログボックスで、分析に使用するデータが含まれている excel 範囲、excel データテーブル、または外部データソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="32613-114">In the **Select source data** dialog box, specify the Excel range, Excel data table, or external data source that contains the data you want to use for analysis.</span></span>  
  
     <span data-ttu-id="32613-115">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="32613-115">Click **Next**.</span></span>  
  
3.  <span data-ttu-id="32613-116">**[列の選択**] ダイアログボックスで、選択したデータソースで使用可能な列の一覧を確認します。</span><span class="sxs-lookup"><span data-stu-id="32613-116">In the **Select Columns** dialog box, review the list of columns available in the selected data source.</span></span>  
  
4.  <span data-ttu-id="32613-117">列名の右側にある矢印をクリックして、列の**使用法**を変更し、次の値から選択します。</span><span class="sxs-lookup"><span data-stu-id="32613-117">Click the arrow to the right of the column name to change the **usage** of the column, choosing from these values:</span></span>  
  
    -   <span data-ttu-id="32613-118">**[キー]**</span><span class="sxs-lookup"><span data-stu-id="32613-118">**Key**.</span></span> <span data-ttu-id="32613-119">各モデルに少なくとも 1 つのキーが必要です。</span><span class="sxs-lookup"><span data-stu-id="32613-119">At least one key is required for each model.</span></span>  
  
    -   <span data-ttu-id="32613-120">**キー時刻**。</span><span class="sxs-lookup"><span data-stu-id="32613-120">**Key time**.</span></span> <span data-ttu-id="32613-121">このオプションは、予測モデルが必要な場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="32613-121">This option is available only for forecasting models, where it is required.</span></span>  
  
    -   <span data-ttu-id="32613-122">を**含め**ます。</span><span class="sxs-lookup"><span data-stu-id="32613-122">**Include**.</span></span> <span data-ttu-id="32613-123">列をマイニング構造で使用できるが、キー列ではありません。</span><span class="sxs-lookup"><span data-stu-id="32613-123">Indicates that the column should be made available in the mining structure but is not a key column.</span></span>  
  
    -   <span data-ttu-id="32613-124">**使用しないで**ください。</span><span class="sxs-lookup"><span data-stu-id="32613-124">**Do not use**.</span></span> <span data-ttu-id="32613-125">列はマイニング構造に含まれません。</span><span class="sxs-lookup"><span data-stu-id="32613-125">Indicates that the column should not be included in the mining structure.</span></span>  
  
     <span data-ttu-id="32613-126">モデルを作成する際はいつでも列を無視できますが、後で列を追加するには、構造とモデルを再処理する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="32613-126">Remember that you can always ignore columns when you build the model, but to add columns later requires that you reprocess the structure and model.</span></span>  
  
5.  <span data-ttu-id="32613-127">参照ボタン ([. **..])** をクリックして、コンテンツの種類、データ型、およびモデリングフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="32613-127">Click the browse **(...)** button to set the content type, data type, and modeling flags.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="32613-128">列に数値データが含まれている場合は、必ずこのダイアログ ボックスを開いて、正しいデータ型が選択されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="32613-128">If the column contains numeric data, you should always open this dialog box to ensure that the correct data type is chosen.</span></span> <span data-ttu-id="32613-129">入力データが数値であっても、カテゴリ変数として処理したり、連続する数値ではなく不連続値として処理する場合があります。</span><span class="sxs-lookup"><span data-stu-id="32613-129">In some cases, even if the input data is a number, you will want to treat it as a categorical variable, or discrete value, instead of a continuous number.</span></span>  
    >   
    >  <span data-ttu-id="32613-130">たとえば、郵便番号列は既定では連続する long データ型として一覧表示されますが、より良い結果を得るために、不連続のテキスト値として処理するように指定することができます。</span><span class="sxs-lookup"><span data-stu-id="32613-130">For example, a postal code column might be listed by default as a continuous long data type, but to get better results, you can specify that it be handled as a discrete text value.</span></span>  
    >   
    >  <span data-ttu-id="32613-131">詳細については、「[データマイニング用のデータの選択](choosing-data-for-data-mining.md)」のコンテンツの種類に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="32613-131">For more information, see the section on content types in [Choosing Data for Data Mining](choosing-data-for-data-mining.md).</span></span>  
  
     <span data-ttu-id="32613-132">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="32613-132">Click **OK** to close the dialog box.</span></span>  
  
6.  <span data-ttu-id="32613-133">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="32613-133">Click **Next**.</span></span>  
  
     <span data-ttu-id="32613-134">使用するデータ型に応じて、この手順を行った後にウィザードを完了することもできます。</span><span class="sxs-lookup"><span data-stu-id="32613-134">Depending on what type of data you are using, you might complete the wizard after this step.</span></span> <span data-ttu-id="32613-135">その場合は、 **[完了**] ページに移動して、マイニング構造に名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="32613-135">In that case, jump ahead to the **Finish** page to name your mining structure.</span></span>  
  
     <span data-ttu-id="32613-136">その他のモデルの場合は、追加のオプションを選択してテスト データ セットを作成します。</span><span class="sxs-lookup"><span data-stu-id="32613-136">For other models, you have the additional option to create a testing data set.</span></span>  
  
7.  <span data-ttu-id="32613-137">[データを**トレーニングおよびテストデータセットに分割**] ダイアログボックスで、データをパーティション分割する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="32613-137">In the **Split data into training and testing data sets** dialog box, specify how you want your data partitioned.</span></span> <span data-ttu-id="32613-138">既定では、データの 30% がテストに使用されます。</span><span class="sxs-lookup"><span data-stu-id="32613-138">By default, 30 percent of data is used for testing.</span></span>  
  
     <span data-ttu-id="32613-139">必要に応じて、テストに使用する最大行数を入力します。</span><span class="sxs-lookup"><span data-stu-id="32613-139">Optionally, type the maximum number of rows to use for testing.</span></span>  
  
     <span data-ttu-id="32613-140">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="32613-140">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="32613-141">**[完了**] ダイアログボックスで、新しいマイニング構造の名前と説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="32613-141">In the **Finish** dialog, type a name and description for the new mining structure.</span></span>  
  
9. <span data-ttu-id="32613-142">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="32613-142">Click **Finish**.</span></span>  
  
### <a name="related-options"></a><span data-ttu-id="32613-143">関連オプション</span><span class="sxs-lookup"><span data-stu-id="32613-143">Related Options</span></span>  
  
|<span data-ttu-id="32613-144">オプション</span><span class="sxs-lookup"><span data-stu-id="32613-144">Option</span></span>|<span data-ttu-id="32613-145">説明</span><span class="sxs-lookup"><span data-stu-id="32613-145">Comments</span></span>|  
|------------|--------------|  
|<span data-ttu-id="32613-146">**[ソースデータの選択**] ダイアログボックス</span><span class="sxs-lookup"><span data-stu-id="32613-146">**Select Source Data** dialog box</span></span>|<span data-ttu-id="32613-147">Excel テーブルを選択したとき、データに既にヘッダーがあるかどうかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32613-147">When you select an Excel table, you should indicate whether the data already has headers.</span></span> <span data-ttu-id="32613-148">これを省略した場合、データの最初の行は列名として使用されます。</span><span class="sxs-lookup"><span data-stu-id="32613-148">If you skip this, the first row of data will be used as the column name.</span></span><br /><br /> <span data-ttu-id="32613-149">[**外部データソース**] オプションを使用すると、データソースで定義できる任意の種類のデータを使用でき [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="32613-149">If you use the option, **External data source**, you can use any kind of data that can be defined in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span> <span data-ttu-id="32613-150">ただし、新しいデータ ソースを作成するためのアドインのダイアログ ボックスには、Analysis Services でサポートされているデータ ソースの一部が表示されないため、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーでデータ ソースを事前に作成してから、アドインを使用して接続することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="32613-150">However, the dialog box in the add-in for creating new data sources does not include the full range of data sources supported by Analysis Services, so we recommend that you create the data sources on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server in advance and then connect using the add-ins.</span></span>|  
|<span data-ttu-id="32613-151">[**データソースクエリエディター** ] ダイアログボックス</span><span class="sxs-lookup"><span data-stu-id="32613-151">**Data Source Query Editor** dialog box</span></span>|<span data-ttu-id="32613-152">指定したデータ ソースに接続した後、列を追加したり、カスタム クエリを作成してカスタム列を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="32613-152">After you have connected to the specified data source, you can add columns, or create a custom query to generate custom columns.</span></span>|  
|<span data-ttu-id="32613-153">**[データをトレーニング データ セットとテスト データ セットに分割]**</span><span class="sxs-lookup"><span data-stu-id="32613-153">**Split data into training and testing data sets**</span></span>|<span data-ttu-id="32613-154">トレーニングセットとテストセットの推奨値は、トレーニングの場合は70%、テストの場合は30% です。ただし、大量のデータがある場合は、テストの最大行数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="32613-154">A recommended value for training vs. testing sets is 70 percent for training and 30 percent for testing; however, if you have a lot of data, you can specify a maximum number of rows for testing.</span></span>|  
|<span data-ttu-id="32613-155">[完了] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="32613-155">Finish dialog box</span></span>|<span data-ttu-id="32613-156">ドリルスルーのオプションは一部のモデルの種類で使用できます。特に、マイニング構造に詳細列が含まれる場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="32613-156">The options for drillthrough are available on some model types and are very useful if you included detail columns in your mining structure.</span></span> <span data-ttu-id="32613-157">たとえば、クラスター モデルを作成した場合、特定のクラスター内の顧客に簡単に連絡できるように、分析ではなく、ドリルスルー用に名前や電子メール アドレスなどの詳細を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="32613-157">For example, if you create a clustering model, you can include details such as name or email address for drillthrough but not analysis, to make it easier to contact customers in a particular cluster.</span></span>|  
  
###  <a name="setting-column-usage-in-the-create-mining-structure-wizard"></a><a name="Bkmk_strctcolumn"></a><span data-ttu-id="32613-158">マイニング構造の作成ウィザードでの列の使用法の設定</span><span class="sxs-lookup"><span data-stu-id="32613-158">Setting Column Usage in the Create Mining Structure Wizard</span></span>  
 <span data-ttu-id="32613-159">新しいマイニング構造を作成する場合は、データ ソースのどの列をマイニング構造に含めるかと、それらの列の使用方法を指定できます。</span><span class="sxs-lookup"><span data-stu-id="32613-159">When you create a new mining structure, you can specify which columns in the data source should be included in the mining structure, and how those columns should be used.</span></span> <span data-ttu-id="32613-160">1 つのマイニング構造には、複数のマイニング モデルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="32613-160">Remember that a mining structure can support multiple mining models.</span></span>  
  
|<span data-ttu-id="32613-161">値</span><span class="sxs-lookup"><span data-stu-id="32613-161">Values</span></span>|<span data-ttu-id="32613-162">説明</span><span class="sxs-lookup"><span data-stu-id="32613-162">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="32613-163">**包含**</span><span class="sxs-lookup"><span data-stu-id="32613-163">**Include**</span></span>|<span data-ttu-id="32613-164">列に格納されているデータは、分析または予測に使用されます。</span><span class="sxs-lookup"><span data-stu-id="32613-164">Specifies that the column contains data that can be used for analysis or prediction.</span></span>|  
|<span data-ttu-id="32613-165">**[キー]**</span><span class="sxs-lookup"><span data-stu-id="32613-165">**Key**</span></span>|<span data-ttu-id="32613-166">列にトランザクション ID、系列 ID など、処理に必要なキーが格納されていることを表します。</span><span class="sxs-lookup"><span data-stu-id="32613-166">Specifies that the column contains a transaction ID, a series ID, or another key required for processing.</span></span><br /><br /> <span data-ttu-id="32613-167">すべてのアルゴリズムには、Key 列が必要です。</span><span class="sxs-lookup"><span data-stu-id="32613-167">All algorithms require a Key column.</span></span> <span data-ttu-id="32613-168">ただし、キーが 1 つのみ許可されるアルゴリズムと複数のキーが許可されるアルゴリズムがあります。</span><span class="sxs-lookup"><span data-stu-id="32613-168">However, some algorithms permit only a single key, while others permit multiple keys.</span></span><br /><br /> <span data-ttu-id="32613-169">列にキーが含まれていても処理に必要ない場合は、[**使用**しない] を選択します。</span><span class="sxs-lookup"><span data-stu-id="32613-169">If the column contains a key but is not required for processing, select **Do Not Use**.</span></span>|  
|<span data-ttu-id="32613-170">**[キー時刻]**</span><span class="sxs-lookup"><span data-stu-id="32613-170">**Key Time**</span></span>|<span data-ttu-id="32613-171">タイム シリーズのアイテムを一意に識別するために使用できる日付などの数値が列に格納されていることを表します。</span><span class="sxs-lookup"><span data-stu-id="32613-171">Specifies that the column contains a date or other numeric value that can be used to uniquely identify items in a time series.</span></span>|  
|<span data-ttu-id="32613-172">**使用しない**</span><span class="sxs-lookup"><span data-stu-id="32613-172">**Do Not Use**</span></span>|<span data-ttu-id="32613-173">列が無視されます。</span><span class="sxs-lookup"><span data-stu-id="32613-173">Specifies that the column should be ignored.</span></span> <span data-ttu-id="32613-174">列のデータは処理されません。</span><span class="sxs-lookup"><span data-stu-id="32613-174">The data in the column will not be processed.</span></span>|  
  
 <span data-ttu-id="32613-175">モデルを正しく処理するには、各行を一意に識別するキー列はどれなのか、予測可能モデルを作成する場合に予測を作成するための対象列はどれなのか、および対象列を予測するリレーションシップを作成するために入力列として使用する列はどれなのかをアルゴリズムに理解させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="32613-175">To process a model correctly, the algorithm must know which column is the key column that uniquely identifies each row, which column is the target column for creating predictions if you are creating a predictable model, and which columns to use as input columns to create the relationships that predict the target column.</span></span>  
  
-   <span data-ttu-id="32613-176">**使用**しないように指定されている列は、マイニング構造には存在しません。</span><span class="sxs-lookup"><span data-stu-id="32613-176">Columns that are specified as **Do not use** will not be present in the mining structure.</span></span>  
  
     <span data-ttu-id="32613-177">不要な列や不適切な値を含む列を追加すると、分析の結果に悪影響を及ぼす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="32613-177">If you add columns that are unnecessary or have bad values, it can adversely affect the results of analysis.</span></span> <span data-ttu-id="32613-178">そのため、適切な列だけを含めるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="32613-178">Therefore, be sure to include only those columns that are relevant.</span></span> <span data-ttu-id="32613-179">ただし、マイニング構造で使用しない列は、クエリに使用できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="32613-179">However, remember that the columns that you do not use in the mining structure will not be available for querying.</span></span>  
  
-   <span data-ttu-id="32613-180">**Include**型として指定された列は、マイニング構造に含まれ、後でマイニングモデルの分析または予測に使用できます。</span><span class="sxs-lookup"><span data-stu-id="32613-180">Columns that are specified as the **Include** type will be included in the mining structure and later can be used for either analysis or prediction in the mining models.</span></span>  
  
     <span data-ttu-id="32613-181">列を使用する必要があるかどうか不明な場合は、その列をマイニング構造に含めておき、後でその列を使用しないマイニング モデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="32613-181">If you are not sure whether you will need to use the column, you can always include the column in the mining structure and then create a mining model that does not use that column.</span></span> <span data-ttu-id="32613-182">たとえば、後で参照できるように電話番号列をデータに含めたものの、電話番号を無視するクラスター モデルを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="32613-182">For example, you might include a phone number column in your data for later reference, but create a clustering model that ignores phone numbers.</span></span> <span data-ttu-id="32613-183">クラスターが作成された後、特定のクラスターに属する人の電話番号を返すクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="32613-183">After the clusters have been created, you can create a query that returns the phone numbers of people who belong to a particular cluster.</span></span>  
  
-   <span data-ttu-id="32613-184">すべてのアルゴリズムに**キー**列が必要です。</span><span class="sxs-lookup"><span data-stu-id="32613-184">All algorithms require a **Key** column.</span></span> <span data-ttu-id="32613-185">Key 列の値は一意でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="32613-185">The values in the Key column must be unique.</span></span> <span data-ttu-id="32613-186">**Key time**列は、予測またはタイムシリーズモデルに対してのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="32613-186">A **Key Time** column is required only for forecasting or time series models.</span></span> <span data-ttu-id="32613-187">.</span><span class="sxs-lookup"><span data-stu-id="32613-187">.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="32613-188">必要条件</span><span class="sxs-lookup"><span data-stu-id="32613-188">Requirements</span></span>  
 <span data-ttu-id="32613-189">データ マイニング構造を作成するには、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32613-189">To create a data mining structure, you must have a connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="32613-190">一時的な構造を操作する場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="32613-190">A connection is required even if you are working with temporary structures.</span></span> <span data-ttu-id="32613-191">接続を作成または変更する方法の詳細については、「 [Connect To Source data &#40;Excel 用データマイニングクライアント&#41;](connect-to-source-data-data-mining-client-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32613-191">For more information about how to create or change a connection, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32613-192">参照</span><span class="sxs-lookup"><span data-stu-id="32613-192">See Also</span></span>  
 [<span data-ttu-id="32613-193">データ マイニング モデルの作成</span><span class="sxs-lookup"><span data-stu-id="32613-193">Creating a Data Mining Model</span></span>](creating-a-data-mining-model.md)  
  
  
