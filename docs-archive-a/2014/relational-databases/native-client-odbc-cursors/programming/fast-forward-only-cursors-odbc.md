---
title: 高速順方向専用カーソル (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fast forward-only cursors
- forward-only cursors
- cursors [ODBC], fast forward-only
- ODBC cursors, fast forward-only
ms.assetid: 0707d07e-fc95-42ed-9280-b7e508ac8c62
author: rothja
ms.author: jroth
ms.openlocfilehash: de8d82a0c72ad51741a3785fba2910f691028cba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643310"
---
# <a name="fast-forward-only-cursors-odbc"></a><span data-ttu-id="f852a-102">高速順方向専用カーソル (ODBC)</span><span class="sxs-lookup"><span data-stu-id="f852a-102">Fast Forward-Only Cursors (ODBC)</span></span>
  <span data-ttu-id="f852a-103">Native Client ODBC ドライバーは、のインスタンスに接続されている場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 順方向専用の読み取り専用カーソルのパフォーマンスの最適化をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f852a-103">When connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports performance optimizations for forward-only, read-only cursors.</span></span> <span data-ttu-id="f852a-104">高速順方向専用カーソルは、既定の結果セットに類似した方法で、ドライバーとサーバーによって内部的に実装されます。</span><span class="sxs-lookup"><span data-stu-id="f852a-104">Fast forward-only cursors are implemented internally by the driver and server in a manner very similar to default result sets.</span></span> <span data-ttu-id="f852a-105">高速順方向専用カーソルには、パフォーマンスが高いこと以外にも、次のような特性があります。</span><span class="sxs-lookup"><span data-stu-id="f852a-105">Besides having high performance, fast forward-only cursors also have these characteristics:</span></span>  
  
-   <span data-ttu-id="f852a-106">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md)はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f852a-106">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md) is not supported.</span></span> <span data-ttu-id="f852a-107">結果セットの列を、プログラム変数にバインドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f852a-107">The result set columns must be bound to program variables.</span></span>  
  
-   <span data-ttu-id="f852a-108">サーバーはカーソルの最後に達したことを検出すると、そのカーソルを自動的に閉じます。</span><span class="sxs-lookup"><span data-stu-id="f852a-108">The server automatically closes the cursor when the end of the cursor is detected.</span></span> <span data-ttu-id="f852a-109">アプリケーションは引き続き[SqlcloSQLFreeStmt](../../native-client-odbc-api/sqlclosecursor.md)または[SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md)(SQL_CLOSE) を呼び出す必要がありますが、ドライバーからサーバーにクローズ要求を送信する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f852a-109">The application must still call [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) or [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md)(SQL_CLOSE), but the driver does not have to send the close request to the server.</span></span> <span data-ttu-id="f852a-110">この動作により、ネットワーク経由でのサーバーとのやり取りが抑えられます。</span><span class="sxs-lookup"><span data-stu-id="f852a-110">This saves a roundtrip across the network to the server.</span></span>  
  
 <span data-ttu-id="f852a-111">アプリケーションでは、ドライバー固有のステートメント属性 SQL_SOPT_SS_CURSOR_OPTIONS を使用して高速順方向専用カーソルを要求します。</span><span class="sxs-lookup"><span data-stu-id="f852a-111">The application requests fast forward-only cursors using the driver-specific statement attribute SQL_SOPT_SS_CURSOR_OPTIONS.</span></span> <span data-ttu-id="f852a-112">SQL_SOPT_SS_CURSOR_OPTIONS 属性に SQL_CO_FFO を設定すると、高速順方向専用カーソルが有効になりますが、autofetch オプションは有効になりません。</span><span class="sxs-lookup"><span data-stu-id="f852a-112">When set to SQL_CO_FFO, fast forward-only cursors are enabled without autofetch.</span></span> <span data-ttu-id="f852a-113">SQL_CO_FFO_AF を設定すると、autofetch オプションも有効になります。</span><span class="sxs-lookup"><span data-stu-id="f852a-113">When set to SQL_CO_FFO_AF, the autofetch option is also enabled.</span></span> <span data-ttu-id="f852a-114">Autofetch の詳細については、「 [Using autofetch WITH ODBC](using-autofetch-with-odbc-cursors.md)cursor」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f852a-114">For more information about autofetch, see [Using Autofetch with ODBC Cursors](using-autofetch-with-odbc-cursors.md).</span></span>  
  
 <span data-ttu-id="f852a-115">autofetch オプションを有効にした高速順方向専用カーソルは、サーバーとのやり取りを 1 度だけ行って小さい結果セットを取得する場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="f852a-115">Fast forward-only cursors with autofetch can be used to retrieve a small result set with only one roundtrip to the server.</span></span> <span data-ttu-id="f852a-116">次の手順では、 *n*が返される行の数を示します。</span><span class="sxs-lookup"><span data-stu-id="f852a-116">In these steps, *n* is the number of rows to be returned:</span></span>  
  
