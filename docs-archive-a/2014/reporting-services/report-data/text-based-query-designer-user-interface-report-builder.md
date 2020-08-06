---
title: テキストベースのクエリ デザイナーのユーザー インターフェイス (レポート ビルダー) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10010"
helpviewer_keywords:
- query designers, text-based
ms.assetid: 89fddca5-bd96-4128-9072-5348d1b6e02c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c1415bdfada46ac09c9ab04047d63484593933e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631569"
---
# <a name="text-based-query-designer-user-interface-report-builder"></a><span data-ttu-id="4ccc2-102">テキストベースのクエリ デザイナーのユーザー インターフェイス (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="4ccc2-102">Text-based Query Designer User Interface (Report Builder)</span></span>
  <span data-ttu-id="4ccc2-103">デザイン時に、データ ソースでサポートされているクエリ言語でクエリを指定し、クエリを実行し、結果を表示するには、テキスト ベースのクエリ デザイナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-103">Use the text-based query designer to specify a query using the query language supported by the data source, run the query, and view the results at design time.</span></span> <span data-ttu-id="4ccc2-104">複数の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメント、カスタム データ処理拡張機能のクエリまたはコマンド構文、および式としてのクエリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-104">You can specify multiple [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements, query or command syntax for custom data processing extensions, and queries that are specified as expressions.</span></span> <span data-ttu-id="4ccc2-105">テキスト ベースのクエリ デザイナーはクエリを前処理せず、あらゆる種類のクエリ構文に対応できるため、これは多くの種類のデータ ソースで既定のクエリ デザイナー ツールになっています。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-105">Because the text-based query designer does not preprocess the query and can accommodate any kind of query syntax, this is the default query designer tool for many data source types.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="4ccc2-106">ユーザーは、クエリを作成して実行する際にデータ ソースにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-106">Users access data sources when they create and run queries.</span></span> <span data-ttu-id="4ccc2-107">したがって、データ ソースに対する最小限の権限 (読み取り専用権限など) を付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-107">You should grant minimal permissions on the data sources, such as read-only permissions.</span></span>

 <span data-ttu-id="4ccc2-108">テキスト ベースのクエリ デザイナーでは、ツール バーと次の 2 つのペインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-108">The text-based query designer displays a toolbar and the following two panes:</span></span>

-   <span data-ttu-id="4ccc2-109">**[クエリ]** クエリの種類に応じて、クエリ テキスト、テーブル名、またはストアド プロシージャ名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-109">**Query** Shows the query text, table name, or stored procedure name depending on the query type.</span></span> <span data-ttu-id="4ccc2-110">すべての種類のデータ ソースですべての種類のクエリが使用できるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-110">Not all query types are available for all data source types.</span></span> <span data-ttu-id="4ccc2-111">たとえば、テーブル名はデータ ソースの種類が OLE DB の場合にのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-111">For example, table name is supported only for the data source type OLE DB.</span></span>

-   <span data-ttu-id="4ccc2-112">**[結果]** デザイン時にクエリの実行結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-112">**Result** Shows the results of running the query at design time.</span></span>

## <a name="text-based-query-designer-toolbar"></a><span data-ttu-id="4ccc2-113">テキスト ベースのクエリ デザイナーのツール バー</span><span class="sxs-lookup"><span data-stu-id="4ccc2-113">Text-based Query Designer Toolbar</span></span>
 <span data-ttu-id="4ccc2-114">テキスト ベースのクエリ デザイナーで使用できるツール バーは、コマンドの種類に関係なく 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-114">The text-based query designer provides a single toolbar for all the command types.</span></span> <span data-ttu-id="4ccc2-115">次の表は、ツール バーの各ボタンとその機能を示しています。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-115">The following table lists each button on the toolbar and its function.</span></span>

|<span data-ttu-id="4ccc2-116">Button</span><span class="sxs-lookup"><span data-stu-id="4ccc2-116">Button</span></span>|<span data-ttu-id="4ccc2-117">説明</span><span class="sxs-lookup"><span data-stu-id="4ccc2-117">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="4ccc2-118">**[テキストとして編集]**</span><span class="sxs-lookup"><span data-stu-id="4ccc2-118">**Edit As Text**</span></span>|<span data-ttu-id="4ccc2-119">テキスト ベースのクエリ デザイナーと、グラフィカル クエリ デザイナー間で切り替えます。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-119">Toggle between the text-based query designer and the graphical query designer.</span></span> <span data-ttu-id="4ccc2-120">すべての種類のデータ ソースでグラフィカル クエリ デザイナーがサポートされているとは限りません。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-120">Not all data source types support graphical query designers.</span></span>|
|<span data-ttu-id="4ccc2-121">**[インポート]**</span><span class="sxs-lookup"><span data-stu-id="4ccc2-121">**Import**</span></span>|<span data-ttu-id="4ccc2-122">ファイルまたはレポートから既存のクエリをインポートします。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-122">Import an existing query from a file or report.</span></span> <span data-ttu-id="4ccc2-123">サポートされているファイルの種類は sql と rdl だけです。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-123">Only file types sql and rdl are supported</span></span>|
|<span data-ttu-id="4ccc2-124">![クエリを実行する](../../analysis-services/media/rsqdicon-run.gif "クエリを実行する")</span><span class="sxs-lookup"><span data-stu-id="4ccc2-124">![Run the query](../../analysis-services/media/rsqdicon-run.gif "Run the query")</span></span>|<span data-ttu-id="4ccc2-125">クエリを実行し、その結果セットを結果ペインに表示します。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-125">Run the query and display the result set in the Result pane.</span></span>|
|<span data-ttu-id="4ccc2-126">**[コマンドの種類]**</span><span class="sxs-lookup"><span data-stu-id="4ccc2-126">**Command Type**</span></span>|<span data-ttu-id="4ccc2-127">**[Text]** 、 **[StoredProcedure]** 、または **[TableDirect]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-127">Select **Text**, **StoredProcedure**, or **TableDirect**.</span></span> <span data-ttu-id="4ccc2-128">パラメーターを受け取るストアド プロシージャの場合、ツール バーの **[実行]** をクリックすると、 **[クエリ パラメーターの定義]** ダイアログ ボックスが表示され、必要な値を入力できます。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-128">If a stored procedure has parameters, the **Define Query Parameters** dialog box appears when you click **Run** on the toolbar, and you can fill in values as needed.</span></span><br /><br /> <span data-ttu-id="4ccc2-129">注:ストアド プロシージャから複数の結果セットが返された場合、最初の結果セットのみを使ってデータセットが設定されます。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-129">Note: If a stored procedure returns more than one result set, only the first result set is used to populate the dataset.</span></span>|

### <a name="command-type-text"></a><span data-ttu-id="4ccc2-130">コマンドの種類 (Text)</span><span class="sxs-lookup"><span data-stu-id="4ccc2-130">Command Type Text</span></span>
 <span data-ttu-id="4ccc2-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データセットを作成するとき、既定ではリレーショナル クエリ デザイナーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-131">When you create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dataset, the relational query designer opens by default.</span></span> <span data-ttu-id="4ccc2-132">テキスト ベースのクエリ デザイナーに切り替えるには、ツール バーの **[テキストとして編集]** 切り替えボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-132">To switch to the text-based query designer, click the **Edit As Text** toggle button on the toolbar.</span></span> <span data-ttu-id="4ccc2-133">テキスト ベースのクエリ デザイナーは、クエリ ペインと結果ペインの 2 つのペインで構成されています。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-133">The text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="4ccc2-134">次の図に各ペインの名称を示します。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-134">The following figure labels each pane.</span></span>

 <span data-ttu-id="4ccc2-135">![リレーショナル データのクエリに使用する汎用クエリ デザイナー](../../analysis-services/media/rsqd-dsaw-sql-generic.gif "リレーショナル データのクエリに使用する汎用クエリ デザイナー")</span><span class="sxs-lookup"><span data-stu-id="4ccc2-135">![Generic query designer, for relational data query](../../analysis-services/media/rsqd-dsaw-sql-generic.gif "Generic query designer, for relational data query")</span></span>

 <span data-ttu-id="4ccc2-136">次の表に各ペインの機能を示します。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-136">The following table describes the function of each pane.</span></span>

|<span data-ttu-id="4ccc2-137">ペイン</span><span class="sxs-lookup"><span data-stu-id="4ccc2-137">Pane</span></span>|<span data-ttu-id="4ccc2-138">機能</span><span class="sxs-lookup"><span data-stu-id="4ccc2-138">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="4ccc2-139">クエリ</span><span class="sxs-lookup"><span data-stu-id="4ccc2-139">Query</span></span>|<span data-ttu-id="4ccc2-140">[!INCLUDE[tsql](../../../includes/tsql-md.md)] クエリ テキストを表示します。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-140">Displays the [!INCLUDE[tsql](../../../includes/tsql-md.md)] query text.</span></span> <span data-ttu-id="4ccc2-141">[!INCLUDE[tsql](../../../includes/tsql-md.md)] クエリを記述または編集する際に、このペインを使用します。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-141">Use this pane to write or edit a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query.</span></span>|
|<span data-ttu-id="4ccc2-142">結果</span><span class="sxs-lookup"><span data-stu-id="4ccc2-142">Result</span></span>|<span data-ttu-id="4ccc2-143">クエリの結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-143">Displays the results of the query.</span></span> <span data-ttu-id="4ccc2-144">クエリを実行するには、任意のペインで右クリックして、 **[実行]** をクリックするか、ツール バーの **[実行]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-144">To run the query, right-click in any pane and click **Run**, or click the **Run** button on the toolbar.</span></span>|

#### <a name="example"></a><span data-ttu-id="4ccc2-145">例</span><span class="sxs-lookup"><span data-stu-id="4ccc2-145">Example</span></span>
 <span data-ttu-id="4ccc2-146">次のクエリは、 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] スキーマの**2008**データベーステーブルから姓の一覧を返し `ContactType` `Person` ます。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-146">The following query returns the list of last names from the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]**2008** database `ContactType` table for the `Person` schema.</span></span>

