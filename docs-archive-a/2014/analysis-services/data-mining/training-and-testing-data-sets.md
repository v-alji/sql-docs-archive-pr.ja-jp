---
title: データセットのトレーニングとテスト |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- testing mining models
- holdout [data mining]
- testing data mining models
- accuracy testing [data mining]
ms.assetid: 5798fa48-ef3c-4e97-a17c-38274970fccd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4e050a59da542041b9ce825f573625bdb6afc289
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718927"
---
# <a name="training-and-testing-data-sets"></a><span data-ttu-id="0136f-102">トレーニング データ セットとテスト データ セット</span><span class="sxs-lookup"><span data-stu-id="0136f-102">Training and Testing Data Sets</span></span>
  <span data-ttu-id="0136f-103">トレーニング セットとテスト セットにデータを分割することは、データ マイニング モデルの評価における重要な部分です。</span><span class="sxs-lookup"><span data-stu-id="0136f-103">Separating data into training and testing sets is an important part of evaluating data mining models.</span></span> <span data-ttu-id="0136f-104">通常、データセットをトレーニング セットとテスト セットに分割すると、ほとんどのデータはトレーニングに使用され、テストに使用されるデータは少量になります。</span><span class="sxs-lookup"><span data-stu-id="0136f-104">Typically, when you separate a data set into a training set and testing set, most of the data is used for training, and a smaller portion of the data is used for testing.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="0136f-105">ではデータのサンプルがランダムに抽出されるため、テスト セットとトレーニング セットが同様になるように分割されます。</span><span class="sxs-lookup"><span data-stu-id="0136f-105">randomly samples the data to help ensure that the testing and training sets are similar.</span></span> <span data-ttu-id="0136f-106">トレーニングとテストに類似データを使用すると、データの差異による影響を最小限に抑えることができ、モデルの特性をよりよく理解できます。</span><span class="sxs-lookup"><span data-stu-id="0136f-106">By using similar data for training and testing, you can minimize the effects of data discrepancies and better understand the characteristics of the model.</span></span>  
  
 <span data-ttu-id="0136f-107">トレーニング セットを使用してモデルが処理された後、テスト セットに対する予測を実行してモデルをテストします。</span><span class="sxs-lookup"><span data-stu-id="0136f-107">After a model has been processed by using the training set, you test the model by making predictions against the test set.</span></span> <span data-ttu-id="0136f-108">テスト セット内のデータには予測対象の属性の既知の値が既に含まれているため、モデルの推測が正しいかどうかを簡単に判断できます。</span><span class="sxs-lookup"><span data-stu-id="0136f-108">Because the data in the testing set already contains known values for the attribute that you want to predict, it is easy to determine whether the model's guesses are correct.</span></span>  
  
## <a name="creating-test-and-training-sets-for-data-mining-structures"></a><span data-ttu-id="0136f-109">データ マイニング構造のテストとトレーニング セットの作成</span><span class="sxs-lookup"><span data-stu-id="0136f-109">Creating Test and Training Sets for Data Mining Structures</span></span>  
 <span data-ttu-id="0136f-110">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]では、マイニング構造のレベルで元のデータセットを分割します。</span><span class="sxs-lookup"><span data-stu-id="0136f-110">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you separate the original data set at the level of the mining structure.</span></span> <span data-ttu-id="0136f-111">トレーニングとテストのデータセットのサイズ、どの行がどのセットに属するかなどに関する情報は、構造に格納され、その構造に基づくすべてのモデルで、これらのセットを使用してトレーニングとテストを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="0136f-111">The information about the size of the training and testing data sets, and which row belongs to which set, is stored with the structure, and all the models that are based on that structure can use the sets for training and testing.</span></span>  
  
 <span data-ttu-id="0136f-112">マイニング構造のテスト データセットは、次の方法で定義できます。</span><span class="sxs-lookup"><span data-stu-id="0136f-112">You can define a testing data set on a mining structure in the following ways:</span></span>  
  
-   <span data-ttu-id="0136f-113">マイニング構造は、その作成時にデータ マイニング ウィザードを使用して分割します。</span><span class="sxs-lookup"><span data-stu-id="0136f-113">Using the Data Mining Wizard to divide the mining structure when you create it.</span></span>  
  
