---
title: Messages | を生成するステートメントの処理Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- PRINT statement
- messages [ODBC], statements generating messages
- statements [ODBC], message generation
- errors [ODBC], statements generating messages
- SQL Server Native Client ODBC driver, errors
- STATISTICS IO option
- STATISTICS TIME option
- DBCC statements
- SQLExecute function
- RAISERROR statement
- SQLGetDiagRec function
- ODBC error handling, statements generating messages
- SQLExecDirect function
ms.assetid: 672ebdc5-7fa1-4ceb-8d52-fd25ef646654
author: rothja
ms.author: jroth
ms.openlocfilehash: c26376eabb756d356dd71fb3bd8284a6b11dced7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714338"
---
# <a name="processing-statements-that-generate-messages"></a><span data-ttu-id="c4519-102">メッセージを生成するステートメントの処理</span><span class="sxs-lookup"><span data-stu-id="c4519-102">Processing Statements That Generate Messages</span></span>
  <span data-ttu-id="c4519-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] SET ステートメントのオプション STATISTICS TIME と STATISTICS IO は、実行時間の長いクエリの診断に利用できる情報を取得する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="c4519-103">The [!INCLUDE[tsql](../../includes/tsql-md.md)] SET statement options STATISTICS TIME and STATISTICS IO are used to get information that aids in diagnosing long-running queries.</span></span> <span data-ttu-id="c4519-104">以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、クエリ プランを分析するための SHOWPLAN オプションもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c4519-104">Earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] also support the SHOWPLAN option for analyzing query plans.</span></span> <span data-ttu-id="c4519-105">ODBC アプリケーションでは、次のステートメントを実行してこれらのオプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="c4519-105">An ODBC application can set these options by executing the following statements:</span></span>  
  
```  
SQLExecDirect(hstmt, "SET SHOWPLAN ON", SQL_NTS);  
SQLExecDirect(hstmt, "SET STATISTICS TIME ON", SQL_NTS90  
);  
SQLExecDirect(hstmt, "SET STATISTICS IO ON", SQL_NTS);  
```  
  
 <span data-ttu-id="c4519-106">SET STATISTICS TIME または SET SHOWPLAN を ON に設定すると、 **Sqlexecute**と**SQLExecDirect** return SQL_SUCCESS_WITH_INFO が返されます。その時点で、アプリケーションは SQL_NO_DATA を返すまで**SQLGETDIAGREC**を呼び出して、SHOWPLAN または STATISTICS TIME の出力を取得できます。</span><span class="sxs-lookup"><span data-stu-id="c4519-106">When SET STATISTICS TIME or SET SHOWPLAN are ON, **SQLExecute** and **SQLExecDirect** return SQL_SUCCESS_WITH_INFO, and, at that point, the application can retrieve the SHOWPLAN or STATISTICS TIME output by calling **SQLGetDiagRec** until it returns SQL_NO_DATA.</span></span> <span data-ttu-id="c4519-107">SHOWPLAN データの各行は、次の形式で返されます。</span><span class="sxs-lookup"><span data-stu-id="c4519-107">Each line of SHOWPLAN data comes back in the format:</span></span>  
  
```  
szSqlState="01000", *pfNativeError=6223,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]   
              Table Scan"  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c4519-108">Version 7.0 では、SHOWPLAN オプションが SHOWPLAN_ALL オプションと SHOWPLAN_TEXT オプションに置き換えられました。これらの両方のオプションでは、一連のメッセージではなく、結果セットとして出力が返されます。</span><span class="sxs-lookup"><span data-stu-id="c4519-108">version 7.0 replaced the SHOWPLAN option with SHOWPLAN_ALL and SHOWPLAN_TEXT, both of which return output as a result set, not a set of messages.</span></span>  
  
 <span data-ttu-id="c4519-109">STATISTICS TIME の各行は、次の形式で返されます。</span><span class="sxs-lookup"><span data-stu-id="c4519-109">Each line of STATISTICS TIME comes back in the format:</span></span>  
  
```  
szSqlState="01000", *pfNativeError= 3613,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
   SQL Server Parse and Compile Time: cpu time = 0 ms."  
