---
title: '[WMI イベント監視タスクエディター] ([WMI オプション] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmieventwatcher.wmiquery.f1
helpviewer_keywords:
- WMI Event Watcher Task Editor
ms.assetid: 525f3de7-a021-4e52-9939-3a83c88f131a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d7d95501f6442df3723261c970c7a90f48cbdc87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718410"
---
# <a name="wmi-event-watcher-task-editor-wmi-options-page"></a><span data-ttu-id="e0b06-102">[WMI イベント監視タスク エディター] ([WMI オプション] ページ)</span><span class="sxs-lookup"><span data-stu-id="e0b06-102">WMI Event Watcher Task Editor (WMI Options Page)</span></span>
  <span data-ttu-id="e0b06-103">**[WMI イベント監視タスク エディター]** ダイアログ ボックスの **[WMI オプション]** ページを使用すると、WQL (Windows Management Instrumentation Query Language) クエリのソースや、WMI イベント監視タスクがどのように WMI (Microsoft Windows Instrumentation) イベントに応答するかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e0b06-103">Use the **WMI Options** page of the **WMI Event Watcher Task Editor** dialog box to specify the source of the Windows Management Instrumentation Query Language (WQL) query and how the WMI Event Watcher task responds to Microsoft Windows Instrumentation (WMI) events.</span></span>  
  
 <span data-ttu-id="e0b06-104">このタスクの詳細については、「 [WMI Event Watcher Task](control-flow/wmi-event-watcher-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0b06-104">To learn about this task, see [WMI Event Watcher Task](control-flow/wmi-event-watcher-task.md).</span></span> <span data-ttu-id="e0b06-105">WQL (WMI Query Language) の詳細については、MSDN ライブラリにある Windows Management Instrumentation のトピック「 [WQL を使用したクエリ](https://go.microsoft.com/fwlink/?LinkId=79045)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0b06-105">For more information about WMI Query Language (WQL), see the Windows Management Instrumentation topic, [Querying with WQL](https://go.microsoft.com/fwlink/?LinkId=79045), in the MSDN Library.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="e0b06-106">静的オプション</span><span class="sxs-lookup"><span data-stu-id="e0b06-106">Static Options</span></span>  
 <span data-ttu-id="e0b06-107">**[WMIConnectionName]**</span><span class="sxs-lookup"><span data-stu-id="e0b06-107">**WMIConnectionName**</span></span>  
 <span data-ttu-id="e0b06-108">WMI 接続マネージャーを一覧から選択するか、[\<**New WMI Connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e0b06-108">Select a WMI connection manager in the list, or click \<**New WMI Connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="e0b06-109">**関連トピック:** [WMI 接続マネージャー](connection-manager/wmi-connection-manager.md)、[WMI 接続マネージャー エディター](../../2014/integration-services/wmi-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="e0b06-109">**Related Topics:** [WMI Connection Manager](connection-manager/wmi-connection-manager.md), [WMI Connection Manager Editor](../../2014/integration-services/wmi-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="e0b06-110">**[WQLQuerySourceType]**</span><span class="sxs-lookup"><span data-stu-id="e0b06-110">**WQLQuerySourceType**</span></span>  
 <span data-ttu-id="e0b06-111">タスクで実行する WQL クエリのソースの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="e0b06-111">Select the source type of the WQL query that the task runs.</span></span> <span data-ttu-id="e0b06-112">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="e0b06-112">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="e0b06-113">値</span><span class="sxs-lookup"><span data-stu-id="e0b06-113">Value</span></span>|<span data-ttu-id="e0b06-114">説明</span><span class="sxs-lookup"><span data-stu-id="e0b06-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e0b06-115">**[直接入力]**</span><span class="sxs-lookup"><span data-stu-id="e0b06-115">**Direct input**</span></span>|<span data-ttu-id="e0b06-116">ソースを WQL クエリに設定します。</span><span class="sxs-lookup"><span data-stu-id="e0b06-116">Set the source to a WQL query.</span></span> <span data-ttu-id="e0b06-117">この値を選択すると、動的オプションの **[WQLQuerySource]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0b06-117">Selecting this value displays the dynamic option, **WQLQuerySource**.</span></span>|  
|<span data-ttu-id="e0b06-118">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="e0b06-118">**File connection**</span></span>|<span data-ttu-id="e0b06-119">WQL クエリを含むファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="e0b06-119">Select a file that contains the WQL query.</span></span> <span data-ttu-id="e0b06-120">この値を選択すると、動的オプションの **[WQLQuerySource]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0b06-120">Selecting this value displays the dynamic option, **WQLQuerySource**.</span></span>|  
|<span data-ttu-id="e0b06-121">**変数**</span><span class="sxs-lookup"><span data-stu-id="e0b06-121">**Variable**</span></span>|<span data-ttu-id="e0b06-122">ソースを、WQL クエリを定義する変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="e0b06-122">Set the source to a variable that defines WQL query.</span></span> <span data-ttu-id="e0b06-123">この値を選択すると、動的オプションの **[WQLQuerySource]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0b06-123">Selecting this value displays the dynamic option, **WQLQuerySource**.</span></span>|  
  
 <span data-ttu-id="e0b06-124">**[ActionAtEvent]**</span><span class="sxs-lookup"><span data-stu-id="e0b06-124">**ActionAtEvent**</span></span>  
 <span data-ttu-id="e0b06-125">WMI イベントをログに記録すると共に [!INCLUDE[ssIS](../includes/ssis-md.md)] アクションを実行するか、単にイベントをログに記録するだけにするかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e0b06-125">Specify whether the WMI event logs the event and initiates an [!INCLUDE[ssIS](../includes/ssis-md.md)] action, or only logs the event.</span></span>  
  
 <span data-ttu-id="e0b06-126">**[AfterEvent]**</span><span class="sxs-lookup"><span data-stu-id="e0b06-126">**AfterEvent**</span></span>  
 <span data-ttu-id="e0b06-127">WMI イベントを受け取った後にタスクを成功または失敗させるか、イベントの発生をタスクで引き続き監視するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e0b06-127">Specify whether the task succeeds or fails after it receives the WMI event, or if the task continues watching for the event to occur again.</span></span>  
  
 <span data-ttu-id="e0b06-128">**[ActionAtTimeout]**</span><span class="sxs-lookup"><span data-stu-id="e0b06-128">**ActionAtTimeout**</span></span>  
 <span data-ttu-id="e0b06-129">WMI クエリのタイムアウトをログに記録すると共に [!INCLUDE[ssIS](../includes/ssis-md.md)] イベントを発生させるか、単にタイムアウトをログに記録するだけにするかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e0b06-129">Specify whether the task logs a WMI query time-out and initiates an [!INCLUDE[ssIS](../includes/ssis-md.md)] event in response, or only logs the time-out.</span></span>  
  
 <span data-ttu-id="e0b06-130">**[AfterTimeout]**</span><span class="sxs-lookup"><span data-stu-id="e0b06-130">**AfterTimeout**</span></span>  
 <span data-ttu-id="e0b06-131">タイムアウトに対してタスクを成功または失敗させるか、別のタイムアウトの発生をタスクで引き続き監視するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e0b06-131">Specify whether the task succeeds or fails in response to a time-out, or if the task continues watching for another time-out to recur.</span></span>  
  
 <span data-ttu-id="e0b06-132">**[NumberOfEvents]**</span><span class="sxs-lookup"><span data-stu-id="e0b06-132">**NumberOfEvents**</span></span>  
 <span data-ttu-id="e0b06-133">監視するイベントの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="e0b06-133">Specify the number of events to watch for.</span></span>  
  
 <span data-ttu-id="e0b06-134">**タイムアウト**</span><span class="sxs-lookup"><span data-stu-id="e0b06-134">**Timeout**</span></span>  
 <span data-ttu-id="e0b06-135">イベントが発生するのを待機する秒数を指定します。</span><span class="sxs-lookup"><span data-stu-id="e0b06-135">Specify the number of seconds to wait for the event to occur.</span></span> <span data-ttu-id="e0b06-136">値 0 は、タイムアウトを設定しないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="e0b06-136">A value of 0 means that no time-out is in effect.</span></span>  
  
## <a name="wqlquerysource-dynamic-options"></a><span data-ttu-id="e0b06-137">[WQLQuerySource] の動的オプション</span><span class="sxs-lookup"><span data-stu-id="e0b06-137">WQLQuerySource Dynamic Options</span></span>  
  
### <a name="wqlquerysource--direct-input"></a><span data-ttu-id="e0b06-138">[WQLQuerySource] = [直接入力]</span><span class="sxs-lookup"><span data-stu-id="e0b06-138">WQLQuerySource = Direct input</span></span>  
 <span data-ttu-id="e0b06-139">**[WQLQuerySource]**</span><span class="sxs-lookup"><span data-stu-id="e0b06-139">**WQLQuerySource**</span></span>  
 <span data-ttu-id="e0b06-140">クエリを指定します。または、参照ボタン ( [...] ) をクリックし、 **[WQL クエリ]** ダイアログ ボックスを使用してクエリを入力します。</span><span class="sxs-lookup"><span data-stu-id="e0b06-140">Provide a query, or click the ellipsis button (...) and enter a query using the **WQL Query** dialog box.</span></span>  
  
### <a name="wqlquerysource--file-connection"></a><span data-ttu-id="e0b06-141">[WQLQuerySource] = [ファイル接続]</span><span class="sxs-lookup"><span data-stu-id="e0b06-141">WQLQuerySource = File connection</span></span>  
 <span data-ttu-id="e0b06-142">**[WQLQuerySource]**</span><span class="sxs-lookup"><span data-stu-id="e0b06-142">**WQLQuerySource**</span></span>  
 <span data-ttu-id="e0b06-143">一覧でファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e0b06-143">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="e0b06-144">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="e0b06-144">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="wqlquerysource--variable"></a><span data-ttu-id="e0b06-145">[WQLQuerySource] = [変数]</span><span class="sxs-lookup"><span data-stu-id="e0b06-145">WQLQuerySource = Variable</span></span>  
 <span data-ttu-id="e0b06-146">**[WQLQuerySource]**</span><span class="sxs-lookup"><span data-stu-id="e0b06-146">**WQLQuerySource**</span></span>  
 <span data-ttu-id="e0b06-147">一覧で変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="e0b06-147">Select a variable in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="e0b06-148">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="e0b06-148">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0b06-149">参照</span><span class="sxs-lookup"><span data-stu-id="e0b06-149">See Also</span></span>  
 <span data-ttu-id="e0b06-150">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e0b06-150">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="e0b06-151">[[WMI イベント監視タスクエディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="e0b06-151">[WMI Event Watcher Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="e0b06-152">[[式] ページ](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="e0b06-152">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="e0b06-153">WMI データ リーダー タスク</span><span class="sxs-lookup"><span data-stu-id="e0b06-153">WMI Data Reader Task</span></span>](control-flow/wmi-data-reader-task.md)  
  
  