-   <span data-ttu-id="0136f-114">データ マイニング デザイナーの **[マイニング構造]** タブで、構造のプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="0136f-114">Modifying structure properties in the **Mining Structure** tab of the Data Mining Designer.</span></span>  
  
-   <span data-ttu-id="0136f-115">分析管理オブジェクト (AMO) または XML データ定義言語 (DDL) を使用し、プログラムによって構造を作成および変更します。</span><span class="sxs-lookup"><span data-stu-id="0136f-115">Creating and modifying structures programmatically by using Analysis Management Objects (AMO) or XML Data Definition Language (DDL).</span></span>  
  
### <a name="using-the-data-mining-wizard-to-divide-a-mining-structure"></a><span data-ttu-id="0136f-116">データ マイニング ウィザードを使用したマイニング構造の分割</span><span class="sxs-lookup"><span data-stu-id="0136f-116">Using the Data Mining Wizard to Divide a Mining Structure</span></span>  
 <span data-ttu-id="0136f-117">既定では、マイニング構造のデータ ソースを定義した後、データ マイニング ウィザードによって、ソース データの 70% がモデルのトレーニング用、30% がモデルのテスト用に分割されます。</span><span class="sxs-lookup"><span data-stu-id="0136f-117">By default, after you have defined the data sources for a mining structure, the Data Mining Wizard will divide the data into two sets: one with 70 percent of the source data, for training the model, and one with 30 percent of the source data, for testing the model.</span></span> <span data-ttu-id="0136f-118">この既定設定は、データ マイニングでは 70-30 の比率がよく使用されるために選択されていますが、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、独自の要件に合わせてこの比率を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="0136f-118">This default was chosen because a 70-30 ratio is often used in data mining, but with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] you can change this ratio to suit your requirements.</span></span>  
  
 <span data-ttu-id="0136f-119">また、トレーニング ケースの最大数を設定するようにウィザードを構成したり、指定したケースの最大数まで最大割合を許可するように制限を組み合わせたりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="0136f-119">You can also configure the wizard to set a maximum number of training cases, or you can combine the limits to allow a maximum percentage of cases up to a specified maximum number of cases.</span></span> <span data-ttu-id="0136f-120">ケースの最大割合と最大数の両方を指定した場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって、2 つの制限のうちの小さい方がテスト セットのサイズとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="0136f-120">When you specify both a maximum percentage of cases and a maximum number of cases, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses the smaller of the two limits as the size of the test set.</span></span> <span data-ttu-id="0136f-121">たとえば、テスト ケースに 30% の提示データを指定し、テスト ケースの最大数を 1000 に指定した場合、テスト セットのサイズが 1000 ケースを超えることはありません。</span><span class="sxs-lookup"><span data-stu-id="0136f-121">For example, if you specify 30 percent holdout for the testing cases, and the maximum number of test cases as 1000, the size of the test set will never exceed 1000 cases.</span></span> <span data-ttu-id="0136f-122">これを利用すると、モデルにトレーニング データが追加されてもテスト セットのサイズが一定に保たれるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="0136f-122">This can be useful if you want to ensure that the size of your test set stays consistent even if more training data is added to the model.</span></span>  
  
 <span data-ttu-id="0136f-123">複数のマイニング構造に同じデータ ソース ビューを使用する場合、すべてのマイニング構造とそのモデルでほぼ同じようにデータが分割されるようにするには、ランダム サンプリングの初期化に使用するシードを指定します。</span><span class="sxs-lookup"><span data-stu-id="0136f-123">If you use the same data source view for different mining structures, and want to ensure that the data is divided in roughly the same way for all mining structures and their models, you should specify the seed that is used to initialize random sampling.</span></span> <span data-ttu-id="0136f-124">`HoldoutSeed` の値を指定すると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によるサンプリングの開始時にその値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="0136f-124">When you specify a value for `HoldoutSeed`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will use that value to begin sampling.</span></span> <span data-ttu-id="0136f-125">指定しないと、サンプリング時に、マイニング構造の名前に対してハッシュ アルゴリズムを使用してシード値が作成されます。</span><span class="sxs-lookup"><span data-stu-id="0136f-125">Otherwise, sampling uses a hashing algorithm on the name of the mining structure to create the seed value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0136f-126">`EXPORT` ステートメントおよび `IMPORT` ステートメントを使用してマイニング構造のコピーを作成すると、新しいマイニング構造でも同じトレーニング データセットとテスト データセットが使用されます。エクスポート プロセスでは新しい ID が作成されますが、同じ名前が使用されるためです。</span><span class="sxs-lookup"><span data-stu-id="0136f-126">If you create a copy of the mining structure by using the `EXPORT` and `IMPORT` statements, the new mining structure will have the same training and testing data sets, because the export process creates a new ID but uses the same name.</span></span> <span data-ttu-id="0136f-127">一方、2 つのマイニング構造の基になるデータ ソースが同じでも、名前が異なる場合は、それぞれのマイニング構造に作成されるセットも異なります。</span><span class="sxs-lookup"><span data-stu-id="0136f-127">However, if two mining structures use the same underlying data source but have different names, the sets that are created for each mining structure will be different.</span></span>  
  
