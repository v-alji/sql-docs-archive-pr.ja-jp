---
title: SQL Azure の接続の種類 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c84def6c-e8cf-43d9-9912-098171a7ce79
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e2c3d3e75117996f088cff96b2b7a8d4cd504127
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643194"
---
# <a name="sql-azure-connection-type-ssrs"></a><span data-ttu-id="83930-102">SQL Azure の接続の種類 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="83930-102">SQL Azure Connection Type (SSRS)</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="83930-103">[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]は、テクノロジに基づいて構築されたクラウドベースのホスト型リレーショナルデータベースです [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="83930-103">[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] is a cloud-based, hosted relational database built on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technologies.</span></span> <span data-ttu-id="83930-104">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] からのデータをレポートに含めるには、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]の種類のレポート データ ソースに基づいたデータセットが必要です。</span><span class="sxs-lookup"><span data-stu-id="83930-104">To include data from [!INCLUDE[ssSDS](../../includes/sssds-md.md)] in your report, you must have a dataset that is based on a report data source of type [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span> <span data-ttu-id="83930-105">このビルトイン データ ソースの種類は、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] データ拡張機能に基づいています。</span><span class="sxs-lookup"><span data-stu-id="83930-105">This built-in data source type is based on the [!INCLUDE[ssSDS](../../includes/sssds-md.md)] data extension.</span></span> <span data-ttu-id="83930-106">このデータ ソースの種類を使用して、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]からのデータに接続し、そのデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="83930-106">Use this data source type to connect to and retrieve data from [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>

 <span data-ttu-id="83930-107">このデータ拡張機能は、接続文字列とは個別に管理される、複数の値を持つパラメーター、サーバー集計、および資格情報をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="83930-107">This data extension supports multivalued parameters, server aggregates, and credentials managed separately from the connection string.</span></span>

 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] <span data-ttu-id="83930-108">は、オンプレミスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスと似ています。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] からは、一部の例外を除き、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と同じようにデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="83930-108">is similar to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on your premises and getting data from [!INCLUDE[ssSDS](../../includes/sssds-md.md)] is, with a few exceptions, identical to getting data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>

