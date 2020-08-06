---
title: MSSQL_ENG018752 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG018752 error
ms.assetid: 405b2655-acb4-4e15-bcc6-b8f86bb22b37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fe62d540ea8e988cd4249112f196f75493a8f623
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740826"
---
# <a name="mssql_eng018752"></a><span data-ttu-id="d3804-102">MSSQL_ENG018752</span><span class="sxs-lookup"><span data-stu-id="d3804-102">MSSQL_ENG018752</span></span>
    
## <a name="message-details"></a><span data-ttu-id="d3804-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="d3804-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d3804-104">製品名</span><span class="sxs-lookup"><span data-stu-id="d3804-104">Product Name</span></span>|<span data-ttu-id="d3804-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d3804-105">SQL Server</span></span>|  
|<span data-ttu-id="d3804-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="d3804-106">Event ID</span></span>|<span data-ttu-id="d3804-107">18752</span><span class="sxs-lookup"><span data-stu-id="d3804-107">18752</span></span>|  
|<span data-ttu-id="d3804-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="d3804-108">Event Source</span></span>|<span data-ttu-id="d3804-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d3804-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d3804-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d3804-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="d3804-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="d3804-111">Symbolic Name</span></span>||  
|<span data-ttu-id="d3804-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="d3804-112">Message Text</span></span>|<span data-ttu-id="d3804-113">同時にデータベースに接続できるログ リーダー エージェントまたはログ関連のプロシージャ (sp_repldone、sp_replcmds、および sp_replshowcmds) は 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="d3804-113">Only one Log Reader Agent or log-related procedure (sp_repldone, sp_replcmds, and sp_replshowcmds) can connect to a database at a time.</span></span> <span data-ttu-id="d3804-114">ログ関連のプロシージャを実行した場合、そのプロシージャが実行された接続を削除するか、その接続に対して sp_replflush を実行してから、ログ リーダー エージェントを開始するか、別のログ関連のプロシージャを実行してください。</span><span class="sxs-lookup"><span data-stu-id="d3804-114">If you executed a log-related procedure, drop the connection over which the procedure was executed or execute sp_replflush over that connection before starting the Log Reader Agent or executing another log-related procedure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d3804-115">説明</span><span class="sxs-lookup"><span data-stu-id="d3804-115">Explanation</span></span>  
 <span data-ttu-id="d3804-116">複数の現在の接続が、 **sp_repldone**、 **sp_replcmds**、 **sp_replshowcmds**のいずれかを実行しようとしています。</span><span class="sxs-lookup"><span data-stu-id="d3804-116">More than one current connection is trying to execute any of the following: **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds**.</span></span> <span data-ttu-id="d3804-117">ストアド プロシージャの [sp_repldone &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-repldone-transact-sql) と [sp_replcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) は、パブリッシュされたデータベース内のレプリケートされたトランザクションに関する情報を検索および更新するために、ログ リーダー エージェントによって使用されるストアド プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="d3804-117">The stored procedures [sp_repldone &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-repldone-transact-sql) and [sp_replcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) are stored procedures used by the Log Reader Agent to locate and update information about replicated transactions in a published database.</span></span> <span data-ttu-id="d3804-118">ストアド プロシージャ [sp_replshowcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql) は、トランザクション レプリケーションに関する特定のタイプの問題点に対するトラブルシューティングを行うために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3804-118">The stored procedure [sp_replshowcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql) is used to troubleshoot certain types of issues with transactional replication.</span></span>  
  
 <span data-ttu-id="d3804-119">このエラーは、次の状況で発生します。</span><span class="sxs-lookup"><span data-stu-id="d3804-119">This error is raised in the following circumstances:</span></span>  
  
-   <span data-ttu-id="d3804-120">パブリッシュされたデータベースのログ リーダー エージェントが実行されており、2 番目のログ リーダー エージェントの実行を同じデータベースに対して試みた場合、2 番目のエージェントに対してエラーが発生し、エージェント履歴に表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3804-120">If the Log Reader Agent for a published database is running and a second Log Reader Agent attempts to run against the same database, the error is raised for the second agent and appears in the agent history.</span></span>  
  
     <span data-ttu-id="d3804-121">複数のエージェントが存在する状況では、いずれかのエージェントは孤立したプロセスが原因の可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d3804-121">In a situation where it appears there are multiple agents, it is possible that one of them is the result of an orphaned process.</span></span>  
  
-   <span data-ttu-id="d3804-122">パブリッシュされたデータベースに対してログ リーダー エージェントが起動されており、ユーザーが **sp_repldone**、 **sp_replcmds**、または **sp_replshowcmds** を同じデータベースに対して実行する場合は、ストアド プロシージャ ( **sqlcmd**など) が実行されるとアプリケーションでエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d3804-122">If the Log Reader Agent for a published database is started and a user executes **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds** against the same database, the error is raised in the application where the stored procedure was executed (such as **sqlcmd**).</span></span>  
  
