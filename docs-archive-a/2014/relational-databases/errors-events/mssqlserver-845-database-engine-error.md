---
title: MSSQLSERVER_845 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 845 (Database Engine error)
ms.assetid: 8fff6ad4-234c-44be-b123-e25d5e1cd63e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 24bfb8b3758d0656dad96e4af4ed3b94aa51e07f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639531"
---
# <a name="mssqlserver_845"></a><span data-ttu-id="6e96b-102">MSSQLSERVER_845</span><span class="sxs-lookup"><span data-stu-id="6e96b-102">MSSQLSERVER_845</span></span>
    
## <a name="details"></a><span data-ttu-id="6e96b-103">詳細</span><span class="sxs-lookup"><span data-stu-id="6e96b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6e96b-104">製品名</span><span class="sxs-lookup"><span data-stu-id="6e96b-104">Product Name</span></span>|<span data-ttu-id="6e96b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6e96b-105">SQL Server</span></span>|  
|<span data-ttu-id="6e96b-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="6e96b-106">Event ID</span></span>|<span data-ttu-id="6e96b-107">845</span><span class="sxs-lookup"><span data-stu-id="6e96b-107">845</span></span>|  
|<span data-ttu-id="6e96b-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="6e96b-108">Event Source</span></span>|<span data-ttu-id="6e96b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6e96b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6e96b-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6e96b-110">Component</span></span>|<span data-ttu-id="6e96b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6e96b-111">SQLEngine</span></span>|  
|<span data-ttu-id="6e96b-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="6e96b-112">Symbolic Name</span></span>|<span data-ttu-id="6e96b-113">BUFLATCH_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6e96b-113">BUFLATCH_TIMEOUT</span></span>|  
|<span data-ttu-id="6e96b-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="6e96b-114">Message Text</span></span>|<span data-ttu-id="6e96b-115">バッファー ラッチを待機中にタイムアウトが発生しました。ページ %S_PGID の型 %d、データベース ID %d。</span><span class="sxs-lookup"><span data-stu-id="6e96b-115">Time-out occurred while waiting for buffer latch type %d for page %S_PGID, database ID %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6e96b-116">説明</span><span class="sxs-lookup"><span data-stu-id="6e96b-116">Explanation</span></span>  
 <span data-ttu-id="6e96b-117">ラッチを取得するためにプロセスが待機中でしたが、制限時間に達したため、取得できませんでした。</span><span class="sxs-lookup"><span data-stu-id="6e96b-117">A process was waiting to acquire a latch, but the process waited until the time limit expired and failed to acquire one.</span></span> <span data-ttu-id="6e96b-118">このエラーは、I/O 操作の完了までに時間がかかりすぎる場合に発生する可能性があります。通常は、他のタスクによってシステムのプロセスが中断された結果のエラーです。</span><span class="sxs-lookup"><span data-stu-id="6e96b-118">This can occur if an I/O operation takes too long to complete, usually as a result of other tasks blocking system processes.</span></span> <span data-ttu-id="6e96b-119">場合によっては、ハードウェア障害によってこのエラーが生じることもあります。</span><span class="sxs-lookup"><span data-stu-id="6e96b-119">In some instances, this error may be the result of hardware failure.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6e96b-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="6e96b-120">User Action</span></span>  
 <span data-ttu-id="6e96b-121">次のタスクを実行すると、このエラーを回避できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6e96b-121">Performing the following tasks may prevent this error:</span></span>  
  
-   <span data-ttu-id="6e96b-122">ワークロードを軽減します。</span><span class="sxs-lookup"><span data-stu-id="6e96b-122">Reduce the workload.</span></span>  
  
-   <span data-ttu-id="6e96b-123">エラー ログまたはイベント ログで、関連する I/O エラーがあるかどうか確認します。</span><span class="sxs-lookup"><span data-stu-id="6e96b-123">Verify whether there are associated I/O failures in the error log or event log.</span></span> <span data-ttu-id="6e96b-124">通常、I/O エラーはディスクの障害によって発生します。</span><span class="sxs-lookup"><span data-stu-id="6e96b-124">I/O failures are typically caused by disk malfunction.</span></span>  
  
-   <span data-ttu-id="6e96b-125">エラー ログで、応答していないタスクや他の重大なエラーがないか調べます。</span><span class="sxs-lookup"><span data-stu-id="6e96b-125">Check error log for non-yielding tasks and other critical errors.</span></span>  
  
-   <span data-ttu-id="6e96b-126">アサートなどの重大なエラーが頻繁に発生する場合は、その問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="6e96b-126">If critical errors such as asserts frequently occur, resolve these problems.</span></span>  
  
 <span data-ttu-id="6e96b-127">エラーが継続して発生する場合は、マイクロソフト カスタマー サービスおよびサポートに問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="6e96b-127">If the error persists, contact Microsoft Customer Service and Support.</span></span>  
  
  
