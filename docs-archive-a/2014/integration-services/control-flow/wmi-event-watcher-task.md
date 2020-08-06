---
title: WMI イベント監視タスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmieventwatchertask.f1
helpviewer_keywords:
- WQL [Integration Services]
- WMI Event Watcher task [Integration Services]
ms.assetid: b5bb52e9-a77e-41e1-93f9-d4c3bc6b2c9a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: be20624e5ccdf665e6274f647c342498e9c0f0a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741154"
---
# <a name="wmi-event-watcher-task"></a><span data-ttu-id="ee5d7-102">WMI イベント監視タスク</span><span class="sxs-lookup"><span data-stu-id="ee5d7-102">WMI Event Watcher Task</span></span>
  <span data-ttu-id="ee5d7-103">WMI イベント監視タスクは、Windows Management Instrumentation Query Language (WQL) イベント クエリを使用して対象のイベントを指定することにより、Windows Management Instrumentation (WMI) イベントを監視します。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-103">The WMI Event Watcher task watches for a Windows Management Instrumentation (WMI) event using a Management Instrumentation Query Language (WQL) event query to specify events of interest.</span></span> <span data-ttu-id="ee5d7-104">WMI イベント監視タスクは、次の目的で使用できます。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-104">You can use the WMI Event Watcher task for the following purposes:</span></span>  
  
-   <span data-ttu-id="ee5d7-105">ファイルがフォルダーに追加されたという通知を待機し、ファイルの処理を開始します。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-105">Wait for notification that files have been added to a folder and then initiate the processing of the file.</span></span>  
  
-   <span data-ttu-id="ee5d7-106">サーバー上の利用可能なメモリが、指定した割合を下回った場合、ファイルを削除するパッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-106">Run a package that deletes files when the available memory on a server drops lower than a specified percentage.</span></span>  
  
-   <span data-ttu-id="ee5d7-107">アプリケーションのインストールを監視し、そのアプリケーションを使用するパッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-107">Watch for installation of an application, and then run a package that uses the application.</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="ee5d7-108">には、WMI 情報を読み取るタスクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-108">includes a task that reads WMI information.</span></span>  
  
 <span data-ttu-id="ee5d7-109">このタスクの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-109">For more information about this task, click the following topic:</span></span>  
  
-   [<span data-ttu-id="ee5d7-110">WMI データ リーダー タスク</span><span class="sxs-lookup"><span data-stu-id="ee5d7-110">WMI Data Reader Task</span></span>](wmi-data-reader-task.md)  
  
