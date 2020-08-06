---
title: Reporting Services 機能の有効化と無効化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, configuration
- security [Reporting Services], strategies
ms.assetid: b69db02a-43a7-4fdc-ad9b-438d817a7f83
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f56f9984b5b02431db23b782652e5575af557bdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640583"
---
# <a name="turn-reporting-services-features-on-or-off"></a><span data-ttu-id="d5206-102">Reporting Services 機能の有効化と無効化</span><span class="sxs-lookup"><span data-stu-id="d5206-102">Turn Reporting Services Features On or Off</span></span>
  <span data-ttu-id="d5206-103">運用レポート サーバーに対する外部からの攻撃の危険性を低減するためのロックダウン ストラテジには含まれないレポート サーバー機能を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="d5206-103">You can turn off report server features that you do not use as part of a lockdown strategy for reducing the attack surface of a production report server.</span></span> <span data-ttu-id="d5206-104">ほとんどの場合は、複数の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 機能を同時に実行して、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]で提供される機能をすべて利用します。</span><span class="sxs-lookup"><span data-stu-id="d5206-104">In most cases, you will want to run [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features concurrently to use all of the functionality provided in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="d5206-105">ただし、配置モデルによっては、不要な機能を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d5206-105">However, depending on your deployment model, you can disable the features that you do not require.</span></span> <span data-ttu-id="d5206-106">たとえば、すべてのレポート処理をスケジュールに従って実行するように構成すると、バックグラウンド処理だけを有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d5206-106">For example, you can enable only the background processing if all report processing is configured as scheduled operations.</span></span> <span data-ttu-id="d5206-107">同様に、対話型の要求時レポートだけが必要な場合は、レポート サーバー Web サービスだけを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="d5206-107">Similarly, you can run just the Report Server Web service if you only want interactive, on-demand reporting.</span></span>  
  
 <span data-ttu-id="d5206-108">このトピックの手順では、ネイティブ モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 機能を無効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d5206-108">The procedures in this topic show you how to turn off native mode [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features.</span></span> <span data-ttu-id="d5206-109">機能の構成は、 `RsReportServer.config` ファイルを直接編集する、 **のポリシー ベースの管理の** [Reporting Services のセキュリティ構成] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ファセットを使用するなど、さまざまな方法で行うことができます。</span><span class="sxs-lookup"><span data-stu-id="d5206-109">Features can be configured in different ways, such as by editing the `RsReportServer.config` file directly or by using the **Surface Area Configuration for Reporting Services** facet of Policy-Based Management in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="d5206-110">次のリンクを使用して、機能を有効または無効にする方法を説明した手順を探します。</span><span class="sxs-lookup"><span data-stu-id="d5206-110">Use the links to locate the procedure or procedures that explain how to turn a feature on or off:</span></span>  
  
-   [<span data-ttu-id="d5206-111">レポートサーバー Web サービス</span><span class="sxs-lookup"><span data-stu-id="d5206-111">Report Server Web service</span></span>](#RSWebSvc)  
  
-   [<span data-ttu-id="d5206-112">スケジュールされたイベントおよび処理</span><span class="sxs-lookup"><span data-stu-id="d5206-112">Scheduled events and processing</span></span>](#Sched)  
  
-   [<span data-ttu-id="d5206-113">レポート マネージャー</span><span class="sxs-lookup"><span data-stu-id="d5206-113">Report Manager</span></span>](#ReportManager)  
  
-   [<span data-ttu-id="d5206-114">レポート ビルダー</span><span class="sxs-lookup"><span data-stu-id="d5206-114">Report Builder</span></span>](#ReportBuilder)  
  
-   [<span data-ttu-id="d5206-115">レポート データ ソース用 Windows 統合セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d5206-115">Windows Integrated security for report data sources</span></span>](#WinIntSec)  
  
##  <a name="report-server-web-service"></a><a name="RSWebSvc"></a><span data-ttu-id="d5206-116">レポートサーバー Web サービス</span><span class="sxs-lookup"><span data-stu-id="d5206-116">Report Server Web Service</span></span>  
  
#### <a name="to-turn-on-or-off-the-report-server-web-service-by-editing-configuration"></a><span data-ttu-id="d5206-117">構成を編集してレポート サーバー Web サービスを有効または無効にするには</span><span class="sxs-lookup"><span data-stu-id="d5206-117">To turn on or off the Report Server Web service by editing configuration</span></span>  
  
1.  <span data-ttu-id="d5206-118">テキスト エディターで `RsReportServer.config` ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="d5206-118">Open the `RsReportServer.config` file in a text editor.</span></span> <span data-ttu-id="d5206-119">詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「[Reporting Services の構成ファイル &#40;RSreportserver.config&#41; の変更](modify-a-reporting-services-configuration-file-rsreportserver-config.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5206-119">For more information, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
2.  <span data-ttu-id="d5206-120">レポート サーバー Web サービスを有効にするには、`IsWebServiceEnabled` を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="d5206-120">To turn on the Report Server Web service, set `IsWebServiceEnabled` to `true`:</span></span>  
  
    ```  
    <IsWebServiceEnabled>true</IsWebServiceEnabled>  
    ```  
  
3.  <span data-ttu-id="d5206-121">レポート サーバー Web サービスを無効にするには、`IsWebServiceEnabled` を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="d5206-121">To turn off the Report Server Web service, set `IsWebServiceEnabled` to `false`:</span></span>  
  
    ```  
    <IsWebServiceEnabled>false</IsWebServiceEnabled>  
    ```  
  
4.  <span data-ttu-id="d5206-122">変更を保存し、ファイルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="d5206-122">Save your changes and then close the file.</span></span>  
  
#### <a name="to-turn-on-or-off-the-report-server-web-service-by-using-sql-server-management-studio"></a><span data-ttu-id="d5206-123">SQL Server Management Studio を使用してレポート サーバー Web サービスを有効または無効にするには</span><span class="sxs-lookup"><span data-stu-id="d5206-123">To turn on or off the Report Server Web service by using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="d5206-124">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を開き、構成する [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d5206-124">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span>  
  
2.  <span data-ttu-id="d5206-125">オブジェクト エクスプローラーで [ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ] ノードを右クリックし、 **[ポリシー]** をポイントして、 **[ファセット]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d5206-125">In Object Explorer, right-click the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] node, point to **Policies**, and click **Facets**.</span></span>  
  
3.  <span data-ttu-id="d5206-126">**[ファセット]** ボックスの一覧で、 **[Reporting Services のセキュリティ構成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d5206-126">In the **Facet** list, select **Surface Area Configuration for Reporting Services**.</span></span>  
  
4.  <span data-ttu-id="d5206-127">**[ファセットのプロパティ]** で次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="d5206-127">Under **Facet Properties**:</span></span>  
  
    -   <span data-ttu-id="d5206-128">レポートサーバー Web サービスを有効にするには、 **Webserviceandhttpaccessenabled**をに設定 `True` します。</span><span class="sxs-lookup"><span data-stu-id="d5206-128">To turn on the Report Server Web service, set **WebServiceAndHTTPAccessEnabled** to `True`.</span></span>  
  
    -   <span data-ttu-id="d5206-129">レポートサーバー Web サービスを無効にするには、 **Webserviceandhttpaccessenabled**をに設定 `False` します。</span><span class="sxs-lookup"><span data-stu-id="d5206-129">To turn off the Report Server Web service, set **WebServiceAndHTTPAccessEnabled** to `False`.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="scheduled-events-and-delivery"></a><a name="Sched"></a> <span data-ttu-id="d5206-130">定期的なイベントおよび配信</span><span class="sxs-lookup"><span data-stu-id="d5206-130">Scheduled Events and Delivery</span></span>  
  
#### <a name="to-turn-on-or-off-scheduled-events-and-delivery-by-editing-configuration"></a><span data-ttu-id="d5206-131">構成を編集して定期的なイベントおよび配信を有効または無効にするには</span><span class="sxs-lookup"><span data-stu-id="d5206-131">To turn on or off scheduled events and delivery by editing configuration</span></span>  
  
1.  <span data-ttu-id="d5206-132">テキスト エディターで RsReportServer.config ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="d5206-132">Open the RsReportServer.config file in a text editor.</span></span> <span data-ttu-id="d5206-133">詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「[Reporting Services の構成ファイル &#40;RSreportserver.config&#41; の変更](modify-a-reporting-services-configuration-file-rsreportserver-config.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5206-133">For more information, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
2.  <span data-ttu-id="d5206-134">スケジュールされたレポート処理および配信を有効にするには、`IsSchedulingService`、`IsNotificationService`、および `IsEventService` を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="d5206-134">To turn on scheduled report processing and delivery, set `IsSchedulingService`, `IsNotificationService`, and `IsEventService` to `true`:</span></span>  
  
    ```  
    <IsSchedulingService>true</IsSchedulingService>  
    <IsNotificationService>true</IsNotificationService>  
    <IsEventService>true</IsEventService>  
    ```  
  
3.  <span data-ttu-id="d5206-135">スケジュールされたレポート処理および配信を無効にするには、`IsSchedulingService`、`IsNotificationService`、および `IsEventService` を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="d5206-135">To turn off scheduled report processing and delivery, set `IsSchedulingService`, `IsNotificationService`, and `IsEventService` to `false`:</span></span>  
  
    ```  
    <IsSchedulingService>false</IsSchedulingService>  
    <IsNotificationService>false</IsNotificationService>  
    <IsEventService>false</IsEventService>  
    ```  
  
4.  <span data-ttu-id="d5206-136">変更を保存し、ファイルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="d5206-136">Save your changes and then close the file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d5206-137">バックグラウンド処理によって、サーバー処理に必要なデータベース メンテナンス機能が提供されているため、バックグラウンド処理を完全に無効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d5206-137">You cannot turn off background processing completely because it provides database maintenance functionality that is required for server operations.</span></span>  
  
#### <a name="to-turn-on-or-off-scheduled-events-and-delivery-by-using-sql-server-management-studio"></a><span data-ttu-id="d5206-138">SQL Server Management Studio を使用して定期的なイベントおよび配信を有効または無効にするには</span><span class="sxs-lookup"><span data-stu-id="d5206-138">To turn on or off scheduled events and delivery by using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="d5206-139">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を開き、構成する [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d5206-139">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span>  
  
2.  <span data-ttu-id="d5206-140">オブジェクト エクスプローラーで [ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ] ノードを右クリックし、 **[ポリシー]** をポイントして、 **[ファセット]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d5206-140">In Object Explorer, right-click the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] node, point to **Policies**, and click **Facets**.</span></span>  
  
3.  <span data-ttu-id="d5206-141">**[ファセット]** ボックスの一覧で、 **[Reporting Services のセキュリティ構成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d5206-141">In the **Facet** list, select **Surface Area Configuration for Reporting Services**.</span></span>  
  
4.  <span data-ttu-id="d5206-142">**[ファセットのプロパティ]** で次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="d5206-142">Under **Facet Properties**:</span></span>  
  
    -   <span data-ttu-id="d5206-143">スケジュールされたイベントおよび配信を有効にするには、 **ScheduleEventsAndReportDeliveryEnabled**をに設定 `True` します。</span><span class="sxs-lookup"><span data-stu-id="d5206-143">To turn on scheduled events and delivery, set **ScheduleEventsAndReportDeliveryEnabled** to `True`.</span></span>  
  
    -   <span data-ttu-id="d5206-144">スケジュールされたイベントおよび配信をオフにするには、 **ScheduleEventsAndReportDeliveryEnabled**をに設定 `False` します。</span><span class="sxs-lookup"><span data-stu-id="d5206-144">To turn off scheduled events and delivery, set **ScheduleEventsAndReportDeliveryEnabled** to `False`.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  <span data-ttu-id="d5206-145">バックグラウンド処理によって、サーバー処理に必要なデータベース メンテナンス機能が提供されているため、バックグラウンド処理を完全に無効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d5206-145">You cannot turn off background processing completely because it provides database maintenance functionality that is required for server operations.</span></span>  
  
##  <a name="report-manager"></a><a name="ReportManager"></a><span data-ttu-id="d5206-146">レポート マネージャー</span><span class="sxs-lookup"><span data-stu-id="d5206-146">Report Manager</span></span>  
  
#### <a name="to-turn-on-or-off-report-manager-by-editing-configuration"></a><span data-ttu-id="d5206-147">構成を編集してレポート マネージャーを有効または無効にするには</span><span class="sxs-lookup"><span data-stu-id="d5206-147">To turn on or off Report Manager by editing configuration</span></span>  
  
1.  <span data-ttu-id="d5206-148">テキスト エディターで RsReportServer.config ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="d5206-148">Open the RsReportServer.config file in a text editor.</span></span> <span data-ttu-id="d5206-149">手順については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「[Reporting Services の構成ファイル &#40;RSreportserver.config&#41; の変更](modify-a-reporting-services-configuration-file-rsreportserver-config.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d5206-149">For instructions, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
2.  <span data-ttu-id="d5206-150">レポート マネージャーを有効にするには、`IsReportManagerEnabled` を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="d5206-150">To turn on Report Manager, set `IsReportManagerEnabled` to `true`:</span></span>  
  
    ```  
    <IsReportManagerEnabled>true</IsReportManagerEnabled>  
    ```  
  
3.  <span data-ttu-id="d5206-151">レポート マネージャーを無効にするには、`IsReportManagerEnabled` を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="d5206-151">To turn off Report Manager, set `IsReportManagerEnabled` to `false`:</span></span>  
  
    ```  
    <IsReportManagerEnabled>false</IsReportManagerEnabled>  
    ```  
  
4.  <span data-ttu-id="d5206-152">変更を保存し、ファイルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="d5206-152">Save your changes and then close the file.</span></span>  
  
#### <a name="to-turn-on-or-off-report-manager-by-using-sql-server-management-studio"></a><span data-ttu-id="d5206-153">SQL Server Management Studio を使用してレポート マネージャーを有効または無効にするには</span><span class="sxs-lookup"><span data-stu-id="d5206-153">To turn on or off Report Manager by using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="d5206-154">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を開き、構成する [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d5206-154">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span>  
  
2.  <span data-ttu-id="d5206-155">**オブジェクトエクスプローラー**で、ノードを右クリックして [ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **ポリシー**] をポイントし、[**ファセット**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d5206-155">In **Object Explorer**, right-click the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] node, point to **Policies**, and click **Facets**.</span></span>  
  
3.  <span data-ttu-id="d5206-156">**[ファセット]** ボックスの一覧で、 **[Reporting Services のセキュリティ構成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d5206-156">In the **Facet** list, select **Surface Area Configuration for Reporting Services**.</span></span>  
  
4.  <span data-ttu-id="d5206-157">**[ファセットのプロパティ]** で次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="d5206-157">Under **Facet Properties**:</span></span>  
  
    -   <span data-ttu-id="d5206-158">レポートマネージャーをオンにするには、 **Reportmanagerenabled**をに設定 `True` します。</span><span class="sxs-lookup"><span data-stu-id="d5206-158">To turn on Report Manager, set **ReportManagerEnabled** to `True`.</span></span>  
  
    -   <span data-ttu-id="d5206-159">レポートマネージャーを無効にするには、 **Reportmanagerenabled**をに設定 `False` します。</span><span class="sxs-lookup"><span data-stu-id="d5206-159">To turn off Report Manager, set **ReportManagerEnabled** to `False`.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="report-builder"></a><a name="ReportBuilder"></a> <span data-ttu-id="d5206-160">レポート ビルダー</span><span class="sxs-lookup"><span data-stu-id="d5206-160">Report Builder</span></span>  
  
#### <a name="to-turn-on-or-off-report-builder-by-using-sql-server-management-studio"></a><span data-ttu-id="d5206-161">SQL Server Management Studio を使用してレポート ビルダーを有効または無効にするには</span><span class="sxs-lookup"><span data-stu-id="d5206-161">To turn on or off Report Builder by using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="d5206-162">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を開き、構成する [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d5206-162">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span>  
  
2.  <span data-ttu-id="d5206-163">オブジェクト エクスプローラーで [ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ] ノードを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d5206-163">In Object Explorer, right-click the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] node, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="d5206-164">**[サーバーのプロパティ]** ダイアログ ボックスの **[ページの選択]** で **[セキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d5206-164">In the **Server Properties** dialog box, under **Select a page**, click **Security**.</span></span>  
  
    -   <span data-ttu-id="d5206-165">レポート ビルダーを有効にするには、 **[アドホック レポート実行を有効にする]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="d5206-165">To turn on Report Builder, select the **Enable ad hoc report executions** option.</span></span>  
  
    -   <span data-ttu-id="d5206-166">レポート ビルダーを無効にするには、 **[アドホック レポート実行を有効にする]** オプションを選択解除します。</span><span class="sxs-lookup"><span data-stu-id="d5206-166">To turn off Report Builder, unselect the **Enable ad hoc report executions** option.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="windows-integrated-security"></a><a name="WinIntSec"></a> <span data-ttu-id="d5206-167">Windows 統合セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d5206-167">Windows Integrated Security</span></span>  
  
#### <a name="to-turn-on-or-off-windows-integrated-security-by-using-sql-server-management-studio"></a><span data-ttu-id="d5206-168">SQL Server Management Studio を使用して Windows 統合セキュリティを有効または無効にするには</span><span class="sxs-lookup"><span data-stu-id="d5206-168">To turn on or off Windows Integrated security by using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="d5206-169">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を開き、構成する [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d5206-169">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span>  
  
2.  <span data-ttu-id="d5206-170">オブジェクト エクスプローラーで [ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ] ノードを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d5206-170">In Object Explorer, right-click the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] node, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="d5206-171">**[サーバーのプロパティ]** ダイアログ ボックスの **[ページの選択]** で **[セキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d5206-171">In the **Server Properties** dialog box, under **Select a page**, click **Security**.</span></span>  
  
    -   <span data-ttu-id="d5206-172">Windows 統合セキュリティを有効にするには、 **[レポート データ ソースで Windows 統合セキュリティを有効にする]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="d5206-172">To turn on Windows Integrated security, select the **Enable Windows Integrated security for report data sources** option.</span></span>  
  
    -   <span data-ttu-id="d5206-173">Windows 統合セキュリティを無効にするには、 **[レポート データ ソースで Windows 統合セキュリティを有効にする]** オプションを選択解除します。</span><span class="sxs-lookup"><span data-stu-id="d5206-173">To turn off Windows integrated security, unselect the **Enable Windows Integrated security for report data sources** option.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d5206-174">参照</span><span class="sxs-lookup"><span data-stu-id="d5206-174">See Also</span></span>  
 [<span data-ttu-id="d5206-175">Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;</span><span class="sxs-lookup"><span data-stu-id="d5206-175">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
