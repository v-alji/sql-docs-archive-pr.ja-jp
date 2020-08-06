---
title: SharePoint モードのレポートサーバー上のパブリッシュされたレポートアイテムの URL の例 (SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 54cb861a-8cec-445c-875d-599fb9bd1973
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1e444d10cd84b194518fdab9b904eec7a7849ecd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716005"
---
# <a name="url-examples-for-published-report-items-on-a-report-server-in-sharepoint-mode-ssrs"></a><span data-ttu-id="ee128-102">SharePoint モードのレポート サーバー上のパブリッシュされたレポート アイテムの URL の例 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="ee128-102">URL Examples for Published Report Items on a Report Server in SharePoint Mode (SSRS)</span></span>
  <span data-ttu-id="ee128-103">レポートおよび関連アイテムを SharePoint ライブラリにパブリッシュするには、レポート デザイナーなどの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 作成ツールを使用してコンテンツをパブリッシュするか、SharePoint サイトのアクションを使用してコンテンツをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="ee128-103">To publish reports and related items to a SharePoint library, you can either publish the content using the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] authoring tools such as Report Designer or you can upload the content by using SharePoint site actions.</span></span>  
  
 <span data-ttu-id="ee128-104">SharePoint サイトでは、ネイティブ モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーとは異なる Web アドレスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ee128-104">SharePoint sites use different Web addresses than a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server in native mode.</span></span> <span data-ttu-id="ee128-105">SharePoint サイトの Web 階層には、SharePoint Web アプリケーション、トップレベル サイト、オプションのサブサイト、およびライブラリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ee128-105">A SharePoint site Web hierarchy includes the SharePoint Web application, a top-level site, optional subsites, and libraries.</span></span> <span data-ttu-id="ee128-106">レポートまたは関連アイテムのパブリッシュ先となる、SharePoint サーバーおよび SharePoint サイト階層内の位置を指定する URL アドレスの作成方法を知っておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee128-106">You must know how to create a URL address that specifies the SharePoint server as well as the location in the SharePoint site hierarchy where you want to publish a report or related items.</span></span>  
  
 <span data-ttu-id="ee128-107">レポートに関連するアイテムには、共有データ ソース、サブレポート、詳細レポート、およびリソース (Web ベースのイメージ ファイルなど) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ee128-107">Items related to a report include shared data sources, subreports, drillthrough reports, and resources such as Web-based image files.</span></span> <span data-ttu-id="ee128-108">SharePoint ライブラリにパブリッシュされたレポートは、SharePoint ライブラリ内の場所でこれらの関連アイテムを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee128-108">A report that has been published to a SharePoint library must specify these related items by their location in the SharePoint library.</span></span>  
  
 <span data-ttu-id="ee128-109">このトピックの例は、レポート ソリューション内のレポートおよび関連アイテムの URL を作成するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ee128-109">Use the examples in this topic to help create URLs to reports and related items in your reporting solutions.</span></span>  
  
## <a name="site-hierarchy"></a><span data-ttu-id="ee128-110">サイト階層</span><span class="sxs-lookup"><span data-stu-id="ee128-110">Site Hierarchy</span></span>  
 <span data-ttu-id="ee128-111">レポート サーバーが SharePoint 統合モードで実行されるように構成する場合、レポート サーバーで処理および管理されるアイテムの場所の指定には、SharePoint の Web 階層を使用します。</span><span class="sxs-lookup"><span data-stu-id="ee128-111">When you configure a report server to run in SharePoint integrated mode, the SharePoint Web hierarchy is used to address items that are processed and managed on a report server.</span></span>  
  
 <span data-ttu-id="ee128-112">レポート サーバー コンテンツへのアクセスおよびセキュリティ保護には、次に示す Web 階層の要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="ee128-112">The following elements of the Web hierarchy can be used to access and secure report server content.</span></span> <span data-ttu-id="ee128-113">リストやページなどのオブジェクトは、レポート サーバーのコンテンツへのアクセスに使用されないため、この表では説明しません。</span><span class="sxs-lookup"><span data-stu-id="ee128-113">Other objects such as lists and pages are not used to access report server content and therefore are not described in the following table.</span></span>  
  
