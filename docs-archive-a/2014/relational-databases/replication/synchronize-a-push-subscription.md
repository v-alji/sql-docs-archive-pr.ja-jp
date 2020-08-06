---
title: プッシュ サブスクリプションの同期 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], push subscriptions
- subscriptions [SQL Server replication], push
- push subscriptions [SQL Server replication], synchronizing
ms.assetid: 0cfa7ae5-91d3-4a4f-9edf-a852d45783b5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5fb2f7bd961748272d6cd67e3412b09d9370a6f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716238"
---
# <a name="synchronize-a-push-subscription"></a><span data-ttu-id="513f7-102">プッシュ サブスクリプションの同期</span><span class="sxs-lookup"><span data-stu-id="513f7-102">Synchronize a Push Subscription</span></span>
  <span data-ttu-id="513f7-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [レプリケーション エージェント](agents/replication-agents-overview.md)、またはレプリケーション管理オブジェクト (RMO) を使用して、プッシュ サブスクリプションを同期する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="513f7-103">This topic describes how to synchronize a push subscription in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [replication agents](agents/replication-agents-overview.md), or Replication Management Objects (RMO).</span></span>  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="513f7-104">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="513f7-104">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="513f7-105">サブスクリプションは、ディストリビューション エージェント (スナップショット レプリケーションおよびトランザクション レプリケーションの場合) またはマージ エージェント (マージ レプリケーションの場合) で同期されます。</span><span class="sxs-lookup"><span data-stu-id="513f7-105">Subscriptions are synchronized by the Distribution Agent (for snapshot and transactional replication) or the Merge Agent (for merge replication).</span></span> <span data-ttu-id="513f7-106">エージェントは継続的に実行、要求時に実行、またはスケジュールで実行できます。</span><span class="sxs-lookup"><span data-stu-id="513f7-106">Agents can run continuously, run on demand, or run on a schedule.</span></span> <span data-ttu-id="513f7-107">同期スケジュールの指定の詳細については、「[同期スケジュールの指定](specify-synchronization-schedules.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="513f7-107">For more information about specifying synchronization schedules, see [Specify Synchronization Schedules](specify-synchronization-schedules.md).</span></span>  
  
 <span data-ttu-id="513f7-108">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の **[ローカル パブリケーション]** フォルダーと **[ローカル サブスクリプション]** フォルダー、およびレプリケーション モニターの **[すべてのサブスクリプション]** タブからは、要求時にサブスクリプションを同期します。</span><span class="sxs-lookup"><span data-stu-id="513f7-108">Synchronize a subscription on demand from the **Local Publications** and **Local Subscriptions** folders in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and the **All Subscriptions** tab in Replication Monitor.</span></span> <span data-ttu-id="513f7-109">Oracle パブリケーションに対するサブスクリプションは、サブスクライバーから要求時に同期することはできません。</span><span class="sxs-lookup"><span data-stu-id="513f7-109">Subscriptions to Oracle publications cannot be synchronized on demand from the Subscriber.</span></span> <span data-ttu-id="513f7-110">レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor](monitor/start-the-replication-monitor.md)」 (レプリケーション モニターの開始) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="513f7-110">For information about starting Replication Monitor, see [Start the Replication Monitor](monitor/start-the-replication-monitor.md).</span></span>  
  
#### <a name="to-synchronize-a-push-subscription-on-demand-in-management-studio-at-the-publisher"></a><span data-ttu-id="513f7-111">Management Studio で要求時にプッシュ サブスクリプションを同期するには (パブリッシャー側)</span><span class="sxs-lookup"><span data-stu-id="513f7-111">To synchronize a push subscription on demand in Management Studio (at the Publisher)</span></span>  
  