## <a name="wql-queries"></a><span data-ttu-id="ee5d7-111">WQL クエリ</span><span class="sxs-lookup"><span data-stu-id="ee5d7-111">WQL Queries</span></span>  
 <span data-ttu-id="ee5d7-112">WQL は SQL 言語仕様の 1 つで、WMI イベント通知やその他 WMI 固有の機能をサポートする拡張機能が付いています。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-112">WQL is a dialect of SQL with extensions to support WMI event notification and other WMI-specific features.</span></span> <span data-ttu-id="ee5d7-113">WQL の詳細については、 [MSDN ライブラリ](https://go.microsoft.com/fwlink/?linkid=62553)にある Windows Management Instrumentation のマニュアルをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-113">For more information about WQL, see the Windows Management Instrumentation documentation in the [MSDN Library](https://go.microsoft.com/fwlink/?linkid=62553).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ee5d7-114">WMI クラスは、Windows のバージョンによって異なります。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-114">WMI classes vary between versions of Windows.</span></span>  
  
 <span data-ttu-id="ee5d7-115">次のクエリは、CPU 使用率が 40% を超えた場合の通知を監視します。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-115">The following query watches for notification that the CPU use is more than 40 percent.</span></span>  
  
```  
SELECT * from __InstanceModificationEvent WITHIN 2 WHERE TargetInstance ISA 'Win32_Processor' and TargetInstance.LoadPercentage > 40  
```  
  
 <span data-ttu-id="ee5d7-116">次のクエリは、ファイルがフォルダーに追加された場合の通知を監視します。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-116">The following query watches for notification that a file has been added to a folder.</span></span>  
  
```  
SELECT * FROM __InstanceCreationEvent WITHIN 10 WHERE TargetInstance ISA "CIM_DirectoryContainsFile" and TargetInstance.GroupComponent= "Win32_Directory.Name=\"c:\\\\WMIFileWatcher\""   
```  
  
## <a name="custom-logging-messages-available-on-the-wmi-event-watcher-task"></a><span data-ttu-id="ee5d7-117">WMI イベント監視タスクで使用できるカスタム ログ メッセージ</span><span class="sxs-lookup"><span data-stu-id="ee5d7-117">Custom Logging Messages Available on the WMI Event Watcher Task</span></span>  
 <span data-ttu-id="ee5d7-118">次の表は、WMI イベント監視タスクのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-118">The following table lists the custom log entries for the WMI Event Watcher task.</span></span> <span data-ttu-id="ee5d7-119">詳しくは、「[Integration Services &#40;SSIS&#41; のログ記録](../performance/integration-services-ssis-logging.md)」と「[ログ記録用のカスタム メッセージ](../custom-messages-for-logging.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-119">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="ee5d7-120">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="ee5d7-120">Log entry</span></span>|<span data-ttu-id="ee5d7-121">説明</span><span class="sxs-lookup"><span data-stu-id="ee5d7-121">Description</span></span>|  
|---------------|-----------------|  
|`WMIEventWatcherEventOccurred`|<span data-ttu-id="ee5d7-122">タスクが監視しているイベントが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-122">Indicates that an event occurred that the task was monitoring.</span></span>|  
|`WMIEventWatcherTimedout`|<span data-ttu-id="ee5d7-123">タスクがタイムアウトしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-123">Indicates that the task timed out.</span></span>|  
|`WMIEventWatcherWatchingForWMIEvents`|<span data-ttu-id="ee5d7-124">タスクが WQL クエリの実行を開始したことを示します。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-124">Indicates that the task began to execute the WQL query.</span></span> <span data-ttu-id="ee5d7-125">このエントリには、クエリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-125">The entry includes the query.</span></span>|  
  
## <a name="configuration-of-the-wmi-event-watcher-task"></a><span data-ttu-id="ee5d7-126">WMI イベント監視タスクの構成</span><span class="sxs-lookup"><span data-stu-id="ee5d7-126">Configuration of the WMI Event Watcher Task</span></span>  
 <span data-ttu-id="ee5d7-127">WMI データ リーダー タスクは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-127">You can configure the WMI Data Reader task in the following ways:</span></span>  
  
-   <span data-ttu-id="ee5d7-128">使用する WMI 接続マネージャーを指定します。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-128">Specify the WMI connection manager to use.</span></span>  
  
-   <span data-ttu-id="ee5d7-129">WQL クエリの実行元を指定します。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-129">Specify the source of the WQL query.</span></span> <span data-ttu-id="ee5d7-130">実行元には、タスクの外部の変数またはファイルを設定できます。また、クエリはタスクのプロパティ内に格納できます。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-130">The source can be external to the task, a variable or a file, or the query can be stored in a task property.</span></span>  
  
-   <span data-ttu-id="ee5d7-131">WMI イベントが発生したときにタスクが実行するアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-131">Specify the action that the task takes when the WMI event occurs.</span></span> <span data-ttu-id="ee5d7-132">イベント通知およびイベント後の状態のログが記録できます。または、WMI イベント、通知、およびイベント後の状態に関連する情報を提供する、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のカスタム イベントを発生させることができます。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-132">You can log the event notification and the status after the event, or raise custom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] events that provide information associated with the WMI event, the notification, and the status after the event.</span></span>  
  
