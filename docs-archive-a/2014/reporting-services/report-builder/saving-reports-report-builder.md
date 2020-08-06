---
title: レポートの保存 (レポート ビルダー) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 59ddc4b8-9517-4d3f-9c88-a07e9907cecb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9210eafb65ee7adced8d0cd821d88b5f0cbcb9c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631615"
---
# <a name="saving-reports-report-builder"></a><span data-ttu-id="f0410-102">レポートの保存 (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="f0410-102">Saving Reports (Report Builder)</span></span>
  <span data-ttu-id="f0410-103">レポート ビルダーでは、自分が書き込み権限を持っているレポート サーバー、SharePoint ライブラリ、またはファイル共有、あるいは自分のコンピューターにレポートを保存できます。</span><span class="sxs-lookup"><span data-stu-id="f0410-103">In Report Builder you can save a report to a report server, SharePoint library, file share on which you have write permission, or your computer.</span></span> <span data-ttu-id="f0410-104">レポートは、レポートを開いた場所に保存することも、別の場所に保存することもできます。また、新しい名前を付けてそれらの場所に保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="f0410-104">You can save a report to the same location from which you opened it, save it to a different location, or save it with a new name to the same or different location.</span></span> <span data-ttu-id="f0410-105">既定では、レポートは、レポートを開いた場所に再保存されます。</span><span class="sxs-lookup"><span data-stu-id="f0410-105">By default, a report is resaved to the location from which you opened it.</span></span> <span data-ttu-id="f0410-106">レポートを保存する場合、実際に保存されるのは、レポート レイアウトを記述したレポート定義です。</span><span class="sxs-lookup"><span data-stu-id="f0410-106">When you save the report, what you are really saving is the report definition, which describes the report layout.</span></span> <span data-ttu-id="f0410-107">データは保存されません。</span><span class="sxs-lookup"><span data-stu-id="f0410-107">You are not saving the data.</span></span> <span data-ttu-id="f0410-108">レポートを実行するたびにレポート データは更新され、ほとんどの場合、前回の実行時とは異なります。</span><span class="sxs-lookup"><span data-stu-id="f0410-108">Every time you run the report, the report data is refreshed and is likely to be different than the previous time you ran the report.</span></span>  
  
 <span data-ttu-id="f0410-109">レポートを他の形式で保存する場合やレポート定義をデータと共に保存する場合は、次の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の機能のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="f0410-109">If you want to save the report to a different format or save the report definition with the data, use one of the following [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features:</span></span>  
  
-   <span data-ttu-id="f0410-110">表示されたレポートをコンマ区切り (CSV) や Excel ブックなどの別のファイル形式にエクスポートし、その形式でレポートを保存する。</span><span class="sxs-lookup"><span data-stu-id="f0410-110">Export a rendered report to a different file format such as comma separated files (CSV) or Excel workbooks and save the report in that format.</span></span> <span data-ttu-id="f0410-111">レポートからデータ フィードを生成し、レポート データを保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="f0410-111">You can also generate data feeds from reports and save the report data.</span></span>  
  
-   <span data-ttu-id="f0410-112">レポート サブスクリプションを作成し、ファイル共有にレポートを配信して保存する。</span><span class="sxs-lookup"><span data-stu-id="f0410-112">Create report subscriptions to deliver and save reports to a file share.</span></span>  
  
-   <span data-ttu-id="f0410-113">レポート履歴を使用して、表示されたレポートのバージョンを履歴コピーとして保存する。</span><span class="sxs-lookup"><span data-stu-id="f0410-113">Use report history to save versions of rendered reports as historical copies.</span></span>  
  
 <span data-ttu-id="f0410-114">レポート サーバー上のレポートを直接表示し、管理する方法の詳細については、msdn.microsoft.com で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブック](https://go.microsoft.com/fwlink/?LinkId=154888)の「[レポートの検索、表示、管理 (レポート ビルダーおよび SSRS)](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)」および「[Reporting Services レポート サーバー (ネイティブ モード)](../report-server/reporting-services-report-server-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0410-114">To learn more about viewing and managing reports directly on the report server, see [Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) and [Reporting Services Report Server &#40;Native Mode&#41;](../report-server/reporting-services-report-server-native-mode.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) on msdn.microsoft.com.</span></span>  
  
##  <a name="saving-report-definitions"></a><a name="SavingReportDefinitions"></a><span data-ttu-id="f0410-115">レポート定義の保存</span><span class="sxs-lookup"><span data-stu-id="f0410-115">Saving Report Definitions</span></span>  
 <span data-ttu-id="f0410-116">レポートは自分のコンピューターに保存することもできますが、レポート サーバーに保存すると多くの利点があります。</span><span class="sxs-lookup"><span data-stu-id="f0410-116">Although you can save reports to your computer, saving reports to a report server offers many advantages.</span></span>  
  
 <span data-ttu-id="f0410-117">レポートをレポート サーバーに保存すると、次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="f0410-117">Saving a report to a report server offers the following advantages:</span></span>  
  
-   <span data-ttu-id="f0410-118">レポートを保存したフォルダーへのアクセス権限を持つ他のユーザーに対して、レポートが利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="f0410-118">Reports become available to others who have permission to access the folder in which you saved the report.</span></span>  
  
-   <span data-ttu-id="f0410-119">レポート マネージャーを使用してレポートの管理や表示を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="f0410-119">Reports can be managed and viewed from Report Manager.</span></span>  
  
-   <span data-ttu-id="f0410-120">データ ソース、画像、サブレポートなどのレポート リソースを 1 か所に保存するのでアクセスが容易です。</span><span class="sxs-lookup"><span data-stu-id="f0410-120">Report resources such as data sources, images, and subreports are stored in one place for easier access.</span></span>  
  
-   <span data-ttu-id="f0410-121">サブスクリプションによって、レポートを他のユーザーに配信できます。</span><span class="sxs-lookup"><span data-stu-id="f0410-121">Reports can be delivered to others by subscriptions.</span></span>  
  
-   <span data-ttu-id="f0410-122">レポートは、レポート サーバー データベースに安全に保存されます。</span><span class="sxs-lookup"><span data-stu-id="f0410-122">Reports are securely stored in the report server database.</span></span>  
  
-   <span data-ttu-id="f0410-123">レポートの実行はログに記録され、パフォーマンスと監査に関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="f0410-123">Report runs can be logged and provide performance and auditing information.</span></span>  
  
 <span data-ttu-id="f0410-124">レポートをレポート サーバーに保存することを、レポートのパブリッシュと呼びます。</span><span class="sxs-lookup"><span data-stu-id="f0410-124">Saving a report to a report server is also known as publishing a report.</span></span> <span data-ttu-id="f0410-125">レポートを保存すると、レポート定義のみが保存されます。</span><span class="sxs-lookup"><span data-stu-id="f0410-125">When you save the report you save the report definition only.</span></span> <span data-ttu-id="f0410-126">レポートを実行するたびにレポート データは更新され、ほとんどの場合、前回の実行時とは異なります。</span><span class="sxs-lookup"><span data-stu-id="f0410-126">Every time you run the report, the report data is refreshed and likely different that the previous time you ran the report.</span></span> <span data-ttu-id="f0410-127">レポート定義をデータと共に保存する場合は、レポート履歴機能を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0410-127">If you want to save the report definition with the data you should use the report history feature.</span></span> <span data-ttu-id="f0410-128">この機能を使用すると、レポートのコピーとそのデータが一緒に保存されます。</span><span class="sxs-lookup"><span data-stu-id="f0410-128">Using this feature, you save a copy of the report with its data.</span></span>  
  

  
##  <a name="exporting-and-saving-reports"></a><a name="ExportingAndSavingReports"></a> <span data-ttu-id="f0410-129">レポートのエクスポートと保存</span><span class="sxs-lookup"><span data-stu-id="f0410-129">Exporting and Saving Reports</span></span>  
 <span data-ttu-id="f0410-130">アーカイブするレポートの数が少ない場合、レポートをエクスポートしてファイルとして保存することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="f0410-130">If you have a small number of reports to archive, consider exporting a report and saving it as a file.</span></span> <span data-ttu-id="f0410-131">レポートをアプリケーション (PDF や Excel など) にエクスポートしたら、そのレポートをファイルとして保存し、ネットワーク上の保護された共有ディレクトリに配置できます。</span><span class="sxs-lookup"><span data-stu-id="f0410-131">After you export a report to an application (such as PDF or Excel), you can save it as a file and place it in a protected shared directory on the network.</span></span> <span data-ttu-id="f0410-132">また、形式にかかわらず、レポート サーバー データベースにレポートのすべてのコピーを保存する場合、リソース アイテムとして保存した PDF または Excel ファイルをアップロードできます。</span><span class="sxs-lookup"><span data-stu-id="f0410-132">Alternatively, you can upload a saved PDF or Excel file as a resource item if you want to keep all copies of a report, regardless of the format, in the report server database.</span></span> <span data-ttu-id="f0410-133">レポートのエクスポートの詳細については、「[レポート &#40;レポートビルダーおよび SSRS&#41;をエクスポート](export-reports-report-builder-and-ssrs.md)する」および「[ファイルまたは &#40;レポートをアップロードするレポートマネージャー ](../reports/upload-a-file-or-report-report-manager.md)&#41;」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0410-133">For more information about exporting a report, see [Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) and [Upload a File or Report &#40;Report Manager&#41;](../reports/upload-a-file-or-report-report-manager.md).</span></span>  
  

  
##  <a name="using-file-share-delivery"></a><a name="UsingFileShareDelivery"></a> <span data-ttu-id="f0410-134">ファイル共有配信の使用</span><span class="sxs-lookup"><span data-stu-id="f0410-134">Using File-Share Delivery</span></span>  
 <span data-ttu-id="f0410-135">アーカイブするレポートが多数ある場合、ファイル システムにレポートを直接配信するサブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="f0410-135">If you have a large number of reports to archive, create a subscription that delivers the report directly to the file system.</span></span> <span data-ttu-id="f0410-136">この方法の場合、レポートごとにサブスクリプションを作成し、レポートを格納するための共有フォルダーを選択して、ファイルの作成日時を決定するスケジュールを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0410-136">For this approach, you must create a subscription for each report, choose a shared folder to store the reports, and define a schedule that determines when the file is created.</span></span> <span data-ttu-id="f0410-137">サブスクリプションを定義したら、レポート サーバーによるレポートの自動実行や、指定したスケジュールによるレポート ファイルのアーカイブへの追加が可能になります。</span><span class="sxs-lookup"><span data-stu-id="f0410-137">Once you define a subscription, the report server can run the report unattended and add report files to the archive using the schedule that you provide.</span></span> <span data-ttu-id="f0410-138">また、定期的にレポートをアーカイブしない場合は、1 回のみ使用するスケジュールを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="f0410-138">You can also create single-use schedules if you want to archive reports on an occasional basis.</span></span> <span data-ttu-id="f0410-139">サブスクリプションとファイル共有配信の詳細については、 [Reporting Services のドキュメント](https://go.microsoft.com/fwlink/?linkid=121312) (SQL Server オンライン ブック) の「Reporting Services でのファイル共有の配信」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0410-139">For more information about subscriptions and file share delivery, see "File Delivery in Reporting Services" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  

  
##  <a name="using-report-history"></a><a name="UsingReportHistory"></a> <span data-ttu-id="f0410-140">レポート履歴の使用</span><span class="sxs-lookup"><span data-stu-id="f0410-140">Using Report History</span></span>  
 <span data-ttu-id="f0410-141">レポート履歴機能を使用して、履歴のコピーを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="f0410-141">You can also use the report history feature to create historical copies.</span></span> <span data-ttu-id="f0410-142">その後、レポート サーバー データベースをバックアップし、今後使用するために安全な場所にバックアップを格納することができます。</span><span class="sxs-lookup"><span data-stu-id="f0410-142">You can then back up the report server database and store the backup in a safe location for future use.</span></span> <span data-ttu-id="f0410-143">すべてのレポート履歴は (レポート、共有データ ソース アイテム、フォルダー、サブスクリプション、および共有スケジュールと共に)、レポート サーバー データベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="f0410-143">All report history (along with reports, shared data source items, folders, subscriptions, and shared schedules) is stored in the report server database.</span></span> <span data-ttu-id="f0410-144">レポート履歴およびメタデータの永続的なコピーを保持するために、バックアップを作成できます。メタデータには、レポートの受信者を示すサブスクリプション情報などがあります。</span><span class="sxs-lookup"><span data-stu-id="f0410-144">You can create a backup to maintain a permanent copy of report history and metadata such as subscription information that indicates the recipients of a report.</span></span> <span data-ttu-id="f0410-145">詳細については、 [Reporting Services のドキュメント](https://go.microsoft.com/fwlink/?linkid=121312) (SQL Server オンライン ブック) の「レポート履歴の管理」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0410-145">For more information, see "Managing Report History" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  

  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="f0410-146">操作方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="f0410-146">How-To Topics</span></span>  
  
-   [<span data-ttu-id="f0410-147">レポートのレポート サーバーへの保存 (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="f0410-147">Save Reports to a Report Server &#40;Report Builder&#41;</span></span>](save-reports-to-a-report-server-report-builder.md)  
  
-   [<span data-ttu-id="f0410-148">SharePoint ライブラリへのレポートの保存 &#40;レポート ビルダー&#41;</span><span class="sxs-lookup"><span data-stu-id="f0410-148">Save a Report to a SharePoint Library &#40;Report Builder&#41;</span></span>](save-a-report-to-a-sharepoint-library-report-builder.md)  
  
-   [<span data-ttu-id="f0410-149">コンピューターにレポートを保存 &#40;レポートビルダー&#41;</span><span class="sxs-lookup"><span data-stu-id="f0410-149">Save Reports to Your Computer &#40;Report Builder&#41;</span></span>](../save-reports-to-your-computer-report-builder.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="f0410-150">参照</span><span class="sxs-lookup"><span data-stu-id="f0410-150">See Also</span></span>  
 <span data-ttu-id="f0410-151">[レポート、レポートパーツ、およびレポート定義 &#40;レポートビルダーと SSRS&#41;](../report-design/reports-report-parts-and-report-definitions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f0410-151">[Reports, Report Parts, and Report Definitions &#40;Report Builder and SSRS&#41;](../report-design/reports-report-parts-and-report-definitions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f0410-152">[インストール、アンインストール、およびレポートビルダーサポート](../install-uninstall-and-report-builder-support.md) </span><span class="sxs-lookup"><span data-stu-id="f0410-152">[Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md) </span></span>  
 <span data-ttu-id="f0410-153">[レポートの検索、表示、および管理 &#40;レポートビルダーと SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f0410-153">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f0410-154">[レポートのエクスポート &#40;レポートビルダーと SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f0410-154">[Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f0410-155">レポートの印刷 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f0410-155">Print Reports &#40;Report Builder and SSRS&#41;</span></span>](print-reports-report-builder-and-ssrs.md)  
  
  
