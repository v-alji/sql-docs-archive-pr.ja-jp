---
title: データソースビューデザイナー (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.f1
helpviewer_keywords:
- Data Source View Designer
ms.assetid: 6f40a074-761f-440b-a999-09b755bd86ce
author: minewiskan
ms.author: owend
ms.openlocfilehash: 31e70f3f9b577f44b9ebb61b5ae2975c0a129828
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717000"
---
# <a name="data-source-view-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="3664f-102">データ ソース ビュー デザイナー (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="3664f-102">Data Source View Designer (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="3664f-103">データ ソース ビュー (DSV) は、多次元モデル内でキューブやディメンションを作成するために使用される外部リレーショナル データ ソースの論理ビューです。</span><span class="sxs-lookup"><span data-stu-id="3664f-103">A data source view (DSV) is a logical view of an external relational data source used to create cubes and dimensions in a multidimensional model.</span></span>

 <span data-ttu-id="3664f-104">DSV を生成した後、 **内で** データ ソース ビュー デザイナー [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] を使用して DSV を直接操作することができます。基になるデータ ソースで、多次元モデルで必要とされるデータ要素が欠落している場合に、この方法が役に立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="3664f-104">After a DSV is generated, you can use the **Data Source View Designer** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to work directly on the DSV, which can be useful if the underlying data source is missing data elements needed in a multidimensional model.</span></span>

 <span data-ttu-id="3664f-105">**データ ソース ビュー デザイナー** を開くには:</span><span class="sxs-lookup"><span data-stu-id="3664f-105">To open **Data Source View Designer** :</span></span>

-   <span data-ttu-id="3664f-106">**ソリューション エクスプローラー**でデータ ソース ビューをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="3664f-106">Double-click a data source view in **Solution Explorer**.</span></span>

-   <span data-ttu-id="3664f-107">**ソリューション エクスプローラー** のデータ ソース ビューを右クリックし、 **[開く]** または **[デザイナーの表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3664f-107">Right-click a data source view in **Solution Explorer** and select **Open** or **View Designer**.</span></span>

 <span data-ttu-id="3664f-108">**データ ソース ビュー デザイナー** には、ツール バー、DSV 内のオブジェクトとリレーションシップを示すダイアグラム、テーブルと名前付きクエリをアルファベット順に示すテーブル ペイン、および DSV の特定のダイアグラムを作成および表示するために使用する [ダイアグラム オーガナイザー] ペインがあります。</span><span class="sxs-lookup"><span data-stu-id="3664f-108">The **Data Source View Designer** contains a toolbar, a diagram showing the objects and relationships in the DSV, a table pane listing tables and named queries in alphabetical order, and a Diagram Organizer pane used to create and view specific diagrams of the DSV.</span></span> <span data-ttu-id="3664f-109">テーブルまたはリレーションシップを右クリックして、状況に依存するコマンドにアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="3664f-109">You can right-click a table or relationship to access context-sensitive commands.</span></span>

 <span data-ttu-id="3664f-110">![データ ソース ビュー デザイナー](media/ssas-dsvdesigner.PNG "データ ソース ビュー デザイナー")</span><span class="sxs-lookup"><span data-stu-id="3664f-110">![Data Source View Designer](media/ssas-dsvdesigner.PNG "Data Source View Designer")</span></span>

 <span data-ttu-id="3664f-111">少なくとも DSV には、処理中にモデル オブジェクトを設定するために使用されるリレーショナル データベース テーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3664f-111">At a minimum, a DSV shows the relational database tables that will be used to populate model objects during processing.</span></span> <span data-ttu-id="3664f-112">DSV は通常、データ ソース ビュー ウィザードを使用して生成します。</span><span class="sxs-lookup"><span data-stu-id="3664f-112">A DSV is generated, usually by using the Data Source View wizard.</span></span> <span data-ttu-id="3664f-113">DSV 内のテーブル、列、およびリレーションシップが、キューブ内にあるディメンションとメジャーの基準になります。</span><span class="sxs-lookup"><span data-stu-id="3664f-113">Tables, columns, and relationships in the DSV become the basis for dimensions and measures in a cube.</span></span> <span data-ttu-id="3664f-114">DSV を作成した後、データ ソース ビュー デザイナーを使用して変更を加えることができます。</span><span class="sxs-lookup"><span data-stu-id="3664f-114">Once the DSV is created, you can use the Data Source View Designer to modify it.</span></span>

 <span data-ttu-id="3664f-115">ほとんどの Analysis Services 開発者は、生成された DSV をほぼそのまま使用し、多少のカスタマイズを加えます。</span><span class="sxs-lookup"><span data-stu-id="3664f-115">Most Analysis Services developers use a generated DSV as is, with few customizations.</span></span> <span data-ttu-id="3664f-116">特に SQL Server データベース内のビューからソース データを生成する場合は、この方法が一般的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3664f-116">This is especially common if source data originates from a view in a SQL Server database.</span></span> <span data-ttu-id="3664f-117">その場合、Analysis Services DSV の代わりに、T-SQL ビュー内でデータのリレーションシップと計算を管理したいと考えることがあります。</span><span class="sxs-lookup"><span data-stu-id="3664f-117">In this case, you might prefer to manage data relationships and calculations in a T-SQL view rather than an Analysis Services DSV.</span></span> <span data-ttu-id="3664f-118">ただし、基になるデータベースの所有者でない場合は、Analysis Services 内で DSV を変更し、モデル内で使用するデータ構造の開発をさらに進めることができます。</span><span class="sxs-lookup"><span data-stu-id="3664f-118">However, if you are not the owner of the underlying database, you can modify the DSV in Analysis Services to further develop the data structures used in your model.</span></span>

## <a name="tasks-in-data-source-view-designer"></a><span data-ttu-id="3664f-119">データ ソース ビュー デザイナー内のタスク</span><span class="sxs-lookup"><span data-stu-id="3664f-119">Tasks in Data Source View Designer</span></span>
 <span data-ttu-id="3664f-120">データ ソース ビュー デザイナーを使用して、DSV に対して次の編集を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3664f-120">Using Data Source View Designer, you can make the following edits to a DSV:</span></span>

|||
|-|-|
|<span data-ttu-id="3664f-121">列またはテーブルの名前を変更するか、新しい計算列を作成する。</span><span class="sxs-lookup"><span data-stu-id="3664f-121">Rename columns or tables, or create new calculated columns.</span></span> <span data-ttu-id="3664f-122">たとえば、名と姓を結合して、新しフル ネーム列を作成します。</span><span class="sxs-lookup"><span data-stu-id="3664f-122">For example, concatenate a first name and last name into a new full-name column.</span></span>|[<span data-ttu-id="3664f-123">データ ソース ビューでの名前付き計算の定義 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="3664f-123">Define Named Calculations in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)|
|<span data-ttu-id="3664f-124">テーブルのリレーションシップの手動での追加</span><span class="sxs-lookup"><span data-stu-id="3664f-124">Manually add table relationships</span></span>|[<span data-ttu-id="3664f-125">データ ソース ビューでの論理リレーションシップの定義 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="3664f-125">Define Logical Relationships in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/define-logical-relationships-in-a-data-source-view-analysis-services.md)|
|<span data-ttu-id="3664f-126">T-SQL クエリに基づいて新しいオブジェクトを定義する、名前付きクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="3664f-126">Create a named query to define a new object based on a T-SQL query.</span></span>|[<span data-ttu-id="3664f-127">データ ソース ビューでの名前付きクエリの定義 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="3664f-127">Define Named Queries in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/define-named-queries-in-a-data-source-view-analysis-services.md)|
|<span data-ttu-id="3664f-128">基になるデータを探索し、モデル オブジェクトによって表される実際のデータ値を表示します。</span><span class="sxs-lookup"><span data-stu-id="3664f-128">Explore underlying data to view actual data values represented by model objects.</span></span><br /><br /> <span data-ttu-id="3664f-129">データ探索では、基になるディメンション テーブルやクエリから返されるデータを視覚的に検査し、コピーすることができます。</span><span class="sxs-lookup"><span data-stu-id="3664f-129">Data exploration lets you visually inspect and copy data that is returned from the underlying dimensional table or query.</span></span> <span data-ttu-id="3664f-130">既定では、データ探索には上から順に取得するサンプリング方法が使用され、サンプル数は 5,000 ですが、これらの設定は変更できます。</span><span class="sxs-lookup"><span data-stu-id="3664f-130">By default, data exploration uses the top count sampling methodology, with a sample count of 5000, but you can revise these settings.</span></span>|[<span data-ttu-id="3664f-131">データ ソース ビューでのデータの検索 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="3664f-131">Explore Data in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/explore-data-in-a-data-source-view-analysis-services.md)|
|<span data-ttu-id="3664f-132">DSV のテーブルとリレーションシップのすべてまたは一部の図示</span><span class="sxs-lookup"><span data-stu-id="3664f-132">Diagram all or part of the tables and relationships in a DSV</span></span>|[<span data-ttu-id="3664f-133">データ ソース ビュー デザイナーでのダイアグラムの操作 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="3664f-133">Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;</span></span>](multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)|

## <a name="see-also"></a><span data-ttu-id="3664f-134">参照</span><span class="sxs-lookup"><span data-stu-id="3664f-134">See Also</span></span>
 <span data-ttu-id="3664f-135">[多次元モデルのデータソースビュー](multidimensional-models/data-source-views-in-multidimensional-models.md) [&#40;Analysis Services データソースビューでのテーブルまたはビューの追加または削除&#41;](multidimensional-models/adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)</span><span class="sxs-lookup"><span data-stu-id="3664f-135">[Data Source Views in Multidimensional Models](multidimensional-models/data-source-views-in-multidimensional-models.md) [Adding or Removing Tables or Views in a Data Source View &#40;Analysis Services&#41;](multidimensional-models/adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)</span></span>


