---
title: データベース ミラーリング中に発生する可能性のあるエラー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- time-out period [SQL Server database mirroring]
- soft errors [SQL Server]
- database mirroring [SQL Server], troubleshooting
- timeout errors [SQL Server]
- troubleshooting [SQL Server], database mirroring
- hard errors
- failed database mirroring sessions [SQL Server]
ms.assetid: d7031f58-5f49-4e6d-9a62-9b420f2bb17e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 25ba1ccc87c024fa3da370f2ff19251a1bee9f30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716786"
---
# <a name="possible-failures-during-database-mirroring"></a><span data-ttu-id="0cdec-102">データベース ミラーリング中に発生する可能性のあるエラー</span><span class="sxs-lookup"><span data-stu-id="0cdec-102">Possible Failures During Database Mirroring</span></span>
  <span data-ttu-id="0cdec-103">物理的な問題、オペレーティング システムの問題、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の問題により、データベース ミラーリング セッションが失敗する場合があります。</span><span class="sxs-lookup"><span data-stu-id="0cdec-103">Physical, operating system, or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] problems can cause a failure in a database mirroring session.</span></span> <span data-ttu-id="0cdec-104">データベース ミラーリングでは、Sqlservr.exe が依存しているコンポーネントを定期的にチェックして、それらのコンポーネントが正常に機能しているのか失敗したのかを確認する処理は行われません。</span><span class="sxs-lookup"><span data-stu-id="0cdec-104">Database mirroring does not regularly check the components on which Sqlservr.exe relies to verify whether they are functioning correctly or have failed.</span></span> <span data-ttu-id="0cdec-105">ただし、失敗の種類によっては、影響を受けたコンポーネントからエラーが Sqlservr.exe に報告されます。</span><span class="sxs-lookup"><span data-stu-id="0cdec-105">However, for some types of failures, the affected component reports an error to Sqlservr.exe.</span></span> <span data-ttu-id="0cdec-106">他のコンポーネントから報告されるエラーを *ハード エラー*といいます。</span><span class="sxs-lookup"><span data-stu-id="0cdec-106">An error reported by another component is called a *hard error*.</span></span> <span data-ttu-id="0cdec-107">データベース ミラーリングでは、通知されないその他の失敗を検出するために、独自のタイムアウト メカニズムを実装しています。</span><span class="sxs-lookup"><span data-stu-id="0cdec-107">To detect other failures that would otherwise go unnoticed, database mirroring implements its own time-out mechanism.</span></span> <span data-ttu-id="0cdec-108">ミラーリングでタイムアウトが発生すると、データベース ミラーリングでは失敗が発生したと想定し、 *ソフト エラー*を宣言します。</span><span class="sxs-lookup"><span data-stu-id="0cdec-108">When a mirroring time-out occurs, database mirroring assumes that a failure has occurred and declares a *soft error*.</span></span> <span data-ttu-id="0cdec-109">ただし、SQL Server のインスタンス レベルで発生する一部の失敗ではミラーリングがタイムアウトしないため、失敗が検出されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="0cdec-109">However, some failures that happen at the SQL Server instance level do not cause mirroring to time-out and can go undetected.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0cdec-110">ミラー化されたデータベース以外のデータベースで発生した障害は、データベース ミラーリング セッションでは検出されません。</span><span class="sxs-lookup"><span data-stu-id="0cdec-110">Failures in databases other than the mirrored database are not detectable in a database mirroring session.</span></span> <span data-ttu-id="0cdec-111">さらに、データ ディスクの障害によりデータベースが再起動した場合を除き、データ ディスクの障害はほとんど検出されません。</span><span class="sxs-lookup"><span data-stu-id="0cdec-111">Moreover, a data disk failure is unlikely to be detected, unless the database is restarted because of a data disk failure.</span></span>  
  
 <span data-ttu-id="0cdec-112">したがって、エラー検出の速度と、ミラーリング セッションの失敗への反応時間は、ハード エラーかソフト エラーかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="0cdec-112">The speed of error detection and, therefore, the reaction time of the mirroring session to a failure, depends on whether the error is hard or soft.</span></span> <span data-ttu-id="0cdec-113">ハード エラーの中には、ネットワーク障害など、直ちに報告されるものもあります。</span><span class="sxs-lookup"><span data-stu-id="0cdec-113">Some hard errors, such as network failures are reported immediately.</span></span> <span data-ttu-id="0cdec-114">しかし、場合によっては、コンポーネント固有のタイムアウト時間のために報告が遅くなるハード エラーもあります。</span><span class="sxs-lookup"><span data-stu-id="0cdec-114">However, in some cases, component-specific time-out periods can delay the reporting of some hard errors.</span></span> <span data-ttu-id="0cdec-115">ソフト エラーの場合は、ミラーリング タイムアウト時間の長さによってエラー検出の速度が決まります。</span><span class="sxs-lookup"><span data-stu-id="0cdec-115">For soft errors, the length of the mirroring time-out period determines the speed of error detection.</span></span> <span data-ttu-id="0cdec-116">既定では、この時間は 10 秒間です。</span><span class="sxs-lookup"><span data-stu-id="0cdec-116">By default, this period is 10 seconds.</span></span> <span data-ttu-id="0cdec-117">これは推奨最小値です。</span><span class="sxs-lookup"><span data-stu-id="0cdec-117">This is the minimum recommended value.</span></span>  
  
