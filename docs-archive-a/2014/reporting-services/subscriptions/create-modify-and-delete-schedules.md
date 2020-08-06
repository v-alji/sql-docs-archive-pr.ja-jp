---
title: スケジュールの作成、変更、および削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report-specific schedules [Reporting Services]
- shared schedules [Reporting Services]
- modifying schedules
- removing schedules
- shared schedules [Reporting Services], creating
- shared schedules [Reporting Services], modifying
- schedules [Reporting Services], deleting
- deleting schedules
- schedules [Reporting Services], creating
- schedules [Reporting Services], modifying
- shared schedules [Reporting Services], deleting
ms.assetid: 05da5f3d-9222-43a9-893b-aa10f0f690f8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ec235126caee5acd0d5c79958528565d917bf522
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643691"
---
# <a name="create-modify-and-delete-schedules"></a><span data-ttu-id="2debc-102">Create, Modify, and Delete Schedules</span><span class="sxs-lookup"><span data-stu-id="2debc-102">Create, Modify, and Delete Schedules</span></span>
  <span data-ttu-id="2debc-103">このトピックでは、スケジュールを作成、変更、および削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2debc-103">Use this topic to learn about how to create, modify, and delete schedules.</span></span>  
  
 <span data-ttu-id="2debc-104">このトピックの内容:</span><span class="sxs-lookup"><span data-stu-id="2debc-104">In this topic:</span></span>  
  