### <a name="modifying-structure-properties-to-create-a-test-data-set"></a><span data-ttu-id="0136f-128">テスト データセットの作成のための構造のプロパティの変更</span><span class="sxs-lookup"><span data-stu-id="0136f-128">Modifying Structure Properties to Create a Test Data Set</span></span>  
 <span data-ttu-id="0136f-129">マイニング構造を作成および処理した後にテスト データセットを確保する場合は、マイニング構造のプロパティを変更できます。</span><span class="sxs-lookup"><span data-stu-id="0136f-129">If you create and process a mining structure, and then later decide that you want to set aside a test data set, you can modify the properties of the mining structure.</span></span> <span data-ttu-id="0136f-130">データのパーティション分割方法を変更するには、次のプロパティを編集します。</span><span class="sxs-lookup"><span data-stu-id="0136f-130">To change the way that data is partitioned, edit the following properties:</span></span>  
  
|<span data-ttu-id="0136f-131">プロパティ</span><span class="sxs-lookup"><span data-stu-id="0136f-131">Property</span></span>|<span data-ttu-id="0136f-132">説明</span><span class="sxs-lookup"><span data-stu-id="0136f-132">Description</span></span>|  
|--------------|-----------------|  
|`HoldoutMaxCases`|<span data-ttu-id="0136f-133">テスト セットに含めるケースの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="0136f-133">Specifies the maximum number of cases to include in the testing set.</span></span>|  
|`HoldoutMaxPercent`|<span data-ttu-id="0136f-134">テスト セットに含めるケースの数を、データセット全体に対する割合で指定します。</span><span class="sxs-lookup"><span data-stu-id="0136f-134">Specifies the number of cases to include in the testing set as a percentage of the complete data set.</span></span> <span data-ttu-id="0136f-135">データセットを含めないようにするには、0 を指定します。</span><span class="sxs-lookup"><span data-stu-id="0136f-135">To have no data set, you would specify 0.</span></span>|  
|`HoldoutSeed`|<span data-ttu-id="0136f-136">パーティションのデータをランダムに選択するときにシードとして使用する整数値を指定します。</span><span class="sxs-lookup"><span data-stu-id="0136f-136">Specifies an integer value to use as seed when randomly selecting data for the partitions.</span></span> <span data-ttu-id="0136f-137">この値は、トレーニング セット内のケース数には影響を与えずに、パーティションを反復可能にします。</span><span class="sxs-lookup"><span data-stu-id="0136f-137">This value does not affect the number of cases in the training set; instead, it ensures that the partition can be repeated.</span></span>|  
  
 <span data-ttu-id="0136f-138">既存の構造でテスト データセットを追加または変更した場合、構造および関連するすべてのモデルを再処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0136f-138">If you add or change a test data set to an existing structure, you must reprocess the structure and all associated models.</span></span> <span data-ttu-id="0136f-139">また、ソース データを分割すると、異なるデータ サブセットでモデルがトレーニングされるようになるため、モデルの結果が変化する場合があります。</span><span class="sxs-lookup"><span data-stu-id="0136f-139">Also, because dividing the source data causes the model to be trained on a different subset of the data, you might see different results from your model.</span></span>  
  
