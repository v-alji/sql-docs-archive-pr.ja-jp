---
title: ドリルスルーアクションの定義と使用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 3765f865-2b93-44be-b290-28e3815d5ecb
author: minewiskan
ms.author: owend
ms.openlocfilehash: ea19a9721d87936bc88b5401c71ee550a47bc1ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714705"
---
# <a name="defining-and-using-a-drillthrough-action"></a><span data-ttu-id="b9e8f-102">ドリルスルー アクションの定義と使用</span><span class="sxs-lookup"><span data-stu-id="b9e8f-102">Defining and Using a Drillthrough Action</span></span>
  <span data-ttu-id="b9e8f-103">ファクト ディメンションによってファクト データを多次元化する場合、必要なデータのみが返されるようにフィルターを設定しないとクエリのパフォーマンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-103">Dimensioning fact data by a fact dimension without correctly filtering the data that the query returns can cause slow query performance.</span></span> <span data-ttu-id="b9e8f-104">これを回避するために、返される合計行数を制限するドリルスルー アクションを定義できます。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-104">To avoid this, you can define a drillthrough action that restricts the total number of rows that are returned.</span></span> <span data-ttu-id="b9e8f-105">これにより、クエリのパフォーマンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-105">This will significantly improve query performance.</span></span>  
  
 <span data-ttu-id="b9e8f-106">このトピックの作業では、インターネット経由での顧客への販売について注文の詳細情報を返すドリルスルー アクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-106">In the tasks in this topic, you define a drillthrough action to return order detail information for sales to customers over the Internet.</span></span>  
  
## <a name="defining-the-drillthrough-action-properties"></a><span data-ttu-id="b9e8f-107">ドリルスルー アクション プロパティの定義</span><span class="sxs-lookup"><span data-stu-id="b9e8f-107">Defining the Drillthrough Action Properties</span></span>  
  
