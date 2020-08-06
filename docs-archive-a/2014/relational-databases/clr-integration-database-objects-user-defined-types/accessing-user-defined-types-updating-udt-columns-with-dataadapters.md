---
title: Dataadapter | を使用した UDT 列の更新Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- ADO.NET [CLR integration]
- updating data [CLR integration]
- populating DataSet
- datasets [CLR integration]
- UDTs [CLR integration], ADO.NET
- updating UDT columns
- user-defined types [CLR integration], ADO.NET
- data adapters [CLR integration]
ms.assetid: 4489c938-ba03-4fdb-b533-cc3f5975ae50
author: rothja
ms.author: jroth
ms.openlocfilehash: 8b908db850b1b77216824a5225d9bd8874387f78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642839"
---
# <a name="updating-udt-columns-with-dataadapters"></a><span data-ttu-id="00c1b-102">データ アダプターによる UDT 列の更新</span><span class="sxs-lookup"><span data-stu-id="00c1b-102">Updating UDT Columns with DataAdapters</span></span>
  <span data-ttu-id="00c1b-103">UDT (ユーザー定義型) は、データの取得や変更を行う `System.Data.DataSet` と `System.Data.SqlClient.SqlDataAdapter` を使用することでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="00c1b-103">User-defined types (UDTs) are supported by using a `System.Data.DataSet` and a `System.Data.SqlClient.SqlDataAdapter` to retrieve and modify data.</span></span>  
  
