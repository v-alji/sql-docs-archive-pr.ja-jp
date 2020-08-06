---
title: レポートのプレビュー
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: fb068937efff71667d7f73c8e7ecd4d9ebfa576b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633743"
---
# <a name="preview-reports-in-sql-server-reporting-services-ssrs"></a><span data-ttu-id="ad259-102">SQL Server Reporting Services (SSRS) でレポートをプレビューする</span><span class="sxs-lookup"><span data-stu-id="ad259-102">Preview Reports in SQL Server Reporting Services (SSRS)</span></span>

  <span data-ttu-id="ad259-103">レポートをデザインするときに、そのレポートを実稼働環境にパブリッシュする前に表示することができます。</span><span class="sxs-lookup"><span data-stu-id="ad259-103">When you design a report, you may want to view it before publishing it to a production environment.</span></span> <span data-ttu-id="ad259-104">これを行うには、レポート デザイナーでプレビュー モードに切り替えるか、レポート デザイナーのプレビュー ウィンドウを使用するか、テスト環境のレポート サーバーにレポートをパブリッシュします。</span><span class="sxs-lookup"><span data-stu-id="ad259-104">You can do this in several ways: by switching to Preview mode in Report Designer, by using the preview window in Report Designer, and by publishing the report to a report server in a test environment.</span></span>  
  
> [!NOTE]  
> <span data-ttu-id="ad259-105">レポートをプレビューすると、レポートのデータがローカル コンピューターのファイルにキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="ad259-105">When you preview a report, the data for the report is cached to a file on the local computer.</span></span> <span data-ttu-id="ad259-106">同じレポートを、同じクエリ、パラメーター、および資格情報を使用して再びプレビューすると、レポート デザイナーはクエリを再実行する代わりにキャッシュされたコピーを表示します。</span><span class="sxs-lookup"><span data-stu-id="ad259-106">When you preview the same report again using the same query, parameters, and credentials, Report Designer retrieves the cached copy rather than rerunning the query.</span></span> <span data-ttu-id="ad259-107">データファイルは、 *\<reportname>* レポート定義ファイルと同じディレクトリに .rdl. データとして保存されます。</span><span class="sxs-lookup"><span data-stu-id="ad259-107">The data file is saved as *\<reportname>*.rdl.data in the same directory as the report definition file.</span></span> <span data-ttu-id="ad259-108">レポート デザイナーを終了してもファイルは削除されません。</span><span class="sxs-lookup"><span data-stu-id="ad259-108">The file is not deleted when you close Report Designer.</span></span>  
  
## <a name="preview-mode"></a><span data-ttu-id="ad259-109">プレビュー モード</span><span class="sxs-lookup"><span data-stu-id="ad259-109">Preview Mode</span></span>

 <span data-ttu-id="ad259-110">[**プレビュー**] をクリックすると、レポートデザイナーでレポートをプレビューできます。</span><span class="sxs-lookup"><span data-stu-id="ad259-110">You can preview a report in Report Designer by clicking **Preview**.</span></span> <span data-ttu-id="ad259-111">この場合、レポート サーバーで提供されるものと同じレポート処理および表示機能を使用して、レポートがローカルで実行されます。</span><span class="sxs-lookup"><span data-stu-id="ad259-111">This runs the report locally, using the same report processing and rendering functionality that is provided with the report server.</span></span> <span data-ttu-id="ad259-112">表示されるレポートは対話型のイメージです。ユーザーは、パラメーターの選択、リンクのクリック、ドキュメント マップの表示、レポートの非表示部分の展開と折りたたみなどを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ad259-112">The report that is displayed is an interactive image; you can select parameters, click links, view the document map, and expand and collapse hidden areas of the report.</span></span> <span data-ttu-id="ad259-113">また、インストールされている任意の表示形式にレポートをエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="ad259-113">You can also export the report to any of the installed rendering formats.</span></span>  
  
## <a name="standalone-preview"></a><span data-ttu-id="ad259-114">スタンドアロン プレビュー</span><span class="sxs-lookup"><span data-stu-id="ad259-114">Standalone Preview</span></span>

 <span data-ttu-id="ad259-115">レポートをプレビューするもう 1 つの方法は、作成したカスタム アセンブリをデバッグする際などに、デバッグ構成でレポート プロジェクトを実行することです。</span><span class="sxs-lookup"><span data-stu-id="ad259-115">Another way to preview a report is to run the report project in a debug configuration, for example, to debug custom assemblies that you write.</span></span> <span data-ttu-id="ad259-116">プロジェクトの実行方法には、次の 3 とおりがあります。</span><span class="sxs-lookup"><span data-stu-id="ad259-116">There are three ways to run a project:</span></span>  
  
