---
title: 計算されるメンバーを定義する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 07f13e1c-0b20-4f9e-ad62-c438983f2785
author: minewiskan
ms.author: owend
ms.openlocfilehash: f2a054356613ebf3d4cf825c1fa4c238a5362ec3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639748"
---
# <a name="defining-calculated-members"></a><span data-ttu-id="d7494-102">計算されるメンバーの定義</span><span class="sxs-lookup"><span data-stu-id="d7494-102">Defining Calculated Members</span></span>
  <span data-ttu-id="d7494-103">計算されるメンバーとは、キューブ データ、算術演算子、数値、関数を組み合わせて定義した、ディメンション グループまたはメジャー グループのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="d7494-103">Calculated members are members of a dimension or a measure group that are defined based on a combination of cube data, arithmetic operators, numbers, and functions.</span></span> <span data-ttu-id="d7494-104">たとえば、キューブ内の 2 つの物理的なメジャーの合計を計算する、計算されるメンバーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d7494-104">For example, you can create a calculated member that calculates the sum of two physical measures in the cube.</span></span> <span data-ttu-id="d7494-105">計算されるメンバーの定義はキューブ内に保存されますが、その値はクエリ時に計算されます。</span><span class="sxs-lookup"><span data-stu-id="d7494-105">Calculated member definitions are stored in cubes, but their values are calculated at query time.</span></span>  
  
 <span data-ttu-id="d7494-106">計算されるメンバーを作成するには、キューブ デザイナーの **[計算]** タブで **[新しい計算されるメンバー]** コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d7494-106">To create a calculated member, use the **New Calculated Member** command on the **Calculations** tab of Cube Designer.</span></span> <span data-ttu-id="d7494-107">計算されるメンバーは、メジャー ディメンションなどの任意のディメンション内に作成できます。</span><span class="sxs-lookup"><span data-stu-id="d7494-107">You can create a calculated member within any dimension, including the measures dimension.</span></span> <span data-ttu-id="d7494-108">**[計算プロパティ]** ダイアログ ボックスを使用して、計算されるメンバーを表示フォルダー内に配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="d7494-108">You can also place a calculated member within a display folder in the **Calculation Properties** dialog box.</span></span> <span data-ttu-id="d7494-109">詳しくは、「 [計算](multidimensional-models-olap-logical-cube-objects/calculations.md)」、「 [多次元モデルの計算](multidimensional-models/calculations-in-multidimensional-models.md)」、および「 [計算されるメンバーの作成](multidimensional-models/create-calculated-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7494-109">For more information, see [Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md), [Calculations in Multidimensional Models](multidimensional-models/calculations-in-multidimensional-models.md), and [Create Calculated Members](multidimensional-models/create-calculated-members.md).</span></span>  
  
 <span data-ttu-id="d7494-110">このトピックの作業では、計算されるメジャーを定義し、インターネット販売、再販業者による販売、およびすべての販売について、売上総利益率と売上比率を表示できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d7494-110">In the tasks in this topic, you define calculated measures to let users view the gross profit margin percentage and sales ratios for Internet sales, reseller sales, and for all sales.</span></span>  
  
## <a name="defining-calculations-to-aggregate-physical-measures"></a><span data-ttu-id="d7494-111">物理メジャーを集計する計算の定義</span><span class="sxs-lookup"><span data-stu-id="d7494-111">Defining Calculations to Aggregate Physical Measures</span></span>  
  
1.  <span data-ttu-id="d7494-112">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーを開き、 **[計算]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-112">Open Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Calculations** tab.</span></span>  
  
     <span data-ttu-id="d7494-113">**計算式** ペインと **[スクリプト オーガナイザー]** ペインには、既定で CALCULATE コマンドが表示されています。</span><span class="sxs-lookup"><span data-stu-id="d7494-113">Notice the default CALCULATE command in the **Calculation Expressions** pane and in the **Script Organizer** pane.</span></span> <span data-ttu-id="d7494-114">このコマンドは、AggregateFunction プロパティで指定されている値に基づいて、キューブ内のメジャーを集計するように指定します。</span><span class="sxs-lookup"><span data-stu-id="d7494-114">This command specifies that the measures in the cube should be aggregated according to the value that is specified by their AggregateFunction properties.</span></span> <span data-ttu-id="d7494-115">通常、メジャー値は合計されますが、他の方法でカウントまたは集計することも可能です。</span><span class="sxs-lookup"><span data-stu-id="d7494-115">Measure values are generally summed, but may also be counted or aggregated in some other manner.</span></span>  
  
     <span data-ttu-id="d7494-116">次の図は、キューブ デザイナーの **[計算]** タブを示しています。</span><span class="sxs-lookup"><span data-stu-id="d7494-116">The following image shows the **Calculations** tab of Cube Designer.</span></span>  
  
     <span data-ttu-id="d7494-117">![キューブ デザイナーの [計算] タブ](../../2014/tutorials/media/l6-calculatedmembers-1.gif "キューブ デザイナーの [計算] タブ")</span><span class="sxs-lookup"><span data-stu-id="d7494-117">![Calculations tab of Cube Designer](../../2014/tutorials/media/l6-calculatedmembers-1.gif "Calculations tab of Cube Designer")</span></span>  
  
