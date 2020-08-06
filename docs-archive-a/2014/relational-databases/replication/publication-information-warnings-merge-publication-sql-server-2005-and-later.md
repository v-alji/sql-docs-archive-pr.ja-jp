---
title: パブリケーション情報、[警告] (マージパブリケーション、SQL Server 2005 以降) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.warningsandagents.merge.f1
ms.assetid: 9bef3565-5f13-42ac-8723-ebe55b0c11e6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 75f58a4cd9bd84791acf7fd9d28147ef3bbd6232
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641618"
---
# <a name="publication-information-warnings-merge-publication-sql-server-2005-and-later"></a><span data-ttu-id="0e210-102">パブリケーション情報、[警告] (マージ パブリケーション、SQL Server 2005 以降)</span><span class="sxs-lookup"><span data-stu-id="0e210-102">Publication Information, Warnings (Merge Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="0e210-103">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降を実行しているディストリビューターでは、**[警告]** タブを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0e210-103">The **Warnings** tab is available for Distributors that are running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span> <span data-ttu-id="0e210-104">**[警告]** タブでは、選択されているパブリケーションに対して次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="0e210-104">The **Warnings** tab allows you to perform the following tasks for the selected publication:</span></span>  
  
-   <span data-ttu-id="0e210-105">警告を有効にする。</span><span class="sxs-lookup"><span data-stu-id="0e210-105">Enable warnings.</span></span>  
  
-   <span data-ttu-id="0e210-106">警告に関連するしきい値を指定する。</span><span class="sxs-lookup"><span data-stu-id="0e210-106">Specify thresholds associated with warnings.</span></span>  
  
-   <span data-ttu-id="0e210-107">警告に関連する通知を定義する。</span><span class="sxs-lookup"><span data-stu-id="0e210-107">Define alerts associated with warnings.</span></span>  
  
## <a name="warnings-thresholds-and-alerts"></a><span data-ttu-id="0e210-108">警告、しきい値、および通知</span><span class="sxs-lookup"><span data-stu-id="0e210-108">Warnings, Thresholds, and Alerts</span></span>  
 <span data-ttu-id="0e210-109">既定では、レプリケーション モニターは、初期化されていないサブスクリプションに対して警告を表示します。サブスクリプション情報を含むページの **[状態]** 列に、警告として **[初期化されていないサブスクリプション]** という状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0e210-109">By default, Replication Monitor displays warnings for uninitialized subscriptions: a status of **Uninitialized subscription** is displayed as a warning in the **Status** column of pages that include subscription information.</span></span> <span data-ttu-id="0e210-110">マージ パブリケーションの場合は、以下の追加条件で警告を表示するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="0e210-110">For merge publications, you can specify whether these additional conditions result in warnings:</span></span>  
  
-   <span data-ttu-id="0e210-111">差し迫ったサブスクリプションの有効期限。</span><span class="sxs-lookup"><span data-stu-id="0e210-111">Imminent subscription expiration.</span></span>  
  
     <span data-ttu-id="0e210-112">これは、 **[サブスクリプションの有効期限がしきい値内で切れる場合に警告します。]** オプションに対応します。</span><span class="sxs-lookup"><span data-stu-id="0e210-112">This corresponds to the option **Warn if a subscription will expire within the threshold**.</span></span> <span data-ttu-id="0e210-113">指定したしきい値に到達するか、しきい値を超過すると、(より優先度が高い問題を表示する必要がない限り) **[まもなく期限切れ/期限切れ]** というサブスクリプション状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0e210-113">If the specified threshold is met or exceeded, the subscription status is displayed as **Expiring soon/Expired** (unless an issue with a higher priority needs to be displayed).</span></span>  
  
