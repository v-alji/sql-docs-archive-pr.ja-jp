---
title: ピボット変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.pivottrans.f1
helpviewer_keywords:
- Pivot transformation
- normalized data [Integration Services]
- PivotUsage property
- datasets [Integration Services], normalized data
- less normalized data set [Integration Services]
ms.assetid: 55f5db6e-6777-435f-8a06-b68c129f8437
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 43bdc5be709ea00d4be4601f52c38e96fe3f1ce4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743410"
---
# <a name="pivot-transformation"></a><span data-ttu-id="20d0b-102">ピボット変換</span><span class="sxs-lookup"><span data-stu-id="20d0b-102">Pivot Transformation</span></span>
  <span data-ttu-id="20d0b-103">ピボット変換は、入力データを列の値でピボットすることにより、正規化されたデータセットを、正規化の度合は低いがより圧縮された形に設定します。</span><span class="sxs-lookup"><span data-stu-id="20d0b-103">The Pivot transformation makes a normalized data set into a less normalized but more compact version by pivoting the input data on a column value.</span></span> <span data-ttu-id="20d0b-104">たとえば、顧客名、製品、購入した数量を一覧表示する、正規化された **Orders** データセットには、通常、複数の製品を購入した顧客に対して複数の行があり、その顧客に対する各行には製品ごとに注文の詳細が示されています。</span><span class="sxs-lookup"><span data-stu-id="20d0b-104">For example, a normalized **Orders** data set that lists customer name, product, and quantity purchased typically has multiple rows for any customer who purchased multiple products, with each row for that customer showing order details for a different product.</span></span> <span data-ttu-id="20d0b-105">ピボット変換では、データセットを製品列でピボットすることにより、各顧客のデータセットを単一行で出力できます。</span><span class="sxs-lookup"><span data-stu-id="20d0b-105">By pivoting the data set on the product column, the Pivot transformation can output a data set with a single row per customer.</span></span> <span data-ttu-id="20d0b-106">その行では顧客のすべての購入情報が一覧となり、列名に製品名が表示され、製品列の値には購入した数量が表示されます。</span><span class="sxs-lookup"><span data-stu-id="20d0b-106">That single row lists all the purchases by the customer, with the product names shown as column names, and the quantity shown as a value in the product column.</span></span> <span data-ttu-id="20d0b-107">すべての顧客がすべての製品を購入するわけではないので、多くの列に NULL 値が含まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="20d0b-107">Because not every customer purchases every product, many columns may contain null values.</span></span>  
  
 <span data-ttu-id="20d0b-108">データセットがピボットされる場合、ピボット処理において入力列はさまざまに機能します。</span><span class="sxs-lookup"><span data-stu-id="20d0b-108">When a dataset is pivoted, input columns perform different roles in the pivoting process.</span></span> <span data-ttu-id="20d0b-109">列が果たす役割には、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="20d0b-109">A column can participate in the following ways:</span></span>  
  
-   <span data-ttu-id="20d0b-110">列は、変更されずに出力に渡されます。</span><span class="sxs-lookup"><span data-stu-id="20d0b-110">The column is passed through unchanged to the output.</span></span> <span data-ttu-id="20d0b-111">入力行は 1 つの出力行のみに渡される場合が多いため、変換により列の最初の入力値のみがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="20d0b-111">Because many input rows can result only in one output row, the transformation copies only the first input value for the column.</span></span>  
  
-   <span data-ttu-id="20d0b-112">列は、レコードのセットを識別するためのキーまたはキーの一部として機能します。</span><span class="sxs-lookup"><span data-stu-id="20d0b-112">The column acts as the key or part of the key that identifies a set of records.</span></span>  
  
-   <span data-ttu-id="20d0b-113">列は、ピボットを定義します。</span><span class="sxs-lookup"><span data-stu-id="20d0b-113">The column defines the pivot.</span></span> <span data-ttu-id="20d0b-114">この列の値は、ピボットされたデータセットの列に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="20d0b-114">The values in this column are associated with columns in the pivoted dataset.</span></span>  
  
