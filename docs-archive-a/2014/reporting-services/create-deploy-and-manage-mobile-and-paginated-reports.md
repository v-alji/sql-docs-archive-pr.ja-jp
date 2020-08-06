---
title: Reporting Services (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services]
- SSRS
- reports [Reporting Services], about reports
- Reporting Services
- SQL Server Reporting Services
ms.assetid: b8d18d3d-9db0-43e7-8286-7b46cc3a37ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0418acaab54032148f4bc6d42d06c97070b89e1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711765"
---
# <a name="reporting-services-ssrs"></a><span data-ttu-id="734bb-102">Reporting Services (SSRS)</span><span class="sxs-lookup"><span data-stu-id="734bb-102">Reporting Services (SSRS)</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<span data-ttu-id="734bb-103">に [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] は、組織のレポートの作成、展開、および管理に役立つ、すぐに使用できるツールとサービスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="734bb-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] provides a full range of ready-to-use tools and services to help you create, deploy, and manage reports for your organization.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="734bb-104">では、プログラミング機能を使用し、レポート作成機能を拡張したりカスタマイズしたりすることも可能です。</span><span class="sxs-lookup"><span data-stu-id="734bb-104">includes programming features that enable you to extend and customize your reporting functionality.</span></span>

 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="734bb-105">は、さまざまなデータソースに対して包括的なレポート機能を提供する、サーバーベースのレポートプラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="734bb-105">is a server-based reporting platform that provides comprehensive reporting functionality for a variety of data sources.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="734bb-106">に付属する完全なツール セットを使用してレポートを作成、管理、配布でき、付属する API を使用すると開発者はカスタム アプリケーションでデータおよびレポートの処理を統合および拡張できます。</span><span class="sxs-lookup"><span data-stu-id="734bb-106">includes a complete set of tools for you to create, manage, and deliver reports, and APIs that enable developers to integrate or extend data and report processing in custom applications.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="734bb-107">ツールは環境内で動作 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] し、ツールおよびコンポーネントと完全に統合されてい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="734bb-107">tools work within the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environment and are fully integrated with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tools and components.</span></span>

 <span data-ttu-id="734bb-108">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] では、リレーショナル データ ソース、多次元データ ソース、または XML ベースのデータ ソースから、対話形式、表形式、グラフィカル形式、または自由形式のレポートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="734bb-108">With [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], you can create interactive, tabular, graphical, or free-form reports from relational, multidimensional, or XML-based data sources.</span></span> <span data-ttu-id="734bb-109">レポートには、グラフ、地図、スパークラインなどの豊富なデータの可視化を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="734bb-109">Reports can include rich data visualization, including charts, maps, and sparklines.</span></span> <span data-ttu-id="734bb-110">レポートを発行し、レポート処理のスケジュールを設定し、レポートにオン デマンドでアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="734bb-110">You can publish reports, schedule report processing, or access reports on-demand.</span></span> <span data-ttu-id="734bb-111">さまざまな表示形式から選択でき、[!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] などの他のアプリケーションにレポートをエクスポートしたり、パブリッシュしたレポートをサブスクライブすることができます。</span><span class="sxs-lookup"><span data-stu-id="734bb-111">You can select from a variety of viewing formats, export reports to other applications such as [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)], and subscribe to published reports.</span></span> <span data-ttu-id="734bb-112">作成したレポートは、Web ベースの接続によって表示することも、[!INCLUDE[msCoName](../includes/msconame-md.md)] Windows アプリケーションや SharePoint サイトの一部として表示することも可能です。</span><span class="sxs-lookup"><span data-stu-id="734bb-112">The reports that you create can be viewed over a Web-based connection or as part of a [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows application or SharePoint site.</span></span> <span data-ttu-id="734bb-113">また、SharePoint サイトに発行されるレポートでデータ警告を作成したり、レポートのデータが変化したときに電子メール メッセージを受信したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="734bb-113">You can also create data alerts on reports published to a SharePoint site and receive email messages when report data changes.</span></span>

 <span data-ttu-id="734bb-114">の新機能の詳細について [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] は、「[新機能 &#40;Reporting Services&#41;](../../2014/reporting-services/what-s-new-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="734bb-114">For more information about features new in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], see [What's New &#40;Reporting Services&#41;](../../2014/reporting-services/what-s-new-reporting-services.md).</span></span>

 <span data-ttu-id="734bb-115">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のコンポーネント、ツール、およびリソースについては、 [SQL Server オンライン ブック](../index.yml)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="734bb-115">For information about other [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] components, tools, and resources, see [SQL Server Books Online](../index.yml).</span></span>

 <span data-ttu-id="734bb-116">[レポートサーバー Reporting Services](../../2014/reporting-services/reporting-services-report-server.md)領域![フォルダー](media/hlp-16folder.gif "フォルダー アイコン") **別にコンテンツを参照**する</span><span class="sxs-lookup"><span data-stu-id="734bb-116">**Browse Content by Area** ![Folder icon](media/hlp-16folder.gif "Folder icon") [Reporting Services Report Server](../../2014/reporting-services/reporting-services-report-server.md)</span></span>

 <span data-ttu-id="734bb-117">SSRS&#41;の![フォルダーアイコン](media/hlp-16folder.gif "フォルダー アイコン") [Reporting Services レポート &#40;](reports/reporting-services-reports-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="734bb-117">![Folder icon](media/hlp-16folder.gif "Folder icon") [Reporting Services Reports &#40;SSRS&#41;](reports/reporting-services-reports-ssrs.md)</span></span>

 <span data-ttu-id="734bb-118">![フォルダーアイコン](media/hlp-16folder.gif "フォルダー アイコン")[レポートデータ &#40;SSRS&#41;](report-data/report-data-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="734bb-118">![Folder icon](media/hlp-16folder.gif "Folder icon") [Report Data &#40;SSRS&#41;](report-data/report-data-ssrs.md)</span></span>

 <span data-ttu-id="734bb-119">![フォルダーアイコン](media/hlp-16folder.gif "フォルダー アイコン")[レポートパラメーター &#40;レポートビルダーとレポートデザイナー&#41;](report-design/report-parameters-report-builder-and-report-designer.md)</span><span class="sxs-lookup"><span data-stu-id="734bb-119">![Folder icon](media/hlp-16folder.gif "Folder icon") [Report Parameters &#40;Report Builder and Report Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md)</span></span>

 <span data-ttu-id="734bb-120">[レポートデザイナー &#40;SSRS&#41;の](report-design/report-parts-in-report-designer-ssrs.md)![フォルダーアイコン](media/hlp-16folder.gif "フォルダー アイコン")レポートパーツ</span><span class="sxs-lookup"><span data-stu-id="734bb-120">![Folder icon](media/hlp-16folder.gif "Folder icon") [Report Parts in Report Designer &#40;SSRS&#41;](report-design/report-parts-in-report-designer-ssrs.md)</span></span>

 <span data-ttu-id="734bb-121">![フォルダーアイコン](media/hlp-16folder.gif "フォルダー アイコン")の[スケジュール](subscriptions/schedules.md)</span><span class="sxs-lookup"><span data-stu-id="734bb-121">![Folder icon](media/hlp-16folder.gif "Folder icon") [Schedules](subscriptions/schedules.md)</span></span>

 <span data-ttu-id="734bb-122">![フォルダーアイコン](media/hlp-16folder.gif "フォルダー アイコン")[のサブスクリプションと配信 &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md)</span><span class="sxs-lookup"><span data-stu-id="734bb-122">![Folder icon](media/hlp-16folder.gif "Folder icon") [Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md)</span></span>

 <span data-ttu-id="734bb-123">[データ警告 Reporting Services](../ssms/agent/alerts.md) ![フォルダーアイコン](media/hlp-16folder.gif "フォルダー アイコン")</span><span class="sxs-lookup"><span data-stu-id="734bb-123">![Folder icon](media/hlp-16folder.gif "Folder icon") [Reporting Services Data Alerts](../ssms/agent/alerts.md)</span></span>

 <span data-ttu-id="734bb-124">![フォルダーアイコン](media/hlp-16folder.gif "フォルダー アイコン") [Power View](https://office.microsoft.com/excel-help/power-view-explore-visualize-and-present-your-data-HA102835634.aspx)</span><span class="sxs-lookup"><span data-stu-id="734bb-124">![Folder icon](media/hlp-16folder.gif "Folder icon") [Power View](https://office.microsoft.com/excel-help/power-view-explore-visualize-and-present-your-data-HA102835634.aspx)</span></span>

 <span data-ttu-id="734bb-125">![フォルダーアイコン](media/hlp-16folder.gif "フォルダー アイコン") [Reporting Services のセキュリティと保護](security/reporting-services-security-and-protection.md)</span><span class="sxs-lookup"><span data-stu-id="734bb-125">![Folder icon](media/hlp-16folder.gif "Folder icon") [Reporting Services Security and Protection](security/reporting-services-security-and-protection.md)</span></span>

 <span data-ttu-id="734bb-126">![フォルダーアイコン](media/hlp-16folder.gif "フォルダー アイコン") [URL アクセス &#40;SSRS&#41;](url-access-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="734bb-126">![Folder icon](media/hlp-16folder.gif "Folder icon") [URL Access &#40;SSRS&#41;](url-access-ssrs.md)</span></span>

 <span data-ttu-id="734bb-127">![Folder icon](media/hlp-16folder.gif "フォルダー アイコン") [SSRS&#41;&#40;フォルダーアイコン拡張機能](extensions-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="734bb-127">![Folder icon](media/hlp-16folder.gif "Folder icon") [Extensions &#40;SSRS&#41;](extensions-ssrs.md)</span></span>

 <span data-ttu-id="734bb-128">![フォルダーアイコン](media/hlp-16folder.gif "フォルダー アイコン") [Reporting Services ツール](tools/reporting-services-tools.md)</span><span class="sxs-lookup"><span data-stu-id="734bb-128">![Folder icon](media/hlp-16folder.gif "Folder icon") [Reporting Services Tools](tools/reporting-services-tools.md)</span></span>

 <span data-ttu-id="734bb-129">![フォルダーアイコン](media/hlp-16folder.gif "フォルダー アイコン")[のエラーとイベントのリファレンス &#40;Reporting Services&#41;](troubleshooting/errors-and-events-reference-reporting-services.md)</span><span class="sxs-lookup"><span data-stu-id="734bb-129">![Folder icon](media/hlp-16folder.gif "Folder icon") [Errors and Events Reference &#40;Reporting Services&#41;](troubleshooting/errors-and-events-reference-reporting-services.md)</span></span>

 <span data-ttu-id="734bb-130">![フォルダーアイコン](media/hlp-16folder.gif "フォルダー アイコン")[機能の参照 &#40;Reporting Services&#41;](feature-reference-reporting-services.md)</span><span class="sxs-lookup"><span data-stu-id="734bb-130">![Folder icon](media/hlp-16folder.gif "Folder icon") [Feature Reference &#40;Reporting Services&#41;](feature-reference-reporting-services.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="734bb-131">参照</span><span class="sxs-lookup"><span data-stu-id="734bb-131">See Also</span></span>
 [<span data-ttu-id="734bb-132">SQL Server リソース センター</span><span class="sxs-lookup"><span data-stu-id="734bb-132">SQL Server Resource Center</span></span>](https://go.microsoft.com/fwlink/?linkID=219676)


