---
title: イベントの管理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- event forwarding servers [SQL Server]
- events [SQL Server], forwarding
- event-triggered jobs [SQL Server]
- forwarding events [SQL Server]
- alerts [SQL Server], forwarded events
- alerts [SQL Server], management servers
- SQL Server Agent alerts, management servers
ms.assetid: 8f4ee7f5-80df-49fd-b2b8-d020e04b6e1b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7ca6d56440b06d285cbb90f8d92325d59a452c16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711578"
---
# <a name="manage-events"></a><span data-ttu-id="af4db-102">イベントの管理</span><span class="sxs-lookup"><span data-stu-id="af4db-102">Manage Events</span></span>
  <span data-ttu-id="af4db-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスには、特定のエラー重大度レベル以上のあらゆるイベント メッセージを転送できます。</span><span class="sxs-lookup"><span data-stu-id="af4db-103">You can forward to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] all event messages that meet or exceed a specific error severity level.</span></span> <span data-ttu-id="af4db-104">この処理を *イベントの転送*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="af4db-104">This is called *event forwarding*.</span></span> <span data-ttu-id="af4db-105">転送先サーバーは、マスター サーバーにもなる専用のサーバーです。</span><span class="sxs-lookup"><span data-stu-id="af4db-105">The forwarding server is a dedicated server that can also be a master server.</span></span> <span data-ttu-id="af4db-106">イベントの転送を使用して、サーバーのグループに対する警告を集中管理できます。その結果、使用頻度の高いサーバーの負荷を減少させることができます。</span><span class="sxs-lookup"><span data-stu-id="af4db-106">You can use event forwarding to centralize alert management for a group of servers, thereby reducing the workload on heavily used servers.</span></span>  
  
 <span data-ttu-id="af4db-107">1 台のサーバーが別のサーバー グループのイベントを受信する場合、イベントを受信するサーバーは *警告管理サーバー*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="af4db-107">When one server receives events for a group of other servers, the server that receives events is called an *alerts management server*.</span></span> <span data-ttu-id="af4db-108">マルチサーバー環境では、マスター サーバーを警告管理サーバーとして指定します。</span><span class="sxs-lookup"><span data-stu-id="af4db-108">In a multiserver environment, you designate the master server as the alerts management server.</span></span>  
  
## <a name="advantages-of-using-an-alerts-management-server"></a><span data-ttu-id="af4db-109">警告管理サーバーを使用する利点</span><span class="sxs-lookup"><span data-stu-id="af4db-109">Advantages of Using an Alerts Management Server</span></span>  
 <span data-ttu-id="af4db-110">警告管理サーバーのセットアップには、次の利点があります。</span><span class="sxs-lookup"><span data-stu-id="af4db-110">The advantages of setting up an alerts management server include:</span></span>  
  
-   <span data-ttu-id="af4db-111">**集中化**。</span><span class="sxs-lookup"><span data-stu-id="af4db-111">**Centralization**.</span></span> <span data-ttu-id="af4db-112">1 台のサーバーで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の複数のインスタンスのイベントを集中管理したり統合表示したりできます。</span><span class="sxs-lookup"><span data-stu-id="af4db-112">Centralized control and a consolidated view of the events of several instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are possible from a single server.</span></span>  
  
-   <span data-ttu-id="af4db-113">**スケーラビリティ**。</span><span class="sxs-lookup"><span data-stu-id="af4db-113">**Scalability**.</span></span> <span data-ttu-id="af4db-114">多くの物理サーバーを 1 台の論理サーバーとして管理できます。</span><span class="sxs-lookup"><span data-stu-id="af4db-114">Many physical servers can be administered as one logical server.</span></span> <span data-ttu-id="af4db-115">必要に応じて、この物理サーバー グループに対してサーバーを追加または削除できます。</span><span class="sxs-lookup"><span data-stu-id="af4db-115">You can add or remove servers to this physical server group as needed.</span></span>  
  
-   <span data-ttu-id="af4db-116">**効率**。</span><span class="sxs-lookup"><span data-stu-id="af4db-116">**Efficiency**.</span></span> <span data-ttu-id="af4db-117">警告とオペレーターは一度だけ定義すればよいので、構成にかかる時間を節約できます。</span><span class="sxs-lookup"><span data-stu-id="af4db-117">Configuration time is reduced, because you need to define alerts and operators only once.</span></span>  
  
## <a name="disadvantages-of-using-an-alerts-management-server"></a><span data-ttu-id="af4db-118">警告管理サーバーを使用する欠点</span><span class="sxs-lookup"><span data-stu-id="af4db-118">Disadvantages of Using an Alerts Management Server</span></span>  
 <span data-ttu-id="af4db-119">警告管理サーバーのセットアップには、次のような欠点があります。</span><span class="sxs-lookup"><span data-stu-id="af4db-119">The disadvantages of setting up an alerts management server include:</span></span>  
  