> [!NOTE]
>  <span data-ttu-id="83930-109">[!INCLUDE[ssSDS](../../includes/sssds-md.md)]への接続を開くときに、接続タイムアウトを 30 秒に設定してください。</span><span class="sxs-lookup"><span data-stu-id="83930-109">When opening a connection to a [!INCLUDE[ssSDS](../../includes/sssds-md.md)], set the connection timeout to 30 seconds.</span></span>

 <span data-ttu-id="83930-110">詳細については、 [Azure SQL Database のドキュメント](https://docs.microsoft.com/azure/sql-database/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83930-110">For more information, see [Azure SQL Database Documentation](https://docs.microsoft.com/azure/sql-database/).</span></span>

 <span data-ttu-id="83930-111">このトピックの情報を使用して、データ ソースを構築してください。</span><span class="sxs-lookup"><span data-stu-id="83930-111">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="83930-112">詳細な手順については、「[データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;の追加と検証](add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83930-112">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>

##  <a name="connection-string"></a><a name="Connection"></a><span data-ttu-id="83930-113">接続文字列</span><span class="sxs-lookup"><span data-stu-id="83930-113">Connection String</span></span>
 <span data-ttu-id="83930-114">[!INCLUDE[ssSDS](../../includes/sssds-md.md)]に接続する場合、クラウド内のデータベース オブジェクトに接続します。</span><span class="sxs-lookup"><span data-stu-id="83930-114">When you connect to [!INCLUDE[ssSDS](../../includes/sssds-md.md)], you are connecting to a database object in the cloud.</span></span> <span data-ttu-id="83930-115">オンサイトのデータベースと同様に、ホストされているデータベースには、複数のテーブル、ビュー、およびストアド プロシージャを含むスキーマが複数存在している場合があります。</span><span class="sxs-lookup"><span data-stu-id="83930-115">Just like onsite databases, the hosted database might have multiple schemas that have multiple tables, views, and stored procedures.</span></span> <span data-ttu-id="83930-116">クエリ デザイナーで、使用するデータベース オブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="83930-116">You specify the database object to use in the query designer.</span></span> <span data-ttu-id="83930-117">接続文字列でデータベースを指定しない場合は、管理者によって割り当てられた既定のデータベースに接続されます。</span><span class="sxs-lookup"><span data-stu-id="83930-117">If you do not specify a database in the connection string, you connect to the default database that the administrator assigned to you.</span></span>

 <span data-ttu-id="83930-118">データ ソースへの接続に使用する接続情報および資格情報については、データベース管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="83930-118">Contact your database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="83930-119">AdventureWorks というホストされているサンプル データベースを指定する接続文字列の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="83930-119">The following connection string example specifies a hosted sample database named AdventureWorks.</span></span>

```
Data Source=<host>;Initial Catalog=AdventureWorks; Encrypt=True;
```

 <span data-ttu-id="83930-120">また、 **[データ ソースのプロパティ]** ダイアログ ボックスを使用して、ユーザー名やパスワードなどの資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="83930-120">In addition, you use the **Data Sources Properties** dialog box to provide credentials such as user name and password.</span></span> <span data-ttu-id="83930-121">`User Id` オプションと `Password` オプションは、接続文字列に自動的に付加されます。これらを接続文字列の一部として入力する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="83930-121">The `User Id` and `Password` options are automatically appended to the connection string; you do not need to type them as part of the connection string.</span></span>

 <span data-ttu-id="83930-122">詳細および接続文字列の例については、「 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83930-122">For more information and connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>

##  <a name="credentials"></a><a name="Credentials"></a><span data-ttu-id="83930-123">認証</span><span class="sxs-lookup"><span data-stu-id="83930-123">Credentials</span></span>
 <span data-ttu-id="83930-124">Windows 認証 (統合セキュリティ) はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="83930-124">Windows Authentication (integrated security) is not supported.</span></span> <span data-ttu-id="83930-125">Windows 認証を使用して [!INCLUDE[ssSDS](../../includes/sssds-md.md)] に接続しようとすると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="83930-125">If you attempt to connect to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] using Windows Authentication an error occurs.</span></span> [!INCLUDE[ssSDS](../../includes/sssds-md.md)] <span data-ttu-id="83930-126">でサポートされているのが SQL Server 認証 (ユーザー名とパスワード) のみであるため、ユーザーは [!INCLUDE[ssSDS](../../includes/sssds-md.md)]に接続するたびに資格情報 (ログインとパスワード) を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83930-126">supports only SQL Server Authentication (user name and password) and users must provide credentials (login and password) every time they connect to [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>

 <span data-ttu-id="83930-127">データベースにアクセスするには、十分な資格情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="83930-127">Credentials must be sufficient to access the database.</span></span> <span data-ttu-id="83930-128">クエリによっては、他の権限 (ストアド プロシージャを実行したり、テーブルやビューにアクセスしたりするために必要な権限) が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="83930-128">Depending on your query, you might need other permissions, such as sufficient permissions to run stored procedures and access tables and views.</span></span> <span data-ttu-id="83930-129">外部データ ソースの所有者は、十分な資格情報を構成して、ユーザーが必要とするデータベース オブジェクトに対する読み取り専用アクセスを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83930-129">The owner of the external data source must configure credentials that are sufficient to provide read-only access to the database objects that you need.</span></span>

 <span data-ttu-id="83930-130">レポート作成クライアントから、次のオプションを使用して資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="83930-130">From a report authoring client, the following options are available to specify credentials:</span></span>

-   <span data-ttu-id="83930-131">保存されているユーザー名とパスワードを使用する。</span><span class="sxs-lookup"><span data-stu-id="83930-131">Use a stored user name and password.</span></span> <span data-ttu-id="83930-132">レポート データを格納するデータベースがレポート サーバーとは別のサーバーに存在する場合に発生するダブル ホップに対処するには、資格情報を Windows 資格情報として使用するオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="83930-132">To negotiate the double hop that occurs when the database that contains the report data is different than the report server, select options to use credentials as Windows credentials.</span></span> <span data-ttu-id="83930-133">データ ソースに接続した後に、認証されているユーザーの権限を借用するオプションもあります。</span><span class="sxs-lookup"><span data-stu-id="83930-133">You can also chose to impersonate the authenticated user after connecting to the data source.</span></span>

-   <span data-ttu-id="83930-134">資格情報を必要としない。</span><span class="sxs-lookup"><span data-stu-id="83930-134">No credentials are required.</span></span> <span data-ttu-id="83930-135">このオプションを使用するには、レポート サーバーで自動実行アカウントを構成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="83930-135">To use this option, you must have the unattended execution account configured on the report server.</span></span> <span data-ttu-id="83930-136">詳細については、msdn.microsoft.com で [Reporting Services に関するドキュメント](https://go.microsoft.com/fwlink/?linkid=121312)の「[自動実行アカウントの構成 &#40;SSRS 構成マネージャー&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83930-136">For more information, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in on msdn.microsoft.com.</span></span>

 <span data-ttu-id="83930-137">詳細については、「 [Reporting Services のデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)」または「[レポートビルダーで資格情報を指定する](../specify-credentials-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83930-137">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>

 

##  <a name="queries"></a><a name="Query"></a><span data-ttu-id="83930-138">問い合わせ</span><span class="sxs-lookup"><span data-stu-id="83930-138">Queries</span></span>
 <span data-ttu-id="83930-139">クエリでは、レポート データセット用に取得するデータを指定します。</span><span class="sxs-lookup"><span data-stu-id="83930-139">A query specifies which data to retrieve for a report dataset.</span></span> <span data-ttu-id="83930-140">クエリの結果セットの列には、データセットのフィールド コレクションが設定されます。</span><span class="sxs-lookup"><span data-stu-id="83930-140">The columns in the result set for a query populate the field collection for a dataset.</span></span> <span data-ttu-id="83930-141">クエリで複数の結果セットが返された場合にレポートによって処理されるのは、クエリから取得された最初の結果セットだけです。</span><span class="sxs-lookup"><span data-stu-id="83930-141">If the query returns multiple result sets, the report processes only the first result set that the query retrieves.</span></span> <span data-ttu-id="83930-142">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と [!INCLUDE[ssSDS](../../includes/sssds-md.md)]の間には、サポートされるデータベースのサイズなど、いくつか違いがありますが、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]に対するクエリの作成方法と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに対するクエリの作成方法はほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="83930-142">Although there are some differences between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssSDS](../../includes/sssds-md.md)]s such as the sizes of databases supported, writing queries against [!INCLUDE[ssSDS](../../includes/sssds-md.md)]s is similar to writing queries against [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span> <span data-ttu-id="83930-143">[!INCLUDE[tsql](../../includes/tsql-md.md)] では、BACKUP などの一部の [!INCLUDE[ssSDS](../../includes/sssds-md.md)]ステートメントがサポートされていませんが、これらはレポート クエリで使用するステートメントではありません。</span><span class="sxs-lookup"><span data-stu-id="83930-143">Some [!INCLUDE[tsql](../../includes/tsql-md.md)] statements such as BACKUP are not supported in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], but they are not ones that you use in report queries.</span></span> <span data-ttu-id="83930-144">詳細については、「[SQL Server の接続の種類 (SSRS)](sql-server-connection-type-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83930-144">For more information, see [SQL Server Connection Type &#40;SSRS&#41;](sql-server-connection-type-ssrs.md).</span></span>

 <span data-ttu-id="83930-145">新しいクエリを作成するか、グラフィカル クエリ デザイナーで表示できる既存のクエリを開く場合、既定でリレーショナル クエリ デザイナーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="83930-145">By default, if you create a new query or open an existing query that can be represented in the graphical query designer, the relational query designer is available.</span></span> <span data-ttu-id="83930-146">クエリは、次の方法で指定できます。</span><span class="sxs-lookup"><span data-stu-id="83930-146">You can specify a query in the following ways:</span></span>

-   <span data-ttu-id="83930-147">クエリを対話形式で作成します。</span><span class="sxs-lookup"><span data-stu-id="83930-147">Build a query interactively.</span></span> <span data-ttu-id="83930-148">データベース スキーマ別に編成された、テーブル、ビュー、ストアド プロシージャ、およびその他のデータベース アイテムの階層ビューが表示されるリレーショナル クエリ デザイナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="83930-148">Use the relational query designer that displays a hierarchical view of tables, views, stored procedures, and other database items, organized by database schema.</span></span> <span data-ttu-id="83930-149">テーブルまたはビューから列を選択するか、ストアド プロシージャまたはテーブル値関数を指定します。</span><span class="sxs-lookup"><span data-stu-id="83930-149">Select columns from tables or views, or specify stored procedures or table-valued functions.</span></span> <span data-ttu-id="83930-150">フィルター条件を指定して、取得するデータの行数を制限します。</span><span class="sxs-lookup"><span data-stu-id="83930-150">Limit the number of rows of data to retrieve by specifying filter criteria.</span></span> <span data-ttu-id="83930-151">パラメーター オプションを設定してレポートの実行時にフィルターをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="83930-151">Customize the filter when the report runs by setting the parameter option.</span></span>

-   <span data-ttu-id="83930-152">クエリを入力するか、貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="83930-152">Type or paste a query.</span></span> <span data-ttu-id="83930-153">テキスト ベースのクエリ デザイナーは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] テキストを直接入力する、クエリ テキストを別のソースから貼り付ける、リレーショナル クエリ デザイナーでは作成できない複雑なクエリを入力する、クエリ ベースの式を入力する、などの場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="83930-153">Use the text-based query designer to enter [!INCLUDE[tsql](../../includes/tsql-md.md)] text directly, to paste query text from another source, to enter complex queries that cannot be built by using the relational query designer, or to enter query-based expressions.</span></span>