|<span data-ttu-id="ee128-114">Object</span><span class="sxs-lookup"><span data-stu-id="ee128-114">Object</span></span>|<span data-ttu-id="ee128-115">説明</span><span class="sxs-lookup"><span data-stu-id="ee128-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ee128-116">SharePoint Web アプリケーション</span><span class="sxs-lookup"><span data-stu-id="ee128-116">SharePoint Web application</span></span>|<span data-ttu-id="ee128-117">SharePoint Web アプリケーションは、スタンドアロン サーバーとしてインストールするか、一連の仮想サーバーを含むファームの下にインストールできます。</span><span class="sxs-lookup"><span data-stu-id="ee128-117">A SharePoint Web application can be installed as a stand-alone server or under a farm that contains a collection of virtual servers.</span></span> <span data-ttu-id="ee128-118">Web アプリケーションには http:*//servername*などの URL を指定します。複数のサイトを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="ee128-118">A Web application has a URL (for example, http:*//servername*) and can contain multiple sites.</span></span>|  
|<span data-ttu-id="ee128-119">サイト</span><span class="sxs-lookup"><span data-stu-id="ee128-119">Site</span></span>|<span data-ttu-id="ee128-120">サイトは、Web アプリケーションの親サイトまたはサブサイトになります。</span><span class="sxs-lookup"><span data-stu-id="ee128-120">A site is either a parent site for a Web application or a subsite.</span></span>|  
|<span data-ttu-id="ee128-121">SharePoint ライブラリ</span><span class="sxs-lookup"><span data-stu-id="ee128-121">SharePoint library</span></span>|<span data-ttu-id="ee128-122">ライブラリには、ドキュメントやフォルダーが格納されます。</span><span class="sxs-lookup"><span data-stu-id="ee128-122">A library contains documents or folders.</span></span> <span data-ttu-id="ee128-123">レポート、レポート モデル、共有データ ソース、および外部画像を保存できるサイト オブジェクトは、ライブラリまたはライブラリ内のフォルダーのみです。</span><span class="sxs-lookup"><span data-stu-id="ee128-123">A library or folder in a library is the only site object that can store reports, report models, shared data sources, and external images.</span></span>|  
|<span data-ttu-id="ee128-124">アイテム</span><span class="sxs-lookup"><span data-stu-id="ee128-124">Item</span></span>|<span data-ttu-id="ee128-125">URL 内で参照できるレポート サーバーのアイテムとしては、レポートまたはサブレポートのレポート定義、レポート モデル、共有データ ソース、外部画像などがあります。</span><span class="sxs-lookup"><span data-stu-id="ee128-125">Report server items that you can reference in a URL include a report definition for a report or subreport, a report model, a shared data source, or an external image.</span></span>|  
  
## <a name="url-syntax-and-rules"></a><span data-ttu-id="ee128-126">URL の構文と規則</span><span class="sxs-lookup"><span data-stu-id="ee128-126">URL Syntax and Rules</span></span>  
 <span data-ttu-id="ee128-127">ライブラリ内の各レポート サーバー アイテムを識別するには、完全修飾 URL を使用します。完全修飾 URL は、プロトコルを表すプレフィックス、サーバー名、サイト、ライブラリ、ファイル名、ファイルの種類を示すファイル名拡張子で構成されます。</span><span class="sxs-lookup"><span data-stu-id="ee128-127">Each report server item in a library is identified by a fully qualified URL that includes a protocol prefix, server name, site, library, file name, and file name extension for the file type.</span></span>  
  
### <a name="url-for-a-sharepoint-server"></a><span data-ttu-id="ee128-128">SharePoint サーバーの URL</span><span class="sxs-lookup"><span data-stu-id="ee128-128">URL for a SharePoint Server</span></span>  
 <span data-ttu-id="ee128-129">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] からレポート サーバーに、レポート サーバー プロジェクトまたはレポート モデル プロジェクトを配置する場合は、SharePoint サーバーの URL を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee128-129">You must use a URL to the SharePoint server when you deploy a Report Server or Report Model project from [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to the report server.</span></span>  
  
 <span data-ttu-id="ee128-130">使用するサーバーの名前を見つけるには、ブラウザーを開いて、レポートのパブリッシュ先として使用する SharePoint ライブラリを探します。</span><span class="sxs-lookup"><span data-stu-id="ee128-130">To find the name of the server to use, open a browser and locate the SharePoint library where you want to publish a report.</span></span> <span data-ttu-id="ee128-131">プロトコル プレフィックスのすぐ後に、http:*//servername*のような形式のサーバー名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee128-131">The server name appears immediately after the protocol prefix, for example, http:*//servername*.</span></span>  
  
 <span data-ttu-id="ee128-132">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL プロキシ エンドポイントの使用はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ee128-132">Using the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL proxy endpoint is not supported.</span></span> <span data-ttu-id="ee128-133">プロキシ エンドポイントには、http:*//servername:8080/reportserver*のようにポート番号が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ee128-133">A proxy endpoint includes a port number, for example, http:*//servername:8080/reportserver*.</span></span>  
  