2.  <span data-ttu-id="d7494-118">**[計算]** タブのツール バーで、 **[新しい計算されるメンバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-118">On the toolbar of the **Calculations** tab, click **New Calculated Member**.</span></span>  
  
     <span data-ttu-id="d7494-119">**計算式** ペインに新しいフォームが表示されます。このフォームで、この新しい計算されるメンバーのプロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="d7494-119">A new form appears in the **Calculation Expressions** pane within which you define the properties of this new calculated member.</span></span> <span data-ttu-id="d7494-120">新しいメンバーは **[スクリプト オーガナイザー]** ペインにも表示されます。</span><span class="sxs-lookup"><span data-stu-id="d7494-120">The new member also appears in the **Script Organizer** pane.</span></span>  
  
     <span data-ttu-id="d7494-121">次の図は、 **[新しい計算されるメンバー]** をクリックしたとき、 **計算式**ペインに表示されるフォームを示しています。</span><span class="sxs-lookup"><span data-stu-id="d7494-121">The following image shows the form that appears in the **Calculation Expressions** pane when you click **New Calculated Member**.</span></span>  
  
     <span data-ttu-id="d7494-122">![計算式ペイン フォーム](../../2014/tutorials/media/l6-calculatedmembers-02.gif "計算式ペイン フォーム")</span><span class="sxs-lookup"><span data-stu-id="d7494-122">![Calculation Expressions pane form](../../2014/tutorials/media/l6-calculatedmembers-02.gif "Calculation Expressions pane form")</span></span>  
  
3.  <span data-ttu-id="d7494-123">[**名前**] ボックスで、計算されるメジャーの名前をに変更 `[Total Sales Amount]` します。</span><span class="sxs-lookup"><span data-stu-id="d7494-123">In the **Name** box, change the name of the calculated measure to `[Total Sales Amount]`.</span></span>  
  
     <span data-ttu-id="d7494-124">計算されるメンバーの名前に空白文字が含まれる場合は、その名前全体を角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7494-124">If the name of a calculated member contains a space, the calculated member name must be enclosed in square brackets.</span></span>  
  
     <span data-ttu-id="d7494-125">**[親階層]** ボックスを見るとわかるように、既定では、新しい計算されるメンバーは **Measures** ディメンションに作成されます。</span><span class="sxs-lookup"><span data-stu-id="d7494-125">Notice in the **Parent hierarchy** list that, by default, a new calculated member is created in the **Measures** dimension.</span></span> <span data-ttu-id="d7494-126">Measures ディメンションの計算されるメンバーは、多くの場合、計算されるメジャーと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d7494-126">A calculated member in the Measures dimension is also frequently called a calculated measure.</span></span>  
  
4.  <span data-ttu-id="d7494-127">**[計算]** タブの **[計算ツール]** ペインで **[メタデータ]** タブをクリックし、 **[Measures]** 、 **[Internet Sales]** の順に展開します。 **Internet Sales** メジャー グループのメタデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d7494-127">On the **Metadata** tab in the **Calculation Tools** pane of the **Calculations** tab, expand **Measures** and then expand **Internet Sales** to view the metadata for the **Internet Sales** measure group.</span></span>  
  
     <span data-ttu-id="d7494-128">メタデータ要素を **[計算ツール]** ペインから **[式]** ボックスにドラッグし、さらに演算子と他の要素を追加して、多次元式 (MDX) を作成します。</span><span class="sxs-lookup"><span data-stu-id="d7494-128">You can drag metadata elements from the **Calculation Tools** pane into the **Expression** box and then add operators and other elements to create Multidimensional Expressions (MDX) expressions.</span></span> <span data-ttu-id="d7494-129">**[式]** ボックスには、MDX 式を直接入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="d7494-129">Alternatively, you can type the MDX expression directly into the **Expression** box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d7494-130">**[計算ツール]** ペインにメタデータが表示されない場合、ツール バーの **[再接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-130">If you cannot view any metadata in the **Calculation Tools** pane, click **Reconnect** on the toolbar.</span></span> <span data-ttu-id="d7494-131">それでも表示されない場合は、キューブを処理するか、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のインスタンスを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7494-131">If this does not work, you may have to process the cube or start the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
5.  <span data-ttu-id="d7494-132">**[計算ツール]** ペインの **[メタデータ]** タブで **[Internet Sales-Sales Amount]** をクリックし、 **計算式** ペインの **[式]** ボックスまでドラッグします。</span><span class="sxs-lookup"><span data-stu-id="d7494-132">Drag **Internet Sales-Sales Amount** from the **Metadata** tab in the **Calculation Tools** pane into the **Expression** box in the **Calculation Expressions** pane.</span></span>  
  
6.  <span data-ttu-id="d7494-133">**[式]** ボックスで、`+`[Measures].[Internet Sales-Sales Amount] **の後ろにプラス符号 (**) を入力します。</span><span class="sxs-lookup"><span data-stu-id="d7494-133">In the **Expression** box, type a plus sign (`+`) after **[Measures].[Internet Sales-Sales Amount]**.</span></span>  
  
7.  <span data-ttu-id="d7494-134">**[計算ツール]** ペインの **[メタデータ]** タブで **[Reseller Sales]** を展開します。次に、 **[Reseller Sales-Sales Amount]** を、 **計算式** ペインの **[式]** ボックスにあるプラス符号 (+) の後ろにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="d7494-134">On the **Metadata** tab in the **Calculation Tools** pane, expand **Reseller Sales**, and then drag **Reseller Sales-Sales Amount** into the **Expression** box in the **Calculation Expressions** pane after the plus sign (+).</span></span>  
  
8.  <span data-ttu-id="d7494-135">[**書式設定文字列**] ボックスの一覧で、[通貨] を選択し**ます。**</span><span class="sxs-lookup"><span data-stu-id="d7494-135">In the **Format string** list, select **"Currency".**</span></span>  
  
9. <span data-ttu-id="d7494-136">**[空以外の動作]** ボックスの一覧で、 **Internet Sales-Sales Amount** と **Reseller Sales-Sales Amount**のチェック ボックスをオンにして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-136">In the **Non-empty behavior** list, select the check boxes for **Internet Sales-Sales Amount** and **Reseller Sales-Sales Amount**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="d7494-137">**[空以外の動作]** ボックスで指定したメジャーは、MDX の NON EMPTY クエリを解決するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d7494-137">The measures you specify in the **Non-empty behavior** list are used to resolve NON EMPTY queries in MDX.</span></span> <span data-ttu-id="d7494-138">**[空以外の動作]** ボックスで 1 つ以上のメジャーを指定すると、指定したメジャーがすべて空である場合、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は計算されるメンバーを空として処理します。</span><span class="sxs-lookup"><span data-stu-id="d7494-138">When you specify one or more measures in the **Non-empty behavior** list, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] treats the calculated member as empty if all the specified measures are empty.</span></span> <span data-ttu-id="d7494-139">**[空以外の動作]** プロパティを空白にした場合は、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は計算されるメンバー自体を評価し、空メンバーであるかどうかを判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7494-139">If the **Non-empty behavior** property is blank, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] must evaluate the calculated member itself to determine whether the member is empty.</span></span>  
  
     <span data-ttu-id="d7494-140">次の図は、上記の手順で指定した設定が入力された **計算式** ペインを示しています。</span><span class="sxs-lookup"><span data-stu-id="d7494-140">The following image shows the **Calculation Expressions** pane populated with the settings that you specified in the previous steps.</span></span>  
  
     <span data-ttu-id="d7494-141">![値が設定された計算式ペイン](../../2014/tutorials/media/l6-calculatedmembers-03.gif "値が設定された計算式ペイン")</span><span class="sxs-lookup"><span data-stu-id="d7494-141">![Populated Calculation Expressions pane](../../2014/tutorials/media/l6-calculatedmembers-03.gif "Populated Calculation Expressions pane")</span></span>  
  