-   <span data-ttu-id="0e210-114">指定した同期時刻を超えた場合。</span><span class="sxs-lookup"><span data-stu-id="0e210-114">Exceeding the specified synchronization time.</span></span>  
  
     <span data-ttu-id="0e210-115">これは、オプション **[ダイヤルアップ接続のマージ長がしきい値を超えた場合に警告します。]** および **[LAN 接続のマージ長がしきい値を超えた場合に警告します。]** に対応します。</span><span class="sxs-lookup"><span data-stu-id="0e210-115">This corresponds to the options **Warn if a merge length for dialup connections exceeds the threshold** and **Warn if a merge length for LAN connections exceeds the threshold**.</span></span> <span data-ttu-id="0e210-116">これらのしきい値は両方とも設定できますが、特定の同期の実行中に使用できるのはいずれか 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="0e210-116">Both of these thresholds can be set, but only one is used during a given synchronization.</span></span> <span data-ttu-id="0e210-117">マージ エージェントは、接続の種類に基づいて適切なしきい値を適用します。</span><span class="sxs-lookup"><span data-stu-id="0e210-117">The Merge Agent applies the appropriate threshold based on the connection type.</span></span>  
  
     <span data-ttu-id="0e210-118">指定したしきい値に到達するかまたはしきい値を超過すると、(より優先度が高い問題を表示する必要がない限り) **[長期マージ]** というサブスクリプション状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0e210-118">If the specified threshold is met or exceeded, the subscription status is displayed as **Long-running merge** (unless an issue with a higher priority needs to be displayed).</span></span>  
  
