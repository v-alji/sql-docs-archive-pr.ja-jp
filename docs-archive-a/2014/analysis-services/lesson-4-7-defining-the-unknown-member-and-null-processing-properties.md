---
title: 不明なメンバーと Null 処理のプロパティの定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d9abb09c-9bfa-4e32-b530-8590e4383566
author: minewiskan
ms.author: owend
ms.openlocfilehash: cdd6504bec4f129f64d9bef6f6b0138e917888e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639777"
---
# <a name="defining-the-unknown-member-and-null-processing-properties"></a><span data-ttu-id="b3618-102">不明なメンバーと NULL 処理のプロパティの定義</span><span class="sxs-lookup"><span data-stu-id="b3618-102">Defining the Unknown Member and Null Processing Properties</span></span>
  <span data-ttu-id="b3618-103">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] がディメンションを処理するときに、ディメンションの属性を生成しているのは、データ ソース ビューのテーブルまたはビュー内の基になる列の各値です。</span><span class="sxs-lookup"><span data-stu-id="b3618-103">When [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] processes a dimension, all the distinct values from the underlying columns in the tables, or views in the data source view, populate the attributes in the dimension.</span></span> <span data-ttu-id="b3618-104">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] での処理中に NULL 値があった場合は、既定によって NULL は数値列ではゼロに、文字列型の列では空の文字列に変換されます。</span><span class="sxs-lookup"><span data-stu-id="b3618-104">If [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] encounters a null value during processing, by default, it converts this null to a zero for numeric columns or to an empty string for string columns.</span></span> <span data-ttu-id="b3618-105">この既定の設定を変更したり、基礎的なリレーショナル データ ウェアハウスに固有の抽出、変換、読み込みプロセスがあればそれらを使用して NULL 値を変換したりできます。</span><span class="sxs-lookup"><span data-stu-id="b3618-105">You can modify the default settings or convert null values in your extract, transform, and load process (if any) of the underlying relational data warehouse.</span></span> <span data-ttu-id="b3618-106">また、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] を使用し、ディメンションに対しては **UnknownMember** プロパティと **UnknownMemberName** プロパティ、ディメンションのキー属性に対しては **NullProcessing** プロパティという 3 つのプロパティを構成して、指定した値に NULL 値を変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="b3618-106">Additionally, you can have [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] convert the null value to a designated value by configuring three properties: the **UnknownMember** and **UnknownMemberName** properties for the dimension, and the **NullProcessing** property for the dimension's key attribute.</span></span>

 <span data-ttu-id="b3618-107">ディメンション ウィザードおよびキューブ ウィザードでは、ディメンションのキー属性が NULL 値を許容するかどうか、またはスノーフレーク ディメンションのルート属性が NULL 値を許容する列に基づいているかどうかを基準にして、これらのプロパティを有効化します。</span><span class="sxs-lookup"><span data-stu-id="b3618-107">The Dimension Wizard and the Cube Wizard will enable these properties for you based on whether the key attribute of a dimension is nullable or the root attribute of a snowflake dimension is based on a nullable column.</span></span> <span data-ttu-id="b3618-108">この場合では、キー属性の **NullProcessing** プロパティは **UnknownMember** に設定され、 **UnknownMember** プロパティは **Visible**に設定されます。</span><span class="sxs-lookup"><span data-stu-id="b3618-108">In these cases, the **NullProcessing** property of the key attribute will be set to **UnknownMember** and the **UnknownMember** property will be set to **Visible**.</span></span>

 <span data-ttu-id="b3618-109">ただし、このチュートリアルで Product ディメンションに対して行っているようにスノーフレーク ディメンションを段階的に構築する場合、またはディメンション デザイナーを使用してディメンションを定義してこれらの既存のディメンションをキューブに組み込む場合は、 **UnknownMember** プロパティおよび **NullProcessing** プロパティを手動で設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3618-109">However, when you build snowflaked dimensions incrementally, as we are doing with the Product dimension in this tutorial, or when you define dimensions using Dimension Designer and then incorporate these existing dimensions into a cube, the **UnknownMember** and **NullProcessing** properties might need to be set manually.</span></span>

 <span data-ttu-id="b3618-110">このトピックの実習では、 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW のデータ ソース ビューに追加するスノーフレーク テーブルから、製品カテゴリおよび製品サブカテゴリの属性を取得し、それらの属性を Product ディメンションに追加します。</span><span class="sxs-lookup"><span data-stu-id="b3618-110">In the tasks in this topic, you will add the product category and product subcategory attributes to the Product dimension from snowflaked tables that you will add to the [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW data source view.</span></span> <span data-ttu-id="b3618-111">次に、Product ディメンションの**UnknownMember**プロパティを有効にし、 `Assembly Components` **UnknownMemberName**プロパティの値としてを指定し `Subcategory` 、 `Category` 属性と属性を product name 属性に関連付けてから、スノーフレークテーブルをリンクするメンバーキー属性のカスタムエラー処理を定義します。</span><span class="sxs-lookup"><span data-stu-id="b3618-111">You will then enable the **UnknownMember** property for the Product dimension, specify `Assembly Components` as the value for the **UnknownMemberName** property, relate the `Subcategory` and `Category` attributes to the product name attribute, and then define custom error handling for the member key attribute that links the snowflaked tables.</span></span>

> [!NOTE]
>  <span data-ttu-id="b3618-112">キューブ ウィザードを使用して [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブを最初に定義したときに Subcategory 属性と Category 属性を追加していれば、これらの手順は自動的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="b3618-112">If you have added the Subcategory and Category attributes when you originally defined the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube using the Cube Wizard, these steps would have been performed for you automatically.</span></span>

## <a name="reviewing-error-handling-and-unknown-member-properties-in-the-product-dimension"></a><span data-ttu-id="b3618-113">Product ディメンションでのエラー処理のプロパティと不明なメンバーのプロパティの確認</span><span class="sxs-lookup"><span data-stu-id="b3618-113">Reviewing Error Handling and Unknown Member Properties in the Product Dimension</span></span>

1.  <span data-ttu-id="b3618-114">**Product** ディメンションのディメンション デザイナーに切り替え、 **[ディメンション構造]** タブをクリックします。次に、 **[属性]** ペインで **[Product]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3618-114">Switch to Dimension Designer for the **Product** dimension, click the **Dimension Structure** tab, and then select **Product** in the **Attributes** pane.</span></span>

     <span data-ttu-id="b3618-115">ディメンション自体のプロパティを表示し、修正できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="b3618-115">This enables you to view and modify the properties of the dimension itself.</span></span>

2.  <span data-ttu-id="b3618-116">[プロパティ] ウィンドウで、 **UnknownMember** プロパティと **UnknownMemberName** プロパティを確認します。</span><span class="sxs-lookup"><span data-stu-id="b3618-116">In the Properties window, review the **UnknownMember** and **UnknownMemberName** properties.</span></span>

     <span data-ttu-id="b3618-117">**UnknownMember** プロパティは有効になっていません。このプロパティの値が **Visible** または **Hidden** ではなく、 **None**に設定されているためです。また、 **UnknownMemberName** プロパティには名前が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="b3618-117">Notice that the **UnknownMember** property is not enabled, because its value is set to **None** instead of **Visible** or **Hidden**, and that no name is specified for the **UnknownMemberName** property.</span></span>

3.  <span data-ttu-id="b3618-118">[プロパティ] ウィンドウで、 **ErrorConfiguration** プロパティのセルをクリックして、 **[(カスタム)]** を選択します。次に、 **ErrorConfiguration** プロパティ コレクションを展開します。</span><span class="sxs-lookup"><span data-stu-id="b3618-118">In the Properties window, select **(custom)** in the **ErrorConfiguration** property cell, and then expand the **ErrorConfiguration** properties collection.</span></span>

     <span data-ttu-id="b3618-119">**ErrorConfiguration** プロパティを **[(Custom)]** に設定すると、既定のエラー構成設定を表示できます。既定のエラー構成設定は変更されていません。</span><span class="sxs-lookup"><span data-stu-id="b3618-119">Setting the **ErrorConfiguration** property to **(custom)** allows you to view the default error configuration settings - it does not change any settings.</span></span>

4.  <span data-ttu-id="b3618-120">キーおよび NULL キーについて、エラーの構成のプロパティを確認します。変更はしないでください。</span><span class="sxs-lookup"><span data-stu-id="b3618-120">Review the key and null key error configuration properties, but do not make any changes.</span></span>

     <span data-ttu-id="b3618-121">NULL キーが不明なメンバーに変換される際に、この変換に関連する処理エラーが無視されていることがわかります (これが既定の動作です)。</span><span class="sxs-lookup"><span data-stu-id="b3618-121">Notice that, by default, when null keys are converted to the unknown member and the processing error associated with this conversion is ignored.</span></span>

     <span data-ttu-id="b3618-122">次の図は、 **ErrorConfiguration** プロパティ コレクションのプロパティ設定を示しています。</span><span class="sxs-lookup"><span data-stu-id="b3618-122">The following image shows the property settings for the **ErrorConfiguration** properties collection.</span></span>

     <span data-ttu-id="b3618-123">![ErrorConfiguration プロパティ コレクション](../../2014/tutorials/media/l4-productdimensionerrorconfig-1.gif "ErrorConfiguration プロパティ コレクション")</span><span class="sxs-lookup"><span data-stu-id="b3618-123">![ErrorConfiguration property collection](../../2014/tutorials/media/l4-productdimensionerrorconfig-1.gif "ErrorConfiguration property collection")</span></span>

5.  <span data-ttu-id="b3618-124">[**ブラウザー** ] タブをクリックし、[**階層**] ボックスの一覧で [ **Product Model Lines** ] が選択されていることを確認して、を展開し `All Products` ます。</span><span class="sxs-lookup"><span data-stu-id="b3618-124">Click the **Browser** tab, verify that **Product Model Lines** is selected in the **Hierarchy** list, and then expand `All Products`.</span></span>

     <span data-ttu-id="b3618-125">Product Line レベルには 5 つのメンバーが存在します。</span><span class="sxs-lookup"><span data-stu-id="b3618-125">Notice the five members of the Product Line level.</span></span>

6.  <span data-ttu-id="b3618-126">**[Components]** を展開します。 **Model Name** レベルのメンバーのうち、ラベルが付いていないメンバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="b3618-126">Expand **Components**, and then expand the unlabeled member of the **Model Name** level.</span></span>

     <span data-ttu-id="b3618-127">次の図のように、このレベルには、アジャスタブル レース ( **Adjustable Race** ) など、他の部品を組み立てるときに使用するアセンブリ部品が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b3618-127">This level contains the assembly components that are used when building other components, starting with the **Adjustable Race** product, as shown in the following image.</span></span>

     <span data-ttu-id="b3618-128">![他の部品を組み立てるのに使用するアセンブリ部品](../../2014/tutorials/media/l4-productdimensionerrorconfig-2.gif "他の部品を組み立てるのに使用するアセンブリ部品")</span><span class="sxs-lookup"><span data-stu-id="b3618-128">![Assembly components used to build other components](../../2014/tutorials/media/l4-productdimensionerrorconfig-2.gif "Assembly components used to build other components")</span></span>

## <a name="defining-attributes-from-snowflaked-tables-and-a-product-category-user-defined-hierarchy"></a><span data-ttu-id="b3618-129">スノーフレーク テーブルおよび Product Category ユーザー定義階層の属性の定義</span><span class="sxs-lookup"><span data-stu-id="b3618-129">Defining Attributes from Snowflaked Tables and a Product Category User-Defined Hierarchy</span></span>

1.  <span data-ttu-id="b3618-130">[!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW データ ソース ビューのデータ ソース ビュー デザイナーを開き、 **[ダイアグラム オーガナイザー]** ペインで **[Reseller Sales]** を選択します。次に、 **の** [データ ソース ビュー] **メニューの** [オブジェクトの追加と削除] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3618-130">Open Data Source View Designer for the [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW data source view, select **Reseller Sales** in the **Diagram Organizer** pane, and then click **Add/Remove Objects** on the **Data Source View** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>

     <span data-ttu-id="b3618-131">**[テーブルの追加と削除]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="b3618-131">The **Add/Remove Tables** dialog box opens.</span></span>

2.  <span data-ttu-id="b3618-132">**[含まれているオブジェクト]** ボックスの一覧の **[DimProduct (dbo)]** をクリックします。次に、 **[関連テーブルの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3618-132">In the **Included objects** list, select **DimProduct (dbo)**, and then click **Add Related Tables**.</span></span>

     <span data-ttu-id="b3618-133">**DimProductSubcategory (dbo)** と **FactProductInventory (dbo)** の両方が追加されます。</span><span class="sxs-lookup"><span data-stu-id="b3618-133">Both **DimProductSubcategory (dbo)** and **FactProductInventory (dbo)** are added.</span></span> <span data-ttu-id="b3618-134">**FactProductInventory (dbo)** を削除して、 **DimProductSubcategory (dbo)** テーブルだけが **[含まれているオブジェクト]** の一覧に追加されるようにします。</span><span class="sxs-lookup"><span data-stu-id="b3618-134">Remove **FactProductInventory (dbo)** so that just the **DimProductSubcategory (dbo)** table is added to the **Included objects** list.</span></span>

3.  <span data-ttu-id="b3618-135">既定では、最後に追加した **DimProductSubcategory (dbo)** テーブルが選択されます。この状態で、 **[関連テーブルの追加]** をもう一度クリックします。</span><span class="sxs-lookup"><span data-stu-id="b3618-135">With the **DimProductSubcategory (dbo)** table selected by default as the table most recently added, click **Add Related Tables** again.</span></span>

     <span data-ttu-id="b3618-136">**[含まれているオブジェクト]** の一覧に **DimProductCategory (dbo)** テーブルが追加されます。</span><span class="sxs-lookup"><span data-stu-id="b3618-136">The **DimProductCategory (dbo)** table is added to the **Included objects** list.</span></span>

4.  <span data-ttu-id="b3618-137">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3618-137">Click **OK**.</span></span>

5.  <span data-ttu-id="b3618-138">**の** [書式] [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]メニューで **[自動レイアウト]** をポイントし、 **[ダイアグラム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3618-138">On the **Format** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], point to **Auto Layout**, and then click **Diagram**.</span></span>

     <span data-ttu-id="b3618-139">**DimProductSubcategory (dbo)** テーブルと **DimProductCategory (dbo)** テーブルは互いにリンクしています。また、 **Product** テーブルを介して **ResellerSales** テーブルにもリンクしています。</span><span class="sxs-lookup"><span data-stu-id="b3618-139">Notice that the **DimProductSubcategory (dbo)** table and **DimProductCategory (dbo)** table are linked to each other, and also to the **ResellerSales** table through the **Product** table.</span></span>

6.  <span data-ttu-id="b3618-140">**Product** ディメンションのディメンション デザイナーに切り替え、 **[ディメンション構造]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3618-140">Switch to Dimension Designer for the **Product** dimension, and then click the **Dimension Structure** tab.</span></span>

7.  <span data-ttu-id="b3618-141">**[データ ソース ビュー]** ペイン内を右クリックし、 **[すべてのテーブルを表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3618-141">Right-click anywhere in the **Data Source View** pane, and then click **Show All Tables**.</span></span>

8.  <span data-ttu-id="b3618-142">**[データ ソース ビュー]** ペインで、 **DimProductCategory** テーブルを探します。次に、このテーブルの **ProductCategoryKey** を右クリックし、 **[列から新しい属性を作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3618-142">In the **Data Source View** pane, locate the **DimProductCategory** table, right-click **ProductCategoryKey** in that table, and then click **New Attribute from Column**.</span></span>

9. <span data-ttu-id="b3618-143">[**属性**] ペインで、この新しい属性の名前をに変更 `Category` します。</span><span class="sxs-lookup"><span data-stu-id="b3618-143">In the **Attributes** pane, change the name of this new attribute to `Category`.</span></span>

10. <span data-ttu-id="b3618-144">プロパティウィンドウで、[ **NameColumn** ] プロパティフィールドをクリックし、参照ボタン ([.**..**]) をクリックして、[**名前列**] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="b3618-144">In the Properties window, click in the **NameColumn** property field and then click the browse (**...**) button to open the **Name Column** dialog box.</span></span>

11. <span data-ttu-id="b3618-145">**[基になる列]** ボックスの一覧で **[EnglishProductCategoryName]** を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3618-145">Select **EnglishProductCategoryName** in the **Source column** list and then click **OK**.</span></span>

12. <span data-ttu-id="b3618-146">**[データ ソース ビュー]** ペインで、 **DimProductSubcategory** テーブルを探します。このテーブルの **ProductSubcategoryKey** を右クリックし、 **[列から新しい属性を作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3618-146">In the **Data Source View** pane, locate the **DimProductSubcategory** table, right-click **ProductSubcategoryKey** in that table, and then click **New Attribute from Column**.</span></span>

13. <span data-ttu-id="b3618-147">[**属性**] ペインで、この新しい属性の名前をに変更 `Subcategory` します。</span><span class="sxs-lookup"><span data-stu-id="b3618-147">In the **Attributes** pane, change the name of this new attribute to `Subcategory`.</span></span>

14. <span data-ttu-id="b3618-148">プロパティウィンドウで、[ **NameColumn** ] プロパティフィールドをクリックし、参照ボタン ([. **..])** をクリックして、[**名前列**] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="b3618-148">In the Properties window, click in the **NameColumn** property field and then click the browse **(...)** button to open the **Name Column** dialog box.</span></span>

15. <span data-ttu-id="b3618-149">**[基になる列]** ボックスの一覧で **[EnglishProductSubcategoryName]** を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3618-149">Select **EnglishProductSubcategoryName** in the **Source column** list and then click **OK**.</span></span>

16. <span data-ttu-id="b3618-150">**Product Categories**という名前の新しいユーザー定義階層を作成します。次のレベルは、上から下に、、 `Category` `Subcategory` 、および**製品名**の順に並べ替えられています。</span><span class="sxs-lookup"><span data-stu-id="b3618-150">Create a new user-defined hierarchy called **Product Categories** with the following levels, in order from top to bottom: `Category`, `Subcategory`, and **Product Name**.</span></span>

17. <span data-ttu-id="b3618-151">`All Products`Product Categories ユーザー定義階層の**allmembername**プロパティの値としてを指定します。</span><span class="sxs-lookup"><span data-stu-id="b3618-151">Specify `All Products` as the value for the **AllMemberName** property of the Product Categories user-defined hierarchy.</span></span>

## <a name="browsing-the-user-defined-hierarchies-in-the-product-dimension"></a><span data-ttu-id="b3618-152">Product ディメンションのユーザー定義階層の表示</span><span class="sxs-lookup"><span data-stu-id="b3618-152">Browsing the User-Defined Hierarchies in the Product Dimension</span></span>

1.  <span data-ttu-id="b3618-153">**Product** ディメンションの **ディメンション デザイナー** で、 **[ディメンションの構造]** タブのツール バーにある **[処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3618-153">On the toolbar of the **Dimension Structure** tab of **Dimension Designer** for the **Product** dimension, click **Process**.</span></span>

2.  <span data-ttu-id="b3618-154">**[はい]** をクリックして、プロジェクトを作成し、配置します。次に、 **[実行]** をクリックして、 **Product** ディメンションを処理します。</span><span class="sxs-lookup"><span data-stu-id="b3618-154">Click **Yes** to build and deploy the project, and then click **Run** to process the **Product** dimension.</span></span>

3.  <span data-ttu-id="b3618-155">処理が正常に完了したら、 **[処理の進行状況]** ダイアログ ボックスで **[ディメンション 'Product' の処理が正常に完了しました]** を展開し、 **[ディメンション属性 'Product Name' の処理が完了しました]** を展開します。次に、 **[SQL クエリ数 1]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="b3618-155">When processing has succeeded, expand **Processing Dimension 'Product' completed successfully** in the **Process Progress** dialog box, expand **Processing Dimension Attribute 'Product Name' completed**, and then expand **SQL queries 1**.</span></span>

4.  <span data-ttu-id="b3618-156">SELECT DISTINCT クエリをクリックし、 **[詳細表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3618-156">Click the SELECT DISTINCT query and then click **View Details**.</span></span>

     <span data-ttu-id="b3618-157">SELECT DISTINCT 句に WHERE 句が追加されています。次の図のように、この WHERE 句は、値を持たない製品を ProductSubcategoryKey から削除します。</span><span class="sxs-lookup"><span data-stu-id="b3618-157">Notice that a WHERE clause has been added to the SELECT DISTINCT clause that removes those products that have no value in the ProductSubcategoryKey column, as shown in the following image.</span></span>

     <span data-ttu-id="b3618-158">![SELECT DISTINCT 句に含まれた WHERE 句](../../2014/tutorials/media/l4-productnametraceline-1.gif "SELECT DISTINCT 句に含まれた WHERE 句")</span><span class="sxs-lookup"><span data-stu-id="b3618-158">![SELECT DISTINCT clause showing WHERE clause](../../2014/tutorials/media/l4-productnametraceline-1.gif "SELECT DISTINCT clause showing WHERE clause")</span></span>

5.  <span data-ttu-id="b3618-159">**[閉じる]** を 3 回クリックし、処理中のダイアログ ボックスをすべて閉じます。</span><span class="sxs-lookup"><span data-stu-id="b3618-159">Click **Close** three times to close all processing dialog boxes.</span></span>

6.  <span data-ttu-id="b3618-160">**Product** ディメンションのディメンション デザイナーで、 **[ブラウザー]** タブをクリックします。次に、 **[再接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3618-160">Click the **Browser** tab in Dimension Designer for the **Product** dimension, and then click **Reconnect**.</span></span>

7.  <span data-ttu-id="b3618-161">[**階層**] ボックスの一覧で [ **Product Model Lines** ] が表示されていることを確認し、 `All Products` []、[ **Components**] の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="b3618-161">Verify that **Product Model Lines** appears in the **Hierarchy** list, expand `All Products`, and then expand **Components**.</span></span>

8.  <span data-ttu-id="b3618-162">[**階層**] の一覧で [**製品カテゴリ**] を選択し、 `All Products` []、[**コンポーネント**] の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="b3618-162">Select **Product Categories** in the **Hierarchy** list, expand `All Products`, and then expand **Components**.</span></span>

     <span data-ttu-id="b3618-163">アセンブリ部品は何も表示されません。</span><span class="sxs-lookup"><span data-stu-id="b3618-163">Notice that none of the assembly components appear.</span></span>

 <span data-ttu-id="b3618-164">前のタスクで説明されている動作を変更するには、Products ディメンションの**UnknownMember**プロパティを有効にし、 **UnknownMemberName**プロパティの値を設定します。また、モデル名属性の**nullprocessing**プロパティを UnknownMember に設定し、属性を属性の関連属性として定義 `Subcategory` してから、 **Model Name** **UnknownMember** `Category` `Subcategory` **Product Line**属性を**モデル名**属性の関連属性として定義します</span><span class="sxs-lookup"><span data-stu-id="b3618-164">To modify the behavior mentioned in the previous task, you will enable the **UnknownMember** property of the Products dimension, set a value for the **UnknownMemberName** property, set the **NullProcessing** property for the `Subcategory` and **Model Name** attributes to **UnknownMember**, define the `Category` attribute as a related attribute of the `Subcategory` attribute, and then define the **Product Line** attribute as a related attribute of the **Model Name** attribute.</span></span> <span data-ttu-id="b3618-165">以上の操作により、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] では、 **SubcategoryKey** 列に値を持たないそれぞれの製品について、不明なメンバーの名前の値が使用されるようになります。次の実習でそれを確認します。</span><span class="sxs-lookup"><span data-stu-id="b3618-165">These steps will cause [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to use the unknown member name value for each product that does not have a value for the **SubcategoryKey** column, as you will see in the following task.</span></span>

## <a name="enabling-the-unknown-member-defining-attribute-relationships-and-specifying-custom-processing-properties-for-nulls"></a><span data-ttu-id="b3618-166">不明なメンバーの有効化、属性リレーションシップの定義、および NULL のカスタム処理プロパティの指定</span><span class="sxs-lookup"><span data-stu-id="b3618-166">Enabling the Unknown Member, Defining Attribute Relationships, and Specifying Custom Processing Properties for Nulls</span></span>

1.  <span data-ttu-id="b3618-167">**Product** ディメンションのディメンション デザイナーで **[ディメンション構造]** タブをクリックし、 **[属性]** ペインで **[Product]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3618-167">Click the **Dimension Structure** tab in Dimension Designer for the **Product** dimension, and then select **Product** in the **Attributes** pane.</span></span>

2.  <span data-ttu-id="b3618-168">[**プロパティ**] ウィンドウで、 **UnknownMember**プロパティを**Visible**に変更し、 **UnknownMemberName**プロパティの値をに変更し `Assembly Components` ます。</span><span class="sxs-lookup"><span data-stu-id="b3618-168">In the **Properties** window, change the **UnknownMember** property to **Visible**, and then change the value for the **UnknownMemberName** property to `Assembly Components`.</span></span>

     <span data-ttu-id="b3618-169">**UnknownMember** プロパティを **Visible** または **Hidden** に変更すると、ディメンションの **[UnknownMember]** プロパティが有効になります。</span><span class="sxs-lookup"><span data-stu-id="b3618-169">Changing the **UnknownMember** property to either **Visible** or **Hidden** enables the **UnknownMember** property for the dimension.</span></span>

3.  <span data-ttu-id="b3618-170">**[属性リレーションシップ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3618-170">Click the **Attribute Relationships** tab.</span></span>

4.  <span data-ttu-id="b3618-171">ダイアグラムで属性を右クリックし、[ `Subcategory` **新しい属性リレーションシップ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3618-171">In the diagram, right-click the `Subcategory` attribute and then select **New Attribute Relationship**.</span></span>

5.  <span data-ttu-id="b3618-172">[**属性リレーションシップの作成**] ダイアログボックスで、[基になる**属性**] を選択 `Subcategory` します。</span><span class="sxs-lookup"><span data-stu-id="b3618-172">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is `Subcategory`.</span></span> <span data-ttu-id="b3618-173">**関連属性**をに設定し `Category` ます。</span><span class="sxs-lookup"><span data-stu-id="b3618-173">Set the **Related Attribute** to `Category`.</span></span> <span data-ttu-id="b3618-174">リレーションシップの種類の設定は **[可変]** のままにします。</span><span class="sxs-lookup"><span data-stu-id="b3618-174">Leave the relationship type set to **Flexible**.</span></span>

6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

7.  <span data-ttu-id="b3618-175">**[属性]** ペインで、 **[Subcategory]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b3618-175">In the **Attributes** pane, select **Subcategory.**</span></span>

8.  <span data-ttu-id="b3618-176">[プロパティ] ウィンドウで、 **[KeyColumns]** プロパティ、 **[DimProductSubcategory.ProductSubcategoryKey (Integer)]** プロパティの順に展開します。</span><span class="sxs-lookup"><span data-stu-id="b3618-176">In the Properties window, expand the **KeyColumns** property and then expand the **DimProductSubcategory.ProductSubcategoryKey (Integer)** property.</span></span>

9. <span data-ttu-id="b3618-177">**NullProcessing** プロパティを **UnknownMember**に変更します。</span><span class="sxs-lookup"><span data-stu-id="b3618-177">Change the **NullProcessing** property to **UnknownMember**.</span></span>

10. <span data-ttu-id="b3618-178">**[属性]** ペインで、 **[Model Name]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b3618-178">In the **Attributes** pane, select **Model Name**.</span></span>

11. <span data-ttu-id="b3618-179">[プロパティ] ウィンドウで、 **[KeyColumns]** プロパティ、 **[Product.ModelName (WChar)]** プロパティの順に展開します。</span><span class="sxs-lookup"><span data-stu-id="b3618-179">In the Properties window, expand the **KeyColumns** property and then expand the **Product.ModelName (WChar)** property.</span></span>

12. <span data-ttu-id="b3618-180">**NullProcessing** プロパティを **UnknownMember**に変更します。</span><span class="sxs-lookup"><span data-stu-id="b3618-180">Change the **NullProcessing** property to **UnknownMember**.</span></span>

     <span data-ttu-id="b3618-181">これらの変更により、が [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 処理中に属性またはモデル名属性に対して null 値を検出した場合、 `Subcategory` 不明なメンバー値はキー値として置き換えられ、ユーザー定義階層が正しく構築されます。 **Model Name**</span><span class="sxs-lookup"><span data-stu-id="b3618-181">Because of these changes, when [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] encounters a null value for the `Subcategory` attribute or the **Model Name** attribute during processing, the unknown member value will be substituted as the key value, and the user-defined hierarchies will be constructed correctly.</span></span>

## <a name="browsing-the-product-dimension-again"></a><span data-ttu-id="b3618-182">Product ディメンションの再表示</span><span class="sxs-lookup"><span data-stu-id="b3618-182">Browsing the Product Dimension Again</span></span>

1.  <span data-ttu-id="b3618-183">**[ビルド]** メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3618-183">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="b3618-184">配置が正常に完了したら、 **Product** ディメンションのディメンション デザイナーで **[ブラウザー]** タブをクリックし、 **[再接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3618-184">When deployment has successfully completed, click the **Browser** tab in Dimension Designer for the **Product** dimension, and then click **Reconnect**.</span></span>

3.  <span data-ttu-id="b3618-185">[**階層**] ボックスの一覧で [**製品カテゴリ**] が選択されていることを確認し、を展開し `All Products` ます。</span><span class="sxs-lookup"><span data-stu-id="b3618-185">Verify that **Product Categories** is selected in the **Hierarchy** list, and then expand `All Products`.</span></span>

     <span data-ttu-id="b3618-186">Category レベルの新しいメンバーとして Assembly Components が表示されています。</span><span class="sxs-lookup"><span data-stu-id="b3618-186">Notice that Assembly Components appears as a new member of the Category level.</span></span>

4.  <span data-ttu-id="b3618-187">レベルのメンバーを展開し、 `Assembly Components` `Category` `Assembly Components` レベルのメンバーを展開し `Subcategory` ます。</span><span class="sxs-lookup"><span data-stu-id="b3618-187">Expand the `Assembly Components` member of the `Category` level and then expand the `Assembly Components` member of the `Subcategory` level.</span></span>

     <span data-ttu-id="b3618-188">次の図のように、 **Product Name** レベルにアセンブリ部品が表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="b3618-188">Notice that all the assembly components now appear at the **Product Name** level, as shown in the following image.</span></span>

     <span data-ttu-id="b3618-189">![アセンブリ コンポーネントを示す製品名レベル](../../2014/tutorials/media/l4-assemblycomponents-1.gif "アセンブリ コンポーネントを示す製品名レベル")</span><span class="sxs-lookup"><span data-stu-id="b3618-189">![Product Name level showing assembly components](../../2014/tutorials/media/l4-assemblycomponents-1.gif "Product Name level showing assembly components")</span></span>

## <a name="next-lesson"></a><span data-ttu-id="b3618-190">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="b3618-190">Next Lesson</span></span>
 [<span data-ttu-id="b3618-191">レッスン 5: ディメンションおよびメジャー グループ間のリレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="b3618-191">Lesson 5: Defining Relationships Between Dimensions and Measure Groups</span></span>](lesson-5-defining-relationships-between-dimensions-and-measure-groups.md)