10. <span data-ttu-id="d7494-142">**[計算]** タブのツール バーにある **[スクリプト ビュー]** をクリックし、 **計算式** ペインで計算スクリプトを確認します。</span><span class="sxs-lookup"><span data-stu-id="d7494-142">On the toolbar of the **Calculations** tab, click **Script View**, and then review the calculation script in the **Calculation Expressions** pane.</span></span>  
  
     <span data-ttu-id="d7494-143">新しい計算が最初の CALCULATE 式に追加されているはずです。個々の計算はセミコロンで区切られています。</span><span class="sxs-lookup"><span data-stu-id="d7494-143">Notice that the new calculation is added to the initial CALCULATE expression; each individual calculation is separated by a semicolon.</span></span> <span data-ttu-id="d7494-144">計算スクリプトの冒頭には、コメントが挿入されています。</span><span class="sxs-lookup"><span data-stu-id="d7494-144">Notice also that a comment appears at the beginning of the calculation script.</span></span> <span data-ttu-id="d7494-145">計算スクリプト内で計算のグループごとにコメントを追加すると、開発者が複雑な計算スクリプトを理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d7494-145">Adding comments within the calculation script for groups of calculations is a good practice, to help you and other developers understand complex calculation scripts.</span></span>  
  
11. <span data-ttu-id="d7494-146">計算スクリプトで、 **Calculate;** コマンドの後、新しく追加された計算スクリプトの前に新しい行を追加し、その行に以下のテキストを独自の行として追加します。</span><span class="sxs-lookup"><span data-stu-id="d7494-146">Add a new line in the calculation script after the **Calculate;** command and before the newly added calculation script, and then add the following text to the script on its own line:</span></span>  
  
    ```  
    /* Calculations to aggregate Internet Sales and Reseller Sales measures */  
    ```  
  
     <span data-ttu-id="d7494-147">次の図は、チュートリアルのこの時点で **計算式** ペインに表示される計算スクリプトを示しています。</span><span class="sxs-lookup"><span data-stu-id="d7494-147">The following image shows the calculation scripts as they should appear in the **Calculation Expressions** pane at this point in the tutorial.</span></span>  
  
     <span data-ttu-id="d7494-148">![計算式ペインのスクリプト](../../2014/tutorials/media/l6-calculatedmembers-04.gif "計算式ペインのスクリプト")</span><span class="sxs-lookup"><span data-stu-id="d7494-148">![Scripts in Calculation Expressions pane](../../2014/tutorials/media/l6-calculatedmembers-04.gif "Scripts in Calculation Expressions pane")</span></span>  
  
12. <span data-ttu-id="d7494-149">[**計算**] タブのツールバーで、[**フォームビュー**] をクリックし、[ `[Total Sales Amount]` **スクリプトオーガナイザー** ] ペインでが選択されていることを確認して、[**新しい計算**されるメンバー] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-149">On the toolbar of the **Calculations** tab, click **Form View**, verify that `[Total Sales Amount]` is selected in the **Script Organizer** pane, and then click **New Calculated Member**.</span></span>  
  
