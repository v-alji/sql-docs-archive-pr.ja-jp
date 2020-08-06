---
title: Kpi (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a0524602-5239-45a7-8c44-2477302a3637
author: minewiskan
ms.author: owend
ms.openlocfilehash: 54cc7341f2d0f002496c1936f2c4f0808cd5e243
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712493"
---
# <a name="kpis-ssas-tabular"></a><span data-ttu-id="ff391-102">KPI (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="ff391-102">KPIs (SSAS Tabular)</span></span>
  <span data-ttu-id="ff391-103">*KPI* (主要業績評価指標) は、表形式モデルで、 *対象* の値に対する *ベース* メジャーによって定義される、また、メジャーまたは絶対値によって定義される値のパフォーマンスの測定に使用されます。</span><span class="sxs-lookup"><span data-stu-id="ff391-103">A *KPI* (Key Performance Indicator), in a tabular model, is used to gauge performance of a value, defined by a *Base* measure, against a *Target* value, also defined by a measure or by an absolute value.</span></span> <span data-ttu-id="ff391-104">このトピックは、テーブル モデル作成者が表形式モデルの KPI の基本を理解できることを目的としています。</span><span class="sxs-lookup"><span data-stu-id="ff391-104">This topic provides tabular model authors a basic understanding of KPIs in a tabular model.</span></span>  
  
 <span data-ttu-id="ff391-105">このトピックのセクション:</span><span class="sxs-lookup"><span data-stu-id="ff391-105">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="ff391-106">メリット</span><span class="sxs-lookup"><span data-stu-id="ff391-106">Benefits</span></span>](#bkmk_benefits)  
  
-   [<span data-ttu-id="ff391-107">例</span><span class="sxs-lookup"><span data-stu-id="ff391-107">Example</span></span>](#bkmk_example)  
  
-   [<span data-ttu-id="ff391-108">Kpi の作成と編集</span><span class="sxs-lookup"><span data-stu-id="ff391-108">Create and Edit KPIs</span></span>](#bkmk_create)  
  
-   [<span data-ttu-id="ff391-109">関連タスク</span><span class="sxs-lookup"><span data-stu-id="ff391-109">Related Tasks</span></span>](#bkmk_related_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_benefits"></a> <span data-ttu-id="ff391-110">利点</span><span class="sxs-lookup"><span data-stu-id="ff391-110">Benefits</span></span>  
 <span data-ttu-id="ff391-111">ビジネス用語では、主要業績評価指標 (KPI) とは、ビジネス目標を判断するための測定値のことです。</span><span class="sxs-lookup"><span data-stu-id="ff391-111">In business terminology, a Key Performance Indicator (KPI) is a quantifiable measurement for gauging business objectives.</span></span> <span data-ttu-id="ff391-112">KPI は一定期間中頻繁に評価されます。</span><span class="sxs-lookup"><span data-stu-id="ff391-112">A KPI is frequently evaluated over time.</span></span> <span data-ttu-id="ff391-113">たとえば、組織の営業部門では KPI を使用して予測総利益に対する月間売上総利益を測定できます。</span><span class="sxs-lookup"><span data-stu-id="ff391-113">For example, the sales department of an organization may use a KPI to measure monthly gross profit against projected gross profit.</span></span> <span data-ttu-id="ff391-114">経理部門では、月間の収入に対する支出を測定してコストを評価し、人事部門では、四半期単位の従業員離職率を測定することができます。</span><span class="sxs-lookup"><span data-stu-id="ff391-114">The accounting department may measure monthly expenditures against revenue to evaluate costs, and a human resources department may measure quarterly employee turnover.</span></span> <span data-ttu-id="ff391-115">これらはそれぞれ KPI の一例です。</span><span class="sxs-lookup"><span data-stu-id="ff391-115">Each is an example of a KPI.</span></span> <span data-ttu-id="ff391-116">企業のプロフェッショナルは、グループにまとめて事業のスコアカードに記録した KPI を頻繁に使用し、事業の成功度の履歴要約をすばやく正確に取得したり、傾向を把握したりします。</span><span class="sxs-lookup"><span data-stu-id="ff391-116">Business professionals frequently consume KPIs that are grouped together in a business scorecard to obtain a quick and accurate historical summary of business success or to identify trends.</span></span>  
  
 <span data-ttu-id="ff391-117">表形式モデルの KPI には次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ff391-117">A KPI in a tabular model includes:</span></span>  
  
 <span data-ttu-id="ff391-118">**ベース値**</span><span class="sxs-lookup"><span data-stu-id="ff391-118">**Base Value**</span></span>  
 <span data-ttu-id="ff391-119">ベース値は、値に解決されるメジャーによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff391-119">A Base value is defined by a measure that resolves to a value.</span></span> <span data-ttu-id="ff391-120">ベース値には、実績販売の集計や、特定期間の利益などの計算メジャーなどを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ff391-120">This value, for example, can be an aggregate of actual Sales or a calculated measure such as Profit for a given period.</span></span>  
  
 <span data-ttu-id="ff391-121">**対象の値**</span><span class="sxs-lookup"><span data-stu-id="ff391-121">**Target value**</span></span>  
 <span data-ttu-id="ff391-122">対象の値は、値に解決されるメジャーまたは絶対値によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff391-122">A Target value is defined by a measure that resolves to a value, or by an absolute value.</span></span> <span data-ttu-id="ff391-123">たとえば、組織の経営層が目標とする売上または利益の増加額を対象の値にすることができます。</span><span class="sxs-lookup"><span data-stu-id="ff391-123">For example, a target value could be the amount by which the business managers of an organization want to increase sales or profit.</span></span>  
  
 <span data-ttu-id="ff391-124">**状態のしきい値**</span><span class="sxs-lookup"><span data-stu-id="ff391-124">**Status thresholds**</span></span>  
 <span data-ttu-id="ff391-125">状態のしきい値は、低いしきい値と高いしきい値との間の範囲によって、または固定値によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff391-125">A Status threshold is defined by the range between a low and high threshold or by a fixed value.</span></span> <span data-ttu-id="ff391-126">状態のしきい値は、対象の値と比べたベース値の状態を簡単に判別できるようにグラフィックで表示されます。</span><span class="sxs-lookup"><span data-stu-id="ff391-126">The Status threshold displays with a graphic to help users easily determine the status of the Base value compared to the Target value.</span></span>  
  
##  <a name="example"></a><a name="bkmk_example"></a> <span data-ttu-id="ff391-127">例</span><span class="sxs-lookup"><span data-stu-id="ff391-127">Example</span></span>  
 <span data-ttu-id="ff391-128">Adventure Works の販売責任者は、販売担当者の一定期間 (年) の販売ノルマの達成状況がひとめでわかるようなピボットテーブルを作成しようとしています。</span><span class="sxs-lookup"><span data-stu-id="ff391-128">The sales manager at Adventure Works wants to create a PivotTable that she can use to quickly display whether or not sales employees are meeting their sales quota for a given period (year).</span></span> <span data-ttu-id="ff391-129">各営業担当者に対して、ピボットテーブルに実際の販売量をドル単位で表示し、販売ノルマの金額をドル単位で表示し、各販売員が販売ノルマを下回っているか、上回るか、または上回っているかを示す簡単なグラフィックを表示したいと考えています。</span><span class="sxs-lookup"><span data-stu-id="ff391-129">For each sales employee, she wants the PivotTable to display the actual sales amount in dollars, the sales quota amount in dollars, and a simple graphic display showing the status of whether or not each sales employee is below, at, or above their sales quota.</span></span> <span data-ttu-id="ff391-130">データは年単位でスライスできるようにしたいと考えています。</span><span class="sxs-lookup"><span data-stu-id="ff391-130">She wants to be able to slice the data by year.</span></span>  
  
 <span data-ttu-id="ff391-131">これを行うために、営業課長は、組織の BI ソリューション開発者に対して、AdventureWorks テーブルモデルに Sales KPI を追加するための支援を参加させます。</span><span class="sxs-lookup"><span data-stu-id="ff391-131">To do this, the sales manager enlists the help of her organization's BI solution developer to add a Sales KPI to the AdventureWorks Tabular Model.</span></span> <span data-ttu-id="ff391-132">次に、 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] を使用してデータ ソースの Adventure Works 表形式モデルに接続し、ピボットテーブルを作成してフィールド (メジャーと KPI) およびスライサーを設定し、販売担当者がノルマを達成したかどうかを分析します。</span><span class="sxs-lookup"><span data-stu-id="ff391-132">The sales manager will then use [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] to connect to the Adventure Works Tabular Model as a data source and create a PivotTable with the fields (measures and KPI) and slicers to analyze whether or not the sales force is meeting their quotas.</span></span>  
  
 <span data-ttu-id="ff391-133">モデルの FactResellerSales テーブルの SalesAmount 列に、各販売担当者の実績販売額をドル単位で表すメジャーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ff391-133">In the model, a measure on the SalesAmount column in the FactResellerSales table, which gives the actual sales amount in dollars for each sales employee is created.</span></span> <span data-ttu-id="ff391-134">このメジャーは KPI のベース値を定義します。</span><span class="sxs-lookup"><span data-stu-id="ff391-134">This measure will define the Base value of the KPI.</span></span>  
  
 <span data-ttu-id="ff391-135">次の式で販売メジャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="ff391-135">The Sales measure is created with the following formula:</span></span>  
  
```  
Sales:=Sum(FactResellerSales[SalesAmount])  
```  
  
 <span data-ttu-id="ff391-136">FactSalesQuota テーブルの SalesAmountQuota 列には、各担当者の販売ノルマが定義されています。</span><span class="sxs-lookup"><span data-stu-id="ff391-136">The SalesAmountQuota column in the FactSalesQuota table has a sales amount quota defined for each employee.</span></span> <span data-ttu-id="ff391-137">この列の値が KPI の対象のメジャー (値) になります。</span><span class="sxs-lookup"><span data-stu-id="ff391-137">The values in this column will serve as the Target measure (value) in the KPI.</span></span>  
  
 <span data-ttu-id="ff391-138">次の式で SalesAmountQuota メジャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="ff391-138">The SalesAmountQuota measure is created with the following formula:</span></span>  
  
```  
Target SalesAmountQuota:=Sum(FactSalesQuota[SalesAmountQuota])  
```  
  
> [!NOTE]  
>  <span data-ttu-id="ff391-139">FactSalesQuota テーブルの EmployeeKey 列と DimEmployees テーブルの EmployeeKey 列との間にリレーションシップがあります。</span><span class="sxs-lookup"><span data-stu-id="ff391-139">There is a relationship between the EmployeeKey column in the FactSalesQuota table and the EmployeeKey in the DimEmployees table.</span></span> <span data-ttu-id="ff391-140">このリレーションシップは、DimEmployee テーブルの各販売担当者を FactSalesQuota テーブルで表すために必要です。</span><span class="sxs-lookup"><span data-stu-id="ff391-140">This relationship is necessary so that each sales employee in the DimEmployee table is represented in the FactSalesQuota table.</span></span>  
  
 <span data-ttu-id="ff391-141">KPI のベース値および対象の値となるメジャーを作成した後は、販売メジャーを新しい販売 KPI に拡張します。</span><span class="sxs-lookup"><span data-stu-id="ff391-141">Now that measures have been created to serve as the Base value and Target value of the KPI, the Sales measure is extended to a new Sales KPI.</span></span> <span data-ttu-id="ff391-142">販売 KPI では、ターゲットの SalesAmountQuota メジャーが対象の値として定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff391-142">In the Sales KPI, the Target SalesAmountQuota measure is defined as the Target value.</span></span> <span data-ttu-id="ff391-143">状態のしきい値はパーセンテージ範囲によって定義されます。ターゲットが 100% の場合、販売メジャーによって定義された実績販売額がターゲットの SalesAmoutnQuota メジャーで定義されたノルマに達したことを意味します。</span><span class="sxs-lookup"><span data-stu-id="ff391-143">The Status threshold is defined as a range by percentage, the target of which is 100% meaning actual sales defined by the Sales measure met the quota amount defined in the Target SalesAmoutnQuota measure.</span></span> <span data-ttu-id="ff391-144">[低] および [高] のパーセンテージはステータス バーで定義され、グラフィックの種類が選択されます。</span><span class="sxs-lookup"><span data-stu-id="ff391-144">Low and High percentages are defined on the status bar, and a graphic type is selected.</span></span>  
  
 <span data-ttu-id="ff391-145">Sales manager は、KPI のベース値、対象の値、状態を [値] フィールドに追加するピボットテーブルを作成できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ff391-145">The sales manager can now create a PivotTable adding the KPI's Base value, Target value, and Status to the Values field.</span></span> <span data-ttu-id="ff391-146">Employees 列を RowLabel フィールドに追加し、CalendarYear 列をスライサーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="ff391-146">The Employees column is added to the RowLabel field, and the CalendarYear column is added as a Slicer.</span></span>  
  
 <span data-ttu-id="ff391-147">販売責任者は、各販売担当者の実績販売額、販売ノルマ、状態を年単位でスライスできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ff391-147">The sales manager can now slice by year the actual sales amount, sales quota amount, and status for each sales employee.</span></span> <span data-ttu-id="ff391-148">これによって数年間の売上傾向を分析し、販売担当者の販売ノルマを調整する必要があるかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="ff391-148">She can analyze sales trends over years to determine whether or not she needs to adjust the sales quota for a sales employee.</span></span>  
  
##  <a name="create-and-edit-kpis"></a><a name="bkmk_create"></a><span data-ttu-id="ff391-149">Kpi の作成と編集</span><span class="sxs-lookup"><span data-stu-id="ff391-149">Create and Edit KPIs</span></span>  
 <span data-ttu-id="ff391-150">KPI を作成するには、モデル デザイナーの [主要業績評価指標] ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="ff391-150">To create KPIs, in the model designer, you will use the Key Performance Indicator dialog box.</span></span> <span data-ttu-id="ff391-151">KPI はメジャーと関連付ける必要があるため、ベース値を評価するメジャーを拡張してから、対象の値を評価するメジャーを作成するか、絶対値を入力することにより、KPI を作成します。</span><span class="sxs-lookup"><span data-stu-id="ff391-151">Since KPIs must be associated with a measure, you create a KPI by extending a measure that evaluates to a Base value, and then either creating a measure that evaluates to a Target value or by entering an absolute value.</span></span> <span data-ttu-id="ff391-152">ベース メジャー (値) および対象の値が定義された後、状態のしきい値のパラメーターをベース値と対象の値の間で定義できます。</span><span class="sxs-lookup"><span data-stu-id="ff391-152">After the Base measure (value) and Target value is defined, you can then define the status threshold parameters between the Base and Target values.</span></span> <span data-ttu-id="ff391-153">状態は、選択可能なアイコン、バー、グラフ、または色を使用して、グラフィカルな形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="ff391-153">The status is displayed in a graphical format using selectable icons, bars, graphs, or colors.</span></span> <span data-ttu-id="ff391-154">ベース値および対象の値は、状態と同様に、他のデータ フィールドに対してスライスできる値として、レポートまたはピボットテーブルに追加できます。</span><span class="sxs-lookup"><span data-stu-id="ff391-154">The Base and Target values, as well as the Status can then be added to a report or PivotTable as values that can be sliced against other data fields.</span></span>  
  
 <span data-ttu-id="ff391-155">[主要業績評価指標] ダイアログ ボックスを表示するには、テーブルのメジャー グリッドで、ベース値として機能するメジャーを右クリックし、 **[KPI の作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff391-155">To view the Key Performance Indicator dialog box, in the measure grid for a table, right click a measure that will serve as the Base value, and then click **Create KPI**.</span></span> <span data-ttu-id="ff391-156">ベース値としての KPI にメジャーが拡張された後、メジャー グリッドのメジャー名の横にアイコンが表示され、メジャーが KPI に関連付けられていることを示します。</span><span class="sxs-lookup"><span data-stu-id="ff391-156">After a measure has been extended to a KPI as a Base value, an icon will appear alongside the measure name in the measure grid identifying the measure as associated with a KPI.</span></span>  
  
##  <a name="related-tasks"></a><a name="bkmk_related_tasks"></a> <span data-ttu-id="ff391-157">関連タスク</span><span class="sxs-lookup"><span data-stu-id="ff391-157">Related Tasks</span></span>  
  
|<span data-ttu-id="ff391-158">トピック</span><span class="sxs-lookup"><span data-stu-id="ff391-158">Topic</span></span>|<span data-ttu-id="ff391-159">説明</span><span class="sxs-lookup"><span data-stu-id="ff391-159">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ff391-160">KPI を作成および管理する (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="ff391-160">Create and Manage KPIs &#40;SSAS Tabular&#41;</span></span>](kpis-ssas-tabular.md)|<span data-ttu-id="ff391-161">ベース メジャー、対象のメジャー、および状態のしきい値と共に KPI を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ff391-161">Describes how to create a KPI with a Base measure, a Target measure, and status thresholds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff391-162">参照</span><span class="sxs-lookup"><span data-stu-id="ff391-162">See Also</span></span>  
 <span data-ttu-id="ff391-163">[SSAS テーブル&#41;&#40;メジャー](measures-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="ff391-163">[Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="ff391-164">パースペクティブ &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="ff391-164">Perspectives &#40;SSAS Tabular&#41;</span></span>](perspectives-ssas-tabular.md)  
  
  
