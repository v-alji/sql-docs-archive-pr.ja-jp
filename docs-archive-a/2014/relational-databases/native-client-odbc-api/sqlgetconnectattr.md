---
title: SQLGetConnectAttr |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetConnectAttr function
ms.assetid: 26e4e69a-44fd-45e3-b47a-ae39184f041b
author: rothja
ms.author: jroth
ms.openlocfilehash: f82a0fb71103e811b36280f9722c160791023e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631007"
---
# <a name="sqlgetconnectattr"></a><span data-ttu-id="6cdce-102">SQLGetConnectAttr</span><span class="sxs-lookup"><span data-stu-id="6cdce-102">SQLGetConnectAttr</span></span>
  <span data-ttu-id="6cdce-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、ドライバー固有の接続属性が定義されます。</span><span class="sxs-lookup"><span data-stu-id="6cdce-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver defines driver-specific connection attributes.</span></span> <span data-ttu-id="6cdce-104">一部の属性はで使用でき `SQLGetConnectAttr` ます。関数は、現在の設定をレポートするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6cdce-104">Some of the attributes are available to `SQLGetConnectAttr`, and the function is used to report their current settings.</span></span> <span data-ttu-id="6cdce-105">これらの属性について報告される値は、接続が確立されるか、または[SQLSetConnectAttr](sqlsetconnectattr.md)を使用して属性が設定されるまでは保証されません。</span><span class="sxs-lookup"><span data-stu-id="6cdce-105">The values reported for these attributes are not guaranteed until after a connection has been made or the attribute has been set using [SQLSetConnectAttr](sqlsetconnectattr.md).</span></span>  
  
 <span data-ttu-id="6cdce-106">ここでは、読み取り専用の属性を示します。</span><span class="sxs-lookup"><span data-stu-id="6cdce-106">This topic lists the read only attributes.</span></span> <span data-ttu-id="6cdce-107">Native Client ODBC ドライバー固有のその他の接続属性の詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [SQLSetConnectAttr](sqlsetconnectattr.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cdce-107">For information about the other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver-specific connection attributes, see [SQLSetConnectAttr](sqlsetconnectattr.md).</span></span>  
  
## <a name="sql_copt_ss_connection_dead"></a><span data-ttu-id="6cdce-108">SQL_COPT_SS_CONNECTION_DEAD</span><span class="sxs-lookup"><span data-stu-id="6cdce-108">SQL_COPT_SS_CONNECTION_DEAD</span></span>  
 <span data-ttu-id="6cdce-109">SQL_COPT_SS_CONNECTION_DEAD 属性では、サーバーへの接続状態が報告されます。</span><span class="sxs-lookup"><span data-stu-id="6cdce-109">The SQL_COPT_SS_CONNECTION_DEAD attribute reports the state of a connection to a server.</span></span> <span data-ttu-id="6cdce-110">ドライバーは、接続の現在の状態をネットワークにクエリします。</span><span class="sxs-lookup"><span data-stu-id="6cdce-110">The driver queries the network for the current state of the connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6cdce-111">標準の ODBC 接続属性 SQL_ATTR_CONNECTION_DEAD は、接続の最新の状態を返します。</span><span class="sxs-lookup"><span data-stu-id="6cdce-111">The standard ODBC connection attribute SQL_ATTR_CONNECTION_DEAD returns the most recent state of the connection.</span></span> <span data-ttu-id="6cdce-112">これは現在の接続状態と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6cdce-112">This might not be the current connection state.</span></span>  
  
|<span data-ttu-id="6cdce-113">値</span><span class="sxs-lookup"><span data-stu-id="6cdce-113">Value</span></span>|<span data-ttu-id="6cdce-114">説明</span><span class="sxs-lookup"><span data-stu-id="6cdce-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6cdce-115">SQL_CD_TRUE</span><span class="sxs-lookup"><span data-stu-id="6cdce-115">SQL_CD_TRUE</span></span>|<span data-ttu-id="6cdce-116">サーバーへの接続が失われました。</span><span class="sxs-lookup"><span data-stu-id="6cdce-116">The connection to the server has been lost.</span></span>|  
|<span data-ttu-id="6cdce-117">SQL_CD_FALSE</span><span class="sxs-lookup"><span data-stu-id="6cdce-117">SQL_CD_FALSE</span></span>|<span data-ttu-id="6cdce-118">接続が開かれており、ステートメントの処理に使用できます。</span><span class="sxs-lookup"><span data-stu-id="6cdce-118">The connection is open and available for statement processing.</span></span>|  
  
## <a name="sql_copt_ss_client_connection_id"></a><span data-ttu-id="6cdce-119">SQL_COPT_SS_CLIENT_CONNECTION_ID</span><span class="sxs-lookup"><span data-stu-id="6cdce-119">SQL_COPT_SS_CLIENT_CONNECTION_ID</span></span>  
 <span data-ttu-id="6cdce-120">SQL_COPT_SS_CLIENT_CONNECTION_ID 属性は、クライアント接続 ID を取得します。この ID を使用すると、次の情報を検索できます。</span><span class="sxs-lookup"><span data-stu-id="6cdce-120">The SQL_COPT_SS_CLIENT_CONNECTION_ID attribute retrieves the client connection ID, which can then be used to locate:</span></span>  
  
-   <span data-ttu-id="6cdce-121">XEvent ログの診断情報 (有効な場合)。</span><span class="sxs-lookup"><span data-stu-id="6cdce-121">Diagnostic information in the XEvents log, when enabled.</span></span>  
  
-   <span data-ttu-id="6cdce-122">接続リング バッファーの接続エラー情報。</span><span class="sxs-lookup"><span data-stu-id="6cdce-122">Connection error information in the connection ring buffer.</span></span>  
  
-   <span data-ttu-id="6cdce-123">データ アクセスのトレース ログの診断情報 (有効な場合)。</span><span class="sxs-lookup"><span data-stu-id="6cdce-123">Diagnostic information in the data access tracing logs, when enabled.</span></span>  
  
 <span data-ttu-id="6cdce-124">詳細については、「[拡張イベントログの診断情報へのアクセス](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cdce-124">For more information, see [Accessing Diagnostic Information in the Extended Events Log](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).</span></span>  
  
|<span data-ttu-id="6cdce-125">値</span><span class="sxs-lookup"><span data-stu-id="6cdce-125">Value</span></span>|<span data-ttu-id="6cdce-126">説明</span><span class="sxs-lookup"><span data-stu-id="6cdce-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6cdce-127">SQL_ERROR</span><span class="sxs-lookup"><span data-stu-id="6cdce-127">SQL_ERROR</span></span>|<span data-ttu-id="6cdce-128">接続に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="6cdce-128">The connection failed.</span></span>|  
|<span data-ttu-id="6cdce-129">SQL_SUCCESS</span><span class="sxs-lookup"><span data-stu-id="6cdce-129">SQL_SUCCESS</span></span>|<span data-ttu-id="6cdce-130">接続に成功しました。</span><span class="sxs-lookup"><span data-stu-id="6cdce-130">The connection succeeded.</span></span> <span data-ttu-id="6cdce-131">クライアント接続 ID は出力バッファーで見つかります。</span><span class="sxs-lookup"><span data-stu-id="6cdce-131">The client connection ID will be found in the output buffer.</span></span>|  
  
## <a name="sql_copt_ss_perf_data"></a><span data-ttu-id="6cdce-132">SQL_COPT_SS_PERF_DATA</span><span class="sxs-lookup"><span data-stu-id="6cdce-132">SQL_COPT_SS_PERF_DATA</span></span>  
 <span data-ttu-id="6cdce-133">SQL_COPT_SS_PERF_DATA 属性は、現在のドライバーのパフォーマンス統計情報を保持する SQLPERF 構造体へのポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="6cdce-133">The SQL_COPT_SS_PERF_DATA attribute returns a pointer to a SQLPERF structure containing the current driver performance statistics.</span></span> <span data-ttu-id="6cdce-134">`SQLGetConnectAttr`パフォーマンスログが有効になっていない場合、は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="6cdce-134">`SQLGetConnectAttr` will return NULL if performance logging is not enabled.</span></span> <span data-ttu-id="6cdce-135">SQLPERF 構造体内の統計情報がドライバーで動的に更新されることはありません。</span><span class="sxs-lookup"><span data-stu-id="6cdce-135">The statistics in the SQLPERF structure are not dynamically updated by the driver.</span></span> <span data-ttu-id="6cdce-136">`SQLGetConnectAttr`パフォーマンス統計を更新する必要があるたびに、を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6cdce-136">Call `SQLGetConnectAttr` each time the performance statistics need to be refreshed.</span></span>  
  
|<span data-ttu-id="6cdce-137">値</span><span class="sxs-lookup"><span data-stu-id="6cdce-137">Value</span></span>|<span data-ttu-id="6cdce-138">説明</span><span class="sxs-lookup"><span data-stu-id="6cdce-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6cdce-139">NULL</span><span class="sxs-lookup"><span data-stu-id="6cdce-139">NULL</span></span>|<span data-ttu-id="6cdce-140">パフォーマンスのログ記録が無効です。</span><span class="sxs-lookup"><span data-stu-id="6cdce-140">Performance logging is not enabled.</span></span>|  
|<span data-ttu-id="6cdce-141">その他の値</span><span class="sxs-lookup"><span data-stu-id="6cdce-141">Any other value</span></span>|<span data-ttu-id="6cdce-142">SQLPERF 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6cdce-142">A pointer to a SQLPERF structure.</span></span>|  
  
## <a name="sql_copt_ss_perf_query"></a><span data-ttu-id="6cdce-143">SQL_COPT_SS_PERF_QUERY</span><span class="sxs-lookup"><span data-stu-id="6cdce-143">SQL_COPT_SS_PERF_QUERY</span></span>  
 <span data-ttu-id="6cdce-144">SQL_COPT_SS_PERF_QUERY 属性は、実行時間の長いクエリのログ記録が有効の場合に TRUE を返します。</span><span class="sxs-lookup"><span data-stu-id="6cdce-144">The SQL_COPT_SS_PERF_QUERY attribute returns TRUE if logging of long running queries is enabled.</span></span> <span data-ttu-id="6cdce-145">クエリのログ記録が無効の場合は FALSE を返します。</span><span class="sxs-lookup"><span data-stu-id="6cdce-145">The request returns FALSE if query logging is not active.</span></span>  
  
## <a name="sql_copt_ss_user_data"></a><span data-ttu-id="6cdce-146">SQL_COPT_SS_USER_DATA</span><span class="sxs-lookup"><span data-stu-id="6cdce-146">SQL_COPT_SS_USER_DATA</span></span>  
 <span data-ttu-id="6cdce-147">SQL_COPT_SS_USER_DATA 属性は、ユーザー データ ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="6cdce-147">The SQL_COPT_SS_USER_DATA attribute retrieves the user-data pointer.</span></span> <span data-ttu-id="6cdce-148">ユーザー データはクライアントのメモリに格納され、接続ごとに記録されます。</span><span class="sxs-lookup"><span data-stu-id="6cdce-148">User data is stored in client-owned memory and recorded per connection.</span></span> <span data-ttu-id="6cdce-149">ユーザー データ ポインターが設定されていない場合、SQL_UD_NOTSET という NULL ポインターが返されます。</span><span class="sxs-lookup"><span data-stu-id="6cdce-149">If the user-data pointer has not been set, SQL_UD_NOTSET, a NULL pointer, is returned.</span></span>  
  
|<span data-ttu-id="6cdce-150">値</span><span class="sxs-lookup"><span data-stu-id="6cdce-150">Value</span></span>|<span data-ttu-id="6cdce-151">説明</span><span class="sxs-lookup"><span data-stu-id="6cdce-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6cdce-152">SQL_UD_NOTSET</span><span class="sxs-lookup"><span data-stu-id="6cdce-152">SQL_UD_NOTSET</span></span>|<span data-ttu-id="6cdce-153">ユーザー データ ポインターが設定されていません。</span><span class="sxs-lookup"><span data-stu-id="6cdce-153">No user-data pointer is set.</span></span>|  
|<span data-ttu-id="6cdce-154">その他の値</span><span class="sxs-lookup"><span data-stu-id="6cdce-154">Any other value</span></span>|<span data-ttu-id="6cdce-155">ユーザー データへのポインターです。</span><span class="sxs-lookup"><span data-stu-id="6cdce-155">A pointer to the user data.</span></span>|  
  
## <a name="sqlgetconnectattr-support-for-service-principal-names-spns"></a><span data-ttu-id="6cdce-156">SQLGetConnectAttr によるサービス プリンシパル名 (SPN) のサポート</span><span class="sxs-lookup"><span data-stu-id="6cdce-156">SQLGetConnectAttr Support for Service Principal Names (SPNs)</span></span>  
 <span data-ttu-id="6cdce-157">SQLGetConnectAttr を使用すると、SQL_COPT_SS_SERVER_SPN、SQL_COPT_SS_FAILOVER_PARTNER_SPN、SQL_COPT_SS_MUTUALLY_AUTHENTICATED、および SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD の新しい接続属性の値を照会できます。</span><span class="sxs-lookup"><span data-stu-id="6cdce-157">SQLGetConnectAttr can be used to query the value of the new connection attributes SQL_COPT_SS_SERVER_SPN, SQL_COPT_SS_FAILOVER_PARTNER_SPN, SQL_COPT_SS_MUTUALLY_AUTHENTICATED, and SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD.</span></span> <span data-ttu-id="6cdce-158">(SQLGetConnectOption を使用してこれらの値を照会することもできます)。</span><span class="sxs-lookup"><span data-stu-id="6cdce-158">(SQLGetConnectOption can also be used to query these values.)</span></span>  
  
 <span data-ttu-id="6cdce-159">SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD は、Windows 認証を使用する、開いている接続でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="6cdce-159">SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD is only available for open connections that use Windows Authentication.</span></span>  
  
 <span data-ttu-id="6cdce-160">SQL_COPT_SS_SERVER_SPN または SQL_COPT_SS_FAILOVER_PARTNER が設定されていない場合は、既定値 (空の文字列) が返されます。</span><span class="sxs-lookup"><span data-stu-id="6cdce-160">If SQL_COPT_SS_SERVER_SPN or SQL_COPT_SS_FAILOVER_PARTNER has not been set, the default value (an empty string) is returned.</span></span>  
  
 <span data-ttu-id="6cdce-161">Spn の詳細については、「[クライアント接続 &#40;ODBC&#41;のサービスプリンシパル名 &#40;spn&#41; ](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cdce-161">For more information about SPNs, see [Service Principal Names &#40;SPNs&#41; in Client Connections &#40;ODBC&#41;](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cdce-162">参照</span><span class="sxs-lookup"><span data-stu-id="6cdce-162">See Also</span></span>  
 <span data-ttu-id="6cdce-163">[SQLGetConnectAttr 関数](https://go.microsoft.com/fwlink/?LinkId=59347) </span><span class="sxs-lookup"><span data-stu-id="6cdce-163">[SQLGetConnectAttr Function](https://go.microsoft.com/fwlink/?LinkId=59347) </span></span>  
 <span data-ttu-id="6cdce-164">[ODBC API の実装の詳細](odbc-api-implementation-details.md) </span><span class="sxs-lookup"><span data-stu-id="6cdce-164">[ODBC API Implementation Details](odbc-api-implementation-details.md) </span></span>  
 <span data-ttu-id="6cdce-165">[SET QUOTED_IDENTIFIER &#40;Transact-sql&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6cdce-165">[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql) </span></span>  
 <span data-ttu-id="6cdce-166">[SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6cdce-166">[SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span></span>  
 <span data-ttu-id="6cdce-167">[SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6cdce-167">[SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span></span>  
 [<span data-ttu-id="6cdce-168">SET ANSI_WARNINGS &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6cdce-168">SET ANSI_WARNINGS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-ansi-warnings-transact-sql)  
  
  
