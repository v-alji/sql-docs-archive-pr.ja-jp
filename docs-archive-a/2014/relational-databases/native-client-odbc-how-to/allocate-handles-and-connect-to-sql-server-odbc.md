---
title: ハンドルを割り当てて SQL Server に接続する (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- handles [ODBC]
- handles [ODBC], connection
- handles [ODBC], about handles
ms.assetid: 6172cd52-9c9a-467d-992f-def07f3f3bb1
author: rothja
ms.author: jroth
ms.openlocfilehash: 615a6dbe966b4c681e9cd4285ff55864d7a13370
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742005"
---
# <a name="allocate-handles-and-connect-to-sql-server-odbc"></a><span data-ttu-id="884ee-102">ハンドルの割り当てと SQL Server への接続 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="884ee-102">Allocate Handles and Connect to SQL Server (ODBC)</span></span>
    
### <a name="to-allocate-handles-and-connect-to-sql-server"></a><span data-ttu-id="884ee-103">ハンドルを割り当てて SQL Server に接続するには</span><span class="sxs-lookup"><span data-stu-id="884ee-103">To allocate handles and connect to SQL Server</span></span>  
  
1.  <span data-ttu-id="884ee-104">ODBC ヘッダー ファイル Sql.h、Sqlext.h、Sqltypes.h を含めます。</span><span class="sxs-lookup"><span data-stu-id="884ee-104">Include the ODBC header files Sql.h, Sqlext.h, Sqltypes.h.</span></span>  
  
2.  <span data-ttu-id="884ee-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ドライバー固有のヘッダー ファイル Odbcss.h を含めます。</span><span class="sxs-lookup"><span data-stu-id="884ee-105">Include the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver-specific header file, Odbcss.h.</span></span>  
  
3.  <span data-ttu-id="884ee-106">を使用して[SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396)を呼び出し `HandleType` SQL_HANDLE_ENV、ODBC を初期化して環境ハンドルを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="884ee-106">Call [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) with a `HandleType` of SQL_HANDLE_ENV to initialize ODBC and allocate an environment handle.</span></span>  
  
4.  <span data-ttu-id="884ee-107">[SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) `Attribute` を SQL_ATTR_ODBC_VERSION に設定し、 `ValuePtr` を SQL_OV_ODBC3 に設定して、アプリケーションが ODBC 3. x 形式の関数呼び出しを使用することを示すには、を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="884ee-107">Call [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) with `Attribute` set to SQL_ATTR_ODBC_VERSION and `ValuePtr` set to SQL_OV_ODBC3 to indicate the application will use ODBC 3.x-format function calls.</span></span>  
  
5.  <span data-ttu-id="884ee-108">必要に応じて、 [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md)を呼び出して他の環境オプションを設定するか、 [SQLGetEnvAttr](https://go.microsoft.com/fwlink/?LinkId=58403)を呼び出して環境オプションを取得します。</span><span class="sxs-lookup"><span data-stu-id="884ee-108">Optionally, call [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) to set other environment options, or call [SQLGetEnvAttr](https://go.microsoft.com/fwlink/?LinkId=58403) to get environment options.</span></span>  
  
6.  <span data-ttu-id="884ee-109">SQL_HANDLE_DBC のを使用して[SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396)を呼び出し、 `HandleType` 接続ハンドルを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="884ee-109">Call [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) with a `HandleType` of SQL_HANDLE_DBC to allocate a connection handle.</span></span>  
  
7.  <span data-ttu-id="884ee-110">必要に応じて、 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)を呼び出して接続オプションを設定するか、 [Sqlgetconnectattr](../native-client-odbc-api/sqlgetconnectattr.md)を呼び出して接続オプションを取得します。</span><span class="sxs-lookup"><span data-stu-id="884ee-110">Optionally, call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) to set connection options, or call [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md) to get connection options.</span></span>  
  
