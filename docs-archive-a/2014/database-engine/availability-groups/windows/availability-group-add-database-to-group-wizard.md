---
title: 可用性グループへのデータベース追加ウィザードの使用 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.adddatabasewizard.f1
helpviewer_keywords:
- Availability Groups [SQL Server], wizards
- Availability Groups [SQL Server], databases
ms.assetid: 81e5e36d-735d-4731-8017-2654673abb88
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a093bb23687d4e49d311b46a7bb0bd211016a0ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632133"
---
# <a name="use-the-add-database-to-availability-group-wizard-sql-server-management-studio"></a><span data-ttu-id="068c7-102">可用性グループへのデータベース追加ウィザードの使用 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="068c7-102">Use the Add Database to Availability Group Wizard (SQL Server Management Studio)</span></span>
  <span data-ttu-id="068c7-103">可用性グループへのデータベースの追加ウィザードを使用して、既存の AlwaysOn 可用性グループに 1 つ以上のデータベースを追加できます。</span><span class="sxs-lookup"><span data-stu-id="068c7-103">Use the Add Database to Availability Group Wizard to help you add one or more databases to an existing AlwaysOn availability group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="068c7-104">[!INCLUDE[tsql](../../../includes/tsql-md.md)] または PowerShell を使用してデータベースを追加する方法については、「[可用性グループへのデータベースの追加 &#40;SQL Server&#41;](availability-group-add-a-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="068c7-104">For information about using [!INCLUDE[tsql](../../../includes/tsql-md.md)] or PowerShell to add a database, see [Add a Database to an Availability Group &#40;SQL Server&#41;](availability-group-add-a-database.md).</span></span>  
  
 <span data-ttu-id="068c7-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="068c7-105">**In This Topic:**</span></span>  
  
-   <span data-ttu-id="068c7-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="068c7-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="068c7-107">前提条件と制限</span><span class="sxs-lookup"><span data-stu-id="068c7-107">Prerequisites and Restrictions</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="068c7-108">Security</span><span class="sxs-lookup"><span data-stu-id="068c7-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="068c7-109">**データベースの追加に使用するもの:**  [可用性グループへのデータベース追加ウィザード (SQL Server Management Studio)](#SSMSProcedure)</span><span class="sxs-lookup"><span data-stu-id="068c7-109">**To add a database, using:**  [Add Database to Availability Group Wizard (SQL Server Management Studio)](#SSMSProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="068c7-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="068c7-110">Before You Begin</span></span>  
 <span data-ttu-id="068c7-111">可用性グループにデータベースを追加したことがない場合は、「 [AlwaysOn 可用性グループ &#40;SQL Server&#41;の前提条件、制限事項、および推奨事項](prereqs-restrictions-recommendations-always-on-availability.md)」の「可用性データベース」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="068c7-111">If you have never added a database to an availability group, see the "Availability Databases" section in [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="prerequisites-restrictions-and-recommendations"></a><a name="Prerequisites"></a><span data-ttu-id="068c7-112">前提条件、制限事項、および推奨事項</span><span class="sxs-lookup"><span data-stu-id="068c7-112">Prerequisites, Restrictions, and Recommendations</span></span>  
  
-   <span data-ttu-id="068c7-113">現在のプライマリ レプリカをホストするサーバー インスタンスに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="068c7-113">You must be connected to the server instance that hosts the current primary replica.</span></span>  
  
-   <span data-ttu-id="068c7-114">データベースが暗号化されているか、データベース暗号化キー (DEK) を含んでいる場合、 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] または [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] を使用してそのデータベースを可用性グループに追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="068c7-114">If a database is encrypted or even contains a Database Encryption Key (DEK), you cannot use the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] or [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] to add the database to an availability group.</span></span> <span data-ttu-id="068c7-115">暗号化されたデータベースの暗号化を解除した場合でも、そのログ バックアップには暗号化されたデータが含まれていることがあります。</span><span class="sxs-lookup"><span data-stu-id="068c7-115">Even if an encrypted database has been decrypted, its log backups might contain encrypted data.</span></span> <span data-ttu-id="068c7-116">この場合、データベースに対する初期データの完全同期が失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="068c7-116">In this case, full initial data synchronization could fail on the database.</span></span> <span data-ttu-id="068c7-117">これは、ログの復元操作にはデータベース暗号化キー (DEK) で使用された証明書が必要なことがあり、その証明書を使用できないことがあるためです。</span><span class="sxs-lookup"><span data-stu-id="068c7-117">This is because the restore log operation might require the certificate that was used by the database encryption keys (DEKs), and that certificate might be unavailable.</span></span>  
  
     <span data-ttu-id="068c7-118">**暗号化解除されたデータベースを、ウィザードを使用して可用性グループに追加できるようにするには、次の操作を行います。**</span><span class="sxs-lookup"><span data-stu-id="068c7-118">**To make a decrypted database eligible to add to an availability group using the wizard:**</span></span>  
  
    1.  <span data-ttu-id="068c7-119">プライマリ データベースのログ バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="068c7-119">Create a log backup of the primary database.</span></span>  
  
    2.  <span data-ttu-id="068c7-120">プライマリ データベースの完全バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="068c7-120">Create a full database backup of the primary database.</span></span>  
  
    3.  <span data-ttu-id="068c7-121">セカンダリ レプリカをホストするサーバー インスタンスでデータベース バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="068c7-121">Restore the database backup on the server instance that hosts the secondary replica.</span></span>  
  
    4.  <span data-ttu-id="068c7-122">プライマリ データベースから新しいログ バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="068c7-122">Create a new log backup from primary database.</span></span>  
  
    5.  <span data-ttu-id="068c7-123">セカンダリ データベースでこのログ バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="068c7-123">Restore this log backup on the secondary database.</span></span>  
  
