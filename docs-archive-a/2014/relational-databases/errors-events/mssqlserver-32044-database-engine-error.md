---
title: MSSQLSERVER_32044 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 32044 (Database Engine error)
ms.assetid: f2d073be-d9a1-4837-8a38-028d3e3403bd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 27d9655c3a908f1302f048c6f68159d4f610367a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640036"
---
# <a name="mssqlserver_32044"></a><span data-ttu-id="7fcd3-102">MSSQLSERVER_32044</span><span class="sxs-lookup"><span data-stu-id="7fcd3-102">MSSQLSERVER_32044</span></span>
    
## <a name="details"></a><span data-ttu-id="7fcd3-103">詳細</span><span class="sxs-lookup"><span data-stu-id="7fcd3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7fcd3-104">製品名</span><span class="sxs-lookup"><span data-stu-id="7fcd3-104">Product Name</span></span>|<span data-ttu-id="7fcd3-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7fcd3-105">SQL Server</span></span>|  
|<span data-ttu-id="7fcd3-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="7fcd3-106">Event ID</span></span>|<span data-ttu-id="7fcd3-107">32044</span><span class="sxs-lookup"><span data-stu-id="7fcd3-107">32044</span></span>|  
|<span data-ttu-id="7fcd3-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="7fcd3-108">Event Source</span></span>|<span data-ttu-id="7fcd3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7fcd3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7fcd3-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7fcd3-110">Component</span></span>|<span data-ttu-id="7fcd3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="7fcd3-111">SQLEngine</span></span>|  
|<span data-ttu-id="7fcd3-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="7fcd3-112">Symbolic Name</span></span>|<span data-ttu-id="7fcd3-113">SQLErrorNum32044</span><span class="sxs-lookup"><span data-stu-id="7fcd3-113">SQLErrorNum32044</span></span>|  
|<span data-ttu-id="7fcd3-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="7fcd3-114">Message Text</span></span>|<span data-ttu-id="7fcd3-115">'ミラー コミットのオーバーヘッド' の警告が発生しました。</span><span class="sxs-lookup"><span data-stu-id="7fcd3-115">The alert for 'mirror commit overhead' has been raised.</span></span> <span data-ttu-id="7fcd3-116">現在の値 '%d' はしきい値 '%d' を上回っています。</span><span class="sxs-lookup"><span data-stu-id="7fcd3-116">The current value of '%d' surpasses the threshold '%d'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7fcd3-117">説明</span><span class="sxs-lookup"><span data-stu-id="7fcd3-117">Explanation</span></span>  
 <span data-ttu-id="7fcd3-118">このデータベース ミラーリング イベントはプリンシパル サーバー インスタンスで発生し、データベース ミラーリングが原因で、コミットの合計待機時間がユーザー指定のしきい値に達したか、それを超えたことを示します。</span><span class="sxs-lookup"><span data-stu-id="7fcd3-118">This database mirroring event is issued on the principal server instance to indicate that the aggregate commit wait time reached or exceeded a user-specified threshold value because of database mirroring.</span></span> <span data-ttu-id="7fcd3-119">待機時間は、トランザクション数と各トランザクションの待機時間の積です。</span><span class="sxs-lookup"><span data-stu-id="7fcd3-119">The wait time is the product of the number of transactions and the time of each.</span></span> <span data-ttu-id="7fcd3-120">たとえば、次のような場合は、どちらも待機時間が 1000 ミリ秒になります: トランザクション 1000 回 \* 1 ミリ秒、トランザクション 1 回 \* 1000 ミリ秒。</span><span class="sxs-lookup"><span data-stu-id="7fcd3-120">For example, the following cases both produce 1000 milliseconds of wait time: 1000 transactions \* 1 millisecond, and 1 transaction \* 1000 milliseconds.</span></span> <span data-ttu-id="7fcd3-121">コミットの待機時間が増加するのは、ミラー サーバー インスタンスでのトランザクション数の増加、ログ送信の遅れ、またはログ フラッシュの遅れが原因の可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7fcd3-121">An increased commit wait time can be caused by a surge in the transaction count, delays in sending the log, or delays in flushing the log on the mirror server instance.</span></span>  
  
 <span data-ttu-id="7fcd3-122">ミラー コミットのオーバーヘッドの量は、同期操作によって現在のパフォーマンスに与える影響を評価するのに役立つパフォーマンス基準です。</span><span class="sxs-lookup"><span data-stu-id="7fcd3-122">The amount of mirror commit overhead is a performance metric that can help you evaluate the current performance impact of synchronous operation.</span></span> <span data-ttu-id="7fcd3-123">この基準は、高い安全性モードのみに関連しています。</span><span class="sxs-lookup"><span data-stu-id="7fcd3-123">This metric is relevant only in high-safety mode.</span></span> <span data-ttu-id="7fcd3-124">高い安全性モードは同期モードなので、プリンシパル サーバー インスタンスでは、ミラー サーバー インスタンスにログ レコードを送信後、ミラー サーバー インスタンスがディスクにログ レコードを書き込んだことを確認できるまで、トランザクションのコミットを待機します。</span><span class="sxs-lookup"><span data-stu-id="7fcd3-124">Because high-safety mode is synchronous, the principal server instance waits to commit the transaction after it sends a log record to the mirror server instance until it receives confirmation that the mirror server instance has written the log record to disk.</span></span> <span data-ttu-id="7fcd3-125">ログ レコードは、ミラー データベースへの復元を待機している間は、ミラー サーバー インスタンスのディスクに残ります。</span><span class="sxs-lookup"><span data-stu-id="7fcd3-125">The log record remains on disk on the mirror server instance while it waits to be restored to the mirror database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7fcd3-126">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="7fcd3-126">User Action</span></span>  
 <span data-ttu-id="7fcd3-127">プリンシパル サーバー インスタンス、ミラー サーバー インスタンス、および両者のネットワーク接続の負荷が原因になっているかどうかを調査します。</span><span class="sxs-lookup"><span data-stu-id="7fcd3-127">Check the loads on the principal and mirror server instances and their network connection for the cause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fcd3-128">参照</span><span class="sxs-lookup"><span data-stu-id="7fcd3-128">See Also</span></span>  
 <span data-ttu-id="7fcd3-129">[データベース ミラーリング &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7fcd3-129">[Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="7fcd3-130">ミラーリング パフォーマンス基準の警告しきい値および警告の使用 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7fcd3-130">Use Warning Thresholds and Alerts on Mirroring Performance Metrics &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
  
