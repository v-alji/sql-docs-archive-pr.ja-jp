---
title: Product ディメンションの変更 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8e3ffecd-7f40-41a8-8735-bc9858a310cb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 04c0a778a73371dada92c9ff207a17366a2fbc7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642397"
---
# <a name="modifying-the-product-dimension"></a><span data-ttu-id="b7ff4-102">Product ディメンションの変更</span><span class="sxs-lookup"><span data-stu-id="b7ff4-102">Modifying the Product Dimension</span></span>
  <span data-ttu-id="b7ff4-103">このトピックの実習では、名前付き計算を使用して製品ラインにわかりやすい名前を指定し、Product ディメンションに階層を定義して、その階層の (All) メンバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-103">In the tasks in this topic, you use a named calculation to provide more descriptive names for the product lines, define a hierarchy in the Product dimension, and specify the (All) member name for the hierarchy.</span></span> <span data-ttu-id="b7ff4-104">また、属性をグループ化して別々の表示フォルダーに格納します。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-104">You also group attributes into display folders.</span></span>  
  
## <a name="adding-a-named-calculation"></a><span data-ttu-id="b7ff4-105">名前付き計算の追加</span><span class="sxs-lookup"><span data-stu-id="b7ff4-105">Adding a Named Calculation</span></span>  
 <span data-ttu-id="b7ff4-106">データ ソース ビューで名前付き計算をテーブルに追加できます。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-106">You can add a named calculation to a table in a data source view.</span></span> <span data-ttu-id="b7ff4-107">次の実習では、製品ラインの完全な名前を表示する名前付き計算を作成します。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-107">In the following task, you create a named calculation that displays the full product line name.</span></span>  
  
#### <a name="to-add-a-named-calculation"></a><span data-ttu-id="b7ff4-108">名前付き計算を追加するには</span><span class="sxs-lookup"><span data-stu-id="b7ff4-108">To add a named calculation</span></span>  
  
1.  <span data-ttu-id="b7ff4-109">**Adventure Works DW 2012** データ ソース ビューを開くには、ソリューション エクスプローラーの **[データ ソース ビュー]** フォルダーで **[Adventure Works DW 2012]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-109">To open the **Adventure Works DW 2012** data source view, double-click **Adventure Works DW 2012** in the **Data Source Views** folder in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="b7ff4-110">ダイアグラム ペインの下部で **[Product]** テーブル ヘッダーを右クリックし、 **[新しい名前付き計算]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-110">In the bottom of the diagram pane, right-click the **Product** table header, and then click **New Named Calculation**.</span></span>  
  
3.  <span data-ttu-id="b7ff4-111">[**名前付き計算の作成**] ダイアログボックスで、[ `ProductLineName` **列名**] ボックスに「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-111">In the **Create Named Calculation** dialog box, type `ProductLineName` in the **Column name** box.</span></span>  
  
4.  <span data-ttu-id="b7ff4-112">**[式]** ボックスに、次の **CASE** ステートメントを入力するか、またはコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-112">In the **Expression** box, type or copy and paste the following **CASE** statement:</span></span>  
  
    ```  
    CASE ProductLine  
       WHEN 'M' THEN 'Mountain'  
       WHEN 'R' THEN 'Road'  
       WHEN 'S' THEN 'Accessory'  
       WHEN 'T' THEN 'Touring'  
       ELSE 'Components'  
    END  
    ```  
  
     <span data-ttu-id="b7ff4-113">この **CASE** ステートメントは、キューブ内の各製品ラインにわかりやすい名前を付けるためのものです。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-113">This **CASE** statement creates user-friendly names for each product line in the cube.</span></span>  
  
5.  <span data-ttu-id="b7ff4-114">[ **OK** ] をクリックして、 `ProductLineName` 名前付き計算を作成します。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-114">Click **OK** to create the `ProductLineName` named calculation.</span></span> <span data-ttu-id="b7ff4-115">場合によっては、しばらく待つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-115">You might need to wait.</span></span>  
  
6.  <span data-ttu-id="b7ff4-116">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-116">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="modifying-the-namecolumn-property-of-an-attribute"></a><span data-ttu-id="b7ff4-117">属性の NameColumn プロパティの変更</span><span class="sxs-lookup"><span data-stu-id="b7ff4-117">Modifying the NameColumn Property of an Attribute</span></span>  
  
#### <a name="to-modify-the-namecolumn-property-value-of-an-attribute"></a><span data-ttu-id="b7ff4-118">属性の NameColumn プロパティ値を変更するには</span><span class="sxs-lookup"><span data-stu-id="b7ff4-118">To modify the NameColumn property value of an attribute</span></span>  
  
