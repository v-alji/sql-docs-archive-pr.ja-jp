---
title: 計算列 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e1011278-556d-4984-b01d-a37f8a33b304
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5d77b36ee3327d1b9e0d31ac97e5dbe135093a63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711033"
---
# <a name="calculated-columns-ssas-tabular"></a><span data-ttu-id="a2862-102">計算列 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="a2862-102">Calculated Columns (SSAS Tabular)</span></span>
  <span data-ttu-id="a2862-103">テーブル モデルの計算列では、モデルに新しいデータを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="a2862-103">Calculated columns, in tabular models, allow you to add new data to your model.</span></span> <span data-ttu-id="a2862-104">列に値を貼り付けるかインポートする代わりに、列の行レベル値を定義する DAX 数式を作成します。</span><span class="sxs-lookup"><span data-stu-id="a2862-104">Instead of pasting or importing values into the column, you create a DAX formula that defines the column's row level values.</span></span> <span data-ttu-id="a2862-105">すると、計算列を他のデータ列と同じように、レポート、ピボットテーブル、またはピボットグラフで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a2862-105">The calculated column can then be used in a report, PivotTable, or PivotChart as would any other column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a2862-106">計算列は、DirectQuery モードでのテーブル モデルではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="a2862-106">Calculated columns are not supported for tabular models in DirectQuery mode.</span></span> <span data-ttu-id="a2862-107">詳しくは、「[DirectQuery モード &#40;SSAS テーブル&#41;](directquery-mode-ssas-tabular.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a2862-107">For more information, see [DirectQuery Mode &#40;SSAS Tabular&#41;](directquery-mode-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="a2862-108">このトピックのセクション:</span><span class="sxs-lookup"><span data-stu-id="a2862-108">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="a2862-109">メリット</span><span class="sxs-lookup"><span data-stu-id="a2862-109">Benefits</span></span>](#bkmk_understanding)  
  
