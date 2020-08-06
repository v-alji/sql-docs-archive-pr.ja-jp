---
title: 同期スケジュールの指定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], synchronizing
- scheduling synchronization [SQL Server replication]
- synchronization [SQL Server replication], schedules
- replication [SQL Server], synchronization
ms.assetid: 97f2535b-ec19-4973-823d-bcf3d5aa0216
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4d752817f7d620b2c6e5fdc5eeb2178c50c42040
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738191"
---
# <a name="specify-synchronization-schedules"></a><span data-ttu-id="d77c1-102">同期スケジュールの指定</span><span class="sxs-lookup"><span data-stu-id="d77c1-102">Specify Synchronization Schedules</span></span>
  <span data-ttu-id="d77c1-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、同期スケジュールを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-103">This topic describes how to specify synchronization schedules in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span> <span data-ttu-id="d77c1-104">サブスクリプションを作成するときに、サブスクリプションのレプリケーション エージェントをいつ実行するかを制御する同期スケジュールを定義できます。</span><span class="sxs-lookup"><span data-stu-id="d77c1-104">When you create a subscription, you can define a synchronization schedule that controls when the replication agent for the subscription will run.</span></span> <span data-ttu-id="d77c1-105">スケジュール設定のパラメーターを指定しなかった場合、サブスクリプションは既定のスケジュールを使用します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-105">If you do not specify scheduling parameters, the subscription will use the default schedule.</span></span>  
  
 <span data-ttu-id="d77c1-106">サブスクリプションは、ディストリビューション エージェント (スナップショット レプリケーションおよびトランザクション レプリケーションの場合) またはマージ エージェント (マージ レプリケーションの場合) で同期されます。</span><span class="sxs-lookup"><span data-stu-id="d77c1-106">Subscriptions are synchronized by the Distribution Agent (for snapshot and transactional replication) or the Merge Agent (for merge replication).</span></span> <span data-ttu-id="d77c1-107">エージェントは継続的に実行、要求時に実行、またはスケジュールで実行できます。</span><span class="sxs-lookup"><span data-stu-id="d77c1-107">Agents can run continuously, run on demand, or run on a schedule.</span></span>  
  
 <span data-ttu-id="d77c1-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="d77c1-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d77c1-109">**同期スケジュールを指定するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="d77c1-109">**To specify synchronization schedules, using:**</span></span>  
  
     [<span data-ttu-id="d77c1-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d77c1-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d77c1-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d77c1-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="d77c1-112">レプリケーション管理オブジェクト (RMO)</span><span class="sxs-lookup"><span data-stu-id="d77c1-112">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d77c1-113">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="d77c1-113">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="d77c1-114">サブスクリプションの新規作成ウィザードの **[同期スケジュール]** ページで同期スケジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-114">Specify synchronization schedules on the **Synchronization Schedule** page of the New Subscription Wizard.</span></span> <span data-ttu-id="d77c1-115">このウィザードへのアクセスの詳細については、「 [Create a Push Subscription](create-a-push-subscription.md) 」および「 [Create a Pull Subscription](create-a-pull-subscription.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d77c1-115">For more information about accessing this wizard, see [Create a Push Subscription](create-a-push-subscription.md) and [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
 <span data-ttu-id="d77c1-116">**[ジョブ スケジュールのプロパティ]** ダイアログ ボックスで同期スケジュールを変更します。このダイアログ ボックスは、 **の** [ジョブ] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] フォルダーおよびレプリケーション モニターのエージェントの詳細ウィンドウから使用できます。</span><span class="sxs-lookup"><span data-stu-id="d77c1-116">Modify synchronization schedules in the **Job Schedule Properties** dialog box, which is available from the **Jobs** folder in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and from the agent details windows in Replication Monitor.</span></span> <span data-ttu-id="d77c1-117">レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor](monitor/start-the-replication-monitor.md)」 (レプリケーション モニターの開始) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d77c1-117">For information about starting Replication Monitor, see [Start the Replication Monitor](monitor/start-the-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="d77c1-118">**[ジョブ]** フォルダーからスケジュールを指定する場合は、次の表でエージェントのジョブ名を確認してください。</span><span class="sxs-lookup"><span data-stu-id="d77c1-118">If you specify schedules from the **Jobs** folder, use the following table to determine the agent job name.</span></span>  
  
