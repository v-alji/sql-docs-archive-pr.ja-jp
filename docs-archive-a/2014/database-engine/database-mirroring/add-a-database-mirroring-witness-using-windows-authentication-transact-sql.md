---
title: Windows 認証の使用によるデータベースのミラーリング監視の追加 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- witness [SQL Server], establishing
- Windows authentication [SQL Server]
- database mirroring [SQL Server], witness
ms.assetid: bf5e87df-91a4-49f9-ae88-2a6dcf644510
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 88684c3a1ca12ea579859759ed804ca281647fa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634046"
---
# <a name="add-a-database-mirroring-witness-using-windows-authentication-transact-sql"></a><span data-ttu-id="7ffba-102">Windows 認証の使用によるデータベースのミラーリング監視の追加 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7ffba-102">Add a Database Mirroring Witness Using Windows Authentication (Transact-SQL)</span></span>
  <span data-ttu-id="7ffba-103">データベースのミラーリング監視を設定するには、データベース所有者が、データベース エンジンのインスタンスをミラーリング監視サーバーの役割に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="7ffba-103">To set up a witness for a database, the database owner assigns a Database Engine instance to the role of witness server.</span></span> <span data-ttu-id="7ffba-104">ミラーリング監視サーバーのインスタンスは、プリンシパル サーバーまたはミラー サーバーのインスタンスと同じコンピューターで実行できますが、このようにすると、自動フェールオーバーの堅牢性が大幅に低下します。</span><span class="sxs-lookup"><span data-stu-id="7ffba-104">The witness server instance can run on the same computer as the principal or mirror server instance, but this substantially reduces the robustness of automatic failover.</span></span>  
  
 <span data-ttu-id="7ffba-105">ミラーリング監視は独立したコンピューターに常駐させることを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7ffba-105">We strongly recommend that the witness reside on a separate computer.</span></span> <span data-ttu-id="7ffba-106">特定のサーバーを、同じパートナーまたは別のパートナーを含む複数の同時実行データベース ミラーリング セッションに参加させることができます。</span><span class="sxs-lookup"><span data-stu-id="7ffba-106">A given server can participate in multiple concurrent database mirroring sessions with the same or different partners.</span></span> <span data-ttu-id="7ffba-107">また、特定のサーバーを、あるセッションではパートナーとし、別のセッションではミラーリング監視にすることができます。</span><span class="sxs-lookup"><span data-stu-id="7ffba-107">A given server can be a partner in some sessions and a witness in other sessions.</span></span>  
  
 <span data-ttu-id="7ffba-108">ミラーリング監視は、自動フェールオーバーを伴う高い安全性モードでの使用だけが想定されています。</span><span class="sxs-lookup"><span data-stu-id="7ffba-108">The witness is intended exclusively for high-safety mode with automatic failover.</span></span> <span data-ttu-id="7ffba-109">ミラーリング監視を設定する前に、SAFETY プロパティが現在 FULL に設定されていることを確認するよう強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7ffba-109">Before you set a witness, we strongly recommend that you ensure that the SAFETY property is currently set to FULL.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7ffba-110">構成はパフォーマンスに影響する場合があるので、データベース ミラーリングの構成はピーク タイム以外の時間に行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7ffba-110">We recommend that you configure database mirroring during off-peak hours because configuration can impact performance.</span></span>  
  
### <a name="to-establish-a-witness"></a><span data-ttu-id="7ffba-111">ミラーリング監視を確立するには</span><span class="sxs-lookup"><span data-stu-id="7ffba-111">To establish a witness</span></span>  
  
