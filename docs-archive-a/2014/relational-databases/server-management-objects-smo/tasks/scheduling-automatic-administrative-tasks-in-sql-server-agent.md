---
title: SQL Server エージェントでの自動管理タスクのスケジュール設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- scheduling administrative tasks [SMO]
- SQL Server Agent [SMO]
- automatic administrative SMO tasks
ms.assetid: 900242ad-d6a2-48e9-8a1b-f0eea4413c16
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a7620935a257a4200999cce27ba901588839b16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644403"
---
# <a name="scheduling-automatic-administrative-tasks-in-sql-server-agent"></a><span data-ttu-id="376b1-102">SQL Server エージェントでの自動管理タスクのスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="376b1-102">Scheduling Automatic Administrative Tasks in SQL Server Agent</span></span>
  <span data-ttu-id="376b1-103">SMO では、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントは次のオブジェクトで表現されます。</span><span class="sxs-lookup"><span data-stu-id="376b1-103">In SMO, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is represented by the following objects:</span></span>  
  
-   <span data-ttu-id="376b1-104"><xref:Microsoft.SqlServer.Management.Smo.Agent.JobServer> オブジェクトには、ジョブ、警告、オペレーターの 3 つのコレクションがあります。</span><span class="sxs-lookup"><span data-stu-id="376b1-104">The <xref:Microsoft.SqlServer.Management.Smo.Agent.JobServer> object has three collections of jobs, alerts and operators.</span></span>  
  
