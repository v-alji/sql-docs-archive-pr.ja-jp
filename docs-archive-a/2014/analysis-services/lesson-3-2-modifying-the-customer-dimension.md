---
title: Customer ディメンションの変更 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5b5aed99-1760-4bc7-b248-52ecb0b97ebc
author: minewiskan
ms.author: owend
ms.openlocfilehash: bd5c5c47205a89f8429b0b6f0ba55da266d5e811
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642997"
---
# <a name="modifying-the-customer-dimension"></a><span data-ttu-id="36cfa-102">Customer ディメンションの変更</span><span class="sxs-lookup"><span data-stu-id="36cfa-102">Modifying the Customer Dimension</span></span>
  <span data-ttu-id="36cfa-103">キューブのディメンションの使いやすさと機能性を向上させる方法は数多くあります。</span><span class="sxs-lookup"><span data-stu-id="36cfa-103">There are many different ways that you can increase the usability and functionality of the dimensions in a cube.</span></span> <span data-ttu-id="36cfa-104">このトピックの実習では、Customer ディメンションを変更します。</span><span class="sxs-lookup"><span data-stu-id="36cfa-104">In the tasks in this topic, you modify the Customer dimension.</span></span>  
  
## <a name="renaming-attributes"></a><span data-ttu-id="36cfa-105">属性名の変更</span><span class="sxs-lookup"><span data-stu-id="36cfa-105">Renaming Attributes</span></span>  
 <span data-ttu-id="36cfa-106">属性名は、ディメンション デザイナーの **[ディメンション構造]** タブで変更できます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-106">You can change attribute names with the **Dimension Structure** tab of Dimension Designer.</span></span>  
  
#### <a name="to-rename-an-attribute"></a><span data-ttu-id="36cfa-107">属性名を変更するには</span><span class="sxs-lookup"><span data-stu-id="36cfa-107">To rename an attribute</span></span>  
  
