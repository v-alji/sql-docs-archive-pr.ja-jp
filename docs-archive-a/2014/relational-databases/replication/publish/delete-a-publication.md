---
title: パブリケーションの削除 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- removing publications
- publications [SQL Server replication], deleting
- articles [SQL Server replication], deleting
- deleting publications
ms.assetid: 408a1360-12ee-4896-ac94-482ae839593b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5d2b39a326d59333868b4f8015eb9a2e59d59e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741781"
---
# <a name="delete-a-publication"></a><span data-ttu-id="7a91e-102">パブリケーションの削除</span><span class="sxs-lookup"><span data-stu-id="7a91e-102">Delete a Publication</span></span>
  <span data-ttu-id="7a91e-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、パブリケーションを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-103">This topic describes how to delete a publication in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="7a91e-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="7a91e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7a91e-105">**パブリケーションを削除するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="7a91e-105">**To delete a publication, using:**</span></span>  
  
     [<span data-ttu-id="7a91e-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7a91e-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="7a91e-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7a91e-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="7a91e-108">レプリケーション管理オブジェクト (RMO)</span><span class="sxs-lookup"><span data-stu-id="7a91e-108">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7a91e-109">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="7a91e-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="7a91e-110">**内の** [ローカル パブリケーション] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]フォルダーからパブリケーションを削除します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-110">Delete publications from the **Local Publications** folder in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-delete-a-publication"></a><span data-ttu-id="7a91e-111">パブリケーションを削除するには</span><span class="sxs-lookup"><span data-stu-id="7a91e-111">To delete a publication</span></span>  
  
1.  <span data-ttu-id="7a91e-112">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-112">Connect to the Publisher in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="7a91e-113">**[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-113">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="7a91e-114">削除するパブリケーションを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a91e-114">Right-click the publication you want to delete, and then click **Delete**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7a91e-115">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="7a91e-115">Using Transact-SQL</span></span>  
 <span data-ttu-id="7a91e-116">パブリケーションは、レプリケーションのストアド プロシージャを使用してプログラムから削除できます。</span><span class="sxs-lookup"><span data-stu-id="7a91e-116">Publications can be deleted programmatically using replication stored procedures.</span></span> <span data-ttu-id="7a91e-117">どのストアド プロシージャを使用するかは、削除するパブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="7a91e-117">The stored procedures that you use depend on the type of publication being deleted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a91e-118">パブリケーションを削除しても、パブリッシュされたオブジェクトはパブリケーション データベースから削除されず、対応するオブジェクトはサブスクリプション データベースから削除されません。</span><span class="sxs-lookup"><span data-stu-id="7a91e-118">Deleting a publication does not remove published objects from the publication database or the corresponding objects from the subscription database.</span></span> <span data-ttu-id="7a91e-119">これらのオブジェクトは、必要に応じて `DROP <object>` コマンドを使用し、手動で削除します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-119">Use the `DROP <object>` command to manually remove these objects if necessary.</span></span>  
  