-   <span data-ttu-id="83930-154">ファイルまたはレポートから既存のクエリをインポートします。</span><span class="sxs-lookup"><span data-stu-id="83930-154">Import an existing query from a file or report.</span></span> <span data-ttu-id="83930-155">クエリ デザイナーの **[クエリのインポート]** ボタンを使用して、.sql ファイルまたは .rdl ファイルを参照し、クエリをインポートします。</span><span class="sxs-lookup"><span data-stu-id="83930-155">Use the **Import** query button from either query designer to browse to a .sql file or .rdl file and import a query.</span></span>

 <span data-ttu-id="83930-156">テキスト ベースのクエリ デザイナーでは、次の 2 つのモードがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="83930-156">The text-based query designer supports the following two modes:</span></span>

-   <span data-ttu-id="83930-157">[テキスト](#QueryText) : データ ソースからデータを選択する [!INCLUDE[tsql](../../includes/tsql-md.md)] コマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="83930-157">[Text](#QueryText) Type [!INCLUDE[tsql](../../includes/tsql-md.md)] commands that select data from the data source.</span></span>

-   <span data-ttu-id="83930-158">[ストアド プロシージャ](#QueryStoredProcedure) : ストアド プロシージャの一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="83930-158">[Stored Procedure](#QueryStoredProcedure) Choose from a list of stored procedures.</span></span>

 <span data-ttu-id="83930-159">詳細については、「[リレーショナル クエリ デザイナーのユーザー インターフェイス &#40;レポート ビルダー&#41;](relational-query-designer-user-interface-report-builder.md)」および「[テキストベースのクエリ デザイナーのユーザー インターフェイス &#40;レポート ビルダー&#41;](text-based-query-designer-user-interface-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83930-159">For more information, see [Relational Query Designer User Interface &#40;Report Builder&#41;](relational-query-designer-user-interface-report-builder.md) and [Text-based Query Designer User Interface &#40;Report Builder&#41;](text-based-query-designer-user-interface-report-builder.md).</span></span>

 <span data-ttu-id="83930-160">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] で使用されるグラフィカル クエリ デザイナーには、要約データのみを取得するクエリの作成に役立つグループ化と集計のサポートが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="83930-160">The graphical query designer that [!INCLUDE[ssSDS](../../includes/sssds-md.md)] uses provides built-in support for grouping and aggregates to help you write queries that retrieve only summary data.</span></span> <span data-ttu-id="83930-161">[!INCLUDE[tsql](../../includes/tsql-md.md)] 言語の機能には、GROUP BY 句、DISTINCT キーワード、および集計 (SUM、COUNT など) があります。</span><span class="sxs-lookup"><span data-stu-id="83930-161">The [!INCLUDE[tsql](../../includes/tsql-md.md)] language features are: the GROUP BY clause, DISTINCT keyword, and aggregates such as SUM and COUNT.</span></span> <span data-ttu-id="83930-162">テキスト ベースのクエリ デザイナーでは、グループ化と集計が含まれている [!INCLUDE[tsql](../../includes/tsql-md.md)] 言語が完全にサポートされています。</span><span class="sxs-lookup"><span data-stu-id="83930-162">The text-based query designer provides full support for the [!INCLUDE[tsql](../../includes/tsql-md.md)] language, including grouping and aggregates.</span></span> <span data-ttu-id="83930-163">[!INCLUDE[tsql](../../includes/tsql-md.md)] の詳細については、msdn.microsoft.com の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブック](https://go.microsoft.com/fwlink/?LinkId=141687)にある「[Transact-SQL リファレンス (データベース エンジン)](/sql/t-sql/language-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83930-163">For more information about [!INCLUDE[tsql](../../includes/tsql-md.md)], see [Transact-SQL Reference &#40;Database Engine&#41;](/sql/t-sql/language-reference)in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=141687) on msdn.microsoft.com.</span></span>

###  <a name="using-query-type-text"></a><a name="QueryText"></a> <span data-ttu-id="83930-164">Text の種類のクエリの使用</span><span class="sxs-lookup"><span data-stu-id="83930-164">Using Query Type Text</span></span>
 <span data-ttu-id="83930-165">テキスト ベースのクエリ デザイナーでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] コマンドを入力して、データセット内のデータを定義します。</span><span class="sxs-lookup"><span data-stu-id="83930-165">In the text-based query designer, you type [!INCLUDE[tsql](../../includes/tsql-md.md)] commands to define the data in a dataset.</span></span> <span data-ttu-id="83930-166">たとえば、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリでは、マーケティング アシスタントであるすべての従業員の名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="83930-166">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] query selects the names of all employees who are marketing assistants:</span></span>

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

 <span data-ttu-id="83930-167">ツール バーの **[実行]** ボタン (**!**) をクリックすると、クエリが実行され、結果セットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83930-167">Click the **Run** button (**!**) on the toolbar to run the query and display a result set.</span></span>

 <span data-ttu-id="83930-168">このクエリをパラメーター化するには、クエリ パラメーターを追加します。</span><span class="sxs-lookup"><span data-stu-id="83930-168">To parameterize this query, add a query parameter.</span></span> <span data-ttu-id="83930-169">たとえば、WHERE 句を次の構文に変更します。</span><span class="sxs-lookup"><span data-stu-id="83930-169">For example, change the WHERE clause to the following:</span></span>

