---
title: ミラーリング状態 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- states [SQL Server], database mirroring
- PENDING_FAILOVER state
- mirroring states [SQL Server]
- DISCONNECTED state
- SYNCHRONIZING state
- SYNCHRONIZED state
- SUSPENDED state
- database mirroring [SQL Server], states
ms.assetid: 90062917-74f9-471b-b49e-bc153ae1a468
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d458939ba233bdfe7a99edd38afc74b5433ae061
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632653"
---
# <a name="mirroring-states-sql-server"></a><span data-ttu-id="ba09e-102">ミラーリング状態 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ba09e-102">Mirroring States (SQL Server)</span></span>
  <span data-ttu-id="ba09e-103">データベース ミラーリング セッション中、ミラー化されたデータベースは常に特定の状態 ( *ミラーリング状態*) にあります。</span><span class="sxs-lookup"><span data-stu-id="ba09e-103">During a database mirroring session, the mirrored database is always in a specific state (the *mirroring state*).</span></span> <span data-ttu-id="ba09e-104">データベースの状態は、通信状態、データ フロー、およびパートナー間のデータの違いを反映します。</span><span class="sxs-lookup"><span data-stu-id="ba09e-104">The state of the database reflects the communication status, data flow, and the difference in data between the partners.</span></span> <span data-ttu-id="ba09e-105">データベース ミラーリング セッションには、プリンシパル データベースと同じ状態が採用されます。</span><span class="sxs-lookup"><span data-stu-id="ba09e-105">The database mirroring session adopts the same state as the principal database.</span></span>  
  
 <span data-ttu-id="ba09e-106">各サーバー インスタンスは、データベース ミラーリング セッション全体を通して相互に監視します。</span><span class="sxs-lookup"><span data-stu-id="ba09e-106">Throughout a database mirroring session, the server instances monitor each other.</span></span> <span data-ttu-id="ba09e-107">各パートナーは、ミラーリング状態を使用してデータベースを監視します。</span><span class="sxs-lookup"><span data-stu-id="ba09e-107">The partners use the mirroring state to monitor the database.</span></span> <span data-ttu-id="ba09e-108">プリンシパル データベースとミラー データベースは、フェールオーバー保留中状態の場合を除いて常に同じ状態になります。</span><span class="sxs-lookup"><span data-stu-id="ba09e-108">With the exception of the PENDING_FAILOVER state, the principal and mirror database are always in the same state.</span></span> <span data-ttu-id="ba09e-109">ミラーリング監視サーバーがセッションに対して設定されている場合、各パートナーは、それぞれの接続状態 (接続または切断) を使用してミラーリング監視サーバーを監視します。</span><span class="sxs-lookup"><span data-stu-id="ba09e-109">If a witness is set for the session, each of the partners monitors the witness using its connection state (CONNECTED or DISCONNECTED).</span></span>  
  
 <span data-ttu-id="ba09e-110">次の表に、考えられるミラーリング状態を示します。</span><span class="sxs-lookup"><span data-stu-id="ba09e-110">The possible mirroring states of the database are as follows:</span></span>  
  
