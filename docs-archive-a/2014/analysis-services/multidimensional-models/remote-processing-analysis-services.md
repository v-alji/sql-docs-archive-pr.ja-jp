---
title: リモート処理 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d58bcb3c-0b3f-4ab0-81eb-4fdcc86153af
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4e0d6ade25f5a321e49c748692a961abc369efad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642369"
---
# <a name="remote-processing-analysis-services"></a><span data-ttu-id="06a60-102">リモート処理 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="06a60-102">Remote Processing (Analysis Services)</span></span>
  <span data-ttu-id="06a60-103">あるコンピューターから発行された処理要求を同じネットワーク上の別のコンピューターで実行する場合、スケジュールされた処理や自動処理をリモートの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスで実行できます。</span><span class="sxs-lookup"><span data-stu-id="06a60-103">You can run scheduled or unattended processing on a remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, where the processing request originates from one computer but executes on another computer on the same network.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="06a60-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="06a60-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="06a60-105">各コンピューターでそれぞれ異なるバージョンの SQL Server を実行している場合、クライアント ライブラリはモデルを処理する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのバージョンと一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="06a60-105">If you are running different versions of SQL Server on each computer, the client libraries must match the version of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance that is processing the model.</span></span> <span data-ttu-id="06a60-106">たとえば、 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] インスタンスで処理を行う場合、要求の発行元のコンピューターには [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]に対応するクライアント ライブラリが必要です。</span><span class="sxs-lookup"><span data-stu-id="06a60-106">For example, if processing is on a [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] instance, then the computer from which the request originates must have the client library corresponding to [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)].</span></span> <span data-ttu-id="06a60-107">「 [Analysis Services 接続に使用するデータ プロバイダー](../instances/data-providers-used-for-analysis-services-connections.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="06a60-107">See [Data providers used for Analysis Services connections](../instances/data-providers-used-for-analysis-services-connections.md).</span></span>  
  
-   <span data-ttu-id="06a60-108">リモート サーバーでは、 **[このコンピューターへのリモート接続を許可する]** が有効になっている必要があり、処理要求を発行するアカウントは許可されたユーザーとして一覧に表示されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="06a60-108">On the remote server, **Allow remote connections to this computer** must be enabled, and the account issuing the processing request must be listed as an allowed user.</span></span>  
  
-   <span data-ttu-id="06a60-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]への着信接続を許可するように Windows ファイアウォール ルールを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="06a60-109">Windows firewall rules must be configured to allow inbound connections to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="06a60-110">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を使用してリモートの [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]インスタンスに接続できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="06a60-110">Verify you can connect to the remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="06a60-111">「 [Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="06a60-111">See [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
-   <span data-ttu-id="06a60-112">リモート処理を試みる前に、既存のローカル処理エラーを解決します。</span><span class="sxs-lookup"><span data-stu-id="06a60-112">Resolve any existing local processing errors before attempting remote processing.</span></span> <span data-ttu-id="06a60-113">処理要求がローカルの場合、外部リレーショナル データ ソースからデータを正常に取得できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="06a60-113">Verify that when the processing request is local, data can be successfully retrieved from the external relational data source.</span></span> <span data-ttu-id="06a60-114">データの取得に使用する資格情報を指定する手順については、「[権限借用オプションの設定 &#40;SSAS - 多次元&#41;](set-impersonation-options-ssas-multidimensional.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="06a60-114">See [Set Impersonation Options &#40;SSAS - Multidimensional&#41;](set-impersonation-options-ssas-multidimensional.md) for instructions on specifying credentials used to retrieve data.</span></span>  
  
## <a name="on-demand-remote-processing"></a><span data-ttu-id="06a60-115">オンデマンドのリモート処理</span><span class="sxs-lookup"><span data-stu-id="06a60-115">On-demand remote processing</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="06a60-116">は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の管理者権限を持つユーザー アカウントまたはアプリケーション アカウントからの処理要求を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="06a60-116">accepts processing requests from user or application accounts that have [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrator permissions.</span></span> <span data-ttu-id="06a60-117">管理者は、リモート インスタンスに接続し、リモート接続でデータベースを手動で処理できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="06a60-117">If you are an administrator, verify that you can connect to the remote instance and process the database manually over the remote connection.</span></span>  
  
1.  <span data-ttu-id="06a60-118">処理のスケジュールを設定する際に使用するコンピューターで、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を起動し、リモートの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="06a60-118">On the computer that will be used to schedule processing, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
2.  <span data-ttu-id="06a60-119">データベースを右クリックして **[処理]** を選択し、 **[スクリプト]** をポイントして **[スクリプト操作を新規クエリ ウィンドウに保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06a60-119">Right-click the database, select **Process**, point to **Script** and choose **Script Action to New Query Window**.</span></span> <span data-ttu-id="06a60-120">処理の呼び出しに使用するコマンドがクエリ ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="06a60-120">Commands used to invoke processing will appear in the query window.</span></span>  
  
3.  <span data-ttu-id="06a60-121">**[OK]** をクリックして、処理を開始します。</span><span class="sxs-lookup"><span data-stu-id="06a60-121">Click **OK** to begin processing.</span></span>  
  
     <span data-ttu-id="06a60-122">このタスクが正常に完了すると、スケジュールされたジョブに組み込むことができる XMLA クエリが提供されます。</span><span class="sxs-lookup"><span data-stu-id="06a60-122">Successful completion of this task provides an XMLA query that you can embed in a scheduled job.</span></span> <span data-ttu-id="06a60-123">また、接続の問題が発生していないことも確認されます。</span><span class="sxs-lookup"><span data-stu-id="06a60-123">It also confirms there are no connection problems.</span></span>  
  
## <a name="schedule-remote-processing-using-sql-server-agent-service"></a><span data-ttu-id="06a60-124">SQL Server エージェント サービスを使用したリモート処理のスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="06a60-124">Schedule remote processing using SQL Server Agent Service</span></span>  
 <span data-ttu-id="06a60-125">既定では、SQL Server エージェント サービスは、コンピューター アカウントを使用して作成されたネットワーク接続によって、仮想アカウントで実行されます。</span><span class="sxs-lookup"><span data-stu-id="06a60-125">By default, SQL Server Agent service runs under a virtual account, with network connections made using the machine account.</span></span> <span data-ttu-id="06a60-126">リモートの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに対する管理権限をコンピューター アカウントに付与しないようにするには、最小特権のドメイン ユーザー アカウントとして実行するように SQL Server エージェント サービス アカウントを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="06a60-126">To avoid having to give a machine account administrative rights on the remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, you should change the SQL Server Agent service account to run as a least-privilege domain user account.</span></span>  
  
 <span data-ttu-id="06a60-127">必要なすべての権限を必ず付与してください。たとえば、サービスを提供するデータベース エンジン インスタンスに対する **sysadmin** 権限をアカウントに付与します。</span><span class="sxs-lookup"><span data-stu-id="06a60-127">Be sure to grant all of the necessary permissions, including giving the account **sysadmin** rights on the Database Engine instance providing the service.</span></span>  
  
 <span data-ttu-id="06a60-128">次のリンクを使用して権限を設定します。</span><span class="sxs-lookup"><span data-stu-id="06a60-128">Use the following links to set permissions:</span></span>  
  
-   [<span data-ttu-id="06a60-129">SQL Server エージェントの構成</span><span class="sxs-lookup"><span data-stu-id="06a60-129">Configure SQL Server Agent</span></span>](../../ssms/agent/configure-sql-server-agent.md)  
  
-   <span data-ttu-id="06a60-130">[sysadmin](../../ssms/agent/sql-server-agent.md#Components) 権限を付与することができない場合、 **SQL Server エージェントのコンポーネント** は代替の固定サーバー ロールを提示します。</span><span class="sxs-lookup"><span data-stu-id="06a60-130">[SQL Server Agent Components](../../ssms/agent/sql-server-agent.md#Components) suggests alternative fixed server roles if granting **sysadmin** permissions is not possible.</span></span>  
  
 <span data-ttu-id="06a60-131">アカウントの権限を構成したら、以下の手順を続行します。</span><span class="sxs-lookup"><span data-stu-id="06a60-131">After account permissions are configured, continue with these steps.</span></span>  
  
#### <a name="grant-the-sql-server-agent-account-administrator-permission-on-ssas"></a><span data-ttu-id="06a60-132">SSAS に対する管理者権限を SQL Server エージェント アカウントに付与する</span><span class="sxs-lookup"><span data-stu-id="06a60-132">Grant the SQL Server Agent account administrator permission on SSAS</span></span>  
  
1.  <span data-ttu-id="06a60-133">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]を使用して、リモートの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="06a60-133">Using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], connect to the remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
2.  <span data-ttu-id="06a60-134">サーバー名を右クリックして **[プロパティ]** をクリックし、 **[セキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="06a60-134">Right-click the server name, click P**roperties**, and then click **Security**.</span></span>  
  
3.  <span data-ttu-id="06a60-135">**[追加]** をクリックして、SQL Server エージェント アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="06a60-135">Click **Add** to add the SQL Server Agent account.</span></span>  
  
#### <a name="create-the-job"></a><span data-ttu-id="06a60-136">ジョブの作成</span><span class="sxs-lookup"><span data-stu-id="06a60-136">Create the Job</span></span>  
  
1.  <span data-ttu-id="06a60-137">Management Studio で、ローカルのデータベース エンジン インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="06a60-137">In Management Studio, connect to the local Database Engine instance.</span></span> <span data-ttu-id="06a60-138">SQL Server エージェントは、オブジェクト エクスプローラー内の最後のアイテムです。</span><span class="sxs-lookup"><span data-stu-id="06a60-138">SQL Server Agent is the last item in Object Explorer.</span></span> <span data-ttu-id="06a60-139">起動の必要なサービスがあれば起動します。</span><span class="sxs-lookup"><span data-stu-id="06a60-139">If necessary, start the service.</span></span>  
  
2.  <span data-ttu-id="06a60-140">**[ジョブ]** を右クリックして **[新しいジョブ]** をクリックし、名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="06a60-140">Right-click **Job**s, click **New Job** and then enter a name.</span></span>  
  
3.  <span data-ttu-id="06a60-141">[ステップ] で **[新規作成]** をクリックし、名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="06a60-141">In Steps, click **New** and then enter a name.</span></span>  
  
4.  <span data-ttu-id="06a60-142">[種類] で **[SQL Server Analysis Services コマンド]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06a60-142">In Type, choose **SQL Server Analysis Services Command**.</span></span>  
  
5.  <span data-ttu-id="06a60-143">[サーバー] で、リモートの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="06a60-143">In Server, enter the name of the remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
6.  <span data-ttu-id="06a60-144">[コマンド] でデータベースを処理する XMLA コマンドを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="06a60-144">In Command, paste the XMLA command for processing the database.</span></span> <span data-ttu-id="06a60-145">これは、オンデマンドのリモート処理の検証手順で生成した XMLA スクリプトです。</span><span class="sxs-lookup"><span data-stu-id="06a60-145">This is the XMLA script that you generated in the verification step for on-demand remote processing.</span></span> <span data-ttu-id="06a60-146">**[OK]** をクリックしてジョブを保存します。</span><span class="sxs-lookup"><span data-stu-id="06a60-146">Click **OK** to save the job.</span></span>  
  
#### <a name="start-sql-server-profiler"></a><span data-ttu-id="06a60-147">SQL Server Profiler の起動</span><span class="sxs-lookup"><span data-stu-id="06a60-147">Start SQL Server Profiler</span></span>  
  
1.  <span data-ttu-id="06a60-148">リモート コンピューターで SQL Server Profiler を起動します。</span><span class="sxs-lookup"><span data-stu-id="06a60-148">On the remote computer, start SQL Server Profiler.</span></span> <span data-ttu-id="06a60-149">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに接続し、 **[実行]** をクリックして、既定のイベントを使用してトレースを開始します。</span><span class="sxs-lookup"><span data-stu-id="06a60-149">Connect to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, and click **Run** to start the trace using the default events.</span></span>  
  
     <span data-ttu-id="06a60-150">SQL Server Profiler を使用して、発生した処理イベントを監視します。</span><span class="sxs-lookup"><span data-stu-id="06a60-150">You will use SQL Server Profiler to monitor the processing events as they occur.</span></span>  
  
2.  <span data-ttu-id="06a60-151">必要に応じて、データベース内のファイルまたはテーブルにトレースを送信するようにトレースのプロパティを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="06a60-151">Optionally, you can set trace properties to send the trace to a file or table in a database.</span></span>  
  
#### <a name="run-the-job"></a><span data-ttu-id="06a60-152">ジョブの実行</span><span class="sxs-lookup"><span data-stu-id="06a60-152">Run the job</span></span>  
  
1.  <span data-ttu-id="06a60-153">ジョブの実行に使用するコンピューターで、ジョブが基本操作を実行できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="06a60-153">On the computer used to run the job, verify that the job can perform the basic operation.</span></span> <span data-ttu-id="06a60-154">オブジェクト エクスプローラーで、SQL Server エージェントの下の **[ジョブ]** を展開し、作成したジョブを右クリックして **[ステップでジョブを開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="06a60-154">In Object Explorer, under SQL Server Agent, expand **Jobs**, right-click the job you just created, and click **Start Job at Step**.</span></span> <span data-ttu-id="06a60-155">ジョブがすぐに開始されます。</span><span class="sxs-lookup"><span data-stu-id="06a60-155">The job starts immediately.</span></span> <span data-ttu-id="06a60-156">SQL Server Profiler で進行状況を監視できます。</span><span class="sxs-lookup"><span data-stu-id="06a60-156">You can monitor progress in SQL Server Profiler.</span></span>  
  
2.  <span data-ttu-id="06a60-157">最後の手順として、ジョブを管理するために必要な警告や通知を追加して、定義したスケジュールで実行するようにジョブを変更します。</span><span class="sxs-lookup"><span data-stu-id="06a60-157">As a final step, modify the job to run on a schedule that you define, adding any alerts or notifications necessary to administer the job.</span></span> <span data-ttu-id="06a60-158">また、処理スクリプトを調整したり、ジョブ内に複数のステップを作成してオブジェクトを個別に処理したりできます。</span><span class="sxs-lookup"><span data-stu-id="06a60-158">You might also want to refine the processing script, or create multiple steps in the job to process objects independently.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06a60-159">参照</span><span class="sxs-lookup"><span data-stu-id="06a60-159">See Also</span></span>  
 <span data-ttu-id="06a60-160">[SQL Server エージェントコンポーネント](../../ssms/agent/sql-server-agent.md#Components) </span><span class="sxs-lookup"><span data-stu-id="06a60-160">[SQL Server Agent Components](../../ssms/agent/sql-server-agent.md#Components) </span></span>  
 <span data-ttu-id="06a60-161">[SQL Server エージェントで SSAS 管理タスクのスケジュールを設定する](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md) </span><span class="sxs-lookup"><span data-stu-id="06a60-161">[Schedule SSAS Administrative Tasks with SQL Server Agent](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md) </span></span>  
 <span data-ttu-id="06a60-162">[バッチ処理 &#40;Analysis Services&#41;](batch-processing-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="06a60-162">[Batch Processing &#40;Analysis Services&#41;](batch-processing-analysis-services.md) </span></span>  
 <span data-ttu-id="06a60-163">[多次元モデルオブジェクトの処理](processing-a-multidimensional-model-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="06a60-163">[Multidimensional Model Object Processing](processing-a-multidimensional-model-analysis-services.md) </span></span>  
 [<span data-ttu-id="06a60-164">オブジェクトの処理 &#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="06a60-164">Processing Objects &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)  
  
  
