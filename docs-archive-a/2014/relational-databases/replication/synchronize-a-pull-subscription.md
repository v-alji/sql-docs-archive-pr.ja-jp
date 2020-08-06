---
title: プル サブスクリプションの同期 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- pull subscriptions [SQL Server replication], synchronizing
- synchronization [SQL Server replication], pull subscriptions
- subscriptions [SQL Server replication], pull
ms.assetid: 3ca24b23-fdc3-408e-8208-a2ace48fc8e3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 826622cd17862c0535e60c01baab756af2b2996b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641609"
---
# <a name="synchronize-a-pull-subscription"></a><span data-ttu-id="cf84e-102">プル サブスクリプションの同期</span><span class="sxs-lookup"><span data-stu-id="cf84e-102">Synchronize a Pull Subscription</span></span>
  <span data-ttu-id="cf84e-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [レプリケーション エージェント](agents/replication-agents-overview.md)、またはレプリケーション管理オブジェクト (RMO) を使用して、プル サブスクリプションを同期する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-103">This topic describes how to synchronize a pull subscription in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [replication agents](agents/replication-agents-overview.md), or Replication Management Objects (RMO).</span></span>  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cf84e-104">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="cf84e-104">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="cf84e-105">サブスクリプションは、ディストリビューション エージェント (スナップショット レプリケーションおよびトランザクション レプリケーションの場合) またはマージ エージェント (マージ レプリケーションの場合) で同期されます。</span><span class="sxs-lookup"><span data-stu-id="cf84e-105">Subscriptions are synchronized by the Distribution Agent (for snapshot and transactional replication) or the Merge Agent (for merge replication).</span></span> <span data-ttu-id="cf84e-106">エージェントは継続的に実行、要求時に実行、またはスケジュールで実行できます。</span><span class="sxs-lookup"><span data-stu-id="cf84e-106">Agents can run continuously, run on demand, or run on a schedule.</span></span> <span data-ttu-id="cf84e-107">同期スケジュールの指定の詳細については、「[同期スケジュールの指定](specify-synchronization-schedules.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf84e-107">For more information about specifying synchronization schedules, see [Specify Synchronization Schedules](specify-synchronization-schedules.md).</span></span>  
  
 <span data-ttu-id="cf84e-108">**の** [ローカル サブスクリプション] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]フォルダーから、サブスクリプションを要求時に同期します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-108">Synchronize a subscription on demand from the **Local Subscriptions** folder in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-synchronize-a-pull-subscription-on-demand-in-management-studio"></a><span data-ttu-id="cf84e-109">Management Studio でプル サブスクリプションを要求時に同期するには</span><span class="sxs-lookup"><span data-stu-id="cf84e-109">To synchronize a pull subscription on demand in Management Studio</span></span>  
  
