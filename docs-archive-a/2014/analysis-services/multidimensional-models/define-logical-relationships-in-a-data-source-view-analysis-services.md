---
title: データソースビューでの論理リレーションシップの定義 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- adding relationships
- relationships [Analysis Services], data source views
- data source views [Analysis Services], relationships
ms.assetid: a20d6dae-e769-4131-8a59-7ef56f174220
author: minewiskan
ms.author: owend
ms.openlocfilehash: c46c2b360a4528aeb0eb88348d0d1242b22d8ef5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641347"
---
# <a name="define-logical-relationships-in-a-data-source-view-analysis-services"></a><span data-ttu-id="e661e-102">データ ソース ビューでの論理リレーションシップの定義 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="e661e-102">Define Logical Relationships in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="e661e-103">データ ソース ビュー ウィザードとデータ ソース ビュー デザイナーでは、データ ソース ビュー (DSV) に追加されたテーブル間のリレーションシップが、基になるデータベース リレーションシップまたは指定した名前一致条件に基づき、自動的に定義されます。</span><span class="sxs-lookup"><span data-stu-id="e661e-103">The Data Source View Wizard and Data Source View Designer automatically define relationships between tables added to a data source view (DSV) based on underlying database relationships or name matching criteria you specify.</span></span>  
  
 <span data-ttu-id="e661e-104">複数のデータ ソースのデータを使用する場合は、データ ソース ビューの論理リレーションシップを手動で定義して、自動的に定義されたリレーションシップを補完する必要があることもあります。</span><span class="sxs-lookup"><span data-stu-id="e661e-104">In cases where you are working with data from multiple data sources, you may need to manually define logical relationships in the DSV to supplement those relationships that are defined automatically.</span></span> <span data-ttu-id="e661e-105">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、ファクト テーブルやディメンション テーブルの識別、基になるデータ ソースからデータやメタデータを取得するためのクエリの作成、および高度なビジネス インテリジェンス機能の利用において、リレーションシップが必要となります。</span><span class="sxs-lookup"><span data-stu-id="e661e-105">Relationships are required in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to identify fact and dimension tables, to construct queries for retrieving data and metadata from underlying data sources, and to take advantage of advanced business intelligence features.</span></span>  
  
 <span data-ttu-id="e661e-106">データ ソース ビュー デザイナーでは、次の種類のリレーションシップを定義できます。</span><span class="sxs-lookup"><span data-stu-id="e661e-106">You can define the following types of relationships in Data Source View Designer:</span></span>  
  
-   <span data-ttu-id="e661e-107">同じデータ ソース内のテーブル間のリレーションシップ</span><span class="sxs-lookup"><span data-stu-id="e661e-107">A relationship from one table to another table in the same data source.</span></span>  
  
-   <span data-ttu-id="e661e-108">親子リレーションシップのように、あるテーブルからそのテーブル自体へのリレーションシップ</span><span class="sxs-lookup"><span data-stu-id="e661e-108">A relationship from one table to itself, as in a parent-child relationship.</span></span>  
  
