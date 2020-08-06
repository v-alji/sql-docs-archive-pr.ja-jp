---
title: '[オブジェクト エクスプローラーの詳細] ペイン | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.summary.report.f1
- sql12.swb.summary.general.f1
helpviewer_keywords:
- object search [SQL Server], Object Explorer
- Object Explorer
- object search [SQL Server]
- searching objects [SQL Server]
ms.assetid: b963e3c2-dc9e-4d38-bd28-2e00fe9e0e47
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0ec856ce01930683cf20683a418a658a5b877729
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741534"
---
# <a name="object-explorer-details-pane"></a><span data-ttu-id="94da1-102">[オブジェクト エクスプローラーの詳細] ペイン</span><span class="sxs-lookup"><span data-stu-id="94da1-102">Object Explorer Details Pane</span></span>
  <span data-ttu-id="94da1-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のコンポーネントである [オブジェクト エクスプローラーの詳細] は、サーバーのすべてのオブジェクトを表形式で表示し、それらのオブジェクトを管理するためのユーザー インターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="94da1-103">Object Explorer Details, a component of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], provides a tabular view of all the objects in the server and presents a user interface to manage them.</span></span> <span data-ttu-id="94da1-104">オブジェクト エクスプローラーの機能は、サーバーの種類によって多少異なりますが、データベースの開発機能と管理機能は、基本的にサーバーの種類にかかわりなく用意されています。</span><span class="sxs-lookup"><span data-stu-id="94da1-104">The capabilities of Object Explorer vary slightly depending on the type of server, but generally include the development features for databases and management features for all server types.</span></span>  
  
 <span data-ttu-id="94da1-105">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] では、[オブジェクト エクスプローラーの詳細] ペインが既定で表示されます。</span><span class="sxs-lookup"><span data-stu-id="94da1-105">The Object Explorer Details pane is visible in the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] by default.</span></span> <span data-ttu-id="94da1-106">オブジェクト エクスプローラーが表示されていない場合は、 **[表示]** メニューの **[オブジェクト エクスプローラーの詳細]** をクリックするか、 **F7**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="94da1-106">If you cannot see Object Explorer, on the **View** menu, click **Object Explorer Details** or press **F7**.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="94da1-107">では、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] の起動時に有効になっていた Microsoft Windows の [地域と言語のオプション] に基づく形式で日付が表示されます。</span><span class="sxs-lookup"><span data-stu-id="94da1-107">presents dates formatted with the Microsoft Windows Regional and Language Options in effect when [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] was started.</span></span> <span data-ttu-id="94da1-108">新しい設定を有効にするには、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94da1-108">Restart [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to reflect newer settings.</span></span>  
  
## <a name="object-explorer-details"></a><span data-ttu-id="94da1-109">[オブジェクト エクスプローラーの詳細]</span><span class="sxs-lookup"><span data-stu-id="94da1-109">Object Explorer Details</span></span>  
 <span data-ttu-id="94da1-110">[オブジェクト エクスプローラーの詳細] を使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス上のフォルダーやオブジェクト内を移動できます。</span><span class="sxs-lookup"><span data-stu-id="94da1-110">Object Explorer Details can be used to navigate through folders and objects on your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="94da1-111">32 ビット オペレーティング システムでは、オブジェクト エクスプローラーに表示できるオブジェクトは最大で 64,000 個です。</span><span class="sxs-lookup"><span data-stu-id="94da1-111">On 32-bit operating systems, Object Explorer can only display 64,000 objects.</span></span> <span data-ttu-id="94da1-112">追加のオブジェクトにアクセスするアイコンを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94da1-112">An icon must be selected to access additional objects.</span></span>  
  
 <span data-ttu-id="94da1-113">[オブジェクト エクスプローラーの詳細] には、次の表に説明するアイコンが用意されたツール バーがあります。</span><span class="sxs-lookup"><span data-stu-id="94da1-113">Object Explorer Details includes a toolbar which contains the icons described in the following table.</span></span> <span data-ttu-id="94da1-114">アイコンは、適切な場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="94da1-114">Icons are only available when appropriate.</span></span>  
  
