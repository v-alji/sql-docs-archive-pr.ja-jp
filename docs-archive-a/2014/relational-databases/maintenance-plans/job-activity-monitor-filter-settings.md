---
title: '[ジョブの利用状況モニター] ([フィルターの設定]) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.jobactivitymon.filter.f1
ms.assetid: 89cb0055-5262-447f-8464-7203d4caba78
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: feba7b992d5d1d375b93df12135487a092792ee1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643314"
---
# <a name="job-activity-monitor-filter-settings"></a><span data-ttu-id="9a99a-102">[ジョブの利用状況モニター] ([フィルターの設定])</span><span class="sxs-lookup"><span data-stu-id="9a99a-102">Job Activity Monitor (Filter Settings)</span></span>
  <span data-ttu-id="9a99a-103">このページを使用すると、ジョブの利用状況モニターに表示される行数を削減できます。</span><span class="sxs-lookup"><span data-stu-id="9a99a-103">Use this page to reduce the number of rows visible in the Job Activity Monitor.</span></span> <span data-ttu-id="9a99a-104">1 つまたは複数の利用可能なボックスに基準を入力すると、指定した値に一致する行のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9a99a-104">Enter criteria in one or several of the available boxes, to show only the rows that meet the specified values.</span></span> <span data-ttu-id="9a99a-105">一部のボックス ( **[状態]** や **[ブロッキングの種類]** ) は指定できる有効な値が決まっており、ドロップダウン リストによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="9a99a-105">Some of the boxes, such as **Status** or **Blocking Type** offer a finite number of possible values, provided by a drop-down list.</span></span> <span data-ttu-id="9a99a-106">他のボックス ( **[アプリケーション]** など) は、任意の値をコンマ区切りのリストにして必要な数だけ入力できます。</span><span class="sxs-lookup"><span data-stu-id="9a99a-106">Others, such as **Application,** allow you to enter whatever value and as many values as you wish, as a comma separated list.</span></span> <span data-ttu-id="9a99a-107">ツール バーのアイコンを使用すると、利用可能なボックスをカテゴリ別またはアルファベット順に並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="9a99a-107">Toolbar icons allow you to sort the available boxes by category or alphabetically.</span></span> <span data-ttu-id="9a99a-108">基準をクリックすると、それぞれの簡単な説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9a99a-108">Click the criteria to show a short description of the each one.</span></span>  
  
 <span data-ttu-id="9a99a-109">ジョブの利用状況モニターをフィルタリングするには、必要な数のフィルター基準を指定し、 **[フィルターの適用]** をクリックしてから **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a99a-109">To filter the Job Activity Monitor, provide as many filter criteria as you want, click **Apply filter**, and then click **OK**.</span></span>  
  