13. <span data-ttu-id="d7494-150">この新しい計算されるメンバーの名前をに変更し、 `[Total Product Cost]` [**式**] ボックスに次の式を作成します。</span><span class="sxs-lookup"><span data-stu-id="d7494-150">Change the name of this new calculated member to `[Total Product Cost]`, and then create the following expression in the **Expression** box:</span></span>  
  
    ```  
    [Measures].[Internet Sales-Total Product Cost] + [Measures].[Reseller Sales-Total Product Cost]  
    ```  
  
14. <span data-ttu-id="d7494-151">**[書式設定文字列]** ボックスの一覧の **["Currency"]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d7494-151">In the **Format string** list, select **"Currency"**.</span></span>  
  
15. <span data-ttu-id="d7494-152">**[空以外の動作]** ボックスの一覧で、 **Internet Sales-Total Product Cost** と **Reseller Sales-Total Product Cost**のチェック ボックスをオンにして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-152">In the **Non-empty behavior** list, select the check boxes for **Internet Sales-Total Product Cost** and **Reseller Sales-Total Product Cost**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="d7494-153">これで 2 つの計算されるメンバーが定義され、どちらも **[スクリプト オーガナイザー]** ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d7494-153">You have now defined two calculated members, both of which are visible in the **Script Organizer** pane.</span></span> <span data-ttu-id="d7494-154">これらの計算されるメンバーは、計算スクリプト内で後に定義する他の計算で使用することができます。</span><span class="sxs-lookup"><span data-stu-id="d7494-154">These calculated members can be used by other calculations that you define later in the calculation script.</span></span> <span data-ttu-id="d7494-155">**[スクリプト オーガナイザー]** ペインでいずれかの計算されるメンバーを選択すると、その計算されるメンバーの定義を表示できます。計算されるメンバーの定義は、フォーム ビューの **計算式** ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d7494-155">You can view the definition of any calculated member by selecting the calculated member in the **Script Organizer** pane; the definition of the calculated member will appear in the **Calculation Expressions** pane in the Form view.</span></span> <span data-ttu-id="d7494-156">新しく定義した計算されるメンバーは、配置されるまでは **[計算ツール]** ペインに表示されません。</span><span class="sxs-lookup"><span data-stu-id="d7494-156">Newly defined calculated members will not appear in the **Calculation Tools** pane until these objects have been deployed.</span></span> <span data-ttu-id="d7494-157">計算は処理を必要としません。</span><span class="sxs-lookup"><span data-stu-id="d7494-157">Calculations do not require processing.</span></span>  
  
## <a name="defining-gross-profit-margin-calculations"></a><span data-ttu-id="d7494-158">売上総利益率の計算の定義</span><span class="sxs-lookup"><span data-stu-id="d7494-158">Defining Gross Profit Margin Calculations</span></span>  
  
1.  <span data-ttu-id="d7494-159">[ `[Total Product Cost]` **スクリプトオーガナイザー** ] ペインでが選択されていることを確認し、[**計算**] タブのツールバーの [**新しい計算**されるメンバー] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-159">Verify that `[Total Product Cost]` is selected in the **Script Organizer** pane, and then click **New Calculated Member** on the toolbar of the **Calculations** tab.</span></span>  
  
2.  <span data-ttu-id="d7494-160">[**名前**] ボックスで、この新しい計算されるメジャーの名前をに変更し `[Internet GPM]` ます。</span><span class="sxs-lookup"><span data-stu-id="d7494-160">In the **Name** box, change the name of this new calculated measure to `[Internet GPM]`.</span></span>  
  
3.  <span data-ttu-id="d7494-161">**[式]** ボックスで、以下の MDX 式を作成します。</span><span class="sxs-lookup"><span data-stu-id="d7494-161">In the **Expression** box, create the following MDX expression:</span></span>  
  
    ```  
    ([Measures].[Internet Sales-Sales Amount] -   
    [Measures].[Internet Sales-Total Product Cost]) /  
    [Measures].[Internet Sales-Sales Amount]  
    ```  
  
4.  <span data-ttu-id="d7494-162">**[書式設定文字列]** ボックスの一覧で **["Percent"]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d7494-162">In the **Format string** list, select **"Percent"**.</span></span>  
  
5.  <span data-ttu-id="d7494-163">**[空以外の動作]** ボックスの一覧で、 **Internet Sales-Sales Amount**のチェック ボックスをオンにして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-163">In the **Non-empty behavior** list, select the check box for **Internet Sales-Sales Amount**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="d7494-164">**[計算]** タブのツール バーで、 **[新しい計算されるメンバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-164">On the toolbar of the **Calculations** tab, click **New Calculated Member**.</span></span>  
  
7.  <span data-ttu-id="d7494-165">[**名前**] ボックスで、この新しい計算されるメジャーの名前をに変更し `[Reseller GPM]` ます。</span><span class="sxs-lookup"><span data-stu-id="d7494-165">In the **Name** box, change the name of this new calculated measure to `[Reseller GPM]`.</span></span>  
  