### <a name="url-for-a-sharepoint-server-site-or-subsite"></a><span data-ttu-id="ee128-134">SharePoint Server サイトまたはサブサイトの URL</span><span class="sxs-lookup"><span data-stu-id="ee128-134">URL for a SharePoint Server Site or Subsite</span></span>  
 <span data-ttu-id="ee128-135">レポートまたはレポート データ ソースを配置する場合は、SharePoint サイトおよびサブサイト (ある場合) の URL を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee128-135">When you deploy a report or report data source, you must use a URL to a SharePoint site and subsite, if there is one.</span></span> <span data-ttu-id="ee128-136">URL ではサーバー名のすぐ後にサイト名が示されます。たとえば、http://*servername/site* または http://*servername/site/subsite*のようになります。</span><span class="sxs-lookup"><span data-stu-id="ee128-136">In the URL, the site name appears immediately after the server name., for example, http://*servername/site* or http://*servername/site/subsite*.</span></span>  
  
 <span data-ttu-id="ee128-137">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[offSPServ](../../includes/offspserv-md.md)] 2007 または [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Web アプリケーションでは、サイトおよびサブサイトは一般的にメイン サイトのタブに対応します。</span><span class="sxs-lookup"><span data-stu-id="ee128-137">On a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[offSPServ](../../includes/offspserv-md.md)] 2007 or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Web application, the site and subsite frequently correspond to the tabs on the main site.</span></span> <span data-ttu-id="ee128-138">サイト名またはサブサイト名を見つけるには、 **[ホーム]** をクリックし、次に **[すべてのサイト コンテンツの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee128-138">To find the site name or subsite name, click **Home**, and then **All Site Content**.</span></span> <span data-ttu-id="ee128-139">末尾までスクロールして **[サイトとワークスペース]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ee128-139">Scroll to the bottom and look for **Sites and Workspaces**.</span></span> <span data-ttu-id="ee128-140">このセクションにサイトの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee128-140">The list of sites appears in this section.</span></span>  
  
### <a name="url-for-a-sharepoint-library"></a><span data-ttu-id="ee128-141">SharePoint ライブラリの URL</span><span class="sxs-lookup"><span data-stu-id="ee128-141">URL for a SharePoint Library</span></span>  
 <span data-ttu-id="ee128-142">レポートまたは関連アイテムを SharePoint ライブラリに配置する場合は、SharePoint ライブラリの URL を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee128-142">When you deploy a report or related item to a SharePoint library, you must use a URL to the SharePoint library.</span></span> <span data-ttu-id="ee128-143">ライブラリに使用する URL は、使用している SharePoint のバージョンによって異なります。</span><span class="sxs-lookup"><span data-stu-id="ee128-143">The URL to use for a library differs depending on the version of SharePoint you are using.</span></span>  
  
 <span data-ttu-id="ee128-144">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 3.0 または [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]では、ライブラリはサーバー名の後に示されます。たとえば、http://*servername/* Shared Documents のようになります。</span><span class="sxs-lookup"><span data-stu-id="ee128-144">On [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 3.0 or [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], the library appears after the server name, for example, http://*servername/* Shared Documents.</span></span>  
  
 <span data-ttu-id="ee128-145">[!INCLUDE[offSPServ](../../includes/offspserv-md.md)] 2007 または [!INCLUDE[SPS2010](../../includes/sps2010-md.md)]では、ライブラリはサイトおよびサブサイトの後に示されます。</span><span class="sxs-lookup"><span data-stu-id="ee128-145">On [!INCLUDE[offSPServ](../../includes/offspserv-md.md)] 2007 or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)], the library appears after the site and subsite.</span></span> <span data-ttu-id="ee128-146">たとえば、http://*servername/site/* Documents のようになります。</span><span class="sxs-lookup"><span data-stu-id="ee128-146">For example, http://*servername/site/* Documents.</span></span>  
  
 <span data-ttu-id="ee128-147">新しい SharePoint ライブラリまたは使用したことがないサイトのパス情報を見つけるには、ブラウザーを開き、レポートのパブリッシュ先として使用する SharePoint ライブラリを探します。</span><span class="sxs-lookup"><span data-stu-id="ee128-147">To find the path information for a new SharePoint library or for an unfamiliar site, open a browser and locate the SharePoint library where you want to publish your reports.</span></span> <span data-ttu-id="ee128-148">ライブラリが空である場合は、任意のファイルをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="ee128-148">If the library is empty, upload any file.</span></span> <span data-ttu-id="ee128-149">ファイルを右クリックして **[プロパティ]** をクリックし、 **[プロパティ]** ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="ee128-149">Right-click the file and select **Properties** to open the **Properties** window.</span></span> <span data-ttu-id="ee128-150">ファイルのアドレスには、パブリッシュ操作に必要な URL 値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ee128-150">The address of the file contains the URL values that you need for a publish operation.</span></span>  
  
