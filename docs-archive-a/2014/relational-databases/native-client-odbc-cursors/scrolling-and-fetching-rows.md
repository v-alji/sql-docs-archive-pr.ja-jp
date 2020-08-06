---
title: 行のスクロールとフェッチ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- SQLFetchScroll function
- ODBC applications, cursors
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- fetching [ODBC]
- ODBC cursors, scrolling rows
ms.assetid: 9109f10d-326b-4a6d-8c97-831f60da8c4c
author: rothja
ms.author: jroth
ms.openlocfilehash: 97586f82ddddb79581b0f9c027aa60d7822b472c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739900"
---
# <a name="scrolling-and-fetching-rows"></a><span data-ttu-id="72500-102">行のスクロールとフェッチ</span><span class="sxs-lookup"><span data-stu-id="72500-102">Scrolling and Fetching Rows</span></span>
  <span data-ttu-id="72500-103">スクロール可能なカーソルを使用するには、ODBC アプリケーションでは次の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="72500-103">To use a scrollable cursor, an ODBC application must:</span></span>  
  
-   <span data-ttu-id="72500-104">[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)を使用してカーソル機能を設定します。</span><span class="sxs-lookup"><span data-stu-id="72500-104">Set the cursor capabilities using [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md).</span></span>  
  
-   <span data-ttu-id="72500-105">**Sqlexecute**または**SQLExecDirect**を使用してカーソルを開きます。</span><span class="sxs-lookup"><span data-stu-id="72500-105">Open the cursor using **SQLExecute** or **SQLExecDirect**.</span></span>  
  
-   <span data-ttu-id="72500-106">**Sqlfetch**または[sqlfetchscroll](../native-client-odbc-api/sqlfetchscroll.md)を使用して行をスクロールおよびフェッチします。</span><span class="sxs-lookup"><span data-stu-id="72500-106">Scroll and fetch rows using **SQLFetch** or [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md).</span></span>  
  
 <span data-ttu-id="72500-107">**Sqlfetch**と**Sqlfetchsroll**は、同時に行のブロックをフェッチできます。</span><span class="sxs-lookup"><span data-stu-id="72500-107">Both **SQLFetch** and **SQLFetchSroll** can fetch blocks of rows at a time.</span></span> <span data-ttu-id="72500-108">返される行の数は、SQL_ATTR_ROW_ARRAY_SIZE パラメーターを設定するために**SQLSetStmtAttr**を使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="72500-108">The number of rows returned is specified by using **SQLSetStmtAttr** to set the SQL_ATTR_ROW_ARRAY_SIZE parameter.</span></span>  
  
 <span data-ttu-id="72500-109">ODBC アプリケーションでは、 **Sqlfetch**を使用して、順方向専用カーソルを介してフェッチできます。</span><span class="sxs-lookup"><span data-stu-id="72500-109">ODBC applications can use **SQLFetch** to fetch through a forward-only cursor.</span></span>  
  
 <span data-ttu-id="72500-110">カーソルをスクロールするには、 **Sqlfetchscroll**を使用します。</span><span class="sxs-lookup"><span data-stu-id="72500-110">**SQLFetchScroll** is used to scroll around a cursor.</span></span> <span data-ttu-id="72500-111">**Sqlfetchscroll**は、相対フェッチ (現在の行セットの先頭から行セット*n*の行をフェッチ) と絶対フェッチ (行*n*で始まる行セットのフェッチ) に加えて、次の行セット、以前の行セット、最初の行セット、および最後の行セットのフェッチをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="72500-111">**SQLFetchScroll** supports fetching the next, prior, first, and last rowsets in addition to relative fetching (fetch the rowset *n* rows from the start of the current rowset) and absolute fetching (fetch the rowset starting at row *n*).</span></span> <span data-ttu-id="72500-112">絶対フェッチで*n*が負の値の場合、行は結果セットの末尾からカウントされます。</span><span class="sxs-lookup"><span data-stu-id="72500-112">If *n* is negative in an absolute fetch, rows are counted from the end of the result set.</span></span> <span data-ttu-id="72500-113">たとえば、行 -1 の絶対フェッチは、結果セット内にある最後の行を起点とした行セットをフェッチします。</span><span class="sxs-lookup"><span data-stu-id="72500-113">An absolute fetch of row -1 means to fetch the rowset that starts with the last row in the result set.</span></span>  
  
 <span data-ttu-id="72500-114">レポートなどのブロックカーソル機能に対してのみ**Sqlfetchscroll**を使用するアプリケーションは、次の行セットをフェッチするオプションのみを使用して、結果セットを1回だけ通過する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="72500-114">Applications that use **SQLFetchScroll** only for its block cursor capabilities, such as reports, are likely to pass through the result set a single time, using only the option to fetch the next rowset.</span></span> <span data-ttu-id="72500-115">一方、画面ベースのアプリケーションでは、 **Sqlfetchscroll**のすべての機能を利用できます。</span><span class="sxs-lookup"><span data-stu-id="72500-115">Screen-based applications, on the other hand, can take advantage of all the capabilities of **SQLFetchScroll**.</span></span> <span data-ttu-id="72500-116">アプリケーションで、行セットのサイズを画面に表示される行数に設定し、画面バッファーを結果セットにバインドすると、スクロールバーの操作を**Sqlfetchscroll**の呼び出しに直接変換できます。</span><span class="sxs-lookup"><span data-stu-id="72500-116">If the application sets the rowset size to the number of rows displayed on the screen and binds the screen buffers to the result set, it can translate scroll bar operations directly to calls to **SQLFetchScroll**.</span></span>  
  
