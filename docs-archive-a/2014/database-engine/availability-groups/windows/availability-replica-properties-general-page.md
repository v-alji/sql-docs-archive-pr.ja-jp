---
title: 可用性レプリカのプロパティ ([全般] ページ) | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilityreplicaproperties.general.f1
ms.assetid: 8318fefb-e045-4fab-8507-e1951fc7cec6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 313314baf009cdfb6109e63e9b65e369ac314f60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741326"
---
# <a name="availability-replica-properties-general-page"></a><span data-ttu-id="035b4-102">可用性レプリカのプロパティ ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="035b4-102">Availability Replica Properties (General Page)</span></span>
  <span data-ttu-id="035b4-103">このダイアログ ボックスには、可用性レプリカのプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="035b4-103">Use this dialog box to viewthe properties of an availability replica.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="035b4-104">タスク一覧</span><span class="sxs-lookup"><span data-stu-id="035b4-104">Task List</span></span>  
 <span data-ttu-id="035b4-105">**可用性レプリカのプロパティを表示するには**</span><span class="sxs-lookup"><span data-stu-id="035b4-105">**To view availability replica properties**</span></span>  
  
-   [<span data-ttu-id="035b4-106">可用性レプリカのプロパティの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="035b4-106">View Availability Replica Properties &#40;SQL Server&#41;</span></span>](view-availability-replica-properties-sql-server.md)  
  
-   [<span data-ttu-id="035b4-107">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="035b4-107">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
## <a name="ui-element-list"></a><span data-ttu-id="035b4-108">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="035b4-108">UI element list</span></span>  
 <span data-ttu-id="035b4-109">**[可用性グループ名]**</span><span class="sxs-lookup"><span data-stu-id="035b4-109">**Availability group name**</span></span>  
 <span data-ttu-id="035b4-110">可用性グループの名前。</span><span class="sxs-lookup"><span data-stu-id="035b4-110">Name of the availability group.</span></span> <span data-ttu-id="035b4-111">これはユーザー指定の名前であり、Windows Server フェールオーバー クラスター (WSFC) 内で一意であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="035b4-111">This is a user-specified name that must be unique within the Windows Server Failover Cluster (WSFC).</span></span>  
  
 <span data-ttu-id="035b4-112">**サーバー インスタンス**</span><span class="sxs-lookup"><span data-stu-id="035b4-112">**Server instance**</span></span>  
 <span data-ttu-id="035b4-113">このレプリカをホストし、既定ではないインスタンスの場合はレプリカのインスタンス名もホストしている、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスのサーバー名。</span><span class="sxs-lookup"><span data-stu-id="035b4-113">Server name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is hosting this replica and, for a non-default instance, its instance name.</span></span>  
  
 <span data-ttu-id="035b4-114">**ロール**</span><span class="sxs-lookup"><span data-stu-id="035b4-114">**Role**</span></span>  
 <span data-ttu-id="035b4-115">**プライマリ**</span><span class="sxs-lookup"><span data-stu-id="035b4-115">**Primary**</span></span>  
 <span data-ttu-id="035b4-116">現在、プライマリ レプリカです。</span><span class="sxs-lookup"><span data-stu-id="035b4-116">Currently the primary replica.</span></span>  
  
 <span data-ttu-id="035b4-117">**セカンダリ**</span><span class="sxs-lookup"><span data-stu-id="035b4-117">**Secondary**</span></span>  
 <span data-ttu-id="035b4-118">現在、セカンダリ レプリカです。</span><span class="sxs-lookup"><span data-stu-id="035b4-118">Currently a secondary replica.</span></span>  
  
 <span data-ttu-id="035b4-119">**[解決中]**</span><span class="sxs-lookup"><span data-stu-id="035b4-119">**Resolving**</span></span>  
 <span data-ttu-id="035b4-120">現在、レプリカのロールは、プライマリ ロールとセカンダリ ロールのどちらかに解決中です。</span><span class="sxs-lookup"><span data-stu-id="035b4-120">Currently the replica role is in the process of being resolved to either the primary or secondary role.</span></span>  
  
 <span data-ttu-id="035b4-121">**[可用性モード]**</span><span class="sxs-lookup"><span data-stu-id="035b4-121">**Availability mode**</span></span>  
 <span data-ttu-id="035b4-122">レプリカの可用性モード。次のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="035b4-122">The availability mode of the replica, one of:</span></span>  
  
 <span data-ttu-id="035b4-123">**[非同期コミット]**</span><span class="sxs-lookup"><span data-stu-id="035b4-123">**Asynchronous commit**</span></span>  
 <span data-ttu-id="035b4-124">プライマリ レプリカは、セカンダリがログをディスクに書き込むのを待機することなくトランザクションをコミットできます。</span><span class="sxs-lookup"><span data-stu-id="035b4-124">The primary replica can commit transactions without waiting for the secondary to write the log to disk.</span></span>  
  
 <span data-ttu-id="035b4-125">**[同期コミット]**</span><span class="sxs-lookup"><span data-stu-id="035b4-125">**Synchronous commit**</span></span>  
 <span data-ttu-id="035b4-126">プライマリ レプリカは、セカンダリ レプリカがトランザクションをディスクに書き込むまで、特定のトランザクションのコミットを待機します。</span><span class="sxs-lookup"><span data-stu-id="035b4-126">The primary replica waits to commit a given transaction until the secondary replica has written the transaction to disk.</span></span>  
  
 <span data-ttu-id="035b4-127">詳細については、「[可用性モード (AlwaysOn 可用性グループ)](availability-modes-always-on-availability-groups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="035b4-127">For more information, see [Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="035b4-128">**Failover mode**</span><span class="sxs-lookup"><span data-stu-id="035b4-128">**Failover mode**</span></span>  
 <span data-ttu-id="035b4-129">レプリカのフェールオーバー モード。次のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="035b4-129">The failover mode of the replica, one of:</span></span>  
  
 <span data-ttu-id="035b4-130">**自動**</span><span class="sxs-lookup"><span data-stu-id="035b4-130">**Automatic**</span></span>  
 <span data-ttu-id="035b4-131">自動フェールオーバー。</span><span class="sxs-lookup"><span data-stu-id="035b4-131">Automatic failover.</span></span> <span data-ttu-id="035b4-132">レプリカは、自動フェールオーバーのターゲットです。</span><span class="sxs-lookup"><span data-stu-id="035b4-132">The replica is a target for automatic failovers.</span></span> <span data-ttu-id="035b4-133">可用性モードが同期コミットに設定されている場合にのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="035b4-133">This is supported only if the availability mode is set to synchronous commit.</span></span>  
  
 <span data-ttu-id="035b4-134">**手動**</span><span class="sxs-lookup"><span data-stu-id="035b4-134">**Manual**</span></span>  
 <span data-ttu-id="035b4-135">手動フェールオーバー。</span><span class="sxs-lookup"><span data-stu-id="035b4-135">Manual failover.</span></span> <span data-ttu-id="035b4-136">このレプリカには、データベース管理者が手動でのみフェールオーバーできます。</span><span class="sxs-lookup"><span data-stu-id="035b4-136">The replica can only be failed over to manually by the database administrator.</span></span>  
  
 <span data-ttu-id="035b4-137">**[プライマリ ロールの接続]**</span><span class="sxs-lookup"><span data-stu-id="035b4-137">**Connections in primary role**</span></span>  
 <span data-ttu-id="035b4-138">レプリカがプライマリ ロールを所有している場合にサポートされるクライアント接続の種類。</span><span class="sxs-lookup"><span data-stu-id="035b4-138">The type of client connections supported when the replica owns the primary role.</span></span>  
  
 <span data-ttu-id="035b4-139">**[すべての接続を許可]**</span><span class="sxs-lookup"><span data-stu-id="035b4-139">**Allow all connections**</span></span>  
 <span data-ttu-id="035b4-140">プライマリ レプリカのデータベースに対するすべての接続が許可されます。</span><span class="sxs-lookup"><span data-stu-id="035b4-140">All connections are allowed to the databases in the primary replica.</span></span> <span data-ttu-id="035b4-141">これが既定の設定です。</span><span class="sxs-lookup"><span data-stu-id="035b4-141">This is the default setting.</span></span>  
  
 <span data-ttu-id="035b4-142">**[読み取り/書き込みの接続を許可]**</span><span class="sxs-lookup"><span data-stu-id="035b4-142">**Allow read/write connections**</span></span>  
 <span data-ttu-id="035b4-143">Application Intent 接続プロパティが **ReadOnly** に設定されている接続は許可されません。</span><span class="sxs-lookup"><span data-stu-id="035b4-143">Connections where the Application Intent connection property is set to **ReadOnly** are disallowed.</span></span> <span data-ttu-id="035b4-144">Application Intent プロパティが **ReadWrite** に設定されている場合、または Application Intent 接続プロパティが設定されていない場合は、接続が許可されます。</span><span class="sxs-lookup"><span data-stu-id="035b4-144">When the Application Intent property is set to **ReadWrite** or the application intent connection property is not set, the connection is allowed.</span></span>  
  
 <span data-ttu-id="035b4-145">**[読み取り可能セカンダリ]**</span><span class="sxs-lookup"><span data-stu-id="035b4-145">**Readable Secondary**</span></span>  
 <span data-ttu-id="035b4-146">セカンダリ ロールを実行している (つまりセカンダリ レプリカとして機能している) 可用性レプリカがクライアントからの接続を受け入れることができるかどうか。以下のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="035b4-146">Whether an availability replica that is performing the secondary role (that is, a secondary replica) can accept connections from clients, one of:</span></span>  
  
 <span data-ttu-id="035b4-147">**いいえ**</span><span class="sxs-lookup"><span data-stu-id="035b4-147">**No**</span></span>  
 <span data-ttu-id="035b4-148">このレプリカのセカンダリ データベースに対する直接接続は禁止されます。</span><span class="sxs-lookup"><span data-stu-id="035b4-148">No direct connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="035b4-149">読み取りアクセスで利用することはできません。</span><span class="sxs-lookup"><span data-stu-id="035b4-149">They are not available for read access.</span></span> <span data-ttu-id="035b4-150">これが既定の設定です。</span><span class="sxs-lookup"><span data-stu-id="035b4-150">This is the default setting.</span></span>  
  
 <span data-ttu-id="035b4-151">**[読み取り目的のみ]**</span><span class="sxs-lookup"><span data-stu-id="035b4-151">**Read-intent only**</span></span>  
 <span data-ttu-id="035b4-152">このレプリカのセカンダリ データベースに対する直接接続は、読み取り専用でのみ許可されます。</span><span class="sxs-lookup"><span data-stu-id="035b4-152">Only direct read-only connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="035b4-153">セカンダリ データベースはすべて読み取りアクセスで利用できます。</span><span class="sxs-lookup"><span data-stu-id="035b4-153">The secondary database(s) are all available for read access.</span></span>  
  
 <span data-ttu-id="035b4-154">**はい**</span><span class="sxs-lookup"><span data-stu-id="035b4-154">**Yes**</span></span>  
 <span data-ttu-id="035b4-155">読み取りアクセスに限り、このレプリカのセカンダリ データベースに対するすべての接続が許可されます。</span><span class="sxs-lookup"><span data-stu-id="035b4-155">All connections are allowed to secondary databases of this replica, but only for read access.</span></span> <span data-ttu-id="035b4-156">セカンダリ データベースはすべて読み取りアクセスで利用できます。</span><span class="sxs-lookup"><span data-stu-id="035b4-156">The secondary database(s) are all available for read access.</span></span>  
  
 <span data-ttu-id="035b4-157">詳細については、「[アクティブなセカンダリ: 読み取り可能なセカンダリレプリカ (AlwaysOn 可用性グループ)](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="035b4-157">For more information, see [Active Secondaries: Readable Secondary Replicas (AlwaysOn Availability Groups)](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="035b4-158">**[セッションのタイムアウト (秒)]**</span><span class="sxs-lookup"><span data-stu-id="035b4-158">**Session timeout (seconds)**</span></span>  
 <span data-ttu-id="035b4-159">タイムアウト時間 (秒単位)。</span><span class="sxs-lookup"><span data-stu-id="035b4-159">The time-out period, in seconds.</span></span> <span data-ttu-id="035b4-160">タイムアウト時間は、レプリカが別のレプリカからのメッセージの受信を待機する最大時間です。この時間を過ぎると、プライマリ レプリカとセカンダリ レプリカの間の接続は障害があるものと見なされます。</span><span class="sxs-lookup"><span data-stu-id="035b4-160">The time-out period is the maximum time that the replica waits to receive a message from another replica before considering connection between the primary and secondary replica have failed.</span></span> <span data-ttu-id="035b4-161">セッション タイムアウトは、セカンダリ レプリカがプライマリ レプリカに接続されているかどうかを検出します。</span><span class="sxs-lookup"><span data-stu-id="035b4-161">Session timeout detects whether secondaries are connected the primary replica.</span></span> <span data-ttu-id="035b4-162">セカンダリ レプリカとの接続が確立されていないことを検出すると、プライマリ レプリカはセカンダリ レプリカが NOT_SYNCHRONIZED であるものと判断します。</span><span class="sxs-lookup"><span data-stu-id="035b4-162">On detecting a failed connection with a secondary replica, the primary replica considers the secondary replica to be NOT_SYNCHRONIZED.</span></span> <span data-ttu-id="035b4-163">プライマリ レプリカとの接続が確立されていないことを検出すると、セカンダリ レプリカは単に再接続を試みます。</span><span class="sxs-lookup"><span data-stu-id="035b4-163">On detecting a failed connection with the primary replica, a secondary replica simply attempts to reconnect.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="035b4-164">セッション タイムアウトにより自動フェールオーバーが発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="035b4-164">Session timeouts do not cause automatic failovers.</span></span>  
  
 <span data-ttu-id="035b4-165">**エンドポイント URL**</span><span class="sxs-lookup"><span data-stu-id="035b4-165">**Endpoint URL**</span></span>  
 <span data-ttu-id="035b4-166">データ同期のためにプライマリとセカンダリのレプリカの間の接続で使用される、ユーザー指定のデータベース ミラーリング エンドポイントの文字列表現。</span><span class="sxs-lookup"><span data-stu-id="035b4-166">String representation of the user-specified database mirroring endpoint that is used by connections between primary and secondary replicas for data synchronization.</span></span> <span data-ttu-id="035b4-167">エンドポイント URL の構文の詳細については、「[可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="035b4-167">For information about the syntax of endpoint URLs, see [Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="035b4-168">参照</span><span class="sxs-lookup"><span data-stu-id="035b4-168">See Also</span></span>  
 [<span data-ttu-id="035b4-169">AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;</span><span class="sxs-lookup"><span data-stu-id="035b4-169">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
