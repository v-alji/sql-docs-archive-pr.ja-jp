---
title: パブリケーション情報、[エージェント] (トランザクション パブリケーション) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.downlevelagents.tran.f1
ms.assetid: 38ef2f54-53bb-4053-876d-86f8f06a4519
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1a3d50da15ea653a7911e65ad888d5997f47a3f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631800"
---
# <a name="publication-information-agents-transactional-publication"></a><span data-ttu-id="6d71d-102">パブリケーション情報、[エージェント] (トランザクション パブリケーション)</span><span class="sxs-lookup"><span data-stu-id="6d71d-102">Publication Information, Agents (Transactional Publication)</span></span>
  <span data-ttu-id="6d71d-103">**[エージェント]** タブには、選択したパブリケーションにおけるエージェントの要約情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d71d-103">The **Agents** tab displays summary information on the agents for the selected publication.</span></span> <span data-ttu-id="6d71d-104">すべてのトランザクション パブリケーションのスナップショット エージェントとログ リーダー エージェントの情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d71d-104">Information on the Snapshot Agent and Log Reader Agent is displayed for all transactional publications.</span></span> <span data-ttu-id="6d71d-105">キュー更新サブスクリプション用に有効になっているトランザクション パブリケーションについては、キュー リーダー エージェントに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d71d-105">Information on the Queue Reader Agent is displayed for those transactional publications that are enabled for queued updating subscriptions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6d71d-106">Options</span><span class="sxs-lookup"><span data-stu-id="6d71d-106">Options</span></span>  
 <span data-ttu-id="6d71d-107">エージェントに関する詳細情報やタスクを調べるには、そのエージェントの行を右クリックし、ショートカット メニューのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d71d-107">For more detailed information and tasks related to an agent, right-click the row for that agent, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="6d71d-108">グリッドにデータを表示する方法を変更するには、グリッドを右クリックし、次のいずれかのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d71d-108">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="6d71d-109">**[並べ替え]**: **[列の並べ替え]** ダイアログ ボックスで、1 つ以上の列を基準にして並べ替えを行います。</span><span class="sxs-lookup"><span data-stu-id="6d71d-109">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="6d71d-110">**[表示する列の選択]**: **[列の選択]** ダイアログ ボックスで、表示する列とその表示順序を選択します。</span><span class="sxs-lookup"><span data-stu-id="6d71d-110">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="6d71d-111">**[フィルター]**: **[フィルターの設定]** ダイアログ ボックスで、列の値に基づいてグリッドの行をフィルター選択します。</span><span class="sxs-lookup"><span data-stu-id="6d71d-111">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="6d71d-112">**[フィルターのクリア]**: グリッドのフィルター設定をすべてクリアします。</span><span class="sxs-lookup"><span data-stu-id="6d71d-112">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="6d71d-113">フィルター設定は各グリッドに固有です。</span><span class="sxs-lookup"><span data-stu-id="6d71d-113">Filter settings are specific to each grid.</span></span> <span data-ttu-id="6d71d-114">列の選択と並べ替えは、各パブリッシャーのパブリケーション グリッドなど、同じ種類のすべてのグリッドに適用されます。</span><span class="sxs-lookup"><span data-stu-id="6d71d-114">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="6d71d-115">**状態**</span><span class="sxs-lookup"><span data-stu-id="6d71d-115">**Status**</span></span>  
 <span data-ttu-id="6d71d-116">パブリケーションに関連付けられている、各レプリケーション エージェントの状態です。</span><span class="sxs-lookup"><span data-stu-id="6d71d-116">The status of each replication agent associated with the publication.</span></span> <span data-ttu-id="6d71d-117">表示される状態の種類を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="6d71d-117">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="6d71d-118">エラー</span><span class="sxs-lookup"><span data-stu-id="6d71d-118">Error</span></span>  
  
-   <span data-ttu-id="6d71d-119">[失敗したコマンドの再試行]</span><span class="sxs-lookup"><span data-stu-id="6d71d-119">Retrying failed commands</span></span>  
  
-   <span data-ttu-id="6d71d-120">[実行されていません]</span><span class="sxs-lookup"><span data-stu-id="6d71d-120">Not running</span></span>  
  
-   <span data-ttu-id="6d71d-121">実行中</span><span class="sxs-lookup"><span data-stu-id="6d71d-121">Running</span></span>  
  
-   <span data-ttu-id="6d71d-122">完了</span><span class="sxs-lookup"><span data-stu-id="6d71d-122">Completed</span></span>  
  
 <span data-ttu-id="6d71d-123">**エージェント**</span><span class="sxs-lookup"><span data-stu-id="6d71d-123">**Agent**</span></span>  
 <span data-ttu-id="6d71d-124">パブリケーションに関連付けられている、各レプリケーション エージェントの名前です。</span><span class="sxs-lookup"><span data-stu-id="6d71d-124">The name of each replication agent associated with the publication.</span></span> <span data-ttu-id="6d71d-125">ディストリビューション エージェントは、このパブリケーションに対するサブスクリプションに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="6d71d-125">The Distribution Agent is associated with subscriptions to this publication.</span></span> <span data-ttu-id="6d71d-126">詳細については、「[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d71d-126">For more information, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="6d71d-127">**前回の開始時刻**</span><span class="sxs-lookup"><span data-stu-id="6d71d-127">**Last Start Time**</span></span>  
 <span data-ttu-id="6d71d-128">エージェントが最後に起動された時刻です。</span><span class="sxs-lookup"><span data-stu-id="6d71d-128">The last time the agent started.</span></span>  
  
 <span data-ttu-id="6d71d-129">**Duration**</span><span class="sxs-lookup"><span data-stu-id="6d71d-129">**Duration**</span></span>  
 <span data-ttu-id="6d71d-130">エージェントが実行された時間の長さです。</span><span class="sxs-lookup"><span data-stu-id="6d71d-130">The amount of time the agent has run.</span></span> <span data-ttu-id="6d71d-131">この時間は、エージェントが現在実行中の場合は経過時間、エージェントが以前に実行されている場合は合計時間を表します。</span><span class="sxs-lookup"><span data-stu-id="6d71d-131">The time represents elapsed time if the agent is currently running and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="6d71d-132">**[最後のアクション]**</span><span class="sxs-lookup"><span data-stu-id="6d71d-132">**Last Action**</span></span>  
 <span data-ttu-id="6d71d-133">エージェントが最後に実行されたときに最後に実行されたアクションです。</span><span class="sxs-lookup"><span data-stu-id="6d71d-133">The last action performed during the most recent run of the agent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d71d-134">参照</span><span class="sxs-lookup"><span data-stu-id="6d71d-134">See Also</span></span>  
 <span data-ttu-id="6d71d-135">[レプリケーションモニターを開始する](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="6d71d-135">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="6d71d-136">[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="6d71d-136">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="6d71d-137">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="6d71d-137">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
