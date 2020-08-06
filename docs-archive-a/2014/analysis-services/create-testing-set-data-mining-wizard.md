---
title: テストセットの作成 (データマイニングウィザード)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.holdout.f1
ms.assetid: d0a44b59-ffbd-45fc-baa8-6b8046b1a2f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: ab22597224f5c6c6006a02af81fa6583886d93b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641370"
---
# <a name="create-testing-set-data-mining-wizard"></a><span data-ttu-id="30fcc-102">テスト セットの作成 (データ マイニング ウィザード)</span><span class="sxs-lookup"><span data-stu-id="30fcc-102">Create Testing Set (Data Mining Wizard)</span></span>
  <span data-ttu-id="30fcc-103">**[テスト セットの作成]** ページを使用すると、トレーニングに使用するデータの量、およびテスト セットとして使用するために予約するデータの量を指定できます。</span><span class="sxs-lookup"><span data-stu-id="30fcc-103">Use the **Create Testing Set** page to specify how much of the data is to be used for training, and how much is to be reserved for use as a test set.</span></span> <span data-ttu-id="30fcc-104">マイニング構造を作成する際にデータをトレーニングとテストのセットに分割すると、後で作成するマイニング モデルの精度をより簡単に評価できるようになります。</span><span class="sxs-lookup"><span data-stu-id="30fcc-104">Separating data into a training and testing set when you create a mining structure makes it much easier to assess the accuracy of mining models that you create later.</span></span>  
  
 <span data-ttu-id="30fcc-105">テスト データの量を割合で指定することも、テストに使用するケースの数を制限する数値を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="30fcc-105">You can specify the amount of testing data as a percentage, or you can specify a number to limit the number of cases used for testing.</span></span> <span data-ttu-id="30fcc-106">テストに使用するケースの最大数と割合の両方を指定すると、両方の設定が使用され、テスト データセットには小さい方の数のケースが含められます。</span><span class="sxs-lookup"><span data-stu-id="30fcc-106">If you specify both a percentage and a maximum number of cases to use for testing, both settings are used, and the testing data set contains the smaller number of cases.</span></span> <span data-ttu-id="30fcc-107">既定では、データの 30% がテストに、70% がトレーニングに使用され、テスト ケースの最大数はありません。</span><span class="sxs-lookup"><span data-stu-id="30fcc-107">By default, 30 percent of data is used for testing, 70 percent for training, and there is no maximum number of test cases.</span></span>  
  
 <span data-ttu-id="30fcc-108">既定では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で、パーティション分割の開始に使用される数値シードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="30fcc-108">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] generates a numeric seed that is used to start partitioning.</span></span> <span data-ttu-id="30fcc-109">このシードはマイニング構造の名前に基づきます。</span><span class="sxs-lookup"><span data-stu-id="30fcc-109">This seed is based on the name of the mining structure.</span></span> <span data-ttu-id="30fcc-110">マイニング構造の名前を変更してもパーティションが変わらないようにするには、マイニング構造の HoldoutSeed プロパティを設定してシードの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="30fcc-110">If you want to ensure that the partition stays the same even if the name of the mining structure is changed, you can specify a value for the seed, by setting the HoldoutSeed property of the mining structure.</span></span> <span data-ttu-id="30fcc-111">提示されたシードを変更する場合は、構造を再処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30fcc-111">If you change the holdout seed, you must reprocess the structure.</span></span>  
  
 <span data-ttu-id="30fcc-112">テストデータまたはトレーニングデータの量を後で変更する場合は `HoldoutMaxCases` `HoldoutMaxPercent` 、[**プロパティ**] ウィンドウを使用して、データマイニング構造のプロパティとプロパティを変更できます。</span><span class="sxs-lookup"><span data-stu-id="30fcc-112">If you later want to change the amount of testing or training data, you can modify the `HoldoutMaxCases` and `HoldoutMaxPercent` properties on the data mining structure by using the **Properties** window.</span></span> <span data-ttu-id="30fcc-113">ただし、変更を行った後、マイニング構造および関連するすべてのマイニング モデルを再処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30fcc-113">However, after you make the change you must reprocess the mining structure and all associated mining models.</span></span> <span data-ttu-id="30fcc-114">また、次の制限事項が適用されます。</span><span class="sxs-lookup"><span data-stu-id="30fcc-114">The following limitations also apply:</span></span>  
  
