---
title: データソースへの接続 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- checking connection states
- ODBC data sources, connections
- data sources [SQL Server Native Client]
- SQLBrowseConnect function
- ODBC applications, connections
- ODBC applications, data sources
- connections [SQL Server Native Client]
- SQLConnect function
- SQLDriveConnect function
- verifying connection states
- SQL Server Native Client ODBC driver, data sources
- SQL Server Native Client ODBC driver, connections
ms.assetid: ae30dd1d-06ae-452b-9618-8fd8cd7ba074
author: rothja
ms.author: jroth
ms.openlocfilehash: 25ce5954e45bb8070b5e99d8ebb7bfa9ad149c3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640907"
---
# <a name="connecting-to-a-data-source-odbc"></a><span data-ttu-id="0402c-102">データ ソースへの接続 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="0402c-102">Connecting to a Data Source (ODBC)</span></span>
  <span data-ttu-id="0402c-103">アプリケーションは、環境ハンドルと接続ハンドルを割り当て、任意の接続属性を設定してから、データ ソースまたはドライバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="0402c-103">After allocating environment and connection handles and setting any connection attributes, the application connects to the data source or driver.</span></span> <span data-ttu-id="0402c-104">接続には、次の 3 つの関数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0402c-104">There are three functions you can use to connect:</span></span>  
  
-   <span data-ttu-id="0402c-105">**SQLConnect**</span><span class="sxs-lookup"><span data-stu-id="0402c-105">**SQLConnect**</span></span>  
  
-   <span data-ttu-id="0402c-106">**SQLDriverConnect**</span><span class="sxs-lookup"><span data-stu-id="0402c-106">**SQLDriverConnect**</span></span>  
  
