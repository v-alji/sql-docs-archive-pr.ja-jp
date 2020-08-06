---
title: 可用性レプリカ間のセッション中に発生する可能性のあるエラー (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting [SQL Server, HADR]
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], troubleshooting
ms.assetid: cd613898-82d9-482f-a255-0230a6c7d6fe
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4cfacb7f7c75875d4f5d0b0b435d282b3f537cc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718729"
---
# <a name="possible-failures-during-sessions-between-availability-replicas-sql-server"></a><span data-ttu-id="a5883-102">可用性レプリカ間のセッション中に発生する可能性のあるエラー (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a5883-102">Possible Failures During Sessions Between Availability Replicas (SQL Server)</span></span>
  <span data-ttu-id="a5883-103">物理的な問題、オペレーティング システムの問題、または [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の問題により、2 つの可用性レプリカ間のセッションが失敗する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a5883-103">Physical, operating system, or [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] problems can cause a failure in a session between two availability replicas.</span></span> <span data-ttu-id="a5883-104">可用性レプリカでは、Sqlservr.exe が依存しているコンポーネントを定期的にチェックして、それらのコンポーネントが正常に機能しているのか失敗したのかを確認する処理は行われません。</span><span class="sxs-lookup"><span data-stu-id="a5883-104">An availability replica does not regularly check the components on which Sqlservr.exe relies to verify whether they are functioning correctly or have failed.</span></span> <span data-ttu-id="a5883-105">ただし、失敗の種類によっては、影響を受けたコンポーネントからエラーが Sqlservr.exe に報告されます。</span><span class="sxs-lookup"><span data-stu-id="a5883-105">However, for some types of failures, the affected component reports an error to Sqlservr.exe.</span></span> <span data-ttu-id="a5883-106">他のコンポーネントから報告されるエラーを *ハード エラー*といいます。</span><span class="sxs-lookup"><span data-stu-id="a5883-106">An error reported by another component is called a *hard error*.</span></span> <span data-ttu-id="a5883-107">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] では、通知されないその他の失敗を検出するために、独自のセッション タイムアウト メカニズムを実装しています。</span><span class="sxs-lookup"><span data-stu-id="a5883-107">To detect other failures that would otherwise go unnoticed, [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] implements its own session-timeout mechanism.</span></span> <span data-ttu-id="a5883-108">セッション タイムアウト期間を秒単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="a5883-108">Specifies the session-timeout period in seconds.</span></span> <span data-ttu-id="a5883-109">このタイムアウト時間は、別のインスタンスからの PING メッセージを受信するために、サーバー インスタンスが待機する最大時間です。この時間を過ぎると、待機していたインスタンスは接続解除されたものと見なされます。</span><span class="sxs-lookup"><span data-stu-id="a5883-109">This time-out period is the maximum time that a server instance waits to receive a PING message from another instance before considering that other instance to be disconnected.</span></span> <span data-ttu-id="a5883-110">2 つの可用性レプリカ間でセッション タイムアウトが発生すると、可用性レプリカはエラーが発生したと想定し、 *ソフト エラー*を宣言します。</span><span class="sxs-lookup"><span data-stu-id="a5883-110">When a session timeout occurs between two availability replicas, the availability replicas assume that a failure has occurred and declares a *soft error*.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a5883-111">プライマリ データベース以外のデータベースで発生した障害は検出されません。</span><span class="sxs-lookup"><span data-stu-id="a5883-111">Failures in databases other than the primary database are not detectable.</span></span> <span data-ttu-id="a5883-112">さらに、データ ディスクの障害によりデータベースが再起動した場合を除き、データ ディスクの障害はほとんど検出されません。</span><span class="sxs-lookup"><span data-stu-id="a5883-112">Moreover, a data disk failure is unlikely to be detected unless the database is restarted because of a data disk failure.</span></span>  
  
 <span data-ttu-id="a5883-113">したがって、エラー検出の速度と、失敗への反応時間は、ハード エラーかソフト エラーかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="a5883-113">The speed of error detection and, therefore, the reaction time to a failure, depends on whether the error is hard or soft.</span></span> <span data-ttu-id="a5883-114">ハード エラーの中には、ネットワーク障害など、直ちに報告されるものもあります。</span><span class="sxs-lookup"><span data-stu-id="a5883-114">Some hard errors, such as network failures are reported immediately.</span></span> <span data-ttu-id="a5883-115">しかし、場合によっては、コンポーネント固有のタイムアウト時間のために報告が遅くなるハード エラーもあります。</span><span class="sxs-lookup"><span data-stu-id="a5883-115">However, in some cases, component-specific time-out periods can delay the reporting of some hard errors.</span></span> <span data-ttu-id="a5883-116">ソフト エラーの場合は、セッション タイムアウト期間の長さによってエラー検出の速度が決まります。</span><span class="sxs-lookup"><span data-stu-id="a5883-116">For soft errors, the length of the session-timeout period determines the speed of error detection.</span></span> <span data-ttu-id="a5883-117">既定では、この時間は 10 秒間です。</span><span class="sxs-lookup"><span data-stu-id="a5883-117">By default, this period is 10 seconds.</span></span> <span data-ttu-id="a5883-118">これは推奨最小値です。</span><span class="sxs-lookup"><span data-stu-id="a5883-118">This is the minimum recommended value.</span></span>  
  
## <a name="failures-due-to-hard-errors"></a><span data-ttu-id="a5883-119">ハード エラーによるエラー</span><span class="sxs-lookup"><span data-stu-id="a5883-119">Failures Due to Hard Errors</span></span>  
 <span data-ttu-id="a5883-120">次のような状況が、ハード エラーの原因になる可能性があります (ただし、これだけではありません)。</span><span class="sxs-lookup"><span data-stu-id="a5883-120">Possible causes of hard errors include (but are not limited to) the following conditions:</span></span>  
  
-   <span data-ttu-id="a5883-121">接続またはケーブルの切断</span><span class="sxs-lookup"><span data-stu-id="a5883-121">A broken connection or wire</span></span>  
  
-   <span data-ttu-id="a5883-122">不適切なネットワーク カード</span><span class="sxs-lookup"><span data-stu-id="a5883-122">A bad network card</span></span>  
  
-   <span data-ttu-id="a5883-123">ルーターの変更</span><span class="sxs-lookup"><span data-stu-id="a5883-123">A router change</span></span>  
  
-   <span data-ttu-id="a5883-124">ファイアウォールの設定変更</span><span class="sxs-lookup"><span data-stu-id="a5883-124">Changes in the firewall</span></span>  
  
-   <span data-ttu-id="a5883-125">エンドポイントの再構成</span><span class="sxs-lookup"><span data-stu-id="a5883-125">Endpoint reconfiguration</span></span>  
  
-   <span data-ttu-id="a5883-126">トランザクション ログの保存先ドライブの消失</span><span class="sxs-lookup"><span data-stu-id="a5883-126">Loss of the drive where the transaction log resides</span></span>  
  
-   <span data-ttu-id="a5883-127">オペレーティング システムまたはプロセスのエラー</span><span class="sxs-lookup"><span data-stu-id="a5883-127">Operating system or process failure</span></span>  
  
 <span data-ttu-id="a5883-128">たとえば、プライマリ データベースのログ ドライブが応答を停止し障害が発生すると、オペレーティング システムから Sqlservr.exe に、深刻なエラーが発生したことが通知されます。</span><span class="sxs-lookup"><span data-stu-id="a5883-128">For example, when the log drive on the primary database becomes unresponsive and fails, the operating system informs Sqlservr.exe that a serious error has occurred.</span></span>  
  
 <span data-ttu-id="a5883-129">ネットワーク コンポーネントや一部の IO サブシステムなど、コンポーネントによっては、障害を特定するための独自のタイムアウトを実装しているものもあります。</span><span class="sxs-lookup"><span data-stu-id="a5883-129">Some components, such as network components and some IO subsystems, have their own time-outs to determine failures.</span></span> <span data-ttu-id="a5883-130">このようなタイムアウトは [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]とは独立して機能します。そのタイムアウトが認識されたり、その動作が完全に把握されることはありません。</span><span class="sxs-lookup"><span data-stu-id="a5883-130">Such time-outs are independent of [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], which has no knowledge of them and is completely unaware of their behavior.</span></span> <span data-ttu-id="a5883-131">このような場合、タイムアウトの遅延により、障害が発生してから、可用性レプリカがハード エラーを受け取るまでの時間が増加します。</span><span class="sxs-lookup"><span data-stu-id="a5883-131">In these cases, the time-out delay increases the time between a failure and when the availability replica receives the resulting hard error.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5883-132">ソフト エラーの場合には、可用性レプリカに対して実行されるアクティブなエラー チェックだけが発生します。</span><span class="sxs-lookup"><span data-stu-id="a5883-132">The only active error checking performed for availability replicas occurs for soft error cases.</span></span> <span data-ttu-id="a5883-133">詳細については、このトピックの後半の「ソフト エラーによるエラー」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5883-133">For more information, see "Failures Due to Soft Errors," later in this topic.</span></span>  
  
 <span data-ttu-id="a5883-134">ネットワーク上で発生しているエラー状態を把握できるように、次のようなイベントが TCP 接続で発生した場合にはどのようなエラー メッセージがポートに送信されるのかを、ネットワーク エンジニアに問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="a5883-134">To help you interpret the error conditions that occur on the network, ask a network engineer what error messages are sent to a port when the following events occur on a TCP connection:</span></span>  
  
-   <span data-ttu-id="a5883-135">DNS が動作していません。</span><span class="sxs-lookup"><span data-stu-id="a5883-135">DNS is not working.</span></span>  
  
-   <span data-ttu-id="a5883-136">ケーブルが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="a5883-136">Cables are unplugged.</span></span>  
  
-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="a5883-137">Windows に存在します。</span><span class="sxs-lookup"><span data-stu-id="a5883-137">Windows has a firewall that blocks a specific port.</span></span>  
  
-   <span data-ttu-id="a5883-138">ポートを監視しているアプリケーションで障害が発生しています。</span><span class="sxs-lookup"><span data-stu-id="a5883-138">The application that is monitoring a port fails.</span></span>  
  
-   <span data-ttu-id="a5883-139">Windows ベースのサーバーの名前が変更されています。</span><span class="sxs-lookup"><span data-stu-id="a5883-139">A Windows-based server is renamed.</span></span>  
  
-   <span data-ttu-id="a5883-140">Windows ベースのサーバーが再起動されています。</span><span class="sxs-lookup"><span data-stu-id="a5883-140">A Windows-based server is rebooted.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssHADRc](../../../includes/sshadrc-md.md)]<span data-ttu-id="a5883-141">は、サーバーにアクセスするクライアントに固有の問題からは保護されません。</span><span class="sxs-lookup"><span data-stu-id="a5883-141">does not protect against problems specific to client accessing the servers.</span></span> <span data-ttu-id="a5883-142">たとえば、プライマリ レプリカへのクライアント接続をパブリック ネットワーク アダプターが処理していて、可用性グループのレプリカをホストしているサーバー インスタンス間のトラフィックをプライベート ネットワーク インターフェイス カードが処理している場合を考えます。</span><span class="sxs-lookup"><span data-stu-id="a5883-142">For example, consider a case in which a public network adapter handles client connections to the primary replica, while a private network interface card handles traffic among the server instances that are hosting the replicas of an availability group.</span></span> <span data-ttu-id="a5883-143">この場合、パブリック ネットワーク アダプターに障害が生じると、クライアントはデータベースにアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="a5883-143">In this case, failure of the public network adapter would prevent clients from accessing the databases.</span></span>  
  
