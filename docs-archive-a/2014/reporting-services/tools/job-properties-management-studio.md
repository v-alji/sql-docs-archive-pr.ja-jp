---
title: '[ジョブのプロパティ] (Management Studio) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.jobproperties.f1
ms.assetid: 807ffd0e-9363-4f8f-9c36-c5d746ad19fd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c4d309ba78a21114cf51c48f0a5c5b3b2f7c2500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716026"
---
# <a name="job-properties-management-studio"></a><span data-ttu-id="a3899-102">[ジョブのプロパティ]\(Management Studio)</span><span class="sxs-lookup"><span data-stu-id="a3899-102">Job Properties (Management Studio)</span></span>
  <span data-ttu-id="a3899-103">**[ジョブのプロパティ]** ページを使用して、進行中のレポートまたはサブスクリプションを取り消す前にそれらの情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="a3899-103">Use the **Job Properties** page to view information about an in-progress report or subscription before you cancel it.</span></span>  
  
 <span data-ttu-id="a3899-104">このページを開くには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を起動して、レポート サーバーに接続し、 **[ジョブ]** フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="a3899-104">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, and open the **Jobs** folder.</span></span> <span data-ttu-id="a3899-105">実行中のジョブを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3899-105">Right-click a job that is running, and then click **Properties**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3899-106">この機能は、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] with Advanced Services ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="a3899-106">This feature is not supported in [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] with Advanced Services.</span></span> <span data-ttu-id="a3899-107">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]を実行している場合、このページは表示されません。</span><span class="sxs-lookup"><span data-stu-id="a3899-107">The page does not appear when you are running [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="a3899-108">処理手順</span><span class="sxs-lookup"><span data-stu-id="a3899-108">Tasks</span></span>  
 <span data-ttu-id="a3899-109">ジョブに関する情報を表示する前に、ページを更新してレポート サーバーで現在実行されているジョブに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="a3899-109">Before you can view information about a job, refresh the page to retrieve information about jobs that are currently running on the report server:</span></span>  
  
1.  <span data-ttu-id="a3899-110">レポート サーバーのフォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="a3899-110">Open the report server folder.</span></span>  
  
2.  <span data-ttu-id="a3899-111">**[ジョブ]** を右クリックし、 **[更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3899-111">Right-click **Jobs**, and then click **Refresh**.</span></span>  
  
3.  <span data-ttu-id="a3899-112">ジョブが表示されたら、ジョブを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3899-112">If a job is listed, right-click the job, and then click **Properties**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a3899-113">オプション</span><span class="sxs-lookup"><span data-stu-id="a3899-113">Options</span></span>  
 <span data-ttu-id="a3899-114">**[ジョブ ID]**</span><span class="sxs-lookup"><span data-stu-id="a3899-114">**Job ID**</span></span>  
 <span data-ttu-id="a3899-115">処理中にジョブに割り当てられる GUID。</span><span class="sxs-lookup"><span data-stu-id="a3899-115">A GUID that is assigned to a job while it is processing.</span></span> <span data-ttu-id="a3899-116">この値は、レポートまたはサブスクリプションが実行されるたびにランダムに生成されます。</span><span class="sxs-lookup"><span data-stu-id="a3899-116">The value is randomly generated each time a report or subscription runs.</span></span>  
  
 <span data-ttu-id="a3899-117">**ジョブの状態**</span><span class="sxs-lookup"><span data-stu-id="a3899-117">**Job Status**</span></span>  
 <span data-ttu-id="a3899-118">有効な値は、 **[新規]** および **[実行中]** です。</span><span class="sxs-lookup"><span data-stu-id="a3899-118">Valid values are **New** and **Running**.</span></span> <span data-ttu-id="a3899-119">ジョブの開始時の状態は常に **[新規]** です。</span><span class="sxs-lookup"><span data-stu-id="a3899-119">Status is always **New** when the job begins.</span></span> <span data-ttu-id="a3899-120">60 秒後に、状態は **[実行中]** に変わります。</span><span class="sxs-lookup"><span data-stu-id="a3899-120">After 60 seconds, status changes to **Running**.</span></span> <span data-ttu-id="a3899-121">変更を確認するには、ページを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3899-121">You must refresh the page to pick up the change.</span></span>  
  
 <span data-ttu-id="a3899-122">**ジョブの種類**</span><span class="sxs-lookup"><span data-stu-id="a3899-122">**Job Type**</span></span>  
 <span data-ttu-id="a3899-123">有効な値は、 **[ユーザー]** または **[システム]** です。</span><span class="sxs-lookup"><span data-stu-id="a3899-123">Valid values are **User** and **System**.</span></span> <span data-ttu-id="a3899-124">ユーザー ジョブは、各ユーザーによって開始される任意のジョブです。</span><span class="sxs-lookup"><span data-stu-id="a3899-124">A user job is any job that is initiated by an individual user.</span></span> <span data-ttu-id="a3899-125">このジョブには、要求時のレポートの実行、レポート履歴スナップショットの手動生成、またはレポート実行スナップショットの手動作成が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a3899-125">This includes running a report on-demand, manually generating a report history snapshot, or manually creating a report execution snapshot.</span></span> <span data-ttu-id="a3899-126">実行中の標準サブスクリプションも、ユーザー ジョブです。</span><span class="sxs-lookup"><span data-stu-id="a3899-126">An in-progress standard subscription is also a user job.</span></span> <span data-ttu-id="a3899-127">システム ジョブは、レポート サーバーで開始されるジョブです。</span><span class="sxs-lookup"><span data-stu-id="a3899-127">A system job is one that is initiated by the report server.</span></span> <span data-ttu-id="a3899-128">システム ジョブには、スケジュールでトリガーされるレポートの処理が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a3899-128">System jobs include report processing that is triggered by a schedule.</span></span>  
  
 <span data-ttu-id="a3899-129">**ジョブの操作**</span><span class="sxs-lookup"><span data-stu-id="a3899-129">**Job Action**</span></span>  
 <span data-ttu-id="a3899-130">レポートの場合、この列には実行中のレポート実行処理が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3899-130">For reports, this column shows which report execution processes are underway.</span></span> <span data-ttu-id="a3899-131">この値は常に **[表示]** です。</span><span class="sxs-lookup"><span data-stu-id="a3899-131">This value is always **Render**.</span></span>  
  
 <span data-ttu-id="a3899-132">**[ジョブの説明]**</span><span class="sxs-lookup"><span data-stu-id="a3899-132">**Job Description**</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="a3899-133">では、既定ではジョブの説明は表示されません。</span><span class="sxs-lookup"><span data-stu-id="a3899-133">does not provide job descriptions by default.</span></span>  
  
 <span data-ttu-id="a3899-134">**[サーバー名]**</span><span class="sxs-lookup"><span data-stu-id="a3899-134">**Server Name**</span></span>  
 <span data-ttu-id="a3899-135">ジョブを処理しているレポート サーバーの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3899-135">Shows the name of the report server that is processing the job.</span></span> <span data-ttu-id="a3899-136">スケールアウト配置を構成している場合、この値にはジョブを処理しているサーバーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3899-136">If you configured a scale-out deployment, this value will show which server is processing the job.</span></span>  
  
 <span data-ttu-id="a3899-137">**[レポート名]**</span><span class="sxs-lookup"><span data-stu-id="a3899-137">**Report Name**</span></span>  
 <span data-ttu-id="a3899-138">レポートの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3899-138">Shows the name of the report.</span></span> <span data-ttu-id="a3899-139">サブスクリプションは、説明で識別されます。</span><span class="sxs-lookup"><span data-stu-id="a3899-139">Subscriptions are identified by their descriptions.</span></span>  
  
 <span data-ttu-id="a3899-140">**[レポートのパス]**</span><span class="sxs-lookup"><span data-stu-id="a3899-140">**Report Path**</span></span>  
 <span data-ttu-id="a3899-141">レポート サーバー フォルダー階層のレポートのパスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3899-141">Shows the path of the report in the report server folder hierarchy.</span></span>  
  
 <span data-ttu-id="a3899-142">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="a3899-142">**Start Time**</span></span>  
 <span data-ttu-id="a3899-143">処理の開始時刻が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3899-143">Shows when the process started.</span></span>  
  
 <span data-ttu-id="a3899-144">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="a3899-144">**User Name**</span></span>  
 <span data-ttu-id="a3899-145">ユーザーによって開始された処理の場合、この列には処理を開始したユーザーの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3899-145">For processes initiated by a user, this column shows the name of the user.</span></span> <span data-ttu-id="a3899-146">システム ジョブの場合は、レポート サーバーの名前になります。</span><span class="sxs-lookup"><span data-stu-id="a3899-146">For system jobs, this is the name of the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3899-147">参照</span><span class="sxs-lookup"><span data-stu-id="a3899-147">See Also</span></span>  
 <span data-ttu-id="a3899-148">[Management Studio のレポート サーバーの F1 ヘルプ](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="a3899-148">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="a3899-149">[Management Studio でレポート サーバーに接続する](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="a3899-149">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 [<span data-ttu-id="a3899-150">実行中の処理を管理する</span><span class="sxs-lookup"><span data-stu-id="a3899-150">Manage a Running Process</span></span>](../subscriptions/manage-a-running-process.md)  
  
  
