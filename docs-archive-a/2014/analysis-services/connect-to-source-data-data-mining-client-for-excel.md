---
title: ソースデータへの接続 (Excel 用のデータマイニングクライアント) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- connections
ms.assetid: 548672ce-e403-4aca-b67a-c2c797f053dd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4b4759d94043fdccacdf5b285de50697a18965e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633455"
---
# <a name="connect-to-source-data-data-mining-client-for-excel"></a><span data-ttu-id="42fc8-102">ソース データへの接続 (Excel 用データ マイニング クライアント)</span><span class="sxs-lookup"><span data-stu-id="42fc8-102">Connect to Source Data (Data Mining Client for Excel)</span></span>
  <span data-ttu-id="42fc8-103">このトピックでは、データ マイニング モデルの保存、および、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] に保存されている外部データへのアクセスに使用する接続の作成方法と使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="42fc8-103">This topic describes how to create and use connections used for storing data mining models, and for accessing external data stored in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="42fc8-104">**データマイニング接続。**</span><span class="sxs-lookup"><span data-stu-id="42fc8-104">**Data mining connections.**</span></span> <span data-ttu-id="42fc8-105">アドインの開始時に作成する最初の接続は、アルゴリズムへのアクセス、データ分析、マイニング構造およびモデルの格納に使用されます。</span><span class="sxs-lookup"><span data-stu-id="42fc8-105">The initial connection that you create when you start the add-ins is used to access algorithms, analyze data, and store mining structure and models.</span></span>  
  
 <span data-ttu-id="42fc8-106">アドインでモデリング ツールと視覚化ツールを使用するには、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスへの接続が必要です。なぜなら、アドインは [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の高度なアルゴリズムとデータ構造に依存しているためです。</span><span class="sxs-lookup"><span data-stu-id="42fc8-106">A connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] is required to use the modeling and visualization tools in the add-ins, because the add-ins depend on algorithms and data structures that are provided by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="42fc8-107">**外部データ ソースへの接続。**</span><span class="sxs-lookup"><span data-stu-id="42fc8-107">**Connections to external data sources.**</span></span> <span data-ttu-id="42fc8-108">モデルの作成時や結果の保存時に外部データへの接続を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="42fc8-108">You can also create connections to external data as you are building models or saving the results.</span></span> <span data-ttu-id="42fc8-109">たとえば、あるサーバー上にデータ マイニング モデルを作成してから、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の別のインスタンス、Excel データ テーブル、または [!INCLUDE[msCoName](../includes/msconame-md.md)] Access のような外部データ ソースに保存されているデータを使用して、作成したデータ マイニング モデルに基づく予測クエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="42fc8-109">For example, you can create a data mining model on one server, and then perform a prediction query against the data mining model by using data stored in another instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], in an Excel data table, or in an external data source such as [!INCLUDE[msCoName](../includes/msconame-md.md)] Access.</span></span> <span data-ttu-id="42fc8-110">新しいデータ ソースにアクセスするたびに、ダイアログ ボックスを使用して接続を作成するように求められます。</span><span class="sxs-lookup"><span data-stu-id="42fc8-110">Each time that you access a new data source, you will be prompted to create a connection by using a dialog box.</span></span>  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq2"></a> <span data-ttu-id="42fc8-111">前提条件</span><span class="sxs-lookup"><span data-stu-id="42fc8-111">Prerequisites</span></span>  
 <span data-ttu-id="42fc8-112">このバージョンのアドインを使用するには、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスが SQL Server 2012 であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="42fc8-112">This version of the add-ins requires that your instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] be SQL Server 2012.</span></span> <span data-ttu-id="42fc8-113">以前のバージョンの [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] に接続する場合、それぞれのバージョンのアドインを使用できます。</span><span class="sxs-lookup"><span data-stu-id="42fc8-113">A separate version of the add-ins is available if you want to connect to an earlier version of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="42fc8-114">SQL Server 2005、SQL Server 2008、SQL Server 2008 R2 をサポートするアドインのバージョンがあります。</span><span class="sxs-lookup"><span data-stu-id="42fc8-114">There are versions of the add-ins that support SQL Server 2005, SQL Server 2008, and SQL Server 2008 R2.</span></span>  
  
 <span data-ttu-id="42fc8-115">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに接続するには、データベース サーバーにアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="42fc8-115">To connect to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, you must have permissions to access the database server.</span></span> <span data-ttu-id="42fc8-116">また、データ マイニング セッションが有効にされていて、サーバーに格納されているデータベース オブジェクトに対する読み取り権限または読み取り/書き込み権限を有している必要があります。</span><span class="sxs-lookup"><span data-stu-id="42fc8-116">Moreover, data mining sessions must be enabled, and you must have read or read/write permissions on database objects stored on the server.</span></span>  
  
