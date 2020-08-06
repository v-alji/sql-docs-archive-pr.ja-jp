---
title: ジョブ転送タスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferjobstask.f1
helpviewer_keywords:
- Transfer Jobs task [Integration Services]
ms.assetid: 1bf33885-9c5b-47e4-a549-f5920b66a1de
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d692934d5f7c8c1449b123ee8b9caf1d8bb34744
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631176"
---
# <a name="transfer-jobs-task"></a><span data-ttu-id="a6648-102">ジョブ転送タスク</span><span class="sxs-lookup"><span data-stu-id="a6648-102">Transfer Jobs Task</span></span>
  <span data-ttu-id="a6648-103">ジョブ転送タスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス間で 1 つ以上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント ジョブを転送します。</span><span class="sxs-lookup"><span data-stu-id="a6648-103">The Transfer Jobs task transfers one or more [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="a6648-104">ジョブ転送タスクは、すべてのジョブまたは指定したジョブのみを転送するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="a6648-104">The Transfer Jobs task can be configured to transfer all jobs, or only specified jobs.</span></span> <span data-ttu-id="a6648-105">また、転送先で転送したジョブを有効にするかどうかも指定できます。</span><span class="sxs-lookup"><span data-stu-id="a6648-105">You can also indicate whether the transferred jobs are enabled at the destination.</span></span>  
  
 <span data-ttu-id="a6648-106">転送しようとするジョブが既に転送先に存在している場合もあります。</span><span class="sxs-lookup"><span data-stu-id="a6648-106">The jobs to be transferred may already exist on the destination.</span></span> <span data-ttu-id="a6648-107">ジョブ転送タスクでは、既存のジョブの処理を次のように構成できます。</span><span class="sxs-lookup"><span data-stu-id="a6648-107">The Transfer Jobs task can be configured to handle existing jobs in the following ways:</span></span>  
  
-   <span data-ttu-id="a6648-108">既存のジョブを上書きします。</span><span class="sxs-lookup"><span data-stu-id="a6648-108">Overwrite existing jobs.</span></span>  
  
-   <span data-ttu-id="a6648-109">重複するジョブが存在する場合、タスクを失敗させます。</span><span class="sxs-lookup"><span data-stu-id="a6648-109">Fail the task when duplicate jobs exist.</span></span>  
  
-   <span data-ttu-id="a6648-110">重複するジョブをスキップします。</span><span class="sxs-lookup"><span data-stu-id="a6648-110">Skip duplicate jobs.</span></span>  
  
 <span data-ttu-id="a6648-111">実行時に、ジョブ転送タスクは 1 つまたは 2 つの SMO 接続マネージャーを使用して、転送元および転送先サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="a6648-111">At run time, the Transfer Jobs task connects to the source and destination servers by using one or two SMO connection managers.</span></span> <span data-ttu-id="a6648-112">SMO 接続マネージャーはジョブ転送タスクとは別に構成され、ジョブ転送タスクで参照されます。</span><span class="sxs-lookup"><span data-stu-id="a6648-112">The SMO connection manager is configured separately from the Transfer Jobs task, and then is referenced in the Transfer Jobs task.</span></span> <span data-ttu-id="a6648-113">SMO 接続マネージャーは、サーバーと、このサーバーにアクセスするときに使用する認証モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="a6648-113">The SMO connection manager specifies the server and the authentication mode to use when accessing the server.</span></span> <span data-ttu-id="a6648-114">詳細については、「 [SMO 接続マネージャー](../connection-manager/smo-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a6648-114">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
## <a name="transferring-jobs-between-instances-of-sql-server"></a><span data-ttu-id="a6648-115">SQL Server のインスタンス間でのジョブの転送</span><span class="sxs-lookup"><span data-stu-id="a6648-115">Transferring Jobs Between Instances of SQL Server</span></span>  
 <span data-ttu-id="a6648-116">ジョブ転送タスクは、転送元または転送先として、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をサポートします。</span><span class="sxs-lookup"><span data-stu-id="a6648-116">The Transfer Jobs task supports a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source and destination.</span></span> <span data-ttu-id="a6648-117">転送元または転送先として使用するバージョンに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="a6648-117">There are no restrictions on which version to use as a source or destination.</span></span>  
  
## <a name="events"></a><span data-ttu-id="a6648-118">events</span><span class="sxs-lookup"><span data-stu-id="a6648-118">Events</span></span>  
 <span data-ttu-id="a6648-119">ジョブ転送タスクでは、転送されたジョブの数を報告する情報イベントと、ジョブが上書きされた場合の警告イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="a6648-119">The Transfer Jobs task raises an information event that reports the number of jobs transferred and a warning event when a job is overwritten.</span></span> <span data-ttu-id="a6648-120">ジョブの転送の進捗状況は報告されません。0% または 100% 完了した場合のみ報告されます。</span><span class="sxs-lookup"><span data-stu-id="a6648-120">The task does not report incremental progress of the job transfer; it reports only 0% and 100% completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="a6648-121">実行値</span><span class="sxs-lookup"><span data-stu-id="a6648-121">Execution Value</span></span>  
 <span data-ttu-id="a6648-122">タスクの `ExecutionValue` プロパティで定義される実行値は、転送されたジョブの数を返します。</span><span class="sxs-lookup"><span data-stu-id="a6648-122">The execution value, defined in the `ExecutionValue` property of the task, returns the number of jobs that are transferred.</span></span> <span data-ttu-id="a6648-123">ジョブ転送タスクの `ExecValueVariable` プロパティにユーザー定義変数を割り当てると、パッケージの他のオブジェクトからジョブの転送に関する情報を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a6648-123">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer Jobs task, information about the job transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="a6648-124">詳細については、「[Integration Services &#40;SSIS&#41; の変数](../integration-services-ssis-variables.md)」と「[パッケージで変数を使用する](../use-variables-in-packages.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a6648-124">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="a6648-125">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="a6648-125">Log Entries</span></span>  
 <span data-ttu-id="a6648-126">ジョブ転送タスクには、次のようなカスタム ログ エントリがあります。</span><span class="sxs-lookup"><span data-stu-id="a6648-126">The Transfer Jobs task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="a6648-127">TransferJobsTaskStarTransferringObjects   転送が開始されたことを報告するログ エントリです。</span><span class="sxs-lookup"><span data-stu-id="a6648-127">TransferJobsTaskStarTransferringObjects   This log entry reports that the transfer has started.</span></span> <span data-ttu-id="a6648-128">ログ エントリには、開始時刻が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a6648-128">The log entry includes the start time.</span></span>  
  
-   <span data-ttu-id="a6648-129">TransferJobsTaskFinishedTransferringObjects    転送が終了したことを報告するログ エントリです。</span><span class="sxs-lookup"><span data-stu-id="a6648-129">TransferJobsTaskFinishedTransferringObjects    This log entry reports that the transfer has finished.</span></span> <span data-ttu-id="a6648-130">ログ エントリには、終了時刻が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a6648-130">The log entry includes the end time.</span></span>  
  
 <span data-ttu-id="a6648-131">また、`OnInformation` イベントのログ エントリは転送されたジョブの数を報告し、`OnWarning` イベントのログ エントリは転送先でジョブが上書きされると書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="a6648-131">In addition, a log entry for the `OnInformation` event reports the number of jobs that were transferred and a log entry for the `OnWarning` event is written for each job on the destination that is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="a6648-132">セキュリティとアクセス許可</span><span class="sxs-lookup"><span data-stu-id="a6648-132">Security and Permissions</span></span>  
 <span data-ttu-id="a6648-133">ジョブを転送するユーザーは、sysadmin 固定サーバー ロールのメンバー、または転送元および転送先の両方の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの msdb データベースで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6648-133">To transfer jobs, the user must be a member of the sysadmin fixed server role or one of the fixed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles on the msdb database on the both the source and destination instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="configuration-of-the-transfer-jobs-task"></a><span data-ttu-id="a6648-134">ジョブ転送タスクの構成</span><span class="sxs-lookup"><span data-stu-id="a6648-134">Configuration of the Transfer Jobs Task</span></span>  
 <span data-ttu-id="a6648-135">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="a6648-135">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="a6648-136">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6648-136">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="a6648-137">[[ジョブ転送タスク エディター] ([全般] ページ)](../general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="a6648-137">[Transfer Jobs Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md)</span></span>  
  
-   <span data-ttu-id="a6648-138">[[ジョブ転送タスク エディター] ([ジョブ] ページ)](../transfer-jobs-task-editor-jobs-page.md)</span><span class="sxs-lookup"><span data-stu-id="a6648-138">[Transfer Jobs Task Editor &#40;Jobs Page&#41;](../transfer-jobs-task-editor-jobs-page.md)</span></span>  
  
-   <span data-ttu-id="a6648-139">[[式] ページ](../expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="a6648-139">[Expressions Page](../expressions/expressions-page.md)</span></span>  
  
 <span data-ttu-id="a6648-140">プログラムによってこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6648-140">For information about programmatically setting these properties, click the of the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferJobsTask.TransferJobsTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="a6648-141">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="a6648-141">Related Tasks</span></span>  
 <span data-ttu-id="a6648-142">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6648-142">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="a6648-143">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="a6648-143">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="a6648-144">参照</span><span class="sxs-lookup"><span data-stu-id="a6648-144">See Also</span></span>  
 <span data-ttu-id="a6648-145">[Integration Services タスク](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="a6648-145">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="a6648-146">制御フロー</span><span class="sxs-lookup"><span data-stu-id="a6648-146">Control Flow</span></span>](control-flow.md)  
  
  