1.  <span data-ttu-id="b7ff4-119">Product ディメンションのディメンション デザイナーに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-119">Switch to Dimension Designer for the Product dimension.</span></span> <span data-ttu-id="b7ff4-120">これを行うには、ソリューション エクスプローラーの **[ディメンション]** ノードで **[Product]** ディメンションをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-120">To do this, double-click the **Product** dimension in the **Dimensions** node of Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="b7ff4-121">**[ディメンション構造]** タブの **[属性]** ペインで、 **[Product Line]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-121">In the **Attributes** pane of the **Dimension Structure** tab, select **Product Line**.</span></span>  
  
3.  <span data-ttu-id="b7ff4-122">画面の右側にあるプロパティウィンドウで、ウィンドウの下部にある [ **NameColumn** ] プロパティフィールドをクリックし、参照ボタン ([.**..**]) をクリックして、[**名前列**] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-122">In the Properties window on the right side of the screen, click the **NameColumn** property field at the bottom of the window, and then click the browse (**...**) button to open the **Name Column** dialog box.</span></span> <span data-ttu-id="b7ff4-123">(場合によっては、画面右側の **[プロパティ]** タブをクリックして、[プロパティ] ウィンドウを開く必要があります)。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-123">(You might need to click the **Properties** tab on the right side of the screen to open the Properties window.</span></span>  
  
4.  <span data-ttu-id="b7ff4-124">[ `ProductLineName` 基になる**列**] ボックスの一覧の下部にあるを選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-124">Select `ProductLineName` at the bottom of the **Source column** list, and then click **OK**.</span></span>  
  
     <span data-ttu-id="b7ff4-125">NameColumn フィールドに、テキスト " **Product.ProductLineName (WChar)**" が表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-125">The NameColumn field now contains the text, **Product.ProductLineName (WChar)**.</span></span> <span data-ttu-id="b7ff4-126">これで、 **Product Line** 属性階層のメンバーが、簡略名ではなく製品ラインの完全な名前で表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-126">The members of the **Product Line** attribute hierarchy now display the full name of the product line instead of an abbreviated product line name.</span></span>  
  
5.  <span data-ttu-id="b7ff4-127">**[ディメンション構造]** タブの **[属性]** ペインで、 **[Product Key]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-127">In the **Attributes** pane of the **Dimension Structure** tab, select **Product Key**.</span></span>  
  
6.  <span data-ttu-id="b7ff4-128">プロパティウィンドウで、[ **NameColumn** ] プロパティフィールドをクリックし、参照ボタン ([.**..**]) をクリックして、[**名前列**] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-128">In the Properties window, click the **NameColumn** property field, and then click the ellipsis browse (**...**) button to open the **Name Column** dialog box.</span></span>  
  
7.  <span data-ttu-id="b7ff4-129">**[基になる列]** ボックスの一覧で **[EnglishProductName]** を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-129">Select **EnglishProductName** in the **Source column** list, and then click **OK**.</span></span>  
  
     <span data-ttu-id="b7ff4-130">NameColumn フィールドに、テキスト " **Product.EnglishProductName (WChar)**" が表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-130">The NameColumn field now contains the text, **Product.EnglishProductName (WChar)**.</span></span>  
  
8.  <span data-ttu-id="b7ff4-131">プロパティウィンドウで、上にスクロールし、[ **Name** ] プロパティフィールドをクリックして「」と入力し `Product Name` ます。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-131">In the Properties window, scroll up, click the **Name** property field, and then type `Product Name`.</span></span>  
  
## <a name="creating-a-hierarchy"></a><span data-ttu-id="b7ff4-132">階層の作成</span><span class="sxs-lookup"><span data-stu-id="b7ff4-132">Creating a Hierarchy</span></span>  
  
#### <a name="to-create-a-hierarchy"></a><span data-ttu-id="b7ff4-133">階層を作成するには</span><span class="sxs-lookup"><span data-stu-id="b7ff4-133">To create a hierarchy</span></span>  
  
1.  <span data-ttu-id="b7ff4-134">**[属性]** ペインの **[Product Line]** 属性を **[階層]** ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-134">Drag the **Product Line** attribute from the **Attributes** pane into the **Hierarchies** pane.</span></span>  
  
2.  <span data-ttu-id="b7ff4-135">**[属性]** ペインの **[Model Name]** 属性を、 **\<new level>** [階層] **ペインの** セル ( **[Product Line]** レベルの下) にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-135">Drag the **Model Name** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **Product Line** level.</span></span>  
  
3.  <span data-ttu-id="b7ff4-136">[ `Product Name` **属性**] ペインの属性を、[ **\<new level>** **階層**] ペインのセル (**モデル名**レベルの下) にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-136">Drag the `Product Name` attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **Model Name** level.</span></span> <span data-ttu-id="b7ff4-137">(前のセクションで、Product Key を Product Name に名前変更しました)。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-137">(You renamed Product Key to Product Name in the previous section.)</span></span>  
  
4.  <span data-ttu-id="b7ff4-138">[**ディメンション構造**] タブの [**階層**] ペインで、[ **hierarchy** ] 階層のタイトルバーを右クリックし、[**名前の変更**] をクリックして「」と入力し `Product Model Lines` ます。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-138">In the **Hierarchies** pane of the **Dimension Structure** tab, right-click the title bar of the **Hierarchy** hierarchy, click **Rename**, and then type `Product Model Lines`.</span></span>  
  
     <span data-ttu-id="b7ff4-139">階層の名前はになりました `Product Model Lines` 。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-139">The name of the hierarchy is now `Product Model Lines`.</span></span>  
  
5.  <span data-ttu-id="b7ff4-140">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-140">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="specifying-folder-names-and-all-member-names"></a><span data-ttu-id="b7ff4-141">フォルダー名およびすべてのメンバー名の指定</span><span class="sxs-lookup"><span data-stu-id="b7ff4-141">Specifying Folder Names and All Member Names</span></span>  
  
#### <a name="to-specify-the-folder-and-member-names"></a><span data-ttu-id="b7ff4-142">フォルダー名とメンバー名を指定するには</span><span class="sxs-lookup"><span data-stu-id="b7ff4-142">To specify the folder and member names</span></span>  
  
1.  <span data-ttu-id="b7ff4-143">**[属性]** ペインで、Ctrl キーを押しながら次の各属性をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-143">In the **Attributes** pane, select the following attributes by holding down the CTRL key while clicking each of them:</span></span>  
  
    -   <span data-ttu-id="b7ff4-144">**クラス**</span><span class="sxs-lookup"><span data-stu-id="b7ff4-144">**Class**</span></span>  
  
    -   <span data-ttu-id="b7ff4-145">**色**</span><span class="sxs-lookup"><span data-stu-id="b7ff4-145">**Color**</span></span>  
  
    -   <span data-ttu-id="b7ff4-146">**製造日**</span><span class="sxs-lookup"><span data-stu-id="b7ff4-146">**Days To Manufacture**</span></span>  
  
    -   <span data-ttu-id="b7ff4-147">**Reorder Point**</span><span class="sxs-lookup"><span data-stu-id="b7ff4-147">**Reorder Point**</span></span>  
  
    -   <span data-ttu-id="b7ff4-148">**Safety Stock Level**</span><span class="sxs-lookup"><span data-stu-id="b7ff4-148">**Safety Stock Level**</span></span>  
  
    -   <span data-ttu-id="b7ff4-149">**[サイズ]**</span><span class="sxs-lookup"><span data-stu-id="b7ff4-149">**Size**</span></span>  
  
    -   <span data-ttu-id="b7ff4-150">**Size Range**</span><span class="sxs-lookup"><span data-stu-id="b7ff4-150">**Size Range**</span></span>  
  
    -   <span data-ttu-id="b7ff4-151">**Style**</span><span class="sxs-lookup"><span data-stu-id="b7ff4-151">**Style**</span></span>  
  
    -   <span data-ttu-id="b7ff4-152">**Weight**</span><span class="sxs-lookup"><span data-stu-id="b7ff4-152">**Weight**</span></span>  
  
2.  <span data-ttu-id="b7ff4-153">プロパティウィンドウの [ **attributehierarchydisplayfolder]** ] プロパティフィールドに、「」と入力 `Stocking` します。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-153">In the **AttributeHierarchyDisplayFolder** property field in the Properties window, type `Stocking`.</span></span>  
  
     <span data-ttu-id="b7ff4-154">上記の属性をグループ化し、1 つの表示フォルダーに表示されるようにしました。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-154">You have now grouped these attributes into a single display folder.</span></span>  
  
