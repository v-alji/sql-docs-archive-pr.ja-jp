---
title: アクションフォームエディター (キューブデザイナーの [アクション] タブ) (Analysis Services 多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionexpression.action.f1
ms.assetid: c363a29b-6099-473c-9625-460cc15b3d95
author: minewiskan
ms.author: owend
ms.openlocfilehash: b08ed03e843ba206f22969f9ada0da5a590a5811
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632806"
---
# <a name="action-form-editor-actions-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="fe801-102">アクション フォーム エディター (キューブ デザイナーの [アクション] タブ) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="fe801-102">Action Form Editor (Actions Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="fe801-103">キューブ デザイナーの **[アクション** ] タブのアクション フォーム エディター ペインを使用すると、標準のアクションを作成したり変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="fe801-103">Use the Action Form Editor pane on the **Actions** tab in Cube Designer to create and modify standard actions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fe801-104">Options</span><span class="sxs-lookup"><span data-stu-id="fe801-104">Options</span></span>  
 <span data-ttu-id="fe801-105">**名前**</span><span class="sxs-lookup"><span data-stu-id="fe801-105">**Name**</span></span>  
 <span data-ttu-id="fe801-106">アクションの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="fe801-106">Type the name of the action.</span></span>  
  
 <span data-ttu-id="fe801-107">**[アクションの対象]**</span><span class="sxs-lookup"><span data-stu-id="fe801-107">**Action Target**</span></span>  
 <span data-ttu-id="fe801-108">**[対象になる種類]** オプションと **[対象になるオブジェクト]** オプションの表示を拡張します。</span><span class="sxs-lookup"><span data-stu-id="fe801-108">Expand to view the **Target type** and **Target object** options.</span></span>  
  
 <span data-ttu-id="fe801-109">**変換後の型**</span><span class="sxs-lookup"><span data-stu-id="fe801-109">**Target type**</span></span>  
 <span data-ttu-id="fe801-110">アクションが関連付けられるオブジェクトの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="fe801-110">Select the type of object to which the action is to be associated.</span></span> <span data-ttu-id="fe801-111">サーバーは、指定された種類のオブジェクトに適用されるアクションのみをクライアントに返します。</span><span class="sxs-lookup"><span data-stu-id="fe801-111">The server returns to the client only those actions that apply to the object of the specified type.</span></span> <span data-ttu-id="fe801-112">アクションは、 **[条件]** が一致する場合、および次の表に指定されたオブジェクトが選択された場合に、クライアントに対して使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="fe801-112">The action is available to the client if the **Condition** is met and if the objects specified in the following table are selected.</span></span>  
  
|<span data-ttu-id="fe801-113">値</span><span class="sxs-lookup"><span data-stu-id="fe801-113">Value</span></span>|<span data-ttu-id="fe801-114">選択されたオブジェクト</span><span class="sxs-lookup"><span data-stu-id="fe801-114">Selected Object</span></span>|  
|-----------|---------------------|  
|<span data-ttu-id="fe801-115">[属性メンバー]</span><span class="sxs-lookup"><span data-stu-id="fe801-115">Attribute members</span></span>|<span data-ttu-id="fe801-116">**[対象になるオブジェクト]** の属性に基づくレベルからメンバーが選択されます。</span><span class="sxs-lookup"><span data-stu-id="fe801-116">A member is selected from a level based on the attribute in **Target object**.</span></span>|  
|<span data-ttu-id="fe801-117">セル</span><span class="sxs-lookup"><span data-stu-id="fe801-117">Cells</span></span>|<span data-ttu-id="fe801-118">**[対象になるオブジェクト]** の名前付きセットが選択されます。</span><span class="sxs-lookup"><span data-stu-id="fe801-118">The named set in **Target object** is selected.</span></span> <span data-ttu-id="fe801-119">キューブ内のすべてのセルを選択するには、 **[すべてのセル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fe801-119">Select **All cells** to select all of the cells in the cube.</span></span>|  
|<span data-ttu-id="fe801-120">キューブ</span><span class="sxs-lookup"><span data-stu-id="fe801-120">Cube</span></span>|<span data-ttu-id="fe801-121">**[対象になるオブジェクト]** のキューブが選択されます。</span><span class="sxs-lookup"><span data-stu-id="fe801-121">The cube in **Target object** is selected.</span></span> <span data-ttu-id="fe801-122">現在のキューブを使用するには、[CURRENTCUBE] を選択します。</span><span class="sxs-lookup"><span data-stu-id="fe801-122">Select CURRENTCUBE to use the current cube.</span></span><br /><br /> <span data-ttu-id="fe801-123">注: キューブが名前を変更したり、アクションを他のキューブへコピーしたりする場合、[CURRENTCUBE] を使用することにより、移植性が向上します。</span><span class="sxs-lookup"><span data-stu-id="fe801-123">Note: Using CURRENTCUBE provides additional portability in cases where the cube may be renamed or the action copied to other cubes.</span></span> <span data-ttu-id="fe801-124">現在のキューブを表すために、[CURRENTCUBE] を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fe801-124">It is recommended that you use CURRENTCUBE to represent the current cube.</span></span>|  
|<span data-ttu-id="fe801-125">[ディメンションのメンバー]</span><span class="sxs-lookup"><span data-stu-id="fe801-125">Dimension members</span></span>|<span data-ttu-id="fe801-126">**[対象になるオブジェクト]** でディメンションのメンバーが選択されます。</span><span class="sxs-lookup"><span data-stu-id="fe801-126">A member of the dimension in **Target object** is selected.</span></span>|  
|<span data-ttu-id="fe801-127">Hierarchy</span><span class="sxs-lookup"><span data-stu-id="fe801-127">Hierarchy</span></span>|<span data-ttu-id="fe801-128">**[対象になるオブジェクト]** で階層が選択されます。</span><span class="sxs-lookup"><span data-stu-id="fe801-128">The hierarchy in **Target object** is selected.</span></span>|  
|<span data-ttu-id="fe801-129">[階層メンバー]</span><span class="sxs-lookup"><span data-stu-id="fe801-129">Hierarchy members</span></span>|<span data-ttu-id="fe801-130">**[対象になるオブジェクト]** で階層内のメンバーが選択されます。</span><span class="sxs-lookup"><span data-stu-id="fe801-130">A member within the hierarchy in **Target object** is selected.</span></span>|  
|<span data-ttu-id="fe801-131">Level</span><span class="sxs-lookup"><span data-stu-id="fe801-131">Level</span></span>|<span data-ttu-id="fe801-132">**[対象になるオブジェクト]** でレベルが選択されます。</span><span class="sxs-lookup"><span data-stu-id="fe801-132">The level in **Target object** is selected.</span></span>|  
|<span data-ttu-id="fe801-133">[レベル メンバー]</span><span class="sxs-lookup"><span data-stu-id="fe801-133">Level members</span></span>|<span data-ttu-id="fe801-134">**[対象になるオブジェクト]** でレベル内のメンバーが選択されます。</span><span class="sxs-lookup"><span data-stu-id="fe801-134">A member within the level in **Target object** is selected.</span></span>|  
  
 <span data-ttu-id="fe801-135">**ターゲットオブジェクト**</span><span class="sxs-lookup"><span data-stu-id="fe801-135">**Target object**</span></span>  
 <span data-ttu-id="fe801-136">アクションが関連付けられるオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="fe801-136">Select the object to which the action is to be associated.</span></span> <span data-ttu-id="fe801-137">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスは、選択したオブジェクトに適用されるこれらのアクションのみをクライアントに返します。</span><span class="sxs-lookup"><span data-stu-id="fe801-137">The [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance returns to the client only those actions that apply to the selected object.</span></span> <span data-ttu-id="fe801-138">使用可能なオブジェクトは、 **[対象になる種類]** の選択によって制限されます。</span><span class="sxs-lookup"><span data-stu-id="fe801-138">The list of available objects is constrained by the choice of **Target type**.</span></span>  
  
 <span data-ttu-id="fe801-139">**[条件 (省略可能)]**</span><span class="sxs-lookup"><span data-stu-id="fe801-139">**Condition (Optional)**</span></span>  
 <span data-ttu-id="fe801-140">オプションの条件を記述する多次元式 (MDX) を入力します。この式は、アクションが使用可能な場合に制限を設定する **[対象になるオブジェクト]** のメンバーと一緒に使用されます。</span><span class="sxs-lookup"><span data-stu-id="fe801-140">Enter the Multidimensional Expressions (MDX) expression that describes an optional condition, used in conjunction with **Target object**, which further restricts when the action is available.</span></span> <span data-ttu-id="fe801-141">この式は、ブール値を返す必要があります (true は、アクションが使用可能なことを示します)。</span><span class="sxs-lookup"><span data-stu-id="fe801-141">The expression must return a Boolean value that, if true, indicates the action is available.</span></span>  
  
 <span data-ttu-id="fe801-142">選択した要素を **[計算ツール]** ペインからこのオプションへドラッグして、選択した要素に対して MDX 構文を含めます。</span><span class="sxs-lookup"><span data-stu-id="fe801-142">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="fe801-143">**[アクションの内容]**</span><span class="sxs-lookup"><span data-stu-id="fe801-143">**Action Content**</span></span>  
 <span data-ttu-id="fe801-144">展開すると、 **[種類]** と **[アクションの式]** オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fe801-144">Expand to view the **Type** and **Action expression** options.</span></span>  
  
 <span data-ttu-id="fe801-145">**Type**</span><span class="sxs-lookup"><span data-stu-id="fe801-145">**Type**</span></span>  
 <span data-ttu-id="fe801-146">アクションが実行されるときのアクションの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="fe801-146">Select the type of action to take when the action is run.</span></span> <span data-ttu-id="fe801-147">次のアクションの種類が使用できます。</span><span class="sxs-lookup"><span data-stu-id="fe801-147">The following action types are available:</span></span>  
  
|<span data-ttu-id="fe801-148">値</span><span class="sxs-lookup"><span data-stu-id="fe801-148">Value</span></span>|<span data-ttu-id="fe801-149">説明</span><span class="sxs-lookup"><span data-stu-id="fe801-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fe801-150">データセット</span><span class="sxs-lookup"><span data-stu-id="fe801-150">Dataset</span></span>|<span data-ttu-id="fe801-151">クライアント アプリケーションによって実行および表示される、多次元データセットを表す多次元式 (MDX) ステートメントを返します。</span><span class="sxs-lookup"><span data-stu-id="fe801-151">Returns a Multidimensional Expressions (MDX) statement, representing a multidimensional dataset, to be run and displayed by the client application.</span></span>|  
|<span data-ttu-id="fe801-152">[専用]</span><span class="sxs-lookup"><span data-stu-id="fe801-152">Proprietary</span></span>|<span data-ttu-id="fe801-153">このアクションの **[アプリケーション]** 設定に関連付けられたクライアント アプリケーションによって、解釈される専用文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="fe801-153">Returns a proprietary string that can be interpreted by client applications associated with the **Application** setting for this action.</span></span>|  
|<span data-ttu-id="fe801-154">[行セット]</span><span class="sxs-lookup"><span data-stu-id="fe801-154">Rowset</span></span>|<span data-ttu-id="fe801-155">クライアント アプリケーションによって実行および表示される、表形式の行セットを表す多次元式 (MDX) ステートメントを返します。</span><span class="sxs-lookup"><span data-stu-id="fe801-155">Returns a Multidimensional Expressions (MDX) statement, representing a tabular rowset, to be run and displayed by the client application.</span></span>|  
|<span data-ttu-id="fe801-156">ステートメント</span><span class="sxs-lookup"><span data-stu-id="fe801-156">Statement</span></span>|<span data-ttu-id="fe801-157">クライアント アプリケーションによって実行されるコマンド文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="fe801-157">Returns a command string to be run by the client application.</span></span>|  
|<span data-ttu-id="fe801-158">URL</span><span class="sxs-lookup"><span data-stu-id="fe801-158">URL</span></span>|<span data-ttu-id="fe801-159">クライアント アプリケーション (通常は、インターネット ブラウザー) によって開かれる URL 文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="fe801-159">Returns a Uniform Resource Location (URL) string to be opened by the client application, typically with an Internet browser.</span></span>|  
  
 <span data-ttu-id="fe801-160">アクションの種類の詳細については、「[アクション &#40;Analysis Services - 多次元データ&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe801-160">For more information about action types, see [Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="fe801-161">**[アクションの式]**</span><span class="sxs-lookup"><span data-stu-id="fe801-161">**Action expression**</span></span>  
 <span data-ttu-id="fe801-162">実行するクライアント アプリケーションに対して、アクションによって返される文字列を返す多次元式 (MDX) を入力します。</span><span class="sxs-lookup"><span data-stu-id="fe801-162">Type the Multidimensional Expressions (MDX) expression that returns the string returned by the action to the client application for execution.</span></span>  
  
 <span data-ttu-id="fe801-163">**追加のプロパティ**</span><span class="sxs-lookup"><span data-stu-id="fe801-163">**Additional Properties**</span></span>  
 <span data-ttu-id="fe801-164">**[呼び出し]**、 **[アプリケーション]**、 **[説明]**、 **[キャプション]**、および **[キャプションに MDX を使用]** オプションの表示を拡張します。</span><span class="sxs-lookup"><span data-stu-id="fe801-164">Expand to view the **Invocation**, **Application**, **Description**, **Caption**, and **Caption Is MDX** options.</span></span>  
  
 <span data-ttu-id="fe801-165">**[呼び出し]**</span><span class="sxs-lookup"><span data-stu-id="fe801-165">**Invocation**</span></span>  
 <span data-ttu-id="fe801-166">いつアクションを実行する必要があるかを設定します。</span><span class="sxs-lookup"><span data-stu-id="fe801-166">Select the setting that indicates when the action should be carried out.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe801-167">このオプションは、クライアント アプリケーションがアクションをいつ実行するかについて推奨するだけで、アクションの呼び出しを直接制御することはありません。</span><span class="sxs-lookup"><span data-stu-id="fe801-167">This option only provides a recommendation to a client application as to when to execute an action, and does not directly control the invocation of the action.</span></span>  
  
 <span data-ttu-id="fe801-168">次の表では、使用可能な設定について説明しています。</span><span class="sxs-lookup"><span data-stu-id="fe801-168">The following table describes the available settings.</span></span>  
  
|<span data-ttu-id="fe801-169">値</span><span class="sxs-lookup"><span data-stu-id="fe801-169">Value</span></span>|<span data-ttu-id="fe801-170">説明</span><span class="sxs-lookup"><span data-stu-id="fe801-170">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fe801-171">Batch</span><span class="sxs-lookup"><span data-stu-id="fe801-171">Batch</span></span>|<span data-ttu-id="fe801-172">アクションは、バッチ操作または [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] タスクの一部として実行されます。</span><span class="sxs-lookup"><span data-stu-id="fe801-172">The action should run as part of a batch operation or an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] task.</span></span>|  
|<span data-ttu-id="fe801-173">Interactive</span><span class="sxs-lookup"><span data-stu-id="fe801-173">Interactive</span></span>|<span data-ttu-id="fe801-174">アクションは、ユーザーがアクションを呼び出したときに実行されます。</span><span class="sxs-lookup"><span data-stu-id="fe801-174">The action runs when the user invokes the action.</span></span>|  
|<span data-ttu-id="fe801-175">[オープン時]</span><span class="sxs-lookup"><span data-stu-id="fe801-175">On Open</span></span>|<span data-ttu-id="fe801-176">アクションは、キューブが最初に開いたときに実行されます。</span><span class="sxs-lookup"><span data-stu-id="fe801-176">The action runs when the cube is first opened.</span></span>|  
  
 <span data-ttu-id="fe801-177">**Application**</span><span class="sxs-lookup"><span data-stu-id="fe801-177">**Application**</span></span>  
 <span data-ttu-id="fe801-178">**[アクションの式]** によって返される文字列を解釈できる、アプリケーションの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="fe801-178">Type the name of the application that can interpret the string returned by **Action expression**.</span></span>  
  
 <span data-ttu-id="fe801-179">このオプションを使用して、どのクライアント アプリケーションが最もよくこのアクションを使用するか識別したり、ポップアップ メニューのアクションの横に適切なアイコンを表示したりできます。</span><span class="sxs-lookup"><span data-stu-id="fe801-179">You can also use this option to identify which client application most commonly uses this action, as well as to display appropriate icons next to the action in a pop-up menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe801-180">このオプションは、どのクライアント アプリケーションがアクションを実行するかについて推奨するだけで、アクションへのアクセスを直接制御することはありません。</span><span class="sxs-lookup"><span data-stu-id="fe801-180">This option only provides a recommendation to a client application as to what client application should execute an action, and does not directly control access to the action.</span></span> <span data-ttu-id="fe801-181">クライアント アプリケーションでは、他のクライアント アプリケーションに関連付けられているすべてのアクションを非表示にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe801-181">Client applications should hide any actions that are associated with other client applications.</span></span>  
  
 <span data-ttu-id="fe801-182">**説明**</span><span class="sxs-lookup"><span data-stu-id="fe801-182">**Description**</span></span>  
 <span data-ttu-id="fe801-183">アクションの説明をオプションで入力します。</span><span class="sxs-lookup"><span data-stu-id="fe801-183">Type the optional description of the action.</span></span>  
  
 <span data-ttu-id="fe801-184">**Caption**</span><span class="sxs-lookup"><span data-stu-id="fe801-184">**Caption**</span></span>  
 <span data-ttu-id="fe801-185">**[キャプションに MDX を使用]** を **[False]** に設定する場合は、クライアント アプリケーションでアクションに対して表示されるキャプションを入力します。</span><span class="sxs-lookup"><span data-stu-id="fe801-185">Type the caption to be displayed for the action in the client application if **Caption Is MDX** is set to **False**.</span></span>  
  
 <span data-ttu-id="fe801-186">**[キャプションに MDX を使用]** を **[True]** に設定する場合は、キャプションの文字列を返す多次元式 (MDX) を入力します。</span><span class="sxs-lookup"><span data-stu-id="fe801-186">Type the Multidimensional Expressions (MDX) expression that returns a string for the caption if **Caption Is MDX** is set to **True**.</span></span>  
  
 <span data-ttu-id="fe801-187">**True**</span><span class="sxs-lookup"><span data-stu-id="fe801-187">**Caption is MDX**</span></span>  
 <span data-ttu-id="fe801-188">クライアント アプリケーションのアクションに表示されるキャプションを表すリテラル文字列が **[キャプション]** に入力されている場合は、 **[False]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fe801-188">Select **False** to indicate that **Caption** contains a literal string representing a caption to be displayed for the action in the client application.</span></span>  
  
 <span data-ttu-id="fe801-189">クライアント アプリケーションのアクションに表示されるキャプションを表す文字列を返す MDX 式が **[キャプション]** に入力されている場合は、 **[True]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fe801-189">Select **True** to indicate that **Caption** contains an MDX expression that returns a string representing a caption to be displayed for the action in the client application.</span></span> <span data-ttu-id="fe801-190">MDX 式は、アクションがクライアント アプリケーションに返される前に解析される必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe801-190">The MDX expression must be resolved before the action is returned to the client application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe801-191">参照</span><span class="sxs-lookup"><span data-stu-id="fe801-191">See Also</span></span>  
 <span data-ttu-id="fe801-192">[アクション &#40;キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fe801-192">[Actions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="fe801-193">[ツールバーの [&#40;の操作] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fe801-193">[Toolbar &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="fe801-194">[アクション &#40;オーガナイザーの [アクション] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fe801-194">[Action Organizer &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="fe801-195">[[計算ツール] &#40;[アクション] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fe801-195">[Calculation Tools &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="fe801-196">[ドリルスルーアクションフォームエディター &#40;[アクション] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fe801-196">[Drillthrough Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="fe801-197">[レポートアクションフォームエディター &#40;[アクション] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="fe801-197">[Report Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)</span></span>  
  
  
