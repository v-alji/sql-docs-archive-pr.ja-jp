---
title: サブスクリプション、[ディストリビューターからサブスクライバーまでの履歴](トランザクション サブスクリプション) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.disttosub.f1
ms.assetid: 1aad5b82-592e-4907-92f7-b90794175be5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5cb9d708b75a9414725907530c7454cdba26d135
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740798"
---
# <a name="subscription-distributor-to-subscriber-history-transactional-subscription"></a><span data-ttu-id="de75d-102">サブスクリプション、[ディストリビューターからサブスクライバーまでの履歴] (トランザクション サブスクリプション)</span><span class="sxs-lookup"><span data-stu-id="de75d-102">Subscription, Distributor to Subscriber History (Transactional Subscription)</span></span>
  <span data-ttu-id="de75d-103">**[ディストリビューターからサブスクライバーまでの履歴]** タブでは、ステータス、履歴、情報メッセージ、およびすべてのエラー メッセージを含む、ディストリビューション エージェントの詳細情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="de75d-103">The **Distributor to Subscriber History** tab displays detailed information on the Distribution Agent, including status, history, informational messages, and any error messages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="de75d-104">Options</span><span class="sxs-lookup"><span data-stu-id="de75d-104">Options</span></span>  
 <span data-ttu-id="de75d-105">表示するディストリビューション エージェントのセッションを **[表示]** メニューで選択した後、 **[ディストリビューション エージェントのセッション]** というラベルのグリッドで特定のセッションを選択します。</span><span class="sxs-lookup"><span data-stu-id="de75d-105">Select which Distribution Agent sessions to view from the **View** menu, and then select a specific session in the grid labeled **Sessions of the Distribution Agent**.</span></span> <span data-ttu-id="de75d-106">このセッションの詳細情報は、 **[選択されたセッションのアクション]** というラベルのグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="de75d-106">Detailed information on this session is displayed in the grid labeled **Actions in the selected session**.</span></span> <span data-ttu-id="de75d-107">選択したセッションがエラーで終了した場合は、 **[選択されたセッションのエラーの詳細またはメッセージ]** というラベルのテキスト領域も表示されます。</span><span class="sxs-lookup"><span data-stu-id="de75d-107">If the selected session ended in an error, the text area labeled **Error details or message of the selected session** is also displayed.</span></span>  
  
 <span data-ttu-id="de75d-108">**表示**</span><span class="sxs-lookup"><span data-stu-id="de75d-108">**View**</span></span>  
 <span data-ttu-id="de75d-109">表示するディストリビューション エージェントのセッションを選択します。</span><span class="sxs-lookup"><span data-stu-id="de75d-109">Select which Distribution Agent sessions to view.</span></span> <span data-ttu-id="de75d-110">一般的に、ディストリビューション エージェントは継続的に実行されるため、表示されるセッションが 1 つのみである場合もあります。</span><span class="sxs-lookup"><span data-stu-id="de75d-110">The Distribution Agent typically runs continuously, therefore there might be only one session to view.</span></span>  
  
 <span data-ttu-id="de75d-111">**状態**</span><span class="sxs-lookup"><span data-stu-id="de75d-111">**Status**</span></span>  
 <span data-ttu-id="de75d-112">ディストリビューション エージェントの状態です。</span><span class="sxs-lookup"><span data-stu-id="de75d-112">The status of the Distribution Agent.</span></span> <span data-ttu-id="de75d-113">表示される状態の種類を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="de75d-113">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="de75d-114">エラー</span><span class="sxs-lookup"><span data-stu-id="de75d-114">Error</span></span>  
  
-   <span data-ttu-id="de75d-115">完了</span><span class="sxs-lookup"><span data-stu-id="de75d-115">Completed</span></span>  
  
-   <span data-ttu-id="de75d-116">[再試行中]</span><span class="sxs-lookup"><span data-stu-id="de75d-116">Retrying</span></span>  
  
