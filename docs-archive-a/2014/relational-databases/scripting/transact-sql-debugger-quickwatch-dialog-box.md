---
title: '[クイック ウォッチ] ダイアログ ボックス'
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- vs.debug.quickwatch
helpviewer_keywords:
- QuickWatch Dialog [Transact-SQL]
ms.assetid: d6bbb373-1452-41f2-bdc5-86ae689c3dc0
author: rothja
ms.author: jroth
ms.openlocfilehash: 48e4bda558b75bec0c81815c90feff9d6500a803
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644963"
---
# <a name="quickwatch-dialog-box"></a><span data-ttu-id="e279d-102">[クイック ウォッチ] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="e279d-102">QuickWatch Dialog Box</span></span>
  <span data-ttu-id="e279d-103">**コードのデバッグ時に** [クイック ウォッチ] [!INCLUDE[tsql](../../includes/tsql-md.md)] ダイアログ ボックスを使用すると、変数やパラメーターなど、1 つの [!INCLUDE[tsql](../../includes/tsql-md.md)] 式のデータ型や値をすばやく表示できます。</span><span class="sxs-lookup"><span data-stu-id="e279d-103">Use the **QuickWatch** dialog box to quickly view the data type and value of one [!INCLUDE[tsql](../../includes/tsql-md.md)] expression, such as a variable or parameter, when you are debugging [!INCLUDE[tsql](../../includes/tsql-md.md)] code.</span></span> <span data-ttu-id="e279d-104">複数の式を確認するために、 **[ウォッチ]** ウィンドウに式を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="e279d-104">To watch multiple expressions, you can also add the expression to a **Watch** window.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="e279d-105">タスク一覧</span><span class="sxs-lookup"><span data-stu-id="e279d-105">Task List</span></span>  
 <span data-ttu-id="e279d-106">**[クイック ウォッチ] ダイアログ ボックスにアクセスするには**</span><span class="sxs-lookup"><span data-stu-id="e279d-106">**To access the QuickWatch dialog box**</span></span>  
  
-   <span data-ttu-id="e279d-107">**[デバッグ]** メニューの **[クイック ウォッチ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e279d-107">On the **Debug** menu, click **QuickWatch**.</span></span>  
  
 <span data-ttu-id="e279d-108">**式に関する情報を表示するには**</span><span class="sxs-lookup"><span data-stu-id="e279d-108">**To view the information about an expression**</span></span>  
  
1.  <span data-ttu-id="e279d-109">**[式]** ボックスで、目的の式を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="e279d-109">In the **Expression** list box, type or select the expression that you want.</span></span> <span data-ttu-id="e279d-110">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] 式がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e279d-110">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] expressions are supported:</span></span>  
  
    -   <span data-ttu-id="e279d-111">変数。</span><span class="sxs-lookup"><span data-stu-id="e279d-111">Variables.</span></span>  
  
    -   <span data-ttu-id="e279d-112">パラメーター。</span><span class="sxs-lookup"><span data-stu-id="e279d-112">Parameters.</span></span>  
  
    -   <span data-ttu-id="e279d-113">名前が @@ で始まるシステム関数。</span><span class="sxs-lookup"><span data-stu-id="e279d-113">System functions whose name starts with @@.</span></span>  
  
    -   <span data-ttu-id="e279d-114">1 つまたは複数の変数、パラメーター、またはシステム関数に演算子を適用して作成された式 (@IntegerCounter + 1、FirstName + LastName など)。</span><span class="sxs-lookup"><span data-stu-id="e279d-114">Expressions built by applying operators to one or more variables, parameters, or system functions, such as @IntegerCounter + 1, or FirstName + LastName.</span></span>  
  
    -   <span data-ttu-id="e279d-115">単一の値を返す Transact-SQL ステートメント (SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1 など)。</span><span class="sxs-lookup"><span data-stu-id="e279d-115">Transact-SQL statements that return a single value, such as: SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1.</span></span>  
  
2.  <span data-ttu-id="e279d-116">**[再評価]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e279d-116">Click **Reevaluate**.</span></span>  
  
 <span data-ttu-id="e279d-117">**[ウォッチ] ウィンドウにクイック ウォッチの式を追加するには**</span><span class="sxs-lookup"><span data-stu-id="e279d-117">**To add the QuickWatch expression to a Watch window**</span></span>  
  
