---
title: SharePoint リストクエリデザイナー |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 593de30c-69f0-42a8-8467-16e78647b74c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 018b525cb68972f579aebfbfec70d0b94afc4b55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712706"
---
# <a name="sharepoint-list-query-designer"></a><span data-ttu-id="86c28-102">SharePoint リストのクエリ デザイナー</span><span class="sxs-lookup"><span data-stu-id="86c28-102">SharePoint List Query Designer</span></span>
  <span data-ttu-id="86c28-103">レポート デザイナーにはグラフィカル クエリ デザイナーとテキストベースのクエリ デザイナーが用意されており、レポート データセット用に SharePoint サイトから取得するデータを指定するクエリの作成に使用できます。</span><span class="sxs-lookup"><span data-stu-id="86c28-103">Report Designer provides both a graphical query designer and a text-based query designer to help you create a query that specifies the data to retrieve from a SharePoint site for a report dataset.</span></span> <span data-ttu-id="86c28-104">SharePoint リスト メタデータを検索してクエリを対話的に作成し、クエリの結果を表示する場合は、グラフィカル クエリ デザイナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="86c28-104">Use the graphical query designer to explore the SharePoint list metadata, interactively build a query, and view the results of your query.</span></span> <span data-ttu-id="86c28-105">グラフィカル クエリ デザイナーで作成されたクエリの表示、クエリの変更、またはクエリ コマンドの入力を行う場合は、テキスト ベースのクエリ デザイナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="86c28-105">Use the text-based query designer to view the query that was built by the graphical query designer, modify a query, or type the query commands.</span></span> <span data-ttu-id="86c28-106">ファイルまたはレポートから既存のクエリをインポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="86c28-106">You can also import an existing query from a file or report.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="86c28-107">ユーザーは、クエリを作成して実行する際にデータ ソースにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="86c28-107">Users access data sources when they create and run queries.</span></span> <span data-ttu-id="86c28-108">したがって、データ ソースに対する最小限の権限 (読み取り専用権限など) を付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86c28-108">You should grant minimal permissions on the data sources, such as read-only permissions.</span></span>  
  
## <a name="graphical-query-designer"></a><span data-ttu-id="86c28-109">グラフィカル クエリ デザイナー</span><span class="sxs-lookup"><span data-stu-id="86c28-109">Graphical Query Designer</span></span>  
 <span data-ttu-id="86c28-110">グラフィカル クエリ デザイナーでは、SharePoint サイトを検索し、データセットの SharePoint リスト データを取得するコマンドを対話的に作成できます。</span><span class="sxs-lookup"><span data-stu-id="86c28-110">In the graphical query designer you can explorer the SharePoint site, interactively build the command that retrieve SharePoint list data for a dataset.</span></span> <span data-ttu-id="86c28-111">データセットに含めるフィールドを選択し、必要に応じて、データセットのデータを制限するフィルターを指定します。</span><span class="sxs-lookup"><span data-stu-id="86c28-111">You choose the fields to include in the dataset and optionally, specify filters that limit the data in the dataset.</span></span> <span data-ttu-id="86c28-112">フィルターをパラメーターとして使用することを指定すると、フィルターの値を実行時に提供できます。</span><span class="sxs-lookup"><span data-stu-id="86c28-112">You can specify that filters are used as parameters and provide the value of the filter at run-time.</span></span>  
  
 <span data-ttu-id="86c28-113">SharePoint リストには、レポートに含めるには適さない大量の SharePoint 固有フィールドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="86c28-113">SharePoint lists include a large number of SharePoint specific fields that might not be useful to include in reports.</span></span> <span data-ttu-id="86c28-114">クエリ デザイナーには、使用するフィールドを見つけやすいようにフィールドを非表示にするオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="86c28-114">The query designer provides an option to hide these fields to make it easier and quicker to determine the fields to use.</span></span>  
  
 <span data-ttu-id="86c28-115">グラフィカル クエリ デザイナーは、3 つの領域に分割されています。</span><span class="sxs-lookup"><span data-stu-id="86c28-115">The graphical query designer is divided into three areas</span></span>  
  
-   <span data-ttu-id="86c28-116">使用するリスト アイテムおよびそのフィールドを選択するための探索ペイン。</span><span class="sxs-lookup"><span data-stu-id="86c28-116">Explore pane in which you select the list items and their fields to use.</span></span>  
  
-   <span data-ttu-id="86c28-117">クエリを作成するためのデザイン領域。</span><span class="sxs-lookup"><span data-stu-id="86c28-117">Design area in which you build the query.</span></span>  
  
