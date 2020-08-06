---
title: Windows 認証を使用してデータベースミラーリングセッションを確立する (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], sessions
ms.assetid: 7cb418d6-dce1-4a0d-830e-9c5ccfe3bd72
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a2f0b748ee8c639c6e64a2f530bfe1f05418dada
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632666"
---
# <a name="establish-a-database-mirroring-session-using-windows-authentication-sql-server-management-studio"></a><span data-ttu-id="91d27-102">Windows 認証を使用してデータベース ミラーリング セッションを確立する (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="91d27-102">Establish a Database Mirroring Session Using Windows Authentication (SQL Server Management Studio)</span></span>
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] <span data-ttu-id="91d27-103">代わりに [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="91d27-103">Use [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] instead.</span></span>  
  
 <span data-ttu-id="91d27-104">データベース ミラーリング セッションを確立したり、特定のデータベースについてデータベース ミラーリングのプロパティを変更するには、 **[データベースのプロパティ]** ダイアログ ボックスの **[ミラーリング]** ページを使用します。 **[ミラーリング]** ページを使用してデータベース ミラーリングを構成する前に、次の要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="91d27-104">To establish a database mirroring session and to modify the properties of database mirroring for a database, use the **Mirroring** page of the **Database Properties** dialog box.Before you use the **Mirroring** page to configure database mirroring, ensure that the following requirements have been met:</span></span>  
  
-   <span data-ttu-id="91d27-105">プリンシパル サーバー インスタンスおよびミラー サーバー インスタンスでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の同じエディション (Standard または Enterprise) を実行している必要があります。</span><span class="sxs-lookup"><span data-stu-id="91d27-105">The principal and mirror server instances must be running the same edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-either Standard or Enterprise.</span></span> <span data-ttu-id="91d27-106">また、ワークロードの処理能力が同程度のシステム上で運用することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="91d27-106">Also, we strongly recommend that they run on comparable systems that can handle identical workloads.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="91d27-107">ミラーリング監視サーバー インスタンスは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="91d27-107">A witness server instance is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="91d27-108">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91d27-108">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="91d27-109">ミラー データベースが存在し、最新状態である必要があります。</span><span class="sxs-lookup"><span data-stu-id="91d27-109">The mirror database must exist and be current.</span></span>  
  
     <span data-ttu-id="91d27-110">ミラー データベースを作成するには、ミラー サーバー インスタンス上でプリンシパル データベースの最新のバックアップを (WITH NORECOVERY を使用して) 復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91d27-110">Creating a mirror database requires restoring a recent backup of the principal database (using WITH NORECOVERY) on the mirror server instance.</span></span> <span data-ttu-id="91d27-111">また、完全バックアップの後に 1 つ以上のログ バックアップを取得し、(WITH NORECOVERY を使用して) これらのバックアップを順にミラー データベースに復元する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="91d27-111">It also requires taking one or more log backups after the full backup and restoring them in sequence to the mirror database (using WITH NORECOVERY).</span></span> <span data-ttu-id="91d27-112">詳細については、「 [ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="91d27-112">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
-   <span data-ttu-id="91d27-113">サーバー インスタンスが別のドメイン ユーザー アカウントで実行されている場合、それぞれに他方のインスタンスの **master** データベースのログインが必要になります。</span><span class="sxs-lookup"><span data-stu-id="91d27-113">If the server instances are running under different domain user accounts, each requires a login in the **master** database of the others.</span></span> <span data-ttu-id="91d27-114">ログインが存在しない場合は、作成してからミラーリングを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91d27-114">If the login does not exist, you must create it before configuring mirroring.</span></span> <span data-ttu-id="91d27-115">詳細については、「 [Windows 認証を使用してデータベース ミラーリング エンドポイントへのネットワーク アクセスを許可する &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91d27-115">For more information, see [Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).</span></span>  
  
### <a name="to-configure-database-mirroring"></a><span data-ttu-id="91d27-116">データベース ミラーリングを構成するには</span><span class="sxs-lookup"><span data-stu-id="91d27-116">To configure database mirroring</span></span>  
  
1.  <span data-ttu-id="91d27-117">プリンシパル サーバー インスタンスに接続した後、オブジェクト エクスプローラーでサーバー名をクリックして、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="91d27-117">After connecting to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="91d27-118">**[データベース]** を展開し、ミラー化するデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="91d27-118">Expand **Databases**, and select the database to be mirrored.</span></span>  
  
3.  <span data-ttu-id="91d27-119">データベースを右クリックして **[タスク]** を選択し、 **[ミラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="91d27-119">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="91d27-120">**[データベースのプロパティ]** ダイアログ ボックスの **[ミラーリング]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="91d27-120">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="91d27-121">ミラーリングの構成を開始するには、 **[セキュリティの構成]** をクリックして、データベース ミラーリング セキュリティ構成ウィザードを起動します。</span><span class="sxs-lookup"><span data-stu-id="91d27-121">To begin configuring mirroring, click the **Configure Security** button to launch the Configure Database Mirroring Security Wizard.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="91d27-122">データベース ミラーリング セッションでは、このウィザードだけを使用して、ミラーリング監視サーバー インスタンスを追加または変更できます。</span><span class="sxs-lookup"><span data-stu-id="91d27-122">During a database mirroring session, you can use this wizard only to add or change the witness server instance.</span></span>  
  
5.  <span data-ttu-id="91d27-123">データベース ミラーリング セキュリティ構成ウィザードでは、各サーバー インスタンス上にデータベース ミラーリング エンドポイントが存在しない場合は自動的に作成され、サーバー インスタンスのロールに対応するフィールド ("**プリンシパル**"、" **ミラー**"、または " **ミラーリング監視**") にサーバー ネットワーク アドレスが入力されます。</span><span class="sxs-lookup"><span data-stu-id="91d27-123">The Configure Database Mirroring Security Wizard automatically creates the database mirroring endpoint (if none exists) on each server instance, and enters the server network addresses in the field corresponding to the role of the server instance (**Principal**, **Mirror**, or **Witness**).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="91d27-124">エンドポイントを作成すると、データベース ミラーリング セキュリティ構成ウィザードでは、常に Windows 認証が使用されます。</span><span class="sxs-lookup"><span data-stu-id="91d27-124">When creating an endpoint, the Configure Database Mirroring Security Wizard always uses Windows Authentication.</span></span> <span data-ttu-id="91d27-125">証明書ベースの認証でウィザードを使用する前に、各サーバー インスタンスで証明書を使用するようにミラーリング エンドポイントを構成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="91d27-125">Before you can use the wizard with certificate-based authentication, the mirroring endpoint must already have been configured to use certificates on each of the server instances.</span></span> <span data-ttu-id="91d27-126">また、ウィザードの **[サービス アカウント]** ダイアログ ボックスのフィールドはすべて空のままにしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="91d27-126">Also, all the fields of the wizard's **Service Accounts** dialog box must remain empty.</span></span> <span data-ttu-id="91d27-127">証明書を使用するデータベース ミラーリング エンドポイントの作成については、「[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="91d27-127">For information about creating a database mirroring endpoint to use certificates, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
6.  <span data-ttu-id="91d27-128">必要に応じて、動作モードを変更します。</span><span class="sxs-lookup"><span data-stu-id="91d27-128">Optionally, change the operating mode.</span></span> <span data-ttu-id="91d27-129">特定の動作モードの可用性は、ミラーリング監視サーバーの TCP アドレスを指定したかどうかに依存します。</span><span class="sxs-lookup"><span data-stu-id="91d27-129">The availability of certain operating mode(s) depends on whether you have specified a TCP address for a witness.</span></span> <span data-ttu-id="91d27-130">次のようなオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="91d27-130">The options are as follows:</span></span>  
  
    |<span data-ttu-id="91d27-131">オプション</span><span class="sxs-lookup"><span data-stu-id="91d27-131">Option</span></span>|<span data-ttu-id="91d27-132">ミラーリング監視サーバー</span><span class="sxs-lookup"><span data-stu-id="91d27-132">Witness?</span></span>|<span data-ttu-id="91d27-133">説明</span><span class="sxs-lookup"><span data-stu-id="91d27-133">Explanation</span></span>|  
    |------------|--------------|-----------------|  
    |<span data-ttu-id="91d27-134">**[高パフォーマンス (非同期)]**</span><span class="sxs-lookup"><span data-stu-id="91d27-134">**High performance (asynchronous)**</span></span>|<span data-ttu-id="91d27-135">Null (存在しても使用されませんが、セッションにクォーラムが必要になります)</span><span class="sxs-lookup"><span data-stu-id="91d27-135">Null (if exists, not used but the session requires a quorum)</span></span>|<span data-ttu-id="91d27-136">最適なパフォーマンスを提供するために、ミラー データベースが常にプリンシパル データベースから多少遅延されます。完全に時間差がなくなることはありません。</span><span class="sxs-lookup"><span data-stu-id="91d27-136">To maximize performance, the mirror database always lags somewhat behind the principal database, never quite catching up.</span></span> <span data-ttu-id="91d27-137">ただし、データベース間の時間差は、通常はわずかです。</span><span class="sxs-lookup"><span data-stu-id="91d27-137">However, the gap between the databases is typically small.</span></span> <span data-ttu-id="91d27-138">パートナーの損失による影響は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="91d27-138">The loss of a partner has the following effect:</span></span><br /><br /> <span data-ttu-id="91d27-139">ミラー サーバー インスタンスが使用できなくなった場合は、引き続きプリンシパル サーバー インスタンスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="91d27-139">If the mirror server instance becomes unavailable, the principal continues.</span></span><br /><br /> <span data-ttu-id="91d27-140">プリンシパル サーバー インスタンスが使用できなくなると、ミラー サーバー インスタンスは停止しますが、セッションにミラーリング監視サーバーがない場合 (推奨) やミラーリング監視サーバーがミラー サーバーに接続されている場合、ミラー サーバーはウォーム スタンバイとしてアクセスできます。つまり、データベース所有者は、ミラー サーバー インスタンスにサービスを強制できます (データ損失の可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="91d27-140">If the principal server instance becomes unavailable, the mirror stops; but if the session has no witness (as recommended) or the witness is connected to the mirror server, the mirror server is accessible as a warm standby; the database owner can force service to the mirror server instance (with possible data loss).</span></span><br /><br /> <br /><br /> <span data-ttu-id="91d27-141">詳細については、「 [データベース ミラーリング セッション中の役割の交代 &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)をダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="91d27-141">For more information, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>|  
    |<span data-ttu-id="91d27-142">**[自動フェールオーバーを伴わない高い安全性 (同期)]**</span><span class="sxs-lookup"><span data-stu-id="91d27-142">**High safety without automatic failover (synchronous)**</span></span>|<span data-ttu-id="91d27-143">いいえ</span><span class="sxs-lookup"><span data-stu-id="91d27-143">No</span></span>|<span data-ttu-id="91d27-144">コミットされているすべてのトランザクションは、ミラー サーバー上のディスクに書き込まれることが保証されています。</span><span class="sxs-lookup"><span data-stu-id="91d27-144">All committed transactions are guaranteed to be written to disk on the mirror server.</span></span><br /><br /> <span data-ttu-id="91d27-145">パートナーが相互に接続され、データベースが同期されると、手動フェールオーバーを開始できます。</span><span class="sxs-lookup"><span data-stu-id="91d27-145">Manual failover is possible when the partners are connected to each other and the database is synchronized.</span></span> <span data-ttu-id="91d27-146">パートナーの損失による影響は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="91d27-146">The loss of a partner has the following effect:</span></span><br /><br /> <span data-ttu-id="91d27-147">ミラー サーバー インスタンスが使用できなくなった場合は、引き続きプリンシパル サーバー インスタンスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="91d27-147">If the mirror server instance becomes unavailable, the principal continues.</span></span><br /><br /> <span data-ttu-id="91d27-148">プリンシパル サーバー インスタンスが使用できなくなると、ミラー サーバー インスタンスは停止しますが、ウォーム スタンバイとしてアクセスできます。データベース所有者は、ミラー サーバー インスタンスにサービスを強制できます (データ損失の可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="91d27-148">If the principal server instance becomes unavailable, the mirror stops but is accessible as a warm standby; the database owner can force service to the mirror server instance (with possible data loss).</span></span><br /><br /> <span data-ttu-id="91d27-149">詳細については、「 [データベース ミラーリング セッション中の役割の交代 &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)をダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="91d27-149">For more information, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>|  
    |<span data-ttu-id="91d27-150">**[自動フェールオーバーを伴う高い安全性 (同期)]**</span><span class="sxs-lookup"><span data-stu-id="91d27-150">**High safety with automatic failover (synchronous)**</span></span>|<span data-ttu-id="91d27-151">指定あり (必須)</span><span class="sxs-lookup"><span data-stu-id="91d27-151">Yes (required)</span></span>|<span data-ttu-id="91d27-152">コミットされているすべてのトランザクションは、ミラー サーバー上のディスクに書き込まれることが保証されています。</span><span class="sxs-lookup"><span data-stu-id="91d27-152">All committed transactions are guaranteed to be written to disk on the mirror server.</span></span> <span data-ttu-id="91d27-153">自動フェールオーバーをサポートするミラーリング監視サーバー インスタンスを含めることによって、可用性は最大限に高まります。</span><span class="sxs-lookup"><span data-stu-id="91d27-153">Availability is maximized by including a witness server instance to support automatic failover.</span></span> <span data-ttu-id="91d27-154">**[自動フェールオーバーを伴う高い安全性 (同期)]** オプションを選択できるのは、最初にミラーリング監視サーバーのアドレスを指定した場合のみです。</span><span class="sxs-lookup"><span data-stu-id="91d27-154">Note that you can select the **High safety with automatic failover (synchronous)** option only if you have first specified a witness server address.</span></span> <span data-ttu-id="91d27-155">パートナーが相互に接続され、データベースが同期されると、手動フェールオーバーを開始できます。</span><span class="sxs-lookup"><span data-stu-id="91d27-155">Manual failover is possible when the partners are connected to each other and the database is synchronized.</span></span><br /><br /> <span data-ttu-id="91d27-156">ミラーリング監視サーバーが存在する場合、パートナーの損失による影響は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="91d27-156">In the presence of a witness, the loss of a partner has the following effect:</span></span><br /><br /> <span data-ttu-id="91d27-157">-プリンシパルサーバーインスタンスが使用できなくなった場合は、自動フェールオーバーが発生します。</span><span class="sxs-lookup"><span data-stu-id="91d27-157">-If the principal server instance becomes unavailable, automatic failover occurs.</span></span> <span data-ttu-id="91d27-158">ミラー サーバー インスタンスはプリンシパル サーバー インスタンスの役割に切り替わり、ミラー データベースがプリンシパル データベースとして提供されます。</span><span class="sxs-lookup"><span data-stu-id="91d27-158">The mirror server instance switches to the role of principal, and it offers its database as the principal database.</span></span><br /><br /> <span data-ttu-id="91d27-159">-ミラーサーバーインスタンスが使用できなくなった場合、プリンシパルは続行されます。</span><span class="sxs-lookup"><span data-stu-id="91d27-159">-If the mirror server instance becomes unavailable, the principal continues.</span></span><br /><br /> <span data-ttu-id="91d27-160">詳細については、「 [データベース ミラーリング セッション中の役割の交代 &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)をダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="91d27-160">For more information, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).</span></span><br /><br /> <span data-ttu-id="91d27-161">重要ミラーリング監視サーバーが切断された場合、データベースを使用できるようにするには、パートナーが相互に接続されている必要があります。 \*\* \* \* \* \* \*\*</span><span class="sxs-lookup"><span data-stu-id="91d27-161">**\*\* Important \*\*** If the witness becomes disconnected, the partners must be connected to each other for the database to be available.</span></span> <span data-ttu-id="91d27-162">詳細については、「[クォーラム: データベースの可用性にミラーリング監視サーバーが与える影響 (データベース ミラーリング)](quorum-how-a-witness-affects-database-availability-database-mirroring.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91d27-162">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>|  
  
7.  <span data-ttu-id="91d27-163">次のすべての条件に当てはまる場合は、 **[ミラーリングの開始]** をクリックしてミラーリングを開始します。</span><span class="sxs-lookup"><span data-stu-id="91d27-163">When all of the following conditions exist, click **Start Mirroring** to begin mirroring:</span></span>  
  
    -   <span data-ttu-id="91d27-164">現在プリンシパル サーバー インスタンスに接続されています。</span><span class="sxs-lookup"><span data-stu-id="91d27-164">You are currently connected to the principal server instance.</span></span>  
  
    -   <span data-ttu-id="91d27-165">セキュリティが正しく構成されています。</span><span class="sxs-lookup"><span data-stu-id="91d27-165">Security has been configured correctly.</span></span>  
  
    -   <span data-ttu-id="91d27-166">プリンシパル サーバー インスタンスとミラー サーバー インスタンスの完全修飾 TCP アドレスが、( **[サーバー ネットワーク アドレス]** セクションで) 指定されています。</span><span class="sxs-lookup"><span data-stu-id="91d27-166">The fully-qualified TCP addresses of the principal and mirror server instances are specified (in the **Server network addresses** section).</span></span>  
  
    -   <span data-ttu-id="91d27-167">動作モードが **[自動フェールオーバーを伴う高い安全性 (同期)]** に設定されている場合、ミラーリング監視サーバー インスタンスの完全修飾 TCP アドレスも指定されています。</span><span class="sxs-lookup"><span data-stu-id="91d27-167">If the operating mode is set to **High safety with automatic failover (synchronous)**, the fully-qualified TCP address of the witness server instance is also specified.</span></span>  
  
8.  <span data-ttu-id="91d27-168">ミラーリングが開始された後でも、動作モードを変更して **[OK]** をクリックすることで変更を保存できます。</span><span class="sxs-lookup"><span data-stu-id="91d27-168">After mirroring begins, you can change the operating mode and save the change by clicking **OK**.</span></span> <span data-ttu-id="91d27-169">自動フェールオーバーを伴う高い安全性モードに切り替えることができるのは、先にミラーリング監視サーバーのアドレスを指定した場合のみです。</span><span class="sxs-lookup"><span data-stu-id="91d27-169">Note that you can switch to high-safety mode with automatic failover only if you have first specified a witness server address.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="91d27-170">ミラーリング監視サーバーを削除するには、 **[ミラーリング監視]** フィールドからそのサーバー ネットワーク アドレスを削除します。</span><span class="sxs-lookup"><span data-stu-id="91d27-170">To remove the witness, delete its server network address from the **Witness** field.</span></span> <span data-ttu-id="91d27-171">自動フェールオーバーを伴う高い安全性モードから高パフォーマンス モードに切り替えると、 **[ミラーリング監視]** フィールドの内容は自動的に消去されます。</span><span class="sxs-lookup"><span data-stu-id="91d27-171">If you switch from high-safety mode with automatic failover to high-performance mode, the **Witness** field is automatically cleared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91d27-172">参照</span><span class="sxs-lookup"><span data-stu-id="91d27-172">See Also</span></span>  
 <span data-ttu-id="91d27-173">[データベース ミラーリング セッション中の役割の交代 &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="91d27-173">[Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md) </span></span>  
 <span data-ttu-id="91d27-174">[ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="91d27-174">[Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="91d27-175">[データベース プロパティ &#40;[ミラーリング] ページ&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="91d27-175">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="91d27-176">[データベース ミラーリング セッションを一時停止または再開する &#40;Transact-SQL&#41;](pause-or-resume-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="91d27-176">[Pause or Resume a Database Mirroring Session &#40;SQL Server&#41;](pause-or-resume-a-database-mirroring-session-sql-server.md) </span></span>  
 <span data-ttu-id="91d27-177">[信頼できるプロパティを使用するようにミラーデータベースを設定する Transact-sql&#41;&#40;](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="91d27-177">[Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md) </span></span>  
 <span data-ttu-id="91d27-178">[データベースミラーリング &#40;SQL Server の削除&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="91d27-178">[Remove Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="91d27-179">[役割の交代後のログインとジョブの管理 &#40;SQL Server&#41;](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="91d27-179">[Management of Logins and Jobs After Role Switching &#40;SQL Server&#41;](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md) </span></span>  
 <span data-ttu-id="91d27-180">[データベース ミラーリングの設定 &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="91d27-180">[Setting Up Database Mirroring &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="91d27-181">[データベースを別のサーバー インスタンスで使用できるようにするときのメタデータの管理 &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md) </span><span class="sxs-lookup"><span data-stu-id="91d27-181">[Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md) </span></span>  
 [<span data-ttu-id="91d27-182">データベース ミラーリング監視サーバーを追加または置き換える方法 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="91d27-182">Add or Replace a Database Mirroring Witness &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
  