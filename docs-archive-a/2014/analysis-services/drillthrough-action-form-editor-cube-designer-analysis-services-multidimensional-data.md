---
title: ドリルスルーアクションフォームエディター (キューブデザイナーの [アクション] タブ) (Analysis Services 多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionexpression.drillthroughaction.f1
ms.assetid: 225fd818-b5ea-494f-b67b-66e09798274a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 546448bd05f3af45b7093acb2dbb9d1e1a8f1bd5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644208"
---
# <a name="drillthrough-action-form-editor-actions-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="90be0-102">ドリルスルー アクション フォーム エディター (キューブ デザイナーの [アクション] タブ) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="90be0-102">Drillthrough Action Form Editor (Actions Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="90be0-103">キューブ デザイナーの **[アクション]** タブの **[ドリルスルー アクション フォーム エディター]** ペインを使用すると、 **[アクション オーガナイザー]** ペインで選択したドリルスルー アクションを変更できます。</span><span class="sxs-lookup"><span data-stu-id="90be0-103">Use the **Drillthrough Action Form Editor** pane on the **Actions** tab in Cube Designer to modify the drillthrough action selected in the **Action Organizer** pane.</span></span> <span data-ttu-id="90be0-104">アクションの種類の詳細については、「[アクション (Analysis Services - 多次元データ)](multidimensional-models/actions-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90be0-104">For more information about drillthrough actions, see [Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="90be0-105">ドリルスルー アクションでは、基になるデータ ストアへのドリル ダウンは行われなくなりました。</span><span class="sxs-lookup"><span data-stu-id="90be0-105">Drillthrough actions no longer drill down to the underlying data store.</span></span> <span data-ttu-id="90be0-106">ドリルスルー アクションでアクセスする情報は、ディメンションまたは階層メンバーを使用してキューブ内でモデル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90be0-106">The information that drillthrough actions access must be modeled within the cube by using dimension or hierarchy members.</span></span>  
  
## <a name="options"></a><span data-ttu-id="90be0-107">Options</span><span class="sxs-lookup"><span data-stu-id="90be0-107">Options</span></span>  
 <span data-ttu-id="90be0-108">**name**</span><span class="sxs-lookup"><span data-stu-id="90be0-108">**name**</span></span>  
 <span data-ttu-id="90be0-109">アクションの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="90be0-109">Type the name of the action.</span></span>  
  
 <span data-ttu-id="90be0-110">**[アクションの対象]**</span><span class="sxs-lookup"><span data-stu-id="90be0-110">**Action Target**</span></span>  
 <span data-ttu-id="90be0-111">展開すると、 **[メジャー グループのメンバー]** オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="90be0-111">Expand to view the **Measure group members** option.</span></span>  
  
 <span data-ttu-id="90be0-112">**[メジャー グループのメンバー]**</span><span class="sxs-lookup"><span data-stu-id="90be0-112">**Measure group members**</span></span>  
 <span data-ttu-id="90be0-113">ドリルスルー アクションを関連付けるメジャー グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="90be0-113">Select the measure group to which the drillthrough action is to be associated.</span></span>  
  
 <span data-ttu-id="90be0-114">**[条件 (省略可能)]**</span><span class="sxs-lookup"><span data-stu-id="90be0-114">**Condition (Optional)**</span></span>  
 <span data-ttu-id="90be0-115">オプションの条件を記述する多次元式 (MDX) を入力します。この式は、アクションが使用可能な場合にさらに制限を設定する **[メジャー グループのメンバー]** のメンバーと一緒に使用されます。</span><span class="sxs-lookup"><span data-stu-id="90be0-115">Enter the Multidimensional Expressions (MDX) expression that describes an optional condition, used in conjunction with **Measure group members**, which further restricts when the action is available.</span></span> <span data-ttu-id="90be0-116">この式は、ブール値を返す必要があります (true は、アクションが使用可能なことを示します)。</span><span class="sxs-lookup"><span data-stu-id="90be0-116">The expression must return a Boolean value that, if true, indicates the action is available.</span></span>  
  
 <span data-ttu-id="90be0-117">選択した要素を **[計算ツール]** ペインからこのオプションへドラッグして、選択した要素に対して MDX 構文を含めます。</span><span class="sxs-lookup"><span data-stu-id="90be0-117">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="90be0-118">**[ドリルスルー列]**</span><span class="sxs-lookup"><span data-stu-id="90be0-118">**Drillthrough Columns**</span></span>  
 <span data-ttu-id="90be0-119">展開すると、ユーザーがこのアクションを実行したときに返される属性を示すグリッドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="90be0-119">Expand to display a grid in which to indicate the attributes that are returned when the user runs this action.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="90be0-120">複数のディメンションを選択できますが、1 回のドリルスルー アクションで複数回使用できるディメンションはありません。</span><span class="sxs-lookup"><span data-stu-id="90be0-120">You can select more than one dimension, but no dimension can be used more than once in a drillthrough action.</span></span>  
  
 <span data-ttu-id="90be0-121">このグリッドには次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="90be0-121">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="90be0-122">列</span><span class="sxs-lookup"><span data-stu-id="90be0-122">Column</span></span>|<span data-ttu-id="90be0-123">説明</span><span class="sxs-lookup"><span data-stu-id="90be0-123">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="90be0-124">**Dimensions**</span><span class="sxs-lookup"><span data-stu-id="90be0-124">**Dimensions**</span></span>|<span data-ttu-id="90be0-125">返される属性の派生元のディメンションを選択します。</span><span class="sxs-lookup"><span data-stu-id="90be0-125">Select the dimension from which the returned attribute is derived.</span></span> <span data-ttu-id="90be0-126">メジャーをドリルスルーするには、[メジャー] を選択します。</span><span class="sxs-lookup"><span data-stu-id="90be0-126">Select MEASURES to drillthrough on measures.</span></span>|  
|<span data-ttu-id="90be0-127">**[返される列]**</span><span class="sxs-lookup"><span data-stu-id="90be0-127">**Return Columns**</span></span>|<span data-ttu-id="90be0-128">アクションが実行されたときに、選択されたディメンションから返される属性またはメジャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="90be0-128">Select the attribute or measure from the selected dimension to be returned when the action is run.</span></span>|  
  
 <span data-ttu-id="90be0-129">**追加のプロパティ**</span><span class="sxs-lookup"><span data-stu-id="90be0-129">**Additional Properties**</span></span>  
 <span data-ttu-id="90be0-130">展開すると、 **[既定]**、 **[最大行数]**、 **[呼び出し]**、 **[アプリケーション]**、 **[説明]**、 **[キャプション]**、および **[キャプションに MDX を使用]** の各オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="90be0-130">Expand to view the **Default**, **Maximum rows**, **Invocation**, **Application**, **Description**, **Caption**, and **Caption Is MDX** options.</span></span>  
  
 <span data-ttu-id="90be0-131">**[Default]**</span><span class="sxs-lookup"><span data-stu-id="90be0-131">**Default**</span></span>  
 <span data-ttu-id="90be0-132">このドリルスルー アクションを既定のドリルスルー アクションとして含める場合は **[True]** を選択します。それ以外の場合は、 **[False]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="90be0-132">Select **True** to include this drillthrough action as a default drillthrough action, otherwise, select **False**.</span></span>  
  
 <span data-ttu-id="90be0-133">`RETURN`クライアントアプリケーションによって実行される MDX ステートメントで句を省略した場合 `DRILLTHROUGH` 、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスはすべての既定のドリルスルーアクションを評価し、空でないセットを返す最初の既定のドリルスルーアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="90be0-133">If the `RETURN` clause is omitted from an MDX `DRILLTHROUGH` statement executed by a client application, the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance evaluates all default drillthrough actions and runs the first default drillthrough action that returns a non-empty set.</span></span> <span data-ttu-id="90be0-134">MDX ステートメントの詳細につい `DRILLTHROUGH` ては、「 [mdx&#41;&#40;のドリルスルーステートメント](/sql/mdx/mdx-data-manipulation-drillthrough)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90be0-134">For more information about the MDX `DRILLTHROUGH` statement, see [DRILLTHROUGH Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-drillthrough).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="90be0-135">このオプションは、下位互換性を保つために使用します。</span><span class="sxs-lookup"><span data-stu-id="90be0-135">This option is used for backwards compatibility purposes.</span></span>  
  
 <span data-ttu-id="90be0-136">**[最大行数]**</span><span class="sxs-lookup"><span data-stu-id="90be0-136">**Maximum rows**</span></span>  
 <span data-ttu-id="90be0-137">ドリルスルー アクションによって返される最大行数を入力します。</span><span class="sxs-lookup"><span data-stu-id="90be0-137">Type the maximum number of rows to be returned by the drillthrough action.</span></span> <span data-ttu-id="90be0-138">このオプションを 0 または空の値に設定すると、ドリルスルー アクションによって取得されたすべての行がクライアント アプリケーションに返されます。</span><span class="sxs-lookup"><span data-stu-id="90be0-138">Setting this option to zero or an empty value indicates that the drillthrough action returns all rows retrieved by the action to the client application.</span></span>  
  
 <span data-ttu-id="90be0-139">**[呼び出し]**</span><span class="sxs-lookup"><span data-stu-id="90be0-139">**Invocation**</span></span>  
 <span data-ttu-id="90be0-140">いつアクションを実行する必要があるかを設定します。</span><span class="sxs-lookup"><span data-stu-id="90be0-140">Select the setting that indicates when the action should be carried out.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="90be0-141">このオプションは、クライアント アプリケーションがアクションをいつ実行するかについて推奨するだけで、アクションの呼び出しを直接制御することはありません。</span><span class="sxs-lookup"><span data-stu-id="90be0-141">This option only provides a recommendation to a client application as to when to execute an action, and does not directly control the invocation of the action.</span></span>  
  
 <span data-ttu-id="90be0-142">次の表では、使用可能な設定について説明しています。</span><span class="sxs-lookup"><span data-stu-id="90be0-142">The following table describes the available settings.</span></span>  
  
|<span data-ttu-id="90be0-143">値</span><span class="sxs-lookup"><span data-stu-id="90be0-143">Value</span></span>|<span data-ttu-id="90be0-144">説明</span><span class="sxs-lookup"><span data-stu-id="90be0-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="90be0-145">Batch</span><span class="sxs-lookup"><span data-stu-id="90be0-145">Batch</span></span>|<span data-ttu-id="90be0-146">アクションは、バッチ操作または [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] タスクの一部として実行されます。</span><span class="sxs-lookup"><span data-stu-id="90be0-146">The action should run as part of a batch operation or an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] task.</span></span>|  
|<span data-ttu-id="90be0-147">Interactive</span><span class="sxs-lookup"><span data-stu-id="90be0-147">Interactive</span></span>|<span data-ttu-id="90be0-148">アクションは、ユーザーがアクションを呼び出したときに実行されます。</span><span class="sxs-lookup"><span data-stu-id="90be0-148">The action runs when the user invokes the action.</span></span>|  
|<span data-ttu-id="90be0-149">[オープン時]</span><span class="sxs-lookup"><span data-stu-id="90be0-149">On Open</span></span>|<span data-ttu-id="90be0-150">アクションは、キューブが最初に開いたときに実行されます。</span><span class="sxs-lookup"><span data-stu-id="90be0-150">The action runs when the cube is first opened.</span></span>|  
  
 <span data-ttu-id="90be0-151">**Application**</span><span class="sxs-lookup"><span data-stu-id="90be0-151">**Application**</span></span>  
 <span data-ttu-id="90be0-152">ドリルスルー アクションを実行できるアプリケーションの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="90be0-152">Type the name of the application that can execute the drillthrough action.</span></span>  
  
 <span data-ttu-id="90be0-153">このオプションを使用して、どのクライアント アプリケーションが最もよくこのアクションを使用するか識別したり、ポップアップ メニューのアクションの横に適切なアイコンを表示したりできます。</span><span class="sxs-lookup"><span data-stu-id="90be0-153">You can also use this option to identify which client application most commonly uses this action, as well as to display appropriate icons next to the action in a pop-up menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="90be0-154">このオプションは、どのクライアント アプリケーションがアクションを実行するかについて推奨するだけで、アクションへのアクセスを直接制御することはありません。</span><span class="sxs-lookup"><span data-stu-id="90be0-154">This option only provides a recommendation to a client application as to what client application should execute an action, and does not directly control access to the action.</span></span> <span data-ttu-id="90be0-155">クライアント アプリケーションでは、他のクライアント アプリケーションに関連付けられているすべてのアクションを非表示にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="90be0-155">Client applications should hide any actions that are associated with other client applications.</span></span>  
  
 <span data-ttu-id="90be0-156">**説明**</span><span class="sxs-lookup"><span data-stu-id="90be0-156">**Description**</span></span>  
 <span data-ttu-id="90be0-157">アクションの説明をオプションで入力します。</span><span class="sxs-lookup"><span data-stu-id="90be0-157">Type the optional description of the action.</span></span>  
  
 <span data-ttu-id="90be0-158">**Caption**</span><span class="sxs-lookup"><span data-stu-id="90be0-158">**Caption**</span></span>  
 <span data-ttu-id="90be0-159">**[キャプションに MDX を使用]** を **[False]** に設定する場合は、クライアント アプリケーションでアクションに対して表示されるキャプションを入力します。</span><span class="sxs-lookup"><span data-stu-id="90be0-159">Type the caption to be displayed for the action in the client application if **Caption Is MDX** is set to **False**.</span></span>  
  
 <span data-ttu-id="90be0-160">**[キャプションに MDX を使用]** を **[True]** に設定する場合は、キャプションの文字列を返す多次元式 (MDX) を入力します。</span><span class="sxs-lookup"><span data-stu-id="90be0-160">Type the Multidimensional Expressions (MDX) expression that returns a string for the caption if **Caption Is MDX** is set to **True**.</span></span>  
  
 <span data-ttu-id="90be0-161">**キャプションは MDX です**</span><span class="sxs-lookup"><span data-stu-id="90be0-161">**Caption Is MDX**</span></span>  
 <span data-ttu-id="90be0-162">クライアント アプリケーションのアクションに表示されるキャプションを表すリテラル文字列が **[キャプション]** に入力されている場合は、 **[False]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="90be0-162">Select **False** to indicate that **Caption** contains a literal string representing a caption to be displayed for the action in the client application.</span></span>  
  
 <span data-ttu-id="90be0-163">クライアント アプリケーションのアクションに表示されるキャプションを表す文字列を返す MDX 式が **[キャプション]** に入力されている場合は、 **[True]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="90be0-163">Select **True** to indicate that **Caption** contains an MDX expression that returns a string representing a caption to be displayed for the action in the client application.</span></span> <span data-ttu-id="90be0-164">MDX 式は、アクションがクライアント アプリケーションに返される前に解析される必要があります。</span><span class="sxs-lookup"><span data-stu-id="90be0-164">The MDX expression must be resolved before the action is returned to the client application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90be0-165">参照</span><span class="sxs-lookup"><span data-stu-id="90be0-165">See Also</span></span>  
 <span data-ttu-id="90be0-166">[MDX&#41; 参照 &#40;多次元式](/sql/mdx/multidimensional-expressions-mdx-reference) </span><span class="sxs-lookup"><span data-stu-id="90be0-166">[Multidimensional Expressions &#40;MDX&#41; Reference](/sql/mdx/multidimensional-expressions-mdx-reference) </span></span>  
 <span data-ttu-id="90be0-167">[アクション &#40;キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="90be0-167">[Actions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="90be0-168">[ツールバーの [&#40;の操作] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="90be0-168">[Toolbar &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="90be0-169">[アクション &#40;オーガナイザーの [アクション] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="90be0-169">[Action Organizer &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="90be0-170">[[計算ツール] &#40;[アクション] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="90be0-170">[Calculation Tools &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="90be0-171">[アクションフォームエディター &#40;[アクション] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="90be0-171">[Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="90be0-172">[レポートアクションフォームエディター &#40;[アクション] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="90be0-172">[Report Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)</span></span>  
  
  
