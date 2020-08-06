---
title: '[プロセス実行タスクエディター] ([処理] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executeprocesstask.process.f1
helpviewer_keywords:
- Execute Process Task Editor
ms.assetid: 0fc22406-e79b-47a4-a7e4-108d4ce6202f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ce8629be2c07ae4caac4586b266936a908e71499
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710982"
---
# <a name="execute-process-task-editor-process-page"></a><span data-ttu-id="c6441-102">Execute Process Task Editor (Process Page)</span><span class="sxs-lookup"><span data-stu-id="c6441-102">Execute Process Task Editor (Process Page)</span></span>
  <span data-ttu-id="c6441-103">**[プロセス実行タスク エディター]** ダイアログ ボックスの **[処理]** ページを使用すると、プロセスを実行する際のオプションを構成できます。</span><span class="sxs-lookup"><span data-stu-id="c6441-103">Use the **Process** page of the **Execute Process Task Editor** dialog box to configure the options that execute the process.</span></span> <span data-ttu-id="c6441-104">オプションには、実行する実行可能ファイル、そのファイルの場所、コマンド プロンプト引数、入力するための変数、出力をキャプチャする変数などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c6441-104">These options include the executable to run, its location, command prompt arguments, and the variables that provide input and capture output.</span></span>  
  
 <span data-ttu-id="c6441-105">このタスクの詳細については、「 [Execute Process Task](control-flow/execute-process-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6441-105">To learn about this task, see [Execute Process Task](control-flow/execute-process-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="c6441-106">Options</span><span class="sxs-lookup"><span data-stu-id="c6441-106">Options</span></span>  
 <span data-ttu-id="c6441-107">**[RequireFullFileName]**</span><span class="sxs-lookup"><span data-stu-id="c6441-107">**RequireFullFileName**</span></span>  
 <span data-ttu-id="c6441-108">指定した場所に実行可能ファイルが見つからなかった場合に、タスクを中止するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6441-108">Indicate whether the task should fail if the executable is not found at the specified location.</span></span>  
  
 <span data-ttu-id="c6441-109">**[実行可能ファイル]**</span><span class="sxs-lookup"><span data-stu-id="c6441-109">**Executable**</span></span>  
 <span data-ttu-id="c6441-110">実行する実行可能ファイルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c6441-110">Type the name of the executable to run.</span></span>  
  
 <span data-ttu-id="c6441-111">**引数**</span><span class="sxs-lookup"><span data-stu-id="c6441-111">**Arguments**</span></span>  
 <span data-ttu-id="c6441-112">コマンド プロンプト引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="c6441-112">Provide command prompt arguments.</span></span>  
  
 <span data-ttu-id="c6441-113">**[WorkingDirectory]**</span><span class="sxs-lookup"><span data-stu-id="c6441-113">**WorkingDirectory**</span></span>  
 <span data-ttu-id="c6441-114">実行可能ファイルが置かれているフォルダーのパスを入力するか、参照ボタン ( **[...]** ) をクリックしてフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6441-114">Type the path of the folder that contains the executable, or click the browse button **(...)** and locate the folder.</span></span>  
  
 <span data-ttu-id="c6441-115">**[StandardInputVariable]**</span><span class="sxs-lookup"><span data-stu-id="c6441-115">**StandardInputVariable**</span></span>  
 <span data-ttu-id="c6441-116">プロセスが入力する変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="c6441-116">Select a variable to provide the input to the process, or click \<**New variable...**> to create a new variable:</span></span>  
  
 <span data-ttu-id="c6441-117">**関連項目:**  [変数の追加](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="c6441-117">**Related Topics:**  [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
 <span data-ttu-id="c6441-118">**[StandardOutputVariable]**</span><span class="sxs-lookup"><span data-stu-id="c6441-118">**StandardOutputVariable**</span></span>  
 <span data-ttu-id="c6441-119">プロセスの出力をキャプチャする変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="c6441-119">Select a variable to capture the output of the process, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="c6441-120">**[StandardErrorVariable]**</span><span class="sxs-lookup"><span data-stu-id="c6441-120">**StandardErrorVariable**</span></span>  
 <span data-ttu-id="c6441-121">プロセッサのエラー出力をキャプチャする変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="c6441-121">Select a variable to capture the error output of the processor, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="c6441-122">**[FailTaskIfReturnCodeIsNotSuccessValue]**</span><span class="sxs-lookup"><span data-stu-id="c6441-122">**FailTaskIfReturnCodeIsNotSuccessValue**</span></span>  
 <span data-ttu-id="c6441-123">プロセス終了コードが **[SuccessValue]** で指定されている値と異なった場合、タスクを終了するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6441-123">Indicate whether the task fails if the process exit code is different from the value specified in **SuccessValue**.</span></span>  
  
 <span data-ttu-id="c6441-124">**[SuccessValue]**</span><span class="sxs-lookup"><span data-stu-id="c6441-124">**SuccessValue**</span></span>  
 <span data-ttu-id="c6441-125">実行可能ファイルが正常に終了した場合に返される値を指定します。</span><span class="sxs-lookup"><span data-stu-id="c6441-125">Specify the value returned by the executable to indicate success.</span></span> <span data-ttu-id="c6441-126">既定では、この値は **0**に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c6441-126">By default this value is set to **0**.</span></span>  
  
 <span data-ttu-id="c6441-127">**[TimeOut]**</span><span class="sxs-lookup"><span data-stu-id="c6441-127">**TimeOut**</span></span>  
 <span data-ttu-id="c6441-128">プロセスを実行できる秒数を指定します。</span><span class="sxs-lookup"><span data-stu-id="c6441-128">Specify the number of seconds that the process can run.</span></span> <span data-ttu-id="c6441-129">値を **0** に指定すると、タイムアウト値が使用されず、プロセスは完了するかエラーが発生するまで実行されます。</span><span class="sxs-lookup"><span data-stu-id="c6441-129">A value of **0** indicates that no time-out value is used, and the process runs until it is completed or until an error occurs.</span></span>  
  
 <span data-ttu-id="c6441-130">**[TerminateProcessAfterTimeOut]**</span><span class="sxs-lookup"><span data-stu-id="c6441-130">**TerminateProcessAfterTimeOut**</span></span>  
 <span data-ttu-id="c6441-131">**[TimeOut]** オプションで指定されたタイムアウト時間の後に、プロセスを強制終了するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6441-131">Indicate whether the process is forced to end after the time-out period specified by the **TimeOut** option.</span></span> <span data-ttu-id="c6441-132">このオプションは、 **[TimeOut]** が **0**以外の場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c6441-132">This option is available only if **TimeOut** is not **0**.</span></span>  
  
 <span data-ttu-id="c6441-133">**[WindowStyle]**</span><span class="sxs-lookup"><span data-stu-id="c6441-133">**WindowStyle**</span></span>  
 <span data-ttu-id="c6441-134">プロセスを実行する際のウィンドウのスタイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6441-134">Specify the window style in which to run the process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6441-135">参照</span><span class="sxs-lookup"><span data-stu-id="c6441-135">See Also</span></span>  
 <span data-ttu-id="c6441-136">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="c6441-136">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="c6441-137">[[式] ページ](expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="c6441-137">[Expressions Page](expressions/expressions-page.md)</span></span>  
  
  
