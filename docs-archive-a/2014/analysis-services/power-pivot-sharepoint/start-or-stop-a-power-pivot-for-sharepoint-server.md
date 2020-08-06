---
title: PowerPivot for SharePoint Server を開始または停止する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e38e6366-9f20-4db0-b2a8-da7d5adf00eb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 41c38f8f96fcbc9175cf0f52dafd8b28a83e5497
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641274"
---
# <a name="start-or-stop-a-powerpivot-for-sharepoint-server"></a><span data-ttu-id="f1478-102">PowerPivot for SharePoint サーバーの開始または停止</span><span class="sxs-lookup"><span data-stu-id="f1478-102">Start or Stop a PowerPivot for SharePoint Server</span></span>
  <span data-ttu-id="f1478-103">PowerPivot System サービスとインスタンスは、 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] 同じローカルアプリケーションサーバー上で連携して動作し、SharePoint ファームでの調整された要求とデータ処理をサポートします。</span><span class="sxs-lookup"><span data-stu-id="f1478-103">PowerPivot System Service and an [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] instance operate together on the same local application server to support coordinated request and data processing in a SharePoint farm.</span></span>  
  
 <span data-ttu-id="f1478-104">このトピックは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="f1478-104">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="f1478-105">サービスの依存関係</span><span class="sxs-lookup"><span data-stu-id="f1478-105">Service Dependencies</span></span>](#dependencies)  
  
 [<span data-ttu-id="f1478-106">サービスの開始または停止</span><span class="sxs-lookup"><span data-stu-id="f1478-106">Start or Stop the Services</span></span>](#startstop)  
  
 [<span data-ttu-id="f1478-107">PowerPivot サーバーの停止の影響</span><span class="sxs-lookup"><span data-stu-id="f1478-107">Effects of Stopping a PowerPivot Server</span></span>](#effects)  
  
##  <a name="service-dependencies"></a><a name="dependencies"></a><span data-ttu-id="f1478-108">サービスの依存関係</span><span class="sxs-lookup"><span data-stu-id="f1478-108">Service Dependencies</span></span>  
 <span data-ttu-id="f1478-109">PowerPivot System サービスには、同じ物理サーバーに一緒にインストールされているローカル Analysis Services サーバー インスタンスに対する依存関係があります。</span><span class="sxs-lookup"><span data-stu-id="f1478-109">The PowerPivot System Service has a dependency on the local Analysis Services server instance that is installed with it on the same physical server.</span></span> <span data-ttu-id="f1478-110">PowerPivot System サービスを停止する場合は、ローカル Analysis Services サーバー インスタンスも手動で停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1478-110">If you stop the PowerPivot System Service, you must also manually stop the local Analysis Services server instance.</span></span> <span data-ttu-id="f1478-111">一方のサービスのみが実行されている場合は、PowerPivot データの処理で要求割り当てエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f1478-111">If one service is running without the other, you will encounter request allocation errors for PowerPivot data processing.</span></span>  
  
 <span data-ttu-id="f1478-112">Analysis Services サーバーを単独で実行するのは、問題の診断またはトラブルシューティングを行う場合だけにしてください。</span><span class="sxs-lookup"><span data-stu-id="f1478-112">The Analysis Services server should only be run by itself if you are diagnosing or troubleshooting a problem.</span></span> <span data-ttu-id="f1478-113">それ以外の場合は、同じサーバーでローカルに実行される PowerPivot System サービスが必要です。</span><span class="sxs-lookup"><span data-stu-id="f1478-113">In all other cases, the server requires the PowerPivot System Service that runs locally on the same server.</span></span>  
  
##  <a name="start-or-stop-the-services"></a><a name="startstop"></a><span data-ttu-id="f1478-114">サービスの開始または停止</span><span class="sxs-lookup"><span data-stu-id="f1478-114">Start or Stop the Services</span></span>  
 <span data-ttu-id="f1478-115">PowerPivot System サービスまたは Analysis Services サーバー インスタンスを開始または停止するには、必ずサーバーの全体管理を使用します。</span><span class="sxs-lookup"><span data-stu-id="f1478-115">Always use Central Administration to start or stop the PowerPivot System Service or Analysis Services server instance.</span></span> <span data-ttu-id="f1478-116">サーバーの全体管理を使用すると、同じページからサービスの開始または停止をまとめて実行できます。</span><span class="sxs-lookup"><span data-stu-id="f1478-116">Central Administration allows you to start or stop the services together from the same page.</span></span> <span data-ttu-id="f1478-117">また、サーバーの全体管理では、実行する必要があると思われるサービスを再起動するために、 **[1 つ以上のサービスが開始または停止されています]** というタイマー ジョブが使用されます。</span><span class="sxs-lookup"><span data-stu-id="f1478-117">In addition, Central Administration uses a timer job called **One or more services have started or stopped** to restart services that it thinks should be running.</span></span> <span data-ttu-id="f1478-118">SharePoint 以外のツールを使用して PowerPivot System サービスまたは Analysis Services を停止した場合は、タイマー ジョブの実行時にサービスが再起動されます。</span><span class="sxs-lookup"><span data-stu-id="f1478-118">If you stop the PowerPivot System Service or Analysis Services using a non-SharePoint tool, the services will be restarted when the timer job runs.</span></span>  
  
 <span data-ttu-id="f1478-119">サービスの開始および停止は、物理サービス インスタンスに適用される操作です。</span><span class="sxs-lookup"><span data-stu-id="f1478-119">Starting and stopping services is an action that applies to a physical service instance.</span></span> <span data-ttu-id="f1478-120">ファーム内に追加の PowerPivot for SharePoint サーバーがある場合、ファーム内の他のサーバーは、PowerPivot データに対する要求の受け入れを続行します。</span><span class="sxs-lookup"><span data-stu-id="f1478-120">If you have additional PowerPivot for SharePoint servers in the farm, the other servers within the farm will continue to accept requests for PowerPivot data.</span></span>  
  
 <span data-ttu-id="f1478-121">ファーム全体のすべての物理サービスを同時に開始または停止することはできません。</span><span class="sxs-lookup"><span data-stu-id="f1478-121">You cannot start or stop all physical services simultaneously across the farm.</span></span> <span data-ttu-id="f1478-122">各サーバーを選択してから、特定のサービスを開始または停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1478-122">You must select each server and then start or stop a particular service.</span></span>  
  
 <span data-ttu-id="f1478-123">特定の Web アプリケーションに対する PowerPivot System サービスを開始、一時停止、または停止することはできませんが、サービスを既定の接続リストから削除して使用できない状態にすることができます。</span><span class="sxs-lookup"><span data-stu-id="f1478-123">You cannot start, pause, or stop a PowerPivot System Service for a specific Web application, but you can remove a service from the default connection list to make it unavailable.</span></span> <span data-ttu-id="f1478-124">詳細については、「[サーバーの全体管理で PowerPivot サービスアプリケーションを SharePoint Web アプリケーションに接続する](connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1478-124">For more information, see [Connect a PowerPivot Service Application to a SharePoint Web Application in Central Administration](connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md).</span></span>  
  
1.  <span data-ttu-id="f1478-125">サーバーの全体管理で、 **[システム設定]** の **[サーバーのサービスの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1478-125">In Central Administration, in **System Settings**, click **Manage services on server**.</span></span>  
  
2.  <span data-ttu-id="f1478-126">ページの上部にある [サーバー] の下矢印をクリックし、 **[サーバーの変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1478-126">At the top of the page, in Server, click the down arrow, and then click **Change Server**.</span></span>  
  
3.  <span data-ttu-id="f1478-127">開始または停止する PowerPivot System サービスまたは [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] インスタンスがある SharePoint サーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="f1478-127">Select the SharePoint server that has the PowerPivot System Service or [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] instance that you want to start or stop.</span></span>  
  
4.  <span data-ttu-id="f1478-128">サービスを選択し、アクションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1478-128">Select the service, and then click the action.</span></span> <span data-ttu-id="f1478-129">サービスはペアで開始または停止することを忘れないでください。</span><span class="sxs-lookup"><span data-stu-id="f1478-129">Remember to start or stop the services as a pair.</span></span> <span data-ttu-id="f1478-130">PowerPivot System サービスを開始または停止する場合は、同じコンピューターで実行される Analysis Services サーバー インスタンスも開始または停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1478-130">If you start or stop the PowerPivot System Service, be sure to also start or stop the Analysis Services server instance that runs on the same computer.</span></span>  
  
##  <a name="effects-of-stopping-a-powerpivot-server"></a><a name="effects"></a><span data-ttu-id="f1478-131">PowerPivot サーバーを停止した場合の影響</span><span class="sxs-lookup"><span data-stu-id="f1478-131">Effects of Stopping a PowerPivot Server</span></span>  
 <span data-ttu-id="f1478-132">次の表に、SharePoint サーバーでの PowerPivot System サービスおよび Analysis Services サービスの停止の影響を示します。</span><span class="sxs-lookup"><span data-stu-id="f1478-132">The following table describes the effects of stopping the PowerPivot System Service and Analysis Services service on a SharePoint server.</span></span>  
  
|<span data-ttu-id="f1478-133">影響を受ける対象</span><span class="sxs-lookup"><span data-stu-id="f1478-133">Effect on</span></span>|<span data-ttu-id="f1478-134">説明</span><span class="sxs-lookup"><span data-stu-id="f1478-134">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f1478-135">既存のクエリ</span><span class="sxs-lookup"><span data-stu-id="f1478-135">Existing queries</span></span>|<span data-ttu-id="f1478-136">Analysis Services サーバーで処理されているクエリは直ちに停止します。</span><span class="sxs-lookup"><span data-stu-id="f1478-136">Queries that are in progress on an Analysis Services server will stop immediately.</span></span> <span data-ttu-id="f1478-137">ユーザーは、データまたはデータ ソース接続が見つからないことを示すエラーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="f1478-137">The user will get a data not found or data source connection not found error.</span></span>|  
|<span data-ttu-id="f1478-138">現在処理中の既存のデータ更新ジョブ</span><span class="sxs-lookup"><span data-stu-id="f1478-138">Existing data refresh jobs that are currently processing</span></span>|<span data-ttu-id="f1478-139">現在の Analysis Services サーバーで処理されているジョブは直ちに停止します。</span><span class="sxs-lookup"><span data-stu-id="f1478-139">Jobs that are in progress on the current Analysis Services server will stop immediately.</span></span> <span data-ttu-id="f1478-140">データ更新が失敗し、データ更新の履歴にエラーが記録されます。</span><span class="sxs-lookup"><span data-stu-id="f1478-140">Data refresh will fail and an error will be logged to data refresh history.</span></span><br /><br /> <span data-ttu-id="f1478-141">SharePoint サーバーの全体管理の [ジョブの状態の確認] ページを使用することにより、サービスを停止する前に現在のジョブの状態を表示できます。</span><span class="sxs-lookup"><span data-stu-id="f1478-141">You can view the status of current jobs before you stop the service by using the Check job status page in SharePoint Central Administration.</span></span><br /><br /> <span data-ttu-id="f1478-142">現在処理中のジョブを確認することはできますが、キュー自体を表示して、他のジョブが開始されようとしているかどうかを確認することはできません。</span><span class="sxs-lookup"><span data-stu-id="f1478-142">While it is possible to know which jobs are currently processing, there is no way to view the queue itself to see whether other jobs are about to start.</span></span>|  
|<span data-ttu-id="f1478-143">キュー内の既存のデータ更新要求</span><span class="sxs-lookup"><span data-stu-id="f1478-143">Existing data refresh requests in the queue</span></span>|<span data-ttu-id="f1478-144">スケジュール設定されたデータ更新要求は、スケジュールのサイクル全体にわたって処理キューに残ります (つまり、次の開始時間までキューに残ります)。</span><span class="sxs-lookup"><span data-stu-id="f1478-144">Scheduled data refresh requests will remain in the processing queue for a complete cycle of the schedule (that is, it stays in the queue until the next start time).</span></span> <span data-ttu-id="f1478-145">PowerPivot System サービスがそのときまでに再起動されなかった場合、データ更新要求は削除され、エラーがログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="f1478-145">If the PowerPivot System Service is not restarted by then, the data refresh request will be dropped and an error will be logged.</span></span>|  
|<span data-ttu-id="f1478-146">新しいクエリ要求またはデータ更新要求</span><span class="sxs-lookup"><span data-stu-id="f1478-146">New requests for queries or data refresh</span></span>|<span data-ttu-id="f1478-147">ファーム内の PowerPivot for SharePoint サーバーのみを停止した場合、PowerPivot データに対する新しい要求は処理されません。データを要求すると、データが見つからないことを示すエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f1478-147">If you are stopping the only PowerPivot for SharePoint server in the farm, new requests for PowerPivot data will not be handled and a request for data will result in a data not found error.</span></span><br /><br /> <span data-ttu-id="f1478-148">ファーム内に追加の PowerPivot for SharePoint サーバーがある場合、要求は使用可能なサーバーのうちの 1 つに送信されます。</span><span class="sxs-lookup"><span data-stu-id="f1478-148">If you have additional PowerPivot for SharePoint servers, the request will go to one of the available servers.</span></span>|  
|<span data-ttu-id="f1478-149">使用状況データ</span><span class="sxs-lookup"><span data-stu-id="f1478-149">Usage data</span></span>|<span data-ttu-id="f1478-150">使用状況データは、サービスの停止中は収集されません。</span><span class="sxs-lookup"><span data-stu-id="f1478-150">Usage data will not be collected while the services are stopped.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1478-151">参照</span><span class="sxs-lookup"><span data-stu-id="f1478-151">See Also</span></span>  
 [<span data-ttu-id="f1478-152">PowerPivot サービス アカウントの構成</span><span class="sxs-lookup"><span data-stu-id="f1478-152">Configure PowerPivot Service Accounts</span></span>](configure-power-pivot-service-accounts.md)  
  
  