-   <span data-ttu-id="20d0b-115">列には、ピボットにより作成される列に配置する値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="20d0b-115">The column contains values that are placed in the columns that the pivot creates.</span></span>  
  
 <span data-ttu-id="20d0b-116">この変換は、1 つの入力、1 つの標準出力、および 1 つのエラー出力をとります。</span><span class="sxs-lookup"><span data-stu-id="20d0b-116">This transformation has one input, one regular output, and one error output.</span></span>  
  
## <a name="sort-and-duplicate-rows"></a><span data-ttu-id="20d0b-117">並べ替えおよび重複する行</span><span class="sxs-lookup"><span data-stu-id="20d0b-117">Sort and Duplicate Rows</span></span>  
 <span data-ttu-id="20d0b-118">データを効率よくピボットする、つまり、出力データセットで作成されるレコード数をできるだけ少なくするには、入力データをピボット列で並べ替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="20d0b-118">To pivot data efficiently, which means creating as few records in the output dataset as possible, the input data must be sorted on the pivot column.</span></span> <span data-ttu-id="20d0b-119">データが並べ替えられていない場合、ピボットの変換では、設定キーの各値に対して複数のレコードが生成されることがあります。ここで設定キーとは、設定されたメンバーシップを定義する列のことです。</span><span class="sxs-lookup"><span data-stu-id="20d0b-119">If the data is not sorted, the Pivot transformation might generate multiple records for each value in the set key, which is the column that defines set membership.</span></span> <span data-ttu-id="20d0b-120">たとえば、データセットを **Name** 列でピボットする際に名前が並べ替えられていない場合、出力データセットには、各顧客の行が複数含まれることがあります。これは、 **Name** 列の値が変わるたびにピボットが発生するためです。</span><span class="sxs-lookup"><span data-stu-id="20d0b-120">For example, if a dataset is pivoted on a **Name** column but the names are not sorted, the output dataset could have more than one row for each customer, because a pivot occurs every time that the value in **Name** changes.</span></span>  
  
 <span data-ttu-id="20d0b-121">入力データには重複する行が含まれる場合があります。重複する行があると、ピボット変換は失敗します。</span><span class="sxs-lookup"><span data-stu-id="20d0b-121">The input data might contain duplicate rows, which will cause the Pivot transformation to fail.</span></span> <span data-ttu-id="20d0b-122">"重複する行" とは、設定キー列およびピボット列に同じ値を持つ行のことです。</span><span class="sxs-lookup"><span data-stu-id="20d0b-122">"Duplicate rows" means rows that have the same values in the set key columns and the pivot columns.</span></span> <span data-ttu-id="20d0b-123">エラーを回避するには、エラー行をエラー出力にリダイレクトするように変換を構成するか、重複する行が存在しないように値を事前に集計しておくことができます。</span><span class="sxs-lookup"><span data-stu-id="20d0b-123">To avoid failure, you can either configure the transformation to redirect error rows to an error output or you can pre-aggregate values to ensure there are no duplicate rows.</span></span>  
  
