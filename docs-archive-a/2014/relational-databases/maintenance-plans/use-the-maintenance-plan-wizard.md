---
title: メンテナンス プラン ウィザードの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.ag.maintwiz.planprop.f1
- sql12.ag.maintwiz.task.f1
- sql12.ag.maintwiz.maintcleanup.f1
- sql12.ag.maintwiz.indexdefrag.f1
- sql12.ag.maintwiz.order.f1
- sql12.ag.maintwiz.histcleanup.f1
- sql12.ag.maintwiz.backuplog.f1
- sql12.ag.maintwiz.progress.f1
- sql12.ag.maintwiz.execagentjob.f1
- sql12.ag.maintwiz.integrity.f1
- sql12.ag.maintwiz.welcome.f1
- sql12.ag.maintwiz.backupdiff.f1
- sql12.ag.maintwiz.server.f1
- sql12.ag.maintwiz.summary.f1
- sql12.ag.maintwiz.backupfull.f1
- sql12.ag.maintwiz.report.f1
- sql12.ag.maintwiz.shrinkdb.f1
- sql12.ag.maintwiz.reindex.f1
- sql12.ag.maintwiz.updatestats.f1
helpviewer_keywords:
- Maintenance Plan Wizard
- Database Maintenance Plan Wizard
- Database Maintenance Plan Wizard, starting
ms.assetid: db65c726-9892-480c-873b-3af29afcee44
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ac134bbd4c65da4700990b69b09134230e98903f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633155"
---
# <a name="use-the-maintenance-plan-wizard"></a><span data-ttu-id="467c0-102">メンテナンス プラン ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="467c0-102">Use the Maintenance Plan Wizard</span></span>
  <span data-ttu-id="467c0-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]でメンテナンス プラン ウィザードを使用して、単一サーバーまたはマルチサーバーのメンテナンス プランを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="467c0-103">This topic describes how to create a single server or multiserver maintenance plan using the Maintenance Plan Wizard in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="467c0-104">メンテナンス プラン ウィザードを使用すると、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによって定期的に実行されるメンテナンス プランを作成できます。</span><span class="sxs-lookup"><span data-stu-id="467c0-104">The Maintenance Plan Wizard creates a maintenance plan that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can run on a regular basis.</span></span> <span data-ttu-id="467c0-105">これにより、バックアップ、データベースの整合性のチェック、データベース統計の更新など、さまざまなデータベース管理タスクを指定した間隔で実行できます。</span><span class="sxs-lookup"><span data-stu-id="467c0-105">This allows you to perform various database administration tasks, including backups, database integrity checks, or database statistics updates, at specified intervals.</span></span>  
  
 <span data-ttu-id="467c0-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="467c0-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="467c0-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="467c0-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="467c0-108">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="467c0-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="467c0-109">Security</span><span class="sxs-lookup"><span data-stu-id="467c0-109">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="467c0-110">SQL Server Management Studio でのメンテナンス プラン ウィザードを使用したメンテナンス プランの作成</span><span class="sxs-lookup"><span data-stu-id="467c0-110">Creating a maintenance plan using the Maintenance Plan Wizard in SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="467c0-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="467c0-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="467c0-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="467c0-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="467c0-113">マルチサーバー メンテナンス プランを作成するには、1 台のマスター サーバーと 1 台以上のターゲット サーバーを含むマルチサーバー環境を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="467c0-113">To create a multiserver maintenance plan, a multiserver environment containing one master server and one or more target servers must be configured.</span></span> <span data-ttu-id="467c0-114">マルチサーバー メンテナンス プランは、マスター サーバー上で作成および管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="467c0-114">Multiserver maintenance plans must be created and maintained on the master server.</span></span> <span data-ttu-id="467c0-115">このプランはターゲット サーバー上でも表示できますが、ターゲット サーバーでは管理できません。</span><span class="sxs-lookup"><span data-stu-id="467c0-115">These plans can be viewed, but not maintained, on target servers.</span></span>  
  
