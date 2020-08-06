---
title: ブレークポイントの有効化、無効化、および削除
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 357b5874-273f-43a9-8e30-83872bdea5dc
author: rothja
ms.author: jroth
ms.openlocfilehash: 17e83c6488b9d9026fb78e5fb8f50e22533fa61e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644987"
---
# <a name="enable-disable-and-delete-breakpoints"></a><span data-ttu-id="a46aa-102">ブレークポイントの有効化、無効化、および削除</span><span class="sxs-lookup"><span data-stu-id="a46aa-102">Enable, Disable, and Delete Breakpoints</span></span>
  <span data-ttu-id="a46aa-103">開かれているすべてのブレークポイントを表示および管理するには、 **[ブレークポイント]** ウィンドウを使用します。</span><span class="sxs-lookup"><span data-stu-id="a46aa-103">To view and manage all the open breakpoints, you can use the **Breakpoints** window.</span></span> <span data-ttu-id="a46aa-104">ブレークポイントの情報を表示し、各種の操作 (ブレークポイントの削除、無効化、有効化など) を実行するには、このウィンドウを使用します。</span><span class="sxs-lookup"><span data-stu-id="a46aa-104">Use the window to view breakpoint information and to take actions such as deleting, disabling, or enabling breakpoints.</span></span>  
  
## <a name="the-breakpoints-window"></a><span data-ttu-id="a46aa-105">[ブレークポイント] ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="a46aa-105">The Breakpoints Window</span></span>  
 <span data-ttu-id="a46aa-106">**[ブレークポイント]** ウィンドウには、ブレークポイントが設定されているコード行などの情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a46aa-106">The **Breakpoints** window lists information such as which line of code the breakpoint is located on.</span></span> <span data-ttu-id="a46aa-107">**[ブレークポイント]** ウィンドウでは、ブレークポイントの削除、無効化、および有効化を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="a46aa-107">In the **Breakpoints** window, you can also delete, disable, and enable breakpoints.</span></span> <span data-ttu-id="a46aa-108">**[ブレークポイント]** ウィンドウの詳細については、「 [[ブレークポイント] Window](transact-sql-debugger-breakpoints-window.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a46aa-108">For more information about the **Breakpoints** window, see [Breakpoints Window](transact-sql-debugger-breakpoints-window.md)</span></span>  
  
 <span data-ttu-id="a46aa-109">ブレークポイントを無効化した場合、そのブレークポイントで実行は一時停止されませんが、後でブレークポイントを有効化できるように、定義がその位置に保持されます。</span><span class="sxs-lookup"><span data-stu-id="a46aa-109">Disabling a breakpoint prevents it from pausing execution, but leaves the definition in place in case you want to enable the breakpoint later.</span></span> <span data-ttu-id="a46aa-110">削除したブレークポイントは完全に削除されます。</span><span class="sxs-lookup"><span data-stu-id="a46aa-110">Deleting a breakpoint removes it permanently.</span></span> <span data-ttu-id="a46aa-111">そのステートメントで実行を一時停止するには、新たにブレークポイントを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a46aa-111">You must toggle a new breakpoint to pause execution on the statement.</span></span>  
  
## <a name="to-open-the-breakpoints-window"></a><span data-ttu-id="a46aa-112">[ブレークポイント] ウィンドウを開くには</span><span class="sxs-lookup"><span data-stu-id="a46aa-112">To Open the Breakpoints Window</span></span>  
 <span data-ttu-id="a46aa-113">**To open the Breakpoints window**</span><span class="sxs-lookup"><span data-stu-id="a46aa-113">**To open the Breakpoints window**</span></span>  
  
 <span data-ttu-id="a46aa-114">**[ブレークポイント]** ウィンドウを開くには、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="a46aa-114">You can open the **Breakpoints** window in one of the following ways:</span></span>  
  