##  <a name="creating-data-mining-server-connections"></a><a name="bkmk_connect"></a><span data-ttu-id="42fc8-117">データマイニングサーバー接続の作成</span><span class="sxs-lookup"><span data-stu-id="42fc8-117">Creating Data Mining Server Connections</span></span>  
 <span data-ttu-id="42fc8-118">Excel 用のデータマイニングクライアントおよび Excel 用のテーブル分析ツールの [**接続**] グループには、のインスタンスへの接続を管理するためのツールが用意されて [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] います。</span><span class="sxs-lookup"><span data-stu-id="42fc8-118">The **Connections** group in the Data Mining Client for Excel and the Table Analysis Tools for Excel provides tools for managing connections to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="42fc8-119">アドインをインストールするときに接続を作成できます。後で接続を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="42fc8-119">You can create the connection when you install the add-in, or you can add a connection later.</span></span>  
  
-   <span data-ttu-id="42fc8-120">モデルの作成中やクエリの実行中でない限り、複数の接続を作成して、接続を随時変更できます。</span><span class="sxs-lookup"><span data-stu-id="42fc8-120">You can create multiple connections, and change connections at any time, unless you are in the process of creating or querying a model.</span></span>  
  
     <span data-ttu-id="42fc8-121">データ マイニング モデルの処理中に接続を変更したり閉じたりしないでください。</span><span class="sxs-lookup"><span data-stu-id="42fc8-121">Do not change or close a connection when a data mining model is being processed.</span></span> <span data-ttu-id="42fc8-122">データ マイニング モデルのデータが失われたり、モデルが使用できなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="42fc8-122">The data mining model might lose data, or the model might become unusable.</span></span>  
  
-   <span data-ttu-id="42fc8-123">有効にできるのは一度に 1 つの接続のみです。</span><span class="sxs-lookup"><span data-stu-id="42fc8-123">Only one connection can be active at a particular time.</span></span>  
  
