---
title: SQL Server のインスタンスからの切断 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, disconnecting
- SMO [SQL Server], disconnecting
- instances of SQL Server, disconnecting
- disconnecting [SMO]
ms.assetid: 4ca7f7eb-6b3f-4c73-ac63-88afa8570b61
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3514fce8fb8f1ccc8bd1b54acfa27825eaebbd34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644958"
---
# <a name="disconnecting-from-an-instance-of-sql-server"></a><span data-ttu-id="e006d-102">SQL Server のインスタンスからの切断</span><span class="sxs-lookup"><span data-stu-id="e006d-102">Disconnecting from an Instance of SQL Server</span></span>
  <span data-ttu-id="e006d-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) オブジェクトを手動で閉じたり切断する処理は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="e006d-103">Manually closing and disconnecting [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) objects is not required.</span></span> <span data-ttu-id="e006d-104">接続を開いたり閉じたりする操作は、必要に応じて行われます。</span><span class="sxs-lookup"><span data-stu-id="e006d-104">Connections are opened and closed as required.</span></span>  
  
## <a name="connection-pooling"></a><span data-ttu-id="e006d-105">接続プール</span><span class="sxs-lookup"><span data-stu-id="e006d-105">Connection Pooling</span></span>  
 <span data-ttu-id="e006d-106"><xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> メソッドが呼び出された場合、接続は自動的には解放されません。</span><span class="sxs-lookup"><span data-stu-id="e006d-106">When the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> method is called, the connection is not automatically released.</span></span> <span data-ttu-id="e006d-107">接続プールに接続を解放するには、<xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> メソッドを明示的に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="e006d-107">The <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> method must be called explicitly to release the connection to the connection pool.</span></span> <span data-ttu-id="e006d-108">また、プールされていない接続を要求することもできます。</span><span class="sxs-lookup"><span data-stu-id="e006d-108">Also, you can request a non-pooled connection.</span></span> <span data-ttu-id="e006d-109">これを行うには、<xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> オブジェクトを参照する <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> プロパティの <xref:Microsoft.SqlServer.Management.Common.ServerConnection> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="e006d-109">You do this by setting the <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> property that references the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
## <a name="disconnecting-from-an-instance-of-sql-server-for-rmo"></a><span data-ttu-id="e006d-110">RMO の SQL Server のインスタンスからの切断</span><span class="sxs-lookup"><span data-stu-id="e006d-110">Disconnecting from an Instance of SQL Server for RMO</span></span>  
 <span data-ttu-id="e006d-111">RMO を使ったプログラミングでサーバー接続を閉じる方法は、SMO とは若干異なります。</span><span class="sxs-lookup"><span data-stu-id="e006d-111">Closing server connections when you are programming with RMO works slightly different from SMO.</span></span>  
  
 <span data-ttu-id="e006d-112">RMO オブジェクトのサーバー接続はオブジェクトによって維持されるため <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] rmo を使用してプログラムを作成するときに、このオブジェクトはのインスタンスから切断するときにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="e006d-112">Because the server connection for an RMO object is maintained by the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object, this object is also used when disconnecting from an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when you program by using RMO.</span></span> <span data-ttu-id="e006d-113"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトを使用して接続を閉じるには、RMO オブジェクトの <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e006d-113">To close a connection by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object, call the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> method of the RMO object.</span></span> <span data-ttu-id="e006d-114">接続が閉じられた後は、RMO オブジェクトを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="e006d-114">After the connection has been closed, RMO objects cannot be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e006d-115">例</span><span class="sxs-lookup"><span data-stu-id="e006d-115">Example</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-basic"></a><span data-ttu-id="e006d-116">Visual Basic で SMO オブジェクトを閉じたり切断する処理を行う方法</span><span class="sxs-lookup"><span data-stu-id="e006d-116">Closing and Disconnecting an SMO Object in Visual Basic</span></span>  
 <span data-ttu-id="e006d-117">このコード例では、<xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> オブジェクト プロパティの <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> プロパティを設定して、プールされていない接続を要求する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e006d-117">This code example shows how to request a non-pooled connection by setting the <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> object property.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB4](SMO How to#SMO_VB4)]  -->  
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-c"></a><span data-ttu-id="e006d-118">Visual C# で SMO オブジェクトを閉じたり切断する処理を行う方法</span><span class="sxs-lookup"><span data-stu-id="e006d-118">Closing and Disconnecting an SMO Object in Visual C#</span></span>  
 <span data-ttu-id="e006d-119">このコード例では、<xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> オブジェクト プロパティの <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> プロパティを設定して、プールされていない接続を要求する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e006d-119">This code example shows how to request a non-pooled connection by setting the <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> object property.</span></span>  
  
```  
{   
Server srv;   
srv = new Server();   
//Disable automatic disconnection.   
srv.ConnectionContext.AutoDisconnectMode = AutoDisconnectMode.NoAutoDisconnect;   
//Connect to the local, default instance of SQL Server.   
srv.ConnectionContext.Connect();   
//The actual connection is made when a property is retrieved.   
Console.WriteLine(srv.Information.Version);   
//Disconnect explicitly.   
srv.ConnectionContext.Disconnect();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e006d-120">参照</span><span class="sxs-lookup"><span data-stu-id="e006d-120">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  
