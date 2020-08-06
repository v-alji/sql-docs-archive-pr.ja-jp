---
title: 現在のトランザクションへのアクセス |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- current transaction access
- Current property
- Transaction class
ms.assetid: 1a4e2ce5-f627-4c81-8960-6a9968cefda2
author: rothja
ms.author: jroth
ms.openlocfilehash: 34b7e67d30cb9d89a02eb918fcd03651b2915955
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742302"
---
# <a name="accessing-the-current-transaction"></a><span data-ttu-id="b58e3-102">現在のトランザクションへのアクセス</span><span class="sxs-lookup"><span data-stu-id="b58e3-102">Accessing the Current Transaction</span></span>
  <span data-ttu-id="b58e3-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で実行されている CLR (共通言語ランタイム) コードに実行が移った時点でトランザクションがアクティブな場合、`System.Transactions.Transaction` クラスによりそのトランザクションが公開されます。</span><span class="sxs-lookup"><span data-stu-id="b58e3-103">If a transaction is active at the point at which common language runtime (CLR) code running on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is entered, the transaction is exposed through the `System.Transactions.Transaction` class.</span></span> <span data-ttu-id="b58e3-104">現在のトランザクションにアクセスするには、`Transaction.Current` プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="b58e3-104">The `Transaction.Current` property is used to access the current transaction.</span></span> <span data-ttu-id="b58e3-105">ほとんどの場合、トランザクションに明示的にアクセスする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b58e3-105">In most cases it is not necessary to access the transaction explicitly.</span></span> <span data-ttu-id="b58e3-106">データベース接続の場合、`Transaction.Current` メソッドが呼び出されると、ADO.NET が `Connection.Open` を自動的にチェックし、ユーザーに意識させることなく接続をそのトランザクションに参加させます (接続文字列の `Enlist` キーワードを false に設定した場合は除く)。</span><span class="sxs-lookup"><span data-stu-id="b58e3-106">For database connections, ADO.NET checks `Transaction.Current` automatically when the `Connection.Open` method is called, and transparently enlists the connection in that transaction (unless the `Enlist` keyword is set to false in the connection string).</span></span>  
  
 <span data-ttu-id="b58e3-107">次のようなシナリオでは、`Transaction` オブジェクトを直接使用できます。</span><span class="sxs-lookup"><span data-stu-id="b58e3-107">You might want to use the `Transaction` object directly in the following scenarios:</span></span>  
  
-   <span data-ttu-id="b58e3-108">自動参加が行われないリソースや、何かの理由で初期化中に参加しなかったリソースを参加させる場合。</span><span class="sxs-lookup"><span data-stu-id="b58e3-108">If you want to enlist a resource that does not do automatic enlistment, or that for some reason was not enlisted during initialization.</span></span>  
  
-   <span data-ttu-id="b58e3-109">リソースを明示的にトランザクションに参加させる場合。</span><span class="sxs-lookup"><span data-stu-id="b58e3-109">If you want to explicitly enlist a resource in the transaction.</span></span>  
  
-   <span data-ttu-id="b58e3-110">ストアド プロシージャまたは関数内から外部トランザクションを終了させる場合。</span><span class="sxs-lookup"><span data-stu-id="b58e3-110">If you want to terminate the external transaction from within your stored procedure or function.</span></span> <span data-ttu-id="b58e3-111">この場合は、<xref:System.Transactions.TransactionScope> を使用します。</span><span class="sxs-lookup"><span data-stu-id="b58e3-111">In this case, you use <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="b58e3-112">たとえば、次のコードでは、現在のトランザクションがロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="b58e3-112">For example, the following code will rollback the current transaction:</span></span>  
  
    ```  
    using(TransactionScope transactionScope = new TransactionScope(TransactionScopeOptions.Required)) { }  
    ```  
  
 <span data-ttu-id="b58e3-113">以下に、外部トランザクションを取り消す別の方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="b58e3-113">The rest of this topic describes other ways to cancel an external transaction.</span></span>  
  
## <a name="canceling-an-external-transaction"></a><span data-ttu-id="b58e3-114">外部トランザクションのキャンセル</span><span class="sxs-lookup"><span data-stu-id="b58e3-114">Canceling an External Transaction</span></span>  
 <span data-ttu-id="b58e3-115">外部トランザクションは、次の方法でマネージド プロシージャまたは関数からキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="b58e3-115">You can cancel external transactions from a managed procedure or function in the following ways:</span></span>  
  
