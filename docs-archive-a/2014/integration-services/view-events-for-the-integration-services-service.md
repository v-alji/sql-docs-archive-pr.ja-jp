---
title: Integration Services サービスのイベントを表示する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- events [Integration Services]
- service [Integration Services], events
- Integration Services service, events
ms.assetid: 37e23946-10d1-4116-8568-8fd24067102e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a513c8fc917da2987f3619c8eb9011e1170f7dcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644017"
---
# <a name="view-events-for-the-integration-services-service"></a><span data-ttu-id="cdb24-102">Integration Services サービスのイベントを表示する</span><span class="sxs-lookup"><span data-stu-id="cdb24-102">View Events for the Integration Services Service</span></span>
  <span data-ttu-id="cdb24-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスのイベントを表示できるツールには、次の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="cdb24-103">There are two tools in which you can view events for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service:</span></span>  
  
-   <span data-ttu-id="cdb24-104">**の** [ログ ファイルの表示] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="cdb24-104">The **Log File Viewer** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="cdb24-105">**[ログ ファイルの表示]** ダイアログ ボックスには、ログのエクスポート、フィルター、および検索を行うオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="cdb24-105">The **Log File Viewer** dialog box includes options to export, filter, and search the log.</span></span> <span data-ttu-id="cdb24-106">**[ログ ファイルの表示]** のオプションの詳細については、「 [[ログ ファイルの表示] の F1 ヘルプ](../relational-databases/logs/log-file-viewer-f1-help.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdb24-106">For more information about the options in the **Log File Viewer**, see [Log File Viewer F1 Help](../relational-databases/logs/log-file-viewer-f1-help.md).</span></span>  
  
-   <span data-ttu-id="cdb24-107">Windows イベント ビューアー。</span><span class="sxs-lookup"><span data-stu-id="cdb24-107">The Windows Event Viewer.</span></span>  
  
 <span data-ttu-id="cdb24-108">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスによってログに記録されるイベントの詳細については、「 [Integration Services サービスによってログに記録されるイベント](service/events-logged-by-the-integration-services-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdb24-108">For descriptions of the events logged by the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, see [Events Logged by the Integration Services Service](service/events-logged-by-the-integration-services-service.md).</span></span>  
  
### <a name="to-view-service-events-for-integration-services-in-sql-server-management-studio"></a><span data-ttu-id="cdb24-109">SQL Server Management Studio で Integration Services のサービス イベントを表示するには</span><span class="sxs-lookup"><span data-stu-id="cdb24-109">To view service events for Integration Services in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="cdb24-110">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="cdb24-110">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="cdb24-111">**[ファイル]** メニューの **[オブジェクト エクスプローラーを接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cdb24-111">On the **File** menu, click **Connect Object Explorer**.</span></span>  
  
3.  <span data-ttu-id="cdb24-112">**[サーバーへの接続]** ダイアログ ボックスで [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のサーバーの種類を選択し、接続するサーバー名を選択または参照して、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cdb24-112">In the **Connect to Server** dialog box, select the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server type, select or locate the server to connect to, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="cdb24-113">オブジェクト エクスプローラーで [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] を右クリックして、 **[ログの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cdb24-113">In Object Explorer, right-click [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] and click **View Logs**.</span></span>  
  
5.  <span data-ttu-id="cdb24-114">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のイベントを表示するには、 **[SQL Server Integration Services]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cdb24-114">To view [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] events, select **SQL Server Integration Services**.</span></span> <span data-ttu-id="cdb24-115">**[NT イベント]** オプションは、 **[SQL Server Integration Services]** オプションに応じて、自動的に選択または選択解除されます。</span><span class="sxs-lookup"><span data-stu-id="cdb24-115">The **NT Events** option is automatically selected and cleared with the **SQL Server Integration Services** option.</span></span>  
  
### <a name="to-view-service-events-for-integration-services-in-windows-event-viewer"></a><span data-ttu-id="cdb24-116">Windows イベント ビューアーで Integration Services のサービス イベントを表示するには</span><span class="sxs-lookup"><span data-stu-id="cdb24-116">To view service events for Integration Services in Windows Event Viewer</span></span>  
  
1.  <span data-ttu-id="cdb24-117">**[コントロール パネル]** で、クラシック表示を使用している場合は **[管理ツール]**、カテゴリの表示を使用している場合は **[パフォーマンスとメンテナンス]** をクリックしてから **[管理ツール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cdb24-117">In **Control Panel**, if you are using Classic View, click **Administrative Tools**, or, if you are using Category View, click **Performance and Maintenance** and then click **Administrative Tools**.</span></span>  
  
2.  <span data-ttu-id="cdb24-118">**[イベント ビューアー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cdb24-118">Click **Event Viewer**.</span></span>  
  
3.  <span data-ttu-id="cdb24-119">**[イベント ビューアー]** ダイアログ ボックスで、 **[アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cdb24-119">In the **Event Viewer** dialog box, click **Application**.</span></span>  
  
4.  <span data-ttu-id="cdb24-120">**[アプリケーション]** スナップインから **[ソース]** 列の値が **[SQLISService]** のエントリを探して右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cdb24-120">In the **Application** snap-in, locate an entry in the **Source** column that has the value **SQLISService**, right-click the entry, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="cdb24-121">必要に応じて、上矢印または下矢印をクリックして、前後のイベントを表示します。</span><span class="sxs-lookup"><span data-stu-id="cdb24-121">Optionally, click the up or down arrow to show the previous or next event.</span></span>  
  
6.  <span data-ttu-id="cdb24-122">必要に応じて、[クリップボードにコピー] アイコンをクリックして、イベントの情報をコピーします。</span><span class="sxs-lookup"><span data-stu-id="cdb24-122">Optionally, click the Copy to Clipboard icon to copy the event information.</span></span>  
  
7.  <span data-ttu-id="cdb24-123">イベントのデータをバイトと単語のどちらで表示するか選択します。</span><span class="sxs-lookup"><span data-stu-id="cdb24-123">Choose to display event data using bytes or words.</span></span>  
  
8.  <span data-ttu-id="cdb24-124">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cdb24-124">Click **OK**.</span></span>  
  
9. <span data-ttu-id="cdb24-125">**[ファイル]** メニューの **[終了]** をクリックして、 **[イベント ビューアー]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="cdb24-125">On the **File** menu, click **Exit** to close the **Event Viewer** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdb24-126">参照</span><span class="sxs-lookup"><span data-stu-id="cdb24-126">See Also</span></span>  
 <span data-ttu-id="cdb24-127">[Integration Services サービスを管理する](../../2014/integration-services/manage-the-integration-services-service.md) </span><span class="sxs-lookup"><span data-stu-id="cdb24-127">[Manage the Integration Services Service](../../2014/integration-services/manage-the-integration-services-service.md) </span></span>  
 [<span data-ttu-id="cdb24-128">データ フロー パフォーマンス カウンターのログを追加する</span><span class="sxs-lookup"><span data-stu-id="cdb24-128">Add a Log for Data Flow Performance Counters</span></span>](performance/performance-counters.md)  
  
  