3.  <span data-ttu-id="b7ff4-155">**[属性]** ペインで、次の属性を選択します。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-155">In the **Attributes** pane, select the following attributes:</span></span>  
  
    -   <span data-ttu-id="b7ff4-156">**Dealer Price**</span><span class="sxs-lookup"><span data-stu-id="b7ff4-156">**Dealer Price**</span></span>  
  
    -   <span data-ttu-id="b7ff4-157">**List Price**</span><span class="sxs-lookup"><span data-stu-id="b7ff4-157">**List Price**</span></span>  
  
    -   <span data-ttu-id="b7ff4-158">**Standard Cost**</span><span class="sxs-lookup"><span data-stu-id="b7ff4-158">**Standard Cost**</span></span>  
  
4.  <span data-ttu-id="b7ff4-159">プロパティウィンドウの [ **attributehierarchydisplayfolder]** ] プロパティセルに、「」と入力 `Financial` します。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-159">In the **AttributeHierarchyDisplayFolder** property cell in the Properties window, type `Financial`.</span></span>  
  
     <span data-ttu-id="b7ff4-160">上記の属性をグループ化し、別の表示フォルダーに表示されるようにしました。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-160">You have now grouped these attributes into a second display folder.</span></span>  
  
5.  <span data-ttu-id="b7ff4-161">**[属性]** ペインで、次の属性を選択します。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-161">In the **Attributes** pane, select the following attributes:</span></span>  
  
    -   <span data-ttu-id="b7ff4-162">**終了日**</span><span class="sxs-lookup"><span data-stu-id="b7ff4-162">**End Date**</span></span>  
  
    -   <span data-ttu-id="b7ff4-163">**[開始日]**</span><span class="sxs-lookup"><span data-stu-id="b7ff4-163">**Start Date**</span></span>  
  
    -   <span data-ttu-id="b7ff4-164">**状態**</span><span class="sxs-lookup"><span data-stu-id="b7ff4-164">**Status**</span></span>  
  
