---
title: 'レッスン 3 : テーブル レポートのデータセットの定義 (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ee93dfcb-8f52-4d63-b4f6-0d38e00fd350
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 33fe48a60db2e7d15d205a4bff6205347f95c61c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634314"
---
# <a name="lesson-3-defining-a-dataset-for-the-table-report-reporting-services"></a><span data-ttu-id="229e5-102">レッスン 3 : テーブル レポートのデータセットの定義 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="229e5-102">Lesson 3: Defining a Dataset for the Table Report (Reporting Services)</span></span>
  <span data-ttu-id="229e5-103">データ ソースを定義した後、データセットを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="229e5-103">After you define the data source, you need to define a dataset.</span></span> <span data-ttu-id="229e5-104">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]では、レポートで使用するデータは *データセット*に格納されます。</span><span class="sxs-lookup"><span data-stu-id="229e5-104">In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], data that you use in reports is contained in a *dataset*.</span></span> <span data-ttu-id="229e5-105">データセットには、データ ソースへのポインターと、レポートで使用されるクエリ、および計算フィールドと変数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="229e5-105">A dataset includes a pointer to a data source and a query to be used by the report, as well as calculated fields and variables.</span></span>  
  
 <span data-ttu-id="229e5-106">レポート デザイナーでクエリ デザイナーを使用すると、クエリをデザインできます。</span><span class="sxs-lookup"><span data-stu-id="229e5-106">You can use the query designer in Report Designer to design the query.</span></span> <span data-ttu-id="229e5-107">このチュートリアルでは、2008データベースから販売注文情報を取得するクエリを作成し [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] **2008**ます。</span><span class="sxs-lookup"><span data-stu-id="229e5-107">For this tutorial, you will create a query that retrieves sales order information from the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]**2008** database.</span></span>  
  
### <a name="to-define-a-transact-sql-query-for-report-data"></a><span data-ttu-id="229e5-108">レポート データ用に Transact-SQL クエリを定義するには</span><span class="sxs-lookup"><span data-stu-id="229e5-108">To define a Transact-SQL query for report data</span></span>  
  
