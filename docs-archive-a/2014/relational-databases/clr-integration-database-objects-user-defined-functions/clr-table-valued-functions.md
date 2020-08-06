---
title: CLR テーブル値関数 |Microsoft Docs
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
- Transact-SQL table-valued functions
- table-valued functions [CLR integration]
- TVFs [CLR integration]
ms.assetid: 9a6133ea-36e9-45bf-b572-1c0df3d6c194
author: rothja
ms.author: jroth
ms.openlocfilehash: b700aba5a753ecd8ee50ee9b7679cafb2f1f8581
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641696"
---
# <a name="clr-table-valued-functions"></a><span data-ttu-id="e4311-102">CLR テーブル値関数</span><span class="sxs-lookup"><span data-stu-id="e4311-102">CLR Table-Valued Functions</span></span>
  <span data-ttu-id="e4311-103">テーブル値関数とは、テーブルを返すユーザー定義関数です。</span><span class="sxs-lookup"><span data-stu-id="e4311-103">A table-valued function is a user-defined function that returns a table.</span></span>  
  
 <span data-ttu-id="e4311-104">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、テーブル値関数の機能が拡張され、テーブル値関数をどのマネージド言語でも定義できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e4311-104">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] extends the functionality of table-valued functions by allowing you to define a table-valued function in any managed language.</span></span> <span data-ttu-id="e4311-105">テーブル値関数からは `IEnumerable` オブジェクトまたは `IEnumerator` オブジェクトを経由してデータが返されます。</span><span class="sxs-lookup"><span data-stu-id="e4311-105">Data is returned from a table-valued function through an `IEnumerable` or `IEnumerator` object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e4311-106">テーブル値関数で返されるテーブル型の列には、timestamp 型の列および Unicode 以外の文字列データ型の列 (`char`、`varchar`、`text` など) を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="e4311-106">For table-valued functions, the columns of the return table type cannot include timestamp columns or non-Unicode string data type columns (such as `char`, `varchar`, and `text`).</span></span> <span data-ttu-id="e4311-107">NOT NULL 制約はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e4311-107">The NOT NULL constraint is not supported.</span></span>  
  
## <a name="differences-between-transact-sql-and-clr-table-valued-functions"></a><span data-ttu-id="e4311-108">Transact-SQL と CLR のテーブル値関数の違い</span><span class="sxs-lookup"><span data-stu-id="e4311-108">Differences Between Transact-SQL and CLR Table-Valued Functions</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="e4311-109">のテーブル値関数は、関数の呼び出し結果を具体化して中間テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="e4311-109">table-valued functions materialize the results of calling the function into an intermediate table.</span></span> <span data-ttu-id="e4311-110">TVF では中間テーブルを使用するため、結果に対する制約や一意インデックスがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e4311-110">Since they use an intermediate table, they can support constraints and unique indexes over the results.</span></span> <span data-ttu-id="e4311-111">これらの機能は、大量の結果が返される場合に非常に有用です。</span><span class="sxs-lookup"><span data-stu-id="e4311-111">These features can be extremely useful when large results are returned.</span></span>  
  
 <span data-ttu-id="e4311-112">一方、CLR のテーブル値関数は同じことをストリーミングで実現します。</span><span class="sxs-lookup"><span data-stu-id="e4311-112">In contrast, CLR table-valued functions represent a streaming alternative.</span></span> <span data-ttu-id="e4311-113">結果セット全体を 1 つのテーブルに具体化する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e4311-113">There is no requirement that the entire set of results be materialized in a single table.</span></span> <span data-ttu-id="e4311-114">テーブル値関数を呼び出すクエリの実行プランから、マネージド関数が返す `IEnumerable` オブジェクトを直接呼び出し、結果を増分方式で使用します。</span><span class="sxs-lookup"><span data-stu-id="e4311-114">The `IEnumerable` object returned by the managed function is directly called by the execution plan of the query that calls the table-valued function, and the results are consumed in an incremental manner.</span></span> <span data-ttu-id="e4311-115">このストリーミング モデルでは、テーブル全体に値が格納されるまで待たなくても、最初の行が生成された直後から結果を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e4311-115">This streaming model ensures that results can be consumed immediately after the first row is available, instead of waiting for the entire table to be populated.</span></span> <span data-ttu-id="e4311-116">返される行をメモリ内で一括して具体化する必要がないので、返される行数が多い場合にもストリーミングが適しています。</span><span class="sxs-lookup"><span data-stu-id="e4311-116">It is also a better alternative if you have very large numbers of rows returned, because they do not have to be materialized in memory as a whole.</span></span> <span data-ttu-id="e4311-117">たとえば、マネージド テーブル値関数を使用して、テキスト ファイルを解析し、テキストの各行を 1 つのテーブル行にして返すことができます。</span><span class="sxs-lookup"><span data-stu-id="e4311-117">For example, a managed table-valued function could be used to parse a text file and return each line as a row.</span></span>  
  
