---
title: テキストベースのクエリデザイナーのユーザーインターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10010"
- sql12.rtp.rptdesigner.dataview.genericquerydesigner.f1
helpviewer_keywords:
- text-based query designer [Reporting Services]
- query designers [Reporting Services], text-based
ms.assetid: 44b7c664-03aa-494e-a484-052b318e810c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1647d69246ba85dfbe0718799441c3687c0beca3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739073"
---
# <a name="text-based-query-designer-user-interface"></a><span data-ttu-id="f4922-102">テキストベースのクエリ デザイナーのユーザー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4922-102">Text-based Query Designer User Interface</span></span>
  <span data-ttu-id="f4922-103">デザイン時に、データ ソースでサポートされているクエリ言語でクエリを指定し、クエリを実行し、結果を表示するには、テキスト ベースのクエリ デザイナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="f4922-103">Use the text-based query designer to specify a query using the query language supported by the data source, run the query, and view the results at design time.</span></span> <span data-ttu-id="f4922-104">複数の [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメント、カスタム データ処理拡張機能のクエリまたはコマンド構文、および式としてのクエリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f4922-104">You can specify multiple [!INCLUDE[tsql](../includes/tsql-md.md)] statements, query or command syntax for custom data processing extensions, and queries that are specified as expressions.</span></span> <span data-ttu-id="f4922-105">テキスト ベースのクエリ デザイナーはクエリを前処理せず、あらゆる種類のクエリ構文に対応できるため、これは多くの種類のデータ ソースで既定のクエリ デザイナー ツールになっています。</span><span class="sxs-lookup"><span data-stu-id="f4922-105">Because the text-based query designer does not preprocess the query and can accommodate any kind of query syntax, this is the default query designer tool for many data source types.</span></span>

 <span data-ttu-id="f4922-106">テキスト ベースのクエリ デザイナーでは、ツール バーと次の 2 つのペインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4922-106">The text-based query designer displays a toolbar and the following two panes:</span></span>

-   <span data-ttu-id="f4922-107">**クエリ**クエリテキスト、テーブル名、またはストアドプロシージャ名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4922-107">**Query** Shows the query text, table name, or stored procedure name.</span></span>

-   <span data-ttu-id="f4922-108">**[結果]** デザイン時にクエリの実行結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4922-108">**Result** Shows the results of running the query at design time.</span></span>

## <a name="text-based-query-designer-toolbar"></a><span data-ttu-id="f4922-109">テキスト ベースのクエリ デザイナーのツール バー</span><span class="sxs-lookup"><span data-stu-id="f4922-109">Text-based Query Designer Toolbar</span></span>
 <span data-ttu-id="f4922-110">テキスト ベースのクエリ デザイナーで使用できるツール バーは、コマンドの種類に関係なく 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="f4922-110">The text-based query designer provides a single toolbar for all the command types.</span></span> <span data-ttu-id="f4922-111">次の表は、ツール バーの各ボタンとその機能を示しています。</span><span class="sxs-lookup"><span data-stu-id="f4922-111">The following table lists each button on the toolbar and its function.</span></span>

|<span data-ttu-id="f4922-112">Button</span><span class="sxs-lookup"><span data-stu-id="f4922-112">Button</span></span>|<span data-ttu-id="f4922-113">説明</span><span class="sxs-lookup"><span data-stu-id="f4922-113">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="f4922-114">**[テキストとして編集]**</span><span class="sxs-lookup"><span data-stu-id="f4922-114">**Edit As Text**</span></span>|<span data-ttu-id="f4922-115">テキスト ベースのクエリ デザイナーと、グラフィカル クエリ デザイナー間で切り替えます。</span><span class="sxs-lookup"><span data-stu-id="f4922-115">Toggle between the text-based query designer and the graphical query designer.</span></span> <span data-ttu-id="f4922-116">すべての種類のデータ ソースでグラフィカル クエリ デザイナーがサポートされているとは限りません。</span><span class="sxs-lookup"><span data-stu-id="f4922-116">Not all data source types support graphical query designers.</span></span>|
|<span data-ttu-id="f4922-117">**[インポート]**</span><span class="sxs-lookup"><span data-stu-id="f4922-117">**Import**</span></span>|<span data-ttu-id="f4922-118">ファイルまたはレポートから既存のクエリをインポートします。</span><span class="sxs-lookup"><span data-stu-id="f4922-118">Import an existing query from a file or report.</span></span> <span data-ttu-id="f4922-119">サポートされているファイルの種類は sql と rdl だけです。</span><span class="sxs-lookup"><span data-stu-id="f4922-119">Only file types sql and rdl are supported.</span></span> <span data-ttu-id="f4922-120">詳細については、「 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="f4922-120">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>|
|<span data-ttu-id="f4922-121">![クエリを実行する](../analysis-services/media/rsqdicon-run.gif "クエリを実行する")</span><span class="sxs-lookup"><span data-stu-id="f4922-121">![Run the query](../analysis-services/media/rsqdicon-run.gif "Run the query")</span></span>|<span data-ttu-id="f4922-122">クエリを実行し、その結果セットを結果ペインに表示します。</span><span class="sxs-lookup"><span data-stu-id="f4922-122">Run the query and display the result set in the Result pane.</span></span>|
|<span data-ttu-id="f4922-123">**[コマンドの種類]**</span><span class="sxs-lookup"><span data-stu-id="f4922-123">**Command Type**</span></span>|<span data-ttu-id="f4922-124">**[Text]** 、 **[StoredProcedure]** 、または **[TableDirect]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f4922-124">Select **Text**, **StoredProcedure**, or **TableDirect**.</span></span> <span data-ttu-id="f4922-125">パラメーターを受け取るストアド プロシージャの場合、ツール バーの **[実行]** をクリックすると、 **[クエリ パラメーターの定義]** ダイアログ ボックスが表示され、必要な値を入力できます。</span><span class="sxs-lookup"><span data-stu-id="f4922-125">If a stored procedure has parameters, the **Define Query Parameters** dialog box appears when you click **Run** on the toolbar, and you can fill in values as needed.</span></span> <span data-ttu-id="f4922-126">ストアドプロシージャから複数の結果セットが返された場合は、最初の結果セットのみを使用してデータセットが設定されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f4922-126">Note that if a stored procedure returns more than one result set, only the first result set is used to populate the dataset.</span></span><br /><br /> <span data-ttu-id="f4922-127">サポートされるコマンドの種類は、データ ソースの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="f4922-127">Support for command type varies by data source type.</span></span> <span data-ttu-id="f4922-128">たとえば、 **[TableDirect]** がサポートされるのは、OLE DB と ODBC だけです。</span><span class="sxs-lookup"><span data-stu-id="f4922-128">For example, only OLE DB and ODBC support **TableDirect**.</span></span>|

### <a name="command-type-text"></a><span data-ttu-id="f4922-129">コマンドの種類 (Text)</span><span class="sxs-lookup"><span data-stu-id="f4922-129">Command Type Text</span></span>
 <span data-ttu-id="f4922-130">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データセットを作成するとき、レポート デザイナーには既定によりグラフィカル クエリ デザイナーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4922-130">When you create a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dataset, Report Designer displays the graphical query designer by default.</span></span> <span data-ttu-id="f4922-131">テキスト ベースのクエリ デザイナーに切り替えるには、ツール バーの **[テキストとして編集]** 切り替えボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f4922-131">To switch to the text-based query designer, click the **Edit As Text** toggle button on the toolbar.</span></span> <span data-ttu-id="f4922-132">テキスト ベースのクエリ デザイナーは、クエリ ペインと結果ペインの 2 つのペインで構成されています。</span><span class="sxs-lookup"><span data-stu-id="f4922-132">The text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="f4922-133">次の図に各ペインの名称を示します。</span><span class="sxs-lookup"><span data-stu-id="f4922-133">The following figure labels each pane.</span></span>

 <span data-ttu-id="f4922-134">![リレーショナル データのクエリに使用する汎用クエリ デザイナー](../analysis-services/media/rsqd-dsaw-sql-generic.gif "リレーショナル データのクエリに使用する汎用クエリ デザイナー")</span><span class="sxs-lookup"><span data-stu-id="f4922-134">![Generic query designer, for relational data query](../analysis-services/media/rsqd-dsaw-sql-generic.gif "Generic query designer, for relational data query")</span></span>

 <span data-ttu-id="f4922-135">次の表に各ペインの機能を示します。</span><span class="sxs-lookup"><span data-stu-id="f4922-135">The following table describes the function of each pane.</span></span>

|<span data-ttu-id="f4922-136">ペイン</span><span class="sxs-lookup"><span data-stu-id="f4922-136">Pane</span></span>|<span data-ttu-id="f4922-137">機能</span><span class="sxs-lookup"><span data-stu-id="f4922-137">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="f4922-138">クエリ</span><span class="sxs-lookup"><span data-stu-id="f4922-138">Query</span></span>|<span data-ttu-id="f4922-139">[!INCLUDE[tsql](../includes/tsql-md.md)] クエリ テキストを表示します。</span><span class="sxs-lookup"><span data-stu-id="f4922-139">Displays the [!INCLUDE[tsql](../includes/tsql-md.md)] query text.</span></span> <span data-ttu-id="f4922-140">[!INCLUDE[tsql](../includes/tsql-md.md)] クエリを記述または編集する際に、このペインを使用します。</span><span class="sxs-lookup"><span data-stu-id="f4922-140">Use this pane to write or edit a [!INCLUDE[tsql](../includes/tsql-md.md)] query.</span></span>|
|<span data-ttu-id="f4922-141">結果</span><span class="sxs-lookup"><span data-stu-id="f4922-141">Result</span></span>|<span data-ttu-id="f4922-142">クエリの結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="f4922-142">Displays the results of the query.</span></span> <span data-ttu-id="f4922-143">クエリを実行するには、任意のペインで右クリックして、 **[実行]** をクリックするか、ツール バーの **[実行]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f4922-143">To run the query, right-click in any pane and click **Run**, or click the **Run** button on the toolbar.</span></span>|

#### <a name="example"></a><span data-ttu-id="f4922-144">例</span><span class="sxs-lookup"><span data-stu-id="f4922-144">Example</span></span>
 <span data-ttu-id="f4922-145">次のクエリは、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベースの `Contact` テーブルから姓の一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="f4922-145">The following query returns the list of last names from the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database `Contact` table.</span></span>

```
SELECT LastName FROM Person.Person;
```

 <span data-ttu-id="f4922-146">`EXEC` ステートメントを含むコマンドの種類 (Text) のすべての [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f4922-146">You can use any [!INCLUDE[tsql](../includes/tsql-md.md)] statement for Command type Text, including `EXEC` statements.</span></span> <span data-ttu-id="f4922-147">次のクエリでは、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] のストアド プロシージャである `uspGetEmployeeManagers` を呼び出して、識別番号が 1 である従業員の指揮系統を取得しています。</span><span class="sxs-lookup"><span data-stu-id="f4922-147">The following query calls the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] stored procedure `uspGetEmployeeManagers` and returns the chain-of-command for the employee with identification number 1.</span></span>

```
EXEC uspGetEmployeeManagers 1;
```

 <span data-ttu-id="f4922-148">ツール バーの **[実行]** をクリックすると、 **クエリ** ペインのコマンドが実行され、その結果が **結果** ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4922-148">When you click **Run** on the toolbar, the command in the **Query** pane runs and the results are displayed in the **Result** pane.</span></span>

### <a name="command-type-storedprocedure"></a><span data-ttu-id="f4922-149">コマンドの種類 (StoredProcedure)</span><span class="sxs-lookup"><span data-stu-id="f4922-149">Command Type StoredProcedure</span></span>
 <span data-ttu-id="f4922-150">**[コマンドの種類] で [StoredProcedure]** を選択した場合、テキスト ベースのクエリ デザイナーには、クエリ ペインと結果ペインの 2 つのペインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4922-150">When you select **Command typeStoredProcedure**, the text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="f4922-151">ストアド プロシージャ名をクエリ ペインに入力し、ツール バーの **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f4922-151">Enter the stored procedure name in the Query pane and click **Run** on the toolbar.</span></span> <span data-ttu-id="f4922-152">[クエリ パラメーターの定義] ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4922-152">The Define Query Parameters dialog box opens.</span></span> <span data-ttu-id="f4922-153">ストアド プロシージャのパラメーター値を入力します。</span><span class="sxs-lookup"><span data-stu-id="f4922-153">Enter the parameter values for the stored procedure.</span></span> <span data-ttu-id="f4922-154">すべてのストアド プロシージャ パラメーターについて、レポート パラメーターが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f4922-154">A report parameter is created for every stored procedure parameter.</span></span>

#### <a name="example"></a><span data-ttu-id="f4922-155">例</span><span class="sxs-lookup"><span data-stu-id="f4922-155">Example</span></span>
 <span data-ttu-id="f4922-156">次のクエリでは、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] ストアド プロシージャである `uspGetEmployeeManagers` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f4922-156">The following query calls the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] stored procedure `uspGetEmployeeManagers`.</span></span> <span data-ttu-id="f4922-157">クエリを実行する場合は、従業員 ID 番号パラメーターの値を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4922-157">You must enter a value for the employee identification number parameter when you run the query.</span></span>

```
uspGetEmployeeManagers;
```

### <a name="command-type-tabledirect"></a><span data-ttu-id="f4922-158">コマンドの種類 (TableDirect)</span><span class="sxs-lookup"><span data-stu-id="f4922-158">Command Type TableDirect</span></span>
 <span data-ttu-id="f4922-159">**[コマンドの種類] で [TableDirect]** を選択した場合、テキスト ベースのクエリ デザイナーには、クエリ ペインと結果ペインの 2 つのペインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4922-159">When you select **Command typeTableDirect**, the text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="f4922-160">テーブルを入力し、 **[実行]** ボタンをクリックすると、そのテーブルのすべての列が返されます。</span><span class="sxs-lookup"><span data-stu-id="f4922-160">When you enter a table and click the **Run** button, all the columns for that table are returned.</span></span>

#### <a name="example"></a><span data-ttu-id="f4922-161">例</span><span class="sxs-lookup"><span data-stu-id="f4922-161">Example</span></span>
 <span data-ttu-id="f4922-162">次のクエリでは、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベースのすべての顧客を結果セットとして取得しています。</span><span class="sxs-lookup"><span data-stu-id="f4922-162">The following query returns a result set for all customers in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span>

 `Sales.Customer`

 <span data-ttu-id="f4922-163">テーブル名として「Sales. Customer」と入力すると、ステートメントの作成に相当します。 [!INCLUDE[tsql](../includes/tsql-md.md)] `SELECT * FROM Sales.Customer;`</span><span class="sxs-lookup"><span data-stu-id="f4922-163">When you enter the table name Sales.Customer, it is the equivalent of creating the [!INCLUDE[tsql](../includes/tsql-md.md)] statement `SELECT * FROM Sales.Customer;`.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4922-164">参照</span><span class="sxs-lookup"><span data-stu-id="f4922-164">See Also</span></span>
 <span data-ttu-id="f4922-165">[レポートデザイナー &#40;SQL Server Data Tools のクエリデザインツール ssrs&#41;](report-data/query-design-tools-ssrs.md) [レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと Ssrs&#41;SQL Server 接続の](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)[種類](report-data/sql-server-connection-type-ssrs.md)&#40;ssrs&#41;[OLE DB 接続](report-data/ole-db-connection-type-ssrs.md)の[種類 &#40;Ssrs](report-data/odbc-connection-type-ssrs.md) [の&#41;レポート埋め込みデータセットと共有データセット &#40;&#41;と ssrs &#40;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [rsreportdesigner 構成ファイル](report-server/rsreportdesigner-configuration-file.md)</span><span class="sxs-lookup"><span data-stu-id="f4922-165">[Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;](report-data/query-design-tools-ssrs.md) [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [SQL Server Connection Type &#40;SSRS&#41;](report-data/sql-server-connection-type-ssrs.md) [OLE DB Connection Type &#40;SSRS&#41;](report-data/ole-db-connection-type-ssrs.md) [ODBC Connection Type &#40;SSRS&#41;](report-data/odbc-connection-type-ssrs.md) [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [RSReportDesigner Configuration File](report-server/rsreportdesigner-configuration-file.md)</span></span>


