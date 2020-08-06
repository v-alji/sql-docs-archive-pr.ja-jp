---
title: WMI データ リーダー タスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmidatareadertask.f1
helpviewer_keywords:
- WQL [Integration Services]
- WMI Data Reader task [Integration Services]
ms.assetid: dae57067-0275-4ac3-8f34-1b9d169f1112
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1d2f16a28e8b6c94c7275468dedb6d2dfec76d8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633253"
---
# <a name="wmi-data-reader-task"></a><span data-ttu-id="41218-102">WMI データ リーダー タスク</span><span class="sxs-lookup"><span data-stu-id="41218-102">WMI Data Reader Task</span></span>
  <span data-ttu-id="41218-103">WMI データ リーダー タスクは、WQL (Windows Management Instrumentation Query Language) を使用してクエリを実行し、コンピューター システムに関する WMI から情報を返します。</span><span class="sxs-lookup"><span data-stu-id="41218-103">The WMI Data Reader task runs queries using the Windows Management Instrumentation (WMI) Query Language that returns information from WMI about a computer system.</span></span> <span data-ttu-id="41218-104">WMI データ リーダー タスクは、次の目的で使用できます。</span><span class="sxs-lookup"><span data-stu-id="41218-104">You can use the WMI Data Reader task for the following purposes:</span></span>  
  
-   <span data-ttu-id="41218-105">ローカルまたはリモート コンピューター上の Windows イベント ログのクエリを実行し、その情報をファイルまたは変数に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="41218-105">Query the Windows event logs on a local or remote computer and write the information to a file or variable.</span></span>  
  
-   <span data-ttu-id="41218-106">ハードウェア コンポーネントの存在、状態、またはプロパティに関する情報を取得し、この情報を使用して制御フロー内の他のタスクを実行するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="41218-106">Obtain information about the presence, state, or properties of hardware components, and then use this information to determine whether other tasks in the control flow should run.</span></span>  
  
-   <span data-ttu-id="41218-107">アプリケーションの一覧を取得し、インストールされている各アプリケーションのバージョンを判別します。</span><span class="sxs-lookup"><span data-stu-id="41218-107">Get a list of applications and determine what version of each application is installed.</span></span>  
  
 <span data-ttu-id="41218-108">WMI データ リーダー タスクは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="41218-108">You can configure the WMI Data Reader task in the following ways:</span></span>  
  
-   <span data-ttu-id="41218-109">使用する WMI 接続マネージャーを指定します。</span><span class="sxs-lookup"><span data-stu-id="41218-109">Specify the WMI connection manager to use.</span></span>  
  
-   <span data-ttu-id="41218-110">WQL クエリの実行元を指定します。</span><span class="sxs-lookup"><span data-stu-id="41218-110">Specify the source of the WQL query.</span></span> <span data-ttu-id="41218-111">このクエリは、タスクのプロパティ内に格納できます。または、タスク外の変数またはファイル内にも格納できます。</span><span class="sxs-lookup"><span data-stu-id="41218-111">The query can be stored in a task property, or the query can be stored outside the task, in a variable or a file.</span></span>  
  
-   <span data-ttu-id="41218-112">WQL クエリ結果の形式を定義します。</span><span class="sxs-lookup"><span data-stu-id="41218-112">Define the format of the WQL query results.</span></span> <span data-ttu-id="41218-113">このタスクでは、テーブル、プロパティの名前と値のペア、またはプロパティ値の形式がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="41218-113">The task supports a table, property name/value pair, or property value format.</span></span>  
  
-   <span data-ttu-id="41218-114">クエリの実行先を指定します。</span><span class="sxs-lookup"><span data-stu-id="41218-114">Specify the destination of the query.</span></span> <span data-ttu-id="41218-115">この実行先には、変数またはファイルを設定できます。</span><span class="sxs-lookup"><span data-stu-id="41218-115">The destination can be a variable or a file.</span></span>  
  
