---
title: 可用性グループのプロパティと [新しい可用性グループ] ([全般] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroupproperties.general.f1
ms.assetid: 9af5379f-91b8-4729-9f75-4a80242a30e9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 876b9d0948b7cd0d01c21b0ec1d64c51a55fa157
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632117"
---
# <a name="availability-group-properties-and-new-availability-group-general-page"></a><span data-ttu-id="1bc53-102">[可用性グループのプロパティ] と [新しい可用性グループ] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="1bc53-102">Availability Group Properties and New Availability Group (General Page)</span></span>
  <span data-ttu-id="1bc53-103">このトピックは、 **[新しい可用性グループ]** ダイアログ ボックスと **[可用性グループのプロパティ]** ダイアログ ボックスの **[全般]** タブに該当します。</span><span class="sxs-lookup"><span data-stu-id="1bc53-103">This topic applies to the **General** tab of both the **New Availability Group** dialog box and the **Availability Group Properties** dialog box.</span></span>  <span data-ttu-id="1bc53-104">**[新しい可用性グループ]** ダイアログ ボックスでは、 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)]を使用せずに新しい可用性グループを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1bc53-104">The **New Availability Group** dialog box enables you to create a new availability group without using the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)].</span></span> <span data-ttu-id="1bc53-105">**[可用性グループのプロパティ]** ダイアログ ボックスでは、既存の可用性グループの構成を表示、変更できます。</span><span class="sxs-lookup"><span data-stu-id="1bc53-105">The **Availability Group Properties** dialog box enables you to view and alter the configuration of an existing availability group.</span></span>  
  
 <span data-ttu-id="1bc53-106">**可用性グループのプロパティを表示するには**</span><span class="sxs-lookup"><span data-stu-id="1bc53-106">**To view availability group properties**</span></span>  
  
