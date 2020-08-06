---
title: ブレークポイント アクションの指定
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint action
- Transact-SQL debugger, breakpoint when hit action
ms.assetid: f97f0097-6f51-40c1-b2e0-294a93ce1e1b
author: rothja
ms.author: jroth
ms.openlocfilehash: 57b3c445e738752400e716538e038349e04e7bd2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641586"
---
# <a name="specify-a-breakpoint-action"></a><span data-ttu-id="33ae5-102">ブレークポイント アクションの指定</span><span class="sxs-lookup"><span data-stu-id="33ae5-102">Specify a Breakpoint Action</span></span>
  <span data-ttu-id="33ae5-103">ブレークポイント **ヒット時** アクションは、ブレークポイントに対して [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーが実行するカスタム タスクを指定します。</span><span class="sxs-lookup"><span data-stu-id="33ae5-103">A breakpoint **When Hit** action specifies a custom task that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger performs for a breakpoint.</span></span> <span data-ttu-id="33ae5-104">指定したヒット カウントに達し、指定したブレークポイントの条件が満たされると、ブレークポイントに指定されたアクションがデバッガーによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="33ae5-104">If the specified hit count is reached and any specified breakpoint condition is satisfied, the debugger performs the action specified for the breakpoint.</span></span>  
  
##  <a name="action-considerations"></a><a name="BKMK_ActionConsiderations"></a> <span data-ttu-id="33ae5-105">アクションに関する注意点</span><span class="sxs-lookup"><span data-stu-id="33ae5-105">Action Considerations</span></span>  
 <span data-ttu-id="33ae5-106">ブレークポイントの既定のアクションでは、ヒット カウントとブレークポイントの条件の両方が満たされたときに、実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="33ae5-106">The default action for a breakpoint is to break execution when both the hit count and breakpoint condition have been satisfied.</span></span> <span data-ttu-id="33ae5-107">**デバッガーでの** ヒット時 [!INCLUDE[tsql](../../includes/tsql-md.md)] アクションの主な用途は、出力メッセージを指定して、デバッガーの **[出力]** ウィンドウに情報を出力することです。</span><span class="sxs-lookup"><span data-stu-id="33ae5-107">The primary use of a **When Hit** action in the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger is to instead print information to the debugger **Output** window by specifying a print message.</span></span>  
  
 <span data-ttu-id="33ae5-108">出力メッセージは、デバッグ対象の **からの情報を格納した式を含むテキスト文字列として、** [メッセージを表示する] [!INCLUDE[tsql](../../includes/tsql-md.md)] オプションで指定します。</span><span class="sxs-lookup"><span data-stu-id="33ae5-108">A print message is specified in the **Print a Message** option, and is specified as a text string that includes expressions containing information from the [!INCLUDE[tsql](../../includes/tsql-md.md)] being debugged.</span></span> <span data-ttu-id="33ae5-109">式には、次の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="33ae5-109">Expressions include:</span></span>  
  
-   <span data-ttu-id="33ae5-110">中かっこ ({}) に囲まれた [!INCLUDE[tsql](../../includes/tsql-md.md)] 式。</span><span class="sxs-lookup"><span data-stu-id="33ae5-110">A [!INCLUDE[tsql](../../includes/tsql-md.md)] expression contained in curly braces ({}).</span></span> <span data-ttu-id="33ae5-111">式には、 [!INCLUDE[tsql](../../includes/tsql-md.md)] 変数、パラメーター、および組み込み関数を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="33ae5-111">The expressions can include [!INCLUDE[tsql](../../includes/tsql-md.md)] variables, parameters, and built-in functions.</span></span> <span data-ttu-id="33ae5-112">例としては、{@MyVariable}、{@NameParameter}、{@@SPID}、{SERVERPROPERTY('ProcessID')} などがあります。</span><span class="sxs-lookup"><span data-stu-id="33ae5-112">Examples include {@MyVariable}, {@NameParameter}, {@@SPID}, or {SERVERPROPERTY('ProcessID')}.</span></span>  
  
-   <span data-ttu-id="33ae5-113">次のキーワードのいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="33ae5-113">One of the following keywords:</span></span>  
  
    1.  <span data-ttu-id="33ae5-114">$ADDRESS は、ブレークポイントが設定されているストアド プロシージャまたはユーザー定義関数の名前を返します。</span><span class="sxs-lookup"><span data-stu-id="33ae5-114">$ADDRESS returns the name of the stored procedure or user-defined function where the breakpoint is set.</span></span> <span data-ttu-id="33ae5-115">ブレークポイントがエディター ウィンドウに設定されている場合、$ADDRESS は編集されているスクリプト ファイルの名前を返します。</span><span class="sxs-lookup"><span data-stu-id="33ae5-115">If the breakpoint is set in the editor window, $ADDRESS returns the name of the script file being edited.</span></span> <span data-ttu-id="33ae5-116">$ADDRESS および $FUNCTION は、 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーで同じ情報を返します。</span><span class="sxs-lookup"><span data-stu-id="33ae5-116">$ADDRESS and $FUNCTION return the same information in the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span>  
  
    2.  <span data-ttu-id="33ae5-117">$CALLER は、ストアド プロシージャまたは関数を呼び出した [!INCLUDE[tsql](../../includes/tsql-md.md)] コードの単位の名前を返します。</span><span class="sxs-lookup"><span data-stu-id="33ae5-117">$CALLER returns the name of the unit of [!INCLUDE[tsql](../../includes/tsql-md.md)] code that called a stored procedure or function.</span></span> <span data-ttu-id="33ae5-118">ブレークポイントがエディターウィンドウにある場合、$CALLER はを返し \<No caller available> ます。</span><span class="sxs-lookup"><span data-stu-id="33ae5-118">If the breakpoint is in the editor window, $CALLER returns \<No caller available>.</span></span> <span data-ttu-id="33ae5-119">ブレークポイントが、エディター ウィンドウ内のコードから呼び出されるストアド プロシージャまたはユーザー定義関数にある場合は、$CALLER は編集されているファイルの名前を返します。</span><span class="sxs-lookup"><span data-stu-id="33ae5-119">If the breakpoint is in a stored procedure or user-defined function called from the code in the editor window, $CALLER returns the name of the file being edited.</span></span> <span data-ttu-id="33ae5-120">ブレークポイントが、他のストアド プロシージャまたは関数から呼び出されるストアド プロシージャまたはユーザー定義関数にある場合は、$CALLER は呼び出しているプロシージャまたは関数の名前を返します。</span><span class="sxs-lookup"><span data-stu-id="33ae5-120">If the breakpoint is in a stored procedure or user-defined function called from another stored procedure or function, $CALLER returns the name of the calling procedure or function.</span></span>  
  
    3.  <span data-ttu-id="33ae5-121">$CALLSTACK は、現在のストアド プロシージャまたはユーザー定義関数を呼び出したチェーン内の関数の呼び出し履歴を返します。</span><span class="sxs-lookup"><span data-stu-id="33ae5-121">$CALLSTACK returns the call stack of functions in the chain that called the current stored procedure or user-defined function.</span></span> <span data-ttu-id="33ae5-122">ブレークポイントがエディター ウィンドウにある場合、$CALLSTACK は編集されているスクリプト ファイルの名前を返します。</span><span class="sxs-lookup"><span data-stu-id="33ae5-122">If the breakpoint is in the editor window, $CALLSTACK returns the name of the script file being edited.</span></span>  
  
    4.  <span data-ttu-id="33ae5-123">$FUNCTION は、ブレークポイントが設定されているストアド プロシージャまたはユーザー定義関数の名前を返します。</span><span class="sxs-lookup"><span data-stu-id="33ae5-123">$FUNCTION returns the name of the stored procedure or user-defined function where the breakpoint is set.</span></span> <span data-ttu-id="33ae5-124">ブレークポイントがエディター ウィンドウに設定されている場合、$FUNCTION は編集されているスクリプト ファイルの名前を返します。</span><span class="sxs-lookup"><span data-stu-id="33ae5-124">If the breakpoint is set in the editor window, $FUNCTION returns the name of the script file being edited.</span></span>  
  
    5.  <span data-ttu-id="33ae5-125">$PID および $PNAME は、 [!INCLUDE[tsql](../../includes/tsql-md.md)] が実行されているデータベース エンジンのインスタンスを実行しているオペレーティング システム プロセスの ID および名前を返します。</span><span class="sxs-lookup"><span data-stu-id="33ae5-125">$PID and $PNAME return the ID and name of the operating system process running the instance of the Database Engine where the [!INCLUDE[tsql](../../includes/tsql-md.md)] is running.</span></span> <span data-ttu-id="33ae5-126">$PID は、SERVERPROPERTY('ProcessID') と同じ ID を返しますが、SERVERPROPERTY('ProcessID') が 10 進値であるのに対して $PID は 16 進数の値である点が異なります。</span><span class="sxs-lookup"><span data-stu-id="33ae5-126">$PID returns the same ID as SERVERPROPERTY('ProcessID'), except that $PID is a hexadecimal value while SERVERPROPERTY('ProcessID') is a decimal value.</span></span>  
  
    6.  <span data-ttu-id="33ae5-127">$TID および $TNAME は、 [!INCLUDE[tsql](../../includes/tsql-md.md)] バッチを実行しているオペレーティング システム スレッドの ID および名前を返します。</span><span class="sxs-lookup"><span data-stu-id="33ae5-127">$TID and $TNAME return the ID and name of the operating system thread running the [!INCLUDE[tsql](../../includes/tsql-md.md)] batch.</span></span> <span data-ttu-id="33ae5-128">スレッドは、データベース エンジンのインスタンスを実行しているプロセスに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="33ae5-128">The thread is one associated with the process running the instance of the Database Engine.</span></span> <span data-ttu-id="33ae5-129">$TID は SELECT kpid FROM sys.sysprocesses WHERE spid = @@SPID と同じ値を返しますが、kpid が 10 進値であるのに対して $TID は 16 進数の値である点が異なります。</span><span class="sxs-lookup"><span data-stu-id="33ae5-129">$TID returns the same value as SELECT kpid FROM sys.sysprocesses WHERE spid = @@SPID, except that $TID is a hexadecimal value while kpid is a decimal value.</span></span>  
  
-   <span data-ttu-id="33ae5-130">"\\{"、" \\}"、" \\" のようにバックスラッシュ記号 ( \\\\) をエスケープ文字とすることで、メッセージ内で中かっことバックスラッシュを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="33ae5-130">You can also use the backslash character (\\) as an escape character to allow curly braces and backslashes in the message: \\{, \\}, and \\\\.</span></span>  
  
#### <a name="to-specify-a-when-hit-action"></a><span data-ttu-id="33ae5-131">ヒット時アクションを指定するには</span><span class="sxs-lookup"><span data-stu-id="33ae5-131">To Specify a When Hit Action</span></span>  
  
1.  <span data-ttu-id="33ae5-132">エディター ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[ヒット時]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33ae5-132">In the editor window, right-click the breakpoint glyph, and then click **When Hit** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="33ae5-133">または</span><span class="sxs-lookup"><span data-stu-id="33ae5-133">-or-</span></span>  
  
     <span data-ttu-id="33ae5-134">**[ブレークポイント]** ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[ヒット時]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33ae5-134">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **When hit** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="33ae5-135">**[ブレークポイントのヒット時]** ダイアログ ボックスで、目的の動作を選択します。</span><span class="sxs-lookup"><span data-stu-id="33ae5-135">In the **When Breakpoint Is Hit** dialog box, select the behavior you want:</span></span>  
  
    1.  <span data-ttu-id="33ae5-136">ブレークポイントにヒットしたときにデバッガーの出力ウィンドウにメッセージを出力するには、 **[メッセージを表示する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="33ae5-136">Select **Print a Message** to print a message in the debugger Output window when the breakpoint is hit.</span></span>  
  
    2.  <span data-ttu-id="33ae5-137">**[マクロを実行する]** オプションは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーでは使用できないため、グレーで表示されます。</span><span class="sxs-lookup"><span data-stu-id="33ae5-137">The **Run a Macro** option is not available from the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger, and is greyed out.</span></span>  
  
    3.  <span data-ttu-id="33ae5-138">ブレークポイントの実行を中断したくない場合は、 **[続けて実行する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="33ae5-138">Select **Continue execution** if you do not want the breakpoint to pause execution.</span></span> <span data-ttu-id="33ae5-139">このオプションは、 **[メッセージを表示する]** オプションを選択した場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="33ae5-139">This option is active only if you have selected the **Print a Message** option.</span></span>  
  
3.  <span data-ttu-id="33ae5-140">**[OK]** をクリックして変更を適用するか、 **[キャンセル]** をクリックして変更を適用せずに終了します。</span><span class="sxs-lookup"><span data-stu-id="33ae5-140">Click **OK** to implement the changes, or **Cancel** to exit without applying the changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33ae5-141">参照</span><span class="sxs-lookup"><span data-stu-id="33ae5-141">See Also</span></span>  
 <span data-ttu-id="33ae5-142">[ブレークポイント条件の指定](specify-a-breakpoint-condition.md) </span><span class="sxs-lookup"><span data-stu-id="33ae5-142">[Specify a Breakpoint Condition](specify-a-breakpoint-condition.md) </span></span>  
 [<span data-ttu-id="33ae5-143">ヒット カウントの指定</span><span class="sxs-lookup"><span data-stu-id="33ae5-143">Specify a Hit Count</span></span>](specify-a-hit-count.md)  
