---
title: イベントの監視と応答 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- notifications [SQL Server], alert
- events [SQL Server], alerts
- alerts [SQL Server]
- notifications [SQL Server]
- events [SQL Server], automatically responding to
- administrator notifications [SQL Server Agent]
- automatic event responses
- SQL Server Agent alerts
- monitoring [SQL Server], events
- responding to events automatically
ms.assetid: f7fbe155-5b68-4777-bc71-a47637471f32
author: stevestein
ms.author: sstein
ms.openlocfilehash: afdf1beffd6099fce84f03a8ba65f7de9abb8f0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715009"
---
# <a name="monitor-and-respond-to-events"></a><span data-ttu-id="db837-102">イベントの監視と応答</span><span class="sxs-lookup"><span data-stu-id="db837-102">Monitor and Respond to Events</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="db837-103">エージェントは、のメッセージ*events* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、特定のパフォーマンス条件、Windows Management Instrumentation (WMI) イベントなどのイベントを監視し、自動的に応答します。</span><span class="sxs-lookup"><span data-stu-id="db837-103">Agent can monitor and automatically respond to *events*, such as messages from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], specific performance conditions, and Windows Management Instrumentation (WMI) events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db837-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="db837-104">In This Section</span></span>  
 [<span data-ttu-id="db837-105">アラート</span><span class="sxs-lookup"><span data-stu-id="db837-105">Alerts</span></span>](alerts.md)  
 <span data-ttu-id="db837-106">警告の命名、および警告が応答するイベントやパフォーマンス条件の選択について説明します。</span><span class="sxs-lookup"><span data-stu-id="db837-106">Contains information about naming an alert and selecting the events or performance conditions to which alerts respond.</span></span>  
  
 [<span data-ttu-id="db837-107">ユーザー定義イベントの作成</span><span class="sxs-lookup"><span data-stu-id="db837-107">Create a User-Defined Event</span></span>](create-a-user-defined-event.md)  
 <span data-ttu-id="db837-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によってあらかじめ定義されているイベント以外のイベントを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="db837-108">Contains information about how to create events other than those that are predefined by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="db837-109">オペレーター</span><span class="sxs-lookup"><span data-stu-id="db837-109">Operators</span></span>](operators.md)  
 <span data-ttu-id="db837-110">ジョブが失敗または成功したときに通知を送信するために [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで使用できる、管理者の別名の作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="db837-110">Contains information about creating aliases for administrators that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can use to send notifications when jobs fail or succeed.</span></span>  
  
## <a name="about-monitoring-and-responding-to-events"></a><span data-ttu-id="db837-111">イベントの監視と応答について</span><span class="sxs-lookup"><span data-stu-id="db837-111">About Monitoring and Responding to Events</span></span>  
 <span data-ttu-id="db837-112">イベントへの自動応答を *警告*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="db837-112">Automated responses to events are called *alerts*.</span></span> <span data-ttu-id="db837-113">1 つ以上のイベントの警告を定義して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがイベントの発生に応答する方法を指定できます。</span><span class="sxs-lookup"><span data-stu-id="db837-113">You can define an alert on one or more events to specify how you want [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to respond to their occurrence.</span></span> <span data-ttu-id="db837-114">警告は、管理者に通知するか、ジョブを実行するか、またはその両方を行ってイベントに応答できます。</span><span class="sxs-lookup"><span data-stu-id="db837-114">An alert can respond to an event by notifying an administrator or running a job, or both.</span></span> <span data-ttu-id="db837-115">警告は、別のコンピューターの Microsoft Windows アプリケーション ログにイベントを転送することもできます。</span><span class="sxs-lookup"><span data-stu-id="db837-115">An alert can also forward an event to the Microsoft Windows application log on a different computer.</span></span> <span data-ttu-id="db837-116">たとえば、重大度レベル 19 のイベントが発生した場合に、オペレーターに直ちに通知されるように指定できます。</span><span class="sxs-lookup"><span data-stu-id="db837-116">For example, you can specify that an operator be notified immediately if an event of severity 19 occurs.</span></span> <span data-ttu-id="db837-117">データベース管理者は警告を定義することにより、より効果的に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を監視および管理できます。</span><span class="sxs-lookup"><span data-stu-id="db837-117">By defining alerts, database administrators can more effectively monitor and manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="db837-118">エージェントは、警告が定義されているイベントにのみ応答します。</span><span class="sxs-lookup"><span data-stu-id="db837-118">Agent only responds to events for which an alert is defined.</span></span> <span data-ttu-id="db837-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントでによってイベントを監視するために使用される方法は、イベントの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="db837-119">The method that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent uses to monitor events depends on the type of event.</span></span>  
  
 <span data-ttu-id="db837-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの警告がパフォーマンス カウンターに定義されていると、そのパフォーマンス カウンターは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによって直接監視されます。</span><span class="sxs-lookup"><span data-stu-id="db837-120">When a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert is defined for a performance counter, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent directly monitors the performance counter.</span></span> <span data-ttu-id="db837-121">WMI イベントでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントにより WMI イベントのイベント クエリが登録されます。</span><span class="sxs-lookup"><span data-stu-id="db837-121">For a WMI event, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent registers an event query for the WMI event.</span></span>  
  
 <span data-ttu-id="db837-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からのメッセージに応答するために Windows アプリケーション ログが監視されます。</span><span class="sxs-lookup"><span data-stu-id="db837-122">To respond to messages from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent monitors the Windows application log.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="db837-123">エージェントは、このログに示されるメッセージだけに応答できます。</span><span class="sxs-lookup"><span data-stu-id="db837-123">Agent can only respond to messages that appear in this log.</span></span> <span data-ttu-id="db837-124">既定では、SQL Server によって、次のメッセージが Windows アプリケーション ログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="db837-124">By default, SQL Server logs the following messages in the Windows application log:</span></span>  
  
-   <span data-ttu-id="db837-125">重大度レベルが 19 以上の sysmessages エラー。</span><span class="sxs-lookup"><span data-stu-id="db837-125">Severity 19 or higher sysmessages errors.</span></span>  
  
     <span data-ttu-id="db837-126">重大度レベルが 19 より低い特定の sysmessages エラーもログに記録する場合は、sp_altermessage ストアド プロシージャを使用して、"常にログ記録されています" などのエラーを指定します。</span><span class="sxs-lookup"><span data-stu-id="db837-126">If you also want to log specific sysmessages errors that have a severity lower than 19, use the sp_altermessage stored procedure to designate such errors as "always logged".</span></span>  
  
-   <span data-ttu-id="db837-127">WITH LOG 構文を使用して実行されるすべての RAISERROR ステートメント。</span><span class="sxs-lookup"><span data-stu-id="db837-127">Any RAISERROR statement invoked by using the WITH LOG syntax.</span></span>  
  
     <span data-ttu-id="db837-128">RAISERROR WITH LOG は、SQL Server のインスタンスから Windows アプリケーション ログに書き込むのに推奨できる手段です。</span><span class="sxs-lookup"><span data-stu-id="db837-128">Using RAISERROR WITH LOG is the recommended way to write to the Windows application log from an instance of SQL Server.</span></span>  
  
-   <span data-ttu-id="db837-129">xp_logevent を使用してログ記録されたアプリケーション イベント。</span><span class="sxs-lookup"><span data-stu-id="db837-129">Any application event that is logged by using xp_logevent.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="db837-130">アプリケーション イベントのログ記録により、ログ領域が使用され、その結果 Windows アプリケーション ログの最大サイズを超える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="db837-130">Logging application events consumes log space and can cause the Windows application log to exceed its maximum size.</span></span> <span data-ttu-id="db837-131">SQL Server のイベント情報を失わないように、Windows アプリケーション ログの最大サイズが十分大きいかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="db837-131">Make sure that the maximum Windows application log size is large enough to avoid loss of SQL Server event information.</span></span>  
  
 <span data-ttu-id="db837-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってメッセージがログ記録されると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理者が定義した警告とメッセージが比較されます。</span><span class="sxs-lookup"><span data-stu-id="db837-132">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logs a message, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service compares the message against the alerts defined by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrator.</span></span>  
  
 <span data-ttu-id="db837-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスは、イベントのソースが何であっても、イベントの警告で指定されたタスクを実行することによりそのイベントに応答します。</span><span class="sxs-lookup"><span data-stu-id="db837-133">Regardless of the source of the event, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service responds to the event by performing the tasks specified in the alert for the event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db837-134">参照</span><span class="sxs-lookup"><span data-stu-id="db837-134">See Also</span></span>  
 [<span data-ttu-id="db837-135">sp_altermessage &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="db837-135">sp_altermessage &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-altermessage-transact-sql)  
  
  
