---
title: MSSQLSERVER_32042 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 32042 (Database Engine error)
ms.assetid: 53a51c7a-dcd4-4c15-b4d2-6aaa9dce76da
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bd959d84da2c54310dea5156b1a45b73490211a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640037"
---
# <a name="mssqlserver_32042"></a><span data-ttu-id="fa11a-102">MSSQLSERVER_32042</span><span class="sxs-lookup"><span data-stu-id="fa11a-102">MSSQLSERVER_32042</span></span>
    
## <a name="details"></a><span data-ttu-id="fa11a-103">詳細</span><span class="sxs-lookup"><span data-stu-id="fa11a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fa11a-104">製品名</span><span class="sxs-lookup"><span data-stu-id="fa11a-104">Product Name</span></span>|<span data-ttu-id="fa11a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="fa11a-105">SQL Server</span></span>|  
|<span data-ttu-id="fa11a-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="fa11a-106">Event ID</span></span>|<span data-ttu-id="fa11a-107">32042</span><span class="sxs-lookup"><span data-stu-id="fa11a-107">32042</span></span>|  
|<span data-ttu-id="fa11a-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="fa11a-108">Event Source</span></span>|<span data-ttu-id="fa11a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="fa11a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="fa11a-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="fa11a-110">Component</span></span>|<span data-ttu-id="fa11a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="fa11a-111">SQLEngine</span></span>|  
|<span data-ttu-id="fa11a-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="fa11a-112">Symbolic Name</span></span>|<span data-ttu-id="fa11a-113">SQLErrorNum32042</span><span class="sxs-lookup"><span data-stu-id="fa11a-113">SQLErrorNum32042</span></span>|  
|<span data-ttu-id="fa11a-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="fa11a-114">Message Text</span></span>|<span data-ttu-id="fa11a-115">'未送信のログ' の警告が発生しました。</span><span class="sxs-lookup"><span data-stu-id="fa11a-115">The alert for 'unsent log' has been raised.</span></span> <span data-ttu-id="fa11a-116">現在の値 '%d' はしきい値 '%d' を上回っています。</span><span class="sxs-lookup"><span data-stu-id="fa11a-116">The current value of '%d' surpasses the threshold '%d'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fa11a-117">説明</span><span class="sxs-lookup"><span data-stu-id="fa11a-117">Explanation</span></span>  
 <span data-ttu-id="fa11a-118">プリンシパル サーバー インスタンスで発生したこのデータベース ミラーリング イベントは、未送信ログの量がユーザー指定のしきい値に達したことを示しています。</span><span class="sxs-lookup"><span data-stu-id="fa11a-118">This database mirroring event is issued on the principal server instance to indicate that the amount of unsent log has reached a user-specified threshold value.</span></span> <span data-ttu-id="fa11a-119">通常は、システム パフォーマンスの変化が原因で発生します。</span><span class="sxs-lookup"><span data-stu-id="fa11a-119">Typically, this event occurs because the performance of the system has changed.</span></span> <span data-ttu-id="fa11a-120">2 つのシステムを接続する帯域幅が縮小したか、負荷が増加しています。</span><span class="sxs-lookup"><span data-stu-id="fa11a-120">Either the bandwidth between the two systems has decreased, or the load has increased.</span></span>  
  
 <span data-ttu-id="fa11a-121">未送信ログの量は、データ損失の可能性を評価する際に役立つパフォーマンス基準であり、送信されていないログが KB 数で示されます。</span><span class="sxs-lookup"><span data-stu-id="fa11a-121">The amount of unsent log is a performance metric that can help you evaluate the potential for data loss in terms of the number of kilobytes (KB) of unsent log.</span></span> <span data-ttu-id="fa11a-122">この基準は、特に高パフォーマンス モードのセッションに関連があります。</span><span class="sxs-lookup"><span data-stu-id="fa11a-122">This metric is particularly relevant for high-performance mode sessions.</span></span> <span data-ttu-id="fa11a-123">ただし、パートナー間の接続が切断され、ミラーリングが中断している場合は、高度な安全性モードのセッションにも関係します。</span><span class="sxs-lookup"><span data-stu-id="fa11a-123">However, this metric is also a relevant for high-safety mode session when mirroring is paused or suspended because the partners become disconnected.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fa11a-124">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="fa11a-124">User Action</span></span>  
 <span data-ttu-id="fa11a-125">プリンシパル サーバー インスタンス、ミラー サーバー インスタンス、および両者のネットワーク接続の負荷が原因になっているかどうかを調査します。</span><span class="sxs-lookup"><span data-stu-id="fa11a-125">Check the loads on the principal and mirror server instances and their network connection for the cause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa11a-126">参照</span><span class="sxs-lookup"><span data-stu-id="fa11a-126">See Also</span></span>  
 <span data-ttu-id="fa11a-127">[データベース ミラーリング &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fa11a-127">[Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="fa11a-128">ミラーリング パフォーマンス基準の警告しきい値および警告の使用 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fa11a-128">Use Warning Thresholds and Alerts on Mirroring Performance Metrics &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
  
