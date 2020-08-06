---
title: UDT データの取得 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SqlDataReader object
- ADO.NET [CLR integration]
- binding UDTs [CLR integration]
- UDTs [CLR integration], ADO.NET
- assemblies [CLR integration], user-defined types
- query parameters [CLR integration]
- user-defined types [CLR integration], ADO.NET
- bytes [CLR integration]
ms.assetid: 6a98ac8c-0e69-4c03-83a4-2062cb782049
author: rothja
ms.author: jroth
ms.openlocfilehash: cb9133ea45069f76e7590f6b74d3c1e1cb98c7bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642842"
---
# <a name="retrieving-udt-data"></a><span data-ttu-id="b222c-102">UDT データの取得</span><span class="sxs-lookup"><span data-stu-id="b222c-102">Retrieving UDT Data</span></span>
  <span data-ttu-id="b222c-103">クライアント側で UDT (ユーザー定義型) を作成するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに UDT として登録されたアセンブリをクライアント アプリケーションで使用できるようにしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="b222c-103">In order to create a user-defined type (UDT) on the client, the assembly that was registered as a UDT in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database must be available to the client application.</span></span> <span data-ttu-id="b222c-104">この UDT アセンブリは、アプリケーションと同じディレクトリまたは GAC (グローバル アセンブリ キャッシュ) に配置できます。</span><span class="sxs-lookup"><span data-stu-id="b222c-104">The UDT assembly can be placed in the same directory with the application, or in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="b222c-105">また、プロジェクト内で、このアセンブリへの参照を設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="b222c-105">You can also set a reference to the assembly in your project.</span></span>  
  
## <a name="requirements-for-using-udts-in-adonet"></a><span data-ttu-id="b222c-106">ADO.NET で UDT を使用するための要件</span><span class="sxs-lookup"><span data-stu-id="b222c-106">Requirements for Using UDTs in ADO.NET</span></span>  
 <span data-ttu-id="b222c-107">クライアント側で UDT を作成するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に読み込まれたアセンブリとクライアント側に存在するアセンブリとの間に互換性がなくてはなりません。</span><span class="sxs-lookup"><span data-stu-id="b222c-107">The assembly loaded in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the assembly on the client must be compatible in order for the UDT to be created on the client.</span></span> <span data-ttu-id="b222c-108">`Native` シリアル化形式で定義した UDT の場合は、アセンブリの構造に互換性が必要です。</span><span class="sxs-lookup"><span data-stu-id="b222c-108">For UDTs defined with the `Native` serialization format, the assemblies must be structurally compatible.</span></span> <span data-ttu-id="b222c-109">`UserDefined` 形式で定義したアセンブリの場合は、そのアセンブリをクライアント側で使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="b222c-109">For assemblies defined with the `UserDefined` format, the assembly must be available on the client.</span></span>  
  
 <span data-ttu-id="b222c-110">テーブルの UDT 列からデータをそのまま取得するために、クライアントに UDT アセンブリをコピーする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b222c-110">You do not need a copy of the UDT assembly on the client in order to retrieve the raw data from a UDT column in a table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b222c-111">UDT のバージョンが一致しない場合や他の問題が発生した場合に、 **SqlClient**が udt の読み込みに失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="b222c-111">**SqlClient** may fail to load a UDT in the event of mismatched UDT versions or other problems.</span></span> <span data-ttu-id="b222c-112">この場合、通常のトラブルシューティング メカニズムを使用して、呼び出し元のアプリケーションで UDT を含むアセンブリが検出されない原因を特定します。</span><span class="sxs-lookup"><span data-stu-id="b222c-112">In this case, use regular troubleshooting mechanisms to determine why the assembly containing the UDT cannot be found by the calling application.</span></span> <span data-ttu-id="b222c-113">詳細については、.NET Framework のドキュメントのトピック「マネージド デバッグ アシスタントによるエラーの診断」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b222c-113">For more information, read the topic titled "Diagnosing Errors with Managed Debugging Assistants" in the .NET Framework documentation.</span></span>  
  
## <a name="accessing-udts-with-a-sqldatareader"></a><span data-ttu-id="b222c-114">SqlDataReader による UDT へのアクセス</span><span class="sxs-lookup"><span data-stu-id="b222c-114">Accessing UDTs with a SqlDataReader</span></span>  
 <span data-ttu-id="b222c-115">クライアント コードから `System.Data.SqlClient.SqlDataReader` を使用して、UDT 列を含む結果セットを取得することができます。この結果セットは、オブジェクトのインスタンスとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="b222c-115">A `System.Data.SqlClient.SqlDataReader` can be used from client code to retrieve a result set that contains a UDT column, which is exposed as an instance of the object.</span></span>  
  
