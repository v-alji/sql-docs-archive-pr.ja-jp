---
title: SQL Server 2014 | のレポートビルダーMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10428"
helpviewer_keywords:
- overview of Report Builder
- getting started
ms.assetid: 55bf4f9c-d037-412f-ae57-3fc39ce32fa5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b2fb8994272eb24594239551d623021f7b87694c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632946"
---
# <a name="report-builder-in-sql-server-2014"></a><span data-ttu-id="e06eb-102">SQL Server 2014 のレポート ビルダー</span><span class="sxs-lookup"><span data-stu-id="e06eb-102">Report Builder in SQL Server 2014</span></span>
  <span data-ttu-id="e06eb-103">レポートビルダーは、Office 環境での作業を好むビジネスユーザー向けのレポート作成環境 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] です。</span><span class="sxs-lookup"><span data-stu-id="e06eb-103">Report Builder is a report authoring environment for business users who prefer to work in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office environment.</span></span> <span data-ttu-id="e06eb-104">レポートをデザインする際には、データの取得場所、取得するデータ、およびデータの表示方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="e06eb-104">When you design a report, you specify where to get the data, which data to get, and how to display the data.</span></span> <span data-ttu-id="e06eb-105">レポートを実行すると、指定した情報がすべてレポート プロセッサに渡されます。レポート プロセッサは、データを取得し、それをレポート レイアウトに結合して、レポートを生成します。</span><span class="sxs-lookup"><span data-stu-id="e06eb-105">When you run the report, the report processor takes all the information you have specified, retrieves the data, and combines it with the report layout to generate the report.</span></span> <span data-ttu-id="e06eb-106">レポート ビルダーでレポートをプレビューすることも、レポート サーバーまたは SharePoint 統合モードのレポート サーバーにレポートをパブリッシュして、他のユーザーがそこからレポートを実行できるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="e06eb-106">You can preview your reports in Report Builder, or you can publish your report to a report server or a report server in SharePoint integrated mode, where others can run it.</span></span>  
  
 <span data-ttu-id="e06eb-107">この図に示すレポートでは、行グループ、列グループ、スパークライン、インジケーター、およびコーナー セルの概要円グラフが含まれたマトリックスが使用されています。色と円サイズで表される 2 組の地理データが含まれた地図も使用されています。</span><span class="sxs-lookup"><span data-stu-id="e06eb-107">The report in this illustration features a matrix with row and column groups, sparklines, indicators, and a summary pie chart in the corner cell, accompanied by a map with two sets of geographic data represented by color and by circle size.</span></span>  
  
 <span data-ttu-id="e06eb-108">![rs_GettingStartedReport](../media/rs-gettingstartedreport.gif "rs_GettingStartedReport")</span><span class="sxs-lookup"><span data-stu-id="e06eb-108">![rs_GettingStartedReport](../media/rs-gettingstartedreport.gif "rs_GettingStartedReport")</span></span>  
  
##  <a name="jump-start-report-creation"></a><a name="JumpStartReptCreation"></a><span data-ttu-id="e06eb-109">レポート作成の開始</span><span class="sxs-lookup"><span data-stu-id="e06eb-109">Jump-Start Report Creation</span></span>  
  
-   <span data-ttu-id="e06eb-110">チームの他のユーザーによって作成された**レポートパーツを使用して、レポートを開始**します。</span><span class="sxs-lookup"><span data-stu-id="e06eb-110">**Start your report withreport parts** created by someone else on your team.</span></span> <span data-ttu-id="e06eb-111">レポート パーツとは、レポート サーバー、またはレポート サーバーに統合されている SharePoint サイトに、個別にパブリッシュされたレポート アイテムです。</span><span class="sxs-lookup"><span data-stu-id="e06eb-111">Report parts are report items that have been published separately to a report server or a SharePoint site that is integrated with a report server.</span></span> <span data-ttu-id="e06eb-112">これらは、他のレポートに再利用できます。</span><span class="sxs-lookup"><span data-stu-id="e06eb-112">They can be reused in other reports.</span></span> <span data-ttu-id="e06eb-113">テーブル、マトリックス、グラフ、画像などのレポート アイテムを、レポート パーツとしてパブリッシュできます。</span><span class="sxs-lookup"><span data-stu-id="e06eb-113">Report items such as tables, matrices, charts, and images can be published as report parts.</span></span>  
  