|<span data-ttu-id="94da1-115">アイコン</span><span class="sxs-lookup"><span data-stu-id="94da1-115">Icon</span></span>|<span data-ttu-id="94da1-116">アクション</span><span class="sxs-lookup"><span data-stu-id="94da1-116">Action</span></span>|  
|----------|------------|  
|<span data-ttu-id="94da1-117">**戻る**</span><span class="sxs-lookup"><span data-stu-id="94da1-117">**Back**</span></span>|<span data-ttu-id="94da1-118">[オブジェクト エクスプローラーの詳細] に表示されている前の項目に移動します。</span><span class="sxs-lookup"><span data-stu-id="94da1-118">Moves to the previous items displayed in Object Explorer Details.</span></span> <span data-ttu-id="94da1-119">前の表示が検索操作の結果である場合は、検索を再実行します。</span><span class="sxs-lookup"><span data-stu-id="94da1-119">Re-runs a search when the previous display is the result of a search operation.</span></span>|  
|<span data-ttu-id="94da1-120">**進む**</span><span class="sxs-lookup"><span data-stu-id="94da1-120">**Forward**</span></span>|<span data-ttu-id="94da1-121">**[戻る]** 操作を選択した後に次の画面に移動します。</span><span class="sxs-lookup"><span data-stu-id="94da1-121">Moves to the next screen after a **Back** operation is selected.</span></span>|  
|<span data-ttu-id="94da1-122">**Up**</span><span class="sxs-lookup"><span data-stu-id="94da1-122">**Up**</span></span>|<span data-ttu-id="94da1-123">親のオブジェクトまたはフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="94da1-123">Moves to the parent object or folder.</span></span>|  
|<span data-ttu-id="94da1-124">**Synchronize**</span><span class="sxs-lookup"><span data-stu-id="94da1-124">**Synchronize**</span></span>|<span data-ttu-id="94da1-125">[オブジェクト エクスプローラーの詳細] で選択されているオブジェクトに、オブジェクト エクスプローラーのフォーカスを設定します。</span><span class="sxs-lookup"><span data-stu-id="94da1-125">Sets the focus of Object Explorer to the selected object in Object Explorer Details.</span></span>|  
|<span data-ttu-id="94da1-126">**Assert**</span><span class="sxs-lookup"><span data-stu-id="94da1-126">**Filter**</span></span>|<span data-ttu-id="94da1-127">利用できる場合、構成可能なオブジェクトのサブセットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="94da1-127">When available, shows a configurable subset of objects.</span></span>|  
|<span data-ttu-id="94da1-128">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="94da1-128">**Refresh**</span></span>|<span data-ttu-id="94da1-129">[オブジェクト エクスプローラーの詳細] の表示を更新します。</span><span class="sxs-lookup"><span data-stu-id="94da1-129">Refreshes the display in Object Explorer Details.</span></span>|  
|<span data-ttu-id="94da1-130">**検索**</span><span class="sxs-lookup"><span data-stu-id="94da1-130">**Search**</span></span>|<span data-ttu-id="94da1-131">特定のデータベース オブジェクトの検索語句を入力するための領域を提供します。</span><span class="sxs-lookup"><span data-stu-id="94da1-131">Provides an area to enter a search term for certain database objects.</span></span>|  
  