### <a name="specifying-holdout-programmatically"></a><span data-ttu-id="0136f-140">プログラムによる HOLDOUT の指定</span><span class="sxs-lookup"><span data-stu-id="0136f-140">Specifying Holdout Programmatically</span></span>  
 <span data-ttu-id="0136f-141">DMX ステートメント、AMO、または XML DDL を使用すると、データ マイニング構造でテスト データセットおよびトレーニング データセットを定義できます。</span><span class="sxs-lookup"><span data-stu-id="0136f-141">You can define testing and training data sets on a mining structure by using DMX statements, AMO, or XML DDL.</span></span> <span data-ttu-id="0136f-142">ALTER MINING STRUCTURE ステートメントは、提示パラメーターの使用をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="0136f-142">The ALTER MINING STRUCTURE statement does not support the use of holdout parameters.</span></span>  
  
-   <span data-ttu-id="0136f-143">**DMX** データ マイニング拡張機能 (DMX) 言語では CREATE MINING STRUCTURE ステートメントが拡張されており、WITH HOLDOUT 句を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0136f-143">**DMX** In the Data Mining Extensions (DMX) language, the CREATE MINING STRUCTURE statement has been extended to include a WITH HOLDOUT clause..</span></span>  
  
-   <span data-ttu-id="0136f-144">**ASSL**[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] スクリプト言語 (ASSL) を使用すると、マイニング構造を新しく作成することも、既存のデータ マイニング構造にテスト データセットを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="0136f-144">**ASSL** You can either create a new mining structure, or add a testing data set to an existing mining structure, by using the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language (ASSL)..</span></span>  
  
-   <span data-ttu-id="0136f-145">**AMO** また、AMO を使用して予約データセットを表示および変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="0136f-145">**AMO** You can also view and modify holdout data sets  by using AMO..</span></span>  
  
 <span data-ttu-id="0136f-146">データ マイニング スキーマ行セットに対してクエリを実行すると、既存のマイニング構造内の予約データセットに関する情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="0136f-146">You can view information about the holdout data set in an existing mining structure by querying the data mining schema rowset.</span></span> <span data-ttu-id="0136f-147">これを行うには、DISCOVER ROWSET を呼び出すか、DMX クエリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0136f-147">You can do this by making a DISCOVER ROWSET call, or you can use a DMX query.</span></span>  
  
## <a name="retrieving-information-about-holdout-data"></a><span data-ttu-id="0136f-148">予約データに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="0136f-148">Retrieving Information about Holdout Data</span></span>  
 <span data-ttu-id="0136f-149">既定では、トレーニング データセットとテスト データセットに関する情報はすべてキャッシュされるので、既存のデータを使用して新しいモデルをトレーニングし、テストできます。</span><span class="sxs-lookup"><span data-stu-id="0136f-149">By default, all information about the training and test data sets is cached, so that you can use existing data to train and then test new models.</span></span> <span data-ttu-id="0136f-150">データのサブセットに対してモデルを評価できるように、キャッシュ済みの予約データに適用するフィルターをユーザーが定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="0136f-150">You can also define filters to apply to the cached holdout data so that you can evaluate the model on subsets of the data.</span></span>  
  
 <span data-ttu-id="0136f-151">ケースがどのようにトレーニング データセットおよびテスト データセットに分割されるかは、予約データの構成方法、および指定したデータによって異なります。</span><span class="sxs-lookup"><span data-stu-id="0136f-151">The way that cases are divided into training and testing data sets depends on the way that you configure holdout, and the data that you provide.</span></span> <span data-ttu-id="0136f-152">トレーニングまたはテストに使用されるケース数を確認する場合、またはトレーニング セットとテスト セットに含まれているケースの詳細を調べる場合は、DMX クエリを作成してモデル構造でクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="0136f-152">If you want to determine the number of cases used for training or for testing, or if you want to find additional details about the cases included in the training and test sets, you can query the model structure by creating a DMX query.</span></span> <span data-ttu-id="0136f-153">たとえば、次のクエリでは、モデルのトレーニング セットで使用されたケースが返されます。</span><span class="sxs-lookup"><span data-stu-id="0136f-153">For example, the following query returns the cases that were used in the training set of the model.</span></span>  
  
```  
SELECT * from <structure>.CASES WHERE IsTrainingCase()  
```  
  
 <span data-ttu-id="0136f-154">テスト ケースのみを取得し、さらにマイニング構造内のいずれかの列でテスト ケースをフィルター処理するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="0136f-154">To retrieve only the test cases, and additionally filter the test cases on one of the columns in the mining structure, use the following syntax:</span></span>  
  
