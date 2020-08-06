---
title: スクリプト タスクによる HTML メール メッセージの送信 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Send Mail task [Integration Services]
- Script task [Integration Services], examples
- Script task [Integration Services], HTML mail message
ms.assetid: dd2b1eef-b04f-4946-87ab-7bc56bb525ce
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6c1a967b52a84e1ff9c2e54c48e40f4d149b2dbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712181"
---
# <a name="sending-an-html-mail-message-with-the-script-task"></a><span data-ttu-id="833eb-102">スクリプト タスクによる HTML メール メッセージの送信</span><span class="sxs-lookup"><span data-stu-id="833eb-102">Sending an HTML Mail Message with the Script Task</span></span>
  <span data-ttu-id="833eb-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の SendMail タスクでは、プレーン テキスト形式のメール メッセージのみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="833eb-103">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] SendMail task only supports mail messages in plain text format.</span></span> <span data-ttu-id="833eb-104">ただし、.NET Framework のスクリプト タスクとメール機能を使用して、HTML メール メッセージを簡単に送信できます。</span><span class="sxs-lookup"><span data-stu-id="833eb-104">However you can easily send HTML mail messages by using the Script task and the mail capabilities of the .NET Framework.</span></span>

> [!NOTE]
>  <span data-ttu-id="833eb-105">複数のパッケージでより簡単に再利用できるタスクを作成する場合は、このスクリプト タスク サンプルのコードを基にした、カスタム タスクの作成を検討してください。</span><span class="sxs-lookup"><span data-stu-id="833eb-105">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="833eb-106">詳細については、「 [カスタム タスクの開発](../extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="833eb-106">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>

## <a name="description"></a><span data-ttu-id="833eb-107">説明</span><span class="sxs-lookup"><span data-stu-id="833eb-107">Description</span></span>
 <span data-ttu-id="833eb-108">次の例では、`System.Net.Mail` 名前空間を使用して、HTML メール メッセージを構成および送信します。</span><span class="sxs-lookup"><span data-stu-id="833eb-108">The following example uses the `System.Net.Mail` namespace to configure and send an HTML mail message.</span></span> <span data-ttu-id="833eb-109">スクリプトは、電子メールの宛先、差出人、件名、および本文をパッケージ変数から取得し、これらを使用して新しい `MailMessag` を作成します。また、その `IsBodyHtml` プロパティに `True` を設定します。</span><span class="sxs-lookup"><span data-stu-id="833eb-109">The script obtains the To, From, Subject, and body of the e-mail from package variables, uses them to create a new `MailMessag`e, and sets its `IsBodyHtml` property to `True`.</span></span> <span data-ttu-id="833eb-110">次に、別のパッケージ変数から SMTP サーバー名を取得し、`System.Net.Mail.SmtpClient` のインスタンスを初期化し、そのインスタンスの `Send` メソッドを呼び出して HTML メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="833eb-110">Then it obtains the SMTP server name from another package variable, initializes an instance of `System.Net.Mail.SmtpClient`, and calls its `Send` method to send the HTML message.</span></span> <span data-ttu-id="833eb-111">このサンプルでは、メッセージ送信機能をサブルーチンにカプセル化しているため、他のスクリプトで再利用できます。</span><span class="sxs-lookup"><span data-stu-id="833eb-111">The sample encapsulates the message sending functionality in a subroutine that could be reused in other scripts.</span></span>

#### <a name="to-configure-this-script-task-example-without-an-smtp-connection-manager"></a><span data-ttu-id="833eb-112">このスクリプト タスクの例を SMTP 接続マネージャーを使用せずに構成するには</span><span class="sxs-lookup"><span data-stu-id="833eb-112">To configure this Script Task example without an SMTP Connection Manager</span></span>

1.  <span data-ttu-id="833eb-113">`HtmlEmailTo`、`HtmlEmailFrom`、および `HtmlEmailSubject` という名前の文字列変数を作成し、これらに適切な値を割り当てて、有効なテスト メッセージを用意します。</span><span class="sxs-lookup"><span data-stu-id="833eb-113">Create string variables named `HtmlEmailTo`, `HtmlEmailFrom`, and `HtmlEmailSubject` and assign appropriate values to them for a valid test message.</span></span>

2.  <span data-ttu-id="833eb-114">`HtmlEmailBody` という名前の文字列変数を作成し、HTML マークアップの文字列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="833eb-114">Create a string variable named `HtmlEmailBody` and assign a string of HTML markup to it.</span></span> <span data-ttu-id="833eb-115">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="833eb-115">For example:</span></span>

    ```
    <html><body><h1>Testing</h1><p>This is a <b>test</b> message.</p></body></html>
    ```

3.  <span data-ttu-id="833eb-116">`HtmlEmailServer` という名前の文字列変数を作成し、匿名発信メッセージを受け入れる、使用可能な SMTP サーバーの名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="833eb-116">Create a string variable named `HtmlEmailServer` and assign the name of an available SMTP server that accepts anonymous outgoing messages.</span></span>

4.  <span data-ttu-id="833eb-117">これらの 5 つすべての変数を、新しいスクリプト タスクの **ReadOnlyVariables** プロパティに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="833eb-117">Assign all five of these variables to the **ReadOnlyVariables** property of a new Script task.</span></span>

5.  <span data-ttu-id="833eb-118">コードに `System.Net` および `System.Net.Mail` 名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="833eb-118">Import the `System.Net` and `System.Net.Mail` namespaces into your code.</span></span>

 <span data-ttu-id="833eb-119">このトピックのサンプル コードでは、SMTP サーバー名をパッケージ変数から取得します。</span><span class="sxs-lookup"><span data-stu-id="833eb-119">The sample code in this topic obtains the SMTP server name from a package variable.</span></span> <span data-ttu-id="833eb-120">ただし、SMTP 接続マネージャーを利用して接続情報をカプセル化し、コード内で接続マネージャーからサーバー名を抽出することもできます。</span><span class="sxs-lookup"><span data-stu-id="833eb-120">However, you could also take advantage of an SMTP connection manager to encapsulate the connection information, and extract the server name from the connection manager in your code.</span></span> <span data-ttu-id="833eb-121">SMTP 接続マネージャーの <xref:Microsoft.SqlServer.Dts.ManagedConnections.SMTPConn.AcquireConnection%2A> メソッドは、次の形式の文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="833eb-121">The <xref:Microsoft.SqlServer.Dts.ManagedConnections.SMTPConn.AcquireConnection%2A> method of the SMTP connection manager returns a string in the following format:</span></span>

 `SmtpServer=smtphost;UseWindowsAuthentication=False;EnableSsl=False;`

 <span data-ttu-id="833eb-122">`String.Split` メソッドを使用して、この引数リストをセミコロン (;) または等号 (=) で個々の文字列の配列に分割し、配列の 2 番目の引数 (subscript 1) をサーバー名として抽出することができます。</span><span class="sxs-lookup"><span data-stu-id="833eb-122">You can use the `String.Split` method to separate this argument list into an array of individual strings at each semicolon (;) or equal sign (=), and then extract the second argument (subscript 1) from the array as the server name.</span></span>

#### <a name="to-configure-this-script-task-example-with-an-smtp-connection-manager"></a><span data-ttu-id="833eb-123">このスクリプト タスクの例を SMTP 接続マネージャーを使用して構成するには</span><span class="sxs-lookup"><span data-stu-id="833eb-123">To configure this Script Task example with an SMTP Connection Manager</span></span>

1.  <span data-ttu-id="833eb-124">**ReadOnlyVariables** の一覧から `HtmlEmailServer` 変数を削除して、前に構成したスクリプト タスクを変更します。</span><span class="sxs-lookup"><span data-stu-id="833eb-124">Modify the Script task configured earlier by removing the `HtmlEmailServer` variable from the list of **ReadOnlyVariables**.</span></span>

2.  <span data-ttu-id="833eb-125">サーバー名を取得する次のコード行を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="833eb-125">Replace the line of code that obtains the server name:</span></span>

    ```
    Dim smtpServer As String = _
      Dts.Variables("HtmlEmailServer").Value.ToString
    ```

     <span data-ttu-id="833eb-126">次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="833eb-126">with the following lines:</span></span>

    ```
    Dim smtpConnectionString As String = _
      DirectCast(Dts.Connections("SMTP Connection Manager").AcquireConnection(Dts.Transaction), String)
    Dim smtpServer As String = _
      smtpConnectionString.Split(New Char() {"="c, ";"c})(1)
    ```

## <a name="code"></a><span data-ttu-id="833eb-127">コード</span><span class="sxs-lookup"><span data-stu-id="833eb-127">Code</span></span>

```vb
Public Sub Main()

  Dim htmlMessageTo As String = _
    Dts.Variables("HtmlEmailTo").Value.ToString
  Dim htmlMessageFrom As String = _
    Dts.Variables("HtmlEmailFrom").Value.ToString
  Dim htmlMessageSubject As String = _
    Dts.Variables("HtmlEmailSubject").Value.ToString
  Dim htmlMessageBody As String = _
    Dts.Variables("HtmlEmailBody").Value.ToString
  Dim smtpServer As String = _
    Dts.Variables("HtmlEmailServer").Value.ToString

  SendMailMessage( _
      htmlMessageTo, htmlMessageFrom, _
      htmlMessageSubject, htmlMessageBody, _
      True, smtpServer)

  Dts.TaskResult = ScriptResults.Success

End Sub

Private Sub SendMailMessage( _
    ByVal SendTo As String, ByVal From As String, _
    ByVal Subject As String, ByVal Body As String, _
    ByVal IsBodyHtml As Boolean, ByVal Server As String)

  Dim htmlMessage As MailMessage
  Dim mySmtpClient As SmtpClient

  htmlMessage = New MailMessage( _
    SendTo, From, Subject, Body)
  htmlMessage.IsBodyHtml = IsBodyHtml

  mySmtpClient = New SmtpClient(Server)
  mySmtpClient.Credentials = CredentialCache.DefaultNetworkCredentials
  mySmtpClient.Send(htmlMessage)

End Sub
```

```csharp
public void Main()
        {

            string htmlMessageTo = Dts.Variables["HtmlEmailTo"].Value.ToString();
            string htmlMessageFrom = Dts.Variables["HtmlEmailFrom"].Value.ToString();
            string htmlMessageSubject = Dts.Variables["HtmlEmailSubject"].Value.ToString();
            string htmlMessageBody = Dts.Variables["HtmlEmailBody"].Value.ToString();
            string smtpServer = Dts.Variables["HtmlEmailServer"].Value.ToString();

            SendMailMessage(htmlMessageTo, htmlMessageFrom, htmlMessageSubject, htmlMessageBody, true, smtpServer);

            Dts.TaskResult = (int)ScriptResults.Success;

        }

        private void SendMailMessage(string SendTo, string From, string Subject, string Body, bool IsBodyHtml, string Server)
        {

            MailMessage htmlMessage;
            SmtpClient mySmtpClient;

            htmlMessage = new MailMessage(SendTo, From, Subject, Body);
            htmlMessage.IsBodyHtml = IsBodyHtml;

            mySmtpClient = new SmtpClient(Server);
            mySmtpClient.Credentials = CredentialCache.DefaultNetworkCredentials;
            mySmtpClient.Send(htmlMessage);

        }
```

<span data-ttu-id="833eb-128">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="833eb-128">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="833eb-129">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="833eb-129">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="833eb-130">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="833eb-130">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="833eb-131">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="833eb-131">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="833eb-132">参照</span><span class="sxs-lookup"><span data-stu-id="833eb-132">See Also</span></span>
 [<span data-ttu-id="833eb-133">メール送信タスク</span><span class="sxs-lookup"><span data-stu-id="833eb-133">Send Mail Task</span></span>](../control-flow/send-mail-task.md)