1.  <span data-ttu-id="7ffba-112">ミラーリング監視サーバーのインスタンスで、データベース ミラーリングのエンドポイントが存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="7ffba-112">On the witness server instance, ensure that an endpoint exists for database mirroring.</span></span> <span data-ttu-id="7ffba-113">サポートされるミラーリング セッションの数に関係なく、サーバー インスタンスにはデータベース ミラーリング エンドポイントが 1 つだけ存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ffba-113">Regardless of the number of mirroring session to be supported, the server instance must have only one database mirroring endpoint.</span></span> <span data-ttu-id="7ffba-114">このサーバーインスタンスをデータベースミラーリングセッションでミラーリング監視サーバーとして排他的に使用する場合は、ミラーリング監視サーバーのロールをエンドポイント (ロール **=** 監視) に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="7ffba-114">If you intend to use this server instance exclusively as a witness in database mirroring sessions, assign the role of witness to the endpoint (ROLE **=** WITNESS).</span></span> <span data-ttu-id="7ffba-115">このサーバー インスタンスを 1 つ以上の他のデータベース ミラーリング セッションのパートナーとして使用する場合、エンドポイントの役割を ALL に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="7ffba-115">If you intend to use this server instance as a partner in one or more other database mirroring sessions, assign the role of the endpoint as ALL.</span></span>  
  
     <span data-ttu-id="7ffba-116">SET WITNESS ステートメントを実行するには、データベース ミラーリング セッションが (パートナー間で) 既に開始されていて、ミラーリング監視のエンドポイントの STATE が STARTED に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ffba-116">To execute a SET WITNESS statement, the database mirroring session must already be started (between the partners), and the STATE of the endpoint of the witness must be set to STARTED.</span></span>  
  
     <span data-ttu-id="7ffba-117">ミラーリング監視サーバーのインスタンスにデータベース ミラーリング エンドポイントがあるかどうかを把握し、そのエンドポイントの役割と状態を把握するには、インスタンスで次の Transact-SQL ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="7ffba-117">To learn whether the witness server instance has its database mirroring endpoint and to learn its role and state, on that instance, use the following Transact-SQL statement:</span></span>  
  
    ```  
    SELECT role_desc, state_desc FROM sys.database_mirroring_endpoints  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="7ffba-118">データベース ミラーリング エンドポイントが存在し、既に使用されている場合、サーバー インスタンスのすべてのセッションでそのエンドポイントを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7ffba-118">If a database mirroring endpoint exists and is already in use, we recommend that you use that endpoint for every session on the server instance.</span></span> <span data-ttu-id="7ffba-119">使用中のエンドポイントを削除すると、既存のセッションの接続が切断されます。</span><span class="sxs-lookup"><span data-stu-id="7ffba-119">Dropping an in-use endpoint disrupts the connections of the existing sessions.</span></span> <span data-ttu-id="7ffba-120">セッションにミラーリング監視サーバーが設定されている場合、データベース ミラーリングのエンドポイントを削除すると、そのセッションのプリンシパル サーバーがクォーラムを失う可能性があります。プリンシパル サーバーがクォーラムを失うと、データベースがオフラインになりユーザー接続が切断されます。</span><span class="sxs-lookup"><span data-stu-id="7ffba-120">If a witness has been set for a session, dropping the database mirroring endpoint can cause the principal server of that session to lose quorum; if that occurs, the database is taken offline and its users are disconnected.</span></span> <span data-ttu-id="7ffba-121">詳細については、「[クォーラム: データベースの可用性にミラーリング監視サーバーが与える影響 (データベース ミラーリング)](quorum-how-a-witness-affects-database-availability-database-mirroring.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ffba-121">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
     <span data-ttu-id="7ffba-122">ミラーリング監視にエンドポイントが存在しない場合は、「[Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ffba-122">If the witness lacks an endpoint, see [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).</span></span>  
  
2.  <span data-ttu-id="7ffba-123">パートナー インスタンスが異なるドメイン ユーザー アカウントで実行されている場合、各インスタンスの master データベースに別のアカウントのログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="7ffba-123">If the partner instances are running under different domain user accounts, create a login for the different accounts in the master database of each instance.</span></span> <span data-ttu-id="7ffba-124">詳細については、「 [Windows 認証を使用してデータベース ミラーリング エンドポイントへのネットワーク アクセスを許可する &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ffba-124">For more information, see [Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).</span></span>  
  
3.  <span data-ttu-id="7ffba-125">プリンシパル サーバーに接続し、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="7ffba-125">Connect to the principal server and issue the following statement:</span></span>  
  
     <span data-ttu-id="7ffba-126">ALTER DATABASE *<database_name>* SET 監視 **=** _<server_network_address>_</span><span class="sxs-lookup"><span data-stu-id="7ffba-126">ALTER DATABASE *<database_name>* SET WITNESS **=** _<server_network_address>_</span></span>  
  
     <span data-ttu-id="7ffba-127">*<database_name>* はミラー化するデータベースの名前 (両方のパートナーで同一の名前にします)、 *<server_network_address>* はミラーリング監視サーバー インスタンスのサーバー ネットワーク アドレスです。</span><span class="sxs-lookup"><span data-stu-id="7ffba-127">where *<database_name>* is the name of the database to be mirrored (this name is the same on both partners), and *<server_network_address>* is the server network address of the witness server instance.</span></span>  
  
     <span data-ttu-id="7ffba-128">サーバー ネットワーク アドレスの構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7ffba-128">The syntax for a server network address is as follows:</span></span>  
  
     <span data-ttu-id="7ffba-129">TCP:**//** \<_system-address> _**:**\<*port>\*</span><span class="sxs-lookup"><span data-stu-id="7ffba-129">TCP **://**\<_system-address>_**:**\<*port>\*</span></span>  
  
     <span data-ttu-id="7ffba-130">ここで、\<*system-address>\* は目的のコンピューター システムを明確に指定する文字列です。また、\<*port>\* はパートナー サーバー インスタンスのミラーリング エンドポイントで使用するポート番号です。</span><span class="sxs-lookup"><span data-stu-id="7ffba-130">where \<*system-address>\* is a string that unambiguously identifies the destination computer system, and \<*port>\* is the port number used by the mirroring endpoint of the partner server instance.</span></span> <span data-ttu-id="7ffba-131">詳細については、「 [サーバー ネットワーク アドレスの指定 &#40;データベース ミラーリング&#41;](specify-a-server-network-address-database-mirroring.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="7ffba-131">For more information, see [Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md).</span></span>  
  
     <span data-ttu-id="7ffba-132">たとえば、プリンシパル サーバー インスタンスでは、次の ALTER DATABASE ステートメントでミラーリング監視を設定します。</span><span class="sxs-lookup"><span data-stu-id="7ffba-132">For example, on the principal server instance, the following ALTER DATABASE statement sets the witness.</span></span> <span data-ttu-id="7ffba-133">データベース名は **AdventureWorks**、システム アドレスは DBSERVER3 (ミラーリング監視システムの名前)、ミラーリング監視のデータベース ミラーリング エンドポイントが使用するポートは `7022` です。</span><span class="sxs-lookup"><span data-stu-id="7ffba-133">The database name is **AdventureWorks**, the system address is DBSERVER3-the name of the witness system, and the port used by the database mirroring endpoint of the witness is `7022`:</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
      SET WITNESS = 'TCP://DBSERVER3:7022'  
    ```  
  