-   <span data-ttu-id="e661e-109">データ ソース内のテーブルから別のデータ ソース内のテーブルへのリレーションシップ</span><span class="sxs-lookup"><span data-stu-id="e661e-109">A relationship from one table in a data source to another table in a different data source.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e661e-110">データ ソース ビューで定義されているリレーションシップは論理的なもので、基になるデータ ソースで定義されている実際のリレーションシップを反映していない場合があります。</span><span class="sxs-lookup"><span data-stu-id="e661e-110">The relationships defined in a DSV are logical and may not reflect the actual relationships defined in the underlying data source.</span></span> <span data-ttu-id="e661e-111">データ ソース ビュー デザイナーでは、基になるデータ ソースに存在しないリレーションシップを作成できます。また、データ ソース ビュー デザイナーで作成したリレーションシップを、基になるデータ ソースの既存の外部キー リレーションシップから削除することができます。</span><span class="sxs-lookup"><span data-stu-id="e661e-111">You can create relationships in Data Source View Designer that do not exist in the underlying data source, and remove relationships created by Data Source View Designer from existing foreign key relationships in the underlying data source.</span></span>  
  
 <span data-ttu-id="e661e-112">リレーションシップには方向があります。</span><span class="sxs-lookup"><span data-stu-id="e661e-112">Relationships are directed.</span></span> <span data-ttu-id="e661e-113">基になる列のそれぞれの値に対して、対象になる列に対応する値が存在します。</span><span class="sxs-lookup"><span data-stu-id="e661e-113">For every value in the source column, there is a corresponding value in the destination column.</span></span> <span data-ttu-id="e661e-114">**[ダイアグラム]** ペインに表示されるダイアグラムなどのデータ ソース ビュー ダイアグラムでは、2 つのテーブル間の線上にある矢印が、リレーションシップの方向を示します。</span><span class="sxs-lookup"><span data-stu-id="e661e-114">In a data source view diagram, such as the diagrams displayed in the **Diagram** pane, an arrow on the line between two tables indicates the direction of the relationship.</span></span>  
  
 <span data-ttu-id="e661e-115">このトピックのセクションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e661e-115">This topic includes the following sections:</span></span>  
  
 [<span data-ttu-id="e661e-116">テーブル、名前付きクエリ、またはビュー間のリレーションシップを追加するには</span><span class="sxs-lookup"><span data-stu-id="e661e-116">To add a relationship between tables, named queries, or views</span></span>](#bkmk_addRel)  
  
 [<span data-ttu-id="e661e-117">ダイアグラムペインでリレーションシップを表示または変更するには</span><span class="sxs-lookup"><span data-stu-id="e661e-117">To view or modify a relationship in the Diagram pane</span></span>](#bkmk_diagrampane)  
  
 <span data-ttu-id="e661e-118">[[テーブル] ペインでリレーションシップを表示または変更するには](#bkmk_tablespane)</span><span class="sxs-lookup"><span data-stu-id="e661e-118">[To view or modify a relationship in the Tables pane](#bkmk_tablespane)</span></span>  
  
##  <a name="to-add-a-relationship-between-tables-named-queries-or-views"></a><a name="bkmk_addRel"></a><span data-ttu-id="e661e-119">テーブル、名前付きクエリ、またはビューの間にリレーションシップを追加するには</span><span class="sxs-lookup"><span data-stu-id="e661e-119">To add a relationship between tables, named queries, or views</span></span>  
  
1.  <span data-ttu-id="e661e-120">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でプロジェクトを開くか、論理リレーションシップを追加するデータ ソース ビューが含まれているデータベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="e661e-120">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you wish to add a logical relationship.</span></span>  
  
2.  <span data-ttu-id="e661e-121">ソリューション エクスプローラーで **[データ ソース ビュー]** フォルダーを展開し、データ ソース ビューをダブルクリックして **データ ソース ビュー デザイナー**を開きます。</span><span class="sxs-lookup"><span data-stu-id="e661e-121">In Solution Explorer, expand the **Data Source Views** folder, then double-click the data source view to open it in **Data Source View Designer**.</span></span>  
  
3.  <span data-ttu-id="e661e-122">**[テーブル]** ペインで、リレーションシップの追加先のテーブル、名前付きクエリ、またはビューを右クリックし、 **[新しいリレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e661e-122">Right-click the table, named query or view to which you want to add a relationship in either the **Tables** pane and then click **New Relationship**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e661e-123">テーブル、ビュー、または名前付きクエリを検索するには、 **[データ ソース ビュー]** メニューをクリックするか、 **テーブル** ペインまたは **ダイアグラム** ペインの空いている領域を右クリックして、 **[テーブルの検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e661e-123">To locate a table, view or named query, you can use the **Find Table** option by either clicking the **Data Source View** menu or right-clicking in an open area of the **Tables** or **Diagram** panes.</span></span>  
  
4.  <span data-ttu-id="e661e-124">**[リレーションシップの指定]** ダイアログ ボックスで、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="e661e-124">In the **Specify Relationship** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="e661e-125">**[作成元 (外部キー) テーブル]** の一覧で、該当するテーブル、名前付きクエリ、またはビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="e661e-125">Select the appropriate table, named query, or view in the **Source (foreign key) table** list.</span></span>  
  
    2.  <span data-ttu-id="e661e-126">**[作成元 (主キー) テーブル]** の一覧で、該当するテーブル、名前付きクエリ、またはビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="e661e-126">Select the appropriate table, named query, or view in the **Destination (primary key) table** lists.</span></span>  
  
    3.  <span data-ttu-id="e661e-127">**[基になる列]** および **[対象になる列]** 一覧から列を選択して、2 つのテーブル間のリレーションシップを作成します。</span><span class="sxs-lookup"><span data-stu-id="e661e-127">Select columns from the **Source Columns** and **Destination Columns** lists to create a relationship between the two tables.</span></span>  
  
         <span data-ttu-id="e661e-128">基になるテーブル、ビュー、または名前付きクエリのデータをサンプリングすることで、誤った方向 (外部キーから主キーではなく、主キーから外部キー) にリレーションシップを定義したことが [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] によって検出された場合は、順序を逆にするように要求されます。</span><span class="sxs-lookup"><span data-stu-id="e661e-128">If [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] detects, by sampling the data in the underlying table, view, or named query, that you have defined the relationship in the wrong direction (from the primary key to the foreign key rather than from the foreign key to the primary key), you will be prompted to reverse the order.</span></span> <span data-ttu-id="e661e-129">順序を逆にするには、 **[反転]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e661e-129">To quickly reverse the order, click **Reverse**.</span></span>  
  
         <span data-ttu-id="e661e-130">選択した列にリレーションシップが既に存在することが [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] によって検出された場合は、メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e661e-130">If [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] detects that a relationship already exists for the columns you have selected, you will be prompted.</span></span> <span data-ttu-id="e661e-131">リレーションシップを重複して定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="e661e-131">You cannot define duplicate relationships.</span></span>  
  
    4.  <span data-ttu-id="e661e-132">必要に応じて、 **[説明]** ボックスにリレーションシップの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="e661e-132">Optionally, in the **Description** box, type a description for the relationship.</span></span>  
  
##  <a name="to-view-or-modify-a-relationship-in-the-diagram-pane"></a><a name="bkmk_diagrampane"></a> <span data-ttu-id="e661e-133">[ダイアグラム] ペインでリレーションシップを表示または変更するには</span><span class="sxs-lookup"><span data-stu-id="e661e-133">To view or modify a relationship in the Diagram pane</span></span>  
  
-   <span data-ttu-id="e661e-134">**データ ソース ビュー デザイナー** の **[ダイアグラム]** ペインで、表示するリレーションシップを右クリックし、 **[リレーションシップの編集]** をクリックするか、リレーションシップの矢印をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="e661e-134">In the **Diagram** pane in **Data Source View Designer**, right-click the relationship that you want to view and click **Edit Relationship** (or simply double-click the relationship arrow).</span></span>  <span data-ttu-id="e661e-135">リレーションシップを変更するには、 **[リレーションシップの編集]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="e661e-135">Use the **Edit Relationship** dialog box to modify the relationship.</span></span>  
  
##  <a name="to-view-or-modify-a-relationship-in-the-tables-pane"></a><a name="bkmk_tablespane"></a> <span data-ttu-id="e661e-136">[テーブル] ペインでリレーションシップを表示または変更するには</span><span class="sxs-lookup"><span data-stu-id="e661e-136">To view or modify a relationship in the Tables pane</span></span>  
  
1.  <span data-ttu-id="e661e-137">**データ ソース ビュー デザイナー** の **[テーブル]** ペインで、表示または変更するリレーションシップを含むテーブル、ビュー、または名前付きクエリを検索し、展開します。</span><span class="sxs-lookup"><span data-stu-id="e661e-137">In the **Tables** pane in **Data Source View Designer**, locate and then expand the table, view or named query containing the relationship that you wish to view or modify.</span></span>  
  
2.  <span data-ttu-id="e661e-138">**[リレーションシップ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="e661e-138">Expand the **Relationships** folder.</span></span>  <span data-ttu-id="e661e-139">選択したテーブル、ビュー、または名前付きクエリと他のテーブル、ビュー、および名前付きクエリ間のリレーションシップが、リレーションシップ列と共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e661e-139">The relationships between the selected table, view or named query and other tables, views and named queries appear with the relationship column listed.</span></span>  
  
3.  <span data-ttu-id="e661e-140">変更するリレーションシップを右クリックし、 **[リレーションシップの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e661e-140">Right-click the relationship you want to modify, and then click **Edit Relationship**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e661e-141">参照</span><span class="sxs-lookup"><span data-stu-id="e661e-141">See Also</span></span>  
 [<span data-ttu-id="e661e-142">多次元モデル内のデータ ソース ビュー</span><span class="sxs-lookup"><span data-stu-id="e661e-142">Data Source Views in Multidimensional Models</span></span>](data-source-views-in-multidimensional-models.md)  
  
  
