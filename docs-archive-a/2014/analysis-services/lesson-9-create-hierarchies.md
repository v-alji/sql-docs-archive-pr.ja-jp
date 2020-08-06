---
title: 'レッスン 10: 階層を作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1e2561d3-4890-4495-a9cd-84eb88508938
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4d0982a05c37c28167e44e3f9f082ea5113b59bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715854"
---
# <a name="lesson-10-create-hierarchies"></a><span data-ttu-id="7e4ad-102">レッスン 10: 階層を作成する</span><span class="sxs-lookup"><span data-stu-id="7e4ad-102">Lesson 10: Create Hierarchies</span></span>
  <span data-ttu-id="7e4ad-103">このレッスンでは、階層を作成します。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-103">In this lesson, you will create hierarchies.</span></span> <span data-ttu-id="7e4ad-104">階層は、複数のレベルに分類された列のグループです。たとえば、Geography という階層に、Country、State、County、および City というサブレベルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-104">Hierarchies are groups of columns arranged in levels; for example, a Geography hierarchy might have sub-levels for Country, State, County, and City.</span></span> <span data-ttu-id="7e4ad-105">階層は、レポートするクライアント アプリケーションのフィールド リストにある他の列とは別に表示できます。階層を使用すれば、クライアント ユーザーが列をより簡単に探してレポートに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-105">Hierarchies can appear separate from other columns in a reporting client application field list, making them easier for client users to navigate and include in a report.</span></span> <span data-ttu-id="7e4ad-106">詳細については、[「階層 (SSAS テーブル)」](tabular-models/hierarchies-ssas-tabular.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-106">To learn more, see [Hierarchies &#40;SSAS Tabular&#41;](tabular-models/hierarchies-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="7e4ad-107">階層を作成するには、 *ダイアグラム ビュー*のモデル デザイナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-107">To create hierarchies, you will use the model designer in *Diagram View*.</span></span> <span data-ttu-id="7e4ad-108">階層の作成と管理は、データ ビューのモデル デザイナーではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-108">Creating and managing hierarchies is not supported in the model designer in Data View.</span></span>  
  
 <span data-ttu-id="7e4ad-109">このレッスンの推定所要時間: **20 分**</span><span class="sxs-lookup"><span data-stu-id="7e4ad-109">Estimated time to complete this lesson: **20 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7e4ad-110">前提条件</span><span class="sxs-lookup"><span data-stu-id="7e4ad-110">Prerequisites</span></span>  
 <span data-ttu-id="7e4ad-111">このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-111">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="7e4ad-112">このレッスンの実習を行う前に、前のレッスン [「レッスン 9: パースペクティブの作成」](lesson-8-create-perspectives.md)を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-112">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 9: Create Perspectives](lesson-8-create-perspectives.md).</span></span>  
  
## <a name="create-hierarchies"></a><span data-ttu-id="7e4ad-113">階層を作成する</span><span class="sxs-lookup"><span data-stu-id="7e4ad-113">Create Hierarchies</span></span>  
  
#### <a name="to-create-a-category-hierarchy-in-the-product-table"></a><span data-ttu-id="7e4ad-114">Product テーブル内に Category 階層を作成するには</span><span class="sxs-lookup"><span data-stu-id="7e4ad-114">To create a Category hierarchy in the Product table</span></span>  
  
