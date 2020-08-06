---
title: 多対多リレーションシップの定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7bebb174-148c-4cbb-a285-2f6d536a16d5
author: minewiskan
ms.author: owend
ms.openlocfilehash: fb4e18831ae23b8cf1f0702b357672f7520478a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714750"
---
# <a name="defining-a-many-to-many-relationship"></a><span data-ttu-id="412cb-102">多対多関係の定義</span><span class="sxs-lookup"><span data-stu-id="412cb-102">Defining a Many-to-Many Relationship</span></span>
  <span data-ttu-id="412cb-103">通常、ディメンションを定義する場合、1 つのディメンション メンバーは多数のファクトに結合できますが、各ファクトを結合できるのは 1 つのディメンションのみです。</span><span class="sxs-lookup"><span data-stu-id="412cb-103">When you define a dimension, typically each fact joins to one and only one dimension member, whereas a single dimension member can be associated with many different facts.</span></span> <span data-ttu-id="412cb-104">たとえば、各顧客は多数の商品を注文できますが、それぞれの注文は 1 人の顧客に所属します。</span><span class="sxs-lookup"><span data-stu-id="412cb-104">For example, each customer can have many orders but each order belongs to a single customer.</span></span> <span data-ttu-id="412cb-105">リレーショナルデータベースの用語では、これを*一対多のリレーションシップ*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="412cb-105">In relational database terminology, this is referred to as a *one-to-many relationship*.</span></span> <span data-ttu-id="412cb-106">しかし、1 つのファクトが複数のディメンション メンバーに結合する場合があります。</span><span class="sxs-lookup"><span data-stu-id="412cb-106">However, sometimes a single fact can join to multiple dimension members.</span></span> <span data-ttu-id="412cb-107">リレーショナル データベース用語では、これを *多対多のリレーションシップ*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="412cb-107">In relational database terminology, this is referred to as a *many-to-many relationship*.</span></span> <span data-ttu-id="412cb-108">たとえば、1 回の購入には複数の購入動機があることが考えられ、また、1 つの購入動機が複数の購入に結び付く (関連付けられる) ことがあります。</span><span class="sxs-lookup"><span data-stu-id="412cb-108">For example, a customer may have multiple reasons for making a purchase, and a purchase reason can be associated with multiple purchases.</span></span> <span data-ttu-id="412cb-109">結合テーブルは、各購入に関連する購入動機の定義に使用されます。</span><span class="sxs-lookup"><span data-stu-id="412cb-109">A join table is used to define the sales reasons that relate to each purchase.</span></span> <span data-ttu-id="412cb-110">このようなリレーションシップから作成された Sales Reason ディメンションには、1 回の販売取り引きに関連付けられるメンバーが複数存在します。</span><span class="sxs-lookup"><span data-stu-id="412cb-110">A Sales Reason dimension constructed from such relationships would then have multiple members that relate to a single sales transaction.</span></span> <span data-ttu-id="412cb-111">多対多のディメンションは、従来のスター スキーマ以上にディメンショナル モデルを展開し、ディメンションが直接ファクト テーブルに関連付けられていなくても複雑な分析を可能にします。</span><span class="sxs-lookup"><span data-stu-id="412cb-111">Many-to-many dimensions expand the dimensional model beyond the classic star schema and support complex analytics when dimensions are not directly related to a fact table.</span></span>

 <span data-ttu-id="412cb-112">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]では、ディメンションとメジャー グループの間に多対多のリレーションシップを定義します。この定義は、ディメンション テーブルに関連付けられる中間ファクト テーブルを指定することにより行われます。</span><span class="sxs-lookup"><span data-stu-id="412cb-112">In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], you define a many-to-many relationship between a dimension and a measure group by specifying an intermediate fact table that is joined to the dimension table.</span></span> <span data-ttu-id="412cb-113">その後、中間ファクト テーブルは、ファクト テーブルを関連付ける中間ディメンション テーブルに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="412cb-113">An intermediate fact table is joined, in turn, to an intermediate dimension table to which the fact table is joined.</span></span> <span data-ttu-id="412cb-114">中間ファクト テーブルとリレーションシップ内のディメンション テーブル、および中間ファクトと中間ディメンション間の多対多のリレーションシップにより、そのリレーションシップに指定されている主ディメンションのメンバーおよびメジャー グループ内のグループとの間に多対多のリレーションシップが作成されます。</span><span class="sxs-lookup"><span data-stu-id="412cb-114">The many-to-many relationships between the intermediate fact table and both the dimension tables in the relationship and the intermediate dimension creates the many-to-many relationships between members of the primary dimension and measures in the measure group that is specified by the relationship.</span></span> <span data-ttu-id="412cb-115">中間メジャー グループを通じてディメンションとメジャー グループ間の多対多のリレーションシップを定義するには、中間メジャー グループは 1 つ以上のディメンションを元のメジャー グループと共有する必要があります。</span><span class="sxs-lookup"><span data-stu-id="412cb-115">In order to define a many-to-many relationship between a dimension and a measure group through an intermediate measure group, the intermediate measure group must share one or more dimensions with the original measure group.</span></span>

 <span data-ttu-id="412cb-116">多対多のディメンションでは値は個別に集計され、すべてのメンバーに対して 2 回以上集計されることはありません。</span><span class="sxs-lookup"><span data-stu-id="412cb-116">With a many-to-many dimension, values are distinct summed, which means that they do not aggregate more than once to the All member.</span></span>

