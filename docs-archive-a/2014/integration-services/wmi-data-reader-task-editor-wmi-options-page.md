---
title: '[WMI データリーダータスクエディター] ([WMI オプション] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmidatareadertask.wmiquery.f1
helpviewer_keywords:
- WMI Data Reader Task Editor
ms.assetid: 4b8d4716-882d-41b0-b77e-e0e2741a2cd5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cfb28e7f8f352f708085bf664757391a05869752
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644514"
---
# <a name="wmi-data-reader-task-editor-wmi-options-page"></a><span data-ttu-id="d9075-102">[WMI データ リーダー タスク エディター] ([WMI オプション] ページ)</span><span class="sxs-lookup"><span data-stu-id="d9075-102">WMI Data Reader Task Editor (WMI Options Page)</span></span>
  <span data-ttu-id="d9075-103">**[WMI データ リーダー タスク エディター]** ダイアログ ボックスの **[WMI オプション]** ページを使用すると、WQL (Windows Management Instrumentation Query Language) クエリのソースおよびクエリ結果の出力先を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d9075-103">Use the **WMI Options** page of the **WMI Data Reader Task Editor** dialog box to specify the source of the Windows Management Instrumentation Query Language (WQL) query and the destination of the query result.</span></span>  
  
 <span data-ttu-id="d9075-104">このタスクの詳細については、「 [WMI Data Reader Task](control-flow/wmi-data-reader-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9075-104">To learn about this task, see [WMI Data Reader Task](control-flow/wmi-data-reader-task.md).</span></span> <span data-ttu-id="d9075-105">WQL (WMI Query Language) の詳細については、MSDN ライブラリにある Windows Management Instrumentation のトピック「 [WQL を使用したクエリ](https://go.microsoft.com/fwlink/?LinkId=79045)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9075-105">For more information about WMI Query Language (WQL), see the Windows Management Instrumentation topic, [Querying with WQL](https://go.microsoft.com/fwlink/?LinkId=79045), in the MSDN Library.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="d9075-106">静的オプション</span><span class="sxs-lookup"><span data-stu-id="d9075-106">Static Options</span></span>  
 <span data-ttu-id="d9075-107">**[WMIConnectionName]**</span><span class="sxs-lookup"><span data-stu-id="d9075-107">**WMIConnectionName**</span></span>  
 <span data-ttu-id="d9075-108">WMI 接続マネージャーを一覧から選択するか、[\<**New WMI Connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d9075-108">Select a WMI connection manager in the list, or click \<**New WMI Connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d9075-109">**関連トピック:** [WMI 接続マネージャー](connection-manager/wmi-connection-manager.md)、[WMI 接続マネージャー エディター](../../2014/integration-services/wmi-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="d9075-109">**Related Topics:** [WMI Connection Manager](connection-manager/wmi-connection-manager.md), [WMI Connection Manager Editor](../../2014/integration-services/wmi-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="d9075-110">**[WQLQuerySourceType]**</span><span class="sxs-lookup"><span data-stu-id="d9075-110">**WQLQuerySourceType**</span></span>  
 <span data-ttu-id="d9075-111">タスクで実行する WQL クエリのソースの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="d9075-111">Select the source type of the WQL query that the task runs.</span></span> <span data-ttu-id="d9075-112">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="d9075-112">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d9075-113">値</span><span class="sxs-lookup"><span data-stu-id="d9075-113">Value</span></span>|<span data-ttu-id="d9075-114">説明</span><span class="sxs-lookup"><span data-stu-id="d9075-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d9075-115">**[直接入力]**</span><span class="sxs-lookup"><span data-stu-id="d9075-115">**Direct input**</span></span>|<span data-ttu-id="d9075-116">ソースを WQL クエリに設定します。</span><span class="sxs-lookup"><span data-stu-id="d9075-116">Set the source to a WQL query.</span></span> <span data-ttu-id="d9075-117">この値を選択すると、動的オプションの **[WQLQuerySourceType]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d9075-117">Selecting this value displays the dynamic option **WQLQuerySourceType**.</span></span>|  
|<span data-ttu-id="d9075-118">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="d9075-118">**File connection**</span></span>|<span data-ttu-id="d9075-119">WQL クエリを含むファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="d9075-119">Select a file that contains the WQL query.</span></span> <span data-ttu-id="d9075-120">この値を選択すると、動的オプションの **[WQLQuerySourceType]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d9075-120">Selecting this value displays the dynamic option **WQLQuerySourceType**.</span></span>|  
|<span data-ttu-id="d9075-121">**変数**</span><span class="sxs-lookup"><span data-stu-id="d9075-121">**Variable**</span></span>|<span data-ttu-id="d9075-122">WQL クエリを定義する変数に、ソースを設定します。</span><span class="sxs-lookup"><span data-stu-id="d9075-122">Set the source to a variable that defines the WQL query.</span></span> <span data-ttu-id="d9075-123">この値を選択すると、動的オプションの **[WQLQuerySourceType]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d9075-123">Selecting this value displays the dynamic option **WQLQuerySourceType**.</span></span>|  
  
 <span data-ttu-id="d9075-124">**[OutputType]**</span><span class="sxs-lookup"><span data-stu-id="d9075-124">**OutputType**</span></span>  
 <span data-ttu-id="d9075-125">データ テーブル、プロパティ値、またはプロパティ名と値のいずれを出力に含めるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d9075-125">Specify whether the output should be a data table, property value, or property name and value.</span></span>  
  
 <span data-ttu-id="d9075-126">**[OverwriteDestination]**</span><span class="sxs-lookup"><span data-stu-id="d9075-126">**OverwriteDestination**</span></span>  
 <span data-ttu-id="d9075-127">出力先のファイルまたは変数内の元のデータを変更しないか、上書きするか、データを追加するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d9075-127">Specifies whether to keep, overwrite, or append to the original data in the destination file or variable.</span></span>  
  
 <span data-ttu-id="d9075-128">**[DestinationType]**</span><span class="sxs-lookup"><span data-stu-id="d9075-128">**DestinationType**</span></span>  
 <span data-ttu-id="d9075-129">タスクで実行する WQL クエリの出力先の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="d9075-129">Select the destination type of the WQL query that the task runs.</span></span> <span data-ttu-id="d9075-130">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="d9075-130">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d9075-131">値</span><span class="sxs-lookup"><span data-stu-id="d9075-131">Value</span></span>|<span data-ttu-id="d9075-132">説明</span><span class="sxs-lookup"><span data-stu-id="d9075-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d9075-133">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="d9075-133">**File connection**</span></span>|<span data-ttu-id="d9075-134">WQL クエリの結果を保存するファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="d9075-134">Select a file to save the results of the WQL query in.</span></span> <span data-ttu-id="d9075-135">この値を選択すると、動的オプションの **[DestinationType]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d9075-135">Selecting this value displays the dynamic option, **DestinationType**.</span></span>|  
|<span data-ttu-id="d9075-136">**変数**</span><span class="sxs-lookup"><span data-stu-id="d9075-136">**Variable**</span></span>|<span data-ttu-id="d9075-137">WQL クエリの結果を保存する変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="d9075-137">Set the variable to store the results of the WQL query in.</span></span> <span data-ttu-id="d9075-138">この値を選択すると、動的オプションの **[DestinationType]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d9075-138">Selecting this value displays the dynamic option, **DestinationType**.</span></span>|  
  
## <a name="wqlquerysourcetype-dynamic-options"></a><span data-ttu-id="d9075-139">[WQLQuerySourceType] 動的オプション</span><span class="sxs-lookup"><span data-stu-id="d9075-139">WQLQuerySourceType Dynamic Options</span></span>  
  
### <a name="wqlquerysourcetype--direct-input"></a><span data-ttu-id="d9075-140">[WQLQuerySourceType] = [直接入力]</span><span class="sxs-lookup"><span data-stu-id="d9075-140">WQLQuerySourceType = Direct input</span></span>  
 <span data-ttu-id="d9075-141">**[WQLQuerySource]**</span><span class="sxs-lookup"><span data-stu-id="d9075-141">**WQLQuerySource**</span></span>  
 <span data-ttu-id="d9075-142">クエリを指定します。または、参照 ( [...] ) をクリックし、 **[WQL クエリ]** ダイアログ ボックスを使用してクエリを入力します。</span><span class="sxs-lookup"><span data-stu-id="d9075-142">Provide a query, or click the ellipsis (...) and enter a query using the **WQL Query** dialog box.</span></span>  
  
### <a name="wqlquerysourcetype--file-connection"></a><span data-ttu-id="d9075-143">[WQLQuerySourceType] = [ファイル接続]</span><span class="sxs-lookup"><span data-stu-id="d9075-143">WQLQuerySourceType = File connection</span></span>  
 <span data-ttu-id="d9075-144">**[WQLQuerySource]**</span><span class="sxs-lookup"><span data-stu-id="d9075-144">**WQLQuerySource**</span></span>  
 <span data-ttu-id="d9075-145">一覧でファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d9075-145">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d9075-146">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="d9075-146">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="wqlquerysourcetype--variable"></a><span data-ttu-id="d9075-147">[WQLQuerySourceType] = [変数]</span><span class="sxs-lookup"><span data-stu-id="d9075-147">WQLQuerySourceType = Variable</span></span>  
 <span data-ttu-id="d9075-148">**[WQLQuerySource]**</span><span class="sxs-lookup"><span data-stu-id="d9075-148">**WQLQuerySource**</span></span>  
 <span data-ttu-id="d9075-149">一覧で変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="d9075-149">Select a variable in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="d9075-150">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="d9075-150">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="destinationtype-dynamic-options"></a><span data-ttu-id="d9075-151">[DestinationType] 動的オプション</span><span class="sxs-lookup"><span data-stu-id="d9075-151">DestinationType Dynamic Options</span></span>  
  
### <a name="destinationtype--file-connection"></a><span data-ttu-id="d9075-152">[DestinationType] = [ファイル接続]</span><span class="sxs-lookup"><span data-stu-id="d9075-152">DestinationType = File connection</span></span>  
 <span data-ttu-id="d9075-153">**宛先**</span><span class="sxs-lookup"><span data-stu-id="d9075-153">**Destination**</span></span>  
 <span data-ttu-id="d9075-154">一覧でファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d9075-154">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d9075-155">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="d9075-155">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="destinationtype--variable"></a><span data-ttu-id="d9075-156">[DestinationType] = [変数]</span><span class="sxs-lookup"><span data-stu-id="d9075-156">DestinationType = Variable</span></span>  
 <span data-ttu-id="d9075-157">**宛先**</span><span class="sxs-lookup"><span data-stu-id="d9075-157">**Destination**</span></span>  
 <span data-ttu-id="d9075-158">一覧で変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="d9075-158">Select a variable in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="d9075-159">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="d9075-159">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9075-160">参照</span><span class="sxs-lookup"><span data-stu-id="d9075-160">See Also</span></span>  
 <span data-ttu-id="d9075-161">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d9075-161">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="d9075-162">[[WMI データリーダータスクエディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="d9075-162">[WMI Data Reader Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="d9075-163">[[式] ページ](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="d9075-163">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="d9075-164">WMI イベント監視タスク</span><span class="sxs-lookup"><span data-stu-id="d9075-164">WMI Event Watcher Task</span></span>](control-flow/wmi-event-watcher-task.md)  
  
  
