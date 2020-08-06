---
title: パブリケーション情報、[警告] (スナップショットパブリケーション、SQL Server 2005 以降) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.warningsandagents.snapshot.f1
ms.assetid: 7aa2eb52-b6b7-4dd3-8483-8ef00d9f0435
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a3ae662a339e1e211ce4f46a588f4d7de65bf5e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717906"
---
# <a name="publication-information-warnings-snapshot-publication-sql-server-2005-and-later"></a><span data-ttu-id="01305-102">パブリケーション情報、[警告] (スナップショット パブリケーション、SQL Server 2005 以降)</span><span class="sxs-lookup"><span data-stu-id="01305-102">Publication Information, Warnings (Snapshot Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="01305-103">**以降を実行しているディストリビューターでは、** [警告] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] タブを使用できます。</span><span class="sxs-lookup"><span data-stu-id="01305-103">The **Warnings** tab is available for Distributors that are running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span> <span data-ttu-id="01305-104">**[警告]** タブでは、選択されているパブリケーションに対して次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="01305-104">The **Warnings** tab allows you to perform the following tasks for the selected publication:</span></span>  
  
-   <span data-ttu-id="01305-105">警告を有効にする。</span><span class="sxs-lookup"><span data-stu-id="01305-105">Enable warnings.</span></span>  
  
-   <span data-ttu-id="01305-106">警告に関連するしきい値を指定する。</span><span class="sxs-lookup"><span data-stu-id="01305-106">Specify thresholds associated with warnings.</span></span>  
  
-   <span data-ttu-id="01305-107">警告に関連する通知を定義する。</span><span class="sxs-lookup"><span data-stu-id="01305-107">Define alerts associated with warnings.</span></span>  
  
## <a name="warnings-thresholds-and-alerts"></a><span data-ttu-id="01305-108">警告、しきい値、および通知</span><span class="sxs-lookup"><span data-stu-id="01305-108">Warnings, Thresholds, and Alerts</span></span>  
 <span data-ttu-id="01305-109">既定では、レプリケーション モニターは、初期化されていないサブスクリプションに対して警告を表示します。サブスクリプション情報を含むページの **[状態]** 列に、警告として **[初期化されていないサブスクリプション]** という状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="01305-109">By default, Replication Monitor displays warnings for uninitialized subscriptions: a status of **Uninitialized subscription** is displayed as a warning in the **Status** column of pages that include subscription information.</span></span> <span data-ttu-id="01305-110">スナップショット パブリケーションの場合は、 **[サブスクリプションの有効期限がしきい値内で切れる場合に警告します]** オプションを設定することで、サブスクリプションの有効期限が差し迫っている場合に警告を生成するように指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="01305-110">For snapshot publications, you can also specify that imminent subscription expiration results in a warning by setting the option **Warn if a subscription will expire within the threshold**.</span></span> <span data-ttu-id="01305-111">指定したしきい値に到達するか、しきい値を超過すると、(より優先度が高い問題を表示する必要がない限り) **[まもなく期限切れ/期限切れ]** というサブスクリプション状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="01305-111">If the specified threshold is met or exceeded, the subscription status is displayed as **Expiring soon/Expired** (unless an issue with a higher priority needs to be displayed).</span></span>  
  
 <span data-ttu-id="01305-112">しきい値に到達した場合は、レプリケーション モニターに警告を表示でき、さらに通知を発行することができます。</span><span class="sxs-lookup"><span data-stu-id="01305-112">In addition to displaying a warning in Replication Monitor, reaching a threshold can also trigger an alert.</span></span> <span data-ttu-id="01305-113">通知を定義するには、 **[警告の構成]** をクリックし、 **[レプリケーションの警告の構成]** ダイアログ ボックスに情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="01305-113">Alerts are defined by clicking **Configure Alerts** and providing information in the **Configure Replication Alerts** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="01305-114">オプション</span><span class="sxs-lookup"><span data-stu-id="01305-114">Options</span></span>  
 <span data-ttu-id="01305-115">**有効**</span><span class="sxs-lookup"><span data-stu-id="01305-115">**Enabled**</span></span>  
 <span data-ttu-id="01305-116">警告を有効にする場合に選択します。その場合は、しきい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="01305-116">Select to enable a warning and specify a threshold.</span></span>  
  
 <span data-ttu-id="01305-117">**警告**</span><span class="sxs-lookup"><span data-stu-id="01305-117">**Warning**</span></span>  
 <span data-ttu-id="01305-118">しきい値に関連付けられている警告の説明です。</span><span class="sxs-lookup"><span data-stu-id="01305-118">A description of the warning associated with a threshold.</span></span>  
  
 <span data-ttu-id="01305-119">**しきい値**</span><span class="sxs-lookup"><span data-stu-id="01305-119">**Threshold**</span></span>  
 <span data-ttu-id="01305-120">しきい値の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="01305-120">Specify a value for the threshold.</span></span>  
  
 <span data-ttu-id="01305-121">**[警告の構成]**</span><span class="sxs-lookup"><span data-stu-id="01305-121">**Configure Alerts**</span></span>  
 <span data-ttu-id="01305-122">**[警告]** グリッドの行を選択し、 **[警告の構成]** をクリックすると、 **[レプリケーションの警告の構成]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="01305-122">Select a row in the **Warnings** grid, and click **Configure Alerts** to launch the **Configure Replication Alerts** dialog box.</span></span> <span data-ttu-id="01305-123">このダイアログ ボックスでは、選択したしきい値および警告に関連付けた通知を定義できます。</span><span class="sxs-lookup"><span data-stu-id="01305-123">The dialog box allows you to define an alert, which is associated with the selected threshold and warning.</span></span>  
  
 <span data-ttu-id="01305-124">**[変更の破棄]**</span><span class="sxs-lookup"><span data-stu-id="01305-124">**Discard Changes**</span></span>  
 <span data-ttu-id="01305-125">クリックすると、警告およびしきい値に対する変更が破棄されます。</span><span class="sxs-lookup"><span data-stu-id="01305-125">Click to discard any changes to warnings and thresholds.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="01305-126">**[変更の破棄]** をクリックしても、 **[レプリケーションの警告の構成]** ダイアログ ボックスに定義されている通知は影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="01305-126">Clicking **Discard Changes** does not affect alerts defined in the **Configure Replication Alerts** dialog box.</span></span>  
  
 <span data-ttu-id="01305-127">**[変更の保存]**</span><span class="sxs-lookup"><span data-stu-id="01305-127">**Save Changes**</span></span>  
 <span data-ttu-id="01305-128">クリックすると、警告およびしきい値に対する変更が保存されます。</span><span class="sxs-lookup"><span data-stu-id="01305-128">Click to save any changes to warnings and thresholds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01305-129">参照</span><span class="sxs-lookup"><span data-stu-id="01305-129">See Also</span></span>  
 <span data-ttu-id="01305-130">[レプリケーション モニターの開始](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="01305-130">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="01305-131">[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="01305-131">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="01305-132">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="01305-132">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
