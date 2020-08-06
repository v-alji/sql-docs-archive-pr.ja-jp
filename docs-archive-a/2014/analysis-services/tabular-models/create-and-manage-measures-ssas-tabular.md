---
title: メジャーの作成および管理 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: edc1a4b2-96d3-4f34-bb70-6cacec79e819
author: minewiskan
ms.author: owend
ms.openlocfilehash: da507bf48b285a1414ffb85ba79da50508a2ae2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634667"
---
# <a name="create-and-manage-measures-ssas-tabular"></a><span data-ttu-id="b7294-102">メジャーを作成および管理する (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="b7294-102">Create and Manage Measures (SSAS Tabular)</span></span>
  <span data-ttu-id="b7294-103">メジャーとは、レポートまたは Excel ピボットテーブル (またはピボットグラフ) で使用するために作成される数式のことです。</span><span class="sxs-lookup"><span data-stu-id="b7294-103">A measure is a formula that is created for use in a report or Excel PivotTable (or PivotChart).</span></span> <span data-ttu-id="b7294-104">COUNT や SUM などの標準の集計関数に基づいてメジャーを作成することも、DAX を使用して独自の数式を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="b7294-104">Measures can be based on standard aggregation functions, such as COUNT or SUM, or you can define your own formula by using DAX.</span></span> <span data-ttu-id="b7294-105">このトピックのタスクでは、テーブルのメジャーグリッドを使用してメジャーを作成および管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b7294-105">The tasks in this topic describe how to create and manage measures by using a table's measure grid.</span></span>  
  
 <span data-ttu-id="b7294-106">このトピックでは、次のタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b7294-106">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="b7294-107">標準の集計式を使用してメジャーを作成するには</span><span class="sxs-lookup"><span data-stu-id="b7294-107">To create a measure using a standard aggregation formula</span></span>](#bkmk_create_stand)  
  
