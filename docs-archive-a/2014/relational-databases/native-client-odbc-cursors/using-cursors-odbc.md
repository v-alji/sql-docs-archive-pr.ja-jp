---
title: カーソルの使用 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC]
- ODBC cursors
ms.assetid: 51322f92-0d76-44c9-9c33-9223676cf1d3
author: rothja
ms.author: jroth
ms.openlocfilehash: 61afedab4f4a1e309a08d9c2421ca7889811da8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739888"
---
# <a name="using-cursors-odbc"></a><span data-ttu-id="26d06-102">カーソルの使用 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="26d06-102">Using Cursors (ODBC)</span></span>
  <span data-ttu-id="26d06-103">ODBC では、次のことを可能にするカーソル モデルがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="26d06-103">ODBC supports a cursor model that allows:</span></span>  
  
-   <span data-ttu-id="26d06-104">複数種類のカーソル</span><span class="sxs-lookup"><span data-stu-id="26d06-104">Several types of cursors.</span></span>  
  
-   <span data-ttu-id="26d06-105">カーソル内でのスクロールと位置指定</span><span class="sxs-lookup"><span data-stu-id="26d06-105">Scrolling and positioning within a cursor.</span></span>  
  
-   <span data-ttu-id="26d06-106">複数のコンカレンシー オプション。</span><span class="sxs-lookup"><span data-stu-id="26d06-106">Several concurrency options.</span></span>  
  