```  
  
 <span data-ttu-id="c4519-110">SET STATISTICS IO の出力は、結果セットの最後に到達するまで使用できません。</span><span class="sxs-lookup"><span data-stu-id="c4519-110">The output of SET STATISTICS IO is not available until the end of a result set.</span></span> <span data-ttu-id="c4519-111">統計 IO 出力を取得するために、アプリケーションは、 **Sqlfetch**または[sqlfetchscroll](../native-client-odbc-api/sqlfetchscroll.md)が SQL_NO_DATA を返す時点で**SQLGetDiagRec**を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c4519-111">To get STATISTICS IO output, the application calls **SQLGetDiagRec** at the time **SQLFetch** or [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md) returns SQL_NO_DATA.</span></span> <span data-ttu-id="c4519-112">STATISTICS IO の出力は、次の形式で返されます。</span><span class="sxs-lookup"><span data-stu-id="c4519-112">The output of STATISTICS IO comes back in the format:</span></span>  
  
```  
szSqlState="01000", *pfNativeError= 3615,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Table: testshow  scan count 1,  logical reads: 1,  
   physical reads: 0."  
```  
  
## <a name="using-dbcc-statements"></a><span data-ttu-id="c4519-113">DBCC ステートメントの使用</span><span class="sxs-lookup"><span data-stu-id="c4519-113">Using DBCC Statements</span></span>  
 <span data-ttu-id="c4519-114">DBCC ステートメントは、結果セットではなく、メッセージとしてデータを返します。</span><span class="sxs-lookup"><span data-stu-id="c4519-114">DBCC statements return their data as messages, not result sets.</span></span> <span data-ttu-id="c4519-115">**SQLExecDirect**または**sqlexecute**は SQL_SUCCESS_WITH_INFO を返し、SQL_NO_DATA を返すまで、アプリケーションは**SQLGetDiagRec**を呼び出して出力を取得します。</span><span class="sxs-lookup"><span data-stu-id="c4519-115">**SQLExecDirect** or **SQLExecute** return SQL_SUCCESS_WITH_INFO, and the application retrieves the output by calling **SQLGetDiagRec** until it returns SQL_NO_DATA.</span></span>  
  
 <span data-ttu-id="c4519-116">たとえば、次のステートメントでは SQL_SUCCESS_WITH_INFO が返されます。</span><span class="sxs-lookup"><span data-stu-id="c4519-116">For example, the following statement returns SQL_SUCCESS_WITH_INFO:</span></span>  
  
```  
SQLExecDirect(hstmt, "DBCC CHECKTABLE(Authors)", SQL_NTS);  
```  
  
 <span data-ttu-id="c4519-117">**SQLGetDiagRec**を呼び出すと、次のように戻ります。</span><span class="sxs-lookup"><span data-stu-id="c4519-117">Calls to **SQLGetDiagRec** return:</span></span>  
  
```  
szSqlState = "01000", *pfNativeError = 2536,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Checking authors"  
szSqlState = "01000", *pfNativeError = 2579,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   The total number of data pages in this table is 1."  
szSqlState = "01000", *pfNativeError = 7929,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Table has 23 data rows."  
szSqlState = "01000", *pfNativeError = 2528  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   DBCC execution completed. If DBCC printed error messages,  
   see your System Administrator."  
