---
title: MSSQLSERVER_844 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 844 (Database Engine error)
ms.assetid: 2060c886-1226-4066-bc0c-de90a1cfb82b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c4870d6e43ec12b49033ea3b5f88fa0d0cdd597a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639535"
---
# <a name="mssqlserver_844"></a><span data-ttu-id="77863-102">MSSQLSERVER_844</span><span class="sxs-lookup"><span data-stu-id="77863-102">MSSQLSERVER_844</span></span>
    
## <a name="details"></a><span data-ttu-id="77863-103">詳細</span><span class="sxs-lookup"><span data-stu-id="77863-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="77863-104">製品名</span><span class="sxs-lookup"><span data-stu-id="77863-104">Product Name</span></span>|<span data-ttu-id="77863-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="77863-105">SQL Server</span></span>|  
|<span data-ttu-id="77863-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="77863-106">Event ID</span></span>|<span data-ttu-id="77863-107">844</span><span class="sxs-lookup"><span data-stu-id="77863-107">844</span></span>|  
|<span data-ttu-id="77863-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="77863-108">Event Source</span></span>|<span data-ttu-id="77863-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="77863-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="77863-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="77863-110">Component</span></span>|<span data-ttu-id="77863-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="77863-111">SQLEngine</span></span>|  
|<span data-ttu-id="77863-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="77863-112">Symbolic Name</span></span>|<span data-ttu-id="77863-113">BUFLATCH_TIMEOUT_CONTINUE</span><span class="sxs-lookup"><span data-stu-id="77863-113">BUFLATCH_TIMEOUT_CONTINUE</span></span>|  
|<span data-ttu-id="77863-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="77863-114">Message Text</span></span>|<span data-ttu-id="77863-115">バッファー ラッチを待機中にタイムアウトが発生しました。型 %d、BP %p、ページ %d:%d、状態 %#x、データベース ID: %d、アロケーション ユニット ID: %I64d%ls、タスク 0x%p : %d、待機時間 %d、フラグ 0x%I64x、所有しているタスク 0x%p。</span><span class="sxs-lookup"><span data-stu-id="77863-115">Time-out occurred while waiting for buffer latch -- type %d, bp %p, page %d:%d, stat %#x, database id: %d, allocation unit id: %I64d%ls, task 0x%p : %d, waittime %d, flags 0x%I64x, owning task 0x%p.</span></span>  <span data-ttu-id="77863-116">待機を続行します。</span><span class="sxs-lookup"><span data-stu-id="77863-116">Continuing to wait.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="77863-117">説明</span><span class="sxs-lookup"><span data-stu-id="77863-117">Explanation</span></span>  
 <span data-ttu-id="77863-118">プロセスが、ラッチの獲得を待機しています。</span><span class="sxs-lookup"><span data-stu-id="77863-118">A process is waiting to acquire a latch.</span></span> <span data-ttu-id="77863-119">この問題は、I/O 操作の完了までに時間がかかりすぎている場合に生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="77863-119">This problem can be caused by an I/O operation taking too long to complete.</span></span> <span data-ttu-id="77863-120">このタイプのエラーは、他のタスクによってシステム プロセスがブロックされた結果に生じることが普通です。</span><span class="sxs-lookup"><span data-stu-id="77863-120">Typically this type of error is the result of other tasks blocking system processes.</span></span> <span data-ttu-id="77863-121">場合によっては、ハードウェア障害によってこのエラーが生じることもあります。</span><span class="sxs-lookup"><span data-stu-id="77863-121">In some instances, this error may be the result of hardware failure.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="77863-122">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="77863-122">User Action</span></span>  
 <span data-ttu-id="77863-123">このエラーを回避するには、次の操作を試してみます。</span><span class="sxs-lookup"><span data-stu-id="77863-123">Try the following to prevent this error from occurring:</span></span>  
  
-   <span data-ttu-id="77863-124">ワークロードを減らします。</span><span class="sxs-lookup"><span data-stu-id="77863-124">Reduce workload.</span></span>  
  
-   <span data-ttu-id="77863-125">エラー ログまたはイベント ログで、関連する I/O エラーがないか調べます。</span><span class="sxs-lookup"><span data-stu-id="77863-125">Check for associated I/O failures in error log or event log.</span></span> <span data-ttu-id="77863-126">通常、I/O エラーはディスクに障害があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="77863-126">I/O failures typically point to a disk malfunction.</span></span>  
  
-   <span data-ttu-id="77863-127">応答していないタスクや他の重大なエラーがないか、エラー ログで調べます。</span><span class="sxs-lookup"><span data-stu-id="77863-127">Check the error log for non-yielding tasks and other critical errors.</span></span>  
  
-   <span data-ttu-id="77863-128">アサートなどの重大なエラーが頻繁に発生する場合は、その問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="77863-128">If critical errors such as asserts frequently occur, resolve these problems.</span></span>  
  
 <span data-ttu-id="77863-129">エラーが継続して発生する場合は、マイクロソフト カスタマー サービスおよびサポートに問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="77863-129">If the error persists, contact Microsoft Customer Service and Support.</span></span>  
  
  