## <a name="example"></a><span data-ttu-id="7ffba-134">例</span><span class="sxs-lookup"><span data-stu-id="7ffba-134">Example</span></span>  
 <span data-ttu-id="7ffba-135">次の例では、データのミラーリング監視を確立します。</span><span class="sxs-lookup"><span data-stu-id="7ffba-135">The following example establishes a data mirroring witness.</span></span> <span data-ttu-id="7ffba-136">ミラーリング監視サーバー インスタンス ( `WITNESSHOST4`の既定のインスタンス) で、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="7ffba-136">On the witness server instance (default instance on `WITNESSHOST4`):</span></span>  
  
1.  <span data-ttu-id="7ffba-137">`7022`を使用する WITNESS の役割だけにこのサーバー インスタンスのエンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="7ffba-137">Create an endpoint for this server instance for the WITNESS role only using port `7022`.</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=WITNESS)  
    GO  
    ```  
  
2.  <span data-ttu-id="7ffba-138">パートナー インスタンスのドメイン ユーザー アカウントが異なる場合は、そのログインを作成します。たとえば、ミラーリング監視サーバーが `SOMEDOMAIN\witnessuser`で実行されていて、パートナーが `MYDOMAIN\dbousername`で実行されている場合などです。</span><span class="sxs-lookup"><span data-stu-id="7ffba-138">Create a login for domain user account of partner instances, if different; for example, assume that the witness is running as `SOMEDOMAIN\witnessuser`, but the partners are running as `MYDOMAIN\dbousername`.</span></span> <span data-ttu-id="7ffba-139">パートナーのログインを作成するには、以下のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="7ffba-139">Create a login for the partners, as follows:</span></span>  
  
    ```  
    --Create a login for the partner server instances,  
    --which are both running as MYDOMAIN\dbousername:  
    USE master ;  
    GO  
    CREATE LOGIN [MYDOMAIN\dbousername] FROM WINDOWS ;  
    GO  
    --Grant connect permissions on endpoint to login account   
    --of partners  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [MYDOMAIN\dbousername];  
    GO  
    ```  
  
3.  <span data-ttu-id="7ffba-140">各パートナー サーバー インスタンスで、ミラーリング監視サーバー インスタンスのログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="7ffba-140">On each of the partner server instances, create a login for the witness server instance:</span></span>  
  
    ```  
    --Create a login for the witness server instance,  
    --which is running as SOMEDOMAIN\witnessuser:  
    USE master ;  
    GO  
    CREATE LOGIN [SOMEDOMAIN\witnessuser] FROM WINDOWS ;  
    GO  
    --Grant connect permissions on endpoint to login account   
    --of partners  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [SOMEDOMAIN\witnessuser];  
    GO  
    ```  
  
4.  <span data-ttu-id="7ffba-141">プリンシパル サーバーで、ミラーリング監視サーバー ( `WITNESSHOST4`) を設定します。</span><span class="sxs-lookup"><span data-stu-id="7ffba-141">On the principal server, set the witness (which is on `WITNESSHOST4`):</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
        SET WITNESS =   
        'TCP://WITNESSHOST4:7022'  
    GO  
    ```  
  
