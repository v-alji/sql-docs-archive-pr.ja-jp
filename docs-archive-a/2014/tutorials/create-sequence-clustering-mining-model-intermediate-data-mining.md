---
title: シーケンスクラスターマイニングモデル構造の作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e9339227-6c2e-4c4b-8be2-8c1960bc4a8d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 37d0a1738a758a9d8c4fd6b80310037937a9803f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634750"
---
# <a name="creating-a-sequence-clustering-mining-model-structure-intermediate-data-mining-tutorial"></a><span data-ttu-id="563ce-102">シーケンス クラスター マイニング モデル構造の作成 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="563ce-102">Creating a Sequence Clustering Mining Model Structure (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="563ce-103">シーケンス クラスター マイニング モデルを作成する最初の手順では、データ マイニング ウィザードを使用して新しいマイニング構造を作成し、[!INCLUDE[msCoName](../includes/msconame-md.md)] シーケンス クラスター アルゴリズムに基づくマイニング モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="563ce-103">The first step in creating a sequence clustering mining model is to use the Data Mining Wizard to create a new mining structure and a mining model based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering algorithm.</span></span>  
  
 <span data-ttu-id="563ce-104">マーケット バスケット分析に使用したものと同じデータ ソース ビューを使用しますが、`sequence` ID を格納する列を追加します。</span><span class="sxs-lookup"><span data-stu-id="563ce-104">You will use the same data source view that you used for the market basket analysis, but you will add a column that contains the `sequence` identifier.</span></span> <span data-ttu-id="563ce-105">このシナリオでは、シーケンスは、顧客が品目を買い物かごに追加した順序を表します。</span><span class="sxs-lookup"><span data-stu-id="563ce-105">In this scenario, the sequence means the order in which the customer added items to the shopping basket.</span></span>  
  
 <span data-ttu-id="563ce-106">統計データによって顧客を分類するためにいずれかのモデルで使用する列も追加します。</span><span class="sxs-lookup"><span data-stu-id="563ce-106">You will also add some columns that are used in one of the models to group customers by demographics.</span></span>  
  
### <a name="to-create-a-sequence-clustering-structure-and-model"></a><span data-ttu-id="563ce-107">シーケンス クラスターの構造とモデルを作成するには</span><span class="sxs-lookup"><span data-stu-id="563ce-107">To create a sequence clustering structure and model</span></span>  
  
