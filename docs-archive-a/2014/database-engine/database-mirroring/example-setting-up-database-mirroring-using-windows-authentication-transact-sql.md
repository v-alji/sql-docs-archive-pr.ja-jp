---
title: Windows 認証を使用したデータベースミラーリングの設定の例 (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- Windows authentication [SQL Server]
- authentication [SQL Server], database mirroring
- database mirroring [SQL Server], security
ms.assetid: 35800769-aede-4aac-b077-0e0e487e302f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 95df855e8e41c5937aae02884c71792537eb2bfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632655"
---
# <a name="example-setting-up-database-mirroring-using-windows-authentication-transact-sql"></a><span data-ttu-id="93f35-102">Windows 認証を使用したデータベース ミラーリングの設定の例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="93f35-102">Example: Setting Up Database Mirroring Using Windows Authentication (Transact-SQL)</span></span>
  <span data-ttu-id="93f35-103">この例では、Windows 認証を使用してミラーリング監視サーバーを利用するデータベース ミラーリング セッションを作成する場合に必要なすべての段階を示しています。</span><span class="sxs-lookup"><span data-stu-id="93f35-103">This example shows all the stages required to create a database mirroring session with a witness using Windows Authentication.</span></span> <span data-ttu-id="93f35-104">このトピックの例では、 [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用します。</span><span class="sxs-lookup"><span data-stu-id="93f35-104">The examples in this topic use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="93f35-105">[!INCLUDE[tsql](../../includes/tsql-md.md)] を使用する代わりに、データベース ミラーリング セキュリティ構成ウィザードを使用してデータベース ミラーリングを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="93f35-105">Note that as an alternative to using [!INCLUDE[tsql](../../includes/tsql-md.md)] steps, you can use the Configure Database Mirroring Security Wizard for database mirroring setup.</span></span> <span data-ttu-id="93f35-106">詳細については、このトピックの後半の「 [Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93f35-106">For more information, see [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md).</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="93f35-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="93f35-107">Prerequisite</span></span>  
 <span data-ttu-id="93f35-108">この例では、既定により単純復旧モデルを使用する **AdventureWorks** サンプル データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="93f35-108">The example uses the **AdventureWorks** sample database, which uses the simple recovery model by default.</span></span> <span data-ttu-id="93f35-109">このデータベースでデータベース ミラーリングを使用するには、完全復旧モデルを使用するように変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="93f35-109">To use database mirroring with this database, you must alter it to use the full recovery model.</span></span> <span data-ttu-id="93f35-110">[!INCLUDE[tsql](../../includes/tsql-md.md)] を使用してこの変更を行うには、次のように ALTER DATABASE ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="93f35-110">To do this in [!INCLUDE[tsql](../../includes/tsql-md.md)], use the ALTER DATABASE statement, as follows:</span></span>  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks   
SET RECOVERY FULL;  
GO  
```  
  
 <span data-ttu-id="93f35-111">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の復旧モデルを変更する方法については、「[データベースの復旧モデルの表示または変更 &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="93f35-111">For information on changing the recovery model in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md).</span></span>  
  
### <a name="permissions"></a><span data-ttu-id="93f35-112">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="93f35-112">Permissions</span></span>  
 <span data-ttu-id="93f35-113">データベースにおける ALTER 権限、および CREATE ENDPOINT 権限、または **sysadmin** 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="93f35-113">Requires ALTER permission on the database and CREATE ENDPOINT permission, or membership in the **sysadmin** fixed server role.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93f35-114">例</span><span class="sxs-lookup"><span data-stu-id="93f35-114">Example</span></span>  
 <span data-ttu-id="93f35-115">この例では、2 つのパートナーとミラーリング監視サーバーが、3 つのコンピューター システムの既定のサーバー インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="93f35-115">In this example, the two partners and the witness are the default server instances on three computer systems.</span></span> <span data-ttu-id="93f35-116">3 つのサーバー インスタンスは同じ Windows ドメインで実行されますが、ミラーリング監視サーバー インスタンスはユーザー アカウント (スタートアップ サービス アカウントとして使用されます) が異なります。</span><span class="sxs-lookup"><span data-stu-id="93f35-116">The three server instances run the same Windows domain, but the user account (used as the startup service account) is different for the example's witness server instance.</span></span>  
  
 <span data-ttu-id="93f35-117">次の表は、この例で使用する値をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="93f35-117">The following table summarizes the values used in this example.</span></span>  
  
|<span data-ttu-id="93f35-118">初期ミラー化ロール</span><span class="sxs-lookup"><span data-stu-id="93f35-118">Initial mirroring role</span></span>|<span data-ttu-id="93f35-119">ホスト システム</span><span class="sxs-lookup"><span data-stu-id="93f35-119">Host system</span></span>|<span data-ttu-id="93f35-120">ドメイン ユーザー アカウント</span><span class="sxs-lookup"><span data-stu-id="93f35-120">Domain user account</span></span>|  
|----------------------------|-----------------|-------------------------|  
|<span data-ttu-id="93f35-121">プリンシパル</span><span class="sxs-lookup"><span data-stu-id="93f35-121">Principal</span></span>|<span data-ttu-id="93f35-122">PARTNERHOST1</span><span class="sxs-lookup"><span data-stu-id="93f35-122">PARTNERHOST1</span></span>|<span data-ttu-id="93f35-123">*\<Mydomain>\\<dbousername\>*</span><span class="sxs-lookup"><span data-stu-id="93f35-123">*\<Mydomain>\\<dbousername\>*</span></span>|  
|<span data-ttu-id="93f35-124">ミラー</span><span class="sxs-lookup"><span data-stu-id="93f35-124">Mirror</span></span>|<span data-ttu-id="93f35-125">PARTNERHOST5</span><span class="sxs-lookup"><span data-stu-id="93f35-125">PARTNERHOST5</span></span>|<span data-ttu-id="93f35-126">*\<Mydomain>\\<dbousername\>*</span><span class="sxs-lookup"><span data-stu-id="93f35-126">*\<Mydomain>\\<dbousername\>*</span></span>|  
|<span data-ttu-id="93f35-127">ミラーリング監視サーバー</span><span class="sxs-lookup"><span data-stu-id="93f35-127">Witness</span></span>|<span data-ttu-id="93f35-128">WITNESSHOST4</span><span class="sxs-lookup"><span data-stu-id="93f35-128">WITNESSHOST4</span></span>|<span data-ttu-id="93f35-129">*\<Somedomain>\\<witnessuser\>*</span><span class="sxs-lookup"><span data-stu-id="93f35-129">*\<Somedomain>\\<witnessuser\>*</span></span>|  
  
1.  <span data-ttu-id="93f35-130">プリンシパル サーバー インスタンス (PARTNERHOST1 の既定のインスタンス) でエンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="93f35-130">Create an endpoint on the principal server instance (default instance on PARTNERHOST1).</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=PARTNER)  
    GO  
    --Partners under same domain user; login already exists in master.  
    --Create a login for the witness server instance,  
    --which is running as Somedomain\witnessuser:  
    USE master ;  
    GO  
    CREATE LOGIN [Somedomain\witnessuser] FROM WINDOWS ;  
    GO  
    -- Grant connect permissions on endpoint to login account of witness.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Somedomain\witnessuser];  
    --Grant connect permissions on endpoint to login account of partners.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Mydomain\dbousername];  
    GO  
    ```  
  
2.  <span data-ttu-id="93f35-131">ミラー サーバー インスタンス (PARTNERHOST5 の既定のインスタンス) でエンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="93f35-131">Create an endpoint on the mirror server instance (default instance on PARTNERHOST5).</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO  
    --Partners under same domain user; login already exists in master.  
    --Create a login for the witness server instance,  
    --which is running as Somedomain\witnessuser:  
    USE master ;  
    GO  
    CREATE LOGIN [Somedomain\witnessuser] FROM WINDOWS ;  
    GO  
    --Grant connect permissions on endpoint to login account of witness.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Somedomain\witnessuser];  
    --Grant connect permissions on endpoint to login account of partners.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Mydomain\dbousername];  
    GO  
    ```  
  
3.  <span data-ttu-id="93f35-132">ミラーリング監視サーバー インスタンス (WITNESSHOST4 の既定のインスタンス) でエンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="93f35-132">Create an endpoint on the witness server instance (default instance on WITNESSHOST4).</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=WITNESS)  
    GO  
    --Create a login for the partner server instances,  
    --which are both running as Mydomain\dbousername:  
    USE master ;  
    GO  
    CREATE LOGIN [Mydomain\dbousername] FROM WINDOWS ;  
    GO  
    --Grant connect permissions on endpoint to login account of partners.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Mydomain\dbousername];  
    GO  
    ```  
  
4.  <span data-ttu-id="93f35-133">ミラー データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="93f35-133">Create the mirror database.</span></span> <span data-ttu-id="93f35-134">詳細については、「 [ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="93f35-134">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
5.  <span data-ttu-id="93f35-135">PARTNERHOST5 のミラー サーバー インスタンスで、PARTNERHOST1 のサーバー インスタンスをパートナーとして設定します (初期プリンシパル サーバー インスタンスにします)。</span><span class="sxs-lookup"><span data-stu-id="93f35-135">On the mirror server instance on PARTNERHOST5, set the server instance on PARTNERHOST1 as the partner (making it the initial principal server instance).</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
        SET PARTNER =   
        'TCP://PARTNERHOST1.COM:7022'  
    GO  
    ```  
  
6.  <span data-ttu-id="93f35-136">PARTNERHOST1 のプリンシパル サーバー インスタンスで、PARTNERHOST5 のサーバー インスタンスをパートナーとして設定します (初期ミラー サーバー インスタンスにします)。</span><span class="sxs-lookup"><span data-stu-id="93f35-136">On the principal server instance on PARTNERHOST1, set the server instance on PARTNERHOST5 as the partner (making it the initial mirror server instance).</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
        SET PARTNER = 'TCP://PARTNERHOST5.COM:7022'  
    GO  
    ```  
  
7.  <span data-ttu-id="93f35-137">プリンシパル サーバーで、ミラーリング監視サーバー (WITNESSHOST4) を設定します。</span><span class="sxs-lookup"><span data-stu-id="93f35-137">On the principal server, set the witness (which is on WITNESSHOST4).</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
        SET WITNESS =   
        'TCP://WITNESSHOST4.COM:7022'  
    GO  
    ```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="93f35-138">関連タスク</span><span class="sxs-lookup"><span data-stu-id="93f35-138">Related Tasks</span></span>  
  
-   [<span data-ttu-id="93f35-139">ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="93f35-139">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
-   [<span data-ttu-id="93f35-140">データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="93f35-140">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
-   [<span data-ttu-id="93f35-141">TRUSTWORTHY プロパティを使用するようにミラー データベースを設定する方法 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="93f35-141">Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;</span></span>](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)  
  
-   [<span data-ttu-id="93f35-142">データベース ミラーリング エンドポイントで発信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="93f35-142">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-outbound-connections.md)  
  
-   [<span data-ttu-id="93f35-143">データベース ミラーリング エンドポイントで着信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="93f35-143">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="93f35-144">例:証明書を使用したデータベース ミラーリングの設定 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="93f35-144">Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;</span></span>](example-setting-up-database-mirroring-using-certificates-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="93f35-145">参照</span><span class="sxs-lookup"><span data-stu-id="93f35-145">See Also</span></span>  
 <span data-ttu-id="93f35-146">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="93f35-146">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="93f35-147">[データベース ミラーリング エンドポイント &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="93f35-147">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="93f35-148">[データベースミラーリングと AlwaysOn 可用性グループ &#40;SQL Server のトランスポートセキュリティ&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="93f35-148">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="93f35-149">[データベースを別のサーバー インスタンスで使用できるようにするときのメタデータの管理 &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md) </span><span class="sxs-lookup"><span data-stu-id="93f35-149">[Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md) </span></span>  
 [<span data-ttu-id="93f35-150">SQL Server データベース エンジンと Azure SQL Database のセキュリティ センター</span><span class="sxs-lookup"><span data-stu-id="93f35-150">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
