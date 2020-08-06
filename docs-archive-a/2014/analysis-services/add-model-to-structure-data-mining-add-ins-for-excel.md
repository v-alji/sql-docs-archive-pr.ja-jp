---
title: 構造へのモデルの追加 (Excel 用データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, creating
ms.assetid: 8efd5bf4-4e6a-4ee8-971a-6efaed5f3b76
author: minewiskan
ms.author: owend
ms.openlocfilehash: b42cecafc2e3d676465e372e00fe472132f06a3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633700"
---
# <a name="add-model-to-structure-data-mining-add-ins-for-excel"></a><span data-ttu-id="5af71-102">構造へのモデルの追加 (Excel 用データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="5af71-102">Add Model to Structure (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="5af71-103">![[構造へのモデルの追加] ボタン](media/dmc-addmodel.gif "[構造へのモデルの追加] ボタン")</span><span class="sxs-lookup"><span data-stu-id="5af71-103">![Add Model to Structure button](media/dmc-addmodel.gif "Add Model to Structure button")</span></span>  
  
 <span data-ttu-id="5af71-104">[**構造へのモデルの追加**] をクリックすると、既存のマイニング構造で使用する新しいマイニングモデルの作成に役立つウィザードが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5af71-104">When you click **Add Model to Structure**, a wizard starts that helps you create a new mining model to use with an existing mining structure.</span></span> <span data-ttu-id="5af71-105">このオプションは、同じデータに基づくモデルを比較したり、カスタマイズしたモデルを作成したりできるため便利です。</span><span class="sxs-lookup"><span data-stu-id="5af71-105">This option is useful because it lets you compare models that are based on the same data, or create customized models.</span></span>  
  
 <span data-ttu-id="5af71-106">Analysis Services のインスタンスに必要なデータがまだ含まれていない場合は、マイニング構造の[作成 &#40;SQL Server データマイニングアドイン&#41;](create-mining-structure-sql-server-data-mining-add-ins.md)ウィザードを使用して、マイニング構造を設定します。</span><span class="sxs-lookup"><span data-stu-id="5af71-106">If the instance of Analysis Services does not already contain the data you need, use the [Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41;](create-mining-structure-sql-server-data-mining-add-ins.md) wizard to set up a mining structure.</span></span> <span data-ttu-id="5af71-107">または、モデリング ウィザードのいずれかを起動してから、ウィザードで作成した構造に新しいモデルを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="5af71-107">Or, you can launch one of the modeling wizards, and then add a new model to the structure created by the wizard.</span></span>  
  
 <span data-ttu-id="5af71-108">ウィザードでサポートされていないアルゴリズムを使用して高度なモデルを作成するには、マイニング構造を作成してから、**データマイニング詳細クエリエディター**を使用してモデルを追加します。</span><span class="sxs-lookup"><span data-stu-id="5af71-108">To create advanced models using algorithms not supported by the wizards, create a mining structure and then add a model using the **Data Mining Advanced Query Editor**.</span></span>  
  
## <a name="add-a-new-model-to-an-existing-structure"></a><span data-ttu-id="5af71-109">既存の構造に新しいモデルを追加する</span><span class="sxs-lookup"><span data-stu-id="5af71-109">Add a new model to an existing structure</span></span>  
  
1.  <span data-ttu-id="5af71-110">[**データマイニング**] リボンで、[**詳細設定**] の下の矢印をクリックし、[**構造へのモデルの追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5af71-110">On the **Data Mining** ribbon, click the arrow under **Advanced**, and then select **Add Model to Structure**.</span></span>  
  
2.  <span data-ttu-id="5af71-111">[**構造の選択**] ダイアログボックスで、使用するデータが含まれている構造を選択し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5af71-111">In the **Select Structure** dialog box, choose the structure that contains the data you want to use, and then click **Next**.</span></span>  
  
     <span data-ttu-id="5af71-112">**ヒント**: 必要なデータが含まれているマイニング構造がわからない場合は、**モデルのドキュメント**化ウィザードを使用して、データに関する列と基本的な統計情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="5af71-112">**Tip**: If you are not sure which mining structure contains the data you need, use the **Document Model** wizard to view the columns and basic statistics about the data.</span></span>  
  
     <span data-ttu-id="5af71-113">マイニング構造が見つからない場合は、現在使用している接続を確認してください。</span><span class="sxs-lookup"><span data-stu-id="5af71-113">If you can't find a mining structure, check the connection that you are currently using.</span></span> <span data-ttu-id="5af71-114">別のサーバーへの接続を開く必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="5af71-114">You might need to open a connection to a different server.</span></span>  
  
3.  <span data-ttu-id="5af71-115">**[マイニングアルゴリズムの選択**] ダイアログボックスで、新しいマイニングモデルで使用するマイニングアルゴリズムを選択します。</span><span class="sxs-lookup"><span data-stu-id="5af71-115">In the **Select Mining Algorithm** dialog box, choose a mining algorithm to use in the new mining model.</span></span>  
  
     <span data-ttu-id="5af71-116">このダイアログボックスには、ウィザードに表示されるよりも多くのオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="5af71-116">Notice that the dialog box provides a lot more options than you'll see in the wizards.</span></span> <span data-ttu-id="5af71-117">データに互換性がある場合は、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーでサポートされているアルゴリズムを使用してモデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="5af71-117">You can create a model using any algorithm supported on your [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server, provided your data is compatible.</span></span>  
  
4.  <span data-ttu-id="5af71-118">また、[**パラメーター** ] ボタンをクリックして [**アルゴリズムパラメーター** ] ダイアログボックスを開き、アルゴリズムのパラメーターをカスタマイズすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5af71-118">We recommend that you also click the **Parameters** button to open the **Algorithm Parameters** dialog box and customize parameters on the algorithm.</span></span> <span data-ttu-id="5af71-119">このオプションは、カスタム マイニング モデルを作成する最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="5af71-119">This option is the easiest way to create custom mining models.</span></span>  
  
5.  <span data-ttu-id="5af71-120">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5af71-120">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="5af71-121">**[列の選択**] ダイアログボックスで、列の一覧を確認し、必要に応じて、列の使用法を次のいずれかの値に変更します。</span><span class="sxs-lookup"><span data-stu-id="5af71-121">In the **Select Columns** dialog box, review the list of columns, and if necessary, change the usage of the columns to one of these values:</span></span>  
  
    -   <span data-ttu-id="5af71-122">**入力**。</span><span class="sxs-lookup"><span data-stu-id="5af71-122">**Input**.</span></span> <span data-ttu-id="5af71-123">列に含まれる変数が結果に影響する可能性があり、モデルへの入力として使用されます。</span><span class="sxs-lookup"><span data-stu-id="5af71-123">Indicates that the column contains variables that may affect the outcome and should be used as inputs to the model.</span></span>  
  
    -   <span data-ttu-id="5af71-124">**入力と予測**。</span><span class="sxs-lookup"><span data-stu-id="5af71-124">**Input and Predict**.</span></span> <span data-ttu-id="5af71-125">データは入力として使用され、これらの値が予測されます。</span><span class="sxs-lookup"><span data-stu-id="5af71-125">Indicates that the data should be used as an input, and that you also want to predict these values.</span></span>  
  
    -   <span data-ttu-id="5af71-126">**予測のみ**。</span><span class="sxs-lookup"><span data-stu-id="5af71-126">**Predict only**.</span></span> <span data-ttu-id="5af71-127">データはモデルの入力として使用されません。</span><span class="sxs-lookup"><span data-stu-id="5af71-127">Indicates that the data should not be used as an input for the model.</span></span>  
  
    -   <span data-ttu-id="5af71-128">**[キー]**</span><span class="sxs-lookup"><span data-stu-id="5af71-128">**Key**.</span></span> <span data-ttu-id="5af71-129">各モデルには、少なくとも1つのキーが必要です。</span><span class="sxs-lookup"><span data-stu-id="5af71-129">Each model requires at least one key.</span></span> <span data-ttu-id="5af71-130">モデルの種類によっては、 **sequencekey**や**timekey**などの追加の特殊キーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="5af71-130">Depending on the model type, you might also have the option to additional special keys, such as the **SequenceKey** or **TimeKey**.</span></span>  
  
    -   <span data-ttu-id="5af71-131">**使用しないで**ください。</span><span class="sxs-lookup"><span data-stu-id="5af71-131">**Do not use**.</span></span> <span data-ttu-id="5af71-132">データが構造内に存在してもモデルには使用されません。</span><span class="sxs-lookup"><span data-stu-id="5af71-132">Indicates that the data should not be used in the model, even if present in the structure.</span></span>  
  
7.  <span data-ttu-id="5af71-133">参照ボタン ([. **..])** をクリックして、[**列モデルフラグの設定**] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="5af71-133">Click the browse **(...)** button to open the **Set Column Model Flags** dialog box.</span></span>  
  
     <span data-ttu-id="5af71-134">各データ列の使用法がモデルに適切かどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="5af71-134">Take a minute to verify that the usage of each data column is appropriate for the model.</span></span> <span data-ttu-id="5af71-135">これは、モデルを処理するときに発生するエラーを回避するための重要な手順です。</span><span class="sxs-lookup"><span data-stu-id="5af71-135">This is an important step for preventing errors when you try to process the model.</span></span>  
  
     <span data-ttu-id="5af71-136">たとえば、デシジョン ツリー モデルに対して作成された構造を再利用して、Naïve Bayes アルゴリズムをこれに適用する場合、データ型が `Numeric` でコンテンツの種類が `Continuous` の列はビン分割するか、離散変数に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5af71-136">For example, if you re-use a structure that was created for a decision trees model and apply the Naïve Bayes algorithm to it, columns that have the data type `Numeric` and the content type `Continuous` will need to be binned or changed to discrete variables.</span></span>  
  
     <span data-ttu-id="5af71-137">構造内の列が新しいアルゴリズムに適用されない場合は、[**使用しない**] を選択するとバイパスできます。</span><span class="sxs-lookup"><span data-stu-id="5af71-137">If columns in the structure are not applicable to the new algorithm, you can bypass them by selecting **Do not use**.</span></span>  
  
8.  <span data-ttu-id="5af71-138">[**列モデルフラグの設定**] ダイアログボックスで、モデリングフラグ (存在する場合) を確認または設定します。</span><span class="sxs-lookup"><span data-stu-id="5af71-138">In the **Set Column Model Flags** dialog box, review or set the modeling flags, if any.</span></span>  
  
     <span data-ttu-id="5af71-139">モデリング フラグを使用すると、特に null 値の処理方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="5af71-139">Modeling flags let you control the way that nulls are handled, among other things.</span></span> <span data-ttu-id="5af71-140">詳細については、「[モデリング フラグ &#40;データ マイニング&#41;](data-mining/modeling-flags-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5af71-140">For more information, see [Modeling Flags &#40;Data Mining&#41;](data-mining/modeling-flags-data-mining.md).</span></span>  
  
     <span data-ttu-id="5af71-141">完了したら [ **OK** ] をクリックして、ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="5af71-141">Click **OK** when done to close the dialog box.</span></span>  
  
9. <span data-ttu-id="5af71-142">[**完了**] ダイアログボックスで、新しいマイニングモデルの名前と説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="5af71-142">In the **Finish** dialog box, type a name and description for the new mining model.</span></span>  
  
     <span data-ttu-id="5af71-143">作成したモデルの種類に応じて、次のオプションも表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="5af71-143">Depending on the type of model you built, you might also have these options:</span></span>  
  
    -   <span data-ttu-id="5af71-144">作成後に完成したマイニング モデルを参照します。</span><span class="sxs-lookup"><span data-stu-id="5af71-144">Browse the completed mining model after it is built.</span></span>  
  
    -   <span data-ttu-id="5af71-145">モデルからソース データへのドリルスルーを使用します。</span><span class="sxs-lookup"><span data-stu-id="5af71-145">Use drillthrough from the model to the source data.</span></span>  
  
         <span data-ttu-id="5af71-146">詳細については、「[マイニングモデルのドリルスルー](data-mining/drillthrough-on-mining-models.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5af71-146">For more information, see [Drillthrough on Mining Models](data-mining/drillthrough-on-mining-models.md).</span></span>  
  
10. <span data-ttu-id="5af71-147">**[完了]** をクリックして、変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="5af71-147">Click **Finish** to save your changes.</span></span> <span data-ttu-id="5af71-148">これにより、新しいモデルはサーバーに配置され処理されます。</span><span class="sxs-lookup"><span data-stu-id="5af71-148">As you do so the new model is deployed to the server and processed.</span></span>  
  
### <a name="related-options"></a><span data-ttu-id="5af71-149">関連オプション</span><span class="sxs-lookup"><span data-stu-id="5af71-149">Related Options</span></span>  
  
|<span data-ttu-id="5af71-150">オプション</span><span class="sxs-lookup"><span data-stu-id="5af71-150">Option</span></span>|<span data-ttu-id="5af71-151">説明</span><span class="sxs-lookup"><span data-stu-id="5af71-151">Comments</span></span>|  
|------------|--------------|  
|<span data-ttu-id="5af71-152">**[構造またはモデルの選択**] ダイアログボックス</span><span class="sxs-lookup"><span data-stu-id="5af71-152">**Select Structure or Model** dialog box</span></span>|<span data-ttu-id="5af71-153">新しいモデルの作成の基礎として使用する既存のマイニング構造を選択します。</span><span class="sxs-lookup"><span data-stu-id="5af71-153">Choose en existing mining structure to use as the basis for building a new model.</span></span>  <span data-ttu-id="5af71-154">選択する構造は、現在の接続にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="5af71-154">The structure you pick must be located on the current connection.</span></span> <span data-ttu-id="5af71-155">接続されていない場合は、[ [Excel 用データマイニングクライアント &#40;データマイニングクライアント]&#41;](connect-to-source-data-data-mining-client-for-excel.md)ツールを使用して接続を変更します。</span><span class="sxs-lookup"><span data-stu-id="5af71-155">If not, change connections using the [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md) tool.</span></span>|  
|<span data-ttu-id="5af71-156">**[マイニングアルゴリズムの選択**] ダイアログボックス</span><span class="sxs-lookup"><span data-stu-id="5af71-156">**Select Mining Algorithm** dialog Box</span></span>|<span data-ttu-id="5af71-157">接続先のサーバーに応じて、データ マイニング アルゴリズムの一覧は異なります。</span><span class="sxs-lookup"><span data-stu-id="5af71-157">The list of data mining algorithms depends on which server you are connected to.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="5af71-158">の Standard Edition と Enterprise Edition には異なるアルゴリズムが用意されています。</span><span class="sxs-lookup"><span data-stu-id="5af71-158">provides different algorithms in the Standard and Enterprise editions.</span></span> <span data-ttu-id="5af71-159">管理者が、カスタム アルゴリズムを追加している場合もあります。</span><span class="sxs-lookup"><span data-stu-id="5af71-159">Your administrator also might have added custom algorithms.</span></span><br /><br /> <span data-ttu-id="5af71-160">アルゴリズムが表示されない場合は、のインスタンスに接続していることを確認し [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="5af71-160">If you can't see any algorithms, verify that you are connected to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>|  
|<span data-ttu-id="5af71-161">**アルゴリズムパラメーター**ダイアログボックス</span><span class="sxs-lookup"><span data-stu-id="5af71-161">**Algorithm Parameters** Dialog Box</span></span>|<span data-ttu-id="5af71-162">これらの設定では、分析メソッドに固有のパラメーターを使用して各アルゴリズムをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="5af71-162">In these settings, you can customize each algorithm using parameters specific to the analytical method.</span></span> <span data-ttu-id="5af71-163">また、モデルの結果を複数のトレーニング パス間で再現できるようにシードを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="5af71-163">You can also set a seed to ensure that the results of the model can be reproduced across multiple training passes.</span></span><br /><br /> <span data-ttu-id="5af71-164">詳細については、「 [SQL Server データマイニングアドイン&#41;&#40;のアルゴリズムパラメーター ](algorithm-parameters-sql-server-data-mining-add-ins.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5af71-164">For more information, see [Algorithm Parameters &#40;SQL Server Data Mining Add-ins&#41;](algorithm-parameters-sql-server-data-mining-add-ins.md).</span></span>|  
|<span data-ttu-id="5af71-165">**列モデルフラグの設定**ダイアログボックス</span><span class="sxs-lookup"><span data-stu-id="5af71-165">**Set Column Model Flags** Dialog Box</span></span>|<span data-ttu-id="5af71-166">モデリング フラグを使用すると、欠落しているデータの処理方法を指定してモデルを改善できます。</span><span class="sxs-lookup"><span data-stu-id="5af71-166">Modeling flags can improve your model by specifying how missing data is to be handled.</span></span> <span data-ttu-id="5af71-167">詳細については、「[モデリング フラグ &#40;データ マイニング&#41;](data-mining/modeling-flags-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5af71-167">For more information, see [Modeling Flags &#40;Data Mining&#41;](data-mining/modeling-flags-data-mining.md).</span></span>|  
  
###  <a name="setting-column-usage"></a><a name="Bkmk_mdlcolumn"></a><span data-ttu-id="5af71-168">列の使用法の設定</span><span class="sxs-lookup"><span data-stu-id="5af71-168">Setting Column Usage</span></span>  
 <span data-ttu-id="5af71-169">新しいモデルを既存のマイニング構造に追加する場合は、マイニング構造の各データ列をどのようにモデルで使用するかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5af71-169">When you add a new model to an existing mining structure, you must specify how the model will use each of the columns of data in the mining structure.</span></span> <span data-ttu-id="5af71-170">このウィザードのオプションは、マイニング構造のオプションよりもはるかに詳細であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="5af71-170">You'll probably observe that the options in this wizard are far more detailed than the options on the mining structure.</span></span> <span data-ttu-id="5af71-171">なぜですか?</span><span class="sxs-lookup"><span data-stu-id="5af71-171">Why?</span></span>  
  
 <span data-ttu-id="5af71-172">これは、ウィザードを使用してモデルと構造を一緒に作成すると、アルゴリズムでデータが使用される方法を制御する多くのオプションが自動的に設定されるためです。</span><span class="sxs-lookup"><span data-stu-id="5af71-172">The reason is that when you create a model and a structure together using a wizard, many of the options that control how data is used by the algorithm are set automatically.</span></span> <span data-ttu-id="5af71-173">ただし、既存のモデルに新しいモデルを追加する場合は、これらのオプションを手動で確認し、データを分析に使用するかどうか、データ型が正しいかどうかなどを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5af71-173">However, when you add a new model to an existing, you need to see these options manually, and specify whether data should be used for analysis, whether the data type is correct, and so forth.</span></span>  
  
 <span data-ttu-id="5af71-174">新しいアルゴリズムを既存のデータに適用すると、エラー メッセージが表示されることがありますが、これらは一般的に、モデルを処理するために必要な修正に関する詳細情報を提供するメッセージです。</span><span class="sxs-lookup"><span data-stu-id="5af71-174">You might get error messages when applying new algorithms to existing data, but these messages generally provide detailed information about the corrections you need to make to allow the model to be processed.</span></span> <span data-ttu-id="5af71-175">一般的な問題を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5af71-175">Typical problems include the following:</span></span>  
  
-   <span data-ttu-id="5af71-176">モデルがその構造に含まれているデータ型とは異なるデータ型を必要としている。</span><span class="sxs-lookup"><span data-stu-id="5af71-176">The model expects a different data type than the structure contains.</span></span>  
  
     <span data-ttu-id="5af71-177">アルゴリズムには、数字のみを使用できるものや、テキストのみを使用できるものがあります。</span><span class="sxs-lookup"><span data-stu-id="5af71-177">Some algorithms can only work with numbers; some can only work with text.</span></span> <span data-ttu-id="5af71-178">データが新しいモデルに対して無効な型である場合、モデルで処理できるように構造を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5af71-178">If your data is the wrong type for the new model, you might need to modify the structure to enable the model to process.</span></span>  
  
-   <span data-ttu-id="5af71-179">マイニング構造に予測可能な属性が含まれていない。</span><span class="sxs-lookup"><span data-stu-id="5af71-179">The mining structure contains no predictable attribute.</span></span>  
  
     <span data-ttu-id="5af71-180">クラスター モデルは予測可能な値を指定せずに作成できますが、その他のモデルは通常、予測に使用する単一列を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5af71-180">Clustering models can be built with no predictable value, but other models generally require that you specify a single column for prediction.</span></span>  
  
-   <span data-ttu-id="5af71-181">データの構成は、選択したアルゴリズムと互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="5af71-181">The composition of the data is incompatible with the algorithm you've chosen.</span></span>  
  
     <span data-ttu-id="5af71-182">分析の種類によっては、一意の規則に従って慎重に構造化されたデータが必要です。</span><span class="sxs-lookup"><span data-stu-id="5af71-182">Some types of analysis require data that is carefully structured according to unique rules.</span></span> <span data-ttu-id="5af71-183">例として、予測モデル、アソシエーション モデルなどがあります。</span><span class="sxs-lookup"><span data-stu-id="5af71-183">Examples are forecasting models and association models.</span></span> <span data-ttu-id="5af71-184">たとえば、カスタマイズを行って同じ種類の新しいモデルを簡単に追加できますが、データが他のアルゴリズムでは動作しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="5af71-184">You can easily add new models of the same type, perhaps with customizations, but the data might not work with other algorithms.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="5af71-185">必要条件</span><span class="sxs-lookup"><span data-stu-id="5af71-185">Requirements</span></span>  
 <span data-ttu-id="5af71-186">データ マイニング モデルを作成するには、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5af71-186">To create data mining models, you must have a connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="5af71-187">接続を作成または変更する方法の詳細については、「 [Connect To Source data &#40;Excel 用データマイニングクライアント&#41;](connect-to-source-data-data-mining-client-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5af71-187">For more information about how to create or change a connection, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
 <span data-ttu-id="5af71-188">必要なデータ マイニング構造が表示されない場合、その構造が別のインスタンスまたは別の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに保存されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5af71-188">If you cannot see the data mining structure that you want, it could be that the structure was saved to a different instance or different [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="5af71-189">別のデータマイニング接続に変更する方法の詳細については、「[データマイニングサーバーへの接続](connect-to-a-data-mining-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5af71-189">For information about how to change to a different data mining connection, see [Connect to a Data Mining Server](connect-to-a-data-mining-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5af71-190">参照</span><span class="sxs-lookup"><span data-stu-id="5af71-190">See Also</span></span>  
 [<span data-ttu-id="5af71-191">データ マイニング モデルの作成</span><span class="sxs-lookup"><span data-stu-id="5af71-191">Creating a Data Mining Model</span></span>](creating-a-data-mining-model.md)   