-   <span data-ttu-id="86c28-118">クエリ結果を表示するための結果ペイン。</span><span class="sxs-lookup"><span data-stu-id="86c28-118">Results pane in which you view the query results.</span></span>  
  
 <span data-ttu-id="86c28-119">次の図は、SharePoint リストを使用した場合のグラフィカル クエリ デザイナーです。</span><span class="sxs-lookup"><span data-stu-id="86c28-119">The following figure shows the graphical query designer when it is used with SharePoint lists.</span></span>  
  
 <span data-ttu-id="86c28-120">![rsQD_Relational_Graphical_SharePoint](media/rsqd-relational-graphical-sharepoint.gif "rsQD_Relational_Graphical_SharePoint")</span><span class="sxs-lookup"><span data-stu-id="86c28-120">![rsQD_Relational_Graphical_SharePoint](media/rsqd-relational-graphical-sharepoint.gif "rsQD_Relational_Graphical_SharePoint")</span></span>  
  
 <span data-ttu-id="86c28-121">次の表に各ペインの機能を示します。</span><span class="sxs-lookup"><span data-stu-id="86c28-121">The following table describes the function of each pane.</span></span>  
  
 [<span data-ttu-id="86c28-122">SharePoint リスト</span><span class="sxs-lookup"><span data-stu-id="86c28-122">SharePoint Lists</span></span>](#DatabaseView)  
 <span data-ttu-id="86c28-123">SharePoint リストとリストに含まれる各アイテム内のフィールドを表示します。</span><span class="sxs-lookup"><span data-stu-id="86c28-123">Displays SharePoint lists and the fields within each item in the list.</span></span>  
  
 [<span data-ttu-id="86c28-124">選択されたフィールド</span><span class="sxs-lookup"><span data-stu-id="86c28-124">Selected fields</span></span>](#SelectedFields)  
 <span data-ttu-id="86c28-125">SharePoint リスト ペインで選択したアイテムの SharePoint リストのフィールド名の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="86c28-125">Displays the list of SharePoint list field names from the selected items in the SharePoint Lists pane.</span></span> <span data-ttu-id="86c28-126">これらのフィールドがレポート データセットのフィールド コレクションになります。</span><span class="sxs-lookup"><span data-stu-id="86c28-126">These fields become the field collection for the report dataset.</span></span>  
  
 [<span data-ttu-id="86c28-127">適用されたフィルター</span><span class="sxs-lookup"><span data-stu-id="86c28-127">Applied filters</span></span>](#AppliedFilters)  
 <span data-ttu-id="86c28-128">データベース ビューのテーブルまたはビューのフィールドおよびフィルター条件の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="86c28-128">Displays a list of fields and filter criteria for tables or views in the Database view.</span></span>  
  
 [<span data-ttu-id="86c28-129">Query results</span><span class="sxs-lookup"><span data-stu-id="86c28-129">Query results</span></span>](#QueryResults)  
 <span data-ttu-id="86c28-130">自動的に生成されたクエリの結果セットのサンプル データを表示します。</span><span class="sxs-lookup"><span data-stu-id="86c28-130">Displays sample data for the result set for the automatically generated query.</span></span>  
  
###  <a name="sharepoint-lists-pane"></a><a name="DatabaseView"></a> <span data-ttu-id="86c28-131">SharePoint リスト ペイン</span><span class="sxs-lookup"><span data-stu-id="86c28-131">SharePoint Lists Pane</span></span>  
 <span data-ttu-id="86c28-132">SharePoint リスト ペインには、表示する権限のあるデータベース オブジェクトのメタデータが表示されます。表示されるメタデータは、データ ソース接続と資格情報によって決まります。</span><span class="sxs-lookup"><span data-stu-id="86c28-132">The SharePoint Lists pane displays the metadata for database objects that you have the permissions to view, which is determined by the data source connection and credentials.</span></span> <span data-ttu-id="86c28-133">階層ビューに、データベース スキーマ別に編成されたデータベース オブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="86c28-133">The hierarchical view displays database objects organized by database schema.</span></span> <span data-ttu-id="86c28-134">各スキーマのノードを展開すると、テーブル、ビュー、ストアド プロシージャ、およびテーブル値関数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="86c28-134">Expand the node for each schema to view tables, views, stored procedures, and table-valued functions.</span></span> <span data-ttu-id="86c28-135">テーブルまたはビューを展開すると列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="86c28-135">Expand a table or view to display the columns.</span></span>  
  
###  <a name="selected-fields-pane"></a><a name="SelectedFields"></a> <span data-ttu-id="86c28-136">選択されたフィールド ペイン</span><span class="sxs-lookup"><span data-stu-id="86c28-136">Selected Fields Pane</span></span>  
 <span data-ttu-id="86c28-137">選択されたフィールド ペインには、SharePoint リスト アイテムについて選択したリスト アイテム フィールドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="86c28-137">The Selected Fields pane displays the list item fields that you select for SharePoint list items.</span></span> <span data-ttu-id="86c28-138">このペインに表示されるフィールドがレポート データセットのフィールド コレクションになります。</span><span class="sxs-lookup"><span data-stu-id="86c28-138">The fields that are displayed in this pane become the field collection for the report dataset.</span></span> <span data-ttu-id="86c28-139">データセットとクエリを作成した後、レポート データ ペインを使用して、レポート データセットのフィールド コレクションを表示できます。</span><span class="sxs-lookup"><span data-stu-id="86c28-139">After you create a dataset and a query, use the Report Data pane to view the field collection for a report dataset.</span></span> <span data-ttu-id="86c28-140">これらのフィールドは、レポートを表示するときにテーブル、グラフ、およびその他のレポート アイテムに表示できるデータを表します。</span><span class="sxs-lookup"><span data-stu-id="86c28-140">These fields represent the data you can display in tables, charts, and other report items when you view a report.</span></span>  
  
 <span data-ttu-id="86c28-141">このペインのフィールドを追加したり削除したりするには、SharePoint リスト ペインでテーブルまたはビューのフィールドのチェック ボックスをオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="86c28-141">To add or remove fields to this pane, select or clear check boxes for the table or view fields in the SharePoint Lists pane.</span></span>  
  
###  <a name="applied-filters-pane"></a><a name="AppliedFilters"></a> <span data-ttu-id="86c28-142">適用されたフィルター ペイン</span><span class="sxs-lookup"><span data-stu-id="86c28-142">Applied Filters Pane</span></span>  
 <span data-ttu-id="86c28-143">適用されたフィルター ペインには、実行時に取得されるデータの行数を制限するために使用される条件が表示されます。</span><span class="sxs-lookup"><span data-stu-id="86c28-143">The Applied Filters pane displays the criteria that are used to limit the number of rows of data that are retrieved at run-time.</span></span> <span data-ttu-id="86c28-144">このペインで指定された条件を使用して [!INCLUDE[tsql](../includes/tsql-md.md)] の WHERE 句が生成されます。</span><span class="sxs-lookup"><span data-stu-id="86c28-144">Criteria specified in this pane are used to generate a [!INCLUDE[tsql](../includes/tsql-md.md)] WHERE clause.</span></span> <span data-ttu-id="86c28-145">パラメーター オプションを選択すると、レポート パラメーターが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="86c28-145">When you select the parameter option, a report parameter is automatically created.</span></span> <span data-ttu-id="86c28-146">クエリ パラメーターに基づくレポート パラメーターを使用すると、ユーザーがクエリの値を指定してレポートのデータを制御できるようになります。</span><span class="sxs-lookup"><span data-stu-id="86c28-146">Report parameters that are based on query parameters enable a user to specify values for the query to control the data in the report.</span></span>  
  
 <span data-ttu-id="86c28-147">次の列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="86c28-147">The following columns are displayed:</span></span>  
  
-   <span data-ttu-id="86c28-148">**フィールド名** : 条件を適用するフィールドの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="86c28-148">**Field Name** Displays the name of the field to apply the criteria to.</span></span>  
  
-   <span data-ttu-id="86c28-149">**[演算子]** フィルター式で使用する演算を表示します。</span><span class="sxs-lookup"><span data-stu-id="86c28-149">**Operator** Displays the operation to use in the filter expression.</span></span>  
  
-   <span data-ttu-id="86c28-150">**値** : フィルター式で使用する値を表示します。</span><span class="sxs-lookup"><span data-stu-id="86c28-150">**Value** Displays the value to use in the filter expression.</span></span>  
  
-   <span data-ttu-id="86c28-151">**パラメーター** : クエリ パラメーターをクエリに追加するオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="86c28-151">**Parameter** Displays the option to add a query parameter to the query.</span></span> <span data-ttu-id="86c28-152">[データセットのプロパティ] を使用すると、クエリ パラメーターとレポート パラメーターの関係を表示できます。</span><span class="sxs-lookup"><span data-stu-id="86c28-152">Use the Dataset properties to view the relationship between query parameter and report parameter.</span></span>  
  
###  <a name="query-results-pane"></a><a name="QueryResults"></a> <span data-ttu-id="86c28-153">クエリ結果ペイン</span><span class="sxs-lookup"><span data-stu-id="86c28-153">Query Results Pane</span></span>  
 <span data-ttu-id="86c28-154">クエリ結果ペインには、その他のペインの選択内容によって指定されている自動的に生成されたクエリの結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="86c28-154">The Query results pane displays the results for the automatically generated query that is specified by selections in the other panes.</span></span> <span data-ttu-id="86c28-155">結果セットの列は選択されたフィールド ペインで指定したフィールドで、行データは適用されたフィルター ペインで指定したフィルターによって制限されます。</span><span class="sxs-lookup"><span data-stu-id="86c28-155">The columns in the result set are the fields that you specify in the Selected Fields pane and the row data is limited by the filters that you specify in the Applied Filters pane.</span></span>  
  
 <span data-ttu-id="86c28-156">このデータは、クエリの実行時にデータ ソースから取得された値を表します。</span><span class="sxs-lookup"><span data-stu-id="86c28-156">This data represents values from the data source at the time that you run the query.</span></span> <span data-ttu-id="86c28-157">このデータはレポート定義に保存されません。レポートの実際のデータは、レポートの処理時に取得されます。</span><span class="sxs-lookup"><span data-stu-id="86c28-157">The data is not saved in the report definition .The actual data in the report is retrieved when the report is processed.</span></span>  
  
 <span data-ttu-id="86c28-158">結果セットの並べ替え順序は、データがデータ ソースから取得された順序によって決まります。</span><span class="sxs-lookup"><span data-stu-id="86c28-158">Sort order in the result set is determined by the order the data is retrieved from the data source.</span></span> <span data-ttu-id="86c28-159">並べ替え順序は、クエリの修正によって変更することも、レポートのデータが取得された後に変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="86c28-159">Sort order can be changed by modifying the query or after the data is retrieved for the report.</span></span>  
  
### <a name="graphical-query-designer-toolbar"></a><span data-ttu-id="86c28-160">グラフィカル クエリ デザイナーのツール バー</span><span class="sxs-lookup"><span data-stu-id="86c28-160">Graphical Query Designer Toolbar</span></span>  
 <span data-ttu-id="86c28-161">リレーショナル クエリ デザイナーのツール バーにある次のボタンを使用すると、クエリを指定したりその結果を表示したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="86c28-161">The relational query designer toolbar provides the following buttons to help you specify or view the results of a query.</span></span>  
  
|<span data-ttu-id="86c28-162">Button</span><span class="sxs-lookup"><span data-stu-id="86c28-162">Button</span></span>|<span data-ttu-id="86c28-163">説明</span><span class="sxs-lookup"><span data-stu-id="86c28-163">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="86c28-164">**[テキストとして編集]**</span><span class="sxs-lookup"><span data-stu-id="86c28-164">**Edit As Text**</span></span>|<span data-ttu-id="86c28-165">テキスト ベースのクエリ デザイナーに切り替えて、自動的に生成されたクエリの表示や変更を行います。</span><span class="sxs-lookup"><span data-stu-id="86c28-165">Toggle to the text-based query designer to view the automatically generated query or to modify the query.</span></span>|  
|<span data-ttu-id="86c28-166">**[インポート]**</span><span class="sxs-lookup"><span data-stu-id="86c28-166">**Import**</span></span>|<span data-ttu-id="86c28-167">ファイルまたはレポートから既存のクエリをインポートします。</span><span class="sxs-lookup"><span data-stu-id="86c28-167">Import an existing query from a file or report.</span></span> <span data-ttu-id="86c28-168">サポートされているファイルの種類は .sql と .rdl です。</span><span class="sxs-lookup"><span data-stu-id="86c28-168">File types .sql and .rdl are supported.</span></span>|  
|<span data-ttu-id="86c28-169">**クエリの実行**</span><span class="sxs-lookup"><span data-stu-id="86c28-169">**Run Query**</span></span>|<span data-ttu-id="86c28-170">クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="86c28-170">Run the query.</span></span> <span data-ttu-id="86c28-171">クエリ結果ペインに結果セットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="86c28-171">The Query results pane displays the result set.</span></span>|  
|<span data-ttu-id="86c28-172">**[非表示フィールドの表示]**</span><span class="sxs-lookup"><span data-stu-id="86c28-172">**Show Hidden Fields**</span></span>|<span data-ttu-id="86c28-173">SharePoint リンク アイテムの ProgID やレベルなど、SharePoint で自動的に生成されたが、レポートでは通常使用されないフィールドの表示と非表示を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="86c28-173">Toggle to show or hide the fields that were automatically generated by SharePoint such as the ProgId and Level for SharePoint link items, but are typically not used in reports..</span></span> <span data-ttu-id="86c28-174">これらのフィールドを非表示にすると、フィールド一覧が簡略化され、使いやすくなります。</span><span class="sxs-lookup"><span data-stu-id="86c28-174">Hiding these fields makes the field list shorter and easier to use.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86c28-175">参照</span><span class="sxs-lookup"><span data-stu-id="86c28-175">See Also</span></span>  
 [<span data-ttu-id="86c28-176">Reporting Services クエリ デザイナー</span><span class="sxs-lookup"><span data-stu-id="86c28-176">Reporting Services Query Designers</span></span>](../../2014/reporting-services/reporting-services-query-designers.md)  
  
  
