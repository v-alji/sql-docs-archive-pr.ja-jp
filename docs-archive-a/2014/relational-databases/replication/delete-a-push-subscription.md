---
title: プッシュ サブスクリプションの削除 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- removing subscriptions
- push subscriptions [SQL Server replication], deleting
- deleting subscriptions
- subscriptions [SQL Server replication], push
ms.assetid: 3c4847e2-aed9-4488-b45d-8164422bdb10
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 912958e00d117f51c5dc95c0dc1247d278acb0ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632388"
---
# <a name="delete-a-push-subscription"></a><span data-ttu-id="9353a-102">プッシュ サブスクリプションの削除</span><span class="sxs-lookup"><span data-stu-id="9353a-102">Delete a Push Subscription</span></span>
  <span data-ttu-id="9353a-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、プッシュ サブスクリプションを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9353a-103">This topic describes how to delete a push subscription in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="9353a-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="9353a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9353a-105">**プッシュ サブスクリプションを削除するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="9353a-105">**To delete a push subscription, using:**</span></span>  
  
     [<span data-ttu-id="9353a-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9353a-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9353a-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9353a-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="9353a-108">レプリケーション管理オブジェクト (RMO)</span><span class="sxs-lookup"><span data-stu-id="9353a-108">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9353a-109">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="9353a-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="9353a-110">パブリッシャーまたはサブスクライバーで、プッシュ サブスクリプションを削除します (パブリッシャーの場合は **の** [ローカル パブリケーション] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]フォルダーから、サブスクライバーの場合は **[ローカル サブスクリプション]** フォルダーから削除します)。</span><span class="sxs-lookup"><span data-stu-id="9353a-110">Delete a push subscription at the Publisher (from the **Local Publications** folder in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) or the Subscriber (from the **Local Subscriptions** folder).</span></span> <span data-ttu-id="9353a-111">サブスクリプションを削除しても、サブスクリプションのオブジェクトやデータは削除されません。これらは手動で削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9353a-111">Deleting a subscription does not remove objects or data from the subscription; they must be removed manually.</span></span>  
  
#### <a name="to-delete-a-push-subscription-at-the-publisher"></a><span data-ttu-id="9353a-112">パブリッシャーでプッシュ サブスクリプションを削除するには</span><span class="sxs-lookup"><span data-stu-id="9353a-112">To delete a push subscription at the Publisher</span></span>  
  
1.  <span data-ttu-id="9353a-113">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="9353a-113">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="9353a-114">**[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="9353a-114">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="9353a-115">削除するサブスクリプションに関連付けられているパブリケーションを展開します。</span><span class="sxs-lookup"><span data-stu-id="9353a-115">Expand the publication associated with the subscription you want to delete.</span></span>  
  
4.  <span data-ttu-id="9353a-116">サブスクリプションを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9353a-116">Right-click the subscription, and then click **Delete**.</span></span>  
  
5.  <span data-ttu-id="9353a-117">確認のダイアログ ボックスで、サブスクライバーに接続してサブスクリプション情報を削除するかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="9353a-117">In the confirmation dialog box, select whether to connect to the Subscriber to delete subscription information.</span></span> <span data-ttu-id="9353a-118">**[サブスクライバーへの接続]** チェック ボックスをオフにした場合は、後でサブスクライバーに接続してこの情報を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9353a-118">If you clear the **Connect to Subscriber** checkbox, you should connect to the Subscriber later to delete the information.</span></span>  
  
#### <a name="to-delete-a-push-subscription-at-the-subscriber"></a><span data-ttu-id="9353a-119">サブスクライバーでプッシュ サブスクリプションを削除するには</span><span class="sxs-lookup"><span data-stu-id="9353a-119">To delete a push subscription at the Subscriber</span></span>  
  
1.  <span data-ttu-id="9353a-120">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でサブスクライバーに接続して、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="9353a-120">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="9353a-121">**[レプリケーション]** フォルダーを展開し、 **[ローカル サブスクリプション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="9353a-121">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="9353a-122">削除するサブスクリプションを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9353a-122">Right-click the subscription you want to delete, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="9353a-123">確認のダイアログ ボックスで、パブリッシャーに接続してサブスクリプション情報を削除するかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="9353a-123">In the confirmation dialog box, select whether to connect to the Publisher to delete subscription information.</span></span> <span data-ttu-id="9353a-124">**[パブリッシャーへの接続]** チェック ボックスをオフにした場合は、後でパブリッシャーに接続してこの情報を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9353a-124">If you clear the **Connect to Publisher** check box, you should connect to the Publisher later to delete the information.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9353a-125">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="9353a-125">Using Transact-SQL</span></span>  
 <span data-ttu-id="9353a-126">プッシュ サブスクリプションは、レプリケーション ストアド プロシージャを使用してプログラムで削除できます。</span><span class="sxs-lookup"><span data-stu-id="9353a-126">Push subscriptions can be deleted programmatically using replication stored procedures.</span></span> <span data-ttu-id="9353a-127">使用するストアド プロシージャは、サブスクリプションが属するパブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="9353a-127">The stored procedures used depend on the type of publication to which the subscription belongs.</span></span>  
  
#### <a name="to-delete-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="9353a-128">スナップショット パブリケーションまたはトランザクション パブリケーションに対するプッシュ サブスクリプションを削除するには</span><span class="sxs-lookup"><span data-stu-id="9353a-128">To delete a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="9353a-129">パブリッシャー側のパブリケーション データベースに対して、[sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="9353a-129">At the Publisher on the publication database, execute [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql).</span></span> <span data-ttu-id="9353a-130">およびを指定し **@publication** **@subscriber** ます。</span><span class="sxs-lookup"><span data-stu-id="9353a-130">Specify **@publication** and **@subscriber**.</span></span> <span data-ttu-id="9353a-131">**@article** に **all** を指定します。</span><span class="sxs-lookup"><span data-stu-id="9353a-131">Specify a value of **all** for **@article**.</span></span> <span data-ttu-id="9353a-132">(省略可) ディストリビューターにアクセスできない場合、 **@ignore_distributor** に **@ignore_distributor** を指定して、ディストリビューターの関連オブジェクトを削除せずにサブスクリプションを削除します。</span><span class="sxs-lookup"><span data-stu-id="9353a-132">(Optional) If the Distributor cannot be accessed, specify a value of **1** for **@ignore_distributor** to delete the subscription without removing related objects at the Distributor.</span></span>  
  
2.  <span data-ttu-id="9353a-133">サブスクライバーのサブスクリプション データベースで [sp_subscription_cleanup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql) を実行して、サブスクリプション データベース内のレプリケーション メタデータを削除します。</span><span class="sxs-lookup"><span data-stu-id="9353a-133">At the Subscriber on the subscription database, execute [sp_subscription_cleanup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql) to remove replication metadata in the subscription database.</span></span>  
  
#### <a name="to-delete-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="9353a-134">マージ パブリケーションに対するプッシュ サブスクリプションを削除するには</span><span class="sxs-lookup"><span data-stu-id="9353a-134">To delete a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="9353a-135">パブリッシャーで、、、およびを指定して[sp_dropmergesubscription &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql)を実行し **@publication** **@subscriber** **@subscriber_db** ます。</span><span class="sxs-lookup"><span data-stu-id="9353a-135">At the Publisher, execute [sp_dropmergesubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql), specifying **@publication**, **@subscriber** and **@subscriber_db**.</span></span> <span data-ttu-id="9353a-136">(省略可) ディストリビューターにアクセスできない場合、 **@ignore_distributor** に **@ignore_distributor** を指定して、ディストリビューターの関連オブジェクトを削除せずにサブスクリプションを削除します。</span><span class="sxs-lookup"><span data-stu-id="9353a-136">(Optional) If the Distributor cannot be accessed, specify a value of **1** for **@ignore_distributor** to delete the subscription without removing related objects at the Distributor.</span></span>  
  
2.  <span data-ttu-id="9353a-137">サブスクライバー側のサブスクリプション データベースに対して、[sp_mergesubscription_cleanup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="9353a-137">At the Subscriber on the subscription database, execute [sp_mergesubscription_cleanup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql).</span></span> <span data-ttu-id="9353a-138">**@publisher**、、およびを指定し **@publisher_db** **@publication** ます。</span><span class="sxs-lookup"><span data-stu-id="9353a-138">Specify **@publisher**, **@publisher_db**, and **@publication**.</span></span> <span data-ttu-id="9353a-139">これにより、サブスクリプション データベースのマージ メタデータが削除されます。</span><span class="sxs-lookup"><span data-stu-id="9353a-139">This removes merge metadata from the subscription database.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="9353a-140">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9353a-140">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="9353a-141">この例では、トランザクション パブリケーションへのプッシュ サブスクリプションを削除します。</span><span class="sxs-lookup"><span data-stu-id="9353a-141">This example deletes a push subscription to a transactional publication.</span></span>  
  
 [!code-sql[HowTo#sp_droptransubscription](../../snippets/tsql/SQL15/replication/howto/tsql/droptranpullsub.sql#sp_droptransubscription)]  
  
 <span data-ttu-id="9353a-142">この例では、マージ パブリケーションへのプッシュ サブスクリプションを削除します。</span><span class="sxs-lookup"><span data-stu-id="9353a-142">This example deletes a push subscription to a merge publication.</span></span>  
  
 [!code-sql[HowTo#sp_dropmergesubscription](../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepullsub.sql#sp_dropmergesubscription)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="9353a-143">レプリケーション管理オブジェクト (RMO) の使用</span><span class="sxs-lookup"><span data-stu-id="9353a-143">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="9353a-144">プッシュ サブスクリプションの削除に使用する RMO クラスは、プッシュ サブスクリプションをサブスクライブするパブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="9353a-144">The RMO classes that you use to delete a push subscription depend on the type of publication to which the push subscription is subscribed.</span></span>  
  
#### <a name="to-delete-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="9353a-145">スナップショット パブリケーションまたはトランザクション パブリケーションに対するプッシュ サブスクリプションを削除するには</span><span class="sxs-lookup"><span data-stu-id="9353a-145">To delete a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="9353a-146"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、サブスクライバーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="9353a-146">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="9353a-147"><xref:Microsoft.SqlServer.Replication.TransSubscription> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9353a-147">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransSubscription> class.</span></span>  
  
3.  <span data-ttu-id="9353a-148"><xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> の各プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="9353a-148">Set the <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, and <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="9353a-149">手順 1. の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> を <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに設定します。</span><span class="sxs-lookup"><span data-stu-id="9353a-149">Set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="9353a-150"><xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> プロパティをチェックして、サブスクリプションが存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="9353a-150">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the subscription exists.</span></span> <span data-ttu-id="9353a-151">このプロパティの値が `false` の場合、手順 2. でサブスクリプション プロパティが不適切に定義されたか、サブスクリプションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="9353a-151">If the value of this property is `false`, either the subscription properties in step 2 were defined incorrectly or the subscription does not exist.</span></span>  
  
6.  <span data-ttu-id="9353a-152"><xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9353a-152">Call the <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> method.</span></span>  
  
#### <a name="to-delete-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="9353a-153">マージ パブリケーションに対するプッシュ サブスクリプションを削除するには</span><span class="sxs-lookup"><span data-stu-id="9353a-153">To delete a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="9353a-154"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、サブスクライバーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="9353a-154">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="9353a-155"><xref:Microsoft.SqlServer.Replication.MergeSubscription> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9353a-155">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> class.</span></span>  
  
3.  <span data-ttu-id="9353a-156"><xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> の各プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="9353a-156">Set the <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, and <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="9353a-157">手順 1. の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> を <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに設定します。</span><span class="sxs-lookup"><span data-stu-id="9353a-157">Set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="9353a-158"><xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> プロパティをチェックして、サブスクリプションが存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="9353a-158">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the subscription exists.</span></span> <span data-ttu-id="9353a-159">このプロパティの値が `false` の場合、手順 2. でサブスクリプション プロパティが不適切に定義されたか、サブスクリプションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="9353a-159">If the value of this property is `false`, either the subscription properties in step 2 were defined incorrectly or the subscription does not exist.</span></span>  
  
6.  <span data-ttu-id="9353a-160"><xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9353a-160">Call the <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> method.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="9353a-161">例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="9353a-161">Examples (RMO)</span></span>  
 <span data-ttu-id="9353a-162">レプリケーション管理オブジェクト (RMO) を使用することで、プログラムによってプッシュ サブスクリプションを削除できます。</span><span class="sxs-lookup"><span data-stu-id="9353a-162">You can delete push subscriptions programmatically by using Replication Management Objects (RMO).</span></span>  
  
 [!code-csharp[HowTo#rmo_DropTranPushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_droptranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_droptranpushsub)]  
  
## <a name="see-also"></a><span data-ttu-id="9353a-163">参照</span><span class="sxs-lookup"><span data-stu-id="9353a-163">See Also</span></span>  
 <span data-ttu-id="9353a-164">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="9353a-164">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 [<span data-ttu-id="9353a-165">レプリケーション セキュリティの推奨事項</span><span class="sxs-lookup"><span data-stu-id="9353a-165">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
