---
title: SQL Server Native Client ODBC ドライバーアプリケーションの作成 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, architecture
- SQL Server Native Client ODBC driver, creating applications
- ODBC function calls
- ODBC, header files
- ODBC applications
- ODBC applications, creating
- SQL Server Native Client ODBC driver, extensions
- applications [SQL Server Native Client]
- SQL Server Native Client ODBC driver, ODBC architecture
- extensions [ODBC]
- ODBC, driver extensions
- function calls [ODBC]
ms.assetid: c83c36e2-734e-4960-bc7e-92235910bc6f
author: rothja
ms.author: jroth
ms.openlocfilehash: c8a1719f8b60885810d9b2f8a1f1023a7ffe6e47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738221"
---
# <a name="creating-a-sql-server-native-client-odbc-driver-application"></a><span data-ttu-id="dea76-102">SQL Server Native Client ODBC ドライバー アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="dea76-102">Creating a SQL Server Native Client ODBC Driver Application</span></span>
  <span data-ttu-id="dea76-103">ODBC アーキテクチャには、次の機能を実行する 4 つのコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="dea76-103">ODBC architecture has four components that perform the following functions.</span></span>  
  
|<span data-ttu-id="dea76-104">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="dea76-104">Component</span></span>|<span data-ttu-id="dea76-105">機能</span><span class="sxs-lookup"><span data-stu-id="dea76-105">Function</span></span>|  
|---------------|--------------|  
|<span data-ttu-id="dea76-106">アプリケーション</span><span class="sxs-lookup"><span data-stu-id="dea76-106">Application</span></span>|<span data-ttu-id="dea76-107">ODBC 関数を呼び出して ODBC データ ソースと通信し、SQL ステートメントを送信して、結果セットを処理します。</span><span class="sxs-lookup"><span data-stu-id="dea76-107">Calls ODBC functions to communicate with an ODBC data source, submits SQL statements, and processes result sets.</span></span>|  
|<span data-ttu-id="dea76-108">ドライバー マネージャー</span><span class="sxs-lookup"><span data-stu-id="dea76-108">Driver Manager</span></span>|<span data-ttu-id="dea76-109">アプリケーションと、そのアプリケーションで使用されるすべての ODBC ドライバー間の通信を管理します。</span><span class="sxs-lookup"><span data-stu-id="dea76-109">Manages communication between an application and all ODBC drivers used by the application.</span></span>|  
|<span data-ttu-id="dea76-110">Driver</span><span class="sxs-lookup"><span data-stu-id="dea76-110">Driver</span></span>|<span data-ttu-id="dea76-111">アプリケーションからのすべての ODBC 関数呼び出しを処理し、データ ソースに接続して、SQL ステートメントをアプリケーションからデータ ソースに渡し、結果をアプリケーションに返します。</span><span class="sxs-lookup"><span data-stu-id="dea76-111">Processes all ODBC function calls from the application, connects to a data source, passes SQL statements from the application to the data source, and returns results to the application.</span></span> <span data-ttu-id="dea76-112">必要に応じて、アプリケーションの ODBC SQL をデータ ソースで使用されるネイティブ SQL に変換します。</span><span class="sxs-lookup"><span data-stu-id="dea76-112">If necessary, the driver translates ODBC SQL from the application to native SQL used by the data source.</span></span>|  
|<span data-ttu-id="dea76-113">データ ソース</span><span class="sxs-lookup"><span data-stu-id="dea76-113">Data source</span></span>|<span data-ttu-id="dea76-114">DBMS 内にあるデータの特定のインスタンスにアクセスするためにドライバーが必要とするすべての情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="dea76-114">Contains all information a driver needs to access a specific instance of data in a DBMS.</span></span>|  
  
 <span data-ttu-id="dea76-115">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーを使用してのインスタンスと通信するアプリケーションは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="dea76-115">An application that uses the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver to communicate with an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] performs the following tasks:</span></span>  
  
