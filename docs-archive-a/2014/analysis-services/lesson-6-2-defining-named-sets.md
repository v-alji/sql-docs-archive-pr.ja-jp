---
title: 名前付きセットの定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 47254fd3-525f-4c35-b93d-316607652517
author: minewiskan
ms.author: owend
ms.openlocfilehash: e02f4624dc0ec25ee0c3d8950c83550ca3d9ed57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639749"
---
# <a name="defining-named-sets"></a><span data-ttu-id="6b3dd-102">名前付きセットの定義</span><span class="sxs-lookup"><span data-stu-id="6b3dd-102">Defining Named Sets</span></span>
  <span data-ttu-id="6b3dd-103">名前付きセットとは、ディメンション メンバーのセットを返す多次元式 (MDX) です。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-103">A named set is a Multidimensional Expressions (MDX) expression that returns a set of dimension members.</span></span> <span data-ttu-id="6b3dd-104">名前付きセットを定義し、キューブ定義の一部として保存できます。さらに、名前付きセットをクライアント アプリケーションで作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-104">You can define named sets and save them as part of the cube definition; you can also create named sets in client applications.</span></span> <span data-ttu-id="6b3dd-105">名前付きセットは、キューブ データ、算術演算子、数値、関数を組み合わせることによって作成します。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-105">You create named sets by combining cube data, arithmetic operators, numbers, and functions.</span></span> <span data-ttu-id="6b3dd-106">名前付きセットは、クライアント アプリケーションの MDX クエリの中で使用できます。また、サブキューブのセットを定義するときも使用できます。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-106">Named sets can be used by users in MDX queries in client applications and can also be used to define sets in subcubes.</span></span> <span data-ttu-id="6b3dd-107">サブキューブは、クロス結合によるセットのコレクションであり、後続のステートメントに対して、キューブ空間を定義されたサブスペースに制限します。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-107">A subcube is a collection of crossjoined sets that restricts the cube space to the defined subspace for subsequent statements.</span></span> <span data-ttu-id="6b3dd-108">制限されたキューブ領域の定義は MDX スクリプティングの基本概念です。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-108">Defining a restricted cube space is a fundamental concept to MDX scripting.</span></span>

 <span data-ttu-id="6b3dd-109">名前付きセットを使用すると、MDX クエリを単純化することができ、よく使用する複雑なセット式に対して便利な別名を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-109">Named sets simplify MDX queries and provide useful aliases for complex, typically used, set expressions.</span></span> <span data-ttu-id="6b3dd-110">たとえば、従業員が最も多い Reseller ディメンションのメンバーを含む Large Resellers 名前付きセットを定義できます。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-110">For example, you can define a named set called Large Resellers that contains the set of members in the Reseller dimension that have the most employees.</span></span> <span data-ttu-id="6b3dd-111">エンド ユーザーはクエリの中でこの Large Resellers 名前付きセットを使用できます。また、サブキューブ内のセットを定義するために名前付きセットを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-111">End users could then use the Large Resellers named set in queries, or you could use the named set to define a set in a subcube.</span></span> <span data-ttu-id="6b3dd-112">名前付きセットの定義はキューブに格納されますが、その値はメモリにしか存在しません。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-112">Named set definitions are stored in cubes, but their values exist only in memory.</span></span> <span data-ttu-id="6b3dd-113">名前付きセットを作成するには、キューブ デザイナーの **[計算]** タブで **[新しい名前付きセット]** コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-113">To create a named set, use the **New Named Set** command on the **Calculations** tab of Cube Designer.</span></span> <span data-ttu-id="6b3dd-114">詳細については、「 [計算](multidimensional-models-olap-logical-cube-objects/calculations.md)」、「 [名前付きセットの作成](multidimensional-models/create-named-sets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-114">For more information, see [Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md), [Create Named Sets](multidimensional-models/create-named-sets.md).</span></span>

 <span data-ttu-id="6b3dd-115">このトピックの作業では、Core Products と Large Resellers という 2 つの名前付きセットを定義します。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-115">In the tasks in this topic, you will define two named sets: a Core Products named set and a Large Resellers named set.</span></span>

## <a name="defining-a-core-products-named-set"></a><span data-ttu-id="6b3dd-116">Core Products 名前付きセットの定義</span><span class="sxs-lookup"><span data-stu-id="6b3dd-116">Defining a Core Products Named Set</span></span>

