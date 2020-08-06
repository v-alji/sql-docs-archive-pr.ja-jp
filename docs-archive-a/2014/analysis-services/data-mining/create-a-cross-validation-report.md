---
title: クロス検証レポートを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- validating data mining models
- mining structures [Analysis Services], how-to topics
- cross-validation [data mining]
- statistical standard deviation
ms.assetid: 7b1fec4c-7053-41eb-b030-5179257967a4
author: minewiskan
ms.author: owend
ms.openlocfilehash: ccbafe63b0026cd45a15ea71fd84e223c1b32a9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711158"
---
# <a name="create-a-cross-validation-report"></a><span data-ttu-id="f99b0-102">クロス検証レポートの作成</span><span class="sxs-lookup"><span data-stu-id="f99b0-102">Create a Cross-Validation Report</span></span>
  <span data-ttu-id="f99b0-103">このトピックでは、データ マイニング デザイナーの [精度チャート] タブを使用してクロス検証レポートを作成する方法を順を追って説明します。</span><span class="sxs-lookup"><span data-stu-id="f99b0-103">This topic walks you through creation of a cross-validation report using the Accuracy Chart tab in Data Mining Designer.</span></span> <span data-ttu-id="f99b0-104">クロス検証レポートの外観およびレポートに含まれる統計メジャーに関する一般的な情報については、「[相互検証 (Analysis Services - データ マイニング)](cross-validation-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f99b0-104">For general information about what a cross-validation report looks like, and the statistical measures it includes, see [Cross-Validation &#40;Analysis Services - Data Mining&#41;](cross-validation-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="f99b0-105">クロス検証レポートは、リフト チャートや分類マトリックスなどの精度チャートとは基本的に異なります。</span><span class="sxs-lookup"><span data-stu-id="f99b0-105">A cross-validation report is fundamentally different from an accuracy chart, such as a lift chart or classification matrix.</span></span>  
  
-   <span data-ttu-id="f99b0-106">クロス検証では、モデルまたは構造で使用されるデータの全体的な分布を評価します。したがって、テスト データ セットは指定しません。</span><span class="sxs-lookup"><span data-stu-id="f99b0-106">Cross-validation assesses the overall distribution of data that is used in a model or structure; therefore, you do not specify a testing data set.</span></span> <span data-ttu-id="f99b0-107">クロス検証では、モデルまたはマイニング構造のトレーニングに使用された元のデータのみ常に使用されます。</span><span class="sxs-lookup"><span data-stu-id="f99b0-107">Cross-validation always uses only the original data that was used to train the model or the mining structure.</span></span>  
  
-   <span data-ttu-id="f99b0-108">クロス検証は、1 つの予測可能な結果に対してのみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="f99b0-108">Cross-validation can only be performed with respect to a single predictable outcome.</span></span> <span data-ttu-id="f99b0-109">構造で異なる予測可能属性を持つモデルがサポートされる場合は、予測可能な出力ごとに異なるレポートを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f99b0-109">If the structure supports models that have different predictable attributes, you must create separate reports for each predictable output.</span></span>  
  
-   <span data-ttu-id="f99b0-110">クロス検証に使用できるのは、現在選択されている構造に関連するモデルだけです。</span><span class="sxs-lookup"><span data-stu-id="f99b0-110">Only models that are related to the currently selected structure are available for cross-validation.</span></span>  
  
-   <span data-ttu-id="f99b0-111">現在選択されている構造でクラスター モデルと非クラスター モデルの組み合わせがサポートされる場合、 **[結果の取得]** をクリックすると、クロス検証ストアド プロシージャによって、同じ予測可能列を持つモデルが自動的に読み込まれ、同じ予測可能な属性を共有しないクラスター モデルは無視されます。</span><span class="sxs-lookup"><span data-stu-id="f99b0-111">If the structure that is currently selected supports a combination of clustering and non-clustering models, when you click **Get Results**, the cross-validation stored procedure will automatically load models that have the same predicted column, and ignore clustering models that do not share the same predictable attribute.</span></span>  
  
-   <span data-ttu-id="f99b0-112">予測可能属性を持たないクラスター モデルに対するクロス検証レポートは、マイニング構造で他の予測可能な属性がサポートされない場合にのみ作成できます。</span><span class="sxs-lookup"><span data-stu-id="f99b0-112">You can create a cross-validation report on a clustering model that does not have a predictable attribute only if the mining structure does not support any other predictable attributes.</span></span>  
  
### <a name="select-a-mining-structure"></a><span data-ttu-id="f99b0-113">マイニング構造の選択</span><span class="sxs-lookup"><span data-stu-id="f99b0-113">Select a mining structure</span></span>  
  
1.  <span data-ttu-id="f99b0-114">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でデータ マイニング デザイナーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f99b0-114">Open the Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="f99b0-115">ソリューション エクスプローラーで、レポートを作成する構造またはモデルを含んだデータベースを開きます。</span><span class="sxs-lookup"><span data-stu-id="f99b0-115">In Solution Explorer, open the database that contains the structure or model for which you want to create a report.</span></span>  
  
3.  <span data-ttu-id="f99b0-116">マイニング構造をダブルクリックして、構造とその関連モデルをデータ マイニング デザイナーで開きます。</span><span class="sxs-lookup"><span data-stu-id="f99b0-116">Double-click the mining structure to open the structure and its related models in Data Mining Designer.</span></span>  
  
4.  <span data-ttu-id="f99b0-117">**[マイニング精度チャート]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f99b0-117">Click the **Mining Accuracy Chart** tab.</span></span>  
  
5.  <span data-ttu-id="f99b0-118">**[クロス検証]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f99b0-118">Click the **Cross Validation** tab.</span></span>  
  
### <a name="set-cross-validation-options"></a><span data-ttu-id="f99b0-119">クロス検証オプションの設定</span><span class="sxs-lookup"><span data-stu-id="f99b0-119">Set cross-validation options</span></span>  
  
1.  <span data-ttu-id="f99b0-120">**[クロス検証]** タブの **[フォールド カウント]** で、下矢印をクリックして 1 ～ 10 の数字を選択します。</span><span class="sxs-lookup"><span data-stu-id="f99b0-120">On the **Cross Validation** tab, for **Fold Count**, click the down arrow to select a number between 1 and 10.</span></span> <span data-ttu-id="f99b0-121">既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="f99b0-121">The default value is 10.</span></span>  
  
     <span data-ttu-id="f99b0-122">**[フォールド カウント]** は、元のデータセット内に作成されるパーティションの数を表します。</span><span class="sxs-lookup"><span data-stu-id="f99b0-122">The **Fold Count** represents the number of partitions that will be created within the original data set.</span></span> <span data-ttu-id="f99b0-123">[フォールド カウント] を 1 に設定すると、パーティション分割を行わずにトレーニング セットが使用されます。</span><span class="sxs-lookup"><span data-stu-id="f99b0-123">If you set Fold Count to 1, the training set will be used without partitioning.</span></span>  
  
2.  <span data-ttu-id="f99b0-124">**[対象の属性]** で、下矢印をクリックし、一覧から列を選択します。</span><span class="sxs-lookup"><span data-stu-id="f99b0-124">For **Target Attribute**, click the down arrow, and select a column from the list.</span></span> <span data-ttu-id="f99b0-125">モデルがクラスター モデルである場合は、モデルに予測可能な属性がないことを示す **[#クラスター]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f99b0-125">If the model is a clustering model, select **#Cluster** to indicate that the model does not have a predictable attribute.</span></span> <span data-ttu-id="f99b0-126">**[#クラスター]** という値は、マイニング構造で他の種類の予測可能な属性がサポートされない場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f99b0-126">Note that the value, **#Cluster**, is available only when the mining structure does not support other types of predictable attributes.</span></span>  
  
     <span data-ttu-id="f99b0-127">予測可能な属性は、レポートごとに 1 つしか選択できません。</span><span class="sxs-lookup"><span data-stu-id="f99b0-127">You can select only one predictable attribute per report.</span></span> <span data-ttu-id="f99b0-128">既定では、予測可能な属性が同じであるすべての関連モデルがレポートの対象となります。</span><span class="sxs-lookup"><span data-stu-id="f99b0-128">By default, all related models that have the same predictable attribute are included in the report.</span></span>  
  
3.  <span data-ttu-id="f99b0-129">データが指定した数のフォールドに分割される場合に、データの代表的なサンプルを提供できるだけの数を **[ケースの最大数]** に入力します。</span><span class="sxs-lookup"><span data-stu-id="f99b0-129">For **Max Cases**, type a number that is large enough to provide a representative sample of data when the data is split among the specified number of folds.</span></span> <span data-ttu-id="f99b0-130">この数値がモデルのトレーニング セットのケース数を上回る場合は、すべてのケースが使用されます。</span><span class="sxs-lookup"><span data-stu-id="f99b0-130">If the number is greater than the count of cases in the model training set, all cases will be used.</span></span>  
  
     <span data-ttu-id="f99b0-131">トレーニング データセットが非常に大きい場合は、 **[ケースの最大数]** に値を設定することで、処理されるケースの総数が制限され、レポートを早く完了できます。</span><span class="sxs-lookup"><span data-stu-id="f99b0-131">If the training data set is very large, setting the value for **Max Cases** limits the total number of cases processed, and lets the report finish faster.</span></span> <span data-ttu-id="f99b0-132">ただし、クロス検証のためのデータが不十分となる可能性があるので、 **[ケースの最大数]** をあまり小さな値に設定しないでください。</span><span class="sxs-lookup"><span data-stu-id="f99b0-132">However, you should not set **Max Cases** too low or there may be insufficient data for cross-validation.</span></span>  
  
4.  <span data-ttu-id="f99b0-133">必要に応じて、 **[対象の状態]** にモデル化する予測可能な属性の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="f99b0-133">Optionally, for **Target State**, type the value of the predictable attribute that you want to model.</span></span> <span data-ttu-id="f99b0-134">たとえば、[Bike Buyer] 列の設定可能な値が 1 (Yes) と 2 (No) の 2 つである場合は、「1」を入力することで目的の結果のモデルの精度を評価できます。</span><span class="sxs-lookup"><span data-stu-id="f99b0-134">For example, if the column [Bike Buyer] has two possible values, 1 (Yes) and 2 (No), you can enter the value 1 to assess the accuracy of the model for just the desired outcome.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f99b0-135"> 値を入力しなかった場合は、 **[対象のしきい値]** オプションを指定できなくなり、予測可能な属性の設定可能なすべての値についてモデルが評価されます。</span><span class="sxs-lookup"><span data-stu-id="f99b0-135">If you do not enter a value, the **Target Threshold** option is not available, and the model is assessed for all possible values of the predictable attribute.</span></span>  
  
5.  <span data-ttu-id="f99b0-136">必要に応じて、 **[対象のしきい値]** に 0 ～ 1 の小数を入力して、予測が正確であると見なされるために必要な最小確率を指定します。</span><span class="sxs-lookup"><span data-stu-id="f99b0-136">Optionally, for **Target Threshold**, type a decimal number between 0 and 1 to specify the minimum probability that a prediction must have to be counted as accurate.</span></span>  
  
     <span data-ttu-id="f99b0-137">確率のしきい値の設定方法に関するその他のヒントについては、「 [相互検証レポートのメジャー](measures-in-the-cross-validation-report.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f99b0-137">For additional tips about how to set probability thresholds, see [Measures in the Cross-Validation Report](measures-in-the-cross-validation-report.md).</span></span>  
  
6.  <span data-ttu-id="f99b0-138">**[結果の取得]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f99b0-138">Click **Get Results**.</span></span>  
  
### <a name="print-the-cross-validation-report"></a><span data-ttu-id="f99b0-139">相互検証レポートの印刷</span><span class="sxs-lookup"><span data-stu-id="f99b0-139">Print the cross-validation report</span></span>  
  
1.  <span data-ttu-id="f99b0-140">**[クロス検証]** タブで、完了したレポートを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="f99b0-140">Right-click the completed report on the **Cross Validation** tab.</span></span>  
  
2.  <span data-ttu-id="f99b0-141">ショートカット メニューの **[印刷]** をクリックするか、先にレポートを確認する場合は **[印刷プレビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f99b0-141">In the shortcut menu, select **Print** or **Print Preview** to review the report first.</span></span>  
  
### <a name="create-a-copy-of-the-report-in-microsoft-excel"></a><span data-ttu-id="f99b0-142">Microsoft Excel でのレポートのコピーの作成</span><span class="sxs-lookup"><span data-stu-id="f99b0-142">Create a copy of the report in Microsoft Excel</span></span>  
  
1.  <span data-ttu-id="f99b0-143">**[クロス検証]** タブで、完了したレポートを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="f99b0-143">Right-click the completed report on the **Cross Validation** tab.</span></span>  
  
2.  <span data-ttu-id="f99b0-144">ショートカット メニューの **[すべて選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f99b0-144">In the shortcut menu, select **Select All**.</span></span>  
  
3.  <span data-ttu-id="f99b0-145">選択したテキストを右クリックし、 **[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f99b0-145">Right-click the selected text, and select **Copy**.</span></span>  
  
4.  <span data-ttu-id="f99b0-146">選択した内容を、開いている Excel ブックに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="f99b0-146">Paste the selection into an open Excel workbook.</span></span> <span data-ttu-id="f99b0-147">**[貼り付け]** オプションを使用すると、レポートが HTML として Excel に貼り付けられ、行と列の形式が維持されます。</span><span class="sxs-lookup"><span data-stu-id="f99b0-147">If you use the **Paste** option, the report is pasted into Excel as HTML, which preserves row and column formatting.</span></span> <span data-ttu-id="f99b0-148">**[形式を選択して貼り付け]** オプションを使用して、テキストまたは Unicode テキストとしてレポートを貼り付けると、行で区切られた形式でレポートが貼り付けられます。</span><span class="sxs-lookup"><span data-stu-id="f99b0-148">If you paste the report by using the **Paste Special** options for text or Unicode text, the report is pasted in row-delimited format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f99b0-149">参照</span><span class="sxs-lookup"><span data-stu-id="f99b0-149">See Also</span></span>  
 [<span data-ttu-id="f99b0-150">相互検証レポートのメジャー</span><span class="sxs-lookup"><span data-stu-id="f99b0-150">Measures in the Cross-Validation Report</span></span>](measures-in-the-cross-validation-report.md)  
  
  
