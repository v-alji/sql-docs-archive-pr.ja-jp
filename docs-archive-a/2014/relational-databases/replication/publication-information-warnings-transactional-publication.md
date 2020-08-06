---
title: パブリケーション情報、[警告] (トランザクションパブリケーション、SQL Server 2005 以降) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.warningsandagents.tran.f1
ms.assetid: 4d4baf1d-d0a1-4d09-bec7-137811f43f09
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cac7ab0f712fe69d3736985921d70b0ce200d474
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717841"
---
# <a name="publication-information-warnings-transactional-publication-sql-server-2005-and-later"></a><span data-ttu-id="fd192-102">パブリケーション情報、[警告] (トランザクション パブリケーション、SQL Server 2005 以降)</span><span class="sxs-lookup"><span data-stu-id="fd192-102">Publication Information, Warnings (Transactional Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="fd192-103">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降を実行しているディストリビューターでは、**[警告]** タブを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fd192-103">The **Warnings** tab is available for Distributors that are running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span> <span data-ttu-id="fd192-104">**[警告]** タブでは、選択されているパブリケーションに対して次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="fd192-104">The **Warnings** tab allows you to perform the following tasks for the selected publication:</span></span>  
  
-   <span data-ttu-id="fd192-105">レプリケーション モニターに警告を表示します。</span><span class="sxs-lookup"><span data-stu-id="fd192-105">Enable warnings to be displayed in Replication Monitor.</span></span>  
  
-   <span data-ttu-id="fd192-106">警告に関連するしきい値を指定する。</span><span class="sxs-lookup"><span data-stu-id="fd192-106">Specify thresholds associated with warnings.</span></span>  
  
-   <span data-ttu-id="fd192-107">警告に関連する通知を定義する。</span><span class="sxs-lookup"><span data-stu-id="fd192-107">Define alerts associated with warnings.</span></span>  
  
## <a name="warnings-thresholds-and-alerts"></a><span data-ttu-id="fd192-108">警告、しきい値、および通知</span><span class="sxs-lookup"><span data-stu-id="fd192-108">Warnings, Thresholds, and Alerts</span></span>  
 <span data-ttu-id="fd192-109">既定では、レプリケーション モニターは、初期化されていないサブスクリプションに対して警告を表示します。サブスクリプション情報を含むページの **[状態]** 列に、警告として **[初期化されていないサブスクリプション]** という状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fd192-109">By default, Replication Monitor displays warnings for uninitialized subscriptions: a status of **Uninitialized subscription** is displayed as a warning in the **Status** column of pages that include subscription information.</span></span> <span data-ttu-id="fd192-110">トランザクション パブリケーションの場合は、次のような追加の条件で警告を生成するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="fd192-110">For transactional publications, you can specify whether these additional conditions result in warnings:</span></span>  
  
-   <span data-ttu-id="fd192-111">差し迫ったサブスクリプションの有効期限。</span><span class="sxs-lookup"><span data-stu-id="fd192-111">Imminent subscription expiration.</span></span>  
  
     <span data-ttu-id="fd192-112">これは、 **[サブスクリプションの有効期限がしきい値内で切れる場合に警告します。]** オプションに対応します。</span><span class="sxs-lookup"><span data-stu-id="fd192-112">This corresponds to the option **Warn if a subscription will expire within the threshold**.</span></span> <span data-ttu-id="fd192-113">指定したしきい値に到達するか、しきい値を超過すると、(より優先度が高い問題を表示する必要がない限り) **[まもなく期限切れ/期限切れ]** というサブスクリプション状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fd192-113">If the specified threshold is met or exceeded, the subscription status is displayed as **Expiring soon/Expired** (unless an issue with a higher priority needs to be displayed).</span></span>  
  