-   <span data-ttu-id="068c7-124">**初期データの完全同期を使用するための前提条件**</span><span class="sxs-lookup"><span data-stu-id="068c7-124">**Prerequisites for using full initial data synchronization**</span></span>  
  
    -   <span data-ttu-id="068c7-125">可用性グループのレプリカをホストするすべてのサーバー インスタンスで、すべてのデータベース ファイルのパスが同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="068c7-125">All the database-file paths must be identical on every server instance that hosts a replica for the availability group.</span></span>  
  
    -   <span data-ttu-id="068c7-126">セカンダリ レプリカをホストするサーバー インスタンスにプライマリ データベース名が存在することはできません。</span><span class="sxs-lookup"><span data-stu-id="068c7-126">No primary database name can exist on any server instance that hosts a secondary replica.</span></span> <span data-ttu-id="068c7-127">これは、新しいセカンダリ データベースがまだ存在しないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="068c7-127">This means that none of the new secondary databases can exist yet.</span></span>  
  
    -   <span data-ttu-id="068c7-128">ウィザードでバックアップを作成し、バックアップにアクセスするために、ネットワーク共有を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="068c7-128">You will need to specify a network share in order for the wizard to create and access backups.</span></span> <span data-ttu-id="068c7-129">プライマリ レプリカでは、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] の起動に使用するアカウントにネットワーク共有での読み取り/書き込みファイルシステム権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="068c7-129">For the primary replica, the account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must have read and write file-system permissions on a network share.</span></span> <span data-ttu-id="068c7-130">セカンダリ レプリカでは、アカウントは、ネットワーク共有に対する読み取り権限を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="068c7-130">For secondary replicas, the account must have read permission on the network share.</span></span>  
  
     <span data-ttu-id="068c7-131">ウィザードを使用して初期データの完全同期を実行できない場合は、セカンダリ データベースを手動で準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="068c7-131">If you are unable to use the wizard to perform full initial data synchronization, you need to prepare your secondary databases manually.</span></span> <span data-ttu-id="068c7-132">これは、ウィザードの実行前でも実行後でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="068c7-132">You can do this before or after running the wizard.</span></span> <span data-ttu-id="068c7-133">詳細については、「 [可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)、または PowerShell を使用して、AlwaysOn 可用性グループにセカンダリ データベースを参加させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="068c7-133">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="068c7-134">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="068c7-134">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="068c7-135">Permissions</span><span class="sxs-lookup"><span data-stu-id="068c7-135">Permissions</span></span>  
 <span data-ttu-id="068c7-136">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="068c7-136">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-the-add-database-to-availability-group-wizard-sql-server-management-studio"></a><a name="SSMSProcedure"></a><span data-ttu-id="068c7-137">可用性グループへのデータベース追加ウィザードの使用 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="068c7-137">Using the Add Database to Availability Group Wizard (SQL Server Management Studio)</span></span>  
 <span data-ttu-id="068c7-138">**可用性グループへのデータベース追加ウィザードを使用するには**</span><span class="sxs-lookup"><span data-stu-id="068c7-138">**To Use the Add Database to Availability Group Wizard**</span></span>  
  
