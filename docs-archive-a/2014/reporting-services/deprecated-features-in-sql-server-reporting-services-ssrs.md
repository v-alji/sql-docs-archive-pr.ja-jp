---
title: SQL Server 2014 | の SQL Server Reporting Services の非推奨の機能Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- deprecated features [Reporting Services]
- HTML OWC rendering extension [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: 3876c01e-f81d-4cce-9104-5106a8c369e6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af858ae94bf5ea3d9f0cfe0b99759442dabd6629
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641501"
---
# <a name="deprecated-features-in-sql-server-reporting-services-in-sql-server-2014"></a><span data-ttu-id="818a7-102">SQL Server 2014 における SQL Server Reporting Services の非推奨機能</span><span class="sxs-lookup"><span data-stu-id="818a7-102">Deprecated Features in SQL Server Reporting Services in SQL Server 2014</span></span>
  <span data-ttu-id="818a7-103">このトピックでは、非推奨とされた [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="818a7-103">This topic describes the deprecated [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features.</span></span> <span data-ttu-id="818a7-104">非推奨とされたリリースで機能を引き続き使用できますが、これらの機能は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の今後のリリースで削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="818a7-104">The features are still available in the release in which they are deprecated; however the features are scheduled to be removed in a future release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="818a7-105">非推奨の機能を新しいアプリケーションで使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="818a7-105">Deprecated features should not be used in new applications.</span></span>  
  
 <span data-ttu-id="818a7-106">このトピックの内容:</span><span class="sxs-lookup"><span data-stu-id="818a7-106">In this topic:</span></span>  
  
-   [<span data-ttu-id="818a7-107">SQL Server 2014 Reporting Services の非推奨の機能</span><span class="sxs-lookup"><span data-stu-id="818a7-107">SQL Server 2014 Reporting Services Deprecated Features</span></span>](#bkmk_2014)  
  
-   [<span data-ttu-id="818a7-108">SQL Server 2012 SP1 Reporting Services の非推奨の機能</span><span class="sxs-lookup"><span data-stu-id="818a7-108">SQL Server 2012 SP1 Reporting Services Deprecated Features</span></span>](#bkmk_2012sp1)  
  
-   [<span data-ttu-id="818a7-109">SQL Server 2012 Reporting Services の非推奨の機能</span><span class="sxs-lookup"><span data-stu-id="818a7-109">SQL Server 2012 Reporting Services Deprecated Features</span></span>](#bkmk_2012)  
  
-   [<span data-ttu-id="818a7-110">SQL Server 2008 R2 Reporting Services の非推奨の機能</span><span class="sxs-lookup"><span data-stu-id="818a7-110">SQL Server 2008 R2 Reporting Services Deprecated Features</span></span>](#bkmk_kj)  
  
##  <a name="sql-server-2014-reporting-services-deprecated-features"></a><a name="bkmk_2014"></a><span data-ttu-id="818a7-111">SQL Server 2014 Reporting Services 非推奨の機能</span><span class="sxs-lookup"><span data-stu-id="818a7-111">SQL Server 2014 Reporting Services Deprecated Features</span></span>  
  
### <a name="features-not-supported-in-the-next-version-of-sql-server"></a><span data-ttu-id="818a7-112">SQL Server の次のバージョンでサポートされない機能</span><span class="sxs-lookup"><span data-stu-id="818a7-112">Features Not Supported in the Next Version of SQL Server</span></span>  
 <span data-ttu-id="818a7-113">次 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のバージョンので**は、次**の機能はサポートされません [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="818a7-113">The following [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features will not be supported in the **next** version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="818a7-114">新規の開発作業ではこれらの機能を使用しないようにし、現在これらの機能を使用しているアプリケーションはできるだけ早く修正してください。</span><span class="sxs-lookup"><span data-stu-id="818a7-114">Do not use these features in new development work, and modify applications that currently use these features as soon as possible.</span></span>  
  
#### <a name="html-rendering-extension-device-information-settings"></a><span data-ttu-id="818a7-115">HTML 表示拡張機能のデバイス情報設定</span><span class="sxs-lookup"><span data-stu-id="818a7-115">HTML Rendering Extension Device Information Settings</span></span>  
 <span data-ttu-id="818a7-116">HTML 表示拡張機能の次のデバイス情報設定は、非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="818a7-116">The following device information settings for the HTML rendering extension are deprecated.</span></span>  
  
-   <span data-ttu-id="818a7-117">ActionScript</span><span class="sxs-lookup"><span data-stu-id="818a7-117">ActionScript</span></span>  
  
-   <span data-ttu-id="818a7-118">ActiveXControls</span><span class="sxs-lookup"><span data-stu-id="818a7-118">ActiveXControls</span></span>  
  
-   <span data-ttu-id="818a7-119">GetImage</span><span class="sxs-lookup"><span data-stu-id="818a7-119">GetImage</span></span>  
  
-   <span data-ttu-id="818a7-120">OnlyVisibleStyles</span><span class="sxs-lookup"><span data-stu-id="818a7-120">OnlyVisibleStyles</span></span>  
  
-   <span data-ttu-id="818a7-121">ReplacementRoot</span><span class="sxs-lookup"><span data-stu-id="818a7-121">ReplacementRoot</span></span>  
  
-   <span data-ttu-id="818a7-122">ResourceStreamRoot</span><span class="sxs-lookup"><span data-stu-id="818a7-122">ResourceStreamRoot</span></span>  
  
-   <span data-ttu-id="818a7-123">StreamRoot</span><span class="sxs-lookup"><span data-stu-id="818a7-123">StreamRoot</span></span>  
  
-   <span data-ttu-id="818a7-124">UsePx</span><span class="sxs-lookup"><span data-stu-id="818a7-124">UsePx</span></span>  
  
-   <span data-ttu-id="818a7-125">Zoom</span><span class="sxs-lookup"><span data-stu-id="818a7-125">Zoom</span></span>  
  
 <span data-ttu-id="818a7-126">HTML 表示拡張機能の詳細については、「 [HTML Device Information Settings](html-device-information-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="818a7-126">For more information on the HTML rendering extension, see [HTML Device Information Settings](html-device-information-settings.md)</span></span>  
  
#### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a><span data-ttu-id="818a7-127">Microsoft Word および Microsoft Excel 1997-2003 表示拡張機能</span><span class="sxs-lookup"><span data-stu-id="818a7-127">Microsoft Word and Microsoft Excel 1997-2003 Rendering</span></span>  
 <span data-ttu-id="818a7-128">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]BIFF8 の表示拡張機能は、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[msCoName](../includes/msconame-md.md)] Word および [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003 バイナリインターチェンジファイル形式を報告します。</span><span class="sxs-lookup"><span data-stu-id="818a7-128">The[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] BIFF8 rendering extensions [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports to the [!INCLUDE[msCoName](../includes/msconame-md.md)] Word and [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003 binary interchange file format.</span></span> [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]<span data-ttu-id="818a7-129">Office 2007-2010 Open XML 形式で表示される拡張機能が含まれてい [!INCLUDE[msCoName](../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="818a7-129">includes extensions that render in the [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 Open XML format.</span></span>  
  
#### <a name="report-definition-language-rdl-2005-and-earlier"></a><span data-ttu-id="818a7-130">レポート定義言語 (RDL) 2005 以前</span><span class="sxs-lookup"><span data-stu-id="818a7-130">Report Definition Language (RDL) 2005 and Earlier</span></span>  
 <span data-ttu-id="818a7-131">レポート定義言語 (RDL) 2005 およびそれ以前のバージョンは非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="818a7-131">Report Definition Language (RDL) 2005 and earlier is deprecated.</span></span> <span data-ttu-id="818a7-132">RDL の詳細については、「[レポート定義言語 &#40;SSRS&#41;](reports/report-definition-language-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="818a7-132">For more information about RDL, see [Report Definition Language &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).</span></span>  
  
 <span data-ttu-id="818a7-133">レポートのアップグレードの詳細については、「 [Upgrade Reports](install-windows/upgrade-reports.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="818a7-133">For more information on upgrading reports, see [Upgrade Reports](install-windows/upgrade-reports.md).</span></span>  
  
#### <a name="sql-server-2005-and-earlier-custom-report-items"></a><span data-ttu-id="818a7-134">SQL Server 2005 およびそれ以前のバージョンのカスタム レポート アイテム</span><span class="sxs-lookup"><span data-stu-id="818a7-134">SQL Server 2005 and earlier Custom Report Items</span></span>  
 <span data-ttu-id="818a7-135">2005以前のバージョンでコンパイルされたカスタムレポートアイテム (CRI) [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] は非推奨となりました。</span><span class="sxs-lookup"><span data-stu-id="818a7-135">Custom Report Items (CRI) compiled for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 and earlier are deprecated.</span></span>  
  
#### <a name="reporting-services-snapshots-2005-and-earlier"></a><span data-ttu-id="818a7-136">Reporting Services Snapshots 2005 およびそれ以前のバージョン</span><span class="sxs-lookup"><span data-stu-id="818a7-136">Reporting Services Snapshots 2005 and earlier</span></span>  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="818a7-137">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 以前でレンダリングされたスナップショットは非推奨となりました。</span><span class="sxs-lookup"><span data-stu-id="818a7-137">snapshots rendered with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 and earlier are deprecated.</span></span>  
  
#### <a name="report-models"></a><span data-ttu-id="818a7-138">レポート モデル</span><span class="sxs-lookup"><span data-stu-id="818a7-138">Report Models</span></span>  
 <span data-ttu-id="818a7-139">セマンティック モデリング言語 (SMDL) レポート モデルは非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="818a7-139">Semantic modeling language (SMDL) report models are deprecated.</span></span> <span data-ttu-id="818a7-140">既存のレポートモデルをレポートのデータソースとして使用することもできますが、レポート [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] モデルへの依存関係を削除するには、レポートの更新を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="818a7-140">Although you can you continue to use existing report models as data sources in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports you should consider updating your reports to remove their dependency on report models.</span></span>  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]<span data-ttu-id="818a7-141">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]には、レポートモデルを作成または更新するためのツールは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="818a7-141">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] does not include tools for creating or updating report models.</span></span> <span data-ttu-id="818a7-142">詳細については、 [SQL Server 2014 の SQL Server Reporting Services での重大な変更に](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="818a7-142">For more information, see [Breaking Changes in SQL Server Reporting Services in SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).</span></span>  
  
#### <a name="deprecated-methods-in-the-web-service-endpoint"></a><span data-ttu-id="818a7-143">Web サービス エンドポイントで非推奨のメソッド</span><span class="sxs-lookup"><span data-stu-id="818a7-143">Deprecated Methods in the Web Service Endpoint</span></span>  
 <span data-ttu-id="818a7-144">次の操作は、<xref:ReportService2010.ReportingService2010> Web サービス エンドポイントでは非推奨です：</span><span class="sxs-lookup"><span data-stu-id="818a7-144">The following operations are deprecated in the <xref:ReportService2010.ReportingService2010> Web service endpoint:</span></span>  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
#### <a name="sharepoint-web-parts"></a><span data-ttu-id="818a7-145">Sharepoint Web パーツ</span><span class="sxs-lookup"><span data-stu-id="818a7-145">SharePoint Web Parts</span></span>  
 <span data-ttu-id="818a7-146">インストール キャビネット ファイル **RSWebParts.cab** とその cab ファイルから抽出できる SharePoint Web パーツは非推奨とされています。</span><span class="sxs-lookup"><span data-stu-id="818a7-146">The installation cabinet file **RSWebParts.cab** and the SharePoint web parts that can be extracted from the cab file, are deprecated.</span></span> <span data-ttu-id="818a7-147">非推奨の web パーツは、レポートエクスプローラー (**Spexplorer.**.dwp) とレポートビューアー (**spexplorer. .dwp**) です。</span><span class="sxs-lookup"><span data-stu-id="818a7-147">The deprecated web parts are Report Explorer (**SPExplorer.dwp**) and Report Viewer (**SPViewer.dwp**).</span></span>  
  
 <span data-ttu-id="818a7-148">非推奨の web パーツの詳細については、「 [SharePoint Web パーツを使用したネイティブモードのレポートの表示と探索 (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="818a7-148">For more information on the deprecated web parts, see [View and Explore Native Mode Reports Using SharePoint Web Parts (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx)</span></span>  
  
### <a name="features-not-supported-in-a-future-version-of-sql-server"></a><span data-ttu-id="818a7-149">SQL Server の今後のバージョンでサポートされない機能</span><span class="sxs-lookup"><span data-stu-id="818a7-149">Features Not Supported in a Future Version of SQL Server</span></span>  
 <span data-ttu-id="818a7-150">以下の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 機能は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の次のバージョンではサポートされますが、その後のバージョンでは削除されます。</span><span class="sxs-lookup"><span data-stu-id="818a7-150">The following [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features are supported in the next version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], but will be removed in a later version.</span></span> <span data-ttu-id="818a7-151">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のどのバージョンであるかは決定していません。</span><span class="sxs-lookup"><span data-stu-id="818a7-151">The specific version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] has not been determined.</span></span>  
  
 <span data-ttu-id="818a7-152">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] で非推奨の [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]機能はありません。</span><span class="sxs-lookup"><span data-stu-id="818a7-152">No [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features were deprecated in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
##  <a name="sql-server-2012-sp1-reporting-services-deprecated-features"></a><a name="bkmk_2012sp1"></a><span data-ttu-id="818a7-153">SQL Server 2012 SP1 Reporting Services 非推奨の機能</span><span class="sxs-lookup"><span data-stu-id="818a7-153">SQL Server 2012 SP1 Reporting Services Deprecated Features</span></span>  
 <span data-ttu-id="818a7-154">ここでは、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] で非推奨とされた [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] 機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="818a7-154">This section describes [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features deprecated in [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)].</span></span> <span data-ttu-id="818a7-155">以下の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 機能は [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]の次のバージョンではサポートされますが、その後のバージョンでは削除されます。</span><span class="sxs-lookup"><span data-stu-id="818a7-155">The following [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features are supported in the next version of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], but will be removed in a later version.</span></span> <span data-ttu-id="818a7-156">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のどのバージョンであるかは決定していません。</span><span class="sxs-lookup"><span data-stu-id="818a7-156">The specific version of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] has not been determined.</span></span>  
  
### <a name="sharepoint-web-parts"></a><span data-ttu-id="818a7-157">Sharepoint Web パーツ</span><span class="sxs-lookup"><span data-stu-id="818a7-157">SharePoint Web Parts</span></span>  
 <span data-ttu-id="818a7-158">インストール キャビネット ファイル **RSWebParts.cab** とその cab ファイルから抽出できる SharePoint Web パーツは非推奨とされています。</span><span class="sxs-lookup"><span data-stu-id="818a7-158">The installation cabinet file **RSWebParts.cab** and the SharePoint web parts that can be extracted from the cab file, are deprecated.</span></span> <span data-ttu-id="818a7-159">非推奨の web パーツは、レポートエクスプローラー (**Spexplorer.**.dwp) とレポートビューアー (**spexplorer. .dwp**) です。</span><span class="sxs-lookup"><span data-stu-id="818a7-159">The deprecated web parts are Report Explorer (**SPExplorer.dwp**) and Report Viewer (**SPViewer.dwp**).</span></span>  
  
 <span data-ttu-id="818a7-160">非推奨の web パーツの詳細については、「 [SharePoint Web パーツを使用したネイティブモードのレポートの表示と探索 (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="818a7-160">For more information on the deprecated web parts, see [View and Explore Native Mode Reports Using SharePoint Web Parts (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx)</span></span>  
  
##  <a name="sql-server-2012-reporting-services-deprecated-features"></a><a name="bkmk_2012"></a><span data-ttu-id="818a7-161">SQL Server 2012 Reporting Services 非推奨の機能</span><span class="sxs-lookup"><span data-stu-id="818a7-161">SQL Server 2012 Reporting Services Deprecated Features</span></span>  
 <span data-ttu-id="818a7-162">ここでは、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] で非推奨とされた [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="818a7-162">This section describes [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features deprecated in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span>  
  
### <a name="html-rendering-extension-device-information-settings"></a><span data-ttu-id="818a7-163">HTML 表示拡張機能のデバイス情報設定</span><span class="sxs-lookup"><span data-stu-id="818a7-163">HTML Rendering Extension Device Information Settings</span></span>  
 <span data-ttu-id="818a7-164">HTML 表示拡張機能の次のデバイス情報設定は、非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="818a7-164">The following device information settings for the HTML rendering extension are deprecated.</span></span>  
  
-   <span data-ttu-id="818a7-165">ActionScript</span><span class="sxs-lookup"><span data-stu-id="818a7-165">ActionScript</span></span>  
  
-   <span data-ttu-id="818a7-166">ActiveXControls</span><span class="sxs-lookup"><span data-stu-id="818a7-166">ActiveXControls</span></span>  
  
-   <span data-ttu-id="818a7-167">GetImage</span><span class="sxs-lookup"><span data-stu-id="818a7-167">GetImage</span></span>  
  
-   <span data-ttu-id="818a7-168">OnlyVisibleStyles</span><span class="sxs-lookup"><span data-stu-id="818a7-168">OnlyVisibleStyles</span></span>  
  
-   <span data-ttu-id="818a7-169">ReplacementRoot</span><span class="sxs-lookup"><span data-stu-id="818a7-169">ReplacementRoot</span></span>  
  
-   <span data-ttu-id="818a7-170">ResourceStreamRoot</span><span class="sxs-lookup"><span data-stu-id="818a7-170">ResourceStreamRoot</span></span>  
  
-   <span data-ttu-id="818a7-171">StreamRoot</span><span class="sxs-lookup"><span data-stu-id="818a7-171">StreamRoot</span></span>  
  
-   <span data-ttu-id="818a7-172">UsePx</span><span class="sxs-lookup"><span data-stu-id="818a7-172">UsePx</span></span>  
  
-   <span data-ttu-id="818a7-173">Zoom</span><span class="sxs-lookup"><span data-stu-id="818a7-173">Zoom</span></span>  
  
 <span data-ttu-id="818a7-174">HTML 表示拡張機能の詳細については、「 [HTML Device Information Settings](html-device-information-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="818a7-174">For more information on the HTML rendering extension, see [HTML Device Information Settings](html-device-information-settings.md)</span></span>  
  
### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a><span data-ttu-id="818a7-175">Microsoft Word および Microsoft Excel 1997-2003 表示拡張機能</span><span class="sxs-lookup"><span data-stu-id="818a7-175">Microsoft Word and Microsoft Excel 1997-2003 Rendering</span></span>  
 <span data-ttu-id="818a7-176">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]BIFF8 の表示拡張機能は、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[msCoName](../includes/msconame-md.md)] Word および [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003 バイナリインターチェンジファイル形式を報告します。</span><span class="sxs-lookup"><span data-stu-id="818a7-176">The[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] BIFF8 rendering extensions [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports to the [!INCLUDE[msCoName](../includes/msconame-md.md)] Word and [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003 binary interchange file format.</span></span> [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]<span data-ttu-id="818a7-177">Office 2007-2010 Open XML 形式で表示される拡張機能が含まれてい [!INCLUDE[msCoName](../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="818a7-177">includes extensions that render in the [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 Open XML format.</span></span>  
  
### <a name="report-definition-language-rdl-2005-and-earlier"></a><span data-ttu-id="818a7-178">レポート定義言語 (RDL) 2005 以前</span><span class="sxs-lookup"><span data-stu-id="818a7-178">Report Definition Language (RDL) 2005 and Earlier</span></span>  
 <span data-ttu-id="818a7-179">レポート定義言語 (RDL) 2005 およびそれ以前のバージョンは非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="818a7-179">Report Definition Language (RDL) 2005 and earlier is deprecated.</span></span> <span data-ttu-id="818a7-180">RDL の詳細については、「[レポート定義言語 &#40;SSRS&#41;](reports/report-definition-language-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="818a7-180">For more information about RDL, see [Report Definition Language &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).</span></span>  
  
 <span data-ttu-id="818a7-181">レポートのアップグレードの詳細については、「 [Upgrade Reports](install-windows/upgrade-reports.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="818a7-181">For more information on upgrading reports, see [Upgrade Reports](install-windows/upgrade-reports.md).</span></span>  
  
### <a name="sql-server-2005-and-earlier-custom-report-items"></a><span data-ttu-id="818a7-182">SQL Server 2005 およびそれ以前のバージョンのカスタム レポート アイテム</span><span class="sxs-lookup"><span data-stu-id="818a7-182">SQL Server 2005 and earlier Custom Report Items</span></span>  
 <span data-ttu-id="818a7-183">2005以前のバージョンでコンパイルされたカスタムレポートアイテム (CRI) [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] は非推奨となりました。</span><span class="sxs-lookup"><span data-stu-id="818a7-183">Custom Report Items (CRI) compiled for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 and earlier are deprecated.</span></span>  
  
### <a name="reporting-services-snapshots-2005-and-earlier"></a><span data-ttu-id="818a7-184">Reporting Services Snapshots 2005 およびそれ以前のバージョン</span><span class="sxs-lookup"><span data-stu-id="818a7-184">Reporting Services Snapshots 2005 and earlier</span></span>  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="818a7-185">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 以前でレンダリングされたスナップショットは非推奨となりました。</span><span class="sxs-lookup"><span data-stu-id="818a7-185">snapshots rendered with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 and earlier are deprecated.</span></span>  
  
### <a name="report-models"></a><span data-ttu-id="818a7-186">レポート モデル</span><span class="sxs-lookup"><span data-stu-id="818a7-186">Report Models</span></span>  
 <span data-ttu-id="818a7-187">セマンティック モデリング言語 (SMDL) レポート モデルは非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="818a7-187">Semantic modeling language (SMDL) report models are deprecated.</span></span> <span data-ttu-id="818a7-188">既存のレポートモデルをレポートのデータソースとして使用することもできますが、レポート [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] モデルへの依存関係を削除するには、レポートの更新を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="818a7-188">Although you can you continue to use existing report models as data sources in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports you should consider updating your reports to remove their dependency on report models.</span></span>  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]<span data-ttu-id="818a7-189">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]には、レポートモデルを作成または更新するためのツールは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="818a7-189">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] does not include tools for creating or updating report models.</span></span> <span data-ttu-id="818a7-190">詳細については、 [SQL Server 2014 の SQL Server Reporting Services での重大な変更に](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="818a7-190">For more information, see [Breaking Changes in SQL Server Reporting Services in SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).</span></span>  
  
### <a name="deprecated-methods-in-the-web-service-endpoint"></a><span data-ttu-id="818a7-191">Web サービス エンドポイントで非推奨のメソッド</span><span class="sxs-lookup"><span data-stu-id="818a7-191">Deprecated Methods in the Web Service Endpoint</span></span>  
 <span data-ttu-id="818a7-192">次の操作は、<xref:ReportService2010.ReportingService2010> Web サービス エンドポイントでは非推奨です：</span><span class="sxs-lookup"><span data-stu-id="818a7-192">The following operations are deprecated in the <xref:ReportService2010.ReportingService2010> Web service endpoint:</span></span>  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
##  <a name="sql-server-2008-r2-reporting-services-deprecated-features"></a><a name="bkmk_kj"></a><span data-ttu-id="818a7-193">SQL Server 2008 R2 Reporting Services 非推奨の機能</span><span class="sxs-lookup"><span data-stu-id="818a7-193">SQL Server 2008 R2 Reporting Services Deprecated Features</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="818a7-194">SQL Server 2008 R2 は SQL Server 2008 のマイナー バージョン アップグレードなので、SQL Server 2008 のセクションのコンテンツも確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="818a7-194">Because SQL Server 2008 R2 is a minor version upgrade of SQL Server 2008, we recommend that you also review the content in the SQL Server 2008 section.</span></span>  
  
### <a name="report-server-web-service-endpoints"></a><span data-ttu-id="818a7-195">レポート サーバー Web サービスのエンドポイント</span><span class="sxs-lookup"><span data-stu-id="818a7-195">Report Server Web Service Endpoints</span></span>  
 <span data-ttu-id="818a7-196">このリリースでは、Web サービスの <xref:ReportService2005.ReportingService2005> および <xref:ReportService2006.ReportingService2006> が非推奨になっています。</span><span class="sxs-lookup"><span data-stu-id="818a7-196">The Web services <xref:ReportService2005.ReportingService2005> and <xref:ReportService2006.ReportingService2006> have been deprecated in this release.</span></span> <span data-ttu-id="818a7-197">これらのエンドポイントは、新しいエンドポイント <xref:ReportService2010.ReportingService2010> に置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="818a7-197">These endpoints have been replaced by a new endpoint: <xref:ReportService2010.ReportingService2010>.</span></span>  
  
 <span data-ttu-id="818a7-198">新しいエンドポイントには、非推奨のエンドポイントで使用できるすべての機能と SQL Server 2008 R2 で導入された新しい機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="818a7-198">The new endpoint includes all the functionality available in the deprecated endpoints and the new features introduced in SQL Server 2008 R2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="818a7-199">参照</span><span class="sxs-lookup"><span data-stu-id="818a7-199">See Also</span></span>  
 <span data-ttu-id="818a7-200">[新機能 &#40;Reporting Services&#41;](what-s-new-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="818a7-200">[What's New &#40;Reporting Services&#41;](what-s-new-reporting-services.md) </span></span>  
 <span data-ttu-id="818a7-201">[旧バージョンとの互換性](../getting-started/backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="818a7-201">[Backward Compatibility](../getting-started/backward-compatibility.md) </span></span>  
 <span data-ttu-id="818a7-202">[SQL Server 2014 での SQL Server Reporting Services の動作の変更](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="818a7-202">[Behavior Changes to SQL Server Reporting Services  in SQL Server 2014](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md) </span></span>  
 [<span data-ttu-id="818a7-203">SQL Server 2014 で廃止された SQL Server Reporting Services の機能</span><span class="sxs-lookup"><span data-stu-id="818a7-203">Discontinued Functionality to SQL Server Reporting Services in SQL Server 2014</span></span>](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  
  
  
