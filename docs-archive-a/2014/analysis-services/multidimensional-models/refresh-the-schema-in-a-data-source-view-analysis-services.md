---
title: データソースビューでのスキーマの更新 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data source views [Analysis Services], schema updates
- refreshing data source views
- data source views [Analysis Services], refreshing
ms.assetid: 634b0504-1437-43e7-8ac7-3248ac7989a3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 808f6ea431592aaecadf6f20a1ae16850cdb20e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633402"
---
# <a name="refresh-the-schema-in-a-data-source-view-analysis-services"></a><span data-ttu-id="8df11-102">データ ソース ビューでのスキーマの更新 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="8df11-102">Refresh the Schema in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="8df11-103">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] プロジェクトまたはデータベースでデータ ソース ビュー (DSV) を定義した後に、基になるデータ ソースのスキーマが変更される場合があります。</span><span class="sxs-lookup"><span data-stu-id="8df11-103">After defining a data source view (DSV) in an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] project or database, the schema in an underlying data source may change.</span></span> <span data-ttu-id="8df11-104">開発プロジェクトでは、これらの変更は自動的に検出または更新されません。</span><span class="sxs-lookup"><span data-stu-id="8df11-104">These changes are not automatically detected or updated in a development project.</span></span> <span data-ttu-id="8df11-105">さらに、プロジェクトをサーバーに配置した場合に、Analysis Services が外部データ ソースに接続できないという処理エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="8df11-105">Moreover, if you deployed the project to a server, you will now encounter processing errors if Analysis Services can no longer connect to the external data source.</span></span>

 <span data-ttu-id="8df11-106">外部データ ソースと一致するように DSV を更新するには、Business Intelligence Development Studio (BIDS) で DSV を更新します。</span><span class="sxs-lookup"><span data-stu-id="8df11-106">To update the DSV so that it matches the external data source, you can refresh the DSV in Business Intelligence Development Studio (BIDS).</span></span> <span data-ttu-id="8df11-107">DSV を更新すると、DSV の基になる外部データ ソースへの変更が検出され、外部データ ソース内の追加と削除を列挙した変更リストが構築されます。</span><span class="sxs-lookup"><span data-stu-id="8df11-107">Refreshing the DSV detects changes to the external data sources upon which the DSV is based, and builds a change list that enumerates the additions or deletions in the external data source.</span></span> <span data-ttu-id="8df11-108">その後、再配置を行う DSV への一連の変更を、基になるデータ ソースに適用できます。</span><span class="sxs-lookup"><span data-stu-id="8df11-108">You can then apply the set of changes to the DSV that will realign it to the underlying data source.</span></span> <span data-ttu-id="8df11-109">DSV を使用するプロジェクトでキューブとディメンションをさらに更新するために、追加の作業が必要になることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="8df11-109">Note that additional work is often required to further update the cubes and dimensions in the project that use the DSV.</span></span>

 <span data-ttu-id="8df11-110">このトピックのセクションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8df11-110">This topic includes the following sections:</span></span>

 [<span data-ttu-id="8df11-111">更新でサポートされている変更</span><span class="sxs-lookup"><span data-stu-id="8df11-111">Changes Supported in Refresh</span></span>](#bkmk_changlist)

 [<span data-ttu-id="8df11-112">SQL Server Data Tools での DSV の更新</span><span class="sxs-lookup"><span data-stu-id="8df11-112">Refresh a DSV in SQL Server Data Tools</span></span>](#bkmk_DSVrefresh)

##  <a name="changes-supported-in-refresh"></a><a name="bkmk_changlist"></a><span data-ttu-id="8df11-113">更新でサポートされている変更</span><span class="sxs-lookup"><span data-stu-id="8df11-113">Changes Supported in Refresh</span></span>
 <span data-ttu-id="8df11-114">DSV 更新には、次のアクションを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="8df11-114">DSV Refresh can include any of the following the actions:</span></span>

-   <span data-ttu-id="8df11-115">テーブル、列、およびリレーションシップの削除。</span><span class="sxs-lookup"><span data-stu-id="8df11-115">Deletion of tables, columns, and relationships</span></span>

-   <span data-ttu-id="8df11-116">列およびリレーションシップの追加 (DSV に既に含まれているテーブルに適用)。</span><span class="sxs-lookup"><span data-stu-id="8df11-116">Addition of columns and relationships, as applied to tables that are already included in the DSV</span></span>

-   <span data-ttu-id="8df11-117">新しい一意の制約の追加。</span><span class="sxs-lookup"><span data-stu-id="8df11-117">Addition of new unique constraints.</span></span> <span data-ttu-id="8df11-118">DSV のテーブルに論理主キーが存在し、データ ソースのテーブルに物理キーが追加されると、論理キーが削除され、物理キーで置換されます。</span><span class="sxs-lookup"><span data-stu-id="8df11-118">If a logical primary key exists for a table in the DSV and a physical key is added to the table in the data source, the logical key is removed and replaced by the physical key.</span></span>

 <span data-ttu-id="8df11-119">更新によって DSV に新しいテーブルが追加されることはありません。</span><span class="sxs-lookup"><span data-stu-id="8df11-119">Refresh never adds new tables to a DSV.</span></span> <span data-ttu-id="8df11-120">新しいテーブルを追加する場合は、手動で追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8df11-120">If you want to add a new table, you must add it manually.</span></span> <span data-ttu-id="8df11-121">詳細については、「 [データ ソース ビューでのテーブルまたはビューの追加または削除 (Analysis Services)](adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)内のソリューション エクスプローラーでデータ ソース ビュー ウィザードを実行します。</span><span class="sxs-lookup"><span data-stu-id="8df11-121">For more information, see [Adding or Removing Tables or Views in a Data Source View &#40;Analysis Services&#41;](adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md).</span></span>

##  <a name="refresh-a-dsv-in-sql-server-data-tools"></a><a name="bkmk_DSVrefresh"></a><span data-ttu-id="8df11-122">SQL Server Data Tools で DSV を更新する</span><span class="sxs-lookup"><span data-stu-id="8df11-122">Refresh a DSV in SQL Server Data Tools</span></span>
 <span data-ttu-id="8df11-123">DSV を更新するには、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーで [DSV] をダブルクリックしてから、[データ ソース ビューを最新状態に更新] をクリックするか、[データ ソース ビュー] メニューの **[更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8df11-123">To refresh a DSV, double-click the DSV from Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], and then click the Refresh Data Source View button or choose **Refresh** from the Data Source View menu.</span></span>

 <span data-ttu-id="8df11-124">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、更新中、基になるリレーショナル データ ソースのすべてにクエリして、DSV に含まれているテーブルやビューが変更されたかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="8df11-124">During refresh, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] queries all underlying relational data sources to determine whether there have been changes in tables/views which are included in the DSV.</span></span> <span data-ttu-id="8df11-125">基になるデータ ソースのすべてに接続を確立できる場合は、変更されていれば **[データ ソース ビューを最新状態に更新]** ダイアログ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8df11-125">If connections can be established to all underlying data sources and there have been any changes, you will see them in the **Refresh Data Source View** dialog box.</span></span>

 <span data-ttu-id="8df11-126">![[データソースビューの更新] ダイアログボックス](../media/ssas-olapdsv-refresh.gif "[データ ソース ビューを最新状態に更新] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="8df11-126">![Refresh Data Source View dialog box](../media/ssas-olapdsv-refresh.gif "Refresh Data Source View dialog box")</span></span>

 <span data-ttu-id="8df11-127">ダイアログ ボックスには、DSV で削除または追加されるテーブル、列、制約、およびリレーションシップが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="8df11-127">The dialog box lists tables, columns, constraints, and relationships that will be deleted or added in the DSV.</span></span> <span data-ttu-id="8df11-128">また、レポートには、正常に準備できない名前付きクエリまたは計算も一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="8df11-128">The report also lists any named query or calculation that cannot be successfully prepared.</span></span> <span data-ttu-id="8df11-129">影響を受けたオブジェクトは、テーブルで入れ子になった列およびリレーションシップと、オブジェクトごとに示されている変更の種類 (削除または追加) と共に、ツリー ビューに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="8df11-129">The affected objects are listed in a tree view with columns and relationships nested under tables and the type of change (deletion or addition) indicated for each object.</span></span> <span data-ttu-id="8df11-130">標準的なデータ ソース ビューのオブジェクト アイコンは、影響を受けたオブジェクトの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="8df11-130">The standard data source view object icons indicate the type of object affected.</span></span>

 <span data-ttu-id="8df11-131">更新は、基になるオブジェクトの名前に完全に基づいています。</span><span class="sxs-lookup"><span data-stu-id="8df11-131">Refresh is based completely on the names of the underlying objects.</span></span> <span data-ttu-id="8df11-132">そのため、基になるオブジェクトの名前がデータソースで変更された場合、データソースビューデザイナーは、名前が変更されたオブジェクトを、削除と加算という2つの別個の操作として扱います。</span><span class="sxs-lookup"><span data-stu-id="8df11-132">Therefore, if an underlying object is renamed in the data source, Data Source View Designer treats the renamed object as two separate operations-a deletion and an addition.</span></span> <span data-ttu-id="8df11-133">この場合、名前が変更されたオブジェクトをデータ ソース ビューに手動で追加し直すことが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="8df11-133">In this case, you may have to manually add the renamed object back to the data source view.</span></span> <span data-ttu-id="8df11-134">また、リレーションシップまたは論理主キーを再作成することが必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="8df11-134">You may also have to re-create relationships or logical primary keys.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="8df11-135">データ ソースでテーブルの名前が変更されたことがわかっている場合は、 **[テーブルの置換]** コマンドを使用して、データ ソース ビューを更新する前に、テーブルを名前変更後のテーブルで置換することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="8df11-135">If you are aware that a table has been renamed in a data source, you may want to use the **Replace Table** command to replace the table with the renamed table before you refresh the data source view.</span></span> <span data-ttu-id="8df11-136">詳細については、「[データ ソース ビュー内のテーブルまたは名前付きクエリの置換 (Analysis Services)](replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8df11-136">For more information, see [Replace a Table or a Named Query in a Data Source View &#40;Analysis Services&#41;](replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services.md).</span></span>

 <span data-ttu-id="8df11-137">レポートの確認後は、変更内容を受け入れるか、更新を取り消して変更内容を拒否することができます。</span><span class="sxs-lookup"><span data-stu-id="8df11-137">After you examine the report, you can either accept the changes or cancel the update to reject any changes.</span></span> <span data-ttu-id="8df11-138">すべての変更はまとめて受け入れるか拒否する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8df11-138">All changes must be accepted or rejected together.</span></span> <span data-ttu-id="8df11-139">一覧の個々のアイテムを選択することはできません。</span><span class="sxs-lookup"><span data-stu-id="8df11-139">You cannot choose individual items in the list.</span></span> <span data-ttu-id="8df11-140">また、変更内容のレポートを保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="8df11-140">You can also save a report of the changes.</span></span>

## <a name="see-also"></a><span data-ttu-id="8df11-141">参照</span><span class="sxs-lookup"><span data-stu-id="8df11-141">See Also</span></span>
 [<span data-ttu-id="8df11-142">多次元モデル内のデータ ソース ビュー</span><span class="sxs-lookup"><span data-stu-id="8df11-142">Data Source Views in Multidimensional Models</span></span>](data-source-views-in-multidimensional-models.md)