-   <span data-ttu-id="d3804-123">パブリッシュされたデータベースに対してログ リーダー エージェントが実行されておらず、ユーザーが **sp_repldone**、 **sp_replcmds**、または **sp_replshowcmds** を実行してから、プロシージャを実行した接続を閉じない場合は、ログ リーダー エージェントによってデータベースへの接続が試行されるとエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d3804-123">If no Log Reader Agent is running for a published database and a user executes **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds** and then does not close the connection over which the procedure was executed, the error is raised when the Log Reader Agent attempts to connect to the database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d3804-124">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="d3804-124">User Action</span></span>  
 <span data-ttu-id="d3804-125">次の手順を実行して、この問題に対するトラブルシューティングに役立てることができます。</span><span class="sxs-lookup"><span data-stu-id="d3804-125">The following steps can help you to troubleshoot the problem.</span></span> <span data-ttu-id="d3804-126">いずれかの手順によって、ログ リーダー エージェントをエラーを発生させないで起動できるようになった場合は、残りの手順を実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d3804-126">If any step allows the Log Reader Agent to start without errors, there is no need to complete the remaining steps.</span></span>  
  
-   <span data-ttu-id="d3804-127">このエラーの発生原因となる可能性があるその他のエラーについて、ログ リーダー エージェントの履歴を確認します。</span><span class="sxs-lookup"><span data-stu-id="d3804-127">Check the history of the Log Reader agent for any other errors that could be contributing to this error.</span></span> <span data-ttu-id="d3804-128">レプリケーション モニターでのエージェントの状態やエラーの詳細の表示について詳しくは、「[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3804-128">For information about viewing agent status and error details in Replication Monitor, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="d3804-129">パブリッシュされたデータベースに接続されている特定のプロセス識別番号 (SPID) に対応する [sp_who &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) の出力を確認します。</span><span class="sxs-lookup"><span data-stu-id="d3804-129">Check the output of [sp_who &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) for specific process identification numbers (SPIDs) that are connected to the published database.</span></span> <span data-ttu-id="d3804-130">**sp_repldone**、 **sp_replcmds**、または **sp_replshowcmds**を実行していた可能性のある接続をすべて閉じます。</span><span class="sxs-lookup"><span data-stu-id="d3804-130">Close any connections that might have run **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds**.</span></span>  
  
-   <span data-ttu-id="d3804-131">ログ リーダー エージェントを再起動します。</span><span class="sxs-lookup"><span data-stu-id="d3804-131">Restart the Log Reader Agent.</span></span> <span data-ttu-id="d3804-132">詳細については、「[レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3804-132">For more information, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="d3804-133">ディストリビューターで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスを再起動します (クラスター内でオフラインまたはオンラインにします)。</span><span class="sxs-lookup"><span data-stu-id="d3804-133">Restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service (bring it offline or online in a cluster) on the Distributor.</span></span> <span data-ttu-id="d3804-134">スケジュールされたジョブがその他の **インスタンスから**sp_repldone **、** sp_replcmds **、または** sp_replshowcmds [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行した可能性がある場合は、これらのインスタンスに対しても [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを再起動します。</span><span class="sxs-lookup"><span data-stu-id="d3804-134">If there is possibility that a scheduled job could have executed **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds** from any other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent for those instances as well.</span></span> <span data-ttu-id="d3804-135">詳細については、「[SQL Server エージェント サービスの開始、停止、または一時停止](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3804-135">For more information, see [Start, Stop, or Pause the SQL Server Agent Service](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md).</span></span>  
  
-   <span data-ttu-id="d3804-136">パブリケーション データベース上のパブリッシャーで [sp_replflush &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replflush-transact-sql) を実行してから、ログ リーダー エージェントを再起動します。</span><span class="sxs-lookup"><span data-stu-id="d3804-136">Execute [sp_replflush &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replflush-transact-sql) at the Publisher on the publication database, and then restart the Log Reader Agent.</span></span>  
  
-   <span data-ttu-id="d3804-137">エラーの発生が継続する場合は、エージェントのログ記録を増やし、ログの出力ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="d3804-137">If the error continues to occur, increase the logging of the agent and specify an output file for the log.</span></span> <span data-ttu-id="d3804-138">エラーのコンテキストによっては、エラーや他のエラー メッセージにつながる手順が示される可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="d3804-138">Depending on the context of the error, this could provide the steps leading up to the error and/or additional error messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3804-139">参照</span><span class="sxs-lookup"><span data-stu-id="d3804-139">See Also</span></span>  
 <span data-ttu-id="d3804-140">[エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="d3804-140">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 [<span data-ttu-id="d3804-141">レプリケーション ログ リーダー エージェント</span><span class="sxs-lookup"><span data-stu-id="d3804-141">Replication Log Reader Agent</span></span>](agents/replication-log-reader-agent.md)  
  
  
