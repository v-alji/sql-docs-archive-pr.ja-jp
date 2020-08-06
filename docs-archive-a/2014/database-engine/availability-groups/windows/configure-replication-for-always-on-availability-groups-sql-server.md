---
title: AlwaysOn 可用性グループ用のレプリケーションの構成 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 4e001426-5ae0-4876-85ef-088d6e3fb61c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 916458d2d6b8fbba81940257ee85ffe014d1f12e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713510"
---
# <a name="configure-replication-for-always-on-availability-groups-sql-server"></a><span data-ttu-id="80606-102">AlwaysOn 可用性グループ用のレプリケーションの構成 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="80606-102">Configure Replication for Always On Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="80606-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でのレプリケーションおよび AlwaysOn 可用性グループの構成には、7 つのステップが必要です。</span><span class="sxs-lookup"><span data-stu-id="80606-103">Configuring [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication and AlwaysOn availability groups involves seven steps.</span></span> <span data-ttu-id="80606-104">各ステップの詳細については、以下のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="80606-104">Each step is described in more detail in the following sections.</span></span>  

##  <a name="1-configure-the-database-publications-and-subscriptions"></a><a name="step1"></a> <span data-ttu-id="80606-105">1.データベースのパブリケーションとサブスクリプションを構成する</span><span class="sxs-lookup"><span data-stu-id="80606-105">1. Configure the Database Publications and Subscriptions</span></span>  

### <a name="configure-the-distributor"></a><span data-ttu-id="80606-106">ディストリビューターの構成</span><span class="sxs-lookup"><span data-stu-id="80606-106">Configure the distributor</span></span>
  
 <span data-ttu-id="80606-107">ディストリビューターは、パブリッシング データベースが属している (またはこれから属する) 可用性グループの現在の (または目的の) レプリカのホストにはしないでください。</span><span class="sxs-lookup"><span data-stu-id="80606-107">The distributor should not be a host for any of the current (or intended) replicas of the availability group that the publishing database is (or will become) a member of.</span></span>  
  
1.  <span data-ttu-id="80606-108">ディストリビューター側のディストリビューションを構成します。</span><span class="sxs-lookup"><span data-stu-id="80606-108">Configure distribution at the distributor.</span></span> <span data-ttu-id="80606-109">ストアド プロシージャを使用して構成する場合は、`sp_adddistributor` を実行します。</span><span class="sxs-lookup"><span data-stu-id="80606-109">If stored procedures are being used for configuration, run `sp_adddistributor`.</span></span> <span data-ttu-id="80606-110">パラメーターを使用して、 *@password* リモートパブリッシャーがディストリビューターに接続するときに使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="80606-110">Use the *@password* parameter to identify the password that will be used when a remote publisher connects to the distributor.</span></span> <span data-ttu-id="80606-111">このパスワードは、各リモート パブリッシャーでリモート ディストリビューターを設定するときにも必要になります。</span><span class="sxs-lookup"><span data-stu-id="80606-111">The password will also be needed at each remote publisher when the remote distributor is set up.</span></span>  
  
    ```sql
    USE master;  
    GO  
    EXEC sys.sp_adddistributor  
        @distributor = 'MyDistributor',  
        @password = '**Strong password for distributor**';  
    ```  
  
2.  <span data-ttu-id="80606-112">ディストリビューター側のディストリビューション データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="80606-112">Create the distribution database at the distributor.</span></span> <span data-ttu-id="80606-113">ストアド プロシージャを使用して構成する場合は、`sp_adddistributiondb` を実行します。</span><span class="sxs-lookup"><span data-stu-id="80606-113">If stored procedures are being used for configuration, run `sp_adddistributiondb`.</span></span>  
  
    ```  
    USE master;  
    GO  
    EXEC sys.sp_adddistributiondb  
        @database = 'distribution',  
        @security_mode = 1;  
    ```  
  
