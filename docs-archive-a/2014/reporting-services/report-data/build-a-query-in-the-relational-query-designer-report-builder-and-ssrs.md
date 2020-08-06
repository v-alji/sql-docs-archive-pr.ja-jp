---
title: リレーショナル クエリ デザイナーでのクエリの作成 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 28b25861-f3b4-4c3e-a9b0-03d6e4cfea26
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 555d72c4d3bca8677d04fdc4160639f004d6bbe9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739426"
---
# <a name="build-a-query-in-the-relational-query-designer-report-builder-and-ssrs"></a><span data-ttu-id="ba84b-102">リレーショナル クエリ デザイナーでのクエリの作成 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="ba84b-102">Build a Query in the Relational Query Designer (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ba84b-103">クエリ デザイナーでは、レポート データセットの外部データ ソースから取得するデータを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ba84b-103">A query designer helps you specify which data to retrieve from an external data source for a report dataset.</span></span> <span data-ttu-id="ba84b-104">クエリ デザイナーは、ウィザードでクエリを構築するときや、データセット クエリを作成するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="ba84b-104">You use a query designer when you build a query in a wizard or create a dataset query.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="ba84b-105">データセットはデータ ソースに基づきます。</span><span class="sxs-lookup"><span data-stu-id="ba84b-105">A dataset is based on a data source.</span></span> <span data-ttu-id="ba84b-106">データセット クエリを定義するときに開くクエリ デザイナーは、データ ソースの種類と作成環境によって決まります。</span><span class="sxs-lookup"><span data-stu-id="ba84b-106">The type of data source and the authoring environment determines which query designer opens when you define the dataset query.</span></span> <span data-ttu-id="ba84b-107">クエリ デザイナーの機能は、基になるデータ ソースによって異なります。</span><span class="sxs-lookup"><span data-stu-id="ba84b-107">Query designer features vary based on the underlying data source.</span></span> <span data-ttu-id="ba84b-108">データ層の詳細については、「Reporting Services でのデータ[接続、データソース、およびレポートビルダー](../data-connections-data-sources-and-connection-strings-in-report-builder.md)または[データ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba84b-108">For more information about data layers, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md) or [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md).</span></span>  
  
 <span data-ttu-id="ba84b-109">クエリ デザイナーでは、次のタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="ba84b-109">You can use a query designer for the following tasks:</span></span>  
  
-   <span data-ttu-id="ba84b-110">外部データ ソースの複数のスキーマについてメタデータを検索する</span><span class="sxs-lookup"><span data-stu-id="ba84b-110">Explore the metadata for multiple schemas on the external data source</span></span>  
  
-   <span data-ttu-id="ba84b-111">データセット用に取得するフィールドを指定する</span><span class="sxs-lookup"><span data-stu-id="ba84b-111">Specify fields to retrieve for the dataset</span></span>  
  
-   <span data-ttu-id="ba84b-112">テーブルなどの 2 つのオブジェクト間のリレーションシップを指定する</span><span class="sxs-lookup"><span data-stu-id="ba84b-112">Specify relationships between two objects such as tables</span></span>  
  
-   <span data-ttu-id="ba84b-113">レポート データとして取得する前にデータを制限するフィルターを指定する</span><span class="sxs-lookup"><span data-stu-id="ba84b-113">Specify filters to restrict the data before it is retrieved as report data</span></span>  
  
-   <span data-ttu-id="ba84b-114">パラメーターを作成するかどうかを指定する</span><span class="sxs-lookup"><span data-stu-id="ba84b-114">Indicate whether to create parameters</span></span>  
  
