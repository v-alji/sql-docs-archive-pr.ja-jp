---
title: スパース列を含むテーブルで SQLColumns を呼び出す |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: afd35e13-2370-43c2-9cbc-f8da6248c39c
author: rothja
ms.author: jroth
ms.openlocfilehash: 5493ff9f51f34382f3565cabd49bd672e43d4e79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740917"
---
# <a name="call-sqlcolumns-on-a-table-with-sparse-columns"></a><span data-ttu-id="8c0a6-102">スパース列を持つテーブルに対する SQLColumns の呼び出し</span><span class="sxs-lookup"><span data-stu-id="8c0a6-102">Call SQLColumns on a Table with Sparse Columns</span></span>
  <span data-ttu-id="8c0a6-103">このサンプルでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client の ODBC を使用して定義されたスパース列を含むテーブルに対し、SQLColumns を呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8c0a6-103">This sample shows how to call SQLColumns on a table with sparse columns that were defined by using ODBC in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="8c0a6-104">このサンプルは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] では動作しません。</span><span class="sxs-lookup"><span data-stu-id="8c0a6-104">This sample will not work with any version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="8c0a6-105">スパース列の機能の詳細については、「 [SQL Server Native Client でのスパース列のサポート](../native-client/features/sparse-columns-support-in-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c0a6-105">For more information about the sparse columns feature, see [Sparse Columns Support in SQL Server Native Client](../native-client/features/sparse-columns-support-in-sql-server-native-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c0a6-106">例</span><span class="sxs-lookup"><span data-stu-id="8c0a6-106">Example</span></span>  
 <span data-ttu-id="8c0a6-107">最初のリストは、C++ ソース コードです。</span><span class="sxs-lookup"><span data-stu-id="8c0a6-107">The first listing is the C++ source code.</span></span> <span data-ttu-id="8c0a6-108">"MyServer" を有効なサーバー名に変更してください。</span><span class="sxs-lookup"><span data-stu-id="8c0a6-108">Change "MyServer" to a valid server name.</span></span> <span data-ttu-id="8c0a6-109">INCLUDE 環境変数に、sqlncli を含むディレクトリが含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8c0a6-109">Make sure your INCLUDE environment variable includes the directory that contains sqlncli.h.</span></span> <span data-ttu-id="8c0a6-110">このサンプルを 64 ビット オペレーティング システムで 32 ビット アプリケーションとしてビルドし、実行する場合、%windir%\SysWOW64\odbcad32.exe の ODBC アドミニストレーターを使用して ODBC データ ソースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c0a6-110">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="8c0a6-111">このサンプルでは、コンピューターの既定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="8c0a6-111">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="8c0a6-112">名前付きインスタンスに接続するには、ODBC データ ソースの定義を変更し、server\namedinstance 形式でそのインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="8c0a6-112">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="8c0a6-113">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] は、既定で名前付きインスタンスとしてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="8c0a6-113">By default, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="8c0a6-114">/EHsc /D、"UNICODE"、および odbc32.lib を使用してコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="8c0a6-114">Compile with /EHsc /D, "UNICODE", and odbc32.lib.</span></span>  
  
 <span data-ttu-id="8c0a6-115">2 つ目の ([!INCLUDE[tsql](../../includes/tsql-md.md)]) コード リストは、このサンプルで作成したテーブルを削除します。</span><span class="sxs-lookup"><span data-stu-id="8c0a6-115">The second ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing deletes the table created by this sample.</span></span>  
  
