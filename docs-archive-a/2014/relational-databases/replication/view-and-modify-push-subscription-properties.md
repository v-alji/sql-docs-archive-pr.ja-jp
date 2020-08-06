---
title: プッシュ サブスクリプションのプロパティの表示または変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing replication properties
- push subscriptions [SQL Server replication], properties
- subscriptions [SQL Server replication], push
- push subscriptions [SQL Server replication], modifying
- modifying replication properties, push subscriptions
- modifying subscriptions, SQL Server Management Studio
ms.assetid: 801d2995-7aa5-4626-906e-c8190758ec71
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c1506d4f83fcfb94d62efd01c4d6447048fecfd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738178"
---
# <a name="view-and-modify-push-subscription-properties"></a><span data-ttu-id="a9cfc-102">プッシュ サブスクリプションのプロパティの表示または変更</span><span class="sxs-lookup"><span data-stu-id="a9cfc-102">View and Modify Push Subscription Properties</span></span>
  <span data-ttu-id="a9cfc-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、プッシュ サブスクリプションのプロパティを表示および変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-103">This topic describes how to view and modify push subscription properties in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="a9cfc-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="a9cfc-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a9cfc-105">**プッシュ サブスクリプションのプロパティを表示および変更するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="a9cfc-105">**To view and modify push subscription properties, using:**</span></span>  
  
     [<span data-ttu-id="a9cfc-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a9cfc-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a9cfc-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a9cfc-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="a9cfc-108">レプリケーション管理オブジェクト (RMO)</span><span class="sxs-lookup"><span data-stu-id="a9cfc-108">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a9cfc-109">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="a9cfc-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="a9cfc-110">プッシュ サブスクリプション プロパティを表示および変更するには、以下の方法があります。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-110">View and modify push subscription properties from the Publisher in:</span></span>  
  
-   <span data-ttu-id="a9cfc-111">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] から使用できる **[サブスクリプションのプロパティ - \<Publisher>: \<PublicationDatabase>]** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-111">The **Subscription Properties - \<Publisher>: \<PublicationDatabase>** dialog box, which is available from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="a9cfc-112">レプリケーション モニターの **[すべてのサブスクリプション]** タブ。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-112">The **All Subscriptions** tab, which is available in Replication Monitor.</span></span> <span data-ttu-id="a9cfc-113">レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor](monitor/start-the-replication-monitor.md)」 (レプリケーション モニターの開始) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-113">For information about starting Replication Monitor, see [Start the Replication Monitor](monitor/start-the-replication-monitor.md).</span></span>  
  
#### <a name="to-view-and-modify-push-subscription-properties-in-management-studio"></a><span data-ttu-id="a9cfc-114">Management Studio でプッシュ サブスクリプション プロパティを表示および変更するには</span><span class="sxs-lookup"><span data-stu-id="a9cfc-114">To view and modify push subscription properties in Management Studio</span></span>  
  
1.  <span data-ttu-id="a9cfc-115">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-115">Connect to the Publisher in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="a9cfc-116">**[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-116">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="a9cfc-117">適切なパブリケーションを展開し、サブスクリプションを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-117">Expand the appropriate publication, right-click a subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="a9cfc-118">必要に応じてプロパティを変更し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-118">Modify any properties if necessary, and then click **OK**.</span></span>  
  
#### <a name="to-view-and-modify-push-subscription-properties-in-replication-monitor"></a><span data-ttu-id="a9cfc-119">レプリケーション モニターでプッシュ サブスクリプション プロパティを表示および変更するには</span><span class="sxs-lookup"><span data-stu-id="a9cfc-119">To view and modify push subscription properties in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="a9cfc-120">レプリケーション モニターの左ペインのパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-120">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="a9cfc-121">**[すべてのサブスクリプション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-121">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="a9cfc-122">サブスクリプションを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-122">Right-click a subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="a9cfc-123">必要に応じてプロパティを変更し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-123">Modify any properties if necessary, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a9cfc-124">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="a9cfc-124">Using Transact-SQL</span></span>  
 <span data-ttu-id="a9cfc-125">プッシュ サブスクリプションのプロパティは、レプリケーションのストアド プロシージャを使用して、プログラムから変更できます。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-125">Push subscriptions can be modified and their properties accessed programmatically using replication stored procedures.</span></span> <span data-ttu-id="a9cfc-126">使用するストアド プロシージャは、サブスクリプションが属するパブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-126">The stored procedures used depend on the type of publication to which the subscription belongs.</span></span>  
  
