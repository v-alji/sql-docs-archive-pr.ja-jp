---
title: MSSQL_ENG020557 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020557 error
ms.assetid: c43c6952-5b60-4347-b881-11a0004dce24
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 45c24d453eb95abaa967ae65ceb5934b7dee969e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645555"
---
# <a name="mssql_eng020557"></a><span data-ttu-id="6cd38-102">MSSQL_ENG020557</span><span class="sxs-lookup"><span data-stu-id="6cd38-102">MSSQL_ENG020557</span></span>
    
## <a name="message-details"></a><span data-ttu-id="6cd38-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="6cd38-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6cd38-104">製品名</span><span class="sxs-lookup"><span data-stu-id="6cd38-104">Product Name</span></span>|<span data-ttu-id="6cd38-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6cd38-105">SQL Server</span></span>|  
|<span data-ttu-id="6cd38-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="6cd38-106">Event ID</span></span>|<span data-ttu-id="6cd38-107">20557</span><span class="sxs-lookup"><span data-stu-id="6cd38-107">20557</span></span>|  
|<span data-ttu-id="6cd38-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="6cd38-108">Event Source</span></span>|<span data-ttu-id="6cd38-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6cd38-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6cd38-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6cd38-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="6cd38-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="6cd38-111">Symbolic Name</span></span>||  
|<span data-ttu-id="6cd38-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="6cd38-112">Message Text</span></span>|<span data-ttu-id="6cd38-113">エージェントがシャットダウンされました。</span><span class="sxs-lookup"><span data-stu-id="6cd38-113">Agent shutdown.</span></span> <span data-ttu-id="6cd38-114">詳細については、ジョブ '%s' の SQL Server エージェントのジョブ履歴を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cd38-114">For more information, see the SQL Server Agent job history for job '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6cd38-115">説明</span><span class="sxs-lookup"><span data-stu-id="6cd38-115">Explanation</span></span>  
 <span data-ttu-id="6cd38-116">レプリケーション エージェントは、原因を適切な履歴テーブルに書き込むことなくシャットダウンされました。つまり、このエージェントは処理の途中でシャットダウンされました。</span><span class="sxs-lookup"><span data-stu-id="6cd38-116">A replication agent has shut down without writing a reason to the appropriate history table, or the agent was shut down while in the middle of a process.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6cd38-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="6cd38-117">User Action</span></span>  
  
-   <span data-ttu-id="6cd38-118">エージェントを再起動し、問題なく実行されるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="6cd38-118">Restart the agent to see whether it will now run without failures.</span></span> <span data-ttu-id="6cd38-119">詳細については、「[レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)」および「[レプリケーション エージェント実行可能ファイルの概念](concepts/replication-agent-executables-concepts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cd38-119">For more information, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) and [Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
-   <span data-ttu-id="6cd38-120">エージェント履歴およびジョブ履歴を参照し、同時期に発生したその他のエラーを確認します。</span><span class="sxs-lookup"><span data-stu-id="6cd38-120">Check the agent history and job history for other errors that occurred around the same time.</span></span> <span data-ttu-id="6cd38-121">レプリケーション モニターでエージェントの状態やエラーの詳細を表示する方法については、「[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cd38-121">For information about how to view agent status and error details in Replication Monitor, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>
-   <span data-ttu-id="6cd38-122">エージェントがアクセスするコンピューター間で基本的な接続が機能していることを確認し、 **sqlcmd** ユーティリティなどのユーティリティを使用して各コンピューターに接続します。</span><span class="sxs-lookup"><span data-stu-id="6cd38-122">Verify that basic connectivity is working between the computers that are accessed by the agent, and then connect to each computer by using a utility, such as the **sqlcmd** utility.</span></span> <span data-ttu-id="6cd38-123">接続時には、エージェントが接続に使用するものと同じアカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="6cd38-123">When you connect, use the same account under which the agent makes connections.</span></span> <span data-ttu-id="6cd38-124">各エージェント アカウントで必要な権限の詳細については、「 [Replication Agent Security Model](security/replication-agent-security-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cd38-124">For more information about the permissions that are required by each agent account, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
-   <span data-ttu-id="6cd38-125">スナップショットの作成中または適用中にエラーが発生した場合は、スナップショット ディレクトリのファイルにエラーがないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="6cd38-125">If the error occurs while you are creating or applying a snapshot, check the files in the snapshot directory for errors.</span></span>  
  
-   <span data-ttu-id="6cd38-126">エラーの発生が継続する場合は、エージェントのログ記録を増やし、ログの出力ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="6cd38-126">If the error continues to occur, increase the logging of the agent and specify an output file for the log.</span></span> <span data-ttu-id="6cd38-127">エラーのコンテキストによっては、エラーや他のエラー メッセージを発生させる手順が示される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="6cd38-127">Depending on the context of the error, this could provide the steps leading up to the error and additional error messages.</span></span> <span data-ttu-id="6cd38-128">レプリケーションのログ記録を構成する方法については、サポート技術情報の資料 [312292](https://support.microsoft.com/kb/312292)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cd38-128">For more information about how to configure logging for replication, see the Microsoft Knowledge Base article [312292](https://support.microsoft.com/kb/312292).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd38-129">参照</span><span class="sxs-lookup"><span data-stu-id="6cd38-129">See Also</span></span>  
 [<span data-ttu-id="6cd38-130">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="6cd38-130">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
