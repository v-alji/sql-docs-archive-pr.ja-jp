---
title: MSSQL_ENG021075 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021075 error
ms.assetid: c8c29543-d1f6-49d5-b6c8-e8c3aa373090
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 20f2428038326681f5f8eb877e5c3017ced30f00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643251"
---
# <a name="mssql_eng021075"></a><span data-ttu-id="82ffc-102">MSSQL_ENG021075</span><span class="sxs-lookup"><span data-stu-id="82ffc-102">MSSQL_ENG021075</span></span>
    
## <a name="message-details"></a><span data-ttu-id="82ffc-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="82ffc-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="82ffc-104">製品名</span><span class="sxs-lookup"><span data-stu-id="82ffc-104">Product Name</span></span>|<span data-ttu-id="82ffc-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="82ffc-105">SQL Server</span></span>|  
|<span data-ttu-id="82ffc-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="82ffc-106">Event ID</span></span>|<span data-ttu-id="82ffc-107">21075</span><span class="sxs-lookup"><span data-stu-id="82ffc-107">21075</span></span>|  
|<span data-ttu-id="82ffc-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="82ffc-108">Event Source</span></span>|<span data-ttu-id="82ffc-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="82ffc-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="82ffc-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="82ffc-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="82ffc-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="82ffc-111">Symbolic Name</span></span>||  
|<span data-ttu-id="82ffc-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="82ffc-112">Message Text</span></span>|<span data-ttu-id="82ffc-113">パブリケーション '%s' の初期スナップショットはまだ使用できません。</span><span class="sxs-lookup"><span data-stu-id="82ffc-113">The initial snapshot for publication '%s' is not yet available.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="82ffc-114">説明</span><span class="sxs-lookup"><span data-stu-id="82ffc-114">Explanation</span></span>  
 <span data-ttu-id="82ffc-115">エラー MSSQL_ENG021075 は、スナップショット エージェントがスナップショットの生成を終える前にディストリビューション エージェントまたはマージ エージェントが開始されると発生します。</span><span class="sxs-lookup"><span data-stu-id="82ffc-115">Error MSSQL_ENG021075 is raised if the Distribution Agent or Merge Agent is started before the Snapshot Agent has finished generating the snapshot.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="82ffc-116">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="82ffc-116">User Action</span></span>  
 <span data-ttu-id="82ffc-117">サブスクリプションが作成されてから、または最後にサブスクリプションの再初期化を選択してから、一度もパブリケーションのスナップショット エージェントが開始されていない場合は、スナップショット エージェントを開始し、完了した後でディストリビューション エージェントまたはマージ エージェントを開始します。</span><span class="sxs-lookup"><span data-stu-id="82ffc-117">If the Snapshot Agent for the publication has not been started since the subscription was created, or if it has not been started since the last time you chose to reinitialize the subscription, start the Snapshot Agent and let it complete before starting the Distribution Agent or Merge Agent.</span></span> <span data-ttu-id="82ffc-118">詳細については、「[スナップショットの作成および適用](create-and-apply-the-snapshot.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82ffc-118">For more information, see [Create and Apply the Snapshot](create-and-apply-the-snapshot.md).</span></span>  
  
 <span data-ttu-id="82ffc-119">スナップショット エージェントが完了しない場合は、スナップショット エージェントの履歴でエラーを確認して対応します。</span><span class="sxs-lookup"><span data-stu-id="82ffc-119">If the Snapshot Agent does not complete, check the Snapshot Agent history for errors and address them.</span></span> <span data-ttu-id="82ffc-120">レプリケーション モニターでのエージェントの状態やエラーの詳細の表示について詳しくは、「[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82ffc-120">For information about viewing agent status and error details in Replication Monitor, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="82ffc-121">エラーの発生が継続する場合は、エージェントのログ記録を増やし、ログの出力ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="82ffc-121">If the error continues to occur, increase the logging of the agent and specify an output file for the log.</span></span> <span data-ttu-id="82ffc-122">エラーのコンテキストによっては、エラーや他のエラー メッセージにつながる手順が示される可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="82ffc-122">Depending on the context of the error, this could provide the steps leading up to the error and/or additional error messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82ffc-123">参照</span><span class="sxs-lookup"><span data-stu-id="82ffc-123">See Also</span></span>  
 [<span data-ttu-id="82ffc-124">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="82ffc-124">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
