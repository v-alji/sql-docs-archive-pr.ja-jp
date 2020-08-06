---
title: 'レッスン 11: パーティションの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 92eb21a8-5fc4-4999-ad37-1332ce26431d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4db5edd5d47fe424ef6e6ad2a822106110209059
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631306"
---
# <a name="lesson-11-create-partitions"></a><span data-ttu-id="5a3ef-102">レッスン 11:パーティションの作成</span><span class="sxs-lookup"><span data-stu-id="5a3ef-102">Lesson 11: Create Partitions</span></span>
  <span data-ttu-id="5a3ef-103">このレッスンでは、パーティションを作成して Internet Sales テーブルをより小さな論理部分に分割し、他のパーティションと分離して処理 (更新) できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-103">In this lesson, you will create partitions to divide the Internet Sales table into smaller logical parts that can be processed (Refreshed) independent of other partitions.</span></span> <span data-ttu-id="5a3ef-104">既定では、モデルに含めるすべてのテーブルには、テーブルのすべての列と行を含む1つのパーティションがあります。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-104">By default, every table you include in your model has one partition which includes all of the table's columns and rows.</span></span> <span data-ttu-id="5a3ef-105">Internet Sales テーブルでは、データを年で分割します。テーブルの5年ごとに1つのパーティション。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-105">For the Internet Sales table, we want to divide the data by year; one partition for each of the table's five years.</span></span>  <span data-ttu-id="5a3ef-106">これにより、各パーティションを個別に処理できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-106">Each partition can then be processed independently.</span></span> <span data-ttu-id="5a3ef-107">詳細については、「[パーティション (SSAS テーブル)](tabular-models/partitions-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-107">To learn more, see [Partitions &#40;SSAS Tabular&#41;](tabular-models/partitions-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="5a3ef-108">このレッスンの推定所要時間: **15 分**</span><span class="sxs-lookup"><span data-stu-id="5a3ef-108">Estimated time to complete this lesson: **15 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5a3ef-109">前提条件</span><span class="sxs-lookup"><span data-stu-id="5a3ef-109">Prerequisites</span></span>  
 <span data-ttu-id="5a3ef-110">このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-110">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="5a3ef-111">このレッスンの実習を行う前に、前のレッスン「 [レッスン 10: 階層の作成](lesson-9-create-hierarchies.md)」を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-111">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 10: Create Hierarchies](lesson-9-create-hierarchies.md).</span></span>  
  
## <a name="create-partitions"></a><span data-ttu-id="5a3ef-112">パーティションの作成</span><span class="sxs-lookup"><span data-stu-id="5a3ef-112">Create Partitions</span></span>  
  
#### <a name="to-create-partitions-in-the-internet-sales-table"></a><span data-ttu-id="5a3ef-113">Internet Sales テーブル内にパーティションを作成するには</span><span class="sxs-lookup"><span data-stu-id="5a3ef-113">To create partitions in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="5a3ef-114">モデル デザイナーで **[Internet Sales]** テーブルをクリックし、 **[テーブル]** メニュー、 **[パーティション]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-114">In the model designer, click on the **Internet Sales** table, then click on the **Table** menu, and then click **Partitions**.</span></span>  
  
     <span data-ttu-id="5a3ef-115">**[パーティション マネージャー]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-115">The **Partition Manager** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="5a3ef-116">[**パーティションマネージャー** ] ダイアログボックスの [**パーティション**] で、[ **Internet Sales** ] パーティションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-116">In the **Partition Manager** dialog box, in **Partitions**, click the **Internet Sales** partition.</span></span>  
  
3.  <span data-ttu-id="5a3ef-117">[**パーティション名**] で、名前をに変更 `Internet Sales 2005` します。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-117">In **Partition Name**, change the name to `Internet Sales 2005`.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="5a3ef-118">次の手順に進む前に、[テーブルのプレビュー] ウィンドウの列名が、モデル テーブル (チェックされている) に含まれている列を、ソースの列名で表示していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-118">Before continuing to the next step, notice the column names in the Table Preview window display those columns included in the model table (checked) with the column names from the source.</span></span> <span data-ttu-id="5a3ef-119">これは、[テーブルのプレビュー] ウィンドウでは、モデル テーブルからではなく、ソース テーブルから取得された列が表示されるためです。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-119">This is because the Table Preview window displays columns from the source table, not from the model table.</span></span>  
  