### <a name="fully-qualified-urls-for-items-on-a-sharepoint-site"></a><span data-ttu-id="ee128-151">SharePoint サイトのアイテムに使用する完全修飾 URL</span><span class="sxs-lookup"><span data-stu-id="ee128-151">Fully qualified URLs for Items on a SharePoint Site</span></span>  
 <span data-ttu-id="ee128-152">SharePoint ライブラリに保存されているアイテムの場所は、必ず完全修飾 URL で指定します。先頭にはルート ノードとして Web アプリケーションを指定し (http://*server*など)、参照するファイルの名前を最後に指定します。</span><span class="sxs-lookup"><span data-stu-id="ee128-152">Items that are stored in a SharePoint library are always addressed through a fully qualified URL that starts with the Web application (http://*server*) as the root node, and concludes with the name of the file that you are referencing.</span></span>  
  
 <span data-ttu-id="ee128-153">URL 内に指定するファイル名にはファイル名拡張子が必要です。</span><span class="sxs-lookup"><span data-stu-id="ee128-153">File names in the URL must include a file name extension.</span></span>  
  
 <span data-ttu-id="ee128-154">SharePoint サイトにパブリッシュするレポート内の依存アイテムには、相対 URL は使用できません。</span><span class="sxs-lookup"><span data-stu-id="ee128-154">You cannot use relative URLs for dependent items in reports that you publish to a SharePoint site.</span></span> <span data-ttu-id="ee128-155">たとえば相対 URL で共有データ ソース、レポート モデル、またはサブレポートを参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="ee128-155">For example, you cannot use a relative URL to reference a shared data source, report model, or subreport.</span></span> <span data-ttu-id="ee128-156">各アイテムには常に、SharePoint ライブラリへの完全修飾 URL を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee128-156">You must always specify the fully qualified URL to a SharePoint library for each item.</span></span> <span data-ttu-id="ee128-157">サイトには、URL 形式の解析に使用できるような事前定義された階層はないため、依存ファイルの場所を予測することはできません。</span><span class="sxs-lookup"><span data-stu-id="ee128-157">There is no way to predict where a dependent file might be located as there is no predefined hierarchy to the sites that you can use to parse a URL format.</span></span>  
  
 <span data-ttu-id="ee128-158">依存アイテムが含まれているレポートをパブリッシュまたはアップロードする場合は、レポートをパブリッシュした後で依存アイテムへの参照を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee128-158">When you publish or upload a report that contains dependent items, you must set the references to the dependent items after the report is published.</span></span> <span data-ttu-id="ee128-159">参照がレポート デザイナーのプレビュー モードで正しく機能しても、レポートをパブリッシュした後に正しく機能するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="ee128-159">References that worked correctly in Preview mode in Report Designer are not guaranteed to work after the report is published.</span></span> <span data-ttu-id="ee128-160">詳細については、このトピックの「 [作成ツールから SharePoint ライブラリへのパブリッシュ](#publishingToDocLib) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee128-160">For more information, see [Publishing from an Authoring Tool to a SharePoint Library](#publishingToDocLib) in this topic.</span></span>  
  
### <a name="urls-for-external-images"></a><span data-ttu-id="ee128-161">外部画像の URL</span><span class="sxs-lookup"><span data-stu-id="ee128-161">URLs for External Images</span></span>  
 <span data-ttu-id="ee128-162">レポート定義には、外部ファイルとして保存されている画像ファイルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ee128-162">A report definition can include an image file that is stored as an external file.</span></span> <span data-ttu-id="ee128-163">レポート定義内に画像ファイルの参照情報として、ファイルへの完全修飾 URL を設定します。</span><span class="sxs-lookup"><span data-stu-id="ee128-163">You can reference that file in the report definition by setting a fully qualified URL to the image file.</span></span> <span data-ttu-id="ee128-164">画像ファイルは、SharePoint サイトまたはリモート コンピューターに保存できます。</span><span class="sxs-lookup"><span data-stu-id="ee128-164">It can be stored on a SharePoint site or on a remote computer.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ee128-165">外部 URL が SharePoint サイト上の画像を指している場合、レポート ビルダーでレポートをプレビューすると壊れた画像アイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee128-165">If the external URL is for an image on a SharePoint site, the broken image icon will appear when you preview the report in Report Builder.</span></span> <span data-ttu-id="ee128-166">"`View Items`" 権限のみが与えられている場合に SharePoint サイトにレポートをアップロードし、接続モードでレポートを表示すると、壊れた画像アイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee128-166">When you upload the report to the SharePoint site, and render the report in connected mode, the broken image icon will appear if you have only `View Items` permissions.</span></span>  
  
 <span data-ttu-id="ee128-167">レポート内の外部画像ファイルへの参照は、レポート サーバーのモードに関係なく、完全修飾 URL にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee128-167">Regardless of the report server mode, references to an external image file in a report must be a fully qualified URL.</span></span> <span data-ttu-id="ee128-168">また、外部画像ファイルを参照する場合、通常は自動レポート処理アカウントを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee128-168">Also, referencing an external image file typically requires that you configure the unattended report processing account.</span></span>  
  
### <a name="specifying-subreports-and-drillthrough-reports"></a><span data-ttu-id="ee128-169">サブレポートと詳細レポートの指定</span><span class="sxs-lookup"><span data-stu-id="ee128-169">Specifying Subreports and Drillthrough Reports</span></span>  
 <span data-ttu-id="ee128-170">サブレポートは、メイン レポートと同じフォルダーに存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee128-170">Subreports must reside in the same folder as the main report.</span></span> <span data-ttu-id="ee128-171">相対フォルダーを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="ee128-171">You cannot specify a relative folder.</span></span>  
  
 <span data-ttu-id="ee128-172">詳細レポートを指定するには、式に URL を含めます。</span><span class="sxs-lookup"><span data-stu-id="ee128-172">To specify drillthrough reports, include the URL in an expression.</span></span> <span data-ttu-id="ee128-173">たとえば、SalesDetails という名前のレポートを詳細レポートとして指定するには、テキスト ボックスまたはプレースホルダー テキストのアクションで、ReportName を次の式に設定します。</span><span class="sxs-lookup"><span data-stu-id="ee128-173">For example, to specify the report that is named SalesDetails as a drillthrough report, in the Action for the text box or placeholder text, set ReportName to the following expression:</span></span>  
  
```  
="http://site/subsite/documentlibrary/SalesDetails.rdl"  
```  
  
### <a name="reserved-names-on-sharepoint-sites"></a><span data-ttu-id="ee128-174">SharePoint サイトの予約名</span><span class="sxs-lookup"><span data-stu-id="ee128-174">Reserved Names on SharePoint Sites</span></span>  
 <span data-ttu-id="ee128-175">SharePoint サイト上のアイテムの URL を作成する場合、 **Personal** および **Sites** という語はどちらも既定サイト内の予約名であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ee128-175">If you are creating or constructing a URL to an item that is located on a SharePoint site, know that the words **Personal** and **Sites** are both reserved names under the default site.</span></span>  
  
## <a name="examples-of-urls"></a><span data-ttu-id="ee128-176">URL の例</span><span class="sxs-lookup"><span data-stu-id="ee128-176">Examples of URLs</span></span>  
 <span data-ttu-id="ee128-177">アイテムを SharePoint ライブラリにパブリッシュする場合は、完全修飾 URL をターゲット ライブラリに指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee128-177">When publishing items to a SharePoint library, you must specify fully qualified URLs to the target library.</span></span> <span data-ttu-id="ee128-178">完全修飾 SharePoint URL は、SharePoint Web アプリケーション、サイト、ライブラリ、フォルダー、ファイル、およびファイル名拡張子で構成されます。フォルダーは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="ee128-178">A fully qualified SharePoint URL includes the SharePoint Web application, site, library, folder (optional), file, and file name extension.</span></span> <span data-ttu-id="ee128-179">使用可能な構文の例をいくつか次に示します。</span><span class="sxs-lookup"><span data-stu-id="ee128-179">The following examples provide several illustrations of the syntax you should use.</span></span>  
  
|<span data-ttu-id="ee128-180">移行先</span><span class="sxs-lookup"><span data-stu-id="ee128-180">Target</span></span>|<span data-ttu-id="ee128-181">Example URL (URL の例)</span><span class="sxs-lookup"><span data-stu-id="ee128-181">Example URL</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ee128-182">SharePoint サーバー</span><span class="sxs-lookup"><span data-stu-id="ee128-182">A SharePoint server.</span></span>|http://TestServer|  
|<span data-ttu-id="ee128-183">SharePoint サーバー サイトまたはサブサイト</span><span class="sxs-lookup"><span data-stu-id="ee128-183">A SharePoint server site or subsite.</span></span>|http://TestServer/toplevelsite/subsite|  
|<span data-ttu-id="ee128-184">**または** 配置上の [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] Shared Documents [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] 内の Company Sales サンプル レポート。</span><span class="sxs-lookup"><span data-stu-id="ee128-184">The Company Sales sample report in **Shared Documents** on a [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] or [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] deployment.</span></span>|http://TestServer/TestSite/Shared%20Documents/Company%20Sales.rdl|  
|<span data-ttu-id="ee128-185">**または** インスタンス上の [!INCLUDE[offSPServ](../../includes/offspserv-md.md)] Documents/Doc [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] フォルダー内の Company Sales サンプル レポート。</span><span class="sxs-lookup"><span data-stu-id="ee128-185">The Company Sales sample report in **Documents/Doc** folder on a [!INCLUDE[offSPServ](../../includes/offspserv-md.md)] or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] instance.</span></span>|http://TestServer/TestSite/Documents/Doc/Company%20Sales.rdl|  
|<span data-ttu-id="ee128-186">**または** インスタンス上の [!INCLUDE[offSPServ](../../includes/offspserv-md.md)] Report Center [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 内の Company Sales サンプル レポート。</span><span class="sxs-lookup"><span data-stu-id="ee128-186">The Company Sales sample report in **Report Center** on an [!INCLUDE[offSPServ](../../includes/offspserv-md.md)] or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] instance.</span></span>|http://TestServer/TestSite/Reports/Doc/Company%20Sales.rdl|  
  
##  <a name="publishing-from-an-authoring-tool-to-a-sharepoint-library"></a><a name="publishingToDocLib"></a> <span data-ttu-id="ee128-187">作成ツールから SharePoint ライブラリへのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="ee128-187">Publishing from an Authoring Tool to a SharePoint Library</span></span>  
 <span data-ttu-id="ee128-188">レポート作成ツールを使用してレポートと関連ファイルをライブラリにパブリッシュする場合、ファイルは検証されてから追加されます。</span><span class="sxs-lookup"><span data-stu-id="ee128-188">When you use a report authoring tool to publish reports and related files to a library, the files are validated before they are added.</span></span> <span data-ttu-id="ee128-189">SharePoint ライブラリで **[アップロード]** アクションを使用してレポートと関連ファイルをアップロードする場合、検証チェックは行われません。</span><span class="sxs-lookup"><span data-stu-id="ee128-189">If you upload reports and related files by using the **Upload** action on a SharePoint library, no validation check occurs.</span></span> <span data-ttu-id="ee128-190">ファイルが有効かどうかは、管理、編集、または実行のためにレポートにアクセスするまで知ることができません。</span><span class="sxs-lookup"><span data-stu-id="ee128-190">You will not know whether the file is valid until you access the report by managing, editing, or running it.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ee128-191">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]から SharePoint サイトにレポートをパブリッシュするとき、場合によっては、Internet Explorer ブラウザーの信頼できる場所のリストに SharePoint サイトを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee128-191">In order to publish reports to a SharePoint site from [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you might need to add the SharePoint site to your list of trusted locations in the Internet Explorer browser.</span></span>  
  
### <a name="shared-data-sources"></a><span data-ttu-id="ee128-192">共有データ ソース</span><span class="sxs-lookup"><span data-stu-id="ee128-192">Shared Data Sources</span></span>  
 <span data-ttu-id="ee128-193">共有データ ソースをレポート作成ツールからパブリッシュする場合は、プロジェクト プロパティ `TargetDataSourceFolder` を設定します。</span><span class="sxs-lookup"><span data-stu-id="ee128-193">When you publish a shared data source from a report authoring tool, you set the project property `TargetDataSourceFolder`.</span></span> <span data-ttu-id="ee128-194">ターゲット データ ソース フォルダーは、SharePoint ライブラリへの URL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee128-194">The target data source folder must be a URL to a SharePoint library.</span></span> <span data-ttu-id="ee128-195">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モードの場合と異なり、相対パスは有効ではなく、相対フォルダーは指定できません。</span><span class="sxs-lookup"><span data-stu-id="ee128-195">Unlike in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] native mode, you cannot specify a relative folder; relative paths are not valid.</span></span> <span data-ttu-id="ee128-196">ドキュメント ライブラリ パス内のフォルダーが存在しない場合は、フォルダーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ee128-196">If a folder in the Document Library path does not exist, one will be created.</span></span>  
  
 <span data-ttu-id="ee128-197">共有データ ソース (.rds) ファイルを SharePoint サイトにパブリッシュすると、データ ソース ファイル名拡張子が .rsds に変更されます。</span><span class="sxs-lookup"><span data-stu-id="ee128-197">When you publish a shared data source (.rds) file to a SharePoint site, this changes the data source file to an .rsds file name extension.</span></span> <span data-ttu-id="ee128-198">.rsds ファイルは SharePoint サイトからローカルに保存することも、既存の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] プロジェクトにインポートすることもできません。</span><span class="sxs-lookup"><span data-stu-id="ee128-198">The .rsds file cannot be saved locally from a SharePoint site and imported into an existing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] project.</span></span> <span data-ttu-id="ee128-199">ファイル名拡張子 .rds の共有データ ソースと .rsds の共有データ ソースを入れ替えることはできません。</span><span class="sxs-lookup"><span data-stu-id="ee128-199">Shared data sources with file name extensions .rds and .rsds are not interchangeable.</span></span>  
  
