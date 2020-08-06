---
title: ヒット カウントの指定
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpt.hitcount
helpviewer_keywords:
- Transact-SQL debugger, breakpoint hit count
ms.assetid: 24836939-94ed-4e57-aa85-5d6938d859e4
author: rothja
ms.author: jroth
ms.openlocfilehash: 34c75e990bce1ea5e64c0b45f7acbcaa52fc3c40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643230"
---
# <a name="specify-a-hit-count"></a><span data-ttu-id="aa94e-102">ヒット カウントの指定</span><span class="sxs-lookup"><span data-stu-id="aa94e-102">Specify a Hit Count</span></span>
  <span data-ttu-id="aa94e-103">ブレークポイントのヒット カウントは、ブレークポイントに達するたびに [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーによって増加されるカウンターです。</span><span class="sxs-lookup"><span data-stu-id="aa94e-103">A breakpoint hit count is a counter that is incremented by the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger each time the breakpoint is reached.</span></span> <span data-ttu-id="aa94e-104">指定したヒット カウントに達し、指定したブレークポイントの条件が満たされると、ブレークポイントに指定されたアクションがデバッガーによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="aa94e-104">If the specified hit count is reached and any specified breakpoint condition is satisfied, the debugger performs the action specified for the breakpoint.</span></span>  
  
## <a name="hit-count-considerations"></a><span data-ttu-id="aa94e-105">ヒット カウントの考慮事項</span><span class="sxs-lookup"><span data-stu-id="aa94e-105">Hit Count Considerations</span></span>  
 <span data-ttu-id="aa94e-106">既定では、ブレークポイントにヒットするたびに、実行が中断します。</span><span class="sxs-lookup"><span data-stu-id="aa94e-106">By default, execution breaks every time a breakpoint is hit.</span></span> <span data-ttu-id="aa94e-107">次のオプションのいずれかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="aa94e-107">You can choose between the following options:</span></span>  
  
-   <span data-ttu-id="aa94e-108">常に中断する (既定)。</span><span class="sxs-lookup"><span data-stu-id="aa94e-108">Break always (the default).</span></span>  
  
-   <span data-ttu-id="aa94e-109">ヒット カウントが指定した値と等しくなったときに中断する。</span><span class="sxs-lookup"><span data-stu-id="aa94e-109">Break when the hit count equals a specified value.</span></span>  
  
-   <span data-ttu-id="aa94e-110">ヒット カウントが指定した値の倍数と等しくなったときに中断する。</span><span class="sxs-lookup"><span data-stu-id="aa94e-110">Break when the hit count equals a multiple of a specified value.</span></span>  
  
-   <span data-ttu-id="aa94e-111">ヒット カウントが指定した値以上になったときに中断する。</span><span class="sxs-lookup"><span data-stu-id="aa94e-111">Break when the hit count is greater than or equal to a specified value.</span></span>  
  
 <span data-ttu-id="aa94e-112">ブレークポイントのヒット カウントは、デバッグ セッションのスコープ内で増加します。</span><span class="sxs-lookup"><span data-stu-id="aa94e-112">Breakpoint hit counts are incremented within the scope of a debugging session.</span></span> <span data-ttu-id="aa94e-113">すべてのヒット カウントは各デバッグ セッションの開始時に 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="aa94e-113">All hit counts are set to zero at the start of each debugging session.</span></span>  
  
 <span data-ttu-id="aa94e-114">ブレークポイントで実行を中断せずに、ブレークポイントにヒットした回数を追跡する場合は、ヒット カウントに非常に大きい値を指定して、ブレークポイントで中断しないようにします。</span><span class="sxs-lookup"><span data-stu-id="aa94e-114">If you want to track how many times a breakpoint is hit without having the breakpoint break execution, specify a hit count with a very high value so the breakpoint never breaks.</span></span>  
  
 <span data-ttu-id="aa94e-115">ブレークポイントの既定のアクションでは、ヒット カウントとブレークポイントの条件の両方が満たされたときに、実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="aa94e-115">The default action for a breakpoint is to break execution when both the hit count and breakpoint condition have been satisfied.</span></span> <span data-ttu-id="aa94e-116">他のアクションを指定する方法の詳細については、「 [ブレークポイント アクションの指定](specify-a-breakpoint-action.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa94e-116">For information about specifying other actions, see [Specify a Breakpoint Action](specify-a-breakpoint-action.md).</span></span>  
  
#### <a name="to-specify-a-hit-count"></a><span data-ttu-id="aa94e-117">ヒット カウントを指定するには</span><span class="sxs-lookup"><span data-stu-id="aa94e-117">To Specify a Hit Count</span></span>  
  
1.  <span data-ttu-id="aa94e-118">エディター ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[ヒット カウント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aa94e-118">In the editor window, right-click the breakpoint glyph, and then click **Hit Count** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="aa94e-119">または</span><span class="sxs-lookup"><span data-stu-id="aa94e-119">-or-</span></span>  
  
     <span data-ttu-id="aa94e-120">**[ブレークポイント]** ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[ヒット カウント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aa94e-120">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **Hit Count** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="aa94e-121">**[ブレークポイントのヒット カウント]** ダイアログ ボックスで、 **[ブレークポイントをヒットした時]** ボックスから目的の動作を選択します。</span><span class="sxs-lookup"><span data-stu-id="aa94e-121">In the **Breakpoint Hit Count** dialog box, select the behavior you want from the **When the breakpoint is hit** box.</span></span>  
  
     <span data-ttu-id="aa94e-122">**[常に中断]** 以外の設定を選択すると、一覧の右側にテキスト ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa94e-122">If you choose any setting other than **Break Always**, a text box appears to the right of the list.</span></span> <span data-ttu-id="aa94e-123">テキスト ボックスに整数を入力して、目的のヒット カウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="aa94e-123">Enter an integer in the text box to specify the hit count you want.</span></span>  
  
3.  <span data-ttu-id="aa94e-124">**[OK]** をクリックして変更を適用するか、 **[キャンセル]** をクリックして変更を適用せずに終了します。</span><span class="sxs-lookup"><span data-stu-id="aa94e-124">Click **OK** to implement the changes, or **Cancel** to exit without applying the changes.</span></span>  
  
#### <a name="to-view-or-reset-the-current-hit-count"></a><span data-ttu-id="aa94e-125">現在のヒット カウントを表示またはリセットするには</span><span class="sxs-lookup"><span data-stu-id="aa94e-125">To View or Reset the Current Hit Count</span></span>  
  
1.  <span data-ttu-id="aa94e-126">エディター ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[ヒット カウント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aa94e-126">In the editor window, right-click the breakpoint glyph, and then click **Hit Count** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="aa94e-127">または</span><span class="sxs-lookup"><span data-stu-id="aa94e-127">-or-</span></span>  
  
     <span data-ttu-id="aa94e-128">**[ブレークポイント]** ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[ヒット カウント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aa94e-128">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **Hit Count** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="aa94e-129">**[ブレークポイントのヒット カウント]** ダイアログ ボックスの **[リセット]** ボタンのすぐ上に、 **[現在のヒット カウント]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa94e-129">In the **Breakpoint Hit Count** dialog box, the **Current hit count:** is displayed just above the **Reset** button.</span></span>  
  
3.  <span data-ttu-id="aa94e-130">現在のヒット カウントを 0 に設定する場合は、 **[リセット]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aa94e-130">Click **Reset** if you want to set the current hit count to zero.</span></span>  
  
4.  <span data-ttu-id="aa94e-131">**[OK]** または **[キャンセル]** をクリックして、ダイアログ ボックスを終了します。</span><span class="sxs-lookup"><span data-stu-id="aa94e-131">Click **OK** or **Cancel** to exit the dialog.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa94e-132">参照</span><span class="sxs-lookup"><span data-stu-id="aa94e-132">See Also</span></span>  
 [<span data-ttu-id="aa94e-133">ブレークポイント条件の指定</span><span class="sxs-lookup"><span data-stu-id="aa94e-133">Specify a Breakpoint Condition</span></span>](specify-a-breakpoint-condition.md)  
  
  
