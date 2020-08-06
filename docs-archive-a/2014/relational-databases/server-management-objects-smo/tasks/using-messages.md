---
title: Messages | を使用するMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- messages [SMO]
ms.assetid: 4037a866-4826-4c1f-890c-e7e3658adf13
author: stevestein
ms.author: sstein
ms.openlocfilehash: 53b2e0fa4be2dfd53cdd8f4f0cacb7ae0bd79edb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644400"
---
# <a name="using-messages"></a><span data-ttu-id="dc438-102">メッセージの使用</span><span class="sxs-lookup"><span data-stu-id="dc438-102">Using Messages</span></span>
  <span data-ttu-id="dc438-103">SMO では、システム メッセージは、`Server` オブジェクトに属する <xref:Microsoft.SqlServer.Management.Smo.SystemMessageCollection> オブジェクトで表現します。</span><span class="sxs-lookup"><span data-stu-id="dc438-103">In SMO, system messages are represented by the <xref:Microsoft.SqlServer.Management.Smo.SystemMessageCollection> object that belongs to the `Server` object.</span></span> <span data-ttu-id="dc438-104">システム メッセージは変更することができないため、`SystemMessage` オブジェクト プロパティは読み込み専用となります。</span><span class="sxs-lookup"><span data-stu-id="dc438-104">Because the system messages cannot be modified, `SystemMessage` object properties are read-only.</span></span>  
  
 <span data-ttu-id="dc438-105">SMO では、プログラム上では <xref:Microsoft.SqlServer.Management.Smo.UserDefinedMessageCollection> オブジェクトを使用してユーザー定義メッセージを表現します。</span><span class="sxs-lookup"><span data-stu-id="dc438-105">User-defined messages are represented programmatically in SMO by the <xref:Microsoft.SqlServer.Management.Smo.UserDefinedMessageCollection> object.</span></span> <span data-ttu-id="dc438-106">既存のユーザー定義メッセージは、コレクションを反復処理することで検索することができます。</span><span class="sxs-lookup"><span data-stu-id="dc438-106">Existing user-defined messages can be discovered by iterating through the collection.</span></span> <span data-ttu-id="dc438-107">新しいユーザー定義メッセージは、新しい `UserDefinedMessage` オブジェクトをインスタンス化し、適切なプロパティの設定を行うことによって作成することができます。</span><span class="sxs-lookup"><span data-stu-id="dc438-107">New user-defined messages can be created by instantiating a new `UserDefinedMessage` object and setting the appropriate properties.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="dc438-108">例</span><span class="sxs-lookup"><span data-stu-id="dc438-108">Examples</span></span>  
 <span data-ttu-id="dc438-109">次のコード例では、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc438-109">For the following code examples, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="dc438-110">詳細については、「 [Visual studio .net での VISUAL BASIC Smo プロジェクトの作成](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)」および「visual [Studio .Net で VISUAL C&#35; Smo プロジェクトを作成](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc438-110">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="finding-a-particular-system-message-in-visual-basic"></a><span data-ttu-id="dc438-111">Visual Basic での特定のシステム メッセージの検索</span><span class="sxs-lookup"><span data-stu-id="dc438-111">Finding a Particular System Message in Visual Basic</span></span>  
 <span data-ttu-id="dc438-112">このコード例では、システム メッセージを ID 番号で識別してメッセージを表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="dc438-112">The code example shows how to identify a system message by ID number and display the message.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMessages1](SMO How to#SMO_VBMessages1)]  -->  
  
## <a name="finding-a-particular-system-message-in-visual-c"></a><span data-ttu-id="dc438-113">Visual C# での特定のシステム メッセージの検索</span><span class="sxs-lookup"><span data-stu-id="dc438-113">Finding a Particular System Message in Visual C#</span></span>  
 <span data-ttu-id="dc438-114">このコード例では、システム メッセージを ID 番号で識別してメッセージを表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="dc438-114">The code example shows how to identify a system message by ID number and display the message.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Reference an existing system message using the   
            //ItemByIdAndLanguage method.   
            SystemMessage msg = default(SystemMessage);  
            msg = srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english");  
            //Display the message ID and text.   
            Console.WriteLine(msg.ID.ToString() + " " + msg.Text);  
        }  
```  
  
## <a name="finding-a-particular-system-message-in-powershell"></a><span data-ttu-id="dc438-115">PowerShell での特定のシステム メッセージの検索</span><span class="sxs-lookup"><span data-stu-id="dc438-115">Finding a Particular System Message in PowerShell</span></span>  
 <span data-ttu-id="dc438-116">このコード例では、システム メッセージを ID 番号で識別してメッセージを表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="dc438-116">The code example shows how to identify a system message by ID number and display the message.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = Get-Item default  
  
#Get the message 14126 in US English and display it  
$msg = $srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english")  
$msg.ID.ToString() + " "+ $msg.Text  
```  
  
## <a name="adding-a-new-user-defined-message-in-visual-basic"></a><span data-ttu-id="dc438-117">Visual Basic での新しいユーザー定義メッセージの追加</span><span class="sxs-lookup"><span data-stu-id="dc438-117">Adding a New User-Defined Message in Visual Basic</span></span>  
 <span data-ttu-id="dc438-118">コード例では、50000 より大きい ID を使用してユーザー定義メッセージを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="dc438-118">The code example demonstrates how to create a user-defined message with an ID greater than 50000.</span></span>  
  
```vb
Dim mysrv As Server  
mysrv = New Server  
Dim udm As UserDefinedMessage  
udm = New UserDefinedMessage(mysrv, 50003, "us_english", 16, "Test message")  
udm.Create()  
```  
  
## <a name="adding-a-new-user-defined-message-in-visual-c"></a><span data-ttu-id="dc438-119">Visual C# での新しいユーザー定義メッセージの追加</span><span class="sxs-lookup"><span data-stu-id="dc438-119">Adding a New User-Defined Message in Visual C#</span></span>  
 <span data-ttu-id="dc438-120">コード例では、50000 より大きい ID を使用してユーザー定義メッセージを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="dc438-120">The code example demonstrates how to create a user-defined message with an ID greater than 50000.</span></span>  
  
```csharp
{
            Server mysrv = new Server();  
  
            UserDefinedMessage udm = new UserDefinedMessage(mysrv, 50030, "us_english",16, "Test message");  
            udm.Create();  
             UserDefinedMessage  msg = mysrv.UserDefinedMessages.ItemByIdAndLanguage(50030, "us_english");  
            //Display the message ID and text.   
            Console.WriteLine(msg.ID.ToString() + " " + msg.Text);  
  
        }  
```  
  
## <a name="adding-a-new-user-defined-message-in-powershell"></a><span data-ttu-id="dc438-121">PowerShell での新しいユーザー定義メッセージの追加</span><span class="sxs-lookup"><span data-stu-id="dc438-121">Adding a New User-Defined Message in PowerShell</span></span>
 <span data-ttu-id="dc438-122">コード例では、50000 より大きい ID を使用してユーザー定義メッセージを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="dc438-122">The code example demonstrates how to create a user-defined message with an ID greater than 50000.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a new message
$udm = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedMessage -ArgumentList `  
$srv, 50030, "us_english", 16, "Test message"  
$udm.Create()  
$msg = $srv.UserDefinedMessages.ItemByIdAndLanguage(50030, "us_english");  
$msg  
```  