#### <a name="shared-data-sources-from-report-designer"></a><span data-ttu-id="ee128-200">共有データ ソース (レポート デザイナーから)</span><span class="sxs-lookup"><span data-stu-id="ee128-200">Shared Data Sources from Report Designer</span></span>  
 <span data-ttu-id="ee128-201">レポート デザイナー プロジェクトから共有データ ソースをパブリッシュする場合は、ターゲット ライブラリを指定する URL を使用するか、プロパティを空白のままにすることができます。</span><span class="sxs-lookup"><span data-stu-id="ee128-201">If you are publishing shared data sources from a Report Designer project, you can either use a URL that specifies the target library or you can leave the property blank.</span></span> <span data-ttu-id="ee128-202">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モードの場合と異なり、相対パスは有効ではなく、相対フォルダーは指定できません。</span><span class="sxs-lookup"><span data-stu-id="ee128-202">Unlike in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] native mode, you cannot specify a relative folder; relative paths are not valid.</span></span> <span data-ttu-id="ee128-203">ドキュメント ライブラリ パス内のフォルダーが存在しない場合は、フォルダーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ee128-203">If a folder in the Document Library path does not exist, one will be created.</span></span> <span data-ttu-id="ee128-204">ターゲット データ ソース フォルダーを空のままにした場合、データ ソースはターゲット レポート フォルダーにパブリッシュされます。</span><span class="sxs-lookup"><span data-stu-id="ee128-204">If you leave the target data source folder blank, the data source will be published in the target report folder.</span></span>  
  