```  
SELECT * from <structure>.CASES WHERE IsTestCase() AND <structure column name> = '<value>'  
```  
  
## <a name="limitations-on-the-use-of-holdout-data"></a><span data-ttu-id="0136f-155">予約データの使用に関する制限事項</span><span class="sxs-lookup"><span data-stu-id="0136f-155">Limitations on the Use of Holdout Data</span></span>  
  
-   <span data-ttu-id="0136f-156">提示データを使用するには、マイニング構造の <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> プロパティが既定値の `KeepTrainingCases` に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0136f-156">To use holdout, the <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> property of the mining structure must be set to the default value, `KeepTrainingCases`.</span></span> <span data-ttu-id="0136f-157">`CacheMode` プロパティを `ClearAfterProcessing` に変更してマイニング構造を再処理すると、パーティションが失われます。</span><span class="sxs-lookup"><span data-stu-id="0136f-157">If you change the `CacheMode` property to `ClearAfterProcessing`, and then reprocess the mining structure, the partition will be lost.</span></span>  
  
-   <span data-ttu-id="0136f-158">タイム シリーズ モデルからデータを削除することはできません。したがって、ソース データをトレーニング セットとテスト セットに分割することはできません。</span><span class="sxs-lookup"><span data-stu-id="0136f-158">You cannot remove data from a time series model; therefore, you cannot separate the source data into training and testing sets.</span></span> <span data-ttu-id="0136f-159">マイニング構造とモデルの作成を開始し、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] タイム シリーズ アルゴリズムを選択すると、予約データセットを作成するオプションは無効になります。</span><span class="sxs-lookup"><span data-stu-id="0136f-159">If you begin to create a mining structure and model and choose the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series algorithm, the option to create a holdout data set is disabled.</span></span> <span data-ttu-id="0136f-160">また、ケース テーブル レベルまたは入れ子になったテーブル レベルで、マイニング構造に KEY TIME 列が含まれている場合も、予約データの使用が無効になります。</span><span class="sxs-lookup"><span data-stu-id="0136f-160">Use of holdout data is also disabled if the mining structure contains a KEY TIME column at either the case or nested table level.</span></span>  
  
-   <span data-ttu-id="0136f-161">データセット全体がテストに使用され、トレーニング用のデータが残らなくなるように予約データセットが誤って構成されることもあります。</span><span class="sxs-lookup"><span data-stu-id="0136f-161">It is possible to inadvertently configure the holdout data set such that the complete data set is used for testing, and no data remains for training.</span></span> <span data-ttu-id="0136f-162">ただし、この問題を修正できるように、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によりエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="0136f-162">However, if you do so, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will raise an error so that you can correct the problem.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="0136f-163">により警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0136f-163">also warns you when the structure is processed if more than 50 percent of the data has been held out for testing.</span></span>  
  
-   <span data-ttu-id="0136f-164">多くの場合、提示データの既定値である 30 を使用すると、トレーニング データとテスト データのバランスがとれます。</span><span class="sxs-lookup"><span data-stu-id="0136f-164">In most cases, the default holdout value of 30 provides a good balance between training and testing data.</span></span> <span data-ttu-id="0136f-165">十分なトレーニングのためにデータセットをどの程度大きくするか、また、オーバーフィットを回避するためにトレーニング セットをどの程度小さくするかを、単純に算出する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="0136f-165">There is no simple way to determine how large the data set should be to provide sufficient training, or how sparse the training set can be and still avoid overfitting.</span></span> <span data-ttu-id="0136f-166">ただし、モデルを作成した後、クロス検証を使用して、特定のモデルについてデータセットを評価できます。</span><span class="sxs-lookup"><span data-stu-id="0136f-166">However, after you have built a model, you can use cross-validation to assess the data set with respect to a particular model.</span></span>  
  
-   <span data-ttu-id="0136f-167">AMO と XML DDL には、前の表に示したプロパティに加えて、読み取り専用プロパティ `HoldoutActualSize` が用意されています。</span><span class="sxs-lookup"><span data-stu-id="0136f-167">In addition to the properties listed in the previous table, a read-only property, `HoldoutActualSize`, is provided in AMO and XML DDL.</span></span> <span data-ttu-id="0136f-168">ただし、構造が処理されるまではパーティションの実際のサイズを正確に知ることができないため、`HoldoutActualSize` プロパティの値を取得する前に、モデルが処理済みであるかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0136f-168">However, because the actual size of a partition cannot be determined accurately until after the structure has been processed, you should check whether the model has been processed before you retrieve the value of the `HoldoutActualSize` property.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="0136f-169">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="0136f-169">Related Content</span></span>  
  
