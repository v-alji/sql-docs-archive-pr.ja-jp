---
title: 拡張イベントへの PowerShell プロバイダーの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- PowerShell [SQL Server], xevent
- extended events [SQL Server], PowerShell
- PowerShell [SQL Server], extended events
ms.assetid: 0b10016f-a479-4444-a484-46cb4677cf64
author: rothja
ms.author: jroth
ms.openlocfilehash: a9efbd389545dcde8285a38b06f41580fb65de6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642083"
---
# <a name="use-the-powershell-provider-for-extended-events"></a><span data-ttu-id="0adb0-102">拡張イベントへの PowerShell プロバイダーの使用</span><span class="sxs-lookup"><span data-stu-id="0adb0-102">Use the PowerShell Provider for Extended Events</span></span>
  <span data-ttu-id="0adb0-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell プロバイダーを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 拡張イベントを管理できます。</span><span class="sxs-lookup"><span data-stu-id="0adb0-103">You can manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Extended Events by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell provider.</span></span> <span data-ttu-id="0adb0-104">XEvent サブフォルダーは、SQLSERVER ドライブで利用可能です。</span><span class="sxs-lookup"><span data-stu-id="0adb0-104">The XEvent subfolder is available under the SQLSERVER drive.</span></span> <span data-ttu-id="0adb0-105">このフォルダーには、次のいずれかの方法でアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0adb0-105">You can access the folder by using either of the following methods:</span></span>  
  
-   <span data-ttu-id="0adb0-106">コマンドプロンプトで「」と入力し、enter `sqlps` キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0adb0-106">At a command prompt, type `sqlps`, and then press ENTER.</span></span> <span data-ttu-id="0adb0-107">「`cd xevent`」と入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0adb0-107">Type `cd xevent`, and then press ENTER.</span></span> <span data-ttu-id="0adb0-108">そこから、 **cd**と `dir` コマンド (また**Set-Location**は**get-childitem**コマンドレット) を使用して、サーバー名とインスタンス名に移動できます。</span><span class="sxs-lookup"><span data-stu-id="0adb0-108">From there, you can use the **cd** and `dir` commands (or **Set-Location** and **Get-Childitem** cmdlets) to navigate to the server name and instance name.</span></span>  
  
