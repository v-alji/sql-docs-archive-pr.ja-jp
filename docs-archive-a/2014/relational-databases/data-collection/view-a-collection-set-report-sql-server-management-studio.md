---
title: コレクション セット レポートの表示 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.reporthistory.calendar.f1
helpviewer_keywords:
- collection sets [SQL Server], viewing reports
- reports [SQL Server], viewing collection set
ms.assetid: c3b1e791-9aa1-4bba-9622-4954568e1820
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cb8755c67e6c03bb318fdb86d703f6d647d5a3eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643974"
---
# <a name="view-a-collection-set-report-sql-server-management-studio"></a><span data-ttu-id="153c7-102">コレクション セット レポートの表示 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="153c7-102">View a Collection Set Report (SQL Server Management Studio)</span></span>
  <span data-ttu-id="153c7-103">管理データ ウェアハウスを構成した後、コレクション セットのレポートを [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で表示できます。</span><span class="sxs-lookup"><span data-stu-id="153c7-103">After you have configured the management data warehouse, you can view a collection set report in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="153c7-104">セットアップ中にインストールされるシステム データ コレクション セットについては、レポートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="153c7-104">Reports are provided for the System Data collection sets that are installed during Setup.</span></span> <span data-ttu-id="153c7-105">レポートには、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="153c7-105">The reports include the following:</span></span>  
  
-   <span data-ttu-id="153c7-106">ディスク使用量の概要</span><span class="sxs-lookup"><span data-stu-id="153c7-106">Disk Usage Summary</span></span>  
  
-   <span data-ttu-id="153c7-107">クエリ統計の履歴</span><span class="sxs-lookup"><span data-stu-id="153c7-107">Query Statistics History</span></span>  
  
-   <span data-ttu-id="153c7-108">サーバーの利用状況の履歴</span><span class="sxs-lookup"><span data-stu-id="153c7-108">Server Activity History</span></span>  
  
 <span data-ttu-id="153c7-109">この手順では、 **[ディスク使用量]** コレクション セットのレポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="153c7-109">This procedure displays the report for the **Disk Usage** collection set.</span></span> <span data-ttu-id="153c7-110">同様の一般的な手順を使用して、他のシステム データ コレクション セットのレポートを表示できます。</span><span class="sxs-lookup"><span data-stu-id="153c7-110">You can follow the same general procedure to view the reports for the other System Data collection sets.</span></span>  
  
### <a name="to-view-a-collection-set-report"></a><span data-ttu-id="153c7-111">コレクション セットのレポートを表示するには</span><span class="sxs-lookup"><span data-stu-id="153c7-111">To view a collection set report</span></span>  
  
1.  <span data-ttu-id="153c7-112">レポートのテーブルは、収集したデータの初回アップロード時に作成されます。</span><span class="sxs-lookup"><span data-stu-id="153c7-112">The tables for a report are created the first time that the collected data is uploaded.</span></span> <span data-ttu-id="153c7-113">この初回アップロード以前にレポートを表示しようとするとエラーが発生し、レポートは表示されません。</span><span class="sxs-lookup"><span data-stu-id="153c7-113">If you try to view a report before this first upload, an error occurs and no report is displayed.</span></span> <span data-ttu-id="153c7-114">ディスク使用量コレクション セットのデータをアップロードするには、オブジェクト エクスプローラーで、 **[管理]** フォルダー、 **[データ コレクション]** 、 **[システム データ コレクション セット]** の順に展開し、 **[ディスク使用量]** コレクション セットを右クリックして、 **[今すぐ収集してアップロード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="153c7-114">To upload data for the Disk Usage collection set, in Object Explorer, expand the **Management** folder, expand **Data Collection**, expand **System Data Collection Sets**, right-click the **Disk Usage** collection set, and then click **Collect and Upload Now**.</span></span>  
  
2.  <span data-ttu-id="153c7-115">レポートを表示するには、オブジェクト エクスプローラーで、 **[管理]** フォルダーを展開し、 **[データ コレクション]** を右クリックします。次に、 **[レポート]** 、 **[管理データ ウェアハウス]** の順にポイントし、 **[ディスク使用量の概要]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="153c7-115">To view the report, in Object Explorer, expand the **Management** folder, right-click **Data Collection**, point to **Reports**, point to **Management Data Warehouse**, and then click **Disk Usage Summary**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="153c7-116">一部のレポートでは、データ コレクション タイムラインの下にカレンダーのボタンが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="153c7-116">Some reports might display a calendar button under the data collection timeline.</span></span> <span data-ttu-id="153c7-117">このボタンをクリックして、 **データ コレクション レポート カレンダー**にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="153c7-117">Click this button to access the **Data Collection Report Calendar**.</span></span>  
  
#### <a name="data-collection-report-calendar"></a><span data-ttu-id="153c7-118">データ コレクション レポート カレンダー</span><span class="sxs-lookup"><span data-stu-id="153c7-118">Data Collection Report Calendar</span></span>  
 <span data-ttu-id="153c7-119">このダイアログ ボックスを使用すると、レポート対象にするデータの開始日、開始時刻、および実行時間を指定できます。</span><span class="sxs-lookup"><span data-stu-id="153c7-119">Use this dialog box to specify the start date, start time, and duration of the data that you want to report on.</span></span> <span data-ttu-id="153c7-120">たとえば、先週の水曜日の特定の 12 時間におけるサーバーのディスク利用状況をレポート対象とすることができます。</span><span class="sxs-lookup"><span data-stu-id="153c7-120">For example, you may want to report on the disk usage activity of a server for a specific 12-hour period last Wednesday.</span></span>  
  
 <span data-ttu-id="153c7-121">**開始日**</span><span class="sxs-lookup"><span data-stu-id="153c7-121">**Start date**</span></span>  
 <span data-ttu-id="153c7-122">レポート データの開始日を入力するか、カレンダーから開始日を選択します。</span><span class="sxs-lookup"><span data-stu-id="153c7-122">Enter a beginning date for the report data, or select one from the calendar.</span></span>  
  
 <span data-ttu-id="153c7-123">**[開始時刻]**</span><span class="sxs-lookup"><span data-stu-id="153c7-123">**Start time**</span></span>  
 <span data-ttu-id="153c7-124">レポート データの開始時刻を入力するか、矢印をクリックして開始時刻を指定します。</span><span class="sxs-lookup"><span data-stu-id="153c7-124">Enter a beginning time for the report data or specify one by clicking the arrows.</span></span>  
  
 <span data-ttu-id="153c7-125">**Duration**</span><span class="sxs-lookup"><span data-stu-id="153c7-125">**Duration**</span></span>  
 <span data-ttu-id="153c7-126">レポートに含める時間範囲を指定します。</span><span class="sxs-lookup"><span data-stu-id="153c7-126">Specify the time range to include in the report.</span></span> <span data-ttu-id="153c7-127">既定値は 240 分です。</span><span class="sxs-lookup"><span data-stu-id="153c7-127">The default value is 240 minutes.</span></span> <span data-ttu-id="153c7-128">選択できる値は、15 分、60 分、240 分 (4 時間)、720 分 (12 時間)、および 1440 分 (24 時間) です。</span><span class="sxs-lookup"><span data-stu-id="153c7-128">The possible values to select from are 15 minutes, 60 minutes, 240 minutes (4 hours), 720 minutes (12 hours), and 1440 minutes (24 hours).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="153c7-129">参照</span><span class="sxs-lookup"><span data-stu-id="153c7-129">See Also</span></span>  
 <span data-ttu-id="153c7-130">[[データ コレクション]](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="153c7-130">[Data Collection](data-collection.md) </span></span>  
 <span data-ttu-id="153c7-131">[Management Studio におけるカスタム レポート](../../ssms/object/custom-reports-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="153c7-131">[Custom Reports in Management Studio](../../ssms/object/custom-reports-in-management-studio.md) </span></span>  
 [<span data-ttu-id="153c7-132">管理データ ウェアハウスの構成 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="153c7-132">Configure the Management Data Warehouse &#40;SQL Server Management Studio&#41;</span></span>](configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  
