---
title: 一括コピーフォーマットファイルを作成する (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], file formats
- bulk copy [ODBC], data files
ms.assetid: 0572fef3-daf5-409e-b557-c2a632f9a06d
author: rothja
ms.author: jroth
ms.openlocfilehash: 9d35342b2f6b25a129df968383d204931d64bfa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631884"
---
# <a name="create-a-bulk-copy-format-file-odbc"></a><span data-ttu-id="e852b-102">一括コピー フォーマット ファイル (ODBC) の作成</span><span class="sxs-lookup"><span data-stu-id="e852b-102">Create a Bulk Copy Format File (ODBC)</span></span>
  <span data-ttu-id="e852b-103">このサンプルでは、一括コピー関数を使用してデータ ファイルとフォーマット ファイルの両方を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e852b-103">This sample shows how to use bulk copy functions to create both a data file and a format file.</span></span> <span data-ttu-id="e852b-104">このサンプルは、ODBC 3.0 以降のバージョン用に開発されました。</span><span class="sxs-lookup"><span data-stu-id="e852b-104">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e852b-105">可能な場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="e852b-105">When possible, use Windows Authentication.</span></span> <span data-ttu-id="e852b-106">Windows 認証が使用できない場合は、実行時に資格情報を入力するようユーザーに求めます。</span><span class="sxs-lookup"><span data-stu-id="e852b-106">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="e852b-107">資格情報をファイルに保存するのは避けてください。</span><span class="sxs-lookup"><span data-stu-id="e852b-107">Avoid storing credentials in a file.</span></span> <span data-ttu-id="e852b-108">資格情報を保持する必要がある場合は、[Win32 Crypto API](https://go.microsoft.com/fwlink/?LinkId=64532) を使用して暗号化してください。</span><span class="sxs-lookup"><span data-stu-id="e852b-108">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-create-a-bulk-copy-format-file"></a><span data-ttu-id="e852b-109">一括コピー フォーマット ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="e852b-109">To create a bulk copy format file</span></span>  
  
1.  <span data-ttu-id="e852b-110">環境ハンドルおよび接続ハンドルを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e852b-110">Allocate an environment handle and a connection handle.</span></span>  
  
2.  <span data-ttu-id="e852b-111">一括コピー操作が有効になるように SQL_COPT_SS_BCP および SQL_BCP_ON を設定します。</span><span class="sxs-lookup"><span data-stu-id="e852b-111">Set SQL_COPT_SS_BCP and SQL_BCP_ON to enable bulk copy operations.</span></span>  
  
3.  <span data-ttu-id="e852b-112">SQL Server に接続します。</span><span class="sxs-lookup"><span data-stu-id="e852b-112">Connect to SQL Server.</span></span>  
  
4.  <span data-ttu-id="e852b-113">[Bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)を呼び出して、次の情報を設定します。</span><span class="sxs-lookup"><span data-stu-id="e852b-113">Call [bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) to set the following information:</span></span>  
  
    -   <span data-ttu-id="e852b-114">一括コピー操作の対象になるテーブルまたはビューの名前</span><span class="sxs-lookup"><span data-stu-id="e852b-114">The name of the table or view to bulk copy from or to.</span></span>  
  
    -   <span data-ttu-id="e852b-115">データベースにコピーするデータが含まれたデータ ファイルの名前、またはデータベースからのコピー時にデータを受け取るデータ ファイルの名前</span><span class="sxs-lookup"><span data-stu-id="e852b-115">The name of the data file that contains the data to copy into the database or that receives data when copying from the database.</span></span>  
  
    -   <span data-ttu-id="e852b-116">一括コピー エラー メッセージを受信するデータ ファイルの名前 (メッセージ ファイルが不要な場合は NULL を指定)。</span><span class="sxs-lookup"><span data-stu-id="e852b-116">The name of a data file to receive any bulk copy error messages (specify NULL if you do not want a message file).</span></span>  
  
    -   <span data-ttu-id="e852b-117">コピーの方向 (テーブルまたはビューからファイルへのコピーの場合は DB_OUT)</span><span class="sxs-lookup"><span data-stu-id="e852b-117">The direction of the copy: DB_OUT to the file from the table or view.</span></span>  
  
5.  <span data-ttu-id="e852b-118">[Bcp_columns](../../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)を呼び出して、列の数を設定します。</span><span class="sxs-lookup"><span data-stu-id="e852b-118">Call [bcp_columns](../../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) to set the number of columns.</span></span>  
  
6.  <span data-ttu-id="e852b-119">各列に対して[bcp_colfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)を呼び出して、データファイル内の特性を定義します。</span><span class="sxs-lookup"><span data-stu-id="e852b-119">Call [bcp_colfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) for each column to define its characteristics in the data file.</span></span>  
  
7.  <span data-ttu-id="e852b-120">[Bcp_writefmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md)を呼び出して、一括コピー操作によって作成されるデータファイルを記述するフォーマットファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="e852b-120">Call [bcp_writefmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md) to create a format file describing the data file to be created by the bulk copy operation.</span></span>  
  
8.  <span data-ttu-id="e852b-121">[Bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)を呼び出して、一括コピー操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="e852b-121">Call [bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) to execute the bulk copy operation.</span></span>  
  
 <span data-ttu-id="e852b-122">このように一括コピー操作を実行すると、一括コピーされたデータが含まれたデータ ファイルとデータ ファイルのレイアウトが記述されたフォーマット ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e852b-122">A bulk copy operation run in this way creates both a data file containing the bulk copied data and a format file describing the layout of the data file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e852b-123">例</span><span class="sxs-lookup"><span data-stu-id="e852b-123">Example</span></span>  
 <span data-ttu-id="e852b-124">AdventureWorks と呼ばれる ODBC データ ソース (既定のデータベースは AdventureWorks サンプル データベース) が必要です </span><span class="sxs-lookup"><span data-stu-id="e852b-124">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="e852b-125">(AdventureWorks サンプルデータベースは、 [Microsoft SQL Server のサンプルとコミュニティのプロジェクト](https://go.microsoft.com/fwlink/?LinkID=85384)のホームページからダウンロードできます)。このデータソースは、オペレーティングシステムによって提供される ODBC ドライバーに基づいている必要があります (ドライバー名は "SQL Server")。</span><span class="sxs-lookup"><span data-stu-id="e852b-125">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="e852b-126">このサンプルを 64 ビット オペレーティング システムで 32 ビット アプリケーションとしてビルドし、実行する場合、%windir%\SysWOW64\odbcad32.exe の ODBC アドミニストレーターを使用して ODBC データ ソースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e852b-126">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="e852b-127">このサンプルでは、コンピューターの既定の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e852b-127">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="e852b-128">名前付きインスタンスに接続するには、ODBC データ ソースの定義を変更し、server\namedinstance 形式でそのインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="e852b-128">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="e852b-129">[!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] は、既定で名前付きインスタンスとしてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="e852b-129">By default, [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="e852b-130">最初の ( [!INCLUDE[tsql](../../../includes/tsql-md.md)] ) コードリストを実行して、サンプルで使用するテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="e852b-130">Execute the first ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) code listing to create the table that the sample will use.</span></span>  
  
 <span data-ttu-id="e852b-131">odbc32.lib と odbcbcp.lib を使用して 2 つ目の (C++) コード リストをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="e852b-131">Compile the second (C++) code listing with odbc32.lib and odbcbcp.lib.</span></span>  
  
 <span data-ttu-id="e852b-132">3 つ目の ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) コード リストを実行して、サンプルで使用したテーブルを削除します。</span><span class="sxs-lookup"><span data-stu-id="e852b-132">Execute the third ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) code listing to delete the table that the sample used.</span></span>  
  
```  
use AdventureWorks  
  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPDate')  
     DROP TABLE BCPDate  
GO  
  
CREATE TABLE BCPDate (cola int, colb datetime)  
insert BCPDate(cola) values(1)   
insert BCPDate(cola) values(2)   
insert BCPDate(cola) values(3)   
insert BCPDate(cola) values(4)  
```  
  
```  
// compile with: odbc32.lib odbcbcp.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
SQLHENV henv = SQL_NULL_HENV;  
HDBC hdbc1 = SQL_NULL_HDBC;    
  
void Cleanup() {  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
  
   // BCP variables.  
   SDWORD cRows;  
  
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
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample uses Integrated Security, create SQL Server DSN using Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Initialize the bulk copy.  
   retcode = bcp_init(hdbc1, "BCPDate", "BCPODBC.bcp", NULL, DB_OUT);  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set the number of output columns.  
   retcode = bcp_columns(hdbc1, 2);  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Describe the format of column 1 in the data file.  
   retcode = bcp_colfmt(hdbc1, 1, SQLCHARACTER, -1, 5, NULL, 0, 1);  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Describe the format of column 2 in the data file.  
   retcode = bcp_colfmt(hdbc1, 2, SQLCHARACTER, -1, 20, NULL, 0, 2);  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Create the format file.  
   retcode = bcp_writefmt(hdbc1, "c:\\BCPFMT.fmt");  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the bulk copy.  
   retcode = bcp_exec(hdbc1, &cRows);  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("Number of rows bulk copied out = %d.\n", cRows);  
  
   // Cleanup  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
   return(0);  
}  
```  
  
```  
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPDate')  
     DROP TABLE BCPDate  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="e852b-133">参照</span><span class="sxs-lookup"><span data-stu-id="e852b-133">See Also</span></span>  
 <span data-ttu-id="e852b-134">[SQL Server ODBC ドライバーを使用した一括コピーの操作方法に関するトピック &#40;ODBC&#41;](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="e852b-134">[Bulk Copying with the SQL Server ODBC Driver How-to Topics &#40;ODBC&#41;](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md) </span></span>  
 [<span data-ttu-id="e852b-135">データ ファイルとフォーマット ファイルの使用</span><span class="sxs-lookup"><span data-stu-id="e852b-135">Using Data Files and Format Files</span></span>](../../native-client-odbc-bulk-copy-operations/using-data-files-and-format-files.md)  
  
  
