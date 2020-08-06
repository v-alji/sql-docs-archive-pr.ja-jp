---
title: カスタム タスクでのデータ ソースへの接続 | Microsoft Docs
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
- ConnectionManager objects
- connection managers [Integration Services], external data sources
- data sources [Integration Services], external
- custom tasks [Integration Services], external data sources
- external data sources [Integration Services]
- connections [Integration Services], external data sources
- SSIS custom tasks, external data sources
ms.assetid: 9f0b3a43-3eaa-4b3c-bb08-29b630c11306
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 71c504f4b528a0c9809d00de74de4beb9c67c4f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642188"
---
# <a name="connecting-to-data-sources-in-a-custom-task"></a><span data-ttu-id="5f05a-102">カスタム タスクでのデータ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="5f05a-102">Connecting to Data Sources in a Custom Task</span></span>
  <span data-ttu-id="5f05a-103">タスクは、接続マネージャーを使用して外部データ ソースに接続し、データを取得または保存します。</span><span class="sxs-lookup"><span data-stu-id="5f05a-103">Tasks connect to external data sources to retrieve or save data by using a connection manager.</span></span> <span data-ttu-id="5f05a-104">デザイン時には、接続マネージャーは論理接続を表し、サーバー名や認証プロパティなどの重要な情報を示します。</span><span class="sxs-lookup"><span data-stu-id="5f05a-104">At design time, a connection manager represents a logical connection, and describes key information such as the server name and any authentication properties.</span></span> <span data-ttu-id="5f05a-105">実行時に、タスクは接続マネージャーの <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> メソッドを呼び出して、データ ソースへの物理接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="5f05a-105">At run time, tasks call the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method of the connection manager to establish the physical connection to the data source.</span></span>  
  
 <span data-ttu-id="5f05a-106">パッケージに多数のタスクが含まれていると、各タスクに異なるデータ ソースへの接続が含まれる場合があるため、パッケージは <xref:Microsoft.SqlServer.Dts.Runtime.Connections> コレクション内のすべての接続マネージャーを監視します。</span><span class="sxs-lookup"><span data-stu-id="5f05a-106">Because a package can contain many tasks, each of which may have connections to different data sources, the package tracks all the connection managers in a collection, the <xref:Microsoft.SqlServer.Dts.Runtime.Connections> collection.</span></span> <span data-ttu-id="5f05a-107">タスクはパッケージ内にあるコレクションを使用し、検証および実行中に使用する接続マネージャーを検索します。</span><span class="sxs-lookup"><span data-stu-id="5f05a-107">Tasks use the collection in their package to find the connection manager that they will use during validation and execution.</span></span> <span data-ttu-id="5f05a-108"><xref:Microsoft.SqlServer.Dts.Runtime.Connections> コレクションは、<xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> および <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> メソッドの最初のパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="5f05a-108">The <xref:Microsoft.SqlServer.Dts.Runtime.Connections> collection is the first parameter to the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> methods.</span></span>  
  
 <span data-ttu-id="5f05a-109">グラフィカル ユーザー インターフェイスのダイアログ ボックスまたはドロップダウン リストを使用して、コレクションの <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> オブジェクトをユーザーに表示すると、タスクで間違った接続マネージャーが使用されないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="5f05a-109">You can prevent the task from using the wrong connection manager by displaying the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects from the collection to the user, by using a dialog box or drop-down list in the graphical user interface.</span></span> <span data-ttu-id="5f05a-110">これによりユーザーは、パッケージ内に含まれる適切な型の <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> オブジェクトのみから選択できるようになります。</span><span class="sxs-lookup"><span data-stu-id="5f05a-110">This gives the user a way to select from among only those <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects of the appropriate type that are contained in the package.</span></span>  
  
 <span data-ttu-id="5f05a-111">タスクは、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> メソッドを呼び出し、データ ソースに対する物理接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="5f05a-111">Tasks call the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method to establish the physical connection to the data source.</span></span> <span data-ttu-id="5f05a-112">メソッドは基になる接続オブジェクトを返し、タスクはその接続オブジェクトを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5f05a-112">The method returns the underlying connection object that can then be used by the task.</span></span> <span data-ttu-id="5f05a-113">接続マネージャーは、基になる接続オブジェクトの実装の詳細をタスクから分離します。そのため、接続を確立するには、タスクは <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> メソッドを呼び出すだけでよく、接続の他の側面を考慮する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5f05a-113">Because the connection manager isolates the implementation details of the underlying connection object from the task, the task only has to call the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method to establish the connection, and does not have to be concerned with other aspects of the connection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f05a-114">例</span><span class="sxs-lookup"><span data-stu-id="5f05a-114">Example</span></span>  
 <span data-ttu-id="5f05a-115">次の例では、Validate および Execute メソッドで <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 名を検証し、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> メソッドを使用して Execute メソッド内に物理接続を確立する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5f05a-115">The following sample code demonstrates validation of the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> name in the Validate and Execute methods, and shows how to use the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method to establish the physical connection in the Execute method.</span></span>  
  
