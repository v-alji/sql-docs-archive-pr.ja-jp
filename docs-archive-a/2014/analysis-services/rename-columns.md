---
title: 'レッスン 3: 列名の変更 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5fc8ba1a-2b30-4775-9b3b-c09dee711b3e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 59904f1110455b65679b3d19e6e8b7c731465ee9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631255"
---
# <a name="lesson-3-rename-columns"></a><span data-ttu-id="afad6-102">レッスン 3:列名の変更</span><span class="sxs-lookup"><span data-stu-id="afad6-102">Lesson 3: Rename Columns</span></span>
  <span data-ttu-id="afad6-103">このレッスンでは、インポートした各テーブル内の多くの列の名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="afad6-103">In this lesson, you will rename many of the columns in each table you imported.</span></span> <span data-ttu-id="afad6-104">名前を変更することで、列がより識別しやすくなり、モデル デザイナー内でも、またクライアント アプリケーションでユーザーがフィールドを選択する際にも、移動が行いやすくなります。</span><span class="sxs-lookup"><span data-stu-id="afad6-104">Renaming makes columns more identifiable and easier to navigate in both the model designer as well by users selecting fields in a client application.</span></span> <span data-ttu-id="afad6-105">詳細については、「[テーブルまたは列名の変更 (SSAS テーブル)](tabular-models/rename-a-table-or-column-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afad6-105">To learn more, see [Rename a Table or Column &#40;SSAS Tabular&#41;](tabular-models/rename-a-table-or-column-ssas-tabular.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="afad6-106">列名の変更は、このチュートリアルを完了するために必ずしも必要ではありませんが、残りのレッスン (リレーションシップを作成するレッスンと、DAX 数式を使用して計算列とメジャーを作成するレッスン) では、このレッスンに記載されているわかりやすい列名が使用されます。</span><span class="sxs-lookup"><span data-stu-id="afad6-106">Renaming columns is not necessary to complete this tutorial; however, remaining lessons, in particular those that include creating relationships and creating calculated columns and measures using DAX formulas, refer to the column friendly names described in this lesson.</span></span> <span data-ttu-id="afad6-107">列名を変更しない場合は、レッスン 5、6、および 7 を行う際に、このレッスンで示す元のソース列名を使用するように DAX 数式を編集してください。</span><span class="sxs-lookup"><span data-stu-id="afad6-107">If you choose not to rename columns, you will have to edit the DAX formulas in lessons 5, 6, and 7 to use the original source column names provided in this lesson.</span></span>  
  
 <span data-ttu-id="afad6-108">このレッスンの推定所要時間: **20 分**</span><span class="sxs-lookup"><span data-stu-id="afad6-108">Estimated time to complete this lesson: **20 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="afad6-109">前提条件</span><span class="sxs-lookup"><span data-stu-id="afad6-109">Prerequisites</span></span>  
 <span data-ttu-id="afad6-110">このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="afad6-110">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="afad6-111">このレッスンの実習を行う前に、前のレッスン「 [レッスン 2: データの追加](lesson-2-add-data.md)」を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="afad6-111">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 2: Add Data](lesson-2-add-data.md).</span></span>  
  
## <a name="rename-columns"></a><span data-ttu-id="afad6-112">列名の変更</span><span class="sxs-lookup"><span data-stu-id="afad6-112">Rename Columns</span></span>  
  
#### <a name="to-rename-columns"></a><span data-ttu-id="afad6-113">列名を変更するには</span><span class="sxs-lookup"><span data-stu-id="afad6-113">To rename columns</span></span>  
  
