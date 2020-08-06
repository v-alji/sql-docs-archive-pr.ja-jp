---
title: SharePoint リストのクエリ デザイナー (レポート ビルダー) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10016"
ms.assetid: b8a3122c-8008-4950-b515-937636d7967f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a35efb926b8f729874cff42afc53fb5820c920f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742858"
---
# <a name="sharepoint-list-query-designer-report-builder"></a><span data-ttu-id="cd479-102">SharePoint リストのクエリ デザイナー (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="cd479-102">SharePoint List Query Designer (Report Builder)</span></span>
  <span data-ttu-id="cd479-103">レポート ビルダーにはグラフィカル クエリ デザイナーとテキスト ベースのクエリ デザイナーが用意されており、レポート データセットの SharePoint サイトから取得するデータを指定するクエリの作成に使用できます。</span><span class="sxs-lookup"><span data-stu-id="cd479-103">Report Builder provides both a graphical query designer and a text-based query designer to help you create a query that specifies the data to retrieve from a SharePoint site for a report dataset.</span></span> <span data-ttu-id="cd479-104">SharePoint リスト メタデータを検索してクエリを対話的に作成し、クエリの結果を表示する場合は、グラフィカル クエリ デザイナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="cd479-104">Use the graphical query designer to explore the SharePoint list metadata, interactively build a query, and view the results of your query.</span></span> <span data-ttu-id="cd479-105">グラフィカル クエリ デザイナーで作成されたクエリの表示、クエリの変更、またはクエリ コマンドの入力を行う場合は、テキスト ベースのクエリ デザイナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="cd479-105">Use the text-based query designer to view the query that was built by the graphical query designer, modify a query, or type the query commands.</span></span> <span data-ttu-id="cd479-106">ファイルまたはレポートから既存のクエリをインポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="cd479-106">You can also import an existing query from a file or report.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cd479-107">ユーザーは、クエリを作成して実行する際にデータ ソースにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="cd479-107">Users access data sources when they create and run queries.</span></span> <span data-ttu-id="cd479-108">したがって、データ ソースに対する最小限の権限 (読み取り専用権限など) を付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd479-108">You should grant minimal permissions on the data sources, such as read-only permissions.</span></span>  
  
## <a name="graphical-query-designer"></a><span data-ttu-id="cd479-109">グラフィカル クエリ デザイナー</span><span class="sxs-lookup"><span data-stu-id="cd479-109">Graphical Query Designer</span></span>  
 <span data-ttu-id="cd479-110">グラフィカル クエリ デザイナーでは、SharePoint サイトを検索し、データセットの SharePoint リスト データを取得するコマンドを対話的に作成できます。</span><span class="sxs-lookup"><span data-stu-id="cd479-110">In the graphical query designer you can explorer the SharePoint site, interactively build the command that retrieve SharePoint list data for a dataset.</span></span> <span data-ttu-id="cd479-111">データセットに含めるフィールドを選択し、必要に応じて、データセットのデータを制限するフィルターを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd479-111">You choose the fields to include in the dataset and optionally, specify filters that limit the data in the dataset.</span></span> <span data-ttu-id="cd479-112">フィルターをパラメーターとして使用することを指定すると、フィルターの値を実行時に提供できます。</span><span class="sxs-lookup"><span data-stu-id="cd479-112">You can specify that filters are used as parameters and provide the value of the filter at run-time.</span></span>  
  
 <span data-ttu-id="cd479-113">SharePoint リストには、レポートに含めるには適さない大量の SharePoint 固有フィールドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cd479-113">SharePoint lists include a large number of SharePoint specific fields that might not be useful to include in reports.</span></span> <span data-ttu-id="cd479-114">クエリ デザイナーには、使用するフィールドを見つけやすいようにフィールドを非表示にするオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="cd479-114">The query designer provides an option to hide these fields to make it easier and quicker to determine the fields to use.</span></span>  
  
 <span data-ttu-id="cd479-115">グラフィカル クエリ デザイナーは、3 つの領域に分割されています。</span><span class="sxs-lookup"><span data-stu-id="cd479-115">The graphical query designer is divided into three areas</span></span>  
  
-   <span data-ttu-id="cd479-116">使用するリスト アイテムおよびそのフィールドを選択するための探索ペイン。</span><span class="sxs-lookup"><span data-stu-id="cd479-116">Explore pane in which you select the list items and their fields to use.</span></span>  
  
-   <span data-ttu-id="cd479-117">クエリを作成するためのデザイン領域。</span><span class="sxs-lookup"><span data-stu-id="cd479-117">Design area in which you build the query.</span></span>  
  
