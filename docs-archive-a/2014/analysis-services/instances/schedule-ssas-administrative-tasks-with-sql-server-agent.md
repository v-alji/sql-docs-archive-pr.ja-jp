---
title: SQL Server エージェント | で SSAS 管理タスクのスケジュールを設定するMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2d1484b3-51d9-48a0-93d2-0c3e4ed22b87
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2c78fa5fcebc0589ba863163b93ad2d10731b75a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716929"
---
# <a name="schedule-ssas-administrative-tasks-with-sql-server-agent"></a><span data-ttu-id="9375e-102">SQL Server エージェントで SSAS 管理タスクのスケジュール設定を行う</span><span class="sxs-lookup"><span data-stu-id="9375e-102">Schedule SSAS Administrative Tasks with SQL Server Agent</span></span>
  <span data-ttu-id="9375e-103">SQL Server エージェント サービスを使用すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の管理タスクのスケジュールを設定して、必要なときに必要な順序で実行できます。</span><span class="sxs-lookup"><span data-stu-id="9375e-103">Using the SQL Server Agent service, you can schedule [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrative tasks to run in the order and times that you need.</span></span> <span data-ttu-id="9375e-104">定期タスクは、一定の周期または指定した周期で実行されるプロセスを自動化するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9375e-104">Scheduled tasks help you automate processes that run on regular or predictable cycles.</span></span> <span data-ttu-id="9375e-105">キューブ処理などの管理タスクは、ビジネス活動が盛んでない時間帯に実行されるようにスケジュールできます。</span><span class="sxs-lookup"><span data-stu-id="9375e-105">You can schedule administrative tasks, such as cube processing, to run during times of slow business activity.</span></span> <span data-ttu-id="9375e-106">また、SQL Server エージェント ジョブでジョブ ステップを作成することにより、タスクの実行順序を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9375e-106">You can also determine the order in which tasks run by creating job steps within a SQL Server Agent job.</span></span> <span data-ttu-id="9375e-107">たとえば、キューブを処理した後でバックアップを実行できます。</span><span class="sxs-lookup"><span data-stu-id="9375e-107">For example, you can process a cube and then perform a backup of the cube.</span></span>  
  
 <span data-ttu-id="9375e-108">ジョブ ステップを使用すると、実行フローを制御できます。</span><span class="sxs-lookup"><span data-stu-id="9375e-108">Job steps give you control over flow of execution.</span></span> <span data-ttu-id="9375e-109">あるジョブが失敗した場合に、残りのタスクを引き続き実行するか、実行を停止するように、SQL Server エージェントを構成できます。</span><span class="sxs-lookup"><span data-stu-id="9375e-109">If one job fails, you can configure SQL Server Agent to continue to run the remaining tasks or to stop execution.</span></span> <span data-ttu-id="9375e-110">また SQL Server エージェントを、ジョブ実行の成否についての通知を送信するように構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="9375e-110">You can also configure SQL Server Agent to send notifications about the success or failure of job execution.</span></span>  
  
 <span data-ttu-id="9375e-111">このトピックでは、SQL Server エージェントを使用して XMLA スクリプトを実行する方法を 2 つ紹介します。</span><span class="sxs-lookup"><span data-stu-id="9375e-111">This topic is a walkthrough that shows two ways of using SQL Server Agent to run XMLA script.</span></span> <span data-ttu-id="9375e-112">最初の例では、単一のディメンションの処理をスケジュール設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9375e-112">The first example demonstrates how to schedule processing of a single dimension.</span></span> <span data-ttu-id="9375e-113">2 番目の例では、スケジュールに従って実行される単一のスクリプトに複数の処理タスクを組み合わせる方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9375e-113">Example two shows how to combine processing tasks into a single script that runs on a schedule.</span></span> <span data-ttu-id="9375e-114">このチュートリアルを完了するには、次の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="9375e-114">To complete this walkthrough, you will need to meet the following prerequisites.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9375e-115">前提条件</span><span class="sxs-lookup"><span data-stu-id="9375e-115">Prerequisites</span></span>  
 <span data-ttu-id="9375e-116">SQL Server エージェント サービスがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9375e-116">SQL Server Agent service must be installed.</span></span>  
  
 <span data-ttu-id="9375e-117">既定では、ジョブはサービス アカウントで実行されます。</span><span class="sxs-lookup"><span data-stu-id="9375e-117">By default, jobs run under the service account.</span></span> <span data-ttu-id="9375e-118">で [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] は、SQL Server エージェントの既定のアカウントは NT Service\ SQLAgent $ \<instancename> です。</span><span class="sxs-lookup"><span data-stu-id="9375e-118">In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], the default account for SQL Server Agent is NT Service\SQLAgent$\<instancename>.</span></span> <span data-ttu-id="9375e-119">バックアップまたは処理タスクを実行するには、このアカウントが Analysis Services インスタンスのシステム管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9375e-119">To perform a backup or processing task, this account must be a system administrator on the Analysis Services instance.</span></span> <span data-ttu-id="9375e-120">詳細については、「 [Analysis Services&#41;&#40;サーバー管理者のアクセス許可を付与](grant-server-admin-rights-to-an-analysis-services-instance.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9375e-120">For more information, see [Grant Server Administrator Permissions &#40;Analysis Services&#41;](grant-server-admin-rights-to-an-analysis-services-instance.md).</span></span>  
  
 <span data-ttu-id="9375e-121">操作対象のテスト データベースも必要です。</span><span class="sxs-lookup"><span data-stu-id="9375e-121">You should also have a test database to work with.</span></span> <span data-ttu-id="9375e-122">AdventureWorks 多次元サンプル データベースまたはプロジェクトを Analysis Services 多次元チュートリアルから配置して、このチュートリアルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="9375e-122">You can deploy the AdventureWorks multidimensional sample database or a project from the Analysis Services multidimensional tutorial to use in this walkthrough.</span></span> <span data-ttu-id="9375e-123">詳細については、「 [Analysis Services 多次元モデリング チュートリアル用のサンプル データおよびプロジェクトのインストール](../install-sample-data-and-projects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9375e-123">For more information, see [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](../install-sample-data-and-projects.md).</span></span>  
  
## <a name="example-1-processing-a-dimension-in-a-scheduled-task"></a><span data-ttu-id="9375e-124">例 1: 定期タスクでのディメンションの処理</span><span class="sxs-lookup"><span data-stu-id="9375e-124">Example 1: Processing a dimension in a scheduled task</span></span>  
 <span data-ttu-id="9375e-125">この例では、ディメンションを処理するジョブを作成し、スケジュール設定を行う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9375e-125">This example demonstrates how to create and schedule a job that processes a dimension.</span></span>  
  
 <span data-ttu-id="9375e-126">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の定期タスクは、SQL Server エージェント ジョブに組み込まれる XMLA スクリプトです。</span><span class="sxs-lookup"><span data-stu-id="9375e-126">An [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] scheduled task is an XMLA script that is embedded into a SQL Server Agent job.</span></span> <span data-ttu-id="9375e-127">このジョブは、指定した時刻と頻度で実行されるようにスケジュールされます。</span><span class="sxs-lookup"><span data-stu-id="9375e-127">This job is scheduled to run at desired times and frequency.</span></span> <span data-ttu-id="9375e-128">SQL Server エージェントは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の一部なので、管理タスクの作成およびスケジュール設定には、データベース エンジンおよび [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="9375e-128">Because the SQL Server Agent is part of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you work with both the Database Engine and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to create and schedule an administrative task.</span></span>  
  
###  <a name="create-a-script-for-processing-a-dimension-in-a-sql-server-agent-job"></a><a name="bkmk_CreateScript"></a><span data-ttu-id="9375e-129">SQL Server エージェントジョブでディメンションを処理するスクリプトを作成する</span><span class="sxs-lookup"><span data-stu-id="9375e-129">Create a script for processing a dimension in a SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="9375e-130">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="9375e-130">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="9375e-131">データベース フォルダーを開き、ディメンションを検索します。</span><span class="sxs-lookup"><span data-stu-id="9375e-131">Open a database folder and find a dimension.</span></span> <span data-ttu-id="9375e-132">ディメンションを右クリックし、 **[処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-132">Right-click the dimension and select **Process**.</span></span>  
  
2.  <span data-ttu-id="9375e-133">**[ディメンションの処理]** ダイアログ ボックスにある **[オブジェクト一覧]** の **[処理オプション]** 列で、この列のオプションが **[完全処理]** であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9375e-133">In the **Process Dimension** dialog box, in the **Process Options** column under **Object list**, verify that the option for this column is **Process Full**.</span></span> <span data-ttu-id="9375e-134">別のオプションが設定されている場合、 **[処理オプション]** 列のオプションをクリックし、表示される一覧から **[完全処理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9375e-134">If it is not, under **Process Options**, click the option, and then select **Process Full** from the drop-down list.</span></span>  
  
3.  <span data-ttu-id="9375e-135">**[スクリプト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-135">Click **Script**.</span></span>  
  
     <span data-ttu-id="9375e-136">この手順により、ディメンションを処理する XMLA スクリプトを含む **XML クエリ** ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9375e-136">This step opens an **XML Query** window that contains the XMLA script that processes the dimension.</span></span>  
  
4.  <span data-ttu-id="9375e-137">**[ディメンションの処理]** ダイアログ ボックスで、 **[キャンセル]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="9375e-137">In the **Process Dimension** dialog box, click **Cancel** to close the dialog box.</span></span>  
  
5.  <span data-ttu-id="9375e-138">**XMLA クエリ** ウィンドウで、強調表示された XMLA スクリプトを右クリックし、 **[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-138">In the **XMLA Query** window, highlight the XMLA script, right-click the highlighted script, and select **Copy**.</span></span>  
  
     <span data-ttu-id="9375e-139">この手順により、XMLA スクリプトが Windows クリップボードにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="9375e-139">This step copies the XMLA script to the Windows Clipboard.</span></span> <span data-ttu-id="9375e-140">XMLA スクリプトをクリップボードに残しておくか、メモ帳または別のテキスト エディターに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="9375e-140">You can leave the XMLA script in the Clipboard or paste it into Notepad or another text editor.</span></span> <span data-ttu-id="9375e-141">XMLA スクリプトの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9375e-141">The following is an example of the XMLA script.</span></span>  
  
    ```  
    <Batch xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
     <Parallel>  
      <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
        <Object>  
          <DatabaseID>Adventure Works DW Multidimensional</DatabaseID>  
          <DimensionID>Dim Account</DimensionID>  
        </Object>  
        <Type>ProcessFull</Type>  
        <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
      </Process>  
     </Parallel>  
    </Batch>  
    ```  
  
###  <a name="create-and-schedule-the-dimension-processing-job"></a><a name="bkmk_ProcessJob"></a><span data-ttu-id="9375e-142">ディメンション処理ジョブの作成とスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="9375e-142">Create and schedule the dimension processing job</span></span>  
  
1.  <span data-ttu-id="9375e-143">データベース エンジンのインスタンスに接続し、オブジェクト エクスプローラーを開きます。</span><span class="sxs-lookup"><span data-stu-id="9375e-143">Connect to an instance of the Database Engine and then open Object Explorer.</span></span>  
  
2.  <span data-ttu-id="9375e-144">**[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="9375e-144">Expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="9375e-145">**[ジョブ]** を右クリックし、 **[新しいジョブ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-145">Right-click **Jobs** and select **New Job**.</span></span>  
  
4.  <span data-ttu-id="9375e-146">**[新しいジョブ]** ダイアログ ボックスで、 **[名前]** ボックスにジョブ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="9375e-146">In the **New Job** dialog box, enter a job name in **Name**.</span></span>  
  
5.  <span data-ttu-id="9375e-147">**[ページの選択]** で、 **[ステップ]** を選択し、 **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-147">Under **Select a page**, select **Steps**, and then click **New**.</span></span>  
  
6.  <span data-ttu-id="9375e-148">**[新しいジョブ ステップ]** ダイアログ ボックスで、 **[ステップ名]** にステップ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="9375e-148">In the **New Job Step** dialog box, enter a step name in **Step Name**.</span></span>  
  
7.  <span data-ttu-id="9375e-149">[**サーバー**] で、既定のインスタンスの場合は「 **localhost** 」、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 名前付きインスタンスの場合は「 \*\*localhost \\ \*\* 」と入力し \<*instance name*> ます。</span><span class="sxs-lookup"><span data-stu-id="9375e-149">In **Server**, type **localhost** for a default instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and **localhost\\**\<*instance name*> for a named instance.</span></span>  
  
     <span data-ttu-id="9375e-150">リモート コンピューターからジョブを実行する場合は、ジョブが実行されるサーバー名およびインスタンス名を使用します。</span><span class="sxs-lookup"><span data-stu-id="9375e-150">If you will be running the job from a remote computer, use the server name and instance name where the job will run.</span></span> <span data-ttu-id="9375e-151">既定のインスタンスの場合は形式を使用し、 \<*server name*> \<*server name*> \\ < 名前付きインスタンスの場合は*インスタンス名*> を使用します。</span><span class="sxs-lookup"><span data-stu-id="9375e-151">Use the format \<*server name*> for a default instance, and \<*server name*>\\<*instance name*> for a named instance.</span></span>  
  
8.  <span data-ttu-id="9375e-152">**[種類]** で、 **[SQL Server Analysis Services コマンド]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9375e-152">In **Type**, select **SQL Server Analysis Services Command**.</span></span>  
  
9. <span data-ttu-id="9375e-153">**[コマンド]** で、右クリックして **[貼り付け]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9375e-153">In **Command**, right-click and select **Paste**.</span></span> <span data-ttu-id="9375e-154">前の手順で生成した XMLA スクリプトがコマンド ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9375e-154">The XMLA script that you generated in the previous step should appear in the command window.</span></span>  
  
10. <span data-ttu-id="9375e-155">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-155">Click **OK**.</span></span>  
  
11. <span data-ttu-id="9375e-156">**[ページの選択]** で、 **[スケジュール]** をクリックし、 **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-156">Under **Select a page**, click **Schedules**, and then click **New**.</span></span>  
  
12. <span data-ttu-id="9375e-157">**[新しいジョブ スケジュール]** ダイアログ ボックスで、 **[名前]** ボックスにスケジュール名を入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-157">In the **New Job Schedule** dialog box, enter a schedule name in **Name**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="9375e-158">この手順により、日曜日午前 12 時 00 分のスケジュールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9375e-158">This step creates a schedule for Sunday at 12:00 AM.</span></span> <span data-ttu-id="9375e-159">次の手順では、ジョブを手動で実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9375e-159">The next step shows you how to manually execute the job.</span></span> <span data-ttu-id="9375e-160">ジョブを監視しているときに、ジョブを実行するスケジュールを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="9375e-160">You can also specify a schedule that executes the job when you are monitoring it.</span></span>  
  
13. <span data-ttu-id="9375e-161">**[新しいジョブ]** ダイアログ ボックスで、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-161">In the **New Job** dialog box, click **OK**.</span></span>  
  
14. <span data-ttu-id="9375e-162">**オブジェクト エクスプローラー**で、 **[ジョブ]** を展開し、作成したジョブを右クリックして、 **[ステップでジョブを開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-162">In **Object Explorer**, expand **Jobs**, right-click the job you created, and then select **Start Job at Step**.</span></span>  
  
     <span data-ttu-id="9375e-163">このジョブにはステップが 1 つしかないため、すぐにジョブが実行されます。</span><span class="sxs-lookup"><span data-stu-id="9375e-163">Because the job has only one step, the job executes immediately.</span></span> <span data-ttu-id="9375e-164">ジョブに複数のステップが含まれている場合、ジョブを開始するステップを選択できます。</span><span class="sxs-lookup"><span data-stu-id="9375e-164">If the job contains more than one step, you can select the step at which the job should start.</span></span>  
  
15. <span data-ttu-id="9375e-165">ジョブが完了したら、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-165">When the job finishes, click **Close**.</span></span>  
  
## <a name="example-2-batch-processing-a-dimension-and-a-partition-in-a-scheduled-task"></a><span data-ttu-id="9375e-166">例 2: 定期タスクでのディメンションおよびパーティションのバッチ処理</span><span class="sxs-lookup"><span data-stu-id="9375e-166">Example 2: Batch processing a dimension and a partition in a scheduled task</span></span>  
 <span data-ttu-id="9375e-167">この例の手順では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のデータベース ディメンションをバッチ処理するジョブを作成してスケジュールを設定する方法と、そのディメンションに集計で依存するキューブ パーティションを処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9375e-167">The procedures in this example demonstrate how to create and schedule a job that batch processes an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database dimension, and at the same time to process a  cube partition that depends on the dimension for aggregation.</span></span> <span data-ttu-id="9375e-168">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトのバッチ処理の詳細については、「[バッチ処理 (Analysis Services)](../multidimensional-models/batch-processing-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9375e-168">For more information about batch processing of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects, see [Batch Processing &#40;Analysis Services&#41;](../multidimensional-models/batch-processing-analysis-services.md).</span></span>  
  
###  <a name="create-a-script-for-batch-processing-a-dimension-and-partition-in-a-sql-server-agent-job"></a><a name="bkmk_BatchProcess"></a><span data-ttu-id="9375e-169">SQL Server エージェントジョブでディメンションとパーティションをバッチ処理するためのスクリプトを作成する</span><span class="sxs-lookup"><span data-stu-id="9375e-169">Create a script for batch processing a dimension and partition in a SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="9375e-170">同じデータベースを使用して、 **[ディメンション]** を展開し、 **[Customer]** ディメンションを右クリックして **[処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-170">Using the same database, expand **Dimensions**, right-click the **Customer** dimension, and select **Process**.</span></span>  
  
2.  <span data-ttu-id="9375e-171">**[ディメンションの処理]** ダイアログ ボックスにある **[オブジェクト一覧]** の **[処理オプション]** 列で、この列のオプションが **[完全処理]** であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9375e-171">In the **Process Dimension** dialog box, in **Process Options** column under **Object list**, verify that the option for this column is **Process Full**.</span></span>  
  
3.  <span data-ttu-id="9375e-172">**[スクリプト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-172">Click **Script**.</span></span>  
  
     <span data-ttu-id="9375e-173">この手順により、ディメンションを処理する XMLA スクリプトを含む **XML クエリ** ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9375e-173">This step opens an **XML Query** window that contains the XMLA script that processes the dimension.</span></span>  
  
4.  <span data-ttu-id="9375e-174">**[ディメンションの処理]** ダイアログ ボックスで、 **[キャンセル]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="9375e-174">In the **Process Dimension** dialog box, click **Cancel** to close the dialog box.</span></span>  
  
5.  <span data-ttu-id="9375e-175">**[キューブ]**、 **[Adventure Works]**、 **[メジャー グループ]**、 **[インターネット販売]**、 **[パーティション]** の順に展開し、一覧の最後のパーティションを右クリックして **[処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-175">Expand **Cubes**, expand **Adventure Works**, expand **Measure Groups**, expand **Internet Sales**, expand **Partitions**, right-click the last partition in the list, and then select **Process**.</span></span>  
  
6.  <span data-ttu-id="9375e-176">**[パーティションの処理]** ダイアログ ボックスにある **[オブジェクト一覧]** の **[処理オプション]** 列で、この列のオプションが **[完全処理]** であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9375e-176">In the **Process Partition** dialog box, in the **Process Options** column under **Object list**, verify that the option for this column is **Process Full**.</span></span>  
  
7.  <span data-ttu-id="9375e-177">**[スクリプト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-177">Click **Script**.</span></span>  
  
     <span data-ttu-id="9375e-178">この手順により、パーティションを処理する XMLA スクリプトを含む 2 番目の **XML クエリ** ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9375e-178">This step opens a second **XML Query** window that contains the XMLA script that processes the partition.</span></span>  
  
8.  <span data-ttu-id="9375e-179">**[パーティションの処理]** ダイアログ ボックスで、 **[キャンセル]** をクリックしてエディターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="9375e-179">In the **Process Partition** dialog box, click **Cancel** to close the editor.</span></span>  
  
     <span data-ttu-id="9375e-180">この時点で、2 つのスクリプトをマージし、ディメンションが最初に処理されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9375e-180">At this point you must merge the two scripts, and ensure that the dimension is processed first.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="9375e-181">パーティションが最初に処理された場合、後続のディメンション処理により、パーティションが未処理になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9375e-181">If the partition is processed first, the subsequent dimension processing causes the partition to become unprocessed.</span></span> <span data-ttu-id="9375e-182">その場合、パーティションを処理済みの状態にするには、2 番目の処理が必要です。</span><span class="sxs-lookup"><span data-stu-id="9375e-182">The partition would then require a second processing to reach a processed state.</span></span>  
  
9. <span data-ttu-id="9375e-183">パーティションを処理する XMLA スクリプトを含む **XMLA クエリ** ウィンドウで、 `Batch` タグおよび `Parallel` タグの内側にあるコードを強調表示し、強調表示されたスクリプトを右クリックして **[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-183">In the **XMLA Query** window that contains the XMLA script that processes the partition, highlight the code inside the `Batch` and `Parallel` tags, right-click the highlighted script, and select **Copy**.</span></span>  
  
    ```  
    <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
        <Object>  
          <DatabaseID> Adventure Works DW Multidimensional</DatabaseID>  
          <CubeID>Adventure Works</CubeID>  
          <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
          <PartitionID> Internet_Sales_2004</PartitionID>  
        </Object>  
        <Type>ProcessFull</Type>  
        <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
      </Process>  
    ```  
  
10. <span data-ttu-id="9375e-184">ディメンションを処理する XMLA スクリプトを含む **XMLA クエリ** ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="9375e-184">Open the **XMLA Query** window that contains the XMLA script that processes the dimension.</span></span> <span data-ttu-id="9375e-185">スクリプト内で `</Process>` タグの左まで右クリックし、 **[貼り付け]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-185">Right-click within the script to the left of the `</Process>` tag and select **Paste**.</span></span>  
  
     <span data-ttu-id="9375e-186">次の例は、変更後の XMLA スクリプトを示しています。</span><span class="sxs-lookup"><span data-stu-id="9375e-186">The following example shows the revised XMLA script.</span></span>  
  
    ```  
    <Batch xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
     <Parallel>  
      <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
        <Object>  
          <DatabaseID>Adventure Works DW Multidimensional</DatabaseID>  
          <DimensionID>Dim Customer</DimensionID>  
        </Object>  
        <Type>ProcessFull</Type>  
        <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
      </Process>  
      <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
        <Object>  
          <DatabaseID>Adventure Works DW Multidimensional</DatabaseID>  
          <CubeID>Adventure Works</CubeID>  
          <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
          <PartitionID>Internet_Sales_2004</PartitionID>  
        </Object>  
        <Type>ProcessFull</Type>  
        <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
      </Process>  
     </Parallel>  
    </Batch>  
    ```  
  
11. <span data-ttu-id="9375e-187">変更後の XMLA スクリプトを強調表示し、強調表示されたスクリプトを右クリックして **[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-187">Highlight the revised XMLA script, right-click the highlighted script, and select **Copy.**</span></span>  
  
12. <span data-ttu-id="9375e-188">この手順により、XMLA スクリプトが Windows クリップボードにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="9375e-188">This step copies the XMLA script to the Windows Clipboard.</span></span> <span data-ttu-id="9375e-189">XMLA スクリプトをクリップボードに残しておくか、ファイルに保存するか、メモ帳または別のテキスト エディターに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="9375e-189">You can leave the XMLA script in the Clipboard, save it to a file, or paste it into Notepad or another text editor.</span></span>  
  
###  <a name="create-and-schedule-the-batch-processing-job"></a><a name="bkmk_Scheduling"></a><span data-ttu-id="9375e-190">バッチ処理ジョブの作成とスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="9375e-190">Create and schedule the batch processing job</span></span>  
  
1.  <span data-ttu-id="9375e-191">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続し、オブジェクト エクスプローラーを開きます。</span><span class="sxs-lookup"><span data-stu-id="9375e-191">Connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and then open Object Explorer.</span></span>  
  
2.  <span data-ttu-id="9375e-192">**[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="9375e-192">Expand **SQL Server Agent**.</span></span> <span data-ttu-id="9375e-193">サービスが実行されていない場合は開始します。</span><span class="sxs-lookup"><span data-stu-id="9375e-193">Start the service if is not running.</span></span>  
  
3.  <span data-ttu-id="9375e-194">**[ジョブ]** を右クリックし、 **[新しいジョブ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-194">Right-click **Jobs** and select **New Job**.</span></span>  
  
4.  <span data-ttu-id="9375e-195">**[新しいジョブ]** ダイアログ ボックスで、 **[名前]** ボックスにジョブ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="9375e-195">In the **New Job** dialog box, enter a job name in **Name**.</span></span>  
  
5.  <span data-ttu-id="9375e-196">**[ステップ]** で、 **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-196">In **Steps**, click **New**.</span></span>  
  
6.  <span data-ttu-id="9375e-197">**[新しいジョブ ステップ]** ダイアログ ボックスで、 **[ステップ名]** にステップ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="9375e-197">In the **New Job Step** dialog box, enter a step name in **Step Name**.</span></span>  
  
7.  <span data-ttu-id="9375e-198">**[種類]** で、 **[SQL Server Analysis Services コマンド]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9375e-198">In **Type**, select **SQL Server Analysis Services Command**.</span></span>  
  
8.  <span data-ttu-id="9375e-199">**[実行するアカウント名]** で、 **[SQL Server エージェント サービスのアカウント]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9375e-199">In **Run as**, select the **SQL Server Agent Service Account**.</span></span> <span data-ttu-id="9375e-200">「前提条件」で説明したように、このアカウントには Analysis Services に対する管理権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="9375e-200">Recall from the Prerequisites section that this account must have administrative permissions on Analysis Services.</span></span>  
  
9. <span data-ttu-id="9375e-201">**[サーバー]** で、Analysis Services インスタンスのサーバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="9375e-201">In **Server**, specify the server name of the Analysis Services instance.</span></span>  
  
10. <span data-ttu-id="9375e-202">**[コマンド]** で、右クリックして **[貼り付け]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9375e-202">In **Command**, right-click and select **Paste**.</span></span>  
  
11. <span data-ttu-id="9375e-203">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-203">Click **OK**.</span></span>  
  
12. <span data-ttu-id="9375e-204">**[スケジュール]** ページで **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-204">In the **Schedules** page, click **New**.</span></span>  
  
13. <span data-ttu-id="9375e-205">**[新しいジョブ スケジュール]** ダイアログ ボックスで、 **[名前]** ボックスにスケジュール名を入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-205">In the **New Job Schedule** dialog box, enter a schedule name in **Name**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="9375e-206">この手順により、日曜日午前 12 時 00 分のスケジュールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9375e-206">This step creates a schedule for Sunday at 12:00 AM.</span></span> <span data-ttu-id="9375e-207">次の手順では、ジョブを手動で実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9375e-207">The next step shows you how to manually execute the job.</span></span> <span data-ttu-id="9375e-208">ジョブを監視しているときに、ジョブを実行するスケジュールを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="9375e-208">You can also select a schedule which will execute the job when you are monitoring it.</span></span>  
  
14. <span data-ttu-id="9375e-209">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="9375e-209">Click **OK** to close the dialog box.</span></span>  
  
15. <span data-ttu-id="9375e-210">**オブジェクト エクスプローラー**で、 **[ジョブ]** を展開し、作成したジョブを右クリックして、 **[ステップでジョブを開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-210">In **Object Explorer**, expand **Jobs**, right-click the job you created, and select **Start Job at Step**.</span></span>  
  
     <span data-ttu-id="9375e-211">このジョブにはステップが 1 つしかないため、すぐにジョブが実行されます。</span><span class="sxs-lookup"><span data-stu-id="9375e-211">Because the job has only one step, the job executes immediately.</span></span> <span data-ttu-id="9375e-212">ジョブに複数のステップが含まれている場合、ジョブを開始するステップを選択できます。</span><span class="sxs-lookup"><span data-stu-id="9375e-212">If the job contains more than one step, you can select the step at which the job should start.</span></span>  
  
16. <span data-ttu-id="9375e-213">ジョブが完了したら、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9375e-213">When the job finishes, click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9375e-214">参照</span><span class="sxs-lookup"><span data-stu-id="9375e-214">See Also</span></span>  
 <span data-ttu-id="9375e-215">[処理オプションと設定 &#40;Analysis Services&#41;](../multidimensional-models/processing-options-and-settings-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="9375e-215">[Processing Options and Settings &#40;Analysis Services&#41;](../multidimensional-models/processing-options-and-settings-analysis-services.md) </span></span>  
 [<span data-ttu-id="9375e-216">Analysis Services の管理タスクのスクリプト作成</span><span class="sxs-lookup"><span data-stu-id="9375e-216">Script Administrative Tasks in Analysis Services</span></span>](../script-administrative-tasks-in-analysis-services.md)  
  
  
