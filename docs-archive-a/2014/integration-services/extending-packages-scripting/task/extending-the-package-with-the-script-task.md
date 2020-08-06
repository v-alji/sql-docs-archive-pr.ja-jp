---
title: スクリプト タスクによるパッケージの拡張 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- scripts [Integration Services]
- SSIS Script task
- tasks [Integration Services], scripts
- Script task [Integration Services], about Script task
- scripts [Integration Services], about Script task with packages
- SSIS Script task, about Script task
ms.assetid: 911e6d26-a6fd-4fc3-a111-bf5f048e9bff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5f1a265b01a898cdc87bdf9df6cb67399879061b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715590"
---
# <a name="extending-the-package-with-the-script-task"></a><span data-ttu-id="4ae49-102">スクリプト タスクによるパッケージの拡張</span><span class="sxs-lookup"><span data-stu-id="4ae49-102">Extending the Package with the Script Task</span></span>
  <span data-ttu-id="4ae49-103">スクリプト タスクを使用すると、カスタム コードを [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic または [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Visual C# で記述し、パッケージの実行時にコンパイル、実行することにより、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[msCoName](../../../includes/msconame-md.md)] パッケージのランタイム機能を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="4ae49-103">The Script task extends the run-time capabilities of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] packages with custom code written in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# that is compiled and executed at package run time.</span></span> <span data-ttu-id="4ae49-104">スクリプト タスクは、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] に含まれているタスクが十分に要件を満たしていない場合に、カスタム ランタイム タスクの開発を単純化します。</span><span class="sxs-lookup"><span data-stu-id="4ae49-104">The Script task simplifies the development of a custom run-time task when the tasks included with [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] do not fully satisfy your requirements.</span></span> <span data-ttu-id="4ae49-105">必要なすべてのインフラストラクチャ コードがスクリプト タスクによって自動生成されるため、カスタム処理を実行するために必要なコードの記述に集中できます。</span><span class="sxs-lookup"><span data-stu-id="4ae49-105">The Script task writes all the required infrastructure code for you, letting you focus exclusively on the code that is required for your custom processing.</span></span>  
  
 <span data-ttu-id="4ae49-106">スクリプト タスクは、スクリプト環境で公開される <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> クラスのインスタンスであるグローバル オブジェクト `Dts` を介して、内部のパッケージとやり取りします。</span><span class="sxs-lookup"><span data-stu-id="4ae49-106">A Script task interacts with the containing package through the global `Dts` object, an instance of the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> class that is exposed in the scripting environment.</span></span> <span data-ttu-id="4ae49-107">スクリプト タスク内でコードを記述して、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 変数に格納された値を変更できます。その後、更新した変数の値をパッケージで使用して、ワークフローのパスを決定できます。</span><span class="sxs-lookup"><span data-stu-id="4ae49-107">You can write code in a Script task that modifies the values stored in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] variables; later, the package can use those updated values to determine the path of its workflow.</span></span> <span data-ttu-id="4ae49-108">また、カスタム アセンブリだけでなく、[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 名前空間および [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] クラス ライブラリを使用して、スクリプト タスクに独自の機能を実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="4ae49-108">The Script task can also use the [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] namespace and the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] class library, as well as custom assemblies, to implement custom functionality.</span></span>  
  
 <span data-ttu-id="4ae49-109">スクリプト タスクおよびそれによって生成されるインフラストラクチャ コードを活用すれば、カスタム タスクを開発するための手順を大幅に簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="4ae49-109">The Script task and the infrastructure code that it generates for you simplify significantly the process of developing a custom task.</span></span> <span data-ttu-id="4ae49-110">スクリプト タスクの動作のしくみを理解するため、「[カスタム タスクの開発](../../extending-packages-custom-objects/task/developing-a-custom-task.md)」のセクションを参照して、カスタム タスクの開発手順を理解しておくと役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="4ae49-110">However, to understand how the Script task works, you may find it useful to read the section [Developing a Custom Task](../../extending-packages-custom-objects/task/developing-a-custom-task.md) to understand the steps that are involved in developing a custom task.</span></span>  
  
 <span data-ttu-id="4ae49-111">作成したタスクを複数のパッケージで再利用する予定がある場合は、スクリプト タスクではなく、カスタム タスクを開発することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="4ae49-111">If you are creating a task that you plan to reuse in multiple packages, you should consider developing a custom task instead of using the Script task.</span></span> <span data-ttu-id="4ae49-112">詳細については、「[スクリプティング ソリューションとカスタム オブジェクトとの比較](../comparing-scripting-solutions-and-custom-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ae49-112">For more information, see [Comparing Scripting Solutions and Custom Objects](../comparing-scripting-solutions-and-custom-objects.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4ae49-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4ae49-113">In This Section</span></span>  
 <span data-ttu-id="4ae49-114">次のトピックでは、スクリプト タスクの詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="4ae49-114">The following topics provide more information about the Script task.</span></span>  
  
 [<span data-ttu-id="4ae49-115">スクリプト タスク エディターでのスクリプト タスクの構成</span><span class="sxs-lookup"><span data-stu-id="4ae49-115">Configuring the Script Task in the Script Task Editor</span></span>](configuring-the-script-task-in-the-script-task-editor.md)  
 <span data-ttu-id="4ae49-116">**[スクリプト タスク エディター]** で構成したプロパティがスクリプト タスク コードの機能やパフォーマンスに及ぼす影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="4ae49-116">Explains how the properties that you configure in the **Script Task Editor** affect the capabilities and the performance of the code in the Script task.</span></span>  
  
 [<span data-ttu-id="4ae49-117">スクリプト タスクのコーディングおよびデバッグ</span><span class="sxs-lookup"><span data-stu-id="4ae49-117">Coding and Debugging the Script Task</span></span>](../../control-flow/script-task.md)  
 <span data-ttu-id="4ae49-118">スクリプト タスクに含まれるスクリプトを [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) を使用して開発する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4ae49-118">Explains how to use [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) to develop the scripts that are contained in the Script task.</span></span>  
  
 [<span data-ttu-id="4ae49-119">スクリプト タスクでの変数の使用</span><span class="sxs-lookup"><span data-stu-id="4ae49-119">Using Variables in the Script Task</span></span>](using-variables-in-the-script-task.md)  
 <span data-ttu-id="4ae49-120"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> プロパティを介して変数を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4ae49-120">Explains how to use variables through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property.</span></span>  
  
 [<span data-ttu-id="4ae49-121">スクリプト タスクでのデータ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="4ae49-121">Connecting to Data Sources in the Script Task</span></span>](connecting-to-data-sources-in-the-script-task.md)  
 <span data-ttu-id="4ae49-122"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> プロパティを介して接続を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4ae49-122">Explains how to use connections through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> property.</span></span>  
  
 [<span data-ttu-id="4ae49-123">スクリプト タスクでのイベントの発生</span><span class="sxs-lookup"><span data-stu-id="4ae49-123">Raising Events in the Script Task</span></span>](raising-events-in-the-script-task.md)  
 <span data-ttu-id="4ae49-124"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> プロパティを介してイベントを発生させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4ae49-124">Explains how to raise events through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> property.</span></span>  
  
 [<span data-ttu-id="4ae49-125">スクリプト タスクでのログ記録</span><span class="sxs-lookup"><span data-stu-id="4ae49-125">Logging in the Script Task</span></span>](logging-in-the-script-task.md)  
 <span data-ttu-id="4ae49-126"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> メソッドを介して情報をログに記録する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4ae49-126">Explains how to log information through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method.</span></span>  
  
 [<span data-ttu-id="4ae49-127">スクリプト タスクから結果を返す</span><span class="sxs-lookup"><span data-stu-id="4ae49-127">Returning Results from the Script Task</span></span>](returning-results-from-the-script-task.md)  
 <span data-ttu-id="4ae49-128"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> および <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> プロパティを介して結果を返す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4ae49-128">Explains how to return results through the property <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> and the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> property.</span></span>  
  
 [<span data-ttu-id="4ae49-129">スクリプト タスクの例</span><span class="sxs-lookup"><span data-stu-id="4ae49-129">Script Task Examples</span></span>](../../extending-packages-scripting-task-examples/script-task-examples.md)  
 <span data-ttu-id="4ae49-130">スクリプト タスクの使用方法を示す簡単な例をいくつか提供します。</span><span class="sxs-lookup"><span data-stu-id="4ae49-130">Provides simple examples that demonstrate several possible uses for a Script task.</span></span>  
  
<span data-ttu-id="4ae49-131">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="4ae49-131">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="4ae49-132">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] が提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ae49-132">For the latest downloads, articles, samples, and videos from [!INCLUDE[msCoName](../../../includes/msconame-md.md)], as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="4ae49-133">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="4ae49-133">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="4ae49-134">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="4ae49-134">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ae49-135">参照</span><span class="sxs-lookup"><span data-stu-id="4ae49-135">See Also</span></span>  
 <span data-ttu-id="4ae49-136">[スクリプトタスク](../../control-flow/script-task.md) </span><span class="sxs-lookup"><span data-stu-id="4ae49-136">[Script Task](../../control-flow/script-task.md) </span></span>  
 [<span data-ttu-id="4ae49-137">スクリプト タスクとスクリプト コンポーネントの比較</span><span class="sxs-lookup"><span data-stu-id="4ae49-137">Comparing the Script Task and the Script Component</span></span>](../../extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
  
  
