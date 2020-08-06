---
title: メソッドの呼び出し |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- methods [SMO]
- calling methods
- SQL Server Management Objects, method calling
- SMO [SQL Server], method calling
ms.assetid: c88d5c5f-9ff0-4f84-b2b6-24c6b90fa15e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 13216b4c533527d4249471073580d7c86f6b07e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719803"
---
# <a name="calling-methods"></a><span data-ttu-id="7ee9f-102">メソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="7ee9f-102">Calling Methods</span></span>
  <span data-ttu-id="7ee9f-103">メソッドは、オブジェクトに関連する特定のタスクを実行し `Checkpoint` ます。たとえば、データベースでのの発行や、のインスタンスに対するログオンの列挙リストの要求など [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] です。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-103">Methods perform specific tasks related to the object, such as issuing a `Checkpoint` on a database or requesting an enumerated list of logons for the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="7ee9f-104">メソッドはオブジェクトに対する操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-104">Methods perform an operation on an object.</span></span> <span data-ttu-id="7ee9f-105">メソッドはパラメーターを受け取ることができ、多くの場合は戻り値があります。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-105">Methods can take parameters and often have a return value.</span></span> <span data-ttu-id="7ee9f-106">戻り値には、単純なデータ型、複雑なオブジェクト、複数のメンバーを含んでいる構造のいずれを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-106">The return value can be a simple data type, a complex object, or a structure that contains many members.</span></span>  
  
 <span data-ttu-id="7ee9f-107">メソッドが正常に実行されたかどうかを検出するには、例外処理を使用します。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-107">Use exception handling to detect whether the method has been successful.</span></span> <span data-ttu-id="7ee9f-108">詳しくは、「 [Handling SMO Exceptions](handling-smo-exceptions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-108">For more information, see [Handling SMO Exceptions](handling-smo-exceptions.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7ee9f-109">例</span><span class="sxs-lookup"><span data-stu-id="7ee9f-109">Examples</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="using-a-simple-smo-method-in-visual-basic"></a><span data-ttu-id="7ee9f-110">Visual Basic での簡単な SMO メソッドの使用</span><span class="sxs-lookup"><span data-stu-id="7ee9f-110">Using a Simple SMO Method in Visual Basic</span></span>  
 <span data-ttu-id="7ee9f-111">この例で、<xref:Microsoft.SqlServer.Management.Smo.Database.Create%2A> メソッドにはパラメーターがなく、戻り値もありません。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-111">In this example, the <xref:Microsoft.SqlServer.Management.Smo.Database.Create%2A> method takes no parameters and has no return value.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMethods1](SMO How to#SMO_VBMethods1)]  -->  
  
## <a name="using-a-simple-smo-method-in-visual-c"></a><span data-ttu-id="7ee9f-112">Visual C# での簡単な SMO メソッドの使用</span><span class="sxs-lookup"><span data-stu-id="7ee9f-112">Using a Simple SMO Method in Visual C#</span></span>  
 <span data-ttu-id="7ee9f-113">この例で、<xref:Microsoft.SqlServer.Management.Smo.Database.Create%2A> メソッドにはパラメーターがなく、戻り値もありません。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-113">In this example, the <xref:Microsoft.SqlServer.Management.Smo.Database.Create%2A> method takes no parameters and has no return value.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Define a Database object variable by supplying the parent server and the database name arguments in the constructor.   
Database db;   
db = new Database(srv, "Test_SMO_Database");   
//Call the Create method to create the database on the instance of SQL Server.   
db.Create();   
```  
  
 <span data-ttu-id="7ee9f-114">}</span><span class="sxs-lookup"><span data-stu-id="7ee9f-114">}</span></span>  
  
## <a name="using-an-smo-method-with-a-parameter-in-visual-basic"></a><span data-ttu-id="7ee9f-115">Visual Basic でのパラメーターを指定した SMO メソッドの使用</span><span class="sxs-lookup"><span data-stu-id="7ee9f-115">Using an SMO Method with a Parameter in Visual Basic</span></span>  
 <span data-ttu-id="7ee9f-116"><xref:Microsoft.SqlServer.Management.Smo.Table> オブジェクトには、<xref:Microsoft.SqlServer.Management.Smo.Table.RebuildIndexes%2A> と呼ばれるメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-116">The <xref:Microsoft.SqlServer.Management.Smo.Table> object has a method called <xref:Microsoft.SqlServer.Management.Smo.Table.RebuildIndexes%2A>.</span></span> <span data-ttu-id="7ee9f-117">このメソッドには、 `FillFactor`を指定する数値パラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-117">This method requires a numeric parameter that specifies the `FillFactor`.</span></span>  
  
```  
Dim srv As Server  
srv = New Server  
Dim tb As Table  
tb = srv.Databases("AdventureWorks2012").Tables("Employee", "HumanResources")  
tb.RebuildIndexes(70)  
```  
  
## <a name="using-an-smo-method-with-a-parameter-in-visual-c"></a><span data-ttu-id="7ee9f-118">Visual C# でのパラメーターを指定した SMO メソッドの使用</span><span class="sxs-lookup"><span data-stu-id="7ee9f-118">Using an SMO Method with a Parameter in Visual C#</span></span>  
 <span data-ttu-id="7ee9f-119"><xref:Microsoft.SqlServer.Management.Smo.Table> オブジェクトには、<xref:Microsoft.SqlServer.Management.Smo.Table.RebuildIndexes%2A> と呼ばれるメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-119">The <xref:Microsoft.SqlServer.Management.Smo.Table> object has a method called <xref:Microsoft.SqlServer.Management.Smo.Table.RebuildIndexes%2A>.</span></span> <span data-ttu-id="7ee9f-120">このメソッドには、 `FillFactor`を指定する数値パラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-120">This method requires a numeric parameter that specifies the `FillFactor`.</span></span>  
  
```  
{   
Server srv = default(Server);   
srv = new Server();   
Table tb = default(Table);   
tb = srv.Databases("AdventureWorks2012").Tables("Employee", "HumanResources");   
tb.RebuildIndexes(70);   
}   
```  
  
## <a name="using-an-enumeration-method-that-returns-a-datatable-object-in-visual-basic"></a><span data-ttu-id="7ee9f-121">Visual Basic での DataTable オブジェクトを返す列挙メソッドの使用</span><span class="sxs-lookup"><span data-stu-id="7ee9f-121">Using an Enumeration Method that Returns a DataTable Object in Visual Basic</span></span>  
 <span data-ttu-id="7ee9f-122">このセクションでは、列挙メソッドを呼び出す方法、および返された <xref:System.Data.DataTable> オブジェクト内のデータを処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-122">This section describes how to call an enumeration method and how to handle the data in the returned <xref:System.Data.DataTable> object.</span></span>  
  
 <span data-ttu-id="7ee9f-123"><xref:Microsoft.SqlServer.Management.Smo.Server.EnumCollations%2A> メソッドは <xref:System.Data.DataTable> オブジェクトを返します。このオブジェクトでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに関する利用可能な照合順序情報のすべてにアクセスするには、追加の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-123">The <xref:Microsoft.SqlServer.Management.Smo.Server.EnumCollations%2A> method returns a <xref:System.Data.DataTable> object, which requires further navigation to access all available collation information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
```  
'Connect to the local, default instance of SQL Server.  
Dim srv As Server  
srv = New Server  
'Call the EnumCollations method and return collation information to DataTable variable.  
Dim d As DataTable  
'Select the returned data into an array of DataRow.  
d = srv.EnumCollations  
'Iterate through the rows and display collation details for the instance of SQL Server.  
Dim r As DataRow  
Dim c As DataColumn  
For Each r In d.Rows  
    Console.WriteLine("==")  
    For Each c In r.Table.Columns  
        Console.WriteLine(c.ColumnName + " = " + r(c).ToString)  
    Next  
Next  
```  
  
## <a name="using-an-enumeration-method-that-returns-a-datatable-object-in-visual-c"></a><span data-ttu-id="7ee9f-124">Visual C# での DataTable オブジェクトを返す列挙メソッドの使用</span><span class="sxs-lookup"><span data-stu-id="7ee9f-124">Using an Enumeration Method that Returns a DataTable Object in Visual C#</span></span>  
 <span data-ttu-id="7ee9f-125">このセクションでは、列挙メソッドを呼び出す方法、および返された <xref:System.Data.DataTable> オブジェクト内のデータを処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-125">This section describes how to call an enumeration method and how to handle the data in the returned <xref:System.Data.DataTable> object.</span></span>  
  
 <span data-ttu-id="7ee9f-126"><xref:Microsoft.SqlServer.Management.Smo.Server.EnumCollations%2A> メソッドは、システム <xref:System.Data.DataTable> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-126">The <xref:Microsoft.SqlServer.Management.Smo.Server.EnumCollations%2A> method returns a system <xref:System.Data.DataTable> object.</span></span> <span data-ttu-id="7ee9f-127"><xref:System.Data.DataTable> オブジェクトでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに関する利用可能な照合順序情報のすべてにアクセスするには、追加の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-127">The <xref:System.Data.DataTable> object requires further navigation to access all available collation information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
```  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
//Call the EnumCollations method and return collation information to DataTable variable.   
DataTable d = default(DataTable);   
//Select the returned data into an array of DataRow.   
d = srv.EnumCollations;   
//Iterate through the rows and display collation details for the instance of SQL Server.   
DataRow r = default(DataRow);   
DataColumn c = default(DataColumn);   
foreach ( r in d.Rows) {   
  Console.WriteLine("=========");   
  foreach ( c in r.Table.Columns) {   
    Console.WriteLine(c.ColumnName + " = " + r(c).ToString);   
  }   
}   
}   
```  
  
## <a name="constructing-an-object-in-visual-basic"></a><span data-ttu-id="7ee9f-128">Visual Basic でのオブジェクトの構築</span><span class="sxs-lookup"><span data-stu-id="7ee9f-128">Constructing an Object in Visual Basic</span></span>  
 <span data-ttu-id="7ee9f-129">オブジェクトのコンストラクターは、`New` 演算子を使用して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-129">The constructor of any object can be called by using the `New` operator.</span></span> <span data-ttu-id="7ee9f-130"><xref:Microsoft.SqlServer.Management.Smo.Database> オブジェクト コンストラクターはオーバーロードされます。コード例で使用するバージョンの <xref:Microsoft.SqlServer.Management.Smo.Database> オブジェクト コンストラクターでは、パラメーターとして、データベースの親である <xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクトおよび新しいデータベースの名前を表す文字列を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-130">The <xref:Microsoft.SqlServer.Management.Smo.Database> object constructor is overloaded and the version of the <xref:Microsoft.SqlServer.Management.Smo.Database> object constructor that is used in the sample takes two parameters: the parent <xref:Microsoft.SqlServer.Management.Smo.Server> object to which the database belongs, and a string that represents the name of the new database.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMethods4](SMO How to#SMO_VBMethods4)]  -->  
  
## <a name="constructing-an-object-in-visual-c"></a><span data-ttu-id="7ee9f-131">Visual C# でのオブジェクトの構築</span><span class="sxs-lookup"><span data-stu-id="7ee9f-131">Constructing an Object in Visual C#</span></span>  
 <span data-ttu-id="7ee9f-132">オブジェクトのコンストラクターは、`New` 演算子を使用して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-132">The constructor of any object can be called by using the `New` operator.</span></span> <span data-ttu-id="7ee9f-133"><xref:Microsoft.SqlServer.Management.Smo.Database> オブジェクト コンストラクターはオーバーロードされます。コード例で使用するバージョンの <xref:Microsoft.SqlServer.Management.Smo.Database> オブジェクト コンストラクターでは、パラメーターとして、データベースの親である <xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクトおよび新しいデータベースの名前を表す文字列を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-133">The <xref:Microsoft.SqlServer.Management.Smo.Database> object constructor is overloaded and the version of the <xref:Microsoft.SqlServer.Management.Smo.Database> object constructor that is used in the sample takes two parameters: the parent <xref:Microsoft.SqlServer.Management.Smo.Server> object to which the database belongs, and a string that represents the name of the new database.</span></span>  
  
```  
{   
Server srv;   
srv = new Server();   
Table tb;   
tb = srv.Databases("AdventureWorks2012").Tables("Employee", "HumanResources");   
tb.RebuildIndexes(70);   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Declare and define a Database object by supplying the parent server and the database name arguments in the constructor.   
Database d;   
d = new Database(srv, "Test_SMO_Database");   
//Create the database on the instance of SQL Server.   
d.Create();   
Console.WriteLine(d.Name);   
}  
```  
  
## <a name="copying-an-smo-object-in-visual-basic"></a><span data-ttu-id="7ee9f-134">Visual Basic での SMO オブジェクトのコピー</span><span class="sxs-lookup"><span data-stu-id="7ee9f-134">Copying an SMO Object in Visual Basic</span></span>  
 <span data-ttu-id="7ee9f-135">このコード例では、<xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> メソッドを使用して <xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクトのコピーを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-135">This code example uses the <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> method to create a copy of the <xref:Microsoft.SqlServer.Management.Smo.Server> object.</span></span> <span data-ttu-id="7ee9f-136"><xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクトは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスへの接続を表します。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-136">The <xref:Microsoft.SqlServer.Management.Smo.Server> object represents a connection to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VCMethods6](SMO How to#SMO_VCMethods6)]  -->  
  
## <a name="copying-an-smo-object-in-visual-c"></a><span data-ttu-id="7ee9f-137">Visual C# での SMO オブジェクトのコピー</span><span class="sxs-lookup"><span data-stu-id="7ee9f-137">Copying an SMO Object in Visual C#</span></span>  
 <span data-ttu-id="7ee9f-138">このコード例では、<xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> メソッドを使用して <xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクトのコピーを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-138">This code example uses the <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> method to create a copy of the <xref:Microsoft.SqlServer.Management.Smo.Server> object.</span></span> <span data-ttu-id="7ee9f-139"><xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクトは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスへの接続を表します。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-139">The <xref:Microsoft.SqlServer.Management.Smo.Server> object represents a connection to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv1;   
srv1 = new Server();   
//Modify the default database and the timeout period for the connection.   
srv1.ConnectionContext.DatabaseName = "AdventureWorks2012";   
srv1.ConnectionContext.ConnectTimeout = 30;   
//Make a second connection using a copy of the ConnectionContext property and verify settings.   
Server srv2;   
srv2 = new Server(srv1.ConnectionContext.Copy);   
Console.WriteLine(srv2.ConnectionContext.ConnectTimeout.ToString);   
}  
```  
  