-   <span data-ttu-id="0402c-107">**SQLBrowseConnect**</span><span class="sxs-lookup"><span data-stu-id="0402c-107">**SQLBrowseConnect**</span></span>  
  
 <span data-ttu-id="0402c-108">使用できるさまざまな接続文字列オプションなど、データソースへの接続の作成の詳細については、「 [SQL Server Native Client での接続文字列キーワードの使用](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0402c-108">For more information about making connections to a data source, including the various connection string options available, see [Using Connection String Keywords with SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
## <a name="sqlconnect"></a><span data-ttu-id="0402c-109">SQLConnect</span><span class="sxs-lookup"><span data-stu-id="0402c-109">SQLConnect</span></span>  
 <span data-ttu-id="0402c-110">**SQLConnect**は最も単純な接続関数です。</span><span class="sxs-lookup"><span data-stu-id="0402c-110">**SQLConnect** is the simplest connection function.</span></span> <span data-ttu-id="0402c-111">この関数は、データ ソース名、ユーザー ID、パスワードの 3 つのパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="0402c-111">It accepts three parameters: a data source name, a user ID, and a password.</span></span> <span data-ttu-id="0402c-112">この3つのパラメーターに、データベースへの接続に必要なすべての情報が含まれている場合は、 **SQLConnect**を使用します。</span><span class="sxs-lookup"><span data-stu-id="0402c-112">Use **SQLConnect** when these three parameters contain all the information needed to connect to the database.</span></span> <span data-ttu-id="0402c-113">これを行うには、 **sqldatasources**; を使用してデータソースの一覧を作成します。データソース、ユーザー ID、およびパスワードの入力をユーザーに求めます。次に、 **SQLConnect**を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0402c-113">To do this, build a list of data sources using **SQLDataSources**; prompt the user for a data source, user ID, and password; and then call **SQLConnect**.</span></span>  
  
 <span data-ttu-id="0402c-114">**SQLConnect**では、データソース名、ユーザー ID、およびパスワードを使用してデータソースに接続することができ、odbc データソースには odbc ドライバーが接続を確立するために必要な他のすべての情報が含まれていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="0402c-114">**SQLConnect** assumes that a data source name, user ID, and password are sufficient to connect to a data source and that the ODBC data source contains all other information the ODBC driver needs to make the connection.</span></span> <span data-ttu-id="0402c-115">[SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md)や[SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md)とは異なり、 **SQLConnect**は接続文字列を使用しません。</span><span class="sxs-lookup"><span data-stu-id="0402c-115">Unlike [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) and [SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md), **SQLConnect** does not use a connection string.</span></span>  
  
## <a name="sqldriverconnect"></a><span data-ttu-id="0402c-116">SQLDriverConnect</span><span class="sxs-lookup"><span data-stu-id="0402c-116">SQLDriverConnect</span></span>  
 <span data-ttu-id="0402c-117">**SQLDriverConnect**は、データソース名、ユーザー ID、およびパスワードよりも多くの情報が必要な場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="0402c-117">**SQLDriverConnect** is used when more information than the data source name, user ID, and password is required.</span></span> <span data-ttu-id="0402c-118">**SQLDriverConnect**のパラメーターの1つは、ドライバー固有の情報を含む接続文字列です。</span><span class="sxs-lookup"><span data-stu-id="0402c-118">One of the parameters to **SQLDriverConnect** is a connection string containing driver-specific information.</span></span> <span data-ttu-id="0402c-119">次の理由により、 **SQLConnect**の代わりに**SQLDriverConnect**を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0402c-119">You might use **SQLDriverConnect** instead of **SQLConnect** for the following reasons:</span></span>  
  
-   <span data-ttu-id="0402c-120">接続時にドライバー固有の情報を指定する場合</span><span class="sxs-lookup"><span data-stu-id="0402c-120">To specify driver-specific information at connect time.</span></span>  
  
-   <span data-ttu-id="0402c-121">ドライバーがユーザーに対して接続情報を要求する場合</span><span class="sxs-lookup"><span data-stu-id="0402c-121">To request that the driver prompt the user for connection information.</span></span>  
  
-   <span data-ttu-id="0402c-122">ODBC データ ソースを使用せずに接続する場合</span><span class="sxs-lookup"><span data-stu-id="0402c-122">To connect without using an ODBC data source.</span></span>  
  
 <span data-ttu-id="0402c-123">**SQLDriverConnect**接続文字列には、ODBC ドライバーによってサポートされるすべての接続情報を指定する一連のキーワードと値のペアが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0402c-123">The **SQLDriverConnect** connection string contains a series of keyword-value pairs that specify all connection information supported by an ODBC driver.</span></span> <span data-ttu-id="0402c-124">各ドライバーでは、ドライバーでサポートされるすべての接続情報を表すドライバー固有のキーワード以外に、標準の ODBC キーワード (DSN、FILEDSN, DRIVER、UID、PWD、および SAVEFILE) をサポートします。</span><span class="sxs-lookup"><span data-stu-id="0402c-124">Each driver supports the standard ODBC keywords (DSN, FILEDSN, DRIVER, UID, PWD, and SAVEFILE) in addition to driver-specific keywords for all connection information supported by the driver.</span></span> <span data-ttu-id="0402c-125">**SQLDriverConnect**は、データソースを使用せずに接続するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="0402c-125">**SQLDriverConnect** can be used to connect without a data source.</span></span> <span data-ttu-id="0402c-126">たとえば、のインスタンスに対して "DSN レス" 接続を作成するように設計されたアプリケーションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン ID、パスワード、ネットワークライブラリ、接続先のサーバー名、および使用する既定のデータベースを定義する接続文字列を使用して**SQLDriverConnect**を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="0402c-126">For example, an application that is designed to make a "DSN-less" connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can call **SQLDriverConnect** with a connection string that defines the login ID, password, network library, server name to connect to, and default database to use.</span></span>  
  
 <span data-ttu-id="0402c-127">**SQLDriverConnect**を使用する場合、必要な接続情報をユーザーに確認するには、次の2つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="0402c-127">When using **SQLDriverConnect**, there are two options for prompting the user for any needed connection information:</span></span>  
  
-   <span data-ttu-id="0402c-128">アプリケーション ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="0402c-128">Application dialog box</span></span>  
  
     <span data-ttu-id="0402c-129">接続情報の入力を求めるアプリケーションダイアログボックスを作成し、NULL ウィンドウハンドルと*Drivercompletion*を SQL_DRIVER_NOPROMPT に設定して**SQLDriverConnect**を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="0402c-129">You can create an application dialog box that prompts for connection information, and then calls **SQLDriverConnect** with a NULL window handle and *DriverCompletion* set to SQL_DRIVER_NOPROMPT.</span></span> <span data-ttu-id="0402c-130">このようにパラメーターを設定すると、ODBC ドライバー独自のダイアログ ボックスが開かれなくなります。</span><span class="sxs-lookup"><span data-stu-id="0402c-130">These parameter settings prevent the ODBC driver from opening its own dialog box.</span></span> <span data-ttu-id="0402c-131">この方法は、アプリケーションでユーザー インターフェイスを制御することが重要な場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="0402c-131">This method is used when it is important to control the user interface of the application.</span></span>  
  
-   <span data-ttu-id="0402c-132">ドライバー ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="0402c-132">Driver dialog box</span></span>  
  
     <span data-ttu-id="0402c-133">アプリケーションをコーディングして、有効なウィンドウハンドルを**SQLDriverConnect**に渡し、 *drivercompletion*パラメーターを SQL_DRIVER_COMPLETE、SQL_DRIVER_PROMPT、または SQL_DRIVER_COMPLETE_REQUIRED に設定できます。</span><span class="sxs-lookup"><span data-stu-id="0402c-133">You can code the application to pass a valid window handle to **SQLDriverConnect** and set the *DriverCompletion* parameter to SQL_DRIVER_COMPLETE, SQL_DRIVER_PROMPT, or SQL_DRIVER_COMPLETE_REQUIRED.</span></span> <span data-ttu-id="0402c-134">この場合、ドライバーがダイアログ ボックスを生成して、ユーザーに接続情報を要求します。</span><span class="sxs-lookup"><span data-stu-id="0402c-134">The driver then generates a dialog box to prompt the user for connection information.</span></span> <span data-ttu-id="0402c-135">この方法を使用すると、アプリケーション コードが簡素化されます。</span><span class="sxs-lookup"><span data-stu-id="0402c-135">This method simplifies the application code.</span></span>  
  
## <a name="sqlbrowseconnect"></a><span data-ttu-id="0402c-136">SQLBrowseConnect</span><span class="sxs-lookup"><span data-stu-id="0402c-136">SQLBrowseConnect</span></span>  
 <span data-ttu-id="0402c-137">**SQLBrowseConnect**は、 **SQLDriverConnect**のように、接続文字列を使用します。</span><span class="sxs-lookup"><span data-stu-id="0402c-137">**SQLBrowseConnect**, like **SQLDriverConnect**, uses a connection string.</span></span> <span data-ttu-id="0402c-138">ただし、 **SQLBrowseConnect**を使用すると、アプリケーションは実行時にデータソースと繰り返して完全な接続文字列を作成できます。</span><span class="sxs-lookup"><span data-stu-id="0402c-138">However, by using **SQLBrowseConnect**, an application can construct a complete connection string iteratively with the data source at run time.</span></span> <span data-ttu-id="0402c-139">この方法を使用すると、アプリケーションで次の 2 つのことを行えます。</span><span class="sxs-lookup"><span data-stu-id="0402c-139">This allows the application to do two things:</span></span>  
  
-   <span data-ttu-id="0402c-140">アプリケーション独自のダイアログ ボックスを作成して目的の情報を要求できるので、アプリケーションのユーザー インターフェイスで制御できます。</span><span class="sxs-lookup"><span data-stu-id="0402c-140">Build its own dialog boxes to prompt for this information, thereby retaining control over its user interface.</span></span>  
  
-   <span data-ttu-id="0402c-141">特定のドライバーが使用できるデータ ソースをシステムから参照できます。これは複数の手順になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0402c-141">Browse the system for data sources that can be used by a particular driver, possibly in several steps.</span></span>  
  
     <span data-ttu-id="0402c-142">たとえば、ユーザーは最初にネットワークを介してサーバーを参照して、サーバーを選択します。次に、そのサーバーを介して、ドライバーがアクセスできるデータベースを参照するといった手順です。</span><span class="sxs-lookup"><span data-stu-id="0402c-142">For example, the user might first browse the network for servers and, after choosing a server, browse the server for databases accessible by the driver.</span></span>  
  
 <span data-ttu-id="0402c-143">**SQLBrowseConnect**が成功した接続を完了すると、 **SQLDriverConnect**への後続の呼び出しで使用できる接続文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="0402c-143">When **SQLBrowseConnect** completes a successful connection, it returns a connection string that can be used on subsequent calls to **SQLDriverConnect**.</span></span>  
  
 <span data-ttu-id="0402c-144">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーは、 **SQLConnect**、 **SQLDriverConnect**、または**SQLBrowseConnect**が正常に実行された場合、常に SQL_SUCCESS_WITH_INFO を返します。</span><span class="sxs-lookup"><span data-stu-id="0402c-144">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver always returns SQL_SUCCESS_WITH_INFO on a successful **SQLConnect**, **SQLDriverConnect**, or **SQLBrowseConnect**.</span></span> <span data-ttu-id="0402c-145">SQL_SUCCESS_WITH_INFO 取得した後に ODBC アプリケーションが**SQLGetDiagRec**を呼び出すと、次のメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0402c-145">When an ODBC application calls **SQLGetDiagRec** after getting SQL_SUCCESS_WITH_INFO, it can receive the following messages:</span></span>  
  
 <span data-ttu-id="0402c-146">5701</span><span class="sxs-lookup"><span data-stu-id="0402c-146">5701</span></span>  
 <span data-ttu-id="0402c-147">このメッセージは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が、ユーザーのコンテキストをデータ ソースで定義されている既定のデータベースに登録したことを示します。または、データ ソースに既定のデータベースが定義されていない場合は、接続で使用したログイン ID に対して定義されている既定のデータベースに登録したことを示します。</span><span class="sxs-lookup"><span data-stu-id="0402c-147">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] put the user's context into the default database defined in the data source, or into the default database defined for the login ID used in the connection if the data source did not have a default database.</span></span>  
  
 <span data-ttu-id="0402c-148">5703</span><span class="sxs-lookup"><span data-stu-id="0402c-148">5703</span></span>  
 <span data-ttu-id="0402c-149">このメッセージは、その言語がサーバーで使用されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="0402c-149">Indicates the language being used on the server.</span></span>  
  
 <span data-ttu-id="0402c-150">次の例では、システム管理者によって接続が正常に確立されたときに返されるメッセージを示します。</span><span class="sxs-lookup"><span data-stu-id="0402c-150">The following example shows the message returned on a successful connection by the system administrator:</span></span>  
  
