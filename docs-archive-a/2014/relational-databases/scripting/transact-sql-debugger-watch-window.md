---
title: '[ウォッチ] ウィンドウ'
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Watch Window [Transact-SQL]
ms.assetid: 23f3baa4-14c2-4262-92f7-3f43fcfa0436
author: rothja
ms.author: jroth
ms.openlocfilehash: c2a3db9b095902fcb5620af91fb86d80f773d606
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643223"
---
# <a name="watch-window"></a><span data-ttu-id="6a0c0-102">[ウォッチ] ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="6a0c0-102">Watch Window</span></span>
  <span data-ttu-id="6a0c0-103">**[ウォッチ]** ウィンドウには、選択した式に関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a0c0-103">The **Watch** window displays information about the expressions that you have selected.</span></span> <span data-ttu-id="6a0c0-104">最大で 4 つの [ウォッチ] ウィンドウ ( **[ウォッチ 1]** 、 **[ウォッチ 2]、[ウォッチ 3]** 、および **[ウォッチ 4]** ) を表示できます。</span><span class="sxs-lookup"><span data-stu-id="6a0c0-104">There can be up to four watch windows: **Watch 1**, **Watch 2, Watch 3**, and **Watch 4**.</span></span> <span data-ttu-id="6a0c0-105">式は、 **[呼び出し履歴]** ウィンドウで選択された現在の呼び出し履歴フレームのスコープ内で評価されます。</span><span class="sxs-lookup"><span data-stu-id="6a0c0-105">The expressions are evaluated within the scope of the current call stack frame that is selected in the **Call Stack** window.</span></span> <span data-ttu-id="6a0c0-106">変数と式を確認するには、デバッグ モードである必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a0c0-106">You must be in debug mode to watch variables and expressions.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="6a0c0-107">タスク一覧</span><span class="sxs-lookup"><span data-stu-id="6a0c0-107">Task List</span></span>  
 <span data-ttu-id="6a0c0-108">**[ウォッチ] ウィンドウにアクセスするには**</span><span class="sxs-lookup"><span data-stu-id="6a0c0-108">**To access the Watch windows**</span></span>  
  
-   <span data-ttu-id="6a0c0-109">**[デバッグ]** メニューの **[ウィンドウ]** をクリックし、 **[ウォッチ]** をクリックします。次に、 **[ウォッチ 1]** 、 **[ウォッチ 2]、[ウォッチ 3]** 、 **[ウォッチ 4]** のいずれかをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a0c0-109">On the **Debug** menu, click **Windows**, click **Watch**, and then click **Watch 1**, **Watch 2, Watch 3**, or **Watch 4**.</span></span>  
  
 <span data-ttu-id="6a0c0-110">**式の値を変更するには**</span><span class="sxs-lookup"><span data-stu-id="6a0c0-110">**To change the value of an expression**</span></span>  
  
-   <span data-ttu-id="6a0c0-111">式を右クリックし、 **[値の編集]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6a0c0-111">Right-click the expression, and then select **Edit Value**.</span></span>  
  