## <a name="all-jobs"></a><span data-ttu-id="9a99a-110">すべてのジョブ</span><span class="sxs-lookup"><span data-stu-id="9a99a-110">All Jobs</span></span>  
 <span data-ttu-id="9a99a-111">このフィルター基準のグループは、ジョブの利用状況モニターをフィルタリングする場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="9a99a-111">This group of filter criteria is available when filtering the Job Activity Monitor.</span></span>  
  
 <span data-ttu-id="9a99a-112">**Name**</span><span class="sxs-lookup"><span data-stu-id="9a99a-112">**Name**</span></span>  
 <span data-ttu-id="9a99a-113">ジョブを名前でフィルタリングします。</span><span class="sxs-lookup"><span data-stu-id="9a99a-113">Filter jobs by name.</span></span>  
  
 <span data-ttu-id="9a99a-114">**[次の実行]**</span><span class="sxs-lookup"><span data-stu-id="9a99a-114">**Next Run**</span></span>  
 <span data-ttu-id="9a99a-115">次に実行するスケジュールの日付でフィルタリングします。</span><span class="sxs-lookup"><span data-stu-id="9a99a-115">Filter by the date next scheduled to run.</span></span>  
  
 <span data-ttu-id="9a99a-116">**実行可能**</span><span class="sxs-lookup"><span data-stu-id="9a99a-116">**Runnable**</span></span>  
 <span data-ttu-id="9a99a-117">実行できるジョブまたは実行できないジョブを表示します。</span><span class="sxs-lookup"><span data-stu-id="9a99a-117">View jobs that can be run, or jobs that cannot be run.</span></span> <span data-ttu-id="9a99a-118">実行できるジョブだけを表示するには **[はい]** を、実行できないジョブだけを表示するには **[いいえ]** を選択します。実行できるジョブと実行できないジョブの両方を表示するには、 **[すべて]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9a99a-118">Select **Yes** to view only jobs that can be run, select **No** to view only jobs that cannot be run, or select **All** to view both jobs that can be run and those that cannot.</span></span>  
  
 <span data-ttu-id="9a99a-119">**[最終実行]**</span><span class="sxs-lookup"><span data-stu-id="9a99a-119">**Last Run**</span></span>  
 <span data-ttu-id="9a99a-120">最終実行の日付でフィルタリングします。</span><span class="sxs-lookup"><span data-stu-id="9a99a-120">Filter by the date last run.</span></span>  
  
 <span data-ttu-id="9a99a-121">**[最終実行の結果]**</span><span class="sxs-lookup"><span data-stu-id="9a99a-121">**Last Run Outcome**</span></span>  
 <span data-ttu-id="9a99a-122">ジョブが最後に実行されたときの状態でフィルタリングします。</span><span class="sxs-lookup"><span data-stu-id="9a99a-122">Filter jobs by the status last time the jobs were run.</span></span>  
  
 <span data-ttu-id="9a99a-123">**有効**</span><span class="sxs-lookup"><span data-stu-id="9a99a-123">**Enabled**</span></span>  
 <span data-ttu-id="9a99a-124">有効なジョブだけ、または無効なジョブだけを表示します。</span><span class="sxs-lookup"><span data-stu-id="9a99a-124">View only enabled or not enabled jobs</span></span>  
  
 <span data-ttu-id="9a99a-125">**カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="9a99a-125">**Category**</span></span>  
 <span data-ttu-id="9a99a-126">ジョブ カテゴリでジョブをフィルタリングします。</span><span class="sxs-lookup"><span data-stu-id="9a99a-126">Filter jobs by the job category.</span></span>  
  
 <span data-ttu-id="9a99a-127">**[スケジュール]**</span><span class="sxs-lookup"><span data-stu-id="9a99a-127">**Scheduled**</span></span>  
 <span data-ttu-id="9a99a-128">スケジュールを使用するジョブ、またはスケジュールを使用しないジョブをすべて表示します。</span><span class="sxs-lookup"><span data-stu-id="9a99a-128">View all jobs with schedules, or without schedules.</span></span>  
  
 <span data-ttu-id="9a99a-129">**状態**</span><span class="sxs-lookup"><span data-stu-id="9a99a-129">**Status**</span></span>  
 <span data-ttu-id="9a99a-130">状態でジョブをフィルタリングします。</span><span class="sxs-lookup"><span data-stu-id="9a99a-130">Filter jobs by the status.</span></span>  
  
## <a name="description-area"></a><span data-ttu-id="9a99a-131">説明領域</span><span class="sxs-lookup"><span data-stu-id="9a99a-131">Description Area</span></span>  
 <span data-ttu-id="9a99a-132">**説明ボックス**</span><span class="sxs-lookup"><span data-stu-id="9a99a-132">**Description Box**</span></span>  
 <span data-ttu-id="9a99a-133">基準を選択すると、この名前の付いていないボックスに簡単な説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9a99a-133">This unnamed box provides a short description of the criteria as they are selected.</span></span>  
  
 <span data-ttu-id="9a99a-134">**[フィルターの適用]**</span><span class="sxs-lookup"><span data-stu-id="9a99a-134">**Apply filter**</span></span>  
 <span data-ttu-id="9a99a-135">フィルターを適用するには、[**フィルターの適用**] をクリックし、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a99a-135">To apply the filter, click **Apply filter** and then click **OK**.</span></span> <span data-ttu-id="9a99a-136">フィルターの設定を [フィルターの**設定**] ダイアログボックスで保持し、適用しない場合は、[**フィルターの適用**] をオフにし、[ **OK**] をクリックしてすべての行を表示します。</span><span class="sxs-lookup"><span data-stu-id="9a99a-136">To retain the filter settings in the **Filter Settings** dialog box, but not apply them, uncheck **Apply filter**, and then click **OK**, to display all rows.</span></span>  
  
 <span data-ttu-id="9a99a-137">**Clear**</span><span class="sxs-lookup"><span data-stu-id="9a99a-137">**Clear**</span></span>  
 <span data-ttu-id="9a99a-138">フィルター設定を既定の設定に戻します。</span><span class="sxs-lookup"><span data-stu-id="9a99a-138">Returns the filter settings back to the default settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a99a-139">参照</span><span class="sxs-lookup"><span data-stu-id="9a99a-139">See Also</span></span>  
 [<span data-ttu-id="9a99a-140">ジョブの利用状況の監視</span><span class="sxs-lookup"><span data-stu-id="9a99a-140">Monitor Job Activity</span></span>](../../ssms/agent/monitor-job-activity.md)  
  
  
