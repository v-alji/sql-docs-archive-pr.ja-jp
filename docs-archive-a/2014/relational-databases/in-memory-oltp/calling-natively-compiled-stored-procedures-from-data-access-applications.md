---
title: データ アクセス アプリケーションからのネイティブ コンパイル ストアド プロシージャの呼び出し | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 9cf6c5ff-4548-401a-b3ec-084f47ff0eb8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5583137d4c159756246938a83bf8c8e1fad6cdea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741018"
---
# <a name="calling-natively-compiled-stored-procedures-from-data-access-applications"></a><span data-ttu-id="21c8d-102">データ アクセス アプリケーションからのネイティブ コンパイル ストアド プロシージャの呼び出し</span><span class="sxs-lookup"><span data-stu-id="21c8d-102">Calling Natively Compiled Stored Procedures from Data Access Applications</span></span>
  <span data-ttu-id="21c8d-103">このトピックでは、データ アクセス アプリケーションからのネイティブ コンパイル ストアド プロシージャの呼び出しに関するガイダンスを示します。</span><span class="sxs-lookup"><span data-stu-id="21c8d-103">This topic discusses guidance on calling natively compiled stored procedures from data access applications.</span></span>  
  
 <span data-ttu-id="21c8d-104">カーソルは、ネイティブ コンパイル ストアド プロシージャに対して繰り返し処理できません。</span><span class="sxs-lookup"><span data-stu-id="21c8d-104">Cursors cannot iterate over a natively compiled stored procedure.</span></span>  
  
 <span data-ttu-id="21c8d-105">コンテキスト接続を使用して CLR モジュールからネイティブ コンパイル ストアド プロシージャを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="21c8d-105">Calling natively compiled stored procedures from CLR modules using the context connection is not supported.</span></span>  
  
 <span data-ttu-id="21c8d-106">SqlClient</span><span class="sxs-lookup"><span data-stu-id="21c8d-106">SqlClient</span></span>  
 <span data-ttu-id="21c8d-107">SqlClient の場合、準備実行と直接実行の区別はありません。</span><span class="sxs-lookup"><span data-stu-id="21c8d-107">For SqlClient there is no distinction between prepared and direct execution.</span></span> <span data-ttu-id="21c8d-108">CommandType = CommandType.StoredProcedure の SqlCommand を使用してストアド プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="21c8d-108">Execute stored procedures with SqlCommand with CommandType = CommandType.StoredProcedure.</span></span>  
  
 <span data-ttu-id="21c8d-109">SqlClient では、準備された RPC プロシージャ呼び出しはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="21c8d-109">SqlClient does not support prepared RPC procedure calls.</span></span>  
  
 <span data-ttu-id="21c8d-110">SqlClient では、ネイティブ コンパイル ストアド プロシージャ (CommandType.SchemaOnly) から返された結果セットに関するスキーマのみの情報 (メタデータ検出) の取得はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="21c8d-110">SqlClient does not support retrieving schema-only information (metadata discovery) about the result sets returned by a natively compiled stored procedure (CommandType.SchemaOnly).</span></span> <span data-ttu-id="21c8d-111">代わりに、[sp_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql) を使用します。</span><span class="sxs-lookup"><span data-stu-id="21c8d-111">Instead, use [sp_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="21c8d-112">Native Client</span><span class="sxs-lookup"><span data-stu-id="21c8d-112">Native Client</span></span>  
 <span data-ttu-id="21c8d-113">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client では、ネイティブ コンパイル ストアド プロシージャから返された結果セットに関するスキーマのみの情報 (メタデータ検出) の取得はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="21c8d-113">Versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client prior to [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] do not support retrieving schema-only information (metadata discovery) about the result sets returned by a natively compiled stored procedure.</span></span> <span data-ttu-id="21c8d-114">代わりに、[sp_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql) を使用します。</span><span class="sxs-lookup"><span data-stu-id="21c8d-114">Instead, use [sp_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql).</span></span>  
  
 <span data-ttu-id="21c8d-115">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client で ODBC ドライバーを使用したネイティブ コンパイル ストアド プロシージャの呼び出しに関して、次の推奨事項が適用されます。</span><span class="sxs-lookup"><span data-stu-id="21c8d-115">The following recommendations apply to calls of natively compiled stored procedure using the ODBC driver in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="21c8d-116">1 回だけストアド プロシージャを呼び出すのに最も効率的な方法は、`SQLExecDirect` と ODBC CALL 句を使用して直接 RPC を呼び出す方法です。</span><span class="sxs-lookup"><span data-stu-id="21c8d-116">The most efficient way to call a stored procedure once is to issue a direct RPC call using `SQLExecDirect` and ODBC CALL clauses.</span></span> <span data-ttu-id="21c8d-117">ステートメントは使用しないで [!INCLUDE[tsql](../../../includes/tsql-md.md)] `EXECUTE` ください。</span><span class="sxs-lookup"><span data-stu-id="21c8d-117">Do not use the [!INCLUDE[tsql](../../../includes/tsql-md.md)]`EXECUTE` statement.</span></span> <span data-ttu-id="21c8d-118">ストアド プロシージャを複数回呼び出す場合は、準備実行が効率的です。</span><span class="sxs-lookup"><span data-stu-id="21c8d-118">If a stored procedure is called more than once, prepared execution is more efficient.</span></span>  
  
 <span data-ttu-id="21c8d-119">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ストアド プロシージャを複数回呼び出すのに最も効率的な方法は、準備された RPC プロシージャ呼び出しを使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="21c8d-119">The most efficient way to call a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stored procedure more than once is through prepared RPC procedure calls.</span></span> <span data-ttu-id="21c8d-120">準備された RPC 呼び出しは、次のように、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client の ODBC ドライバーを使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="21c8d-120">Prepared RPC calls are performed as follows using the ODBC driver in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client:</span></span>  
  
-   <span data-ttu-id="21c8d-121">データベースへの接続を開きます。</span><span class="sxs-lookup"><span data-stu-id="21c8d-121">Open a connection to the database.</span></span>  
  
-   <span data-ttu-id="21c8d-122">`SQLBindParameter` を使用してパラメーターをバインドします。</span><span class="sxs-lookup"><span data-stu-id="21c8d-122">Bind the parameters using `SQLBindParameter`.</span></span>  
  
-   <span data-ttu-id="21c8d-123">`SQLPrepare.` を使用してプロシージャ呼び出しを準備します。</span><span class="sxs-lookup"><span data-stu-id="21c8d-123">Prepare the procedure call using `SQLPrepare.`</span></span>  
  
-   <span data-ttu-id="21c8d-124">`SQLExecute` を使用してストアド プロシージャを複数回実行します。</span><span class="sxs-lookup"><span data-stu-id="21c8d-124">Execute the stored procedure multiple times using `SQLExecute`.</span></span>  
  
 <span data-ttu-id="21c8d-125">次のコードに、注文に行アイテムを追加するためのストアド プロシージャの準備実行を示します。</span><span class="sxs-lookup"><span data-stu-id="21c8d-125">The following code fragment shows prepared execution of a stored procedure to add line items to an order.</span></span> <span data-ttu-id="21c8d-126">`SQLPrepare` は、1 回だけ呼び出されます。`SQLExecute` は、プロシージャの実行ごとに複数回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="21c8d-126">`SQLPrepare` is called only once and `SQLExecute` is called multiple times, once for each procedure execution.</span></span>  
  
```  
// Bind parameters  
// 1 - OrdNo   
SQLRETURN returnCode = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 10, 0,   
                     &order.OrdNo, sizeof(SQLINTEGER), NULL);  
if (returnCode != SQL_SUCCESS && returnCode != SQL_SUCCESS_WITH_INFO) {  
   ODBCError(henv, hdbc, hstmt, NULL, true);   
   exit(-1);  
}  
  
// 2, 3, 4 - ItemNo, ProdCode, Qty  
...  
  
// Prepare stored procedure  
returnCode = SQLPrepare(hstmt, (SQLTCHAR *) _T("{call ItemInsert(?, ?, ?, ?)}"),SQL_NTS);  
  
for (unsigned int i = 0; i < order.ItemCount; i++) {  
   ItemNo = order.ItemNo[i];  
   ProdCode = order.ProdCode[i];  
   Qty = order.Qty[i];  
  
   // Execute stored procedure  
   returnCode = SQLExecute(hstmt);  
   if (returnCode != SQL_SUCCESS && returnCode != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
}  
```  
  
## <a name="using-odbc-to-execute-a-natively-complied-stored-procedure"></a><span data-ttu-id="21c8d-127">ODBC を使用したネイティブ コンパイル ストアド プロシージャの実行</span><span class="sxs-lookup"><span data-stu-id="21c8d-127">Using ODBC to Execute a Natively Complied Stored Procedure</span></span>  
 <span data-ttu-id="21c8d-128">このサンプルでは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーを使用してパラメーターをバインドし、ストアド プロシージャを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="21c8d-128">This sample shows how to bind parameters and execute stored procedures using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  <span data-ttu-id="21c8d-129">このサンプルは、直接実行を使用して単一の注文を挿入し、準備実行を使用して注文の明細を挿入するコンソール アプリケーションにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="21c8d-129">The sample compiles to a console application that inserts a single order using direct execution, and inserts the order details using prepared execution.</span></span>  
  
 <span data-ttu-id="21c8d-130">このサンプルを実行するには:</span><span class="sxs-lookup"><span data-stu-id="21c8d-130">To run this sample:</span></span>  
  
1.  <span data-ttu-id="21c8d-131">メモリ最適化データ ファイル グループが含まれるサンプル データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="21c8d-131">Create a sample database with a memory-optimized data filegroup.</span></span> <span data-ttu-id="21c8d-132">メモリ最適化データ ファイルグループが含まれるデータベースを作成する方法については、「 [メモリ最適化テーブルおよびネイティブ コンパイル ストアド プロシージャの作成](creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21c8d-132">For information on how to create a database with a memory-optimized data filegroup, see [Creating a Memory-Optimized Table and a Natively Compiled Stored Procedure](creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md).</span></span>  
  
2.  <span data-ttu-id="21c8d-133">データベースを参照する PrepExecSample という ODBC データ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="21c8d-133">Create an ODBC data source called PrepExecSample that points to the database.</span></span> <span data-ttu-id="21c8d-134">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ドライバーを使用します。</span><span class="sxs-lookup"><span data-stu-id="21c8d-134">Use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client driver.</span></span> <span data-ttu-id="21c8d-135">また、サンプルを変更して [Microsoft ODBC Driver for SQL Server](https://msdn.microsoft.com/library/jj730314.aspx)を使用できます。</span><span class="sxs-lookup"><span data-stu-id="21c8d-135">You could also modify the sample and use the [Microsoft ODBC Driver for SQL Server](https://msdn.microsoft.com/library/jj730314.aspx).</span></span>  
  
3.  <span data-ttu-id="21c8d-136">サンプル データベースに [!INCLUDE[tsql](../../../includes/tsql-md.md)] スクリプト (下記) を実行します。</span><span class="sxs-lookup"><span data-stu-id="21c8d-136">Run the [!INCLUDE[tsql](../../../includes/tsql-md.md)] script (below) on the sample database.</span></span>  
  
4.  <span data-ttu-id="21c8d-137">サンプルをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="21c8d-137">Compile and run the sample.</span></span>  
  
5.  <span data-ttu-id="21c8d-138">テーブルの内容を照会することで、プログラムが正常に実行されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="21c8d-138">Verify successful execution of the program by querying the contents of the tables:</span></span>  
  
    ```  
    SELECT * FROM dbo.Ord  
    ```  
  
    ```  
    SELECT * FROM dbo.Item  
    ```  
  
 <span data-ttu-id="21c8d-139">以下は、メモリ最適化データベース オブジェクトを作成する [!INCLUDE[tsql](../../../includes/tsql-md.md)] コード リストです。</span><span class="sxs-lookup"><span data-stu-id="21c8d-139">The following is the [!INCLUDE[tsql](../../../includes/tsql-md.md)] code listing that creates the memory-optimized database objects.</span></span>  
  
```  
IF EXISTS (SELECT * FROM SYS.OBJECTS WHERE OBJECT_ID=OBJECT_ID('dbo.OrderInsert'))  
  DROP PROCEDURE dbo.OrderInsert  
go  
IF EXISTS (SELECT * FROM SYS.OBJECTS WHERE OBJECT_ID=OBJECT_ID('dbo.ItemInsert'))  
  DROP PROCEDURE dbo.ItemInsert  
GO  
IF EXISTS (SELECT * FROM SYS.OBJECTS WHERE OBJECT_ID=OBJECT_ID('dbo.Ord'))  
  DROP TABLE dbo.Ord  
GO  
IF EXISTS (SELECT * FROM SYS.OBJECTS WHERE OBJECT_ID=OBJECT_ID('dbo.Item'))  
  DROP TABLE dbo.Item  
GO  
CREATE TABLE dbo.Ord  
(  
   OrdNo INTEGER NOT NULL PRIMARY KEY NONCLUSTERED,  
   OrdDate DATETIME NOT NULL,   
   CustCode VARCHAR(5) NOT NULL)   
 WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
CREATE TABLE dbo.Item  
(  
   OrdNo INTEGER NOT NULL,   
   ItemNo INTEGER NOT NULL,   
   ProdCode INTEGER NOT NULL,   
   Qty INTEGER NOT NULL,  
   CONSTRAINT PK_Item PRIMARY KEY NONCLUSTERED (OrdNo,ItemNo))  
   WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
CREATE PROCEDURE dbo.OrderInsert(@OrdNo INTEGER, @CustCode VARCHAR(5))  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH  
(   TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
   LANGUAGE = 'english')  
  
  DECLARE @OrdDate datetime = GETDATE();  
  INSERT INTO dbo.Ord (OrdNo, CustCode, OrdDate) VALUES (@OrdNo, @CustCode, @OrdDate);   
END  
GO  
  
CREATE PROCEDURE dbo.ItemInsert(@OrdNo INTEGER, @ItemNo INTEGER, @ProdCode INTEGER, @Qty INTEGER)  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH  
(   TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
   LANGUAGE = N'us_english')  
  
  INSERT INTO dbo.Item (OrdNo, ItemNo, ProdCode, Qty) VALUES (@OrdNo, @ItemNo, @ProdCode, @Qty)  
END  
GO  
```  
  
 <span data-ttu-id="21c8d-140">以下は、C コード リストです。</span><span class="sxs-lookup"><span data-stu-id="21c8d-140">The following is the C code listing.</span></span>  
  
```  
// compile with: user32.lib odbc32.lib  
#pragma once  
#define WIN32_LEAN_AND_MEAN   // Exclude rarely-used stuff from Windows headers  
#include <stdio.h>  
#include <stdlib.h>  
#include <tchar.h>  
#include <windows.h>  
#include "sql.h"  
#include "sqlext.h"  
#include "sqlncli.h"  
  
// cardinality of order item related array variables  
#define ITEM_ARRAY_SIZE 20  
  
// struct to pass order entry data  
typedef struct OrdEntry_struct {  
   SQLINTEGER OrdNo;  
   SQLTCHAR CustCode[6];  
   SQLUINTEGER ItemCount;  
   SQLINTEGER ItemNo[ITEM_ARRAY_SIZE];  
   SQLINTEGER ProdCode[ITEM_ARRAY_SIZE];  
   SQLINTEGER Qty[ITEM_ARRAY_SIZE];  
} OrdEntryData;  
  
SQLHANDLE henv, hdbc, hstmt;  
  
void ODBCError(SQLHANDLE henv, SQLHANDLE hdbc, SQLHANDLE hstmt, SQLHANDLE hdesc, bool ShowError) {  
   SQLRETURN r = 0;  
   SQLTCHAR szSqlState[6] = {0};  
   SQLINTEGER fNativeError = 0;  
   SQLTCHAR szErrorMsg[256] = {0};  
   SQLSMALLINT cbErrorMsgMax = sizeof(szErrorMsg) - 1;  
   SQLSMALLINT cbErrorMsg = 0;  
   TCHAR text[1024] = {0}, title[256] = {0};  
  
   if (hdesc != NULL)  
      r = SQLGetDiagRec(SQL_HANDLE_DESC, hdesc, 1, szSqlState, &fNativeError, szErrorMsg, cbErrorMsgMax, &cbErrorMsg);  
   else {  
      if (hstmt != NULL)  
         r = SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, 1, szSqlState, &fNativeError, szErrorMsg, cbErrorMsgMax, &cbErrorMsg);  
      else {  
         if (hdbc != NULL)  
            r = SQLGetDiagRec(SQL_HANDLE_DBC, hdbc, 1, szSqlState, &fNativeError, szErrorMsg, cbErrorMsgMax, &cbErrorMsg);  
         else  
            r = SQLGetDiagRec(SQL_HANDLE_ENV, henv, 1, szSqlState, &fNativeError, szErrorMsg, cbErrorMsgMax, &cbErrorMsg);  
      }  
   }  
  
   if (ShowError) {  
      _sntprintf_s(title, _countof(title), _TRUNCATE, _T("ODBC Error %i"), fNativeError);  
      _sntprintf_s(text, _countof(text), _TRUNCATE, _T("[%s] - %s"), szSqlState, szErrorMsg);  
  
      MessageBox(NULL, (LPCTSTR) text, (LPCTSTR) _T("ODBC Error"), MB_OK);  
   }  
}  
  
void connect() {  
   SQLRETURN r;  
  
   r = SQLAllocHandle(SQL_HANDLE_ENV, NULL, &henv);  
  
   // This is an ODBC v3 application  
   r = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, 0);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, NULL, NULL, NULL, true);  
      exit(-1);  
   }  
  
   r = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
  
   // Run in ANSI/implicit transaction mode  
   r = SQLSetConnectAttr(hdbc, SQL_ATTR_AUTOCOMMIT, (SQLPOINTER) SQL_AUTOCOMMIT_OFF, SQL_IS_INTEGER);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, NULL, NULL, NULL, true);  
      exit(-1);  
   }  
  
   TCHAR szConnStrIn[256] = _T("DSN=PrepExecSample");  
  
   r = SQLDriverConnect(hdbc, NULL, (SQLTCHAR *) szConnStrIn, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, NULL, NULL, true);  
      exit(-1);  
   }  
}  
  
void setup_ODBC_basics() {  
   SQLRETURN r;  
  
   r = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);  
      exit(-1);  
   }  
}  
  
void OrdEntry(OrdEntryData& order) {  
   // Simple order entry  
   SQLRETURN r;  
  
   SQLINTEGER ItemNo, ProdCode, Qty;  
  
   // Bind parameters for the Order  
   // 1 - OrdNo input  
   r = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 0, 0, &order.OrdNo, sizeof(SQLINTEGER), NULL);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // 2 - Custcode input  
   r = SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT,SQL_C_TCHAR, SQL_VARCHAR, 5, 0, &order.CustCode, sizeof(order.CustCode), NULL);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // Insert the order  
   r = SQLExecDirect(hstmt, (SQLTCHAR *) _T("{call OrderInsert(?, ?)}"),SQL_NTS);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // Flush results & reset hstmt  
   r = SQLMoreResults(hstmt);  
   if (r != SQL_NO_DATA) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   r = SQLFreeStmt(hstmt, SQL_RESET_PARAMS);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // Bind parameters for the Items  
   // 1 - OrdNo   
   r = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 10, 0, &order.OrdNo, sizeof(SQLINTEGER), NULL);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // 2 - ItemNo   
   r = SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 10, 0, &ItemNo, sizeof(SQLINTEGER), NULL);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // 3 - ProdCode  
   r = SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 10, 0, &ProdCode, sizeof(SQLINTEGER), NULL);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // 4 - Qty  
   r = SQLBindParameter(hstmt, 4, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 10, 0, &Qty, sizeof(SQLINTEGER), NULL);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // Prepare to insert items one at a time  
   r = SQLPrepare(hstmt, (SQLTCHAR *) _T("{call ItemInsert(?, ?, ?, ?)}"),SQL_NTS);  
  
   for (unsigned int i = 0; i < order.ItemCount; i++) {  
  ItemNo = order.ItemNo[i];  
      ProdCode = order.ProdCode[i];  
      Qty = order.Qty[i];  
      r = SQLExecute(hstmt);  
      if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
         ODBCError(henv, hdbc, hstmt, NULL, true);   
         exit(-1);  
      }  
   }  
  
   // Flush results & reset hstmt  
   r = SQLMoreResults(hstmt);  
   if (r != SQL_NO_DATA) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   r = SQLFreeStmt(hstmt, SQL_RESET_PARAMS);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // Commit the transaction  
   r = SQLEndTran(SQL_HANDLE_DBC, hdbc, SQL_COMMIT);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
}  
  
void testOrderEntry() {  
  
   OrdEntryData order;  
  
   order.OrdNo = 1;  
   _tcscpy_s((TCHAR *) order.CustCode, _countof(order.CustCode), _T("CUST1"));  
   order.ItemNo[0] = 1;  
   order.ProdCode[0] = 10;  
   order.Qty[0] = 1;  
   order.ItemNo[1] = 2;  
   order.ProdCode[1] = 20;  
   order.Qty[1] = 2;  
   order.ItemNo[2] = 3;  
   order.ProdCode[2] = 30;  
   order.Qty[2] = 3;  
   order.ItemNo[3] = 4;  
   order.ProdCode[3] = 40;  
   order.Qty[3] = 4;  
   order.ItemCount = 4;  
  
   OrdEntry(order);  
}  
int _tmain() {  
   connect();  
   setup_ODBC_basics();  
  
   testOrderEntry();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="21c8d-141">参照</span><span class="sxs-lookup"><span data-stu-id="21c8d-141">See Also</span></span>  
 [<span data-ttu-id="21c8d-142">ネイティブ コンパイル ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="21c8d-142">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
