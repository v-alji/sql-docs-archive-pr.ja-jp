---
title: マーケットバスケットの構造とモデルの作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 659b7a4e-f687-44d9-a60a-86490ccbf90f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b276fe5bed1d9df8e8b2e3e2826966b6abfb734e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631437"
---
# <a name="creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="33391-102">Market Basket 構造およびモデルの作成 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="33391-102">Creating a Market Basket Structure and Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="33391-103">前の作業では、データ ソース ビューを作成しました。次の作業では、データ マイニング ウィザードを使用して、新しいマイニング構造を作成します。</span><span class="sxs-lookup"><span data-stu-id="33391-103">Now that you have created a data source view, you will use the Data Mining Wizard to create a new mining structure.</span></span> <span data-ttu-id="33391-104">この作業では、[!INCLUDE[msCoName](../includes/msconame-md.md)] アソシエーション アルゴリズムに基づくマイニング構造とマイニング モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="33391-104">In this task, you will create a mining structure and a mining model that is based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="33391-105">vAssocSeqLineItems テーブルを入れ子にできないことを示すエラーが表示された場合は、レッスンの前の作業に戻り、多対一の結合を確実に作成してください。この結合を作成するには、vAssocSeqLineItems テーブル ("多" の側) から vAssocSeqOrders テーブル ("一" の側) にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="33391-105">If you encounter an error stating that vAssocSeqLineItems cannot be used as a nested table, return to the previous task in the lesson, and be sure to create the many-to-one join by dragging from the vAssocSeqLineItems table (the many side) to the vAssocSeqOrders table (the one side).</span></span> <span data-ttu-id="33391-106">結合線を右クリックして、テーブル間のリレーションシップを編集することもできます。</span><span class="sxs-lookup"><span data-stu-id="33391-106">You can also edit the relationship between the tables by right-clicking the join line.</span></span>  
  
### <a name="to-create-an-association-mining-structure"></a><span data-ttu-id="33391-107">アソシエーション マイニング構造を作成するには</span><span class="sxs-lookup"><span data-stu-id="33391-107">To create an association mining structure</span></span>  
  
1.  <span data-ttu-id="33391-108">のソリューションエクスプローラーで [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 、[**マイニング構造**] を右クリックし、[**新しいマイニング構造**] をクリックして、データマイニングウィザードを開きます。</span><span class="sxs-lookup"><span data-stu-id="33391-108">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], right-click **Mining Structures** and select **New Mining Structure** to open the Data Mining Wizard.</span></span>  
  
2.  <span data-ttu-id="33391-109">**[データ マイニング ウィザードへようこそ]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33391-109">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="33391-110">[**定義方法の選択**] ページで、[**既存のリレーショナルデータベースまたはデータウェアハウスから**] が選択されていることを確認し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33391-110">On the **Select the Definition Method** page, verify that **From existing relational database or data warehouse** is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="33391-111">[**データマイニング構造の作成**] ページの [**使用するデータマイニング技法を指定**してください] で、一覧から [ **Microsoft アソシエーションルール**] を選択し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33391-111">On the **Create the Data Mining Structure** page, under **Which data mining technique do you want to use?**, select **Microsoft Association Rules** from the list, and then click **Next**.</span></span> <span data-ttu-id="33391-112">**[データソースビューの選択**] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="33391-112">The **Select Data Source View** page appears.</span></span>  
  
5.  <span data-ttu-id="33391-113">[**使用できるデータソースビュー**] で [**注文**] を選択し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33391-113">Select **Orders**under **Available data source views**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="33391-114">[**テーブルの種類の指定**] ページで、vAssocSeqLineItems テーブルの行の [**入れ子**] チェックボックスをオンにし、入れ子になったテーブル vAssocSeqOrders の行で [**ケース**] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="33391-114">On the **Specify Table Types** page, in the row for the vAssocSeqLineItems table, select the **Nested** check box, and in the row for the nested table vAssocSeqOrders, select the **Case** check box.</span></span> <span data-ttu-id="33391-115">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33391-115">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="33391-116">[**トレーニングデータの指定**] ページで、チェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="33391-116">On the **Specify the Training Data** page, clear any boxes that might be checked.</span></span> <span data-ttu-id="33391-117">[OrderNumber] の横にある [**キー** ] チェックボックスをオンにして、ケーステーブル vAssocSeqOrders のキーを設定します。</span><span class="sxs-lookup"><span data-stu-id="33391-117">Set the key for the case table, vAssocSeqOrders, by selecting the **Key** check box next to OrderNumber.</span></span>  
  
     <span data-ttu-id="33391-118">マーケットバスケット分析の目的は、1つのトランザクションに含まれる製品を特定することであるため、[**顧客キー** ] フィールドを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="33391-118">Because the purpose of the market basket analysis is to determine which products are included in a single transaction, you do not have to use the **CustomerKey** field.</span></span>  
  
