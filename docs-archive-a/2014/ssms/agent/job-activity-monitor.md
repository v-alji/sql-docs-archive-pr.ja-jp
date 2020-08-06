---
title: '[ジョブの利用状況モニター] | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.ACTIVITYMON.F1
- sql12.ag.jobactivitymonitor.alljobs.f1
ms.assetid: 11f2182c-5f71-46f8-8d2b-74f0fc48f2d6
author: stevestein
ms.author: sstein
ms.openlocfilehash: f6f89d5448f0885c85229c2808ee6f85bf6fa071
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715034"
---
# <a name="job-activity-monitor"></a><span data-ttu-id="04225-102">[ジョブの利用状況モニター]</span><span class="sxs-lookup"><span data-stu-id="04225-102">Job Activity Monitor</span></span>
  <span data-ttu-id="04225-103">このページでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブの現在の利用状況を参照できます。</span><span class="sxs-lookup"><span data-stu-id="04225-103">Use this page to view the current activity of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span> <span data-ttu-id="04225-104">**[フィルター]** をクリックすると、表示されるジョブが限定されます。</span><span class="sxs-lookup"><span data-stu-id="04225-104">Click **Filter** to limit the jobs displayed.</span></span> <span data-ttu-id="04225-105">**[エージェント ジョブの利用状況]** グリッドは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="04225-105">The **Agent Job Activity** grid is read-only.</span></span> <span data-ttu-id="04225-106">列ヘッダーをクリックすると、グリッドが並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="04225-106">Click on the column headers to sort the grid.</span></span> <span data-ttu-id="04225-107">ジョブを変更するには、ジョブをダブルクリックして **[ジョブのプロパティ]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="04225-107">To modify a job, double-click the job to open the **Job Properties** dialog box.</span></span> <span data-ttu-id="04225-108">グリッドでジョブを右クリックして表示されるメニューから、すべてのジョブ ステップの実行の開始、特定のジョブ ステップの実行、ジョブの無効化または有効化、ジョブの更新、ジョブの削除、ジョブの履歴の表示、ジョブのプロパティの表示ができます。</span><span class="sxs-lookup"><span data-stu-id="04225-108">Right-click a job in the grid to start it running all job steps, start at a particular job step, disable or enable the job, refresh the job, delete the job, view the history of the job, or view the properties of the job.</span></span> <span data-ttu-id="04225-109">**[最新の情報に更新]** をクリックすると、グリッドが現在の情報で更新されます。</span><span class="sxs-lookup"><span data-stu-id="04225-109">Click **Refresh** to update the grid with current information.</span></span>  
  
