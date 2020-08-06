---
title: データベース ミラーリング構成のトラブルシューティング (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- endpoints [SQL Server], database mirroring
- database mirroring [SQL Server], troubleshooting
- troubleshooting [SQL Server], database mirroring
ms.assetid: 87d3801b-dc52-419e-9316-8b1f1490946c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0dafd98f721bfc2d2d0dd64a9f97689466529407
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639650"
---
# <a name="troubleshoot-database-mirroring-configuration-sql-server"></a><span data-ttu-id="968f9-102">データベース ミラーリング構成のトラブルシューティング (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="968f9-102">Troubleshoot Database Mirroring Configuration (SQL Server)</span></span>
  <span data-ttu-id="968f9-103">ここでは、データベース ミラーリング セッションの設定時に発生する問題のトラブルシューティングに役立つ情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="968f9-103">This topic provides information to help you troubleshoot problems in setting up a database mirroring session.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="968f9-104">[データベース ミラーリングの前提条件](prerequisites-restrictions-and-recommendations-for-database-mirroring.md)をすべて満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="968f9-104">Ensure that you are meeting all the [prerequisites for database mirroring](prerequisites-restrictions-and-recommendations-for-database-mirroring.md).</span></span>  
  
|<span data-ttu-id="968f9-105">問題</span><span class="sxs-lookup"><span data-stu-id="968f9-105">Issue</span></span>|<span data-ttu-id="968f9-106">まとめ</span><span class="sxs-lookup"><span data-stu-id="968f9-106">Summary</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="968f9-107">エラー メッセージ 1418</span><span class="sxs-lookup"><span data-stu-id="968f9-107">Error Message 1418</span></span>|<span data-ttu-id="968f9-108">この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メッセージは、サーバー ネットワーク アドレスに到達できないか、そのアドレスが存在しないことを意味し、ネットワーク アドレス名を確認してコマンドを再実行するように示しています。</span><span class="sxs-lookup"><span data-stu-id="968f9-108">This [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] message indicates that the server network address cannot be reached or does not exist, and it suggests that you verify the network address name and reissue the command.</span></span> <span data-ttu-id="968f9-109">詳細については、「 [MSSQLSERVER_1418](../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="968f9-109">For more information, see the [MSSQLSERVER_1418](../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md) topic.</span></span>|  
|[<span data-ttu-id="968f9-110">Accounts</span><span class="sxs-lookup"><span data-stu-id="968f9-110">Accounts</span></span>](#Accounts)|<span data-ttu-id="968f9-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているアカウントを適切に構成するための要件について説明します。</span><span class="sxs-lookup"><span data-stu-id="968f9-111">Discusses requirements for correctly configuring the accounts under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>|  
|[<span data-ttu-id="968f9-112">エンドポイント</span><span class="sxs-lookup"><span data-stu-id="968f9-112">Endpoints</span></span>](#Endpoints)|<span data-ttu-id="968f9-113">各サーバー インスタンスのデータベース ミラーリング エンドポイントを適切に構成するための要件について説明します。</span><span class="sxs-lookup"><span data-stu-id="968f9-113">Discusses requirements for correctly configuring the database mirroring endpoint of each server instance.</span></span>|  
|[<span data-ttu-id="968f9-114">システム アドレス</span><span class="sxs-lookup"><span data-stu-id="968f9-114">SystemAddress</span></span>](#SystemAddress)|<span data-ttu-id="968f9-115">データベース ミラーリング構成でサーバー インスタンスのシステム名を指定するためのその他の方法について概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="968f9-115">Summarizes the alternatives for specifying the system name of a server instance in a database mirroring configuration.</span></span>|  
|[<span data-ttu-id="968f9-116">ネットワーク アクセス</span><span class="sxs-lookup"><span data-stu-id="968f9-116">Network access</span></span>](#NetworkAccess)|<span data-ttu-id="968f9-117">各サーバー インスタンスが他のサーバー インスタンスのポートに TCP 経由でアクセスできるという要件について説明します。</span><span class="sxs-lookup"><span data-stu-id="968f9-117">Documents the requirement that each the server instance be able to access the ports of the other server instance or instances over TCP.</span></span>|  
|[<span data-ttu-id="968f9-118">ミラー データベースの準備</span><span class="sxs-lookup"><span data-stu-id="968f9-118">Mirror database preparation</span></span>](#MirrorDbPrep)|<span data-ttu-id="968f9-119">ミラーリングを開始できるようにミラー データベースを準備する際の要件について概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="968f9-119">Summarizes the requirements for preparing the mirror database to enable mirroring to start.</span></span>|  
|[<span data-ttu-id="968f9-120">失敗したファイル作成操作</span><span class="sxs-lookup"><span data-stu-id="968f9-120">Failed create-file operation</span></span>](#FailedCreateFileOp)|<span data-ttu-id="968f9-121">失敗したファイル作成操作の対処方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="968f9-121">Describes how to respond to a failed create-file operation.</span></span>|  
|[<span data-ttu-id="968f9-122">Transact-SQL を使用したミラーリングの開始</span><span class="sxs-lookup"><span data-stu-id="968f9-122">Starting mirroring by Using Transact-SQL</span></span>](#StartDbm)|<span data-ttu-id="968f9-123">ALTER DATABASE *database_name* SET PARTNER **='***partner_server***'** ステートメントを実行する際に必要な順序について説明します。</span><span class="sxs-lookup"><span data-stu-id="968f9-123">Describes the required order for ALTER DATABASE *database_name* SET PARTNER **='***partner_server***'** statements.</span></span>|  
|[<span data-ttu-id="968f9-124">複数データベースにまたがるトランザクション</span><span class="sxs-lookup"><span data-stu-id="968f9-124">Cross-Database Transactions</span></span>](#CrossDbTxns)|<span data-ttu-id="968f9-125">自動フェールオーバーにより、状態が不明なトランザクションが自動的に解決されることがあります。ただし、この解決は不適切な場合があります。</span><span class="sxs-lookup"><span data-stu-id="968f9-125">An automatic failover could lead to automatic and possibly incorrect resolution of in-doubt transactions.</span></span> <span data-ttu-id="968f9-126">このため、データベース ミラーリングでは複数データベースにまたがるトランザクションをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="968f9-126">For this reason database mirroring does not support cross-database transactions.</span></span>|  
  
##  <a name="accounts"></a><a name="Accounts"></a> <span data-ttu-id="968f9-127">Accounts</span><span class="sxs-lookup"><span data-stu-id="968f9-127">Accounts</span></span>  
 <span data-ttu-id="968f9-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の実行に使用するアカウントは、正しく構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="968f9-128">The accounts under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running must be correctly configured.</span></span>  
  
1.  <span data-ttu-id="968f9-129">アカウントに適切な権限が与えられていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="968f9-129">Do the accounts have the correct permissions?</span></span>  
  
    1.  <span data-ttu-id="968f9-130">アカウントが同じドメインで実行されている場合、アカウントの構成が不適切になる可能性は低くなります。</span><span class="sxs-lookup"><span data-stu-id="968f9-130">If the accounts are running in the same domain accounts, the chances of misconfiguration are reduced.</span></span>  
  
    2.  <span data-ttu-id="968f9-131">アカウントが別のドメインで実行されているか、またはドメイン アカウントではない場合、もう一方のコンピューターの **master** データベースにアカウントのログインを作成する必要があります。また、そのログインには、エンドポイントに対して CONNECT 権限を与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="968f9-131">If the accounts are running in different domains or are not domain accounts, the login of one account must be created in **master** on the other computer, and that login must be granted CONNECT permissions on the endpoint.</span></span> <span data-ttu-id="968f9-132">詳細については、「 [データベースを別のサーバー インスタンスで使用できるようにするときのメタデータの管理 &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="968f9-132">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).</span></span> <span data-ttu-id="968f9-133">これには、ネットワーク サービス アカウントも含まれます。</span><span class="sxs-lookup"><span data-stu-id="968f9-133">This includes the Network Service account.</span></span>  
  
2.  <span data-ttu-id="968f9-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がローカル システム アカウントを使用しているサービスとして実行されている場合、認証には証明書を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="968f9-134">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running as a service that is using the local system account, you must use certificates for authentication.</span></span> <span data-ttu-id="968f9-135">詳細については、この後の「 [データベース ミラーリング エンドポイントでの証明書の使用 &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="968f9-135">For more information, see [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).</span></span>  
  
##  <a name="endpoints"></a><a name="Endpoints"></a> <span data-ttu-id="968f9-136">Endpoints</span><span class="sxs-lookup"><span data-stu-id="968f9-136">Endpoints</span></span>  
 <span data-ttu-id="968f9-137">エンドポイントが正しく構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="968f9-137">Endpoints must be correctly configured.</span></span>  
  
1.  <span data-ttu-id="968f9-138">各サーバー インスタンス (プリンシパル サーバー、ミラー サーバー、およびミラーリング監視サーバー (存在する場合)) にデータベース ミラーリング エンドポイントがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="968f9-138">Make sure that each server instance (the principal server, mirror server, and witness, if any) has a database mirroring endpoint.</span></span> <span data-ttu-id="968f9-139">詳細については、「[sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)」、および、認証形式によって、「[Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)」もしくは「[データベース ミラーリング エンドポイントでの証明書の使用 &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)」のいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="968f9-139">For more information, see [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) and, depending on the form of authentication, either [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) or [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).</span></span>  
  
2.  <span data-ttu-id="968f9-140">ポート番号が適切であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="968f9-140">Check that the port numbers are correct.</span></span>  
  
     <span data-ttu-id="968f9-141">サーバー インスタンスのデータベース ミラーリング エンドポイントに現在関連付けられているポートを識別するには、 [sys.database_mirroring_endpoints](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) カタログ ビューおよび [sys.tcp_endpoints](/sql/relational-databases/system-catalog-views/sys-tcp-endpoints-transact-sql) カタログ ビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="968f9-141">To identify the port currently associated with database mirroring endpoint of a server instance, use the [sys.database_mirroring_endpoints](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) and [sys.tcp_endpoints](/sql/relational-databases/system-catalog-views/sys-tcp-endpoints-transact-sql) catalog views.</span></span>  
  
3.  <span data-ttu-id="968f9-142">説明が困難なデータベース ミラーリングのセットアップに関する問題については、各サーバー インスタンスを調査して、それぞれが正しいポートでリッスンしているかどうかを確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="968f9-142">For database mirroring setup issues that are difficult to explain, we recommend that you inspect each server instance to determine whether it is listening on the correct ports.</span></span> <span data-ttu-id="968f9-143">ポートの可用性の検証については、「 [MSSQLSERVER_1418](../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="968f9-143">For information about verifying port availability, see [MSSQLSERVER_1418](../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md).</span></span>  
  
4.  <span data-ttu-id="968f9-144">エンドポイントが開始されていること (STATE = STARTED) を確認します。</span><span class="sxs-lookup"><span data-stu-id="968f9-144">Make sure that the endpoints are started (STATE=STARTED).</span></span> <span data-ttu-id="968f9-145">各サーバー インスタンスで、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="968f9-145">On each server instance, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
    ```  
    SELECT state_desc FROM sys.database_mirroring_endpoints  
    ```  
  
     <span data-ttu-id="968f9-146">**state_desc** 列の詳細については、「[sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="968f9-146">For more information about the **state_desc** column, see [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql).</span></span>  
  
     <span data-ttu-id="968f9-147">エンドポイントを開始するには、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="968f9-147">To start an endpoint, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
    ```  
    ALTER ENDPOINT Endpoint_Mirroring   
    STATE = STARTED   
    AS TCP (LISTENER_PORT = <port_number>)  
    FOR database_mirroring (ROLE = ALL);  
    GO  
    ```  
  
     <span data-ttu-id="968f9-148">詳細については、「 [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="968f9-148">For more information, see [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
5.  <span data-ttu-id="968f9-149">ROLE の設定が正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="968f9-149">Check that the ROLE is correct.</span></span> <span data-ttu-id="968f9-150">各サーバー インスタンスで、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="968f9-150">On each server instance use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
    ```  
    SELECT role FROM sys.database_mirroring_endpoints;  
    GO  
    ```  
  
     <span data-ttu-id="968f9-151">詳細については、「[sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="968f9-151">For more information, see [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql).</span></span>  
  
6.  <span data-ttu-id="968f9-152">他のサーバー インスタンスからサービス アカウントにログインするには、CONNECT 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="968f9-152">The login for the service account from the other server instance requires CONNECT permission.</span></span> <span data-ttu-id="968f9-153">他のサーバーからのログインに、CONNECT 権限があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="968f9-153">Make sure that the login from the other server has CONNECT permission.</span></span> <span data-ttu-id="968f9-154">あるエンドポイントに対して CONNECT 権限のあるユーザーを確認するには、各サーバー インスタンスで、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="968f9-154">To determine who has CONNECT permission for an endpoint, on each server instance use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
    ```  
    SELECT 'Metadata Check';  
    SELECT EP.name, SP.STATE,   
       CONVERT(nvarchar(38), suser_name(SP.grantor_principal_id))   
          AS GRANTOR,   
       SP.TYPE AS PERMISSION,  
       CONVERT(nvarchar(46),suser_name(SP.grantee_principal_id))   
          AS GRANTEE   
       FROM sys.server_permissions SP , sys.endpoints EP  
       WHERE SP.major_id = EP.endpoint_id  
       ORDER BY Permission,grantor, grantee;   
    GO  
  
    ```  
  
##  <a name="system-address"></a><a name="SystemAddress"></a> <span data-ttu-id="968f9-155">システム アドレス</span><span class="sxs-lookup"><span data-stu-id="968f9-155">System Address</span></span>  
 <span data-ttu-id="968f9-156">データベース ミラーリング構成におけるサーバー インスタンスのシステム名には、システムを明確に識別できる任意の名前を使用できます。</span><span class="sxs-lookup"><span data-stu-id="968f9-156">For the system name of a server instance in a database mirroring configuration, you can use any name that unambiguously identifies the system.</span></span> <span data-ttu-id="968f9-157">サーバー アドレスには、システム名 (システムが同じドメインに存在する場合)、完全修飾ドメイン名、または IP アドレス (可能であれば静的 IP アドレス) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="968f9-157">The server address can be a system name (if the systems are in the same domain), a fully qualified domain name, or an IP address (preferably, a static IP address).</span></span> <span data-ttu-id="968f9-158">完全修飾ドメイン名を使用すると動作が保証されます。</span><span class="sxs-lookup"><span data-stu-id="968f9-158">Using the fully qualified domain name is guaranteed to work.</span></span> <span data-ttu-id="968f9-159">詳細については、「 [サーバー ネットワーク アドレスの指定 &#40;データベース ミラーリング&#41;](specify-a-server-network-address-database-mirroring.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="968f9-159">For more information, see [Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md).</span></span>  
  
##  <a name="network-access"></a><a name="NetworkAccess"></a> <span data-ttu-id="968f9-160">Network Access</span><span class="sxs-lookup"><span data-stu-id="968f9-160">Network Access</span></span>  
 <span data-ttu-id="968f9-161">各サーバー インスタンスは、他のサーバー インスタンスのポートに TCP 経由でアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="968f9-161">Each server instance must be able to access the ports of the other server instance or instances over TCP.</span></span> <span data-ttu-id="968f9-162">これは、サーバー インスタンスが相互に信頼関係を持たない別のドメイン (信頼されていないドメイン) に存在する場合に特に重要になります。</span><span class="sxs-lookup"><span data-stu-id="968f9-162">This is especially important if the server instances are in different domains that do not trust each other (untrusted domains).</span></span> <span data-ttu-id="968f9-163">このような状況では、サーバー インスタンス間の通信の大半が制限されます。</span><span class="sxs-lookup"><span data-stu-id="968f9-163">This restricts much of the communication between the server instances.</span></span>  
  
##  <a name="mirror-database-preparation"></a><a name="MirrorDbPrep"></a> <span data-ttu-id="968f9-164">Mirror Database Preparation</span><span class="sxs-lookup"><span data-stu-id="968f9-164">Mirror Database Preparation</span></span>  
 <span data-ttu-id="968f9-165">ミラーリングを初めて開始する場合も、ミラーリングを削除した後に再度開始する場合も、ミラー データベースがミラーリング用に準備されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="968f9-165">Whether starting mirroring for the first time or starting it again after mirroring was removed, verify that the mirror database is prepared for mirroring.</span></span>  
  
 <span data-ttu-id="968f9-166">ミラー サーバーにミラー データベースを作成する際には、同じデータベース名と WITH NORECOVERY オプションを指定して、プリンシパル データベースのバックアップを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="968f9-166">When you create the mirror database on the mirror server, make sure that you restore the backup of the principal database specifying the same database name WITH NORECOVERY.</span></span> <span data-ttu-id="968f9-167">また、このバックアップが実行された後で作成されたすべてのログ バックアップについても、WITH NORECOVERY を指定して適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="968f9-167">Also, all log backups created after that backup was taken must also be applied, again WITH NORECOVERY.</span></span>  
  
 <span data-ttu-id="968f9-168">また、可能であれば、ミラー データベースのファイル パス (ドライブ文字を含む) を、プリンシパル データベースと同一のパスにすることが推奨されています。</span><span class="sxs-lookup"><span data-stu-id="968f9-168">Also, we recommend that, if it is possible, the file path (including the drive letter) of the mirror database be identical to the path of the principal database.</span></span> <span data-ttu-id="968f9-169">ファイルのパスが異なる場合、たとえば、プリンシパル データベースが "F:" ドライブに存在する一方で、ミラー システムに "F:" ドライブがない場合には、RESTORE ステートメントに MOVE オプションを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="968f9-169">If the file paths must differ, for example, if the principal database is on drive 'F:' but the mirror system lacks an F: drive, you must include the MOVE option in the RESTORE statement.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="968f9-170">ミラー データベースの作成時にデータベース ファイルを移動した場合、そのミラー データベースに後でファイルを追加する際に、ミラーリングの中断が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="968f9-170">If you move the database files when you are creating the mirror database, you might be unable to add files to the database later without mirroring being suspended.</span></span>  
  
 <span data-ttu-id="968f9-171">データベース ミラーリングが停止している場合にミラーリングを再開するには、停止後にプリンシパル データベースで作成されたすべてのログ バックアップをミラー データベースに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="968f9-171">If database mirroring has been stopped, all subsequent log backups taken on the principal database must be applied to the mirror database before mirroring can be restarted.</span></span>  
  
 <span data-ttu-id="968f9-172">詳細については、「 [ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="968f9-172">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
##  <a name="failed-create-file-operation"></a><a name="FailedCreateFileOp"></a> <span data-ttu-id="968f9-173">Failed Create-File Operation</span><span class="sxs-lookup"><span data-stu-id="968f9-173">Failed Create-File Operation</span></span>  
 <span data-ttu-id="968f9-174">ミラーリング セッションに影響を与えずにファイルを追加するには、追加するファイルのパスが両方のサーバーに存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="968f9-174">Adding a file without impacting a mirroring session requires that the path of the file exist on both servers.</span></span> <span data-ttu-id="968f9-175">したがって、ミラー データベースの作成時にデータベース ファイルを移動し、その後でミラー データベースにファイルを追加しようとした場合、ファイルの追加操作が失敗し、ミラーリングが中断されることがあります。</span><span class="sxs-lookup"><span data-stu-id="968f9-175">Therefore, if you move the database files when creating the mirror database, a later add-file operation might fail on the mirror database and cause mirroring to be suspended.</span></span>  
  
 <span data-ttu-id="968f9-176">この問題を解決するには、データベース所有者が次の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="968f9-176">To fix the problem:</span></span>  
  
1.  <span data-ttu-id="968f9-177">ミラーリング セッションを削除し、追加されたファイルを含むファイル グループの完全バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="968f9-177">The database owner must remove the mirroring session and restore a full backup of the filegroup that contains the added file.</span></span>  
  
2.  <span data-ttu-id="968f9-178">次に、ファイルを追加する操作を含むログをプリンシパル サーバーでバックアップし、WITH NORECOVERY オプションと WITH MOVE オプションを使用して、そのログ バックアップをミラー データベースに手動で復元します。</span><span class="sxs-lookup"><span data-stu-id="968f9-178">The owner must then back up the log containing the add-file operation on the principal server and manually restore the log backup on the mirror database using the WITH NORECOVERY and WITH MOVE options.</span></span> <span data-ttu-id="968f9-179">この操作を行うと、指定したファイル パスがミラー サーバーに作成され、その場所に新しいファイルが復元されます。</span><span class="sxs-lookup"><span data-stu-id="968f9-179">Doing this creates the specified file path on the mirror server and restores the new file to that location.</span></span>  
  
3.  <span data-ttu-id="968f9-180">新しいミラーリング セッションのためにデータベースを準備するには、WITH NORECOVERY オプションを使用して、プリンシパル サーバーでバックアップした他の未処理のログをすべて復元する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="968f9-180">To prepare the database for a new mirroring session, the owner must also restore WITH NO RECOVERY any other outstanding log backups from the principal server.</span></span>  
  
 <span data-ttu-id="968f9-181">詳細については、「[データベース ミラーリングの削除 &#40;SQL Server&#41;](database-mirroring-sql-server.md)」、「[ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)」、「[Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md)」、「[データベース ミラーリング エンドポイントでの証明書の使用&#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)」、「[Windows 認証を使用してデータベース ミラーリング セッションを確立する方法 &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)」のいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="968f9-181">For more information, see [Removing Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md), [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md), [Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md), [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md), or [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md).</span></span>  
  
##  <a name="starting-mirroring-by-using-transact-sql"></a><a name="StartDbm"></a><span data-ttu-id="968f9-182">Transact-sql を使用したミラーリングの開始</span><span class="sxs-lookup"><span data-stu-id="968f9-182">Starting mirroring by Using Transact-SQL</span></span>  
 <span data-ttu-id="968f9-183">ALTER DATABASE *database_name* SET PARTNER **='***partner_server***'** ステートメントを実行する際は、順序が非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="968f9-183">The order in which the ALTER DATABASE *database_name* SET PARTNER **='***partner_server***'** statements are issued is very important.</span></span>  
  
1.  <span data-ttu-id="968f9-184">最初のステートメントは、ミラー サーバーで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="968f9-184">The first statement must be run on the mirror server.</span></span> <span data-ttu-id="968f9-185">このステートメントの実行時に、ミラー サーバーでは他のサーバー インスタンスへの接続は試行されません。</span><span class="sxs-lookup"><span data-stu-id="968f9-185">When this statement is issued, the mirror server does not try to contact any other server instance.</span></span> <span data-ttu-id="968f9-186">ミラー サーバーは自身のデータベースに対し、プリンシパル サーバーからそのミラー サーバーへの接続が行われるまで待機するように指示します。</span><span class="sxs-lookup"><span data-stu-id="968f9-186">Instead, the mirror server instructs its database to wait until the mirror server has been contacted by the principal server.</span></span>  
  
2.  <span data-ttu-id="968f9-187">2 番目の ALTER DATABASE ステートメントはプリンシパル サーバーで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="968f9-187">The second ALTER DATABASE statement must be run on the principal server.</span></span> <span data-ttu-id="968f9-188">このステートメントにより、プリンシパル サーバーはミラー サーバーへの接続を試みます。</span><span class="sxs-lookup"><span data-stu-id="968f9-188">This statement causes the principal server to try to connect to the mirror server.</span></span> <span data-ttu-id="968f9-189">この接続が確立されると、ミラー サーバーは、さらに別の接続でプリンシパル サーバーへの接続を試みます。</span><span class="sxs-lookup"><span data-stu-id="968f9-189">After that connection is created, the mirror then tries to connect to the principal server on another connection.</span></span>  
  
 <span data-ttu-id="968f9-190">詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="968f9-190">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="968f9-191">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してミラーリングを開始する方法の詳細については、「[Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="968f9-191">For information about using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to start mirroring, see [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md).</span></span>  
  
##  <a name="cross-database-transactions"></a><a name="CrossDbTxns"></a><span data-ttu-id="968f9-192">複数データベースにまたがるトランザクション</span><span class="sxs-lookup"><span data-stu-id="968f9-192">Cross-Database Transactions</span></span>  
 <span data-ttu-id="968f9-193">データベースが自動フェールオーバーを伴う高い安全性モードでミラー化されている場合、自動フェールオーバーにより、状態が不明なトランザクションが自動的に解決されることがあります。ただし、この解決は不適切な場合があります。</span><span class="sxs-lookup"><span data-stu-id="968f9-193">When a database is being mirrored in high-safety mode with automatic failover, an automatic failover could lead to automatic and possibly incorrect resolution of in-doubt transactions.</span></span> <span data-ttu-id="968f9-194">複数データベースにまたがるトランザクションがコミットされているときに、いずれかのデータベースで自動フェールオーバーが発生すると、データベース間で論理的な不一致が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="968f9-194">If an automatic failover occurs on either database while a cross-database transaction is being committed, logical inconsistencies can occur between the databases.</span></span>  
  
 <span data-ttu-id="968f9-195">自動フェールオーバーの影響を受ける可能性がある、複数データベースにまたがるトランザクションには、次の種類があります。</span><span class="sxs-lookup"><span data-stu-id="968f9-195">The types of cross-database transactions that can be affected by an automatic failover include the following:</span></span>  
  
-   <span data-ttu-id="968f9-196">同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスで複数のデータベースを更新するトランザクション。</span><span class="sxs-lookup"><span data-stu-id="968f9-196">A transaction that is updating multiple databases in the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="968f9-197">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーター (MS DTC) を使用するトランザクション。</span><span class="sxs-lookup"><span data-stu-id="968f9-197">Transactions that use a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC).</span></span>  
  
 <span data-ttu-id="968f9-198">詳細については、「[データベース ミラーリングまたは AlwaysOn 可用性グループではサポートされない複数データベースにまたがるトランザクション &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="968f9-198">For more information, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="968f9-199">参照</span><span class="sxs-lookup"><span data-stu-id="968f9-199">See Also</span></span>  
 <span data-ttu-id="968f9-200">[データベース ミラーリングの設定 &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="968f9-200">[Setting Up Database Mirroring &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="968f9-201">データベースミラーリングと AlwaysOn 可用性グループ &#40;SQL Server のトランスポートセキュリティ&#41;</span><span class="sxs-lookup"><span data-stu-id="968f9-201">Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](transport-security-database-mirroring-always-on-availability.md)  
  
  
