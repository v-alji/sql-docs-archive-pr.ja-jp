---
title: 証明書を使用したデータベース ミラーリングの設定の例 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- certificates [SQL Server], database mirroring
- authentication [SQL Server], database mirroring
- database mirroring [SQL Server], security
ms.assetid: df489ecd-deee-465c-a26a-6d1bef6d7b66
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ea87e2de984107c5a0fda6eb2629ee5cfd197841
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742570"
---
# <a name="example-setting-up-database-mirroring-using-certificates-transact-sql"></a><span data-ttu-id="93a28-102">例:証明書を使用したデータベース ミラーリングの設定 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="93a28-102">Example: Setting Up Database Mirroring Using Certificates (Transact-SQL)</span></span>
  <span data-ttu-id="93a28-103">この例では、証明書ベースの認証を使用してデータベース ミラーリング セッションを作成するために必要なすべての段階について説明します。</span><span class="sxs-lookup"><span data-stu-id="93a28-103">This example shows all the stages required to create a database mirroring session using certificate-based authentication.</span></span> <span data-ttu-id="93a28-104">このトピックの例では、 [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用します。</span><span class="sxs-lookup"><span data-stu-id="93a28-104">The examples in this topic use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="93a28-105">ネットワークがセキュリティで保護されていることを保証できる場合を除いて、データベース ミラーリング接続に対して暗号化を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="93a28-105">Unless you can guarantee that your network is secure, we recommend that you use encryption for database mirroring connections.</span></span>  
  
 <span data-ttu-id="93a28-106">証明書を別のシステムにコピーする場合は、セキュリティで保護されたコピー方法を使用してください。</span><span class="sxs-lookup"><span data-stu-id="93a28-106">When copying a certificate to another system, use a secure copy method.</span></span> <span data-ttu-id="93a28-107">すべての証明書をセキュリティで保護された状態で保管するよう十分に注意してください。</span><span class="sxs-lookup"><span data-stu-id="93a28-107">Be extremely careful to keep all of your certificates secure.</span></span>  
  
##  <a name="example"></a><a name="ExampleH2"></a> <span data-ttu-id="93a28-108">例</span><span class="sxs-lookup"><span data-stu-id="93a28-108">Example</span></span>  
 <span data-ttu-id="93a28-109">以下の例は、HOST_A に存在するパートナーで実行する必要のある処理を示しています。</span><span class="sxs-lookup"><span data-stu-id="93a28-109">The following example demonstrates what must be done on one partner that resides on HOST_A.</span></span> <span data-ttu-id="93a28-110">この例では、2 つのパートナーが、3 つのコンピューター システムの既定のサーバー インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="93a28-110">In this example, the two partners are the default server instances on three computer systems.</span></span> <span data-ttu-id="93a28-111">2 つのサーバー インスタンスは、信頼されていない Windows ドメインで実行されているため、証明書ベースの認証が必要です。</span><span class="sxs-lookup"><span data-stu-id="93a28-111">The two server instances run in nontrusted Windows domains, so certificate-based authentication is required.</span></span>  
  
 <span data-ttu-id="93a28-112">初期プリンシパル ロールは HOST_A によって取得され、ミラー ロールは HOST_B によって取得されます。</span><span class="sxs-lookup"><span data-stu-id="93a28-112">The initial principal role is taken by HOST_A, and the mirror role is taken by HOST_B.</span></span>  
  
 <span data-ttu-id="93a28-113">証明書を使用したデータベース ミラーリングの設定には、一般的な段階が 4 つあり、そのうちの 3 つの段階 (1、2、および 4) をこの例に示します。</span><span class="sxs-lookup"><span data-stu-id="93a28-113">Setting up database mirroring using certificates involves four general stages, of which three stages-1, 2, and 4-are demonstrated by this example.</span></span> <span data-ttu-id="93a28-114">これらの段階は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="93a28-114">These stages are as follows:</span></span>  
  
1.  [<span data-ttu-id="93a28-115">発信接続の構成</span><span class="sxs-lookup"><span data-stu-id="93a28-115">Configuring Outbound Connections</span></span>](#ConfiguringOutboundConnections)  
  
     <span data-ttu-id="93a28-116">この例では次の手順を示します。</span><span class="sxs-lookup"><span data-stu-id="93a28-116">This example shows the steps for:</span></span>  
  
    1.  <span data-ttu-id="93a28-117">発信接続用の Host_A の構成。</span><span class="sxs-lookup"><span data-stu-id="93a28-117">Configuring Host_A for outbound connections.</span></span>  
  
    2.  <span data-ttu-id="93a28-118">発信接続用の Host_B の構成。</span><span class="sxs-lookup"><span data-stu-id="93a28-118">Configuring Host_B for outbound connections.</span></span>  
  
     <span data-ttu-id="93a28-119">データベース ミラーリングの設定のこの段階の詳細については、「 [データベース ミラーリング エンドポイントで発信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="93a28-119">For information about this stage of setting up database mirroring, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span>  
  
2.  [<span data-ttu-id="93a28-120">着信接続の構成</span><span class="sxs-lookup"><span data-stu-id="93a28-120">Configuring Inbound Connections</span></span>](#ConfigureInboundConnections)  
  
     <span data-ttu-id="93a28-121">この例では次の手順を示します。</span><span class="sxs-lookup"><span data-stu-id="93a28-121">This example shows the steps for:</span></span>  
  
    1.  <span data-ttu-id="93a28-122">着信接続用の Host_A の構成。</span><span class="sxs-lookup"><span data-stu-id="93a28-122">Configuring Host_A for inbound connections.</span></span>  
  
    2.  <span data-ttu-id="93a28-123">着信接続用の Host_B の構成。</span><span class="sxs-lookup"><span data-stu-id="93a28-123">Configuring Host_B for inbound connections.</span></span>  
  
     <span data-ttu-id="93a28-124">データベース ミラーリングの設定のこの段階の詳細については、「 [データベース ミラーリング エンドポイントで着信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="93a28-124">For information about this stage of setting up database mirroring, see [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md).</span></span>  
  
3.  <span data-ttu-id="93a28-125">ミラー データベースの作成</span><span class="sxs-lookup"><span data-stu-id="93a28-125">Creating the Mirror Database</span></span>  
  
     <span data-ttu-id="93a28-126">ミラー データベースを作成する方法の詳細については、「 [ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="93a28-126">For information on how to create a mirror database, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
4.  [<span data-ttu-id="93a28-127">ミラーリング パートナーの構成</span><span class="sxs-lookup"><span data-stu-id="93a28-127">Configuring the Mirroring Partners</span></span>](#ConfigureMirroringPartners)  
  
###  <a name="configuring-outbound-connections"></a><a name="ConfiguringOutboundConnections"></a> <span data-ttu-id="93a28-128">発信接続の構成</span><span class="sxs-lookup"><span data-stu-id="93a28-128">Configuring Outbound Connections</span></span>  
 <span data-ttu-id="93a28-129">**発信接続用に Host_A を構成するには**</span><span class="sxs-lookup"><span data-stu-id="93a28-129">**To configure Host_A for outbound connections**</span></span>  
  
1.  <span data-ttu-id="93a28-130">master データベースで、必要な場合はデータベース マスター キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="93a28-130">On the master database, create the database master key, if needed.</span></span>  
  
    ```  
    USE master;  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<1_Strong_Password!>';  
    GO  
    ```  
  
2.  <span data-ttu-id="93a28-131">このサーバー インスタンスに対する証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="93a28-131">Make a certificate for this server instance.</span></span>  
  
    ```  
    USE master;  
    CREATE CERTIFICATE HOST_A_cert   
       WITH SUBJECT = 'HOST_A certificate';  
    GO  
    ```  
  
3.  <span data-ttu-id="93a28-132">作成した証明書を使用して、サーバー インスタンスのミラーリング エンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="93a28-132">Create a mirroring endpoint for server instance using the certificate.</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
       STATE = STARTED  
       AS TCP (  
          LISTENER_PORT=7024  
          , LISTENER_IP = ALL  
       )   
       FOR DATABASE_MIRRORING (   
          AUTHENTICATION = CERTIFICATE HOST_A_cert  
          , ENCRYPTION = REQUIRED ALGORITHM AES  
          , ROLE = ALL  
       );  
    GO  
    ```  
  
4.  <span data-ttu-id="93a28-133">HOST_A の証明書をバックアップし、他のシステム HOST_B にコピーします。</span><span class="sxs-lookup"><span data-stu-id="93a28-133">Back up the HOST_A certificate, and copy it to other system, HOST_B.</span></span>  
  
    ```  
    BACKUP CERTIFICATE HOST_A_cert TO FILE = 'C:\HOST_A_cert.cer';  
    GO  
    ```  
  
5.  <span data-ttu-id="93a28-134">安全なコピー方法を使用して、C:\HOST_A_cert.cer を HOST_B にコピーします。</span><span class="sxs-lookup"><span data-stu-id="93a28-134">Using any secure copy method, copy C:\HOST_A_cert.cer to HOST_B.</span></span>  
  
 <span data-ttu-id="93a28-135">**発信接続用に Host_B を構成するには**</span><span class="sxs-lookup"><span data-stu-id="93a28-135">**To configure Host_B for outbound connections**</span></span>  
  
1.  <span data-ttu-id="93a28-136">master データベースで、必要な場合はデータベース マスター キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="93a28-136">On the master database, create the database master key, if needed.</span></span>  
  
    ```  
    USE master;  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<Strong_Password_#2>';  
    GO  
    ```  
  
2.  <span data-ttu-id="93a28-137">HOST_B サーバー インスタンスで証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="93a28-137">Make a certificate on the HOST_B server instance.</span></span>  
  
    ```  
    CREATE CERTIFICATE HOST_B_cert   
       WITH SUBJECT = 'HOST_B certificate for database mirroring';  
    GO  
    ```  
  
3.  <span data-ttu-id="93a28-138">HOST_B のサーバー インスタンスに対するミラーリング エンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="93a28-138">Create a mirroring endpoint for the server instance on HOST_B.</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
       STATE = STARTED  
       AS TCP (  
          LISTENER_PORT=7024  
          , LISTENER_IP = ALL  
       )   
       FOR DATABASE_MIRRORING (   
          AUTHENTICATION = CERTIFICATE HOST_B_cert  
          , ENCRYPTION = REQUIRED ALGORITHM AES  
          , ROLE = ALL  
       );  
    GO  
    ```  
  
4.  <span data-ttu-id="93a28-139">HOST_B の証明書をバックアップします。</span><span class="sxs-lookup"><span data-stu-id="93a28-139">Back up HOST_B certificate.</span></span>  
  
    ```  
    BACKUP CERTIFICATE HOST_B_cert TO FILE = 'C:\HOST_B_cert.cer';  
    GO   
    ```  
  
5.  <span data-ttu-id="93a28-140">安全なコピー方法を使用して、C:\HOST_B_cert.cer を HOST_A にコピーします。</span><span class="sxs-lookup"><span data-stu-id="93a28-140">Using any secure copy method, copy C:\HOST_B_cert.cer to HOST_A.</span></span>  
  
 <span data-ttu-id="93a28-141">詳細については、「 [データベース ミラーリング エンドポイントで発信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="93a28-141">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span>  
  
###  <a name="configuring-inbound-connections"></a><a name="ConfigureInboundConnections"></a> <span data-ttu-id="93a28-142">着信接続の構成</span><span class="sxs-lookup"><span data-stu-id="93a28-142">Configuring Inbound Connections</span></span>  
 <span data-ttu-id="93a28-143">**着信接続用に Host_A を構成するには**</span><span class="sxs-lookup"><span data-stu-id="93a28-143">**To configure Host_A for inbound connections**</span></span>  
  
1.  <span data-ttu-id="93a28-144">HOST_B に対するログインを HOST_A に作成します。</span><span class="sxs-lookup"><span data-stu-id="93a28-144">Create a login on HOST_A for HOST_B.</span></span>  
  
    ```  
    USE master;  
    CREATE LOGIN HOST_B_login WITH PASSWORD = '1Sample_Strong_Password!@#';  
    GO  
    ```  
  
2.  <span data-ttu-id="93a28-145">そのログインのユーザー名を作成します。</span><span class="sxs-lookup"><span data-stu-id="93a28-145">--Create a user for that login.</span></span>  
  
    ```  
    CREATE USER HOST_B_user FOR LOGIN HOST_B_login;  
    GO  
    ```  
  
3.  <span data-ttu-id="93a28-146">証明書をユーザーと関連付けます。</span><span class="sxs-lookup"><span data-stu-id="93a28-146">--Associate the certificate with the user.</span></span>  
  
    ```  
    CREATE CERTIFICATE HOST_B_cert  
       AUTHORIZATION HOST_B_user  
       FROM FILE = 'C:\HOST_B_cert.cer'  
    GO  
    ```  
  
4.  <span data-ttu-id="93a28-147">リモート ミラーリング エンドポイント用のログインに CONNECT 権限を許可します。</span><span class="sxs-lookup"><span data-stu-id="93a28-147">Grant CONNECT permission on the login for the remote mirroring endpoint.</span></span>  
  
    ```  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [HOST_B_login];  
    GO  
    ```  
  
 <span data-ttu-id="93a28-148">**着信接続用に Host_B を構成するには**</span><span class="sxs-lookup"><span data-stu-id="93a28-148">**To configure Host_B for inbound connections**</span></span>  
  
1.  <span data-ttu-id="93a28-149">HOST_A に対するログインを HOST_B に作成します。</span><span class="sxs-lookup"><span data-stu-id="93a28-149">Create a login on HOST_B for HOST_A.</span></span>  
  
    ```  
    USE master;  
    CREATE LOGIN HOST_A_login WITH PASSWORD = '=Sample#2_Strong_Password2';  
    GO  
    ```  
  
2.  <span data-ttu-id="93a28-150">そのログインのユーザー名を作成します。</span><span class="sxs-lookup"><span data-stu-id="93a28-150">Create a user for that login.</span></span>  
  
    ```  
    CREATE USER HOST_A_user FOR LOGIN HOST_A_login;  
    GO  
    ```  
  
3.  <span data-ttu-id="93a28-151">証明書をユーザーと関連付けます。</span><span class="sxs-lookup"><span data-stu-id="93a28-151">Associate the certificate with the user.</span></span>  
  
    ```  
    CREATE CERTIFICATE HOST_A_cert  
       AUTHORIZATION HOST_A_user  
       FROM FILE = 'C:\HOST_A_cert.cer'  
    GO  
    ```  
  
4.  <span data-ttu-id="93a28-152">リモート ミラーリング エンドポイント用のログインに CONNECT 権限を許可します。</span><span class="sxs-lookup"><span data-stu-id="93a28-152">Grant CONNECT permission on the login for the remote mirroring endpoint.</span></span>  
  
    ```  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [HOST_A_login];  
    GO  
    ```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="93a28-153">自動フェールオーバーを伴う高い安全性モードで実行する場合、発信接続と着信接続の両方で、ミラーリング監視サーバーを構成する同じ手順を繰り返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="93a28-153">If you intend to run in high-safety mode with automatic failover, you must repeat the same setup steps to configure the witness for outbound and inbound connections.</span></span> <span data-ttu-id="93a28-154">ミラーリング監視サーバーを利用する着信接続を設定する場合は、両方のパートナーでミラーリング監視サーバー用にログインとユーザーを設定し、ミラーリング監視サーバーで両方のパートナー用にログインとユーザーを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="93a28-154">Setting up the inbound connections when a witness is involved requires that you set up logins and users for the witness on both of the partners and for both partners on the witness.</span></span>  
  
 <span data-ttu-id="93a28-155">詳細については、「 [データベース ミラーリング エンドポイントで着信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="93a28-155">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md).</span></span>  
  
### <a name="creating-the-mirror-database"></a><span data-ttu-id="93a28-156">ミラー データベースの作成</span><span class="sxs-lookup"><span data-stu-id="93a28-156">Creating the Mirror Database</span></span>  
 <span data-ttu-id="93a28-157">ミラー データベースを作成する方法の詳細については、「 [ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="93a28-157">For information on how to create a mirror database, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
###  <a name="configuring-the-mirroring-partners"></a><a name="ConfigureMirroringPartners"></a> <span data-ttu-id="93a28-158">ミラーリング パートナーの構成</span><span class="sxs-lookup"><span data-stu-id="93a28-158">Configuring the Mirroring Partners</span></span>  
  
1.  <span data-ttu-id="93a28-159">HOST_B のミラー サーバー インスタンスで、HOST_A のサーバー インスタンスをパートナー (最初のプリンシパル サーバー インスタンス) として設定します。</span><span class="sxs-lookup"><span data-stu-id="93a28-159">On the mirror server instance on HOST_B, set the server instance on HOST_A as the partner (making it the initial principal server instance).</span></span> <span data-ttu-id="93a28-160">`TCP://HOST_A.Mydomain.Corp.Adventure-Works``.com:7024`の部分を有効なネットワーク アドレスに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="93a28-160">Substitute a valid network address for `TCP://HOST_A.Mydomain.Corp.Adventure-Works``.com:7024`.</span></span> <span data-ttu-id="93a28-161">詳細については、「 [サーバー ネットワーク アドレスの指定 &#40;データベース ミラーリング&#41;](specify-a-server-network-address-database-mirroring.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="93a28-161">For more information, see [Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md).</span></span>  
  
    ```  
    --At HOST_B, set server instance on HOST_A as partner (principal server):  
    ALTER DATABASE AdventureWorks   
        SET PARTNER = 'TCP://HOST_A.Mydomain.Corp.Adventure-Works.com:7024';  
    GO  
    ```  
  
2.  <span data-ttu-id="93a28-162">HOST_A のプリンシパル サーバー インスタンスで、HOST_B のサーバー インスタンスをパートナー (最初のミラー サーバー インスタンス) として設定します。</span><span class="sxs-lookup"><span data-stu-id="93a28-162">On the principal server instance on HOST_A, set the server instance on HOST_B as the partner (making it the initial mirror server instance).</span></span> <span data-ttu-id="93a28-163">`TCP://HOST_B.Mydomain.Corp.Adventure-Works.com:7024`の部分を有効なネットワーク アドレスに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="93a28-163">Substitute a valid network address for `TCP://HOST_B.Mydomain.Corp.Adventure-Works.com:7024`.</span></span>  
  
    ```  
    --At HOST_A, set server instance on HOST_B as partner (mirror server).  
    ALTER DATABASE AdventureWorks   
        SET PARTNER = 'TCP://HOST_B.Mydomain.Corp.Adventure-Works.com:7024';  
    GO  
    ```  
  
3.  <span data-ttu-id="93a28-164">この例では、セッションが高パフォーマンス モードで実行されると仮定します。</span><span class="sxs-lookup"><span data-stu-id="93a28-164">This example assumes that the session will be running in high-performance mode.</span></span> <span data-ttu-id="93a28-165">このセッションの実行モードを高パフォーマンス モードに構成するには、HOST_A のプリンシパル サーバー インスタンスでトランザクションの安全性を OFF に設定します。</span><span class="sxs-lookup"><span data-stu-id="93a28-165">To configure this session for high-performance mode, on the principal server instance (on HOST_A), set transaction safety to OFF.</span></span>  
  
    ```  
    --Change to high-performance mode by turning off transacton safety.  
    ALTER DATABASE AdventureWorks   
        SET PARTNER SAFETY OFF  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="93a28-166">自動フェールオーバーを伴う高い安全性モードで実行する場合は、トランザクションの安全性を FULL (既定の設定) のままにして、2番目の set PARTNER **' *`partner_server`* '** ステートメントを実行した後、できるだけ早くミラーリング監視サーバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="93a28-166">If you intend to run in high-safety mode with automatic failover, leave transaction safety set to FULL (the default setting) and add the witness as soon as possible after executing the second SET PARTNER **'*`partner_server`*'** statement.</span></span> <span data-ttu-id="93a28-167">ただし、まずミラーリング監視サーバーが発信接続と着信接続用に構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="93a28-167">Note that the witness must first be configured for outbound and inbound connections.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="93a28-168">関連タスク</span><span class="sxs-lookup"><span data-stu-id="93a28-168">Related Tasks</span></span>  
  
-   [<span data-ttu-id="93a28-169">ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="93a28-169">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
-   [<span data-ttu-id="93a28-170">データベース ミラーリング エンドポイントで着信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="93a28-170">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="93a28-171">データベース ミラーリング エンドポイントで発信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="93a28-171">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-outbound-connections.md)  
  
-   [<span data-ttu-id="93a28-172">役割の交代後のログインとジョブの管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="93a28-172">Management of Logins and Jobs After Role Switching &#40;SQL Server&#41;</span></span>](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md)  
  
-   <span data-ttu-id="93a28-173">[データベースを別のサーバー インスタンスで使用できるようにするときのメタデータの管理 &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md) (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="93a28-173">[Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md) (SQL Server)</span></span>  
  
-   [<span data-ttu-id="93a28-174">データベース ミラーリング構成のトラブルシューティング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="93a28-174">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](troubleshoot-database-mirroring-configuration-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="93a28-175">参照</span><span class="sxs-lookup"><span data-stu-id="93a28-175">See Also</span></span>  
 <span data-ttu-id="93a28-176">[データベースミラーリングと AlwaysOn 可用性グループ &#40;SQL Server のトランスポートセキュリティ&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="93a28-176">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="93a28-177">[サーバー ネットワーク アドレスの指定 &#40;データベース ミラーリング&#41;](specify-a-server-network-address-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="93a28-177">[Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md) </span></span>  
 <span data-ttu-id="93a28-178">[データベース ミラーリング エンドポイント &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="93a28-178">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="93a28-179">[データベース ミラーリング エンドポイントでの証明書の使用 &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="93a28-179">[Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md) </span></span>  
 <span data-ttu-id="93a28-180">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="93a28-180">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="93a28-181">SQL Server データベース エンジンと Azure SQL Database のセキュリティ センター</span><span class="sxs-lookup"><span data-stu-id="93a28-181">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
