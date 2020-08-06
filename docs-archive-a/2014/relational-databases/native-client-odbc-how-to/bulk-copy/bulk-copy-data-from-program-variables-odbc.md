---
title: プログラム変数からの一括データコピー (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], program variables
- bulk copy [ODBC]
ms.assetid: 0c3f2d7c-4ff2-4887-adfd-1f488a27c21c
author: rothja
ms.author: jroth
ms.openlocfilehash: e6e1c5294611b280aea8e67963613971f2690c44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741997"
---
# <a name="bulk-copy-data-from-program-variables-odbc"></a><span data-ttu-id="3aa81-102">プログラム変数からのデータの一括コピー (ODBC)</span><span class="sxs-lookup"><span data-stu-id="3aa81-102">Bulk Copy Data from Program Variables (ODBC)</span></span>
  <span data-ttu-id="3aa81-103">このサンプルでは、一括コピー関数 `bcp_bind` と `bcp_sendrow` を使用して、プログラム変数から SQL Server にデータを一括コピーする方法を示します </span><span class="sxs-lookup"><span data-stu-id="3aa81-103">This sample shows how to use bulk copy functions to bulk copy data from program variables to SQL Server using `bcp_bind` and `bcp_sendrow`.</span></span> <span data-ttu-id="3aa81-104">(この例では、簡略化のためエラーチェック コードが削除されています)。</span><span class="sxs-lookup"><span data-stu-id="3aa81-104">(Error-checking code is removed to simplify this example.)</span></span>  
  
 <span data-ttu-id="3aa81-105">このサンプルは、ODBC 3.0 以降のバージョン用に開発されました。</span><span class="sxs-lookup"><span data-stu-id="3aa81-105">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
 <span data-ttu-id="3aa81-106">**セキュリティ**に関する注意可能であれば、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="3aa81-106">**Security Note** When possible, use Windows Authentication.</span></span> <span data-ttu-id="3aa81-107">Windows 認証が使用できない場合は、実行時に資格情報を入力するようユーザーに求めます。</span><span class="sxs-lookup"><span data-stu-id="3aa81-107">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="3aa81-108">資格情報をファイルに保存するのは避けてください。</span><span class="sxs-lookup"><span data-stu-id="3aa81-108">Avoid storing credentials in a file.</span></span> <span data-ttu-id="3aa81-109">資格情報を保存する必要がある場合は、[Win32 CryptoAPI](https://go.microsoft.com/fwlink/?LinkId=9504) を使用して暗号化してください。</span><span class="sxs-lookup"><span data-stu-id="3aa81-109">If you must persist credentials, you should encrypt them with [the Win32 cryptoAPI](https://go.microsoft.com/fwlink/?LinkId=9504).</span></span>  
  
### <a name="to-use-bulk-copy-functions-directly-on-program-variables"></a><span data-ttu-id="3aa81-110">プログラム変数に対して一括コピー関数を直接使用するには</span><span class="sxs-lookup"><span data-stu-id="3aa81-110">To use bulk copy functions directly on program variables</span></span>  
  
1.  <span data-ttu-id="3aa81-111">環境ハンドルおよび接続ハンドルを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="3aa81-111">Allocate an environment handle and a connection handle.</span></span>  
  
2.  <span data-ttu-id="3aa81-112">一括コピー操作が有効になるように SQL_COPT_SS_BCP および SQL_BCP_ON を設定します。</span><span class="sxs-lookup"><span data-stu-id="3aa81-112">Set SQL_COPT_SS_BCP and SQL_BCP_ON to enable bulk copy operations.</span></span>  
  
3.  <span data-ttu-id="3aa81-113">SQL Server に接続します。</span><span class="sxs-lookup"><span data-stu-id="3aa81-113">Connect to SQL Server.</span></span>  
  
4.  <span data-ttu-id="3aa81-114">[Bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)を呼び出して、次の情報を設定します。</span><span class="sxs-lookup"><span data-stu-id="3aa81-114">Call [bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) to set the following information:</span></span>  
  
    -   <span data-ttu-id="3aa81-115">一括コピー操作の対象になるテーブルまたはビューの名前</span><span class="sxs-lookup"><span data-stu-id="3aa81-115">The name of the table or view to bulk copy from or to.</span></span>  
  
    -   <span data-ttu-id="3aa81-116">データ ファイルの名前には NULL を指定します。</span><span class="sxs-lookup"><span data-stu-id="3aa81-116">Specify NULL for the name of the data file.</span></span>  
  
    -   <span data-ttu-id="3aa81-117">一括コピー エラー メッセージを受け取るデータ ファイルの名前 (メッセージ ファイルを使用しない場合は NULL を指定します)。</span><span class="sxs-lookup"><span data-stu-id="3aa81-117">The name of an data file to receive any bulk copy error messages (specify NULL if you do not want a message file).</span></span>  
  
    -   <span data-ttu-id="3aa81-118">コピーの方向 (アプリケーションからビューまたはテーブルへのコピーの場合は DB_IN、テーブルまたはビューからアプリケーションへのコピーの場合は DB_OUT)。</span><span class="sxs-lookup"><span data-stu-id="3aa81-118">The direction of the copy: DB_IN from the application to the view or table or DB_OUT to the application from the table or view.</span></span>  
  
5.  <span data-ttu-id="3aa81-119">一括コピーの各列に対して[bcp_bind](../../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)を呼び出して、列をプログラム変数にバインドします。</span><span class="sxs-lookup"><span data-stu-id="3aa81-119">Call [bcp_bind](../../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) for each column in the bulk copy to bind the column to a program variable.</span></span>  
  
6.  <span data-ttu-id="3aa81-120">プログラム変数にデータを入力し、 [bcp_sendrow](../../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)を呼び出してデータ行を送信します。</span><span class="sxs-lookup"><span data-stu-id="3aa81-120">Fill the program variables with data, and call [bcp_sendrow](../../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) to send a row of data.</span></span>  
  
7.  <span data-ttu-id="3aa81-121">複数の行が送信された後、 [bcp_batch](../../native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md)を呼び出して、既に送信されている行をチェックポイントします。</span><span class="sxs-lookup"><span data-stu-id="3aa81-121">After several rows have been sent, call [bcp_batch](../../native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) to checkpoint the rows already sent.</span></span> <span data-ttu-id="3aa81-122">1000行ごとに少なくとも1回は[bcp_batch](../../native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md)を呼び出すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3aa81-122">It is good practice to call [bcp_batch](../../native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) at least once per 1000 rows.</span></span>  
  
8.  <span data-ttu-id="3aa81-123">すべての行が送信されたら、 [bcp_done](../../native-client-odbc-extensions-bulk-copy-functions/bcp-done.md)を呼び出して操作を完了します。</span><span class="sxs-lookup"><span data-stu-id="3aa81-123">After all rows have been sent, call [bcp_done](../../native-client-odbc-extensions-bulk-copy-functions/bcp-done.md) to complete the operation.</span></span>  
  
 <span data-ttu-id="3aa81-124">一括コピー操作中に、 [bcp_colptr](../../native-client-odbc-extensions-bulk-copy-functions/bcp-colptr.md)と[bcp_collen](../../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)を呼び出すことによって、プログラム変数の場所と長さを変更できます。</span><span class="sxs-lookup"><span data-stu-id="3aa81-124">You can vary the location and length of program variables during a bulk copy operation by calling [bcp_colptr](../../native-client-odbc-extensions-bulk-copy-functions/bcp-colptr.md) and [bcp_collen](../../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md).</span></span> <span data-ttu-id="3aa81-125">[Bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)を使用して、さまざまな一括コピーオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="3aa81-125">Use [bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) to set various bulk copy options.</span></span> <span data-ttu-id="3aa81-126">、 [bcp_moretext](../../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) 、 `text` `ntext` および `image` データをセグメント内のサーバーに送信するには、bcp_moretext を使用します。</span><span class="sxs-lookup"><span data-stu-id="3aa81-126">Use [bcp_moretext](../../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) to send `text`, `ntext`, and `image` data in segments to the server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3aa81-127">例</span><span class="sxs-lookup"><span data-stu-id="3aa81-127">Example</span></span>  
 <span data-ttu-id="3aa81-128">このサンプルは IA64 ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="3aa81-128">This sample is not supported on IA64.</span></span>  
  
 <span data-ttu-id="3aa81-129">AdventureWorks と呼ばれる ODBC データ ソース (既定のデータベースは AdventureWorks サンプル データベース) が必要です </span><span class="sxs-lookup"><span data-stu-id="3aa81-129">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="3aa81-130">(AdventureWorks サンプルデータベースは、 [Microsoft SQL Server のサンプルとコミュニティのプロジェクト](https://go.microsoft.com/fwlink/?LinkID=85384)のホームページからダウンロードできます)。このデータソースは、オペレーティングシステムによって提供される ODBC ドライバーに基づいている必要があります (ドライバー名は "SQL Server")。</span><span class="sxs-lookup"><span data-stu-id="3aa81-130">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="3aa81-131">このサンプルを 64 ビット オペレーティング システムで 32 ビット アプリケーションとしてビルドし、実行する場合、%windir%\SysWOW64\odbcad32.exe の ODBC アドミニストレーターを使用して ODBC データ ソースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3aa81-131">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="3aa81-132">このサンプルでは、コンピューターの既定の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="3aa81-132">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="3aa81-133">名前付きインスタンスに接続するには、ODBC データ ソースの定義を変更し、server\namedinstance 形式でそのインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="3aa81-133">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="3aa81-134">[!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] は、既定で名前付きインスタンスとしてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="3aa81-134">By default, [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="3aa81-135">最初の ( [!INCLUDE[tsql](../../../includes/tsql-md.md)] ) コードリストを実行して、サンプルで使用するテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="3aa81-135">Execute the first ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) code listing to create tables that the sample will use.</span></span>  
  
 <span data-ttu-id="3aa81-136">odbc32.lib と odbcbcp.lib を使用して 2 つ目の (C++) コード リストをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="3aa81-136">Compile the second (C++) code listing with odbc32.lib and odbcbcp.lib.</span></span> <span data-ttu-id="3aa81-137">MSBuild.exe でビルドした場合は、まずプロジェクト ディレクトリの Bcpfmt.fmt と Bcpodbc.bcp を .exe があるディレクトリにコピーし、次に .exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="3aa81-137">If you built with MSBuild.exe, copy Bcpfmt.fmt and Bcpodbc.bcp from the project directory into the directory with the .exe and then invoke the .exe.</span></span>  
  
 <span data-ttu-id="3aa81-138">3番目の ( [!INCLUDE[tsql](../../../includes/tsql-md.md)] ) コードリストを実行して、サンプルで使用したテーブルを削除します。</span><span class="sxs-lookup"><span data-stu-id="3aa81-138">Execute the third ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) code listing to delete the tables that the sample used.</span></span>  
  
```  
// compile with: odbc32.lib odbcbcp.lib  
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPSource')  
     DROP TABLE BCPSource  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPTarget')  
     DROP TABLE BCPTarget  
GO  
  
CREATE TABLE BCPSource (cola int PRIMARY KEY, colb CHAR(10) NULL)  
INSERT INTO BCPSource (cola, colb) VALUES (1, 'aaa')  
INSERT INTO BCPSource (cola, colb) VALUES (2, 'bbb')  
CREATE TABLE BCPTarget (cola int PRIMARY KEY, colb CHAR(10) NULL)  
```  
  
```  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
SQLHENV henv = SQL_NULL_HENV;  
HDBC hdbc1 = SQL_NULL_HDBC, hdbc2 = SQL_NULL_HDBC;  
SQLHSTMT hstmt2 = SQL_NULL_HSTMT;  
  
void Cleanup() {  
   if (hstmt2 != SQL_NULL_HSTMT)  
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt2);  
  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (hdbc2 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc2);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc2);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
  
   // BCP variables.  
   char *terminator = "\0";  
  
   // bcp_done takes a different format return code because it returns number of rows bulk copied  
   // after the last bcp_batch call.  
   DBINT cRowsDone = 0;  
  
   // Set up separate return code for bcp_sendrow so it is not using the same retcode as SQLFetch.  
   RETCODE SendRet;  
  
   // Column variables.  cbCola and cbColb must be defined right before Cola and szColb because   
   // they are used as bulk copy indicator variables.  
   struct ColaData {  
      int cbCola;  
      SQLINTEGER Cola;  
   } ColaInst;  
  
   struct ColbData {  
      int cbColb;  
      SQLCHAR szColb[11];  
   } ColbInst;  
  
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
  
   // Allocate ODBC connection handle, set bulk copy mode, and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLSetConnectAttr(hdbc1, SQL_COPT_SS_BCP, (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetConnectAttr(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // sample uses Integrated Security, create the SQL Server DSN using Windows NT authentication  
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Initialize the bulk copy.  
   retcode = bcp_init(hdbc1, "AdventureWorks..BCPTarget", NULL, NULL, DB_IN);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_init(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Bind the program variables for the bulk copy.  
   retcode = bcp_bind(hdbc1, (BYTE *)&ColaInst.cbCola, 4, SQL_VARLEN_DATA, NULL, (INT)NULL, SQLINT4, 1);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_bind(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Could normally use strlen to calculate the bcp_bind cbTerm parameter, but this terminator   
   // is a null byte (\0), which gives strlen a value of 0. Explicitly give cbTerm a value of 1.  
   retcode = bcp_bind(hdbc1, (BYTE *)&ColbInst.cbColb, 4, 11, (UCHAR*)terminator, 1, SQLCHARACTER, 2);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_bind(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate second ODBC connection handle so bulk copy and cursor operations do not conflict.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc2);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc2) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample uses Integrated Security, create SQL Server DSN using Windows NT authentication.   
   retcode = SQLConnect(hdbc2, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate ODBC statement handle.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc2, &hstmt2);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hstmt2) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
SQLLEN lDataLengthA;  
SQLLEN lDataLengthB;  
  
   // Bind the SELECT statement to the same program variables bound to the bulk copy operation.  
   retcode = SQLBindCol(hstmt2, 1, SQL_C_SLONG, &ColaInst.Cola, 0, &lDataLengthA);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLBindCol(hstmt2) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLBindCol(hstmt2, 2, SQL_C_CHAR, &ColbInst.szColb, 11, &lDataLengthB);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLBindCol(hstmt2) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute SELECT statement to build a cursor containing data to be bulk copied to new table.  
   retcode = SQLExecDirect(hstmt2, (UCHAR*)"SELECT * FROM BCPSource", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
   // Go into a loop fetching rows from the cursor until each row is fetched. Because the   
   // bcp_bind calls and SQLBindCol calls each reference the same variables, each fetch fills   
   // the variables used by bcp_sendrow, so all you have to do to send the data to SQL Server is   
   // to call bcp_sendrow.  
   while ( (retcode = SQLFetch(hstmt2) ) != SQL_NO_DATA) {  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLFetch Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
  
      ColaInst.cbCola = (int)lDataLengthA;  
      ColbInst.cbColb = (int)lDataLengthB;  
  
     if ( (SendRet = bcp_sendrow(hdbc1) ) != SUCCEED ) {  
         printf("bcp_sendrow(hdbc1) Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Signal the end of the bulk copy operation.  
   cRowsDone = bcp_done(hdbc1);  
   if ( (cRowsDone == -1) ) {  
      printf("bcp_done(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("Number of rows bulk copied after last bcp_batch call = %d.\n", cRowsDone);  
  
   // Cleanup.  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt2);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLDisconnect(hdbc2);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc2);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
```  
  
```  
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPSource')  
     DROP TABLE BCPSource  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPTarget')  
     DROP TABLE BCPTarget  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="3aa81-139">参照</span><span class="sxs-lookup"><span data-stu-id="3aa81-139">See Also</span></span>  
 <span data-ttu-id="3aa81-140">[SQL Server ODBC ドライバーを使用した一括コピーの操作方法に関するトピック &#40;ODBC&#41;](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="3aa81-140">[Bulk Copying with the SQL Server ODBC Driver How-to Topics &#40;ODBC&#41;](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md) </span></span>  
 [<span data-ttu-id="3aa81-141">プログラム変数からの一括コピー</span><span class="sxs-lookup"><span data-stu-id="3aa81-141">Bulk Copying from Program Variables</span></span>](../../native-client-odbc-bulk-copy-operations/bulk-copying-from-program-variables.md)  
  
  