## <a name="implementing-table-valued-functions"></a><span data-ttu-id="e4311-118">テーブル値関数の実装</span><span class="sxs-lookup"><span data-stu-id="e4311-118">Implementing Table-Valued Functions</span></span>  
 <span data-ttu-id="e4311-119">テーブル値関数は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework アセンブリのクラスのメソッドとして実装します。</span><span class="sxs-lookup"><span data-stu-id="e4311-119">Implement table-valued functions as methods on a class in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework assembly.</span></span> <span data-ttu-id="e4311-120">テーブル値関数のコードでは、`IEnumerable` インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4311-120">Your table-valued function code must implement the `IEnumerable` interface.</span></span> <span data-ttu-id="e4311-121">`IEnumerable` インターフェイスは .NET Framework で定義されています。</span><span class="sxs-lookup"><span data-stu-id="e4311-121">The `IEnumerable` interface is defined in the .NET Framework.</span></span> <span data-ttu-id="e4311-122">.NET Framework で配列およびコレクションを表す型は、既に `IEnumerable` インターフェイスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="e4311-122">Types representing arrays and collections in the .NET Framework already implement the `IEnumerable` interface.</span></span> <span data-ttu-id="e4311-123">このため、コレクションまたは配列を結果セットに変換するテーブル値関数を簡単に記述できます。</span><span class="sxs-lookup"><span data-stu-id="e4311-123">This makes it easy for writing table-valued functions that convert a collection or an array into a result set.</span></span>  
  