> [!NOTE]
>  <span data-ttu-id="412cb-117">多対多のディメンションリレーションシップをサポートするには、関連するすべてのテーブル間のデータソースビューで主キーと外部キーのリレーションシップを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="412cb-117">In order to support a many-to-many dimension relationship, a primary key-foreign key relationship must be defined in the data source view between all the tables that are involved.</span></span> <span data-ttu-id="412cb-118">このようにしないと、キューブ デザイナーの **[ディメンションの使用法]** タブでリレーションシップを確立するときに正しいメジャー グループを選択できません。</span><span class="sxs-lookup"><span data-stu-id="412cb-118">Otherwise, you will not be able to select the correct intermediate measure group when you establish the relationship in the **Dimension Usage** tab of Cube Designer.</span></span>

 <span data-ttu-id="412cb-119">詳細については、「 [ディメンション リレーションシップ](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)」および「 [多対多のリレーションシップと多対多のリレーションシップのプロパティの定義](multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="412cb-119">For more information, see [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), and [Define a Many-to-Many Relationship and Many-to-Many Relationship Properties](multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md).</span></span>

 <span data-ttu-id="412cb-120">このトピックの実習では、まず、Sales Reasons ディメンションと Sales Reasons メジャー グループを作成します。次に、Sales Reasons メジャー グループを介して、Sales Reasons ディメンションと Internet Sales メジャー グループの間に多対多のリレーションシップを定義します。</span><span class="sxs-lookup"><span data-stu-id="412cb-120">In the tasks in this topic, you define the Sales Reasons dimension and the Sales Reasons measure group, and you define a many-to-many relationship between the Sales Reasons dimension and the Internet Sales measure group through the Sales Reasons measure group.</span></span>

## <a name="adding-required-tables-to-the-data-source-view"></a><span data-ttu-id="412cb-121">データ ソース ビューへの必要なテーブルの追加</span><span class="sxs-lookup"><span data-stu-id="412cb-121">Adding Required Tables to the Data Source View</span></span>

1.  <span data-ttu-id="412cb-122">データ ソース ビュー デザイナーを開き、 **Adventure Works DW 2012** データ ソース ビューを表示します。</span><span class="sxs-lookup"><span data-stu-id="412cb-122">Open Data Source View Designer for the **Adventure Works DW 2012** data source view.</span></span>

2.  <span data-ttu-id="412cb-123">[**ダイアグラムオーガナイザー** ] ペイン内の任意の場所を右クリックし、[**新しいダイアグラム**] をクリックし `Internet Sales Order Reasons` て、この新しいダイアグラムの名前としてを指定します。</span><span class="sxs-lookup"><span data-stu-id="412cb-123">Right-click anywhere in the **Diagram Organizer** pane, click **New Diagram**, and specify `Internet Sales Order Reasons` as the name for this new diagram.</span></span>

3.  <span data-ttu-id="412cb-124">**[テーブル]** ペインの **[InternetSales]** テーブルを、 **[ダイアグラム]** ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="412cb-124">Drag the **InternetSales** table to the **Diagram** pane from the **Tables** pane.</span></span>

4.  <span data-ttu-id="412cb-125">**[ダイアグラム]** ペイン内を右クリックし、 **[テーブルの追加と削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-125">Right-click anywhere in the **Diagram** pane, and then click **Add/Remove Tables**.</span></span>

5.  <span data-ttu-id="412cb-126">**[テーブルの追加と削除]** ダイアログ ボックスで、 **[含まれているオブジェクト]** ボックスの一覧に **DimSalesReason** テーブルと **FactInternetSalesReason** テーブルを追加し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-126">In the **Add/Remove Tables** dialog box, add the **DimSalesReason** table and the **FactInternetSalesReason** table to the **Included objects** list, and then click **OK**.</span></span>

     <span data-ttu-id="412cb-127">関連するテーブル間の主キーと外部キーのリレーションシップは、基になるリレーショナルデータベースで定義されているため、自動的に確立されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="412cb-127">Notice that the primary key-foreign key relationships between the tables that are involved are established automatically because those relationships are defined in the underlying relational database.</span></span> <span data-ttu-id="412cb-128">これらのリレーションシップが基のリレーショナル データベースに定義されていない場合は、データ ソース ビューで定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="412cb-128">If these relationships were not defined in the underlying relational database, you would have to define them in the data source view.</span></span>

6.  <span data-ttu-id="412cb-129">**[書式]** メニューで **[自動レイアウト]** をポイントし、 **[ダイアグラム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-129">On the **Format** menu, point to **Auto Layout**, and then click **Diagram**.</span></span>

7.  <span data-ttu-id="412cb-130">プロパティウィンドウで、 **DimSalesReason**テーブルの**friendlyname**プロパティをに変更し、 `SalesReason` **FactInternetSalesReason**テーブルの**friendlyname**プロパティをに変更し `InternetSalesReason` ます。</span><span class="sxs-lookup"><span data-stu-id="412cb-130">In the Properties window, change the **FriendlyName** property of the **DimSalesReason** table to `SalesReason`, and then change the **FriendlyName** property of the **FactInternetSalesReason** table to `InternetSalesReason`.</span></span>

8.  <span data-ttu-id="412cb-131">**[テーブル]** ペインで **[InternetSalesReason (dbo.FactInternetSalesReason)]** を展開し、 **[SalesOrderNumber]** をクリックします。次に、[プロパティ] ウィンドウで、このデータ列の **DataType** プロパティを確認します。</span><span class="sxs-lookup"><span data-stu-id="412cb-131">In the **Tables** pane, expand **InternetSalesReason (dbo.FactInternetSalesReason)**, click **SalesOrderNumber**, and then review the **DataType** property for this data column in the Properties window.</span></span>

     <span data-ttu-id="412cb-132">**[SalesOrderNumber]** 列のデータ型は文字列になっています。</span><span class="sxs-lookup"><span data-stu-id="412cb-132">Notice that the data type for the **SalesOrderNumber** column is a string data type.</span></span>

9. <span data-ttu-id="412cb-133">テーブル内の他の列のデータ型を確認し `InternetSalesReason` ます。</span><span class="sxs-lookup"><span data-stu-id="412cb-133">Review the data types for the other columns in the `InternetSalesReason` table.</span></span>

     <span data-ttu-id="412cb-134">このテーブルでは、他の 2 つの列のデータ型が数値型になっています。</span><span class="sxs-lookup"><span data-stu-id="412cb-134">Notice that the data types for the other two columns in this table are numeric data types.</span></span>

10. <span data-ttu-id="412cb-135">**[テーブル]** ペインで **[InternetSalesReason (dbo.FactInternetSalesReason)]** を右クリックし、 **[データの探索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-135">In the **Tables** pane, right-click **InternetSalesReason (dbo.FactInternetSalesReason)**, and then click **Explore Data**.</span></span>

     <span data-ttu-id="412cb-136">次の図のように、各並び順の行番号では、その行の商品の購入動機がキー値により識別されます。</span><span class="sxs-lookup"><span data-stu-id="412cb-136">Notice that, for each line number within each order, a key value identifies the sales reason for the purchase of that line item, as shown in the following image.</span></span>

     <span data-ttu-id="412cb-137">![商品の購入動機を識別するためのキー値](../../2014/tutorials/media/l5-many-to-many-1.gif "商品の購入動機を識別するためのキー値")</span><span class="sxs-lookup"><span data-stu-id="412cb-137">![Key value to identify sales reason for purchases](../../2014/tutorials/media/l5-many-to-many-1.gif "Key value to identify sales reason for purchases")</span></span>

## <a name="defining-the-intermediate-measure-group"></a><span data-ttu-id="412cb-138">中間メジャー グループの定義</span><span class="sxs-lookup"><span data-stu-id="412cb-138">Defining the Intermediate Measure Group</span></span>

1.  <span data-ttu-id="412cb-139">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーに切り替え、 **[キューブ構造]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-139">Switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Cube Structure** tab.</span></span>

2.  <span data-ttu-id="412cb-140">**[メジャー]** ペイン内を右クリックし、 **[新しいメジャー グループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-140">Right-click anywhere in the **Measures** pane, and then click **New Measure Group**.</span></span> <span data-ttu-id="412cb-141">詳細については、「 [多次元モデル内のメジャーおよびメジャー グループの作成](multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="412cb-141">For more information, see [Create Measures and Measure Groups in Multidimensional Models](multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md).</span></span>

3.  <span data-ttu-id="412cb-142">[**新しいメジャーグループ**] ダイアログボックスで、[ `InternetSalesReason` **データソースビュー** ] ボックスの一覧から [テーブルの選択] を選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-142">In the **New Measure Group** dialog box, select `InternetSalesReason` in the **Select a table from the data source view** list, and then click **OK**.</span></span>

     <span data-ttu-id="412cb-143">**Internet Sales Reason** メジャー グループが **[メジャー]** ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="412cb-143">Notice that the **Internet Sales Reason** measure group now appears in the **Measures** pane.</span></span>

4.  <span data-ttu-id="412cb-144">**Internet Sales Reason** メジャー グループを展開します。</span><span class="sxs-lookup"><span data-stu-id="412cb-144">Expand the **Internet Sales Reason** measure group.</span></span>

     <span data-ttu-id="412cb-145">この新しいメジャー グループには、メジャー ( **Internet Sales Reason Count** メジャー) が 1 つだけ定義されています。</span><span class="sxs-lookup"><span data-stu-id="412cb-145">Notice that only a single measure is defined for this new measure group, the **Internet Sales Reason Count** measure.</span></span>

5.  <span data-ttu-id="412cb-146">**[Internet Sales Reason Count]** を選択し、[プロパティ] ウィンドウでこのメジャーのプロパティを確認します。</span><span class="sxs-lookup"><span data-stu-id="412cb-146">Select **Internet Sales Reason Count** and review the properties of this measure in the Properties window.</span></span>

     <span data-ttu-id="412cb-147">このメジャーの **AggregateFunction** プロパティは、 **Sum** ではなく、 **Count**として定義されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="412cb-147">Notice that the **AggregateFunction** property for this measure is defined as **Count** instead of **Sum**.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="412cb-148">でこのプロパティが **Count** になっているのは、基のデータ型が文字列データ型であるためです。</span><span class="sxs-lookup"><span data-stu-id="412cb-148">chose **Count** because the underlying data type is a string data type.</span></span> <span data-ttu-id="412cb-149">基のファクト テーブルの他の 2 つの列は、メジャーとしては選択されていません。これらは実際のメジャーではなく、数値キーであることを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] が検出したためです。</span><span class="sxs-lookup"><span data-stu-id="412cb-149">The other two columns in the underlying fact table were not selected as measures because [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] detected them as numeric keys instead of as actual measures.</span></span> <span data-ttu-id="412cb-150">準加法の動作の詳細については、「 [準加法の動作の定義](multidimensional-models/define-semiadditive-behavior.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="412cb-150">For more information, see [Define Semiadditive Behavior](multidimensional-models/define-semiadditive-behavior.md).</span></span>

6.  <span data-ttu-id="412cb-151">[プロパティ] ウィンドウで、 **Internet Sales Reason Count** メジャーの **Visible** プロパティを **False**に変更します。</span><span class="sxs-lookup"><span data-stu-id="412cb-151">In the Properties window, change the **Visible** property of the **Internet Sales Reason Count** measure to **False**.</span></span>

     <span data-ttu-id="412cb-152">このメジャーは、Internet Sales ディメンションの隣に定義する Sales Reason ディメンションを結合するためにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="412cb-152">This measure will only be used to join the Sales Reason dimension that you will define next to the Internet Sales measure group.</span></span> <span data-ttu-id="412cb-153">ユーザーがこのメジャーを直接表示することはありません。</span><span class="sxs-lookup"><span data-stu-id="412cb-153">Users will not browse this measure directly.</span></span>

     <span data-ttu-id="412cb-154">次の図は、 **Internet Sales Reason Count** メジャーのプロパティを示しています。</span><span class="sxs-lookup"><span data-stu-id="412cb-154">The following image shows the properties for the **Internet Sales Reason Count** measure.</span></span>

     <span data-ttu-id="412cb-155">![Internet Sales Reason Count メジャーのプロパティ](../../2014/tutorials/media/l5-many-to-many-2.gif "Internet Sales Reason Count メジャーのプロパティ")</span><span class="sxs-lookup"><span data-stu-id="412cb-155">![Properties for Internet Sales Reason Count measure](../../2014/tutorials/media/l5-many-to-many-2.gif "Properties for Internet Sales Reason Count measure")</span></span>

## <a name="defining-the-many-to-many-dimension"></a><span data-ttu-id="412cb-156">多対多ディメンションの定義</span><span class="sxs-lookup"><span data-stu-id="412cb-156">Defining the Many-to-Many Dimension</span></span>

1.  <span data-ttu-id="412cb-157">ソリューションエクスプローラーで、[**ディメンション**] を右クリックし、[**新しいディメンション**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-157">In Solution Explorer, right-click **Dimensions**, and then click **New Dimension**.</span></span>

2.  <span data-ttu-id="412cb-158">**[ディメンション ウィザードへようこそ]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-158">On the **Welcome to the Dimension Wizard** page, click **Next**.</span></span>

3.  <span data-ttu-id="412cb-159">**[作成方法の選択]** ページで **[既存のテーブルの使用]** オプションが選択されていることを確認し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-159">On the **Select Creation Method** page, verify that the **Use an existing table** option is selected, and then click **Next**.</span></span>

4.  <span data-ttu-id="412cb-160">**[基になる情報の指定]** ページで、 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012 データ ソース ビューが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="412cb-160">On the **Specify Source Information** page, verify that the [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012 data source view is selected.</span></span>

5.  <span data-ttu-id="412cb-161">[**メインテーブル**] ボックスの一覧で、を選択し `SalesReason` ます。</span><span class="sxs-lookup"><span data-stu-id="412cb-161">In the **Main table** list, select `SalesReason`.</span></span>

6.  <span data-ttu-id="412cb-162">**[キー列]** ボックスの一覧に **[SalesReasonKey]** が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="412cb-162">In the **Key columns** list, verify that **SalesReasonKey** is listed.</span></span>

7.  <span data-ttu-id="412cb-163">**[名前列]** ボックスの一覧から **[SalesReasonName]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="412cb-163">In the **Name column** list, select **SalesReasonName**.</span></span>

8.  <span data-ttu-id="412cb-164">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-164">Click **Next**.</span></span>

9. <span data-ttu-id="412cb-165">**[ディメンション属性の選択]** ページで、 **Sales Reason Key** 属性が自動的に選択されます。これは、この属性がキー属性であるためです。</span><span class="sxs-lookup"><span data-stu-id="412cb-165">On the **Select Dimension Attributes** page, the **Sales Reason Key** attribute is automatically selected because it is the key attribute.</span></span> <span data-ttu-id="412cb-166">**Sales Reason Reason Type**属性の横にあるチェックボックスをオンにし、その名前をに変更し `Sales Reason Type` て、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-166">Select the check box beside the **Sales Reason Reason Type** attribute, change its name to `Sales Reason Type`, and then click **Next**.</span></span>

10. <span data-ttu-id="412cb-167">**[ウィザードの完了]** ページで **[完了]** をクリックすると、Sales Reason ディメンションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="412cb-167">On the **Completing the Wizard** page, click **Finish** to create the Sales Reason dimension.</span></span>

11. <span data-ttu-id="412cb-168">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-168">On the **File** menu, click **Save All**.</span></span>

12. <span data-ttu-id="412cb-169">**Sales reason**ディメンションのディメンションデザイナーの [**属性**] ペインで、[ **sales reason Key**] を選択し、プロパティウィンドウの**Name**プロパティをに変更します。`Sales Reason.`</span><span class="sxs-lookup"><span data-stu-id="412cb-169">In the **Attributes** pane of the Dimension Designer for the **Sales Reason** dimension, select **Sales Reason Key**, and then change the **Name** property in the Properties window to `Sales Reason.`</span></span>

13. <span data-ttu-id="412cb-170">ディメンションデザイナーの [**階層**] ペインで、 **Sales Reasons** `Sales Reason Type` レベルと**販売理由**レベルを含む sales Reason ユーザー階層をこの順序で作成します。</span><span class="sxs-lookup"><span data-stu-id="412cb-170">In the **Hierarchies** pane of the Dimension Designer, create a **Sales Reasons** user hierarchy that contains the `Sales Reason Type` level and the **Sales Reason** level, in that order.</span></span>

14. <span data-ttu-id="412cb-171">プロパティウィンドウで、 `All Sales Reasons` Sales 理由階層の**allmembername**プロパティの値としてを定義します。</span><span class="sxs-lookup"><span data-stu-id="412cb-171">In the Properties window, define `All Sales Reasons` as the value for the **AllMemberName** property of the Sales Reasons hierarchy.</span></span>

15. <span data-ttu-id="412cb-172">`All Sales Reasons`Sales Reason ディメンションの**Attributeallmembername**プロパティの値としてを定義します。</span><span class="sxs-lookup"><span data-stu-id="412cb-172">Define `All Sales Reasons` as the value for **AttributeAllMemberName** property of the Sales Reason dimension.</span></span>

16. <span data-ttu-id="412cb-173">新しく作成したディメンションをキューブ ディメンションとして [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブに追加するには、 **キューブ デザイナー**に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="412cb-173">To add the newly created dimension to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube as a cube dimension, switch to **Cube Designer**.</span></span> <span data-ttu-id="412cb-174">**[キューブ構造]** タブの **[ディメンション]** ペイン内で右クリックし、 **[キューブ ディメンションの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-174">On the **Cube Structure** tab, right-click in the **Dimensions** pane and select **Add Cube Dimension**.</span></span>

17. <span data-ttu-id="412cb-175">**[キューブ ディメンションの追加]** ダイアログ ボックスで、 **[Sales Reason]** を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-175">In the **Add Cube Dimension** dialog box, select **Sales Reason** and then click **OK**.</span></span>

18. <span data-ttu-id="412cb-176">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-176">On the **File** menu, click **Save All**.</span></span>

## <a name="defining-the-many-to-many-relationship"></a><span data-ttu-id="412cb-177">多対多リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="412cb-177">Defining the Many to Many Relationship</span></span>

1.  <span data-ttu-id="412cb-178">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーに切り替え、 **[ディメンションの使用法]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-178">Switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Dimension Usage** tab.</span></span>

     <span data-ttu-id="412cb-179">**Sales Reason** ディメンションには、 **Internet Sales Reason** メジャー グループで定義されている標準のリレーションシップがあります。ただし、 **Internet Sales** メジャー グループおよび **Reseller Sales** メジャー グループで定義されたリレーションシップはありません。</span><span class="sxs-lookup"><span data-stu-id="412cb-179">Notice that the **Sales Reason** dimension has a regular relationship defined with the **Internet Sales Reason** measure group, but has no relationship defined with the **Internet Sales** or **Reseller Sales** measure groups.</span></span> <span data-ttu-id="412cb-180">また、 **Internet Sales Order Details** ディメンションには **Internet Sales Reason** ディメンションで定義されている標準のリレーションシップがあり、 **Internet Sales** メジャー グループとの **ファクト リレーションシップ** があります。</span><span class="sxs-lookup"><span data-stu-id="412cb-180">Notice also that the **Internet Sales Order Details** dimension has a regular relationship defined with the **Internet Sales Reason** dimension, which in turn has a **Fact Relationship** with the **Internet Sales** measure group.</span></span> <span data-ttu-id="412cb-181">このディメンションが存在しなかった場合 (または **Internet Sales Reason** メジャー グループおよび **Internet Sales** メジャー グループとのリレーションシップを持つ別のディメンションが存在しなかった場合)、多対多のリレーションシップを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="412cb-181">If this dimension was not present (or another dimension with a relationship with both the **Internet Sales Reason** and the **Internet Sales** measure group were not present), you would not be able to define the many-to-many relationship.</span></span>

2.  <span data-ttu-id="412cb-182">**Internet Sales** メジャー グループと **Sales Reason** ディメンションが交差する位置にあるセルをクリックし、参照ボタン (**[...]**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-182">Click the cell at the intersection of the **Internet Sales** measure group and the **Sales Reason** dimension and then click the browse button (**...**).</span></span>

3.  <span data-ttu-id="412cb-183">**[リレーションシップの定義]** ダイアログ ボックスで、 **[リレーションシップの種類の選択]** ボックスの一覧から **[多対多]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="412cb-183">In the **Define Relationship** dialog box, select **Many-to-Many** in the **Select relationship type** list.</span></span>

     <span data-ttu-id="412cb-184">Sales Reason ディメンションを Internet Sales メジャー グループに接続する中間メジャー グループを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="412cb-184">You have to define the intermediate measure group that connects the Sales Reason dimension to the Internet Sales measure group.</span></span>

4.  <span data-ttu-id="412cb-185">**[中間メジャー グループ]** ボックスの一覧で **[Internet Sales Reason]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="412cb-185">In the **Intermediate measure group** list, select **Internet Sales Reason**.</span></span>

     <span data-ttu-id="412cb-186">次の図は、 **[リレーションシップの定義]** ダイアログ ボックスでの操作を示しています。</span><span class="sxs-lookup"><span data-stu-id="412cb-186">The following image shows the changes in the **Define Relationship** dialog box.</span></span>

     <span data-ttu-id="412cb-187">![[リレーションシップの定義] ダイアログボックス](../../2014/tutorials/media/l5-many-to-many-3.gif "[リレーションシップの定義] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="412cb-187">![Define Relationship dialog box](../../2014/tutorials/media/l5-many-to-many-3.gif "Define Relationship dialog box")</span></span>

5.  <span data-ttu-id="412cb-188">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-188">Click **OK**.</span></span>

     <span data-ttu-id="412cb-189">多対多アイコンにより、Sales Reason ディメンションと Internet Sales メジャー グループの間のリレーションシップが表されます。</span><span class="sxs-lookup"><span data-stu-id="412cb-189">Notice the many-to-many icon that represents the relationship between the Sales Reason dimension and the Internet Sales measure group.</span></span>

## <a name="browsing-the-cube-and-the-many-to-many-dimension"></a><span data-ttu-id="412cb-190">キューブおよび多対多ディメンションの表示</span><span class="sxs-lookup"><span data-stu-id="412cb-190">Browsing the Cube and the Many-to-Many Dimension</span></span>

1.  <span data-ttu-id="412cb-191">**[ビルド]** メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-191">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="412cb-192">配置が正常に完了したら、 **Tutorial キューブのキューブ デザイナーで** [ブラウザー] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] タブに切り替え、 **[再接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-192">When deployment has successfully completed, switch to the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Reconnect**.</span></span>

3.  <span data-ttu-id="412cb-193">データ ペインのデータ領域に **Internet Sales-Sales Amount** メジャーを追加します。</span><span class="sxs-lookup"><span data-stu-id="412cb-193">Add the **Internet Sales-Sales Amount** measure to the data area of the data pane.</span></span>

4.  <span data-ttu-id="412cb-194">**Sales Reason** ディメンションの **Sales Reasons** ユーザー定義階層を、データ ペインの行領域に追加します。</span><span class="sxs-lookup"><span data-stu-id="412cb-194">Add the **Sales Reasons** user-defined hierarchy from the **Sales Reason** dimension to the row area of the data pane.</span></span>

5.  <span data-ttu-id="412cb-195">メタデータ ペインで、 **[Customer]**、 **[Location]**、 **[Customer Geography]**、 **[Members]**、 **[All Customers]**、 **[Australia]** の順にクリックし、 **[Queensland]** を右クリックして **[フィルターに追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="412cb-195">In the metadata pane, expand **Customer**, expand **Location**, expand **Customer Geography**, expand **Members**, expand **All Customers**, expand **Australia**, right-click **Queensland**, and then click **Add to Filter**.</span></span>

6.  <span data-ttu-id="412cb-196">レベルの各メンバーを展開し、 `Sales Reason Type` Queensland の顧客が [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] インターネット経由で製品を購入するために使用した各理由に関連付けられているドル値を確認します。</span><span class="sxs-lookup"><span data-stu-id="412cb-196">Expand each member of the `Sales Reason Type` level to review the dollar values that are associated with each reason a customer in Queensland gave for their purchase of an [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] product over the Internet.</span></span>

     <span data-ttu-id="412cb-197">購入理由に関連付けられている売上金額をすべて加算すると、総売上額を上回ります。</span><span class="sxs-lookup"><span data-stu-id="412cb-197">Notice that the totals that are associated with each sales reason add up to more than the total sales.</span></span> <span data-ttu-id="412cb-198">これは、製品の購入理由を複数選択した顧客がいたためです。</span><span class="sxs-lookup"><span data-stu-id="412cb-198">This is because some customers cited multiple reasons for their purchase.</span></span>

     <span data-ttu-id="412cb-199">次の図は、キューブ デザイナーの **[フィルター]** ペインと **[データ]** ペインです。</span><span class="sxs-lookup"><span data-stu-id="412cb-199">The following image shows the **Filter** pane and **Data** pane of Cube Designer.</span></span>

     <span data-ttu-id="412cb-200">![キューブ デザイナーの [フィルター] ペインと [データ] ペイン](../../2014/tutorials/media/l5-many-to-many-5.gif "キューブ デザイナーの [フィルター] ペインと [データ] ペイン")</span><span class="sxs-lookup"><span data-stu-id="412cb-200">![Filter and Data panes of Cube Designer](../../2014/tutorials/media/l5-many-to-many-5.gif "Filter and Data panes of Cube Designer")</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="412cb-201">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="412cb-201">Next Task in Lesson</span></span>
 [<span data-ttu-id="412cb-202">メジャー グループでのディメンション粒度の定義</span><span class="sxs-lookup"><span data-stu-id="412cb-202">Defining Dimension Granularity within a Measure Group</span></span>](lesson-5-4-defining-dimension-granularity-within-a-measure-group.md)

## <a name="see-also"></a><span data-ttu-id="412cb-203">参照</span><span class="sxs-lookup"><span data-stu-id="412cb-203">See Also</span></span>
 <span data-ttu-id="412cb-204">[データソースビューデザイナーでのダイアグラムの操作 &#40;Analysis Services&#41;](multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md) [ディメンションリレーションシップ](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)[が多対多リレーションシップと多対多リレーションシップのプロパティを定義する](multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md)</span><span class="sxs-lookup"><span data-stu-id="412cb-204">[Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;](multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md) [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) [Define a Many-to-Many Relationship and Many-to-Many Relationship Properties](multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md)</span></span>