#### <a name="to-delete-a-snapshot-or-transactional-publication"></a><span data-ttu-id="7a91e-120">スナップショット パブリケーションまたはトランザクション パブリケーションを削除するには</span><span class="sxs-lookup"><span data-stu-id="7a91e-120">To delete a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="7a91e-121">次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="7a91e-121">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="7a91e-122">単一のパブリケーションを削除するには、パブリッシャーのパブリケーション データベースで [sp_droppublication](/sql/relational-databases/system-stored-procedures/sp-droppublication-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-122">To delete a single publication, execute [sp_droppublication](/sql/relational-databases/system-stored-procedures/sp-droppublication-transact-sql) at the Publisher on the publication database.</span></span>  
  
    -   <span data-ttu-id="7a91e-123">すべてのパブリケーションを削除し、パブリッシュされたデータベースからすべてのレプリケーション オブジェクトを削除するには、パブリッシャーで [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-123">To delete all publications in and remove all replication objects from a published database, execute [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) at the Publisher.</span></span> <span data-ttu-id="7a91e-124">型の値を指定し `tran` ます。 \*\* \@ \*\*</span><span class="sxs-lookup"><span data-stu-id="7a91e-124">Specify a value of `tran` for **\@type**.</span></span> <span data-ttu-id="7a91e-125">(省略可能) ディストリビューターにアクセスできない場合や、ディストリビューターのデータベース ステータスがオフラインになっている可能性がある場合は、 **\@force** に **1** を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-125">(Optional) If the Distributor cannot be accessed or if the status of the database is suspect or offline, specify a value of **1** for **\@force**.</span></span> <span data-ttu-id="7a91e-126">(省略可能) パブリケーション データベースに対して [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) を実行しない場合は、 **\@dbname** にデータベースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-126">(Optional) Specify the name of the database for **\@dbname** if [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) is not executed on the publication database.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="7a91e-127">**\@force** に **1** を指定すると、レプリケーション関連のパブリッシング オブジェクトがデータベース上に残されます。</span><span class="sxs-lookup"><span data-stu-id="7a91e-127">Specifying a value of **1** for **\@force** may leave replication-related publishing objects in the database.</span></span>  
  
2.  <span data-ttu-id="7a91e-128">(省略可) このデータベースに他のパブリケーションが存在しない場合は、[sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) を実行し、スナップショット レプリケーションまたはトランザクション レプリケーションを使用した、現在のデータベースのパブリケーションを無効にします。</span><span class="sxs-lookup"><span data-stu-id="7a91e-128">(Optional) If this database has no other publications, execute [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) to disable publication of the current database using snapshot or transactional replication.</span></span>  
  
3.  <span data-ttu-id="7a91e-129">(省略可) サブスクライバーのサブスクリプション データベースで [sp_subscription_cleanup](/sql/relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql) を実行して、サブスクリプション データベースに残っているレプリケーション メタデータをすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-129">(Optional) At the Subscriber on the subscription database, execute [sp_subscription_cleanup](/sql/relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql) to remove any remaining replication metadata in the subscription database.</span></span>  
  
#### <a name="to-delete-a-merge-publication"></a><span data-ttu-id="7a91e-130">マージ パブリケーションを削除するには</span><span class="sxs-lookup"><span data-stu-id="7a91e-130">To delete a merge publication</span></span>  
  
1.  <span data-ttu-id="7a91e-131">次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="7a91e-131">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="7a91e-132">単一のパブリケーションを削除するには、パブリッシャーのパブリケーション データベースで [sp_dropmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-132">To delete a single publication, execute [sp_dropmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql) at the Publisher on the publication database.</span></span>  
  
    -   <span data-ttu-id="7a91e-133">すべてのパブリケーションを削除し、パブリッシュされたデータベースからすべてのレプリケーション オブジェクトを削除するには、パブリッシャーで [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-133">To delete all publications in and remove all replication objects from a published database, execute [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) at the Publisher.</span></span> <span data-ttu-id="7a91e-134">型の値を指定し `merge` ます。 \*\* \@ \*\*</span><span class="sxs-lookup"><span data-stu-id="7a91e-134">Specify a value of `merge` for **\@type**.</span></span> <span data-ttu-id="7a91e-135">(省略可能) ディストリビューターにアクセスできない場合や、ディストリビューターのデータベース ステータスがオフラインになっている可能性がある場合は、 **\@force** に **1** を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-135">(Optional) If the Distributor cannot be accessed or if the status of the database is suspect or offline, specify a value of **1** for **\@force**.</span></span> <span data-ttu-id="7a91e-136">(省略可能) パブリケーション データベースに対して [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) を実行しない場合は、 **\@dbname** にデータベースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-136">(Optional) Specify the name of the database for **\@dbname** if [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) is not executed on the publication database.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="7a91e-137">**\@force** に **1** を指定すると、レプリケーション関連のパブリッシング オブジェクトがデータベース上に残されます。</span><span class="sxs-lookup"><span data-stu-id="7a91e-137">Specifying a value of **1** for **\@force** may leave replication-related publishing objects in the database.</span></span>  
  
2.  <span data-ttu-id="7a91e-138">(省略可) このデータベースに他のパブリケーションが存在しない場合は、[sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) を実行し、マージ レプリケーションを使用した、現在のデータベースのパブリケーションを無効にします。</span><span class="sxs-lookup"><span data-stu-id="7a91e-138">(Optional) If this database has no other publications, execute [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) to disable publication of the current database using merge replication.</span></span>  
  
3.  <span data-ttu-id="7a91e-139">(省略可) サブスクライバー側のサブスクリプション データベースに対して [sp_mergesubscription_cleanup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql) を実行し、サブスクリプション データベースに残っているレプリケーション メタデータをすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-139">(Optional) At the Subscriber on the subscription database, execute [sp_mergesubscription_cleanup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql) to remove any remaining replication metadata in the subscription database.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="7a91e-140">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7a91e-140">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="7a91e-141">次の例は、トランザクション パブリケーションを削除し、データベースのトランザクション パブリッシングを無効にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7a91e-141">This example shows how to remove a transactional publication and disable transactional publishing for a database.</span></span> <span data-ttu-id="7a91e-142">すべてのサブスクリプションがあらかじめ削除されていることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="7a91e-142">This example assumes that all subscriptions were previously removed.</span></span> <span data-ttu-id="7a91e-143">詳細については、「 [Delete a Pull Subscription](../delete-a-pull-subscription.md) 」または「 [Delete a Push Subscription](../delete-a-push-subscription.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a91e-143">For more information, see [Delete a Pull Subscription](../delete-a-pull-subscription.md) or [Delete a Push Subscription](../delete-a-push-subscription.md).</span></span>  
  
 [!code-sql[HowTo#sp_droppublication](../../../snippets/tsql/SQL15/replication/howto/tsql/droptranpub.sql#sp_droppublication)]  
  
 <span data-ttu-id="7a91e-144">次の例は、マージ パブリケーションを削除し、データベースのマージ パブリッシングを無効にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7a91e-144">This example shows how to remove a merge publication and disable merge publishing for a database.</span></span> <span data-ttu-id="7a91e-145">すべてのサブスクリプションがあらかじめ削除されていることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="7a91e-145">This example assumes that all subscriptions were previously removed.</span></span> <span data-ttu-id="7a91e-146">詳細については、「 [Delete a Pull Subscription](../delete-a-pull-subscription.md) 」または「 [Delete a Push Subscription](../delete-a-push-subscription.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a91e-146">For more information, see [Delete a Pull Subscription](../delete-a-pull-subscription.md) or [Delete a Push Subscription](../delete-a-push-subscription.md).</span></span>  
  
 [!code-sql[HowTo#sp_dropmergepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepub.sql#sp_dropmergepublication)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="7a91e-147">レプリケーション管理オブジェクト (RMO) の使用</span><span class="sxs-lookup"><span data-stu-id="7a91e-147">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="7a91e-148">レプリケーション管理オブジェクト (RMO) を使用することで、プログラムによってパブリケーションを削除できます。</span><span class="sxs-lookup"><span data-stu-id="7a91e-148">You can delete publications programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="7a91e-149">パブリケーションの削除に使用する RMO クラスは、削除するパブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="7a91e-149">The RMO classes that you use to remove a publication depend on the type of publication you remove.</span></span>  
  
#### <a name="to-remove-a-snapshot-or-transactional-publication"></a><span data-ttu-id="7a91e-150">スナップショット パブリケーションまたはトランザクション パブリケーションを削除するには</span><span class="sxs-lookup"><span data-stu-id="7a91e-150">To remove a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="7a91e-151"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-151">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="7a91e-152"><xref:Microsoft.SqlServer.Replication.TransPublication> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-152">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPublication> class.</span></span>  
  
3.  <span data-ttu-id="7a91e-153">パブリケーションの <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> プロパティおよび <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> プロパティを設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成した接続を設定します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-153">Set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="7a91e-154"><xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> プロパティをチェックして、パブリケーションが存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-154">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the publication exists.</span></span> <span data-ttu-id="7a91e-155">このプロパティの値が `false` である場合は、手順 3. でパブリケーション プロパティが不適切に定義されたか、パブリケーションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="7a91e-155">If the value of this property is `false`, either the publication properties in step 3 were defined incorrectly or the publication does not exist.</span></span>  
  
5.  <span data-ttu-id="7a91e-156"><xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-156">Call the <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> method.</span></span>  
  
6.  <span data-ttu-id="7a91e-157">(省略可) このデータベースに他のトランザクション パブリケーションが存在する場合は、次に示すように、トランザクション パブリッシングに対してデータベースを無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="7a91e-157">(Optional) If no other transactional publications exist for this database, the database can be disabled for transactional publishing as follows:</span></span>  
  
    1.  <span data-ttu-id="7a91e-158"><xref:Microsoft.SqlServer.Replication.ReplicationDatabase> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-158">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> class.</span></span> <span data-ttu-id="7a91e-159">手順 1. の <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> インスタンスを <xref:Microsoft.SqlServer.Management.Common.ServerConnection> プロパティに設定します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-159">Set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the instance of <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1.</span></span>  
  
    2.  <span data-ttu-id="7a91e-160"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-160">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="7a91e-161">このメソッドにより `false` が返された場合は、データベースが存在することを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7a91e-161">If this method returns `false`, confirm that the database exists.</span></span>  
  
    3.  <span data-ttu-id="7a91e-162"><xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing%2A> プロパティを `false`に設定します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-162">Set the <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing%2A> property to `false`.</span></span>  
  
    4.  <span data-ttu-id="7a91e-163"><xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-163">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="7a91e-164">接続を閉じます。</span><span class="sxs-lookup"><span data-stu-id="7a91e-164">Close the connections.</span></span>  
  
#### <a name="to-remove-a-merge-publication"></a><span data-ttu-id="7a91e-165">マージ パブリケーションを削除するには</span><span class="sxs-lookup"><span data-stu-id="7a91e-165">To remove a merge publication</span></span>  
  
1.  <span data-ttu-id="7a91e-166"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-166">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="7a91e-167"><xref:Microsoft.SqlServer.Replication.MergePublication> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-167">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class.</span></span>  
  
3.  <span data-ttu-id="7a91e-168">パブリケーションの <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> プロパティおよび <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> プロパティを設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成した接続を設定します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-168">Set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="7a91e-169"><xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> プロパティをチェックして、パブリケーションが存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-169">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the publication exists.</span></span> <span data-ttu-id="7a91e-170">このプロパティの値が `false` である場合は、手順 3. でパブリケーション プロパティが不適切に定義されたか、パブリケーションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="7a91e-170">If the value of this property is `false`, either the publication properties in step 3 were defined incorrectly or the publication does not exist.</span></span>  
  
5.  <span data-ttu-id="7a91e-171"><xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-171">Call the <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> method.</span></span>  
  
6.  <span data-ttu-id="7a91e-172">(省略可) このデータベースに他のマージ パブリケーションが存在する場合は、次に示すように、マージ パブリッシングに対してデータベースを無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="7a91e-172">(Optional) If no other merge publications exist for this database, the database can be disabled for merge publishing as follows:</span></span>  
  
    1.  <span data-ttu-id="7a91e-173"><xref:Microsoft.SqlServer.Replication.ReplicationDatabase> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-173">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> class.</span></span> <span data-ttu-id="7a91e-174"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティを、手順 1. の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> のインスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-174">Set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the instance of <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from Step 1.</span></span>  
  
    2.  <span data-ttu-id="7a91e-175"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-175">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="7a91e-176">このメソッドが `false` を返す場合、データベースが存在するかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7a91e-176">If this method returns `false`, verify that the database exists.</span></span>  
  
    3.  <span data-ttu-id="7a91e-177"><xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> プロパティを `false`に設定します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-177">Set the <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> property to `false`.</span></span>  
  
    4.  <span data-ttu-id="7a91e-178"><xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-178">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="7a91e-179">接続を閉じます。</span><span class="sxs-lookup"><span data-stu-id="7a91e-179">Close the connections.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="7a91e-180">例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="7a91e-180">Examples (RMO)</span></span>  
 <span data-ttu-id="7a91e-181">次の例では、トランザクション パブリケーションを削除します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-181">The following example deletes a transactional publication.</span></span> <span data-ttu-id="7a91e-182">このデータベースに対して他のトランザクション パブリケーションが存在しない場合は、トランザクション パブリッシングも無効になります。</span><span class="sxs-lookup"><span data-stu-id="7a91e-182">If no other transactional publications exist for this database, transactional publishing is also disabled.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropTranPub](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_droptranpub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPub](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_droptranpub)]  
  
 <span data-ttu-id="7a91e-183">次の例では、マージ パブリケーションを削除します。</span><span class="sxs-lookup"><span data-stu-id="7a91e-183">The following example deletes a merge publication.</span></span> <span data-ttu-id="7a91e-184">このデータベースに対して他のマージ パブリケーションが存在しない場合は、マージ パブリッシングも無効になります。</span><span class="sxs-lookup"><span data-stu-id="7a91e-184">If no other merge publications exist for this database, merge publishing is also disabled.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropMergePub](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePub](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropmergepub)]  
  
## <a name="see-also"></a><span data-ttu-id="7a91e-185">参照</span><span class="sxs-lookup"><span data-stu-id="7a91e-185">See Also</span></span>  
 <span data-ttu-id="7a91e-186">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="7a91e-186">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="7a91e-187">データとデータベース オブジェクトのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="7a91e-187">Publish Data and Database Objects</span></span>](publish-data-and-database-objects.md)  
  
  
