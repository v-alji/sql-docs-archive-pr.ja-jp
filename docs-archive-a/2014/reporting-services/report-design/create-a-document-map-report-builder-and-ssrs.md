---
title: ドキュメント マップの作成 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c200a97b-67f2-499f-8374-3ed1ebe3f33c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a9dad0f8e6ee1d9b9ada44fda0eec5908f27cfcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634898"
---
# <a name="create-a-document-map-report-builder-and-ssrs"></a><span data-ttu-id="19e66-102">ドキュメント マップの作成 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="19e66-102">Create a Document Map (Report Builder and SSRS)</span></span>
  <span data-ttu-id="19e66-103">ドキュメント マップは、表示レポート内のレポート アイテムへのナビゲーション リンクのセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="19e66-103">A document map provides a set of navigational links to report items in a rendered report.</span></span> <span data-ttu-id="19e66-104">ドキュメント マップを含むレポートを表示すると、別のサイド ペインがレポートの横に表示されます。</span><span class="sxs-lookup"><span data-stu-id="19e66-104">When you view a report that includes a document map, a separate side pane appears next to the report.</span></span> <span data-ttu-id="19e66-105">ドキュメント マップ内のリンクをクリックすると、そのアイテムが表示されているレポート ページに移動できます。</span><span class="sxs-lookup"><span data-stu-id="19e66-105">A user can click links in the document map to jump to the report page that displays that item.</span></span> <span data-ttu-id="19e66-106">レポート セクションとグループは、リンクの階層として配置されます。</span><span class="sxs-lookup"><span data-stu-id="19e66-106">Report sections and groups are arranged in a hierarchy of links.</span></span> <span data-ttu-id="19e66-107">ドキュメント マップ内のアイテムをクリックすると、レポートが更新され、ドキュメント マップのアイテムに対応したレポートの領域が表示されます。</span><span class="sxs-lookup"><span data-stu-id="19e66-107">Clicking items in the document map refreshes the report and displays the area of the report that corresponds to the item in the document map.</span></span>  
  
 <span data-ttu-id="19e66-108">ドキュメント マップにリンクを追加するには、レポート アイテムの `DocumentMapLabel` プロパティを、作成したテキストに設定するか、またはドキュメント マップに表示するテキストになる式に設定します。</span><span class="sxs-lookup"><span data-stu-id="19e66-108">To add links to the document map, you set the `DocumentMapLabel` property of the report item to text that you create or to an expression that evaluates to the text that you want display in the document map.</span></span> <span data-ttu-id="19e66-109">テーブル グループやマトリックス グループの一意の値を、ドキュメント マップに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="19e66-109">You can also add the unique values for a table or matrix group to the document map.</span></span> <span data-ttu-id="19e66-110">たとえば、色別に分けられたグループの場合、それぞれの色は、その色のグループ インスタンスが表示されているレポート ページへのリンクとなります。</span><span class="sxs-lookup"><span data-stu-id="19e66-110">For example, for a group based on color, each unique color is a link to the report page that displays the group instance for that color.</span></span>  
  
 <span data-ttu-id="19e66-111">また、ドキュメント マップの表示にオーバーライドされるレポートの URL を作成することもできます。このようにすると、ドキュメント マップを表示せずにレポートを実行し、レポート ビューアーのツール バーの **[ドキュメント マップの表示/非表示]** ボタンをクリックして表示を切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="19e66-111">You can also create a URL to a report that overrides the display of the document map, so that you can run the report without displaying the document map, and then click the **Show/Hide Document Map** button on the report viewer toolbar to toggle the display.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="document-maps-and-rendering-extensions"></a><a name="DocMapRenderExtensions"></a> <span data-ttu-id="19e66-112">ドキュメント マップと表示拡張機能</span><span class="sxs-lookup"><span data-stu-id="19e66-112">Document Maps and Rendering Extensions</span></span>  
 <span data-ttu-id="19e66-113">ドキュメント マップは、HTML 表示拡張機能 (プレビュー、レポート ビューアーなど) で使用します。</span><span class="sxs-lookup"><span data-stu-id="19e66-113">The document map is intended for use in the HTML rendering extension-for example, in Preview and the Report Viewer.</span></span> <span data-ttu-id="19e66-114">他の表示拡張機能では、異なる手段でドキュメント マップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="19e66-114">Other rendering extensions have different ways of articulating a document map:</span></span>  
  
