---
title: サブスクリプション、[パブリッシャーからディストリビューターまでの履歴] (トランザクション サブスクリプション) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.pubtodist.tran.f1
ms.assetid: d5a4c697-1342-49fd-8b7b-b059af32556a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3806c59e545e325fa7e60f2cd92a4b990b0505cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743205"
---
# <a name="subscription-publisher-to-distributor-history-transactional-subscription"></a><span data-ttu-id="56698-102">サブスクリプション、[パブリッシャーからディストリビューターまでの履歴] (トランザクション サブスクリプション)</span><span class="sxs-lookup"><span data-stu-id="56698-102">Subscription, Publisher to Distributor History (Transactional Subscription)</span></span>
  <span data-ttu-id="56698-103">**[パブリッシャーからディストリビューターまでの履歴]** タブでは、ステータス、履歴、情報メッセージ、およびすべてのエラー メッセージを含む、ログ リーダー エージェントの詳細情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="56698-103">The **Publisher to Distributor History** tab displays detailed information on the Log Reader Agent, including status, history, informational messages, and any error messages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="56698-104">Options</span><span class="sxs-lookup"><span data-stu-id="56698-104">Options</span></span>  
 <span data-ttu-id="56698-105">**[表示]** メニューから表示するログ リーダー エージェントのセッションを選択し、 **[ログ リーダー エージェントのセッション]** というラベルのグリッド内で特定のセッションを選択します。</span><span class="sxs-lookup"><span data-stu-id="56698-105">Select which Log Reader Agent sessions to view from the **View** menu, and then select a specific session in the grid labeled **Sessions of the Log Reader Agent**.</span></span> <span data-ttu-id="56698-106">このセッションの詳細情報は、 **[選択されたセッションのアクション]** というラベルのグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="56698-106">Detailed information on this session is displayed in the grid labeled **Actions in the selected session**.</span></span> <span data-ttu-id="56698-107">選択したセッションがエラーで終了した場合は、 **[選択されたセッションのエラーの詳細またはメッセージ]** というラベルのテキスト領域も表示されます。</span><span class="sxs-lookup"><span data-stu-id="56698-107">If the selected session ended in an error, the text area labeled **Error details or message of the selected session** is also displayed.</span></span>  
  
 <span data-ttu-id="56698-108">**表示**</span><span class="sxs-lookup"><span data-stu-id="56698-108">**View**</span></span>  
 <span data-ttu-id="56698-109">表示するログ リーダー エージェントのセッションを選択します。</span><span class="sxs-lookup"><span data-stu-id="56698-109">Select which Log Reader Agent sessions to view.</span></span> <span data-ttu-id="56698-110">通常、ログ リーダー エージェントは継続的に実行されるため、表示するセッションが 1 つのみの場合があります。</span><span class="sxs-lookup"><span data-stu-id="56698-110">The Log Reader Agent typically runs continuously, therefore there might be only one session to view.</span></span>  
  
 <span data-ttu-id="56698-111">**状態**</span><span class="sxs-lookup"><span data-stu-id="56698-111">**Status**</span></span>  
 <span data-ttu-id="56698-112">ログ リーダー エージェントの状態です。</span><span class="sxs-lookup"><span data-stu-id="56698-112">The status of the Log Reader Agent.</span></span> <span data-ttu-id="56698-113">表示される状態の種類を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="56698-113">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="56698-114">エラー</span><span class="sxs-lookup"><span data-stu-id="56698-114">Error</span></span>  
  
-   <span data-ttu-id="56698-115">完了</span><span class="sxs-lookup"><span data-stu-id="56698-115">Completed</span></span>  
  
-   <span data-ttu-id="56698-116">[再試行中]</span><span class="sxs-lookup"><span data-stu-id="56698-116">Retrying</span></span>  
  