4.  <span data-ttu-id="5a3ef-120">プレビュー ウィンドウの右上にある **[クエリ エディター]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-120">Select the **Query Editor** button just above the right side of the preview window.</span></span>  
  
     <span data-ttu-id="5a3ef-121">特定の期間内の行だけをパーティションに含めたいので、WHERE 句を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-121">Because you want the partition to include only those rows within a certain period, you must include a WHERE clause.</span></span> <span data-ttu-id="5a3ef-122">WHERE 句は、SQL ステートメントによってのみ作成できます。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-122">You can only create a WHERE clause by using a SQL Statement.</span></span>  
  
5.  <span data-ttu-id="5a3ef-123">**[SQL ステートメント]** フィールドで、次のステートメントを貼り付けて既存のステートメントを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-123">In the **SQL Statement** field, replace the existing statement by pasting in the following statement:</span></span>  
  
    ```  
    SELECT   
    [dbo].[FactInternetSales].[ProductKey],  
    [dbo].[FactInternetSales].[CustomerKey],  
    [dbo].[FactInternetSales].[PromotionKey],  
    [dbo].[FactInternetSales].[CurrencyKey],  
    [dbo].[FactInternetSales].[SalesTerritoryKey],  
    [dbo].[FactInternetSales].[SalesOrderNumber],  
    [dbo].[FactInternetSales].[SalesOrderLineNumber],  
    [dbo].[FactInternetSales].[RevisionNumber],  
    [dbo].[FactInternetSales].[OrderQuantity],  
    [dbo].[FactInternetSales].[UnitPrice],  
    [dbo].[FactInternetSales].[ExtendedAmount],  
    [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
    [dbo].[FactInternetSales].[DiscountAmount],  
    [dbo].[FactInternetSales].[ProductStandardCost],  
    [dbo].[FactInternetSales].[TotalProductCost],  
    [dbo].[FactInternetSales].[SalesAmount],  
    [dbo].[FactInternetSales].[TaxAmt],  
    [dbo].[FactInternetSales].[Freight],  
    [dbo].[FactInternetSales].[CarrierTrackingNumber],  
    [dbo].[FactInternetSales].[CustomerPONumber],  
    [dbo].[FactInternetSales].[OrderDate],  
    [dbo].[FactInternetSales].[DueDate],  
    [dbo].[FactInternetSales].[ShipDate]   
    FROM [dbo].[FactInternetSales]  
    WHERE (([OrderDate] >= N'2005-01-01 00:00:00') AND ([OrderDate] < N'2006-01-01 00:00:00'))  
    ```  
  
     <span data-ttu-id="5a3ef-124">このステートメントは、WHERE 句で指定されているように、OrderDate が 2005 年度に該当する行のすべてのデータをパーティションに含めるよう指定しています。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-124">This statement specifies the partition should include all of the data in those rows where the OrderDate is for the 2005 calendar year as specified in the WHERE clause.</span></span>  
  
6.  <span data-ttu-id="5a3ef-125">**[検証]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-125">Click **Validate**.</span></span>  
  
     <span data-ttu-id="5a3ef-126">特定の列がソースに存在しないことを示す警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-126">Notice a warning is displayed stating that certain columns are not present in source.</span></span> <span data-ttu-id="5a3ef-127">これは、 [「レッスン 3: 列名の変更](rename-columns.md)」では、モデル内の Internet Sales テーブルの列の名前を変更して、ソースの同じ列とは異なるようにするためです。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-127">This is because in [Lesson 3: Rename Columns](rename-columns.md), you renamed those columns in the Internet Sales table in the model to be different from those same columns at the source.</span></span>  
  
#### <a name="to-create-a-partition-for-the-2006-year-in-the-internet-sales-table"></a><span data-ttu-id="5a3ef-128">Internet Sales テーブルに2006年のパーティションを作成するには</span><span class="sxs-lookup"><span data-stu-id="5a3ef-128">To create a partition for the 2006 year in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="5a3ef-129">[**パーティションマネージャー** ] ダイアログボックスの [**パーティション**] で、先ほど作成したパーティションをクリックし、[コピー] をクリックし `Internet Sales 2005` **Copy**ます。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-129">In the **Partition Manager** dialog box, in **Partitions**, click the `Internet Sales 2005` partition you just created, and then **Copy**.</span></span>  
  