|<span data-ttu-id="0136f-170">トピック</span><span class="sxs-lookup"><span data-stu-id="0136f-170">Topics</span></span>|<span data-ttu-id="0136f-171">リンク</span><span class="sxs-lookup"><span data-stu-id="0136f-171">Links</span></span>|  
|------------|-----------|  
|<span data-ttu-id="0136f-172">モデルに対するフィルターとトレーニング データセットおよびテスト データセットとの間の対話方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0136f-172">Describes how filters on a model interact with training and testing data sets.</span></span>|[<span data-ttu-id="0136f-173">マイニング モデルのフィルター &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="0136f-173">Filters for Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-models-analysis-services-data-mining.md)|  
|<span data-ttu-id="0136f-174">トレーニング データとテスト データの使用が相互検証に与える影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="0136f-174">Describes how the use of training and testing data affects cross-validation.</span></span>|[<span data-ttu-id="0136f-175">相互検証 &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="0136f-175">Cross-Validation &#40;Analysis Services - Data Mining&#41;</span></span>](cross-validation-analysis-services-data-mining.md)|  
|<span data-ttu-id="0136f-176">マイニング構造でのトレーニング セットとテスト セットの操作のためのプログラム インターフェイスに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="0136f-176">Provides information on the programmatic interfaces for working with training and testing sets in a mining structure.</span></span>|[<span data-ttu-id="0136f-177">AMO の概念とオブジェクトモデル</span><span class="sxs-lookup"><span data-stu-id="0136f-177">AMO Concepts and Object Model</span></span>](https://docs.microsoft.com/bi-reference/amo/amo-concepts-and-object-model)<br /><br /> [<span data-ttu-id="0136f-178">MiningStructure 要素 (ASSL)</span><span class="sxs-lookup"><span data-stu-id="0136f-178">MiningStructure Element &#40;ASSL&#41;</span></span>](https://docs.microsoft.com/bi-reference/assl/objects/miningstructure-element-assl)|  
|<span data-ttu-id="0136f-179">提示セットを作成するための DMX 構文について説明します。</span><span class="sxs-lookup"><span data-stu-id="0136f-179">Provides DMX syntax for creating holdout sets.</span></span>|[<span data-ttu-id="0136f-180">CREATE MINING STRUCTURE (DMX)</span><span class="sxs-lookup"><span data-stu-id="0136f-180">CREATE MINING STRUCTURE &#40;DMX&#41;</span></span>](/sql/dmx/create-mining-structure-dmx)|  
|<span data-ttu-id="0136f-181">トレーニング セットとテスト セットのケースに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="0136f-181">Retrieve information about cases in the training and testing sets.</span></span>|[<span data-ttu-id="0136f-182">データ マイニング スキーマ行セット</span><span class="sxs-lookup"><span data-stu-id="0136f-182">Data Mining Schema Rowsets</span></span>](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)<br /><br /> [<span data-ttu-id="0136f-183">データマイニングスキーマ行セットのクエリ &#40;Analysis Services-データマイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="0136f-183">Querying the Data Mining Schema Rowsets &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining-schema-rowsets-ssas.md)|  
  
## <a name="see-also"></a><span data-ttu-id="0136f-184">参照</span><span class="sxs-lookup"><span data-stu-id="0136f-184">See Also</span></span>  
 <span data-ttu-id="0136f-185">[データマイニングツール](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="0136f-185">[Data Mining Tools](data-mining-tools.md) </span></span>  
 <span data-ttu-id="0136f-186">[データマイニングの概念](data-mining-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="0136f-186">[Data Mining Concepts](data-mining-concepts.md) </span></span>  
 <span data-ttu-id="0136f-187">[データマイニングソリューション](data-mining-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="0136f-187">[Data Mining Solutions](data-mining-solutions.md) </span></span>  
 [<span data-ttu-id="0136f-188">テストおよび検証 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="0136f-188">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)  
  
  