```  
  
## <a name="using-print-and-raiserror-statements"></a><span data-ttu-id="c4519-118">PRINT ステートメントと RAISERROR ステートメントの使用</span><span class="sxs-lookup"><span data-stu-id="c4519-118">Using PRINT and RAISERROR Statements</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]<span data-ttu-id="c4519-119">PRINT ステートメントと RAISERROR ステートメントでは、 **SQLGetDiagRec**を呼び出すことによってもデータが返されます。</span><span class="sxs-lookup"><span data-stu-id="c4519-119">PRINT and RAISERROR statements also return data by calling **SQLGetDiagRec**.</span></span> <span data-ttu-id="c4519-120">PRINT ステートメントを実行すると SQL_SUCCESS_WITH_INFO が返され、後続の**SQLGetDiagRec**の呼び出しでは*SQLState* 01000 が返されます。</span><span class="sxs-lookup"><span data-stu-id="c4519-120">PRINT statements cause the SQL statement execution to return SQL_SUCCESS_WITH_INFO, and a subsequent call to **SQLGetDiagRec** returns a *SQLState* of 01000.</span></span> <span data-ttu-id="c4519-121">重大度が 10 以下の RAISERROR の動作は PRINT と同様です。</span><span class="sxs-lookup"><span data-stu-id="c4519-121">A RAISERROR with a severity of ten or lower behaves the same as PRINT.</span></span> <span data-ttu-id="c4519-122">重大度が11以上の RAISERROR では、execute は SQL_ERROR を返し、後続の**SQLGetDiagRec**の呼び出しでは*SQLState* 42000 が返されます。</span><span class="sxs-lookup"><span data-stu-id="c4519-122">A RAISERROR with a severity of 11 or higher causes the execute to return SQL_ERROR, and a subsequent call to **SQLGetDiagRec** returns *SQLState* 42000.</span></span> <span data-ttu-id="c4519-123">たとえば、次のステートメントでは SQL_SUCCESS_WITH_INFO が返されます。</span><span class="sxs-lookup"><span data-stu-id="c4519-123">For example, the following statement returns SQL_SUCCESS_WITH_INFO:</span></span>  
  
```  
SQLExecDirect (hstmt, "PRINT  'Some message' ", SQL_NTS);  
```  
  
 <span data-ttu-id="c4519-124">**SQLGetDiagRec**を呼び出すと返されます。</span><span class="sxs-lookup"><span data-stu-id="c4519-124">Calling **SQLGetDiagRec** returns:</span></span>  
  
```  
szSQLState = "01000", *pfNative Error = 0,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Some message"  
```  
  
 <span data-ttu-id="c4519-125">次のステートメントからは、SQL_SUCCESS_WITH_INFO が返されます。</span><span class="sxs-lookup"><span data-stu-id="c4519-125">The following statement returns SQL_SUCCESS_WITH_INFO:</span></span>  
  
```  
SQLExecDirect (hstmt, "RAISERROR ('Sample error 1.', 10, -1)",  
   SQL_NTS)  
