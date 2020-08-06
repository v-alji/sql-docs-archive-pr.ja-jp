---
title: Date ディメンションの変更 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4689d780-4bf6-4cf8-8fde-eb3f15dd668a
author: minewiskan
ms.author: owend
ms.openlocfilehash: b4978e9fe3acd93ddfdca707d2c2353bf171ba12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642398"
---
# <a name="modifying-the-date-dimension"></a><span data-ttu-id="a11d8-102">Date ディメンションの変更</span><span class="sxs-lookup"><span data-stu-id="a11d8-102">Modifying the Date Dimension</span></span>
  <span data-ttu-id="a11d8-103">このトピックの実習では、ユーザー定義階層を作成し、Date、Month、Calendar Quarter、および Calendar Semester 属性に表示されるメンバー名を変更します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-103">In the tasks in this topic, you create a user-defined hierarchy and change the member names that are displayed for the Date, Month, Calendar Quarter, and Calendar Semester attributes.</span></span> <span data-ttu-id="a11d8-104">また、属性の複合キーの定義、ディメンション メンバーの並べ替え順序の制御、および属性リレーションシップの定義も行います。</span><span class="sxs-lookup"><span data-stu-id="a11d8-104">You also define composite keys for attributes, control the sort order of dimension members, and define attribute relationships.</span></span>  
  
## <a name="adding-a-named-calculation"></a><span data-ttu-id="a11d8-105">名前付き計算の追加</span><span class="sxs-lookup"><span data-stu-id="a11d8-105">Adding a Named Calculation</span></span>  
 <span data-ttu-id="a11d8-106">名前付き計算 (計算列として表される SQL 式) をデータ ソース ビューに追加できます。</span><span class="sxs-lookup"><span data-stu-id="a11d8-106">You can add a named calculation, which is a SQL expression that is represented as a calculated column, to a table in a data source view.</span></span> <span data-ttu-id="a11d8-107">この式は、テーブルの列として表示され、動作します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-107">The expression appears and behaves as a column in the table.</span></span> <span data-ttu-id="a11d8-108">名前付き計算を使用すると、基になるデータ ソースのテーブルを変更せずに、データ ソース ビュー内の既存のテーブルのリレーショナル スキーマを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="a11d8-108">Named calculations enable you to extend the relational schema of existing tables in a data source view without modifying the table in the underlying data source.</span></span> <span data-ttu-id="a11d8-109">詳細については、「 [データ ソース ビューでの名前付き計算の定義 (Analysis Services)](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)</span><span class="sxs-lookup"><span data-stu-id="a11d8-109">For more information, see [Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)</span></span>  
  
#### <a name="to-add-a-named-calculation"></a><span data-ttu-id="a11d8-110">名前付き計算を追加するには</span><span class="sxs-lookup"><span data-stu-id="a11d8-110">To add a named calculation</span></span>  
  
1.  <span data-ttu-id="a11d8-111">**Adventure Works DW 2012** データ ソース ビューを開くには、ソリューション エクスプローラーの **[データ ソース ビュー]** フォルダーでこのデータ ソース ビューをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-111">To open the **Adventure Works DW 2012** data source view, double-click it in the **Data Source Views** folder in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="a11d8-112">[**テーブル**] ペインの下部にある [] を右クリックし、 `Date` [**新しい名前付き計算**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-112">Near the bottom of the **Tables** pane, right-click `Date`, and then click **New Named Calculation**.</span></span>  
  
3.  <span data-ttu-id="a11d8-113">[**名前付き計算の作成**] ダイアログボックスで、[ `SimpleDate` **列名**] ボックスに「」と入力します。次に、[ `DATENAME` **式**] ボックスに次のステートメントを入力するか、またはコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="a11d8-113">In the **Create Named Calculation** dialog box, type `SimpleDate` in the **Column name** box, and then type or copy and paste the following `DATENAME` statement in the **Expression** box:</span></span>  
  
    ```  
    DATENAME(mm, FullDateAlternateKey) + ' ' +  
    DATENAME(dd, FullDateAlternateKey) + ', ' +  
    DATENAME(yy, FullDateAlternateKey)  
    ```  
  
     <span data-ttu-id="a11d8-114">この `DATENAME` ステートメントは、FullDateAlternateKey 列から年、月、および日付の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-114">The `DATENAME` statement extracts the year, month, and day values from the FullDateAlternateKey column.</span></span> <span data-ttu-id="a11d8-115">この新しい列を、FullDateAlternateKey 属性の表示名として使用します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-115">You will use this new column as the displayed name for the FullDateAlternateKey attribute.</span></span>  
  
4.  <span data-ttu-id="a11d8-116">[ **OK**] をクリックし、[ `Date` **テーブル**] ペインでを展開します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-116">Click **OK**, and then expand `Date` in the **Tables** pane.</span></span>  
  
     <span data-ttu-id="a11d8-117">`SimpleDate`名前付き計算が Date テーブルの列の一覧に表示され、名前付き計算であることを示すアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a11d8-117">The `SimpleDate` named calculation appears in the list of columns in the Date table, with an icon that indicates that it is a named calculation.</span></span>  
  
5.  <span data-ttu-id="a11d8-118">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-118">On the **File** menu, click **Save All**.</span></span>  
  