-   <span data-ttu-id="26d06-107">位置指定更新。</span><span class="sxs-lookup"><span data-stu-id="26d06-107">Positioned updates.</span></span>  
  
 <span data-ttu-id="26d06-108">ODBC アプリケーションでは、カーソルを宣言して開いたり、カーソル関連の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用することはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="26d06-108">ODBC applications rarely declare and open cursors or use any cursor-related [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="26d06-109">ODBC では、SQL ステートメントから返されたすべての結果セットに対して自動的にカーソルを開きます。</span><span class="sxs-lookup"><span data-stu-id="26d06-109">ODBC automatically opens a cursor for every result set returned from an SQL statement.</span></span> <span data-ttu-id="26d06-110">カーソルの特性は、SQL ステートメントが実行される前に、 [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)で設定されたステートメント属性によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="26d06-110">The characteristics of the cursors are controlled by statement attributes set with [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) before the SQL statement is executed.</span></span> <span data-ttu-id="26d06-111">結果セットの処理に使用する ODBC API 関数では、フェッチ、スクロール、位置指定更新など、すべてのカーソル機能がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="26d06-111">The ODBC API functions for processing result sets support the full range of cursor functionality, including fetching, scrolling, and positioned updates.</span></span>  
  
 <span data-ttu-id="26d06-112">[!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトと ODBC アプリケーションのカーソル操作の比較を次に示します。</span><span class="sxs-lookup"><span data-stu-id="26d06-112">This is a comparison of how [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts and ODBC applications work with cursors.</span></span>  
  
|<span data-ttu-id="26d06-113">アクション</span><span class="sxs-lookup"><span data-stu-id="26d06-113">Action</span></span>|[!INCLUDE[tsql](../../includes/tsql-md.md)]|<span data-ttu-id="26d06-114">ODBC</span><span class="sxs-lookup"><span data-stu-id="26d06-114">ODBC</span></span>|  
|------------|------------------------|----------|  
|<span data-ttu-id="26d06-115">カーソル動作を定義する</span><span class="sxs-lookup"><span data-stu-id="26d06-115">Define cursor behavior</span></span>|<span data-ttu-id="26d06-116">DECLARE CURSOR パラメーターによる指定</span><span class="sxs-lookup"><span data-stu-id="26d06-116">Specify through DECLARE CURSOR parameters</span></span>|<span data-ttu-id="26d06-117">[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)を使用してカーソルの属性を設定する</span><span class="sxs-lookup"><span data-stu-id="26d06-117">Set cursor attributes by using [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)</span></span>|  
|<span data-ttu-id="26d06-118">カーソルを開く</span><span class="sxs-lookup"><span data-stu-id="26d06-118">Open a cursor</span></span>|<span data-ttu-id="26d06-119">カーソルを開く*cursor_name*を宣言</span><span class="sxs-lookup"><span data-stu-id="26d06-119">DECLARE CURSOR OPEN *cursor_name*</span></span>|<span data-ttu-id="26d06-120">**SQLExecDirect**または**sqlexecute**</span><span class="sxs-lookup"><span data-stu-id="26d06-120">**SQLExecDirect** or **SQLExecute**</span></span>|  
|<span data-ttu-id="26d06-121">行をフェッチする</span><span class="sxs-lookup"><span data-stu-id="26d06-121">Fetch rows</span></span>|<span data-ttu-id="26d06-122">FETCH</span><span class="sxs-lookup"><span data-stu-id="26d06-122">FETCH</span></span>|<span data-ttu-id="26d06-123">**Sqlfetch**または[sqlfetchscroll](../native-client-odbc-api/sqlfetchscroll.md)</span><span class="sxs-lookup"><span data-stu-id="26d06-123">**SQLFetch** or [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)</span></span>|  
|<span data-ttu-id="26d06-124">位置指定更新を行う</span><span class="sxs-lookup"><span data-stu-id="26d06-124">Positioned update</span></span>|<span data-ttu-id="26d06-125">UPDATE または DELETE の WHERE CURRENT OF 句</span><span class="sxs-lookup"><span data-stu-id="26d06-125">WHERE CURRENT OF clause on UPDATE or DELETE</span></span>|<span data-ttu-id="26d06-126">**SQLSetPos**</span><span class="sxs-lookup"><span data-stu-id="26d06-126">**SQLSetPos**</span></span>|  
|<span data-ttu-id="26d06-127">カーソルを閉じる</span><span class="sxs-lookup"><span data-stu-id="26d06-127">Close a cursor</span></span>|<span data-ttu-id="26d06-128">割り当て解除*CURSOR_NAME*終了</span><span class="sxs-lookup"><span data-stu-id="26d06-128">CLOSE *cursor_name* DEALLOCATE</span></span>|[<span data-ttu-id="26d06-129">SQLCloseCursor</span><span class="sxs-lookup"><span data-stu-id="26d06-129">SQLCloseCursor</span></span>](../native-client-odbc-api/sqlclosecursor.md)|  
  
 <span data-ttu-id="26d06-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に実装されているサーバー カーソルでは、ODBC カーソル モデルの機能がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="26d06-130">The server cursors implemented in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support the functionality of the ODBC cursor model.</span></span> <span data-ttu-id="26d06-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ドライバーでは、サーバー カーソルを使用して ODBC API のカーソル機能がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="26d06-131">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client driver uses server cursors to support the cursor functionality of the ODBC API.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26d06-132">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="26d06-132">In This Section</span></span>  
  
-   [<span data-ttu-id="26d06-133">カーソルの実装方法</span><span class="sxs-lookup"><span data-stu-id="26d06-133">How Cursors Are Implemented</span></span>](implementation/how-cursors-are-implemented.md)  
  
-   [<span data-ttu-id="26d06-134">カーソルの種類</span><span class="sxs-lookup"><span data-stu-id="26d06-134">Cursor Types</span></span>](cursor-types.md)  
  
-   [<span data-ttu-id="26d06-135">カーソル動作</span><span class="sxs-lookup"><span data-stu-id="26d06-135">Cursor Behaviors</span></span>](cursor-behaviors.md)  
  
-   [<span data-ttu-id="26d06-136">カーソルのプロパティ</span><span class="sxs-lookup"><span data-stu-id="26d06-136">Cursor Properties</span></span>](properties/cursor-properties.md)  
  
-   [<span data-ttu-id="26d06-137">ODBC&#41;&#40;のカーソルプログラミングの詳細</span><span class="sxs-lookup"><span data-stu-id="26d06-137">Cursor Programming Details &#40;ODBC&#41;</span></span>](programming/cursor-programming-details-odbc.md)  
  
-   [<span data-ttu-id="26d06-138">行のスクロールとフェッチ</span><span class="sxs-lookup"><span data-stu-id="26d06-138">Scrolling and Fetching Rows</span></span>](../native-client-ole-db-rowsets/fetching-rows.md)  
  
-   [<span data-ttu-id="26d06-139">位置指定更新 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="26d06-139">Positioned Updates &#40;ODBC&#41;</span></span>](positioned-updates-odbc.md)  
  
## <a name="see-also"></a><span data-ttu-id="26d06-140">参照</span><span class="sxs-lookup"><span data-stu-id="26d06-140">See Also</span></span>  
 <span data-ttu-id="26d06-141">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="26d06-141">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 <span data-ttu-id="26d06-142">[Transact-sql&#41;を閉じる &#40;](/sql/t-sql/language-elements/close-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="26d06-142">[CLOSE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/close-transact-sql) </span></span>  
 <span data-ttu-id="26d06-143">[カーソル](../../relational-databases/cursors.md) </span><span class="sxs-lookup"><span data-stu-id="26d06-143">[Cursors](../../relational-databases/cursors.md) </span></span>  
 <span data-ttu-id="26d06-144">[Transact-sql&#41;の割り当てを解除 &#40;](/sql/t-sql/language-elements/deallocate-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="26d06-144">[DEALLOCATE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/deallocate-transact-sql) </span></span>  
 <span data-ttu-id="26d06-145">[Transact-sql&#41;&#40;カーソルの宣言](/sql/t-sql/language-elements/declare-cursor-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="26d06-145">[DECLARE CURSOR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-cursor-transact-sql) </span></span>  
 <span data-ttu-id="26d06-146">[FETCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/fetch-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="26d06-146">[FETCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/fetch-transact-sql) </span></span>  
 [<span data-ttu-id="26d06-147">OPEN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26d06-147">OPEN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/open-transact-sql)  
  
  