## <a name="failures-due-to-soft-errors"></a><span data-ttu-id="a5883-144">ソフト エラーによるエラー</span><span class="sxs-lookup"><span data-stu-id="a5883-144">Failures Due to Soft Errors</span></span>  
 <span data-ttu-id="a5883-145">次のような状況が、セッション タイムアウトの原因になる可能性があります (ただし、これだけではありません)。</span><span class="sxs-lookup"><span data-stu-id="a5883-145">Conditions that might cause session timeouts include (but are not limited to) the following:</span></span>  
  
-   <span data-ttu-id="a5883-146">TCP リンクのタイムアウト、パケットの紛失または破損、不正な順序のパケットなどのネットワーク エラー。</span><span class="sxs-lookup"><span data-stu-id="a5883-146">Network errors such as TCP link time-outs, dropped or corrupted packets, or packets that are in an incorrect order.</span></span>  
  
-   <span data-ttu-id="a5883-147">オペレーティング システム、サーバー、またはデータベースの応答の停止。</span><span class="sxs-lookup"><span data-stu-id="a5883-147">An operating system, server, or database that is not responding.</span></span>  
  
-   <span data-ttu-id="a5883-148">Windows サーバーのタイムアウト。</span><span class="sxs-lookup"><span data-stu-id="a5883-148">A Windows server timing out.</span></span>  
  
