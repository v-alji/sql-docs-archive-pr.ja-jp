---
title: 共有スケジュールの一時停止と再開 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- pausing schedules
- report-specific schedules [Reporting Services]
- shared schedules [Reporting Services], resuming
- resuming schedules
- continuing schedules
- schedules [Reporting Services], resuming
- schedules [Reporting Services], pausing
ms.assetid: e416be75-5234-4aa6-a3de-77f60f25169a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f525a15b07b79b5c0d37f9a88ed9483b351af326
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641425"
---
# <a name="pause-and-resume-shared-schedules"></a><span data-ttu-id="eca8f-102">Pause and Resume Shared Schedules</span><span class="sxs-lookup"><span data-stu-id="eca8f-102">Pause and Resume Shared Schedules</span></span>
  <span data-ttu-id="eca8f-103">使用中の共有スケジュールは、一時停止および再開することができます。</span><span class="sxs-lookup"><span data-stu-id="eca8f-103">You can pause and resume a shared schedule that is in use.</span></span> <span data-ttu-id="eca8f-104">共有スケジュールを一時停止すると、レポート処理とサブスクリプションのトリガーとして使用しているスケジュールが一時的に無効になります。</span><span class="sxs-lookup"><span data-stu-id="eca8f-104">Pausing a shared schedule provides a way to temporarily freeze a schedule that is used to trigger report processing and subscriptions.</span></span> <span data-ttu-id="eca8f-105">一時停止や再開を行うことができるのは共有スケジュールだけです。</span><span class="sxs-lookup"><span data-stu-id="eca8f-105">Only shared schedules can be paused and resumed.</span></span> <span data-ttu-id="eca8f-106">レポート固有のスケジュールは一時停止できません。</span><span class="sxs-lookup"><span data-stu-id="eca8f-106">You cannot pause report-specific schedules.</span></span>  
  
 <span data-ttu-id="eca8f-107">実行中のレポート処理は、一時停止および再開することができません。</span><span class="sxs-lookup"><span data-stu-id="eca8f-107">You cannot pause and resume report processing that is in progress.</span></span> <span data-ttu-id="eca8f-108">一時停止および再開できるのは、SQL Server エージェント サービスのスケジュール キューにあるスケジュールだけです。</span><span class="sxs-lookup"><span data-stu-id="eca8f-108">You can only pause and resume schedules that are in the scheduling queue of SQL Server Agent service.</span></span> <span data-ttu-id="eca8f-109">進行中のジョブは、スケジュール エンジンの対象外です。</span><span class="sxs-lookup"><span data-stu-id="eca8f-109">A job that is in progress is outside the scope of the scheduling engine.</span></span> <span data-ttu-id="eca8f-110">詳しくは、「 [実行中の処理を管理する](manage-a-running-process.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eca8f-110">For more information, see [Manage a Running Process](manage-a-running-process.md)</span></span>  
  
 <span data-ttu-id="eca8f-111">共有スケジュールを一時停止すると、その間に発生する予定の操作を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="eca8f-111">While a shared schedule is paused, any operations that would have occurred are allowed to lapse.</span></span> <span data-ttu-id="eca8f-112">共有スケジュールを再開すると、サーバーのローカル時刻を使用して、次のスケジュール設定時刻にレポートおよびサブスクリプションの処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="eca8f-112">After you resume a shared schedule, report and subscription processing occurs at the next scheduled time, using the local time of the server.</span></span> <span data-ttu-id="eca8f-113">ネイティブ モードのレポート サーバーまたは SharePoint サービス アプリケーションでは、スケジュールが一時停止されなければ実行される予定だった、スケジュールされていた操作については、埋め合わせるための実行は行われません。</span><span class="sxs-lookup"><span data-stu-id="eca8f-113">The native mode report server or SharePoint service applications, do not make up scheduled operations that would have occurred had the schedule not been paused.</span></span>  
  
 <span data-ttu-id="eca8f-114">このトピックの内容</span><span class="sxs-lookup"><span data-stu-id="eca8f-114">In this Topic:</span></span>  
  
-   [<span data-ttu-id="eca8f-115">共有スケジュールの一時停止と再開 (ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="eca8f-115">Pause and Resume Shared Schedules (Native Mode)</span></span>](#bkmk_native)  
  
-   [<span data-ttu-id="eca8f-116">共有スケジュールの一時停止と再開 (SharePoint モード)</span><span class="sxs-lookup"><span data-stu-id="eca8f-116">Pause and Resume Shared Schedules (SharePoint mode)</span></span>](#bkmk_sharepoint)  
  
##  <a name="pause-and-resume-shared-schedules-native-mode"></a><a name="bkmk_native"></a> <span data-ttu-id="eca8f-117">共有スケジュールの一時停止と再開 (ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="eca8f-117">Pause and Resume Shared Schedules (Native Mode)</span></span>  
 <span data-ttu-id="eca8f-118">共有スケジュールを一時停止または再開するには、レポート マネージャーの [スケジュール] ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="eca8f-118">To pause and resume a shared schedule, use the Schedules page in Report Manager.</span></span> <span data-ttu-id="eca8f-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] は使用できません。これには、スケジュールを一時停止または再開するためのオプションは用意されていません。</span><span class="sxs-lookup"><span data-stu-id="eca8f-119">You cannot use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]; it does not provide options for pausing and resuming schedules.</span></span> <span data-ttu-id="eca8f-120">詳細については、「 [Create, Modify, and Delete Schedules](create-modify-and-delete-schedules.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eca8f-120">For more information, see [Create, Modify, and Delete Schedules](create-modify-and-delete-schedules.md).</span></span>  
  
#### <a name="to-pause-or-resume-a-shared-schedule"></a><span data-ttu-id="eca8f-121">共有スケジュールを一時停止または再開するには</span><span class="sxs-lookup"><span data-stu-id="eca8f-121">To pause or resume a shared schedule</span></span>  
  
1.  <span data-ttu-id="eca8f-122">レポート マネージャーから、 **[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eca8f-122">From Report Manager Click, **Site Settings**.</span></span>  
  
2.  <span data-ttu-id="eca8f-123">**[スケジュール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eca8f-123">Click **Schedules**.</span></span>  
  
3.  <span data-ttu-id="eca8f-124">スケジュールを選択し、リボンで **[一時停止]** または **[再開]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eca8f-124">Select the schedule, and click **Pause** or **Resume** in the ribbon.</span></span> <span data-ttu-id="eca8f-125">スケジュールが現在一時停止している場合は、 **[状態]** 列に **[一時停止]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="eca8f-125">If a Schedule is currently paused, the **Status** column will contain **Paused**.</span></span>  
  
##  <a name="pause-and-resume-shared-schedules-sharepoint-mode"></a><a name="bkmk_sharepoint"></a> <span data-ttu-id="eca8f-126">共有スケジュールの一時停止と再開 (SharePoint モード)</span><span class="sxs-lookup"><span data-stu-id="eca8f-126">Pause and Resume Shared Schedules (SharePoint mode)</span></span>  
 <span data-ttu-id="eca8f-127">共有スケジュールを一時停止または再開するには、[サイトの設定] ページまたは PowerShell を使用します。</span><span class="sxs-lookup"><span data-stu-id="eca8f-127">To pause and resume a shared schedule, use the Site Settings page or PowerShell.</span></span> <span data-ttu-id="eca8f-128">スケジュールは SharePoint サイトごとに管理されます。</span><span class="sxs-lookup"><span data-stu-id="eca8f-128">Schedules are managed per SharePoint site.</span></span>  
  
#### <a name="to-pause-or-resume-a-shared-schedule"></a><span data-ttu-id="eca8f-129">共有スケジュールを一時停止または再開するには</span><span class="sxs-lookup"><span data-stu-id="eca8f-129">To pause or resume a shared schedule</span></span>  
  
1.  <span data-ttu-id="eca8f-130">**[サイトの操作]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eca8f-130">Click **Site Actions**.</span></span>  
  
2.  <span data-ttu-id="eca8f-131">**[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eca8f-131">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="eca8f-132">[Reporting Services] セクションで、 **[共有スケジュールの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eca8f-132">In the Reporting Services section, click **Manage Shared Schedules**.</span></span>  
  
4.  <span data-ttu-id="eca8f-133">スケジュールを選択し、 **[選択したスケジュールの一時停止]** または **[選択したスケジュールの実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eca8f-133">Select the schedule, and click **Pause Selected Schedules** or **Run Selected Schedules**.</span></span> <span data-ttu-id="eca8f-134">スケジュールが現在一時停止している場合は、 **[状態]** 列に **[一時停止]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="eca8f-134">If a Schedule is currently paused, the **Status** column will contain **Paused**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eca8f-135">参照</span><span class="sxs-lookup"><span data-stu-id="eca8f-135">See Also</span></span>  
 <span data-ttu-id="eca8f-136">[[スケジュール]](schedules.md) </span><span class="sxs-lookup"><span data-stu-id="eca8f-136">[Schedules](schedules.md) </span></span>  
 <span data-ttu-id="eca8f-137">[Create, Modify, and Delete Schedules](create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="eca8f-137">[Create, Modify, and Delete Schedules](create-modify-and-delete-schedules.md) </span></span>  
 <span data-ttu-id="eca8f-138">[レポート サーバーでタイム ゾーンと時計の設定を変更する](change-time-zones-and-clock-settings-on-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="eca8f-138">[Change Time Zones and Clock Settings on a Report Server](change-time-zones-and-clock-settings-on-a-report-server.md) </span></span>  
 [<span data-ttu-id="eca8f-139">実行中の処理を管理する</span><span class="sxs-lookup"><span data-stu-id="eca8f-139">Manage a Running Process</span></span>](manage-a-running-process.md)  
  
  
