---
title: 変更したバージョンの Analysis Services チュートリアルプロジェクトを使用する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 685aa217-de1b-4df2-bf22-095228c40775
author: minewiskan
ms.author: owend
ms.openlocfilehash: b833a05a567f37443cf89f7356a0855e0827ea73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642387"
---
# <a name="using-a-modified-version-of-the-analysis-services-tutorial-project"></a><span data-ttu-id="31cbd-102">Analysis Services チュートリアル プロジェクトの修正バージョンの使用</span><span class="sxs-lookup"><span data-stu-id="31cbd-102">Using a Modified Version of the Analysis Services Tutorial Project</span></span>
  <span data-ttu-id="31cbd-103">このチュートリアルの残りのレッスンでは、最初の 3 つのレッスンで作成した [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトの修正版を使用します。</span><span class="sxs-lookup"><span data-stu-id="31cbd-103">The remaining lessons in this tutorial are based on an enhanced version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project that you completed in the first three lessons.</span></span> <span data-ttu-id="31cbd-104">まず、新しいテーブルと名前付き計算が **Adventure Works DW 2012** データ ソース ビューに追加されています。次に、新しいディメンションがプロジェクトおよび [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブに追加されています。</span><span class="sxs-lookup"><span data-stu-id="31cbd-104">Additional tables and named calculations have been added to the **Adventure Works DW 2012** data source view, additional dimensions have been added to the project, and these new dimensions have been added to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span> <span data-ttu-id="31cbd-105">そして、2 つ目のメジャー グループが追加されています。このメジャー グループには、2 番目のファクト テーブルのメジャーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="31cbd-105">In addition, a second measure group has been added, which contains measures from a second fact table.</span></span> <span data-ttu-id="31cbd-106">修正されたこのプロジェクトを使用すれば、これまでに習得したスキルを繰り返し使用せずに、ビジネス インテリジェンス アプリケーションに機能を追加する方法を学習していくことができます。</span><span class="sxs-lookup"><span data-stu-id="31cbd-106">This enhanced project will enable you to continue learning how to add functionality to your business intelligence application without having to repeat the skills you have already learned.</span></span>  
  
 <span data-ttu-id="31cbd-107">チュートリアルを続ける前に、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトの修正版のダウンロード、展開、読み込み、および処理を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="31cbd-107">Before you can continue with the tutorial, you must download, extract, load and process the enhanced version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project.</span></span>  <span data-ttu-id="31cbd-108">すべての手順を確実に実行するために、このレッスンでの指示に従ってください。</span><span class="sxs-lookup"><span data-stu-id="31cbd-108">Use the instructions in this lesson to ensure you have performed all the steps.</span></span>  
  
## <a name="downloading-and-extracting-the-project-file"></a><span data-ttu-id="31cbd-109">プロジェクト ファイルのダウンロードと展開</span><span class="sxs-lookup"><span data-stu-id="31cbd-109">Downloading and Extracting the Project File</span></span>  
  
1.  <span data-ttu-id="31cbd-110">このチュートリアルのサンプル プロジェクトをダウンロードできるページに移動するには、[ここをクリック](https://go.microsoft.com/fwlink/?LinkID=221866) してください。</span><span class="sxs-lookup"><span data-stu-id="31cbd-110">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to go to the download page that provides the sample projects that go with this tutorial.</span></span> <span data-ttu-id="31cbd-111">チュートリアルのプロジェクトは、 **Analysis Services Tutorial SQL Server 2012** ダウンロードに含まれています。</span><span class="sxs-lookup"><span data-stu-id="31cbd-111">The tutorial projects are included in the **Analysis Services Tutorial SQL Server 2012** download.</span></span>  
  
2.  <span data-ttu-id="31cbd-112">このチュートリアルのプロジェクトを含むパッケージをダウンロードするには、 **[Analysis Services Tutorial SQL Server 2012]** をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="31cbd-112">Click **Analysis Services Tutorial SQL Server 2012** to download the package that contains the projects for this tutorial.</span></span>  
  
     <span data-ttu-id="31cbd-113">既定では、.zip ファイルはダウンロード フォルダーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="31cbd-113">By default, a .zip file is saved to the Downloads folder.</span></span> <span data-ttu-id="31cbd-114">より短いパスの場所に .zip ファイルを移動する必要があります (たとえば、ファイルを保存するための C:\Tutorials フォルダーを作成します)。</span><span class="sxs-lookup"><span data-stu-id="31cbd-114">You must move the .zip file to a location that has a shorter path (for example, create a C:\Tutorials folder to store the files).</span></span>  <span data-ttu-id="31cbd-115">その後、.zip ファイルに含まれているファイルを展開します。</span><span class="sxs-lookup"><span data-stu-id="31cbd-115">You can then extract the files contained in the .zip file.</span></span> <span data-ttu-id="31cbd-116">長いパスのダウンロード フォルダーからファイルを解凍しようとすると、レッスン 1 しか取得できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="31cbd-116">If you attempt to unzip the files from the Downloads folder, which has a longer path, you will only get Lesson 1.</span></span>  
  
3.  <span data-ttu-id="31cbd-117">ルート ドライブか、それに近い場所にサブフォルダーを作成します (C:\Tutorial など）。</span><span class="sxs-lookup"><span data-stu-id="31cbd-117">Create a subfolder at or near the root drive, for example, C:\Tutorial.</span></span>  
  
4.  <span data-ttu-id="31cbd-118">そのサブフォルダーに、 **Analysis Services Tutorial SQL Server 2012.zip** ファイルを移動します。</span><span class="sxs-lookup"><span data-stu-id="31cbd-118">Move the **Analysis Services Tutorial SQL Server 2012.zip** file to the subfolder.</span></span>  
  
5.  <span data-ttu-id="31cbd-119">ファイルを右クリックし、 **[すべて展開]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31cbd-119">Right-click the file and select **Extract All**.</span></span>  
  
6.  <span data-ttu-id="31cbd-120">**Lesson 4 Start** フォルダーに移動して、 **Analysis Services Tutorial.sln** ファイルを見つけます。</span><span class="sxs-lookup"><span data-stu-id="31cbd-120">Browse to the **Lesson 4 Start** folder to find the **Analysis Services Tutorial.sln** file.</span></span>  
  
## <a name="loading-and-processing-the-enhanced-project"></a><span data-ttu-id="31cbd-121">修正したプロジェクトの読み込みと処理</span><span class="sxs-lookup"><span data-stu-id="31cbd-121">Loading and Processing the Enhanced Project</span></span>  
  
1.  <span data-ttu-id="31cbd-122">で、 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] [**ファイル**] メニューの [**ソリューションを閉じる**] をクリックして、使用しないファイルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="31cbd-122">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **File** menu, click **Close Solution** to close files you won't be using.</span></span>  
  
2.  <span data-ttu-id="31cbd-123">**[ファイル]** メニューの **[開く]** をポイントし、 **[プロジェクト/ソリューション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31cbd-123">On the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="31cbd-124">チュートリアルのプロジェクト ファイルを展開した場所を参照します。</span><span class="sxs-lookup"><span data-stu-id="31cbd-124">Browse to the location where you extracted the tutorial project files.</span></span>  
  
     <span data-ttu-id="31cbd-125">**Lesson 4 Start**という名前のフォルダーを見つけて、Analysis Services Tutorial.sln をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="31cbd-125">Find the folder named **Lesson 4 Start**, and then double-click Analysis Services Tutorial.sln.</span></span>  
  
4.  <span data-ttu-id="31cbd-126">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトの修正版を、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のローカル インスタンスに配置します。別のインスタンスに配置することもできますが、処理が正常に完了することを確認してください。</span><span class="sxs-lookup"><span data-stu-id="31cbd-126">Deploy the enhanced version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project to the local instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], or to another instance, and verify that processing completes successfully.</span></span>  
  
## <a name="understanding-the-enhancements-to-the-project"></a><span data-ttu-id="31cbd-127">プロジェクトの修正について</span><span class="sxs-lookup"><span data-stu-id="31cbd-127">Understanding the Enhancements to the Project</span></span>  
 <span data-ttu-id="31cbd-128">プロジェクトの修正版は、最初の 3 つのレッスンで作成した [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトとは異なります。</span><span class="sxs-lookup"><span data-stu-id="31cbd-128">The enhanced version of the project is different from the version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project that you completed in the first three lessons.</span></span> <span data-ttu-id="31cbd-129">この相違点について、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="31cbd-129">The differences are described in the following sections.</span></span> <span data-ttu-id="31cbd-130">チュートリアルの残りのレッスンを続ける前に、この情報を確認してください。</span><span class="sxs-lookup"><span data-stu-id="31cbd-130">Review this information before continuing with the remaining lessons in the tutorial.</span></span>  
  
### <a name="data-source-view"></a><span data-ttu-id="31cbd-131">[データ ソース ビュー]</span><span class="sxs-lookup"><span data-stu-id="31cbd-131">Data Source View</span></span>  
 <span data-ttu-id="31cbd-132">修正したプロジェクトのデータ ソース ビューには、 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データベースから取得された 1 つのファクト テーブルと 4 つのディメンション テーブルが追加されています。</span><span class="sxs-lookup"><span data-stu-id="31cbd-132">The data source view in the enhanced project contains one additional fact table and four additional dimension tables from the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span>  
  
 <span data-ttu-id="31cbd-133">このデータ ソース ビューには 10 個のテーブルがあり、 \<All Tables> ダイアグラムの情報が整理されていません。</span><span class="sxs-lookup"><span data-stu-id="31cbd-133">Notice that with ten tables in the data source view, the \<All Tables> diagram is becoming crowded.</span></span> <span data-ttu-id="31cbd-134">このため、テーブル間のリレーションシップがわかりにくく、簡単には特定のテーブルを探すことができません。</span><span class="sxs-lookup"><span data-stu-id="31cbd-134">This makes it difficult to easily understand the relationships between the tables and to locate specific tables.</span></span> <span data-ttu-id="31cbd-135">この問題を解決するために、テーブルを 2 つの論理ダイアグラムに整理します。2 つのダイアグラムとは、 **Internet Sales** ダイアグラムと **Reseller Sales** ダイアグラムです。</span><span class="sxs-lookup"><span data-stu-id="31cbd-135">To solve this problem, the tables are organized into two logical diagrams, the **Internet Sales** diagram and the **Reseller Sales** diagram.</span></span> <span data-ttu-id="31cbd-136">1 つのファクト テーブルに対し、これらのダイアグラムを 1 つずつ構成します。</span><span class="sxs-lookup"><span data-stu-id="31cbd-136">These diagrams are each organized around a single fact table.</span></span> <span data-ttu-id="31cbd-137">1 つのダイアグラムにテーブルやそのリレーションシップをすべて表示しなくとも、論理ダイアグラムを作成することにより、複数のテーブルから特定のサブセットのみをデータ ソース ビューに表示し、操作できます。</span><span class="sxs-lookup"><span data-stu-id="31cbd-137">Creating logical diagrams lets you view and work with a specific subset of the tables in a data source view instead of always viewing all the tables and their relationships in a single diagram.</span></span>  
  
#### <a name="internet-sales-diagram"></a><span data-ttu-id="31cbd-138">Internet Sales ダイアグラム</span><span class="sxs-lookup"><span data-stu-id="31cbd-138">Internet Sales Diagram</span></span>  
 <span data-ttu-id="31cbd-139">**Internet Sales** ダイアグラムには、インターネット経由で直接顧客に販売された、 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] 製品の売上に関連するテーブルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="31cbd-139">The **Internet Sales** diagram contains the tables that are related to the sale of [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] products directly to customers through the Internet.</span></span> <span data-ttu-id="31cbd-140">このダイアグラムには、レッスン 1 で **Adventure Works DW 2012** データ ソース ビューに追加した、4 つのディメンション テーブルと 1 つのファクト テーブルがあります。</span><span class="sxs-lookup"><span data-stu-id="31cbd-140">The tables in the diagram are the four dimension tables and one fact table that you added to the **Adventure Works DW 2012** data source view in Lesson 1.</span></span> <span data-ttu-id="31cbd-141">これらのテーブルを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="31cbd-141">These tables are as follows:</span></span>  
  
-   <span data-ttu-id="31cbd-142">**地理的な場所**</span><span class="sxs-lookup"><span data-stu-id="31cbd-142">**Geography**</span></span>  
  
-   <span data-ttu-id="31cbd-143">**Customer**</span><span class="sxs-lookup"><span data-stu-id="31cbd-143">**Customer**</span></span>  
  
-   <span data-ttu-id="31cbd-144">**日付**</span><span class="sxs-lookup"><span data-stu-id="31cbd-144">**Date**</span></span>  
  
-   <span data-ttu-id="31cbd-145">**Product**</span><span class="sxs-lookup"><span data-stu-id="31cbd-145">**Product**</span></span>  
  
-   <span data-ttu-id="31cbd-146">**InternetSales**</span><span class="sxs-lookup"><span data-stu-id="31cbd-146">**InternetSales**</span></span>  
  
#### <a name="reseller-sales-diagram"></a><span data-ttu-id="31cbd-147">Reseller Sales ダイアグラム</span><span class="sxs-lookup"><span data-stu-id="31cbd-147">Reseller Sales Diagram</span></span>  
 <span data-ttu-id="31cbd-148">**Reseller Sales** ダイアグラムには、販売店による [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] 製品の売上に関するテーブルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="31cbd-148">The **Reseller Sales** diagram contains the tables that are related to the sale of [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] products by resellers.</span></span> <span data-ttu-id="31cbd-149">このダイアグラムには、 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データベースから取得された、次の 7 つのディメンション テーブルと 1 つのファクト テーブルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="31cbd-149">This diagram contains the following seven dimension tables and one fact table from the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database:</span></span>  
  
-   <span data-ttu-id="31cbd-150">**Reseller**</span><span class="sxs-lookup"><span data-stu-id="31cbd-150">**Reseller**</span></span>  
  
-   <span data-ttu-id="31cbd-151">**Promotion**</span><span class="sxs-lookup"><span data-stu-id="31cbd-151">**Promotion**</span></span>  
  
-   <span data-ttu-id="31cbd-152">**SalesTerritory**</span><span class="sxs-lookup"><span data-stu-id="31cbd-152">**SalesTerritory**</span></span>  
  
-   <span data-ttu-id="31cbd-153">**地理的な場所**</span><span class="sxs-lookup"><span data-stu-id="31cbd-153">**Geography**</span></span>  
  
-   <span data-ttu-id="31cbd-154">**日付**</span><span class="sxs-lookup"><span data-stu-id="31cbd-154">**Date**</span></span>  
  
-   <span data-ttu-id="31cbd-155">**Product**</span><span class="sxs-lookup"><span data-stu-id="31cbd-155">**Product**</span></span>  
  
-   <span data-ttu-id="31cbd-156">**Employee**</span><span class="sxs-lookup"><span data-stu-id="31cbd-156">**Employee**</span></span>  
  
-   <span data-ttu-id="31cbd-157">**ResellerSales**</span><span class="sxs-lookup"><span data-stu-id="31cbd-157">**ResellerSales**</span></span>  
  
 <span data-ttu-id="31cbd-158">**DimGeography**、 **DimDate**、および **DimProduct** テーブルは、 **Internet Sales** ダイアグラムと **Reseller Sales** ダイアグラムの両方で使用されます。</span><span class="sxs-lookup"><span data-stu-id="31cbd-158">Notice that the **DimGeography**, **DimDate**, and **DimProduct** tables are used in both the **Internet Sales** diagram and the **Reseller Sales** diagram.</span></span> <span data-ttu-id="31cbd-159">ディメンション テーブルは、複数のファクト テーブルにリンクさせることができます。</span><span class="sxs-lookup"><span data-stu-id="31cbd-159">Dimension tables can be linked to multiple fact tables.</span></span>  
  
### <a name="database-and-cube-dimensions"></a><span data-ttu-id="31cbd-160">データベースとキューブ ディメンション</span><span class="sxs-lookup"><span data-stu-id="31cbd-160">Database and Cube Dimensions</span></span>  
 <span data-ttu-id="31cbd-161">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトには、5 つの新しいデータベース ディメンションがあります。また、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブは、これらと同じ 5 つのディメンションをキューブ ディメンションとして保持します。</span><span class="sxs-lookup"><span data-stu-id="31cbd-161">The [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project contains five new database dimensions, and the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube contains these same five dimensions as cube dimensions.</span></span> <span data-ttu-id="31cbd-162">これらのディメンションには、名前付き計算、複合メンバー キー、および表示フォルダーを使用しながら修正したユーザー階層とユーザー属性が存在します (そのようなユーザー階層とユーザー属性を持つようにディメンションが定義されています)。</span><span class="sxs-lookup"><span data-stu-id="31cbd-162">These dimensions have been defined to have user hierarchies and attributes that were modified by using named calculations, composition member keys, and display folders.</span></span> <span data-ttu-id="31cbd-163">この新しいディメンションの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="31cbd-163">The new dimensions are described in the following list.</span></span>  
  
 <span data-ttu-id="31cbd-164">Reseller ディメンション</span><span class="sxs-lookup"><span data-stu-id="31cbd-164">Reseller Dimension</span></span>  
 <span data-ttu-id="31cbd-165">Reseller ディメンションは、 **Adventure Works DW 2012** データ ソース ビューの **Reseller** テーブルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="31cbd-165">The Reseller dimension is based on the **Reseller** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
 <span data-ttu-id="31cbd-166">Promotion ディメンション</span><span class="sxs-lookup"><span data-stu-id="31cbd-166">Promotion Dimension</span></span>  
 <span data-ttu-id="31cbd-167">Promotion ディメンションは、 **Adventure Works DW 2012** データ ソース ビューの **Promotion** テーブルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="31cbd-167">The Promotion dimension is based on the **Promotion** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
 <span data-ttu-id="31cbd-168">Sales Territory ディメンション</span><span class="sxs-lookup"><span data-stu-id="31cbd-168">Sales Territory Dimension</span></span>  
 <span data-ttu-id="31cbd-169">Sales Territory ディメンションは、 **Adventure Works DW 2012** データ ソース ビューの **Sales Territory** テーブルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="31cbd-169">The Sales Territory dimension is based on the **SalesTerritory** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
 <span data-ttu-id="31cbd-170">Employee ディメンション</span><span class="sxs-lookup"><span data-stu-id="31cbd-170">Employee Dimension</span></span>  
 <span data-ttu-id="31cbd-171">Employee ディメンションは、 **Adventure Works DW 2012** データ ソース ビューの **Employee** テーブルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="31cbd-171">The Employee dimension is based on the **Employee** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
 <span data-ttu-id="31cbd-172">Geography ディメンション</span><span class="sxs-lookup"><span data-stu-id="31cbd-172">Geography Dimension</span></span>  
 <span data-ttu-id="31cbd-173">Geography ディメンションは、 **Adventure Works DW 2012** データ ソース ビューの **Geography** テーブルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="31cbd-173">The Geography dimension is based on the **Geography** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
#### <a name="analysis-services-cube"></a><span data-ttu-id="31cbd-174">Analysis Services キューブ</span><span class="sxs-lookup"><span data-stu-id="31cbd-174">Analysis Services Cube</span></span>  
 <span data-ttu-id="31cbd-175">**Analysis Services Tutorial** キューブには 2 つのメジャー グループがあります。1 つは、 **InternetSales** テーブルに基づく元のメジャー グループ、もう 1 つは、 **Adventure Works DW 2012** データ ソース ビューの **ResellerSales** テーブルに基づくメジャー グループです。</span><span class="sxs-lookup"><span data-stu-id="31cbd-175">The **Analysis Services Tutorial** cube now contains two measure groups, the original measure group based on the **InternetSales** table and a second measure group based on the **ResellerSales** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="31cbd-176">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="31cbd-176">Next Task in Lesson</span></span>  
 [<span data-ttu-id="31cbd-177">親子階層の親属性プロパティの定義</span><span class="sxs-lookup"><span data-stu-id="31cbd-177">Defining Parent Attribute Properties in a Parent-Child Hierarchy</span></span>](lesson-4-2-defining-parent-attribute-properties-in-a-parent-child-hierarchy.md) 
  
## <a name="see-also"></a><span data-ttu-id="31cbd-178">参照</span><span class="sxs-lookup"><span data-stu-id="31cbd-178">See Also</span></span>  
 [<span data-ttu-id="31cbd-179">Analysis Services プロジェクトの配置</span><span class="sxs-lookup"><span data-stu-id="31cbd-179">Deploying an Analysis Services Project</span></span>](lesson-2-5-deploying-an-analysis-services-project.md)  
  
  
