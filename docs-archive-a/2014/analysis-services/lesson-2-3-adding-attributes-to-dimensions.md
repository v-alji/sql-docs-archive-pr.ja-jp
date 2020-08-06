---
title: ディメンションへの属性の追加 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 80551dad-97ac-40d0-90af-b810780321ce
author: minewiskan
ms.author: owend
ms.openlocfilehash: 76a04c42cc501fdca3e5ceb6481452052966796b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631286"
---
# <a name="adding-attributes-to-dimensions"></a><span data-ttu-id="ee43a-102">ディメンションへの属性の追加</span><span class="sxs-lookup"><span data-stu-id="ee43a-102">Adding Attributes to Dimensions</span></span>
  <span data-ttu-id="ee43a-103">ディメンションを定義したので、ディメンションの各データ要素を表す属性をディメンションに読み込めるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ee43a-103">Now that you have defined dimensions, you can populate them with attributes that represent each data element in the dimension.</span></span> <span data-ttu-id="ee43a-104">属性は、通常、データ ソース ビューのフィールドに基づいています。</span><span class="sxs-lookup"><span data-stu-id="ee43a-104">Attributes are commonly based on fields from a data source view.</span></span> <span data-ttu-id="ee43a-105">ディメンションに属性を追加するときに、データ ソース ビュー内の任意のテーブルのフィールドを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ee43a-105">When adding attributes to a dimension, you can include fields from any table in the data source view.</span></span>  
  
 <span data-ttu-id="ee43a-106">この実習では、ディメンション デザイナーを使用して、属性を Customer ディメンションと Product ディメンションに追加します。</span><span class="sxs-lookup"><span data-stu-id="ee43a-106">In this task, you will use Dimension Designer to add attributes to the Customer and Product dimensions.</span></span> <span data-ttu-id="ee43a-107">Customer ディメンションには、Customer テーブルと Geography テーブルの両方のフィールドに基づく属性が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ee43a-107">The Customer dimension will include attributes based on fields from both the Customer and Geography tables.</span></span>  
  
## <a name="adding-attributes-to-the-customer-dimension"></a><span data-ttu-id="ee43a-108">Customer ディメンションへの属性の追加</span><span class="sxs-lookup"><span data-stu-id="ee43a-108">Adding Attributes to the Customer Dimension</span></span>  
  
#### <a name="to-add-attributes"></a><span data-ttu-id="ee43a-109">属性を追加するには</span><span class="sxs-lookup"><span data-stu-id="ee43a-109">To add attributes</span></span>  
  
1.  <span data-ttu-id="ee43a-110">Customer ディメンションのディメンション デザイナーを開きます。</span><span class="sxs-lookup"><span data-stu-id="ee43a-110">Open Dimension Designer for the Customer dimension.</span></span> <span data-ttu-id="ee43a-111">これを行うには、ソリューション エクスプローラーの **[ディメンション]** ノードで **[Customer]** ディメンションをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee43a-111">To do this, double-click the **Customer** dimension in the **Dimensions** node of Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="ee43a-112">**[属性]** ペインに、キューブ ウィザードによって作成された Customer Key 属性および Geography Key 属性が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee43a-112">In the **Attributes** pane, notice the Customer Key and Geography Key attributes that were created by the Cube Wizard.</span></span>  
  
3.  <span data-ttu-id="ee43a-113">**[ディメンション構造]** タブのツール バーで、 **[データ ソース ビュー]** ペイン内のテーブルを表示するための [ズーム] アイコンが 100% に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ee43a-113">On the toolbar of the **Dimension Structure** tab, make sure the Zoom icon to view the tables in the **Data Source View** pane is set at 100 percent.</span></span>  
  