### <a name="connections-in-the-excel-add-ins"></a><span data-ttu-id="42fc8-124">Excel アドインでの接続</span><span class="sxs-lookup"><span data-stu-id="42fc8-124">Connections in the Excel Add-ins</span></span>  
 <span data-ttu-id="42fc8-125">Excel 用のデータマイニングクライアントおよび Excel 用のテーブル分析ツールの [**接続**] グループでは、のインスタンスへの接続を管理し [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="42fc8-125">The **Connections** group in the Data Mining Client for Excel and the Table Analysis Tools for Excel is where you manage connections to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
##### <a name="create-a-new-server-connection-in-the-excel-add-ins"></a><span data-ttu-id="42fc8-126">Excel アドインで新しいサーバー接続を作成する</span><span class="sxs-lookup"><span data-stu-id="42fc8-126">Create a new server connection in the Excel add-ins</span></span>  
  
1.  <span data-ttu-id="42fc8-127">[**分析**] または [**データマイニング**] リボンの [**接続**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="42fc8-127">Click the **Connection** button on the **Analyze** or **Data Mining** ribbon.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="42fc8-128">ボタンに表示されるテキストは、接続が存在するかどうかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="42fc8-128">The text of the button indicates if a connection exists.</span></span> <span data-ttu-id="42fc8-129">ワークシートで接続が確立されていない場合、ボタンには "." というテキストが表示され \<No connection> ます。ブックで以前に接続が作成されていた場合は、その接続の名前がボタンに表示されます。</span><span class="sxs-lookup"><span data-stu-id="42fc8-129">When no connection has been made in the worksheet, the button contains the text "\<No connection>." If a connection was previously made in the workbook, the name of that connection appears in the button.</span></span>  
  
2.  <span data-ttu-id="42fc8-130">[ **Analysis Services 接続**] ダイアログボックスで、[**新規**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="42fc8-130">In the **Analysis Services Connections** dialog box, click **New**.</span></span>  
  
3.  <span data-ttu-id="42fc8-131">[**新しい Analysis Services 接続**] ダイアログボックスで、サーバーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="42fc8-131">In the **New Analysis Services Connection** dialog box, type the name of the server.</span></span>  
  
4.  <span data-ttu-id="42fc8-132">認証方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="42fc8-132">Specify the authentication method.</span></span>  
  
5.  <span data-ttu-id="42fc8-133">[**カタログ名**] ドロップダウンリストからデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="42fc8-133">Select a database from the **Catalog name** drop-down list.</span></span> <span data-ttu-id="42fc8-134">インスタンスにデータベースが存在しない場合は、[ **(既定)**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="42fc8-134">If no database exists on the instance, select **(default)**.</span></span>  
  
6.  <span data-ttu-id="42fc8-135">接続のフレンドリ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="42fc8-135">Type a friendly name for the connection.</span></span>  
  
7.  <span data-ttu-id="42fc8-136">[**接続テスト**] をクリックして、サーバーとデータベースが使用可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="42fc8-136">Click **Test Connection** to verify that the server and database are available.</span></span>  
  
8.  <span data-ttu-id="42fc8-137">**[OK]** をクリックし、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="42fc8-137">Click **OK**, and then click **Close**.</span></span>  
  
### <a name="connections-using-a-web-service"></a><span data-ttu-id="42fc8-138">Web サービスを使用した接続</span><span class="sxs-lookup"><span data-stu-id="42fc8-138">Connections using a Web Service</span></span>  
 <span data-ttu-id="42fc8-139">仮想化アーキテクチャを使用してキューブとデータの参照を有効にする場合は [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Web サービスを使用してサーバーへの接続を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="42fc8-139">If you are using a thin-client architecture to enable browsing of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cubes and data, you can also configure a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server through Web services.</span></span> <span data-ttu-id="42fc8-140">Web ベース クライアントの定義方法については、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="42fc8-140">For information about how to define a Web-based client, see [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="42fc8-141">Web サービス用に構成されたサーバーにアクセスする場合、最初に接続を作成するときに接続の種類を指定できます。</span><span class="sxs-lookup"><span data-stu-id="42fc8-141">If you have access to a server that has been configured for Web services, you can specify the connection type when you first create the connection.</span></span>  
  
##### <a name="create-an-http-connection-to-analysis-services"></a><span data-ttu-id="42fc8-142">Analysis Services への HTTP 接続を作成する</span><span class="sxs-lookup"><span data-stu-id="42fc8-142">Create an HTTP connection to Analysis Services</span></span>  
  
1.  <span data-ttu-id="42fc8-143">[**新しい Analysis Services 接続**] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="42fc8-143">Open the **New Analysis Services Connection** dialog box.</span></span>  
  
2.  <span data-ttu-id="42fc8-144">サーバー名として、http:// の後に続けて、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーに割り当てられた URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="42fc8-144">For the server name, type http:// followed by the URL assigned to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server.</span></span>  
  
3.  <span data-ttu-id="42fc8-145">Web サービスへのアクセスに必要なユーザー名およびパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="42fc8-145">Type the user name and the password that is required to access the Web service.</span></span>  
  
### <a name="connections-in-the-visio-add-in"></a><span data-ttu-id="42fc8-146">Visio アドインでの接続</span><span class="sxs-lookup"><span data-stu-id="42fc8-146">Connections in the Visio Add-In</span></span>  
 <span data-ttu-id="42fc8-147">Excel とは異なり、Visio にツール リボンはありません。また、接続の作成または監視専用のボタンもありません。</span><span class="sxs-lookup"><span data-stu-id="42fc8-147">Unlike Excel, Visio does not provide a tool ribbon, and there are no buttons specifically for creating or monitoring connections.</span></span> <span data-ttu-id="42fc8-148">代わりに、データ マイニング図形を初めて選択して、Visio ページに配置したときに、データ接続が作成されます。</span><span class="sxs-lookup"><span data-stu-id="42fc8-148">Instead, the data connection is created when you first select a data mining shape and drop it onto a Visio page.</span></span> <span data-ttu-id="42fc8-149">ウィザードの指示に従って、図形のモデルを選択し、その他のオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="42fc8-149">A wizard will prompt you to select the model for the shape and to set other options.</span></span>  
  
 <span data-ttu-id="42fc8-150">Excel で [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データ ソースへの接続を以前に使用したことがある場合は、その接続が使用可能なデータ ソースとして表示されて、選択することができます。</span><span class="sxs-lookup"><span data-stu-id="42fc8-150">If you have previously used a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source in Excel, these connections are listed as possible data sources from which to select.</span></span>  
  
##### <a name="create-a-connection-for-a-visio-shape"></a><span data-ttu-id="42fc8-151">Visio 図形の接続を作成する</span><span class="sxs-lookup"><span data-stu-id="42fc8-151">Create a connection for a Visio shape</span></span>  
  
1.  <span data-ttu-id="42fc8-152">データ マイニング テンプレートを開いて、データ マイニング図形を 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="42fc8-152">Open the Data Mining Template, and select one of the data mining shapes.</span></span>  
  
2.  <span data-ttu-id="42fc8-153">空のページに図形をドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="42fc8-153">Drag and drop the shape to a blank page.</span></span>  
  
3.  <span data-ttu-id="42fc8-154">[**データソースの選択**] ダイアログボックスで、一覧からデータソースを選択するか、[**新規作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="42fc8-154">In the **Select a data source** dialog box, select a data source from the list, or click **New**.</span></span>  
  
4.  <span data-ttu-id="42fc8-155">[**新規**] を選択した場合は、前に説明した手順に従って、サーバーとカタログ名を指定するか、Web サービス経由で接続します。</span><span class="sxs-lookup"><span data-stu-id="42fc8-155">If you select **New**, follow the procedure that is described earlier to specify a server and catalog name, or to connect through a Web service.</span></span>  
  
##  <a name="changing-connections"></a><a name="bkmk_change"></a><span data-ttu-id="42fc8-156">接続の変更</span><span class="sxs-lookup"><span data-stu-id="42fc8-156">Changing Connections</span></span>  
 <span data-ttu-id="42fc8-157">同じワークシート内に複数の接続を作成できますが、一度にアクティブにできるのは 1 つの接続のみです。</span><span class="sxs-lookup"><span data-stu-id="42fc8-157">You can create multiple connections in the same worksheet, but only one connection can be active at a time.</span></span> <span data-ttu-id="42fc8-158">現在の接続の名前が [**接続**] ボタンに表示されます。</span><span class="sxs-lookup"><span data-stu-id="42fc8-158">The name of the current connection is displayed in the **Connection** button.</span></span>  
  
 <span data-ttu-id="42fc8-159">Excel 用のデータマイニングクライアントでは、[**トレース**] をクリックし、[**現在の接続**] をクリックして、現在の接続の接続文字列と状態を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="42fc8-159">In the Data Mining Client for Excel, you can also verify the connection string and status for the current connection by clicking **Trace** and then clicking **Current Connection**.</span></span>  
  
#### <a name="use-a-different-server-connection"></a><span data-ttu-id="42fc8-160">別のサーバー接続を使用する</span><span class="sxs-lookup"><span data-stu-id="42fc8-160">Use a different server connection</span></span>  
  
1.  <span data-ttu-id="42fc8-161">[**接続**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="42fc8-161">Click **Connection**.</span></span>  
  
2.  <span data-ttu-id="42fc8-162">[ **Analysis Services 接続**] ウィンドウで、[**その他の**接続] ボックスの一覧から接続を選択し、[**最新の設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="42fc8-162">In the **Analysis Services Connections** pane, select a connection from the **Other Connections** list, and click **Make Current**.</span></span>  
  
3.  <span data-ttu-id="42fc8-163">[**接続テスト**] をクリックして、接続が使用可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="42fc8-163">Click **Test Connection** to verify that the connection is available.</span></span>  
  
 <span data-ttu-id="42fc8-164">マイニング モデルの処理が完了すると、その結果はローカルに保存されます。あるサーバーへの接続を閉じて、別のサーバーに接続しても影響を受けることはありません。</span><span class="sxs-lookup"><span data-stu-id="42fc8-164">After a mining model has finished processing, the results are stored locally, and there is no effect on the data if you close the connection to one server and then connect to another server.</span></span> <span data-ttu-id="42fc8-165">ただし、データ マイニング モデルの処理中に接続を変更したり、接続が切断されたりしないように注意してください。データが破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="42fc8-165">However, you should avoid changing connections or losing the connection when a data mining model is being processed, because this could corrupt data.</span></span>  
  
#### <a name="modify-an-existing-server-connection"></a><span data-ttu-id="42fc8-166">既存のサーバー接続を変更する</span><span class="sxs-lookup"><span data-stu-id="42fc8-166">Modify an existing server connection</span></span>  
  
1.  <span data-ttu-id="42fc8-167">既存の接続は変更できません。別のデータベースまたは別のサーバーに接続する場合は、新しい接続を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="42fc8-167">You cannot modify an existing connection; if you want to connect to a different database or a different server, you should create a new connection.</span></span>  
  
2.  <span data-ttu-id="42fc8-168">接続文字列を変更してクエリ タイムアウトの値を増やしたり、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスに特有のその他のパラメーターを追加する必要がある場合は、接続文字列が格納されている .dmc ファイルを編集するという方法もあります。</span><span class="sxs-lookup"><span data-stu-id="42fc8-168">If you must modify the connection string to increase the query timeout or add other parameters specific to your instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], one option is to edit the .dmc file, where the connection string is stored.</span></span>  
  
     <span data-ttu-id="42fc8-169">\<drive:>\ ユーザー \\<myusername \> \AppData\Local\Microsoft\Data マイニングアドイン</span><span class="sxs-lookup"><span data-stu-id="42fc8-169">\<drive:>\Users\\<myusername\>\AppData\Local\Microsoft\Data Mining Add-in</span></span>  
  
##  <a name="connecting-to-external-data-sources"></a><a name="bkmk_extconnections"></a><span data-ttu-id="42fc8-170">外部データソースへの接続</span><span class="sxs-lookup"><span data-stu-id="42fc8-170">Connecting to External Data Sources</span></span>  
 <span data-ttu-id="42fc8-171">[**分析**] リボンのツールは Excel のデータと排他的に機能しますが、[**データマイニング**] リボンのツールを使用すると、外部データソースに直接接続して、モデルの入力またはサンプリングとして使用することができます。</span><span class="sxs-lookup"><span data-stu-id="42fc8-171">Whereas the tools in the **Analyze** ribbon work exclusively with data in Excel, the tools in the **Data Mining** ribbon let you connect directly to external data sources to use as inputs for your model, or for sampling.</span></span>  
  
 <span data-ttu-id="42fc8-172">これらのアドインにある以下のツールはデータ マイニング用外部データの使用をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="42fc8-172">The following tools in these add-ins support use of external data for data mining:</span></span>  
  
-   [<span data-ttu-id="42fc8-173">データマイニングアドイン SQL Server &#40;サンプルデータ&#41;</span><span class="sxs-lookup"><span data-stu-id="42fc8-173">Sample Data &#40;SQL Server Data Mining Add-ins&#41;</span></span>](sample-data-sql-server-data-mining-add-ins.md)  
  
-   [<span data-ttu-id="42fc8-174">分類ウィザード &#40;Excel 用データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="42fc8-174">Classify Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](classify-wizard-data-mining-add-ins-for-excel.md)  
  
-   [<span data-ttu-id="42fc8-175">推定ウィザード &#40;Excel 用データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="42fc8-175">Estimate Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](estimate-wizard-data-mining-add-ins-for-excel.md)  
  
-   [<span data-ttu-id="42fc8-176">クラスターウィザード &#40;Excel 用データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="42fc8-176">Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](cluster-wizard-data-mining-add-ins-for-excel.md)  
  
-   [<span data-ttu-id="42fc8-177">予測ウィザード &#40;Excel 用データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="42fc8-177">Forecast Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](forecast-wizard-data-mining-add-ins-for-excel.md)  
  
-   [<span data-ttu-id="42fc8-178">SQL Server データマイニングアドイン &#40;マイニング構造の作成&#41;</span><span class="sxs-lookup"><span data-stu-id="42fc8-178">Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41;</span></span>](create-mining-structure-sql-server-data-mining-add-ins.md)  
  
-   [<span data-ttu-id="42fc8-179">精度チャート &#40;SQL Server データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="42fc8-179">Accuracy Chart &#40;SQL Server Data Mining Add-ins&#41;</span></span>](accuracy-chart-sql-server-data-mining-add-ins.md)  
  
-   [<span data-ttu-id="42fc8-180">利益チャート &#40;SQL Server データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="42fc8-180">Profit Chart &#40;SQL Server Data Mining Add-ins&#41;</span></span>](profit-chart-sql-server-data-mining-add-ins.md)  
  
-   [<span data-ttu-id="42fc8-181">分類マトリックス &#40;SQL Server データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="42fc8-181">Classification Matrix &#40;SQL Server Data Mining Add-ins&#41;</span></span>](classification-matrix-sql-server-data-mining-add-ins.md)  
  
### <a name="using-analysis-services-as-a-data-source"></a><span data-ttu-id="42fc8-182">Analysis Services のデータ ソースとしての使用</span><span class="sxs-lookup"><span data-stu-id="42fc8-182">Using Analysis Services as a Data Source</span></span>  
 <span data-ttu-id="42fc8-183">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] キューブまたはテーブル モデルに格納されたデータに直接アクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="42fc8-183">You cannot directly access data stored in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube or tabular model.</span></span> <span data-ttu-id="42fc8-184">代わりに、Excel で [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーへの接続を作成し、そのデータを使用してモデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="42fc8-184">Instead, create a connection in Excel to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server, and use the data to create a model.</span></span>  
  
### <a name="relational-data-sources"></a><span data-ttu-id="42fc8-185">リレーショナルデータソース</span><span class="sxs-lookup"><span data-stu-id="42fc8-185">Relational Data Sources</span></span>  
 <span data-ttu-id="42fc8-186">モデルへの入力としてリレーショナル ソースのデータを使用する場合は、次のバージョンの SQL Server に接続できます。</span><span class="sxs-lookup"><span data-stu-id="42fc8-186">If you want to use data from a relational source as input to your model, you can connect to the following versions of SQL Server:</span></span>  
  
-   <span data-ttu-id="42fc8-187">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="42fc8-187">SQL Server 2008</span></span>  
  
-   <span data-ttu-id="42fc8-188">SQL Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="42fc8-188">SQL Server 2008 R2</span></span>  
  
-   <span data-ttu-id="42fc8-189">SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="42fc8-189">SQL Server 2012</span></span>  
  
 <span data-ttu-id="42fc8-190">また、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] でデータ ソースとしてサポートされている他のリレーショナル データ ソースからデータを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="42fc8-190">You can also get data from any other relational data source that is supported as a data source by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="42fc8-191">サポートされているデータソースの詳細については、「[多次元モデルのデータソース](multidimensional-models/data-sources-in-multidimensional-models.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42fc8-191">For information about supported data sources, see [Data Sources in Multidimensional Models](multidimensional-models/data-sources-in-multidimensional-models.md)</span></span>  
  
 <span data-ttu-id="42fc8-192">以下のデータ型はデータ マイニングで使用することができません。モデルの構築時にこのデータ型が含まれていた場合は、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="42fc8-192">Note that the following data types cannot be used for data mining and will result in an error if included when you build a model:</span></span>  
  
-   <span data-ttu-id="42fc8-193">ntext</span><span class="sxs-lookup"><span data-stu-id="42fc8-193">ntext</span></span>  
  
-   <span data-ttu-id="42fc8-194">binary</span><span class="sxs-lookup"><span data-stu-id="42fc8-194">binary</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42fc8-195">参照</span><span class="sxs-lookup"><span data-stu-id="42fc8-195">See Also</span></span>  
 [<span data-ttu-id="42fc8-196">Excel 用のデータマイニングクライアントのトレース &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="42fc8-196">Trace &#40;Data Mining Client for Excel&#41;</span></span>](trace-data-mining-client-for-excel.md)  
  
  