-   [<span data-ttu-id="1bc53-107">可用性グループのプロパティの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1bc53-107">View Availability Group Properties &#40;SQL Server&#41;</span></span>](view-availability-group-properties-sql-server.md)  
  
-   [<span data-ttu-id="1bc53-108">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="1bc53-108">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
## <a name="ui-element-list"></a><span data-ttu-id="1bc53-109">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="1bc53-109">UI element list</span></span>  
 <span data-ttu-id="1bc53-110">**[可用性グループ名]**</span><span class="sxs-lookup"><span data-stu-id="1bc53-110">**Availability group name**</span></span>  
 <span data-ttu-id="1bc53-111">可用性グループの名前。</span><span class="sxs-lookup"><span data-stu-id="1bc53-111">Name of the availability group.</span></span> <span data-ttu-id="1bc53-112">これはユーザー指定の名前であり、Windows Server フェールオーバー クラスター (WSFC) 内で一意であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="1bc53-112">This is a user-specified name that must be unique within the Windows Server Failover Cluster (WSFC).</span></span>  
  
## <a name="availability-databases"></a><span data-ttu-id="1bc53-113">可用性データベース</span><span class="sxs-lookup"><span data-stu-id="1bc53-113">Availability Databases</span></span>  
 <span data-ttu-id="1bc53-114">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="1bc53-114">**Database Name**</span></span>  
 <span data-ttu-id="1bc53-115">可用性グループに追加されたデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="1bc53-115">Name of a database that has been added to the availability group.</span></span>  
  
 <span data-ttu-id="1bc53-116">**追加**</span><span class="sxs-lookup"><span data-stu-id="1bc53-116">**Add**</span></span>  
 <span data-ttu-id="1bc53-117">クリックすると、データベースが可用性グループに追加されます。</span><span class="sxs-lookup"><span data-stu-id="1bc53-117">Click to add a database to the availability group.</span></span>  
  
 <span data-ttu-id="1bc53-118">**Remove**</span><span class="sxs-lookup"><span data-stu-id="1bc53-118">**Remove**</span></span>  
 <span data-ttu-id="1bc53-119">クリックすると、選択したデータベースが可用性グループから削除されます。</span><span class="sxs-lookup"><span data-stu-id="1bc53-119">Click to remove a selected database from the availability group.</span></span>  
  
## <a name="availability-replicas"></a><span data-ttu-id="1bc53-120">可用性レプリカ</span><span class="sxs-lookup"><span data-stu-id="1bc53-120">Availability Replicas</span></span>  
 <span data-ttu-id="1bc53-121">**サーバー インスタンス**</span><span class="sxs-lookup"><span data-stu-id="1bc53-121">**Server instance**</span></span>  
 <span data-ttu-id="1bc53-122">このレプリカをホストし、既定ではないインスタンスの場合はレプリカのインスタンス名もホストしている、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスのサーバー名。</span><span class="sxs-lookup"><span data-stu-id="1bc53-122">Server name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is hosting this replica and, for a non-default instance, its instance name.</span></span>  
  
 <span data-ttu-id="1bc53-123">**ロール**</span><span class="sxs-lookup"><span data-stu-id="1bc53-123">**Role**</span></span>  
 <span data-ttu-id="1bc53-124">**プライマリ**</span><span class="sxs-lookup"><span data-stu-id="1bc53-124">**Primary**</span></span>  
 <span data-ttu-id="1bc53-125">現在、プライマリ レプリカです。</span><span class="sxs-lookup"><span data-stu-id="1bc53-125">Currently the primary replica.</span></span>  
  
 <span data-ttu-id="1bc53-126">**セカンダリ**</span><span class="sxs-lookup"><span data-stu-id="1bc53-126">**Secondary**</span></span>  
 <span data-ttu-id="1bc53-127">現在、セカンダリ レプリカです。</span><span class="sxs-lookup"><span data-stu-id="1bc53-127">Currently a secondary replica.</span></span>  
  
 <span data-ttu-id="1bc53-128">**[解決中]**</span><span class="sxs-lookup"><span data-stu-id="1bc53-128">**Resolving**</span></span>  
 <span data-ttu-id="1bc53-129">現在、レプリカのロールは、プライマリ ロールとセカンダリ ロールのどちらかに解決中です。</span><span class="sxs-lookup"><span data-stu-id="1bc53-129">Currently the replica role is in the process of being resolved to either the primary or secondary role.</span></span>  
  
 <span data-ttu-id="1bc53-130">**可用性モード**</span><span class="sxs-lookup"><span data-stu-id="1bc53-130">**Availability Mode**</span></span>  
 <span data-ttu-id="1bc53-131">レプリカの可用性モード。次のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="1bc53-131">The availability mode of the replica, one of:</span></span>  
  
 <span data-ttu-id="1bc53-132">**[非同期コミット]**</span><span class="sxs-lookup"><span data-stu-id="1bc53-132">**Asynchronous commit**</span></span>  
 <span data-ttu-id="1bc53-133">プライマリ レプリカは、セカンダリがログをディスクに書き込むのを待機することなくトランザクションをコミットできます。</span><span class="sxs-lookup"><span data-stu-id="1bc53-133">The primary replica can commit transactions without waiting for the secondary to write the log to disk.</span></span>  
  
 <span data-ttu-id="1bc53-134">**[同期コミット]**</span><span class="sxs-lookup"><span data-stu-id="1bc53-134">**Synchronous commit**</span></span>  
 <span data-ttu-id="1bc53-135">プライマリ レプリカは、セカンダリ レプリカがトランザクションをディスクに書き込むまで、特定のトランザクションのコミットを待機します。</span><span class="sxs-lookup"><span data-stu-id="1bc53-135">The primary replica waits to commit a given transaction until the secondary replica has written the transaction to disk.</span></span>  
  
 <span data-ttu-id="1bc53-136">詳細については、「[可用性モード (AlwaysOn 可用性グループ)](availability-modes-always-on-availability-groups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1bc53-136">For more information, see [Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="1bc53-137">**フェールオーバー モード**</span><span class="sxs-lookup"><span data-stu-id="1bc53-137">**Failover Mode**</span></span>  
 <span data-ttu-id="1bc53-138">レプリカのフェールオーバー モード。次のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="1bc53-138">The failover mode of the replica, one of:</span></span>  
  
 <span data-ttu-id="1bc53-139">**自動**</span><span class="sxs-lookup"><span data-stu-id="1bc53-139">**Automatic**</span></span>  
 <span data-ttu-id="1bc53-140">自動フェールオーバー。</span><span class="sxs-lookup"><span data-stu-id="1bc53-140">Automatic failover.</span></span> <span data-ttu-id="1bc53-141">レプリカは、自動フェールオーバーのターゲットです。</span><span class="sxs-lookup"><span data-stu-id="1bc53-141">The replica is a target for automatic failovers.</span></span> <span data-ttu-id="1bc53-142">可用性モードが同期コミットに設定されている場合にのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="1bc53-142">This is supported only if the availability mode is set to synchronous commit.</span></span>  
  
 <span data-ttu-id="1bc53-143">**手動**</span><span class="sxs-lookup"><span data-stu-id="1bc53-143">**Manual**</span></span>  
 <span data-ttu-id="1bc53-144">手動フェールオーバー。</span><span class="sxs-lookup"><span data-stu-id="1bc53-144">Manual failover.</span></span> <span data-ttu-id="1bc53-145">このレプリカには、データベース管理者が手動でのみフェールオーバーできます。</span><span class="sxs-lookup"><span data-stu-id="1bc53-145">The replica can only be failed over to manually by the database administrator.</span></span>  
  
 <span data-ttu-id="1bc53-146">**[プライマリ ロールの接続]**</span><span class="sxs-lookup"><span data-stu-id="1bc53-146">**Connections in Primary Role**</span></span>  
 <span data-ttu-id="1bc53-147">レプリカがプライマリ ロールを所有している場合にサポートされるクライアント接続の種類。</span><span class="sxs-lookup"><span data-stu-id="1bc53-147">The type of client connections supported when the replica owns the primary role.</span></span>  
  
 <span data-ttu-id="1bc53-148">**[すべての接続を許可]**</span><span class="sxs-lookup"><span data-stu-id="1bc53-148">**Allow all connections**</span></span>  
 <span data-ttu-id="1bc53-149">プライマリ レプリカのデータベースに対するすべての接続が許可されます。</span><span class="sxs-lookup"><span data-stu-id="1bc53-149">All connections are allowed to the databases in the primary replica.</span></span> <span data-ttu-id="1bc53-150">これが既定の設定です。</span><span class="sxs-lookup"><span data-stu-id="1bc53-150">This is the default setting.</span></span>  
  
 <span data-ttu-id="1bc53-151">**[読み取り/書き込みの接続を許可]**</span><span class="sxs-lookup"><span data-stu-id="1bc53-151">**Allow read/write connections**</span></span>  
 <span data-ttu-id="1bc53-152">Application Intent 接続プロパティが **ReadOnly** に設定されている接続は許可されません。</span><span class="sxs-lookup"><span data-stu-id="1bc53-152">Connections where the Application Intent connection property is set to **ReadOnly** are disallowed.</span></span> <span data-ttu-id="1bc53-153">Application Intent プロパティが **ReadWrite** に設定されている場合、または Application Intent 接続プロパティが設定されていない場合は、接続が許可されます。</span><span class="sxs-lookup"><span data-stu-id="1bc53-153">When the Application Intent property is set to **ReadWrite** or the Application Intent connection property is not set, the connection is allowed.</span></span> <span data-ttu-id="1bc53-154">"アプリケーションの目的" 接続プロパティの詳細については、「 [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1bc53-154">For more information about Application Intent connection property, see [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
 <span data-ttu-id="1bc53-155">**[読み取り可能セカンダリ]**</span><span class="sxs-lookup"><span data-stu-id="1bc53-155">**Readable Secondary**</span></span>  
 <span data-ttu-id="1bc53-156">セカンダリ ロールを実行している (つまりセカンダリ レプリカとして機能している) 可用性レプリカがクライアントからの接続を受け入れることができるかどうか。以下のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="1bc53-156">Whether an availability replica that is performing the secondary role (that is, a secondary replica) can accept connections from clients, one of:</span></span>  
  
 <span data-ttu-id="1bc53-157">**いいえ**</span><span class="sxs-lookup"><span data-stu-id="1bc53-157">**No**</span></span>  
 <span data-ttu-id="1bc53-158">このレプリカのセカンダリ データベースに対する直接接続は禁止されます。</span><span class="sxs-lookup"><span data-stu-id="1bc53-158">No direct connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="1bc53-159">読み取りアクセスで利用することはできません。</span><span class="sxs-lookup"><span data-stu-id="1bc53-159">They are not available for read access.</span></span> <span data-ttu-id="1bc53-160">これが既定の設定です。</span><span class="sxs-lookup"><span data-stu-id="1bc53-160">This is the default setting.</span></span>  
  
 <span data-ttu-id="1bc53-161">**[読み取り目的のみ]**</span><span class="sxs-lookup"><span data-stu-id="1bc53-161">**Read-intent only**</span></span>  
 <span data-ttu-id="1bc53-162">このレプリカのセカンダリ データベースに対する直接接続は、読み取り専用でのみ許可されます。</span><span class="sxs-lookup"><span data-stu-id="1bc53-162">Only direct read-only connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="1bc53-163">セカンダリ データベースはすべて読み取りアクセスで利用できます。</span><span class="sxs-lookup"><span data-stu-id="1bc53-163">The secondary database(s) are all available for read access.</span></span>  
  
 <span data-ttu-id="1bc53-164">**はい**</span><span class="sxs-lookup"><span data-stu-id="1bc53-164">**Yes**</span></span>  
 <span data-ttu-id="1bc53-165">読み取りアクセスに限り、このレプリカのセカンダリ データベースに対するすべての接続が許可されます。</span><span class="sxs-lookup"><span data-stu-id="1bc53-165">All connections are allowed to secondary databases of this replica, but only for read access.</span></span> <span data-ttu-id="1bc53-166">セカンダリ データベースはすべて読み取りアクセスで利用できます。</span><span class="sxs-lookup"><span data-stu-id="1bc53-166">The secondary database(s) are all available for read access.</span></span>  
  
 <span data-ttu-id="1bc53-167">**[セッションのタイムアウト (秒)]**</span><span class="sxs-lookup"><span data-stu-id="1bc53-167">**Session Timeout (seconds)**</span></span>  
 <span data-ttu-id="1bc53-168">このレプリカでのセッションのタイムアウト期間の秒数。</span><span class="sxs-lookup"><span data-stu-id="1bc53-168">The number of seconds for the session-timeout period on this replica.</span></span>  
  
 <span data-ttu-id="1bc53-169">**エンドポイント URL**</span><span class="sxs-lookup"><span data-stu-id="1bc53-169">**Endpoint URL**</span></span>  
 <span data-ttu-id="1bc53-170">エンドポイントの URL です。</span><span class="sxs-lookup"><span data-stu-id="1bc53-170">The URL of the endpoint.</span></span> <span data-ttu-id="1bc53-171">詳細については、「[可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1bc53-171">For information the format of these URLs, see [Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md).</span></span>  
  
 <span data-ttu-id="1bc53-172">**追加**</span><span class="sxs-lookup"><span data-stu-id="1bc53-172">**Add**</span></span>  
 <span data-ttu-id="1bc53-173">クリックすると、セカンダリ レプリカが可用性グループに追加されます。</span><span class="sxs-lookup"><span data-stu-id="1bc53-173">Click to add a secondary replica to the availability group.</span></span>  
  
 <span data-ttu-id="1bc53-174">**Remove**</span><span class="sxs-lookup"><span data-stu-id="1bc53-174">**Remove**</span></span>  
 <span data-ttu-id="1bc53-175">クリックすると、セカンダリ レプリカが可用性グループから削除されます。</span><span class="sxs-lookup"><span data-stu-id="1bc53-175">Click to remove a secondary replica from the availability group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bc53-176">参照</span><span class="sxs-lookup"><span data-stu-id="1bc53-176">See Also</span></span>  
 [<span data-ttu-id="1bc53-177">AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;</span><span class="sxs-lookup"><span data-stu-id="1bc53-177">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
