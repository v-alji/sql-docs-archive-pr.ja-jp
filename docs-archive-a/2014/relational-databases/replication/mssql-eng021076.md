---
title: MSSQL_ENG021076 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021076 error
ms.assetid: 612e5c59-ba3e-49c3-a3df-56bac3d850a2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4161428767ce78726436c0cf794f5250140d35b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714185"
---
# <a name="mssql_eng021076"></a><span data-ttu-id="9356a-102">MSSQL_ENG021076</span><span class="sxs-lookup"><span data-stu-id="9356a-102">MSSQL_ENG021076</span></span>
    
## <a name="message-details"></a><span data-ttu-id="9356a-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="9356a-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9356a-104">製品名</span><span class="sxs-lookup"><span data-stu-id="9356a-104">Product Name</span></span>|<span data-ttu-id="9356a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9356a-105">SQL Server</span></span>|  
|<span data-ttu-id="9356a-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="9356a-106">Event ID</span></span>|<span data-ttu-id="9356a-107">21076</span><span class="sxs-lookup"><span data-stu-id="9356a-107">21076</span></span>|  
|<span data-ttu-id="9356a-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="9356a-108">Event Source</span></span>|<span data-ttu-id="9356a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9356a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9356a-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="9356a-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="9356a-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="9356a-111">Symbolic Name</span></span>||  
|<span data-ttu-id="9356a-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="9356a-112">Message Text</span></span>|<span data-ttu-id="9356a-113">アーティクル '%s' の初期スナップショットはまだ使用できません。</span><span class="sxs-lookup"><span data-stu-id="9356a-113">The initial snapshot for article '%s' is not yet available.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9356a-114">説明</span><span class="sxs-lookup"><span data-stu-id="9356a-114">Explanation</span></span>  
 <span data-ttu-id="9356a-115">エラー MSSQL_ENG021076 は、スナップショット エージェントがスナップショットの生成を終える前にディストリビューション エージェントが開始すると発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9356a-115">Error MSSQL_ENG021076 can be raised if the Distribution Agent is started before the Snapshot Agent has finished generating the snapshot.</span></span> <span data-ttu-id="9356a-116">このエラーは、パブリケーションに 1 つのアーティクルが含まれる場合にのみ発生します。</span><span class="sxs-lookup"><span data-stu-id="9356a-116">This error is raised only if the publication contains a single article.</span></span> <span data-ttu-id="9356a-117">パブリケーションに複数のアーティクルがある場合は、代わりに MSSQL_ENG021075 が発生します。</span><span class="sxs-lookup"><span data-stu-id="9356a-117">If the publication contains more than one article, MSSQL_ENG021075 is raised instead.</span></span> <span data-ttu-id="9356a-118">詳細については、「 [MSSQL_ENG021075](mssql-eng021075.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9356a-118">For more information, see [MSSQL_ENG021075](mssql-eng021075.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9356a-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="9356a-119">User Action</span></span>  
 <span data-ttu-id="9356a-120">サブスクリプションが作成されてから、または最後にサブスクリプションの再初期化を選択してから、一度もパブリケーションのスナップショット エージェントが開始されていない場合は、スナップショット エージェントを開始し、完了した後でディストリビューション エージェントを開始します。</span><span class="sxs-lookup"><span data-stu-id="9356a-120">If the Snapshot Agent for the publication has not been started since the subscription was created, or if it has not been started since the last time you chose to reinitialize the subscription, start the Snapshot Agent and let it complete before starting the Distribution Agent.</span></span> <span data-ttu-id="9356a-121">詳細については、「[スナップショットの作成および適用](create-and-apply-the-snapshot.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9356a-121">For more information, see [Create and Apply the Snapshot](create-and-apply-the-snapshot.md).</span></span>  
  
 <span data-ttu-id="9356a-122">スナップショット エージェントが完了しない場合は、スナップショット エージェントの履歴でエラーを確認して対応します。</span><span class="sxs-lookup"><span data-stu-id="9356a-122">If the Snapshot Agent does not complete, check the Snapshot Agent history for errors and address them.</span></span> <span data-ttu-id="9356a-123">レプリケーション モニターでのエージェントの状態やエラーの詳細の表示について詳しくは、「[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9356a-123">For information about viewing agent status and error details in Replication Monitor, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="9356a-124">エラーの発生が継続する場合は、エージェントのログ記録を増やし、ログの出力ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="9356a-124">If the error continues to occur, increase the logging of the agent and specify an output file for the log.</span></span> <span data-ttu-id="9356a-125">エラーのコンテキストによっては、エラーや他のエラー メッセージにつながる手順が示される可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="9356a-125">Depending on the context of the error, this could provide the steps leading up to the error and/or additional error messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9356a-126">参照</span><span class="sxs-lookup"><span data-stu-id="9356a-126">See Also</span></span>  
 [<span data-ttu-id="9356a-127">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="9356a-127">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