### <a name="file-names"></a><span data-ttu-id="ee128-205">ファイル名</span><span class="sxs-lookup"><span data-stu-id="ee128-205">File Names</span></span>  
 <span data-ttu-id="ee128-206">レポート アイテムに対して URL 内に指定するファイル名にはファイル名拡張子が必要です。</span><span class="sxs-lookup"><span data-stu-id="ee128-206">File names in a URL for report items must include a file name extension.</span></span> <span data-ttu-id="ee128-207">ファイル名拡張子によってファイルの種類が識別されます。</span><span class="sxs-lookup"><span data-stu-id="ee128-207">The file name extension determines the file type.</span></span> <span data-ttu-id="ee128-208">レポート アイテムをレポート作成ツールからパブリッシュする場合は、ファイル名拡張子が自動的に含まれます。</span><span class="sxs-lookup"><span data-stu-id="ee128-208">When you publish report items from a report authoring tool, the file name extension is included automatically.</span></span> <span data-ttu-id="ee128-209">レポート アイテムを SharePoint ライブラリにアップロードする場合は、ファイル名拡張子を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee128-209">If you upload a report item to a SharePoint library, you must include a file name extension.</span></span>  
  
 <span data-ttu-id="ee128-210">SharePoint サイトにアップロードするアイテムにファイル名拡張子を指定しないと、`rsInvalidDataSourceReference` エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="ee128-210">If you do not specify a file name extension for items that you upload to a SharePoint site, the `rsInvalidDataSourceReference` error will occur.</span></span> <span data-ttu-id="ee128-211">SharePoint アプリケーションで有効なファイル名文字として認識されない文字を、ファイル名に含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="ee128-211">File names may not include characters that are not recognized as valid file name characters by SharePoint applications.</span></span> <span data-ttu-id="ee128-212">次の文字は含めないでください: #% & \*: \< > ?</span><span class="sxs-lookup"><span data-stu-id="ee128-212">Do not include the following characters: # % & \* : \< > ?</span></span> <span data-ttu-id="ee128-213">/ { | } は、使わないでください。</span><span class="sxs-lookup"><span data-stu-id="ee128-213">/ { | }.</span></span>  
  