6.  <span data-ttu-id="a11d8-119">[**テーブル**] ペインで、[] を右クリック `Date` し、[データの**探索**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-119">In the **Tables** pane, right-click `Date`, and then click **Explore Data**.</span></span>  
  
7.  <span data-ttu-id="a11d8-120">**[Date テーブルの探索]** ビューで、右にスクロールして最後の列を確認します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-120">Scroll to the right to review the last column in the **Explore Date Table** view.</span></span>  
  
     <span data-ttu-id="a11d8-121">`SimpleDate`データソースビューに列が表示され、元のデータソースを変更せずに、基になるデータソースの複数の列のデータが正しく連結されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a11d8-121">Notice that the `SimpleDate` column appears in the data source view, correctly concatenating data from several columns from the underlying data source, without modifying the original data source.</span></span>  
  
8.  <span data-ttu-id="a11d8-122">**[Date テーブルの探索]** ビューを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a11d8-122">Close the **Explore Date Table** view.</span></span>  
  
## <a name="using-the-named-calculation-for-member-names"></a><span data-ttu-id="a11d8-123">メンバー名に対応する名前付き計算の使用</span><span class="sxs-lookup"><span data-stu-id="a11d8-123">Using the Named Calculation for Member Names</span></span>  
 <span data-ttu-id="a11d8-124">データ ソース ビューで名前付き計算を作成したら、その名前付き計算を属性のプロパティとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="a11d8-124">After you create a named calculation in the data source view, you can use the named calculation as a property of an attribute.</span></span>  
  
#### <a name="to-use-the-named-calculation-for-member-names"></a><span data-ttu-id="a11d8-125">メンバー名に対応する名前付き計算を使用するには</span><span class="sxs-lookup"><span data-stu-id="a11d8-125">To use the named calculation for member names</span></span>  
  
1.  <span data-ttu-id="a11d8-126">**で Date ディメンションの** ディメンション デザイナー [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="a11d8-126">Open **Dimension Designer** for the Date dimension in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="a11d8-127">これを行うには、 `Date` **ソリューションエクスプローラー**の [**ディメンション**] ノードでディメンションをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-127">To do this, double-click the `Date` dimension in the **Dimensions** node of **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="a11d8-128">**[ディメンション構造]** タブの **[属性]** ペインで、 **[Date Key]** 属性をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-128">In the **Attributes** pane of the **Dimension Structure** tab, click the **Date Key** attribute.</span></span>  
  
3.  <span data-ttu-id="a11d8-129">[プロパティ] ウィンドウが開いていない場合は、[プロパティ] ウィンドウを開き、タイトル バーにある **[自動的に隠す]** ボタンをクリックします。これにより、[プロパティ] ウィンドウが開いたままになります。</span><span class="sxs-lookup"><span data-stu-id="a11d8-129">If the Properties window is not open, open the Properties window, and then click the **Auto Hide** button on the title bar so that it stays open.</span></span>  
  
4.  <span data-ttu-id="a11d8-130">ウィンドウの下部付近にある**NameColumn**プロパティフィールドをクリックし、参照ボタン ([.**..**]) をクリックして、[**名前列**] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="a11d8-130">Click the **NameColumn** property field near the bottom of the window, and then click the ellipsis browse (**...**) button to open the **Name Column** dialog box.</span></span>  
  
5.  <span data-ttu-id="a11d8-131">[ `SimpleDate` 基になる**列**] ボックスの一覧の下部にあるを選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-131">Select `SimpleDate` at the bottom of the **Source column** list, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="a11d8-132">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-132">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="creating-a-hierarchy"></a><span data-ttu-id="a11d8-133">階層の作成</span><span class="sxs-lookup"><span data-stu-id="a11d8-133">Creating a Hierarchy</span></span>  
 <span data-ttu-id="a11d8-134">新しい階層は、属性を **[属性]** ペインから **[階層]** ペインにドラッグすることで作成できます。</span><span class="sxs-lookup"><span data-stu-id="a11d8-134">You can create a new hierarchy by dragging an attribute from the **Attributes** pane to the **Hierarchies** pane.</span></span>  
  
#### <a name="to-create-a-hierarchy"></a><span data-ttu-id="a11d8-135">階層を作成するには</span><span class="sxs-lookup"><span data-stu-id="a11d8-135">To create a hierarchy</span></span>  
  
1.  <span data-ttu-id="a11d8-136">ディメンションのディメンションデザイナーの [**ディメンション構造**] タブで、[ `Date` **属性**] ペインの [ **Calendar Year** ] 属性を [**階層**] ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-136">In **Dimension Structure** tab of the Dimension Designer for the `Date` dimension, drag the **Calendar Year** attribute from the **Attributes** pane into the **Hierarchies** pane.</span></span>  
  
2.  <span data-ttu-id="a11d8-137">**[属性]** ペインの **[Calendar Semester]** 属性を、 **\<new level>** [階層] **ペインの** セル ( **[Calendar Year]** レベルの下) にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-137">Drag the **Calendar Semester** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **Calendar Year** level.</span></span>  
  
3.  <span data-ttu-id="a11d8-138">**[属性]** ペインの **[Calendar Quarter]** 属性を、 **\<new level>** [階層] **ペインの** セル ( **[Calendar Semester]** レベルの下) にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-138">Drag the **Calendar Quarter** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **Calendar Semester** level.</span></span>  
  
4.  <span data-ttu-id="a11d8-139">**[属性]** ペインの **[English Month Name]** 属性を、 **\<new level>** [階層] **ペインの** セル ( **[Calendar Quarter]** レベルの下) にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-139">Drag the **English Month Name** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **Calendar Quarter** level.</span></span>  
  
5.  <span data-ttu-id="a11d8-140">**[属性]** ペインの **[Date Key]** 属性を、 **\<new level>** [階層] **ペインの** セル ( **[English Month Name]** レベルの下) にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-140">Drag the **Date Key** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **English Month Name** level.</span></span>  
  
6.  <span data-ttu-id="a11d8-141">[**階層**] ペインで、[ **hierarchy** ] 階層のタイトルバーを右クリックし、[**名前の変更**] をクリックして「」と入力し `Calendar Date` ます。</span><span class="sxs-lookup"><span data-stu-id="a11d8-141">In the **Hierarchies** pane, right-click the title bar of the **Hierarchy** hierarchy, click **Rename**, and then type `Calendar Date`.</span></span>  
  
7.  <span data-ttu-id="a11d8-142">右クリックのコンテキストメニューを使用して、 `Calendar Date` 階層で**English Month Name**レベルの名前をに変更し、 `Calendar Month` 日付の**キー**レベルの名前をに変更し `Date` ます。</span><span class="sxs-lookup"><span data-stu-id="a11d8-142">By using the right-click context menu, in the `Calendar Date` hierarchy, rename the **English Month Name** level to `Calendar Month`, and then rename the **Date Key** level to `Date`.</span></span>  
  
8.  <span data-ttu-id="a11d8-143">**Full Date Alternate Key** 属性はもう使用しないので、 **[属性]** ペインからこの属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-143">Delete the **Full Date Alternate Key** attribute from the **Attributes** pane because you will not be using it.</span></span> <span data-ttu-id="a11d8-144">**[オブジェクトの削除]** 確認ウィンドウで、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-144">Click **OK** in the **Delete Objects** confirmation window.</span></span>  
  
9. <span data-ttu-id="a11d8-145">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-145">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-attribute-relationships"></a><span data-ttu-id="a11d8-146">属性リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="a11d8-146">Defining Attribute Relationships</span></span>  
 <span data-ttu-id="a11d8-147">基になるデータで属性リレーションシップがサポートされる場合、属性間の属性リレーションシップを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a11d8-147">If the underlying data supports it, you should define attribute relationships between attributes.</span></span> <span data-ttu-id="a11d8-148">属性リレーションシップを定義すると、ディメンション、パーティション、およびクエリの処理速度が上がります。</span><span class="sxs-lookup"><span data-stu-id="a11d8-148">Defining attribute relationships speeds up dimension, partition, and query processing.</span></span>  
  
#### <a name="to-define-attribute-relationships"></a><span data-ttu-id="a11d8-149">属性リレーションシップを定義するには</span><span class="sxs-lookup"><span data-stu-id="a11d8-149">To define attribute relationships</span></span>  
  
1.  <span data-ttu-id="a11d8-150">ディメンションの**ディメンションデザイナー**で、 `Date` [**属性リレーションシップ**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-150">In the **Dimension Designer** for the `Date` dimension, click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="a11d8-151">ダイアグラムで、 **[English Month Name]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-151">In the diagram, right-click the **English Month Name** attribute, and then click **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="a11d8-152">**[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[English Month Name]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-152">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **English Month Name**.</span></span> <span data-ttu-id="a11d8-153">**[関連属性]** を **[Calendar Quarter]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-153">Set the **Related Attribute** to **Calendar Quarter**.</span></span>  
  
4.  <span data-ttu-id="a11d8-154">**[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類を **[固定]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-154">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
     <span data-ttu-id="a11d8-155">リレーションシップの種類を **[固定]** に設定するのは、時間が経過してもメンバー間のリレーションシップが変化しないためです。</span><span class="sxs-lookup"><span data-stu-id="a11d8-155">The relationship type is **Rigid** because relationships between the members will not change over time.</span></span>  
  
5.  <span data-ttu-id="a11d8-156">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-156">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="a11d8-157">ダイアグラムで、 **[Calendar Quarter]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-157">In the diagram, right-click the **Calendar Quarter** attribute, and then click **New Attribute Relationship**.</span></span>  
  
7.  <span data-ttu-id="a11d8-158">**[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[Calendar Quarter]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-158">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Calendar Quarter**.</span></span> <span data-ttu-id="a11d8-159">**[関連属性]** を **[Calendar Semester]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-159">Set the **Related Attribute** to **Calendar Semester**.</span></span>  
  
8.  <span data-ttu-id="a11d8-160">**[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類を **[固定]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-160">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
9. <span data-ttu-id="a11d8-161">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-161">Click **OK**.</span></span>  
  
10. <span data-ttu-id="a11d8-162">ダイアグラムで、 **[Calendar Semester]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-162">In the diagram, right-click the **Calendar Semester** attribute, and then click **New Attribute Relationship**.</span></span>  
  
11. <span data-ttu-id="a11d8-163">**[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[Calendar Semester]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-163">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Calendar Semester**.</span></span> <span data-ttu-id="a11d8-164">**[関連属性]** を **[Calendar Year]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-164">Set the **Related Attribute** to **Calendar Year**.</span></span>  
  
12. <span data-ttu-id="a11d8-165">**[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類を **[固定]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-165">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
13. <span data-ttu-id="a11d8-166">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-166">Click **OK**.</span></span>  
  
14. <span data-ttu-id="a11d8-167">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-167">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="providing-unique-dimension-member-names"></a><span data-ttu-id="a11d8-168">一意なディメンション メンバー名の指定</span><span class="sxs-lookup"><span data-stu-id="a11d8-168">Providing Unique Dimension Member Names</span></span>  
 <span data-ttu-id="a11d8-169">この実習では、 **EnglishMonthName**、 **CalendarQuarter**、および **CalendarSemester** 属性で使用する表示名の列を作成します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-169">In this task, you will create user-friendly name columns that will be used by the **EnglishMonthName**, **CalendarQuarter**, and **CalendarSemester** attributes.</span></span>  
  
#### <a name="to-provide-unique-dimension-member-names"></a><span data-ttu-id="a11d8-170">一意なディメンション メンバー名を指定するには</span><span class="sxs-lookup"><span data-stu-id="a11d8-170">To provide unique dimension member names</span></span>  
  
1.  <span data-ttu-id="a11d8-171">\*\* [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012**データソースビューに切り替えるには、ソリューションエクスプローラーの [**データソースビュー\*\* ] フォルダーでそれをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-171">To switch to the **[!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012** data source view, double-click it in the **Data Source Views** folder in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="a11d8-172">[**テーブル**] ペインで `Date` 、を右クリックし、[**新しい名前付き計算**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-172">In the **Tables** pane, right-click `Date`, and then click **New Named Calculation**.</span></span>  
  
3.  <span data-ttu-id="a11d8-173">[**名前付き計算の作成**] ダイアログボックスで、[ `MonthName` **列名**] ボックスに「」と入力します。次に、[**式**] ボックスに次のステートメントを入力するか、またはコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="a11d8-173">In the **Create Named Calculation** dialog box, type `MonthName` in the **Column name** box, and then type or copy and paste the following statement in the **Expression** box:</span></span>  
  
    ```  
    EnglishMonthName+' '+ CONVERT(CHAR (4), CalendarYear)  
    ```  
  
     <span data-ttu-id="a11d8-174">このステートメントは、テーブルの各月に表示されている月と年度を連結し、連結した名前を新しい列に表示します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-174">The statement concatenates the month and year for each month in the table into a new column.</span></span>  
  
4.  <span data-ttu-id="a11d8-175">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-175">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="a11d8-176">[**テーブル**] ペインで `Date` 、を右クリックし、[**新しい名前付き計算**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-176">In the **Tables** pane, right-click `Date`, and then click **New Named Calculation**.</span></span>  
  
6.  <span data-ttu-id="a11d8-177">[**名前付き計算の作成**] ダイアログボックスで、[ `CalendarQuarterDesc` **列名**] ボックスに「」と入力し、次の SQL スクリプトを入力するかコピーして、[**式**] ボックスに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="a11d8-177">In the **Create Named Calculation** dialog box, type `CalendarQuarterDesc` in the **Column name** box, and then type or copy and paste the following SQL script in the **Expression** box:</span></span>  
  
    ```  
    'Q' + CONVERT(CHAR (1), CalendarQuarter) +' '+ 'CY ' +  
    CONVERT(CHAR (4), CalendarYear)  
    ```  
  
     <span data-ttu-id="a11d8-178">この SQL スクリプトは、テーブルの各四半期に表示されている四半期と年度を連結し、連結した名前を新しい列に表示します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-178">This SQL script concatenates the calendar quarter and year for each quarter in the table into a new column.</span></span>  
  
7.  <span data-ttu-id="a11d8-179">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-179">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="a11d8-180">[**テーブル**] ペインで `Date` 、を右クリックし、[**新しい名前付き計算**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-180">In the **Tables** pane, right-click `Date`, and then click **New Named Calculation**.</span></span>  
  
9. <span data-ttu-id="a11d8-181">[**名前付き計算の作成**] ダイアログボックスで、[ `CalendarSemesterDesc` **列名**] ボックスに「」と入力し、次の SQL スクリプトを入力するかコピーして、[**式**] ボックスに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="a11d8-181">In the **Create Named Calculation** dialog box, type `CalendarSemesterDesc` in the **Column name** box, and then type or copy and paste the following SQL script in the **Expression** box:</span></span>  
  
    ```  
    CASE  
    WHEN CalendarSemester = 1 THEN 'H1' + ' ' + 'CY' + ' '   
           + CONVERT(CHAR(4), CalendarYear)  
    ELSE  
    'H2' + ' ' + 'CY' + ' ' + CONVERT(CHAR(4), CalendarYear)  
    END  
    ```  
  
     <span data-ttu-id="a11d8-182">この SQL スクリプトは、テーブルの各半期に表示されている半期と年度を連結し、連結した名前を新しい列に表示します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-182">This SQL script concatenates the calendar semester and year for each semester in the table into a new column.</span></span>  
  
10. <span data-ttu-id="a11d8-183">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-183">Click **OK.**</span></span>  
  
11. <span data-ttu-id="a11d8-184">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-184">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-composite-keycolumns-and-setting-the-name-column"></a><span data-ttu-id="a11d8-185">複合 KeyColumns の定義と名前列の設定</span><span class="sxs-lookup"><span data-stu-id="a11d8-185">Defining Composite KeyColumns and Setting the Name Column</span></span>  
 <span data-ttu-id="a11d8-186">**KeyColumns** プロパティは、属性のキーを表す 1 つ以上の列を示します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-186">The **KeyColumns** property contains the column or columns that represent the key for the attribute.</span></span> <span data-ttu-id="a11d8-187">この実習では、複合 **KeyColumns**を定義します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-187">In this task, you will define composite **KeyColumns**.</span></span>  
  
#### <a name="to-define-composite-keycolumns-for-the-english-month-name-attribute"></a><span data-ttu-id="a11d8-188">English Month Name 属性の複合 KeyColumns を定義するには</span><span class="sxs-lookup"><span data-stu-id="a11d8-188">To define composite KeyColumns for the English Month Name attribute</span></span>  
  
1.  <span data-ttu-id="a11d8-189">Date ディメンションの **[ディメンション構造]** タブを開きます。</span><span class="sxs-lookup"><span data-stu-id="a11d8-189">Open the **Dimension Structure** tab for the Date dimension.</span></span>  
  
2.  <span data-ttu-id="a11d8-190">**[属性]** ペインで、 **[English Month Name]** 属性をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-190">In the **Attributes** pane, click the **English Month Name** attribute.</span></span>  
  
3.  <span data-ttu-id="a11d8-191">**[プロパティ]** ウィンドウで **[KeyColumns]** フィールドをクリックし、参照ボタン (**[...]**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-191">In the **Properties** window, click the **KeyColumns** field, and then click the browse (**...**) button.</span></span>  
  
4.  <span data-ttu-id="a11d8-192">[**キー列**] ダイアログボックスの [**使用できる列**] ボックスの一覧で、 **calendaryear**列を選択し、ボタンをクリックし **>** ます。</span><span class="sxs-lookup"><span data-stu-id="a11d8-192">In the **Key Columns** dialog box, in the **Available Columns** list, select the column **CalendarYear**, and then click the **>** button.</span></span>  
  
5.  <span data-ttu-id="a11d8-193">**[EnglishMonthName]** 列と **[CalendarYear]** 列が **[キー列]** ボックスの一覧に表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a11d8-193">The **EnglishMonthName** and **CalendarYear** columns are now displayed in the **Key Columns** list.</span></span>  
  
6.  <span data-ttu-id="a11d8-194">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-194">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="a11d8-195">**EnglishMonthName** 属性の **NameColumn** プロパティを設定するには、[プロパティ] ウィンドウで **[NameColumn]** フィールドをクリックし、参照ボタン (**[...]**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-195">To set the **NameColumn** property of the **EnglishMonthName** attribute, click the **NameColumn** field in the Properties window, and then click the browse (**...**) button.</span></span>  
  
8.  <span data-ttu-id="a11d8-196">[**名前列**] ダイアログボックスの [**基**になる列] ボックスの一覧で、を選択し、 `MonthName` [ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-196">In the **Name Column** dialog box, in the **Source Column** list, select `MonthName`, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="a11d8-197">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-197">On the **File** menu, click **Save All**.</span></span>  
  
#### <a name="to-define-composite-keycolumns-for-the-calendar-quarter-attribute"></a><span data-ttu-id="a11d8-198">Calendar Quarter 属性の複合 KeyColumns を定義するには</span><span class="sxs-lookup"><span data-stu-id="a11d8-198">To define composite KeyColumns for the Calendar Quarter attribute</span></span>  
  
1.  <span data-ttu-id="a11d8-199">**[属性]** ペインで、 **[Calendar Quarter]** 属性をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-199">In the **Attributes** pane, click the **Calendar Quarter** attribute.</span></span>  
  
2.  <span data-ttu-id="a11d8-200">**[プロパティ]** ウィンドウで **[KeyColumns]** フィールドをクリックし、参照ボタン (**[...]**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-200">In the **Properties** window, click the **KeyColumns** field, and then click the browse (**...**) button.</span></span>  
  
3.  <span data-ttu-id="a11d8-201">[**キー列**] ダイアログボックスの [**使用できる列**] ボックスの一覧で、 **calendaryear**列を選択し、ボタンをクリックし **>** ます。</span><span class="sxs-lookup"><span data-stu-id="a11d8-201">In the **Key Columns** dialog box, in the **Available Columns** list, select the column **CalendarYear**, and then click the **>** button.</span></span>  
  
     <span data-ttu-id="a11d8-202">**[CalendarQuarter]** 列と **[CalendarYear]** 列が **[キー列]** ボックスの一覧に表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a11d8-202">The **CalendarQuarter** and **CalendarYear** columns are now displayed in the **Key Columns** list.</span></span>  
  
4.  <span data-ttu-id="a11d8-203">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-203">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="a11d8-204">**Calendar Quarter** 属性の **NameColumn** プロパティを設定するには、[プロパティ] ウィンドウで **[NameColumn]** フィールドをクリックし、参照ボタン (**[...]**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-204">To set the **NameColumn** property of the **Calendar Quarter** attribute, click the **NameColumn** field in the Properties window, and then click the browse (**...**) button.</span></span>  
  
6.  <span data-ttu-id="a11d8-205">[**名前列**] ダイアログボックスの [**基**になる列] ボックスの一覧で、を選択し、 `CalendarQuarterDesc` [ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-205">In the **Name Column** dialog box, in the **Source Column** list, select `CalendarQuarterDesc`, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="a11d8-206">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-206">On the **File** menu, click **Save All**.</span></span>  
  
#### <a name="to-define-composite-keycolumns-for-the-calendar-semester-attribute"></a><span data-ttu-id="a11d8-207">Calendar Semester 属性の複合 KeyColumns を定義するには</span><span class="sxs-lookup"><span data-stu-id="a11d8-207">To define composite KeyColumns for the Calendar Semester attribute</span></span>  
  
1.  <span data-ttu-id="a11d8-208">**[属性]** ペインで、 **[Calendar Semester]** 属性をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-208">In the **Attributes** pane, click the **Calendar Semester** attribute.</span></span>  
  
2.  <span data-ttu-id="a11d8-209">**[プロパティ]** ウィンドウで **[KeyColumns]** フィールドをクリックし、参照ボタン (**[...]**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-209">In the **Properties** window, click the **KeyColumns** field, and then click the browse (**...**) button.</span></span>  
  
3.  <span data-ttu-id="a11d8-210">**[キー列]** ダイアログ ボックスの **[使用できる列]** ボックスの一覧で **[CalendarYear]** 列を選択し、**[>]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-210">In the **Key Columns** dialog box, in the **Available Columns** list, select the column, **CalendarYear**, and then click the **>** button.</span></span>  
  
     <span data-ttu-id="a11d8-211">**[CalendarSemester]** 列と **[CalendarYear]** 列が **[キー列]** ボックスの一覧に表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a11d8-211">The **CalendarSemester** and **CalendarYear** columns are now displayed in the **Key Columns** list.</span></span>  
  
4.  <span data-ttu-id="a11d8-212">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-212">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="a11d8-213">**Calendar Semester** 属性の **NameColumn** プロパティを設定するには、[プロパティ] ウィンドウで **[NameColumn]** フィールドをクリックし、参照ボタン (**[...]**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-213">To set the **NameColumn** property of the **Calendar Semester** attribute, click the **NameColumn** field in the property window, and then click the browse (**...**) button.</span></span>  
  
6.  <span data-ttu-id="a11d8-214">[**名前列**] ダイアログボックスの [**基**になる列] ボックスの一覧で、を選択し、 `CalendarSemesterDesc` [ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-214">In the **Name Column** dialog box, in the **Source Column** list, select `CalendarSemesterDesc`, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="a11d8-215">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-215">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="deploying-and-viewing-the-changes"></a><span data-ttu-id="a11d8-216">変更の配置と表示</span><span class="sxs-lookup"><span data-stu-id="a11d8-216">Deploying and Viewing the Changes</span></span>  
 <span data-ttu-id="a11d8-217">属性と階層を変更したら、変更を表示する前に変更を配置し、関連するオブジェクトを再処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a11d8-217">After you have changed attributes and hierarchies, you must deploy the changes and reprocess the related objects before you can view the changes.</span></span>  
  
#### <a name="to-deploy-and-view-the-changes"></a><span data-ttu-id="a11d8-218">変更を配置して表示するには</span><span class="sxs-lookup"><span data-stu-id="a11d8-218">To deploy and view the changes</span></span>  
  
1.  <span data-ttu-id="a11d8-219">**で、** [ビルド] [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-219">On the **Build** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="a11d8-220">"**配置が正常に完了**しました" というメッセージが表示されたら、ディメンションの**ディメンションデザイナー**の [**ブラウザー** ] タブをクリックし、 `Date` デザイナーのツールバーにある [再接続] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-220">After you have received the **Deployment Completed Successfully** message, click the **Browser** tab of **Dimension Designer** for the `Date` dimension, and then click the Reconnect button on the toolbar of the designer.</span></span>  
  
3.  <span data-ttu-id="a11d8-221">**[階層]** ボックスの一覧から **[Calendar Quarter]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-221">Select **Calendar Quarter** from the **Hierarchy** list.</span></span> <span data-ttu-id="a11d8-222">**Calendar Quarter** 属性階層のメンバーを確認します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-222">Review the members in the **Calendar Quarter** attribute hierarchy.</span></span>  
  
     <span data-ttu-id="a11d8-223">名前付き計算を作成して名前として使用しているため、 **Calendar Quarter** 属性階層のメンバー名が明確でわかりやすい名前になっています。</span><span class="sxs-lookup"><span data-stu-id="a11d8-223">Notice that the names of the members of the **Calendar Quarter** attribute hierarchy are clearer and easier to use because you created a named calculation to use as the name.</span></span> <span data-ttu-id="a11d8-224">メンバーは、各年の各四半期の **Calendar Quarter** 属性階層内に存在しています。</span><span class="sxs-lookup"><span data-stu-id="a11d8-224">Members now exist in the **Calendar Quarter** attribute hierarchy for each quarter in each year.</span></span> <span data-ttu-id="a11d8-225">メンバーの並び順は年代順ではありません。</span><span class="sxs-lookup"><span data-stu-id="a11d8-225">The members are not sorted in chronological order.</span></span> <span data-ttu-id="a11d8-226">まず四半期順に並べ替えられ、次に年度順に並べ替えられています。</span><span class="sxs-lookup"><span data-stu-id="a11d8-226">Instead they are sorted by quarter and then by year.</span></span> <span data-ttu-id="a11d8-227">このトピックの次の実習では、この属性階層のメンバーが年度順に並べられ、さらに四半期順に並べられるように設定します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-227">In the next task in this topic, you will modify this behavior to sort the members of this attribute hierarchy by year and then by quarter.</span></span>  
  
4.  <span data-ttu-id="a11d8-228">**English Month Name** および **Calendar Semester** 属性階層のメンバーを確認します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-228">Review the members of the **English Month Name** and **Calendar Semester** attribute hierarchies.</span></span>  
  
     <span data-ttu-id="a11d8-229">この 2 つの階層のメンバーも日時順には並んでいません。</span><span class="sxs-lookup"><span data-stu-id="a11d8-229">Notice that the members of these hierarchies are also not sorted in chronological order.</span></span> <span data-ttu-id="a11d8-230">EnglishMonthName は月、CalendarSemester は半期の順にまず並べ替えられ、その後、年度順に並べ替えられています。</span><span class="sxs-lookup"><span data-stu-id="a11d8-230">Instead, they are sorted by month or semester, respectively, and then by year.</span></span> <span data-ttu-id="a11d8-231">このトピックの次の実習では、この並べ替え順序が変わるように複合キーを修正します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-231">In the next task in this topic, you will modify this behavior to change this sort order.</span></span>  
  
## <a name="changing-the-sort-order-by-modifying-composite-key-member-order"></a><span data-ttu-id="a11d8-232">複合キーのメンバーの順序を変更することによる並べ替え順序の変更</span><span class="sxs-lookup"><span data-stu-id="a11d8-232">Changing the Sort Order by Modifying Composite Key Member Order</span></span>  
 <span data-ttu-id="a11d8-233">この実習では、複合キーを構成するキーの順序を変更することにより並べ替え順序を変更します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-233">In this task, you will change the sort order by changing the order of the keys that make up the composite key.</span></span>  
  
#### <a name="to-modify-the-composite-key-member-order"></a><span data-ttu-id="a11d8-234">複合キーのメンバーの順序を変更するには</span><span class="sxs-lookup"><span data-stu-id="a11d8-234">To modify the composite key member order</span></span>  
  
1.  <span data-ttu-id="a11d8-235">ディメンションのディメンションデザイナーの [**ディメンション構造**] タブを開き、 `Date` [**属性**] ペインで [ **Calendar 半期**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-235">Open the **Dimension Structure** tab of Dimension Designer for the `Date` dimension, and then select **Calendar Semester** in the **Attributes** pane.</span></span>  
  
2.  <span data-ttu-id="a11d8-236">[プロパティ] ウィンドウで、 **OrderBy** プロパティの値を確認します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-236">In the Properties window, review the value for the **OrderBy** property.</span></span> <span data-ttu-id="a11d8-237">**Key**に設定されています。</span><span class="sxs-lookup"><span data-stu-id="a11d8-237">It is set to **Key**.</span></span>  
  
     <span data-ttu-id="a11d8-238">**Calendar Semester** 属性階層のメンバーは、キー値に基づいて並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="a11d8-238">The members of the **Calendar Semester** attribute hierarchy are sorted by their key value.</span></span> <span data-ttu-id="a11d8-239">複合キーにより、メンバーのキーがまず 1 番目のキーに基づいて並べ替えられ、次に 2 番目のキーに基づいて並べ替えられています。</span><span class="sxs-lookup"><span data-stu-id="a11d8-239">With a composite key, the ordering of the member keys is based first on the value of the first member key, and then on the value of the second member key.</span></span> <span data-ttu-id="a11d8-240">つまり、 **Calendar Semester** 属性階層のメンバーはまず半期順に並べ替えられ、続いて年度順に並べ替えられています。</span><span class="sxs-lookup"><span data-stu-id="a11d8-240">In other words, the members of the **Calendar Semester** attribute hierarchy are sorted first by semester and then by year.</span></span>  
  
3.  <span data-ttu-id="a11d8-241">**KeyColumns**プロパティの値を変更するため、[プロパティ] ウィンドウで参照ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-241">In the Properties window, click the ellipsis browse button (**...**) to change the **KeyColumns** property value.</span></span>  
  
4.  <span data-ttu-id="a11d8-242">**[キー列]** ダイアログ ボックスの **[キー列]** ボックスの一覧で、 **[CalendarSemester]** が選択されていることを確認します。次に、下矢印をクリックし、この複合キーのメンバーの順序を逆にします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-242">In the **Key Columns** list of the **Key Columns** dialog box, verify that **CalendarSemester** is selected, and then click the down arrow to reverse the order of the members of this composite key.</span></span> <span data-ttu-id="a11d8-243">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-243">Click **OK**.</span></span>  
  
     <span data-ttu-id="a11d8-244">CalendarSemester 属性階層のメンバーが、まず年度順に並べ替えられ、続いて半期順に並べ替えられるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a11d8-244">The members of the attribute hierarchy are now sorted first by year and then by semester.</span></span>  
  
5.  <span data-ttu-id="a11d8-245">**[属性]** ペインで **[Calendar Quarter]** を選択した後、[プロパティ] ウィンドウで、**KeyColumns**プロパティの省略記号ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-245">Select **Calendar Quarter** in the **Attributes** pane, and then click the ellipsis browse button (**...**) for the **KeyColumns** property in the Properties window.</span></span>  
  
6.  <span data-ttu-id="a11d8-246">**[キー列]** ダイアログ ボックスの **[キー列]** ボックスの一覧で、 **[CalendarQuarter]** が選択されていることを確認します。次に、下矢印をクリックし、この複合キーのメンバーの順序を逆にします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-246">In the **Key Columns** list of the **Key Columns** dialog box, verify that **CalendarQuarter** is selected, and then click the down arrow to reverse the order of the members of this composite key.</span></span> <span data-ttu-id="a11d8-247">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-247">Click **OK**.</span></span>  
  
     <span data-ttu-id="a11d8-248">CalendarQuarter 属性階層のメンバーが、まず年度順に並べ替えられ、続いて四半期順に並べ替えられるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a11d8-248">The members of the attribute hierarchy are now sorted first by year and then by quarter.</span></span>  
  
7.  <span data-ttu-id="a11d8-249">**[属性]** ペインで **[English Month Name]** を選択した後、[プロパティ] ウィンドウで、**KeyColumns**プロパティの省略記号ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-249">Select **English Month Name** in the **Attributes** pane, and then click the ellipsis button (**...**) for the **KeyColumns** property in the Properties window.</span></span>  
  
8.  <span data-ttu-id="a11d8-250">**[キー列]** ダイアログ ボックスの **[キー列]** ボックスの一覧で、 **[EnglishMonthName]** が選択されていることを確認します。次に、下矢印をクリックし、この複合キーのメンバーの順序を逆にします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-250">In the **Key Columns** list of the **Key Columns** dialog box, verify that **EnglishMonthName** is selected, and then click the down arrow to reverse the order of the members of this composite key.</span></span> <span data-ttu-id="a11d8-251">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-251">Click **OK**.</span></span>  
  
     <span data-ttu-id="a11d8-252">EnglishMonthName 属性階層のメンバーが、まず年度順に並べ替えられ、続いて月順に並べ替えられるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a11d8-252">The members of the attribute hierarchy are now sorted first by year and then by month.</span></span>  
  
9. <span data-ttu-id="a11d8-253">**で、** [ビルド] [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-253">On the **Build** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Deploy Analysis Services Tutorial**.</span></span> <span data-ttu-id="a11d8-254">配置が正常に完了したら、ディメンションのディメンションデザイナーで [**ブラウザー** ] タブをクリックし `Date` ます。</span><span class="sxs-lookup"><span data-stu-id="a11d8-254">When deployment has successfully completed, click the **Browser** tab in Dimension Designer for the `Date` dimension.</span></span>  
  
10. <span data-ttu-id="a11d8-255">**[ブラウザー]** タブのツール バーで、[再接続] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a11d8-255">On the toolbar of the **Browser** tab, click the Reconnect button.</span></span>  
  
11. <span data-ttu-id="a11d8-256">**Calendar Quarter** および **Calendar Semester** 属性階層のメンバーを確認します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-256">Review the members of the **Calendar Quarter** and **Calendar Semester** attribute hierarchies.</span></span>  
  
     <span data-ttu-id="a11d8-257">これらの階層のメンバーは、日時順に並べ替えられるようになりました。まず年度順に並べ替えられ、続いて Calendar Quarter は四半期順に、CalendarSemester は半期順に並べ替えられています。</span><span class="sxs-lookup"><span data-stu-id="a11d8-257">Notice that the members of these hierarchies are now sorted in chronological order, by year and then by quarter or semester, respectively.</span></span>  
  
12. <span data-ttu-id="a11d8-258">**English Month Name** 属性階層のメンバーを確認します。</span><span class="sxs-lookup"><span data-stu-id="a11d8-258">Review the members of the **English Month Name** attribute hierarchy.</span></span>  
  
     <span data-ttu-id="a11d8-259">属性階層のメンバーは、まず年度順に並べ替えられ、続いて月名順 (アルファベット順) に並べ替えられるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a11d8-259">Notice that the members of the hierarchy are now sorted first by year and then alphabetically by month.</span></span> <span data-ttu-id="a11d8-260">これは、データ ソース ビューの EnglishCalendarMonth 列のデータ型が、基になるリレーショナル データベースでの nvarchar データ型に基づき、文字列型となっているためです。</span><span class="sxs-lookup"><span data-stu-id="a11d8-260">This is because the data type for the EnglishCalendarMonth column in the data source view is a string column, based on the nvarchar data type in the underlying relational database.</span></span> <span data-ttu-id="a11d8-261">各年度の月を古い順に並べ替えられるようにする方法の詳細については、「 [2 次属性に基づく属性メンバーの並べ替え](lesson-4-5-sorting-attribute-members-based-on-a-secondary-attribute.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a11d8-261">For information about how to enable the months to be sorted chronologically within each year, see [Sorting Attribute Members Based on a Secondary Attribute](lesson-4-5-sorting-attribute-members-based-on-a-secondary-attribute.md).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="a11d8-262">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="a11d8-262">Next Task in Lesson</span></span>  
 [<span data-ttu-id="a11d8-263">配置したキューブの表示</span><span class="sxs-lookup"><span data-stu-id="a11d8-263">Browsing the Deployed Cube</span></span>](lesson-3-5-browsing-the-deployed-cube.md)  
  
## <a name="see-also"></a><span data-ttu-id="a11d8-264">参照</span><span class="sxs-lookup"><span data-stu-id="a11d8-264">See Also</span></span>  
 [<span data-ttu-id="a11d8-265">多次元モデル内のディメンション</span><span class="sxs-lookup"><span data-stu-id="a11d8-265">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
