---
title: ブラウザーを使用したレポートの検索と表示 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: edf4843a-2a0a-486f-be25-14a3c1c6bc72
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5b864188fc5152a11ad66ac9cd986891b88849a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739445"
---
# <a name="finding-and-viewing-reports-with-a-browser-report-builder-and-ssrs"></a><span data-ttu-id="7ea59-102">ブラウザーを使用したレポートの検索と表示 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="7ea59-102">Finding and Viewing Reports with a Browser (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7ea59-103">Web ブラウザーが対応していれば、レポート サーバーに直接接続してレポートを表示できます。</span><span class="sxs-lookup"><span data-stu-id="7ea59-103">You can use any supported Web browser to view a report through a direct connection to a report server.</span></span> <span data-ttu-id="7ea59-104">レポートにはそれぞれ、レポート サーバー上の URL アドレスが割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="7ea59-104">Every report has a URL address on a report server.</span></span> <span data-ttu-id="7ea59-105">レポートの Web アドレスを入力すると、レポートを Web アプリケーションとは無関係にブラウザー ウィンドウで開くことができます。</span><span class="sxs-lookup"><span data-stu-id="7ea59-105">You can enter the Web address of a report to open it in a browser window independently of a Web application.</span></span> <span data-ttu-id="7ea59-106">レポートは HTML 形式で表示され、レポート内でページ間の移動やデータ値の検索を行うことができるようにレポート ツール バーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7ea59-106">The report opens in HTML format and includes the report toolbar so that you can navigate pages or search on data values within the report.</span></span> <span data-ttu-id="7ea59-107">URL でパラメーターを設定すると、ツール バーを非表示にしたりレポートの出力形式を選択したりできます。</span><span class="sxs-lookup"><span data-stu-id="7ea59-107">You can set parameters on the URL to hide the toolbar or select the output format of the report.</span></span>  
  
 <span data-ttu-id="7ea59-108">Web アドレスを使用してレポートを開くのは、レポートの表示には適していますが、レポートの管理には適していません。</span><span class="sxs-lookup"><span data-stu-id="7ea59-108">Opening a report through its Web address is suitable for viewing a report, but not managing a report.</span></span> <span data-ttu-id="7ea59-109">アイテムのプロパティ ページやサブスクリプション定義ページにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="7ea59-109">You cannot access an item's property pages or subscription definition pages.</span></span> <span data-ttu-id="7ea59-110">このような作業には、レポート マネージャーまたは SharePoint サイトを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ea59-110">You must use Report Manager or a SharePoint site for those tasks.</span></span>  
  
 <span data-ttu-id="7ea59-111">レポートの Web アドレスがわからない場合は、レポート サーバーの Web アドレスを開いてから、レポート サーバーのフォルダー階層を参照して、表示するレポートを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="7ea59-111">If you do not know the Web address of a report, you can open the Web address of the report server and then browse the report server folder hierarchy to select the report you want to view.</span></span> <span data-ttu-id="7ea59-112">次の図は、ブラウザー ウィンドウに表示されたフォルダー階層を表しています。</span><span class="sxs-lookup"><span data-stu-id="7ea59-112">The following diagram illustrates a folder hierarchy as it appears in a browser window.</span></span>  
  
 <span data-ttu-id="7ea59-113">![ブラウザーに表示されたフォルダー](../media/rs-browserfolder.GIF "ブラウザーに表示されたフォルダー")</span><span class="sxs-lookup"><span data-stu-id="7ea59-113">![Folders in a browser](../media/rs-browserfolder.GIF "Folders in a browser")</span></span>  