##  <a name="options-in-the-pivot-dialog-box"></a><a name="options"></a> <span data-ttu-id="20d0b-124">[ピボット] ダイアログ ボックスのオプション</span><span class="sxs-lookup"><span data-stu-id="20d0b-124">Options in the Pivot Dialog Box</span></span>  
 <span data-ttu-id="20d0b-125">ピボット操作を構成するには、 **[ピボット]** ダイアログ ボックスのオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="20d0b-125">You configure the pivot operation by setting the options in the **Pivot** dialog box.</span></span> <span data-ttu-id="20d0b-126">**[ピボット]** ダイアログ ボックスを開くには、 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]でパッケージにピボット変換を追加し、コンポーネントを右クリックして **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20d0b-126">To open the **Pivot** dialog box, add the Pivot transformation to the package in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], and then right-click the component and click **Edit**.</span></span>  
  
 <span data-ttu-id="20d0b-127">**[ピボット]** ダイアログ ボックスのオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="20d0b-127">The following list describes the options in the **Pivot** dialog box.</span></span>  
  
 <span data-ttu-id="20d0b-128">**ピボット キー**</span><span class="sxs-lookup"><span data-stu-id="20d0b-128">**Pivot Key**</span></span>  
 <span data-ttu-id="20d0b-129">テーブルの先頭行 (ヘッダー行) の値に使用する列を指定します。</span><span class="sxs-lookup"><span data-stu-id="20d0b-129">Specifies the column to use for values across the top row (header row) of the table.</span></span>  
  
 <span data-ttu-id="20d0b-130">**設定キー**</span><span class="sxs-lookup"><span data-stu-id="20d0b-130">**Set Key**</span></span>  
 <span data-ttu-id="20d0b-131">テーブルの左の列の値に使用する列を指定します。</span><span class="sxs-lookup"><span data-stu-id="20d0b-131">Specifies the column to use for values in the left column of the table.</span></span> <span data-ttu-id="20d0b-132">入力日はこの列で並べ替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="20d0b-132">The input date must be sorted on this column.</span></span>  
  
 <span data-ttu-id="20d0b-133">**ピボット値**</span><span class="sxs-lookup"><span data-stu-id="20d0b-133">**Pivot Value**</span></span>  
 <span data-ttu-id="20d0b-134">ヘッダー行と左の列の値以外のテーブル値に使用する列を指定します。</span><span class="sxs-lookup"><span data-stu-id="20d0b-134">Specifies the column to use for the table values, other than the values in the header row and the left column.</span></span>  
  
 <span data-ttu-id="20d0b-135">**一致しないピボット キー値を無視して DataFlow の実行後に報告する**</span><span class="sxs-lookup"><span data-stu-id="20d0b-135">**Ignore un-matched Pivot Key values and report them after DataFlow execution**</span></span>  
 <span data-ttu-id="20d0b-136">パッケージが実行されるときに、 **[ピボット キー]** 列に不明な値が含まれている行を無視して、ピボット キーの値をすべてログ メッセージに出力するようにピボット変換を構成するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="20d0b-136">Select this option to configure the Pivot transformation to ignore rows containing unrecognized values in the **Pivot Key** column and to output all of the pivot key values to a log message, when the package is run.</span></span>  
  
 <span data-ttu-id="20d0b-137">`PassThroughUnmatchedPivotKeys` カスタム プロパティを `True` に設定することで、値を出力するように変換を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="20d0b-137">You can also configure the transformation to output the values by setting the `PassThroughUnmatchedPivotKeys` custom property to `True`.</span></span>  
  
 <span data-ttu-id="20d0b-138">**値からピボット出力列を生成**</span><span class="sxs-lookup"><span data-stu-id="20d0b-138">**Generate pivot output columns from values**</span></span>  
 <span data-ttu-id="20d0b-139">ピボット変換によって出力列が値ごとに作成されるようにするには、このボックスにピボット キーの値を入力します。</span><span class="sxs-lookup"><span data-stu-id="20d0b-139">Enter the pivot key values in this box to enable the Pivot transformation to create output columns for each value.</span></span> <span data-ttu-id="20d0b-140">パッケージを実行する前に値を入力するか、または次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="20d0b-140">You can either enter the values prior to running the package, or do the following.</span></span>  
  
1.  <span data-ttu-id="20d0b-141">**[一致しないピボット キー値を無視して DataFlow の実行後に報告する]** オプションを選択し、 **[ピボット]** ダイアログ ボックスの **[OK]** をクリックして、ピボット変換に対する変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="20d0b-141">Select the **Ignore un-matched Pivot Key values and report them after DataFlow execution** option, and then click **OK** in the **Pivot** dialog box to save the changes to the Pivot transformation.</span></span>  
  
2.  <span data-ttu-id="20d0b-142">パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="20d0b-142">Run the package.</span></span>  
  