1.  <span data-ttu-id="6b3dd-117">**Tutorial キューブのキューブ デザイナーを開いて、** [計算] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] タブに切り替えます。次に、ツール バーの **[フォーム ビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-117">Switch to the **Calculations** tab of Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Form View** on the toolbar.</span></span>

2.  <span data-ttu-id="6b3dd-118">**[スクリプト オーガナイザー]** ペインの **[Total Sales Ratio to All Products]** をクリックして、 **[計算]** タブのツール バーの **[新しい名前付きセット]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-118">Click **[Total Sales Ratio to All Products]** in the **Script Organizer** pane, and then click **New Named Set** on the toolbar of the **Calculations** tab.</span></span>

     <span data-ttu-id="6b3dd-119">**[計算]** タブで新しい計算を定義する場合、計算は **[スクリプト オーガナイザー]** ペインに表示されている順序で解決されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-119">When you define a new calculation on the **Calculations** tab, remember that calculations are resolved in the order in which they appear in the **Script Organizer** pane.</span></span> <span data-ttu-id="6b3dd-120">新しい計算を作成するときにペイン内でフォーカスが置かれている位置によって、計算の実行順序が決まります。新しい計算は、フォーカスが置かれている計算の直後に定義されます。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-120">Your focus within that pane when you create a new calculation determines the order of the execution of the calculation; a new calculation is defined immediately after the calculation on which you are focused.</span></span>

3.  <span data-ttu-id="6b3dd-121">[**名前**] ボックスで、新しい名前付きセットの名前をに変更し `[Core Products]` ます。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-121">In the **Name** box, change the name of the new named set to `[Core Products]`.</span></span>

     <span data-ttu-id="6b3dd-122">**[スクリプト オーガナイザー]** ペインには、スクリプト コマンドまたは計算されるメンバーとは異なる、名前付きセットの固有のアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-122">In the **Script Organizer** pane, notice the unique icon that differentiates a named set from a script command or a calculated member.</span></span>

4.  <span data-ttu-id="6b3dd-123">[**計算ツール**] ペインの [**メタデータ**] タブで、[ **Product**]、[ **Category**]、 `Members` []、[ **All Products**] の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-123">On the **Metadata** tab in the **Calculation Tools** pane, expand **Product**, expand **Category**, expand `Members`, and then expand **All Products**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="6b3dd-124">**[計算ツール]** ペインにメタデータが表示されない場合、ツール バーの **[再接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-124">If you cannot view any metadata in the **Calculation Tools** pane, click **Reconnect** on the toolbar.</span></span> <span data-ttu-id="6b3dd-125">それでも表示されない場合は、キューブを処理するか、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のインスタンスを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-125">If this does not work, you may have to process the cube or start the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>

5.  <span data-ttu-id="6b3dd-126">**[Bikes]** を **[式]** ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-126">Drag **Bikes** into the **Expression** box.</span></span>

     <span data-ttu-id="6b3dd-127">これで、Product ディメンションの Bike カテゴリに属するメンバーのセットを返すセット式を作成できました。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-127">You now have created a set expression that will return the set of members that are in the Bike category in the Product dimension.</span></span>

## <a name="defining-a-large-resellers-named-set"></a><span data-ttu-id="6b3dd-128">Large Resellers 名前付きセットの定義</span><span class="sxs-lookup"><span data-stu-id="6b3dd-128">Defining a Large Resellers Named Set</span></span>

1.  <span data-ttu-id="6b3dd-129">[ `[Core Products]` **スクリプトオーガナイザー** ] ペイン内を右クリックし、[**新しい名前付きセット**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-129">Right-click `[Core Products]` in the **Script Organizer** pane, and then click **New Named Set**.</span></span>

2.  <span data-ttu-id="6b3dd-130">[**名前**] ボックスで、この名前付きセットの名前をに変更し `[Large Resellers]` ます。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-130">In the **Name** box, change the name of this named set to `[Large Resellers]`.</span></span>

3.  <span data-ttu-id="6b3dd-131">[**式**] ボックスに「」と入力 `Exists()` します。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-131">In the **Expression** box, type `Exists()`.</span></span>

     <span data-ttu-id="6b3dd-132">Exists 関数を使用して、Number of Employees 属性階層内の従業員数が多数であるメンバーのセットと交差する、Reseller Name 属性階層のメンバーのセットを返すようにします。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-132">You will use the Exists function to return the set of members from the Reseller Name attribute hierarchy that intersects with the set of members in the Number of Employees attribute hierarchy that has the largest number of employees.</span></span>

4.  <span data-ttu-id="6b3dd-133">**[計算ツール]** ペインの **[メタデータ]** タブで、 **Reseller** ディメンション、 **Reseller Name** 属性階層の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-133">On the **Metadata** tab in the **Calculation Tools** pane, expand the **Reseller** dimension, and then expand the **Reseller Name** attribute hierarchy.</span></span>

5.  <span data-ttu-id="6b3dd-134">**Reseller Name** レベルを Exists セット式のかっこ内にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-134">Drag the **Reseller Name** level into the parenthesis for the Exists set expression.</span></span>

     <span data-ttu-id="6b3dd-135">このセットのすべてのメンバーを返すには、Members 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-135">You will use the Members function to return all members of this set.</span></span> <span data-ttu-id="6b3dd-136">詳細については、「[Members (Set) (MDX)](/sql/mdx/members-set-mdx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-136">For more information, see [Members &#40;Set&#41; &#40;MDX&#41;](/sql/mdx/members-set-mdx).</span></span>

6.  <span data-ttu-id="6b3dd-137">セット式の部分に続けて、ピリオドを入力して、Members 関数を追加します。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-137">After the partial set expression, type a period, and then add the Members function.</span></span> <span data-ttu-id="6b3dd-138">式は以下のようになります。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-138">Your expression should look like the following:</span></span>

    ```
    Exists([Reseller].[Reseller Name].[Reseller Name].Members)
    ```

     <span data-ttu-id="6b3dd-139">これで、Exists セット式の最初のセットが定義されたので、2番目のセット (最も多くの従業員を含む再販業者ディメンションのメンバーのセット) を追加する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-139">Now that you have defined the first set for the Exists set expression, you are ready to add the second set-the set of members of the Reseller dimension that contains the largest number of employees.</span></span>

7.  <span data-ttu-id="6b3dd-140">[**計算ツール**] ペインの [**メタデータ**] タブで、[リセラー] ディメンションの [ **Number of Employees** ] を展開し、 `Members` []、[ **All リセラー**] の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-140">On the **Metadata** tab in the **Calculation Tools** pane, expand **Number of Employees** in the Reseller dimension, expand `Members`, and then expand **All Resellers**.</span></span>

     <span data-ttu-id="6b3dd-141">この属性階層のメンバーはグループ化されていません。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-141">Notice that the members of this attribute hierarchy are not grouped.</span></span>

8.  <span data-ttu-id="6b3dd-142">**Reseller** ディメンションのディメンション デザイナーを開いて、 **[属性]** ペインの **[Number of Employees]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-142">Open Dimension Designer for the **Reseller** dimension, and then click **Number of Employees** in the **Attributes** pane.</span></span>

9. <span data-ttu-id="6b3dd-143">プロパティウィンドウで、 `DiscretizationMethod` プロパティを**Automatic**に変更し、プロパティをに変更し `DiscretizationBucketCount` `5` ます。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-143">In the Properties window, change the `DiscretizationMethod` property to **Automatic**, and then change the `DiscretizationBucketCount` property to `5`.</span></span> <span data-ttu-id="6b3dd-144">詳細については、[「属性メンバーのグループ化 (分離)](multidimensional-models/attribute-properties-group-attribute-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-144">For more information, see [Group Attribute Members &#40;Discretization&#41;](multidimensional-models/attribute-properties-group-attribute-members.md).</span></span>

10. <span data-ttu-id="6b3dd-145">**で、** [ビルド] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-145">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>

11. <span data-ttu-id="6b3dd-146">配置が正常に完了したら、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーに切り替え、 **[計算]** タブのツール バーで **[再接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-146">When deployment has successfully completed, switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Reconnect** on the toolbar of the **Calculations** tab.</span></span>

12. <span data-ttu-id="6b3dd-147">[**計算ツール**] ペインの [**メタデータ**] タブで、[**リセラー** ] ディメンションの [ **Number of Employees** ] を展開し、 `Members` []、[ **All リセラー**] の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-147">On the **Metadata** tab in the **Calculation Tools** pane, expand **Number of Employees** in the **Reseller** dimension, expand `Members`, and then expand **All Resellers**.</span></span>

     <span data-ttu-id="6b3dd-148">この属性階層のメンバーには、0 から 4 までの番号が付いた 5 つのグループが含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-148">Notice that the members of this attribute hierarchy are now contained in five groups, numbered 0 through 4.</span></span> <span data-ttu-id="6b3dd-149">グループの番号は、グループ上にポインターを合わせると表示されるヒントで確認できます。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-149">To view the number of a group, pause the pointer over that group to view an InfoTip.</span></span> <span data-ttu-id="6b3dd-150">`2 -17`の範囲では、ヒントに `[Reseller].[Number of Employees].&[0]`が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-150">For the range `2 -17`, the InfoTip should contain `[Reseller].[Number of Employees].&[0]`.</span></span>

     <span data-ttu-id="6b3dd-151">この属性階層のメンバーは、DiscretizationBucketCount プロパティがに設定され、 `5` DiscretizationMethod プロパティが**Automatic**に設定されているため、グループ化されます。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-151">The members of this attribute hierarchy are grouped because the DiscretizationBucketCount property is set to `5` and the DiscretizationMethod property is set to **Automatic**.</span></span>

13. <span data-ttu-id="6b3dd-152">**[式]** ボックスで、Exists セット式内の Members 関数の後ろ、右かっこの直前にコンマを追加します。次に、 **[メタデータ]** ペインから **[83 - 100]** をドラッグしてコンマの後に置きます。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-152">In the **Expression** box, add a comma in the Exists set expression after the Members function and before the closing parenthesis, and then drag **83 - 100** from the **Metadata** pane and position it after the comma.</span></span>

     <span data-ttu-id="6b3dd-153">これで、Exists セット式は完成です。この式は、Large Resellers 名前付きセットが軸に設定された場合に、これらの指定された 2 つのセット、つまり全再販業者のセットと 83 から 100 人の従業員を持つ再販業者のセットで交差するメンバーのセットを返します。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-153">You have now completed the Exists set expression that will return the set of members that intersects with these two specified sets, the set of all resellers and the set of resellers who have 83 to 100 employees, when the Large Resellers named set is put on an axis.</span></span>

     <span data-ttu-id="6b3dd-154">次の図は、名前付きセットの**計算式**ペインを示して `[Large Resellers]` います。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-154">The following image shows the **Calculation Expressions** pane for the `[Large Resellers]` named set.</span></span>

     <span data-ttu-id="6b3dd-155">![[Large Resellers] の計算式ペイン](../../2014/tutorials/media/l6-named-set-02.gif "[Large Resellers] の計算式ペイン")</span><span class="sxs-lookup"><span data-stu-id="6b3dd-155">![Calculation Expressions pane for [Large Resellers]](../../2014/tutorials/media/l6-named-set-02.gif "Calculation Expressions pane for [Large Resellers]")</span></span>

14. <span data-ttu-id="6b3dd-156">**[計算]** タブのツール バーで **[スクリプト ビュー]** をクリックし、計算スクリプトに追加した 2 つの名前付きセットを確認します。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-156">On the toolbar of the **Calculations** tab, click **Script View**, and then review the two named sets that you have just added to the calculation script.</span></span>

15. <span data-ttu-id="6b3dd-157">計算スクリプトの最初の CREATE SET コマンドの直前に新しい行を追加して、その行に以下のテキストを独自の行として追加します。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-157">Add a new line in the calculation script immediately before the first CREATE SET command, and then add the following text to the script on its own line:</span></span>

    ```
    /* named sets */
    ```

     <span data-ttu-id="6b3dd-158">これで 2 つの名前付きセットが定義され、それらは **[スクリプト オーガナイザー]** ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-158">You have now defined two named sets, which are visible in the **Script Organizer** pane.</span></span> <span data-ttu-id="6b3dd-159">これらの名前付きセットを配置して、これらのメジャーを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブで表示する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-159">You are now ready to deploy these named sets, and then to browse these measures in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>

## <a name="browsing-the-cube-by-using-the-new-named-sets"></a><span data-ttu-id="6b3dd-160">新しい名前付きセットを使用したキューブの表示</span><span class="sxs-lookup"><span data-stu-id="6b3dd-160">Browsing the Cube by Using the New Named Sets</span></span>

1.  <span data-ttu-id="6b3dd-161">**で、** [ビルド] [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-161">On the **Build** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="6b3dd-162">配置が正常に完了したら、 **[ブラウザー]** タブをクリックして、 **[再接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-162">When deployment has successfully completed, click the **Browser** tab, and then click **Reconnect**.</span></span>

3.  <span data-ttu-id="6b3dd-163">データ ペインのグリッドをクリアします。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-163">Clear the grid in the data pane.</span></span>

4.  <span data-ttu-id="6b3dd-164">**Reseller Sales-Sales Amount** メジャーをデータ領域に追加します。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-164">Add the **Reseller Sales-Sales Amount** measure to the data area.</span></span>

5.  <span data-ttu-id="6b3dd-165">次の図のように、Product ディメンションを展開し、Category と Subcategory を行領域に追加します。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-165">Expand the Product dimension, and then add Category and Subcategory to the row area, as shown in the following image.</span></span>

     <span data-ttu-id="6b3dd-166">![Subcategory 属性のメンバー](../../2014/tutorials/media/l6-named-set-03.gif "Subcategory 属性のメンバー")</span><span class="sxs-lookup"><span data-stu-id="6b3dd-166">![Members of the Subcategory attribute](../../2014/tutorials/media/l6-named-set-03.gif "Members of the Subcategory attribute")</span></span>

6.  <span data-ttu-id="6b3dd-167">**[メタデータ]** ペインの **Product** ディメンションで、 **Core Products** をフィルター領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-167">In the **Metadata** pane, in the **Product** dimension, drag **Core Products** to the filter area.</span></span>

     <span data-ttu-id="6b3dd-168">キューブで表示されるのは **Category** 属性の **Bike** メンバーと、 **Bike** サブカテゴリのメンバーだけになります。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-168">Notice that only the **Bike** member of the **Category** attribute and members of the **Bike** subcategories remain in the cube.</span></span> <span data-ttu-id="6b3dd-169">これは、サブキューブを定義するために **Core Products** 名前付きセットが使用されているためです。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-169">This is because the **Core Products** named set is used to define a subcube.</span></span> <span data-ttu-id="6b3dd-170">次の図のように、このサブキューブは、サブキューブ内の **Product** ディメンション内の **Category** 属性のメンバーを、 **Core Product** 名前付きセットのメンバーに限定します。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-170">This subcube limits the members of the **Category** attribute in the **Product** dimension within the subcube to those members of the **Core Product** named set, as shown in the following image.</span></span>

     <span data-ttu-id="6b3dd-171">![Core Product 名前付きセットのメンバー](../../2014/tutorials/media/l6-named-set-04.gif "Core Product 名前付きセットのメンバー")</span><span class="sxs-lookup"><span data-stu-id="6b3dd-171">![Members of the Core Product named set](../../2014/tutorials/media/l6-named-set-04.gif "Members of the Core Product named set")</span></span>

7.  <span data-ttu-id="6b3dd-172">**[メタデータ]** ペインで **Reseller**を展開し、フィルター領域に **Large Resellers** を追加します。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-172">In the **Metadata** pane, expand **Reseller**, add **Large Resellers** to the filter area.</span></span>

     <span data-ttu-id="6b3dd-173">データ ペインの Reseller Sales Amount メジャーには、自転車の大規模な再販業者の売上高だけが表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-173">Notice that the Reseller Sales Amount measure in the Data pane only displays sales amounts for large resellers of bikes.</span></span> <span data-ttu-id="6b3dd-174">また、次の図のように、フィルター ペインには、この特定のサブキューブを定義するために使用される 2 つの名前付きセットが表示されています。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-174">Notice also that the Filter pane now displays the two named sets that are used to define this particular subcube, as shown in the following image.</span></span>

     <span data-ttu-id="6b3dd-175">![2 つの名前付きセットを含む [フィルター] ペイン](../../2014/tutorials/media/l6-named-set-05.gif "2 つの名前付きセットを含む [フィルター] ペイン")</span><span class="sxs-lookup"><span data-stu-id="6b3dd-175">![Filter pane containing two named sets](../../2014/tutorials/media/l6-named-set-05.gif "Filter pane containing two named sets")</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="6b3dd-176">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="6b3dd-176">Next Task in Lesson</span></span>
 [<span data-ttu-id="6b3dd-177">レッスン 7: 主要業績評価指標 (KPI) の定義</span><span class="sxs-lookup"><span data-stu-id="6b3dd-177">Lesson 7: Defining Key Performance Indicators &#40;KPIs&#41;</span></span>](lesson-7-defining-key-performance-indicators-kpis.md)

## <a name="see-also"></a><span data-ttu-id="6b3dd-178">参照</span><span class="sxs-lookup"><span data-stu-id="6b3dd-178">See Also</span></span>
 <span data-ttu-id="6b3dd-179">[計算](multidimensional-models-olap-logical-cube-objects/calculations.md)で[名前付きセットを作成する](multidimensional-models/create-named-sets.md)</span><span class="sxs-lookup"><span data-stu-id="6b3dd-179">[Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md) [Create Named Sets](multidimensional-models/create-named-sets.md)</span></span>


