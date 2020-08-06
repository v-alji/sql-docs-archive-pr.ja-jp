---
title: プロセス実行タスク | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executeprocesstask.f1
helpviewer_keywords:
- Execute Process task [Integration Services]
ms.assetid: aca5a0b5-34a9-45bc-a234-8e63ea51a1ee
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c0db683d7c900e2554b3b856cbf68f7cfb1ca087
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640183"
---
# <a name="execute-process-task"></a><span data-ttu-id="ef75b-102">プロセス実行タスク</span><span class="sxs-lookup"><span data-stu-id="ef75b-102">Execute Process Task</span></span>
  <span data-ttu-id="ef75b-103">プロセス実行タスクでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージ ワークフローの一部として、アプリケーションまたはバッチ ファイルが実行されます。</span><span class="sxs-lookup"><span data-stu-id="ef75b-103">The Execute Process task runs an application or batch file as part of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package workflow.</span></span> <span data-ttu-id="ef75b-104">[!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] や [!INCLUDE[ofprword](../../includes/ofprword-md.md)]などの標準的なアプリケーションを開くためにプロセス実行タスクを使用することもできますが、一般に、このタスクはデータ ソースを処理対象とするビジネス アプリケーションやバッチ ファイルを実行する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="ef75b-104">Although you can use the Execute Process task to open any standard application, such as [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] or [!INCLUDE[ofprword](../../includes/ofprword-md.md)], you typically use it to run business applications or batch files that work against a data source.</span></span> <span data-ttu-id="ef75b-105">たとえば、プロセス実行タスクを使用して、圧縮されたテキスト ファイルを展開できます。</span><span class="sxs-lookup"><span data-stu-id="ef75b-105">For example, you can use the Execute Process task to expand a compressed text file.</span></span> <span data-ttu-id="ef75b-106">さらに、そのテキスト ファイルをパッケージ内のデータ フローのデータ ソースとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef75b-106">Then the package can use the text file as a data source for the data flow in the package.</span></span> <span data-ttu-id="ef75b-107">その他の例として、プロセス実行タスクを使用し、毎日の売り上げレポートを生成するカスタムの [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] アプリケーションを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="ef75b-107">As another example, you can use the Execute Process task to run a custom [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] application that generates a daily sales report.</span></span> <span data-ttu-id="ef75b-108">その後、このレポートをメール送信タスクに添付し、配信リストに転送できます。</span><span class="sxs-lookup"><span data-stu-id="ef75b-108">Then you can attach the report to a Send Mail task and forward the report to a distribution list.</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="ef75b-109">には、パッケージの実行など、ワークフロー操作を実行するその他のタスクが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ef75b-109">includes other tasks that perform workflow operations such as executing packages.</span></span> <span data-ttu-id="ef75b-110">詳細については、「 [パッケージ実行タスク](execute-package-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef75b-110">For more information, see [Execute Package Task](execute-package-task.md)</span></span>  
  
## <a name="custom-log-entries-available-on-the-execute-process-task"></a><span data-ttu-id="ef75b-111">プロセス実行タスクで使用できるカスタム ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="ef75b-111">Custom Log Entries Available on the Execute Process Task</span></span>  
 <span data-ttu-id="ef75b-112">次の表は、プロセス実行タスクのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="ef75b-112">The following table lists the custom log entries for the Execute Process task.</span></span> <span data-ttu-id="ef75b-113">詳しくは、「[Integration Services &#40;SSIS&#41; のログ記録](../performance/integration-services-ssis-logging.md)」と「[ログ記録用のカスタム メッセージ](../custom-messages-for-logging.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ef75b-113">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="ef75b-114">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="ef75b-114">Log entry</span></span>|<span data-ttu-id="ef75b-115">説明</span><span class="sxs-lookup"><span data-stu-id="ef75b-115">Description</span></span>|  
|---------------|-----------------|  
|`ExecuteProcessExecutingProcess`|<span data-ttu-id="ef75b-116">タスクで実行するように構成されているプロセスに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="ef75b-116">Provides information about the process that the task is configured to run.</span></span><br /><br /> <span data-ttu-id="ef75b-117">2 つのログ エントリが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="ef75b-117">Two log entries are written.</span></span> <span data-ttu-id="ef75b-118">1 つのエントリには、タスクで実行される実行可能ファイルの名前と場所が含まれ、その他のエントリは、実行可能ファイルの終了を記録します。</span><span class="sxs-lookup"><span data-stu-id="ef75b-118">One contains information about the name and location of the executable that the task runs, and the other entry records the exit from the executable.</span></span>|  
|`ExecuteProcessVariableRouting`|<span data-ttu-id="ef75b-119">実行可能ファイルの入力と出力にルーティングされる変数に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="ef75b-119">Provides information about which variables are routed to the input and outputs of the executable.</span></span> <span data-ttu-id="ef75b-120">ログ エントリは、stdin (入力)、stdout (出力)、および stderr (エラー出力) に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="ef75b-120">Log entries are written for stdin (the input), stdout (the output), and stderr (the error output).</span></span>|  
  
## <a name="configuration-of-the-execute-process-task"></a><span data-ttu-id="ef75b-121">プロセス実行タスクの構成</span><span class="sxs-lookup"><span data-stu-id="ef75b-121">Configuration of the Execute Process Task</span></span>  
 <span data-ttu-id="ef75b-122">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="ef75b-122">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="ef75b-123">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef75b-123">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="ef75b-124">[[プロセス実行タスク エディター] &#40;[全般] ページ&#41;](../general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="ef75b-124">[Execute Process Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md)</span></span>  
  
-   <span data-ttu-id="ef75b-125">[[プロセス実行タスク エディター] ([処理] ページ)](../execute-process-task-editor-process-page.md)</span><span class="sxs-lookup"><span data-stu-id="ef75b-125">[Execute Process Task Editor &#40;Process Page&#41;](../execute-process-task-editor-process-page.md)</span></span>  
  
 <span data-ttu-id="ef75b-126">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef75b-126">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="ef75b-127">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="ef75b-127">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
### <a name="property-settings"></a><span data-ttu-id="ef75b-128">プロパティの設定</span><span class="sxs-lookup"><span data-stu-id="ef75b-128">Property Settings</span></span>  
 <span data-ttu-id="ef75b-129">プロセス実行タスクがカスタム アプリケーションを実行するとき、アプリケーションには、次のいずれかまたは両方の方法で入力が提供されます。</span><span class="sxs-lookup"><span data-stu-id="ef75b-129">When the Execute Process task runs a custom application, the task provides input to the application through one or both of the following methods:</span></span>  
  
-   <span data-ttu-id="ef75b-130">**StandardInputVariable** プロパティの設定で指定された変数。</span><span class="sxs-lookup"><span data-stu-id="ef75b-130">A variable that you specify in the **StandardInputVariable** property setting.</span></span> <span data-ttu-id="ef75b-131">変数の詳細については、「[Integration Services &#40;SSIS&#41; の変数](../integration-services-ssis-variables.md)」と「[パッケージで変数を使用する](../use-variables-in-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef75b-131">For more information about variables, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
-   <span data-ttu-id="ef75b-132">**Arguments** プロパティの設定で指定された引数。</span><span class="sxs-lookup"><span data-stu-id="ef75b-132">An argument that you specify in the **Arguments** property setting.</span></span> <span data-ttu-id="ef75b-133">たとえば文書を Word で開く場合、引数で .doc ファイルの名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ef75b-133">(For example, if the task opens a document in Word, the argument can name the .doc file.)</span></span>  
  
 <span data-ttu-id="ef75b-134">1 回のプロセス実行タスクで複数の引数をカスタム アプリケーションに渡すには、それぞれの引数を空白で区切って指定します。</span><span class="sxs-lookup"><span data-stu-id="ef75b-134">To pass multiple arguments to a custom application in one Execute Process task, use spaces to delimit the arguments.</span></span> <span data-ttu-id="ef75b-135">引数そのものに空白を含めることはできません。空白を含めた場合、タスクは実行されません。</span><span class="sxs-lookup"><span data-stu-id="ef75b-135">An argument cannot include a space; otherwise, the task will not run.</span></span> <span data-ttu-id="ef75b-136">変数の値を引数として渡す際には、式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef75b-136">You can use an expression to pass a variable value as the argument.</span></span> <span data-ttu-id="ef75b-137">次の例では、式を使って 2 つの変数の値を空白で区切り、引数として渡します。</span><span class="sxs-lookup"><span data-stu-id="ef75b-137">In the following example, the expression passes two variable values as arguments, and uses a space to delimit the arguments:</span></span>  
  
 `@variable1 + " " + @variable2`  
  
 <span data-ttu-id="ef75b-138">プロセス実行タスクの各種プロパティを設定する際にも、式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef75b-138">You can use an expression to set various Execute Process task properties.</span></span>  
  
 <span data-ttu-id="ef75b-139">**Standardinputvariable**プロパティを使用して入力を提供するようにプロセス実行タスクを構成する場合は、 `Console.ReadLine` アプリケーションからメソッドを呼び出して入力を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="ef75b-139">When you use the **StandardInputVariable** property to configure the Execute Process task to provide input, call the `Console.ReadLine` method from the application to read the input.</span></span> <span data-ttu-id="ef75b-140">詳細については、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] クラス ライブラリの「[Console.ReadLine メソッド](https://go.microsoft.com/fwlink/?LinkId=129201)」トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef75b-140">For more information, see [Console.ReadLine Method](https://go.microsoft.com/fwlink/?LinkId=129201)the topic, , in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Class Library.</span></span>  
  
 <span data-ttu-id="ef75b-141">**Arguments** プロパティを使用して入力を提供するようにプロセス実行タスクを構成した場合は、次のいずれかの手順を実行して、引数を取得します。</span><span class="sxs-lookup"><span data-stu-id="ef75b-141">When you use the **Arguments** property to configure the Execute Process task to provide input, do one of the following steps to obtain the arguments:</span></span>  
  
-   <span data-ttu-id="ef75b-142">Microsoft Visual Basic を使用してアプリケーションを作成する場合は、`My.Application.CommandLineArgs` プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="ef75b-142">If you use Microsoft Visual Basic to write the application, set the `My.Application.CommandLineArgs` property.</span></span> <span data-ttu-id="ef75b-143">次の例では、`My.Application.CommandLineArgs` プロパティを使用して、2 つの引数を取得しています。</span><span class="sxs-lookup"><span data-stu-id="ef75b-143">The following example sets the `My.Application.CommandLineArgs` property is to retrieve two arguments:</span></span>  
  
    ```  
    Dim variable1 As String = My.Application.CommandLineArgs.Item(0)  
    Dim variable2 As String = My.Application.CommandLineArgs.Item(1)   
    ```  
  
     <span data-ttu-id="ef75b-144">詳細については、 [のリファレンスで、](https://go.microsoft.com/fwlink/?LinkId=129200)My.Application.CommandLineArgs プロパティ [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef75b-144">For more information, see the topic, [My.Application.CommandLineArgs Property](https://go.microsoft.com/fwlink/?LinkId=129200), in the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] reference.</span></span>  
  
-   <span data-ttu-id="ef75b-145">Microsoft Visual C# を使用してアプリケーションを作成する場合は、`Main` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="ef75b-145">If you use Microsoft Visual C# to write the applicate, use the `Main` method.</span></span>  
  
     <span data-ttu-id="ef75b-146">詳細については、『C# プログラミング ガイド』の「 [コマンド ライン引数 (C# プログラミング ガイド)](https://go.microsoft.com/fwlink/?LinkId=129406)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef75b-146">For more information, see the topic, [Command-Line Arguments (C# Programming Guide)](https://go.microsoft.com/fwlink/?LinkId=129406), in the C# Programming Guide.</span></span>  
  
 <span data-ttu-id="ef75b-147">プロセス実行タスクには、 **StandardOutputVariable** プロパティおよび **StandardErrorVariable** プロパティがあります。それぞれ、アプリケーションの標準出力とエラー出力を取り込むための変数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ef75b-147">The Execute Process task also includes the **StandardOutputVariable** and **StandardErrorVariable** properties for specifying the variables that consume the standard output and error output of the application, respectively.</span></span>  
  
 <span data-ttu-id="ef75b-148">さらに、プロセス実行タスクを構成することにより、作業ディレクトリ、タイムアウト時間、または実行可能ファイルが正常に実行されたことを示す値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ef75b-148">Additionally, you can configure the Execute Process task to specify a working directory, a time-out period, or a value to indicate that the executable ran successfully.</span></span> <span data-ttu-id="ef75b-149">また、実行可能ファイルのリターン コードが成功を示す値と一致しない場合、または指定された場所で実行可能ファイルが見つからない場合に、失敗するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="ef75b-149">The task can also be configured to fail if the return code of the executable does not match the value that indicates success, or if the executable is not found at the specified location.</span></span>  
  
## <a name="programmatic-configuration-of-the-execute-process-task"></a><span data-ttu-id="ef75b-150">プログラムによるプロセス実行タスクの構成</span><span class="sxs-lookup"><span data-stu-id="ef75b-150">Programmatic Configuration of the Execute Process Task</span></span>  
 <span data-ttu-id="ef75b-151">プログラムによってこれらのプロパティを設定する方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef75b-151">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ExecuteProcess.ExecuteProcess>  
  
## <a name="see-also"></a><span data-ttu-id="ef75b-152">参照</span><span class="sxs-lookup"><span data-stu-id="ef75b-152">See Also</span></span>  
 <span data-ttu-id="ef75b-153">[Integration Services タスク](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="ef75b-153">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="ef75b-154">制御フロー</span><span class="sxs-lookup"><span data-stu-id="ef75b-154">Control Flow</span></span>](control-flow.md)  
  
  
