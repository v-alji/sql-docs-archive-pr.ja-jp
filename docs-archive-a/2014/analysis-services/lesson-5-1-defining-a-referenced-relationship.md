---
title: 参照リレーションシップの定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4a34ba52-e3b3-4e8a-8e55-73e0cd5a97bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7b14699ad098ba8c0931c00a3cbd30a6a8026771
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645235"
---
# <a name="defining-a-referenced-relationship"></a><span data-ttu-id="59903-102">参照リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="59903-102">Defining a Referenced Relationship</span></span>
  <span data-ttu-id="59903-103">このチュートリアルのこれまでの実習では、主キーから外部キーへのリレーションシップを使用し、メジャー グループのファクト テーブルに直接リンクしているテーブルに基づいて、各キューブ ディメンションを定義しました。</span><span class="sxs-lookup"><span data-stu-id="59903-103">Up to this point in the tutorial, each cube dimension that you defined was based on a table that was directly linked to the fact table for a measure group by a primary key to foreign key relationship.</span></span> <span data-ttu-id="59903-104">このトピックの実習では、 **Reseller** ディメンションを介し、 **Geography** ディメンションを再販業者販売のファクト テーブルにリンクさせます。このようにリンクを中継するディメンションを、 *参照ディメンション*といいます。</span><span class="sxs-lookup"><span data-stu-id="59903-104">In the tasks in this topic, you link the **Geography** dimension to the fact table for reseller sales through the **Reseller** dimension, which is called a *reference dimension*.</span></span> <span data-ttu-id="59903-105">参照ディメンションにより、販売店の売上と地域を関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="59903-105">This enables users to dimension reseller sales by geography.</span></span> <span data-ttu-id="59903-106">詳細については、「 [参照リレーションシップと参照リレーションシップのプロパティの定義](multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59903-106">For more information, see [Define a Referenced Relationship and Referenced Relationship Properties](multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md).</span></span>

## <a name="dimensioning-reseller-sales-by-geography"></a><span data-ttu-id="59903-107">販売店の売上と地域を関連付ける</span><span class="sxs-lookup"><span data-stu-id="59903-107">Dimensioning Reseller Sales by Geography</span></span>

1.  <span data-ttu-id="59903-108">ソリューション エクスプローラーで、 **[キューブ]** フォルダー内にある **[Analysis Services Tutorial]** を右クリックし、 **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59903-108">In Solution Explorer, right-click **Analysis Services Tutorial** in the **Cubes** folder, and then click **Browse**.</span></span>

2.  <span data-ttu-id="59903-109">データ ペインからすべての階層を削除します。次に、データ ペインのデータ領域に **Reseller Sales-Sales Amount** メジャーが表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="59903-109">Remove all hierarchies from the data pane, and then verify that the **Reseller Sales-Sales Amount** measure appears in the data area of the data pane.</span></span> <span data-ttu-id="59903-110">表示されていない場合は、このメジャーをデータ ペインに追加します。</span><span class="sxs-lookup"><span data-stu-id="59903-110">Add it to the data pane if it is not already there.</span></span>

3.  <span data-ttu-id="59903-111">メタデータ ペインで **Geography** ディメンションを展開し、 **[Geographies]** ユーザー定義階層を、データ ペインの **[ここに行のフィールドをドロップします]** 領域までドラッグします。</span><span class="sxs-lookup"><span data-stu-id="59903-111">From the **Geography** dimension in the metadata pane, drag the **Geographies** user-defined hierarchy to the **Drop Row Fields Here** area of the data pane.</span></span>

     <span data-ttu-id="59903-112">**Reseller Sales-Sales Amount** メジャーは、 **Regions** 階層の **Country-Region** 属性メンバーによって正しく多次元化されていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="59903-112">Notice that the **Reseller Sales-Sales Amount** measure is not correctly dimensioned by the **Country-Region** attribute members in the **Regions** hierarchy.</span></span> <span data-ttu-id="59903-113">**Reseller Sales-Sales Amount** の値が、各 **Country-Region** 属性メンバーで繰り返されています。</span><span class="sxs-lookup"><span data-stu-id="59903-113">The value for **Reseller Sales-Sales Amount** repeats for each **Country-Region** attribute member.</span></span>

     <span data-ttu-id="59903-114">![ディメンションが指定された Reseller Sales-Sales Amount メジャー](../../2014/tutorials/media/l5-referencedrelationship-1.gif "ディメンションが指定された Reseller Sales-Sales Amount メジャー")</span><span class="sxs-lookup"><span data-stu-id="59903-114">![Dimensioned Reseller Sales-Sales Amount measure](../../2014/tutorials/media/l5-referencedrelationship-1.gif "Dimensioned Reseller Sales-Sales Amount measure")</span></span>

4.  <span data-ttu-id="59903-115">データ ソース ビュー デザイナーを開き、 **Adventure Works DW 2012** データ ソース ビューを表示します。</span><span class="sxs-lookup"><span data-stu-id="59903-115">Open Data Source View Designer for the **Adventure Works DW 2012** data source view.</span></span>

5.  <span data-ttu-id="59903-116">**[ダイアグラム オーガナイザー]** ペインで、 **Geography** テーブルと **ResellerSales** テーブルの間のリレーションシップを確認します。</span><span class="sxs-lookup"><span data-stu-id="59903-116">In the **Diagram Organizer** pane, view the relationship between the **Geography** table and the **ResellerSales** table.</span></span>

     <span data-ttu-id="59903-117">2 つのテーブルの間には直接的なリンクが存在しません。</span><span class="sxs-lookup"><span data-stu-id="59903-117">Notice that there is no direct link between these tables.</span></span> <span data-ttu-id="59903-118">一方、 **Reseller** テーブル、または **SalesTerritory** テーブルを介した間接的なリンクは存在します。</span><span class="sxs-lookup"><span data-stu-id="59903-118">However, there is an indirect link between these tables through either the **Reseller** table or the **SalesTerritory** table.</span></span>

6.  <span data-ttu-id="59903-119">**Geography** テーブルと **Reseller** テーブルの間のリレーションシップを表す矢印をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="59903-119">Double-click the arrow that represents the relationship between the **Geography** table and the **Reseller** table.</span></span>

     <span data-ttu-id="59903-120">**[リレーションシップの編集]** ダイアログ ボックスで、 **GeographyKey** 列は **Geography** テーブルで主キー、 **Reseller** テーブルでは外部キーとなっていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="59903-120">In the **Edit Relationship** dialog box, notice that the **GeographyKey** column is the primary key in the **Geography** table and the foreign key in the **Reseller** table.</span></span>

7.  <span data-ttu-id="59903-121">**[キャンセル]** をクリックします。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーに切り替え、 **[ディメンションの使用法]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="59903-121">Click **Cancel**, switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Dimension Usage** tab.</span></span>

     <span data-ttu-id="59903-122">現在、 **Geography** キューブ ディメンションには、 **Internet Sales** メジャー グループ、または **Reseller Sales** メジャー グループとのリレーションシップがありません。</span><span class="sxs-lookup"><span data-stu-id="59903-122">Notice that the **Geography** cube dimension does not currently have a relationship with either the **Internet Sales** measure group or the **Reseller Sales** measure group.</span></span>

8.  <span data-ttu-id="59903-123">**Customer**ディメンションと**Internet Sales**メジャーグループの交差部分にある [**フルネーム**] セルで、省略記号ボタン ([**...**]) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59903-123">Click the ellipsis button (**...**) in the **Full Name** cell at the intersection of the **Customer** dimension and the **Internet Sales** measure group.</span></span>

     <span data-ttu-id="59903-124">**[リレーションシップの編集]** ダイアログ ボックスが表示されます。設定内容を確認すると、 **DimCustomer** ディメンション テーブルと **FactInternetSales** メジャー グループ テーブルの間には、これら 2 つのテーブルの **CustomerKey** 列に基づいて " **標準** " リレーションシップが定義されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="59903-124">In the **Define Relationship** dialog box, notice that a **Regular** relationship is defined between the **DimCustomer** dimension table and the **FactInternetSales** measure group table based on the **CustomerKey** column in each of these tables.</span></span> <span data-ttu-id="59903-125">これまでに定義したリレーションシップは、すべて "標準" リレーションシップです。</span><span class="sxs-lookup"><span data-stu-id="59903-125">All the relationships that you have defined within this tutorial up to this point have been regular relationships.</span></span>

     <span data-ttu-id="59903-126">次の図は、 **DimCustomer** ディメンション テーブルと、 **FactInternetSales** メジャー グループ テーブルの間に "標準" リレーションシップが定義されている **[リレーションシップの定義]** ダイアログ ボックスです。</span><span class="sxs-lookup"><span data-stu-id="59903-126">The following image shows the **Define Relationship** dialog box with a regular relationship between the **DimCustomer** dimension table and the **FactInternetSales** measure group table.</span></span>

     <span data-ttu-id="59903-127">![[リレーションシップの定義] ダイアログボックス](../../2014/tutorials/media/l5-referencedrelationship-4.gif "[リレーションシップの定義] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="59903-127">![Define Relationship dialog box](../../2014/tutorials/media/l5-referencedrelationship-4.gif "Define Relationship dialog box")</span></span>

9. <span data-ttu-id="59903-128">**[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59903-128">Click **Cancel**.</span></span>

10. <span data-ttu-id="59903-129">**Geography**ディメンションと**再販業者の Sales**メジャーグループの交差部分にある名前のないセルで、省略記号ボタン ([**...**]) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59903-129">Click the ellipsis button (**...**) in the unnamed cell at the intersection of the **Geography** dimension and the **Reseller Sales** measure group.</span></span>

     <span data-ttu-id="59903-130">**[リレーションシップの定義]** ダイアログ ボックスを確認すると、現在のところ、Geography キューブ ディメンションと Reseller Sales メジャー グループの間には、リレーションシップが何も定義されていません。</span><span class="sxs-lookup"><span data-stu-id="59903-130">In the **Define Relationship** dialog box, notice that no relationship is currently defined between the Geography cube dimension and the Reseller Sales measure group.</span></span> <span data-ttu-id="59903-131">Geography ディメンションのディメンション テーブルと Reseller Sales メジャー グループのファクト テーブルの間には直接的なリレーションシップがないため、"標準" リレーションシップは定義できません。</span><span class="sxs-lookup"><span data-stu-id="59903-131">You cannot define a regular relationship because there is no direct relationship between the dimension table for the Geography dimension and the fact table for the Reseller Sales measure group.</span></span>

11. <span data-ttu-id="59903-132">**[リレーションシップの種類の選択]** ボックスの一覧から **[参照対象]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59903-132">In the **Select relationship type** list, select **Referenced**.</span></span>

     <span data-ttu-id="59903-133">*中間テーブル*と呼ばれる、メジャー グループ テーブルに直接接続しているディメンションを指定することにより、参照リレーションシップを定義します。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は、この中間テーブルを使用して参照ディメンションをファクト テーブルにリンクします。</span><span class="sxs-lookup"><span data-stu-id="59903-133">You define a referenced relationship by specifying a dimension that is directly connected to the measure group table, called an *intermediate dimension*, that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] can use to link the reference dimension to the fact table.</span></span> <span data-ttu-id="59903-134">次に、参照ディメンションを中間ディメンションにリンクさせるために使用する属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="59903-134">You then specify the attribute that links the reference dimension to the intermediate dimension.</span></span>

12. <span data-ttu-id="59903-135">**[中間ディメンション]** ボックスの一覧から **[Reseller]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="59903-135">In the **Intermediate dimension** list, select **Reseller**.</span></span>

     <span data-ttu-id="59903-136">Reseller ディメンションの基となるテーブルを介して、Geography ディメンションの基となるテーブルがファクト テーブルにリンクされます。</span><span class="sxs-lookup"><span data-stu-id="59903-136">The underlying table for the Geography dimension is linked to the fact table through the underlying table for the Reseller dimension.</span></span>

13. <span data-ttu-id="59903-137">**[参照ディメンションの属性]** ボックスの一覧から **[Geography Key]** を選択します。次に、 **[中間ディメンションの属性]** ボックスの一覧から **[Geography Key]** を選択してみてください。</span><span class="sxs-lookup"><span data-stu-id="59903-137">In the **Reference dimension attribute** list, select **Geography Key**, and then try to select **Geography Key** in the **Intermediate dimension attribute** list.</span></span>

     <span data-ttu-id="59903-138">**[中間ディメンションの属性]** ボックスの一覧には **[Geography Key]** が表示されません。</span><span class="sxs-lookup"><span data-stu-id="59903-138">Notice that **Geography Key** does not appear in the **Intermediate dimension attribute** list.</span></span> <span data-ttu-id="59903-139">これは、 **GeographyKey** 列が **Reseller** ディメンションの属性として定義されていないためです。</span><span class="sxs-lookup"><span data-stu-id="59903-139">This is because the **GeographyKey** column is not defined as an attribute in the **Reseller** dimension.</span></span>

14. <span data-ttu-id="59903-140">**[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59903-140">Click **Cancel**.</span></span>

 <span data-ttu-id="59903-141">次の実習では、GeographyKey 列に基づく属性を Reseller ディメンションに定義し、この問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="59903-141">In the next task, you will solve this problem by defining an attribute that is based on the GeographyKey column in the Reseller dimension.</span></span>

## <a name="defining-the-intermediate-dimension-attribute-and-the-referenced-dimension-relationship"></a><span data-ttu-id="59903-142">中間ディメンション属性と参照ディメンション リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="59903-142">Defining the Intermediate Dimension Attribute and the Referenced Dimension Relationship</span></span>

1.  <span data-ttu-id="59903-143">**Reseller** ディメンションのディメンション デザイナーを開き、 **[データ ソース ビュー]** ペインで **Reseller** テーブルの各列を確認します。さらに、 **[属性]** ペインの **Reseller** ディメンションに定義されている属性を確認します。</span><span class="sxs-lookup"><span data-stu-id="59903-143">Open Dimension Designer for the **Reseller** dimension, and view the columns in the **Reseller** table in the **Data Source View** pane, and view the defined attributes in the **Reseller** dimension in the **Attributes** pane.</span></span>

     <span data-ttu-id="59903-144">Reseller テーブルでは、GeographyKey が列として定義されています。この列に基づく Reseller ディメンションには、ディメンション定義が何も定義されていません。</span><span class="sxs-lookup"><span data-stu-id="59903-144">Notice that although GeographyKey is defined as a column in the Reseller table, no dimension attribute is defined in the Reseller dimension based on this column.</span></span> <span data-ttu-id="59903-145">Geography ディメンションでは、Geography がディメンション属性として定義されています。Geography が、そのディメンションの基となるテーブルをファクト テーブルにリンクするキー列であるためです。</span><span class="sxs-lookup"><span data-stu-id="59903-145">Geography is defined as a dimension attribute in the Geography dimension because it is the key column that links the underlying table for that dimension to the fact table.</span></span>

2.  <span data-ttu-id="59903-146">**Geography Key** 属性を **Reseller** ディメンションに追加するには、 **[データ ソース ビュー]** ペインで **[GeographyKey]** を右クリックし、 **[列から新しい属性を作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59903-146">To add a **Geography Key** attribute to the **Reseller** dimension, right-click **GeographyKey** in the **Data Source View** pane, and then click **New Attribute from Column**.</span></span>

3.  <span data-ttu-id="59903-147">**[属性]** ペインで、 **[Geography Key]** をクリックします。次に、[プロパティ] ウィンドウで **AttributeHierarchyOptimizedState** プロパティを **NotOptimized**に設定します。さらに、 **AttributeHierarchyOrdered** プロパティを **False**に設定し、 **AttributeHierarchyVisible** プロパティを **False**に設定します。</span><span class="sxs-lookup"><span data-stu-id="59903-147">In the **Attributes** pane, select **Geography Key**, and then, in the Properties window, set the **AttributeHierarchyOptimizedState** property to **NotOptimized**, the **AttributeHierarchyOrdered** property to **False**, and the **AttributeHierarchyVisible** property to **False.**</span></span>

     <span data-ttu-id="59903-148">Reseller ディメンションの Geography Key 属性は、Geography ディメンションを Reseller Sales ファクト テーブルにリンクするためにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="59903-148">The Geography Key attribute in the Reseller dimension will only be used to link the Geography dimension to the Reseller Sales fact table.</span></span> <span data-ttu-id="59903-149">Geography Key 属性は表示しないため、この属性階層の表示を定義する値はありません。</span><span class="sxs-lookup"><span data-stu-id="59903-149">Because it will not be used for browsing, there is no value in defining this attribute hierarchy as visible.</span></span> <span data-ttu-id="59903-150">また、この属性階層の並べ替えや最適化を行っても、処理パフォーマンスを低下させるだけです。</span><span class="sxs-lookup"><span data-stu-id="59903-150">Additionally, ordering and optimizing the attribute hierarchy will only negatively affect processing performance.</span></span> <span data-ttu-id="59903-151">しかし、2 つのディメンション間を結ぶリンクとしてのみ機能するように、この属性を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="59903-151">However, the attribute must be enabled to serve as the link between the two dimensions.</span></span>

4.  <span data-ttu-id="59903-152">チュートリアルキューブのキューブデザイナーに切り替え [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 、[ディメンションの**使用法**] タブをクリックし、**再販業者の Sales**メジャーグループと**Geography**キューブディメンションの交差部分にある省略記号ボタン ([.**..**]) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59903-152">Switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, click the **Dimension Usage** tab, and then click the ellipsis button (**...**) at the intersection of the **Reseller Sales** measure group and the **Geography** cube dimension.</span></span>

5.  <span data-ttu-id="59903-153">**[リレーションシップの種類の選択]** ボックスの一覧から **[参照対象]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59903-153">In the **Select relationship type** list, select **Referenced**.</span></span>

6.  <span data-ttu-id="59903-154">**[中間ディメンション]** ボックスの一覧から **[Reseller]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="59903-154">In the **Intermediate dimension** list, select **Reseller**.</span></span>

7.  <span data-ttu-id="59903-155">**[参照ディメンションの属性]** ボックスの一覧から **[Geography Key]** を選択します。次に、 **[中間ディメンションの属性]** ボックスの一覧から **[Geography Key]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="59903-155">In the **Reference dimension attribute** list, select **Geography Key**, and then select **Geography Key** in the **Intermediate dimension attribute** list.</span></span>

     <span data-ttu-id="59903-156">**[具体化する]** チェック ボックスがオンになっています。</span><span class="sxs-lookup"><span data-stu-id="59903-156">Notice that the **Materialize** check box is selected.</span></span> <span data-ttu-id="59903-157">これは、MOLAP ディメンションの既定設定です。</span><span class="sxs-lookup"><span data-stu-id="59903-157">This is the default setting for MOLAP dimensions.</span></span> <span data-ttu-id="59903-158">ディメンション属性のリンクを具体化すると、各行のファクト テーブルおよび参照ディメンション間のリンクの値が具体化され、処理中にディメンションの MOLAP 構造に格納されます。</span><span class="sxs-lookup"><span data-stu-id="59903-158">Materializing the dimension attribute link causes the value of the link between the fact table and the reference dimension for each row to be materialized, or stored, in the dimension's MOLAP structure during processing.</span></span> <span data-ttu-id="59903-159">この操作は、処理パフォーマンスやストレージの要件に少しだけ影響しますが、クエリ パフォーマンスを (場合により大幅に) 向上させます。</span><span class="sxs-lookup"><span data-stu-id="59903-159">This will have a minor effect on processing performance and storage requirements, but will increase query performance (sometimes significantly).</span></span>

8.  <span data-ttu-id="59903-160">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59903-160">Click **OK**.</span></span>

     <span data-ttu-id="59903-161">**Geography** キューブ ディメンションが **Reseller Sales** メジャー グループにリンクされました。</span><span class="sxs-lookup"><span data-stu-id="59903-161">Notice that the **Geography** cube dimension is now linked to the **Reseller Sales** measure group.</span></span> <span data-ttu-id="59903-162">このアイコンは、リレーションシップが参照ディメンションのリレーションシップであることを表します。</span><span class="sxs-lookup"><span data-stu-id="59903-162">The icon indicates that the relationship is a referenced dimension relationship.</span></span>

9. <span data-ttu-id="59903-163">**[ディメンションの使用法]** タブを開き、 **[ディメンション]** の一覧で **[Geography]** を右クリックし、 **[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59903-163">In the **Dimensions** list on the **Dimension Usage** tab, right-click **Geography**, and then click **Rename**.</span></span>

10. <span data-ttu-id="59903-164">このキューブディメンションの名前をに変更 `Reseller Geography` します。</span><span class="sxs-lookup"><span data-stu-id="59903-164">Change the name of this cube dimension to `Reseller Geography`.</span></span>

     <span data-ttu-id="59903-165">このキューブ ディメンションを **Reseller Sales** メジャー グループにリンクしたので、以降は同キューブ ディメンションを明示的にキューブ内で使用できます。これにより、ユーザーの混乱を避けることができます。</span><span class="sxs-lookup"><span data-stu-id="59903-165">Because this cube dimension is now linked to the **Reseller Sales** measure group, users will benefit from explicitly defining its use in the cube, to avoid possible user confusion.</span></span>

## <a name="successfully-dimensioning-reseller-sales-by-geography"></a><span data-ttu-id="59903-166">販売店の売上と地域の関連付け</span><span class="sxs-lookup"><span data-stu-id="59903-166">Successfully Dimensioning Reseller Sales by Geography</span></span>

1.  <span data-ttu-id="59903-167">**[ビルド]** メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59903-167">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="59903-168">配置が正常に完了したら、 **Tutorial キューブのキューブ デザイナーで** [ブラウザー] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] タブをクリックし、 **[再接続]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="59903-168">When deployment has successfully completed, click the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Reconnect** button.</span></span>

3.  <span data-ttu-id="59903-169">メタデータペインで、[] を展開し、[ `Reseller Geography` **地域**] を右クリックして、[**行領域に追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59903-169">In the metadata pane, expand `Reseller Geography`, right-click **Geographies**, and then click **Add to Row Area**.</span></span>

     <span data-ttu-id="59903-170">次の図を見ると、 **Reseller Sales-Sales Amount** メジャーが、 **Geographies** ユーザー定義階層の **Country-Region** 属性によって正しく多次元化されたことがわかります。</span><span class="sxs-lookup"><span data-stu-id="59903-170">Notice that the **Reseller Sales-Sales Amount** measure is now correctly dimensioned by the **Country-Region** attribute of the **Geographies** user-defined hierarchy, as shown in the following image.</span></span>

     <span data-ttu-id="59903-171">![[リレーションシップの定義] ダイアログボックス](../../2014/tutorials/media/l5-referencedrelationship-5.gif "[リレーションシップの定義] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="59903-171">![Define Relationship dialog box](../../2014/tutorials/media/l5-referencedrelationship-5.gif "Define Relationship dialog box")</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="59903-172">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="59903-172">Next Task in Lesson</span></span>
 [<span data-ttu-id="59903-173">ファクト リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="59903-173">Defining a Fact Relationship</span></span>](lesson-5-2-defining-a-fact-relationship.md)

## <a name="see-also"></a><span data-ttu-id="59903-174">参照</span><span class="sxs-lookup"><span data-stu-id="59903-174">See Also</span></span>
 <span data-ttu-id="59903-175">[属性リレーションシップ](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)[は、参照リレーションシップと参照リレーションシッププロパティを定義し](multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)ます</span><span class="sxs-lookup"><span data-stu-id="59903-175">[Attribute Relationships](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md) [Define a Referenced Relationship and Referenced Relationship Properties](multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)</span></span>