1.  <span data-ttu-id="cf84e-110">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でサブスクライバーに接続して、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-110">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="cf84e-111">**[レプリケーション]** フォルダーを展開し、 **[ローカル サブスクリプション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-111">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="cf84e-112">同期するサブスクリプションを右クリックし、 **[同期の状態の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf84e-112">Right-click the subscription you want to synchronize, and then click **View Synchronization Status**.</span></span>  
  
4.  <span data-ttu-id="cf84e-113">**[同期の状態の表示 - \<Subscriber>:\<SubscriptionDatabase>]** ダイアログ ボックスで、 **[開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf84e-113">In the **View Synchronization Status - \<Subscriber>:\<SubscriptionDatabase>** dialog box, click **Start**.</span></span> <span data-ttu-id="cf84e-114">同期が完了したら、" **同期処理が完了しました** " というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf84e-114">When synchronization is complete, the message **Synchronization completed** is displayed.</span></span>  
  
5.  <span data-ttu-id="cf84e-115">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf84e-115">Click **Close**.</span></span>  
  
##  <a name="replication-agents"></a><a name="ReplProg"></a> <span data-ttu-id="cf84e-116">Replication Agents</span><span class="sxs-lookup"><span data-stu-id="cf84e-116">Replication Agents</span></span>  
 <span data-ttu-id="cf84e-117">コマンド プロンプトから適切なレプリケーション エージェント実行可能ファイルを呼び出すことにより、プル サブスクリプションを要求時にプログラムで同期できます。</span><span class="sxs-lookup"><span data-stu-id="cf84e-117">Pull subscriptions can be synchronized programmatically and on-demand by invoking the appropriate replication agent executable file from the command prompt.</span></span> <span data-ttu-id="cf84e-118">呼び出されるレプリケーション エージェント実行可能ファイルは、プル サブスクリプションが属するパブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="cf84e-118">The replication agent executable file that is invoked will depend on the type of publication to which the pull subscription belongs.</span></span> <span data-ttu-id="cf84e-119">詳しくは、「 [Replication Agents](agents/replication-agents-overview.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cf84e-119">For more information, see [Replication Agents](agents/replication-agents-overview.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cf84e-120">レプリケーション エージェントは、コマンド プロンプトからエージェントを起動したユーザーの Windows 認証資格情報を使ってローカル サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-120">Replication agents connect to the local server using the Windows Authentication credentials of the user who started the agent from the command prompt.</span></span> <span data-ttu-id="cf84e-121">これらの Windows 資格情報は、Windows 統合認証でリモート サーバーに接続する際にも使用されます。</span><span class="sxs-lookup"><span data-stu-id="cf84e-121">These Windows credentials are also used when connecting to remote servers using Windows Integrated Authentication.</span></span>  
  
#### <a name="to-start-the-distribution-agent-from-the-command-prompt-or-from-a-batch-file"></a><span data-ttu-id="cf84e-122">ディストリビューション エージェントをコマンド プロンプトまたはバッチ ファイルから起動するには</span><span class="sxs-lookup"><span data-stu-id="cf84e-122">To start the distribution agent from the command prompt or from a batch file</span></span>  
  
1.  <span data-ttu-id="cf84e-123">コマンド プロンプトまたはバッチ ファイルから、次のコマンド ライン引数を指定して [distrib.exe](agents/replication-distribution-agent.md) を実行し、 **レプリケーション ディストリビューション エージェント**を起動します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-123">From the command prompt or in a batch file, start the [Replication Distribution Agent](agents/replication-distribution-agent.md) by running **distrib.exe**, specifying the following command-line arguments:</span></span>  
  
    -   <span data-ttu-id="cf84e-124">**-Publisher**</span><span class="sxs-lookup"><span data-stu-id="cf84e-124">**-Publisher**</span></span>  
  
    -   <span data-ttu-id="cf84e-125">**-PublisherDB**</span><span class="sxs-lookup"><span data-stu-id="cf84e-125">**-PublisherDB**</span></span>  
  
    -   <span data-ttu-id="cf84e-126">**-Distributor**</span><span class="sxs-lookup"><span data-stu-id="cf84e-126">**-Distributor**</span></span>  
  
    -   <span data-ttu-id="cf84e-127">**-DistributorSecurityMode** = **1**</span><span class="sxs-lookup"><span data-stu-id="cf84e-127">**-DistributorSecurityMode** = **1**</span></span>  
  
    -   <span data-ttu-id="cf84e-128">**-Subscriber**</span><span class="sxs-lookup"><span data-stu-id="cf84e-128">**-Subscriber**</span></span>  
  
    -   <span data-ttu-id="cf84e-129">**-SubscriberDB**</span><span class="sxs-lookup"><span data-stu-id="cf84e-129">**-SubscriberDB**</span></span>  
  
    -   <span data-ttu-id="cf84e-130">**-SubscriberSecurityMode** = **1**</span><span class="sxs-lookup"><span data-stu-id="cf84e-130">**-SubscriberSecurityMode** = **1**</span></span>  
  
    -   <span data-ttu-id="cf84e-131">**-SubscriptionType** = **1**</span><span class="sxs-lookup"><span data-stu-id="cf84e-131">**-SubscriptionType** = **1**</span></span>  
  
     <span data-ttu-id="cf84e-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合は、さらに、次の引数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf84e-132">If you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must also specify the following arguments:</span></span>  
  
    -   <span data-ttu-id="cf84e-133">**-DistributorLogin**</span><span class="sxs-lookup"><span data-stu-id="cf84e-133">**-DistributorLogin**</span></span>  
  
    -   <span data-ttu-id="cf84e-134">**-DistributorPassword**</span><span class="sxs-lookup"><span data-stu-id="cf84e-134">**-DistributorPassword**</span></span>  
  
    -   <span data-ttu-id="cf84e-135">**-DistributorSecurityMode** =  **\@publisher_security_mode**</span><span class="sxs-lookup"><span data-stu-id="cf84e-135">**-DistributorSecurityMode** = **0**</span></span>  
  
    -   <span data-ttu-id="cf84e-136">**-PublisherLogin**</span><span class="sxs-lookup"><span data-stu-id="cf84e-136">**-PublisherLogin**</span></span>  
  
    -   <span data-ttu-id="cf84e-137">**-PublisherPassword**</span><span class="sxs-lookup"><span data-stu-id="cf84e-137">**-PublisherPassword**</span></span>  
  
    -   <span data-ttu-id="cf84e-138">**-PublisherSecurityMode** =  **\@publisher_security_mode**</span><span class="sxs-lookup"><span data-stu-id="cf84e-138">**-PublisherSecurityMode** = **0**</span></span>  
  
    -   <span data-ttu-id="cf84e-139">**-SubscriberLogin**</span><span class="sxs-lookup"><span data-stu-id="cf84e-139">**-SubscriberLogin**</span></span>  
  
    -   <span data-ttu-id="cf84e-140">**-SubscriberPassword**</span><span class="sxs-lookup"><span data-stu-id="cf84e-140">**-SubscriberPassword**</span></span>  
  
    -   <span data-ttu-id="cf84e-141">**-SubscriberSecurityMode** = **0**</span><span class="sxs-lookup"><span data-stu-id="cf84e-141">**-SubscriberSecurityMode** = **0**</span></span>  
  
#### <a name="to-start-the-merge-agent-from-the-command-prompt-or-from-a-batch-file"></a><span data-ttu-id="cf84e-142">マージ エージェントをコマンド プロンプトまたはバッチ ファイルから起動するには</span><span class="sxs-lookup"><span data-stu-id="cf84e-142">To start the merge agent from the command prompt or from a batch file</span></span>  
  
1.  <span data-ttu-id="cf84e-143">コマンド プロンプトまたはバッチ ファイルから、次のコマンド ライン引数を指定して [replmerg.exe](agents/replication-merge-agent.md) を実行し、 **レプリケーション マージ エージェント**を起動します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-143">From the command prompt or in a batch file, start the [Replication Merge Agent](agents/replication-merge-agent.md) by running **replmerg.exe**, specifying the following command-line arguments:</span></span>  
  
    -   <span data-ttu-id="cf84e-144">**-Publisher**</span><span class="sxs-lookup"><span data-stu-id="cf84e-144">**-Publisher**</span></span>  
  
    -   <span data-ttu-id="cf84e-145">**-PublisherDB**</span><span class="sxs-lookup"><span data-stu-id="cf84e-145">**-PublisherDB**</span></span>  
  
    -   <span data-ttu-id="cf84e-146">**-PublisherSecurityMode** = **1**</span><span class="sxs-lookup"><span data-stu-id="cf84e-146">**-PublisherSecurityMode** = **1**</span></span>  
  
    -   <span data-ttu-id="cf84e-147">**-Publication**</span><span class="sxs-lookup"><span data-stu-id="cf84e-147">**-Publication**</span></span>  
  
    -   <span data-ttu-id="cf84e-148">**-Distributor**</span><span class="sxs-lookup"><span data-stu-id="cf84e-148">**-Distributor**</span></span>  
  
    -   <span data-ttu-id="cf84e-149">**-DistributorSecurityMode** = **1**</span><span class="sxs-lookup"><span data-stu-id="cf84e-149">**-DistributorSecurityMode** = **1**</span></span>  
  
    -   <span data-ttu-id="cf84e-150">**-Subscriber**</span><span class="sxs-lookup"><span data-stu-id="cf84e-150">**-Subscriber**</span></span>  
  
    -   <span data-ttu-id="cf84e-151">**-SubscriberSecurityMode** = **1**</span><span class="sxs-lookup"><span data-stu-id="cf84e-151">**-SubscriberSecurityMode** = **1**</span></span>  
  
    -   <span data-ttu-id="cf84e-152">**-SubscriberDB**</span><span class="sxs-lookup"><span data-stu-id="cf84e-152">**-SubscriberDB**</span></span>  
  
    -   <span data-ttu-id="cf84e-153">**-SubscriptionType** = **1**</span><span class="sxs-lookup"><span data-stu-id="cf84e-153">**-SubscriptionType** = **1**</span></span>  
  
     <span data-ttu-id="cf84e-154">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合は、さらに、次の引数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf84e-154">If you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must also specify the following arguments:</span></span>  
  
    -   <span data-ttu-id="cf84e-155">**-DistributorLogin**</span><span class="sxs-lookup"><span data-stu-id="cf84e-155">**-DistributorLogin**</span></span>  
  
    -   <span data-ttu-id="cf84e-156">**-DistributorPassword**</span><span class="sxs-lookup"><span data-stu-id="cf84e-156">**-DistributorPassword**</span></span>  
  
    -   <span data-ttu-id="cf84e-157">**-DistributorSecurityMode** =  **\@publisher_security_mode**</span><span class="sxs-lookup"><span data-stu-id="cf84e-157">**-DistributorSecurityMode** = **0**</span></span>  
  
    -   <span data-ttu-id="cf84e-158">**-PublisherLogin**</span><span class="sxs-lookup"><span data-stu-id="cf84e-158">**-PublisherLogin**</span></span>  
  
    -   <span data-ttu-id="cf84e-159">**-PublisherPassword**</span><span class="sxs-lookup"><span data-stu-id="cf84e-159">**-PublisherPassword**</span></span>  
  
    -   <span data-ttu-id="cf84e-160">**-PublisherSecurityMode** =  **\@publisher_security_mode**</span><span class="sxs-lookup"><span data-stu-id="cf84e-160">**-PublisherSecurityMode** = **0**</span></span>  
  
    -   <span data-ttu-id="cf84e-161">**-SubscriberLogin**</span><span class="sxs-lookup"><span data-stu-id="cf84e-161">**-SubscriberLogin**</span></span>  
  
    -   <span data-ttu-id="cf84e-162">**-SubscriberPassword**</span><span class="sxs-lookup"><span data-stu-id="cf84e-162">**-SubscriberPassword**</span></span>  
  
    -   <span data-ttu-id="cf84e-163">**-SubscriberSecurityMode** = **0**</span><span class="sxs-lookup"><span data-stu-id="cf84e-163">**-SubscriberSecurityMode** = **0**</span></span>  
  
###  <a name="examples-replication-agents"></a><a name="TsqlExample"></a> <span data-ttu-id="cf84e-164">例 (レプリケーション エージェント)</span><span class="sxs-lookup"><span data-stu-id="cf84e-164">Examples (Replication Agents)</span></span>  
 <span data-ttu-id="cf84e-165">次の例では、ディストリビューション エージェントを起動して、プル サブスクリプションを同期します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-165">The following example starts the Distribution Agent to synchronize a pull subscription.</span></span> <span data-ttu-id="cf84e-166">接続はすべて Windows 認証を使用して確立されます。</span><span class="sxs-lookup"><span data-stu-id="cf84e-166">All connections are made using Windows Authentication.</span></span>  
  
 [!code-sql[HowTo#bat_synctranpullsub_10](../../snippets/tsql/SQL15/replication/howto/tsql/synctranpullsub_10.bat)]  
  
 <span data-ttu-id="cf84e-167">次の例では、マージ エージェントを起動して、プル サブスクリプションを同期します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-167">The following example starts the Merge Agent to synchronize a pull subscription.</span></span> <span data-ttu-id="cf84e-168">接続はすべて Windows 認証を使用して確立されます。</span><span class="sxs-lookup"><span data-stu-id="cf84e-168">All connections are made using Windows Authentication.</span></span>  
  
 [!code-sql[HowTo#bat_syncmergepullsub_10](../../snippets/tsql/SQL15/replication/howto/tsql/syncmergepullsub_10.bat)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="cf84e-169">レプリケーション管理オブジェクト (RMO) の使用</span><span class="sxs-lookup"><span data-stu-id="cf84e-169">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="cf84e-170">レプリケーション管理オブジェクト (RMO) およびマネージド コードを使用してレプリケーション エージェント機能にアクセスすることで、プル サブスクリプションをプログラムから同期できます。</span><span class="sxs-lookup"><span data-stu-id="cf84e-170">You can synchronize pull subscriptions programmatically by using Replication Management Objects (RMO) and managed code access to replication agent functionalities.</span></span> <span data-ttu-id="cf84e-171">プル サブスクリプションを同期する際に使用するクラスは、サブスクリプションが属しているパブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="cf84e-171">The classes you use to synchronize a pull subscription depend on the type of publication to which the subscription belongs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cf84e-172">アプリケーションに影響を及ぼすことなく、自立的に実行される同期を開始するには、エージェントを非同期的に起動します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-172">If you want to start a synchronization that runs autonomously without affecting your application, start the agent asynchronously.</span></span> <span data-ttu-id="cf84e-173">ただし、同期処理中に同期の結果を監視し、エージェントからのコールバックを受け取る場合 (たとえば、進行状況バーを表示する場合)、エージェントを同期的に起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf84e-173">However, if you want to monitor the outcome of the synchronization and receive callbacks from the agent during the synchronization process (for example, to display a progress bar), you should start the agent synchronously.</span></span> <span data-ttu-id="cf84e-174">For [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] サブスクライバーの場合、エージェントを同期的に起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf84e-174">For [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] Subscribers, you must start the agent synchronously.</span></span>  
  
#### <a name="to-synchronize-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="cf84e-175">スナップショット パブリケーションまたはトランザクション パブリケーションに対するプル サブスクリプションを同期するには</span><span class="sxs-lookup"><span data-stu-id="cf84e-175">To synchronize a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="cf84e-176"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、サブスクライバーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-176">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="cf84e-177"><xref:Microsoft.SqlServer.Replication.TransPullSubscription> クラスのインスタンスを作成し、次のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-177">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> class, and set the following properties:</span></span>  
  
    -   <span data-ttu-id="cf84e-178"><xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>に、サブスクリプション データベースの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-178">The subscription database name for <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>.</span></span>  
  
    -   <span data-ttu-id="cf84e-179"><xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>に、サブスクリプションが属しているパブリケーションの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-179">The name of the publication to which the subscription belongs for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="cf84e-180"><xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>にパブリケーション データベース名を指定します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-180">The name of the publication database for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>.</span></span>  
  
    -   <span data-ttu-id="cf84e-181"><xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>に、パブリッシャーの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-181">The name of the Publisher for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.</span></span>  
  
    -   <span data-ttu-id="cf84e-182"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>に、手順 1. で作成した接続を設定します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-182">The connection created in step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="cf84e-183"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、その他のサブスクリプション プロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-183">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the remaining subscription properties.</span></span> <span data-ttu-id="cf84e-184">このメソッドが `false` を返す場合、サブスクリプションが存在するかどうかをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="cf84e-184">If this method returns `false`, verify that the subscription exists.</span></span>  
  
4.  <span data-ttu-id="cf84e-185">次のいずれかの方法で、サブスクライバーのディストリビューション エージェントを起動します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-185">Start the Distribution Agent at the Subscriber in one of the following ways:</span></span>  
  
    -   <span data-ttu-id="cf84e-186">手順 2. で作成した <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizeWithJob%2A> インスタンスの <xref:Microsoft.SqlServer.Replication.TransPullSubscription> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-186">Call the <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizeWithJob%2A> method on the instance of <xref:Microsoft.SqlServer.Replication.TransPullSubscription> from step 2.</span></span> <span data-ttu-id="cf84e-187">このメソッドは、ディストリビューション エージェントを非同期的に起動するため、エージェント ジョブの実行中、制御が直ちにアプリケーションに返されます。</span><span class="sxs-lookup"><span data-stu-id="cf84e-187">This method starts the Distribution Agent asynchronously, and control immediately returns to your application while the agent job is running.</span></span> <span data-ttu-id="cf84e-188">[!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] サブスクライバーの場合、または、<xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> の値に `false` (既定値) を指定して作成されたサブスクリプションの場合、このメソッドを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="cf84e-188">You cannot call this method for [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] Subscribers or if the subscription was created with a value of `false` for <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (the default).</span></span>  
  
    -   <span data-ttu-id="cf84e-189"><xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> プロパティから <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizationAgent%2A> クラスのインスタンスを取得し、 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-189">Get an instance of the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> class from the <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizationAgent%2A> property, and call the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> method.</span></span> <span data-ttu-id="cf84e-190">このメソッドにより、エージェントが同期的に起動され、制御は実行中のエージェント ジョブに残ります。</span><span class="sxs-lookup"><span data-stu-id="cf84e-190">This method starts the agent synchronously, and control remains with the running agent job.</span></span> <span data-ttu-id="cf84e-191">同期実行の間、エージェントの実行中に <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> イベントを処理できます。</span><span class="sxs-lookup"><span data-stu-id="cf84e-191">During synchronous execution, you can handle the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> event while the agent is running.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="cf84e-192">プルサブスクリプションを作成するときにの値を (既定値) に指定した場合は `false` <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> 、、、およびオプションで指定する必要があり <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Distributor%2A> <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorSecurityMode%2A> <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorLogin%2A> <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorPassword%2A> ます。これは、サブスクリプションのエージェントジョブに関連するメタデータが[MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql)で使用できないためです。</span><span class="sxs-lookup"><span data-stu-id="cf84e-192">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (the default) when you created the pull subscription, you also need to specify <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Distributor%2A>, <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorSecurityMode%2A>, and optionally <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorLogin%2A> and <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorPassword%2A> because the agent job related metadata for the subscription is not available in [MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql).</span></span>  
  
#### <a name="to-synchronize-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="cf84e-193">マージ パブリケーションに対するプル サブスクリプションを同期するには</span><span class="sxs-lookup"><span data-stu-id="cf84e-193">To synchronize a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="cf84e-194"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、サブスクライバーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-194">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="cf84e-195"><xref:Microsoft.SqlServer.Replication.MergePullSubscription> クラスのインスタンスを作成し、次のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-195">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> class, and set the following properties:</span></span>  
  
    -   <span data-ttu-id="cf84e-196"><xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>に、サブスクリプション データベースの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-196">The subscription database name for <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>.</span></span>  
  
    -   <span data-ttu-id="cf84e-197"><xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>に、サブスクリプションが属しているパブリケーションの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-197">The name of the publication to which the subscription belongs for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="cf84e-198">パブリッシュするデータベースの名前を <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>に指定します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-198">The name of the published database for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>.</span></span>  
  
    -   <span data-ttu-id="cf84e-199"><xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>に、パブリッシャーの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-199">The name of the Publisher for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.</span></span>  
  
    -   <span data-ttu-id="cf84e-200"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>に、手順 1. で作成した接続を設定します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-200">The connection created in step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="cf84e-201"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、その他のサブスクリプション プロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-201">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the remaining subscription properties.</span></span> <span data-ttu-id="cf84e-202">このメソッドが `false` を返す場合、サブスクリプションが存在するかどうかをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="cf84e-202">If this method returns `false`, verify that the subscription exists.</span></span>  
  
4.  <span data-ttu-id="cf84e-203">次のいずれかの方法で、サブスクライバーのマージ エージェントを起動します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-203">Start the Merge Agent at the Subscriber in one of the following ways:</span></span>  
  
    -   <span data-ttu-id="cf84e-204">手順 2. で作成した <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizeWithJob%2A> インスタンスの <xref:Microsoft.SqlServer.Replication.MergePullSubscription> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-204">Call the <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizeWithJob%2A> method on the instance of <xref:Microsoft.SqlServer.Replication.MergePullSubscription> from step 2.</span></span> <span data-ttu-id="cf84e-205">このメソッドは、マージ エージェントを非同期的に起動するため、エージェント ジョブの実行中、制御が直ちにアプリケーションに返されます。</span><span class="sxs-lookup"><span data-stu-id="cf84e-205">This method starts the Merge Agent asynchronously, and control immediately returns to your application while the agent job is running.</span></span> <span data-ttu-id="cf84e-206">[!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] サブスクライバーの場合、または、<xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> の値に `false` (既定値) を指定して作成されたサブスクリプションの場合、このメソッドを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="cf84e-206">You cannot call this method for [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] Subscribers or if the subscription was created with a value of `false` for <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (the default).</span></span>  
  
    -   <span data-ttu-id="cf84e-207"><xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> プロパティから <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizationAgent%2A> クラスのインスタンスを取得し、 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-207">Obtain an instance of the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> class from the <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizationAgent%2A> property, and call the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> method.</span></span> <span data-ttu-id="cf84e-208">このメソッドにより、マージ エージェントが同期的に起動され、制御は実行中のエージェント ジョブに残ります。</span><span class="sxs-lookup"><span data-stu-id="cf84e-208">This method starts the Merge Agent synchronously, and control remains with the running agent job.</span></span> <span data-ttu-id="cf84e-209">同期実行の間、エージェントの実行中に <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> イベントを処理できます。</span><span class="sxs-lookup"><span data-stu-id="cf84e-209">During synchronous execution, you can handle the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> event while the agent is running.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="cf84e-210">プルサブスクリプションの作成時に (既定値) を指定した場合は、、、、、、、およびオプションで、、、 `false` <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> およびを指定する必要もあり <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Distributor%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorSecurityMode%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherSecurityMode%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.HostName%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.SubscriptionType%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.ExchangeType%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorLogin%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorPassword%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherLogin%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherPassword%2A> ます。これは、サブスクリプションのエージェントジョブに関連するメタデータが[MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql)で使用できないためです。</span><span class="sxs-lookup"><span data-stu-id="cf84e-210">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (the default) when you created the pull subscription, you also need to specify <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Distributor%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorSecurityMode%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherSecurityMode%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.HostName%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.SubscriptionType%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.ExchangeType%2A>, and optionally <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorLogin%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorPassword%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherLogin%2A>, and <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherPassword%2A> because the agent job related metadata for the subscription is not available in [MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql).</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="cf84e-211">例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="cf84e-211">Examples (RMO)</span></span>  
 <span data-ttu-id="cf84e-212">次の例では、トランザクション パブリケーションへのプル サブスクリプションを同期します。エージェントはエージェント ジョブを使用して非同期的に起動されます。</span><span class="sxs-lookup"><span data-stu-id="cf84e-212">This example synchronizes a pull subscription to a transactional publication, where the agent is started asynchronously using the agent job.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncTranPullSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpullsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPullSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpullsub_withjob)]  
  
 <span data-ttu-id="cf84e-213">次の例では、トランザクション パブリケーションへのプル サブスクリプションを同期します。エージェントは同期的に起動されます。</span><span class="sxs-lookup"><span data-stu-id="cf84e-213">This example synchronizes a pull subscription to a transactional publication, where the agent is started synchronously.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncTranPullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpullsub)]  
  
 <span data-ttu-id="cf84e-214">次の例では、マージ パブリケーションへのプル サブスクリプションを同期します。エージェントはエージェント ジョブを使用して非同期的に起動されます。</span><span class="sxs-lookup"><span data-stu-id="cf84e-214">This example synchronizes a pull subscription to a merge publication, where the agent is started asynchronously using the agent job.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncMergePullSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepullsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePullSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepullsub_withjob)]  
  
 <span data-ttu-id="cf84e-215">次の例では、マージ パブリケーションへのプル サブスクリプションを同期します。エージェントは同期的に起動されます。</span><span class="sxs-lookup"><span data-stu-id="cf84e-215">This example synchronizes a pull subscription to a merge publication, where the agent is started synchronously.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncMergePullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepullsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepullsub)]  
  
 <span data-ttu-id="cf84e-216">次の例では、Web 同期を使用してマージ パブリケーションのプル サブスクリプションを同期します。</span><span class="sxs-lookup"><span data-stu-id="cf84e-216">This example synchronizes a pull subscription to a merge publication using Web synchronization.</span></span> <span data-ttu-id="cf84e-217">エージェントを同期的に起動し、追加のサブスクリプション情報が提供されるように、サブスクリプションは、エージェント ジョブや、関連するサブスクリプション メタデータを使わずに作成されます。</span><span class="sxs-lookup"><span data-stu-id="cf84e-217">The subscription was created without the agent job and related subscription metadata, so the agent must be started synchronously and additional subscription information is supplied.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncMergePullSub_NoJobWebSync](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepullsub_nojobwebsync)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePullSub_NoJobWebSync](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepullsub_nojobwebsync)]  
  
## <a name="see-also"></a><span data-ttu-id="cf84e-218">参照</span><span class="sxs-lookup"><span data-stu-id="cf84e-218">See Also</span></span>  
 <span data-ttu-id="cf84e-219">[データの同期](synchronize-data.md) </span><span class="sxs-lookup"><span data-stu-id="cf84e-219">[Synchronize Data](synchronize-data.md) </span></span>  
 <span data-ttu-id="cf84e-220">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="cf84e-220">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 [<span data-ttu-id="cf84e-221">レプリケーション セキュリティの推奨事項</span><span class="sxs-lookup"><span data-stu-id="cf84e-221">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
