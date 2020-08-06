---
title: スクリプト タスクによるパフォーマンス カウンターの監視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- performance counters [Integration Services]
- SSIS Script task, performance counters
- custom performance counters [Integration Services]
- Script task [Integration Services], examples
- Script task [Integration Services], performance counters
- counters [Integration Services]
ms.assetid: 86609bf1-cae6-435e-a58d-41bdfc521e94
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 143e11ff966eb11961aa15073a503522c4b9c86b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736571"
---
# <a name="monitoring-performance-counters-with-the-script-task"></a><span data-ttu-id="aace5-102">スクリプト タスクによるパフォーマンス カウンターの監視</span><span class="sxs-lookup"><span data-stu-id="aace5-102">Monitoring Performance Counters with the Script Task</span></span>
  <span data-ttu-id="aace5-103">システム管理者は、大容量のデータ上で複雑な変換を実行する [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのパフォーマンスを監視する必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="aace5-103">Administrators may need to monitor the performance of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages that perform complex transformations on large amounts of data.</span></span> <span data-ttu-id="aace5-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の **System.Diagnostics** 名前空間には、既存のパフォーマンス カウンターを使用したり、ユーザー独自のパフォーマンス カウンターを作成するためのクラスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="aace5-104">The **System.Diagnostics** namespace of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] provides classes for using existing performance counters and for creating your own performance counters.</span></span>  
  
 <span data-ttu-id="aace5-105">パフォーマンス カウンターはアプリケーションのパフォーマンス情報を格納するので、これを使用して、時間経過に伴うソフトウェアのパフォーマンスを分析できます。</span><span class="sxs-lookup"><span data-stu-id="aace5-105">Performance counters store application performance information that you can use to analyze the performance of software over time.</span></span> <span data-ttu-id="aace5-106">パフォーマンス カウンターは **[パフォーマンス モニター]** ツールを使用して、ローカルまたはリモートで監視できます。</span><span class="sxs-lookup"><span data-stu-id="aace5-106">Performance counters can be monitored locally or remotely by using the **Performance Monitor** tool.</span></span> <span data-ttu-id="aace5-107">パフォーマンス カウンターの値を変数に格納して、後でパッケージ内で制御フローを分岐するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="aace5-107">You can store the values of performance counters in variables for later control flow branching in the package.</span></span>  
  
 <span data-ttu-id="aace5-108">パフォーマンス カウンターを使用する代わりに、`Dts` オブジェクトの <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A> プロパティを介して、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> イベントを発生させることができます。</span><span class="sxs-lookup"><span data-stu-id="aace5-108">As an alternative to using performance counters, you can raise the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A> event through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> property of the `Dts` object.</span></span> <span data-ttu-id="aace5-109"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A> イベントは、進捗状況および完了した割合に関する情報を、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ランタイムに返します。</span><span class="sxs-lookup"><span data-stu-id="aace5-109">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A> event returns both incremental progress and percentage complete information to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] runtime.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aace5-110">複数のパッケージでより簡単に再利用できるタスクを作成する場合は、このスクリプト タスク サンプルのコードを基にした、カスタム タスクの作成を検討してください。</span><span class="sxs-lookup"><span data-stu-id="aace5-110">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="aace5-111">詳細については、「 [カスタム タスクの開発](../extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aace5-111">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="aace5-112">説明</span><span class="sxs-lookup"><span data-stu-id="aace5-112">Description</span></span>  
 <span data-ttu-id="aace5-113">次の例では、カスタム パフォーマンス カウンターを作成し、カウンターの値を増やします。</span><span class="sxs-lookup"><span data-stu-id="aace5-113">The following example creates a custom performance counter and increments the counter.</span></span> <span data-ttu-id="aace5-114">最初に、パフォーマンス カウンターが既に存在しているかどうかを判別します。</span><span class="sxs-lookup"><span data-stu-id="aace5-114">First, the example determines whether the performance counter already exists.</span></span> <span data-ttu-id="aace5-115">パフォーマンス カウンターが作成されていない場合、スクリプトは `Create` オブジェクトの `PerformanceCounterCategory` メソッドを呼び出してパフォーマンス カウンターを作成します。</span><span class="sxs-lookup"><span data-stu-id="aace5-115">If the performance counter has not been created, the script calls the `Create` method of the `PerformanceCounterCategory` object to create it.</span></span> <span data-ttu-id="aace5-116">パフォーマンス カウンターが作成されたら、スクリプトはそのカウンターの値を増やします。</span><span class="sxs-lookup"><span data-stu-id="aace5-116">After the performance counter has been created, the script increments the counter.</span></span> <span data-ttu-id="aace5-117">最後に、この例ではベスト プラクティスに従って、パフォーマンス カウンターが不要になると、そのカウンターに対して `Close` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="aace5-117">Finally, the example follows the best practice of calling the `Close` method on the performance counter when it is no longer needed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aace5-118">パフォーマンス カウンター カテゴリとパフォーマンス カウンターを新しく作成するには、管理権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="aace5-118">Creating a new performance counter category and performance counter requires administrative rights.</span></span> <span data-ttu-id="aace5-119">また、新しいカテゴリとカウンターは、作成後もコンピューターに保存されます。</span><span class="sxs-lookup"><span data-stu-id="aace5-119">Also, the new category and counter persist on the computer after creation.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="aace5-120">このスクリプト タスクの例を構成するには</span><span class="sxs-lookup"><span data-stu-id="aace5-120">To configure this Script Task example</span></span>  
  
-   <span data-ttu-id="aace5-121">`Imports`コード内でステートメントを使用して、 **System. Diagnostics**名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="aace5-121">Use an `Imports` statement in your code to import the **System.Diagnostics** namespace.</span></span>  
  
### <a name="example-code"></a><span data-ttu-id="aace5-122">コード例</span><span class="sxs-lookup"><span data-stu-id="aace5-122">Example Code</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim myCounter As PerformanceCounter  
  
    Try  
        'Create the performance counter if it does not already exist.  
        If Not _  
        PerformanceCounterCategory.Exists("TaskExample") Then  
            PerformanceCounterCategory.Create("TaskExample", _  
                "Task Performance Counter Example", "Iterations", _  
                "Number of times this task has been called.")  
        End If  
  
        'Initialize the performance counter.  
        myCounter = New PerformanceCounter("TaskExample", _  
            "Iterations", String.Empty, False)  
  
        'Increment the performance counter.  
        myCounter.Increment()  
  
         myCounter.Close()  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, _  
            "Task Performance Counter Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
  
public class ScriptMain  
{  
  
public void Main()  
        {  
  
            PerformanceCounter myCounter;  
  
            try  
            {  
                //Create the performance counter if it does not already exist.  
                if (!PerformanceCounterCategory.Exists("TaskExample"))  
                {  
                    PerformanceCounterCategory.Create("TaskExample", "Task Performance Counter Example", "Iterations", "Number of times this task has been called.");  
                }  
  
                //Initialize the performance counter.  
                myCounter = new PerformanceCounter("TaskExample", "Iterations", String.Empty, false);  
  
                //Increment the performance counter.  
                myCounter.Increment();  
  
                myCounter.Close();  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                Dts.Events.FireError(0, "Task Performance Counter Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
  
```  
  
<span data-ttu-id="aace5-123">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="aace5-123">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="aace5-124">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="aace5-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="aace5-125">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="aace5-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="aace5-126">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="aace5-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
