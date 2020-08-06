---
title: フォーマットファイルを使用しない一括コピー (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], file formats
- bulk copy [ODBC]
- bulk copy [ODBC], data files
- bulk copy [ODBC], about bulk copy
ms.assetid: 4ee969a7-44ba-40d0-b9ab-8306f1a2b19d
author: rothja
ms.author: jroth
ms.openlocfilehash: a65f013d92f5a5d39a580cfb3a9bd77bc6f84e9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741989"
---
# <a name="bulk-copy-without-a-format-file-odbc"></a><span data-ttu-id="58332-102">フォーマット ファイルを使用しない一括コピー (ODBC)</span><span class="sxs-lookup"><span data-stu-id="58332-102">Bulk Copy Without a Format File (ODBC)</span></span>
  <span data-ttu-id="58332-103">このサンプルでは、フォーマット ファイルを使用せずに、一括コピー関数を使用してネイティブ モード データ ファイルを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="58332-103">This sample shows how to use bulk copy functions to create a native mode data file, without a format file.</span></span> <span data-ttu-id="58332-104">このサンプルは、ODBC 3.0 以降のバージョン用に開発されました。</span><span class="sxs-lookup"><span data-stu-id="58332-104">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="58332-105">可能な場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="58332-105">When possible, use Windows Authentication.</span></span> <span data-ttu-id="58332-106">Windows 認証が使用できない場合は、実行時に資格情報を入力するようユーザーに求めます。</span><span class="sxs-lookup"><span data-stu-id="58332-106">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="58332-107">資格情報をファイルに保存するのは避けてください。</span><span class="sxs-lookup"><span data-stu-id="58332-107">Avoid storing credentials in a file.</span></span> <span data-ttu-id="58332-108">資格情報を保持する必要がある場合は、[Win32 Crypto API](https://go.microsoft.com/fwlink/?LinkId=64532) を使用して暗号化してください。</span><span class="sxs-lookup"><span data-stu-id="58332-108">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-bulk-copy-without-a-format-file"></a><span data-ttu-id="58332-109">フォーマット ファイルを使用せずに一括コピーするには</span><span class="sxs-lookup"><span data-stu-id="58332-109">To bulk copy without a format file</span></span>  
  
1.  <span data-ttu-id="58332-110">環境ハンドルおよび接続ハンドルを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="58332-110">Allocate an environment handle and a connection handle.</span></span>  
  
2.  <span data-ttu-id="58332-111">一括コピー操作が有効になるように SQL_COPT_SS_BCP および SQL_BCP_ON を設定します。</span><span class="sxs-lookup"><span data-stu-id="58332-111">Set SQL_COPT_SS_BCP and SQL_BCP_ON to enable bulk copy operations.</span></span>  
  
3.  <span data-ttu-id="58332-112">SQL Server に接続します。</span><span class="sxs-lookup"><span data-stu-id="58332-112">Connect to SQL Server.</span></span>  
  
4.  <span data-ttu-id="58332-113">[Bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)を呼び出して、次の情報を設定します。</span><span class="sxs-lookup"><span data-stu-id="58332-113">Call [bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) to set the following information:</span></span>  
  
    -   <span data-ttu-id="58332-114">一括コピー操作の対象になるテーブルまたはビューの名前</span><span class="sxs-lookup"><span data-stu-id="58332-114">The name of the table or view to bulk copy from or to.</span></span>  
  
    -   <span data-ttu-id="58332-115">データベースにコピーするデータが含まれたデータ ファイルの名前、またはデータベースからのコピー時にデータを受け取るデータ ファイルの名前</span><span class="sxs-lookup"><span data-stu-id="58332-115">The name of the data file that contains the data to copy into the database or that receives data when copying from the database.</span></span>  
  
    -   <span data-ttu-id="58332-116">一括コピー エラー メッセージを受信するデータ ファイルの名前 (メッセージ ファイルが不要な場合は NULL を指定)。</span><span class="sxs-lookup"><span data-stu-id="58332-116">The name of a data file to receive any bulk copy error messages (specify NULL if you do not want a message file).</span></span>  
  
    -   <span data-ttu-id="58332-117">コピーの方向 (ファイルからビューまたはテーブルへのコピーの場合は DB_IN、テーブルまたはビューからファイルへのコピーの場合は DB_OUT)</span><span class="sxs-lookup"><span data-stu-id="58332-117">The direction of the copy: DB_IN from the file to the view or table, or DB_OUT to the file from the table or view.</span></span>  
  
5.  <span data-ttu-id="58332-118">[Bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)を呼び出して、一括コピー操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="58332-118">Call [bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) to execute the bulk copy operation.</span></span>  
  
 <span data-ttu-id="58332-119">これらの手順で DB_OUT を設定すると、ファイルはネイティブ形式で作成されます。</span><span class="sxs-lookup"><span data-stu-id="58332-119">When DB_OUT is set with these steps, the file is created in native format.</span></span> <span data-ttu-id="58332-120">その後、以下の同様の手順を使用して、このファイルをサーバーに一括コピーできます。ただし、DB_IN ではなく DB_OUT が設定されます。</span><span class="sxs-lookup"><span data-stu-id="58332-120">The file can then be bulk copied into a server by following these same steps, except that DB_OUT is set instead of DB_IN.</span></span> <span data-ttu-id="58332-121">この操作は、コピー元のテーブルとコピー先のテーブルの構造が厳密に同じ場合にのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="58332-121">This works only if both the source and target tables have exactly the same structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58332-122">例</span><span class="sxs-lookup"><span data-stu-id="58332-122">Example</span></span>  
 <span data-ttu-id="58332-123">このサンプルは IA64 ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="58332-123">This sample is not supported on IA64.</span></span>  
  
 <span data-ttu-id="58332-124">AdventureWorks と呼ばれる ODBC データ ソース (既定のデータベースは AdventureWorks サンプル データベース) が必要です </span><span class="sxs-lookup"><span data-stu-id="58332-124">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="58332-125">(AdventureWorks サンプルデータベースは、 [Microsoft SQL Server のサンプルとコミュニティのプロジェクト](https://go.microsoft.com/fwlink/?LinkID=85384)のホームページからダウンロードできます)。このデータソースは、オペレーティングシステムによって提供される ODBC ドライバーに基づいている必要があります (ドライバー名は "SQL Server")。</span><span class="sxs-lookup"><span data-stu-id="58332-125">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="58332-126">このサンプルを 64 ビット オペレーティング システムで 32 ビット アプリケーションとしてビルドし、実行する場合、%windir%\SysWOW64\odbcad32.exe の ODBC アドミニストレーターを使用して ODBC データ ソースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58332-126">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="58332-127">このサンプルでは、コンピューターの既定の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="58332-127">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="58332-128">名前付きインスタンスに接続するには、ODBC データ ソースの定義を変更し、server\namedinstance 形式でそのインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="58332-128">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="58332-129">[!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] は、既定で名前付きインスタンスとしてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="58332-129">By default, [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="58332-130">odbc32.lib と odbcbcp.lib を使用してコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="58332-130">Compile with odbc32.lib and odbcbcp.lib.</span></span>  
  
```  
// compile with: odbc32.lib odbcbcp.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
#define MAXBUFLEN 256  
  
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
  
   // Bulk copy variables.  
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
  
   // Allocate ODBC connection handle, set bulk copy mode, and then connect.  
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
  
   // Sample uses Integrated Security, create the SQL Server DSN using Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Initialize the bulk copy.  
   retcode = bcp_init(hdbc1, "Purchasing.Vendor", "BCPODBC.bcp", "BCPERROR.out", DB_OUT);  
   // Test is for the bulk copy return of SUCCEED, not the ODBC return of SQL_SUCCESS.  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_init(hdbc1) Failed\n\n");  
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
  
   printf("Number of rows bulk copied out = %d.\n", cRows);  
  
   // Cleanup  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="58332-131">参照</span><span class="sxs-lookup"><span data-stu-id="58332-131">See Also</span></span>  
 [<span data-ttu-id="58332-132">SQL Server ODBC ドライバーを使用した一括コピーの操作方法に関するトピック &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="58332-132">Bulk Copying with the SQL Server ODBC Driver How-to Topics &#40;ODBC&#41;</span></span>](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md)  
  
  
