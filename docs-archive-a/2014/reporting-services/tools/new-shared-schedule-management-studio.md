---
title: '[新しい共有スケジュール] (Management Studio) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.newschedule.f1
ms.assetid: b2c69586-d98e-4933-827d-f5e6c15c5203
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6afd406730f815d3ab61e59cdebd21d564daa74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634254"
---
# <a name="new-shared-schedule-management-studio"></a><span data-ttu-id="9ae87-102">[新しい共有スケジュール] (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9ae87-102">New Shared Schedule (Management Studio)</span></span>
  <span data-ttu-id="9ae87-103">このページを使用すると、パブリッシュされたレポートおよびサブスクリプションを実行するための共有スケジュールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="9ae87-103">Use this page to create a shared schedule to run published reports and subscriptions.</span></span> <span data-ttu-id="9ae87-104">共有スケジュールは、レポート固有のスケジュールやサブスクリプション固有のスケジュールの代わりに使用できます。</span><span class="sxs-lookup"><span data-stu-id="9ae87-104">Shared schedules can be used in place of report-specific or subscription-specific schedules.</span></span> <span data-ttu-id="9ae87-105">集中管理されるスケジュール情報と、スケジュールされた操作を一時停止して再開する機能は、アイテム固有のスケジュールと共有スケジュールを区別する 2 つの重要な機能です。</span><span class="sxs-lookup"><span data-stu-id="9ae87-105">Centralized schedule information and the ability to pause and resume scheduled operations are two key features that distinguish shared schedules from item-specific schedules.</span></span>  
  
 <span data-ttu-id="9ae87-106">1 つのスケジュールの中で、複数の頻度を組み合わせて使用することができない場合があります。</span><span class="sxs-lookup"><span data-stu-id="9ae87-106">Not all frequency combinations can be supported in a single schedule.</span></span> <span data-ttu-id="9ae87-107">たとえば、毎週金曜日の正午と</span><span class="sxs-lookup"><span data-stu-id="9ae87-107">For example, if you want to run a report at 12:00 P.M.</span></span> <span data-ttu-id="9ae87-108">午後 4 時 00 分まで</span><span class="sxs-lookup"><span data-stu-id="9ae87-108">and 4:00 P.M.</span></span> <span data-ttu-id="9ae87-109">レポートを実行する場合、実行日を金曜日に指定した日単位のスケジュールを 2 つ作成し、1 つは開始時刻を正午に、</span><span class="sxs-lookup"><span data-stu-id="9ae87-109">every Friday, you must create two daily schedules that specify a Friday run date, one with a start time of 12:00 P.M.</span></span> <span data-ttu-id="9ae87-110">もう 1 つは開始時刻を午後 4 時に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ae87-110">and another with a start time of 4:00 P.M.</span></span>  
  
 <span data-ttu-id="9ae87-111">スケジュールは、そのスケジュールをホストおよび処理するレポート サーバーのローカル時間に基づいて処理されます。</span><span class="sxs-lookup"><span data-stu-id="9ae87-111">Schedule processing is based on the local time of the report server that hosts and processes the schedule.</span></span>  
  
 <span data-ttu-id="9ae87-112">このページを開くには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を起動してレポート サーバーに接続し、 **[共有スケジュール]** を右クリックして **[新しいスケジュール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ae87-112">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, right-click **Shared Schedule**, and select **New Schedule**.</span></span> <span data-ttu-id="9ae87-113">スケジュールを保存するには、SQL Server エージェント サービスが実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ae87-113">To save the schedule, SQL Server Agent service must be running.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9ae87-114">この機能は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="9ae87-114">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9ae87-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各エディションでサポートされる機能の一覧については、「[SQL Server 2012 の各エディションがサポートする機能](https://go.microsoft.com/fwlink/?linkid=232473)」(https://go.microsoft.com/fwlink/?linkid=232473) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ae87-115">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
## <a name="options"></a><span data-ttu-id="9ae87-116">オプション</span><span class="sxs-lookup"><span data-stu-id="9ae87-116">Options</span></span>  
 <span data-ttu-id="9ae87-117">**Name**</span><span class="sxs-lookup"><span data-stu-id="9ae87-117">**Name**</span></span>  
 <span data-ttu-id="9ae87-118">共有スケジュールの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="9ae87-118">Type a name for the shared schedule.</span></span> <span data-ttu-id="9ae87-119">この名前は、ユーザーがレポートおよびサブスクリプションの共有スケジュールを選択するときにドロップダウン リストに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ae87-119">This name appears in drop-down lists when users select a shared schedule for reports and subscriptions.</span></span> <span data-ttu-id="9ae87-120">リスト内に納まり、共有スケジュールと別のスケジュールとを簡単に区別できるわかりやすい名前を付けてください。</span><span class="sxs-lookup"><span data-stu-id="9ae87-120">Be sure to provide a descriptive name that fits easily within a list and that easily distinguishes one shared schedule from another.</span></span> <span data-ttu-id="9ae87-121">名前には、少なくとも 1 つの英数字が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ae87-121">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="9ae87-122">また、スペースおよびいくつかの記号を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="9ae87-122">It can also include spaces and some symbols.</span></span> <span data-ttu-id="9ae87-123">名前を指定するときに使用できない記号は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9ae87-123">Do not use the following characters when specifying a name:</span></span>  
  
 <span data-ttu-id="9ae87-124">; ?</span><span class="sxs-lookup"><span data-stu-id="9ae87-124">; ?</span></span> <span data-ttu-id="9ae87-125">: \@ & = +、$/\*\< ></span><span class="sxs-lookup"><span data-stu-id="9ae87-125">: \@ & = + , $ / \* \< ></span></span>  
  
 <span data-ttu-id="9ae87-126">" /</span><span class="sxs-lookup"><span data-stu-id="9ae87-126">" /</span></span>  
  
 <span data-ttu-id="9ae87-127">**[このスケジュールの実行開始日]**</span><span class="sxs-lookup"><span data-stu-id="9ae87-127">**Begin running this schedule on**</span></span>  
 <span data-ttu-id="9ae87-128">このスケジュールの開始日を指定します。</span><span class="sxs-lookup"><span data-stu-id="9ae87-128">Specify a start date for this schedule.</span></span>  
  
 <span data-ttu-id="9ae87-129">**[このスケジュールの終了日]**</span><span class="sxs-lookup"><span data-stu-id="9ae87-129">**Stop this schedule on**</span></span>  
 <span data-ttu-id="9ae87-130">このスケジュールの有効期限を指定します。</span><span class="sxs-lookup"><span data-stu-id="9ae87-130">Specify an expiration date for this schedule.</span></span>  
  
 <span data-ttu-id="9ae87-131">**Type**</span><span class="sxs-lookup"><span data-stu-id="9ae87-131">**Type**</span></span>  
 <span data-ttu-id="9ae87-132">定期的なパターンが主に時間、日、週、または月のどれに基づくかを指定します。</span><span class="sxs-lookup"><span data-stu-id="9ae87-132">Specifies whether the recurrence pattern is based primarily on hours, days, weeks, or months.</span></span>  
  
 <span data-ttu-id="9ae87-133">**[時間]\([定期的なパターン])**</span><span class="sxs-lookup"><span data-stu-id="9ae87-133">**Hour (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="9ae87-134">スケジュール設定した操作を一定時間ごとに実行する (たとえば 6 時間ごとにレポートを実行する) ためのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="9ae87-134">Select options to run a scheduled operation in intervals of an hour (for example, to run a report every 6 hours).</span></span> <span data-ttu-id="9ae87-135">間隔は時間と分で指定できます。</span><span class="sxs-lookup"><span data-stu-id="9ae87-135">You can specify the interval in hours and minutes.</span></span>  
  
 <span data-ttu-id="9ae87-136">**[日]\([定期的なパターン])**</span><span class="sxs-lookup"><span data-stu-id="9ae87-136">**Day (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="9ae87-137">スケジュール設定した操作を数日間隔で実行する (たとえば 2 日ごとにレポートを実行する) ためのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="9ae87-137">Select options to run a scheduled operation in intervals of days (for example, to run a report every 2 days).</span></span> <span data-ttu-id="9ae87-138">間隔は日数で指定し、スケジュールを実行する時と分を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9ae87-138">You can specify the interval in days and at the hour and minute you want the schedule to run.</span></span>  
  
 <span data-ttu-id="9ae87-139">**[週]\([定期的なパターン])**</span><span class="sxs-lookup"><span data-stu-id="9ae87-139">**Week (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="9ae87-140">スケジュール設定した操作を毎週実行するか、繰り返しのパターンが週単位 (たとえば隔週でレポートを実行する) の場合のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="9ae87-140">Select options to run a scheduled operation in intervals of a week or when the pattern that you want to repeat is based on weeks (for example, to run a report every other week).</span></span> <span data-ttu-id="9ae87-141">週間スケジュールについて、スケジュールを実行する日、時、分を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9ae87-141">You can specify a weekly schedule to the day, hour, and minute that you want the schedule to run.</span></span>  
  
 <span data-ttu-id="9ae87-142">**[月]\([定期的なパターン])**</span><span class="sxs-lookup"><span data-stu-id="9ae87-142">**Month (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="9ae87-143">スケジュール設定した操作を毎月実行するか、繰り返しのパターンが月単位の場合のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="9ae87-143">Select options to run a scheduled operation in intervals of a month or when the pattern that you want to repeat is based on months.</span></span> <span data-ttu-id="9ae87-144">月間スケジュールについて、スケジュールを実行する日、時、分を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9ae87-144">You can specify a monthly schedule to the day, hour, and minute that you want the schedule to run.</span></span> <span data-ttu-id="9ae87-145">スケジュールでは特定の月を指定しなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="9ae87-145">You can omit specific months from the schedule.</span></span>  
  
 <span data-ttu-id="9ae87-146">**1 回。**</span><span class="sxs-lookup"><span data-stu-id="9ae87-146">**Once**</span></span>  
 <span data-ttu-id="9ae87-147">特定の日時に 1 回のみスケジュールを実行する場合にこのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="9ae87-147">Select this option to create a schedule that runs only once, on a specific date and time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ae87-148">参照</span><span class="sxs-lookup"><span data-stu-id="9ae87-148">See Also</span></span>  
 <span data-ttu-id="9ae87-149">[Management Studio のレポート サーバーの F1 ヘルプ](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="9ae87-149">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="9ae87-150">[Management Studio でレポート サーバーに接続する](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="9ae87-150">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="9ae87-151">[Create, Modify, and Delete Schedules](../subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="9ae87-151">[Create, Modify, and Delete Schedules](../subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 <span data-ttu-id="9ae87-152">[[スケジュール]](../subscriptions/schedules.md) </span><span class="sxs-lookup"><span data-stu-id="9ae87-152">[Schedules](../subscriptions/schedules.md) </span></span>  
 [<span data-ttu-id="9ae87-153">Management Studio のレポート サーバーの F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="9ae87-153">Report Server in Management Studio F1 Help</span></span>](report-server-in-management-studio-f1-help.md)  
  
  
