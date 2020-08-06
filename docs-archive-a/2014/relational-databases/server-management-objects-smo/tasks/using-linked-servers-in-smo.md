---
title: SMO でのリンクサーバーの使用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- linked servers [SQL Server], SMO
ms.assetid: 0ea8837b-2596-4df1-b065-3bb717c9f22c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 58804e2be1edfa685a57f56c173c77a50e0f9126
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632322"
---
# <a name="using-linked-servers-in-smo"></a><span data-ttu-id="44d4b-102">SMO でのリンク サーバーの使用</span><span class="sxs-lookup"><span data-stu-id="44d4b-102">Using Linked Servers in SMO</span></span>
  <span data-ttu-id="44d4b-103">リンク サーバーはリモート サーバー上の OLE DB データ ソースを表します。</span><span class="sxs-lookup"><span data-stu-id="44d4b-103">A linked server represents an OLE DB data source on a remote server.</span></span> <span data-ttu-id="44d4b-104">リモート OLE DB データ ソースは、<xref:Microsoft.SqlServer.Management.Smo.LinkedServer> オブジェクトを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスにリンクされます。</span><span class="sxs-lookup"><span data-stu-id="44d4b-104">Remote OLE DB data sources are linked to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using the <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> object.</span></span>  
  
 <span data-ttu-id="44d4b-105">リモートデータベースサーバーは、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] OLE DB プロバイダーを使用して、の現在のインスタンスにリンクすることができ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="44d4b-105">Remote database servers can be linked to the current instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using an OLE DB Provider.</span></span> <span data-ttu-id="44d4b-106">SMO では、リンク サーバーは <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> オブジェクトで表現されます。</span><span class="sxs-lookup"><span data-stu-id="44d4b-106">In SMO, linked servers are represented by the <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> object.</span></span> <span data-ttu-id="44d4b-107"><xref:Microsoft.SqlServer.Management.Smo.LinkedServer.LinkedServerLogins%2A> プロパティは <xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin> オブジェクトのコレクションを参照します。</span><span class="sxs-lookup"><span data-stu-id="44d4b-107">The <xref:Microsoft.SqlServer.Management.Smo.LinkedServer.LinkedServerLogins%2A> property references a collection of <xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin> objects.</span></span> <span data-ttu-id="44d4b-108">これらのオブジェクトには、リンク サーバーとの接続の確立に必要となるログオン資格情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="44d4b-108">These store the logon credentials that are required to establish a connection with the linked server.</span></span>  
  
## <a name="ole-db-providers"></a><span data-ttu-id="44d4b-109">OLE DB プロバイダー</span><span class="sxs-lookup"><span data-stu-id="44d4b-109">OLE-DB Providers</span></span>  
 <span data-ttu-id="44d4b-110">SMO では、インストールされた OLE DB プロバイダーは <xref:Microsoft.SqlServer.Management.Smo.OleDbProviderSettings> オブジェクトのコレクションで表されます。</span><span class="sxs-lookup"><span data-stu-id="44d4b-110">In SMO, installed OLE-DB providers are represented by a collection of <xref:Microsoft.SqlServer.Management.Smo.OleDbProviderSettings> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44d4b-111">例</span><span class="sxs-lookup"><span data-stu-id="44d4b-111">Example</span></span>  
 <span data-ttu-id="44d4b-112">次のコード例では、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="44d4b-112">For the following code example, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="44d4b-113">詳細については、「 [Visual studio .net での VISUAL BASIC Smo プロジェクトの作成](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)」および「visual [Studio .Net で VISUAL C&#35; Smo プロジェクトを作成](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44d4b-113">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-basic"></a><span data-ttu-id="44d4b-114">Visual Basic での OLE DB プロバイダー サーバーへのリンクの作成</span><span class="sxs-lookup"><span data-stu-id="44d4b-114">Creating a link to an OLE-DB Provider Server in Visual Basic</span></span>  
 <span data-ttu-id="44d4b-115">コード例では、<xref:Microsoft.SqlServer.Management.Smo.LinkedServer> オブジェクトを使用して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB 異種データ ソースへのリンクを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="44d4b-115">The code example shows how to create a link to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, heterogeneous data source by using the <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> object.</span></span> <span data-ttu-id="44d4b-116">製品名としてを指定することによって [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の公式 OLE DB プロバイダーであるクライアント OLE DB プロバイダーを使用して、リンクサーバー上のデータにアクセスし [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="44d4b-116">By specifying [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as the product name, data is accessed on the linked server by using the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client OLE DB Provider, which is the official OLE DB provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBLinkedServers1](SMO How to#SMO_VBLinkedServers1)]  -->  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-c"></a><span data-ttu-id="44d4b-117">Visual C# での OLE DB プロバイダー サーバーへのリンクの作成</span><span class="sxs-lookup"><span data-stu-id="44d4b-117">Creating a link to an OLE-DB Provider Server in Visual C#</span></span>  
 <span data-ttu-id="44d4b-118">コード例では、<xref:Microsoft.SqlServer.Management.Smo.LinkedServer> オブジェクトを使用して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB 異種データ ソースへのリンクを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="44d4b-118">The code example shows how to create a link to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, heterogeneous data source by using the <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> object.</span></span> <span data-ttu-id="44d4b-119">製品名として [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定することで、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用の正式な OLE DB プロバイダーである [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Client OLE DB プロバイダーを使用して、リンク サーバーのデータへのアクセスが行われます。</span><span class="sxs-lookup"><span data-stu-id="44d4b-119">By specifying [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as the product name, data is accessed on the linked server by using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client OLE DB Provider, which is the official OLE DB provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
```csharp
//Connect to the local, default instance of SQL Server.   
{   
   Server srv = new Server();   
   //Create a linked server.   
   LinkedServer lsrv = default(LinkedServer);   
   lsrv = new LinkedServer(srv, "OLEDBSRV");   
   //When the product name is SQL Server the remaining properties are   
   //not required to be set.   
   lsrv.ProductName = "SQL Server";   
   lsrv.Create();   
}   
```  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-powershell"></a><span data-ttu-id="44d4b-120">PowerShell での OLE DB プロバイダー サーバーへのリンクの作成</span><span class="sxs-lookup"><span data-stu-id="44d4b-120">Creating a link to an OLE-DB Provider Server in PowerShell</span></span>  
 <span data-ttu-id="44d4b-121">コード例では、<xref:Microsoft.SqlServer.Management.Smo.LinkedServer> オブジェクトを使用して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB 異種データ ソースへのリンクを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="44d4b-121">The code example shows how to create a link to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, heterogeneous data source by using the <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> object.</span></span> <span data-ttu-id="44d4b-122">製品名として [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定することで、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用の正式な OLE DB プロバイダーである [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Client OLE DB プロバイダーを使用して、リンク サーバーのデータへのアクセスが行われます。</span><span class="sxs-lookup"><span data-stu-id="44d4b-122">By specifying [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as the product name, data is accessed on the linked server by using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client OLE DB Provider, which is the official OLE DB provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance  
$svr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a linked server object which corresponds to an OLEDB type of SQL server product  
$lsvr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.LinkedServer -ArgumentList $svr,"OLEDBSRV"  
  
#When the product name is SQL Server the remaining properties are not required to be set.
$lsvr.ProductName = "SQL Server"
  
#Create the Database Object  
$lsvr.Create()
```  