|<span data-ttu-id="d77c1-119">エージェント</span><span class="sxs-lookup"><span data-stu-id="d77c1-119">Agent</span></span>|<span data-ttu-id="d77c1-120">ジョブ名</span><span class="sxs-lookup"><span data-stu-id="d77c1-120">Job name</span></span>|  
|-----------|--------------|  
|<span data-ttu-id="d77c1-121">プル サブスクリプションに対するマージ エージェント</span><span class="sxs-lookup"><span data-stu-id="d77c1-121">Merge Agent for pull subscriptions</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<integer>**|  
|<span data-ttu-id="d77c1-122">プッシュ サブスクリプションに対するマージ エージェント</span><span class="sxs-lookup"><span data-stu-id="d77c1-122">Merge Agent for push subscriptions</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|  
|<span data-ttu-id="d77c1-123">プッシュ サブスクリプションに対するディストリビューション エージェント</span><span class="sxs-lookup"><span data-stu-id="d77c1-123">Distribution Agent for push subscriptions</span></span>|<span data-ttu-id="d77c1-124">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>** <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d77c1-124">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>** <sup>1</sup></span></span>|  
|<span data-ttu-id="d77c1-125">プル サブスクリプションに対するディストリビューション エージェント</span><span class="sxs-lookup"><span data-stu-id="d77c1-125">Distribution Agent for pull subscriptions</span></span>|<span data-ttu-id="d77c1-126">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<GUID>** <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="d77c1-126">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<GUID>** <sup>2</sup></span></span>|  
|<span data-ttu-id="d77c1-127">SQL Server 以外のサブスクライバーへのプッシュ サブスクリプションに対するディストリビューション エージェント</span><span class="sxs-lookup"><span data-stu-id="d77c1-127">Distribution Agent for push subscriptions to non-SQL Server Subscribers</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|  
  
 <span data-ttu-id="d77c1-128"><sup>1</sup> Oracle パブリケーションに対するプッシュ サブスクリプションの場合は、 **\<Publisher>-\<PublicationDatabase>** ではなく \*\*\<Publisher>-\<Publisher**> になります</span><span class="sxs-lookup"><span data-stu-id="d77c1-128"><sup>1</sup> For push subscriptions to Oracle publications, it is \*\*\<Publisher>-\<Publisher**> rather than **\<Publisher>-\<PublicationDatabase>**</span></span>  
  
 <span data-ttu-id="d77c1-129"><sup>2</sup> Oracle パブリケーションに対するプル サブスクリプションの場合は、 **\<Publisher>-\<PublicationDatabase>** ではなく \*\*\<Publisher>-\<DistributionDatabase**> になります</span><span class="sxs-lookup"><span data-stu-id="d77c1-129"><sup>2</sup> For pull subscriptions to Oracle publications, it is \*\*\<Publisher>-\<DistributionDatabase**> rather than **\<Publisher>-\<PublicationDatabase>**</span></span>  
  
#### <a name="to-specify-synchronization-schedules"></a><span data-ttu-id="d77c1-130">同期スケジュールを指定するには</span><span class="sxs-lookup"><span data-stu-id="d77c1-130">To specify synchronization schedules</span></span>  
  
1.  <span data-ttu-id="d77c1-131">サブスクリプションの新規作成ウィザードの **[同期スケジュール]** ページで、作成する各サブスクリプションについて、 **[エージェント スケジュール]** ボックスの一覧から以下のいずれかの値を選択します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-131">On the **SynchronizationSchedule** page of the New Subscription Wizard, select one of the following values from the **Agent Schedule** drop-down list for each subscription you are creating:</span></span>  
  
    -   <span data-ttu-id="d77c1-132">**[連続実行する]**</span><span class="sxs-lookup"><span data-stu-id="d77c1-132">**Run continuously**</span></span>  
  
    -   <span data-ttu-id="d77c1-133">**[要求時にのみ実行する]**</span><span class="sxs-lookup"><span data-stu-id="d77c1-133">**Run on demand only**</span></span>  
  
    -   **\<Define Schedule...>**  
  
2.  <span data-ttu-id="d77c1-134">**[\<Define Schedule...>]** を選択した場合は、 **[ジョブ スケジュールのプロパティ]** ダイアログ ボックスでスケジュールを指定し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d77c1-134">If you select **\<Define Schedule...>**, specify a schedule in the **Job Schedule Properties** dialog box, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="d77c1-135">ウィザードを完了します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-135">Complete the wizard.</span></span>  
  
#### <a name="to-modify-a-synchronization-schedule-for-a-push-subscription-in-replication-monitor"></a><span data-ttu-id="d77c1-136">レプリケーション モニターでプッシュ サブスクリプションの同期スケジュールを変更するには</span><span class="sxs-lookup"><span data-stu-id="d77c1-136">To modify a synchronization schedule for a push subscription in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="d77c1-137">レプリケーション モニターの左ペインのパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d77c1-137">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="d77c1-138">**[すべてのサブスクリプション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d77c1-138">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="d77c1-139">サブスクリプションを右クリックし、 **[詳細表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d77c1-139">Right-click a subscription, and then click **View Details**.</span></span>  
  
