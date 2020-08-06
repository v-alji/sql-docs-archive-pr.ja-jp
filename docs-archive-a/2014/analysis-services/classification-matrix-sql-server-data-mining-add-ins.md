---
title: 分類マトリックス (SQL Server データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- classification matrix
- confusion table
- mining models, testing
ms.assetid: d6f620f4-39af-4714-9628-28ce3c361fca
author: minewiskan
ms.author: owend
ms.openlocfilehash: a930f2628ac41fc5886cf41d7ec0ad274b42bf2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633530"
---
# <a name="classification-matrix-sql-server-data-mining-add-ins"></a><span data-ttu-id="80bb0-102">分類マトリックス (SQL Server データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="80bb0-102">Classification Matrix (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="80bb0-103">![[データ マイニング] リボンの [分類マトリックス] ボタン](media/dmc-cmatrix.gif "[データ マイニング] リボンの [分類マトリックス] ボタン")</span><span class="sxs-lookup"><span data-stu-id="80bb0-103">![Classification Matrix button, Data Mining ribbon](media/dmc-cmatrix.gif "Classification Matrix button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="80bb0-104">分類マトリックスを使用すると、予測で使用するモデルの精度を評価できます。</span><span class="sxs-lookup"><span data-stu-id="80bb0-104">You can use the classification matrix to assess the accuracy of a model for prediction.</span></span> <span data-ttu-id="80bb0-105">分類マトリックスを生成するには、モデルでテスト データのセットを実行し、分類マトリックス ツールを使用してテスト セットの実際の値とモデルで予測した値を比較します。</span><span class="sxs-lookup"><span data-stu-id="80bb0-105">To generate a classification matrix, you run a set of testing data through the model, and the classification matrix tool compares the actual values from the testing set against the predictions made by the model.</span></span> <span data-ttu-id="80bb0-106">マトリックスを確認すると、モデルが正しい頻度とモデルの予測が間違っている頻度がひとめでわかります。</span><span class="sxs-lookup"><span data-stu-id="80bb0-106">By looking at the matrix, you can tell at a glance how often the model is correct, and how often it predicts wrongly.</span></span>  
  
 <span data-ttu-id="80bb0-107">これらのアドインでは、**分類マトリックス**ウィザードを使用してモデルを選択し、テストデータを指定して、結果行列を生成します。</span><span class="sxs-lookup"><span data-stu-id="80bb0-107">In these add-ins, use the **Classification Matrix** wizard to select a model, specify the testing data, and then generate a results matrix.</span></span>  
  
## <a name="how-to-read-a-classification-matrix"></a><span data-ttu-id="80bb0-108">分類マトリックスの見方</span><span class="sxs-lookup"><span data-stu-id="80bb0-108">How to Read a Classification Matrix</span></span>  
 <span data-ttu-id="80bb0-109">目標として、顧客ロイヤルティプログラムを設計し、顧客を適切なカテゴリに割り当てて、適切なレベルのインセンティブを提供できるようにします。</span><span class="sxs-lookup"><span data-stu-id="80bb0-109">Let's assume your objective is to design a customer loyalty program and then assign customers to appropriate categories, so that you can provide them with the appropriate level of incentives.</span></span> <span data-ttu-id="80bb0-110">報酬プログラムに対して3つのレベル (ブロンズ、シルバー、ゴールド) を実装し、評価段階で顧客に提供しました。</span><span class="sxs-lookup"><span data-stu-id="80bb0-110">You have implemented three levels for the reward program -- bronze, silver, and gold - and given these out to customers in a trial phase.</span></span> <span data-ttu-id="80bb0-111">また、顧客を分析し、適切なカテゴリを予測するモデルも設計しました。</span><span class="sxs-lookup"><span data-stu-id="80bb0-111">You have also designed a model that analyzes customers and predicts the correct categories.</span></span> <span data-ttu-id="80bb0-112">これで、試用データで分類マトリックスを使用して、すべての顧客について適切な提供内容を予測する時点でモデルがどの程度適切であったかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="80bb0-112">Now you will use the classification matrix on the trial data to determine how good the model was at predicting the correct offer for all customers.</span></span>  
  
 <span data-ttu-id="80bb0-113">分類マトリックスのテーブルから、モデルに基づいて各カテゴリに何人の顧客が割り当てられるかを確認し、その結果を各報酬レベルに実際に応募した顧客の人数と比較することができます。</span><span class="sxs-lookup"><span data-stu-id="80bb0-113">The table from the classification matrix tells you how many customers would be assigned to each category based on the model, and compares that result to the number of customers who actually signed up for each reward level.</span></span>  
  
||<span data-ttu-id="80bb0-114">ブロンズ (実際)</span><span class="sxs-lookup"><span data-stu-id="80bb0-114">Bronze (Actual)</span></span>|<span data-ttu-id="80bb0-115">ゴールド (実際)</span><span class="sxs-lookup"><span data-stu-id="80bb0-115">Gold (Actual)</span></span>|<span data-ttu-id="80bb0-116">シルバー (実際)</span><span class="sxs-lookup"><span data-stu-id="80bb0-116">Silver (Actual)</span></span>|  
|-|-----------------------|---------------------|-----------------------|  
|<span data-ttu-id="80bb0-117">ブロンズ</span><span class="sxs-lookup"><span data-stu-id="80bb0-117">Bronze</span></span>|<span data-ttu-id="80bb0-118">**94.45%**</span><span class="sxs-lookup"><span data-stu-id="80bb0-118">**94.45%**</span></span>|<span data-ttu-id="80bb0-119">15.18%</span><span class="sxs-lookup"><span data-stu-id="80bb0-119">15.18%</span></span>|<span data-ttu-id="80bb0-120">1.70%</span><span class="sxs-lookup"><span data-stu-id="80bb0-120">1.70%</span></span>|  
|<span data-ttu-id="80bb0-121">ゴールド</span><span class="sxs-lookup"><span data-stu-id="80bb0-121">Gold</span></span>|<span data-ttu-id="80bb0-122">2.72%</span><span class="sxs-lookup"><span data-stu-id="80bb0-122">2.72%</span></span>|<span data-ttu-id="80bb0-123">**84.82%**</span><span class="sxs-lookup"><span data-stu-id="80bb0-123">**84.82%**</span></span>|<span data-ttu-id="80bb0-124">0.00%</span><span class="sxs-lookup"><span data-stu-id="80bb0-124">0.00%</span></span>|  
|<span data-ttu-id="80bb0-125">シルバー</span><span class="sxs-lookup"><span data-stu-id="80bb0-125">Silver</span></span>|<span data-ttu-id="80bb0-126">1.84%</span><span class="sxs-lookup"><span data-stu-id="80bb0-126">1.84%</span></span>|<span data-ttu-id="80bb0-127">0.00%</span><span class="sxs-lookup"><span data-stu-id="80bb0-127">0.00%</span></span>|<span data-ttu-id="80bb0-128">**93.80%**</span><span class="sxs-lookup"><span data-stu-id="80bb0-128">**93.80%**</span></span>|  
|<span data-ttu-id="80bb0-129">*そうです*</span><span class="sxs-lookup"><span data-stu-id="80bb0-129">*Correct*</span></span>|<span data-ttu-id="80bb0-130">*95.45%*</span><span class="sxs-lookup"><span data-stu-id="80bb0-130">*95.45%*</span></span>|<span data-ttu-id="80bb0-131">*84.82%*</span><span class="sxs-lookup"><span data-stu-id="80bb0-131">*84.82%*</span></span>|<span data-ttu-id="80bb0-132">*98.30%*</span><span class="sxs-lookup"><span data-stu-id="80bb0-132">*98.30%*</span></span>|  
|<span data-ttu-id="80bb0-133">*分類ミス*</span><span class="sxs-lookup"><span data-stu-id="80bb0-133">*Misclassified*</span></span>|<span data-ttu-id="80bb0-134">*4.55%*</span><span class="sxs-lookup"><span data-stu-id="80bb0-134">*4.55%*</span></span>|<span data-ttu-id="80bb0-135">*15.18%*</span><span class="sxs-lookup"><span data-stu-id="80bb0-135">*15.18%*</span></span>|<span data-ttu-id="80bb0-136">*1.70%*</span><span class="sxs-lookup"><span data-stu-id="80bb0-136">*1.70%*</span></span>|  
  
-   <span data-ttu-id="80bb0-137">各列は、テスト データセット内の実際の値を示しています。</span><span class="sxs-lookup"><span data-stu-id="80bb0-137">Each column shows the actual values in the testing dataset.</span></span>  
  
-   <span data-ttu-id="80bb0-138">各行は、予測値を示しています。</span><span class="sxs-lookup"><span data-stu-id="80bb0-138">Each row shows the predicted values.</span></span>  
  
-   <span data-ttu-id="80bb0-139">マトリックスの左上から右下まで斜めに並んでいる太字の値は、モデルが正しく予測したことを示しています。</span><span class="sxs-lookup"><span data-stu-id="80bb0-139">The values in boldface, which run diagonally from the upper-left corner to the lower-right corner of the matrix, give you the picture of what the model got right.</span></span>  
  
-   <span data-ttu-id="80bb0-140">この斜めに並んでいる値以外のすべての値は、エラーを示しています。</span><span class="sxs-lookup"><span data-stu-id="80bb0-140">All other values outside the diagonal represent errors.</span></span> <span data-ttu-id="80bb0-141">一部のエラーは偽陽性で、モデルは顧客がゴールド プログラムに応募すると予測したが、実際はそうではなかったことを意味しています。</span><span class="sxs-lookup"><span data-stu-id="80bb0-141">Some errors are false positives, meaning the model predicted the customer would join the gold program but was wrong.</span></span>  <span data-ttu-id="80bb0-142">扱う領域によっては、偽陽性が大きな損失を招く場合もあります。</span><span class="sxs-lookup"><span data-stu-id="80bb0-142">Depending on your domain, false positives can be very costly.</span></span>  
  
     <span data-ttu-id="80bb0-143">その他のエラーは偽陰性で、モデルは顧客が興味を持たないと予測したが、実際はそれらの顧客がプログラムに応募したことを意味しています。</span><span class="sxs-lookup"><span data-stu-id="80bb0-143">Others are false negatives, meaning the model predicted the customer would not be interested though he or she did join the program.</span></span> <span data-ttu-id="80bb0-144">問題とする領域によっては、この機会損失が重大な影響を及ぼす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="80bb0-144">Again, depending on the problem domain, this lost opportunity cost might be significant.</span></span>  
  
## <a name="using-the-classification-matrix-wizard"></a><span data-ttu-id="80bb0-145">分類マトリックス ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="80bb0-145">Using the Classification Matrix Wizard</span></span>  
  
1.  <span data-ttu-id="80bb0-146">予測の基礎となるマイニング モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="80bb0-146">Select the mining model on which to base predictions.</span></span>  
  
2.  <span data-ttu-id="80bb0-147">新しいテスト データのソースを選択するか、構造と共に保存されているテスト データを使用します。</span><span class="sxs-lookup"><span data-stu-id="80bb0-147">Select a source of new test data, or use testing data that was saved with the structure.</span></span>  
  
3.  <span data-ttu-id="80bb0-148">精度を評価する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="80bb0-148">Select the column for which you want to assess accuracy.</span></span> <span data-ttu-id="80bb0-149">マトリックスを作成するときに選択できるのは 1 列だけですが、列には複数の値を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="80bb0-149">You can choose only one column when creating a matrix, but the column can have multiple values.</span></span>  
  
     <span data-ttu-id="80bb0-150">ヒント: 予測可能な列に比較対象の列が数多く含まれている場合、分類マトリックスの解釈が難しくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="80bb0-150">Tip: It can be difficult to interpret a classification matrix if your predictable column has many columns to compare.</span></span>  
  
     <span data-ttu-id="80bb0-151">**[予測する列の選択**] ページでは、間違った値と間違った値の数を表示するか、パーセンテージを表示するかを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="80bb0-151">In the **Select Columns to Predict** page, you can also specify whether you want to display the count of incorrect and incorrect values, or display a percentage.</span></span>  
  
4.  <span data-ttu-id="80bb0-152">[ソース データの選択] ページでは、外部テスト データと、モデルと共に保存されたテスト データのどちらを使用するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="80bb0-152">On the Select Source Data page, indicate whether you are using external testing data, or the test data saved with the model.</span></span>  
  
5.  <span data-ttu-id="80bb0-153">外部テストデータを使用する場合は、ウィザードの [**リレーションシップの指定**] ページで、モデルを入力列にマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="80bb0-153">If you use external testing data, you need to map the model to the input columns on the **Specify Relationship** page of the wizard.</span></span>  
  
     <span data-ttu-id="80bb0-154">埋め込みテスト データセットを使用する場合、マッピングは自動的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="80bb0-154">If you use the embedded test data set, the mapping is done for you</span></span>  
  
6.  <span data-ttu-id="80bb0-155">モデルに対して予測を実行し、分類マトリックスを生成するには、[**完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80bb0-155">Click **Finish** to run predictions against the model and generate the classification matrix.</span></span>  
  
     <span data-ttu-id="80bb0-156">ウィザードにより、分類マトリックスおよび分析に関するその他の詳細を含むレポートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="80bb0-156">The wizard creates a report that contains the classification matrix and other details about the analysis.</span></span> <span data-ttu-id="80bb0-157">このレポートは、Excel のテーブルとして保存されます。レポートの概要には、正しく予測されたケースの数と、誤っていた予測の数が示されます。</span><span class="sxs-lookup"><span data-stu-id="80bb0-157">This report is saved as a table in Excel, with a summary above the report that indicates how many cases were correctly predicted and how many predictions were wrong.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="80bb0-158">必要条件</span><span class="sxs-lookup"><span data-stu-id="80bb0-158">Requirements</span></span>  
  
-   <span data-ttu-id="80bb0-159">分類マトリックスを作成するには、精度の測定をサポートする既存のマイニング モデルにアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="80bb0-159">To create a classification matrix, you must have access to an existing mining model that supports accuracy measurement.</span></span> <span data-ttu-id="80bb0-160">予測モデルおよびアソシエーション モデルは、このツールを使用して測定できません。</span><span class="sxs-lookup"><span data-stu-id="80bb0-160">Forecasting models and association models cannot be measured using this tool.</span></span>  
  
-   <span data-ttu-id="80bb0-161">測定するモデルは、不連続値、または既に分離されている値を予測する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80bb0-161">The model that you are measuring needs to predict a value that is either discrete or that has already been discretized.</span></span>  
  
-   <span data-ttu-id="80bb0-162">構造またはモデルと共にテストセットを保存するオプションを使用していない場合は、モデルで使用されているものと同じ数の列を持つ、データ型が一致する入力データセットを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80bb0-162">If you didn't use the option to save a testing set along with your structure or model, you need to obtain an input data set that has essentially the same number of columns, with matching data types, as those used in the model.</span></span>  
  
-   <span data-ttu-id="80bb0-163">データ マイニング モデルおよびテストに使用する新しいデータの両方に予測可能な列が 1 つ以上含まれ、なおかつ両列に同じ種類のデータが含まれていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="80bb0-163">Both the data mining model and the new data that you are using for testing must contain at least one column that can be predicted, and the columns must contain the same kind of data.</span></span>  
  
### <a name="known-issues"></a><span data-ttu-id="80bb0-164">既知の問題</span><span class="sxs-lookup"><span data-stu-id="80bb0-164">Known Issues</span></span>  
 <span data-ttu-id="80bb0-165">SQL Server 2012 および SQL Server 2014 では、内部テストデータセットをモデルにマップする機能が、**分類マトリックス**ツールで動作していません。</span><span class="sxs-lookup"><span data-stu-id="80bb0-165">In SQL Server 2012 and SQL Server 2014, the ability to map the internal test data set to the model is not working in the **Classification Matrix** tool.</span></span> <span data-ttu-id="80bb0-166">ただし、外部データ セットを指定して、元のデータ セットのエラーを特定するための入力としてトレーニング セットを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="80bb0-166">However, you can specify an external data set, and then select the training set as the input to determine error on the original data set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80bb0-167">参照</span><span class="sxs-lookup"><span data-stu-id="80bb0-167">See Also</span></span>  
 <span data-ttu-id="80bb0-168">[Excel 用データマイニングアドインのモデルを検証し、モデルを使用して予測 &#40;する&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="80bb0-168">[Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span></span>  
 <span data-ttu-id="80bb0-169">[データ &#40;SQL Server データマイニングアドインの探索&#41;](explore-data-sql-server-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="80bb0-169">[Explore Data &#40;SQL Server Data Mining Add-ins&#41;](explore-data-sql-server-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="80bb0-170">Excel 用のテーブル分析ツール &#40;のカテゴリの検出&#41;</span><span class="sxs-lookup"><span data-stu-id="80bb0-170">Detect Categories &#40;Table Analysis Tools for Excel&#41;</span></span>](detect-categories-table-analysis-tools-for-excel.md)  
  
  
