---
title: プログラムによる接続の追加 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- connection managers [Integration Services], packages
- Integration Services packages, connections
- connections [Integration Services], packages
- SSIS packages, connections
- packages [Integration Services], connections
- intrinsic properties [Integration Services]
- SQL Server Integration Services packages, connections
- ConnectionManager class
- SSIS connection managers
- adding package connections
ms.assetid: d90716d1-4c65-466c-b82c-4aabbee1e3e5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a5952221dbf2689d2328695baf965ce884dc07fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639615"
---
# <a name="adding-connections-programmatically"></a><span data-ttu-id="e23f1-102">プログラムによる接続の追加</span><span class="sxs-lookup"><span data-stu-id="e23f1-102">Adding Connections Programmatically</span></span>
  <span data-ttu-id="e23f1-103"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> クラスは、外部データ ソースへの物理接続を表します。</span><span class="sxs-lookup"><span data-stu-id="e23f1-103">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> class represents physical connections to external data sources.</span></span> <span data-ttu-id="e23f1-104"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> クラスは、ランタイムから接続の実装詳細を分離します。</span><span class="sxs-lookup"><span data-stu-id="e23f1-104">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> class isolates the implementation details of the connection from the runtime.</span></span> <span data-ttu-id="e23f1-105">これにより、ランタイムは、一貫した予測可能な方法でそれぞれの接続マネージャーとやり取りを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="e23f1-105">This enables the runtime to interact with each connection manager in a consistent and predictable manner.</span></span> <span data-ttu-id="e23f1-106">接続マネージャーには、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A>、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ID%2A>、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Description%2A>、および <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A> など、すべての接続に共通のストック プロパティのセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e23f1-106">Connection managers contain a set of stock properties that all connections have in common, such as the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ID%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Description%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A>.</span></span> <span data-ttu-id="e23f1-107">ただし、接続マネージャーを構成するために必要なプロパティは、通常 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A> および <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A> プロパティのみです。</span><span class="sxs-lookup"><span data-stu-id="e23f1-107">However, the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A> properties are ordinarily the only properties required to configure a connection manager.</span></span> <span data-ttu-id="e23f1-108">接続クラスが `Open` や `Connect` などのメソッドを公開して物理的にデータ ソースへの接続を確立する他のプログラミング パラダイムと異なり、ランタイム エンジンは、パッケージの実行中に、そのパッケージのすべての接続を管理します。</span><span class="sxs-lookup"><span data-stu-id="e23f1-108">Unlike other programming paradigms, where connection classes expose methods such as `Open` or `Connect` to physically establish a connection to the data source, the run-time engine manages all the connections for the package while it runs.</span></span>  
  
 <span data-ttu-id="e23f1-109"><xref:Microsoft.SqlServer.Dts.Runtime.Connections> クラスは、パッケージに追加されて実行時に使用できる接続マネージャーのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="e23f1-109">The <xref:Microsoft.SqlServer.Dts.Runtime.Connections> class is a collection of the connection managers that have been added to that package and are available for use at run time.</span></span> <span data-ttu-id="e23f1-110">コレクションの <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Add%2A> メソッドを使用し、接続マネージャーの種類を示す文字列を指定することによって、接続マネージャーをコレクションに追加できます。</span><span class="sxs-lookup"><span data-stu-id="e23f1-110">You can add more connection managers to the collection by using the <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Add%2A> method of the collection, and supplying a string that indicates the connection manager type.</span></span> <span data-ttu-id="e23f1-111"><xref:Microsoft.SqlServer.Dts.Runtime.Connections.Add%2A> メソッドは、パッケージに追加された <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> のインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="e23f1-111">The <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Add%2A> method returns the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> instance that was added to the package.</span></span>  
  