8.  <span data-ttu-id="d7494-166">**[式]** ボックスで、以下の MDX 式を作成します。</span><span class="sxs-lookup"><span data-stu-id="d7494-166">In the **Expression** box, create the following MDX expression:</span></span>  
  
    ```  
    ([Measures].[Reseller Sales-Sales Amount] -   
    [Measures].[Reseller Sales-Total Product Cost]) /  
    [Measures].[Reseller Sales-Sales Amount]  
    ```  
  
9. <span data-ttu-id="d7494-167">**[書式設定文字列]** ボックスの一覧で **["Percent"]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d7494-167">In the **Format string** list, select **"Percent"**.</span></span>  
  
10. <span data-ttu-id="d7494-168">**[空以外の動作]** ボックスの一覧で、 **Reseller Sales-Sales Amount**のチェック ボックスをオンにして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-168">In the **Non-empty behavior** list, select the check box for **Reseller Sales-Sales Amount**, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="d7494-169">**[計算]** タブのツール バーで、 **[新しい計算されるメンバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-169">On the toolbar of the **Calculations** tab, click **New Calculated Member**.</span></span>  
  
12. <span data-ttu-id="d7494-170">[**名前**] ボックスで、この計算されるメジャーの名前をに変更し `[Total GPM]` ます。</span><span class="sxs-lookup"><span data-stu-id="d7494-170">In the **Name** box, change the name of this calculated measure to `[Total GPM]`.</span></span>  
  
13. <span data-ttu-id="d7494-171">**[式]** ボックスで、以下の MDX 式を作成します。</span><span class="sxs-lookup"><span data-stu-id="d7494-171">In the **Expression** box, create the following MDX expression:</span></span>  
  
    ```  
    ([Measures].[Total Sales Amount] -   
    [Measures].[Total Product Cost]) /  
    [Measures].[Total Sales Amount]  
    ```  
  
     <span data-ttu-id="d7494-172">この計算されるメンバーは、他の計算されるメンバーを参照しています。</span><span class="sxs-lookup"><span data-stu-id="d7494-172">Notice that this calculated member is referencing other calculated members.</span></span> <span data-ttu-id="d7494-173">この計算されるメンバーは、参照している計算されるメンバーの後に計算されるため、有効な計算されるメンバーになります。</span><span class="sxs-lookup"><span data-stu-id="d7494-173">Because this calculated member will be calculated after the calculated members that it references, this is a valid calculated member.</span></span>  
  
14. <span data-ttu-id="d7494-174">**[書式設定文字列]** ボックスの一覧で **["Percent"]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d7494-174">In the **Format string** list, select **"Percent"**.</span></span>  
  
15. <span data-ttu-id="d7494-175">**[空以外の動作]** ボックスの一覧で、 **Internet Sales-Sales Amount** と **Reseller Sales-Sales Amount**のチェック ボックスをオンにして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-175">In the **Non-empty behavior** list, select the check boxes for **Internet Sales-Sales Amount** and **Reseller Sales-Sales Amount**, and then click **OK**.</span></span>  
  
16. <span data-ttu-id="d7494-176">**[計算]** タブのツール バーで **[スクリプト ビュー]** をクリックし、計算スクリプトに追加した 3 つの計算を確認します。</span><span class="sxs-lookup"><span data-stu-id="d7494-176">On the toolbar of the **Calculations** tab, click **Script View** and review the three calculations you just added to the calculation script.</span></span>  
  
17. <span data-ttu-id="d7494-177">計算スクリプト内の計算の直前に新しい行を追加 `[Internet GPM]` し、次のテキストを独自の行にスクリプトに追加します。</span><span class="sxs-lookup"><span data-stu-id="d7494-177">Add a new line in the calculation script immediately before the `[Internet GPM]` calculation, and then add the following text to the script on its own line:</span></span>  
  
    ```  
    /* Calculations to calculate gross profit margin */  
    ```  
  
     <span data-ttu-id="d7494-178">次の図は、新しい 3 つの計算が表示されている **計算式** ペインを示しています。</span><span class="sxs-lookup"><span data-stu-id="d7494-178">The following image shows the **Expressions** pane with the three new calculations.</span></span>  
  
     <span data-ttu-id="d7494-179">![計算式ペインでの新しい計算](../../2014/tutorials/media/l6-calculatedmembers-05.gif "計算式ペインでの新しい計算")</span><span class="sxs-lookup"><span data-stu-id="d7494-179">![New calculations in Calculation Expressions pane](../../2014/tutorials/media/l6-calculatedmembers-05.gif "New calculations in Calculation Expressions pane")</span></span>  
  
## <a name="defining-the-percent-of-total-calculations"></a><span data-ttu-id="d7494-180">全体に対する比率の計算の定義</span><span class="sxs-lookup"><span data-stu-id="d7494-180">Defining the Percent of Total Calculations</span></span>  
  