```  
szSqlState = "01000", *pfNativeError = 5701,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
       Changed database context to 'pubs'."  
szSqlState = "01000", *pfNativeError = 5703,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
       Changed language setting to 'us_english'."  
```  
  
 <span data-ttu-id="0402c-151">5701 と 5703 のメッセージは、情報提供だけを目的としているので無視できます。</span><span class="sxs-lookup"><span data-stu-id="0402c-151">You can ignore messages 5701 and 5703; they are only informational.</span></span> <span data-ttu-id="0402c-152">ただし、SQL_SUCCESS_WITH_INFO リターン コードでは 5701 や 5703 以外のメッセージも返されることがあるので、そのようなリターン コードは無視しないでください。</span><span class="sxs-lookup"><span data-stu-id="0402c-152">You should not, however, ignore a SQL_SUCCESS_WITH_INFO return code because messages other than 5701 or 5703 may be returned.</span></span> <span data-ttu-id="0402c-153">たとえば、ドライバーがのインスタンスを実行しているサーバーに、古いカタログストアドプロシージャを使用して接続している場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL_SUCCESS_WITH_INFO 後に**SQLGetDiagRec**によって返されたエラーの1つは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="0402c-153">For example, if a driver connects to a server running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with outdated catalog stored procedures, one of the errors returned through **SQLGetDiagRec** after a SQL_SUCCESS_WITH_INFO is:</span></span>  
  