-   <span data-ttu-id="41218-116">クエリの実行先で、上書き、保持、または追加のいずれを行うかを示します。</span><span class="sxs-lookup"><span data-stu-id="41218-116">Indicate whether the query destination is overwritten, kept, or appended.</span></span>  
  
 <span data-ttu-id="41218-117">実行元または実行先がファイルの場合、WMI データ リーダー タスクは、ファイル接続マネージャーを使用してファイルに接続します。</span><span class="sxs-lookup"><span data-stu-id="41218-117">If the source or destination is a file, the WMI Data Reader task uses a File connection manager to connect to the file.</span></span> <span data-ttu-id="41218-118">詳しくは、「 [フラット ファイル接続マネージャー](../connection-manager/file-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="41218-118">For more information, see [Flat File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="41218-119">WMI データ リーダー タスクは、WMI 接続マネージャーを使用して、WMI 情報を読み取るサーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="41218-119">The WMI Data Reader task uses a WMI connection manager to connect to the server from which it reads WMI information.</span></span> <span data-ttu-id="41218-120">詳細については、「 [WMI 接続マネージャー](../connection-manager/wmi-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="41218-120">For more information, see [WMI Connection Manager](../connection-manager/wmi-connection-manager.md).</span></span>  
  
## <a name="wql-query"></a><span data-ttu-id="41218-121">WQL クエリ</span><span class="sxs-lookup"><span data-stu-id="41218-121">WQL Query</span></span>  
 <span data-ttu-id="41218-122">WQL は SQL 言語仕様の 1 つで、WMI イベント通知やその他 WMI 固有の機能をサポートする拡張機能が付いています。</span><span class="sxs-lookup"><span data-stu-id="41218-122">WQL is a dialect of SQL with extensions to support WMI event notification and other WMI-specific features.</span></span> <span data-ttu-id="41218-123">WQL の詳細については、 [MSDN ライブラリ](https://go.microsoft.com/fwlink/?linkid=7022)にある Windows Management Instrumentation のマニュアルをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="41218-123">For more information about WQL, see the Windows Management Instrumentation documentation in the [MSDN Library](https://go.microsoft.com/fwlink/?linkid=7022).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="41218-124">WMI クラスは、Windows のバージョンによって異なります。</span><span class="sxs-lookup"><span data-stu-id="41218-124">WMI classes vary between versions of Windows.</span></span>  
  
 <span data-ttu-id="41218-125">次の WQL クエリは、アプリケーション ログ イベント内のエントリを返します。</span><span class="sxs-lookup"><span data-stu-id="41218-125">The following WQL query returns entries in the Application log event.</span></span>  
  
```  
SELECT * FROM Win32_NTLogEvent WHERE LogFile = 'Application' AND (SourceName='SQLISService' OR SourceName='SQLISPackage') AND TimeGenerated > '20050117'  
```  
  
 <span data-ttu-id="41218-126">次の WQL クエリは、論理ディスク情報を返します。</span><span class="sxs-lookup"><span data-stu-id="41218-126">The following WQL query returns logical disk information.</span></span>  
  
```  
SELECT FreeSpace, DeviceId, Size, SystemName, Description FROM Win32_LlogicalDisk  
```  
  
 <span data-ttu-id="41218-127">次の WQL クエリは、オペレーティング システムに対する QFE (Quick Fix Engineering) 更新の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="41218-127">The following WQL query returns a list of the quick fix engineering (QFE) updates to the operating system.</span></span>  
  
```  
Select * FROM Win32_QuickFixEngineering  
```  
  
## <a name="custom-logging-messages-available-on-the-wmi-data-reader-task"></a><span data-ttu-id="41218-128">WMI データ リーダー タスクで使用できるカスタム ログ メッセージ</span><span class="sxs-lookup"><span data-stu-id="41218-128">Custom Logging Messages Available on the WMI Data Reader Task</span></span>  
 <span data-ttu-id="41218-129">次の表は、WMI データ リーダー タスクのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="41218-129">The following table lists the custom log entries for the WMI Data Reader task.</span></span> <span data-ttu-id="41218-130">詳しくは、「[Integration Services &#40;SSIS&#41; のログ記録](../performance/integration-services-ssis-logging.md)」と「[ログ記録用のカスタム メッセージ](../custom-messages-for-logging.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="41218-130">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="41218-131">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="41218-131">Log entry</span></span>|<span data-ttu-id="41218-132">説明</span><span class="sxs-lookup"><span data-stu-id="41218-132">Description</span></span>|  
|---------------|-----------------|  
|`WMIDataReaderGettingWMIData`|<span data-ttu-id="41218-133">タスクが WMI データの読み取りを開始したことを示します。</span><span class="sxs-lookup"><span data-stu-id="41218-133">Indicates that the task began to read WMI data.</span></span>|  
|`WMIDataReaderOperation`|<span data-ttu-id="41218-134">タスクで実行された WQL クエリを報告します。</span><span class="sxs-lookup"><span data-stu-id="41218-134">Reports the WQL query that the task ran.</span></span>|  
  
## <a name="configuration-of-the-wmi-data-reader-task"></a><span data-ttu-id="41218-135">WMI データ リーダー タスクの構成</span><span class="sxs-lookup"><span data-stu-id="41218-135">Configuration of the WMI Data Reader Task</span></span>  
 <span data-ttu-id="41218-136">プロパティはプログラムによって設定するか、または [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから設定できます。</span><span class="sxs-lookup"><span data-stu-id="41218-136">You can set properties programmatically or through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="41218-137">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="41218-137">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="41218-138">[[WMI データ リーダー タスク エディター] ([WMI オプション] ページ)](../wmi-data-reader-task-editor-wmi-options-page.md)</span><span class="sxs-lookup"><span data-stu-id="41218-138">[WMI Data Reader Task Editor &#40;WMI Options Page&#41;](../wmi-data-reader-task-editor-wmi-options-page.md)</span></span>  
  
-   <span data-ttu-id="41218-139">[[式] ページ](../expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="41218-139">[Expressions Page](../expressions/expressions-page.md)</span></span>  
  
 <span data-ttu-id="41218-140">プログラムによってこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="41218-140">For information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiDataReaderTask.WmiDataReaderTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="41218-141">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="41218-141">Related Tasks</span></span>  
 <span data-ttu-id="41218-142">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="41218-142">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="41218-143">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="41218-143">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="41218-144">参照</span><span class="sxs-lookup"><span data-stu-id="41218-144">See Also</span></span>  
 <span data-ttu-id="41218-145">[Integration Services タスク](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="41218-145">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="41218-146">制御フロー</span><span class="sxs-lookup"><span data-stu-id="41218-146">Control Flow</span></span>](control-flow.md)  
  
  
