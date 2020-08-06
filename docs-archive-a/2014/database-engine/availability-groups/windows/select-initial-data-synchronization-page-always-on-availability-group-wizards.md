---
title: '[最初のデータの同期を選択] ページ (AlwaysOn 可用性グループウィザード) |Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.selectinitialdatasync.f1
- sql12.swb.adddatabasewizard.selectinitialdatasync.f1
- sql12.swb.newagwizard.selectinitialdatasync.f1
ms.assetid: 457b1140-4819-4def-8f7c-54a406e6db12
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 20f7d8fbe6f885136e030c80719f2e16d1c689f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740465"
---
# <a name="select-initial-data-synchronization-page-alwayson-availability-group-wizards"></a><span data-ttu-id="958e5-102">[最初のデータの同期を選択] ページ (AlwaysOn 可用性グループ ウィザード)</span><span class="sxs-lookup"><span data-stu-id="958e5-102">Select Initial Data Synchronization Page (AlwaysOn Availability Group Wizards)</span></span>
  <span data-ttu-id="958e5-103">新しいセカンダリ データベースの初期データ同期のユーザー設定を指定するには、AlwaysOn の **[最初のデータの同期を選択]** ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="958e5-103">Use the AlwaysOn **Select Initial Data Synchronization** page to indicate your preference for initial data synchronization of new secondary databases.</span></span> <span data-ttu-id="958e5-104">このページは、[!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)]、[!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)]、[!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] の 3 つのウィザードで共有されています。</span><span class="sxs-lookup"><span data-stu-id="958e5-104">This page is shared by three wizards-the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)], the [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)], and the [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)].</span></span>  
  
 <span data-ttu-id="958e5-105">可能な選択肢には、 **[完全]**、 **[参加のみ]**、または **[最初のデータの同期をスキップ]** が含まれます。</span><span class="sxs-lookup"><span data-stu-id="958e5-105">The possible choices include **Full**, **Join only**, or **Skip initial data synchronization**.</span></span> <span data-ttu-id="958e5-106">**[完全]** または **[参加のみ]** を選択する前に、使用している環境が前提条件を満たしていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="958e5-106">Before you select **Full** or **Join only** ensure that your environment meets the prerequisites.</span></span>  
  

  
##  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="958e5-107">推奨事項</span><span class="sxs-lookup"><span data-stu-id="958e5-107">Recommendations</span></span>  
  
-   <span data-ttu-id="958e5-108">初期データ同期の実行中は、プライマリ データベースのログ バックアップ タスクを中断します。</span><span class="sxs-lookup"><span data-stu-id="958e5-108">Suspend log backup tasks for the primary databases during initial data synchronization.</span></span>  
  