## <a name="columns"></a><span data-ttu-id="6a0c0-112">[列]</span><span class="sxs-lookup"><span data-stu-id="6a0c0-112">Columns</span></span>  
 <span data-ttu-id="6a0c0-113">**Name**</span><span class="sxs-lookup"><span data-stu-id="6a0c0-113">**Name**</span></span>  
 <span data-ttu-id="6a0c0-114">[!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーによって一覧表示される式です。</span><span class="sxs-lookup"><span data-stu-id="6a0c0-114">Are the expressions that are listed by the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span> <span data-ttu-id="6a0c0-115">次の式がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="6a0c0-115">The following expressions are supported:</span></span>  
  
-   <span data-ttu-id="6a0c0-116">変数。</span><span class="sxs-lookup"><span data-stu-id="6a0c0-116">Variables.</span></span>  
  
-   <span data-ttu-id="6a0c0-117">パラメーター。</span><span class="sxs-lookup"><span data-stu-id="6a0c0-117">Parameters.</span></span>  
  
-   <span data-ttu-id="6a0c0-118">名前が @@ で始まるシステム関数。</span><span class="sxs-lookup"><span data-stu-id="6a0c0-118">System functions whose name starts with @@.</span></span>  
  
-   <span data-ttu-id="6a0c0-119">1 つまたは複数の変数、パラメーター、またはシステム関数に演算子を適用して作成された式 (@IntegerCounter + 1、FirstName + LastName など)。</span><span class="sxs-lookup"><span data-stu-id="6a0c0-119">Expressions built by applying operators to one or more variables, parameters, or system functions, such as @IntegerCounter + 1, or FirstName + LastName.</span></span>  
  
-   <span data-ttu-id="6a0c0-120">単一の値を返す Transact-SQL ステートメント (SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1 など)。</span><span class="sxs-lookup"><span data-stu-id="6a0c0-120">Transact-SQL statements that return a single value, such as: SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1.</span></span>  
  
 <span data-ttu-id="6a0c0-121">**Value**</span><span class="sxs-lookup"><span data-stu-id="6a0c0-121">**Value**</span></span>  
 <span data-ttu-id="6a0c0-122">[!INCLUDE[tsql](../../includes/tsql-md.md)] [名前] **で指定した式が**デバッガーによって評価された後に返される値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a0c0-122">Displays the value that is returned after the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger evaluates the expression specified in **Name**.</span></span>  
  
 <span data-ttu-id="6a0c0-123">式の長さが **[値]** 列の幅よりも長い場合は、その式の **[値]** セルにポインターを移動するとツールヒントに完全な値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a0c0-123">If the length of an expression is larger than the width of the **Value** column, a tooltip displays the full value when you move the pointer over the **Value** cell for that expression.</span></span>  
  
 <span data-ttu-id="6a0c0-124">**[値]** セルの虫眼鏡アイコンは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガー ビジュアライザーが使用可能であることを示します。</span><span class="sxs-lookup"><span data-stu-id="6a0c0-124">A magnifying glass icon in a **Value** cell indicates that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger visualizer is available.</span></span> <span data-ttu-id="6a0c0-125">一覧では、 **[テキスト ビジュアライザー]** 、 **[XML ビジュアライザー]** 、または **[HTML ビジュアライザー]** を指定できます。</span><span class="sxs-lookup"><span data-stu-id="6a0c0-125">In the list, you can specify **Text Visualizer**, **XML Visualizer**, or **HTML Visualizer**.</span></span> <span data-ttu-id="6a0c0-126">デバッガー ビジュアライザーを開始するには、虫眼鏡アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a0c0-126">To start a debugger visualizer, click the magnifying glass icon.</span></span> <span data-ttu-id="6a0c0-127">[!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーによりダイアログ ボックスが開き、データがそのデータ型に適した形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a0c0-127">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger opens a dialog that displays the data in a format appropriate to the data type.</span></span>  
  
 <span data-ttu-id="6a0c0-128">**Type**</span><span class="sxs-lookup"><span data-stu-id="6a0c0-128">**Type**</span></span>  
 <span data-ttu-id="6a0c0-129">式のデータ型を表示します。</span><span class="sxs-lookup"><span data-stu-id="6a0c0-129">Displays the data type of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a0c0-130">参照</span><span class="sxs-lookup"><span data-stu-id="6a0c0-130">See Also</span></span>  
 <span data-ttu-id="6a0c0-131">[Transact-SQL デバッガー](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="6a0c0-131">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="6a0c0-132">[Transact-SQL デバッガー情報](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="6a0c0-132">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 <span data-ttu-id="6a0c0-133">[[ローカル] ウィンドウ](transact-sql-debugger-locals-window.md) </span><span class="sxs-lookup"><span data-stu-id="6a0c0-133">[Locals Window](transact-sql-debugger-locals-window.md) </span></span>  
 <span data-ttu-id="6a0c0-134">[[呼び出し履歴] ウィンドウ](transact-sql-debugger-call-stack-window.md) </span><span class="sxs-lookup"><span data-stu-id="6a0c0-134">[Call Stack Window](transact-sql-debugger-call-stack-window.md) </span></span>  
 <span data-ttu-id="6a0c0-135">[[クイック ウォッチ] ダイアログ ボックス](transact-sql-debugger-quickwatch-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="6a0c0-135">[QuickWatch Dialog Box](transact-sql-debugger-quickwatch-dialog-box.md) </span></span>  
 [<span data-ttu-id="6a0c0-136">式 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6a0c0-136">Expressions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/expressions-transact-sql)  
