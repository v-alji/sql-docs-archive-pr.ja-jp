---
title: ジョブ ステップの管理 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [SQL Server replication]
- job steps [SQL Server Agent]
- jobs [SQL Server Agent], Integration Services package step
- executable programs as job steps
- operating systems [SQL Server], job steps
- Transact-SQL job step
- job steps [Transact-SQL]
- Integration Services packages, job steps
- replication job steps [SQL Server]
- logs [SQL Server], jobs
- SQL Server Agent jobs, job steps
- ActiveX scripting jobs [SQL Server]
- job steps [Analysis Services]
ms.assetid: 51352afc-a0a4-428b-8985-f9e58bb57c31
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7362df13956e44b73d6984691e882bec2f39a1e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642501"
---
# <a name="manage-job-steps"></a><span data-ttu-id="a2f79-102">ジョブ ステップの管理</span><span class="sxs-lookup"><span data-stu-id="a2f79-102">Manage Job Steps</span></span>
  <span data-ttu-id="a2f79-103">ジョブ ステップは、ジョブがデータベースまたはサーバーで行う処理です。</span><span class="sxs-lookup"><span data-stu-id="a2f79-103">A job step is an action that the job takes on a database or a server.</span></span> <span data-ttu-id="a2f79-104">すべてのジョブには、最低 1 つのジョブ ステップを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2f79-104">Every job must have at least one job step.</span></span> <span data-ttu-id="a2f79-105">ジョブ ステップには次のような種類があります。</span><span class="sxs-lookup"><span data-stu-id="a2f79-105">Job steps can be:</span></span>  
  
-   <span data-ttu-id="a2f79-106">実行可能プログラムまたはオペレーティング システムのコマンド。</span><span class="sxs-lookup"><span data-stu-id="a2f79-106">Executable programs and operating system commands.</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="a2f79-107">ステートメント。ストアド プロシージャと拡張ストアド プロシージャを含みます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-107">statements, including stored procedures and extended stored procedures.</span></span>  
  
-   <span data-ttu-id="a2f79-108">PowerShell スクリプト。</span><span class="sxs-lookup"><span data-stu-id="a2f79-108">PowerShell scripts.</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="a2f79-109">ActiveX スクリプト。</span><span class="sxs-lookup"><span data-stu-id="a2f79-109">ActiveX scripts.</span></span>  
  