```
SELECT Name FROM Person.ContactType
```

 <span data-ttu-id="4ccc2-147">ツール バーの **[実行]** をクリックすると、 **クエリ** ペインのコマンドが実行され、その結果が **結果** ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-147">When you click **Run** on the toolbar, the command in the **Query** pane runs and the results are displayed in the **Result** pane.</span></span> <span data-ttu-id="4ccc2-148">結果セットには、所有者や販売担当者など 20 種類の連絡先の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-148">The resultset displays a list of 20 types of contacts, for example, Owner or Sales Agent.</span></span>

### <a name="command-type-storedprocedure"></a><span data-ttu-id="4ccc2-149">コマンドの種類 (StoredProcedure)</span><span class="sxs-lookup"><span data-stu-id="4ccc2-149">Command Type StoredProcedure</span></span>
 <span data-ttu-id="4ccc2-150">**[コマンドの種類] で [StoredProcedure]** を選択した場合、テキスト ベースのクエリ デザイナーには、クエリ ペインと結果ペインの 2 つのペインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-150">When you select **Command typeStoredProcedure**, the text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="4ccc2-151">ストアド プロシージャ名をクエリ ペインに入力し、ツール バーの **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-151">Enter the stored procedure name in the Query pane and click **Run** on the toolbar.</span></span> <span data-ttu-id="4ccc2-152">ストアド プロシージャでパラメーターを使用する場合、 **[クエリ パラメーターの定義]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-152">If the stored procedures uses parameters, the **Define Query Parameters** dialog box opens.</span></span> <span data-ttu-id="4ccc2-153">ストアド プロシージャのパラメーター値を入力します。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-153">Enter the parameter values for the stored procedure.</span></span> <span data-ttu-id="4ccc2-154">すべてのストアド プロシージャの入力パラメーターについて、レポート パラメーターが作成されます。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-154">A report parameter is created for every stored procedure input parameter.</span></span>

 <span data-ttu-id="4ccc2-155">次の図に、ストアド プロシージャを実行したときのクエリ ペインと結果ペインを示します。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-155">The following figure shows the Query and Results panes when you run a stored procedure.</span></span> <span data-ttu-id="4ccc2-156">この場合、入力パラメーターは定数です。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-156">In this case, the input parameters are constants.</span></span>

 <span data-ttu-id="4ccc2-157">![テキスト ベースのクエリ デザイナーのストアド プロシージャ](../../analysis-services/media/rs-relational-text-sp.gif "テキスト ベースのクエリ デザイナーのストアド プロシージャ")</span><span class="sxs-lookup"><span data-stu-id="4ccc2-157">![Stored procedure in text-based query designer](../../analysis-services/media/rs-relational-text-sp.gif "Stored procedure in text-based query designer")</span></span>

 <span data-ttu-id="4ccc2-158">次の表に各ペインの機能を示します。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-158">The following table describes the function of each pane.</span></span>