1.  <span data-ttu-id="563ce-108">のソリューションエクスプローラーで [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 、[**マイニング構造**] を右クリックし、[**新しいマイニング構造**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="563ce-108">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], right-click **Mining Structures** and select **New Mining Structure**.</span></span>  
  
2.  <span data-ttu-id="563ce-109">**[データ マイニング ウィザードへようこそ]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="563ce-109">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="563ce-110">[**定義方法の選択**] ページで、[**既存のリレーショナルデータベースまたはデータウェアハウスから**] が選択されていることを確認し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="563ce-110">On the **Select the Definition Method** page, verify that **From existing relational database or data warehouse** is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="563ce-111">[**データマイニング構造の作成**] ページで、[**マイニングモデルを含むマイニング構造を作成**する] オプションが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="563ce-111">On the **Create the Data Mining Structure** page, verify that the option **Create mining structure with a mining model** is selected.</span></span> <span data-ttu-id="563ce-112">次に、オプションのドロップダウンリストをクリックして、**使用するデータマイニング技法**を選択し、[ **Microsoft シーケンスクラスター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="563ce-112">Next, click the dropdown list for the option, **Which data mining technique do you want to use?**, and select **Microsoft Sequence Clustering**.</span></span> <span data-ttu-id="563ce-113">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="563ce-113">Click **Next**.</span></span>  
  
     <span data-ttu-id="563ce-114">**[データソースビューの選択**] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="563ce-114">The **Select Data Source View** page appears.</span></span> <span data-ttu-id="563ce-115">[**使用できるデータソースビュー**] で、[] を選択し `Orders` ます。</span><span class="sxs-lookup"><span data-stu-id="563ce-115">Under **Available data source views**, select `Orders`.</span></span>  
  
     <span data-ttu-id="563ce-116">Orders は、マーケット バスケット シナリオで使用したものと同じデータ ソース ビューです。</span><span class="sxs-lookup"><span data-stu-id="563ce-116">Orders is the same data source view that you used for the market basket scenario.</span></span> <span data-ttu-id="563ce-117">このデータソースビューを作成していない場合は、「[入れ子になったテーブルを含むデータソースビューの追加 &#40;中級者向けデータマイニングチュートリアル」&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="563ce-117">If you have not created this data source view, see [Adding a Data Source View with Nested Tables &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md).</span></span>  
  
5.  <span data-ttu-id="563ce-118">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="563ce-118">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="563ce-119">[**テーブルの種類の指定**] ページで、 **vAssocSeqOrders**テーブルの横にある [**ケース**] チェックボックスをオンにし、 **VAssocSeqLineItems**テーブルの横にある [**入れ子になっ**た] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="563ce-119">On the **Specify Table Types** page, select the **Case** check box next to the **vAssocSeqOrders** table, and select the **Nested** check box next to the **vAssocSeqLineItems** table.</span></span> <span data-ttu-id="563ce-120">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="563ce-120">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="563ce-121">**ケース**または**入れ子になっ**たチェックボックスをオンにしたときにエラーが発生した場合、データソースビューの結合が正しくない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="563ce-121">If an error occurs when you select the **Case** or **Nested** check boxes, it may be that the join in the data source view is not correct.</span></span> <span data-ttu-id="563ce-122">入れ子になったテーブル**vAssocSeqLineItems**は、多対一の結合によってケーステーブル**vAssocSeqOrders**に接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="563ce-122">The nested table, **vAssocSeqLineItems**, must be connected to the case table, **vAssocSeqOrders,** by a many-to-one join.</span></span> <span data-ttu-id="563ce-123">結合線を右クリックして結合の方向を逆向きにすることによって、リレーションシップを編集できます。</span><span class="sxs-lookup"><span data-stu-id="563ce-123">You can edit the relationship by right-clicking on the join line and then reversing the direction of the join.</span></span> <span data-ttu-id="563ce-124">詳細については、「[[リレーションシップの作成] または [リレーションシップの編集] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](../../2014/analysis-services/create-or-edit-relationship-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="563ce-124">For more information, see [Create or Edit Relationship Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../../2014/analysis-services/create-or-edit-relationship-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
7.  <span data-ttu-id="563ce-125">[**トレーニングデータの指定**] ページで、次のようにチェックボックスをオンにして、モデルで使用する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="563ce-125">On the **Specify the Training Data** page, choose the columns for use in the model by selecting a check box as follows:</span></span>  
  
    -   <span data-ttu-id="563ce-126">**IncomeGroup**[**入力**] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="563ce-126">**IncomeGroup** Select the **Input** check box.</span></span>  
  
         <span data-ttu-id="563ce-127">この列には、クラスタリングに使用できる、顧客に関する有用な情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="563ce-127">This column contains interesting information about the customers that you can use for clustering.</span></span> <span data-ttu-id="563ce-128">最初のモデルではこの情報を使用し、2 番目のモデルではこの情報を無視します。</span><span class="sxs-lookup"><span data-stu-id="563ce-128">You will use it in the first model and then ignore it in the second model.</span></span>  
  
    -   <span data-ttu-id="563ce-129">**Ordernumber**チェックボックスをオンにし `Key` ます。</span><span class="sxs-lookup"><span data-stu-id="563ce-129">**OrderNumber** Select the `Key` check box.</span></span>  
  
         <span data-ttu-id="563ce-130">このフィールドは、ケース テーブルの識別子、つまり `Key` として使用されます。</span><span class="sxs-lookup"><span data-stu-id="563ce-130">This field will be used as the identifier for the case table, or `Key`.</span></span> <span data-ttu-id="563ce-131">一般に、キーにはクラスタリングに適さない一意の値が格納されるので、ケース テーブルのキー フィールドは入力として使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="563ce-131">In general, you should never use the key field of the case table as an input, because the key contains unique values that are not useful for clustering.</span></span>  
  
    -   <span data-ttu-id="563ce-132">**リージョン**[**入力**] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="563ce-132">**Region** Select the **Input** check box.</span></span>  
  
         <span data-ttu-id="563ce-133">この列には、クラスタリングに使用できる、顧客に関する有用な情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="563ce-133">This column contains interesting information about the customers that you can use for clustering.</span></span> <span data-ttu-id="563ce-134">最初のモデルではこの情報を使用し、2 番目のモデルではこの情報を無視します。</span><span class="sxs-lookup"><span data-stu-id="563ce-134">You will use it in the first model and then ignore it in the second model.</span></span>  
  
    -   <span data-ttu-id="563ce-135">**LineNumber**[] `Key` および [**入力**] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="563ce-135">**LineNumber** Select the `Key` and **Input** check boxes.</span></span>  
  
         <span data-ttu-id="563ce-136">**LineNumber**フィールドは、入れ子になったテーブルの識別子として、またはとして使用され `Sequence Key` ます。</span><span class="sxs-lookup"><span data-stu-id="563ce-136">The **LineNumber** field will be used as the identifier for the nested table, or `Sequence Key`.</span></span> <span data-ttu-id="563ce-137">入れ子になったテーブルのキーは、常に入力に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="563ce-137">The key for a nested table must always be used for input.</span></span>  
  
    -   <span data-ttu-id="563ce-138">**モデル**[**入力**] チェックボックスと [**予測可能**] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="563ce-138">**Model** Select the **Input** and **Predictable** check boxes.</span></span>  
  
     <span data-ttu-id="563ce-139">選択内容が正しいことを確認し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="563ce-139">Verify that the selections are correct, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="563ce-140">[**列のコンテンツおよびデータ型の指定**] ページで、次の表に示す列、コンテンツの種類、およびデータ型がグリッドに表示されていることを確認し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="563ce-140">On the **Specify Columns' Content and Data Type** page, verify that the grid contains the columns, content types, and data types shown in the following table, and then click **Next**.</span></span>  
  
    |<span data-ttu-id="563ce-141">テーブルまたは列</span><span class="sxs-lookup"><span data-stu-id="563ce-141">Tables/Columns</span></span>|<span data-ttu-id="563ce-142">コンテンツの種類</span><span class="sxs-lookup"><span data-stu-id="563ce-142">Content Type</span></span>|<span data-ttu-id="563ce-143">データ型</span><span class="sxs-lookup"><span data-stu-id="563ce-143">Data Type</span></span>|  
    |---------------------|------------------|---------------|  
    |<span data-ttu-id="563ce-144">IncomeGroup</span><span class="sxs-lookup"><span data-stu-id="563ce-144">IncomeGroup</span></span>|<span data-ttu-id="563ce-145">離散</span><span class="sxs-lookup"><span data-stu-id="563ce-145">Discrete</span></span>|<span data-ttu-id="563ce-146">Text</span><span class="sxs-lookup"><span data-stu-id="563ce-146">Text</span></span>|  
    |<span data-ttu-id="563ce-147">OrderNumber</span><span class="sxs-lookup"><span data-stu-id="563ce-147">OrderNumber</span></span>|<span data-ttu-id="563ce-148">Key</span><span class="sxs-lookup"><span data-stu-id="563ce-148">Key</span></span>|<span data-ttu-id="563ce-149">Text</span><span class="sxs-lookup"><span data-stu-id="563ce-149">Text</span></span>|  
    |<span data-ttu-id="563ce-150">リージョン</span><span class="sxs-lookup"><span data-stu-id="563ce-150">Region</span></span>|<span data-ttu-id="563ce-151">離散</span><span class="sxs-lookup"><span data-stu-id="563ce-151">Discrete</span></span>|<span data-ttu-id="563ce-152">Text</span><span class="sxs-lookup"><span data-stu-id="563ce-152">Text</span></span>|  
    |<span data-ttu-id="563ce-153">vAssocSeqLineItems</span><span class="sxs-lookup"><span data-stu-id="563ce-153">vAssocSeqLineItems</span></span>|||  
    |<span data-ttu-id="563ce-154">Line Number</span><span class="sxs-lookup"><span data-stu-id="563ce-154">Line Number</span></span>|<span data-ttu-id="563ce-155">Key Sequence</span><span class="sxs-lookup"><span data-stu-id="563ce-155">Key Sequence</span></span>|<span data-ttu-id="563ce-156">Long</span><span class="sxs-lookup"><span data-stu-id="563ce-156">Long</span></span>|  
    |<span data-ttu-id="563ce-157">モデル</span><span class="sxs-lookup"><span data-stu-id="563ce-157">Model</span></span>|<span data-ttu-id="563ce-158">離散</span><span class="sxs-lookup"><span data-stu-id="563ce-158">Discrete</span></span>|<span data-ttu-id="563ce-159">Text</span><span class="sxs-lookup"><span data-stu-id="563ce-159">Text</span></span>|  
  
9. <span data-ttu-id="563ce-160">[**テストセットの作成**] ページで、**テスト用データの割合**を20に変更し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="563ce-160">On the **Create Testing Set** page, change the **Percentage of data for testing** to 20, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="563ce-161">[**ウィザードの完了**] ページで、[**マイニング構造名**] に「」と入力 `Sequence Clustering with Region` します。</span><span class="sxs-lookup"><span data-stu-id="563ce-161">On the **Completing the Wizard** page, for the **Mining structure name**, type `Sequence Clustering with Region`.</span></span>  
  
11. <span data-ttu-id="563ce-162">[**マイニングモデル名**] に「」と入力 `Sequence Clustering with Region` します。</span><span class="sxs-lookup"><span data-stu-id="563ce-162">For the **Mining model name**, type `Sequence Clustering with Region`.</span></span>  
  
12. <span data-ttu-id="563ce-163">[ドリルスルーを**許可する**] チェックボックスをオンにし、[**完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="563ce-163">Check the **Allow drill through** box, and then click **Finish**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="563ce-164">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="563ce-164">Next Task in Lesson</span></span>  
 [<span data-ttu-id="563ce-165">シーケンス クラスター モデルの処理</span><span class="sxs-lookup"><span data-stu-id="563ce-165">Processing the Sequence Clustering Model</span></span>](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="563ce-166">参照</span><span class="sxs-lookup"><span data-stu-id="563ce-166">See Also</span></span>  
 <span data-ttu-id="563ce-167">[データマイニングデザイナー](../../2014/analysis-services/data-mining/data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="563ce-167">[Data Mining Designer](../../2014/analysis-services/data-mining/data-mining-designer.md) </span></span>  
 [<span data-ttu-id="563ce-168">Microsoft シーケンス クラスタリング アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="563ce-168">Microsoft Sequence Clustering Algorithm</span></span>](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)  
  
  
