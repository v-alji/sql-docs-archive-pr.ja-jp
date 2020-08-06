---
title: 可用性グループ リスナーの作成または構成 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.newaglistener.general.f1
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
- Availability Groups [SQL Server], client connectivity
ms.assetid: 2bc294f6-2312-4b6b-9478-2fb8a656e645
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2c74e92286eab4bc1be8f3f538d83d86f056cf01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743450"
---
# <a name="create-or-configure-an-availability-group-listener-sql-server"></a><span data-ttu-id="a3bfe-102">可用性グループ リスナーの作成または構成 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a3bfe-102">Create or Configure an Availability Group Listener (SQL Server)</span></span>
  <span data-ttu-id="a3bfe-103">このトピックでは、で、、または PowerShell を使用して、AlwaysOn 可用性グループの単一の*可用性グループリスナー*を作成または構成する方法について説明し [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../../includes/tsql-md.md)] [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-103">This topic describes how to create or configure a single *availability group listener* for an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a3bfe-104">可用性グループの最初の可用性グループ リスナーを作成するには、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、または [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell を使用することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-104">To create the first availability group listener of an availability group, we strongly recommend that you [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell.</span></span> <span data-ttu-id="a3bfe-105">必要な場合 (追加リスナーを作成する場合など) を除いて、WSFC クラスターでリスナーを直接作成することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-105">Avoid creating a listener directly in the WSFC cluster except when necessary, for example, to create an additional listener.</span></span>  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a3bfe-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="a3bfe-106">Before You Begin</span></span>  
  
###  <a name="does-a-listener-exist-for-this-availability-group-already"></a><a name="DoesListenerExist"></a> <span data-ttu-id="a3bfe-107">この可用性グループに既にリスナーが存在するか</span><span class="sxs-lookup"><span data-stu-id="a3bfe-107">Does a Listener Exist for this Availability Group Already?</span></span>  
 <span data-ttu-id="a3bfe-108">**可用性グループにリスナーが既に存在するかどうかを確認するには**</span><span class="sxs-lookup"><span data-stu-id="a3bfe-108">**To determine whether a listener already exists for the availability group**</span></span>  
  
-   [<span data-ttu-id="a3bfe-109">可用性グループ リスナーのプロパティの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a3bfe-109">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
> [!NOTE]  
>  <span data-ttu-id="a3bfe-110">リスナーが既に存在するときに追加リスナーを作成する場合は、このトピックの「 [可用性グループの追加のリスナーを作成するには (省略可能)](#CreateAdditionalListener)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-110">If a listener already exists and you want to create an additional listener, see [To Create An Additional Listener for an Availability Group (Optional)](#CreateAdditionalListener), later in this topic.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a3bfe-111">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="a3bfe-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="a3bfe-112">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]で、可用性グループに対して作成できるリスナーは 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-112">You can create only one listener per availability group through [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a3bfe-113">通常、それぞれの可用性グループで必要なリスナーは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-113">Typically, each availability group requires only one listener.</span></span> <span data-ttu-id="a3bfe-114">ただし、一部の顧客シナリオでは、1 つの可用性グループで複数のリスナーが必要です。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-114">However, some customer scenarios require multiple listeners for one availability group.</span></span>   <span data-ttu-id="a3bfe-115">SQL Server で 1 つのリスナーを作成した後、フェールオーバー クラスターの Windows PowerShell または WSFC フェールオーバー クラスター マネージャーを使用して、追加のリスナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-115">After creating a listener through SQL Server, you can use Windows PowerShell for failover clusters or the WSFC Failover Cluster Manager to create additional listeners.</span></span> <span data-ttu-id="a3bfe-116">詳細については、このトピックの後の「 [可用性グループの追加のリスナーを作成するには (省略可能)](#CreateAdditionalListener)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-116">For more information, see [To Create An Additional Listener for an Availability Group (Optional)](#CreateAdditionalListener), later in this topic.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="a3bfe-117">推奨事項</span><span class="sxs-lookup"><span data-stu-id="a3bfe-117">Recommendations</span></span>  
 <span data-ttu-id="a3bfe-118">複数のサブネットを構成する場合は、必須ではありませんが、静的 IP アドレスの使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-118">Using a static IP address is recommended, although not required, for multiple subnet configurations.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="a3bfe-119">前提条件</span><span class="sxs-lookup"><span data-stu-id="a3bfe-119">Prerequisites</span></span>  
  
-   <span data-ttu-id="a3bfe-120">プライマリ レプリカをホストするサーバー インスタンスに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-120">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
-   <span data-ttu-id="a3bfe-121">複数のサブネットにわたる可用性グループ リスナーを設定し、静的 IP アドレスを使用する場合は、リスナーを作成する可用性グループの可用性レプリカがホストされているすべてのサブネットの静的 IP アドレスを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-121">If you are setting up an availability group listener across multiple subnets and plan to use static IP addresses, you need to get the static IP address of every subnet that hosts an availability replica for the availability group for which you are creating the listener.</span></span> <span data-ttu-id="a3bfe-122">通常は、静的 IP アドレスをネットワーク管理者に問い合わせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-122">Usually, you will need to ask your network administrators for the static IP addresses.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a3bfe-123">初めてリスナーを作成する前に、「[AlwaysOn クライアント接続 &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md)」を読むことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-123">Before you create your first listener, we strongly recommend that you read [AlwaysOn Client Connectivity &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md).</span></span>  
  
###  <a name="requirements-for-the-dns-name-of-an-availability-group-listener"></a><a name="DNSnameReqs"></a> <span data-ttu-id="a3bfe-124">可用性グループ リスナーの DNS 名の要件</span><span class="sxs-lookup"><span data-stu-id="a3bfe-124">Requirements for the DNS Name of an Availability Group Listener</span></span>  
 <span data-ttu-id="a3bfe-125">各可用性グループ リスナーは、ドメインおよび NetBIOS 内で一意の DNS ホスト名を必要とします。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-125">Each availability group listener requires a DNS host name that is unique in the domain and in NetBIOS.</span></span> <span data-ttu-id="a3bfe-126">DNS 名は、文字列値です。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-126">The DNS name is a string value.</span></span> <span data-ttu-id="a3bfe-127">この名前には、英数字、ダッシュ (-)、およびハイフン (_) のみを任意の順序で含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-127">This name can contain only alphanumeric characters, dashes (-), and hyphens (_), in any order.</span></span> <span data-ttu-id="a3bfe-128">DNS ホスト名では大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-128">DNS host names are case insensitive.</span></span> <span data-ttu-id="a3bfe-129">最大長は 63 文字です。ただし、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で指定できる最大長は 15 文字です。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-129">The maximum length is 63 characters, however, in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], the maximum length you can specify is 15 characters.</span></span>  
  
 <span data-ttu-id="a3bfe-130">意味のある文字列を指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-130">We recommend that you specify a meaningful string.</span></span> <span data-ttu-id="a3bfe-131">たとえば、可用性グループの名前が `AG1`の場合は、 `ag1-listener`のような意味のある DNS ホスト名にします。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-131">For example, for an availability group named `AG1`, a meaningful DNS host name would be `ag1-listener`.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a3bfe-132">NetBIOS では、dns_name の最初の 15 文字のみが認識されます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-132">NetBIOS recognizes only the first 15 chars in the dns_name.</span></span> <span data-ttu-id="a3bfe-133">同じ Active Directory で制御されている 2 つの WSFC クラスターがあり、両方のクラスターで可用性グループ リスナーを作成しようとする場合、15 文字より長い名前を使用して、15 文字のプレフィックスが同一であると、仮想ネットワーク名リソースをオンラインにできなかったことを示すエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-133">If you have two WSFC clusters that are controlled by the same Active Directory and you try to create availability group listeners in both of clusters using names with more than 15 characters and an identical 15 character prefix, you will get an error reporting that the Virtual Network Name resource could not be brought online.</span></span> <span data-ttu-id="a3bfe-134">DNS 名のプレフィックスに対する名前付け規則の詳細については、「 [ドメイン名を割り当てる](https://technet.microsoft.com/library/cc731265\(WS.10\).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-134">For information about prefix naming rules for DNS names, see [Assigning Domain Names](https://technet.microsoft.com/library/cc731265\(WS.10\).aspx).</span></span>  
  
###  <a name="windows-permissions"></a><a name="WinPermissions"></a> <span data-ttu-id="a3bfe-135">Windows 権限</span><span class="sxs-lookup"><span data-stu-id="a3bfe-135">Windows Permissions</span></span>  
  
|<span data-ttu-id="a3bfe-136">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="a3bfe-136">Permissions</span></span>|<span data-ttu-id="a3bfe-137">Link</span><span class="sxs-lookup"><span data-stu-id="a3bfe-137">Link</span></span>|  
|-----------------|----------|  
|<span data-ttu-id="a3bfe-138">可用性グループをホストしている WSFC クラスターのクラスター オブジェクト名 (CNO) には、 **Create Computer objects** アクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-138">The cluster object name (CNO) of WSFC cluster that is hosting the availability group must have **Create Computer objects** permission.</span></span><br /><br /> <span data-ttu-id="a3bfe-139">Active Directory では、CNO は既定で **Create Computer objects** アクセス許可を明示的に持たず、仮想コンピューター オブジェクト (VCO) を最大で 10 個作成できます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-139">In Active Directory, a CNO by default does not have **Create Computer objects** permission explicitly and can create 10 virtual computer objects (VCOs).</span></span> <span data-ttu-id="a3bfe-140">VCO を 10 個作成した後、追加で VCO を作成しようとしても失敗します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-140">After 10 VCOs are created, the creation of additional VCOs will fail.</span></span> <span data-ttu-id="a3bfe-141">この問題は、WSFC クラスターの CNO に権限を明示的に与えることで回避できます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-141">You can avoid this by granting the permission explicitly to the WSFC cluster's CNO.</span></span> <span data-ttu-id="a3bfe-142">削除した可用性グループの VCO は Active Directory 内で自動的に削除されず、手動で削除しない限り、VCO の 10 個の既定の制限の対象としてカウントされます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-142">Note that VCOs for availability groups that you have deleted are not automatically deleted in Active Directory and count against your 10 VCO default limit unless they are manually deleted.</span></span><br /><br /> <span data-ttu-id="a3bfe-143">注:組織によっては、**Create Computer objects** 権限を個別のユーザー アカウントに付与することがセキュリティ ポリシーで禁止されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-143">Note: In some organizations, the security policy prohibits granting **Create Computer objects** permission to individual user accounts.</span></span>|<span data-ttu-id="a3bfe-144">*クラスターをインストールするユーザーのアカウントを構成する手順*: 「[フェールオーバー クラスター ステップ バイ ステップ ガイド:Active Directory のアカウントの構成](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_installer)」</span><span class="sxs-lookup"><span data-stu-id="a3bfe-144">*Steps for configuring the account for the person who installs the cluster* in [Failover Cluster Step-by-Step Guide: Configuring Accounts in Active Directory](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_installer)</span></span><br /><br /> <span data-ttu-id="a3bfe-145">*クラスター名アカウントを事前設定する手順:* 「[フェールオーバー クラスター ステップ バイ ステップ ガイド:Active Directory のアカウントの構成](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_precreating)」</span><span class="sxs-lookup"><span data-stu-id="a3bfe-145">*Steps for prestaging the cluster name account* in [Failover Cluster Step-by-Step Guide: Configuring Accounts in Active Directory](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_precreating)</span></span>|  
|<span data-ttu-id="a3bfe-146">リスナーの仮想ネットワーク名にコンピューター アカウントを事前設定する必要がある場合は、 **Account Operator** グループのメンバーシップが必要です。または、ドメイン管理者に依頼する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-146">If your organization requires that you prestage the computer account for a listener virtual network name, you will need membership in the **Account Operator** group or your domain administrator's assistance.</span></span><br /><br /> <span data-ttu-id="a3bfe-147">ヒント: 一般的には、リスナーの仮想ネットワーク名にコンピューター アカウントを事前設定しないことが最も簡単です。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-147">Tip: Generally, it is simplest not to prestage the computer account for a listener virtual network name.</span></span> <span data-ttu-id="a3bfe-148">可能な場合は、WSFC の高可用性ウィザードを実行する際にアカウントが自動的に作成および構成されるように構成します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-148">If you can, let the account to be created and configured automatically when you run the WSFC High Availability wizard.</span></span>|<span data-ttu-id="a3bfe-149">*クラスター化されたサービスまたはアプリケーションのアカウントを事前設定する手順:* 「 [フェールオーバー クラスター ステップ バイ ステップ ガイド: Active Directory のアカウントの構成](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_precreating2)」</span><span class="sxs-lookup"><span data-stu-id="a3bfe-149">*Steps for prestaging an account for a clustered service or application* in [Failover Cluster Step-by-Step Guide: Configuring Accounts in Active Directory](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_precreating2).</span></span>|  
  
###  <a name="sql-server-permissions"></a><a name="SqlPermissions"></a> <span data-ttu-id="a3bfe-150">SQL Server 権限</span><span class="sxs-lookup"><span data-stu-id="a3bfe-150">SQL Server Permissions</span></span>  
  
|<span data-ttu-id="a3bfe-151">タスク</span><span class="sxs-lookup"><span data-stu-id="a3bfe-151">Task</span></span>|<span data-ttu-id="a3bfe-152">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="a3bfe-152">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="a3bfe-153">可用性グループ リスナーを作成するには</span><span class="sxs-lookup"><span data-stu-id="a3bfe-153">To create an availability group listener</span></span>|<span data-ttu-id="a3bfe-154">**sysadmin** 固定サーバー ロールのメンバーシップと、CREATE AVAILABILITY GROUP サーバー権限、ALTER ANY AVAILABILITY GROUP 権限、CONTROL SERVER 権限のいずれかが必要です。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-154">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
|<span data-ttu-id="a3bfe-155">既存の可用性グループ リスナーを変更するには</span><span class="sxs-lookup"><span data-stu-id="a3bfe-155">To modify an existing availability group listener</span></span>|<span data-ttu-id="a3bfe-156">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-156">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a3bfe-157">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="a3bfe-157">Using SQL Server Management Studio</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="a3bfe-158">[新しい可用性グループ ウィザード](use-the-new-availability-group-dialog-box-sql-server-management-studio.md) は、新しい可用性グループに対するリスナーの作成をサポートします。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-158">The [New Availability Group wizard](use-the-new-availability-group-dialog-box-sql-server-management-studio.md) supports creation of the listener for a new availability group.</span></span>  
  
 <span data-ttu-id="a3bfe-159">**可用性グループ リスナーを作成または構成するには**</span><span class="sxs-lookup"><span data-stu-id="a3bfe-159">**To create or configure an availability group listener**</span></span>  
  
1.  <span data-ttu-id="a3bfe-160">オブジェクト エクスプローラーで、可用性グループのプライマリ レプリカをホストするサーバー インスタンスに接続し、サーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-160">In Object Explorer, connect to the server instance that hosts the primary replica of the availability group, and click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="a3bfe-161">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-161">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="a3bfe-162">リスナーを構成する可用性グループをクリックし、次のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-162">Click the availability group whose listener you want to configure, and choose one of the following alternatives:</span></span>  
  
    -   <span data-ttu-id="a3bfe-163">リスナーを作成するには、 **[可用性グループ リスナー]** ノードを右クリックし、 **[新しいリスナー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-163">To create a listener, right-click the **Availability group Listeners** node, and select the **New Listener** command.</span></span> <span data-ttu-id="a3bfe-164">これにより、 **[新しい可用性グループ リスナー]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-164">This opens the **New Availability Group Listener** dialog box.</span></span> <span data-ttu-id="a3bfe-165">詳細については、このトピックの「 [[新しい可用性グループ リスナー] (ダイアログ ボックス)](#AddAgListenerDialog)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-165">For more information, see [Add Availability Group Listener (Dialog Box)](#AddAgListenerDialog), later in this topic.</span></span>  
  
    -   <span data-ttu-id="a3bfe-166">既存のリスナーのポート番号を変更するには、 **[可用性グループ リスナー]** ノードを展開し、リスナーを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-166">To change the port number of an existing listener, expand the **Availability group Listeners** node, right-click the listener, and select the **Properties** command.</span></span> <span data-ttu-id="a3bfe-167">**[ポート]** フィールドに新しいポート番号を入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-167">Enter the new port number into the **Port** field, and click **OK**.</span></span>  
  
###  <a name="new-availability-group-listener-dialog-box"></a><a name="AddAgListenerDialog"></a> <span data-ttu-id="a3bfe-168">[新しい可用性グループ リスナー] (ダイアログ ボックス)</span><span class="sxs-lookup"><span data-stu-id="a3bfe-168">New Availability Group Listener (Dialog Box)</span></span>  
 <span data-ttu-id="a3bfe-169">**[リスナーの DNS 名]**</span><span class="sxs-lookup"><span data-stu-id="a3bfe-169">**Listener DNS Name**</span></span>  
 <span data-ttu-id="a3bfe-170">可用性グループ リスナーの DNS ホスト名を指定します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-170">Specifies the DNS host name of the availability group listener.</span></span> <span data-ttu-id="a3bfe-171">DNS 名は、ドメインおよび NetBIOS 内で一意であることが必要な文字列です。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-171">The DNS name is a string  must be unique in the domain and in NetBIOS.</span></span> <span data-ttu-id="a3bfe-172">この名前には、英数字、ダッシュ (-)、およびハイフン (_) のみを任意の順序で含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-172">This name can contain only alphanumeric characters, dashes (-), and hyphens (_), in any order.</span></span> <span data-ttu-id="a3bfe-173">DNS ホスト名では大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-173">DNS host names are case insensitive.</span></span> <span data-ttu-id="a3bfe-174">最大長は 15 文字です。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-174">The maximum length is 15 characters.</span></span>  
  
 <span data-ttu-id="a3bfe-175">詳細については、このトピックの前の「 [可用性グループ リスナーの DNS 名の要件](#DNSnameReqs)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-175">For more information, see [Requirements for the DNS Name of an Availability Group Listener](#DNSnameReqs), earlier in this topic.</span></span>  
  
 <span data-ttu-id="a3bfe-176">**[ポート]**</span><span class="sxs-lookup"><span data-stu-id="a3bfe-176">**Port**</span></span>  
 <span data-ttu-id="a3bfe-177">このリスナーで使用される TCP ポート。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-177">The TPC port used by this listener.</span></span>  
  
 <span data-ttu-id="a3bfe-178">**[ネットワーク モード]**</span><span class="sxs-lookup"><span data-stu-id="a3bfe-178">**Network Mode**</span></span>  
 <span data-ttu-id="a3bfe-179">リスナーで使用される TCP プロトコルを指定します。次のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-179">Indicates the TCP protocol used by the listener, one of:</span></span>  
  
 <span data-ttu-id="a3bfe-180">**[DHCP]**</span><span class="sxs-lookup"><span data-stu-id="a3bfe-180">**DHCP**</span></span>  
 <span data-ttu-id="a3bfe-181">リスナーは、動的ホスト構成プロトコル (DHCP) を実行しているサーバーによって割り当てられる動的 IP アドレスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-181">The listener will us a dynamic IP address that is assigned by a server running the Dynamic Host Configuration Protocol (DHCP).</span></span> <span data-ttu-id="a3bfe-182">DHCP は、単一のサブネットに制限されます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-182">DHCP is limited to a single subnet.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a3bfe-183">運用環境での DHCP の使用はお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-183">We do not recommend DHCP in production environment.</span></span> <span data-ttu-id="a3bfe-184">ダウンタイムが発生して DHCP IP のリース期限が切れると、リスナーの DNS 名に関連付けられている新しい DHCP のネットワーク IP アドレスの登録に余分な時間がかかり、クライアント接続に影響が及びます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-184">If there is a down time and the DHCP IP lease expires, extra time is required to register the new DHCP network IP address that is associated with the listener DNS name and impact the client connectivity.</span></span> <span data-ttu-id="a3bfe-185">ただし、開発環境とテスト環境を設定して可用性グループの基本機能を確認する場合や、アプリケーションとの統合の場合には DHCP が適しています。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-185">However, DHCP is good for setting up your development and testing environment to verify basic functions of availability groups and for integration with your applications.</span></span>  
  
 <span data-ttu-id="a3bfe-186">**[静的 IP]**</span><span class="sxs-lookup"><span data-stu-id="a3bfe-186">**Static IP**</span></span>  
 <span data-ttu-id="a3bfe-187">リスナーは、1 つまたは複数の静的 IP アドレスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-187">The listener will use one or more static IP addresses.</span></span> <span data-ttu-id="a3bfe-188">必要に応じて追加の IP アドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-188">Additional IP addresses are optional.</span></span> <span data-ttu-id="a3bfe-189">複数のサブネットにわたる可用性グループ リスナーを作成するには、各サブネットのリスナー構成に静的 IP アドレスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-189">To create an availability group listener across multiple subnets, for each subnet you must specify a static IP address in the listener configuration.</span></span> <span data-ttu-id="a3bfe-190">これらの静的 IP アドレスを取得するには、ネットワーク管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-190">Contact your network administrator to get these static IP addresses.</span></span>  
  
 <span data-ttu-id="a3bfe-191">**[静的 IP]** を選択した場合、 **[ネットワーク モード]** フィールドの下にサブネット グリッドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-191">If you select **Static IP** a subnet grid appears below the **Network Mode** field.</span></span> <span data-ttu-id="a3bfe-192">このグリッドに、この可用性グループ リスナーによってアクセスできる各サブネットについての情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-192">This grid displays information about each subnet that can be accessed by this availability group listener.</span></span> <span data-ttu-id="a3bfe-193">このグリッドは、 **[追加]** をクリックして静的 IP アドレスを追加するまでは空です。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-193">This grid is empty until you add a static IP address by clicking **Add**.</span></span>  
  
 <span data-ttu-id="a3bfe-194">次の列で構成されます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-194">The columns are as follows:</span></span>  
  
 <span data-ttu-id="a3bfe-195">**サブネット**</span><span class="sxs-lookup"><span data-stu-id="a3bfe-195">**Subnet**</span></span>  
 <span data-ttu-id="a3bfe-196">可用性グループ リスナーに追加される各サブネットの識別子が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-196">Displays the identifier of each subnet that you add to the availability group listener.</span></span>  
  
 <span data-ttu-id="a3bfe-197">**IP アドレス**</span><span class="sxs-lookup"><span data-stu-id="a3bfe-197">**IP Address**</span></span>  
 <span data-ttu-id="a3bfe-198">特定のサブネットの IP アドレスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-198">Displays the IP address of a given subnet.</span></span>  <span data-ttu-id="a3bfe-199">サブネットの IP アドレスには、IPv4 アドレスまたは IPv6 アドレスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-199">For a given subnet, the IP address is either an IPv4 address or an IPv6 address.</span></span>  
  
 <span data-ttu-id="a3bfe-200">**追加**</span><span class="sxs-lookup"><span data-stu-id="a3bfe-200">**Add**</span></span>  
 <span data-ttu-id="a3bfe-201">選択したサブネットまたはこのリスナーの別のサブネットに静的 IP アドレスを追加する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-201">Click to add to add a static IP address to a selected subnet or to another subnet for this listener.</span></span> <span data-ttu-id="a3bfe-202">クリックすると、 **[IP アドレスの追加]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-202">This opens the **Add IP Address** dialog box.</span></span> <span data-ttu-id="a3bfe-203">詳細については、「[[IP アドレスの追加] ダイアログ ボックス &#40;SQL Server Management Studio&#41;](add-ip-address-dialog-box-sql-server-management-studio.md)」ヘルプ トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-203">For more information, see the [Add IP Address Dialog Box &#40;SQL Server Management Studio&#41;](add-ip-address-dialog-box-sql-server-management-studio.md) help topic.</span></span>  
  
 <span data-ttu-id="a3bfe-204">**Remove**</span><span class="sxs-lookup"><span data-stu-id="a3bfe-204">**Remove**</span></span>  
 <span data-ttu-id="a3bfe-205">選択したサブネットをこのリスナーから削除する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-205">Click to remove the selected subnet from this listener.</span></span>  
  
 <span data-ttu-id="a3bfe-206">**[OK]**</span><span class="sxs-lookup"><span data-stu-id="a3bfe-206">**OK**</span></span>  
 <span data-ttu-id="a3bfe-207">指定した可用性グループ リスナーを作成する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-207">Click to create the specified availability group listener.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a3bfe-208">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="a3bfe-208">Using Transact-SQL</span></span>  

### <a name="to-create-or-configure-an-availability-group-listener"></a><span data-ttu-id="a3bfe-209">可用性グループ リスナーを作成または構成するには</span><span class="sxs-lookup"><span data-stu-id="a3bfe-209">To create or configure an availability group listener</span></span>
  
1.  <span data-ttu-id="a3bfe-210">プライマリ レプリカをホストするサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-210">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="a3bfe-211">[CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql) ステートメントの LISTENER オプションまたは [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) ステートメントの ADD LISTENER オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-211">Use the LISTENER option of the [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql) statement or the ADD LISTENER option of the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement.</span></span>  
  
     <span data-ttu-id="a3bfe-212">次の例では、可用性グループ リスナーを `MyAg2`という名前の既存の可用性グループに追加します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-212">The following example adds an availability group listener to an existing availability group named `MyAg2`.</span></span> <span data-ttu-id="a3bfe-213">このリスナーには、一意の DNS 名 `MyAg2ListenerIvP6`を指定します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-213">A unique DNS name, `MyAg2ListenerIvP6`, is specified for this listener.</span></span> <span data-ttu-id="a3bfe-214">2 つのレプリカが異なるサブネット上に存在するため、(推奨されるように) リスナーで静的 IP アドレスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-214">The two replicas are on different subnets, so , as recommended, the listener uses static IP addresses.</span></span> <span data-ttu-id="a3bfe-215">WITH IP 句には、2 つの可用性レプリカについて、それぞれ IPv6 形式の静的 IP アドレス ( `2001:4898:f0:f00f::cf3c and 2001:4898:e0:f213::4ce2`) を指定します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-215">For each of the two availability replicas, the WITH IP clause specifies a static IP address, `2001:4898:f0:f00f::cf3c and 2001:4898:e0:f213::4ce2`, which use the IPv6 format.</span></span> <span data-ttu-id="a3bfe-216">また、この例では、オプションの PORT 引数を使用して、 `60173` をリスナー ポートとして指定しています。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-216">This example also specifies uses the optional PORT argument to specify port `60173` as the listener port.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAg2   
          ADD LISTENER 'MyAg2ListenerIvP6' ( WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , PORT = 60173 );   
    GO  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="a3bfe-217">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="a3bfe-217">Using PowerShell</span></span>  

### <a name="to-create-or-configure-an-availability-group-listener"></a><span data-ttu-id="a3bfe-218">可用性グループ リスナーを作成または構成するには</span><span class="sxs-lookup"><span data-stu-id="a3bfe-218">To create or configure an availability group listener</span></span> 
  
1.  <span data-ttu-id="a3bfe-219">プライマリ レプリカをホストするサーバー インスタンスにディレクトリを変更 (`cd`) します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-219">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="a3bfe-220">可用性グループ リスナーを作成または変更するには、次のコマンドレットのいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-220">To create or modify an availability group listener use one of the following cmdlets:</span></span>  
  
     `New-SqlAvailabilityGroupListener`  
     <span data-ttu-id="a3bfe-221">新しい可用性グループ リスナーを作成して、既存の可用性グループにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-221">Creates a new availability group listener and attaches it to an existing availability group.</span></span>  
  
     <span data-ttu-id="a3bfe-222">たとえば、次の `New-SqlAvailabilityGroupListener` コマンドは、可用性グループ `MyListener` に対し、`MyAg` という名前の可用性グループ リスナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-222">For example, the following `New-SqlAvailabilityGroupListener` command creates an availability group listener named `MyListener` for the availability group `MyAg`.</span></span> <span data-ttu-id="a3bfe-223">このリスナーは、`-StaticIp` パラメーターに渡された IPv4 アドレスを仮想 IP アドレスとして使用します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-223">This listener will use the IPv4 address passed to the `-StaticIp` parameter as its virtual IP address.</span></span>  
  
    ```powershell
    New-SqlAvailabilityGroupListener -Name MyListener `
    -StaticIp '192.168.3.1/255.255.252.0' `
    -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg
    ```  
  
     `Set-SqlAvailabilityGroupListener`  
     <span data-ttu-id="a3bfe-224">既存の可用性グループ リスナーのポート設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-224">Modifies the port setting on an existing availability group listener.</span></span>  
  
     <span data-ttu-id="a3bfe-225">たとえば、次の `Set-SqlAvailabilityGroupListener` コマンドは、`MyListener` という名前の可用性グループ リスナーのポート番号を `1535` に設定します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-225">For example, the following `Set-SqlAvailabilityGroupListener` command sets the port number for the availability group listener named `MyListener` to `1535`.</span></span> <span data-ttu-id="a3bfe-226">このポートは、リスナーへの接続をリッスンするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-226">This port is used to listen for connections to the listener.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityGroupListener -Port 1535 `
    -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AGListeners\MyListener  
    ```  
  
     `Add-SqlAGListenerstaticIp`  
     <span data-ttu-id="a3bfe-227">既存の可用性グループ リスナー構成に静的 IP アドレスを追加します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-227">Adds a static IP address to an existing availability group listener configuration.</span></span> <span data-ttu-id="a3bfe-228">IP アドレスには、サブネットを含む IPv4 アドレス、または IPv6 アドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-228">The IP address can be an IPv4 address with subnet, or an IPv6 address.</span></span>  
  
     <span data-ttu-id="a3bfe-229">たとえば、次の `Add-SqlAGListenerstaticIp` コマンドは、可用性グループ `MyListener` の可用性グループ リスナー `MyAg` に静的 IPv4 アドレスを追加します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-229">For example, the following `Add-SqlAGListenerstaticIp` command adds a static IPv4 address to the availability group listener `MyListener` on the availability group `MyAg`.</span></span> <span data-ttu-id="a3bfe-230">この IPv6 アドレスは、サブネット `255.255.252.0`でリスナーの仮想 IP アドレスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-230">This IPv6 address serves as the virtual IP address of the listener on the subnet `255.255.252.0`.</span></span> <span data-ttu-id="a3bfe-231">可用性グループが複数のサブネットにまたがっている場合は、各サブネットの静的 IP アドレスをリスナーに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-231">If the availability group spans multiple subnets, you should add a static IP address for each subnet to the listener.</span></span>  
  
    ```powershell
    $path = "SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AGListeners\ MyListener" `
    Add-SqlAGListenerstaticIp -Path $path `
    -StaticIp "2001:0db8:85a3:0000:0000:8a2e:0370:7334"  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="a3bfe-232">コマンドレットの構文を表示するには、PowerShell 環境で**get-help**コマンドレットを使用し [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-232">To view the syntax of a cmdlet, use the **Get-Help**  cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="a3bfe-233">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-233">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="a3bfe-234">SQL Server PowerShell プロバイダーを設定して使用する方法については、「 [SQL Server PowerShell プロバイダー](../../../powershell/sql-server-powershell-provider.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-234">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>
  
## <a name="troubleshooting"></a><span data-ttu-id="a3bfe-235">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="a3bfe-235">Troubleshooting</span></span>  
  
###  <a name="failure-to-create-an-availability-group-listener-because-of-active-directory-quotas"></a><a name="ADQuotas"></a><span data-ttu-id="a3bfe-236">Active Directory クォータが原因で可用性グループリスナーを作成できない</span><span class="sxs-lookup"><span data-stu-id="a3bfe-236">Failure to Create An Availability Group Listener Because of Active Directory Quotas</span></span>  
 <span data-ttu-id="a3bfe-237">新しい可用性グループ リスナーの作成は、参加しているクラスター ノード マシン アカウントの Active Directory クォータに達したため、失敗する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-237">The creation of a new availability group listener may fail upon creation because you have reached an Active Directory quota for the participating cluster node machine account.</span></span>  <span data-ttu-id="a3bfe-238">詳細については、次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-238">For more information, see the following articles:</span></span>  
  
-   [<span data-ttu-id="a3bfe-239">HYPERLINK " https://support.microsoft.com/kb/307532 " コンピューターオブジェクトが変更されたときにクラスターサービスアカウントのトラブルシューティングを行う方法</span><span class="sxs-lookup"><span data-stu-id="a3bfe-239">HYPERLINK "https://support.microsoft.com/kb/307532" How to Troubleshoot the Cluster Service Account When It Modifies Computer Objects</span></span>](https://support.microsoft.com/kb/307532)  
  
-   <span data-ttu-id="a3bfe-240">[HYPERLINK " https://technet.microsoft.com/library/cc904295(WS.10).aspx " Active Directory クォータ](https://technet.microsoft.com/library/cc904295\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a3bfe-240">[HYPERLINK "https://technet.microsoft.com/library/cc904295(WS.10).aspx" Active Directory Quotas](https://technet.microsoft.com/library/cc904295\(WS.10\).aspx)</span></span>  
  
##  <a name="follow-up-after-creating-an-availability-group-listener"></a><a name="FollowUp"></a> <span data-ttu-id="a3bfe-241">補足情報: 可用性グループ リスナーの作成後</span><span class="sxs-lookup"><span data-stu-id="a3bfe-241">Follow-up: After Creating an Availability Group Listener</span></span>  
  
###  <a name="multisubnetfailover-keyword-and-associated-features"></a><a name="MultiSubnetFailover"></a><span data-ttu-id="a3bfe-242">MultiSubnetFailover キーワードと関連機能</span><span class="sxs-lookup"><span data-stu-id="a3bfe-242">MultiSubnetFailover Keyword and Associated Features</span></span>  
 <span data-ttu-id="a3bfe-243">`MultiSubnetFailover` は、SQL Server 2012 の AlwaysOn 可用性グループおよび AlwaysOn フェールオーバー クラスター インスタンスに対して高速フェールオーバーを有効にするために使用する新しい接続文字列キーワードです。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-243">`MultiSubnetFailover` is a new connection string keyword used to enable faster failover with AlwaysOn Availability Groups and AlwaysOn Failover Cluster Instances in SQL Server 2012.</span></span> <span data-ttu-id="a3bfe-244">接続文字列で `MultiSubnetFailover=True` が設定されていると、次の 3 つのサブ機能が有効になります。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-244">The following three sub-features are enabled when `MultiSubnetFailover=True` is set in connection string:</span></span>  
  
-   <span data-ttu-id="a3bfe-245">AlwaysOn 可用性グループまたはフェールオーバー クラスター インスタンスに対する複数サブネット リスナーへのより高速なマルチサブネット フェールオーバー。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-245">Faster multi-subnet failover to a multi-subnet listener for an AlwaysOn Availability Group or Failover Cluster Instances.</span></span>  
  
-   <span data-ttu-id="a3bfe-246">AlwaysOn 可用性グループまたはフェールオーバー クラスター インスタンスの単一サブネット リスナーへのより高速な単一サブネット フェールオーバー。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-246">Faster single subnet failover to a single subnet listener for an AlwaysOn Availability Group or Failover Cluster Instances.</span></span>  
  
    -   <span data-ttu-id="a3bfe-247">この機能は、単一のサブネット内に単一の IP を持つリスナーに接続する場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-247">This feature is used when connecting to a listener that has a single IP in a single subnet.</span></span> <span data-ttu-id="a3bfe-248">TCP 接続の再試行をより積極的に実行して、単一サブネット フェールオーバーを高速化します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-248">This performs more aggressive TCP connection retries to speed up single subnet failovers.</span></span>  
  
-   <span data-ttu-id="a3bfe-249">マルチサブネット AlwaysOn フェールオーバー クラスター インスタンスへの名前付きインスタンスの解決。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-249">Named instance resolution to a multi-subnet AlwaysOn Failover Cluster Instance.</span></span>  
  
    -   <span data-ttu-id="a3bfe-250">複数サブネット エンドポイントを持つ AlwaysOn フェールオーバー クラスター インスタンスの名前付きインスタンス解決サポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-250">This is to add named instance resolution support for an AlwaysOn Failover Cluster Instances with multiple subnet endpoints.</span></span>  
  
 <span data-ttu-id="a3bfe-251">**.NET Framework 3.5 および OLEDB で MultiSubnetFailover=True はサポートされない**</span><span class="sxs-lookup"><span data-stu-id="a3bfe-251">**MultiSubnetFailover=True Not Supported by NET Framework 3.5 or OLEDB**</span></span>  
  
 <span data-ttu-id="a3bfe-252">**問題:** 異なるサブネットからの複数の IP アドレスに応じて、可用性グループまたはフェールオーバークラスターインスタンスにリスナー名 (WSFC クラスターマネージャーのネットワーク名またはクライアントアクセスポイントと呼ばれる) がある場合、.NET Framework 3.5 SP1 または SQL Native Client 11.0 OLEDB で ADO.NET を使用していると、可用性グループリスナーへのクライアント接続要求の50% が接続タイムアウトに達します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-252">**Issue:** If your Availability Group or Failover Cluster Instance has a listener name (known as the network name or Client Access Point in the WSFC Cluster Manager) depending on multiple IP addresses from different subnets, and you are using either ADO.NET with .NET Framework 3.5SP1 or SQL Native Client 11.0 OLEDB, potentially 50% of your client-connection requests to the availability group listener will hit a connection timeout.</span></span>  
  
 <span data-ttu-id="a3bfe-253">**回避策:** 次のいずれかのタスクを実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-253">**Workarounds:** We recommend that you do one of the following tasks.</span></span>  
  
-   <span data-ttu-id="a3bfe-254">クラスター リソースを操作する権限がない場合は、接続タイムアウトを 30 秒に設定します (この値は結果として、20 秒の TCP タイムアウトと 10 秒のバッファーになります)。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-254">If do not have the permission to manipulate cluster resources, change your connection timeout to 30 seconds (this value results in a 20-second TCP timeout period plus a 10-second buffer).</span></span>  
  
     <span data-ttu-id="a3bfe-255">**長所:** :クロスサブネット フェールオーバーが発生した場合、クライアントの復旧時間が短くなります。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-255">**Pros**: If a cross-subnet failover occurs, client recovery time is short.</span></span>  
  
     <span data-ttu-id="a3bfe-256">**短所**:半数のクライアント接続に 20 秒以上要します</span><span class="sxs-lookup"><span data-stu-id="a3bfe-256">**Cons**: Half of the client connections will take more than 20 seconds</span></span>  
  
-   <span data-ttu-id="a3bfe-257">クラスター リソースを操作する権限がある場合は、可用性グループ リスナーのネットワーク名を `RegisterAllProvidersIP=0`に設定する方法をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-257">If you have the permission to manipulate cluster resources, the more recommended approach is to set the network name of your availability group listener to `RegisterAllProvidersIP=0`.</span></span> <span data-ttu-id="a3bfe-258">詳細については、このセクションの「RegisterAllProvidersIP の設定」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-258">For more information, see "RegisterAllProvidersIP Setting" later in this section.</span></span>  
  
     <span data-ttu-id="a3bfe-259">**長所:** クライアント接続のタイムアウト値を大きくする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-259">**Pros:** You do not need to increase your client-connection timeout value.</span></span>  
  
     <span data-ttu-id="a3bfe-260">**短所:** クロスサブネットフェールオーバーが発生した場合、 `HostRecordTTL` 設定とクロスサイト DNS/AD レプリケーションスケジュールの設定によっては、クライアントの復旧時間が15分以上になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-260">**Cons:** If a cross-subnet failover occurs, the client recovery time could be 15 minutes or longer, depending on your `HostRecordTTL` setting and the setting of your cross-site DNS/AD replication schedule.</span></span>  
  
###  <a name="registerallprovidersip-setting"></a><a name="RegisterAllProvidersIP"></a><span data-ttu-id="a3bfe-261">RegisterAllProvidersIP の設定</span><span class="sxs-lookup"><span data-stu-id="a3bfe-261">RegisterAllProvidersIP Setting</span></span>  
 <span data-ttu-id="a3bfe-262">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)]、または PowerShell を使用して可用性グループ リスナーを作成すると、WSFC にクライアント アクセス ポイントが作成され、その `RegisterAllProvidersIP` プロパティが 1 (true) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-262">When you use [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell to create an availability group listener, the Client Access Point is created in WSFC with the `RegisterAllProvidersIP` property set to 1 (true).</span></span> <span data-ttu-id="a3bfe-263">このプロパティ値の効果は、次に示すように、クライアント接続文字列によって異なります。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-263">The effect of this property value depends on the client connection string, as follows:</span></span>  
  
-   <span data-ttu-id="a3bfe-264">`MultiSubnetFailover` を true に設定する接続文字列</span><span class="sxs-lookup"><span data-stu-id="a3bfe-264">Connection strings that set `MultiSubnetFailover` to true</span></span>  
  
     [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]<span data-ttu-id="a3bfe-265">`RegisterAllProvidersIP`クライアントの接続文字列がを指定しているクライアントのフェールオーバー後の再接続時間を短縮するために、プロパティを1に設定し `MultiSubnetFailover = True` ます (推奨)。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-265">sets the  `RegisterAllProvidersIP` property to 1 in order to reduce re-connection time after a failover for clients whose client connection strings specify `MultiSubnetFailover = True`, as recommended.</span></span> <span data-ttu-id="a3bfe-266">リスナーのマルチサブネット機能を活用するには、クライアントに `MultiSubnetFailover` キーワードをサポートするデータ プロバイダーが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-266">Note that to take advantage of the listener multi-subnet feature, your clients might require a data provider that supports the `MultiSubnetFailover` keyword.</span></span> <span data-ttu-id="a3bfe-267">マルチサブネット フェールオーバーのドライバー サポートについては、「[AlwaysOn クライアント接続 &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-267">For information about driver support for multi-subnet failover, see [AlwaysOn Client Connectivity &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md).</span></span>  
  
     <span data-ttu-id="a3bfe-268">マルチサブネット クラスタリングについては、「 [SQL Server マルチサブネット クラスタリング &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md)を作成または構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-268">For information about multi-subnet clustering, see [SQL Server Multi-Subnet Clustering &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md).</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="a3bfe-269">`RegisterAllProvidersIP = 1`のときに、WSFC クラスターに対して WSFC の構成の検証ウィザードを実行すると、次の警告メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-269">When `RegisterAllProvidersIP = 1`, if you run the WSFC Validate a Configuration Wizard on the WSFC cluster, the wizard generates the following warning message:</span></span>  
    >   
    >  <span data-ttu-id="a3bfe-270">"ネットワーク名 'Name:<network_name>' の RegisterAllProviderIP プロパティは 1 に設定されています。現在のクラスター構成の場合、この値は 0 に設定する必要があります。"</span><span class="sxs-lookup"><span data-stu-id="a3bfe-270">"The RegisterAllProviderIP property for network name 'Name:<network_name>' is set to 1 For the current cluster configuration this value should be set to 0."</span></span>  
    >   
    >  <span data-ttu-id="a3bfe-271">このメッセージは無視してください。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-271">Please ignore this message.</span></span>  
  
-   <span data-ttu-id="a3bfe-272">`MultiSubnetFailover` を true に設定しない接続文字列</span><span class="sxs-lookup"><span data-stu-id="a3bfe-272">Connection strings that do not set `MultiSubnetFailover` to true</span></span>  
  
     <span data-ttu-id="a3bfe-273">`RegisterAllProvidersIP = 1`の場合、接続文字列で `MultiSubnetFailover = True`を使用しないクライアントは、接続の待機時間が長くなります。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-273">When `RegisterAllProvidersIP = 1`, any clients whose connection strings do not use `MultiSubnetFailover = True`, will experience high latency connections.</span></span> <span data-ttu-id="a3bfe-274">これが発生するのは、このようなクライアントはすべての IP への接続を順に試行するためです。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-274">This occurs because these clients attempt connections to all IPs sequentially.</span></span> <span data-ttu-id="a3bfe-275">これに対し、`RegisterAllProvidersIP` を 0 に変更すると、WSFC クラスターのクライアント アクセス ポイントにアクティブな IP アドレスが登録され、レガシ クライアントの待機時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-275">In contrast, if `RegisterAllProvidersIP` is changed to 0, the active IP address is registered in the Client Access Point in the WSFC cluster, reducing latency for legacy clients.</span></span> <span data-ttu-id="a3bfe-276">したがって、可用性グループリスナーに接続する必要があり、プロパティを使用できないレガシクライアントがある場合は、を `MultiSubnetFailover` 0 に変更することをお勧めし `RegisterAllProvidersIP` ます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-276">Therefore, if you have legacy clients that need to connect to an availability group listener and cannot use the `MultiSubnetFailover` property, we recommend that you change `RegisterAllProvidersIP` to 0.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a3bfe-277">WSFC クラスター (フェールオーバー クラスター マネージャーの GUI) を通してリスナーを作成すると、`RegisterAllProvidersIP` は既定で 0 (false) になります。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-277">When you create an availability group listener through the WSFC cluster (Failover Cluster Manager GUI), `RegisterAllProvidersIP` will be 0 (false) by default.</span></span>  
  
###  <a name="hostrecordttl-setting"></a><a name="HostRecordTTL"></a> <span data-ttu-id="a3bfe-278">HostRecordTTL の設定</span><span class="sxs-lookup"><span data-stu-id="a3bfe-278">HostRecordTTL Setting</span></span>  
 <span data-ttu-id="a3bfe-279">既定では、クライアントは 20 分間、クラスター DNS レコードをキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-279">By default, clients cache cluster DNS records for 20 minutes.</span></span>  <span data-ttu-id="a3bfe-280">`HostRecordTTL` の値 (キャッシュするレコードの有効期限 (TTL)) を小さくすると、レガシ クライアントはよりすばやく再接続できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-280">By reducing `HostRecordTTL`, the Time to Live (TTL), for the cached record, legacy clients may reconnect more quickly.</span></span>  <span data-ttu-id="a3bfe-281">ただし、`HostRecordTTL` の設定を小さくすると、DN サーバーへのトラフィックが増加する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-281">However, reducing the `HostRecordTTL` setting may also result in increased traffic to the DN servers.</span></span>  
  
###  <a name="sample-powershell-script-to-disable-registerallprovidersip-and-reduce-ttl"></a><a name="SampleScript"></a><span data-ttu-id="a3bfe-282">RegisterAllProvidersIP を無効にし、TTL を短縮する PowerShell サンプルスクリプト</span><span class="sxs-lookup"><span data-stu-id="a3bfe-282">Sample PowerShell Script to Disable RegisterAllProvidersIP and Reduce TTL</span></span>  
 <span data-ttu-id="a3bfe-283">次の PowerShell の例では、リスナー リソースに対する `RegisterAllProvidersIP` クラスター パラメーターと `HostRecordTTL` クラスター パラメーターの両方を構成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-283">The following PowerShell example demonstrates how to configure both the `RegisterAllProvidersIP` and `HostRecordTTL` cluster parameters for the listener resource.</span></span>  <span data-ttu-id="a3bfe-284">DNS レコードは、既定の 20 分間ではなく、5 分間キャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-284">The DNS record will be cached for 5 minutes rather than the default 20 minutes.</span></span>  <span data-ttu-id="a3bfe-285">両方のクラスター パラメーターを変更すると、`MultiSubnetFailover` パラメーターを使用できないレガシ クライアントのフェールオーバーが発生した後に、適切な IP アドレスに接続する時間が短縮される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-285">Modifying both cluster parameters may reduce the time to connect to the correct IP address after a failover for legacy clients that cannot use the `MultiSubnetFailover` parameter.</span></span>  <span data-ttu-id="a3bfe-286">`yourListenerName` は、変更対象のリスナーの名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-286">Replace `yourListenerName` with the name of the listener that you are changing.</span></span>  
  
```powershell
Import-Module FailoverClusters  
Get-ClusterResource yourListenerName | Set-ClusterParameter RegisterAllProvidersIP 0
Get-ClusterResource yourListenerName|Set-ClusterParameter HostRecordTTL 300  
Stop-ClusterResource yourListenerName  
Start-ClusterResource yourAGResource  
```  
  
 <span data-ttu-id="a3bfe-287">フェールオーバー中の復旧時間の詳細については、「 [Client Recovery Latency During Failover](../../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md#DNS)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-287">For more information about recovery times during failover, see [Client Recovery Latency During Failover](../../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md#DNS).</span></span>  
  
###  <a name="follow-up-recommendations"></a><a name="FollowUpRecommendations"></a> <span data-ttu-id="a3bfe-288">補足情報: 推奨事項</span><span class="sxs-lookup"><span data-stu-id="a3bfe-288">Follow-up Recommendations</span></span>  
 <span data-ttu-id="a3bfe-289">可用性グループ リスナーを作成した後:</span><span class="sxs-lookup"><span data-stu-id="a3bfe-289">After you create an availability group listener:</span></span>  
  
-   <span data-ttu-id="a3bfe-290">リスナーの IP アドレスが排他的に使用されるように確保することを、ネットワーク管理者に依頼します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-290">Ask your network administrator to reserve the listener's IP address for its exclusive use.</span></span>  
  
-   <span data-ttu-id="a3bfe-291">この可用性グループへのクライアント接続を要求するときの接続文字列で使用できるよう、リスナーの DNS ホスト名をアプリケーション開発者に通知します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-291">Give the listener's DNS host name to application developers to use in connection strings when requesting client connections to this availability group.</span></span>  
  
-   <span data-ttu-id="a3bfe-292">可能であれば、 `MultiSubnetFailover = True`を指定するようにクライアント接続文字列を更新することを開発者に勧めます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-292">Encourage developers to update client connection strings to specify `MultiSubnetFailover = True`, if possible.</span></span> <span data-ttu-id="a3bfe-293">マルチサブネット フェールオーバーのドライバー サポートについては、「[AlwaysOn クライアント接続 &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-293">For information about driver support for multi-subnet failover, see [AlwaysOn Client Connectivity &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md).</span></span>  
  
###  <a name="create-an-additional-listener-for-an-availability-group-optional"></a><a name="CreateAdditionalListener"></a> <span data-ttu-id="a3bfe-294">可用性グループの追加のリスナーの作成 (省略可能)</span><span class="sxs-lookup"><span data-stu-id="a3bfe-294">Create an Additional Listener for an Availability Group (Optional)</span></span>  
 <span data-ttu-id="a3bfe-295">SQL Server で 1 つのリスナーを作成した後、次の手順で追加のリスナーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-295">After you create one listener through SQL Server, you can add an additional listener, as follows:</span></span>  
  
1.  <span data-ttu-id="a3bfe-296">次のツールのいずれかを使用してリスナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-296">Create the listener using either of the following tools:</span></span>  
  
    -   <span data-ttu-id="a3bfe-297">**WSFC フェールオーバー クラスター マネージャーの使用:**</span><span class="sxs-lookup"><span data-stu-id="a3bfe-297">**Using WSFC Failover Cluster Manager:**</span></span>  
  
        1.  <span data-ttu-id="a3bfe-298">クライアント アクセス ポイントを追加し、IP アドレスを構成します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-298">Add a client access point and configure the IP address.</span></span>  
  
        2.  <span data-ttu-id="a3bfe-299">リスナーをオンラインにします。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-299">Bring the listener online.</span></span>  
  
        3.  <span data-ttu-id="a3bfe-300">WSFC 可用性グループに対する依存関係を追加します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-300">Add a dependency to the WSFC availability group resource.</span></span>  
  
         <span data-ttu-id="a3bfe-301">フェールオーバー クラスター マネージャーのダイアログ ボックスおよびタブの詳細については、「 [ユーザー インターフェイス: フェールオーバー クラスター マネージャー スナップイン](https://technet.microsoft.com/library/cc772502.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-301">For information about the dialog boxes and tabs of the Failover Cluster Manager, see [User Interface: The Failover Cluster Manager Snap-In](https://technet.microsoft.com/library/cc772502.aspx).</span></span>  
  
    -   <span data-ttu-id="a3bfe-302">**フェールオーバー クラスターの Windows PowerShell の使用:**</span><span class="sxs-lookup"><span data-stu-id="a3bfe-302">**Using Windows PowerShell for failover clusters:**</span></span>  
  
        1.  <span data-ttu-id="a3bfe-303">[Add-ClusterResource](https://technet.microsoft.com/library/ee460983.aspx) を使用して、ネットワーク名と IP アドレス リソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-303">Use [Add-ClusterResource](https://technet.microsoft.com/library/ee460983.aspx) to create a network name and the IP address resources.</span></span>  
  
        2.  <span data-ttu-id="a3bfe-304">[Start-ClusterResource](https://technet.microsoft.com/library/ee461056.aspx) を使用して、ネットワーク名リソースを開始します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-304">Use [Start-ClusterResource](https://technet.microsoft.com/library/ee461056.aspx) to start the network name resource.</span></span>  
  
        3.  <span data-ttu-id="a3bfe-305">[Add-ClusterResourceDependency](https://technet.microsoft.com/library/ee461014.aspx) を使用して、ネットワーク名と、既存の SQL Server 可用性グループ リソース間の依存関係を設定します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-305">Use [Add-ClusterResourceDependency](https://technet.microsoft.com/library/ee461014.aspx) to set the dependency between the network name and the existing SQL Server Availability Group resource.</span></span>  
  
         <span data-ttu-id="a3bfe-306">フェールオーバー クラスターの Windows PowerShell の詳細については、「 [サーバー マネージャーのコマンドの概要](https://technet.microsoft.com/library/cc732757.aspx#BKMK_wps)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-306">For information about using Windows PowerShell for failover clusters, see [Overview of Server Manager Commands](https://technet.microsoft.com/library/cc732757.aspx#BKMK_wps).</span></span>  
  
2.  <span data-ttu-id="a3bfe-307">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で新しいリスナーのリッスンを開始します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-307">Start [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] listening on the new listener.</span></span> <span data-ttu-id="a3bfe-308">追加リスナーを作成した後、プライマリ レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続し、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、または PowerShell を使用してリスナー ポートを変更します。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-308">After creating the additional listener, connect to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the primary replica of the availability group and use [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell to modify the listener port.</span></span>  
  
 <span data-ttu-id="a3bfe-309">詳細については、「[同じ可用性グループの複数のリスナーを作成する方法](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/03/how-to-create-multiple-listeners-for-same-availability-group-goden-yao.aspx)」(SQL Server AlwaysOn チームのブログ) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3bfe-309">For more information, see [How to create multiple listeners for same availability group](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/03/how-to-create-multiple-listeners-for-same-availability-group-goden-yao.aspx) (a SQL Server AlwaysOn team blog).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a3bfe-310">関連タスク</span><span class="sxs-lookup"><span data-stu-id="a3bfe-310">Related Tasks</span></span>  
  
-   [<span data-ttu-id="a3bfe-311">可用性グループ リスナーのプロパティの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a3bfe-311">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
-   [<span data-ttu-id="a3bfe-312">可用性グループ リスナーの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a3bfe-312">Remove an Availability Group Listener &#40;SQL Server&#41;</span></span>](remove-an-availability-group-listener-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="a3bfe-313">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="a3bfe-313">Related Content</span></span>  
  
-   [<span data-ttu-id="a3bfe-314">同じ可用性グループの複数のリスナーを作成する方法</span><span class="sxs-lookup"><span data-stu-id="a3bfe-314">How to create multiple listeners for same availability group</span></span>](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/03/how-to-create-multiple-listeners-for-same-availability-group-goden-yao.aspx)  
  
-   [<span data-ttu-id="a3bfe-315">SQL Server AlwaysOn チームのブログ: SQL Server AlwaysOn チームのオフィシャル ブログ</span><span class="sxs-lookup"><span data-stu-id="a3bfe-315">SQL Server AlwaysOn Team Blog: The official SQL Server AlwaysOn team blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a><span data-ttu-id="a3bfe-316">参照</span><span class="sxs-lookup"><span data-stu-id="a3bfe-316">See Also</span></span>  
 <span data-ttu-id="a3bfe-317">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a3bfe-317">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="a3bfe-318">[可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="a3bfe-318">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 [<span data-ttu-id="a3bfe-319">SQL Server マルチサブネット クラスタリング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a3bfe-319">SQL Server Multi-Subnet Clustering &#40;SQL Server&#41;</span></span>](../../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md)  