1.  <span data-ttu-id="36cfa-108">**で Customer ディメンションの** ディメンション デザイナー [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-108">Switch to **Dimension Designer** for the Customer dimension in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="36cfa-109">これを行うには、ソリューション エクスプローラーの **[ディメンション]** ノードで **[Customer]** ディメンションをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-109">To do this, double-click the **Customer** dimension in the **Dimensions** node of Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="36cfa-110">**[属性]** ペインで **[English Country Region Name]** を右クリックし、 **[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-110">In the **Attributes** pane, right-click **English Country Region Name**, and then click **Rename**.</span></span> <span data-ttu-id="36cfa-111">属性の名前をに変更 `Country-Region` します。</span><span class="sxs-lookup"><span data-stu-id="36cfa-111">Change the name of the attribute to `Country-Region`.</span></span>  
  
3.  <span data-ttu-id="36cfa-112">同様に、次の属性の名前も変更します。</span><span class="sxs-lookup"><span data-stu-id="36cfa-112">Change the names of the following attributes in the same manner:</span></span>  
  
    -   <span data-ttu-id="36cfa-113">**English 教育**属性-変更`Education`</span><span class="sxs-lookup"><span data-stu-id="36cfa-113">**English Education** attribute - change to `Education`</span></span>  
  
    -   <span data-ttu-id="36cfa-114">**英語職業**属性-変更`Occupation`</span><span class="sxs-lookup"><span data-stu-id="36cfa-114">**English Occupation** attribute - change to `Occupation`</span></span>  
  
    -   <span data-ttu-id="36cfa-115">**都道府県名**属性-をに変更`State-Province`</span><span class="sxs-lookup"><span data-stu-id="36cfa-115">**State Province Name** attribute - change to `State-Province`</span></span>  
  
4.  <span data-ttu-id="36cfa-116">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-116">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="creating-a-hierarchy"></a><span data-ttu-id="36cfa-117">階層の作成</span><span class="sxs-lookup"><span data-stu-id="36cfa-117">Creating a Hierarchy</span></span>  
 <span data-ttu-id="36cfa-118">新しい階層は、属性を **[属性]** ペインから **[階層]** ペインにドラッグすることで作成できます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-118">You can create a new hierarchy by dragging an attribute from the **Attributes** pane to the **Hierarchies** pane.</span></span>  
  
#### <a name="to-create-a-hierarchy"></a><span data-ttu-id="36cfa-119">階層を作成するには</span><span class="sxs-lookup"><span data-stu-id="36cfa-119">To create a hierarchy</span></span>  
  
1.  <span data-ttu-id="36cfa-120">属性を [ `Country-Region` **属性**] ペインから [**階層**] ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-120">Drag the `Country-Region` attribute from the **Attributes** pane into the **Hierarchies** pane.</span></span>  
  
2.  <span data-ttu-id="36cfa-121">属性を `State-Province` [**属性**] ペインから、[ **\<new level>** **階層**] ペインのセル (レベルの下) にドラッグし `Country-Region` ます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-121">Drag the `State-Province` attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the `Country-Region` level.</span></span>  
  
3.  <span data-ttu-id="36cfa-122">[**属性**] ペインの [ **City** ] 属性を、[ **\<new level>** **階層**] ペインのセル (レベルの下) にドラッグし `State-Province` ます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-122">Drag the **City** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the `State-Province` level.</span></span>  
  
4.  <span data-ttu-id="36cfa-123">[**ディメンション構造**] タブの [**階層**] ペインで、[ **hierarchy** ] 階層のタイトルバーを右クリックし、[**名前の変更**] をクリックして「」と入力し `Customer Geography` ます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-123">In the **Hierarchies** pane of the **Dimension Structure** tab, right-click the title bar of the **Hierarchy** hierarchy, select **Rename**, and then type `Customer Geography`.</span></span>  
  
     <span data-ttu-id="36cfa-124">階層の名前はになりました `Customer Geography` 。</span><span class="sxs-lookup"><span data-stu-id="36cfa-124">The name of the hierarchy is now `Customer Geography`.</span></span>  
  
5.  <span data-ttu-id="36cfa-125">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-125">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="adding-a-named-calculation"></a><span data-ttu-id="36cfa-126">名前付き計算の追加</span><span class="sxs-lookup"><span data-stu-id="36cfa-126">Adding a Named Calculation</span></span>  
 <span data-ttu-id="36cfa-127">名前付き計算 (計算列として表される SQL 式) をデータ ソース ビューに追加できます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-127">You can add a named calculation, which is a SQL expression that is represented as a calculated column, to a table in a data source view.</span></span> <span data-ttu-id="36cfa-128">この式は、テーブルの列として表示され、動作します。</span><span class="sxs-lookup"><span data-stu-id="36cfa-128">The expression appears and behaves as a column in the table.</span></span> <span data-ttu-id="36cfa-129">名前付き計算により、基になるデータ ソースのテーブルを変更せずに、データ ソース ビューの既存のテーブルのリレーショナル スキーマを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-129">Named calculations let you extend the relational schema of existing tables in a data source view without modifying the table in the underlying data source.</span></span> <span data-ttu-id="36cfa-130">詳細については、「 [データ ソース ビューでの名前付き計算の定義 (Analysis Services)](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)</span><span class="sxs-lookup"><span data-stu-id="36cfa-130">For more information, see [Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)</span></span>  
  
#### <a name="to-add-a-named-calculation"></a><span data-ttu-id="36cfa-131">名前付き計算を追加するには</span><span class="sxs-lookup"><span data-stu-id="36cfa-131">To add a named calculation</span></span>  
  
1.  <span data-ttu-id="36cfa-132">ソリューションエクスプローラーの [**データソースビュー** ] フォルダーで、 \*\* [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012\*\*データソースビューをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-132">Open the **[!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012** data source view by double-clicking it in the **Data Source Views** folder in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="36cfa-133">左側の **[テーブル]** ペインで **Customer**を右クリックし、 **[新しい名前付き計算]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-133">In the **Tables** pane on the left, right-click **Customer**, and then click **New Named Calculation**.</span></span>  
  
3.  <span data-ttu-id="36cfa-134">[**名前付き計算の作成**] ダイアログボックスで、[ `FullName` **列名**] ボックスに「」と入力します。次に、[ `CASE` **式**] ボックスに次のステートメントを入力するか、またはコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-134">In the **Create Named Calculation** dialog box, type `FullName` in the **Column name** box, and then type or copy and paste the following `CASE` statement in the **Expression** box:</span></span>  
  
    ```  
    CASE  
       WHEN MiddleName IS NULL THEN  
       FirstName + ' ' + LastName  
       ELSE  
       FirstName + ' ' + MiddleName + ' ' + LastName  
    END  
    ```  
  
     <span data-ttu-id="36cfa-135">ステートメントは、 `CASE` **FirstName**列、 **MiddleName**列、および**LastName**列を連結して、customer ディメンションで customer 属性の表示名として使用**Customer**する1つの列にします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-135">The `CASE` statement concatenates the **FirstName**, **MiddleName**, and **LastName** columns into a single column that you will use in the Customer dimension as the displayed name for the **Customer** attribute.</span></span>  
  
4.  <span data-ttu-id="36cfa-136">**[OK]** をクリックします。次に、 **[テーブル]** ペインで **Customer** を展開します。</span><span class="sxs-lookup"><span data-stu-id="36cfa-136">Click **OK**, and then expand **Customer** in the **Tables** pane.</span></span>  
  
     <span data-ttu-id="36cfa-137">`FullName`名前付き計算が Customer テーブルの列の一覧に表示され、名前付き計算であることを示すアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-137">The `FullName` named calculation appears in the list of columns in the Customer table, with an icon that indicates that it is a named calculation.</span></span>  
  
5.  <span data-ttu-id="36cfa-138">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-138">On the **File** menu, click **Save All**.</span></span>  
  
6.  <span data-ttu-id="36cfa-139">**[テーブル]** ペインで **[Customer]** を右クリックし、 **[データの探索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-139">In the **Tables** pane, right-click **Customer**, and then click **Explore Data**.</span></span>  
  
7.  <span data-ttu-id="36cfa-140">**[Customer テーブルの探索]** ビューで、最後の列を確認します。</span><span class="sxs-lookup"><span data-stu-id="36cfa-140">Review the last column in the **Explore Customer Table** view.</span></span>  
  
     <span data-ttu-id="36cfa-141">`FullName`データソースビューに列が表示され、元のデータソースを変更せずに、基になるデータソースの複数の列のデータが正しく連結されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="36cfa-141">Notice that the `FullName` column appears in the data source view, correctly concatenating data from several columns from the underlying data source and without modifying the original data source.</span></span>  
  
8.  <span data-ttu-id="36cfa-142">**[Customer テーブルの探索]** タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-142">Close the **Explore Customer Table** tab.</span></span>  
  
## <a name="using-the-named-calculation-for-member-names"></a><span data-ttu-id="36cfa-143">メンバー名に対応する名前付き計算の使用</span><span class="sxs-lookup"><span data-stu-id="36cfa-143">Using the Named Calculation for Member Names</span></span>  
 <span data-ttu-id="36cfa-144">データ ソース ビューで名前付き計算を作成したら、その名前付き計算を属性のプロパティとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-144">After you have created a named calculation in the data source view, you can use the named calculation as a property of an attribute.</span></span>  
  
#### <a name="to-use-the-named-calculation-for-member-names"></a><span data-ttu-id="36cfa-145">メンバー名に対応する名前付き計算を使用するには</span><span class="sxs-lookup"><span data-stu-id="36cfa-145">To use the named calculation for member names</span></span>  
  
1.  <span data-ttu-id="36cfa-146">Customer ディメンションのディメンション デザイナーに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-146">Switch to Dimension Designer for the Customer dimension.</span></span>  
  
2.  <span data-ttu-id="36cfa-147">**[ディメンション構造]** タブの **[属性]** ペインで、 **[Customer Key]** 属性をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-147">In the **Attributes** pane of the **Dimension Structure** tab, click the **Customer Key** attribute.</span></span>  
  
3.  <span data-ttu-id="36cfa-148">[プロパティ] ウィンドウを開いて、タイトル バーにある **[自動的に隠す]** ボタンをクリックします。これにより、[プロパティ] ウィンドウが開いたままになります。</span><span class="sxs-lookup"><span data-stu-id="36cfa-148">Open the Properties window and click the **Auto Hide** button on the title bar so that it stays open.</span></span>  
  
4.  <span data-ttu-id="36cfa-149">[**名前**] プロパティフィールドに「」と入力 `Full Name` します。</span><span class="sxs-lookup"><span data-stu-id="36cfa-149">In the **Name** property field, type `Full Name`.</span></span>  
  
5.  <span data-ttu-id="36cfa-150">下部にある [ **NameColumn** ] プロパティフィールドをクリックし、参照ボタン ([.**..**]) をクリックして、[**名前列**] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-150">Click in the **NameColumn** property field at the bottom, and then click the browse (**...**) button to open the **Name Column** dialog box.</span></span>  
  
6.  <span data-ttu-id="36cfa-151">[ `FullName` 基になる**列**] ボックスの一覧の下部にあるを選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-151">Select `FullName` at the bottom of the **Source column** list, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="36cfa-152">[ディメンション構造] タブで、[ `Full Name` **属性**] ペインの属性を [ **\<new level>** **階層**] ペインのセル ([ **City** ] レベルの下) にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-152">In the Dimensions Structure tab, drag the `Full Name` attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **City** level.</span></span>  
  
8.  <span data-ttu-id="36cfa-153">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-153">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-display-folders"></a><span data-ttu-id="36cfa-154">表示フォルダーの定義</span><span class="sxs-lookup"><span data-stu-id="36cfa-154">Defining Display Folders</span></span>  
 <span data-ttu-id="36cfa-155">表示フォルダーを使用してユーザー階層と属性階層をフォルダー構造内にグループ化することで、使いやすさを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-155">You can use display folders to group user and attribute hierarchies into folder structures to increase usability.</span></span>  
  
#### <a name="to-define-display-folders"></a><span data-ttu-id="36cfa-156">表示フォルダーを定義するには</span><span class="sxs-lookup"><span data-stu-id="36cfa-156">To define display folders</span></span>  
  
1.  <span data-ttu-id="36cfa-157">Customer ディメンションの **[ディメンション構造]** タブを開きます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-157">Open the **Dimension Structure** tab for the Customer dimension.</span></span>  
  
2.  <span data-ttu-id="36cfa-158">**[属性]** ペインで、Ctrl キーを押しながら次の各属性をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="36cfa-158">In the **Attributes** pane, select the following attributes by holding down the CTRL key while clicking each of them:</span></span>  
  
    -   <span data-ttu-id="36cfa-159">**City (市)**</span><span class="sxs-lookup"><span data-stu-id="36cfa-159">**City**</span></span>  
  
    -   `Country-Region`  
  
    -   <span data-ttu-id="36cfa-160">**Postal Code**</span><span class="sxs-lookup"><span data-stu-id="36cfa-160">**Postal Code**</span></span>  
  
    -   `State-Province`  
  
3.  <span data-ttu-id="36cfa-161">プロパティウィンドウで、上部にある [ **attributehierarchydisplayfolder]** ] プロパティフィールドをクリックし (完全な名前を表示するためにポイントする必要がある場合があります)、「」と入力し `Location` ます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-161">In the Properties window, click the **AttributeHierarchyDisplayFolder** property field at the top (you might need to point to it to see the full name), and then type `Location`.</span></span>  
  
4.  <span data-ttu-id="36cfa-162">[**階層**] ペインで、[] をクリックし、 `Customer Geography` 右側のプロパティウィンドウで `Location` **displayfolder**プロパティの値としてを選択します。</span><span class="sxs-lookup"><span data-stu-id="36cfa-162">In the **Hierarchies** pane, click `Customer Geography`, and then in the Properties window on the right, select `Location` as the value of the **DisplayFolder** property.</span></span>  
  
5.  <span data-ttu-id="36cfa-163">**[属性]** ペインで、Ctrl キーを押しながら次の各属性をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="36cfa-163">In the **Attributes** pane, select the following attributes by holding down the CTRL key while clicking each of them:</span></span>  
  
    -   <span data-ttu-id="36cfa-164">**Commute Distance**</span><span class="sxs-lookup"><span data-stu-id="36cfa-164">**Commute Distance**</span></span>  
  
    -   `Education`  
  
    -   <span data-ttu-id="36cfa-165">**性別**</span><span class="sxs-lookup"><span data-stu-id="36cfa-165">**Gender**</span></span>  
  
    -   <span data-ttu-id="36cfa-166">**House Owner Flag**</span><span class="sxs-lookup"><span data-stu-id="36cfa-166">**House Owner Flag**</span></span>  
  
    -   <span data-ttu-id="36cfa-167">**Marital Status**</span><span class="sxs-lookup"><span data-stu-id="36cfa-167">**Marital Status**</span></span>  
  
    -   <span data-ttu-id="36cfa-168">**Number Cars Owned**</span><span class="sxs-lookup"><span data-stu-id="36cfa-168">**Number Cars Owned**</span></span>  
  
    -   <span data-ttu-id="36cfa-169">**子供の子供の数**</span><span class="sxs-lookup"><span data-stu-id="36cfa-169">**Number Children At Home**</span></span>  
  
    -   `Occupation`  
  
    -   <span data-ttu-id="36cfa-170">**Total Children**</span><span class="sxs-lookup"><span data-stu-id="36cfa-170">**Total Children**</span></span>  
  
    -   <span data-ttu-id="36cfa-171">**Yearly Income**</span><span class="sxs-lookup"><span data-stu-id="36cfa-171">**Yearly Income**</span></span>  
  
6.  <span data-ttu-id="36cfa-172">プロパティウィンドウで、上部にある [ **attributehierarchydisplayfolder]** ] プロパティフィールドをクリックし、「」と入力し `Demographic` ます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-172">In the Properties window, click the **AttributeHierarchyDisplayFolder** property field at the top, and then type `Demographic`.</span></span>  
  
7.  <span data-ttu-id="36cfa-173">**[属性]** ペインで、Ctrl キーを押しながら次の各属性をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="36cfa-173">In the **Attributes** pane, select the following attributes by holding down the CTRL key while clicking each of them:</span></span>  
  
    -   <span data-ttu-id="36cfa-174">**メール アドレス**</span><span class="sxs-lookup"><span data-stu-id="36cfa-174">**Email Address**</span></span>  
  
    -   <span data-ttu-id="36cfa-175">**Phone**</span><span class="sxs-lookup"><span data-stu-id="36cfa-175">**Phone**</span></span>  
  
8.  <span data-ttu-id="36cfa-176">プロパティウィンドウで、[ **attributehierarchydisplayfolder]** ] プロパティフィールドをクリックし、「」と入力し `Contacts` ます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-176">In the Properties window, click the **AttributeHierarchyDisplayFolder** property field and type `Contacts`.</span></span>  
  
9. <span data-ttu-id="36cfa-177">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-177">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-composite-keycolumns"></a><span data-ttu-id="36cfa-178">複合 KeyColumns の定義</span><span class="sxs-lookup"><span data-stu-id="36cfa-178">Defining Composite KeyColumns</span></span>  
 <span data-ttu-id="36cfa-179">**KeyColumns** プロパティは、属性のキーを表す 1 つ以上の列を示します。</span><span class="sxs-lookup"><span data-stu-id="36cfa-179">The **KeyColumns** property contains the column or columns that represent the key for the attribute.</span></span> <span data-ttu-id="36cfa-180">このレッスンでは、**市区町村**と属性の複合キーを作成し `State-Province` ます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-180">In this lesson, you create a composite key for the **City** and `State-Province` attributes.</span></span> <span data-ttu-id="36cfa-181">複合キーは、属性を一意に識別する必要がある場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-181">Composite keys can be helpful when you need to uniquely identify an attribute.</span></span> <span data-ttu-id="36cfa-182">たとえば、このチュートリアルの後半で属性リレーションシップを定義する場合は、 **City**属性で属性を一意に識別する必要があり `State-Province` ます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-182">For example, when you define attribute relationships later in this tutorial, a **City** attribute must uniquely identify a `State-Province` attribute.</span></span> <span data-ttu-id="36cfa-183">ただし、異なる州に同じ名前の都市が存在する可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="36cfa-183">However, there could be several cities with the same name in different states.</span></span> <span data-ttu-id="36cfa-184">そのため、 **City** 属性に対しては **StateProvinceName** 列と **City** 列で構成される複合キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="36cfa-184">For this reason, you will create a composite key that is composed of the **StateProvinceName** and **City** columns for the **City** attribute.</span></span> <span data-ttu-id="36cfa-185">詳細については、「 [属性の KeyColumn プロパティの変更](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36cfa-185">For more information, see [Modify the KeyColumn Property of an Attribute](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md).</span></span>  
  
#### <a name="to-define-composite-keycolumns-for-the-city-attribute"></a><span data-ttu-id="36cfa-186">City 属性の複合 KeyColumns を定義するには</span><span class="sxs-lookup"><span data-stu-id="36cfa-186">To define composite KeyColumns for the City attribute</span></span>  
  
1.  <span data-ttu-id="36cfa-187">Customer ディメンションの **[ディメンション構造]** タブを開きます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-187">Open the **Dimension Structure** tab for the Customer dimension.</span></span>  
  
2.  <span data-ttu-id="36cfa-188">**[属性]** ペインで、 **[City]** 属性をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-188">In the **Attributes** pane, click the **City** attribute.</span></span>  
  
3.  <span data-ttu-id="36cfa-189">**[プロパティ]** ウィンドウで、下部付近の **[KeyColumns]** フィールドをクリックし、参照ボタン (**[...]**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-189">In the **Properties** window, click in the **KeyColumns** field near the bottom, and then click the browse (**...**) button.</span></span>  
  
4.  <span data-ttu-id="36cfa-190">**[キー列]** ダイアログ ボックスの **[使用できる列]** ボックスの一覧で **[StateProvinceName]** 列を選択し、**[>]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-190">In the **Key Columns** dialog box, in the **Available Columns** list, select the column **StateProvinceName**, and then click the **>** button.</span></span>  
  
     <span data-ttu-id="36cfa-191">**[City]** 列と **[StateProvinceName]** 列が **[キー列]** ボックスの一覧に表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="36cfa-191">The **City** and **StateProvinceName** columns are now displayed in the **Key Columns** list.</span></span>  
  
5.  <span data-ttu-id="36cfa-192">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-192">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="36cfa-193">**City** 属性の **NameColumn** プロパティを設定するには、[プロパティ] ウィンドウで **[NameColumn]** フィールドをクリックし、参照ボタン (**[...]**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-193">To set the **NameColumn** property of the **City** attribute, click the **NameColumn** field in the Properties window, and then click the browse (**...**) button.</span></span>  
  
7.  <span data-ttu-id="36cfa-194">**[名前列]** ダイアログ ボックスの **[基になる列]** ボックスの一覧で **[City]** を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-194">In the **Name Column** dialog box, in the **Source column** list, select **City**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="36cfa-195">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-195">On the **File** menu, click **Save All**.</span></span>  
  
#### <a name="to-define-composite-keycolumns-for-the-state-province-attribute"></a><span data-ttu-id="36cfa-196">State-Province 属性の複合 KeyColumns を定義するには</span><span class="sxs-lookup"><span data-stu-id="36cfa-196">To define composite KeyColumns for the State-Province attribute</span></span>  
  
1.  <span data-ttu-id="36cfa-197">Customer ディメンションの **[ディメンション構造]** タブが開いていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="36cfa-197">Make sure the **Dimension Structure** tab for the Customer dimension is open.</span></span>  
  
2.  <span data-ttu-id="36cfa-198">[**属性**] ペインで、属性をクリックし `State-Province` ます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-198">In the **Attributes** pane, click the `State-Province` attribute.</span></span>  
  
3.  <span data-ttu-id="36cfa-199">**[プロパティ]** ウィンドウで **[KeyColumns]** フィールドをクリックし、参照ボタン (**[...]**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-199">In the **Properties** window, click in the **KeyColumns** field, and then click the browse (**...**) button.</span></span>  
  
4.  <span data-ttu-id="36cfa-200">**[キー列]** ダイアログ ボックスの **[使用できる列]** ボックスの一覧で **[EnglishCountryRegionName]** 列を選択し、**[>]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-200">In the **Key Columns** dialog box, in the **Available Columns** list, select the column **EnglishCountryRegionName**, and then click the **>** button.</span></span>  
  
     <span data-ttu-id="36cfa-201">**[EnglishCountryRegionName]** 列と **[StateProvinceName]** 列が **[キー列]** ボックスの一覧に表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="36cfa-201">The **EnglishCountryRegionName** and **StateProvinceName** columns are now displayed in the **Key Columns** list.</span></span>  
  
5.  <span data-ttu-id="36cfa-202">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-202">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="36cfa-203">属性の**NameColumn**プロパティを設定するには、 `State-Province` プロパティウィンドウの [ **NameColumn** ] フィールドをクリックし、参照ボタン ([.**..**]) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-203">To set the **NameColumn** property of the `State-Province` attribute, click the **NameColumn** field in the Properties window, and then click the browse (**...**) button.</span></span>  
  
7.  <span data-ttu-id="36cfa-204">**[名前列]** ダイアログ ボックスの **[基になる列]** ボックスの一覧で **[StateProvinceName]** を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-204">In the **Name Column** dialog box, in the **Source column** list, select **StateProvinceName**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="36cfa-205">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-205">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-attribute-relationships"></a><span data-ttu-id="36cfa-206">属性リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="36cfa-206">Defining Attribute Relationships</span></span>  
 <span data-ttu-id="36cfa-207">基になるデータで属性リレーションシップがサポートされる場合、属性間の属性リレーションシップを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36cfa-207">If the underlying data supports it, you should define attribute relationships between attributes.</span></span> <span data-ttu-id="36cfa-208">属性リレーションシップを定義すると、ディメンション、パーティション、およびクエリの処理速度が上がります。</span><span class="sxs-lookup"><span data-stu-id="36cfa-208">Defining attribute relationships speeds up dimension, partition, and query processing.</span></span> <span data-ttu-id="36cfa-209">詳細については、「 [属性リレーションシップの定義](multidimensional-models/attribute-relationships-define.md) 」および「 [属性リレーションシップ](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36cfa-209">For more information, see [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md) and [Attribute Relationships](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).</span></span>  
  
#### <a name="to-define-attribute-relationships"></a><span data-ttu-id="36cfa-210">属性リレーションシップを定義するには</span><span class="sxs-lookup"><span data-stu-id="36cfa-210">To define attribute relationships</span></span>  
  
1.  <span data-ttu-id="36cfa-211">Customer ディメンションの**ディメンションデザイナー**で、[**属性リレーションシップ**] タブをクリックします。場合によっては、しばらく待つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="36cfa-211">In the **Dimension Designer** for the Customer dimension, click the **Attribute Relationships** tab. You might need to wait.</span></span>  
  
2.  <span data-ttu-id="36cfa-212">ダイアグラムで、 **[City]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-212">In the diagram, right-click the **City** attribute, and then click **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="36cfa-213">**[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[City]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="36cfa-213">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **City**.</span></span> <span data-ttu-id="36cfa-214">**関連属性**をに設定し `State-Province` ます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-214">Set the **Related Attribute** to `State-Province`.</span></span>  
  
4.  <span data-ttu-id="36cfa-215">**[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類を **[固定]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="36cfa-215">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
     <span data-ttu-id="36cfa-216">リレーションシップの種類を **[固定]** に設定するのは、時間が経過してもメンバー間のリレーションシップが変化しないためです。</span><span class="sxs-lookup"><span data-stu-id="36cfa-216">The relationship type is **Rigid** because relationships between the members will not change over time.</span></span> <span data-ttu-id="36cfa-217">たとえば、ある都市が別の都道府県の一部となることは通常ありません。</span><span class="sxs-lookup"><span data-stu-id="36cfa-217">For example, it would be unusual for a city to become part of a different state or province.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="36cfa-218">ダイアグラムで属性を右クリックし、[ `State-Province` **新しい属性リレーションシップ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-218">In the diagram, right-click the `State-Province` attribute and then select **New Attribute Relationship**.</span></span>  
  
7.  <span data-ttu-id="36cfa-219">[**属性リレーションシップの作成**] ダイアログボックスで、[基になる**属性**] を選択 `State-Province` します。</span><span class="sxs-lookup"><span data-stu-id="36cfa-219">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is `State-Province`.</span></span> <span data-ttu-id="36cfa-220">**関連属性**をに設定し `Country-Region` ます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-220">Set the **Related Attribute** to `Country-Region`.</span></span>  
  
8.  <span data-ttu-id="36cfa-221">**[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類を **[固定]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="36cfa-221">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
9. <span data-ttu-id="36cfa-222">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-222">Click **OK**.</span></span>  
  
10. <span data-ttu-id="36cfa-223">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-223">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="deploying-changes-processing-the-objects-and-viewing-the-changes"></a><span data-ttu-id="36cfa-224">オブジェクトの配置、変更、処理、および変更内容の表示</span><span class="sxs-lookup"><span data-stu-id="36cfa-224">Deploying Changes, Processing the Objects, and Viewing the Changes</span></span>  
 <span data-ttu-id="36cfa-225">属性と階層を変更したら、変更を表示する前に変更を配置し、関連するオブジェクトを再処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36cfa-225">After you have changed attributes and hierarchies, you must deploy the changes and reprocess the related objects before you can view the changes.</span></span>  
  
#### <a name="to-deploy-the-changes-process-the-objects-and-view-the-changes"></a><span data-ttu-id="36cfa-226">変更の配置、オブジェクトの処理、および変更の表示を行うには</span><span class="sxs-lookup"><span data-stu-id="36cfa-226">To deploy the changes, process the objects, and view the changes</span></span>  
  
1.  <span data-ttu-id="36cfa-227">**で、** [ビルド] [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-227">On the **Build** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="36cfa-228">" **配置が正常に完了しました** " というメッセージが表示されたら、Customer ディメンションのディメンション デザイナーの **[ブラウザー]** タブをクリックし、ディメンション デザイナーのツール バーの左側にある [再接続] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-228">After you receive the **Deployment Completed Successfully** message, click the **Browser** tab of Dimension Designer for the Customer dimension, and then click the Reconnect button on the left side of the toolbar of the designer.</span></span>  
  
3.  <span data-ttu-id="36cfa-229">[ `Customer Geography` **階層**] ボックスの一覧でが選択されていることを確認し、[ブラウザー] ウィンドウで [**すべて**]、[**オーストラリア**]、[ **New 南部ウェールズ**]、[ **coffs harbour ハーバー**] の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="36cfa-229">Verify that `Customer Geography` is selected in the **Hierarchy** list, and then in the browser pane, expand **All**, expand **Australia**, expand **New South Wales**, and then expand **Coffs Harbour**.</span></span>  
  
     <span data-ttu-id="36cfa-230">この都市の顧客がブラウザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-230">The browser displays the customers in the city.</span></span>  
  
4.  <span data-ttu-id="36cfa-231">**Tutorial キューブの** キューブ デザイナー [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-231">Switch to **Cube Designer** for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span> <span data-ttu-id="36cfa-232">これを行うには、**ソリューションエクスプローラー**の [**キューブ**] ノードで**Analysis Services チュートリアル**キューブをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-232">To do this, double-click the **Analysis Services Tutorial** cube in the **Cubes** node of **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="36cfa-233">**[ブラウザー]** タブをクリックし、キューブ デザイナーのツール バーにある [再接続] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-233">Click the **Browser** tab, and then click the Reconnect button on the toolbar of the designer.</span></span>  
  
6.  <span data-ttu-id="36cfa-234">**[メジャー グループ]** ペインで **[Customer]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="36cfa-234">In the **Measure Group** pane, expand **Customer**.</span></span>  
  
     <span data-ttu-id="36cfa-235">[Customer] の下には、属性が展開されて表示される代わりに、表示フォルダーが表示されています。表示フォルダー値が割り当てられていない属性はそのまま表示されます。</span><span class="sxs-lookup"><span data-stu-id="36cfa-235">Notice that instead of a long list of attributes, only the display folders and the attributes that do not have display folder values appear underneath Customer.</span></span>  
  
7.  <span data-ttu-id="36cfa-236">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cfa-236">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="36cfa-237">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="36cfa-237">Next Task in Lesson</span></span>  
 [<span data-ttu-id="36cfa-238">Product ディメンションの変更</span><span class="sxs-lookup"><span data-stu-id="36cfa-238">Modifying the Product Dimension</span></span>](lesson-3-3-modifying-the-product-dimension.md)  
  
## <a name="see-also"></a><span data-ttu-id="36cfa-239">参照</span><span class="sxs-lookup"><span data-stu-id="36cfa-239">See Also</span></span>  
 <span data-ttu-id="36cfa-240">[ディメンションの属性のプロパティのリファレンス](multidimensional-models/dimension-attribute-properties-reference.md) </span><span class="sxs-lookup"><span data-stu-id="36cfa-240">[Dimension Attribute Properties Reference](multidimensional-models/dimension-attribute-properties-reference.md) </span></span>  
 <span data-ttu-id="36cfa-241">[ディメンションからの属性の削除](multidimensional-models/attribute-properties-remove-an-attribute-from-a-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="36cfa-241">[Remove an Attribute from a Dimension](multidimensional-models/attribute-properties-remove-an-attribute-from-a-dimension.md) </span></span>  
 <span data-ttu-id="36cfa-242">[属性名の変更](multidimensional-models/attribute-properties-rename-an-attribute.md) </span><span class="sxs-lookup"><span data-stu-id="36cfa-242">[Rename an Attribute](multidimensional-models/attribute-properties-rename-an-attribute.md) </span></span>  
 [<span data-ttu-id="36cfa-243">データ ソース ビューでの名前付き計算の定義 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="36cfa-243">Define Named Calculations in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
  
