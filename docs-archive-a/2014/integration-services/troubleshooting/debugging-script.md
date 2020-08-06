---
title: スクリプトのデバッグ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Script task [Integration Services], debugging
- debugging [Integration Services], scripts
- scripts [Integration Services], debugging
ms.assetid: fddf57d8-8607-4f88-85a0-1b683087b491
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a7926f806f20f76c7aaac0c22b970addc5e93a78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736505"
---
# <a name="debugging-script"></a><span data-ttu-id="a4f5a-102">スクリプトのデバッグ</span><span class="sxs-lookup"><span data-stu-id="a4f5a-102">Debugging Script</span></span>
  <span data-ttu-id="a4f5a-103">スクリプト タスクやスクリプト コンポーネントで使うスクリプトは、[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) で作成します。</span><span class="sxs-lookup"><span data-stu-id="a4f5a-103">You write the scripts that the Script task and Script component use, in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span>  
  
 <span data-ttu-id="a4f5a-104">VSTA では、ブレークポイントを設定してスクリプト化します。</span><span class="sxs-lookup"><span data-stu-id="a4f5a-104">You set and script breakpoints in VSTA.</span></span> <span data-ttu-id="a4f5a-105">ブレークポイントは VSTA で管理できますが、 **デザイナーで用意されている** [ブレークポイントの設定] [!INCLUDE[ssIS](../../includes/ssis-md.md)] ダイアログ ボックスを使用しても管理できます。</span><span class="sxs-lookup"><span data-stu-id="a4f5a-105">You can manage breakpoints in VSTA, but you can also manage the breakpoints using the **Set Breakpoints** dialog box that [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer provides.</span></span> <span data-ttu-id="a4f5a-106">詳細については、「 [制御フローのデバッグ](debugging-control-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4f5a-106">For more information, see [Debugging Control Flow](debugging-control-flow.md).</span></span>  
  
 <span data-ttu-id="a4f5a-107">**[ブレークポイントの設定]** ダイアログ ボックスには、スクリプト ブレークポイントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a4f5a-107">The **Set Breakpoints** dialog box includes the script breakpoints.</span></span> <span data-ttu-id="a4f5a-108">スクリプト ブレークポイントは、ブレークポイントの一覧の一番下に表示され、ブレークポイントが設定されている行番号と関数の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="a4f5a-108">These breakpoints appear at the bottom of the breakpoint list, and display the line number and the name of the function in which the breakpoint appears.</span></span> <span data-ttu-id="a4f5a-109">スクリプト ブレークポイントは、 **[ブレークポイントの設定]** ダイアログ ボックスで削除できます。</span><span class="sxs-lookup"><span data-stu-id="a4f5a-109">You can delete a script breakpoint from the **Set Breakpoints** dialog box.</span></span>  
  
 <span data-ttu-id="a4f5a-110">実行時に、スクリプトのコード行に設定されたブレークポイントは、パッケージ、またはパッケージ内のタスクやコンテナーに設定されたブレークポイントと統合されます。</span><span class="sxs-lookup"><span data-stu-id="a4f5a-110">At run time, the breakpoints set on lines of code in script are integrated with the breakpoints set on the package or the tasks and containers in the package.</span></span> <span data-ttu-id="a4f5a-111">デバッガーは、スクリプト内のブレークポイントから、パッケージ、タスク、またはコンテナーに設定されたブレークポイントまで実行できます。また、その逆の実行も可能です。</span><span class="sxs-lookup"><span data-stu-id="a4f5a-111">The debugger can run from a breakpoint in the script to a breakpoint set on the package, task, or container, and vice versa.</span></span> <span data-ttu-id="a4f5a-112">たとえば、 **OnPreExecute** イベントまたは **OnPostExecute** イベントを受け取ったときに発生するブレークの条件で、設定されたブレークポイントがパッケージにあり、スクリプト行にブレークポイントが設定されたスクリプト タスクがあるとします。</span><span class="sxs-lookup"><span data-stu-id="a4f5a-112">For example, a package might have breakpoints set on the break conditions that occur when the package receives the **OnPreExecute** and **OnPostExecute** events, and also have a Script task that has breakpoints on lines of its script.</span></span> <span data-ttu-id="a4f5a-113">この場合、パッケージは **OnPreExecute** イベントに関連付けられたブレークの条件で実行を中断し、スクリプト内のブレークポイントまで実行して、最終的に **OnPostExecute** イベントに関連付けられたブレークの条件まで実行できます。</span><span class="sxs-lookup"><span data-stu-id="a4f5a-113">In this scenario, the package can suspend execution on the break condition associated with the **OnPreExecute** event, run to the breakpoints in the script, and finally run to the break condition associated with the **OnPostExecute** event.</span></span>  
  
 <span data-ttu-id="a4f5a-114">スクリプト タスクとスクリプト コンポーネントのデバッグの詳細については、「 [スクリプト タスクのコーディングおよびデバッグ](../extending-packages-scripting/task/coding-and-debugging-the-script-task.md) 」および「 [スクリプト コンポーネントのコーディングおよびデバッグ](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4f5a-114">For more information about debugging the Script task and Script component, see [Coding and Debugging the Script Task](../extending-packages-scripting/task/coding-and-debugging-the-script-task.md) and [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).</span></span>  
  
### <a name="to-set-a-breakpoint-in-visual-studio-for-applications"></a><span data-ttu-id="a4f5a-115">Visual Studio for Applications でブレークポイントを設定するには</span><span class="sxs-lookup"><span data-stu-id="a4f5a-115">To set a breakpoint in Visual Studio for Applications</span></span>  
  
-   [<span data-ttu-id="a4f5a-116">スクリプト タスクとスクリプト コンポーネントにブレークポイントを設定してスクリプトをデバッグする</span><span class="sxs-lookup"><span data-stu-id="a4f5a-116">Debug a Script by Setting Breakpoints in a Script Task and Script Component</span></span>](../extending-packages-scripting/debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component.md)  
  
## <a name="see-also"></a><span data-ttu-id="a4f5a-117">参照</span><span class="sxs-lookup"><span data-stu-id="a4f5a-117">See Also</span></span>  
 [<span data-ttu-id="a4f5a-118">パッケージ開発のトラブルシューティング ツール</span><span class="sxs-lookup"><span data-stu-id="a4f5a-118">Troubleshooting Tools for Package Development</span></span>](troubleshooting-tools-for-package-development.md)  
  
  