## <a name="failures-due-to-hard-errors"></a><span data-ttu-id="0cdec-118">ハード エラーによるエラー</span><span class="sxs-lookup"><span data-stu-id="0cdec-118">Failures Due to Hard Errors</span></span>  
 <span data-ttu-id="0cdec-119">次のような状況が、ハード エラーの原因になる可能性があります (ただし、これだけではありません)。</span><span class="sxs-lookup"><span data-stu-id="0cdec-119">Possible causes of hard errors include (but are not limited to) the following conditions:</span></span>  
  
-   <span data-ttu-id="0cdec-120">接続またはケーブルの切断</span><span class="sxs-lookup"><span data-stu-id="0cdec-120">A broken connection or wire</span></span>  
  
-   <span data-ttu-id="0cdec-121">不適切なネットワーク カード</span><span class="sxs-lookup"><span data-stu-id="0cdec-121">A bad network card</span></span>  
  
-   <span data-ttu-id="0cdec-122">ルーターの変更</span><span class="sxs-lookup"><span data-stu-id="0cdec-122">A router change</span></span>  
  
-   <span data-ttu-id="0cdec-123">ファイアウォールの設定変更</span><span class="sxs-lookup"><span data-stu-id="0cdec-123">Changes in the firewall</span></span>  
  
-   <span data-ttu-id="0cdec-124">エンドポイントの再構成</span><span class="sxs-lookup"><span data-stu-id="0cdec-124">Endpoint reconfiguration</span></span>  
  
-   <span data-ttu-id="0cdec-125">トランザクション ログの保存先ドライブの消失</span><span class="sxs-lookup"><span data-stu-id="0cdec-125">Loss of the drive where the transaction log resides</span></span>  
  
-   <span data-ttu-id="0cdec-126">オペレーティング システムまたはプロセスのエラー</span><span class="sxs-lookup"><span data-stu-id="0cdec-126">Operating system or process failure</span></span>  
  
 <span data-ttu-id="0cdec-127">たとえば、プリンシパル データベースのログ ドライブが応答を停止し障害が発生すると、オペレーティング システムから Sqlservr.exe に、深刻なエラーが発生したことが通知されます。</span><span class="sxs-lookup"><span data-stu-id="0cdec-127">For example, when the log drive on the principal database becomes unresponsive and fails, the operating system informs Sqlservr.exe that a serious error has occurred.</span></span>  
  
 <span data-ttu-id="0cdec-128">ネットワーク コンポーネントや一部の IO サブシステムなど、コンポーネントによっては、障害を特定するための独自のタイムアウトを実装しているものもあります。</span><span class="sxs-lookup"><span data-stu-id="0cdec-128">Some components, such as network components and some IO subsystems, have their own time-outs to determine failures.</span></span> <span data-ttu-id="0cdec-129">このようなタイムアウトはデータベース ミラーリングとは独立して機能します。データベース ミラーリングでは、そのタイムアウトを認識したり、その動作を完全に把握することはありません。</span><span class="sxs-lookup"><span data-stu-id="0cdec-129">Such time-outs are independent of database mirroring, which has no knowledge of them and is completely unaware of their behavior.</span></span> <span data-ttu-id="0cdec-130">このような場合、タイムアウトの遅延により、障害が発生してから、データベース ミラーリングがハード エラーを受け取るまでの時間が増加します。</span><span class="sxs-lookup"><span data-stu-id="0cdec-130">In these cases, the time-out delay increases the time between a failure and when database mirroring receive the resulting hard error.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0cdec-131">ソフト エラーの場合には、データベース ミラーリングに対して実行されるアクティブなエラー チェックだけが発生します。</span><span class="sxs-lookup"><span data-stu-id="0cdec-131">The only active error checking performed for database mirroring occurs for soft error cases.</span></span> <span data-ttu-id="0cdec-132">詳細については、このトピックの後半の「ソフト エラーによるエラー」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0cdec-132">For more information, see "Failures Due to Soft Errors," later in this topic.</span></span>  
  
 <span data-ttu-id="0cdec-133">ネットワーク上で発生しているエラー状態を把握できるように、次のようなイベントが TCP 接続で発生した場合にはどのようなエラー メッセージがポートに送信されるのかを、ネットワーク エンジニアに問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="0cdec-133">To help you interpret the error conditions that occur on the network, ask a network engineer what error messages are sent to a port when the following events occur on a TCP connection:</span></span>  
  