-   <span data-ttu-id="b58e3-116">マネージド プロシージャまたは関数は、出力パラメーターを使用して値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="b58e3-116">The managed procedure or function can return a value by using an output parameter.</span></span> <span data-ttu-id="b58e3-117">呼び出し元の [!INCLUDE[tsql](../../includes/tsql-md.md)] プロシージャは、戻り値を確認して、必要に応じて `ROLLBACK TRANSACTION` を実行できます。</span><span class="sxs-lookup"><span data-stu-id="b58e3-117">The calling [!INCLUDE[tsql](../../includes/tsql-md.md)] procedure can check the returned value and, if appropriate, execute `ROLLBACK TRANSACTION`.</span></span>  
  
-   <span data-ttu-id="b58e3-118">マネージド プロシージャまたは関数は、カスタムの例外をスローできます。</span><span class="sxs-lookup"><span data-stu-id="b58e3-118">The managed procedure or function can throw a custom exception.</span></span> <span data-ttu-id="b58e3-119">呼び出し元のプロシージャは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] try/catch ブロックでマネージプロシージャまたは関数によってスローされた例外をキャッチし、を実行でき `ROLLBACK TRANSACTION` ます。</span><span class="sxs-lookup"><span data-stu-id="b58e3-119">The calling [!INCLUDE[tsql](../../includes/tsql-md.md)] procedure can catch the exception thrown by the managed procedure or function in a try/catch block and execute `ROLLBACK TRANSACTION`.</span></span>  
  
-   <span data-ttu-id="b58e3-120">マネージド プロシージャまたは関数は、特定の条件が満たされた場合に `Transaction.Rollback` メソッドを呼び出して、現在のトランザクションをキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="b58e3-120">The managed procedure or function can cancel the current transaction by calling the `Transaction.Rollback` method if a certain condition is met.</span></span>  
  
 <span data-ttu-id="b58e3-121">マネージド プロシージャまたは関数の内部から呼び出された場合、`Transaction.Rollback` メソッドは不明確なエラー メッセージを表示して例外をスローします。これは try/catch ブロックでラップできます。</span><span class="sxs-lookup"><span data-stu-id="b58e3-121">When it is called within a managed procedure or function, the `Transaction.Rollback` method throws an exception with an ambiguous error message and can be wrapped in a try/catch block.</span></span> <span data-ttu-id="b58e3-122">表示されるエラー メッセージは、たとえば次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b58e3-122">The error message thresembles similar to the following:</span></span>  
  
```  
Msg 3994, Level 16, State 1, Procedure uspRollbackFromProc, Line 0  
Transaction is not allowed to roll back inside a user defined routine, trigger or aggregate because the transaction is not started in that CLR level. Change application logic to enforce strict transaction nesting.  
```  
  
 <span data-ttu-id="b58e3-123">この例外は想定されるものであり、コードの実行を継続するには try/catch ブロックが必要です。</span><span class="sxs-lookup"><span data-stu-id="b58e3-123">This exception is expected and the try/catch block is necessary for code execution to continue.</span></span> <span data-ttu-id="b58e3-124">try/catch ブロックがない場合、例外はすぐに呼び出し元の [!INCLUDE[tsql](../../includes/tsql-md.md)] プロシージャにスローされ、マネージド コードの実行は終了します。</span><span class="sxs-lookup"><span data-stu-id="b58e3-124">Without the try/catch block, the exception will be immediately thrown to the calling [!INCLUDE[tsql](../../includes/tsql-md.md)] procedure and managed code execution will finish.</span></span> <span data-ttu-id="b58e3-125">マネージド コードが実行を終了すると、別の例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="b58e3-125">When the managed code finishes execution, another exception is raised:</span></span>  
  
```  
Msg 3991, Level 16, State 1, Procedure uspRollbackFromProc, Line 1   
The context transaction which was active before entering user defined routine, trigger or aggregate " uspRollbackFromProc " has been ended inside of it, which is not allowed. Change application logic to enforce strict transaction nesting. The statement has been terminated.  
```  
  
 <span data-ttu-id="b58e3-126">この例外も想定されるもので、実行を継続するには、トリガーを起動するアクションを実行する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでの try/catch ブロックが必要です。</span><span class="sxs-lookup"><span data-stu-id="b58e3-126">This exception is also expected, and for execution to continue, you must have a try/catch block around the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that performs the action that fires the trigger.</span></span> <span data-ttu-id="b58e3-127">この 2 つの例外がスローされますが、トランザクションはロールバックされ、変更はコミットされません。</span><span class="sxs-lookup"><span data-stu-id="b58e3-127">Despite the two exceptions thrown, the transaction is rolled back and the changes are not committed.</span></span>  
  