#### <a name="to-view-the-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="a9cfc-127">スナップショット パブリケーションまたはトランザクション パブリケーションのプッシュ サブスクリプションのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="a9cfc-127">To view the properties of a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="a9cfc-128">パブリッシャーのパブリケーション データベースで [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-128">At the Publisher on the publication database, execute [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).</span></span> <span data-ttu-id="a9cfc-129">には **@publication** 、、 **@subscriber** 、および**すべて**の値を指定し **@article** ます。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-129">Specify **@publication**, **@subscriber**, and a value of **all** for **@article**.</span></span>  
  
2.  <span data-ttu-id="a9cfc-130">パブリッシャーのパブリケーション データベースで [@subscriber](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)を指定して **@subscriber**ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-130">At the Publisher on the publication database, execute [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql), specifying **@subscriber**.</span></span>  
  
#### <a name="to-change-the-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="a9cfc-131">スナップショット パブリケーションまたはトランザクション パブリケーションのプッシュ サブスクリプションのプロパティを変更するには</span><span class="sxs-lookup"><span data-stu-id="a9cfc-131">To change the properties of a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="a9cfc-132">パブリッシャーのパブリケーション データベースで [sp_changesubscriber](/sql/relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql)を指定して **@subscriber** を指定し、さらに、変更対象とするサブスクライバー プロパティのパラメーターをすべて指定します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-132">At the Publisher on the publication database, execute [sp_changesubscriber](/sql/relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql), specifying **@subscriber** and any parameters for the Subscriber properties being changed.</span></span>  
  