2.  <span data-ttu-id="5a3ef-130">[**パーティション名**] に「」と入力 `Internet Sales 2006` します。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-130">In **Partition Name**, type `Internet Sales 2006`.</span></span>  
  
3.  <span data-ttu-id="5a3ef-131">SQL ステートメントで、パーティションに2006年の行だけが含まれるようにするには、WHERE 句を次のように置き換えます。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-131">In the SQL Statement, in-order for the partition to include only those rows for the 2006 year, replace the WHERE clause with the following:</span></span>  
  
    ```  
    WHERE (([OrderDate] >= N'2006-01-01 00:00:00') AND ([OrderDate] < N'2007-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2007-year-in-the-internet-sales-table"></a><span data-ttu-id="5a3ef-132">Internet Sales テーブルに2007年のパーティションを作成するには</span><span class="sxs-lookup"><span data-stu-id="5a3ef-132">To create a partition for the 2007 year in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="5a3ef-133">**[パーティション マネージャー]** ダイアログ ボックスで **[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-133">In the **Partition Manager** dialog box, click **Copy**.</span></span>  
  
2.  <span data-ttu-id="5a3ef-134">[**パーティション名**] に「」と入力 `Internet Sales 2007` します。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-134">In **Partition Name**, type `Internet Sales 2007`.</span></span>  
  
3.  <span data-ttu-id="5a3ef-135">[**切り替え先**] で、[**クエリエディター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-135">In **Switch To**, select **Query Editor**.</span></span>  
  
4.  <span data-ttu-id="5a3ef-136">SQL ステートメントで、パーティションに2007年の行だけが含まれるようにするには、WHERE 句を次のように置き換えます。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-136">In the SQL Statement, in-order for the partition to include only those rows for the 2007 year, replace the WHERE clause with the following:</span></span>  
  
    ```  
    WHERE (([OrderDate] >= N'2007-01-01 00:00:00') AND ([OrderDate] < N'2008-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2008-year-in-the-internet-sales-table"></a><span data-ttu-id="5a3ef-137">Internet Sales テーブルに2008年のパーティションを作成するには</span><span class="sxs-lookup"><span data-stu-id="5a3ef-137">To create a partition for the 2008 year in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="5a3ef-138">**[パーティション マネージャー]** ダイアログ ボックスで **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-138">In the **Partition Manager** dialog box, click **New**.</span></span>  
  
2.  <span data-ttu-id="5a3ef-139">[**パーティション名**] に「」と入力 `Internet Sales 2008` します。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-139">In **Partition Name**, type `Internet Sales 2008`.</span></span>  
  
3.  <span data-ttu-id="5a3ef-140">[**切り替え先**] で、[**クエリエディター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-140">In **Switch To**, select **Query Editor**.</span></span>  
  
4.  <span data-ttu-id="5a3ef-141">SQL ステートメントで、パーティションに2008年の行だけが含まれるようにするには、WHERE 句を次のように置き換えます。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-141">In the SQL Statement, in-order for the partition to include only those rows for the 2008 year, replace the WHERE clause with the following:</span></span>  
  
    ```  
    WHERE (([OrderDate] >= N'2008-01-01 00:00:00') AND ([OrderDate] < N'2009-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2009-year-in-the-internet-sales-table"></a><span data-ttu-id="5a3ef-142">Internet Sales テーブル内に 2009 年用のパーティションを作成するには</span><span class="sxs-lookup"><span data-stu-id="5a3ef-142">To create a partition for the 2009 year in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="5a3ef-143">**[パーティション マネージャー]** ダイアログ ボックスで **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-143">In the **Partition Manager** dialog box, click **New**.</span></span>  
  
2.  <span data-ttu-id="5a3ef-144">[**パーティション名**] に「」と入力 `Internet Sales 2009` します。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-144">In **Partition Name**, type `Internet Sales 2009`.</span></span>  
  
3.  <span data-ttu-id="5a3ef-145">[**切り替え先**] で、[**クエリエディター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-145">In **Switch To**, select **Query Editor**.</span></span>  
  
4.  <span data-ttu-id="5a3ef-146">SQL ステートメントで、WHERE 句を次の内容に置き換えて、2009 年の行だけがパーティションに含まれるようにします。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-146">In the SQL Statement, in-order for the partition to include only those rows for the 2009 year, replace the WHERE clause with the following:</span></span>  
  
    ```  
    WHERE (([OrderDate] >= N'2009-01-01 00:00:00') AND ([OrderDate] < N'2010-01-01 00:00:00'))  
    ```  
  
## <a name="process-partitions"></a><span data-ttu-id="5a3ef-147">パーティションの処理</span><span class="sxs-lookup"><span data-stu-id="5a3ef-147">Process Partitions</span></span>  
 <span data-ttu-id="5a3ef-148">**[パーティション マネージャー]** ダイアログ ボックスで、新たに作成した各パーティションのパーティション名の隣にアスタリスク (**\***) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-148">In the **Partition Manager** dialog box, notice the asterisk (**\***) next to the partition names for each of the new partitions you just created.</span></span> <span data-ttu-id="5a3ef-149">これは、パーティションがまだ処理 (更新) されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-149">This indicates that the partition has not been processed (refreshed).</span></span> <span data-ttu-id="5a3ef-150">新しいパーティションを作成したら、"パーティションの処理" または "テーブルの処理" 操作を実行して、それらのパーティション内のデータを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-150">When you create new partitions, you should run a Process Partitions or Process Table operation to refresh the data in those partitions.</span></span>  
  
#### <a name="to-process-internet-sales-partitions"></a><span data-ttu-id="5a3ef-151">Internet Sales パーティションを処理するには</span><span class="sxs-lookup"><span data-stu-id="5a3ef-151">To process Internet Sales partitions</span></span>  
  
1.  <span data-ttu-id="5a3ef-152">**[OK]** をクリックし、 **[パーティション マネージャー]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-152">Click **OK** to close the **Partition Manager** dialog box.</span></span>  
  
2.  <span data-ttu-id="5a3ef-153">モデル デザイナーで **[Internet Sales]** テーブルをクリックし、 **[モデル]** メニューをクリックした後、 **[処理]** (更新) をポイントし、 **[パーティションの処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-153">In the model designer, click the **Internet Sales** table, then click the **Model** menu, then point to **Process** (Refresh), and then click **Process Partitions**.</span></span>  
  
3.  <span data-ttu-id="5a3ef-154">**[パーティションの処理]** ダイアログ ボックスで、 **[モード]** が **[既定の処理]** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-154">In the **Process Partitions** dialog box, verify the **Mode** is set to **Process Default**.</span></span>  
  
4.  <span data-ttu-id="5a3ef-155">作成した 5 つのパーティションのそれぞれについて､ **[Process]** 列のチェックボックスを選択し､**[OK]** をクリックします｡</span><span class="sxs-lookup"><span data-stu-id="5a3ef-155">Select the checkbox in the **Process** column for each of the five partitions you created, and then click **OK**.</span></span>  
  
     <span data-ttu-id="5a3ef-156">権限借用資格情報の入力を求められた場合は、レッスン 2 の手順 6. で指定した、Windows のユーザー名とパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-156">If you are prompted for Impersonation credentials, enter the Windows user name and password you specified in Lesson 2, step 6.</span></span>  
  
     <span data-ttu-id="5a3ef-157">[**データ処理**] ダイアログボックスが表示され、各パーティションのプロセスの詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-157">The **Data Process** dialog box then appears and displays process details for each partition.</span></span> <span data-ttu-id="5a3ef-158">転送される行数はパーティションごとに異なります。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-158">Notice that a different number of rows for each partition are transferred.</span></span> <span data-ttu-id="5a3ef-159">これは、各パーティションに、SQL ステートメントの WHERE 句で指定された年の行が含められるためです。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-159">This is because each partition includes only those rows for the year specified in the WHERE clause in the SQL Statement.</span></span> <span data-ttu-id="5a3ef-160">2010 年についてはデータがありません。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-160">There is no data for the 2010 year.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5a3ef-161">次の手順</span><span class="sxs-lookup"><span data-stu-id="5a3ef-161">Next Steps</span></span>  
 <span data-ttu-id="5a3ef-162">このチュートリアルを続行するには、次のレッスン「 [レッスン 12: ロールの作成](lesson-11-create-roles.md)」に進んでください。</span><span class="sxs-lookup"><span data-stu-id="5a3ef-162">To continue this tutorial, go to the next lesson: Lesson: [Lesson 12: Create Roles](lesson-11-create-roles.md).</span></span>  
  
  
