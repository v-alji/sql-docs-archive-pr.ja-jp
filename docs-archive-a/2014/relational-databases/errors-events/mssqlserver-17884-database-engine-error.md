---
title: MSSQLSERVER_17884 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17884 (Database Engine error)
ms.assetid: 8d05ba05-3f71-4dc3-bd81-2ea5ac9fe843
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bd5beca2a7dfd20afbf9eff196d89452ef3533d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718201"
---
# <a name="mssqlserver_17884"></a><span data-ttu-id="97b67-102">MSSQLSERVER_17884</span><span class="sxs-lookup"><span data-stu-id="97b67-102">MSSQLSERVER_17884</span></span>
    
## <a name="details"></a><span data-ttu-id="97b67-103">詳細</span><span class="sxs-lookup"><span data-stu-id="97b67-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="97b67-104">製品名</span><span class="sxs-lookup"><span data-stu-id="97b67-104">Product Name</span></span>|<span data-ttu-id="97b67-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="97b67-105">SQL Server</span></span>|  
|<span data-ttu-id="97b67-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="97b67-106">Event ID</span></span>|<span data-ttu-id="97b67-107">17884</span><span class="sxs-lookup"><span data-stu-id="97b67-107">17884</span></span>|  
|<span data-ttu-id="97b67-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="97b67-108">Event Source</span></span>|<span data-ttu-id="97b67-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="97b67-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="97b67-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="97b67-110">Component</span></span>|<span data-ttu-id="97b67-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="97b67-111">SQLEngine</span></span>|  
|<span data-ttu-id="97b67-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="97b67-112">Symbolic Name</span></span>|<span data-ttu-id="97b67-113">SRV_SCHEDULER_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="97b67-113">SRV_SCHEDULER_DEADLOCK</span></span>|  
|<span data-ttu-id="97b67-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="97b67-114">Message Text</span></span>|<span data-ttu-id="97b67-115">ノード %d のプロセスに割り当てられた新しいクエリが、この %d 秒間ワーカー スレッドで選択されませんでした。</span><span class="sxs-lookup"><span data-stu-id="97b67-115">New queries assigned to process on Node %d have not been picked  up by a worker thread in the last %d seconds.</span></span> <span data-ttu-id="97b67-116">クエリのブロックまたは長時間実行をこの条件に含めることができますが、クライアントの応答時間が低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="97b67-116">Blocking or long-running queries can contribute to this condition, and may degrade client response time.</span></span> <span data-ttu-id="97b67-117">"max worker threads" 構成オプションを使用して使用可能なスレッド数を増やすか、現在実行中のクエリを最適化してください。</span><span class="sxs-lookup"><span data-stu-id="97b67-117">Use the "max worker threads" configuration option to increase number  of allowable threads, or optimize current running queries.</span></span>  <span data-ttu-id="97b67-118">SQL プロセス使用率: %d%%。</span><span class="sxs-lookup"><span data-stu-id="97b67-118">SQL Process Utilization: %d%%.</span></span> <span data-ttu-id="97b67-119">システムのアイドル状態: %d%%。</span><span class="sxs-lookup"><span data-stu-id="97b67-119">System Idle: %d%%.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="97b67-120">説明</span><span class="sxs-lookup"><span data-stu-id="97b67-120">Explanation</span></span>  
 <span data-ttu-id="97b67-121">各スケジューラで処理の進行が示されません。デッドロックが原因である可能性があり、その場合、スレッドは進行せず、新しい作業は選択されず処理されません。</span><span class="sxs-lookup"><span data-stu-id="97b67-121">There is no sign of progress in each of the schedulers and could be caused by deadlocks where none of the threads can advance and/or no new work can be picked up and processed.</span></span> <span data-ttu-id="97b67-122">プロセス使用率が低い場合は、コンピューター上の他のプロセスによってサーバー プロセスの CPU 不足が発生している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="97b67-122">If process utilization is low then other processes on the machine may be causing the server process CPU starvation.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="97b67-123">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="97b67-123">User Action</span></span>  
 <span data-ttu-id="97b67-124">ブロックが発生して処理が進行していない理由を特定し、それに応じて状況に対処します。</span><span class="sxs-lookup"><span data-stu-id="97b67-124">Determine why there is blocking and no progress being made and resolve situation accordingly.</span></span> <span data-ttu-id="97b67-125">プロセス使用率が低い場合は、他のプロセスによって発生しているシステムへの負荷を確認します。</span><span class="sxs-lookup"><span data-stu-id="97b67-125">If process utilization is low check the load on the system caused by other processes.</span></span>  
  
  