-   <span data-ttu-id="0cdec-134">DNS が動作していません。</span><span class="sxs-lookup"><span data-stu-id="0cdec-134">DNS is not working.</span></span>  
  
-   <span data-ttu-id="0cdec-135">ケーブルが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="0cdec-135">Cables are unplugged.</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="0cdec-136">Windows に存在します。</span><span class="sxs-lookup"><span data-stu-id="0cdec-136">Windows has a firewall that blocks a specific port.</span></span>  
  
-   <span data-ttu-id="0cdec-137">ポートを監視しているアプリケーションで障害が発生しています。</span><span class="sxs-lookup"><span data-stu-id="0cdec-137">The application that is monitoring a port fails.</span></span>  
  
-   <span data-ttu-id="0cdec-138">Windows ベースのサーバーの名前が変更されています。</span><span class="sxs-lookup"><span data-stu-id="0cdec-138">A Windows-based server is renamed.</span></span>  
  
-   <span data-ttu-id="0cdec-139">Windows ベースのサーバーが再起動されています。</span><span class="sxs-lookup"><span data-stu-id="0cdec-139">A Windows-based server is rebooted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0cdec-140">サーバーにアクセスするクライアント専用のパブリック NIC の障害はミラーリングによって保証されません。</span><span class="sxs-lookup"><span data-stu-id="0cdec-140">Mirroring does not protect against problems specific to client accessing the servers.</span></span> <span data-ttu-id="0cdec-141">たとえば、パブリック ネットワーク アダプターがプリンシパル サーバー インスタンスへのクライアント接続を処理していて、プライベート ネットワーク インターフェイス カードがサーバー インスタンス間のすべてのミラーリング トラフィックを処理している場合を考えます。</span><span class="sxs-lookup"><span data-stu-id="0cdec-141">For example, consider a case in which a public network adapter handles client connections to the principal server instance, while a private network interface card handles all mirroring traffic among server instances.</span></span> <span data-ttu-id="0cdec-142">この場合、パブリック ネットワーク アダプターに障害が生じると、クライアントはデータベースにアクセスできなくなります。ただし、データベースのミラー化は引き続き行われます。</span><span class="sxs-lookup"><span data-stu-id="0cdec-142">In this case, failure of the public network adapter would prevent clients from accessing the database, though the database would continue to be mirrored.</span></span>  
  
## <a name="failures-due-to-soft-errors"></a><span data-ttu-id="0cdec-143">ソフト エラーによるエラー</span><span class="sxs-lookup"><span data-stu-id="0cdec-143">Failures Due to Soft Errors</span></span>  
 <span data-ttu-id="0cdec-144">次のような状況が、ミラーリング タイムアウトの原因になる可能性があります (ただし、これだけではありません)。</span><span class="sxs-lookup"><span data-stu-id="0cdec-144">Conditions that might cause mirroring time-outs include (but are not limited to) the following:</span></span>  
  
-   <span data-ttu-id="0cdec-145">TCP リンクのタイムアウト、パケットの紛失または破損、不正な順序のパケットなどのネットワーク エラー。</span><span class="sxs-lookup"><span data-stu-id="0cdec-145">Network errors such as TCP link time-outs, dropped or corrupted packets, or packets that are in an incorrect order.</span></span>  
  