### <a name="example"></a><span data-ttu-id="b58e3-128">例</span><span class="sxs-lookup"><span data-stu-id="b58e3-128">Example</span></span>  
 <span data-ttu-id="b58e3-129">次の例では、`Transaction.Rollback` メソッドを使用してマネージド プロシージャからトランザクションをロールバックします。</span><span class="sxs-lookup"><span data-stu-id="b58e3-129">The following is an example of a transaction being rolled back from a managed procedure by using the `Transaction.Rollback` method.</span></span> <span data-ttu-id="b58e3-130">マネージド コード内にある `Transaction.Rollback` メソッドの前後の try/catch ブロックに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b58e3-130">Notice the try/catch block around the `Transaction.Rollback` method in the managed code.</span></span> <span data-ttu-id="b58e3-131">[!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトは、アセンブリおよびマネージド ストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="b58e3-131">The [!INCLUDE[tsql](../../includes/tsql-md.md)] script creates an assembly and managed stored procedure.</span></span> <span data-ttu-id="b58e3-132">`EXEC uspRollbackFromProc`ステートメントが try/catch ブロックにラップされていることに注意してください。これにより、マネージプロシージャの実行が終了したときにスローされる例外がキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="b58e3-132">Be aware that the `EXEC uspRollbackFromProc` statement is wrapped in a try/catch block, so that the exception thrown when the managed procedure completes execution is caught.</span></span>  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
using System.Transactions;  
  
public partial class StoredProcedures  
{  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void uspRollbackFromProc()  
{  
   using (SqlConnection connection = new SqlConnection(@"context connection=true"))  
   {  
      // Open the connection.  
      connection.Open();  
  
      bool successCondition = true;  
  
      // Success condition is met.  
      if (successCondition)  
      {  
         SqlContext.Pipe.Send("Success condition met in procedure.");   
         // Perform other actions here.  
      }  
  
      //  Success condition is not met, the transaction will be rolled back.  
      else  
      {  
         SqlContext.Pipe.Send("Success condition not met in managed procedure. Transaction rolling back...");  
         try  
         {  
               // Get the current transaction and roll it back.  
               Transaction trans = Transaction.Current;  
               trans.Rollback();  
         }  
         catch (SqlException ex)  
         {  
            // Catch the expected exception.   
            // This allows the connection to close correctly.                      
         }    
      }  
  
      // Close the connection.  
      connection.Close();  
   }  
}  
};  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Transactions  
  
Partial Public Class StoredProcedures  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub  uspRollbackFromProc ()  
   Using connection As New SqlConnection("context connection=true")  
  
   ' Open the connection.  
   connection.Open()  
  
   Dim successCondition As Boolean  
   successCondition = False  
  
   ' Success condition is met.  
   If successCondition Then  
  
      SqlContext.Pipe.Send("Success condition met in procedure.")  
  
      ' Success condition is not met, the transaction will be rolled back.  
  
   Else  
      SqlContext.Pipe.Send("Success condition not met in managed procedure. Transaction rolling back...")  
      Try  
         ' Get the current transaction and roll it back.  
         Dim trans As Transaction  
         trans = Transaction.Current  
         trans.Rollback()  
  
      Catch ex As SqlException  
         ' Catch the exception instead of throwing it.    
         ' This allows the connection to close correctly.                      
      End Try  
  
   End If  
  
   ' Close the connection.  
   connection.Close()  
  
End Using  
End Sub  
End Class  
```  
  
 <span data-ttu-id="b58e3-133">**Transact-SQL**</span><span class="sxs-lookup"><span data-stu-id="b58e3-133">**Transact-SQL**</span></span>  
  
```  
--Register assembly.  
CREATE ASSEMBLY TestProcs FROM 'C:\Programming\TestProcs.dll'   
Go  
CREATE PROCEDURE uspRollbackFromProc AS EXTERNAL NAME TestProcs.StoredProcedures.uspRollbackFromProc  
Go  
  
-- Execute procedure.  
BEGIN TRY  
BEGIN TRANSACTION   
-- Perform other actions.  
Exec uspRollbackFromProc  
-- Perform other actions.  
PRINT N'Commiting transaction...'  
COMMIT TRANSACTION  
END TRY  
  
BEGIN CATCH  
SELECT ERROR_NUMBER() AS ErrorNum, ERROR_MESSAGE() AS ErrorMessage  
PRINT N'Exception thrown, rolling back transaction.'  
ROLLBACK TRANSACTION  
PRINT N'Transaction rolled back.'   
END CATCH  
Go  
  
-- Clean up.  
DROP Procedure uspRollbackFromProc;  
Go  
DROP ASSEMBLY TestProcs;  
Go  
```  
  
## <a name="see-also"></a><span data-ttu-id="b58e3-134">参照</span><span class="sxs-lookup"><span data-stu-id="b58e3-134">See Also</span></span>  
 [<span data-ttu-id="b58e3-135">CLR 統合とトランザクション</span><span class="sxs-lookup"><span data-stu-id="b58e3-135">CLR Integration and Transactions</span></span>](../native-client-ole-db-transactions/transactions.md)  
  
  