1.  <span data-ttu-id="b9e8f-108">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーを開いて、 **[アクション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-108">In Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, click the **Actions** tab.</span></span>  
  
     <span data-ttu-id="b9e8f-109">**[アクション]** タブにはいくつかのペインがあります。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-109">The **Actions** tab includes several panes.</span></span> <span data-ttu-id="b9e8f-110">このタブの左側には **[アクション オーガナイザー]** ペインと **[計算ツール]** ペインがあります。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-110">On the left side of the tab are the **Action Organizer** pane and the **Calculation Tools** pane.</span></span> <span data-ttu-id="b9e8f-111">これら 2 つのペインの右側には **[表示]** ペインがあり、 **[アクション オーガナイザー]** ペインで選択したアクションの詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-111">The pane to the right of these two panes is the **Display** pane, which contains the details of the action that is selected in the **Action Organizer** pane.</span></span>  
  
     <span data-ttu-id="b9e8f-112">次の図はキューブ デザイナーの **[アクション]** タブを示しています。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-112">The following image shows the **Actions** tab of Cube Designer.</span></span>  
  
     <span data-ttu-id="b9e8f-113">![キューブ デザイナーの [アクション] タブ](../../2014/tutorials/media/l8-action1.gif "キューブ デザイナーの [アクション] タブ")</span><span class="sxs-lookup"><span data-stu-id="b9e8f-113">![Actions tab of Cube Designer](../../2014/tutorials/media/l8-action1.gif "Actions tab of Cube Designer")</span></span>  
  
2.  <span data-ttu-id="b9e8f-114">**[アクション]** タブのツール バーで **[新しいドリルスルー アクション]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-114">On the toolbar of the **Actions** tab, click the **New Drillthrough Action** button.</span></span>  
  
     <span data-ttu-id="b9e8f-115">表示ペインに、空のアクション テンプレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-115">A blank action template appears in the display pane.</span></span>  
  
     <span data-ttu-id="b9e8f-116">![表示ペインの空白のアクション テンプレート](../../2014/tutorials/media/l8-action2.gif "表示ペインの空白のアクション テンプレート")</span><span class="sxs-lookup"><span data-stu-id="b9e8f-116">![Blank Action template in the display pane](../../2014/tutorials/media/l8-action2.gif "Blank Action template in the display pane")</span></span>  
  
3.  <span data-ttu-id="b9e8f-117">[**名前**] ボックスで、このアクションの名前をに変更 `Internet Sales Details Drillthrough Action` します。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-117">In the **Name** box, change the name of this action to `Internet Sales Details Drillthrough Action`.</span></span>  
  
4.  <span data-ttu-id="b9e8f-118">**[メジャー グループのメンバー]** リストで **[Internet Sales]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-118">In the **Measure group members** list, select **Internet Sales**.</span></span>  
  
5.  <span data-ttu-id="b9e8f-119">**[ドリルスルー列]** で、 **[ディメンション]** リストから **[Internet Sales Order Details]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-119">In the **Drillthrough Columns** box, select **Internet Sales Order Details** in the **Dimensions** list.</span></span>  
  
6.  <span data-ttu-id="b9e8f-120">**[返される列]** リストで、 **[Item Description]** と **[Order Number]** チェック ボックスをオンにして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-120">In the **Return Columns** list, select the **Item Description** and the **Order Number** check boxes, and then click **OK**.</span></span> <span data-ttu-id="b9e8f-121">次の図は、ここまでの手順を実行した場合に表示されるアクション テンプレートを示しています。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-121">The following image shows the Action template as it should appear at this point in this procedure.</span></span>  
  
     <span data-ttu-id="b9e8f-122">![[ドリルスルー列] ボックス](../../2014/tutorials/media/l8-action3.gif "[ドリルスルー列] ボックス")</span><span class="sxs-lookup"><span data-stu-id="b9e8f-122">![Drillthrough Columns box](../../2014/tutorials/media/l8-action3.gif "Drillthrough Columns box")</span></span>  
  
7.  <span data-ttu-id="b9e8f-123">次の図のように、 **[追加のプロパティ]** ボックスを展開します。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-123">Expand the **Additional Properties** box, as shown in the following image.</span></span>  
  
     <span data-ttu-id="b9e8f-124">![[追加のプロパティ] ボックス](../../2014/tutorials/media/l8-action4.gif "[追加のプロパティ] ボックス")</span><span class="sxs-lookup"><span data-stu-id="b9e8f-124">![Additional Properties box](../../2014/tutorials/media/l8-action4.gif "Additional Properties box")</span></span>  
  
8.  <span data-ttu-id="b9e8f-125">[**最大行数**] ボックスに「」と入力 `10` します。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-125">In the **Maximum Rows** box, type `10`.</span></span>  
  
9. <span data-ttu-id="b9e8f-126">[**キャプション**] ボックスに「」と入力 `Drillthrough to Order Details...` します。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-126">In the **Caption** box, type `Drillthrough to Order Details...`.</span></span>  
  
     <span data-ttu-id="b9e8f-127">これらの設定は、返される行数を制限し、クライアント アプリケーションのメニューに表示されるキャプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-127">These settings limit the number of rows returned and specify the caption that appears in the client application menu.</span></span> <span data-ttu-id="b9e8f-128">次の図は、 **[追加のプロパティ]** ボックスでの設定を示しています。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-128">The following image shows these settings in the **AdditionalProperties** box.</span></span>  
  
     <span data-ttu-id="b9e8f-129">![[追加のプロパティ] ボックス](../../2014/tutorials/media/l8-action5.gif "[追加のプロパティ] ボックス")</span><span class="sxs-lookup"><span data-stu-id="b9e8f-129">![Additional Properties box](../../2014/tutorials/media/l8-action5.gif "Additional Properties box")</span></span>  
  
## <a name="using-the-drillthrough-action"></a><span data-ttu-id="b9e8f-130">ドリルスルー アクションの使用</span><span class="sxs-lookup"><span data-stu-id="b9e8f-130">Using the Drillthrough Action</span></span>  
  
1.  <span data-ttu-id="b9e8f-131">**[ビルド]** メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-131">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="b9e8f-132">配置が正常に完了したら、 **Tutorial キューブのキューブ デザイナーで** [ブラウザー] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] タブをクリックし、 **[再接続]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-132">When deployment has successfully completed, click the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Reconnect** button.</span></span>  
  
3.  <span data-ttu-id="b9e8f-133">Excel を起動します。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-133">Start Excel.</span></span>  
  
4.  <span data-ttu-id="b9e8f-134">**Internet Sales-Sales Amount** メジャーを値領域に追加します。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-134">Add the **Internet Sales-Sales Amount** measure to the Values area.</span></span>  
  
5.  <span data-ttu-id="b9e8f-135">**Customer** ディメンションの **Location** フォルダーの **Customer Geography** ユーザー定義階層を **[レポート フィルター]** 領域に追加します。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-135">Add the **Customer Geography** user-defined hierarchy from the **Location** folder in the **Customer** dimension to the **Report Filter** area.</span></span>  
  
6.  <span data-ttu-id="b9e8f-136">ピボットテーブルの **Customer Geography**で、1 人の顧客を選択するフィルターを追加します。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-136">On the PivotTable, in **Customer Geography**, add a filter that selects a single customer.</span></span> <span data-ttu-id="b9e8f-137">**[All Customers]**、 **[Australia]**、 **[Queensland]**、 **[Brisbane]**、 **[4000]** の順に展開し、 **Adam Powell**のチェック ボックスをオンにして **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-137">Expand **All Customers**, expand **Australia**, expand **Queensland**, expand **Brisbane**, expand **4000**, select the check box for **Adam Powell**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="b9e8f-138">Adam Powell に対する [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 社製品の売上合計がデータ領域に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-138">The total sales of products by [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] to Adam Powell are displayed in the data area.</span></span>  
  
7.  <span data-ttu-id="b9e8f-139">売上高を右クリックし、 **[追加アクション]** をポイントして、 **[Drillthrough to Order Details]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-139">Right-click on the sales amount, point to **Additional Actions**, and then click **Drillthrough to Order Details**.</span></span>  
  
     <span data-ttu-id="b9e8f-140">次の図のように、Adam Powell に発送された注文の詳細が **[データ サンプル ビューアー]** に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-140">The details of the orders that were shipped to Adam Powell are displayed in the **Data Sample Viewer**, as shown in the following image.</span></span> <span data-ttu-id="b9e8f-141">しかし、注文日、期限、発送日などの追加の情報があればさらに便利です。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-141">However, some additional details would also be useful, such as the order date, due date, and ship date.</span></span> <span data-ttu-id="b9e8f-142">次の手順では、これらの情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-142">In the next procedure, you will add these additional details.</span></span>  
  
     <span data-ttu-id="b9e8f-143">![Adam Powell 氏に出荷された注文](../../2014/tutorials/media/l8-action6.gif "Adam Powell 氏に出荷された注文")</span><span class="sxs-lookup"><span data-stu-id="b9e8f-143">![Orders shipped to Adam Powell](../../2014/tutorials/media/l8-action6.gif "Orders shipped to Adam Powell")</span></span>  
  
8.  <span data-ttu-id="b9e8f-144">Excel を閉じます。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-144">Close Excel/</span></span>  
  
## <a name="modifying-the-drillthrough-action"></a><span data-ttu-id="b9e8f-145">ドリルスルー アクションの変更</span><span class="sxs-lookup"><span data-stu-id="b9e8f-145">Modifying the Drillthrough Action</span></span>  
  
1.  <span data-ttu-id="b9e8f-146">**Internet Sales Order Details** ディメンションのディメンション デザイナーを開きます。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-146">Open Dimension Designer for the **Internet Sales Order Details** dimension.</span></span>  
  
     <span data-ttu-id="b9e8f-147">このディメンションには 3 つの属性しか定義されていません。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-147">Notice that only three attributes have been defined for this dimension.</span></span>  
  
2.  <span data-ttu-id="b9e8f-148">**[データ ソース ビュー]** ペインで、何もない領域を右クリックし、 **[すべてのテーブルを表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-148">In the **Data Source View** pane, right-click an open area, and then click **Show All Tables**.</span></span>  
  
3.  <span data-ttu-id="b9e8f-149">**[書式]** メニューの **[自動レイアウト]** をポイントし、 **[ダイアグラム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-149">On the **Format** menu, point to **Autolayout** and then click **Diagram**.</span></span>  
  
4.  <span data-ttu-id="b9e8f-150">**InternetSales (dbo.FactInternetSales)** テーブルを検索します。検索するには、 **[データ ソース ビュー]** ペインの空いている領域を右クリックし、</span><span class="sxs-lookup"><span data-stu-id="b9e8f-150">Locate the **InternetSales (dbo.FactInternetSales)** table by right-clicking in an open area of the **Data Source View** pane.</span></span> <span data-ttu-id="b9e8f-151">**[テーブルの検索]** 、 **[InternetSales]** 、 **[OK]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-151">Then click **Find Table,** click **InternetSales,** and click **OK**.</span></span>  
  
5.  <span data-ttu-id="b9e8f-152">以下の列を基にして、新しい属性を作成します。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-152">Create new attributes based on the following columns:</span></span>  
  
    -   <span data-ttu-id="b9e8f-153">OrderDateKey</span><span class="sxs-lookup"><span data-stu-id="b9e8f-153">OrderDateKey</span></span>  
  
    -   <span data-ttu-id="b9e8f-154">DueDateKey</span><span class="sxs-lookup"><span data-stu-id="b9e8f-154">DueDateKey</span></span>  
  
    -   <span data-ttu-id="b9e8f-155">ShipDateKey</span><span class="sxs-lookup"><span data-stu-id="b9e8f-155">ShipDateKey</span></span>  
  
6.  <span data-ttu-id="b9e8f-156">**Order Date Key**属性の**name**プロパティをに変更し `Order Date` 、 **name column**プロパティの参照ボタンをクリックします。次に、[**名前列**] ダイアログボックスで、基になるテーブルとして [**日付**] を選択し、基になる列として [simpledate] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-156">Change the **Name** property for the **Order Date Key** attribute to `Order Date` Then, click the browse button for the **Name Column** property, and in the **Name Column** dialog box, select **Date** as the source table and select SimpleDate as the source column.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="b9e8f-157">[**期限切れ**日] 属性の [**名前**] プロパティをに変更 `Due Date` し、 **Order Date key**属性と同じ方法を使用して、この属性の**name Column**プロパティを**date. simpledate (WChar)** に変更します。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-157">Change the **Name** property for the **Due Date Key** attribute to `Due Date`, and then, by using the same method as the **Order Date Key** attribute, change the **Name Column** property for this attribute to **Date.SimpleDate (WChar)**.</span></span>  
  
8.  <span data-ttu-id="b9e8f-158">**Ship Date Key**属性の**name**プロパティをに変更 `Ship Date` し、この属性の**Name Column**プロパティを**date. simpledate (WChar)** に変更します。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-158">Change the **Name** property for the **Ship Date Key** attribute to `Ship Date`, and then change the **Name Column** property for this attribute to **Date.SimpleDate (WChar)**.</span></span>  
  
9. <span data-ttu-id="b9e8f-159">**Tutorial キューブのキューブ デザイナーを開き、** [アクション] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] タブに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-159">Switch to the **Actions** tab of Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>  
  
10. <span data-ttu-id="b9e8f-160">**[ドリルスルー列]** ボックスで、チェック ボックスをオンにして以下の列を **[返される列]** リストに追加し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-160">In the **Drillthrough Columns** box, select the check boxes to add the following columns to the **Return Columns** list, and then click **OK**:</span></span>  
  
    -   <span data-ttu-id="b9e8f-161">Order Date</span><span class="sxs-lookup"><span data-stu-id="b9e8f-161">Order Date</span></span>  
  
    -   <span data-ttu-id="b9e8f-162">Due Date</span><span class="sxs-lookup"><span data-stu-id="b9e8f-162">Due Date</span></span>  
  
    -   <span data-ttu-id="b9e8f-163">Ship Date</span><span class="sxs-lookup"><span data-stu-id="b9e8f-163">Ship Date</span></span>  
  
     <span data-ttu-id="b9e8f-164">次の図はこれらの列が選択された状態を示しています。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-164">The following image shows these columns selected.</span></span>  
  
     <span data-ttu-id="b9e8f-165">![[ドリルスルー列] ボックス](../../2014/tutorials/media/l8-action7.gif "[ドリルスルー列] ボックス")</span><span class="sxs-lookup"><span data-stu-id="b9e8f-165">![Drillthrough Columns box](../../2014/tutorials/media/l8-action7.gif "Drillthrough Columns box")</span></span>  
  
## <a name="reviewing-the-modified-drillthrough-action"></a><span data-ttu-id="b9e8f-166">変更されたドリルスルー アクションの確認</span><span class="sxs-lookup"><span data-stu-id="b9e8f-166">Reviewing the Modified Drillthrough Action</span></span>  
  
1.  <span data-ttu-id="b9e8f-167">**[ビルド]** メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-167">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="b9e8f-168">配置が正常に完了したら、 **Tutorial キューブのキューブ デザイナーで** [ブラウザー] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] タブに切り替え、 **[再接続]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-168">When deployment has successfully completed, switch to the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Reconnect** button.</span></span>  
  
3.  <span data-ttu-id="b9e8f-169">Excel を起動します。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-169">Start Excel.</span></span>  
  
4.  <span data-ttu-id="b9e8f-170">値領域の **Internet Sales-Sales Amount** とレポート フィルターの **Customer Geography** を使用してピボットテーブルを再作成します。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-170">Recreate the PivotTable using **Internet Sales-Sales Amount** in the Values area and **Customer Geography** in the Report Filter.</span></span>  
  
     <span data-ttu-id="b9e8f-171">**All Customers**、 **Australia**、 **Queensland**、 **Brisbane**、 **4000**、 **Adam Powell**から選択するフィルターを追加します。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-171">Add a filter that selects from **All Customers**, **Australia**, **Queensland**, **Brisbane**, **4000**, **Adam Powell**.</span></span>  
  
5.  <span data-ttu-id="b9e8f-172">**Internet Sales-Sales Amount** データ セルをクリックし、 **[追加アクション]** をポイントして、 **[Drillthrough to Order Details]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-172">Click the **Internet Sales-Sales Amount** data cell, point to **Additional Actions**, and then click **Drillthrough to Order Details**.</span></span>  
  
     <span data-ttu-id="b9e8f-173">Adam Powell に発送された注文の詳細が一時ワークシートに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-173">The details of these orders shipped to Adam Powell are displayed in a temporary worksheet.</span></span> <span data-ttu-id="b9e8f-174">表示される情報には、次の図に示すように、アイテムの説明、注文番号、受注日、期日、出荷日が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b9e8f-174">This includes item description, order number, order date, due date, and ship date information, as shown in the following image.</span></span>  
  
     <span data-ttu-id="b9e8f-175">![Adam Powell 氏に出荷された注文](../../2014/tutorials/media/l8-action8.gif "Adam Powell 氏に出荷された注文")</span><span class="sxs-lookup"><span data-stu-id="b9e8f-175">![Orders shipped to Adam Powell](../../2014/tutorials/media/l8-action8.gif "Orders shipped to Adam Powell")</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="b9e8f-176">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="b9e8f-176">Next Lesson</span></span>  
 [<span data-ttu-id="b9e8f-177">レッスン 9: パースペクティブと翻訳の定義</span><span class="sxs-lookup"><span data-stu-id="b9e8f-177">Lesson 9: Defining Perspectives and Translations</span></span>](lesson-9-defining-perspectives-and-translations.md)  
  
## <a name="see-also"></a><span data-ttu-id="b9e8f-178">参照</span><span class="sxs-lookup"><span data-stu-id="b9e8f-178">See Also</span></span>  
 <span data-ttu-id="b9e8f-179">[アクション &#40;Analysis Services-多次元データ&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="b9e8f-179">[Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="b9e8f-180">[多次元モデルでのアクション](multidimensional-models/actions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="b9e8f-180">[Actions in Multidimensional Models](multidimensional-models/actions-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="b9e8f-181">[ディメンションのリレーションシップ](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span><span class="sxs-lookup"><span data-stu-id="b9e8f-181">[Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span></span>  
 <span data-ttu-id="b9e8f-182">[ファクトリレーションシップの定義](lesson-5-2-defining-a-fact-relationship.md) </span><span class="sxs-lookup"><span data-stu-id="b9e8f-182">[Defining a Fact Relationship](lesson-5-2-defining-a-fact-relationship.md) </span></span>  
 [<span data-ttu-id="b9e8f-183">ファクト リレーションシップとファクト リレーションシップのプロパティの定義</span><span class="sxs-lookup"><span data-stu-id="b9e8f-183">Define a Fact Relationship and Fact Relationship Properties</span></span>](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)  
  
  