-   <span data-ttu-id="0cdec-146">オペレーティング システム、サーバー、またはデータベースの応答の停止。</span><span class="sxs-lookup"><span data-stu-id="0cdec-146">An operating system, server, or database that is not responding.</span></span>  
  
-   <span data-ttu-id="0cdec-147">Windows サーバーのタイムアウト。</span><span class="sxs-lookup"><span data-stu-id="0cdec-147">A Windows server timing out.</span></span>  
  
-   <span data-ttu-id="0cdec-148">CPU やディスクの過負荷、いっぱいになったトランザクション ログ、メモリやスレッドが不足しているシステムなど、コンピューティング リソースの不足。</span><span class="sxs-lookup"><span data-stu-id="0cdec-148">Insufficient computing resources, such as a CPU or disk overload, the transaction log filling up, or the system is running out of memory or threads.</span></span> <span data-ttu-id="0cdec-149">このような場合は、タイムアウト期間を長くするか、ワークロードを軽減するか、ハードウェアを交換してワークロードを処理できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0cdec-149">In these cases, you must increase the time-out period, reduce the workload, or change the hardware to handle the workload.</span></span>  
  
### <a name="the-mirroring-time-out-mechanism"></a><span data-ttu-id="0cdec-150">ミラーリング タイムアウトのメカニズム</span><span class="sxs-lookup"><span data-stu-id="0cdec-150">The Mirroring Time-Out Mechanism</span></span>  
 <span data-ttu-id="0cdec-151">サーバー インスタンスはソフト エラーを直接検出できないので、ソフト エラーのために、サーバー インスタンスが無限に待機する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0cdec-151">Because soft errors are not detectable directly by a server instance, a soft error could potentially cause a server instance to wait indefinitely.</span></span> <span data-ttu-id="0cdec-152">このような状態を防ぐため、データベース ミラーリングではタイムアウト メカニズムが実装されており、ミラーリング セッション内の各サーバー インスタンスは、一定の間隔で、開いている各接続に対して ping を送信します。</span><span class="sxs-lookup"><span data-stu-id="0cdec-152">To prevent this, database mirroring implements its own time-out mechanism, based on each server instance in a mirroring session sending out a ping on each open connection at a fixed interval.</span></span>  
  
 <span data-ttu-id="0cdec-153">接続が開いた状態を維持するためには、定義されたタイムアウト期間と、ping をもう 1 回送信するために必要な時間を足した時間内に、その接続でサーバー インスタンスが ping を受信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0cdec-153">To keep a connection open, a server instance must receive a ping on that connection in the time-out period defined, plus the time that is required to send one more ping.</span></span> <span data-ttu-id="0cdec-154">タイムアウト時間内に ping を受信した場合は、その接続がまだ開いており、サーバー インスタンスがその接続により通信していることを示します。</span><span class="sxs-lookup"><span data-stu-id="0cdec-154">Receiving a ping during the time-out period indicates that the connection is still open and that the server instances are communicating over it.</span></span> <span data-ttu-id="0cdec-155">ping を受信すると、サーバー インスタンスはその接続に対するタイムアウト カウンターをリセットします。</span><span class="sxs-lookup"><span data-stu-id="0cdec-155">On receiving a ping, a server instance resets its time-out counter on that connection.</span></span>  
  
 <span data-ttu-id="0cdec-156">タイムアウト時間内に接続で ping を受信しない場合、サーバー インスタンスは接続がタイムアウトしたものと見なします。サーバー インスタンスは、タイムアウトした接続を閉じ、セッションの状態と動作モードに従ってタイムアウト イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="0cdec-156">If no ping is received on a connection during the time-out period, a server instance considers the connection to have timed out. The server instance closes the timed-out connection and handles the time-out event according to the state and operating mode of the session.</span></span>  
  
 <span data-ttu-id="0cdec-157">他のサーバーが実際には正常に動作し続けていたとしても、タイムアウトは障害と見なされます。</span><span class="sxs-lookup"><span data-stu-id="0cdec-157">Even if the other server is actually proceeding correctly, a time-out is considered a failure.</span></span> <span data-ttu-id="0cdec-158">いずれかのパートナーの通常の応答時間に対し、セッションのタイムアウト値が短すぎる場合は、誤認エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0cdec-158">If the time-out value for a session is too short for the regular responsiveness of either partner, false failures can occur.</span></span> <span data-ttu-id="0cdec-159">あるサーバー インスタンスが別のサーバー インスタンスに正常に接続しても、接続先の応答時間が遅すぎて、タイムアウト時間が経過する前に ping を受信できない場合、誤認エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="0cdec-159">A false failure occurs when one server instance successfully contacts another whose response time is so slow that its pings are not received before the time-out period expires.</span></span>  
  
 <span data-ttu-id="0cdec-160">高パフォーマンス モードのセッションでは、タイムアウト時間は常に 10 秒です。</span><span class="sxs-lookup"><span data-stu-id="0cdec-160">In high-performance mode sessions, the time-out period is always 10 seconds.</span></span> <span data-ttu-id="0cdec-161">これは一般的に誤認エラーを避けるには十分な時間です。</span><span class="sxs-lookup"><span data-stu-id="0cdec-161">This is generally enough to avoid false failures.</span></span> <span data-ttu-id="0cdec-162">高い安全性モードのセッションでは、既定のタイムアウト時間は 10 秒ですが、変更できます。</span><span class="sxs-lookup"><span data-stu-id="0cdec-162">In high-safety mode sessions, the default time-out period is 10 seconds, but you can change the duration.</span></span> <span data-ttu-id="0cdec-163">誤認エラーを避けるために、ミラーリングのタイムアウト時間を常に 10 秒以上にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0cdec-163">To avoid false failures, we recommend that the mirroring time-out period always be 10 seconds or more.</span></span>  
  
 <span data-ttu-id="0cdec-164">**タイムアウト値を変更するには (高い安全性モードのみ)**</span><span class="sxs-lookup"><span data-stu-id="0cdec-164">**To change the time-out value (high-safety mode only)**</span></span>  
  