|<span data-ttu-id="ba09e-111">ミラーリング状態</span><span class="sxs-lookup"><span data-stu-id="ba09e-111">Mirroring state</span></span>|<span data-ttu-id="ba09e-112">説明</span><span class="sxs-lookup"><span data-stu-id="ba09e-112">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="ba09e-113">SYNCHRONIZING</span><span class="sxs-lookup"><span data-stu-id="ba09e-113">SYNCHRONIZING</span></span>|<span data-ttu-id="ba09e-114">ミラー データベースの内容が、プリンシパル データベースの内容に遅れています。</span><span class="sxs-lookup"><span data-stu-id="ba09e-114">The contents of the mirror database are lagging behind the contents of the principal database.</span></span> <span data-ttu-id="ba09e-115">プリンシパル サーバーからミラー サーバーにログ レコードを送信しています。ミラー サーバーでは、ミラー データベースをロールフォワードするために変更を適用しています。</span><span class="sxs-lookup"><span data-stu-id="ba09e-115">The principal server is sending log records to the mirror server, which is applying the changes to the mirror database to roll it forward.</span></span><br /><br /> <span data-ttu-id="ba09e-116">データベース ミラーリング セッションの開始時、データベースは同期中状態にあります。</span><span class="sxs-lookup"><span data-stu-id="ba09e-116">At the start of a database mirroring session, the database is in the SYNCHRONIZING state.</span></span> <span data-ttu-id="ba09e-117">プリンシパル サーバーはデータベースとして機能しており、ミラー サーバーは遅延を解消しようとしています。</span><span class="sxs-lookup"><span data-stu-id="ba09e-117">The principal server is serving the database, and the mirror is trying to catch up.</span></span>|  
|<span data-ttu-id="ba09e-118">SYNCHRONIZED</span><span class="sxs-lookup"><span data-stu-id="ba09e-118">SYNCHRONIZED</span></span>|<span data-ttu-id="ba09e-119">ミラー サーバーがプリンシパル サーバーとの遅延を解消すると、ミラーリング状態が同期状態になります。</span><span class="sxs-lookup"><span data-stu-id="ba09e-119">When the mirror server becomes sufficiently caught up to the principal server, the mirroring state changes to SYNCHRONIZED.</span></span> <span data-ttu-id="ba09e-120">プリンシパル サーバーがミラー サーバーに変更を送信し、ミラー サーバーがミラー データベースに変更を適用する、という処理が継続されている限り、データベースはこの状態のままです。</span><span class="sxs-lookup"><span data-stu-id="ba09e-120">The database remains in this state as long as the principal server continues to send changes to the mirror server and the mirror server continues to apply changes to the mirror database.</span></span><br /><br /> <span data-ttu-id="ba09e-121">トランザクションの安全性が FULL に設定されている場合、同期状態では自動フェールオーバーと手動フェールオーバーの両方がサポートされます。フェールオーバー後のデータの損失はありません。</span><span class="sxs-lookup"><span data-stu-id="ba09e-121">If transaction safety is set to FULLautomatic failover and manual failover are both supported in the SYNCHRONIZED state, there is no data loss after a failover.</span></span><br /><br /> <span data-ttu-id="ba09e-122">トランザクションの安全性が無効な場合は、同期状態の場合でも、一部データの損失の可能性が常にあります。</span><span class="sxs-lookup"><span data-stu-id="ba09e-122">If transaction safety is off, some data loss is always possible, even in the SYNCHRONIZED state.</span></span>|  
|<span data-ttu-id="ba09e-123">SUSPENDED</span><span class="sxs-lookup"><span data-stu-id="ba09e-123">SUSPENDED</span></span>|<span data-ttu-id="ba09e-124">データベースのミラー コピーは使用できない状態です。</span><span class="sxs-lookup"><span data-stu-id="ba09e-124">The mirror copy of the database is not available.</span></span> <span data-ttu-id="ba09e-125">プリンシパル データベースがミラー サーバーにログを送信せずに、実行されています。この状態を *不安定な実行*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="ba09e-125">The principal database is running without sending any logs to the mirror server, a condition known as *running exposed*.</span></span> <span data-ttu-id="ba09e-126">この状態はフェールオーバー後に発生します。</span><span class="sxs-lookup"><span data-stu-id="ba09e-126">This is the state after a failover.</span></span><br /><br /> <span data-ttu-id="ba09e-127">また、セッションは、再実行エラーの結果として、または管理者がセッションを一時停止した場合、中断状態になることがあります。</span><span class="sxs-lookup"><span data-stu-id="ba09e-127">A session can also become SUSPENDED as a result of redo errors or if the administrator pauses the session.</span></span><br /><br /> <span data-ttu-id="ba09e-128">中断状態は持続状態であり、パートナーがシャットダウンや起動を行っても保持されます。</span><span class="sxs-lookup"><span data-stu-id="ba09e-128">SUSPENDED is a persistent state that survives partner shutdowns and startups.</span></span>|  
|<span data-ttu-id="ba09e-129">PENDING_FAILOVER</span><span class="sxs-lookup"><span data-stu-id="ba09e-129">PENDING_FAILOVER</span></span>|<span data-ttu-id="ba09e-130">この状態は、フェールオーバーが開始された後、サーバーがまだミラーの役割に移行していない状態であり、プリンシパル サーバーだけで発生します。</span><span class="sxs-lookup"><span data-stu-id="ba09e-130">This state is found only on the principal server after a failover has begun, but the server has not transitioned into the mirror role.</span></span><br /><br /> <span data-ttu-id="ba09e-131">フェールオーバーが開始されると、プリンシパル データベースはフェールオーバー保留中状態になり、すべてのユーザー接続をすばやく終了し、その後すぐにミラーの役割を引き継ぎます。</span><span class="sxs-lookup"><span data-stu-id="ba09e-131">When the failover is initiated, the principal database goes into the PENDING_FAILOVER state, quickly terminates any user connections, and takes over the mirror role soon thereafter.</span></span>|  
|<span data-ttu-id="ba09e-132">DISCONNECTED</span><span class="sxs-lookup"><span data-stu-id="ba09e-132">DISCONNECTED</span></span>|<span data-ttu-id="ba09e-133">パートナーが、他のパートナーと通信できなくなった状態です。</span><span class="sxs-lookup"><span data-stu-id="ba09e-133">The partner has lost communication with the other partner.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba09e-134">参照</span><span class="sxs-lookup"><span data-stu-id="ba09e-134">See Also</span></span>  
 [<span data-ttu-id="ba09e-135">データベース ミラーリングの監視 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ba09e-135">Monitoring Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