-   <span data-ttu-id="e06eb-114">チーム内の他のユーザーによって作成された**共有データセットを使用**して開始します。</span><span class="sxs-lookup"><span data-stu-id="e06eb-114">**Start with a shared dataset** created by someone else on your team.</span></span> <span data-ttu-id="e06eb-115">共有データセットは、共有データ ソースに基づくクエリで、レポート サーバーまたはレポート サーバーに統合されている SharePoint サイトに保存されます。</span><span class="sxs-lookup"><span data-stu-id="e06eb-115">Shared datasets are queries based on a shared data source that are saved to a report server or a SharePoint site that is integrated with a report server.</span></span>  
  
-   <span data-ttu-id="e06eb-116">**テーブル、マトリックス、またはグラフ ウィザードから開始します**。</span><span class="sxs-lookup"><span data-stu-id="e06eb-116">**Start with the Table, Matrix, or Chart wizard**.</span></span> <span data-ttu-id="e06eb-117">データ ソース接続を選択したり、フィールドをドラッグ アンド ドロップしてデータセット クエリを作成したりできます。また、レイアウトとスタイルを選択して、レポートをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="e06eb-117">Choose a data source connection, drag and drop fields to create a dataset query, select a layout and style, and customize your report.</span></span>  
  
-   <span data-ttu-id="e06eb-118">**マップ ウィザードを使用して開始します**。地図や幾何図形を背景として集計データを表示するレポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="e06eb-118">**Start with the Map wizard** to create reports that display aggregated data against a geographic or geometric background.</span></span> <span data-ttu-id="e06eb-119">マップ データには、 [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリや Environmental Systems Research Institute, Inc. (ESRI) シェープファイルの空間データを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e06eb-119">Map data can be spatial data from a [!INCLUDE[tsql](../../includes/tsql-md.md)] query or an Environmental Systems Research Institute, Inc. (ESRI) shapefile.</span></span> <span data-ttu-id="e06eb-120">また、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Bing のマップ タイルの背景を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="e06eb-120">You can also add a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Bing map tile background.</span></span>  
  

  
##  <a name="design-your-report"></a><a name="DesignRept"></a><span data-ttu-id="e06eb-121">レポートをデザインする</span><span class="sxs-lookup"><span data-stu-id="e06eb-121">Design Your Report</span></span>  
  
-   <span data-ttu-id="e06eb-122">**テーブル、マトリックス、グラフ、および自由形式のレポート レイアウトのレポートを作成します。**</span><span class="sxs-lookup"><span data-stu-id="e06eb-122">**Create reports with table, matrix, chart, and free-form report layouts.**</span></span> <span data-ttu-id="e06eb-123">列ベースのデータ向けのテーブル レポート、概要データ向けのマトリックス レポート (クロス集計レポートやピボットテーブル レポートなど)、グラフィカル データ向けのグラフ レポート、およびそれ以外のすべて向けの自由形式レポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="e06eb-123">Create table reports for column-based data, matrix reports (like cross-tab or PivotTable reports) for summarized data, chart reports for graphical data, and free-form reports for anything else.</span></span> <span data-ttu-id="e06eb-124">他のレポートやグラフを、リスト、グラフィック、および動的な Web ベースのアプリケーション用のコントロールと共に、レポートに埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="e06eb-124">Reports can embed other reports and charts, together with lists, graphics, and controls for dynamic Web-based applications.</span></span>  
  
-   <span data-ttu-id="e06eb-125">**さまざまなデータ ソースからのレポート。**</span><span class="sxs-lookup"><span data-stu-id="e06eb-125">**Report from a variety of data sources.**</span></span> <span data-ttu-id="e06eb-126">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] マネージデータプロバイダー、OLE DB プロバイダー、または ODBC データソースを持つ任意のデータソースの種類のデータを使用して、レポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="e06eb-126">Build reports using data from any data source type that has a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-managed data provider, OLE DB provider, or ODBC data source.</span></span> <span data-ttu-id="e06eb-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、Oracle、Hyperion、およびその他のデータベースのリレーショナル データおよび多次元データを使用するレポートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e06eb-127">You can create reports that use relational and multidimensional data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], Oracle, Hyperion, and other databases.</span></span> <span data-ttu-id="e06eb-128">XML データ処理拡張機能を使用すると、任意の XML データ ソースからデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="e06eb-128">You can use an XML data processing extension to retrieve data from any XML data source.</span></span> <span data-ttu-id="e06eb-129">テーブル値関数を使用すると、カスタム データ ソースをデザインできます。</span><span class="sxs-lookup"><span data-stu-id="e06eb-129">You can use table-valued functions to design custom data sources.</span></span>  
  