1.  <span data-ttu-id="7e4ad-115">モデルデザイナーで、メニューをクリックし、[ `Model` **モデルビュー**] をポイントし、[**ダイアグラムビュー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-115">In the model designer, click on the `Model` menu, then point to **Model View**, and then click **Diagram View**.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="7e4ad-116">モデル デザイナーの右上にあるミニマップ コントロールを使用すると、ダイアグラム ビューでのオブジェクトの表示方法を変更できます。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-116">Use the Minimap controls at the top-right of the model designer to change how you can view objects in Diagram View.</span></span> <span data-ttu-id="7e4ad-117">ダイアグラム ビューでモデルを移動した場合、プロジェクトを保存する際にそのビューが保持されます。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-117">If you reposition objects in Diagram View, that view will be retained when you save the project.</span></span>  
  
2.  <span data-ttu-id="7e4ad-118">モデルデザイナーでテーブルを右クリックし、 `Product` [**階層の作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-118">In the model designer, right-click the `Product` table, and then click **Create Hierarchy**.</span></span> <span data-ttu-id="7e4ad-119">テーブル ウィンドウの下部に新しい階層が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-119">A new hierarchy appears at the bottom of the table window.</span></span>  
  
3.  <span data-ttu-id="7e4ad-120">階層名に「」と入力して階層の名前を変更し、enter `Category` キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-120">In the hierarchy name, rename the hierarchy by typing `Category`, and then press ENTER.</span></span>  
  
4.  <span data-ttu-id="7e4ad-121">テーブルで、 `Product` **Product Category Name**列をクリックし、それを階層にドラッグして、 `Category` 名前の上にリリースし `Category` ます。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-121">In the `Product` table, click the **Product Category Name** column, then drag it to the `Category` hierarchy, and then release on top of the `Category` name.</span></span>  
  
5.  <span data-ttu-id="7e4ad-122">階層で、 `Category` **Product Category Name**列を右クリックし、[名前の**変更**] をクリックして「」と入力し `Category` ます。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-122">In the `Category` hierarchy, right-click the **Product Category Name** column, then click **Rename**, and then type `Category`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7e4ad-123">階層内の列の名前を変更しても、テーブル内のその列の名前は変更されません。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-123">Renaming a column in a hierarchy does not rename that column in the table.</span></span> <span data-ttu-id="7e4ad-124">階層内の列は、テーブル内の列の 1 つの表現形態に過ぎません。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-124">A column in a hierarchy is just a representation of the column in the table.</span></span>  
  
6.  <span data-ttu-id="7e4ad-125">テーブルで、 `Product` **Product サブカテゴリ名**列を右クリックし、コンテキストメニューで [**階層に追加**] をポイントして、[] をクリックし `Category` ます。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-125">In the `Product` table, right-click the **Product Subcategory Name** column, then in the context menu, point to **Add to Hierarchy**, and then click `Category`.</span></span>  
  
7.  <span data-ttu-id="7e4ad-126">**製品サブカテゴリ名**をに変更 `Subcategory` します。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-126">Rename **Product Subcategory Name** to `Subcategory`.</span></span>  
  
8.  <span data-ttu-id="7e4ad-127">クリックしてドラッグするか、コンテキストメニューの [**階層に追加**] コマンドを使用して、**モデル名**と**製品名**の列を順番に追加し、 **product サブカテゴリ名**列の下に配置します。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-127">By using click and drag, or by using the **Add to Hierarchy** command in the context menu, add the **Model Name** and **Product Name** columns (in order) and place them beneath the **Product Subcategory Name** column.</span></span> <span data-ttu-id="7e4ad-128">これらの列の名前をそれぞれ変更し `Model` `Product` ます。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-128">Rename these columns `Model` and `Product`, respectively.</span></span>  
  
#### <a name="to-create-hierarchies-in-the-date-table"></a><span data-ttu-id="7e4ad-129">Date テーブル内に階層を作成するには</span><span class="sxs-lookup"><span data-stu-id="7e4ad-129">To create hierarchies in the Date table</span></span>  
  
1.  <span data-ttu-id="7e4ad-130">モデル デザイナーで、 **Date** テーブルをクリックし、 **[階層の作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-130">In the model designer, right-click the **Date** table, and then click **Create Hierarchy**.</span></span>  
  
2.  <span data-ttu-id="7e4ad-131">階層の名前を **Calendar**に変更します。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-131">Rename the hierarchy to **Calendar**.</span></span>  
  
3.  <span data-ttu-id="7e4ad-132">次の列を (順序どおりに) 追加し、名前を次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-132">Add the following columns, in-order, and then rename them:</span></span>  
  
    |<span data-ttu-id="7e4ad-133">列</span><span class="sxs-lookup"><span data-stu-id="7e4ad-133">Column</span></span>|<span data-ttu-id="7e4ad-134">変更後の名前</span><span class="sxs-lookup"><span data-stu-id="7e4ad-134">Rename to:</span></span>|  
    |------------|----------------|  
    |<span data-ttu-id="7e4ad-135">Calendar Year</span><span class="sxs-lookup"><span data-stu-id="7e4ad-135">Calendar Year</span></span>|<span data-ttu-id="7e4ad-136">年</span><span class="sxs-lookup"><span data-stu-id="7e4ad-136">Year</span></span>|  
    |<span data-ttu-id="7e4ad-137">Calendar Semester</span><span class="sxs-lookup"><span data-stu-id="7e4ad-137">Calendar Semester</span></span>|<span data-ttu-id="7e4ad-138">Semester</span><span class="sxs-lookup"><span data-stu-id="7e4ad-138">Semester</span></span>|  
    |<span data-ttu-id="7e4ad-139">Calendar Quarter</span><span class="sxs-lookup"><span data-stu-id="7e4ad-139">Calendar Quarter</span></span>|<span data-ttu-id="7e4ad-140">Quarter</span><span class="sxs-lookup"><span data-stu-id="7e4ad-140">Quarter</span></span>|  
    |<span data-ttu-id="7e4ad-141">Month Calendar</span><span class="sxs-lookup"><span data-stu-id="7e4ad-141">Month Calendar</span></span>|<span data-ttu-id="7e4ad-142">Month</span><span class="sxs-lookup"><span data-stu-id="7e4ad-142">Month</span></span>|  
    |<span data-ttu-id="7e4ad-143">Day Of Month</span><span class="sxs-lookup"><span data-stu-id="7e4ad-143">Day Of Month</span></span>|<span data-ttu-id="7e4ad-144">日間</span><span class="sxs-lookup"><span data-stu-id="7e4ad-144">Day</span></span>|  
  
4.  <span data-ttu-id="7e4ad-145">**Date** テーブルで上記の手順を繰り返し、次の列を含んだ **Fiscal** 階層を作成します。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-145">In the **Date** table, repeat the above steps, creating a **Fiscal** hierarchy, including the following columns:</span></span>  
  
    |<span data-ttu-id="7e4ad-146">列</span><span class="sxs-lookup"><span data-stu-id="7e4ad-146">Column</span></span>|<span data-ttu-id="7e4ad-147">変更後の名前</span><span class="sxs-lookup"><span data-stu-id="7e4ad-147">Rename to:</span></span>|  
    |------------|----------------|  
    |<span data-ttu-id="7e4ad-148">Fiscal Year</span><span class="sxs-lookup"><span data-stu-id="7e4ad-148">Fiscal Year</span></span>|<span data-ttu-id="7e4ad-149">年</span><span class="sxs-lookup"><span data-stu-id="7e4ad-149">Year</span></span>|  
    |<span data-ttu-id="7e4ad-150">Fiscal Semester</span><span class="sxs-lookup"><span data-stu-id="7e4ad-150">Fiscal Semester</span></span>|<span data-ttu-id="7e4ad-151">Semester</span><span class="sxs-lookup"><span data-stu-id="7e4ad-151">Semester</span></span>|  
    |<span data-ttu-id="7e4ad-152">Fiscal Quarter</span><span class="sxs-lookup"><span data-stu-id="7e4ad-152">Fiscal Quarter</span></span>|<span data-ttu-id="7e4ad-153">Quarter</span><span class="sxs-lookup"><span data-stu-id="7e4ad-153">Quarter</span></span>|  
    |<span data-ttu-id="7e4ad-154">Month Calendar</span><span class="sxs-lookup"><span data-stu-id="7e4ad-154">Month Calendar</span></span>|<span data-ttu-id="7e4ad-155">Month</span><span class="sxs-lookup"><span data-stu-id="7e4ad-155">Month</span></span>|  
    |<span data-ttu-id="7e4ad-156">Day Of Month</span><span class="sxs-lookup"><span data-stu-id="7e4ad-156">Day Of Month</span></span>|<span data-ttu-id="7e4ad-157">日間</span><span class="sxs-lookup"><span data-stu-id="7e4ad-157">Day</span></span>|  
  
5.  <span data-ttu-id="7e4ad-158">最後に、 **Date** テーブルで上記の手順を繰り返し、次の列を含んだ **Production Calendar** 階層を作成します。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-158">Finally, in the **Date** table, repeat the above steps, creating a **Production Calendar** hierarchy, including the following columns:</span></span>  
  
    |<span data-ttu-id="7e4ad-159">列</span><span class="sxs-lookup"><span data-stu-id="7e4ad-159">Column</span></span>|<span data-ttu-id="7e4ad-160">変更後の名前</span><span class="sxs-lookup"><span data-stu-id="7e4ad-160">Rename to:</span></span>|  
    |------------|----------------|  
    |<span data-ttu-id="7e4ad-161">Calendar Year</span><span class="sxs-lookup"><span data-stu-id="7e4ad-161">Calendar Year</span></span>|<span data-ttu-id="7e4ad-162">年</span><span class="sxs-lookup"><span data-stu-id="7e4ad-162">Year</span></span>|  
    |<span data-ttu-id="7e4ad-163">Week Number Of Year</span><span class="sxs-lookup"><span data-stu-id="7e4ad-163">Week Number Of Year</span></span>|<span data-ttu-id="7e4ad-164">週</span><span class="sxs-lookup"><span data-stu-id="7e4ad-164">Week</span></span>|  
    |<span data-ttu-id="7e4ad-165">Day Of Week</span><span class="sxs-lookup"><span data-stu-id="7e4ad-165">Day Of Week</span></span>|<span data-ttu-id="7e4ad-166">日間</span><span class="sxs-lookup"><span data-stu-id="7e4ad-166">Day</span></span>|  
  
## <a name="next-steps"></a><span data-ttu-id="7e4ad-167">次の手順</span><span class="sxs-lookup"><span data-stu-id="7e4ad-167">Next Steps</span></span>  
 <span data-ttu-id="7e4ad-168">このチュートリアルを続行するには、次のレッスン [「レッスン 11: パーティションの作成」](lesson-10-create-partitions.md)に進んでください。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-168">To continue this tutorial, go to the next lesson: [Lesson 11: Create Partitions](lesson-10-create-partitions.md).</span></span>  
  
  
