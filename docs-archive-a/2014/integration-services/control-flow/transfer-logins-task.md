---
title: ログイン転送タスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferloginstask.f1
helpviewer_keywords:
- Transfer Logins task [Integration Services]
ms.assetid: 1df60fd6-c019-405d-8155-c330dbac2cc1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d42d39b6cc7c2f350e3e3adc774be23934981369
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631174"
---
# <a name="transfer-logins-task"></a><span data-ttu-id="5aa41-102">ログイン転送タスク</span><span class="sxs-lookup"><span data-stu-id="5aa41-102">Transfer Logins Task</span></span>
  <span data-ttu-id="5aa41-103">ログイン転送タスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス間で 1 つ以上のログインを転送します。</span><span class="sxs-lookup"><span data-stu-id="5aa41-103">The Transfer Logins task transfers one or more logins between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="transfer-logins-between-instances-of-sql-server"></a><span data-ttu-id="5aa41-104">SQL Server のインスタンス間でのログインの転送</span><span class="sxs-lookup"><span data-stu-id="5aa41-104">Transfer Logins Between Instances of SQL Server</span></span>  
 <span data-ttu-id="5aa41-105">ログイン転送タスクでは、転送元または転送先として、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をサポートします。</span><span class="sxs-lookup"><span data-stu-id="5aa41-105">The Transfer Logins task supports a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source and destination.</span></span>  
  