-   <span data-ttu-id="a2f79-110">レプリケーション タスク。</span><span class="sxs-lookup"><span data-stu-id="a2f79-110">Replication tasks.</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="a2f79-111">タスク。</span><span class="sxs-lookup"><span data-stu-id="a2f79-111">tasks.</span></span>  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="a2f79-112">パッケージ。</span><span class="sxs-lookup"><span data-stu-id="a2f79-112">packages.</span></span>  
  
 <span data-ttu-id="a2f79-113">各ジョブ ステップは特定のセキュリティ コンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-113">Every job step runs in a specific security context.</span></span> <span data-ttu-id="a2f79-114">ジョブ ステップがプロキシを指定している場合、このジョブ ステップは指定されたプロキシの資格情報のセキュリティ コンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-114">If the job step specifies a proxy, the job step runs in the security context of the credential for the proxy.</span></span> <span data-ttu-id="a2f79-115">ジョブ ステップがプロキシを指定していない場合、このジョブ ステップは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントのコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-115">If a job step does not specify a proxy, the job step runs in the context of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account.</span></span> <span data-ttu-id="a2f79-116">プロキシを明示的に指定せずにジョブを作成できるのは、sysadmin 固定サーバー ロールのメンバーのみです。</span><span class="sxs-lookup"><span data-stu-id="a2f79-116">Only members of the sysadmin fixed server role can create jobs that do not explicitly specify a proxy.</span></span>  
  
 <span data-ttu-id="a2f79-117">ジョブ ステップは特定の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ユーザーのコンテキストで実行されるので、ユーザーには、ジョブ ステップの実行に必要なアクセス許可と構成が必要です。</span><span class="sxs-lookup"><span data-stu-id="a2f79-117">Because job steps run in the context of a specific [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user, that user must have the permissions and configuration necessary for the job step to execute.</span></span> <span data-ttu-id="a2f79-118">たとえば、ドライブ文字または汎用名前付け規則 (UNC) パスを必要とするようなジョブを作成した場合、タスクのテスト時にはジョブ ステップを作成者の Windows ユーザー アカウントで実行していることがあります。</span><span class="sxs-lookup"><span data-stu-id="a2f79-118">For example, if you create a job that requires a drive letter or a Universal Naming Convention (UNC) path, the job steps may run under your Windows user account while testing the tasks.</span></span> <span data-ttu-id="a2f79-119">ところが、このジョブ ステップの Windows ユーザーにも、このジョブ ステップを実行するためのアクセス許可、ドライブ文字構成、指定ドライブへのアクセスが必要になります。</span><span class="sxs-lookup"><span data-stu-id="a2f79-119">However, the Windows user for the job step must also have the necessary permissions, drive letter configurations, or access to the required drive.</span></span> <span data-ttu-id="a2f79-120">そうでなければ、このジョブ ステップは失敗します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-120">Otherwise, the job step fails.</span></span> <span data-ttu-id="a2f79-121">この問題を回避するには、各ジョブ ステップのプロキシに、ジョブ ステップで実行するタスクに対して必要なアクセス許可が設定されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a2f79-121">To prevent this problem, ensure that the proxy for each job step has the necessary permissions for the task that the job step performs.</span></span> <span data-ttu-id="a2f79-122">詳細については、「 [SQL Server データベースエンジンと Azure SQL Database の Security Center](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2f79-122">For more information, see [Security Center for SQL Server Database Engine and Azure SQL Database](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).</span></span>  
  
## <a name="job-step-logs"></a><span data-ttu-id="a2f79-123">ジョブ ステップのログ</span><span class="sxs-lookup"><span data-stu-id="a2f79-123">Job Step Logs</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a2f79-124">エージェントは、オペレーティング システム ファイルまたは msdb データベースの sysjobstepslogs テーブルに、一部のジョブ ステップからの出力を書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-124">Agent can write output from some job steps either to an operating system file or to the sysjobstepslogs table in the msdb database.</span></span> <span data-ttu-id="a2f79-125">両方の出力先に出力を書き込めるジョブ ステップの種類は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a2f79-125">The following job step types can write output to both destinations:</span></span>  
  
-   <span data-ttu-id="a2f79-126">実行可能プログラムまたはオペレーティング システムのコマンド。</span><span class="sxs-lookup"><span data-stu-id="a2f79-126">Executable programs and operating system commands.</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="a2f79-127">ステートメント。</span><span class="sxs-lookup"><span data-stu-id="a2f79-127">statements.</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="a2f79-128">タスク。</span><span class="sxs-lookup"><span data-stu-id="a2f79-128">tasks.</span></span>  
  
 <span data-ttu-id="a2f79-129">ジョブ ステップの出力をオペレーティング システム ファイルに書き込めるのは、sysadmin 固定サーバー ロールのメンバーであるユーザーが実行するジョブ ステップのみです。</span><span class="sxs-lookup"><span data-stu-id="a2f79-129">Only job steps that are executed by users who are members of the sysadmin fixed server role can write job step output to operating system files.</span></span> <span data-ttu-id="a2f79-130">ジョブ ステップを実行するユーザーが、msdb データベースの SQLAgentUserRole 固定データベース ロール、SQLAgentReaderRole 固定データベース ロール、または SQLAgentOperatorRole 固定データベース ロールのメンバーである場合、ジョブ ステップの出力は sysjobstepslogs テーブルにのみ書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-130">If job steps are executed by users who are members of the SQLAgentUserRole, SQLAgentReaderRole, or the SQLAgentOperatorRole fixed database roles in the msdb database, then the output from these job steps can be written only to the sysjobstepslogs table.</span></span>  
  
 <span data-ttu-id="a2f79-131">ジョブ ステップのログは、ジョブまたはジョブ ステップが削除されると自動的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-131">Job step logs are automatically deleted when jobs or job steps are deleted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a2f79-132">レプリケーション タスクと [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのジョブ ステップのログ記録は、それぞれのサブシステムによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-132">Replication task and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package job step logging is handled by their respective subsystem.</span></span> <span data-ttu-id="a2f79-133">これらのタイプのジョブ ステップについては、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用してジョブ ステップのログ記録を構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="a2f79-133">You cannot use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to configure jog step logging for these types of job steps.</span></span>  
  
## <a name="executable-programs-and-operating-system-commands-as-job-steps"></a><span data-ttu-id="a2f79-134">ジョブ ステップとしての実行可能プログラムとオペレーティング システム コマンド</span><span class="sxs-lookup"><span data-stu-id="a2f79-134">Executable Programs and Operating-System Commands As Job Steps</span></span>  
 <span data-ttu-id="a2f79-135">実行可能プログラムとオペレーティング システム コマンドは、ジョブ ステップとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-135">Executable programs and operating-system commands can be used as job steps.</span></span> <span data-ttu-id="a2f79-136">これらのファイルの拡張子は、.bat、.cmd、.com、または .exe です。</span><span class="sxs-lookup"><span data-stu-id="a2f79-136">These files may have .bat, .cmd, .com, or .exe file extensions.</span></span>  
  
 <span data-ttu-id="a2f79-137">実行可能プログラムまたはオペレーティング システム コマンドをジョブ ステップとして使用する場合は、次の項目を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2f79-137">When you use an executable program or an operating-system command as a job step, you must specify:</span></span>  
  
-   <span data-ttu-id="a2f79-138">コマンドが正常に終了した場合に返されるプロセス終了コード。</span><span class="sxs-lookup"><span data-stu-id="a2f79-138">The process exit code returned if the command was successful.</span></span>  
  
-   <span data-ttu-id="a2f79-139">実行するコマンドです。</span><span class="sxs-lookup"><span data-stu-id="a2f79-139">The command to execute.</span></span> <span data-ttu-id="a2f79-140">オペレーティング システム コマンドを実行する場合、これはコマンド自体を指します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-140">To execute an operating system command, this is simply the command itself.</span></span> <span data-ttu-id="a2f79-141">外部プログラムの場合は、 **C:\Program Files\Microsoft SQL Server\100\Tools\Binn\sqlcmd.exe -e -q "sp_who"** など、プログラム名とそのプログラムの引数を指します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-141">For an external program, this is the name of the program and the arguments to the program, for example: **C:\Program Files\Microsoft SQL Server\100\Tools\Binn\sqlcmd.exe -e -q "sp_who"**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a2f79-142">システム パスまたはジョブ ステップの実行ユーザーのパスで指定されたディレクトリ内に、実行可能ファイルが存在しない場合は、実行可能ファイルの完全パスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2f79-142">You must provide the full path to the executable if the executable is not located in a directory specified in the system path or the path for the user that the job step runs as.</span></span>  
  
## <a name="transact-sql-job-steps"></a><span data-ttu-id="a2f79-143">Transact-SQL ジョブ ステップ</span><span class="sxs-lookup"><span data-stu-id="a2f79-143">Transact-SQL Job Steps</span></span>  
 <span data-ttu-id="a2f79-144">[!INCLUDE[tsql](../../includes/tsql-md.md)] ジョブ ステップを作成するには、次の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2f79-144">When you create a [!INCLUDE[tsql](../../includes/tsql-md.md)] job step, you must:</span></span>  
  
-   <span data-ttu-id="a2f79-145">ジョブを実行するデータベースを特定します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-145">Identify the database in which to run the job.</span></span>  
  
-   <span data-ttu-id="a2f79-146">実行する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-146">Type the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to execute.</span></span> <span data-ttu-id="a2f79-147">このステートメントで、ストアド プロシージャまたは拡張ストアド プロシージャを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-147">The statement may call a stored procedure or an extended stored procedure.</span></span>  
  
 <span data-ttu-id="a2f79-148">必要に応じて、ジョブ ステップのコマンドとして既存の [!INCLUDE[tsql](../../includes/tsql-md.md)] ファイルを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-148">Optionally, you can open an existing [!INCLUDE[tsql](../../includes/tsql-md.md)] file as the command for the job step.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="a2f79-149">ジョブ ステップでは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント プロキシを使用しません。</span><span class="sxs-lookup"><span data-stu-id="a2f79-149">job steps do not use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxies.</span></span> <span data-ttu-id="a2f79-150">このジョブ ステップはジョブ ステップの所有者として実行されるか、ジョブ ステップの所有者が sysadmin 固定サーバー ロールのメンバーの場合には [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-150">Instead, the job step runs as the owner of the job step, or as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account if the owner of the job step is a member of the sysadmin fixed server role.</span></span> <span data-ttu-id="a2f79-151">sysadmin 固定サーバー ロールのメンバーは、sp_add_jobstep ストアド プロシージャの [!INCLUDE[tsql](../../includes/tsql-md.md)] database_user_name *パラメーターを使用して、別のユーザーのコンテキストで* ジョブ ステップが実行されるように指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-151">Members of the sysadmin fixed server role can also specify that [!INCLUDE[tsql](../../includes/tsql-md.md)] job steps run under the context of another user by using the *database_user_name* parameter of the sp_add_jobstep stored procedure.</span></span> <span data-ttu-id="a2f79-152">詳細については、「 [sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2f79-152">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a2f79-153">1 つの [!INCLUDE[tsql](../../includes/tsql-md.md)] ジョブ ステップに、複数のバッチを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-153">A single [!INCLUDE[tsql](../../includes/tsql-md.md)] job step can contain multiple batches.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="a2f79-154">ジョブ ステップには埋め込み GO コマンドを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-154">job steps can contain embedded GO commands.</span></span>  
  
## <a name="powershell-scripting-job-steps"></a><span data-ttu-id="a2f79-155">PowerShell スクリプティング ジョブ ステップ</span><span class="sxs-lookup"><span data-stu-id="a2f79-155">PowerShell Scripting Job Steps</span></span>  
 <span data-ttu-id="a2f79-156">PowerShell スクリプト ジョブ ステップを作成するときには、次のいずれかをステップのコマンドとして指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2f79-156">When you create a PowerShell script job step, you must specify one of two things as the command for the step:</span></span>  
  
-   <span data-ttu-id="a2f79-157">PowerShell スクリプトのテキスト。</span><span class="sxs-lookup"><span data-stu-id="a2f79-157">The text of a PowerShell script.</span></span>  
  
-   <span data-ttu-id="a2f79-158">開く対象の既存の PowerShell スクリプト ファイル。</span><span class="sxs-lookup"><span data-stu-id="a2f79-158">An existing PowerShell script file to be opened.</span></span>  
  
 <span data-ttu-id="a2f79-159">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントの powershell サブシステムが powershell セッションを開き、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] powershell スナップインを読み込みます。ジョブステップコマンドとして使用される PowerShell スクリプトでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] powershell プロバイダーおよびコマンドレットを参照できます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-159">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent PowerShell subsystem opens a PowerShell session and loads the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell snap-ins. The PowerShell script used as the job step command can reference the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell provider and cmdlets.</span></span> <span data-ttu-id="a2f79-160">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell スナップインを使用した PowerShell スクリプトの作成の詳細については、「 [SQL Server PowerShell](../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2f79-160">For more information about writing PowerShell scripts using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell snap-ins, see the [SQL Server PowerShell](../../powershell/sql-server-powershell.md).</span></span>  
  
## <a name="activex-scripting-job-steps"></a><span data-ttu-id="a2f79-161">ActiveX スクリプティング ジョブ ステップ</span><span class="sxs-lookup"><span data-stu-id="a2f79-161">ActiveX Scripting Job Steps</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a2f79-162">ActiveX スクリプティング ジョブ ステップは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の将来のバージョンで [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントから削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="a2f79-162">The ActiveX scripting job step will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a2f79-163">新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a2f79-163">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="a2f79-164">ActiveX スクリプティング ジョブ ステップを作成するには、次の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2f79-164">When you create an ActiveX scripting job step, you must:</span></span>  
  
-   <span data-ttu-id="a2f79-165">ジョブ ステップを記述するスクリプティング言語を特定します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-165">Identify the scripting language in which the job step is written.</span></span>  
  
-   <span data-ttu-id="a2f79-166">ActiveX スクリプトを記述します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-166">Write the ActiveX script.</span></span>  
  
 <span data-ttu-id="a2f79-167">ジョブ ステップのコマンドとして既存の ActiveX スクリプト ファイルを開くこともできます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-167">You can also open an existing ActiveX script file as the command for the job step.</span></span> <span data-ttu-id="a2f79-168">ActiveX スクリプト コマンドは、Microsoft Visual Basic などを使用して外部でコンパイルし、実行可能プログラムとして実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-168">Alternatively, ActiveX script commands can be externally compiled (for example, using Microsoft Visual Basic) and then run as executable programs.</span></span>  
  
 <span data-ttu-id="a2f79-169">ジョブ ステップ コマンドが ActiveX スクリプトの場合は、SQLActiveScriptHost オブジェクトを使用してジョブ ステップ履歴ログに出力するか、COM オブジェクトを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-169">When a job step command is an ActiveX script, you can use the SQLActiveScriptHost object to print output to the job step history log or create COM objects.</span></span> <span data-ttu-id="a2f79-170">SQLActiveScriptHost は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのホスト システムによってスクリプト名前空間に導入されるグローバル オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="a2f79-170">SQLActiveScriptHost is a global object that is introduced by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent hosting system into the script name space.</span></span> <span data-ttu-id="a2f79-171">このオブジェクトには 2 つのメソッドがあります (Print と CreateObject)。</span><span class="sxs-lookup"><span data-stu-id="a2f79-171">The object has two methods (Print and CreateObject).</span></span> <span data-ttu-id="a2f79-172">次の例は、Visual Basic Scripting Edition (VBScript) での ActiveX スクリプティングの動作を示しています。</span><span class="sxs-lookup"><span data-stu-id="a2f79-172">The following example shows how ActiveX scripting works in Visual Basic Scripting Edition (VBScript).</span></span>  
  
```  
' VBScript example for ActiveX Scripting job step  
' Create a Dmo.Server object. The object connects to the  
' server on which the script is running.  
  
Set oServer = CreateObject("SQLDmo.SqlServer")  
oServer.LoginSecure = True  
oServer.Connect "(local)"  
'Disconnect and destroy the server object  
oServer.DisConnect  
Set oServer = nothing
```  
  
## <a name="replication-job-steps"></a><span data-ttu-id="a2f79-173">レプリケーション ジョブ ステップ</span><span class="sxs-lookup"><span data-stu-id="a2f79-173">Replication Job Steps</span></span>  
 <span data-ttu-id="a2f79-174">レプリケーションを使用してパブリケーションとサブスクリプションを作成した場合、既定でレプリケーション ジョブが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-174">When you create publications and subscriptions using replication, replication jobs are created by default.</span></span> <span data-ttu-id="a2f79-175">作成されるジョブの種類は、レプリケーションの種類 (スナップショット レプリケーション、トランザクション レプリケーション、またはマージ レプリケーション) と使用するオプションによって決まります。</span><span class="sxs-lookup"><span data-stu-id="a2f79-175">The type of job created is determined by the type of replication (snapshot, transactional, or merge) and the options used.</span></span>  
  
 <span data-ttu-id="a2f79-176">レプリケーション ジョブ ステップでは、次のレプリケーション エージェントのいずれかがアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="a2f79-176">Replication job steps activate one of these replication agents:</span></span>  
  
-   <span data-ttu-id="a2f79-177">スナップショット エージェント (スナップショット ジョブ)</span><span class="sxs-lookup"><span data-stu-id="a2f79-177">Snapshot Agent (Snapshot job)</span></span>  
  
-   <span data-ttu-id="a2f79-178">ログ リーダー エージェント (LogReader ジョブ)</span><span class="sxs-lookup"><span data-stu-id="a2f79-178">Log Reader Agent (LogReader job)</span></span>  
  
-   <span data-ttu-id="a2f79-179">ディストリビューション エージェント (ディストリビューション ジョブ)</span><span class="sxs-lookup"><span data-stu-id="a2f79-179">Distribution Agent (Distribution job)</span></span>  
  
-   <span data-ttu-id="a2f79-180">マージ エージェント (マージ ジョブ)</span><span class="sxs-lookup"><span data-stu-id="a2f79-180">Merge Agent (Merge job)</span></span>  
  
-   <span data-ttu-id="a2f79-181">キュー リーダー エージェント (QueueReader ジョブ)</span><span class="sxs-lookup"><span data-stu-id="a2f79-181">Queue Reader Agent (QueueReader job)</span></span>  
  
 <span data-ttu-id="a2f79-182">レプリケーションのセットアップ時には、レプリケーション エージェントを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント起動後に連続的に実行するか、要求に応じて実行するか、またはスケジュールに従って実行するかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-182">When replication is set up, you can specify to run the replication agents in one of three ways: continuously after [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is started, on demand, or according to a schedule.</span></span> <span data-ttu-id="a2f79-183">レプリケーション エージェントの詳細については、「 [レプリケーション エージェントの概要](../../relational-databases/replication/agents/replication-agents-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2f79-183">For more information about replication agents, see [Replication Agents Overview](../../relational-databases/replication/agents/replication-agents-overview.md).</span></span>  
  
## <a name="analysis-services-job-steps"></a><span data-ttu-id="a2f79-184">Analysis Services ジョブ ステップ</span><span class="sxs-lookup"><span data-stu-id="a2f79-184">Analysis Services Job Steps</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a2f79-185">エージェントでは、コマンド ジョブ ステップとクエリ ジョブ ステップという 2 種類の Analysis Services ジョブ ステップがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-185">Agent supports two distinct types of Analysis Services job steps, command job steps, and query job steps.</span></span>  
  
### <a name="analysis-services-command-job-steps"></a><span data-ttu-id="a2f79-186">Analysis Services コマンド ジョブ ステップ</span><span class="sxs-lookup"><span data-stu-id="a2f79-186">Analysis Services Command Job Steps</span></span>  
 <span data-ttu-id="a2f79-187">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コマンド ジョブ ステップを作成するには、次の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2f79-187">When you create an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] command job step, you must:</span></span>  
  
-   <span data-ttu-id="a2f79-188">ジョブ ステップが実行される OLAP サーバーのデータベースを特定します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-188">Identify the database OLAP server in which to run the job step.</span></span>  
  
-   <span data-ttu-id="a2f79-189">実行するステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-189">Type the statement to execute.</span></span> <span data-ttu-id="a2f79-190">ステートメントは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] **Execute** メソッドの XML である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2f79-190">The statement must be an XML for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] **Execute** method.</span></span> <span data-ttu-id="a2f79-191">ステートメントには、完全な SOAP エンベロープまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] **Discover** メソッドの XML が含まれていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a2f79-191">The statement may not contain a complete SOAP envelope or an XML for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] **Discover** method.</span></span> <span data-ttu-id="a2f79-192">SOAP エンベロープおよび [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Discover **メソッドは、** ではサポートされていますが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ ステップではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a2f79-192">Notice that, while [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] supports complete SOAP envelopes and the **Discover** method, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps do not.</span></span>  
  