|<span data-ttu-id="4ccc2-159">ペイン</span><span class="sxs-lookup"><span data-stu-id="4ccc2-159">Pane</span></span>|<span data-ttu-id="4ccc2-160">機能</span><span class="sxs-lookup"><span data-stu-id="4ccc2-160">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="4ccc2-161">クエリ</span><span class="sxs-lookup"><span data-stu-id="4ccc2-161">Query</span></span>|<span data-ttu-id="4ccc2-162">ストアド プロシージャの名前と入力パラメーターを表示します。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-162">Displays the name of the stored procedure and any input parameters.</span></span>|
|<span data-ttu-id="4ccc2-163">結果</span><span class="sxs-lookup"><span data-stu-id="4ccc2-163">Result</span></span>|<span data-ttu-id="4ccc2-164">クエリの結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-164">Displays the results of the query.</span></span> <span data-ttu-id="4ccc2-165">クエリを実行するには、任意のペインで右クリックして、 **[実行]** をクリックするか、ツール バーの **[実行]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-165">To run the query, right-click in any pane and click **Run**, or click the **Run** button on the toolbar.</span></span>|

#### <a name="example"></a><span data-ttu-id="4ccc2-166">例</span><span class="sxs-lookup"><span data-stu-id="4ccc2-166">Example</span></span>
 <span data-ttu-id="4ccc2-167">次のクエリは、 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] **2008**ストアドプロシージャを呼び出し `uspGetWhereUsedProductID` ます。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-167">The following query calls the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]**2008** stored procedure `uspGetWhereUsedProductID`.</span></span> <span data-ttu-id="4ccc2-168">クエリを実行する場合は、製品 ID 番号パラメーターの値を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-168">You must enter a value for the product identification number parameter when you run the query.</span></span>