|<span data-ttu-id="72500-117">スクロール バーの操作</span><span class="sxs-lookup"><span data-stu-id="72500-117">Scroll bar operation</span></span>|<span data-ttu-id="72500-118">SQLFetchScroll のスクロール操作</span><span class="sxs-lookup"><span data-stu-id="72500-118">SQLFetchScroll scrolling option</span></span>|  
|--------------------------|-------------------------------------|  
|<span data-ttu-id="72500-119">1 画面分上へ移動 (PageUp)</span><span class="sxs-lookup"><span data-stu-id="72500-119">Page up</span></span>|<span data-ttu-id="72500-120">SQL_FETCH_PRIOR</span><span class="sxs-lookup"><span data-stu-id="72500-120">SQL_FETCH_PRIOR</span></span>|  
|<span data-ttu-id="72500-121">1 画面分下へ移動 (PageDown)</span><span class="sxs-lookup"><span data-stu-id="72500-121">Page down</span></span>|<span data-ttu-id="72500-122">SQL_FETCH_NEXT</span><span class="sxs-lookup"><span data-stu-id="72500-122">SQL_FETCH_NEXT</span></span>|  
|<span data-ttu-id="72500-123">1 行上へ移動</span><span class="sxs-lookup"><span data-stu-id="72500-123">Line up</span></span>|<span data-ttu-id="72500-124">FetchOffset が-1 に等しい SQL_FETCH_RELATIVE</span><span class="sxs-lookup"><span data-stu-id="72500-124">SQL_FETCH_RELATIVE with FetchOffset equal to -1</span></span>|  
|<span data-ttu-id="72500-125">1 行下へ移動</span><span class="sxs-lookup"><span data-stu-id="72500-125">Line down</span></span>|<span data-ttu-id="72500-126">FetchOffset に 1 を指定した SQL_FETCH_RELATIVE </span><span class="sxs-lookup"><span data-stu-id="72500-126">SQL_FETCH_RELATIVE with FetchOffset equal to 1</span></span>|  
|<span data-ttu-id="72500-127">スクロール ボックスを先頭に移動</span><span class="sxs-lookup"><span data-stu-id="72500-127">Scroll box to top</span></span>|<span data-ttu-id="72500-128">SQL_FETCH_FIRST</span><span class="sxs-lookup"><span data-stu-id="72500-128">SQL_FETCH_FIRST</span></span>|  
|<span data-ttu-id="72500-129">スクロール ボックスを末尾に移動</span><span class="sxs-lookup"><span data-stu-id="72500-129">Scroll box to bottom</span></span>|<span data-ttu-id="72500-130">SQL_FETCH_LAST</span><span class="sxs-lookup"><span data-stu-id="72500-130">SQL_FETCH_LAST</span></span>|  
|<span data-ttu-id="72500-131">スクロール ボックスを任意の位置に移動</span><span class="sxs-lookup"><span data-stu-id="72500-131">Random scroll box position</span></span>|<span data-ttu-id="72500-132">SQL_FETCH_ABSOLUTE</span><span class="sxs-lookup"><span data-stu-id="72500-132">SQL_FETCH_ABSOLUTE</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="72500-133">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="72500-133">In This Section</span></span>  
  
-   [<span data-ttu-id="72500-134">ODBC での行のブックマーク</span><span class="sxs-lookup"><span data-stu-id="72500-134">Bookmarking Rows in ODBC</span></span>](scrolling-and-fetching-rows-bookmarking-rows-in-odbc.md)  
  
## <a name="see-also"></a><span data-ttu-id="72500-135">参照</span><span class="sxs-lookup"><span data-stu-id="72500-135">See Also</span></span>  
 [<span data-ttu-id="72500-136">ODBC&#41;&#40;カーソルの使用</span><span class="sxs-lookup"><span data-stu-id="72500-136">Using Cursors &#40;ODBC&#41;</span></span>](using-cursors-odbc.md)  
  
  
