---
title: カスタム接続マネージャーのコーディング | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom connection managers [Integration Services], coding
ms.assetid: b12b6778-1f01-4a7d-984d-73f2f7630aa5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 793d70ba0a9ae6176ab35c82e16b9aba8c9ba2cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736588"
---
# <a name="coding-a-custom-connection-manager"></a><span data-ttu-id="f0e53-102">カスタム接続マネージャーのコーディング</span><span class="sxs-lookup"><span data-stu-id="f0e53-102">Coding a Custom Connection Manager</span></span>
  <span data-ttu-id="f0e53-103"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> 基本クラスを継承するクラスを作成し、<xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> 属性をそのクラスに適用したら、基本クラスのプロパティとメソッドの実装をオーバーライドして、カスタム機能を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0e53-103">After you have created a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> base class, and applied the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> attribute to the class, you must override the implementation of the properties and methods of the base class to provide your custom functionality.</span></span>  
  
 <span data-ttu-id="f0e53-104">カスタム接続マネージャーのサンプルについては、「[カスタム接続マネージャー用ユーザー インターフェイスの開発](developing-a-user-interface-for-a-custom-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0e53-104">For samples of custom connection managers, see [Developing a User Interface for a Custom Connection Manager](developing-a-user-interface-for-a-custom-connection-manager.md).</span></span> <span data-ttu-id="f0e53-105">このトピック内のコード例は、SQL Server カスタム接続マネージャーのサンプルに含まれています。</span><span class="sxs-lookup"><span data-stu-id="f0e53-105">The code examples shown in this topic are drawn from the SQL Server Custom Connection Manager sample.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0e53-106">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] に組み込まれているタスク、変換元、および変換先の多くは、組み込みの接続マネージャーの特定の種類でのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="f0e53-106">Most of the tasks, sources, and destinations that have been built into [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] work only with specific types of built-in connection managers.</span></span> <span data-ttu-id="f0e53-107">そのため、これらのサンプルは組み込みのタスクおよびコンポーネントではテストできません。</span><span class="sxs-lookup"><span data-stu-id="f0e53-107">Therefore, these samples cannot be tested with the built-in tasks and components.</span></span>  
  
## <a name="configuring-the-connection-manager"></a><span data-ttu-id="f0e53-108">接続マネージャーの構成</span><span class="sxs-lookup"><span data-stu-id="f0e53-108">Configuring the Connection Manager</span></span>  
  
### <a name="setting-the-connectionstring-property"></a><span data-ttu-id="f0e53-109">ConnectionString プロパティの設定</span><span class="sxs-lookup"><span data-stu-id="f0e53-109">Setting the ConnectionString Property</span></span>  
 <span data-ttu-id="f0e53-110"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> プロパティは重要なプロパティです。このプロパティだけが、カスタム接続マネージャーごとに一意です。</span><span class="sxs-lookup"><span data-stu-id="f0e53-110">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> property is an important property and the only property unique to a custom connection manager.</span></span> <span data-ttu-id="f0e53-111">接続マネージャーは、このプロパティの値を使用して、外部のデータ ソースへ接続します。</span><span class="sxs-lookup"><span data-stu-id="f0e53-111">The connection manager uses the value of this property to connect to the external data source.</span></span> <span data-ttu-id="f0e53-112">サーバー名やデータベース名など、他の複数のプロパティを組み合わせて接続文字列を作成する場合は、接続文字列テンプレートの一部の値をユーザー指定による新しい値に置き換えることによって文字列をアセンブルするためのヘルパー関数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0e53-112">If you are combining several other properties, such as server name and database name, to create the connection string, you can use a helper function to assemble the string by replacing certain values in a connection string template with the new value supplied by the user.</span></span> <span data-ttu-id="f0e53-113">次のコード例は、ヘルパー関数を使用して文字列をアセンブルする <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> プロパティを実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f0e53-113">The following code example shows an implementation of the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> property that relies on a helper function to assemble the string.</span></span>  
  
