---
title: Master ストアド プロシージャ転送タスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfermasterspstask.f1
helpviewer_keywords:
- Transfer Master Stored Procedures task [Integration Services]
ms.assetid: 81702560-48a3-46d1-a469-e41304c7af8e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1915a3129eeb6e14c4315c37f2c6c2bf5b0d5412
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741161"
---
# <a name="transfer-master-stored-procedures-task"></a><span data-ttu-id="40a3e-102">Master ストアド プロシージャ転送タスク</span><span class="sxs-lookup"><span data-stu-id="40a3e-102">Transfer Master Stored Procedures Task</span></span>
  <span data-ttu-id="40a3e-103">Master ストアド プロシージャ転送タスクは、 **のインスタンス上の** master [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース間で、1 つ以上のユーザー定義ストアド プロシージャを転送します。</span><span class="sxs-lookup"><span data-stu-id="40a3e-103">The Transfer Master Stored Procedures task transfers one or more user-defined stored procedures between **master** databases on instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="40a3e-104">**master** データベースからストアド プロシージャを転送するには、プロシージャの所有者が dbo である必要があります。</span><span class="sxs-lookup"><span data-stu-id="40a3e-104">To transfer a stored procedure from the **master** database, the owner of the procedure must be dbo.</span></span>  
  
 <span data-ttu-id="40a3e-105">Master ストアド プロシージャ転送タスクは、すべてのストアド プロシージャまたは指定したストアド プロシージャのみを転送するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="40a3e-105">The Transfer Master Stored Procedures task can be configured to transfer all stored procedures or only specified stored procedures.</span></span> <span data-ttu-id="40a3e-106">このタスクでは、システム ストアド プロシージャはコピーされません。</span><span class="sxs-lookup"><span data-stu-id="40a3e-106">This task does not copy system stored procedures.</span></span>  
  
 <span data-ttu-id="40a3e-107">転送する master ストアド プロシージャが既に転送先に存在している場合もあります。</span><span class="sxs-lookup"><span data-stu-id="40a3e-107">The master stored procedures to be transferred may already exist on the destination.</span></span> <span data-ttu-id="40a3e-108">Master ストアド プロシージャ転送タスクでは、既存のストアド プロシージャの処理を次のように設定できます。</span><span class="sxs-lookup"><span data-stu-id="40a3e-108">The Transfer Master Stored Procedures task can be configured to handle existing stored procedures in the following ways:</span></span>  
  
-   <span data-ttu-id="40a3e-109">既存のストアド プロシージャを上書きします。</span><span class="sxs-lookup"><span data-stu-id="40a3e-109">Overwrite existing stored procedures.</span></span>  
  
-   <span data-ttu-id="40a3e-110">重複するストアド プロシージャが存在する場合、タスクを失敗とします。</span><span class="sxs-lookup"><span data-stu-id="40a3e-110">Fail the task when duplicate stored procedures exist.</span></span>  
  
-   <span data-ttu-id="40a3e-111">重複するストアド プロシージャをスキップします。</span><span class="sxs-lookup"><span data-stu-id="40a3e-111">Skip duplicate stored procedures.</span></span>  
  
 <span data-ttu-id="40a3e-112">Master ストアド プロシージャ転送タスクは実行時に、2 つの SMO 接続マネージャーを使用して、転送元および転送先サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="40a3e-112">At run time, the Transfer Master Stored Procedures task connects to the source and destination servers by using two SMO connection managers.</span></span> <span data-ttu-id="40a3e-113">SMO 接続マネージャーの構成は Master ストアド プロシージャ転送タスクとは別に行い、Master ストアド プロシージャ転送タスクは SMO 接続マネージャーを参照します。</span><span class="sxs-lookup"><span data-stu-id="40a3e-113">The SMO connection managers are configured separately from the Transfer Master Stored Procedures task, and then referenced in the Transfer Master Stored Procedures task.</span></span> <span data-ttu-id="40a3e-114">SMO 接続マネージャーは、サーバーと、サーバーに接続する際に使用する認証モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="40a3e-114">The SMO connection managers specify the server and the authentication mode to use when accessing the server.</span></span> <span data-ttu-id="40a3e-115">詳細については、「 [SMO 接続マネージャー](../connection-manager/smo-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="40a3e-115">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
## <a name="transferring-stored-procedures-between-instances-of-sql-server"></a><span data-ttu-id="40a3e-116">SQL Server のインスタンス間でのストアド プロシージャの転送</span><span class="sxs-lookup"><span data-stu-id="40a3e-116">Transferring Stored Procedures Between Instances of SQL Server</span></span>  
 <span data-ttu-id="40a3e-117">Master ストアド プロシージャ転送タスクでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 転送元と転送先をサポートします。</span><span class="sxs-lookup"><span data-stu-id="40a3e-117">The Transfer Master Stored Procedures task supports a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source and destination.</span></span>  
  
## <a name="events"></a><span data-ttu-id="40a3e-118">events</span><span class="sxs-lookup"><span data-stu-id="40a3e-118">Events</span></span>  
 <span data-ttu-id="40a3e-119">Master ストアド プロシージャ転送タスクでは、転送されたストアド プロシージャの数を報告する情報イベントと、ストアド プロシージャが上書きされた場合の警告イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="40a3e-119">The task raises an information event that reports the number of stored procedures transferred and a warning event when a stored procedure is overwritten.</span></span>  
  
 <span data-ttu-id="40a3e-120">Master ストアド プロシージャ転送タスクでは、増分中のログイン転送タスクの進捗状況は報告されません。0% または 100% 完了した場合のみ報告されます。</span><span class="sxs-lookup"><span data-stu-id="40a3e-120">The Transfer Master Stored Procedures task does not report incremental progress of the login transfer; it reports only 0% and 100 % completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="40a3e-121">実行値</span><span class="sxs-lookup"><span data-stu-id="40a3e-121">Execution Value</span></span>  
 <span data-ttu-id="40a3e-122">タスクの `ExecutionValue` プロパティで定義する実行値は、転送されたストアド プロシージャの数を返します。</span><span class="sxs-lookup"><span data-stu-id="40a3e-122">The execution value, defined in the `ExecutionValue` property of the task, returns the number of stored procedures transferred.</span></span> <span data-ttu-id="40a3e-123">Master ストアド プロシージャ転送タスクの `ExecValueVariable` プロパティにユーザー定義変数を割り当てると、パッケージの他のオブジェクトからストアド プロシージャの転送に関する情報を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="40a3e-123">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer Master Stored Procedures task, information about the stored procedure transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="40a3e-124">詳細については、「[Integration Services &#40;SSIS&#41; の変数](../integration-services-ssis-variables.md)」と「[パッケージで変数を使用する](../use-variables-in-packages.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="40a3e-124">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="40a3e-125">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="40a3e-125">Log Entries</span></span>  
 <span data-ttu-id="40a3e-126">Master ストアド プロシージャ転送タスクには、次のようなカスタム ログ エントリがあります。</span><span class="sxs-lookup"><span data-stu-id="40a3e-126">The Transfer Master Stored Procedures task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="40a3e-127">TransferStoredProceduresTaskStartTransferringObjects  転送が開始されたことを報告するログ エントリです。</span><span class="sxs-lookup"><span data-stu-id="40a3e-127">TransferStoredProceduresTaskStartTransferringObjects  This log entry reports that the transfer has started.</span></span> <span data-ttu-id="40a3e-128">ログ エントリには、開始時刻が含まれます。</span><span class="sxs-lookup"><span data-stu-id="40a3e-128">The log entry includes the start time.</span></span>  
  
-   <span data-ttu-id="40a3e-129">TransferSStoredProceduresTaskFinishedTransferringObjects  転送が終了したことを報告するログ エントリです。</span><span class="sxs-lookup"><span data-stu-id="40a3e-129">TransferSStoredProceduresTaskFinishedTransferringObjects  This log entry reports that the transfer has finished.</span></span> <span data-ttu-id="40a3e-130">ログ エントリには、終了時刻が含まれます。</span><span class="sxs-lookup"><span data-stu-id="40a3e-130">The log entry includes the end time.</span></span>  
  
 <span data-ttu-id="40a3e-131">また、`OnInformation` イベントのログ エントリは転送されたストアド プロシージャの数を報告し、`OnWarning` イベントのログ エントリは転送先でストアド プロシージャが上書きされると書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="40a3e-131">In addition, a log entry for the `OnInformation` event reports the number of stored procedures that were transferred, and a log entry for the `OnWarning` event is written for each stored procedure on the destination that is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="40a3e-132">セキュリティとアクセス許可</span><span class="sxs-lookup"><span data-stu-id="40a3e-132">Security and Permissions</span></span>  
 <span data-ttu-id="40a3e-133">ソースの **master** データベースでストアド プロシージャの一覧を表示する権限が必要です。また、転送先サーバーの sysadmin サーバー ロールのメンバーであるか、転送先サーバーの **master** データベースでストアド プロシージャを作成する権限を持つユーザーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="40a3e-133">The user must have permission to view the list of stored procedure in the **master** database on the source, and must be a member of the sysadmin server role or have permission to created stored procedures in the **master** database on the destination server.</span></span>  
  
## <a name="configuration-of-the-transfer-master-stored-procedures-task"></a><span data-ttu-id="40a3e-134">Master ストアド プロシージャ転送タスクの構成</span><span class="sxs-lookup"><span data-stu-id="40a3e-134">Configuration of the Transfer Master Stored Procedures Task</span></span>  
 <span data-ttu-id="40a3e-135">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="40a3e-135">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="40a3e-136">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="40a3e-136">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="40a3e-137">[[Master ストアド プロシージャ転送タスク エディター] ([全般] ページ)](../general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="40a3e-137">[Transfer Master Stored Procedures Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md)</span></span>  
  
-   <span data-ttu-id="40a3e-138">[[Master ストアド プロシージャ転送タスク エディター] &#40;[ストアド プロシージャ] ページ&#41;](../transfer-master-stored-procedures-task-editor-stored-procedures-page.md)</span><span class="sxs-lookup"><span data-stu-id="40a3e-138">[Transfer Master Stored Procedures Task Editor &#40;Stored Procedures Page&#41;](../transfer-master-stored-procedures-task-editor-stored-procedures-page.md)</span></span>  
  
-   <span data-ttu-id="40a3e-139">[[式] ページ](../expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="40a3e-139">[Expressions Page](../expressions/expressions-page.md)</span></span>  
  
 <span data-ttu-id="40a3e-140">プログラムによってこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="40a3e-140">For information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferStoredProceduresTask.TransferStoredProceduresTask>  
  
### <a name="configuring-the-transfer-master-stored-procedures-task-programmatically"></a><span data-ttu-id="40a3e-141">プログラムによる Master ストアド プロシージャ転送タスクの構成</span><span class="sxs-lookup"><span data-stu-id="40a3e-141">Configuring the Transfer Master Stored Procedures Task Programmatically</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="40a3e-142">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="40a3e-142">Related Tasks</span></span>  
 <span data-ttu-id="40a3e-143">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="40a3e-143">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="40a3e-144">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="40a3e-144">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="40a3e-145">参照</span><span class="sxs-lookup"><span data-stu-id="40a3e-145">See Also</span></span>  
 <span data-ttu-id="40a3e-146">[SQL Server オブジェクトの転送タスク](transfer-sql-server-objects-task.md) </span><span class="sxs-lookup"><span data-stu-id="40a3e-146">[Transfer SQL Server Objects Task](transfer-sql-server-objects-task.md) </span></span>  
 <span data-ttu-id="40a3e-147">[Integration Services タスク](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="40a3e-147">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="40a3e-148">制御フロー</span><span class="sxs-lookup"><span data-stu-id="40a3e-148">Control Flow</span></span>](control-flow.md)  
  
  
