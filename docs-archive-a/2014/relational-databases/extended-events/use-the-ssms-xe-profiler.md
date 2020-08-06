---
title: system_health セッションの使用 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], system health session
- extended events [SQL Server], system_health session
- system_health session [SQL Server extended events]
- system health session [SQL Server extended events]
ms.assetid: 1e1fad43-d747-4775-ac0d-c50648e56d78
author: yualan
ms.author: alayu
ms.openlocfilehash: 86c3221fb4c0ea0690b369888ac8f2f9f82d6ef9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631910"
---
# <a name="use-the-system_health-session"></a><span data-ttu-id="79360-102">system_health セッションの使用</span><span class="sxs-lookup"><span data-stu-id="79360-102">Use the system_health Session</span></span>
  <span data-ttu-id="79360-103">system_health セッションは、既定で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に含まれている拡張イベント セッションです。</span><span class="sxs-lookup"><span data-stu-id="79360-103">The system_health session is an Extended Events session that is included by default with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="79360-104">このセッションは、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] の起動時に自動的に開始されます。実行中にパフォーマンスに大きな影響が及ぶことはありません。</span><span class="sxs-lookup"><span data-stu-id="79360-104">This session starts automatically when the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] starts, and runs without any noticeable performance effects.</span></span> <span data-ttu-id="79360-105">[!INCLUDE[ssDE](../../includes/ssde-md.md)]のパフォーマンスの問題をトラブルシューティングするのに役立つシステム データを収集します。</span><span class="sxs-lookup"><span data-stu-id="79360-105">The session collects system data that you can use to help troubleshoot performance issues in the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="79360-106">そのため、このセッションを停止または削除しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="79360-106">Therefore, we recommend that you do not stop or delete the session.</span></span>  
  
 <span data-ttu-id="79360-107">このセッションでは、次の情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="79360-107">The session collects information that includes the following:</span></span>  
  
-   <span data-ttu-id="79360-108">重大度が 20 以上のエラーが発生したすべてのセッションの sql_text と session_id。</span><span class="sxs-lookup"><span data-stu-id="79360-108">The sql_text and session_id for any sessions that encounter an error that has a severity >=20.</span></span>  
  
-   <span data-ttu-id="79360-109">メモリ関連のエラーが発生したすべてのセッションの sql_text とsession_id。</span><span class="sxs-lookup"><span data-stu-id="79360-109">The sql_text and session_id for any sessions that encounter a memory-related error.</span></span> <span data-ttu-id="79360-110">エラーには、17803、701、802、8645、8651、8657、8902 などがあります。</span><span class="sxs-lookup"><span data-stu-id="79360-110">The errors include 17803, 701, 802, 8645, 8651, 8657 and 8902.</span></span>  
  
