---
title: SqlPipe オブジェクト |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- custom result sets [CLR integration]
- SqlPipe object
- tabular results
ms.assetid: 3e090faf-085f-4c01-a565-79e3f1c36e3b
author: rothja
ms.author: jroth
ms.openlocfilehash: 0044815a0b20d72b48b87bfe8f693d7196aaeaf3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642128"
---
# <a name="sqlpipe-object"></a><span data-ttu-id="66f31-102">SqlPipe オブジェクト</span><span class="sxs-lookup"><span data-stu-id="66f31-102">SqlPipe Object</span></span>
  <span data-ttu-id="66f31-103">以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、結果や出力パラメーターを呼び出し側のクライアントに送信するストアド プロシージャ (または拡張ストアド プロシージャ) を作成することがごく一般的でした。</span><span class="sxs-lookup"><span data-stu-id="66f31-103">In previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it is very common to write a stored procedure (or an extended stored procedure) that sends results or output parameters to the calling client.</span></span>  
  
 <span data-ttu-id="66f31-104">[!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャでは、0 行以上の行を返す `SELECT` ステートメントはすべて、接続している呼び出し側の "パイプ" に結果を送信します。</span><span class="sxs-lookup"><span data-stu-id="66f31-104">In a [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, any `SELECT` statement that returns zero or more rows sends the results to the connected caller's "pipe."</span></span>  
  
 <span data-ttu-id="66f31-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で実行されている CLR (共通言語ランタイム) データベース オブジェクトの場合は、`Send` オブジェクトの `SqlPipe` メソッドを使用して、接続しているパイプに結果を送信できます。</span><span class="sxs-lookup"><span data-stu-id="66f31-105">For common language runtime (CLR) database objects running in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can send results to the connected pipe using the `Send` methods of the `SqlPipe` object.</span></span> <span data-ttu-id="66f31-106">`Pipe` オブジェクトを取得するには、`SqlContext` オブジェクトの `SqlPipe` プロパティにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="66f31-106">Access the `Pipe` property of the `SqlContext` object to obtain the `SqlPipe` object.</span></span> <span data-ttu-id="66f31-107">`SqlPipe` クラスは、概念的には ASP.NET の `Response` クラスに似ています。</span><span class="sxs-lookup"><span data-stu-id="66f31-107">The `SqlPipe` class is conceptually similar to the `Response` class found in ASP.NET.</span></span> <span data-ttu-id="66f31-108">詳細については、.NET Framework Software Development Kit の SqlPipe クラスのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="66f31-108">For more information, see the SqlPipe Class reference documentation in the .NET Framework software development kit.</span></span>  
  
## <a name="returning-tabular-results-and-messages"></a><span data-ttu-id="66f31-109">表形式の結果とメッセージを返す</span><span class="sxs-lookup"><span data-stu-id="66f31-109">Returning Tabular Results and Messages</span></span>  
 <span data-ttu-id="66f31-110">`SqlPipe` には、3 つのオーバーロードを持つ `Send` メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="66f31-110">The `SqlPipe` has a `Send` method, which has three overloads.</span></span> <span data-ttu-id="66f31-111">これらは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="66f31-111">They are:</span></span>  
  
-   `void Send(string message)`  
  
-   `void Send(SqlDataReader reader)`  
  
-   `void Send(SqlDataRecord record)`  
  
 <span data-ttu-id="66f31-112">`Send` メソッドでは、データがそのままクライアントまたは呼び出し元に送信されます。</span><span class="sxs-lookup"><span data-stu-id="66f31-112">The `Send` method sends data straight to the client or caller.</span></span> <span data-ttu-id="66f31-113">通常、`SqlPipe` の出力を使用するのはクライアントですが、入れ子になった CLR ストアド プロシージャの場合、ストアド プロシージャが出力のコンシューマーになる可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="66f31-113">It is usually the client that consumes the output from the `SqlPipe`, but in the case of nested CLR stored procedures the output consumer can also be a stored procedure.</span></span> <span data-ttu-id="66f31-114">たとえば、Procedure1 がコマンド テキスト "EXEC Procedure2" の SqlCommand.ExecuteReader() を呼び出すとします。</span><span class="sxs-lookup"><span data-stu-id="66f31-114">For example, Procedure1 calls SqlCommand.ExecuteReader() with the command text "EXEC Procedure2".</span></span> <span data-ttu-id="66f31-115">Procedure2 もマネージド ストアド プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="66f31-115">Procedure2 is also a managed stored procedure.</span></span> <span data-ttu-id="66f31-116">ここで Procedure2 が SqlPipe.Send( SqlDataRecord ) を呼び出すと、行はクライアントではなく、Procedure1 のリーダーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="66f31-116">If Procedure2 now calls SqlPipe.Send( SqlDataRecord ), the row is sent to Procedure1's reader, not the client.</span></span>  
  
 <span data-ttu-id="66f31-117">`Send` メソッドは、クライアントで情報メッセージとして表示される文字列メッセージを送信します。これは、[!INCLUDE[tsql](../../includes/tsql-md.md)] の PRINT と同等です。</span><span class="sxs-lookup"><span data-stu-id="66f31-117">The `Send` method sends a string message that appears on the client as an information message, equivalent to PRINT in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="66f31-118">また、`SqlDataRecord` を使用して単一行の結果セットを送信することも、`SqlDataReader` を使用して複数行の結果セットを送信することもできます。</span><span class="sxs-lookup"><span data-stu-id="66f31-118">It can also send a single-row result-set using `SqlDataRecord`, or a multi-row result-set using a `SqlDataReader`.</span></span>  
  
 <span data-ttu-id="66f31-119">`SqlPipe` オブジェクトには、`ExecuteAndSend` メソッドもあります。</span><span class="sxs-lookup"><span data-stu-id="66f31-119">The `SqlPipe` object also has an `ExecuteAndSend` method.</span></span> <span data-ttu-id="66f31-120">このメソッドは、(`SqlCommand` オブジェクトで渡された) コマンドを実行し、その結果を直接呼び出し側に返送するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="66f31-120">This method can be used to execute a command (passed as a `SqlCommand` object) and send results directly back to the caller.</span></span> <span data-ttu-id="66f31-121">送信されたコマンドにエラーがある場合、パイプに例外が送信されますが、呼び出し元のマネージド コードにもコピーが送信されます。</span><span class="sxs-lookup"><span data-stu-id="66f31-121">If there are errors in the command that was submitted, exceptions are sent to the pipe, but a copy is also sent to calling managed code.</span></span> <span data-ttu-id="66f31-122">呼び出し元コードが例外をキャッチしない場合は、履歴を伝わり [!INCLUDE[tsql](../../includes/tsql-md.md)] コードに反映され、2 度出力に表示されます。</span><span class="sxs-lookup"><span data-stu-id="66f31-122">If the calling code does not catch the exception, it propagates up the stack to the [!INCLUDE[tsql](../../includes/tsql-md.md)] code and appears in the output twice.</span></span> <span data-ttu-id="66f31-123">呼び出し元コードが例外をキャッチした場合、パイプ コンシューマーにはまだエラーが表示されますが、重複するエラーはありません。</span><span class="sxs-lookup"><span data-stu-id="66f31-123">If the calling code does catch the exception, the pipe consumer still sees the error, but there is not a duplicate error.</span></span>  
  
 <span data-ttu-id="66f31-124">このメソッドは、コンテキスト接続に関連付けられた `SqlCommand` だけを受け取ります。コンテキスト接続以外に関連付けられたコマンドを受け取ることはできません。</span><span class="sxs-lookup"><span data-stu-id="66f31-124">It can only take a `SqlCommand` that is associated with the context connection; it cannot take a command that is associated with the non-context connection.</span></span>  
  
## <a name="returning-custom-result-sets"></a><span data-ttu-id="66f31-125">カスタム結果セットを返す</span><span class="sxs-lookup"><span data-stu-id="66f31-125">Returning Custom Result Sets</span></span>  
 <span data-ttu-id="66f31-126">マネージド ストアド プロシージャでは、`SqlDataReader` 以外からの結果セットを送信できます。</span><span class="sxs-lookup"><span data-stu-id="66f31-126">Managed stored procedures can send result sets that do not come from a `SqlDataReader`.</span></span> <span data-ttu-id="66f31-127">`SendResultsStart` メソッドでは、`SendResultsRow` や `SendResultsEnd` と同様に、ストアド プロシージャからクライアントにカスタム結果セットを送信できます。</span><span class="sxs-lookup"><span data-stu-id="66f31-127">The `SendResultsStart` method, along with `SendResultsRow` and `SendResultsEnd`, allows stored procedures to send custom result sets to the client.</span></span>  
  
 <span data-ttu-id="66f31-128">`SendResultsStart` は、`SqlDataRecord` を入力として受け取ります。</span><span class="sxs-lookup"><span data-stu-id="66f31-128">`SendResultsStart` takes a `SqlDataRecord` as an input.</span></span> <span data-ttu-id="66f31-129">さらに、結果セットの先頭にマークを付け、レコード メタデータを使用して、結果セットを説明するメタデータを生成します。</span><span class="sxs-lookup"><span data-stu-id="66f31-129">It marks the beginning of a result set and uses the record metadata to construct the metadata that describes the result set.</span></span> <span data-ttu-id="66f31-130">`SendResultsStart` を使ってレコードの値が送信されることはありません。</span><span class="sxs-lookup"><span data-stu-id="66f31-130">It does not send the value of the record with `SendResultsStart`.</span></span> <span data-ttu-id="66f31-131">以降、`SendResultsRow` を使用して送信されるすべての行は、そのメタデータ定義に一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66f31-131">All the subsequent rows, sent using `SendResultsRow`, must match that metadata definition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="66f31-132">`SendResultsStart` メソッドを呼び出した後に呼び出せるのは、`SendResultsRow` と `SendResultsEnd` のみです。</span><span class="sxs-lookup"><span data-stu-id="66f31-132">After calling the `SendResultsStart` method only `SendResultsRow` and `SendResultsEnd` can be called.</span></span> <span data-ttu-id="66f31-133">`SqlPipe` の同じインスタンスで他のどのメソッドを呼び出しても、`InvalidOperationException` が発生することになります。</span><span class="sxs-lookup"><span data-stu-id="66f31-133">Calling any other method in the same instance of `SqlPipe` causes an `InvalidOperationException`.</span></span> <span data-ttu-id="66f31-134">`SendResultsEnd` は、`SqlPipe` を初期状態に戻し、他のメソッドを呼び出せるようにします。</span><span class="sxs-lookup"><span data-stu-id="66f31-134">`SendResultsEnd` sets `SqlPipe` back to the initial state in which other methods can be called.</span></span>  
  
### <a name="example"></a><span data-ttu-id="66f31-135">例</span><span class="sxs-lookup"><span data-stu-id="66f31-135">Example</span></span>  
 <span data-ttu-id="66f31-136">`uspGetProductLine` ストアド プロシージャは、指定した製品ライン内のすべての製品の名前、製品番号、色、および表示価格を返します。</span><span class="sxs-lookup"><span data-stu-id="66f31-136">The `uspGetProductLine` stored procedure returns the name, product number, color, and list price of all products within a specified product line.</span></span> <span data-ttu-id="66f31-137">このストアドプロシージャは、 *prodLine*と完全に一致するものを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="66f31-137">This stored procedure accepts exact matches for *prodLine*.</span></span>  
  
 <span data-ttu-id="66f31-138">C#</span><span class="sxs-lookup"><span data-stu-id="66f31-138">C#</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
  
public partial class StoredProcedures  
{  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void uspGetProductLine(SqlString prodLine)  
{  
    // Connect through the context connection.  
    using (SqlConnection connection = new SqlConnection("context connection=true"))  
    {  
        connection.Open();  
  
        SqlCommand command = new SqlCommand(  
            "SELECT Name, ProductNumber, Color, ListPrice " +  
            "FROM Production.Product " +   
            "WHERE ProductLine = @prodLine;", connection);  
  
        command.Parameters.AddWithValue("@prodLine", prodLine);  
  
        try  
        {  
            // Execute the command and send the results to the caller.  
            SqlContext.Pipe.ExecuteAndSend(command);  
        }  
        catch (System.Data.SqlClient.SqlException ex)  
        {  
            // An error occurred executing the SQL command.  
        }  
     }  
}  
};  
```  
  
 <span data-ttu-id="66f31-139">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="66f31-139">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Partial Public Class StoredProcedures  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub uspGetProductLine(ByVal prodLine As SqlString)  
    Dim command As SqlCommand  
  
    ' Connect through the context connection.  
    Using connection As New SqlConnection("context connection=true")  
        connection.Open()  
  
        command = New SqlCommand( _  
        "SELECT Name, ProductNumber, Color, ListPrice " & _  
        "FROM Production.Product " & _  
        "WHERE ProductLine = @prodLine;", connection)  
        command.Parameters.AddWithValue("@prodLine", prodLine)  
  
        Try  
            ' Execute the command and send the results   
            ' directly to the caller.  
            SqlContext.Pipe.ExecuteAndSend(command)  
        Catch ex As System.Data.SqlClient.SqlException  
            ' An error occurred executing the SQL command.  
        End Try  
    End Using  
End Sub  
End Class  
```  
  
 <span data-ttu-id="66f31-140">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントは、ツーリング自転車製品の一覧を返す `uspGetProduct` プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="66f31-140">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement executes the `uspGetProduct` procedure, which returns a list of touring bike products.</span></span>  
  
```  
EXEC uspGetProductLineVB 'T';  
```  
  
## <a name="see-also"></a><span data-ttu-id="66f31-141">参照</span><span class="sxs-lookup"><span data-stu-id="66f31-141">See Also</span></span>  
 <span data-ttu-id="66f31-142">[SqlDataRecord オブジェクト](sqldatarecord-object.md) </span><span class="sxs-lookup"><span data-stu-id="66f31-142">[SqlDataRecord Object](sqldatarecord-object.md) </span></span>  
 <span data-ttu-id="66f31-143">[CLR ストアドプロシージャ](../../database-engine/dev-guide/clr-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="66f31-143">[CLR Stored Procedures](../../database-engine/dev-guide/clr-stored-procedures.md) </span></span>  
 [<span data-ttu-id="66f31-144">ADO.NET に対する SQL Server インプロセス固有の拡張機能</span><span class="sxs-lookup"><span data-stu-id="66f31-144">SQL Server In-Process Specific Extensions to ADO.NET</span></span>](sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