-   [<span data-ttu-id="b7294-108">カスタム式を使用してメジャーを作成するには</span><span class="sxs-lookup"><span data-stu-id="b7294-108">To create a measure using a custom formula</span></span>](#bkmk_create_custom)  
  
-   [<span data-ttu-id="b7294-109">メジャー プロパティを編集するには</span><span class="sxs-lookup"><span data-stu-id="b7294-109">To edit measure properties</span></span>](#bkmk_edit)  
  
-   [<span data-ttu-id="b7294-110">メジャー名を変更するには</span><span class="sxs-lookup"><span data-stu-id="b7294-110">To rename a measure</span></span>](#bkmk_rename)  
  
-   [<span data-ttu-id="b7294-111">メジャーを削除するには</span><span class="sxs-lookup"><span data-stu-id="b7294-111">To delete a measure</span></span>](#bkmk_delete)  
  
## <a name="tasks"></a><span data-ttu-id="b7294-112">タスク</span><span class="sxs-lookup"><span data-stu-id="b7294-112">Tasks</span></span>  
 <span data-ttu-id="b7294-113">メジャーを作成および管理するには、テーブルのメジャーグリッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b7294-113">To create and manage measures, you will use a table's measure grid.</span></span> <span data-ttu-id="b7294-114">テーブルのメジャー グリッドは、モデル デザイナーのデータ ビューのみで表示することができます。</span><span class="sxs-lookup"><span data-stu-id="b7294-114">You can view the measure grid for a table in the model designer in Data View only.</span></span> <span data-ttu-id="b7294-115">ダイアグラム ビューでは、メジャーの作成もメジャー グリッドの表示もできません。ただし、既存のメジャーであれば、ダイアグラム ビューで表示できます。</span><span class="sxs-lookup"><span data-stu-id="b7294-115">You cannot create measures or view the measure grid when in Diagram View; however, you can view existing measures in Diagram View.</span></span> <span data-ttu-id="b7294-116">あるテーブルのメジャー グリッドを表示するには、 **[テーブル]** メニューをクリックしてから **[メジャー グリッドの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7294-116">To show the measure grid for a table, click the **Table** menu, and then click **Show Measure Grid**.</span></span>  
  
###  <a name="to-create-a-measure-using-a-standard-aggregation-formula"></a><a name="bkmk_create_stand"></a><span data-ttu-id="b7294-117">標準の集計式を使用してメジャーを作成するには</span><span class="sxs-lookup"><span data-stu-id="b7294-117">To create a measure using a standard aggregation formula</span></span>  
  
-   <span data-ttu-id="b7294-118">メジャーを作成する列をクリックし、 **[列]** メニューをクリックしてから **[オート SUM]** をポイントし、集計の種類をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7294-118">Click on the column for which you want to create the measure, then click the **Column** menu, then point to **AutoSum**, and then click an aggregation type.</span></span>  
  
     <span data-ttu-id="b7294-119">既定名を持つメジャー、そしてその後に数式が列の直下にあるメジャー グリッドの最初のセルに自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="b7294-119">The measure will be created automatically with a default name, followed by the formula in the first cell in the measure grid directly beneath the column.</span></span>  
  
###  <a name="to-create-a-measure-using-a-custom-formula"></a><a name="bkmk_create_custom"></a> <span data-ttu-id="b7294-120">カスタム式を使用してメジャーを作成するには</span><span class="sxs-lookup"><span data-stu-id="b7294-120">To create a measure using a custom formula</span></span>  
  
-   <span data-ttu-id="b7294-121">メジャー グリッド内のメジャーを作成する列の下で、任意のセルをクリックしてから、数式バーに名前、コロン (:)、等号 (=)、および数式を続けて入力します。</span><span class="sxs-lookup"><span data-stu-id="b7294-121">In the measure grid, beneath the column for which you want to create the measure, click a cell, then in the formula bar, type a name, followed by a colon (:), followed by an equals sign (=), followed by the formula.</span></span> <span data-ttu-id="b7294-122">Enter キーを押して数式を確定します。</span><span class="sxs-lookup"><span data-stu-id="b7294-122">Press ENTER to accept the formula.</span></span>  
  
###  <a name="to-edit-measure-properties"></a><a name="bkmk_edit"></a><span data-ttu-id="b7294-123">メジャーのプロパティを編集するには</span><span class="sxs-lookup"><span data-stu-id="b7294-123">To edit measure properties</span></span>  
  
-   <span data-ttu-id="b7294-124">メジャー グリッド内で、メジャーをクリックしてから **[プロパティ]** ウィンドウで別のプロパティ値を入力するか選択します。</span><span class="sxs-lookup"><span data-stu-id="b7294-124">In the measure grid, click a measure, and then In the **Properties** window, type or select a different property value.</span></span>  
  
###  <a name="to-rename-a-measure"></a><a name="bkmk_rename"></a><span data-ttu-id="b7294-125">メジャーの名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="b7294-125">To rename a measure</span></span>  
  
-   <span data-ttu-id="b7294-126">メジャー グリッド内で、メジャーをクリックしてから **[プロパティ]** ウィンドウの **[メジャー名]** ボックスに新しい名前を入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="b7294-126">In the measure grid, click on a measure, and then In the **Properties** window, in **Measure Name**, type a new name, and then click ENTER.</span></span>  
  
     <span data-ttu-id="b7294-127">数式バー内でメジャーの名前を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="b7294-127">You can also rename a measure in the formula bar.</span></span> <span data-ttu-id="b7294-128">メジャー名の後に数式を付け、その後にコロンを付けます。</span><span class="sxs-lookup"><span data-stu-id="b7294-128">The measure name precedes the formula, followed by a colon.</span></span>  
  
###  <a name="to-delete-a-measure"></a><a name="bkmk_delete"></a><span data-ttu-id="b7294-129">メジャーを削除するには</span><span class="sxs-lookup"><span data-stu-id="b7294-129">To delete a measure</span></span>  
  
-   <span data-ttu-id="b7294-130">メジャー グリッドで、メジャーを右クリックしてから **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7294-130">In the measure grid, right-click a measure, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7294-131">参照</span><span class="sxs-lookup"><span data-stu-id="b7294-131">See Also</span></span>  
 <span data-ttu-id="b7294-132">[SSAS テーブル&#41;&#40;メジャー](measures-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="b7294-132">[Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md) </span></span>  
 <span data-ttu-id="b7294-133">[SSAS 表形式&#41;&#40;Kpi](kpis-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="b7294-133">[KPIs &#40;SSAS Tabular&#41;](kpis-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="b7294-134">計算列 &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="b7294-134">Calculated Columns &#40;SSAS Tabular&#41;</span></span>](ssas-calculated-columns.md)  
  
  
