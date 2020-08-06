---
title: '[呼び出し履歴] ウィンドウ'
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Call Stack Window [Transact-SQL]
ms.assetid: ddb0b19c-87cd-4883-bcb8-ec09ffb30369
author: rothja
ms.author: jroth
ms.openlocfilehash: b4b72e484ade696be81ebac8ea4eed9be295edf2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644417"
---
# <a name="call-stack-window"></a><span data-ttu-id="5fa8f-102">[呼び出し履歴] ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="5fa8f-102">Call Stack Window</span></span>
  <span data-ttu-id="5fa8f-103">**[呼び出し履歴]** ウィンドウには、呼び出し履歴上のモジュール、およびモジュールに渡されるパラメーターのデータ型と値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-103">The **Call Stack** window displays the modules on the call stack, and the data types and values of any parameters that are passed to the modules.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="5fa8f-104">モジュール (ストアド プロシージャ、関数、およびトリガーを含む)</span><span class="sxs-lookup"><span data-stu-id="5fa8f-104">modules include stored procedures, functions, and triggers.</span></span> <span data-ttu-id="5fa8f-105">呼び出し履歴を表示するには、デバッグ モードである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-105">To display the call stack, you must be in debug mode.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="5fa8f-106">タスク一覧</span><span class="sxs-lookup"><span data-stu-id="5fa8f-106">Task List</span></span>  
 <span data-ttu-id="5fa8f-107">**[呼び出し履歴] ウィンドウにアクセスするには**</span><span class="sxs-lookup"><span data-stu-id="5fa8f-107">**To access the Call Stack window**</span></span>  
  
-   <span data-ttu-id="5fa8f-108">**[デバッグ]** メニューの **[ウィンドウ]** をポイントし、 **[呼び出し履歴]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-108">On the **Debug** menu, click **Windows**, and then click **Call Stack**.</span></span>  
  
 <span data-ttu-id="5fa8f-109">**現在の呼び出し履歴フレームを変更するには**</span><span class="sxs-lookup"><span data-stu-id="5fa8f-109">**To change the current Call Stack frame**</span></span>  
  
 <span data-ttu-id="5fa8f-110">次の手順のどちらかを使用して、スタック フレームを現在のフレームにすることができます。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-110">You can use either of the following procedures to make a stack frame the current frame:</span></span>  
  
