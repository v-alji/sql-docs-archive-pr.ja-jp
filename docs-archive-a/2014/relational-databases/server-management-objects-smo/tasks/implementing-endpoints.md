---
title: エンドポイントの実装 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- endpoints [SMO]
ms.assetid: f8674dbb-9bc0-488f-9def-e9e0ce1ddf86
author: stevestein
ms.author: sstein
ms.openlocfilehash: 293a661c6e1ad6f6139e30e0824e99686af98f90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739619"
---
# <a name="implementing-endpoints"></a><span data-ttu-id="e7867-102">エンドポイントの実装</span><span class="sxs-lookup"><span data-stu-id="e7867-102">Implementing Endpoints</span></span>
  <span data-ttu-id="e7867-103">エンドポイントは、要求をネイティブにリッスンできるサービスです。</span><span class="sxs-lookup"><span data-stu-id="e7867-103">An endpoint is a service that can listen natively for requests.</span></span> <span data-ttu-id="e7867-104">SMO は、<xref:Microsoft.SqlServer.Management.Smo.Endpoint> オブジェクトを使用することで、さまざまな種類のエンドポイントをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="e7867-104">SMO supports various types of endpoints by using the <xref:Microsoft.SqlServer.Management.Smo.Endpoint> object.</span></span> <span data-ttu-id="e7867-105"><xref:Microsoft.SqlServer.Management.Smo.Endpoint> オブジェクトのインスタンスを作成し、そのプロパティを設定することで、特定のプロトコルを必要とする特定の種類のペイロードを処理するためのエンドポイント サービスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e7867-105">You can create an endpoint service that handles a specific type of payload, which uses a specific protocol, by creating an instance of an <xref:Microsoft.SqlServer.Management.Smo.Endpoint> object and setting its properties.</span></span>  
  
 <span data-ttu-id="e7867-106"><xref:Microsoft.SqlServer.Management.Smo.Endpoint.EndpointType%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Endpoint> プロパティを使用して、次の種類のペイロードの 1 つを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="e7867-106">The <xref:Microsoft.SqlServer.Management.Smo.Endpoint.EndpointType%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Endpoint> object can be used to specify on of the following payload types:</span></span>  
  
-   <span data-ttu-id="e7867-107">データベース ミラーリング</span><span class="sxs-lookup"><span data-stu-id="e7867-107">Database mirroring</span></span>  
  
-   <span data-ttu-id="e7867-108">SOAP (SOAP エンドポイントは、 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] および以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でサポートされます)</span><span class="sxs-lookup"><span data-stu-id="e7867-108">SOAP (support for SOAP endpoints is present in [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] and earlier [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] versions)</span></span>  
  
-   <span data-ttu-id="e7867-109">Service Broker</span><span class="sxs-lookup"><span data-stu-id="e7867-109">Service Broker</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)]  
  
 <span data-ttu-id="e7867-110">また、<xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> プロパティを使用して、サポートされている次の 2 つのプロトコルを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="e7867-110">Also, the <xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> property can be used to specify the following two supported protocols:</span></span>  
  
-   <span data-ttu-id="e7867-111">HTTP プロトコル</span><span class="sxs-lookup"><span data-stu-id="e7867-111">HTTP protocol</span></span>  
  
