---
title: スクリプト タスクによるリモート プライベート メッセージ キューへの送信 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], remote private message queues
- Message Queue task [Integration Services]
- Script task [Integration Services], examples
ms.assetid: 636314fd-d099-45cd-8bb4-f730d0a06739
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 308815293dfc41f0a0ac60c21ce7f561a5e7f660
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716417"
---
# <a name="sending-to-a-remote-private-message-queue-with-the-script-task"></a><span data-ttu-id="6c84e-102">スクリプト タスクによるリモート プライベート メッセージ キューへの送信</span><span class="sxs-lookup"><span data-stu-id="6c84e-102">Sending to a Remote Private Message Queue with the Script Task</span></span>
  <span data-ttu-id="6c84e-103">メッセージ キュー (MSMQ) では、開発者がメッセージを送受信することにより、アプリケーション プログラムとすばやく確実に通信できます。</span><span class="sxs-lookup"><span data-stu-id="6c84e-103">Message Queuing (also known as MSMQ) makes it easy for developers to communicate with application programs quickly and reliably by sending and receiving messages.</span></span> <span data-ttu-id="6c84e-104">メッセージ キューは、ローカル コンピューターまたはリモート コンピューターに存在し、パブリックであることも、プライベートであることもあります。</span><span class="sxs-lookup"><span data-stu-id="6c84e-104">A message queue may be located on the local computer or a remote computer, and may be public or private.</span></span> <span data-ttu-id="6c84e-105">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の MSMQ 接続マネージャーとメッセージ キュー タスクでは、リモート コンピューター上のプライベート キューへの送信はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="6c84e-105">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], the MSMQ connection manager and Message Queue task do not support sending to a private queue on a remote computer.</span></span> <span data-ttu-id="6c84e-106">ただし、スクリプト タスクを使用することにより、リモート プライベート キューにメッセージを簡単に送信できます。</span><span class="sxs-lookup"><span data-stu-id="6c84e-106">However, by using the Script task, it is easy to send a message to a remote private queue.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6c84e-107">複数のパッケージでより簡単に再利用できるタスクを作成する場合は、このスクリプト タスク サンプルのコードを基にした、カスタム タスクの作成を検討してください。</span><span class="sxs-lookup"><span data-stu-id="6c84e-107">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="6c84e-108">詳細については、「 [カスタム タスクの開発](../extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c84e-108">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="6c84e-109">説明</span><span class="sxs-lookup"><span data-stu-id="6c84e-109">Description</span></span>  
 <span data-ttu-id="6c84e-110">次の例では、既存の MSMQ 接続マネージャーを System.Messaging 名前空間のオブジェクトおよびメソッドと共に使用して、パッケージ変数に含まれているテキストをリモート プライベート メッセージ キューに送信します。</span><span class="sxs-lookup"><span data-stu-id="6c84e-110">The following example uses an existing MSMQ connection manager, together with objects and methods from the System.Messaging namespace, to send the text contained in a package variable to a remote private message queue.</span></span> <span data-ttu-id="6c84e-111">MSMQ 接続マネージャーの M:Microsoft.SqlServer.Dts.ManagedConnections.MSMQConn.AcquireConnection (System.object) メソッドを呼び出すと、このタスクを処理するメソッドを持つ**MessageQueue**オブジェクトが返され `Send` ます。</span><span class="sxs-lookup"><span data-stu-id="6c84e-111">The call to the M:Microsoft.SqlServer.Dts.ManagedConnections.MSMQConn.AcquireConnection(System.Object) method of the MSMQ connection manager returns a **MessageQueue** object whose `Send` method accomplishes this task.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="6c84e-112">このスクリプト タスクの例を構成するには</span><span class="sxs-lookup"><span data-stu-id="6c84e-112">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="6c84e-113">既定の名前を使用して MSMQ 接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="6c84e-113">Create an MSMQ connection manager with the default name.</span></span> <span data-ttu-id="6c84e-114">有効なリモート プライベート キューのパスを次の形式で設定します。</span><span class="sxs-lookup"><span data-stu-id="6c84e-114">Set the path of a valid remote private queue, in the following format:</span></span>  
  
    ```  
    FORMATNAME:DIRECT=OS:<computername>\private$\<queuename>  
    ```  
  