-   <span data-ttu-id="ba84b-115">外部データ ソースに対して計算を実行する集計を指定する</span><span class="sxs-lookup"><span data-stu-id="ba84b-115">Specify aggregates to perform calculations on the external data source</span></span>  
  
 <span data-ttu-id="ba84b-116">クエリ デザイナーを開いた後、埋め込みデータセットと共有データセットのどちらについても、同じ方法でクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="ba84b-116">After you open a query designer, you build a query in the same way for either an embedded dataset or a shared dataset.</span></span> <span data-ttu-id="ba84b-117">次の手順では、埋め込みデータセット クエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="ba84b-117">The following procedures use an embedded dataset query.</span></span>  
  
 <span data-ttu-id="ba84b-118">詳細については、「[リレーショナル クエリ デザイナーのユーザー インターフェイス &#40;レポート ビルダー&#41;](relational-query-designer-user-interface-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba84b-118">For more information, see [Relational Query Designer User Interface &#40;Report Builder&#41;](relational-query-designer-user-interface-report-builder.md).</span></span>  
  
### <a name="to-build-a-query-for-an-embedded-dataset-in-report-design-view"></a><span data-ttu-id="ba84b-119">レポート デザイン ビューで埋め込みデータセットに対するクエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="ba84b-119">To build a query for an embedded dataset in Report Design View</span></span>  
  
1.  <span data-ttu-id="ba84b-120">クエリ デザイナーを開きます。</span><span class="sxs-lookup"><span data-stu-id="ba84b-120">Open the query designer.</span></span> <span data-ttu-id="ba84b-121">レポート データ ペインでデータセットを右クリックし、 **[クエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ba84b-121">In the Report Data pane, right-click the dataset, and then click **Query**.</span></span>  
  
     <span data-ttu-id="ba84b-122">データ ソースに関連付けられているクエリ デザイナーが開きます。</span><span class="sxs-lookup"><span data-stu-id="ba84b-122">The query designer that is associated with the data source opens.</span></span>  
  
2.  <span data-ttu-id="ba84b-123">データベース ビュー ペインで、テーブル、ビュー、ストアド プロシージャなどのデータベース スキーマ オブジェクトの階層ビューを表示するフォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="ba84b-123">In the Database view pane, expand the folders that display a hierarchical view of database schema objects such as tables, views, and stored procedures.</span></span> <span data-ttu-id="ba84b-124">選択ボックスをクリックしてオブジェクトのすべてのフィールドを選択するか、ノードを展開して個々のフィールドを選択します。</span><span class="sxs-lookup"><span data-stu-id="ba84b-124">Click the select box to select all fields for an object or expand the node to select individual fields.</span></span>  
  
     <span data-ttu-id="ba84b-125">データベース ビュー ペインでフィールドを選択すると、 **[フィールドの選択]** ペインに選択内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ba84b-125">As you select fields from the Database view pane, the **Select fields** pane displays your selections.</span></span>  
  
     <span data-ttu-id="ba84b-126">複数の関連するデータベース テーブルからフィールドを選択する場合に、データベース スキーマから検出されたテーブルのリレーションシップを表示するには、リレーションシップ ペインを使用します。</span><span class="sxs-lookup"><span data-stu-id="ba84b-126">If you select fields from more than one related database table, use the Relationships pane to view the table relationships that were detected from the database schema.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="ba84b-127">データセット フィールドの一覧がレポート データ ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ba84b-127">The list of dataset fields appears in the Report Data pane.</span></span>  
  
### <a name="to-specify-limits-for-a-query"></a><span data-ttu-id="ba84b-128">クエリに対する制限を指定するには</span><span class="sxs-lookup"><span data-stu-id="ba84b-128">To specify limits for a query</span></span>  
  
1.  <span data-ttu-id="ba84b-129">リレーショナル クエリ デザイナーで、フィールドを選択しており、それらのフィールドが **[選択されたフィールド]** ペインに表示されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ba84b-129">In the relational query designer, verify that you have fields selected and that the fields appear in the **Selected fields** pane.</span></span>  
  
2.  <span data-ttu-id="ba84b-130">適用されたフィルター ペインのツール バーで、 **[フィルターの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ba84b-130">In the Applied filters pane toolbar, click **Add Filter**.</span></span> <span data-ttu-id="ba84b-131">新しいフィルター行が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ba84b-131">A new filter row appears.</span></span>  
  
3.  <span data-ttu-id="ba84b-132">**[フィールド名]** で、クリックしてフィールドのドロップダウン リストを表示し、フィルター処理の基準にするフィールドの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ba84b-132">In **Field name**, click to display the drop-down list of fields, and then click the name of the field that you want to filter by.</span></span> <span data-ttu-id="ba84b-133">たとえば、数量を基準にフィルター処理を行うには、アイテムの数を格納するフィールドをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ba84b-133">For example, to filter by quantity, click the field that contains the number of items.</span></span>  
  
4.  <span data-ttu-id="ba84b-134">**[演算子]** で、クリックして演算子のドロップダウン リストを表示し、フィルターで使用する比較演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="ba84b-134">In **Operator**, click to display the drop-down list of operators, and then select the comparison operator to use in the filter.</span></span>  
  
5.  <span data-ttu-id="ba84b-135">**[値]** に、フィルター処理の基準にする値を入力します。</span><span class="sxs-lookup"><span data-stu-id="ba84b-135">In **Value**, type the value that you want to filter by.</span></span> <span data-ttu-id="ba84b-136">たとえば、100 よりも大きい数量をフィルター処理の対象とするには、「100」と入力します。</span><span class="sxs-lookup"><span data-stu-id="ba84b-136">For example, to filter on quantity greater than 100, type 100.</span></span>  
  
6.  <span data-ttu-id="ba84b-137">ユーザーがフィルター値を指定できるようにデータセット パラメーターを作成する場合は、この行のパラメーター オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="ba84b-137">Select the parameter option in this row to create a dataset parameter to enable a user to specify a filter value.</span></span> <span data-ttu-id="ba84b-138">データセット パラメーターに対応するレポート パラメーターが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="ba84b-138">A report parameter that matches the dataset parameter is automatically created.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="ba84b-139">データセット フィールドの一覧がレポート データ ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ba84b-139">The list of dataset fields appears in the Report Data pane.</span></span>  
  
### <a name="to-view-a-query-result-set"></a><span data-ttu-id="ba84b-140">クエリの結果セットを表示するには</span><span class="sxs-lookup"><span data-stu-id="ba84b-140">To view a query result set</span></span>  
  
1.  <span data-ttu-id="ba84b-141">クエリ デザイナーのツール バーで、 **[クエリの実行]\(!)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ba84b-141">On the query designer toolbar, click **Run Query (!)**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ba84b-142">クエリ デザイナーでは、デザイン時の資格情報を使用してクエリを実行し、結果セットを取得します。</span><span class="sxs-lookup"><span data-stu-id="ba84b-142">The query designer uses design time credentials to run the query and retrieve the result set.</span></span> <span data-ttu-id="ba84b-143">詳細については、「 [レポート ビルダーでの資格情報の指定](../specify-credentials-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba84b-143">For more information, see [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
 <span data-ttu-id="ba84b-144">データ ソースに対してクエリが実行され、サンプル データがクエリ結果ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ba84b-144">The query runs on the data source and returns example data in the Query results pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba84b-145">参照</span><span class="sxs-lookup"><span data-stu-id="ba84b-145">See Also</span></span>  
 <span data-ttu-id="ba84b-146">[レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ba84b-146">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="ba84b-147">[外部データ ソースのデータを追加する &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ba84b-147">[Add Data from External Data Sources &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md) </span></span>  
 <span data-ttu-id="ba84b-148">[クエリデザイナー &#40;レポートビルダー&#41;](../query-designers-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="ba84b-148">[Query Designers &#40;Report Builder&#41;](../query-designers-report-builder.md) </span></span>  
 <span data-ttu-id="ba84b-149">[共有データセットまたは埋め込みデータセットの作成 &#40;レポート ビルダーおよび SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ba84b-149">[Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ba84b-150">[レポート デザイン ビュー (レポート ビルダー)](../report-builder/report-design-view-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="ba84b-150">[Report Design View &#40;Report Builder&#41;](../report-builder/report-design-view-report-builder.md) </span></span>  
 <span data-ttu-id="ba84b-151">[共有データセット デザイン ビュー (レポート ビルダー)](../report-builder/shared-dataset-design-view-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="ba84b-151">[Shared Dataset Design View &#40;Report Builder&#41;](../report-builder/shared-dataset-design-view-report-builder.md) </span></span>  
 [<span data-ttu-id="ba84b-152">Reporting Services クエリ デザイナー</span><span class="sxs-lookup"><span data-stu-id="ba84b-152">Reporting Services Query Designers</span></span>](../reporting-services-query-designers.md)  
  
  