-   <span data-ttu-id="0cdec-165">[ALTER DATABASE \<database> SET PARTNER TIMEOUT \<integer>](/sql/t-sql/statements/alter-database-transact-sql) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="0cdec-165">Use the [ALTER DATABASE \<database> SET PARTNER TIMEOUT \<integer>](/sql/t-sql/statements/alter-database-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="0cdec-166">**現在のタイムアウト値を表示するには**</span><span class="sxs-lookup"><span data-stu-id="0cdec-166">**To view the current time-out value**</span></span>  
  
-   <span data-ttu-id="0cdec-167">**sys.database_mirroring** の [mirroring_connection_timeout](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql)にクエリを行います。</span><span class="sxs-lookup"><span data-stu-id="0cdec-167">Query **mirroring_connection_timeout** in [sys.database_mirroring](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql).</span></span>  
  
## <a name="responding-to-an-error"></a><span data-ttu-id="0cdec-168">エラーへの対応</span><span class="sxs-lookup"><span data-stu-id="0cdec-168">Responding to an Error</span></span>  
 <span data-ttu-id="0cdec-169">エラーを検出したサーバー インスタンスは、エラーの種類に関係なく、インスタンスのロール、セッションの動作モード、およびセッション内の他のすべての接続の状態に基づいて、適切な応答を行います。</span><span class="sxs-lookup"><span data-stu-id="0cdec-169">Regardless of the type of error, a server instance that detects an error responds appropriately based on the role of the instance, the operating mode of the session, and the state of any other connection in the session.</span></span> <span data-ttu-id="0cdec-170">パートナーと通信できなくなった場合の処置の詳細については、「 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0cdec-170">For information about what occurs on the loss of a partner, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cdec-171">参照</span><span class="sxs-lookup"><span data-stu-id="0cdec-171">See Also</span></span>  
 <span data-ttu-id="0cdec-172">[役割の交代中に発生するサービスの中断時間の算出 &#40;データベース ミラーリング&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="0cdec-172">[Estimate the Interruption of Service During Role Switching &#40;Database Mirroring&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md) </span></span>  
 <span data-ttu-id="0cdec-173">[データベース ミラーリングの動作モード](database-mirroring-operating-modes.md) </span><span class="sxs-lookup"><span data-stu-id="0cdec-173">[Database Mirroring Operating Modes](database-mirroring-operating-modes.md) </span></span>  
 <span data-ttu-id="0cdec-174">[データベース ミラーリング セッション中の役割の交代 &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0cdec-174">[Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md) </span></span>  
 [<span data-ttu-id="0cdec-175">データベース ミラーリング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0cdec-175">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
