---
title: 'レッスン 7: メジャーを作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 01bd2ad7-09b7-49ae-ad80-83f25da301aa
author: minewiskan
ms.author: owend
ms.openlocfilehash: d89ea5c847276c7a34b4fc800d8bed7b9cd8ad34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639739"
---
# <a name="lesson-7-create-measures"></a><span data-ttu-id="f61b0-102">レッスン 7: メジャーを作成する</span><span class="sxs-lookup"><span data-stu-id="f61b0-102">Lesson 7: Create Measures</span></span>
  <span data-ttu-id="f61b0-103">このレッスンでは、モデルに含められるメジャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="f61b0-103">In this lesson, you will create measures to be included in your model.</span></span> <span data-ttu-id="f61b0-104">前のレッスンで作成した計算列と同様、メジャーは、基本的には、DAX 数式を使用して作成される計算です。</span><span class="sxs-lookup"><span data-stu-id="f61b0-104">Similar to the calculated columns you created in the previous lesson, a measure is essentially a calculation created using a DAX formula.</span></span> <span data-ttu-id="f61b0-105">ただし、計算列とは違い、メジャーはユーザーが選択した " *フィルター*" に基づいて評価されます (たとえば、PivotTable 内の行ラベル フィールドに追加された特定の列やスライサーなど)。</span><span class="sxs-lookup"><span data-stu-id="f61b0-105">However, unlike calculated columns, measures are evaluated based on a user selected *filter*; for example, a particular column or slicer added to the Row Labels field in a PivotTable.</span></span>   <span data-ttu-id="f61b0-106">フィルター内の各セルの値は､適用されたメジャーによって求められます｡</span><span class="sxs-lookup"><span data-stu-id="f61b0-106">A value for each cell in the filter is then calculated by the applied measure.</span></span> <span data-ttu-id="f61b0-107">メジャーは強力で柔軟な計算なので、ほとんどすべてのテーブル モデルに含めて、数値データに対する動的な計算を実行できます。</span><span class="sxs-lookup"><span data-stu-id="f61b0-107">Measures are powerful, flexible calculations that you will want to include in almost all tabular models, to perform dynamic calculations on numerical data.</span></span> <span data-ttu-id="f61b0-108">詳細については、「[メジャー (SSAS テーブル)](tabular-models/measures-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f61b0-108">To learn more, see [Measures &#40;SSAS Tabular&#41;](tabular-models/measures-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="f61b0-109">メジャーを作成するには、メジャー グリッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f61b0-109">To create measures, you will use the Measure Grid.</span></span> <span data-ttu-id="f61b0-110">既定では、各テーブルに空のメジャー グリッドがあります。ただし、通常はすべてのテーブルにメジャーを作成することはありません。</span><span class="sxs-lookup"><span data-stu-id="f61b0-110">By default, each table has an empty measure grid; however, you typically will not create measures for every table.</span></span> <span data-ttu-id="f61b0-111">メジャー グリッドは、モデル デザイナーのデータ ビューで、テーブルの下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f61b0-111">The Measure Grid appears below a table in the model designer when in Data View.</span></span> <span data-ttu-id="f61b0-112">テーブルのメジャー グリッドを非表示または表示するには､**[テーブル]** メニューをクリックし､**[Show Measure Grid]** をクリックします｡</span><span class="sxs-lookup"><span data-stu-id="f61b0-112">To hide or show the measure grid for a table, click the **Table** menu, and then click **Show Measure Grid**.</span></span>  
  
 <span data-ttu-id="f61b0-113">メジャーを作成するには、メジャー グリッド内で空のセルをクリックし、数式バーに DAX 数式を入力します。</span><span class="sxs-lookup"><span data-stu-id="f61b0-113">You can create a measure by clicking on an empty cell in the measure grid, and then typing a DAX formula in the formula bar.</span></span> <span data-ttu-id="f61b0-114">Enter キーを押して式の入力を完了すると、そのセルにメジャーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f61b0-114">When you click ENTER to complete the formula, the measure will then appear in the cell.</span></span> <span data-ttu-id="f61b0-115">またメジャーは､標準の集計関数を使用して作成することもできます｡このためには､列をクリックし､ツールバー上の [AutoSum] ボタン (**∑**) をクリックします｡</span><span class="sxs-lookup"><span data-stu-id="f61b0-115">You can also create measures using a standard aggregation function by clicking on a column, and then clicking on the AutoSum button (**∑**) on the toolbar.</span></span> <span data-ttu-id="f61b0-116">オート SUM 機能を使用して作成したメジャーは、その列のすぐ下のメジャー グリッド セルに表示されますが、必要に応じて移動できます。</span><span class="sxs-lookup"><span data-stu-id="f61b0-116">Measures created using the AutoSum feature will appear in the measure grid cell directly beneath the column, but can be moved if necessary.</span></span>  
  
 <span data-ttu-id="f61b0-117">このレッスンでは、数式バーに DAX 数式を入力する方法と、オート SUM 機能を使用する方法の両方でメジャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="f61b0-117">In this lesson, you will create measures by both entering a DAX formula in the formula bar and by using the AutoSum feature.</span></span>  
  
 <span data-ttu-id="f61b0-118">このレッスンの推定所要時間: **30 分**</span><span class="sxs-lookup"><span data-stu-id="f61b0-118">Estimated time to complete this lesson: **30 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f61b0-119">前提条件</span><span class="sxs-lookup"><span data-stu-id="f61b0-119">Prerequisites</span></span>  
 <span data-ttu-id="f61b0-120">このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f61b0-120">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="f61b0-121">このレッスンの実習を行う前に、前のレッスン「 [レッスン 6: 計算列の作成](lesson-5-create-calculated-columns.md)」を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="f61b0-121">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 6: Create Calculated Columns](lesson-5-create-calculated-columns.md).</span></span>  
  
## <a name="create-measures"></a><span data-ttu-id="f61b0-122">メジャーを作成する</span><span class="sxs-lookup"><span data-stu-id="f61b0-122">Create Measures</span></span>  
  
#### <a name="to-create-a-days-current-quarter-to-date-measure-in-the-date-table"></a><span data-ttu-id="f61b0-123">Date テーブル内に Days Current Quarter to Date メジャーを作成するには</span><span class="sxs-lookup"><span data-stu-id="f61b0-123">To create a Days Current Quarter to Date measure in the Date table</span></span>  
  
1.  <span data-ttu-id="f61b0-124">モデルデザイナーで、 **Date**テーブルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f61b0-124">In the model designer, click the **Date** table.</span></span>  
  
2.  <span data-ttu-id="f61b0-125">テーブルの下に空のメジャー グリッドが表示されていない場合は、 **[テーブル]** メニューをクリックし、 **[メジャー グリッドの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f61b0-125">If an empty measure grid does not already appear beneath the table, click on the **Table** menu, and then click **Show Measure Grid**.</span></span>  
  
3.  <span data-ttu-id="f61b0-126">メジャー グリッドの左上の空のセルをクリックします｡</span><span class="sxs-lookup"><span data-stu-id="f61b0-126">In the measure grid, click the top-left empty cell.</span></span>  
  
4.  <span data-ttu-id="f61b0-127">テーブルの上の数式バーに次の式を入力します｡</span><span class="sxs-lookup"><span data-stu-id="f61b0-127">In the formula bar, above the table, type the following formula:</span></span>  
  
     `=COUNTROWS( DATESQTD( 'Date'[Date]))`  
  
     <span data-ttu-id="f61b0-128">数式の入力が終了したら、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f61b0-128">When you have finished building the formula, press ENTER.</span></span>  
  
     <span data-ttu-id="f61b0-129">左上のセルにメジャー名 ( **measure 1**) が含まれ、その後に結果**30**が表示されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f61b0-129">Notice the top-left cell now contains a measure name, **Measure 1**, followed by the result, **30**.</span></span> <span data-ttu-id="f61b0-130">メジャー名は、数式バーの数式の前にも表示されます。</span><span class="sxs-lookup"><span data-stu-id="f61b0-130">The measure name also precedes the formula in the formula bar.</span></span>  
  
5.  <span data-ttu-id="f61b0-131">メジャーの名前を変更するには、数式バーで名前 ( **measure 1**) を強調表示し、「」と入力して `Days Current Quarter to Date` 、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f61b0-131">To rename the measure, in the formula bar, highlight the name, **Measure  1**, then type `Days Current Quarter to Date`, and then press ENTER.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="f61b0-132">数式バーで数式を入力する際には、最初にメジャー名を入力し、続けてコロン (:)、スペース、数式の順に入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="f61b0-132">When typing a formula in the formula bar, you can also first type the measure name followed by a colon (:), followed by a space, and then followed by the formula.</span></span> <span data-ttu-id="f61b0-133">この方法を使用すれば、メジャー名を変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f61b0-133">Using this method, you do not have to rename the measure.</span></span>  
  
#### <a name="to-create-a-days-in-current-quarter-measure-in-the-date-table"></a><span data-ttu-id="f61b0-134">Date テーブル内に Days in Current Quarter メジャーを作成するには</span><span class="sxs-lookup"><span data-stu-id="f61b0-134">To create a Days in Current Quarter measure in the Date table</span></span>  
  
1.  <span data-ttu-id="f61b0-135">モデル デザイナー内の **Date** テーブルをアクティブな状態にしたまま、メジャー グリッドで、先ほど作成したメジャーの下の空のセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f61b0-135">With the **Date** table still active in the model designer, in the measure grid, click the empty cell below the measure you just created.</span></span>  
  
2.  <span data-ttu-id="f61b0-136">数式バーに次の式を入力します｡</span><span class="sxs-lookup"><span data-stu-id="f61b0-136">In the formula bar, type the following formula:</span></span>  
  
     `Days in Current Quarter :=COUNTROWS( DATESBETWEEN( 'Date'[Date], STARTOFQUARTER( LASTDATE('Date'[Date])), ENDOFQUARTER('Date'[Date])))`  
  
     <span data-ttu-id="f61b0-137">この式では、最初にメジャー名を入力し、続けてコロン (:) を入力します。</span><span class="sxs-lookup"><span data-stu-id="f61b0-137">Notice in this formula you first included the measure name followed by a colon (:).</span></span>  
  
     <span data-ttu-id="f61b0-138">数式の入力が終了したら、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f61b0-138">When you have finished building the formula, press ENTER.</span></span>  
  
 <span data-ttu-id="f61b0-139">未完了の期間と前の期間との間に比較率を作成する場合、数式では、経過した期間の比率を考慮に入れて、それを前の期間内の同じ比率と比較する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f61b0-139">When creating a comparison ratio between one incomplete period and the previous period; the formula must take into account the proportion of the period that has elapsed, and compare it to the same proportion in the previous period.</span></span> <span data-ttu-id="f61b0-140">この場合は、[Days Current Quarter to Date]/[Days in Current Quarter] とすることで、現行期間内の経過比率を割り出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f61b0-140">In this case, [Days Current Quarter to Date]/[Days in Current Quarter] gives the proportion elapsed in the current period.</span></span>  
  
#### <a name="to-create-an-internet-distinct-count-sales-order-measure-in-the-internet-sales-table"></a><span data-ttu-id="f61b0-141">Internet Sales テーブル内に Internet Distinct Count Sales Order メジャーを作成するには</span><span class="sxs-lookup"><span data-stu-id="f61b0-141">To create an Internet Distinct Count Sales Order measure in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="f61b0-142">モデル デザイナーで、[ **Internet Sales** ] テーブル (タブ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f61b0-142">In the model designer, click the **Internet Sales** table (tab).</span></span>  
  
     <span data-ttu-id="f61b0-143">テーブルの下にメジャー グリッドが表示されていない場合は、 **[Internet Sales]** テーブル (タブ) を右クリックし、 **[メジャー グリッドの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f61b0-143">If the measure grid does not already appear, right-click the **Internet Sales** table (tab), and then click **Show Measure Grid**.</span></span>  
  
2.  <span data-ttu-id="f61b0-144">**[Sales Order Number]** 列見出しをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f61b0-144">Click on the **Sales Order Number** column heading.</span></span>  
  
3.  <span data-ttu-id="f61b0-145">ツールバーで 「AutoSum」\ (**∑**) ボタンの下向き矢印をクリックし､**DistinctCount** を選択します｡</span><span class="sxs-lookup"><span data-stu-id="f61b0-145">On the toolbar, click the down-arrow next to the AutoSum (**∑**) button, and then select **DistinctCount**.</span></span>  
  
     <span data-ttu-id="f61b0-146">AutoSum 機能により､DistinctCount 標準集計式を使用して選択された列のメジャーが自動的に作成されます｡</span><span class="sxs-lookup"><span data-stu-id="f61b0-146">The AutoSum feature automatically creates a measure for the selected column using the DistinctCount standard aggregation formula.</span></span>  
  
     <span data-ttu-id="f61b0-147">メジャー グリッド内の対象列のすぐ下のセルに、メジャー名 ( **Distinct Count Sales Order Number**) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f61b0-147">Notice the top cell below the column in the measure grid now contains a measure name, **Distinct Count Sales Order Number**.</span></span> <span data-ttu-id="f61b0-148">オート SUM 機能を使用して作成したメジャーは、メジャー グリッド内で、関連付けられた列のすぐ下のセルに自動的に配置されます。</span><span class="sxs-lookup"><span data-stu-id="f61b0-148">Measures created using the AutoSum feature are automatically placed in the top-most cell in the measure grid below the associated column.</span></span>  
  
4.  <span data-ttu-id="f61b0-149">メジャー グリッドで新しいメジャーをクリックし、 **[プロパティ]** ウィンドウの **[メジャー名]** に「 **Internet Distinct Count Sales Order**」と入力して名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="f61b0-149">In the measure grid, click the new measure, and then in the **Properties** window, in **Measure Name**, rename the measure to **Internet Distinct Count Sales Order**.</span></span>  
  
#### <a name="to-create-additional-measures-in-the-internet-sales-table"></a><span data-ttu-id="f61b0-150">Internet Sales テーブル内に追加のメジャーを作成するには</span><span class="sxs-lookup"><span data-stu-id="f61b0-150">To create additional measures in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="f61b0-151">AutoSum 機能を使用して次のメジャーを作成し､名前を指定します｡</span><span class="sxs-lookup"><span data-stu-id="f61b0-151">By using the AutoSum feature, create and name the following measures:</span></span>  
  
    |<span data-ttu-id="f61b0-152">[メジャー名]</span><span class="sxs-lookup"><span data-stu-id="f61b0-152">Measure Name</span></span>|<span data-ttu-id="f61b0-153">列</span><span class="sxs-lookup"><span data-stu-id="f61b0-153">Column</span></span>|<span data-ttu-id="f61b0-154">オート SUM (∑)</span><span class="sxs-lookup"><span data-stu-id="f61b0-154">AutoSum (∑)</span></span>|<span data-ttu-id="f61b0-155">計算式</span><span class="sxs-lookup"><span data-stu-id="f61b0-155">Formula</span></span>|  
    |------------------|------------|-------------------|-------------|  
    |<span data-ttu-id="f61b0-156">Internet Order Lines Count</span><span class="sxs-lookup"><span data-stu-id="f61b0-156">Internet Order Lines Count</span></span>|<span data-ttu-id="f61b0-157">Sales Order Line Number</span><span class="sxs-lookup"><span data-stu-id="f61b0-157">Sales Order Line Number</span></span>|<span data-ttu-id="f61b0-158">Count</span><span class="sxs-lookup"><span data-stu-id="f61b0-158">Count</span></span>|<span data-ttu-id="f61b0-159">=COUNT([Sales Order Line Number])</span><span class="sxs-lookup"><span data-stu-id="f61b0-159">=COUNT([Sales Order Line Number])</span></span>|  
    |<span data-ttu-id="f61b0-160">Internet Total Units</span><span class="sxs-lookup"><span data-stu-id="f61b0-160">Internet Total Units</span></span>|<span data-ttu-id="f61b0-161">Order Quantity</span><span class="sxs-lookup"><span data-stu-id="f61b0-161">Order Quantity</span></span>|<span data-ttu-id="f61b0-162">SUM</span><span class="sxs-lookup"><span data-stu-id="f61b0-162">Sum</span></span>|<span data-ttu-id="f61b0-163">=SUM([Order Quantity])</span><span class="sxs-lookup"><span data-stu-id="f61b0-163">=SUM([Order Quantity])</span></span>|  
    |<span data-ttu-id="f61b0-164">Internet Total Discount Amount</span><span class="sxs-lookup"><span data-stu-id="f61b0-164">Internet Total Discount Amount</span></span>|<span data-ttu-id="f61b0-165">Discount Amount</span><span class="sxs-lookup"><span data-stu-id="f61b0-165">Discount Amount</span></span>|<span data-ttu-id="f61b0-166">SUM</span><span class="sxs-lookup"><span data-stu-id="f61b0-166">Sum</span></span>|<span data-ttu-id="f61b0-167">=SUM([Discount Amount])</span><span class="sxs-lookup"><span data-stu-id="f61b0-167">=SUM([Discount Amount])</span></span>|  
    |<span data-ttu-id="f61b0-168">Internet Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="f61b0-168">Internet Total Product Cost</span></span>|<span data-ttu-id="f61b0-169">Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="f61b0-169">Total Product Cost</span></span>|<span data-ttu-id="f61b0-170">SUM</span><span class="sxs-lookup"><span data-stu-id="f61b0-170">Sum</span></span>|<span data-ttu-id="f61b0-171">=SUM([Total Product Cost])</span><span class="sxs-lookup"><span data-stu-id="f61b0-171">=SUM([Total Product Cost])</span></span>|  
    |<span data-ttu-id="f61b0-172">Internet Total Sales</span><span class="sxs-lookup"><span data-stu-id="f61b0-172">Internet Total Sales</span></span>|<span data-ttu-id="f61b0-173">Sales Amount</span><span class="sxs-lookup"><span data-stu-id="f61b0-173">Sales Amount</span></span>|<span data-ttu-id="f61b0-174">SUM</span><span class="sxs-lookup"><span data-stu-id="f61b0-174">Sum</span></span>|<span data-ttu-id="f61b0-175">=SUM([Sales Amount])</span><span class="sxs-lookup"><span data-stu-id="f61b0-175">=SUM([Sales Amount])</span></span>|  
    |<span data-ttu-id="f61b0-176">Internet Total Margin</span><span class="sxs-lookup"><span data-stu-id="f61b0-176">Internet Total Margin</span></span>|<span data-ttu-id="f61b0-177">余白</span><span class="sxs-lookup"><span data-stu-id="f61b0-177">Margin</span></span>|<span data-ttu-id="f61b0-178">SUM</span><span class="sxs-lookup"><span data-stu-id="f61b0-178">Sum</span></span>|<span data-ttu-id="f61b0-179">=SUM([Margin])</span><span class="sxs-lookup"><span data-stu-id="f61b0-179">=SUM([Margin])</span></span>|  
    |<span data-ttu-id="f61b0-180">Internet Total Tax Amt</span><span class="sxs-lookup"><span data-stu-id="f61b0-180">Internet Total Tax Amt</span></span>|<span data-ttu-id="f61b0-181">Tax Amt</span><span class="sxs-lookup"><span data-stu-id="f61b0-181">Tax Amt</span></span>|<span data-ttu-id="f61b0-182">SUM</span><span class="sxs-lookup"><span data-stu-id="f61b0-182">Sum</span></span>|<span data-ttu-id="f61b0-183">=SUM([Tax Amt])</span><span class="sxs-lookup"><span data-stu-id="f61b0-183">=SUM([Tax Amt])</span></span>|  
    |<span data-ttu-id="f61b0-184">Internet Total Freight</span><span class="sxs-lookup"><span data-stu-id="f61b0-184">Internet Total Freight</span></span>|<span data-ttu-id="f61b0-185">運送料</span><span class="sxs-lookup"><span data-stu-id="f61b0-185">Freight</span></span>|<span data-ttu-id="f61b0-186">SUM</span><span class="sxs-lookup"><span data-stu-id="f61b0-186">Sum</span></span>|<span data-ttu-id="f61b0-187">=SUM([Freight])</span><span class="sxs-lookup"><span data-stu-id="f61b0-187">=SUM([Freight])</span></span>|  
  
2.  <span data-ttu-id="f61b0-188">メジャー グリッド内で空のセルをクリックし、数式バーを使用して、次の名前のメジャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="f61b0-188">By clicking on an empty cell in the measure grid, and by using the formula bar, create and name the following measures:</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f61b0-189">メジャーは次の順序のとおりに作成する必要があります (先行するメジャーは後続のメジャー内の数式から参照されるため)。</span><span class="sxs-lookup"><span data-stu-id="f61b0-189">You must create the following measures in order; formulas in later measures refer to earlier measures.</span></span>  
  
    |<span data-ttu-id="f61b0-190">[メジャー名]</span><span class="sxs-lookup"><span data-stu-id="f61b0-190">Measure Name</span></span>|<span data-ttu-id="f61b0-191">計算式</span><span class="sxs-lookup"><span data-stu-id="f61b0-191">Formula</span></span>|  
    |------------------|-------------|  
    |<span data-ttu-id="f61b0-192">Internet Previous Quarter Margin</span><span class="sxs-lookup"><span data-stu-id="f61b0-192">Internet Previous Quarter Margin</span></span>|<span data-ttu-id="f61b0-193">=CALCULATE([Internet Total Margin],PREVIOUSQUARTER('Date'[Date]))</span><span class="sxs-lookup"><span data-stu-id="f61b0-193">=CALCULATE([Internet Total Margin],PREVIOUSQUARTER('Date'[Date]))</span></span>|  
    |<span data-ttu-id="f61b0-194">Internet Current Quarter Margin</span><span class="sxs-lookup"><span data-stu-id="f61b0-194">Internet Current Quarter Margin</span></span>|<span data-ttu-id="f61b0-195">=TOTALQTD([Internet Total Margin],'Date'[Date])</span><span class="sxs-lookup"><span data-stu-id="f61b0-195">=TOTALQTD([Internet Total Margin],'Date'[Date])</span></span>|  
    |<span data-ttu-id="f61b0-196">Internet Previous Quarter Margin Proportion to QTD</span><span class="sxs-lookup"><span data-stu-id="f61b0-196">Internet Previous Quarter Margin Proportion to QTD</span></span>|<span data-ttu-id="f61b0-197">=[Internet Previous Quarter Margin]\*([Days Current Quarter to Date]/[Days In Current Quarter])</span><span class="sxs-lookup"><span data-stu-id="f61b0-197">=[Internet Previous Quarter Margin]\*([Days Current Quarter to Date]/[Days In Current Quarter])</span></span>|  
    |<span data-ttu-id="f61b0-198">Internet Previous Quarter Sales</span><span class="sxs-lookup"><span data-stu-id="f61b0-198">Internet Previous Quarter Sales</span></span>|<span data-ttu-id="f61b0-199">=CALCULATE([Internet Total Sales],PREVIOUSQUARTER('Date'[Date]))</span><span class="sxs-lookup"><span data-stu-id="f61b0-199">=CALCULATE([Internet Total Sales],PREVIOUSQUARTER('Date'[Date]))</span></span>|  
    |<span data-ttu-id="f61b0-200">Internet Current Quarter Sales</span><span class="sxs-lookup"><span data-stu-id="f61b0-200">Internet Current Quarter Sales</span></span>|<span data-ttu-id="f61b0-201">=TOTALQTD([Internet Total Sales],'Date'[Date])</span><span class="sxs-lookup"><span data-stu-id="f61b0-201">=TOTALQTD([Internet Total Sales],'Date'[Date])</span></span>|  
    |<span data-ttu-id="f61b0-202">Internet Previous Quarter Sales Proportion to QTD</span><span class="sxs-lookup"><span data-stu-id="f61b0-202">Internet Previous Quarter Sales Proportion to QTD</span></span>|<span data-ttu-id="f61b0-203">=[Internet Previous Quarter Sales]\*([Days Current Quarter to Date]/[Days In Current Quarter])</span><span class="sxs-lookup"><span data-stu-id="f61b0-203">=[Internet Previous Quarter Sales]\*([Days Current Quarter to Date]/[Days In Current Quarter])</span></span>|  
  
 <span data-ttu-id="f61b0-204">Internet Sales テーブル用に作成されたメジャーは、ユーザー選択のフィルターによって定義された項目に関する重要な財務データ (売上、コスト、利益率など) を分析するためにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="f61b0-204">Measures created for the Internet Sales table can be used to analyze critical financial data such as sales, costs, and profit margin for items defined by the user selected filter.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="f61b0-205">次の手順</span><span class="sxs-lookup"><span data-stu-id="f61b0-205">Next Step</span></span>  
 <span data-ttu-id="f61b0-206">このチュートリアルを続行するには、次のレッスン「 [レッスン 8: 主要業績評価指標の作成](lesson-7-create-key-performance-indicators.md)」に進んでください。</span><span class="sxs-lookup"><span data-stu-id="f61b0-206">To continue this tutorial, go to the next lesson: [Lesson 8: Create Key Performance Indicators](lesson-7-create-key-performance-indicators.md).</span></span>  
  
  