## <a name="table-valued-parameters"></a><span data-ttu-id="e4311-124">テーブル値パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4311-124">Table-Valued Parameters</span></span>  
 <span data-ttu-id="e4311-125">テーブル値パラメーターとは、プロシージャや関数に渡されるユーザー定義のテーブル型です。テーブル値パラメーターを使用すると、複数行のデータを効率的にサーバーに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="e4311-125">Table-valued parameters are user-defined table types that are passed into a procedure or function and provide an efficient way to pass multiple rows of data to the server.</span></span> <span data-ttu-id="e4311-126">テーブル値パラメーターの機能はパラメーター配列に似ていますが、より柔軟性が高く、[!INCLUDE[tsql](../../includes/tsql-md.md)] との統合も緊密です。</span><span class="sxs-lookup"><span data-stu-id="e4311-126">Table-valued parameters provide similar functionality to parameter arrays, but offer greater flexibility and closer integration with [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e4311-127">テーブル値パラメーターを使用するとパフォーマンスが向上する可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="e4311-127">They also provide the potential for better performance.</span></span> <span data-ttu-id="e4311-128">さらに、サーバーへのラウンド トリップの回数を減らすのにも有用です。</span><span class="sxs-lookup"><span data-stu-id="e4311-128">Table-valued parameters also help reduce the number of round trips to the server.</span></span> <span data-ttu-id="e4311-129">スカラー パラメーターのリストを使用するなどしてサーバーに複数の要求を送信する代わりに、データをテーブル値パラメーターとしてサーバーに送信できます。</span><span class="sxs-lookup"><span data-stu-id="e4311-129">Instead of sending multiple requests to the server, such as with a list of scalar parameters, data can be sent to the server as a table-valued parameter.</span></span> <span data-ttu-id="e4311-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のプロセスで実行されているマネージド ストアド プロシージャやマネージド関数にユーザー定義のテーブル型をテーブル値パラメーターとして渡したり、戻り値として受け取ったりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e4311-130">A user-defined table type cannot be passed as a table-valued parameter to, or be returned from, a managed stored procedure or function executing in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span> <span data-ttu-id="e4311-131">テーブル値パラメーターの詳細については、「[テーブル値パラメーターの使用 &#40;データベース エンジン&#41;](../tables/use-table-valued-parameters-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4311-131">For more information about table-valued parameters, see [Use Table-Valued Parameters &#40;Database Engine&#41;](../tables/use-table-valued-parameters-database-engine.md).</span></span>  
  
## <a name="output-parameters-and-table-valued-functions"></a><span data-ttu-id="e4311-132">出力パラメーターとテーブル値関数</span><span class="sxs-lookup"><span data-stu-id="e4311-132">Output Parameters and Table-Valued Functions</span></span>  
 <span data-ttu-id="e4311-133">出力パラメーターを使用すると、テーブル値関数から情報を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="e4311-133">Information may be returned from table-valued functions using output parameters.</span></span> <span data-ttu-id="e4311-134">実装コードのテーブル値関数の対応するパラメーターは、引数として参照渡しのパラメーターを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4311-134">The corresponding parameter in the implementation code table-valued function should use a pass-by-reference parameter as the argument.</span></span> <span data-ttu-id="e4311-135">Visual Basic は出力パラメーターを Visual C# と同様にはサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e4311-135">Note that Visual Basic does not support output parameters in the same way that Visual C# does.</span></span> <span data-ttu-id="e4311-136">次に示すように、パラメーターを参照によって指定し、属性を適用し \<Out()> て出力パラメーターを表す必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4311-136">You must specify the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
...  
Public Shared Sub FillRow ( <Out()> ByRef value As SqlInt32)  
```  
  
### <a name="defining-a-table-valued-function-in-transact-sql"></a><span data-ttu-id="e4311-137">Transact-SQL のテーブル値関数の定義</span><span class="sxs-lookup"><span data-stu-id="e4311-137">Defining a Table-Valued Function in Transact-SQL</span></span>  
 <span data-ttu-id="e4311-138">CLR テーブル値関数を定義するための構文は [!INCLUDE[tsql](../../includes/tsql-md.md)] テーブル値関数の構文と似ていますが、`EXTERNAL NAME` 句が追加されています。</span><span class="sxs-lookup"><span data-stu-id="e4311-138">The syntax for defining a CLR table-valued function is similar to that of a [!INCLUDE[tsql](../../includes/tsql-md.md)] table-valued function, with the addition of the `EXTERNAL NAME` clause.</span></span> <span data-ttu-id="e4311-139">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e4311-139">For example:</span></span>  
  
```  
CREATE FUNCTION GetEmpFirstLastNames()  
RETURNS TABLE (FirstName NVARCHAR(4000), LastName NVARCHAR(4000))  
EXTERNAL NAME MyDotNETAssembly.[MyNamespace.MyClassname]. GetEmpFirstLastNames;  
```  
  
 <span data-ttu-id="e4311-140">テーブル値関数を使用して、クエリで追加処理を行うリレーショナル形式のデータを表現できます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e4311-140">Table-valued functions are used to represent data in relational form for further processing in queries such as:</span></span>  
  
```  
select * from function();  
select * from tbl join function() f on tbl.col = f.col;  
select * from table t cross apply function(t.column);  
```  
  
 <span data-ttu-id="e4311-141">テーブル値関数は、次の場合にテーブルを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="e4311-141">Table-valued functions can return a table when:</span></span>  
  
-   <span data-ttu-id="e4311-142">スカラー値の入力引数から作成された場合。</span><span class="sxs-lookup"><span data-stu-id="e4311-142">Created from scalar input arguments.</span></span> <span data-ttu-id="e4311-143">たとえば、数値をコンマで区切った文字列をピボットしてテーブルにするテーブル値関数などです。</span><span class="sxs-lookup"><span data-stu-id="e4311-143">For example, a table-valued function that takes a comma-delimited string of numbers and pivots them into a table.</span></span>  
  
-   <span data-ttu-id="e4311-144">外部データから生成した場合。</span><span class="sxs-lookup"><span data-stu-id="e4311-144">Generated from external data.</span></span> <span data-ttu-id="e4311-145">たとえば、イベント ログを読み取り、テーブルとして公開するテーブル値関数などです。</span><span class="sxs-lookup"><span data-stu-id="e4311-145">For example, a table-valued function that reads the event log and exposes it as a table.</span></span>  
  
 <span data-ttu-id="e4311-146">**メモ**テーブル値関数は、メソッドでは [!INCLUDE[tsql](../../includes/tsql-md.md)] なく、メソッド内のクエリを通じてのみデータアクセスを実行でき `InitMethod` `FillRow` ます。</span><span class="sxs-lookup"><span data-stu-id="e4311-146">**Note** A table-valued function can only perform data access through a [!INCLUDE[tsql](../../includes/tsql-md.md)] query in the `InitMethod` method, and not in the `FillRow` method.</span></span> <span data-ttu-id="e4311-147">[!INCLUDE[tsql](../../includes/tsql-md.md)] クエリを実行する場合は、`InitMethod` を `SqlFunction.DataAccess.Read` 属性プロパティに指定してください。</span><span class="sxs-lookup"><span data-stu-id="e4311-147">The `InitMethod` should be marked with the `SqlFunction.DataAccess.Read` attribute property if a [!INCLUDE[tsql](../../includes/tsql-md.md)] query is performed.</span></span>  
  
## <a name="a-sample-table-valued-function"></a><span data-ttu-id="e4311-148">テーブル値関数のサンプル</span><span class="sxs-lookup"><span data-stu-id="e4311-148">A Sample Table-Valued Function</span></span>  
 <span data-ttu-id="e4311-149">次のテーブル値関数は、システム イベント ログから情報を返します。</span><span class="sxs-lookup"><span data-stu-id="e4311-149">The following table-valued function returns information from the system event log.</span></span> <span data-ttu-id="e4311-150">読み取るイベント ログの名前を含んだ文字列引数を 1 つ受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e4311-150">The function takes a single string argument containing the name of the event log to read.</span></span>  
  
###### <a name="sample-code"></a><span data-ttu-id="e4311-151">サンプル コード</span><span class="sxs-lookup"><span data-stu-id="e4311-151">Sample Code</span></span>  
  
```csharp  
using System;  
using System.Data.Sql;  
using Microsoft.SqlServer.Server;  
using System.Collections;  
using System.Data.SqlTypes;  
using System.Diagnostics;  
  
public class TabularEventLog  
{  
    [SqlFunction(FillRowMethodName = "FillRow")]  
    public static IEnumerable InitMethod(String logname)  
    {  
        return new EventLog(logname).Entries;    }  
  
    public static void FillRow(Object obj, out SqlDateTime timeWritten, out SqlChars message, out SqlChars category, out long instanceId)  
    {  
        EventLogEntry eventLogEntry = (EventLogEntry)obj;  
        timeWritten = new SqlDateTime(eventLogEntry.TimeWritten);  
        message = new SqlChars(eventLogEntry.Message);  
        category = new SqlChars(eventLogEntry.Category);  
        instanceId = eventLogEntry.InstanceId;  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data.Sql  
Imports Microsoft.SqlServer.Server  
Imports System.Collections  
Imports System.Data.SqlTypes  
Imports System.Diagnostics  
Imports System.Runtime.InteropServices  
  
Public Class TabularEventLog  
    <SqlFunction(FillRowMethodName:="FillRow")> _  
    Public Shared Function InitMethod(ByVal logname As String) As IEnumerable  
        Return New EventLog(logname).Entries  
    End Function  
  
    Public Shared Sub FillRow(ByVal obj As Object, <Out()> ByRef timeWritten As SqlDateTime, <Out()> ByRef message As SqlChars, <Out()> ByRef category As SqlChars, <Out()> ByRef instanceId As Long)  
        Dim eventLogEnTry As EventLogEntry = CType(obj, EventLogEntry)  
        timeWritten = New SqlDateTime(eventLogEnTry.TimeWritten)  
        message = New SqlChars(eventLogEnTry.Message)  
        category = New SqlChars(eventLogEnTry.Category)  
        instanceId = eventLogEnTry.InstanceId  
    End Sub  
End Class  
```  
  
###### <a name="declaring-and-using-the-sample-table-valued-function"></a><span data-ttu-id="e4311-152">サンプルのテーブル値関数の宣言と使用</span><span class="sxs-lookup"><span data-stu-id="e4311-152">Declaring and Using the Sample Table-Valued Function</span></span>  
 <span data-ttu-id="e4311-153">コンパイルしたサンプルのテーブル値関数は、次のように [!INCLUDE[tsql](../../includes/tsql-md.md)] で宣言できます。</span><span class="sxs-lookup"><span data-stu-id="e4311-153">After the sample table-valued function has been compiled, it can be declared in [!INCLUDE[tsql](../../includes/tsql-md.md)] like this:</span></span>  
  
```  
use master;  
-- Replace SQL_Server_logon with your SQL Server user credentials.  
GRANT EXTERNAL ACCESS ASSEMBLY TO [SQL_Server_logon];   
-- Modify the following line to specify a different database.  
ALTER DATABASE master SET TRUSTWORTHY ON;  
  
-- Modify the next line to use the appropriate database.  
CREATE ASSEMBLY tvfEventLog   
FROM 'D:\assemblies\tvfEventLog\tvfeventlog.dll'   
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
GO  
CREATE FUNCTION ReadEventLog(@logname nvarchar(100))  
RETURNS TABLE   
(logTime datetime,Message nvarchar(4000),Category nvarchar(4000),InstanceId bigint)  
AS   
EXTERNAL NAME tvfEventLog.TabularEventLog.InitMethod;  
GO  
```  
  
 <span data-ttu-id="e4311-154">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] では、/clr:pure を指定してコンパイルした Visual C++ のデータベース オブジェクトは実行できません。</span><span class="sxs-lookup"><span data-stu-id="e4311-154">Visual C++ database objects compiled with /clr:pure are not supported for execution on [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="e4311-155">このようなデータベース オブジェクトには、テーブル値関数などがあります。</span><span class="sxs-lookup"><span data-stu-id="e4311-155">For example, such database objects include table-valued functions.</span></span>  
  
 <span data-ttu-id="e4311-156">サンプルをテストするには、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="e4311-156">To test the sample, try the following [!INCLUDE[tsql](../../includes/tsql-md.md)] code:</span></span>  
  
```  
-- Select the top 100 events,  
SELECT TOP 100 *  
FROM dbo.ReadEventLog(N'Security') as T;  
go  
  
-- Select the last 10 login events.  
SELECT TOP 10 T.logTime, T.Message, T.InstanceId   
FROM dbo.ReadEventLog(N'Security') as T  
WHERE T.Category = N'Logon/Logoff';  
go  
```  
  
## <a name="sample-returning-the-results-of-a-sql-server-query"></a><span data-ttu-id="e4311-157">サンプル: SQL Server クエリの結果を返す</span><span class="sxs-lookup"><span data-stu-id="e4311-157">Sample: Returning the Results of a SQL Server Query</span></span>  
 <span data-ttu-id="e4311-158">次の例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに対してクエリを実行するテーブル値関数を示します。</span><span class="sxs-lookup"><span data-stu-id="e4311-158">The following sample shows a table-valued function that queries a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="e4311-159">この例では、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] の AdventureWorks Light データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="e4311-159">This sample uses the AdventureWorks Light database from [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span> <span data-ttu-id="e4311-160">[https://www.codeplex.com/sqlserversamples](https://go.microsoft.com/fwlink/?LinkId=87843)AdventureWorks のダウンロードの詳細については、「」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4311-160">See [https://www.codeplex.com/sqlserversamples](https://go.microsoft.com/fwlink/?LinkId=87843) for more information on downloading AdventureWorks.</span></span>  
  
 <span data-ttu-id="e4311-161">ソース コード ファイルに FindInvalidEmails.cs または FindInvalidEmails.vb という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="e4311-161">Name your source code file FindInvalidEmails.cs or FindInvalidEmails.vb.</span></span>  
  
```csharp  
using System;  
using System.Collections;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
  
using Microsoft.SqlServer.Server;  
  
public partial class UserDefinedFunctions {  
   private class EmailResult {  
      public SqlInt32 CustomerId;  
      public SqlString EmailAdress;  
  
      public EmailResult(SqlInt32 customerId, SqlString emailAdress) {  
         CustomerId = customerId;  
         EmailAdress = emailAdress;  
      }  
   }  
  
   public static bool ValidateEmail(SqlString emailAddress) {  
      if (emailAddress.IsNull)  
         return false;  
  
      if (!emailAddress.Value.EndsWith("@adventure-works.com"))  
         return false;  
  
      // Validate the address. Put any more rules here.  
      return true;  
   }  
  
   [SqlFunction(  
       DataAccess = DataAccessKind.Read,  
       FillRowMethodName = "FindInvalidEmails_FillRow",  
       TableDefinition="CustomerId int, EmailAddress nvarchar(4000)")]  
   public static IEnumerable FindInvalidEmails(SqlDateTime modifiedSince) {  
      ArrayList resultCollection = new ArrayList();  
  
      using (SqlConnection connection = new SqlConnection("context connection=true")) {  
         connection.Open();  
  
         using (SqlCommand selectEmails = new SqlCommand(  
             "SELECT " +  
             "[CustomerID], [EmailAddress] " +  
             "FROM [AdventureWorksLT2008].[SalesLT].[Customer] " +  
             "WHERE [ModifiedDate] >= @modifiedSince",  
             connection)) {  
            SqlParameter modifiedSinceParam = selectEmails.Parameters.Add(  
                "@modifiedSince",  
                SqlDbType.DateTime);  
            modifiedSinceParam.Value = modifiedSince;  
  
            using (SqlDataReader emailsReader = selectEmails.ExecuteReader()) {  
               while (emailsReader.Read()) {  
                  SqlString emailAddress = emailsReader.GetSqlString(1);  
                  if (ValidateEmail(emailAddress)) {  
                     resultCollection.Add(new EmailResult(  
                         emailsReader.GetSqlInt32(0),  
                         emailAddress));  
                  }  
               }  
            }  
         }  
      }  
  
      return resultCollection;  
   }  
  
   public static void FindInvalidEmails_FillRow(  
       object emailResultObj,  
       out SqlInt32 customerId,  
       out SqlString emailAdress) {  
      EmailResult emailResult = (EmailResult)emailResultObj;  
  
      customerId = emailResult.CustomerId;  
      emailAdress = emailResult.EmailAdress;  
   }  
};  
```  
  
```vb  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Public Partial Class UserDefinedFunctions  
   Private Class EmailResult  
      Public CustomerId As SqlInt32  
      Public EmailAdress As SqlString  
  
      Public Sub New(customerId__1 As SqlInt32, emailAdress__2 As SqlString)  
         CustomerId = customerId__1  
         EmailAdress = emailAdress__2  
      End Sub  
   End Class  
  
   Public Shared Function ValidateEmail(emailAddress As SqlString) As Boolean  
      If emailAddress.IsNull Then  
         Return False  
      End If  
  
      If Not emailAddress.Value.EndsWith("@adventure-works.com") Then  
         Return False  
      End If  
  
      ' Validate the address. Put any more rules here.  
      Return True  
   End Function  
  
   <SqlFunction(DataAccess := DataAccessKind.Read, FillRowMethodName := "FindInvalidEmails_FillRow", TableDefinition := "CustomerId int, EmailAddress nvarchar(4000)")> _  
   Public Shared Function FindInvalidEmails(modifiedSince As SqlDateTime) As IEnumerable  
      Dim resultCollection As New ArrayList()  
  
      Using connection As New SqlConnection("context connection=true")  
         connection.Open()  
  
         Using selectEmails As New SqlCommand("SELECT " & "[CustomerID], [EmailAddress] " & "FROM [AdventureWorksLT2008].[SalesLT].[Customer] " & "WHERE [ModifiedDate] >= @modifiedSince", connection)  
            Dim modifiedSinceParam As SqlParameter = selectEmails.Parameters.Add("@modifiedSince", SqlDbType.DateTime)  
            modifiedSinceParam.Value = modifiedSince  
  
            Using emailsReader As SqlDataReader = selectEmails.ExecuteReader()  
               While emailsReader.Read()  
                  Dim emailAddress As SqlString = emailsReader.GetSqlString(1)  
                  If ValidateEmail(emailAddress) Then  
                     resultCollection.Add(New EmailResult(emailsReader.GetSqlInt32(0), emailAddress))  
                  End If  
               End While  
            End Using  
         End Using  
      End Using  
  
      Return resultCollection  
   End Function  
  
   Public Shared Sub FindInvalidEmails_FillRow(emailResultObj As Object, ByRef customerId As SqlInt32, ByRef emailAdress As SqlString)  
      Dim emailResult As EmailResult = DirectCast(emailResultObj, EmailResult)  
  
      customerId = emailResult.CustomerId  
      emailAdress = emailResult.EmailAdress  
   End Sub  
End ClassImports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Public Partial Class UserDefinedFunctions  
   Private Class EmailResult  
      Public CustomerId As SqlInt32  
      Public EmailAdress As SqlString  
  
      Public Sub New(customerId__1 As SqlInt32, emailAdress__2 As SqlString)  
         CustomerId = customerId__1  
         EmailAdress = emailAdress__2  
      End Sub  
   End Class  
  
   Public Shared Function ValidateEmail(emailAddress As SqlString) As Boolean  
      If emailAddress.IsNull Then  
         Return False  
      End If  
  
      If Not emailAddress.Value.EndsWith("@adventure-works.com") Then  
         Return False  
      End If  
  
      ' Validate the address. Put any more rules here.  
      Return True  
   End Function  
  
   <SqlFunction(DataAccess := DataAccessKind.Read, FillRowMethodName := "FindInvalidEmails_FillRow", TableDefinition := "CustomerId int, EmailAddress nvarchar(4000)")> _  
   Public Shared Function FindInvalidEmails(modifiedSince As SqlDateTime) As IEnumerable  
      Dim resultCollection As New ArrayList()  
  
      Using connection As New SqlConnection("context connection=true")  
         connection.Open()  
  
         Using selectEmails As New SqlCommand("SELECT " & "[CustomerID], [EmailAddress] " & "FROM [AdventureWorksLT2008].[SalesLT].[Customer] " & "WHERE [ModifiedDate] >= @modifiedSince", connection)  
            Dim modifiedSinceParam As SqlParameter = selectEmails.Parameters.Add("@modifiedSince", SqlDbType.DateTime)  
            modifiedSinceParam.Value = modifiedSince  
  
            Using emailsReader As SqlDataReader = selectEmails.ExecuteReader()  
               While emailsReader.Read()  
                  Dim emailAddress As SqlString = emailsReader.GetSqlString(1)  
                  If ValidateEmail(emailAddress) Then  
                     resultCollection.Add(New EmailResult(emailsReader.GetSqlInt32(0), emailAddress))  
                  End If  
               End While  
            End Using  
         End Using  
      End Using  
  
      Return resultCollection  
   End Function  
  
   Public Shared Sub FindInvalidEmails_FillRow(emailResultObj As Object, customerId As SqlInt32, emailAdress As SqlString)  
      Dim emailResult As EmailResult = DirectCast(emailResultObj, EmailResult)  
  
      customerId = emailResult.CustomerId  
      emailAdress = emailResult.EmailAdress  
   End Sub  
End Class  
```  
  
 <span data-ttu-id="e4311-162">ソース コードをコンパイルして DLL を生成し、DLL を C ドライブのルート ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="e4311-162">Compile the source code to a DLL and copy the DLL to the root directory of your C drive.</span></span>  <span data-ttu-id="e4311-163">その後、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="e4311-163">Then, execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] query.</span></span>  
  
```  
use AdventureWorksLT2008;  
go  
  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'FindInvalidEmails')  
   DROP FUNCTION FindInvalidEmails;  
go  
  
IF EXISTS (SELECT name FROM sys.assemblies WHERE name = 'MyClrCode')  
   DROP ASSEMBLY MyClrCode;  
go  
  
CREATE ASSEMBLY MyClrCode FROM 'C:\FindInvalidEmails.dll'  
WITH PERMISSION_SET = SAFE -- EXTERNAL_ACCESS;  
GO  
  
CREATE FUNCTION FindInvalidEmails(@ModifiedSince datetime)   
RETURNS TABLE (  
   CustomerId int,  
   EmailAddress nvarchar(4000)  
)  
AS EXTERNAL NAME MyClrCode.UserDefinedFunctions.[FindInvalidEmails];  
go  
  
SELECT * FROM FindInvalidEmails('2000-01-01');  
go  
```  
  
