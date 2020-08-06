---
title: Azure のレプリカ追加ウィザードの使用 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.azurereplica.f1
ms.assetid: b89cc41b-07b4-49f3-82cc-bc42b2e793ae
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8f7ee9e80f0511fe23aebb887b15b5e8b7e9cabf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712381"
---
# <a name="use-the-add-azure-replica-wizard-sql-server"></a><span data-ttu-id="78f74-102">Azure のレプリカ追加ウィザードの使用 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="78f74-102">Use the Add Azure Replica Wizard (SQL Server)</span></span>
  <span data-ttu-id="78f74-103">Azure のレプリカ追加ウィザードを使用して、ハイブリッド IT で新しい Azure VM を作成し、新規または既存の AlwaysOn 可用性グループのセカンダリレプリカとして構成することができます。</span><span class="sxs-lookup"><span data-stu-id="78f74-103">Use the Add Azure Replica Wizard to help you create a new Azure VM in hybrid IT and configure it as a secondary replica for a new or existing AlwaysOn availability group.</span></span>  
  
-   <span data-ttu-id="78f74-104">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="78f74-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="78f74-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="78f74-105">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="78f74-106">Security</span><span class="sxs-lookup"><span data-stu-id="78f74-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="78f74-107">**レプリカを追加する方法:**  [Azure のレプリカ追加ウィザード (SQL Server Management Studio)](#SSMSProcedure)</span><span class="sxs-lookup"><span data-stu-id="78f74-107">**To add a replica, using:**  [Add Azure Replica Wizard (SQL Server Management Studio)](#SSMSProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="78f74-108">はじめに</span><span class="sxs-lookup"><span data-stu-id="78f74-108">Before You Begin</span></span>  
 <span data-ttu-id="78f74-109">可用性グループに可用性レプリカを追加したことがない場合は、「サーバーインスタンス」と「可用性グループとレプリカ」のセクション「 [AlwaysOn 可用性グループ &#40;SQL Server&#41;の前提条件、制限事項、推奨事項](prereqs-restrictions-recommendations-always-on-availability.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78f74-109">If you have never added any availability replica to an availability group, see the "Server instances" and "Availability groups and replicas" sections in [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="78f74-110">前提条件</span><span class="sxs-lookup"><span data-stu-id="78f74-110">Prerequisites</span></span>  
  
-   <span data-ttu-id="78f74-111">現在のプライマリ レプリカをホストするサーバー インスタンスに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="78f74-111">You must be connected to the server instance that hosts the current primary replica.</span></span>  
  
-   <span data-ttu-id="78f74-112">オンプレミスのサブネットに Azure とのサイト間 VPN があるハイブリッド IT 環境が必要です。</span><span class="sxs-lookup"><span data-stu-id="78f74-112">You must have a hybrid-IT environment where your on-premise subnet has a site-to-site VPN with Azure.</span></span> <span data-ttu-id="78f74-113">詳細については、「 [管理ポータルでのサイト間 VPN の構成](https://azure.microsoft.com/documentation/articles/vpn-gateway-site-to-site-create)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78f74-113">For more information, see [Configure a Site-to-Site VPN in the Management Portal](https://azure.microsoft.com/documentation/articles/vpn-gateway-site-to-site-create).</span></span>  
  
-   <span data-ttu-id="78f74-114">可用性グループに、内部設置型可用性レプリカが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="78f74-114">Your availability group must contain on-premise availability replicas.</span></span>  
  
-   <span data-ttu-id="78f74-115">可用性グループ リスナーに対するクライアントで、可用性グループが Azure レプリカにフェールオーバーした場合にリスナーとの接続を維持するには、インターネット接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="78f74-115">Clients to the availability group listener must have connectivity to the Internet if they want to maintain connectivity with the listener when the availability group is failed over to an Azure replica.</span></span>  
  
-   <span data-ttu-id="78f74-116">**初期データの完全同期を使用するための前提条件** ウィザードでのバックアップの作成およびバックアップへのアクセスには、ネットワーク共有を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78f74-116">**Prerequisites for using full initial data synchronization** You will need to specify a network share in order for the wizard to create and access backups.</span></span> <span data-ttu-id="78f74-117">プライマリ レプリカでは、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] の起動に使用するアカウントにネットワーク共有での読み取り/書き込みファイルシステム権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="78f74-117">For the primary replica, the account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must have read and write file-system permissions on a network share.</span></span> <span data-ttu-id="78f74-118">セカンダリ レプリカでは、アカウントは、ネットワーク共有に対する読み取り権限を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="78f74-118">For secondary replicas, the account must have read permission on the network share.</span></span>  
  
     <span data-ttu-id="78f74-119">ウィザードを使用して初期データの完全同期を実行できない場合は、セカンダリ データベースを手動で準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78f74-119">If you are unable to use the wizard to perform full initial data synchronization, you need to prepare your secondary databases manually.</span></span> <span data-ttu-id="78f74-120">これは、ウィザードの実行前でも実行後でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="78f74-120">You can do this before or after running the wizard.</span></span> <span data-ttu-id="78f74-121">詳細については、「 [可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)、または PowerShell を使用して、AlwaysOn 可用性グループにセカンダリ データベースを参加させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="78f74-121">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="78f74-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="78f74-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="78f74-123">Permissions</span><span class="sxs-lookup"><span data-stu-id="78f74-123">Permissions</span></span>  
 <span data-ttu-id="78f74-124">「 [Security](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md#Security)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78f74-124">See [Security](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md#Security)</span></span>  
  
##  <a name="using-the-add-azure-replica-wizard-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="78f74-125">Azure のレプリカ追加ウィザードの使用 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="78f74-125">Using the Add Azure Replica Wizard (SQL Server Management Studio)</span></span>  
 <span data-ttu-id="78f74-126">Azure のレプリカ追加ウィザードは、 [[レプリカの指定] ページ](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md)から起動できます。</span><span class="sxs-lookup"><span data-stu-id="78f74-126">The Add Azure Replica Wizard can be launched from the [Specify Replicas Page](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md).</span></span> <span data-ttu-id="78f74-127">このページを開くには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="78f74-127">There are two ways to reach this page:</span></span>  
  
-   [<span data-ttu-id="78f74-128">可用性グループ ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="78f74-128">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="78f74-129">可用性グループへのレプリカ追加ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="78f74-129">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
 <span data-ttu-id="78f74-130">Azure のレプリカ追加ウィザードを起動したら、次の手順を行います。</span><span class="sxs-lookup"><span data-stu-id="78f74-130">Once you have launched the Add Azure Replica Wizard, follow the steps below:</span></span>  
  
1.  <span data-ttu-id="78f74-131">まず、Azure サブスクリプションの管理証明書をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="78f74-131">First, download a management certificate for your Azure subscription.</span></span> <span data-ttu-id="78f74-132">**[ダウンロード]** をクリックして、サインイン ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="78f74-132">Click **Download** to open the sign-in page.</span></span>  
  
2.  <span data-ttu-id="78f74-133">サインインページで、Azure サブスクリプションにサインインします。</span><span class="sxs-lookup"><span data-stu-id="78f74-133">In the sign-in page, sign in to your Azure subscription.</span></span> <span data-ttu-id="78f74-134">サインインすると、ローカル コンピューターに管理証明書がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="78f74-134">Once you are signed in, the wizard installs a management certificate onto your local machine.</span></span> <span data-ttu-id="78f74-135">ウィザードを再度使用する場合は、この管理証明書が自動的に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="78f74-135">This management certificate is automatically loaded when you use this wizard again.</span></span> <span data-ttu-id="78f74-136">複数の管理証明書をダウンロードした場合は、 **[...]** ボタンをクリックして、使用する管理証明書を選択します。</span><span class="sxs-lookup"><span data-stu-id="78f74-136">If you have downloaded multiple management certificates, you can click the **...** button to select the one you want to use.</span></span>  
  
3.  <span data-ttu-id="78f74-137">次に、 **[接続]** をクリックしてサブスクリプションに接続します。</span><span class="sxs-lookup"><span data-stu-id="78f74-137">Next, connect to your subscription by clicking **Connect**.</span></span> <span data-ttu-id="78f74-138">接続すると、 **[仮想ネットワーク]** や **[仮想ネットワーク サブネット]** などの Azure のパラメーターがドロップダウン リストに設定されます。</span><span class="sxs-lookup"><span data-stu-id="78f74-138">Once you are connected, the drop-down lists are populated with your Azure parameters, such as **Virtual Network** and **Virtual Network Subnet**.</span></span>  
  
4.  <span data-ttu-id="78f74-139">新しいセカンダリ レプリカをホストする Azure VM の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="78f74-139">Specify the settings for the Azure VM that will host the new secondary replica:</span></span>  
  
     <span data-ttu-id="78f74-140">Image</span><span class="sxs-lookup"><span data-stu-id="78f74-140">Image</span></span>  
     <span data-ttu-id="78f74-141">Azure VM に使用する SQL Server イメージの名前</span><span class="sxs-lookup"><span data-stu-id="78f74-141">The name of the SQL Server image to use for the Azure VM</span></span>  
  
     <span data-ttu-id="78f74-142">[VM サイズ]</span><span class="sxs-lookup"><span data-stu-id="78f74-142">VM Size</span></span>  
     <span data-ttu-id="78f74-143">Azure VM のサイズ</span><span class="sxs-lookup"><span data-stu-id="78f74-143">The size of the Azure VM</span></span>  
  
     <span data-ttu-id="78f74-144">VM 名</span><span class="sxs-lookup"><span data-stu-id="78f74-144">VM Name</span></span>  
     <span data-ttu-id="78f74-145">Azure VM の DNS 名</span><span class="sxs-lookup"><span data-stu-id="78f74-145">The DNS name of the Azure VM</span></span>  
  
     <span data-ttu-id="78f74-146">[VM ユーザー名]</span><span class="sxs-lookup"><span data-stu-id="78f74-146">VM Username</span></span>  
     <span data-ttu-id="78f74-147">Azure VM の既定の管理者のユーザー名</span><span class="sxs-lookup"><span data-stu-id="78f74-147">The username of the default administrator for the Azure VM</span></span>  
  
     <span data-ttu-id="78f74-148">[VM 管理者パスワード] (および [パスワードの確認入力])</span><span class="sxs-lookup"><span data-stu-id="78f74-148">VM Administrator Password (and Confirm Password)</span></span>  
     <span data-ttu-id="78f74-149">Azure VM の既定の管理者のパスワード</span><span class="sxs-lookup"><span data-stu-id="78f74-149">The password for the default administrator for the Azure VM</span></span>  
  
     <span data-ttu-id="78f74-150">Virtual Network</span><span class="sxs-lookup"><span data-stu-id="78f74-150">Virtual Network</span></span>  
     <span data-ttu-id="78f74-151">Azure VM を配置する仮想ネットワーク</span><span class="sxs-lookup"><span data-stu-id="78f74-151">The virtual network in which to place the Azure VM</span></span>  
  
     <span data-ttu-id="78f74-152">[仮想ネットワーク サブネット]</span><span class="sxs-lookup"><span data-stu-id="78f74-152">Virtual Network Subnet</span></span>  
     <span data-ttu-id="78f74-153">Azure VM を配置する仮想ネットワーク サブネット</span><span class="sxs-lookup"><span data-stu-id="78f74-153">The virtual network subnet in which to place the Azure VM</span></span>  
  
     <span data-ttu-id="78f74-154">Domain</span><span class="sxs-lookup"><span data-stu-id="78f74-154">Domain</span></span>  
     <span data-ttu-id="78f74-155">Azure VM を参加させる Active Directory (AD) ドメイン</span><span class="sxs-lookup"><span data-stu-id="78f74-155">The Active Directory (AD) domain to join the Azure VM</span></span>  
  
     <span data-ttu-id="78f74-156">ドメイン ユーザー名</span><span class="sxs-lookup"><span data-stu-id="78f74-156">Domain Username</span></span>  
     <span data-ttu-id="78f74-157">Azure VM をドメインに参加させるために使用される AD ユーザー名</span><span class="sxs-lookup"><span data-stu-id="78f74-157">The AD username used to join the Azure VM to the domain</span></span>  
  
     <span data-ttu-id="78f74-158">Password</span><span class="sxs-lookup"><span data-stu-id="78f74-158">Password</span></span>  
     <span data-ttu-id="78f74-159">Azure VM をドメインに参加させるために使用されるパスワード</span><span class="sxs-lookup"><span data-stu-id="78f74-159">The password used to join the Azure VM to the domain</span></span>  
  
5.  <span data-ttu-id="78f74-160">**[OK]** をクリックして設定をコミットし、Azure のレプリカ追加ウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="78f74-160">Click **OK** to commit your settings and exit the Add Azure Replica Wizard.</span></span>  
  
6.  <span data-ttu-id="78f74-161">新しいレプリカの場合と同じように、 [[レプリカの指定] ページ](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md) で残りの構成手順を行います。</span><span class="sxs-lookup"><span data-stu-id="78f74-161">Continue with the rest of the configuration steps for [Specify Replicas Page](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md) as you do for any new replica.</span></span>  
  
     <span data-ttu-id="78f74-162">可用性グループウィザードまたは可用性グループへのレプリカ追加ウィザードを終了すると、構成プロセスは Azure 内のすべての操作を実行して新しい VM を作成し、AD ドメインに参加させ、それを Windows クラスターに追加して、AlwaysOn 高可用性を有効にし、新しいレプリカを可用性グループに追加します。</span><span class="sxs-lookup"><span data-stu-id="78f74-162">Once you are finished with the Availability Group Wizard or the Add Replica to Availability Group Wizard, the configuration process performs all operations in Azure to create the new VM, join it to the AD domain, add it to the Windows cluster, enable AlwaysOn High Availability, and add the new replica to the availability group.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="78f74-163">関連タスク</span><span class="sxs-lookup"><span data-stu-id="78f74-163">Related Tasks</span></span>  
  
-   [<span data-ttu-id="78f74-164">可用性グループへのセカンダリ レプリカの追加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="78f74-164">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="78f74-165">参照</span><span class="sxs-lookup"><span data-stu-id="78f74-165">See Also</span></span>  
 <span data-ttu-id="78f74-166">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="78f74-166">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="78f74-167">[AlwaysOn 可用性グループ &#40;SQL Server の前提条件、制限事項、推奨事項&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="78f74-167">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 [<span data-ttu-id="78f74-168">可用性グループへのセカンダリ レプリカの追加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="78f74-168">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
  