4.  <span data-ttu-id="ee43a-114">次の列を、 **[データ ソース ビュー]** ペインの **Customer** テーブルから **[属性]** ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ee43a-114">Drag the following columns from the **Customer** table in the **Data Source View** pane to the **Attributes** pane:</span></span>  
  
    -   <span data-ttu-id="ee43a-115">**BirthDate**</span><span class="sxs-lookup"><span data-stu-id="ee43a-115">**BirthDate**</span></span>  
  
    -   <span data-ttu-id="ee43a-116">**MaritalStatus**</span><span class="sxs-lookup"><span data-stu-id="ee43a-116">**MaritalStatus**</span></span>  
  
    -   <span data-ttu-id="ee43a-117">**性別**</span><span class="sxs-lookup"><span data-stu-id="ee43a-117">**Gender**</span></span>  
  
    -   <span data-ttu-id="ee43a-118">**EmailAddress**</span><span class="sxs-lookup"><span data-stu-id="ee43a-118">**EmailAddress**</span></span>  
  
    -   <span data-ttu-id="ee43a-119">**YearlyIncome**</span><span class="sxs-lookup"><span data-stu-id="ee43a-119">**YearlyIncome**</span></span>  
  
    -   <span data-ttu-id="ee43a-120">**TotalChildren**</span><span class="sxs-lookup"><span data-stu-id="ee43a-120">**TotalChildren**</span></span>  
  
    -   <span data-ttu-id="ee43a-121">**NumberChildrenAtHome**</span><span class="sxs-lookup"><span data-stu-id="ee43a-121">**NumberChildrenAtHome**</span></span>  
  
    -   <span data-ttu-id="ee43a-122">**EnglishEducation**</span><span class="sxs-lookup"><span data-stu-id="ee43a-122">**EnglishEducation**</span></span>  
  
    -   <span data-ttu-id="ee43a-123">**EnglishOccupation**</span><span class="sxs-lookup"><span data-stu-id="ee43a-123">**EnglishOccupation**</span></span>  
  
    -   <span data-ttu-id="ee43a-124">**HouseOwnerFlag**</span><span class="sxs-lookup"><span data-stu-id="ee43a-124">**HouseOwnerFlag**</span></span>  
  
    -   <span data-ttu-id="ee43a-125">**NumberCarsOwned**</span><span class="sxs-lookup"><span data-stu-id="ee43a-125">**NumberCarsOwned**</span></span>  
  
    -   <span data-ttu-id="ee43a-126">**Phone**</span><span class="sxs-lookup"><span data-stu-id="ee43a-126">**Phone**</span></span>  
  
    -   <span data-ttu-id="ee43a-127">**DateFirstPurchase**</span><span class="sxs-lookup"><span data-stu-id="ee43a-127">**DateFirstPurchase**</span></span>  
  
    -   <span data-ttu-id="ee43a-128">**CommuteDistance**</span><span class="sxs-lookup"><span data-stu-id="ee43a-128">**CommuteDistance**</span></span>  
  
5.  <span data-ttu-id="ee43a-129">次の列を、 **[データ ソース ビュー]** ペインの **Geography** テーブルから **[属性]** ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ee43a-129">Drag the following columns from the **Geography** table in the **Data Source View** pane to the **Attributes** pane:</span></span>  
  
    -   <span data-ttu-id="ee43a-130">**City (市)**</span><span class="sxs-lookup"><span data-stu-id="ee43a-130">**City**</span></span>  
  
    -   <span data-ttu-id="ee43a-131">**StateProvinceName**</span><span class="sxs-lookup"><span data-stu-id="ee43a-131">**StateProvinceName**</span></span>  
  
    -   <span data-ttu-id="ee43a-132">**EnglishCountryRegionName**</span><span class="sxs-lookup"><span data-stu-id="ee43a-132">**EnglishCountryRegionName**</span></span>  
  
    -   <span data-ttu-id="ee43a-133">**PostalCode**</span><span class="sxs-lookup"><span data-stu-id="ee43a-133">**PostalCode**</span></span>  
  
6.  <span data-ttu-id="ee43a-134">[File]\(ファイル\) メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee43a-134">On the File menu, click **Save All**.</span></span>  
  
## <a name="adding-attributes-to-the-product-dimension"></a><span data-ttu-id="ee43a-135">Product ディメンションへの属性の追加</span><span class="sxs-lookup"><span data-stu-id="ee43a-135">Adding Attributes to the Product Dimension</span></span>  
  
#### <a name="to-add-attributes"></a><span data-ttu-id="ee43a-136">属性を追加するには</span><span class="sxs-lookup"><span data-stu-id="ee43a-136">To add attributes</span></span>  
  
1.  <span data-ttu-id="ee43a-137">Product ディメンションのディメンション デザイナーを開きます。</span><span class="sxs-lookup"><span data-stu-id="ee43a-137">Open Dimension Designer for the Product dimension.</span></span> <span data-ttu-id="ee43a-138">ソリューション エクスプローラーで、 **Product** ディメンションをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee43a-138">Double-click the **Product** dimension in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="ee43a-139">**[属性]** ペインに、キューブ ウィザードによって作成された Product Key 属性が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee43a-139">In the **Attributes** pane, notice the Product Key attribute that was created by the Cube Wizard.</span></span>  
  
