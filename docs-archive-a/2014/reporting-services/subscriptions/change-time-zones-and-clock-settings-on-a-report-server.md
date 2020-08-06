---
title: レポート サーバーでタイム ゾーンと時計の設定を変更する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- time zones [Reporting Services]
- clocks [Reporting Services]
- schedules [Reporting Services], clock settings
- schedules [Reporting Services], time zones
ms.assetid: 69a19468-baa1-40f6-b158-8afdab0f8968
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 566e421cd120010ea32f6936853e4319ec2efa11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739133"
---
# <a name="change-time-zones-and-clock-settings-on-a-report-server"></a><span data-ttu-id="6f88f-102">レポート サーバーでタイム ゾーンと時計の設定を変更する</span><span class="sxs-lookup"><span data-stu-id="6f88f-102">Change Time Zones and Clock Settings on a Report Server</span></span>
  <span data-ttu-id="6f88f-103">レポート サーバーでは、インストールされているコンピューターのローカル時刻が常に使用されます。</span><span class="sxs-lookup"><span data-stu-id="6f88f-103">A report server always uses the local time of the computer on which it is installed.</span></span> <span data-ttu-id="6f88f-104">異なるタイム ゾーンを使用するように構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="6f88f-104">You cannot configure it to use a different time zone.</span></span> <span data-ttu-id="6f88f-105">クライアント アプリケーションと、参照先のレポート サーバーのタイム ゾーンが異なる場合、スケジュールが設定された操作は、レポート サーバーのタイム ゾーンを使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="6f88f-105">If a client application points to a report server in a different time zone, the report server time zone is used to execute a scheduled operation.</span></span> <span data-ttu-id="6f88f-106">レポート マネージャーと SharePoint 管理ページの各スケジュール ページには、スケジュールが設定された操作が行われる正確な日時がわかるよう、タイム ゾーンが明記されます。</span><span class="sxs-lookup"><span data-stu-id="6f88f-106">In Report Manager and SharePoint management pages, the time zone is indicated on each scheduling page so that you know exactly when a scheduled operation will occur.</span></span> <span data-ttu-id="6f88f-107">たとえば、カスタム スケジュールを作成するためのページには、"時間は (UTC-08:00) 太平洋標準時 (米国およびカナダ) で表されます" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f88f-107">For example, the page for creating custom schedules will note "Times are expressed in (UTC-08:00) Pacific time (US and Canada)."</span></span>  
  
## <a name="changing-the-time-zone-native-mode"></a><span data-ttu-id="6f88f-108">タイム ゾーンの変更 (ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="6f88f-108">Changing the Time Zone (Native Mode)</span></span>  
 <span data-ttu-id="6f88f-109">レポート サーバーをホストするコンピューターのタイム ゾーンを変更した場合、変更を有効にするにはレポート サーバー サービスを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f88f-109">If you change the time zone on a computer hosting a report server, you must restart the Report Server service in order for the time zone change to take effect.</span></span>  
  
 <span data-ttu-id="6f88f-110">既存のレポート履歴スナップショットのタイムスタンプ値は、新しいタイム ゾーンの設定に同期されます。</span><span class="sxs-lookup"><span data-stu-id="6f88f-110">Timestamp values of existing report history snapshots are synchronized to the new time zone setting.</span></span> <span data-ttu-id="6f88f-111">午前 9 時にレポート履歴スナップショットを生成し、タイム ゾーンを 1 つ前のタイム ゾーンに再設定した場合、生成したスナップショットのタイムスタンプは午前 9 時から</span><span class="sxs-lookup"><span data-stu-id="6f88f-111">If you generated a report history snapshot at 9:00 A.M., and then reset the time zone ahead one time zone, the timestamp on the generated snapshot will change from 9:00 A.M.</span></span> <span data-ttu-id="6f88f-112">午前 10 時に変わります。</span><span class="sxs-lookup"><span data-stu-id="6f88f-112">to 10:00 A.M.</span></span>  
  
 <span data-ttu-id="6f88f-113">スケジュールの既存の設定は残りますが、新しいタイム ゾーンにスライドされます。</span><span class="sxs-lookup"><span data-stu-id="6f88f-113">Schedules retain existing settings, except that they are mapped to the new time zone.</span></span> <span data-ttu-id="6f88f-114">たとえば、太平洋標準時の午前 2 時に</span><span class="sxs-lookup"><span data-stu-id="6f88f-114">For example, if a schedule runs at 2:00 A.M.</span></span> <span data-ttu-id="6f88f-115">スケジュールを実行している場合に、タイム ゾーンをオーストラリア東部標準時に変更すると、スケジュールはオーストラリア東部標準時の</span><span class="sxs-lookup"><span data-stu-id="6f88f-115">Pacific Standard Time and you change the time zone to East Australia Standard Time, the schedule runs at 2:00 A.M.</span></span> <span data-ttu-id="6f88f-116">午前 2 時に実行されます。</span><span class="sxs-lookup"><span data-stu-id="6f88f-116">East Australia Standard Time.</span></span>  
  
 <span data-ttu-id="6f88f-117">プロパティのタイムスタンプ値 (フォルダーまたはリンク レポート アイテムの作成日時など) は、新しいタイム ゾーンの設定に同期されません。</span><span class="sxs-lookup"><span data-stu-id="6f88f-117">Property timestamp values (for example, the time at which a folder or linked report item is created) are not synchronized to a new time zone setting.</span></span> <span data-ttu-id="6f88f-118">6 月 25 日の午前 9 時にアイテムを作成し、タイム ゾーンまたは時計の設定を変更しても、タイムスタンプは 6 月 25 日の午前 9 時のままです。</span><span class="sxs-lookup"><span data-stu-id="6f88f-118">If you create an item on June 25 at 9:00 A.M., and then reset the time zone or clock, the timestamp remains June 25 at 9:00 A.M.</span></span>  
  