-   <span data-ttu-id="af4db-120">**トラフィックの増加**。</span><span class="sxs-lookup"><span data-stu-id="af4db-120">**Increased traffic**.</span></span> <span data-ttu-id="af4db-121">警告管理サーバーにイベントを転送すると、ネットワーク トラフィックが増加することがあります。</span><span class="sxs-lookup"><span data-stu-id="af4db-121">Forwarding events to an alerts management server can increase network traffic.</span></span> <span data-ttu-id="af4db-122">ネットワーク トラフィックの増加を緩和するには、指定した重大度レベルを超えるイベントだけを転送するように制限します。</span><span class="sxs-lookup"><span data-stu-id="af4db-122">This increase can be moderated by restricting event forwarding to events that are above a designated severity level.</span></span>  
  
-   <span data-ttu-id="af4db-123">**単一地点での障害**。</span><span class="sxs-lookup"><span data-stu-id="af4db-123">**Single point of failure**.</span></span> <span data-ttu-id="af4db-124">警告管理サーバーがオフラインになると、管理されたサーバーのグループのイベントに対して警告が発行されません。</span><span class="sxs-lookup"><span data-stu-id="af4db-124">If the alerts management server goes offline, no alerts are issued for any event on the managed group of servers.</span></span>  
  
-   <span data-ttu-id="af4db-125">**サーバーの負荷**。</span><span class="sxs-lookup"><span data-stu-id="af4db-125">**Server load**.</span></span> <span data-ttu-id="af4db-126">転送されるイベントの警告処理により、警告管理サーバーの処理負荷が増加します。</span><span class="sxs-lookup"><span data-stu-id="af4db-126">Handling alerts for the forwarded events causes an increased processing load on the alerts management server.</span></span>  
  
## <a name="guidelines-for-using-an-alerts-management-server"></a><span data-ttu-id="af4db-127">警告管理サーバーの使用に関するガイドライン</span><span class="sxs-lookup"><span data-stu-id="af4db-127">Guidelines for Using an Alerts Management Server</span></span>  
 <span data-ttu-id="af4db-128">警告管理サーバーを構成する場合、次のガイドラインに従います。</span><span class="sxs-lookup"><span data-stu-id="af4db-128">When configuring an alerts management server, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="af4db-129">転送されたイベントを受信するには、警告管理サーバーが SQL Server の既定のインスタンスである必要があります。</span><span class="sxs-lookup"><span data-stu-id="af4db-129">In order to receive forwarded events, the alerts management server must be a default instance of SQL Server.</span></span>  
  
-   <span data-ttu-id="af4db-130">警告管理サーバーで、重要度または使用頻度の高いアプリケーションを実行しないようにします。</span><span class="sxs-lookup"><span data-stu-id="af4db-130">Avoid running critical or heavily used applications on the alerts management server.</span></span>  
  
-   <span data-ttu-id="af4db-131">多くのサーバーで同じ警告管理サーバーが共有されるように構成する場合、それに伴うネットワーク トラフィックについて慎重に検討します。</span><span class="sxs-lookup"><span data-stu-id="af4db-131">Carefully plan for the network traffic involved in configuring many servers to share the same alerts management server.</span></span> <span data-ttu-id="af4db-132">トラフィックが集中してしまった場合は、特定の警告管理サーバーを使用するサーバーの台数を減らします。</span><span class="sxs-lookup"><span data-stu-id="af4db-132">If congestion results, reduce the number of servers that use a particular alerts management server.</span></span>  
  
     <span data-ttu-id="af4db-133">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 内で登録されたサーバーは、警告転送サーバーとして選択できるサーバーの一覧に含まれます。</span><span class="sxs-lookup"><span data-stu-id="af4db-133">The servers that are registered within [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] constitute the list of servers available to be chosen by that server as the alerts-forwarding server.</span></span>  
  
-   <span data-ttu-id="af4db-134">警告管理サーバーに警告を転送するのではなく、サーバー固有の応答を必要とする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンスで警告を定義します。</span><span class="sxs-lookup"><span data-stu-id="af4db-134">Define alerts on the local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that require a server-specific response, instead of forwarding the alerts to the alerts management server.</span></span>  
  
     <span data-ttu-id="af4db-135">警告管理サーバーは、警告を転送してくるすべてのサーバーを 1 台の論理サーバーと見なします。</span><span class="sxs-lookup"><span data-stu-id="af4db-135">The alerts management server views all the servers forwarding to it as a logical whole.</span></span> <span data-ttu-id="af4db-136">たとえば、警告管理サーバーは、サーバー A からの 605 イベントと、サーバー B からの 605 イベントに同じように応答します。</span><span class="sxs-lookup"><span data-stu-id="af4db-136">For example, an alerts management server responds in the same way to a 605 event from server A and a 605 event from server B.</span></span>  
  
