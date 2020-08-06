---
title: MSSQLSERVER_32043 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 32043 (Database Engine error)
ms.assetid: a0c48ae3-4c8c-419c-afb5-579fcefac01d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2febc7173c8144451c7a9b0576f2293d5594c6df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631981"
---
# <a name="mssqlserver_32043"></a><span data-ttu-id="6d8df-102">MSSQLSERVER_32043</span><span class="sxs-lookup"><span data-stu-id="6d8df-102">MSSQLSERVER_32043</span></span>
    
## <a name="details"></a><span data-ttu-id="6d8df-103">詳細</span><span class="sxs-lookup"><span data-stu-id="6d8df-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6d8df-104">製品名</span><span class="sxs-lookup"><span data-stu-id="6d8df-104">Product Name</span></span>|<span data-ttu-id="6d8df-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6d8df-105">SQL Server</span></span>|  
|<span data-ttu-id="6d8df-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="6d8df-106">Event ID</span></span>|<span data-ttu-id="6d8df-107">32043</span><span class="sxs-lookup"><span data-stu-id="6d8df-107">32043</span></span>|  
|<span data-ttu-id="6d8df-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="6d8df-108">Event Source</span></span>|<span data-ttu-id="6d8df-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6d8df-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6d8df-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6d8df-110">Component</span></span>|<span data-ttu-id="6d8df-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6d8df-111">SQLEngine</span></span>|  
|<span data-ttu-id="6d8df-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="6d8df-112">Symbolic Name</span></span>|<span data-ttu-id="6d8df-113">SQLErrorNum32043</span><span class="sxs-lookup"><span data-stu-id="6d8df-113">SQLErrorNum32043</span></span>|  
|<span data-ttu-id="6d8df-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="6d8df-114">Message Text</span></span>|<span data-ttu-id="6d8df-115">'復元されていないログ' の警告が発生しました。</span><span class="sxs-lookup"><span data-stu-id="6d8df-115">The alert for 'unrestored log' has been raised.</span></span> <span data-ttu-id="6d8df-116">現在の値 '%d' はしきい値 '%d' を上回っています。</span><span class="sxs-lookup"><span data-stu-id="6d8df-116">The current value of '%d' surpasses the threshold '%d'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6d8df-117">説明</span><span class="sxs-lookup"><span data-stu-id="6d8df-117">Explanation</span></span>  
 <span data-ttu-id="6d8df-118">ミラー サーバー インスタンスで発生したこのデータベース ミラーリング イベントは、復元されていないログの量がユーザー指定のしきい値に達したことを示しています。</span><span class="sxs-lookup"><span data-stu-id="6d8df-118">This database mirroring event is issued on the mirror server instance to indicate that the amount of unrestored log reached a user-specified threshold value.</span></span> <span data-ttu-id="6d8df-119">通常は、システム パフォーマンスの変化が原因で発生します。</span><span class="sxs-lookup"><span data-stu-id="6d8df-119">Typically, this event occurs because the performance of the system has changed.</span></span> <span data-ttu-id="6d8df-120">2 つのシステムを接続する帯域幅が縮小したか、負荷が増加しています。</span><span class="sxs-lookup"><span data-stu-id="6d8df-120">Either the bandwidth between the two systems has decreased, or the load has increased.</span></span>  
  
 <span data-ttu-id="6d8df-121">復元されていないログとは、ミラー サーバー インスタンスで受信してディスクに書き込んだが、ミラー データベースに復元されるのを待機しているログです。</span><span class="sxs-lookup"><span data-stu-id="6d8df-121">An unrestored log is a log that has been received by the mirror server instance and written to disk but is waiting to be restored to the mirror database.</span></span> <span data-ttu-id="6d8df-122">復元されていないログの量 (KB) は、現在のフェールオーバー時間を求めるうえで役立つ、パフォーマンス基準です。</span><span class="sxs-lookup"><span data-stu-id="6d8df-122">The amount of unrestored log in kilobytes (KB) is a performance metric that can help you evaluate the current failover time.</span></span> <span data-ttu-id="6d8df-123">フェールオーバー時間の主要因は、復元されていないログを適用するために必要な時間です。さらに、データベースを復旧してオンラインに復帰するための時間が必要です。</span><span class="sxs-lookup"><span data-stu-id="6d8df-123">The time that is required to apply the unrestored log is the main factor in failover time, along with a short additional time that is required to recover the database and bring it online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6d8df-124">自動フェールオーバーの場合、システムが障害を通知するまでの時間は、フェールオーバー時間に関係ありません。</span><span class="sxs-lookup"><span data-stu-id="6d8df-124">For an automatic failover, the time for the system to notice the failure is independent of the failover time.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6d8df-125">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="6d8df-125">User Action</span></span>  
 <span data-ttu-id="6d8df-126">プリンシパル サーバー インスタンス、ミラー サーバー インスタンス、および両者のネットワーク接続の負荷が原因になっているかどうかを調査します。</span><span class="sxs-lookup"><span data-stu-id="6d8df-126">Check the loads on the principal and mirror server instances and their network connection for the cause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d8df-127">参照</span><span class="sxs-lookup"><span data-stu-id="6d8df-127">See Also</span></span>  
 <span data-ttu-id="6d8df-128">[データベース ミラーリング &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6d8df-128">[Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="6d8df-129">ミラーリング パフォーマンス基準の警告しきい値および警告の使用 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6d8df-129">Use Warning Thresholds and Alerts on Mirroring Performance Metrics &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
  
