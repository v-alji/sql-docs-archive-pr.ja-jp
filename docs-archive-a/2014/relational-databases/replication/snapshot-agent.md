---
title: スナップショット エージェント | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.snapshotagent.f1
helpviewer_keywords:
- Snapshot Agent dialog box
ms.assetid: b715e621-2cd5-4a15-8f58-a341aa8ef5e4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 925f2d3841b5dded6c8504a4a05dc60e61024161
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645503"
---
# <a name="snapshot-agent"></a><span data-ttu-id="465bd-102">スナップショット エージェント</span><span class="sxs-lookup"><span data-stu-id="465bd-102">Snapshot Agent</span></span>
  <span data-ttu-id="465bd-103">**[スナップショット エージェント]** ダイアログ ボックスには、状態、履歴、情報メッセージ、およびすべてのエラー メッセージを含む、スナップショット エージェントの詳細情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="465bd-103">The **Snapshot Agent** dialog box displays detailed information on the Snapshot Agent, including status, history, informational messages, and any error messages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="465bd-104">オプション</span><span class="sxs-lookup"><span data-stu-id="465bd-104">Options</span></span>  
 <span data-ttu-id="465bd-105">表示するスナップショット エージェントのセッションを **[表示]** メニューで選択した後、 **[スナップショット エージェントのセッション]** というラベルのグリッドで特定のセッションを選択します。</span><span class="sxs-lookup"><span data-stu-id="465bd-105">Select which Snapshot Agent sessions to view from the **View** menu, and then select a specific session in the grid labeled **Sessions of the Snapshot Agent**.</span></span> <span data-ttu-id="465bd-106">このセッションの詳細情報は、 **[選択されたセッションのアクション]** というラベルのグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="465bd-106">Detailed information on this session is displayed in the grid labeled **Actions in the selected session**.</span></span> <span data-ttu-id="465bd-107">選択したセッションがエラーで終了した場合は、 **[選択されたセッションのエラーの詳細またはメッセージ]** というラベルのテキスト領域も表示されます。</span><span class="sxs-lookup"><span data-stu-id="465bd-107">If the selected session ended in an error, the text area labeled **Error details or message of the selected session** is also displayed.</span></span>  
  
 <span data-ttu-id="465bd-108">**表示**</span><span class="sxs-lookup"><span data-stu-id="465bd-108">**View**</span></span>  
 <span data-ttu-id="465bd-109">表示するスナップショット エージェント セッションを選択します。</span><span class="sxs-lookup"><span data-stu-id="465bd-109">Select which Snapshot Agent sessions to view.</span></span>  
  
 <span data-ttu-id="465bd-110">**状態**</span><span class="sxs-lookup"><span data-stu-id="465bd-110">**Status**</span></span>  
 <span data-ttu-id="465bd-111">スナップショット エージェントの状態です。</span><span class="sxs-lookup"><span data-stu-id="465bd-111">The status of the Snapshot Agent.</span></span> <span data-ttu-id="465bd-112">表示される状態の種類を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="465bd-112">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="465bd-113">エラー</span><span class="sxs-lookup"><span data-stu-id="465bd-113">Error</span></span>  
  
-   <span data-ttu-id="465bd-114">[失敗したコマンドの再試行]</span><span class="sxs-lookup"><span data-stu-id="465bd-114">Retrying failed commands</span></span>  
  
-   <span data-ttu-id="465bd-115">[実行されていません]</span><span class="sxs-lookup"><span data-stu-id="465bd-115">Not running</span></span>  
  