6.  <span data-ttu-id="b7ff4-165">プロパティウィンドウの [ **attributehierarchydisplayfolder]** ] プロパティセルに、「」と入力 `History` します。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-165">In the **AttributeHierarchyDisplayFolder** property cell in the Properties window, type `History`.</span></span>  
  
     <span data-ttu-id="b7ff4-166">上記の属性をグループ化し、3 番目の表示フォルダーに表示されるようにしました。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-166">You have now grouped these attributes into a third display folder.</span></span>  
  
7.  <span data-ttu-id="b7ff4-167">[ `Product Model Lines` **階層**] ペインで階層を選択し、プロパティウィンドウの**allmembername**プロパティをに変更し `All Products` ます。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-167">Select the `Product Model Lines` hierarchy in the **Hierarchies** pane, and then change the **AllMemberName** property in the Properties window to `All Products`.</span></span>  
  
8.  <span data-ttu-id="b7ff4-168">[**階層**] ペインの空いている領域をクリックし、プロパティウィンドウの上部にある**attributeallmembername**プロパティをに変更し `All Products` ます。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-168">Click an open area of the **Hierarchies** pane, and then change the **AttributeAllMemberName** property at the top of the Properties window to `All Products`.</span></span>  
  
     <span data-ttu-id="b7ff4-169">空いている領域をクリックすると、Product ディメンション自体のプロパティを変更できます。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-169">Clicking an open area lets you modify properties of the Product dimension itself.</span></span> <span data-ttu-id="b7ff4-170">**[属性]** ペインの属性リストの上部にある **[Product]** をクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-170">You could also click **Product** at the top of the attributes list in the **Attributes** pane.</span></span>  
  
