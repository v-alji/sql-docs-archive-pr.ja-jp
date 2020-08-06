---
title: Kpi の作成と管理 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.kpi.f1
ms.assetid: c96026c2-4394-4c3c-986b-4c95a4421900
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8e9d7ef77939efe407ed6ab0d725a6d788c58b49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634668"
---
# <a name="create-and-manage-kpis-ssas-tabular"></a><span data-ttu-id="89ac9-102">KPI の作成および管理 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="89ac9-102">Create and Manage KPIs (SSAS Tabular)</span></span>
  <span data-ttu-id="89ac9-103">このトピックでは、テーブル モデルで KPI (主要業績評価指標) を作成、編集、または削除する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="89ac9-103">This topic describes how to create, edit, or delete a KPI (Key Performance Indicator) in a tabular model.</span></span> <span data-ttu-id="89ac9-104">KPI を作成するには、KPI の基本値に評価されるメジャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="89ac9-104">To create a KPI, you select a measure that evaluates to the KPI's Base value.</span></span> <span data-ttu-id="89ac9-105">次に、[主要業績評価指標] ダイアログ ボックスで、評価結果が対象の値になる 2 番目のメジャーまたは絶対値を選択します。</span><span class="sxs-lookup"><span data-stu-id="89ac9-105">You then use the Key Performance Indicator dialog box to select a second measure or an absolute value that evaluates to a target value.</span></span> <span data-ttu-id="89ac9-106">ベース メジャーと対象のメジャーの間のパフォーマンスを測定する、状態のしきい値を定義します。</span><span class="sxs-lookup"><span data-stu-id="89ac9-106">You can then define status thresholds that measure the performance between the Base and Target measures.</span></span>  
  
 <span data-ttu-id="89ac9-107">このトピックでは、次のタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="89ac9-107">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="89ac9-108">KPI を作成するには</span><span class="sxs-lookup"><span data-stu-id="89ac9-108">To create a KPI</span></span>](#bkmk_create_KPI)  
  
-   [<span data-ttu-id="89ac9-109">KPI を編集するには</span><span class="sxs-lookup"><span data-stu-id="89ac9-109">To edit a KPI</span></span>](#bkmk_edit_KPI)  
  
-   [<span data-ttu-id="89ac9-110">KPI とベースメジャーを削除するには</span><span class="sxs-lookup"><span data-stu-id="89ac9-110">To delete a KPI and the base measure</span></span>](#bkmk_delete)  
  
-   [<span data-ttu-id="89ac9-111">ベース メジャーは削除せずに KPI を削除するには</span><span class="sxs-lookup"><span data-stu-id="89ac9-111">To delete a KPI, but keep the base measure</span></span>](#bkmk_delete_KPI)  
  
## <a name="tasks"></a><span data-ttu-id="89ac9-112">タスク</span><span class="sxs-lookup"><span data-stu-id="89ac9-112">Tasks</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="89ac9-113">KPI を作成する前に、値を評価するベース メジャーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89ac9-113">Before creating a KPI, you must first create a Base measure that evaluates to value.</span></span> <span data-ttu-id="89ac9-114">次に、ベース メジャーを KPI に拡張します。</span><span class="sxs-lookup"><span data-stu-id="89ac9-114">You then extend the Base measure to a KPI.</span></span> <span data-ttu-id="89ac9-115">メジャーの作成方法は、別のトピック (「 [メジャーを作成および管理する &#40;SSAS テーブル&#41;](measures-ssas-tabular.md)」) に説明があります。</span><span class="sxs-lookup"><span data-stu-id="89ac9-115">How to create measures are described in another topic, [Create and Manage Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md).</span></span> <span data-ttu-id="89ac9-116">KPI には対象の値も必要です。</span><span class="sxs-lookup"><span data-stu-id="89ac9-116">A KPI also requires a target value.</span></span> <span data-ttu-id="89ac9-117">この値には事前定義された別のメジャーまたは絶対値を使用できます。</span><span class="sxs-lookup"><span data-stu-id="89ac9-117">This value can be from another pre-defined measure or an absolute value.</span></span> <span data-ttu-id="89ac9-118">ベース メジャーを KPI に拡張すると、[主要業績評価指標] ダイアログ ボックスで対象の値を選択し、状態のしきい値を定義できます。</span><span class="sxs-lookup"><span data-stu-id="89ac9-118">Once you have extended a Base measure to a KPI, you can then select the target value and define status thresholds in the Key Performance Indicator dialog box.</span></span>  
  
###  <a name="to-create-a-kpi"></a><a name="bkmk_create_KPI"></a> <span data-ttu-id="89ac9-119">KPI を作成するには</span><span class="sxs-lookup"><span data-stu-id="89ac9-119">To create a KPI</span></span>  
  
1.  <span data-ttu-id="89ac9-120">メジャー グリッドで、ベース メジャー (値) となるメジャーを右クリックし、 **[KPI の作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89ac9-120">In the measure grid, right-click the measure that will serve as the Base measure (value), and then click **Create KPI**.</span></span>  
  
2.  <span data-ttu-id="89ac9-121">**[主要業績評価指標]** ダイアログ ボックスの **[ターゲット値の定義]** で、次のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="89ac9-121">In the **Key Performance Indicator** dialog box, in **Define target value**, select from one of the following:</span></span>  
  
     <span data-ttu-id="89ac9-122">**[メジャー]** を選択し、リスト ボックスから対象のメジャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="89ac9-122">Select **Measure**, and then select a target measure from the listbox.</span></span>  
  
     <span data-ttu-id="89ac9-123">**[絶対値]** を選択し、数値を入力します。</span><span class="sxs-lookup"><span data-stu-id="89ac9-123">Select **Absolute value**, and then type a numerical value.</span></span>  
  
3.  <span data-ttu-id="89ac9-124">**[状態のしきい値の定義]** で、低いしきい値および高いしきい値をクリックしてスライドします。</span><span class="sxs-lookup"><span data-stu-id="89ac9-124">In **Define status thresholds**, click and slide the low and high threshold values.</span></span>  
  
4.  <span data-ttu-id="89ac9-125">**[アイコンのスタイルの選択]** で画像の種類をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89ac9-125">In **Select icon style**, click an image type.</span></span>  
  
5.  <span data-ttu-id="89ac9-126">**[説明]** をクリックして KPI、値、状態、および対象の説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="89ac9-126">Click on **Descriptions**, and then type descriptions for KPI, Value, Status, and Target.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="89ac9-127">Excel で分析機能を使用して、KPI をテストできます。</span><span class="sxs-lookup"><span data-stu-id="89ac9-127">You can use the Analyze in Excel feature to test your KPI.</span></span> <span data-ttu-id="89ac9-128">詳しくは、後の「 [Excel で分析 &#40;SSAS テーブル&#41;](analyze-in-excel-ssas-tabular.md)で [ロール マネージャー] ダイアログ ボックスを使用してロールを定義するテーブル モデル作成者向けです。</span><span class="sxs-lookup"><span data-stu-id="89ac9-128">For more information, see [Analyze in Excel &#40;SSAS Tabular&#41;](analyze-in-excel-ssas-tabular.md).</span></span>  
  
###  <a name="to-edit-a-kpi"></a><a name="bkmk_edit_KPI"></a> <span data-ttu-id="89ac9-129">KPI を編集するには</span><span class="sxs-lookup"><span data-stu-id="89ac9-129">To edit a KPI</span></span>  
  
-   <span data-ttu-id="89ac9-130">メジャー グリッドで、KPI のベース メジャー (値) となるメジャーを右クリックし、 **[KPI 設定の編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89ac9-130">In the measure grid, right-click the measure that serves as the Base measure (value) of the KPI, and then click **Edit KPI Settings**.</span></span>  
  
###  <a name="to-delete-a-kpi-and-the-base-measure"></a><a name="bkmk_delete"></a> <span data-ttu-id="89ac9-131">KPI とベース メジャーを削除するには</span><span class="sxs-lookup"><span data-stu-id="89ac9-131">To delete a KPI and the base measure</span></span>  
  
-   <span data-ttu-id="89ac9-132">メジャー グリッドで、KPI のベース メジャー (値) となるメジャーを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89ac9-132">In the measure grid, right-click the measure that serves as the Base measure (value) of the KPI, and then click **Delete**.</span></span>  
  
###  <a name="to-delete-a-kpi-but-keep-the-base-measure"></a><a name="bkmk_delete_KPI"></a><span data-ttu-id="89ac9-133">KPI を削除するがベースメジャーを保持するには</span><span class="sxs-lookup"><span data-stu-id="89ac9-133">To delete a KPI, but keep the base measure</span></span>  
  
-   <span data-ttu-id="89ac9-134">メジャー グリッドで、KPI のベース メジャー (値) となるメジャーを右クリックし、 **[KPI の削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89ac9-134">In the measure grid, right-click the measure that serves as the Base measure (value) of the KPI, and then click **Delete KPI**.</span></span>  
  
## <a name="alt-shortcuts"></a><span data-ttu-id="89ac9-135">Alt ショートカット</span><span class="sxs-lookup"><span data-stu-id="89ac9-135">ALT Shortcuts</span></span>  
  
|<span data-ttu-id="89ac9-136">UI セクション</span><span class="sxs-lookup"><span data-stu-id="89ac9-136">UI section</span></span>|<span data-ttu-id="89ac9-137">キー コマンド</span><span class="sxs-lookup"><span data-stu-id="89ac9-137">Key command</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="89ac9-138">KPI ベース メジャー</span><span class="sxs-lookup"><span data-stu-id="89ac9-138">KPI base measure</span></span>|<span data-ttu-id="89ac9-139">Alt + B</span><span class="sxs-lookup"><span data-stu-id="89ac9-139">ALT+B</span></span>|  
|<span data-ttu-id="89ac9-140">KPI ステータス</span><span class="sxs-lookup"><span data-stu-id="89ac9-140">KPI Status</span></span>|<span data-ttu-id="89ac9-141">Alt + S</span><span class="sxs-lookup"><span data-stu-id="89ac9-141">ALT+S</span></span>|  
|<span data-ttu-id="89ac9-142">Measure</span><span class="sxs-lookup"><span data-stu-id="89ac9-142">Measure</span></span>|<span data-ttu-id="89ac9-143">Alt + M</span><span class="sxs-lookup"><span data-stu-id="89ac9-143">ALT+M</span></span>|  
|<span data-ttu-id="89ac9-144">[絶対値]</span><span class="sxs-lookup"><span data-stu-id="89ac9-144">Absolute value</span></span>|<span data-ttu-id="89ac9-145">Alt + A</span><span class="sxs-lookup"><span data-stu-id="89ac9-145">ALT+A</span></span>|  
|<span data-ttu-id="89ac9-146">[状態のしきい値の定義]</span><span class="sxs-lookup"><span data-stu-id="89ac9-146">Define status thresholds</span></span>|<span data-ttu-id="89ac9-147">Alt + U</span><span class="sxs-lookup"><span data-stu-id="89ac9-147">ALT+U</span></span>|  
|<span data-ttu-id="89ac9-148">[アイコンのスタイルの選択]</span><span class="sxs-lookup"><span data-stu-id="89ac9-148">Select icon style</span></span>|<span data-ttu-id="89ac9-149">Alt&lt;/localizedText&gt; + &lt;localizedText&gt;I</span><span class="sxs-lookup"><span data-stu-id="89ac9-149">ALT+I</span></span>|  
|<span data-ttu-id="89ac9-150">傾向</span><span class="sxs-lookup"><span data-stu-id="89ac9-150">Trend</span></span>|<span data-ttu-id="89ac9-151">Alt + T</span><span class="sxs-lookup"><span data-stu-id="89ac9-151">ALT+T</span></span>|  
|<span data-ttu-id="89ac9-152">説明</span><span class="sxs-lookup"><span data-stu-id="89ac9-152">Descriptions</span></span>|<span data-ttu-id="89ac9-153">Alt + D</span><span class="sxs-lookup"><span data-stu-id="89ac9-153">ALT+D</span></span>|  
|<span data-ttu-id="89ac9-154">傾向</span><span class="sxs-lookup"><span data-stu-id="89ac9-154">Trend</span></span>|<span data-ttu-id="89ac9-155">Alt + T</span><span class="sxs-lookup"><span data-stu-id="89ac9-155">ALT+T</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89ac9-156">参照</span><span class="sxs-lookup"><span data-stu-id="89ac9-156">See Also</span></span>  
 <span data-ttu-id="89ac9-157">[SSAS 表形式&#41;&#40;Kpi](kpis-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="89ac9-157">[KPIs &#40;SSAS Tabular&#41;](kpis-ssas-tabular.md) </span></span>  
 <span data-ttu-id="89ac9-158">[SSAS テーブル&#41;&#40;メジャー](measures-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="89ac9-158">[Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="89ac9-159">メジャーを作成および管理する &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="89ac9-159">Create and Manage Measures &#40;SSAS Tabular&#41;</span></span>](create-and-manage-measures-ssas-tabular.md)  
  
  