## <a name="intrinsic-properties"></a><span data-ttu-id="e23f1-112">固有プロパティ</span><span class="sxs-lookup"><span data-stu-id="e23f1-112">Intrinsic Properties</span></span>  
 <span data-ttu-id="e23f1-113"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> クラスは、すべての接続に共通のプロパティのセットを公開します。</span><span class="sxs-lookup"><span data-stu-id="e23f1-113">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> class exposes a set of properties that are common to all connections.</span></span> <span data-ttu-id="e23f1-114">ただし、特定の接続の種類に固有のプロパティにアクセスする必要が生じる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e23f1-114">However, sometimes you need access to properties that are unique to the specific connection type.</span></span> <span data-ttu-id="e23f1-115"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Properties%2A> クラスの <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> コレクションは、これらのプロパティへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="e23f1-115">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Properties%2A> collection of the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> class provides access to these properties.</span></span> <span data-ttu-id="e23f1-116">プロパティをコレクションから取得するには、インデクサーまたはプロパティ名、および **GetValue** メソッドを使用し、その値を設定するには **SetValue** メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="e23f1-116">The properties can be retrieved from the collection using the indexer or the property name and the **GetValue** method, and the values are set using the **SetValue** method.</span></span> <span data-ttu-id="e23f1-117">基になる接続オブジェクトのプロパティには、オブジェクトの実際のインスタンスを取得し、そのプロパティを直接設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="e23f1-117">The properties of the underlying connection object properties can also be set by acquiring an actual instance of the object and setting its properties directly.</span></span> <span data-ttu-id="e23f1-118">基になる接続を取得するには、接続マネージャーの <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.InnerObject%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="e23f1-118">To get the underlying connection, use the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.InnerObject%2A> property of the connection manager.</span></span> <span data-ttu-id="e23f1-119">次のコード行は、基になるクラス <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.ConnectionManagerAdoNetClass> を持つ ADO.NET 接続マネージャーを作成する C# の行を示しています。</span><span class="sxs-lookup"><span data-stu-id="e23f1-119">The following line of code shows a C# line that creates an ADO.NET connection manager that has the underlying class, <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.ConnectionManagerAdoNetClass>.</span></span>  
  
 `ConnectionManagerAdoNetClass cmado = cm.InnerObject as ConnectionManagerAdoNet;`  
  
 <span data-ttu-id="e23f1-120">これは、マネージド接続マネージャー オブジェクトを、その基になる接続オブジェクトにキャストします。</span><span class="sxs-lookup"><span data-stu-id="e23f1-120">This casts the managed connection manager object to its underlying connection object.</span></span> <span data-ttu-id="e23f1-121">C++ を使用している場合、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> オブジェクトの `QueryInterface` メソッドが呼び出され、基になる接続オブジェクトのインターフェイスが要求されます。</span><span class="sxs-lookup"><span data-stu-id="e23f1-121">If you are using C++, the `QueryInterface` method of the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> object is called and the interface of the underlying connection object is requested.</span></span>  
  
 <span data-ttu-id="e23f1-122">次の表は、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] が備えている接続マネージャーと</span><span class="sxs-lookup"><span data-stu-id="e23f1-122">The following table lists the connection managers included with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="e23f1-123">`package.Connections.Add("xxx")` ステートメントで使用される文字列を示しています。</span><span class="sxs-lookup"><span data-stu-id="e23f1-123">and the string that is used in the `package.Connections.Add("xxx")` statement.</span></span> <span data-ttu-id="e23f1-124">すべての接続マネージャーのリストについては、「[Integration Services &#40;SSIS&#41; の接続](../connection-manager/integration-services-ssis-connections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e23f1-124">For a list of all connection managers, see [Integration Services &#40;SSIS&#41; Connections](../connection-manager/integration-services-ssis-connections.md).</span></span>  
  
|<span data-ttu-id="e23f1-125">String</span><span class="sxs-lookup"><span data-stu-id="e23f1-125">String</span></span>|<span data-ttu-id="e23f1-126">[ODBC 入力元エディター]</span><span class="sxs-lookup"><span data-stu-id="e23f1-126">Connection manager</span></span>|  
|------------|------------------------|  
|<span data-ttu-id="e23f1-127">"OLEDB"</span><span class="sxs-lookup"><span data-stu-id="e23f1-127">"OLEDB"</span></span>|<span data-ttu-id="e23f1-128">OLE DB 接続用の接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="e23f1-128">Connection manager for OLE DB connections.</span></span>|  
|<span data-ttu-id="e23f1-129">"ODBC"</span><span class="sxs-lookup"><span data-stu-id="e23f1-129">"ODBC"</span></span>|<span data-ttu-id="e23f1-130">ODBC 接続用の接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="e23f1-130">Connection manager for ODBC connections.</span></span>|  
|<span data-ttu-id="e23f1-131">"ADO"</span><span class="sxs-lookup"><span data-stu-id="e23f1-131">"ADO"</span></span>|<span data-ttu-id="e23f1-132">ADO 接続用の接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="e23f1-132">Connection manager for ADO connections.</span></span>|  
|<span data-ttu-id="e23f1-133">"ADO.NET:SQL"</span><span class="sxs-lookup"><span data-stu-id="e23f1-133">"ADO.NET:SQL"</span></span>|<span data-ttu-id="e23f1-134">ADO.NET (SQL データ プロバイダー) 接続用の接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="e23f1-134">Connection manager for ADO.NET (SQL data provider) connections.</span></span>|  
|<span data-ttu-id="e23f1-135">"ADO.NET:OLEDB"</span><span class="sxs-lookup"><span data-stu-id="e23f1-135">"ADO.NET:OLEDB"</span></span>|<span data-ttu-id="e23f1-136">ADO.NET (OLE DB データ プロバイダー) 接続用の接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="e23f1-136">Connection manager for ADO.NET (OLE DB data provider) connections.</span></span>|  
|<span data-ttu-id="e23f1-137">"FLATFILE"</span><span class="sxs-lookup"><span data-stu-id="e23f1-137">"FLATFILE"</span></span>|<span data-ttu-id="e23f1-138">フラット ファイル接続用の接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="e23f1-138">Connection manager for flat file connections.</span></span>|  
|<span data-ttu-id="e23f1-139">"FILE"</span><span class="sxs-lookup"><span data-stu-id="e23f1-139">"FILE"</span></span>|<span data-ttu-id="e23f1-140">ファイル接続用の接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="e23f1-140">Connection manager for file connections.</span></span>|  
|<span data-ttu-id="e23f1-141">"MULTIFLATFILE"</span><span class="sxs-lookup"><span data-stu-id="e23f1-141">"MULTIFLATFILE"</span></span>|<span data-ttu-id="e23f1-142">複数のフラット ファイル接続用の接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="e23f1-142">Connection manager for multiple flat file connections.</span></span>|  
|<span data-ttu-id="e23f1-143">"MULTIFILE"</span><span class="sxs-lookup"><span data-stu-id="e23f1-143">"MULTIFILE"</span></span>|<span data-ttu-id="e23f1-144">複数のファイル接続用の接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="e23f1-144">Connection manager for multiple file connections.</span></span>|  
|<span data-ttu-id="e23f1-145">"SQLMOBILE"</span><span class="sxs-lookup"><span data-stu-id="e23f1-145">"SQLMOBILE"</span></span>|<span data-ttu-id="e23f1-146">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 接続用の接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="e23f1-146">Connection manager for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connections.</span></span>|  
|<span data-ttu-id="e23f1-147">"MSOLAP100"</span><span class="sxs-lookup"><span data-stu-id="e23f1-147">"MSOLAP100"</span></span>|<span data-ttu-id="e23f1-148">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 接続用の接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="e23f1-148">Connection manager for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connections.</span></span>|  
|<span data-ttu-id="e23f1-149">"FTP"</span><span class="sxs-lookup"><span data-stu-id="e23f1-149">"FTP"</span></span>|<span data-ttu-id="e23f1-150">FTP 接続用の接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="e23f1-150">Connection manager for FTP connections.</span></span>|  
|<span data-ttu-id="e23f1-151">"HTTP"</span><span class="sxs-lookup"><span data-stu-id="e23f1-151">"HTTP"</span></span>|<span data-ttu-id="e23f1-152">HTTP 接続用の接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="e23f1-152">Connection manager for HTTP connections.</span></span>|  
|<span data-ttu-id="e23f1-153">"MSMQ"</span><span class="sxs-lookup"><span data-stu-id="e23f1-153">"MSMQ"</span></span>|<span data-ttu-id="e23f1-154">メッセージ キュー (MSMQ) 接続用の接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="e23f1-154">Connection manager for Message Queuing (also known as MSMQ) connections.</span></span>|  
|<span data-ttu-id="e23f1-155">"SMTP"</span><span class="sxs-lookup"><span data-stu-id="e23f1-155">"SMTP"</span></span>|<span data-ttu-id="e23f1-156">SMTP 接続用の接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="e23f1-156">Connection manager for SMTP connections.</span></span>|  
|<span data-ttu-id="e23f1-157">"WMI"</span><span class="sxs-lookup"><span data-stu-id="e23f1-157">"WMI"</span></span>|<span data-ttu-id="e23f1-158">WMI (Windows Management Instrumentation) 接続用の接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="e23f1-158">Connection manager for Microsoft Windows Management Instrumentation (WMI) connections.</span></span>|  
  
 <span data-ttu-id="e23f1-159">次のコード例では、OLE DB 接続およびファイル接続を <xref:Microsoft.SqlServer.Dts.Runtime.Package.Connections%2A> の <xref:Microsoft.SqlServer.Dts.Runtime.Package> コレクションに追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e23f1-159">The following code example demonstrates adding an OLE DB and FILE connection to the <xref:Microsoft.SqlServer.Dts.Runtime.Package.Connections%2A> collection of a <xref:Microsoft.SqlServer.Dts.Runtime.Package>.</span></span> <span data-ttu-id="e23f1-160">この例では、次に、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A>、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A>、および <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Description%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="e23f1-160">The example then sets the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Description%2A> properties.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      // Create a package, and retrieve its connections.  
      Package pkg = new Package();  
      Connections pkgConns = pkg.Connections;  
  
      // Add an OLE DB connection to the package, using the   
      // method defined in the AddConnection class.  
      CreateConnection myOLEDBConn = new CreateConnection();  
      myOLEDBConn.CreateOLEDBConnection(pkg);  
  
      // View the new connection in the package.  
      Console.WriteLine("Connection description: {0}",  
         pkg.Connections["SSIS Connection Manager for OLE DB"].Description);  
  
      // Add a second connection to the package.  
      CreateConnection myFileConn = new CreateConnection();  
      myFileConn.CreateFileConnection(pkg);  
  
      // View the second connection in the package.  
      Console.WriteLine("Connection description: {0}",  
        pkg.Connections["SSIS Connection Manager for Files"].Description);  
  
      Console.WriteLine();  
      Console.WriteLine("Number of connections in package: {0}", pkg.Connections.Count);  
  
      Console.Read();  
    }  
  }  
  // <summary>  
  // This class contains the definitions for multiple  
  // connection managers.  
  // </summary>  
  public class CreateConnection  
  {  
    // Private data.  
    private ConnectionManager ConMgr;  
  
    // Class definition for OLE DB Provider.  
    public void CreateOLEDBConnection(Package p)  
    {  
      ConMgr = p.Connections.Add("OLEDB");  
      ConMgr.ConnectionString = "Provider=SQLOLEDB.1;" +  
        "Integrated Security=SSPI;Initial Catalog=AdventureWorks;" +  
        "Data Source=(local);";  
      ConMgr.Name = "SSIS Connection Manager for OLE DB";  
      ConMgr.Description = "OLE DB connection to the AdventureWorks database.";  
    }  
    public void CreateFileConnection(Package p)  
    {  
      ConMgr = p.Connections.Add("File");  
      ConMgr.ConnectionString = @"\\<yourserver>\<yourfolder>\books.xml";  
      ConMgr.Name = "SSIS Connection Manager for Files";  
      ConMgr.Description = "Flat File connection";  
    }  
  }  
  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    ' Create a package, and retrieve its connections.  
    Dim pkg As New Package()  
    Dim pkgConns As Connections = pkg.Connections  
  
    ' Add an OLE DB connection to the package, using the   
    ' method defined in the AddConnection class.  
    Dim myOLEDBConn As New CreateConnection()  
    myOLEDBConn.CreateOLEDBConnection(pkg)  
  
    ' View the new connection in the package.  
    Console.WriteLine("Connection description: {0}", _  
      pkg.Connections("SSIS Connection Manager for OLE DB").Description)  
  
    ' Add a second connection to the package.  
    Dim myFileConn As New CreateConnection()  
    myFileConn.CreateFileConnection(pkg)  
  
    ' View the second connection in the package.  
    Console.WriteLine("Connection description: {0}", _  
      pkg.Connections("SSIS Connection Manager for Files").Description)  
  
    Console.WriteLine()  
    Console.WriteLine("Number of connections in package: {0}", pkg.Connections.Count)  
  
    Console.Read()  
  
  End Sub  
  
