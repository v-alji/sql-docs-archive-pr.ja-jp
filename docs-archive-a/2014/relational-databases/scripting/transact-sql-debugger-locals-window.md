---
title: '[ローカル] ウィンドウ'
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Locals Window [Transact-SQL]
ms.assetid: 59bea640-7823-4b4d-832c-f384d83cca2f
author: rothja
ms.author: jroth
ms.openlocfilehash: 6f8f62eb69a50d7543af41dddb9c62c842d17151
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644965"
---
# <a name="locals-window"></a><span data-ttu-id="2a4ec-102">ローカル ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="2a4ec-102">Locals Window</span></span>
  <span data-ttu-id="2a4ec-103">**[ローカル]** ウィンドウには、 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーの現在のスコープ内にあるローカル式についての情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2a4ec-103">The **Locals** window displays information about the local expressions in the current scope of the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span> <span data-ttu-id="2a4ec-104">スコープは、 **[呼び出し履歴]** ウィンドウで選択された現在の呼び出し履歴フレームに設定されます。</span><span class="sxs-lookup"><span data-stu-id="2a4ec-104">The scope is set to the current call stack frame that is selected in the **Call Stack** window.</span></span> <span data-ttu-id="2a4ec-105">ローカル式を表示するには、デバッグ モードである必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a4ec-105">You must be in debug mode to display the local expressions.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="2a4ec-106">タスク一覧</span><span class="sxs-lookup"><span data-stu-id="2a4ec-106">Task List</span></span>  
 <span data-ttu-id="2a4ec-107">**[ローカル] ウィンドウにアクセスするには**</span><span class="sxs-lookup"><span data-stu-id="2a4ec-107">**To access the Locals window**</span></span>  
  
-   <span data-ttu-id="2a4ec-108">**[デバッグ]** メニューの **[ウィンドウ]** をポイントし、 **[ローカル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a4ec-108">On the **Debug** menu, click **Windows**, and then click **Locals**.</span></span>  
  
 <span data-ttu-id="2a4ec-109">**式の値を変更するには**</span><span class="sxs-lookup"><span data-stu-id="2a4ec-109">**To change the value of an expression**</span></span>  
  
-   <span data-ttu-id="2a4ec-110">式を右クリックし、 **[値の編集]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2a4ec-110">Right-click the expression, and then select **Edit Value**.</span></span>  
  
## <a name="columns"></a><span data-ttu-id="2a4ec-111">[列]</span><span class="sxs-lookup"><span data-stu-id="2a4ec-111">Columns</span></span>  
 <span data-ttu-id="2a4ec-112">**Name**</span><span class="sxs-lookup"><span data-stu-id="2a4ec-112">**Name**</span></span>  
 <span data-ttu-id="2a4ec-113">ローカル式の名前です。</span><span class="sxs-lookup"><span data-stu-id="2a4ec-113">Is the name of the local expression.</span></span> <span data-ttu-id="2a4ec-114">[!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーでは、変数、パラメーター、および名前が @@ で始まるシステム関数が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="2a4ec-114">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger lists variables, parameters, and the system functions that have names that start with @@.</span></span>  
  
 <span data-ttu-id="2a4ec-115">**Value**</span><span class="sxs-lookup"><span data-stu-id="2a4ec-115">**Value**</span></span>  
 <span data-ttu-id="2a4ec-116">ローカル式に現在割り当てられている値を表示します。</span><span class="sxs-lookup"><span data-stu-id="2a4ec-116">Displays the value that is currently assigned to the local expression.</span></span> <span data-ttu-id="2a4ec-117">式に値が割り当てられていない場合、この列は空白です。</span><span class="sxs-lookup"><span data-stu-id="2a4ec-117">This column is blank when no value has been assigned to the expression.</span></span>  
  
 <span data-ttu-id="2a4ec-118">式の長さが **[値]** 列の幅よりも長い場合は、その式の **[値]** セルにポインターを移動するとツールヒントに完全な値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2a4ec-118">If the length of an expression is larger than the width of the **Value** column, a tooltip displays the full value when you move the pointer over the **Value** cell for that expression.</span></span>  
  
 <span data-ttu-id="2a4ec-119">**[値]** セルの虫眼鏡アイコンは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガー ビジュアライザーが使用可能であることを示します。</span><span class="sxs-lookup"><span data-stu-id="2a4ec-119">A magnifying glass icon in a **Value** cell indicates that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger visualizer is available.</span></span> <span data-ttu-id="2a4ec-120">一覧では、 **[テキスト ビジュアライザー]** 、 **[XML ビジュアライザー]** 、または **[HTML ビジュアライザー]** を指定できます。</span><span class="sxs-lookup"><span data-stu-id="2a4ec-120">In the list, you can specify **Text Visualizer**, **XML Visualizer**, or **HTML Visualizer**.</span></span> <span data-ttu-id="2a4ec-121">デバッガー ビジュアライザーを開始するには、虫眼鏡アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a4ec-121">To start a debugger visualizer, click the magnifying glass icon.</span></span> <span data-ttu-id="2a4ec-122">[!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーによりダイアログ ボックスが開き、データがそのデータ型に適した形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="2a4ec-122">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger opens a dialog box that displays the data in a format appropriate to the data type.</span></span>  
  
 <span data-ttu-id="2a4ec-123">**Type**</span><span class="sxs-lookup"><span data-stu-id="2a4ec-123">**Type**</span></span>  
 <span data-ttu-id="2a4ec-124">式のデータ型を表示します。</span><span class="sxs-lookup"><span data-stu-id="2a4ec-124">Displays the data type of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a4ec-125">参照</span><span class="sxs-lookup"><span data-stu-id="2a4ec-125">See Also</span></span>  
 <span data-ttu-id="2a4ec-126">[Transact-SQL デバッガー](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="2a4ec-126">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="2a4ec-127">[Transact-SQL デバッガー情報](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="2a4ec-127">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 <span data-ttu-id="2a4ec-128">[[ウォッチ] ウィンドウ](transact-sql-debugger-watch-window.md) </span><span class="sxs-lookup"><span data-stu-id="2a4ec-128">[Watch Window](transact-sql-debugger-watch-window.md) </span></span>  
 <span data-ttu-id="2a4ec-129">[[呼び出し履歴] ウィンドウ](transact-sql-debugger-call-stack-window.md) </span><span class="sxs-lookup"><span data-stu-id="2a4ec-129">[Call Stack Window](transact-sql-debugger-call-stack-window.md) </span></span>  
 <span data-ttu-id="2a4ec-130">[[クイック ウォッチ] ダイアログ ボックス](transact-sql-debugger-quickwatch-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="2a4ec-130">[QuickWatch Dialog Box](transact-sql-debugger-quickwatch-dialog-box.md) </span></span>  
 [<span data-ttu-id="2a4ec-131">式 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2a4ec-131">Expressions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/expressions-transact-sql)  
