---
title: スクリプト タスクでのログ記録 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- SQL Server Integration Services packages, logs
- SSIS packages, logs
- logs [Integration Services], scripts
- Integration Services packages, logs
- Log method
- SSIS Script task, logs
- Script task [Integration Services], logs
- packages [Integration Services], logs
ms.assetid: 2e11fc15-df18-4309-bd2d-fc58aa4b9b7a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 61f7a46088de5df2765d860bd4a43e4872a1be6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715578"
---
# <a name="logging-in-the-script-task"></a><span data-ttu-id="289e0-102">スクリプト タスクでのログ記録</span><span class="sxs-lookup"><span data-stu-id="289e0-102">Logging in the Script Task</span></span>
  <span data-ttu-id="289e0-103">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] パッケージのログ記録を使用すると、実行の進行状況、結果、問題点などに関する詳細な情報を、あらかじめ定義されたイベントまたはユーザー定義のメッセージとして記録し、後で分析することができます。</span><span class="sxs-lookup"><span data-stu-id="289e0-103">The use of logging in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] packages lets you record detailed information about execution progress, results, and problems by recording predefined events or user-defined messages for later analysis.</span></span> <span data-ttu-id="289e0-104">スクリプト タスクでユーザー定義のデータをログ記録するには、`Dts` オブジェクトの <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="289e0-104">The Script task can use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method of the `Dts` object to log user-defined data.</span></span> <span data-ttu-id="289e0-105">ログ記録が有効で、 **[SSIS ログの構成]** ダイアログ ボックスの **[詳細]** タブでログ記録の対象として **[ScriptTaskLogEntry]** イベントが選択されている場合、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> メソッドを 1 回呼び出すと、そのタスク用に設定されたすべてのログ プロバイダーに対し、イベント情報が保存されます。</span><span class="sxs-lookup"><span data-stu-id="289e0-105">If logging is enabled, and the **ScriptTaskLogEntry** event is selected for logging on the **Details** tab of the **Configure SSIS Logs** dialog box, a single call to the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method stores the event information in all the log providers configured for the task.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="289e0-106">ログ記録はスクリプト タスクから直接実行できますが、ログ記録ではなくイベントを実装することを検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="289e0-106">Although you can perform logging directly from your Script task, you may want to consider implementing events rather than logging.</span></span> <span data-ttu-id="289e0-107">イベントを使用すると、イベント メッセージのログ記録を有効にできるだけでなく、既定またはユーザー定義のイベント ハンドラーによってイベントに応答することもできます。</span><span class="sxs-lookup"><span data-stu-id="289e0-107">When using events, not only can you enable the logging of event messages, but you can also respond to the event with default or user-defined event handlers.</span></span>  
  
 <span data-ttu-id="289e0-108">ログ記録の詳細については、「[Integration Services &#40;SSIS&#41; のログ記録](../../performance/integration-services-ssis-logging.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="289e0-108">For more information about logging, see [Integration Services &#40;SSIS&#41; Logging](../../performance/integration-services-ssis-logging.md).</span></span>  
  
## <a name="logging-example"></a><span data-ttu-id="289e0-109">ログ記録の例</span><span class="sxs-lookup"><span data-stu-id="289e0-109">Logging Example</span></span>  
 <span data-ttu-id="289e0-110">次の例は、処理された行数を表す値をログに記録する、スクリプト タスクのログ記録を示します。</span><span class="sxs-lookup"><span data-stu-id="289e0-110">The following example demonstrates logging from the Script task by logging a value that represents the number of rows processed.</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim rowsProcessed As Integer = 100  
    Dim emptyBytes(0) As Byte  
  
    Try  
        Dts.Log("Rows processed: " & rowsProcessed.ToString, _  
            0, _  
            emptyBytes)  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        'An error occurred.  
        Dts.Events.FireError(0, "Script Task Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class ScriptMain  
{  
  
    public void Main()  
        {  
            //  
            int rowsProcessed = 100;  
            byte[] emptyBytes = new byte[0];  
  
            try  
            {  
                Dts.Log("Rows processed: " + rowsProcessed.ToString(), 0, emptyBytes);  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                //An error occurred.  
                Dts.Events.FireError(0, "Script Task Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
        }  
```  
  
 <span data-ttu-id="289e0-111">}</span><span class="sxs-lookup"><span data-stu-id="289e0-111">}</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="289e0-112">外部リソース</span><span class="sxs-lookup"><span data-stu-id="289e0-112">External Resources</span></span>  
  
<span data-ttu-id="289e0-113">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="289e0-113">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="289e0-114">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="289e0-114">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="289e0-115">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="289e0-115">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="289e0-116">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="289e0-116">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="289e0-117">参照</span><span class="sxs-lookup"><span data-stu-id="289e0-117">See Also</span></span>  
 [<span data-ttu-id="289e0-118">Integration Services &#40;SSIS&#41; のログ記録</span><span class="sxs-lookup"><span data-stu-id="289e0-118">Integration Services &#40;SSIS&#41; Logging</span></span>](../../performance/integration-services-ssis-logging.md)  
  
  