End Module  
  
' This class contains the definitions for multiple  
' connection managers.  
  
Public Class CreateConnection  
  ' Private data.  
  Private ConMgr As ConnectionManager  
  
  ' Class definition for OLE DB provider.  
  Public Sub CreateOLEDBConnection(ByVal p As Package)  
    ConMgr = p.Connections.Add("OLEDB")  
    ConMgr.ConnectionString = "Provider=SQLOLEDB.1;" & _  
      "Integrated Security=SSPI;Initial Catalog=AdventureWorks;" & _  
      "Data Source=(local);"  
    ConMgr.Name = "SSIS Connection Manager for OLE DB"  
    ConMgr.Description = "OLE DB connection to the AdventureWorks database."  
  End Sub  
  
  Public Sub CreateFileConnection(ByVal p As Package)  
    ConMgr = p.Connections.Add("File")  
    ConMgr.ConnectionString = "\\<yourserver>\<yourfolder>\books.xml"  
    ConMgr.Name = "SSIS Connection Manager for Files"  
    ConMgr.Description = "Flat File connection"  
  End Sub  
  
End Class  
```  
  
 <span data-ttu-id="e23f1-161">**サンプル出力:**</span><span class="sxs-lookup"><span data-stu-id="e23f1-161">**Sample Output:**</span></span>  
  
 `Connection description: OLE DB connection to the AdventureWorks database.`  
  
 `Connection description: OLE DB connection to the AdventureWorks database.`  
  
 `Number of connections in package: 2`  
  
## <a name="external-resources"></a><span data-ttu-id="e23f1-162">外部リソース</span><span class="sxs-lookup"><span data-stu-id="e23f1-162">External Resources</span></span>  
 <span data-ttu-id="e23f1-163">carlprothman.net の [接続文字列](https://go.microsoft.com/fwlink/?LinkId=220743)に関する技術記事</span><span class="sxs-lookup"><span data-stu-id="e23f1-163">Technical article, [Connection Strings](https://go.microsoft.com/fwlink/?LinkId=220743), on carlprothman.net.</span></span>  
  
<span data-ttu-id="e23f1-164">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="e23f1-164">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="e23f1-165">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e23f1-165">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="e23f1-166">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="e23f1-166">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="e23f1-167">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="e23f1-167">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e23f1-168">参照</span><span class="sxs-lookup"><span data-stu-id="e23f1-168">See Also</span></span>  
 <span data-ttu-id="e23f1-169">[SSIS&#41; 接続の Integration Services &#40;](../connection-manager/integration-services-ssis-connections.md) </span><span class="sxs-lookup"><span data-stu-id="e23f1-169">[Integration Services &#40;SSIS&#41; Connections](../connection-manager/integration-services-ssis-connections.md) </span></span>  
 [<span data-ttu-id="e23f1-170">接続マネージャーを作成する</span><span class="sxs-lookup"><span data-stu-id="e23f1-170">Create Connection Managers</span></span>](../create-connection-managers.md)  
  
  