1.  <span data-ttu-id="229e5-109">**レポートデータ**ペインで、[**新規作成**] をクリックし、[**データセット...**] をクリックします。[**データセットのプロパティ**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="229e5-109">In the **Report Data** pane, click **New**, and then click **Dataset...**. The **Dataset Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="229e5-110">**[名前]** ボックスに「 **AdventureWorksDataset**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="229e5-110">In the **Name** box, type **AdventureWorksDataset**.</span></span>  
  
3.  <span data-ttu-id="229e5-111">**[レポートに埋め込まれたデータセットを使用します]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="229e5-111">Click **Use a dataset embedded in my report**.</span></span>  
  
4.  <span data-ttu-id="229e5-112">データソース AdventureWorks2012 の名前が [**データソース**] ボックスに表示されていること、および [**クエリの種類**] が [**テキスト**] であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="229e5-112">Make sure the name of your data source, AdventureWorks2012, is in the **Data source** text box, and that the **Query type** is **Text**.</span></span>  
  
5.  <span data-ttu-id="229e5-113">**[クエリ]** ボックスに次の Transact-SQL クエリを入力するか、コピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="229e5-113">Type, or copy and paste, the following Transact-SQL query into the **Query** box.</span></span>  
  
    ```  
    SELECT   
       soh.OrderDate AS [Date],   
       soh.SalesOrderNumber AS [Order],   
       pps.Name AS Subcat, pp.Name as Product,    
       SUM(sd.OrderQty) AS Qty,  
       SUM(sd.LineTotal) AS LineTotal  
    FROM Sales.SalesPerson sp   
       INNER JOIN Sales.SalesOrderHeader AS soh   
          ON sp.BusinessEntityID = soh.SalesPersonID  
       INNER JOIN Sales.SalesOrderDetail AS sd   
          ON sd.SalesOrderID = soh.SalesOrderID  
       INNER JOIN Production.Product AS pp   
          ON sd.ProductID = pp.ProductID  
       INNER JOIN Production.ProductSubcategory AS pps   
          ON pp.ProductSubcategoryID = pps.ProductSubcategoryID  
       INNER JOIN Production.ProductCategory AS ppc   
          ON ppc.ProductCategoryID = pps.ProductCategoryID  
    GROUP BY ppc.Name, soh.OrderDate, soh.SalesOrderNumber, pps.Name, pp.Name,   
       soh.SalesPersonID  
    HAVING ppc.Name = 'Clothing'  
    ```  
  
6.  <span data-ttu-id="229e5-114">(省略可能) **[クエリ デザイナー]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="229e5-114">(Optional) Click the **Query Designer** button.</span></span> <span data-ttu-id="229e5-115">クエリは、テキスト ベースのクエリ デザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="229e5-115">The query is displayed in the text-based query designer.</span></span> <span data-ttu-id="229e5-116">**[テキストとして編集]** をクリックすると、グラフィカル クエリ デザイナーに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="229e5-116">You can toggle to the graphical query designer by clicking **Edit As Text**.</span></span> <span data-ttu-id="229e5-117">クエリデザイナーのツールバーの [実行] **(!)** ボタンをクリックして、クエリの結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="229e5-117">View the results of the query by clicking the run **(!)** button on the query designer toolbar.</span></span>  
  
     <span data-ttu-id="229e5-118">[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベースの 4 つの異なるテーブルの 6 個のフィールドから取得したデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="229e5-118">You see the data from six fields from four different tables in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="229e5-119">クエリでは、エイリアスなど Transact-SQL の機能が利用されます。</span><span class="sxs-lookup"><span data-stu-id="229e5-119">The query makes use of Transact-SQL functionality such as aliases.</span></span> <span data-ttu-id="229e5-120">たとえば、SalesOrderHeader テーブルは soh と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="229e5-120">For example, the SalesOrderHeader table is called soh.</span></span>  
  
     <span data-ttu-id="229e5-121">**[OK]** をクリックしてクエリ デザイナーを終了します。</span><span class="sxs-lookup"><span data-stu-id="229e5-121">Click **OK** to exit the query designer.</span></span>  
  
7.  <span data-ttu-id="229e5-122">**[OK]** をクリックして **[データセットのプロパティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="229e5-122">Click **OK** to exit the **Dataset Properties** dialog box.</span></span>  
  
     <span data-ttu-id="229e5-123">レポート データ ペインに **AdventureWorksDataset** データセットとフィールドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="229e5-123">Your **AdventureWorksDataset** dataset and fields appear in the Report Data pane.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="229e5-124">次の作業</span><span class="sxs-lookup"><span data-stu-id="229e5-124">Next Task</span></span>  
 <span data-ttu-id="229e5-125">これで、レポートのデータを取得するクエリを指定できました。</span><span class="sxs-lookup"><span data-stu-id="229e5-125">You have successfully specified a query that retrieves data for your report.</span></span> <span data-ttu-id="229e5-126">次に、レポートのレイアウトを作成します。</span><span class="sxs-lookup"><span data-stu-id="229e5-126">Next, you will create the report layout.</span></span> <span data-ttu-id="229e5-127">「[レッスン 4: レポートへのテーブルの追加 &#40;Reporting Services&#41;](lesson-4-adding-a-table-to-the-report-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="229e5-127">See [Lesson 4: Adding a Table to the Report &#40;Reporting Services&#41;](lesson-4-adding-a-table-to-the-report-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="229e5-128">参照</span><span class="sxs-lookup"><span data-stu-id="229e5-128">See Also</span></span>  
 <span data-ttu-id="229e5-129">[レポートデザイナー SQL Server Data Tools のクエリデザインツール &#40;SSRS&#41;](report-data/query-design-tools-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="229e5-129">[Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;](report-data/query-design-tools-ssrs.md) </span></span>  
 <span data-ttu-id="229e5-130">[SSRS&#41;&#40;の接続の種類の SQL Server](report-data/sql-server-connection-type-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="229e5-130">[SQL Server Connection Type &#40;SSRS&#41;](report-data/sql-server-connection-type-ssrs.md) </span></span>  
 [<span data-ttu-id="229e5-131">チュートリアル:Transact-SQL ステートメントの作成</span><span class="sxs-lookup"><span data-stu-id="229e5-131">Tutorial: Writing Transact-SQL Statements</span></span>](../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  