3.  <span data-ttu-id="20d0b-143">パッケージの実行が成功したら、 **[進行状況]** タブをクリックして、ピボット キーの値を含むピボット変換の情報ログ メッセージを確認します。</span><span class="sxs-lookup"><span data-stu-id="20d0b-143">When the package succeeds, click the **Progress** tab and look for the information log message from the Pivot transformation that contains the pivot key values.</span></span>  
  
4.  <span data-ttu-id="20d0b-144">メッセージを右クリックして、 **[メッセージ テキストのコピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20d0b-144">Right-click the message and click **Copy Message Text**.</span></span>  
  
5.  <span data-ttu-id="20d0b-145">**[デバッグ]** メニューの **[デバッグの停止]** をクリックしてデザイン モードに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="20d0b-145">Click **Stop Debugging** on the **Debug** menu to switch to the design mode.</span></span>  
  
6.  <span data-ttu-id="20d0b-146">ピボット変換を右クリックして、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20d0b-146">Right-click the Pivot transformation, and then click **Edit**.</span></span>  
  
7.  <span data-ttu-id="20d0b-147">**[一致しないピボット キー値を無視して DataFlow の実行後に報告する]** オプションをオフにして、 **[値からピボット出力列を生成]** ボックスに、次の形式を使用してピボット キーの値を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="20d0b-147">Uncheck the **Ignore un-matched Pivot Key values and report them after DataFlow execution** option, and then paste the pivot key values in the **Generate pivot output columns from values** box using the following format.</span></span>  
  
     <span data-ttu-id="20d0b-148">[value1],[value2],[value3]</span><span class="sxs-lookup"><span data-stu-id="20d0b-148">[value1],[value2],[value3]</span></span>  
  
 <span data-ttu-id="20d0b-149">**今すぐに列を生成**</span><span class="sxs-lookup"><span data-stu-id="20d0b-149">**Generate Columns Now**</span></span>  
 <span data-ttu-id="20d0b-150">クリックすると、 **[値からピボット出力列を生成]** ボックスに表示されるピボット キーの値ごとに出力列を作成できます。</span><span class="sxs-lookup"><span data-stu-id="20d0b-150">Click to create an output column for each pivot key value that is listed in the **Generate pivot output columns from values** box.</span></span>  
  
 <span data-ttu-id="20d0b-151">出力列は、 **[既存のピボット出力列]** ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="20d0b-151">The output columns appear in the **Existing pivoted output columns** box.</span></span>  
  
 <span data-ttu-id="20d0b-152">**[既存のピボット出力列]**</span><span class="sxs-lookup"><span data-stu-id="20d0b-152">**Existing pivoted output columns**</span></span>  
 <span data-ttu-id="20d0b-153">ピボット キーの値の出力列が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="20d0b-153">Lists the output columns for the pivot key values</span></span>  
  
 <span data-ttu-id="20d0b-154">次の表は、データが **Year** 列でピボットされる前のデータセットを示しています。</span><span class="sxs-lookup"><span data-stu-id="20d0b-154">The following table shows a data set before the data is pivoted on the **Year** column.</span></span>  
  
|<span data-ttu-id="20d0b-155">年</span><span class="sxs-lookup"><span data-stu-id="20d0b-155">Year</span></span>|<span data-ttu-id="20d0b-156">製品名</span><span class="sxs-lookup"><span data-stu-id="20d0b-156">Product Name</span></span>|<span data-ttu-id="20d0b-157">合計</span><span class="sxs-lookup"><span data-stu-id="20d0b-157">Total</span></span>|  
|----------|------------------|-----------|  
|<span data-ttu-id="20d0b-158">2004</span><span class="sxs-lookup"><span data-stu-id="20d0b-158">2004</span></span>|<span data-ttu-id="20d0b-159">HL Mountain Tire</span><span class="sxs-lookup"><span data-stu-id="20d0b-159">HL Mountain Tire</span></span>|<span data-ttu-id="20d0b-160">1504884.15</span><span class="sxs-lookup"><span data-stu-id="20d0b-160">1504884.15</span></span>|  
|<span data-ttu-id="20d0b-161">2003</span><span class="sxs-lookup"><span data-stu-id="20d0b-161">2003</span></span>|<span data-ttu-id="20d0b-162">Road Tire Tube</span><span class="sxs-lookup"><span data-stu-id="20d0b-162">Road Tire Tube</span></span>|<span data-ttu-id="20d0b-163">35920.50</span><span class="sxs-lookup"><span data-stu-id="20d0b-163">35920.50</span></span>|  
|<span data-ttu-id="20d0b-164">2004</span><span class="sxs-lookup"><span data-stu-id="20d0b-164">2004</span></span>|<span data-ttu-id="20d0b-165">Water Bottle - 30 oz.</span><span class="sxs-lookup"><span data-stu-id="20d0b-165">Water Bottle - 30 oz.</span></span>|<span data-ttu-id="20d0b-166">2805.00</span><span class="sxs-lookup"><span data-stu-id="20d0b-166">2805.00</span></span>|  
|<span data-ttu-id="20d0b-167">2002</span><span class="sxs-lookup"><span data-stu-id="20d0b-167">2002</span></span>|<span data-ttu-id="20d0b-168">Touring Tire</span><span class="sxs-lookup"><span data-stu-id="20d0b-168">Touring Tire</span></span>|<span data-ttu-id="20d0b-169">62364.225</span><span class="sxs-lookup"><span data-stu-id="20d0b-169">62364.225</span></span>|  
  
 <span data-ttu-id="20d0b-170">次の表は、データが **Year** 列でピボットされた後のデータセットを示しています。</span><span class="sxs-lookup"><span data-stu-id="20d0b-170">The following table shows a data set after the data has been pivoted on the **Year** column.</span></span>  
  
||<span data-ttu-id="20d0b-171">2002</span><span class="sxs-lookup"><span data-stu-id="20d0b-171">2002</span></span>|<span data-ttu-id="20d0b-172">2003</span><span class="sxs-lookup"><span data-stu-id="20d0b-172">2003</span></span>|<span data-ttu-id="20d0b-173">2004</span><span class="sxs-lookup"><span data-stu-id="20d0b-173">2004</span></span>|  
|-|----------|----------|----------|  
|<span data-ttu-id="20d0b-174">HL Mountain Tire</span><span class="sxs-lookup"><span data-stu-id="20d0b-174">HL Mountain Tire</span></span>|<span data-ttu-id="20d0b-175">141164.10</span><span class="sxs-lookup"><span data-stu-id="20d0b-175">141164.10</span></span>|<span data-ttu-id="20d0b-176">446297.775</span><span class="sxs-lookup"><span data-stu-id="20d0b-176">446297.775</span></span>|<span data-ttu-id="20d0b-177">1504884.15</span><span class="sxs-lookup"><span data-stu-id="20d0b-177">1504884.15</span></span>|  
|<span data-ttu-id="20d0b-178">Road Tire Tube</span><span class="sxs-lookup"><span data-stu-id="20d0b-178">Road Tire Tube</span></span>|<span data-ttu-id="20d0b-179">3592.05</span><span class="sxs-lookup"><span data-stu-id="20d0b-179">3592.05</span></span>|<span data-ttu-id="20d0b-180">35920.50</span><span class="sxs-lookup"><span data-stu-id="20d0b-180">35920.50</span></span>|<span data-ttu-id="20d0b-181">89801.25</span><span class="sxs-lookup"><span data-stu-id="20d0b-181">89801.25</span></span>|  
|<span data-ttu-id="20d0b-182">Water Bottle - 30 oz.</span><span class="sxs-lookup"><span data-stu-id="20d0b-182">Water Bottle - 30 oz.</span></span>|<span data-ttu-id="20d0b-183">*NULL*</span><span class="sxs-lookup"><span data-stu-id="20d0b-183">*NULL*</span></span>|<span data-ttu-id="20d0b-184">*NULL*</span><span class="sxs-lookup"><span data-stu-id="20d0b-184">*NULL*</span></span>|<span data-ttu-id="20d0b-185">2805.00</span><span class="sxs-lookup"><span data-stu-id="20d0b-185">2805.00</span></span>|  
|<span data-ttu-id="20d0b-186">Touring Tire</span><span class="sxs-lookup"><span data-stu-id="20d0b-186">Touring Tire</span></span>|<span data-ttu-id="20d0b-187">62364.225</span><span class="sxs-lookup"><span data-stu-id="20d0b-187">62364.225</span></span>|<span data-ttu-id="20d0b-188">375051.60</span><span class="sxs-lookup"><span data-stu-id="20d0b-188">375051.60</span></span>|<span data-ttu-id="20d0b-189">1041810.00</span><span class="sxs-lookup"><span data-stu-id="20d0b-189">1041810.00</span></span>|  
  
 <span data-ttu-id="20d0b-190">上記のように、 **Year** 列でデータをピボットするために、 **[ピボット]** ダイアログ ボックスでは次のオプションが設定されます。</span><span class="sxs-lookup"><span data-stu-id="20d0b-190">To pivot the data on the **Year** column, as shown above, the following options are set in the **Pivot** dialog box.</span></span>  
  
-   <span data-ttu-id="20d0b-191">**[ピボット キー]** ボックスでは [Year] が選択されます。</span><span class="sxs-lookup"><span data-stu-id="20d0b-191">Year is selected in the **Pivot Key** list box.</span></span>  
  
-   <span data-ttu-id="20d0b-192">**[設定キー]** ボックスでは [Product Name] が選択されます。</span><span class="sxs-lookup"><span data-stu-id="20d0b-192">Product Name is selected in the **Set Key** list box.</span></span>  
  
-   <span data-ttu-id="20d0b-193">**[ピボット値]** ボックスでは [Total] が選択されます。</span><span class="sxs-lookup"><span data-stu-id="20d0b-193">Total is selected in the **Pivot Value** list box.</span></span>  
  
-   <span data-ttu-id="20d0b-194">**[値からピボット出力列を生成]** ボックスには、次の値が入力されます。</span><span class="sxs-lookup"><span data-stu-id="20d0b-194">The following values are entered in the **Generate pivot output columns from values** box.</span></span>  
  
     <span data-ttu-id="20d0b-195">[2002],[2003],[2004]</span><span class="sxs-lookup"><span data-stu-id="20d0b-195">[2002],[2003],[2004]</span></span>  
  
## <a name="configuration-of-the-pivot-transformation"></a><span data-ttu-id="20d0b-196">ピボット変換の構成</span><span class="sxs-lookup"><span data-stu-id="20d0b-196">Configuration of the Pivot Transformation</span></span>  
 <span data-ttu-id="20d0b-197">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="20d0b-197">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="20d0b-198">**[詳細エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="20d0b-198">For more information about the properties that you can set in the **Advanced Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="20d0b-199">Common Properties</span><span class="sxs-lookup"><span data-stu-id="20d0b-199">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="20d0b-200">変換のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="20d0b-200">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-content"></a><span data-ttu-id="20d0b-201">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="20d0b-201">Related Content</span></span>  
 <span data-ttu-id="20d0b-202">このコンポーネントのプロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20d0b-202">For information about how to set the properties of this component, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20d0b-203">参照</span><span class="sxs-lookup"><span data-stu-id="20d0b-203">See Also</span></span>  
 <span data-ttu-id="20d0b-204">[ピボット解除変換](pivot-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="20d0b-204">[Unpivot Transformation](pivot-transformation.md) </span></span>  
 <span data-ttu-id="20d0b-205">[データ フロー](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="20d0b-205">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="20d0b-206">Integration Services の変換</span><span class="sxs-lookup"><span data-stu-id="20d0b-206">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
