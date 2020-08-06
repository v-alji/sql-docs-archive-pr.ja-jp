---
title: パースペクティブの定義と参照 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 766004b9-6578-4914-a445-6f44843a5fb0
author: minewiskan
ms.author: owend
ms.openlocfilehash: c9658098180618c2d5d6d6d9e00e7a7e4a6c4231
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718860"
---
# <a name="defining-and-browsing-perspectives"></a><span data-ttu-id="a3be7-102">パースペクティブの定義と表示</span><span class="sxs-lookup"><span data-stu-id="a3be7-102">Defining and Browsing Perspectives</span></span>
  <span data-ttu-id="a3be7-103">パースペクティブを使用すれば、特定の目的に従ってキューブの表示を単純化できます。</span><span class="sxs-lookup"><span data-stu-id="a3be7-103">A perspective can simplify the view of a cube for specific purposes.</span></span> <span data-ttu-id="a3be7-104">既定では、ユーザーはアクセスする権限のあるキューブ内のすべての要素を表示できます。</span><span class="sxs-lookup"><span data-stu-id="a3be7-104">By default, users can see all of the elements in a cube to which they have permissions.</span></span> <span data-ttu-id="a3be7-105">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] キューブ全体の表示時に表示されるものが、キューブの既定のパースペクティブです。</span><span class="sxs-lookup"><span data-stu-id="a3be7-105">What users are viewing when they view an entire [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube is the default perspective for the cube.</span></span> <span data-ttu-id="a3be7-106">キューブ全体を表示すると、操作が非常に複雑になる可能性があります。特に、ビジネス インテリジェンスやレポートの要件に応じてキューブのごく一部分しか操作する必要のないユーザーにとっては複雑すぎます。</span><span class="sxs-lookup"><span data-stu-id="a3be7-106">A view of the whole cube can be very complex for users to navigate, especially for users who only need to interact with a small part of the cube to satisfy their business intelligence and reporting requirements.</span></span>  
  
 <span data-ttu-id="a3be7-107">キューブの表示上の複雑さを軽減するために、 *パースペクティブ*、つまりキューブの表示可能なサブセットを作成することができます。こうすれば、キューブ内のメジャー グループ、メジャー、ディメンション、属性、階層、主要業績評価指標 (KPI)、アクション、計算されるメンバーのうちの一部分だけがユーザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3be7-107">To reduce the apparent complexity of a cube, you can create viewable subsets of the cube, called *perspectives*, which show users only a part of the measure groups, measures, dimensions, attributes, hierarchies, Key Performance Indicators (KPIs), actions, and calculated members in the cube.</span></span> <span data-ttu-id="a3be7-108">これは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]の以前のリリース用に作成されたクライアント アプリケーションを使用する場合は特に有効です。</span><span class="sxs-lookup"><span data-stu-id="a3be7-108">This can be particularly useful for working with client applications that were written for a previous release of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="a3be7-109">たとえば、これらのクライアントにはフォルダーやパースペクティブを表示する概念はありませんが、パースペクティブはあたかもキューブであるかのように古いクライアントに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3be7-109">These clients have no concept of display folders or perspectives, for example, but a perspective appears to older clients as if it were a cube.</span></span> <span data-ttu-id="a3be7-110">詳細については、「 [パースペクティブ](multidimensional-models-olap-logical-cube-objects/perspectives.md)」および「 [多次元モデルのパースペクティブ](multidimensional-models/perspectives-in-multidimensional-models.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3be7-110">For more information, see [Perspectives](multidimensional-models-olap-logical-cube-objects/perspectives.md), and [Perspectives in Multidimensional Models](multidimensional-models/perspectives-in-multidimensional-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3be7-111">パースペクティブはセキュリティ上のメカニズムではなく、ユーザー エクスペリエンスを改善するためのツールです。</span><span class="sxs-lookup"><span data-stu-id="a3be7-111">A perspective is not a security mechanism, but instead is a tool for providing a better user experience.</span></span> <span data-ttu-id="a3be7-112">パースペクティブのセキュリティはすべて、基になるキューブから継承されます。</span><span class="sxs-lookup"><span data-stu-id="a3be7-112">All security for a perspective is inherited from the underlying cube.</span></span>  
  
 <span data-ttu-id="a3be7-113">このトピックの作業では、いくつかの異なるパースペクティブを定義した後、それぞれの新しいパースペクティブを使用してキューブを表示します。</span><span class="sxs-lookup"><span data-stu-id="a3be7-113">In the tasks in this topic, you will define several different perspectives and then browse the cube through each of these new perspectives.</span></span>  
  
## <a name="defining-an-internet-sales-perspective"></a><span data-ttu-id="a3be7-114">Internet Sales パースペクティブの定義</span><span class="sxs-lookup"><span data-stu-id="a3be7-114">Defining an Internet Sales Perspective</span></span>  
  
1.  <span data-ttu-id="a3be7-115">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーを開いて、 **[パースペクティブ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3be7-115">Open Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Perspectives** tab.</span></span>  
  
     <span data-ttu-id="a3be7-116">次の図のように、すべてのオブジェクトとその種類が **[パースペクティブ]** ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3be7-116">All the objects and their object types appear in the **Perspectives** pane, as shown in the following image.</span></span>  
  
     <span data-ttu-id="a3be7-117">![キューブ デザイナーの [パースペクティブ] ペイン](../../2014/tutorials/media/l9-perspectives-1.gif "キューブ デザイナーの [パースペクティブ] ペイン")</span><span class="sxs-lookup"><span data-stu-id="a3be7-117">![Perspectives pane of Cube Designer](../../2014/tutorials/media/l9-perspectives-1.gif "Perspectives pane of Cube Designer")</span></span>  
  
2.  <span data-ttu-id="a3be7-118">**[パースペクティブ]** タブのツール バーの **[新しいパースペクティブ]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3be7-118">On the toolbar of the **Perspectives** tab, click the **New Perspective** button.</span></span>  
  
     <span data-ttu-id="a3be7-119">次の図のように、新しいパースペクティブの既定の名前 " **パースペクティブ** " が **[パースペクティブ名]** 列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3be7-119">A new perspective appears in the **Perspective Name** column with a default name of **Perspective**, as shown in the following image.</span></span> <span data-ttu-id="a3be7-120">各オブジェクトのチェック ボックスはオンになっています。いずれかのオブジェクトのチェック ボックスをオフにするまでは、このキューブの既定のパースペクティブと同じ表示内容になります。</span><span class="sxs-lookup"><span data-stu-id="a3be7-120">Notice that the check box for every object is selected; until you clear the check box for an object, this perspective is identical to the default perspective of this cube.</span></span>  
  
     <span data-ttu-id="a3be7-121">![[パースペクティブ名] 列の新しいパースペクティブ](../../2014/tutorials/media/l9-perspectives-2.gif "[パースペクティブ名] 列の新しいパースペクティブ")</span><span class="sxs-lookup"><span data-stu-id="a3be7-121">![New perspective in Perspective Name column](../../2014/tutorials/media/l9-perspectives-2.gif "New perspective in Perspective Name column")</span></span>  
  
3.  <span data-ttu-id="a3be7-122">パースペクティブ名をに変更 `Internet Sales` します。</span><span class="sxs-lookup"><span data-stu-id="a3be7-122">Change the perspective name to `Internet Sales`.</span></span>  
  
4.  <span data-ttu-id="a3be7-123">次の行で、DefaultMeasure を **[Internet Sales-Sales Amount]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="a3be7-123">On the next row, set the DefaultMeasure to **Internet Sales-Sales Amount**.</span></span>  
  
     <span data-ttu-id="a3be7-124">ユーザーがこのパースペクティブを使ってキューブを表示する場合、他のメジャーをユーザーが指定しない限り、このメジャーがユーザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3be7-124">When users browse the cube by using this perspective, this will be the measure that the users see unless they specify some other measure.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a3be7-125">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブ全体の既定のメジャーは、キューブの **[キューブ構造]** タブのプロパティ ウィンドウでも設定できます。</span><span class="sxs-lookup"><span data-stu-id="a3be7-125">You can also set the default measure for the whole [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube in the Properties window on the **Cube Structure** tab for the cube.</span></span>  
  
5.  <span data-ttu-id="a3be7-126">次のオブジェクトのチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="a3be7-126">Clear the check box for the following objects:</span></span>  
  
    -   <span data-ttu-id="a3be7-127">`Reseller Sales`メジャーグループ</span><span class="sxs-lookup"><span data-stu-id="a3be7-127">`Reseller Sales` measure group</span></span>  
  
    -   <span data-ttu-id="a3be7-128">**Sales Quotas** メジャー グループ</span><span class="sxs-lookup"><span data-stu-id="a3be7-128">**Sales Quotas** measure group</span></span>  
  
    -   <span data-ttu-id="a3be7-129">**Sales Quotas 1** メジャー グループ</span><span class="sxs-lookup"><span data-stu-id="a3be7-129">**Sales Quotas 1** measure group</span></span>  
  
    -   <span data-ttu-id="a3be7-130">**Reseller** キューブ ディメンション</span><span class="sxs-lookup"><span data-stu-id="a3be7-130">**Reseller** cube dimension</span></span>  
  
    -   <span data-ttu-id="a3be7-131">**Reseller Geography** キューブ ディメンション</span><span class="sxs-lookup"><span data-stu-id="a3be7-131">**Reseller Geography** cube dimension</span></span>  
  
    -   <span data-ttu-id="a3be7-132">**Sales Territory** キューブ ディメンション</span><span class="sxs-lookup"><span data-stu-id="a3be7-132">**Sales Territory** cube dimension</span></span>  
  
    -   <span data-ttu-id="a3be7-133">**Employee** キューブ ディメンション</span><span class="sxs-lookup"><span data-stu-id="a3be7-133">**Employee** cube dimension</span></span>  
  
    -   <span data-ttu-id="a3be7-134">**Promotion** キューブ ディメンション</span><span class="sxs-lookup"><span data-stu-id="a3be7-134">**Promotion** cube dimension</span></span>  
  
    -   <span data-ttu-id="a3be7-135">**Reseller Revenue** KPI</span><span class="sxs-lookup"><span data-stu-id="a3be7-135">**Reseller Revenue** KPI</span></span>  
  
    -   <span data-ttu-id="a3be7-136">**Large Resellers** 名前付きセット</span><span class="sxs-lookup"><span data-stu-id="a3be7-136">**Large Resellers** named set</span></span>  
  
    -   <span data-ttu-id="a3be7-137">計算されるメンバー**Total Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="a3be7-137">**Total Sales Amount** calculated member</span></span>  
  
    -   <span data-ttu-id="a3be7-138">計算されるメンバー**Total Product Cost**</span><span class="sxs-lookup"><span data-stu-id="a3be7-138">**Total Product Cost** calculated member</span></span>  
  
    -   <span data-ttu-id="a3be7-139">計算されるメンバー**Reseller GPM**</span><span class="sxs-lookup"><span data-stu-id="a3be7-139">**Reseller GPM** calculated member</span></span>  
  
    -   <span data-ttu-id="a3be7-140">計算されるメンバー**Total GPM**</span><span class="sxs-lookup"><span data-stu-id="a3be7-140">**Total GPM** calculated member</span></span>  
  
    -   <span data-ttu-id="a3be7-141">計算されるメンバー**Reseller Sales Ratio to All Products**</span><span class="sxs-lookup"><span data-stu-id="a3be7-141">**Reseller Sales Ratio to All Products** calculated member</span></span>  
  
    -   <span data-ttu-id="a3be7-142">計算されるメンバー**Total Sales Ratio to All Products**</span><span class="sxs-lookup"><span data-stu-id="a3be7-142">**Total Sales Ratio to All Products** calculated member</span></span>  
  
     <span data-ttu-id="a3be7-143">これらのオブジェクトはインターネット販売とは関係がありません。</span><span class="sxs-lookup"><span data-stu-id="a3be7-143">These objects do not relate to Internet sales.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a3be7-144">さらに、ディメンションごとに、パースペクティブに表示するユーザー定義階層と属性を個別に選択できます。</span><span class="sxs-lookup"><span data-stu-id="a3be7-144">Within each dimension, you can also individually select the user-defined hierarchies and attributes that you want to appear in a perspective.</span></span>  
  
## <a name="defining-a-reseller-sales-perspective"></a><span data-ttu-id="a3be7-145">Reseller Sales パースペクティブの定義</span><span class="sxs-lookup"><span data-stu-id="a3be7-145">Defining a Reseller Sales Perspective</span></span>  
  
1.  <span data-ttu-id="a3be7-146">**[パースペクティブ]** タブのツール バーの **[新しいパースペクティブ]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3be7-146">On the toolbar of the **Perspectives** tab, click the **New Perspective** button.</span></span>  
  
2.  <span data-ttu-id="a3be7-147">新しいパースペクティブの名前をに変更し `Reseller Sales` ます。</span><span class="sxs-lookup"><span data-stu-id="a3be7-147">Change the name of the new perspective to `Reseller Sales`.</span></span>  
  
3.  <span data-ttu-id="a3be7-148">既定のメジャーとして **[Reseller Sales-Sales Amount]** を設定します。</span><span class="sxs-lookup"><span data-stu-id="a3be7-148">Set **Reseller Sales-Sales Amount** as the default measure.</span></span>  
  
     <span data-ttu-id="a3be7-149">ユーザーがこのパースペクティブを使用してキューブを表示するとき、他のメジャーをユーザーが指定しない限り、このメジャーがユーザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3be7-149">When users browse the cube by using this perspective, this measure will be the measure that the users will see unless they specify some other measure.</span></span>  
  
4.  <span data-ttu-id="a3be7-150">次のオブジェクトのチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="a3be7-150">Clear the check box for the following objects:</span></span>  
  
    -   <span data-ttu-id="a3be7-151">`Internet Sales`メジャーグループ</span><span class="sxs-lookup"><span data-stu-id="a3be7-151">`Internet Sales` measure group</span></span>  
  
    -   <span data-ttu-id="a3be7-152">**Internet Sales Reason** メジャー グループ</span><span class="sxs-lookup"><span data-stu-id="a3be7-152">**Internet Sales Reason** measure group</span></span>  
  
    -   <span data-ttu-id="a3be7-153">**Customer** キューブ ディメンション</span><span class="sxs-lookup"><span data-stu-id="a3be7-153">**Customer** cube dimension</span></span>  
  
    -   <span data-ttu-id="a3be7-154">**Internet Sales Order Details** キューブ ディメンション</span><span class="sxs-lookup"><span data-stu-id="a3be7-154">**Internet Sales Order Details** cube dimension</span></span>  
  
    -   <span data-ttu-id="a3be7-155">**Sales Reason** キューブ ディメンション</span><span class="sxs-lookup"><span data-stu-id="a3be7-155">**Sales Reason** cube dimension</span></span>  
  
    -   <span data-ttu-id="a3be7-156">**Internet Sales Details Drillthrough Action** ドリルスルー アクション</span><span class="sxs-lookup"><span data-stu-id="a3be7-156">**Internet Sales Details Drillthrough Action** drillthrough action</span></span>  
  
    -   <span data-ttu-id="a3be7-157">計算されるメンバー**Total Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="a3be7-157">**Total Sales Amount** calculated member</span></span>  
  
    -   <span data-ttu-id="a3be7-158">計算されるメンバー**Total Product Cost**</span><span class="sxs-lookup"><span data-stu-id="a3be7-158">**Total Product Cost** calculated member</span></span>  
  
    -   <span data-ttu-id="a3be7-159">計算されるメンバー**Internet GPM**</span><span class="sxs-lookup"><span data-stu-id="a3be7-159">**Internet GPM** calculated member</span></span>  
  
    -   <span data-ttu-id="a3be7-160">計算されるメンバー**Total GPM**</span><span class="sxs-lookup"><span data-stu-id="a3be7-160">**Total GPM** calculated member</span></span>  
  
    -   <span data-ttu-id="a3be7-161">計算されるメンバー**Internet Sales Ratio to All Products**</span><span class="sxs-lookup"><span data-stu-id="a3be7-161">**Internet Sales Ratio to All Products** calculated member</span></span>  
  
    -   <span data-ttu-id="a3be7-162">計算されるメンバー**Total Sales Ratio to All Products**</span><span class="sxs-lookup"><span data-stu-id="a3be7-162">**Total Sales Ratio to All Products** calculated member</span></span>  
  
     <span data-ttu-id="a3be7-163">これらのオブジェクトは再販業者の販売とは関係がありません。</span><span class="sxs-lookup"><span data-stu-id="a3be7-163">These objects do not relate to resellers sales.</span></span>  
  
## <a name="defining-a-sales-summary-perspective"></a><span data-ttu-id="a3be7-164">Sales Summary パースペクティブの定義</span><span class="sxs-lookup"><span data-stu-id="a3be7-164">Defining a Sales Summary Perspective</span></span>  
  
1.  <span data-ttu-id="a3be7-165">**[パースペクティブ]** タブのツール バーの **[新しいパースペクティブ]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3be7-165">On the toolbar of the **Perspectives** tab, click the **New Perspective** button.</span></span>  
  
2.  <span data-ttu-id="a3be7-166">新しいパースペクティブの名前をに変更し `Sales Summary` ます。</span><span class="sxs-lookup"><span data-stu-id="a3be7-166">Change the name of the new perspective to `Sales Summary`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a3be7-167">計算されるメジャーを既定のメジャーとして指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="a3be7-167">You cannot specify a calculated measure as the default measure.</span></span>  
  
3.  <span data-ttu-id="a3be7-168">次のオブジェクトのチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="a3be7-168">Clear the check box for the following objects:</span></span>  
  
    -   <span data-ttu-id="a3be7-169">`Internet Sales`メジャーグループ</span><span class="sxs-lookup"><span data-stu-id="a3be7-169">`Internet Sales` measure group</span></span>  
  
    -   <span data-ttu-id="a3be7-170">`Reseller Sales`メジャーグループ</span><span class="sxs-lookup"><span data-stu-id="a3be7-170">`Reseller Sales` measure group</span></span>  
  
    -   <span data-ttu-id="a3be7-171">**Internet Sales Reason** メジャー グループ</span><span class="sxs-lookup"><span data-stu-id="a3be7-171">**Internet Sales Reason** measure group</span></span>  
  
    -   <span data-ttu-id="a3be7-172">**Sales Quotas** メジャー グループ</span><span class="sxs-lookup"><span data-stu-id="a3be7-172">**Sales Quotas** measure group</span></span>  
  
    -   <span data-ttu-id="a3be7-173">**Sales Quotas1** メジャー グループ</span><span class="sxs-lookup"><span data-stu-id="a3be7-173">**Sales Quotas1** measure group</span></span>  
  
    -   <span data-ttu-id="a3be7-174">**Internet Sales Order Details** キューブ ディメンション</span><span class="sxs-lookup"><span data-stu-id="a3be7-174">**Internet Sales Order Details** cube dimension</span></span>  
  
    -   <span data-ttu-id="a3be7-175">**Sales Reason** キューブ ディメンション</span><span class="sxs-lookup"><span data-stu-id="a3be7-175">**Sales Reason** cube dimension</span></span>  
  
    -   <span data-ttu-id="a3be7-176">**Internet Sales Details Drillthrough Action** ドリルスルー アクション</span><span class="sxs-lookup"><span data-stu-id="a3be7-176">**Internet Sales Details Drillthrough Action** drillthrough action</span></span>  
  
4.  <span data-ttu-id="a3be7-177">次のオブジェクトのチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="a3be7-177">Select the check box for the following objects:</span></span>  
  
    -   <span data-ttu-id="a3be7-178">**Internet Sales Count** メジャー</span><span class="sxs-lookup"><span data-stu-id="a3be7-178">**Internet Sales Count** measure</span></span>  
  
    -   <span data-ttu-id="a3be7-179">**Reseller Sales Count** メジャー</span><span class="sxs-lookup"><span data-stu-id="a3be7-179">**Reseller Sales Count** measure</span></span>  
  
## <a name="browsing-the-cube-through-each-perspective"></a><span data-ttu-id="a3be7-180">各パースペクティブを使用したキューブの表示</span><span class="sxs-lookup"><span data-stu-id="a3be7-180">Browsing the Cube Through Each Perspective</span></span>  
  
1.  <span data-ttu-id="a3be7-181">**[ビルド]** メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3be7-181">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="a3be7-182">配置が正常に完了したら、 **[ブラウザー]** タブに切り替えて、 **[再接続]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3be7-182">When deployment has successfully completed, switch to the **Browser** tab, and then click the **Reconnect** button.</span></span>  
  
3.  <span data-ttu-id="a3be7-183">Excel を起動します。</span><span class="sxs-lookup"><span data-stu-id="a3be7-183">Start Excel.</span></span>  
  
4.  <span data-ttu-id="a3be7-184">次の図のように、Excel の分析機能では、Excel でモデルを参照するときに使用するパースペクティブを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="a3be7-184">Analyze in Excel prompts you to choose which perspective to use when browsing the model in Excel, as shown in the following image.</span></span>  
  
     <span data-ttu-id="a3be7-185">![[Internet Sales] パースペクティブのオブジェクト](../../2014/tutorials/media/l9-perspectives-3.gif "[Internet Sales] パースペクティブのオブジェクト")</span><span class="sxs-lookup"><span data-stu-id="a3be7-185">![Objects for the Internet Sales perspective](../../2014/tutorials/media/l9-perspectives-3.gif "Objects for the Internet Sales perspective")</span></span>  
  
5.  <span data-ttu-id="a3be7-186">または、Windows の [スタート] メニューから Excel を起動して、次の図のように、データ接続ウィザードで localhost 上の Analysis Services Tutorial データベースへの接続を定義し、パースペクティブを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="a3be7-186">Alternatively, you can start Excel from the Windows Start menu, define a connection to the Analysis Services Tutorial database on localhost, and choose a perspective in the Data Connection wizard, as shown in the following image.</span></span>  
  
     <span data-ttu-id="a3be7-187">![Excel でのデータ接続ウィザード](../../2014/tutorials/media/l9-perspectives-3b.gif "Excel でのデータ接続ウィザード")</span><span class="sxs-lookup"><span data-stu-id="a3be7-187">![Data Connection wizard in Excel](../../2014/tutorials/media/l9-perspectives-3b.gif "Data Connection wizard in Excel")</span></span>  
  
6.  <span data-ttu-id="a3be7-188">[ `Internet Sales` **パースペクティブ**] ボックスの一覧でを選択し、[メタデータ] ペインでメジャーとディメンションを確認します。</span><span class="sxs-lookup"><span data-stu-id="a3be7-188">Select `Internet Sales` in the **Perspective** list and then review the measures and dimensions in the metadata pane.</span></span>  
  
     <span data-ttu-id="a3be7-189">Internet Sales パースペクティブ用に指定されたオブジェクトだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3be7-189">Notice that only those objects that are specified for the Internet Sales perspective appear.</span></span>  
  
7.  <span data-ttu-id="a3be7-190">メタデータ ペインで、 **[Measures]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="a3be7-190">In the metadata pane, expand **Measures**.</span></span>  
  
     <span data-ttu-id="a3be7-191">`Internet Sales`メジャーグループのみが表示され、**インターネット GPM**と、計算される**すべての製品の internet Sales 比率**が計算されるメンバーになります。</span><span class="sxs-lookup"><span data-stu-id="a3be7-191">Notice that only the `Internet Sales` measure group appears, together with the **Internet GPM** and **Internet Sales Ratio to All Products** calculated members.</span></span>  
  
8.  <span data-ttu-id="a3be7-192">モデルで再度 Excel を選択します。</span><span class="sxs-lookup"><span data-stu-id="a3be7-192">In the model, select Excel again.</span></span> <span data-ttu-id="a3be7-193">[`Sales Summary`] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a3be7-193">Select `Sales Summary`.</span></span>  
  
     <span data-ttu-id="a3be7-194">次の図のように、これらの各メジャー グループには 1 つのメジャーだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3be7-194">Notice that in each of these measure groups, only a single measure appears, as shown in the following image.</span></span>  
  
     <span data-ttu-id="a3be7-195">![[Internet Sales] および [Reseller Sales] メジャー](../../2014/tutorials/media/l9-perspectives-4.gif "[Internet Sales] および [Reseller Sales] メジャー")</span><span class="sxs-lookup"><span data-stu-id="a3be7-195">![Internet Sales and Reseller Sales measures](../../2014/tutorials/media/l9-perspectives-4.gif "Internet Sales and Reseller Sales measures")</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="a3be7-196">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="a3be7-196">Next Task in Lesson</span></span>  
 [<span data-ttu-id="a3be7-197">翻訳の定義と表示</span><span class="sxs-lookup"><span data-stu-id="a3be7-197">Defining and Browsing Translations</span></span>](lesson-9-2-defining-and-browsing-translations.md)  
  
## <a name="see-also"></a><span data-ttu-id="a3be7-198">参照</span><span class="sxs-lookup"><span data-stu-id="a3be7-198">See Also</span></span>  
 <span data-ttu-id="a3be7-199">[ビジョン](multidimensional-models-olap-logical-cube-objects/perspectives.md) </span><span class="sxs-lookup"><span data-stu-id="a3be7-199">[Perspectives](multidimensional-models-olap-logical-cube-objects/perspectives.md) </span></span>  
 [<span data-ttu-id="a3be7-200">多次元モデルのパースペクティブ</span><span class="sxs-lookup"><span data-stu-id="a3be7-200">Perspectives in Multidimensional Models</span></span>](multidimensional-models/perspectives-in-multidimensional-models.md)  
  
  