-   <span data-ttu-id="465bd-116">[完了]</span><span class="sxs-lookup"><span data-stu-id="465bd-116">Completed</span></span>  
  
 <span data-ttu-id="465bd-117">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="465bd-117">**Start Time**</span></span>  
 <span data-ttu-id="465bd-118">セッションの開始時刻です。</span><span class="sxs-lookup"><span data-stu-id="465bd-118">The start time of the session.</span></span>  
  
 <span data-ttu-id="465bd-119">**[終了時刻]**</span><span class="sxs-lookup"><span data-stu-id="465bd-119">**End Time**</span></span>  
 <span data-ttu-id="465bd-120">セッションの終了時刻です。</span><span class="sxs-lookup"><span data-stu-id="465bd-120">The end time of the session.</span></span> <span data-ttu-id="465bd-121">エージェントが停止していない場合は、このフィールドは空になっています。</span><span class="sxs-lookup"><span data-stu-id="465bd-121">If the agent has not stopped, this field is empty.</span></span>  
  
 <span data-ttu-id="465bd-122">**Duration**</span><span class="sxs-lookup"><span data-stu-id="465bd-122">**Duration**</span></span>  
 <span data-ttu-id="465bd-123">このセッションでスナップショット エージェントが実行された時間の合計です。</span><span class="sxs-lookup"><span data-stu-id="465bd-123">The amount of time the Snapshot Agent has run in this session.</span></span> <span data-ttu-id="465bd-124">この時間は、エージェントが現在実行中の場合の経過時間と、エージェント セッションが終了した場合のセッションの合計時間を表します。</span><span class="sxs-lookup"><span data-stu-id="465bd-124">The time represents elapsed time if the agent is currently running and the total time of the session if the agent session has ended.</span></span>  
  
 <span data-ttu-id="465bd-125">**エラー メッセージ**</span><span class="sxs-lookup"><span data-stu-id="465bd-125">**Error Message**</span></span>  
 <span data-ttu-id="465bd-126">セッションがエラーで終了した場合、スナップショット エージェントによって記録された最新のエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="465bd-126">If a session ended in an error, this field displays the last error message logged by the Snapshot Agent.</span></span> <span data-ttu-id="465bd-127">セッションがエラーで終了しなかった場合は、このフィールドは空白です。</span><span class="sxs-lookup"><span data-stu-id="465bd-127">If a session did not end in an error, this field is blank.</span></span>  
  
 <span data-ttu-id="465bd-128">**[動作メッセージ]**</span><span class="sxs-lookup"><span data-stu-id="465bd-128">**Action Message**</span></span>  
 <span data-ttu-id="465bd-129">選択したセッション中にスナップショット エージェントによって記録された、すべての情報メッセージとエラー メッセージです。</span><span class="sxs-lookup"><span data-stu-id="465bd-129">All informational messages and error messages that the Snapshot Agent has logged during the selected session.</span></span>  
  
 <span data-ttu-id="465bd-130">**[動作時間]**</span><span class="sxs-lookup"><span data-stu-id="465bd-130">**Action Time**</span></span>  
 <span data-ttu-id="465bd-131">**[動作メッセージ]** 列で説明されたアクションが実行された時間です。</span><span class="sxs-lookup"><span data-stu-id="465bd-131">The time at which the action described in the **Action Message** column was performed.</span></span>  
  
 <span data-ttu-id="465bd-132">**[選択されたセッションのエラーの詳細またはメッセージ]**</span><span class="sxs-lookup"><span data-stu-id="465bd-132">**Error details or message of the selected session**</span></span>  
 <span data-ttu-id="465bd-133">選択したセッションの **[状態]** 列に **[エラー]** の値が表示されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="465bd-133">Is displayed only if the selected session displays a value of **Error** in the **Status** column.</span></span> <span data-ttu-id="465bd-134">このテキスト領域では、エラーの詳細情報とエラーの発生時に試行されたコマンドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="465bd-134">This text area displays detailed error information and the command that was attempted at the time of the error.</span></span> <span data-ttu-id="465bd-135">エラーに関連する追加コンテンツへのリンクも含まれます。</span><span class="sxs-lookup"><span data-stu-id="465bd-135">It also includes links to additional content related to the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="465bd-136">参照</span><span class="sxs-lookup"><span data-stu-id="465bd-136">See Also</span></span>  
 <span data-ttu-id="465bd-137">[レプリケーション モニターの開始](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="465bd-137">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="465bd-138">[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="465bd-138">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="465bd-139">[レプリケーションの監視](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="465bd-139">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="465bd-140">レプリケーション エージェントの概要</span><span class="sxs-lookup"><span data-stu-id="465bd-140">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