### <a name="column-header-selections"></a><span data-ttu-id="94da1-132">列ヘッダーの選択</span><span class="sxs-lookup"><span data-stu-id="94da1-132">Column Header Selections</span></span>  
 <span data-ttu-id="94da1-133">[オブジェクト エクスプローラーの詳細] には、選択可能な列があります。</span><span class="sxs-lookup"><span data-stu-id="94da1-133">Object Explorer Details has selectable columns.</span></span> <span data-ttu-id="94da1-134">任意の列ヘッダーを右クリックし、表示する項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="94da1-134">You can right-click in any column header and check the items that you want to display.</span></span> <span data-ttu-id="94da1-135">選択内容は、オブジェクト間を移動しても保持されます。</span><span class="sxs-lookup"><span data-stu-id="94da1-135">Your selections will be persisted across the different objects you navigate through.</span></span> <span data-ttu-id="94da1-136">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]をいったん終了して再起動した場合でも、各ユーザーの選択内容は保持されます。</span><span class="sxs-lookup"><span data-stu-id="94da1-136">Selections for each user are retained when you leave and restart [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="94da1-137">特定のオブジェクトの種類 (たとえばデータベース) についてすべての列を表示する場合、オブジェクトのセットが大量にあると表示速度が低下することがあります。</span><span class="sxs-lookup"><span data-stu-id="94da1-137">Showing all columns for some object types (such as Databases) might slow the display rendering slightly for large sets of objects.</span></span>  
  
### <a name="sorting"></a><span data-ttu-id="94da1-138">並べ替え</span><span class="sxs-lookup"><span data-stu-id="94da1-138">Sorting</span></span>  
 <span data-ttu-id="94da1-139">列ヘッダーを 1 回クリックすると、その列のデータを使用して並べ替えが行われます。</span><span class="sxs-lookup"><span data-stu-id="94da1-139">Clicking one time on a column header will sort by that column.</span></span> <span data-ttu-id="94da1-140">同じヘッダーを再度クリックすると、その列のデータを使用して逆順に並べ替えが行われます。</span><span class="sxs-lookup"><span data-stu-id="94da1-140">Clicking again on the same header reverse-sorts by that column.</span></span> <span data-ttu-id="94da1-141">並べ替えに関する選択内容は、別のオブジェクトやフォルダーに移動しても、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を再起動した後も、ユーザーごとに保持されます。</span><span class="sxs-lookup"><span data-stu-id="94da1-141">Sort selections are maintained for each user across objects and folders, and on [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] restart.</span></span>  
  
### <a name="filtering"></a><span data-ttu-id="94da1-142">Filtering</span><span class="sxs-lookup"><span data-stu-id="94da1-142">Filtering</span></span>  
 <span data-ttu-id="94da1-143">[オブジェクト エクスプローラーの詳細] に表示される特定のオブジェクトのリストは、[オブジェクト エクスプローラーの詳細] ツール バーの **[フィルター]** アイコンを使用してフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="94da1-143">Certain lists of objects displayed in Object Explorer Detail can be filtered using the **Filter** icon on the Object Explorer Details toolbar.</span></span> <span data-ttu-id="94da1-144">アイコンは、フィルター処理が可能な場合に有効になります。</span><span class="sxs-lookup"><span data-stu-id="94da1-144">The icon will be enabled when filtering is possible.</span></span>  
  
### <a name="details-pane"></a><span data-ttu-id="94da1-145">[詳細] ペイン</span><span class="sxs-lookup"><span data-stu-id="94da1-145">Details Pane</span></span>  
 <span data-ttu-id="94da1-146">[オブジェクト エクスプローラーの詳細] の下部には、選択したオブジェクトの詳細が表示されるパネルがあります。</span><span class="sxs-lookup"><span data-stu-id="94da1-146">The very bottom area of Object Explorer Details contains a panel that displays certain details of the selected object.</span></span> <span data-ttu-id="94da1-147">複数のオブジェクトが選択されている場合は、オブジェクトの数のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="94da1-147">Multiple object selections show only the count of the objects.</span></span> <span data-ttu-id="94da1-148">パネル内の項目が選択されているときに、 **[コピー]** アイコンをクリックすると、表示されているテキストがクリップボードにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="94da1-148">When items are selected in the panel, click the **Copy** icon to copy the displayed text to the clipboard.</span></span>  
  
 <span data-ttu-id="94da1-149">下方向キーを押すと、リスト内の次の項目に移動します。</span><span class="sxs-lookup"><span data-stu-id="94da1-149">The down arrow key moves the selection to the next item in the list.</span></span> <span data-ttu-id="94da1-150">上方向キーを押すと、リスト内の前の項目に移動します。</span><span class="sxs-lookup"><span data-stu-id="94da1-150">The up arrow key moves the selection to the previous item in the list.</span></span> <span data-ttu-id="94da1-151">方向キーを押したままにすると、項目間の移動が高速化されます。</span><span class="sxs-lookup"><span data-stu-id="94da1-151">Holding the arrow key down will speed through the items.</span></span> <span data-ttu-id="94da1-152">移動操作は、プロパティ リストの末尾または先頭に到達すると停止します。</span><span class="sxs-lookup"><span data-stu-id="94da1-152">The selection stops at the bottom or top of the property list.</span></span>  
  
 <span data-ttu-id="94da1-153">プロパティ名の最初の文字を入力すると、その文字で始まる次のプロパティに移動します。</span><span class="sxs-lookup"><span data-stu-id="94da1-153">Typing the first character of a property name moves the selection to the next property that begins with that character.</span></span>  
  
 <span data-ttu-id="94da1-154">プロパティが複数の列に配置されている場合は、左方向キーまたは右方向キーを使用して隣の列に移動できます。</span><span class="sxs-lookup"><span data-stu-id="94da1-154">When properties are arranged in multiple columns, use the left arrow and right arrow keys to move to adjacent columns.</span></span>  
  
 <span data-ttu-id="94da1-155">プロパティ値をクリップボードにコピーするには、次のキーボード キーの組み合わせを使用します。</span><span class="sxs-lookup"><span data-stu-id="94da1-155">To copy property values to the clipboard, use the following keyboard key combinations:</span></span>  
  
-   <span data-ttu-id="94da1-156">Ctrl</localizedText> + <localizedText>C</localizedText> を押すと、プロパティ値がコピーされます。</span><span class="sxs-lookup"><span data-stu-id="94da1-156">Ctrl+C copies the property value.</span></span>  
  
-   <span data-ttu-id="94da1-157">Ctrl</localizedText> + <localizedText>Shift</localizedText> + <localizedText>C</localizedText> を押すと、プロパティ名とプロパティ値がタブで区切られてコピーされます。</span><span class="sxs-lookup"><span data-stu-id="94da1-157">Ctrl+Shift+C copies the property name and the property value with a tab delimiter.</span></span>  
  
 <span data-ttu-id="94da1-158">すべてのプロパティ、またはすべてのプロパティと名前をクリップボードにコピーするには、[オブジェクト エクスプローラーの詳細] プロパティ ペインの右クリック メニューを使用します。</span><span class="sxs-lookup"><span data-stu-id="94da1-158">Use the right-click menu in the Object Explorer Details property pane to copy all properties or all properties and names to the clipboard.</span></span>  
  
 <span data-ttu-id="94da1-159">フィールドの幅が狭いためプロパティ値の一部が隠れている場合、プロパティ値を確認するには、値の上にマウス ポインターを置くか、プロパティ値に UI フォーカスを移動して、プロパティ値全体を示すツールヒントが表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="94da1-159">To display a property value when the field width does not completely display a property value, hover the mouse cursor over the value or set UI focus on the property value to activate a tool tip with the entire property value.</span></span> <span data-ttu-id="94da1-160">ユーザー補助機能のスクリーン リーダーでは、ユーザーが長いプロパティ値にフォーカスを移動すると、完全なプロパティ値が読み上げられます。</span><span class="sxs-lookup"><span data-stu-id="94da1-160">Accessibility screen readers will report the full property value when the user focuses on the long property value.</span></span>  
  
 <span data-ttu-id="94da1-161">プロパティ ペイン内のプロパティの数が多すぎてコンテンツ領域に収まらない場合、プロパティ ペインの右側にスクロール バーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="94da1-161">If the number of properties in the property pane exceeds that which will fit in the content area, a scroll bar will appear on the right side of the property pane.</span></span> <span data-ttu-id="94da1-162">このスクロール バーを使用して、コンテンツ領域のプロパティ値の表示状態を調整します。</span><span class="sxs-lookup"><span data-stu-id="94da1-162">Use the scroll bar to adjust the view of property values in the content area.</span></span>  
  
### <a name="multiple-object-selection"></a><span data-ttu-id="94da1-163">複数のオブジェクトの選択</span><span class="sxs-lookup"><span data-stu-id="94da1-163">Multiple Object Selection</span></span>  
 <span data-ttu-id="94da1-164">[オブジェクト エクスプローラーの詳細] では、複数のオブジェクトの選択がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="94da1-164">Object Explorer Details supports multiple object selection.</span></span> <span data-ttu-id="94da1-165">たとえば、オブジェクト エクスプローラーで [テーブル] を選択した後、[オブジェクト エクスプローラーの詳細] ウィンドウで **Ctrl** キーを押しながら複数のテーブルを選択して右クリックし、 **[削除]** または **[テーブルをスクリプト化]** を選択することで、選択したすべてのテーブルをまとめて操作できます。</span><span class="sxs-lookup"><span data-stu-id="94da1-165">For example, if you select Tables in Object Explorer, then in the Object Explorer Details window if you hold down the **Ctrl** key, you can select several tables, right-click them, and then select **Delete** or **Script Table AS** to act on all the selected tables immediately.</span></span> <span data-ttu-id="94da1-166">標準のコピー コマンドにより、表示されているテキストをクリップボードにコピーできます。</span><span class="sxs-lookup"><span data-stu-id="94da1-166">The standard copy commands will copy the displayed text to the clipboard.</span></span>  
  
## <a name="sql-server-object-search"></a><span data-ttu-id="94da1-167">SQL Server オブジェクトの検索</span><span class="sxs-lookup"><span data-stu-id="94da1-167">SQL Server Object Search</span></span>  
 <span data-ttu-id="94da1-168">ワイルドカード</span><span class="sxs-lookup"><span data-stu-id="94da1-168">Wildcards</span></span>  
  
-   <span data-ttu-id="94da1-169">標準のワイルドカード文字がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="94da1-169">Standard wildcard characters are supported.</span></span> <span data-ttu-id="94da1-170">たとえば、 **dm_os%counters** を検索すると、dm_os_memory_cache_counters と dm_os_performance_counters の両方が返されます。</span><span class="sxs-lookup"><span data-stu-id="94da1-170">For example, searching for **dm_os%counters** returns both dm_os_memory_cache_counters and dm_os_performance_counters.</span></span> <span data-ttu-id="94da1-171">詳細については、「[ワイルドカードを使用したテキストの検索](../../relational-databases/scripting/search-text-with-wildcards.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94da1-171">For more information, see [Search Text with Wildcards](../../relational-databases/scripting/search-text-with-wildcards.md).</span></span>  
  
 <span data-ttu-id="94da1-172">検索範囲</span><span class="sxs-lookup"><span data-stu-id="94da1-172">Search Scope</span></span>  
  
-   <span data-ttu-id="94da1-173">オブジェクト エクスプローラー ツリーの現在のフォーカスが検索範囲として使用されます。</span><span class="sxs-lookup"><span data-stu-id="94da1-173">Each search is scoped to the current focus in the Object Explorer tree.</span></span> <span data-ttu-id="94da1-174">たとえば、オブジェクト エクスプローラーのフォーカスがデータベースにある場合に **dm_os%counters** を検索すると、そのデータベースに含まれる dm_os_memory_cache_counters と dm_os_performance_counters が返されます。</span><span class="sxs-lookup"><span data-stu-id="94da1-174">For example, if the Object Explorer focus is on a database, search for **dm_os%counters** returns dm_os_memory_cache_counters and dm_os_performance_counters in that database.</span></span> <span data-ttu-id="94da1-175">オブジェクト エクスプローラーのフォーカスが [データベース] ノードにある場合は、すべてのデータベースが検索の対象となり、動的なビューの複数のインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="94da1-175">If the Object Explorer focus is on the Databases node, all databases are searched and multiple instances of the dynamic views are returned.</span></span>  
  
 <span data-ttu-id="94da1-176">大規模なセット</span><span class="sxs-lookup"><span data-stu-id="94da1-176">Large Sets</span></span>  
  
-   <span data-ttu-id="94da1-177">大規模なオブジェクト セットを検索した場合、処理に時間がかかったり、サーバーのパフォーマンスが低下したりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="94da1-177">Searching large object sets can take a long time and slow server performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94da1-178">参照</span><span class="sxs-lookup"><span data-stu-id="94da1-178">See Also</span></span>  
 <span data-ttu-id="94da1-179">[[オブジェクト エクスプローラー]](object-explorer.md)</span><span class="sxs-lookup"><span data-stu-id="94da1-179">[Object Explorer](object-explorer.md)</span></span>  
  
  