## <a name="populating-a-dataset"></a><span data-ttu-id="00c1b-104">データセットの設定</span><span class="sxs-lookup"><span data-stu-id="00c1b-104">Populating a Dataset</span></span>  
 <span data-ttu-id="00c1b-105">[!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT ステートメントを使用して UDT 列の値を選択すれば、データ アダプターを使用してデータセットにデータを設定できます。</span><span class="sxs-lookup"><span data-stu-id="00c1b-105">You can use a [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT statement to select UDT column values to populate a dataset using a data adapter.</span></span> <span data-ttu-id="00c1b-106">次の例では、次の構造といくつかのサンプルデータを使用して、 **Points**テーブルが定義されていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="00c1b-106">The following example assumes that you have a **Points** table defined with the following structure and some sample data.</span></span> <span data-ttu-id="00c1b-107">次のステートメントでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] **Points**テーブルを作成し、いくつかの行を挿入します。</span><span class="sxs-lookup"><span data-stu-id="00c1b-107">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements create the **Points** table and insert a few rows.</span></span>  
  
```  
CREATE TABLE dbo.Points (id int PRIMARY Key, p Point);  
  
INSERT INTO dbo.Points VALUES (1, CONVERT(Point, '1,3'));  
INSERT INTO dbo.Points VALUES (2, CONVERT(Point, '2,4'));  
INSERT INTO dbo.Points VALUES (3, CONVERT(Point, '3,5'));  
INSERT INTO dbo.Points VALUES (4, CONVERT(Point, '4,6'));  
GO  
```  
  
 <span data-ttu-id="00c1b-108">次の ADO.NET コード片では、有効な接続文字列を取得し、新しいを作成 `SqlDataAdapter` し、 `System.Data.DataTable` **Points**テーブルのデータ行をに設定します。</span><span class="sxs-lookup"><span data-stu-id="00c1b-108">The following ADO.NET code fragment retrieves a valid connection string, creates a new `SqlDataAdapter`, and populates a `System.Data.DataTable` with the rows of data from the **Points** table.</span></span>  
  
```vb  
Dim da As New SqlDataAdapter( _  
    "SELECT id, p FROM dbo.Points", connectionString)  
Dim datTable As New DataTable("Points")  
da.Fill(datTable)  
```  
  
```csharp  
SqlDataAdapter da = new SqlDataAdapter(  
   "SELECT id, p FROM dbo.Points", connectionString);  
DataTable datTable = new DataTable("Points");  
da.Fill(datTable);  
```  
  
## <a name="updating-udt-data-in-a-dataset"></a><span data-ttu-id="00c1b-109">データセットの UDT データの更新</span><span class="sxs-lookup"><span data-stu-id="00c1b-109">Updating UDT Data in a Dataset</span></span>  
 <span data-ttu-id="00c1b-110">`DataSet` の UDT 列を更新するには、次の 2 つの方法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="00c1b-110">You can use two methods to update a UDT column in a `DataSet`:</span></span>  
  
-   <span data-ttu-id="00c1b-111">`InsertCommand` オブジェクト用に独自の `UpdateCommand` オブジェクト、`DeleteCommand` オブジェクトおよび `SqlDataAdapter` オブジェクトを用意します。</span><span class="sxs-lookup"><span data-stu-id="00c1b-111">Provide custom `InsertCommand`, `UpdateCommand` and `DeleteCommand` objects for a `SqlDataAdapter` object.</span></span>  
  
-   <span data-ttu-id="00c1b-112">独自の INSERT コマンド、UPDATE コマンド、および DELETE コマンドを自動的に作成するために、コマンド ビルダー (`System.Data.SqlClient.SqlCommandBuilder`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="00c1b-112">Use the command builder (`System.Data.SqlClient.SqlCommandBuilder`) to create automatically the INSERT, UPDATE, and DELETE commands for you.</span></span> <span data-ttu-id="00c1b-113">競合を検出するために、UDT を含む [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに `timestamp` 列 (別名 `rowversion`) を追加します。</span><span class="sxs-lookup"><span data-stu-id="00c1b-113">In order to have conflict detection, add a `timestamp` column (alias `rowversion`) to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table that contains the UDT.</span></span> <span data-ttu-id="00c1b-114">`timestamp` データ型によりテーブル内の行にバージョン スタンプが設定され、その行がデータベース内で一意になることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="00c1b-114">The `timestamp` data type allows you to version-stamp the rows in a table, and is guaranteed to be unique within a database.</span></span> <span data-ttu-id="00c1b-115">テーブル内の値が変更されると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではその変更の影響を受ける行の 8 バイトのバイナリ番号が自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="00c1b-115">When a value in the table is changed, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] automatically updates the eight-byte binary number for the row affected by the change.</span></span>  
  
 <span data-ttu-id="00c1b-116">基になるテーブルに `SqlCommandBuilder` がなければ、`timestamp` では競合の検出時に UDT を考慮しないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="00c1b-116">Note that the `SqlCommandBuilder` does not consider the UDT for conflict detection unless there is a `timestamp` column in the underlying table.</span></span> <span data-ttu-id="00c1b-117">UDT は比較できる場合も比較できない場合もあるので、コマンドの生成に "元の値の比較" オプションを使用しているときは、UDT が WHERE 句に含められません。</span><span class="sxs-lookup"><span data-stu-id="00c1b-117">UDTs may or may not be comparable, so they are not included in the WHERE clause when the "compare original values" option is used to generate a command.</span></span>  
  
### <a name="example"></a><span data-ttu-id="00c1b-118">例</span><span class="sxs-lookup"><span data-stu-id="00c1b-118">Example</span></span>  
 <span data-ttu-id="00c1b-119">次の例では、`Point` UDT 列と `timestamp` 列を含む 2 つ目のテーブルを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00c1b-119">The following example requires the creation of a second table containing the `Point` UDT column as well as a `timestamp` column.</span></span> <span data-ttu-id="00c1b-120">この両方のテーブルを使用して、データを更新するカスタム コマンド オブジェクトを作成する方法と、`timestamp` 列を使用して更新する方法を例示します。</span><span class="sxs-lookup"><span data-stu-id="00c1b-120">Both tables are used to illustrate how to create custom command objects to update data, and how to update using a `timestamp` column.</span></span> <span data-ttu-id="00c1b-121">2 つ目のテーブルを作成し、そのテーブルにサンプル データを設定するには、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="00c1b-121">Run the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements to create the second table and populate it with sample data.</span></span>  
  
```  
CREATE TABLE dbo.Points_ts (id int PRIMARY KEY, p Point, ts timestamp);  
  
INSERT INTO dbo.Points_ts (id, p) VALUES (1, CONVERT(Point, '1,3'));  
INSERT INTO dbo.Points_ts (id, p) VALUES (2, CONVERT(Point, '2,4'));  
INSERT INTO dbo.Points_ts (id, p) VALUES (3, CONVERT(Point, '3,5'));  
INSERT INTO dbo.Points_ts (id, p) VALUES (4, CONVERT(Point, '4,6'));  
```  
  
 <span data-ttu-id="00c1b-122">次の ADO.NET の例には 2 つのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="00c1b-122">The following ADO.NET example has two methods:</span></span>  
  
-   <span data-ttu-id="00c1b-123">`UserProvidedCommands`、、、およびの各オブジェクトを指定し `InsertCommand` `UpdateCommand` て、 `DeleteCommand` `Point` **Points**テーブル (列を含まない) の UDT を更新する方法を示し `timestamp` ます。</span><span class="sxs-lookup"><span data-stu-id="00c1b-123">`UserProvidedCommands`, which demonstrates how to supply `InsertCommand`, `UpdateCommand`, and `DeleteCommand` objects for updating the `Point` UDT in the **Points** table (which does not contain a `timestamp` column).</span></span>  
  
-   <span data-ttu-id="00c1b-124">`CommandBuilder``SqlCommandBuilder`。この列を含む**Points_ts**テーブルでを使用する方法を示し `timestamp` ます。</span><span class="sxs-lookup"><span data-stu-id="00c1b-124">`CommandBuilder`, which demonstrates how to use a `SqlCommandBuilder` in the **Points_ts** table that contains the `timestamp` column.</span></span>  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
    ' Retrieves the connection string  
    Private connString As String = GetConnectionString()  
  
    Sub Main()  
        UserProvidedCommands()  
        CommandBuilder()  
    End Sub  
  
    Private Sub UserProvidedCommands()  
        ' Create a new SqlDataAdapter  
        Dim da As New SqlDataAdapter( _  
          "SELECT id, p FROM dbo.Points", connString)  
  
        ' Setup the INSERT/UPDATE/DELETE commands  
        Dim idParam As SqlParameter  
        Dim pointParam As SqlParameter  
  
        da.InsertCommand = New SqlCommand( _  
          "INSERT INTO dbo.Points (id, p) VALUES (@id, @p)", _  
          da.SelectCommand.Connection)  
        idParam = da.InsertCommand.Parameters.Add( _  
          "@id", SqlDbType.Int)  
        idParam.SourceColumn = "id"  
        pointParam = da.InsertCommand.Parameters.Add( _  
          "@p", SqlDbType.Udt)  
        pointParam.SourceColumn = "p"  
        pointParam.UdtTypeName = "dbo.Point"  
  
        da.UpdateCommand = New SqlCommand( _  
          "UPDATE dbo.Points SET p = @p WHERE id = @id", _  
          da.SelectCommand.Connection)  
        idParam = _  
           da.UpdateCommand.Parameters.Add("@id", SqlDbType.Int)  
        idParam.SourceColumn = "id"  
        pointParam = da.UpdateCommand.Parameters.Add( _  
          "@p", SqlDbType.Udt)  
        pointParam.SourceColumn = "p"  
        pointParam.UdtTypeName = "dbo.Point"  
  
        da.DeleteCommand = New SqlCommand( _  
          "DELETE dbo.Points WHERE id = @id", _  
          da.SelectCommand.Connection)  
        idParam = da.DeleteCommand.Parameters.Add( _  
          "@id", SqlDbType.Int)  
        idParam.SourceColumn = "id"  
  
        ' Fill the DataTable with UDT rows  
        Dim datTable As New DataTable("Points")  
        da.Fill(datTable)  
  
        ' Display the contents of the p (Point) column  
        Dim r As DataRow  
        For Each r In datTable.Rows  
            Dim p As Point = CType(r(1), Point)  
            Console.WriteLine( _  
              "ID: {0}, x={1}, y={1}", r(0), p.X, p.Y)  
        Next r  
  
        ' Update a row if the DataTable has at least 1 row  
        If datTable.Rows.Count > 0 Then  
            Dim oldPoint As Point = _  
              CType(datTable.Rows(0)(1), Point)  
            datTable.Rows(0)(1) = _  
              New Point(oldPoint.X + 1, oldPoint.Y + 1)  
        End If  
  
        ' Delete the last row  
        If datTable.Rows.Count > 0 Then  
            ' If we have at least 1 row  
            datTable.Rows(1).Delete()  
        End If  
  
        ' Insert a row. This will fail if run twice  
        ' because 100 is a primary key value.  
        datTable.Rows.Add(100, New Point(100, 200))  
  
        ' Send the changes back to the database  
        da.Update(datTable)  
    End Sub  
  
    Private Sub CommandBuilder()  
        ' Create a new SqlDataAdapter  
        Dim da As New SqlDataAdapter( _  
          "SELECT id, ts, p FROM dbo.Points_ts", connString)  
  
        ' Select a few rows with UDTs from the database  
        Dim datTable As New DataTable("Points")  
        da.Fill(datTable)  
  
        ' Display the contents of the p (Point) column  
        Dim r As DataRow  
        For Each r In datTable.Rows  
            Dim p As Point = CType(r(2), Point)  
            Console.WriteLine( _  
              "ID: {0}, x={1}, y={1}", r(0), p.X, p.Y)  
        Next r  
  
        ' Update a row if DataTable has at least 1 row  
        If datTable.Rows.Count > 0 Then  
            Dim oldPoint As Point = _  
              CType(datTable.Rows(0)(2), Point)  
            datTable.Rows(0)(2) = _  
              New Point(oldPoint.X + 1, oldPoint.Y + 1)  
        End If  
  
        ' Delete the last row  
        If datTable.Rows.Count > 0 Then  
            ' if we have at least 1 row  
            datTable.Rows(1).Delete()  
        End If  
  
        ' Insert a row. This will fail if run twice  
        ' because 100 is a primary key value  
        datTable.Rows.Add(100, Nothing, New Point(100, 200))  
  
        ' Use the CommandBuilder to generate DML statements  
        Dim bld As New SqlCommandBuilder(da)  
        bld.ConflictDetection = ConflictOptions.CompareRowVersion  
  
        ' Send the changes back to the database  
        da.Update(datTable)  
    End Sub  
  
  Private Function GetConnectionString() As String  
      ' To avoid storing the connection string in your code,   
      ' you can retrieve it from a configuration file.  
     Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
       & "Integrated Security=SSPI"  
   End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Class1  
  {  
// Retrieves the connection string  
private string connString = GetConnectionString();  
  
static void Main()  
{  
        UserProvidedCommands();  
        CommandBuilder();  
 }  
    static void UserProvidedCommands()  
    {  
        // Create a new SqlDataAdapter  
        SqlDataAdapter da = new SqlDataAdapter(  
          "SELECT id, p FROM dbo.Points", connString);  
  
        // Setup the INSERT/UPDATE/DELETE commands  
        SqlParameter idParam;  
        SqlParameter pointParam;  
  
        da.InsertCommand = new SqlCommand(  
            "INSERT INTO dbo.Points (id, p) VALUES (@id, @p)",   
             da.SelectCommand.Connection);  
        idParam =   
            da.InsertCommand.Parameters.Add("@id", SqlDbType.Int);  
        idParam.SourceColumn = "id";  
        pointParam =   
            da.InsertCommand.Parameters.Add("@p", SqlDbType.Udt);  
        pointParam.SourceColumn = "p";  
        pointParam.UdtTypeName = "dbo.Point";  
  
        da.UpdateCommand = new SqlCommand(  
            "UPDATE dbo.Points SET p = @p WHERE id = @id",   
            da.SelectCommand.Connection);  
        idParam =   
            da.UpdateCommand.Parameters.Add("@id", SqlDbType.Int);  
        idParam.SourceColumn = "id";  
        pointParam =   
            da.UpdateCommand.Parameters.Add("@p", SqlDbType.Udt);  
        pointParam.SourceColumn = "p";  
        pointParam.UdtTypeName = "dbo.Point";   
  
        da.DeleteCommand = new SqlCommand(  
            "DELETE dbo.Points WHERE id = @id",   
            da.SelectCommand.Connection);  
        idParam =   
            da.DeleteCommand.Parameters.Add("@id", SqlDbType.Int);  
        idParam.SourceColumn = "id";  
  
        // Fill the DataTable with UDT rows  
        DataTable datTable = new DataTable("Points");  
        da.Fill(datTable);  
  
        // Display the contents of the p (Point) column  
        foreach(DataRow r in datTable.Rows)   
        {  
            Point p = (Point)r[1];  
            Console.WriteLine(  
                "ID: {0}, x={1}, y={1}", r[0], p.X, p.Y);  
        }  
  
        // Update a row if the DataTable has at least 1 row  
        if(datTable.Rows.Count > 0 )   
        {   
            Point oldPoint = (Point)datTable.Rows[0][1];  
            datTable.Rows[0][1] =   
                new Point(oldPoint.X+1, oldPoint.Y+1);  
        }  
  
        // Delete the last row  
        if(datTable.Rows.Count > 0 )   
        { // If we have at least 1 row  
            datTable.Rows[1].Delete();  
        }  
  
        // Insert a row. This will fail if run twice  
        // because 100 is a primary key value.  
        datTable.Rows.Add(100, new Point(100, 200));   
  
        // Send the changes back to the database  
        da.Update(datTable);  
    }  
  
    static void CommandBuilder()  
    {  
        // Create a new SqlDataAdapter  
        SqlDataAdapter da = new SqlDataAdapter(  
            "SELECT id, ts, p FROM dbo.Points_ts", connString);  
  
        // Select a few rows with UDTs from the database  
        DataTable datTable = new DataTable("Points");  
        da.Fill(datTable);  
  
        // Display the contents of the p (Point) column  
        foreach (DataRow r in datTable.Rows)  
        {  
            Point p = (Point)r[2];  
            Console.WriteLine(  
                "ID: {0}, x={1}, y={1}", r[0], p.X, p.Y);  
        }  
  
        // Update a row if DataTable has at least 1 row  
        if (datTable.Rows.Count > 0)  
        {   
            Point oldPoint = (Point)datTable.Rows[0][2];  
            datTable.Rows[0][2] =   
                new Point(oldPoint.X + 1, oldPoint.Y + 1);  
        }  
  
        // Delete the last row  
        if (datTable.Rows.Count > 0)  
        { // if we have at least 1 row  
            datTable.Rows[1].Delete();  
        }  
  
        // Insert a row. This will fail if run twice  
        // because 100 is a primary key value  
        datTable.Rows.Add(100, null, new Point(100, 200));   
  
        // Use the CommandBuilder to generate DML statements  
        SqlCommandBuilder bld = new SqlCommandBuilder(da);  
        bld.ConflictDetection = ConflictOptions.CompareRowVersion;  
  
        // Send the changes back to the database  
        da.Update(datTable);  
    }  
  
 static private string GetConnectionString()  
 {  
 // To avoid storing the connection string in your code,   
 // you can retrieve it from a configuration file.  
    return "Data Source=localhost;Initial Catalog=AdventureWorks;"  
        + "Integrated Security=SSPI";  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="00c1b-125">参照</span><span class="sxs-lookup"><span data-stu-id="00c1b-125">See Also</span></span>  
 [<span data-ttu-id="00c1b-126">ADO.NET でのユーザー定義型へのアクセス</span><span class="sxs-lookup"><span data-stu-id="00c1b-126">Accessing User-Defined Types in ADO.NET</span></span>](accessing-user-defined-types-in-ado-net.md)  
  
  
