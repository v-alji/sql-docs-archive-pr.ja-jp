---
title: 一般的に使用されるフィルター (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- multivalued parameters [Reporting Services]
- single-valued parameters [Reporting Services]
- parameters [Reporting Services], multivalued
- valid values [Reporting Services]
ms.assetid: cb70d0cd-707b-4de5-b39f-e4eb57d316aa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 201cf83d431d1b61e0f20e9d039b2016ad4f13e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641460"
---
# <a name="commonly-used-filters-report-builder-and-ssrs"></a><span data-ttu-id="151f2-102">一般的に使用されるフィルター (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="151f2-102">Commonly Used Filters (Report Builder and SSRS)</span></span>
  <span data-ttu-id="151f2-103">フィルターを作成するには、1 つ以上のフィルター式を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="151f2-103">To create a filter, you must specify one or more filter equations.</span></span> <span data-ttu-id="151f2-104">フィルター式には、式、データ型、演算子、および値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="151f2-104">A filter equation includes an expression, a data type, an operator, and a value.</span></span> <span data-ttu-id="151f2-105">ここでは、一般的に使用されるフィルターの例を示します。</span><span class="sxs-lookup"><span data-stu-id="151f2-105">This topic provides examples of commonly used filters.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="filter-examples"></a><span data-ttu-id="151f2-106">フィルターの例</span><span class="sxs-lookup"><span data-stu-id="151f2-106">Filter Examples</span></span>  
 <span data-ttu-id="151f2-107">次の表は、さまざまなデータ型と演算子を使用するフィルター式の例を示します。</span><span class="sxs-lookup"><span data-stu-id="151f2-107">The following table shows examples of filter equations that use different data types and different operators.</span></span> <span data-ttu-id="151f2-108">比較のスコープは、フィルターが定義されたレポート アイテムによって決まります。</span><span class="sxs-lookup"><span data-stu-id="151f2-108">The scope for the comparison is determined by report item for which a filter is defined.</span></span> <span data-ttu-id="151f2-109">たとえば、データセットに定義されたフィルターの場合、 **[上位 10%]** はデータセットの値の上位 10% になります。グループに定義されたフィルターの場合、 **[上位 10%]** はグループの値の上位 10% になります。</span><span class="sxs-lookup"><span data-stu-id="151f2-109">For example, for a filter defined on a dataset, **TOP % 10** is the top 10 percent of values in the dataset; for a filter defined on a group, **TOP % 10** is the top 10 percent of values in the group.</span></span>  
  
|<span data-ttu-id="151f2-110">単純式</span><span class="sxs-lookup"><span data-stu-id="151f2-110">Simple Expression</span></span>|<span data-ttu-id="151f2-111">データ型</span><span class="sxs-lookup"><span data-stu-id="151f2-111">Data Type</span></span>|<span data-ttu-id="151f2-112">演算子</span><span class="sxs-lookup"><span data-stu-id="151f2-112">Operator</span></span>|<span data-ttu-id="151f2-113">値</span><span class="sxs-lookup"><span data-stu-id="151f2-113">Value</span></span>|<span data-ttu-id="151f2-114">説明</span><span class="sxs-lookup"><span data-stu-id="151f2-114">Description</span></span>|  
|-----------------------|---------------|--------------|-----------|-----------------|  
|`[SUM(Quantity)]`|`Integer`|`>`|`7`|<span data-ttu-id="151f2-115">7 より大きいデータ値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="151f2-115">Includes data values that are greater than 7.</span></span>|  
|`[SUM(Quantity)]`|`Integer`|`TOP N`|`10`|<span data-ttu-id="151f2-116">上位 10 データ値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="151f2-116">Includes the top 10 data values.</span></span>|  
|`[SUM(Quantity)]`|`Integer`|`TOP %`|`20`|<span data-ttu-id="151f2-117">上位 20% のデータ値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="151f2-117">Includes the top 20% of data values.</span></span>|  
|`[Sales]`|`Text`|`>`|`=CDec(100)`|<span data-ttu-id="151f2-118">$100 より大きい System.Decimal 型 (SQL "money" データ型) のすべての値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="151f2-118">Includes all values of type System.Decimal (SQL "money" data types) greater than $100.</span></span>|  
|`[OrderDate]`|`DateTime`|`>`|`2088-01-01`|<span data-ttu-id="151f2-119">2008 年 1 月 1 日から現在の日付までのすべての日付が含まれます。</span><span class="sxs-lookup"><span data-stu-id="151f2-119">Includes all dates from January 1, 2008 to the present date.</span></span>|  
|`[OrderDate]`|`DateTime`|`BETWEEN`|`2008-01-01`<br /><br /> `2008-02-01`|<span data-ttu-id="151f2-120">2008 年 1 月 1 日から 2008 年 2 月 1 日までの日付が含まれます。</span><span class="sxs-lookup"><span data-stu-id="151f2-120">Includes dates from January 1, 2008 up to and including February 1, 2008.</span></span>|  
|`[Territory]`|`Text`|`LIKE`|`*east`|<span data-ttu-id="151f2-121">最後に "east" が付くすべての販売区域名。</span><span class="sxs-lookup"><span data-stu-id="151f2-121">All territory names that end in "east".</span></span>|  
|`[Territory]`|`Text`|`LIKE`|`%o%th*`|<span data-ttu-id="151f2-122">名前の先頭に North と South が含まれるすべての販売区域名。</span><span class="sxs-lookup"><span data-stu-id="151f2-122">All territory names that include North and South at the beginning of the name.</span></span>|  
|`=LEFT(Fields!Subcat.Value,1)`|`Text`|`IN`|`B, C, T`|<span data-ttu-id="151f2-123">B、C、T のいずれかの文字で始まるすべてのサブカテゴリ値。</span><span class="sxs-lookup"><span data-stu-id="151f2-123">All subcategory values that begin with the letters B, C, or T.</span></span>|  
  
## <a name="examples-with-report-parameters"></a><span data-ttu-id="151f2-124">レポート パラメーターの例</span><span class="sxs-lookup"><span data-stu-id="151f2-124">Examples with Report Parameters</span></span>  
 <span data-ttu-id="151f2-125">次の表は、単一値か複数値のパラメーター参照を含むフィルター式の例を示します。</span><span class="sxs-lookup"><span data-stu-id="151f2-125">The following table provides examples of filter expression that includes a single-value or multivalue parameter reference.</span></span>  
  
|<span data-ttu-id="151f2-126">パラメーターのタイプ</span><span class="sxs-lookup"><span data-stu-id="151f2-126">Parameter type</span></span>|<span data-ttu-id="151f2-127">(フィルター) 式</span><span class="sxs-lookup"><span data-stu-id="151f2-127">(Filter) Expression</span></span>|<span data-ttu-id="151f2-128">演算子</span><span class="sxs-lookup"><span data-stu-id="151f2-128">Operator</span></span>|<span data-ttu-id="151f2-129">値</span><span class="sxs-lookup"><span data-stu-id="151f2-129">Value</span></span>|<span data-ttu-id="151f2-130">データ型</span><span class="sxs-lookup"><span data-stu-id="151f2-130">Data Type</span></span>|  
|--------------------|---------------------------|--------------|-----------|---------------|  
|<span data-ttu-id="151f2-131">単一値</span><span class="sxs-lookup"><span data-stu-id="151f2-131">Single value</span></span>|`[EmployeeID]`|=|`[@EmployeeID]`|<span data-ttu-id="151f2-132">Integer</span><span class="sxs-lookup"><span data-stu-id="151f2-132">Integer</span></span>|  
|<span data-ttu-id="151f2-133">MultiValue</span><span class="sxs-lookup"><span data-stu-id="151f2-133">Multivalue</span></span>|`[EmployeeID]`|<span data-ttu-id="151f2-134">IN</span><span class="sxs-lookup"><span data-stu-id="151f2-134">IN</span></span>|`[@EmployeeID]`|<span data-ttu-id="151f2-135">Integer</span><span class="sxs-lookup"><span data-stu-id="151f2-135">Integer</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="151f2-136">参照</span><span class="sxs-lookup"><span data-stu-id="151f2-136">See Also</span></span>  
 <span data-ttu-id="151f2-137">[レポートパラメーター &#40;レポートビルダーとレポートデザイナー&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="151f2-137">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="151f2-138">[データセットフィルター、データ領域フィルター、およびグループフィルターを追加 &#40;レポートビルダーと SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="151f2-138">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="151f2-139">[レポートでの式の使用 &#40;レポートビルダーと SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="151f2-139">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="151f2-140">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="151f2-140">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="151f2-141">式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="151f2-141">Data Types in Expressions &#40;Report Builder and SSRS&#41;</span></span>](expressions-report-builder-and-ssrs.md)  
  
  