-   [<span data-ttu-id="a2862-110">計算列の名前付け</span><span class="sxs-lookup"><span data-stu-id="a2862-110">Naming a Calculated Column</span></span>](#bkmk_naming)  
  
-   [<span data-ttu-id="a2862-111">計算列のパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="a2862-111">Performance of Calculated Columns</span></span>](#bkmk_perf)  
  
-   [<span data-ttu-id="a2862-112">関連タスク</span><span class="sxs-lookup"><span data-stu-id="a2862-112">Related Tasks</span></span>](#bkmk_rel_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_understanding"></a> <span data-ttu-id="a2862-113">利点</span><span class="sxs-lookup"><span data-stu-id="a2862-113">Benefits</span></span>  
 <span data-ttu-id="a2862-114">計算列の数式は、Excel での数式と非常によく似ています。</span><span class="sxs-lookup"><span data-stu-id="a2862-114">Formulas in calculated columns are much like formulas in Excel.</span></span> <span data-ttu-id="a2862-115">ただし、Excel とは異なり、テーブル内の異なる行に異なる数式を作成することはできません。代わりに列全体に自動的に DAX 数式が適用されます。</span><span class="sxs-lookup"><span data-stu-id="a2862-115">Unlike Excel, however, you cannot create different formulas for different rows in a table; instead, the DAX formula is automatically applied to the entire column.</span></span>  
  
 <span data-ttu-id="a2862-116">列に数式が含まれている場合は、各行について値が計算されます。</span><span class="sxs-lookup"><span data-stu-id="a2862-116">When a column contains a formula, the value is computed for each row.</span></span> <span data-ttu-id="a2862-117">有効な数式を入力すると、その列に対する結果が計算されます。</span><span class="sxs-lookup"><span data-stu-id="a2862-117">The results are calculated for the column when you enter a valid formula.</span></span> <span data-ttu-id="a2862-118">基になるデータが更新された場合など、列の値は必要に応じて再計算されます。</span><span class="sxs-lookup"><span data-stu-id="a2862-118">Column values are then recalculated as necessary, such as when the underlying data is refreshed.</span></span>  
  
 <span data-ttu-id="a2862-119">メジャーおよび他の計算列に基づく計算列も作成できます。</span><span class="sxs-lookup"><span data-stu-id="a2862-119">You can create calculated columns that are based on measures and other calculated columns.</span></span> <span data-ttu-id="a2862-120">たとえば、計算列を作成してテキストの文字列から数字を抽出し、その数字を別の計算列に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="a2862-120">For example, you might create one calculated column to extract a number from a string of text, and then use that number in another calculated column.</span></span>  
  
 <span data-ttu-id="a2862-121">計算列は、既存テーブルに既に持っているデータに基づくか、または DAX 数式を使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="a2862-121">A calculated column is based on data that you already have in an existing table, or created by using a DAX formula.</span></span> <span data-ttu-id="a2862-122">たとえば、他のフィールドの値に対して連結、加算、サブストリングの抽出、比較などを行うための計算列を作成できます。</span><span class="sxs-lookup"><span data-stu-id="a2862-122">For example, you might choose to concatenate values, perform addition, extract substrings, or compare the values in other fields.</span></span> <span data-ttu-id="a2862-123">計算列を追加するには、モデルにテーブルが 1 つ以上存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2862-123">To add a calculated column, you must have at least one table in your model.</span></span>  
  
 <span data-ttu-id="a2862-124">計算列における簡単な数式を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="a2862-124">This example demonstrates a simple formula in a calculated column:</span></span>  
  
```  
=EOMONTH([StartDate],0])  
  
```  
  
 <span data-ttu-id="a2862-125">この数式では、StartDate 列から月を抽出します。</span><span class="sxs-lookup"><span data-stu-id="a2862-125">This formula extracts the month from the StartDate column.</span></span> <span data-ttu-id="a2862-126">そして、テーブルの各行について月の最終日を計算します。</span><span class="sxs-lookup"><span data-stu-id="a2862-126">It then calculates the end of the month value for each row in the table.</span></span> <span data-ttu-id="a2862-127">2 番目のパラメーターは、StartDate の月より前または後の月数を指定します。この場合、0 は同じ月であることを表します。</span><span class="sxs-lookup"><span data-stu-id="a2862-127">The second parameter specifies the number of months before or after the month in StartDate; in this case, 0 means the same month.</span></span> <span data-ttu-id="a2862-128">たとえば、StartDate 列の値が 6/1/2001 の場合、計算列の値は 6/30/2001 になります。</span><span class="sxs-lookup"><span data-stu-id="a2862-128">For example, if the value in the StartDate column is 6/1/2001, the value in the calculated column will be 6/30/2001.</span></span>  
  
##  <a name="naming-a-calculated-column"></a><a name="bkmk_naming"></a><span data-ttu-id="a2862-129">計算列の名前付け</span><span class="sxs-lookup"><span data-stu-id="a2862-129">Naming a Calculated Column</span></span>  
 <span data-ttu-id="a2862-130">既定では、新しい計算列はテーブル内のその他の列の右側に追加され、 **CalculatedColumn1**、 **CalculatedColumn2**などの既定の名前が自動的に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="a2862-130">By default, new calculated columns are added to the right of other columns in a table, and the column is automatically assigned the default name of **CalculatedColumn1**, **CalculatedColumn2**, and so forth.</span></span> <span data-ttu-id="a2862-131">列を右クリックしてから [列の挿入] をクリックして、2 つの既存列の間に新しい列を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="a2862-131">You can also right click a column, and then click Insert Column to create a new column between two existing columns.</span></span> <span data-ttu-id="a2862-132">クリックしてドラッグすることで、同じテーブル内の列を並べ替えることができます。また、列の作成後に名前を変更することもできます。ただし、計算列の変更に対する次の制限事項に注意してください。</span><span class="sxs-lookup"><span data-stu-id="a2862-132">You can rearrange columns within the same table by clicking and dragging, and you can rename columns after they are created; however, you should be aware of the following restrictions on changes to calculated columns:</span></span>  
  
-   <span data-ttu-id="a2862-133">それぞれの列名は、1 つのテーブル内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2862-133">Each column name must be unique within a table.</span></span>  
  
-   <span data-ttu-id="a2862-134">同じモデル内のメジャーに既に使用されている名前は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="a2862-134">Avoid names that have already been used for measures within the same model.</span></span> <span data-ttu-id="a2862-135">メジャーと計算列を同じ名前にすることは可能ですが、名前が一意でないと計算エラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="a2862-135">Although it is possible for a measure and a calculated column to have the same name, if names are not unique you can get calculation errors.</span></span> <span data-ttu-id="a2862-136">誤ってメジャーが呼び出されないようにするために、列を参照するときは常に完全修飾列参照を使用してください。</span><span class="sxs-lookup"><span data-stu-id="a2862-136">To avoid accidentally invoking a measure, when referring to a column always use a fully qualified column reference.</span></span>  
  
-   <span data-ttu-id="a2862-137">計算列の名前を変更する場合、その列に依存する数式をすべて手動で更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2862-137">When you rename a calculated column, any formulas that rely on the column must be updated manually.</span></span> <span data-ttu-id="a2862-138">手動更新モードでない場合、数式の結果の更新は自動的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="a2862-138">Unless you are in manual update mode, updating the results of formulas takes place automatically.</span></span> <span data-ttu-id="a2862-139">ただし、この処理には時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="a2862-139">However, this operation might take some time.</span></span>  
  
-   <span data-ttu-id="a2862-140">列名に使用できない文字がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="a2862-140">There are some characters that cannot be used within the names of columns.</span></span> <span data-ttu-id="a2862-141">詳細については、「[PowerPivot の DAX 構文の仕様](/dax/dax-syntax-reference)」の「名前付けに関する要件」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2862-141">For more information, see "Naming Requirements" in [DAX Syntax Specification for PowerPivot](/dax/dax-syntax-reference).</span></span>  
  
##  <a name="performance-of-calculated-columns"></a><a name="bkmk_perf"></a><span data-ttu-id="a2862-142">計算列のパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="a2862-142">Performance of Calculated Columns</span></span>  
 <span data-ttu-id="a2862-143">計算列で使用される数式は、メジャーで使用される数式よりリソースを大量に消費する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a2862-143">The formula for a calculated column can be more resource-intensive than the formula used for a measure.</span></span> <span data-ttu-id="a2862-144">その理由の 1 つとして、計算列の結果が常にテーブルのすべての行を対象に計算されるのに対し、メジャーはレポート、ピボットテーブル、またはピボットグラフに使用されているフィルターで定義されたセルのみを対象として計算されることが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="a2862-144">One reason is that the result for a calculated column is always calculated for each row in a table, whereas a measure is only calculated for the cells defined by the filter used in a report, PivotTable, or PivotChart.</span></span> <span data-ttu-id="a2862-145">たとえば、テーブルに 100 万行含まれている場合、計算列には必ず 100 万個の結果が含まれるため、それだけパフォーマンスにも影響します。</span><span class="sxs-lookup"><span data-stu-id="a2862-145">For example, a table with a million rows will always have a calculated column with a million results, and a corresponding effect on performance.</span></span> <span data-ttu-id="a2862-146">ただし、ピボットテーブルでは、通常、行見出しおよび列見出しを適用してデータをフィルター処理します。したがって、メジャーは、ピボットテーブルの各セルに含まれているデータのサブセットのみを対象として計算されます。</span><span class="sxs-lookup"><span data-stu-id="a2862-146">However, a PivotTable generally filters data by applying row and column headings; therefore, a measure is calculated only for the subset of data in each cell of the PivotTable.</span></span>  
  
 <span data-ttu-id="a2862-147">数式は、値を評価する他の列や式など、数式で参照されるオブジェクトに依存しています。</span><span class="sxs-lookup"><span data-stu-id="a2862-147">A formula has dependencies on the objects that are referenced in the formula, such as other columns or expressions that evaluate values.</span></span> <span data-ttu-id="a2862-148">たとえば、別の列に基づいている計算列、つまり列参照を使用する式を含む計算は、その別の列が評価されるまで評価することができません。</span><span class="sxs-lookup"><span data-stu-id="a2862-148">For example, a calculated column that is based on another column, or a calculation that contains an expression with a column reference, cannot be evaluated until the other column is evaluated.</span></span> <span data-ttu-id="a2862-149">既定では、ブックで自動更新が有効になっています。したがって、値の更新時や数式の更新時にこうした依存関係すべてがパフォーマンスに影響する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a2862-149">By default, automatic refresh is enabled in workbooks; therefore, all such dependencies can affect performance while values are updated and formulas refreshed.</span></span>  
  
 <span data-ttu-id="a2862-150">計算列を作成するときにパフォーマンス上の問題を回避するには、次のガイドラインに従ってください。</span><span class="sxs-lookup"><span data-stu-id="a2862-150">To avoid performance issues when you create calculated columns, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="a2862-151">複雑な依存性を多く含む 1 つの数式を作成するのではなく、結果を列に保存しながら段階的に計算を行う複数の数式を作成することで、結果を検証し、パフォーマンスを評価できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a2862-151">Rather than create a single formula that contains many complex dependencies, create the formulas in steps, with results saved to columns, so that you can validate the results and assess performance.</span></span>  
  
-   <span data-ttu-id="a2862-152">データを変更すると、多くの場合は計算列を再計算する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2862-152">Modification of data will often require that calculated columns be recalculated.</span></span> <span data-ttu-id="a2862-153">再計算が実行されないようにするには、再計算モードを手動に設定します。ただし、計算列の値が正しくない場合、データを更新して再計算するまで、その列はグレー表示されます。</span><span class="sxs-lookup"><span data-stu-id="a2862-153">You can prevent this by setting the recalculation mode to manual; however, if any values in the calculated column are incorrect the column will be grayed out until you refresh and recalculate the data.</span></span>  
  
-   <span data-ttu-id="a2862-154">テーブル間のリレーションシップを変更または削除すると、そのテーブル内の列を使用する数式が無効になります。</span><span class="sxs-lookup"><span data-stu-id="a2862-154">If you change or delete relationships between tables, formulas that use columns in those tables will become invalid.</span></span>  
  
-   <span data-ttu-id="a2862-155">循環依存や自己参照依存を含む数式を作成した場合、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="a2862-155">If you create a formula that contains a circular or self-referencing dependency, an error will occur.</span></span>  
  
##  <a name="related-tasks"></a><a name="bkmk_rel_tasks"></a> <span data-ttu-id="a2862-156">関連タスク</span><span class="sxs-lookup"><span data-stu-id="a2862-156">Related Tasks</span></span>  
  
|<span data-ttu-id="a2862-157">トピック</span><span class="sxs-lookup"><span data-stu-id="a2862-157">Topic</span></span>|<span data-ttu-id="a2862-158">説明</span><span class="sxs-lookup"><span data-stu-id="a2862-158">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a2862-159">計算列の作成 &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="a2862-159">Create a Calculated Column &#40;SSAS Tabular&#41;</span></span>](ssas-calculated-columns-create-a-calculated-column.md)|<span data-ttu-id="a2862-160">このトピックのタスクでは、テーブルに新しい計算列を追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2862-160">Tasks in this topic describe how to add a new calculated column to a table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a2862-161">参照</span><span class="sxs-lookup"><span data-stu-id="a2862-161">See Also</span></span>  
 <span data-ttu-id="a2862-162">[SSAS 表形式のテーブルと列 &#40;&#41;](tables-and-columns-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="a2862-162">[Tables and Columns &#40;SSAS Tabular&#41;](tables-and-columns-ssas-tabular.md) </span></span>  
 <span data-ttu-id="a2862-163">[SSAS テーブル&#41;&#40;メジャー](measures-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="a2862-163">[Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="a2862-164">計算 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="a2862-164">Calculations &#40;SSAS Tabular&#41;</span></span>](calculations-ssas-tabular.md)  
  
  