-   <span data-ttu-id="e7867-112">TCP プロトコル</span><span class="sxs-lookup"><span data-stu-id="e7867-112">TCP protocol</span></span>  
  
 <span data-ttu-id="e7867-113">ペイロードの種類を指定すると、<xref:Microsoft.SqlServer.Management.Smo.Endpoint.Payload%2A> オブジェクト プロパティを使用して実際のペイロードを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="e7867-113">Having specified the type of payload, the actual payload can be set by using the <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Payload%2A> object property.</span></span> <span data-ttu-id="e7867-114"><xref:Microsoft.SqlServer.Management.Smo.Payload> オブジェクト プロパティは、プロパティを変更できる、指定された種類のペイロード オブジェクトへの参照を提供します。</span><span class="sxs-lookup"><span data-stu-id="e7867-114">The <xref:Microsoft.SqlServer.Management.Smo.Payload> object property provides a reference to a payload object of the specified type, for which the properties can be modified.</span></span>  
  
 <span data-ttu-id="e7867-115"><xref:Microsoft.SqlServer.Management.Smo.DatabaseMirroringPayload> オブジェクトに対して、ミラーリング ロール、および暗号化が有効であるかどうかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e7867-115">For the <xref:Microsoft.SqlServer.Management.Smo.DatabaseMirroringPayload> object, you must specify the mirroring role and whether encryption is enabled.</span></span> <span data-ttu-id="e7867-116"><xref:Microsoft.SqlServer.Management.Smo.ServiceBrokerPayload> オブジェクトには、メッセージ転送、許可される最大接続数、および認証モードに関する情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="e7867-116">The <xref:Microsoft.SqlServer.Management.Smo.ServiceBrokerPayload> object requires information about message forwarding, maximum number of connections allowed and the authentication mode.</span></span> <span data-ttu-id="e7867-117"><xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethod.%23ctor%2A> オブジェクトでは、さまざまなプロパティの設定が必要です。これには、クライアントが使用できる SOAP ペイロード メソッド (ストアド プロシージャおよびユーザー定義関数) を指定する、<xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethodCollection.Add%2A> オブジェクト プロパティなどがあります。</span><span class="sxs-lookup"><span data-stu-id="e7867-117">The <xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethod.%23ctor%2A> object requires various properties to be set including the <xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethodCollection.Add%2A> object property that specifies the SOAP payload methods available to clients (stored procedures and user-defined functions).</span></span>  
  
 <span data-ttu-id="e7867-118"><xref:Microsoft.SqlServer.Management.Smo.Endpoint.Protocol%2A> オブジェクト プロパティを使用すると、<xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> プロパティで指定された型のプロトコル オブジェクトを参照して、実際のプロトコルを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="e7867-118">Similarly, the actual protocol can be set by using the <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Protocol%2A> object property that references a protocol object of the type specified by <xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> property.</span></span> <span data-ttu-id="e7867-119"><xref:Microsoft.SqlServer.Management.Smo.HttpProtocol> オブジェクトには、制限された IP アドレス、ポート、Web サイト、および認証情報のリストが必要です。</span><span class="sxs-lookup"><span data-stu-id="e7867-119">The <xref:Microsoft.SqlServer.Management.Smo.HttpProtocol> object requires a list of restricted IP addresses, and port, website, and authentication information.</span></span> <span data-ttu-id="e7867-120">また、<xref:Microsoft.SqlServer.Management.Smo.TcpProtocol> オブジェクトには、制限された IP アドレスおよびポート情報のリストも必要です。</span><span class="sxs-lookup"><span data-stu-id="e7867-120">The <xref:Microsoft.SqlServer.Management.Smo.TcpProtocol> object also requires a list of restricted IP addresses and port information.</span></span>  
  
 <span data-ttu-id="e7867-121">エンドポイントを作成して定義を完了したら、データベース ユーザー、グループ、ロール、およびログオンに対して、アクセスの許可、取り消し、および拒否を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="e7867-121">When the endpoint has been created and fully defined, access can be granted to, revoked from, and denied to database users, groups, roles, and logons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7867-122">例</span><span class="sxs-lookup"><span data-stu-id="e7867-122">Example</span></span>  
 <span data-ttu-id="e7867-123">次のコード例では、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e7867-123">For the following code example, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="e7867-124">詳細については、「 [Visual studio .net での VISUAL BASIC Smo プロジェクトの作成](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)」および「visual [Studio .Net で VISUAL C&#35; Smo プロジェクトを作成](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7867-124">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-visual-basic"></a><span data-ttu-id="e7867-125">Visual Basic でのデータベース ミラーリング エンドポイント サービスの作成</span><span class="sxs-lookup"><span data-stu-id="e7867-125">Creating a Database Mirroring Endpoint Service in Visual Basic</span></span>  
 <span data-ttu-id="e7867-126">コード例では、SMO でデータベース ミラーリング エンドポイントを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e7867-126">The code example demonstrates how to create a Database Mirroring endpoint in SMO.</span></span> <span data-ttu-id="e7867-127">これは、データベース ミラーを作成する前に必要な操作です。</span><span class="sxs-lookup"><span data-stu-id="e7867-127">This is necessary before you create a database mirror.</span></span> <span data-ttu-id="e7867-128"><xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Database> プロパティおよびその他のプロパティを使用して、データベース ミラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e7867-128">Use the <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> and other properties on the <xref:Microsoft.SqlServer.Management.Smo.Database> object to create a database mirror.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBEndpoints1](SMO How to#SMO_VBEndpoints1)]  -->  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-visual-c"></a><span data-ttu-id="e7867-129">Visual C# でのデータベース ミラーリング エンドポイント サービスの作成</span><span class="sxs-lookup"><span data-stu-id="e7867-129">Creating a Database Mirroring Endpoint Service in Visual C#</span></span>  
 <span data-ttu-id="e7867-130">コード例では、SMO でデータベース ミラーリング エンドポイントを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e7867-130">The code example demonstrates how to create a Database Mirroring endpoint in SMO.</span></span> <span data-ttu-id="e7867-131">これは、データベース ミラーを作成する前に必要な操作です。</span><span class="sxs-lookup"><span data-stu-id="e7867-131">This is necessary before you create a database mirror.</span></span> <span data-ttu-id="e7867-132"><xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Database> プロパティおよびその他のプロパティを使用して、データベース ミラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e7867-132">Use the <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> and other properties on the <xref:Microsoft.SqlServer.Management.Smo.Database> object to create a database mirror.</span></span>  
  
```csharp
{  
            //Set up a database mirroring endpoint on the server before   
        //setting up a database mirror.   
        //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Define an Endpoint object variable for database mirroring.   
            Endpoint ep = default(Endpoint);  
            ep = new Endpoint(srv, "Mirroring_Endpoint");  
            ep.ProtocolType = ProtocolType.Tcp;  
            ep.EndpointType = EndpointType.DatabaseMirroring;  
            //Specify the protocol ports.   
            ep.Protocol.Http.SslPort = 5024;  
            ep.Protocol.Tcp.ListenerPort = 6666;  
            //Specify the role of the payload.   
            ep.Payload.DatabaseMirroring.ServerMirroringRole = ServerMirroringRole.All;  
            //Create the endpoint on the instance of SQL Server.   
            ep.Create();  
            //Start the endpoint.   
            ep.Start();  
            Console.WriteLine(ep.EndpointState);  
        }  
```  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-powershell"></a><span data-ttu-id="e7867-133">PowerShell でのデータベース ミラーリング エンドポイント サービスの作成</span><span class="sxs-lookup"><span data-stu-id="e7867-133">Creating a Database Mirroring Endpoint Service in PowerShell</span></span>  
 <span data-ttu-id="e7867-134">コード例では、SMO でデータベース ミラーリング エンドポイントを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e7867-134">The code example demonstrates how to create a Database Mirroring endpoint in SMO.</span></span> <span data-ttu-id="e7867-135">これは、データベース ミラーを作成する前に必要な操作です。</span><span class="sxs-lookup"><span data-stu-id="e7867-135">This is necessary before you create a database mirror.</span></span> <span data-ttu-id="e7867-136"><xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Database> プロパティおよびその他のプロパティを使用して、データベース ミラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e7867-136">Use the <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> and other properties on the <xref:Microsoft.SqlServer.Management.Smo.Database> object to create a database mirror.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = Get-Item default  
  
#Get a new endpoint to congure and add  
$ep = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Endpoint -argumentlist $srv,"Mirroring_Endpoint"  
  
#Set some properties  
$ep.ProtocolType = [Microsoft.SqlServer.Management.SMO.ProtocolType]::Tcp  
$ep.EndpointType = [Microsoft.SqlServer.Management.SMO.EndpointType]::DatabaseMirroring  
$ep.Protocol.Http.SslPort = 5024  
$ep.Protocol.Tcp.ListenerPort = 6666 #inline comment  
$ep.Payload.DatabaseMirroring.ServerMirroringRole = [Microsoft.SqlServer.Management.SMO.ServerMirroringRole]::All  
  
# Create the endpoint on the instance  
$ep.Create()  
  
# Start the endpoint  
$ep.Start()  
  
# Report its state  
$ep.EndpointState;  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7867-137">参照</span><span class="sxs-lookup"><span data-stu-id="e7867-137">See Also</span></span>  
 [<span data-ttu-id="e7867-138">データベース ミラーリング エンドポイント &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e7867-138">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](../../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