```vb  
' Default values.  
Private _serverName As String = "(local)"  
Private _databaseName As String = "AdventureWorks"  
Private _connectionString As String = String.Empty  
  
Private Const CONNECTIONSTRING_TEMPLATE As String = _  
  "Data Source=<servername>;Initial Catalog=<databasename>;Integrated Security=SSPI"  
  
Public Property ServerName() As String  
  Get  
    Return _serverName  
  End Get  
  Set(ByVal value As String)  
    _serverName = value  
  End Set  
End Property  
  
Public Property DatabaseName() As String  
  Get  
    Return _databaseName  
  End Get  
  Set(ByVal value As String)  
    _databaseName = value  
  End Set  
End Property  
  
Public Overrides Property ConnectionString() As String  
  Get  
    UpdateConnectionString()  
    Return _connectionString  
  End Get  
  Set(ByVal value As String)  
    _connectionString = value  
  End Set  
End Property  
  
Private Sub UpdateConnectionString()  
  
  Dim temporaryString As String = CONNECTIONSTRING_TEMPLATE  
  
  If Not String.IsNullOrEmpty(_serverName) Then  
    temporaryString = temporaryString.Replace("<servername>", _serverName)  
  End If  
  If Not String.IsNullOrEmpty(_databaseName) Then  
    temporaryString = temporaryString.Replace("<databasename>", _databaseName)  
  End If  
  
  _connectionString = temporaryString  
  
End Sub  
```  
  
```csharp  
// Default values.  
private string _serverName = "(local)";  
private string _databaseName = "AdventureWorks";  
private string _connectionString = String.Empty;  
  
private const string CONNECTIONSTRING_TEMPLATE = "Data Source=<servername>;Initial Catalog=<databasename>;Integrated Security=SSPI";  
  
public string ServerName  
{  
  get  
  {  
    return _serverName;  
  }  
  set  
  {  
    _serverName = value;  
  }  
}  
  
public string DatabaseName  
{  
  get  
  {  
    return _databaseName;  
  }  
  set  
  {  
    _databaseName = value;  
  }  
}  
  
public override string ConnectionString  
{  
  get  
  {  
    UpdateConnectionString();  
    return _connectionString;  
  }  
  set  
  {  
    _connectionString = value;  
  }  
}  
  
private void UpdateConnectionString()  
{  
  
  string temporaryString = CONNECTIONSTRING_TEMPLATE;  
  
  if (!String.IsNullOrEmpty(_serverName))  
  {  
    temporaryString = temporaryString.Replace("<servername>", _serverName);  
  }  
  
  if (!String.IsNullOrEmpty(_databaseName))  
  {  
    temporaryString = temporaryString.Replace("<databasename>", _databaseName);  
  }  
  
  _connectionString = temporaryString;  
  
}  
```  
  
### <a name="validating-the-connection-manager"></a><span data-ttu-id="f0e53-114">接続マネージャーの検証</span><span class="sxs-lookup"><span data-stu-id="f0e53-114">Validating the Connection Manager</span></span>  
 <span data-ttu-id="f0e53-115"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> メソッドをオーバーライドして、接続マネージャーが正しく構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f0e53-115">You override the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> method to make sure that the connection manager has been configured correctly.</span></span> <span data-ttu-id="f0e53-116">少なくとも、接続文字列の形式を検証し、すべての引数に値が指定されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f0e53-116">At a minimum, you should validate the format of the connection string and make sure that values have been provided for all arguments.</span></span> <span data-ttu-id="f0e53-117">接続マネージャーが <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success> メソッドから <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> を返すまでは、実行を続行できません。</span><span class="sxs-lookup"><span data-stu-id="f0e53-117">Execution cannot continue until the connection manager returns <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success> from the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="f0e53-118">次のコード例は、接続用のサーバー名がユーザーによって指定されていることを確認する <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> の実装を示します。</span><span class="sxs-lookup"><span data-stu-id="f0e53-118">The following code example shows an implementation of <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> that makes sure that the user has specified a server name for the connection.</span></span>  
  