```  
SqlState:   01000  
pfNative:   0  
szErrorMsg: "[Microsoft][SQL Server Native Client]The ODBC  
            catalog stored procedures installed on server  
            my65server are version 06.50.0193; version 07.00.0205  
            or later is required to ensure proper operation.  
            Please contact your system administrator."  
```  
  
 <span data-ttu-id="0402c-154">接続用のアプリケーションのエラー処理関数は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL_NO_DATA を返すまで**SQLGetDiagRec**を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="0402c-154">The error handling function of an application for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connections should call **SQLGetDiagRec** until it returns SQL_NO_DATA.</span></span> <span data-ttu-id="0402c-155">次に、 *pfNative*コードが5701または5703のメッセージ以外のすべてのメッセージに対して動作します。</span><span class="sxs-lookup"><span data-stu-id="0402c-155">It should then act on any messages other than the ones with a *pfNative* code of 5701 or 5703.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0402c-156">参照</span><span class="sxs-lookup"><span data-stu-id="0402c-156">See Also</span></span>  
 [<span data-ttu-id="0402c-157">ODBC&#41;&#40;SQL Server との通信</span><span class="sxs-lookup"><span data-stu-id="0402c-157">Communicating with SQL Server &#40;ODBC&#41;</span></span>](communicating-with-sql-server-odbc.md)  
  
  
