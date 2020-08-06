---
title: Cube を定義する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8aa4ac2d-857f-4048-baa0-0f314e207cf6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 354a05840dd2e091f956454858edd5c75c8c4bdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631288"
---
# <a name="defining-a-cube"></a><span data-ttu-id="0e9c4-102">キューブの定義</span><span class="sxs-lookup"><span data-stu-id="0e9c4-102">Defining a Cube</span></span>
  <span data-ttu-id="0e9c4-103">キューブ ウィザードを使用すると、キューブのメジャー グループとディメンションを定義できます。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-103">The Cube Wizard helps you define the measure groups and dimensions for a cube.</span></span> <span data-ttu-id="0e9c4-104">この実習では、キューブ ウィザードを使用してキューブを作成します。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-104">In the following task, you will use the Cube Wizard to build a cube.</span></span>  
  
### <a name="to-define-a-cube-and-its-properties"></a><span data-ttu-id="0e9c4-105">キューブとそのプロパティを定義するには</span><span class="sxs-lookup"><span data-stu-id="0e9c4-105">To define a cube and its properties</span></span>  
  
1.  <span data-ttu-id="0e9c4-106">ソリューションエクスプローラーで、[**キューブ**] を右クリックし、[**新しいキューブ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-106">In Solution Explorer, right-click **Cubes**, and then click **New Cube**.</span></span> <span data-ttu-id="0e9c4-107">キューブ ウィザードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-107">The Cube Wizard appears.</span></span>  
  
2.  <span data-ttu-id="0e9c4-108">**[キューブ ウィザードへようこそ]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-108">On the **Welcome to the Cube Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="0e9c4-109">**[作成方法の選択]** ページで **[既存のテーブルを使用する]** オプションが選択されていることを確認し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-109">On the **Select Creation Method** page, verify that the **Use existing tables** option is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="0e9c4-110">**[メジャー グループ テーブルの選択]** ページで、 **Adventure Works DW 2012** データ ソース ビューが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-110">On the **Select Measure Group Tables** page, verify that the **Adventure Works DW 2012** data source view is selected.</span></span>  
  
5.  <span data-ttu-id="0e9c4-111">**[候補検索]** をクリックすると、メジャー グループの作成に使用するテーブルがキューブ ウィザードによって提示されます。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-111">Click **Suggest** to have the cube wizard suggest tables to use to create measure groups.</span></span>  
  
     <span data-ttu-id="0e9c4-112">ウィザードでそれらのテーブルが調べられ、 **InternetSales** がメジャー グループ テーブルとして提示されます。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-112">The wizard examines the tables and suggests **InternetSales** as a measure group table.</span></span> <span data-ttu-id="0e9c4-113">メジャー グループ テーブル (ファクト テーブルとも呼ばれます) には、販売数など必要なメジャーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-113">Measure group tables, also called fact tables, contain the measures you are interested in, such as the number of units sold.</span></span>  
  
6.  <span data-ttu-id="0e9c4-114">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-114">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="0e9c4-115">**[メジャーの選択]** ページで、 **Internet Sales** メジャー グループ内の選択されているメジャーを確認し、以下のメジャーのチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-115">On the **Select Measures** page, review the selected measures in the **Internet Sales** measure group, and then clear the check boxes for the following measures:</span></span>  
  
    -   <span data-ttu-id="0e9c4-116">**Promotion Key**</span><span class="sxs-lookup"><span data-stu-id="0e9c4-116">**Promotion Key**</span></span>  
  
    -   <span data-ttu-id="0e9c4-117">**Currency Key**</span><span class="sxs-lookup"><span data-stu-id="0e9c4-117">**Currency Key**</span></span>  
  
    -   <span data-ttu-id="0e9c4-118">**Sales Territory Key**</span><span class="sxs-lookup"><span data-stu-id="0e9c4-118">**Sales Territory Key**</span></span>  
  
    -   <span data-ttu-id="0e9c4-119">**リビジョン番号**</span><span class="sxs-lookup"><span data-stu-id="0e9c4-119">**Revision Number**</span></span>  
  
     <span data-ttu-id="0e9c4-120">既定では、ファクト テーブル内で、ディメンションにリンクしていないすべての数値列がメジャーとして選択されます。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-120">By default, the wizard selects as measures all numeric columns in the fact table that are not linked to dimensions.</span></span> <span data-ttu-id="0e9c4-121">ただし、上の 4 つの列は実際にはメジャーではありません。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-121">However, these four columns are not actual measures.</span></span> <span data-ttu-id="0e9c4-122">最初の 3 つは、ファクト テーブルとディメンション テーブルをリンクするキー値で、この初期段階のキューブでは使用しません。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-122">The first three are key values that link the fact table with dimension tables that are not used in the initial version of this cube.</span></span>  
  
8.  <span data-ttu-id="0e9c4-123">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-123">Click **Next**.</span></span>  
  
9. <span data-ttu-id="0e9c4-124">**[既存のディメンションの選択]** ページで、既に作成した **Date** ディメンションが選択されていることを確認し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-124">On the **Select Existing Dimensions** page, make sure the **Date** dimension that you created earlier is selected, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="0e9c4-125">**[新しいディメンションの選択]** ページで、作成する新しいディメンションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-125">On the **Select New Dimensions** page, select the new dimensions to be created.</span></span> <span data-ttu-id="0e9c4-126">そのためには、 **[Customer]**、 **[Geography]**、 **[Product]** の各チェック ボックスがオンになっていることを確認し、 **[InternetSales]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-126">To do this, verify that the **Customer**, **Geography**, and **Product** check boxes are selected, and then clear the **InternetSales** check box.</span></span>  
  
11. <span data-ttu-id="0e9c4-127">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-127">Click **Next**.</span></span>  
  
12. <span data-ttu-id="0e9c4-128">[**ウィザードの完了**] ページで、キューブの名前をに変更し `Analysis Services Tutorial` ます。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-128">On the **Completing the Wizard** page, change the name of the cube to `Analysis Services Tutorial`.</span></span> <span data-ttu-id="0e9c4-129">[プレビュー] ペインで、 **InternetSales** メジャー グループとそのメジャーを表示できます。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-129">In the Preview pane, you can see the **InternetSales** measure group and its measures.</span></span> <span data-ttu-id="0e9c4-130">**Date**、 **Customer** 、 **Product** の各ディメンションも表示できます。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-130">You can also see the **Date**, **Customer,** and **Product** dimensions.</span></span>  
  
13. <span data-ttu-id="0e9c4-131">**[完了]** をクリックしてウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-131">Click **Finish** to complete the wizard.</span></span>  
  
     <span data-ttu-id="0e9c4-132">ソリューション エクスプローラーで、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトの [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [キューブ] **フォルダー内に** Tutorial キューブが表示されます。また、 **[ディメンション]** フォルダーの下には、Customer、Product というデータベース ディメンションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-132">In Solution Explorer, in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project, the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube appears in the **Cubes** folder, and the Customer and Product database dimensions appear in the **Dimensions** folder.</span></span> <span data-ttu-id="0e9c4-133">さらに、開発環境の中央の [キューブ構造] タブには [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-133">Additionally, in the center of the development environment, the Cube Structure tab displays the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>  
  
14. <span data-ttu-id="0e9c4-134">キューブ内のディメンション テーブルとファクト テーブルをすべて表示できるよう、[キューブ構造] タブのツール バーで、 **ズーム** レベルを 50% に変更します。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-134">On the toolbar of the Cube Structure tab, change the **Zoom** level to 50 percent, so that you can more easily see the dimensions and fact tables in the cube.</span></span> <span data-ttu-id="0e9c4-135">ファクト テーブルは黄色、ディメンション テーブルは青で表示されています。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-135">Notice that the fact table is yellow and the dimension tables are blue.</span></span>  
  
15. <span data-ttu-id="0e9c4-136">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e9c4-136">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="0e9c4-137">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="0e9c4-137">Next Task in Lesson</span></span>  
 [<span data-ttu-id="0e9c4-138">ディメンションへの属性の追加</span><span class="sxs-lookup"><span data-stu-id="0e9c4-138">Adding Attributes to Dimensions</span></span>](lesson-2-3-adding-attributes-to-dimensions.md)  
  
## <a name="see-also"></a><span data-ttu-id="0e9c4-139">参照</span><span class="sxs-lookup"><span data-stu-id="0e9c4-139">See Also</span></span>  
 <span data-ttu-id="0e9c4-140">[多次元モデルのキューブ](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="0e9c4-140">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="0e9c4-141">多次元モデル内のディメンション</span><span class="sxs-lookup"><span data-stu-id="0e9c4-141">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
