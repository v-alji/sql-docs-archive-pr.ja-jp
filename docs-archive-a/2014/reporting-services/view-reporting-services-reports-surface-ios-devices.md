---
title: Microsoft Surface デバイスと Apple iOS デバイスで Reporting Services レポートを表示する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- iPad
- Safari
- SSRS
- Report Viewer [Reporting Services]
- iOS
ms.assetid: 2124bcf5-d60a-475f-a4ae-de6df44d2860
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: db52ed500559969ae52eb9477caa6b410889c1d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643167"
---
# <a name="view-reporting-services-reports-on-microsoft-surface-devices-and--apple-ios-devices"></a><span data-ttu-id="11bb0-102">Microsoft Surface デバイスと Apple iOS デバイスでの Reporting Services レポートの表示</span><span class="sxs-lookup"><span data-stu-id="11bb0-102">View Reporting Services Reports on Microsoft Surface Devices and  Apple iOS Devices</span></span>
  <span data-ttu-id="11bb0-103">このトピックでは、Microsoft Surface デバイス、Apple iOS 6 と Apple Safari を搭載したデバイス (iPad など) でサポートされる [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の機能とワークフローについて説明します。</span><span class="sxs-lookup"><span data-stu-id="11bb0-103">This article describes the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features and workflows supported for Microsoft Surface devices, and devices with Apple iOS 6 and Apple Safari such as the iPad.</span></span>

## <a name="view-and-interact-with-reports"></a><span data-ttu-id="11bb0-104">レポートの表示および操作</span><span class="sxs-lookup"><span data-stu-id="11bb0-104">View and Interact With Reports</span></span>
 <span data-ttu-id="11bb0-105">[!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)]以降の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] では、Microsoft Surface デバイス、Apple iOS 6 と Apple Safari ブラウザーを搭載したデバイス (iPad など) でのレポートの表示と基本的な対話操作がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="11bb0-105">Starting with [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] supports viewing and basic interactivity with reports on Microsoft Surface devices, and devices with Apple iOS 6 and Apple Safari browser such as the iPad.</span></span> <span data-ttu-id="11bb0-106">Microsoft Surface デバイスを使用してレポートをパブリッシュすることもできます。</span><span class="sxs-lookup"><span data-stu-id="11bb0-106">You can also publish reports using Microsoft Surface devices.</span></span>

 <span data-ttu-id="11bb0-107">![IPad デスクトップ](media/videothumbnail.jpg "IPad デスクトップ")IPad でレポートを表示する方法のデモをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="11bb0-107">![IPad Desktop](media/videothumbnail.jpg "IPad Desktop") Watch a demonstration of viewing reports on an iPad.</span></span>

 <span data-ttu-id="11bb0-108">Windows Phone 8 デバイスで [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポートを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="11bb0-108">You can also view [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports on a Windows Phone 8 device.</span></span>

 <span data-ttu-id="11bb0-109">ここで説明する機能を使用するには、次のいずれかをインストールします。</span><span class="sxs-lookup"><span data-stu-id="11bb0-109">To utilize the features described in this topic, install one of the following:</span></span>

-   <span data-ttu-id="11bb0-110">ネイティブ モードのレポート サーバーの場合は、 [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] 以降のバージョンをインストールします。</span><span class="sxs-lookup"><span data-stu-id="11bb0-110">For a native mode report server, install [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] or later.</span></span>

     [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)]<span data-ttu-id="11bb0-111">は、 [Microsoft ダウンロードセンター](https://www.microsoft.com/download/details.aspx?id=35575)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="11bb0-111">is available for download from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=35575).</span></span>

-   <span data-ttu-id="11bb0-112">SharePoint モードのレポート サーバーの場合は、SharePoint 製品用 [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] アドインの [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 以降をインストールします。</span><span class="sxs-lookup"><span data-stu-id="11bb0-112">For a SharePoint mode report server, install [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] or later of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in for SharePoint products.</span></span>

 <span data-ttu-id="11bb0-113">**iPad デバイスまたは Microsoft Surface デバイスでレポートを表示および操作するには**</span><span class="sxs-lookup"><span data-stu-id="11bb0-113">**To view and interact with a report on an iPad device or Microsoft Surface device**</span></span>

1.  <span data-ttu-id="11bb0-114">レポートが存在するレポート サーバーまたは SharePoint サイトに接続できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="11bb0-114">Make sure that you can connect to the report server or SharePoint site where the report resides.</span></span>

2.  <span data-ttu-id="11bb0-115">次のいずれかの手順に従って、レポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="11bb0-115">Open the report by doing one of the following.</span></span>

    -   <span data-ttu-id="11bb0-116">**電子メールからの起動:** サブスクリプションによって作成された電子メールから、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポートの URL をタップします。</span><span class="sxs-lookup"><span data-stu-id="11bb0-116">**Start from e-mail:** From an e-mail that is created by a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] subscription, tap the URL of the report.</span></span> <span data-ttu-id="11bb0-117">レポートがブラウザーで開かれます。</span><span class="sxs-lookup"><span data-stu-id="11bb0-117">The report will open in the browser.</span></span>

    -   <span data-ttu-id="11bb0-118">**レポートサーバーからの起動:** レポートサーバー上のディレクトリを参照し、レポート [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 名をタップしてレポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="11bb0-118">**Start from Report Server:** Browse the directory on the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server, and then tap the report name to open the report.</span></span>

    -   <span data-ttu-id="11bb0-119">**SharePoint ドキュメントライブラリからの起動:** レポートを含む SharePoint ドキュメントライブラリを参照し、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポート名をタップします。</span><span class="sxs-lookup"><span data-stu-id="11bb0-119">**Start from a SharePoint document library:** Browse to a SharePoint document library that contains [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports, and then tap the report name.</span></span> <span data-ttu-id="11bb0-120">レポートを表示および操作できます。</span><span class="sxs-lookup"><span data-stu-id="11bb0-120">You can view and interact with the report.</span></span>

        > [!IMPORTANT]
        >  <span data-ttu-id="11bb0-121">iPad の場合は、Safari の **[プライベート ブラウズ]** プロパティがオフになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="11bb0-121">For the iPad, ensure that the **Private Browsing** property for Safari is turned off.</span></span>

    -   <span data-ttu-id="11bb0-122">**SharePoint Web パーツ:** Web パーツが SharePoint ページに追加されている場合は、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のレポートを表示できます。</span><span class="sxs-lookup"><span data-stu-id="11bb0-122">**SharePoint web part:** If the web part has been added to a SharePoint page, you can view [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports.</span></span>

3.  <span data-ttu-id="11bb0-123">Microsoft Surface デバイスでは、レポート マネージャーを使用してレポートを開くこともできます。</span><span class="sxs-lookup"><span data-stu-id="11bb0-123">On your Microsoft Surface device, you can also open the report by using Report Manager.</span></span> <span data-ttu-id="11bb0-124">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポート マネージャーでディレクトリを参照し、レポート名をタップしてレポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="11bb0-124">Browse the directory in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Report Manager, and then tap the report name to open the report.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="11bb0-125">iPad では、レポート マネージャーでのレポートの表示はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="11bb0-125">Viewing reports in Report Manager is not supported on an iPad.</span></span>

4.  <span data-ttu-id="11bb0-126">次のように操作することによって、スクロールやズームを行います。</span><span class="sxs-lookup"><span data-stu-id="11bb0-126">Scroll and zoom by doing the following.</span></span>

    -   <span data-ttu-id="11bb0-127">レポートをスクロールするには、画面上で指をドラッグします (上、下、左、または右)。</span><span class="sxs-lookup"><span data-stu-id="11bb0-127">To scroll the report, drag your finger across the screen (up, down, left or right).</span></span> <span data-ttu-id="11bb0-128">これはスワイプ ジェスチャです。</span><span class="sxs-lookup"><span data-stu-id="11bb0-128">This is the swipe gesture.</span></span>

    -   <span data-ttu-id="11bb0-129">拡大するには、画面に指を 2 本当て、指と指の距離を広げます。</span><span class="sxs-lookup"><span data-stu-id="11bb0-129">To zoom in, place two fingers on the screen and separate the fingers.</span></span> <span data-ttu-id="11bb0-130">縮小するには、画面に指を 2 本当て、指と指の距離を狭めます。</span><span class="sxs-lookup"><span data-stu-id="11bb0-130">To zoom out, place two fingers on the screen and move the fingers together.</span></span> <span data-ttu-id="11bb0-131">これはピンチ ジェスチャです。</span><span class="sxs-lookup"><span data-stu-id="11bb0-131">This is the pinch gesture.</span></span>

5.  <span data-ttu-id="11bb0-132">次のように操作することによって、レポートでの移動と操作を行います。</span><span class="sxs-lookup"><span data-stu-id="11bb0-132">Navigate and interact with the report by doing the following.</span></span>

    -   <span data-ttu-id="11bb0-133">レポート アイテムや、グループに関連付けられている行と列を折りたたむにはプラス記号 (+) をタップし、展開するにはマイナス記号 (-) をタップします。</span><span class="sxs-lookup"><span data-stu-id="11bb0-133">Collapse and expand report items, and rows and columns that are associated with groups, by taping the plus (+) sign to collapse and the minus (-) sign to expand.</span></span>

    -   <span data-ttu-id="11bb0-134">テーブルの行またはマトリックスの行と列を昇順および降順で並べ替えるには、並べ替えボタンをタップします。</span><span class="sxs-lookup"><span data-stu-id="11bb0-134">Toggle between ascending and descending order for rows in a table or for rows and columns in a matrix, by tapping the sort button.</span></span> <span data-ttu-id="11bb0-135">並べ替えボタンは、通常、列ヘッダーにあります。</span><span class="sxs-lookup"><span data-stu-id="11bb0-135">The sort button is usually located in the column header.</span></span>

    -   <span data-ttu-id="11bb0-136">パラメーター ペインを展開したり折りたたんだりするには、レポートの上部にある矢印ボタンをタップします。</span><span class="sxs-lookup"><span data-stu-id="11bb0-136">Expand and collapse the parameter pane, by tapping the arrow button near the top of the report.</span></span>

    -   <span data-ttu-id="11bb0-137">パラメーター値を選択するには、パラメーターの横にあるボックスまたはコントロールをタップします。</span><span class="sxs-lookup"><span data-stu-id="11bb0-137">Select a parameter value by tapping the box or control next to the parameter.</span></span> <span data-ttu-id="11bb0-138">パラメーター値をレポートに適用するには、 **[レポートの表示]** をタップします。</span><span class="sxs-lookup"><span data-stu-id="11bb0-138">Tap **View Report** to apply the parameter value to the report.</span></span>

    -   <span data-ttu-id="11bb0-139">レポートの内容を検索するには、 **[検索]** の横にあるボックスをタップし、検索語句を入力して、 **[検索]** をタップします。</span><span class="sxs-lookup"><span data-stu-id="11bb0-139">Search the report content by taping the box next to **Find**, typing a search term, and then taping **Find**.</span></span>

    -   <span data-ttu-id="11bb0-140">レポートのページ間を移動するには、ナビゲーション ボタンをタップするか、ボタンの横にあるテキスト ボックスをタップしてページ番号を入力します。</span><span class="sxs-lookup"><span data-stu-id="11bb0-140">Navigate the report pages by tapping the navigation buttons, or tapping the text box next to the buttons and typing the page number.</span></span>

    -   <span data-ttu-id="11bb0-141">URL に移動するには、レポート アイテムに追加されたテキスト ボックス、画像、グラフ、ゲージなどのハイパーリンクをタップします。</span><span class="sxs-lookup"><span data-stu-id="11bb0-141">Navigate to URLs by taping hyperlinks that have been added to report items such as text boxes, images, charts, and gauges.</span></span>

    -   <span data-ttu-id="11bb0-142">レポートをエクスポートするには、 **[エクスポート]** メニューのアイコンをタップし、ファイル形式をタップします。</span><span class="sxs-lookup"><span data-stu-id="11bb0-142">Export the report by tapping the icon for the **Export drop down menu** and then tapping a file format.</span></span>

        -   <span data-ttu-id="11bb0-143">Microsoft Surface デバイスでレポートを表示している場合は、次のいずれかの形式にレポートをエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="11bb0-143">If you're viewing the report on a Microsoft Surface device, you can export the report to one of the following formats.</span></span>

            -   <span data-ttu-id="11bb0-144">レポート データが含まれている XML ファイル</span><span class="sxs-lookup"><span data-stu-id="11bb0-144">XML file with report data</span></span>

            -   <span data-ttu-id="11bb0-145">CSV (コンマ区切り)</span><span class="sxs-lookup"><span data-stu-id="11bb0-145">CSV (comma delimited)</span></span>

            -   <span data-ttu-id="11bb0-146">PDF</span><span class="sxs-lookup"><span data-stu-id="11bb0-146">PDF</span></span>

            -   <span data-ttu-id="11bb0-147">MHTML (Web アーカイブ)</span><span class="sxs-lookup"><span data-stu-id="11bb0-147">MHTML (web archive)</span></span>

            -   <span data-ttu-id="11bb0-148">Excel</span><span class="sxs-lookup"><span data-stu-id="11bb0-148">Excel</span></span>

            -   <span data-ttu-id="11bb0-149">TIFF</span><span class="sxs-lookup"><span data-stu-id="11bb0-149">TIFF</span></span>

            -   <span data-ttu-id="11bb0-150">Word</span><span class="sxs-lookup"><span data-stu-id="11bb0-150">Word</span></span>

        -   <span data-ttu-id="11bb0-151">IPad でレポートを表示している場合は、TIFF または PDF ファイルとしてレポートをエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="11bb0-151">If you're viewing the report on an iPad, you can export the report as a TIFF or PDF file.</span></span>

## <a name="authentication"></a><span data-ttu-id="11bb0-152">認証</span><span class="sxs-lookup"><span data-stu-id="11bb0-152">Authentication</span></span>
 <span data-ttu-id="11bb0-153">RSWindowsNTLM 認証および RSWindowsBasic 認証は、ネイティブ モードと iPad の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] で動作します。</span><span class="sxs-lookup"><span data-stu-id="11bb0-153">RSWindowsNTLM authentication and RSWindowsBasic authentication work with [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in native mode and the iPad.</span></span>

 <span data-ttu-id="11bb0-154">一般に、この種類の認証は転送資格認証に機密性を提供しないため、RSWindowsBasic は HTTPS 環境以外では使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="11bb0-154">In general, it is recommended that RSWindowsBasic is not used in non-https environments because this type of authentication provides no confidentiality for the transmitted credentials.</span></span>

 <span data-ttu-id="11bb0-155">RSWindowsNTLM 認証と RSWindowsBasic 認証の詳細については、「 [Authentication with the Report Server](security/authentication-with-the-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11bb0-155">For more information about RSWindowsNTLM and RSWindowsBasic authentication, see [Authentication with the Report Server](security/authentication-with-the-report-server.md).</span></span>

## <a name="uploading-reports"></a><span data-ttu-id="11bb0-156">レポートのアップロード</span><span class="sxs-lookup"><span data-stu-id="11bb0-156">Uploading Reports</span></span>
 <span data-ttu-id="11bb0-157">適切な権限がある場合は、次のどちらかの方法を使用して Microsoft Surface デバイスからレポートをパブリッシュできます。</span><span class="sxs-lookup"><span data-stu-id="11bb0-157">You can publish reports from a Microsoft Surface device using one of the following methods, if you have the appropriate permissions.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="11bb0-158">iPad ではこれらの方法はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="11bb0-158">These methods are not supported on the iPad.</span></span>

-   <span data-ttu-id="11bb0-159">ライブラリを開き、 **[ドキュメントのアップロード]** をタップして、SharePoint ドキュメント ライブラリにレポート定義ファイル (.rdl) をアップロードします。</span><span class="sxs-lookup"><span data-stu-id="11bb0-159">Upload a report definition file (.rdl) to a SharePoint document library by opening the library and tapping **Upload Document**.</span></span>

-   <span data-ttu-id="11bb0-160">レポート マネージャーを開き、 **[ファイルのアップロード]** をタップして、レポート サーバー データベースにレポート定義ファイルをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="11bb0-160">Upload a report definition file to the report server database by opening Report Manager and tapping **Upload File**.</span></span>

## <a name="additional-information"></a><span data-ttu-id="11bb0-161">追加情報</span><span class="sxs-lookup"><span data-stu-id="11bb0-161">Additional Information</span></span>
 <span data-ttu-id="11bb0-162">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] およびサポートされているブラウザーの詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11bb0-162">For more information on [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] and supported browsers, see:</span></span>

-   [<span data-ttu-id="11bb0-163">Reporting Services と Power View のブラウザーサポートの計画 &#40;Reporting Services 2014&#41;</span><span class="sxs-lookup"><span data-stu-id="11bb0-163">Planning for Reporting Services and Power View Browser Support &#40;Reporting Services 2014&#41;</span></span>](../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md)

 <span data-ttu-id="11bb0-164">Microsoft Business Intelligence およびモバイル デバイスの詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11bb0-164">For more information on Microsoft Business Intelligence and Mobile devices, see the following:</span></span>

-   <span data-ttu-id="11bb0-165">[モバイルデバイスと SharePoint 2013 の概要](https://technet.microsoft.com/library/fp161351\(v=office.15\).aspx)(をご説明 https://technet.microsoft.com/library/fp161351(v=office.15).aspx) します。</span><span class="sxs-lookup"><span data-stu-id="11bb0-165">[Overview of mobile devices and SharePoint 2013](https://technet.microsoft.com/library/fp161351\(v=office.15\).aspx) (https://technet.microsoft.com/library/fp161351(v=office.15).aspx).</span></span>

-   <span data-ttu-id="11bb0-166">[SharePoint 2013 でサポートされているモバイルデバイスブラウザー](https://technet.microsoft.com/library/fp161353\(v=office.15\).aspx) https://technet.microsoft.com/library/fp161353(v=office.15).aspx) ()</span><span class="sxs-lookup"><span data-stu-id="11bb0-166">[Supported mobile device browsers in SharePoint 2013](https://technet.microsoft.com/library/fp161353\(v=office.15\).aspx) (https://technet.microsoft.com/library/fp161353(v=office.15).aspx).</span></span>

-   <span data-ttu-id="11bb0-167">[Apple iPad デバイスでのレポートとスコアカードの表示 (SharePoint Server 2010)](https://technet.microsoft.com/library/hh697482.aspx) (を参照して https://technet.microsoft.com/library/hh697482.aspx) ください。</span><span class="sxs-lookup"><span data-stu-id="11bb0-167">[Viewing reports and scorecards on Apple iPad devices (SharePoint Server 2010)](https://technet.microsoft.com/library/hh697482.aspx) (https://technet.microsoft.com/library/hh697482.aspx).</span></span>

-   <span data-ttu-id="11bb0-168">[IPad での Reporting Services レポートの表示 (ビデオ)](https://technet.microsoft.com/sqlserver/jj873792.aspx) ( https://technet.microsoft.com/sqlserver/jj873792.aspx) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11bb0-168">[Viewing Reporting Services Reports on an iPad (video)](https://technet.microsoft.com/sqlserver/jj873792.aspx) (https://technet.microsoft.com/sqlserver/jj873792.aspx).</span></span>

-   [<span data-ttu-id="11bb0-169">Microsoft Surface RT デバイスでの Reporting Services レポートの表示 (ビデオ)</span><span class="sxs-lookup"><span data-stu-id="11bb0-169">Viewing Reporting Services Reports on a Microsoft Surface RT Device (video)</span></span>](https://technet.microsoft.com/sqlserver/dn146017)


