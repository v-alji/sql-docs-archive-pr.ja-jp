---
title: SQL Server の接続の種類 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 957e7091-e08f-48d2-9506-872227ae8b20
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 34a519c8a291dc351be98316b18a45ade4918579
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643192"
---
# <a name="sql-server-connection-type-ssrs"></a><span data-ttu-id="486d3-102">SQL Server の接続の種類 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="486d3-102">SQL Server Connection Type (SSRS)</span></span>
  <span data-ttu-id="486d3-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのデータをレポートに含めるには、種類が [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のレポート データ ソースに基づいたデータセットが必要です。</span><span class="sxs-lookup"><span data-stu-id="486d3-103">To include data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database in your report, you must have a dataset that is based on a report data source of type [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="486d3-104">このビルトイン データ ソースの種類は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ拡張機能に基づいています。</span><span class="sxs-lookup"><span data-stu-id="486d3-104">This built-in data source type is based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data extension.</span></span> <span data-ttu-id="486d3-105">現在のバージョンと以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続してデータを取得するには、このデータ ソースの種類を使用します。</span><span class="sxs-lookup"><span data-stu-id="486d3-105">Use this data source type to connect to and retrieve data from the current version and earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="486d3-106">このデータ拡張機能は、複数の値を持つパラメーター、サーバー集計、および接続文字列とは別に管理される資格情報をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="486d3-106">This data extension supports multivalue parameters, server aggregates, and credentials managed separately from the connection string.</span></span>  
  
 <span data-ttu-id="486d3-107">このトピックの情報を使用して、データ ソースを構築してください。</span><span class="sxs-lookup"><span data-stu-id="486d3-107">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="486d3-108">詳細な手順については、「[データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;の追加と検証](add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="486d3-108">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="486d3-109">接続文字列</span><span class="sxs-lookup"><span data-stu-id="486d3-109">Connection String</span></span>  
 <span data-ttu-id="486d3-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続する場合は、サーバー上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのデータベース オブジェクトに接続します。</span><span class="sxs-lookup"><span data-stu-id="486d3-110">When you connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, you are connecting to the database object in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a server.</span></span> <span data-ttu-id="486d3-111">データベースには、複数のテーブル、ビュー、およびストアド プロシージャを含むスキーマが複数存在している場合があります。</span><span class="sxs-lookup"><span data-stu-id="486d3-111">The database might have multiple schemas that have multiple tables, views, and stored procedures.</span></span> <span data-ttu-id="486d3-112">クエリ デザイナーで、使用するデータベース オブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="486d3-112">You specify the database object to use in the query designer.</span></span> <span data-ttu-id="486d3-113">接続文字列でデータベースを指定しない場合は、データベース管理者によって割り当てられた既定のデータベースに接続されます。</span><span class="sxs-lookup"><span data-stu-id="486d3-113">If you do not specify a database in the connection string, you connect to the default database that the database administrator assigned to you.</span></span>  
  
 <span data-ttu-id="486d3-114">データ ソースへの接続に使用する接続情報および資格情報については、データベース管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="486d3-114">Contact your database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="486d3-115">ローカル クライアント上のサンプル データベースを指定する接続文字列の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="486d3-115">The following connection string example specifies a sample database on the local client:</span></span>  
  
```  
Data Source=<server>;Initial Catalog=AdventureWorks  
```  
  
 <span data-ttu-id="486d3-116">接続文字列の例の詳細については、「 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="486d3-116">For more information about connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="486d3-117">[資格情報]</span><span class="sxs-lookup"><span data-stu-id="486d3-117">Credentials</span></span>  
 <span data-ttu-id="486d3-118">クエリの実行、ローカルでのレポートのプレビュー、およびレポート サーバーからのレポートのプレビューには、資格情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="486d3-118">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="486d3-119">レポートをパブリッシュした後、レポートをレポート サーバーで実行するときに、データを取得するための権限が有効な状態になるように、データ ソースの資格情報を変更する必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="486d3-119">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="486d3-120">レポート作成クライアントから、次のオプションを使用して資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="486d3-120">From a report authoring client, the following options are available to specify credentials:</span></span>  
  
-   <span data-ttu-id="486d3-121">現在の Windows ユーザー (統合セキュリティとも呼ばれます)。</span><span class="sxs-lookup"><span data-stu-id="486d3-121">Current Windows user (also known as integrated security).</span></span>  
  
-   <span data-ttu-id="486d3-122">保存されているユーザー名とパスワードを使用する。</span><span class="sxs-lookup"><span data-stu-id="486d3-122">Use a stored user name and password.</span></span>  
  
-   <span data-ttu-id="486d3-123">ユーザーに資格情報を要求する。</span><span class="sxs-lookup"><span data-stu-id="486d3-123">Prompt the user for credentials.</span></span> <span data-ttu-id="486d3-124">このオプションでは Windows 統合セキュリティのみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="486d3-124">This option supports Windows integrated security only.</span></span>  
  
-   <span data-ttu-id="486d3-125">資格情報を必要としない。</span><span class="sxs-lookup"><span data-stu-id="486d3-125">No credentials are required.</span></span> <span data-ttu-id="486d3-126">このオプションを使用するには、レポート サーバーで自動実行アカウントを構成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="486d3-126">To use this option, you must have the unattended execution account configured on the report server.</span></span> <span data-ttu-id="486d3-127">詳細については、msdn.microsoft.com で [Reporting Services に関するドキュメント](https://go.microsoft.com/fwlink/?linkid=121312)の「[自動実行アカウントの構成 &#40;SSRS 構成マネージャー&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="486d3-127">For more information, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="486d3-128">詳細については、「 [Reporting Services のデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)」または「[レポートビルダーで資格情報を指定する](../specify-credentials-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="486d3-128">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
  
##  <a name="queries"></a><a name="Query"></a> <span data-ttu-id="486d3-129">クエリ</span><span class="sxs-lookup"><span data-stu-id="486d3-129">Queries</span></span>  
 <span data-ttu-id="486d3-130">クエリでは、レポート データセット用に取得するデータを指定します。</span><span class="sxs-lookup"><span data-stu-id="486d3-130">A query specifies which data to retrieve for a report dataset.</span></span> <span data-ttu-id="486d3-131">クエリの結果セットの列には、データセットのフィールド コレクションが設定されます。</span><span class="sxs-lookup"><span data-stu-id="486d3-131">The columns in the result set for a query populate the field collection for a dataset.</span></span> <span data-ttu-id="486d3-132">レポートによって処理されるのは、クエリから取得された最初の結果セットだけです。</span><span class="sxs-lookup"><span data-stu-id="486d3-132">A report processes only the first result set that a query retrieves.</span></span>  
  
 <span data-ttu-id="486d3-133">新しいクエリを作成するか、グラフィカル クエリ デザイナーで表示できる既存のクエリを開く場合、既定でリレーショナル クエリ デザイナーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="486d3-133">By default, if you create a new query or open an existing query that can be represented in the graphical query designer, the relational query designer is available.</span></span> <span data-ttu-id="486d3-134">クエリは、次の方法で指定できます。</span><span class="sxs-lookup"><span data-stu-id="486d3-134">You can specify a query in the following ways:</span></span>  
  
-   <span data-ttu-id="486d3-135">クエリを対話形式で作成します。</span><span class="sxs-lookup"><span data-stu-id="486d3-135">Build a query interactively.</span></span> <span data-ttu-id="486d3-136">データベース スキーマ別に編成された、テーブル、ビュー、ストアド プロシージャ、およびその他のデータベース アイテムの階層ビューが表示されるリレーショナル クエリ デザイナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="486d3-136">Use the relational query designer that displays a hierarchical view of tables, views, stored procedures, and other database items, organized by database schema.</span></span> <span data-ttu-id="486d3-137">テーブルまたはビューから列を選択するか、ストアド プロシージャまたはテーブル値関数を指定します。</span><span class="sxs-lookup"><span data-stu-id="486d3-137">Select columns from tables or views, or specify stored procedures or table-valued functions.</span></span> <span data-ttu-id="486d3-138">フィルター条件を指定して、取得するデータの行数を制限します。</span><span class="sxs-lookup"><span data-stu-id="486d3-138">Limit the number of rows of data to retrieve by specifying filter criteria.</span></span> <span data-ttu-id="486d3-139">パラメーター オプションを設定してレポートの実行時にフィルターをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="486d3-139">Customize the filter when the report runs by setting the parameter option.</span></span>  
  
-   <span data-ttu-id="486d3-140">クエリを入力するか、貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="486d3-140">Type or paste a query.</span></span> <span data-ttu-id="486d3-141">テキスト ベースのクエリ デザイナーは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] テキストを直接入力する、クエリ テキストを別のソースから貼り付ける、リレーショナル クエリ デザイナーでは作成できない複雑なクエリを入力する、クエリ ベースの式を入力する、などの場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="486d3-141">Use the text-based query designer to enter [!INCLUDE[tsql](../../includes/tsql-md.md)] text directly, to paste query text from another source, to enter complex queries that cannot be built by using the relational query designer, or to enter query-based expressions.</span></span>  
  
-   <span data-ttu-id="486d3-142">ファイルまたはレポートから既存のクエリをインポートします。</span><span class="sxs-lookup"><span data-stu-id="486d3-142">Import an existing query from a file or report.</span></span> <span data-ttu-id="486d3-143">クエリ デザイナーの **[クエリのインポート]** ボタンを使用して、.sql ファイルまたは .rdl ファイルを参照し、クエリをインポートします。</span><span class="sxs-lookup"><span data-stu-id="486d3-143">Use the **Import** query button from either query designer to browse to a .sql file or .rdl file and import a query.</span></span>  
  
 <span data-ttu-id="486d3-144">詳細については、「[リレーショナル クエリ デザイナーのユーザー インターフェイス &#40;レポート ビルダー&#41;](relational-query-designer-user-interface-report-builder.md)」および「[テキストベースのクエリ デザイナーのユーザー インターフェイス &#40;レポート ビルダー&#41;](text-based-query-designer-user-interface-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="486d3-144">For more information, see [Relational Query Designer User Interface &#40;Report Builder&#41;](relational-query-designer-user-interface-report-builder.md) and [Text-based Query Designer User Interface &#40;Report Builder&#41;](text-based-query-designer-user-interface-report-builder.md).</span></span>  
  
 <span data-ttu-id="486d3-145">次のクエリ モードがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="486d3-145">The following query modes are supported:</span></span>  
  
-   <span data-ttu-id="486d3-146">[Text](#QueryText)[!INCLUDE[tsql](../../includes/tsql-md.md)] のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="486d3-146">[Text](#QueryText) Type in [!INCLUDE[tsql](../../includes/tsql-md.md)] commands.</span></span>  
  
-   <span data-ttu-id="486d3-147">[ストアド プロシージャ](#QueryStoredProcedure) : ストアド プロシージャの一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="486d3-147">[Stored Procedure](#QueryStoredProcedure) Choose from a list of stored procedures.</span></span>  
  
###  <a name="using-query-type-text"></a><a name="QueryText"></a> <span data-ttu-id="486d3-148">Text の種類のクエリの使用</span><span class="sxs-lookup"><span data-stu-id="486d3-148">Using Query Type Text</span></span>  
 <span data-ttu-id="486d3-149">テキスト ベースのクエリ デザイナーでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] コマンドを入力して、データセット内のデータを定義できます。</span><span class="sxs-lookup"><span data-stu-id="486d3-149">In the text-based query designer, you can type [!INCLUDE[tsql](../../includes/tsql-md.md)] commands to define the data in a dataset.</span></span> <span data-ttu-id="486d3-150">たとえば、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリでは、マーケティング アシスタントであるすべての従業員の名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="486d3-150">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] query selects the names of all employees who are marketing assistants:</span></span>  
  
```  
SELECT  
  HumanResources.Employee.BusinessEntityID  
  ,HumanResources.Employee.JobTitle  
  ,Person.Person.FirstName  
  ,Person.Person.LastName  
FROM  
  Person.Person  
  INNER JOIN HumanResources.Employee  
    ON Person.Person.BusinessEntityID = HumanResources.Employee.BusinessEntityID  
WHERE HumanResources.Employee.JobTitle = 'Marketing Assistant'   
```  
  
 <span data-ttu-id="486d3-151">ツール バーの **[実行]** ボタン ( **!** ) をクリックすると、クエリが実行され、結果セットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="486d3-151">Click the **Run** button (**!**) on the toolbar to run the query and display a result set.</span></span>  
  
 <span data-ttu-id="486d3-152">このクエリをパラメーター化するには、クエリ パラメーターを追加します。</span><span class="sxs-lookup"><span data-stu-id="486d3-152">To parameterize this query, add a query parameter.</span></span> <span data-ttu-id="486d3-153">たとえば、WHERE 句を次の構文に変更します。</span><span class="sxs-lookup"><span data-stu-id="486d3-153">For example, change the WHERE clause to the following:</span></span>  
  
 `WHERE HumanResources.Employee.JobTitle = (@JobTitle)`  
  
 <span data-ttu-id="486d3-154">クエリの実行時に、クエリ パラメーターに対応するレポート パラメーターが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="486d3-154">When you run the query, report parameters that correspond to query parameters are automatically created.</span></span> <span data-ttu-id="486d3-155">詳細については、このトピックの「 [クエリ パラメーター](#Parameters) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="486d3-155">For more information, see [Query Parameters](#Parameters) later in this topic.</span></span>  
  
  
###  <a name="using-query-type-storedprocedure"></a><a name="QueryStoredProcedure"></a> <span data-ttu-id="486d3-156">StoredProcedure の種類のクエリの使用</span><span class="sxs-lookup"><span data-stu-id="486d3-156">Using Query Type StoredProcedure</span></span>  
 <span data-ttu-id="486d3-157">データセット クエリのストアド プロシージャは、次のいずれかの方法で指定できます。</span><span class="sxs-lookup"><span data-stu-id="486d3-157">You can specify a stored procedure for a dataset query in one of the following ways:</span></span>  
  
-   <span data-ttu-id="486d3-158">**[データセットのプロパティ]** ダイアログ ボックスで、 **[ストアド プロシージャ]** オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="486d3-158">In the **Dataset Properties** dialog box, set the **Stored Procedure** option.</span></span> <span data-ttu-id="486d3-159">ドロップダウン リストからストアド プロシージャまたはテーブル値関数を選択します。</span><span class="sxs-lookup"><span data-stu-id="486d3-159">Choose from the drop-down list of stored procedures and table-valued functions.</span></span>  
  
-   <span data-ttu-id="486d3-160">リレーショナル クエリ デザイナーのデータベース ビュー ペインで、ストアド プロシージャまたはテーブル値関数を選択します。</span><span class="sxs-lookup"><span data-stu-id="486d3-160">In the relational query designer, in the Database view pane, select a stored procedure or table-valued function.</span></span>  
  
-   <span data-ttu-id="486d3-161">テキスト ベースのクエリ デザイナーで、ツール バーから **[StoredProcedure]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="486d3-161">In the text-based query designer, select **StoredProcedure** from the toolbar.</span></span>  
  
 <span data-ttu-id="486d3-162">ストアド プロシージャまたはテーブル値関数を選択したら、クエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="486d3-162">After you select a stored procedure or table-valued function, you can run the query.</span></span> <span data-ttu-id="486d3-163">入力パラメーター値の入力を要求されます。</span><span class="sxs-lookup"><span data-stu-id="486d3-163">You will be prompted for input parameter values.</span></span> <span data-ttu-id="486d3-164">クエリの実行時に、入力パラメーターに対応するレポート パラメーターが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="486d3-164">When you run the query, report parameters that correspond to input parameters are automatically created.</span></span> <span data-ttu-id="486d3-165">詳細については、このトピックの「 [クエリ パラメーター](#Parameters) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="486d3-165">For more information, see [Query Parameters](#Parameters) later in this topic.</span></span>  
  
 <span data-ttu-id="486d3-166">ストアド プロシージャから取得した最初の結果セットだけがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="486d3-166">Only the first result set that is retrieved for a stored procedure is supported.</span></span> <span data-ttu-id="486d3-167">ストアド プロシージャから複数の結果セットが返された場合、最初の結果セットだけが使用されます。</span><span class="sxs-lookup"><span data-stu-id="486d3-167">If a stored procedure returns multiple result sets, only the first one is used.</span></span>  
  
 <span data-ttu-id="486d3-168">既定値が指定されたパラメーターがストアド プロシージャに含まれている場合、パラメーターの値として DEFAULT キーワードを使用してその値にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="486d3-168">If a stored procedure has a parameter that has a default value, you can access that value by using the DEFAULT keyword as a value for the parameter.</span></span> <span data-ttu-id="486d3-169">クエリ パラメーターがレポート パラメーターにリンクされている場合は、レポート パラメーターの入力ボックスで DEFAULT キーワードを入力または選択できます。</span><span class="sxs-lookup"><span data-stu-id="486d3-169">If the query parameter is linked to a report parameter, the user can type or select the word DEFAULT in the input box for the report parameter.</span></span>  
  
 <span data-ttu-id="486d3-170">詳細については、msdn.microsoft.com にある [SQL Server オンライン ブック](https://go.microsoft.com/fwlink/?linkid=98335) の「ストアド プロシージャ (データベース エンジン)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="486d3-170">For more information, see "Stored Procedures (Database Engine)" in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=98335) on msdn.microsoft.com.</span></span>  
  
  
##  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="486d3-171">パラメーター</span><span class="sxs-lookup"><span data-stu-id="486d3-171">Parameters</span></span>  
 <span data-ttu-id="486d3-172">入力パラメーターを含むクエリ変数またはストアド プロシージャがクエリ テキストに含まれている場合、対応するデータセットのクエリ パラメーターとレポートのレポート パラメーターが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="486d3-172">When query text contains query variables or stored procedures that have input parameters, the corresponding query parameters for the dataset and report parameters for the report are automatically generated.</span></span> <span data-ttu-id="486d3-173">クエリ テキストには、各クエリ変数の DECLARE ステートメントを含めないでください。</span><span class="sxs-lookup"><span data-stu-id="486d3-173">The query text must not include the DECLARE statement for each query variable.</span></span>  
  
 <span data-ttu-id="486d3-174">たとえば、次の SQL クエリでは、`EmpID` という名前のレポート パラメーターが作成されます。</span><span class="sxs-lookup"><span data-stu-id="486d3-174">For example, the following SQL query creates a report parameter named `EmpID`:</span></span>  
  
```  
SELECT FirstName, LastName FROM HumanResources.Employee E INNER JOIN  
       Person.Contact C ON  E.ContactID=C.ContactID   
WHERE EmployeeID = (@EmpID)  
```  
  
 <span data-ttu-id="486d3-175">レポート パラメーターは、既定のプロパティ値を使用して作成されます。この既定のプロパティ値は、変更が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="486d3-175">Report parameters are created with default property values that you might need to modify.</span></span> <span data-ttu-id="486d3-176">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="486d3-176">For example:</span></span>  
  
-   <span data-ttu-id="486d3-177">各レポート パラメーターの既定のデータ型は **Text**です。</span><span class="sxs-lookup"><span data-stu-id="486d3-177">By default, each report parameter is data type **Text**.</span></span> <span data-ttu-id="486d3-178">基になるデータのデータ型が異なる場合は、パラメーターのデータ型を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="486d3-178">If the underlying data is a different data type, you must change the parameter data type.</span></span>  
  
-   <span data-ttu-id="486d3-179">複数値パラメーターのオプションを選択した場合は、クエリを手動で変更し、`IN` 演算子を使用して値がセットの一部かどうかをテストする必要があります (`WHERE EmployeeID IN (@EmpID)` など)。</span><span class="sxs-lookup"><span data-stu-id="486d3-179">If you select the option for multivalued parameters, you must manually change the query to test whether values are part of a set by using the `IN` operator, for example, `WHERE EmployeeID IN (@EmpID)`.</span></span>  
  
 <span data-ttu-id="486d3-180">詳細については、「 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../report-design/report-parameters-report-builder-and-report-designer.md)にあります。</span><span class="sxs-lookup"><span data-stu-id="486d3-180">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="486d3-181">解説</span><span class="sxs-lookup"><span data-stu-id="486d3-181">Remarks</span></span>  
 <span data-ttu-id="486d3-182">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースからのデータの取得は、OLE DB または ODBC のデータ ソースの種類を使用して行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="486d3-182">You can also retrieve data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database by using an OLE DB or ODBC data source type.</span></span> <span data-ttu-id="486d3-183">詳細については、「[OLE DB の接続の種類 &#40;SSRS&#41;](ole-db-connection-type-ssrs.md)」または「[ODBC の接続の種類 &#40;SSRS&#41;](odbc-connection-type-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="486d3-183">For more information, see [OLE DB Connection Type &#40;SSRS&#41;](ole-db-connection-type-ssrs.md) or [ODBC Connection Type &#40;SSRS&#41;](odbc-connection-type-ssrs.md).</span></span>  
  
###### <a name="platform-and-version-information"></a><span data-ttu-id="486d3-184">プラットフォームおよびバージョン情報</span><span class="sxs-lookup"><span data-stu-id="486d3-184">Platform and Version Information</span></span>  
 <span data-ttu-id="486d3-185">プラットフォームおよびバージョン サポートの詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブック](https://go.microsoft.com/fwlink/?linkid=121312)にある [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ドキュメントの「[Reporting Services でサポートされるデータ ソース (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="486d3-185">For more information about platform and version support, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a> <span data-ttu-id="486d3-186">操作方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="486d3-186">How-To Topics</span></span>  
 <span data-ttu-id="486d3-187">データ接続、データ ソース、およびデータセットを操作する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="486d3-187">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="486d3-188">データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;に追加して検証する</span><span class="sxs-lookup"><span data-stu-id="486d3-188">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="486d3-189">共有データセットまたは埋め込みデータセットの作成 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="486d3-189">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="486d3-190">データセットへのフィルターの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="486d3-190">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="486d3-191">関連項目</span><span class="sxs-lookup"><span data-stu-id="486d3-191">Related Sections</span></span>  
 <span data-ttu-id="486d3-192">次に示すセクションでは、レポート データの概念が詳細に説明されているほか、データに関連するレポートのパーツを定義しカスタマイズし使用する手順が説明されています。</span><span class="sxs-lookup"><span data-stu-id="486d3-192">These sections of the documentation provide in-depth conceptual information about report data, and procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="486d3-193">レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する</span><span class="sxs-lookup"><span data-stu-id="486d3-193">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="486d3-194">レポートのデータへのアクセスの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="486d3-194">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="486d3-195">レポート ビルダーでのデータ接続、データ ソース、および接続文字列</span><span class="sxs-lookup"><span data-stu-id="486d3-195">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="486d3-196">データ接続とデータ ソースについて説明します。</span><span class="sxs-lookup"><span data-stu-id="486d3-196">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="486d3-197">レポート埋め込みデータセットと共有データセット (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="486d3-197">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="486d3-198">埋め込みデータセットと共有データセットについて説明します。</span><span class="sxs-lookup"><span data-stu-id="486d3-198">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="486d3-199">データセット フィールド コレクション (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="486d3-199">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="486d3-200">クエリによって生成されるデータセット フィールド コレクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="486d3-200">Provides information about the dataset field collection generated by the query.</span></span>  
  
 <span data-ttu-id="486d3-201">[Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブックの [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ドキュメント](https://go.microsoft.com/fwlink/?linkid=121312))。</span><span class="sxs-lookup"><span data-stu-id="486d3-201">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="486d3-202">各データ拡張機能のプラットフォームおよびバージョン サポートに関する詳細な情報です。</span><span class="sxs-lookup"><span data-stu-id="486d3-202">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="486d3-203">参照</span><span class="sxs-lookup"><span data-stu-id="486d3-203">See Also</span></span>  
 <span data-ttu-id="486d3-204">[レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="486d3-204">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="486d3-205">[データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="486d3-205">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="486d3-206">式 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="486d3-206">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
