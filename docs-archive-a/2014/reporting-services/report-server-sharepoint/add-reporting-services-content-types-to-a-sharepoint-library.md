---
title: レポートビューアー Web パーツを Web ページに追加します (SharePoint 統合モードの Reporting Services)。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], viewing reports
- Web Parts [Reporting Services]
- SharePoint integration [Reporting Services], Web Parts
- Report Viewer Web Part [Reporting Services]
ms.assetid: cac75345-2380-467d-a394-0a2140908a5a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d9b933fad8bc566b3cb0ef04303a85c5f034e620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721104"
---
# <a name="add-the-report-viewer-web-part-to-a-web-page-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="27479-102">レポート ビューアー Web パーツを Web ページに追加する (Reporting Services の SharePoint 統合モード)</span><span class="sxs-lookup"><span data-stu-id="27479-102">Add the Report Viewer Web Part to a Web Page (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="27479-103">レポート ビューアー Web パーツを使用することで、SharePoint 統合モード用に構成されているレポート サーバーで実行されるレポートを表示できます。</span><span class="sxs-lookup"><span data-stu-id="27479-103">You can use the Report Viewer Web Part to view reports that run on report server that is configured to run in SharePoint integrated mode.</span></span> <span data-ttu-id="27479-104">この Web パーツでは、レポート ビルダーまたはレポート デザイナーで作成してライブラリにアップロードしたレポート定義ファイル (.rdl) を表示できます。</span><span class="sxs-lookup"><span data-stu-id="27479-104">You can use the Web Part to display report definition (.rdl) files that you created in Report Builder or Report Designer and uploaded to a library.</span></span>  
  
 <span data-ttu-id="27479-105">Web ページにレポート ビューアー Web パーツを追加することで、Web ページにレポートを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="27479-105">You can add the Report Viewer Web Part to a Web page if you want to embed a report on that page.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27479-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインによってインストールされるレポート ビューアー Web パーツと、RSWebParts.cab ファイルに含まれているレポート ビューアー Web パーツは、名前は同じでも異なるものです。</span><span class="sxs-lookup"><span data-stu-id="27479-106">Although they have identical names, the Report Viewer Web Part that is installed through the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in is different from the Report Viewer Web Part that is included in the RSWebParts.cab file.</span></span> <span data-ttu-id="27479-107">このトピックでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインを使用してインストールされるレポート ビューアー Web パーツを利用するための手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="27479-107">The instructions in this topic are specifically for the Report Viewer Web Part that is installed through the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in.</span></span>  
  
 <span data-ttu-id="27479-108">Web パーツを Web ページに追加するには、サイト レベルでの "ページの追加とカスタマイズ" 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="27479-108">To add a Web Part to a Web page, you must have the Add and Customize Pages permission at the site level.</span></span> <span data-ttu-id="27479-109">既定のセキュリティ設定を使用する場合、この権限はフル コントロール レベルの権限を持つ **所有者** グループのメンバーに与えられます。</span><span class="sxs-lookup"><span data-stu-id="27479-109">If you are using default security settings, this permission is granted to members of the **Owners** group who have the Full Control level of permission.</span></span>  
  
### <a name="to-embed-a-report-in-a-web-page"></a><span data-ttu-id="27479-110">Web ページにレポートを埋め込むには</span><span class="sxs-lookup"><span data-stu-id="27479-110">To embed a report in a Web page</span></span>  
  
1.  <span data-ttu-id="27479-111">Web パーツ ページまたはダッシュボードを開くか、作成します。</span><span class="sxs-lookup"><span data-stu-id="27479-111">Open or create the Web Part page or dashboard.</span></span>  
  
