---
title: SQL Server のインスタンスへの接続 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, connections
- connections [SMO]
- instances of SQL Server, connections
- SMO [SQL Server], connections
ms.assetid: ad3cf354-b2e3-468b-b986-1232e375fd84
author: stevestein
ms.author: sstein
ms.openlocfilehash: efc21451f4a876c6edfe4a2389ca937d11bc5c8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644960"
---
# <a name="connecting-to-an-instance-of-sql-server"></a><span data-ttu-id="df672-102">SQL Server のインスタンスへの接続</span><span class="sxs-lookup"><span data-stu-id="df672-102">Connecting to an Instance of SQL Server</span></span>
  <span data-ttu-id="df672-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]管理オブジェクト (SMO) アプリケーションの最初のプログラミング手順では、オブジェクトのインスタンスを作成 <xref:Microsoft.SqlServer.Management.Smo.Server> し、のインスタンスへの接続を確立し [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="df672-103">The first programming step in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) application is to create an instance of the <xref:Microsoft.SqlServer.Management.Smo.Server> object and to establish its connection to an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="df672-104"><xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクトのインスタンスを作成し、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスへの接続を確立するには、3 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="df672-104">You can create an instance of the <xref:Microsoft.SqlServer.Management.Smo.Server> object and establish a connection to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in three ways.</span></span> <span data-ttu-id="df672-105">1 つは、<xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクト変数を使用して接続情報を提供する方法です。</span><span class="sxs-lookup"><span data-stu-id="df672-105">The first is using a <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object variable to provide the connection information.</span></span> <span data-ttu-id="df672-106">2 つ目は、<xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクト プロパティを明示的に設定することで接続情報を提供する方法です。</span><span class="sxs-lookup"><span data-stu-id="df672-106">The second is to provide the connection information by explicitly setting the <xref:Microsoft.SqlServer.Management.Smo.Server> object properties.</span></span> <span data-ttu-id="df672-107">3 つ目は、<xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクト コンストラクターに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスの名前を渡す方法です。</span><span class="sxs-lookup"><span data-stu-id="df672-107">The third is to pass the name of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in the <xref:Microsoft.SqlServer.Management.Smo.Server> object constructor.</span></span>  
  
 <span data-ttu-id="df672-108">**ServerConnection オブジェクトの使用**</span><span class="sxs-lookup"><span data-stu-id="df672-108">**Using a ServerConnection object**</span></span>  
  
 <span data-ttu-id="df672-109"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクト変数を使用することの利点は、接続情報を再利用できることです。</span><span class="sxs-lookup"><span data-stu-id="df672-109">The advantage of using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object variable is that the connection information can be reused.</span></span> <span data-ttu-id="df672-110">まず、<xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクト変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="df672-110">Declare a <xref:Microsoft.SqlServer.Management.Smo.Server> object variable.</span></span> <span data-ttu-id="df672-111">次に、<xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトを宣言し、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスの名前などの接続情報を持つプロパティ、および認証モードを設定します。</span><span class="sxs-lookup"><span data-stu-id="df672-111">Then, declare a <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object and set properties with connection information such as the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], and the authentication mode.</span></span> <span data-ttu-id="df672-112">そして、パラメーターとして <xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクト変数を <xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクト コンストラクターに渡します。</span><span class="sxs-lookup"><span data-stu-id="df672-112">Then, pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object variable as a parameter to the <xref:Microsoft.SqlServer.Management.Smo.Server> object constructor.</span></span> <span data-ttu-id="df672-113">異なるサーバー オブジェクト間で同時に接続を共有することはお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="df672-113">It is not recommended to share connections between different server objects at the same time.</span></span> <span data-ttu-id="df672-114"><xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> メソッドを使用して、既存の接続設定のコピーを取得してください。</span><span class="sxs-lookup"><span data-stu-id="df672-114">Use the <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> method to get a copy of the existing connection settings.</span></span>  
  
 <span data-ttu-id="df672-115">**サーバー オブジェクト プロパティの明示的な設定**</span><span class="sxs-lookup"><span data-stu-id="df672-115">**Setting Server object properties explicitly**</span></span>  
  
 <span data-ttu-id="df672-116">別の方法として、<xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクト変数を宣言して、既定のコンストラクターを呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="df672-116">Alternatively, you can declare the <xref:Microsoft.SqlServer.Management.Smo.Server> object variable and call the default constructor.</span></span> <span data-ttu-id="df672-117"><xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクトは、すべての既定の接続設定で [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定インスタンスに接続しようとします。</span><span class="sxs-lookup"><span data-stu-id="df672-117">As is, the <xref:Microsoft.SqlServer.Management.Smo.Server> object tries to connect to the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with all the default connection settings.</span></span>  
  
 <span data-ttu-id="df672-118">**Server オブジェクト コンストラクターへの SQL&amp;#xA0;Server インスタンス名の提供**</span><span class="sxs-lookup"><span data-stu-id="df672-118">**Providing the SQL Server instance name in the Server object constructor**</span></span>  
  
 <span data-ttu-id="df672-119"><xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクト変数を宣言し、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を文字列パラメーターとしてコンストラクターに渡します。</span><span class="sxs-lookup"><span data-stu-id="df672-119">Declare the <xref:Microsoft.SqlServer.Management.Smo.Server> object variable and pass the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance name as a string parameter in the constructor.</span></span> <span data-ttu-id="df672-120"><xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクトは、既定の接続設定で [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスとの接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="df672-120">The <xref:Microsoft.SqlServer.Management.Smo.Server> object establishes a connection with the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with the default connection settings.</span></span>  
  
## <a name="connection-pooling"></a><span data-ttu-id="df672-121">接続プール</span><span class="sxs-lookup"><span data-stu-id="df672-121">Connection Pooling</span></span>  
 <span data-ttu-id="df672-122">通常、<xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Common.ServerConnection> メソッドを呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="df672-122">It is typically not required to call the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> method of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span> <span data-ttu-id="df672-123">SMO は、必要な場合には自動的に接続を確立し、実行中の操作が完了した後で接続プールに接続を解放します。</span><span class="sxs-lookup"><span data-stu-id="df672-123">SMO will automatically establish a connection when required, and release the connection to the connection pool after it has finished performing operations.</span></span> <span data-ttu-id="df672-124"><xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> メソッドが呼び出された場合、接続はプールに解放されません。</span><span class="sxs-lookup"><span data-stu-id="df672-124">When the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> method is called, the connection is not released to the pool.</span></span> <span data-ttu-id="df672-125">接続をプールに解放するには、<xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> メソッドへの明示的な呼び出しが必要です。</span><span class="sxs-lookup"><span data-stu-id="df672-125">An explicit call to the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> method is required to release the connection to the pool.</span></span> <span data-ttu-id="df672-126">また、<xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Common.ServerConnection> プロパティを設定することによって、プールされていない接続を要求することもできます。</span><span class="sxs-lookup"><span data-stu-id="df672-126">Additionally, you can request a non-pooled connection by setting the <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> property of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
## <a name="multithreaded-applications"></a><span data-ttu-id="df672-127">マルチスレッド アプリケーション</span><span class="sxs-lookup"><span data-stu-id="df672-127">Multithreaded Applications</span></span>  
 <span data-ttu-id="df672-128">マルチスレッド化されたアプリケーションの場合、各スレッドで別々の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="df672-128">For multithreaded applications, a separate <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object should be used in each thread.</span></span>  
  
## <a name="connecting-to-an-instance-of-sql-server-for-rmo"></a><span data-ttu-id="df672-129">RMO の SQL Server のインスタンスへの接続</span><span class="sxs-lookup"><span data-stu-id="df672-129">Connecting to an Instance of SQL Server for RMO</span></span>  
 <span data-ttu-id="df672-130">レプリケーション管理オブジェクト (RMO) では、レプリケーション サーバーへの接続には、SMO とは少し異なる方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="df672-130">Replication Management Objects (RMO) uses a slightly different method from SMO to connect to a replication server.</span></span>  
  
 <span data-ttu-id="df672-131">RMO プログラミング オブジェクトでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスへの接続は、`Microsoft.SqlServer.Management.Common` 名前空間によって実装された <xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトを使用して行われる必要があります。</span><span class="sxs-lookup"><span data-stu-id="df672-131">RMO programming objects require that a connection to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is made by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object implemented by the `Microsoft.SqlServer.Management.Common` namespace.</span></span> <span data-ttu-id="df672-132">サーバーへのこの接続は、RMO プログラミング オブジェクトからは独立して行われます。</span><span class="sxs-lookup"><span data-stu-id="df672-132">This connection to the server is made independently of an RMO programming object.</span></span> <span data-ttu-id="df672-133">そして、インスタンスの作成時、またはオブジェクトの <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティへの割り当てによって、RMO オブジェクトに渡されます。</span><span class="sxs-lookup"><span data-stu-id="df672-133">It is then it is passed to the RMO object either during instance creation or by assignment to the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property of the object.</span></span> <span data-ttu-id="df672-134">この方法では、RMO プログラミング オブジェクトおよび接続オブジェクト インスタンスを別々に作成および管理することが可能となり、単一の接続オブジェクトを複数の RMO プログラミング オブジェクトと共に再利用することができます。</span><span class="sxs-lookup"><span data-stu-id="df672-134">In this manner, an RMO programming object and the connection object instances can be created and managed separately, and a single connection object can be reused with multiple RMO programming objects.</span></span> <span data-ttu-id="df672-135">レプリケーション サーバーへの接続には、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="df672-135">The following rules apply for connections to a replication server:</span></span>  
  
-   <span data-ttu-id="df672-136">接続のプロパティはすべて、<xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトに対して定義します。</span><span class="sxs-lookup"><span data-stu-id="df672-136">All properties for the connection are defined for a specified <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="df672-137">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスへの各接続には、独自の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトが必要です。</span><span class="sxs-lookup"><span data-stu-id="df672-137">Each connection to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] must have its own <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="df672-138">接続を作成し、サーバーに正常にログオンするための認証情報はすべて <xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトで指定されます。</span><span class="sxs-lookup"><span data-stu-id="df672-138">All authentication information to make the connection and successfully log on to the server is supplied in the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="df672-139">既定では、接続は Microsoft Windows 認証を使用して作成します。</span><span class="sxs-lookup"><span data-stu-id="df672-139">By default, connections are made by using Microsoft Windows Authentication.</span></span> <span data-ttu-id="df672-140">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用するには、<xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.LoginSecure%2A> を False に設定し、<xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Login%2A> および <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Password%2A> に、有効な [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログオンおよびパスワードを設定しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="df672-140">To use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.LoginSecure%2A> must be set to False and <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Login%2A> and <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Password%2A> must be set to a valid [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logon and password.</span></span> <span data-ttu-id="df672-141">セキュリティの資格情報は、常に安全に格納および処理し、いつでも可能であれば実行時に提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df672-141">Security credentials must always be stored and handled securely, and supplied at run time whenever possible.</span></span>  
  
-   <span data-ttu-id="df672-142"><xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> メソッドは、RMO プログラミング オブジェクトに接続を渡す前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="df672-142">The <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> method must be called before passing the connection to any RMO programming object.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="df672-143">例</span><span class="sxs-lookup"><span data-stu-id="df672-143">Examples</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="connecting-to-the-local-instance-of-sql-server-by-using-windows-authentication-in-visual-basic"></a><span data-ttu-id="df672-144">Visual Basic で Windows 認証を使用して SQL Server のローカル インスタンスに接続する</span><span class="sxs-lookup"><span data-stu-id="df672-144">Connecting to the Local Instance of SQL Server by Using Windows Authentication in Visual Basic</span></span>  
 <span data-ttu-id="df672-145">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のローカル インスタンスへの接続に必要なコードは多くありません。</span><span class="sxs-lookup"><span data-stu-id="df672-145">Connecting to the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not require much code.</span></span> <span data-ttu-id="df672-146">ただし、認証方法とサーバーの既定の設定によってコードが異なります。</span><span class="sxs-lookup"><span data-stu-id="df672-146">Instead, it relies on default settings for authentication method and server.</span></span> <span data-ttu-id="df672-147">接続は、データの取得を必要とする操作が初めて発生する際に作成します。</span><span class="sxs-lookup"><span data-stu-id="df672-147">The first operation that requires data to be retrieved will cause a connection to be created.</span></span>  
  
 <span data-ttu-id="df672-148">この例は、 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Windows 認証を使用してのローカルインスタンスに接続する .net コードです。</span><span class="sxs-lookup"><span data-stu-id="df672-148">This example is [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET code that connects to the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB1](SMO How to#SMO_VB1)]  -->  
  
## <a name="connecting-to-the-local-instance-of-sql-server-by-using-windows-authentication-in-visual-c"></a><span data-ttu-id="df672-149">Visual C# で Windows 認証を使用して SQL Server のローカル インスタンスに接続する</span><span class="sxs-lookup"><span data-stu-id="df672-149">Connecting to the Local Instance of SQL Server by Using Windows Authentication in Visual C#</span></span>  
 <span data-ttu-id="df672-150">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のローカル インスタンスへの接続に必要なコードは多くありません。</span><span class="sxs-lookup"><span data-stu-id="df672-150">Connecting to the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not require much code.</span></span> <span data-ttu-id="df672-151">ただし、認証方法とサーバーの既定の設定によってコードが異なります。</span><span class="sxs-lookup"><span data-stu-id="df672-151">Instead, it relies on default settings for authentication method and server.</span></span> <span data-ttu-id="df672-152">接続は、データの取得を必要とする操作が初めて発生する際に作成します。</span><span class="sxs-lookup"><span data-stu-id="df672-152">The first operation that requires data to be retrieved will cause a connection to be created.</span></span>  
  
 <span data-ttu-id="df672-153">この例は、Windows 認証を使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のローカル インスタンスに接続する Visual C# .NET コードです。</span><span class="sxs-lookup"><span data-stu-id="df672-153">This example is Visual C# .NET code that connects to the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//The connection is established when a property is requested.   
Console.WriteLine(srv.Information.Version);   
}   
//The connection is automatically disconnected when the Server variable goes out of scope.  
```  
  
## <a name="connecting-to-a-remote-instance-of-sql-server-by-using-windows-authentication-in-visual-basic"></a><span data-ttu-id="df672-154">Visual Basic で Windows 認証を使用して SQL Server のリモート インスタンスに接続する</span><span class="sxs-lookup"><span data-stu-id="df672-154">Connecting to a Remote Instance of SQL Server by Using Windows Authentication in Visual Basic</span></span>  
 <span data-ttu-id="df672-155">Windows 認証を使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続する場合、認証の種類を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="df672-155">When you connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication, you do not have to specify the authentication type.</span></span> <span data-ttu-id="df672-156">既定は Windows 認証です。</span><span class="sxs-lookup"><span data-stu-id="df672-156">Windows Authentication is the default.</span></span>  
  
 <span data-ttu-id="df672-157">この例は [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Windows 認証を使用してのリモートインスタンスに接続する .net コードです。</span><span class="sxs-lookup"><span data-stu-id="df672-157">This example is [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET code that connects to the remote instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication.</span></span> <span data-ttu-id="df672-158">文字列変数*Strserver*には、リモートインスタンスの名前が含まれています。</span><span class="sxs-lookup"><span data-stu-id="df672-158">The string variable *strServer* contains the name of the remote instance.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB2](SMO How to#SMO_VB2)]  -->  
  
## <a name="connecting-to-a-remote-instance-of-sql-server-by-using-windows-authentication-in-visual-c"></a><span data-ttu-id="df672-159">Visual C# で Windows 認証を使用して SQL Server のリモート インスタンスに接続する</span><span class="sxs-lookup"><span data-stu-id="df672-159">Connecting to a Remote Instance of SQL Server by Using Windows Authentication in Visual C#</span></span>  
 <span data-ttu-id="df672-160">Windows 認証を使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続する場合、認証の種類を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="df672-160">When you connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication, you do not have to specify the authentication type.</span></span> <span data-ttu-id="df672-161">既定は Windows 認証です。</span><span class="sxs-lookup"><span data-stu-id="df672-161">Windows Authentication is the default.</span></span>  
  
 <span data-ttu-id="df672-162">この例は、Windows 認証を使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のリモート インスタンスに接続する Visual C# .NET コードです。</span><span class="sxs-lookup"><span data-stu-id="df672-162">This example is Visual C# .NET code that connects to the remote instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication.</span></span> <span data-ttu-id="df672-163">文字列変数*Strserver*には、リモートインスタンスの名前が含まれています。</span><span class="sxs-lookup"><span data-stu-id="df672-163">The string variable *strServer* contains the name of the remote instance.</span></span>  
  
```  
{   
//Connect to a remote instance of SQL Server.   
Server srv;   
//The strServer string variable contains the name of a remote instance of SQL Server.   
srv = new Server(strServer);   
//The actual connection is made when a property is retrieved.   
Console.WriteLine(srv.Information.Version);   
}   
//The connection is automatically disconnected when the Server variable goes out of scope.  
```  
  
## <a name="connecting-to-an-instance-of-sql-server-by-using-sql-server-authentication-in-visual-basic"></a><span data-ttu-id="df672-164">Visual Basic で SQL Server 認証を使用して SQL Server のインスタンスに接続する</span><span class="sxs-lookup"><span data-stu-id="df672-164">Connecting to an Instance of SQL Server by Using SQL Server Authentication in Visual Basic</span></span>  
 <span data-ttu-id="df672-165">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続する場合、認証の種類を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df672-165">When you connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, you must specify the authentication type.</span></span> <span data-ttu-id="df672-166">この例では、もう 1 つの方法として、<xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクト変数を宣言する方法を示します。この方法では、接続情報の再利用が可能になります。</span><span class="sxs-lookup"><span data-stu-id="df672-166">This example demonstrates the alternative method of declaring a <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object variable, which enables the connection information to be reused.</span></span>  
  
 <span data-ttu-id="df672-167">この例は、 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] リモートの接続方法と、ログオンとパスワードを格納する*vpassword*を示す .net コードです。</span><span class="sxs-lookup"><span data-stu-id="df672-167">The example is [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET code that demonstrates how to connect to the remote and *vPassword* contain the logon and password.</span></span>  
  
```  
' compile with:   
' /r:Microsoft.SqlServer.Smo.dll  
' /r:Microsoft.SqlServer.ConnectionInfo.dll  
' /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
  
Public Class A  
   Public Shared Sub Main()  
      Dim sqlServerLogin As [String] = "user_id"  
      Dim password As [String] = "pwd"  
      Dim instanceName As [String] = "instance_name"  
      Dim remoteSvrName As [String] = "remote_server_name"  
  
      ' Connecting to an instance of SQL Server using SQL Server Authentication  
      Dim srv1 As New Server()   ' connects to default instance  
      srv1.ConnectionContext.LoginSecure = False   ' set to true for Windows Authentication  
      srv1.ConnectionContext.Login = sqlServerLogin  
      srv1.ConnectionContext.Password = password  
      Console.WriteLine(srv1.Information.Version)   ' connection is established  
  
      ' Connecting to a named instance of SQL Server with SQL Server Authentication using ServerConnection  
      Dim srvConn As New ServerConnection()  
      srvConn.ServerInstance = ".\" & instanceName   ' connects to named instance  
      srvConn.LoginSecure = False   ' set to true for Windows Authentication  
      srvConn.Login = sqlServerLogin  
      srvConn.Password = password  
      Dim srv2 As New Server(srvConn)  
      Console.WriteLine(srv2.Information.Version)   ' connection is established  
  
      ' For remote connection, remote server name / ServerInstance needs to be specified  
      Dim srvConn2 As New ServerConnection(remoteSvrName)  
      srvConn2.LoginSecure = False  
      srvConn2.Login = sqlServerLogin  
      srvConn2.Password = password  
      Dim srv3 As New Server(srvConn2)  
      Console.WriteLine(srv3.Information.Version)   ' connection is established  
   End Sub  
End Class  
```  
  
## <a name="connecting-to-an-instance-of-sql-server-by-using-sql-server-authentication-in-visual-c"></a><span data-ttu-id="df672-168">Visual C# で SQL Server 認証を使用して SQL Server のインスタンスに接続する</span><span class="sxs-lookup"><span data-stu-id="df672-168">Connecting to an Instance of SQL Server by Using SQL Server Authentication in Visual C#</span></span>  
 <span data-ttu-id="df672-169">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続する場合、認証の種類を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df672-169">When you connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, you must specify the authentication type.</span></span> <span data-ttu-id="df672-170">この例では、もう 1 つの方法として、<xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクト変数を宣言する方法を示します。この方法では、接続情報の再利用が可能になります。</span><span class="sxs-lookup"><span data-stu-id="df672-170">This example demonstrates the alternative method of declaring a <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object variable, which enables the connection information to be reused.</span></span>  
  
 <span data-ttu-id="df672-171">この例は、リモートと*Vpassword*に接続してログオンとパスワードを格納する方法を示す Visual C# .net コードです。</span><span class="sxs-lookup"><span data-stu-id="df672-171">The example is Visual C# .NET code that demonstrates how to connect to the remote and *vPassword* contain the logon and password.</span></span>  
  
```  
// compile with:   
// /r:Microsoft.SqlServer.Smo.dll  
// /r:Microsoft.SqlServer.ConnectionInfo.dll  
// /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
using System;  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Common;  
  
public class A {  
   public static void Main() {   
      String sqlServerLogin = "user_id";  
      String password = "pwd";  
      String instanceName = "instance_name";  
      String remoteSvrName = "remote_server_name";  
  
      // Connecting to an instance of SQL Server using SQL Server Authentication  
      Server srv1 = new Server();   // connects to default instance  
      srv1.ConnectionContext.LoginSecure = false;   // set to true for Windows Authentication  
      srv1.ConnectionContext.Login = sqlServerLogin;  
      srv1.ConnectionContext.Password = password;  
      Console.WriteLine(srv1.Information.Version);   // connection is established  
  
      // Connecting to a named instance of SQL Server with SQL Server Authentication using ServerConnection  
      ServerConnection srvConn = new ServerConnection();  
      srvConn.ServerInstance = @".\" + instanceName;   // connects to named instance  
      srvConn.LoginSecure = false;   // set to true for Windows Authentication  
      srvConn.Login = sqlServerLogin;  
      srvConn.Password = password;  
      Server srv2 = new Server(srvConn);  
      Console.WriteLine(srv2.Information.Version);   // connection is established  
  
      // For remote connection, remote server name / ServerInstance needs to be specified  
      ServerConnection srvConn2 = new ServerConnection(remoteSvrName);  
      srvConn2.LoginSecure = false;  
      srvConn2.Login = sqlServerLogin;  
      srvConn2.Password = password;  
      Server srv3 = new Server(srvConn2);  
      Console.WriteLine(srv3.Information.Version);   // connection is established  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="df672-172">参照</span><span class="sxs-lookup"><span data-stu-id="df672-172">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  