### <a name="analysis-services-query-job-steps"></a><span data-ttu-id="a2f79-193">Analysis Services クエリ ジョブ ステップ</span><span class="sxs-lookup"><span data-stu-id="a2f79-193">Analysis Services Query Job Steps</span></span>  
 <span data-ttu-id="a2f79-194">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] クエリ ジョブ ステップを作成するには、次の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2f79-194">When you create an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] query job step, you must:</span></span>  
  
-   <span data-ttu-id="a2f79-195">ジョブ ステップが実行される OLAP サーバーのデータベースを特定します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-195">Identify the database OLAP server in which to run the job step.</span></span>  
  
-   <span data-ttu-id="a2f79-196">実行するステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-196">Type the statement to execute.</span></span> <span data-ttu-id="a2f79-197">このステートメントでは、多次元式 (MDX) クエリを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2f79-197">The statement must be a multidimensional expressions (MDX) query.</span></span>  
  
 <span data-ttu-id="a2f79-198">MDX の詳細については、「 [Mdx クエリの基礎 &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2f79-198">For more information on MDX, see [MDX Query Fundamentals &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services).</span></span>  
  
## <a name="integration-services-packages"></a><span data-ttu-id="a2f79-199">Integration Services パッケージ</span><span class="sxs-lookup"><span data-stu-id="a2f79-199">Integration Services Packages</span></span>  
 <span data-ttu-id="a2f79-200">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージ ジョブ ステップを作成するには、次の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2f79-200">When you create an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package job step, you must do the following:</span></span>  
  
-   <span data-ttu-id="a2f79-201">パッケージのソースを特定します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-201">Identify the source of the package.</span></span>  
  
-   <span data-ttu-id="a2f79-202">パッケージの場所を特定します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-202">Identify the location of the package.</span></span>  
  
-   <span data-ttu-id="a2f79-203">パッケージに構成ファイルが必要な場合は、構成ファイルを特定します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-203">If configuration files are required for the package, identify the configuration files.</span></span>  
  
-   <span data-ttu-id="a2f79-204">パッケージにコマンド ファイルが必要な場合は、コマンド ファイルを特定します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-204">If command files are required for the package, identify the command files.</span></span>  
  
-   <span data-ttu-id="a2f79-205">パッケージに使用する検証方法を特定します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-205">Identify the verification to use for the package.</span></span> <span data-ttu-id="a2f79-206">たとえば、パッケージに署名や特定のパッケージ ID が必要であることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-206">For example, you can specify that the package must be signed, or that the package must have a specific package ID.</span></span>  
  
-   <span data-ttu-id="a2f79-207">パッケージのデータ ソースを特定します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-207">Identify the data sources for the package.</span></span>  
  
-   <span data-ttu-id="a2f79-208">ログ プロバイダーを特定します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-208">Identify the log providers for the package.</span></span>  
  
-   <span data-ttu-id="a2f79-209">パッケージを実行する前に、変数と値を指定します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-209">Specify variables and values to set before running the package.</span></span>  
  
-   <span data-ttu-id="a2f79-210">実行オプションを特定します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-210">Identify execution options.</span></span>  
  
-   <span data-ttu-id="a2f79-211">コマンド ライン オプションを追加または変更します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-211">Add or modify command-line options.</span></span>  
  
 <span data-ttu-id="a2f79-212">SSIS カタログにパッケージを配置し、 **[SSIS カタログ]** をパッケージのソースとして指定した場合、この構成情報の多くがパッケージから自動的に得られることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a2f79-212">Note that if you deployed the package to the SSIS Catalog and you specify **SSIS Catalog** as the package source, much of this configuration information is obtained automatically from the package.</span></span> <span data-ttu-id="a2f79-213">**[構成]** タブでは、環境、パラメーターの値、接続マネージャーの値、プロパティのオーバーライド設定、およびパッケージが 32 ビット ランタイム環境で実行するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a2f79-213">Under the **Configuration** tab you can specify the environment, parameter values, connection manager values, property overrides, and whether the package runs in a 32-bit runtime environment.</span></span>  
  
 <span data-ttu-id="a2f79-214">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを実行するジョブ ステップの作成に関する詳細については、「 [パッケージに対する SQL Server エージェント ジョブ](../../integration-services/packages/sql-server-agent-jobs-for-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2f79-214">For more information about creating job steps that run [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, see [SQL Server Agent Jobs for Packages](../../integration-services/packages/sql-server-agent-jobs-for-packages.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="a2f79-215">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="a2f79-215">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a2f79-216">**説明**</span><span class="sxs-lookup"><span data-stu-id="a2f79-216">**Description**</span></span>|<span data-ttu-id="a2f79-217">**トピック**</span><span class="sxs-lookup"><span data-stu-id="a2f79-217">**Topic**</span></span>|  
|<span data-ttu-id="a2f79-218">実行可能プログラムを使用してジョブ ステップを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-218">Describes how to create a job step with an executable program.</span></span>|[<span data-ttu-id="a2f79-219">CmdExec ジョブ ステップの作成</span><span class="sxs-lookup"><span data-stu-id="a2f79-219">Create a CmdExec Job Step</span></span>](create-a-cmdexec-job-step.md)|  
|<span data-ttu-id="a2f79-220">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのアクセス許可をリセットする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-220">Describes how to reset [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent permissions.</span></span>|[<span data-ttu-id="a2f79-221">Configure a User to Create and Manage SQL Server Agent Jobs</span><span class="sxs-lookup"><span data-stu-id="a2f79-221">Configure a User to Create and Manage SQL Server Agent Jobs</span></span>](configure-a-user-to-create-and-manage-sql-server-agent-jobs.md)|  
|<span data-ttu-id="a2f79-222">[!INCLUDE[tsql](../../includes/tsql-md.md)] ジョブ ステップを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-222">Describes how to create a [!INCLUDE[tsql](../../includes/tsql-md.md)] job step.</span></span>|[<span data-ttu-id="a2f79-223">Create a Transact-SQL Job Step</span><span class="sxs-lookup"><span data-stu-id="a2f79-223">Create a Transact-SQL Job Step</span></span>](create-a-transact-sql-job-step.md)|  
|<span data-ttu-id="a2f79-224">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント Transact-SQL ジョブ ステップのオプションを定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-224">Describes how to define options for Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Transact-SQL job steps.</span></span>|[<span data-ttu-id="a2f79-225">Define Transact-SQL Job Step Options</span><span class="sxs-lookup"><span data-stu-id="a2f79-225">Define Transact-SQL Job Step Options</span></span>](define-transact-sql-job-step-options.md)|  
|<span data-ttu-id="a2f79-226">ActiveX スクリプト ジョブ ステップを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-226">Describes how to create an ActiveX script job step.</span></span>|[<span data-ttu-id="a2f79-227">Create an ActiveX Script Job Step</span><span class="sxs-lookup"><span data-stu-id="a2f79-227">Create an ActiveX Script Job Step</span></span>](create-an-activex-script-job-step.md)|  
|<span data-ttu-id="a2f79-228">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Analysis Service のコマンドとクエリを実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ ステップを作成し、定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-228">Describes how to create and define [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps that execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Analysis Services commands and queries.</span></span>|[<span data-ttu-id="a2f79-229">Create an Analysis Services Job Step</span><span class="sxs-lookup"><span data-stu-id="a2f79-229">Create an Analysis Services Job Step</span></span>](create-an-analysis-services-job-step.md)|  
|<span data-ttu-id="a2f79-230">ジョブの実行中にエラーが発生した場合に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が実行する必要があるアクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-230">Describes what action [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should take if a failure occurs during job execution.</span></span>|[<span data-ttu-id="a2f79-231">Set Job Step Success or Failure Flow</span><span class="sxs-lookup"><span data-stu-id="a2f79-231">Set Job Step Success or Failure Flow</span></span>](set-job-step-success-or-failure-flow.md)|  
|<span data-ttu-id="a2f79-232">[ジョブ ステップのプロパティ] ダイアログ ボックスにジョブ ステップの詳細を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-232">Describes how to view job step details in the Job Step Properties dialog.</span></span>|[<span data-ttu-id="a2f79-233">View Job Step Information</span><span class="sxs-lookup"><span data-stu-id="a2f79-233">View Job Step Information</span></span>](view-job-step-information.md)|  
|<span data-ttu-id="a2f79-234">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブ ステップのログを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2f79-234">Describes how to delete a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step log.</span></span>|[<span data-ttu-id="a2f79-235">Delete a Job Step Log</span><span class="sxs-lookup"><span data-stu-id="a2f79-235">Delete a Job Step Log</span></span>](delete-a-job-step-log.md)|  
  
## <a name="see-also"></a><span data-ttu-id="a2f79-236">参照</span><span class="sxs-lookup"><span data-stu-id="a2f79-236">See Also</span></span>  
 <span data-ttu-id="a2f79-237">[dbo.sysjobstepslogs &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobstepslogs-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a2f79-237">[dbo.sysjobstepslogs &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobstepslogs-transact-sql) </span></span>  
 <span data-ttu-id="a2f79-238">[ジョブの作成](create-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="a2f79-238">[Create Jobs](create-jobs.md) </span></span>  
 [<span data-ttu-id="a2f79-239">sp_add_job &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a2f79-239">sp_add_job &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
