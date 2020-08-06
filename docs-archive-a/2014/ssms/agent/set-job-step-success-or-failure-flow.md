---
title: ジョブ ステップの成功時または失敗時の動作を設定する方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, action flow logic
- successful jobs [SQL Server]
- failed jobs [SQL Server]
- jobs [SQL Server Agent], action flow logic
ms.assetid: 23041ccf-8a07-41d3-85b9-c449a54b7e1e
author: stevestein
ms.author: sstein
ms.openlocfilehash: fddc5820676cb231b6f0cd5f7151e24d8eceaefa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742734"
---
# <a name="set-job-step-success-or-failure-flow"></a><span data-ttu-id="19a11-102">Set Job Step Success or Failure Flow</span><span class="sxs-lookup"><span data-stu-id="19a11-102">Set Job Step Success or Failure Flow</span></span>
  <span data-ttu-id="19a11-103">エージェントジョブを作成するときに [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、ジョブの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 実行中にエラーが発生した場合に実行するアクションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="19a11-103">When creating [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs, you can specify what action [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should take if a failure occurs during job execution.</span></span> <span data-ttu-id="19a11-104">各ジョブ ステップの成功時または失敗時に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が実行するアクションを決定します。</span><span class="sxs-lookup"><span data-stu-id="19a11-104">Determine the action that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should take upon the success or failure of each job step.</span></span> <span data-ttu-id="19a11-105">その後、次のプロシージャを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用したジョブ ステップ アクション フロー ロジックを構成します。</span><span class="sxs-lookup"><span data-stu-id="19a11-105">Then use the following procedure to configure the job step action flow logic by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
-   <span data-ttu-id="19a11-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="19a11-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="19a11-107">Security</span><span class="sxs-lookup"><span data-stu-id="19a11-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="19a11-108">**ジョブ ステップの成功時または失敗時の動作を設定する方法:**</span><span class="sxs-lookup"><span data-stu-id="19a11-108">**To set job step success or failure flow, using:**</span></span>  
  
     [<span data-ttu-id="19a11-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="19a11-109">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="19a11-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="19a11-110">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="19a11-111">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="19a11-111">SQL Server Management Objects</span></span>](#SMO)  
  
## <a name="before-you-begin"></a><span data-ttu-id="19a11-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="19a11-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="19a11-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="19a11-113">Security</span></span>  
 <span data-ttu-id="19a11-114">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="19a11-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="19a11-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="19a11-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-job-step-success-or-failure-flow"></a><span data-ttu-id="19a11-116">ジョブ ステップの成功時または失敗時の動作を設定するには</span><span class="sxs-lookup"><span data-stu-id="19a11-116">To set job step success or failure flow</span></span>  
  
1.  <span data-ttu-id="19a11-117">**オブジェクト エクスプローラー**で、 **[SQL Server エージェント]**、 **[ジョブ]** の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="19a11-117">In **Object Explorer**, expand **SQL Server Agent**, and then expand **Jobs**.</span></span>  
  
2.  <span data-ttu-id="19a11-118">編集するジョブを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19a11-118">Right-click the job you want to edit, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="19a11-119">**[ステップ]** ページを選択し、ステップをクリックし、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19a11-119">Select the **Steps** page, click a step, and then click **Edit**.</span></span>  
  
4.  <span data-ttu-id="19a11-120">**[ジョブ ステップのプロパティ]** ダイアログ ボックスの **[詳細設定]** ページを選択します。</span><span class="sxs-lookup"><span data-stu-id="19a11-120">In the **Job Step Properties** dialog box, select the **Advanced** page.</span></span>  
  
5.  <span data-ttu-id="19a11-121">**[成功した場合のアクション]** 一覧で、ジョブ ステップが正常に完了した場合に実行するアクションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="19a11-121">In the **On success action**list, click the action to perform if the job step completes successfully.</span></span>  
  
6.  <span data-ttu-id="19a11-122">**[再試行回数]** ボックスに、ジョブ ステップが失敗したと見なされるまでにそのステップを繰り返す回数を 0 ～ 9999 の範囲で入力します。</span><span class="sxs-lookup"><span data-stu-id="19a11-122">In the **Retry attempts** box, enter the number of times from 0 through 9999 that the job step should be repeated before it is considered to have failed.</span></span> <span data-ttu-id="19a11-123">**[再試行回数]** ボックスに 0 を超える値を入力した場合は、ジョブ ステップが再試行されるまでの経過時間 (分単位) を 1 ～ 9999 の範囲で **[再試行間隔 (分)]** ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="19a11-123">If you entered a value greater than 0 in the **Retry attempts** box, enter in the **Retry interval (minutes)** box the number of minutes from 1 through 9999 that must pass before the job step is retried.</span></span>  
  
7.  <span data-ttu-id="19a11-124">**[失敗した場合のアクション]** ボックスの一覧で、ジョブ ステップが失敗した場合に実行するアクションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="19a11-124">In the **On failure action** list, click the action to perform if the job step fails.</span></span>  
  
8.  <span data-ttu-id="19a11-125">ジョブが [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトの場合は、以下の方法から選択できます。</span><span class="sxs-lookup"><span data-stu-id="19a11-125">If the job is a [!INCLUDE[tsql](../../includes/tsql-md.md)] script, you can choose from the following options:</span></span>  
  
    -   <span data-ttu-id="19a11-126">**[出力ファイル]** ボックスに、スクリプトの出力が書き込まれる出力ファイルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="19a11-126">In the **Output file** box, enter the name of an output file to which the script output will be written.</span></span> <span data-ttu-id="19a11-127">既定では、ジョブ ステップの実行ごとに出力ファイルが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="19a11-127">By default the file is overwritten each time the job step executes.</span></span> <span data-ttu-id="19a11-128">出力ファイルを上書きしない場合は、 **[既存のファイルに出力を追加する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="19a11-128">If you do not want the output file overwritten, check **Append output to existing file**.</span></span>  
  
    -   <span data-ttu-id="19a11-129">ジョブ ステップのログをデータベース テーブルに記録する場合は、 **[テーブルにログ記録する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="19a11-129">Check **Log to table** if you want to log the job step to a database table.</span></span> <span data-ttu-id="19a11-130">既定では、ジョブ ステップの実行ごとにテーブルの内容が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="19a11-130">By default the table contents are overwritten each time the job step executes.</span></span> <span data-ttu-id="19a11-131">テーブルの内容を上書きしない場合は、 **[テーブル内の既存のエントリに出力を追加する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="19a11-131">If you do not want the table contents overwritten, check **Append output to existing entry in table**.</span></span> <span data-ttu-id="19a11-132">ジョブ ステップの実行後にこのテーブルのコンテンツを表示するには、 **[表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19a11-132">After the job step executes, you can view the contents of this table by clicking **View**.</span></span>  
  
    -   <span data-ttu-id="19a11-133">ステップの履歴に出力を含める場合は、 **[履歴にステップ出力を含める]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="19a11-133">Check **Include step output in history** if you want the output included in the step's history.</span></span> <span data-ttu-id="19a11-134">エラーがない場合にのみ、出力は表示されます。</span><span class="sxs-lookup"><span data-stu-id="19a11-134">Output will only be shown if there were no errors.</span></span> <span data-ttu-id="19a11-135">また、出力が切り捨てられる場合があります。</span><span class="sxs-lookup"><span data-stu-id="19a11-135">Also, output may be truncated.</span></span>  
  
9. <span data-ttu-id="19a11-136">**[実行時のユーザー]** ボックスの一覧を使用できる場合、ジョブで使用する資格情報を持つプロキシ アカウントを選択します。</span><span class="sxs-lookup"><span data-stu-id="19a11-136">If the **Run as user** list is available, select the proxy account with the credentials that the job will use.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="19a11-137">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="19a11-137">Using Transact-SQL</span></span>  
  
#### <a name="to-set-job-step-success-or-failure-flow"></a><span data-ttu-id="19a11-138">ジョブ ステップの成功時または失敗時の動作を設定するには</span><span class="sxs-lookup"><span data-stu-id="19a11-138">To set job step success or failure flow</span></span>  
  
1.  <span data-ttu-id="19a11-139">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="19a11-139">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="19a11-140">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19a11-140">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="19a11-141">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19a11-141">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @on_success_action = 1;  
    GO  
    ```  
  
 <span data-ttu-id="19a11-142">詳細については、「 [sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19a11-142">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="19a11-143">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="19a11-143">Using SQL Server Management Objects</span></span>  

### <a name="to-set-job-step-success-or-failure-flow"></a><span data-ttu-id="19a11-144">ジョブ ステップの成功時または失敗時の動作を設定するには</span><span class="sxs-lookup"><span data-stu-id="19a11-144">To set job step success or failure flow</span></span>
  
 <span data-ttu-id="19a11-145">`JobStep`Visual Basic、Visual C#、PowerShell など、選択したプログラミング言語でクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="19a11-145">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="19a11-146">詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](https://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19a11-146">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