-   <span data-ttu-id="dea76-116">データ ソースとの接続</span><span class="sxs-lookup"><span data-stu-id="dea76-116">Connects with a data source</span></span>  
  
-   <span data-ttu-id="dea76-117">データ ソースへの SQL ステートメントの送信</span><span class="sxs-lookup"><span data-stu-id="dea76-117">Sends SQL statements to the data source</span></span>  
  
-   <span data-ttu-id="dea76-118">データ ソースから返されたステートメント結果の処理</span><span class="sxs-lookup"><span data-stu-id="dea76-118">Processes the results of statements from the data source</span></span>  
  
-   <span data-ttu-id="dea76-119">エラーとメッセージを処理します</span><span class="sxs-lookup"><span data-stu-id="dea76-119">Processes errors and messages</span></span>  
  
-   <span data-ttu-id="dea76-120">データ ソースへの接続の終了</span><span class="sxs-lookup"><span data-stu-id="dea76-120">Terminates the connection to the data source</span></span>  
  
 <span data-ttu-id="dea76-121">Native Client ODBC ドライバー用に記述されたより複雑なアプリケーションで [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] も、次のタスクが実行される場合があります。</span><span class="sxs-lookup"><span data-stu-id="dea76-121">A more complex application written for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver might also perform the following tasks:</span></span>  
  
-   <span data-ttu-id="dea76-122">カーソルを使用した結果セット内の位置の制御</span><span class="sxs-lookup"><span data-stu-id="dea76-122">Use cursors to control location in a result set</span></span>  
  
-   <span data-ttu-id="dea76-123">トランザクション制御に関するコミット操作やロールバック操作の要求</span><span class="sxs-lookup"><span data-stu-id="dea76-123">Request commit or rollback operations for transaction control</span></span>  
  
-   <span data-ttu-id="dea76-124">2 台以上のサーバーに関連する分散トランザクションの実行</span><span class="sxs-lookup"><span data-stu-id="dea76-124">Perform distributed transactions involving two or more servers</span></span>  
  
-   <span data-ttu-id="dea76-125">リモート サーバーでのストアド プロシージャの実行</span><span class="sxs-lookup"><span data-stu-id="dea76-125">Run stored procedures on the remote server</span></span>  
  
-   <span data-ttu-id="dea76-126">結果セットの属性に関する情報を取得するためのカタログ関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="dea76-126">Call catalog functions to inquire about the attributes of a result set</span></span>  
  
-   <span data-ttu-id="dea76-127">一括コピー操作の実行</span><span class="sxs-lookup"><span data-stu-id="dea76-127">Perform bulk copy operations</span></span>  
  
-   <span data-ttu-id="dea76-128">大規模データ (**varchar (max)**、 **nvarchar (max)**、および**varbinary (max)** の各列) 操作の管理</span><span class="sxs-lookup"><span data-stu-id="dea76-128">Manage large data (**varchar(max)**, **nvarchar(max)**, and **varbinary(max)** columns) operations</span></span>  
  
-   <span data-ttu-id="dea76-129">データベース ミラーリングが構成されているときにフェールオーバーを容易にするための再接続ロジックの使用</span><span class="sxs-lookup"><span data-stu-id="dea76-129">Use reconnection logic to facilitate failover when database mirroring is configured</span></span>  
  