```  
  
 <span data-ttu-id="c4519-126">**SQLGetDiagRec**を呼び出すと返されます。</span><span class="sxs-lookup"><span data-stu-id="c4519-126">Calling **SQLGetDiagRec** returns:</span></span>  
  
```  
szSQLState = "01000", *pfNative Error = 50000,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Sample error 1."  
```  
  
 <span data-ttu-id="c4519-127">次のステートメントからは、SQL_ERROR が返されます。</span><span class="sxs-lookup"><span data-stu-id="c4519-127">The following statement returns SQL_ERROR:</span></span>  
  
```  
SQLExecDirect (hstmt, "RAISERROR ('Sample error 2.', 11, -1)", SQL_NTS)  
```  
  
 <span data-ttu-id="c4519-128">**SQLGetDiagRec**を呼び出すと返されます。</span><span class="sxs-lookup"><span data-stu-id="c4519-128">Calling **SQLGetDiagRec** returns:</span></span>  
  
```  
szSQLState = "42000", *pfNative Error = 50000,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Sample error 2."  
```  
  
 <span data-ttu-id="c4519-129">PRINT ステートメントまたは RAISERROR ステートメントからの出力が結果セットに含まれる場合、 **SQLGetDiagRec**の呼び出しのタイミングは重要です。</span><span class="sxs-lookup"><span data-stu-id="c4519-129">The timing of calling **SQLGetDiagRec** is critical when output from PRINT or RAISERROR statements is included in a result set.</span></span> <span data-ttu-id="c4519-130">PRINT または RAISERROR 出力を取得する**SQLGetDiagRec**の呼び出しは、SQL_ERROR または SQL_SUCCESS_WITH_INFO を受け取るステートメントの直後に行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4519-130">The call to **SQLGetDiagRec** to retrieve the PRINT or RAISERROR output must be made immediately after the statement that receives SQL_ERROR or SQL_SUCCESS_WITH_INFO.</span></span> <span data-ttu-id="c4519-131">この操作は、上記の例のように、1 つの SQL ステートメントのみを実行するときは容易に実行できます。</span><span class="sxs-lookup"><span data-stu-id="c4519-131">This is straightforward when only a single SQL statement is executed, as in the examples above.</span></span> <span data-ttu-id="c4519-132">このような場合、 **SQLExecDirect**または**sqlexecute**を呼び出すと、SQL_ERROR または SQL_SUCCESS_WITH_INFO が返され、 **SQLGetDiagRec**を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="c4519-132">In these cases, the call to **SQLExecDirect** or **SQLExecute** returns SQL_ERROR or SQL_SUCCESS_WITH_INFO and **SQLGetDiagRec** can then be called.</span></span> <span data-ttu-id="c4519-133">SQL ステートメントのバッチの出力を処理するループをコーディングするとき、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャを実行するときは、1 つの SQL ステートメントのみを実行するときほど簡単ではありません。</span><span class="sxs-lookup"><span data-stu-id="c4519-133">It is less straightforward when coding loops to handle the output of a batch of SQL statements or when executing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures.</span></span>  
  
 <span data-ttu-id="c4519-134">この場合、バッチまたはストアド プロシージャで実行される SELECT ステートメントごとに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から結果セットが返されます。</span><span class="sxs-lookup"><span data-stu-id="c4519-134">In this case, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] returns a result set for every SELECT statement executed in a batch or stored procedure.</span></span> <span data-ttu-id="c4519-135">バッチまたはプロシージャに PRINT ステートメントまたは RAISERROR ステートメントが含まれている場合、これらのステートメントの出力は SELECT ステートメントの結果セットと交互に返されます。</span><span class="sxs-lookup"><span data-stu-id="c4519-135">If the batch or procedure contains PRINT or RAISERROR statements, the output for these is interleaved with the SELECT statement result sets.</span></span> <span data-ttu-id="c4519-136">バッチまたはプロシージャの最初のステートメントが PRINT または RAISERROR の場合、 **Sqlexecute**または**SQLExecDirect**は SQL_SUCCESS_WITH_INFO または SQL_ERROR を返し、アプリケーションは SQL_NO_DATA を返して印刷情報または raiserror 情報を取得するまで、 **SQLGetDiagRec**を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4519-136">If the first statement in the batch or procedure is a PRINT or RAISERROR, the **SQLExecute** or **SQLExecDirect** returns SQL_SUCCESS_WITH_INFO or SQL_ERROR, and the application needs to call **SQLGetDiagRec** until it returns SQL_NO_DATA to retrieve the PRINT or RAISERROR information.</span></span>  
  
 <span data-ttu-id="c4519-137">PRINT ステートメントまたは RAISERROR ステートメントが SQL ステートメント (SELECT ステートメントなど) の後にある場合は、 [Sqlmoreresults](../native-client-odbc-api/sqlmoreresults.md)がエラーを含む結果セットに位置するときに、print または raiserror の情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="c4519-137">If the PRINT or RAISERROR statement comes after an SQL statement (such as a SELECT statement), then the PRINT or RAISERROR information is returned when [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md)positions on the result set containing the error.</span></span> <span data-ttu-id="c4519-138">**Sqlmoreresults**は、メッセージの重大度に応じて SQL_SUCCESS_WITH_INFO または SQL_ERROR を返します。</span><span class="sxs-lookup"><span data-stu-id="c4519-138">**SQLMoreResults** returns SQL_SUCCESS_WITH_INFO or SQL_ERROR depending on the severity of the message.</span></span> <span data-ttu-id="c4519-139">メッセージは SQL_NO_DATA が返されるまで、 **SQLGetDiagRec**を呼び出すことによって取得されます。</span><span class="sxs-lookup"><span data-stu-id="c4519-139">Messages are retrieved by calling **SQLGetDiagRec** until it returns SQL_NO_DATA.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4519-140">参照</span><span class="sxs-lookup"><span data-stu-id="c4519-140">See Also</span></span>  
 [<span data-ttu-id="c4519-141">エラーとメッセージの処理</span><span class="sxs-lookup"><span data-stu-id="c4519-141">Handling Errors and Messages</span></span>](handling-errors-and-messages.md)  
  
  