-   <span data-ttu-id="5fa8f-111">スタック フレームを右クリックし、 **[フレームに切り替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-111">Right-click the stack frame, and then click **Switch To Frame**.</span></span>  
  
-   <span data-ttu-id="5fa8f-112">スタック フレームをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-112">Double-click the stack frame.</span></span>  
  
 <span data-ttu-id="5fa8f-113">**現在のフレーム以外のフレームのソースを表示するには**</span><span class="sxs-lookup"><span data-stu-id="5fa8f-113">**To view the source of a frame other than the current frame**</span></span>  
  
-   <span data-ttu-id="5fa8f-114">スタック フレームを右クリックし、 **[ソース コードへ移動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-114">Right-click the stack frame, and then click **Go To Source Code**.</span></span>  
  
## <a name="stack-frames"></a><span data-ttu-id="5fa8f-115">スタック フレーム</span><span class="sxs-lookup"><span data-stu-id="5fa8f-115">Stack Frames</span></span>  
 <span data-ttu-id="5fa8f-116">**[呼び出し履歴]** ウィンドウの各行はスタック フレームと呼ばれ、 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイルからモジュールへの呼び出し、またはあるモジュールから別のモジュールへの呼び出しを表します。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-116">Each row in the **Call Stack** window is called a stack frame and represents either a call from a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file to a module or a call from one module to another.</span></span> <span data-ttu-id="5fa8f-117">表示上、一番下のスタック フレームは、スタックへの最初の呼び出しを行った [!INCLUDE[ssDE](../../includes/ssde-md.md)] のクエリ エディター ウィンドウの行を表します。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-117">The bottom stack frame in the display indicates the line in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window that made the first call into the stack.</span></span> <span data-ttu-id="5fa8f-118">一番上の行は、デバッガーが実行を一時停止した行を表し、ウィンドウの左余白の黄色の矢印で示されます。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-118">The top row indicates the line on which the debugger paused execution, and is identified by a yellow arrow in the left margin of the window.</span></span> <span data-ttu-id="5fa8f-119">その間の各行は、モジュールと、1 つ上のスタック フレームを呼び出したソース コードの行番号を表します。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-119">Each intermediate row indicates the module and the line number of the source code that called the next higher stack frame.</span></span>  
  
 <span data-ttu-id="5fa8f-120">**[ローカル]** 、 **[ウォッチ]** 、および **[クイック ウォッチ]** の各ウィンドウ内のすべての式は、現在のスタック フレームに基づいて評価されます。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-120">All expressions in the **Locals**, **Watch**, and **QuickWatch** windows are evaluated based on the current stack frame.</span></span> <span data-ttu-id="5fa8f-121">クエリ エディター ウィンドウには、現在のフレームのコードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-121">The Query Editor window displays the code for the current frame.</span></span> <span data-ttu-id="5fa8f-122">既定では、現在のスタック フレームは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーが実行を一時停止したフレームです。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-122">By default, the current stack frame is the frame in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger paused execution.</span></span> <span data-ttu-id="5fa8f-123">現在のスタック フレームを別のフレームに変更すると、 **[ローカル]** 、 **[ウォッチ]** 、および **[クイック ウォッチ]** の各ウィンドウ内の式が新しいフレームのコンテキストで再評価され、新しいフレームのソース コードがクエリ エディター ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-123">When you change the current stack frame to another frame, the expressions in the **Locals**, **Watch**, and **QuickWatch** windows are reevaluated in the context of the new frame, and the source code of the new frame is displayed in the Query Editor window.</span></span>  
  
## <a name="columns"></a><span data-ttu-id="5fa8f-124">[列]</span><span class="sxs-lookup"><span data-stu-id="5fa8f-124">Columns</span></span>  
 <span data-ttu-id="5fa8f-125">**Name**</span><span class="sxs-lookup"><span data-stu-id="5fa8f-125">**Name**</span></span>  
 <span data-ttu-id="5fa8f-126">呼び出し履歴上のモジュールに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-126">Displays information about a module on the call stack.</span></span>  
  
 <span data-ttu-id="5fa8f-127">呼び出し履歴の一番下の行の場合、 **[名前]** には、クエリ エディターのソース ウィンドウとスタックへの最初の呼び出しの行番号が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-127">For the bottom row in the call stack, **Name** lists the Query Editor source window and line number of the first call into the stack.</span></span> <span data-ttu-id="5fa8f-128">その他の行の場合、 **[名前]** は、 **[Module(Instance.Database)(ParmList) LineNumber]** の形式になります。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-128">For the other rows, **Name** has the format **Module(Instance.Database)(ParmList) LineNumber**.</span></span>  
  
 <span data-ttu-id="5fa8f-129">**[Module]**</span><span class="sxs-lookup"><span data-stu-id="5fa8f-129">**Module**</span></span>  
 <span data-ttu-id="5fa8f-130">ストアド プロシージャ、関数、または次のフレームを呼び出したストアド プロシージャの名前です。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-130">Is the name of the stored procedure, function, or stored procedure that called to the next frame.</span></span>  
  
 <span data-ttu-id="5fa8f-131">**[Instance.Database]**</span><span class="sxs-lookup"><span data-stu-id="5fa8f-131">**Instance.Database**</span></span>  
 <span data-ttu-id="5fa8f-132">[!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスと、モジュールを保持しているデータベースです。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-132">Is the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and the database that is holding the module.</span></span>  
  
 <span data-ttu-id="5fa8f-133">**[ParmList]**</span><span class="sxs-lookup"><span data-stu-id="5fa8f-133">**ParmList**</span></span>  
 <span data-ttu-id="5fa8f-134">モジュールの呼び出し時に渡される各パラメーターのデータ型、名前、および値を示します。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-134">Indicates the data type, name, and value for each parameter that is passed in during the call to the module.</span></span>  
  
 <span data-ttu-id="5fa8f-135">**LineNumber**</span><span class="sxs-lookup"><span data-stu-id="5fa8f-135">**LineNumber**</span></span>  
 <span data-ttu-id="5fa8f-136">一番上の行を除くすべての行では、 **[LineNumber]** は、モジュール内のどの行でフレームを呼び出したかを示します。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-136">For all rows except the top row, **LineNumber** indicates which line in the module called to the frame.</span></span> <span data-ttu-id="5fa8f-137">一番上の行では、 **[LineNumber]** は、デバッガーのフォーカスが現在置かれている行を示します。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-137">For the top row, **LineNumber** indicates the line on which the debugger is currently focused.</span></span>  
  
 <span data-ttu-id="5fa8f-138">**Language**</span><span class="sxs-lookup"><span data-stu-id="5fa8f-138">**Language**</span></span>  
 <span data-ttu-id="5fa8f-139">**を表す** [Transact-SQL] [!INCLUDE[tsql](../../includes/tsql-md.md)]が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5fa8f-139">Displays **Transact-SQL** for [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fa8f-140">参照</span><span class="sxs-lookup"><span data-stu-id="5fa8f-140">See Also</span></span>  
 <span data-ttu-id="5fa8f-141">[Transact-sql デバッガー](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="5fa8f-141">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="5fa8f-142">[Transact-sql デバッガー情報](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="5fa8f-142">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 [<span data-ttu-id="5fa8f-143">Transact-SQL コードのステップ実行</span><span class="sxs-lookup"><span data-stu-id="5fa8f-143">Step Through Transact-SQL Code</span></span>](step-through-transact-sql-code.md)  
