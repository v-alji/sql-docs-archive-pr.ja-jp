---
title: 更新可能トランザクション サブスクリプションの更新モードの切り替え | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, updatable subscriptions
- updatable subscriptions, update modes
- subscriptions [SQL Server replication], updatable
ms.assetid: ab5ebab1-7ee4-41f4-999b-b4f0c420c921
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c31814d1e2ab6fac64ffcde883f3cac2439828a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646139"
---
# <a name="switch-between-update-modes-for-an-updatable-transactional-subscription"></a><span data-ttu-id="7cabf-102">更新可能トランザクション サブスクリプションの更新モードの切り替え</span><span class="sxs-lookup"><span data-stu-id="7cabf-102">Switch Between Update Modes for an Updatable Transactional Subscription</span></span>
  <span data-ttu-id="7cabf-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、更新可能トランザクション サブスクリプションの更新モードを切り替える方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7cabf-103">This topic describes how to switch between update modes for an updatable transaction subscription in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="7cabf-104">サブスクリプションの新規作成ウィザードを使用して、更新可能サブスクリプションのモードを指定します。</span><span class="sxs-lookup"><span data-stu-id="7cabf-104">Specify the mode for updatable subscriptions using the New Subscription Wizard.</span></span> <span data-ttu-id="7cabf-105">このウィザードを使用する場合のモードの設定については、「[プル サブスクリプションのプロパティの表示または変更](../view-and-modify-pull-subscription-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cabf-105">For information about setting the mode when using this wizard, see [View and Modify Pull Subscription Properties](../view-and-modify-pull-subscription-properties.md).</span></span>  
  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7cabf-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="7cabf-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="7cabf-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="7cabf-107">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="7cabf-108">即時更新からキュー更新に、いつでもフェールオーバーできます。</span><span class="sxs-lookup"><span data-stu-id="7cabf-108">You can fail over from immediate to queued updating at any time.</span></span> <span data-ttu-id="7cabf-109">ただしそれ以降、サブスクライバーとパブリッシャーが接続され、キュー リーダー エージェントによってキュー内の保留中メッセージがすべてパブリッシャーに適用されるまで、即時更新に戻すことはできません。</span><span class="sxs-lookup"><span data-stu-id="7cabf-109">After you do, however, you cannot return to immediate updating until the Subscriber and Publisher are connected and the Queue Reader Agent has applied all pending messages in the queue to the Publisher.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="7cabf-110">推奨事項</span><span class="sxs-lookup"><span data-stu-id="7cabf-110">Recommendations</span></span>  
  
-   <span data-ttu-id="7cabf-111">トランザクション パブリケーションへの更新サブスクリプションで更新モード間のフェールオーバーがサポートされている場合、接続が短時間で変化する状況に対応するために、更新モードをプログラムで変更することができます。</span><span class="sxs-lookup"><span data-stu-id="7cabf-111">When an updating subscription to a transactional publication supports failover from one updating mode to another, you can programmatically switch update modes to handle situations when connectivity changes for a short period of time.</span></span> <span data-ttu-id="7cabf-112">更新モードはレプリケーション ストアド プロシージャを使用して、プログラムから設定することも、要求時に設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="7cabf-112">The update mode can be set programmatically and on demand using replication stored procedures.</span></span> <span data-ttu-id="7cabf-113">詳細については、「 [Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cabf-113">For more information, see [Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7cabf-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="7cabf-114">Using SQL Server Management Studio</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7cabf-115">サブスクリプションを作成した後で更新モードを変更するには、 **update_mode** プロパティを **failover** (即時更新をキュー更新に切り替え) または **queued failover** (キュー更新を即時更新に切り替え) に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7cabf-115">To change the update mode after the subscription is created, the **update_mode** property must be set to **failover** (which allows a switch from immediate updating to queued updating) or **queued failover** (which allows a switch from queued updating to immediate updating) when the subscription is created.</span></span> <span data-ttu-id="7cabf-116">これらのプロパティは、サブスクリプションの新規作成ウィザードで自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="7cabf-116">These properties are set automatically in the New Subscription Wizard.</span></span>  
  
#### <a name="to-set-the-updating-mode-for-a-push-subscription"></a><span data-ttu-id="7cabf-117">プッシュ サブスクリプションの更新モードを設定するには</span><span class="sxs-lookup"><span data-stu-id="7cabf-117">To set the updating mode for a push subscription</span></span>  
  
1.  <span data-ttu-id="7cabf-118">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]でサブスクライバーに接続して、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="7cabf-118">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="7cabf-119">**[レプリケーション]** フォルダーを展開し、 **[ローカル サブスクリプション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="7cabf-119">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="7cabf-120">更新モードを設定するサブスクリプションを右クリックしてから、 **[更新方法の設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7cabf-120">Right-click the subscription for which you want to set the update mode, and then click **Set Update Method**.</span></span>  
  
4.  <span data-ttu-id="7cabf-121">**[更新方法の設定 - \<Subscriber>: \<SubscriptionDatabase>]** ダイアログ ボックスで、 **[即時更新]** または **[キュー更新]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7cabf-121">In the **Set Update Method - \<Subscriber>: \<SubscriptionDatabase>** dialog box, select **Immediate updating** or **Queued updating**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-set-the-updating-mode-for-a-pull-subscription"></a><span data-ttu-id="7cabf-122">プル サブスクリプションの更新モードを設定するには</span><span class="sxs-lookup"><span data-stu-id="7cabf-122">To set the updating mode for a pull subscription</span></span>  
  
1.  <span data-ttu-id="7cabf-123">**[サブスクリプションのプロパティ - \<Publisher>: \<PublicationDatabase>]** ダイアログ ボックスの **[サブスクライバーの更新方法]** オプションで、 **[変更をすぐにレプリケートする]** または **[変更をキューに登録]** のいずれかの値を選択します。</span><span class="sxs-lookup"><span data-stu-id="7cabf-123">In the **Subscription Properties - \<Publisher>: \<PublicationDatabase>** dialog box, select a value of **Immediately replicate changes** or **Queue changes** for the **Subscriber update method** option.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="7cabf-124">**[サブスクリプションのプロパティ - \<Publisher>: \<PublicationDatabase>]** ダイアログ ボックスへのアクセスの詳細については、「[プル サブスクリプションのプロパティの表示または変更](../view-and-modify-pull-subscription-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cabf-124">For more information about accessing the **Subscription Properties - \<Publisher>: \<PublicationDatabase>** dialog box, see [View and Modify Pull Subscription Properties](../view-and-modify-pull-subscription-properties.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7cabf-125">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="7cabf-125">Using Transact-SQL</span></span>  
  
#### <a name="to-switch-between-update-modes"></a><span data-ttu-id="7cabf-126">更新モードを切り替えるには</span><span class="sxs-lookup"><span data-stu-id="7cabf-126">To switch between update modes</span></span>  
  
1.  <span data-ttu-id="7cabf-127">プル サブスクリプションの場合は [sp_helppullsubscription](/sql/relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql) 、プッシュ サブスクリプションの場合は [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql) を実行して、サブスクリプションでフェールオーバーがサポートされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7cabf-127">Verify that the subscription supports failover by executing [sp_helppullsubscription](/sql/relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql) for a pull subscription or [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql) for a push subscription.</span></span> <span data-ttu-id="7cabf-128">結果セットの **update mode** の値が **3** または **4**の場合、フェールオーバーがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7cabf-128">If the value of **update mode** in the result set is **3** or **4**, failover is supported.</span></span>  
  
2.  <span data-ttu-id="7cabf-129">サブスクライバー側のサブスクリプション データベースに対して、 [sp_setreplfailovermode](/sql/relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="7cabf-129">At the Subscriber on the subscription database, execute [sp_setreplfailovermode](/sql/relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql).</span></span> <span data-ttu-id="7cabf-130">**@publisher**、、 **@publisher_db** **@publication** 、およびに対して次のいずれかの値を指定し **@failover_mode** ます。</span><span class="sxs-lookup"><span data-stu-id="7cabf-130">Specify **@publisher**, **@publisher_db**, **@publication**, and one of the following values for **@failover_mode**:</span></span>  
  
    -   <span data-ttu-id="7cabf-131">**queued** - 接続が一時的に失われた場合、キュー更新にフェールオーバーします。</span><span class="sxs-lookup"><span data-stu-id="7cabf-131">**queued** - fail over to queued updating when connectivity has been temporarily lost.</span></span>  
  
    -   <span data-ttu-id="7cabf-132">**immediate** - 接続が回復した場合、即時更新にフェールオーバーします。</span><span class="sxs-lookup"><span data-stu-id="7cabf-132">**immediate** - fail over to immediate updating when connectivity has been restored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cabf-133">参照</span><span class="sxs-lookup"><span data-stu-id="7cabf-133">See Also</span></span>  
 [<span data-ttu-id="7cabf-134">Updatable Subscriptions for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="7cabf-134">Updatable Subscriptions for Transactional Replication</span></span>](../transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