-   <span data-ttu-id="fd192-114">指定した待機時間の超過。</span><span class="sxs-lookup"><span data-stu-id="fd192-114">Exceeding the specified latency.</span></span> <span data-ttu-id="fd192-115">トランザクションがパブリッシャー側でコミットされたときから、サブスクライバー側で対応するトランザクションがコミットされるまでに経過した時間です。</span><span class="sxs-lookup"><span data-stu-id="fd192-115">This is the amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber.</span></span>  
  
     <span data-ttu-id="fd192-116">これは、 **[待機時間がしきい値を超えた場合に警告します。]** オプションに対応します。</span><span class="sxs-lookup"><span data-stu-id="fd192-116">This corresponds to the option **Warn if latency exceeds the threshold**.</span></span> <span data-ttu-id="fd192-117">指定したしきい値に到達するか、しきい値を超過すると、(より優先度が高い問題を表示する必要がない限り) **[パフォーマンス クリティカル]** というサブスクリプション状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fd192-117">If the specified threshold is met or exceeded, the subscription status is displayed as **Performance critical** (unless an issue with a higher priority needs to be displayed).</span></span> <span data-ttu-id="fd192-118">しきい値は、サブスクリプション情報を含むページの **[パフォーマンス]** 列に表示されるパフォーマンス評価にも使用されます。</span><span class="sxs-lookup"><span data-stu-id="fd192-118">The threshold is also used to provide a performance rating, which is displayed in the **Performance** column of pages that include subscription information.</span></span> <span data-ttu-id="fd192-119">パフォーマンス評価は、次のいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="fd192-119">The performance rating is one of the following values:</span></span>  
  
    -   <span data-ttu-id="fd192-120">非常に良い</span><span class="sxs-lookup"><span data-stu-id="fd192-120">Excellent</span></span>  
  
    -   <span data-ttu-id="fd192-121">良い</span><span class="sxs-lookup"><span data-stu-id="fd192-121">Good</span></span>  
  
    -   <span data-ttu-id="fd192-122">普通</span><span class="sxs-lookup"><span data-stu-id="fd192-122">Fair</span></span>  
  
    -   <span data-ttu-id="fd192-123">悪い</span><span class="sxs-lookup"><span data-stu-id="fd192-123">Poor</span></span>  
  
    -   <span data-ttu-id="fd192-124">重要</span><span class="sxs-lookup"><span data-stu-id="fd192-124">Critical</span></span>  
  
 <span data-ttu-id="fd192-125">警告を有効にする場合は、しきい値も設定します。</span><span class="sxs-lookup"><span data-stu-id="fd192-125">When you enable a warning, you also set a threshold.</span></span> <span data-ttu-id="fd192-126">たとえば、 **[待機時間がしきい値を超えた場合に警告します。]** 警告を有効にした場合は、パブリッシャー側でトランザクションをコミットしたときからサブスクライバー側でトランザクションをコミットするまでに許容する時間を選択します。</span><span class="sxs-lookup"><span data-stu-id="fd192-126">For example, if you enable the warning **Warn if latency exceeds the threshold**, select the amount of time allowable between a transaction being committed at the Publisher and the transaction being committed at the Subscriber.</span></span>  
  
 <span data-ttu-id="fd192-127">しきい値に到達した場合は、レプリケーション モニターに警告を表示でき、さらに通知を発行することができます。</span><span class="sxs-lookup"><span data-stu-id="fd192-127">In addition to displaying a warning in Replication Monitor, reaching a threshold can also trigger an alert.</span></span> <span data-ttu-id="fd192-128">通知を定義するには、 **[警告の構成]** をクリックし、 **[レプリケーションの警告の構成]** ダイアログ ボックスに情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="fd192-128">Alerts are defined by clicking **Configure Alerts** and providing information in the **Configure Replication Alerts** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fd192-129">Options</span><span class="sxs-lookup"><span data-stu-id="fd192-129">Options</span></span>  
 <span data-ttu-id="fd192-130">**有効**</span><span class="sxs-lookup"><span data-stu-id="fd192-130">**Enabled**</span></span>  
 <span data-ttu-id="fd192-131">警告を有効にする場合に選択します。その場合は、しきい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd192-131">Select to enable a warning and specify a threshold.</span></span>  
  
 <span data-ttu-id="fd192-132">**警告**</span><span class="sxs-lookup"><span data-stu-id="fd192-132">**Warning**</span></span>  
 <span data-ttu-id="fd192-133">しきい値に関連付けられている警告の説明です。</span><span class="sxs-lookup"><span data-stu-id="fd192-133">A description of the warning associated with a threshold.</span></span>  
  
 <span data-ttu-id="fd192-134">**しきい値**</span><span class="sxs-lookup"><span data-stu-id="fd192-134">**Threshold**</span></span>  
 <span data-ttu-id="fd192-135">しきい値の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd192-135">Specify a value for the threshold.</span></span>  
  
 <span data-ttu-id="fd192-136">**アラートの構成**</span><span class="sxs-lookup"><span data-stu-id="fd192-136">**Configure Alerts**</span></span>  
 <span data-ttu-id="fd192-137">**[警告]** グリッドの行を選択し、 **[警告の構成]** をクリックすると、 **[レプリケーションの警告の構成]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fd192-137">Select a row in the **Warnings** grid, and click **Configure Alerts** to launch the **Configure Replication Alerts** dialog box.</span></span> <span data-ttu-id="fd192-138">このダイアログ ボックスでは、選択したしきい値および警告に関連付けた通知を定義できます。</span><span class="sxs-lookup"><span data-stu-id="fd192-138">The dialog box allows you to define an alert, which is associated with the selected threshold and warning.</span></span>  
  
 <span data-ttu-id="fd192-139">**[変更の破棄]**</span><span class="sxs-lookup"><span data-stu-id="fd192-139">**Discard Changes**</span></span>  
 <span data-ttu-id="fd192-140">クリックすると、警告およびしきい値に対する変更が破棄されます。</span><span class="sxs-lookup"><span data-stu-id="fd192-140">Click to discard any changes to warnings and thresholds.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fd192-141">**[変更の破棄]** をクリックしても、 **[レプリケーションの警告の構成]** ダイアログ ボックスに定義されている通知は影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="fd192-141">Clicking **Discard Changes** does not affect alerts defined in the **Configure Replication Alerts** dialog box.</span></span>  
  
 <span data-ttu-id="fd192-142">**[変更の保存]**</span><span class="sxs-lookup"><span data-stu-id="fd192-142">**Save Changes**</span></span>  
 <span data-ttu-id="fd192-143">クリックすると、警告およびしきい値に対する変更が保存されます。</span><span class="sxs-lookup"><span data-stu-id="fd192-143">Click to save any changes to warnings and thresholds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd192-144">参照</span><span class="sxs-lookup"><span data-stu-id="fd192-144">See Also</span></span>  
 <span data-ttu-id="fd192-145">[レプリケーションモニターを開始する](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="fd192-145">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="fd192-146">[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="fd192-146">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="fd192-147">[レプリケーションモニターを使用したパフォーマンスの監視](monitor/monitor-performance-with-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="fd192-147">[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) </span></span>  
 <span data-ttu-id="fd192-148">[レプリケーションの監視](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="fd192-148">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="fd192-149">レプリケーション モニターのしきい値と警告の設定</span><span class="sxs-lookup"><span data-stu-id="fd192-149">Set Thresholds and Warnings in Replication Monitor</span></span>](monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
  
  
