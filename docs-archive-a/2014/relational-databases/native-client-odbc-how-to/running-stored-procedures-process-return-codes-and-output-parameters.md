---
title: リターンコードと出力パラメーターの処理 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- return codes [ODBC]
- output parameters [ODBC]
ms.assetid: 102ae1d0-973d-4e12-992c-d844bf05160d
author: rothja
ms.author: jroth
ms.openlocfilehash: b119d43806dafa68fe049595d94e909a5a1bb896
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640891"
---
# <a name="process-return-codes-and-output-parameters-odbc"></a><span data-ttu-id="05689-102">リターン コードと出力パラメーターの処理 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="05689-102">Process Return Codes and Output Parameters (ODBC)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="05689-103">のストアド プロシージャでは、整数のリターン コードと出力パラメーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="05689-103">stored procedures can have integer return codes and output parameters.</span></span> <span data-ttu-id="05689-104">リターンコードと出力パラメーターはサーバーからの最後のパケットで送信され、 [Sqlmoreresults](../native-client-odbc-api/sqlmoreresults.md)が SQL_NO_DATA を返すまではアプリケーションで使用できません。</span><span class="sxs-lookup"><span data-stu-id="05689-104">The return codes and output parameters are sent in the last packet from the server and are not available to the application until [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) returns SQL_NO_DATA.</span></span> <span data-ttu-id="05689-105">ストアドプロシージャからエラーが返された場合は、SQLMoreResults を呼び出して、SQL_NO_DATA が返されるまで次の結果に進みます。</span><span class="sxs-lookup"><span data-stu-id="05689-105">If an error is returned from a stored procedure, call SQLMoreResults to advance to the next result until SQL_NO_DATA is returned.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="05689-106">可能な場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="05689-106">When possible, use Windows Authentication.</span></span> <span data-ttu-id="05689-107">Windows 認証が使用できない場合は、実行時に資格情報を入力するようユーザーに求めます。</span><span class="sxs-lookup"><span data-stu-id="05689-107">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="05689-108">資格情報をファイルに保存するのは避けてください。</span><span class="sxs-lookup"><span data-stu-id="05689-108">Avoid storing credentials in a file.</span></span> <span data-ttu-id="05689-109">資格情報を保持する必要がある場合は、[Win32 Crypto API](https://go.microsoft.com/fwlink/?LinkId=64532) を使用して暗号化してください。</span><span class="sxs-lookup"><span data-stu-id="05689-109">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-process-return-codes-and-output-parameters"></a><span data-ttu-id="05689-110">リターン コードと出力パラメーターを処理するには</span><span class="sxs-lookup"><span data-stu-id="05689-110">To process return codes and output parameters</span></span>  
  
1.  <span data-ttu-id="05689-111">ODBC CALL エスケープ シーケンスを使用する SQL ステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="05689-111">Construct an SQL statement that uses the ODBC CALL escape sequence.</span></span> <span data-ttu-id="05689-112">このステートメントでは、各入力、入出力、出力パラメーター、およびプロシージャの戻り値 (存在する場合) に対してパラメーター マーカーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05689-112">The statement should use parameter markers for each input, input/output, and output parameter, and for the procedure return value (if any).</span></span>  
  
