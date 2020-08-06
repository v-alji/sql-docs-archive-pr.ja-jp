---
title: ファクトリレーションシップの定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4b49a078-6848-4286-bc71-cf4862d29064
author: minewiskan
ms.author: owend
ms.openlocfilehash: 26f8068301c424d5aea9f54e882ceb8a4dc72806
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645222"
---
# <a name="defining-a-fact-relationship"></a><span data-ttu-id="c4357-102">ファクト リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="c4357-102">Defining a Fact Relationship</span></span>
  <span data-ttu-id="c4357-103">ディメンション メジャーをファクト テーブルのデータ アイテムに関連付けなければならない場合があります。また、特定の販売ファクター (請求番号や受注番号) など、関連している特定の補足情報について、ファクト テーブルから情報を抽出しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="c4357-103">Users sometimes want to be able to dimension measures by data items that are in the fact table or to query the fact table for specific additional related information, such as invoice numbers or purchase order numbers related to specific sales facts.</span></span> <span data-ttu-id="c4357-104">このように、ファクト テーブル アイテムに基づいて定義されたディメンションを、 *ファクト ディメンション*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="c4357-104">When you define a dimension based on such a fact table item, the dimension is called a *fact dimension*.</span></span> <span data-ttu-id="c4357-105">ファクト ディメンションは、逆ディメンションとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="c4357-105">Fact dimensions are also known as degenerate dimensions.</span></span> <span data-ttu-id="c4357-106">特定の請求番号に関連するすべての行をグループ化する場合などのように、関連するテーブルの行をまとめてグループ化するには、ファクト ディメンションを使用すると便利です。</span><span class="sxs-lookup"><span data-stu-id="c4357-106">Fact dimensions are useful for grouping together related fact table rows, such as all the rows that are related to a particular invoice number.</span></span> <span data-ttu-id="c4357-107">この情報は、リレーショナル データベースの個々のディメンション テーブルに格納することができます。しかし、情報ごとに異なるディメンション テーブルを作成してもメリットはありません。ファクト テーブルのサイズに比例してディメンション テーブルが大きくなり、データを複製することによって不要な複雑さを招くことになるからです。</span><span class="sxs-lookup"><span data-stu-id="c4357-107">Although you can put this information in a separate dimension table in the relational database, creating a separate dimension table for the information provides no benefit because the dimension table would grow at the same rate as the fact table, and would just create duplicate data and unnecessary complexity.</span></span>

 <span data-ttu-id="c4357-108">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]では、MOLAP ディメンションにファクト ディメンション データを複製してクエリ パフォーマンスを向上させる方法か、ファクト ディメンションを ROLAP ディメンションとして定義し、クエリ パフォーマンスという点を譲歩して記憶領域を節約する方法を選択できます。</span><span class="sxs-lookup"><span data-stu-id="c4357-108">Within [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], you can determine whether to duplicate the fact dimension data in a MOLAP dimension structure for increased query performance, or whether to define the fact dimension as a ROLAP dimension to save storage space at the expense of query performance.</span></span> <span data-ttu-id="c4357-109">MOLAP ストレージ モードでディメンションを格納する場合、すべてのディメンション メンバーは、メジャー グループのパーティションの他に、圧縮率の高い MOLAP 構造内の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c4357-109">When you store a dimension with the MOLAP storage mode, all the dimension members are stored in the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in a highly compressed MOLAP structure, in addition to being stored in the measure group's partitions.</span></span> <span data-ttu-id="c4357-110">ROLAP ストレージモードでディメンションを格納する場合、MOLAP 構造にはディメンション定義のみが格納されます。ディメンションメンバー自体は、クエリ時に基になるリレーショナルファクトテーブルからクエリが実行されます。</span><span class="sxs-lookup"><span data-stu-id="c4357-110">When you store a dimension with the ROLAP storage mode, only the dimension definition is stored in the MOLAP structure-the dimension members themselves are queried from the underlying relational fact table at query time.</span></span> <span data-ttu-id="c4357-111">ファクト ディメンションにクエリを送信する頻度、通常のクエリにより返される行数、クエリのパフォーマンス、および処理コストなどを考慮し、適切なストレージ モードを決定します。</span><span class="sxs-lookup"><span data-stu-id="c4357-111">You decide the appropriate storage mode based on how frequently the fact dimension is queried, the number of rows returned by a typical query, the performance of the query, and the processing cost.</span></span> <span data-ttu-id="c4357-112">ディメンションを ROLAP モードとして定義する場合は、そのディメンションを使用するすべてのキューブを ROLAP ストレージ モードで格納しなければならないということではありません。</span><span class="sxs-lookup"><span data-stu-id="c4357-112">Defining a dimension as ROLAP does not require that all cubes that use the dimension also be stored with the ROLAP storage mode.</span></span> <span data-ttu-id="c4357-113">各ディメンションのストレージ モードは、個別に構成できます。</span><span class="sxs-lookup"><span data-stu-id="c4357-113">The storage mode for each dimension can be configured independently.</span></span>

 <span data-ttu-id="c4357-114">ファクト ディメンションを定義している場合は、ファクト ディメンションとメジャー グループの間のリレーションシップを、ファクト リレーションシップとして定義できます。</span><span class="sxs-lookup"><span data-stu-id="c4357-114">When you define a fact dimension, you can define the relationship between the fact dimension and the measure group as a fact relationship.</span></span> <span data-ttu-id="c4357-115">ファクト リレーションシップには、次の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="c4357-115">The following constraints apply to fact relationships:</span></span>

