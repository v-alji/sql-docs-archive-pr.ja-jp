---
title: '[ブレークポイント] ウィンドウ'
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Breakpoints Window [Transact-SQL]
ms.assetid: bad88d10-fdd5-4d3d-b5ea-a4f063847485
author: rothja
ms.author: jroth
ms.openlocfilehash: 077d501e581ed5baaac45cc6bbbb34e0040730e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643756"
---
# <a name="breakpoints-window"></a><span data-ttu-id="79cc0-102">[ブレークポイント] ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="79cc0-102">Breakpoints Window</span></span>
  <span data-ttu-id="79cc0-103">**[ブレークポイント]** ウィンドウには、現在の [!INCLUDE[ssDE](../../includes/ssde-md.md)] のクエリ エディターで設定されているすべてのブレークポイントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="79cc0-103">The **Breakpoints** window lists all the breakpoints that are set in the current [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span> <span data-ttu-id="79cc0-104">ブレークポイントを管理するには、 **[ブレークポイント]** ウィンドウのツール バーを使用します。</span><span class="sxs-lookup"><span data-stu-id="79cc0-104">To manage the breakpoints, use the toolbar in the **Breakpoints** window.</span></span> <span data-ttu-id="79cc0-105">ブレークポイントとは、デバッグ モードでコードの実行を一時停止する箇所で、デバッグ データを表示できます。</span><span class="sxs-lookup"><span data-stu-id="79cc0-105">Breakpoints are locations in the code where execution pauses in debug mode so that you can view debugging data.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="79cc0-106">タスク一覧</span><span class="sxs-lookup"><span data-stu-id="79cc0-106">Task List</span></span>  
 <span data-ttu-id="79cc0-107">**[ブレークポイント] ウィンドウにアクセスするには**</span><span class="sxs-lookup"><span data-stu-id="79cc0-107">**To access the Breakpoints window**</span></span>  
  
-   <span data-ttu-id="79cc0-108">**[デバッグ]** メニューの **[ウィンドウ]** をポイントし、 **[ブレークポイント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79cc0-108">On the **Debug** menu, click **Windows**, and then click **Breakpoints**.</span></span>  
  
## <a name="breakpoints-window-columns"></a><span data-ttu-id="79cc0-109">[ブレークポイント] ウィンドウの列</span><span class="sxs-lookup"><span data-stu-id="79cc0-109">Breakpoints Window Columns</span></span>  
 <span data-ttu-id="79cc0-110">既定では、 **[ブレークポイント]** ウィンドウには次の列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="79cc0-110">By default, the **Breakpoints** window lists the following columns.</span></span>  
  
 <span data-ttu-id="79cc0-111">**Name**</span><span class="sxs-lookup"><span data-stu-id="79cc0-111">**Name**</span></span>  
 <span data-ttu-id="79cc0-112">ブレークポイントの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="79cc0-112">Displays the name of the breakpoint.</span></span> <span data-ttu-id="79cc0-113">ブレークポイント名はデバッガーによって指定されます。</span><span class="sxs-lookup"><span data-stu-id="79cc0-113">Breakpoint names are provided by the debugger.</span></span> <span data-ttu-id="79cc0-114">この名前には、そのブレークポイントを含むデータベース エンジンのクエリ エディター ウィンドウの名前、およびそのブレークポイントが設定されているクエリ エディター内の行番号が含まれます。</span><span class="sxs-lookup"><span data-stu-id="79cc0-114">This name includes the name of Database Engine Query Editor window that contains the breakpoint, and the line number in the Query Editor on which the breakpoint is set.</span></span>  
  
 <span data-ttu-id="79cc0-115">**Condition**</span><span class="sxs-lookup"><span data-stu-id="79cc0-115">**Condition**</span></span>  
 <span data-ttu-id="79cc0-116">**[(条件なし)]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="79cc0-116">Displays **(no condition)**.</span></span> <span data-ttu-id="79cc0-117">[!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーは、ブレークポイント条件の設定をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="79cc0-117">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger does not support setting breakpoint conditions.</span></span>  
  
 <span data-ttu-id="79cc0-118">**[ヒット カウント]**</span><span class="sxs-lookup"><span data-stu-id="79cc0-118">**Hit Count**</span></span>  
 <span data-ttu-id="79cc0-119">**[breaks always (常に中断)]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="79cc0-119">Displays**breaks always**.</span></span>  
  
 <span data-ttu-id="79cc0-120">**[列]** ボックスの一覧で次の列を選択して、それらの列を追加したり、削除したりできます。</span><span class="sxs-lookup"><span data-stu-id="79cc0-120">You can add and remove the following columns by selecting them on the **Columns** list.</span></span>  
  
 <span data-ttu-id="79cc0-121">**Assert**</span><span class="sxs-lookup"><span data-stu-id="79cc0-121">**Filter**</span></span>  
 <span data-ttu-id="79cc0-122">**[(なし)]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="79cc0-122">Displays **(none)**.</span></span> <span data-ttu-id="79cc0-123">[!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーは、ブレークポイント フィルターの設定をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="79cc0-123">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger does not support setting breakpoint filters.</span></span>  
  
 <span data-ttu-id="79cc0-124">**[ヒット時]**</span><span class="sxs-lookup"><span data-stu-id="79cc0-124">**When Hit**</span></span>  
 <span data-ttu-id="79cc0-125">**[中断]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="79cc0-125">Displays **Break**.</span></span>  
  
 <span data-ttu-id="79cc0-126">**Language**</span><span class="sxs-lookup"><span data-stu-id="79cc0-126">**Language**</span></span>  
 <span data-ttu-id="79cc0-127">**を表す** [Transact-SQL] [!INCLUDE[tsql](../../includes/tsql-md.md)]が表示されます。</span><span class="sxs-lookup"><span data-stu-id="79cc0-127">Displays **Transact-SQL** for [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="79cc0-128">**Function**</span><span class="sxs-lookup"><span data-stu-id="79cc0-128">**Function**</span></span>  
 <span data-ttu-id="79cc0-129">ブレークポイントが設定されている行番号が表示されます。</span><span class="sxs-lookup"><span data-stu-id="79cc0-129">Displays the number of the line on which the breakpoint is set.</span></span>  
  
 <span data-ttu-id="79cc0-130">**[最近使ったファイル]**</span><span class="sxs-lookup"><span data-stu-id="79cc0-130">**File**</span></span>  
 <span data-ttu-id="79cc0-131">ブレークポイントを含むソース ファイルの名前、およびブレークポイントが設定されている行番号が表示されます。</span><span class="sxs-lookup"><span data-stu-id="79cc0-131">Displays the name of the source file that contains the breakpoint, and the number of the line on which the breakpoint is set.</span></span>  
  
 <span data-ttu-id="79cc0-132">**アドレス**</span><span class="sxs-lookup"><span data-stu-id="79cc0-132">**Address**</span></span>  
 <span data-ttu-id="79cc0-133">[!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーはこの機能をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="79cc0-133">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger does not support this feature.</span></span>  
  
 <span data-ttu-id="79cc0-134">**[処理]**</span><span class="sxs-lookup"><span data-stu-id="79cc0-134">**Process**</span></span>  
 <span data-ttu-id="79cc0-135">**プロセスであることを示す** [SQL] [!INCLUDE[ssDE](../../includes/ssde-md.md)] が表示されます。</span><span class="sxs-lookup"><span data-stu-id="79cc0-135">Displays **[SQL]** to indicate that this is a [!INCLUDE[ssDE](../../includes/ssde-md.md)] process.</span></span> <span data-ttu-id="79cc0-136">この後に、コードが実行される [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="79cc0-136">This is followed by the name of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in which the code executes.</span></span>  
  
## <a name="breakpoints-window-toolbar"></a><span data-ttu-id="79cc0-137">[ブレークポイント] ウィンドウのツール バー</span><span class="sxs-lookup"><span data-stu-id="79cc0-137">Breakpoints Window Toolbar</span></span>  
 <span data-ttu-id="79cc0-138">現在の [!INCLUDE[ssDE](../../includes/ssde-md.md)] のクエリ エディター ウィンドウにアクティブなブレークポイントがある場合、それらのブレークポイントの管理に使用できるツール バーが **[ブレークポイント]** ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="79cc0-138">When the current [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window has active breakpoints, the **Breakpoints** window displays a toolbar that can be used to manage the breakpoints.</span></span>  
  
 <span data-ttu-id="79cc0-139">**削除**</span><span class="sxs-lookup"><span data-stu-id="79cc0-139">**Delete**</span></span>  
 <span data-ttu-id="79cc0-140">選択したブレークポイントを削除します。</span><span class="sxs-lookup"><span data-stu-id="79cc0-140">Deletes the selected breakpoint.</span></span>  
  
 <span data-ttu-id="79cc0-141">**[すべてのブレークポイントの削除]**</span><span class="sxs-lookup"><span data-stu-id="79cc0-141">**Delete All Breakpoints**</span></span>  
 <span data-ttu-id="79cc0-142">**[ブレークポイント]** ウィンドウに表示されているすべてのブレークポイントを削除します。</span><span class="sxs-lookup"><span data-stu-id="79cc0-142">Deletes all breakpoints that are displayed in the **Breakpoints** window.</span></span>  
  
 <span data-ttu-id="79cc0-143">**[すべてのブレークポイントを無効にする]**</span><span class="sxs-lookup"><span data-stu-id="79cc0-143">**Disable All Breakpoints**</span></span>  
 <span data-ttu-id="79cc0-144">すべてのブレークポイントを無効にして、コードの実行が停止されなくなるようにします。ただし、ブレークポイントは削除されません。</span><span class="sxs-lookup"><span data-stu-id="79cc0-144">Disables all breakpoints so that they no longer stop code execution; however, the breakpoints remain.</span></span> <span data-ttu-id="79cc0-145">すべてのブレークポイントを無効にすると、このボタンは **[すべてのブレークポイントを有効にする]** になります。</span><span class="sxs-lookup"><span data-stu-id="79cc0-145">When all the breakpoints are disabled, this button becomes **Enable All Breakpoints**.</span></span>  
  
 <span data-ttu-id="79cc0-146">**[すべてのブレークポイントを有効にする]**</span><span class="sxs-lookup"><span data-stu-id="79cc0-146">**Enable All Breakpoints**</span></span>  
 <span data-ttu-id="79cc0-147">すべてのブレークポイントを有効にして、コードの実行が停止されるようにします。</span><span class="sxs-lookup"><span data-stu-id="79cc0-147">Enables all breakpoints so that they stop code execution.</span></span> <span data-ttu-id="79cc0-148">すべてのブレークポイントを有効にすると、このボタンは **[すべてのブレークポイントを無効にする]** になります。</span><span class="sxs-lookup"><span data-stu-id="79cc0-148">When all breakpoints are enabled, this button becomes **Disable All Breakpoints**.</span></span>  
  
 <span data-ttu-id="79cc0-149">**[ソース コードへ移動]**</span><span class="sxs-lookup"><span data-stu-id="79cc0-149">**Go To Source Code**</span></span>  
 <span data-ttu-id="79cc0-150">選択したブレークポイントを含むクエリ エディター内の行にカーソルを移動します。</span><span class="sxs-lookup"><span data-stu-id="79cc0-150">Positions the cursor on the line in the Query Editor that contains the selected breakpoint.</span></span>  
  
 <span data-ttu-id="79cc0-151">**[列]**</span><span class="sxs-lookup"><span data-stu-id="79cc0-151">**Columns**</span></span>  
 <span data-ttu-id="79cc0-152">**[ブレークポイント]** ウィンドウで表示できるすべての列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="79cc0-152">Lists all the columns that can be displayed in the **Breakpoints** window.</span></span> <span data-ttu-id="79cc0-153">チェック ボックスによって、表示される列を指定します。</span><span class="sxs-lookup"><span data-stu-id="79cc0-153">A check box indicates the columns that are displayed.</span></span> <span data-ttu-id="79cc0-154">**[ブレークポイント]** ウィンドウの列を追加または削除するには、一覧でその列を選択します。</span><span class="sxs-lookup"><span data-stu-id="79cc0-154">To add or remove a column in the **Breakpoints** window, select the column on the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79cc0-155">参照</span><span class="sxs-lookup"><span data-stu-id="79cc0-155">See Also</span></span>  
 [<span data-ttu-id="79cc0-156">Transact-SQL デバッガー</span><span class="sxs-lookup"><span data-stu-id="79cc0-156">Transact-SQL Debugger</span></span>](transact-sql-debugger.md)  