### <a name="example"></a><span data-ttu-id="b222c-116">例</span><span class="sxs-lookup"><span data-stu-id="b222c-116">Example</span></span>  
 <span data-ttu-id="b222c-117">この例では、`Main` メソッドを使用して、新しい `SqlDataReader` オブジェクトを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b222c-117">This example shows how to use the `Main` method to create a new `SqlDataReader` object.</span></span> <span data-ttu-id="b222c-118">このコード例では、次の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="b222c-118">The following actions occur within the code example:</span></span>  
  
1.  <span data-ttu-id="b222c-119">Main メソッドでは、新しい `SqlDataReader` オブジェクトが作成され、Points テーブルから値が取得されます。このテーブルには、Point という名前の UDT 列があります。</span><span class="sxs-lookup"><span data-stu-id="b222c-119">The Main method creates a new `SqlDataReader` object and retrieves the values from the Points table, which has a UDT column named Point.</span></span>  
  
2.  <span data-ttu-id="b222c-120">Point UDT では、整数型として定義されている X 座標と Y 座標が公開されます。</span><span class="sxs-lookup"><span data-stu-id="b222c-120">The Point UDT exposes X and Y coordinates defined as integers.</span></span>  
  
3.  <span data-ttu-id="b222c-121">UDT では、`Distance` メソッドと `GetDistanceFromXY` メソッドが定義されています。</span><span class="sxs-lookup"><span data-stu-id="b222c-121">The UDT defines a `Distance` method and a `GetDistanceFromXY` method.</span></span>  
  
4.  <span data-ttu-id="b222c-122">このサンプル コードでは、UDT の機能を例示するために主キーと UDT 列の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="b222c-122">The sample code retrieves the values of the primary key and UDT columns in order to demonstrate the capabilities of the UDT.</span></span>  
  
5.  <span data-ttu-id="b222c-123">サンプル コードでは、`Point.Distance` メソッドと `Point.GetDistanceFromXY` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b222c-123">The sample code calls the `Point.Distance` and `Point.GetDistanceFromXY` methods.</span></span>  
  
6.  <span data-ttu-id="b222c-124">結果はコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b222c-124">The results are displayed in the console window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b222c-125">アプリケーションでは、事前に UDT アセンブリへの参照が設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b222c-125">The application must already have a reference to the UDT assembly.</span></span>  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
  
Module ReadPoints  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Retrieve the value of the UDT  
                Dim pnt As Point = CType(rdr(1), Point)  
  
             ' You can also use GetSqlValue and GetValue  
             ' Dim pnt As Point = CType(rdr.GetSqlValue(1), Point)  
             ' Dim pnt As Point = CType(rdr.GetValue(1), Point)  
  
                ' Print values  
                Console.WriteLine( _  
                 "ID={0} Point={1} X={2} Y={3} DistanceFromXY={4} Distance={5}", _  
                  id, pnt, pnt.X, pnt.Y, pnt.DistanceFromXY(1, 9), pnt.Distance())  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
         & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
  