-   <span data-ttu-id="30fcc-115">データ マイニング構造のパーティション分割は、そのデータ マイニング構造が [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]に格納されている場合にのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="30fcc-115">Partitioning of a data mining structure is supported only when the data mining structure is stored in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span> <span data-ttu-id="30fcc-116">以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] では、マイニング構造のパーティション情報のキャッシュはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="30fcc-116">Earlier versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] do not support caching of partition information for mining structures.</span></span>  
  
-   <span data-ttu-id="30fcc-117">タイム シリーズ マイニング モデルに必要な Key Time 列がマイニング構造に含まれている場合、そのマイニング構造をパーティション分割することはできません。</span><span class="sxs-lookup"><span data-stu-id="30fcc-117">You cannot partition a mining structure if the mining structure contains a Key Time column, which is required for time series mining models.</span></span>  
  
-   <span data-ttu-id="30fcc-118">入れ子になったテーブルに格納されている値を予測しようとしている場合、データをパーティション分割することはできません。</span><span class="sxs-lookup"><span data-stu-id="30fcc-118">You cannot partition data if you are trying to predict a value that is stored in a nested table.</span></span>  
  
 <span data-ttu-id="30fcc-119">**詳細情報:** [テストおよび検証 &#40;データ マイニング&#41;](data-mining/testing-and-validation-data-mining.md)、[リレーショナル マイニング構造の作成](data-mining/create-a-relational-mining-structure.md)、[基本的なデータ マイニング チュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md)</span><span class="sxs-lookup"><span data-stu-id="30fcc-119">**For More Information:** [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md), [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="30fcc-120">Options</span><span class="sxs-lookup"><span data-stu-id="30fcc-120">Options</span></span>  
 <span data-ttu-id="30fcc-121">**[テスト用データの割合]**</span><span class="sxs-lookup"><span data-stu-id="30fcc-121">**Percentage of data for testing**</span></span>  
 <span data-ttu-id="30fcc-122">トレーニング セットとして使用するデータの割合を増減するには、上矢印および下矢印をクリックするか、テキスト ボックスに 0 ～ 100 の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="30fcc-122">Click the up and down arrows to increase or decrease the percentage of data to use as a training set, or type a value between 0 and 100 in the text box.</span></span>  
  
 <span data-ttu-id="30fcc-123">**[テスト データセット内のケースの最大数]**</span><span class="sxs-lookup"><span data-stu-id="30fcc-123">**Maximum number of cases in testing data set**</span></span>  
 <span data-ttu-id="30fcc-124">テストに使用できるケースの数を制限する数値を入力します。</span><span class="sxs-lookup"><span data-stu-id="30fcc-124">Type a number to limit the number of cases that can be used for testing.</span></span>  
  
 <span data-ttu-id="30fcc-125">データの実際のケース数よりも大きな数値を指定すると、すべてのケースが使用されます。</span><span class="sxs-lookup"><span data-stu-id="30fcc-125">If you specify a number that is larger than the number of actual cases in the data, all the cases will be used.</span></span>  
  
 <span data-ttu-id="30fcc-126">既定値は NULL です。</span><span class="sxs-lookup"><span data-stu-id="30fcc-126">The default is NULL.</span></span> <span data-ttu-id="30fcc-127">これは制限がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="30fcc-127">This means there is no limit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30fcc-128">参照</span><span class="sxs-lookup"><span data-stu-id="30fcc-128">See Also</span></span>  
 <span data-ttu-id="30fcc-129">[データマイニングウィザードの F1 ヘルプ &#40;Analysis Services データマイニング&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="30fcc-129">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="30fcc-130">[データマイニングウィザード &#40;関連する列の提案&#41;](suggest-related-columns-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="30fcc-130">[Suggest Related Columns &#40;Data Mining Wizard&#41;](suggest-related-columns-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="30fcc-131">[データマイニングウィザード &#40;テーブルの種類の指定&#41;](specify-table-types-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="30fcc-131">[Specify Table Types &#40;Data Mining Wizard&#41;](specify-table-types-data-mining-wizard.md) </span></span>  
 [<span data-ttu-id="30fcc-132">列のコンテンツとデータ型 &#40;データマイニングウィザードを指定し&#41;</span><span class="sxs-lookup"><span data-stu-id="30fcc-132">Specify the Column's Content and Data Type &#40;Data Mining Wizard&#41;</span></span>](specify-the-column-s-content-and-data-type-data-mining-wizard.md)  
  
  
