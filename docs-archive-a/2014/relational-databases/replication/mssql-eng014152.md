---
title: MSSQL_ENG014152 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014152 error
ms.assetid: 4215e2b1-cd30-441f-9671-9afc742adf6e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 615b9cf2996653d86c44d6e43a83e01e8287b110
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639462"
---
# <a name="mssql_eng014152"></a><span data-ttu-id="70aa9-102">MSSQL_ENG014152</span><span class="sxs-lookup"><span data-stu-id="70aa9-102">MSSQL_ENG014152</span></span>
    
## <a name="message-details"></a><span data-ttu-id="70aa9-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="70aa9-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="70aa9-104">製品名</span><span class="sxs-lookup"><span data-stu-id="70aa9-104">Product Name</span></span>|<span data-ttu-id="70aa9-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="70aa9-105">SQL Server</span></span>|  
|<span data-ttu-id="70aa9-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="70aa9-106">Event ID</span></span>|<span data-ttu-id="70aa9-107">14152</span><span class="sxs-lookup"><span data-stu-id="70aa9-107">14152</span></span>|  
|<span data-ttu-id="70aa9-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="70aa9-108">Event Source</span></span>|<span data-ttu-id="70aa9-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="70aa9-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="70aa9-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="70aa9-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="70aa9-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="70aa9-111">Symbolic Name</span></span>||  
|<span data-ttu-id="70aa9-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="70aa9-112">Message Text</span></span>|<span data-ttu-id="70aa9-113">レプリケーション-%s: エージェント %s には再試行のスケジュールが設定されました。</span><span class="sxs-lookup"><span data-stu-id="70aa9-113">Replication-%s: agent %s scheduled for retry.</span></span> <span data-ttu-id="70aa9-114">%s</span><span class="sxs-lookup"><span data-stu-id="70aa9-114">%s</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="70aa9-115">説明</span><span class="sxs-lookup"><span data-stu-id="70aa9-115">Explanation</span></span>  
 <span data-ttu-id="70aa9-116">指定されたレプリケーション エージェントは、要求された操作を再試行するようにスケジュール設定されました。</span><span class="sxs-lookup"><span data-stu-id="70aa9-116">The specified replication agent has been scheduled to retry the requested operation.</span></span> <span data-ttu-id="70aa9-117">ジョブ ステップに設定された再試行の最大回数に達するまで、このプロセスが繰り返し再試行されます。</span><span class="sxs-lookup"><span data-stu-id="70aa9-117">The process continues to retry until it reaches the configured maximum number of retry attempts for the job step.</span></span>  
  
 <span data-ttu-id="70aa9-118">通常、再試行は次のいずれかの理由により発生します。</span><span class="sxs-lookup"><span data-stu-id="70aa9-118">A retry typically occurs because of one of the following reasons:</span></span>  
  
-   <span data-ttu-id="70aa9-119">**QueryTimeout** 値を超過する。</span><span class="sxs-lookup"><span data-stu-id="70aa9-119">The **QueryTimeout** value is exceeded.</span></span>  
  
-   <span data-ttu-id="70aa9-120">**LoginTimeout** 値を超過する。</span><span class="sxs-lookup"><span data-stu-id="70aa9-120">The **LoginTimeout** value is exceeded.</span></span>  
  
-   <span data-ttu-id="70aa9-121">レプリケーション プロセスがデッドロックの対象として選択される。</span><span class="sxs-lookup"><span data-stu-id="70aa9-121">The replication process was chosen as a deadlock victim.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="70aa9-122">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="70aa9-122">User Action</span></span>  
 <span data-ttu-id="70aa9-123">この再試行のメッセージの発生頻度が低い場合、ユーザー操作は不要です。</span><span class="sxs-lookup"><span data-stu-id="70aa9-123">If the retry message is infrequent, no user action is required.</span></span>  
  
 <span data-ttu-id="70aa9-124">[sp_help_jobstep](/sql/relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql) を使用して、指定されたレプリケーション エージェントの **[エージェントを実行します。]** ステップが再試行される最大回数の現在の設定を表示します。</span><span class="sxs-lookup"><span data-stu-id="70aa9-124">Use [sp_help_jobstep](/sql/relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql) to view the current setting for the maximum number of times the **Run agent** step for the specified replication agent will retry.</span></span> <span data-ttu-id="70aa9-125">**@retry_attempts** [Sp_update_jobstep](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql)ストアドプロシージャのパラメーターを使用して、ジョブステップが再試行される回数を調整できます。</span><span class="sxs-lookup"><span data-stu-id="70aa9-125">You can use the **@retry_attempts** parameter of the [sp_update_jobstep](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) stored procedure to adjust the number of times a job step retries.</span></span>  
  
 <span data-ttu-id="70aa9-126">再試行のメッセージが頻繁に表示される場合は、再試行が発生するメッセージに基づく問題のトラブルシューティングを行います。</span><span class="sxs-lookup"><span data-stu-id="70aa9-126">If the retry message recurs frequently, troubleshoot the issue based on the message that is causing the retry.</span></span> <span data-ttu-id="70aa9-127">エージェントの履歴で、再試行をスケジュール設定する必要があった理由を示すメッセージを確認します。</span><span class="sxs-lookup"><span data-stu-id="70aa9-127">Check the agent's history for messages that indicate why the retry had to be scheduled.</span></span> <span data-ttu-id="70aa9-128">場合によっては、レプリケーション エージェントに対してより詳細なログ記録を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="70aa9-128">In some cases you may have to enable more detailed logging for your replication agent.</span></span> <span data-ttu-id="70aa9-129">レプリケーションのログ記録を構成する方法については、サポート技術情報の資料 [312292](https://support.microsoft.com/kb/312292)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70aa9-129">For more information about how to configure logging for replication, see the Microsoft Knowledge Base article [312292](https://support.microsoft.com/kb/312292).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70aa9-130">参照</span><span class="sxs-lookup"><span data-stu-id="70aa9-130">See Also</span></span>  
 [<span data-ttu-id="70aa9-131">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="70aa9-131">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