1.  <span data-ttu-id="068c7-139">オブジェクト エクスプローラーで、可用性グループのプライマリ レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="068c7-139">In Object Explorer, connect to the server instance that hosts the primary replica of the availability group, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="068c7-140">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="068c7-140">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="068c7-141">データベースを追加する可用性グループを右クリックして、 **[データベースの追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="068c7-141">Right-click the availability group to which you are adding a database, and select the **Add Database** command.</span></span> <span data-ttu-id="068c7-142">可用性グループへのデータベース追加ウィザードが起動します。</span><span class="sxs-lookup"><span data-stu-id="068c7-142">This command launches the Add Database to Availability Group Wizard.</span></span>  
  
4.  <span data-ttu-id="068c7-143">**[データベースの選択]** ページで 1 つまたは複数のデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="068c7-143">On the **Select Databases** page, select one or more databases.</span></span> <span data-ttu-id="068c7-144">詳細については、「 [[データベースの選択] ページ &#40;新しい可用性グループウィザード-データベースの追加ウィザード&#41;](select-databases-page-new-availability-group-wizard-and-add-database-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="068c7-144">For more information, see [Select Databases Page &#40;New Availability Group Wizard-Add Database Wizard&#41;](select-databases-page-new-availability-group-wizard-and-add-database-wizard.md).</span></span>  
  
5.  <span data-ttu-id="068c7-145">**[最初のデータの同期を選択]** ページで、新しいセカンダリ データベースを作成して可用性グループに参加させる方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="068c7-145">On the **Select Initial Data Synchronization** page, choose how you want your new secondary databases to be created and joined to the availability group.</span></span> <span data-ttu-id="068c7-146">次のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="068c7-146">Choose one of the following options:</span></span>  
  
    -   <span data-ttu-id="068c7-147">**完全**</span><span class="sxs-lookup"><span data-stu-id="068c7-147">**Full**</span></span>  
  
         <span data-ttu-id="068c7-148">使用している環境が、初期データの同期を自動的に開始するための要件を満たす場合は、このオプションを選択します (詳細については、このトピックの「 [前提条件、制限事項、および推奨事項](#Prerequisites)」をご覧ください)。</span><span class="sxs-lookup"><span data-stu-id="068c7-148">Select this option if your environment meets the requirements for automatically starting initial data synchronization (for more information, see [Prerequisites, Restrictions, and Recommendations](#Prerequisites), earlier in this topic).</span></span>  
  
         <span data-ttu-id="068c7-149">**[完全]** を選択すると、可用性グループを作成後、ウィザードはすべてのプライマリ データベースとそのトランザクション ログをネットワーク共有にバックアップし、セカンダリ レプリカをホストするすべてのサーバー インスタンスでそのバックアップを復元しようとします。</span><span class="sxs-lookup"><span data-stu-id="068c7-149">If you select **Full**, after creating the availability group, the wizard will attempt to back up every primary database and its transaction log to a network share and restore the backups on every server instance that hosts an secondary replica.</span></span> <span data-ttu-id="068c7-150">その後、ウィザードは、すべてのセカンダリ データベースを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="068c7-150">The wizard will then join every secondary database to the availability group.</span></span>  
  
         <span data-ttu-id="068c7-151">**[すべてのレプリカからアクセス可能な共有ネットワーク場所を指定]** フィールドで、レプリカをホストするサーバー インスタンスが読み取り/書き込み権限を持つバックアップ共有を指定します。</span><span class="sxs-lookup"><span data-stu-id="068c7-151">In the **Specify a shared network location accessible by all replicas:** field, specify a backup share to which all of the server instance that host replicas have read-write access.</span></span> <span data-ttu-id="068c7-152">ログ バックアップは、ログ バックアップ チェーンの一部になります。</span><span class="sxs-lookup"><span data-stu-id="068c7-152">The log backups will be part of your log backup chain.</span></span> <span data-ttu-id="068c7-153">ログ バックアップ ファイルは適切に保存してください。</span><span class="sxs-lookup"><span data-stu-id="068c7-153">Store the log backup files appropriately.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="068c7-154">必要なファイル システム権限については、このトピックの「 [前提条件](#Prerequisites)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="068c7-154">For information about the required file-system permissions, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="068c7-155">**[参加のみ]**</span><span class="sxs-lookup"><span data-stu-id="068c7-155">**Join only**</span></span>  
  
         <span data-ttu-id="068c7-156">セカンダリ レプリカをホストするサーバー インスタンス上のセカンダリ データベースを手動で準備した場合は、このオプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="068c7-156">If you have manually prepared secondary databases on the server instances that will host the secondary replicas, you can select this option.</span></span> <span data-ttu-id="068c7-157">ウィザードは、既存のセカンダリ データベースを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="068c7-157">The wizard will join the existing secondary databases to the availability group.</span></span>  
  
    -   <span data-ttu-id="068c7-158">**[最初のデータの同期をスキップ]**</span><span class="sxs-lookup"><span data-stu-id="068c7-158">**Skip initial data synchronization**</span></span>  
  
         <span data-ttu-id="068c7-159">プライマリ データベースの独自のデータベースとログ バックアップを使用する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="068c7-159">Select this option if you want to use your own database and log backups of your primary databases.</span></span> <span data-ttu-id="068c7-160">詳細については、「[AlwaysOn セカンダリ データベース上のデータ移動の開始 &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="068c7-160">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
     <span data-ttu-id="068c7-161">詳細については、「 [AlwaysOn 可用性グループウィザード&#41;&#40;[初期データの同期を選択] ページ](select-initial-data-synchronization-page-always-on-availability-group-wizards.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="068c7-161">For more information, see [Select Initial Data Synchronization Page &#40;AlwaysOn Availability Group Wizards&#41;](select-initial-data-synchronization-page-always-on-availability-group-wizards.md).</span></span>  
  
6.  <span data-ttu-id="068c7-162">**[既存のセカンダリ レプリカへの接続]** ページで、この可用性グループの可用性レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスがすべて同じユーザー アカウントのサービスとして実行されている場合、 **[すべて接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="068c7-162">On the **Connect to Existing Secondary Replicas** page, if the instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that host the availability replicas for this availability group are all running as a service in the same user account, click **Connect all**.</span></span> <span data-ttu-id="068c7-163">サーバー インスタンスがサービスとして複数のアカウントで実行されている場合、各サーバー インスタンス名の右側の **[接続]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="068c7-163">If any of the server instances are running as a service under different accounts, click the individual **Connect** button to the right of each server instance name.</span></span>  
  
     <span data-ttu-id="068c7-164">詳細については、「既存のセカンダリレプリカへの接続」を参照してください。 [&#40;レプリカの追加ウィザードとデータベースの追加ウィザード&#41;](connect-to-existing-secondary-replicas-page.md)です。</span><span class="sxs-lookup"><span data-stu-id="068c7-164">For more information, see [Connect to Existing Secondary Replicas Page &#40;Add Replica Wizard and Add Databases Wizard&#41;](connect-to-existing-secondary-replicas-page.md).</span></span>  
  
7.  <span data-ttu-id="068c7-165">**[検証]** ページでは、このウィザードで指定した値が、新しい可用性グループ ウィザードの要件を満たしているかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="068c7-165">The **Validation** page verifies whether the values you specified in this Wizard meet the requirements of the New Availability Group Wizard.</span></span> <span data-ttu-id="068c7-166">変更が必要な場合は、 **[戻る]** をクリックして前のウィザード ページに戻り、値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="068c7-166">To make a change, you can click **Previous** to return to an earlier wizard page to change one or more values.</span></span> <span data-ttu-id="068c7-167">その後、 **[次へ]** をクリックして **[検証]** ページに戻り、 **[検証の再実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="068c7-167">The click **Next** to return to the **Validation** page, and click **Re-run Validation**.</span></span>  
  
     <span data-ttu-id="068c7-168">詳細については、「[[検証] ページ &#40;AlwaysOn 可用性グループウィザード&#41;](validation-page-always-on-availability-group-wizards.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="068c7-168">For more information, see [Validation Page &#40;AlwaysOn Availability Group Wizards&#41;](validation-page-always-on-availability-group-wizards.md).</span></span>  
  
8.  <span data-ttu-id="068c7-169">**[概要]** ページで、新しい可用性グループに対して選択した内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="068c7-169">On the **Summary** page, review your choices for the new availability group.</span></span> <span data-ttu-id="068c7-170">変更が必要な場合は、 **[戻る]** をクリックして、該当するページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="068c7-170">To make a change, click **Previous** to return to the relevant page.</span></span> <span data-ttu-id="068c7-171">必要な変更を加えたら、 **[次へ]** をクリックして、 **[概要]** ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="068c7-171">After making the change, click **Next** to return to the **Summary** page.</span></span>  
  
     <span data-ttu-id="068c7-172">詳細については、「 [AlwaysOn 可用性グループウィザード&#41;&#40;概要ページ](summary-page-always-on-availability-group-wizards.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="068c7-172">For more information, see [Summary Page &#40;AlwaysOn Availability Group Wizards&#41;](summary-page-always-on-availability-group-wizards.md).</span></span>  
  
     <span data-ttu-id="068c7-173">選択内容に問題がなければ、[スクリプト] をクリックして、ウィザードが実行する手順のスクリプトを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="068c7-173">If you are satisfied with your selections, optionally click Script to create a script of the steps the wizard will execute.</span></span> <span data-ttu-id="068c7-174">新しい可用性グループを作成して構成するには、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="068c7-174">Then, to create and configure the new availability group, click **Finish**.</span></span>  
  
9. <span data-ttu-id="068c7-175">可用性グループの作成手順 (エンドポイントの構成、可用性グループの作成、グループへのセカンダリ レプリカの参加) の進行状況が、 **[進行状況]** ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="068c7-175">The **Progress** page displays the progress of the steps for creating the availability group (configuring endpoints, creating the availability group, and joining the secondary replica to the group).</span></span>  
  
     <span data-ttu-id="068c7-176">詳細については、「 [AlwaysOn 可用性グループウィザード&#41;&#40;[進行状況] ページ](progress-page-always-on-availability-group-wizards.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="068c7-176">For more information, see [Progress Page &#40;AlwaysOn Availability Group Wizards&#41;](progress-page-always-on-availability-group-wizards.md).</span></span>  
  
10. <span data-ttu-id="068c7-177">以上の手順が完了すると、 **[結果]** ページに各手順の結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="068c7-177">When these steps complete, the **Results** page displays the result of each step.</span></span> <span data-ttu-id="068c7-178">これらのすべての手順が成功した場合は、新しい可用性グループが完全に構成されます。</span><span class="sxs-lookup"><span data-stu-id="068c7-178">If all these steps succeed, the new availability group is completely configured.</span></span> <span data-ttu-id="068c7-179">手順のいずれかでエラーが発生した場合は、手動で構成を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="068c7-179">If any of the steps result in an error, you might need to manually complete the configuration.</span></span> <span data-ttu-id="068c7-180">特定のエラーの原因については、 **[結果]** 列の [エラー] リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="068c7-180">For information about the cause of a given error, click the associated "Error" link in the **Result** column.</span></span>  
  
     <span data-ttu-id="068c7-181">ウィザードでの作業が完了したら、 **[閉じる]** をクリックして終了します。</span><span class="sxs-lookup"><span data-stu-id="068c7-181">When the wizard completes, click **Close** to exit.</span></span>  
  
     <span data-ttu-id="068c7-182">詳細については、「[[結果] ページ &#40;AlwaysOn 可用性グループ ウィザード&#41;](results-page-always-on-availability-group-wizards.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="068c7-182">For more information, see [Results Page &#40;AlwaysOn Availability Group Wizards&#41;](results-page-always-on-availability-group-wizards.md).</span></span>  
  
11. <span data-ttu-id="068c7-183">すべてのセカンダリ データベースで初期データ同期が自動的に開始されない場合は、まだ参加していないセカンダリ データベースを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="068c7-183">If initial data synchronization was not automatically started on all of you secondary database, you need to configure any not-yet-joined secondary databases.</span></span> <span data-ttu-id="068c7-184">詳細については、「[AlwaysOn セカンダリ データベース上のデータ移動の開始 &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="068c7-184">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="068c7-185">関連タスク</span><span class="sxs-lookup"><span data-stu-id="068c7-185">Related Tasks</span></span>  
  
-   [<span data-ttu-id="068c7-186">可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="068c7-186">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="068c7-187">可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="068c7-187">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="068c7-188">参照</span><span class="sxs-lookup"><span data-stu-id="068c7-188">See Also</span></span>  
 <span data-ttu-id="068c7-189">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="068c7-189">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="068c7-190">[AlwaysOn 可用性グループ &#40;SQL Server の前提条件、制限事項、推奨事項&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="068c7-190">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="068c7-191">[可用性グループにデータベースを追加 &#40;SQL Server&#41;](availability-group-add-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="068c7-191">[Add a Database to an Availability Group &#40;SQL Server&#41;](availability-group-add-a-database.md) </span></span>  
 <span data-ttu-id="068c7-192">[AlwaysOn セカンダリデータベース &#40;SQL Server でのデータ移動の開始&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="068c7-192">[Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md) </span></span>  
 [<span data-ttu-id="068c7-193">可用性グループへのデータベースの追加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="068c7-193">Add a Database to an Availability Group &#40;SQL Server&#41;</span></span>](availability-group-add-a-database.md)  
  
  