-   <span data-ttu-id="79360-111">応答していないスケジューラの問題の記録</span><span class="sxs-lookup"><span data-stu-id="79360-111">A record of any non-yielding scheduler problems.</span></span> <span data-ttu-id="79360-112">(これらはエラー 17883 として [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログに書き込まれます)。</span><span class="sxs-lookup"><span data-stu-id="79360-112">(These appear in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log as error 17883.)</span></span>  
  
-   <span data-ttu-id="79360-113">検出されたすべてのデッドロック。</span><span class="sxs-lookup"><span data-stu-id="79360-113">Any deadlocks that are detected.</span></span>  
  
-   <span data-ttu-id="79360-114">ラッチ (またはその他の注目する必要があるリソース) での待機時間が 15 秒を超えるすべてのセッションの callstack、sql_text、および session_id。</span><span class="sxs-lookup"><span data-stu-id="79360-114">The callstack, sql_text, and session_id for any sessions that have waited on latches (or other interesting resources) for > 15 seconds.</span></span>  
  
-   <span data-ttu-id="79360-115">ロックでの待機時間が 30 秒を超えるすべてのセッションの callstack、sql_text、および session_id。</span><span class="sxs-lookup"><span data-stu-id="79360-115">The callstack, sql_text, and session_id for any sessions that have waited on locks for > 30 seconds.</span></span>  
  
-   <span data-ttu-id="79360-116">プリエンプティブ待機のために長時間待機しているすべてのセッションの callstack、sql_text、および session_id。</span><span class="sxs-lookup"><span data-stu-id="79360-116">The callstack, sql_text, and session_id for any sessions that have waited for a long time for preemptive waits.</span></span> <span data-ttu-id="79360-117">待機時間は、待機の種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="79360-117">The duration varies by wait type.</span></span> <span data-ttu-id="79360-118">プリエンプティブ待機とは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が外部の API 呼び出しを待機している状態です。</span><span class="sxs-lookup"><span data-stu-id="79360-118">A preemptive wait is where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is waiting for external API calls.</span></span>  
  
-   <span data-ttu-id="79360-119">CLR の割り当てと仮想の割り当ての失敗に対する呼び出し履歴と session_id。</span><span class="sxs-lookup"><span data-stu-id="79360-119">The callstack and session_id for CLR allocation and virtual allocation failures.</span></span>  
  
-   <span data-ttu-id="79360-120">メモリ ブローカー、スケジューラ モニター、メモリ ノード OOM、セキュリティ、接続性に関する ring_buffer イベント。</span><span class="sxs-lookup"><span data-stu-id="79360-120">The ring_buffer events for the memory broker, scheduler monitor, memory node OOM, security, and connectivity.</span></span>  
  
-   <span data-ttu-id="79360-121">sp_server_diagnostics からのシステム コンポーネントの結果。</span><span class="sxs-lookup"><span data-stu-id="79360-121">System component results from sp_server_diagnostics.</span></span>  
  
-   <span data-ttu-id="79360-122">scheduler_monitor_system_health_ring_buffer_recorded によって収集されたインスタンスの正常性。</span><span class="sxs-lookup"><span data-stu-id="79360-122">Instance health collected by scheduler_monitor_system_health_ring_buffer_recorded.</span></span>  
  
-   <span data-ttu-id="79360-123">CLR 割り当ての失敗。</span><span class="sxs-lookup"><span data-stu-id="79360-123">CLR Allocation failures.</span></span>  
  
-   <span data-ttu-id="79360-124">connectivity_ring_buffer_recorded を使用する接続のエラー。</span><span class="sxs-lookup"><span data-stu-id="79360-124">Connectivity errors using connectivity_ring_buffer_recorded.</span></span>  
  
-   <span data-ttu-id="79360-125">security_error_ring_buffer_recorded を使用するセキュリティのエラー。</span><span class="sxs-lookup"><span data-stu-id="79360-125">Security errors using security_error_ring_buffer_recorded.</span></span>  
  
## <a name="viewing-the-session-data"></a><span data-ttu-id="79360-126">セッション データの表示</span><span class="sxs-lookup"><span data-stu-id="79360-126">Viewing the Session Data</span></span>  
 <span data-ttu-id="79360-127">このセッションでは、リング バッファー ターゲットを使用して、データを格納します。</span><span class="sxs-lookup"><span data-stu-id="79360-127">The session uses the ring buffer target to store the data.</span></span> <span data-ttu-id="79360-128">セッション データを表示するには、次のクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="79360-128">To view the session data, use the following query:</span></span>  
  
```  
SELECT CAST(xet.target_data as xml) FROM sys.dm_xe_session_targets xet  
JOIN sys.dm_xe_sessions xe  
ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'system_health'  
```  
  
 <span data-ttu-id="79360-129">イベント ファイルからセッション データを表示するには、Management Studio の拡張イベント ユーザー インターフェイスを使用します。</span><span class="sxs-lookup"><span data-stu-id="79360-129">To view the session data from the event file, use the Extended Events user interface available in Management Studio.</span></span> <span data-ttu-id="79360-130">詳細については、「[イベントセッションデータの表示](../../database-engine/view-event-session-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79360-130">See [View Event Session Data](../../database-engine/view-event-session-data.md) for more information.</span></span>  
  
## <a name="restoring-the-system_health-session"></a><span data-ttu-id="79360-131">system_health セッションの復元</span><span class="sxs-lookup"><span data-stu-id="79360-131">Restoring the system_health Session</span></span>  
 <span data-ttu-id="79360-132">system_health セッションを削除した場合、クエリ エディターで **u_tables.sql** ファイルを実行することでそのセッションを復元できます。</span><span class="sxs-lookup"><span data-stu-id="79360-132">If you delete the system_health session, you can restore it by executing the **u_tables.sql** file in Query Editor.</span></span> <span data-ttu-id="79360-133">このファイルは次のフォルダーにあります (C: は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プログラム ファイルのインストール先ドライブを表しています)。</span><span class="sxs-lookup"><span data-stu-id="79360-133">This file is located in the following folder, where C: represents the drive where you installed the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] program files:</span></span>  
  
 <span data-ttu-id="79360-134">C:\Program Server\MSSQL12. \<*instanceid*> SQL\MSSQL\Install</span><span class="sxs-lookup"><span data-stu-id="79360-134">C:\Program Files\Microsoft SQL Server\MSSQL12.\<*instanceid*>\MSSQL\Install</span></span>  
  
 <span data-ttu-id="79360-135">セッションを復元したら、ALTER EVENT SESSION ステートメントを使用するか、オブジェクト エクスプローラーで **[拡張イベント]** ノードを使用して、セッションを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="79360-135">Be aware that after you restore the session, you must start the session by using the ALTER EVENT SESSION statement or by using the **Extended Events** node in Object Explorer.</span></span> <span data-ttu-id="79360-136">ただし、そのようにして開始しない場合でも、次に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを再起動したときにセッションは自動的に開始されます。</span><span class="sxs-lookup"><span data-stu-id="79360-136">Otherwise, the session starts automatically the next time that you restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79360-137">参照</span><span class="sxs-lookup"><span data-stu-id="79360-137">See Also</span></span>  
 [<span data-ttu-id="79360-138">拡張イベントのツール</span><span class="sxs-lookup"><span data-stu-id="79360-138">Extended Events Tools</span></span>](extended-events-tools.md)  
  
  