-   <span data-ttu-id="467c0-116">**db_ssisadmin** ロールおよび **dc_admin** ロールのメンバーは、特権を **sysadmin**に昇格できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="467c0-116">Members of the **db_ssisadmin** and **dc_admin** roles may be able to elevate their privileges to **sysadmin**.</span></span> <span data-ttu-id="467c0-117">このような特権の昇格が発生するのは、それらのロールが [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを変更でき、これらのパッケージを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの **sysadmin** セキュリティ コンテキストを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で実行できるためです。</span><span class="sxs-lookup"><span data-stu-id="467c0-117">This elevation of privilege can occur because these roles can modify [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages; these packages can be executed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the **sysadmin** security context of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="467c0-118">メンテナンス プラン、データ コレクション セット、およびその他の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの実行時にこの特権の昇格を防ぐには、特権が制限されたプロキシ アカウントを使用するようにパッケージを実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを構成するか、 **db_ssisadmin** ロールおよび **dc_admin** ロールには **sysadmin** メンバーのみを追加するようにします。</span><span class="sxs-lookup"><span data-stu-id="467c0-118">To guard against this elevation of privilege when running maintenance plans, data collection sets, and other [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs that run packages to use a proxy account with limited privileges or only add **sysadmin** members to the **db_ssisadmin** and **dc_admin** roles.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="467c0-119">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="467c0-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="467c0-120">Permissions</span><span class="sxs-lookup"><span data-stu-id="467c0-120">Permissions</span></span>  
 <span data-ttu-id="467c0-121">メンテナンス プランを作成または管理するには、 **sysadmin** 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="467c0-121">To create or manage maintenance plans, you must be a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="467c0-122">ユーザーが **sysadmin** 固定サーバー ロールのメンバーである場合のみ、オブジェクト エクスプローラーに **[メンテナンス プラン]** ノードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-122">Object Explorer only displays the **Maintenance Plans** node for users who are members of the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-maintenance-plan-wizard"></a><a name="SSMSProcedure"></a><span data-ttu-id="467c0-123">メンテナンスプランウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="467c0-123">Using Maintenance Plan Wizard</span></span>  
  
#### <a name="to-start-the-maintenance-plan-wizard"></a><span data-ttu-id="467c0-124">メンテナンス プラン ウィザードを起動するには</span><span class="sxs-lookup"><span data-stu-id="467c0-124">To start the Maintenance Plan Wizard</span></span>  
  
1.  <span data-ttu-id="467c0-125">管理計画を作成するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="467c0-125">Expand the server where you want to create your management plan.</span></span>  
  
2.  <span data-ttu-id="467c0-126">**[管理]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="467c0-126">Expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="467c0-127">**[メンテナンス プラン]** フォルダーを右クリックし、 **[メンテナンス プラン ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-127">Right-click the **Maintenance Plans** folder and select **Maintenance Plan Wizard**.</span></span>  
  
4.  <span data-ttu-id="467c0-128">**[SQL Server メンテナンス プラン ウィザード]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-128">On the **SQL Server Maintenance Plan Wizard** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="467c0-129">**[プランのプロパティを選択]** ページで、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="467c0-129">On the **Select Plan Properties** page:</span></span>  
  
    1.  <span data-ttu-id="467c0-130">**[名前]** ボックスに、作成するメンテナンス プランの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="467c0-130">In the **Name** box, enter the name of the maintenance plan you are creating.</span></span>  
  
    2.  <span data-ttu-id="467c0-131">**[説明]** ボックスに、メンテナンス プランの簡単な説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="467c0-131">In the **Description** box, briefly describe your maintenance plan.</span></span>  
  
    3.  <span data-ttu-id="467c0-132">**[実行するアカウント名]** ボックスで、Microsoft SQL Server エージェントがメンテナンス プランを実行するときに使用する資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-132">In the **Run as** list, specify the credential that Microsoft SQL Server Agent uses when executing the maintenance plan.</span></span>  
  
    4.  <span data-ttu-id="467c0-133">**[タスクごとに個別のスケジュールを使用する]** または **[プラン全体で単一のスケジュールを使用するか、スケジュールを使用しない]** を選択して、メンテナンス プランの定期的なスケジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-133">Select either **Separate schedules for each task** or **Single schedule for the entire plan or no schedule** to specify the recurring schedule of the maintenance plan.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="467c0-134">**[タスクごとに個別のスケジュールを使用する]** を選択した場合、メンテナンス プランのそれぞれのタスクに対して、**e** の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="467c0-134">If you select **Separate schedules for each task**, you will need to follow the steps in **e.**</span></span> <span data-ttu-id="467c0-135">の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="467c0-135">below for each task in your maintenance plan.</span></span>  
  
    5.  <span data-ttu-id="467c0-136">**[プラン全体で単一のスケジュールを使用するか、スケジュールを使用しない]** を選択した場合、 **[スケジュール]** の **[変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-136">If you selected **Single schedule for the entire plan or no schedule**, under **Schedule**, click **Change**.</span></span>  
  
        1.  <span data-ttu-id="467c0-137">**[新しいジョブ スケジュール]** ダイアログ ボックスで、 **[名前]** ボックスに、ジョブのスケジュールの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="467c0-137">In the **New Job Schedule** dialog box, in the **Name** box, enter the job schedule's name.</span></span>  
  
        2.  <span data-ttu-id="467c0-138">**[スケジュールの種類]** ボックスで、スケジュールの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-138">On the **Schedule type** list, select the type of schedule:</span></span>  
  
            -   <span data-ttu-id="467c0-139">**[SQL Server エージェントの開始時に自動的に開始]**</span><span class="sxs-lookup"><span data-stu-id="467c0-139">**Start automatically when SQL Server Agent starts**</span></span>  
  
            -   <span data-ttu-id="467c0-140">**[CPU がアイドル状態になったときに開始]**</span><span class="sxs-lookup"><span data-stu-id="467c0-140">**Start whenever the CPUs become idle**</span></span>  
  
            -   <span data-ttu-id="467c0-141">**[定期的]** 。</span><span class="sxs-lookup"><span data-stu-id="467c0-141">**Recurring**.</span></span> <span data-ttu-id="467c0-142">これは既定値です。</span><span class="sxs-lookup"><span data-stu-id="467c0-142">This is the default selection.</span></span>  
  
            -   <span data-ttu-id="467c0-143">**指定日時**</span><span class="sxs-lookup"><span data-stu-id="467c0-143">**One time**</span></span>  
  
        3.  <span data-ttu-id="467c0-144">**[有効]** チェック ボックスをオンまたはオフにして、スケジュールを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="467c0-144">Select or clear the **Enabled** check box to enable or disable the schedule.</span></span>  
  
        4.  <span data-ttu-id="467c0-145">**[定期的]** を選択した場合:</span><span class="sxs-lookup"><span data-stu-id="467c0-145">If you select **Recurring**:</span></span>  
  
            1.  <span data-ttu-id="467c0-146">**[頻度]** の **[実行]** ボックスの一覧で、実行の頻度を指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-146">Under **Frequency**, on the **Occurs** list, specify the frequency of occurrence:</span></span>  
  
                -   <span data-ttu-id="467c0-147">**[日単位]** を選択した場合は、 **[間隔]** ボックスに、ジョブ スケジュールを繰り返す頻度を日単位で入力します。</span><span class="sxs-lookup"><span data-stu-id="467c0-147">If you select **Daily**, in the **Recurs every** box, enter how often the job schedule repeats in days.</span></span>  
  
                -   <span data-ttu-id="467c0-148">**[週単位]** を選択した場合は、 **[間隔]** ボックスに、ジョブ スケジュールを繰り返す頻度を週単位で入力します。</span><span class="sxs-lookup"><span data-stu-id="467c0-148">If you select **Weekly**, in the **Recurs every** box, enter how often the job schedule repeats in weeks.</span></span> <span data-ttu-id="467c0-149">ジョブ スケジュールを実行する曜日を選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-149">Select the day or days of the week on which the job schedule is run.</span></span>  
  
                -   <span data-ttu-id="467c0-150">**[月単位]** を選択した場合は、 **[日]** または **[曜日]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-150">If you select **Monthly**, select either **Day** or **The**.</span></span>  
  
                    -   <span data-ttu-id="467c0-151">**[日]** を選択した場合は、ジョブ スケジュールを実行する日付と、ジョブ スケジュールを繰り返す頻度を月単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-151">If you select **Day**, enter both the date of the month you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="467c0-152">たとえば、隔月の 15 日にジョブ スケジュールを実行する場合は、 **[日]** を選択し、1 番目のボックスに「15」と入力し、2 番目のボックスに「2」と入力します。</span><span class="sxs-lookup"><span data-stu-id="467c0-152">For example, if you want the job schedule to run on the 15th day of the month every other month, select **Day** and enter "15" in the first box and "2" in the second box.</span></span> <span data-ttu-id="467c0-153">2 番目のボックスで使用できる最大の値は "99" であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="467c0-153">Please note that the largest number allowed in the second box is "99".</span></span>  
  
                    -   <span data-ttu-id="467c0-154">**[曜日]** を選択した場合は、ジョブ スケジュールを実行する曜日と、ジョブ スケジュールを繰り返す頻度を月単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-154">If you select **The**, select the specific day of the week within the month that you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="467c0-155">たとえば、隔月の最後の平日にジョブ スケジュールを実行する場合は、 **[日]** を選択し、リストから **[最終]** を選択します。次に 2 番目のリストから **[平日]** を選択し、最後のボックスに「2」と入力します。</span><span class="sxs-lookup"><span data-stu-id="467c0-155">For example, if you want the job schedule to run on the last weekday of the month every other month, select **Day**, select **last** from the first list and **weekday** from the second list, and then enter "2" in the last box.</span></span> <span data-ttu-id="467c0-156">**[第 1]** 、 **[第 2]** 、 **[第 3]** 、または **[第 4]** も、特定の平日 (たとえば、日曜日や水曜日) に加えて、最初の 2 つのリストから選択できます。</span><span class="sxs-lookup"><span data-stu-id="467c0-156">You can also select **first**, **second**, **third**, or **fourth**, as well as specific weekdays (for example: Sunday or Wednesday) from the first two lists.</span></span> <span data-ttu-id="467c0-157">最後のボックスで使用できる最大の値は "99" であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="467c0-157">Please note that the largest number allowed in the last box is "99".</span></span>  
  
            2.  <span data-ttu-id="467c0-158">**[一日のうちの頻度]** で、頻度、ジョブ スケジュールを実行する当日にジョブ スケジュールを繰り返す頻度を指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-158">Under **Daily frequency**, specify how often the job schedule repeats on the day the job schedule runs:</span></span>  
  
                -   <span data-ttu-id="467c0-159">**[1 回]** を選択した場合は、ジョブ スケジュールを実行する特定の時刻を **[1 回]** ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="467c0-159">If you select **Occurs once at**, enter the specific time of day when the job schedule should run in the **Occurs once at** box.</span></span> <span data-ttu-id="467c0-160">間、分、秒に加え、午前か午後かを入力します。</span><span class="sxs-lookup"><span data-stu-id="467c0-160">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
                -   <span data-ttu-id="467c0-161">**[間隔]** を選択した場合は、 **[頻度]** で選択した日にジョブ スケジュールを実行する頻度を指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-161">If you select **Occurs every**, specify how often the job schedule runs during the day chosen under **Frequency**.</span></span> <span data-ttu-id="467c0-162">たとえば、ジョブ スケジュールを実行する当日に 2 時間おきにジョブ スケジュールを実行する場合は、 **[間隔]** を選択し、1 番目のボックスに「2」と入力してから、 **[時間]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-162">For example, if you want the job schedule to repeat every 2 hours during the day that the job schedule is run, select **Occurs every**, enter "2" in the first box, and then select **hour(s)** from the list.</span></span> <span data-ttu-id="467c0-163">このリストでは、 **[分]** と **[秒]** を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="467c0-163">From this list you can also select **minute(s)** and **second(s)**.</span></span> <span data-ttu-id="467c0-164">1 番目のボックスで使用できる最大の値は "100" であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="467c0-164">Please note that the largest number allowed in the first box is "100".</span></span>  
  
                     <span data-ttu-id="467c0-165">**[開始]** ボックスに、ジョブ スケジュールの実行を開始する時刻を入力します。</span><span class="sxs-lookup"><span data-stu-id="467c0-165">In the **Starting at** box, enter the time that the job schedule should start running.</span></span> <span data-ttu-id="467c0-166">**[終了]** ボックスに、ジョブ スケジュールの実行を終了する時刻を入力します。</span><span class="sxs-lookup"><span data-stu-id="467c0-166">In the **Ending at** box, enter the time that the job schedule should stop repeating.</span></span> <span data-ttu-id="467c0-167">間、分、秒に加え、午前か午後かを入力します。</span><span class="sxs-lookup"><span data-stu-id="467c0-167">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
            3.  <span data-ttu-id="467c0-168">**[期間]** で、 **[開始日]** に、ジョブ スケジュールの実行を開始する日付を入力します。</span><span class="sxs-lookup"><span data-stu-id="467c0-168">Under **Duration**, in **Start date**, enter the date that you want the job schedule to start running.</span></span> <span data-ttu-id="467c0-169">**[終了日]** を選択します。ジョブ スケジュールの実行を停止するタイミングを指定しない場合は、 **[終了日なし]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-169">Select **End date** or **No end date** to indicate when the job schedule should stop running.</span></span> <span data-ttu-id="467c0-170">**[終了日]** を選択した場合は、ジョブ スケジュールの実行を停止する日付を入力します。</span><span class="sxs-lookup"><span data-stu-id="467c0-170">If you select **End date**, enter the date that you want to job schedule to stop running.</span></span>  
  
        5.  <span data-ttu-id="467c0-171">**[指定日時]** を選択した場合は、 **[指定日時に発生]** の **[日付]** ボックスに、ジョブ スケジュールを実行する日付を入力します。</span><span class="sxs-lookup"><span data-stu-id="467c0-171">If you select **One Time**, under **One-time occurrence**, in the **Date** box, enter the date that the job schedule will be run.</span></span> <span data-ttu-id="467c0-172">**[時刻]** ボックスに、ジョブ スケジュールを実行する時刻を入力します。</span><span class="sxs-lookup"><span data-stu-id="467c0-172">In the **Time** box, enter the time that the job schedule will be run.</span></span> <span data-ttu-id="467c0-173">間、分、秒に加え、午前か午後かを入力します。</span><span class="sxs-lookup"><span data-stu-id="467c0-173">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
        6.  <span data-ttu-id="467c0-174">**[概要]** の **[説明]** で、すべてのジョブ スケジュール設定が適切であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="467c0-174">Under **Summary**, in **Description**, verify that all job schedule settings are correct.</span></span>  
  
        7.  <span data-ttu-id="467c0-175">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-175">Click **OK**.</span></span>  
  
    6.  <span data-ttu-id="467c0-176">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-176">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="467c0-177">**[ターゲット サーバーの選択]** ページで、メンテナンス プランを実行するサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-177">On the **Select Target Servers** page, select the servers where you want to run the maintenance plan.</span></span> <span data-ttu-id="467c0-178">このページは、マスター サーバーとして構成された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのみで表示されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-178">This page is only visible on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances that are configured as master servers.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="467c0-179">マルチサーバー メンテナンス プランを作成するには、1 台のマスター サーバーと 1 台以上のターゲット サーバーを含むマルチサーバー環境を構成する必要があります。ローカル サーバーをマスター サーバーとして構成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="467c0-179">To create a multiserver maintenance plan, a multiserver environment containing one master server and one or more target servers must be configured, and the local server should be configured as a master server.</span></span> <span data-ttu-id="467c0-180">マルチサーバー環境では、このページに **"(local)"** マスター サーバーと、対応するすべてのターゲット サーバーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-180">In multiserver environments, this page displays the **(local)** master server and all corresponding target servers.</span></span>  
  
7.  <span data-ttu-id="467c0-181">**[メンテナンス タスクの選択]** ページで、プランに追加するメンテナンス タスクを 1 つ以上選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-181">On the **Select Maintenance Tasks** page, select one or more maintenance tasks to add to the plan.</span></span> <span data-ttu-id="467c0-182">必要なタスクをすべて選択したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-182">When you have selected all of the necessary tasks, click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="467c0-183">ここで選択したタスクにより、次の **[メンテナンス タスクの順序を選択]** ページの後に指定するページが決まります。</span><span class="sxs-lookup"><span data-stu-id="467c0-183">The tasks you select here will determine which pages you will need to complete after the **Select Maintenance Task Order** page below.</span></span>  
  
8.  <span data-ttu-id="467c0-184">**[メンテナンス タスクの順序を選択]** ページで、タスクを選択し、 **[上へ移動...]** または **[下へ移動...]** をクリックして、タスクの実行順序を変更します。</span><span class="sxs-lookup"><span data-stu-id="467c0-184">On the **Select Maintenance Task Order** page, select a task and click either **Move Up...** or **Move Down...** to change its order of execution.</span></span> <span data-ttu-id="467c0-185">完了したら (またはタスクの現在の順序を受け入れる場合は)、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-185">When finished, or if you are satisfied with the current order of tasks, click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="467c0-186">上の **[プランのプロパティを選択]** ページで **[タスクごとに個別のスケジュールを使用する]** を選択した場合は、このページでメンテナンス タスクの順序を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="467c0-186">If you selected **Separate schedules for each task** on the **Select Plan Properties** page above, you will not be able to change the order of the maintenance tasks on this page.</span></span>  
  
#### <a name="define-database-check-integrity-checkdb-tasks"></a><span data-ttu-id="467c0-187">データベースの整合性確認 (CHECKDB) タスクを定義する</span><span class="sxs-lookup"><span data-stu-id="467c0-187">Define Database Check Integrity (CHECKDB) Tasks</span></span>  
  
1.  <span data-ttu-id="467c0-188">**[データベースの整合性確認タスクの定義]** ページで、ユーザー テーブルとシステム テーブルの割り当ておよび構造的整合性、およびインデックスを確認するデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-188">On the **Define Database Check Integrity Task** page, choose the database or databases where the allocation and structural integrity of user and system tables and indexes will be checked.</span></span> <span data-ttu-id="467c0-189">`DBCC CHECKDB`[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行することにより、データベースに整合性の問題があった場合は報告されるため、システム管理者またはデータベースの所有者によって対処できます。</span><span class="sxs-lookup"><span data-stu-id="467c0-189">By running the `DBCC CHECKDB`[!INCLUDE[tsql](../../includes/tsql-md.md)] statement, this task ensures that any integrity problems with the database are reported, thereby allowing them to be addressed later by a system administrator or database owner.</span></span> <span data-ttu-id="467c0-190">詳細については、「[DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)」を参照してください。完了したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-190">For more information, see [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)When complete, click **Next**.</span></span>  
  
     <span data-ttu-id="467c0-191">このページで使用できるオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="467c0-191">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="467c0-192">**[データベース]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-192">**Databases** list</span></span>  
     <span data-ttu-id="467c0-193">このタスクで操作するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-193">Specify the databases affected by this task.</span></span>  
  
    -   <span data-ttu-id="467c0-194">**[すべてのデータベース]**</span><span class="sxs-lookup"><span data-stu-id="467c0-194">**All databases**</span></span>  
  
         <span data-ttu-id="467c0-195">**tempdb** を除くすべての [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースを対象として、このタスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="467c0-195">Generate a maintenance plan that runs this task against all [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases except **tempdb**.</span></span>  
  
    -   <span data-ttu-id="467c0-196">**システム データベース**</span><span class="sxs-lookup"><span data-stu-id="467c0-196">**System databases**</span></span>  
  
         <span data-ttu-id="467c0-197">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tempdb **およびユーザーが作成したデータベースを除く** システム データベースを対象として、このタスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="467c0-197">Generate a maintenance plan that runs this task against [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except **tempdb** and user-created databases.</span></span>  
  
    -   <span data-ttu-id="467c0-198">**[すべてのユーザー データベース] \(master、model、msdb、tempdb は対象外)**</span><span class="sxs-lookup"><span data-stu-id="467c0-198">**All user databases (excluding master, model, msdb, tempdb)**</span></span>  
  
         <span data-ttu-id="467c0-199">ユーザーが作成したすべてのデータベースを対象として、このタスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="467c0-199">Generate a maintenance plan that runs this task against all user-created databases.</span></span> <span data-ttu-id="467c0-200">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム データベースではメンテナンス タスクは実行されません。</span><span class="sxs-lookup"><span data-stu-id="467c0-200">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
    -   <span data-ttu-id="467c0-201">**[これらのデータベース]**</span><span class="sxs-lookup"><span data-stu-id="467c0-201">**These databases**</span></span>  
  
         <span data-ttu-id="467c0-202">選択されたデータベースだけを対象として、このタスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="467c0-202">Generate a maintenance plan that runs this task against only those databases that are selected.</span></span> <span data-ttu-id="467c0-203">このオプションをオンにする場合は、少なくとも 1 つのデータベースが一覧内で選択されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="467c0-203">At least one database in the list must be selected if this option is chosen.</span></span>  
  
     <span data-ttu-id="467c0-204">**[インデックスを含める]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-204">**Include indexes** check box</span></span>  
     <span data-ttu-id="467c0-205">すべてのインデックス ページおよびテーブル データ ページの整合性を確認します。</span><span class="sxs-lookup"><span data-stu-id="467c0-205">Check the integrity of all the index pages as well as the table data pages.</span></span>  
  
#### <a name="define-database-shrink-tasks"></a><span data-ttu-id="467c0-206">データベースの圧縮タスクを定義する</span><span class="sxs-lookup"><span data-stu-id="467c0-206">Define Database Shrink Tasks</span></span>  
  
1.  <span data-ttu-id="467c0-207">**[データベースの圧縮タスクの定義]** ページで、 `DBCC SHRINKDATABASE` ステートメントと `NOTRUNCATE` オプションまたは `TRUNCATEONLY` オプションを使用して、選択されているデータベースのサイズを小さくするタスクを作成します。</span><span class="sxs-lookup"><span data-stu-id="467c0-207">On the **Define Shrink Database Task** page, create a task that attempts to reduce the size of the selected databases by using the `DBCC SHRINKDATABASE` statement, with either the `NOTRUNCATE` or `TRUNCATEONLY` option.</span></span> <span data-ttu-id="467c0-208">詳細については、「[DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="467c0-208">For more information, see [DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql).</span></span> <span data-ttu-id="467c0-209">完了したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-209">When complete, click **Next**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="467c0-210">ファイルを圧縮するために移動されたデータは、ファイル内のあらゆる使用可能な場所に分散される場合があります。</span><span class="sxs-lookup"><span data-stu-id="467c0-210">Data that is moved to shrink a file can be scattered to any available location in the file.</span></span> <span data-ttu-id="467c0-211">これにより、インデックスの断片化が発生し、広範なインデックスを検索するクエリのパフォーマンスが低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="467c0-211">This causes index fragmentation and can slow the performance of queries that search a range of the index.</span></span> <span data-ttu-id="467c0-212">断片化を解消するには、圧縮後にファイルのインデックスを再構築することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="467c0-212">To eliminate the fragmentation, consider rebuilding the indexes on the file after shrinking.</span></span>  
  
     <span data-ttu-id="467c0-213">このページで使用できるオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="467c0-213">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="467c0-214">**[データベース]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-214">**Databases** list</span></span>  
     <span data-ttu-id="467c0-215">このタスクで操作するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-215">Specify the databases affected by this task.</span></span> <span data-ttu-id="467c0-216">この一覧で利用可能なオプションの詳細については、上の手順 9. を参照してください。</span><span class="sxs-lookup"><span data-stu-id="467c0-216">See step 9, above, for more information on the available options on this list.</span></span>  
  
     <span data-ttu-id="467c0-217">**[次のサイズに到達したらデータベースを圧縮]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-217">**Shrink database when it grows beyond** box</span></span>  
     <span data-ttu-id="467c0-218">このタスクが実行されるときのサイズをメガバイト単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-218">Specify the size in megabytes that causes the task to execute.</span></span>  
  
     <span data-ttu-id="467c0-219">**[圧縮後に残す空き領域]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-219">**Amount of free space to remain after shrink** box</span></span>  
     <span data-ttu-id="467c0-220">データベース ファイルの空き領域がこのサイズ (%) になったときに圧縮を停止します。</span><span class="sxs-lookup"><span data-stu-id="467c0-220">Stop shrinking when free space in database files reaches this size (as a percentage).</span></span>  
  
     <span data-ttu-id="467c0-221">**[データベース ファイルの解放された領域を保持する]**</span><span class="sxs-lookup"><span data-stu-id="467c0-221">**Retain freed space in database files**</span></span>  
     <span data-ttu-id="467c0-222">データベースは連続するページに圧縮されますが、ページの割り当ては解除されず、データベース ファイルは圧縮されません。</span><span class="sxs-lookup"><span data-stu-id="467c0-222">The database is condensed to contiguous pages but the pages are not deallocated, and the database files do not shrink.</span></span> <span data-ttu-id="467c0-223">データベースを再度展開することが予想され、領域を再割り当てしない場合に、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="467c0-223">Use this option if you expect the database to expand again, and you do not want to reallocate space.</span></span> <span data-ttu-id="467c0-224">このオプションを指定した場合、データベース ファイルを可能な限り圧縮する動作は行われません。</span><span class="sxs-lookup"><span data-stu-id="467c0-224">With this option, the database files do not shrink as much as possible.</span></span> <span data-ttu-id="467c0-225">NOTRUNCATE オプションが使用されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-225">This uses the NOTRUNCATE option.</span></span>  
  
     <span data-ttu-id="467c0-226">**[解放された領域をオペレーティング システムに返す]**</span><span class="sxs-lookup"><span data-stu-id="467c0-226">**Return freed space to operating system**</span></span>  
     <span data-ttu-id="467c0-227">データベースは連続するページに圧縮され、そのページが他のプログラムで使用できるようにオペレーティング システムに返されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-227">The database is condensed to contiguous pages and the pages are released back to the operating system for use by other programs.</span></span> <span data-ttu-id="467c0-228">データベース ファイルは可能な限り圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-228">This database files shrink as much as possible.</span></span> <span data-ttu-id="467c0-229">TRUNCATEONLY オプションが使用されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-229">This uses the TRUNCATEONLY option.</span></span> <span data-ttu-id="467c0-230">既定のオプションです。</span><span class="sxs-lookup"><span data-stu-id="467c0-230">This is the default option.</span></span>  
  
#### <a name="define-the-index-tasks"></a><span data-ttu-id="467c0-231">インデックスのタスクを定義する</span><span class="sxs-lookup"><span data-stu-id="467c0-231">Define the Index Tasks</span></span>  
  
1.  <span data-ttu-id="467c0-232">**[インデックスの再構成タスクの定義]** ページで、インデックス ページをより効率的な検索順に移動する 1 つまたは複数のサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-232">On the **Define Reorganize Index Task** page, select the server or servers where you'll be moving index pages into a more efficient search order.</span></span> <span data-ttu-id="467c0-233">このタスクでは `ALTER INDEX ... REORGANIZE` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="467c0-233">This task uses the `ALTER INDEX ... REORGANIZE` statement.</span></span> <span data-ttu-id="467c0-234">詳細については、「[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="467c0-234">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span> <span data-ttu-id="467c0-235">完了したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-235">When complete, click **Next**.</span></span>  
  
     <span data-ttu-id="467c0-236">このページで使用できるオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="467c0-236">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="467c0-237">**[データベース]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-237">**Databases** list</span></span>  
     <span data-ttu-id="467c0-238">このタスクで操作するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-238">Specify the databases affected by this task.</span></span> <span data-ttu-id="467c0-239">この一覧で利用可能なオプションの詳細については、上の手順 9. を参照してください。</span><span class="sxs-lookup"><span data-stu-id="467c0-239">See step 9, above, for more information on the available options on this list.</span></span>  
  
     <span data-ttu-id="467c0-240">**[オブジェクト]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-240">**Object** list</span></span>  
     <span data-ttu-id="467c0-241">**[選択]** ボックスの一覧で、テーブル、ビュー、または両方を表示するように制限します。</span><span class="sxs-lookup"><span data-stu-id="467c0-241">Limit the **Selection** list to display tables, views, or both.</span></span> <span data-ttu-id="467c0-242">この一覧は、上の **[データベース]** ボックスの一覧で 1 つのデータベースが選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-242">This list is only available if a single database is chosen from the **Databases** list above.</span></span>  
  
     <span data-ttu-id="467c0-243">**[選択]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-243">**Selection** list</span></span>  
     <span data-ttu-id="467c0-244">このタスクの対象とするテーブルまたはインデックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-244">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="467c0-245">[オブジェクト] ボックスで **[テーブルとビュー]** が選択されている場合は、このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="467c0-245">Not available when **Tables and Views** is selected in the Object box.</span></span>  
  
     <span data-ttu-id="467c0-246">**[ラージ オブジェクトを圧縮する]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-246">**Compact large objects** check box</span></span>  
     <span data-ttu-id="467c0-247">可能であれば、テーブルとビューに対する領域の割り当てを解除します。</span><span class="sxs-lookup"><span data-stu-id="467c0-247">Deallocate space for tables and views when possible.</span></span> <span data-ttu-id="467c0-248">このオプションでは `ALTER INDEX ... LOB_COMPACTION = ON`を使用します。</span><span class="sxs-lookup"><span data-stu-id="467c0-248">This option uses `ALTER INDEX ... LOB_COMPACTION = ON`.</span></span>  
  
2.  <span data-ttu-id="467c0-249">**[インデックスの再構築タスクの定義]** ページで、複数のインデックスを再構築する 1 つまたは複数のデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-249">On the **Define Rebuild Index Task** page, select the database or databases where you'll be re-creating multiple indexes.</span></span> <span data-ttu-id="467c0-250">このタスクでは `ALTER INDEX ... REBUILD PARTITION` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="467c0-250">This task uses the `ALTER INDEX ... REBUILD PARTITION` statement.</span></span> <span data-ttu-id="467c0-251">詳細については、「[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)」を参照してください。完了したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-251">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).) When complete, click **Next**.</span></span>  
  
     <span data-ttu-id="467c0-252">このページで使用できるオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="467c0-252">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="467c0-253">**[データベース]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-253">**Databases** list</span></span>  
     <span data-ttu-id="467c0-254">このタスクで操作するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-254">Specify the databases affected by this task.</span></span> <span data-ttu-id="467c0-255">この一覧で利用可能なオプションの詳細については、上の手順 9. を参照してください。</span><span class="sxs-lookup"><span data-stu-id="467c0-255">See step 9, above, for more information on the available options on this list.</span></span>  
  
     <span data-ttu-id="467c0-256">**[オブジェクト]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-256">**Object** list</span></span>  
     <span data-ttu-id="467c0-257">**[選択]** ボックスの一覧で、テーブル、ビュー、または両方を表示するように制限します。</span><span class="sxs-lookup"><span data-stu-id="467c0-257">Limit the **Selection** list to display tables, views, or both.</span></span> <span data-ttu-id="467c0-258">この一覧は、上の **[データベース]** ボックスの一覧で 1 つのデータベースが選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-258">This list is only available if a single database is chosen from the **Databases** list above.</span></span>  
  
     <span data-ttu-id="467c0-259">**[選択]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-259">**Selection** list</span></span>  
     <span data-ttu-id="467c0-260">このタスクの対象とするテーブルまたはインデックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-260">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="467c0-261">[オブジェクト] ボックスで **[テーブルとビュー]** が選択されている場合は、このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="467c0-261">Not available when **Tables and Views** is selected in the Object box.</span></span>  
  
     <span data-ttu-id="467c0-262">**[空き領域のオプション]** 領域</span><span class="sxs-lookup"><span data-stu-id="467c0-262">**Free space options** area</span></span>  
     <span data-ttu-id="467c0-263">インデックスとテーブルに FILL FACTOR を適用するためのオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="467c0-263">Presents options for applying fill factor to indexes and tables.</span></span>  
  
     <span data-ttu-id="467c0-264">**[ページごとの既定の空き領域]**</span><span class="sxs-lookup"><span data-stu-id="467c0-264">**Default free space per page**</span></span>  
     <span data-ttu-id="467c0-265">既定の空き領域を使用してページを再構成します。</span><span class="sxs-lookup"><span data-stu-id="467c0-265">Reorganizes the pages with the default amount of free space.</span></span> <span data-ttu-id="467c0-266">データベース内のテーブルに定義されているインデックスを削除し、インデックスの作成時に指定された FILL FACTOR を使用して、新しいインデックスを再作成します。</span><span class="sxs-lookup"><span data-stu-id="467c0-266">This will drop the indexes on the tables in the database and re-create them with the fill factor that was specified when the indexes were created.</span></span> <span data-ttu-id="467c0-267">既定のオプションです。</span><span class="sxs-lookup"><span data-stu-id="467c0-267">This is the default option.</span></span>  
  
     <span data-ttu-id="467c0-268">**[ページごとの空き領域を変更する]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-268">**Change free space per page to** box</span></span>  
     <span data-ttu-id="467c0-269">データベース内のテーブルに定義されているインデックスを削除し、指定した割合の空き領域が各インデックス ページに確保されるように自動的に計算される FILL FACTOR の値を使用してインデックスを再作成します。</span><span class="sxs-lookup"><span data-stu-id="467c0-269">Drop the indexes on the tables in the database and re-create them with a new, automatically calculated fill factor, thereby reserving the specified amount of free space on the index pages.</span></span> <span data-ttu-id="467c0-270">指定するパーセント値を大きくすると、インデックス ページに確保される空き領域が増えて、より多くのデータをインデックスに追加できるようになります。</span><span class="sxs-lookup"><span data-stu-id="467c0-270">The higher the percentage, the more free space is reserved on the index pages, and the larger the index grows.</span></span> <span data-ttu-id="467c0-271">有効値は、0 ～ 100 です。</span><span class="sxs-lookup"><span data-stu-id="467c0-271">Valid values are from 0 through 100.</span></span> <span data-ttu-id="467c0-272">`FILLFACTOR` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="467c0-272">Uses the `FILLFACTOR` option.</span></span>  
  
     <span data-ttu-id="467c0-273">**[詳細設定オプション]** 領域</span><span class="sxs-lookup"><span data-stu-id="467c0-273">**Advanced options** area</span></span>  
     <span data-ttu-id="467c0-274">インデックスの並べ替えと再作成を行うためのオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="467c0-274">Presents additional options for sorting indexes and reindexing.</span></span>  
  
     <span data-ttu-id="467c0-275">**[tempdb の結果を並べ替える]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-275">**Sort results in tempdb** check box</span></span>  
     <span data-ttu-id="467c0-276">`SORT_IN_TEMPDB` オプションを使用して、インデックスの作成中に生成される並べ替えの中間結果を一時的に格納する場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-276">Uses the `SORT_IN_TEMPDB` option which determines where the intermediate sort results, generated during index creation, are temporarily stored.</span></span> <span data-ttu-id="467c0-277">並べ替え操作が必要ない場合、または並べ替えをメモリ上で実行できる場合、 `SORT_IN_TEMPDB` オプションは無視されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-277">If a sort operation is not required, or if the sort can be performed in memory, the `SORT_IN_TEMPDB` option is ignored.</span></span>  
  
     <span data-ttu-id="467c0-278">**[インデックスの再作成中にオンラインのインデックスを保持する]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-278">**Keep index online while reindexing** check box</span></span>  
     <span data-ttu-id="467c0-279">`ONLINE` オプションを使用します。これにより、インデックス操作の実行中に、ユーザーは基になるテーブルまたはクラスター化インデックス データ、および任意の関連付けられた非クラスター化インデックスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="467c0-279">Uses the `ONLINE` option which allows users to access the underlying table or clustered index data and any associated nonclustered indexes during index operations.</span></span> <span data-ttu-id="467c0-280">このオプションを選択すると、インデックスを再構築するための追加のオプションとして、オンラインの再構築が許可されない **[インデックスを再構築しない]** と **[オフラインでインデックスを再構築する]** が有効になります。</span><span class="sxs-lookup"><span data-stu-id="467c0-280">Selecting this option activates additional options for rebuilding indexes that do not allow for online rebuilds: **Do not rebuild indexes** and **Rebuild indexes offline**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="467c0-281">オンラインでのインデックス操作は、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="467c0-281">Online index operations are not available in every edition of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="467c0-282">詳しくは「 [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="467c0-282">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
#### <a name="define-the-update-statistics-task"></a><span data-ttu-id="467c0-283">統計の更新タスクを定義する</span><span class="sxs-lookup"><span data-stu-id="467c0-283">Define the Update Statistics Task</span></span>  
  
1.  <span data-ttu-id="467c0-284">**[統計の更新タスクの定義]** ページで、テーブルおよびインデックスの統計を更新する 1 つまたは複数のデータベースを定義します。</span><span class="sxs-lookup"><span data-stu-id="467c0-284">On the **Define Update Statistics Task** page, define the database or databases on which table and index statistics will be updated.</span></span> <span data-ttu-id="467c0-285">このタスクでは `UPDATE STATISTICS` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="467c0-285">This task uses the `UPDATE STATISTICS` statement.</span></span> <span data-ttu-id="467c0-286">詳細については、「[UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql)」を参照してください。完了したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-286">For more information, see [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql) When finished, click **Next**</span></span>  
  
     <span data-ttu-id="467c0-287">このページで使用できるオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="467c0-287">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="467c0-288">**[データベース]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-288">**Databases** list</span></span>  
     <span data-ttu-id="467c0-289">このタスクで操作するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-289">Specify the databases affected by this task.</span></span> <span data-ttu-id="467c0-290">この一覧で利用可能なオプションの詳細については、上の手順 9. を参照してください。</span><span class="sxs-lookup"><span data-stu-id="467c0-290">See step 9, above, for more information on the available options on this list.</span></span>  
  
     <span data-ttu-id="467c0-291">**[オブジェクト]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-291">**Object** list</span></span>  
     <span data-ttu-id="467c0-292">**[選択]** ボックスの一覧で、テーブル、ビュー、または両方を表示するように制限します。</span><span class="sxs-lookup"><span data-stu-id="467c0-292">Limit the **Selection** list to display tables, views, or both.</span></span> <span data-ttu-id="467c0-293">この一覧は、上の **[データベース]** ボックスの一覧で 1 つのデータベースが選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-293">This list is only available if a single database is chosen from the **Databases** list above.</span></span>  
  
     <span data-ttu-id="467c0-294">**[選択]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-294">**Selection** list</span></span>  
     <span data-ttu-id="467c0-295">このタスクの対象とするテーブルまたはインデックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-295">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="467c0-296">[オブジェクト] ボックスで **[テーブルとビュー]** が選択されている場合は、このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="467c0-296">Not available when **Tables and Views** is selected in the Object box.</span></span>  
  
     <span data-ttu-id="467c0-297">**[すべての既存の統計]**</span><span class="sxs-lookup"><span data-stu-id="467c0-297">**All existing statistics**</span></span>  
     <span data-ttu-id="467c0-298">列とインデックスの統計を両方とも更新します。</span><span class="sxs-lookup"><span data-stu-id="467c0-298">Update statistics for both columns and indexes.</span></span>  
  
     <span data-ttu-id="467c0-299">**[列統計のみ]**</span><span class="sxs-lookup"><span data-stu-id="467c0-299">**Column statistics only**</span></span>  
     <span data-ttu-id="467c0-300">列統計のみを更新します。</span><span class="sxs-lookup"><span data-stu-id="467c0-300">Only update column statistics.</span></span> <span data-ttu-id="467c0-301">`WITH COLUMNS` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="467c0-301">Uses the `WITH COLUMNS` option.</span></span>  
  
     <span data-ttu-id="467c0-302">**[インデックス統計のみ]**</span><span class="sxs-lookup"><span data-stu-id="467c0-302">**Index statistics only**</span></span>  
     <span data-ttu-id="467c0-303">インデックス統計のみを更新します。</span><span class="sxs-lookup"><span data-stu-id="467c0-303">Only update index statistics.</span></span> <span data-ttu-id="467c0-304">`WITH INDEX` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="467c0-304">Uses the `WITH INDEX` option.</span></span>  
  
     <span data-ttu-id="467c0-305">**[スキャンの種類]**</span><span class="sxs-lookup"><span data-stu-id="467c0-305">**Scan type**</span></span>  
     <span data-ttu-id="467c0-306">更新された統計情報を収集するスキャンの種類です。</span><span class="sxs-lookup"><span data-stu-id="467c0-306">Type of scan used to gather updated statistics.</span></span>  
  
     <span data-ttu-id="467c0-307">**[フル スキャン]**</span><span class="sxs-lookup"><span data-stu-id="467c0-307">**Full scan**</span></span>  
     <span data-ttu-id="467c0-308">統計を収集する際、テーブルまたはビューのすべての行を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="467c0-308">Read all rows in the table or view to gather the statistics.</span></span>  
  
     <span data-ttu-id="467c0-309">**[サンプル対象]**</span><span class="sxs-lookup"><span data-stu-id="467c0-309">**Sample by**</span></span>  
     <span data-ttu-id="467c0-310">大きなテーブルやビューの統計を収集するときにサンプリングする、テーブルまたはインデックス付きビューの割合や行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-310">Specify the percentage of the table or indexed view, or the number of rows to sample when collecting statistics for larger tables or views.</span></span>  
  
#### <a name="define-the-history-cleanup-task"></a><span data-ttu-id="467c0-311">履歴クリーンアップ タスクを定義する</span><span class="sxs-lookup"><span data-stu-id="467c0-311">Define the History Cleanup Task</span></span>  
  
1.  <span data-ttu-id="467c0-312">**[履歴クリーンアップ タスクの定義]** ページで、古いタスク履歴を破棄する 1 つまたは複数のデータベースを定義します。</span><span class="sxs-lookup"><span data-stu-id="467c0-312">On the **Define History Cleanup Task** page, define the database or databases where you want to discard old task history.</span></span> <span data-ttu-id="467c0-313">このタスクでは、 `EXEC sp_purge_jobhistory`、 `EXEC sp_maintplan_delete_log`、および `EXEC sp_delete_backuphistory` ステートメントを使用して、 **msdb** テーブルから履歴情報を削除します。</span><span class="sxs-lookup"><span data-stu-id="467c0-313">This task uses the `EXEC sp_purge_jobhistory`, `EXEC sp_maintplan_delete_log`, and `EXEC sp_delete_backuphistory` statements to remove history information from the **msdb** tables.</span></span> <span data-ttu-id="467c0-314">完了したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-314">When finished, click **Next**.</span></span>  
  
     <span data-ttu-id="467c0-315">このページで使用できるオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="467c0-315">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="467c0-316">**[削除する履歴データを選択]**</span><span class="sxs-lookup"><span data-stu-id="467c0-316">**Select the historical data to delete**</span></span>  
     <span data-ttu-id="467c0-317">削除するタスク データの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-317">Chose the type of task data to delete/</span></span>  
  
     <span data-ttu-id="467c0-318">**[バックアップおよび復元の履歴]**</span><span class="sxs-lookup"><span data-stu-id="467c0-318">**Backup and restore history**</span></span>  
     <span data-ttu-id="467c0-319">最新のバックアップを作成したときのレコードを保存しておくと、データベースの復元時に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で復元プランを作成するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="467c0-319">Retaining records of when recent backups were created can help [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] create a recovery plan when you want to restore a database.</span></span> <span data-ttu-id="467c0-320">保存期間は、データベースの完全バックアップの実行間隔以上にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="467c0-320">The retention period should be at least the frequency of full database backups.</span></span>  
  
     <span data-ttu-id="467c0-321">**[SQL Server エージェントのジョブ履歴]**</span><span class="sxs-lookup"><span data-stu-id="467c0-321">**SQL Server Agent Job history**</span></span>  
     <span data-ttu-id="467c0-322">この履歴を利用して、失敗したジョブをトラブルシューティングしたり、データベース アクションの発生原因を調べたりできます。</span><span class="sxs-lookup"><span data-stu-id="467c0-322">This history can help you troubleshoot failed jobs, or determine why database actions occurred.</span></span>  
  
     <span data-ttu-id="467c0-323">**[メンテナンス プランの履歴]**</span><span class="sxs-lookup"><span data-stu-id="467c0-323">**Maintenance Plan history**</span></span>  
     <span data-ttu-id="467c0-324">この履歴を利用して、失敗したメンテナンス プラン ジョブをトラブルシューティングしたり、データベース アクションの発生原因を調べたりできます。</span><span class="sxs-lookup"><span data-stu-id="467c0-324">This history can help you troubleshoot failed maintenance plan jobs, or determine why database actions occurred.</span></span>  
  
     <span data-ttu-id="467c0-325">**[これより古い履歴データの削除]**</span><span class="sxs-lookup"><span data-stu-id="467c0-325">**Remove historical data older than**</span></span>  
     <span data-ttu-id="467c0-326">削除するアイテムの古さを指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-326">Specify age of items that you want to delete.</span></span> <span data-ttu-id="467c0-327">**[時間]** , **[日]** , **[週]** (既定値)、 **[月]** 、または **[年]** を選択できます。</span><span class="sxs-lookup"><span data-stu-id="467c0-327">You can specify **Hour(s)**, **Day(s)**, **Week(s)** (the default), **Month(s)**, or **Year(s)**</span></span>  
  
#### <a name="define-the-execute-agent-job-task"></a><span data-ttu-id="467c0-328">エージェント ジョブ実行タスクを定義する</span><span class="sxs-lookup"><span data-stu-id="467c0-328">Define the Execute Agent Job Task</span></span>  
  
1.  <span data-ttu-id="467c0-329">**[エージェント ジョブ実行タスクの定義]** ページの **[使用できる SQL Server エージェント ジョブ]** で、実行する 1 つまたは複数のジョブを選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-329">On the **Define Execute Agent Job Task** page, under **Available SQL Server Agent jobs**, choose the job or jobs to run.</span></span> <span data-ttu-id="467c0-330">SQL エージェント ジョブが存在しない場合は、このオプションを利用できません。</span><span class="sxs-lookup"><span data-stu-id="467c0-330">This option will not be available if you have no SQL Agent jobs.</span></span> <span data-ttu-id="467c0-331">このタスクでは `EXEC sp_start_job` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="467c0-331">This task uses the `EXEC sp_start_job` statement.</span></span> <span data-ttu-id="467c0-332">詳細については、「[sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)」を参照してください。完了したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-332">For more information, see [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)When finished, click **Next**.</span></span>  
  
#### <a name="define-backup-tasks"></a><span data-ttu-id="467c0-333">バックアップ タスクを定義する</span><span class="sxs-lookup"><span data-stu-id="467c0-333">Define Backup Tasks</span></span>  
  
1.  <span data-ttu-id="467c0-334">**[データベースのバックアップ (完全) タスクの定義]** ページで、完全バックアップを実行する 1 つまたは複数のデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-334">On the **Define Backup Database (Full) Task** page, select the database or databases on which to run a full backup.</span></span> <span data-ttu-id="467c0-335">このタスクでは `BACKUP DATABASE` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="467c0-335">This task uses the `BACKUP DATABASE` statement.</span></span> <span data-ttu-id="467c0-336">詳細については、「 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="467c0-336">For more information, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span> <span data-ttu-id="467c0-337">完了したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-337">When finished, click **Next**.</span></span>  
  
     <span data-ttu-id="467c0-338">このページで使用できるオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="467c0-338">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="467c0-339">**[バックアップの種類]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-339">**Backup type** list</span></span>  
     <span data-ttu-id="467c0-340">実行するバックアップの種類を表示します。</span><span class="sxs-lookup"><span data-stu-id="467c0-340">Displays the type of backup to be performed.</span></span> <span data-ttu-id="467c0-341">読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="467c0-341">This is read-only.</span></span>  
  
     <span data-ttu-id="467c0-342">**[データベース]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-342">**Databases** list</span></span>  
     <span data-ttu-id="467c0-343">このタスクで操作するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-343">Specify the databases affected by this task.</span></span> <span data-ttu-id="467c0-344">この一覧で利用可能なオプションの詳細については、上の手順 9. を参照してください。</span><span class="sxs-lookup"><span data-stu-id="467c0-344">See step 9, above, for more information on the available options on this list.</span></span>  
  
     <span data-ttu-id="467c0-345">**[バックアップ コンポーネント]**</span><span class="sxs-lookup"><span data-stu-id="467c0-345">**Backup component**</span></span>  
     <span data-ttu-id="467c0-346">データベース全体をバックアップするには、 **[データベース]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-346">Select **Database** to back up the entire database.</span></span> <span data-ttu-id="467c0-347">データベースの一部だけをバックアップするには、 **[ファイルとファイル グループ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-347">Select **File and filegroups** to back up only a portion of the database.</span></span> <span data-ttu-id="467c0-348">後者のオプションを選択した場合は、ファイル名またはファイル グループ名を指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-348">If selected, provide the file or filegroup name.</span></span> <span data-ttu-id="467c0-349">**[データベース]** ボックスで複数のデータベースを選択した場合、 **[バックアップ コンポーネント]** には **[データベース]** のみを指定できます。</span><span class="sxs-lookup"><span data-stu-id="467c0-349">When multiple databases are selected in the **Databases** box, only specify **Databases** for the **Backup components**.</span></span> <span data-ttu-id="467c0-350">ファイルまたはファイル グループのバックアップを実行するには、データベースごとにタスクを作成します。</span><span class="sxs-lookup"><span data-stu-id="467c0-350">To perform file or filegroup backups, create a task for each database.</span></span> <span data-ttu-id="467c0-351">これらのオプションは、上の **[データベース]** ボックスの一覧で 1 つのデータベースが選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-351">These options are only available if a single database is chosen from the **Databases** list above.</span></span>  
  
     <span data-ttu-id="467c0-352">**[バックアップ セットの有効期限]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-352">**Backup set will expire** check box</span></span>  
     <span data-ttu-id="467c0-353">このバックアップのバックアップ セットがいつ上書きできるようになるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-353">Specifies when the backup set for this backup can be overwritten.</span></span> <span data-ttu-id="467c0-354">**[期間指定]** を選択して期限切れまでの日数を入力するか、または **[日時指定]** を選択して有効期限の日付を入力します。</span><span class="sxs-lookup"><span data-stu-id="467c0-354">Select **After** and enter a number of days to expiration, or select **On** and enter a date of expiration.</span></span> <span data-ttu-id="467c0-355">**[URL]** がバックアップ先として選択された場合、このオプションは無効です。</span><span class="sxs-lookup"><span data-stu-id="467c0-355">This option is disabled if **URL** is selected as the backup destination.</span></span>  
  
     <span data-ttu-id="467c0-356">**[バックアップ先]**</span><span class="sxs-lookup"><span data-stu-id="467c0-356">**Back up to**</span></span>  
     <span data-ttu-id="467c0-357">データベースをバックアップするメディアを指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-357">Specifies the medium on which to back up the database.</span></span> <span data-ttu-id="467c0-358">**[ディスク]** 、 **[テープ]** 、または **[URL]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-358">Select **Disk**, **Tape**, or **URL**.</span></span> <span data-ttu-id="467c0-359">データベースを格納しているコンピューターに接続したテープ デバイスのみを利用できます。</span><span class="sxs-lookup"><span data-stu-id="467c0-359">Only tape devices attached to the computer containing the database are available.</span></span>  
  
     <span data-ttu-id="467c0-360">**[1 つ以上のファイルにデータベースをバックアップする]**</span><span class="sxs-lookup"><span data-stu-id="467c0-360">**Back up database(s) across one or more files**</span></span>  
     <span data-ttu-id="467c0-361">**[追加]** をクリックして **[バックアップ先の選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="467c0-361">Click **Add** to open the **Select Backup Destination** dialog box.</span></span> <span data-ttu-id="467c0-362">バックアップ先として [URL] を選択した場合、このオプションは無効になります。</span><span class="sxs-lookup"><span data-stu-id="467c0-362">This option is disabled if you selected URL as the backup destination.</span></span>  
  
     <span data-ttu-id="467c0-363">ボックスからファイルを削除するには、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-363">Click **Remove** to remove a file from the box.</span></span>  
  
     <span data-ttu-id="467c0-364">ファイル ヘッダーを読み取り、ファイルの現在のバックアップ内容を表示するには、 **[コンテンツ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-364">Click **Contents** to read the file header and display the current backup contents of the file.</span></span>  
  
     <span data-ttu-id="467c0-365">**[バックアップ先の選択]** ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-365">**Select Backup Destination** dialog box</span></span>  
     <span data-ttu-id="467c0-366">バックアップ先として、ファイル、テープ、またはバックアップ デバイスを選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-366">Select the file, tape drive, or backup device for the backup destination.</span></span> <span data-ttu-id="467c0-367">バックアップ先として [URL] を選択した場合、このオプションは無効になります。</span><span class="sxs-lookup"><span data-stu-id="467c0-367">This option is disabled if you selected URL as the backup destination.</span></span>  
  
     <span data-ttu-id="467c0-368">**[バックアップ ファイルが存在する場合に行う操作]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-368">**If backup files exist** list</span></span>  
     <span data-ttu-id="467c0-369">既存のバックアップを処理する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-369">Specify how to handle existing backups.</span></span> <span data-ttu-id="467c0-370">ファイル内またはテープ上の既存のバックアップの後に新しいバックアップを追加するには、 **[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-370">Select **Append** to add the new backups after any existing backups in the file or on the tape.</span></span> <span data-ttu-id="467c0-371">ファイルまたはテープの古い内容を削除し、この新しいバックアップで置き換えるには、 **[上書き]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-371">Select **Overwrite** to remove the old content of a file or tape, and replace it with this new backup.</span></span>  
  
     <span data-ttu-id="467c0-372">**[すべてのデータベースにバックアップ ファイルを作成する]**</span><span class="sxs-lookup"><span data-stu-id="467c0-372">**Create a backup file for every database**</span></span>  
     <span data-ttu-id="467c0-373">[フォルダー] ボックスで指定された場所にバックアップ ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="467c0-373">Create a backup file in the location specified in the folder box.</span></span> <span data-ttu-id="467c0-374">選択されたデータベースごとに、1 つのファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-374">One file is created for each database selected.</span></span> <span data-ttu-id="467c0-375">バックアップ先として [URL] を選択した場合、このオプションは無効になります。</span><span class="sxs-lookup"><span data-stu-id="467c0-375">This option is disabled if you selected URL as the backup destination.</span></span>  
  
     <span data-ttu-id="467c0-376">**[データベースごとにサブディレクトリを作成する]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-376">**Create a sub-directory for each database** check box</span></span>  
     <span data-ttu-id="467c0-377">メンテナンス プランの一部としてバックアップされるデータベースごとに、データベース バックアップを格納するサブディレクトリを、指定されたディスク ディレクトリの下に作成します。</span><span class="sxs-lookup"><span data-stu-id="467c0-377">Create a sub-directory under the specified disk directory that contains the database backup for each database being backed up as part of the maintenance plan.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="467c0-378">サブディレクトリには、親ディレクトリから権限が継承されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-378">The sub-directory will inherit permissions from the parent directory.</span></span> <span data-ttu-id="467c0-379">不正アクセスを防ぐには、権限を制限してください。</span><span class="sxs-lookup"><span data-stu-id="467c0-379">Restrict permissions to avoid unauthorized access.</span></span>  
  
     <span data-ttu-id="467c0-380">**[フォルダー]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-380">**Folder** box</span></span>  
     <span data-ttu-id="467c0-381">自動的に作成されたデータベース ファイルを格納するフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-381">Specify the folder to contain the automatically created database files.</span></span> <span data-ttu-id="467c0-382">バックアップ先として [URL] を選択した場合、このオプションは無効になります。</span><span class="sxs-lookup"><span data-stu-id="467c0-382">This option is disabled if you selected URL as the backup destination.</span></span>  
  
     <span data-ttu-id="467c0-383">**[SQL 資格情報]**</span><span class="sxs-lookup"><span data-stu-id="467c0-383">**SQL Credential**</span></span>  
     <span data-ttu-id="467c0-384">Azure Storage への認証に使用する SQL 資格情報を選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-384">Select a SQL Credential used to authenticate to Azure Storage.</span></span> <span data-ttu-id="467c0-385">使用できる既存の SQL 資格情報がない場合は、 **[作成]** ボタンをクリックして新しい SQL 資格情報を作成します。</span><span class="sxs-lookup"><span data-stu-id="467c0-385">If you do not have an existing SQL Credential you can use, click the **Create** button to create a new SQL Credential.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="467c0-386">**[作成]** をクリックすると開くダイアログでは、サブスクリプションの管理証明書または公開プロファイルが求められます。</span><span class="sxs-lookup"><span data-stu-id="467c0-386">The dialog that opens when you click **Create** requires a management certificate or the publishing profile for the subscription.</span></span> <span data-ttu-id="467c0-387">管理証明書または公開プロファイルにアクセスできない場合は、Transact-SQL または SQL Server Management Studio を使用してストレージ アカウント名とアクセス キーの情報を指定し、SQL 資格情報を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="467c0-387">If you do not have access to the management certificate or publishing profile, you can create a SQL Credential by specifying the storage account name and access key information using Transact-SQL or SQL Server Management Studio.</span></span> <span data-ttu-id="467c0-388">Transact-sql を使用して資格情報を作成する方法については、「」のサンプル[コードを参照](../security/authentication-access/create-a-credential.md#Credential)してください。</span><span class="sxs-lookup"><span data-stu-id="467c0-388">See the sample code in the [To create a credential](../security/authentication-access/create-a-credential.md#Credential) topic to create a credential using Transact-SQL.</span></span> <span data-ttu-id="467c0-389">または SQL Server Management Studio を使用して、データベース エンジン インスタンスから、 **[セキュリティ]** を右クリックし、 **[新規作成]**、 **[資格情報]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-389">Alternatively, using SQL Server Management Studio, from the database engine instance, right click **Security**, select **New**, and select **Credential**.</span></span> <span data-ttu-id="467c0-390">**[ID]** にストレージ アカウント名、 **[パスワード]** にアクセス キーを指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-390">Specify the storage account name for **Identity** and the access key in the **Password** field.</span></span>  
  
     <span data-ttu-id="467c0-391">**[Azure ストレージ コンテナー]**</span><span class="sxs-lookup"><span data-stu-id="467c0-391">**Azure storage container**</span></span>  
     <span data-ttu-id="467c0-392">Azure ストレージ コンテナーの名前を指定します</span><span class="sxs-lookup"><span data-stu-id="467c0-392">Specify the name of the Azure storage container</span></span>  
  
     <span data-ttu-id="467c0-393">**[URL プレフィックス]**</span><span class="sxs-lookup"><span data-stu-id="467c0-393">**URL prefix:**</span></span>  
     <span data-ttu-id="467c0-394">これは、SQL 資格情報に格納されているストレージ アカウント情報と、指定した Azure ストレージ コンテナー名に基づいて自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-394">This is automatically generated based on the storage account information stored in the SQL Credential, and Azure storage container name you specified.</span></span> <span data-ttu-id="467c0-395">**\<storage account>.blob.core.windows.net** 以外の形式を使ったドメインを使用している場合を除き、このフィールドの情報は編集しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="467c0-395">We recommend that you do not edit the information in this field unless you are using a domain that uses a format other than **\<storage account>.blob.core.windows.net**.</span></span>  
  
     <span data-ttu-id="467c0-396">**[バックアップ ファイルの拡張子]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-396">**Backup file extension** box</span></span>  
     <span data-ttu-id="467c0-397">バックアップ ファイルに使用する拡張子を指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-397">Specify the extension to use for the backup files.</span></span> <span data-ttu-id="467c0-398">既定の拡張子は .bak です。</span><span class="sxs-lookup"><span data-stu-id="467c0-398">The default is .bak.</span></span>  
  
     <span data-ttu-id="467c0-399">**[バックアップの整合性を検証する]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-399">**Verify backup integrity** check box</span></span>  
     <span data-ttu-id="467c0-400">バックアップ セットが完全で、すべてのボリュームが読み取り可能であることを検証します。</span><span class="sxs-lookup"><span data-stu-id="467c0-400">Verify that the backup set is complete and that all volumes are readable.</span></span>  
  
     <span data-ttu-id="467c0-401">**バックアップの暗号化**</span><span class="sxs-lookup"><span data-stu-id="467c0-401">**Backup Encryption**</span></span>  
     <span data-ttu-id="467c0-402">暗号化されたバックアップを作成するには、 **[バックアップ ファイルを暗号化する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="467c0-402">To create an encrypted backup, check the **Encrypt backup** check box.</span></span> <span data-ttu-id="467c0-403">暗号化手順に使用する暗号化アルゴリズムを選択し、既存の証明書または非対称キーの一覧から証明書または非対称キーを指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-403">Select an encryption algorithm to use for the encryption step, and provide a Certificate or Asymmetric key from a list of existing certificates or asymmetric keys.</span></span> <span data-ttu-id="467c0-404">暗号化に使用できるアルゴリズムは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="467c0-404">The available algorithms for encryption are:</span></span>  
  
    -   <span data-ttu-id="467c0-405">AES 128</span><span class="sxs-lookup"><span data-stu-id="467c0-405">AES 128</span></span>  
  
    -   <span data-ttu-id="467c0-406">AES 192</span><span class="sxs-lookup"><span data-stu-id="467c0-406">AES 192</span></span>  
  
    -   <span data-ttu-id="467c0-407">AES 256</span><span class="sxs-lookup"><span data-stu-id="467c0-407">AES 256</span></span>  
  
    -   <span data-ttu-id="467c0-408">Triple DES</span><span class="sxs-lookup"><span data-stu-id="467c0-408">Triple DES</span></span>  
  
     <span data-ttu-id="467c0-409">既存のバックアップ セットに追加することを選択した場合、暗号化オプションは無効になります。</span><span class="sxs-lookup"><span data-stu-id="467c0-409">The encryption option is disabled if you selected to append to existing backup set.</span></span>  
  
     <span data-ttu-id="467c0-410">証明書またはキーをバックアップし、暗号化されたバックアップとは別の場所に保管することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="467c0-410">It is recommended practice to back up your certificate or keys and store them in a different location than the backup you encrypted.</span></span>  
  
     <span data-ttu-id="467c0-411">拡張キー管理 (EKM) に存在するキーのみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="467c0-411">Only keys residing in the Extensible Key Management (EKM) are supported.</span></span>  
  
     <span data-ttu-id="467c0-412">**[バックアップの圧縮の設定]**  ボックスの一覧</span><span class="sxs-lookup"><span data-stu-id="467c0-412">**Set backup compression**  list</span></span>  
     <span data-ttu-id="467c0-413">[!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (またはそれ以降のバージョン) で、 [バックアップの圧縮](../backup-restore/backup-compression-sql-server.md) の値を次の中から 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-413">In [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (or later versions), select one the following [backup compression](../backup-restore/backup-compression-sql-server.md) values:</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="467c0-414">**[既定のサーバー設定を使用する]**</span><span class="sxs-lookup"><span data-stu-id="467c0-414">**Use the default server setting**</span></span>|<span data-ttu-id="467c0-415">オンにすると、サーバー レベルの既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-415">Click to use the server-level default.</span></span> <span data-ttu-id="467c0-416">この既定値は、 **backup compression default** サーバー構成オプションで設定されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-416">This default is set by the **backup compression default** server-configuration option.</span></span> <span data-ttu-id="467c0-417">このオプションの現在の設定を表示する方法については、「 [backup compression default サーバー構成オプションの表示または構成](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="467c0-417">For information about how to view the current setting of this option, see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>|  
    |<span data-ttu-id="467c0-418">**[バックアップを圧縮する]**</span><span class="sxs-lookup"><span data-stu-id="467c0-418">**Compress backup**</span></span>|<span data-ttu-id="467c0-419">オンにすると、サーバー レベルの既定値に関係なく、バックアップが圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-419">Click to compress the backup, regardless of the server-level default.</span></span><br /><br /> <span data-ttu-id="467c0-420">**\*\* 重要 \*\*** 既定の設定では、圧縮によって CPU 使用率が著しく増加し、圧縮処理によって CPU がさらに消費されるために、同時に実行される操作が悪影響を受ける場合があります。</span><span class="sxs-lookup"><span data-stu-id="467c0-420">**\*\* Important \*\*** By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely affect concurrent operations.</span></span> <span data-ttu-id="467c0-421">このため、リソース ガバナーによって CPU 使用率が制限されるセッションで、優先度の低い圧縮バックアップを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="467c0-421">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by the Resource Governor.</span></span> <span data-ttu-id="467c0-422">詳細については、「 [リソース ガバナーを使用してバックアップの圧縮による CPU 使用率を制限する方法 &#40;Transact-SQL&#41;](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="467c0-422">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>|  
    |<span data-ttu-id="467c0-423">**[バックアップを圧縮しない]**</span><span class="sxs-lookup"><span data-stu-id="467c0-423">**Do not compress backup**</span></span>|<span data-ttu-id="467c0-424">オンにすると、サーバー レベルの既定値に関係なく、圧縮されていないバックアップが作成されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-424">Click to create an uncompressed backup, regardless of the server-level default.</span></span>|  
  
2.  <span data-ttu-id="467c0-425">**[データベースのバックアップ (差分) タスクの定義]** ページで、部分バックアップを実行する 1 つまたは複数のデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-425">On the **Define Backup Database (Differential) Task** page, select the database or databases on which to run a partial backup.</span></span> <span data-ttu-id="467c0-426">このページで利用可能なオプションの詳細については、上の手順 16. の定義リストを参照してください。</span><span class="sxs-lookup"><span data-stu-id="467c0-426">See the definition list in step 16, above, for more information about the available options on this page.</span></span> <span data-ttu-id="467c0-427">このタスクでは `BACKUP DATABASE ... WITH DIFFERENTIAL` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="467c0-427">This task uses the `BACKUP DATABASE ... WITH DIFFERENTIAL` statement.</span></span> <span data-ttu-id="467c0-428">詳細については、「 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="467c0-428">For more information, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  <span data-ttu-id="467c0-429">完了したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-429">When finished, click **Next**.</span></span>  
  
3.  <span data-ttu-id="467c0-430">**[データベースのバックアップ (トランザクション ログ) タスクの定義]** ページで、(トランザクション ログのバックアップを実行する 1 つまたは複数のデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-430">On the **Define Backup Database (Transaction Log) Task** page, select the database or databases on which to run a backup for a transaction log.</span></span> <span data-ttu-id="467c0-431">このページで利用可能なオプションの詳細については、上の手順 16. の定義リストを参照してください。</span><span class="sxs-lookup"><span data-stu-id="467c0-431">See the definition list in step 16, above, for more information about the available options on this page.</span></span> <span data-ttu-id="467c0-432">このタスクでは `BACKUP LOG` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="467c0-432">This task uses the `BACKUP LOG` statement.</span></span> <span data-ttu-id="467c0-433">詳細については、「 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="467c0-433">For more information, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span> <span data-ttu-id="467c0-434">完了したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-434">When finished, click **Next**.</span></span>  
  
#### <a name="define-maintenance-cleanup-tasks"></a><span data-ttu-id="467c0-435">メンテナンス クリーンアップ タスクを定義する</span><span class="sxs-lookup"><span data-stu-id="467c0-435">Define Maintenance Cleanup Tasks</span></span>  
  
1.  <span data-ttu-id="467c0-436">**[メンテナンス クリーンアップ タスクの定義]** ページで、メンテナンス プランで作成されたテキスト レポートやデータベースのバックアップ ファイルなど、メンテナンス プランの一部として削除するファイルの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-436">On the **Define Maintenance Cleanup Task** page, specify the types of files to delete as part of the maintenance plan, including text reports created by maintenance plans and database backup files.</span></span> <span data-ttu-id="467c0-437">このタスクでは `EXEC xp_delete_file` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="467c0-437">This task uses the `EXEC xp_delete_file` statement.</span></span> <span data-ttu-id="467c0-438">完了したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-438">When finished, click **Next**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="467c0-439">このタスクでは、指定したディレクトリのサブフォルダーにあるファイルは自動的に削除されません。</span><span class="sxs-lookup"><span data-stu-id="467c0-439">This task does not automatically delete files in the subfolders of the specified directory.</span></span> <span data-ttu-id="467c0-440">この予防策により、メンテナンス クリーンアップ タスクを使用してファイルを削除するような、悪意のある攻撃を受ける可能性を最小限に抑えています。</span><span class="sxs-lookup"><span data-stu-id="467c0-440">This precaution reduces the possibility of a malicious attack that uses the Maintenance Cleanup task to delete files.</span></span> <span data-ttu-id="467c0-441">直下のサブフォルダーにあるファイルを削除する場合は、 **[直下のサブフォルダーを含める]** を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="467c0-441">If you want to delete files in first-level subfolders, you must select **Include first-level subfolders**.</span></span>  
  
     <span data-ttu-id="467c0-442">このページで使用できるオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="467c0-442">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="467c0-443">**[次の種類のファイルを削除]**</span><span class="sxs-lookup"><span data-stu-id="467c0-443">**Delete files of the following type**</span></span>  
     <span data-ttu-id="467c0-444">削除するファイルの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-444">Specify the type of files to be deleted.</span></span>  
  
     <span data-ttu-id="467c0-445">**[バックアップ ファイル]**</span><span class="sxs-lookup"><span data-stu-id="467c0-445">**Backup files**</span></span>  
     <span data-ttu-id="467c0-446">データベース バックアップ ファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="467c0-446">Delete database backup files.</span></span>  
  
     <span data-ttu-id="467c0-447">**[メンテナンス プラン テキスト レポート]**</span><span class="sxs-lookup"><span data-stu-id="467c0-447">**Maintenance Plan text reports**</span></span>  
     <span data-ttu-id="467c0-448">以前に実行されたメンテナンス プランのテキスト レポートを削除します。</span><span class="sxs-lookup"><span data-stu-id="467c0-448">Delete text reports of previously run maintenance plans.</span></span>  
  
     <span data-ttu-id="467c0-449">**ファイルの場所**</span><span class="sxs-lookup"><span data-stu-id="467c0-449">**File location**</span></span>  
     <span data-ttu-id="467c0-450">削除するファイルのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-450">Specify path to files to be deleted.</span></span>  
  
     <span data-ttu-id="467c0-451">**[特定のファイルを削除する]**</span><span class="sxs-lookup"><span data-stu-id="467c0-451">**Delete specific file**</span></span>  
     <span data-ttu-id="467c0-452">**[ファイル名]** ボックスに指定したファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="467c0-452">Delete the specific file provided in the **File name** text box.</span></span>  
  
     <span data-ttu-id="467c0-453">**[フォルダーを検索し、拡張子に基づいてファイルを削除する]**</span><span class="sxs-lookup"><span data-stu-id="467c0-453">**Search folder and delete files based on an extension**</span></span>  
     <span data-ttu-id="467c0-454">指定したフォルダー内にある、指定した拡張子を持つすべてのファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="467c0-454">Delete all files with the specified extension in the specified folder.</span></span> <span data-ttu-id="467c0-455">このオプションは、複数のファイルを削除するときに使用します。たとえば、拡張子が .bak であり Tuesday フォルダーに保存されている、すべてのバックアップ ファイルを一度に削除できます。</span><span class="sxs-lookup"><span data-stu-id="467c0-455">Use this to delete multiple files at once, such as all backup files in the Tuesday folder with the .bak extension.</span></span>  
  
     <span data-ttu-id="467c0-456">**[フォルダー]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-456">**Folder** box</span></span>  
     <span data-ttu-id="467c0-457">削除するファイルが格納されているフォルダーのパスと名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-457">Path and name of the folder containing the files to be deleted.</span></span>  
  
     <span data-ttu-id="467c0-458">**[ファイル拡張子]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-458">**File extension** box</span></span>  
     <span data-ttu-id="467c0-459">削除するファイルのファイル拡張子を指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-459">Provide the file extension of the files to be deleted.</span></span> <span data-ttu-id="467c0-460">複数のファイル、たとえば、Tuesday フォルダー内にある、.bak 拡張子が付いたすべてのバックアップ ファイルを一度に削除するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="467c0-460">To delete multiple files at one time, like all backup files with the .bak extension in the Tuesday folder, specify .bak.</span></span>  
  
     <span data-ttu-id="467c0-461">**[直下のサブフォルダーを含める]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-461">**Include first-level subfolders** check box</span></span>  
     <span data-ttu-id="467c0-462">**[フォルダー]** で指定したフォルダーの直下にあるサブフォルダーから、 **[ファイル拡張子]** で指定した拡張子を持つファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="467c0-462">Delete files with the extension specified for **File extension** from first-level subfolders under the folder specified in **Folder**.</span></span>  
  
     <span data-ttu-id="467c0-463">**[タスク実行時にファイルの経過期間に基づいてファイルを削除する]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-463">**Delete files based on the age of the file at task run time** check box</span></span>  
     <span data-ttu-id="467c0-464">**[次の期間経過したファイルを削除]** ボックスに数値と時間単位を指定して、削除するファイルの最小経過期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-464">Specify the minimum age of the files that you want to delete by providing a number, and unit of time in the **Delete files older than the following** box.</span></span>  
  
     <span data-ttu-id="467c0-465">**[次の期間経過したファイルを削除]**</span><span class="sxs-lookup"><span data-stu-id="467c0-465">**Delete files older than the following**</span></span>  
     <span data-ttu-id="467c0-466">数値と時間単位 ( **[時間]** 、 **[日]** 、 **[週]** 、 **[月]** 、または **[年]** ) を指定して、削除するファイルの最小経過期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-466">Specify the minimum age of the files that you want to delete by providing a number, and unit of time (**Hour**, **Day**, **Week**, **Month**, or **Year**).</span></span> <span data-ttu-id="467c0-467">指定した期間より古いファイルが削除されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-467">Files older than the time frame specified will be deleted.</span></span>  
  
#### <a name="select-report-options"></a><span data-ttu-id="467c0-468">レポート オプションを選択する</span><span class="sxs-lookup"><span data-stu-id="467c0-468">Select Report Options</span></span>  
  
1.  <span data-ttu-id="467c0-469">**[レポート オプションの選択]** ページで、メンテナンス プラン操作のレポートを保存または配布するためのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="467c0-469">On the **Select Report Options** page, select options for saving or distributing a report of the maintenance plan actions.</span></span> <span data-ttu-id="467c0-470">このタスクでは `EXEC sp_notify_operator` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="467c0-470">This task uses the `EXEC sp_notify_operator` statement.</span></span> <span data-ttu-id="467c0-471">詳細については、[sp_notify_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-notify-operator-transact-sql)」を参照してください。完了したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-471">For more information, see [sp_notify_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-notify-operator-transact-sql).When finished, click **Next**.</span></span>  
  
     <span data-ttu-id="467c0-472">このページで使用できるオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="467c0-472">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="467c0-473">**[レポートをテキスト ファイルに書き込む]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-473">**Write a report to a text file** check box</span></span>  
     <span data-ttu-id="467c0-474">レポートをファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="467c0-474">Save the report in a file.</span></span>  
  
     <span data-ttu-id="467c0-475">**[フォルダーの場所]** ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-475">**Folder location** box</span></span>  
     <span data-ttu-id="467c0-476">レポートを格納するファイルの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-476">Specify the location of the file that will contain the report.</span></span>  
  
     <span data-ttu-id="467c0-477">**[レポートを電子メールで送信する]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="467c0-477">**E-mail report** check box</span></span>  
     <span data-ttu-id="467c0-478">タスクが失敗した場合に電子メールを送信します。</span><span class="sxs-lookup"><span data-stu-id="467c0-478">Send an e-mail when a task fails.</span></span> <span data-ttu-id="467c0-479">このタスクを使用するには、[データベース メール] が有効になっていて、MSDB がメール ホスト データベースとして正しく構成され、有効な電子メール アドレスを持つ [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのオペレーターが存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="467c0-479">To use this task you must have Database Mail enabled and correctly configured with MSDB as a Mail Host Database, and have a [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operator with a valid e-mail address.</span></span>  
  
     <span data-ttu-id="467c0-480">**[エージェント オペレーター]**</span><span class="sxs-lookup"><span data-stu-id="467c0-480">**Agent operator**</span></span>  
     <span data-ttu-id="467c0-481">電子メールの受信者を指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-481">Specify the recipient of the e-mail.</span></span>  
  
     <span data-ttu-id="467c0-482">**[メール プロファイル]**</span><span class="sxs-lookup"><span data-stu-id="467c0-482">**Mail profile**</span></span>  
     <span data-ttu-id="467c0-483">プロファイル定義する電子メールの送信者を指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-483">Specify the profile that defines the sender of the e-mail.</span></span>  
  
#### <a name="complete-the-wizard"></a><span data-ttu-id="467c0-484">ウィザードを完了する</span><span class="sxs-lookup"><span data-stu-id="467c0-484">Complete the Wizard</span></span>  
  
1.  <span data-ttu-id="467c0-485">**[ウィザードの完了]** ページで、これまでのページで選択した内容を確認し、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="467c0-485">On the **Complete the Wizard** page, verify the choices made on the previous pages, and click **Finish**.</span></span>  
  
2.  <span data-ttu-id="467c0-486">**[メンテナンス プラン ウィザードの進行状況]** ページでは、メンテナンス プラン ウィザードの操作に関する状態情報を監視できます。</span><span class="sxs-lookup"><span data-stu-id="467c0-486">On the **Maintenance Wizard Progress** page, monitor status information about the actions of the Maintenance Plan Wizard.</span></span> <span data-ttu-id="467c0-487">ウィザードで選択したオプションに応じて、[進行状況] ページに 1 つまたは複数のアクションが含まれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="467c0-487">Depending on the options that you selected in the wizard, the progress page might contain one or more actions.</span></span> <span data-ttu-id="467c0-488">上部のボックスには、ウィザードの全体的な状態と受信した状態メッセージ、エラー メッセージ、および警告メッセージの数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-488">The top box displays the overall status of the wizard and the number of status, error, and warning messages that the wizard has received.</span></span>  
  
     <span data-ttu-id="467c0-489">**[メンテナンス プラン ウィザードの進行状況]** ページでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="467c0-489">The following options are available on the **Maintenance Wizard Progress** page:</span></span>  
  
     <span data-ttu-id="467c0-490">**詳細**</span><span class="sxs-lookup"><span data-stu-id="467c0-490">**Details**</span></span>  
     <span data-ttu-id="467c0-491">アクション、状態、およびウィザードで実行したアクションから返されたメッセージが提供されます。</span><span class="sxs-lookup"><span data-stu-id="467c0-491">Provides the action, status, and any messages that are returned from action taken by the wizard.</span></span>  
  
     <span data-ttu-id="467c0-492">**操作**</span><span class="sxs-lookup"><span data-stu-id="467c0-492">**Action**</span></span>  
     <span data-ttu-id="467c0-493">各アクションの種類と名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="467c0-493">Specifies the type and name of each action.</span></span>  
  
     <span data-ttu-id="467c0-494">**状態**</span><span class="sxs-lookup"><span data-stu-id="467c0-494">**Status**</span></span>  
     <span data-ttu-id="467c0-495">全体としてウィザードのアクションが **[成功]** または **[失敗]** のいずれの値を返したかを示します。</span><span class="sxs-lookup"><span data-stu-id="467c0-495">Indicates whether the wizard action as a whole returned the value of **Success** or **Failure**.</span></span>  
  
     <span data-ttu-id="467c0-496">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="467c0-496">**Message**</span></span>  
     <span data-ttu-id="467c0-497">プロセスから返されたすべてのエラー メッセージまたは警告メッセージを提供します。</span><span class="sxs-lookup"><span data-stu-id="467c0-497">Provides any error or warning messages that are returned from the process.</span></span>  
  
     <span data-ttu-id="467c0-498">**Report**</span><span class="sxs-lookup"><span data-stu-id="467c0-498">**Report**</span></span>  
     <span data-ttu-id="467c0-499">パーティションの作成ウィザードの結果を含むレポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="467c0-499">Creates a report that contains the results of the Create Partition Wizard.</span></span> <span data-ttu-id="467c0-500">**[レポートの表示]** 、 **[レポートをファイルに保存]** 、 **[レポートをクリップボードにコピー]** 、 **[レポートを電子メールとして送信]** の各オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="467c0-500">The options are **View Report**, **Save Report to File**, **Copy Report to Clipboard**, and **Send Report as Email**.</span></span>  
  
     <span data-ttu-id="467c0-501">**[レポートの表示]**</span><span class="sxs-lookup"><span data-stu-id="467c0-501">**View Report**</span></span>  
     <span data-ttu-id="467c0-502">パーティションの作成ウィザードの進行状況に関するテキスト レポートを表示する **[レポートの表示]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="467c0-502">Opens the **View Report** dialog box, which contains a text report of the progress of the Create Partition Wizard.</span></span>  
  
     <span data-ttu-id="467c0-503">**[レポートをファイルに保存]**</span><span class="sxs-lookup"><span data-stu-id="467c0-503">**Save Report to File**</span></span>  
     <span data-ttu-id="467c0-504">**[レポートに名前を付けて保存]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="467c0-504">Opens the **Save Report As** dialog box.</span></span>  
  
     <span data-ttu-id="467c0-505">**[レポートをクリップボードにコピー]**</span><span class="sxs-lookup"><span data-stu-id="467c0-505">**Copy Report to Clipboard**</span></span>  
     <span data-ttu-id="467c0-506">ウィザードの進行状況レポートの結果をクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="467c0-506">Copies the results of the wizard's progress report to the Clipboard.</span></span>  
  
     <span data-ttu-id="467c0-507">**[レポートを電子メールとして送信]**</span><span class="sxs-lookup"><span data-stu-id="467c0-507">**Send Report as Email**</span></span>  
     <span data-ttu-id="467c0-508">ウィザードの進行状況レポートの結果を電子メール メッセージにコピーします。</span><span class="sxs-lookup"><span data-stu-id="467c0-508">Copies the results of the wizard's progress report into an email message.</span></span>  
  
  