-   <span data-ttu-id="56698-117">実行中</span><span class="sxs-lookup"><span data-stu-id="56698-117">Running</span></span>  
  
 <span data-ttu-id="56698-118">**開始時刻**</span><span class="sxs-lookup"><span data-stu-id="56698-118">**Start Time**</span></span>  
 <span data-ttu-id="56698-119">セッションの開始時刻です。</span><span class="sxs-lookup"><span data-stu-id="56698-119">The start time of the session.</span></span>  
  
 <span data-ttu-id="56698-120">**終了時刻**</span><span class="sxs-lookup"><span data-stu-id="56698-120">**End Time**</span></span>  
 <span data-ttu-id="56698-121">セッションの終了時刻です。</span><span class="sxs-lookup"><span data-stu-id="56698-121">The end time of the session.</span></span> <span data-ttu-id="56698-122">エージェントが停止していない場合は、このフィールドは空になっています。</span><span class="sxs-lookup"><span data-stu-id="56698-122">If the agent has not stopped, this field is empty.</span></span>  
  
 <span data-ttu-id="56698-123">**Duration**</span><span class="sxs-lookup"><span data-stu-id="56698-123">**Duration**</span></span>  
 <span data-ttu-id="56698-124">ログ リーダー エージェントがこのセッション中に実行されている合計時間です。</span><span class="sxs-lookup"><span data-stu-id="56698-124">The amount of time the Log Reader Agent has run in this session.</span></span> <span data-ttu-id="56698-125">この時間は、エージェントが現在実行中の場合の経過時間と、エージェント セッションが終了した場合のセッションの合計時間を表します。</span><span class="sxs-lookup"><span data-stu-id="56698-125">The time represents elapsed time if the agent is currently running and the total time of the session if the agent session has ended.</span></span>  
  
 <span data-ttu-id="56698-126">**エラー メッセージ**</span><span class="sxs-lookup"><span data-stu-id="56698-126">**Error Message**</span></span>  
 <span data-ttu-id="56698-127">セッションがエラーで終了した場合、ログ リーダー エージェントによって記録された最新のエラー メッセージがこのフィールドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="56698-127">If a session ended in an error, this field displays the last error message logged by the Log Reader Agent.</span></span> <span data-ttu-id="56698-128">セッションがエラーで終了しなかった場合は、このフィールドは空白です。</span><span class="sxs-lookup"><span data-stu-id="56698-128">If a session did not end in an error, this field is blank.</span></span>  
  
 <span data-ttu-id="56698-129">**[動作メッセージ]**</span><span class="sxs-lookup"><span data-stu-id="56698-129">**Action Message**</span></span>  
 <span data-ttu-id="56698-130">選択したセッション中にログ リーダー エージェントによって記録された、すべての情報メッセージとエラー メッセージです。</span><span class="sxs-lookup"><span data-stu-id="56698-130">All informational messages and error messages that the Log Reader Agent has logged during the selected session.</span></span>  
  
 <span data-ttu-id="56698-131">**[動作時間]**</span><span class="sxs-lookup"><span data-stu-id="56698-131">**Action Time**</span></span>  
 <span data-ttu-id="56698-132">**[動作メッセージ]** 列で説明されたアクションが実行された時間です。</span><span class="sxs-lookup"><span data-stu-id="56698-132">The time at which the action described in the **Action Message** column was performed.</span></span>  
  
 <span data-ttu-id="56698-133">**[選択されたセッションのエラーの詳細またはメッセージ]**</span><span class="sxs-lookup"><span data-stu-id="56698-133">**Error details or message of the selected session**</span></span>  
 <span data-ttu-id="56698-134">選択したセッションの **[状態]** 列に **[エラー]** の値が表示されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="56698-134">Displayed only if the selected session displays a value of **Error** in the **Status** column.</span></span> <span data-ttu-id="56698-135">このテキスト領域では、エラーの詳細情報とエラーの発生時に試行されたコマンドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="56698-135">This text area displays detailed error information and the command that was attempted at the time of the error.</span></span> <span data-ttu-id="56698-136">エラーに関連する追加コンテンツへのリンクも含まれます。</span><span class="sxs-lookup"><span data-stu-id="56698-136">It also includes links to additional content related to the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56698-137">参照</span><span class="sxs-lookup"><span data-stu-id="56698-137">See Also</span></span>  
 <span data-ttu-id="56698-138">[レプリケーションモニターを開始する](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="56698-138">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="56698-139">[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="56698-139">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="56698-140">[レプリケーションの監視](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="56698-140">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="56698-141">レプリケーション エージェントの概要</span><span class="sxs-lookup"><span data-stu-id="56698-141">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
