---
title: '[スクリプトオーガナイザー] (キューブデザイナーの [計算] タブ) (Analysis Services 多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.calculationsview.scriptorganizerpane.f1
ms.assetid: 92624ca4-de67-4ebd-aab2-8adb527d327e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4ee8ccb491995176dc56da90e4cbf48961e30e98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633367"
---
# <a name="script-organizer-calculations-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="1f0dc-102">[スクリプト オーガナイザー] (キューブ デザイナーの [計算] タブ) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="1f0dc-102">Script Organizer (Calculations Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="1f0dc-103">キューブ デザイナーの **[計算]** タブの **[スクリプト オーガナイザー]** ペインを使用すると、指定したキューブのキューブ スクリプトに含まれた計算されるメンバー、名前付きセット、およびスクリプト コマンドにアクセスして順序を並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="1f0dc-103">Use the **Script Organizer** pane on the **Calculations** tab in Cube Designer to access and reorder the calculated members, named sets, and script commands contained in the cube script for the specified cube.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1f0dc-104">このペインは、フォーム ビューには表示されません。</span><span class="sxs-lookup"><span data-stu-id="1f0dc-104">This pane is not displayed in form view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1f0dc-105">Options</span><span class="sxs-lookup"><span data-stu-id="1f0dc-105">Options</span></span>  
 <span data-ttu-id="1f0dc-106">**Step**</span><span class="sxs-lookup"><span data-stu-id="1f0dc-106">**Step**</span></span>  
 <span data-ttu-id="1f0dc-107">キューブ スクリプト内の計算されるメンバー、名前付きセット、およびスクリプト コマンドの実行順を表示します。</span><span class="sxs-lookup"><span data-stu-id="1f0dc-107">Displays the execution order of the calculated members, named sets, and script commands within the cube script.</span></span>  
  
 <span data-ttu-id="1f0dc-108">**[ツール バー]** ペインまたはショートカット メニューで **[上へ移動]** または **[下へ移動]** をクリックし、計算の実行順を変更します。</span><span class="sxs-lookup"><span data-stu-id="1f0dc-108">Click **Move Up** or **Move Down** in the **Toolbar** pane or context menu to change the execution order of the calculations.</span></span>  
  
 <span data-ttu-id="1f0dc-109">**Type**</span><span class="sxs-lookup"><span data-stu-id="1f0dc-109">**Type**</span></span>  
 <span data-ttu-id="1f0dc-110">計算されるメンバー、名前付きセット、またはスクリプト コマンドとして計算を識別するアイコンを表示します。</span><span class="sxs-lookup"><span data-stu-id="1f0dc-110">Displays an icon that identifies the calculation as a calculated member, a named set, or a script command.</span></span>  
  
 <span data-ttu-id="1f0dc-111">**コマンド**</span><span class="sxs-lookup"><span data-stu-id="1f0dc-111">**Command**</span></span>  
 <span data-ttu-id="1f0dc-112">計算されるメンバーおよび名前付きセットの場合はコマンドの名前を表示し、スクリプト コマンドの場合は計算の最初の行を表示します。</span><span class="sxs-lookup"><span data-stu-id="1f0dc-112">Displays the name of the command (for calculated members and named sets) or the first line of the calculation (for script commands.)</span></span>  
  
 <span data-ttu-id="1f0dc-113">フォーム ビューでコマンドを選択すると、各コマンドに応じた **スクリプト エディター**、 **計算されるメンバー フォーム エディター**、または **名前付きセット フォーム エディター** が表示されます。スクリプト ビューの場合は、 **スクリプト エディター** ペインでスクロールしてキューブ スクリプト内のコマンドの位置まで移動します。</span><span class="sxs-lookup"><span data-stu-id="1f0dc-113">Select a command to display the **Script Editor**, **Calculated Member Form Editor**, or **Named Set Form Editor** as appropriate for that command (in form view) or to scroll the contents of the **Script Editor** pane to the location of the command in the cube script (in script view).</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="1f0dc-114">コンテキスト メニュー</span><span class="sxs-lookup"><span data-stu-id="1f0dc-114">Context Menu</span></span>  
 <span data-ttu-id="1f0dc-115">**[スクリプト オーガナイザー]** ペインでコマンドを右クリックして表示されるショートカット メニューでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1f0dc-115">The following options are available in the context menu displayed by right-clicking a command in the **Script Organizer** pane:</span></span>  
  