1.  <span data-ttu-id="513f7-112">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="513f7-112">Connect to the Publisher in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="513f7-113">**[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="513f7-113">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="513f7-114">サブスクリプションを同期するパブリケーションを展開します。</span><span class="sxs-lookup"><span data-stu-id="513f7-114">Expand the publication for which you want to synchronize subscriptions.</span></span>  
  
4.  <span data-ttu-id="513f7-115">同期するサブスクリプションを右クリックし、 **[同期の状態の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="513f7-115">Right-click the subscription you want to synchronize, and then click **View Synchronization Status**.</span></span>  
  
5.  <span data-ttu-id="513f7-116">**[同期の状態の表示 - \<Subscriber>:\<SubscriptionDatabase>]** ダイアログ ボックスで、 **[開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="513f7-116">In the **View Synchronization Status - \<Subscriber>:\<SubscriptionDatabase>** dialog box, click **Start**.</span></span> <span data-ttu-id="513f7-117">同期が完了したら、" **同期処理が完了しました** " というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="513f7-117">When synchronization is complete, the message **Synchronization completed** is displayed.</span></span>  
  
6.  <span data-ttu-id="513f7-118">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="513f7-118">Click **Close**.</span></span>  
  
#### <a name="to-synchronize-a-push-subscription-on-demand-in-management-studio-at-the-subscriber"></a><span data-ttu-id="513f7-119">Management Studio で要求時にプッシュ サブスクリプションを同期するには (サブスクライバー側)</span><span class="sxs-lookup"><span data-stu-id="513f7-119">To synchronize a push subscription on demand in Management Studio (at the Subscriber)</span></span>  
  
1.  <span data-ttu-id="513f7-120">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でサブスクライバーに接続して、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="513f7-120">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="513f7-121">**[レプリケーション]** フォルダーを展開し、 **[ローカル サブスクリプション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="513f7-121">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="513f7-122">同期するサブスクリプションを右クリックし、 **[同期の状態の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="513f7-122">Right-click the subscription you want to synchronize, and then click **View Synchronization Status**.</span></span>  
  
4.  <span data-ttu-id="513f7-123">ディストリビューターへの接続の確立に関するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="513f7-123">A message is displayed about establishing a connection to the Distributor.</span></span> <span data-ttu-id="513f7-124">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="513f7-124">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="513f7-125">**[同期の状態の表示 - \<Subscriber>:\<SubscriptionDatabase>]** ダイアログ ボックスで、 **[開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="513f7-125">In the **View Synchronization Status - \<Subscriber>:\<SubscriptionDatabase>** dialog box, click **Start**.</span></span> <span data-ttu-id="513f7-126">同期が完了したら、" **同期処理が完了しました** " というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="513f7-126">When synchronization is complete, the message **Synchronization completed** is displayed.</span></span>  
  
6.  <span data-ttu-id="513f7-127">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="513f7-127">Click **Close**.</span></span>  
  
#### <a name="to-synchronize-a-push-subscription-on-demand-in-replication-monitor"></a><span data-ttu-id="513f7-128">レプリケーション モニターで要求時にプッシュ サブスクリプションを同期するには</span><span class="sxs-lookup"><span data-stu-id="513f7-128">To synchronize a push subscription on demand in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="513f7-129">レプリケーション モニターで、左ペインのパブリッシャー グループを展開し、パブリッシャーを展開してパブリケーションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="513f7-129">In Replication Monitor, expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="513f7-130">**[すべてのサブスクリプション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="513f7-130">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="513f7-131">同期するサブスクリプションを右クリックし、 **[同期の開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="513f7-131">Right-click the subscription you want to synchronize, and then click **Start Synchronizing**.</span></span>  
  
4.  <span data-ttu-id="513f7-132">同期の進行状況を見るには、サブスクリプションを右クリックして **[詳細表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="513f7-132">To view synchronization progress, right-click the subscription, and then click **View Details**.</span></span>  
  
##  <a name="using-replication-agents"></a><a name="ReplProg"></a> <span data-ttu-id="513f7-133">レプリケーション エージェントの使用</span><span class="sxs-lookup"><span data-stu-id="513f7-133">Using Replication Agents</span></span>  
 <span data-ttu-id="513f7-134">コマンド プロンプトから適切なレプリケーション エージェント実行可能ファイルを呼び出すことにより、プッシュ サブスクリプションを要求時にプログラムで同期できます。</span><span class="sxs-lookup"><span data-stu-id="513f7-134">Push subscriptions can be synchronized programmatically and on-demand by invoking the appropriate replication agent executable file from the command prompt.</span></span> <span data-ttu-id="513f7-135">呼び出されるレプリケーション エージェント実行可能ファイルは、プッシュ サブスクリプションが属するパブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="513f7-135">The replication agent executable file that is invoked will depend on the type of publication to which the push subscription belongs.</span></span>  
  
#### <a name="to-start-the-distribution-agent-to-synchronize-a-push-subscription-to-a-transactional-publication"></a><span data-ttu-id="513f7-136">ディストリビューション エージェントを開始してプッシュ サブスクリプションをトランザクション パブリケーションに同期するには</span><span class="sxs-lookup"><span data-stu-id="513f7-136">To start the Distribution Agent to synchronize a push subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="513f7-137">コマンド プロンプトから、またはディストリビューターからバッチ ファイルで、 **distrib.exe**を実行します。</span><span class="sxs-lookup"><span data-stu-id="513f7-137">From the command prompt or in a batch file at the Distributor, execute **distrib.exe**.</span></span> <span data-ttu-id="513f7-138">次のコマンド ライン引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="513f7-138">Specify the following command-line arguments:</span></span>  
  
    -   <span data-ttu-id="513f7-139">**-Publisher**</span><span class="sxs-lookup"><span data-stu-id="513f7-139">**-Publisher**</span></span>  
  
    -   <span data-ttu-id="513f7-140">**-PublisherDB**</span><span class="sxs-lookup"><span data-stu-id="513f7-140">**-PublisherDB**</span></span>  
  
    -   <span data-ttu-id="513f7-141">**-Distributor**</span><span class="sxs-lookup"><span data-stu-id="513f7-141">**-Distributor**</span></span>  
  
    -   <span data-ttu-id="513f7-142">**-Subscriber**</span><span class="sxs-lookup"><span data-stu-id="513f7-142">**-Subscriber**</span></span>  
  
    -   <span data-ttu-id="513f7-143">**-SubscriberDB**</span><span class="sxs-lookup"><span data-stu-id="513f7-143">**-SubscriberDB**</span></span>  
  
    -   <span data-ttu-id="513f7-144">**-SubscriptionType = 0**</span><span class="sxs-lookup"><span data-stu-id="513f7-144">**-SubscriptionType = 0**</span></span>  
  
     <span data-ttu-id="513f7-145">SQL Server 認証を使用する場合は、次の引数も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="513f7-145">If you are using SQL Server Authentication, you must also specify the following arguments:</span></span>  
  
    -   <span data-ttu-id="513f7-146">**-DistributorLogin**</span><span class="sxs-lookup"><span data-stu-id="513f7-146">**-DistributorLogin**</span></span>  
  
    -   <span data-ttu-id="513f7-147">**-DistributorPassword**</span><span class="sxs-lookup"><span data-stu-id="513f7-147">**-DistributorPassword**</span></span>  
  
    -   <span data-ttu-id="513f7-148">**-DistributorSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="513f7-148">**-DistributorSecurityMode = 0**</span></span>  
  
    -   <span data-ttu-id="513f7-149">**-PublisherLogin**</span><span class="sxs-lookup"><span data-stu-id="513f7-149">**-PublisherLogin**</span></span>  
  
    -   <span data-ttu-id="513f7-150">**-PublisherPassword**</span><span class="sxs-lookup"><span data-stu-id="513f7-150">**-PublisherPassword**</span></span>  
  
    -   <span data-ttu-id="513f7-151">**-PublisherSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="513f7-151">**-PublisherSecurityMode = 0**</span></span>  
  
    -   <span data-ttu-id="513f7-152">**-SubscriberLogin**</span><span class="sxs-lookup"><span data-stu-id="513f7-152">**-SubscriberLogin**</span></span>  
  
    -   <span data-ttu-id="513f7-153">**-SubscriberPassword**</span><span class="sxs-lookup"><span data-stu-id="513f7-153">**-SubscriberPassword**</span></span>  
  
    -   <span data-ttu-id="513f7-154">**-SubscriberSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="513f7-154">**-SubscriberSecurityMode = 0**</span></span>  
  
        > [!IMPORTANT]  
        >  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
#### <a name="to-start-the-merge-agent-to-synchronize-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="513f7-155">マージ エージェントを開始してプッシュ サブスクリプションをマージ パブリケーションに同期するには</span><span class="sxs-lookup"><span data-stu-id="513f7-155">To start the Merge Agent to synchronize a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="513f7-156">コマンド プロンプトから、またはディストリビューターからバッチ ファイルで、 **replmerg.exe**を実行します。</span><span class="sxs-lookup"><span data-stu-id="513f7-156">From the command prompt or in a batch file at the Distributor, execute **replmerg.exe**.</span></span> <span data-ttu-id="513f7-157">次のコマンド ライン引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="513f7-157">Specify the following command-line arguments:</span></span>  
  
    -   <span data-ttu-id="513f7-158">**-Publisher**</span><span class="sxs-lookup"><span data-stu-id="513f7-158">**-Publisher**</span></span>  
  
    -   <span data-ttu-id="513f7-159">**-PublisherDB**</span><span class="sxs-lookup"><span data-stu-id="513f7-159">**-PublisherDB**</span></span>  
  
    -   <span data-ttu-id="513f7-160">**-Publication**</span><span class="sxs-lookup"><span data-stu-id="513f7-160">**-Publication**</span></span>  
  
    -   <span data-ttu-id="513f7-161">**-Distributor**</span><span class="sxs-lookup"><span data-stu-id="513f7-161">**-Distributor**</span></span>  
  
    -   <span data-ttu-id="513f7-162">**-Subscriber**</span><span class="sxs-lookup"><span data-stu-id="513f7-162">**-Subscriber**</span></span>  
  
    -   <span data-ttu-id="513f7-163">**-SubscriberDB**</span><span class="sxs-lookup"><span data-stu-id="513f7-163">**-SubscriberDB**</span></span>  
  
    -   <span data-ttu-id="513f7-164">**-SubscriptionType = 0**</span><span class="sxs-lookup"><span data-stu-id="513f7-164">**-SubscriptionType = 0**</span></span>  
  
     <span data-ttu-id="513f7-165">SQL Server 認証を使用する場合は、次の引数も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="513f7-165">If you are using SQL Server Authentication, you must also specify the following arguments:</span></span>  
  
    -   <span data-ttu-id="513f7-166">**-DistributorLogin**</span><span class="sxs-lookup"><span data-stu-id="513f7-166">**-DistributorLogin**</span></span>  
  
    -   <span data-ttu-id="513f7-167">**-DistributorPassword**</span><span class="sxs-lookup"><span data-stu-id="513f7-167">**-DistributorPassword**</span></span>  
  
    -   <span data-ttu-id="513f7-168">**-DistributorSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="513f7-168">**-DistributorSecurityMode = 0**</span></span>  
  
    -   <span data-ttu-id="513f7-169">**-PublisherLogin**</span><span class="sxs-lookup"><span data-stu-id="513f7-169">**-PublisherLogin**</span></span>  
  
    -   <span data-ttu-id="513f7-170">**-PublisherPassword**</span><span class="sxs-lookup"><span data-stu-id="513f7-170">**-PublisherPassword**</span></span>  
  
    -   <span data-ttu-id="513f7-171">**-PublisherSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="513f7-171">**-PublisherSecurityMode = 0**</span></span>  
  
    -   <span data-ttu-id="513f7-172">**-SubscriberLogin**</span><span class="sxs-lookup"><span data-stu-id="513f7-172">**-SubscriberLogin**</span></span>  
  
    -   <span data-ttu-id="513f7-173">**-SubscriberPassword**</span><span class="sxs-lookup"><span data-stu-id="513f7-173">**-SubscriberPassword**</span></span>  
  
    -   <span data-ttu-id="513f7-174">**-SubscriberSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="513f7-174">**-SubscriberSecurityMode = 0**</span></span>  
  
        > [!IMPORTANT]  
        >  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
###  <a name="examples-replication-agents"></a><a name="TsqlExample"></a> <span data-ttu-id="513f7-175">例 (レプリケーション エージェント)</span><span class="sxs-lookup"><span data-stu-id="513f7-175">Examples (Replication Agents)</span></span>  
 <span data-ttu-id="513f7-176">次の例では、ディストリビューション エージェントを開始してプッシュ サブスクリプションを同期します。</span><span class="sxs-lookup"><span data-stu-id="513f7-176">The following example starts the Distribution Agent to synchronize a push subscription.</span></span>  
  
 
```
REM -- Declare the variables.  
SET Publisher=%instancename%  
SET Subscriber=%instancename%  
SET PublicationDB=AdventureWorks2012  
SET SubscriptionDB=AdventureWorks2012Replica   
SET Publication=AdvWorksProductsTran  
  
REM -- Start the Distribution Agent with four subscription streams.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\DISTRIB.EXE" -Subscriber %Subscriber%   
-SubscriberDB %SubscriptionDB% -SubscriberSecurityMode 1 -Publication %Publication%   
-Publisher %Publisher% -PublisherDB %PublicationDB% -Distributor %Publisher%   
-DistributorSecurityMode 1 -Continuous -SubscriptionType 0 -SubscriptionStreams 4
```
  
 <span data-ttu-id="513f7-177">次の例では、マージ エージェントを開始してプッシュ サブスクリプションを同期します。</span><span class="sxs-lookup"><span data-stu-id="513f7-177">The following example starts the Merge Agent to synchronize a push subscription.</span></span>  

```
REM -- Declare the variables.  
SET Publisher=%instancename%  
SET Subscriber=%instancename%  
SET PublicationDB=AdventureWorks2012  
SET SubscriptionDB=AdventureWorks2012Replica   
SET Publication=AdvWorksSalesOrdersMerge  
  
REM -- Start the Merge Agent.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE"  -Publisher %Publisher%   
-Subscriber  %Subscriber%  -Distributor %Publisher% -PublisherDB  %PublicationDB%   
-SubscriberDB %SubscriptionDB% -Publication %Publication% -PublisherSecurityMode 1   
-OutputVerboseLevel 3  -Output -SubscriberSecurityMode 1  -SubscriptionType 0   
-DistributorSecurityMode 1
```
  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="513f7-178">レプリケーション管理オブジェクト (RMO) の使用</span><span class="sxs-lookup"><span data-stu-id="513f7-178">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="513f7-179">レプリケーション管理オブジェクト (RMO) およびマネージド コードを使用してレプリケーション エージェント機能にアクセスすることで、プッシュ サブスクリプションをプログラムから同期できます。</span><span class="sxs-lookup"><span data-stu-id="513f7-179">You can synchronize push subscriptions programmatically by using Replication Management Objects (RMO) and managed code access to replication agent functionalities.</span></span> <span data-ttu-id="513f7-180">プッシュ サブスクリプションを同期する際に使用するクラスは、サブスクリプションが属しているパブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="513f7-180">The classes that you use to synchronize a push subscription depend on the type of publication to which the subscription belongs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="513f7-181">アプリケーションに影響を及ぼすことなく、自立的に実行される同期を開始するには、エージェントを非同期的に起動します。</span><span class="sxs-lookup"><span data-stu-id="513f7-181">If you want to start a synchronization that runs autonomously without affecting your application, start the agent asynchronously.</span></span> <span data-ttu-id="513f7-182">ただし、同期処理中に同期の結果を監視し、エージェントからのコールバックを受け取る場合 (たとえば、進行状況バーを表示する場合)、エージェントを同期的に起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="513f7-182">However, if you want to monitor the outcome of the synchronization and receive callbacks from the agent during the synchronization process (for example, if you want to display a progress bar), you should start the agent synchronously.</span></span> <span data-ttu-id="513f7-183">For [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] サブスクライバーの場合、エージェントを同期的に起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="513f7-183">For [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] Subscribers, you must start the agent synchronously.</span></span>  
  
#### <a name="to-synchronize-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="513f7-184">スナップショット パブリケーションまたはトランザクション パブリケーションに対するプッシュ サブスクリプションを同期するには</span><span class="sxs-lookup"><span data-stu-id="513f7-184">To synchronize a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="513f7-185"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、ディストリビューターへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="513f7-185">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="513f7-186"><xref:Microsoft.SqlServer.Replication.TransSubscription> クラスのインスタンスを作成し、次のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="513f7-186">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransSubscription> class and set the following properties:</span></span>  
  
    -   <span data-ttu-id="513f7-187"><xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>に、パブリケーション データベースの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="513f7-187">The publication database name for <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>.</span></span>  
  
    -   <span data-ttu-id="513f7-188"><xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>に、サブスクリプションが属しているパブリケーションの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="513f7-188">The name of the publication to which the subscription belongs for <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="513f7-189"><xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>に、サブスクリプション データベースの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="513f7-189">The name of the subscription database for <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>.</span></span>  
  
    -   <span data-ttu-id="513f7-190"><xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>に、サブスクリプションの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="513f7-190">The name of the Subscriber for <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>.</span></span>  
  
    -   <span data-ttu-id="513f7-191"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>に、手順 1. で作成した接続を設定します。</span><span class="sxs-lookup"><span data-stu-id="513f7-191">The connection created in step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="513f7-192"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、その他のサブスクリプション プロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="513f7-192">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the remaining subscription properties.</span></span> <span data-ttu-id="513f7-193">このメソッドが `false` を返す場合、サブスクリプションが存在するかどうかをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="513f7-193">If this method returns `false`, verify that the subscription exists.</span></span>  
  
4.  <span data-ttu-id="513f7-194">次のいずれかの方法で、ディストリビューターのディストリビューション エージェントを起動します。</span><span class="sxs-lookup"><span data-stu-id="513f7-194">Start the Distribution Agent at the Distributor in one of the following ways:</span></span>  
  
    -   <span data-ttu-id="513f7-195">手順 2. で作成した <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizeWithJob%2A> インスタンスの <xref:Microsoft.SqlServer.Replication.TransSubscription> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="513f7-195">Call the <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizeWithJob%2A> method on the instance of <xref:Microsoft.SqlServer.Replication.TransSubscription> from step 2.</span></span> <span data-ttu-id="513f7-196">このメソッドは、ディストリビューション エージェントを非同期的に起動するため、エージェント ジョブの実行中、制御が直ちにアプリケーションに返されます。</span><span class="sxs-lookup"><span data-stu-id="513f7-196">This method starts the Distribution Agent asynchronously, and control immediately returns to your application while the agent job is running.</span></span> <span data-ttu-id="513f7-197"><xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A> に `false` を使用してサブスクリプションが作成された場合、このメソッドを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="513f7-197">You cannot call this method if the subscription was created with a value of `false` for <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A>.</span></span>  
  
    -   <span data-ttu-id="513f7-198"><xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> プロパティから <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizationAgent%2A> クラスのインスタンスを取得し、 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="513f7-198">Obtain an instance of the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> class from the <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizationAgent%2A> property, and call the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> method.</span></span> <span data-ttu-id="513f7-199">このメソッドにより、エージェントが同期的に起動され、制御は実行中のエージェント ジョブに残ります。</span><span class="sxs-lookup"><span data-stu-id="513f7-199">This method starts the agent synchronously, and control remains with the running agent job.</span></span> <span data-ttu-id="513f7-200">同期実行の間、エージェントの実行中に <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> イベントを処理できます。</span><span class="sxs-lookup"><span data-stu-id="513f7-200">During synchronous execution you can handle the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> event while the agent is running.</span></span>  
  
#### <a name="to-synchronize-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="513f7-201">マージ パブリケーションに対するプッシュ サブスクリプションを同期するには</span><span class="sxs-lookup"><span data-stu-id="513f7-201">To synchronize a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="513f7-202"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、ディストリビューターへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="513f7-202">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="513f7-203"><xref:Microsoft.SqlServer.Replication.MergeSubscription> クラスのインスタンスを作成し、次のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="513f7-203">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> class, and set the following properties:</span></span>  
  
    -   <span data-ttu-id="513f7-204"><xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>に、パブリケーション データベースの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="513f7-204">The publication database name for <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>.</span></span>  
  
    -   <span data-ttu-id="513f7-205"><xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>に、サブスクリプションが属しているパブリケーションの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="513f7-205">The name of the publication to which the subscription belongs for <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="513f7-206"><xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>に、サブスクリプション データベースの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="513f7-206">The name of the subscription database for <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>.</span></span>  
  
    -   <span data-ttu-id="513f7-207"><xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>に、サブスクリプションの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="513f7-207">The name of the Subscriber for <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>.</span></span>  
  
    -   <span data-ttu-id="513f7-208"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>に、手順 1. で作成した接続を設定します。</span><span class="sxs-lookup"><span data-stu-id="513f7-208">The connection created in step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="513f7-209"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、その他のサブスクリプション プロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="513f7-209">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the remaining subscription properties.</span></span> <span data-ttu-id="513f7-210">このメソッドが `false` を返す場合、サブスクリプションが存在するかどうかをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="513f7-210">If this method returns `false`, verify that the subscription exists.</span></span>  
  
4.  <span data-ttu-id="513f7-211">次のいずれかの方法で、ディストリビューターのマージ エージェントを起動します。</span><span class="sxs-lookup"><span data-stu-id="513f7-211">Start the Merge Agent at the Distributor in one of the following ways:</span></span>  
  
    -   <span data-ttu-id="513f7-212">手順 2. で作成した <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizeWithJob%2A> インスタンスの <xref:Microsoft.SqlServer.Replication.MergeSubscription> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="513f7-212">Call the <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizeWithJob%2A> method on the instance of <xref:Microsoft.SqlServer.Replication.MergeSubscription> from step 2.</span></span> <span data-ttu-id="513f7-213">このメソッドは、マージ エージェントを非同期的に起動するため、エージェント ジョブの実行中、制御が直ちにアプリケーションに返されます。</span><span class="sxs-lookup"><span data-stu-id="513f7-213">This method starts the Merge Agent asynchronously, and control immediately returns to your application while the agent job is running.</span></span> <span data-ttu-id="513f7-214"><xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A> に `false` を使用してサブスクリプションが作成された場合、このメソッドを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="513f7-214">You cannot call this method if the subscription was created with a value of `false` for <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A>.</span></span>  
  
    -   <span data-ttu-id="513f7-215"><xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> プロパティから <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizationAgent%2A> クラスのインスタンスを取得し、 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="513f7-215">Obtain an instance of the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> class from the <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizationAgent%2A> property, and call the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> method.</span></span> <span data-ttu-id="513f7-216">このメソッドにより、マージ エージェントが同期的に起動され、制御は実行中のエージェント ジョブに残ります。</span><span class="sxs-lookup"><span data-stu-id="513f7-216">This method starts the Merge Agent synchronously, and control remains with the running agent job.</span></span> <span data-ttu-id="513f7-217">同期実行の間、エージェントの実行中に <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> イベントを処理できます。</span><span class="sxs-lookup"><span data-stu-id="513f7-217">During synchronous execution, you can handle the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> event while the agent is running.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="513f7-218">例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="513f7-218">Examples (RMO)</span></span>  
 <span data-ttu-id="513f7-219">次の例では、トランザクション パブリケーションへのプッシュ サブスクリプションを同期します。エージェントはエージェント ジョブを使用して非同期的に起動されます。</span><span class="sxs-lookup"><span data-stu-id="513f7-219">This example synchronizes a push subscription to a transactional publication, where the agent is started asynchronously using the agent job.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncTranPushSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpushsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPushSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpushsub_withjob)]  
  
 <span data-ttu-id="513f7-220">次の例では、トランザクション パブリケーションへのプッシュ サブスクリプションを同期します。エージェントは同期的に起動されます。</span><span class="sxs-lookup"><span data-stu-id="513f7-220">This example synchronizes a push subscription to a transactional publication, where the agent is started synchronously.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncTranPushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpushsub)]  
  
 <span data-ttu-id="513f7-221">次の例では、マージ パブリケーションへのプッシュ サブスクリプションを同期します。エージェントはエージェント ジョブを使用して非同期的に起動されます。</span><span class="sxs-lookup"><span data-stu-id="513f7-221">This example synchronizes a push subscription to a merge publication, where the agent is started asynchronously using the agent job.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncMergePushSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepushsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePushSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepushsub_withjob)]  
  
 <span data-ttu-id="513f7-222">次の例では、マージ パブリケーションへのプッシュ サブスクリプションを同期します。エージェントは同期的に起動されます。</span><span class="sxs-lookup"><span data-stu-id="513f7-222">This example synchronizes a push subscription to a merge publication, where the agent is started synchronously.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncMergePushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepushsub)]  
  
## <a name="see-also"></a><span data-ttu-id="513f7-223">参照</span><span class="sxs-lookup"><span data-stu-id="513f7-223">See Also</span></span>  
 <span data-ttu-id="513f7-224">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="513f7-224">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span></span>  
 <span data-ttu-id="513f7-225">[データの同期](synchronize-data.md) </span><span class="sxs-lookup"><span data-stu-id="513f7-225">[Synchronize Data](synchronize-data.md) </span></span>  
 [<span data-ttu-id="513f7-226">レプリケーション セキュリティの推奨事項</span><span class="sxs-lookup"><span data-stu-id="513f7-226">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
