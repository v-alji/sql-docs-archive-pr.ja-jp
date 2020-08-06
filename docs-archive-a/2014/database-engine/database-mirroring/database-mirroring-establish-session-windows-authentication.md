---
title: Windows 認証を使用してデータベースミラーリングセッションを確立する (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Windows authentication [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 143c68a5-589f-4e7f-be59-02707e1a430a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f3088333fbfd4babd209df07f8880c838ce626d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632686"
---
# <a name="establish-a-database-mirroring-session-using-windows-authentication-transact-sql"></a><span data-ttu-id="137bc-102">Windows 認証を使用してデータベース ミラーリング セッションを確立する方法 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="137bc-102">Establish a Database Mirroring Session Using Windows Authentication (Transact-SQL)</span></span>
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] <span data-ttu-id="137bc-103">代わりに [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="137bc-103">Use [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] instead.</span></span>  
  
 <span data-ttu-id="137bc-104">ミラー データベースを準備した後 (「 [ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)」を参照)、データベース ミラーリング セッションを確立できます。</span><span class="sxs-lookup"><span data-stu-id="137bc-104">After the mirror database is prepared (see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)), you can establish a database mirroring session.</span></span> <span data-ttu-id="137bc-105">プリンシパル サーバー、ミラー サーバー、およびミラーリング監視サーバーのインスタンスは、別々のホスト システムにある別々のサーバー インスタンスでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="137bc-105">The principal, mirror, and witness server instances must be separate server instances, which should be on separate host systems.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="137bc-106">ミラーリングの構成はパフォーマンスに影響する場合があるので、データベース ミラーリングの構成はピーク タイム以外の時間に行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="137bc-106">We recommend that you configure database mirroring during off-peak hours because configuring mirroring can impact performance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="137bc-107">特定のサーバー インスタンスを、同じパートナーまたは別のパートナーを含む複数の同時実行データベース ミラーリング セッションに参加させることができます。</span><span class="sxs-lookup"><span data-stu-id="137bc-107">A given server instance can participate in multiple concurrent database mirroring sessions with the same or different partners.</span></span> <span data-ttu-id="137bc-108">また、サーバー インスタンスを、あるセッションではパートナーとし、別のセッションではミラーリング監視にすることができます。</span><span class="sxs-lookup"><span data-stu-id="137bc-108">A server instance can be a partner in some sessions and a witness in other sessions.</span></span> <span data-ttu-id="137bc-109">ミラー サーバー インスタンスでは、プリンシパル サーバー インスタンスと同じエディションの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="137bc-109">The mirror server instance must be running the same edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as the principal server instance.</span></span> <span data-ttu-id="137bc-110">データベース ミラーリングは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="137bc-110">Database mirroring is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="137bc-111">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="137bc-111">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="137bc-112">また、ワークロードの処理能力が同程度のシステム上で運用することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="137bc-112">Also, we strongly recommend that they run on comparable systems that can handle identical workloads.</span></span>  
  
### <a name="to-establish-a-database-mirroring-session"></a><span data-ttu-id="137bc-113">データベース ミラーリング セッションを確立するには</span><span class="sxs-lookup"><span data-stu-id="137bc-113">To establish a database mirroring session</span></span>  
  
1.  <span data-ttu-id="137bc-114">ミラー データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="137bc-114">Create the mirror database.</span></span> <span data-ttu-id="137bc-115">詳細については、「 [ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="137bc-115">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="137bc-116">各サーバー インスタンスにセキュリティを設定します。</span><span class="sxs-lookup"><span data-stu-id="137bc-116">Set up security on each server instance.</span></span>  
  
     <span data-ttu-id="137bc-117">データベース ミラーリング セッションの各サーバー インスタンスには、データベース ミラーリング エンドポイントが必要です。</span><span class="sxs-lookup"><span data-stu-id="137bc-117">Each server instance in a database mirroring session requires a database mirroring endpoint.</span></span> <span data-ttu-id="137bc-118">エンドポイントが存在しない場合は、作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="137bc-118">If the endpoint does not exist, you must create it.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="137bc-119">サーバー インスタンスによりデータベースのミラーリングに使用される認証の形式は、データベース ミラーリング エンドポイントのプロパティで指定します。</span><span class="sxs-lookup"><span data-stu-id="137bc-119">The form of authentication used for database mirroring by a server instance is a property of its database mirroring endpoint.</span></span> <span data-ttu-id="137bc-120">データベース ミラーリングのトランスポートには、Windows 認証と証明書ベースの認証の 2 種類のセキュリティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="137bc-120">Two types of transport security are available for database mirroring: Windows Authentication or certificate-based authentication.</span></span> <span data-ttu-id="137bc-121">詳細については、「[データベースミラーリングのトランスポートセキュリティ」および「AlwaysOn 可用性グループ &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="137bc-121">For more information, see [Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md).</span></span>  
  
     <span data-ttu-id="137bc-122">各パートナー サーバーで、データベース ミラーリング用のエンドポイントが存在していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="137bc-122">On each partner server, ensure that an endpoint exists for database mirroring.</span></span> <span data-ttu-id="137bc-123">サポートするミラーリング セッションの数にかかわらず、サーバー インスタンスではデータベース ミラーリング エンドポイントを 1 つしか持つことができません。</span><span class="sxs-lookup"><span data-stu-id="137bc-123">Regardless of the number of mirroring sessions to be supported, the server instance can have only one database mirroring endpoint.</span></span> <span data-ttu-id="137bc-124">このサーバー インスタンスをデータベース ミラーリング セッションでパートナー専用に使用する場合は、パートナーのロールをエンドポイントに割り当てることができます (ROLE **=** PARTNER)。</span><span class="sxs-lookup"><span data-stu-id="137bc-124">If you intend to use this server instance exclusively for partners in database mirroring sessions, you can assign the role of partner to the endpoint (ROLE**=** PARTNER).</span></span> <span data-ttu-id="137bc-125">また、このサーバーを他のデータベース ミラーリング セッションのミラーリング監視サーバーとしても使用する場合は、エンドポイントのロールを ALL として割り当てます。</span><span class="sxs-lookup"><span data-stu-id="137bc-125">If you intend also to use this server for the witness in other database mirroring sessions, assign the role of the endpoint as ALL.</span></span>  
  
     <span data-ttu-id="137bc-126">SET PARTNER ステートメントを実行するには、両方のパートナーのエンドポイントの STATE が、STARTED に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="137bc-126">To execute a SET PARTNER statement, the STATE of the endpoints of both partners must be set to STARTED.</span></span>  
  
     <span data-ttu-id="137bc-127">サーバー インスタンスにデータベース ミラーリング エンドポイントがあるかどうかを調べて、そのロールと状態を確認するには、そのインスタンスで、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="137bc-127">To learn whether a server instance has a database mirroring endpoint and to learn its role and state, on that instance, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    SELECT role_desc, state_desc FROM sys.database_mirroring_endpoints  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="137bc-128">使用中のデータベース ミラーリング エンドポイントは再構成しないでください。</span><span class="sxs-lookup"><span data-stu-id="137bc-128">Do not reconfigure an in-use database mirroring endpoint.</span></span> <span data-ttu-id="137bc-129">データベース ミラーリング エンドポイントが存在し、既に使用されている場合、サーバー インスタンスのすべてのセッションでそのエンドポイントを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="137bc-129">If a database mirroring endpoint exists and is already in use, we recommend that you use that endpoint for every session on the server instance.</span></span> <span data-ttu-id="137bc-130">使用中のエンドポイントを削除すると、そのエンドポイントが再起動され、既存のセッションの接続が切断される場合があります。この場合、他のサーバー インスタンスからはエラーが発生したように見える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="137bc-130">Dropping an in-use endpoint can cause the endpoint to restart, disrupting the connections of the existing sessions, which can appear to be an error to the other server instances.</span></span> <span data-ttu-id="137bc-131">これは、自動フェールオーバーを伴う高い安全性モードでは特に重要です。この場合、パートナーでエンドポイントを再構成すると、フェールオーバーの原因になることがあります。</span><span class="sxs-lookup"><span data-stu-id="137bc-131">This is particularly important in high-safety mode with automatic failover, in which reconfiguring the endpoint on a partner could cause a failover to occur.</span></span> <span data-ttu-id="137bc-132">また、セッションにミラーリング監視サーバーが設定されている場合、データベース ミラーリング エンドポイントを削除すると、そのセッションのプリンシパル サーバーがクォーラムを失う可能性があります。プリンシパル サーバーがクォーラムを失うと、データベースがオフラインになりユーザー接続が切断されます。</span><span class="sxs-lookup"><span data-stu-id="137bc-132">Also, if a witness has been set for a session, dropping the database mirroring endpoint can cause the principal server of that session to lose quorum; if that occurs, the database is taken offline and its users are disconnected.</span></span> <span data-ttu-id="137bc-133">詳細については、「[クォーラム: データベースの可用性にミラーリング監視サーバーが与える影響 (データベース ミラーリング)](quorum-how-a-witness-affects-database-availability-database-mirroring.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="137bc-133">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
     <span data-ttu-id="137bc-134">いずれかのパートナーにエンドポイントがない場合は、「[Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="137bc-134">If either partner lacks an endpoint, see [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).</span></span>  
  
3.  <span data-ttu-id="137bc-135">サーバー インスタンスが別のドメイン ユーザー アカウントで実行されている場合、それぞれに他方のインスタンスの **master** データベースのログインが必要になります。</span><span class="sxs-lookup"><span data-stu-id="137bc-135">If server instances are running under different domain user accounts, each requires a login in the **master** database of the others.</span></span> <span data-ttu-id="137bc-136">ログインが存在しない場合は、作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="137bc-136">If the login does not exist, you must create it.</span></span> <span data-ttu-id="137bc-137">詳細については、「 [Windows 認証を使用してデータベース ミラーリング エンドポイントへのネットワーク アクセスを許可する &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="137bc-137">For more information, see [Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).</span></span>  
  
4.  <span data-ttu-id="137bc-138">プリンシパル サーバーをミラー データベースのパートナーとして設定するには、ミラー サーバーに接続し、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="137bc-138">To set the principal server as partner on the mirror database, connect to the mirror server, and issue the following statement:</span></span>  
  
     <span data-ttu-id="137bc-139">ALTER DATABASE *<database_name>* SET PARTNER **=** _<server_network_address>_</span><span class="sxs-lookup"><span data-stu-id="137bc-139">ALTER DATABASE *<database_name>* SET PARTNER **=**_<server_network_address>_</span></span>  
  
     <span data-ttu-id="137bc-140">ここで *<database_name>* はミラー化されるデータベースの名前 (両方のパートナーで同じ名前になります)、および *<server_network_address*>はプリンシパルサーバーのサーバーネットワークアドレスです。</span><span class="sxs-lookup"><span data-stu-id="137bc-140">where *<database_name>* is the name of the database to be mirrored (this name is the same on both partners), and *<server_network_address>* is the server network address of the principal server.</span></span>  
  
     <span data-ttu-id="137bc-141">サーバー ネットワーク アドレスの構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="137bc-141">The syntax for a server network address is as follows:</span></span>  
  
     <span data-ttu-id="137bc-142">TCP:<strong>//</strong> \<*system-address> \*<strong>:</strong> \<*port> \*</span><span class="sxs-lookup"><span data-stu-id="137bc-142">TCP<strong>://</strong>\<*system-address>*<strong>:</strong>\<*port>*</span></span>  
  
     <span data-ttu-id="137bc-143">ここで、\<*system-address>\* は目的のコンピューター システムを明確に指定する文字列です。また、\<*port>\* はパートナー サーバー インスタンスのミラーリング エンドポイントで使用するポート番号です。</span><span class="sxs-lookup"><span data-stu-id="137bc-143">where \<*system-address>\* is a string that unambiguously identifies the destination computer system, and \<*port>\* is the port number used by the mirroring endpoint of the partner server instance.</span></span> <span data-ttu-id="137bc-144">詳細については、「 [サーバー ネットワーク アドレスの指定 &#40;データベース ミラーリング&#41;](specify-a-server-network-address-database-mirroring.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="137bc-144">For more information, see [Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md).</span></span>  
  
     <span data-ttu-id="137bc-145">たとえば、ミラーリング サーバー インスタンスで、次の ALTER DATABASE ステートメントは元のプリンシパル サーバー インスタンスとしてパートナーを設定します。</span><span class="sxs-lookup"><span data-stu-id="137bc-145">For example, on the mirror server instance, the following ALTER DATABASE statement sets the partner as the original principal server instance.</span></span> <span data-ttu-id="137bc-146">データベース名は **AdventureWorks**、システムのアドレスは DBSERVER1 (パートナーのシステム名)、パートナーのデータベース ミラーリング エンドポイントが使用するポートは 7022 です。</span><span class="sxs-lookup"><span data-stu-id="137bc-146">The database name is **AdventureWorks**, the system address is DBSERVER1-the name of the partner's system-and the port used by the partner's database mirroring endpoint is 7022:</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
       SET PARTNER = 'TCP://DBSERVER1:7022'  
    ```  
  
     <span data-ttu-id="137bc-147">このステートメントを実行すると、プリンシパル サーバーからの接続時にミラー サーバーにセッションを確立する準備が整います。</span><span class="sxs-lookup"><span data-stu-id="137bc-147">This statement prepares the mirror server to form a session when it is contacted by the principal server.</span></span>  
  
5.  <span data-ttu-id="137bc-148">ミラー サーバーをプリンシパル データベースのパートナーとして設定するには、プリンシパル サーバーに接続し、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="137bc-148">To set the mirror server as partner on the principal database, connect to the principal server, and issue the following statement:</span></span>  
  
     <span data-ttu-id="137bc-149">ALTER DATABASE *<database_name>* SET PARTNER **=** _<server_network_address>_</span><span class="sxs-lookup"><span data-stu-id="137bc-149">ALTER DATABASE *<database_name>* SET PARTNER **=**_<server_network_address>_</span></span>  
  
     <span data-ttu-id="137bc-150">詳細については、手順 4. を参照してください。</span><span class="sxs-lookup"><span data-stu-id="137bc-150">For more information, see step 4.</span></span>  
  
     <span data-ttu-id="137bc-151">たとえば、プリンシパル サーバー インスタンスで、次の ALTER DATABASE ステートメントは元のミラー サーバー インスタンスとしてパートナーを設定します。</span><span class="sxs-lookup"><span data-stu-id="137bc-151">For example, on the principal server instance, the following ALTER DATABASE statement sets the partner as the original mirror server instance.</span></span> <span data-ttu-id="137bc-152">データベース名は **AdventureWorks**、システムのアドレスは DBSERVER2 (パートナーのシステム名)、パートナーのデータベースのミラーリング エンドポイントが使用するポートは 7025 です。</span><span class="sxs-lookup"><span data-stu-id="137bc-152">The database name is **AdventureWorks**, the system address is DBSERVER2-the name of the partner's system-and the port used by the partner's database mirroring endpoint is 7025:</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks SET PARTNER = 'TCP://DBSERVER2:7022'  
    ```  
  
     <span data-ttu-id="137bc-153">プリンシパル サーバーでこのステートメントを入力すると、データベース ミラーリング セッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="137bc-153">Entering this statement on the principal server begins the database mirroring session.</span></span>  
  
6.  <span data-ttu-id="137bc-154">既定ではセッションでのトランザクションの安全性が "完全" に設定され (SAFETY が FULL に設定された状態)、同期セッションが自動フェールオーバーを伴わない高い安全性モードで開始されます。</span><span class="sxs-lookup"><span data-stu-id="137bc-154">By default a session is set to full transaction safety (SAFETY is set to FULL), which starts the session in synchronous, high-safety mode without automatic failover.</span></span> <span data-ttu-id="137bc-155">セッションは、次のように自動フェールオーバーを伴う高い安全性モードか、非同期の高パフォーマンス モードで実行するように再構成できます。</span><span class="sxs-lookup"><span data-stu-id="137bc-155">You can reconfigure the session to run in high-safety mode with automatic failover or in asynchronous, high-performance mode, as follows:</span></span>  
  
    -   <span data-ttu-id="137bc-156">**自動フェールオーバーを伴う高い安全性モード**</span><span class="sxs-lookup"><span data-stu-id="137bc-156">**High-safety mode with automatic failover**</span></span>  
  
         <span data-ttu-id="137bc-157">自動フェールオーバーをサポートするために高い安全性モードでセッションを実行する場合は、ミラーリング監視サーバー インスタンスを追加します。</span><span class="sxs-lookup"><span data-stu-id="137bc-157">If you want a high-safety mode session to support automatic failover, add a witness server instance.</span></span> <span data-ttu-id="137bc-158">詳細については、「[Windows 認証の使用によるデータベースのミラーリング監視の追加 &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="137bc-158">For more information, see [Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md).</span></span>  
  
    -   <span data-ttu-id="137bc-159">**高パフォーマンス モード**</span><span class="sxs-lookup"><span data-stu-id="137bc-159">**High-performance mode**</span></span>  
  
         <span data-ttu-id="137bc-160">自動フェールオーバーを行わず、高可用性よりパフォーマンスを重視する場合は、トランザクションの安全性を無効にします。</span><span class="sxs-lookup"><span data-stu-id="137bc-160">Alternatively, if you do not want automatic failover and you prefer to emphasize performance over availability, turn off transaction safety.</span></span> <span data-ttu-id="137bc-161">詳細については、｢[データベース ミラーリング セッションでのトランザクションの安全性の変更 &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="137bc-161">For more information, see [Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md).</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="137bc-162">高パフォーマンス モードでは、WITNESS を OFF に設定してください。</span><span class="sxs-lookup"><span data-stu-id="137bc-162">In high-performance mode, WITNESS should be set to OFF.</span></span> <span data-ttu-id="137bc-163">詳細については、「[クォーラム: データベースの可用性にミラーリング監視サーバーが与える影響 (データベース ミラーリング)](quorum-how-a-witness-affects-database-availability-database-mirroring.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="137bc-163">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="137bc-164">例</span><span class="sxs-lookup"><span data-stu-id="137bc-164">Example</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="137bc-165">次の例では、既存のミラー データベースのためにパートナー間にデータベース ミラーリング セッションを確立します。</span><span class="sxs-lookup"><span data-stu-id="137bc-165">The following example establishes a database mirroring session between partners for an existing mirror database.</span></span> <span data-ttu-id="137bc-166">ミラー データベースを作成する方法の詳細については、「 [ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="137bc-166">For information on creating a mirror database, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)=.</span></span>  
  
 <span data-ttu-id="137bc-167">ミラーリング監視サーバーを使用せずにデータベース ミラーリング セッションを作成するための基本的な手順を示します。</span><span class="sxs-lookup"><span data-stu-id="137bc-167">The example shows the basic steps for creating a database mirroring session without a witness.</span></span> <span data-ttu-id="137bc-168">2 つのパートナーは、2 台のコンピューター システムにある既定のサーバー インスタンスです (PARTNERHOST1 および PARTNERHOST5)。</span><span class="sxs-lookup"><span data-stu-id="137bc-168">The two partners are the default server instances on two computer systems (PARTNERHOST1 and PARTNERHOST5).</span></span> <span data-ttu-id="137bc-169">2 つのパートナー インスタンスは、同一の Windows ドメイン ユーザー アカウント (MYDOMAIN\dbousername) で実行されます。</span><span class="sxs-lookup"><span data-stu-id="137bc-169">The two partner instances run the same Windows domain user account (MYDOMAIN\dbousername).</span></span>  
  
1.  <span data-ttu-id="137bc-170">プリンシパル サーバー インスタンス (PARTNERHOST1 の既定のインスタンス) で、ポート 7022 を使用するすべてのロールをサポートするエンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="137bc-170">On the principal server instance (default instance on PARTNERHOST1), create an endpoint that supports all roles using port 7022:</span></span>  
  
    ```  
    --create an endpoint for this instance  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO  
    --Partners under same domain user; login already exists in master.  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="137bc-171">ログインをセットアップする方法の例は、「 [Windows 認証を使用してデータベース ミラーリング エンドポイントへのネットワーク アクセスを許可する &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md)のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="137bc-171">For an example of how to setup a login, see [Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).</span></span>  
  
2.  <span data-ttu-id="137bc-172">ミラー サーバー インスタンス (PARTNERHOST5 の既定のインスタンス) で、ポート 7022 を使用するすべてのロールをサポートするエンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="137bc-172">On the mirror server instance (default instance on PARTNERHOST5), create an endpoint that supports all roles using port 7022:</span></span>  
  
    ```  
    --create an endpoint for this instance  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO  
    --Partners under same domain user; login already exists in master.  
    ```  
  
3.  <span data-ttu-id="137bc-173">プリンシパル サーバー インスタンス (PARTNERHOST1) で、データベースをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="137bc-173">On the principal server instance (on PARTNERHOST1), back up the database:</span></span>  
  
    ```  
    BACKUP DATABASE AdventureWorks   
        TO DISK = 'C:\AdvWorks_dbmirror.bak'   
        WITH FORMAT  
    GO  
    ```  
  
4.  <span data-ttu-id="137bc-174">ミラー サーバー インスタンス ( `PARTNERHOST5`) で、データベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="137bc-174">On the mirror server instance (on `PARTNERHOST5`), restore the database:</span></span>  
  
    ```  
    RESTORE DATABASE AdventureWorks   
        FROM DISK = 'Z:\AdvWorks_dbmirror.bak'   
        WITH NORECOVERY  
    GO  
    ```  
  
5.  <span data-ttu-id="137bc-175">完全データベース バックアップを作成した後、プリンシパル データベースでログ バックアップを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="137bc-175">After you create the full database backup, you must create a log backup on the principal database.</span></span> <span data-ttu-id="137bc-176">たとえば、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントは、前回の完全データベース バックアップで使用したものと同じファイルにログをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="137bc-176">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement backs up the log to the same file used by the preceding database backup:</span></span>  
  
    ```  
    BACKUP LOG AdventureWorks   
        TO DISK = 'C:\AdventureWorks.bak'   
    GO  
    ```  
  
6.  <span data-ttu-id="137bc-177">ミラーリングを開始する前に、必要なログ バックアップ (および、それ以降のログ バックアップ) を適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="137bc-177">Before you can start mirroring, you must apply the required log backup (and any subsequent log backups).</span></span>  
  
     <span data-ttu-id="137bc-178">たとえば、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントは C:\AdventureWorks.bak から最初のログを復元します。</span><span class="sxs-lookup"><span data-stu-id="137bc-178">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement restores the first log from C:\AdventureWorks.bak:</span></span>  
  
    ```  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\ AdventureWorks.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    ```  
  
7.  <span data-ttu-id="137bc-179">ミラー サーバー インスタンスで、PARTNERHOST1 のサーバー インスタンスをパートナーとして設定します (初期プリンシパル サーバーにします)。</span><span class="sxs-lookup"><span data-stu-id="137bc-179">On the mirror server instance, set the server instance on PARTNERHOST1 as the partner (making it the initial principal server):</span></span>  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks   
        SET PARTNER =   
        'TCP://PARTNERHOST1:7022'  
    GO  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="137bc-180">既定でデータベース ミラーリング セッションは、トランザクションの安全性が「完全」に設定された (SAFETY が FULL に設定された) 状態の同期モードで実行されます。</span><span class="sxs-lookup"><span data-stu-id="137bc-180">default, a database mirroring session runs in synchronous mode, which depends on having full transaction safety (SAFETY is set to FULL).</span></span> <span data-ttu-id="137bc-181">セッションを非同期の高パフォーマンス モードで実行するには、SAFETY を OFF にします。</span><span class="sxs-lookup"><span data-stu-id="137bc-181">To cause a session to run in asynchronous, high-performance mode, set SAFETY to OFF.</span></span> <span data-ttu-id="137bc-182">詳しくは、「 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="137bc-182">For more information, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
8.  <span data-ttu-id="137bc-183">プリンシパル サーバー インスタンスで、 `PARTNERHOST5` のサーバー インスタンスをパートナーとして設定します (初期ミラー サーバーにします)。</span><span class="sxs-lookup"><span data-stu-id="137bc-183">On the principal server instance, set the server instance on `PARTNERHOST5` as the partner (making it the initial mirror server):</span></span>  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks   
        SET PARTNER = 'TCP://PARTNERHOST5:7022'  
    GO  
    ```  
  
9. <span data-ttu-id="137bc-184">自動フェールオーバーを伴う高い安全性モードを使用する場合、必要に応じてミラーリング監視サーバー インスタンスを設定します。</span><span class="sxs-lookup"><span data-stu-id="137bc-184">Optionally, if you intend to use high-safety mode with automatic failover, set up the witness server instance.</span></span> <span data-ttu-id="137bc-185">詳細については、「[Windows 認証の使用によるデータベースのミラーリング監視の追加 &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="137bc-185">For more information, see [Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="137bc-186">セキュリティの設定、ミラー データベースの準備、パートナーの設定、およびミラーリング監視サーバーの追加をすべて含む例については、「[データベース ミラーリングの設定 &#40;SQL Server&#41;](database-mirroring-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="137bc-186">For a complete example showing security setup, preparing the mirror database, setting up the partners, and adding a witness, see [Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="137bc-187">参照</span><span class="sxs-lookup"><span data-stu-id="137bc-187">See Also</span></span>  
 <span data-ttu-id="137bc-188">[データベース ミラーリングの設定 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="137bc-188">[Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="137bc-189">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="137bc-189">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="137bc-190">[Windows 認証を使用してデータベース ミラーリング エンドポイントへのネットワーク アクセスを許可する &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="137bc-190">[Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md) </span></span>  
 <span data-ttu-id="137bc-191">[ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="137bc-191">[Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="137bc-192">[Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="137bc-192">[Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span></span>  
 <span data-ttu-id="137bc-193">[データベース ミラーリングとログ配布 &#40;SQL Server&#41;](database-mirroring-and-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="137bc-193">[Database Mirroring and Log Shipping &#40;SQL Server&#41;](database-mirroring-and-log-shipping-sql-server.md) </span></span>  
 <span data-ttu-id="137bc-194">[データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="137bc-194">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="137bc-195">[データベース ミラーリングとレプリケーション &#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="137bc-195">[Database Mirroring and Replication &#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md) </span></span>  
 <span data-ttu-id="137bc-196">[データベース ミラーリングの設定 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="137bc-196">[Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="137bc-197">[サーバー ネットワーク アドレスの指定 &#40;データベース ミラーリング&#41;](specify-a-server-network-address-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="137bc-197">[Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md) </span></span>  
 [<span data-ttu-id="137bc-198">Database Mirroring Operating Modes</span><span class="sxs-lookup"><span data-stu-id="137bc-198">Database Mirroring Operating Modes</span></span>](database-mirroring-operating-modes.md)  
  
  