-   <span data-ttu-id="0adb0-109">オブジェクト エクスプローラーで、インスタンス名、 **[管理]** の順に展開し、 **[拡張イベント]** を右クリックして、 **[PowerShell の起動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0adb0-109">In Object Explorer, expand the instance name, expand **Management**, right-click **Extended Events**, and then click **Start PowerShell**.</span></span> <span data-ttu-id="0adb0-110">これにより、次のパスで PowerShell が起動します。</span><span class="sxs-lookup"><span data-stu-id="0adb0-110">This starts PowerShell in the following path:</span></span>  
  
     <span data-ttu-id="0adb0-111">PS SQLSERVER: \ XEvent \\ *ServerName* \\ *InstanceName*></span><span class="sxs-lookup"><span data-stu-id="0adb0-111">PS SQLSERVER:\XEvent\\*ServerName*\\*InstanceName*></span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0adb0-112">PowerShell は、 **[拡張イベント]** の下の任意のノードから起動できます。</span><span class="sxs-lookup"><span data-stu-id="0adb0-112">You can start PowerShell from any node under **Extended Events**.</span></span> <span data-ttu-id="0adb0-113">たとえば、 **[Sessions]** を右クリックし、 **[PowerShell の起動]** をクリックできます。</span><span class="sxs-lookup"><span data-stu-id="0adb0-113">For example, you can right-click **Sessions**, and then click **Start PowerShell**.</span></span> <span data-ttu-id="0adb0-114">これにより、1 レベル深い Sessions フォルダーで PowerShell が起動します。</span><span class="sxs-lookup"><span data-stu-id="0adb0-114">This starts PowerShell one level deeper, at the Sessions folder.</span></span>  
  
 <span data-ttu-id="0adb0-115">XEvent フォルダー ツリーを参照して、既存の拡張イベント セッションと、関連するイベント、ターゲット、および述語を表示できます。</span><span class="sxs-lookup"><span data-stu-id="0adb0-115">You can browse the XEvent folder tree to view existing Extended Events sessions and their associated events, targets and predicates.</span></span> <span data-ttu-id="0adb0-116">たとえば、PS SQLSERVER:\ XEvent ServerName InstanceName> パスで、「」と入力し、enter キーを押し、「」と入力して enter \\ *ServerName* \\ *InstanceName* `cd sessions` `dir` キーを押すと、そのインスタンスに格納されているセッションの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0adb0-116">For example, from the PS SQLSERVER:\XEvent\\*ServerName*\\*InstanceName*> path, if you type `cd sessions`, press ENTER, type `dir`, and then press ENTER, you can see the list of sessions that are stored on that instance.</span></span> <span data-ttu-id="0adb0-117">また、セッションが実行中かどうか (および実行中の場合は実行時間)、およびセッションがインスタンスの起動時に開始されるように構成されているかどうかも表示されます。</span><span class="sxs-lookup"><span data-stu-id="0adb0-117">You can also view whether the session is running (and if this is the case, for how long), and whether the session is configured to start when the instance starts.</span></span>  
  
 <span data-ttu-id="0adb0-118">セッションに関連付けられているイベント、述語、およびターゲットを表示するには、ディレクトリをセッション名に変更してから、events フォルダーまたは targets フォルダーを表示します。</span><span class="sxs-lookup"><span data-stu-id="0adb0-118">To view the events, their predictates, and the targets that are associated with a session, you can change directories to the session name, and then view either the events or targets folder.</span></span> <span data-ttu-id="0adb0-119">たとえば、既定のシステム正常性セッションに関連付けられているイベントとその述語を表示するには、PS SQLSERVER:\ XEvent \\ *ServerName* \\ *InstanceName*\ Sessions> パスで、enter `cd system_health\events,` キーを押し、「」と入力して `dir` 、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0adb0-119">For example, to view the events and their predicates that are associated with the default system health session, from the PS SQLSERVER:\XEvent\\*ServerName*\\*InstanceName*\Sessions> path, type `cd system_health\events,` press ENTER, type `dir`, and then press ENTER.</span></span>  
  
 <span data-ttu-id="0adb0-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell プロバイダーは、拡張イベント セッションの作成、変更、および管理に使用できる強力なツールです。</span><span class="sxs-lookup"><span data-stu-id="0adb0-120">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell provider is a powerful tool that you can use to create, alter, and manage Extended Events sessions.</span></span> <span data-ttu-id="0adb0-121">次のセクションでは、拡張イベントに PowerShell スクリプトを使用する基本的な例をいくつか紹介します。</span><span class="sxs-lookup"><span data-stu-id="0adb0-121">The following section provides some basic examples of using PowerShell scripts with Extended Events.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0adb0-122">例</span><span class="sxs-lookup"><span data-stu-id="0adb0-122">Examples</span></span>  
 <span data-ttu-id="0adb0-123">以下の例では、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="0adb0-123">In the following examples, note the following:</span></span>  
  
-   <span data-ttu-id="0adb0-124">スクリプトは、PS SQLSERVER: \\> prompt (コマンドプロンプトで「」と入力すると使用できます) から実行する必要があり `sqlps` ます。</span><span class="sxs-lookup"><span data-stu-id="0adb0-124">The scripts must be run from the PS SQLSERVER:\\> prompt (available by typing `sqlps` at a command prompt).</span></span>  
  
-   <span data-ttu-id="0adb0-125">スクリプトでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の既定のインスタンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="0adb0-125">The scripts use the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="0adb0-126">スクリプトは、.ps1 拡張子を付けて保存してください。</span><span class="sxs-lookup"><span data-stu-id="0adb0-126">The scripts must be saved with a .ps1 extension.</span></span>  
  
-   <span data-ttu-id="0adb0-127">PowerShell 実行ポリシーで、スクリプトを実行できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0adb0-127">The PowerShell execution policy must allow the script to run.</span></span> <span data-ttu-id="0adb0-128">実行ポリシーを設定するには、 **Set-Executionpolicy** コマンドレットを使用します</span><span class="sxs-lookup"><span data-stu-id="0adb0-128">To set the execution policy, use the **Set-Executionpolicy** cmdlet.</span></span> <span data-ttu-id="0adb0-129">(詳細については、「`get-help set-executionpolicy -detailed`」と入力し、Enter キーを押します)。</span><span class="sxs-lookup"><span data-stu-id="0adb0-129">(For more information, type `get-help set-executionpolicy -detailed`, and then press ENTER.)</span></span>  
  
 <span data-ttu-id="0adb0-130">次のスクリプトでは、"TestSession" という名前の新しいセッションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0adb0-130">The following script creates a new session that is named 'TestSession'.</span></span>  
  
```powershell
#Script for creating a session.  
cd XEvent  
$h = hostname  
cd $h  
  
#Use the default instance.  
$store = dir | where {$_.DisplayName -ieq 'default'}  
$session = New-Object Microsoft.SqlServer.Management.XEvent.Session -ArgumentList $store, "TestSession"  
$event = $session.AddEvent("sqlserver.file_written")  
$event.AddAction("package0.callstack")  
$session.Create()  
```  
  
 <span data-ttu-id="0adb0-131">次のスクリプトでは、前の例で作成したセッションにリング バッファー ターゲットが追加されます</span><span class="sxs-lookup"><span data-stu-id="0adb0-131">The following script adds the ring buffer target to the session that was created in the previous example.</span></span> <span data-ttu-id="0adb0-132">(この例では、`Alter` メソッドの使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="0adb0-132">(This example shows the use of the `Alter` method.</span></span> <span data-ttu-id="0adb0-133">ターゲットは、最初にセッションを作成するときに追加できます)。</span><span class="sxs-lookup"><span data-stu-id="0adb0-133">Be aware that you can add the target when you first create the session.)</span></span>  
  
```powershell
#Script to alter a session.  
cd XEvent  
$h = hostname  
cd $h  
cd DEFAULT\Sessions  
  
#Used to find the specified session.  
$session = dir | where {$_.Name -eq 'TestSession'}  
  
#Add the ring buffer target and call the Alter method.  
$session.AddTarget("package0.ring_buffer")  
$session.Alter()  
```  
  
 <span data-ttu-id="0adb0-134">次のスクリプトでは、述語式を使用する新しいセッションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0adb0-134">The following script creates a new session that uses a predicate expression.</span></span> <span data-ttu-id="0adb0-135">この例では、sqlserver.file_written イベントを利用して、c:\temp.log ファイルに書き込まれたときの情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="0adb0-135">In this case, the session collects information for when the c:\temp.log file is written to (through the sqlserver.file_written event).</span></span>  
  
```powershell
#Script for creating a session.  
cd XEvent  
$h = hostname  
cd $h  
  
#Use the default instance.  
$store = dir | where {$_.DisplayName -ieq 'default'}  
$session = New-Object Microsoft.SqlServer.Management.XEvent.Session -ArgumentList $store, "TestSession2"  
$event = $session.AddEvent("sqlserver.file_written")  
  
#Construct a predicate "equal_i_unicode_string(path, N'c:\temp.log')".  
$column = $store.SqlServerPackage.EventInfoSet["file_written"].DataEventColumnInfoSet["path"]  
$operand = new-object Microsoft.SqlServer.Management.XEvent.PredOperand -argumentlist $column  
$value = new-object Microsoft.SqlServer.Management.XEvent.PredValue -argumentlist "c:\temp.log"  
$compare = $store.Package0Package.PredCompareInfoSet["equal_i_unicode_string"]  
$predicate = new-object Microsoft.SqlServer.Management.XEvent.PredFunctionExpr -ArgumentList $compare, $operand, $value  
$event.SetPredicate($predicate)  
$session.Create()  
```  
  
## <a name="security"></a><span data-ttu-id="0adb0-136">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="0adb0-136">Security</span></span>  
 <span data-ttu-id="0adb0-137">拡張イベント セッションを作成、変更、または削除するには、ALTER ANY EVENT SESSION 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="0adb0-137">To create, alter, or drop an Extended Events session, you must have the ALTER ANY EVENT SESSION permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0adb0-138">参照</span><span class="sxs-lookup"><span data-stu-id="0adb0-138">See Also</span></span>  
 <span data-ttu-id="0adb0-139">[SQL Server PowerShell](../../powershell/sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="0adb0-139">[SQL Server PowerShell](../../powershell/sql-server-powershell.md) </span></span>  
 <span data-ttu-id="0adb0-140">[System_health セッションを使用する](use-the-ssms-xe-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="0adb0-140">[Use the system_health Session](use-the-ssms-xe-profiler.md) </span></span>  
 [<span data-ttu-id="0adb0-141">拡張イベントのツール</span><span class="sxs-lookup"><span data-stu-id="0adb0-141">Extended Events Tools</span></span>](extended-events-tools.md)  