|<span data-ttu-id="1f0dc-116">オプション</span><span class="sxs-lookup"><span data-stu-id="1f0dc-116">Option</span></span>|<span data-ttu-id="1f0dc-117">定義</span><span class="sxs-lookup"><span data-stu-id="1f0dc-117">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="1f0dc-118">**[新しい計算されるメンバー]**</span><span class="sxs-lookup"><span data-stu-id="1f0dc-118">**New Calculated Member**</span></span>|<span data-ttu-id="1f0dc-119">選択すると、 **計算されるメンバー フォーム エディター** が表示され、新しい計算されるメンバーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1f0dc-119">Select to display the **Calculated Member Form Editor** and create a new calculated member.</span></span> <span data-ttu-id="1f0dc-120">**計算されるメンバーフォームエディター**の詳細については、「[計算されるメンバーフォームエディター &#40;の計算] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f0dc-120">For more information about the **Calculated Member Form Editor**, see [Calculated Member Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="1f0dc-121">**[新しい名前付きセット]**</span><span class="sxs-lookup"><span data-stu-id="1f0dc-121">**New Named Set**</span></span>|<span data-ttu-id="1f0dc-122">選択すると、 **名前付きセット フォーム エディター** が表示され、新しい名前付きセットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1f0dc-122">Select to display the **Named Set Form Editor** and create a new named set.</span></span> <span data-ttu-id="1f0dc-123">**名前付きセットフォームエディター**の詳細については、「[名前付きセットフォームエディター &#40;の計算] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f0dc-123">For more information about the **Named Set Form Editor**, see [Named Set Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="1f0dc-124">**[新しいスクリプト コマンド]**</span><span class="sxs-lookup"><span data-stu-id="1f0dc-124">**New Script Command**</span></span>|<span data-ttu-id="1f0dc-125">選択すると、 **スクリプト エディター** が表示され、新しいスクリプト コマンドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1f0dc-125">Select to display the **Script Editor** and create a new script command.</span></span> <span data-ttu-id="1f0dc-126">**スクリプトエディター**の詳細については、「[スクリプトエディター &#40;の計算] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f0dc-126">For more information about the **Script Editor**, see [Script Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="1f0dc-127">**[上へ移動]**</span><span class="sxs-lookup"><span data-stu-id="1f0dc-127">**Move Up**</span></span>|<span data-ttu-id="1f0dc-128">選択した計算を 1 つ上に移動する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="1f0dc-128">Select to move the selected calculation up one place.</span></span><br /><br /> <span data-ttu-id="1f0dc-129">注: このオプションは、選択した計算を移動できない場合は無効です。</span><span class="sxs-lookup"><span data-stu-id="1f0dc-129">Note: This option is disabled if the selected calculation cannot be moved further.</span></span>|  
|<span data-ttu-id="1f0dc-130">**[下へ移動]**</span><span class="sxs-lookup"><span data-stu-id="1f0dc-130">**Move Down**</span></span>|<span data-ttu-id="1f0dc-131">選択されている計算を 1 つ下に移動する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="1f0dc-131">Select to move the selected calculation down one place.</span></span><br /><br /> <span data-ttu-id="1f0dc-132">注: このオプションは、選択した計算を移動できない場合は無効です。</span><span class="sxs-lookup"><span data-stu-id="1f0dc-132">Note: This option is disabled if the selected calculation cannot be moved further.</span></span>|  
|<span data-ttu-id="1f0dc-133">**削除**</span><span class="sxs-lookup"><span data-stu-id="1f0dc-133">**Delete**</span></span>|<span data-ttu-id="1f0dc-134">選択した計算を削除する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="1f0dc-134">Select to delete the selected calculation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1f0dc-135">参照</span><span class="sxs-lookup"><span data-stu-id="1f0dc-135">See Also</span></span>  
 <span data-ttu-id="1f0dc-136">[キューブデザイナー &#40;Analysis Services-多次元データ&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="1f0dc-136">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="1f0dc-137">[ツールバー &#40;キューブデザイナーの [計算] タブ&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="1f0dc-137">[Toolbar &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="1f0dc-138">[計算ツール &#40;[計算] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="1f0dc-138">[Calculation Tools &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="1f0dc-139">[計算されるメンバーフォームエディター &#40;[計算] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="1f0dc-139">[Calculated Member Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="1f0dc-140">[名前付きセットフォームエディター &#40;の [計算] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="1f0dc-140">[Named Set Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="1f0dc-141">[スクリプトエディターの [&#40;の計算] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="1f0dc-141">[Script Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="1f0dc-142">キューブデザイナーの計算 &#40;&#41; &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="1f0dc-142">Calculations &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](calculations-cube-designer-analysis-services-multidimensional-data.md)  
  
  