2.  <span data-ttu-id="6c84e-115">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]メッセージテキストをスクリプトに渡すために、型の**messagetext**という名前の変数を作成し `String` ます。</span><span class="sxs-lookup"><span data-stu-id="6c84e-115">Create an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] variable named **MessageText** of type `String` to pass the message text into the script.</span></span> <span data-ttu-id="6c84e-116">この変数の値として既定のメッセージを入力します。</span><span class="sxs-lookup"><span data-stu-id="6c84e-116">Enter a default message as the value of the variable.</span></span>  
  
3.  <span data-ttu-id="6c84e-117">スクリプト タスクをデザイン画面に追加して編集します。</span><span class="sxs-lookup"><span data-stu-id="6c84e-117">Add a Script Task to the design surface and edit it.</span></span> <span data-ttu-id="6c84e-118">**[スクリプト タスク エディター]** の **[スクリプト]** タブで、**ReadOnlyVariables** プロパティに `MessageText` 変数を追加し、この変数をスクリプト内で使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="6c84e-118">On the **Script** tab of the **Script Task Editor**, add the `MessageText` variable to the **ReadOnlyVariables** property to make the variable available inside the script.</span></span>  
  
4.  <span data-ttu-id="6c84e-119">**[スクリプトの編集]** をクリックして、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) スクリプト エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="6c84e-119">Click **Edit Script** to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) script editor.</span></span>  
  
5.  <span data-ttu-id="6c84e-120">スクリプト プロジェクトに `System.Messaging` 名前空間への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="6c84e-120">Add a reference in the script project to the `System.Messaging` namespace.</span></span>  
  
6.  <span data-ttu-id="6c84e-121">スクリプト ウィンドウの内容を、次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="6c84e-121">Replace the contents of the script window with the code in the following section.</span></span>  
  
## <a name="code"></a><span data-ttu-id="6c84e-122">コード</span><span class="sxs-lookup"><span data-stu-id="6c84e-122">Code</span></span>  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports System.Messaging  
  
Public Class ScriptMain  
  
    Public Sub Main()  
  
        Dim remotePrivateQueue As MessageQueue  
        Dim messageText As String  
  
        remotePrivateQueue = _  
            DirectCast(Dts.Connections("Message Queue Connection Manager").AcquireConnection(Dts.Transaction), _  
            MessageQueue)  
        messageText = DirectCast(Dts.Variables("MessageText").Value, String)  
        remotePrivateQueue.Send(messageText)  
  
        Dts.TaskResult = ScriptResults.Success  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Messaging;  
  
public class ScriptMain  
{  
  
    public void Main()  
        {  
  
            MessageQueue remotePrivateQueue = new MessageQueue();  
            string messageText;  
  
            remotePrivateQueue = (MessageQueue)(Dts.Connections["Message Queue Connection Manager"].AcquireConnection(Dts.Transaction) as MessageQueue);  
            messageText = (string)(Dts.Variables["MessageText"].Value);  
            remotePrivateQueue.Send(messageText);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
}  
```  
  
<span data-ttu-id="6c84e-123">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="6c84e-123">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="6c84e-124">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c84e-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="6c84e-125">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="6c84e-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="6c84e-126">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="6c84e-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c84e-127">参照</span><span class="sxs-lookup"><span data-stu-id="6c84e-127">See Also</span></span>  
 [<span data-ttu-id="6c84e-128">メッセージ キュー タスク</span><span class="sxs-lookup"><span data-stu-id="6c84e-128">Message Queue Task</span></span>](../control-flow/message-queue-task.md)  
  
  