```  
// compile with: /EHsc /D "UNICODE" odbc32.lib  
#include <windows.h>  
#include <stdio.h>  
#include <sqlext.h>  
  
#include <sqlncli.h>  
  
#define SUCCESS(x) (!((x) & 0xFFFE))  
  
#define CHKRC(stmt) rc = (stmt); \  
   if (!SUCCESS(rc)) \  
   throw (RETCODE) rc;  
  
void PrintError(SQLSMALLINT HandleType, SQLHANDLE Handle) {  
   RETCODE rc = SQL_SUCCESS;  
   SQLTCHAR szSqlState[6], szMessage[1024];  
   SQLSMALLINT i = 1, msgLen = 0;  
   SQLINTEGER NativeError;  
  
   do {  
      i = 1;  
      while (SQL_NO_DATA != (rc = SQLGetDiagRec(HandleType, Handle, i, szSqlState, &NativeError,   
         szMessage, sizeof(szMessage)/sizeof(SQLTCHAR), &msgLen)) && SUCCESS(rc)) {  
            wprintf(L"SQLState=%s, NativeError=%ld, Message=%s\r\n", szSqlState, NativeError, szMessage);  
            i++;  
      }  
   }   
   while (SQL_NO_DATA != (rc = SQLMoreResults(Handle)) && SUCCESS(rc));  
}  
  
#define STR_LEN 128 + 1  
#define REM_LEN 254 + 1  
  
void ProcessSQLColumnsResult(SQLHSTMT hstmt) {  
   SQLCHAR szSchema[STR_LEN];  
   SQLCHAR szCatalog[STR_LEN];  
   SQLCHAR szColumnName[STR_LEN];  
   SQLCHAR szTableName[STR_LEN];  
   SQLCHAR szTypeName[STR_LEN];  
   SQLCHAR szRemarks[REM_LEN];  
   SQLCHAR szColumnDefault[STR_LEN];  
   SQLCHAR szIsNullable[STR_LEN];  
  
   SQLINTEGER ColumnSize;  
   SQLINTEGER BufferLength;  
   SQLINTEGER CharOctetLength;  
   SQLINTEGER OrdinalPosition;  
  
   SQLSMALLINT DataType;  
   SQLSMALLINT DecimalDigits;  
   SQLSMALLINT NumPrecRadix;  
   SQLSMALLINT Nullable;  
   SQLSMALLINT SQLDataType;  
   SQLSMALLINT DatetimeSubtypeCode;  
   SQLLEN cbCatalog;  
   SQLLEN cbSchema;  
   SQLLEN cbTableName;  
   SQLLEN cbColumnName;  
   SQLLEN cbDataType;  
   SQLLEN cbTypeName;  
   SQLLEN cbColumnSize;  
   SQLLEN cbBufferLength;  
   SQLLEN cbDecimalDigits;  
   SQLLEN cbNumPrecRadix;  
   SQLLEN cbNullable;  
   SQLLEN cbRemarks;  
   SQLLEN cbColumnDefault;  
   SQLLEN cbSQLDataType;  
   SQLLEN cbDatetimeSubtypeCode;  
   SQLLEN cbCharOctetLength;  
   SQLLEN cbOrdinalPosition;  
   SQLLEN cbIsNullable;  
  
   SQLRETURN rc = SQL_SUCCESS;  
  
   CHKRC(SQLColumns(hstmt, L"tempdb", SQL_NTS, L"dbo", SQL_NTS, L"tbl_sparse_test", SQL_NTS, NULL, 0 ));  
  
   // Bind columns in result set to buffers  
   SQLBindCol(hstmt, 1,  SQL_C_CHAR,   szCatalog,              STR_LEN,    &cbCatalog);  
   SQLBindCol(hstmt, 2,  SQL_C_CHAR,   szSchema,               STR_LEN,    &cbSchema);  
   SQLBindCol(hstmt, 3,  SQL_C_CHAR,   szTableName,            STR_LEN,    &cbTableName);  
   SQLBindCol(hstmt, 4,  SQL_C_CHAR,   szColumnName,           STR_LEN,    &cbColumnName);  
   SQLBindCol(hstmt, 5,  SQL_C_SSHORT, &DataType,              0,          &cbDataType);  
   SQLBindCol(hstmt, 6,  SQL_C_CHAR,   szTypeName,             STR_LEN,    &cbTypeName);  
   SQLBindCol(hstmt, 7,  SQL_C_SLONG,  &ColumnSize,            0,          &cbColumnSize);  
   SQLBindCol(hstmt, 8,  SQL_C_SLONG,  &BufferLength,          0,          &cbBufferLength);  
   SQLBindCol(hstmt, 9,  SQL_C_SSHORT, &DecimalDigits,         0,          &cbDecimalDigits);  
   SQLBindCol(hstmt, 10, SQL_C_SSHORT, &NumPrecRadix,          0,          &cbNumPrecRadix);  
   SQLBindCol(hstmt, 11, SQL_C_SSHORT, &Nullable,              0,          &cbNullable);  
   SQLBindCol(hstmt, 12, SQL_C_CHAR,   szRemarks,              REM_LEN,    &cbRemarks);  
   SQLBindCol(hstmt, 13, SQL_C_CHAR,   szColumnDefault,        STR_LEN,    &cbColumnDefault);  
   SQLBindCol(hstmt, 14, SQL_C_SSHORT, &SQLDataType,           0,          &cbSQLDataType);  
   SQLBindCol(hstmt, 15, SQL_C_SSHORT, &DatetimeSubtypeCode,   0,          &cbDatetimeSubtypeCode);  
   SQLBindCol(hstmt, 16, SQL_C_SLONG,  &CharOctetLength,       0,          &cbCharOctetLength);  
   SQLBindCol(hstmt, 17, SQL_C_SLONG,  &OrdinalPosition,       0,          &cbOrdinalPosition);  
   SQLBindCol(hstmt, 18, SQL_C_CHAR,   szIsNullable,           STR_LEN,    &cbIsNullable);  
  
   try {  
      while (SQL_SUCCESS == rc) {  
         CHKRC(SQLFetch(hstmt));  
         wprintf(L"Column name: %hs\tIsNullable: %hs\tType: %hs\n", szColumnName, szIsNullable, szTypeName);  
      }  
   }  
   catch (RETCODE retcode) {  
      if (SQL_NO_DATA != retcode)  
         throw retcode;  
   }  
   SQLFreeStmt(hstmt, SQL_CLOSE);  
}  
  
int main() {  
   RETCODE rc = SQL_SUCCESS;  
   HENV henv = SQL_NULL_HENV;  
   HDBC hdbc = SQL_NULL_HDBC;  
   SQLHSTMT hstmt = SQL_NULL_HSTMT;  
   SQLTCHAR * pszConnection = L"DRIVER={SQL Server Native Client 10.0}; Server=MyServer; Trusted_Connection=Yes;";  
  
   try {  
      CHKRC(SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HENV, &henv));  
      CHKRC(SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER)SQL_OV_ODBC3, 0));  
      CHKRC(SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc));  
      CHKRC(SQLDriverConnect( hdbc, NULL, pszConnection, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT));  
      CHKRC(SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt));  
      CHKRC(SQLExecDirect(hstmt,  
         L"if object_id('tempdb.dbo.tbl_sparse_test','U') is not null drop table tempdb.dbo.tbl_sparse_test",  
         SQL_NTS));  
  
      // Create a new table  
      CHKRC(SQLExecDirect(hstmt,  
         L"create table tempdb.dbo.tbl_sparse_test (col1 int SPARSE, col2 int, col3 XML column_set for all_sparse_columns)",  
         SQL_NTS));  
  
      // Insert a row into the table  
      CHKRC(SQLExecDirect(hstmt,  
         L"insert tempdb.dbo.tbl_sparse_test (col1, col2) values (1,2)",  
         SQL_NTS));  
  
      wprintf(L"Checking default SQLColumns behavior.\nYou should not see the first sparse column.\n");  
  
      ProcessSQLColumnsResult(hstmt);  
  
      wprintf(L"\nChecking SQLColumns with the statement attribute SQL_SS_NAME_SCOPE_EXTENDED.\nYou should see all the columns\n");  
      CHKRC(SQLSetStmtAttr(hstmt, SQL_SOPT_SS_NAME_SCOPE, (SQLPOINTER)SQL_SS_NAME_SCOPE_EXTENDED, SQL_IS_SMALLINT));  
  
      ProcessSQLColumnsResult(hstmt);  
  
      wprintf(L"\nChecking SQLColumns with the statement attribute SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET.\nYou should see only the sparse columns\n");  
      CHKRC(SQLSetStmtAttr(hstmt, SQL_SOPT_SS_NAME_SCOPE, (SQLPOINTER)SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET, SQL_IS_SMALLINT));  
  
      ProcessSQLColumnsResult(hstmt);  
  
   }  
   catch (RETCODE retcode) {  
      rc = retcode;  
   }  
  
   if (!SUCCESS(rc)) {  
      if (hstmt)  
         PrintError(SQL_HANDLE_STMT, hstmt);  
      else if (hdbc)  
         PrintError(SQL_HANDLE_DBC, hdbc);  
      else if(henv)  
         PrintError(SQL_HANDLE_ENV, henv);  
   }  
  
   if (hstmt)  
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
   if (hdbc) {  
      SQLDisconnect(hdbc);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
   }  
   if (henv)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
```  
use tempdb  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'tbl_sparse_test')  
     DROP TABLE tbl_sparse_test  
GO  
```  
  
  
