---
title: データマイニングサーバーに接続する |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- connections
- getting started
ms.assetid: 85962ad6-d840-4bc6-905e-c667c3276944
author: minewiskan
ms.author: owend
ms.openlocfilehash: 528dee62e9074b0d9df6668182c04282500639e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633490"
---
# <a name="connect-to-a-data-mining-server"></a><span data-ttu-id="9193e-102">データ マイニング サーバーへの接続</span><span class="sxs-lookup"><span data-stu-id="9193e-102">Connect to a Data Mining Server</span></span>
  <span data-ttu-id="9193e-103">![[接続] ボタン](media/misc-connection.gif "[接続] ボタン")</span><span class="sxs-lookup"><span data-stu-id="9193e-103">![Connections button](media/misc-connection.gif "Connections button")</span></span>  
  
 <span data-ttu-id="9193e-104">[**接続**] ボタンをクリックして既存の接続を選択するか、のインスタンスへの新しい接続を作成し [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="9193e-104">Click the **Connection** button to select an existing connection, or to create a new connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9193e-105">**サーバーへの接続が必要な理由**</span><span class="sxs-lookup"><span data-stu-id="9193e-105">**Why do I need to connect to a server?**</span></span>  
  
 <span data-ttu-id="9193e-106">接続を作成すると、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーが提供するデータ マイニング アルゴリズムと、サーバーによる最適化された処理を利用できます。</span><span class="sxs-lookup"><span data-stu-id="9193e-106">When you create a connection, it enables you to use the data mining algorithms that are provided by the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server, and to take advantage of the optimized processing of the server.</span></span>  
  
 <span data-ttu-id="9193e-107">データまたは結果を [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースまたは SQL Server データベースに保存する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9193e-107">You do not have to keep your data or your results in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, or in a SQL Server database.</span></span> <span data-ttu-id="9193e-108">Excel データ マイニング アドインでは、Excel だけに格納されているデータまたは Excel データ ソースとして接続するデータを操作できます。</span><span class="sxs-lookup"><span data-stu-id="9193e-108">The Excel data mining add-ins can work with data stored only in Excel, or data that you connect to as an Excel data source.</span></span>  
  
## <a name="how-to-create-a-new-connection"></a><span data-ttu-id="9193e-109">新しい接続を作成する方法</span><span class="sxs-lookup"><span data-stu-id="9193e-109">How to Create a New Connection</span></span>  
  
1.  <span data-ttu-id="9193e-110">[**接続**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9193e-110">Click the **Connection** button.</span></span>  
  
2.  <span data-ttu-id="9193e-111">[ **Analysis Services 接続**] ダイアログボックスで、[**新規**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9193e-111">In the **Analysis Services Connections** dialog box, click **New**.</span></span>  
  
3.  <span data-ttu-id="9193e-112">[ **Analysis Services への接続**] ダイアログボックスで、サーバー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="9193e-112">In the **Connect to Analysis Services** dialog box, type a server name.</span></span>  
  
4.  <span data-ttu-id="9193e-113">認証方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="9193e-113">Specify the authentication method.</span></span>  
  
5.  <span data-ttu-id="9193e-114">データ マイニング モデルを格納するカタログまたは [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="9193e-114">Specify the catalog, or [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, where you will store your data mining models.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9193e-115">データベースをまだ作成していない場合は、(既定値) を使用して接続を作成し、テストできます。ただし、マイニング モデルを既定の接続に追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="9193e-115">If you have not created any databases yet, you can use (default) to create and then test the connection; however, you cannot add mining models to the default connection.</span></span> <span data-ttu-id="9193e-116">マイニング モデルを作成する前に、既存のデータベースへの接続を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9193e-116">Before you create any mining models, you should create a connection to an existing database.</span></span>  
  
6.  <span data-ttu-id="9193e-117">Web サービス経由でサーバーに接続する場合は、Web サービスから要求されるユーザー名およびパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="9193e-117">If you are connecting to the server via a Web service, type the user name and password required by the Web service.</span></span>  
  
7.  <span data-ttu-id="9193e-118">新しい接続の表示名を入力します。</span><span class="sxs-lookup"><span data-stu-id="9193e-118">Type a friendly name for the new connection.</span></span>  
  
8.  <span data-ttu-id="9193e-119">[**接続テスト**] をクリックして、サーバーが使用可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9193e-119">Click **Test Connection** to verify that the server is available.</span></span>  
  
## <a name="troubleshooting-connections"></a><span data-ttu-id="9193e-120">接続のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="9193e-120">Troubleshooting Connections</span></span>  
 <span data-ttu-id="9193e-121">このセクションでは、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] への接続に関する一般的な質問の回答を提供します。</span><span class="sxs-lookup"><span data-stu-id="9193e-121">This section provides answers to some common questions about connections to [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9193e-122">**"接続が見つかりませんでした" というメッセージが表示できます。**</span><span class="sxs-lookup"><span data-stu-id="9193e-122">**I get a message saying "No connection found."**</span></span>  
  
 <span data-ttu-id="9193e-123">ボタンの下部のテキストが [**接続なし**] と表示されている場合は、データベースへの接続が作成されていないか、接続に失敗したことを意味 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="9193e-123">If the text in the lower part of the button says **No Connection**, it means that you have not created a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, or that the connection failed.</span></span> <span data-ttu-id="9193e-124">Access など他のソースからの Excel 内のデータの作業は継続できますが、データ マイニング モデルの作成や予測クエリの実行のためにはアクティブな接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="9193e-124">You can continue to work with data in Excel from Access or other sources, but to create a data mining model or run a prediction query you must have an active connection.</span></span>  
  
 <span data-ttu-id="9193e-125">**サーバーを使用するためのアクセス許可がないとします。**</span><span class="sxs-lookup"><span data-stu-id="9193e-125">**Suppose I don't have permission to use the server?**</span></span>  
  
 <span data-ttu-id="9193e-126">サーバーにマイニングモデルを格納するための十分なアクセス許可がない場合、またはデータマイニングを使用して作業を保存しない場合は、一時的なデータ構造と一時的なモデルを作成するテーブル分析ツールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9193e-126">If you do not have sufficient permissions to store your mining models on the server, or if you want to experiment with data mining and not save your work, you can use the Table Analysis Tools, which create temporary data structures and temporary models.</span></span> <span data-ttu-id="9193e-127">その場合でも、サーバーに一時的なモデルを格納できる権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="9193e-127">You still need to be able to store temporary models on the server.</span></span> <span data-ttu-id="9193e-128">サーバーで*セッションマイニングモデル*の使用を有効にするには、管理者に依頼してください。</span><span class="sxs-lookup"><span data-stu-id="9193e-128">Ask your administrator to enable use of *session mining models* on the server.</span></span>  
  
 <span data-ttu-id="9193e-129">モデルが保存されていることを確認する場合は、一時的なモデルを使用するオプションを無効にするか、データ マイニング クライアント内のウィザードを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="9193e-129">If you want to ensure that your models are saved, you can disable the option to use temporary models, or you can use the wizards in the Data Mining Client.</span></span> <span data-ttu-id="9193e-130">これらのウィザードには、サーバーのすべてのモデルが格納されています。</span><span class="sxs-lookup"><span data-stu-id="9193e-130">These wizards store all models on the server.</span></span> <span data-ttu-id="9193e-131">モデルが格納されているデータベースへの管理アクセス権が必要です。そのため、管理者は、特にアドインを使用してマイニングモデルを作成するためのデータベースを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9193e-131">You will need administrative access to the database where the models are stored, so we recommend that you get the administrator to create a database especially for creating mining models with the add-ins.</span></span>  
  
 <span data-ttu-id="9193e-132">**接続が失われた場合は、すべての作業内容も失われていますか?**</span><span class="sxs-lookup"><span data-stu-id="9193e-132">**I lost my connection; did I lose all my work?**</span></span>  
  
 <span data-ttu-id="9193e-133">サーバーへの接続を終了しても結果とデータが失われることはありません。これは、これらが Excel に保存されているためです。</span><span class="sxs-lookup"><span data-stu-id="9193e-133">If you terminate the connection to the server, your results and data will not be lost, because they are stored in Excel.</span></span> <span data-ttu-id="9193e-134">ただし一時的なモデルを作成している場合、これらのモデルはすぐにサーバーから削除されます。</span><span class="sxs-lookup"><span data-stu-id="9193e-134">However, if you created some temporary models, those models will be deleted from the server after a short time.</span></span> <span data-ttu-id="9193e-135">そのため、一時的に接続が切断されても、モデルがまだ削除されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="9193e-135">So if you lose the connection temporarily, sometime the models won't be deleted yet.</span></span>  
  
 <span data-ttu-id="9193e-136">すべてのレポートおよびテーブルが Excel 内に保存されるため、生成した結果やデータが失われることはありません。</span><span class="sxs-lookup"><span data-stu-id="9193e-136">Any data or results that were generated will not be lost, because all reports and tables are stored in Excel.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9193e-137">アドインが [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーとやり取りしている間は、サーバーまたはネットワークから接続解除しないでください。</span><span class="sxs-lookup"><span data-stu-id="9193e-137">Do not disconnect from the server or from the network while the add-in is communicating with the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server.</span></span> <span data-ttu-id="9193e-138">たとえば、モデルの作成中やデータの処理中には接続解除しないでください。</span><span class="sxs-lookup"><span data-stu-id="9193e-138">For example, never disconnect when a model is being created, or when the data is being processed.</span></span> <span data-ttu-id="9193e-139">状況によっては、データが破損する場合があります。</span><span class="sxs-lookup"><span data-stu-id="9193e-139">In some situations your data could be corrupted.</span></span>  
  
 <span data-ttu-id="9193e-140">**Visio のツールを使用してモデルに接続できません**</span><span class="sxs-lookup"><span data-stu-id="9193e-140">**I cannot connect to the model using the Visio tools**</span></span>  
  
 <span data-ttu-id="9193e-141">Visio 用のデータ マイニング テンプレートでは、一時的なマイニング構造およびモデルを使用できません。</span><span class="sxs-lookup"><span data-stu-id="9193e-141">The Data Mining Templates for Visio cannot use temporary mining structures and models.</span></span> <span data-ttu-id="9193e-142">マイニング モデルのダイアグラムを作成するには、そのモデルがサーバー上に格納されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9193e-142">To create a diagram of a mining model, the model must be stored on a server.</span></span>  
  
 <span data-ttu-id="9193e-143">**接続の使用状況を監視する方法は?**</span><span class="sxs-lookup"><span data-stu-id="9193e-143">**How can I monitor usage of the connection?**</span></span>  
  
 <span data-ttu-id="9193e-144">[Excel&#41;用のトレース &#40;データマイニングクライアント](trace-data-mining-client-for-excel.md)は、アドインと指定されたサーバー間のすべてのアクティビティのログを作成します。</span><span class="sxs-lookup"><span data-stu-id="9193e-144">The [Trace &#40;Data Mining Client for Excel&#41;](trace-data-mining-client-for-excel.md) tool creates a log of all activity between the add-ins and the specified server.</span></span>  
  
 <span data-ttu-id="9193e-145">セッションモデルの監視を有効にするには、[**トレーサー** ] ダイアログボックスの [**セッションモデルを使用**する] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="9193e-145">To enable monitoring of session models, select the **Use session models** option in the **Tracer** dialog box.</span></span>  
  
 <span data-ttu-id="9193e-146">トレースでは、モデルと構造を作成する際に生成された DMX および XMLA コマンドを表示できます。</span><span class="sxs-lookup"><span data-stu-id="9193e-146">The trace lets you view the DMX and XMLA commands generated while models and structures are being created.</span></span> <span data-ttu-id="9193e-147">また、結果とその他のレポートを Excel で生成するためにクライアントが送信したクエリも表示できます。</span><span class="sxs-lookup"><span data-stu-id="9193e-147">You can also view the queries that are sent by the client to generate results and reports in Excel.</span></span>  
  
 <span data-ttu-id="9193e-148">**一時的なモデルとは一時的なモデルを保存するにはどうすればよいですか。**</span><span class="sxs-lookup"><span data-stu-id="9193e-148">**What is a temporary model? How can I save a temporary model?**</span></span>  
  
 <span data-ttu-id="9193e-149">Excel 用テーブル分析ツールは、既定で一時的なデータ構造とマイニング モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="9193e-149">The Table Analysis Tools for Excel by default creates temporary data structures and mining models.</span></span> <span data-ttu-id="9193e-150">ブックを開いた状態で [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] への接続を保持している限り、一時的なモデルの参照やクエリを継続して実行できます。</span><span class="sxs-lookup"><span data-stu-id="9193e-150">You can continue to browse and query temporary models as long as you keep the workbook open and do not disconnect from [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9193e-151">Excel ブックを閉じるか [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] への接続を変更または終了すると、構造とモデルが直ちに削除されます。</span><span class="sxs-lookup"><span data-stu-id="9193e-151">The structures and models that you have created will be deleted as soon as you close the Excel workbook, or if you change or end your connection to [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9193e-152">Excel 用データ マイニング クライアントのウィザードを完了する際は、既定でモデルがサーバーに保存されます。ただし、各ウィザードの最終ページには、一時的なモデルを使用するためのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="9193e-152">When you complete a wizard in the Data Mining Client for Excel, models are saved to the server by default, but on the final page of each wizard there is the option to use a temporary model.</span></span> <span data-ttu-id="9193e-153">このオプションを選択した場合は、作成したデータ マイニング構造とモデルが一時ファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="9193e-153">If you select this option, the data mining structure and model that you created are stored in a temporary file.</span></span> <span data-ttu-id="9193e-154">Excel を開いている限り、構造およびモデルを参照、管理、および変更できます。</span><span class="sxs-lookup"><span data-stu-id="9193e-154">You can browse, manage, and modify the structure and model as long as Excel remains open.</span></span> <span data-ttu-id="9193e-155">ただし、Excel を終了すると、構造とすべての関連モデルが削除されます。</span><span class="sxs-lookup"><span data-stu-id="9193e-155">However, once you close Excel, the structure and any related models are deleted.</span></span>  
  
 <span data-ttu-id="9193e-156">また、**データマイニング詳細クエリエディター**を使用し、DMX テンプレートの1つを選択して、一時的な構造またはモデルを明示的に作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="9193e-156">You can also explicitly create a temporary structure or model by using the **Data Mining Advanced Query Editor** and selecting one of the DMX templates.</span></span> <span data-ttu-id="9193e-157">`USE SESSION MODELS` 句を追加すると、これらのオブジェクトが一時的なものとして指定されます。</span><span class="sxs-lookup"><span data-stu-id="9193e-157">Add the `USE SESSION MODELS` clause to specify that objects be temporary.</span></span>   
  
### <a name="creating-backups-of-mining-models-and-structures"></a><span data-ttu-id="9193e-158">マイニング モデルおよび構造のバックアップの作成</span><span class="sxs-lookup"><span data-stu-id="9193e-158">Creating Backups of Mining Models and Structures</span></span>  
 <span data-ttu-id="9193e-159">モデルまたは構造のバックアップを作成するには、Excel 用のデータマイニングクライアントで、[[モデルの管理 &#40;SQL Server データマイニングアドイン&#41;](manage-models-sql-server-data-mining-add-ins.md)を使用してエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="9193e-159">To create a backup of a model or structure, you can export it by using [Manage Models &#40;SQL Server Data Mining Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md), in the Data Mining Client for Excel.</span></span>  
  
 <span data-ttu-id="9193e-160">通常、作成された一時的なマイニング モデルには、Table5_593679_TS_62446 などのわかりにくい名前が付いています。</span><span class="sxs-lookup"><span data-stu-id="9193e-160">If you created a temporary mining model, it typically has a name that is difficult to understand, such as Table5_593679_TS_62446.</span></span> <span data-ttu-id="9193e-161">ただし、[ [Excel&#41;用のトレース &#40;データマイニングクライアント](trace-data-mining-client-for-excel.md)] ツールを使用すると、テーブル分析ツールによって作成された一時的な構造およびモデルの名前を検出し、[**モデルの管理**] を使用してそれらをバックアップできます。</span><span class="sxs-lookup"><span data-stu-id="9193e-161">However, you can use the [Trace &#40;Data Mining Client for Excel&#41;](trace-data-mining-client-for-excel.md) tool to discover the names of temporary structures and models that were created by the Table Analysis Tools and then back them up using **Manage Models**.</span></span>  
  
##### <a name="identify-and-export-a-temporary-model"></a><span data-ttu-id="9193e-162">一時的なモデルの特定とエクスポート</span><span class="sxs-lookup"><span data-stu-id="9193e-162">Identify and export a temporary model</span></span>  
  
1.  <span data-ttu-id="9193e-163">Excel 用のデータマイニングクライアントの [**接続**] グループで、[**トレース**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9193e-163">In the **Connections** group of the Data Mining Client for Excel, click **Trace**.</span></span>  
  
2.  <span data-ttu-id="9193e-164">接続のアクティビティ ログを表示して、列および予測可能な出力 (一例です) を確認してモデルを特定します。</span><span class="sxs-lookup"><span data-stu-id="9193e-164">View the connection activity log, and locate the model by reviewing the columns and predictable outputs (for example).</span></span>  
  
     <span data-ttu-id="9193e-165">上級ユーザー: DMX または XMLA について理解している場合は、ステートメントをファイルにコピーして後で使用することができます。</span><span class="sxs-lookup"><span data-stu-id="9193e-165">Advanced users: If you are familiar with DMX or XMLA, you can copy the statements to a file for later use.</span></span>  
  
3.  <span data-ttu-id="9193e-166">一時的なモデルと構造の名前が見つかったら、[モデルの**管理**] を開き、モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="9193e-166">When you have found the name of the temporary model and structure, open **Manage Model** and select the model.</span></span>  
  
4.  <span data-ttu-id="9193e-167">[このマイニング モデルをエクスポートします] をクリックして、指定した場所にスクリプト ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="9193e-167">Click Export this mining model to generate a script file in a location you specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9193e-168">参照</span><span class="sxs-lookup"><span data-stu-id="9193e-168">See Also</span></span>  
 <span data-ttu-id="9193e-169">[Excel 用のデータマイニングクライアント &#40;ソースデータへの接続&#41;](connect-to-source-data-data-mining-client-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="9193e-169">[Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md) </span></span>  
 [<span data-ttu-id="9193e-170">Excel 用データマイニングアドイン &#40;サーバー構成ユーティリティ&#41;</span><span class="sxs-lookup"><span data-stu-id="9193e-170">Server Configuration Utility &#40;Data Mining Add-ins for Excel&#41;</span></span>](server-configuration-utility-data-mining-add-ins-for-excel.md)  
  
  
