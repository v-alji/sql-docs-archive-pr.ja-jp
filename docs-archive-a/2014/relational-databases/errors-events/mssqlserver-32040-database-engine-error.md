---
title: MSSQLSERVER_32040 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 32040 (Database Engine error)
ms.assetid: 709219b1-f8b2-4696-8923-dd2e91492eb8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 05692e2f20b0719c1ca8f48282c3b7aaed8e2341
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640038"
---
# <a name="mssqlserver_32040"></a><span data-ttu-id="257ac-102">MSSQLSERVER_32040</span><span class="sxs-lookup"><span data-stu-id="257ac-102">MSSQLSERVER_32040</span></span>
    
## <a name="details"></a><span data-ttu-id="257ac-103">詳細</span><span class="sxs-lookup"><span data-stu-id="257ac-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="257ac-104">製品名</span><span class="sxs-lookup"><span data-stu-id="257ac-104">Product Name</span></span>|<span data-ttu-id="257ac-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="257ac-105">SQL Server</span></span>|  
|<span data-ttu-id="257ac-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="257ac-106">Event ID</span></span>|<span data-ttu-id="257ac-107">32040</span><span class="sxs-lookup"><span data-stu-id="257ac-107">32040</span></span>|  
|<span data-ttu-id="257ac-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="257ac-108">Event Source</span></span>|<span data-ttu-id="257ac-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="257ac-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="257ac-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="257ac-110">Component</span></span>|<span data-ttu-id="257ac-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="257ac-111">SQLEngine</span></span>|  
|<span data-ttu-id="257ac-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="257ac-112">Symbolic Name</span></span>|<span data-ttu-id="257ac-113">SQLErrorNum32040</span><span class="sxs-lookup"><span data-stu-id="257ac-113">SQLErrorNum32040</span></span>|  
|<span data-ttu-id="257ac-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="257ac-114">Message Text</span></span>|<span data-ttu-id="257ac-115">'最も古い未送信のトランザクション' の警告が発生しました。</span><span class="sxs-lookup"><span data-stu-id="257ac-115">The alert for 'oldest unsent transaction' has been raised.</span></span> <span data-ttu-id="257ac-116">現在の値 '%d' はしきい値 '%d' を上回っています。</span><span class="sxs-lookup"><span data-stu-id="257ac-116">The current value of '%d' surpasses the threshold '%d'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="257ac-117">説明</span><span class="sxs-lookup"><span data-stu-id="257ac-117">Explanation</span></span>  
 <span data-ttu-id="257ac-118">このデータベース ミラーリング イベントはプリンシパル サーバー インスタンスで発生し、最も古い未送信のトランザクションの経過期間がユーザー指定のしきい値に達したことを示しています。</span><span class="sxs-lookup"><span data-stu-id="257ac-118">This database mirroring event is issued on the principal server instance to indicate that the age of the oldest unsent transaction has reached a user-specified threshold value.</span></span> <span data-ttu-id="257ac-119">通常は、システム パフォーマンスの変化が原因で発生します。</span><span class="sxs-lookup"><span data-stu-id="257ac-119">Typically, this event occurs because the performance of the system has changed.</span></span> <span data-ttu-id="257ac-120">2 つのシステムを接続する帯域幅が縮小したか、負荷が増加しています。</span><span class="sxs-lookup"><span data-stu-id="257ac-120">Either the bandwidth between the two systems has decreased, or the load has increased.</span></span>  
  
 <span data-ttu-id="257ac-121">最も古い未送信のトランザクションの経過期間は、未送信のトランザクションの経過時間 (分) によって判断されるデータ損失の可能性を評価するのに役立つパフォーマンス基準です。</span><span class="sxs-lookup"><span data-stu-id="257ac-121">The age of the oldest unsent transaction is a performance metric that can help you evaluate the potential for data loss as measured by the number of minutes of unsent transactions.</span></span> <span data-ttu-id="257ac-122">この基準は、特に高パフォーマンス モードのセッションに関連しています。</span><span class="sxs-lookup"><span data-stu-id="257ac-122">This metric is especially relevant for high-performance mode sessions.</span></span> <span data-ttu-id="257ac-123">ただし、パートナー間の接続が切断され、ミラーリングが中断している場合は、高度な安全性モードのセッションにも関係します。</span><span class="sxs-lookup"><span data-stu-id="257ac-123">However, this metric is also relevant for high-safety mode session when mirroring is paused or suspended because the partners become disconnected.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="257ac-124">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="257ac-124">User Action</span></span>  
 <span data-ttu-id="257ac-125">プリンシパル サーバー インスタンス、ミラー サーバー インスタンス、および両者のネットワーク接続の負荷が原因になっているかどうかを調査します。</span><span class="sxs-lookup"><span data-stu-id="257ac-125">Check the loads on the principal and mirror server instances and their network connection for the cause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="257ac-126">参照</span><span class="sxs-lookup"><span data-stu-id="257ac-126">See Also</span></span>  
 <span data-ttu-id="257ac-127">[データベース ミラーリング &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="257ac-127">[Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="257ac-128">ミラーリング パフォーマンス基準の警告しきい値および警告の使用 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="257ac-128">Use Warning Thresholds and Alerts on Mirroring Performance Metrics &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
  