## <a name="monitoring-server-processes-in-visual-basic"></a><span data-ttu-id="7ee9f-140">Visual Basic でのサーバー プロセスの監視</span><span class="sxs-lookup"><span data-stu-id="7ee9f-140">Monitoring Server Processes in Visual Basic</span></span>  
 <span data-ttu-id="7ee9f-141">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに関する現在の状態の型情報は、列挙メソッドを使用して取得することができます。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-141">You can obtain the current status type information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] through enumeration methods.</span></span> <span data-ttu-id="7ee9f-142">コード例では、<xref:Microsoft.SqlServer.Management.Smo.Server.EnumProcesses%2A> メソッドを使用して、現在のプロセスに関する情報を検出します。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-142">The code example uses the <xref:Microsoft.SqlServer.Management.Smo.Server.EnumProcesses%2A> method to discover information about the current processes.</span></span> <span data-ttu-id="7ee9f-143">また、返された <xref:System.Data.DataTable> オブジェクトの列および行を操作する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-143">It also demonstrates how to work with the columns and rows in the returned <xref:System.Data.DataTable> object.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMethods5](SMO How to#SMO_VBMethods5)]  -->  
  
## <a name="monitoring-server-processes-in-visual-c"></a><span data-ttu-id="7ee9f-144">Visual C# でのサーバー プロセスの監視</span><span class="sxs-lookup"><span data-stu-id="7ee9f-144">Monitoring Server Processes in Visual C#</span></span>  
 <span data-ttu-id="7ee9f-145">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに関する現在の状態の型情報は、列挙メソッドを使用して取得することができます。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-145">You can obtain the current status type information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] through enumeration methods.</span></span> <span data-ttu-id="7ee9f-146">コード例では、<xref:Microsoft.SqlServer.Management.Smo.Server.EnumProcesses%2A> メソッドを使用して、現在のプロセスに関する情報を検出します。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-146">The code example uses the <xref:Microsoft.SqlServer.Management.Smo.Server.EnumProcesses%2A> method to discover information about the current processes.</span></span> <span data-ttu-id="7ee9f-147">また、返された <xref:System.Data.DataTable> オブジェクトの列および行を操作する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="7ee9f-147">It also demonstrates how to work with the columns and rows in the returned <xref:System.Data.DataTable> object.</span></span>  
  
```  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
//Call the EnumCollations method and return collation information to DataTable variable.   
DataTable d = default(DataTable);   
//Select the returned data into an array of DataRow.   
d = srv.EnumProcesses;   
//Iterate through the rows and display collation details for the instance of SQL Server.   
DataRow r = default(DataRow);   
DataColumn c = default(DataColumn);   
foreach ( r in d.Rows) {   
  Console.WriteLine("=====");   
  foreach ( c in r.Table.Columns) {   
    Console.WriteLine(c.ColumnName + " = " + r(c).ToString);   
  }   
}   
}   
```  
  
## <a name="see-also"></a><span data-ttu-id="7ee9f-148">参照</span><span class="sxs-lookup"><span data-stu-id="7ee9f-148">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  
