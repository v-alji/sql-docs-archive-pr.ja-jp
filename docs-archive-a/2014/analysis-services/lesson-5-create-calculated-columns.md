---
title: 'レッスン 6: 計算列を作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d126766a-5699-4e9f-8213-8c7eea0fc14e
author: minewiskan
ms.author: owend
ms.openlocfilehash: dcebf61955e230c9e61c955683b897026553cb52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639757"
---
# <a name="lesson-6-create-calculated-columns"></a><span data-ttu-id="6ccb7-102">レッスン 6: 計算列の作成</span><span class="sxs-lookup"><span data-stu-id="6ccb7-102">Lesson 6: Create Calculated Columns</span></span>
  <span data-ttu-id="6ccb7-103">このレッスンでは、計算列を追加して、モデル内に新しいデータを作成します。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-103">In this lesson, you will create new data in your model by adding calculated columns.</span></span> <span data-ttu-id="6ccb7-104">計算列は、モデル内の既存のデータに基づいて機能します。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-104">A calculated column is based on data that already exists in the model.</span></span> <span data-ttu-id="6ccb7-105">詳細については、「[計算列 (SSAS テーブル)](tabular-models/ssas-calculated-columns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-105">To learn more, see [Calculated Columns &#40;SSAS Tabular&#41;](tabular-models/ssas-calculated-columns.md).</span></span>  
  
 <span data-ttu-id="6ccb7-106">3 つのテーブルに 5 つの計算列を新しく作成します｡</span><span class="sxs-lookup"><span data-stu-id="6ccb7-106">You will create five new calculated columns in three different tables.</span></span> <span data-ttu-id="6ccb7-107">手順は実習ごとに少しずつ異なります。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-107">The steps are slightly different for each task.</span></span> <span data-ttu-id="6ccb7-108">これは、新しい列を作成したり、それらの名前を変更したり、それらをテーブル内のさまざまな場所へ配置するのには、いくつかの方法があることを示すためです。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-108">This is to show you there are several ways to create new columns, rename them, and place them in various locations in a table.</span></span>  
  
 <span data-ttu-id="6ccb7-109">このレッスンの推定所要時間: **15 分**</span><span class="sxs-lookup"><span data-stu-id="6ccb7-109">Estimated time to complete this lesson: **15 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6ccb7-110">前提条件</span><span class="sxs-lookup"><span data-stu-id="6ccb7-110">Prerequisites</span></span>  
 <span data-ttu-id="6ccb7-111">このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-111">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="6ccb7-112">このレッスンの実習を行う前に、前のレッスン「 [レッスン 5: リレーションシップの作成](lesson-4-create-relationships.md)」を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-112">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 5: Create Relationships](lesson-4-create-relationships.md).</span></span>  
  
## <a name="create-calculated-columns"></a><span data-ttu-id="6ccb7-113">計算列の作成</span><span class="sxs-lookup"><span data-stu-id="6ccb7-113">Create Calculated Columns</span></span>  
  
#### <a name="create-a-month-calendar-calculated-column-in-the-date-table"></a><span data-ttu-id="6ccb7-114">Date テーブル内に Month Calendar 計算列を作成する</span><span class="sxs-lookup"><span data-stu-id="6ccb7-114">Create a Month Calendar calculated column in the Date table</span></span>  
  
