---
title: '[表示] ページ、レポート (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4874ba29-429b-4dd4-a8cb-d4f087237dc2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4eb5733bf6ddfc8d7ba5a1d3d6f5ebe18ce85c66
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737782"
---
# <a name="view-page-reports-report-manager"></a><span data-ttu-id="12502-102">[表示] ページ、レポート (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="12502-102">View Page, Reports (Report Manager)</span></span>
  <span data-ttu-id="12502-103">レポートの [表示] ページではレポートを参照できます。</span><span class="sxs-lookup"><span data-stu-id="12502-103">Use the View page for reports to view a report.</span></span> <span data-ttu-id="12502-104">レポートをレポート マネージャーで最初に開くと、HTML で書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="12502-104">When you first open a report in Report Manager, it is formatted in HTML.</span></span> <span data-ttu-id="12502-105">HTML レポートの場合、レポートの一番上に [レポート] ツール バーが表示されます。このツール バーを使用すると、レポート ページ間の移動、レポート内の検索、または異なる形式でのレポートの表示が可能になります。</span><span class="sxs-lookup"><span data-stu-id="12502-105">HTML reports include a report toolbar that appears at the top of the report so that you can navigate through report pages, search within a report, or export the report to a different format.</span></span> <span data-ttu-id="12502-106">次の図は、[レポート] ツール バーを示しています。</span><span class="sxs-lookup"><span data-stu-id="12502-106">The following diagram shows the report toolbar.</span></span>  
  
 <span data-ttu-id="12502-107">![レポート ツール バー](media/htmlviewer-toolbar.gif "レポート ツール バー")</span><span class="sxs-lookup"><span data-stu-id="12502-107">![Report toolbar](media/htmlviewer-toolbar.gif "Report toolbar")</span></span>  
<span data-ttu-id="12502-108">レポート ツール バー</span><span class="sxs-lookup"><span data-stu-id="12502-108">Report toolbar</span></span>  
  
 <span data-ttu-id="12502-109">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]では、レポートを要求時に実行するか、レポート実行スナップショットから実行するかを構成できます。</span><span class="sxs-lookup"><span data-stu-id="12502-109">In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], reports can be configured to run on demand or from a report execution snapshot.</span></span> <span data-ttu-id="12502-110">レポートを要求時に実行する場合、すべてのデータ処理およびレポート処理が、レポートを開くたびに実行されます。</span><span class="sxs-lookup"><span data-stu-id="12502-110">If a report is run on demand, all data processing and report processing occur each time you open the report.</span></span> <span data-ttu-id="12502-111">レポートをレポート実行スナップショットとして実行するよう構成している場合、スナップショットの作成時にデータ処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="12502-111">If you view a report that is configured to run as a report execution snapshot, data processing occurred when the snapshot was created.</span></span>  
  
## <a name="exporting-reports"></a><span data-ttu-id="12502-112">レポートのエクスポート</span><span class="sxs-lookup"><span data-stu-id="12502-112">Exporting Reports</span></span>  
 <span data-ttu-id="12502-113">エクスポートの形式によっては、レポートの機能が一部失われる場合があります。</span><span class="sxs-lookup"><span data-stu-id="12502-113">Not all report features are available in all of the export formats.</span></span> <span data-ttu-id="12502-114">HTML レポートを別の形式にエクスポートすると、レポートの表示形式が一部異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="12502-114">If you export an HTML report to another format, you can expect to see some differences in how the report appears.</span></span> <span data-ttu-id="12502-115">また、レポートに対話機能 (ハイパーリンク、ブックマーク、またはドキュメント マップ) が含まれている場合、別の形式ではこれらの機能が使用できなかったり、同じように動作しなかったりする場合があります。</span><span class="sxs-lookup"><span data-stu-id="12502-115">Also, if the report includes interactive features (such as hyperlinks, bookmarks, or document maps) those features might not be available or work the same way in the new format.</span></span>  
  
## <a name="generating-data-feeds-from-report-data"></a><span data-ttu-id="12502-116">レポート データからのデータ フィードの生成</span><span class="sxs-lookup"><span data-stu-id="12502-116">Generating Data Feeds from Report Data</span></span>  
 <span data-ttu-id="12502-117">レポートからは、データ フィードを生成できます。</span><span class="sxs-lookup"><span data-stu-id="12502-117">You can generate data feeds from reports.</span></span> <span data-ttu-id="12502-118">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Atom 表示拡張機能は、2 種類の Atom 準拠のドキュメント (レポートから提供されるデータ フィードとレポート データを含むデータ フィードを一覧表示する Atom サービス ドキュメント) を生成します。</span><span class="sxs-lookup"><span data-stu-id="12502-118">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Atom rendering extension generates two Atom-compliant documents: an Atom service document that lists the data feeds the report provides and the data feeds that contains the report data.</span></span> <span data-ttu-id="12502-119">データ フィードは、Atom 準拠のデータ フィードを使用するアプリケーションで読み取りと交換が可能な標準化された Atom 1.0 準拠の形式で、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] によって生成されます。</span><span class="sxs-lookup"><span data-stu-id="12502-119">The data feeds are generated by [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in a standardized Atom 1.0 compliant format that it readable and exchangeable with applications that consume Atom compliant data feeds.</span></span> <span data-ttu-id="12502-120">たとえば、 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] クライアントは、レポートから生成されたデータ フィードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="12502-120">For example the [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] client can consume data feeds that are generated from reports.</span></span>  
  
## <a name="running-parameterized-reports"></a><span data-ttu-id="12502-121">パラメーター化されたレポートの実行</span><span class="sxs-lookup"><span data-stu-id="12502-121">Running Parameterized Reports</span></span>  
 <span data-ttu-id="12502-122">入力フィールドおよび **[レポートの表示]** ボタンが含まれているレポートは、パラメーター化されたレポートです。</span><span class="sxs-lookup"><span data-stu-id="12502-122">A report that contains input fields and a **View Report** button is a parameterized report.</span></span> <span data-ttu-id="12502-123">パラメーター化されたレポートを表示する際、レポートの実行に使用する値を指定する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="12502-123">To view a parameterized report, you may need to provide values that are used to run the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="12502-124">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のどのエディションでも、レポート実行スナップショットおよび一部のエクスポート形式は使用できません。</span><span class="sxs-lookup"><span data-stu-id="12502-124">Report execution snapshots and some export formats are not available in all editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="12502-125">詳しくは「 [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="12502-125">For more information, see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12502-126">参照</span><span class="sxs-lookup"><span data-stu-id="12502-126">See Also</span></span>  
 <span data-ttu-id="12502-127">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="12502-127">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="12502-128">レポート マネージャー F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="12502-128">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
