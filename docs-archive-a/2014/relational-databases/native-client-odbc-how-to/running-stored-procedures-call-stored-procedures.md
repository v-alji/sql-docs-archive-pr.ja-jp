---
title: ストアドプロシージャの呼び出し (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], calling
ms.assetid: 31176be8-d40e-4f93-8d44-a46e804a3e2d
author: rothja
ms.author: jroth
ms.openlocfilehash: d98d623dbbb4701bb59c95df502d0063d528d0d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640899"
---
# <a name="call-stored-procedures-odbc"></a><span data-ttu-id="6334e-102">ストアド プロシージャの呼び出し (ODBC)</span><span class="sxs-lookup"><span data-stu-id="6334e-102">Call Stored Procedures (ODBC)</span></span>
  <span data-ttu-id="6334e-103">SQL ステートメントで ODBC CALL エスケープ句を使用してストアドプロシージャを呼び出すと、Microsoft SQL Server ドライバーは、リモートストアドプロシージャコール (RPC) メカニズムを使用して SQL Server にプロシージャを送信します。</span><span class="sxs-lookup"><span data-stu-id="6334e-103">When a SQL statement calls a stored procedure using the ODBC CALL escape clause, the Microsoft SQL Server driver sends the procedure to SQL Server using the remote stored procedure call (RPC) mechanism.</span></span> <span data-ttu-id="6334e-104">RPC 要求は、SQL Server でのステートメント解析やパラメーター処理の多くを省略するため、Transact-SQL の EXECUTE ステートメントを使用するよりも高速です。</span><span class="sxs-lookup"><span data-stu-id="6334e-104">RPC requests bypass much of the statement parsing and parameter processing in SQL Server and are faster than using the Transact-SQL EXECUTE statement.</span></span>  
  
 <span data-ttu-id="6334e-105">この機能を示すサンプルアプリケーションについては、「[リターンコードを処理する」および「ODBC&#41;&#40;出力パラメーター ](running-stored-procedures-process-return-codes-and-output-parameters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6334e-105">For a sample application that demonstrates this feature, see [Process Return Codes and Output Parameters &#40;ODBC&#41;](running-stored-procedures-process-return-codes-and-output-parameters.md).</span></span>  
  
### <a name="to-run-a-procedure-as-an-rpc"></a><span data-ttu-id="6334e-106">プロシージャを RPC として実行するには</span><span class="sxs-lookup"><span data-stu-id="6334e-106">To run a procedure as an RPC</span></span>  
  
1.  <span data-ttu-id="6334e-107">ODBC CALL エスケープ シーケンスを使用する SQL ステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="6334e-107">Construct a SQL statement that uses the ODBC CALL escape sequence.</span></span> <span data-ttu-id="6334e-108">このステートメントでは、各入力、入出力、出力パラメーター、およびプロシージャの戻り値 (存在する場合) に対してパラメーター マーカーを使用します。</span><span class="sxs-lookup"><span data-stu-id="6334e-108">The statement uses parameter markers for each input, input/output, and output parameter, and for the procedure return value (if any):</span></span>  
  
    ```  
    {? = CALL procname (?,?)}  
    ```  
  
2.  <span data-ttu-id="6334e-109">各入力、入出力、出力パラメーター、およびプロシージャの戻り値 (存在する場合) に対して[SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6334e-109">Call [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) for each input, input/output, and output parameter, and for the procedure return value (if any).</span></span>  
  
3.  <span data-ttu-id="6334e-110">[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)を使用してステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="6334e-110">Execute the statement with [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6334e-111">アプリケーションでプロシージャの送信に (ODBC CALL エスケープ シーケンスではなく) Transact-SQL の EXECUTE 構文を使用した場合、プロシージャ コールは、SQL Server ODBC ドライバーから SQL Server に、RPC ではなく SQL ステートメントとして渡されます。</span><span class="sxs-lookup"><span data-stu-id="6334e-111">If an application submits a procedure using the Transact-SQL EXECUTE syntax (as opposed to the ODBC CALL escape sequence), the SQL Server ODBC driver passes the procedure call to SQL Server as a SQL statement rather than as an RPC.</span></span> <span data-ttu-id="6334e-112">また、Transact-SQL の EXECUTE ステートメントを使用した場合、出力パラメーターは返されません。</span><span class="sxs-lookup"><span data-stu-id="6334e-112">Also, output parameters are not returned if the Transact-SQL EXECUTE statement is used.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6334e-113">参照</span><span class="sxs-lookup"><span data-stu-id="6334e-113">See Also</span></span>  
 <span data-ttu-id="6334e-114">[ストアドプロシージャの実行方法に関するトピック &#40;ODBC&#41;](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="6334e-114">[Running Stored Procedures How-to Topics &#40;ODBC&#41;](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md) </span></span>  
 <span data-ttu-id="6334e-115">[ストアドプロシージャ呼び出しのバッチ処理](../native-client-odbc-stored-procedures/batching-stored-procedure-calls.md) </span><span class="sxs-lookup"><span data-stu-id="6334e-115">[Batching Stored Procedure Calls](../native-client-odbc-stored-procedures/batching-stored-procedure-calls.md) </span></span>  
 <span data-ttu-id="6334e-116">[ストアドプロシージャの実行](../native-client-odbc-stored-procedures/running-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="6334e-116">[Running Stored Procedures](../native-client-odbc-stored-procedures/running-stored-procedures.md) </span></span>  
 <span data-ttu-id="6334e-117">[ストアドプロシージャの呼び出し](../native-client-odbc-stored-procedures/calling-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="6334e-117">[Calling a Stored Procedure](../native-client-odbc-stored-procedures/calling-a-stored-procedure.md) </span></span>  
 [<span data-ttu-id="6334e-118">手順</span><span class="sxs-lookup"><span data-stu-id="6334e-118">Procedures</span></span>](../native-client-odbc-queries/executing-statements/procedures.md)  
  
  