## <a name="options"></a><span data-ttu-id="04225-110">Options</span><span class="sxs-lookup"><span data-stu-id="04225-110">Options</span></span>  
 <span data-ttu-id="04225-111">**名前**</span><span class="sxs-lookup"><span data-stu-id="04225-111">**Name**</span></span>  
 <span data-ttu-id="04225-112">ジョブの名前。</span><span class="sxs-lookup"><span data-stu-id="04225-112">Name of the job.</span></span>  
  
 <span data-ttu-id="04225-113">**有効**</span><span class="sxs-lookup"><span data-stu-id="04225-113">**Enabled**</span></span>  
 <span data-ttu-id="04225-114">ジョブが有効 (**[はい]**) か無効 (**[いいえ]**) かを示します。</span><span class="sxs-lookup"><span data-stu-id="04225-114">Whether the job is enabled (**yes**) or not enabled (**no**).</span></span>  
  
 <span data-ttu-id="04225-115">**状態** <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="04225-115">**Status** <sup>1</sup></span></span>  
 <span data-ttu-id="04225-116">ジョブの現在の状態です。</span><span class="sxs-lookup"><span data-stu-id="04225-116">Current status of the job.</span></span>  
  
 <span data-ttu-id="04225-117">**[最終実行の結果]**</span><span class="sxs-lookup"><span data-stu-id="04225-117">**Last Run Outcome**</span></span>  
 <span data-ttu-id="04225-118">最終実行時のジョブの状態です。</span><span class="sxs-lookup"><span data-stu-id="04225-118">Job status when last run.</span></span>  
  
 <span data-ttu-id="04225-119">**[最終実行]**</span><span class="sxs-lookup"><span data-stu-id="04225-119">**Last Run**</span></span>  
 <span data-ttu-id="04225-120">サーバーのローカル時刻に基づき、ジョブが最後に実行された日付と時刻を示します。</span><span class="sxs-lookup"><span data-stu-id="04225-120">Date and time job was last run using the local date and time of the server.</span></span>  
  
 <span data-ttu-id="04225-121">**次の実行** <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="04225-121">**Next Run** <sup>1</sup></span></span>  
 <span data-ttu-id="04225-122">サーバーのローカル時刻に基づき、ジョブが次に実行される予定の日付と時刻を示します。</span><span class="sxs-lookup"><span data-stu-id="04225-122">Date and time the job is next scheduled to run using the local date and time of the server.</span></span>  
  
 <span data-ttu-id="04225-123">**カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="04225-123">**Category**</span></span>  
 <span data-ttu-id="04225-124">ジョブに割り当てられているジョブ カテゴリです。</span><span class="sxs-lookup"><span data-stu-id="04225-124">The job category assigned to the job.</span></span>  
  
 <span data-ttu-id="04225-125">**可**</span><span class="sxs-lookup"><span data-stu-id="04225-125">**Runnable**</span></span>  
 <span data-ttu-id="04225-126">ジョブを実行できる場合は **[はい]** 、実行できない場合は **[いいえ]** になります。</span><span class="sxs-lookup"><span data-stu-id="04225-126">**Yes** if the job can be run; **No** if the job cannot be run.</span></span> <span data-ttu-id="04225-127">ステップがないジョブおよびターゲット サーバーがないジョブは実行できません。</span><span class="sxs-lookup"><span data-stu-id="04225-127">A job is not runnable if it has no steps or if it has no target server.</span></span>  
  
 <span data-ttu-id="04225-128">**スケジュール**</span><span class="sxs-lookup"><span data-stu-id="04225-128">**Scheduled**</span></span>  
 <span data-ttu-id="04225-129">ジョブがジョブ スケジュールに割り当てられている場合は **[はい]** 、ジョブにスケジュールがない場合は **[いいえ]** になります。</span><span class="sxs-lookup"><span data-stu-id="04225-129">**Yes** if the job is assigned to a job schedule; **No** if the job has no schedule.</span></span>  
  
 <span data-ttu-id="04225-130"><sup>1</sup>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Sysadmin 固定サーバーロールおよび server administrators グループのメンバーだけが、この列の値を表示できます。</span><span class="sxs-lookup"><span data-stu-id="04225-130"><sup>1</sup>Only members of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sysadmin fixed server role and the server administrators group can see values in this column.</span></span> <span data-ttu-id="04225-131">SQLAgentOperatorRole ロールのメンバーはこの列の値を表示できません。</span><span class="sxs-lookup"><span data-stu-id="04225-131">Members of the SQLAgentOperatorRole role cannot see values in this column.</span></span>  
  
#### <a name="to-open-the-job-activity-monitor"></a><span data-ttu-id="04225-132">[ジョブの利用状況モニター] を開くには</span><span class="sxs-lookup"><span data-stu-id="04225-132">To open the Job Activity Monitor</span></span>  
  
-   <span data-ttu-id="04225-133">**オブジェクト エクスプローラー**で、サーバーを展開して **[SQL Server エージェント]** を展開し、 **[ジョブの利用状況モニター]** を右クリックした後、 **[ジョブの利用状況の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04225-133">In **Object Explorer**, expand your server, expand **SQL Server Agent**, right-click **Job Activity Monitor**, and then click **View Job Activity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04225-134">参照</span><span class="sxs-lookup"><span data-stu-id="04225-134">See Also</span></span>  
 [<span data-ttu-id="04225-135">ジョブの利用状況の監視</span><span class="sxs-lookup"><span data-stu-id="04225-135">Monitor Job Activity</span></span>](monitor-job-activity.md)  
  
  