1.  <span data-ttu-id="afad6-114">モデル デザイナーで、 **Customer** テーブル (タブ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="afad6-114">In the model designer, click the **Customer** table (tab).</span></span>  
  
     <span data-ttu-id="afad6-115">タブをクリックすると、そのテーブルがモデル デザイナー ウィンドウでアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="afad6-115">When you click a tab, that table becomes active in the model designer window.</span></span>  
  
2.  <span data-ttu-id="afad6-116">[**顧客キー** ] 列の名前をダブルクリックし、「」と入力して `Customer  Id` 、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="afad6-116">Double click the **CustomerKey** column name, then type `Customer  Id`, and then press ENTER.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="afad6-117">列の名前を変更するには、列の [**プロパティ**] ウィンドウまたはダイアグラムビューの [**列名**] プロパティを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="afad6-117">You can also rename a column in the **Column Name** property in the column's **Properties** window, or in Diagram View.</span></span>  
  
3.  <span data-ttu-id="afad6-118">**Customer** テーブル内の残りの列と、その他のテーブル内の列についても、ソース名を次の表示名に置き換えて名前変更します。</span><span class="sxs-lookup"><span data-stu-id="afad6-118">Rename the remaining columns in the **Customer** table, as well as the columns in the remaining tables, replacing the source name with the friendly name:</span></span>  
  
     <span data-ttu-id="afad6-119">**Customer テーブル**</span><span class="sxs-lookup"><span data-stu-id="afad6-119">**Customer Table**</span></span>  
  
    |<span data-ttu-id="afad6-120">ソース名</span><span class="sxs-lookup"><span data-stu-id="afad6-120">Source Name</span></span>|<span data-ttu-id="afad6-121">フレンドリ名</span><span class="sxs-lookup"><span data-stu-id="afad6-121">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="afad6-122">GeographyKey</span><span class="sxs-lookup"><span data-stu-id="afad6-122">GeographyKey</span></span>|<span data-ttu-id="afad6-123">[Geography Id]</span><span class="sxs-lookup"><span data-stu-id="afad6-123">Geography Id</span></span>|  
    |<span data-ttu-id="afad6-124">CustomerAlternateKey</span><span class="sxs-lookup"><span data-stu-id="afad6-124">CustomerAlternateKey</span></span>|<span data-ttu-id="afad6-125">Customer Alternate Id</span><span class="sxs-lookup"><span data-stu-id="afad6-125">Customer Alternate Id</span></span>|  
    |<span data-ttu-id="afad6-126">FirstName</span><span class="sxs-lookup"><span data-stu-id="afad6-126">FirstName</span></span>|<span data-ttu-id="afad6-127">名</span><span class="sxs-lookup"><span data-stu-id="afad6-127">First Name</span></span>|  
    |<span data-ttu-id="afad6-128">MiddleName</span><span class="sxs-lookup"><span data-stu-id="afad6-128">MiddleName</span></span>|<span data-ttu-id="afad6-129">Middle Name</span><span class="sxs-lookup"><span data-stu-id="afad6-129">Middle Name</span></span>|  
    |<span data-ttu-id="afad6-130">LastName</span><span class="sxs-lookup"><span data-stu-id="afad6-130">LastName</span></span>|<span data-ttu-id="afad6-131">姓</span><span class="sxs-lookup"><span data-stu-id="afad6-131">Last Name</span></span>|  
    |<span data-ttu-id="afad6-132">NameStyle</span><span class="sxs-lookup"><span data-stu-id="afad6-132">NameStyle</span></span>|<span data-ttu-id="afad6-133">Name Style</span><span class="sxs-lookup"><span data-stu-id="afad6-133">Name Style</span></span>|  
    |<span data-ttu-id="afad6-134">BirthDate</span><span class="sxs-lookup"><span data-stu-id="afad6-134">BirthDate</span></span>|<span data-ttu-id="afad6-135">[Birth Date]</span><span class="sxs-lookup"><span data-stu-id="afad6-135">Birth Date</span></span>|  
    |<span data-ttu-id="afad6-136">MaritalStatus</span><span class="sxs-lookup"><span data-stu-id="afad6-136">MaritalStatus</span></span>|<span data-ttu-id="afad6-137">Marital Status</span><span class="sxs-lookup"><span data-stu-id="afad6-137">Marital Status</span></span>|  
    |<span data-ttu-id="afad6-138">EmailAddress</span><span class="sxs-lookup"><span data-stu-id="afad6-138">EmailAddress</span></span>|<span data-ttu-id="afad6-139">電子メール アドレス</span><span class="sxs-lookup"><span data-stu-id="afad6-139">Email Address</span></span>|  
    |<span data-ttu-id="afad6-140">YearlyIncome</span><span class="sxs-lookup"><span data-stu-id="afad6-140">YearlyIncome</span></span>|<span data-ttu-id="afad6-141">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="afad6-141">Yearly Income</span></span>|  
    |<span data-ttu-id="afad6-142">TotalChildren</span><span class="sxs-lookup"><span data-stu-id="afad6-142">TotalChildren</span></span>|<span data-ttu-id="afad6-143">Total Children</span><span class="sxs-lookup"><span data-stu-id="afad6-143">Total Children</span></span>|  
    |<span data-ttu-id="afad6-144">NumberChildrenAtHome</span><span class="sxs-lookup"><span data-stu-id="afad6-144">NumberChildrenAtHome</span></span>|<span data-ttu-id="afad6-145">Number of Children At Home</span><span class="sxs-lookup"><span data-stu-id="afad6-145">Number of Children At Home</span></span>|  
    |<span data-ttu-id="afad6-146">EnglishEducation</span><span class="sxs-lookup"><span data-stu-id="afad6-146">EnglishEducation</span></span>|<span data-ttu-id="afad6-147">Education</span><span class="sxs-lookup"><span data-stu-id="afad6-147">Education</span></span>|  
    |<span data-ttu-id="afad6-148">EnglishOccupation</span><span class="sxs-lookup"><span data-stu-id="afad6-148">EnglishOccupation</span></span>|<span data-ttu-id="afad6-149">Occupation</span><span class="sxs-lookup"><span data-stu-id="afad6-149">Occupation</span></span>|  
    |<span data-ttu-id="afad6-150">HouseOwnerFlag</span><span class="sxs-lookup"><span data-stu-id="afad6-150">HouseOwnerFlag</span></span>|<span data-ttu-id="afad6-151">Owns House</span><span class="sxs-lookup"><span data-stu-id="afad6-151">Owns House</span></span>|  
    |<span data-ttu-id="afad6-152">NumberCarsOwned</span><span class="sxs-lookup"><span data-stu-id="afad6-152">NumberCarsOwned</span></span>|<span data-ttu-id="afad6-153">Number of Cars Owned</span><span class="sxs-lookup"><span data-stu-id="afad6-153">Number of Cars Owned</span></span>|  
    |<span data-ttu-id="afad6-154">AddressLine1</span><span class="sxs-lookup"><span data-stu-id="afad6-154">AddressLine1</span></span>|<span data-ttu-id="afad6-155">Address Line 1</span><span class="sxs-lookup"><span data-stu-id="afad6-155">Address Line 1</span></span>|  
    |<span data-ttu-id="afad6-156">AddressLine2</span><span class="sxs-lookup"><span data-stu-id="afad6-156">AddressLine2</span></span>|<span data-ttu-id="afad6-157">Address Line 2</span><span class="sxs-lookup"><span data-stu-id="afad6-157">Address Line 2</span></span>|  
    |<span data-ttu-id="afad6-158">Phone</span><span class="sxs-lookup"><span data-stu-id="afad6-158">Phone</span></span>|<span data-ttu-id="afad6-159">電話番号</span><span class="sxs-lookup"><span data-stu-id="afad6-159">Phone Number</span></span>|  
    |<span data-ttu-id="afad6-160">DateFirstPurchase</span><span class="sxs-lookup"><span data-stu-id="afad6-160">DateFirstPurchase</span></span>|<span data-ttu-id="afad6-161">Date of First Purchase</span><span class="sxs-lookup"><span data-stu-id="afad6-161">Date of First Purchase</span></span>|  
    |<span data-ttu-id="afad6-162">CommuteDistance</span><span class="sxs-lookup"><span data-stu-id="afad6-162">CommuteDistance</span></span>|<span data-ttu-id="afad6-163">Commute Distance</span><span class="sxs-lookup"><span data-stu-id="afad6-163">Commute Distance</span></span>|  
  
     <span data-ttu-id="afad6-164">**日付**</span><span class="sxs-lookup"><span data-stu-id="afad6-164">**Date**</span></span>  
  
    |<span data-ttu-id="afad6-165">ソース名</span><span class="sxs-lookup"><span data-stu-id="afad6-165">Source Name</span></span>|<span data-ttu-id="afad6-166">フレンドリ名</span><span class="sxs-lookup"><span data-stu-id="afad6-166">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="afad6-167">FullDateAlternateKey</span><span class="sxs-lookup"><span data-stu-id="afad6-167">FullDateAlternateKey</span></span>|<span data-ttu-id="afad6-168">Date</span><span class="sxs-lookup"><span data-stu-id="afad6-168">Date</span></span>|  
    |<span data-ttu-id="afad6-169">DayNumberOfWeek</span><span class="sxs-lookup"><span data-stu-id="afad6-169">DayNumberOfWeek</span></span>|<span data-ttu-id="afad6-170">Day Number of Week</span><span class="sxs-lookup"><span data-stu-id="afad6-170">Day Number of Week</span></span>|  
    |<span data-ttu-id="afad6-171">EnglishDayNameOfWeek</span><span class="sxs-lookup"><span data-stu-id="afad6-171">EnglishDayNameOfWeek</span></span>|<span data-ttu-id="afad6-172">Day Name</span><span class="sxs-lookup"><span data-stu-id="afad6-172">Day Name</span></span>|  
    |<span data-ttu-id="afad6-173">DayNumberOfMonth</span><span class="sxs-lookup"><span data-stu-id="afad6-173">DayNumberOfMonth</span></span>|<span data-ttu-id="afad6-174">月の日付</span><span class="sxs-lookup"><span data-stu-id="afad6-174">Day of Month</span></span>|  
    |<span data-ttu-id="afad6-175">DayNumberOfYear</span><span class="sxs-lookup"><span data-stu-id="afad6-175">DayNumberOfYear</span></span>|<span data-ttu-id="afad6-176">年の通算日</span><span class="sxs-lookup"><span data-stu-id="afad6-176">Day of Year</span></span>|  
    |<span data-ttu-id="afad6-177">WeekNumberOfYear</span><span class="sxs-lookup"><span data-stu-id="afad6-177">WeekNumberOfYear</span></span>|<span data-ttu-id="afad6-178">Week Number of Year</span><span class="sxs-lookup"><span data-stu-id="afad6-178">Week Number of Year</span></span>|  
    |<span data-ttu-id="afad6-179">EnglishMonthName</span><span class="sxs-lookup"><span data-stu-id="afad6-179">EnglishMonthName</span></span>|<span data-ttu-id="afad6-180">月の名前</span><span class="sxs-lookup"><span data-stu-id="afad6-180">Month Name</span></span>|  
    |<span data-ttu-id="afad6-181">MonthNumberOfYear</span><span class="sxs-lookup"><span data-stu-id="afad6-181">MonthNumberOfYear</span></span>|<span data-ttu-id="afad6-182">Month</span><span class="sxs-lookup"><span data-stu-id="afad6-182">Month</span></span>|  
    |<span data-ttu-id="afad6-183">CalendarQuarter</span><span class="sxs-lookup"><span data-stu-id="afad6-183">CalendarQuarter</span></span>|<span data-ttu-id="afad6-184">Calendar Quarter</span><span class="sxs-lookup"><span data-stu-id="afad6-184">Calendar Quarter</span></span>|  
    |<span data-ttu-id="afad6-185">CalendarYear</span><span class="sxs-lookup"><span data-stu-id="afad6-185">CalendarYear</span></span>|<span data-ttu-id="afad6-186">Calendar Year</span><span class="sxs-lookup"><span data-stu-id="afad6-186">Calendar Year</span></span>|  
    |<span data-ttu-id="afad6-187">CalendarSemester</span><span class="sxs-lookup"><span data-stu-id="afad6-187">CalendarSemester</span></span>|<span data-ttu-id="afad6-188">Calendar Semester</span><span class="sxs-lookup"><span data-stu-id="afad6-188">Calendar Semester</span></span>|  
    |<span data-ttu-id="afad6-189">FiscalQuarter</span><span class="sxs-lookup"><span data-stu-id="afad6-189">FiscalQuarter</span></span>|<span data-ttu-id="afad6-190">Fiscal Quarter</span><span class="sxs-lookup"><span data-stu-id="afad6-190">Fiscal Quarter</span></span>|  
    |<span data-ttu-id="afad6-191">FiscalYear</span><span class="sxs-lookup"><span data-stu-id="afad6-191">FiscalYear</span></span>|<span data-ttu-id="afad6-192">Fiscal Year</span><span class="sxs-lookup"><span data-stu-id="afad6-192">Fiscal Year</span></span>|  
    |<span data-ttu-id="afad6-193">FiscalSemester</span><span class="sxs-lookup"><span data-stu-id="afad6-193">FiscalSemester</span></span>|<span data-ttu-id="afad6-194">Fiscal Semester</span><span class="sxs-lookup"><span data-stu-id="afad6-194">Fiscal Semester</span></span>|  
  
     <span data-ttu-id="afad6-195">**地理的な場所**</span><span class="sxs-lookup"><span data-stu-id="afad6-195">**Geography**</span></span>  
  
    |<span data-ttu-id="afad6-196">ソース名</span><span class="sxs-lookup"><span data-stu-id="afad6-196">Source Name</span></span>|<span data-ttu-id="afad6-197">フレンドリ名</span><span class="sxs-lookup"><span data-stu-id="afad6-197">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="afad6-198">GeographyKey</span><span class="sxs-lookup"><span data-stu-id="afad6-198">GeographyKey</span></span>|<span data-ttu-id="afad6-199">[Geography Id]</span><span class="sxs-lookup"><span data-stu-id="afad6-199">Geography Id</span></span>|  
    |<span data-ttu-id="afad6-200">StateProvinceCode</span><span class="sxs-lookup"><span data-stu-id="afad6-200">StateProvinceCode</span></span>|<span data-ttu-id="afad6-201">State Province Code</span><span class="sxs-lookup"><span data-stu-id="afad6-201">State Province Code</span></span>|  
    |<span data-ttu-id="afad6-202">StateProvinceName</span><span class="sxs-lookup"><span data-stu-id="afad6-202">StateProvinceName</span></span>|<span data-ttu-id="afad6-203">State Province Name</span><span class="sxs-lookup"><span data-stu-id="afad6-203">State Province Name</span></span>|  
    |<span data-ttu-id="afad6-204">CountryRegionCode</span><span class="sxs-lookup"><span data-stu-id="afad6-204">CountryRegionCode</span></span>|<span data-ttu-id="afad6-205">Country Region Code</span><span class="sxs-lookup"><span data-stu-id="afad6-205">Country Region Code</span></span>|  
    |<span data-ttu-id="afad6-206">EnglishCountryRegionName</span><span class="sxs-lookup"><span data-stu-id="afad6-206">EnglishCountryRegionName</span></span>|<span data-ttu-id="afad6-207">Country Region Name</span><span class="sxs-lookup"><span data-stu-id="afad6-207">Country Region Name</span></span>|  
    |<span data-ttu-id="afad6-208">郵便番号</span><span class="sxs-lookup"><span data-stu-id="afad6-208">PostalCode</span></span>|<span data-ttu-id="afad6-209">郵便番号</span><span class="sxs-lookup"><span data-stu-id="afad6-209">Postal Code</span></span>|  
    |<span data-ttu-id="afad6-210">SalesTerritoryKey</span><span class="sxs-lookup"><span data-stu-id="afad6-210">SalesTerritoryKey</span></span>|<span data-ttu-id="afad6-211">Sales Territory Id</span><span class="sxs-lookup"><span data-stu-id="afad6-211">Sales Territory Id</span></span>|  
  
     <span data-ttu-id="afad6-212">**Product**</span><span class="sxs-lookup"><span data-stu-id="afad6-212">**Product**</span></span>  
  
    |<span data-ttu-id="afad6-213">ソース名</span><span class="sxs-lookup"><span data-stu-id="afad6-213">Source Name</span></span>|<span data-ttu-id="afad6-214">フレンドリ名</span><span class="sxs-lookup"><span data-stu-id="afad6-214">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="afad6-215">ProductKey</span><span class="sxs-lookup"><span data-stu-id="afad6-215">ProductKey</span></span>|<span data-ttu-id="afad6-216">[Product Id]</span><span class="sxs-lookup"><span data-stu-id="afad6-216">Product Id</span></span>|  
    |<span data-ttu-id="afad6-217">ProductAlternateKey</span><span class="sxs-lookup"><span data-stu-id="afad6-217">ProductAlternateKey</span></span>|<span data-ttu-id="afad6-218">Product Alternate Id</span><span class="sxs-lookup"><span data-stu-id="afad6-218">Product Alternate Id</span></span>|  
    |<span data-ttu-id="afad6-219">ProductSubcategoryKey</span><span class="sxs-lookup"><span data-stu-id="afad6-219">ProductSubcategoryKey</span></span>|<span data-ttu-id="afad6-220">Product Subcategory Id</span><span class="sxs-lookup"><span data-stu-id="afad6-220">Product Subcategory Id</span></span>|  
    |<span data-ttu-id="afad6-221">WeightUnitMeasureCode</span><span class="sxs-lookup"><span data-stu-id="afad6-221">WeightUnitMeasureCode</span></span>|<span data-ttu-id="afad6-222">Weight Unit Code</span><span class="sxs-lookup"><span data-stu-id="afad6-222">Weight Unit Code</span></span>|  
    |<span data-ttu-id="afad6-223">SizeUnitMeasureCode</span><span class="sxs-lookup"><span data-stu-id="afad6-223">SizeUnitMeasureCode</span></span>|<span data-ttu-id="afad6-224">Size Unit Code</span><span class="sxs-lookup"><span data-stu-id="afad6-224">Size Unit Code</span></span>|  
    |<span data-ttu-id="afad6-225">EnglishProductName</span><span class="sxs-lookup"><span data-stu-id="afad6-225">EnglishProductName</span></span>|<span data-ttu-id="afad6-226">製品名</span><span class="sxs-lookup"><span data-stu-id="afad6-226">Product Name</span></span>|  
    |<span data-ttu-id="afad6-227">StandardCost</span><span class="sxs-lookup"><span data-stu-id="afad6-227">StandardCost</span></span>|<span data-ttu-id="afad6-228">Standard Cost</span><span class="sxs-lookup"><span data-stu-id="afad6-228">Standard Cost</span></span>|  
    |<span data-ttu-id="afad6-229">FinishedGoodsFlag</span><span class="sxs-lookup"><span data-stu-id="afad6-229">FinishedGoodsFlag</span></span>|<span data-ttu-id="afad6-230">Is Finished Product</span><span class="sxs-lookup"><span data-stu-id="afad6-230">Is Finished Product</span></span>|  
    |<span data-ttu-id="afad6-231">SafetyStockLevel</span><span class="sxs-lookup"><span data-stu-id="afad6-231">SafetyStockLevel</span></span>|<span data-ttu-id="afad6-232">Safety Stock Level</span><span class="sxs-lookup"><span data-stu-id="afad6-232">Safety Stock Level</span></span>|  
    |<span data-ttu-id="afad6-233">ReorderPoint</span><span class="sxs-lookup"><span data-stu-id="afad6-233">ReorderPoint</span></span>|<span data-ttu-id="afad6-234">Reorder Point</span><span class="sxs-lookup"><span data-stu-id="afad6-234">Reorder Point</span></span>|  
    |<span data-ttu-id="afad6-235">ListPrice</span><span class="sxs-lookup"><span data-stu-id="afad6-235">ListPrice</span></span>|<span data-ttu-id="afad6-236">List Price</span><span class="sxs-lookup"><span data-stu-id="afad6-236">List Price</span></span>|  
    |<span data-ttu-id="afad6-237">SizeRange</span><span class="sxs-lookup"><span data-stu-id="afad6-237">SizeRange</span></span>|<span data-ttu-id="afad6-238">Size Range</span><span class="sxs-lookup"><span data-stu-id="afad6-238">Size Range</span></span>|  
    |<span data-ttu-id="afad6-239">DaysToManufacture</span><span class="sxs-lookup"><span data-stu-id="afad6-239">DaysToManufacture</span></span>|<span data-ttu-id="afad6-240">Days to Manufacture</span><span class="sxs-lookup"><span data-stu-id="afad6-240">Days to Manufacture</span></span>|  
    |<span data-ttu-id="afad6-241">ProductLine</span><span class="sxs-lookup"><span data-stu-id="afad6-241">ProductLine</span></span>|<span data-ttu-id="afad6-242">Product Line</span><span class="sxs-lookup"><span data-stu-id="afad6-242">Product Line</span></span>|  
    |<span data-ttu-id="afad6-243">Dealer Price</span><span class="sxs-lookup"><span data-stu-id="afad6-243">Dealer Price</span></span>|<span data-ttu-id="afad6-244">Dealer Price</span><span class="sxs-lookup"><span data-stu-id="afad6-244">Dealer Price</span></span>|  
    |<span data-ttu-id="afad6-245">ModelName</span><span class="sxs-lookup"><span data-stu-id="afad6-245">ModelName</span></span>|<span data-ttu-id="afad6-246">Model Name</span><span class="sxs-lookup"><span data-stu-id="afad6-246">Model Name</span></span>|  
    |<span data-ttu-id="afad6-247">LargePhoto</span><span class="sxs-lookup"><span data-stu-id="afad6-247">LargePhoto</span></span>|<span data-ttu-id="afad6-248">Large Photo</span><span class="sxs-lookup"><span data-stu-id="afad6-248">Large Photo</span></span>|  
    |<span data-ttu-id="afad6-249">EnglishDescription</span><span class="sxs-lookup"><span data-stu-id="afad6-249">EnglishDescription</span></span>|<span data-ttu-id="afad6-250">説明</span><span class="sxs-lookup"><span data-stu-id="afad6-250">Description</span></span>|  
    |<span data-ttu-id="afad6-251">StartDate</span><span class="sxs-lookup"><span data-stu-id="afad6-251">StartDate</span></span>|<span data-ttu-id="afad6-252">Product Start Date</span><span class="sxs-lookup"><span data-stu-id="afad6-252">Product Start Date</span></span>|  
    |<span data-ttu-id="afad6-253">EndDate</span><span class="sxs-lookup"><span data-stu-id="afad6-253">EndDate</span></span>|<span data-ttu-id="afad6-254">Product End Date</span><span class="sxs-lookup"><span data-stu-id="afad6-254">Product End Date</span></span>|  
    |<span data-ttu-id="afad6-255">Status</span><span class="sxs-lookup"><span data-stu-id="afad6-255">Status</span></span>|<span data-ttu-id="afad6-256">Product Status</span><span class="sxs-lookup"><span data-stu-id="afad6-256">Product Status</span></span>|  
  
     <span data-ttu-id="afad6-257">**製品カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="afad6-257">**Product Category**</span></span>  
  
    |<span data-ttu-id="afad6-258">ソース名</span><span class="sxs-lookup"><span data-stu-id="afad6-258">Source Name</span></span>|<span data-ttu-id="afad6-259">フレンドリ名</span><span class="sxs-lookup"><span data-stu-id="afad6-259">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="afad6-260">ProductCategoryKey</span><span class="sxs-lookup"><span data-stu-id="afad6-260">ProductCategoryKey</span></span>|<span data-ttu-id="afad6-261">Product Category Id</span><span class="sxs-lookup"><span data-stu-id="afad6-261">Product Category Id</span></span>|  
    |<span data-ttu-id="afad6-262">ProductCategoryAlternateKey</span><span class="sxs-lookup"><span data-stu-id="afad6-262">ProductCategoryAlternateKey</span></span>|<span data-ttu-id="afad6-263">Product Category Alternate Id</span><span class="sxs-lookup"><span data-stu-id="afad6-263">Product Category Alternate Id</span></span>|  
    |<span data-ttu-id="afad6-264">EnglishProductCategoryName</span><span class="sxs-lookup"><span data-stu-id="afad6-264">EnglishProductCategoryName</span></span>|<span data-ttu-id="afad6-265">Product Category Name</span><span class="sxs-lookup"><span data-stu-id="afad6-265">Product Category Name</span></span>|  
  
     <span data-ttu-id="afad6-266">**Product Subcategory**</span><span class="sxs-lookup"><span data-stu-id="afad6-266">**Product Subcategory**</span></span>  
  
    |<span data-ttu-id="afad6-267">ソース名</span><span class="sxs-lookup"><span data-stu-id="afad6-267">Source Name</span></span>|<span data-ttu-id="afad6-268">フレンドリ名</span><span class="sxs-lookup"><span data-stu-id="afad6-268">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="afad6-269">ProductSubcategoryKey</span><span class="sxs-lookup"><span data-stu-id="afad6-269">ProductSubcategoryKey</span></span>|<span data-ttu-id="afad6-270">Product Subcategory Id</span><span class="sxs-lookup"><span data-stu-id="afad6-270">Product Subcategory Id</span></span>|  
    |<span data-ttu-id="afad6-271">ProductSubcategoryAlternateKey</span><span class="sxs-lookup"><span data-stu-id="afad6-271">ProductSubcategoryAlternateKey</span></span>|<span data-ttu-id="afad6-272">Product Subcategory Alternate Id</span><span class="sxs-lookup"><span data-stu-id="afad6-272">Product Subcategory Alternate Id</span></span>|  
    |<span data-ttu-id="afad6-273">EnglishProductSubcategoryName</span><span class="sxs-lookup"><span data-stu-id="afad6-273">EnglishProductSubcategoryName</span></span>|<span data-ttu-id="afad6-274">Product Subcategory Name</span><span class="sxs-lookup"><span data-stu-id="afad6-274">Product Subcategory Name</span></span>|  
    |<span data-ttu-id="afad6-275">ProductCategoryKey</span><span class="sxs-lookup"><span data-stu-id="afad6-275">ProductCategoryKey</span></span>|<span data-ttu-id="afad6-276">Product Category Id</span><span class="sxs-lookup"><span data-stu-id="afad6-276">Product Category Id</span></span>|  
  
     <span data-ttu-id="afad6-277">**Internet Sales**</span><span class="sxs-lookup"><span data-stu-id="afad6-277">**Internet Sales**</span></span>  
  
    |<span data-ttu-id="afad6-278">ソース名</span><span class="sxs-lookup"><span data-stu-id="afad6-278">Source Name</span></span>|<span data-ttu-id="afad6-279">フレンドリ名</span><span class="sxs-lookup"><span data-stu-id="afad6-279">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="afad6-280">ProductKey</span><span class="sxs-lookup"><span data-stu-id="afad6-280">ProductKey</span></span>|<span data-ttu-id="afad6-281">[Product Id]</span><span class="sxs-lookup"><span data-stu-id="afad6-281">Product Id</span></span>|  
    |<span data-ttu-id="afad6-282">CustomerKey</span><span class="sxs-lookup"><span data-stu-id="afad6-282">CustomerKey</span></span>|<span data-ttu-id="afad6-283">[Customer Id]</span><span class="sxs-lookup"><span data-stu-id="afad6-283">Customer Id</span></span>|  
    |<span data-ttu-id="afad6-284">PromotionKey</span><span class="sxs-lookup"><span data-stu-id="afad6-284">PromotionKey</span></span>|<span data-ttu-id="afad6-285">Promotion Id</span><span class="sxs-lookup"><span data-stu-id="afad6-285">Promotion Id</span></span>|  
    |<span data-ttu-id="afad6-286">CurrencyKey</span><span class="sxs-lookup"><span data-stu-id="afad6-286">CurrencyKey</span></span>|<span data-ttu-id="afad6-287">Currency Id</span><span class="sxs-lookup"><span data-stu-id="afad6-287">Currency Id</span></span>|  
    |<span data-ttu-id="afad6-288">SalesTerritoryKey</span><span class="sxs-lookup"><span data-stu-id="afad6-288">SalesTerritoryKey</span></span>|<span data-ttu-id="afad6-289">Sales Territory Id</span><span class="sxs-lookup"><span data-stu-id="afad6-289">Sales Territory Id</span></span>|  
    |<span data-ttu-id="afad6-290">SalesOrderNumber</span><span class="sxs-lookup"><span data-stu-id="afad6-290">SalesOrderNumber</span></span>|<span data-ttu-id="afad6-291">Sales Order Number</span><span class="sxs-lookup"><span data-stu-id="afad6-291">Sales Order Number</span></span>|  
    |<span data-ttu-id="afad6-292">SalesOrderLineNumber</span><span class="sxs-lookup"><span data-stu-id="afad6-292">SalesOrderLineNumber</span></span>|<span data-ttu-id="afad6-293">Sales Order Line Number</span><span class="sxs-lookup"><span data-stu-id="afad6-293">Sales Order Line Number</span></span>|  
    |<span data-ttu-id="afad6-294">RevisionNumber</span><span class="sxs-lookup"><span data-stu-id="afad6-294">RevisionNumber</span></span>|<span data-ttu-id="afad6-295">Revision Number</span><span class="sxs-lookup"><span data-stu-id="afad6-295">Revision Number</span></span>|  
    |<span data-ttu-id="afad6-296">OrderQuantity</span><span class="sxs-lookup"><span data-stu-id="afad6-296">OrderQuantity</span></span>|<span data-ttu-id="afad6-297">Order Quantity</span><span class="sxs-lookup"><span data-stu-id="afad6-297">Order Quantity</span></span>|  
    |<span data-ttu-id="afad6-298">UnitPrice</span><span class="sxs-lookup"><span data-stu-id="afad6-298">UnitPrice</span></span>|<span data-ttu-id="afad6-299">Unit Price</span><span class="sxs-lookup"><span data-stu-id="afad6-299">Unit Price</span></span>|  
    |<span data-ttu-id="afad6-300">ExtendedAmount</span><span class="sxs-lookup"><span data-stu-id="afad6-300">ExtendedAmount</span></span>|<span data-ttu-id="afad6-301">Extended Amount</span><span class="sxs-lookup"><span data-stu-id="afad6-301">Extended Amount</span></span>|  
    |<span data-ttu-id="afad6-302">UnitPriceDiscountPct</span><span class="sxs-lookup"><span data-stu-id="afad6-302">UnitPriceDiscountPct</span></span>|<span data-ttu-id="afad6-303">Unit Price Discount Pct</span><span class="sxs-lookup"><span data-stu-id="afad6-303">Unit Price Discount Pct</span></span>|  
    |<span data-ttu-id="afad6-304">DiscountAmount</span><span class="sxs-lookup"><span data-stu-id="afad6-304">DiscountAmount</span></span>|<span data-ttu-id="afad6-305">Discount Amount</span><span class="sxs-lookup"><span data-stu-id="afad6-305">Discount Amount</span></span>|  
    |<span data-ttu-id="afad6-306">ProductStandardCost</span><span class="sxs-lookup"><span data-stu-id="afad6-306">ProductStandardCost</span></span>|<span data-ttu-id="afad6-307">Product Standard Cost</span><span class="sxs-lookup"><span data-stu-id="afad6-307">Product Standard Cost</span></span>|  
    |<span data-ttu-id="afad6-308">TotalProductCost</span><span class="sxs-lookup"><span data-stu-id="afad6-308">TotalProductCost</span></span>|<span data-ttu-id="afad6-309">Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="afad6-309">Total Product Cost</span></span>|  
    |<span data-ttu-id="afad6-310">SalesAmount</span><span class="sxs-lookup"><span data-stu-id="afad6-310">SalesAmount</span></span>|<span data-ttu-id="afad6-311">Sales Amount</span><span class="sxs-lookup"><span data-stu-id="afad6-311">Sales Amount</span></span>|  
    |<span data-ttu-id="afad6-312">TaxAmt</span><span class="sxs-lookup"><span data-stu-id="afad6-312">TaxAmt</span></span>|<span data-ttu-id="afad6-313">Tax Amt</span><span class="sxs-lookup"><span data-stu-id="afad6-313">Tax Amt</span></span>|  
    |<span data-ttu-id="afad6-314">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="afad6-314">CarrierTrackingNumber</span></span>|<span data-ttu-id="afad6-315">Carrier Tracking Number</span><span class="sxs-lookup"><span data-stu-id="afad6-315">Carrier Tracking Number</span></span>|  
    |<span data-ttu-id="afad6-316">CustomerPONumber</span><span class="sxs-lookup"><span data-stu-id="afad6-316">CustomerPONumber</span></span>|<span data-ttu-id="afad6-317">Customer PO Number</span><span class="sxs-lookup"><span data-stu-id="afad6-317">Customer PO Number</span></span>|  
    |<span data-ttu-id="afad6-318">OrderDate</span><span class="sxs-lookup"><span data-stu-id="afad6-318">OrderDate</span></span>|<span data-ttu-id="afad6-319">Order Date</span><span class="sxs-lookup"><span data-stu-id="afad6-319">Order Date</span></span>|  
    |<span data-ttu-id="afad6-320">DueDate</span><span class="sxs-lookup"><span data-stu-id="afad6-320">DueDate</span></span>|<span data-ttu-id="afad6-321">Due Date</span><span class="sxs-lookup"><span data-stu-id="afad6-321">Due Date</span></span>|  
    |<span data-ttu-id="afad6-322">ShipDate</span><span class="sxs-lookup"><span data-stu-id="afad6-322">ShipDate</span></span>|<span data-ttu-id="afad6-323">Ship Date</span><span class="sxs-lookup"><span data-stu-id="afad6-323">Ship Date</span></span>|  
  
## <a name="next-step"></a><span data-ttu-id="afad6-324">次の手順</span><span class="sxs-lookup"><span data-stu-id="afad6-324">Next Step</span></span>  
 <span data-ttu-id="afad6-325">このチュートリアルを続行するには、次のレッスン「 [レッスン 4: 日付テーブルとしてマーク](lesson-3-mark-as-date-table.md)」に進んでください。</span><span class="sxs-lookup"><span data-stu-id="afad6-325">To continue this tutorial, go to the next lesson: [Lesson 4: Mark as Date Table](lesson-3-mark-as-date-table.md).</span></span>  
  
  