```
uspGetWhereUsedProductID
```

 <span data-ttu-id="4ccc2-169">**[実行]** ( **!** ) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-169">Click the **Run** (**!**) button.</span></span> <span data-ttu-id="4ccc2-170">クエリ パラメーターの入力画面が表示されたら、次の表にある値を入力します。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-170">When prompted for the query parameters, use the following table to enter values.</span></span>

|||
|-|-|
|*@StartProductID*|<span data-ttu-id="4ccc2-171">820</span><span class="sxs-lookup"><span data-stu-id="4ccc2-171">820</span></span>|
|*@CheckDate*|<span data-ttu-id="4ccc2-172">20010115</span><span class="sxs-lookup"><span data-stu-id="4ccc2-172">20010115</span></span>|

 <span data-ttu-id="4ccc2-173">指定した日付について、結果セットには、指定したコンポーネント番号を使用している 13 の製品 ID の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-173">For the specified date, the result set displays a list of 13 product identifiers that used the specified component number.</span></span>

### <a name="command-type-tabledirect"></a><span data-ttu-id="4ccc2-174">コマンドの種類 (TableDirect)</span><span class="sxs-lookup"><span data-stu-id="4ccc2-174">Command Type TableDirect</span></span>
 <span data-ttu-id="4ccc2-175">**[コマンドの種類] で [TableDirect]** を選択した場合、テキスト ベースのクエリ デザイナーには、クエリ ペインと結果ペインの 2 つのペインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-175">When you select **Command typeTableDirect**, the text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="4ccc2-176">テーブルを入力し、 **[実行]** ボタンをクリックすると、そのテーブルのすべての列が返されます。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-176">When you enter a table and click the **Run** button, all the columns for that table are returned.</span></span>

#### <a name="example"></a><span data-ttu-id="4ccc2-177">例</span><span class="sxs-lookup"><span data-stu-id="4ccc2-177">Example</span></span>
 <span data-ttu-id="4ccc2-178">データソースの種類が OLE DB の場合、次のデータセットクエリでは、2008データベースのすべての種類の連絡先について結果セットが返され [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] **2008**ます。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-178">For a data source type OLE DB, the following dataset query returns a result set for all contact types in the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]**2008** database.</span></span>

 `Person.ContactType`

 <span data-ttu-id="4ccc2-179">テーブル名 Person.ContactType を入力した場合、これは [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントの `SELECT * FROM Person.ContactType`を作成することに相当します。</span><span class="sxs-lookup"><span data-stu-id="4ccc2-179">When you enter the table name Person.ContactType, it is the equivalent of creating the [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement `SELECT * FROM Person.ContactType`.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ccc2-180">参照</span><span class="sxs-lookup"><span data-stu-id="4ccc2-180">See Also</span></span>
 <span data-ttu-id="4ccc2-181">[リレーショナルクエリデザイナーのユーザーインターフェイス &#40;レポートビルダー&#41;](relational-query-designer-user-interface-report-builder.md) [クエリデザイナー &#40;レポートビルダー&#41;](../query-designers-report-builder.md)</span><span class="sxs-lookup"><span data-stu-id="4ccc2-181">[Relational Query Designer User Interface &#40;Report Builder&#41;](relational-query-designer-user-interface-report-builder.md) [Query Designers &#40;Report Builder&#41;](../query-designers-report-builder.md)</span></span>