-   <span data-ttu-id="e279d-118">**[ウォッチ式の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e279d-118">Click **Add Watch**.</span></span>  
  
 <span data-ttu-id="e279d-119">**クイック ウォッチの式の値を変更するには**</span><span class="sxs-lookup"><span data-stu-id="e279d-119">**To change the value of the QuickWatch expression**</span></span>  
  
-   <span data-ttu-id="e279d-120">式を右クリックし、 **[値の編集]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e279d-120">Right-click the expression, and then select **Edit Value**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e279d-121">オプション</span><span class="sxs-lookup"><span data-stu-id="e279d-121">Options</span></span>  
 <span data-ttu-id="e279d-122">**[式の一覧]**</span><span class="sxs-lookup"><span data-stu-id="e279d-122">**Expression list**</span></span>  
 <span data-ttu-id="e279d-123">現在選択されている式を表示します。</span><span class="sxs-lookup"><span data-stu-id="e279d-123">Displays the currently selected expression.</span></span> <span data-ttu-id="e279d-124">このドロップダウン リストには、選択して表示できる式のセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e279d-124">The drop-down list contains a set of expressions that you can select to display.</span></span> <span data-ttu-id="e279d-125">一覧の式は、 **[呼び出し履歴]** ウィンドウで現在選択されているスタック フレームのスコープで使用できる式です。</span><span class="sxs-lookup"><span data-stu-id="e279d-125">The expressions in the list are those available in the scope of the stack frame that is currently selected in the **Call Stack** window.</span></span> <span data-ttu-id="e279d-126">別の式を表示するには、式を入力するか、一覧から式を選択します。</span><span class="sxs-lookup"><span data-stu-id="e279d-126">To display a different expression, either enter the expression or select it from list.</span></span> <span data-ttu-id="e279d-127">[!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーでは、変数、パラメーター、および名前が @@ で始まるシステム関数の式がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e279d-127">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger supports the following expressions: variables, parameters, and the system functions that have names that start with @@.</span></span>  
  
 <span data-ttu-id="e279d-128">**[値グリッド]**</span><span class="sxs-lookup"><span data-stu-id="e279d-128">**Value grid**</span></span>  
 <span data-ttu-id="e279d-129">現在監視されている式のプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="e279d-129">Displays the properties of the expression that is currently being watched.</span></span>  
  
 <span data-ttu-id="e279d-130">**Name**</span><span class="sxs-lookup"><span data-stu-id="e279d-130">**Name**</span></span>  
 <span data-ttu-id="e279d-131">監視対象の [!INCLUDE[tsql](../../includes/tsql-md.md)] 式です。</span><span class="sxs-lookup"><span data-stu-id="e279d-131">Is the [!INCLUDE[tsql](../../includes/tsql-md.md)] expression being watched.</span></span>  
  
 <span data-ttu-id="e279d-132">**Value**</span><span class="sxs-lookup"><span data-stu-id="e279d-132">**Value**</span></span>  
 <span data-ttu-id="e279d-133">式に現在割り当てられている値を表示します。</span><span class="sxs-lookup"><span data-stu-id="e279d-133">Displays the value that is currently assigned to the expression.</span></span> <span data-ttu-id="e279d-134">式に現在値がない場合は、空白になります。</span><span class="sxs-lookup"><span data-stu-id="e279d-134">A blank is displayed when the expression currently has no value.</span></span>  
  
 <span data-ttu-id="e279d-135">式の長さが **[値]** 列の幅よりも長い場合は、その式の **[値]** セルにポインターを移動するとツールヒントに完全な値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e279d-135">If the length of an expression is larger than the width of the **Value** column, a tooltip displays the full value when you move the pointer over the **Value** cell for that expression.</span></span>  
  
 <span data-ttu-id="e279d-136">**[値]** セルの虫眼鏡アイコンは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガー ビジュアライザーが使用可能であることを示します。</span><span class="sxs-lookup"><span data-stu-id="e279d-136">A magnifying glass icon in a **Value** cell indicates that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger visualizer is available.</span></span> <span data-ttu-id="e279d-137">一覧では、 **[テキスト ビジュアライザー]** 、 **[XML ビジュアライザー]** 、または **[HTML ビジュアライザー]** を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e279d-137">In the list, you can specify **Text Visualizer**, **XML Visualizer**, or **HTML Visualizer**.</span></span> <span data-ttu-id="e279d-138">デバッガー ビジュアライザーを開始するには、虫眼鏡アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e279d-138">To start a debugger visualizer, click the magnifying glass icon.</span></span> <span data-ttu-id="e279d-139">[!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーによりダイアログ ボックスが開き、データがそのデータ型に適した形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="e279d-139">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger opens a dialog box that displays the data in a format appropriate to the data type.</span></span>  
  
 <span data-ttu-id="e279d-140">**Type**</span><span class="sxs-lookup"><span data-stu-id="e279d-140">**Type**</span></span>  
 <span data-ttu-id="e279d-141">式のデータ型を表示します。</span><span class="sxs-lookup"><span data-stu-id="e279d-141">Displays the data type of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e279d-142">参照</span><span class="sxs-lookup"><span data-stu-id="e279d-142">See Also</span></span>  
 <span data-ttu-id="e279d-143">[Transact-SQL デバッガー](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="e279d-143">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="e279d-144">[Transact-SQL デバッガー情報](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="e279d-144">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 <span data-ttu-id="e279d-145">[[ウォッチ] ウィンドウ](transact-sql-debugger-watch-window.md) </span><span class="sxs-lookup"><span data-stu-id="e279d-145">[Watch Window](transact-sql-debugger-watch-window.md) </span></span>  
 <span data-ttu-id="e279d-146">[[ローカル] ウィンドウ](transact-sql-debugger-locals-window.md) </span><span class="sxs-lookup"><span data-stu-id="e279d-146">[Locals Window](transact-sql-debugger-locals-window.md) </span></span>  
 <span data-ttu-id="e279d-147">[[呼び出し履歴] ウィンドウ](transact-sql-debugger-call-stack-window.md) </span><span class="sxs-lookup"><span data-stu-id="e279d-147">[Call Stack Window](transact-sql-debugger-call-stack-window.md) </span></span>  
 [<span data-ttu-id="e279d-148">式 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e279d-148">Expressions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/expressions-transact-sql)  
  
  
