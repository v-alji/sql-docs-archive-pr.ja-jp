---
title: 入れ子になったテーブルを含むデータソースビューの追加 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a14cd7f1-7a10-4ec6-af6a-f5f0676a0308
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: da1a9bff093e0b59e9d1166554d95bcf61aded08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720547"
---
# <a name="adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial"></a><span data-ttu-id="564bc-102">入れ子になったテーブルを伴うデータ ソース ビューの追加 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="564bc-102">Adding a Data Source View with Nested Tables (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="564bc-103">マーケット バスケット モデルを作成するには、結合データをサポートしているデータ ソース ビューを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="564bc-103">To create a market basket model, you must use a data source view that supports associative data.</span></span> <span data-ttu-id="564bc-104">このデータ ソース ビューは、シーケンス クラスター シナリオでも使用されます。</span><span class="sxs-lookup"><span data-stu-id="564bc-104">This data source view will also be used for the sequence clustering scenario.</span></span>  
  
 <span data-ttu-id="564bc-105">このデータソースビューは、*入れ子になったテーブル*が含まれているため、作業していた可能性があります。</span><span class="sxs-lookup"><span data-stu-id="564bc-105">This data source view is different from others that you may have worked with because it contains a *nested table*.</span></span> <span data-ttu-id="564bc-106">*入れ子になったテーブル*とは、ケーステーブル内の1つの行に関する複数行の情報を含むテーブルです。</span><span class="sxs-lookup"><span data-stu-id="564bc-106">A *nested table* is a table that contains multiple rows of information about a single row in the case table.</span></span> <span data-ttu-id="564bc-107">たとえば、モデルで顧客の購入行動を分析する場合は、顧客ごとに固有の行があるテーブルをケース テーブルとして使用するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="564bc-107">For example, if your model analyzes the purchasing behavior of customers, you would typically use a table that has a unique row for each customer as the case table.</span></span> <span data-ttu-id="564bc-108">しかし、1 人の顧客が複数の商品を購入することもあります。また、顧客の一連の購入記録を分析したり、一緒に購入されることの多い商品を分析することが必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="564bc-108">However, each customer might make multiple purchases, and you might want to analyze the sequence of purchases, or products that are frequently purchased together.</span></span> <span data-ttu-id="564bc-109">モデルを使ってこのような購入記録を論理的に表すには、データ ソース ビューに、顧客ごとの購入記録を一覧表示するテーブルを 1 つ追加します。</span><span class="sxs-lookup"><span data-stu-id="564bc-109">To logically represent these purchases in your model, you add another table to the data source view that lists the purchases for each customer.</span></span>  
  
 <span data-ttu-id="564bc-110">この入れ子になった購入記録テーブルは、多対一のリレーションシップで顧客テーブルに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="564bc-110">This nested purchases table is related to the customer table by a many-to-one relationship.</span></span> <span data-ttu-id="564bc-111">入れ子になったテーブルには顧客ごとに複数の行を作成でき、各行には購入された製品 (通常、購入が行われた注文に関する情報が追加されます)、注文時の価格、適用されたプロモーションなどが記録されます。</span><span class="sxs-lookup"><span data-stu-id="564bc-111">The nested table might contain many rows for each customer, each row containing a single product that was purchased, perhaps with additional information about the order that the purchases were made, the price at the time of the order, or any promotions that applied.</span></span> <span data-ttu-id="564bc-112">入れ子になったテーブルの情報は、モデルへの入力または予測可能な属性として使用できます。</span><span class="sxs-lookup"><span data-stu-id="564bc-112">You can use the information in the nested table as inputs to the model, or as the predictable attribute.</span></span>  
  
 <span data-ttu-id="564bc-113">このレッスンでは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="564bc-113">In this lesson, you do the following tasks:</span></span>  
  
-   <span data-ttu-id="564bc-114">データソースにデータソースビューを追加し [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="564bc-114">You add a data source view to the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] data source.</span></span>  
  
-   <span data-ttu-id="564bc-115">このビューにケース テーブルと入れ子になったテーブルを追加します。</span><span class="sxs-lookup"><span data-stu-id="564bc-115">You add the case and nested tables to this view.</span></span>  
  
-   <span data-ttu-id="564bc-116">ケース テーブルと入れ子になったテーブルの間に多対一のリレーションシップを指定します。</span><span class="sxs-lookup"><span data-stu-id="564bc-116">You specify the many-to-one relationship between the case and nested table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="564bc-117">.</span><span class="sxs-lookup"><span data-stu-id="564bc-117">.</span></span> <span data-ttu-id="564bc-118">説明した手順に正確に従い、ケース テーブルと入れ子になったテーブルの間のリレーションシップを正しく指定して、モデルの処理時にエラーが発生しないようにすることが重要です。</span><span class="sxs-lookup"><span data-stu-id="564bc-118">It is important that you follow the described procedure exactly, to correctly specify the relationship between the case table and the nested table and to avoid errors when you process the model.</span></span>  
  
