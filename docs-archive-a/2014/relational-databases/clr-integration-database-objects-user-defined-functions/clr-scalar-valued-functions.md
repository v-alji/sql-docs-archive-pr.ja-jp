---
title: CLR スカラー値関数 |Microsoft Docs
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
- SVF
- scalar-valued functions
ms.assetid: 20dcf802-c27d-4722-9cd3-206b1e77bee0
author: rothja
ms.author: jroth
ms.openlocfilehash: be8f9616fb285d6a68d6734924874ded06fb3bd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714430"
---
# <a name="clr-scalar-valued-functions"></a><span data-ttu-id="75bcc-102">CLR スカラー値関数</span><span class="sxs-lookup"><span data-stu-id="75bcc-102">CLR Scalar-Valued Functions</span></span>
  <span data-ttu-id="75bcc-103">スカラー値関数 (SVF) は、文字列値、整数値、ビット値などの単一値を返します。任意の .NET Framework プログラミング言語を使用し、マネージド コードでユーザー定義スカラー値関数を作成できます。</span><span class="sxs-lookup"><span data-stu-id="75bcc-103">A scalar-valued function (SVF) returns a single value, such as a string, integer, or bit value.You can create scalar-valued user-defined functions in managed code using any .NET Framework programming language.</span></span> <span data-ttu-id="75bcc-104">これらの関数からは、[!INCLUDE[tsql](../../includes/tsql-md.md)] コードや他のマネージド コードにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="75bcc-104">These functions are accessible to [!INCLUDE[tsql](../../includes/tsql-md.md)] or other managed code.</span></span> <span data-ttu-id="75bcc-105">CLR 統合の利点とマネージコードとの使い分けの詳細については [!INCLUDE[tsql](../../includes/tsql-md.md)] 、「 [clr 統合の概要](../clr-integration/clr-integration-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75bcc-105">For information about the advantages of CLR integration and choosing between managed code and [!INCLUDE[tsql](../../includes/tsql-md.md)], see [Overview of CLR Integration](../clr-integration/clr-integration-overview.md).</span></span>  
  
## <a name="requirements-for-clr-scalar-valued-functions"></a><span data-ttu-id="75bcc-106">CLR スカラー値関数の要件</span><span class="sxs-lookup"><span data-stu-id="75bcc-106">Requirements for CLR Scalar-Valued Functions</span></span>  
 <span data-ttu-id="75bcc-107">.NET Framework SVF は、.NET Framework アセンブリのクラスのメソッドとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="75bcc-107">.NET Framework SVFs are implemented as methods on a class in a .NET Framework assembly.</span></span> <span data-ttu-id="75bcc-108">SVF から返される入力パラメーターと型は、でサポートされる任意のスカラーデータ型にすることができます。ただし、、、、、、、、、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `varchar` `char` `rowversion` `text` `ntext` `image` `timestamp` `table` またはは除き `cursor` ます。</span><span class="sxs-lookup"><span data-stu-id="75bcc-108">The input parameters and the type returned from a SVF can be any of the scalar data types supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], except `varchar`, `char`, `rowversion`, `text`, `ntext`, `image`, `timestamp`, `table`, or `cursor`.</span></span> <span data-ttu-id="75bcc-109">SVF では、実装メソッドの戻り値のデータ型が上記のいずれかの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型になるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="75bcc-109">SVFs must ensure a match between the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type and the return data type of the implementation method.</span></span> <span data-ttu-id="75bcc-110">型変換の詳細については、「 [CLR パラメーターデータのマッピング](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75bcc-110">For more information about type conversions, see [Mapping CLR Parameter Data](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).</span></span>  
  
 <span data-ttu-id="75bcc-111">.NET Framework 言語で .NET Framework SVF を実装する場合、`SqlFunction` カスタム属性を指定し、その関数に関する詳細情報を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="75bcc-111">When implementing a .NET Framework SVF in a .NET Framework language, the `SqlFunction` custom attribute can be specified to include additional information about the function.</span></span> <span data-ttu-id="75bcc-112">`SqlFunction` 属性は、その関数がデータへのアクセスや変更を行うかどうか、決定的関数かどうか、浮動小数点演算を必要とするかどうかなどを示します。</span><span class="sxs-lookup"><span data-stu-id="75bcc-112">The `SqlFunction` attribute indicates whether or not the function accesses or modifies data, if it is deterministic, and if the function involves floating point operations.</span></span>  
  
 <span data-ttu-id="75bcc-113">ユーザー定義スカラー値関数は、決定的関数になる場合と非決定的関数になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="75bcc-113">Scalar-valued user-defined functions may be deterministic or non-deterministic.</span></span> <span data-ttu-id="75bcc-114">特定の入力パラメーターのセットを渡して決定的関数を呼び出すと、常に同じ結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="75bcc-114">A deterministic function always returns the same result when it is called with a specific set of input parameters.</span></span> <span data-ttu-id="75bcc-115">一方、特定の入力パラメーターのセットを渡して非決定的関数を呼び出すと、異なる結果が返されることがあります。</span><span class="sxs-lookup"><span data-stu-id="75bcc-115">A non-deterministic function may return different results when it is called with a specific set of input parameters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="75bcc-116">入力値とデータベースの状態が同じでも、関数が必ずしも常に同じ出力値を生成しない場合は、その関数を決定的関数としてマークしないでください。</span><span class="sxs-lookup"><span data-stu-id="75bcc-116">Do not mark a function as deterministic if the function does not always produces the same output values, given the same input values and the same database state.</span></span> <span data-ttu-id="75bcc-117">完全に決定的ではない関数を決定的関数としてマークした場合、インデックス付きビューと計算列が破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="75bcc-117">Marking a function as deterministic, when the function isn't truly deterministic can result in corrupted indexed views and computed columns.</span></span> <span data-ttu-id="75bcc-118">関数を決定的関数としてマークするには、`IsDeterministic` プロパティを True に設定します。</span><span class="sxs-lookup"><span data-stu-id="75bcc-118">You mark a function as deterministic by setting the `IsDeterministic` property to true.</span></span>  
  
### <a name="table-valued-parameters"></a><span data-ttu-id="75bcc-119">テーブル値パラメーター</span><span class="sxs-lookup"><span data-stu-id="75bcc-119">Table-Valued Parameters</span></span>  
 <span data-ttu-id="75bcc-120">テーブル値パラメーター (TVP) とは、プロシージャや関数に渡されるユーザー定義のテーブル型です。TVP を使用すると、複数行のデータを効率的にサーバーに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="75bcc-120">Table-valued parameters (TVPs), user-defined table types that are passed into a procedure or function, provide an efficient way to pass multiple rows of data to the server.</span></span> <span data-ttu-id="75bcc-121">TVP の機能はパラメーター配列に似ていますが、より柔軟性が高く、[!INCLUDE[tsql](../../includes/tsql-md.md)] との統合も緊密です。</span><span class="sxs-lookup"><span data-stu-id="75bcc-121">TVPs provide similar functionality to parameter arrays, but offer greater flexibility and closer integration with [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="75bcc-122">テーブル値パラメーターを使用するとパフォーマンスが向上する可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="75bcc-122">They also provide the potential for better performance.</span></span> <span data-ttu-id="75bcc-123">また、サーバーへのラウンド トリップを減らすのにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="75bcc-123">TVPs also help reduce the number of round trips to the server.</span></span> <span data-ttu-id="75bcc-124">スカラー パラメーターのリストを使用するなどしてサーバーに複数の要求を送信する代わりに、データを TVP としてサーバーに送信できます。</span><span class="sxs-lookup"><span data-stu-id="75bcc-124">Instead of sending multiple requests to the server, such as with a list of scalar parameters, data can be sent to the server as a TVP.</span></span> <span data-ttu-id="75bcc-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のプロセスで実行されているマネージド ストアド プロシージャやマネージド関数にユーザー定義のテーブル型をテーブル値パラメーターとして渡したり、戻り値として受け取ったりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="75bcc-125">A user-defined table type cannot be passed as a table-valued parameter to, or be returned from, a managed stored procedure or function executing in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span> <span data-ttu-id="75bcc-126">Tvp の詳細については、「[データベースエンジン&#41;&#40;テーブル値パラメーターの使用](../tables/use-table-valued-parameters-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75bcc-126">For more information about TVPs, see [Use Table-Valued Parameters &#40;Database Engine&#41;](../tables/use-table-valued-parameters-database-engine.md).</span></span>  
  
## <a name="example-of-a-clr-scalar-valued-function"></a><span data-ttu-id="75bcc-127">CLR スカラー値関数の例</span><span class="sxs-lookup"><span data-stu-id="75bcc-127">Example of a CLR Scalar-Valued Function</span></span>  
 <span data-ttu-id="75bcc-128">データにアクセスして整数値を返す簡単な SVF を次に示します。</span><span class="sxs-lookup"><span data-stu-id="75bcc-128">Here is a simple SVF that accesses data and returns an integer value:</span></span>  
  
```csharp  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
  
public class T  
{  
    [SqlFunction(DataAccess = DataAccessKind.Read)]  
    public static int ReturnOrderCount()  
    {  
        using (SqlConnection conn   
            = new SqlConnection("context connection=true"))  
        {  
            conn.Open();  
            SqlCommand cmd = new SqlCommand(  
                "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn);  
            return (int)cmd.ExecuteScalar();  
        }  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Public Class T  
    <SqlFunction(DataAccess:=DataAccessKind.Read)> _  
    Public Shared Function ReturnOrderCount() As Integer  
        Using conn As New SqlConnection("context connection=true")  
            conn.Open()  
            Dim cmd As New SqlCommand("SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn)  
            Return CType(cmd.ExecuteScalar(), Integer)  
        End Using  
    End Function  
End Class  
```  
  
 <span data-ttu-id="75bcc-129">コードの 1 行目では、属性にアクセスするために `Microsoft.SqlServer.Server` を参照し、ADO.NET 名前空間にアクセスするために `System.Data.SqlClient`</span><span class="sxs-lookup"><span data-stu-id="75bcc-129">The first line of code references `Microsoft.SqlServer.Server` to access attributes and `System.Data.SqlClient` to access the ADO.NET namespace.</span></span> <span data-ttu-id="75bcc-130">(この名前空間には、.NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の `SqlClient` が含まれます) を参照しています。</span><span class="sxs-lookup"><span data-stu-id="75bcc-130">(This namespace contains `SqlClient`, the .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
 <span data-ttu-id="75bcc-131">次に、この関数は `SqlFunction` 名前空間の `Microsoft.SqlServer.Server` カスタム属性を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="75bcc-131">Next, the function receives the `SqlFunction` custom attribute, which is found in the `Microsoft.SqlServer.Server` namespace.</span></span> <span data-ttu-id="75bcc-132">このカスタム属性は、UDF (ユーザー定義関数) がサーバーのデータを読み取るときにインプロセス プロバイダーを使用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="75bcc-132">The custom attribute indicates whether or not the user-defined function (UDF) uses the in-process provider to read data in the server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="75bcc-133">では、UDF によるデータの更新、挿入、または削除を許可していません。</span><span class="sxs-lookup"><span data-stu-id="75bcc-133">does not allow UDFs to update, insert, or delete data.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="75bcc-134">では、インプロセス プロバイダーを使用しない UDF の実行を最適化できます。</span><span class="sxs-lookup"><span data-stu-id="75bcc-134">can optimize execution of a UDF that does not use the in-process provider.</span></span> <span data-ttu-id="75bcc-135">これを指定するには、`DataAccessKind` を `DataAccessKind.None` に設定します。</span><span class="sxs-lookup"><span data-stu-id="75bcc-135">This is indicated by setting `DataAccessKind` to `DataAccessKind.None`.</span></span> <span data-ttu-id="75bcc-136">その次の行で、対象のメソッドは public static (Visual Basic .NET では shared) になっています。</span><span class="sxs-lookup"><span data-stu-id="75bcc-136">On the next line, the target method is a public static (shared in Visual Basic .NET).</span></span>  
  
 <span data-ttu-id="75bcc-137">`SqlContext` 名前空間の `Microsoft.SqlServer.Server` クラスは、既に設定されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへの接続を使用して `SqlCommand` オブジェクトにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="75bcc-137">The `SqlContext` class, located in the `Microsoft.SqlServer.Server` namespace, can then access a `SqlCommand` object with a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that is already set up.</span></span> <span data-ttu-id="75bcc-138">ここでは使用されていませんが、`System.Transactions` API (アプリケーション プログラミング インターフェイス) を使って現在のトランザクション コンテキストを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="75bcc-138">Although not used here, the current transaction context is also available through the `System.Transactions` application programming interface (API).</span></span>  
  
 <span data-ttu-id="75bcc-139">関数の本文に記述されているコード行のほとんどは、`System.Data.SqlClient` 名前空間の型を使用しており、クライアント アプリケーションを記述したことのある開発者にとってはなじみのあるコードです。</span><span class="sxs-lookup"><span data-stu-id="75bcc-139">Most of the lines of code in the function body should look familiar to developers who have written client applications that use the types found in the `System.Data.SqlClient` namespace.</span></span>  
  
 <span data-ttu-id="75bcc-140">[C#]</span><span class="sxs-lookup"><span data-stu-id="75bcc-140">[C#]</span></span>  
  
```  
using(SqlConnection conn = new SqlConnection("context connection=true"))   
{  
   conn.Open();  
   SqlCommand cmd = new SqlCommand(  
        "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn);  
   return (int) cmd.ExecuteScalar();  
}    
```  
  
 <span data-ttu-id="75bcc-141">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="75bcc-141">[Visual Basic]</span></span>  
  
```  
Using conn As New SqlConnection("context connection=true")  
   conn.Open()  
   Dim cmd As New SqlCommand( _  
        "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn)  
   Return CType(cmd.ExecuteScalar(), Integer)  
End Using  
```  
  
 <span data-ttu-id="75bcc-142">`SqlCommand` オブジェクトを初期化することにより、適切なコマンド テキストが指定されます。</span><span class="sxs-lookup"><span data-stu-id="75bcc-142">The appropriate command text is specified by initializing the `SqlCommand` object.</span></span> <span data-ttu-id="75bcc-143">上の例では、テーブル `SalesOrderHeader` 内の行数をカウントしています。</span><span class="sxs-lookup"><span data-stu-id="75bcc-143">The previous example counts the number of rows in table `SalesOrderHeader`.</span></span> <span data-ttu-id="75bcc-144">次に、`ExecuteScalar` オブジェクトの `cmd` メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="75bcc-144">Next, the `ExecuteScalar` method of the `cmd` object is called.</span></span> <span data-ttu-id="75bcc-145">これにより、クエリに基づいて `int` 型の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="75bcc-145">This returns a value of type `int` based on the query.</span></span> <span data-ttu-id="75bcc-146">最後に、注文数が呼び出し側に返されます。</span><span class="sxs-lookup"><span data-stu-id="75bcc-146">Finally, the order count is returned to the caller.</span></span>  
  
 <span data-ttu-id="75bcc-147">このコードを FirstUdf.cs というファイルに保存すると、次のようにアセンブリとしてコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="75bcc-147">If this code is saved in a file called FirstUdf.cs, it could be compiled into as assembly as follows:</span></span>  
  
 <span data-ttu-id="75bcc-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="75bcc-148">[C#]</span></span>  
  
```  
csc.exe /t:library /out:FirstUdf.dll FirstUdf.cs   
```  
  
 <span data-ttu-id="75bcc-149">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="75bcc-149">[Visual Basic]</span></span>  
  
```  
vbc.exe /t:library /out:FirstUdf.dll FirstUdf.vb  
```  
  
> [!NOTE]  
>  <span data-ttu-id="75bcc-150">`/t:library`は、実行可能ファイルではなくライブラリを生成することを示しています。</span><span class="sxs-lookup"><span data-stu-id="75bcc-150">`/t:library` indicates that a library, rather than an executable, should be produced.</span></span> <span data-ttu-id="75bcc-151">実行可能ファイルは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には登録できません。</span><span class="sxs-lookup"><span data-stu-id="75bcc-151">Executables cannot be registered in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="75bcc-152">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、`/clr:pure` を指定してコンパイルした Visual C++ のデータベース オブジェクトは実行できません。</span><span class="sxs-lookup"><span data-stu-id="75bcc-152">Visual C++ database objects compiled with `/clr:pure` are not supported for execution on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="75bcc-153">このようなデータベース オブジェクトには、スカラー値関数などがあります。</span><span class="sxs-lookup"><span data-stu-id="75bcc-153">For example, such database objects include scalar-valued functions.</span></span>  
  
 <span data-ttu-id="75bcc-154">アセンブリと UDF を登録する [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリと呼び出しの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="75bcc-154">The [!INCLUDE[tsql](../../includes/tsql-md.md)] query and a sample invocation to register the assembly and UDF are:</span></span>  
  
```  
CREATE ASSEMBLY FirstUdf FROM 'FirstUdf.dll';  
GO  
  
CREATE FUNCTION CountSalesOrderHeader() RETURNS INT   
AS EXTERNAL NAME FirstUdf.T.ReturnOrderCount;   
GO  
  
SELECT dbo.CountSalesOrderHeader();  
GO  
  
```  
  
 <span data-ttu-id="75bcc-155">[!INCLUDE[tsql](../../includes/tsql-md.md)] で公開する関数名は、対象の public static メソッドの名前と一致している必要はありません。</span><span class="sxs-lookup"><span data-stu-id="75bcc-155">Note that the function name as exposed in [!INCLUDE[tsql](../../includes/tsql-md.md)] does not need to match the name of the target public static method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75bcc-156">参照</span><span class="sxs-lookup"><span data-stu-id="75bcc-156">See Also</span></span>  
 <span data-ttu-id="75bcc-157">[CLR パラメーターデータのマッピング](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md) </span><span class="sxs-lookup"><span data-stu-id="75bcc-157">[Mapping CLR Parameter Data](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md) </span></span>  
 <span data-ttu-id="75bcc-158">[CLR 統合のカスタム属性の概要](../../database-engine/dev-guide/overview-of-clr-integration-custom-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="75bcc-158">[Overview of CLR Integration Custom Attributes](../../database-engine/dev-guide/overview-of-clr-integration-custom-attributes.md) </span></span>  
 <span data-ttu-id="75bcc-159">[ユーザー定義関数](../user-defined-functions/user-defined-functions.md) </span><span class="sxs-lookup"><span data-stu-id="75bcc-159">[User-Defined Functions](../user-defined-functions/user-defined-functions.md) </span></span>  
 [<span data-ttu-id="75bcc-160">CLR データベース オブジェクトからのデータ アクセス</span><span class="sxs-lookup"><span data-stu-id="75bcc-160">Data Access from CLR Database Objects</span></span>](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
