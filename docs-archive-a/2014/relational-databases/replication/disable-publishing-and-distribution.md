---
title: パブリッシングおよびディストリビューションの無効化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- disabling publishing
- publishing [SQL Server replication], disabling
- distribution disabling [SQL Server replication]
- removing replication
- replication [SQL Server], removing
- disabling replication
- disabling distribution
ms.assetid: 6d4a1474-4d13-4826-8be2-80050fafa8a5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8843dac310d1e023fe7ce63eded02c9e1bed3731
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632384"
---
# <a name="disable-publishing-and-distribution"></a><span data-ttu-id="a2a3d-102">パブリッシングおよびディストリビューションの無効化</span><span class="sxs-lookup"><span data-stu-id="a2a3d-102">Disable Publishing and Distribution</span></span>
  <span data-ttu-id="a2a3d-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、パブリッシングとディストリビューションを無効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-103">This topic describes how to disable publishing and distribution in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="a2a3d-104">次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-104">You can do the following:</span></span>  
  
-   <span data-ttu-id="a2a3d-105">ディストリビューターですべてのディストリビューション データベースを削除します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-105">Delete all distribution databases on the Distributor.</span></span>  
  
-   <span data-ttu-id="a2a3d-106">ディストリビューターを使用するすべてのパブリッシャーを無効にし、それらのパブリッシャーのすべてのパブリケーションを削除します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-106">Disable all Publishers that use the Distributor and delete all publications on those Publishers.</span></span>  
  
