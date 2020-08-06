---
title: サブスクリプション、[ディストリビューターからサブスクライバーまでの履歴] (スナップショット サブスクリプション) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.pubtodist.snapshot.f1
ms.assetid: d3575964-f287-4bcf-8d2e-f81a33141b25
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fe894e23e7ad7fef9c328334740eff73164130a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740797"
---
# <a name="subscription-distributor-to-subscriber-history-snapshot-subscription"></a><span data-ttu-id="6c0ce-102">サブスクリプション、[ディストリビューターからサブスクライバーまでの履歴] (スナップショット サブスクリプション)</span><span class="sxs-lookup"><span data-stu-id="6c0ce-102">Subscription, Distributor to Subscriber History (Snapshot Subscription)</span></span>
  <span data-ttu-id="6c0ce-103">**[ディストリビューターからサブスクライバーまでの履歴]** タブでは、ステータス、履歴、情報メッセージ、およびすべてのエラー メッセージを含む、ディストリビューション エージェントの詳細情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c0ce-103">The **Distributor to Subscriber History** tab displays detailed information on the Distribution Agent, including status, history, informational messages, and any error messages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6c0ce-104">Options</span><span class="sxs-lookup"><span data-stu-id="6c0ce-104">Options</span></span>  
 <span data-ttu-id="6c0ce-105">表示するディストリビューション エージェントのセッションを **[表示]** メニューで選択した後、 **[ディストリビューション エージェントのセッション]** というラベルのグリッドで特定のセッションを選択します。</span><span class="sxs-lookup"><span data-stu-id="6c0ce-105">Select which Distribution Agent sessions to view from the **View** menu, and then select a specific session in the grid labeled **Sessions of the Distribution Agent**.</span></span> <span data-ttu-id="6c0ce-106">このセッションの詳細情報は、 **[選択されたセッションのアクション]** というラベルのグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c0ce-106">Detailed information on this session is displayed in the grid labeled **Actions in the selected session**.</span></span> <span data-ttu-id="6c0ce-107">選択したセッションがエラーで終了した場合は、 **[選択されたセッションのエラーの詳細またはメッセージ]** というラベルのテキスト領域も表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c0ce-107">If the selected session ended in an error, the text area labeled **Error details or message of the selected session** is also displayed.</span></span>  
  
 <span data-ttu-id="6c0ce-108">**表示**</span><span class="sxs-lookup"><span data-stu-id="6c0ce-108">**View**</span></span>  
 <span data-ttu-id="6c0ce-109">表示するディストリビューション エージェントのセッションを選択します。</span><span class="sxs-lookup"><span data-stu-id="6c0ce-109">Select which Distribution Agent sessions to view.</span></span>  
  
 <span data-ttu-id="6c0ce-110">**状態**</span><span class="sxs-lookup"><span data-stu-id="6c0ce-110">**Status**</span></span>  
 <span data-ttu-id="6c0ce-111">ディストリビューション エージェントの状態です。</span><span class="sxs-lookup"><span data-stu-id="6c0ce-111">The status of the Distribution Agent.</span></span> <span data-ttu-id="6c0ce-112">表示される状態の種類を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="6c0ce-112">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="6c0ce-113">エラー</span><span class="sxs-lookup"><span data-stu-id="6c0ce-113">Error</span></span>  
  
-   <span data-ttu-id="6c0ce-114">完了</span><span class="sxs-lookup"><span data-stu-id="6c0ce-114">Completed</span></span>  
  
-   <span data-ttu-id="6c0ce-115">[再試行中]</span><span class="sxs-lookup"><span data-stu-id="6c0ce-115">Retrying</span></span>  
  