3.  <span data-ttu-id="ee43a-140">**[ディメンション構造]** タブのツール バーで、 **[データ ソース ビュー]** ペイン内のテーブルを表示するための [ズーム] アイコンが 100% に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ee43a-140">On the toolbar of the **Dimension Structure** tab, make sure the Zoom icon to view the tables in the **Data Source View** pane is set at 100 percent.</span></span>  
  
4.  <span data-ttu-id="ee43a-141">次の列を、 **[データ ソース ビュー]** ペインの **Product** テーブルから **[属性]** ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ee43a-141">Drag the following columns from the **Product** table in the **Data Source View** pane to the **Attributes** pane:</span></span>  
  
    -   <span data-ttu-id="ee43a-142">**StandardCost**</span><span class="sxs-lookup"><span data-stu-id="ee43a-142">**StandardCost**</span></span>  
  
    -   <span data-ttu-id="ee43a-143">**色**</span><span class="sxs-lookup"><span data-stu-id="ee43a-143">**Color**</span></span>  
  
    -   <span data-ttu-id="ee43a-144">**SafetyStockLevel**</span><span class="sxs-lookup"><span data-stu-id="ee43a-144">**SafetyStockLevel**</span></span>  
  
    -   <span data-ttu-id="ee43a-145">**ReorderPoint**</span><span class="sxs-lookup"><span data-stu-id="ee43a-145">**ReorderPoint**</span></span>  
  
    -   <span data-ttu-id="ee43a-146">**ListPrice**</span><span class="sxs-lookup"><span data-stu-id="ee43a-146">**ListPrice**</span></span>  
  
    -   <span data-ttu-id="ee43a-147">**[サイズ]**</span><span class="sxs-lookup"><span data-stu-id="ee43a-147">**Size**</span></span>  
  
    -   <span data-ttu-id="ee43a-148">**SizeRange**</span><span class="sxs-lookup"><span data-stu-id="ee43a-148">**SizeRange**</span></span>  
  
    -   <span data-ttu-id="ee43a-149">**Weight**</span><span class="sxs-lookup"><span data-stu-id="ee43a-149">**Weight**</span></span>  
  
    -   <span data-ttu-id="ee43a-150">**DaysToManufacture**</span><span class="sxs-lookup"><span data-stu-id="ee43a-150">**DaysToManufacture**</span></span>  
  
    -   <span data-ttu-id="ee43a-151">**ProductLine**</span><span class="sxs-lookup"><span data-stu-id="ee43a-151">**ProductLine**</span></span>  
  
    -   <span data-ttu-id="ee43a-152">**DealerPrice**</span><span class="sxs-lookup"><span data-stu-id="ee43a-152">**DealerPrice**</span></span>  
  
    -   <span data-ttu-id="ee43a-153">**クラス**</span><span class="sxs-lookup"><span data-stu-id="ee43a-153">**Class**</span></span>  
  
    -   <span data-ttu-id="ee43a-154">**Style**</span><span class="sxs-lookup"><span data-stu-id="ee43a-154">**Style**</span></span>  
  
    -   <span data-ttu-id="ee43a-155">**ModelName**</span><span class="sxs-lookup"><span data-stu-id="ee43a-155">**ModelName**</span></span>  
  
    -   <span data-ttu-id="ee43a-156">**StartDate**</span><span class="sxs-lookup"><span data-stu-id="ee43a-156">**StartDate**</span></span>  
  
    -   <span data-ttu-id="ee43a-157">**EndDate**</span><span class="sxs-lookup"><span data-stu-id="ee43a-157">**EndDate**</span></span>  
  
    -   <span data-ttu-id="ee43a-158">**状態**</span><span class="sxs-lookup"><span data-stu-id="ee43a-158">**Status**</span></span>  
  
5.  <span data-ttu-id="ee43a-159">[File]\(ファイル\) メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee43a-159">On the File menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="ee43a-160">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="ee43a-160">Next Task in Lesson</span></span>  
 [<span data-ttu-id="ee43a-161">キューブとディメンションのプロパティの確認</span><span class="sxs-lookup"><span data-stu-id="ee43a-161">Reviewing Cube and Dimension Properties</span></span>](lesson-2-4-reviewing-cube-and-dimension-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="ee43a-162">参照</span><span class="sxs-lookup"><span data-stu-id="ee43a-162">See Also</span></span>  
 [<span data-ttu-id="ee43a-163">ディメンションの属性のプロパティの参照</span><span class="sxs-lookup"><span data-stu-id="ee43a-163">Dimension Attribute Properties Reference</span></span>](multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
