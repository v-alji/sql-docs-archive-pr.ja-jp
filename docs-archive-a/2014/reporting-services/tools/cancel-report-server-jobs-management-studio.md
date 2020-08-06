---
title: '[レポート サーバー ジョブのキャンセル] (Management Studio) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.cancelreportserverjobs.f1
ms.assetid: 1c5b4975-49e9-4d0b-b298-2638e81edbfd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0ef8ada32aab4ac368871da711d0fe63fff7620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737909"
---
# <a name="cancel-report-server-jobs-management-studio"></a><span data-ttu-id="1c339-102">[レポート サーバー ジョブのキャンセル] (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="1c339-102">Cancel Report Server Jobs (Management Studio)</span></span>
  <span data-ttu-id="1c339-103">実行中のレポートの表示や実行のキャンセルを行うには、 **[レポート サーバー ジョブのキャンセル]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="1c339-103">Use the **Cancel Report Server Jobs** dialog box to view or cancel in-progress reports.</span></span> <span data-ttu-id="1c339-104">このダイアログ ボックスには、レポート サーバーで現在実行中のすべてのジョブが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1c339-104">This dialog box shows all jobs that are currently running on the report server.</span></span> <span data-ttu-id="1c339-105">現在処理中のジョブを一時停止または再開することはできませんが、すべてのジョブ、または時間がかかりすぎて完了できない場合は個々のジョブをキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="1c339-105">Although you cannot pause or restart jobs that are currently processing, you can cancel all jobs or individual jobs if they are taking too long to complete.</span></span>  
  
 <span data-ttu-id="1c339-106">ユーザー ジョブとシステム ジョブをキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="1c339-106">You can cancel user jobs and system jobs.</span></span>  
  
-   <span data-ttu-id="1c339-107">ユーザー ジョブは、各ユーザーによって開始される任意のジョブです。</span><span class="sxs-lookup"><span data-stu-id="1c339-107">A user job is any job that is initiated by an individual user.</span></span> <span data-ttu-id="1c339-108">このジョブには、要求時のレポートの実行、レポート履歴スナップショットの手動作成、またはレポート実行スナップショットの手動作成が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1c339-108">This includes running a report on-demand, manually creating a report history snapshot, or manually creating report execution snapshot.</span></span> <span data-ttu-id="1c339-109">実行中の標準サブスクリプションも、ユーザー ジョブです。</span><span class="sxs-lookup"><span data-stu-id="1c339-109">An in-progress standard subscription is also a user job.</span></span>  
  