1.  <span data-ttu-id="6ccb7-115">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、 **[モデル]** メニューをクリックし、 **[モデル ビュー]** をポイントして、 **[データ ビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-115">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, then point to **Model View**, and then click **Data View**.</span></span>  
  
     <span data-ttu-id="6ccb7-116">計算列は、モデル デザイナーのデータ ビューでのみ作成できます。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-116">Calculated columns can only be created by using the model designer in Data View.</span></span>  
  
2.  <span data-ttu-id="6ccb7-117">モデル デザイナーで、 **Date** テーブル (タブ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-117">In the model designer, click the **Date** table (tab).</span></span>  
  
3.  <span data-ttu-id="6ccb7-118">[ **Calendar Quarter** ] 列を右クリックし、[**列の挿入**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-118">Right-click the **Calendar Quarter** column, and then click **Insert Column**.</span></span>  
  
     <span data-ttu-id="6ccb7-119">**CalculatedColumn1**という名前の新しい列が、 **Calendar Quarter**列の左側に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-119">A new column named **CalculatedColumn1** is inserted to the left of the **Calendar Quarter** column.</span></span>  
  
4.  <span data-ttu-id="6ccb7-120">テーブルの上にある数式バーに、以下の数式を入力します。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-120">In the formula bar above the table, type the following formula.</span></span> <span data-ttu-id="6ccb7-121">AutoComplete は列やテーブルの完全修飾名を入力するのに役立つとともに､使用可能な関数をすべて一覧表示します｡</span><span class="sxs-lookup"><span data-stu-id="6ccb7-121">AutoComplete helps you type the fully qualified names of columns and tables, and lists the functions that are available.</span></span>  
  
     `=RIGHT(" " & FORMAT([Month],"#0"), 2) & " - " & [Month Name]`  
  
     <span data-ttu-id="6ccb7-122">数式の入力が終了したら、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-122">When you have finished building the formula, press ENTER.</span></span>  
  
     <span data-ttu-id="6ccb7-123">計算列のすべての行に値が入力されます｡</span><span class="sxs-lookup"><span data-stu-id="6ccb7-123">Values are then populated for all the rows in the calculated column.</span></span> <span data-ttu-id="6ccb7-124">テーブルを下方向にスクロールすると､この列の各行のデータに基づいて､行にさまざまな値が設定さていることが分かります｡</span><span class="sxs-lookup"><span data-stu-id="6ccb7-124">If you scroll down through the table, you will see that rows can have different values for this column, based on the data that is in each row.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6ccb7-125">エラーが返された場合は、数式内の列名が、「 [レッスン 3: 列名の変更](rename-columns.md)」で変更した列名と一致していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-125">If you receive an error, verify the column names in the formula match the column names you changed in [Lesson 3: Rename Columns](rename-columns.md).</span></span>  
  
5.  <span data-ttu-id="6ccb7-126">この列の名前をに変更 `Month Calendar` します。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-126">Rename this column to `Month Calendar`.</span></span>  
  
 <span data-ttu-id="6ccb7-127">Month Calendar 計算列は、Month の並べ替え可能な名前を提供します。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-127">The Month Calendar calculated column provides a sortable name for Month.</span></span>  
  
#### <a name="create-a-day-of-week-calculated-column-in-the-date-table"></a><span data-ttu-id="6ccb7-128">Date テーブル内に Day of Week 計算列を作成する</span><span class="sxs-lookup"><span data-stu-id="6ccb7-128">Create a Day of Week calculated column in the Date table</span></span>  
  
1.  <span data-ttu-id="6ccb7-129">**Date** テーブルがアクティブな状態のままで、 **[列]** メニューをクリックし、 **[列の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-129">With the **Date** table still active, click on the **Column** menu, and then click **Add Column**.</span></span>  
  
     <span data-ttu-id="6ccb7-130">新しい列がテーブルの右端に追加されます。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-130">A new column is added to the far right of the table</span></span>  
  
2.  <span data-ttu-id="6ccb7-131">数式バーに次の式を入力します｡</span><span class="sxs-lookup"><span data-stu-id="6ccb7-131">In the formula bar, type the following formula:</span></span>  
  
     `=RIGHT(" " & FORMAT([Day Number Of Week],"#0"), 2) & " - " & [Day Name]`  
  
     <span data-ttu-id="6ccb7-132">数式の入力が終了したら、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-132">When you have finished building the formula, press ENTER.</span></span>  
  
3.  <span data-ttu-id="6ccb7-133">列の名前をに変更 `Day of Week` します。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-133">Rename the column to `Day of Week`.</span></span>  
  
4.  <span data-ttu-id="6ccb7-134">列見出しをクリックし、列を **Day Name** 列と **Day of Month** 列の間にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-134">Click on the column heading, and then drag the column between the **Day Name** column and the **Day of Month** column.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="6ccb7-135">テーブル内の列を移動することで、列が参照しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-135">Moving columns in your table makes it easier to navigate.</span></span>  
  
 <span data-ttu-id="6ccb7-136">Day of Week 計算列では、曜日を表す、並べ替え可能な名前が提供されます。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-136">The Day of Week calculated column provides a sortable name for the day of week.</span></span>  
  
#### <a name="create-a-product-subcategory-name-calculated-column-in-the-product-table"></a><span data-ttu-id="6ccb7-137">Product テーブル内に Product Subcategory Name 計算列を作成する</span><span class="sxs-lookup"><span data-stu-id="6ccb7-137">Create a Product Subcategory Name calculated column in the Product table</span></span>  
  
1.  <span data-ttu-id="6ccb7-138">モデル デザイナーで、 **Product** テーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-138">In the model designer, select the **Product** table.</span></span>  
  
2.  <span data-ttu-id="6ccb7-139">テーブルの右端までスクロールします。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-139">Scroll to the far right of the table.</span></span> <span data-ttu-id="6ccb7-140">右端の列名が **Add Column** (斜体) になっています｡この列の見出しをクリックします｡</span><span class="sxs-lookup"><span data-stu-id="6ccb7-140">Notice the right-most column is named **Add Column** (italicized), click the column heading.</span></span>  
  
3.  <span data-ttu-id="6ccb7-141">数式バーに次の式を入力します｡</span><span class="sxs-lookup"><span data-stu-id="6ccb7-141">In the formula bar, type the following formula.</span></span>  
  
     `=RELATED('Product Subcategory'[Product Subcategory Name])`  
  
     <span data-ttu-id="6ccb7-142">数式の入力が終了したら、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-142">When you have finished building the formula, press ENTER.</span></span>  
  
4.  <span data-ttu-id="6ccb7-143">列の名前をに変更 `Product Subcategory Name` します。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-143">Rename the column to `Product Subcategory Name`.</span></span>  
  
 <span data-ttu-id="6ccb7-144">Product Subcategory Name 計算列は、Product テーブル内に、Product Subcategory テーブルの Product Subcategory Name 列のデータを含んだ階層を作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-144">The Product Subcategory Name calculated column is used to create a hierarchy in the Product table which includes data from the Product Subcategory Name column in the Product Subcategory table.</span></span> <span data-ttu-id="6ccb7-145">階層が複数のテーブルにまたがることはできません｡</span><span class="sxs-lookup"><span data-stu-id="6ccb7-145">Hierarchies cannot span more than one table.</span></span> <span data-ttu-id="6ccb7-146">階層の作成は、この後のレッスン 7 で行います。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-146">You will create hierarchies later in Lesson 7.</span></span>  
  
#### <a name="create-a-product-category-name-calculated-column-in-the-product-table"></a><span data-ttu-id="6ccb7-147">Product テーブル内に Product Category Name 計算列を作成する</span><span class="sxs-lookup"><span data-stu-id="6ccb7-147">Create a Product Category Name calculated column in the Product table</span></span>  
  
1.  <span data-ttu-id="6ccb7-148">**Product** テーブルがアクティブな状態のままで、 **[列]** メニューをクリックし、 **[列の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-148">With the **Product** table still active, click the **Column** menu, and then click **Add Column**.</span></span>  
  
2.  <span data-ttu-id="6ccb7-149">数式バーに次の式を入力します｡</span><span class="sxs-lookup"><span data-stu-id="6ccb7-149">In the formula bar, type the following formula:</span></span>  
  
     `=RELATED('Product Category'[Product Category Name])`  
  
     <span data-ttu-id="6ccb7-150">数式の入力が終了したら、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-150">When you have finished building the formula, press ENTER.</span></span>  
  
3.  <span data-ttu-id="6ccb7-151">列の名前をに変更 `Product Category Name` します。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-151">Rename the column to `Product Category Name`.</span></span>  
  
 <span data-ttu-id="6ccb7-152">Product Category Name 計算列は、Product テーブル内に、Product Category テーブルの Product Category Name 列のデータを含んだ階層を作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-152">The Product Category Name calculated column is used to create a hierarchy in the Product table which includes data from the Product Category Name column in the Product Category table.</span></span> <span data-ttu-id="6ccb7-153">階層が複数のテーブルにまたがることはできません｡</span><span class="sxs-lookup"><span data-stu-id="6ccb7-153">Hierarchies cannot span more than one table.</span></span>  
  
#### <a name="create-a-margin-calculated-column-in-the-internet-sales-table"></a><span data-ttu-id="6ccb7-154">Internet Sales テーブル内に Margin 計算列を作成する</span><span class="sxs-lookup"><span data-stu-id="6ccb7-154">Create a Margin calculated column in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="6ccb7-155">モデル デザイナーで、 **[Internet Sales]** テーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-155">In the model designer, select the **Internet Sales** table.</span></span>  
  
2.  <span data-ttu-id="6ccb7-156">新しい列を追加します。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-156">Add a new column.</span></span>  
  
3.  <span data-ttu-id="6ccb7-157">数式バーに次の式を入力します｡</span><span class="sxs-lookup"><span data-stu-id="6ccb7-157">In the formula bar, type the following formula:</span></span>  
  
     `=[Sales Amount]-[Total Product Cost]`  
  
     <span data-ttu-id="6ccb7-158">数式の入力が終了したら、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-158">When you have finished building the formula, press ENTER.</span></span>  
  
4.  <span data-ttu-id="6ccb7-159">列の名前をに変更 `Margin` します。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-159">Rename the column to `Margin`.</span></span>  
  
5.  <span data-ttu-id="6ccb7-160">列を、 **Sales Amount** 列と **Tax Amt** 列の間にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-160">Drag the column between the **Sales Amount** column and the **Tax Amt** column.</span></span>  
  
 <span data-ttu-id="6ccb7-161">Margin 計算列は、各 (製品) 行の利益率を分析するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-161">The Margin calculated column is used to analyze profit margins for each (product) row.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="6ccb7-162">次の手順</span><span class="sxs-lookup"><span data-stu-id="6ccb7-162">Next Step</span></span>  
 <span data-ttu-id="6ccb7-163">このチュートリアルを続行するには、次のレッスン「 [レッスン 7: メジャーの作成](lesson-6-create-measures.md)」に進んでください。</span><span class="sxs-lookup"><span data-stu-id="6ccb7-163">To continue this lesson, go to the next lesson: [Lesson 7: Create Measures](lesson-6-create-measures.md).</span></span>  
  
  