8.  <span data-ttu-id="33391-119">[モデル] の横にある [**キー** ] チェックボックスをオンにして、入れ子になったテーブル vAssocSeqLineItems のキーを設定します。</span><span class="sxs-lookup"><span data-stu-id="33391-119">Set the key for the nested table, vAssocSeqLineItems, by selecting the **Key** check box next to Model.</span></span> <span data-ttu-id="33391-120">この操作を行うと、[**入力**] チェックボックスも自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="33391-120">The **Input** check box is also automatically selected when you do this.</span></span> <span data-ttu-id="33391-121">[**予測可能**] チェックボックスもオンにし `Model` ます。</span><span class="sxs-lookup"><span data-stu-id="33391-121">Select the **Predictable** check box for `Model` as well.</span></span>  
  
     <span data-ttu-id="33391-122">マーケットバスケットモデルでは、買い物かごに含まれる一連の製品を気にする必要はないため、入れ子になったテーブルのキーとして**LineNumber**を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="33391-122">In a market basket model, you do not care about the sequence of products in the shopping basket, and therefore you should not include **LineNumber** as a key for the nested table.</span></span> <span data-ttu-id="33391-123">**LineNumber**は、シーケンスが重要なモデル内でのみキーとして使用します。</span><span class="sxs-lookup"><span data-stu-id="33391-123">You would use **LineNumber** as a key only in a model where the sequence is important.</span></span> <span data-ttu-id="33391-124">レッスン 4 では、[!INCLUDE[msCoName](../includes/msconame-md.md)] シーケンス クラスター アルゴリズムを使用するモデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="33391-124">You will create a model that uses the [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering algorithm in Lesson 4.</span></span>  
  
9. <span data-ttu-id="33391-125">[IncomeGroup] および [Region] の左側にあるチェック ボックスをオンにします。ただし、それ以外のチェック ボックスはオンにしないでください。</span><span class="sxs-lookup"><span data-stu-id="33391-125">Select the check box to the left of IncomeGroup and Region,but do not make any other selections.</span></span> <span data-ttu-id="33391-126">左端の列のチェック ボックスをオンにすると、これらの列が構造に追加され、後で参照できるようになります。ただし、これらの列はモデルでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="33391-126">Checking the leftmost column adds the columns to the structure for later reference, but the columns will not be used in the model.</span></span> <span data-ttu-id="33391-127">選択内容は以下のようになります。</span><span class="sxs-lookup"><span data-stu-id="33391-127">Your selections should look like the following:</span></span>  
  
     <span data-ttu-id="33391-128">![ダイアログ ボックスの状態](../../2014/tutorials/media/tutorial-configassocmodel.gif "ダイアログ ボックスの状態")</span><span class="sxs-lookup"><span data-stu-id="33391-128">![how dialog box should look](../../2014/tutorials/media/tutorial-configassocmodel.gif "how dialog box should look")</span></span>  
  
10. <span data-ttu-id="33391-129">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33391-129">Click **Next**.</span></span>  
  
11. <span data-ttu-id="33391-130">[**列のコンテンツおよびデータ型の指定**] ページで、選択内容 (次の表を参照) を確認し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33391-130">On the **Specify Columns' Content and Data Type**page, review the selections, which should be as shown in the following table, and then click **Next**.</span></span>  
  
    |<span data-ttu-id="33391-131">[列]</span><span class="sxs-lookup"><span data-stu-id="33391-131">Columns</span></span>|<span data-ttu-id="33391-132">コンテンツの種類</span><span class="sxs-lookup"><span data-stu-id="33391-132">Content Type</span></span>|<span data-ttu-id="33391-133">データ型</span><span class="sxs-lookup"><span data-stu-id="33391-133">Data Type</span></span>|  
    |-------------|------------------|---------------|  
    |<span data-ttu-id="33391-134">IncomeGroup</span><span class="sxs-lookup"><span data-stu-id="33391-134">IncomeGroup</span></span>|<span data-ttu-id="33391-135">離散</span><span class="sxs-lookup"><span data-stu-id="33391-135">Discrete</span></span>|<span data-ttu-id="33391-136">Text</span><span class="sxs-lookup"><span data-stu-id="33391-136">Text</span></span>|  
    |<span data-ttu-id="33391-137">Order Number</span><span class="sxs-lookup"><span data-stu-id="33391-137">Order Number</span></span>|<span data-ttu-id="33391-138">Key</span><span class="sxs-lookup"><span data-stu-id="33391-138">Key</span></span>|<span data-ttu-id="33391-139">Text</span><span class="sxs-lookup"><span data-stu-id="33391-139">Text</span></span>|  
    |<span data-ttu-id="33391-140">リージョン</span><span class="sxs-lookup"><span data-stu-id="33391-140">Region</span></span>|<span data-ttu-id="33391-141">離散</span><span class="sxs-lookup"><span data-stu-id="33391-141">Discrete</span></span>|<span data-ttu-id="33391-142">Text</span><span class="sxs-lookup"><span data-stu-id="33391-142">Text</span></span>|  
    |<span data-ttu-id="33391-143">vAssocSeqLineItems</span><span class="sxs-lookup"><span data-stu-id="33391-143">vAssocSeqLineItems</span></span>|||  
    |<span data-ttu-id="33391-144">モデル</span><span class="sxs-lookup"><span data-stu-id="33391-144">Model</span></span>|<span data-ttu-id="33391-145">Key</span><span class="sxs-lookup"><span data-stu-id="33391-145">Key</span></span>|<span data-ttu-id="33391-146">Text</span><span class="sxs-lookup"><span data-stu-id="33391-146">Text</span></span>|  
  
12. <span data-ttu-id="33391-147">[**テストセットの作成**] ページの [**テスト用データの割合**] オプションの既定値は30% です。</span><span class="sxs-lookup"><span data-stu-id="33391-147">On the **Create testing set** page, the default value for the option **Percentage of data for testing** is 30 percent.</span></span> <span data-ttu-id="33391-148">これを**0**に変更します。</span><span class="sxs-lookup"><span data-stu-id="33391-148">Change this to **0**.</span></span> <span data-ttu-id="33391-149">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33391-149">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="33391-150">には、モデルの精度を測定するための別のチャートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="33391-150">provides different charts for measuring model accuracy.</span></span> <span data-ttu-id="33391-151">ただし、リフト チャートや相互検証レポートなど、一部の種類の精度チャートは、分類および推定用に設計されています。</span><span class="sxs-lookup"><span data-stu-id="33391-151">However, some accuracy chart types, such as the lift chart and cross-validation report, are designed for classification and estimation.</span></span> <span data-ttu-id="33391-152">結合型の予測には使用できません。</span><span class="sxs-lookup"><span data-stu-id="33391-152">They are not supported for associative prediction.</span></span>  
  
13. <span data-ttu-id="33391-153">[**ウィザードの完了**] ページの [**マイニング構造名**] に「」と入力 `Association` します。</span><span class="sxs-lookup"><span data-stu-id="33391-153">On the **Completing the Wizard** page, in **Mining structure name**, type `Association`.</span></span>  
  
14. <span data-ttu-id="33391-154">[**マイニングモデル名**] に「」と入力 `Association` します。</span><span class="sxs-lookup"><span data-stu-id="33391-154">In **Mining model name**, type `Association`.</span></span>  
  
15. <span data-ttu-id="33391-155">[ドリルスルーを**許可する**] オプションを選択し、[**完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33391-155">Select the option **Allow drill through**, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="33391-156">データマイニングデザイナーが開き、作成した `Association` マイニング構造が表示されます。</span><span class="sxs-lookup"><span data-stu-id="33391-156">Data Mining Designer opens to display the `Association` mining structure that you just created.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="33391-157">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="33391-157">Next Task in Lesson</span></span>  
 [<span data-ttu-id="33391-158">「中級者向けデータマイニングチュートリアル &#40;のマーケットバスケットモデルの変更と処理&#41;</span><span class="sxs-lookup"><span data-stu-id="33391-158">Modifying and Processing the Market Basket Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/modify-process-market-basket-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="33391-159">参照</span><span class="sxs-lookup"><span data-stu-id="33391-159">See Also</span></span>  
 <span data-ttu-id="33391-160">[Microsoft アソシエーションアルゴリズム](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="33391-160">[Microsoft Association Algorithm](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) </span></span>  
 [<span data-ttu-id="33391-161">コンテンツの種類 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="33391-161">Content Types &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/content-types-data-mining.md)  
  
  