-   <span data-ttu-id="e06eb-130">**既存のレポートを変更する。**</span><span class="sxs-lookup"><span data-stu-id="e06eb-130">**Modify existing reports.**</span></span> <span data-ttu-id="e06eb-131">レポートビルダーを使用すると、レポートデザイナーで作成されたレポートをカスタマイズおよび更新でき [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="e06eb-131">By using Report Builder, you can customize and update reports that were created in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]Report Designer.</span></span>  
  
-   <span data-ttu-id="e06eb-132">データのフィルター処理、グループ化と並べ替え、または数式や式の追加によって、**データを変更**します。</span><span class="sxs-lookup"><span data-stu-id="e06eb-132">**Modify your data** by filtering, grouping and sorting data, or by adding formulas or expressions.</span></span>  
  
-   <span data-ttu-id="e06eb-133">データをビジュアルな形式でまとめ、大量の集計情報がひとめでわかるようにするため、**グラフ、ゲージ、スパークライン、およびインジケーターを追加します。**</span><span class="sxs-lookup"><span data-stu-id="e06eb-133">**Add charts, gauges, sparklines, and indicators** to summarize data in a visual format, and present large volumes of aggregated information at a glance.</span></span>  
  
-   <span data-ttu-id="e06eb-134">ドキュメント マップ、表示/非表示ボタン、サブレポートと詳細レポートへのドリルスルー リンクなどの**対話機能を追加します。**</span><span class="sxs-lookup"><span data-stu-id="e06eb-134">**Add interactive features** such as document maps, show/hide buttons, and drillthrough links to subreports and drillthrough reports.</span></span> <span data-ttu-id="e06eb-135">パラメーターとフィルターを使用し、データをフィルター処理してビューをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="e06eb-135">Use parameters and filters to filter data for customized views.</span></span>  
  
-   <span data-ttu-id="e06eb-136">画像や外部コンテンツなどの他のリソースを**埋め込んだり参照したりします。**</span><span class="sxs-lookup"><span data-stu-id="e06eb-136">**Embed or reference images** and other resources, including external content.</span></span>  
  

  
##  <a name="manage-your-report"></a><a name="ManageRpt"></a><span data-ttu-id="e06eb-137">レポートの管理</span><span class="sxs-lookup"><span data-stu-id="e06eb-137">Manage Your Report</span></span>  
  
-   <span data-ttu-id="e06eb-138">コンピューターまたはレポート サーバーに**レポートの定義を保存**して、レポートの管理と他のユーザーとの共有を実行できます。</span><span class="sxs-lookup"><span data-stu-id="e06eb-138">**Save the definition of the report** to your computer or to the report server, where you can manage it and share it with others.</span></span>  
  
