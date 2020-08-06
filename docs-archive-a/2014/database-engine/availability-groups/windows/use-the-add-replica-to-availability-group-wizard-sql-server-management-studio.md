---
title: 可用性グループへのレプリカ追加ウィザードの使用 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.f1
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], wizards
ms.assetid: 60d962b6-2af4-4394-9190-61939a102bc0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e4d75372cd2388e88fcb3d3ce95975bdefa54c5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634053"
---
# <a name="use-the-add-replica-to-availability-group-wizard-sql-server-management-studio"></a><span data-ttu-id="f86bc-102">可用性グループへのレプリカ追加ウィザードの使用 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f86bc-102">Use the Add Replica to Availability Group Wizard (SQL Server Management Studio)</span></span>
  <span data-ttu-id="f86bc-103">可用性グループへのレプリカの追加ウィザードを使用して、既存の AlwaysOn 可用性グループに新しいセカンダリ レプリカを追加できます。</span><span class="sxs-lookup"><span data-stu-id="f86bc-103">Use the Add Replica to Availability Group Wizard to help you a add new secondary replica to an existing AlwaysOn availability group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f86bc-104">[!INCLUDE[tsql](../../../includes/tsql-md.md)] または PowerShell を使用して可用性グループにセカンダリ レプリカを追加する方法については、「[可用性グループへのセカンダリ レプリカの追加 &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f86bc-104">For information about using [!INCLUDE[tsql](../../../includes/tsql-md.md)] or PowerShell to add a secondary replica to an availability group, see [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f86bc-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="f86bc-105">Before You Begin</span></span>  
 <span data-ttu-id="f86bc-106">可用性グループに可用性レプリカを追加したことがない場合は、「サーバーインスタンス」と「可用性グループとレプリカ」のセクション「 [AlwaysOn 可用性グループ &#40;SQL Server&#41;の前提条件、制限事項、推奨事項](prereqs-restrictions-recommendations-always-on-availability.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f86bc-106">If you have never added any availability replica to an availability group, see the "Server instances" and "Availability groups and replicas" sections in [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="f86bc-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="f86bc-107">Prerequisites</span></span>  
  
-   <span data-ttu-id="f86bc-108">現在のプライマリ レプリカをホストするサーバー インスタンスに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f86bc-108">You must be connected to the server instance that hosts the current primary replica.</span></span>  
  
-   <span data-ttu-id="f86bc-109">セカンダリ レプリカを追加する前に、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のホスト インスタンスが、既存のレプリカとして同じ Windows Server フェールオーバー クラスタリング (WSFC) クラスター内にあり、しかも異なるクラスター ノードにあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f86bc-109">Before adding a secondary replica, verify that the host instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is in the same Windows Server Failover Clustering (WSFC) cluster as the existing replicas but resides on a different cluster node.</span></span> <span data-ttu-id="f86bc-110">また、このサーバー インスタンスが [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の他のすべての前提条件を満たしていることも確認します。</span><span class="sxs-lookup"><span data-stu-id="f86bc-110">Also, verify that this server instance meets all other [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prerequisites.</span></span> <span data-ttu-id="f86bc-111">詳細については、「[AlwaysOn 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f86bc-111">For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
-   <span data-ttu-id="f86bc-112">可用性レプリカのホストとして選択したサーバー インスタンスがドメイン ユーザー アカウントで実行されていて、まだデータベース ミラーリング エンドポイントが存在しない場合、ウィザードでエンドポイントを作成し、サーバー インスタンスのサービス アカウントに CONNECT 権限を許可することができます。</span><span class="sxs-lookup"><span data-stu-id="f86bc-112">If a server instance that you select to host an availability replica is running under a domain user account and does not yet have a database mirroring endpoint, the wizard can create the endpoint and grant CONNECT permission to the server instance service account.</span></span> <span data-ttu-id="f86bc-113">ただし、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスがビルトイン アカウント (Local System、Local Service、Network Service など) で実行されている場合または非ドメイン アカウントで実行されている場合は、エンドポイント認証に証明書を使用する必要があります。ウィザードは、サーバー インスタンス上でデータベース ミラーリング エンドポイントを作成できなくなります。</span><span class="sxs-lookup"><span data-stu-id="f86bc-113">However, if the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service is running as a built-in account, such as Local System, Local Service, or Network Service, or a nondomain account, you must use certificates for endpoint authentication, and the wizard will be unable to create a database mirroring endpoint on the server instance.</span></span> <span data-ttu-id="f86bc-114">この場合は、データベース ミラーリング エンドポイントを手動で作成してから、可用性グループへのレプリカ追加ウィザードを起動することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f86bc-114">In this case, we recommend that you create the database mirroring endpoints manually before you launch the Add Replica to Availability Group Wizard.</span></span>  
  
     `To use certificates for a database mirroring endpoint:`  
  
     [<span data-ttu-id="f86bc-115">CREATE ENDPOINT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f86bc-115">CREATE ENDPOINT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-endpoint-transact-sql)  
  
     [<span data-ttu-id="f86bc-116">データベース ミラーリング エンドポイントでの証明書の使用 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f86bc-116">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   <span data-ttu-id="f86bc-117">**初期データの完全同期を使用するための前提条件**</span><span class="sxs-lookup"><span data-stu-id="f86bc-117">**Prerequisites for using full initial data synchronization**</span></span>  
  
    -   <span data-ttu-id="f86bc-118">可用性グループのレプリカをホストするすべてのサーバー インスタンスで、すべてのデータベース ファイルのパスが同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="f86bc-118">All the database-file paths must be identical on every server instance that hosts a replica for the availability group.</span></span>  
  
    -   <span data-ttu-id="f86bc-119">セカンダリ レプリカをホストするサーバー インスタンスにプライマリ データベース名が存在することはできません。</span><span class="sxs-lookup"><span data-stu-id="f86bc-119">No primary database name can exist on any server instance that hosts a secondary replica.</span></span> <span data-ttu-id="f86bc-120">これは、新しいセカンダリ データベースがまだ存在しないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="f86bc-120">This means that none of the new secondary databases can exist yet.</span></span>  
  
    -   <span data-ttu-id="f86bc-121">ウィザードでバックアップを作成し、バックアップにアクセスするために、ネットワーク共有を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f86bc-121">You will need to specify a network share in order for the wizard to create and access backups.</span></span> <span data-ttu-id="f86bc-122">プライマリ レプリカでは、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] の起動に使用するアカウントにネットワーク共有での読み取り/書き込みファイルシステム権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="f86bc-122">For the primary replica, the account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must have read and write file-system permissions on a network share.</span></span> <span data-ttu-id="f86bc-123">セカンダリ レプリカでは、アカウントは、ネットワーク共有に対する読み取り権限を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="f86bc-123">For secondary replicas, the account must have read permission on the network share.</span></span>  
  
     <span data-ttu-id="f86bc-124">ウィザードを使用して初期データの完全同期を実行できない場合は、セカンダリ データベースを手動で準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f86bc-124">If you are unable to use the wizard to perform full initial data synchronization, you need to prepare your secondary databases manually.</span></span> <span data-ttu-id="f86bc-125">これは、ウィザードの実行前でも実行後でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="f86bc-125">You can do this before or after running the wizard.</span></span> <span data-ttu-id="f86bc-126">詳細については、「 [可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)、または PowerShell を使用して、AlwaysOn 可用性グループにセカンダリ データベースを参加させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f86bc-126">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f86bc-127">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f86bc-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f86bc-128">Permissions</span><span class="sxs-lookup"><span data-stu-id="f86bc-128">Permissions</span></span>  
 <span data-ttu-id="f86bc-129">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="f86bc-129">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
 <span data-ttu-id="f86bc-130">また、可用性グループへのレプリカ追加ウィザードでデータベース ミラーリング エンドポイントを管理できるようにする場合は、CONTROL ON ENDPOINT 権限も必要です。</span><span class="sxs-lookup"><span data-stu-id="f86bc-130">Also requires CONTROL ON ENDPOINT permission if you want to allow Add Replica to Availability Group Wizard to manage the database mirroring endpoint.</span></span>  
  

  
##  <a name="using-the-add-replica-to-availability-group-wizard-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f86bc-131">可用性グループへのレプリカ追加ウィザードの使用 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f86bc-131">Using the Add Replica to Availability Group Wizard (SQL Server Management Studio)</span></span>  
 <span data-ttu-id="f86bc-132">**可用性グループへのレプリカ追加ウィザードを使用するには**</span><span class="sxs-lookup"><span data-stu-id="f86bc-132">**To Use the Add Replica to Availability Group Wizard**</span></span>  
  
1.  <span data-ttu-id="f86bc-133">オブジェクト エクスプローラーで、可用性グループのプライマリ レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="f86bc-133">In Object Explorer, connect to the server instance that hosts the primary replica of the availability group, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="f86bc-134">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="f86bc-134">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="f86bc-135">セカンダリ レプリカを追加する可用性グループを右クリックし、 **[レプリカの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f86bc-135">Right-click the availability group to which you are adding a secondary replica, and select the **Add Replica** command.</span></span> <span data-ttu-id="f86bc-136">可用性グループへのレプリカ追加ウィザードが起動します。</span><span class="sxs-lookup"><span data-stu-id="f86bc-136">This launches the Add Replica to Availability Group Wizard.</span></span>  
  
4.  <span data-ttu-id="f86bc-137">**[既存のセカンダリ レプリカへの接続]** ページで、可用性グループのすべてのセカンダリ レプリカに接続します。</span><span class="sxs-lookup"><span data-stu-id="f86bc-137">On the **Connect to Existing Secondary Replicas** page, connect to every secondary replica in the availability group.</span></span> <span data-ttu-id="f86bc-138">詳細については、「既存のセカンダリレプリカへの接続」を参照してください。 [&#40;レプリカの追加ウィザードとデータベースの追加ウィザード&#41;](connect-to-existing-secondary-replicas-page.md)です。</span><span class="sxs-lookup"><span data-stu-id="f86bc-138">For more information, see [Connect to Existing Secondary Replicas Page &#40;Add Replica Wizard and Add Databases Wizard&#41;](connect-to-existing-secondary-replicas-page.md).</span></span>  
  
5.  <span data-ttu-id="f86bc-139">**[レプリカの指定]** ページで、可用性グループの 1 つまたは複数の新しいセカンダリ レプリカを指定し、構成します。</span><span class="sxs-lookup"><span data-stu-id="f86bc-139">On the **Specify Replicas** page, specify and configure one or more new secondary replicas for the availability group.</span></span> <span data-ttu-id="f86bc-140">このページには、3 つのタブがあります。</span><span class="sxs-lookup"><span data-stu-id="f86bc-140">This page contains three tabs.</span></span> <span data-ttu-id="f86bc-141">次の表では、これらのタブについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f86bc-141">The following table introduces these tabs.</span></span> <span data-ttu-id="f86bc-142">詳細については、「[[レプリカの指定] ページ &#40;新しい可用性グループウィザード/レプリカの追加ウィザード&#41;](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f86bc-142">For more information, see [Specify Replicas Page &#40;New Availability Group Wizard: Add Replica Wizard&#41;](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md).</span></span>  
  
    |<span data-ttu-id="f86bc-143">タブ</span><span class="sxs-lookup"><span data-stu-id="f86bc-143">Tab</span></span>|<span data-ttu-id="f86bc-144">簡単な説明</span><span class="sxs-lookup"><span data-stu-id="f86bc-144">Brief Description</span></span>|  
    |---------|-----------------------|  
    |<span data-ttu-id="f86bc-145">**レプリカ**</span><span class="sxs-lookup"><span data-stu-id="f86bc-145">**Replicas**</span></span>|<span data-ttu-id="f86bc-146">このタブを使用して、新しいセカンダリ レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の各インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="f86bc-146">Use this tab to specify each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that will host a new secondary replica.</span></span>|  
    |<span data-ttu-id="f86bc-147">**エンドポイント**</span><span class="sxs-lookup"><span data-stu-id="f86bc-147">**Endpoints**</span></span>|<span data-ttu-id="f86bc-148">このタブを使用して、新しいセカンダリ レプリカに対する既存のデータベース ミラーリング エンドポイントを検証します (存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="f86bc-148">Use this tab to verify the existing database mirroring endpoint, if any, for each new secondary replica.</span></span> <span data-ttu-id="f86bc-149">サービス アカウントが Windows 認証を使用しているサーバー インスタンスでエンドポイントが不足している場合、ウィザードは、エンドポイントの自動作成を試行します。</span><span class="sxs-lookup"><span data-stu-id="f86bc-149">If this endpoint is lacking on a server instance whose service accounts use Windows Authentication, the wizard will attempt to create the endpoint automatically.</span></span> <span data-ttu-id="f86bc-150">**注:** ドメイン以外のユーザーアカウントで実行されているサーバーインスタンスがある場合は、ウィザードを続行する前に、サーバーインスタンスに手動で変更を加える必要があります。</span><span class="sxs-lookup"><span data-stu-id="f86bc-150">**Note:**  If any server instance is running under a non-domain user account, you need to do make a manual change to your server instance before you can proceed in the wizard.</span></span> <span data-ttu-id="f86bc-151">詳細については、このトピックの「 [前提条件](#Prerequisites)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f86bc-151">For more information, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>|  
    |<span data-ttu-id="f86bc-152">**バックアップの設定**</span><span class="sxs-lookup"><span data-stu-id="f86bc-152">**Backup Preferences**</span></span>|<span data-ttu-id="f86bc-153">このタブを使用して、可用性グループ全体のバックアップ設定を指定し (現在の設定を変更する場合)、各可用性レプリカのバックアップの優先順位を指定します。</span><span class="sxs-lookup"><span data-stu-id="f86bc-153">Use this tab to specify your backup preference for the availability group as a whole, if you wish to modify the current setting, and to specify your backup priorities for the individual availability replicas.</span></span>|  
  
6.  <span data-ttu-id="f86bc-154">**[最初のデータの同期を選択]** ページで、新しいセカンダリ データベースを作成して可用性グループに参加させる方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="f86bc-154">On the **Select Initial Data Synchronization** page, choose how you want your new secondary databases to be created and joined to the availability group.</span></span> <span data-ttu-id="f86bc-155">次のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="f86bc-155">Choose one of the following options:</span></span>  
  
    -   <span data-ttu-id="f86bc-156">**完全**</span><span class="sxs-lookup"><span data-stu-id="f86bc-156">**Full**</span></span>  
  
         <span data-ttu-id="f86bc-157">使用している環境が、初期データの同期を自動的に開始するための要件を満たす場合は、このオプションを選択します (詳細については、このトピックの「 [前提条件、制限事項、および推奨事項](#Prerequisites)」をご覧ください)。</span><span class="sxs-lookup"><span data-stu-id="f86bc-157">Select this option if your environment meets the requirements for automatically starting initial data synchronization (for more information, see [Prerequisites, Restrictions, and Recommendations](#Prerequisites), earlier in this topic).</span></span>  
  
         <span data-ttu-id="f86bc-158">**[完全]** を選択すると、可用性グループを作成後、ウィザードはすべてのプライマリ データベースとそのトランザクション ログをネットワーク共有にバックアップし、新しいセカンダリ レプリカをホストするすべてのサーバー インスタンスでそのバックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="f86bc-158">If you select **Full**, after creating the availability group, the wizard will back up every primary database and its transaction log to a network share and restore the backups on every server instance that hosts a new secondary replica.</span></span> <span data-ttu-id="f86bc-159">その後、ウィザードは、すべての新しいセカンダリ データベースを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="f86bc-159">The wizard will then join every new secondary database to the availability group.</span></span>  
  
         <span data-ttu-id="f86bc-160">**[すべてのレプリカからアクセス可能な共有ネットワーク場所を指定]** フィールドで、レプリカをホストするサーバー インスタンスが読み取り/書き込み権限を持つバックアップ共有を指定します。</span><span class="sxs-lookup"><span data-stu-id="f86bc-160">In the **Specify a shared network location accessible by all replicas:** field, specify a backup share to which all of the server instance that host replicas have read-write access.</span></span> <span data-ttu-id="f86bc-161">ログ バックアップは、ログ バックアップ チェーンの一部になります。</span><span class="sxs-lookup"><span data-stu-id="f86bc-161">The log backups will be part of your log backup chain.</span></span> <span data-ttu-id="f86bc-162">ログ バックアップ ファイルは適切に保存してください。</span><span class="sxs-lookup"><span data-stu-id="f86bc-162">Store the log backup files appropriately.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="f86bc-163">必要なファイル システム権限については、このトピックの「 [前提条件](#Prerequisites)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f86bc-163">For information about the required file-system permissions, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="f86bc-164">**[参加のみ]**</span><span class="sxs-lookup"><span data-stu-id="f86bc-164">**Join only**</span></span>  
  
         <span data-ttu-id="f86bc-165">新しいセカンダリ レプリカをホストするサーバー インスタンス上のセカンダリ データベースを手動で準備した場合は、このオプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="f86bc-165">If you have manually prepared secondary databases on the server instances that will host the new secondary replicas, you can select this option.</span></span> <span data-ttu-id="f86bc-166">ウィザードは、新しいセカンダリ データベースを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="f86bc-166">The wizard will join these new secondary databases to the availability group.</span></span>  
  
    -   <span data-ttu-id="f86bc-167">**[最初のデータの同期をスキップ]**</span><span class="sxs-lookup"><span data-stu-id="f86bc-167">**Skip initial data synchronization**</span></span>  
  
         <span data-ttu-id="f86bc-168">プライマリ データベースの独自のデータベースとログ バックアップを使用する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="f86bc-168">Select this option if you want to use your own database and log backups of your primary databases.</span></span> <span data-ttu-id="f86bc-169">詳細については、「[AlwaysOn セカンダリ データベース上のデータ移動の開始 &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f86bc-169">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
7.  <span data-ttu-id="f86bc-170">**[検証]** ページでは、このウィザードで指定した値が、可用性グループへのレプリカ追加ウィザードの要件を満たしているかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="f86bc-170">The **Validation** page verifies whether the values you specified in this Wizard meet the requirements of the Add Replica to Availability Group Wizard.</span></span> <span data-ttu-id="f86bc-171">変更が必要な場合は、 **[戻る]** をクリックして前のウィザード ページに戻り、値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="f86bc-171">To make a change, click **Previous** to return to an earlier wizard page to change one or more values.</span></span> <span data-ttu-id="f86bc-172">その後、 **[次へ]** をクリックして **[検証]** ページに戻り、 **[検証の再実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f86bc-172">The click **Next** to return to the **Validation** page, and click **Re-run Validation**.</span></span>  
  
8.  <span data-ttu-id="f86bc-173">**[概要]** ページで、新しい可用性グループに対して選択した内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="f86bc-173">On the **Summary** page, review your choices for the new availability group.</span></span> <span data-ttu-id="f86bc-174">変更が必要な場合は、 **[戻る]** をクリックして、該当するページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="f86bc-174">To make a change, click **Previous** to return to the relevant page.</span></span> <span data-ttu-id="f86bc-175">必要な変更を加えたら、 **[次へ]** をクリックして、 **[概要]** ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="f86bc-175">After making the change, click **Next** to return to the **Summary** page.</span></span>  
  
     <span data-ttu-id="f86bc-176">選択内容に問題がなければ、[スクリプト] をクリックして、ウィザードが実行する手順のスクリプトを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="f86bc-176">If you are satisfied with your selections, optionally click Script to create a script of the steps the wizard will execute.</span></span> <span data-ttu-id="f86bc-177">新しい可用性グループを作成して構成するには、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f86bc-177">Then, to create and configure the new availability group, click **Finish**.</span></span>  
  
9. <span data-ttu-id="f86bc-178">可用性グループの作成手順 (エンドポイントの構成、可用性グループの作成、グループへのセカンダリ レプリカの参加) の進行状況が、 **[進行状況]** ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="f86bc-178">The **Progress** page displays the progress of the steps for creating the availability group (configuring endpoints, creating the availability group, and joining the secondary replica to the group).</span></span>  
  
10. <span data-ttu-id="f86bc-179">以上の手順が完了すると、 **[結果]** ページに各手順の結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f86bc-179">When these steps complete, the **Results** page displays the result of each step.</span></span> <span data-ttu-id="f86bc-180">これらのすべての手順が成功した場合は、新しい可用性グループが完全に構成されます。</span><span class="sxs-lookup"><span data-stu-id="f86bc-180">If all these steps succeed, the new availability group is completely configured.</span></span> <span data-ttu-id="f86bc-181">手順のいずれかでエラーが発生した場合は、手動で構成を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f86bc-181">If any of the steps result in an error, you might need to manually complete the configuration.</span></span> <span data-ttu-id="f86bc-182">特定のエラーの原因については、 **[結果]** 列の [エラー] リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f86bc-182">For information about the cause of a given error, click the associated "Error" link in the **Result** column.</span></span>  
  
     <span data-ttu-id="f86bc-183">ウィザードでの作業が完了したら、 **[閉じる]** をクリックして終了します。</span><span class="sxs-lookup"><span data-stu-id="f86bc-183">When the wizard completes, click **Close** to exit.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f86bc-184">レプリカ追加後の操作については、「[可用性グループへのセカンダリ レプリカの追加 &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)」の「補足情報: レプリカの追加後」 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f86bc-184">After adding a replica, see the "Follow Up: After Adding a Replica" section in [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  

  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f86bc-185">関連タスク</span><span class="sxs-lookup"><span data-stu-id="f86bc-185">Related Tasks</span></span>  
  
-   [<span data-ttu-id="f86bc-186">可用性グループへのセカンダリ レプリカの追加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f86bc-186">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="f86bc-187">参照</span><span class="sxs-lookup"><span data-stu-id="f86bc-187">See Also</span></span>  
 <span data-ttu-id="f86bc-188">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f86bc-188">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="f86bc-189">[AlwaysOn 可用性グループ &#40;SQL Server の前提条件、制限事項、推奨事項&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="f86bc-189">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 [<span data-ttu-id="f86bc-190">可用性グループへのセカンダリ レプリカの追加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f86bc-190">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
  
