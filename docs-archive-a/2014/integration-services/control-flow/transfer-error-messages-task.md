---
title: エラー メッセージ転送タスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfererrormessagestask.f1
helpviewer_keywords:
- Transfer Error Messages task [Integration Services]
ms.assetid: da702289-035a-4d14-bd74-04461fbfee1b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 952acc28a79fef7e7351c97400e05bc7ba5b9243
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631177"
---
# <a name="transfer-error-messages-task"></a><span data-ttu-id="16c82-102">エラー メッセージ転送タスク</span><span class="sxs-lookup"><span data-stu-id="16c82-102">Transfer Error Messages Task</span></span>
  <span data-ttu-id="16c82-103">エラー メッセージ転送タスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス間で 1 つ以上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ユーザー定義エラー メッセージを転送します。</span><span class="sxs-lookup"><span data-stu-id="16c82-103">The Transfer Error Messages task transfers one or more [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user-defined error messages between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="16c82-104">ユーザー定義メッセージとは、ID の値が 50000 以上のメッセージのことです。</span><span class="sxs-lookup"><span data-stu-id="16c82-104">User-defined messages are messages with an identifier that is equal to or greater than 50000.</span></span> <span data-ttu-id="16c82-105">ID の値が 50000 未満のメッセージはシステム エラー メッセージなので、エラー メッセージ転送タスクを使用して転送することはできません。</span><span class="sxs-lookup"><span data-stu-id="16c82-105">Messages with an identifier less than 50000 are system error messages, and cannot be transferred by using the Transfer Error Messages task.</span></span>  
  
 <span data-ttu-id="16c82-106">エラー メッセージ転送タスクは、すべてのエラー メッセージを転送するか、指定したエラー メッセージだけを転送できるように、構成することができます。</span><span class="sxs-lookup"><span data-stu-id="16c82-106">The Transfer Error Messages task can be configured to transfer all error messages, or only the specified error messages.</span></span> <span data-ttu-id="16c82-107">ユーザー定義エラー メッセージはさまざまな言語で利用できます。このタスクでは、選択した言語のメッセージだけを転送するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="16c82-107">User-defined error messages may be available in a number of different languages and the task can be configured to transfer only messages in selected languages.</span></span> <span data-ttu-id="16c82-108">他言語バージョンのメッセージを転送先サーバーに転送するには、コード ページ 1033 を使用した us_english バージョンのメッセージが転送先サーバーにあらかじめ存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="16c82-108">A us_english version of the message that uses code page 1033 must exist on the destination server before you can transfer other language versions of the message to that server.</span></span>  
  
 <span data-ttu-id="16c82-109">master データベースの sysmessages テーブルには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用されるすべてのシステム エラー メッセージおよびユーザー定義エラー メッセージが格納されます。</span><span class="sxs-lookup"><span data-stu-id="16c82-109">The sysmessages table in the master database contains all the error messages-both system and user-defined-that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses.</span></span>  
  
 <span data-ttu-id="16c82-110">転送対象のユーザー定義メッセージは、転送先に既に存在している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="16c82-110">The user-defined messages to be transferred may already exist on the destination.</span></span> <span data-ttu-id="16c82-111">エラー メッセージは、その識別子と言語が同じ場合は、重複エラー メッセージとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="16c82-111">An error message is defined as a duplicate error message if the identifier and the language are the same.</span></span> <span data-ttu-id="16c82-112">エラー メッセージ転送タスクでは、既存のエラー メッセージの処理方法を次のように構成できます。</span><span class="sxs-lookup"><span data-stu-id="16c82-112">The Transfer Error Messages task can be configured to handle existing error messages in the following ways:</span></span>  
  
-   <span data-ttu-id="16c82-113">既存のエラー メッセージを上書きします。</span><span class="sxs-lookup"><span data-stu-id="16c82-113">Overwrite existing error messages.</span></span>  
  
-   <span data-ttu-id="16c82-114">重複するメッセージが存在する場合、タスクを失敗とします。</span><span class="sxs-lookup"><span data-stu-id="16c82-114">Fail the task when duplicate messages exist.</span></span>  
  
-   <span data-ttu-id="16c82-115">重複エラー メッセージをスキップします。</span><span class="sxs-lookup"><span data-stu-id="16c82-115">Skip duplicate error messages.</span></span>  
  
 <span data-ttu-id="16c82-116">実行時、エラー メッセージ転送タスクは、1 つまたは 2 つの SMO 接続マネージャーを使用して、転送元サーバーと転送先サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="16c82-116">At run time, the Transfer Error Messages task connects to the source and destination servers by using one or two SMO connection managers.</span></span> <span data-ttu-id="16c82-117">SMO 接続マネージャーの構成はエラー メッセージ転送タスクとは別に行い、エラー メッセージ転送タスクは接続マネージャーを参照します。</span><span class="sxs-lookup"><span data-stu-id="16c82-117">The SMO connection manager is configured separately from the Transfer Error Messages task, and then is referenced in the Transfer Error Messages task.</span></span> <span data-ttu-id="16c82-118">SMO 接続マネージャーは、サーバーと、このサーバーにアクセスするときに使用する認証モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="16c82-118">The SMO connection manager specifies the server and the authentication mode to use when accessing the server.</span></span> <span data-ttu-id="16c82-119">詳細については、「 [SMO 接続マネージャー](../connection-manager/smo-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="16c82-119">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
 <span data-ttu-id="16c82-120">エラー メッセージ転送タスクは、転送元および転送先として [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="16c82-120">The Transfer Error Messages task supports a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source and destination.</span></span> <span data-ttu-id="16c82-121">転送元または転送先として使用するバージョンに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="16c82-121">There are no restrictions on which version to use as a source or destination.</span></span>  
  
## <a name="events"></a><span data-ttu-id="16c82-122">events</span><span class="sxs-lookup"><span data-stu-id="16c82-122">Events</span></span>  
 <span data-ttu-id="16c82-123">このタスクは、転送されたエラー メッセージの数を報告する情報イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="16c82-123">The task raises an information event that reports the number of error messages that have been transferred.</span></span>  
  
 <span data-ttu-id="16c82-124">エラー メッセージ転送タスクでは、エラー メッセージ転送の進捗状況は報告されません。0% または 100% 完了した場合のみ報告されます。</span><span class="sxs-lookup"><span data-stu-id="16c82-124">The Transfer Error Messages task does not report incremental progress of the error message transfer; it reports only 0% and 100 % completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="16c82-125">実行値</span><span class="sxs-lookup"><span data-stu-id="16c82-125">Execution Value</span></span>  
 <span data-ttu-id="16c82-126">このタスクの `ExecutionValue` プロパティに定義される実行値は、転送されたエラー メッセージの数を返します。</span><span class="sxs-lookup"><span data-stu-id="16c82-126">The execution value, defined in the `ExecutionValue` property of the task, returns the number of error messages that have been transferred.</span></span> <span data-ttu-id="16c82-127">エラー メッセージ転送タスクの `ExecValueVariable` プロパティにユーザー定義変数を割り当てると、エラー メッセージ転送に関する情報をパッケージ内の他のオブジェクトで利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="16c82-127">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer Error Message task, information about the error message transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="16c82-128">詳細については、「[Integration Services &#40;SSIS&#41; の変数](../integration-services-ssis-variables.md)」と「[パッケージで変数を使用する](../use-variables-in-packages.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="16c82-128">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="16c82-129">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="16c82-129">Log Entries</span></span>  
 <span data-ttu-id="16c82-130">エラー メッセージ転送タスクには、次のようなカスタム ログ エントリがあります。</span><span class="sxs-lookup"><span data-stu-id="16c82-130">The Transfer Error Messages task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="16c82-131">TransferErrorMessagesTaskStartTransferringObjects: 転送が開始されたことを報告するログ エントリです。</span><span class="sxs-lookup"><span data-stu-id="16c82-131">TransferErrorMessagesTaskStartTransferringObjects    This log entry reports that the transfer has started.</span></span> <span data-ttu-id="16c82-132">ログ エントリには、開始時刻が含まれます。</span><span class="sxs-lookup"><span data-stu-id="16c82-132">The log entry includes the start time.</span></span>  
  
-   <span data-ttu-id="16c82-133">TransferErrorMessagesTaskFinishedTransferringObjects: 転送が終了したことを報告するログ エントリです。</span><span class="sxs-lookup"><span data-stu-id="16c82-133">TransferErrorMessagesTaskFinishedTransferringObjects   This log entry reports that the transfer has finished.</span></span> <span data-ttu-id="16c82-134">ログ エントリには、終了時刻が含まれます。</span><span class="sxs-lookup"><span data-stu-id="16c82-134">The log entry includes the end time.</span></span>  
  
 <span data-ttu-id="16c82-135">また、`OnInformation` イベントのログ エントリは転送されたエラー メッセージの数をレポートし、`OnWarning event` のログ エントリは転送先でエラー メッセージが上書きされるたびに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="16c82-135">In addition, a log entry for the `OnInformation` event reports the number of error messages that were transferred, and a log entry for the `OnWarning event` is written for each error message on the destination that is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="16c82-136">セキュリティとアクセス許可</span><span class="sxs-lookup"><span data-stu-id="16c82-136">Security and Permissions</span></span>  
 <span data-ttu-id="16c82-137">新しいエラー メッセージを作成する場合、パッケージを実行するユーザーは、転送先サーバーで sysadmin または serveradmin サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="16c82-137">To create new error messages, the user that runs the package must be a member of the sysadmin or serveradmin server role on the destination server.</span></span>  
  
## <a name="configuration-of-the-transfer-error-messages-task"></a><span data-ttu-id="16c82-138">エラー メッセージ転送タスクの構成</span><span class="sxs-lookup"><span data-stu-id="16c82-138">Configuration of the Transfer Error Messages Task</span></span>  
 <span data-ttu-id="16c82-139">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="16c82-139">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="16c82-140">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="16c82-140">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="16c82-141">[[エラー メッセージ転送タスク エディター] &#40;[全般] ページ&#41;](../general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="16c82-141">[Transfer Error Messages Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md)</span></span>  
  
-   <span data-ttu-id="16c82-142">[[エラー メッセージ転送タスク エディター] &#40;[メッセージ] ページ&#41;](../transfer-error-messages-task-editor-messages-page.md)</span><span class="sxs-lookup"><span data-stu-id="16c82-142">[Transfer Error Messages Task Editor &#40;Messages Page&#41;](../transfer-error-messages-task-editor-messages-page.md)</span></span>  
  
-   <span data-ttu-id="16c82-143">[[式] ページ](../expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="16c82-143">[Expressions Page](../expressions/expressions-page.md)</span></span>  
  
 <span data-ttu-id="16c82-144">プログラムによってこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="16c82-144">For information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferErrorMessagesTask.TransferErrorMessagesTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="16c82-145">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="16c82-145">Related Tasks</span></span>  
 <span data-ttu-id="16c82-146">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="16c82-146">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="16c82-147">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="16c82-147">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="16c82-148">参照</span><span class="sxs-lookup"><span data-stu-id="16c82-148">See Also</span></span>  
 <span data-ttu-id="16c82-149">[Integration Services タスク](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="16c82-149">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="16c82-150">制御フロー</span><span class="sxs-lookup"><span data-stu-id="16c82-150">Control Flow</span></span>](control-flow.md)  
  
  