1.  <span data-ttu-id="d7494-181">**[計算]** タブのツール バーで、 **[フォーム ビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-181">On the toolbar of the **Calculations** tab, click **Form View**.</span></span>  
  
2.  <span data-ttu-id="d7494-182">[**スクリプトオーガナイザー** ] ペインで、[] を選択し、[ `[Total GPM]` **計算**] タブのツールバーの [**新しい計算されるメンバー** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-182">In the **Script Organizer** pane, select `[Total GPM]`, and then click **New Calculated Member** on the toolbar of the **Calculations** tab.</span></span>  
  
     <span data-ttu-id="d7494-183">**[スクリプト オーガナイザー]** ペインで最後の計算されるメンバーをクリックしてから **[新しい計算されるメンバー]** をクリックすると、新しい計算されるメンバーがスクリプトの末尾に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="d7494-183">Clicking the final calculated member in the **Script Organizer** pane before you click **New Calculated Member** guarantees that the new calculated member will be entered at the end of the script.</span></span> <span data-ttu-id="d7494-184">スクリプトは、 **[スクリプト オーガナイザー]** ペインに表示される順序で実行されます。</span><span class="sxs-lookup"><span data-stu-id="d7494-184">Scripts execute in the order that they appear in the **Script Organizer** pane.</span></span>  
  
3.  <span data-ttu-id="d7494-185">この新しい計算されるメンバーの名前をに変更 `[Internet Sales Ratio to All Products]` します。</span><span class="sxs-lookup"><span data-stu-id="d7494-185">Change the name of this new calculated member to `[Internet Sales Ratio to All Products]`.</span></span>  
  
4.  <span data-ttu-id="d7494-186">**[式]** ボックスに以下の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="d7494-186">Type the following expression in the **Expression** box:</span></span>  
  
    ```  
    Case  
        When IsEmpty( [Measures].[Internet Sales-Sales Amount] )   
        Then 0  
        Else ( [Product].[Product Categories].CurrentMember,  
               [Measures].[Internet Sales-Sales Amount]) /  
             ( [Product].[Product Categories].[(All)].[All],   
               [Measures].[Internet Sales-Sales Amount] )  
        End  
    ```  
  
     <span data-ttu-id="d7494-187">この MDX 式は、インターネット販売の合計売上に占める各製品の割合を計算します。</span><span class="sxs-lookup"><span data-stu-id="d7494-187">This MDX expression calculates the contribution to total Internet sales of each product.</span></span> <span data-ttu-id="d7494-188">Case ステートメントを ISEMPTY 関数と共に使用すると、製品の売上がない場合でも、ゼロによる除算のエラーが発生しません。</span><span class="sxs-lookup"><span data-stu-id="d7494-188">The Case statement together with the IS EMPTY function ensures that a divide by zero error does not occur when a product has no sales.</span></span>  
  
5.  <span data-ttu-id="d7494-189">**[書式設定文字列]** ボックスの一覧で **["Percent"]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d7494-189">In the **Format string** list, select **"Percent"**.</span></span>  
  
6.  <span data-ttu-id="d7494-190">**[空以外の動作]** ボックスの一覧で、 **Internet Sales-Sales Amount**のチェック ボックスをオンにして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-190">In the **Non-empty behavior** list, select the check box for **Internet Sales-Sales Amount**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="d7494-191">**[計算]** タブのツール バーで、 **[新しい計算されるメンバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-191">On the toolbar of the **Calculations** tab, click **New Calculated Member**.</span></span>  
  
8.  <span data-ttu-id="d7494-192">この計算されるメンバーの名前をに変更 `[Reseller Sales Ratio to All Products]` します。</span><span class="sxs-lookup"><span data-stu-id="d7494-192">Change the name of this calculated member to `[Reseller Sales Ratio to All Products]`.</span></span>  
  
9. <span data-ttu-id="d7494-193">**[式]** ボックスに以下の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="d7494-193">Type the following expression in the **Expression** box:</span></span>  
  
    ```  
    Case  
        When IsEmpty( [Measures].[Reseller Sales-Sales Amount] )   
        Then 0  
        Else ( [Product].[Product Categories].CurrentMember,  
               [Measures].[Reseller Sales-Sales Amount]) /  
             ( [Product].[Product Categories].[(All)].[All],   
               [Measures].[Reseller Sales-Sales Amount] )  
        End  
    ```  
  
10. <span data-ttu-id="d7494-194">**[書式設定文字列]** ボックスの一覧で **["Percent"]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d7494-194">In the **Format string** list, select **"Percent"**.</span></span>  
  
11. <span data-ttu-id="d7494-195">**[空以外の動作]** ボックスの一覧で、 **Reseller Sales-Sales Amount**のチェック ボックスをオンにして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-195">In the **Non-empty behavior** list, select the check box for **Reseller Sales-Sales Amount**, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="d7494-196">**[計算]** タブのツール バーで、 **[新しい計算されるメンバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-196">On the toolbar of the **Calculations** tab, click **New Calculated Member**.</span></span>  
  
13. <span data-ttu-id="d7494-197">この計算されるメンバーの名前をに変更 `[Total Sales Ratio to All Products]` します。</span><span class="sxs-lookup"><span data-stu-id="d7494-197">Change the name of this calculated member to `[Total Sales Ratio to All Products]`.</span></span>  
  
14. <span data-ttu-id="d7494-198">**[式]** ボックスに以下の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="d7494-198">Type the following expression in the **Expression** box:</span></span>  
  
    ```  
    Case  
        When IsEmpty( [Measures].[Total Sales Amount] )   
        Then 0  
        Else ( [Product].[Product Categories].CurrentMember,  
               [Measures].[Total Sales Amount]) /  
             ( [Product].[Product Categories].[(All)].[All],   
               [Measures].[Total Sales Amount] )  
        End  
    ```  
  
15. <span data-ttu-id="d7494-199">**[書式設定文字列]** ボックスの一覧で **["Percent"]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d7494-199">In the **Format string** list, select **"Percent"**.</span></span>  
  
16. <span data-ttu-id="d7494-200">**[空以外の動作]** ボックスの一覧で、 **Internet Sales-Sales Amount** と **Reseller Sales-Sales Amount**のチェック ボックスをオンにして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-200">In the **Non-empty behavior** list, select the check boxes for **Internet Sales-Sales Amount** and **Reseller Sales-Sales Amount**, and then click **OK**.</span></span>  
  
17. <span data-ttu-id="d7494-201">**[計算]** タブのツール バーで **[スクリプト ビュー]** をクリックし、計算スクリプトに追加した 3 つの計算を確認します。</span><span class="sxs-lookup"><span data-stu-id="d7494-201">On the toolbar of the **Calculations** tab, click **Script View**, and then review the three calculations that you just added to the calculation script.</span></span>  
  
18. <span data-ttu-id="d7494-202">計算スクリプト内の計算の直前に新しい行を追加 `[Internet Sales Ratio to All Products]` し、次のテキストを独自の行にスクリプトに追加します。</span><span class="sxs-lookup"><span data-stu-id="d7494-202">Add a new line in the calculation script immediately before the `[Internet Sales Ratio to All Products]` calculation, and then add the following text to the script on its own line:</span></span>  
  
    ```  
    /* Calculations to calculate percentage of product to total product sales */  
    ```  
  
     <span data-ttu-id="d7494-203">これで、合計 8 つの計算されるメンバーを定義しました。これらはフォーム ビューの **[スクリプト オーガナイザー]** ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d7494-203">You have now defined a total of eight calculated members, which are visible in the **Script Organizer** pane when you are in Form view.</span></span>  
  
## <a name="browsing-the-new-calculated-members"></a><span data-ttu-id="d7494-204">新しい計算されるメンバーの表示</span><span class="sxs-lookup"><span data-stu-id="d7494-204">Browsing the New Calculated Members</span></span>  
  
1.  <span data-ttu-id="d7494-205">**で、** [ビルド] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-205">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="d7494-206">配置が正常に完了したら、 **[ブラウザー]** タブに切り替えて、 **[再接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-206">When deployment has successfully completed, switch to the **Browser** tab, click **Reconnect**.</span></span>  
  
3.  <span data-ttu-id="d7494-207">Excel アイコンをクリックし、 **[有効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7494-207">Click the Excel icon, and then click **Enable**.</span></span>  
  
4.  <span data-ttu-id="d7494-208">**[ピボットテーブルのフィールドの一覧]** ペインで **[Values]** を展開して、メジャー ディメンションの新しい計算されるメンバーを表示します。</span><span class="sxs-lookup"><span data-stu-id="d7494-208">In the **PivotTable Field List** pane, expand **Values** folder to view the new calculated members in the Measures dimension.</span></span>  
  
5.  <span data-ttu-id="d7494-209">**Total Sales Amount** を値領域にドラッグして、結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="d7494-209">Drag the **Total Sales Amount** to the Values area, and then review the results.</span></span>  
  
     <span data-ttu-id="d7494-210">**Internet Sales** および **Reseller Sales** メジャー グループから **Internet Sales-Sales Amount** および **Reseller Sales-Sales Amount** メジャーを値領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="d7494-210">Drag **Internet Sales-Sales Amount** and **Reseller Sales-Sales Amount** measures from the **Internet Sales** and **Reseller Sales** measure groups to the Values area.</span></span>  
  
     <span data-ttu-id="d7494-211">**Total Sales Amount** メジャーは、 **Internet Sales-Sales Amount** メジャーと **Reseller Sales-Sales Amount** メジャーの合計になっています。</span><span class="sxs-lookup"><span data-stu-id="d7494-211">Notice that the **Total Sales Amount** measure is the sum of the **Internet Sales-Sales Amount** measure and the **Reseller Sales-Sales Amount** measure.</span></span>  
  
6.  <span data-ttu-id="d7494-212">**Product Categories** ユーザー定義階層を **[レポート フィルター]** 領域のフィルター領域に追加し、 **Mountain Bikes**でデータをフィルターします。</span><span class="sxs-lookup"><span data-stu-id="d7494-212">Add the **Product Categories** user-defined hierarchy to the filter area of the **Report Filter** area, and then filter the data by **Mountain Bikes**.</span></span>  
  
     <span data-ttu-id="d7494-213">製品売上の計算対象が **Mountain Bikes** カテゴリになります。つまり、 **Mountain Bikes** の **Internet Sales-Sales Amount** メジャーと **Reseller Sales-Sales Amount** メジャーに基づいて **Total Sales Amount**が計算されます。</span><span class="sxs-lookup"><span data-stu-id="d7494-213">Notice that the **Total Sales Amount** measure is calculated for the **Mountain Bikes** category of product sales based on the **Internet Sales-Sales Amount** and the **Reseller Sales-Sales Amount** measures for **Mountain Bikes**.</span></span>  
  
7.  <span data-ttu-id="d7494-214">**Date.Calendar Date** ユーザー定義階層を行ラベル領域に追加して、結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="d7494-214">Add the **Date.Calendar Date** user-defined hierarchy to the Row labels area, and then review the results.</span></span>  
  
     <span data-ttu-id="d7494-215">今度は、 **Mountain Bikes** の **Internet Sales-Sales Amount** メジャーと **Reseller Sales-Sales Amount** メジャーに基づき、 **Mountain Bikes** カテゴリを対象とした製品売上が年度ごとに計算され、 **Total Sales Amount**として表示されます。</span><span class="sxs-lookup"><span data-stu-id="d7494-215">Notice that the **Total Sales Amount** measure for each calendar year is calculated for the **Mountain Bikes** category of product sales based on the **Internet Sales-Sales Amount** and the **Reseller Sales-Sales Amount** measures for **Mountain Bikes**.</span></span>  
  
8.  <span data-ttu-id="d7494-216">**Total GPM**、 **Internet GPM**、および **Reseller GPM** メジャーを値領域に追加して、結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="d7494-216">Add the **Total GPM**, **Internet GPM**, and **Reseller GPM** measures to the Values area, and then review the results.</span></span>  
  
     <span data-ttu-id="d7494-217">次の図のように、再販業者による売上の売上総利益率は、インターネットでの販売と比べて著しく低くなっています。</span><span class="sxs-lookup"><span data-stu-id="d7494-217">Notice that the gross profit margin for reseller sales is significantly lower than for sales over the Internet, as shown in the following image.</span></span>  
  
     <span data-ttu-id="d7494-218">![再販業者の販売を示す [データ] ペイン](../../2014/tutorials/media/l6-calculatedmembers-7b.gif "再販業者の販売を示す [データ] ペイン")</span><span class="sxs-lookup"><span data-stu-id="d7494-218">![Data pane showing reseller sales](../../2014/tutorials/media/l6-calculatedmembers-7b.gif "Data pane showing reseller sales")</span></span>  
  
9. <span data-ttu-id="d7494-219">**Total Sales Ratio to All Products**、 **Internet Sales Ratio to All Products**、および **Reseller Sales Ratio to All Products** メジャーを値領域に追加します。</span><span class="sxs-lookup"><span data-stu-id="d7494-219">Add the **Total Sales Ratio to All Products**, **Internet Sales Ratio to All Products**, and **Reseller Sales Ratio to All Products** measures to the Values area.</span></span>  
  
     <span data-ttu-id="d7494-220">全製品の合計売上に占めるマウンテン バイクの売上の比率は、インターネット販売では毎年増加しているのに対し、再販業者販売では減少しています。</span><span class="sxs-lookup"><span data-stu-id="d7494-220">Notice that the ratio of the sales of mountain bikes to all products has increased over time for Internet sales, but is decreasing over time for reseller sales.</span></span> <span data-ttu-id="d7494-221">全製品の合計売上に占めるマウンテン バイクの売上の比率は、インターネット販売の場合よりも、再販業者販売の場合の方が低いことにも注目してください。</span><span class="sxs-lookup"><span data-stu-id="d7494-221">Notice also that the ratio of the sale of mountain bikes to all products is lower from sales through resellers than it is for sales over the Internet.</span></span>  
  
10. <span data-ttu-id="d7494-222">フィルターを **Mountain Bikes** から **Bikes**に変更して、結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="d7494-222">Change the filter from **Mountain Bikes** to **Bikes**, and review the results.</span></span>  
  
     <span data-ttu-id="d7494-223">再販業者によるすべての自転車の販売に関する売上総利益率は負の値になっています。これはツーリング バイクおよびロード バイクの販売が赤字であるためです。</span><span class="sxs-lookup"><span data-stu-id="d7494-223">Notice that the gross profit margin for all bikes sold through resellers is negative, because touring bikes and road bikes are being sold at a loss.</span></span>  
  
11. <span data-ttu-id="d7494-224">フィルターを **Accessories**に変更して、結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="d7494-224">Change the filter to **Accessories**, and then review the results.</span></span>  
  
     <span data-ttu-id="d7494-225">アクセサリの売上は毎年増加しているものの、合計売上に占める割合が非常に小さいことがわかります。</span><span class="sxs-lookup"><span data-stu-id="d7494-225">Notice that the sale of accessories is increasing over time, but that these sales make up only a small fraction of total sales.</span></span> <span data-ttu-id="d7494-226">また、アクセサリの売上における総利益率は、自転車よりも高くなっています。</span><span class="sxs-lookup"><span data-stu-id="d7494-226">Notice also that the gross profit margin for sales of accessories is higher than for bikes.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="d7494-227">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="d7494-227">Next Task in Lesson</span></span>  
 [<span data-ttu-id="d7494-228">名前付きセットの定義</span><span class="sxs-lookup"><span data-stu-id="d7494-228">Defining Named Sets</span></span>](lesson-6-2-defining-named-sets.md)  
  
## <a name="see-also"></a><span data-ttu-id="d7494-229">参照</span><span class="sxs-lookup"><span data-stu-id="d7494-229">See Also</span></span>  
 <span data-ttu-id="d7494-230">[Custom](multidimensional-models-olap-logical-cube-objects/calculations.md) </span><span class="sxs-lookup"><span data-stu-id="d7494-230">[Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md) </span></span>  
 <span data-ttu-id="d7494-231">[多次元モデルの計算](multidimensional-models/calculations-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="d7494-231">[Calculations in Multidimensional Models](multidimensional-models/calculations-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="d7494-232">計算されるメンバーの作成</span><span class="sxs-lookup"><span data-stu-id="d7494-232">Create Calculated Members</span></span>](multidimensional-models/create-calculated-members.md)  
  
  