-   <span data-ttu-id="dea76-130">パフォーマンス データや実行時間の長いクエリのログ記録</span><span class="sxs-lookup"><span data-stu-id="dea76-130">Log performance data and long-running queries</span></span>  
  
 <span data-ttu-id="dea76-131">ODBC 関数を呼び出すには、C または C++ アプリケーションで sql.h ヘッダー ファイル、sqlext.h ヘッダー ファイル、および sqltypes.h ヘッダー ファイルをインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dea76-131">To make ODBC function calls, a C or C++ application must include the sql.h, sqlext.h, and sqltypes.h header files.</span></span> <span data-ttu-id="dea76-132">ODBC インストーラーの API 関数を呼び出す場合は、アプリケーションで odbcinst.h ヘッダー ファイルをインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dea76-132">To make calls to the ODBC installer API functions, an application must include the odbcinst.h header file.</span></span> <span data-ttu-id="dea76-133">Unicode ODBC アプリケーションでは、sqlucode.h ヘッダー ファイルをインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dea76-133">A Unicode ODBC application must include the sqlucode.h header file.</span></span> <span data-ttu-id="dea76-134">ODBC アプリケーションは、odbc32.lib ファイルとリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dea76-134">ODBC applications must be linked with the odbc32.lib file.</span></span> <span data-ttu-id="dea76-135">ODBC インストーラーの API 関数を呼び出す ODBC アプリケーションは、odbccp32.lib ファイルとリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dea76-135">ODBC applications that call the ODBC installer API functions must be linked with the odbccp32.lib file.</span></span> <span data-ttu-id="dea76-136">これらのファイルは、Windows プラットフォーム SDK に含まれています。</span><span class="sxs-lookup"><span data-stu-id="dea76-136">These files are included in the Windows Platform SDK.</span></span>  
  
 <span data-ttu-id="dea76-137">Native Client ODBC ドライバーを含む多くの ODBC ドライバーには、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ドライバー固有の odbc 拡張機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="dea76-137">Many ODBC drivers, including the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver, offer driver-specific ODBC extensions.</span></span> <span data-ttu-id="dea76-138">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバー固有の拡張機能を利用するには、アプリケーションに sqlncli ヘッダーファイルを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="dea76-138">To take advantage of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver-specific extensions, an application should include the sqlncli.h header file.</span></span> <span data-ttu-id="dea76-139">このヘッダー ファイルには、次の要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="dea76-139">This header file contains:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="dea76-140">Native Client ODBC ドライバー固有の接続属性。</span><span class="sxs-lookup"><span data-stu-id="dea76-140">Native Client ODBC driver-specific connection attributes.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="dea76-141">Native Client ODBC ドライバー固有のステートメント属性。</span><span class="sxs-lookup"><span data-stu-id="dea76-141">Native Client ODBC driver-specific statement attributes.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="dea76-142">Native Client ODBC ドライバー固有の列属性。</span><span class="sxs-lookup"><span data-stu-id="dea76-142">Native Client ODBC driver-specific column attributes.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="dea76-143">固有のデータ型</span><span class="sxs-lookup"><span data-stu-id="dea76-143">-specific data types.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="dea76-144">固有のユーザー定義データ型</span><span class="sxs-lookup"><span data-stu-id="dea76-144">-specific user-defined data types.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="dea76-145">Native Client ODBC ドライバー固有の[SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md)型。</span><span class="sxs-lookup"><span data-stu-id="dea76-145">Native Client ODBC driver-specific [SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md) types.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="dea76-146">Native Client ODBC ドライバーの診断フィールド。</span><span class="sxs-lookup"><span data-stu-id="dea76-146">Native Client ODBC driver diagnostics fields.</span></span>  
  
-   <span data-ttu-id="dea76-147">診断に役立つ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 固有の動的関数コード</span><span class="sxs-lookup"><span data-stu-id="dea76-147">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-specific diagnostic dynamic function codes.</span></span>  
  
-   <span data-ttu-id="dea76-148">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 固有のネイティブ C データ型に関する C 型定義や C++ 型定義 (列が C データ型の SQL_C_BINARY にバインドされるときに返される)</span><span class="sxs-lookup"><span data-stu-id="dea76-148">C/C++ type definitions for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-specific native C data types (returned when columns bound to C data type SQL_C_BINARY).</span></span>  
  
-   <span data-ttu-id="dea76-149">SQLPERF データ構造体の型定義</span><span class="sxs-lookup"><span data-stu-id="dea76-149">Type definition for the SQLPERF data structure.</span></span>  
  