4.  <span data-ttu-id="d77c1-140">[**サブスクリプション \< SubscriptionName> \*\* ] ウィンドウで、[**アクション**] をクリックし、[ \*\* \<AgentName> ジョブのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d77c1-140">In the **Subscription \< SubscriptionName>** window, click **Action**, and then click **\<AgentName> Job Properties**.</span></span>  
  
5.  <span data-ttu-id="d77c1-141">**[ジョブのプロパティ - \<JobName>]** ダイアログ ボックスの **[スケジュール]** ページで、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d77c1-141">On the **Schedules** page of the **Job Properties - \<JobName>** dialog box, click **Edit.**</span></span>  
  
6.  <span data-ttu-id="d77c1-142">**[ジョブ スケジュールのプロパティ]** ダイアログ ボックスで、 **[スケジュールの種類]** ボックスの一覧の値を選択します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-142">In the **Job Schedule Properties** dialog box, select a value from the **Schedule Type** drop-down list:</span></span>  
  
    -   <span data-ttu-id="d77c1-143">エージェントを連続実行するには、 **[SQL Server エージェントの開始時に自動的に開始]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-143">To specify that the agent should run continuously, select **Start automatically when SQL Server Agent starts**.</span></span>  
  
    -   <span data-ttu-id="d77c1-144">エージェントをスケジュールで実行するには、 **[定期的]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-144">To specify that the agent should run on a schedule, select **Recurring**.</span></span>  
  
    -   <span data-ttu-id="d77c1-145">エージェントを要求時に実行するには、 **[指定日時]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-145">To specify that the agent should run on demand, select **One time**.</span></span>  
  
7.  <span data-ttu-id="d77c1-146">**[定期的]** を選択した場合は、エージェントのスケジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-146">If you select **Recurring**, specify a schedule for the agent.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### <a name="to-modify-a-synchronization-schedule-for-a-push-subscription-in-management-studio"></a><span data-ttu-id="d77c1-147">Management Studio でプッシュ サブスクリプションの同期スケジュールを変更するには</span><span class="sxs-lookup"><span data-stu-id="d77c1-147">To modify a synchronization schedule for a push subscription in Management Studio</span></span>  
  
1.  <span data-ttu-id="d77c1-148">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でディストリビューターに接続して、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-148">Connect to the Distributor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="d77c1-149">**[SQL Server エージェント]** フォルダーを展開して、 **[ジョブ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-149">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="d77c1-150">サブスクリプションに関連付けられているディストリビューション エージェントまたはマージ エージェントのジョブを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d77c1-150">Right-click the job for the Distribution Agent or Merge Agent associated with the subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="d77c1-151">**[ジョブのプロパティ - \<JobName>]** ダイアログ ボックスの **[スケジュール]** ページで、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d77c1-151">On the **Schedules** page of the **Job Properties - \<JobName>** dialog box, click **Edit.**</span></span>  
  
5.  <span data-ttu-id="d77c1-152">**[ジョブ スケジュールのプロパティ]** ダイアログ ボックスで、 **[スケジュールの種類]** ボックスの一覧の値を選択します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-152">In the **Job Schedule Properties** dialog box, select a value from the **Schedule Type** drop-down list:</span></span>  
  
    -   <span data-ttu-id="d77c1-153">エージェントを連続実行するには、 **[SQL Server エージェントの開始時に自動的に開始]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-153">To specify that the agent should run continuously, select **Start automatically when SQL Server Agent starts**.</span></span>  
  
    -   <span data-ttu-id="d77c1-154">エージェントをスケジュールで実行するには、 **[定期的]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-154">To specify that the agent should run on a schedule, select **Recurring**.</span></span>  
  
    -   <span data-ttu-id="d77c1-155">エージェントを要求時に実行するには、 **[指定日時]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-155">To specify that the agent should run on demand, select **One time**.</span></span>  
  
6.  <span data-ttu-id="d77c1-156">**[定期的]** を選択した場合は、エージェントのスケジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-156">If you select **Recurring**, specify a schedule for the agent.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### <a name="to-modify-a-synchronization-schedule-for-a-pull-subscription-in-management-studio"></a><span data-ttu-id="d77c1-157">Management Studio でプル サブスクリプションの同期スケジュールを変更するには</span><span class="sxs-lookup"><span data-stu-id="d77c1-157">To modify a synchronization schedule for a pull subscription in Management Studio</span></span>  
  
1.  <span data-ttu-id="d77c1-158">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でサブスクライバーに接続して、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-158">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="d77c1-159">**[SQL Server エージェント]** フォルダーを展開して、 **[ジョブ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-159">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="d77c1-160">サブスクリプションに関連付けられているディストリビューション エージェントまたはマージ エージェントのジョブを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d77c1-160">Right-click the job for the Distribution Agent or Merge Agent associated with the subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="d77c1-161">**[ジョブのプロパティ - \<JobName>]** ダイアログ ボックスの **[スケジュール]** ページで、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d77c1-161">On the **Schedules** page of the **Job Properties - \<JobName>** dialog box, click **Edit.**</span></span>  
  
5.  <span data-ttu-id="d77c1-162">**[ジョブ スケジュールのプロパティ]** ダイアログ ボックスで、 **[スケジュールの種類]** ボックスの一覧の値を選択します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-162">In the **Job Schedule Properties** dialog box, select a value from the **Schedule Type** drop-down list:</span></span>  
  
    -   <span data-ttu-id="d77c1-163">エージェントを連続実行するには、 **[SQL Server エージェントの開始時に自動的に開始]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-163">To specify that the agent should run continuously, select **Start automatically when SQL Server Agent starts**.</span></span>  
  
    -   <span data-ttu-id="d77c1-164">エージェントをスケジュールで実行するには、 **[定期的]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-164">To specify that the agent should run on a schedule, select **Recurring**.</span></span>  
  
    -   <span data-ttu-id="d77c1-165">エージェントを要求時に実行するには、 **[指定日時]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-165">To specify that the agent should run on demand, select **One time**.</span></span>  
  
6.  <span data-ttu-id="d77c1-166">**[定期的]** を選択した場合は、エージェントのスケジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-166">If you select **Recurring**, specify a schedule for the agent.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d77c1-167">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="d77c1-167">Using Transact-SQL</span></span>  
 <span data-ttu-id="d77c1-168">レプリケーション ストアド プロシージャを使用してプログラムで同期スケジュールを定義できます。</span><span class="sxs-lookup"><span data-stu-id="d77c1-168">You can define synchronization schedules programmatically using replication stored procedures.</span></span> <span data-ttu-id="d77c1-169">使用するストアド プロシージャは、レプリケーションの種類およびサブスクリプションの種類 (プルまたはプッシュ) によって異なります。</span><span class="sxs-lookup"><span data-stu-id="d77c1-169">The stored procedures that you use depend on the type of replication and the type of subscription (pull or push).</span></span>  
  
 <span data-ttu-id="d77c1-170">スケジュールを定義するには、次のスケジュール設定のパラメーターを使用します。これらのパラメーターの動作は、[sp_add_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql) から継承されます。</span><span class="sxs-lookup"><span data-stu-id="d77c1-170">A schedule is defined by the following scheduling parameters, the behaviors of which are inherited from [sp_add_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql):</span></span>  
  
-   <span data-ttu-id="d77c1-171">**@frequency_type**-エージェントのスケジュール設定時に使用される頻度の種類。</span><span class="sxs-lookup"><span data-stu-id="d77c1-171">**@frequency_type** - the type of frequency used when scheduling the agent.</span></span>  
  
-   <span data-ttu-id="d77c1-172">**@frequency_interval**-エージェントを実行する曜日。</span><span class="sxs-lookup"><span data-stu-id="d77c1-172">**@frequency_interval** - the day of the week when an agent runs.</span></span>  
  
-   <span data-ttu-id="d77c1-173">**@frequency_relative_interval**-エージェントを毎月実行するようにスケジュールされている特定の月の週。</span><span class="sxs-lookup"><span data-stu-id="d77c1-173">**@frequency_relative_interval** - the week of a given month when the agent is scheduled to run monthly.</span></span>  
  
-   <span data-ttu-id="d77c1-174">**@frequency_recurrence_factor**-同期の間に発生する頻度の種類の単位の数。</span><span class="sxs-lookup"><span data-stu-id="d77c1-174">**@frequency_recurrence_factor** - the number of frequency-type units that occur between synchronizations.</span></span>  
  
-   <span data-ttu-id="d77c1-175">**@frequency_subday**-エージェントを1日に複数回実行する頻度の単位。</span><span class="sxs-lookup"><span data-stu-id="d77c1-175">**@frequency_subday** - the frequency unit when the agent runs more often than once a day.</span></span>  
  
-   <span data-ttu-id="d77c1-176">**@frequency_subday_interval**-エージェントを1日に複数回実行する場合の頻度の単位。</span><span class="sxs-lookup"><span data-stu-id="d77c1-176">**@frequency_subday_interval** - the number of frequency units between runs when the agent runs more often than once a day.</span></span>  
  
-   <span data-ttu-id="d77c1-177">**@active_start_time_of_day**-エージェントの実行を開始する特定の日の最も早い時刻。</span><span class="sxs-lookup"><span data-stu-id="d77c1-177">**@active_start_time_of_day** - the earliest time in a given day when an agent run will start.</span></span>  
  
-   <span data-ttu-id="d77c1-178">**@active_end_time_of_day**-エージェントの実行が開始されたときの特定の日の最も遅い時刻。</span><span class="sxs-lookup"><span data-stu-id="d77c1-178">**@active_end_time_of_day** - the latest time in a given day when an agent run will start.</span></span>  
  
-   <span data-ttu-id="d77c1-179">**@active_start_date**-エージェントスケジュールが有効になる最初の日。</span><span class="sxs-lookup"><span data-stu-id="d77c1-179">**@active_start_date** - the first day that the agent schedule will be in effect.</span></span>  
  
-   <span data-ttu-id="d77c1-180">**@active_end_date**-エージェントスケジュールが有効になる最後の日。</span><span class="sxs-lookup"><span data-stu-id="d77c1-180">**@active_end_date** - the last day that the agent schedule will be in effect.</span></span>  
  
#### <a name="to-define-the-synchronization-schedule-for-a-pull-subscription-to-a-transactional-publication"></a><span data-ttu-id="d77c1-181">トランザクション パブリケーションに対するプル サブスクリプションの同期スケジュールを定義するには</span><span class="sxs-lookup"><span data-stu-id="d77c1-181">To define the synchronization schedule for a pull subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="d77c1-182">トランザクション パブリケーションに対して新しいプル サブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-182">Create a new pull subscription to a transactional publication.</span></span> <span data-ttu-id="d77c1-183">詳細については、「 [プル サブスクリプションの作成](create-a-pull-subscription.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d77c1-183">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
2.  <span data-ttu-id="d77c1-184">サブスクライバーで、[sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-184">At the Subscriber, execute [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql).</span></span> <span data-ttu-id="d77c1-185">**@publisher**、、 **@publisher_db** **@publication** 、および [!INCLUDE[msCoName](../../includes/msconame-md.md)] サブスクライバーでのディストリビューションエージェントがおよびに対して実行するときに使用する Windows 資格情報を指定し **@job_name** **@password** ます。</span><span class="sxs-lookup"><span data-stu-id="d77c1-185">Specify **@publisher**, **@publisher_db**, **@publication**, and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows credentials under which the Distribution Agent at the Subscriber runs for **@job_name** and **@password**.</span></span> <span data-ttu-id="d77c1-186">サブスクリプションを同期するディストリビューション エージェント ジョブのスケジュールを定義する、上述の同期のパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-186">Specify the synchronization parameters, detailed above, that define the schedule for the Distribution Agent job that synchronizes the subscription.</span></span>  
  
#### <a name="to-define-the-synchronization-schedule-for-a-push-subscription-to-a-transactional-publication"></a><span data-ttu-id="d77c1-187">トランザクション パブリケーションに対するプッシュ サブスクリプションの同期スケジュールを定義するには</span><span class="sxs-lookup"><span data-stu-id="d77c1-187">To define the synchronization schedule for a push subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="d77c1-188">トランザクション パブリケーションに対して新しいプッシュ サブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-188">Create a new push subscription to a transactional publication.</span></span> <span data-ttu-id="d77c1-189">詳細については、「 [プッシュ サブスクリプションの作成](create-a-push-subscription.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d77c1-189">For more information, see [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
2.  <span data-ttu-id="d77c1-190">サブスクライバーで、[sp_addpushsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-190">At the Subscriber, execute [sp_addpushsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql).</span></span> <span data-ttu-id="d77c1-191">**@subscriber**、、 **@subscriber_db** **@publication** 、およびサブスクライバーでのディストリビューションエージェントがおよびに対して実行するときに使用する Windows 資格情報を指定し **@job_name** **@password** ます。</span><span class="sxs-lookup"><span data-stu-id="d77c1-191">Specify **@subscriber**, **@subscriber_db**, **@publication**, and the Windows credentials under which the Distribution Agent at the Subscriber runs for **@job_name** and **@password**.</span></span> <span data-ttu-id="d77c1-192">サブスクリプションを同期するディストリビューション エージェント ジョブのスケジュールを定義する、上述の同期のパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-192">Specify the synchronization parameters, detailed above, that define the schedule for the Distribution Agent job that synchronizes the subscription.</span></span>  
  
#### <a name="to-define-the-synchronization-schedule-for-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="d77c1-193">マージ パブリケーションに対するプル サブスクリプションの同期スケジュールを定義するには</span><span class="sxs-lookup"><span data-stu-id="d77c1-193">To define the synchronization schedule for a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="d77c1-194">マージ パブリケーションに対して新しいプル サブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-194">Create a new pull subscription to a merge publication.</span></span> <span data-ttu-id="d77c1-195">詳細については、「 [プル サブスクリプションの作成](create-a-pull-subscription.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d77c1-195">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
2.  <span data-ttu-id="d77c1-196">サブスクライバーで、 [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-196">At the Subscriber, execute [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql).</span></span> <span data-ttu-id="d77c1-197">**@publisher**、、 **@publisher_db** **@publication** 、およびサブスクライバーでのマージエージェントがおよびに対して実行するときに使用する Windows 資格情報を指定し **@job_name** **@password** ます。</span><span class="sxs-lookup"><span data-stu-id="d77c1-197">Specify **@publisher**, **@publisher_db**, **@publication**, and the Windows credentials under which the Merge Agent at the Subscriber runs for **@job_name** and **@password**.</span></span> <span data-ttu-id="d77c1-198">サブスクリプションを同期するマージ エージェント ジョブのスケジュールを定義する、上述の同期のパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-198">Specify the synchronization parameters, detailed above, that define the schedule for the Merge Agent job that synchronizes the subscription.</span></span>  
  
#### <a name="to-define-the-synchronization-schedule-for-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="d77c1-199">マージ パブリケーションに対するプッシュ サブスクリプションの同期スケジュールを定義するには</span><span class="sxs-lookup"><span data-stu-id="d77c1-199">To define the synchronization schedule for a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="d77c1-200">マージ パブリケーションに対して新しいプッシュ サブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-200">Create a new push subscription to a merge publication.</span></span> <span data-ttu-id="d77c1-201">詳細については、「 [プッシュ サブスクリプションの作成](create-a-push-subscription.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d77c1-201">For more information, see [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
2.  <span data-ttu-id="d77c1-202">サブスクライバーで、 [sp_addmergepushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-202">At the Subscriber, execute [sp_addmergepushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql).</span></span> <span data-ttu-id="d77c1-203">**@subscriber**、、 **@subscriber_db** **@publication** 、およびサブスクライバーでのマージエージェントがおよびに対して実行するときに使用する Windows 資格情報を指定し **@job_name** **@password** ます。</span><span class="sxs-lookup"><span data-stu-id="d77c1-203">Specify **@subscriber**, **@subscriber_db**, **@publication**, and the Windows credentials under which the Merge Agent at the Subscriber runs for **@job_name** and **@password**.</span></span> <span data-ttu-id="d77c1-204">サブスクリプションを同期するマージ エージェント ジョブのスケジュールを定義する、上述の同期のパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-204">Specify the synchronization parameters, detailed above, that define the schedule for the Merge Agent job that synchronizes the subscription.</span></span>  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="d77c1-205">レプリケーション管理オブジェクト (RMO) の使用</span><span class="sxs-lookup"><span data-stu-id="d77c1-205">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="d77c1-206">レプリケーションは、SQL&#xA0;Server エージェントを使用して、スナップショットの生成やサブスクリプションの同期など、定期的に発生する動作のジョブをスケジュール設定します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-206">Replication uses the SQL Server Agent to schedule jobs for activities that occur periodically, such as snapshot generation and subscription synchronization.</span></span> <span data-ttu-id="d77c1-207">レプリケーション管理オブジェクト (RMO) をプログラムで使用して、レプリケーション エージェント ジョブのスケジュールを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d77c1-207">You can use Replication Management Objects (RMO) programmatically to specify schedules for replication agent jobs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d77c1-208">サブスクリプションを作成し、`false` に `CreateSyncAgentByDefault` を指定すると (プル サブスクリプションの既定の動作)、エージェント ジョブは作成されず、スケジュール設定のプロパティは無視されます。</span><span class="sxs-lookup"><span data-stu-id="d77c1-208">When you create a subscription and specify a value `false` for `CreateSyncAgentByDefault` (the default behavior for pull subscriptions) the agent job is not created and scheduling properties are ignored.</span></span> <span data-ttu-id="d77c1-209">この場合は、アプリケーションによって同期スケジュールを決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d77c1-209">In this case, the synchronization schedule must be determined by the application.</span></span> <span data-ttu-id="d77c1-210">詳細については、「 [Create a Pull Subscription](create-a-pull-subscription.md) 」および「 [Create a Push Subscription](create-a-push-subscription.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d77c1-210">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md) and [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-push-subscription-to-a-transactional-publication"></a><span data-ttu-id="d77c1-211">トランザクション パブリケーションに対するプッシュ サブスクリプションを作成するレプリケーション エージェント スケジュールを定義するには</span><span class="sxs-lookup"><span data-stu-id="d77c1-211">To define a replication agent schedule when you create a push subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="d77c1-212">作成するサブスクリプションに対して <xref:Microsoft.SqlServer.Replication.TransSubscription> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-212">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransSubscription> class for the subscription you are creating.</span></span> <span data-ttu-id="d77c1-213">詳細については、「 [プッシュ サブスクリプションの作成](create-a-push-subscription.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d77c1-213">For more information, see [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
2.  <span data-ttu-id="d77c1-214"><xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>を呼び出す前に、 <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> プロパティの次のフィールドを 1 つ以上設定します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-214">Before you call <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>, set one or more of the following fields of the <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> property:</span></span>  
  
    -   <span data-ttu-id="d77c1-215"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - エージェントのスケジュール設定時に使用する頻度の種類 (毎日、毎週など)。</span><span class="sxs-lookup"><span data-stu-id="d77c1-215"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - the type of frequency (such as daily or weekly) you use when you schedule the agent.</span></span>  
  
    -   <span data-ttu-id="d77c1-216"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - エージェントを実行する曜日。</span><span class="sxs-lookup"><span data-stu-id="d77c1-216"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - the day of the week that an agent runs.</span></span>  
  
    -   <span data-ttu-id="d77c1-217"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - エージェントを月単位でスケジュール設定する場合の指定された月の週。</span><span class="sxs-lookup"><span data-stu-id="d77c1-217"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - the week of a given month when the agent is scheduled to run monthly.</span></span>  
  
    -   <span data-ttu-id="d77c1-218"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - 同期から同期の間に発生する頻度の種類の単位の数。</span><span class="sxs-lookup"><span data-stu-id="d77c1-218"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - the number of frequency-type units that occur between synchronizations.</span></span>  
  
    -   <span data-ttu-id="d77c1-219"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - エージェントを 1 日に複数回実行する場合の頻度の単位。</span><span class="sxs-lookup"><span data-stu-id="d77c1-219"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - the frequency unit when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="d77c1-220"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - エージェントを 1 日に複数回実行する場合の頻度の単位。</span><span class="sxs-lookup"><span data-stu-id="d77c1-220"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - the number of frequency units between runs when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="d77c1-221"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - エージェントの実行を開始する特定の日の最も早い時刻。</span><span class="sxs-lookup"><span data-stu-id="d77c1-221"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - earliest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="d77c1-222"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - エージェントの実行を開始する特定の日の最も遅い時刻。</span><span class="sxs-lookup"><span data-stu-id="d77c1-222"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - latest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="d77c1-223"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - エージェント スケジュールが有効になっている最初の日。</span><span class="sxs-lookup"><span data-stu-id="d77c1-223"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - first day that the agent schedule is in effect.</span></span>  
  
    -   <span data-ttu-id="d77c1-224"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - エージェント スケジュールが有効になっている最後の日。</span><span class="sxs-lookup"><span data-stu-id="d77c1-224"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - last day that the agent schedule is in effect.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d77c1-225">これらのプロパティを指定しなかった場合、既定値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="d77c1-225">If you do not specify one of these properties, a default value is set.</span></span>  
  
3.  <span data-ttu-id="d77c1-226"><xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> メソッドを呼び出してサブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-226">Call the <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> method to create the subscription.</span></span>  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-pull-subscription-to-a-transactional-publication"></a><span data-ttu-id="d77c1-227">トランザクション パブリケーションに対するプル サブスクリプションを作成するレプリケーション エージェント スケジュールを定義するには</span><span class="sxs-lookup"><span data-stu-id="d77c1-227">To define a replication agent schedule when you create a pull subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="d77c1-228">作成するサブスクリプションに対して <xref:Microsoft.SqlServer.Replication.TransPullSubscription> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-228">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> class for the subscription you are creating.</span></span> <span data-ttu-id="d77c1-229">詳細については、「 [プル サブスクリプションの作成](create-a-pull-subscription.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d77c1-229">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
2.  <span data-ttu-id="d77c1-230"><xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>を呼び出す前に、 <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> プロパティの次のフィールドを 1 つ以上設定します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-230">Before you call <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>, set one or more of the following fields of the <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> property:</span></span>  
  
    -   <span data-ttu-id="d77c1-231"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - エージェントのスケジュール設定時に使用する頻度の種類 (毎日、毎週など)。</span><span class="sxs-lookup"><span data-stu-id="d77c1-231"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - the type of frequency (such as daily or weekly) that you use when you schedule the agent.</span></span>  
  
    -   <span data-ttu-id="d77c1-232"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - エージェントを実行する曜日。</span><span class="sxs-lookup"><span data-stu-id="d77c1-232"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - the day of the week that an agent runs.</span></span>  
  
    -   <span data-ttu-id="d77c1-233"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - エージェントを月単位でスケジュール設定する場合の指定された月の週。</span><span class="sxs-lookup"><span data-stu-id="d77c1-233"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - the week of a given month that the agent is scheduled to run monthly.</span></span>  
  
    -   <span data-ttu-id="d77c1-234"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - 同期から同期の間に発生する頻度の種類の単位の数。</span><span class="sxs-lookup"><span data-stu-id="d77c1-234"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - the number of frequency-type units that occur between synchronizations.</span></span>  
  
    -   <span data-ttu-id="d77c1-235"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - エージェントを 1 日に複数回実行する場合の頻度の単位。</span><span class="sxs-lookup"><span data-stu-id="d77c1-235"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - the frequency unit when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="d77c1-236"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - エージェントを 1 日に複数回実行する場合の頻度の単位。</span><span class="sxs-lookup"><span data-stu-id="d77c1-236"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - the number of frequency units between runs when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="d77c1-237"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - エージェントの実行を開始する特定の日の最も早い時刻。</span><span class="sxs-lookup"><span data-stu-id="d77c1-237"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - earliest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="d77c1-238"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - エージェントの実行を開始する特定の日の最も遅い時刻。</span><span class="sxs-lookup"><span data-stu-id="d77c1-238"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - latest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="d77c1-239"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - エージェント スケジュールが有効になっている最初の日。</span><span class="sxs-lookup"><span data-stu-id="d77c1-239"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - first day that the agent schedule is in effect.</span></span>  
  
    -   <span data-ttu-id="d77c1-240"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - エージェント スケジュールが有効になっている最後の日。</span><span class="sxs-lookup"><span data-stu-id="d77c1-240"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - last day that the agent schedule is in effect.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d77c1-241">これらのプロパティを指定しなかった場合、既定値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="d77c1-241">If you do not specify one of these properties, a default value is set.</span></span>  
  
3.  <span data-ttu-id="d77c1-242"><xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> メソッドを呼び出してサブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-242">Call the <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> method to create the subscription.</span></span>  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="d77c1-243">マージ パブリケーションに対するプル サブスクリプションを作成するレプリケーション エージェント スケジュールを定義するには</span><span class="sxs-lookup"><span data-stu-id="d77c1-243">To define a replication agent schedule when you create a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="d77c1-244">作成するサブスクリプションに対して <xref:Microsoft.SqlServer.Replication.MergePullSubscription> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-244">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> class for the subscription you are creating.</span></span> <span data-ttu-id="d77c1-245">詳細については、「 [プル サブスクリプションの作成](create-a-pull-subscription.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d77c1-245">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
2.  <span data-ttu-id="d77c1-246"><xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>を呼び出す前に、 <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> プロパティの次のフィールドを 1 つ以上設定します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-246">Before you call <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>, set one or more of the following fields of the <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> property:</span></span>  
  
    -   <span data-ttu-id="d77c1-247"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - エージェントのスケジュール設定時に使用する頻度の種類 (毎日、毎週など)。</span><span class="sxs-lookup"><span data-stu-id="d77c1-247"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - the type of frequency (such as daily or weekly) that you use when you schedule the agent.</span></span>  
  
    -   <span data-ttu-id="d77c1-248"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - エージェントを実行する曜日。</span><span class="sxs-lookup"><span data-stu-id="d77c1-248"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - the day of the week that an agent runs.</span></span>  
  
    -   <span data-ttu-id="d77c1-249"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - エージェントを月単位でスケジュール設定する場合の指定された月の週。</span><span class="sxs-lookup"><span data-stu-id="d77c1-249"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - the week of a given month that the agent is scheduled to run monthly.</span></span>  
  
    -   <span data-ttu-id="d77c1-250"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - 同期から同期の間に発生する頻度の種類の単位の数。</span><span class="sxs-lookup"><span data-stu-id="d77c1-250"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - the number of frequency-type units that occur between synchronizations.</span></span>  
  
    -   <span data-ttu-id="d77c1-251"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - エージェントを 1 日に複数回実行する場合の頻度の単位。</span><span class="sxs-lookup"><span data-stu-id="d77c1-251"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - the frequency unit when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="d77c1-252"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - エージェントを 1 日に複数回実行する場合の頻度の単位。</span><span class="sxs-lookup"><span data-stu-id="d77c1-252"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - the number of frequency units between runs when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="d77c1-253"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - エージェントの実行を開始する特定の日の最も早い時刻。</span><span class="sxs-lookup"><span data-stu-id="d77c1-253"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - earliest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="d77c1-254"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - エージェントの実行を開始する特定の日の最も遅い時刻。</span><span class="sxs-lookup"><span data-stu-id="d77c1-254"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - latest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="d77c1-255"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - エージェント スケジュールが有効になっている最初の日。</span><span class="sxs-lookup"><span data-stu-id="d77c1-255"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - first day that the agent schedule is in effect.</span></span>  
  
    -   <span data-ttu-id="d77c1-256"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - エージェント スケジュールが有効になっている最後の日。</span><span class="sxs-lookup"><span data-stu-id="d77c1-256"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - last day that the agent schedule is in effect.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d77c1-257">これらのプロパティを指定しなかった場合、既定値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="d77c1-257">If you do not specify one of these properties, a default value is set.</span></span>  
  
3.  <span data-ttu-id="d77c1-258"><xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> メソッドを呼び出してサブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-258">Call the <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> method to create the subscription.</span></span>  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="d77c1-259">マージ パブリケーションに対するプッシュ サブスクリプションを作成するレプリケーション エージェント スケジュールを定義するには</span><span class="sxs-lookup"><span data-stu-id="d77c1-259">To define a replication agent schedule when you create a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="d77c1-260">作成するサブスクリプションに対して <xref:Microsoft.SqlServer.Replication.MergeSubscription> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-260">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> class for the subscription you are creating.</span></span> <span data-ttu-id="d77c1-261">詳細については、「 [プッシュ サブスクリプションの作成](create-a-push-subscription.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d77c1-261">For more information, see [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
2.  <span data-ttu-id="d77c1-262"><xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>を呼び出す前に、 <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> プロパティの次のフィールドを 1 つ以上設定します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-262">Before you call <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>, set one or more of the following fields of the <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> property:</span></span>  
  
    -   <span data-ttu-id="d77c1-263"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - エージェントのスケジュール設定時に使用する頻度の種類 (毎日、毎週など)。</span><span class="sxs-lookup"><span data-stu-id="d77c1-263"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - the type of frequency (such as daily or weekly) that you use when you schedule the agent.</span></span>  
  
    -   <span data-ttu-id="d77c1-264"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - エージェントを実行する曜日。</span><span class="sxs-lookup"><span data-stu-id="d77c1-264"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - the day of the week that an agent runs.</span></span>  
  
    -   <span data-ttu-id="d77c1-265"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - エージェントを月単位でスケジュール設定する場合の指定された月の週。</span><span class="sxs-lookup"><span data-stu-id="d77c1-265"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - the week of a given month that the agent is scheduled to run monthly.</span></span>  
  
    -   <span data-ttu-id="d77c1-266"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - 同期から同期の間に発生する頻度の種類の単位の数。</span><span class="sxs-lookup"><span data-stu-id="d77c1-266"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - the number of frequency-type units that occur between synchronizations.</span></span>  
  
    -   <span data-ttu-id="d77c1-267"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - エージェントを 1 日に複数回実行する場合の頻度の単位。</span><span class="sxs-lookup"><span data-stu-id="d77c1-267"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - the frequency unit when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="d77c1-268"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - エージェントを 1 日に複数回実行する場合の頻度の単位。</span><span class="sxs-lookup"><span data-stu-id="d77c1-268"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - the number of frequency units between runs when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="d77c1-269"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - エージェントの実行を開始する特定の日の最も早い時刻。</span><span class="sxs-lookup"><span data-stu-id="d77c1-269"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - earliest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="d77c1-270"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - エージェントの実行を開始する特定の日の最も遅い時刻。</span><span class="sxs-lookup"><span data-stu-id="d77c1-270"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - latest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="d77c1-271"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - エージェント スケジュールが有効になっている最初の日。</span><span class="sxs-lookup"><span data-stu-id="d77c1-271"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - first day that the agent schedule is in effect.</span></span>  
  
    -   <span data-ttu-id="d77c1-272"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - エージェント スケジュールが有効になっている最後の日。</span><span class="sxs-lookup"><span data-stu-id="d77c1-272"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - last day that the agent schedule is in effect.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d77c1-273">これらのプロパティを指定しなかった場合、既定値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="d77c1-273">If you do not specify one of these properties, a default value is set.</span></span>  
  
3.  <span data-ttu-id="d77c1-274"><xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> メソッドを呼び出してサブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-274">Call the <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> method to create the subscription.</span></span>  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="d77c1-275">例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="d77c1-275">Example (RMO)</span></span>  
 <span data-ttu-id="d77c1-276">次の例では、マージ パブリケーションに対するプッシュ サブスクリプションを作成して、サブスクリプションを同期するスケジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="d77c1-276">This example creates a push subscription to a merge publication and specifies the schedule on which the subscription is synchronized.</span></span>  
  
 [!code-csharp[HowTo#rmo_CreateMergePushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergepushsub)]  
  
## <a name="see-also"></a><span data-ttu-id="d77c1-277">参照</span><span class="sxs-lookup"><span data-stu-id="d77c1-277">See Also</span></span>  
 <span data-ttu-id="d77c1-278">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="d77c1-278">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 <span data-ttu-id="d77c1-279">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="d77c1-279">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 <span data-ttu-id="d77c1-280">[プッシュ サブスクリプションの同期](synchronize-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="d77c1-280">[Synchronize a Push Subscription](synchronize-a-push-subscription.md) </span></span>  
 <span data-ttu-id="d77c1-281">[プル サブスクリプションの同期](synchronize-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="d77c1-281">[Synchronize a Pull Subscription](synchronize-a-pull-subscription.md) </span></span>  
 [<span data-ttu-id="d77c1-282">データの同期</span><span class="sxs-lookup"><span data-stu-id="d77c1-282">Synchronize Data</span></span>](synchronize-data.md)  
  
  