-   <span data-ttu-id="ee5d7-133">イベントに対するタスクの応答方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-133">Define how the task responds to the event.</span></span> <span data-ttu-id="ee5d7-134">タスクは、イベントに応じて、成功または失敗するように構成できます。または、単にイベントを再度監視するように構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-134">The task can be configured to succeed or fail, depending on the event, or the task can just watch for the event again.</span></span>  
  
-   <span data-ttu-id="ee5d7-135">WMI クエリがタイムアウトしたときに、タスクが実行するアクションを指定します。タイムアウトとタイムアウト後の状態のログを記録できます。または、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のカスタム イベントを発生させ、WMI イベントのタイムアウトを示し、タイムアウトとタイムアウトの状態のログを記録できます。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-135">Specify the action the task takes when the WMI query times out. You can log the time-out and the status after time-out, or raise a custom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] event, indicating that the WMI event timed out and logging the time-out and time-out status.</span></span>  
  
-   <span data-ttu-id="ee5d7-136">タイムアウトに対するタスクの応答方法を定義します。タスクは成功または失敗するように構成できます。または、単にイベントを再度監視するように構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-136">Define how the task responds to the time-out. The task can be configured to succeed or fail, or the task can just watch for the event again.</span></span>  
  
-   <span data-ttu-id="ee5d7-137">タスクがイベントを監視する回数を指定します。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-137">Specify the number of times the task watches for the event.</span></span>  
  
-   <span data-ttu-id="ee5d7-138">タイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-138">Specify the time-out.</span></span>  
  
 <span data-ttu-id="ee5d7-139">監視元がファイルの場合、WMI イベント監視タスクは、ファイル接続マネージャーを使用してファイルに接続します。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-139">If the source is a file, the WMI Event Watcher task uses a File connection manager to connect to the file.</span></span> <span data-ttu-id="ee5d7-140">詳しくは、「 [フラット ファイル接続マネージャー](../connection-manager/file-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-140">For more information, see [Flat File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="ee5d7-141">WMI イベント監視タスクは、WMI 接続マネージャーを使用して、WMI 情報を読み取るサーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-141">The WMI Event Watcher task uses a WMI connection manager to connect to the server from which it reads WMI information.</span></span> <span data-ttu-id="ee5d7-142">詳細については、「 [WMI 接続マネージャー](../connection-manager/wmi-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-142">For more information, see [WMI Connection Manager](../connection-manager/wmi-connection-manager.md).</span></span>  
  
 <span data-ttu-id="ee5d7-143">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-143">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="ee5d7-144">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-144">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="ee5d7-145">[[WMI イベント監視タスク エディター] &#40;[全般] ページ&#41;](../general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="ee5d7-145">[WMI Event Watcher Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md)</span></span>  
  
-   <span data-ttu-id="ee5d7-146">[[WMI イベント監視タスク エディター] &#40;[WMI オプション] ページ&#41;](../wmi-event-watcher-task-editor-wmi-options-page.md)</span><span class="sxs-lookup"><span data-stu-id="ee5d7-146">[WMI Event Watcher Task Editor &#40;WMI Options Page&#41;](../wmi-event-watcher-task-editor-wmi-options-page.md)</span></span>  
  
-   <span data-ttu-id="ee5d7-147">[[式] ページ](../expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="ee5d7-147">[Expressions Page](../expressions/expressions-page.md)</span></span>  
  
 <span data-ttu-id="ee5d7-148">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-148">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="ee5d7-149">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="ee5d7-149">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-wmi-event-watcher-task"></a><span data-ttu-id="ee5d7-150">プログラムによる WMI イベント監視タスクの構成</span><span class="sxs-lookup"><span data-stu-id="ee5d7-150">Programmatic Configuration of the WMI Event Watcher Task</span></span>  
 <span data-ttu-id="ee5d7-151">プログラムによってこれらのプロパティを設定する方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee5d7-151">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiEventWatcherTask.WmiEventWatcherTask>  
  
  