- <span data-ttu-id="ad259-117">[**デバッグ**] メニューの [**開始**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad259-117">By clicking **Start** on the **Debug** menu.</span></span>  
  
- <span data-ttu-id="ad259-118">[標準] ツールバーの [**開始**] ボタンをクリックし [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="ad259-118">By clicking the **Start** button on the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] standard toolbar.</span></span>  
  
- <span data-ttu-id="ad259-119">F5 キーを押す。</span><span class="sxs-lookup"><span data-stu-id="ad259-119">By pressing F5.</span></span>  
  
 <span data-ttu-id="ad259-120">レポートを作成しても配置しないプロジェクト構成を使用している場合は、現在の構成の `StartItem` プロパティで指定されたレポートが、別のプレビュー ウィンドウで開きます。</span><span class="sxs-lookup"><span data-stu-id="ad259-120">If you use a project configuration that builds the report but does not deploy it, the report that is specified in the `StartItem` property of the current configuration opens in a separate preview window.</span></span> <span data-ttu-id="ad259-121">プレビュー ウィンドウは、プレビュー モードと同じ方法でレポートを表示し、同じ機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="ad259-121">The preview window displays the report in the same way and has the same functionality as Preview mode.</span></span>  
  
> [!NOTE]  
> <span data-ttu-id="ad259-122">レポートをデバッグする前に、開始アイテムを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad259-122">Before debugging a report, you must set a start item.</span></span> <span data-ttu-id="ad259-123">開始項目を設定するには、ソリューションエクスプローラーでレポートプロジェクトを右クリックし、[**プロパティ**] をクリックし `StartItem` ます。次に、で、表示するレポートの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="ad259-123">To set a start item, in Solution Explorer, right-click the report project, click **Properties**, and then in `StartItem`, select the name of the report to display.</span></span>  
  
 <span data-ttu-id="ad259-124">プロジェクトの開始アイテムではない特定のレポートをプレビューする場合は、レポートを作成しても配置しない構成 (DebugLocal 構成など) を選択し、レポートを右クリックして、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad259-124">If you wish to preview a particular report that is not the start item for the project, select a configuration that builds the report but does not deploy it (for example, the DebugLocal configuration), right-click the report, and then click **Run**.</span></span> <span data-ttu-id="ad259-125">レポートを配置しない構成を選択する必要があります。そうしないと、レポートはローカルのプレビュー ウィンドウに表示されずに、レポート サーバーにパブリッシュされます。</span><span class="sxs-lookup"><span data-stu-id="ad259-125">You must choose a configuration that does not deploy the report; otherwise, the report will be published to the report server instead of displayed locally in a preview window.</span></span>  
  
## <a name="print-preview"></a><span data-ttu-id="ad259-126">印刷プレビュー</span><span class="sxs-lookup"><span data-stu-id="ad259-126">Print Preview</span></span>

 <span data-ttu-id="ad259-127">プレビュー モードまたはプレビュー ウィンドウに最初に表示されるレポートは、HTML 表示拡張機能によって生成されるレポートと似ています。</span><span class="sxs-lookup"><span data-stu-id="ad259-127">When you first view a report on in Preview mode or in the preview window, the view of the report resembles a report produced by the HTML rendering extension.</span></span> <span data-ttu-id="ad259-128">プレビューは HTML 形式ではありませんが、レポートのレイアウトおよび改ページは HTML 出力と似ています。</span><span class="sxs-lookup"><span data-stu-id="ad259-128">The preview is not HTML, but the layout and pagination of the report is similar to HTML output.</span></span>  
  
 <span data-ttu-id="ad259-129">印刷プレビュー モードに切り替えることによって、表示を変更し、印刷されるレポートを表示できます。</span><span class="sxs-lookup"><span data-stu-id="ad259-129">You can change the view to represent a printed report by switching to print preview mode.</span></span> <span data-ttu-id="ad259-130">プレビュー ツール バーの **[印刷プレビュー]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad259-130">Click the **Print Preview** button on the preview toolbar.</span></span> <span data-ttu-id="ad259-131">レポートは、実際のページに近い状態で表示されます。</span><span class="sxs-lookup"><span data-stu-id="ad259-131">The report will display as though it were on a physical page.</span></span> <span data-ttu-id="ad259-132">この表示は、画像表示拡張機能および PDF 表示拡張機能によって生成される出力と似ています。</span><span class="sxs-lookup"><span data-stu-id="ad259-132">This view resembles the output produced by the Image and PDF rendering extensions.</span></span> <span data-ttu-id="ad259-133">印刷プレビューは画像または PDF ファイルではありませんが、レポートのレイアウトおよびページ割り当ては、それらの形式での出力と似ています。</span><span class="sxs-lookup"><span data-stu-id="ad259-133">Print preview is not an image or PDF file, but the layout and pagination of the report is similar the output in those formats.</span></span>  
  
## <a name="publish-to-a-test-server"></a><span data-ttu-id="ad259-134">テスト サーバーにパブリッシュする</span><span class="sxs-lookup"><span data-stu-id="ad259-134">Publish to a Test Server</span></span>

 <span data-ttu-id="ad259-135">レポートのテストは、テスト サーバーにレポートをパブリッシュして行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="ad259-135">You can also test reports by publishing them to a test server.</span></span> <span data-ttu-id="ad259-136">テスト サーバーにレポートをパブリッシュする操作は、実稼働サーバーにレポートをパブリッシュする場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="ad259-136">Publishing a report to a test server is the same as publishing to a production server.</span></span> <span data-ttu-id="ad259-137">レポートのパブリッシュ方法の詳細については、「 [レポート サーバーへのレポートのパブリッシュ](publishing-reports-to-a-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad259-137">For information about publishing a report, see [Publishing Reports to a Report Server](publishing-reports-to-a-report-server.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ad259-138">次のステップ</span><span class="sxs-lookup"><span data-stu-id="ad259-138">Next steps</span></span>

 - [<span data-ttu-id="ad259-139">レポートの印刷 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ad259-139">Print Reports &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/print-reports-report-builder-and-ssrs.md)
 - [<span data-ttu-id="ad259-140">レポートの印刷 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ad259-140">Print a Report &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/print-a-report-report-builder-and-ssrs.md)
 - [<span data-ttu-id="ad259-141">レポートのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="ad259-141">Publish Reports</span></span>](../publish-reports.md)
 - [<span data-ttu-id="ad259-142">レポートでのカスタム アセンブリの使用</span><span class="sxs-lookup"><span data-stu-id="ad259-142">Using Custom Assemblies with Reports</span></span>](../custom-assemblies/using-custom-assemblies-with-reports.md)