-   <span data-ttu-id="cd479-118">クエリ結果を表示するための結果ペイン。</span><span class="sxs-lookup"><span data-stu-id="cd479-118">Results pane in which you view the query results.</span></span>  
  
 <span data-ttu-id="cd479-119">次の図は、SharePoint リストを使用した場合のグラフィカル クエリ デザイナーです。</span><span class="sxs-lookup"><span data-stu-id="cd479-119">The following figure shows the graphical query designer when it is used with SharePoint lists.</span></span>  
  
 <span data-ttu-id="cd479-120">![rsQD_Relational_Graphical_SharePoint](../media/rsqd-relational-graphical-sharepoint.gif "rsQD_Relational_Graphical_SharePoint")</span><span class="sxs-lookup"><span data-stu-id="cd479-120">![rsQD_Relational_Graphical_SharePoint](../media/rsqd-relational-graphical-sharepoint.gif "rsQD_Relational_Graphical_SharePoint")</span></span>  
  
 <span data-ttu-id="cd479-121">次の表に各ペインの機能を示します。</span><span class="sxs-lookup"><span data-stu-id="cd479-121">The following table describes the function of each pane.</span></span>  
  
 [<span data-ttu-id="cd479-122">SharePoint リスト</span><span class="sxs-lookup"><span data-stu-id="cd479-122">SharePoint Lists</span></span>](#DatabaseView)  
 <span data-ttu-id="cd479-123">SharePoint リストとリストに含まれる各アイテム内のフィールドを表示します。</span><span class="sxs-lookup"><span data-stu-id="cd479-123">Displays SharePoint lists and the fields within each item in the list.</span></span>  
  
 [<span data-ttu-id="cd479-124">選択されたフィールド</span><span class="sxs-lookup"><span data-stu-id="cd479-124">Selected fields</span></span>](#SelectedFields)  
 <span data-ttu-id="cd479-125">SharePoint リスト ペインで選択したアイテムの SharePoint リストのフィールド名の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="cd479-125">Displays the list of SharePoint list field names from the selected items in the SharePoint Lists pane.</span></span> <span data-ttu-id="cd479-126">これらのフィールドがレポート データセットのフィールド コレクションになります。</span><span class="sxs-lookup"><span data-stu-id="cd479-126">These fields become the field collection for the report dataset.</span></span>  
  
 [<span data-ttu-id="cd479-127">適用されたフィルター</span><span class="sxs-lookup"><span data-stu-id="cd479-127">Applied filters</span></span>](#AppliedFilters)  
 <span data-ttu-id="cd479-128">データベース ビューのテーブルまたはビューのフィールドおよびフィルター条件の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="cd479-128">Displays a list of fields and filter criteria for tables or views in the Database view.</span></span>  
  
 [<span data-ttu-id="cd479-129">クエリの結果</span><span class="sxs-lookup"><span data-stu-id="cd479-129">Query results</span></span>](#QueryResults)  
 <span data-ttu-id="cd479-130">自動的に生成されたクエリの結果セットのサンプル データを表示します。</span><span class="sxs-lookup"><span data-stu-id="cd479-130">Displays sample data for the result set for the automatically generated query.</span></span>  
  
###  <a name="sharepoint-lists-pane"></a><a name="DatabaseView"></a> <span data-ttu-id="cd479-131">SharePoint リスト ペイン</span><span class="sxs-lookup"><span data-stu-id="cd479-131">SharePoint Lists Pane</span></span>  
 <span data-ttu-id="cd479-132">SharePoint リスト ペインには、表示する権限のあるデータベース オブジェクトのメタデータが表示されます。表示されるメタデータは、データ ソース接続と資格情報によって決まります。</span><span class="sxs-lookup"><span data-stu-id="cd479-132">The SharePoint Lists pane displays the metadata for database objects that you have the permissions to view, which is determined by the data source connection and credentials.</span></span> <span data-ttu-id="cd479-133">階層ビューに、データベース スキーマ別に編成されたデータベース オブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd479-133">The hierarchical view displays database objects organized by database schema.</span></span> <span data-ttu-id="cd479-134">各スキーマのノードを展開すると、テーブル、ビュー、ストアド プロシージャ、およびテーブル値関数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd479-134">Expand the node for each schema to view tables, views, stored procedures, and table-valued functions.</span></span> <span data-ttu-id="cd479-135">テーブルまたはビューを展開すると列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd479-135">Expand a table or view to display the columns.</span></span>  
  
###  <a name="selected-fields-pane"></a><a name="SelectedFields"></a> <span data-ttu-id="cd479-136">選択されたフィールド ペイン</span><span class="sxs-lookup"><span data-stu-id="cd479-136">Selected Fields Pane</span></span>  
 <span data-ttu-id="cd479-137">選択されたフィールド ペインには、SharePoint リスト アイテムについて選択したリスト アイテム フィールドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd479-137">The Selected Fields pane displays the list item fields that you select for SharePoint list items.</span></span> <span data-ttu-id="cd479-138">このペインに表示されるフィールドがレポート データセットのフィールド コレクションになります。</span><span class="sxs-lookup"><span data-stu-id="cd479-138">The fields that are displayed in this pane become the field collection for the report dataset.</span></span> <span data-ttu-id="cd479-139">データセットとクエリを作成した後、レポート データ ペインを使用して、レポート データセットのフィールド コレクションを表示できます。</span><span class="sxs-lookup"><span data-stu-id="cd479-139">After you create a dataset and a query, use the Report Data pane to view the field collection for a report dataset.</span></span> <span data-ttu-id="cd479-140">これらのフィールドは、レポートを表示するときにテーブル、グラフ、およびその他のレポート アイテムに表示できるデータを表します。</span><span class="sxs-lookup"><span data-stu-id="cd479-140">These fields represent the data you can display in tables, charts, and other report items when you view a report.</span></span>  
  
 <span data-ttu-id="cd479-141">このペインのフィールドを追加したり削除したりするには、SharePoint リスト ペインでテーブルまたはビューのフィールドのチェック ボックスをオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="cd479-141">To add or remove fields to this pane, select or clear check boxes for the table or view fields in the SharePoint Lists pane.</span></span>  
  
###  <a name="applied-filters-pane"></a><a name="AppliedFilters"></a> <span data-ttu-id="cd479-142">適用されたフィルター ペイン</span><span class="sxs-lookup"><span data-stu-id="cd479-142">Applied Filters Pane</span></span>  
 <span data-ttu-id="cd479-143">適用されたフィルター ペインには、実行時に取得されるデータの行数を制限するために使用される条件が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd479-143">The Applied Filters pane displays the criteria that are used to limit the number of rows of data that are retrieved at run-time.</span></span> <span data-ttu-id="cd479-144">このペインで指定された条件を使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] の WHERE 句が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cd479-144">Criteria specified in this pane are used to generate a [!INCLUDE[tsql](../../includes/tsql-md.md)] WHERE clause.</span></span> <span data-ttu-id="cd479-145">パラメーター オプションを選択すると、レポート パラメーターが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="cd479-145">When you select the parameter option, a report parameter is automatically created.</span></span> <span data-ttu-id="cd479-146">クエリ パラメーターに基づくレポート パラメーターを使用すると、ユーザーがクエリの値を指定してレポートのデータを制御できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cd479-146">Report parameters that are based on query parameters enable a user to specify values for the query to control the data in the report.</span></span>  
  
 <span data-ttu-id="cd479-147">次の列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd479-147">The following columns are displayed:</span></span>  
  
-   <span data-ttu-id="cd479-148">**フィールド名** : 条件を適用するフィールドの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="cd479-148">**Field Name** Displays the name of the field to apply the criteria to.</span></span>  
  
-   <span data-ttu-id="cd479-149">**[演算子]** フィルター式で使用する演算を表示します。</span><span class="sxs-lookup"><span data-stu-id="cd479-149">**Operator** Displays the operation to use in the filter expression.</span></span>  
  
-   <span data-ttu-id="cd479-150">**値** : フィルター式で使用する値を表示します。</span><span class="sxs-lookup"><span data-stu-id="cd479-150">**Value** Displays the value to use in the filter expression.</span></span>  
  
-   <span data-ttu-id="cd479-151">**パラメーター** : クエリ パラメーターをクエリに追加するオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="cd479-151">**Parameter** Displays the option to add a query parameter to the query.</span></span> <span data-ttu-id="cd479-152">[データセットのプロパティ] を使用すると、クエリ パラメーターとレポート パラメーターの関係を表示できます。</span><span class="sxs-lookup"><span data-stu-id="cd479-152">Use the Dataset properties to view the relationship between query parameter and report parameter.</span></span>  
  
###  <a name="query-results-pane"></a><a name="QueryResults"></a> <span data-ttu-id="cd479-153">クエリ結果ペイン</span><span class="sxs-lookup"><span data-stu-id="cd479-153">Query Results Pane</span></span>  
 <span data-ttu-id="cd479-154">クエリ結果ペインには、その他のペインの選択内容によって指定されている自動的に生成されたクエリの結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd479-154">The Query results pane displays the results for the automatically generated query that is specified by selections in the other panes.</span></span> <span data-ttu-id="cd479-155">結果セットの列は選択されたフィールド ペインで指定したフィールドで、行データは適用されたフィルター ペインで指定したフィルターによって制限されます。</span><span class="sxs-lookup"><span data-stu-id="cd479-155">The columns in the result set are the fields that you specify in the Selected Fields pane and the row data is limited by the filters that you specify in the Applied Filters pane.</span></span>  
  
 <span data-ttu-id="cd479-156">このデータは、クエリの実行時にデータ ソースから取得された値を表します。</span><span class="sxs-lookup"><span data-stu-id="cd479-156">This data represents values from the data source at the time that you run the query.</span></span> <span data-ttu-id="cd479-157">このデータはレポート定義に保存されません。レポートの実際のデータは、レポートの処理時に取得されます。</span><span class="sxs-lookup"><span data-stu-id="cd479-157">The data is not saved in the report definition .The actual data in the report is retrieved when the report is processed.</span></span>  
  
 <span data-ttu-id="cd479-158">結果セットの並べ替え順序は、データがデータ ソースから取得された順序によって決まります。</span><span class="sxs-lookup"><span data-stu-id="cd479-158">Sort order in the result set is determined by the order the data is retrieved from the data source.</span></span> <span data-ttu-id="cd479-159">並べ替え順序は、クエリの修正によって変更することも、レポートのデータが取得された後に変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="cd479-159">Sort order can be changed by modifying the query or after the data is retrieved for the report.</span></span>  
  
### <a name="graphical-query-designer-toolbar"></a><span data-ttu-id="cd479-160">グラフィカル クエリ デザイナーのツール バー</span><span class="sxs-lookup"><span data-stu-id="cd479-160">Graphical Query Designer Toolbar</span></span>  
 <span data-ttu-id="cd479-161">リレーショナル クエリ デザイナーのツール バーにある次のボタンを使用すると、クエリを指定したりその結果を表示したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="cd479-161">The relational query designer toolbar provides the following buttons to help you specify or view the results of a query.</span></span>  
  
|<span data-ttu-id="cd479-162">ボタン</span><span class="sxs-lookup"><span data-stu-id="cd479-162">Button</span></span>|<span data-ttu-id="cd479-163">説明</span><span class="sxs-lookup"><span data-stu-id="cd479-163">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="cd479-164">**[テキストとして編集]**</span><span class="sxs-lookup"><span data-stu-id="cd479-164">**Edit As Text**</span></span>|<span data-ttu-id="cd479-165">テキスト ベースのクエリ デザイナーに切り替えて、自動的に生成されたクエリの表示や変更を行います。</span><span class="sxs-lookup"><span data-stu-id="cd479-165">Toggle to the text-based query designer to view the automatically generated query or to modify the query.</span></span>|  
|<span data-ttu-id="cd479-166">**[インポート]**</span><span class="sxs-lookup"><span data-stu-id="cd479-166">**Import**</span></span>|<span data-ttu-id="cd479-167">ファイルまたはレポートから既存のクエリをインポートします。</span><span class="sxs-lookup"><span data-stu-id="cd479-167">Import an existing query from a file or report.</span></span> <span data-ttu-id="cd479-168">サポートされているファイルの種類は .sql と .rdl です。</span><span class="sxs-lookup"><span data-stu-id="cd479-168">File types .sql and .rdl are supported.</span></span>|  
|<span data-ttu-id="cd479-169">**[クエリの実行]**</span><span class="sxs-lookup"><span data-stu-id="cd479-169">**Run Query**</span></span>|<span data-ttu-id="cd479-170">クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="cd479-170">Run the query.</span></span> <span data-ttu-id="cd479-171">クエリ結果ペインに結果セットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd479-171">The Query results pane displays the result set.</span></span>|  
|<span data-ttu-id="cd479-172">**[非表示フィールドの表示]**</span><span class="sxs-lookup"><span data-stu-id="cd479-172">**Show Hidden Fields**</span></span>|<span data-ttu-id="cd479-173">SharePoint リンク アイテムの ProgID やレベルなど、SharePoint で自動的に生成されたが、レポートでは通常使用されないフィールドの表示と非表示を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="cd479-173">Toggle to show or hide the fields that were automatically generated by SharePoint such as the ProgId and Level for SharePoint link items, but are typically not used in reports..</span></span> <span data-ttu-id="cd479-174">これらのフィールドを非表示にすると、フィールド一覧が簡略化され、使いやすくなります。</span><span class="sxs-lookup"><span data-stu-id="cd479-174">Hiding these fields makes the field list shorter and easier to use.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd479-175">参照</span><span class="sxs-lookup"><span data-stu-id="cd479-175">See Also</span></span>  
 [<span data-ttu-id="cd479-176">クエリ デザイナー &#40;レポート ビルダー&#41;</span><span class="sxs-lookup"><span data-stu-id="cd479-176">Query Designers &#40;Report Builder&#41;</span></span>](../query-designers-report-builder.md)  
  
  