2.  <span data-ttu-id="a9cfc-133">パブリッシャーのパブリケーション データベースで [sp_changesubscription](/sql/relational-databases/system-stored-procedures/sp-changesubscription-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-133">At the Publisher on the publication database, execute [sp_changesubscription](/sql/relational-databases/system-stored-procedures/sp-changesubscription-transact-sql).</span></span> <span data-ttu-id="a9cfc-134">、、を指定し、に all を、に変更するサブスクリプションプロパティを、に新しい値を指定し **@publication** **@subscriber** **@destination_db** **all** **@article** **@property** **@value** ます。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-134">Specify **@publication**, **@subscriber**, **@destination_db**, a value of **all** for **@article**, the subscription property being changed as **@property**, and the new value as **@value**.</span></span> <span data-ttu-id="a9cfc-135">これにより、プッシュ サブスクリプションのセキュリティ設定が変更されます。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-135">This changes security settings for the push subscription.</span></span>  
  
3.  <span data-ttu-id="a9cfc-136">(省略可) サブスクリプションのデータ変換サービス (DTS) パッケージのプロパティを変更するには、サブスクライバーのサブスクリプション データベースで [sp_changesubscriptiondtsinfo](/sql/relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-136">(Optional) To change the Data Transformation Services (DTS) package properties of a subscription, execute [sp_changesubscriptiondtsinfo](/sql/relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql) at the Subscriber on the subscription database.</span></span> <span data-ttu-id="a9cfc-137">にディストリビューションエージェントジョブの ID を指定 **@jobid** し、次の DTS パッケージのプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-137">Specify the ID of the Distribution Agent job for **@jobid** and the following DTS package properties:</span></span>  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     <span data-ttu-id="a9cfc-138">これにより、サブスクリプションの DTS パッケージ プロパティが変更されます。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-138">This changes the DTS package properties of a subscription.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a9cfc-139">ジョブ ID は、 [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)を実行することで取得できます。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-139">The job ID can be obtained by executing [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).</span></span>  
  
#### <a name="to-view-the-properties-of-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="a9cfc-140">マージ パブリケーションのプッシュ サブスクリプションのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="a9cfc-140">To view the properties of a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="a9cfc-141">パブリッシャーのパブリケーション データベースで [sp_helpmergesubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-141">At the Publisher on the publication database, execute [sp_helpmergesubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql).</span></span> <span data-ttu-id="a9cfc-142">およびを指定し **@publication** **@subscriber** ます。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-142">Specify **@publication** and **@subscriber**.</span></span>  
  
2.  <span data-ttu-id="a9cfc-143">パブリッシャーで[sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)を実行し、を指定 **@subscriber** します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-143">At the Publisher, execute [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql), specifying **@subscriber**.</span></span>  
  
#### <a name="to-change-the-properties-of-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="a9cfc-144">マージ パブリケーションのプッシュ サブスクリプションのプロパティを変更するには</span><span class="sxs-lookup"><span data-stu-id="a9cfc-144">To change the properties of a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="a9cfc-145">パブリッシャーのパブリケーション データベースで [sp_changemergesubscription](/sql/relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-145">At the Publisher on the publication database, execute [sp_changemergesubscription](/sql/relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql).</span></span> <span data-ttu-id="a9cfc-146">**@publication**、、 **@subscriber** **@subscriber_db** 、変更するサブスクリプションプロパティを、 **@property** および新しい値として指定し **@value** ます。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-146">Specify **@publication**, **@subscriber**, **@subscriber_db**, the subscription property being changed as **@property**, and the new value as **@value**.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="a9cfc-147">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a9cfc-147">Example (Transact-SQL)</span></span>  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="a9cfc-148">レプリケーション管理オブジェクト (RMO) の使用</span><span class="sxs-lookup"><span data-stu-id="a9cfc-148">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="a9cfc-149">プッシュ サブスクリプション プロパティの表示や変更に使用する RMO クラスは、プッシュ サブスクリプションをサブスクライブするパブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-149">The RMO classes you use to view or modify push subscription properties depend on the type of publication to which the push subscription is subscribed.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="a9cfc-150">スナップショット パブリケーションまたはトランザクション パブリケーションに対するプッシュ サブスクリプションのプロパティを表示または変更するには</span><span class="sxs-lookup"><span data-stu-id="a9cfc-150">To view or modify properties of a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="a9cfc-151"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-151">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="a9cfc-152"><xref:Microsoft.SqlServer.Replication.TransSubscription> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-152">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransSubscription> class.</span></span>  
  
3.  <span data-ttu-id="a9cfc-153"><xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> の各プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-153">Set the <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, and <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="a9cfc-154"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> プロパティ設定に、手順 1. の <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> を設定します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-154">Set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property setting.</span></span>  
  
5.  <span data-ttu-id="a9cfc-155"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-155">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="a9cfc-156">このメソッドから `false` が返された場合、手順 3. で指定したサブスクリプションのプロパティが正しく定義されていないか、サブスクリプションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-156">If this method returns `false`, either the subscription properties in step 3 were defined incorrectly or the subscription does not exist.</span></span>  
  
6.  <span data-ttu-id="a9cfc-157">(省略可) プロパティを変更するには、 <xref:Microsoft.SqlServer.Replication.TransSubscription> の設定可能なプロパティに新しい値を設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-157">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.TransSubscription> properties that can be set, and then call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="a9cfc-158">(省略可) 新しい設定を表示するには、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> メソッドを呼び出して、サブスクリプションのプロパティを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-158">(Optional) To view the new settings, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> method to reload the properties for the subscription.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="a9cfc-159">マージ パブリケーションに対するプッシュ サブスクリプションのプロパティを表示または変更するには</span><span class="sxs-lookup"><span data-stu-id="a9cfc-159">To view or modify properties of a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="a9cfc-160"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、サブスクライバーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-160">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="a9cfc-161"><xref:Microsoft.SqlServer.Replication.MergeSubscription> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-161">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> class.</span></span>  
  
3.  <span data-ttu-id="a9cfc-162"><xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> の各プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-162">Set the <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, and <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="a9cfc-163"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> プロパティ設定に、手順 1. の <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> を設定します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-163">Set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property setting.</span></span>  
  
5.  <span data-ttu-id="a9cfc-164"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-164">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="a9cfc-165">このメソッドから `false` が返された場合、手順 3. で指定したサブスクリプションのプロパティが正しく定義されていないか、サブスクリプションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-165">If this method returns `false`, either the subscription properties in step 3 were defined incorrectly or the subscription does not exist.</span></span>  
  
6.  <span data-ttu-id="a9cfc-166">(省略可) プロパティを変更するには、 <xref:Microsoft.SqlServer.Replication.MergeSubscription> の設定可能なプロパティに新しい値を設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-166">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> properties that can be set, and then call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="a9cfc-167">(省略可) 新しい設定を表示するには、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> メソッドを呼び出して、サブスクリプションのプロパティを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="a9cfc-167">(Optional) To view the new settings, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> method to reload the properties for the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9cfc-168">参照</span><span class="sxs-lookup"><span data-stu-id="a9cfc-168">See Also</span></span>  
 <span data-ttu-id="a9cfc-169">[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="a9cfc-169">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="a9cfc-170">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="a9cfc-170">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="a9cfc-171">パブリケーションのサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="a9cfc-171">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