## <a name="events"></a><span data-ttu-id="5aa41-106">events</span><span class="sxs-lookup"><span data-stu-id="5aa41-106">Events</span></span>  
 <span data-ttu-id="5aa41-107">ログイン転送タスクでは、転送されたログインの数を報告する情報イベントと、ログインが上書きされた場合の警告イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="5aa41-107">The task raises an information event that reports the number of logins transferred and a warning event when a login is overwritten.</span></span>  
  
 <span data-ttu-id="5aa41-108">ログインの転送の進捗状況は報告されません。0% または 100% 完了した場合のみ報告されます。</span><span class="sxs-lookup"><span data-stu-id="5aa41-108">The Transfer Logins task does not report incremental progress of the login transfer; it reports only 0% and 100 % completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="5aa41-109">実行値</span><span class="sxs-lookup"><span data-stu-id="5aa41-109">Execution Value</span></span>  
 <span data-ttu-id="5aa41-110">タスクの `ExecutionValue` プロパティで定義する実行値は、転送されたログインの数を返します。</span><span class="sxs-lookup"><span data-stu-id="5aa41-110">The execution value, defined in the `ExecutionValue` property of the task, returns the number of logins transferred.</span></span> <span data-ttu-id="5aa41-111">ログイン転送タスクの `ExecValueVariable` プロパティにユーザー定義変数を割り当てると、パッケージの他のオブジェクトからログインの転送に関する情報を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="5aa41-111">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer Logins task, information about the login transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="5aa41-112">詳細については、「[Integration Services &#40;SSIS&#41; の変数](../integration-services-ssis-variables.md)」と「[パッケージで変数を使用する](../use-variables-in-packages.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5aa41-112">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="5aa41-113">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="5aa41-113">Log Entries</span></span>  
 <span data-ttu-id="5aa41-114">ログイン転送タスクには、次のようなカスタム ログ エントリがあります。</span><span class="sxs-lookup"><span data-stu-id="5aa41-114">The Transfer Logins task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="5aa41-115">TransferLoginsTaskStarTransferringObjects   転送が開始されたことを報告するログ エントリです。</span><span class="sxs-lookup"><span data-stu-id="5aa41-115">TransferLoginsTaskStarTransferringObjects    This log entry reports the transfer has started.</span></span> <span data-ttu-id="5aa41-116">ログ エントリには、開始時刻が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5aa41-116">The log entry includes the start time.</span></span>  
  
-   <span data-ttu-id="5aa41-117">TransferLoginsTaskFinishedTransferringObjects   転送が完了したことを報告するログ エントリです。</span><span class="sxs-lookup"><span data-stu-id="5aa41-117">TransferLoginsTaskFinishedTransferringObjects   This log entry reports the transfer has completed.</span></span> <span data-ttu-id="5aa41-118">ログ エントリには、終了時刻が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5aa41-118">The log entry includes the end time.</span></span>  
  
 <span data-ttu-id="5aa41-119">また、`OnInformation` イベントのログ エントリは転送されたログインの数を報告し、`OnWarning` イベントのログ エントリは転送先でログインが上書きされると書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="5aa41-119">In addition, a log entry for the `OnInformation` event reports the number of logins that were transferred, and a log entry for the `OnWarning` event is written for each login on the destination that is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="5aa41-120">セキュリティとアクセス許可</span><span class="sxs-lookup"><span data-stu-id="5aa41-120">Security and Permissions</span></span>  
 <span data-ttu-id="5aa41-121">転送元サーバーのログインを参照し、転送先サーバーにログインを作成するユーザーは、両方のサーバーのサーバー ロール sysadmin のメンバーでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="5aa41-121">To browse logins on the source server and to create logins on the destination server, the user must be a member of the sysadmin server role on both servers.</span></span>  
  
## <a name="configuration-of-the-transfer-logins-task"></a><span data-ttu-id="5aa41-122">ログイン転送タスクの構成</span><span class="sxs-lookup"><span data-stu-id="5aa41-122">Configuration of the Transfer Logins Task</span></span>  
 <span data-ttu-id="5aa41-123">ログイン転送タスクは、すべてのログイン、指定したログインのみ、または指定したデータベースにアクセスしたすべてのログインを転送するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="5aa41-123">The Transfer Logins task can be configured to transfer all logins, only specified logins, or all logins that have access to specified databases only.</span></span> <span data-ttu-id="5aa41-124">sa ログインは転送できません。</span><span class="sxs-lookup"><span data-stu-id="5aa41-124">The sa login cannot be transferred.</span></span> <span data-ttu-id="5aa41-125">sa ログインの名前は変更できますが、名前を変更した sa ログインを転送することはできません。</span><span class="sxs-lookup"><span data-stu-id="5aa41-125">The sa login may be renamed; however, the renamed sa login cannot be transferred either.</span></span>  
  
 <span data-ttu-id="5aa41-126">また、ログインに関連付けられているセキュリティ識別子 (SID) をコピーするかどうかも指定できます。</span><span class="sxs-lookup"><span data-stu-id="5aa41-126">You can also indicate whether the task copies the security identifiers (SIDs) associated with the logins.</span></span> <span data-ttu-id="5aa41-127">ログイン転送タスクをデータベース転送タスクと共に使用する場合、SID を転送先にコピーする必要があります。コピーしない場合、転送したログインが転送先データベースで認識されません。</span><span class="sxs-lookup"><span data-stu-id="5aa41-127">If the Transfer Logins task is used in conjunction with the Transfer Database task the SIDs must be copied to the destination; otherwise, the transferred logins are not recognized by the destination database.</span></span>  
  
 <span data-ttu-id="5aa41-128">転送先では、転送されたログインは無効にされ、ランダムなパスワードが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="5aa41-128">At the destination, the transferred logins are disabled and assigned random passwords.</span></span> <span data-ttu-id="5aa41-129">ログインを使用する前に、転送先サーバーの sysadmin ロールのメンバーがパスワードを変更して、ログインを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5aa41-129">A member of the sysadmin role on the destination server must change the passwords and enable the logins before the logins can be used.</span></span>  
  
 <span data-ttu-id="5aa41-130">転送するログインが既に転送先に存在している場合もあります。</span><span class="sxs-lookup"><span data-stu-id="5aa41-130">The logins to be transferred may already exist on the destination.</span></span> <span data-ttu-id="5aa41-131">ログイン転送タスクでは、既存のログインの処理を次のように構成できます。</span><span class="sxs-lookup"><span data-stu-id="5aa41-131">The Transfer Logins task can be configured to handle existing logins in the following ways:</span></span>  
  
-   <span data-ttu-id="5aa41-132">既存のログインを上書きします。</span><span class="sxs-lookup"><span data-stu-id="5aa41-132">Overwrite existing logins.</span></span>  
  
-   <span data-ttu-id="5aa41-133">重複するログインが存在する場合、タスクを失敗とします。</span><span class="sxs-lookup"><span data-stu-id="5aa41-133">Fail the task when duplicate logins exist.</span></span>  
  
-   <span data-ttu-id="5aa41-134">重複するログインをスキップします。</span><span class="sxs-lookup"><span data-stu-id="5aa41-134">Skip duplicate logins.</span></span>  
  
 <span data-ttu-id="5aa41-135">ログイン転送タスクは実行時に、2 つの SMO 接続マネージャーを使用して、転送元および転送先サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="5aa41-135">At run time, the Transfer Logins task connects to the source and destination servers by using two SMO connection managers.</span></span> <span data-ttu-id="5aa41-136">SMO 接続マネージャーの構成はログイン転送タスクとは別に行い、ログイン転送タスクは SMO 接続マネージャーを参照します。</span><span class="sxs-lookup"><span data-stu-id="5aa41-136">The SMO connection managers are configured separately from the Transfer Logins task, and then referenced in the Transfer Logins task.</span></span> <span data-ttu-id="5aa41-137">SMO 接続マネージャーは、サーバーと、サーバーに接続する際に使用する認証モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="5aa41-137">The SMO connection managers specify the server and the authentication mode to use when accessing the server.</span></span> <span data-ttu-id="5aa41-138">詳細については、「 [SMO 接続マネージャー](../connection-manager/smo-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5aa41-138">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
 <span data-ttu-id="5aa41-139">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="5aa41-139">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="5aa41-140">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5aa41-140">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="5aa41-141">[[ログイン転送タスク エディター] ([全般] ページ)](../general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="5aa41-141">[Transfer Logins Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md)</span></span>  
  
-   <span data-ttu-id="5aa41-142">[[ログイン転送タスク エディター] ([ログイン] ページ)](../transfer-logins-task-editor-logins-page.md)</span><span class="sxs-lookup"><span data-stu-id="5aa41-142">[Transfer Logins Task Editor &#40;Logins Page&#41;](../transfer-logins-task-editor-logins-page.md)</span></span>  
  
-   <span data-ttu-id="5aa41-143">[[式] ページ](../expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="5aa41-143">[Expressions Page](../expressions/expressions-page.md)</span></span>  
  
 <span data-ttu-id="5aa41-144">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5aa41-144">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="5aa41-145">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="5aa41-145">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-transfer-logins-task"></a><span data-ttu-id="5aa41-146">プログラムによるログイン転送タスクの構成</span><span class="sxs-lookup"><span data-stu-id="5aa41-146">Programmatic Configuration of the Transfer Logins Task</span></span>  
 <span data-ttu-id="5aa41-147">プログラムによってこれらのプロパティを設定する方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5aa41-147">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferLoginsTask.TransferLoginsTask>  
  
  
