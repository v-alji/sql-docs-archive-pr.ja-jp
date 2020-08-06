---
title: Analysis Services ジョブ ステップの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [Analysis Services]
ms.assetid: 03d4bb86-514b-4a55-97b9-c2c0fa08b428
author: stevestein
ms.author: sstein
ms.openlocfilehash: ed0e63c22d4cad270bcb544b03decba269e4f43a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715062"
---
# <a name="create-an-analysis-services-job-step"></a><span data-ttu-id="8d99e-102">Create an Analysis Services Job Step</span><span class="sxs-lookup"><span data-stu-id="8d99e-102">Create an Analysis Services Job Step</span></span>
  <span data-ttu-id="8d99e-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、または SQL Server 管理オブジェクトを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Analysis Services のコマンドとクエリを実行する [!INCLUDE[tsql](../../includes/tsql-md.md)] エージェント ジョブ ステップの作成と定義方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8d99e-103">This topic describes how to create and define [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Analysis Services commands and queries by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  
  
-   <span data-ttu-id="8d99e-104">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="8d99e-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8d99e-105">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="8d99e-105">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="8d99e-106">Security</span><span class="sxs-lookup"><span data-stu-id="8d99e-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8d99e-107">**Analysis Services コマンドまたはクエリを使用する SQL Server ジョブ ステップを作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="8d99e-107">**To create a SQL Server job steps using Analysis Services commands and/or queries, with:**</span></span>  
  
     [<span data-ttu-id="8d99e-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8d99e-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="8d99e-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8d99e-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="8d99e-110">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="8d99e-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8d99e-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="8d99e-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8d99e-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="8d99e-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="8d99e-113">ジョブ ステップで Analysis Services コマンドを使用する場合、コマンド ステートメントは XML for Analysis Services の **Execute** メソッドである必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d99e-113">If the job step uses an Analysis Services command, the command statement must be an XML for Analysis Services **Execute** method.</span></span> <span data-ttu-id="8d99e-114">ステートメントには、完全な SOAP (Simple Object Access Protocol) エンベロープまたは XML for Analysis の **Discover** メソッドを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="8d99e-114">The statement may not contain a complete Simple Object Access Protocol (SOAP) envelope or an XML for Analysis **Discover** method.</span></span> <span data-ttu-id="8d99e-115">完全な SOAP エンベロープと [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Discover **メソッドは、** ではサポートされていますが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ ステップではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8d99e-115">While [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] supports complete SOAP envelopes and the **Discover** method, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps do not.</span></span> <span data-ttu-id="8d99e-116">XML for Analysis Services の詳細については、「 [XML for Analysis の概要 (XMLA)](https://msdn.microsoft.com/library/ms187190.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d99e-116">For more information about XML for Analysis Services, see [XML for Analysis Overview (XMLA)](https://msdn.microsoft.com/library/ms187190.aspx).</span></span>  
  
-   <span data-ttu-id="8d99e-117">ジョブ ステップで Analysis Services クエリを使用する場合、クエリ ステートメントは多次元式 (MDX) クエリである必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d99e-117">If the job step uses an Analysis Services query, the query statement must be a multidimensional expressions (MDX) query.</span></span> <span data-ttu-id="8d99e-118">MDX の詳細については、「 [Mdx クエリの基礎 &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d99e-118">For more information about MDX, see [MDX Query Fundamentals &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8d99e-119">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="8d99e-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8d99e-120">Permissions</span><span class="sxs-lookup"><span data-stu-id="8d99e-120">Permissions</span></span>  
  
-   <span data-ttu-id="8d99e-121">Analysis Services サブシステムを使用するジョブ ステップを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーであるか、このサブシステム用に定義された有効なプロキシ アカウントへアクセスできるユーザーだけです。</span><span class="sxs-lookup"><span data-stu-id="8d99e-121">To run a job step that uses the Analysis Services subsystem, a user must be a member of the **sysadmin** fixed server role or have access to a valid proxy account defined to use this subsystem.</span></span> <span data-ttu-id="8d99e-122">さらに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントまたはプロキシは、Analysis Services 管理者であり、かつ有効な Windows ドメイン アカウントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d99e-122">In addition, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account or the proxy must be an Analysis Services administrator and a valid Windows domain account.</span></span>  
  
-   <span data-ttu-id="8d99e-123">**sysadmin** 固定サーバー ロールのメンバーのみがジョブ ステップ出力をファイルに書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="8d99e-123">Only members of the **sysadmin** fixed server role can write job step output to a file.</span></span> <span data-ttu-id="8d99e-124">**msdb** データベースで **SQLAgentUserRole** データベース ロールのメンバーであるユーザーによってジョブ ステップが実行される場合、出力はテーブルのみに書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="8d99e-124">If the job step is run by users who are members of the **SQLAgentUserRole** database role in the **msdb** database, then the output can be written only to a table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8d99e-125">エージェントによって **SQLAgentUserRole** データベースの **SQLAgentUserRole** テーブルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="8d99e-125">Agent writes job step output to the **sysjobstepslog** table in the **msdb** database.</span></span>  
  
-   <span data-ttu-id="8d99e-126">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8d99e-126">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="8d99e-127">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="8d99e-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-an-analysis-services-command-job-step"></a><span data-ttu-id="8d99e-128">Analysis Services コマンド ジョブ ステップを作成するには</span><span class="sxs-lookup"><span data-stu-id="8d99e-128">To create an Analysis Services command job step</span></span>  
  
1.  <span data-ttu-id="8d99e-129">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="8d99e-129">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="8d99e-130">**[SQL Server エージェント]** を展開し、新しいジョブを作成するか、既存のジョブを右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8d99e-130">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="8d99e-131">ジョブの作成の詳細については、「 [ジョブの作成](create-jobs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d99e-131">For more information on creating a job, see [Create Jobs](create-jobs.md).</span></span>  
  
3.  <span data-ttu-id="8d99e-132">**[ジョブのプロパティ]** ダイアログ ボックスで **[ステップ]** タブをクリックし、 **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8d99e-132">In the **Job Properties** dialog box, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="8d99e-133">**[新しいジョブ ステップ]** ダイアログ ボックスで、ジョブの **[ステップ名]** を入力します。</span><span class="sxs-lookup"><span data-stu-id="8d99e-133">In the **New Job Step** dialog box, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="8d99e-134">**[種類]** ボックスの一覧で、 **[SQL Server Analysis Services コマンド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8d99e-134">In the **Type** list, click **SQL Server Analysis Services Command**.</span></span>  
  
6.  <span data-ttu-id="8d99e-135">**[実行するアカウント名]** ボックスの一覧で、その Analysis Services コマンド サブシステムを使用するように定義済みのプロキシを選択します。</span><span class="sxs-lookup"><span data-stu-id="8d99e-135">In the **Run as** list, select a proxy that has been defined to use the Analysis Services Command subsystem.</span></span> <span data-ttu-id="8d99e-136">ユーザーが **sysadmin** 固定サーバー ロールのメンバーである場合は、 **[SQL エージェント サービスのアカウント]** を使用してこのジョブ ステップを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="8d99e-136">A user who is a member of the **sysadmin** fixed server role can also select **SQL Agent Service Account** to run this job step.</span></span>  
  
7.  <span data-ttu-id="8d99e-137">**[サーバー]** でジョブ ステップを実行するサーバーを選択するか、サーバー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="8d99e-137">Select the **Server** where the job step will run, or type the server name.</span></span>  
  
8.  <span data-ttu-id="8d99e-138">実行するステートメントを **[コマンド]** ボックスに入力します。または、 **[開く]** をクリックしてステートメントを選択します。</span><span class="sxs-lookup"><span data-stu-id="8d99e-138">In the **Command** box, type the statement to execute, or click **Open** to select a statement.</span></span>  
  
9. <span data-ttu-id="8d99e-139">**[詳細設定]** ページをクリックして、ジョブ ステップが成功または失敗した場合に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが実行するアクション、ジョブ ステップの試行回数、ジョブ ステップ出力の出力先など、このジョブ ステップに関するさまざまなオプションを定義します。</span><span class="sxs-lookup"><span data-stu-id="8d99e-139">Click the **Advanced** page to define options for this job step, such as what action [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should take if the job step succeeds or fails, how many times the job step should be attempted, and where the job step output should be written.</span></span>  
  
#### <a name="to-create-an-analysis-services-query-job-step"></a><span data-ttu-id="8d99e-140">Analysis Services クエリ ジョブ ステップを作成するには</span><span class="sxs-lookup"><span data-stu-id="8d99e-140">To create an Analysis Services query job step</span></span>  
  
1.  <span data-ttu-id="8d99e-141">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="8d99e-141">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="8d99e-142">**[SQL Server エージェント]** を展開し、新しいジョブを作成するか、既存のジョブを右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8d99e-142">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="8d99e-143">ジョブの作成の詳細については、「 [ジョブの作成](create-jobs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d99e-143">For more information on creating a job, see [Create Jobs](create-jobs.md).</span></span>  
  
3.  <span data-ttu-id="8d99e-144">**[ジョブのプロパティ]** ダイアログで **[ステップ]** ページをクリックし、 **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8d99e-144">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="8d99e-145">**[新しいジョブ ステップ]** ダイアログの **[ステップ名]** ボックスにジョブ ステップ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="8d99e-145">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="8d99e-146">**[種類]** ボックスの一覧で、 **[SQL Server Analysis Services クエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8d99e-146">In the **Type** list, click **SQL Server Analysis Services Query**.</span></span>  
  
6.  <span data-ttu-id="8d99e-147">**[実行するアカウント名]** ボックスの一覧で、その Analysis Services クエリ サブシステムを使用するように定義済みのプロキシを選択します。</span><span class="sxs-lookup"><span data-stu-id="8d99e-147">In the **Run as** list, select a proxy that has been defined to use the Analysis Services Query subsystem.</span></span> <span data-ttu-id="8d99e-148">ユーザーが **sysadmin** 固定サーバー ロールのメンバーである場合は、 **[SQL エージェント サービスのアカウント]** を使用してこのジョブ ステップを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="8d99e-148">A user who is a member of the **sysadmin** fixed server role can also select **SQL Agent Service Account** to run this job step.</span></span>  
  
7.  <span data-ttu-id="8d99e-149">**[サーバー]** および **[データベース]** で、ジョブ ステップを実行するサーバーとデータベースを選択するか、サーバー名またはデータベース名を直接入力します。</span><span class="sxs-lookup"><span data-stu-id="8d99e-149">Select the **Server** and the **Database** where the job step will run, or type the server or database name.</span></span>  
  
8.  <span data-ttu-id="8d99e-150">実行するステートメントを **[コマンド]** ボックスに入力します。または、 **[開く]** をクリックしてステートメントを選択します。</span><span class="sxs-lookup"><span data-stu-id="8d99e-150">In the **Command** box, type the statement to execute, or click **Open** to select a statement.</span></span>  
  
9. <span data-ttu-id="8d99e-151">**[詳細設定]** ページをクリックして、ジョブ ステップが成功または失敗した場合に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが実行するアクション、ジョブ ステップの試行回数、ジョブ ステップ出力の出力先など、このジョブ ステップに関するさまざまなオプションを定義します。</span><span class="sxs-lookup"><span data-stu-id="8d99e-151">Click the **Advanced** page to define options for this job step, such as what action [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should take if the job step succeeds or fails, how many times the job step should be attempted, and where the job step output should be written.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="8d99e-152">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="8d99e-152">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-analysis-services-command-job-step"></a><span data-ttu-id="8d99e-153">Analysis Services コマンド ジョブ ステップを作成するには</span><span class="sxs-lookup"><span data-stu-id="8d99e-153">To create an Analysis Services command job step</span></span>  
  
1.  <span data-ttu-id="8d99e-154">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="8d99e-154">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8d99e-155">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8d99e-155">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8d99e-156">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8d99e-156">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- Creates a job step that uses XMLA to create a relational data source that references the AdventureWorks2012 Microsoft SQL Server database  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Create a relational data source that references the AdventureWorks2012 Microsoft SQL Server database ',  
        @subsystem = N'ANALYSISCOMMAND',  
        @command = N' <Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
        <ParentObject>  
            <DatabaseID>AdventureWorks2012</DatabaseID>  
        </ParentObject>  
        <ObjectDefinition>  
            <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
                <ID>AdventureWorks2012</ID>  
                <Name>Adventure Works 2012</Name>  
                <ConnectionString>Data Source=localhost;Initial Catalog=AdventureWorks2012;Integrated Security=True</ConnectionString>  
                <ImpersonationInfo>  
                    <ImpersonationMode>ImpersonateServiceAccount</ImpersonationMode>  
                </ImpersonationInfo>  
                <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
                <Timeout>PT0S</Timeout>  
            </DataSource>  
        </ObjectDefinition>  
    </Create>', ;  
    GO  
    ```  
  
 <span data-ttu-id="8d99e-157">詳細については、「 [sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d99e-157">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
#### <a name="to-create-an-analysis-services-query-job-step"></a><span data-ttu-id="8d99e-158">Analysis Services クエリ ジョブ ステップを作成するには</span><span class="sxs-lookup"><span data-stu-id="8d99e-158">To create an Analysis Services query job step</span></span>  
  
1.  <span data-ttu-id="8d99e-159">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="8d99e-159">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8d99e-160">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8d99e-160">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8d99e-161">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8d99e-161">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- Creates a job step that uses MDX to return data  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Returns the Internet sales amount by state',  
        @subsystem = N'ANALYSISQUERY',  
        @command = N' SELECT  
       [Measures].[Internet Sales Amount] ON COLUMNS,  
       [Customer].[State-Province].Members ON ROWS  
    FROM [AdventureWorks2012]',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 <span data-ttu-id="8d99e-162">詳細については、「 [sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d99e-162">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="8d99e-163">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="8d99e-163">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="8d99e-164">**PowerShell スクリプト ジョブ ステップを作成するには**</span><span class="sxs-lookup"><span data-stu-id="8d99e-164">**To create a PowerShell Script job step**</span></span>  
  
 <span data-ttu-id="8d99e-165">選択した XMLA や MDX などのプログラミング言語で、`JobStep` クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="8d99e-165">Use the `JobStep` class by using a programming language that you choose, such as XMLA or MDX.</span></span> <span data-ttu-id="8d99e-166">詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](https://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d99e-166">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