2.  <span data-ttu-id="27479-112">**[サイトの操作]** の **[ページの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="27479-112">On **Site Actions**, click **Edit Page**.</span></span>  
  
3.  <span data-ttu-id="27479-113">[ **Web パーツの追加] を**クリックします。</span><span class="sxs-lookup"><span data-stu-id="27479-113">Click **Add a Web Part**.</span></span>  
  
4.  <span data-ttu-id="27479-114">Web パーツ カテゴリの一覧で、 **[その他]** カテゴリをクリックし、 **[SQL Server Reporting Services レポート ビューアー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="27479-114">In the list of web part categories, select the **Miscellaneous** category, and then select **SQL Server Reporting Services Report Viewer**.</span></span>  
  
5.  <span data-ttu-id="27479-115">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="27479-115">Click **Add**.</span></span> <span data-ttu-id="27479-116">Web パーツが、ゾーンの一番上に追加されます。</span><span class="sxs-lookup"><span data-stu-id="27479-116">The Web Part is added at the top of the zone.</span></span> <span data-ttu-id="27479-117">Web パーツは、ドラッグして、領域内の別の場所に移動できます。</span><span class="sxs-lookup"><span data-stu-id="27479-117">You can drag it to a different location in the zone.</span></span>  
  
6.  <span data-ttu-id="27479-118">ビューアー内で、 **[ツール ペインを開くにはここをクリックします]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="27479-118">Within the viewer, click **Click here to open the tool pane**.</span></span>  
  
7.  <span data-ttu-id="27479-119">参照ボタン (**[...]**) をクリックして、現在のサイト コレクションの任意のライブラリにあるレポートを選択します。</span><span class="sxs-lookup"><span data-stu-id="27479-119">Select a report from any library in the current site collection by clicking the browse (**...**) button.</span></span> <span data-ttu-id="27479-120">レポートの URL を入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="27479-120">You can also type the report URL.</span></span> <span data-ttu-id="27479-121">レポートの URL を調べるには、レポートを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="27479-121">To determine the URL for any report, right-click the report and select **Properties**.</span></span> <span data-ttu-id="27479-122">レポートの横にある下向きの矢印アイコンはクリックしないでください。アイテムの [プロパティの表示] ページでは、レポートの URL は表示されません。</span><span class="sxs-lookup"><span data-stu-id="27479-122">Do not click the down arrow next to the report; the report URL is not indicated in the View Properties page of the item.</span></span> <span data-ttu-id="27479-123">**[プロパティ]** ダイアログ ボックスで URL をコピーし、貼り付ける場合には、URL 内の "%20" をスペースに置き換えてください (たとえば、"Company%20Sales" は "Company Sales" にします)。</span><span class="sxs-lookup"><span data-stu-id="27479-123">If you copy and paste the URL from the **Properties** dialog box, replace the "%20" URL encoding with a space (for example, "Company%20Sales" should be "Company Sales").</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="27479-124">1 つのレポート ビューアー Web パーツには、1 つのレポートが格納されます。</span><span class="sxs-lookup"><span data-stu-id="27479-124">Each Report Viewer Web Part contains a single report.</span></span> <span data-ttu-id="27479-125">URL は、現在の SharePoint サイト、または同じ Web アプリケーションやファーム内のサイト上のレポートへの完全修飾パスで指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="27479-125">The URL must be the fully qualified path to a report that is on the current SharePoint site, or on a site within the same Web application or farm.</span></span> <span data-ttu-id="27479-126">この URL は、ドキュメント ライブラリとして解決されるか、ドキュメント ライブラリ内でレポートが格納されるフォルダーとして解決される必要があります。</span><span class="sxs-lookup"><span data-stu-id="27479-126">The URL must resolve to a document library or to a folder within a document library that contains the report.</span></span> <span data-ttu-id="27479-127">レポート URL には、ファイル拡張子 .rdl を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="27479-127">The report URL must include the .rdl file extension.</span></span> <span data-ttu-id="27479-128">レポートがモデル ファイルまたは共有データ ソース ファイルに依存している場合、URL でそのファイルを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="27479-128">If the report depends on a model or shared data source files, you do not need to specify those files in the URL.</span></span> <span data-ttu-id="27479-129">必要なファイルへの参照は、レポートに含まれています。</span><span class="sxs-lookup"><span data-stu-id="27479-129">The report contains references to the files it needs.</span></span>  
  
8.  <span data-ttu-id="27479-130">開いているツール ペインでプロパティを設定し、既定の外観とレイアウトを変更します。</span><span class="sxs-lookup"><span data-stu-id="27479-130">While the tool pane is open, you can set properties to modify the default appearance and layout.</span></span>  
  
9. <span data-ttu-id="27479-131">ツール ペインの下部で **[適用]** をクリックし、 **[OK]** をクリックしてペインを閉じます。</span><span class="sxs-lookup"><span data-stu-id="27479-131">Click **Apply** at the bottom of the tool pane, and then click **OK** to close the pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27479-132">参照</span><span class="sxs-lookup"><span data-stu-id="27479-132">See Also</span></span>  
 <span data-ttu-id="27479-133">[SharePoint サイトのレポートビューアー Web パーツ](../report-viewer-web-part-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="27479-133">[Report Viewer Web Part on a SharePoint Site](../report-viewer-web-part-on-a-sharepoint-site.md) </span></span>  
 <span data-ttu-id="27479-134">[レポートビューアー Web パーツのカスタマイズ](../customize-the-report-viewer-web-part.md) </span><span class="sxs-lookup"><span data-stu-id="27479-134">[Customize the Report Viewer Web Part](../customize-the-report-viewer-web-part.md) </span></span>  
 <span data-ttu-id="27479-135">[SharePoint サイト上のレポートサーバーアイテムに対する権限の許可](../security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="27479-135">[Granting Permissions on Report Server Items on a SharePoint Site](../security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md) </span></span>  
 [<span data-ttu-id="27479-136">Sharepoint &#40;sharepoint 2010 および SharePoint 2013 の Reporting Services アドインをインストールまたはアンインストール&#41;</span><span class="sxs-lookup"><span data-stu-id="27479-136">Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](../install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