-   <span data-ttu-id="a46aa-115">**[デバッグ]** メニューの **[ウィンドウ]** をポイントし、 **[ブレークポイント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a46aa-115">On the **Debug** menu, click **Windows**, and then click **Breakpoints**.</span></span>  
  
-   <span data-ttu-id="a46aa-116">**[デバッグ]** ツール バーの **[ブレークポイント]** ボタンをクリックする。</span><span class="sxs-lookup"><span data-stu-id="a46aa-116">On the **Debug** toolbar, click the **Breakpoints** button.</span></span>  
  
-   <span data-ttu-id="a46aa-117">Ctrl + Alt + B キーを押す。</span><span class="sxs-lookup"><span data-stu-id="a46aa-117">Press CTRL+ALT+B.</span></span>  
  
## <a name="to-disable-a-single-breakpoint"></a><span data-ttu-id="a46aa-118">単一のブレークポイントを無効にするには</span><span class="sxs-lookup"><span data-stu-id="a46aa-118">To Disable a Single Breakpoint</span></span>  
 <span data-ttu-id="a46aa-119">**To disable a single breakpoint**</span><span class="sxs-lookup"><span data-stu-id="a46aa-119">**To disable a single breakpoint**</span></span>  
  
 <span data-ttu-id="a46aa-120">単一のブレークポイントを無効にするには、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="a46aa-120">You can disable a single breakpoint in one of the following ways:</span></span>  
  
-   <span data-ttu-id="a46aa-121">クエリ エディター ウィンドウで、ブレークポイントを右クリックし、 **[ブレークポイントの無効化]** をクリックする。</span><span class="sxs-lookup"><span data-stu-id="a46aa-121">In the Query Editor window, right-click the breakpoint, and then click **Disable Breakpoint**.</span></span>  
  
-   <span data-ttu-id="a46aa-122">[ブレークポイント] ウィンドウで、ブレークポイントの左側のチェック ボックスをオフにする。</span><span class="sxs-lookup"><span data-stu-id="a46aa-122">In the Breakpoints window, clear the check box to the left of the breakpoint.</span></span>  
  
## <a name="to-disable-all-breakpoints"></a><span data-ttu-id="a46aa-123">すべてのブレークポイントを無効にするには</span><span class="sxs-lookup"><span data-stu-id="a46aa-123">To Disable All Breakpoints</span></span>  
 <span data-ttu-id="a46aa-124">**To disable all breakpoints**</span><span class="sxs-lookup"><span data-stu-id="a46aa-124">**To disable all breakpoints**</span></span>  
  
 <span data-ttu-id="a46aa-125">すべてのブレークポイントを無効にするには、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="a46aa-125">You can disable all breakpoints in one of the following ways:</span></span>  
  
-   <span data-ttu-id="a46aa-126">**[デバッグ]** メニューの **[すべてのブレークポイントを無効にする]** をクリックする。</span><span class="sxs-lookup"><span data-stu-id="a46aa-126">On the **Debug** menu, click **Disable All Breakpoints**.</span></span>  
  
-   <span data-ttu-id="a46aa-127">**[ブレークポイント]** ウィンドウのツール バーの **[すべてのブレークポイントを無効にする]** ボタンをクリックする。</span><span class="sxs-lookup"><span data-stu-id="a46aa-127">On the toolbar of the **Breakpoints** window, click the **Disable All Breakpoints** button.</span></span>  
  
## <a name="to-enable-a-single-breakpoint"></a><span data-ttu-id="a46aa-128">単一のブレークポイントを有効にするには</span><span class="sxs-lookup"><span data-stu-id="a46aa-128">To Enable a Single Breakpoint</span></span>  
 <span data-ttu-id="a46aa-129">**To enable a single breakpoint**</span><span class="sxs-lookup"><span data-stu-id="a46aa-129">**To enable a single breakpoint**</span></span>  
  
 <span data-ttu-id="a46aa-130">単一のブレークポイントを有効にするには、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="a46aa-130">You can enable a single breakpoint in one of the following ways:</span></span>  
  
-   <span data-ttu-id="a46aa-131">クエリ エディター ウィンドウで、ブレークポイントを右クリックし、 **[ブレークポイントの有効化]** をクリックする。</span><span class="sxs-lookup"><span data-stu-id="a46aa-131">In the Query Editor window, right-click the breakpoint, and then click **Enable Breakpoint**.</span></span>  
  
-   <span data-ttu-id="a46aa-132">[ブレークポイント] ウィンドウで、ブレークポイントの左側のボックスをオンにする。</span><span class="sxs-lookup"><span data-stu-id="a46aa-132">In the Breakpoints window, click the box to the left of the breakpoint.</span></span>  
  
## <a name="to-enable-all-breakpoints"></a><span data-ttu-id="a46aa-133">すべてのブレークポイントを有効にするには</span><span class="sxs-lookup"><span data-stu-id="a46aa-133">To Enable All Breakpoints</span></span>  
 <span data-ttu-id="a46aa-134">**To enable all breakpoints**</span><span class="sxs-lookup"><span data-stu-id="a46aa-134">**To enable all breakpoints**</span></span>  
  
 <span data-ttu-id="a46aa-135">すべてのブレークポイントを有効にするには、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="a46aa-135">You can enable all breakpoints in one of the following ways:</span></span>  
  
-   <span data-ttu-id="a46aa-136">**[デバッグ]** メニューの **[すべてのブレークポイントを有効にする]** をクリックする。</span><span class="sxs-lookup"><span data-stu-id="a46aa-136">On the **Debug** menu, click **Enable All Breakpoints**.</span></span>  
  
-   <span data-ttu-id="a46aa-137">**[ブレークポイント]** ウィンドウのツール バーの **[すべてのブレークポイントを有効にする]** ボタンをクリックする。</span><span class="sxs-lookup"><span data-stu-id="a46aa-137">On the toolbar of the **Breakpoints** window, click the **Enable All Breakpoints** button.</span></span>  
  
## <a name="to-delete-a-single-breakpoint"></a><span data-ttu-id="a46aa-138">単一のブレークポイントを削除するには</span><span class="sxs-lookup"><span data-stu-id="a46aa-138">To Delete a Single Breakpoint</span></span>  
 <span data-ttu-id="a46aa-139">**To delete a single breakpoint**</span><span class="sxs-lookup"><span data-stu-id="a46aa-139">**To delete a single breakpoint**</span></span>  
  
 <span data-ttu-id="a46aa-140">単一のブレークポイントを削除するには、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="a46aa-140">You can delete a single breakpoint in one of the following ways:</span></span>  
  
-   <span data-ttu-id="a46aa-141">クエリ エディター ウィンドウで、ブレークポイントを右クリックし、 **[ブレークポイントの削除]** をクリックする。</span><span class="sxs-lookup"><span data-stu-id="a46aa-141">In the Query Editor window, right-click the breakpoint, and then click **Delete Breakpoint**.</span></span>  
  
-   <span data-ttu-id="a46aa-142">[ブレークポイント] ウィンドウで、ブレークポイントを右クリックし、ショートカット メニューの **[削除]** をクリックする。</span><span class="sxs-lookup"><span data-stu-id="a46aa-142">In the Breakpoints window, right-click the breakpoint, and then click **Delete** on the shortcut menu.</span></span>  
  
-   <span data-ttu-id="a46aa-143">[ブレークポイント] ウィンドウで、ブレークポイントを選択し、Del キーを押す。</span><span class="sxs-lookup"><span data-stu-id="a46aa-143">In the Breakpoints window, select the breakpoint, and then press DELETE.</span></span>  
  
## <a name="to-delete-all-breakpoints"></a><span data-ttu-id="a46aa-144">すべてのブレークポイントを削除するには</span><span class="sxs-lookup"><span data-stu-id="a46aa-144">To Delete All Breakpoints</span></span>  
 <span data-ttu-id="a46aa-145">**To delete all breakpoints**</span><span class="sxs-lookup"><span data-stu-id="a46aa-145">**To delete all breakpoints**</span></span>  
  
 <span data-ttu-id="a46aa-146">すべてのブレークポイントを削除するには、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="a46aa-146">You can delete all breakpoints in one of the following ways:</span></span>  
  
-   <span data-ttu-id="a46aa-147">**[デバッグ]** メニューの **[すべてのブレークポイントの削除]** をクリックする。</span><span class="sxs-lookup"><span data-stu-id="a46aa-147">On the **Debug** menu, cllick **Delete All Breakpoints**.</span></span>  
  
-   <span data-ttu-id="a46aa-148">**[ブレークポイント]** ウィンドウのツール バーの **[すべてのブレークポイントの削除]** ボタンをクリックする。</span><span class="sxs-lookup"><span data-stu-id="a46aa-148">On the toolbar of the **Breakpoints** window, click the **Delete All Breakpoints** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a46aa-149">参照</span><span class="sxs-lookup"><span data-stu-id="a46aa-149">See Also</span></span>  
 [<span data-ttu-id="a46aa-150">ブレークポイントの切り替え</span><span class="sxs-lookup"><span data-stu-id="a46aa-150">Toggle a Breakpoint</span></span>](../spatial/point.md)  
  
  