-   <span data-ttu-id="e06eb-139">レポートを開くとき、またはレポートを開いた後で**表示形式を選択します**。</span><span class="sxs-lookup"><span data-stu-id="e06eb-139">**Choose a presentation format** when you open the report, or after you open the report.</span></span> <span data-ttu-id="e06eb-140">Web 指向、ページ指向、およびデスクトップ アプリケーション形式を選択できます。</span><span class="sxs-lookup"><span data-stu-id="e06eb-140">You can select Web-oriented, page-oriented, and desktop application formats.</span></span> <span data-ttu-id="e06eb-141">形式には、HTML、MHTML、PDF、XML、CSV、TIFF、Word、および Excel があります。</span><span class="sxs-lookup"><span data-stu-id="e06eb-141">Formats include HTML, MHTML, PDF, XML, CSV, TIFF, Word, and Excel.</span></span>  
  
-   <span data-ttu-id="e06eb-142">**サブスクリプションを設定します。**</span><span class="sxs-lookup"><span data-stu-id="e06eb-142">**Set up subscriptions.**</span></span> <span data-ttu-id="e06eb-143">レポート サーバーまたは SharePoint 統合モードのレポート サーバーにレポートをパブリッシュした後、特定の時刻にレポートを実行したり、レポート履歴の作成や、電子メール サブスクリプションの設定を行うなど、レポートに対するさまざまな構成を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="e06eb-143">After you publish the report to the report server or a report server in SharePoint integrated mode, you can configure your report to run at a specific time, create a report history, and set up e-mail subscriptions.</span></span>  
  
