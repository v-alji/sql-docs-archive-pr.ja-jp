---
title: フォーマットファイルを使用した一括コピー (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy using format file [ODBC]
- ODBC, bulk copy operations
ms.assetid: 970fd3af-f918-4fc3-a5b1-92596515d4de
author: rothja
ms.author: jroth
ms.openlocfilehash: 19959d5f1da7243275c60560963d577446f809b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741998"
---
# <a name="bulk-copy-by-using-a-format-file-odbc"></a><span data-ttu-id="73e29-102">フォーマット ファイルを使用した一括コピー (ODBC)</span><span class="sxs-lookup"><span data-stu-id="73e29-102">Bulk Copy by Using a Format File (ODBC)</span></span>
  <span data-ttu-id="73e29-103">このサンプルでは、ODBC bcp_init 関数をフォーマット ファイルと共に使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="73e29-103">This sample shows how to use the ODBC bcp_init function with a format file.</span></span>  
  
### <a name="to-bulk-copy-by-using-a-format-file"></a><span data-ttu-id="73e29-104">フォーマット ファイルを使用して一括コピーするには</span><span class="sxs-lookup"><span data-stu-id="73e29-104">To bulk copy by using a format file</span></span>  
  
1.  <span data-ttu-id="73e29-105">環境ハンドルおよび接続ハンドルを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="73e29-105">Allocate an environment handle and a connection handle.</span></span>  
  
2.  <span data-ttu-id="73e29-106">一括コピー操作が有効になるように SQL_COPT_SS_BCP および SQL_BCP_ON を設定します。</span><span class="sxs-lookup"><span data-stu-id="73e29-106">Set SQL_COPT_SS_BCP and SQL_BCP_ON to enable bulk copy operations.</span></span>  
  
3.  <span data-ttu-id="73e29-107">Microsoft SQL Server に接続します。</span><span class="sxs-lookup"><span data-stu-id="73e29-107">Connect to Microsoft SQL Server.</span></span>  
  
4.  <span data-ttu-id="73e29-108">[Bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)を呼び出して、次の情報を設定します。</span><span class="sxs-lookup"><span data-stu-id="73e29-108">Call [bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) to set the following information:</span></span>  
  
    -   <span data-ttu-id="73e29-109">一括コピー操作の対象になるテーブルまたはビューの名前</span><span class="sxs-lookup"><span data-stu-id="73e29-109">The name of the table or view to bulk copy from or to.</span></span>  
  
    -   <span data-ttu-id="73e29-110">データベースにコピーするデータが含まれたデータ ファイルの名前、またはデータベースからのコピー時にデータを受け取るデータ ファイルの名前</span><span class="sxs-lookup"><span data-stu-id="73e29-110">The name of the data file that contains the data to copy into the database or that receives data when copying from the database.</span></span>  
  
    -   <span data-ttu-id="73e29-111">一括コピー エラー メッセージを受信するデータ ファイルの名前 (メッセージ ファイルが不要な場合は NULL を指定)。</span><span class="sxs-lookup"><span data-stu-id="73e29-111">The name of a data file to receive any bulk copy error messages (specify NULL if you do not want a message file).</span></span>  
  
    -   <span data-ttu-id="73e29-112">コピーの方向 (ファイルからテーブルまたはビューへのコピーの場合は DB_IN)</span><span class="sxs-lookup"><span data-stu-id="73e29-112">The direction of the copy: DB_IN from the file to the table or view.</span></span>  
  
5.  <span data-ttu-id="73e29-113">[Bcp_readfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)を呼び出して、一括コピー操作で使用されるデータファイルを記述するフォーマットファイルを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="73e29-113">Call [bcp_readfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) to read the format file describing the data file to be used by the bulk copy operation.</span></span>  
  
6.  <span data-ttu-id="73e29-114">[Bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)を呼び出して、一括コピー操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="73e29-114">Call [bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) to execute the bulk copy operation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73e29-115">例</span><span class="sxs-lookup"><span data-stu-id="73e29-115">Example</span></span>  
 <span data-ttu-id="73e29-116">このサンプルは IA64 ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="73e29-116">This sample is not supported on IA64.</span></span>  
  
 <span data-ttu-id="73e29-117">AdventureWorks と呼ばれる ODBC データ ソース (既定のデータベースは AdventureWorks サンプル データベース) が必要です </span><span class="sxs-lookup"><span data-stu-id="73e29-117">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="73e29-118">(AdventureWorks サンプルデータベースは、 [Microsoft SQL Server のサンプルとコミュニティのプロジェクト](https://go.microsoft.com/fwlink/?LinkID=85384)のホームページからダウンロードできます)。このデータソースは、オペレーティングシステムによって提供される ODBC ドライバーに基づいている必要があります (ドライバー名は "SQL Server")。</span><span class="sxs-lookup"><span data-stu-id="73e29-118">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="73e29-119">このサンプルを 64 ビット オペレーティング システムで 32 ビット アプリケーションとしてビルドし、実行する場合、%windir%\SysWOW64\odbcad32.exe の ODBC アドミニストレーターを使用して ODBC データ ソースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73e29-119">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="73e29-120">このサンプルでは、コンピューターの既定の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="73e29-120">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="73e29-121">名前付きインスタンスに接続するには、ODBC データ ソースの定義を変更し、server\namedinstance 形式でそのインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="73e29-121">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="73e29-122">[!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] は、既定で名前付きインスタンスとしてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="73e29-122">By default, [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="73e29-123">最初の ( [!INCLUDE[tsql](../../../includes/tsql-md.md)] ) コードリストを実行して、サンプルで使用するテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="73e29-123">Execute the first ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) code listing to create the table that the sample will use.</span></span>  
  
 <span data-ttu-id="73e29-124">2 つ目のコード リストをコピーし、Bcpfmt.fmt という名前のファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="73e29-124">Copy the second code listing and paste it into a file called Bcpfmt.fmt.</span></span> <span data-ttu-id="73e29-125">テーブルの各列はタブ文字で区切られています。</span><span class="sxs-lookup"><span data-stu-id="73e29-125">Each column in the table is separated by a tab character.</span></span>  
  
 <span data-ttu-id="73e29-126">3 つ目のコード リストをコピーし、Bcpodbc.bcp という名前のファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="73e29-126">Copy the third code listing and paste it into a file called Bcpodbc.bcp.</span></span> <span data-ttu-id="73e29-127">ファイル内の各キャリッジ リターンの前にはタブ文字があります。</span><span class="sxs-lookup"><span data-stu-id="73e29-127">A tab character precedes each carriage return in the file.</span></span>  
  
 <span data-ttu-id="73e29-128">odbc32.lib と odbcbcp.lib を使用して 4 つ目の (C++) コード リストをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="73e29-128">Compile the fourth (C++) code listing with odbc32.lib and odbcbcp.lib.</span></span> <span data-ttu-id="73e29-129">MSBuild.exe でビルドした場合は、まずプロジェクト ディレクトリの Bcpfmt.fmt と Bcpodbc.bcp を .exe があるディレクトリにコピーし、次に .exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="73e29-129">If you built with MSBuild.exe, copy Bcpfmt.fmt and Bcpodbc.bcp from the project directory into the directory with the .exe and then invoke the .exe.</span></span>  
  
 <span data-ttu-id="73e29-130">5 つ目の ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) コード リストを実行して、サンプルで使用したテーブルを削除します。</span><span class="sxs-lookup"><span data-stu-id="73e29-130">Execute the fifth ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) code listing to delete the table that the sample used.</span></span>  
  
```sql
use AdventureWorks  
CREATE TABLE BCPDate (cola int, colb datetime)  
```  
  
```  
8.0  
2  
1SQLCHAR04"\t"1colaSQL_Latin1_General_Cp437_Bin  
2SQLCHAR08"\r\n"2colbSQL_Latin1_General_Cp437_Bin  
```  
  
```  
1  
2  
```  
  
```cpp
// compile with: odbc32.lib odbcbcp.lib  
#include <stdio.h>  
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
  
   // Allocate ODBC connection handle, set BCP mode, and connect.  
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
  
   // Sample uses Integrated Security. Create SQL Server DSN using Windows NT authentication.  
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Initialize the bulk copy.  
   retcode = bcp_init(hdbc1, "BCPDate", "BCPODBC.bcp", NULL, DB_IN);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_init(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Read the format file.  
   retcode = bcp_readfmt(hdbc1, "BCPFMT.fmt");  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_readfmt(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the bulk copy.  
   retcode = bcp_exec(hdbc1, &cRows);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_exec(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("Number of rows bulk copied in = %d.\n", cRows);  
  
   // Cleanup  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
```sql
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPDate')  
     DROP TABLE BCPDate  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="73e29-131">参照</span><span class="sxs-lookup"><span data-stu-id="73e29-131">See Also</span></span>  
 <span data-ttu-id="73e29-132">[SQL Server ODBC ドライバーを使用した一括コピーの操作方法に関するトピック &#40;ODBC&#41;](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="73e29-132">[Bulk Copying with the SQL Server ODBC Driver How-to Topics &#40;ODBC&#41;](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md) </span></span>  
 [<span data-ttu-id="73e29-133">データ ファイルとフォーマット ファイルの使用</span><span class="sxs-lookup"><span data-stu-id="73e29-133">Using Data Files and Format Files</span></span>](../../native-client-odbc-bulk-copy-operations/using-data-files-and-format-files.md)  
  
  
