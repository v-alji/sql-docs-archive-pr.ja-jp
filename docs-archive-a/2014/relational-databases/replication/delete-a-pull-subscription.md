---
title: プル サブスクリプションの削除 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- removing subscriptions
- deleting subscriptions
- pull subscriptions [SQL Server replication], deleting
- subscriptions [SQL Server replication], pull
ms.assetid: 997c0b8e-d8d9-4eed-85b1-6baa1f8594ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f869e26075bb837b2110e9db3ac5ac7220659525
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632392"
---
# <a name="delete-a-pull-subscription"></a><span data-ttu-id="cbb05-102">プル サブスクリプションの削除</span><span class="sxs-lookup"><span data-stu-id="cbb05-102">Delete a Pull Subscription</span></span>
  <span data-ttu-id="cbb05-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、プル サブスクリプションを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-103">This topic describes how to delete a pull subscription in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="cbb05-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="cbb05-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cbb05-105">**プル サブスクリプションを削除するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="cbb05-105">**To delete a pull subscription, using:**</span></span>  
  
     [<span data-ttu-id="cbb05-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cbb05-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cbb05-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cbb05-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="cbb05-108">レプリケーション管理オブジェクト (RMO)</span><span class="sxs-lookup"><span data-stu-id="cbb05-108">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cbb05-109">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="cbb05-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="cbb05-110">パブリッシャーまたはサブスクライバーで、プル サブスクリプションを削除します (パブリッシャーの場合は **の** [ローカル パブリケーション] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]フォルダーから、サブスクライバーの場合は **[ローカル サブスクリプション]** フォルダーから削除します)。</span><span class="sxs-lookup"><span data-stu-id="cbb05-110">Delete a pull subscription at the Publisher (from the **Local Publications** folder in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) or the Subscriber (from the **Local Subscriptions** folder).</span></span> <span data-ttu-id="cbb05-111">サブスクリプションを削除しても、サブスクリプションのオブジェクトやデータは削除されません。これらは手動で削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cbb05-111">Deleting a subscription does not remove objects or data from the subscription; they must be removed manually.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-at-the-publisher"></a><span data-ttu-id="cbb05-112">パブリッシャーでプル サブスクリプションを削除するには</span><span class="sxs-lookup"><span data-stu-id="cbb05-112">To delete a pull subscription at the Publisher</span></span>  
  
1.  <span data-ttu-id="cbb05-113">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-113">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="cbb05-114">**[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-114">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="cbb05-115">削除するサブスクリプションに関連付けられているパブリケーションを展開します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-115">Expand the publication associated with the subscription you want to delete.</span></span>  
  
4.  <span data-ttu-id="cbb05-116">サブスクリプションを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cbb05-116">Right-click the subscription, and then click **Delete**.</span></span>  
  
5.  <span data-ttu-id="cbb05-117">確認のダイアログ ボックスで、サブスクライバーに接続してサブスクリプション情報を削除するかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-117">In the confirmation dialog box, select whether to connect to the Subscriber to delete subscription information.</span></span> <span data-ttu-id="cbb05-118">**[サブスクライバーへの接続]** チェック ボックスをオフにする場合は、後でサブスクライバーに接続してこの情報を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cbb05-118">If you clear the **Connect to Subscriber** check box, you should connect to the Subscriber later to delete the information.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-at-the-subscriber"></a><span data-ttu-id="cbb05-119">サブスクライバーでプル サブスクリプションを削除するには</span><span class="sxs-lookup"><span data-stu-id="cbb05-119">To delete a pull subscription at the Subscriber</span></span>  
  
1.  <span data-ttu-id="cbb05-120">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でサブスクライバーに接続して、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-120">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="cbb05-121">**[レプリケーション]** フォルダーを展開し、 **[ローカル サブスクリプション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-121">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="cbb05-122">削除するサブスクリプションを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cbb05-122">Right-click the subscription you want to delete, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="cbb05-123">確認のダイアログ ボックスで、パブリッシャーに接続してサブスクリプション情報を削除するかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-123">In the confirmation dialog box, select whether to connect to the Publisher to delete subscription information.</span></span> <span data-ttu-id="cbb05-124">**[パブリッシャーへの接続]** チェック ボックスをオフにした場合は、後でパブリッシャーに接続してこの情報を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cbb05-124">If you clear the **Connect to Publisher** check box, you should connect to the Publisher later to delete the information.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cbb05-125">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="cbb05-125">Using Transact-SQL</span></span>  
 <span data-ttu-id="cbb05-126">プル サブスクリプションは、レプリケーション ストアド プロシージャを使用してプログラムで削除できます。</span><span class="sxs-lookup"><span data-stu-id="cbb05-126">Pull subscriptions can be deleted programmatically using replication stored procedures.</span></span> <span data-ttu-id="cbb05-127">使用するストアド プロシージャは、サブスクリプションが属するパブリケーションの種類によって変わります。</span><span class="sxs-lookup"><span data-stu-id="cbb05-127">The stored procedures used will depend on the type of publication to which the subscription belongs.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="cbb05-128">スナップショット パブリケーションまたはトランザクション パブリケーションに対するプル サブスクリプションを削除するには</span><span class="sxs-lookup"><span data-stu-id="cbb05-128">To delete a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="cbb05-129">サブスクライバー側のサブスクリプション データベースに対して、[sp_droppullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-129">At the Subscriber on the subscription database, execute [sp_droppullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql).</span></span> <span data-ttu-id="cbb05-130">**@publication**、、およびを指定し **@publisher** **@publisher_db** ます。</span><span class="sxs-lookup"><span data-stu-id="cbb05-130">Specify **@publication**, **@publisher**, and **@publisher_db**.</span></span>  
  
2.  <span data-ttu-id="cbb05-131">パブリッシャー側のパブリケーション データベースに対して、[sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-131">At the Publisher on the publication database, execute [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql).</span></span> <span data-ttu-id="cbb05-132">およびを指定し **@publication** **@subscriber** ます。</span><span class="sxs-lookup"><span data-stu-id="cbb05-132">Specify **@publication** and **@subscriber**.</span></span> <span data-ttu-id="cbb05-133">**@article** に **all** を指定します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-133">Specify a value of **all** for **@article**.</span></span> <span data-ttu-id="cbb05-134">(省略可) ディストリビューターにアクセスできない場合、 **@ignore_distributor** に **@ignore_distributor** を指定して、ディストリビューターの関連オブジェクトを削除せずにサブスクリプションを削除します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-134">(Optional) If the Distributor cannot be accessed, specify a value of **1** for **@ignore_distributor** to delete the subscription without removing related objects at the Distributor.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="cbb05-135">マージ パブリケーションに対するプル サブスクリプションを削除するには</span><span class="sxs-lookup"><span data-stu-id="cbb05-135">To delete a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="cbb05-136">サブスクライバー側のサブスクリプション データベースに対して、[sp_dropmergepullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-136">At the Subscriber on the subscription database, execute [sp_dropmergepullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql).</span></span> <span data-ttu-id="cbb05-137">**@publication**、、およびを指定し **@publisher** **@publisher_db** ます。</span><span class="sxs-lookup"><span data-stu-id="cbb05-137">Specify **@publication**, **@publisher**, and **@publisher_db**.</span></span>  
  
2.  <span data-ttu-id="cbb05-138">パブリッシャー側のパブリケーション データベースに対して、[sp_dropmergepullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-138">At the Publisher on the publication database, execute [sp_dropmergesubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql).</span></span> <span data-ttu-id="cbb05-139">**@publication**、、およびを指定し **@subscriber** **@subscriber_db** ます。</span><span class="sxs-lookup"><span data-stu-id="cbb05-139">Specify **@publication**, **@subscriber**, and **@subscriber_db**.</span></span> <span data-ttu-id="cbb05-140">**@subscription_type** に **pull** を指定します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-140">Specify a value of **pull** for **@subscription_type**.</span></span> <span data-ttu-id="cbb05-141">(省略可) ディストリビューターにアクセスできない場合、 **@ignore_distributor** に **@ignore_distributor** を指定して、ディストリビューターの関連オブジェクトを削除せずにサブスクリプションを削除します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-141">(Optional) If the Distributor cannot be accessed, specify a value of **1** for **@ignore_distributor** to delete the subscription without removing related objects at the Distributor.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="cbb05-142">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="cbb05-142">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="cbb05-143">次の例では、トランザクション パブリケーションへのプル サブスクリプションを削除します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-143">The following example deletes a pull subscription to a transactional publication.</span></span> <span data-ttu-id="cbb05-144">最初のバッチはサブスクライバーで実行され、次のバッチはパブリッシャーで実行されます。</span><span class="sxs-lookup"><span data-stu-id="cbb05-144">The first batch is executed at the Subscriber and the second is executed at the Publisher.</span></span>  
  
 [!code-sql[HowTo#sp_droptranpullsubscription](../../snippets/tsql/SQL15/replication/howto/tsql/droptranpullsub.sql#sp_droptranpullsubscription)]  
  
 [!code-sql[HowTo#sp_droptransubscription](../../snippets/tsql/SQL15/replication/howto/tsql/droptranpullsub.sql#sp_droptransubscription)]  
  
 <span data-ttu-id="cbb05-145">次の例では、マージ パブリケーションに対するプル サブスクリプションを削除します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-145">The following example deletes a pull subscription to a merge publication.</span></span> <span data-ttu-id="cbb05-146">最初のバッチはサブスクライバーで実行され、次のバッチはパブリッシャーで実行されます。</span><span class="sxs-lookup"><span data-stu-id="cbb05-146">The first batch is executed at the Subscriber and the second is executed at the Publisher.</span></span>  
  
 [!code-sql[HowTo#sp_dropmergepullsubscription](../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepullsub.sql#sp_dropmergepullsubscription)]  
  
 [!code-sql[HowTo#sp_dropmergesubscription](../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepullsub.sql#sp_dropmergesubscription)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="cbb05-147">レプリケーション管理オブジェクト (RMO) の使用</span><span class="sxs-lookup"><span data-stu-id="cbb05-147">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="cbb05-148">レプリケーション管理オブジェクト (RMO) を使用することで、プログラムによってプル サブスクリプションを削除できます。</span><span class="sxs-lookup"><span data-stu-id="cbb05-148">You can delete pull subscriptions programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="cbb05-149">プル サブスクリプションの削除に使用する RMO クラスは、プル サブスクリプションをサブスクライブするパブリケーションの種類によって決まります。</span><span class="sxs-lookup"><span data-stu-id="cbb05-149">The RMO classes that you use to delete a pull subscription depend on the type of publication to which the pull subscription is subscribed.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="cbb05-150">スナップショット パブリケーションまたはトランザクション パブリケーションに対するプル サブスクリプションを削除するには</span><span class="sxs-lookup"><span data-stu-id="cbb05-150">To delete a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="cbb05-151"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、サブスクライバーおよびパブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-151">Create connections to both the Subscriber and Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Class.</span></span>  
  
2.  <span data-ttu-id="cbb05-152"><xref:Microsoft.SqlServer.Replication.TransPullSubscription> クラスのインスタンスを作成し、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>、および <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> の各プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-152">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> class, and set the <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> properties.</span></span> <span data-ttu-id="cbb05-153">手順 1. のサブスクライバー接続を使用して、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-153">Use the Subscriber connection from step 1 to set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
3.  <span data-ttu-id="cbb05-154"><xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> プロパティをチェックして、サブスクリプションが存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-154">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the subscription exists.</span></span> <span data-ttu-id="cbb05-155">このプロパティの値が `false` の場合、手順 2. でサブスクリプション プロパティが不適切に定義されたか、サブスクリプションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="cbb05-155">If the value of this property is `false`, either the subscription properties in step 2 were defined incorrectly or the subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="cbb05-156"><xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-156">Call the <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> method.</span></span>  
  
5.  <span data-ttu-id="cbb05-157">手順 1. のパブリッシャー接続を使用して、 <xref:Microsoft.SqlServer.Replication.TransPublication> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-157">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPublication> class by using the Publisher connection from step 1.</span></span> <span data-ttu-id="cbb05-158"><xref:Microsoft.SqlServer.Replication.Publication.Name%2A>、 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 、および <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>を指定します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-158">Specify <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> and <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
6.  <span data-ttu-id="cbb05-159"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-159">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="cbb05-160">このメソッドが `false` を返す場合、手順 5. で指定したプロパティが誤っているか、サーバーにパブリケーションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="cbb05-160">If this method returns `false`, either the properties specified in step 5 are incorrect or the publication does not exist on the server.</span></span>  
  
7.  <span data-ttu-id="cbb05-161"><xref:Microsoft.SqlServer.Replication.TransPublication.RemovePullSubscription%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-161">Call the <xref:Microsoft.SqlServer.Replication.TransPublication.RemovePullSubscription%2A> method.</span></span> <span data-ttu-id="cbb05-162">*subscriber* パラメーターと *subscriberDB* パラメーターに、サブスクライバーの名前とサブスクリプション データベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-162">Specify the name of the Subscriber and the subscription database for the *subscriber* and *subscriberDB* parameters.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="cbb05-163">マージ パブリケーションに対するプル サブスクリプションを削除するには</span><span class="sxs-lookup"><span data-stu-id="cbb05-163">To delete a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="cbb05-164"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、サブスクライバーおよびパブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-164">Create connections to both the Subscriber and Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Class.</span></span>  
  
2.  <span data-ttu-id="cbb05-165"><xref:Microsoft.SqlServer.Replication.MergePullSubscription> クラスのインスタンスを作成し、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>、および <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> の各プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-165">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> class, and set the <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> properties.</span></span> <span data-ttu-id="cbb05-166">手順 1. の接続を使用して、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-166">Use the connection from step 1 to set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
3.  <span data-ttu-id="cbb05-167"><xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> プロパティをチェックして、サブスクリプションが存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-167">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the subscription exists.</span></span> <span data-ttu-id="cbb05-168">このプロパティの値が `false` の場合、手順 2. でサブスクリプション プロパティが不適切に定義されたか、サブスクリプションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="cbb05-168">If the value of this property is `false`, either the subscription properties in step 2 were defined incorrectly or the subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="cbb05-169"><xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-169">Call the <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> method.</span></span>  
  
5.  <span data-ttu-id="cbb05-170">手順 1. のパブリッシャー接続を使用して、 <xref:Microsoft.SqlServer.Replication.MergePublication> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-170">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class by using the Publisher connection from step 1.</span></span> <span data-ttu-id="cbb05-171"><xref:Microsoft.SqlServer.Replication.Publication.Name%2A>、 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 、および <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>を指定します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-171">Specify <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> and <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
6.  <span data-ttu-id="cbb05-172"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-172">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="cbb05-173">このメソッドが `false` を返す場合、手順 5. で指定したプロパティが誤っているか、サーバーにパブリケーションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="cbb05-173">If this method returns `false`, either the properties specified in step 5 are incorrect or the publication does not exist on the server.</span></span>  
  
7.  <span data-ttu-id="cbb05-174"><xref:Microsoft.SqlServer.Replication.MergePublication.RemovePullSubscription%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-174">Call the <xref:Microsoft.SqlServer.Replication.MergePublication.RemovePullSubscription%2A> method.</span></span> <span data-ttu-id="cbb05-175">*subscriber* パラメーターと *subscriberDB* パラメーターに、サブスクライバーの名前とサブスクリプション データベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-175">Specify the name of the Subscriber and the subscription database for the *subscriber* and *subscriberDB* parameters.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="cbb05-176">例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="cbb05-176">Examples (RMO)</span></span>  
 <span data-ttu-id="cbb05-177">次の例では、トランザクション パブリケーションに対するプル サブスクリプションを削除し、パブリッシャー側のサブスクリプション登録を削除します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-177">This example deletes a pull subscription to a transactional publication and removes the subscription registration at the Publisher.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropTranPullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_droptranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_droptranpullsub)]  
  
 <span data-ttu-id="cbb05-178">次の例では、マージ パブリケーションに対するプル サブスクリプションを削除し、パブリッシャー側のサブスクリプション登録を削除します。</span><span class="sxs-lookup"><span data-stu-id="cbb05-178">This example deletes a pull subscription to a merge publication and removes the subscription registration at the Publisher.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropMergePullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropmergepullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropmergepullsub)]  
  
## <a name="see-also"></a><span data-ttu-id="cbb05-179">参照</span><span class="sxs-lookup"><span data-stu-id="cbb05-179">See Also</span></span>  
 <span data-ttu-id="cbb05-180">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="cbb05-180">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 [<span data-ttu-id="cbb05-181">レプリケーション セキュリティの推奨事項</span><span class="sxs-lookup"><span data-stu-id="cbb05-181">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