-   <span data-ttu-id="e06eb-144">Reporting Services の Atom 表示拡張機能を使用して、レポートから**データ フィードを生成** します。</span><span class="sxs-lookup"><span data-stu-id="e06eb-144">**Generate data feeds** from your report by using the Reporting Services Atom rendering extension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e06eb-145">パブリッシュされたレポートは、レポート サーバー上または SharePoint 統合モードのレポート サーバー上で、レポート サーバー管理者が管理します。</span><span class="sxs-lookup"><span data-stu-id="e06eb-145">Published reports are managed on a report server or a report server in SharePoint integrated mode by a report server administrator.</span></span> <span data-ttu-id="e06eb-146">レポート サーバー管理者は、セキュリティの定義、プロパティの設定、および操作 (レポート履歴や電子メールによるレポート配信など) のスケジュール設定を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="e06eb-146">Report server administrators can define security, set properties, and schedule operations such as report history and e-mail report delivery.</span></span> <span data-ttu-id="e06eb-147">共有スケジュールおよび共有データ ソースを作成し、それらを一般的な用途で使用できます。</span><span class="sxs-lookup"><span data-stu-id="e06eb-147">They can create shared schedules and shared data sources and make them available for general use.</span></span> <span data-ttu-id="e06eb-148">管理者はさらに、レポート サーバーのすべてのフォルダーの管理も行います。</span><span class="sxs-lookup"><span data-stu-id="e06eb-148">Administrators also manage all of the report server folders.</span></span> <span data-ttu-id="e06eb-149">実行できる管理タスクは、ユーザー権限により異なります。</span><span class="sxs-lookup"><span data-stu-id="e06eb-149">The ability to perform management tasks depends on user permissions.</span></span>  
  

  
##  <a name="in-this-section"></a><a name="InThisSection"></a> <span data-ttu-id="e06eb-150">トピックの内容</span><span class="sxs-lookup"><span data-stu-id="e06eb-150">In This Section</span></span>  
 [<span data-ttu-id="e06eb-151">SQL Server 2014 レポート ビルダーの新機能</span><span class="sxs-lookup"><span data-stu-id="e06eb-151">What's New in Report Builder for SQL Server 2014</span></span>](../what-s-new-in-report-builder-for-sql-server-2014.md)  
 <span data-ttu-id="e06eb-152">このバージョンのレポートビルダーの新機能 (マップなど) について説明します。</span><span class="sxs-lookup"><span data-stu-id="e06eb-152">Describes the new features in this version of Report Builder, including maps.</span></span>  
  
 [<span data-ttu-id="e06eb-153">チュートリアル: オフラインでのクイック グラフ レポートの作成</span><span class="sxs-lookup"><span data-stu-id="e06eb-153">Tutorial: Creating a Quick Chart Report Offline</span></span>](tutorial-create-a-quick-chart-report-offline-report-builder.md)  
 <span data-ttu-id="e06eb-154">レポート ビルダーとレポートの作成に使用できるウィザードを紹介します。</span><span class="sxs-lookup"><span data-stu-id="e06eb-154">Introduces Report Builder and the wizards available to help you create reports.</span></span> <span data-ttu-id="e06eb-155">このチュートリアルには、作業用の一連のデータが用意されているため、データ ソースに接続せずに実習を開始できます。</span><span class="sxs-lookup"><span data-stu-id="e06eb-155">The tutorial provides a set of data for you to work with so you do not need to connect to a data source to get started.</span></span>  
  
 [<span data-ttu-id="e06eb-156">レポートの計画 (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="e06eb-156">Planning a Report &#40;Report Builder&#41;</span></span>](../report-design/planning-a-report-report-builder.md)  
 <span data-ttu-id="e06eb-157">レポートを作成する前の考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="e06eb-157">Provides information on what you should consider before you start to build your report.</span></span>  
  
 [<span data-ttu-id="e06eb-158">レポート作成の概念 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="e06eb-158">Report Authoring Concepts &#40;Report Builder and SSRS&#41;</span></span>](../report-design/report-authoring-concepts-report-builder-and-ssrs.md)  
 <span data-ttu-id="e06eb-159">レポート ビルダーのドキュメント全体で使用する主要な概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="e06eb-159">Defines key concepts used in throughout Report Builder documentation.</span></span>  
  
 [<span data-ttu-id="e06eb-160">レポート デザイン ビュー &#40;レポート ビルダー&#41;</span><span class="sxs-lookup"><span data-stu-id="e06eb-160">Report Design View &#40;Report Builder&#41;</span></span>](report-design-view-report-builder.md)  
 <span data-ttu-id="e06eb-161">レポート デザイン ビューの各ペインと領域について説明します。</span><span class="sxs-lookup"><span data-stu-id="e06eb-161">Explains the different panes and regions of report design view.</span></span>  
  
 [<span data-ttu-id="e06eb-162">共有データセット デザイン ビュー (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="e06eb-162">Shared Dataset Design View &#40;Report Builder&#41;</span></span>](shared-dataset-design-view-report-builder.md)  
 <span data-ttu-id="e06eb-163">共有データセット デザイン ビューの各ペインと領域について説明します。</span><span class="sxs-lookup"><span data-stu-id="e06eb-163">Explains the different panes and regions of shared dataset design view.</span></span>  
  
 [<span data-ttu-id="e06eb-164">キーボード ショートカット (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="e06eb-164">Keyboard Shortcuts &#40;Report Builder&#41;</span></span>](keyboard-shortcuts-report-builder.md)  
 <span data-ttu-id="e06eb-165">レポート ビルダーでレポートのナビゲーションとデザインに使用できるショートカット キーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e06eb-165">Outlines the shortcut keys available for navigating and designing reports in Report Builder.</span></span>  
  
 [<span data-ttu-id="e06eb-166">&#40;レポートビルダーを開始レポートビルダー&#41;</span><span class="sxs-lookup"><span data-stu-id="e06eb-166">Start Report Builder &#40;Report Builder&#41;</span></span>](start-report-builder.md)  
 <span data-ttu-id="e06eb-167">レポート ビルダーの 2 つの異なるバージョン (スタンドアロンと [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)]) を起動する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e06eb-167">Explains how to start the two different versions of Report Builder: stand-alone and [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)].</span></span>  
  
  