-   <span data-ttu-id="1c339-110">システム ジョブは、レポート サーバーで開始されるジョブです。</span><span class="sxs-lookup"><span data-stu-id="1c339-110">A system job is one that is initiated by the report server.</span></span> <span data-ttu-id="1c339-111">システム ジョブには、スケジュールされたレポート処理が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1c339-111">System jobs include scheduled report processing.</span></span>  
  
 <span data-ttu-id="1c339-112">このページを開くには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を起動してレポート サーバーに接続し、 **[ジョブ]** を右クリックして **[すべてのジョブのキャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c339-112">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, right-click **Jobs**, and then click **Cancel All Jobs**.</span></span> <span data-ttu-id="1c339-113">または、 **[ジョブ]** を開き、レポート サーバーで実行中のジョブを右クリックして、 **[ジョブのキャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c339-113">You can also open **Jobs**, right-click a job that is running on the report server, and select **Cancel Job(s)**.</span></span>  
  
 <span data-ttu-id="1c339-114">ジョブを取り消す前に、そのプロパティを表示し、ジョブがいつ開始されたかを確認します。</span><span class="sxs-lookup"><span data-stu-id="1c339-114">Before cancelling a job, you can view its properties to determine when the job started.</span></span> <span data-ttu-id="1c339-115">詳細については、「[ジョブのプロパティ &#40;Management Studio&#41;](job-properties-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c339-115">For more information, see [Job Properties &#40;Management Studio&#41;](job-properties-management-studio.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1c339-116">この機能は、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] with Advanced Services ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="1c339-116">This feature is not supported in [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] with Advanced Services.</span></span> <span data-ttu-id="1c339-117">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]を実行している場合、このページは表示されません。</span><span class="sxs-lookup"><span data-stu-id="1c339-117">The page does not appear when you are running [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="1c339-118">オプション</span><span class="sxs-lookup"><span data-stu-id="1c339-118">Options</span></span>  
 <span data-ttu-id="1c339-119">**Name**</span><span class="sxs-lookup"><span data-stu-id="1c339-119">**Name**</span></span>  
 <span data-ttu-id="1c339-120">レポートの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1c339-120">Shows the name of the report.</span></span> <span data-ttu-id="1c339-121">サブスクリプションは、説明で識別されます。</span><span class="sxs-lookup"><span data-stu-id="1c339-121">Subscriptions are identified by their descriptions.</span></span>  
  
 <span data-ttu-id="1c339-122">**Type**</span><span class="sxs-lookup"><span data-stu-id="1c339-122">**Type**</span></span>  
 <span data-ttu-id="1c339-123">有効な値は、 **[ユーザー]** または **[システム]** です。</span><span class="sxs-lookup"><span data-stu-id="1c339-123">Valid values are **User** and **System**.</span></span>  
  
 <span data-ttu-id="1c339-124">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="1c339-124">**Start Time**</span></span>  
 <span data-ttu-id="1c339-125">ジョブの開始時刻が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1c339-125">Shows when the job started.</span></span>  
  
 <span data-ttu-id="1c339-126">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="1c339-126">**User Name**</span></span>  
 <span data-ttu-id="1c339-127">ユーザーによって開始されたジョブの場合、この列には処理を開始したユーザーの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1c339-127">For jobs that are initiated by a user, this column shows the name of the user.</span></span>  
  
 <span data-ttu-id="1c339-128">**状態**</span><span class="sxs-lookup"><span data-stu-id="1c339-128">**Status**</span></span>  
 <span data-ttu-id="1c339-129">ジョブの状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1c339-129">Shows the status of the job.</span></span> <span data-ttu-id="1c339-130">有効な値は、 **[新規]** および **[実行中]** です。</span><span class="sxs-lookup"><span data-stu-id="1c339-130">Valid values are **New** and **Running**.</span></span> <span data-ttu-id="1c339-131">ジョブの開始時の状態は常に **[新規]** です。</span><span class="sxs-lookup"><span data-stu-id="1c339-131">Status is always **New** when the job begins.</span></span> <span data-ttu-id="1c339-132">60 秒後に、状態は **[実行中]** に変わります。</span><span class="sxs-lookup"><span data-stu-id="1c339-132">After 60 seconds, status changes to **Running**.</span></span> <span data-ttu-id="1c339-133">変更を確認するには、ページを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c339-133">You must refresh the page to pick up the change.</span></span>  
  
 <span data-ttu-id="1c339-134">**[OK]**</span><span class="sxs-lookup"><span data-stu-id="1c339-134">**OK**</span></span>  
 <span data-ttu-id="1c339-135">1 つのジョブまたは複数のジョブを取り消します。</span><span class="sxs-lookup"><span data-stu-id="1c339-135">Cancel a single job or multiple jobs.</span></span> <span data-ttu-id="1c339-136">ジョブはすぐに取り消され、再開することはできません。</span><span class="sxs-lookup"><span data-stu-id="1c339-136">The jobs are cancelled immediately and cannot be resumed.</span></span> <span data-ttu-id="1c339-137">誤ってジョブを取り消した場合は、レポートまたはサブスクリプションを再度要求して新しいジョブを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c339-137">If you mistakenly cancel a job, you must request the report or subscription again to start a new job.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c339-138">参照</span><span class="sxs-lookup"><span data-stu-id="1c339-138">See Also</span></span>  
 <span data-ttu-id="1c339-139">[Management Studio のレポート サーバーの F1 ヘルプ](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="1c339-139">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="1c339-140">[Management Studio でレポート サーバーに接続する](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="1c339-140">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 [<span data-ttu-id="1c339-141">実行中の処理を管理する</span><span class="sxs-lookup"><span data-stu-id="1c339-141">Manage a Running Process</span></span>](../subscriptions/manage-a-running-process.md)  
  
  
