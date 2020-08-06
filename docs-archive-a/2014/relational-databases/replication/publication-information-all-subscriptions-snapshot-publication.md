---
title: パブリケーション情報、[すべてのサブスクリプション](スナップショット パブリケーション) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.allsubscriptions.snapshot.f1
ms.assetid: 7ce656c2-6e60-4625-8955-1daff641070c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 75eb85adae46481ddd4360f095c00060af5677fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641617"
---
# <a name="publication-information-all-subscriptions-snapshot-publication"></a><span data-ttu-id="ecc60-102">パブリケーション情報、[すべてのサブスクリプション] (スナップショット パブリケーション)</span><span class="sxs-lookup"><span data-stu-id="ecc60-102">Publication Information, All Subscriptions (Snapshot Publication)</span></span>
  <span data-ttu-id="ecc60-103">**[すべてのサブスクリプション]** タブには、選択したスナップショット パブリケーションに対するすべてのサブスクリプションの情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ecc60-103">The **All Subscriptions** tab displays information on all subscriptions to the selected snapshot publication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ecc60-104">Options</span><span class="sxs-lookup"><span data-stu-id="ecc60-104">Options</span></span>  
 <span data-ttu-id="ecc60-105">サブスクリプションに関する詳細情報やタスクを調べるには、そのサブスクリプションの行を右クリックし、ショートカット メニューのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ecc60-105">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="ecc60-106">グリッドにデータを表示する方法を変更するには、グリッドを右クリックし、次のいずれかのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ecc60-106">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="ecc60-107">**[並べ替え]**: **[列の並べ替え]** ダイアログ ボックスで、1 つ以上の列を基準にして並べ替えを行います。</span><span class="sxs-lookup"><span data-stu-id="ecc60-107">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="ecc60-108">**[表示する列の選択]**: **[列の選択]** ダイアログ ボックスで、表示する列とその表示順序を選択します。</span><span class="sxs-lookup"><span data-stu-id="ecc60-108">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="ecc60-109">**[フィルター]**: **[フィルターの設定]** ダイアログ ボックスで、列の値に基づいてグリッドの行をフィルター選択します。</span><span class="sxs-lookup"><span data-stu-id="ecc60-109">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="ecc60-110">**[フィルターのクリア]**: グリッドのフィルター設定をすべてクリアします。</span><span class="sxs-lookup"><span data-stu-id="ecc60-110">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="ecc60-111">フィルター設定は各グリッドに固有です。</span><span class="sxs-lookup"><span data-stu-id="ecc60-111">Filter settings are specific to each grid.</span></span> <span data-ttu-id="ecc60-112">列の選択と並べ替えは、各パブリッシャーのパブリケーション グリッドなど、同じ種類のすべてのグリッドに適用されます。</span><span class="sxs-lookup"><span data-stu-id="ecc60-112">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="ecc60-113">**表示**</span><span class="sxs-lookup"><span data-stu-id="ecc60-113">**Show**</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="ecc60-114">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみです。</span><span class="sxs-lookup"><span data-stu-id="ecc60-114">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="ecc60-115">サブスクリプション状態を選択すると、選択した種類の状態のサブスクリプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ecc60-115">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="ecc60-116">たとえば、エラーを含むサブスクリプションのみを表示するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="ecc60-116">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="ecc60-117">**状態**</span><span class="sxs-lookup"><span data-stu-id="ecc60-117">**Status**</span></span>  
 <span data-ttu-id="ecc60-118">各サブスクリプションの状態です。スナップショット エージェントまたはディストリビューション エージェントの状態 (より高い優先度の状態が表示されます) によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="ecc60-118">The status of each subscription, which is determined by the status of the Snapshot Agent or the Distribution Agent (the higher priority status is displayed).</span></span>  
  
 <span data-ttu-id="ecc60-119">既定では、サブスクリプション情報を表示するグリッドは **[状態]** 列の順序で並べられています。</span><span class="sxs-lookup"><span data-stu-id="ecc60-119">By default, the grid containing subscription information is sorted by the **Status** column.</span></span> <span data-ttu-id="ecc60-120">表示される状態の値と、その値の並べ替え順 (たとえば、エラーは常にグリッドの上部に表示されます) を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ecc60-120">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="ecc60-121">エラー</span><span class="sxs-lookup"><span data-stu-id="ecc60-121">Error</span></span>  
  