1.  <span data-ttu-id="f852a-117">SQL_SOPT_SS_CURSOR_OPTIONS を SQL_CO_FFO_AF に設定します。</span><span class="sxs-lookup"><span data-stu-id="f852a-117">Set SQL_SOPT_SS_CURSOR_OPTIONS to SQL_CO_FFO_AF.</span></span>  
  
2.  <span data-ttu-id="f852a-118">SQL_ATTR_ROW_ARRAY_SIZE を*n* + 1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="f852a-118">Set SQL_ATTR_ROW_ARRAY_SIZE to *n* + 1.</span></span>  
  
3.  <span data-ttu-id="f852a-119">結果列を*n* + 1 個の要素の配列にバインドします ( *n* + 1 行が実際にフェッチされた場合は安全です)。</span><span class="sxs-lookup"><span data-stu-id="f852a-119">Bind the result columns to arrays of *n* + 1 elements (to be safe if *n* + 1 rows are actually fetched).</span></span>  
  
4.  <span data-ttu-id="f852a-120">**SQLExecDirect**または**sqlexecute**のいずれかを使用してカーソルを開きます。</span><span class="sxs-lookup"><span data-stu-id="f852a-120">Open the cursor with either **SQLExecDirect** or **SQLExecute**.</span></span>  
  
5.  <span data-ttu-id="f852a-121">返された状態が SQL_SUCCESS の場合は、 **SQLFreeStmt**または**sqlcloを**呼び出してカーソルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="f852a-121">If the return status is SQL_SUCCESS, then call **SQLFreeStmt** or **SQLCloseCursor** to close the cursor.</span></span> <span data-ttu-id="f852a-122">行のすべてのデータが、バインドされたプログラム変数に格納されます。</span><span class="sxs-lookup"><span data-stu-id="f852a-122">All data for the rows will be in the bound program variables.</span></span>  
  
 <span data-ttu-id="f852a-123">これらの手順で、 **SQLExecDirect**または**sqlexecute**は、autofetch オプションが有効になっている状態で、cursor open 要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="f852a-123">With these steps, the **SQLExecDirect** or **SQLExecute** sends a cursor open request with the autofetch option enabled.</span></span> <span data-ttu-id="f852a-124">クライアントからこの要求を 1 つ受け取ると、サーバーでは次の手順が実行されます。</span><span class="sxs-lookup"><span data-stu-id="f852a-124">On that single request from the client, the server:</span></span>  
  
-   <span data-ttu-id="f852a-125">カーソルを開きます。</span><span class="sxs-lookup"><span data-stu-id="f852a-125">Opens the cursor.</span></span>  
  
-   <span data-ttu-id="f852a-126">結果セットを作成してクライアントに行を送信します。</span><span class="sxs-lookup"><span data-stu-id="f852a-126">Builds the result set and sends the rows to the client.</span></span>  
  
-   <span data-ttu-id="f852a-127">行セットのサイズを結果セットの行数よりも 1 だけ多いサイズに設定したので、サーバーでカーソルが最後まで達したことが検出され、そのカーソルが閉じられます。</span><span class="sxs-lookup"><span data-stu-id="f852a-127">Because the rowset size was set to 1 more than the number of rows in the result set, the server detects the end of the cursor and closes the cursor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f852a-128">参照</span><span class="sxs-lookup"><span data-stu-id="f852a-128">See Also</span></span>  
 [<span data-ttu-id="f852a-129">ODBC&#41;&#40;のカーソルプログラミングの詳細</span><span class="sxs-lookup"><span data-stu-id="f852a-129">Cursor Programming Details &#40;ODBC&#41;</span></span>](cursor-programming-details-odbc.md)  
  
  
