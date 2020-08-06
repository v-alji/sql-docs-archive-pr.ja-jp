---
title: CLR ストアドプロシージャ |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- database objects [CLR integration], stored procedures
- stored procedures [CLR integration]
- common language runtime [SQL Server], stored procedures
- building database objects [CLR integration], stored procedures
- output parameters [CLR integration]
- tabular results
ms.assetid: bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f8c69435e28bfa67c72e26b7a54e419cd91ef220
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634000"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="8542b-102">CLR ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="8542b-102">CLR Stored Procedures</span></span>
  <span data-ttu-id="8542b-103">ストアド プロシージャは、スカラー式では使用できないルーチンです。</span><span class="sxs-lookup"><span data-stu-id="8542b-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="8542b-104">ストアド プロシージャはスカラー関数とは異なり、表形式の結果やメッセージをクライアントに返す操作、DDL (データ定義言語) ステートメントや DML (データ操作言語) ステートメントを呼び出す操作、出力パラメーターを返す操作が行えます。</span><span class="sxs-lookup"><span data-stu-id="8542b-104">Unlike scalar functions, they can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span> <span data-ttu-id="8542b-105">CLR 統合の利点とマネージコードとの使い分けの詳細については [!INCLUDE[tsql](../../includes/tsql-md.md)] 、「 [clr 統合の概要](../../relational-databases/clr-integration/clr-integration-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8542b-105">For information about the advantages of CLR integration and choosing between managed code and [!INCLUDE[tsql](../../includes/tsql-md.md)], see [Overview of CLR Integration](../../relational-databases/clr-integration/clr-integration-overview.md).</span></span>  
  
