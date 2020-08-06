---
title: サブスクリプションの再初期化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- initializing subscriptions [SQL Server replication], reinitializing
- subscriptions [SQL Server replication], reinitializing
- reinitializing subscriptions
ms.assetid: ca3625c5-c62e-4ab7-9829-d511f838e385
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f751928c05caa5c4acdcc6c667dc59bb7824021b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741773"
---
# <a name="reinitialize-a-subscription"></a><span data-ttu-id="822ce-102">サブスクリプションの再初期化</span><span class="sxs-lookup"><span data-stu-id="822ce-102">Reinitialize a Subscription</span></span>
  <span data-ttu-id="822ce-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、サブスクリプションを再初期化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="822ce-103">This topic describes how to reinitialize a subscription in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span> <span data-ttu-id="822ce-104">次回の同期で新しいスナップショットが適用されるように、個別のサブスクリプションに再初期化のマークを付けることができます。</span><span class="sxs-lookup"><span data-stu-id="822ce-104">Individual subscriptions can be marked for reinitialization so that a new snapshot is applied during the next synchronization.</span></span>  
  
 <span data-ttu-id="822ce-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="822ce-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="822ce-106">**サブスクリプションを再初期化するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="822ce-106">**To reinitialize a subscription, using:**</span></span>  
  
     [<span data-ttu-id="822ce-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="822ce-107">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="822ce-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="822ce-108">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="822ce-109">レプリケーション管理オブジェクト (RMO)</span><span class="sxs-lookup"><span data-stu-id="822ce-109">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="822ce-110">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="822ce-110">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="822ce-111">サブスクリプションの再初期化には、2 段階の処理があります。</span><span class="sxs-lookup"><span data-stu-id="822ce-111">Reinitializing a subscription is a two-part process:</span></span>  
  
1.  <span data-ttu-id="822ce-112">パブリケーションの単一のサブスクリプションまたはすべてのサブスクリプションが再初期化対象として *マーク* されます。</span><span class="sxs-lookup"><span data-stu-id="822ce-112">A single subscription or all subscriptions to a publication are *marked* for reinitialization.</span></span> <span data-ttu-id="822ce-113">サブスクリプションの再初期化のマークを設定するには、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の **[ローカル パブリケーション]** フォルダーおよび **[ローカル サブスクリプション]** フォルダーから **[サブスクリプションの再初期化]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="822ce-113">Mark subscriptions for reinitialization in the **Reinitialize Subscription(s)** dialog box, which is available from the **Local Publications** folder and the **Local Subscriptions** folder in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="822ce-114">また、 **[すべてのサブスクリプション]** タブやレプリケーション モニターのパブリケーション ノードからマークを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="822ce-114">You can also mark subscriptions from the **All Subscriptions** tab and the publications node in Replication Monitor.</span></span> <span data-ttu-id="822ce-115">レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor](monitor/start-the-replication-monitor.md)」 (レプリケーション モニターの開始) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="822ce-115">For information about starting Replication Monitor, see [Start the Replication Monitor](monitor/start-the-replication-monitor.md).</span></span> <span data-ttu-id="822ce-116">サブスクリプションの再初期化の設定には、以下のオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="822ce-116">When you mark a subscription for reinitialization, you have the following options:</span></span>  
  
     <span data-ttu-id="822ce-117">**[現在のスナップショットを使用する]**</span><span class="sxs-lookup"><span data-stu-id="822ce-117">**Use the current snapshot**</span></span>  
     <span data-ttu-id="822ce-118">このオプションを選択すると、次にディストリビューション エージェントまたはマージ エージェントが実行されたときに、現在のスナップショットがサブスクライバーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="822ce-118">Select to apply the current snapshot to the Subscriber the next time the Distribution Agent or Merge Agent runs.</span></span> <span data-ttu-id="822ce-119">有効なスナップショットが使用できない場合、このオプションは選択できません。</span><span class="sxs-lookup"><span data-stu-id="822ce-119">If there is no valid snapshot available, this option cannot be selected.</span></span>  
  
     <span data-ttu-id="822ce-120">**[新しいスナップショットを使用する]**</span><span class="sxs-lookup"><span data-stu-id="822ce-120">**Use a new snapshot**</span></span>  
     <span data-ttu-id="822ce-121">このオプションを選択すると、新しいスナップショットによってサブスクリプションが再初期化されます。</span><span class="sxs-lookup"><span data-stu-id="822ce-121">Select to reinitialize the subscription with a new snapshot.</span></span> <span data-ttu-id="822ce-122">スナップショットは、スナップショット エージェントによって生成された後にだけ、サブスクライバーに適用できます。</span><span class="sxs-lookup"><span data-stu-id="822ce-122">The snapshot can be applied to the Subscriber only after it has been generated by the Snapshot Agent.</span></span> <span data-ttu-id="822ce-123">スナップショットがスケジュールに従って実行されるように設定している場合は、スナップショット エージェントが次回実行されて終了するまでサブスクリプションを再初期化できません。</span><span class="sxs-lookup"><span data-stu-id="822ce-123">If the Snapshot Agent is set to run on a schedule, the subscription is not reinitialized until after the next scheduled Snapshot Agent run.</span></span> <span data-ttu-id="822ce-124">スナップショット エージェントをすぐに開始するには、 **[今すぐ新しいスナップショットを生成する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="822ce-124">Select **Generate the new snapshot now** to start the Snapshot Agent immediately.</span></span>  
  
     <span data-ttu-id="822ce-125">**[再初期化する前に、同期されていない変更をアップロード]**</span><span class="sxs-lookup"><span data-stu-id="822ce-125">**Upload unsynchronized changes before reinitialization**</span></span>  
     <span data-ttu-id="822ce-126">マージ レプリケーションのみです。</span><span class="sxs-lookup"><span data-stu-id="822ce-126">Merge replication only.</span></span> <span data-ttu-id="822ce-127">このオプションを選択すると、サブスクライバーのデータがスナップショットで上書きされる前に、保留中の変更がサブスクリプション データベースからアップロードされます。</span><span class="sxs-lookup"><span data-stu-id="822ce-127">Select to upload any pending changes from the subscription database before the data at the Subscriber is overwritten with a snapshot.</span></span>  
  
     <span data-ttu-id="822ce-128">パラメーター化フィルターを追加、削除、変更する場合は、再初期化の際、サブスクライバーで保留中の変更をパブリッシャーにアップロードできません。</span><span class="sxs-lookup"><span data-stu-id="822ce-128">If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="822ce-129">保留中の変更をアップロードしたい場合は、フィルターを変更する前にすべてのサブスクリプションを同期してください。</span><span class="sxs-lookup"><span data-stu-id="822ce-129">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
2.  <span data-ttu-id="822ce-130">サブスクリプションは、次回同期されるときに再初期化されます。ディストリビューション エージェント (トランザクション レプリケーションの場合) またはマージ エージェント (マージ レプリケーションの場合) により、再初期化するように設定されている各サブスクライバーに最新のスナップショットが適用されます。</span><span class="sxs-lookup"><span data-stu-id="822ce-130">A subscription is reinitialized the next time it is synchronized: the Distribution Agent (for transactional replication) or Merge Agent (for merge replication) applies the most recent snapshot to each Subscriber that has a subscription marked for reinitialization.</span></span> <span data-ttu-id="822ce-131">サブスクリプションの同期の詳細については、「 [Synchronize a Push Subscription](synchronize-a-push-subscription.md) 」および「 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="822ce-131">For more information about synchronizing subscriptions, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md) and [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
#### <a name="to-mark-a-single-push-or-pull-subscription-for-reinitialization-in-management-studio-at-the-publisher"></a><span data-ttu-id="822ce-132">Management Studio で単一のプッシュ サブスクリプションまたはプル サブスクリプションに再初期化を設定するには (パブリッシャーで実行)</span><span class="sxs-lookup"><span data-stu-id="822ce-132">To mark a single push or pull subscription for reinitialization in Management Studio (at the Publisher)</span></span>  
  
1.  <span data-ttu-id="822ce-133">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="822ce-133">Connect to the Publisher in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="822ce-134">**[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="822ce-134">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="822ce-135">再初期化するサブスクリプションが含まれているパブリケーションを展開します。</span><span class="sxs-lookup"><span data-stu-id="822ce-135">Expand the publication that has the subscription you want to reinitialize.</span></span>  
  
4.  <span data-ttu-id="822ce-136">サブスクリプションを右クリックし、 **[再初期化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="822ce-136">Right-click the subscription, and then click **Reinitialize**.</span></span>  
  
5.  <span data-ttu-id="822ce-137">**[サブスクリプションの再初期化]** ダイアログ ボックスでオプションを選択し、 **[再初期化するように設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="822ce-137">In the **Reinitialize Subscription(s)** dialog box, select options, and then click **Mark for Reinitialization**.</span></span>  
  
#### <a name="to-mark-a-single-pull-subscription-for-reinitialization-in-management-studio-at-the-subscriber"></a><span data-ttu-id="822ce-138">Management Studio で単一のプル サブスクリプションに再初期化を設定するには (サブスクライバーで実行)</span><span class="sxs-lookup"><span data-stu-id="822ce-138">To mark a single pull subscription for reinitialization in Management Studio (at the Subscriber)</span></span>  
  
1.  <span data-ttu-id="822ce-139">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でサブスクライバーに接続して、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="822ce-139">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="822ce-140">**[レプリケーション]** フォルダーを展開し、 **[ローカル サブスクリプション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="822ce-140">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="822ce-141">サブスクリプションを右クリックし、 **[再初期化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="822ce-141">Right-click the subscription, and then click **Reinitialize**.</span></span>  
  
4.  <span data-ttu-id="822ce-142">表示される確認のダイアログ ボックスで、 **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="822ce-142">In the confirmation dialog box that is displayed, click **Yes**.</span></span>  
  
#### <a name="to-mark-all-subscriptions-for-reinitialization-in-management-studio"></a><span data-ttu-id="822ce-143">Management Studio ですべてのサブスクリプションに再初期化を設定するには</span><span class="sxs-lookup"><span data-stu-id="822ce-143">To mark all subscriptions for reinitialization in Management Studio</span></span>  
  
1.  <span data-ttu-id="822ce-144">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="822ce-144">Connect to the Publisher in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="822ce-145">**[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="822ce-145">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="822ce-146">サブスクリプションを再初期化するパブリケーションを右クリックし、 **[すべてのサブスクリプションの再初期化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="822ce-146">Right-click the publication with subscriptions you want to reinitialize, and then click **Reinitialize All Subscriptions**.</span></span>  
  
4.  <span data-ttu-id="822ce-147">**[サブスクリプションの再初期化]** ダイアログ ボックスでオプションを選択し、 **[再初期化するように設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="822ce-147">In the **Reinitialize Subscription(s)** dialog box, select options, and then click **Mark for Reinitialization**.</span></span>  
  
#### <a name="to-mark-a-single-push-or-pull-subscription-for-reinitialization-in-replication-monitor"></a><span data-ttu-id="822ce-148">レプリケーション モニターで単一のプッシュ サブスクリプションまたはプル サブスクリプションに再初期化を設定するには</span><span class="sxs-lookup"><span data-stu-id="822ce-148">To mark a single push or pull subscription for reinitialization in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="822ce-149">レプリケーション モニターで、左ペインのパブリッシャー グループを展開し、パブリッシャーを展開してパブリケーションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="822ce-149">In Replication Monitor, expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="822ce-150">**[すべてのサブスクリプション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="822ce-150">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="822ce-151">再初期化するサブスクリプションを右クリックし、 **[サブスクリプションの再初期化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="822ce-151">Right-click the subscription you want to reinitialize, and then click **Reinitialize Subscription**.</span></span>  
  
4.  <span data-ttu-id="822ce-152">**[サブスクリプションの再初期化]** ダイアログ ボックスでオプションを選択し、 **[再初期化するように設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="822ce-152">In the **Reinitialize Subscription(s)** dialog box, select options, and then click **Mark for Reinitialization**.</span></span>  
  
#### <a name="to-mark-all-subscriptions-for-reinitialization-in-replication-monitor"></a><span data-ttu-id="822ce-153">レプリケーション モニターですべてのサブスクリプションに再初期化を設定するには</span><span class="sxs-lookup"><span data-stu-id="822ce-153">To mark all subscriptions for reinitialization in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="822ce-154">レプリケーション モニターの左ペインでパブリッシャー グループを展開し、パブリッシャーを展開します。</span><span class="sxs-lookup"><span data-stu-id="822ce-154">In Replication Monitor, expand a Publisher group in the left pane, and then expand a Publisher.</span></span>  
  
2.  <span data-ttu-id="822ce-155">サブスクリプションを再初期化するパブリケーションを右クリックし、 **[すべてのサブスクリプションの再初期化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="822ce-155">Right-click the publication with subscriptions you want to reinitialize, and then click **Reinitialize All Subscriptions**.</span></span>  
  
3.  <span data-ttu-id="822ce-156">**[サブスクリプションの再初期化]** ダイアログ ボックスでオプションを選択し、 **[再初期化するように設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="822ce-156">In the **Reinitialize Subscription(s)** dialog box, select options, and then click **Mark for Reinitialization**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="822ce-157">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="822ce-157">Using Transact-SQL</span></span>  
 <span data-ttu-id="822ce-158">サブスクリプションは、プログラムでレプリケーション ストアド プロシージャを使用して再初期化できます。</span><span class="sxs-lookup"><span data-stu-id="822ce-158">Subscriptions can be reinitialized programmatically using replication stored procedures.</span></span> <span data-ttu-id="822ce-159">使用するストアド プロシージャは、サブスクリプションの種類 (プッシュまたはプル) およびサブスクリプションが属しているパブリケーションの種類によって変わります。</span><span class="sxs-lookup"><span data-stu-id="822ce-159">The stored procedure that is used depends on the type of subscription (push or pull) and the type of publication to which the subscription belongs.</span></span>  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-transactional-publication"></a><span data-ttu-id="822ce-160">トランザクション パブリケーションに対するプル サブスクリプションを再初期化するには</span><span class="sxs-lookup"><span data-stu-id="822ce-160">To reinitialize a pull subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="822ce-161">サブスクライバー側のサブスクリプション データベースに対して、[sp_reinitpullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitpullsubscription-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="822ce-161">At the Subscriber on the subscription database, execute [sp_reinitpullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitpullsubscription-transact-sql).</span></span> <span data-ttu-id="822ce-162">**@publisher**、、およびを指定し **@publisher_db** **@publication** ます。</span><span class="sxs-lookup"><span data-stu-id="822ce-162">Specify **@publisher**, **@publisher_db**, and **@publication**.</span></span> <span data-ttu-id="822ce-163">これにより、ディストリビューション エージェントの次回実行時に再初期化するようにサブスクリプションにマークが付けられます。</span><span class="sxs-lookup"><span data-stu-id="822ce-163">This marks the subscription for reinitialization the next time the Distribution Agent runs.</span></span>  
  
2.  <span data-ttu-id="822ce-164">(省略可) サブスクライバーでディストリビューション エージェントを起動し、サブスクリプションを同期します。</span><span class="sxs-lookup"><span data-stu-id="822ce-164">(Optional) Start the Distribution Agent at the Subscriber to synchronize the subscription.</span></span> <span data-ttu-id="822ce-165">詳細については、「 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="822ce-165">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-transactional-publication"></a><span data-ttu-id="822ce-166">トランザクション パブリケーションに対するプッシュ サブスクリプションを再初期化するには</span><span class="sxs-lookup"><span data-stu-id="822ce-166">To reinitialize a push subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="822ce-167">パブリッシャーで、[sp_reinitsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitsubscription-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="822ce-167">At the Publisher, execute [sp_reinitsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitsubscription-transact-sql).</span></span> <span data-ttu-id="822ce-168">**@publication**、、およびを指定し **@subscriber** **@destination_db** ます。</span><span class="sxs-lookup"><span data-stu-id="822ce-168">Specify **@publication**, **@subscriber**, and **@destination_db**.</span></span> <span data-ttu-id="822ce-169">これにより、ディストリビューション エージェントの次回実行時に再初期化するようにサブスクリプションにマークが付けられます。</span><span class="sxs-lookup"><span data-stu-id="822ce-169">This marks the subscription for reinitialization the next time the Distribution Agent runs.</span></span>  
  
2.  <span data-ttu-id="822ce-170">(省略可) ディストリビューターでディストリビューション エージェントを起動し、サブスクリプションを同期します。</span><span class="sxs-lookup"><span data-stu-id="822ce-170">(Optional) Start the Distribution Agent at the Distributor to synchronize the subscription.</span></span> <span data-ttu-id="822ce-171">詳細については、「 [プッシュ サブスクリプションの同期](synchronize-a-push-subscription.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="822ce-171">For more information, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="822ce-172">マージ パブリケーションに対するプル サブスクリプションを再初期化するには</span><span class="sxs-lookup"><span data-stu-id="822ce-172">To reinitialize a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="822ce-173">サブスクライバー側のサブスクリプション データベースに対して、[sp_reinitmergepullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitmergepullsubscription-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="822ce-173">At the Subscriber on the subscription database, execute [sp_reinitmergepullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitmergepullsubscription-transact-sql).</span></span> <span data-ttu-id="822ce-174">**@publisher**、、およびを指定し **@publisher_db** **@publication** ます。</span><span class="sxs-lookup"><span data-stu-id="822ce-174">Specify **@publisher**, **@publisher_db**, and **@publication**.</span></span> <span data-ttu-id="822ce-175">再初期化が発生する前にサブスクライバーから変更をアップロードするには、に値を指定し `true` **@upload_first** ます。</span><span class="sxs-lookup"><span data-stu-id="822ce-175">To upload changes from the Subscriber before reinitialization occurs, specify a value of `true` for **@upload_first**.</span></span> <span data-ttu-id="822ce-176">これにより、マージ エージェントの次回実行時に再初期化するようにサブスクリプションにマークが付けられます。</span><span class="sxs-lookup"><span data-stu-id="822ce-176">This marks the subscription for reinitialization the next time the Merge Agent runs.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="822ce-177">パラメーター化フィルターを追加、削除、変更する場合は、再初期化の際、サブスクライバーで保留中の変更をパブリッシャーにアップロードできません。</span><span class="sxs-lookup"><span data-stu-id="822ce-177">If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="822ce-178">保留中の変更をアップロードしたい場合は、フィルターを変更する前にすべてのサブスクリプションを同期してください。</span><span class="sxs-lookup"><span data-stu-id="822ce-178">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
2.  <span data-ttu-id="822ce-179">(省略可) サブスクライバーでマージ エージェントを起動し、サブスクリプションを同期します。</span><span class="sxs-lookup"><span data-stu-id="822ce-179">(Optional) Start the Merge Agent at the Subscriber to synchronize the subscription.</span></span> <span data-ttu-id="822ce-180">詳細については、「 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="822ce-180">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="822ce-181">マージ パブリケーションに対するプッシュ サブスクリプションを再初期化するには</span><span class="sxs-lookup"><span data-stu-id="822ce-181">To reinitialize a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="822ce-182">パブリッシャーで、[sp_reinitmergesubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitmergesubscription-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="822ce-182">At the Publisher, execute [sp_reinitmergesubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitmergesubscription-transact-sql).</span></span> <span data-ttu-id="822ce-183">**@publication**、、およびを指定し **@subscriber** **@subscriber_db** ます。</span><span class="sxs-lookup"><span data-stu-id="822ce-183">Specify **@publication**, **@subscriber**, and **@subscriber_db**.</span></span> <span data-ttu-id="822ce-184">再初期化が発生する前にサブスクライバーから変更をアップロードするには、に値を指定し `true` **@upload_first** ます。</span><span class="sxs-lookup"><span data-stu-id="822ce-184">To upload changes from the Subscriber before reinitialization occurs, specify a value of `true` for **@upload_first**.</span></span> <span data-ttu-id="822ce-185">これにより、ディストリビューション エージェントの次回実行時に再初期化するようにサブスクリプションにマークが付けられます。</span><span class="sxs-lookup"><span data-stu-id="822ce-185">This marks the subscription for reinitialization the next time the Distribution Agent runs.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="822ce-186">パラメーター化フィルターを追加、削除、変更する場合は、再初期化の際、サブスクライバーで保留中の変更をパブリッシャーにアップロードできません。</span><span class="sxs-lookup"><span data-stu-id="822ce-186">If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="822ce-187">保留中の変更をアップロードしたい場合は、フィルターを変更する前にすべてのサブスクリプションを同期してください。</span><span class="sxs-lookup"><span data-stu-id="822ce-187">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
2.  <span data-ttu-id="822ce-188">(省略可) ディストリビューターでマージ エージェントを起動し、サブスクリプションを同期します。</span><span class="sxs-lookup"><span data-stu-id="822ce-188">(Optional) Start the Merge Agent at the Distributor to synchronize the subscription.</span></span> <span data-ttu-id="822ce-189">詳細については、「 [プッシュ サブスクリプションの同期](synchronize-a-push-subscription.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="822ce-189">For more information, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
#### <a name="to-set-the-reinitialization-policy-when-creating-a-new-merge-publication"></a><span data-ttu-id="822ce-190">新しいマージ パブリケーションを作成するときに再初期化ポリシーを設定するには</span><span class="sxs-lookup"><span data-stu-id="822ce-190">To set the reinitialization policy when creating a new merge publication</span></span>  
  
1.  <span data-ttu-id="822ce-191">パブリッシャー側のパブリケーション データベースで、 [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)を実行し、次のいずれかの値を **@automatic_reinitialization_policy**に指定します。</span><span class="sxs-lookup"><span data-stu-id="822ce-191">At the Publisher on the publication database, execute [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql), specifying one of the following values for **@automatic_reinitialization_policy**:</span></span>  
  
    -   <span data-ttu-id="822ce-192">**1** - パブリケーションに対する変更に応じてサブスクリプションが自動的に再初期化される前に、サブスクライバーの変更がアップロードされます。</span><span class="sxs-lookup"><span data-stu-id="822ce-192">**1** - changes are uploaded from the Subscriber before a subscription is automatically reinitialized as required by a change to the publication.</span></span>  
  
    -   <span data-ttu-id="822ce-193">**0** - パブリケーションに対する変更に応じてサブスクリプションが自動的に再初期化されるときに、サブスクライバーの変更は破棄されます。</span><span class="sxs-lookup"><span data-stu-id="822ce-193">**0** - changes at the Subscriber are discarded when a subscription is automatically reinitialized as required by a change to the publication.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="822ce-194">パラメーター化フィルターを追加、削除、変更する場合は、再初期化の際、サブスクライバーで保留中の変更をパブリッシャーにアップロードできません。</span><span class="sxs-lookup"><span data-stu-id="822ce-194">If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="822ce-195">保留中の変更をアップロードしたい場合は、フィルターを変更する前にすべてのサブスクリプションを同期してください。</span><span class="sxs-lookup"><span data-stu-id="822ce-195">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
     <span data-ttu-id="822ce-196">詳しくは、「 [パブリケーションを作成](publish/create-a-publication.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="822ce-196">For more information, see [Create a Publication](publish/create-a-publication.md).</span></span>  
  
#### <a name="to-change-the-reinitialization-policy-for-an-existing-merge-publication"></a><span data-ttu-id="822ce-197">既存のマージ パブリケーションの再初期化ポリシーを変更するには</span><span class="sxs-lookup"><span data-stu-id="822ce-197">To change the reinitialization policy for an existing merge publication</span></span>  
  
1.  <span data-ttu-id="822ce-198">パブリッシャー側のパブリケーション データベースで、 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)を実行します。 **@property** @upload_first **@property** を指定し、次のいずれかの値を **@value**に指定します。</span><span class="sxs-lookup"><span data-stu-id="822ce-198">At the Publisher on the publication database, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), specifying **automatic_reinitialization_policy** for **@property** and one of the following values for **@value**:</span></span>  
  
    -   <span data-ttu-id="822ce-199">**1** - パブリケーションに対する変更に応じてサブスクリプションが自動的に再初期化される前に、サブスクライバーの変更がアップロードされます。</span><span class="sxs-lookup"><span data-stu-id="822ce-199">**1** - changes are uploaded from the Subscriber before a subscription is automatically reinitialized as required by a change to the publication.</span></span>  
  
    -   <span data-ttu-id="822ce-200">**0** - パブリケーションに対する変更に応じてサブスクリプションが自動的に再初期化されるときに、サブスクライバーの変更は破棄されます。</span><span class="sxs-lookup"><span data-stu-id="822ce-200">**0** - changes at the Subscriber are discarded when a subscription is automatically reinitialized as required by a change to the publication.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="822ce-201">パラメーター化フィルターを追加、削除、変更する場合は、再初期化の際、サブスクライバーで保留中の変更をパブリッシャーにアップロードできません。</span><span class="sxs-lookup"><span data-stu-id="822ce-201">If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="822ce-202">保留中の変更をアップロードしたい場合は、フィルターを変更する前にすべてのサブスクリプションを同期してください。</span><span class="sxs-lookup"><span data-stu-id="822ce-202">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
     <span data-ttu-id="822ce-203">詳しくは、「 [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="822ce-203">For more information, see [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).</span></span>  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="822ce-204">レプリケーション管理オブジェクト (RMO) の使用</span><span class="sxs-lookup"><span data-stu-id="822ce-204">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="822ce-205">次回の同期で新しいスナップショットが適用されるように、個別のサブスクリプションに再初期化のマークを付けることができます。</span><span class="sxs-lookup"><span data-stu-id="822ce-205">Individual subscriptions can be marked for reinitialization so that during the next synchronization, a new snapshot is applied.</span></span> <span data-ttu-id="822ce-206">レプリケーション管理オブジェクト (RMO) を使用することで、プログラムによってサブスクリプションを再初期化できます。</span><span class="sxs-lookup"><span data-stu-id="822ce-206">Subscriptions can be reinitialized programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="822ce-207">使用するクラスは、サブスクリプションが属するパブリケーションの種類と、サブスクリプションの種類 (プッシュ サブスクリプションまたはプル サブスクリプション) に応じて変わります。</span><span class="sxs-lookup"><span data-stu-id="822ce-207">The classes you use depend on the type of publication to which the subscription belongs and the type of subscription (that is, a push or pull subscription).</span></span>  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-transactional-publication"></a><span data-ttu-id="822ce-208">トランザクション パブリケーションに対するプル サブスクリプションを再初期化するには</span><span class="sxs-lookup"><span data-stu-id="822ce-208">To reinitialize a pull subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="822ce-209"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、サブスクライバーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="822ce-209">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="822ce-210"><xref:Microsoft.SqlServer.Replication.TransPullSubscription> クラスのインスタンスを作成し、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>を設定して、手順 1. の接続を <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>に設定します。</span><span class="sxs-lookup"><span data-stu-id="822ce-210">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> class, and set <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>, and the connection from step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="822ce-211"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="822ce-211">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="822ce-212">このメソッドが `false` を返す場合、手順 2. でサブスクリプション プロパティを不適切に設定したか、プル サブスクリプションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="822ce-212">If this method returns `false`, either the subscription properties in step 2 were defined incorrectly or the pull subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="822ce-213"><xref:Microsoft.SqlServer.Replication.TransPullSubscription.Reinitialize%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="822ce-213">Call the <xref:Microsoft.SqlServer.Replication.TransPullSubscription.Reinitialize%2A> method.</span></span> <span data-ttu-id="822ce-214">このメソッドにより、サブスクリプションを再初期化するようにマークされます。</span><span class="sxs-lookup"><span data-stu-id="822ce-214">This method marks the subscription for reinitialization.</span></span>  
  
5.  <span data-ttu-id="822ce-215">プル サブスクリプションを同期します。</span><span class="sxs-lookup"><span data-stu-id="822ce-215">Synchronize the pull subscription.</span></span> <span data-ttu-id="822ce-216">詳細については、「 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="822ce-216">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-transactional-publication"></a><span data-ttu-id="822ce-217">トランザクション パブリケーションに対するプッシュ サブスクリプションを再初期化するには</span><span class="sxs-lookup"><span data-stu-id="822ce-217">To reinitialize a push subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="822ce-218"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="822ce-218">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="822ce-219"><xref:Microsoft.SqlServer.Replication.TransSubscription> クラスのインスタンスを作成し、 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>を設定して、手順 1. の接続を <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>に設定します。</span><span class="sxs-lookup"><span data-stu-id="822ce-219">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransSubscription> class, and set <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, and the connection from step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="822ce-220"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="822ce-220">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="822ce-221">このメソッドが `false` を返す場合、手順 2. でサブスクリプション プロパティを不適切に設定したか、プッシュ サブスクリプションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="822ce-221">If this method returns `false`, either the subscription properties in step 2 were defined incorrectly or the push subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="822ce-222"><xref:Microsoft.SqlServer.Replication.TransSubscription.Reinitialize%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="822ce-222">Call the <xref:Microsoft.SqlServer.Replication.TransSubscription.Reinitialize%2A> method.</span></span> <span data-ttu-id="822ce-223">このメソッドにより、サブスクリプションを再初期化するようにマークされます。</span><span class="sxs-lookup"><span data-stu-id="822ce-223">This method marks the subscription for reinitialization.</span></span>  
  
5.  <span data-ttu-id="822ce-224">プッシュ サブスクリプションを同期します。</span><span class="sxs-lookup"><span data-stu-id="822ce-224">Synchronize the push subscription.</span></span> <span data-ttu-id="822ce-225">詳細については、「 [プッシュ サブスクリプションの同期](synchronize-a-push-subscription.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="822ce-225">For more information, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="822ce-226">マージ パブリケーションに対するプル サブスクリプションを再初期化するには</span><span class="sxs-lookup"><span data-stu-id="822ce-226">To reinitialize a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="822ce-227"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、サブスクライバーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="822ce-227">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="822ce-228"><xref:Microsoft.SqlServer.Replication.MergePullSubscription> クラスのインスタンスを作成し、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>を設定して、手順 1. の接続を <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>に設定します。</span><span class="sxs-lookup"><span data-stu-id="822ce-228">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> class, and set <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>, and the connection from step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="822ce-229"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="822ce-229">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="822ce-230">このメソッドが `false` を返す場合、手順 2. でサブスクリプション プロパティを不適切に設定したか、プル サブスクリプションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="822ce-230">If this method returns `false`, either the subscription properties in step 2 were defined incorrectly or the pull subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="822ce-231"><xref:Microsoft.SqlServer.Replication.MergePullSubscription.Reinitialize%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="822ce-231">Call the <xref:Microsoft.SqlServer.Replication.MergePullSubscription.Reinitialize%2A> method.</span></span> <span data-ttu-id="822ce-232">再初期化の前に `true` を渡してサブスクライバーの変更をアップロードするか、`false` を渡して再初期化し、サブスクライバーの保留中の変更をすべて破棄します。</span><span class="sxs-lookup"><span data-stu-id="822ce-232">Pass a value of `true` to upload changes at the Subscriber before reinitialization or a value of `false` to reinitialize and lose any pending changes at the Subscriber.</span></span> <span data-ttu-id="822ce-233">このメソッドにより、サブスクリプションを再初期化するようにマークされます。</span><span class="sxs-lookup"><span data-stu-id="822ce-233">This method marks the subscription for reinitialization.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="822ce-234">サブスクリプションの有効期限が切れると、変更をアップロードできません。</span><span class="sxs-lookup"><span data-stu-id="822ce-234">Changes cannot be uploaded if the subscription is expired.</span></span> <span data-ttu-id="822ce-235">詳しくは、「 [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="822ce-235">For more information, see [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md).</span></span>  
  
5.  <span data-ttu-id="822ce-236">プル サブスクリプションを同期します。</span><span class="sxs-lookup"><span data-stu-id="822ce-236">Synchronize the pull subscription.</span></span> <span data-ttu-id="822ce-237">詳細については、「 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="822ce-237">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="822ce-238">マージ パブリケーションに対するプッシュ サブスクリプションを再初期化するには</span><span class="sxs-lookup"><span data-stu-id="822ce-238">To reinitialize a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="822ce-239"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="822ce-239">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="822ce-240"><xref:Microsoft.SqlServer.Replication.MergeSubscription> クラスのインスタンスを作成し、 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>を設定して、手順 1. の接続を <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>に設定します。</span><span class="sxs-lookup"><span data-stu-id="822ce-240">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> class, and set <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, and the connection from step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="822ce-241"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="822ce-241">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="822ce-242">このメソッドが `false` を返す場合、手順 2. でサブスクリプション プロパティを不適切に設定したか、プッシュ サブスクリプションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="822ce-242">If this method returns `false`, either the subscription properties in step 2 were defined incorrectly or the push subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="822ce-243"><xref:Microsoft.SqlServer.Replication.MergeSubscription.Reinitialize%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="822ce-243">Call the <xref:Microsoft.SqlServer.Replication.MergeSubscription.Reinitialize%2A> method.</span></span> <span data-ttu-id="822ce-244">再初期化の前に `true` を渡してサブスクライバーの変更をアップロードするか、`false` を渡して再初期化し、サブスクライバーの保留中の変更をすべて破棄します。</span><span class="sxs-lookup"><span data-stu-id="822ce-244">Pass a value of `true` to upload changes at the Subscriber before reinitialization or a value of `false` to reinitialize and lose any pending changes at the Subscriber.</span></span> <span data-ttu-id="822ce-245">このメソッドにより、サブスクリプションを再初期化するようにマークされます。</span><span class="sxs-lookup"><span data-stu-id="822ce-245">This method marks the subscription for reinitialization.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="822ce-246">サブスクリプションの有効期限が切れると、変更をアップロードできません。</span><span class="sxs-lookup"><span data-stu-id="822ce-246">Changes cannot be uploaded if the subscription is expired.</span></span> <span data-ttu-id="822ce-247">詳しくは、「 [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="822ce-247">For more information, see [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md).</span></span>  
  
5.  <span data-ttu-id="822ce-248">プッシュ サブスクリプションを同期します。</span><span class="sxs-lookup"><span data-stu-id="822ce-248">Synchronize the push subscription.</span></span> <span data-ttu-id="822ce-249">詳細については、「 [プッシュ サブスクリプションの同期](synchronize-a-push-subscription.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="822ce-249">For more information, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="822ce-250">例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="822ce-250">Examples (RMO)</span></span>  
 <span data-ttu-id="822ce-251">次の例では、トランザクション パブリケーションに対するプル サブスクリプションを再初期化します。</span><span class="sxs-lookup"><span data-stu-id="822ce-251">This example reinitializes a pull subscription to a transactional publication.</span></span>  
  
 [!code-csharp[HowTo#rmo_ReinitTranPullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_reinittranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_ReinitTranPullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_reinittranpullsub)]  
  
 <span data-ttu-id="822ce-252">次の例では、最初にサブスクライバーの保留中の変更をアップロードした後、マージ パブリケーションに対するプル サブスクリプションを初期化します。</span><span class="sxs-lookup"><span data-stu-id="822ce-252">This example reinitializes a pull subscription to a merge publication after first uploading pending changes at the Subscriber.</span></span>  
  
 [!code-csharp[HowTo#rmo_ReinitMergePullSub_WithUpload](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_reinitmergepullsub_withupload)]  
  
 [!code-vb[HowTo#rmo_vb_ReinitMergePullSub_WithUpload](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_reinitmergepullsub_withupload)]  
  
## <a name="see-also"></a><span data-ttu-id="822ce-253">参照</span><span class="sxs-lookup"><span data-stu-id="822ce-253">See Also</span></span>  
 <span data-ttu-id="822ce-254">[サブスクリプションの再初期化](reinitialize-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="822ce-254">[Reinitialize Subscriptions](reinitialize-subscriptions.md) </span></span>  
 <span data-ttu-id="822ce-255">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="822ce-255">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span></span>  
 [<span data-ttu-id="822ce-256">レプリケーション セキュリティの推奨事項</span><span class="sxs-lookup"><span data-stu-id="822ce-256">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