```vb  
Public Overrides Function Validate(ByVal infoEvents As Microsoft.SqlServer.Dts.Runtime.IDTSInfoEvents) As Microsoft.SqlServer.Dts.Runtime.DTSExecResult  
  
  If String.IsNullOrEmpty(_serverName) Then  
    infoEvents.FireError(0, "SqlConnectionManager", "No server name specified", String.Empty, 0)  
    Return DTSExecResult.Failure  
  Else  
    Return DTSExecResult.Success  
  End If  
  
End Function  
```  
  
```csharp  
public override Microsoft.SqlServer.Dts.Runtime.DTSExecResult Validate(Microsoft.SqlServer.Dts.Runtime.IDTSInfoEvents infoEvents)  
{  
  
  if (String.IsNullOrEmpty(_serverName))  
  {  
    infoEvents.FireError(0, "SqlConnectionManager", "No server name specified", String.Empty, 0);  
    return DTSExecResult.Failure;  
  }  
  else  
  {  
    return DTSExecResult.Success;  
  }  
  
}  
```  
  
### <a name="persisting-the-connection-manager"></a><span data-ttu-id="f0e53-119">接続マネージャーの保存</span><span class="sxs-lookup"><span data-stu-id="f0e53-119">Persisting the Connection Manager</span></span>  
 <span data-ttu-id="f0e53-120">通常、接続マネージャーに対して、カスタムの永続性を実装する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f0e53-120">Usually, you do not have to implement custom persistence for a connection manager.</span></span> <span data-ttu-id="f0e53-121">カスタムの永続性は、オブジェクトのプロパティで複合データ型が使用されている場合にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="f0e53-121">Custom persistence is required only when the properties of an object use complex data types.</span></span> <span data-ttu-id="f0e53-122">詳細については、「[Integration Services 用のカスタム オブジェクトの開発](../developing-custom-objects-for-integration-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0e53-122">For more information, see [Developing Custom Objects for Integration Services](../developing-custom-objects-for-integration-services.md).</span></span>  
  
## <a name="working-with-the-external-data-source"></a><span data-ttu-id="f0e53-123">外部データ ソースの使用</span><span class="sxs-lookup"><span data-stu-id="f0e53-123">Working with the External Data Source</span></span>  
 <span data-ttu-id="f0e53-124">外部データ ソースへの接続をサポートするメソッドは、カスタム接続マネージャーにとって非常に重要なメソッドです。</span><span class="sxs-lookup"><span data-stu-id="f0e53-124">The methods that support connecting to an external data source are the most important methods of a custom connection manager.</span></span> <span data-ttu-id="f0e53-125"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> メソッドおよび <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> メソッドは、デザイン時と実行時のさまざまな時点で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f0e53-125">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> methods are called at various times during both design time and run time.</span></span>  
  
### <a name="acquiring-the-connection"></a><span data-ttu-id="f0e53-126">接続の取得</span><span class="sxs-lookup"><span data-stu-id="f0e53-126">Acquiring the Connection</span></span>  
 <span data-ttu-id="f0e53-127"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> メソッドの使用時にカスタム接続マネージャーが返すオブジェクトについて、適切な種類を決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0e53-127">You need to decide what type of object it is appropriate for the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> method to return from your custom connection manager.</span></span> <span data-ttu-id="f0e53-128">たとえば、ファイル接続マネージャーは、パスとファイル名が含まれた文字列のみを返し、ADO.NET 接続マネージャーは、既に開いているマネージド接続オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="f0e53-128">For example, a File connection manager returns only a string that contains a path and filename, whereas an ADO.NET connection manager returns a managed connection object that is already open.</span></span> <span data-ttu-id="f0e53-129">OLE DB 接続マネージャーは、マネージド コードから使用できないネイティブの OLE DB 接続オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="f0e53-129">An OLE DB connection manager returns a native OLE DB connection object that cannot be used from managed code.</span></span> <span data-ttu-id="f0e53-130">このトピック内のコード スニペットの基になっているカスタム SQL Server 接続マネージャーは、開いている `SqlConnection` オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="f0e53-130">The custom SQL Server connection manager, from which the code snippets in this topic are taken, returns an open `SqlConnection` object.</span></span>  
  
 <span data-ttu-id="f0e53-131">接続マネージャーのユーザーは、返されるオブジェクトを適切な種類にキャストし、そのメソッドとプロパティにアクセスできるよう、オブジェクトの種類をあらかじめ知っておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0e53-131">Users of your connection manager need to know in advance what type of object to expect, so that they can cast the returned object to the appropriate type and access its methods and properties.</span></span>  
  