```
WHERE HumanResources.Employee.JobTitle = (@JobTitle)
```

 <span data-ttu-id="83930-170">クエリの実行時に、クエリ パラメーターに対応するレポート パラメーターが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="83930-170">When you run the query, report parameters that correspond to query parameters are automatically created.</span></span> <span data-ttu-id="83930-171">詳細については、このトピックの「 [クエリ パラメーター](#Parameters) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83930-171">For more information, see [Query Parameters](#Parameters) later in this topic.</span></span>



###  <a name="using-query-type-storedprocedure"></a><a name="QueryStoredProcedure"></a><span data-ttu-id="83930-172">クエリ型 StoredProcedure の使用</span><span class="sxs-lookup"><span data-stu-id="83930-172">Using Query Type StoredProcedure</span></span>
 <span data-ttu-id="83930-173">データセット クエリのストアド プロシージャは、次のいずれかの方法で指定できます。</span><span class="sxs-lookup"><span data-stu-id="83930-173">You can specify a stored procedure for a dataset query in one of the following ways:</span></span>

-   <span data-ttu-id="83930-174">**[データセットのプロパティ]** ダイアログ ボックスで、 **[ストアド プロシージャ]** オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="83930-174">In the **Dataset Properties** dialog box, set the **Stored Procedure** option.</span></span> <span data-ttu-id="83930-175">ドロップダウン リストからストアド プロシージャまたはテーブル値関数を選択します。</span><span class="sxs-lookup"><span data-stu-id="83930-175">Choose from the drop-down list of stored procedures and table-valued functions.</span></span>

-   <span data-ttu-id="83930-176">リレーショナル クエリ デザイナーのデータベース ビュー ペインで、ストアド プロシージャまたはテーブル値関数を選択します。</span><span class="sxs-lookup"><span data-stu-id="83930-176">In the relational query designer, in the Database view pane, select a stored procedure or table-valued function.</span></span>

-   <span data-ttu-id="83930-177">テキスト ベースのクエリ デザイナーで、ツール バーから **[StoredProcedure]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="83930-177">In the text-based query designer, select **StoredProcedure** from the toolbar.</span></span>

 <span data-ttu-id="83930-178">ストアド プロシージャまたはテーブル値関数を選択したら、クエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="83930-178">After you select a stored procedure or table-valued function, you can run the query.</span></span> <span data-ttu-id="83930-179">入力パラメーター値の入力を要求されます。</span><span class="sxs-lookup"><span data-stu-id="83930-179">You will be prompted for input parameter values.</span></span> <span data-ttu-id="83930-180">クエリの実行時に、入力パラメーターに対応するレポート パラメーターが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="83930-180">When you run the query, report parameters that correspond to input parameters are automatically created.</span></span> <span data-ttu-id="83930-181">詳細については、このトピックの「 [クエリ パラメーター](#Parameters) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83930-181">For more information, see [Query Parameters](#Parameters) later in this topic.</span></span>

 <span data-ttu-id="83930-182">ストアド プロシージャから取得した最初の結果セットだけがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="83930-182">Only the first result set that is retrieved for a stored procedure is supported.</span></span> <span data-ttu-id="83930-183">ストアド プロシージャから複数の結果セットが返された場合、最初の結果セットだけが使用されます。</span><span class="sxs-lookup"><span data-stu-id="83930-183">If a stored procedure returns multiple result sets, only the first one is used.</span></span>

 <span data-ttu-id="83930-184">既定値が指定されたパラメーターがストアド プロシージャに含まれている場合、パラメーターの値として DEFAULT キーワードを使用してその値にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="83930-184">If a stored procedure has a parameter that has a default value, you can access that value by using the DEFAULT keyword as a value for the parameter.</span></span> <span data-ttu-id="83930-185">クエリ パラメーターがレポート パラメーターにリンクされている場合は、レポート パラメーターの入力ボックスで DEFAULT キーワードを入力または選択できます。</span><span class="sxs-lookup"><span data-stu-id="83930-185">If the query parameter is linked to a report parameter, the user can type or select the word DEFAULT in the input box for the report parameter.</span></span>

 <span data-ttu-id="83930-186">ストアド プロシージャの詳細については、msdn.microsoft.com にある [SQL Server オンライン ブック](https://go.microsoft.com/fwlink/?linkid=98335) の「ストアド プロシージャ (データベース エンジン)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83930-186">For more information about stored procedures, see "Stored Procedures (Database Engine)" in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=98335) on msdn.microsoft.com.</span></span>



##  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="83930-187">パラメーター</span><span class="sxs-lookup"><span data-stu-id="83930-187">Parameters</span></span>
 <span data-ttu-id="83930-188">入力パラメーターを含むクエリ変数またはストアド プロシージャがクエリ テキストに含まれている場合、対応するデータセットのクエリ パラメーターとレポートのレポート パラメーターが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="83930-188">When query text contains query variables or stored procedures that have input parameters, the corresponding query parameters for the dataset and report parameters for the report are automatically generated.</span></span> <span data-ttu-id="83930-189">クエリ テキストには、各クエリ変数の DECLARE ステートメントを含めないでください。</span><span class="sxs-lookup"><span data-stu-id="83930-189">The query text must not include the DECLARE statement for each query variable.</span></span>

 <span data-ttu-id="83930-190">たとえば、次の SQL クエリでは、`EmpID` という名前のレポート パラメーターが作成されます。</span><span class="sxs-lookup"><span data-stu-id="83930-190">For example, the following SQL query creates a report parameter named `EmpID`:</span></span>

```
SELECT FirstName, LastName FROM HumanResources.Employee E INNER JOIN
       Person.Contact C ON  E.ContactID=C.ContactID 
WHERE EmployeeID = (@EmpID)
```

 <span data-ttu-id="83930-191">レポート パラメーターの既定のデータ型は Text です。各レポート パラメーターには自動的に作成されたデータセットが設定され、使用可能な値のドロップダウン リストで使用されます。</span><span class="sxs-lookup"><span data-stu-id="83930-191">By default, each report parameter has data type Text and an automatically created dataset to provide a drop-down list of available values.</span></span> <span data-ttu-id="83930-192">レポート パラメーターを作成した後に、既定値の変更が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="83930-192">After the report parameters are created, you might have to change default values.</span></span> <span data-ttu-id="83930-193">詳細については、「 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../report-design/report-parameters-report-builder-and-report-designer.md)にあります。</span><span class="sxs-lookup"><span data-stu-id="83930-193">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>



##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="83930-194">解説</span><span class="sxs-lookup"><span data-stu-id="83930-194">Remarks</span></span>

###### <a name="alternate-data-extensions"></a><span data-ttu-id="83930-195">代替データ拡張機能</span><span class="sxs-lookup"><span data-stu-id="83930-195">Alternate Data Extensions</span></span>
 <span data-ttu-id="83930-196">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースからのデータの取得は、ODBC のデータ ソースの種類を使用して行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="83930-196">You can also retrieve data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database by using an ODBC data source type.</span></span> <span data-ttu-id="83930-197">OLE DB を使用した [!INCLUDE[ssSDS](../../includes/sssds-md.md)] への接続はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="83930-197">Connecting to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] by using OLE DB is not supported.</span></span>

 <span data-ttu-id="83930-198">詳細については、「[ODBC 接続の種類 &#40;SSRS&#41;](odbc-connection-type-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83930-198">For more information, see [ODBC Connection Type &#40;SSRS&#41;](odbc-connection-type-ssrs.md).</span></span>

###### <a name="platform-and-version-information"></a><span data-ttu-id="83930-199">プラットフォームおよびバージョン情報</span><span class="sxs-lookup"><span data-stu-id="83930-199">Platform and Version Information</span></span>
 <span data-ttu-id="83930-200">プラットフォームおよびバージョン サポートの詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブック](https://go.microsoft.com/fwlink/?linkid=121312)にある [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ドキュメントの「[Reporting Services でサポートされるデータ ソース (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83930-200">For more information about platform and version support, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>



##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="83930-201">操作方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="83930-201">How-To Topics</span></span>
 <span data-ttu-id="83930-202">データ接続、データ ソース、およびデータセットを操作する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="83930-202">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>

 [<span data-ttu-id="83930-203">データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;に追加して検証する</span><span class="sxs-lookup"><span data-stu-id="83930-203">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)

 [<span data-ttu-id="83930-204">共有データセットまたは埋め込みデータセットの作成 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="83930-204">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)

 [<span data-ttu-id="83930-205">データセットへのフィルターの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="83930-205">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)



##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="83930-206">関連セクション</span><span class="sxs-lookup"><span data-stu-id="83930-206">Related Sections</span></span>
 <span data-ttu-id="83930-207">次に示すセクションでは、レポート データの概念が詳細に説明されているほか、データに関連するレポートのパーツを定義しカスタマイズし使用する手順が説明されています。</span><span class="sxs-lookup"><span data-stu-id="83930-207">These sections of the documentation provide in-depth conceptual information about report data, and procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>

 <span data-ttu-id="83930-208">[レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-datasets-ssrs.md)レポートのデータへのアクセスの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="83930-208">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) Provides an overview of accessing data for your report.</span></span>

 <span data-ttu-id="83930-209">[レポートビルダーのデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)データ接続とデータソースに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="83930-209">[Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md) Provides information about data connections and data sources.</span></span>

 <span data-ttu-id="83930-210">[レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)埋め込みデータセットと共有データセットに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="83930-210">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) Provides information about embedded and shared datasets.</span></span>

 <span data-ttu-id="83930-211">[データセットフィールドコレクション &#40;レポートビルダーと SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)クエリによって生成されるデータセットフィールドコレクションに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="83930-211">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) Provides information about the dataset field collection generated by the query.</span></span>

 <span data-ttu-id="83930-212">[Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブックの [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ドキュメント](https://go.microsoft.com/fwlink/?linkid=121312))。</span><span class="sxs-lookup"><span data-stu-id="83930-212">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>
<span data-ttu-id="83930-213">各データ拡張機能のプラットフォームおよびバージョン サポートに関する詳細な情報です。</span><span class="sxs-lookup"><span data-stu-id="83930-213">Provides in-depth information about platform and version support for each data extension.</span></span>



## <a name="see-also"></a><span data-ttu-id="83930-214">参照</span><span class="sxs-lookup"><span data-stu-id="83930-214">See Also</span></span>
 <span data-ttu-id="83930-215">[レポートパラメーター &#40;レポートビルダーとレポートデザイナー](../report-design/report-parameters-report-builder-and-report-designer.md) [データのフィルター処理、グループ化、並べ替え&#41;&#40;と ssrs レポートビルダー](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) [式&#41;&#40;と ssrs レポートビルダー](../report-design/expressions-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="83930-215">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) [Expressions &#40;Report Builder and SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)</span></span>