> [!NOTE]  
>  <span data-ttu-id="7ffba-142">サーバー ネットワーク アドレスはターゲット サーバー インスタンスを、インスタンスのミラーリング エンドポイントにマップされるポート番号で示します。</span><span class="sxs-lookup"><span data-stu-id="7ffba-142">The server network address indicates the target server instance by the port number, which maps to the mirroring endpoint of the instance.</span></span>  
  
 <span data-ttu-id="7ffba-143">セキュリティの設定、ミラー データベースの準備、パートナーの設定、およびミラーリング監視サーバーの追加をすべて含む例については、「[データベース ミラーリングの設定 &#40;SQL Server&#41;](database-mirroring-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ffba-143">For a complete example showing security setup, preparing the mirror database, setting up the partners, and adding a witness, see [Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ffba-144">参照</span><span class="sxs-lookup"><span data-stu-id="7ffba-144">See Also</span></span>  
 <span data-ttu-id="7ffba-145">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7ffba-145">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="7ffba-146">[Windows 認証を使用してデータベース ミラーリング エンドポイントへのネットワーク アクセスを許可する &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="7ffba-146">[Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md) </span></span>  
 <span data-ttu-id="7ffba-147">[Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="7ffba-147">[Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span></span>  
 <span data-ttu-id="7ffba-148">[Windows 認証を使用してデータベース ミラーリング セッションを確立する方法 &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="7ffba-148">[Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md) </span></span>  
 <span data-ttu-id="7ffba-149">[データベース ミラーリング セッションからのミラーリング監視サーバーの削除 &#40;SQL Server&#41;](remove-the-witness-from-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7ffba-149">[Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;](remove-the-witness-from-a-database-mirroring-session-sql-server.md) </span></span>  
 [<span data-ttu-id="7ffba-150">データベース ミラーリング監視サーバー</span><span class="sxs-lookup"><span data-stu-id="7ffba-150">Database Mirroring Witness</span></span>](database-mirroring-witness.md)  
  
  