```csharp  
private string connectionManagerName = "";  
  
public string ConnectionManagerName  
{  
  get { return this.connectionManagerName; }  
  set { this.connectionManagerName = value; }  
}  
  
public override DTSExecResult Validate(  
  Connections connections, VariableDispenser variableDispenser,  
  IDTSComponentEvents componentEvents, IDTSLogging log)  
{  
  // If the connection manager exists, validation is successful;  
  // otherwise, fail validation.  
  try  
  {  
    ConnectionManager cm = connections[this.connectionManagerName];  
    return DTSExecResult.Success;  
  }  
  catch (System.Exception e)  
  {  
    componentEvents.FireError(0, "SampleTask", "Invalid connection manager.", "", 0);  
    return DTSExecResult.Failure;  
  }  
}  
  
public override DTSExecResult Execute(Connections connections,   
  VariableDispenser variableDispenser, IDTSComponentEvents componentEvents,   
  IDTSLogging log, object transaction)  
{  
  try  
  {  
    ConnectionManager cm = connections[this.connectionManagerName];  
    object connection = cm.AcquireConnection(transaction);  
    return DTSExecResult.Success;  
  }  
  catch (System.Exception exception)  
  {  
    componentEvents.FireError(0, "SampleTask", exception.Message, "", 0);  
    return DTSExecResult.Failure;  
  }  
}  
```  
  
```vb  
Private _connectionManagerName As String = ""  
  
Public Property ConnectionManagerName() As String  
  Get  
    Return Me._connectionManagerName  
  End Get  
  Set(ByVal Value As String)  
    Me._connectionManagerName = value  
  End Set  
End Property  
  
Public Overrides Function Validate( _  
  ByVal connections As Microsoft.SqlServer.Dts.Runtime.Connections, _  
  ByVal variableDispenser As Microsoft.SqlServer.Dts.Runtime.VariableDispenser, _  
  ByVal componentEvents As Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents, _  
  ByVal log As Microsoft.SqlServer.Dts.Runtime.IDTSLogging) _  
  As Microsoft.SqlServer.Dts.Runtime.DTSExecResult  
  
  ' If the connection manager exists, validation is successful;  
  ' otherwise fail validation.  
  Try  
    Dim cm As ConnectionManager = connections(Me._connectionManagerName)  
    Return DTSExecResult.Success  
  Catch e As System.Exception  
    componentEvents.FireError(0, "SampleTask", "Invalid connection manager.", "", 0)  
    Return DTSExecResult.Failure  
  End Try  
  
End Function  
  
Public Overrides Function Execute( _  
  ByVal connections As Microsoft.SqlServer.Dts.Runtime.Connections, _  
  ByVal variableDispenser As Microsoft.SqlServer.Dts.Runtime.VariableDispenser, _  
  ByVal componentEvents As Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents, _  
  ByVal log As Microsoft.SqlServer.Dts.Runtime.IDTSLogging, ByVal transaction As Object) _  
  As Microsoft.SqlServer.Dts.Runtime.DTSExecResult  
  
  Try  
    Dim cm As ConnectionManager = connections(Me._connectionManagerName)  
    Dim connection As Object = cm.AcquireConnection(transaction)  
    Return DTSExecResult.Success  
  Catch exception As System.Exception  
    componentEvents.FireError(0, "SampleTask", exception.Message, "", 0)  
    Return DTSExecResult.Failure  
  End Try  
  
End Function  
```  
  
<span data-ttu-id="5f05a-116">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="5f05a-116">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="5f05a-117">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f05a-117">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="5f05a-118">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="5f05a-118">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="5f05a-119">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="5f05a-119">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f05a-120">参照</span><span class="sxs-lookup"><span data-stu-id="5f05a-120">See Also</span></span>  
 <span data-ttu-id="5f05a-121">[SSIS&#41; 接続の Integration Services &#40;](../../connection-manager/integration-services-ssis-connections.md) </span><span class="sxs-lookup"><span data-stu-id="5f05a-121">[Integration Services &#40;SSIS&#41; Connections](../../connection-manager/integration-services-ssis-connections.md) </span></span>  
 [<span data-ttu-id="5f05a-122">接続マネージャーを作成する</span><span class="sxs-lookup"><span data-stu-id="5f05a-122">Create Connection Managers</span></span>](../../create-connection-managers.md)  
  
  
