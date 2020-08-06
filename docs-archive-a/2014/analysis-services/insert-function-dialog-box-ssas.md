---
title: '[関数の挿入] ダイアログボックス (SSAS) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.BIDTOOLSET.INSERTFUNCTIONDB.F1
ms.assetid: c4b36d8f-2328-45f7-8bd4-cc0111571e25
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0d92dd34e671dc026215d79e7eaed88bebfac15f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641363"
---
# <a name="insert-function-dialog-box-ssas"></a><span data-ttu-id="43f34-102">[関数の挿入] ダイアログ ボックス (SSAS)</span><span class="sxs-lookup"><span data-stu-id="43f34-102">Insert Function Dialog Box (SSAS)</span></span>
  <span data-ttu-id="43f34-103">**[関数の挿入]** ダイアログ ボックスを使用すると、数式の作成時に使用できる関数の一覧から関数を選択できます。</span><span class="sxs-lookup"><span data-stu-id="43f34-103">The **Insert Function** dialog box enables you to choose from a list of functions that can be used when building formulas.</span></span> <span data-ttu-id="43f34-104">モデル デザイナーからこのダイアログ ボックスにアクセスするには、各テーブルの上にある数式バーで、関数 (**[fx]**) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="43f34-104">To access this dialog box from the model designer, in the formula bar above each table, click the function (**fx**) button.</span></span> <span data-ttu-id="43f34-105">数式で使用する関数の選択の詳細については、「DAX の概要」と「数式の作成」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43f34-105">For more information about choosing functions to use in formulas, see DAX Introduction and Build a Formula.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="43f34-106">Item</span><span class="sxs-lookup"><span data-stu-id="43f34-106">Item</span></span>|<span data-ttu-id="43f34-107">説明</span><span class="sxs-lookup"><span data-stu-id="43f34-107">Description</span></span>|  
|<span data-ttu-id="43f34-108">**カテゴリの選択**</span><span class="sxs-lookup"><span data-stu-id="43f34-108">**Select a category**</span></span>|<span data-ttu-id="43f34-109">必要な関数の種類がわかっている場合は、一覧からカテゴリを選択します。わからない場合は、 **[すべて]** をクリックしてアルファベット順の関数の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="43f34-109">If you have a general idea which kind of function you need, choose a category from the list; or select **All** to view an alphabetical list of functions.</span></span>|  
|<span data-ttu-id="43f34-110">**関数を選択する**</span><span class="sxs-lookup"><span data-stu-id="43f34-110">**Select a function**</span></span>|<span data-ttu-id="43f34-111">選択したカテゴリの関数の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="43f34-111">Displays a list of the functions in the selected category.</span></span>|  
|<span data-ttu-id="43f34-112">**説明**</span><span class="sxs-lookup"><span data-stu-id="43f34-112">**Description**</span></span>|<span data-ttu-id="43f34-113">関数の処理内容と、必須またはオプションの引数 (列名、式など) についての説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="43f34-113">Displays a description of what the function does, together with any required or optional arguments, such as column names and expressions.</span></span>|  
  
## <a name="function-categories"></a><span data-ttu-id="43f34-114">関数のカテゴリ</span><span class="sxs-lookup"><span data-stu-id="43f34-114">Function Categories</span></span>  
 <span data-ttu-id="43f34-115">Data Analysis Expressions (DAX) には、 **[関数の挿入]** ダイアログ ボックスに表示される次の種類の関数のカテゴリが用意されています。</span><span class="sxs-lookup"><span data-stu-id="43f34-115">Data Analysis Expressions (DAX) provides the following types of function categories in the **Insert Functions** dialog box.</span></span>  
  
 <span data-ttu-id="43f34-116">All</span><span class="sxs-lookup"><span data-stu-id="43f34-116">All</span></span>  
  
 <span data-ttu-id="43f34-117">日付と時刻の関数</span><span class="sxs-lookup"><span data-stu-id="43f34-117">Date & Time</span></span>  
  
 <span data-ttu-id="43f34-118">Assert</span><span class="sxs-lookup"><span data-stu-id="43f34-118">Filter</span></span>  
  
 <span data-ttu-id="43f34-119">論理</span><span class="sxs-lookup"><span data-stu-id="43f34-119">Logical</span></span>  
  
 <span data-ttu-id="43f34-120">数学関数と三角関数</span><span class="sxs-lookup"><span data-stu-id="43f34-120">Math & Trig</span></span>  
  
 <span data-ttu-id="43f34-121">統計</span><span class="sxs-lookup"><span data-stu-id="43f34-121">Statistical</span></span>  
  
 <span data-ttu-id="43f34-122">Text</span><span class="sxs-lookup"><span data-stu-id="43f34-122">Text</span></span>  
  
## <a name="measures-and-formulas"></a><span data-ttu-id="43f34-123">メジャーと数式</span><span class="sxs-lookup"><span data-stu-id="43f34-123">Measures and Formulas</span></span>  
 <span data-ttu-id="43f34-124">**[関数の挿入]** ダイアログ ボックスを使用できるのは、数式を作成するときだけです。</span><span class="sxs-lookup"><span data-stu-id="43f34-124">The **Insert Function** dialog box is available only when you are building a formula.</span></span> <span data-ttu-id="43f34-125">計算は、計算列、ピボットテーブル、またはピボットグラフで作成することができます。</span><span class="sxs-lookup"><span data-stu-id="43f34-125">You can create calculations either in a calculated column, or in a PivotTable or PivotChart.</span></span> <span data-ttu-id="43f34-126">ピボットテーブルで明示的に使用する数式は、 *メジャー*とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="43f34-126">Formulas that you build expressly for use in a PivotTable are also called *measures*.</span></span> <span data-ttu-id="43f34-127">詳細については、「[ &#40;SSAS テーブル&#41;](tabular-models/ssas-calculated-columns-create-a-calculated-column.md)」と「[メジャーを作成および管理する &#40;SSAS テーブル&#41;](tabular-models/measures-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43f34-127">For more information, see [Create a Calculated Column &#40;SSAS Tabular&#41;](tabular-models/ssas-calculated-columns-create-a-calculated-column.md) and [Create and Manage Measures &#40;SSAS Tabular&#41;](tabular-models/measures-ssas-tabular.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43f34-128">参照</span><span class="sxs-lookup"><span data-stu-id="43f34-128">See Also</span></span>  
 [<span data-ttu-id="43f34-129">計算 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="43f34-129">Calculations &#40;SSAS Tabular&#41;</span></span>](tabular-models/calculations-ssas-tabular.md)  
  
  