namespace Microsoft.Samples.SqlServer  
{  
class ReadPoints  
{  
static void Main()  
{  
  string connectionString = GetConnectionString();  
  using (SqlConnection cnn = new SqlConnection(connectionString))  
  {  
    cnn.Open();  
    SqlCommand cmd = new SqlCommand(  
       "SELECT ID, Pnt FROM dbo.Points", cnn);  
    SqlDataReader rdr = cmd.ExecuteReader();  
  
    while (rdr.Read())  
    {  
      // Retrieve the value of the Primary Key column  
      int id = rdr.GetInt32(0);  
  
        // Retrieve the value of the UDT  
        Point pnt = (Point)rdr[1];  
  
        // You can also use GetSqlValue and GetValue  
        // Point pnt = (Point)rdr.GetSqlValue(1);  
        // Point pnt = (Point)rdr.GetValue(1);  
  
        Console.WriteLine(  
        "ID={0} Point={1} X={2} Y={3} DistanceFromXY={4} Distance={5}",   
        id, pnt, pnt.X, pnt.Y, pnt.DistanceFromXY(1, 9), pnt.Distance());  
    }  
  rdr.Close();  
  Console.WriteLine("done");  
  }  
  static private string GetConnectionString()  
  {  
    // To avoid storing the connection string in your code,   
    // you can retrieve it from a configuration file.  
    return "Data Source=(local);Initial Catalog=AdventureWorks;"  
        + "Integrated Security=SSPI";  
  }  
}  
```  
  
## <a name="binding-udts-as-bytes"></a><span data-ttu-id="b222c-126">バイト型としての UDT のバインド</span><span class="sxs-lookup"><span data-stu-id="b222c-126">Binding UDTs as Bytes</span></span>  
 <span data-ttu-id="b222c-127">場合によっては、UDT 列からそのままデータを取得する必要が生じることもあります。</span><span class="sxs-lookup"><span data-stu-id="b222c-127">In some situations, you may want to retrieve the raw data from the UDT column.</span></span> <span data-ttu-id="b222c-128">たとえば、型がローカルに存在しない場合や、UDT のインスタンスを作成したくない場合などです。</span><span class="sxs-lookup"><span data-stu-id="b222c-128">Perhaps the type is not available locally, or you do not wish to instantiate an instance of the UDT.</span></span> <span data-ttu-id="b222c-129">の**GetBytes**メソッドを使用して、生バイトをバイト配列に読み取ることができ `SqlDataReader` ます。</span><span class="sxs-lookup"><span data-stu-id="b222c-129">You can read the raw bytes into a byte array using the **GetBytes** method of a `SqlDataReader`.</span></span> <span data-ttu-id="b222c-130">このメソッドでは、バイトのストリームを、指定した列オフセットから、指定したバッファー オフセットから始まる配列のバッファーに読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="b222c-130">This method reads a stream of bytes from the specified column offset into the buffer of an array starting at a specified buffer offset.</span></span> <span data-ttu-id="b222c-131">別の方法として、 **Getsqlbytes**メソッドまたは**getsqlbytes**メソッドのいずれかを使用して、すべての内容を1回の操作で読み取ることもできます。</span><span class="sxs-lookup"><span data-stu-id="b222c-131">Another option is to use one of the **GetSqlBytes** or **GetSqlBinary** methods and read all of the contents in a single operation.</span></span> <span data-ttu-id="b222c-132">どちらの場合も、UDT オブジェクトのインスタンスが作成されることはないので、クライアントのアセンブリで UDT への参照を設定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b222c-132">In either case, the UDT object is never instantiated, so you do not need to set a reference to the UDT in the client assembly.</span></span>  
  
### <a name="example"></a><span data-ttu-id="b222c-133">例</span><span class="sxs-lookup"><span data-stu-id="b222c-133">Example</span></span>  
 <span data-ttu-id="b222c-134">この例では、を使用して、 **Point**データを生バイトとしてバイト配列に取得する方法を示し `SqlDataReader` ます。</span><span class="sxs-lookup"><span data-stu-id="b222c-134">This example shows how to retrieve the **Point** data as raw bytes into a byte array using a `SqlDataReader`.</span></span> <span data-ttu-id="b222c-135">このコードでは、`System.Text.StringBuilder` を使用して、生のバイト列をコンソール ウィンドウに表示する文字列形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="b222c-135">The code uses a `System.Text.StringBuilder` to convert the raw bytes to a string representation to be displayed in the console window.</span></span>  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Text  
  
Module GetRawBytes  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Retrieve the raw bytes into a byte array  
                Dim buffer(31) As Byte  
                Dim byteCount As Integer = _  
                 CInt(rdr.GetBytes(1, 0, buffer, 0, 31))  
  
                ' Format and print bytes   
                Dim str As New StringBuilder  
                str.AppendFormat("ID={0} Point=", id)  
  
                Dim i As Integer  
                For i = 0 To (byteCount - 1)  
                    str.AppendFormat("{0:x}", buffer(i))  
                Next  
                Console.WriteLine(str.ToString)  
  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Text;  
  
class GetRawBytes  
{  
    static void Main()  
    {  
        string connectionString = GetConnectionString();  
        using (SqlConnection cnn = new SqlConnection(connectionString))  
        {  
            cnn.Open();  
            SqlCommand cmd = new SqlCommand("SELECT ID, Pnt FROM dbo.Points", cnn);  
            SqlDataReader rdr = cmd.ExecuteReader();  
  
            while (rdr.Read())  
            {  
                // Retrieve the value of the Primary Key column  
                int id = rdr.GetInt32(0);  
  
                // Retrieve the raw bytes into a byte array  
                byte[] buffer = new byte[32];  
                long byteCount = rdr.GetBytes(1, 0, buffer, 0, 32);  
  
                // Format and print bytes   
                StringBuilder str = new StringBuilder();  
                str.AppendFormat("ID={0} Point=", id);  
  
                for (int i = 0; i < byteCount; i++)  
                    str.AppendFormat("{0:x}", buffer[i]);  
                Console.WriteLine(str.ToString());  
            }  
            rdr.Close();  
            Console.WriteLine("done");  
        }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
### <a name="example-using-getsqlbytes"></a><span data-ttu-id="b222c-136">GetSqlBytes メソッドの使用例</span><span class="sxs-lookup"><span data-stu-id="b222c-136">Example Using GetSqlBytes</span></span>  
 <span data-ttu-id="b222c-137">この例では、 **Getsqlbytes**メソッドを使用して、1回の操作で生バイトとして**ポイント**データを取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b222c-137">This example shows how to retrieve the **Point** data as raw bytes in a single operation using the **GetSqlBytes** method.</span></span> <span data-ttu-id="b222c-138">このコードでは、`StringBuilder` を使用して、生のバイト列をコンソール ウィンドウに表示する文字列形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="b222c-138">The code uses a `StringBuilder` to convert the raw bytes to a string representation to be displayed in the console window.</span></span>  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Text  
  
Module GetRawBytes  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Use SqlBytes to retrieve raw bytes  
                Dim sb As SqlBytes = rdr.GetSqlBytes(1)  
                Dim byteCount As Long = sb.Length  
  
                ' Format and print bytes   
                Dim str As New StringBuilder  
                str.AppendFormat("ID={0} Point=", id)  
  
                Dim i As Integer  
                For i = 0 To (byteCount - 1)  
                    str.AppendFormat("{0:x}", sb(i))  
                Next  
                Console.WriteLine(str.ToString)  
  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Text;  
  
class GetRawBytes  
{  
    static void Main()  
    {  
         string connectionString = GetConnectionString();  
        using (SqlConnection cnn = new SqlConnection(connectionString))  
        {  
            cnn.Open();  
            SqlCommand cmd = new SqlCommand(  
                "SELECT ID, Pnt FROM dbo.Points", cnn);  
            SqlDataReader rdr = cmd.ExecuteReader();  
  
            while (rdr.Read())  
            {  
                // Retrieve the value of the Primary Key column  
                int id = rdr.GetInt32(0);  
  
                // Use SqlBytes to retrieve raw bytes  
                SqlBytes sb = rdr.GetSqlBytes(1);  
                long byteCount = sb.Length;  
  
                // Format and print bytes   
                StringBuilder str = new StringBuilder();  
                str.AppendFormat("ID={0} Point=", id);  
  
                for (int i = 0; i < byteCount; i++)  
                    str.AppendFormat("{0:x}", sb[i]);  
                Console.WriteLine(str.ToString());  
            }  
            rdr.Close();  
            Console.WriteLine("done");  
        }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
## <a name="working-with-udt-parameters"></a><span data-ttu-id="b222c-139">UDT パラメーターを使用した作業</span><span class="sxs-lookup"><span data-stu-id="b222c-139">Working with UDT Parameters</span></span>  
 <span data-ttu-id="b222c-140">ADO.NET コードでは、UDT は入力パラメーターと出力パラメーターのどちらとしても使用することができます。</span><span class="sxs-lookup"><span data-stu-id="b222c-140">UDTs can be used as both input and output parameters in your ADO.NET code.</span></span>  
  
## <a name="using-udts-in-query-parameters"></a><span data-ttu-id="b222c-141">クエリ パラメーターでの UDT の使用</span><span class="sxs-lookup"><span data-stu-id="b222c-141">Using UDTs in Query Parameters</span></span>  
 <span data-ttu-id="b222c-142">UDT は、`SqlParameter` オブジェクトの `System.Data.SqlClient.SqlCommand` を設定する際にパラメーター値として使用できます。</span><span class="sxs-lookup"><span data-stu-id="b222c-142">UDTs can be used as parameter values when setting up a `SqlParameter` for a `System.Data.SqlClient.SqlCommand` object.</span></span> <span data-ttu-id="b222c-143">`SqlDbType.Udt` オブジェクトの `SqlParameter` 列挙値は、`Add` コレクションに対して `Parameters` メソッドを呼び出す際、パラメーターが UDT であることを示すために使用します。</span><span class="sxs-lookup"><span data-stu-id="b222c-143">The `SqlDbType.Udt` enumeration of a `SqlParameter` object is used to indicate that the parameter is a UDT when calling the `Add` method to the `Parameters` collection.</span></span> <span data-ttu-id="b222c-144">`UdtTypeName`オブジェクトのプロパティは `SqlCommand` 、データベース内の UDT の完全修飾名を指定するために使用されます。 *schema_name object_name*構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="b222c-144">The `UdtTypeName` property of a `SqlCommand` object is used to specify the fully qualified name of the UDT in the database using the *database.schema_name.object_name* syntax.</span></span> <span data-ttu-id="b222c-145">必須ではありませんが、完全修飾名を使用すると、コードを明確にすることができます。</span><span class="sxs-lookup"><span data-stu-id="b222c-145">Although it is not required, using the fully qualified name removes ambiguity from your code.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b222c-146">クライアント プロジェクトが、UDT アセンブリのローカル コピーを使用できることが前提です。</span><span class="sxs-lookup"><span data-stu-id="b222c-146">A local copy of the UDT assembly must be available to the client project.</span></span>  
  
### <a name="example"></a><span data-ttu-id="b222c-147">例</span><span class="sxs-lookup"><span data-stu-id="b222c-147">Example</span></span>  
 <span data-ttu-id="b222c-148">この例のコードでは、`SqlCommand` オブジェクトと `SqlParameter` オブジェクトを使用して、テーブルの UDT 列にデータを挿入します。</span><span class="sxs-lookup"><span data-stu-id="b222c-148">The code in this example creates `SqlCommand` and `SqlParameter` objects to insert data into a UDT column in a table.</span></span> <span data-ttu-id="b222c-149">このコードでは、`SqlDbType.Udt` 列挙値を使用してデータ型を指定し、`UdtTypeName` オブジェクトの `SqlParameter` プロパティを使用してデータベースの UDT の完全修飾名を指定します。</span><span class="sxs-lookup"><span data-stu-id="b222c-149">The code uses the `SqlDbType.Udt` enumeration to specify the data type, and the `UdtTypeName` property of the `SqlParameter` object to specify the fully qualified name of the UDT in the database.</span></span>  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports system.Data  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim ConnectionString As String = GetConnectionString()  
    Dim cnn As New SqlConnection(ConnectionString)  
    Using cnn  
      Dim cmd As SqlCommand = cnn.CreateCommand()  
      cmd.CommandText = "INSERT INTO dbo.Points (Pnt) VALUES (@Point)"  
      cmd.CommandType = CommandType.Text  
  
      Dim param As New SqlParameter("@Point", SqlDbType.Udt)      param.UdtTypeName = "TestPoint.dbo.Point"      param.Direction = ParameterDirection.Input      param.Value = New Point(5, 6)      cmd.Parameters.Add(param)  
  
      cnn.Open()  
      cmd.ExecuteNonQuery()  
      Console.WriteLine("done")  
    End Using  
  End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlClient;  
  
class Class1  
{  
static void Main()  
{  
  string ConnectionString = GetConnectionString();  
     using (SqlConnection cnn = new SqlConnection(ConnectionString))  
     {  
       SqlCommand cmd = cnn.CreateCommand();  
       cmd.CommandText =   
         "INSERT INTO dbo.Points (Pnt) VALUES (@Point)";  
       cmd.CommandType = CommandType.Text;  
  
       SqlParameter param = new SqlParameter("@Point", SqlDbType.Udt);       param.UdtTypeName = "TestPoint.dbo.Point";       param.Direction = ParameterDirection.Input;       param.Value = new Point(5, 6);       cmd.Parameters.Add(param);  
  
       cnn.Open();  
       cmd.ExecuteNonQuery();  
       Console.WriteLine("done");  
     }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b222c-150">参照</span><span class="sxs-lookup"><span data-stu-id="b222c-150">See Also</span></span>  
 [<span data-ttu-id="b222c-151">ADO.NET でのユーザー定義型へのアクセス</span><span class="sxs-lookup"><span data-stu-id="b222c-151">Accessing User-Defined Types in ADO.NET</span></span>](accessing-user-defined-types-in-ado-net.md)  
  
  