-   <span data-ttu-id="376b1-105"><xref:Microsoft.SqlServer.Management.Smo.Agent.OperatorCollection> オブジェクトは、Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントによって自動的にイベントの通知を行える、ポケットベル、電子メール アドレス、およびネット送信オペレーターのリストを表します。</span><span class="sxs-lookup"><span data-stu-id="376b1-105">The <xref:Microsoft.SqlServer.Management.Smo.Agent.OperatorCollection> object represents a list of pager, e-mail addresses and net send operators that can be notified of events automatically by the Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
-   <span data-ttu-id="376b1-106"><xref:Microsoft.SqlServer.Management.Smo.Agent.AlertCollection> オブジェクトは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によって監視される、システム イベントやパフォーマンス条件などの状況のリストを表します。</span><span class="sxs-lookup"><span data-stu-id="376b1-106">The <xref:Microsoft.SqlServer.Management.Smo.Agent.AlertCollection> object represents a list of circumstances such as system events or performance conditions that are monitored by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="376b1-107"><xref:Microsoft.SqlServer.Management.Smo.Agent.JobCollection> オブジェクトは、やや複雑です。</span><span class="sxs-lookup"><span data-stu-id="376b1-107">The <xref:Microsoft.SqlServer.Management.Smo.Agent.JobCollection> object is slightly more complex.</span></span> <span data-ttu-id="376b1-108">このオブジェクトは、指定されたスケジュールで実行されるマルチステップ タスクのリストを表します。</span><span class="sxs-lookup"><span data-stu-id="376b1-108">It represents a list of multi-step tasks that run at specified schedules.</span></span> <span data-ttu-id="376b1-109">ステップおよびスケジュール情報は、<xref:Microsoft.SqlServer.Management.Smo.Agent.JobStep> オブジェクトおよび <xref:Microsoft.SqlServer.Management.Smo.Agent.JobSchedule> オブジェクトに格納されます。</span><span class="sxs-lookup"><span data-stu-id="376b1-109">The steps and schedule information are stored in the <xref:Microsoft.SqlServer.Management.Smo.Agent.JobStep> and <xref:Microsoft.SqlServer.Management.Smo.Agent.JobSchedule> objects.</span></span>  
  
 <span data-ttu-id="376b1-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント オブジェクトは、<xref:Microsoft.SqlServer.Management.Smo.Agent> 名前空間にあります。</span><span class="sxs-lookup"><span data-stu-id="376b1-110">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent objects are in the <xref:Microsoft.SqlServer.Management.Smo.Agent> namespace.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="376b1-111">例</span><span class="sxs-lookup"><span data-stu-id="376b1-111">Examples</span></span>  
 <span data-ttu-id="376b1-112">提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="376b1-112">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="376b1-113">詳細については、「 [Visual studio .net で VISUAL BASIC SMO プロジェクトを作成する](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)」または「visual [Studio .Net で VISUAL C&#35; Smo プロジェクトを作成](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="376b1-113">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
1.  <span data-ttu-id="376b1-114">プログラムで [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントを使用する場合、エージェント名前空間を修飾する `Imports` ステートメントを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="376b1-114">For programs that use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent, you must include the `Imports` statement to qualify the Agent namespace.</span></span> <span data-ttu-id="376b1-115">アプリケーションの宣言の前、かつ他の `Imports` ステートメントの後に、次のようにステートメントを挿入します。</span><span class="sxs-lookup"><span data-stu-id="376b1-115">Insert the statement after the other `Imports` statements, before any declarations in the application, such as:</span></span>  
  
 `Imports Microsoft.SqlServer.Management.Smo`  
  
 `Imports Microsoft.SqlServer.Management.Common`  
  
 `Imports Microsoft.SqlServer.Management.Smo.Agent`  
  
## <a name="creating-a-job-with-steps-and-a-schedule-in-visual-basic"></a><span data-ttu-id="376b1-116">Visual Basic でのステップを持つジョブとスケジュールの作成</span><span class="sxs-lookup"><span data-stu-id="376b1-116">Creating a Job with Steps and a Schedule in Visual Basic</span></span>  
 <span data-ttu-id="376b1-117">このコード例では、ステップを持つジョブとスケジュールを作成し、オペレーターへの通知を行います。</span><span class="sxs-lookup"><span data-stu-id="376b1-117">This code example creates a job with steps and a schedule, and then informs an operator.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBAgent1](SMO How to#SMO_VBAgent1)]  -->  
  
## <a name="creating-a-job-with-steps-and-a-schedule-in-visual-c"></a><span data-ttu-id="376b1-118">Visual C# でのステップを持つジョブとスケジュールの作成</span><span class="sxs-lookup"><span data-stu-id="376b1-118">Creating a Job with Steps and a Schedule in Visual C#</span></span>  
 <span data-ttu-id="376b1-119">このコード例では、ステップを持つジョブとスケジュールを作成し、オペレーターへの通知を行います。</span><span class="sxs-lookup"><span data-stu-id="376b1-119">This code example creates a job with steps and a schedule, and then informs an operator.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.  
            Server srv = new Server();  
  
            //Define an Operator object variable by supplying the Agent (parent JobServer object) and the name in the constructor.   
            Operator op = new Operator(srv.JobServer, "Test_Operator");  
  
            //Set the Net send address.   
            op.NetSendAddress = "Network1_PC";  
  
            //Create the operator on the instance of SQL Server Agent.   
            op.Create();  
  
            //Define a Job object variable by supplying the Agent and the name arguments in the constructor and setting properties.   
            Job jb = new Job(srv.JobServer, "Test_Job");  
  
            //Specify which operator to inform and the completion action.   
            jb.OperatorToNetSend = "Test_Operator";  
            jb.NetSendLevel = CompletionAction.Always;  
  
            //Create the job on the instance of SQL Server Agent.   
            jb.Create();  
  
            //Define a JobStep object variable by supplying the parent job and name arguments in the constructor.   
            JobStep jbstp = new JobStep(jb, "Test_Job_Step");  
            jbstp.Command = "Test_StoredProc";  
            jbstp.OnSuccessAction = StepCompletionAction.QuitWithSuccess;  
            jbstp.OnFailAction = StepCompletionAction.QuitWithFailure;  
  
            //Create the job step on the instance of SQL Agent.   
            jbstp.Create();  
  
            //Define a JobSchedule object variable by supplying the parent job and name arguments in the constructor.   
  
            JobSchedule jbsch = new JobSchedule(jb, "Test_Job_Schedule");  
  
            //Set properties to define the schedule frequency, and duration.   
            jbsch.FrequencyTypes = FrequencyTypes.Daily;  
            jbsch.FrequencySubDayTypes = FrequencySubDayTypes.Minute;  
            jbsch.FrequencySubDayInterval = 30;  
            TimeSpan ts1 = new TimeSpan(9, 0, 0);  
            jbsch.ActiveStartTimeOfDay = ts1;  
  
            TimeSpan ts2 = new TimeSpan(17, 0, 0);  
            jbsch.ActiveEndTimeOfDay = ts2;  
            jbsch.FrequencyInterval = 1;  
  
            System.DateTime d = new System.DateTime(2003, 1, 1);  
            jbsch.ActiveStartDate = d;  
  
            //Create the job schedule on the instance of SQL Agent.   
            jbsch.Create();  
        }  
```  
  
## <a name="creating-a-job-with-steps-and-a-schedule-in-powershell"></a><span data-ttu-id="376b1-120">PowerShell でのステップを持つジョブとスケジュールの作成</span><span class="sxs-lookup"><span data-stu-id="376b1-120">Creating a Job with Steps and a Schedule in PowerShell</span></span>  
 <span data-ttu-id="376b1-121">このコード例では、ステップを持つジョブとスケジュールを作成し、オペレーターへの通知を行います。</span><span class="sxs-lookup"><span data-stu-id="376b1-121">This code example creates a job with steps and a schedule, and then informs an operator.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define an Operator object variable by supplying the Agent (parent JobServer object) and the name in the constructor.  
$op = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Operator -argumentlist $srv.JobServer, "Test_Operator"  
  
#Set the Net send address.  
$op.NetSendAddress = "Network1_PC"  
  
#Create the operator on the instance of SQL Agent.  
$op.Create()  
  
#Define a Job object variable by supplying the Agent and the name arguments in the constructor and setting properties.   
$jb = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Job -argumentlist $srv.JobServer, "Test_Job"   
  
#Specify which operator to inform and the completion action.   
$jb.OperatorToNetSend = "Test_Operator";   
$jb.NetSendLevel = [Microsoft.SqlServer.Management.SMO.Agent.CompletionAction]::Always  
  
#Create the job on the instance of SQL Server Agent.   
$jb.Create()  
  
#Define a JobStep object variable by supplying the parent job and name arguments in the constructor.   
$jbstp = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.JobStep -argumentlist $jb, "Test_Job_Step"   
$jbstp.Command = "Test_StoredProc";   
$jbstp.OnSuccessAction = [Microsoft.SqlServer.Management.SMO.Agent.StepCompletionAction]::QuitWithSuccess;   
$jbstp.OnFailAction =[Microsoft.SqlServer.Management.SMO.Agent.StepCompletionAction]::QuitWithFailure;   
  
#Create the job step on the instance of SQL Agent.   
$jbstp.Create();   
  
#Define a JobSchedule object variable by supplying the parent job and name arguments in the constructor.   
$jbsch = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.JobSchedule -argumentlist $jb, "Test_Job_Schedule"   
  
#Set properties to define the schedule frequency, and duration.   
$jbsch.FrequencyTypes =  [Microsoft.SqlServer.Management.SMO.Agent.FrequencyTypes]::Daily  
  
$jbsch.FrequencySubDayTypes = [Microsoft.SqlServer.Management.SMO.Agent.FrequencySubDayTypes]::Minute  
$jbsch.FrequencySubDayInterval = 30  
$ts1 =  New-Object -TypeName TimeSpan -argumentlist 9, 0, 0  
$jbsch.ActiveStartTimeOfDay = $ts1  
$ts2 = New-Object -TypeName TimeSpan -argumentlist 17, 0, 0  
$jbsch.ActiveEndTimeOfDay = $ts2  
$jbsch.FrequencyInterval = 1  
$jbsch.ActiveStartDate = "01/01/2003"  
  
#Create the job schedule on the instance of SQL Agent.   
$jbsch.Create();  
```  
  
## <a name="creating-an-alert-in-visual-basic"></a><span data-ttu-id="376b1-122">Visual Basic での警告の作成</span><span class="sxs-lookup"><span data-stu-id="376b1-122">Creating an Alert in Visual Basic</span></span>  
 <span data-ttu-id="376b1-123">このコード例では、パフォーマンス条件によってトリガーされる警告を作成しています。</span><span class="sxs-lookup"><span data-stu-id="376b1-123">This code example creates an alert that is triggered by a performance condition.</span></span> <span data-ttu-id="376b1-124">条件は、次の形式で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="376b1-124">The condition must be provided in a specific format:</span></span>  
  
 <span data-ttu-id="376b1-125">**ObjectName |CounterName |Instance |ComparisionOp |CompValue**</span><span class="sxs-lookup"><span data-stu-id="376b1-125">**ObjectName|CounterName|Instance|ComparisionOp|CompValue**</span></span>  
  
 <span data-ttu-id="376b1-126">警告の通知にはオペレーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="376b1-126">An operator is required for the alert notification.</span></span> <span data-ttu-id="376b1-127">`operator` は Visual Basic キーワードであるため、<xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> 型には角かっこが必要です。</span><span class="sxs-lookup"><span data-stu-id="376b1-127">The <xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> type requires square parentheses because `operator` is a Visual Basic keyword.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBAgent3](SMO How to#SMO_VBAgent3)]  -->  
  
## <a name="creating-an-alert-in-visual-c"></a><span data-ttu-id="376b1-128">Visual C# での警告の作成</span><span class="sxs-lookup"><span data-stu-id="376b1-128">Creating an Alert in Visual C#</span></span>  
 <span data-ttu-id="376b1-129">このコード例では、パフォーマンス条件によってトリガーされる警告を作成しています。</span><span class="sxs-lookup"><span data-stu-id="376b1-129">This code example creates an alert that is triggered by a performance condition.</span></span> <span data-ttu-id="376b1-130">条件は、次の形式で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="376b1-130">The condition must be provided in a specific format:</span></span>  
  
 <span data-ttu-id="376b1-131">**ObjectName |CounterName |Instance |ComparisionOp |CompValue**</span><span class="sxs-lookup"><span data-stu-id="376b1-131">**ObjectName|CounterName|Instance|ComparisionOp|CompValue**</span></span>  
  
 <span data-ttu-id="376b1-132">警告の通知にはオペレーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="376b1-132">An operator is required for the alert notification.</span></span> <span data-ttu-id="376b1-133">`operator` は [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] キーワードであるため、<xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> 型には角かっこが必要です。</span><span class="sxs-lookup"><span data-stu-id="376b1-133">The <xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> type requires square parentheses because `operator` is a [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] keyword.</span></span>  
  
```csharp
{  
             //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
  
            //Define an Alert object variable by supplying the SQL Server Agent and the name arguments in the constructor.   
            Alert al = new Alert(srv.JobServer, "Test_Alert");  
  
            //Specify the performance condition string to define the alert.   
            al.PerformanceCondition = "SQLServer:General Statistics|User Connections||>|3";  
  
            //Create the alert on the SQL Agent.   
            al.Create();  
  
            //Define an Operator object variable by supplying the SQL Server Agent and the name arguments in the constructor.   
  
            Operator op = new Operator(srv.JobServer, "Test_Operator");  
            //Set the net send address.   
            op.NetSendAddress = "NetworkPC";  
            //Create the operator on the SQL Agent.   
            op.Create();  
            //Run the AddNotification method to specify the operator is notified when the alert is raised.   
            al.AddNotification("Test_Operator", NotifyMethods.NetSend);  
        }  
```  
  
## <a name="creating-an-alert-in-powershell"></a><span data-ttu-id="376b1-134">PowerShell での警告の作成</span><span class="sxs-lookup"><span data-stu-id="376b1-134">Creating an Alert in PowerShell</span></span>  
 <span data-ttu-id="376b1-135">このコード例では、パフォーマンス条件によってトリガーされる警告を作成しています。</span><span class="sxs-lookup"><span data-stu-id="376b1-135">This code example creates an alert that is triggered by a performance condition.</span></span> <span data-ttu-id="376b1-136">条件は、次の形式で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="376b1-136">The condition must be provided in a specific format:</span></span>  
  
 <span data-ttu-id="376b1-137">**ObjectName |CounterName |Instance |ComparisionOp |CompValue**</span><span class="sxs-lookup"><span data-stu-id="376b1-137">**ObjectName|CounterName|Instance|ComparisionOp|CompValue**</span></span>  
  
 <span data-ttu-id="376b1-138">警告の通知にはオペレーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="376b1-138">An operator is required for the alert notification.</span></span> <span data-ttu-id="376b1-139">`operator` は [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] キーワードであるため、<xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> 型には角かっこが必要です。</span><span class="sxs-lookup"><span data-stu-id="376b1-139">The <xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> type requires square parentheses because `operator` is a [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] keyword.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define an Alert object variable by supplying the SQL Agent and the name arguments in the constructor.  
$al = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Alert -argumentlist $srv.JobServer, "Test_Alert"  
  
#Specify the performance condition string to define the alert.  
$al.PerformanceCondition = "SQLServer:General Statistics|User Connections||>|3"  
  
#Create the alert on the SQL Agent.  
$al.Create()  
  
#Define an Operator object variable by supplying the Agent (parent JobServer object) and the name in the constructor.  
$op = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Operator -argumentlist $srv.JobServer, "Test_Operator"  
  
#Set the Net send address.  
$op.NetSendAddress = "Network1_PC"  
  
#Create the operator on the instance of SQL Agent.  
$op.Create()  
  
#Run the AddNotification method to specify the operator is notified when the alert is raised.  
$ns = [Microsoft.SqlServer.Management.SMO.Agent.NotifyMethods]::NetSend  
$al.AddNotification("Test_Operator", $ns)  
  
#Drop the alert and the operator  
$al.Drop()  
$op.Drop()  
```  
  
## <a name="allowing-user-access-to-subsystem-by-using-a-proxy-account-in-visual-basic"></a><span data-ttu-id="376b1-140">Visual Basic でプロキシ アカウントを使用することでユーザーがサブシステムにアクセスできるようにする</span><span class="sxs-lookup"><span data-stu-id="376b1-140">Allowing User Access to Subsystem by Using a Proxy Account in Visual Basic</span></span>  
 <span data-ttu-id="376b1-141">このコード例では、<xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount.AddSubSystem%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount> メソッドを使用して、ユーザーが指定されたサブシステムにアクセスできるようにする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="376b1-141">This code example shows how to allow a user access to a specified subsystem by using the <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount.AddSubSystem%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount> object.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBAgent2](SMO How to#SMO_VBAgent2)]  -->  
  
## <a name="allowing-user-access-to-subsystem-by-using-a-proxy-account-in-visual-c"></a><span data-ttu-id="376b1-142">Visual C# でプロキシ アカウントを使用することでユーザーがサブシステムにアクセスできるようにする</span><span class="sxs-lookup"><span data-stu-id="376b1-142">Allowing User Access to Subsystem by Using a Proxy Account in Visual C#</span></span>  
 <span data-ttu-id="376b1-143">このコード例では、<xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount.AddSubSystem%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount> メソッドを使用して、ユーザーが指定されたサブシステムにアクセスできるようにする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="376b1-143">This code example shows how to allow a user access to a specified subsystem by using the <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount.AddSubSystem%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount> object.</span></span>  
  
```csharp
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
//Declare a JobServer object variable and reference the SQL Server Agent.   
JobServer js = default(JobServer);   
js = srv.JobServer;   
//Define a Credential object variable by supplying the parent server and name arguments in the constructor.   
Credential c = default(Credential);   
c = new Credential(srv, "Proxy_accnt");   
//Set the identity to a valid login represented by the vIdentity string variable.   
//The sub system will run under this login.   
c.Identity = vIdentity;   
//Create the credential on the instance of SQL Server.   
c.Create();   
//Define a ProxyAccount object variable by supplying the SQL Server Agent, the name, the credential, the description arguments in the constructor.   
ProxyAccount pa = default(ProxyAccount);   
pa = new ProxyAccount(js, "Test_proxy", "Proxy_accnt", true, "Proxy account for users to run job steps in command shell.");   
//Create the proxy account on the SQL Agent.   
pa.Create();   
//Add the login, represented by the vLogin string variable, to the proxy account.   
pa.AddLogin(vLogin);   
//Add the CmdExec subsytem to the proxy account.   
pa.AddSubSystem(AgentSubSystem.CmdExec);   
}   
//Now users logged on as vLogin can run CmdExec job steps with the specified credentials.   
```  
  
## <a name="see-also"></a><span data-ttu-id="376b1-144">参照</span><span class="sxs-lookup"><span data-stu-id="376b1-144">See Also</span></span>  
 <span data-ttu-id="376b1-145">[SQL Server エージェント](../../../ssms/agent/sql-server-agent.md) </span><span class="sxs-lookup"><span data-stu-id="376b1-145">[SQL Server Agent](../../../ssms/agent/sql-server-agent.md) </span></span>  
 [<span data-ttu-id="376b1-146">ジョブの実装</span><span class="sxs-lookup"><span data-stu-id="376b1-146">Implement Jobs</span></span>](../../../ssms/agent/implement-jobs.md)  