-   <span data-ttu-id="6c0ce-116">実行中</span><span class="sxs-lookup"><span data-stu-id="6c0ce-116">Running</span></span>  
  
 <span data-ttu-id="6c0ce-117">**開始時刻**</span><span class="sxs-lookup"><span data-stu-id="6c0ce-117">**Start Time**</span></span>  
 <span data-ttu-id="6c0ce-118">セッションの開始時刻です。</span><span class="sxs-lookup"><span data-stu-id="6c0ce-118">The start time of the session.</span></span>  
  
 <span data-ttu-id="6c0ce-119">**終了時刻**</span><span class="sxs-lookup"><span data-stu-id="6c0ce-119">**End Time**</span></span>  
 <span data-ttu-id="6c0ce-120">セッションの終了時刻です。</span><span class="sxs-lookup"><span data-stu-id="6c0ce-120">The end time of the session.</span></span> <span data-ttu-id="6c0ce-121">エージェントが停止していない場合は、このフィールドは空になっています。</span><span class="sxs-lookup"><span data-stu-id="6c0ce-121">If the agent has not stopped, this field is empty.</span></span>  
  
 <span data-ttu-id="6c0ce-122">**Duration**</span><span class="sxs-lookup"><span data-stu-id="6c0ce-122">**Duration**</span></span>  
 <span data-ttu-id="6c0ce-123">このセッションでディストリビューション エージェントが実行された時間の合計です。</span><span class="sxs-lookup"><span data-stu-id="6c0ce-123">The amount of time the Distribution Agent has run in this session.</span></span> <span data-ttu-id="6c0ce-124">エージェントが現在実行中の場合、経過時間を表します。エージェントが終了している場合、セッションの合計時間を表します。</span><span class="sxs-lookup"><span data-stu-id="6c0ce-124">The time represents elapsed time if the agent is currently running and the total time of the session if the agent session had ended.</span></span>  
  
 <span data-ttu-id="6c0ce-125">**エラー メッセージ**</span><span class="sxs-lookup"><span data-stu-id="6c0ce-125">**Error Message**</span></span>  
 <span data-ttu-id="6c0ce-126">セッションがエラーで終了した場合は、ディストリビューション エージェントによって記録された最新のエラー メッセージがこのフィールドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c0ce-126">If a session ended in an error, this field displays the last error message logged by the Distribution Agent.</span></span> <span data-ttu-id="6c0ce-127">セッションがエラーで終了しなかった場合は、このフィールドは空白です。</span><span class="sxs-lookup"><span data-stu-id="6c0ce-127">If a session did not end in an error, this field is blank.</span></span>  
  
 <span data-ttu-id="6c0ce-128">**[動作メッセージ]**</span><span class="sxs-lookup"><span data-stu-id="6c0ce-128">**Action Message**</span></span>  
 <span data-ttu-id="6c0ce-129">選択したセッション中に、ディストリビューション エージェントによってログに記録された、すべての情報メッセージとエラー メッセージです。</span><span class="sxs-lookup"><span data-stu-id="6c0ce-129">All informational messages and error messages that the Distribution Agent has logged during the selected session.</span></span>  
  
 <span data-ttu-id="6c0ce-130">**[動作時間]**</span><span class="sxs-lookup"><span data-stu-id="6c0ce-130">**Action Time**</span></span>  
 <span data-ttu-id="6c0ce-131">**[動作メッセージ]** 列で説明されたアクションが実行された時間です。</span><span class="sxs-lookup"><span data-stu-id="6c0ce-131">The time at which the action described in the **Action Message** column was performed.</span></span>  
  
 <span data-ttu-id="6c0ce-132">**[選択されたセッションのエラーの詳細またはメッセージ]**</span><span class="sxs-lookup"><span data-stu-id="6c0ce-132">**Error details or message of the selected session**</span></span>  
 <span data-ttu-id="6c0ce-133">選択したセッションの **[状態]** 列に **[エラー]** の値が表示されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c0ce-133">Displayed only if the selected session displays a value of **Error** in the **Status** column.</span></span> <span data-ttu-id="6c0ce-134">このテキスト領域では、エラーの詳細情報とエラーの発生時に試行されたコマンドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c0ce-134">This text area displays detailed error information and the command that was attempted at the time of the error.</span></span> <span data-ttu-id="6c0ce-135">エラーに関連する追加コンテンツへのリンクも含まれます。</span><span class="sxs-lookup"><span data-stu-id="6c0ce-135">It also includes links to additional content related to the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c0ce-136">参照</span><span class="sxs-lookup"><span data-stu-id="6c0ce-136">See Also</span></span>  
 <span data-ttu-id="6c0ce-137">[レプリケーションモニターを開始する](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="6c0ce-137">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="6c0ce-138">[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="6c0ce-138">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="6c0ce-139">[レプリケーションの監視](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="6c0ce-139">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="6c0ce-140">レプリケーション エージェントの概要</span><span class="sxs-lookup"><span data-stu-id="6c0ce-140">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
