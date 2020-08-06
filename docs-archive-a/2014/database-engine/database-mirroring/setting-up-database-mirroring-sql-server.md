---
title: データベース ミラーリングの設定 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
ms.assetid: da45efed-55eb-4c71-be34-ac2589dfce8d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7e55e973ffbb888394d13578f21e08a08ae9d03c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641845"
---
# <a name="setting-up-database-mirroring-sql-server"></a><span data-ttu-id="2a4e2-102">データベース ミラーリングの設定 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2a4e2-102">Setting Up Database Mirroring (SQL Server)</span></span>
  <span data-ttu-id="2a4e2-103">ここでは、データベース ミラーリングを設定するための前提条件、推奨事項、および手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-103">This section describes the prerequisites, recommendations, and steps for setting up database mirroring.</span></span> <span data-ttu-id="2a4e2-104">データベース ミラーリングの概要については、「 [データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-104">For an introduction to database mirroring, see [Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2a4e2-105">構成はパフォーマンスに影響する場合があるので、データベース ミラーリングの構成はピーク タイム以外の時間に行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-105">We recommend that you configure database mirroring during off-peak hours because configuration can impact performance.</span></span>  
  
 
  
##  <a name="preparing-a-server-instance-to-host-a-mirror-server"></a><a name="PrepareInstances"></a> <span data-ttu-id="2a4e2-106">ミラー サーバーをホストするサーバー インスタンスの準備</span><span class="sxs-lookup"><span data-stu-id="2a4e2-106">Preparing a Server Instance to Host a Mirror Server</span></span>  
 <span data-ttu-id="2a4e2-107">各データベース ミラーリング セッションで、以下を実行します。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-107">For each database mirroring session:</span></span>  
  
1.  <span data-ttu-id="2a4e2-108">プリンシパル サーバー、ミラー サーバー、およびミラーリング監視サーバー (存在する場合) は、別々のホスト システムにある別々のサーバー インスタンスによってホストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-108">The principal server, mirror server, and witness, if any, must be hosted by separate server instances, which should be on separate host systems.</span></span> <span data-ttu-id="2a4e2-109">サーバー インスタンスは、それぞれがデータベース ミラーリング エンドポイントを必要とします。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-109">Each of the server instances requires a database mirroring endpoint.</span></span> <span data-ttu-id="2a4e2-110">データベース ミラーリング エンドポイントを作成する必要がある場合は、他のサーバー インスタンスもそのエンドポイントにアクセス可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-110">If you need to create a database mirroring endpoint, ensure that it is accessible to the other server instances.</span></span>  
  
     <span data-ttu-id="2a4e2-111">サーバー インスタンスによりデータベースのミラーリングに使用される認証の形式は、データベース ミラーリング エンドポイントのプロパティで指定します。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-111">The form of authentication used for database mirroring by a server instance is a property of its database mirroring endpoint.</span></span> <span data-ttu-id="2a4e2-112">データベース ミラーリングのトランスポートには、Windows 認証と証明書ベースの認証の 2 種類のセキュリティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-112">Two types of transport security are available for database mirroring: Windows Authentication or certificate-based authentication.</span></span> <span data-ttu-id="2a4e2-113">詳細については、「[データベースミラーリングのトランスポートセキュリティ」および「AlwaysOn 可用性グループ &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-113">For more information, see [Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md).</span></span>  
  
     <span data-ttu-id="2a4e2-114">ネットワーク アクセスの要件は、次に示すように、認証の形式に固有です。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-114">The requirements for network access are specific to the form of authentication, as follows:</span></span>  
  
    -   <span data-ttu-id="2a4e2-115">**Windows 認証を使用する場合**</span><span class="sxs-lookup"><span data-stu-id="2a4e2-115">**If using Windows Authentication**</span></span>  
  
         <span data-ttu-id="2a4e2-116">サーバー インスタンスが別のドメイン ユーザー アカウントで実行されている場合、それぞれに他方のインスタンスの **master** データベースのログインが必要になります。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-116">If server instances are running under different domain user accounts, each requires a login in the **master** database of the others.</span></span> <span data-ttu-id="2a4e2-117">ログインが存在しない場合は、作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-117">If the login does not exist, you must create it.</span></span> <span data-ttu-id="2a4e2-118">詳細については、「 [Windows 認証を使用してデータベース ミラーリング エンドポイントへのネットワーク アクセスを許可する &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-118">For more information, see [Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).</span></span>  
  
    -   <span data-ttu-id="2a4e2-119">**証明書を使用する場合**</span><span class="sxs-lookup"><span data-stu-id="2a4e2-119">**If using certificates**</span></span>  
  
         <span data-ttu-id="2a4e2-120">あるサーバー インスタンスのデータベース ミラーリングで証明書による認証を有効にするには、システム管理者は、各サーバー インスタンスが発信接続と着信接続の両方で証明書を使用するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-120">To enable certificate authentication for database mirroring on a given server instance, the system administrator must configure each server instance to use certificates on both outbound and inbound connections.</span></span> <span data-ttu-id="2a4e2-121">この場合、発信接続を最初に構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-121">Outbound connections must be configured first.</span></span> <span data-ttu-id="2a4e2-122">詳細については、この後の「 [データベース ミラーリング エンドポイントでの証明書の使用 &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-122">For more information, see [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).</span></span>  
  
2.  <span data-ttu-id="2a4e2-123">すべてのデータベース ユーザーのログインが、ミラー サーバーに存在するようにします。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-123">Make sure that logins exist on the mirror server for all the database users.</span></span> <span data-ttu-id="2a4e2-124">詳細については、「[データベースミラーリングのログインアカウントの設定」または「AlwaysOn 可用性グループ &#40;SQL Server&#41;](set-up-login-accounts-database-mirroring-always-on-availability.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-124">For more information, see [Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](set-up-login-accounts-database-mirroring-always-on-availability.md).</span></span>  
  
3.  <span data-ttu-id="2a4e2-125">ミラー データベースをホストするサーバー インスタンスで、ミラー化されたデータベースで必要な残りの環境を設定します。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-125">On the server instance that will host the mirror database, set up the rest of the environment that is required for the mirrored database.</span></span> <span data-ttu-id="2a4e2-126">詳細については、「 [データベースを別のサーバー インスタンスで使用できるようにするときのメタデータの管理 &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-126">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
##  <a name="overview-establishing-a-database-mirroring-session"></a><a name="EstablishUsingWinAuthentication"></a> <span data-ttu-id="2a4e2-127">概要: データベース ミラーリング セッションの確立</span><span class="sxs-lookup"><span data-stu-id="2a4e2-127">Overview: Establishing a Database Mirroring Session</span></span>  
 <span data-ttu-id="2a4e2-128">ミラーリング セッションを確立するための基本手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-128">The basic steps for establishing a mirroring session are as follows:</span></span>  
  
1.  <span data-ttu-id="2a4e2-129">次のバックアップを復元することで、ミラー データベースを作成します。すべての復元操作で RESTORE WITH NORECOVERY を使用します。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-129">Create the mirror database by restoring the following backups, using RESTORE WITH NORECOVERY on every restore operation:</span></span>  
  
    1.  <span data-ttu-id="2a4e2-130">プリンシパル データベースのバックアップ作成時に、プリンシパル データベースで完全復元モデルが既に使用されていたことを確認した後、プリンシパル データベースの完全バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-130">Restore a recent full database backup of the principal database, after making sure that the principal database was already using the full recovery model when the backup was taken.</span></span> <span data-ttu-id="2a4e2-131">ミラー データベースとプリンシパル データベースの名前は同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-131">The mirror database must have the same name as the principal database.</span></span>  
  
    2.  <span data-ttu-id="2a4e2-132">完全バックアップの復元後に、データベースの差分バックアップを作成している場合は、最新の差分バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-132">If you have taken any differential backups of the database since the restored full backup, restore your most recent differential backup.</span></span>  
  
    3.  <span data-ttu-id="2a4e2-133">データベースの完全バックアップまたは差分バックアップの作成後に行われたログ バックアップをすべて復元します。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-133">Restore all the log backups done since the full or differential database backup.</span></span>  
  
     <span data-ttu-id="2a4e2-134">詳細については、「 [ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-134">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2a4e2-135">プリンシパル データベースのバックアップを作成してから、可能な限り早い時点に残りの設定手順を完了します。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-135">Complete the remaining setup steps as soon as you can after taking the backup of the principal database.</span></span> <span data-ttu-id="2a4e2-136">パートナー上でミラーリングを開始するには、元のデータベースの現在のログ バックアップを作成し、ミラー データベースになるデータベースに復元しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-136">Before you can start mirroring on the partners, you should create a current log backup on the original database and restore it to the future mirror database.</span></span>  
  
2.  <span data-ttu-id="2a4e2-137">データベース ミラーリングは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] またはデータベース ミラーリング ウィザードを使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-137">You can set up mirroring by using either [!INCLUDE[tsql](../../includes/tsql-md.md)] or the Database Mirroring Wizard.</span></span> <span data-ttu-id="2a4e2-138">詳細については、以下のいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-138">For more information, see one of the following:</span></span>  
  
    -   [<span data-ttu-id="2a4e2-139">Windows 認証を使用してデータベース ミラーリング セッションを確立する方法 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-139">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
  
    -   [<span data-ttu-id="2a4e2-140">Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-140">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
3.  <span data-ttu-id="2a4e2-141">既定ではセッションでのトランザクションの安全性が "完全" に設定され (SAFETY が FULL に設定された状態)、同期セッションが自動フェールオーバーを伴わない高い安全性モードで開始されます。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-141">By default a session is set to full transaction safety (SAFETY is set to FULL), which starts the session in synchronous, high-safety mode without automatic failover.</span></span> <span data-ttu-id="2a4e2-142">セッションは、次のように自動フェールオーバーを伴う高い安全性モードか、非同期の高パフォーマンス モードで実行するように再構成できます。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-142">You can reconfigure the session to run in high-safety mode with automatic failover or in asynchronous, high-performance mode, as follows:</span></span>  
  
    -   <span data-ttu-id="2a4e2-143">**自動フェールオーバーを伴う高い安全性モード**</span><span class="sxs-lookup"><span data-stu-id="2a4e2-143">**High-safety mode with automatic failover**</span></span>  
  
         <span data-ttu-id="2a4e2-144">自動フェールオーバーをサポートするために高い安全性モードでセッションを実行する場合は、ミラーリング監視サーバー インスタンスを追加します。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-144">If you want a high-safety mode session to support automatic failover, add a witness server instance.</span></span>  
  
         <span data-ttu-id="2a4e2-145">**ミラーリング監視サーバーを追加するには**</span><span class="sxs-lookup"><span data-stu-id="2a4e2-145">**To add a witness**</span></span>  
  
        -   [<span data-ttu-id="2a4e2-146">Windows 認証を使用してデータベースのミラーリング監視を追加する &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-146">Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
        -   [<span data-ttu-id="2a4e2-147">Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-147">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
        > [!NOTE]  
        >  <span data-ttu-id="2a4e2-148">データベース所有者は、いつでもデータベースのミラーリング監視サーバーを無効にできます。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-148">The database owner can turn off the witness for a database at any time.</span></span> <span data-ttu-id="2a4e2-149">ミラーリング監視サーバーを無効にすると、ミラーリングの監視が行われない状態になり、自動フェールオーバーは行われません。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-149">Turning off the witness is equivalent to having no witness, and automatic failover cannot occur.</span></span>  
  
    -   <span data-ttu-id="2a4e2-150">**高パフォーマンス モード**</span><span class="sxs-lookup"><span data-stu-id="2a4e2-150">**High-performance mode**</span></span>  
  
         <span data-ttu-id="2a4e2-151">自動フェールオーバーを行わず、高可用性よりパフォーマンスを重視する場合は、トランザクションの安全性を無効にします。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-151">Alternatively, if you do not want automatic failover and you prefer to emphasize performance over availability, turn off transaction safety.</span></span> <span data-ttu-id="2a4e2-152">詳細については、｢[データベース ミラーリング セッションでのトランザクションの安全性の変更 &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-152">For more information, see [Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md).</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="2a4e2-153">高パフォーマンス モードでは、WITNESS を OFF に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-153">In high-performance mode, WITNESS needs to be set to OFF.</span></span> <span data-ttu-id="2a4e2-154">詳細については、「[クォーラム: データベースの可用性にミラーリング監視サーバーが与える影響 (データベース ミラーリング)](quorum-how-a-witness-affects-database-availability-database-mirroring.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-154">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a4e2-155">[!INCLUDE[tsql](../../includes/tsql-md.md)] での Microsoft Windows 認証を使用したデータベース ミラーリングの設定例については、「[Windows 認証を使用したデータベース ミラーリングの設定の例 &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-155">For an example of using [!INCLUDE[tsql](../../includes/tsql-md.md)] to set up database mirroring using Microsoft Windows Authentication, see [Example: Setting Up Database Mirroring Using Windows Authentication &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md).</span></span>  
>   
>  <span data-ttu-id="2a4e2-156">[!INCLUDE[tsql](../../includes/tsql-md.md)] での証明書ベースのセキュリティを使用したデータベース ミラーリングの設定例については、「[証明書を使用したデータベース ミラーリングの設定の例 &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-156">For an example of using [!INCLUDE[tsql](../../includes/tsql-md.md)] to set up database mirroring using certificate-based security, see [Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md).</span></span>  
  
 
  
##  <a name="in-this-section"></a><a name="InThisSection"></a> <span data-ttu-id="2a4e2-157">トピックの内容</span><span class="sxs-lookup"><span data-stu-id="2a4e2-157">In This Section</span></span>  
 [<span data-ttu-id="2a4e2-158">ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-158">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](prepare-a-mirror-database-for-mirroring-sql-server.md)  
 <span data-ttu-id="2a4e2-159">中断されたセッションを再開する前に、ミラー データベースを作成したりミラー データベースを準備するための手順についてまとめています。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-159">Summarizes the steps for creating a mirror database or preparing a mirror database before resuming a suspended session.</span></span> <span data-ttu-id="2a4e2-160">また、操作方法に関するトピックへのリンクも示します。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-160">Also provides links to how-to topics.</span></span>  
  
 [<span data-ttu-id="2a4e2-161">サーバー ネットワーク アドレスの指定 &#40;データベース ミラーリング&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-161">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](specify-a-server-network-address-database-mirroring.md)  
 <span data-ttu-id="2a4e2-162">サーバー ネットワーク アドレスの構文、そのアドレスによってサーバー インスタンスのデータベース ミラーリング エンドポイントがどのように識別されるか、およびシステムの完全修飾ドメイン名を検索する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-162">Describes the syntax of a server network address, how the address identifies the database mirroring endpoint of the server instance, and how to find the fully-qualified domain name of a system.</span></span>  
  
 [<span data-ttu-id="2a4e2-163">Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-163">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
 <span data-ttu-id="2a4e2-164">データベース ミラーリング セキュリティ構成ウィザードを使用してデータベース ミラーリングを開始する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-164">Describes how to use the Configure Database Mirroring Security Wizard to start database mirroring on a database.</span></span>  
  
 [<span data-ttu-id="2a4e2-165">Windows 認証を使用してデータベース ミラーリング セッションを確立する方法 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-165">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
 <span data-ttu-id="2a4e2-166">データベース ミラーリングを設定するための [!INCLUDE[tsql](../../includes/tsql-md.md)] の手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-166">Describes the [!INCLUDE[tsql](../../includes/tsql-md.md)] steps for setting up database mirroring.</span></span>  
  
 [<span data-ttu-id="2a4e2-167">例:Windows 認証を使用したデータベース ミラーリングの設定 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-167">Example: Setting Up Database Mirroring Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md)  
 <span data-ttu-id="2a4e2-168">Windows 認証を使用してミラーリング監視サーバーを利用するデータベース ミラーリング セッションを作成する場合に必要なすべての段階の例を示します。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-168">Contains an example of all the stages required to create a database mirroring session with a witness, using Windows Authentication.</span></span>  
  
 [<span data-ttu-id="2a4e2-169">例:証明書を使用したデータベース ミラーリングの設定 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-169">Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;</span></span>](example-setting-up-database-mirroring-using-certificates-transact-sql.md)  
 <span data-ttu-id="2a4e2-170">証明書ベースの認証を使用してミラーリング監視サーバーを利用するデータベース ミラーリング セッションを作成する場合に必要なすべての段階の例を示します。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-170">Contains an example of all the stages required to create a database mirroring session with a witness, using certificate-based authentication.</span></span>  
  
 [<span data-ttu-id="2a4e2-171">データベースミラーリングまたは AlwaysOn 可用性グループ &#40;SQL Server のログインアカウントを設定&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-171">Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](set-up-login-accounts-database-mirroring-always-on-availability.md)  
 <span data-ttu-id="2a4e2-172">ローカル サーバー インスタンスと異なるアカウントを使用しているリモート サーバー インスタンスのログインの作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="2a4e2-172">Describes creating a login for a remote server instance that is using a different account than the local server instance.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="2a4e2-173">関連タスク</span><span class="sxs-lookup"><span data-stu-id="2a4e2-173">Related Tasks</span></span>  
 <span data-ttu-id="2a4e2-174">**SQL Server Management Studio**</span><span class="sxs-lookup"><span data-stu-id="2a4e2-174">**SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="2a4e2-175">データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-175">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
-   [<span data-ttu-id="2a4e2-176">Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-176">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
 <span data-ttu-id="2a4e2-177">**Transact-SQL**</span><span class="sxs-lookup"><span data-stu-id="2a4e2-177">**Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="2a4e2-178">Windows 認証を使用してデータベース ミラーリング エンドポイントへのネットワーク アクセスを許可する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-178">Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;</span></span>](../database-mirroring-allow-network-access-windows-authentication.md)  
  
-   [<span data-ttu-id="2a4e2-179">データベース ミラーリング エンドポイントで発信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-179">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-outbound-connections.md)  
  
-   [<span data-ttu-id="2a4e2-180">データベース ミラーリング エンドポイントで着信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-180">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="2a4e2-181">Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-181">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="2a4e2-182">Windows 認証を使用してデータベース ミラーリング セッションを確立する方法 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-182">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
  
-   [<span data-ttu-id="2a4e2-183">Windows 認証を使用してデータベースのミラーリング監視を追加する &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-183">Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="2a4e2-184">TRUSTWORTHY プロパティを使用するようにミラー データベースを設定する方法 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-184">Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;</span></span>](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)  
  
 <span data-ttu-id="2a4e2-185">**Transact-SQL/SQL Server Management Studio**</span><span class="sxs-lookup"><span data-stu-id="2a4e2-185">**Transact-SQL/SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="2a4e2-186">サーバー インスタンスのアップグレード時に、ミラー化されたデータベースのダウンタイムを最小化する方法</span><span class="sxs-lookup"><span data-stu-id="2a4e2-186">Minimize Downtime for Mirrored Databases When Upgrading Server Instances</span></span>](upgrading-mirrored-instances.md)  
  
-   [<span data-ttu-id="2a4e2-187">ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-187">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
-   [<span data-ttu-id="2a4e2-188">データベース ミラーリング構成のトラブルシューティング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-188">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](troubleshoot-database-mirroring-configuration-sql-server.md)  
  
 
  
## <a name="see-also"></a><span data-ttu-id="2a4e2-189">参照</span><span class="sxs-lookup"><span data-stu-id="2a4e2-189">See Also</span></span>  
 <span data-ttu-id="2a4e2-190">[データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2a4e2-190">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="2a4e2-191">[データベース ミラーリング: 相互運用性と共存 &#40;SQL Server&#41;](database-mirroring-interoperability-and-coexistence-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2a4e2-191">[Database Mirroring: Interoperability and Coexistence &#40;SQL Server&#41;](database-mirroring-interoperability-and-coexistence-sql-server.md) </span></span>  
 <span data-ttu-id="2a4e2-192">[データベースミラーリングと AlwaysOn 可用性グループ &#40;SQL Server のトランスポートセキュリティ&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="2a4e2-192">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 [<span data-ttu-id="2a4e2-193">サーバー ネットワーク アドレスの指定 &#40;データベース ミラーリング&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4e2-193">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](specify-a-server-network-address-database-mirroring.md)  
  
  