3.  <span data-ttu-id="80606-114">リモート パブリッシャーを構成します。</span><span class="sxs-lookup"><span data-stu-id="80606-114">Configure the remote publisher.</span></span> <span data-ttu-id="80606-115">ストアド プロシージャを使用してディストリビューターを構成する場合は、`sp_adddistpublisher` を実行します。</span><span class="sxs-lookup"><span data-stu-id="80606-115">If stored procedures are being used to configure the distributor, run `sp_adddistpublisher`.</span></span> <span data-ttu-id="80606-116">*@security_mode*パラメーターは、レプリケーションエージェントから実行されるパブリッシャーの検証ストアドプロシージャが現在のプライマリに接続する方法を決定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="80606-116">The *@security_mode* parameter is used to determine how the publisher validation stored procedure that is run from the replication agents, connects to the current primary.</span></span> <span data-ttu-id="80606-117">1 に設定すると、現在のプライマリへの接続に Windows 認証が使用されます。</span><span class="sxs-lookup"><span data-stu-id="80606-117">If set to 1 Windows authentication is used to connect to the current primary.</span></span> <span data-ttu-id="80606-118">0に設定する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] と、指定したおよびの値で認証が使用され *@login* *@password* ます。</span><span class="sxs-lookup"><span data-stu-id="80606-118">If set to 0, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] authentication is used with the specified *@login* and *@password* values.</span></span> <span data-ttu-id="80606-119">検証ストアド プロシージャをセカンダリ レプリカに正常に接続するには、各レプリカで有効なログインとパスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80606-119">The login and password specified must be valid at each secondary replica for the validation stored procedure to successfully connect to that replica.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="80606-120">変更されたレプリケーション エージェントをディストリビューター以外のコンピューターで実行する場合、プライマリへの接続に Windows 認証を使用するには、レプリカのホスト コンピューター間の通信に使用する Kerberos 認証を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80606-120">If any modified replication agents run on a computer other than the distributor, use of Windows authentication for the connection to the primary will require Kerberos authentication to be configured for the communication between the replica host computers.</span></span> <span data-ttu-id="80606-121">現在のプライマリへの接続に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインを使用する場合は、Kerberos 認証は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="80606-121">Use of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login for the connection to the current primary will not require Kerberos authentication.</span></span>  
  
    ```sql
    USE master;  
    GO  
    EXEC sys.sp_adddistpublisher  
        @publisher = 'AGPrimaryReplicaHost',  
        @distribution_db = 'distribution',  
        @working_directory = '\\MyReplShare\WorkingDir',  
        @login = 'MyPubLogin',  
        @password = '**Strong password for publisher**';  
    ```  
  
 <span data-ttu-id="80606-122">詳細については、「[sp_adddistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80606-122">For more information, see [sp_adddistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql).</span></span>  
  
### <a name="configure-the-publisher-at-the-original-publisher"></a><span data-ttu-id="80606-123">元のパブリッシャーでのパブリッシャーの構成</span><span class="sxs-lookup"><span data-stu-id="80606-123">Configure the publisher at the original publisher</span></span>
  
1.  <span data-ttu-id="80606-124">リモート ディストリビューションを構成します。</span><span class="sxs-lookup"><span data-stu-id="80606-124">Configure remote distribution.</span></span> <span data-ttu-id="80606-125">ストアド プロシージャを使用してパブリッシャーを構成する場合は、`sp_adddistributor` を実行します。</span><span class="sxs-lookup"><span data-stu-id="80606-125">If stored procedures are being used to configure the publisher, run `sp_adddistributor`.</span></span> <span data-ttu-id="80606-126">*@password* `sp_adddistrbutor` ディストリビューションを設定するためにディストリビューターでを実行したときに使用したのと同じ値を指定します。</span><span class="sxs-lookup"><span data-stu-id="80606-126">Specify the same value for *@password* as that used when `sp_adddistrbutor` was run at the distributor to set up distribution.</span></span>  
  
    ```sql
    exec sys.sp_adddistributor  
        @distributor = 'MyDistributor',  
        @password = 'MyDistPass'  
    ```  
  
2.  <span data-ttu-id="80606-127">データベースでレプリケーションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="80606-127">Enable the database for replication.</span></span> <span data-ttu-id="80606-128">ストアド プロシージャを使用してパブリッシャーを構成する場合は、`sp_replicationdboption` を実行します。</span><span class="sxs-lookup"><span data-stu-id="80606-128">If stored procedures are being used to configure the publisher, run `sp_replicationdboption`.</span></span> <span data-ttu-id="80606-129">データベースに対してトランザクション レプリケーションとマージ レプリケーションの両方を構成する場合は、それぞれを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="80606-129">If both transactional and merge replication are to be configured for the database, each must be enabled.</span></span>  
  
    ```sql
    USE master;  
    GO  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'publish',  
        @value = 'true';  
  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'merge publish',  
        @value = 'true';  
    ```  
  
3.  <span data-ttu-id="80606-130">レプリケーションのパブリケーション、アーティクル、およびサブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="80606-130">Create the replication publication, articles, and subscriptions.</span></span> <span data-ttu-id="80606-131">レプリケーションを構成する方法の詳細については、「データとデータベース オブジェクトのパブリッシュ」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80606-131">For more information about how to configure replication, see Publishing Data and Database objects.</span></span>  
  
##  <a name="2-configure-the-alwayson-availability-group"></a><a name="step2"></a><span data-ttu-id="80606-132">2. AlwaysOn 可用性グループを構成する</span><span class="sxs-lookup"><span data-stu-id="80606-132">2. Configure the AlwaysOn Availability Group</span></span>  
 <span data-ttu-id="80606-133">目的のプライマリで、メンバー データベースとしてパブリッシュされている (またはパブリッシュする) データベースを含む可用性グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="80606-133">At the intended primary, create the availability group with the published (or to be published) database as a member database.</span></span> <span data-ttu-id="80606-134">可用性グループ ウィザードを使用する場合は、ウィザードで最初にセカンダリ レプリカ データベースを同期するか、バックアップと復元を使用して手動で初期化を実行するかを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="80606-134">If using the Availability Group Wizard, you can either allow the wizard to initially synchronize the secondary replica databases or you can perform the initialization manually by using backup and restore.</span></span>  
  
 <span data-ttu-id="80606-135">現在のプライマリへの接続にレプリケーション エージェントで使用される可用性グループの DNS リスナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="80606-135">Create a DNS listener for the availability group that will be used by the replication agents to connect to the current primary.</span></span> <span data-ttu-id="80606-136">指定したリスナー名は、元のパブリッシャーとパブリッシュされたデータベースのペアに対してリダイレクトの対象として使用されます。</span><span class="sxs-lookup"><span data-stu-id="80606-136">The listener name that is specified will be used as the target of redirection for the original publisher/published database pair.</span></span> <span data-ttu-id="80606-137">たとえば、DDL を使用して可用性グループを構成する場合は、次のコード例に従って、`MyAG` という名前の既存の可用性グループの可用性グループ リスナーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="80606-137">For example, if you are using DDL to configure the availability group, the following code example can be used to specify an availability group listener for an existing availability group named `MyAG`:</span></span>  
  
```sql
ALTER AVAILABILITY GROUP 'MyAG'   
    ADD LISTENER 'MyAGListenerName' (WITH IP (('10.120.19.155', '255.255.254.0')));  
```  
  
 <span data-ttu-id="80606-138">詳細については、「[可用性グループの作成と構成 &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80606-138">For more information, see [Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md).</span></span>  
  
##  <a name="3-insure-that-all-of-the-secondary-replica-hosts-are-configured-for-replication"></a><a name="step3"></a><span data-ttu-id="80606-139">3. セカンダリレプリカのすべてのホストがレプリケーション用に構成されていることを確認する</span><span class="sxs-lookup"><span data-stu-id="80606-139">3. Insure that all of the Secondary Replica Hosts are Configured for Replication</span></span>  
 <span data-ttu-id="80606-140">セカンダリ レプリカの各ホストで、レプリケーションをサポートするように [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="80606-140">At each secondary replica host, verify that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] has been configured to support replication.</span></span> <span data-ttu-id="80606-141">レプリケーションがインストールされているかどうかを確認するには、セカンダリ レプリカの各ホストで次のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="80606-141">The following query can be run at each secondary replica host to determine whether replication is installed:</span></span>  
  
```sql
USE master;  
GO  
DECLARE @installed int;  
EXEC @installed = sys.sp_MS_replication_installed;  
SELECT @installed;  
```  
  
 <span data-ttu-id="80606-142">*@installed*が0の場合、インストールにレプリケーションを追加する必要があり [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="80606-142">If *@installed* is 0, replication must be added to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation.</span></span>  
  
##  <a name="4-configure-the-secondary-replica-hosts-as-replication-publishers"></a><a name="step4"></a> <span data-ttu-id="80606-143">4.セカンダリ レプリカのホストをレプリケーションのパブリッシャーとして構成する</span><span class="sxs-lookup"><span data-stu-id="80606-143">4. Configure the Secondary Replica Hosts as Replication Publishers</span></span>  
 <span data-ttu-id="80606-144">セカンダリ レプリカはレプリケーションのパブリッシャーまたはリパブリッシャーとしては機能しませんが、フェールオーバー後にセカンダリで処理を引き継ぐようにレプリケーションを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80606-144">A secondary replica cannot act as a replication publisher or republisher but replication must be configured so that the secondary can take over after a failover.</span></span> <span data-ttu-id="80606-145">ディストリビューターで、セカンダリ レプリカの各ホストのディストリビューションを構成します。</span><span class="sxs-lookup"><span data-stu-id="80606-145">At the distributor, configure distribution for each secondary replica host.</span></span> <span data-ttu-id="80606-146">ディストリビューション データベースと作業ディレクトリは、元のパブリッシャーをディストリビューターに追加したときと同じものを指定します。</span><span class="sxs-lookup"><span data-stu-id="80606-146">Specify the same distribution database and working directory as was specified when the original publisher was added to the distributor.</span></span> <span data-ttu-id="80606-147">ストアド プロシージャを使用してディストリビューションを構成する場合は、`sp_adddistpublisher` を使用してリモート パブリッシャーをディストリビューターに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="80606-147">If you are using stored procedures to configure distribution, use `sp_adddistpublisher` to associate the remote publishers with the distributor.</span></span> <span data-ttu-id="80606-148">*@login*とが *@password* 元のパブリッシャーに対して使用されていた場合は、セカンダリレプリカのホストをパブリッシャーとして追加するときに、それぞれに同じ値を指定します。</span><span class="sxs-lookup"><span data-stu-id="80606-148">If *@login* and *@password* were used for the original publisher, specify the same values for each when you add the secondary replica hosts as publishers.</span></span>  
  
```sql
EXEC sys.sp_adddistpublisher  
    @publisher = 'AGSecondaryReplicaHost',  
    @distribution_db = 'distribution',  
    @working_directory = '\\MyReplShare\WorkingDir',  
    @login = 'MyPubLogin',  
    @password = '**Strong password for publisher**';  
```  
  
 <span data-ttu-id="80606-149">セカンダリ レプリカの各ホストで、ディストリビューションを構成します。</span><span class="sxs-lookup"><span data-stu-id="80606-149">At each secondary replica host, configure distribution.</span></span> <span data-ttu-id="80606-150">リモート ディストリビューターには、元のパブリッシャーのディストリビューターを指定します。</span><span class="sxs-lookup"><span data-stu-id="80606-150">Identify the distributor of the original publisher as the remote distributor.</span></span> <span data-ttu-id="80606-151">パスワードは、ディストリビューターで最初に `sp_adddistributor` を実行したときと同じものを使用します。</span><span class="sxs-lookup"><span data-stu-id="80606-151">Use the same password as that used when `sp_adddistributor` was run originally at the distributor.</span></span> <span data-ttu-id="80606-152">ストアドプロシージャを使用してディストリビューションを構成する場合 *@password* は、のパラメーターを使用して `sp_adddistributor` パスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="80606-152">If stored procedures are being used to configure distribution, the *@password* parameter of `sp_adddistributor` is used to specify the password.</span></span>  
  
```sql
EXEC sp_adddistributor   
    @distributor = 'MyDistributor',  
    @password = '**Strong password for distributor**';  
```  
  
 <span data-ttu-id="80606-153">セカンダリ レプリカの各ホストで、データベースのパブリケーションのプッシュ サブスクライバーがリンク サーバーとして表示されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="80606-153">At each secondary replica host, make sure that the push subscribers of the database publications appear as linked servers.</span></span> <span data-ttu-id="80606-154">ストアド プロシージャを使用してリモート パブリッシャーを構成する場合は、`sp_addlinkedserver` を使用してパブリッシャーにリンク サーバーとしてサブスクライバーを追加します (まだ存在しない場合)。</span><span class="sxs-lookup"><span data-stu-id="80606-154">If stored procedures are being used to configure the remote publishers, use `sp_addlinkedserver` to add the subscribers (if not already present) as linked servers to the publishers.</span></span>  
  
```sql
EXEC sys.sp_addlinkedserver   
    @server = 'MySubscriber';  
```  
  
##  <a name="5-redirect-the-original-publisher-to-the-ag-listener-name"></a><a name="step5"></a> <span data-ttu-id="80606-155">5.元のパブリッシャーを AG リスナー名にリダイレクトする</span><span class="sxs-lookup"><span data-stu-id="80606-155">5. Redirect the Original Publisher to the AG Listener Name</span></span>  
 <span data-ttu-id="80606-156">ディストリビューター側のディストリビューション データベースで、ストアド プロシージャ `sp_redirect_publisher` を実行して、元のパブリッシャーとパブリッシュされたデータベースを可用性グループの可用性グループ リスナー名に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="80606-156">At the distributor, in the distribution database, run the stored procedure `sp_redirect_publisher` to associate the original publisher and the published database with the availability group listener name of the availability group.</span></span>  
  
```sql
USE distribution;  
GO  
EXEC sys.sp_redirect_publisher   
@original_publisher = 'MyPublisher',  
    @publisher_db = 'MyPublishedDB',  
    @redirected_publisher = 'MyAGListenerName';  
```  
  
##  <a name="6-run-the-replication-validation-stored-procedure-to-verify-the-configuration"></a><a name="step6"></a> <span data-ttu-id="80606-157">6.レプリケーションの検証ストアド プロシージャを実行して構成を確認する</span><span class="sxs-lookup"><span data-stu-id="80606-157">6. Run the Replication Validation Stored Procedure to Verify the Configuration</span></span>  
 <span data-ttu-id="80606-158">ディストリビューター側のディストリビューション データベースで、ストアド プロシージャ `sp_validate_replica_hosts_as_publishers` を実行して、レプリカのすべてのホストが、パブリッシュされたデータベースのパブリッシャーとして機能するように構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="80606-158">At the distributor, in the distribution database, run the stored procedure `sp_validate_replica_hosts_as_publishers` to verify that all replica hosts are now configured to serve as publishers for the published database.</span></span>  
  
```sql
USE distribution;  
GO  
DECLARE @redirected_publisher sysname;  
EXEC sys.sp_validate_replica_hosts_as_publishers  
    @original_publisher = 'MyPublisher',  
    @publisher_db = 'MyPublishedDB',  
    @redirected_publisher = @redirected_publisher output;  
```  
  
 <span data-ttu-id="80606-159">ストアド プロシージャ `sp_validate_replica_hosts_as_publishers` は、可用性グループ レプリカの各ホストで、可用性グループに関する情報をクエリするための十分な権限を持つログインから実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80606-159">The stored procedure `sp_validate_replica_hosts_as_publishers` should be run from a login with sufficient authorization at each availability group replica host to query for information about the availability group.</span></span> <span data-ttu-id="80606-160">とは異なり `sp_validate_redirected_publisher` 、は呼び出し元の資格情報を使用し、msdb に保持されているログインを使用して可用性グループレプリカに接続しません。</span><span class="sxs-lookup"><span data-stu-id="80606-160">Unlike `sp_validate_redirected_publisher`, it uses the credentials of the caller and does not use the login retained in msdb.dbo.MSdistpublishers to connect to the availability group replicas.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="80606-161">セカンダリ レプリカのホストで読み取りアクセスが許可されていない場合や、読み取りを目的としたアクセスを指定する必要がある場合、`sp_validate_replica_hosts_as_publishers` による検証は失敗し、次のエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="80606-161">`sp_validate_replica_hosts_as_publishers` will fail with the following error when validating secondary replica hosts that do not allow read access, or require read intent to be specified.</span></span>  
>   
>  <span data-ttu-id="80606-162">メッセージ 21899、レベル 11、状態 1、プロシージャ `sp_hadr_verify_subscribers_at_publisher`、行 109</span><span class="sxs-lookup"><span data-stu-id="80606-162">Msg 21899, Level 11, State 1, Procedure `sp_hadr_verify_subscribers_at_publisher`, Line 109</span></span>  
>   
>  <span data-ttu-id="80606-163">元のパブリッシャー 'MyOriginalPublisher' のサブスクライバーの sysserver エントリがあるかどうかを判断するために、リダイレクトされたパブリッシャー 'MyReplicaHostName' で実行したクエリが、エラー '976'、エラー メッセージ 'エラー 976、レベル 14、状態 1、メッセージ: 対象になるデータベース 'MyPublishedDB' は可用性グループに参加しているため、現在クエリでアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="80606-163">The query at the redirected publisher 'MyReplicaHostName' to determine whether there were sysserver entries for the subscribers of the original publisher 'MyOriginalPublisher' failed with error '976', error message 'Error 976, Level 14, State 1, Message: The target database, 'MyPublishedDB', is participating in an availability group and is currently not accessible for queries.</span></span> <span data-ttu-id="80606-164">データ移動が中断されているか、可用性レプリカの読み取りアクセスが有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="80606-164">Either data movement is suspended or the availability replica is not enabled for read access.</span></span> <span data-ttu-id="80606-165">このデータベースや可用性グループの他のデータベースへの読み取り専用アクセスを許可するには、グループの 1 つ以上のセカンダリ可用性レプリカへの読み取りアクセスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="80606-165">To allow read-only access to this and other databases in the availability group, enable read access to one or more secondary availability replicas in the group.</span></span>  <span data-ttu-id="80606-166">詳細については、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オンライン ブックの `ALTER AVAILABILITY GROUP` ステートメントのトピックを参照してください。' で失敗しました。</span><span class="sxs-lookup"><span data-stu-id="80606-166">For more information, see the `ALTER AVAILABILITY GROUP` statement in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.'.</span></span>  
>   
>  <span data-ttu-id="80606-167">レプリカ ホスト 'MyReplicaHostName' について、1 つまたは複数のパブリッシャー検証エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="80606-167">One or more publisher validation errors were encountered for replica host 'MyReplicaHostName'.</span></span>  
  
 <span data-ttu-id="80606-168">これは正しい動作です。</span><span class="sxs-lookup"><span data-stu-id="80606-168">This is expected behavior.</span></span> <span data-ttu-id="80606-169">これらのセカンダリ レプリカのホストでは、sysserver エントリをホストで直接クエリして、サブスクライバー サーバーのエントリがあるかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80606-169">You must verify the presence of the subscriber server entries at these secondary replica hosts by querying for the sysserver entries directly at the host.</span></span>  
  
##  <a name="7-add-the-original-publisher-to-replication-monitor"></a><a name="step7"></a> <span data-ttu-id="80606-170">7.元のパブリッシャーをレプリケーション モニターに追加する</span><span class="sxs-lookup"><span data-stu-id="80606-170">7. Add the Original Publisher to Replication Monitor</span></span>  
 <span data-ttu-id="80606-171">それぞれの可用性グループ レプリカで、元のパブリッシャーをレプリケーション モニターに追加します。</span><span class="sxs-lookup"><span data-stu-id="80606-171">At each availability group replica, add the original publisher to Replication Monitor.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="80606-172">関連タスク</span><span class="sxs-lookup"><span data-stu-id="80606-172">Related Tasks</span></span>  
 <span data-ttu-id="80606-173">**レプリケーション**</span><span class="sxs-lookup"><span data-stu-id="80606-173">**Replication**</span></span>  
  
-   [<span data-ttu-id="80606-174">AlwaysOn パブリケーションデータベースのメンテナンス &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="80606-174">Maintaining an AlwaysOn Publication Database &#40;SQL Server&#41;</span></span>](maintaining-an-always-on-publication-database-sql-server.md)  
  
-   [<span data-ttu-id="80606-175">レプリケーション、Change Tracking、変更データキャプチャ、AlwaysOn 可用性グループ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="80606-175">Replication, Change Tracking, Change Data Capture, and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replicate-track-change-data-capture-always-on-availability.md)  
  
-   [<span data-ttu-id="80606-176">レプリケーション管理に関する FAQ</span><span class="sxs-lookup"><span data-stu-id="80606-176">Replication Administration FAQ</span></span>](../../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md)  
  
 <span data-ttu-id="80606-177">**可用性グループを作成して構成するには**</span><span class="sxs-lookup"><span data-stu-id="80606-177">**To create and configure an availability group**</span></span>  
  
-   [<span data-ttu-id="80606-178">可用性グループ ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="80606-178">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   <span data-ttu-id="80606-179">[[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="80606-179">[Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span></span>  
  
-   [<span data-ttu-id="80606-180">可用性グループの作成 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="80606-180">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
-   [<span data-ttu-id="80606-181">可用性グループの作成 &#40;SQL Server PowerShell&#41;</span><span class="sxs-lookup"><span data-stu-id="80606-181">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
-   [<span data-ttu-id="80606-182">可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="80606-182">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="80606-183">AlwaysOn 可用性グループ &#40;SQL Server PowerShell のデータベースミラーリングエンドポイントを作成&#41;</span><span class="sxs-lookup"><span data-stu-id="80606-183">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="80606-184">可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="80606-184">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="80606-185">可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="80606-185">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="80606-186">可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="80606-186">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="80606-187">可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="80606-187">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="80606-188">参照</span><span class="sxs-lookup"><span data-stu-id="80606-188">See Also</span></span>  
 <span data-ttu-id="80606-189">[AlwaysOn 可用性グループ &#40;SQL Server の前提条件、制限事項、推奨事項&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="80606-189">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="80606-190">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="80606-190">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="80606-191">[AlwaysOn 可用性グループ: 相互運用性 (SQL Server)](always-on-availability-groups-interoperability-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="80606-191">[AlwaysOn Availability Groups: Interoperability (SQL Server)](always-on-availability-groups-interoperability-sql-server.md) </span></span>  
 [<span data-ttu-id="80606-192">SQL Server レプリケーション</span><span class="sxs-lookup"><span data-stu-id="80606-192">SQL Server Replication</span></span>](../../../relational-databases/replication/sql-server-replication.md)  