-   <span data-ttu-id="a2a3d-107">パブリケーションへのすべてのサブスクリプションを削除します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-107">Delete all subscriptions to the publications.</span></span> <span data-ttu-id="a2a3d-108">パブリケーション データベースおよびサブスクリプション データベースのデータは削除されませんが、パブリケーション データベースとの同期リレーションシップは失われます。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-108">Data in the publication and subscription databases will not be deleted; however, it loses its synchronization relationship to any publication databases.</span></span> <span data-ttu-id="a2a3d-109">サブスクライバーにあるデータを削除するには、手動で削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-109">If you want the data at the Subscriber to be deleted, you must delete it manually.</span></span>  
  
 <span data-ttu-id="a2a3d-110">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="a2a3d-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a2a3d-111">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="a2a3d-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a2a3d-112">前提条件</span><span class="sxs-lookup"><span data-stu-id="a2a3d-112">Prerequisites</span></span>](#Prerequisites)  
  
-   <span data-ttu-id="a2a3d-113">**パブリッシングおよびディストリビューションを無効にするために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="a2a3d-113">**To disable publishing and distribution, using:**</span></span>  
  
     [<span data-ttu-id="a2a3d-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a2a3d-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a2a3d-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a2a3d-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="a2a3d-116">レプリケーション管理オブジェクト (RMO)</span><span class="sxs-lookup"><span data-stu-id="a2a3d-116">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a2a3d-117">はじめに</span><span class="sxs-lookup"><span data-stu-id="a2a3d-117">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="a2a3d-118">前提条件</span><span class="sxs-lookup"><span data-stu-id="a2a3d-118">Prerequisites</span></span>  
  
-   <span data-ttu-id="a2a3d-119">パブリッシングおよびディストリビューションを無効にするには、すべてのディストリビューション データベースおよびパブリケーション データベースをオンラインにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-119">To disable publishing and distribution, all distribution and publication databases must be online.</span></span> <span data-ttu-id="a2a3d-120">ディストリビューション データベースまたはパブリケーション データベースに対して、 *データベース スナップショット* が存在する場合、これらを削除してからパブリッシングおよびディストリビューションを無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-120">If any *database snapshots* exist for distribution or publication databases, they must be dropped before disabling publishing and distribution.</span></span> <span data-ttu-id="a2a3d-121">データベース スナップショットは、データベースの読み取り専用のオフライン コピーで、レプリケーション スナップショットとは関連がありません。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-121">A database snapshot is a read-only offline copy of a database and is not related to a replication snapshot.</span></span> <span data-ttu-id="a2a3d-122">詳細については、「[データベース スナップショット &#40;SQL Server&#41;](../databases/database-snapshots-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-122">For more information, see [Database Snapshots &#40;SQL Server&#41;](../databases/database-snapshots-sql-server.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a2a3d-123">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="a2a3d-123">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="a2a3d-124">パブリッシングとディストリビューションの無効化ウィザードを使用して、パブリッシングおよびディストリビューションを無効化します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-124">Disable publishing and distribution by using the Disable Publishing and Distribution Wizard.</span></span>  
  
#### <a name="to-disable-publishing-and-distribution"></a><span data-ttu-id="a2a3d-125">パブリッシングおよびディストリビューションを無効化するには</span><span class="sxs-lookup"><span data-stu-id="a2a3d-125">To disable publishing and distribution</span></span>  
  
1.  <span data-ttu-id="a2a3d-126">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で無効化するパブリッシャーまたはディストリビューターに接続して、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-126">Connect to the Publisher or Distributor you want to disable in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="a2a3d-127">**[レプリケーション]** フォルダーを右クリックし、 **[パブリッシングとディストリビューションの無効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-127">Right-click the **Replication** folder, and then click **Disable Publishing and Distribution**.</span></span>  
  
3.  <span data-ttu-id="a2a3d-128">パブリッシングとディストリビューションの無効ウィザードの手順に従って操作します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-128">Complete the steps in the Disable Publishing and Distribution Wizard.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a2a3d-129">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="a2a3d-129">Using Transact-SQL</span></span>  
 <span data-ttu-id="a2a3d-130">パブリッシングおよびディストリビューションは、レプリケーションのストアド プロシージャを使用してプログラムから無効にできます。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-130">Publishing and distributing can be disabled programmatically using replication stored procedures.</span></span>  
  
#### <a name="to-disable-publishing-and-distribution"></a><span data-ttu-id="a2a3d-131">パブリッシングおよびディストリビューションを無効化するには</span><span class="sxs-lookup"><span data-stu-id="a2a3d-131">To disable publishing and distribution</span></span>  
  
1.  <span data-ttu-id="a2a3d-132">レプリケーション関連のすべてのジョブを停止します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-132">Stop all replication-related jobs.</span></span> <span data-ttu-id="a2a3d-133">ジョブ名の一覧については、「 [レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md)」の「SQL Server エージェントのエージェント セキュリティ」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-133">For a list of job names, see the "Agent Security Under SQL Server Agent" section of [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
2.  <span data-ttu-id="a2a3d-134">各サブスクライバーのサブスクリプション データベースに対して [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) を実行して、レプリケーション オブジェクトをデータベースから削除します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-134">At each Subscriber on the subscription database, execute [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) to remove replication objects from the database.</span></span> <span data-ttu-id="a2a3d-135">このストアド プロシージャでは、ディストリビューターのレプリケーション ジョブは削除されません。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-135">This stored procedure will not remove replication jobs at the Distributor.</span></span>  
  
3.  <span data-ttu-id="a2a3d-136">パブリッシャー側のパブリケーション データベースに対して、 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) を実行して、レプリケーション オブジェクトをデータベースから削除します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-136">At the Publisher on the publication database, execute [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) to remove replication objects from the database.</span></span>  
  
4.  <span data-ttu-id="a2a3d-137">パブリッシャーがリモート ディストリビューターを使用している場合は、 [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-137">If the Publisher uses a remote Distributor, execute [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql).</span></span>  
  
5.  <span data-ttu-id="a2a3d-138">ディストリビューターで [sp_dropdistpublisher](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-138">At the Distributor, execute [sp_dropdistpublisher](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql).</span></span> <span data-ttu-id="a2a3d-139">このストアド プロシージャは、ディストリビューターに登録されている各パブリッシャーについて一度ずつ実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-139">This stored procedure should be run once for each Publisher registered at the Distributor.</span></span>  
  
6.  <span data-ttu-id="a2a3d-140">ディストリビューターで [sp_dropdistributiondb](/sql/relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql) を実行して、ディストリビューション データベースを削除します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-140">At the Distributor, execute [sp_dropdistributiondb](/sql/relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql) to delete the distribution database.</span></span> <span data-ttu-id="a2a3d-141">このストアド プロシージャは、ディストリビューターの各ディストリビューション データベースについて実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-141">This stored procedure should be run once for each distribution database at the Distributor.</span></span> <span data-ttu-id="a2a3d-142">これにより、ディストリビューション データベースに関連付けられているキュー リーダー エージェント ジョブがすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-142">This also removes any Queue Reader Agent jobs associated with the distribution database.</span></span>  
  
7.  <span data-ttu-id="a2a3d-143">ディストリビューターで [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql) を実行して、サーバーからディストリビューターの指定を削除します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-143">At the Distributor, execute [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql) to remove the Distributor designation from the server.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a2a3d-144">[sp_dropdistpublisher](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql) および [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql)の実行前にレプリケーションのパブリッシング オブジェクトおよびディストリビューション オブジェクトがすべて削除されていなかった場合は、これらのプロシージャからエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-144">If all replication publishing and distribution objects are not dropped before you execute [sp_dropdistpublisher](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql) and [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql), these procedures will return an error.</span></span> <span data-ttu-id="a2a3d-145">パブリッシャーまたはディストリビューターの削除時に、レプリケーション関連のオブジェクトをすべて削除するには、 \*\* \@ no_checks**パラメーターを**1\*\*に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-145">To drop all replication-related objects when a Publisher or Distributor is dropped, the **\@no_checks** parameter must be set to **1**.</span></span> <span data-ttu-id="a2a3d-146">パブリッシャーまたはディストリビューターがオフラインであるか、またはディストリビューターにアクセスできない場合は、 \*\* \@ ignore_distributor**パラメーターを**1\*\*に設定して削除することができます。ただし、パブリッシュおよび配布オブジェクトを残さないようにするには、手動で削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-146">If a Publisher or Distributor is offline or unreachable, the **\@ignore_distributor** parameter can be set to **1** so that they can be dropped; however, any publishing and distributing objects left behind must be removed manually.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="a2a3d-147">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a2a3d-147">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="a2a3d-148">次の例は、サブスクリプション データベースからレプリケーション オブジェクトを削除するスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-148">This example script removes replication objects from the subscription database.</span></span>  
  
 [!code-sql[HowTo#sp_removedbreplication](../../snippets/tsql/SQL15/replication/howto/tsql/dropdistpub.sql#sp_removedbreplication)]  
  
 <span data-ttu-id="a2a3d-149">次の例は、パブリッシャーおよびディストリビューターとして機能しているサーバー上のパブリッシングおよびディストリビューションを無効にし、ディストリビューション データベースを削除するスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-149">This example script disables publishing and distribution on a server that is a Publisher and Distributor and drops the distribution database.</span></span>  
  
 [!code-sql[HowTo#sp_DropDistPub](../../snippets/tsql/SQL15/replication/howto/tsql/dropdistpub.sql#sp_dropdistpub)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="a2a3d-150">レプリケーション管理オブジェクト (RMO) の使用</span><span class="sxs-lookup"><span data-stu-id="a2a3d-150">Using Replication Management Objects (RMO)</span></span>  
  
#### <a name="to-disable-publishing-and-distribution"></a><span data-ttu-id="a2a3d-151">パブリッシングおよびディストリビューションを無効化するには</span><span class="sxs-lookup"><span data-stu-id="a2a3d-151">To disable publishing and distribution</span></span>  
  
1.  <span data-ttu-id="a2a3d-152">ディストリビューターを利用するパブリケーションへのサブスクリプションをすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-152">Remove all subscriptions to publications that use the Distributor.</span></span> <span data-ttu-id="a2a3d-153">詳細については、「 [Delete a Pull Subscription](delete-a-pull-subscription.md) 」および「 [Delete a Push Subscription](delete-a-push-subscription.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-153">For more information, see [Delete a Pull Subscription](delete-a-pull-subscription.md) and [Delete a Push Subscription](delete-a-push-subscription.md).</span></span>  
  
2.  <span data-ttu-id="a2a3d-154">パブリッシャーとディストリビューターが同じサーバーにある場合、ディストリビューターを利用するパブリケーションをすべて削除し、すべてのデータベースに対するパブリッシングを無効にします。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-154">Remove all publications that use the Distributor, and disable publishing for all databases if the Publisher and Distributor are on the same server.</span></span> <span data-ttu-id="a2a3d-155">詳しくは、「 [Delete a Publication](publish/delete-a-publication.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-155">For more information, see [Delete a Publication](publish/delete-a-publication.md).</span></span>  
  
3.  <span data-ttu-id="a2a3d-156"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、ディストリビューターへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-156">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
4.  <span data-ttu-id="a2a3d-157"><xref:Microsoft.SqlServer.Replication.DistributionPublisher> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-157">Create an instance of the <xref:Microsoft.SqlServer.Replication.DistributionPublisher> class.</span></span> <span data-ttu-id="a2a3d-158"><xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> プロパティを指定し、手順 3. の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-158">Specify the <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> property, and pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object from step 3.</span></span>  
  
5.  <span data-ttu-id="a2a3d-159">(省略可) <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得し、パブリッシャーが存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-159">(Optional) Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object and verify that the Publisher exists.</span></span> <span data-ttu-id="a2a3d-160">このメソッドが `false` を返した場合、手順 4. で設定したパブリッシャーの名前が誤っていたか、このディストリビューターではこのパブリッシャーが使用されていません。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-160">If this method returns `false`, the Publisher name set in step 4 was incorrect or the Publisher is not used by this Distributor.</span></span>  
  
6.  <span data-ttu-id="a2a3d-161"><xref:Microsoft.SqlServer.Replication.DistributionPublisher.Remove%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-161">Call the <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Remove%2A> method.</span></span> <span data-ttu-id="a2a3d-162">`true`パブリッシャーとディストリビューターが別々のサーバーにあり、パブリッシャーにパブリケーションが存在しないことを最初に確認せずにディストリビューターでパブリッシャーをアンインストールする必要がある場合は、 *force*に値を渡します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-162">Pass a value of `true` for *force* if the Publisher and Distributor are on different servers, and when the Publisher should be uninstalled at the Distributor without first verifying that publications no longer exist at the Publisher.</span></span>  
  
7.  <span data-ttu-id="a2a3d-163"><xref:Microsoft.SqlServer.Replication.ReplicationServer> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-163">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span> <span data-ttu-id="a2a3d-164">手順 3 の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-164">Pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object from step 3.</span></span>  
  
8.  <span data-ttu-id="a2a3d-165"><xref:Microsoft.SqlServer.Replication.ReplicationServer.UninstallDistributor%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-165">Call the <xref:Microsoft.SqlServer.Replication.ReplicationServer.UninstallDistributor%2A> method.</span></span> <span data-ttu-id="a2a3d-166">Force の値を渡して、 `true` すべてのローカルパブリケーションデータベースが無効になっていること、およびディストリビューションデータベースがアンインストールされていることを最初に確認せずに、ディストリビューターのすべてのレプリケーションオブジェクトを削除します。 *force*</span><span class="sxs-lookup"><span data-stu-id="a2a3d-166">Pass a value of `true` for *force* to remove all replication objects at the Distributor without first verifying that all local publication databases have been disabled, and distribution databases have been uninstalled.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="a2a3d-167">例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="a2a3d-167">Examples (RMO)</span></span>  
 <span data-ttu-id="a2a3d-168">次の例では、ディストリビューターのパブリッシャーの登録を削除し、ディストリビューション データベースを削除して、ディストリビューターをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-168">This example removes the Publisher registration at the Distributor, drops the distribution database, and uninstalls the Distributor.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropDistPub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropdistpub)]  
  
 [!code-vb[HowTo#rmo_vb_DropDistPub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropdistpub)]  
  
 <span data-ttu-id="a2a3d-169">次の例では、最初にローカル パブリケーション データベースを無効にしたりディストリビューション データベースを削除せずに、ディストリビューターをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="a2a3d-169">This example uninstalls the Distributor without first disabling local publication databases or dropping the distribution database.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropDistPubForce](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropdistpubforce)]  
  
 [!code-vb[HowTo#rmo_vb_DropDistPubForce](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropdistpubforce)]  
  
## <a name="see-also"></a><span data-ttu-id="a2a3d-170">参照</span><span class="sxs-lookup"><span data-stu-id="a2a3d-170">See Also</span></span>  
 <span data-ttu-id="a2a3d-171">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="a2a3d-171">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span></span>  
 [<span data-ttu-id="a2a3d-172">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="a2a3d-172">Replication System Stored Procedures Concepts</span></span>](concepts/replication-system-stored-procedures-concepts.md)  
  
  
