---
title: カーソルオプションの設定 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], options
ms.assetid: 0e72b48a-fc5a-4656-8cf5-39f57d8c1565
author: rothja
ms.author: jroth
ms.openlocfilehash: 877c2596c87ce50295a15912493661c6dd4e0305
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739865"
---
# <a name="set-cursor-options-odbc"></a><span data-ttu-id="1902b-102">カーソル オプションの設定 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="1902b-102">Set Cursor Options (ODBC)</span></span>
  <span data-ttu-id="1902b-103">カーソルオプションを設定するには、 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)を呼び出して、カーソルの動作を制御するステートメントオプションを設定または[SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md)に取得します。</span><span class="sxs-lookup"><span data-stu-id="1902b-103">To set cursor options, Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set or [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) to get the statement options that control cursor behavior.</span></span>  
  
|<span data-ttu-id="1902b-104">*属性*</span><span class="sxs-lookup"><span data-stu-id="1902b-104">*Attribute*</span></span>|<span data-ttu-id="1902b-105">指定内容</span><span class="sxs-lookup"><span data-stu-id="1902b-105">Specifies</span></span>|  
|-----------------|---------------|  
|<span data-ttu-id="1902b-106">SQL_ATTR_CURSOR_TYPE</span><span class="sxs-lookup"><span data-stu-id="1902b-106">SQL_ATTR_CURSOR_TYPE</span></span>|<span data-ttu-id="1902b-107">カーソルの種類。順方向専用、静的、動的、キーセット ドリブンのいずれか</span><span class="sxs-lookup"><span data-stu-id="1902b-107">Cursor type of forward-only, static, dynamic, or keyset-driven</span></span>|  
|<span data-ttu-id="1902b-108">SQL_ATTR_CONCURRENCY</span><span class="sxs-lookup"><span data-stu-id="1902b-108">SQL_ATTR_CONCURRENCY</span></span>|<span data-ttu-id="1902b-109">コンカレンシー制御オプション。読み取り専用、ロック、タイムスタンプを使用するオプティミスティック、値を使用するオプティミスティックのいずれか</span><span class="sxs-lookup"><span data-stu-id="1902b-109">Concurrency control option of read-only, locking, optimistic using timestamps, or optimistic using values</span></span>|  
|<span data-ttu-id="1902b-110">SQL_ATTR_ROW_ARRAY_SIZE</span><span class="sxs-lookup"><span data-stu-id="1902b-110">SQL_ATTR_ROW_ARRAY_SIZE</span></span>|<span data-ttu-id="1902b-111">フェッチごとに取得される行数</span><span class="sxs-lookup"><span data-stu-id="1902b-111">Number of rows retrieved in each fetch</span></span>|  
|<span data-ttu-id="1902b-112">SQL_ATTR_CURSOR_SENSITIVITY</span><span class="sxs-lookup"><span data-stu-id="1902b-112">SQL_ATTR_CURSOR_SENSITIVITY</span></span>|<span data-ttu-id="1902b-113">他の接続によるカーソル行の更新を、カーソルで表示するかしないか</span><span class="sxs-lookup"><span data-stu-id="1902b-113">Cursor that does or does not show updates to cursor rows made by other connections</span></span>|  
|<span data-ttu-id="1902b-114">SQL_ATTR_CURSOR_SCROLLABLE</span><span class="sxs-lookup"><span data-stu-id="1902b-114">SQL_ATTR_CURSOR_SCROLLABLE</span></span>|<span data-ttu-id="1902b-115">カーソルを前後にスクロール可能</span><span class="sxs-lookup"><span data-stu-id="1902b-115">Cursor that can be scrolled forward and backward</span></span>|  
  
 <span data-ttu-id="1902b-116">これらの属性の既定値 (順方向専用、読み取り専用、行セット サイズ 1) では、サーバー カーソルを使用しません。</span><span class="sxs-lookup"><span data-stu-id="1902b-116">The default values for these attributes (forward-only, read-only, rowset size of 1) do not use server cursors.</span></span> <span data-ttu-id="1902b-117">サーバー カーソルを使用するには、少なくともこれらの属性のいずれかを既定値以外に設定する必要があります。また、実行するステートメントを、単一の SELECT ステートメントか、単一の SELECT ステートメントを含むストアド プロシージャにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1902b-117">To use server cursors, at least one of these attributes must be set to a value other than the default, and the statement being executed must be a single SELECT statement or a stored procedure that contains a single SELECT statement.</span></span> <span data-ttu-id="1902b-118">サーバー カーソルの使用時に、サーバー カーソルによってサポートされていない句 (COMPUTE、COMPUTE BY、FOR BROWSE、および INTO) を SELECT ステートメントで使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="1902b-118">When using server cursors, SELECT statements cannot use clauses not supported by server cursors: COMPUTE, COMPUTE BY, FOR BROWSE, and INTO.</span></span>  
  
 <span data-ttu-id="1902b-119">使用するカーソルの種類を制御するには、SQL_ATTR_CURSOR_TYPE と SQL_ATTR_CONCURRENCY を設定するか、SQL_ATTR_CURSOR_SENSITIVITY と SQL_ATTR_CURSOR_SCROLLABLE を設定します。</span><span class="sxs-lookup"><span data-stu-id="1902b-119">You can control the type of cursor used either by setting SQL_ATTR_CURSOR_TYPE and SQL_ATTR_CONCURRENCY, or by setting SQL_ATTR_CURSOR_SENSITIVITY and SQL_ATTR_CURSOR_SCROLLABLE.</span></span> <span data-ttu-id="1902b-120">カーソルの動作を指定するこの 2 つの方法を組み合わせて実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="1902b-120">You should not mix the two methods of specifying cursor behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1902b-121">例</span><span class="sxs-lookup"><span data-stu-id="1902b-121">Example</span></span>  
 <span data-ttu-id="1902b-122">次のサンプルでは、ステートメント ハンドルを割り当て、行のバージョンに基づくオプティミスティック コンカレンシーを使用する動的カーソルを種類として設定してから、SELECT を実行します。</span><span class="sxs-lookup"><span data-stu-id="1902b-122">The following sample allocates a statement handle, sets a dynamic cursor type with row versioning optimistic concurrency, and then executes a SELECT.</span></span>  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER)SQL_CURSOR_DYNAMIC, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CONCURRENCY, SQLPOINTER)SQL_CONCUR_ROWVER, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, SELECT au_lname FROM authors", SQL_NTS);  
```  
  
## <a name="example"></a><span data-ttu-id="1902b-123">例</span><span class="sxs-lookup"><span data-stu-id="1902b-123">Example</span></span>  
 <span data-ttu-id="1902b-124">次のサンプルでは、ステートメント ハンドルを割り当て、スクロール可能な反映型カーソルを設定してから、SELECT を実行します。</span><span class="sxs-lookup"><span data-stu-id="1902b-124">The following sample allocates a statement handle, sets a scrollable, sensitive cursor, and then executes a SELECT</span></span>  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
  
// Set the cursor options and execute the statement.  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SCROLLABLE, SQLPOINTER)SQL_SCROLLABLE, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SENSITIVITY, SQLPOINTER)SQL_INSENSITIVE, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, select au_lname from authors", SQL_NTS);  
```  
  
## <a name="see-also"></a><span data-ttu-id="1902b-125">参照</span><span class="sxs-lookup"><span data-stu-id="1902b-125">See Also</span></span>  
 [<span data-ttu-id="1902b-126">クエリの実行方法に関するトピック &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="1902b-126">Executing Queries How-to Topics &#40;ODBC&#41;</span></span>](executing-queries-how-to-topics-odbc.md)  
  
  
