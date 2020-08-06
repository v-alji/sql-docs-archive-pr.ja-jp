---
title: SQLDriverConnect |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLDriverConnect function
ms.assetid: a1e38e2c-3a97-42d1-9c45-a0ca3282ffd1
author: rothja
ms.author: jroth
ms.openlocfilehash: 40691dfb381883b59155607fb56f4933820e3e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736312"
---
# <a name="sqldriverconnect"></a><span data-ttu-id="70685-102">SQLDriverConnect</span><span class="sxs-lookup"><span data-stu-id="70685-102">SQLDriverConnect</span></span>
  <span data-ttu-id="70685-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、接続文字列のキーワードを置き換えたり、拡張したりするための接続属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="70685-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver defines connection attributes that either replace or enhance connection-string keywords.</span></span> <span data-ttu-id="70685-104">接続文字列のいくつかのキーワードには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーが指定する既定値があります。</span><span class="sxs-lookup"><span data-stu-id="70685-104">Several connection-string keywords have default values specified by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
 <span data-ttu-id="70685-105">Native Client ODBC ドライバーで使用できるキーワードの一覧については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [SQL Server Native Client での接続文字列キーワードの使用](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70685-105">For a list of the keywords available in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, see [Using Connection String Keywords with SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
 <span data-ttu-id="70685-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続属性とドライバーの既定の動作の詳細については、「 [SQLSetConnectAttr](sqlsetconnectattr.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70685-106">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection attributes and driver default behaviors, see [SQLSetConnectAttr](sqlsetconnectattr.md).</span></span>  
  
 <span data-ttu-id="70685-107">Native Client で有効な接続文字列キーワードの詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [SQL Server Native Client での接続文字列キーワードの使用](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70685-107">For a discussion of connection string keywords that are valid for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, see [Using Connection String Keywords with SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
 <span data-ttu-id="70685-108">`SQLDriverConnect` *Drivercompletion*パラメーター値が SQL_DRIVER_PROMPT、SQL_DRIVER_COMPLETE、または SQL_DRIVER_COMPLETE_REQUIRED の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、表示されるダイアログボックスからキーワード値を取得します。</span><span class="sxs-lookup"><span data-stu-id="70685-108">When the `SQLDriverConnect`*DriverCompletion* parameter value is SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE, or SQL_DRIVER_COMPLETE_REQUIRED, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver retrieves keyword values from the displayed dialog box.</span></span> <span data-ttu-id="70685-109">接続文字列でキーワード値が渡され、ユーザーがダイアログ ボックスでキーワードの値を変更しなかった場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは接続文字列の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="70685-109">If the keyword value is passed in the connection string and the user does not alter the value for the keyword in the dialog box, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver uses the value from the connection string.</span></span> <span data-ttu-id="70685-110">接続文字列で値が設定されていない場合、ユーザーがダイアログ ボックスで割り当てを行わないと、ドライバーは既定値を使用します。</span><span class="sxs-lookup"><span data-stu-id="70685-110">If the value is not set in the connection string and the user makes no assignment in the dialog box, the driver uses the default.</span></span>  
  
 <span data-ttu-id="70685-111">`SQLDriverConnect`*Drivercompletion*の値がドライバーの接続ダイアログボックスを表示する必要がある (または必要になる可能性がある) 場合は、有効な*WindowHandle*を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70685-111">`SQLDriverConnect` must be given a valid *WindowHandle* when any *DriverCompletion* value requires (or could require) the display of the driver's connection dialog box.</span></span> <span data-ttu-id="70685-112">無効なハンドルを指定すると、SQL_ERROR が返されます。</span><span class="sxs-lookup"><span data-stu-id="70685-112">An invalid handle returns SQL_ERROR.</span></span>  
  
 <span data-ttu-id="70685-113">DRIVER キーワードまたは DSN キーワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="70685-113">Specify either the DRIVER or DSN keywords.</span></span> <span data-ttu-id="70685-114">ODBC は、これらの 2 つのキーワードが両方指定されている場合、左側に指定されているキーワードを使用し、他方を無視するように指示します。</span><span class="sxs-lookup"><span data-stu-id="70685-114">ODBC states that a driver uses the leftmost of these two keywords and ignores the other if both are specified.</span></span> <span data-ttu-id="70685-115">DRIVER が指定されている場合、またはが2つの左端で、 `SQLDriverConnect` *drivercompletion*パラメーター値が SQL_DRIVER_NOPROMPT の場合は、SERVER キーワードと適切な値が必要です。</span><span class="sxs-lookup"><span data-stu-id="70685-115">If DRIVER is specified, or is the leftmost of the two, and the `SQLDriverConnect`*DriverCompletion* parameter value is SQL_DRIVER_NOPROMPT, the SERVER keyword and an appropriate value are required.</span></span>  
  
 <span data-ttu-id="70685-116">SQL_DRIVER_NOPROMPT が指定されているときは、ユーザー認証に関するキーワードに値が指定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="70685-116">When SQL_DRIVER_NOPROMPT is specified, user authentication keywords must be present with values.</span></span> <span data-ttu-id="70685-117">ドライバーは、文字列 "Trusted_Connection=yes" または UID キーワードと PWD キーワードの両方が指定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="70685-117">The driver ensures that either the string "Trusted_Connection=yes" or both the UID and PWD keywords are present.</span></span>  
  
 <span data-ttu-id="70685-118">*Drivercompletion*パラメーター値が SQL_DRIVER_NOPROMPT または SQL_DRIVER_COMPLETE_REQUIRED であり、言語またはデータベースが接続文字列から取得されていて、かつ無効である場合、は `SQLDriverConnect` SQL_ERROR を返します。</span><span class="sxs-lookup"><span data-stu-id="70685-118">If the *DriverCompletion* parameter value is SQL_DRIVER_NOPROMPT or SQL_DRIVER_COMPLETE_REQUIRED and the language or database comes from the connection string and either is invalid, `SQLDriverConnect` returns SQL_ERROR.</span></span>  
  
 <span data-ttu-id="70685-119">*Drivercompletion*パラメーターの値が SQL_DRIVER_NOPROMPT または SQL_DRIVER_COMPLETE_REQUIRED で、言語またはデータベースが ODBC データソースの定義から取得され、その言語またはデータベースが無効である場合、は、 `SQLDriverConnect` 指定されたユーザー ID の既定の言語またはデータベースを使用して SQL_SUCCESS_WITH_INFO を返します。</span><span class="sxs-lookup"><span data-stu-id="70685-119">If the *DriverCompletion* parameter value is SQL_DRIVER_NOPROMPT or SQL_DRIVER_COMPLETE_REQUIRED and the language or database comes from the ODBC data source definitions and either is invalid, `SQLDriverConnect` uses the default language or database for the specified user ID and returns SQL_SUCCESS_WITH_INFO.</span></span>  
  
 <span data-ttu-id="70685-120">*Drivercompletion*パラメーター値が SQL_DRIVER_COMPLETE または SQL_DRIVER_PROMPT で、言語またはデータベースが無効である場合は、に `SQLDriverConnect` よってダイアログボックスが再されます。</span><span class="sxs-lookup"><span data-stu-id="70685-120">If the *DriverCompletion* parameter value is SQL_DRIVER_COMPLETE or SQL_DRIVER_PROMPT and if the language or database is invalid, `SQLDriverConnect` redisplays the dialog box.</span></span>  
  
## <a name="sqldriverconnect-support-for-high-availability-disaster-recovery"></a><span data-ttu-id="70685-121">SQLDriverConnect の HADR サポート</span><span class="sxs-lookup"><span data-stu-id="70685-121">SQLDriverConnect Support for High Availability, Disaster Recovery</span></span>  
 <span data-ttu-id="70685-122">を使用したクラスターへの接続の詳細については `SQLDriverConnect` [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 、「[高可用性、ディザスターリカバリーのサポートの SQL Server Native Client](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70685-122">For more information about using `SQLDriverConnect` to connect to a [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] cluster, see [SQL Server Native Client Support for High Availability, Disaster Recovery](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).</span></span>  
  
## <a name="sqldriverconnect-support-for-service-principal-names-spns"></a><span data-ttu-id="70685-123">SQLDriverConnect によるサービス プリンシパル名 (SPN) のサポート</span><span class="sxs-lookup"><span data-stu-id="70685-123">SQLDriverConnect Support for Service Principal Names (SPNs)</span></span>  
 <span data-ttu-id="70685-124">SQLDDriverConnect では、プロンプトが有効になっているときに ODBC ログインダイアログボックスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="70685-124">SQLDDriverConnect will use the ODBC Login dialog boxwhen prompting is enabled.</span></span> <span data-ttu-id="70685-125">これにより、プリンシパル サーバーとそのフェールオーバー パートナーの両方に対して SPN を入力できます。</span><span class="sxs-lookup"><span data-stu-id="70685-125">This allows SPNs to be entered for both the principal server and its failover partner.</span></span>  
  
 <span data-ttu-id="70685-126">SQLDriverConnect は新しい接続文字列キーワード `ServerSPN` とを受け取り、 `FailoverPartnerSPN` 新しい接続属性 SQL_COPT_SS_SERVER_SPN と SQL_COPT_SS_FAILOVER_PARTNER_SPN を認識します。</span><span class="sxs-lookup"><span data-stu-id="70685-126">SQLDriverConnect will accept the new connection string keywords `ServerSPN` and `FailoverPartnerSPN`, and will recognize the new connection attributes SQL_COPT_SS_SERVER_SPN and SQL_COPT_SS_FAILOVER_PARTNER_SPN.</span></span>  
  
 <span data-ttu-id="70685-127">接続属性の値が複数指定されている場合は、DSN の値や接続文字列の値より、プログラムによって設定された値が優先されます。</span><span class="sxs-lookup"><span data-stu-id="70685-127">When a connection attribute value is specified more than once, a value that is set programmatically takes precedence over the value in a DSN and a value in a connection string.</span></span> <span data-ttu-id="70685-128">DSN の値は接続文字列の値より優先されます。</span><span class="sxs-lookup"><span data-stu-id="70685-128">A value in a DSN takes precedence over a value in a connection string.</span></span>  
  
 <span data-ttu-id="70685-129">接続が開いている場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client では、SQL_COPT_SS_MUTUALLY_AUTHENTICATED および SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD が、接続を開くときに使用された認証方式に設定されます。</span><span class="sxs-lookup"><span data-stu-id="70685-129">When a connection is opened, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sets SQL_COPT_SS_MUTUALLY_AUTHENTICATED and SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD to the authentication method used to open the connection.</span></span>  
  
 <span data-ttu-id="70685-130">Spn の詳細については、「[クライアント接続 &#40;ODBC&#41;のサービスプリンシパル名 &#40;spn&#41; ](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70685-130">For more information about SPNs, see [Service Principal Names &#40;SPNs&#41; in Client Connections &#40;ODBC&#41;](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="70685-131">例</span><span class="sxs-lookup"><span data-stu-id="70685-131">Examples</span></span>  
 <span data-ttu-id="70685-132">次の呼び出しは、に必要なデータ量の最小値を示してい `SQLDriverConnect` ます。</span><span class="sxs-lookup"><span data-stu-id="70685-132">The following call illustrates the least amount of data required for `SQLDriverConnect`:</span></span>  
  
```  
SQLDriverConnect(hdbc, hwnd,  
    (SQLTCHAR*) TEXT("DRIVER={SQL Server Native Client 10};"), SQL_NTS, szOutConn,  
    MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
```  
  
 <span data-ttu-id="70685-133">次の接続文字列は、 *Drivercompletion*パラメーター値が SQL_DRIVER_NOPROMPT 場合に最低限必要なデータを示しています。</span><span class="sxs-lookup"><span data-stu-id="70685-133">The following connection strings illustrate minimum required data when the *DriverCompletion* parameter value is SQL_DRIVER_NOPROMPT:</span></span>  
  
```  
"DSN=Human Resources;Trusted_Connection=yes"  
  
"FILEDSN=HR_FDSN;Trusted_Connection=yes"  
  
"DRIVER={SQL Server Native Client 10};SERVER=(local);Trusted_Connection=yes"  
```  
  
## <a name="see-also"></a><span data-ttu-id="70685-134">参照</span><span class="sxs-lookup"><span data-stu-id="70685-134">See Also</span></span>  
 <span data-ttu-id="70685-135">[SQLDriverConnect 関数](https://go.microsoft.com/fwlink/?LinkId=59340) </span><span class="sxs-lookup"><span data-stu-id="70685-135">[SQLDriverConnect Function](https://go.microsoft.com/fwlink/?LinkId=59340) </span></span>  
 <span data-ttu-id="70685-136">[ODBC API の実装の詳細](odbc-api-implementation-details.md) </span><span class="sxs-lookup"><span data-stu-id="70685-136">[ODBC API Implementation Details](odbc-api-implementation-details.md) </span></span>  
 <span data-ttu-id="70685-137">[SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="70685-137">[SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span></span>  
 <span data-ttu-id="70685-138">[SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="70685-138">[SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span></span>  
 [<span data-ttu-id="70685-139">SET ANSI_WARNINGS &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="70685-139">SET ANSI_WARNINGS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-ansi-warnings-transact-sql)  
  
  
