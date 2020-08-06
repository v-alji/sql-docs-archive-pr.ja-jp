---
title: スクリプト タスクでのイベントの発生 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- events [Integration Services], scripts
- warnings [Integration Services]
- SSIS events, scripts
- errors [Integration Services], events
- SSIS Script task, events
- Events property
- Script task [Integration Services], events
ms.assetid: 21ea07d1-e267-4fb1-a6cc-82c95a39beae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e20a276b91e434b6915cfb218eba17c07acd6544
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715574"
---
# <a name="raising-events-in-the-script-task"></a><span data-ttu-id="d214a-102">スクリプト タスクでのイベントの発生</span><span class="sxs-lookup"><span data-stu-id="d214a-102">Raising Events in the Script Task</span></span>
  <span data-ttu-id="d214a-103">イベントは、エラーや警告、タスクの進行状況や状態などのその他の情報を、親パッケージにレポートする方法を提供するものです。</span><span class="sxs-lookup"><span data-stu-id="d214a-103">Events provide a way to report errors, warnings, and other information, such as task progress or status, to the containing package.</span></span> <span data-ttu-id="d214a-104">パッケージには、イベントの通知機能を管理するためのイベント ハンドラーがあります。</span><span class="sxs-lookup"><span data-stu-id="d214a-104">The package provides event handlers for managing event notifications.</span></span> <span data-ttu-id="d214a-105">スクリプト タスクは、`Dts` オブジェクトの <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> プロパティに対してメソッドを呼び出して、イベントを発生させることができます。</span><span class="sxs-lookup"><span data-stu-id="d214a-105">The Script task can raise events by calling methods on the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> property of the `Dts` object.</span></span> <span data-ttu-id="d214a-106">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] パッケージのイベントの処理の詳細については、「[Integration Services &#40;SSIS&#41; のイベント ハンドラー](../../integration-services-ssis-event-handlers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d214a-106">For more information about how [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] packages handle events, see [Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md).</span></span>  
  
 <span data-ttu-id="d214a-107">イベントは、パッケージ内で有効な任意のログ プロバイダーに記録できます。</span><span class="sxs-lookup"><span data-stu-id="d214a-107">Events can be logged to any log provider that is enabled in the package.</span></span> <span data-ttu-id="d214a-108">ログ プロバイダーは、イベントに関する情報をデータ ストアに保存します。</span><span class="sxs-lookup"><span data-stu-id="d214a-108">Log providers store information about events in a data store.</span></span> <span data-ttu-id="d214a-109">スクリプト タスクは、イベントを発生させずに <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> メソッドを使用して、情報をログ プロバイダーに記録することもできます。</span><span class="sxs-lookup"><span data-stu-id="d214a-109">The Script task can also use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method to log information to a log provider without raising an event.</span></span> <span data-ttu-id="d214a-110"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> メソッドの使用方法の詳細については、「[スクリプト タスクでのログ記録](logging-in-the-script-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d214a-110">For more information about how to use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method, see [Logging in the Script Task](logging-in-the-script-task.md).</span></span>  
  
 <span data-ttu-id="d214a-111">イベントを発生させるには、スクリプト タスクは <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> プロパティによって公開されるメソッドのいずれかを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d214a-111">To raise an event, the Script task calls one of the methods exposed by the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> property.</span></span> <span data-ttu-id="d214a-112">次の表に、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> プロパティにより公開されているメソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="d214a-112">The following table lists the methods exposed by the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> property.</span></span>  
  
|<span data-ttu-id="d214a-113">Event</span><span class="sxs-lookup"><span data-stu-id="d214a-113">Event</span></span>|<span data-ttu-id="d214a-114">説明</span><span class="sxs-lookup"><span data-stu-id="d214a-114">Description</span></span>|  
|-----------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A>|<span data-ttu-id="d214a-115">パッケージ内でユーザー定義のカスタム イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="d214a-115">Raises a user-defined custom event in the package.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A>|<span data-ttu-id="d214a-116">パッケージにエラー条件を通知します。</span><span class="sxs-lookup"><span data-stu-id="d214a-116">Informs the package of an error condition.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireInformation%2A>|<span data-ttu-id="d214a-117">ユーザーに情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="d214a-117">Provides information to the user.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A>|<span data-ttu-id="d214a-118">タスクの進行状況をパッケージに通知します。</span><span class="sxs-lookup"><span data-stu-id="d214a-118">Informs the package of the progress of the task.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireQueryCancel%2A>|<span data-ttu-id="d214a-119">パッケージがタスクを途中でシャットダウンする必要があるかどうかを示す値を返します。</span><span class="sxs-lookup"><span data-stu-id="d214a-119">Returns a value that indicates whether the package needs the task to shut down prematurely.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A>|<span data-ttu-id="d214a-120">エラー条件ではないが、タスクがユーザーに通知する正当な理由がある状態であることをパッケージに通知します。</span><span class="sxs-lookup"><span data-stu-id="d214a-120">Informs the package that the task is in a state that warrants user notification, but is not an error condition.</span></span>|  
  
## <a name="events-example"></a><span data-ttu-id="d214a-121">イベントの例</span><span class="sxs-lookup"><span data-stu-id="d214a-121">Events Example</span></span>  
 <span data-ttu-id="d214a-122">次の例では、スクリプト タスク内でイベントを発生させる方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d214a-122">The following example demonstrates how to raise events from within the Script task.</span></span> <span data-ttu-id="d214a-123">この例では、ネイティブ Windows API 関数を使用して、インターネット接続が使用できるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="d214a-123">The example uses a native Windows API function to determine whether an Internet connection is available.</span></span> <span data-ttu-id="d214a-124">接続が使用できない場合、エラーを発生させます。</span><span class="sxs-lookup"><span data-stu-id="d214a-124">If no connection is available, it raises an error.</span></span> <span data-ttu-id="d214a-125">使用されているモデム接続が切断される可能性がある場合、この例では警告が発生します。</span><span class="sxs-lookup"><span data-stu-id="d214a-125">If a potentially volatile modem connection is in use, the example raises a warning.</span></span> <span data-ttu-id="d214a-126">それ以外の場合は、インターネット接続が検出されたことを示す情報メッセージを返します。</span><span class="sxs-lookup"><span data-stu-id="d214a-126">Otherwise, it returns an informational message that an Internet connection has been detected.</span></span>  
  
```vb  
Private Declare Function InternetGetConnectedState Lib "wininet" _  
    (ByRef dwFlags As Long, ByVal dwReserved As Long) As Long  
  
Private Enum ConnectedStates  
    LAN = &H2  
    Modem = &H1  
    Proxy = &H4  
    Offline = &H20  
    Configured = &H40  
    RasInstalled = &H10  
End Enum  
  
Public Sub Main()  
  
    Dim dwFlags As Long  
    Dim connectedState As Long  
    Dim fireAgain as Boolean  
  
    connectedState = InternetGetConnectedState(dwFlags, 0)  
  
    If connectedState <> 0 Then  
        If (dwFlags And ConnectedStates.Modem) = ConnectedStates.Modem Then  
            Dts.Events.FireWarning(0, "Script Task Example", _  
                "Volatile Internet connection detected.", String.Empty, 0)  
        Else  
            Dts.Events.FireInformation(0, "Script Task Example", _  
                "Internet connection detected.", String.Empty, 0, fireAgain)  
        End If  
    Else  
        ' If not connected to the Internet, raise an error.  
        Dts.Events.FireError(0, "Script Task Example", _  
            "Internet connection not available.", String.Empty, 0)  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Windows.Forms;  
using System.Runtime.InteropServices;  
  
public class ScriptMain  
{  
  
[DllImport("wininet")]  
        private extern static long InternetGetConnectedState(ref long dwFlags, long dwReserved);  
  
        private enum ConnectedStates  
        {  
            LAN = 0x2,  
            Modem = 0x1,  
            Proxy = 0x4,  
            Offline = 0x20,  
            Configured = 0x40,  
            RasInstalled = 0x10  
        };  
  
        public void Main()  
        {  
            //  
            long dwFlags = 0;  
            long connectedState;  
            bool fireAgain = true;  
            int state;  
  
            connectedState = InternetGetConnectedState(ref dwFlags, 0);  
            state = (int)ConnectedStates.Modem;  
            if (connectedState != 0)  
            {  
                if ((dwFlags & state) == state)  
                {  
                    Dts.Events.FireWarning(0, "Script Task Example", "Volatile Internet connection detected.", String.Empty, 0);  
                }  
                else  
                {  
                    Dts.Events.FireInformation(0, "Script Task Example", "Internet connection detected.", String.Empty, 0, ref fireAgain);  
                }  
            }  
            else  
            {  
                // If not connected to the Internet, raise an error.  
                Dts.Events.FireError(0, "Script Task Example", "Internet connection not available.", String.Empty, 0);  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
```  
  
<span data-ttu-id="d214a-127">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="d214a-127">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="d214a-128">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d214a-128">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="d214a-129">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="d214a-129">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="d214a-130">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="d214a-130">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d214a-131">参照</span><span class="sxs-lookup"><span data-stu-id="d214a-131">See Also</span></span>  
 <span data-ttu-id="d214a-132">[Integration Services &#40;SSIS&#41; のイベント ハンドラー](../../integration-services-ssis-event-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="d214a-132">[Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md) </span></span>  
 [<span data-ttu-id="d214a-133">パッケージにイベント ハンドラーを追加する</span><span class="sxs-lookup"><span data-stu-id="d214a-133">Add an Event Handler to a Package</span></span>](../../add-an-event-handler-to-a-package.md)  
  
  