-   <span data-ttu-id="958e5-109">大規模なデータベースでは、完全バックアップ操作と復元操作に多くの時間とリソースが必要となる場合があります。</span><span class="sxs-lookup"><span data-stu-id="958e5-109">For large database, full backup and restore operations can take extensive time and resources.</span></span> <span data-ttu-id="958e5-110">このような場合は、セカンダリ データベースを手動で準備することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="958e5-110">In such cases, we recommend that you prepare secondary databases yourself.</span></span> <span data-ttu-id="958e5-111">詳細については、このトピックの「 [セカンダリ データベースを手動で準備するには](#PrepareSecondaryDbs)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="958e5-111">For more information, see [To Prepare Secondary Databases Manually](#PrepareSecondaryDbs), later in this topic.</span></span>  
  
-   <span data-ttu-id="958e5-112">初期データの完全同期では、ネットワーク共有を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="958e5-112">Full initial data synchronization requires you to specify a network share.</span></span> <span data-ttu-id="958e5-113">ウィザードを使用して初期データの完全同期を実行する前に、ネットワーク共有フォルダーのアクセス権限のセキュリティ プランを実装することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="958e5-113">Before you use a wizard to perform full initial data synchronization, we recommend that you implement a security plan for the access permissions on the network share folder.</span></span> <span data-ttu-id="958e5-114">この対策が重要なのは、フォルダーの読み取り権限を持つ人はだれでもバックアップ ファイル内の機密情報にアクセス可能であるためです。</span><span class="sxs-lookup"><span data-stu-id="958e5-114">This precaution is important because potentially sensitive data in the backup file can be accessed by anyone who has a READ permission on the folder.</span></span> <span data-ttu-id="958e5-115">また、バックアップおよび復元操作を保護するために、可用性レプリカをホストする各サーバー インスタンスとネットワーク共有フォルダー間のネットワーク チャネルをセキュリティで保護することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="958e5-115">Also, to protect your backup and restore operations, we recommend that you secure the network channels between every server instance that hosts an availability replica and the network share folder.</span></span>  
  
     <span data-ttu-id="958e5-116">バックアップおよび復元操作を高いセキュリティで保護する必要がある場合は、 **[参加のみ]** または **[最初のデータの同期をスキップ]** オプションのどちらかを選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="958e5-116">If your backup and restore operations must be highly secured, we recommend that you select either the **Join only** or **Skip initial data synchronization** option.</span></span>  
  
##  <a name="full"></a><a name="Full"></a><span data-ttu-id="958e5-117">全角</span><span class="sxs-lookup"><span data-stu-id="958e5-117">Full</span></span>  
 <span data-ttu-id="958e5-118">各プライマリ データベースに対して **[完全]** オプションを選択すると、1 つのワークフローで、プライマリ データベースの完全バックアップとログ バックアップを作成する、セカンダリ レプリカをホストする各サーバー インスタンスでこれらのバックアップを復元して、対応するセカンダリ データベースを作成する、各セカンダリ データベースを可用性グループに参加させる、という操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="958e5-118">For each primary database, the **Full** option performs several operations in one workflow:  create a full and log backup of the primary database, create the corresponding secondary databases by restoring these backups on every server instance that is hosting a secondary replica, and join each secondary database to availability group.</span></span>  
  
 <span data-ttu-id="958e5-119">使用している環境が、次の「初期データの完全同期を使用するための前提条件」を満たしており、ウィザードでデータ同期を自動的に開始する場合にのみ、このオプションを選択してください。</span><span class="sxs-lookup"><span data-stu-id="958e5-119">Select this option only if your environment meets the following prerequisites for using full initial data synchronization, and you want the wizard to automatically start data synchronization.</span></span>  
  
 <span data-ttu-id="958e5-120">**初期データの完全同期を使用するための前提条件**</span><span class="sxs-lookup"><span data-stu-id="958e5-120">**Prerequisites for using full initial data synchronization**</span></span>  
  
-   <span data-ttu-id="958e5-121">可用性グループのレプリカをホストするすべてのサーバー インスタンスで、すべてのデータベース ファイルのパスが同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="958e5-121">All the database-file paths must be identical on every server instance that hosts a replica for the availability group.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="958e5-122">ウィザードを実行するサーバー インスタンスとセカンダリ レプリカをホストするサーバー インスタンスで、バックアップ ファイルと復元ファイルのパスが異なる場合は、</span><span class="sxs-lookup"><span data-stu-id="958e5-122">If the backup and restore file paths differ between the server instance where you run the wizard and any server instance that is to host a secondary replica.</span></span> <span data-ttu-id="958e5-123">WITH MOVE オプションを使用して、バックアップ操作と復元操作を手動で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="958e5-123">The backup and restore operations must be performed manually using the WITH MOVE option.</span></span> <span data-ttu-id="958e5-124">詳細については、このトピックの「 [セカンダリ データベースを手動で準備するには](#PrepareSecondaryDbs)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="958e5-124">For more information, see [To Prepare Secondary Databases Manually](#PrepareSecondaryDbs), later in this topic.</span></span>  
  
-   <span data-ttu-id="958e5-125">セカンダリ レプリカをホストするサーバー インスタンスにプライマリ データベース名が存在することはできません。</span><span class="sxs-lookup"><span data-stu-id="958e5-125">No primary database name can exist on any server instance that hosts a secondary replica.</span></span> <span data-ttu-id="958e5-126">これは、新しいセカンダリ データベースがまだ存在しないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="958e5-126">This means that none of the new secondary databases can exist yet.</span></span>  
  
-   <span data-ttu-id="958e5-127">ウィザードでバックアップを作成し、バックアップにアクセスするために、ネットワーク共有を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="958e5-127">You will need to specify a network share in order for the wizard to create and access backups.</span></span> <span data-ttu-id="958e5-128">プライマリ レプリカでは、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] の起動に使用するアカウントにネットワーク共有での読み取り/書き込みファイルシステム権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="958e5-128">For the primary replica, the account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must have read and write file-system permissions on a network share.</span></span> <span data-ttu-id="958e5-129">セカンダリ レプリカでは、アカウントは、ネットワーク共有に対する読み取り権限を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="958e5-129">For secondary replicas, the account must have read permission on the network share.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="958e5-130">ログ バックアップは、ログ バックアップ チェーンの一部になります。</span><span class="sxs-lookup"><span data-stu-id="958e5-130">The log backups will be part of your log backup chain.</span></span> <span data-ttu-id="958e5-131">ログ バックアップ ファイルは適切に保存してください。</span><span class="sxs-lookup"><span data-stu-id="958e5-131">Store the log backup files appropriately.</span></span>  
  
 <span data-ttu-id="958e5-132">**前提条件を満たしていない場合**</span><span class="sxs-lookup"><span data-stu-id="958e5-132">**If prerequisites are not met**</span></span>  
  
 <span data-ttu-id="958e5-133">ウィザードでは、この可用性グループのセカンダリ データベースを作成できません。</span><span class="sxs-lookup"><span data-stu-id="958e5-133">The wizard cannot create the secondary databases for this availability group.</span></span> <span data-ttu-id="958e5-134">セカンダリ データベースを準備する方法については、このトピックの「 [セカンダリ データベースを手動で準備するには](#PrepareSecondaryDbs)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="958e5-134">For information on how to prepare them, see [To Prepare Secondary Databases Manually](#PrepareSecondaryDbs), later in this topic.</span></span>  
  
 <span data-ttu-id="958e5-135">**前提条件を満たしている場合**</span><span class="sxs-lookup"><span data-stu-id="958e5-135">**If prerequisites are met**</span></span>  
  
 <span data-ttu-id="958e5-136">前の前提条件がすべて満たされており、ウィザードで初期データの完全同期を実行する場合は、 **[完全]** オプションを選択し、ネットワーク共有を指定します。</span><span class="sxs-lookup"><span data-stu-id="958e5-136">If these prerequisites are all met and you want the wizard to perform full initial data synchronization, select the **Full** option and specify a network share.</span></span> <span data-ttu-id="958e5-137">これにより、ウィザードによって選択した各データベースの完全バックアップとログ バックアップが作成され、指定したネットワーク共有に配置されます。</span><span class="sxs-lookup"><span data-stu-id="958e5-137">This will cause  the wizard to create full database and log backups of every selected database and to place these backups on the network share that you specify.</span></span> <span data-ttu-id="958e5-138">その後、新しいセカンダリ レプリカの 1 つをホストする各サーバー インスタンスで、RESTORE WITH NORECOVERY を使用してバックアップを復元することで、セカンダリ データベースが作成されます。</span><span class="sxs-lookup"><span data-stu-id="958e5-138">Then, on every server instance that hosts one of the new secondary replicas, the wizard will create the secondary databases by restoring backups using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="958e5-139">各セカンダリ データベースが作成された後、新しいセカンダリ データベースを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="958e5-139">After creating each of the secondary databases, the wizard will join the new secondary database to the availability group.</span></span> <span data-ttu-id="958e5-140">セカンダリ データベースを参加させるとすぐに、データベース上でデータの同期が開始されます。</span><span class="sxs-lookup"><span data-stu-id="958e5-140">As soon as a secondary database is joined, data synchronizations starts on that database.</span></span>  
  
 <span data-ttu-id="958e5-141">**[すべてのレプリカからアクセス可能な共有ネットワーク場所を指定]**</span><span class="sxs-lookup"><span data-stu-id="958e5-141">**Specify a shared network location accessible by all replicas**</span></span>  
 <span data-ttu-id="958e5-142">バックアップを作成および復元するには、ウィザードでネットワーク共有を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="958e5-142">To create and restore backups, the wizard requires that you specify a network share.</span></span> <span data-ttu-id="958e5-143">可用性レプリカをホストする各サーバー インスタンス上で [!INCLUDE[ssDE](../../../includes/ssde-md.md)] を起動するために使用されるアカウントは、ネットワーク共有での読み取り/書き込みファイルシステム権限を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="958e5-143">The account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] on each server instance that will host an availability replica must have read and write file-system permissions on the network share.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="958e5-144">ログ バックアップは、ログ バックアップ チェーンの一部になります。</span><span class="sxs-lookup"><span data-stu-id="958e5-144">The log backups will be part of your log backup chain.</span></span> <span data-ttu-id="958e5-145">それらのバックアップ ファイルは、適切に保存してください。</span><span class="sxs-lookup"><span data-stu-id="958e5-145">Store their backup files appropriately.</span></span>  
  
##  <a name="join-only"></a><a name="Joinonly"></a><span data-ttu-id="958e5-146">結合のみ</span><span class="sxs-lookup"><span data-stu-id="958e5-146">Join only</span></span>  
 <span data-ttu-id="958e5-147">このオプションは、可用性グループのセカンダリ レプリカをホストする各サーバー インスタンス上に、新しいセカンダリ データベースが既に存在する場合にのみ選択します。</span><span class="sxs-lookup"><span data-stu-id="958e5-147">Select this option only if the new secondary databases already exist on each server instance that hosts a secondary replica for the availability group.</span></span> <span data-ttu-id="958e5-148">セカンダリ データベースの準備については、このセクションの「 [セカンダリ データベースを手動で準備するには](#PrepareSecondaryDbs)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="958e5-148">For information about preparing secondary databases, see [To Prepare Secondary Databases Manually](#PrepareSecondaryDbs), later in this section.</span></span>  
  
 <span data-ttu-id="958e5-149">**[参加のみ]** を選択すると、既存の各セカンダリ データベースを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="958e5-149">If you select **Join only**, the wizard will attempt to join each existing secondary database to the availability group.</span></span>  
  
## <a name="skip-initial-data-synchronization"></a><span data-ttu-id="958e5-150">[最初のデータの同期をスキップ]</span><span class="sxs-lookup"><span data-stu-id="958e5-150">Skip initial data synchronization</span></span>  
 <span data-ttu-id="958e5-151">このオプションは、各プライマリ データベースのデータベースおよびログ バックアップを実行し、セカンダリ レプリカをホストする各サーバー インスタンスに復元する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="958e5-151">Select this option if you want to perform your own database and log backups of every primary database, restore them to every server instance that hosts a secondary replica.</span></span> <span data-ttu-id="958e5-152">ウィザードの終了後、各セカンダリ レプリカのすべてのセカンダリ データベースを参加させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="958e5-152">After you exit the wizard, you will then need to join every secondary database on every secondary replica.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="958e5-153">詳細については、「[AlwaysOn セカンダリ データベース上のデータ移動の開始 &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="958e5-153">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
##  <a name="to-prepare-secondary-databases-manually"></a><a name="PrepareSecondaryDbs"></a><span data-ttu-id="958e5-154">セカンダリデータベースを手動で準備するには</span><span class="sxs-lookup"><span data-stu-id="958e5-154">To Prepare Secondary Databases Manually</span></span>  
 <span data-ttu-id="958e5-155">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ウィザードを使用せずにセカンダリ データベースを準備するには、次の方法のどちらかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="958e5-155">To prepare secondary databases independently of any [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] wizard, you can use either of the following approaches:</span></span>  
  
-   <span data-ttu-id="958e5-156">RESTORE WITH NORECOVERY を使用してプライマリ データベースの最新のデータベース バックアップを手動で復元し、その後、RESTORE WITH NORECOVERY を使用して後続のログ バックアップを復元する。</span><span class="sxs-lookup"><span data-stu-id="958e5-156">Manually restore a recent database backup of the primary database using RESTORE WITH NORECOVERY, and then restore each subsequent log backup using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="958e5-157">プライマリ データベースとセカンダリ データベースのファイル パスが異なる場合は、WITH MOVE オプションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="958e5-157">If the primary and secondary databases have different file paths, you must use the WITH MOVE option.</span></span> <span data-ttu-id="958e5-158">可用性グループのセカンダリ レプリカをホストする各サーバー インスタンスで、この復元シーケンスを実行します。</span><span class="sxs-lookup"><span data-stu-id="958e5-158">Perform this restore sequence on every server instance that hosts a secondary replica for the availability group.</span></span>  <span data-ttu-id="958e5-159">これらのバックアップ操作と復元操作は、 [!INCLUDE[tsql](../../../includes/tsql-md.md)] または PowerShell を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="958e5-159">You can use [!INCLUDE[tsql](../../../includes/tsql-md.md)] or PowerShell to perform these backup and restore operations.</span></span>  
  
     <span data-ttu-id="958e5-160">**詳細情報:**</span><span class="sxs-lookup"><span data-stu-id="958e5-160">**For more information:**</span></span>  
  
     [<span data-ttu-id="958e5-161">可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="958e5-161">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   <span data-ttu-id="958e5-162">可用性グループに 1 つ以上のログ配布プライマリ データベースを追加する場合、対応する 1 つ以上のセカンダリ データベースをログ配布から [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]に移行できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="958e5-162">If you are adding one or more log shipping primary databases to an availability group, you might be able to migrate one or more of the corresponding secondary databases from log shipping to [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="958e5-163">詳細については、「[ログ配布から AlwaysOn 可用性グループ &#40;SQL Server&#41;への移行の前提条件](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="958e5-163">For more information, see [Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="958e5-164">可用性グループのすべてのセカンダリ データベースを作成した後、セカンダリ レプリカにバックアップを実行する場合は、可用性グループの自動バックアップ設定を再構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="958e5-164">After you have created all the secondary databases for the availability group, if you want to perform backups on secondary replicas, you will need to re-configure the automated backup preference of the availability group.</span></span>  
  
     <span data-ttu-id="958e5-165">**詳細情報:**</span><span class="sxs-lookup"><span data-stu-id="958e5-165">**For more information:**</span></span>  
  
     [<span data-ttu-id="958e5-166">ログ配布から AlwaysOn 可用性グループ &#40;SQL Server への移行の前提条件&#41;</span><span class="sxs-lookup"><span data-stu-id="958e5-166">Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)  
  
     [<span data-ttu-id="958e5-167">可用性レプリカでのバックアップの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="958e5-167">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
 <span data-ttu-id="958e5-168">セカンダリ データベースの作成後、現在のすべてのログ バックアップを新しいセカンダリ データベースに適用します。</span><span class="sxs-lookup"><span data-stu-id="958e5-168">After creating a secondary database, apply all current log backups to the new secondary database.</span></span>  
  
 <span data-ttu-id="958e5-169">すべてのセカンダリ データベースを準備してから、ウィザードを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="958e5-169">Optionally, you can prepare all the secondary databases before you run the wizard.</span></span> <span data-ttu-id="958e5-170">この場合、ウィザードの **[最初のデータの同期を選択]** ページで **[参加のみ]** を選択して、準備した新しいセカンダリ データベースを可用性グループに自動的に参加させます。</span><span class="sxs-lookup"><span data-stu-id="958e5-170">Then, on the wizard's **Specify Initial Data Synchronization** page, select **Join only** to automatically join your new secondary databases to the availability group.</span></span>  
  
##  <a name="related-tasks"></a><a name="LaunchWiz"></a> <span data-ttu-id="958e5-171">関連タスク</span><span class="sxs-lookup"><span data-stu-id="958e5-171">Related Tasks</span></span>  
  
-   <span data-ttu-id="958e5-172">[[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="958e5-172">[Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span></span>  
  
-   [<span data-ttu-id="958e5-173">可用性グループへのレプリカ追加ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="958e5-173">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="958e5-174">可用性グループへのデータベース追加ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="958e5-174">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
-   [<span data-ttu-id="958e5-175">可用性グループのフェールオーバー ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="958e5-175">Use the Fail Over Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="958e5-176">AlwaysOn セカンダリデータベース &#40;SQL Server でのデータ移動の開始&#41;</span><span class="sxs-lookup"><span data-stu-id="958e5-176">Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;</span></span>](start-data-movement-on-an-always-on-secondary-database-sql-server.md)  
  
-   [<span data-ttu-id="958e5-177">可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="958e5-177">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   <span data-ttu-id="958e5-178">[[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="958e5-178">[Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="958e5-179">参照</span><span class="sxs-lookup"><span data-stu-id="958e5-179">See Also</span></span>  
 [<span data-ttu-id="958e5-180">AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;</span><span class="sxs-lookup"><span data-stu-id="958e5-180">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