## <a name="requirements-for-clr-stored-procedures"></a><span data-ttu-id="8542b-106">CLR ストアド プロシージャの要件</span><span class="sxs-lookup"><span data-stu-id="8542b-106">Requirements for CLR Stored Procedures</span></span>  
 <span data-ttu-id="8542b-107">共通言語ランタイム (CLR) では、ストアドプロシージャは、アセンブリ内のクラスのパブリック静的メソッドとして実装され [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="8542b-107">In the common language runtime (CLR), stored procedures are implemented as public static methods on a class in a [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] assembly.</span></span> <span data-ttu-id="8542b-108">この静的メソッドは、void として宣言することも、整数値を返すようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8542b-108">The static method can either be declared as void, or return an integer value.</span></span> <span data-ttu-id="8542b-109">整数値を返す場合は、その整数値はストアド プロシージャからのリターン コードとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="8542b-109">If it returns an integer value, the integer returned is treated as the return code from the procedure.</span></span> <span data-ttu-id="8542b-110">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8542b-110">For example:</span></span>  
  
 `EXECUTE @return_status = procedure_name`  
  
 <span data-ttu-id="8542b-111">@return_status変数には、メソッドによって返される値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8542b-111">The @return_status variable will contain the value returned by the method.</span></span> <span data-ttu-id="8542b-112">このメソッドを void として宣言した場合は、リターン コードは 0 になります。</span><span class="sxs-lookup"><span data-stu-id="8542b-112">If the method is declared void, the return code is 0.</span></span>  
  
 <span data-ttu-id="8542b-113">パラメーターを受け取るメソッドの場合、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 実装のパラメーター数は、このストアド プロシージャの [!INCLUDE[tsql](../../includes/tsql-md.md)] 宣言で使用したパラメーター数と同じにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8542b-113">If the method takes parameters, the number of parameters in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] implementation should be the same as the number of parameters used in the [!INCLUDE[tsql](../../includes/tsql-md.md)] declaration of the stored procedure.</span></span>  
  
 <span data-ttu-id="8542b-114">CLR ストアド プロシージャに渡すパラメーターには、マネージド コード内に同等のパラメーターを持つネイティブの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 型であればどの型でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="8542b-114">Parameters passed to a CLR stored procedure can be any of the native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types that have an equivalent in managed code.</span></span> <span data-ttu-id="8542b-115">プロシージャを作成する [!INCLUDE[tsql](../../includes/tsql-md.md)] 構文では、これらの型には最も適切なネイティブ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と同等の型を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8542b-115">For the [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax to create the procedure, these types should be specified with the most appropriate native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type equivalent.</span></span> <span data-ttu-id="8542b-116">型変換の詳細については、「 [CLR パラメーターデータのマッピング](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8542b-116">For more information about type conversions, see [Mapping CLR Parameter Data](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).</span></span>  
  
### <a name="table-valued-parameters"></a><span data-ttu-id="8542b-117">テーブル値パラメーター</span><span class="sxs-lookup"><span data-stu-id="8542b-117">Table-Valued Parameters</span></span>  
 <span data-ttu-id="8542b-118">テーブル値パラメーター (TVP) とは、プロシージャや関数に渡されるユーザー定義のテーブル型です。TVP を使用すると、複数行のデータを効率的にサーバーに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="8542b-118">Table-valued parameters (TVPs), user-defined table types that are passed into a procedure or function, provide an efficient way to pass multiple rows of data to the server.</span></span> <span data-ttu-id="8542b-119">TVP の機能はパラメーター配列に似ていますが、より柔軟性が高く、[!INCLUDE[tsql](../../includes/tsql-md.md)] との統合も緊密です。</span><span class="sxs-lookup"><span data-stu-id="8542b-119">TVPs provide similar functionality to parameter arrays, but offer greater flexibility and closer integration with [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="8542b-120">テーブル値パラメーターを使用するとパフォーマンスが向上する可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="8542b-120">They also provide the potential for better performance.</span></span> <span data-ttu-id="8542b-121">また、サーバーへのラウンド トリップを減らすのにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8542b-121">TVPs also help reduce the number of round trips to the server.</span></span> <span data-ttu-id="8542b-122">スカラー パラメーターのリストを使用するなどしてサーバーに複数の要求を送信する代わりに、データを TVP としてサーバーに送信できます。</span><span class="sxs-lookup"><span data-stu-id="8542b-122">Instead of sending multiple requests to the server, such as with a list of scalar parameters, data can be sent to the server as a TVP.</span></span> <span data-ttu-id="8542b-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のプロセスで実行されているマネージド ストアド プロシージャやマネージド関数にユーザー定義のテーブル型をテーブル値パラメーターとして渡したり、戻り値として受け取ったりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="8542b-123">A user-defined table type cannot be passed as a table-valued parameter to, or be returned from, a managed stored procedure or function executing in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span> <span data-ttu-id="8542b-124">Tvp の詳細については、「[データベースエンジン&#41;&#40;テーブル値パラメーターの使用](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8542b-124">For more information about TVPs, see [Use Table-Valued Parameters &#40;Database Engine&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).</span></span>  
  
## <a name="returning-results-from-clr-stored-procedures"></a><span data-ttu-id="8542b-125">CLR ストアド プロシージャから結果を返す</span><span class="sxs-lookup"><span data-stu-id="8542b-125">Returning Results from CLR Stored Procedures</span></span>  
 <span data-ttu-id="8542b-126">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ストアド プロシージャからの情報はいくつかの形式で返すことができます。</span><span class="sxs-lookup"><span data-stu-id="8542b-126">Information may be returned from [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] stored procedures in several ways.</span></span> <span data-ttu-id="8542b-127">出力パラメーター、表形式の結果、およびメッセージの形式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8542b-127">This includes output parameters, tabular results, and messages.</span></span>  
  
### <a name="output-parameters-and-clr-stored-procedures"></a><span data-ttu-id="8542b-128">OUTPUT パラメーターと CLR ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="8542b-128">OUTPUT Parameters and CLR Stored Procedures</span></span>  
 <span data-ttu-id="8542b-129">[!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャと同様に、OUTPUT パラメーターを使用して [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ストアド プロシージャから情報を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="8542b-129">As with [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures, information may be returned from [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] stored procedures using OUTPUT parameters.</span></span> <span data-ttu-id="8542b-130">[!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャの作成に使用する [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] DML 構文は、[!INCLUDE[tsql](../../includes/tsql-md.md)] で記述されたストアド プロシージャの作成に使用する構文と同じです。</span><span class="sxs-lookup"><span data-stu-id="8542b-130">The [!INCLUDE[tsql](../../includes/tsql-md.md)] DML syntax used for creating [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] stored procedures is the same as that used for creating stored procedures written in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="8542b-131">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] クラスの実装コードの対応するパラメーターは、引数として参照渡しのパラメーターを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8542b-131">The corresponding parameter in the implementation code in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] class should use a pass-by-reference parameter as the argument.</span></span> <span data-ttu-id="8542b-132">Visual Basic では、C# と同じように出力パラメーターがサポートされないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8542b-132">Note that Visual Basic does not support output parameters in the same way that C# does.</span></span> <span data-ttu-id="8542b-133">次に示すように、パラメーターを参照によって指定し、属性を適用し \<Out()> て出力パラメーターを表す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8542b-133">You must specify the parameter by reference and apply the \<Out()> attribute to represent an OUTPUT parameter, as in the following:</span></span>  
  
```vb
Imports System.Runtime.InteropServices  
...  
Public Shared Sub PriceSum ( <Out()> ByRef value As SqlInt32)  
```  
  
 <span data-ttu-id="8542b-134">OUTPUT パラメーターを使用して情報を返すストアド プロシージャを次に示します。</span><span class="sxs-lookup"><span data-stu-id="8542b-134">The following shows a stored procedure returning information through an OUTPUT parameter:</span></span>  
  
```csharp  
using System;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void PriceSum(out SqlInt32 value)  
   {  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         value = 0;  
         connection.Open();  
         SqlCommand command = new SqlCommand("SELECT Price FROM Products", connection);  
         SqlDataReader reader = command.ExecuteReader();  
  
         using (reader)  
         {  
            while( reader.Read() )  
            {  
               value += reader.GetSqlInt32(0);  
            }  
         }           
      }  
   }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
Imports System.Runtime.InteropServices  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Executes a query and iterates over the results to perform a summation.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub PriceSum( <Out()> ByRef value As SqlInt32)  
  
        Using connection As New SqlConnection("context connection=true")  
           value = 0  
           Connection.Open()  
           Dim command As New SqlCommand("SELECT Price FROM Products", connection)  
           Dim reader As SqlDataReader  
           reader = command.ExecuteReader()  
  
           Using reader  
              While reader.Read()  
                 value += reader.GetSqlInt32(0)  
              End While  
           End Using  
        End Using          
    End Sub  
End Class  
```  
  
 <span data-ttu-id="8542b-135">上記の CLR ストアドプロシージャを含むアセンブリがサーバー上に構築され、作成されたら、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ように使用してデータベースでプロシージャを作成し、 *SUM*を OUTPUT パラメーターとして指定します。</span><span class="sxs-lookup"><span data-stu-id="8542b-135">Once the assembly containing the above CLR stored procedure has been built and created on the server, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] is used to create the procedure in the database, and specifies *sum* as an OUTPUT parameter.</span></span>  
  
```sql
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
-- if StoredProcedures class was inside a namespace, called MyNS,  
-- you would use:  
-- AS EXTERNAL NAME TestStoredProc.[MyNS.StoredProcedures].PriceSum  
```  
  
 <span data-ttu-id="8542b-136">*Sum*が SQL Server データ型として宣言され、 `int` clr ストアドプロシージャで定義されている*値*パラメーターが clr データ型として指定されていることに注意して `SqlInt32` ください。</span><span class="sxs-lookup"><span data-stu-id="8542b-136">Note that *sum* is declared as an `int` SQL Server data type, and that the *value* parameter defined in the CLR stored procedure is specified as a `SqlInt32` CLR data type.</span></span> <span data-ttu-id="8542b-137">呼び出し元のプログラムが CLR ストアドプロシージャを実行すると、に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] よって自動的に `SqlInt32` clr データ型がデータ型に変換され `int` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="8542b-137">When a calling program executes the CLR stored procedure, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] automatically converts the `SqlInt32` CLR data type to an `int`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>  <span data-ttu-id="8542b-138">変換できる CLR データ型と変換できない CLR データ型の詳細については、「 [Clr パラメーターデータのマッピング](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8542b-138">For more information about which CLR data types can and cannot be converted, see [Mapping CLR Parameter Data](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).</span></span>  
  
### <a name="returning-tabular-results-and-messages"></a><span data-ttu-id="8542b-139">表形式の結果とメッセージを返す</span><span class="sxs-lookup"><span data-stu-id="8542b-139">Returning Tabular Results and Messages</span></span>  
 <span data-ttu-id="8542b-140">表形式の結果とメッセージは、`SqlPipe` クラスの `Pipe` プロパティを使用して取得した `SqlContext` オブジェクトを使用してクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="8542b-140">Returning tabular results and messages to the client is done through the `SqlPipe` object, which is obtained by using the `Pipe` property of the `SqlContext` class.</span></span> <span data-ttu-id="8542b-141">`SqlPipe` オブジェクトには `Send` メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="8542b-141">The `SqlPipe` object has a `Send` method.</span></span> <span data-ttu-id="8542b-142">`Send` メソッドを呼び出すことにより、パイプ経由で呼び出し側のアプリケーションにデータを送信できます。</span><span class="sxs-lookup"><span data-stu-id="8542b-142">By calling the `Send` method, you can transmit data through the pipe to the calling application.</span></span>  
  
 <span data-ttu-id="8542b-143">次に示すのは、`SqlPipe.Send` を送信したり、単純にテキスト文字列を送信するために使用する、`SqlDataReader` メソッドのオーバーロードです。</span><span class="sxs-lookup"><span data-stu-id="8542b-143">These are several overloads of the `SqlPipe.Send` method, including one that sends a `SqlDataReader` and another that simply sends a text string.</span></span>  
  
###### <a name="returning-messages"></a><span data-ttu-id="8542b-144">メッセージを返す</span><span class="sxs-lookup"><span data-stu-id="8542b-144">Returning Messages</span></span>  
 <span data-ttu-id="8542b-145">`SqlPipe.Send(string)` はクライアント アプリケーションへのメッセージの送信に使用します。</span><span class="sxs-lookup"><span data-stu-id="8542b-145">Use `SqlPipe.Send(string)` to send messages to the client application.</span></span> <span data-ttu-id="8542b-146">メッセージのテキストの上限は 8,000 文字です。</span><span class="sxs-lookup"><span data-stu-id="8542b-146">The text of the message is limited to 8000 characters.</span></span> <span data-ttu-id="8542b-147">メッセージが 8,000 文字を超えると、そのメッセージは切り詰められます。</span><span class="sxs-lookup"><span data-stu-id="8542b-147">If the message exceeds 8000 characters, it will be truncated.</span></span>  
  
###### <a name="returning-tabular-results"></a><span data-ttu-id="8542b-148">表形式の結果を返す</span><span class="sxs-lookup"><span data-stu-id="8542b-148">Returning Tabular Results</span></span>  
 <span data-ttu-id="8542b-149">クエリの結果を直接クライアントに送信するには、`Execute` オブジェクトの `SqlPipe` メソッドのいずれかのオーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="8542b-149">To send the results of a query directly to the client, use one of the overloads of the `Execute` method on the `SqlPipe` object.</span></span> <span data-ttu-id="8542b-150">マネージド メモリにコピーされることなくデータがネットワーク バッファーに転送されるので、これはクライアントに結果を返す最も効率的な方法です。</span><span class="sxs-lookup"><span data-stu-id="8542b-150">This is the most efficient way to return results to the client, since the data is transferred to the network buffers without being copied into managed memory.</span></span> <span data-ttu-id="8542b-151">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8542b-151">For example:</span></span>  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Execute a command and send the results to the client directly.  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void ExecuteToClient()  
   {  
   using(SqlConnection connection = new SqlConnection("context connection=true"))   
   {  
      connection.Open();  
      SqlCommand command = new SqlCommand("select @@version", connection);  
      SqlContext.Pipe.ExecuteAndSend(command);  
      }  
   }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub ExecuteToClient()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            SqlContext.Pipe.ExecuteAndSend(command)  
        End Using  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="8542b-152">インプロセス プロバイダーによりそれ以前に実行されたクエリの結果を送信するには (または `SqlDataReader` のカスタム実装を使用して事前処理するには)、`Send` メソッドの `SqlDataReader` を受け取るオーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="8542b-152">To send the results of a query that was executed previously through the in-process provider (or to pre-process the data using a custom implementation of `SqlDataReader`), use the overload of the `Send` method that takes a `SqlDataReader`.</span></span> <span data-ttu-id="8542b-153">このメソッドは、前述の直接的なメソッドより少し動作が遅くなりますが、クライアントにデータを送信する前に、きわめて柔軟にデータを操作できます。</span><span class="sxs-lookup"><span data-stu-id="8542b-153">This method is slightly slower than the direct method described previously, but it offers greater flexibility to manipulate the data before it is sent to the client.</span></span>  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Execute a command and send the resulting reader to the client  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void SendReaderToClient()  
   {  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         connection.Open();  
         SqlCommand command = new SqlCommand("select @@version", connection);  
         SqlDataReader r = command.ExecuteReader();  
         SqlContext.Pipe.Send(r);  
      }  
   }  
}  
```  
 
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub SendReaderToClient()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            Dim reader As SqlDataReader  
            reader = command.ExecuteReader()  
            SqlContext.Pipe.Send(reader)  
        End Using  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="8542b-154">動的な結果セットを作成し、それにデータを設定してクライアントに送信するには、現在の接続からのレコードを作成し、`SqlPipe.Send` を使用してそれらを送信できます。</span><span class="sxs-lookup"><span data-stu-id="8542b-154">To create a dynamic result set, populate it and send it to the client, you can create records from the current connection and send them using `SqlPipe.Send`.</span></span>  
  
```csharp  
using System.Data;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
using System.Data.SqlTypes;  
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Create a result set on the fly and send it to the client.  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void SendTransientResultSet()  
   {  
      // Create a record object that represents an individual row, including it's metadata.  
      SqlDataRecord record = new SqlDataRecord(new SqlMetaData("stringcol", SqlDbType.NVarChar, 128));  
  
      // Populate the record.  
      record.SetSqlString(0, "Hello World!");  
  
      // Send the record to the client.  
      SqlContext.Pipe.Send(record);  
   }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Create a result set on the fly and send it to the client.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub SendTransientResultSet()  
        ' Create a record object that represents an individual row, including it's metadata.  
        Dim record As New SqlDataRecord(New SqlMetaData("stringcol", SqlDbType.NVarChar, 128) )  
  
        ' Populate the record.  
        record.SetSqlString(0, "Hello World!")  
  
        ' Send the record to the client.  
        SqlContext.Pipe.Send(record)          
    End Sub  
End Class   
```  
  
 <span data-ttu-id="8542b-155">次に、表形式の結果とメッセージを `SqlPipe` を使用して送信する例を示します。</span><span class="sxs-lookup"><span data-stu-id="8542b-155">Here is an example of sending a tabular result and a message through `SqlPipe`.</span></span>  
  
```csharp  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void HelloWorld()  
   {  
      SqlContext.Pipe.Send("Hello world! It's now " + System.DateTime.Now.ToString()+"\n");  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         connection.Open();  
         SqlCommand command = new SqlCommand("SELECT ProductNumber FROM ProductMaster", connection);  
         SqlDataReader reader = command.ExecuteReader();  
         SqlContext.Pipe.Send(reader);  
      }  
   }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub HelloWorld()  
        SqlContext.Pipe.Send("Hello world! It's now " & System.DateTime.Now.ToString() & "\n")  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT ProductNumber FROM ProductMaster", connection)  
            Dim reader As SqlDataReader  
            reader = command.ExecuteReader()  
            SqlContext.Pipe.Send(reader)  
        End Using  
    End Sub  
End Class   
```  
  
 <span data-ttu-id="8542b-156">最初の `Send` はクライアントにメッセージを送信し、2 番目は `SqlDataReader` を使用して表形式の結果を送信しています。</span><span class="sxs-lookup"><span data-stu-id="8542b-156">The first `Send` sends a message to the client, while the second sends a tabular result using `SqlDataReader`.</span></span>  
  
 <span data-ttu-id="8542b-157">これらの例は、説明のみの目的でここに記載しています。</span><span class="sxs-lookup"><span data-stu-id="8542b-157">Note that these examples are for illustrative purposes only.</span></span> <span data-ttu-id="8542b-158">計算を集中的に行うアプリケーションには、実際には単純な [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントよりも CLR 関数の方が適しています。</span><span class="sxs-lookup"><span data-stu-id="8542b-158">CLR functions are more appropriate than simple [!INCLUDE[tsql](../../includes/tsql-md.md)] statements for computation-intensive applications.</span></span> <span data-ttu-id="8542b-159">上の例とほぼ同等の [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャを次に示します。</span><span class="sxs-lookup"><span data-stu-id="8542b-159">An almost equivalent [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure to the previous example is:</span></span>  
  
```sql
CREATE PROCEDURE HelloWorld() AS  
BEGIN  
PRINT('Hello world!')  
SELECT ProductNumber FROM ProductMaster  
END;  
```  
  
> [!NOTE]  
>  <span data-ttu-id="8542b-160">メッセージと結果セットはクライアント アプリケーションで個別に取得されます。</span><span class="sxs-lookup"><span data-stu-id="8542b-160">Messages and result sets are retrieved differently in the client application.</span></span> <span data-ttu-id="8542b-161">たとえば、結果 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] セットは [**結果**] ビューに表示され、メッセージは [**メッセージ**] ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8542b-161">For instance, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] result sets appear in the **Results** view, and messages appear in the **Messages** pane.</span></span>  
  
 <span data-ttu-id="8542b-162">上の Visual C# コードをファイル MyFirstUdp.cs に保存した場合、次のようにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="8542b-162">If the above Visual C# code is saved in a file MyFirstUdp.cs and compiled with:</span></span>  
  
```console
csc /t:library /out:MyFirstUdp.dll MyFirstUdp.cs   
```  
  
 <span data-ttu-id="8542b-163">上の Visual Basic コードをファイル MyFirstUdp.vb に保存した場合、次のようにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="8542b-163">Or, if the above Visual Basic code is saved in a file MyFirstUdp.vb and compiled with:</span></span>  
  
```console
vbc /t:library /out:MyFirstUdp.dll MyFirstUdp.vb   
```  
  
> [!NOTE]  
>  <span data-ttu-id="8542b-164">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降では、`/clr:pure` を指定してコンパイルした Visual C++ のデータベース オブジェクト (ストアド プロシージャなど) は実行できません。</span><span class="sxs-lookup"><span data-stu-id="8542b-164">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], Visual C++ database objects (such as stored procedures) compiled with `/clr:pure` are not supported for execution.</span></span>  
  
 <span data-ttu-id="8542b-165">生成されるアセンブリは登録でき、次の DDL を使用してエントリ ポイントを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8542b-165">The resulting assembly can be registered, and the entry point invoked, with the following DDL:</span></span>  
  
```sql
CREATE ASSEMBLY MyFirstUdp FROM 'C:\Programming\MyFirstUdp.dll';  
CREATE PROCEDURE HelloWorld  
AS EXTERNAL NAME MyFirstUdp.StoredProcedures.HelloWorld;  
EXEC HelloWorld;  
```  
  
## <a name="see-also"></a><span data-ttu-id="8542b-166">参照</span><span class="sxs-lookup"><span data-stu-id="8542b-166">See Also</span></span>  
 <span data-ttu-id="8542b-167">[CLR ユーザー定義関数](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md) </span><span class="sxs-lookup"><span data-stu-id="8542b-167">[CLR User-Defined Functions](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md) </span></span>  
 <span data-ttu-id="8542b-168">[CLR ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) </span><span class="sxs-lookup"><span data-stu-id="8542b-168">[CLR User-Defined Types](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) </span></span>  
 [<span data-ttu-id="8542b-169">CLR トリガー</span><span class="sxs-lookup"><span data-stu-id="8542b-169">CLR Triggers</span></span>](../../../2014/database-engine/dev-guide/clr-triggers.md)  
  
  
