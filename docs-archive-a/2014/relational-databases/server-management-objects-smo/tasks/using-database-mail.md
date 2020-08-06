---
title: データベースメール | を使用するMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- e-mail [SMO]
- Database Mail [SMO]
- mail [SMO]
ms.assetid: 7605390f-b485-48cc-8d97-e364a066067b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 86ceec7417638f53427ed5a62101f2fdb6d7440a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716166"
---
# <a name="using-database-mail"></a><span data-ttu-id="35300-102">データベース メールの使用</span><span class="sxs-lookup"><span data-stu-id="35300-102">Using Database Mail</span></span>
  <span data-ttu-id="35300-103">SMO では、<xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> プロパティによって参照される <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> オブジェクトで、データベース メール サブシステムを表現します。</span><span class="sxs-lookup"><span data-stu-id="35300-103">In SMO, the Database Mail subsystem is represented by the <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> object that is referenced by the <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> property.</span></span> <span data-ttu-id="35300-104">SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> オブジェクトを使用すると、データベース メール サブシステムを構成して、プロファイルおよびメール アカウントを管理することができます。</span><span class="sxs-lookup"><span data-stu-id="35300-104">By using the SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> object, you can configure the Database Mail subsystem and manage profiles and mail accounts.</span></span> <span data-ttu-id="35300-105">SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> オブジェクトは `Server` オブジェクトに属しています。これは、メール アカウントのスコープがサーバー レベルであることを意味しています。</span><span class="sxs-lookup"><span data-stu-id="35300-105">The SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> object belongs to the `Server` object, meaning that scope of the mail accounts is at the server level.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="35300-106">例</span><span class="sxs-lookup"><span data-stu-id="35300-106">Examples</span></span>  
 <span data-ttu-id="35300-107">提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35300-107">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="35300-108">詳細については、「 [Visual studio .net で VISUAL BASIC SMO プロジェクトを作成する](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)」または「visual [Studio .Net で VISUAL C&#35; Smo プロジェクトを作成](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35300-108">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
 <span data-ttu-id="35300-109">データベースメールを使用するプログラムでは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 、 `Imports` メール名前空間を修飾するステートメントを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="35300-109">For programs that use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Database Mail, you must include the `Imports` statement to qualify the Mail namespace.</span></span> <span data-ttu-id="35300-110">アプリケーションの宣言の前、かつ他の `Imports` ステートメントの後に、次のようにステートメントを挿入します。</span><span class="sxs-lookup"><span data-stu-id="35300-110">Insert the statement after the other `Imports` statements, before any declarations in the application, such as:</span></span>  
  
 `Imports Microsoft.SqlServer.Management.Smo`  
  
 `Imports Microsoft.SqlServer.Management.Common`  
  
 `Imports Microsoft.SqlServer.Management.Smo.Mail`  
  
## <a name="creating-a-database-mail-account-by-using-visual-basic"></a><span data-ttu-id="35300-111">Visual Basic によるデータベース メール アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="35300-111">Creating a Database Mail Account by Using Visual Basic</span></span>  
 <span data-ttu-id="35300-112">このコード例では、SMO で電子メール アカウントを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="35300-112">This code example shows how to create an e-mail account in SMO.</span></span> <span data-ttu-id="35300-113">データベース メールは <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> オブジェクトで表現され、<xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Server> プロパティによって参照されます。</span><span class="sxs-lookup"><span data-stu-id="35300-113">Database Mail is represented by the <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> object and referenced by the <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server> object.</span></span> <span data-ttu-id="35300-114">SMO は、プログラムでデータベース メールを構成するために使用することはできますが、電子メールを送信したり、受信した電子メールを処理したりするために使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="35300-114">SMO can be used to programmatically configure Database Mail, but it cannot be used to send or handle received e-mail.</span></span>  
  
 <span data-ttu-id="35300-115">VB.NET</span><span class="sxs-lookup"><span data-stu-id="35300-115">VB.NET</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMail1](SMO How to#SMO_VBMail1)]  -->  
  
## <a name="creating-a-database-mail-account-by-using-visual-c"></a><span data-ttu-id="35300-116">Visual C# によるデータベース メール アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="35300-116">Creating a Database Mail Account by Using Visual C#</span></span>  
 <span data-ttu-id="35300-117">このコード例では、SMO で電子メール アカウントを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="35300-117">This code example shows how to create an e-mail account in SMO.</span></span> <span data-ttu-id="35300-118">データベース メールは <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> オブジェクトで表現され、<xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Server> プロパティによって参照されます。</span><span class="sxs-lookup"><span data-stu-id="35300-118">Database Mail is represented by the <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> object and referenced by the <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server> object.</span></span> <span data-ttu-id="35300-119">SMO は、プログラムでデータベース メールを構成するために使用することはできますが、電子メールを送信したり、受信した電子メールを処理したりするために使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="35300-119">SMO can be used to programmatically configure Database Mail, but it cannot be used to send or handle received e-mail.</span></span>  
  
```csharp  
{  
         //Connect to the local, default instance of SQL Server.  
         Server srv = default(Server);   
           srv = new Server();   
           //Define the Database Mail service with a SqlMail object variable   
           //and reference it using the Server Mail property.   
           SqlMail sm;   
           sm = srv.Mail;   
           //Define and create a mail account by supplying the Database Mail  
           //service, name, description, display name, and email address  
           //arguments in the constructor.   
           MailAccount a = default(MailAccount);   
           a = new MailAccount(sm, "AdventureWorks2012 Administrator", "AdventureWorks2012 Automated Mailer", "Mail account for administrative e-mail.", "dba@Adventure-Works.com");   
           a.Create();    
}  
```  
  
## <a name="creating-a-database-mail-account-by-using-powershell"></a><span data-ttu-id="35300-120">PowerShell によるデータベース メール アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="35300-120">Creating a Database Mail Account by Using PowerShell</span></span>  
 <span data-ttu-id="35300-121">このコード例では、SMO で電子メール アカウントを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="35300-121">This code example shows how to create an e-mail account in SMO.</span></span> <span data-ttu-id="35300-122">データベース メールは <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> オブジェクトで表現され、<xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Server> プロパティによって参照されます。</span><span class="sxs-lookup"><span data-stu-id="35300-122">Database Mail is represented by the <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> object and referenced by the <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server> object.</span></span> <span data-ttu-id="35300-123">SMO は、プログラムでデータベース メールを構成するために使用することはできますが、電子メールを送信したり、受信した電子メールを処理したりするために使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="35300-123">SMO can be used to programmatically configure Database Mail, but it cannot be used to send or handle received e-mail.</span></span>
  
```powershell  
#Connect to the local, default instance of SQL Server.  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define the Database Mail; reference it using the Server Mail property.  
$sm = $srv.Mail  
  
#Define and create a mail account by supplying the Database Mail service,  
#name, description, display name, and email address arguments in the constructor.  
$a = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Mail.MailAccount -ArgumentList $sm, `  
"Adventure Works Administrator", "Adventure Works Automated Mailer",`  
 "Mail account for administrative e-mail.", "dba@Adventure-Works.com"  
$a.Create()  
```  