-   <span data-ttu-id="de75d-117">実行中</span><span class="sxs-lookup"><span data-stu-id="de75d-117">Running</span></span>  
  
 <span data-ttu-id="de75d-118">**開始時刻**</span><span class="sxs-lookup"><span data-stu-id="de75d-118">**Start Time**</span></span>  
 <span data-ttu-id="de75d-119">セッションの開始時刻です。</span><span class="sxs-lookup"><span data-stu-id="de75d-119">The start time of the session.</span></span>  
  
 <span data-ttu-id="de75d-120">**終了時刻**</span><span class="sxs-lookup"><span data-stu-id="de75d-120">**End Time**</span></span>  
 <span data-ttu-id="de75d-121">セッションの終了時刻です。</span><span class="sxs-lookup"><span data-stu-id="de75d-121">The end time of the session.</span></span> <span data-ttu-id="de75d-122">エージェントが停止していない場合は、このフィールドは空になっています。</span><span class="sxs-lookup"><span data-stu-id="de75d-122">If the agent has not stopped, this field is empty.</span></span>  
  
 <span data-ttu-id="de75d-123">**Duration**</span><span class="sxs-lookup"><span data-stu-id="de75d-123">**Duration**</span></span>  
 <span data-ttu-id="de75d-124">このセッションでディストリビューション エージェントが実行された時間の合計です。</span><span class="sxs-lookup"><span data-stu-id="de75d-124">The amount of time the Distribution Agent has run in this session.</span></span> <span data-ttu-id="de75d-125">この時間は、エージェントが現在実行中の場合の経過時間と、エージェント セッションが終了した場合のセッションの合計時間を表します。</span><span class="sxs-lookup"><span data-stu-id="de75d-125">The time represents elapsed time if the agent is currently running and the total time of the session if the agent session has ended.</span></span>  
  
 <span data-ttu-id="de75d-126">**エラー メッセージ**</span><span class="sxs-lookup"><span data-stu-id="de75d-126">**Error Message**</span></span>  
 <span data-ttu-id="de75d-127">セッションがエラーで終了した場合は、ディストリビューション エージェントによって記録された最新のエラー メッセージがこのフィールドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="de75d-127">If a session ended in an error, this field displays the last error message logged by the Distribution Agent.</span></span> <span data-ttu-id="de75d-128">セッションがエラーで終了しなかった場合は、このフィールドは空白です。</span><span class="sxs-lookup"><span data-stu-id="de75d-128">If a session did not end in an error, this field is blank.</span></span>  
  
 <span data-ttu-id="de75d-129">**[動作メッセージ]**</span><span class="sxs-lookup"><span data-stu-id="de75d-129">**Action Message**</span></span>  
 <span data-ttu-id="de75d-130">選択したセッション中に、ディストリビューション エージェントによってログに記録された、すべての情報メッセージとエラー メッセージです。</span><span class="sxs-lookup"><span data-stu-id="de75d-130">All informational messages and error messages that the Distribution Agent has logged during the selected session.</span></span>  
  
 <span data-ttu-id="de75d-131">**[動作時間]**</span><span class="sxs-lookup"><span data-stu-id="de75d-131">**Action Time**</span></span>  
 <span data-ttu-id="de75d-132">**[動作メッセージ]** 列で説明されたアクションが実行された時間です。</span><span class="sxs-lookup"><span data-stu-id="de75d-132">The time at which the action described in the **Action Message** column was performed.</span></span>  
  
 <span data-ttu-id="de75d-133">**[選択されたセッションのエラーの詳細またはメッセージ]**</span><span class="sxs-lookup"><span data-stu-id="de75d-133">**Error details or message of the selected session**</span></span>  
 <span data-ttu-id="de75d-134">選択したセッションの **[状態]** 列に **[エラー]** の値が表示されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="de75d-134">Displayed only if the selected session displays a value of **Error** in the **Status** column.</span></span> <span data-ttu-id="de75d-135">このテキスト領域では、エラーの詳細情報とエラーの発生時に試行されたコマンドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="de75d-135">This text area displays detailed error information and the command that was attempted at the time of the error.</span></span> <span data-ttu-id="de75d-136">エラーに関連する追加コンテンツへのリンクも含まれます。</span><span class="sxs-lookup"><span data-stu-id="de75d-136">It also includes links to additional content related to the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de75d-137">参照</span><span class="sxs-lookup"><span data-stu-id="de75d-137">See Also</span></span>  
 <span data-ttu-id="de75d-138">[レプリケーションモニターを開始する](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="de75d-138">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="de75d-139">[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="de75d-139">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="de75d-140">[レプリケーションの監視](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="de75d-140">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="de75d-141">レプリケーション エージェントの概要</span><span class="sxs-lookup"><span data-stu-id="de75d-141">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
