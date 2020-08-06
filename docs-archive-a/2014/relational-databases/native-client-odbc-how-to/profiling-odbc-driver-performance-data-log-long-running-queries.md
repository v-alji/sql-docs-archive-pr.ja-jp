---
title: 実行時間の長いクエリのログ記録 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- queries [ODBC]
ms.assetid: b9c1ddce-1dd9-409d-a414-8b544d616273
author: rothja
ms.author: jroth
ms.openlocfilehash: f73dbf6fe8fc4b3dfbbbc0012d14a58614b218dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740918"
---
# <a name="log-long-running-queries-odbc"></a><span data-ttu-id="cb68a-102">実行時間の長いクエリの記録 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="cb68a-102">Log Long-Running Queries (ODBC)</span></span>
  <span data-ttu-id="cb68a-103">このサンプルでは、実行時間の長いクエリをログに記録するための [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC ドライバー固有のオプションを示します。</span><span class="sxs-lookup"><span data-stu-id="cb68a-103">This sample shows the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC driver-specific options to log long-running queries.</span></span> <span data-ttu-id="cb68a-104">このサンプルを実行すると Odbcqry.log が作成されます。このファイルには、アプリケーションの設定間隔よりも実行時間が長いクエリの一覧が格納されます。</span><span class="sxs-lookup"><span data-stu-id="cb68a-104">When run, this sample creates Odbcqry.log, which contains a list of queries whose execution exceeds an interval set by the application.</span></span> <span data-ttu-id="cb68a-105">このサンプルは IA64 ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="cb68a-105">This sample is not supported on IA64.</span></span> <span data-ttu-id="cb68a-106">このサンプルは、ODBC 3.0 以降のバージョン用に開発されました。</span><span class="sxs-lookup"><span data-stu-id="cb68a-106">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cb68a-107">可能な場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="cb68a-107">When possible, use Windows Authentication.</span></span> <span data-ttu-id="cb68a-108">Windows 認証が使用できない場合は、実行時に資格情報を入力するようユーザーに求めます。</span><span class="sxs-lookup"><span data-stu-id="cb68a-108">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="cb68a-109">資格情報をファイルに保存するのは避けてください。</span><span class="sxs-lookup"><span data-stu-id="cb68a-109">Avoid storing credentials in a file.</span></span> <span data-ttu-id="cb68a-110">資格情報を保持する必要がある場合は、[Win32 Crypto API](https://go.microsoft.com/fwlink/?LinkId=64532) を使用して暗号化してください。</span><span class="sxs-lookup"><span data-stu-id="cb68a-110">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-log-long-running-queries-using-odbc-administrator"></a><span data-ttu-id="cb68a-111">ODBC アドミニストレーターを使用して実行時間の長いクエリをログに記録するには</span><span class="sxs-lookup"><span data-stu-id="cb68a-111">To log long-running queries using ODBC Administrator</span></span>  
  
1.  <span data-ttu-id="cb68a-112">**コントロールパネル**で、[**管理ツール**] をダブルクリックし、[**データソース (ODBC)**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb68a-112">In **Control Panel**, double-click **Administrative Tools** and then double-click **Data Sources (ODBC)**.</span></span> <span data-ttu-id="cb68a-113">(または、コマンドプロンプトから odbcad32.exe を実行することもできます)。</span><span class="sxs-lookup"><span data-stu-id="cb68a-113">(Alternatively, you can run odbcad32.exe from the command prompt.)</span></span>  
  
2.  <span data-ttu-id="cb68a-114">[**ユーザー dsn**]、[**システム dsn**]、または [**ファイル dsn** ] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb68a-114">Click the **User DSN**, **System DSN**, or **File DSN** tab.</span></span>  
  
3.  <span data-ttu-id="cb68a-115">実行時間の長いクエリのログを記録するデータ ソースをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb68a-115">Click the data source for which to log long-running queries.</span></span>  
  
4.  <span data-ttu-id="cb68a-116">**[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb68a-116">Click **Configure**.</span></span>  
  
5.  <span data-ttu-id="cb68a-117">Microsoft SQL Server DSN の構成ウィザードで、[**実行時間の長いクエリをログファイルに保存する**] ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="cb68a-117">In the Microsoft SQL Server Configure DSN Wizard, navigate to the page with **Save long-running queries to the log file**.</span></span>  
  
6.  <span data-ttu-id="cb68a-118">[**実行時間の長いクエリをログファイルに保存する**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb68a-118">Select **Save long-running queries to the log file**.</span></span> <span data-ttu-id="cb68a-119">ボックスに、実行時間の長いクエリのログを記録するファイルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="cb68a-119">In the box, place the name of the file where the long-running queries should be logged.</span></span> <span data-ttu-id="cb68a-120">必要に応じて、[**参照**] をクリックして、ファイルシステムでクエリログを参照します。</span><span class="sxs-lookup"><span data-stu-id="cb68a-120">Optionally, click **Browse** to browse the file system for the query log.</span></span>  
  
7.  <span data-ttu-id="cb68a-121">[**長いクエリ時間 (ミリ秒)** ] ボックスで、クエリのタイムアウト間隔をミリ秒単位で設定します。</span><span class="sxs-lookup"><span data-stu-id="cb68a-121">Set a query time-out interval, in milliseconds, in the **Long query time (milliseconds)** box.</span></span>  
  
### <a name="to-log-long-running-queries-data-programmatically"></a><span data-ttu-id="cb68a-122">実行時間の長いクエリをプログラムでログに記録するには</span><span class="sxs-lookup"><span data-stu-id="cb68a-122">To log long-running queries data programmatically</span></span>  
  
1.  <span data-ttu-id="cb68a-123">SQL_COPT_SS_PERF_QUERY_LOG と、実行時間の長いクエリログファイルの完全なパスとファイル名を使用して、 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cb68a-123">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_QUERY_LOG and the full path and file name of the long-running query log file.</span></span> <span data-ttu-id="cb68a-124">例:</span><span class="sxs-lookup"><span data-stu-id="cb68a-124">For example:</span></span>  
  
    ```  
    C:\\Odbcqry.log  
    ```  
  
2.  <span data-ttu-id="cb68a-125">SQL_COPT_SS_PERF_QUERY_INTERVAL を使用して[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)を呼び出し、タイムアウト間隔をミリ秒単位で設定します。</span><span class="sxs-lookup"><span data-stu-id="cb68a-125">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_QUERY_INTERVAL and set to the time-out interval, in milliseconds.</span></span>  
  
3.  <span data-ttu-id="cb68a-126">SQL_COPT_SS_PERF_QUERY と SQL_PERF_START を使用して[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)を呼び出し、実行時間の長いクエリのログ記録を開始します。</span><span class="sxs-lookup"><span data-stu-id="cb68a-126">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_QUERY and SQL_PERF_START to start logging long-running queries.</span></span>  
  
4.  <span data-ttu-id="cb68a-127">SQL_COPT_SS_PERF_QUERY と SQL_PERF_STOP を使用して[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)を呼び出し、実行時間の長いクエリのログ記録を停止します。</span><span class="sxs-lookup"><span data-stu-id="cb68a-127">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_QUERY and SQL_PERF_STOP to stop logging long-running queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb68a-128">例</span><span class="sxs-lookup"><span data-stu-id="cb68a-128">Example</span></span>  
 <span data-ttu-id="cb68a-129">AdventureWorks と呼ばれる ODBC データ ソース (既定のデータベースは AdventureWorks サンプル データベース) が必要です </span><span class="sxs-lookup"><span data-stu-id="cb68a-129">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="cb68a-130">(AdventureWorks サンプルデータベースは、 [Microsoft SQL Server のサンプルとコミュニティのプロジェクト](https://go.microsoft.com/fwlink/?LinkID=85384)のホームページからダウンロードできます)。このデータソースは、オペレーティングシステムによって提供される ODBC ドライバーに基づいている必要があります (ドライバー名は "SQL Server")。</span><span class="sxs-lookup"><span data-stu-id="cb68a-130">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="cb68a-131">このサンプルを 64 ビット オペレーティング システムで 32 ビット アプリケーションとしてビルドし、実行する場合、%windir%\SysWOW64\odbcad32.exe の ODBC アドミニストレーターを使用して ODBC データ ソースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb68a-131">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="cb68a-132">このサンプルでは、コンピューターの既定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="cb68a-132">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="cb68a-133">名前付きインスタンスに接続するには、ODBC データ ソースの定義を変更し、server\namedinstance 形式でそのインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="cb68a-133">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="cb68a-134">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] は、既定で名前付きインスタンスとしてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="cb68a-134">By default, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="cb68a-135">odbc32.lib を使用してコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="cb68a-135">Compile with odbc32.lib.</span></span>  
  
```  
// compile with: odbc32.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
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
  
   // sample uses Integrated Security, create SQL Server DSN using the Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set options to log long-running queries, including the file to use for the log.  
   retcode = SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_QUERY_LOG, &"odbcqry.log", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set the long-running query interval (in milliseconds).  Note that for version 2.50 and 2.65  
   // drivers, this value is specified in seconds, not milliseconds.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_QUERY_INTERVAL, (SQLPOINTER)3000, SQL_IS_UINTEGER);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Start the long-running query log.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_QUERY, (SQLPOINTER)SQL_PERF_START, SQL_IS_UINTEGER);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle then execute commands.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle(hstmt1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Purchasing.Vendor", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults Failed\n\n");  
         Cleanup();  
           return(9);  
      }  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Sales.Store", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Generate a long-running query.  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"waitfor delay '00:00:04' ", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Cleanup  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb68a-136">参照</span><span class="sxs-lookup"><span data-stu-id="cb68a-136">See Also</span></span>  
 [<span data-ttu-id="cb68a-137">Odbc&#41;&#40;ODBC ドライバーのパフォーマンスのプロファイル方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="cb68a-137">Profiling ODBC Driver Performance How-to Topics &#40;ODBC&#41;</span></span>](profiling-odbc-driver-performance-odbc.md)  
  
  