-   <span data-ttu-id="dea76-150">ODBC 接続経由の一括コピー API の使用をサポートするための一括コピー用のマクロとプロトタイプ</span><span class="sxs-lookup"><span data-stu-id="dea76-150">Bulk copy macros and prototypes to support bulk copy API usage through an ODBC connection.</span></span>  
  
-   <span data-ttu-id="dea76-151">リンク サーバーとリンク サーバーのカタログ一覧を取得するための分散クエリ メタデータ API 関数呼び出し</span><span class="sxs-lookup"><span data-stu-id="dea76-151">Call the distributed query metadata API functions for lists of linked servers and their catalogs.</span></span>  
  
 <span data-ttu-id="dea76-152">Native Client ODBC ドライバーの一括コピー機能を使用する C または C++ ODBC アプリケーション [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、sqlncli11 ファイルとリンクされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="dea76-152">Any C or C++ ODBC application that uses the bulk copy feature of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver must be linked with the sqlncli11.lib file.</span></span> <span data-ttu-id="dea76-153">分散クエリ メタデータ API 関数を呼び出すアプリケーションも、sqlncli11.lib とリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dea76-153">Applications calling the distributed query metadata API functions must also be linked with sqlncli11.lib.</span></span> <span data-ttu-id="dea76-154">Sqlncli ファイルと sqlncli11 ファイルは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 開発者ツールの一部として配布されます。</span><span class="sxs-lookup"><span data-stu-id="dea76-154">The sqlncli.h and sqlncli11.lib files are distributed as part of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] developer's tools.</span></span> <span data-ttu-id="dea76-155">次のように、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の Include ディレクトリはコンパイラの INCLUDE パスに、Lib ディレクトリは LIB パスに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="dea76-155">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Include and Lib directories should be in the compiler's INCLUDE and LIB paths as in the following:</span></span>  
  
```  
LIB=c:\Program Files\Microsoft Data Access SDK 2.8\Libs\x86\lib;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Lib;  
INCLUDE=c:\Program Files\Microsoft Data Access SDK 2.8\inc;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Include;  
```  
  
 <span data-ttu-id="dea76-156">アプリケーションで複数の ODBC 呼び出しが同時に未処理状態になる必要があるかどうかというデザイン上の決定を、アプリケーションのビルド処理の初期段階で行います。</span><span class="sxs-lookup"><span data-stu-id="dea76-156">One design decision made early in the process of building an application is whether the application needs to have multiple ODBC calls outstanding at the same time.</span></span> <span data-ttu-id="dea76-157">複数の同時実行 ODBC 呼び出しをサポートするには 2 つの方法があり、このセクションの残りのトピックで説明されています。</span><span class="sxs-lookup"><span data-stu-id="dea76-157">There are two methods for supporting multiple concurrent ODBC calls, which are described in the remaining topics in this section.</span></span> <span data-ttu-id="dea76-158">詳細については、 [ODBC プログラマーズリファレンス](https://go.microsoft.com/fwlink/?LinkId=45250)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dea76-158">For more information, see the [ODBC Programmer's Reference](https://go.microsoft.com/fwlink/?LinkId=45250).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dea76-159">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="dea76-159">In This Section</span></span>  
  
-   [<span data-ttu-id="dea76-160">非同期モードと SQLCancel</span><span class="sxs-lookup"><span data-stu-id="dea76-160">Asynchronous Mode and SQLCancel</span></span>](../../native-client-odbc-api/sqlcancel.md)  
  
-   [<span data-ttu-id="dea76-161">マルチスレッド アプリケーション</span><span class="sxs-lookup"><span data-stu-id="dea76-161">Multithreaded Applications</span></span>](creating-a-driver-application-multithreaded-applications.md)  
  
## <a name="see-also"></a><span data-ttu-id="dea76-162">参照</span><span class="sxs-lookup"><span data-stu-id="dea76-162">See Also</span></span>  
 [<span data-ttu-id="dea76-163">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="dea76-163">SQL Server Native Client &#40;ODBC&#41;</span></span>](sql-server-native-client-odbc.md)  
  
  