-   <span data-ttu-id="0e210-119">指定した数の行を特定の時間内で処理できない場合。</span><span class="sxs-lookup"><span data-stu-id="0e210-119">Falling short of processing the specified number of rows in a given amount of time.</span></span>  
  
     <span data-ttu-id="0e210-120">これは、オプション **[ダイヤルアップ接続で 1 秒あたりにマージされる行数がしきい値未満の場合に警告します。]** および **[LAN 接続のマージ長がしきい値を超えた場合に警告します。]** に相当します。</span><span class="sxs-lookup"><span data-stu-id="0e210-120">This corresponds to the options **Warn if rows merged per second for dialup connections is less than the threshold** and **Warn if a merge length for LAN connections exceeds the threshold**.</span></span> <span data-ttu-id="0e210-121">これらのしきい値は両方とも設定できますが、特定の同期の実行中に使用できるのはいずれか 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="0e210-121">Both of these thresholds can be set, but only one is used during a given synchronization.</span></span> <span data-ttu-id="0e210-122">マージ エージェントは、接続の種類に基づいて適切なしきい値を適用します。</span><span class="sxs-lookup"><span data-stu-id="0e210-122">The Merge Agent applies the appropriate threshold based on the connection type.</span></span>  
  
     <span data-ttu-id="0e210-123">指定したしきい値に到達するか、しきい値を超過すると、(より優先度が高い問題を表示する必要がない限り) **[パフォーマンス クリティカル]** というサブスクリプション状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0e210-123">If the specified threshold is met or exceeded, the subscription status is displayed as **Performance critical** (unless an issue with a higher priority needs to be displayed).</span></span>  
  
 <span data-ttu-id="0e210-124">警告を有効にする場合は、しきい値も設定します。</span><span class="sxs-lookup"><span data-stu-id="0e210-124">When you enable a warning, you also set a threshold.</span></span> <span data-ttu-id="0e210-125">たとえば、警告 **[LAN 接続のマージ長がしきい値を超えた場合に警告します。]** を有効にした場合は、マージ同期の長さとして許容できる最大値を設定します。</span><span class="sxs-lookup"><span data-stu-id="0e210-125">For example, if you enable the warning **Warn if a merge length for LAN connections exceeds the threshold**, set the maximum allowable length of time for a merge synchronization.</span></span>  
  
 <span data-ttu-id="0e210-126">しきい値に到達した場合は、レプリケーション モニターに警告を表示でき、さらに通知を発行することができます。</span><span class="sxs-lookup"><span data-stu-id="0e210-126">In addition to displaying a warning in Replication Monitor, reaching a threshold can also trigger an alert.</span></span> <span data-ttu-id="0e210-127">通知を定義するには、 **[警告の構成]** をクリックし、 **[レプリケーションの警告の構成]** ダイアログ ボックスに情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="0e210-127">Alerts are defined by clicking **Configure Alerts** and providing information in the **Configure Replication Alerts** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0e210-128">Options</span><span class="sxs-lookup"><span data-stu-id="0e210-128">Options</span></span>  
 <span data-ttu-id="0e210-129">**有効**</span><span class="sxs-lookup"><span data-stu-id="0e210-129">**Enabled**</span></span>  
 <span data-ttu-id="0e210-130">警告を有効にする場合に選択します。その場合は、しきい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="0e210-130">Select to enable a warning and specify a threshold.</span></span>  
  
 <span data-ttu-id="0e210-131">**Alert**</span><span class="sxs-lookup"><span data-stu-id="0e210-131">**Alert**</span></span>  
 <span data-ttu-id="0e210-132">特定のレプリケーションの警告用の警告の設定を有効にする場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="0e210-132">Select to enable the alert setting for a given replication warning.</span></span>  
  
 <span data-ttu-id="0e210-133">**警告**</span><span class="sxs-lookup"><span data-stu-id="0e210-133">**Warning**</span></span>  
 <span data-ttu-id="0e210-134">しきい値に関連付けられている警告の説明です。</span><span class="sxs-lookup"><span data-stu-id="0e210-134">A description of the warning associated with a threshold.</span></span>  
  
 <span data-ttu-id="0e210-135">**しきい値**</span><span class="sxs-lookup"><span data-stu-id="0e210-135">**Threshold**</span></span>  
 <span data-ttu-id="0e210-136">しきい値の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="0e210-136">Specify a value for the threshold.</span></span>  
  
 <span data-ttu-id="0e210-137">**アラートの構成**</span><span class="sxs-lookup"><span data-stu-id="0e210-137">**Configure Alerts**</span></span>  
 <span data-ttu-id="0e210-138">**[警告]** グリッドの行を選択し、 **[警告の構成]** をクリックすると、 **[レプリケーションの警告の構成]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0e210-138">Select a row in the **Warnings** grid, and click **Configure Alerts** to launch the **Configure Replication Alerts** dialog box.</span></span> <span data-ttu-id="0e210-139">このダイアログ ボックスでは、選択したしきい値および警告に関連付けた通知を定義できます。</span><span class="sxs-lookup"><span data-stu-id="0e210-139">The dialog box allows you to define an alert, which is associated with the selected threshold and warning.</span></span>  
  
 <span data-ttu-id="0e210-140">**[変更の破棄]**</span><span class="sxs-lookup"><span data-stu-id="0e210-140">**Discard Changes**</span></span>  
 <span data-ttu-id="0e210-141">クリックすると、警告およびしきい値に対する変更が破棄されます。</span><span class="sxs-lookup"><span data-stu-id="0e210-141">Click to discard any changes to warnings and thresholds.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e210-142">**[変更の破棄]** をクリックしても、 **[レプリケーションの警告の構成]** ダイアログ ボックスに定義されている通知は影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="0e210-142">Clicking **Discard Changes** does not affect alerts defined in the **Configure Replication Alerts** dialog box.</span></span>  
  
 <span data-ttu-id="0e210-143">**[変更の保存]**</span><span class="sxs-lookup"><span data-stu-id="0e210-143">**Save Changes**</span></span>  
 <span data-ttu-id="0e210-144">クリックすると、警告およびしきい値に対する変更が保存されます。</span><span class="sxs-lookup"><span data-stu-id="0e210-144">Click to save any changes to warnings and thresholds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e210-145">参照</span><span class="sxs-lookup"><span data-stu-id="0e210-145">See Also</span></span>  
 <span data-ttu-id="0e210-146">[レプリケーションモニターを開始する](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="0e210-146">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="0e210-147">[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="0e210-147">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="0e210-148">[レプリケーションモニターを使用したパフォーマンスの監視](monitor/monitor-performance-with-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="0e210-148">[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) </span></span>  
 <span data-ttu-id="0e210-149">[レプリケーションの監視](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="0e210-149">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="0e210-150">レプリケーション モニターのしきい値と警告の設定</span><span class="sxs-lookup"><span data-stu-id="0e210-150">Set Thresholds and Warnings in Replication Monitor</span></span>](monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
  
  