## <a name="changing-the-time-zone-sharepoint-mode"></a><span data-ttu-id="6f88f-119">タイム ゾーンの変更 (SharePoint モード)</span><span class="sxs-lookup"><span data-stu-id="6f88f-119">Changing the Time Zone (SharePoint Mode)</span></span>  
 <span data-ttu-id="6f88f-120">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードのタイム ゾーンの構成は、SharePoint の地域設定の一部として管理されます。</span><span class="sxs-lookup"><span data-stu-id="6f88f-120">The time zone configuration for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode is managed as part of the SharePoint regional settings.</span></span> <span data-ttu-id="6f88f-121">詳細については、「[SharePoint Server 2010 SP1 の説明」(https://technet.microsoft.com/library/cc824907.aspx)](https://technet.microsoft.com/library/cc824907.aspx) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f88f-121">For more information, see [Regional settings (SharePoint Server 2010 (https://technet.microsoft.com/library/cc824907.aspx)](https://technet.microsoft.com/library/cc824907.aspx).</span></span>  
  
## <a name="changing-the-clock-settings"></a><span data-ttu-id="6f88f-122">時計の設定の変更</span><span class="sxs-lookup"><span data-stu-id="6f88f-122">Changing the Clock Settings</span></span>  
 <span data-ttu-id="6f88f-123">内蔵時計を変更しても、既存のタイムスタンプ値に影響はありません。たとえば、時計を 1 時間進めても、レポート履歴スナップショットのタイムスタンプは変わりません。</span><span class="sxs-lookup"><span data-stu-id="6f88f-123">Changing the computer clock has no effect on existing timestamp values (for example, if you move the clock forward an hour, the timestamps of report history snapshots do not change).</span></span> <span data-ttu-id="6f88f-124">スケジュールおよび配信のプロセッサの設定が新しく切り替わるまでに、10 秒の遅延が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="6f88f-124">There may be a delay of 10 seconds before the Scheduling and Delivery Processor uses the new setting.</span></span> <span data-ttu-id="6f88f-125">構成ファイルのポーリング間隔の設定を変更した場合、実際の遅延時間が異なることがあります。</span><span class="sxs-lookup"><span data-stu-id="6f88f-125">The actual delay may vary if you modified polling interval settings in the configuration files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f88f-126">参照</span><span class="sxs-lookup"><span data-stu-id="6f88f-126">See Also</span></span>  
 <span data-ttu-id="6f88f-127">[Start and Stop the Report Server Service](../report-server/start-and-stop-the-report-server-service.md) </span><span class="sxs-lookup"><span data-stu-id="6f88f-127">[Start and Stop the Report Server Service](../report-server/start-and-stop-the-report-server-service.md) </span></span>  
 [<span data-ttu-id="6f88f-128">スケジュール</span><span class="sxs-lookup"><span data-stu-id="6f88f-128">Schedules</span></span>](schedules.md)  
  
  
