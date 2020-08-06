---
title: 計算列の作成 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.as.daxref.CreataCalculatedColumn.f1
ms.assetid: 59440510-2d76-41dc-9b55-edc15259f9da
author: minewiskan
ms.author: owend
ms.openlocfilehash: cdb56ffb2b42aa8225b7eff76b11315ea511fd81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711034"
---
# <a name="create-a-calculated-column-ssas-tabular"></a><span data-ttu-id="e4032-102">計算列の作成 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="e4032-102">Create a Calculated Column (SSAS Tabular)</span></span>
  <span data-ttu-id="e4032-103">計算列では、モデルに新しいデータを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="e4032-103">Calculated columns allow you to add new data to your model.</span></span> <span data-ttu-id="e4032-104">列に値を貼り付けるかインポートする代わりに、列の行レベル値を定義する DAX 数式を作成します。</span><span class="sxs-lookup"><span data-stu-id="e4032-104">Instead of pasting or importing values into the column, you create a DAX formula that defines the column's row level values.</span></span> <span data-ttu-id="e4032-105">計算列の各行の値は、有効な数式を作成して Enter キーを押したときに、計算および代入されます。</span><span class="sxs-lookup"><span data-stu-id="e4032-105">The values in each row of a calculated column are calculated and populated when you create a valid formula and then click ENTER.</span></span> <span data-ttu-id="e4032-106">計算列は、他のデータ列と同じように、レポートまたは分析のアプリケーションに追加できます。</span><span class="sxs-lookup"><span data-stu-id="e4032-106">The calculated column can then be added to a reporting or analysis application just as would any other column of data.</span></span> <span data-ttu-id="e4032-107">このトピックでは、モデル デザイナーの DAX 数式バーを使用して新しい計算列を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e4032-107">This topic describes how to create a new calculated column by using the DAX formula bar in the model designer.</span></span>  
  
#### <a name="to-create-a-new-calculated-column"></a><span data-ttu-id="e4032-108">新しい計算列を作成するには</span><span class="sxs-lookup"><span data-stu-id="e4032-108">To create a new calculated column</span></span>  
  
1.  <span data-ttu-id="e4032-109">モデル デザイナーのデータ ビューで、計算列を追加するテーブルを選択し、 **[列]** メニューをクリックしてから **[列の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e4032-109">In the model designer, in Data View, select the table to which you want to add a calculated column, then click the **Column** menu, and then click **Add Column**.</span></span>  
  
     <span data-ttu-id="e4032-110">右端の空白の列に対して **[列の追加]** が強調表示され、カーソルが数式バーに移動します。</span><span class="sxs-lookup"><span data-stu-id="e4032-110">**Add Column** is highlighted over the empty rightmost column, and the cursor moves to the formula bar.</span></span>  
  
     <span data-ttu-id="e4032-111">2 つの既存の列の間に新しい列を作成するには、既存の列をクリックしてから **[列の挿入]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e4032-111">To create a new column between two existing columns, right-click an existing column, and then click **Insert Column**.</span></span>  
  
2.  <span data-ttu-id="e4032-112">数式バーで次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="e4032-112">In the formula bar, do one of the following:</span></span>  
  
    -   <span data-ttu-id="e4032-113">等号を入力し、続いて数式を入力します。</span><span class="sxs-lookup"><span data-stu-id="e4032-113">Type an equal sign followed by a formula.</span></span>  
  
    -   <span data-ttu-id="e4032-114">等号に続けて DAX 関数、その後に関数に必要な引数やパラメーターを入力します。</span><span class="sxs-lookup"><span data-stu-id="e4032-114">Type an equal sign, followed by a DAX function, followed by arguments and parameters as required by the function.</span></span>  
  
    -   <span data-ttu-id="e4032-115">関数ボタン (**[fx]**) をクリックし、 **[関数の挿入]** ダイアログ ボックスでカテゴリおよび関数を選択してから、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e4032-115">Click the function button (**fx**), then in the **Insert Function** dialog box, select a category and function, and then click **OK**.</span></span> <span data-ttu-id="e4032-116">数式バーで、関数に必要な残りの引数とパラメーターを入力します。</span><span class="sxs-lookup"><span data-stu-id="e4032-116">In the formula bar, type the remaining arguments and parameters as required by the function.</span></span>  
  
3.  <span data-ttu-id="e4032-117">Enter キーを押して数式を確定します。</span><span class="sxs-lookup"><span data-stu-id="e4032-117">Press ENTER to accept the formula.</span></span>  
  
     <span data-ttu-id="e4032-118">列全体に数式が設定され、行ごとに値が計算されます。</span><span class="sxs-lookup"><span data-stu-id="e4032-118">The entire column is populated with the formula, and a value is calculated for each row.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="e4032-119">DAX 数式のオートコンプリート機能は、関数が入れ子になっている既存の数式の途中で使用できます。</span><span class="sxs-lookup"><span data-stu-id="e4032-119">You can use DAX Formula AutoComplete in the middle of an existing formula with nested functions.</span></span> <span data-ttu-id="e4032-120">挿入ポイントの直前のテキストが、ドロップダウン リストに値を表示するために使用されます。挿入ポイントより後ろのすべてのテキストは変更されません。</span><span class="sxs-lookup"><span data-stu-id="e4032-120">The text immediately before the insertion point is used to display values in the drop-down list, and all of the text after the insertion point remains unchanged.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4032-121">参照</span><span class="sxs-lookup"><span data-stu-id="e4032-121">See Also</span></span>  
 <span data-ttu-id="e4032-122">[SSAS 表形式の計算列 &#40;&#41;](ssas-calculated-columns.md) </span><span class="sxs-lookup"><span data-stu-id="e4032-122">[Calculated Columns &#40;SSAS Tabular&#41;](ssas-calculated-columns.md) </span></span>  
 [<span data-ttu-id="e4032-123">メジャー &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="e4032-123">Measures &#40;SSAS Tabular&#41;</span></span>](measures-ssas-tabular.md)  
  
  
