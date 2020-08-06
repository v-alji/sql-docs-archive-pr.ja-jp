---
title: プロファイルドライバーのパフォーマンスデータ (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- driver performance data [ODBC]
ms.assetid: b997790a-8cc6-4800-8867-74c1bef07be3
author: rothja
ms.author: jroth
ms.openlocfilehash: 3575cfd304d526bdb25eee6a2578d67c6bb67bc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714329"
---
# <a name="profile-driver-performance-data-odbc"></a><span data-ttu-id="6fbe4-102">ドライバーのパフォーマンス データのプロファイル (ODBC)</span><span class="sxs-lookup"><span data-stu-id="6fbe4-102">Profile Driver Performance Data (ODBC)</span></span>
  <span data-ttu-id="6fbe4-103">このサンプルでは、パフォーマンス統計を記録するための [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC ドライバー固有のオプションを示します。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-103">This sample shows the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC driver-specific options to record performance statistics.</span></span> <span data-ttu-id="6fbe4-104">このサンプルでは、1 つのファイル (odbcperf.log) を作成します。このサンプルを通じて、パフォーマンス データのログ ファイルの作成と、SQLPERF データ構造体からのパフォーマンス データの直接表示の例を確認できます (SQLPERF 構造体は Odbcss.h で定義されます)。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-104">The sample creates one file: odbcperf.log.This sample shows both the creation of a performance data log file and displaying performance data directly from the SQLPERF data structure (The SQLPERF structure is defined in Odbcss.h.).</span></span> <span data-ttu-id="6fbe4-105">このサンプルは、ODBC 3.0 以降のバージョン用に開発されました。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-105">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6fbe4-106">可能な場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-106">When possible, use Windows Authentication.</span></span> <span data-ttu-id="6fbe4-107">Windows 認証が使用できない場合は、実行時に資格情報を入力するようユーザーに求めます。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-107">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="6fbe4-108">資格情報をファイルに保存するのは避けてください。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-108">Avoid storing credentials in a file.</span></span> <span data-ttu-id="6fbe4-109">資格情報を保持する必要がある場合は、[Win32 Crypto API](https://go.microsoft.com/fwlink/?LinkId=64532) を使用して暗号化してください。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-109">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-log-driver-performance-data-using-odbc-administrator"></a><span data-ttu-id="6fbe4-110">ODBC アドミニストレーターを使用してドライバーのパフォーマンス データをログに記録するには</span><span class="sxs-lookup"><span data-stu-id="6fbe4-110">To log driver performance data using ODBC Administrator</span></span>  
  
1.  <span data-ttu-id="6fbe4-111">**コントロールパネル**で、[**管理ツール**] をダブルクリックし、[**データソース (ODBC)**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-111">In **Control Panel**, double-click **Administrative Tools** and then double-click **Data Sources (ODBC)**.</span></span> <span data-ttu-id="6fbe4-112">または、odbcad32.exe を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-112">Alternatively, you can invoke odbcad32.exe.</span></span>  
  
2.  <span data-ttu-id="6fbe4-113">[**ユーザー dsn**]、[**システム dsn**]、または [**ファイル dsn** ] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-113">Click the **User DSN**, **System DSN**, or **File DSN** tab.</span></span>  
  
3.  <span data-ttu-id="6fbe4-114">パフォーマンスのログを記録するデータ ソースをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-114">Click the data source for which to log performance.</span></span>  
  
4.  <span data-ttu-id="6fbe4-115">**[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-115">Click **Configure**.</span></span>  
  
5.  <span data-ttu-id="6fbe4-116">Microsoft SQL Server DSN の構成ウィザードで、ログ**ファイルに ODBC ドライバーの統計情報が記録**されたページに移動します。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-116">In the Microsoft SQL Server Configure DSN Wizard, navigate to the page with **Log ODBC driver statistics to the log file**.</span></span>  
  
6.  <span data-ttu-id="6fbe4-117">[ **ODBC ドライバーの統計情報をログファイルに記録する**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-117">Select **Log ODBC driver statistics to the log file**.</span></span> <span data-ttu-id="6fbe4-118">ボックスに、統計をログに記録するファイルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-118">In the box, place the name of the file where the statistics should be logged.</span></span> <span data-ttu-id="6fbe4-119">必要に応じて、[**参照**] をクリックして、ファイルシステムで統計ログを参照します。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-119">Optionally, click **Browse** to browse the file system for the statistics log.</span></span>  
  
### <a name="to-log-driver-performance-data-programmatically"></a><span data-ttu-id="6fbe4-120">ドライバーのパフォーマンス データをプログラムを使用してログに記録するには</span><span class="sxs-lookup"><span data-stu-id="6fbe4-120">To log driver performance data programmatically</span></span>  
  
1.  <span data-ttu-id="6fbe4-121">SQL_COPT_SS_PERF_DATA_LOG と、パフォーマンスデータログファイルの完全なパスとファイル名を使用して[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-121">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_DATA_LOG and the full path and file name of the performance data log file.</span></span> <span data-ttu-id="6fbe4-122">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-122">For example:</span></span>  
  
    ```  
    "C:\\Odbcperf.log"  
    ```  
  
2.  <span data-ttu-id="6fbe4-123">SQL_COPT_SS_PERF_DATA と SQL_PERF_START を使用して[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)を呼び出し、パフォーマンスデータのログ記録を開始します。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-123">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_DATA and SQL_PERF_START to start logging performance data.</span></span>  
  
3.  <span data-ttu-id="6fbe4-124">必要に応じて、SQL_COPT_SS_LOG_NOW および NULL を使用して[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)を呼び出し、パフォーマンスデータのタブ区切りのレコードをパフォーマンスデータログファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-124">Optionally, call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_LOG_NOW and NULL to write a tab-delimited record of performance data to the performance data log file.</span></span> <span data-ttu-id="6fbe4-125">これは、アプリケーションの実行時に複数回実行できます。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-125">This can be done multiple times as the application runs.</span></span>  
  
4.  <span data-ttu-id="6fbe4-126">SQL_COPT_SS_PERF_DATA と SQL_PERF_STOP を使用して[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)を呼び出し、パフォーマンスデータのログ記録を停止します。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-126">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_DATA and SQL_PERF_STOP to stop logging performance data.</span></span>  
  
### <a name="to-pull-driver-performance-data-into-an-application"></a><span data-ttu-id="6fbe4-127">ドライバーのパフォーマンス データをアプリケーションにプルするには</span><span class="sxs-lookup"><span data-stu-id="6fbe4-127">To pull driver performance data into an application</span></span>  
  
1.  <span data-ttu-id="6fbe4-128">SQL_COPT_SS_PERF_DATA と SQL_PERF_START を使用して[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)を呼び出し、パフォーマンスデータのプロファイルを開始します。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-128">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_DATA and SQL_PERF_START to start profiling performance data.</span></span>  
  
2.  <span data-ttu-id="6fbe4-129">SQL_COPT_SS_PERF_DATA と SQLPERF 構造体へのポインターのアドレスを使用して、 [Sqlgetconnectattr](../native-client-odbc-api/sqlgetconnectattr.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-129">Call [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md) with SQL_COPT_SS_PERF_DATA and the address of a pointer to a SQLPERF structure.</span></span> <span data-ttu-id="6fbe4-130">最初の呼び出しでは、現在のパフォーマンス データを含む有効な SQLPERF 構造体のアドレスを指すポインターが設定されます。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-130">The first such call sets the pointer to the address of a valid SQLPERF structure that contains current performance data.</span></span> <span data-ttu-id="6fbe4-131">ドライバーは、パフォーマンス構造体内のデータを継続的に更新しません。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-131">The driver does not continually refresh the data in the performance structure.</span></span> <span data-ttu-id="6fbe4-132">アプリケーションでは、現在のパフォーマンスデータを使用して構造を更新する必要があるときはいつでも、 [Sqlgetconnectattr](../native-client-odbc-api/sqlgetconnectattr.md)への呼び出しを繰り返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-132">The application must repeat the call to [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md) any time it needs to refresh the structure with more current performance data.</span></span>  
  
3.  <span data-ttu-id="6fbe4-133">SQL_COPT_SS_PERF_DATA と SQL_PERF_STOP を使用して[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)を呼び出し、パフォーマンスデータのログ記録を停止します。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-133">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_DATA and SQL_PERF_STOP to stop logging performance data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fbe4-134">例</span><span class="sxs-lookup"><span data-stu-id="6fbe4-134">Example</span></span>  
 <span data-ttu-id="6fbe4-135">AdventureWorks と呼ばれる ODBC データ ソース (既定のデータベースは AdventureWorks サンプル データベース) が必要です </span><span class="sxs-lookup"><span data-stu-id="6fbe4-135">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="6fbe4-136">(AdventureWorks サンプルデータベースは、 [Microsoft SQL Server のサンプルとコミュニティのプロジェクト](https://go.microsoft.com/fwlink/?LinkID=85384)のホームページからダウンロードできます)。このデータソースは、オペレーティングシステムによって提供される ODBC ドライバーに基づいている必要があります (ドライバー名は "SQL Server")。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-136">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="6fbe4-137">このサンプルを 64 ビット オペレーティング システムで 32 ビット アプリケーションとしてビルドし、実行する場合、%windir%\SysWOW64\odbcad32.exe の ODBC アドミニストレーターを使用して ODBC データ ソースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-137">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="6fbe4-138">このサンプルでは、コンピューターの既定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-138">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="6fbe4-139">名前付きインスタンスに接続するには、ODBC データ ソースの定義を変更し、server\namedinstance 形式でそのインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-139">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="6fbe4-140">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] は、既定で名前付きインスタンスとしてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-140">By default, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="6fbe4-141">odbc32.lib を使用してコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="6fbe4-141">Compile with odbc32.lib.</span></span>  
  
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
  
   // Pointer to the ODBC driver performance structure.  
   SQLPERF *PerfPtr;  
   SQLINTEGER cbPerfPtr;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // This sample use Integrated Security. Please create the SQL Server   
   // DSN by using the Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set options to log performance statistics.  Specify file to use for the log.  
   retcode = SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA_LOG, &"odbcperf.log", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Start the performance statistics log.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA, (SQLPOINTER)SQL_PERF_START, SQL_IS_UINTEGER);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle, then execute command.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Purchasing.Vendor", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults() Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Sales.Store", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults() Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Generate a long-running query.  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"waitfor delay '00:00:04' ", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults() Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Write current statistics to the performance log.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA_LOG_NOW, (SQLPOINTER)NULL, SQL_IS_UINTEGER);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Get pointer to current SQLPerf structure.  
   // Print a couple of statistics.  
   retcode =   
      SQLGetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA, (SQLPOINTER)&PerfPtr, SQL_IS_POINTER, &cbPerfPtr);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLGetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("SQLSelects = %d, SQLSelectRows = %d\n", PerfPtr->SQLSelects, PerfPtr->SQLSelectRows);  
  
   // Cleanup  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6fbe4-142">参照</span><span class="sxs-lookup"><span data-stu-id="6fbe4-142">See Also</span></span>  
 <span data-ttu-id="6fbe4-143">[Odbc&#41;&#40;ODBC ドライバーのパフォーマンスのプロファイル方法に関するトピック](profiling-odbc-driver-performance-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="6fbe4-143">[Profiling ODBC Driver Performance How-to Topics &#40;ODBC&#41;](profiling-odbc-driver-performance-odbc.md) </span></span>  
 [<span data-ttu-id="6fbe4-144">ODBC ドライバーのパフォーマンスのプロファイル</span><span class="sxs-lookup"><span data-stu-id="6fbe4-144">Profiling ODBC Driver Performance</span></span>](../native-client/odbc/profiling-odbc-driver-performance.md)  
  
  
