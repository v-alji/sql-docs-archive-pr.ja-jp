---
title: '[スケジュールのプロパティ] ([全般] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.scheduleproperties.general.f1
ms.assetid: 20e43966-6caf-4972-a2e2-0d9131ac8f51
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a61837cd977526021be948d8c74a93eba6506e67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634824"
---
# <a name="schedule-properties-general-page"></a><span data-ttu-id="23a58-102">[スケジュールのプロパティ]\([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="23a58-102">Schedule Properties (General Page)</span></span>
  <span data-ttu-id="23a58-103">このページを使用すると、共有スケジュールを表示したり変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="23a58-103">Use this page to view or modify a shared schedule.</span></span> <span data-ttu-id="23a58-104">共有スケジュールは、レポート固有のスケジュールやサブスクリプション固有のスケジュールの代わりに使用できます。</span><span class="sxs-lookup"><span data-stu-id="23a58-104">Shared schedules can be used in place of report-specific or subscription-specific schedules.</span></span> <span data-ttu-id="23a58-105">スケジュールに対する変更は、スケジュールを保存した後に適用されます。</span><span class="sxs-lookup"><span data-stu-id="23a58-105">Changes to the schedule are applied after you save the schedule.</span></span> <span data-ttu-id="23a58-106">スケジュールを編集しても、現在実行中のジョブには影響しません。</span><span class="sxs-lookup"><span data-stu-id="23a58-106">Editing a schedule has no effect on jobs that are currently in progress.</span></span> <span data-ttu-id="23a58-107">使用中のスケジュールを編集すると、そのスケジュールからトリガーされた現在処理中のレポートおよびサブスクリプションはすべて終了できるようになります。</span><span class="sxs-lookup"><span data-stu-id="23a58-107">If you edit a schedule while it is being used, all currently processing reports and subscriptions triggered from that schedule will be allowed to finish.</span></span>  
  
 <span data-ttu-id="23a58-108">1 つのスケジュールの中で、複数の頻度を組み合わせて使用することができない場合があります。</span><span class="sxs-lookup"><span data-stu-id="23a58-108">Not all frequency combinations can be supported in a single schedule.</span></span> <span data-ttu-id="23a58-109">たとえば、毎週金曜日の正午と</span><span class="sxs-lookup"><span data-stu-id="23a58-109">For example, if you want to run a report at 12:00 P.M.</span></span> <span data-ttu-id="23a58-110">午後 4 時 00 分まで</span><span class="sxs-lookup"><span data-stu-id="23a58-110">and 4:00 P.M.</span></span> <span data-ttu-id="23a58-111">レポートを実行する場合、実行日を金曜日に指定した日単位のスケジュールを 2 つ作成し、1 つは開始時刻を正午に、</span><span class="sxs-lookup"><span data-stu-id="23a58-111">every Friday, you must create two daily schedules that specify a Friday run date, one with a start time of 12:00 P.M.</span></span> <span data-ttu-id="23a58-112">もう 1 つは開始時刻を午後 4 時に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="23a58-112">and another with a start time of 4:00 P.M.</span></span>  
  
 <span data-ttu-id="23a58-113">スケジュールは、そのスケジュールをホストおよび処理するレポート サーバーのローカル時間に基づいて処理されます。</span><span class="sxs-lookup"><span data-stu-id="23a58-113">Schedule processing is based on the local time of the report server that hosts and processes the schedule.</span></span>  
  
 <span data-ttu-id="23a58-114">このページを開くには、を起動し、レポートサーバーに接続します。次に、[ [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **共有スケジュール**] フォルダーを開き、共有スケジュールを右クリックして、[**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="23a58-114">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, open the **Shared Schedules** folder, right-click a shared schedule, and select **Properties**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="23a58-115">この機能は、すべてのエディションの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用できるわけではなく、この機能がないエディションを実行している場合は、このページが表示されません。</span><span class="sxs-lookup"><span data-stu-id="23a58-115">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and this page does not appear when you are running an edition which does not have this feature.</span></span> <span data-ttu-id="23a58-116">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2012 の各エディションがサポートする機能](https://go.microsoft.com/fwlink/?linkid=232473)」 (を参照してください https://go.microsoft.com/fwlink/?linkid=232473) 。</span><span class="sxs-lookup"><span data-stu-id="23a58-116">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
## <a name="options"></a><span data-ttu-id="23a58-117">Options</span><span class="sxs-lookup"><span data-stu-id="23a58-117">Options</span></span>  
 <span data-ttu-id="23a58-118">**名前**</span><span class="sxs-lookup"><span data-stu-id="23a58-118">**Name**</span></span>  
 <span data-ttu-id="23a58-119">共有スケジュールの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="23a58-119">Specifies the name for the shared schedule.</span></span>  
  
 <span data-ttu-id="23a58-120">**[このスケジュールの実行開始日]**</span><span class="sxs-lookup"><span data-stu-id="23a58-120">**Begin running this schedule on**</span></span>  
 <span data-ttu-id="23a58-121">このスケジュールの開始日を指定します。</span><span class="sxs-lookup"><span data-stu-id="23a58-121">Specifies a start date for this schedule.</span></span>  
  
 <span data-ttu-id="23a58-122">**[このスケジュールの終了日]**</span><span class="sxs-lookup"><span data-stu-id="23a58-122">**Stop this schedule on**</span></span>  
 <span data-ttu-id="23a58-123">このスケジュールの終了日を指定します。</span><span class="sxs-lookup"><span data-stu-id="23a58-123">Specifies an expiration date for this schedule.</span></span>  
  
 <span data-ttu-id="23a58-124">**Type**</span><span class="sxs-lookup"><span data-stu-id="23a58-124">**Type**</span></span>  
 <span data-ttu-id="23a58-125">定期的なパターンが主に時間、日、週、月のどの単位に基づくか、または一度だけ実行するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="23a58-125">Specifies whether the recurrence pattern is based primarily on hours, days, weeks, months, or only runs once.</span></span>  
  
 <span data-ttu-id="23a58-126">**[時間]\([定期的なパターン])**</span><span class="sxs-lookup"><span data-stu-id="23a58-126">**Hour (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="23a58-127">スケジュール設定した操作を一定時間ごとに実行する (たとえば 6 時間ごとにレポートを実行する) ためのオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="23a58-127">Specifies options for running a scheduled operation in intervals of an hour (for example, to run a report every 6 hours).</span></span> <span data-ttu-id="23a58-128">間隔は時間と分で指定できます。</span><span class="sxs-lookup"><span data-stu-id="23a58-128">You can specify the interval in hours and minutes.</span></span>  
  
 <span data-ttu-id="23a58-129">**[日] ([定期的なパターン])**</span><span class="sxs-lookup"><span data-stu-id="23a58-129">**Day (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="23a58-130">スケジュール設定した操作を数日間隔で実行する (たとえば 2 日ごとにレポートを実行する) ためのオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="23a58-130">Specifies options for running a scheduled operation in intervals of days (for example, to run a report every 2 days).</span></span> <span data-ttu-id="23a58-131">間隔は日数で指定し、スケジュールを実行する時と分を指定できます。</span><span class="sxs-lookup"><span data-stu-id="23a58-131">You can specify the interval in days and at the hour and minute you want the schedule to run.</span></span>  
  
 <span data-ttu-id="23a58-132">**[週] ([定期的なパターン])**</span><span class="sxs-lookup"><span data-stu-id="23a58-132">**Week (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="23a58-133">スケジュール設定した操作を毎週実行するか、繰り返しのパターンが週単位 (たとえば隔週でレポートを実行する) の場合のオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="23a58-133">Specifies options for running a scheduled operation in intervals of a week or when the pattern that you want to repeat is based on weeks (for example, to run a report every other week).</span></span> <span data-ttu-id="23a58-134">週間スケジュールについて、スケジュールを実行する日、時、分を指定できます。</span><span class="sxs-lookup"><span data-stu-id="23a58-134">You can specify a weekly schedule to the day, hour, and minute that you want the schedule to run.</span></span>  
  
 <span data-ttu-id="23a58-135">**[月]\([定期的なパターン])**</span><span class="sxs-lookup"><span data-stu-id="23a58-135">**Month (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="23a58-136">スケジュール設定した操作を毎月実行するか、繰り返しのパターンが月単位の場合のオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="23a58-136">Specifies options for running a scheduled operation in intervals of a month or when the pattern that you want to repeat is based on months.</span></span> <span data-ttu-id="23a58-137">月間スケジュールについて、スケジュールを実行する日、時、分を指定できます。</span><span class="sxs-lookup"><span data-stu-id="23a58-137">You can specify a monthly schedule to the day, hour, and minute that you want the schedule to run.</span></span> <span data-ttu-id="23a58-138">スケジュールでは特定の月を指定しなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="23a58-138">You can omit specific months from the schedule.</span></span>  
  
 <span data-ttu-id="23a58-139">**1 度**</span><span class="sxs-lookup"><span data-stu-id="23a58-139">**Once**</span></span>  
 <span data-ttu-id="23a58-140">特定の日時に 1 回のみスケジュールを実行するように指定します。</span><span class="sxs-lookup"><span data-stu-id="23a58-140">Specifies a schedule that runs only once, on a specific date and time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23a58-141">参照</span><span class="sxs-lookup"><span data-stu-id="23a58-141">See Also</span></span>  
 <span data-ttu-id="23a58-142">[Management Studio F1 ヘルプのレポートサーバー](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="23a58-142">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="23a58-143">[Management Studio でレポートサーバーに接続する](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="23a58-143">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="23a58-144">[Create, Modify, and Delete Schedules](../subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="23a58-144">[Create, Modify, and Delete Schedules](../subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 [<span data-ttu-id="23a58-145">スケジュール</span><span class="sxs-lookup"><span data-stu-id="23a58-145">Schedules</span></span>](../subscriptions/schedules.md)  
  
  
