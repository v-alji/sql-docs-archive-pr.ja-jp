---
title: ODBC エラーの処理 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- errors [ODBC]
ms.assetid: 66ab0762-79fe-4a31-b655-27dd215a0af7
author: rothja
ms.author: jroth
ms.openlocfilehash: 9f42223ffda8462ec740b94eb584565dfe286e0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738298"
---
# <a name="process-odbc-errors-odbc"></a><span data-ttu-id="61f27-102">ODBC エラーの処理 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="61f27-102">Process ODBC Errors (ODBC)</span></span>
  <span data-ttu-id="61f27-103">2 つの ODBC 関数呼び出し [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) および [SQLGetDiagField](../native-client-odbc-api/sqlgetdiagfield.md) を使用すると、ODBC メッセージを取得できます。</span><span class="sxs-lookup"><span data-stu-id="61f27-103">Two ODBC function calls can be used to retrieve ODBC messages: [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) and [SQLGetDiagField](../native-client-odbc-api/sqlgetdiagfield.md).</span></span> <span data-ttu-id="61f27-104">**SQLState**、**pfNative**、および **ErrorMessage** の各診断フィールドの主要な ODBC 関連情報を取得するには、SQL_NO_DATA が返されるまで [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="61f27-104">To obtain primary ODBC-related information in the **SQLState**, **pfNative**, and **ErrorMessage** diagnostic fields, call [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) until it returns SQL_NO_DATA.</span></span> <span data-ttu-id="61f27-105">診断レコードごとに、[SQLGetDiagField](../native-client-odbc-api/sqlgetdiagfield.md) を呼び出して個々のフィールドを取得できます。</span><span class="sxs-lookup"><span data-stu-id="61f27-105">For each diagnostic record, [SQLGetDiagField](../native-client-odbc-api/sqlgetdiagfield.md) can be called to retrieve individual fields.</span></span> <span data-ttu-id="61f27-106">ドライバー固有のフィールドはすべて、`SQLGetDiagField` を使用して取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61f27-106">All driver-specific fields must be retrieved using `SQLGetDiagField`.</span></span>  
  
 <span data-ttu-id="61f27-107">[SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) および [SQLGetDiagField](../native-client-odbc-api/sqlgetdiagfield.md) は、個々のドライバーではなく、ODBC ドライバー マネージャーによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="61f27-107">[SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) and [SQLGetDiagField](../native-client-odbc-api/sqlgetdiagfield.md) are processed by ODBC Driver Manager, not an individual driver.</span></span> <span data-ttu-id="61f27-108">ODBC ドライバー マネージャーは、接続が正しく確立されるまでドライバー固有の診断フィールドをキャッシュしません。</span><span class="sxs-lookup"><span data-stu-id="61f27-108">ODBC Driver Manager does not cache driver-specific diagnostic fields until a successful connection has been made.</span></span> <span data-ttu-id="61f27-109">接続が正しく確立される前に、ドライバー固有の診断フィールドに対して [SQLGetDiagField](../native-client-odbc-api/sqlgetdiagfield.md) を呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="61f27-109">Calling [SQLGetDiagField](../native-client-odbc-api/sqlgetdiagfield.md) for driver-specific diagnostic fields is not possible before a successful connection.</span></span> <span data-ttu-id="61f27-110">これには、SQL_SUCCESS_WITH_INFO が返される場合の ODBC 接続コマンドも含まれます。</span><span class="sxs-lookup"><span data-stu-id="61f27-110">This includes the ODBC connection commands, even if they return SQL_SUCCESS_WITH_INFO.</span></span> <span data-ttu-id="61f27-111">ドライバー固有の診断フィールドは、次の ODBC 関数呼び出しまで使用できません。</span><span class="sxs-lookup"><span data-stu-id="61f27-111">Driver-specific diagnostic fields will not be available until the next ODBC function call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61f27-112">例</span><span class="sxs-lookup"><span data-stu-id="61f27-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="61f27-113">説明</span><span class="sxs-lookup"><span data-stu-id="61f27-113">Description</span></span>  
 <span data-ttu-id="61f27-114">このサンプルでは、[SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) を呼び出して標準的な ODBC 情報を取得する簡単なエラー ハンドラーを示します。</span><span class="sxs-lookup"><span data-stu-id="61f27-114">This sample shows a simple error handler that calls [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) for the standard ODBC information.</span></span> <span data-ttu-id="61f27-115">その後、有効な接続を調べ、有効な接続がある場合は、`SQLGetDiagField` を呼び出して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC ドライバー固有の診断フィールドを取得します。</span><span class="sxs-lookup"><span data-stu-id="61f27-115">It then tests for a valid connection, and if one exists, it calls `SQLGetDiagField` for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC driver-specific diagnostic fields.</span></span> <span data-ttu-id="61f27-116">このサンプルは IA64 ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="61f27-116">This sample is not supported on IA64.</span></span>  
  
 <span data-ttu-id="61f27-117">このサンプルは、ODBC 3.0 以降のバージョン用に開発されました。</span><span class="sxs-lookup"><span data-stu-id="61f27-117">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="61f27-118">可能な場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="61f27-118">When possible, use Windows Authentication.</span></span> <span data-ttu-id="61f27-119">Windows 認証が使用できない場合は、実行時に資格情報を入力するようユーザーに求めます。</span><span class="sxs-lookup"><span data-stu-id="61f27-119">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="61f27-120">資格情報をファイルに保存するのは避けてください。</span><span class="sxs-lookup"><span data-stu-id="61f27-120">Avoid storing credentials in a file.</span></span> <span data-ttu-id="61f27-121">資格情報を保持する必要がある場合は、[Win32 Crypto API](https://go.microsoft.com/fwlink/?LinkId=64532) を使用して暗号化してください。</span><span class="sxs-lookup"><span data-stu-id="61f27-121">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
 <span data-ttu-id="61f27-122">AdventureWorks と呼ばれる ODBC データ ソース (既定のデータベースは AdventureWorks サンプル データベース) が必要です </span><span class="sxs-lookup"><span data-stu-id="61f27-122">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="61f27-123">(AdventureWorks サンプルデータベースは、 [Microsoft SQL Server のサンプルとコミュニティのプロジェクト](https://go.microsoft.com/fwlink/?LinkID=85384)のホームページからダウンロードできます)。このデータソースは、オペレーティングシステムによって提供される ODBC ドライバーに基づいている必要があります (ドライバー名は "SQL Server")。</span><span class="sxs-lookup"><span data-stu-id="61f27-123">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="61f27-124">このサンプルを 64 ビット オペレーティング システムで 32 ビット アプリケーションとしてビルドし、実行する場合、%windir%\SysWOW64\odbcad32.exe の ODBC アドミニストレーターを使用して ODBC データ ソースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61f27-124">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="61f27-125">このサンプルでは、コンピューターの既定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="61f27-125">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="61f27-126">名前付きインスタンスに接続するには、ODBC データ ソースの定義を変更し、server\namedinstance 形式でそのインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="61f27-126">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="61f27-127">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] は、既定で名前付きインスタンスとしてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="61f27-127">By default, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="61f27-128">1 つ目の ([!INCLUDE[tsql](../../includes/tsql-md.md)]) コード リストを実行して、このサンプルで使用するストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="61f27-128">Execute the first ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing to create the stored procedure used by this sample.</span></span>  
  
 <span data-ttu-id="61f27-129">odbc32.lib を使用して 2 つ目の (C++) コード リストをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="61f27-129">Compile the second (C++) code listing with odbc32.lib.</span></span> <span data-ttu-id="61f27-130">次に、プログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="61f27-130">Then, execute the program.</span></span>  
  
 <span data-ttu-id="61f27-131">3 つ目の ([!INCLUDE[tsql](../../includes/tsql-md.md)]) コード リストを実行して、このサンプルで使用したストアド プロシージャを削除します。</span><span class="sxs-lookup"><span data-stu-id="61f27-131">Execute the third ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing to delete the stored procedure used by this sample.</span></span>  
  
### <a name="code"></a><span data-ttu-id="61f27-132">コード</span><span class="sxs-lookup"><span data-stu-id="61f27-132">Code</span></span>  
  
```  
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BadOne')  
   DROP PROCEDURE BadOne  
  
Go  
  
CREATE PROCEDURE BadOne   
AS   
SELECT * FROM Purchasing.Vendor  
Go  
```  
  
### <a name="code"></a><span data-ttu-id="61f27-133">コード</span><span class="sxs-lookup"><span data-stu-id="61f27-133">Code</span></span>  
  
```  
// compile with: odbc32.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
#define MAXBUFLEN 256  
  
SQLHENV henv = SQL_NULL_HENV;  
SQLHDBC hdbc1 = SQL_NULL_HDBC;       
SQLHSTMT hstmt1 = SQL_NULL_HSTMT;  
  
void ProcessLogMessages(SQLSMALLINT plm_handle_type, SQLHANDLE plm_handle, char *logstring, int ConnInd);  
  
void Cleanup() {  
   if (hstmt1 != SQL_NULL_HSTMT)  
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER)SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // This sample use Integrated Security. Please create the SQL Server   
   // DSN by using the Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) &&  
      (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         ProcessLogMessages(SQL_HANDLE_DBC, hdbc1, "SQLConnect() Failed\n\n", FALSE);  
         Cleanup();  
         return(9);  
   }  
   else {  
      ProcessLogMessages(SQL_HANDLE_DBC, hdbc1,  
         "\nConnect Successful\n\n", FALSE);  
   }  
  
   // Allocate statement handle, and then execute command.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      ProcessLogMessages(SQL_HANDLE_DBC, hdbc1, "SQLAllocHandle(hstmt1) Failed\n\n", TRUE);  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"exec BadOne", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         ProcessLogMessages(SQL_HANDLE_STMT, hstmt1, "SQLExecute() Failed\n\n", TRUE);  
         Cleanup();  
         return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA )  
      ;  
  
   // Clean up.   
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
void ProcessLogMessages(SQLSMALLINT plm_handle_type, SQLHANDLE plm_handle, char *logstring, int ConnInd) {  
   RETCODE plm_retcode = SQL_SUCCESS;  
   UCHAR plm_szSqlState[MAXBUFLEN] = "", plm_szErrorMsg[MAXBUFLEN] = "";  
   SDWORD plm_pfNativeError = 0L;  
   SWORD plm_pcbErrorMsg = 0;  
   SQLSMALLINT plm_cRecNmbr = 1;  
   SDWORD plm_SS_MsgState = 0, plm_SS_Severity = 0;  
   SQLINTEGER plm_Rownumber = 0;  
   USHORT plm_SS_Line;  
   SQLSMALLINT plm_cbSS_Procname, plm_cbSS_Srvname;  
   SQLCHAR plm_SS_Procname[MAXNAME], plm_SS_Srvname[MAXNAME];  
  
   if (logstring)  
      printf(logstring);  
  
   while (plm_retcode != SQL_NO_DATA_FOUND) {  
      plm_retcode = SQLGetDiagRec(plm_handle_type, plm_handle, plm_cRecNmbr,   
                                  plm_szSqlState, &plm_pfNativeError, plm_szErrorMsg,   
                                  MAXBUFLEN - 1, &plm_pcbErrorMsg);  
  
      // Note that if the application has not yet made a successful connection,   
      // the SQLGetDiagField information has not yet been cached by ODBC Driver Manager and   
      // these calls to SQLGetDiagField will fail.  
      if (plm_retcode != SQL_NO_DATA_FOUND) {  
         if (ConnInd) {   
            plm_retcode = SQLGetDiagField( plm_handle_type, plm_handle, plm_cRecNmbr,  
                                                        SQL_DIAG_ROW_NUMBER, &plm_Rownumber,  
                                                        SQL_IS_INTEGER, NULL);  
  
            plm_retcode = SQLGetDiagField( plm_handle_type, plm_handle, plm_cRecNmbr,  
                                           SQL_DIAG_SS_LINE, &plm_SS_Line, SQL_IS_INTEGER, NULL);  
  
            plm_retcode = SQLGetDiagField( plm_handle_type, plm_handle, plm_cRecNmbr,   
                                           SQL_DIAG_SS_MSGSTATE, &plm_SS_MsgState,  
                                           SQL_IS_INTEGER, NULL);  
  
            plm_retcode = SQLGetDiagField( plm_handle_type, plm_handle, plm_cRecNmbr,  
                                           SQL_DIAG_SS_SEVERITY, &plm_SS_Severity,  
                                           SQL_IS_INTEGER, NULL);  
  
            plm_retcode = SQLGetDiagField( plm_handle_type, plm_handle, plm_cRecNmbr,  
                                           SQL_DIAG_SS_PROCNAME, &plm_SS_Procname,  
                                           sizeof(plm_SS_Procname), &plm_cbSS_Procname);  
  
            plm_retcode = SQLGetDiagField( plm_handle_type, plm_handle, plm_cRecNmbr,  
                                           SQL_DIAG_SS_SRVNAME, &plm_SS_Srvname,   
                                           sizeof(plm_SS_Srvname), &plm_cbSS_Srvname);  
         }  
  
         printf("szSqlState = %s\n", plm_szSqlState);  
         printf("pfNativeError = %d\n", plm_pfNativeError);  
         printf("szErrorMsg = %s\n", plm_szErrorMsg);  
         printf("pcbErrorMsg = %d\n\n", plm_pcbErrorMsg);  
  
         if (ConnInd) {  
            printf("ODBCRowNumber = %d\n", plm_Rownumber);  
            printf("SSrvrLine = %d\n", plm_Rownumber);  
            printf("SSrvrMsgState = %d\n", plm_SS_MsgState);  
            printf("SSrvrSeverity = %d\n", plm_SS_Severity);  
            printf("SSrvrProcname = %s\n", plm_SS_Procname);  
            printf("SSrvrSrvname = %s\n\n", plm_SS_Srvname);  
         }  
      }  
  
      plm_cRecNmbr++;   // Increment to next diagnostic record.  
   }  
}  
```  
  
### <a name="code"></a><span data-ttu-id="61f27-134">コード</span><span class="sxs-lookup"><span data-stu-id="61f27-134">Code</span></span>  
  
```  
use AdventureWorks  
DROP PROCEDURE BadOne  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="61f27-135">参照</span><span class="sxs-lookup"><span data-stu-id="61f27-135">See Also</span></span>  
 [<span data-ttu-id="61f27-136">ODBC の使用法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="61f27-136">ODBC How-to Topics</span></span>](odbc-how-to-topics.md)  
  
  