-   <span data-ttu-id="564bc-119">データの列がモデルでどのように使用されるかを定義します。</span><span class="sxs-lookup"><span data-stu-id="564bc-119">You define how the columns of data are used in the model.</span></span>  
  
 <span data-ttu-id="564bc-120">ケーステーブルと入れ子になったテーブルの操作、および入れ子になったテーブルキーの選択方法の詳細については、「[入れ子になったテーブル &#40;Analysis Services データマイニング&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="564bc-120">For more information about working with case and nested tables, and how to choose a nested table key, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md).</span></span>  
  
### <a name="to-add-a-data-source-view"></a><span data-ttu-id="564bc-121">データ ソース ビューを追加するには</span><span class="sxs-lookup"><span data-stu-id="564bc-121">To add a data source view</span></span>  
  
1.  <span data-ttu-id="564bc-122">ソリューションエクスプローラーで、[**データソースビュー**] を右クリックし、[**新しいデータソースビュー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="564bc-122">In Solution Explorer, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
     <span data-ttu-id="564bc-123">データ ソース ビュー ウィザードが開きます。</span><span class="sxs-lookup"><span data-stu-id="564bc-123">The Data Source View Wizard opens.</span></span>  
  
2.  <span data-ttu-id="564bc-124">**[データ ソース ビュー ウィザードへようこそ]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="564bc-124">On the **Welcome to the Data Source View Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="564bc-125">[**データソースの選択**] ページの [**リレーショナルデータソース**] で、「 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 基本的なデータマイニングチュートリアル」で作成したデータソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="564bc-125">On the **Select a Data Source** page, under **Relational data sources**, select the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] data source that you created in the Basic Data Mining Tutorial.</span></span> <span data-ttu-id="564bc-126">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="564bc-126">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="564bc-127">[**テーブルとビューの選択**] ページで、次のテーブルを選択し、右矢印をクリックして新しいデータソースビューに追加します。</span><span class="sxs-lookup"><span data-stu-id="564bc-127">On the **Select Tables and Views** page, select the following tables, and then click the right arrow to include them in the new data source view:</span></span>  
  
    -   `vAssocSeqOrders`  
  
    -   `vAssocSeqLineItems`  
  
5.  <span data-ttu-id="564bc-128">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="564bc-128">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="564bc-129">既定では、[**ウィザードの完了**] ページにはという名前のデータソースビューが [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] あります。</span><span class="sxs-lookup"><span data-stu-id="564bc-129">On the **Completing the Wizard** page, by default the data source view is named [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].</span></span> <span data-ttu-id="564bc-130">名前をに変更し、 `Orders` [**完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="564bc-130">Change the name to `Orders`, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="564bc-131">データソースビューデザイナーが開き、 `Orders` データソースビューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="564bc-131">Data Source View Designer opens and the `Orders` data source view appears.</span></span>  
  
### <a name="to-create-a-relationship-between-tables"></a><span data-ttu-id="564bc-132">2 つのテーブル間のリレーションシップを作成するには</span><span class="sxs-lookup"><span data-stu-id="564bc-132">To create a relationship between tables</span></span>  
  
1.  <span data-ttu-id="564bc-133">データ ソース ビュー デザイナーで、2 つのテーブルを横に並べて配置します (vAssocSeqLineItems テーブルが左で vAssocSeqOrders テーブルが右)。</span><span class="sxs-lookup"><span data-stu-id="564bc-133">In Data Source View Designer, position the two tables so that the tables are aligned horizontally, with the vAssocSeqLineItems table on the left side and the vAssocSeqOrders table on the right side.</span></span>  
  
2.  <span data-ttu-id="564bc-134">VAssocSeqLineItems テーブルの**Ordernumber**列を選択します。</span><span class="sxs-lookup"><span data-stu-id="564bc-134">Select the **OrderNumber** column in the vAssocSeqLineItems table.</span></span>  
  
3.  <span data-ttu-id="564bc-135">列を vAssocSeqOrders テーブルにドラッグし、 **Ordernumber**列に配置します。</span><span class="sxs-lookup"><span data-stu-id="564bc-135">Drag the column to the vAssocSeqOrders table, and put it on the **OrderNumber** column.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="564bc-136">結合の "多" の側を表す vAssocSeqLineItems 入れ子になったテーブルの**Ordernumber**列を、結合の一方の側を表す vAssocSeqOrders ケーステーブルにドラッグしてください。</span><span class="sxs-lookup"><span data-stu-id="564bc-136">Make sure to drag the **OrderNumber** column from the vAssocSeqLineItems nested table, which represents the many side of the join, to the vAssocSeqOrders case table, which represents the one side of the join.</span></span>  
  
     <span data-ttu-id="564bc-137">VAssocSeqLineItems テーブルと vAssocSeqOrders テーブルの間*に多対一のリレーションシップ*が新たに存在するようになりました。</span><span class="sxs-lookup"><span data-stu-id="564bc-137">A new *many-to-one relationship* now exists between the vAssocSeqLineItems and vAssocSeqOrders tables.</span></span> <span data-ttu-id="564bc-138">テーブルを正しく結合した場合は、データ ソース ビューに次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="564bc-138">If you have joined the tables correctly, the data source view should appear as follows:</span></span>  
  
     <span data-ttu-id="564bc-139">![想定されていた、入れ子になったテーブルとケース テーブルとの多対一結合](../../2014/tutorials/media/dsv-nestedjoin-illustration.gif "想定されていた、入れ子になったテーブルとケース テーブルとの多対一結合")</span><span class="sxs-lookup"><span data-stu-id="564bc-139">![expected many-to-one join on nested and case table](../../2014/tutorials/media/dsv-nestedjoin-illustration.gif "expected many-to-one join on nested and case table")</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="564bc-140">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="564bc-140">Next Task in Lesson</span></span>  
 [<span data-ttu-id="564bc-141">&#40;中級者向けデータマイニングチュートリアルの作成&#41;</span><span class="sxs-lookup"><span data-stu-id="564bc-141">Creating a Market Basket Structure and Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="564bc-142">参照</span><span class="sxs-lookup"><span data-stu-id="564bc-142">See Also</span></span>  
 <span data-ttu-id="564bc-143">[中級者向けデータマイニングチュートリアル &#40;Analysis Services データマイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="564bc-143">[Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="564bc-144">[マイニング構造 &#40;Analysis Services-データマイニング&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="564bc-144">[Mining Structures &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="564bc-145">マイニング モデル (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="564bc-145">Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
  
