---
title: マイニングモデルのドキュメント化 (Excel 用データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- documenting models
- mining structures, managing
- mining models, managing
- model properties
ms.assetid: 0a663e11-e40c-4708-ad18-fabb6c976fa4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 00d84f7ff1dc27d19d497dd11315d3efde603f60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644213"
---
# <a name="documenting-mining-models-data-mining-add-ins-for-excel"></a><span data-ttu-id="cb3d4-102">マイニング モデルのドキュメント化とスケーリング (Excel 用データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="cb3d4-102">Documenting Mining Models (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="cb3d4-103">![[データ マイニング] リボンの [モデルのドキュメント化] ボタン](media/dmc-docmodel.gif "[データ マイニング] リボンの [モデルのドキュメント化] ボタン")</span><span class="sxs-lookup"><span data-stu-id="cb3d4-103">![Document Model button, Data Mining ribbon](media/dmc-docmodel.gif "Document Model button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="cb3d4-104">**モデルのドキュメント**化ウィザードでは、作成したマイニングモデルに関する有用な情報を提供するレポートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-104">The **Document Model** wizard creates a report that provides useful information about the mining models that you have created.</span></span> <span data-ttu-id="cb3d4-105">作成したモデルをドキュメント化すると、モデルの生成に使用されるデータ ソースの追跡、モデルが処理された日時に関する詳細情報の取得、およびモデルの結果に影響するパラメーターの変更の追跡を実行できます。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-105">By documenting the models that you create, you can track the source of the data used to generate a model, get additional information about when the model was processed, and track parameter changes that affect the results of the model.</span></span>  
  
## <a name="using-the-document-model-wizard"></a><span data-ttu-id="cb3d4-106">モデルのドキュメント化ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="cb3d4-106">Using the Document Model Wizard</span></span>  
  
1.  <span data-ttu-id="cb3d4-107">[**データマイニング**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-107">Click the **Data Mining** tab.</span></span>  
  
2.  <span data-ttu-id="cb3d4-108">[**モデルの使用法**] グループで、[**モデルのドキュメント**化] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-108">In the **Model Usage** group, click **Document Model**.</span></span>  
  
3.  <span data-ttu-id="cb3d4-109">[**モデルの選択**] ダイアログボックスで、レポートを作成するモデルを選択し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-109">In the **Select Model** dialog box, select the model on which to report, and then click **Next**.</span></span> <span data-ttu-id="cb3d4-110">ドキュメント**モデル**ウィザードは、ドキュメント化するモデルごとに個別に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-110">You must run the **Document Model** wizard separately for each model that you want to document.</span></span>  
  
4.  <span data-ttu-id="cb3d4-111">**[ドキュメントの詳細の選択**] ダイアログボックスで、[**完全な情報**] または [**概要情報**] の2つのオプションのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-111">In the **Select documentation details** dialog box, choose one of two options: **Complete information** or **Summary information**.</span></span>  
  
5.  <span data-ttu-id="cb3d4-112">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-112">Click **Finish**.</span></span>  
  
6.  <span data-ttu-id="cb3d4-113">ウィザードにより、指定したレポートを含む新しいワークシートが自動的に作成されます。**モデルドキュメント**というタイトルの</span><span class="sxs-lookup"><span data-stu-id="cb3d4-113">The wizard automatically creates a new worksheet that contains the specified report, titled **Model Documentation**,</span></span>  
  
## <a name="understanding-the-report"></a><span data-ttu-id="cb3d4-114">レポートについて</span><span class="sxs-lookup"><span data-stu-id="cb3d4-114">Understanding the Report</span></span>  
 <span data-ttu-id="cb3d4-115">データ マイニング モデルをドキュメント化するレポートを作成する場合は、モデルの名前や説明などの基本的な情報を示すサマリー レポートか、基になる構造やマイニング モデルに関する詳細情報を示す完全なレポートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-115">When you create a report that documents a data mining model, you can create a summary,which contains basic information containing the name and description of the model, or a complete report, which contains details about the underlying structure and advanced information about the mining model.</span></span>  
  
 <span data-ttu-id="cb3d4-116">モデルの作成に使用したアルゴリズムに応じて、示される情報の種類が異なります。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-116">Depending on the algorithm that was used to create the model, different types of information is provided.</span></span> <span data-ttu-id="cb3d4-117">たとえば、アソシエーション モデルの場合は、生成されたアイテムセットおよびルールの数の把握に重点が置かれます。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-117">For example, in an association model, you are more interested in knowing the number of itemsets and rules that were generated.</span></span> <span data-ttu-id="cb3d4-118">クラスター モデルの場合は、クラスター数に重点が置かれます。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-118">For a clustering model, the number of clusters is more interesting.</span></span>  
  
 <span data-ttu-id="cb3d4-119">次の表に、オプションと各オプションのレポートで提供される情報を示します。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-119">The following table lists the options and the information that is provided in the report for each option.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cb3d4-120">レポート内の列は、既定で特定のサイズに設定されます。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-120">The columns in the report are set to a particular size by default.</span></span> <span data-ttu-id="cb3d4-121">したがって、列の名前または値が非常に長い場合、名前や値は表示されないか、Excel では ### と表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-121">Therefore, if any columns names or values are very long, they might not be visible, or might appear as ### in Excel.</span></span> <span data-ttu-id="cb3d4-122">値を表示するには、行のサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-122">To make the values visible, you can resize the row.</span></span> <span data-ttu-id="cb3d4-123">セルを選択し、両矢印をクリックして数式バーの右端までドラッグすると、値または文字列全体を表示できます。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-123">If the cell is selected, you can click and drag the double arrows at the right end of the formula bar to show the complete value or string.</span></span>  
  
### <a name="summary-report"></a><span data-ttu-id="cb3d4-124">サマリー レポート</span><span class="sxs-lookup"><span data-stu-id="cb3d4-124">Summary Report</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="cb3d4-125">**Metadata**</span><span class="sxs-lookup"><span data-stu-id="cb3d4-125">**Metadata**</span></span>|<span data-ttu-id="cb3d4-126">モデル名</span><span class="sxs-lookup"><span data-stu-id="cb3d4-126">Model name</span></span><br /><br /> <span data-ttu-id="cb3d4-127">モデルの説明</span><span class="sxs-lookup"><span data-stu-id="cb3d4-127">Model description</span></span><br /><br /> <span data-ttu-id="cb3d4-128">アルゴリズム名</span><span class="sxs-lookup"><span data-stu-id="cb3d4-128">Algorithm name</span></span><br /><br /> <span data-ttu-id="cb3d4-129">最終処理日</span><span class="sxs-lookup"><span data-stu-id="cb3d4-129">Date last processed</span></span>||  
|<span data-ttu-id="cb3d4-130">**モデルの結果**</span><span class="sxs-lookup"><span data-stu-id="cb3d4-130">**Model results**</span></span>|<span data-ttu-id="cb3d4-131">関連付け</span><span class="sxs-lookup"><span data-stu-id="cb3d4-131">Association</span></span>|<span data-ttu-id="cb3d4-132">アイテムセット数</span><span class="sxs-lookup"><span data-stu-id="cb3d4-132">Count of itemsets</span></span><br /><br /> <span data-ttu-id="cb3d4-133">ルール数</span><span class="sxs-lookup"><span data-stu-id="cb3d4-133">Count of rules</span></span>|  
||<span data-ttu-id="cb3d4-134">クラスタリング</span><span class="sxs-lookup"><span data-stu-id="cb3d4-134">Clustering</span></span>|<span data-ttu-id="cb3d4-135">クラスター数</span><span class="sxs-lookup"><span data-stu-id="cb3d4-135">Count of clusters</span></span><br /><br /> <span data-ttu-id="cb3d4-136">各クラスターのサポート</span><span class="sxs-lookup"><span data-stu-id="cb3d4-136">Support for each cluster</span></span>|  
||<span data-ttu-id="cb3d4-137">デシジョン ツリー</span><span class="sxs-lookup"><span data-stu-id="cb3d4-137">Decision tree</span></span>|<span data-ttu-id="cb3d4-138">ツリー数</span><span class="sxs-lookup"><span data-stu-id="cb3d4-138">Number of trees</span></span><br /><br /> <span data-ttu-id="cb3d4-139">各ツリーのノード数</span><span class="sxs-lookup"><span data-stu-id="cb3d4-139">Number of nodes in each tree</span></span>|  
||<span data-ttu-id="cb3d4-140">Linear regression (線形回帰)</span><span class="sxs-lookup"><span data-stu-id="cb3d4-140">Linear regression</span></span>|<span data-ttu-id="cb3d4-141">ツリー数 (常に 1)</span><span class="sxs-lookup"><span data-stu-id="cb3d4-141">Number of trees (always 1)</span></span><br /><br /> <span data-ttu-id="cb3d4-142">ノード数 (常に 1)</span><span class="sxs-lookup"><span data-stu-id="cb3d4-142">Number of nodes (always 1)</span></span>|  
||<span data-ttu-id="cb3d4-143">Naïve Bayes</span><span class="sxs-lookup"><span data-stu-id="cb3d4-143">Naïve Bayes</span></span>|<span data-ttu-id="cb3d4-144">重要な属性</span><span class="sxs-lookup"><span data-stu-id="cb3d4-144">Important attributes</span></span>|  
||<span data-ttu-id="cb3d4-145">ニューラル ネットワーク</span><span class="sxs-lookup"><span data-stu-id="cb3d4-145">Neural network</span></span>|<span data-ttu-id="cb3d4-146">入力ノード数</span><span class="sxs-lookup"><span data-stu-id="cb3d4-146">Number of input nodes</span></span><br /><br /> <span data-ttu-id="cb3d4-147">出力ノード数</span><span class="sxs-lookup"><span data-stu-id="cb3d4-147">Number of output nodes</span></span><br /><br /> <span data-ttu-id="cb3d4-148">隠しノード数</span><span class="sxs-lookup"><span data-stu-id="cb3d4-148">Number of hidden nodes</span></span>|  
||<span data-ttu-id="cb3d4-149">シーケンス クラスター</span><span class="sxs-lookup"><span data-stu-id="cb3d4-149">Sequence clustering</span></span>|<span data-ttu-id="cb3d4-150">クラスターの数</span><span class="sxs-lookup"><span data-stu-id="cb3d4-150">Number of clusters</span></span>|  
  
### <a name="complete-report"></a><span data-ttu-id="cb3d4-151">完全なレポート</span><span class="sxs-lookup"><span data-stu-id="cb3d4-151">Complete Report</span></span>  
 <span data-ttu-id="cb3d4-152">完全なレポートには、サマリー レポートに示されるすべての情報に加え、モデルで使用されるデータ列や分析の結果に関する詳細情報が示されます。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-152">The complete report contains everything that is in the summary report, plus  detailed information about the columns of data used in the model and the results of analysis:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="cb3d4-153">**Metadata**</span><span class="sxs-lookup"><span data-stu-id="cb3d4-153">**Metadata**</span></span>|<span data-ttu-id="cb3d4-154">モデルのメタデータ</span><span class="sxs-lookup"><span data-stu-id="cb3d4-154">Model metadata</span></span>|<span data-ttu-id="cb3d4-155">アルゴリズム パラメーターおよび値</span><span class="sxs-lookup"><span data-stu-id="cb3d4-155">Algorithm parameters and values</span></span>|  
||<span data-ttu-id="cb3d4-156">列のメタデータ</span><span class="sxs-lookup"><span data-stu-id="cb3d4-156">Column metadata</span></span>|<span data-ttu-id="cb3d4-157">列名</span><span class="sxs-lookup"><span data-stu-id="cb3d4-157">Column name</span></span><br /><br /> <span data-ttu-id="cb3d4-158">使用法</span><span class="sxs-lookup"><span data-stu-id="cb3d4-158">Usage</span></span><br /><br /> <span data-ttu-id="cb3d4-159">データ型</span><span class="sxs-lookup"><span data-stu-id="cb3d4-159">Data type</span></span><br /><br /> <span data-ttu-id="cb3d4-160">Content type</span><span class="sxs-lookup"><span data-stu-id="cb3d4-160">Content type</span></span><br /><br /> <span data-ttu-id="cb3d4-161">値 (不連続値の一覧または特定の範囲の値)</span><span class="sxs-lookup"><span data-stu-id="cb3d4-161">Values (list of discrete values, or range of values)</span></span>|  
|<span data-ttu-id="cb3d4-162">**モデルの統計**</span><span class="sxs-lookup"><span data-stu-id="cb3d4-162">**Model statistics**</span></span>|<span data-ttu-id="cb3d4-163">連続列</span><span class="sxs-lookup"><span data-stu-id="cb3d4-163">Continuous columns</span></span>|<span data-ttu-id="cb3d4-164">平均値</span><span class="sxs-lookup"><span data-stu-id="cb3d4-164">Mean value</span></span><br /><br /> <span data-ttu-id="cb3d4-165">最小値</span><span class="sxs-lookup"><span data-stu-id="cb3d4-165">Minimum value</span></span><br /><br /> <span data-ttu-id="cb3d4-166">最大値</span><span class="sxs-lookup"><span data-stu-id="cb3d4-166">Maximum value</span></span><br /><br /> <span data-ttu-id="cb3d4-167">2 乗平均平方根誤差</span><span class="sxs-lookup"><span data-stu-id="cb3d4-167">Root mean square error</span></span><br /><br /> <span data-ttu-id="cb3d4-168">平均絶対誤差</span><span class="sxs-lookup"><span data-stu-id="cb3d4-168">Mean absolute error</span></span><br /><br /> <span data-ttu-id="cb3d4-169">ログ スコア</span><span class="sxs-lookup"><span data-stu-id="cb3d4-169">Log score</span></span><br /><br /> <span data-ttu-id="cb3d4-170">回帰式 (線形回帰モデルのみ)。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-170">Regression formula (for linear regression models only)</span></span>|  
||<span data-ttu-id="cb3d4-171">不連続列</span><span class="sxs-lookup"><span data-stu-id="cb3d4-171">Discrete columns</span></span>|<span data-ttu-id="cb3d4-172">合格数</span><span class="sxs-lookup"><span data-stu-id="cb3d4-172">Count of passing</span></span><br /><br /> <span data-ttu-id="cb3d4-173">不合格数</span><span class="sxs-lookup"><span data-stu-id="cb3d4-173">Count of failing</span></span><br /><br /> <span data-ttu-id="cb3d4-174">ログ スコア</span><span class="sxs-lookup"><span data-stu-id="cb3d4-174">Log score</span></span><br /><br /> <span data-ttu-id="cb3d4-175">リフト</span><span class="sxs-lookup"><span data-stu-id="cb3d4-175">Lift</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="cb3d4-176">ドキュメント化できるのは、SQL Server Analysis Services でサポートされている種類のモデルです。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-176">You can document any model type that is supported by SQL Server Analysis Services.</span></span> <span data-ttu-id="cb3d4-177">したがって、この表に示されたモデルの中には、テーブル分析ツールまたはデータ マイニング クライアントのウィザードでは作成できない種類のモデルもあります。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-177">Therefore, the table lists some model types that cannot be created by using the Table Analysis Tools or by using the wizards in the Data Mining Client.</span></span> <span data-ttu-id="cb3d4-178">ただし、**高度なデータマイニングクエリエディター**を使用して、すべての種類のモデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-178">However, you can create all model types by using the **Advanced Data Mining Query Editor**.</span></span> <span data-ttu-id="cb3d4-179">詳細については、「[クエリ &#40;SQL Server データマイニングアドイン&#41;](query-sql-server-data-mining-add-ins.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-179">For more information, see [Query &#40;SQL Server Data Mining Add-ins&#41;](query-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb3d4-180">参照</span><span class="sxs-lookup"><span data-stu-id="cb3d4-180">See Also</span></span>  
 [<span data-ttu-id="cb3d4-181">Excel 用データマイニングアドイン &#40;のマイニングモデルの配置とスケーリング&#41;</span><span class="sxs-lookup"><span data-stu-id="cb3d4-181">Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;</span></span>](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