8.  <span data-ttu-id="884ee-111">SQLConnect を呼び出して、既存のデータソースを使用してに接続 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="884ee-111">Call SQLConnect to use an existing data source to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="884ee-112">または</span><span class="sxs-lookup"><span data-stu-id="884ee-112">Or</span></span>  
  
     <span data-ttu-id="884ee-113">接続文字列を使用してに接続するには、 [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md)を呼び出し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="884ee-113">Call [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) to use a connection string to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="884ee-114">最小の完全な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続文字列は、次の 2 つの形式のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="884ee-114">A minimum complete [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection string has one of two forms:</span></span>  
  
    ```  
    DSN=dsn_name;Trusted_connection=yes;  
    DRIVER={SQL Server Native Client 10.0};SERVER=server;Trusted_connection=yes;  
    ```  
  
     <span data-ttu-id="884ee-115">接続文字列が完全でない場合は、`SQLDriverConnect` によって必要な情報の入力が要求される場合があります。</span><span class="sxs-lookup"><span data-stu-id="884ee-115">If the connection string is not complete, `SQLDriverConnect` can prompt for the required information.</span></span> <span data-ttu-id="884ee-116">これは、 *Drivercompletion*パラメーターに指定された値によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="884ee-116">This is controlled by the value specified for the *DriverCompletion* parameter.</span></span>  
  
     <span data-ttu-id="884ee-117">\- または</span><span class="sxs-lookup"><span data-stu-id="884ee-117">\- or -</span></span>  
  
     <span data-ttu-id="884ee-118">反復的な方法で[SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md)を複数回呼び出して、接続文字列を作成し、に接続し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="884ee-118">Call [SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md) multiple times in an iterative fashion to build the connection string and connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
9. <span data-ttu-id="884ee-119">必要に応じて、 [SQLGetInfo](../native-client-odbc-api/sqlgetinfo.md)を呼び出して、データソースのドライバー属性と動作を取得し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="884ee-119">Optionally, call [SQLGetInfo](../native-client-odbc-api/sqlgetinfo.md) to get driver attributes and behavior for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source.</span></span>  
  
10. <span data-ttu-id="884ee-120">ステートメントを割り当てて使用します。</span><span class="sxs-lookup"><span data-stu-id="884ee-120">Allocate and use statements.</span></span>  
  
11. <span data-ttu-id="884ee-121">切断するには SQLDisconnect を呼び出し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続ハンドルを新しい接続に使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="884ee-121">Call SQLDisconnect to disconnect from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and make the connection handle available for a new connection.</span></span>  
  
12. <span data-ttu-id="884ee-122">SQL_HANDLE_DBC のを使用して[Sqlfreehandle](../native-client-odbc-api/sqlfreehandle.md) `HandleType` を呼び出し、接続ハンドルを解放します。</span><span class="sxs-lookup"><span data-stu-id="884ee-122">Call [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) with a `HandleType` of SQL_HANDLE_DBC to free the connection handle.</span></span>  
  
13. <span data-ttu-id="884ee-123">`SQLFreeHandle` を SQL_HANDLE_ENV として `HandleType` を呼び出し、環境ハンドルを解放します。</span><span class="sxs-lookup"><span data-stu-id="884ee-123">Call `SQLFreeHandle` with a `HandleType` of SQL_HANDLE_ENV to free the environment handle.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="884ee-124">可能な場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="884ee-124">When possible, use Windows Authentication.</span></span> <span data-ttu-id="884ee-125">Windows 認証が使用できない場合は、実行時に資格情報を入力するようユーザーに求めます。</span><span class="sxs-lookup"><span data-stu-id="884ee-125">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="884ee-126">資格情報をファイルに保存するのは避けてください。</span><span class="sxs-lookup"><span data-stu-id="884ee-126">Avoid storing credentials in a file.</span></span> <span data-ttu-id="884ee-127">資格情報を保持する必要がある場合は、[Win32 Crypto API](https://go.microsoft.com/fwlink/?LinkId=64532) を使用して暗号化してください。</span><span class="sxs-lookup"><span data-stu-id="884ee-127">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
## <a name="example"></a><span data-ttu-id="884ee-128">例</span><span class="sxs-lookup"><span data-stu-id="884ee-128">Example</span></span>  
 <span data-ttu-id="884ee-129">次の例では、`SQLDriverConnect` を呼び出して、既存の ODBC データ ソースを要求せずに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="884ee-129">This example shows a call to `SQLDriverConnect` to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without requiring an existing ODBC data source.</span></span> <span data-ttu-id="884ee-130">不完全な接続文字列を `SQLDriverConnect` に渡すと、ODBC ドライバーから不足情報を入力するように要求されます。</span><span class="sxs-lookup"><span data-stu-id="884ee-130">By passing an incomplete connection string to `SQLDriverConnect`, it causes the ODBC driver to prompt the user to enter the missing information.</span></span>  
  
```  
#define MAXBUFLEN   255  
  
SQLHENV      henv = SQL_NULL_HENV;  
SQLHDBC      hdbc1 = SQL_NULL_HDBC;  
SQLHSTMT      hstmt1 = SQL_NULL_HSTMT;  
  
SQLCHAR      ConnStrIn[MAXBUFLEN] =  
         "DRIVER={SQL Server Native Client 10.0};SERVER=MyServer";  
  
SQLCHAR      ConnStrOut[MAXBUFLEN];  
SQLSMALLINT   cbConnStrOut = 0;  
  
// Make connection without data source. Ask that driver   
// prompt if insufficient information. Driver returns  
// SQL_ERROR and application prompts user  
// for missing information. Window handle not needed for  
// SQL_DRIVER_NOPROMPT.  
retcode = SQLDriverConnect(hdbc1,      // Connection handle  
                  NULL,         // Window handle  
                  ConnStrIn,      // Input connect string  
                  SQL_NTS,         // Null-terminated string  
                  ConnStrOut,      // Address of output buffer  
                  MAXBUFLEN,      // Size of output buffer  
                  &cbConnStrOut,   // Address of output length  
                  SQL_DRIVER_PROMPT);  
```  
  
  
