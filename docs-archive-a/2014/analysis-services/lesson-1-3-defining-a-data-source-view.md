---
title: データソースビューの定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: af00938a-5a06-4fae-b2fc-f3fb0ca3cea5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7d59c5fbe5fd4a07596745447567a72499ddabd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631309"
---
# <a name="defining-a-data-source-view"></a><span data-ttu-id="25538-102">データ ソース ビューの定義</span><span class="sxs-lookup"><span data-stu-id="25538-102">Defining a Data Source View</span></span>
  <span data-ttu-id="25538-103">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトで使用するデータ ソースを定義した後は、一般に、プロジェクトのデータ ソース ビューを定義します。</span><span class="sxs-lookup"><span data-stu-id="25538-103">After you define the data sources that you will use in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, the next step is generally to define a data source view for the project.</span></span> <span data-ttu-id="25538-104">データ ソース ビューは、指定したテーブルのメタデータと、プロジェクトのデータ ソースによって定義されているビューを 1 つに統合したものです。</span><span class="sxs-lookup"><span data-stu-id="25538-104">A data source view is a single, unified view of the metadata from the specified tables and views that the data source defines in the project.</span></span> <span data-ttu-id="25538-105">データ ソース ビューにメタデータを格納すると、基になるデータ ソースへの接続を開かなくても、開発時にメタデータを操作することができます。</span><span class="sxs-lookup"><span data-stu-id="25538-105">Storing the metadata in the data source view enables you to work with the metadata during development without an open connection to any underlying data source.</span></span> <span data-ttu-id="25538-106">詳細については、 [「多次元モデルのデータ ソース ビュー」](multidimensional-models/data-source-views-in-multidimensional-models.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25538-106">For more information, see [Data Source Views in Multidimensional Models](multidimensional-models/data-source-views-in-multidimensional-models.md).</span></span>  
  
 <span data-ttu-id="25538-107">次の実習では、 **AdventureWorksDW2012** データ ソースの 5 つのテーブルを含むデータ ソース ビューを定義します。</span><span class="sxs-lookup"><span data-stu-id="25538-107">In the following task, you define a data source view that includes five tables from the **AdventureWorksDW2012** data source.</span></span>  
  
### <a name="to-define-a-new-data-source-view"></a><span data-ttu-id="25538-108">新しいデータ ソース ビューを定義するには</span><span class="sxs-lookup"><span data-stu-id="25538-108">To define a new data source view</span></span>  
  
1.  <span data-ttu-id="25538-109">ソリューション エクスプローラー (Microsoft Visual Studio ウィンドウの右側) で、[ **データ ソース ビュー**] を右クリックし、[ **新しいデータ ソース ビュー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25538-109">In Solution Explorer (on the right of the Microsoft Visual Studio window), right-click **Data Source Views**, and then click **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="25538-110">**[データ ソース ビュー ウィザードへようこそ]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25538-110">On the **Welcome to the Data Source View Wizard** page, click **Next**.</span></span> <span data-ttu-id="25538-111">[ **データ ソースの選択** ] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="25538-111">The **Select a Data Source** page appears.</span></span>  
  
3.  <span data-ttu-id="25538-112">[ **リレーショナル データ ソース**] の一覧で、[ **Adventure Works DW 2012** ] データ ソースが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="25538-112">Under **Relational data sources**, the **Adventure Works DW 2012** data source is selected.</span></span> <span data-ttu-id="25538-113">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25538-113">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="25538-114">複数のデータ ソースに基づくデータ ソース ビューを作成するには、まず、1 つのデータ ソースに基づくデータ ソース ビューを定義します。</span><span class="sxs-lookup"><span data-stu-id="25538-114">To create a data source view that is based on multiple data sources, first define a data source view that is based on a single data source.</span></span> <span data-ttu-id="25538-115">このデータ ソースをプライマリ データ ソースと呼びます。</span><span class="sxs-lookup"><span data-stu-id="25538-115">This data source is then called the primary data source.</span></span> <span data-ttu-id="25538-116">次に、2 番目のデータ ソースのテーブルとビューを追加します。</span><span class="sxs-lookup"><span data-stu-id="25538-116">You can then add tables and views from a secondary data source.</span></span> <span data-ttu-id="25538-117">複数のデータ ソースの関連するテーブルに基づいた属性を含むディメンションを設計する場合は、分散クエリ エンジン機能を使用するために、 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データ ソースをプライマリ データ ソースとして定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25538-117">When designing dimensions that contain attributes based on related tables in multiple data sources, you might need to define a [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data source as the primary data source to use its distributed query engine capabilities.</span></span>  
  
4.  <span data-ttu-id="25538-118">[ **テーブルとビューの選択** ] ページには、選択したデータ ソース内で使用できるオブジェクトの一覧が表示されます。この一覧からテーブルとビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="25538-118">On the **Select Tables and Views** page, select tables and views from the list of objects that are available from the selected data source.</span></span> <span data-ttu-id="25538-119">この一覧をフィルター処理すれば、目的のテーブルとビューを簡単に選択できるようになります。</span><span class="sxs-lookup"><span data-stu-id="25538-119">You can filter this list to help you select tables and views.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="25538-120">右上隅の最大化ボタンをクリックして、ウィンドウを全画面表示にします。</span><span class="sxs-lookup"><span data-stu-id="25538-120">Click the maximize button in the upper-right corner so that the window covers the full screen.</span></span> <span data-ttu-id="25538-121">これによって、使用できるオブジェクトの一覧全体を簡単に確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="25538-121">This makes it easier to see the complete list of available objects.</span></span>  
  
     <span data-ttu-id="25538-122">[ **使用できるオブジェクト** ] ボックスの一覧で、次のオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="25538-122">In the **Available objects** list, select the following objects.</span></span> <span data-ttu-id="25538-123">Ctrl キーを押しながらクリックすると、複数のテーブルを選択できます。</span><span class="sxs-lookup"><span data-stu-id="25538-123">You can select multiple tables by clicking each while holding down the CTRL key:</span></span>  
  
    -   <span data-ttu-id="25538-124">**DimCustomer (dbo)**</span><span class="sxs-lookup"><span data-stu-id="25538-124">**DimCustomer (dbo)**</span></span>  
  
    -   <span data-ttu-id="25538-125">**DimDate (dbo)**</span><span class="sxs-lookup"><span data-stu-id="25538-125">**DimDate (dbo)**</span></span>  
  
    -   <span data-ttu-id="25538-126">**DimGeography (dbo)**</span><span class="sxs-lookup"><span data-stu-id="25538-126">**DimGeography (dbo)**</span></span>  
  
    -   <span data-ttu-id="25538-127">**DimProduct (dbo)**</span><span class="sxs-lookup"><span data-stu-id="25538-127">**DimProduct (dbo)**</span></span>  
  
    -   <span data-ttu-id="25538-128">**FactInternetSales (dbo)**</span><span class="sxs-lookup"><span data-stu-id="25538-128">**FactInternetSales (dbo)**</span></span>  
  
5.  <span data-ttu-id="25538-129">クリック **>** すると、選択したテーブルが [**含まれているオブジェクト**] の一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="25538-129">Click **>** to add the selected tables to the **Included objects** list.</span></span>  
  
6.  <span data-ttu-id="25538-130">[**次へ] をクリックします。**</span><span class="sxs-lookup"><span data-stu-id="25538-130">Click **Next.**</span></span>  
  
7.  <span data-ttu-id="25538-131">[名前] フィールドに **Adventure Works DW 2012** と表示されていることを確認し、[ **完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25538-131">In the Name field, make sure **Adventure Works DW 2012** displays, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="25538-132">ソリューション エクスプローラーの [ **データ ソース ビュー** ] フォルダーに、 **Adventure Works DW 2012** データ ソース ビューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="25538-132">The **Adventure Works DW 2012** data source view appears in the **Data Source Views** folder in Solution Explorer.</span></span> <span data-ttu-id="25538-133">データ ソース ビューの内容は、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]のデータ ソース ビュー デザイナーにも表示されます。</span><span class="sxs-lookup"><span data-stu-id="25538-133">The content of the data source view is also displayed in Data Source View Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="25538-134">このデザイナーは次の要素で構成されています。</span><span class="sxs-lookup"><span data-stu-id="25538-134">This designer contains the following elements:</span></span>  
  
    -   <span data-ttu-id="25538-135">[ **ダイアグラム** ] ウィンドウ: テーブルおよびテーブル間のリレーションシップがグラフィカルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="25538-135">A **Diagram** pane in which the tables and their relationships are represented graphically.</span></span>  
  
    -   <span data-ttu-id="25538-136">[ **テーブル** ] ウィンドウ: テーブルとそのスキーマ要素が表示されます。</span><span class="sxs-lookup"><span data-stu-id="25538-136">A **Tables** pane in which the tables and their schema elements are displayed in a tree view.</span></span>  
  
    -   <span data-ttu-id="25538-137">[ **ダイアグラム オーガナイザー** ] ウィンドウ: サブダイアグラムを作成して、データ ソース ビューのサブセットを表示できます。</span><span class="sxs-lookup"><span data-stu-id="25538-137">A **Diagram Organizer** pane in which you can create subdiagrams so that you can view subsets of the data source view.</span></span>  
  
    -   <span data-ttu-id="25538-138">データ ソース ビュー デザイナーのツール バー</span><span class="sxs-lookup"><span data-stu-id="25538-138">A toolbar that is specific to Data Source View Designer.</span></span>  
  
8.  <span data-ttu-id="25538-139">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 開発環境を最大化するには、[ **最大化** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="25538-139">To maximize the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] development environment, click the **Maximize** button.</span></span>  
  
9. <span data-ttu-id="25538-140">[ **ダイアグラム** ] ウィンドウ内のテーブルを 50% の大きさで表示するには、データ ソース ビュー デザイナーのツール バーにある [ **ズーム** ] アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="25538-140">To view the tables in the **Diagram** pane at 50 percent, click the **Zoom** icon on the Data Source View Designer toolbar.</span></span> <span data-ttu-id="25538-141">表示サイズを 50% にすると、各テーブルの列の詳細が非表示になります。</span><span class="sxs-lookup"><span data-stu-id="25538-141">This will hide the column details of each table.</span></span>  
  
10. <span data-ttu-id="25538-142">ソリューション エクスプローラーを非表示にするには、[ **自動的に隠す** ] ボタン (タイトル バーの押しピン アイコン) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25538-142">To hide Solution Explorer, click the **Auto Hide** button, which is the pushpin icon on the title bar.</span></span> <span data-ttu-id="25538-143">再びソリューション エクスプローラーを表示するには、開発環境の右側に表示されているソリューション エクスプローラーのタブの上にポインターを置きます。</span><span class="sxs-lookup"><span data-stu-id="25538-143">To view Solution Explorer again, position your pointer over the Solution Explorer tab along the right side of the development environment.</span></span> <span data-ttu-id="25538-144">ソリューション エクスプローラーの非表示を解除するには、[ **自動的に隠す** ] ボタンを再びクリックします。</span><span class="sxs-lookup"><span data-stu-id="25538-144">To unhide Solution Explorer, click the **Auto Hide** button again.</span></span>  
  
11. <span data-ttu-id="25538-145">ウィンドウが既定で非表示になっていない場合は、[プロパティ] ウィンドウと [ソリューション エクスプローラー] ウィンドウのタイトル バーで [ **自動的に隠す** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="25538-145">If the windows are not hidden by default, click **Auto Hide** on the title bar of the Properties and Solution Explorer windows.</span></span>  
  
     <span data-ttu-id="25538-146">これで、[ **ダイアグラム** ] ウィンドウ内に、すべてのテーブルとそのリレーションシップを表示できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="25538-146">You can now view all the tables and their relationships in the **Diagram** pane.</span></span> <span data-ttu-id="25538-147">FactInternetSales テーブルと DimDate テーブルの間には 3 つのリレーションシップがあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="25538-147">Notice that there are three relationships between the FactInternetSales table and the DimDate table.</span></span> <span data-ttu-id="25538-148">各売上には、それぞれ 3 つの日付が関連付けられています。受注日、期日、出荷日の 3 つです。</span><span class="sxs-lookup"><span data-stu-id="25538-148">Each sale has three dates associated with the sale: an order date, a due date, and a ship date.</span></span> <span data-ttu-id="25538-149">リレーションシップの詳細を表示するには、[ **ダイアグラム** ] ウィンドウで、リレーションシップの矢印をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="25538-149">To view the details of any relationship, double-click the relationship arrow in the **Diagram** pane.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="25538-150">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="25538-150">Next Task in Lesson</span></span>  
 [<span data-ttu-id="25538-151">既定のテーブル名の変更</span><span class="sxs-lookup"><span data-stu-id="25538-151">Modifying Default Table Names</span></span>](lesson-1-4-modifying-default-table-names.md)  
  
## <a name="see-also"></a><span data-ttu-id="25538-152">参照</span><span class="sxs-lookup"><span data-stu-id="25538-152">See Also</span></span>  
 [<span data-ttu-id="25538-153">多次元モデル内のデータ ソース ビュー</span><span class="sxs-lookup"><span data-stu-id="25538-153">Data Source Views in Multidimensional Models</span></span>](multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