-   <span data-ttu-id="af4db-137">警告システムを構成した後は、Microsoft Windows アプリケーション ログで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント イベントの有無を定期的に確認します。</span><span class="sxs-lookup"><span data-stu-id="af4db-137">After configuring your alert system, periodically check the Microsoft Windows application log for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent events.</span></span>  
  
     <span data-ttu-id="af4db-138">警告エンジンによって検出されたエラー状況は、"SQL Server エージェント" のソース名でローカル Windows アプリケーション ログに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="af4db-138">Failure conditions encountered by the alerts engine are written to the local Windows application log with a source name of "SQL Server Agent."</span></span> <span data-ttu-id="af4db-139">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが定義に従って電子メールによる通知を送信できない場合は、アプリケーション ログにイベントが記録されます。</span><span class="sxs-lookup"><span data-stu-id="af4db-139">For example, if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent cannot send an e-mail notification as it has been defined, an event is logged in the application log.</span></span>  
  
 <span data-ttu-id="af4db-140">ローカルで定義された警告が無効になっていて、その警告の発生原因となるイベントが発生した場合、そのイベントが (警告転送の条件を満たしていれば) 警告管理サーバーに転送されます。</span><span class="sxs-lookup"><span data-stu-id="af4db-140">If a locally defined alert is inactivated, and an event occurs that would have caused the alert to fire, the event is forwarded to the alerts management server (if it satisfies the alert-forwarding condition).</span></span> <span data-ttu-id="af4db-141">この場合、ローカル サイトのユーザーの必要に応じて、ローカルオーバーライド (つまりローカル サーバーで定義され、警告管理サーバーでも定義される警告) を有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="af4db-141">This forwarding allows local overrides (alerts defined locally that are also defined on the alerts management server) to be turned off and on as needed by the user at the local site.</span></span> <span data-ttu-id="af4db-142">また、イベントがローカル警告によって処理される場合でも、必ずイベントが転送されるように要求することもできます。</span><span class="sxs-lookup"><span data-stu-id="af4db-142">You can also request that events always be forwarded, even if they are also handled by local alerts.</span></span>  
  
 <span data-ttu-id="af4db-143">次に、マルチサーバー環境でイベントを管理するための一般的なタスクを示します。</span><span class="sxs-lookup"><span data-stu-id="af4db-143">The following are common tasks for managing events in a multiserver environment:</span></span>  
  
 <span data-ttu-id="af4db-144">**警告管理サーバーを指定するには**</span><span class="sxs-lookup"><span data-stu-id="af4db-144">**To designate an alerts management server**</span></span>  
  
-   [<span data-ttu-id="af4db-145">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="af4db-145">SQL Server Management Studio</span></span>](../sql-server-management-studio-ssms.md)  
  
 <span data-ttu-id="af4db-146">**警告に対する応答を定義するには**</span><span class="sxs-lookup"><span data-stu-id="af4db-146">**To define the response to an alert**</span></span>  
  
-   [<span data-ttu-id="af4db-147">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="af4db-147">SQL Server Management Studio</span></span>](define-the-response-to-an-alert-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="af4db-148">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="af4db-148">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)  
  
## <a name="running-event-triggered-jobs"></a><span data-ttu-id="af4db-149">イベント トリガーのジョブの実行</span><span class="sxs-lookup"><span data-stu-id="af4db-149">Running Event-Triggered Jobs</span></span>  
 <span data-ttu-id="af4db-150">警告に応答して実行されるジョブを定義できます。</span><span class="sxs-lookup"><span data-stu-id="af4db-150">You can define a job to be executed in response to an alert.</span></span> <span data-ttu-id="af4db-151">たとえば、警告によって検出された問題を修正したり、さらに診断したりするジョブを実行できます。</span><span class="sxs-lookup"><span data-stu-id="af4db-151">For example, you can execute a job that corrects or further diagnoses a problem detected by the alert.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af4db-152">ジョブがイベントを発生させることもありえるので、再帰的な警告ジョブ ループを作成しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="af4db-152">Because a job can raise an event, be careful not to create a recursive alert-job loop.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af4db-153">参照</span><span class="sxs-lookup"><span data-stu-id="af4db-153">See Also</span></span>  
 [<span data-ttu-id="af4db-154">sys.sysメッセージ &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="af4db-154">sys.sysmessages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-compatibility-views/sys-sysmessages-transact-sql)  
  
  
