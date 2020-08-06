---
title: ニューラルネットワークの構造とモデルの作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- discretization [Analysis Services]
- DISCRETIZED column
- DiscretizationBuckets property
- DiscretizationMethod property
- EQUAL_AREAS method
ms.assetid: 3f16215c-531e-4ecf-a11f-ee7c6a764463
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 91c0210213083868eaab36cf34a05d0b7824a654
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632234"
---
# <a name="creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="f0d9b-102">ニューラル ネットワーク構造およびモデルの作成 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="f0d9b-102">Creating a Neural Network Structure and Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="f0d9b-103">データ マイニング モデルを作成するには、まずデータ マイニング ウィザードを使用して、新しいデータ ソース ビューに基づく新しいマイニング構造を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-103">To create a data mining model, you must first use the Data Mining Wizard to create a new mining structure based on the new data source view.</span></span> <span data-ttu-id="f0d9b-104">ここでは、ウィザードを使用してマイニング構造を作成し、同時に、[!INCLUDE[msCoName](../includes/msconame-md.md)] ニューラル ネットワーク アルゴリズムに基づく関連マイニング モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-104">In this task you will use the wizard to create a mining structure, and at the same time create an associated mining model that is based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Neural Network algorithm.</span></span>  
  
 <span data-ttu-id="f0d9b-105">ニューラル ネットワークは高い柔軟性を持ち、さまざまな入力と出力の組み合わせを分析できるため、最良の結果を得るためにはいくつかのデータ処理方法を試す必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-105">Because neural networks are extremely flexible and can analyze many combinations of inputs and outputs, you should experiment with several ways of processing the data to get the best results.</span></span> <span data-ttu-id="f0d9b-106">たとえば、特定のビジネス要件を対象とし*て、サービス*品質の数値ターゲットをビン分割またはグループ化する方法をカスタマイズすることができます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-106">For example, you might want to customize the way that the numerical target for service quality is *binned*, or grouped, to target specific business requirements.</span></span> <span data-ttu-id="f0d9b-107">そのためには、数値データを別の方法でグループ化する新しい列をマイニング構造に追加して、その新しい列を使用するモデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-107">To do this, you will add a new column to the mining structure that groups numerical data in a different way, and then create a model that uses the new column.</span></span> <span data-ttu-id="f0d9b-108">その後、それらのマイニング モデルを使用して探索を行います。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-108">You will use these mining models to do some exploration.</span></span>  
  
 <span data-ttu-id="f0d9b-109">実務上の目的に最も大きい影響を与える要因がニューラル ネットワーク モデルからわかったら、最後に、予測およびスコアリングのための別のモデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-109">Finally, when you have learned from the neural network model which factors have the greatest impact for your business question, you will build a separate model for prediction and scoring.</span></span> <span data-ttu-id="f0d9b-110">そのためには、[!INCLUDE[msCoName](../includes/msconame-md.md)] ロジスティック回帰アルゴリズムを使用します。このアルゴリズムは、ニューラル ネットワーク モデルが基になっていますが、特定の入力に基づくソリューションの検索用に最適化されています。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-110">You will use the [!INCLUDE[msCoName](../includes/msconame-md.md)] Logistic Regression algorithm, which is based on the neural networks model but is optimized for finding a solution based on specific inputs.</span></span>  
  
 <span data-ttu-id="f0d9b-111">**手順**</span><span class="sxs-lookup"><span data-stu-id="f0d9b-111">**Steps**</span></span>  
  
 [<span data-ttu-id="f0d9b-112">既定のマイニング構造とモデルを作成する</span><span class="sxs-lookup"><span data-stu-id="f0d9b-112">Create the default mining structure and model</span></span>](#bkmk_defaul)  
  
 [<span data-ttu-id="f0d9b-113">分離を使用して予測可能列をビン分割する</span><span class="sxs-lookup"><span data-stu-id="f0d9b-113">Use discretization to bin the predictable column</span></span>](#bkmk_ColumnCopy)  
  
 [<span data-ttu-id="f0d9b-114">列をコピーして別のモデル用に分離メソッドを変更する</span><span class="sxs-lookup"><span data-stu-id="f0d9b-114">Copy the column and change the discretization method for a different model</span></span>](#bkmk_Alias)  
  
 [<span data-ttu-id="f0d9b-115">モデルを比較できるように予測可能列の別名を作成する</span><span class="sxs-lookup"><span data-stu-id="f0d9b-115">Create an alias for the predictable column so that you can compare models</span></span>](#bkmk_Alias2)  
  
 [<span data-ttu-id="f0d9b-116">すべてのモデルの処理</span><span class="sxs-lookup"><span data-stu-id="f0d9b-116">Process all models</span></span>](#bkmk_SeedProcess)  
  
## <a name="create-the-default-call-center-structure"></a><span data-ttu-id="f0d9b-117">既定のコールセンター構造を作成する<a name="bkmk_defaul"></a></span><span class="sxs-lookup"><span data-stu-id="f0d9b-117">Create the Default Call Center Structure  <a name="bkmk_defaul"></a></span></span>  
  
1.  <span data-ttu-id="f0d9b-118">のソリューションエクスプローラーで [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 、[**マイニング構造**] を右クリックし、[**新しいマイニング構造**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-118">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], right-click **Mining Structures** and select **New Mining Structure**.</span></span>  
  
2.  <span data-ttu-id="f0d9b-119">**[データ マイニング ウィザードへようこそ]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-119">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="f0d9b-120">[**定義方法の選択**] ページで、[**既存のリレーショナルデータベースまたはデータウェアハウスから**] が選択されていることを確認し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-120">On the **Select the Definition Method** page, verify that **From existing relational database or data warehouse** is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="f0d9b-121">[**データマイニング構造の作成**] ページで、[**マイニングモデルを含むマイニング構造を作成**する] オプションが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-121">On the **Create the Data Mining Structure** page, verify that the option **Create mining structure with a mining model** is selected.</span></span>  
  
5.  <span data-ttu-id="f0d9b-122">[**使用するデータマイニング技法**を選択してください] のドロップダウンリストをクリックし、[ **Microsoft ニューラルネットワーク**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-122">Click the dropdown list for the option **Which data mining technique do you want to use?**, then select **Microsoft Neural Networks**.</span></span>  
  
     <span data-ttu-id="f0d9b-123">ロジスティック回帰モデルはニューラル ネットワークに基づくため、同じ構造を再利用して新しいマイニング モデルを追加できます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-123">Because the logistic regression models are based on the neural networks, you can reuse the same structure and add a new mining model.</span></span>  
  
6.  <span data-ttu-id="f0d9b-124">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-124">Click **Next**.</span></span>  
  
     <span data-ttu-id="f0d9b-125">**[データソースビューの選択**] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-125">The **Select Data Source View** page appears.</span></span>  
  
7.  <span data-ttu-id="f0d9b-126">[**使用できるデータソースビュー**] で、[] を選択 `Call Center` し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-126">Under **Available data source views**, select `Call Center`, and click **Next**.</span></span>  
  
8.  <span data-ttu-id="f0d9b-127">[**テーブルの種類の指定**] ページで、 **FactCallCenter**テーブルの横にある [**ケース**] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-127">On the **Specify Table Types** page, select the **Case** check box next to the **FactCallCenter** table.</span></span> <span data-ttu-id="f0d9b-128">**DimDate**に対しては何も選択しないでください。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-128">Do not select anything for **DimDate**.</span></span> <span data-ttu-id="f0d9b-129">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-129">Click **Next**.</span></span>  
  
9. <span data-ttu-id="f0d9b-130">[**トレーニングデータの指定**] ページで、[FactCallCenterID] 列の横にある [**キー** ] を選択し**ます。**</span><span class="sxs-lookup"><span data-stu-id="f0d9b-130">On the **Specify the Training Data** page, select **Key** next to the column **FactCallCenterID.**</span></span>  
  
10. <span data-ttu-id="f0d9b-131">[] `Predict` および [**入力**] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-131">Select the `Predict` and **Input** check boxes.</span></span>  
  
11. <span data-ttu-id="f0d9b-132">次の表に示すように、[**キー**]、[**入力**]、および [チェック] チェックボックスをオンにし `Predict` ます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-132">Select the **Key**, **Input**, and `Predict` check boxes as shown in the following table:</span></span>  
  
    |<span data-ttu-id="f0d9b-133">テーブルまたは列</span><span class="sxs-lookup"><span data-stu-id="f0d9b-133">Tables/Columns</span></span>|<span data-ttu-id="f0d9b-134">[キー]/[入力]/[予測]</span><span class="sxs-lookup"><span data-stu-id="f0d9b-134">Key/Input/Predict</span></span>|  
    |---------------------|-------------------------|  
    |<span data-ttu-id="f0d9b-135">AutomaticResponses</span><span class="sxs-lookup"><span data-stu-id="f0d9b-135">AutomaticResponses</span></span>|<span data-ttu-id="f0d9b-136">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-136">Input</span></span>|  
    |<span data-ttu-id="f0d9b-137">AverageTimePerIssue</span><span class="sxs-lookup"><span data-stu-id="f0d9b-137">AverageTimePerIssue</span></span>|<span data-ttu-id="f0d9b-138">[入力]/[予測]</span><span class="sxs-lookup"><span data-stu-id="f0d9b-138">Input/Predict</span></span>|  
    |<span data-ttu-id="f0d9b-139">呼び出し</span><span class="sxs-lookup"><span data-stu-id="f0d9b-139">Calls</span></span>|<span data-ttu-id="f0d9b-140">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-140">Input</span></span>|  
    |<span data-ttu-id="f0d9b-141">DateKey</span><span class="sxs-lookup"><span data-stu-id="f0d9b-141">DateKey</span></span>|<span data-ttu-id="f0d9b-142">使用しない</span><span class="sxs-lookup"><span data-stu-id="f0d9b-142">Do not use</span></span>|  
    |<span data-ttu-id="f0d9b-143">DayOfWeek</span><span class="sxs-lookup"><span data-stu-id="f0d9b-143">DayOfWeek</span></span>|<span data-ttu-id="f0d9b-144">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-144">Input</span></span>|  
    |<span data-ttu-id="f0d9b-145">FactCallCenterID</span><span class="sxs-lookup"><span data-stu-id="f0d9b-145">FactCallCenterID</span></span>|<span data-ttu-id="f0d9b-146">Key</span><span class="sxs-lookup"><span data-stu-id="f0d9b-146">Key</span></span>|  
    |<span data-ttu-id="f0d9b-147">IssuesRaised</span><span class="sxs-lookup"><span data-stu-id="f0d9b-147">IssuesRaised</span></span>|<span data-ttu-id="f0d9b-148">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-148">Input</span></span>|  
    |<span data-ttu-id="f0d9b-149">LevelOneOperators</span><span class="sxs-lookup"><span data-stu-id="f0d9b-149">LevelOneOperators</span></span>|<span data-ttu-id="f0d9b-150">[入力]/[予測]</span><span class="sxs-lookup"><span data-stu-id="f0d9b-150">Input/Predict</span></span>|  
    |<span data-ttu-id="f0d9b-151">LevelTwoOperators</span><span class="sxs-lookup"><span data-stu-id="f0d9b-151">LevelTwoOperators</span></span>|<span data-ttu-id="f0d9b-152">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-152">Input</span></span>|  
    |<span data-ttu-id="f0d9b-153">Orders</span><span class="sxs-lookup"><span data-stu-id="f0d9b-153">Orders</span></span>|<span data-ttu-id="f0d9b-154">[入力]/[予測]</span><span class="sxs-lookup"><span data-stu-id="f0d9b-154">Input/Predict</span></span>|  
    |<span data-ttu-id="f0d9b-155">ServiceGrade</span><span class="sxs-lookup"><span data-stu-id="f0d9b-155">ServiceGrade</span></span>|<span data-ttu-id="f0d9b-156">[入力]/[予測]</span><span class="sxs-lookup"><span data-stu-id="f0d9b-156">Input/Predict</span></span>|  
    |<span data-ttu-id="f0d9b-157">シフト</span><span class="sxs-lookup"><span data-stu-id="f0d9b-157">Shift</span></span>|<span data-ttu-id="f0d9b-158">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-158">Input</span></span>|  
    |<span data-ttu-id="f0d9b-159">TotalOperators</span><span class="sxs-lookup"><span data-stu-id="f0d9b-159">TotalOperators</span></span>|<span data-ttu-id="f0d9b-160">使用しない</span><span class="sxs-lookup"><span data-stu-id="f0d9b-160">Do not use</span></span>|  
    |<span data-ttu-id="f0d9b-161">WageType</span><span class="sxs-lookup"><span data-stu-id="f0d9b-161">WageType</span></span>|<span data-ttu-id="f0d9b-162">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-162">Input</span></span>|  
  
     <span data-ttu-id="f0d9b-163">予測可能列が複数選択されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-163">Note that multiple predictable columns have been selected.</span></span> <span data-ttu-id="f0d9b-164">ニューラル ネットワーク アルゴリズムには、入力属性と出力属性のあらゆる組み合わせを分析できるという利点があります。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-164">One of the strengths of the neural network algorithm is that it can analyze all possible combinations of input and output attributes.</span></span> <span data-ttu-id="f0d9b-165">処理時間が指数関数的に増加する可能性があるため、大きなデータセットに対してこれを行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-165">You wouldn't want to do this for a large data set, as it could exponentially increase processing time..</span></span>  
  
12. <span data-ttu-id="f0d9b-166">[**列のコンテンツおよびデータ型の指定**] ページで、次の表に示すように、グリッドに列、コンテンツの種類、およびデータ型が含まれていることを確認し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-166">On the **Specify Columns' Content and Data Type** page, verify that the grid contains the columns, content types, and data types as shown in the following table, and then click **Next**.</span></span>  
  
    |<span data-ttu-id="f0d9b-167">[列]</span><span class="sxs-lookup"><span data-stu-id="f0d9b-167">Columns</span></span>|<span data-ttu-id="f0d9b-168">コンテンツの種類</span><span class="sxs-lookup"><span data-stu-id="f0d9b-168">Content Type</span></span>|<span data-ttu-id="f0d9b-169">データ型</span><span class="sxs-lookup"><span data-stu-id="f0d9b-169">Data Types</span></span>|  
    |-------------|------------------|----------------|  
    |<span data-ttu-id="f0d9b-170">AutomaticResponses</span><span class="sxs-lookup"><span data-stu-id="f0d9b-170">AutomaticResponses</span></span>|<span data-ttu-id="f0d9b-171">継続的</span><span class="sxs-lookup"><span data-stu-id="f0d9b-171">Continuous</span></span>|<span data-ttu-id="f0d9b-172">Long</span><span class="sxs-lookup"><span data-stu-id="f0d9b-172">Long</span></span>|  
    |<span data-ttu-id="f0d9b-173">AverageTimePerIssue</span><span class="sxs-lookup"><span data-stu-id="f0d9b-173">AverageTimePerIssue</span></span>|<span data-ttu-id="f0d9b-174">継続的</span><span class="sxs-lookup"><span data-stu-id="f0d9b-174">Continuous</span></span>|<span data-ttu-id="f0d9b-175">Long</span><span class="sxs-lookup"><span data-stu-id="f0d9b-175">Long</span></span>|  
    |<span data-ttu-id="f0d9b-176">呼び出し</span><span class="sxs-lookup"><span data-stu-id="f0d9b-176">Calls</span></span>|<span data-ttu-id="f0d9b-177">継続的</span><span class="sxs-lookup"><span data-stu-id="f0d9b-177">Continuous</span></span>|<span data-ttu-id="f0d9b-178">Long</span><span class="sxs-lookup"><span data-stu-id="f0d9b-178">Long</span></span>|  
    |<span data-ttu-id="f0d9b-179">DayOfWeek</span><span class="sxs-lookup"><span data-stu-id="f0d9b-179">DayOfWeek</span></span>|<span data-ttu-id="f0d9b-180">離散</span><span class="sxs-lookup"><span data-stu-id="f0d9b-180">Discrete</span></span>|<span data-ttu-id="f0d9b-181">Text</span><span class="sxs-lookup"><span data-stu-id="f0d9b-181">Text</span></span>|  
    |<span data-ttu-id="f0d9b-182">FactCallCenterID</span><span class="sxs-lookup"><span data-stu-id="f0d9b-182">FactCallCenterID</span></span>|<span data-ttu-id="f0d9b-183">Key</span><span class="sxs-lookup"><span data-stu-id="f0d9b-183">Key</span></span>|<span data-ttu-id="f0d9b-184">Long</span><span class="sxs-lookup"><span data-stu-id="f0d9b-184">Long</span></span>|  
    |<span data-ttu-id="f0d9b-185">IssuesRaised</span><span class="sxs-lookup"><span data-stu-id="f0d9b-185">IssuesRaised</span></span>|<span data-ttu-id="f0d9b-186">継続的</span><span class="sxs-lookup"><span data-stu-id="f0d9b-186">Continuous</span></span>|<span data-ttu-id="f0d9b-187">Long</span><span class="sxs-lookup"><span data-stu-id="f0d9b-187">Long</span></span>|  
    |<span data-ttu-id="f0d9b-188">LevelOneOperators</span><span class="sxs-lookup"><span data-stu-id="f0d9b-188">LevelOneOperators</span></span>|<span data-ttu-id="f0d9b-189">継続的</span><span class="sxs-lookup"><span data-stu-id="f0d9b-189">Continuous</span></span>|<span data-ttu-id="f0d9b-190">Long</span><span class="sxs-lookup"><span data-stu-id="f0d9b-190">Long</span></span>|  
    |<span data-ttu-id="f0d9b-191">LevelTwoOperators</span><span class="sxs-lookup"><span data-stu-id="f0d9b-191">LevelTwoOperators</span></span>|<span data-ttu-id="f0d9b-192">継続的</span><span class="sxs-lookup"><span data-stu-id="f0d9b-192">Continuous</span></span>|<span data-ttu-id="f0d9b-193">Long</span><span class="sxs-lookup"><span data-stu-id="f0d9b-193">Long</span></span>|  
    |<span data-ttu-id="f0d9b-194">Orders</span><span class="sxs-lookup"><span data-stu-id="f0d9b-194">Orders</span></span>|<span data-ttu-id="f0d9b-195">継続的</span><span class="sxs-lookup"><span data-stu-id="f0d9b-195">Continuous</span></span>|<span data-ttu-id="f0d9b-196">Long</span><span class="sxs-lookup"><span data-stu-id="f0d9b-196">Long</span></span>|  
    |<span data-ttu-id="f0d9b-197">ServiceGrade</span><span class="sxs-lookup"><span data-stu-id="f0d9b-197">ServiceGrade</span></span>|<span data-ttu-id="f0d9b-198">継続的</span><span class="sxs-lookup"><span data-stu-id="f0d9b-198">Continuous</span></span>|<span data-ttu-id="f0d9b-199">Double</span><span class="sxs-lookup"><span data-stu-id="f0d9b-199">Double</span></span>|  
    |<span data-ttu-id="f0d9b-200">シフト</span><span class="sxs-lookup"><span data-stu-id="f0d9b-200">Shift</span></span>|<span data-ttu-id="f0d9b-201">離散</span><span class="sxs-lookup"><span data-stu-id="f0d9b-201">Discrete</span></span>|<span data-ttu-id="f0d9b-202">Text</span><span class="sxs-lookup"><span data-stu-id="f0d9b-202">Text</span></span>|  
    |<span data-ttu-id="f0d9b-203">WageType</span><span class="sxs-lookup"><span data-stu-id="f0d9b-203">WageType</span></span>|<span data-ttu-id="f0d9b-204">離散</span><span class="sxs-lookup"><span data-stu-id="f0d9b-204">Discrete</span></span>|<span data-ttu-id="f0d9b-205">Text</span><span class="sxs-lookup"><span data-stu-id="f0d9b-205">Text</span></span>|  
  
13. <span data-ttu-id="f0d9b-206">[**テストセットの作成**] ページで、[**テスト用データの割合**] オプションのテキストボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-206">On the **Create testing set** page, clear the text box for the option, **Percentage of data for testing**.</span></span> <span data-ttu-id="f0d9b-207">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-207">Click **Next**.</span></span>  
  
14. <span data-ttu-id="f0d9b-208">[**ウィザードの完了**] ページで、[**マイニング構造名**] に「」と入力 `Call Center` します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-208">On the **Completing the Wizard** page, for the **Mining structure name**, type `Call Center`.</span></span>  
  
15. <span data-ttu-id="f0d9b-209">[**マイニングモデル名**] に「 `Call Center Default NN` 」と入力し、[**完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-209">For the **Mining model name**, type `Call Center Default NN`, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="f0d9b-210">[**ドリル**スルーを許可する] ボックスは、ニューラルネットワークモデルを使用してデータにドリルスルーすることはできないため、無効になっています。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-210">The **Allow drill through** box is disabled because you cannot drill through to data with neural network models.</span></span>  
  
16. <span data-ttu-id="f0d9b-211">ソリューションエクスプローラーで、先ほど作成したデータマイニング構造の名前を右クリックし、[**処理**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-211">In Solution Explorer, right-click the name of the data mining structure that you just created, and select **Process**.</span></span>  
  
## <a name="use-discretization-to-bin-the-target-column"></a><span data-ttu-id="f0d9b-212">分離を使用して対象列をビン分割する</span><span class="sxs-lookup"><span data-stu-id="f0d9b-212">Use Discretization to Bin the Target Column</span></span>  
 <span data-ttu-id="f0d9b-213">既定では、予測可能な数値属性を持つニューラル ネットワーク モデルを作成したとき、Microsoft ニューラル ネットワーク アルゴリズムではその属性は連続する数値として扱われます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-213">By default, when you create a neural network model that has a numeric predictable attribute, the Microsoft Neural Network algorithm treats the attribute as a continuous number.</span></span> <span data-ttu-id="f0d9b-214">たとえば、ServiceGrade 属性は、理論上は 0.00 (すべての電話に応答している状態) ～ 1.00 (すべての発信元が電話を切っている状態) の範囲の数値です。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-214">For example, the ServiceGrade attribute is a number that theoretically ranges from 0.00 (all calls are answered) to 1.00 (all callers hang up).</span></span> <span data-ttu-id="f0d9b-215">このデータセットにおいて、数値の分布は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-215">In this data set, the values have the following distribution:</span></span>  
  
 <span data-ttu-id="f0d9b-216">![サービス グレード値の分布](../../2014/tutorials/media/skt-service-grade-valuesc.gif "サービス グレード値の分布")</span><span class="sxs-lookup"><span data-stu-id="f0d9b-216">![distribution of service grade values](../../2014/tutorials/media/skt-service-grade-valuesc.gif "distribution of service grade values")</span></span>  
  
 <span data-ttu-id="f0d9b-217">その結果、モデルを処理したときに、その出力が期待どおりにグループ化されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-217">As a result, when you process the model the outputs might be grouped differently than you expect.</span></span> <span data-ttu-id="f0d9b-218">たとえば、クラスタリングを使用して最適な値グループを特定すると、アルゴリズムによって ServiceGrade の値が 0.0748051948-がのような範囲に分割されます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-218">For example, if you use clustering to identify the best groups of values, the algorithm divides the values in ServiceGrade into ranges such as this one: 0.0748051948 - 0.09716216215.</span></span> <span data-ttu-id="f0d9b-219">この分類は数学的には正確ですが、このような範囲がビジネス ユーザーにとって有意なものではない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-219">Although this grouping is mathematically accurate, such ranges might not be as meaningful to business users.</span></span>  
  
 <span data-ttu-id="f0d9b-220">この手順では、結果をわかりやすくするために、数値をグループ化し、数値データ列のコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-220">In this step, to make the result more intuitive, you'll group the numerical values differently, creating copies of the numerical data column.</span></span>  
  
### <a name="how-discretization-works"></a><span data-ttu-id="f0d9b-221">分離のしくみ</span><span class="sxs-lookup"><span data-stu-id="f0d9b-221">How Discretization Works</span></span>  
 <span data-ttu-id="f0d9b-222">Analysis Services には、数値データのビン分割や処理のためのさまざまな方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-222">Analysis Services provides a variety of methods for binning or processing numerical data.</span></span> <span data-ttu-id="f0d9b-223">次の表は、出力属性 ServiceGrade を次の 3 とおりの方法で処理した場合の結果の違いを示しています。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-223">The following table illustrates the differences between the results when the output attribute ServiceGrade has been processed three different ways:</span></span>  
  
-   <span data-ttu-id="f0d9b-224">連続する数値として処理する。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-224">Treating it as a continuous number.</span></span>  
  
-   <span data-ttu-id="f0d9b-225">アルゴリズムでクラスタリングを使用して値の最適な分配を特定する。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-225">Having the algorithm use clustering to identify the best arrangement of values.</span></span>  
  
-   <span data-ttu-id="f0d9b-226">Equal Areas メソッドを使用して数値をビン分割することを指定する。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-226">Specifying that the numbers be binned by the Equal Areas method.</span></span>  
  
 <span data-ttu-id="f0d9b-227">既定のモデル (連続)</span><span class="sxs-lookup"><span data-stu-id="f0d9b-227">Default model (continuous)</span></span>  
  
|<span data-ttu-id="f0d9b-228">値</span><span class="sxs-lookup"><span data-stu-id="f0d9b-228">VALUE</span></span>|<span data-ttu-id="f0d9b-229">SUPPORT</span><span class="sxs-lookup"><span data-stu-id="f0d9b-229">SUPPORT</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="f0d9b-230">Missing</span><span class="sxs-lookup"><span data-stu-id="f0d9b-230">Missing</span></span>|<span data-ttu-id="f0d9b-231">0</span><span class="sxs-lookup"><span data-stu-id="f0d9b-231">0</span></span>|  
|<span data-ttu-id="f0d9b-232">0.09875</span><span class="sxs-lookup"><span data-stu-id="f0d9b-232">0.09875</span></span>|<span data-ttu-id="f0d9b-233">120</span><span class="sxs-lookup"><span data-stu-id="f0d9b-233">120</span></span>|  
  
 <span data-ttu-id="f0d9b-234">クラスタリングによるビン分割</span><span class="sxs-lookup"><span data-stu-id="f0d9b-234">Binned by clustering</span></span>  
  
|<span data-ttu-id="f0d9b-235">値</span><span class="sxs-lookup"><span data-stu-id="f0d9b-235">VALUE</span></span>|<span data-ttu-id="f0d9b-236">SUPPORT</span><span class="sxs-lookup"><span data-stu-id="f0d9b-236">SUPPORT</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="f0d9b-237">\<0.0748051948</span><span class="sxs-lookup"><span data-stu-id="f0d9b-237">\< 0.0748051948</span></span>|<span data-ttu-id="f0d9b-238">34</span><span class="sxs-lookup"><span data-stu-id="f0d9b-238">34</span></span>|  
|<span data-ttu-id="f0d9b-239">0.0748051948-が</span><span class="sxs-lookup"><span data-stu-id="f0d9b-239">0.0748051948 - 0.09716216215</span></span>|<span data-ttu-id="f0d9b-240">27</span><span class="sxs-lookup"><span data-stu-id="f0d9b-240">27</span></span>|  
|<span data-ttu-id="f0d9b-241">が-0.13297297295</span><span class="sxs-lookup"><span data-stu-id="f0d9b-241">0.09716216215 - 0.13297297295</span></span>|<span data-ttu-id="f0d9b-242">39</span><span class="sxs-lookup"><span data-stu-id="f0d9b-242">39</span></span>|  
|<span data-ttu-id="f0d9b-243">0.13297297295 - 0.167499999975</span><span class="sxs-lookup"><span data-stu-id="f0d9b-243">0.13297297295 - 0.167499999975</span></span>|<span data-ttu-id="f0d9b-244">10</span><span class="sxs-lookup"><span data-stu-id="f0d9b-244">10</span></span>|  
|<span data-ttu-id="f0d9b-245">>= 0.167499999975</span><span class="sxs-lookup"><span data-stu-id="f0d9b-245">>= 0.167499999975</span></span>|<span data-ttu-id="f0d9b-246">10</span><span class="sxs-lookup"><span data-stu-id="f0d9b-246">10</span></span>|  
  
 <span data-ttu-id="f0d9b-247">Equal Areas メソッドによるビン分割</span><span class="sxs-lookup"><span data-stu-id="f0d9b-247">Binned by equal areas</span></span>  
  
|<span data-ttu-id="f0d9b-248">値</span><span class="sxs-lookup"><span data-stu-id="f0d9b-248">VALUE</span></span>|<span data-ttu-id="f0d9b-249">SUPPORT</span><span class="sxs-lookup"><span data-stu-id="f0d9b-249">SUPPORT</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="f0d9b-250">\<0.07</span><span class="sxs-lookup"><span data-stu-id="f0d9b-250">\< 0.07</span></span>|<span data-ttu-id="f0d9b-251">26</span><span class="sxs-lookup"><span data-stu-id="f0d9b-251">26</span></span>|  
|<span data-ttu-id="f0d9b-252">0.07 ~ 0.00</span><span class="sxs-lookup"><span data-stu-id="f0d9b-252">0.07 - 0.00</span></span>|<span data-ttu-id="f0d9b-253">22</span><span class="sxs-lookup"><span data-stu-id="f0d9b-253">22</span></span>|  
|<span data-ttu-id="f0d9b-254">0.09 ~ 0.11</span><span class="sxs-lookup"><span data-stu-id="f0d9b-254">0.09 - 0.11</span></span>|<span data-ttu-id="f0d9b-255">36</span><span class="sxs-lookup"><span data-stu-id="f0d9b-255">36</span></span>|  
|<span data-ttu-id="f0d9b-256">>= 0.12</span><span class="sxs-lookup"><span data-stu-id="f0d9b-256">>= 0.12</span></span>|<span data-ttu-id="f0d9b-257">36</span><span class="sxs-lookup"><span data-stu-id="f0d9b-257">36</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="f0d9b-258">これらの統計は、すべてのデータが処理された後のモデルのマージナル統計ノードから取得できます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-258">You can obtain these statistics from the marginal statistics node of the model, after all the data has been processed.</span></span> <span data-ttu-id="f0d9b-259">[最低限の統計] ノードの詳細については、「[ニューラルネットワークモデルのマイニングモデルコンテンツ &#40;Analysis Services データマイニング&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-259">For more information about the marginal statistics node, see [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="f0d9b-260">この表の "値" 列には、ServiceGrade の数値がどのように処理されたかが示されています。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-260">In this table, the VALUE column shows you how the number for ServiceGrade has been handled.</span></span> <span data-ttu-id="f0d9b-261">"サポート" 列には、その値またはその範囲に分類されたケースの数が示されています。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-261">The SUPPORT column shows you how many cases had that value, or that fell in that range.</span></span>  
  
-   <span data-ttu-id="f0d9b-262">**連続する数値の使用 (既定)**</span><span class="sxs-lookup"><span data-stu-id="f0d9b-262">**Use continuous numbers (default)**</span></span>  
  
     <span data-ttu-id="f0d9b-263">既定の方法を使用した場合、120 個の一意の値の結果が計算され、その平均値は 0.09875 になります。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-263">If you used the default method, the algorithm would compute outcomes for 120 distinct values, the mean value of which is 0.09875.</span></span> <span data-ttu-id="f0d9b-264">また、不足値の数も確認できます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-264">You can also see the number of missing values.</span></span>  
  
-   <span data-ttu-id="f0d9b-265">**クラスター化によるビン**</span><span class="sxs-lookup"><span data-stu-id="f0d9b-265">**Bin by clustering**</span></span>  
  
     <span data-ttu-id="f0d9b-266">Microsoft クラスタリング アルゴリズムでオプションの値のグループを特定する場合、ServiceGrade の値が 5 つの範囲にグループ化されます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-266">When you let the Microsoft Clustering algorithm determine the optional grouping of values, the algorithm would group the values for ServiceGrade into five (5) ranges.</span></span> <span data-ttu-id="f0d9b-267">"サポート" 列に示されているように、それぞれの範囲に分配されるケースの数は均等にはなりません。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-267">The number of cases in each range is not evenly distributed, as you can see from the support column.</span></span>  
  
-   <span data-ttu-id="f0d9b-268">**同じ領域ごとのビン**</span><span class="sxs-lookup"><span data-stu-id="f0d9b-268">**Bin by equal areas**</span></span>  
  
     <span data-ttu-id="f0d9b-269">この方法を選択した場合、等しいサイズのバケットに値が分配されてから、各範囲の上限と下限が変更されます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-269">When you choose this method, the algorithm forces the values into buckets of equal size, which in turn changes the upper and lower bounds of each range.</span></span> <span data-ttu-id="f0d9b-270">バケットの数は指定できますが、それぞれのバケットに含まれる値の数が数個だけにならないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-270">You can specify the number of buckets, but you want to avoid having two few values in any bucket.</span></span>  
  
 <span data-ttu-id="f0d9b-271">ビン分割オプションの詳細については、「[データマイニング&#41;メソッド &#40;分離する方法](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-271">For more information about binning options, see [Discretization Methods &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md).</span></span>  
  
 <span data-ttu-id="f0d9b-272">または、数値を使用する代わりに、サービスグレードを定義済みの対象範囲 ( **Best** (servicegrade servicegrade > 0.05) など) に分類し、 \<= 0.05), **Acceptable** (0.10 > **不適切**な (servicegrade >= 0.10) という個別の派生列を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-272">Alternatively, rather than using the numeric values, you could add a separate derived column that classifies the service grades into predefined target ranges, such as **Best** (ServiceGrade \<= 0.05), **Acceptable** (0.10 > ServiceGrade > 0.05), and **Poor** (ServiceGrade >= 0.10).</span></span>  
  
###  <a name="create-a-copy-of-a-column-and-change-the-discretization-method"></a><a name="bkmk_newColumn"></a><span data-ttu-id="f0d9b-273">列のコピーを作成し、分離メソッドを変更する</span><span class="sxs-lookup"><span data-stu-id="f0d9b-273">Create a Copy of a Column and Change the Discretization Method</span></span>  
 <span data-ttu-id="f0d9b-274">ターゲット属性 ServiceGrade を含むマイニング列のコピーを作成し、数値をグループ化する方法を変更します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-274">You'll make a copy of the mining column that contains the target attribute, ServiceGrade and change the way the numbers are grouped.</span></span> <span data-ttu-id="f0d9b-275">予測可能な属性を含め、マイニング構造の任意の列の複数のコピーを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-275">You can create multiple copies of any column in a mining structure, including the predictable attribute.</span></span>  
  
 <span data-ttu-id="f0d9b-276">このチュートリアルでは、Equal Areas 分離メソッドを使用して、バケット数を 4 に指定します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-276">For this tutorial, you will use the Equal Areas method of discretization, and specify four buckets.</span></span> <span data-ttu-id="f0d9b-277">結果のグループ化は、ビジネス ユーザーの興味の対象となるターゲット値に非常に近いものになります。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-277">The groupings that result from this method are fairly close to the target values of interest to your business users.</span></span>  
  
####  <a name="to-create-a-customized-copy-of-a-column-in-the-mining-structure"></a><a name="bkmk_ColumnCopy"></a><span data-ttu-id="f0d9b-278">マイニング構造に列のカスタマイズされたコピーを作成するには</span><span class="sxs-lookup"><span data-stu-id="f0d9b-278">To create a customized copy of a column in the mining structure</span></span>  
  
1.  <span data-ttu-id="f0d9b-279">ソリューション エクスプローラーで、作成したマイニング構造をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-279">In Solution Explorer, double-click the mining structure that you just created.</span></span>  
  
2.  <span data-ttu-id="f0d9b-280">[マイニング構造] タブで、[**マイニング構造列の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-280">In the Mining Structure tab, click **Add a mining structure column**.</span></span>  
  
3.  <span data-ttu-id="f0d9b-281">[**列の選択**] ダイアログボックスで、[**ソース] 列**の一覧から [servicegrade] を選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-281">In the **Select column** dialog box, select ServiceGrade from the list in **Source column**, then click **OK**.</span></span>  
  
     <span data-ttu-id="f0d9b-282">マイニング構造列の一覧に新しい列が追加されます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-282">A new column is added to the list of mining structure columns.</span></span> <span data-ttu-id="f0d9b-283">新しいマイニング列の既定の名前は、元の列と同じ名前に数値の接尾辞を付けたものです (例 : ServiceGrade 1)。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-283">By default, the new mining column has the same name as the existing column, with a numerical postfix: for example, ServiceGrade 1.</span></span> <span data-ttu-id="f0d9b-284">この列の名前を、よりわかりやすい名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-284">You can change the name of this column to be more descriptive.</span></span>  
  
     <span data-ttu-id="f0d9b-285">分離メソッドも指定します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-285">You will also specify the discretization method.</span></span>  
  
4.  <span data-ttu-id="f0d9b-286">[ServiceGrade 1] を右クリックし、[**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-286">Right-click ServiceGrade 1 and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="f0d9b-287">[**プロパティ**] ウィンドウで、 **name**プロパティを見つけ、名前を「 **Service グレード**ビン」に変更します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-287">In the **Properties** window, locate the **Name** property, and change the name to **Service Grade Binned** .</span></span>  
  
6.  <span data-ttu-id="f0d9b-288">関連するすべてのマイニング モデル列の名前を同じように変更するかどうかを確認するダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-288">A dialog box appears asking whether you want to make the same change to the name of all related mining model columns.</span></span> <span data-ttu-id="f0d9b-289">**[いいえ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-289">Click **No**.</span></span>  
  
7.  <span data-ttu-id="f0d9b-290">[**プロパティ**] ウィンドウで、セクションの [**データ型**] を見つけ、必要に応じて展開します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-290">In the **Properties** window, locate the section **Data Type** and expand it if necessary.</span></span>  
  
8.  <span data-ttu-id="f0d9b-291">`Content` プロパティの値を `Continuous` から `Discretized` に変更します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-291">Change the value of the property `Content` from `Continuous` to `Discretized`.</span></span>  
  
     <span data-ttu-id="f0d9b-292">次のプロパティが使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-292">The following properties are now available.</span></span> <span data-ttu-id="f0d9b-293">次の表に従ってプロパティの値を変更します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-293">Change the values of the properties as shown in the following table:</span></span>  
  
    |<span data-ttu-id="f0d9b-294">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f0d9b-294">Property</span></span>|<span data-ttu-id="f0d9b-295">既定値</span><span class="sxs-lookup"><span data-stu-id="f0d9b-295">Default value</span></span>|<span data-ttu-id="f0d9b-296">新しい値</span><span class="sxs-lookup"><span data-stu-id="f0d9b-296">New value</span></span>|  
    |--------------|-------------------|---------------|  
    |`DiscretizationMethod`|`Continuous`|`EqualAreas`|  
    |`DiscretizationBucketCount`|<span data-ttu-id="f0d9b-297">値なし</span><span class="sxs-lookup"><span data-stu-id="f0d9b-297">No value</span></span>|<span data-ttu-id="f0d9b-298">4</span><span class="sxs-lookup"><span data-stu-id="f0d9b-298">4</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="f0d9b-299"><xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> の既定値は実際は 0 です。これは、最適なバケット数がアルゴリズムによって自動的に決定されることを表します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-299">The default value of <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> is actually 0, which means that the algorithm automatically determines the optimum number of buckets.</span></span> <span data-ttu-id="f0d9b-300">したがって、このプロパティの値を既定値に戻すには、「0」と入力します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-300">Therefore, if you want to reset the value of this property to its default, type 0.</span></span>  
  
9. <span data-ttu-id="f0d9b-301">データマイニングデザイナーで、[**マイニングモデル**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-301">In Data Mining Designer, click the **Mining Models** tab.</span></span>  
  
     <span data-ttu-id="f0d9b-302">マイニング構造列のコピーを追加すると、そのコピーの使用法フラグが自動的に `Ignore` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-302">Notice that when you add a copy of a mining structure column, the usage flag for the copy is automatically set to `Ignore`.</span></span> <span data-ttu-id="f0d9b-303">マイニング構造に列のコピーを追加する場合、通常は、そのコピーを元の列と一緒に分析に使用することはありません。一緒に使用すると、アルゴリズムでその 2 つの列の間に強力な相関関係が検出されて、他の関係がわかりにくくなってしまう可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-303">Usually, when you add a copy of a column to a mining structure, you would not use the copy for analysis together with the original column, or the algorithm will find a strong correlation between the two columns that might obscure other relationships.</span></span>  
  
##  <a name="add-a-new-mining-model-to-the-mining-structure"></a><a name="bkmk_NewModel"></a><span data-ttu-id="f0d9b-304">マイニング構造への新しいマイニングモデルの追加</span><span class="sxs-lookup"><span data-stu-id="f0d9b-304">Add a New Mining Model to the Mining Structure</span></span>  
 <span data-ttu-id="f0d9b-305">対象となる属性の新しいグループ化を作成できたら、次に、その離散化列を使用する新しいマイニング モデルを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-305">Now that you have created a new grouping for the target attribute, you need to add a new mining model that uses the discretized column.</span></span> <span data-ttu-id="f0d9b-306">この手順が完了すると、CallCenter マイニング構造に次の 2 つのマイニング モデルが含まれるようになります。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-306">When you are done, the CallCenter mining structure will have two mining models:</span></span>  
  
-   <span data-ttu-id="f0d9b-307">ServiceGrade 値を連続する範囲として処理するマイニング モデル Call Center Default NN</span><span class="sxs-lookup"><span data-stu-id="f0d9b-307">The mining model, Call Center Default NN, handles the ServiceGrade values as a continuous range.</span></span>  
  
-   <span data-ttu-id="f0d9b-308">新しいマイニングモデルを作成します。これは、ターゲットとしてを使用し、ServiceGrade の列の値を、同じサイズの4つのバケットに分散して作成します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-308">You will create a new mining model, Call Center Binned NN, that uses as its target outcomes the values of the ServiceGrade column, distributed into four buckets of equal size.</span></span>  
  
#### <a name="to-add-a-mining-model-based-on-the-new-discretized-column"></a><span data-ttu-id="f0d9b-309">新しい離散化列に基づくマイニング モデルを追加するには</span><span class="sxs-lookup"><span data-stu-id="f0d9b-309">To add a mining model based on the new discretized column</span></span>  
  
1.  <span data-ttu-id="f0d9b-310">ソリューションエクスプローラーで、先ほど作成したマイニング構造を右クリックし、[**開く**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-310">In Solution Explorer, right-click the mining structure that you just created, and select **Open**.</span></span>  
  
2.  <span data-ttu-id="f0d9b-311">**[マイニング モデル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-311">Click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="f0d9b-312">[**関連マイニングモデルの作成] を**クリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-312">Click **Create a related mining model**.</span></span>  
  
4.  <span data-ttu-id="f0d9b-313">[**新しいマイニングモデル**] ダイアログボックスの [**モデル名**] に、「」と入力 `Call Center Binned NN` します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-313">In the **New Mining Model** dialog box, for **Model name**, type `Call Center Binned NN`.</span></span> <span data-ttu-id="f0d9b-314">[**アルゴリズム名**] ドロップダウンリストで、[ **Microsoft ニューラルネットワーク**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-314">In the **Algorithm name** dropdown list, select **Microsoft Neural Network**.</span></span>  
  
5.  <span data-ttu-id="f0d9b-315">新しいマイニング モデルに含まれる列の一覧で ServiceGrade を見つけて、使用法を `Predict` から `Ignore` に変更します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-315">In the list of columns contained in the new mining model, locate ServiceGrade, and change the usage from `Predict` to `Ignore`.</span></span>  
  
6.  <span data-ttu-id="f0d9b-316">同様に、ServiceGrade Binned を見つけて、使用法を `Ignore` から `Predict` に変更します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-316">Similarly, locate ServiceGrade Binned, and change the usage from `Ignore` to `Predict`.</span></span>  
  
##  <a name="create-an-alias-for-the-target-column"></a><a name="bkmk_Alias2"></a><span data-ttu-id="f0d9b-317">ターゲット列の別名を作成します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-317">Create an Alias for the Target Column</span></span>  
 <span data-ttu-id="f0d9b-318">通常は、別の予測可能な属性を使用するマイニング モデルを比較することはできませんが、</span><span class="sxs-lookup"><span data-stu-id="f0d9b-318">Ordinarily you cannot compare mining models that use different predictable attributes.</span></span> <span data-ttu-id="f0d9b-319">マイニング モデル列の別名を作成することができるため、</span><span class="sxs-lookup"><span data-stu-id="f0d9b-319">However, you can create an alias for a mining model column.</span></span> <span data-ttu-id="f0d9b-320">つまり、マイニングモデル内の ServiceGrade ビンの列の名前を変更して、元の列と同じ名前にすることができます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-320">That is, you can rename the column, ServiceGrade Binned, within the mining model so that it has the same name as the original column.</span></span> <span data-ttu-id="f0d9b-321">データが別の方法で分離されていても、この 2 つのモデルを精度チャートで直接比較することができます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-321">You can then directly compare these two models in an accuracy chart, even though the data is discretized differently.</span></span>  
  
###  <a name="to-add-an-alias-for-a-mining-structure-column-in-a-mining-model"></a><a name="bkmk_Alias"></a><span data-ttu-id="f0d9b-322">マイニングモデルのマイニング構造列に別名を追加するには</span><span class="sxs-lookup"><span data-stu-id="f0d9b-322">To add an alias for a mining structure column in a mining model</span></span>  
  
1.  <span data-ttu-id="f0d9b-323">[**マイニングモデル**] タブの [**構造**] で、[servicegrade ビン] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-323">In the **Mining Models** tab, under **Structure**, select ServiceGrade Binned.</span></span>  
  
     <span data-ttu-id="f0d9b-324">[**プロパティ**] ウィンドウに、scalarminingstructurecolumn 列のプロパティが表示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-324">Note that the **Properties** window displays the properties of the object, ScalarMiningStructure column.</span></span>  
  
2.  <span data-ttu-id="f0d9b-325">マイニング モデル ServiceGrade Binned NN の列で、ServiceGrade Binned 列に対応するセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-325">Under the column for the mining model, ServiceGrade Binned NN, click the cell corresponding to the column ServiceGrade Binned.</span></span>  
  
     <span data-ttu-id="f0d9b-326">これで、[**プロパティ**] ウィンドウに、MiningModelColumn オブジェクトのプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-326">Note that now the **Properties** window displays the properties for the object, MiningModelColumn.</span></span>  
  
3.  <span data-ttu-id="f0d9b-327">**Name**プロパティを見つけ、値をに変更し `ServiceGrade` ます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-327">Locate the **Name** property, and change the value to `ServiceGrade`.</span></span>  
  
4.  <span data-ttu-id="f0d9b-328">**Description**プロパティを見つけ、「 **Temporary column alias**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-328">Locate the **Description** property and type **Temporary column alias**.</span></span>  
  
     <span data-ttu-id="f0d9b-329">[**プロパティ**] ウィンドウには、次の情報が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-329">The **Properties** window should contain the following information:</span></span>  
  
    |<span data-ttu-id="f0d9b-330">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f0d9b-330">Property</span></span>|<span data-ttu-id="f0d9b-331">値</span><span class="sxs-lookup"><span data-stu-id="f0d9b-331">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="f0d9b-332">**説明**</span><span class="sxs-lookup"><span data-stu-id="f0d9b-332">**Description**</span></span>|<span data-ttu-id="f0d9b-333">Temporary column alias</span><span class="sxs-lookup"><span data-stu-id="f0d9b-333">Temporary column alias</span></span>|  
    |<span data-ttu-id="f0d9b-334">**ID**</span><span class="sxs-lookup"><span data-stu-id="f0d9b-334">**ID**</span></span>|<span data-ttu-id="f0d9b-335">ServiceGrade ビン分割</span><span class="sxs-lookup"><span data-stu-id="f0d9b-335">ServiceGrade Binned</span></span>|  
    |<span data-ttu-id="f0d9b-336">**ModelingFlags**</span><span class="sxs-lookup"><span data-stu-id="f0d9b-336">**Modeling Flags**</span></span>||  
    |<span data-ttu-id="f0d9b-337">**名前**</span><span class="sxs-lookup"><span data-stu-id="f0d9b-337">**Name**</span></span>|<span data-ttu-id="f0d9b-338">Service Grade</span><span class="sxs-lookup"><span data-stu-id="f0d9b-338">Service Grade</span></span>|  
    |<span data-ttu-id="f0d9b-339">**SourceColumn ID**</span><span class="sxs-lookup"><span data-stu-id="f0d9b-339">**SourceColumn ID**</span></span>|<span data-ttu-id="f0d9b-340">Service Grade 1</span><span class="sxs-lookup"><span data-stu-id="f0d9b-340">Service Grade 1</span></span>|  
    |<span data-ttu-id="f0d9b-341">**使用方法**</span><span class="sxs-lookup"><span data-stu-id="f0d9b-341">**Usage**</span></span>|<span data-ttu-id="f0d9b-342">Predict</span><span class="sxs-lookup"><span data-stu-id="f0d9b-342">Predict</span></span>|  
  
5.  <span data-ttu-id="f0d9b-343">[**マイニングモデル**] タブ内の任意の場所をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-343">Click anywhere in the **Mining Model** tab.</span></span>  
  
     <span data-ttu-id="f0d9b-344">グリッドが更新され、 `ServiceGrade` 列の使用法の横に新しい一時列の別名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-344">The grid is updated to show the new temporary column alias, `ServiceGrade`, beside the column usage.</span></span> <span data-ttu-id="f0d9b-345">マイニング構造と 2 つのマイニング モデルを含むグリッドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-345">The grid containing the mining structure and two mining models should look like the following:</span></span>  
  
    |<span data-ttu-id="f0d9b-346">構造体</span><span class="sxs-lookup"><span data-stu-id="f0d9b-346">Structure</span></span>|<span data-ttu-id="f0d9b-347">Call Center Default NN</span><span class="sxs-lookup"><span data-stu-id="f0d9b-347">Call Center Default NN</span></span>|<span data-ttu-id="f0d9b-348">Call Center Binned NN</span><span class="sxs-lookup"><span data-stu-id="f0d9b-348">Call Center Binned NN</span></span>|  
    |---------------|----------------------------|---------------------------|  
    ||<span data-ttu-id="f0d9b-349">Microsoft ニューラル ネットワーク</span><span class="sxs-lookup"><span data-stu-id="f0d9b-349">Microsoft Neural Network</span></span>|<span data-ttu-id="f0d9b-350">Microsoft ニューラル ネットワーク</span><span class="sxs-lookup"><span data-stu-id="f0d9b-350">Microsoft Neural Network</span></span>|  
    |<span data-ttu-id="f0d9b-351">AutomaticResponses</span><span class="sxs-lookup"><span data-stu-id="f0d9b-351">AutomaticResponses</span></span>|<span data-ttu-id="f0d9b-352">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-352">Input</span></span>|<span data-ttu-id="f0d9b-353">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-353">Input</span></span>|  
    |<span data-ttu-id="f0d9b-354">AverageTimePerIssue</span><span class="sxs-lookup"><span data-stu-id="f0d9b-354">AverageTimePerIssue</span></span>|<span data-ttu-id="f0d9b-355">Predict</span><span class="sxs-lookup"><span data-stu-id="f0d9b-355">Predict</span></span>|<span data-ttu-id="f0d9b-356">Predict</span><span class="sxs-lookup"><span data-stu-id="f0d9b-356">Predict</span></span>|  
    |<span data-ttu-id="f0d9b-357">呼び出し</span><span class="sxs-lookup"><span data-stu-id="f0d9b-357">Calls</span></span>|<span data-ttu-id="f0d9b-358">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-358">Input</span></span>|<span data-ttu-id="f0d9b-359">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-359">Input</span></span>|  
    |<span data-ttu-id="f0d9b-360">DayOfWeek</span><span class="sxs-lookup"><span data-stu-id="f0d9b-360">DayOfWeek</span></span>|<span data-ttu-id="f0d9b-361">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-361">Input</span></span>|<span data-ttu-id="f0d9b-362">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-362">Input</span></span>|  
    |<span data-ttu-id="f0d9b-363">FactCallCenterID</span><span class="sxs-lookup"><span data-stu-id="f0d9b-363">FactCallCenterID</span></span>|<span data-ttu-id="f0d9b-364">Key</span><span class="sxs-lookup"><span data-stu-id="f0d9b-364">Key</span></span>|<span data-ttu-id="f0d9b-365">Key</span><span class="sxs-lookup"><span data-stu-id="f0d9b-365">Key</span></span>|  
    |<span data-ttu-id="f0d9b-366">IssuesRaised</span><span class="sxs-lookup"><span data-stu-id="f0d9b-366">IssuesRaised</span></span>|<span data-ttu-id="f0d9b-367">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-367">Input</span></span>|<span data-ttu-id="f0d9b-368">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-368">Input</span></span>|  
    |<span data-ttu-id="f0d9b-369">LevelOneOperators</span><span class="sxs-lookup"><span data-stu-id="f0d9b-369">LevelOneOperators</span></span>|<span data-ttu-id="f0d9b-370">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-370">Input</span></span>|<span data-ttu-id="f0d9b-371">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-371">Input</span></span>|  
    |<span data-ttu-id="f0d9b-372">LevelTwoOperators</span><span class="sxs-lookup"><span data-stu-id="f0d9b-372">LevelTwoOperators</span></span>|<span data-ttu-id="f0d9b-373">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-373">Input</span></span>|<span data-ttu-id="f0d9b-374">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-374">Input</span></span>|  
    |<span data-ttu-id="f0d9b-375">Orders</span><span class="sxs-lookup"><span data-stu-id="f0d9b-375">Orders</span></span>|<span data-ttu-id="f0d9b-376">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-376">Input</span></span>|<span data-ttu-id="f0d9b-377">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-377">Input</span></span>|  
    |<span data-ttu-id="f0d9b-378">ServiceGrade Binned</span><span class="sxs-lookup"><span data-stu-id="f0d9b-378">ServceGrade Binned</span></span>|<span data-ttu-id="f0d9b-379">無視</span><span class="sxs-lookup"><span data-stu-id="f0d9b-379">Ignore</span></span>|<span data-ttu-id="f0d9b-380">Predict (ServiceGrade)</span><span class="sxs-lookup"><span data-stu-id="f0d9b-380">Predict (ServiceGrade)</span></span>|  
    |<span data-ttu-id="f0d9b-381">ServiceGrade</span><span class="sxs-lookup"><span data-stu-id="f0d9b-381">ServiceGrade</span></span>|<span data-ttu-id="f0d9b-382">Predict</span><span class="sxs-lookup"><span data-stu-id="f0d9b-382">Predict</span></span>|<span data-ttu-id="f0d9b-383">無視</span><span class="sxs-lookup"><span data-stu-id="f0d9b-383">Ignore</span></span>|  
    |<span data-ttu-id="f0d9b-384">シフト</span><span class="sxs-lookup"><span data-stu-id="f0d9b-384">Shift</span></span>|<span data-ttu-id="f0d9b-385">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-385">Input</span></span>|<span data-ttu-id="f0d9b-386">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-386">Input</span></span>|  
    |<span data-ttu-id="f0d9b-387">Total Operators</span><span class="sxs-lookup"><span data-stu-id="f0d9b-387">Total Operators</span></span>|<span data-ttu-id="f0d9b-388">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-388">Input</span></span>|<span data-ttu-id="f0d9b-389">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-389">Input</span></span>|  
    |<span data-ttu-id="f0d9b-390">WageType</span><span class="sxs-lookup"><span data-stu-id="f0d9b-390">WageType</span></span>|<span data-ttu-id="f0d9b-391">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-391">Input</span></span>|<span data-ttu-id="f0d9b-392">入力</span><span class="sxs-lookup"><span data-stu-id="f0d9b-392">Input</span></span>|  
  
## <a name="process-all-models"></a><span data-ttu-id="f0d9b-393">すべてのモデルを処理する</span><span class="sxs-lookup"><span data-stu-id="f0d9b-393">Process All Models</span></span>  
 <span data-ttu-id="f0d9b-394">最後に、作成したモデルを簡単に比較できるように、既定のモデルとビン分割モデルのシード パラメーターを設定します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-394">Finally, to ensure that the models you have created can be easily compared, you will set the seed parameter for both the default and binned models.</span></span> <span data-ttu-id="f0d9b-395">シード値を設定すると、各モデルで同じポイントからデータの処理が開始されるようになります。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-395">Setting a seed value guarantees that each model starts processing the data from the same point.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0d9b-396">シード パラメーターに数値を指定しなかった場合は、SQL Server Analysis Services により、モデルの名前に基づいてシードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-396">If you do not specify a numeric value for the seed parameter, SQL Server Analysis Services will generate a seed based on the name of the model.</span></span> <span data-ttu-id="f0d9b-397">モデルには必ず異なる名前が付けられるため、データが同じ順序で処理されるようにするにはシード値を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-397">Because the models always have different names, you must set a seed value to ensure that they process data in the same order.</span></span>  
  
###  <a name="to-specify-the-seed-and-process-the-models"></a><a name="bkmk_SeedProcess"></a><span data-ttu-id="f0d9b-398">シードを指定してモデルを処理するには</span><span class="sxs-lookup"><span data-stu-id="f0d9b-398">To specify the seed and process the models</span></span>  
  
1.  <span data-ttu-id="f0d9b-399">[**マイニングモデル**] タブで、Call CENTER-LR という名前のモデルの列を右クリックし、[**アルゴリズムパラメーターの設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-399">In the **Mining Model** tab, right-click the column for the model named Call Center - LR, and select **Set Algorithm Parameters**.</span></span>  
  
2.  <span data-ttu-id="f0d9b-400">HOLDOUT_SEED パラメーターの行で、[**値**] の下の空のセルをクリックし、「」と入力し `1` ます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-400">In the row for the HOLDOUT_SEED parameter, click the empty cell under **Value**, and type `1`.</span></span> <span data-ttu-id="f0d9b-401">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-401">Click **OK**.</span></span> <span data-ttu-id="f0d9b-402">構造に関連付けられている各モデルに対してこの手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-402">Repeat this step for each model associated with the structure.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f0d9b-403">関連するすべてのモデルで同じシードを使用する限り、シードとしてどのような値を選択するかは特に重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-403">The value that you choose as the seed does not matter, as long as you use the same seed for all related models.</span></span>  
  
3.  <span data-ttu-id="f0d9b-404">[**マイニングモデル**] メニューで、[**マイニング構造とすべてのモデルの処理**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-404">In the **Mining Models** menu, select **Process Mining Structure and All Models**.</span></span> <span data-ttu-id="f0d9b-405">[**はい**] をクリックして、更新されたデータマイニングプロジェクトをサーバーに配置します。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-405">Click **Yes** to deploy the updated data mining project to the server.</span></span>  
  
4.  <span data-ttu-id="f0d9b-406">[**マイニングモデルの処理**] ダイアログボックスで、[**実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-406">In the **Process Mining Model** dialog box, click **Run**.</span></span>  
  
5.  <span data-ttu-id="f0d9b-407">[**閉じる**] をクリックして [**処理の進行状況**] ダイアログボックスを閉じ、[**マイニングモデルの処理**] ダイアログボックスでもう一度 [**閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-407">Click **Close** to close the **Process Progress** dialog box, and then click **Close** again in the **Process Mining Model** dialog box.</span></span>  
  
 <span data-ttu-id="f0d9b-408">関連する 2 つのマイニング モデルを作成できたので、データを探索してデータの関係を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="f0d9b-408">Now that you have created the two related mining models, you will explore the data to discover relationships in the data.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="f0d9b-409">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="f0d9b-409">Next Task in Lesson</span></span>  
 [<span data-ttu-id="f0d9b-410">「&#40;中級者向けデータマイニングチュートリアル」のコールセンターモデルの調査&#41;</span><span class="sxs-lookup"><span data-stu-id="f0d9b-410">Exploring the Call Center Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-call-center-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="f0d9b-411">参照</span><span class="sxs-lookup"><span data-stu-id="f0d9b-411">See Also</span></span>  
 [<span data-ttu-id="f0d9b-412">マイニング構造 (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="f0d9b-412">Mining Structures &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)  
  
  