9. <span data-ttu-id="b7ff4-171">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-171">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-attribute-relationships"></a><span data-ttu-id="b7ff4-172">属性リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="b7ff4-172">Defining Attribute Relationships</span></span>  
 <span data-ttu-id="b7ff4-173">基になるデータで属性リレーションシップがサポートされる場合、属性間の属性リレーションシップを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-173">If the underlying data supports it, you should define attribute relationships between attributes.</span></span> <span data-ttu-id="b7ff4-174">属性リレーションシップを定義すると、ディメンション、パーティション、およびクエリの処理速度が上がります。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-174">Defining attribute relationships speeds up dimension, partition, and query processing.</span></span> <span data-ttu-id="b7ff4-175">詳細については、「 [属性リレーションシップの定義](multidimensional-models/attribute-relationships-define.md) 」および「 [属性リレーションシップ](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-175">For more information, see [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md) and [Attribute Relationships](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).</span></span>  
  
#### <a name="to-define-attribute-relationships"></a><span data-ttu-id="b7ff4-176">属性リレーションシップを定義するには</span><span class="sxs-lookup"><span data-stu-id="b7ff4-176">To define attribute relationships</span></span>  
  
1.  <span data-ttu-id="b7ff4-177">Product ディメンションの **ディメンション デザイナー** で、 **[属性リレーションシップ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-177">In the **Dimension Designer** for the Product dimension, click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="b7ff4-178">ダイアグラムで、 **[Model Name]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-178">In the diagram, right-click the **Model Name** attribute, and then click **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="b7ff4-179">**[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[Model Name]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-179">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Model Name**.</span></span> <span data-ttu-id="b7ff4-180">**[関連属性]** を **[Product Line]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-180">Set the **Related Attribute** to **Product Line**.</span></span>  
  
     <span data-ttu-id="b7ff4-181">時間が経過するとメンバー間のリレーションシップが変化する可能性があるため、 **[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類の設定は **[可変]** のままにします。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-181">In the **Relationship type** list, leave the relationship type set to **Flexible** because relationships between the members might change over time.</span></span> <span data-ttu-id="b7ff4-182">たとえば、製品モデルが最終的に別の製品ラインに移動される場合があります。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-182">For example, a product model might eventually be moved to a different product line.</span></span>  
  
4.  <span data-ttu-id="b7ff4-183">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-183">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="b7ff4-184">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-184">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="reviewing-product-dimension-changes"></a><span data-ttu-id="b7ff4-185">Product ディメンションの変更の確認</span><span class="sxs-lookup"><span data-stu-id="b7ff4-185">Reviewing Product Dimension Changes</span></span>  
  
#### <a name="to-review-the-product-dimension-changes"></a><span data-ttu-id="b7ff4-186">Product ディメンションの変更を確認するには</span><span class="sxs-lookup"><span data-stu-id="b7ff4-186">To review the Product dimension changes</span></span>  
  
1.  <span data-ttu-id="b7ff4-187">**で、** [ビルド] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-187">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="b7ff4-188">" **配置が正常に完了しました** " というメッセージが表示されたら、 **Product** ディメンションの **ディメンション デザイナー** の **[ブラウザー]** タブをクリックし、ディメンション デザイナーのツール バーにある再接続ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-188">After you have received the **Deployment Completed Successfully** message, click the **Browser** tab of **Dimension Designer** for the **Product** dimension, and then click the Reconnect button on the toolbar of the designer.</span></span>  
  
3.  <span data-ttu-id="b7ff4-189">`Product Model Lines`[**階層**] ボックスの一覧でが選択されていることを確認し、を展開し `All Products` ます。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-189">Verify that `Product Model Lines` is selected in the **Hierarchy** list, and then expand `All Products`.</span></span>  
  
     <span data-ttu-id="b7ff4-190">**All**メンバーの名前がとして表示されていることに注意して `All Products` ください。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-190">Notice that the name of the **All** member appears as `All Products`.</span></span> <span data-ttu-id="b7ff4-191">これは、レッスンでは、階層の**Allmembername**プロパティをに変更したためです `All Products` 。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-191">This is because you changed the **AllMemberName** property for the hierarchy to `All Products` earlier in the lesson.</span></span> <span data-ttu-id="b7ff4-192">また、 **Product Line** レベルのメンバー名が、1 文字の簡略名から、わかりやすい名前に変わりました。</span><span class="sxs-lookup"><span data-stu-id="b7ff4-192">Also, the members of the **Product Line** level now have user-friendly names, instead of single-letter abbreviations.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="b7ff4-193">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="b7ff4-193">Next Task in Lesson</span></span>  
 [<span data-ttu-id="b7ff4-194">Date ディメンションの変更</span><span class="sxs-lookup"><span data-stu-id="b7ff4-194">Modifying the Date Dimension</span></span>](lesson-3-4-modifying-the-date-dimension.md)  
  
## <a name="see-also"></a><span data-ttu-id="b7ff4-195">参照</span><span class="sxs-lookup"><span data-stu-id="b7ff4-195">See Also</span></span>  
 <span data-ttu-id="b7ff4-196">[データソースビューで名前付き計算を定義する &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="b7ff4-196">[Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md) </span></span>  
 <span data-ttu-id="b7ff4-197">[ユーザー定義階層の作成](multidimensional-models/user-defined-hierarchies-create.md) </span><span class="sxs-lookup"><span data-stu-id="b7ff4-197">[Create User-Defined Hierarchies](multidimensional-models/user-defined-hierarchies-create.md) </span></span>  
 [<span data-ttu-id="b7ff4-198">属性階層の &#40;All&#41; レベルの構成</span><span class="sxs-lookup"><span data-stu-id="b7ff4-198">Configure the &#40;All&#41; Level for Attribute Hierarchies</span></span>](multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