-   [<span data-ttu-id="2debc-105">共有スケジュールの管理の概要</span><span class="sxs-lookup"><span data-stu-id="2debc-105">Overview of Managing Shared Schedules</span></span>](#bkmk_overview)  
  
-   [<span data-ttu-id="2debc-106">共有スケジュールの作成および管理 (SharePoint モード)</span><span class="sxs-lookup"><span data-stu-id="2debc-106">Create and Manage Shared Schedules (SharePoint Mode)</span></span>](#bkmk_sharepoint)  
  
-   [<span data-ttu-id="2debc-107">共有スケジュールの作成および管理 (ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="2debc-107">Create and Manage Shared Schedules (Native Mode)</span></span>](#bkmk_native)  
  
##  <a name="overview-of-managing-shared-schedules"></a><a name="bkmk_overview"></a><span data-ttu-id="2debc-108">共有スケジュールの管理の概要</span><span class="sxs-lookup"><span data-stu-id="2debc-108">Overview of Managing Shared Schedules</span></span>  
 <span data-ttu-id="2debc-109">ネイティブ モードの共有スケジュールを管理するには、レポート マネージャーの [スケジュール] ページまたは [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]の [共有スケジュール] フォルダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="2debc-109">To manage shared schedules for native mode, use the Schedules page in Report Manager or the Shared Schedules folder in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="2debc-110">SharePoint モードの場合は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの管理ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="2debc-110">For SharePoint mode use, the management pages for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
 <span data-ttu-id="2debc-111">レポート サーバーに定義されたすべての共有スケジュールの表示、スケジュールの一時停止と再開 (レポート マネージャーのみで可能)、変更または削除するスケジュールの選択を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2debc-111">You can view all the shared schedules that are defined for the report server, pause and resume schedules (on Report Manager only), and select schedules to modify or delete.</span></span> <span data-ttu-id="2debc-112">[共有スケジュール] ページには、頻度、所有者、有効期限、およびステータスなど、各スケジュールの状態に関する情報がまとめられています。</span><span class="sxs-lookup"><span data-stu-id="2debc-112">The Shared Schedules page summarizes the following information about the state of each schedule: frequency, owner, expiration date, and status.</span></span>  
  
 <span data-ttu-id="2debc-113">共有スケジュールがアクティブで使用されているかどうかは、次の方法で判別できます。</span><span class="sxs-lookup"><span data-stu-id="2debc-113">You can tell whether a shared schedule is actively used by:</span></span>  
  
-   <span data-ttu-id="2debc-114">[共有スケジュール] ページで、[最終実行] の日付、[次の実行] の日付、[状態] フィールドの値を調べる。</span><span class="sxs-lookup"><span data-stu-id="2debc-114">Inspecting the values in the Last Run date, Next Run date, and Status fields on the Shared Schedules page.</span></span> <span data-ttu-id="2debc-115">有効期限が切れてスケジュールが実行されなくなった場合、[状態] フィールドに有効期限の日付が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2debc-115">If a schedule no longer runs because it has expired, the expiration date appears in the Status field.</span></span>  
  
-   <span data-ttu-id="2debc-116">特定の共有スケジュールの [レポート] ページを表示する。</span><span class="sxs-lookup"><span data-stu-id="2debc-116">Viewing the Reports page of a given Shared Schedule.</span></span> <span data-ttu-id="2debc-117">このページには、共有スケジュールを使用するすべてのレポートと共有データセットが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="2debc-117">This page lists all reports and shared datasets that use the shared schedule.</span></span>  
  
-   <span data-ttu-id="2debc-118">レポート実行ログ ファイルまたはトレース ログを表示して、レポートがスケジュールによって指定された時間に実行されたかどうかを確認する。</span><span class="sxs-lookup"><span data-stu-id="2debc-118">Viewing the report execution log files or trace logs to determine whether reports have been run at the times specified by the schedule.</span></span> <span data-ttu-id="2debc-119">詳細については、「 [Reporting Services のログ ファイルとソース](../report-server/reporting-services-log-files-and-sources.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2debc-119">For more information, see [Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md).</span></span>  
  
##  <a name="create-and-manage-shared-schedules-sharepoint-mode"></a><a name="bkmk_sharepoint"></a><span data-ttu-id="2debc-120">共有スケジュールの作成および管理 (SharePoint モード)</span><span class="sxs-lookup"><span data-stu-id="2debc-120">Create and Manage Shared Schedules (SharePoint Mode)</span></span>  
 <span data-ttu-id="2debc-121">共有スケジュールは、定義済みのスケジュール情報を任意の数のレポートまたはサブスクリプションに提供する、多目的のスケジュールです。</span><span class="sxs-lookup"><span data-stu-id="2debc-121">A shared schedule is a multipurpose schedule that provides ready-to-use schedule information to any number of reports or subscriptions.</span></span> <span data-ttu-id="2debc-122">共有スケジュールを作成した後は、スケジュール情報が必要なときにサブスクリプションまたはプロパティ ページでその共有スケジュールを参照できます。</span><span class="sxs-lookup"><span data-stu-id="2debc-122">You create a shared schedule once, and then reference it in a subscription or property page when you need schedule information.</span></span> <span data-ttu-id="2debc-123">共有スケジュールは、管理、一時停止、および再開を一元的に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2debc-123">Shared schedules can be centrally managed, paused, and resumed.</span></span> <span data-ttu-id="2debc-124">これとは対照的に、カスタム スケジュールでレポートやサブスクリプションの実行を回避する場合は、手動でスケジュールを編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2debc-124">In contrast, you must edit a custom schedule manually to prevent a report or subscription from running.</span></span>  
  
 <span data-ttu-id="2debc-125">SharePoint サイトでの共有スケジュールの作成、変更、または削除は、サイト管理者のみが実行できます。</span><span class="sxs-lookup"><span data-stu-id="2debc-125">You must be a site administrator to create, modify, or delete shared schedules on a SharePoint site.</span></span>  
  
 <span data-ttu-id="2debc-126">スケジュールは、わかりやすい名前を付けて識別できます。</span><span class="sxs-lookup"><span data-stu-id="2debc-126">You can identify a specific schedule by its descriptive name.</span></span> <span data-ttu-id="2debc-127">名前が指定されなかった場合は、反復パターンや実行日時などの情報を基に既定の名前が作成されます。</span><span class="sxs-lookup"><span data-stu-id="2debc-127">If a name is not specified, a default name is created based on facts about the schedule, such as its recurrence pattern or dates and times when it runs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2debc-128">共有スケジュールを作成するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスが必要です。</span><span class="sxs-lookup"><span data-stu-id="2debc-128">Creating shared schedules requires [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
### <a name="create-shared-schedules-sharepoint"></a><span data-ttu-id="2debc-129">共有スケジュールの作成および管理 (SharePoint)</span><span class="sxs-lookup"><span data-stu-id="2debc-129">Create Shared Schedules (SharePoint)</span></span>  
  
##### <a name="to-create-shared-schedules"></a><span data-ttu-id="2debc-130">共有スケジュールを作成するには</span><span class="sxs-lookup"><span data-stu-id="2debc-130">To create shared schedules</span></span>  
  
1.  <span data-ttu-id="2debc-131">**[サイトの操作]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2debc-131">Click **Site Actions**.</span></span>  
  
2.  <span data-ttu-id="2debc-132">**[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2debc-132">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="2debc-133">[Reporting Services] セクションで、 **[共有スケジュールの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2debc-133">In the Reporting Services section, click **Manage Shared Schedules**.</span></span>  
  
4.  <span data-ttu-id="2debc-134">**[スケジュールの追加]** をクリックして、[スケジュールのプロパティ] ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="2debc-134">Click **Add Schedule** to open the Schedule Properties page.</span></span>  
  
5.  <span data-ttu-id="2debc-135">スケジュールにわかりやすい名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="2debc-135">Enter a descriptive name for the schedule.</span></span> <span data-ttu-id="2debc-136">この名前は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のレポートを操作するために使用するアプリケーション ページで、サイト全体のスケジュール定義ページのドロップダウン リストに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2debc-136">On the application pages used to work with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] reports, this name will appear in drop-down lists in schedule definition pages throughout the site.</span></span> <span data-ttu-id="2debc-137">読みづらい長い名前は避け、</span><span class="sxs-lookup"><span data-stu-id="2debc-137">Avoid long names that are hard to read.</span></span> <span data-ttu-id="2debc-138">名前の先頭に最もわかりやすい情報を置くという名前付け規則に従ってください。</span><span class="sxs-lookup"><span data-stu-id="2debc-138">Do follow a naming convention that puts the most description information at the beginning of the name.</span></span>  
  
6.  <span data-ttu-id="2debc-139">頻度を選択します。</span><span class="sxs-lookup"><span data-stu-id="2debc-139">Choose a frequency.</span></span> <span data-ttu-id="2debc-140">選択した頻度に応じて、その頻度をサポートするスケジュール オプションがページに表示されます (たとえば、 **[月]** を選択した場合、ページには各月が表示されます)。</span><span class="sxs-lookup"><span data-stu-id="2debc-140">Depending on the frequency you choose, the schedule options that appear on the page might change to support that frequency (for example, if you choose **Month**, the name of each month will appear on the page).</span></span>  
  
7.  <span data-ttu-id="2debc-141">スケジュールを定義します。</span><span class="sxs-lookup"><span data-stu-id="2debc-141">Define the schedule.</span></span> <span data-ttu-id="2debc-142">1 つのスケジュールの中での使用がサポートされない組み合わせもあります。</span><span class="sxs-lookup"><span data-stu-id="2debc-142">Not all schedule combinations can be supported in a single schedule.</span></span>  
  
8.  <span data-ttu-id="2debc-143">開始日と終了日を設定します。</span><span class="sxs-lookup"><span data-stu-id="2debc-143">Set a start and end date.</span></span>  
  
9. <span data-ttu-id="2debc-144">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2debc-144">Click **OK**.</span></span>  
  
### <a name="delete-shared-schedules-sharepoint"></a><span data-ttu-id="2debc-145">共有スケジュールの削除 (SharePoint)</span><span class="sxs-lookup"><span data-stu-id="2debc-145">Delete Shared Schedules (SharePoint)</span></span>  
 <span data-ttu-id="2debc-146">共有スケジュールかレポート固有スケジュールかにかかわらず、すべてのスケジュールは手動で削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2debc-146">All schedules, whether shared or report specific, must be deleted manually.</span></span> <span data-ttu-id="2debc-147">使用中の共有スケジュールを削除すると、そのスケジュールへのすべての参照が、未指定のカスタム スケジュール (日時の情報がないカスタム スケジュール) に置き換わります。</span><span class="sxs-lookup"><span data-stu-id="2debc-147">If you delete a shared schedule that is in use, all references to it are replaced with unspecified custom schedules (that is, a custom schedule that does not have date or time information).</span></span>  
  
 <span data-ttu-id="2debc-148">スケジュールを削除することとスケジュールの有効期限が切れることは違います。</span><span class="sxs-lookup"><span data-stu-id="2debc-148">Deleting a schedule and causing it to expire are different.</span></span> <span data-ttu-id="2debc-149">有効期限はスケジュールを停止するために使用されますが、スケジュールは削除されません。</span><span class="sxs-lookup"><span data-stu-id="2debc-149">An expiration date is used to stop a schedule but does not delete it.</span></span> <span data-ttu-id="2debc-150">スケジュールはレポート サーバーの操作を自動化することが目的であり、自動的には削除されません。</span><span class="sxs-lookup"><span data-stu-id="2debc-150">Because schedules are used to automate report server operations, they are never deleted automatically.</span></span> <span data-ttu-id="2debc-151">有効期限切れのスケジュールが残っていることで、レポート サーバー管理者は自動化された処理が突然停止した理由を知ることができます。</span><span class="sxs-lookup"><span data-stu-id="2debc-151">Expired schedules provide evidence to report server administrators as to why an automated process has suddenly stopped.</span></span> <span data-ttu-id="2debc-152">この有効期限が切れたスケジュールがなければ、レポート サーバー管理者は問題の診断を誤るか、正常に機能する処理のトラブルシューティングを行おうとして不要な時間を費やしてしまう可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2debc-152">Without the presence of the expired schedule, a report server administrator might misdiagnose the problem or spend unnecessary time trying to troubleshoot a fully functional process.</span></span>  
  
 <span data-ttu-id="2debc-153">有効期限の切れたカスタム スケジュールは、レポートに関連付けられたままになります。</span><span class="sxs-lookup"><span data-stu-id="2debc-153">A custom schedule that has expired remains attached to the report.</span></span> <span data-ttu-id="2debc-154">スケジュールの有効期限が切れたかどうかは、終了日を確認することで判断できます。</span><span class="sxs-lookup"><span data-stu-id="2debc-154">You can determine if a schedule has expired by checking its end date.</span></span> <span data-ttu-id="2debc-155">有効期限が切れた共有スケジュールは、[共有スケジュール] ボックスの一覧に残ります。</span><span class="sxs-lookup"><span data-stu-id="2debc-155">An expired shared schedule remains in the Shared Schedules list.</span></span> <span data-ttu-id="2debc-156">スケジュールの有効期限が切れたかどうかは [状態] フィールドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2debc-156">The Status field indicates whether the schedule has expired.</span></span> <span data-ttu-id="2debc-157">終了日を延長してスケジュールを再設定するか、不要になった場合はそのスケジュールの参照を削除することができます。</span><span class="sxs-lookup"><span data-stu-id="2debc-157">You can reinstate the schedule by extending the end date, or you can remove the schedule reference if you no longer need it.</span></span>  
  
##### <a name="to-delete-a-shared-schedule"></a><span data-ttu-id="2debc-158">共有スケジュールを削除するには</span><span class="sxs-lookup"><span data-stu-id="2debc-158">To delete a shared schedule</span></span>  
  
1.  <span data-ttu-id="2debc-159">**[サイトの操作]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2debc-159">Click **Site Actions**.</span></span>  
  
2.  <span data-ttu-id="2debc-160">**[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2debc-160">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="2debc-161">[Reporting Services] セクションで、 **[共有スケジュールの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2debc-161">In the Reporting Services section, click **Manage Shared Schedules**.</span></span>  
  
4.  <span data-ttu-id="2debc-162">スケジュールを選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2debc-162">Select the schedule, and click **Delete**.</span></span>  
  
##  <a name="create-and-manage-shared-schedules-native-mode"></a><a name="bkmk_native"></a><span data-ttu-id="2debc-163">共有スケジュールの作成と管理 (ネイティブモード)</span><span class="sxs-lookup"><span data-stu-id="2debc-163">Create and Manage Shared Schedules (Native Mode)</span></span>  
 <span data-ttu-id="2debc-164">共有スケジュールは、レポート マネージャーの [スケジュール] ページまたは [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]の [共有スケジュール] フォルダーを使用して、手動で削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2debc-164">Shared schedules must be deleted manually using the Schedules page in Report Manager or the Shared Schedules folder in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="2debc-165">使用中の共有スケジュールを削除する場合、その共有スケジュールへのすべての参照はレポート固有スケジュールに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="2debc-165">If you delete a shared schedule that is in use, all references to it are replaced with report-specific schedules.</span></span>  
  
 <span data-ttu-id="2debc-166">レポートおよびサブスクリプションに固有のスケジュールは、レポートまたはサブスクリプションを削除したとき、または別の方法でレポートまたはサブスクリプションを実行することを選択したときに削除されます。</span><span class="sxs-lookup"><span data-stu-id="2debc-166">Report and subscription-specific schedules are deleted when you delete the report or subscription, or when you choose a different approach to run the report or subscription.</span></span> <span data-ttu-id="2debc-167">たとえば、 **[常に最新データを使用して、このレポートを実行する]** を選択すると、レポート実行スナップショットとしてレポートを実行するために作成したレポート固有のスケジュールは削除されます。</span><span class="sxs-lookup"><span data-stu-id="2debc-167">For example, choosing **Always run this report with the most recent data** will delete a report-specific schedule that you created to run a report as a report execution snapshot.</span></span>  
  
 <span data-ttu-id="2debc-168">スケジュールを削除することとスケジュールの有効期限が切れることは違います。</span><span class="sxs-lookup"><span data-stu-id="2debc-168">Deleting a schedule and causing it to expire are different.</span></span> <span data-ttu-id="2debc-169">有効期限はスケジュールを停止するために使用されますが、スケジュールは削除されません。</span><span class="sxs-lookup"><span data-stu-id="2debc-169">An expiration date is used to stop a schedule but does not delete it.</span></span> <span data-ttu-id="2debc-170">スケジュールは多くの機能を自動化するために使用されるので、自動的に削除されることは決してありません。</span><span class="sxs-lookup"><span data-stu-id="2debc-170">Because schedules are used to automate so many features, they are never deleted automatically.</span></span> <span data-ttu-id="2debc-171">有効期限切れのスケジュールが残っていることで、レポート サーバー管理者は自動化された処理が突然停止した理由を知ることができます。</span><span class="sxs-lookup"><span data-stu-id="2debc-171">Expired schedules provide evidence to report server administrators as to why an automated process has suddenly stopped.</span></span> <span data-ttu-id="2debc-172">有効期限が切れたスケジュールがないと、レポート サーバー管理者は問題の診断を誤るか、正常に機能していた処理のトラブルシューティングを行おうとして不要な時間を費やしてしまう可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2debc-172">Without the presence of the expired schedule, a report server administrator can misdiagnose the problem or spend unnecessary time trying to troubleshoot a fully functional process.</span></span>  
  
 <span data-ttu-id="2debc-173">有効期限の切れたレポート固有スケジュールは、レポートに添付されたままになります。</span><span class="sxs-lookup"><span data-stu-id="2debc-173">A report-specific schedule that has expired remains attached to the report.</span></span> <span data-ttu-id="2debc-174">スケジュールの有効期限が切れたかどうかは、終了日を確認することで判断できます。</span><span class="sxs-lookup"><span data-stu-id="2debc-174">You can determine if a schedule has expired by checking its end date.</span></span> <span data-ttu-id="2debc-175">有効期限が切れた共有スケジュールは、[共有スケジュール] の一覧に残ります。</span><span class="sxs-lookup"><span data-stu-id="2debc-175">An expired shared schedules remains in the Shared Schedules list.</span></span> <span data-ttu-id="2debc-176">スケジュールの有効期限が切れたかどうかは [状態] フィールドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2debc-176">The Status field indicates whether the schedule has expired.</span></span> <span data-ttu-id="2debc-177">終了日を延長してスケジュールを再設定するか、不要になった場合はそのスケジュールの参照を削除することができます。</span><span class="sxs-lookup"><span data-stu-id="2debc-177">You can reinstate the schedule by extending the end date, or you can remove the schedule reference if you no longer need it.</span></span>  
  
### <a name="create-delete-or-modify-a-shared-schedule-report-manager"></a><span data-ttu-id="2debc-178">共有スケジュールを作成、削除、または変更する (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="2debc-178">Create, Delete, or Modify a Shared Schedule (Report Manager)</span></span>  
 <span data-ttu-id="2debc-179">スケジュールの作成と変更は、スケジュールを実行する日時を指定する頻度オプションの設定で構成されます。</span><span class="sxs-lookup"><span data-stu-id="2debc-179">Creating and modifying a schedule consists of setting frequency options that determine when the schedule runs.</span></span>  
  
-   <span data-ttu-id="2debc-180">共有スケジュールは、個別のアイテムとして作成されます。</span><span class="sxs-lookup"><span data-stu-id="2debc-180">Shared schedules are created as separate items.</span></span> <span data-ttu-id="2debc-181">共有スケジュールは、作成後、サブスクリプションまたは他のスケジュール操作を定義するときに参照します。</span><span class="sxs-lookup"><span data-stu-id="2debc-181">After they are created, you reference them when defining a subscription or some other scheduled operation.</span></span>  
  
-   <span data-ttu-id="2debc-182">レポート固有スケジュールは、サブスクリプションを定義するとき、またはレポート実行プロパティを設定するときに作成されます。スケジュール情報の入力は、サブスクリプションの定義またはプロパティの設定の一部です。</span><span class="sxs-lookup"><span data-stu-id="2debc-182">Report-specific schedules are created when you define a subscription or set report execution properties; filling out schedule information is part of defining a subscription or setting properties.</span></span> <span data-ttu-id="2debc-183">レポート固有スケジュールを定義するには、そのスケジュールを使用するレポートまたはサブスクリプションを開きます。</span><span class="sxs-lookup"><span data-stu-id="2debc-183">To define a report-specific schedule, you open the report or subscription that uses it.</span></span>  
  
 <span data-ttu-id="2debc-184">共有スケジュールには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバー上で実行され、パブリッシュされた任意の数のレポートおよびサブスクリプションが使用できるスケジュールや定期実行情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="2debc-184">A shared schedule contains schedule and recurrence information that can be used by any number of published reports and subscriptions that run on a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="2debc-185">同時に実行されるレポートおよびサブスクリプションが多数存在する場合は、それらのジョブに対する共有スケジュールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2debc-185">If you have many reports and subscriptions that run at the same time, you can create a shared schedule for those jobs.</span></span> <span data-ttu-id="2debc-186">後で定期実行パターンや終了日を変更する必要性が生じた場合でも、それらを一度に変更できます。</span><span class="sxs-lookup"><span data-stu-id="2debc-186">If you want to subsequently change the recurrence pattern or the end date, you can make the change in one place.</span></span>  
  
 <span data-ttu-id="2debc-187">共有スケジュールは管理が容易であり、スケジュールされている操作をより柔軟に管理できます。</span><span class="sxs-lookup"><span data-stu-id="2debc-187">Shared schedules are easier to maintain and give you more flexibility in managing scheduled operations.</span></span> <span data-ttu-id="2debc-188">たとえば、共有スケジュールを一時停止したり再開したりできます。</span><span class="sxs-lookup"><span data-stu-id="2debc-188">For example, you can pause and resume shared schedules.</span></span> <span data-ttu-id="2debc-189">また、同時に実行される操作が多数スケジュールされていることに気付いた場合は、異なるタイミングで実行される複数の共有スケジュールを作成して、スケジュール情報を調整し、処理負荷をレポート サーバーに対して均等に配分することも可能です。</span><span class="sxs-lookup"><span data-stu-id="2debc-189">Also, if you find that too many scheduled operations are running at the same time, you can create multiple shared schedules that run at different times and then adjust the schedule information until the processing load evens out across the report server.</span></span>  
  
 <span data-ttu-id="2debc-190">スケジュールは、いつでも作成または変更できます。</span><span class="sxs-lookup"><span data-stu-id="2debc-190">You can create or modify a schedule at any time.</span></span> <span data-ttu-id="2debc-191">ただし、変更が完了する前にスケジュールが実行された場合、変更前のスケジュールが使用されます。</span><span class="sxs-lookup"><span data-stu-id="2debc-191">However, if a schedule starts to run before you have completed your modifications, the earlier version of the schedule is used.</span></span> <span data-ttu-id="2debc-192">変更されたスケジュールは、保存されるまで有効になりません。</span><span class="sxs-lookup"><span data-stu-id="2debc-192">The revised schedule does not take effect until you save it.</span></span>  
  
 <span data-ttu-id="2debc-193">共有スケジュールを変更する場合は、変更操作を行う前に一時停止することができます。</span><span class="sxs-lookup"><span data-stu-id="2debc-193">If you are modifying a shared schedule, you can pause it before you make changes.</span></span> <span data-ttu-id="2debc-194">変更内容は、スケジュールを再開すると有効になります。</span><span class="sxs-lookup"><span data-stu-id="2debc-194">The changes take effect when you resume the schedule.</span></span>  
  
##### <a name="to-create-or-modify-a-shared-schedule-report-manager"></a><span data-ttu-id="2debc-195">共有スケジュールを作成または変更するには (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="2debc-195">To create or modify a shared schedule (Report Manager)</span></span>  
  
1.  <span data-ttu-id="2debc-196">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md) を開始します。</span><span class="sxs-lookup"><span data-stu-id="2debc-196">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="2debc-197">レポート マネージャーのグローバル ツール バーで、 **[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2debc-197">In Report Manager, click **Site Settings**on the global toolbar.</span></span>  
  
3.  <span data-ttu-id="2debc-198">[**スケジュール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2debc-198">Click **schedules**.</span></span>  
  
4.  <span data-ttu-id="2debc-199">**[新しいスケジュール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2debc-199">Click **New Schedule**.</span></span> <span data-ttu-id="2debc-200">既存のスケジュールを変更するには、スケジュールの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2debc-200">To modify an existing schedule, click the name of the schedule.</span></span>  
  
5.  <span data-ttu-id="2debc-201">わかりやすいスケジュール名を入力します。</span><span class="sxs-lookup"><span data-stu-id="2debc-201">Type a descriptive name for the schedule.</span></span>  
  
6.  <span data-ttu-id="2debc-202">**[時間]** 、 **[日]** 、 **[週]** 、または **[月]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2debc-202">Select **Hour**, **Day**, **Week**, or **Month**.</span></span> <span data-ttu-id="2debc-203">一度だけ実行するスケジュールを作成するには、 **[一度だけ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2debc-203">Click **Once** to create a schedule that runs one time only.</span></span> <span data-ttu-id="2debc-204">スケジュールの基準を指定すると、新たなオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2debc-204">Additional options appear when you specify the basis of your schedule.</span></span>  
  
7.  <span data-ttu-id="2debc-205">必要に応じて、スケジュールの開始日を選択します。</span><span class="sxs-lookup"><span data-stu-id="2debc-205">Optionally select a date to start the schedule.</span></span> <span data-ttu-id="2debc-206">既定値は、現在の日付です。</span><span class="sxs-lookup"><span data-stu-id="2debc-206">The default is the current day.</span></span> <span data-ttu-id="2debc-207">明日以降の日付を入力して、スケジュールの開始日を延期できます。</span><span class="sxs-lookup"><span data-stu-id="2debc-207">You can postpone the schedule start time by choosing a later date.</span></span>  
  
8.  <span data-ttu-id="2debc-208">必要に応じて、スケジュールの終了日を選択します。</span><span class="sxs-lookup"><span data-stu-id="2debc-208">Optionally, select a date to end the schedule.</span></span> <span data-ttu-id="2debc-209">スケジュールの実行は設定日に停止されますが、スケジュールは削除されません。</span><span class="sxs-lookup"><span data-stu-id="2debc-209">The schedule stops running on this date, but is not deleted.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##### <a name="to-delete-a-shared-schedule-report-manager"></a><span data-ttu-id="2debc-210">共有スケジュールを削除するには (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="2debc-210">To delete a shared schedule (Report Manager)</span></span>  
  
1.  <span data-ttu-id="2debc-211">レポート マネージャーのグローバル ツール バーで、 **[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2debc-211">In Report Manager, click **Site Settings**on the global toolbar.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2debc-212">**[サイトの設定]** が利用できない場合は、サイト設定にアクセスする権限がありません。</span><span class="sxs-lookup"><span data-stu-id="2debc-212">If **Site Settings** is not available, you do not have permission to access site settings.</span></span>  
  
2.  <span data-ttu-id="2debc-213">ページの **[その他]** セクションで、 **[共有スケジュールの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2debc-213">In the **Other** section on the page, click **Manage shared schedules**.</span></span>  
  
3.  <span data-ttu-id="2debc-214">削除するスケジュールの隣のチェック ボックスをオンにして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2debc-214">Select the check box next to the schedule you want to delete, and then click **Delete**.</span></span>  
  
 <span data-ttu-id="2debc-215">複数のレポートおよびサブスクリプションによって使用される共有スケジュールを削除した場合、以前にその共有スケジュールを使用していたレポートおよびサブスクリプションごとに別個のスケジュールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2debc-215">If you delete a shared schedule that is used by multiple reports and subscriptions, the report server will create individual schedules for each report and subscription that previously used the shared schedule.</span></span> <span data-ttu-id="2debc-216">新たに作成される各スケジュールには、共有スケジュールで指定されていた日付、時刻、および定期的なパターンが保持されます。</span><span class="sxs-lookup"><span data-stu-id="2debc-216">Each new individual schedule will contain the date, time, and recurrence pattern that was specified in the shared schedule.</span></span> <span data-ttu-id="2debc-217">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には、個々のスケジュールを一元管理する手段は存在しません。</span><span class="sxs-lookup"><span data-stu-id="2debc-217">Note that [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not provide central management of individual schedules.</span></span> <span data-ttu-id="2debc-218">共有スケジュールを削除した場合、それ以降は、各アイテムのスケジュール情報を個別に管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2debc-218">If you delete a shared schedule, you will now have to maintain the schedule information for each individual item.</span></span>  
  
 <span data-ttu-id="2debc-219">共有スケジュールが使用されているかどうかが不明な場合は、代わりに [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] で共有スケジュールを削除することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="2debc-219">If you are not sure whether a shared schedule is used, consider deleting it in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] instead.</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="2debc-220">には、レポート マネージャーと同じ共有スケジュール管理機能が備えられていますが、共有スケジュールが使用されている各レポート名を表示するレポート ページが別途用意されています。</span><span class="sxs-lookup"><span data-stu-id="2debc-220">provides the same shared schedule management features as Report Manager, but it provides an additional Reports page that shows you the name of each report that uses the schedule.</span></span>  
  
### <a name="create-delete-or-modify-a-shared-schedule-management-studio"></a><span data-ttu-id="2debc-221">共有スケジュールを作成、削除、または変更する (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="2debc-221">Create, Delete, or Modify a Shared Schedule (Management Studio)</span></span>  
 <span data-ttu-id="2debc-222">共有スケジュールには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバー上で実行され、パブリッシュされた任意の数のレポートおよびサブスクリプションが使用できるスケジュールや定期実行情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="2debc-222">A shared schedule contains schedule and recurrence information that can be used by any number of published reports and subscriptions that run on a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="2debc-223">同時に実行されるレポートおよびサブスクリプションが多数存在する場合は、それらのジョブに対する共有スケジュールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2debc-223">If you have many reports and subscriptions that run at the same time, you can create a shared schedule for those jobs.</span></span> <span data-ttu-id="2debc-224">後で定期実行パターンや終了日を変更する必要性が生じた場合でも、それらを一度に変更できます。</span><span class="sxs-lookup"><span data-stu-id="2debc-224">If you want to subsequently change the recurrence pattern or the end date, you can make the change in one place.</span></span>  
  
 <span data-ttu-id="2debc-225">共有スケジュールは管理が容易であり、スケジュールされている操作をより柔軟に管理できます。</span><span class="sxs-lookup"><span data-stu-id="2debc-225">Shared schedules are easier to maintain and give you more flexibility in managing scheduled operations.</span></span> <span data-ttu-id="2debc-226">たとえば、共有スケジュールを一時停止したり再開したりできます。</span><span class="sxs-lookup"><span data-stu-id="2debc-226">For example, you can pause and resume shared schedules.</span></span> <span data-ttu-id="2debc-227">また、同時に実行される操作が多数スケジュールされていることに気付いた場合は、異なるタイミングで実行される複数の共有スケジュールを作成して、スケジュール情報を調整し、処理負荷をレポート サーバーに対して均等に配分することも可能です。</span><span class="sxs-lookup"><span data-stu-id="2debc-227">Also, if you find that too many scheduled operations are running at the same time, you can create multiple shared schedules that run at different times and then adjust the schedule information until the processing load evens out across the report server.</span></span>  
  
##### <a name="to-create-or-modify-a-shared-schedule-management-studio"></a><span data-ttu-id="2debc-228">共有スケジュールを作成または変更するには (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="2debc-228">To create or modify a shared schedule (Management Studio)</span></span>  
  
1.  <span data-ttu-id="2debc-229">SQL Server Management Studio を起動し、レポート サーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="2debc-229">Start SQL Server Management Studio and connect to a report server instance.</span></span>  
  
2.  <span data-ttu-id="2debc-230">オブジェクト エクスプローラーで、レポート サーバーのノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="2debc-230">In Object Explorer, expand a report server node.</span></span>  
  
3.  <span data-ttu-id="2debc-231">[共有スケジュール] フォルダーを右クリックし、 **[新しいスケジュール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2debc-231">Right-click the Shared Schedules folder, and then click **New Schedule**.</span></span> <span data-ttu-id="2debc-232">**[新しい共有スケジュール]** ダイアログ ボックスの [全般] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2debc-232">The General page of the **New Shared Schedule** dialog box is displayed.</span></span>  
  
     <span data-ttu-id="2debc-233">既存の共有スケジュールを変更するには、[共有スケジュール] フォルダーを展開し、変更するスケジュールを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2debc-233">To modify an existing shared schedule, expand the Shared Schedules folder, right-click the schedule you want to modify, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="2debc-234">わかりやすいスケジュール名を入力します。</span><span class="sxs-lookup"><span data-stu-id="2debc-234">Type a descriptive name for the schedule.</span></span>  
  
5.  <span data-ttu-id="2debc-235">必要に応じて、スケジュールの開始日を選択します。</span><span class="sxs-lookup"><span data-stu-id="2debc-235">Optionally select a date to start the schedule.</span></span> <span data-ttu-id="2debc-236">既定値は、現在の日付です。</span><span class="sxs-lookup"><span data-stu-id="2debc-236">The default is the current day.</span></span>  
  
6.  <span data-ttu-id="2debc-237">必要に応じて、スケジュールの終了日を選択します。</span><span class="sxs-lookup"><span data-stu-id="2debc-237">Optionally select a date to end the schedule.</span></span> <span data-ttu-id="2debc-238">スケジュールの実行は設定日に停止されますが、スケジュールは削除されません。</span><span class="sxs-lookup"><span data-stu-id="2debc-238">The schedule stops running on this date, but is not deleted.</span></span>  
  
7.  <span data-ttu-id="2debc-239">定期的なスケジュールを構成するには、 **[時間]** 、 **[日]** 、 **[週]** 、または **[月]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2debc-239">To configure a recurring schedule, select **Hour**, **Day**, **Week**, or **Month**.</span></span> <span data-ttu-id="2debc-240">追加のオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2debc-240">Additional options are displayed.</span></span> <span data-ttu-id="2debc-241">これらの追加のオプションを使用して、必要に応じた時間、日、週、または月に基づいて、スケジュールの頻度を構成します。</span><span class="sxs-lookup"><span data-stu-id="2debc-241">Use these additional options to configure schedule frequency, based on your preferred hour, day, week, or month.</span></span>  
  
     <span data-ttu-id="2debc-242">また、1 回のみの (定期的ではない) スケジュールを指定するには、 **[一度だけ]** を選択し、 **[開始時刻]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="2debc-242">Or, to specify a one-time (non-recurring) schedule, select **Once**, and then specify a **Start time**.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##### <a name="to-delete-a-shared-schedule-management-studio"></a><span data-ttu-id="2debc-243">共有スケジュールを削除するには (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="2debc-243">To delete a shared schedule (Management Studio)</span></span>  
  
1.  <span data-ttu-id="2debc-244">オブジェクト エクスプローラーで、レポート サーバーのノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="2debc-244">In Object Explorer, expand a report server node.</span></span>  
  
2.  <span data-ttu-id="2debc-245">[共有スケジュール] フォルダーを展開し、削除するスケジュールを右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2debc-245">Expand the Shared Schedules folder, right-click the schedule you want to delete, and then click **Delete**.</span></span> <span data-ttu-id="2debc-246">**[カタログ アイテムの削除]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2debc-246">The **Delete Catalog Items** dialog box appears.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="2debc-247">複数のレポートおよびサブスクリプションによって使用される共有スケジュールを削除した場合、以前にその共有スケジュールを使用していたレポートおよびサブスクリプションごとに別個のスケジュールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2debc-247">If you delete a shared schedule that is used by multiple reports and subscriptions, the report server will create individual schedules for each report and subscription that previously used the shared schedule.</span></span> <span data-ttu-id="2debc-248">新たに作成される各スケジュールには、共有スケジュールで指定されていた日付、時刻、および定期的なパターンが保持されます。</span><span class="sxs-lookup"><span data-stu-id="2debc-248">Each new individual schedule will contain the date, time, and recurrence pattern that was specified in the shared schedule.</span></span> <span data-ttu-id="2debc-249">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には、個々のスケジュールを一元管理する手段は存在しません。</span><span class="sxs-lookup"><span data-stu-id="2debc-249">Note that [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not provide central management of individual schedules.</span></span> <span data-ttu-id="2debc-250">共有スケジュールを削除した場合、それ以降は、各アイテムのスケジュール情報を個別に管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2debc-250">If you delete a shared schedule, you will now have to maintain the schedule information for each individual item.</span></span> <span data-ttu-id="2debc-251">共有スケジュールを削除する前に、[[レポート] ページ](../tools/schedule-properties-reports-page.md)を使用して、どのレポートが共有スケジュールを現在使用しているかを確認します。</span><span class="sxs-lookup"><span data-stu-id="2debc-251">Before deleting a shared schedule, use the [Reports Page](../tools/schedule-properties-reports-page.md) to determine which reports are currently using the shared schedule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2debc-252">参照</span><span class="sxs-lookup"><span data-stu-id="2debc-252">See Also</span></span>  
 <span data-ttu-id="2debc-253">[[スケジュール]](schedules.md) </span><span class="sxs-lookup"><span data-stu-id="2debc-253">[Schedules](schedules.md) </span></span>  
 <span data-ttu-id="2debc-254">[共有スケジュールを一時停止および再開する](pause-and-resume-shared-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="2debc-254">[Pause and Resume Shared Schedules](pause-and-resume-shared-schedules.md) </span></span>  
 <span data-ttu-id="2debc-255">[レポート &#40;レポートマネージャー&#41;にキャッシュする](../report-server/cache-a-report-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="2debc-255">[Cache a Report &#40;Report Manager&#41;](../report-server/cache-a-report-report-manager.md) </span></span>  
 [<span data-ttu-id="2debc-256">レポート履歴へのスナップショットの追加 &#40;レポート マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="2debc-256">Add a Snapshot to Report History &#40;Report Manager&#41;</span></span>](../report-server/add-a-snapshot-to-report-history-report-manager.md)  
  
  