2.  <span data-ttu-id="05689-113">各入力、入出力、出力パラメーター、およびプロシージャの戻り値 (存在する場合) に対して[SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="05689-113">Call [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) for each input, input/output, and output parameter, and for the procedure return value (if any).</span></span>  
  
3.  <span data-ttu-id="05689-114">`SQLExecDirect` を使用してステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="05689-114">Execute the statement with `SQLExecDirect`.</span></span>  
  
4.  <span data-ttu-id="05689-115">最後の結果セットの処理中に `SQLFetch` または `SQLFetchScroll` によって SQL_NO_DATA が返されるまで、あるいは `SQLMoreResults` によって SQL_NO_DATA が返されるまで、結果セットを処理します。</span><span class="sxs-lookup"><span data-stu-id="05689-115">Process result sets until `SQLFetch` or `SQLFetchScroll` returns SQL_NO_DATA while processing the last result set or until `SQLMoreResults` returns SQL_NO_DATA.</span></span> <span data-ttu-id="05689-116">この時点で、リターン コードと出力パラメーターにバインドされた変数に、返されたデータ値が格納されています。</span><span class="sxs-lookup"><span data-stu-id="05689-116">At this point, the variables bound to the return code and output parameters are filled with returned data values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05689-117">例</span><span class="sxs-lookup"><span data-stu-id="05689-117">Example</span></span>  
 <span data-ttu-id="05689-118">このサンプルでは、リターン コードおよび出力パラメーターの処理を示します。</span><span class="sxs-lookup"><span data-stu-id="05689-118">This sample shows processing a return code and output parameter.</span></span> <span data-ttu-id="05689-119">このサンプルは IA64 ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="05689-119">This sample is not supported on IA64.</span></span> <span data-ttu-id="05689-120">このサンプルは、ODBC 3.0 以降のバージョン用に開発されました。</span><span class="sxs-lookup"><span data-stu-id="05689-120">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
 <span data-ttu-id="05689-121">AdventureWorks と呼ばれる ODBC データ ソース (既定のデータベースは AdventureWorks サンプル データベース) が必要です </span><span class="sxs-lookup"><span data-stu-id="05689-121">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="05689-122">(AdventureWorks サンプルデータベースは、 [Microsoft SQL Server のサンプルとコミュニティのプロジェクト](https://go.microsoft.com/fwlink/?LinkID=85384)のホームページからダウンロードできます)。このデータソースは、オペレーティングシステムによって提供される ODBC ドライバーに基づいている必要があります (ドライバー名は "SQL Server")。</span><span class="sxs-lookup"><span data-stu-id="05689-122">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="05689-123">このサンプルを 64 ビット オペレーティング システムで 32 ビット アプリケーションとしてビルドし、実行する場合、%windir%\SysWOW64\odbcad32.exe の ODBC アドミニストレーターを使用して ODBC データ ソースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05689-123">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="05689-124">このサンプルでは、コンピューターの既定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="05689-124">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="05689-125">名前付きインスタンスに接続するには、ODBC データ ソースの定義を変更し、server\namedinstance 形式でそのインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="05689-125">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="05689-126">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] は、既定で名前付きインスタンスとしてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="05689-126">By default, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="05689-127">1 つ目の ([!INCLUDE[tsql](../../includes/tsql-md.md)]) コード リストは、このサンプルで使用するストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="05689-127">The first ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing creates a stored procedure used by this sample.</span></span>  
  
 <span data-ttu-id="05689-128">odbc32.lib を使用して 2 つ目の (C++) コード リストをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="05689-128">Compile the second (C++) code listing with odbc32.lib.</span></span> <span data-ttu-id="05689-129">次に、プログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="05689-129">Then, execute the program.</span></span>  
  
 <span data-ttu-id="05689-130">3 つ目の ([!INCLUDE[tsql](../../includes/tsql-md.md)]) コード リストは、このサンプルで使用したストアド プロシージャを削除します。</span><span class="sxs-lookup"><span data-stu-id="05689-130">The third ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing deletes the stored procedure used by this sample.</span></span>  
  
```  
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'TestParm')  
   DROP PROCEDURE TestParm  
GO  
  
CREATE PROCEDURE TestParm   
@OutParm int OUTPUT   
AS  
SELECT Name FROM Purchasing.Vendor  
SELECT @OutParm = 88  
RETURN 99  
go  
```  
  
```  
// compile with: odbc32.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
#define MAXBUFLEN 255  
  
SQLHENV henv = SQL_NULL_HENV;  
SQLHDBC hdbc1 = SQL_NULL_HDBC;       
SQLHSTMT hstmt1 = SQL_NULL_HSTMT;  
  
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
   // SQLBindParameter variables.  
   SWORD sParm1 = 0, sParm2 = 1;  
   SQLLEN cbParm1 = SQL_NTS;  
   SQLLEN cbParm2 = SQL_NTS;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
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
  
   // This sample use Integrated Security. Create the SQL Server DSN by using the Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);  
  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle(hstmt1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Bind the return code to variable sParm1.  
   retcode = SQLBindParameter(hstmt1, 1, SQL_PARAM_OUTPUT, SQL_C_SSHORT, SQL_INTEGER, 0, 0, &sParm1, 0, &cbParm1);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLBindParameter(sParm1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Bind the output parameter to variable sParm2.  
   retcode = SQLBindParameter(hstmt1, 2, SQL_PARAM_OUTPUT, SQL_C_SSHORT, SQL_INTEGER, 0, 0, &sParm2, 0, &cbParm2);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLBindParameter(sParm2) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the command.   
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"{? = call TestParm(?)}", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Show parameters are not filled.  
   printf("Before result sets cleared: RetCode = %d, OutParm = %d.\n", sParm1, sParm2);  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA )  
      ;  
  
   // Show parameters are now filled.  
   printf("After result sets drained: RetCode = %d, OutParm = %d.\n", sParm1, sParm2);  
  
   // Clean up.   
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
```  
use AdventureWorks  
DROP PROCEDURE TestParm  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="05689-131">参照</span><span class="sxs-lookup"><span data-stu-id="05689-131">See Also</span></span>  
 [<span data-ttu-id="05689-132">ストアドプロシージャの実行方法に関するトピック &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="05689-132">Running Stored Procedures How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)  
  
  