-   <span data-ttu-id="19e66-115">PDF では、ドキュメント マップは [しおり] ペインとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="19e66-115">PDF renders a document map as the Bookmarks pane.</span></span>  
  
-   <span data-ttu-id="19e66-116">Excel では、ドキュメント マップはリンクの階層を含む名前付きのワークシートとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="19e66-116">Excel renders a document map as a named worksheet that includes a hierarchy of links.</span></span> <span data-ttu-id="19e66-117">レポート セクションは、同じワークブック内の、ドキュメント マップと共に含まれる別のワークシートに表示されます。</span><span class="sxs-lookup"><span data-stu-id="19e66-117">Report sections are rendered in separate worksheets that are included with the document map in the same workbook.</span></span>  
  
-   <span data-ttu-id="19e66-118">Word では、ドキュメント マップは目次として使用されます。</span><span class="sxs-lookup"><span data-stu-id="19e66-118">Word includes a document map as the table of contents.</span></span>  
  
-   <span data-ttu-id="19e66-119">Atom、TIFF、XML、および CSV では、ドキュメント マップは無視されます。</span><span class="sxs-lookup"><span data-stu-id="19e66-119">Atom, TIFF, XML, and CSV ignore document maps.</span></span>  
  
 <span data-ttu-id="19e66-120">詳細については、「[さまざまなレポート表示拡張機能の対話機能 &#40;レポート ビルダーおよび SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19e66-120">For more information, see [Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md).</span></span>  
  
##  <a name="AddRptItemToMap"></a>   
#### <a name="to-add-a-report-item-to-a-document-map"></a><span data-ttu-id="19e66-121">ドキュメント マップにレポート アイテムを追加するには</span><span class="sxs-lookup"><span data-stu-id="19e66-121">To add a report item to a document map</span></span>  
  
1.  <span data-ttu-id="19e66-122">デザイン ビューで、テーブル、マトリックス、ゲージなど、ドキュメント マップに追加するレポート アイテムを選択します。</span><span class="sxs-lookup"><span data-stu-id="19e66-122">In Design view, select the report item such as a table, matrix, or gauge that you want to add to the document map.</span></span> <span data-ttu-id="19e66-123">プロパティ ペインにレポート アイテム プロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="19e66-123">The report item properties appear in the Properties pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="19e66-124">Tablix データ領域を選択するには、任意のセルをクリックして行ハンドルおよび列ハンドルを表示し、コーナー ハンドルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="19e66-124">To select a tablix data region, click in any cell to display the row and column handles, and then click the corner handle.</span></span>  
  
2.  <span data-ttu-id="19e66-125">プロパティペインで、ドキュメントマップに表示するテキストをプロパティに入力するか、結果が `DocumentMapLabel` ラベルになる式を入力します。</span><span class="sxs-lookup"><span data-stu-id="19e66-125">In the Properties pane, type the text that you want to appear in the document map in the `DocumentMapLabel` property, or enter an expression that evaluates to a label.</span></span> <span data-ttu-id="19e66-126">たとえば、「 **Sales Chart**」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="19e66-126">For example, type **Sales Chart**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="19e66-127">[プロパティ] ペインが表示されない場合は、 **[表示]** タブの **[表示/非表示]** グループで、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="19e66-127">If you do not see the Properties pane, on the **View** tab, in the **Show/Hide** group, select **Properties**.</span></span>  
  
3.  <span data-ttu-id="19e66-128">ドキュメント マップに表示するレポート アイテムごとに手順 1. と手順 2. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="19e66-128">Repeat steps 1 and 2 for every report item that you want to appear in the document map.</span></span>  
  
4.  <span data-ttu-id="19e66-129">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19e66-129">Click **Run**.</span></span> <span data-ttu-id="19e66-130">レポートが実行され、作成したラベルがドキュメント マップに表示されます。</span><span class="sxs-lookup"><span data-stu-id="19e66-130">The report runs and the document map displays the labels you created.</span></span> <span data-ttu-id="19e66-131">任意のリンクをクリックすると、このレポート アイテムが配置されたレポート ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="19e66-131">Click any link to jump to the report page with that item.</span></span>  
  
 
  
##  <a name="AddUniqueValuesToMap"></a>   
#### <a name="to-add-unique-group-values-to-a-document-map"></a><span data-ttu-id="19e66-132">ドキュメント マップに一意のグループ値を追加するには</span><span class="sxs-lookup"><span data-stu-id="19e66-132">To add unique group values to a document map</span></span>  
  
1.  <span data-ttu-id="19e66-133">デザイン ビューで、ドキュメント マップに表示するグループを格納するテーブル、マトリックス、または一覧を選択します。</span><span class="sxs-lookup"><span data-stu-id="19e66-133">In Design view, select the table, matrix, or list that contains the group that you want to display in the document map.</span></span> <span data-ttu-id="19e66-134">グループ化ペインに行グループと列グループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="19e66-134">The Grouping pane displays the row and column groups.</span></span>  
  
2.  <span data-ttu-id="19e66-135">行グループ ペインで、グループを右クリックし、 **[グループの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19e66-135">In the Row Groups pane, right-click the group, and then click **Edit Group**.</span></span> <span data-ttu-id="19e66-136">**[Tablix グループのプロパティ]** ダイアログ ボックスの **[全般]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="19e66-136">The **General** page of the **Tablix Group Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="19e66-137">**[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19e66-137">Click **Advanced**.</span></span>  
  
4.  <span data-ttu-id="19e66-138">**[ドキュメント マップ]** ボックスで、グループ式に一致する式を入力するか、選択します。</span><span class="sxs-lookup"><span data-stu-id="19e66-138">In the **Document map** list box, type or select an expression that matches the group expression.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="19e66-139">ドキュメント マップに表示するグループごとに手順 1. ～ 4. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="19e66-139">Repeat steps 1-4 for every group that you want to appear in the document map.</span></span>  
  
7.  <span data-ttu-id="19e66-140">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19e66-140">Click **Run**.</span></span> <span data-ttu-id="19e66-141">レポートが実行され、グループ値がドキュメント マップに表示されます。</span><span class="sxs-lookup"><span data-stu-id="19e66-141">The report runs and the document map displays the group values.</span></span> <span data-ttu-id="19e66-142">任意のリンクをクリックすると、このレポート アイテムが配置されたレポート ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="19e66-142">Click any link to jump to the report page with that item.</span></span>  
  
 
  
##  <a name="HideMapWhenViewRpt"></a>   
#### <a name="to-hide-the-document-map-when-you-view-a-report"></a><span data-ttu-id="19e66-143">レポートを表示する場合にドキュメント マップを非表示にするには</span><span class="sxs-lookup"><span data-stu-id="19e66-143">To hide the document map when you view a report</span></span>  
  
1.  <span data-ttu-id="19e66-144">レポート マネージャーで、ドキュメント マップのあるレポートを参照します。</span><span class="sxs-lookup"><span data-stu-id="19e66-144">In Report Manager, browse to the report that has the document map.</span></span>  
  
     <span data-ttu-id="19e66-145">たとえば、 [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] サンプル レポートの場合、次の URL は、"Product Catalog" というレポートを指定しています。</span><span class="sxs-lookup"><span data-stu-id="19e66-145">For example, for the [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] sample reports, the following URL specifies the report named Product Catalog.</span></span>  
  
    ```  
    http://localhost/Reports/Pages/Report.aspx?ItemPath=%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog  
    ```  
  
2.  <span data-ttu-id="19e66-146">サーバー上のレポート パスをコピーします。</span><span class="sxs-lookup"><span data-stu-id="19e66-146">Copy the report path on the server.</span></span> <span data-ttu-id="19e66-147">この例のレポート パスは `%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog`です。</span><span class="sxs-lookup"><span data-stu-id="19e66-147">In the example, the report path is `%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog`.</span></span>  
  
3.  <span data-ttu-id="19e66-148">次の 3 つのコンポーネントで新しい URL を作成します。</span><span class="sxs-lookup"><span data-stu-id="19e66-148">Create a new URL with the following three components:</span></span>  
  
    -   <span data-ttu-id="19e66-149">レポート サーバー上のレポート ビューアー : `http://localhost/ReportServer/Pages/ReportViewer.aspx?`</span><span class="sxs-lookup"><span data-stu-id="19e66-149">The report viewer on the report server: `http://localhost/ReportServer/Pages/ReportViewer.aspx?`</span></span>  
  
    -   <span data-ttu-id="19e66-150">手順 1. でコピーしたレポートの名前 : `%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog`</span><span class="sxs-lookup"><span data-stu-id="19e66-150">The name of the report you copied in step 1, for example: `%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog`</span></span>  
  
    -   <span data-ttu-id="19e66-151">ドキュメント マップの非表示を指定するデバイス情報パラメーター : `&rs%3aCommand=Render&rc%3aFormat=HTML4.0&rc%3aDocMap=False`</span><span class="sxs-lookup"><span data-stu-id="19e66-151">The device information parameters that specify hiding the document map: `&rs%3aCommand=Render&rc%3aFormat=HTML4.0&rc%3aDocMap=False`</span></span>  
  
     <span data-ttu-id="19e66-152">次の URL は、上から順に付加された以上 3 つのコンポーネントで構成されています。</span><span class="sxs-lookup"><span data-stu-id="19e66-152">The following URL consists of these three components appended in the order they are listed.</span></span>  
  
    ```  
    http://localhost/ReportServer/Pages/ReportViewer.aspx?  
    %2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog  
    &rs%3aCommand=Render&rc%3aFormat=HTML4.0&rc%3aDocMap=False  
    ```  
  
     <span data-ttu-id="19e66-153">この URL を使用するには、コピーし、すべての改行を削除します。</span><span class="sxs-lookup"><span data-stu-id="19e66-153">To use this URL, copy it and remove all line breaks.</span></span>  
  
4.  <span data-ttu-id="19e66-154">レポート マネージャーで URL を貼り付け、&lt;localizedText&gt;Enter&lt;/localizedText&gt; キーを押します。</span><span class="sxs-lookup"><span data-stu-id="19e66-154">Paste the URL in Report Manager, and then press ENTER.</span></span> <span data-ttu-id="19e66-155">レポートが実行され、ドキュメント マップが非表示になります。</span><span class="sxs-lookup"><span data-stu-id="19e66-155">The report runs, and the document map is hidden.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19e66-156">サンプル レポートをダウンロードする方法の詳細については、「 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][レポート ビルダーおよびレポート デザイナーのサンプル レポート](https://go.microsoft.com/fwlink/?LinkId=198283)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19e66-156">For more information about downloading sample reports, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
>   
>  <span data-ttu-id="19e66-157">詳細については、 [Reporting Services のドキュメント](https://go.microsoft.com/fwlink/?linkid=121312) (SQL Server オンライン ブック) の「URL アクセス」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19e66-157">For more information, see "URL Access" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="19e66-158">参照</span><span class="sxs-lookup"><span data-stu-id="19e66-158">See Also</span></span>  
 [<span data-ttu-id="19e66-159">レポート マネージャーを使用したレポートの検索と表示 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="19e66-159">Finding and Viewing Reports in Report Manager &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md)  
  
  