## <a name="differences-between-uploading-and-publishing"></a><span data-ttu-id="ee128-214">アップロードとパブリッシュの相違点</span><span class="sxs-lookup"><span data-stu-id="ee128-214">Differences Between Uploading and Publishing</span></span>  
 <span data-ttu-id="ee128-215">レポート デザイナーまたはレポート ビルダーを使用してレポートと関連ファイルをライブラリにパブリッシュする場合、ファイルは検証されてから追加されます。</span><span class="sxs-lookup"><span data-stu-id="ee128-215">When you use Report Designer or Report Builder to publish reports and related files to a library, the files are validated before they are added.</span></span> <span data-ttu-id="ee128-216">SharePoint ライブラリで **[アップロード]** アクションを使用してレポートと関連ファイルをアップロードする場合、検証チェックは行われません。</span><span class="sxs-lookup"><span data-stu-id="ee128-216">If you upload reports and related files by using the **Upload** action on a SharePoint library, no validation check occurs.</span></span> <span data-ttu-id="ee128-217">ファイルが有効かどうかは、管理、編集、または実行のためにレポートにアクセスするまで知ることができません。</span><span class="sxs-lookup"><span data-stu-id="ee128-217">You will not know whether the file is valid until you access the report by managing, editing, or running it.</span></span>  
  
