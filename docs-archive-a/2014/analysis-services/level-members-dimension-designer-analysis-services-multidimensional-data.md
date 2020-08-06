---
title: レベルとメンバー ([ブラウザー] タブ、ディメンションデザイナー) (Analysis Services 多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.browsertab.levelsandmembers.f1
ms.assetid: 3f61e384-5b4e-4480-a7ed-b408de2fdea7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 21680f00b82b5410e2c7a67122fdcfeb78c999dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743585"
---
# <a name="level-and-members-browser-tab-dimension-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="9f5db-102">レベルとメンバー ([ブラウザー] タブ、ディメンション デザイナー) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="9f5db-102">Level and Members (Browser Tab, Dimension Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="9f5db-103">このペインを使用すると、現在選択している階層と言語のメンバーを参照できます。</span><span class="sxs-lookup"><span data-stu-id="9f5db-103">Use this pane to browse the members of the currently selected hierarchy and language.</span></span> <span data-ttu-id="9f5db-104">参照する階層または言語を選択するには、 **ツール バー** ペインの **[階層]** および **[言語]** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="9f5db-104">To select a hierarchy or language to browse, use the **Hierarchy** and **Language** options on the **Toolbar** pane.</span></span> <span data-ttu-id="9f5db-105">ツールバーペインの詳細については、「[ツールバー &#40;ブラウザータブ」、「ディメンションデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f5db-105">For more information about the Toolbar pane, see [Toolbar &#40;Browser Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="writeback-mode"></a><span data-ttu-id="9f5db-106">書き戻しモード</span><span class="sxs-lookup"><span data-stu-id="9f5db-106">Writeback Mode</span></span>  
 <span data-ttu-id="9f5db-107">書き戻しモードが有効な場合、このペインの機能は変わります。</span><span class="sxs-lookup"><span data-stu-id="9f5db-107">The functionality of this pane changes if writeback mode is enabled.</span></span> <span data-ttu-id="9f5db-108">書き戻しモードを有効にするには、選択したディメンションを書き込み可能にする (つまり、ディメンションの `WriteEnabled` プロパティを true に設定する) 必要があり、さらにディメンションを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f5db-108">The selected dimension must be write-enabled (in other words, the `WriteEnabled` property of the dimension must be set to true) and the dimension must be deployed to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance in order to enable writeback mode.</span></span>  
  
 <span data-ttu-id="9f5db-109">書き戻しモードを有効にするには、 **ツールバー** ペインで **[書き戻し]** を選択するか、 **レベルとメンバー** ペインを右クリックしてショートカット メニューから **[書き戻し]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9f5db-109">To enable writeback mode, you can either select **Writeback** from the **Toolbar** pane, or right-click the **Level and Members** pane and select **Writeback** from the context menu.</span></span>  
  
 <span data-ttu-id="9f5db-110">書き戻しモードを有効にした場合、 **レベルとメンバー** ペインで次の操作を実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9f5db-110">If writeback mode is enabled, you can perform the following additional actions in the **Level and Members** pane:</span></span>  
  
|<span data-ttu-id="9f5db-111">To Do</span><span class="sxs-lookup"><span data-stu-id="9f5db-111">To do</span></span>|<span data-ttu-id="9f5db-112">実行内容</span><span class="sxs-lookup"><span data-stu-id="9f5db-112">Perform</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="9f5db-113">選択した階層に兄弟メンバーと子メンバーを作成する。</span><span class="sxs-lookup"><span data-stu-id="9f5db-113">Create sibling and child members within the selected hierarchy.</span></span>|<span data-ttu-id="9f5db-114">選択したメンバーを右クリックしてショートカット メニューを開き、兄弟メンバーを作成する場合は **[兄弟の作成]**、子メンバーを作成する場合は **[子の作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9f5db-114">Right-click the selected member and select either **Create Sibling**, to create a sibling member, or **Create Child**, to create a child member, from the context menu.</span></span>|  
|<span data-ttu-id="9f5db-115">階層の中で選択したメンバーを上または下に移動する。</span><span class="sxs-lookup"><span data-stu-id="9f5db-115">Move a selected member up or down the hierarchy.</span></span>|<span data-ttu-id="9f5db-116">選択したメンバーを適切な親メンバーまたは子メンバーにドラッグするか、 **ツール バー** ペインの **[インデント]** または **[インデント解除]** をクリックして、選択したメンバーの階層のレベルを上または下に移動します。</span><span class="sxs-lookup"><span data-stu-id="9f5db-116">Either drag the selected member to the appropriate parent or child member, or click **Increase Indent** or **Decrease Indent** on the **Toolbar** pane to move the selected member up or down the levels of the hierarchy.</span></span>|  
|<span data-ttu-id="9f5db-117">選択したメンバーの名前を変更する。</span><span class="sxs-lookup"><span data-stu-id="9f5db-117">Rename a selected member.</span></span>|<span data-ttu-id="9f5db-118">選択したメンバーを右クリックして **[名前の変更]** を選択するか、選択したメンバーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9f5db-118">Either right-click the selected member and select **Rename**, or click an already-selected member.</span></span>|  
|<span data-ttu-id="9f5db-119">メンバーのプロパティの値を編集する。</span><span class="sxs-lookup"><span data-stu-id="9f5db-119">Edit member property values</span></span>|<span data-ttu-id="9f5db-120">選択したメンバーの選択したメンバー プロパティの値をダブルクリックして、値を編集します。</span><span class="sxs-lookup"><span data-stu-id="9f5db-120">Double-click the value in the selected member property for the selected member to edit the value.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="9f5db-121">Options</span><span class="sxs-lookup"><span data-stu-id="9f5db-121">Options</span></span>  
 <span data-ttu-id="9f5db-122">**[現在のレベル]**</span><span class="sxs-lookup"><span data-stu-id="9f5db-122">**Current level**</span></span>  
 <span data-ttu-id="9f5db-123">**[ツリー]** で現在選択されているメンバーが属するレベルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9f5db-123">Displays the level to which the currently selected member in **Tree** belongs.</span></span>  
  
 <span data-ttu-id="9f5db-124">**ツリー**</span><span class="sxs-lookup"><span data-stu-id="9f5db-124">**Tree**</span></span>  
 <span data-ttu-id="9f5db-125">現在選択されている階層と言語のメンバーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9f5db-125">Displays the members of the currently selected hierarchy and language.</span></span>  
  
 <span data-ttu-id="9f5db-126">ツール バー ペインの **[メンバーのプロパティ]** オプションでメンバーのプロパティを選択した場合、各メンバーのプロパティが列として表示されます。</span><span class="sxs-lookup"><span data-stu-id="9f5db-126">If member properties are selected from the **Member Properties** option of the Toolbar pane, each member property is displayed as a column.</span></span>  
  
 <span data-ttu-id="9f5db-127">書き戻しモードが有効な場合、ディメンション内のキー属性に関連付けられている各キー列について、1 つの列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9f5db-127">If writeback mode is enabled, one column for each key column associated with the key attribute in the dimension is displayed.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="9f5db-128">コンテキスト メニュー</span><span class="sxs-lookup"><span data-stu-id="9f5db-128">Context Menu</span></span>  
 <span data-ttu-id="9f5db-129">選択したメンバーの **レベルとメンバー** ペインの任意の場所を右クリックして表示されるショートカット メニューでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9f5db-129">The following options are available in the context menu displayed by right-clicking any part of the **Level and Members** pane for the selected member:</span></span>  
  
 <span data-ttu-id="9f5db-130">**[兄弟の作成]**</span><span class="sxs-lookup"><span data-stu-id="9f5db-130">**Create sibling**</span></span>  
 <span data-ttu-id="9f5db-131">選択したメンバーと同じレベルに、新しいメンバーを作成します。</span><span class="sxs-lookup"><span data-stu-id="9f5db-131">Creates a new member at the same level as the selected member.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f5db-132">このオプションは、[(すべて)] レベル以外のレベルのメンバーが選択されている場合にのみ有効になります。</span><span class="sxs-lookup"><span data-stu-id="9f5db-132">This option is enabled only if a member at a level other than the (All) level is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f5db-133">このオプションは、書き戻しモードが有効な場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="9f5db-133">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="9f5db-134">**[子の作成]**</span><span class="sxs-lookup"><span data-stu-id="9f5db-134">**Create child**</span></span>  
 <span data-ttu-id="9f5db-135">選択したメンバーより 1 つ下のレベルに、選択したメンバーの子として新しいメンバーを作成します。</span><span class="sxs-lookup"><span data-stu-id="9f5db-135">Creates a new member at the next lower level as the selected member, as a child of the selected member.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f5db-136">このオプションは、最も低いレベル以外のメンバーが選択されている場合にのみ有効になります。</span><span class="sxs-lookup"><span data-stu-id="9f5db-136">This option is enabled only if a member at a level other than the lowest level is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f5db-137">このオプションは、書き戻しモードが有効な場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="9f5db-137">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="9f5db-138">**［切り取り］**</span><span class="sxs-lookup"><span data-stu-id="9f5db-138">**Cut**</span></span>  
 <span data-ttu-id="9f5db-139">選択したメンバーをクリップボードにコピーした後、階層から削除します。</span><span class="sxs-lookup"><span data-stu-id="9f5db-139">Copies the selected members to the clipboard and removes them from the hierarchy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f5db-140">このオプションは、[すべて] メンバー以外のメンバーが選択されている場合にのみ有効になります。</span><span class="sxs-lookup"><span data-stu-id="9f5db-140">This option is enabled only if a member other than the All member is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f5db-141">このオプションは、書き戻しモードが有効な場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="9f5db-141">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="9f5db-142">**貼り付け**</span><span class="sxs-lookup"><span data-stu-id="9f5db-142">**Paste**</span></span>  
 <span data-ttu-id="9f5db-143">選択したメンバーの直後に、以前に **[切り取り]** を使用して切り取ったメンバーを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="9f5db-143">Pastes members previously removed using **Cut** immediately after the selected member.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f5db-144">このオプションは、書き戻しモードが有効な場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="9f5db-144">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="9f5db-145">**削除**</span><span class="sxs-lookup"><span data-stu-id="9f5db-145">**Delete**</span></span>  
 <span data-ttu-id="9f5db-146">選択されているメンバーを階層から削除します。</span><span class="sxs-lookup"><span data-stu-id="9f5db-146">Removes the selected members from the hierarchy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f5db-147">このオプションは、[すべて] メンバー以外のメンバーが選択されている場合にのみ有効になります。</span><span class="sxs-lookup"><span data-stu-id="9f5db-147">This option is enabled only if a member other than the All member is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f5db-148">このオプションは、書き戻しモードが有効な場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="9f5db-148">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="9f5db-149">**Rename**</span><span class="sxs-lookup"><span data-stu-id="9f5db-149">**Rename**</span></span>  
 <span data-ttu-id="9f5db-150">選択したメンバーの名前を編集する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="9f5db-150">Select to edit the name of the selected member.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f5db-151">このオプションは、[すべて] メンバー以外のメンバーが選択されている場合にのみ有効になります。</span><span class="sxs-lookup"><span data-stu-id="9f5db-151">This option is enabled only if a member other than the All member is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f5db-152">このオプションは、書き戻しモードが有効な場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="9f5db-152">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="9f5db-153">**[メンバーのフィルター選択]**</span><span class="sxs-lookup"><span data-stu-id="9f5db-153">**Filter Members**</span></span>  
 <span data-ttu-id="9f5db-154">**[メンバーのフィルター選択]** ダイアログ ボックスを表示し、**レベルとメンバー**に表示される選択した階層のメンバーをフィルター選択できます。</span><span class="sxs-lookup"><span data-stu-id="9f5db-154">Displays the **Filter Members** dialog box to filter members displayed in **Level and Members** for the selected hierarchy.</span></span> <span data-ttu-id="9f5db-155">**[メンバーのフィルター選択]** ダイアログ ボックスの詳細については、「[[メンバーのフィルター選択] ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f5db-155">For more information about the **Filter Members** dialog box, see [Filter Members Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="9f5db-156">**すべて展開**</span><span class="sxs-lookup"><span data-stu-id="9f5db-156">**Expand All**</span></span>  
 <span data-ttu-id="9f5db-157">**[ツリー]** 内のすべてのメンバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="9f5db-157">Expands all members in **Tree**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f5db-158">このオプションは、最も低いレベル以外のメンバーが選択されている場合にのみ有効になります。</span><span class="sxs-lookup"><span data-stu-id="9f5db-158">This option is enabled only if a member at a level other than the lowest level is selected.</span></span>  
  
 <span data-ttu-id="9f5db-159">**すべて折りたたむ**</span><span class="sxs-lookup"><span data-stu-id="9f5db-159">**Collapse All**</span></span>  
 <span data-ttu-id="9f5db-160">**[ツリー]** 内のすべてのメンバーを折りたたみます。</span><span class="sxs-lookup"><span data-stu-id="9f5db-160">Collapse all members in **Tree**.</span></span>  
  
 <span data-ttu-id="9f5db-161">**[メンバーの展開]**</span><span class="sxs-lookup"><span data-stu-id="9f5db-161">**Expand Member**</span></span>  
 <span data-ttu-id="9f5db-162">**[ツリー]** 内で選択されているメンバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="9f5db-162">Expand the selected member in **Tree**.</span></span>  
  
 <span data-ttu-id="9f5db-163">**[メンバーの折りたたみ]**</span><span class="sxs-lookup"><span data-stu-id="9f5db-163">**Collapse Member**</span></span>  
 <span data-ttu-id="9f5db-164">**[ツリー]** 内で選択されているメンバーを折りたたみます。</span><span class="sxs-lookup"><span data-stu-id="9f5db-164">Collapse the selected member in **Tree**.</span></span>  
  
 <span data-ttu-id="9f5db-165">**[書き戻し]**</span><span class="sxs-lookup"><span data-stu-id="9f5db-165">**Writeback**</span></span>  
 <span data-ttu-id="9f5db-166">選択すると、書き戻しモードを有効にします。</span><span class="sxs-lookup"><span data-stu-id="9f5db-166">Select to enable writeback mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f5db-167">参照</span><span class="sxs-lookup"><span data-stu-id="9f5db-167">See Also</span></span>  
 <span data-ttu-id="9f5db-168">[ツールバー &#40;[ブラウザー] タブ、ディメンションデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="9f5db-168">[Toolbar &#40;Browser Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="9f5db-169">ブラウザー &#40;ディメンションデザイナー&#41; &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="9f5db-169">Browser &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](browser-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