-   <span data-ttu-id="c4357-116">粒度属性は、ディメンションとファクト テーブル内のファクトとの間に一対一のリレーションシップを作成するディメンションのキー列でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="c4357-116">The granularity attribute must be the key column for the dimension, which creates a one-to-one relationship between the dimension and the facts in the fact table.</span></span>

-   <span data-ttu-id="c4357-117">ディメンションに定義できるファクト リレーションシップは、1 メジャー グループとのファクト リレーションシップに限定されます。</span><span class="sxs-lookup"><span data-stu-id="c4357-117">A dimension can have a fact relationship with only a single measure group.</span></span>

> [!NOTE]
>  <span data-ttu-id="c4357-118">ファクト リレーションシップが参照するメジャー グループを更新するたびに、ファクト ディメンションを増分更新しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="c4357-118">Fact dimensions must be incrementally updated after every update to the measure group that the fact relationship references.</span></span>

 <span data-ttu-id="c4357-119">詳細については、「 [ディメンション リレーションシップ](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)」および「 [ファクト リレーションシップとファクト リレーションシップのプロパティの定義](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4357-119">For more information, see [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), and [Define a Fact Relationship and Fact Relationship Properties](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md).</span></span>

 <span data-ttu-id="c4357-120">このトピックの実習では、 **FactInternetSales** ファクト テーブルの **CustomerPONumber** 列に基づく新しいキューブ ディメンションを追加します。</span><span class="sxs-lookup"><span data-stu-id="c4357-120">In the tasks in this topic, you add a new cube dimension based on the **CustomerPONumber** column in the **FactInternetSales** fact table.</span></span> <span data-ttu-id="c4357-121">次に、新しいキューブ ディメンションと **Internet Sales** メジャー グループの間のリレーションシップを、ファクト リレーションシップとして定義します。</span><span class="sxs-lookup"><span data-stu-id="c4357-121">You then define the relationship between this new cube dimension and the **Internet Sales** measure group as a fact relationship.</span></span>

## <a name="defining-the-internet-sales-orders-fact-dimension"></a><span data-ttu-id="c4357-122">Internet Sales Orders ファクト ディメンションの定義</span><span class="sxs-lookup"><span data-stu-id="c4357-122">Defining the Internet Sales Orders Fact Dimension</span></span>

1.  <span data-ttu-id="c4357-123">ソリューションエクスプローラーで、[**ディメンション**] を右クリックし、[**新しいディメンション**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c4357-123">In Solution Explorer, right-click **Dimensions**, and then click **New Dimension**.</span></span>

2.  <span data-ttu-id="c4357-124">**[ディメンション ウィザードへようこそ]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c4357-124">On the **Welcome to the Dimension Wizard** page, click **Next**.</span></span>

3.  <span data-ttu-id="c4357-125">**[作成方法の選択]** ページで **[既存のテーブルの使用]** オプションが選択されていることを確認し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c4357-125">On the **Select Creation Method** page, verify that the **Use an existing table** option is selected, and then click **Next**.</span></span>

4.  <span data-ttu-id="c4357-126">**[基になる情報の指定]** ページで、 **Adventure Works DW 2012** データ ソース ビューが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c4357-126">On the **Specify Source Information** page, verify that the **Adventure Works DW 2012** data source view is selected.</span></span>

5.  <span data-ttu-id="c4357-127">**[メイン テーブル]** ボックスの一覧で、 **[InternetSales]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c4357-127">In the **Main table** list, select **InternetSales**.</span></span>

6.  <span data-ttu-id="c4357-128">**[キー列]** ボックスの一覧に **[SalesOrderNumber]** と **[SalesOrderLineNumber]** が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c4357-128">In the **Key columns** list, verify that **SalesOrderNumber** and **SalesOrderLineNumber** are listed.</span></span>

7.  <span data-ttu-id="c4357-129">**[名前列]** ボックスの一覧から **[SalesOrderLineNumber]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c4357-129">In the **Name column** list, select **SalesOrderLineNumber**.</span></span>

8.  <span data-ttu-id="c4357-130">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c4357-130">Click **Next**.</span></span>

9. <span data-ttu-id="c4357-131">**[関連テーブルの選択]** ページで、すべてのテーブルの横のチェック ボックスをオフにし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c4357-131">On the **Select Related Tables** page, clear the check boxes beside all of the tables, and then click **Next**.</span></span>

10. <span data-ttu-id="c4357-132">**[ディメンション属性の選択]** ページで、ヘッダーのチェック ボックスを 2 回クリックしてすべてのチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="c4357-132">On the **Select Dimension Attributes** page, click the check box in the header twice to clear all of the check boxes.</span></span> <span data-ttu-id="c4357-133">**Sales Order Number** 属性はキー属性なので、選択されたままになります。</span><span class="sxs-lookup"><span data-stu-id="c4357-133">The **Sales Order Number** attribute will remain selected because it is the key attribute.</span></span>

11. <span data-ttu-id="c4357-134">**Customer PO Number** 属性を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c4357-134">Select the **Customer PO Number** attribute, and then click **Next**.</span></span>

12. <span data-ttu-id="c4357-135">**[ウィザードの完了]** ページで、名前を **Internet Sales Order Details** に変更します。 **[完了]** をクリックしてウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="c4357-135">On the **Completing the Wizard** page, change the name to **Internet Sales Order Details** and then click **Finish** to complete the wizard.</span></span>

13. <span data-ttu-id="c4357-136">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c4357-136">On the **File** menu, click **Save All**.</span></span>

14. <span data-ttu-id="c4357-137">**Internet Sales Order Details**ディメンションのディメンションデザイナーの [**属性**] ペインで、[ **Sales order Number**] を選択し、プロパティウィンドウの**Name**プロパティをに変更します。`Item Description.`</span><span class="sxs-lookup"><span data-stu-id="c4357-137">In the **Attributes** pane of the Dimension Designer for the **Internet Sales Order Details** dimension, select **Sales Order Number**, and then change the **Name** property in the Properties window to `Item Description.`</span></span>

15. <span data-ttu-id="c4357-138">**NameColumn**プロパティセルで、参照ボタン ([. **..])** をクリックします。[**名前列**] ダイアログボックスで、[基に**なるテーブル**] ボックスの一覧から [ **Product** ] を選択し、[基になる**列**] で [ **EnglishProductName** ] を選択して、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c4357-138">In the **NameColumn** property cell, click the browse button **(...)**. In the **Name Column** dialog box, select **Product** from the **Source table** list, select **EnglishProductName** for the **Source column**, and then click **OK**.</span></span>

16. <span data-ttu-id="c4357-139">**[データ ソース ビュー]** ペインで、 **InternetSales** テーブルの **SalesOrderNumber** 列をクリックし、 **[属性]** ペインにドラッグします。これにより、 **Sales Order Number** 属性がディメンションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="c4357-139">Add the **Sales Order Number** attribute to the dimension by dragging the **SalesOrderNumber** column from the **InternetSales** table in the **Data Source View** pane to the **Attributes** pane.</span></span>

17. <span data-ttu-id="c4357-140">新しい**Sales Order Number**属性の**Name**プロパティをに変更 `Order Number` し、 **OrderBy**プロパティを**Key**に変更します。</span><span class="sxs-lookup"><span data-stu-id="c4357-140">Change the **Name** property of the new **Sales Order Number** attribute to `Order Number`, and change the **OrderBy** property to **Key**.</span></span>

18. <span data-ttu-id="c4357-141">[**階層**] ペインで、および項目の説明のレベルを含む**Internet Sales Orders**ユーザー階層をこの `Order Number` 順序で作成し**Item Description**ます。</span><span class="sxs-lookup"><span data-stu-id="c4357-141">In the **Hierarchies** pane, create an **Internet Sales Orders** user hierarchy that contains the `Order Number` and **Item Description** levels, in that order.</span></span>

19. <span data-ttu-id="c4357-142">**[属性]** ペインで **Internet Sales Order Details**をクリックします。次に、[プロパティ] ウィンドウで、 **StorageMode** プロパティの値を確認します。</span><span class="sxs-lookup"><span data-stu-id="c4357-142">In the **Attributes** pane, select **Internet Sales Order Details**, and then review the value for the **StorageMode** property in the Properties window.</span></span>

     <span data-ttu-id="c4357-143">既定では、このディメンションは MOLAP ディメンションに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c4357-143">Notice that, by default, this dimension is stored as a MOLAP dimension.</span></span> <span data-ttu-id="c4357-144">このストレージ モードを ROLAP に変更すると、処理時間を短縮し、記憶領域を節約できますが、クエリのパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="c4357-144">Although changing the storage mode to ROLAP will save processing time and storage space, it occurs at the expense of query performance.</span></span> <span data-ttu-id="c4357-145">このチュートリアルでは、MOLAP ストレージ モードを使用します。</span><span class="sxs-lookup"><span data-stu-id="c4357-145">For the purposes of this tutorial, you will use MOLAP as the storage mode.</span></span>

20. <span data-ttu-id="c4357-146">新しく作成したディメンションをキューブ ディメンションとして [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブに追加するには、 **キューブ デザイナー**に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="c4357-146">To add the newly created dimension to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube as a cube dimension, switch to **Cube Designer**.</span></span> <span data-ttu-id="c4357-147">**[キューブ構造]** タブの **[ディメンション]** ペイン内で右クリックし、 **[キューブ ディメンションの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c4357-147">On the **Cube Structure** tab, right-click in the **Dimensions** pane and select **Add Cube Dimension**.</span></span>

21. <span data-ttu-id="c4357-148">**[キューブ ディメンションの追加]** ダイアログ ボックスで、 **[Internet Sales Order Details]** を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c4357-148">In the **Add Cube Dimension**.dialog box, select **Internet Sales Order Details** and then click **OK**.</span></span>

## <a name="defining-a-fact-relationship-for-the-fact-dimension"></a><span data-ttu-id="c4357-149">ファクト ディメンションへのファクト リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="c4357-149">Defining a Fact Relationship for the Fact Dimension</span></span>

1.  <span data-ttu-id="c4357-150">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーを開いて、 **[ディメンションの使用法]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c4357-150">In the Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, click the **Dimension Usage** tab.</span></span>

     <span data-ttu-id="c4357-151">以下のアイコンが示すように、 **Internet Sales Order Details** キューブ ディメンションがファクト リレーションシップを保持するよう、自動的に構成されます。</span><span class="sxs-lookup"><span data-stu-id="c4357-151">Notice that the **Internet Sales Order Details** cube dimension is automatically configured as having a fact relationship, as shown by the unique icon.</span></span>

2.  <span data-ttu-id="c4357-152">**Internet sales**メジャーグループと**Internet sales Order Details**ディメンションが交差する位置にある**Item Description**セルで参照ボタン ([.**..**]) をクリックし、ファクトリレーションシップのプロパティを確認します。</span><span class="sxs-lookup"><span data-stu-id="c4357-152">Click the browse button (**...**) in the **Item Description** cell, at the intersection of the **Internet Sales** measure group and the **Internet Sales Order Details** dimension, to review the fact relationship properties.</span></span>

     <span data-ttu-id="c4357-153">**[リレーションシップの定義]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="c4357-153">The **Define Relationship** dialog box opens.</span></span> <span data-ttu-id="c4357-154">構成できるプロパティはありません。</span><span class="sxs-lookup"><span data-stu-id="c4357-154">Notice that you cannot configure any of the properties.</span></span>

     <span data-ttu-id="c4357-155">次の図は **[リレーションシップの定義]** ダイアログ ボックスのファクト リレーションシップのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="c4357-155">The following image shows the fact relationship properties in the **Define Relationship** dialog box.</span></span>

     <span data-ttu-id="c4357-156">![[リレーションシップの定義] ダイアログボックス](../../2014/tutorials/media/l5-factrelationship-2.gif "[リレーションシップの定義] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="c4357-156">![Define Relationship dialog box](../../2014/tutorials/media/l5-factrelationship-2.gif "Define Relationship dialog box")</span></span>

3.  <span data-ttu-id="c4357-157">**[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c4357-157">Click **Cancel**.</span></span>

## <a name="browsing-the-cube-by-using-the-fact-dimension"></a><span data-ttu-id="c4357-158">ファクト ディメンションを使用したキューブの表示</span><span class="sxs-lookup"><span data-stu-id="c4357-158">Browsing the Cube by Using the Fact Dimension</span></span>

1.  <span data-ttu-id="c4357-159">**[ビルド]** メニューの **[Analysis Services Tutorial の配置]** をクリックし、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスへの変更を配置して、データベースを処理します。</span><span class="sxs-lookup"><span data-stu-id="c4357-159">On the **Build** menu, click **Deploy Analysis Services Tutorial** to deploy the changes to the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and process the database.</span></span>

2.  <span data-ttu-id="c4357-160">配置が正常に完了したら、 **Tutorial キューブのキューブ デザイナーで** [ブラウザー] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] タブをクリックし、 **[再接続]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c4357-160">After deployment has successfully completed, click the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Reconnect** button.</span></span>

3.  <span data-ttu-id="c4357-161">データ ペインからすべてのメジャーと階層を消去します。次に、データ ペインのデータ領域に **Internet Sales-Sales Amount** メジャーを追加します。</span><span class="sxs-lookup"><span data-stu-id="c4357-161">Clear all measures and hierarchies from the data pane, and then add the **Internet Sales-Sales Amount** measure to the data area of the data pane.</span></span>

4.  <span data-ttu-id="c4357-162">メタデータ ペインで、 **[Customer]**、 **[Location]**、 **[Customer Geography]**、 **[Members]**、 **[All Customers]**、 **[Australia]**、 **[Queensland]**、 **[Brisbane]**、 **[4000]** の順にクリックし、 **[Adam Powell]** を右クリックして **[フィルターに追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c4357-162">In the metadata pane, expand **Customer**, expand **Location**, expand **Customer Geography**, expand **Members**, expand **All Customers**, expand **Australia**, expand **Queensland**, expand **Brisbane**, expand **4000**, right-click **Adam Powell**, and then click **Add to Filter**.</span></span>

     <span data-ttu-id="c4357-163">フィルタリングを使用し、1 顧客から返される販売注文数を制限すると、クエリ パフォーマンスを大幅に犠牲にすることなく、基となる詳細情報を大規模なファクト テーブルから検索できます。</span><span class="sxs-lookup"><span data-stu-id="c4357-163">Filtering to limit the sales orders returned to a single customer lets the user drill down to the underlying detail in a large fact table without suffering a significant loss in query performance.</span></span>

5.  <span data-ttu-id="c4357-164">**Internet Sales Order Details** ディメンションの **Internet Sales Orders** ユーザー定義階層を、データ ペインの行領域に追加します。</span><span class="sxs-lookup"><span data-stu-id="c4357-164">Add the **Internet Sales Orders** user-defined hierarchy from the **Internet Sales Order Details** dimension to the row area of the data pane.</span></span>

     <span data-ttu-id="c4357-165">Adam Powell 氏の注文数と、それに対応するインターネット販売量がデータ ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c4357-165">Notice that the sales order numbers and the corresponding Internet sales amounts for Adam Powell appear in the data pane.</span></span>

     <span data-ttu-id="c4357-166">次の図は、前の手順の結果を示します。</span><span class="sxs-lookup"><span data-stu-id="c4357-166">The following image shows the result of the previous steps.</span></span>

     <span data-ttu-id="c4357-167">![Internet Sales-Sales Amount のディメンション指定](../../2014/tutorials/media/l5-factrelationship-3.gif "Internet Sales-Sales Amount のディメンション指定")</span><span class="sxs-lookup"><span data-stu-id="c4357-167">![Dimensioning of Internet Sales-Sales Amount](../../2014/tutorials/media/l5-factrelationship-3.gif "Dimensioning of Internet Sales-Sales Amount")</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="c4357-168">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="c4357-168">Next Task in Lesson</span></span>
 [<span data-ttu-id="c4357-169">多対多関係の定義</span><span class="sxs-lookup"><span data-stu-id="c4357-169">Defining a Many-to-Many Relationship</span></span>](lesson-5-3-defining-a-many-to-many-relationship.md)

## <a name="see-also"></a><span data-ttu-id="c4357-170">参照</span><span class="sxs-lookup"><span data-stu-id="c4357-170">See Also</span></span>
 <span data-ttu-id="c4357-171">[ディメンションリレーションシップ](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)[は、ファクトリレーションシップとファクトリレーションシップのプロパティを定義し](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)ます。</span><span class="sxs-lookup"><span data-stu-id="c4357-171">[Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) [Define a Fact Relationship and Fact Relationship Properties](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)</span></span>