## <a name="updating-a-published-item"></a><span data-ttu-id="ee128-218">パブリッシュされたアイテムの更新</span><span class="sxs-lookup"><span data-stu-id="ee128-218">Updating a Published Item</span></span>  
 <span data-ttu-id="ee128-219">SharePoint ライブラリにアイテムをパブリッシュまたはアップロードした後、アイテムを更新するときは、まずアイテムをライブラリからチェックアウトする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee128-219">After you have published or uploaded an item to a SharePoint library, you should check the item out of the library before updating it.</span></span> <span data-ttu-id="ee128-220">レポートがチェックアウトされている間、他のユーザーはこのレポートを変更できなくなります。</span><span class="sxs-lookup"><span data-stu-id="ee128-220">While the report is checked out to you, you will be the only user who has permission to change the report.</span></span> <span data-ttu-id="ee128-221">変更が終わったら、レポートを再びチェックインします。</span><span class="sxs-lookup"><span data-stu-id="ee128-221">When you are finished, check it back in.</span></span>  
  
 <span data-ttu-id="ee128-222">最初にドキュメントをチェックアウトせずにレポートをアップロードまたはパブリッシュした場合 (既存のアイテムと同じ名前のアイテムをアップロードした場合など) は、レポート サーバーで自動的にアイテムがチェックアウトされ、既存アイテムの新しいバージョンとして更新後のレポートが追加された後、ドキュメントが再びチェックインされます。</span><span class="sxs-lookup"><span data-stu-id="ee128-222">If you upload or publish a report without checking the document out first (for example, by uploading an item that has the same name as an existing item), the report server will check it out for you, add the updated report as a new version of the existing item, and then check the document back in.</span></span>  
  
## <a name="external-images-as-resources"></a><span data-ttu-id="ee128-223">リソースとしての外部画像</span><span class="sxs-lookup"><span data-stu-id="ee128-223">External Images as Resources</span></span>  
 <span data-ttu-id="ee128-224">ネイティブ モードで実行しているレポート サーバーでは、リソースという概念がサポートされます。リソースとは、レポート サーバー上に保存されてセキュリティで保護されていても、レポート サーバーによる処理は行われないファイルのことです。</span><span class="sxs-lookup"><span data-stu-id="ee128-224">A report server that runs in native mode supports the concept of a resource, which is defined as any file that is stored and secured on the report server, but is not processed by the report server.</span></span> <span data-ttu-id="ee128-225">ネイティブ モードでは、どのような種類のファイルもリソースになります。</span><span class="sxs-lookup"><span data-stu-id="ee128-225">In native mode, it can be any kind of file.</span></span>  
  
 <span data-ttu-id="ee128-226">SharePoint 統合モードで実行しているレポート サーバーでは、リソースの概念は狭義になります。</span><span class="sxs-lookup"><span data-stu-id="ee128-226">When a report server runs in SharePoint integrated mode, the concept of a resource has a narrower definition.</span></span> <span data-ttu-id="ee128-227">この場合、レポート サーバーのリソースとは、外部画像を参照するレポートの保存場所を指します。</span><span class="sxs-lookup"><span data-stu-id="ee128-227">The report server retains the concept of a resource for storing reports that reference an external image.</span></span> <span data-ttu-id="ee128-228">レポートが内部用のスナップショットまたはコピーとして保持されている場合がこれに該当します。</span><span class="sxs-lookup"><span data-stu-id="ee128-228">This applies if the report is a snapshot or a copy that is kept for internal use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee128-229">参照</span><span class="sxs-lookup"><span data-stu-id="ee128-229">See Also</span></span>  
 <span data-ttu-id="ee128-230">[SharePoint ライブラリへのレポートのパブリッシュ](../reports/publish-a-report-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="ee128-230">[Publish a Report to a SharePoint Library](../reports/publish-a-report-to-a-sharepoint-library.md) </span></span>  
 <span data-ttu-id="ee128-231">[SharePoint ライブラリへの共有データ ソースのパブリッシュ](../reports/publish-a-shared-data-source-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="ee128-231">[Publish a Shared Data Source to a SharePoint Library](../reports/publish-a-shared-data-source-to-a-sharepoint-library.md) </span></span>  
 <span data-ttu-id="ee128-232">[[プロパティ ページ] ダイアログ ボックス](project-property-pages-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="ee128-232">[Project Property Pages Dialog Box](project-property-pages-dialog-box.md)</span></span>  
  
  