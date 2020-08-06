---
title: Transact-SQL コードのステップ実行
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, debugging code
- Transact-SQL debugger, step over
- Transact-SQL debugger, step out
- Transact-SQL debugger, step into
ms.assetid: e09079b8-c4c9-42b4-821b-4ce81a98a086
author: rothja
ms.author: jroth
ms.openlocfilehash: 48cb307130c65729640864a26bdf1dfaf344b32b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643765"
---
# <a name="step-through-transact-sql-code"></a><span data-ttu-id="3e496-102">Transact-SQL コードのステップ実行</span><span class="sxs-lookup"><span data-stu-id="3e496-102">Step Through Transact-SQL Code</span></span>
  <span data-ttu-id="3e496-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリ エディター ウィンドウでどの [!INCLUDE[ssDE](../../includes/ssde-md.md)] ステートメントを実行するかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="3e496-103">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger enables you to control which [!INCLUDE[tsql](../../includes/tsql-md.md)] statements are run in a [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window.</span></span> <span data-ttu-id="3e496-104">個々のステートメントでデバッガーを一時停止して、その時点のコード要素の状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="3e496-104">You can pause the debugger on individual statements and then view the state of the code elements at that point.</span></span>  
  
## <a name="breakpoints"></a><span data-ttu-id="3e496-105">ブレークポイント</span><span class="sxs-lookup"><span data-stu-id="3e496-105">Breakpoints</span></span>  
 <span data-ttu-id="3e496-106">ブレークポイントは、特定の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで実行を一時停止することをデバッガーに指示するために使用します。</span><span class="sxs-lookup"><span data-stu-id="3e496-106">A breakpoint signals the debugger to pause execution on a specific [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="3e496-107">ブレークポイントの詳細については、「Transact-SQL ブレークポイントの使用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e496-107">For more information about breakpoints, see Using Transact-SQL Breakpoints.</span></span>  
  
## <a name="controlling-statement-execution"></a><span data-ttu-id="3e496-108">ステートメントの実行の制御</span><span class="sxs-lookup"><span data-stu-id="3e496-108">Controlling Statement Execution</span></span>  
 <span data-ttu-id="3e496-109">[!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] コードの現在のステートメントからの実行について、次のオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3e496-109">In the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger, you can specify the following options for executing from the current statement in [!INCLUDE[tsql](../../includes/tsql-md.md)] code:</span></span>  
  
-   <span data-ttu-id="3e496-110">次のブレークポイントまで実行する。</span><span class="sxs-lookup"><span data-stu-id="3e496-110">Run to the next breakpoint.</span></span>  
  
-   <span data-ttu-id="3e496-111">次のステートメントにステップ インする。</span><span class="sxs-lookup"><span data-stu-id="3e496-111">Step into the next statement.</span></span>  
  
     <span data-ttu-id="3e496-112">次のステートメントで [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャ、関数、またはトリガーが呼び出される場合、モジュールのコードが含まれた新しいクエリ エディター ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3e496-112">If the next statement invokes a [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, function, or trigger, the debugger displays a new Query Editor window that contains the code of the module.</span></span> <span data-ttu-id="3e496-113">ウィンドウはデバッグ モードに設定され、実行はモジュールの最初のステートメントで一時停止します。</span><span class="sxs-lookup"><span data-stu-id="3e496-113">The window is in debug mode, and execution pauses on the first statement in the module.</span></span> <span data-ttu-id="3e496-114">その後、モジュールのコードに対して、ブレークポイントの設定やコードのステップ実行などの操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3e496-114">You can then move through the module code, for example, by setting breakpoints or stepping through the code.</span></span>  
  
-   <span data-ttu-id="3e496-115">次のステートメントにステップ オーバーする。</span><span class="sxs-lookup"><span data-stu-id="3e496-115">Step over the next statement.</span></span>  
  
     <span data-ttu-id="3e496-116">次のステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="3e496-116">The next statement is executed.</span></span> <span data-ttu-id="3e496-117">ただし、ステートメントでストアド プロシージャ、関数、またはトリガーが呼び出される場合、モジュールのコードは完了するまで実行され、その結果が呼び出し元のコードに返されます。</span><span class="sxs-lookup"><span data-stu-id="3e496-117">However, if the statement invokes a stored procedure, function, or trigger, the module code runs until it finishes, and the results are returned to the calling code.</span></span> <span data-ttu-id="3e496-118">ストアド プロシージャにエラーがないことがわかっている場合は、ストアド プロシージャにステップ オーバーできます。</span><span class="sxs-lookup"><span data-stu-id="3e496-118">If you are sure there are no errors in a stored procedure, you can step over it.</span></span> <span data-ttu-id="3e496-119">実行は、ストアド プロシージャ、関数、またはトリガーの呼び出しに続くステートメントで一時停止します。</span><span class="sxs-lookup"><span data-stu-id="3e496-119">Execution pauses on the statement that follows the call to the stored procedure, function, or trigger.</span></span>  
  
-   <span data-ttu-id="3e496-120">ストアド プロシージャ、関数、またはトリガーからステップ アウトする。</span><span class="sxs-lookup"><span data-stu-id="3e496-120">Step out of a stored procedure, function, or trigger.</span></span>  
  
     <span data-ttu-id="3e496-121">実行は、ストアド プロシージャ、関数、またはトリガーの呼び出しに続くステートメントで一時停止します。</span><span class="sxs-lookup"><span data-stu-id="3e496-121">Execution pauses on the statement that follows the call to the stored procedure, function, or trigger.</span></span>  
  
-   <span data-ttu-id="3e496-122">すべてのブレークポイントを無視して、現在の位置からポインターの現在の位置まで実行する。</span><span class="sxs-lookup"><span data-stu-id="3e496-122">Run from the current location to the current location of the pointer, and ignore all breakpoints.</span></span>  
  
 <span data-ttu-id="3e496-123">[!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーでのステートメントの実行を制御するためのさまざまな操作方法を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="3e496-123">The following table lists the various ways in which you can control how statements execute in the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span>  
  
|<span data-ttu-id="3e496-124">アクション</span><span class="sxs-lookup"><span data-stu-id="3e496-124">Action</span></span>|<span data-ttu-id="3e496-125">手順</span><span class="sxs-lookup"><span data-stu-id="3e496-125">Procedure</span></span>|  
|------------|---------------|  
|<span data-ttu-id="3e496-126">現在のステートメントから次のブレークポイントまですべてのステートメントを実行する。</span><span class="sxs-lookup"><span data-stu-id="3e496-126">Run all statements from the current statement to the next breakpoint</span></span>|<span data-ttu-id="3e496-127">**[デバッグ]** メニューの **[続行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e496-127">On the **Debug** menu, click **Continue**.</span></span><br /><br /> <span data-ttu-id="3e496-128">[**デバッグ**] ツールバーの [**続行**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e496-128">On the **Debug** toolbar, click the **Continue** button.</span></span>|  
|<span data-ttu-id="3e496-129">次のステートメントまたはモジュールにステップ インする。</span><span class="sxs-lookup"><span data-stu-id="3e496-129">Step into the next statement or module</span></span>|<span data-ttu-id="3e496-130">[**デバッグ**] メニューの [**ステップイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e496-130">On the **Debug** menu, click **Step Into**.</span></span><br /><br /> <span data-ttu-id="3e496-131">[**デバッグ**] ツールバーの [**ステップイン**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e496-131">On the **Debug** toolbar, click the **Step Into** button.</span></span><br /><br /> <span data-ttu-id="3e496-132">F11 キーを押す。</span><span class="sxs-lookup"><span data-stu-id="3e496-132">Press F11.</span></span>|  
|<span data-ttu-id="3e496-133">次のステートメントまたはモジュールにステップ オーバーする。</span><span class="sxs-lookup"><span data-stu-id="3e496-133">Step over the next statement or module</span></span>|<span data-ttu-id="3e496-134">**[デバッグ]** メニューの **[ステップ オーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e496-134">On the **Debug** menu, click **Step Over**.</span></span><br /><br /> <span data-ttu-id="3e496-135">[**デバッグ**] ツールバーの [**ステップオーバー** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e496-135">On the **Debug** toolbar, click the **Step Over** button.</span></span><br /><br /> <span data-ttu-id="3e496-136">F10 キーを押す。</span><span class="sxs-lookup"><span data-stu-id="3e496-136">Press F10.</span></span>|  
|<span data-ttu-id="3e496-137">モジュールからステップ アウトする。</span><span class="sxs-lookup"><span data-stu-id="3e496-137">Step out of a module</span></span>|<span data-ttu-id="3e496-138">[**デバッグ**] メニューの [**ステップアウト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e496-138">On the **Debug** menu, click **Step Out**.</span></span><br /><br /> <span data-ttu-id="3e496-139">[**デバッグ**] ツールバーの [**ステップアウト**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e496-139">On the **Debug** toolbar, click the **Step Out** button.</span></span><br /><br /> <span data-ttu-id="3e496-140">Shift&lt;/localizedText&gt; + &lt;localizedText&gt;F11&lt;/localizedText&gt; キーを押す。</span><span class="sxs-lookup"><span data-stu-id="3e496-140">Press SHIFT+F11.</span></span>|  
|<span data-ttu-id="3e496-141">現在のカーソル位置まで実行する。</span><span class="sxs-lookup"><span data-stu-id="3e496-141">Run to the current cursor location</span></span>|<span data-ttu-id="3e496-142">クエリ エディター ウィンドウ内で右クリックし、 **[カーソルまで実行]** をクリックする。</span><span class="sxs-lookup"><span data-stu-id="3e496-142">Right-click in the Query Editor window, and then click **Run To Cursor**.</span></span><br /><br /> <span data-ttu-id="3e496-143">Ctrl</localizedText> + <localizedText>F10</localizedText> キーを押す。</span><span class="sxs-lookup"><span data-stu-id="3e496-143">Press CTRL+F10.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3e496-144">参照</span><span class="sxs-lookup"><span data-stu-id="3e496-144">See Also</span></span>  
 [<span data-ttu-id="3e496-145">Transact-SQL デバッガー情報</span><span class="sxs-lookup"><span data-stu-id="3e496-145">Transact-SQL Debugger Information</span></span>](transact-sql-debugger-information.md)  
  
  