-   <span data-ttu-id="ecc60-122">[まもなく期限切れ/期限切れ] ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)</span><span class="sxs-lookup"><span data-stu-id="ecc60-122">Expiring soon/Expired ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="ecc60-123">[初期化されていないサブスクリプション]\([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)</span><span class="sxs-lookup"><span data-stu-id="ecc60-123">Uninitialized subscription ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="ecc60-124">[失敗したコマンドの再試行]</span><span class="sxs-lookup"><span data-stu-id="ecc60-124">Retrying failed command</span></span>  
  
-   <span data-ttu-id="ecc60-125">[同期中]</span><span class="sxs-lookup"><span data-stu-id="ecc60-125">Synchronizing</span></span>  
  
-   <span data-ttu-id="ecc60-126">[同期されていません]</span><span class="sxs-lookup"><span data-stu-id="ecc60-126">Not synchronizing</span></span>  
  
 <span data-ttu-id="ecc60-127">特定のサブスクリプションが複数の状態である場合に表示される値も、並べ替え順によって決まります。</span><span class="sxs-lookup"><span data-stu-id="ecc60-127">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="ecc60-128">たとえば、サブスクリプションにエラーがあり、まもなく期限切れになる場合、 **[状態]** 列には **[エラー]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="ecc60-128">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="ecc60-129">状態値 **[まもなく期限切れ/期限切れ]** および **[初期化されていないサブスクリプション]** は警告です。</span><span class="sxs-lookup"><span data-stu-id="ecc60-129">The status values **Expiring soon/Expired** and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="ecc60-130">警告が表示される場合、 **[状態]** 列にはエージェントが実行中かどうかも表示されます。</span><span class="sxs-lookup"><span data-stu-id="ecc60-130">When a warning is displayed, the **Status** column also displays if an agent is running.</span></span> <span data-ttu-id="ecc60-131">たとえば、 **[実行中]、[まもなく期限切れ/期限切れ]** という形式で状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ecc60-131">For example, the status could be **Running, Expiring soon/Expired**.</span></span>  
  
 <span data-ttu-id="ecc60-132">状態値 **[まもなく期限切れ/期限切れ]** は、しきい値が設定されている場合のみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="ecc60-132">The status value **Expiring soon/Expired** is displayed only if a threshold is set.</span></span> <span data-ttu-id="ecc60-133">しきい値の設定方法の詳細については、「[レプリケーション モニターのしきい値と警告の設定](monitor/set-thresholds-and-warnings-in-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ecc60-133">For information on setting thresholds, see [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="ecc60-134">**サブスクリプション**</span><span class="sxs-lookup"><span data-stu-id="ecc60-134">**Subscription**</span></span>  
 <span data-ttu-id="ecc60-135">各サブスクリプションの名前です。 *SubscriberName: SubscriptionDatabaseName*という形式になります。</span><span class="sxs-lookup"><span data-stu-id="ecc60-135">The name of each subscription, in the form: *SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="ecc60-136">**[最後の同期]**</span><span class="sxs-lookup"><span data-stu-id="ecc60-136">**Last Synchronization**</span></span>  
 <span data-ttu-id="ecc60-137">ディストリビューション エージェントが最後に実行された時刻です。</span><span class="sxs-lookup"><span data-stu-id="ecc60-137">The time at which the Distribution Agent last ran.</span></span> <span data-ttu-id="ecc60-138">同期が進行中の場合は、 **[実行中]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="ecc60-138">If synchronization is in progress, **In progress** is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecc60-139">参照</span><span class="sxs-lookup"><span data-stu-id="ecc60-139">See Also</span></span>  
 <span data-ttu-id="ecc60-140">[レプリケーションモニターを開始する](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="ecc60-140">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="ecc60-141">[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="ecc60-141">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="ecc60-142">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="ecc60-142">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