-   <span data-ttu-id="a5883-149">CPU やディスクの過負荷、いっぱいになったトランザクション ログ、メモリやスレッドが不足しているシステムなど、コンピューティング リソースの不足。</span><span class="sxs-lookup"><span data-stu-id="a5883-149">Insufficient computing resources, such as a CPU or disk overload, the transaction log filling up, or the system is running out of memory or threads.</span></span> <span data-ttu-id="a5883-150">このような場合は、タイムアウト期間を長くするか、ワークロードを軽減するか、ハードウェアを交換してワークロードを処理できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5883-150">In these cases, you must increase the time-out period, reduce the workload, or change the hardware to handle the workload.</span></span>  
  
### <a name="the-session-timeout-mechanism"></a><span data-ttu-id="a5883-151">セッション タイムアウトのメカニズム</span><span class="sxs-lookup"><span data-stu-id="a5883-151">The Session-Timeout Mechanism</span></span>  
 <span data-ttu-id="a5883-152">サーバー インスタンスはソフト エラーを直接検出できないため、ソフト エラーが原因で、可用性レプリカがセッションでの他の可用性レプリカからの応答を無限に待機する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a5883-152">Because soft errors are not detectable directly by a server instance, a soft error could potentially cause an availability replica to wait indefinitely for a response from the other availability replica in a session.</span></span> <span data-ttu-id="a5883-153">このような状態を防ぐため、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ではセッション タイムアウト メカニズムが実装されており、接続されている可用性レプリカは、一定の間隔で、開いている各接続に対して ping を送信します。</span><span class="sxs-lookup"><span data-stu-id="a5883-153">To prevent this, [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] implements a session time-out mechanism, based on the connected availability replicas sending out a ping on each open connection at a fixed interval.</span></span> <span data-ttu-id="a5883-154">タイムアウト時間内に ping を受信した場合は、その接続がまだ開いており、サーバー インスタンスがその接続により通信していることを示します。</span><span class="sxs-lookup"><span data-stu-id="a5883-154">Receiving a ping during the time-out period indicates that the connection is still open and that the server instances are communicating over it.</span></span> <span data-ttu-id="a5883-155">ping を受信すると、レプリカはその接続に対するタイムアウト カウンターをリセットします。</span><span class="sxs-lookup"><span data-stu-id="a5883-155">On receiving a ping, a replica resets its time-out counter on that connection.</span></span> <span data-ttu-id="a5883-156">可用性モードとセッションタイムアウトの関係については、「[可用性モード (AlwaysOn 可用性グループ)](availability-modes-always-on-availability-groups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5883-156">For information about the relationship of availability mode and session timeouts, see [Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="a5883-157">プライマリ レプリカとセカンダリ レプリカは、アクティブであることを通知するために互いに ping を実行します。セッション タイムアウト制限を設定することにより、相手レプリカからの ping を受信するまで無期限に待機することがなくなります。</span><span class="sxs-lookup"><span data-stu-id="a5883-157">The primary and secondary replicas ping each other to signal that they are still active, and a session-timeout limit prevents either replica from waiting indefinitely to receive a ping from the other replica.</span></span> <span data-ttu-id="a5883-158">セッション タイムアウト制限はユーザーが構成できるレプリカ プロパティで、既定値は 10 秒です。</span><span class="sxs-lookup"><span data-stu-id="a5883-158">The session-timeout limit is a user-configurable replica property with a default value of 10 seconds.</span></span> <span data-ttu-id="a5883-159">タイムアウト時間内に ping を受信した場合は、その接続がまだ開いており、サーバー インスタンスがその接続により通信していることを示します。</span><span class="sxs-lookup"><span data-stu-id="a5883-159">Receiving a ping during the time-out period indicates that the connection is still open and that the server instances are communicating over it.</span></span> <span data-ttu-id="a5883-160">可用性レプリカは、ping を受信すると、接続のタイムアウト カウンターをリセットします。</span><span class="sxs-lookup"><span data-stu-id="a5883-160">On receiving a ping, an availability replica resets its time-out counter on that connection.</span></span>  
  
 <span data-ttu-id="a5883-161">セッションタイムアウト期間内に他のレプリカから ping を受信しなかった場合、接続はタイムアウトします。接続が閉じられ、タイムアウトしたレプリカが切断状態になります。</span><span class="sxs-lookup"><span data-stu-id="a5883-161">If no ping is received from the other replica within the session-timeout period, the connection times out. The connection is closed, and the timed-out replica enters the DISCONNECTED state.</span></span> <span data-ttu-id="a5883-162">切断されたレプリカが同期コミット モード用に構成されている場合でも、トランザクションは、そのレプリカが再接続および再同期するのを待機しません。</span><span class="sxs-lookup"><span data-stu-id="a5883-162">Even if a disconnected replica is configured for synchronous-commit mode, transactions will not wait for that replica to reconnect and resynchronize.</span></span>  
  
## <a name="responding-to-an-error"></a><span data-ttu-id="a5883-163">エラーへの対応</span><span class="sxs-lookup"><span data-stu-id="a5883-163">Responding to an Error</span></span>  
 <span data-ttu-id="a5883-164">エラーを検出したサーバー インスタンスは、エラーの種類に関係なく、インスタンスのロール、セッションの可用性モード、およびセッション内の他のすべての接続の状態に基づいて、適切な応答を行います。</span><span class="sxs-lookup"><span data-stu-id="a5883-164">Regardless of the type of error, a server instance that detects an error responds appropriately based on the role of the instance, the availability mode of the session, and the state of any other connection in the session.</span></span> <span data-ttu-id="a5883-165">パートナーが失われた場合の対処方法については、「[可用性モード (AlwaysOn 可用性グループ)](availability-modes-always-on-availability-groups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5883-165">For information about what occurs on the loss of a partner, see [Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="a5883-166">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="a5883-166">Related Tasks</span></span>  
 <span data-ttu-id="a5883-167">**タイムアウト値を変更するには (同期コミット可用性モードのみ)**</span><span class="sxs-lookup"><span data-stu-id="a5883-167">**To change the time-out value (synchronous-commit availability mode only)**</span></span>  
  
-   [<span data-ttu-id="a5883-168">可用性レプリカのセッション タイムアウト期間の変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a5883-168">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 <span data-ttu-id="a5883-169">**現在のタイムアウト値を表示するには**</span><span class="sxs-lookup"><span data-stu-id="a5883-169">**To view the current time-out value**</span></span>  
  
-   <span data-ttu-id="a5883-170">「[sys.availability_replicas &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)」で **session_timeout** クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="a5883-170">Query **session_timeout** in [sys.availability_replicas &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5883-171">参照</span><span class="sxs-lookup"><span data-stu-id="a5883-171">See Also</span></span>  
 [<span data-ttu-id="a5883-172">AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;</span><span class="sxs-lookup"><span data-stu-id="a5883-172">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