<span data-ttu-id="7ea59-114">ブラウザーに表示されたフォルダー</span><span class="sxs-lookup"><span data-stu-id="7ea59-114">Folders in a browser</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7ea59-115">ハンドヘルド デバイスからレポートにアクセスする場合は、ブラウザーを使用してレポートを開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ea59-115">If you are accessing a report from a handheld device, you must use a browser to open a report.</span></span> <span data-ttu-id="7ea59-116">レポート マネージャーは、ハンドヘルド デバイスには対応していません。</span><span class="sxs-lookup"><span data-stu-id="7ea59-116">Report Manager is not scaled for handheld devices.</span></span>  
  
 <span data-ttu-id="7ea59-117">使用できるブラウザーの種類の詳細については、 [Reporting Services のドキュメント](https://go.microsoft.com/fwlink/?linkid=121312) (SQL Server オンライン ブック) の「Reporting Services でサポートされるブラウザーの種類」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ea59-117">For more information about types of browsers that you can use, see "Browser Types Supported by Reporting Services" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="navigating-report-server-folders-in-a-web-browser"></a><span data-ttu-id="7ea59-118">Web ブラウザーでのレポート サーバー フォルダー間の移動</span><span class="sxs-lookup"><span data-stu-id="7ea59-118">Navigating Report Server Folders in a Web Browser</span></span>  
 <span data-ttu-id="7ea59-119">Web ブラウザーを使用して、レポート サーバー フォルダー間を移動したり、レポートを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="7ea59-119">You can use a Web browser to navigate report server folders and run reports.</span></span> <span data-ttu-id="7ea59-120">レポートおよびアイテムは、フォルダー階層のリンクとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ea59-120">Reports and items are displayed as links in the folder hierarchy.</span></span> <span data-ttu-id="7ea59-121">リンクをクリックすることで、レポート、リソース、またはフォルダーを開いたり、共有データ ソースの内容を参照することができます。</span><span class="sxs-lookup"><span data-stu-id="7ea59-121">You can click links to open a report, resource, or folder, or view the contents of a shared data source.</span></span> <span data-ttu-id="7ea59-122">フォルダー階層を利用した移動は、レポートの URL が不明な場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="7ea59-122">Navigating the folder hierarchy is useful if you do not know the URL of a report.</span></span> <span data-ttu-id="7ea59-123">レポート サーバーの Web アドレスを指定して、フォルダー階層のルート ノードでブラウザー接続を開き、フォルダー リンクをクリックしてフォルダー階層内を移動できます。</span><span class="sxs-lookup"><span data-stu-id="7ea59-123">You can specify the report server Web address to open a browser connection at the root node of the folder hierarchy, and then click folder links to navigate through the hierarchy.</span></span>  
  
 <span data-ttu-id="7ea59-124">レポート サーバーの仮想ディレクトリにアクセスした場合、表示されるのは、フォルダー、レポート、およびこれまでにアクセスしたことのあるアップロードされたアイテムのみです。</span><span class="sxs-lookup"><span data-stu-id="7ea59-124">When you access a report server virtual directory, you see only the folders, reports, and uploaded items to which you have access.</span></span> <span data-ttu-id="7ea59-125">ユーザー インターフェイスには、フォルダー階層と、作成日時や更新日時、ファイル サイズ、および以下のような各アイテムの種類などの基本情報のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ea59-125">The user interface shows only the folder hierarchy and basic information, such as creation or modification date, file size, and item type for individual items:</span></span>  
  
-   <span data-ttu-id="7ea59-126">他の識別情報が何も付加されていないリンクは、レポートまたはモデルを表します。</span><span class="sxs-lookup"><span data-stu-id="7ea59-126">A link with no other indicator is a report or a model.</span></span>  
  
-   <span data-ttu-id="7ea59-127">タグは、 \<ds> 共有データソースを示します。</span><span class="sxs-lookup"><span data-stu-id="7ea59-127">The tag \<ds> indicates a shared data source.</span></span>  
  
-   <span data-ttu-id="7ea59-128">タグは、 \<dir> フォルダーアイテムを示します。</span><span class="sxs-lookup"><span data-stu-id="7ea59-128">The tag \<dir> indicates a folder item.</span></span>  
  
-   <span data-ttu-id="7ea59-129">ファイル名拡張子は、リソースを表します。</span><span class="sxs-lookup"><span data-stu-id="7ea59-129">A file name extension indicates a resource.</span></span> <span data-ttu-id="7ea59-130">ファイル名拡張子によって、リソースの MIME の種類が識別されます。</span><span class="sxs-lookup"><span data-stu-id="7ea59-130">The file name extension identifies the MIME type of the resource.</span></span> <span data-ttu-id="7ea59-131">たとえば、.jpg は JPEG 形式の画像であることを表します。</span><span class="sxs-lookup"><span data-stu-id="7ea59-131">For example, .jpg indicates an image in JPEG format.</span></span>  
  
## <a name="typing-the-url-address-of-a-report"></a><span data-ttu-id="7ea59-132">レポートの URL アドレスの入力</span><span class="sxs-lookup"><span data-stu-id="7ea59-132">Typing the URL Address of a Report</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="7ea59-133">では、レポート サーバー上の特定のアイテムへの URL アクセスをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="7ea59-133">supports URL access to specific items on a report server.</span></span> <span data-ttu-id="7ea59-134">URL には、レポートの絶対パスと、レポートを表示するためのコマンドを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ea59-134">The URL must include a fully qualified path to the report and commands to render the report.</span></span> <span data-ttu-id="7ea59-135">レポートにパラメーターが含まれている場合は、レポートを開くのに必要なすべての値も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ea59-135">If the report includes parameters, you must also specify any values that are required to open the report.</span></span> <span data-ttu-id="7ea59-136">パスに含まれるスペース、パラメーター値、または表示拡張機能が含まれているレポートの URL を入力する場合、予想どおりの結果を得るには、URL エンコードされた文字を URL に組み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ea59-136">If you are typing a URL for a report that includes spaces in the path, parameter values, or a rendering extension, you must incorporate URL encoded characters into the URL to get the results you expect.</span></span> <span data-ttu-id="7ea59-137">パス名に含まれるスペース、パラメーター、および表示拡張機能のエンコードを含むレポートの URL の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7ea59-137">The following example illustrates a report URL that includes encoding for spaces in the path name, parameters, and a rendering extension:</span></span>  
  
 `http://<Webservername>/reportserver?/<reportfolder>/employee+sales+summary&ReportYear=2004&ReportMonth=06&EmpID=24&rs:Command=Render&rs:Format=HTML4.0`  
  
 <span data-ttu-id="7ea59-138">Internet Explorer での URL の最大文字数は 2,083 文字です。</span><span class="sxs-lookup"><span data-stu-id="7ea59-138">The maximum limit for a URL in Internet Explorer is 2,083 characters.</span></span> <span data-ttu-id="7ea59-139">詳細については、「 [[IE] URL に使用可能な文字数は最大 2,083 文字](https://support.microsoft.com/kb/208427)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ea59-139">For more information, see [Maximum URL length in Internet Explorer](https://support.microsoft.com/kb/208427).</span></span>  
  
 <span data-ttu-id="7ea59-140">URL の構築方法など、URL を介してレポートにアクセスする方法の詳細については、 [Reporting Services のドキュメント](https://go.microsoft.com/fwlink/?linkid=121312) (SQL Server オンライン ブック) の「URL アクセス」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ea59-140">For more information about how to access a report through a URL, including information on how a URL is constructed, see "URL Access" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ea59-141">参照</span><span class="sxs-lookup"><span data-stu-id="7ea59-141">See Also</span></span>  
 [<span data-ttu-id="7ea59-142">レポート マネージャーを使用したレポートの検索と表示 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7ea59-142">Finding and Viewing Reports in Report Manager &#40;Report Builder and SSRS&#41;</span></span>](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md)  
  
  
