---
title: MSSQL_ENG014151 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014151 error
ms.assetid: 54b45e70-46b3-4c7a-a5bf-06f6dd028ceb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d2796451f6f681cfb0ce529ed44a946c34135649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631814"
---
# <a name="mssql_eng014151"></a><span data-ttu-id="6be61-102">MSSQL_ENG014151</span><span class="sxs-lookup"><span data-stu-id="6be61-102">MSSQL_ENG014151</span></span>
    
## <a name="message-details"></a><span data-ttu-id="6be61-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="6be61-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6be61-104">製品名</span><span class="sxs-lookup"><span data-stu-id="6be61-104">Product Name</span></span>|<span data-ttu-id="6be61-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6be61-105">SQL Server</span></span>|  
|<span data-ttu-id="6be61-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="6be61-106">Event ID</span></span>|<span data-ttu-id="6be61-107">14151</span><span class="sxs-lookup"><span data-stu-id="6be61-107">14151</span></span>|  
|<span data-ttu-id="6be61-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="6be61-108">Event Source</span></span>|<span data-ttu-id="6be61-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6be61-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6be61-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6be61-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="6be61-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="6be61-111">Symbolic Name</span></span>||  
|<span data-ttu-id="6be61-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="6be61-112">Message Text</span></span>|<span data-ttu-id="6be61-113">レプリケーション-%s: エージェント %s は失敗しました。</span><span class="sxs-lookup"><span data-stu-id="6be61-113">Replication-%s: agent %s failed.</span></span> <span data-ttu-id="6be61-114">%s</span><span class="sxs-lookup"><span data-stu-id="6be61-114">%s</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6be61-115">説明</span><span class="sxs-lookup"><span data-stu-id="6be61-115">Explanation</span></span>  
 <span data-ttu-id="6be61-116">このエラーは、すべてのレプリケーション エージェントのエラーに対して発生します。</span><span class="sxs-lookup"><span data-stu-id="6be61-116">This error is raised for any replication agent failure.</span></span> <span data-ttu-id="6be61-117">メッセージの最後のテキストは、エラーのコンテキストに依存します。</span><span class="sxs-lookup"><span data-stu-id="6be61-117">The text at the end of the message depends on the context of the failure.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6be61-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="6be61-118">User Action</span></span>  
 <span data-ttu-id="6be61-119">このエラーはさまざまな状況で発生します。必要に応じて、以下の方法を使用してください。</span><span class="sxs-lookup"><span data-stu-id="6be61-119">This error can occur in a number of situations; use the following approaches as necessary:</span></span>  
  
-   <span data-ttu-id="6be61-120">失敗したエージェントを再起動し、問題なく実行されるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="6be61-120">Restart the failed agent to see if it will now run without failures.</span></span> <span data-ttu-id="6be61-121">詳細については、「[レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)」および「[レプリケーション エージェント実行可能ファイルの概念](concepts/replication-agent-executables-concepts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6be61-121">For more information, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) and [Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
-   <span data-ttu-id="6be61-122">エージェント履歴およびジョブ履歴を参照し、同時期に発生したその他のエラーを確認します。</span><span class="sxs-lookup"><span data-stu-id="6be61-122">Check the agent history and job history for other errors that occurred around the same time.</span></span> <span data-ttu-id="6be61-123">レプリケーション モニターでのエージェントの状態やエラーの詳細の表示について詳しくは、「[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6be61-123">For information about viewing agent status and error details in Replication Monitor, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="6be61-124">エージェントがアクセスするコンピューター間で基本的な接続が機能していることを確認し、 [sqlcmd Utility](../../tools/sqlcmd-utility.md)などのユーティリティにより各コンピューターを接続します。</span><span class="sxs-lookup"><span data-stu-id="6be61-124">Verify that basic connectivity is working between the computers accessed by the agent, and then connect to each computer with a utility like the [sqlcmd Utility](../../tools/sqlcmd-utility.md).</span></span> <span data-ttu-id="6be61-125">接続の際には、エージェントが接続に使用するものと同じアカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="6be61-125">When connecting, use the same account under which the agent makes connections.</span></span> <span data-ttu-id="6be61-126">各エージェント アカウントで必要な権限の詳細については、「 [Replication Agent Security Model](security/replication-agent-security-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6be61-126">For more information about the permissions required by each agent account, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
-   <span data-ttu-id="6be61-127">スナップショットの作成中または適用中にエラーが発生した場合は、スナップショット ディレクトリのファイルにエラーがないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="6be61-127">If the error occurs while creating or applying a snapshot, check the files in the snapshot directory for errors.</span></span>  
  
-   <span data-ttu-id="6be61-128">エラーの発生が継続する場合は、エージェントのログ記録を増やし、ログの出力ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="6be61-128">If the error continues to occur, increase the logging of the agent and specify an output file for the log.</span></span> <span data-ttu-id="6be61-129">エラーのコンテキストによっては、エラーや他のエラー メッセージにつながる手順が示される可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="6be61-129">Depending on the context of the error, this could provide the steps leading up to the error and/or additional error messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6be61-130">参照</span><span class="sxs-lookup"><span data-stu-id="6be61-130">See Also</span></span>  
 <span data-ttu-id="6be61-131">[レプリケーション エージェントの管理](agents/replication-agent-administration.md) </span><span class="sxs-lookup"><span data-stu-id="6be61-131">[Replication Agent Administration](agents/replication-agent-administration.md) </span></span>  
 <span data-ttu-id="6be61-132">[エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="6be61-132">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="6be61-133">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span><span class="sxs-lookup"><span data-stu-id="6be61-133">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span></span>  
 <span data-ttu-id="6be61-134">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="6be61-134">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span></span>  
 <span data-ttu-id="6be61-135">[Replication Merge Agent](agents/replication-merge-agent.md) </span><span class="sxs-lookup"><span data-stu-id="6be61-135">[Replication Merge Agent](agents/replication-merge-agent.md) </span></span>  
 <span data-ttu-id="6be61-136">[レプリケーション キュー リーダー エージェント](agents/replication-queue-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="6be61-136">[Replication Queue Reader Agent](agents/replication-queue-reader-agent.md) </span></span>  
 [<span data-ttu-id="6be61-137">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="6be61-137">Replication Snapshot Agent</span></span>](agents/replication-snapshot-agent.md)  
  
  