```vb  
Public Overrides Function AcquireConnection(ByVal txn As Object) As Object  
  
  Dim sqlConnection As New SqlConnection  
  
  UpdateConnectionString()  
  
  With sqlConnection  
    .ConnectionString = _connectionString  
    .Open()  
  End With  
  
  Return sqlConnection  
  
End Function  
```  
  
```csharp  
public override object AcquireConnection(object txn)  
{  
  
  SqlConnection sqlConnection = new SqlConnection();  
  
  UpdateConnectionString();  
  
  {  
    sqlConnection.ConnectionString = _connectionString;  
    sqlConnection.Open();  
  }  
  
  return sqlConnection;  
  
}  
```  
  
### <a name="releasing-the-connection"></a><span data-ttu-id="f0e53-132">接続の解放</span><span class="sxs-lookup"><span data-stu-id="f0e53-132">Releasing the Connection</span></span>  
 <span data-ttu-id="f0e53-133"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> メソッドでのアクションは、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> メソッドから返されたオブジェクトの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="f0e53-133">The action that you take in the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> method depends on the type of object that you returned from the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> method.</span></span> <span data-ttu-id="f0e53-134">開いている接続オブジェクトがあれば、それを閉じて、使用中のリソースを解放してください。</span><span class="sxs-lookup"><span data-stu-id="f0e53-134">If there is an open connection object, you should close it and to release any resources that it is using.</span></span> <span data-ttu-id="f0e53-135"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> から文字列値のみが返された場合、必要なアクションはありません。</span><span class="sxs-lookup"><span data-stu-id="f0e53-135">If <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> returned only a string value, no action needs to be taken.</span></span>  
  
```vb  
Public Overrides Sub ReleaseConnection(ByVal connection As Object)  
  
  Dim sqlConnection As SqlConnection  
  
  sqlConnection = DirectCast(connection, SqlConnection)  
  
  If sqlConnection.State <> ConnectionState.Closed Then  
    sqlConnection.Close()  
  End If  
  
End Sub  
```  
  
```csharp  
public override void ReleaseConnection(object connection)  
{  
  SqlConnection sqlConnection;  
  sqlConnection = (SqlConnection)connection;  
  if (sqlConnection.State != ConnectionState.Closed)  
    sqlConnection.Close();  
}  
```  
  
<span data-ttu-id="f0e53-136">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="f0e53-136">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="f0e53-137">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0e53-137">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="f0e53-138">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="f0e53-138">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="f0e53-139">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="f0e53-139">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0e53-140">参照</span><span class="sxs-lookup"><span data-stu-id="f0e53-140">See Also</span></span>  
 <span data-ttu-id="f0e53-141">[カスタム接続マネージャーの作成](creating-a-custom-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="f0e53-141">[Creating a Custom Connection Manager](creating-a-custom-connection-manager.md) </span></span>  
 [<span data-ttu-id="f0e53-142">カスタム接続マネージャー用ユーザー インターフェイスの開発</span><span class="sxs-lookup"><span data-stu-id="f0e53-142">Developing a User Interface for a Custom Connection Manager</span></span>](developing-a-user-interface-for-a-custom-connection-manager.md)  
  
  
