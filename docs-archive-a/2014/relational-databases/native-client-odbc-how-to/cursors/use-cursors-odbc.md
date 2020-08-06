---
title: カーソルの使用 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], how to topics
ms.assetid: c502736f-bca0-45c3-ae25-d2ad52d296bf
author: rothja
ms.author: jroth
ms.openlocfilehash: e08156b03407c7a05d86278c11482a568d651f5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630985"
---
# <a name="use-cursors-odbc"></a><span data-ttu-id="23358-102">カーソルの使用 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="23358-102">Use Cursors (ODBC)</span></span>
    
### <a name="to-use-cursors"></a><span data-ttu-id="23358-103">カーソルを使用するには</span><span class="sxs-lookup"><span data-stu-id="23358-103">To use cursors</span></span>  
  
1.  <span data-ttu-id="23358-104">[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) を呼び出して、目的のカーソル属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="23358-104">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the desired cursor attributes:</span></span>  
  
     <span data-ttu-id="23358-105">SQL_ATTR_CURSOR_TYPE および SQL_ATTR_CONCURRENCY 属性を設定します (これは推奨オプションです)。</span><span class="sxs-lookup"><span data-stu-id="23358-105">Set the SQL_ATTR_CURSOR_TYPE and SQL_ATTR_CONCURRENCY attributes (this is the preferred option).</span></span>  
  
     <span data-ttu-id="23358-106">または</span><span class="sxs-lookup"><span data-stu-id="23358-106">Or</span></span>  
  
     <span data-ttu-id="23358-107">SQL_CURSOR_SCROLLABLE および SQL_CURSOR_SENSITIVITY 属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="23358-107">Set the SQL_CURSOR_SCROLLABLE and SQL_CURSOR_SENSITIVITY attributes.</span></span>  
  
2.  <span data-ttu-id="23358-108">[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) を呼び出して、SQL_ATTR_ROW_ARRAY_SIZE 属性を使用して行セットのサイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="23358-108">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the rowset size by using the SQL_ATTR_ROW_ARRAY_SIZE attribute.</span></span>  
  
3.  <span data-ttu-id="23358-109">WHERE CURRENT OF 句を使用して位置指定更新を実行する場合は、[SQLSetCursorName](https://go.microsoft.com/fwlink/?LinkId=58406) を呼び出して、カーソル名を設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="23358-109">Optionally, call [SQLSetCursorName](https://go.microsoft.com/fwlink/?LinkId=58406) to set a cursor name if positioned updates will be done by using the WHERE CURRENT OF clause.</span></span>  
  
4.  <span data-ttu-id="23358-110">SQL ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="23358-110">Execute the SQL statement.</span></span>  
  
5.  <span data-ttu-id="23358-111">WHERE CURRENT OF 句を使用して位置指定更新を実行する場合、手順 3. で [SQLSetCursorName](https://go.microsoft.com/fwlink/?LinkId=58406) を使用してカーソル名を指定していなかったときは、[SQLGetCursorName](../../native-client-odbc-api/sqlgetcursorname.md) を呼び出してカーソル名を取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="23358-111">Optionally, call [SQLGetCursorName](../../native-client-odbc-api/sqlgetcursorname.md) to get the cursor name if positioned updates will be done by using the WHERE CURRENT OF clause and a cursor name was not supplied with [SQLSetCursorName](https://go.microsoft.com/fwlink/?LinkId=58406) in Step 3.</span></span>  
  
6.  <span data-ttu-id="23358-112">[SQLNumResultCols](../../native-client-odbc-api/sqlnumresultcols.md) を呼び出して、行セット内の列数 (C) を取得します。</span><span class="sxs-lookup"><span data-stu-id="23358-112">Call [SQLNumResultCols](../../native-client-odbc-api/sqlnumresultcols.md) to get the number of columns (C) in the rowset.</span></span>  
  
     <span data-ttu-id="23358-113">列方向のバインドを使用します。</span><span class="sxs-lookup"><span data-stu-id="23358-113">Use column-wise binding.</span></span>  
  
     <span data-ttu-id="23358-114">\- または</span><span class="sxs-lookup"><span data-stu-id="23358-114">\- or -</span></span>  
  
     <span data-ttu-id="23358-115">行方向のバインドを使用します。</span><span class="sxs-lookup"><span data-stu-id="23358-115">Use row-wise binding.</span></span>  
  
7.  <span data-ttu-id="23358-116">必要に応じてカーソルから行セットをフェッチします。</span><span class="sxs-lookup"><span data-stu-id="23358-116">Fetch rowsets from the cursor as desired.</span></span>  
  
8.  <span data-ttu-id="23358-117">[SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) を呼び出して、別の結果セットが使用可能かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="23358-117">Call [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) to determine if another result set is available.</span></span>  
  
    -   <span data-ttu-id="23358-118">SQL_SUCCESS が返された場合は、別の結果セットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="23358-118">If it returns SQL_SUCCESS, another result set is available.</span></span>  
  
    -   <span data-ttu-id="23358-119">SQL_NO_DATA が返された場合は、他に使用できる結果セットはありません。</span><span class="sxs-lookup"><span data-stu-id="23358-119">If it returns SQL_NO_DATA, no more result sets are available.</span></span>  
  
    -   <span data-ttu-id="23358-120">SQL_SUCCESS_WITH_INFO または SQL_ERROR が返された場合は、[SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) を呼び出して、PRINT ステートメントまたは RAISERROR ステートメントからの出力が使用可能かどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="23358-120">If it returns SQL_SUCCESS_WITH_INFO or SQL_ERROR, call [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) to determine if the output from a PRINT or RAISERROR statement is available.</span></span>  
  
     <span data-ttu-id="23358-121">バインドされたステートメントのパラメーターが出力パラメーターまたはストアド プロシージャの戻り値に使用されている場合は、バインドされたパラメーターのバッファーでデータを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="23358-121">If bound statement parameters are used for output parameters or the return value of a stored procedure, use the data now available in the bound parameter buffers.</span></span>  
  
     <span data-ttu-id="23358-122">バインドされたパラメーターが使用される場合は、[SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) または [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) への各呼び出しで、SQL ステートメントが S 回実行されます。S は、バインドされたパラメーターの配列内にある要素数です。</span><span class="sxs-lookup"><span data-stu-id="23358-122">When bound parameters are used, each call to [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) or [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) will have executed the SQL statement S times, where S is the number of elements in the array of bound parameters.</span></span> <span data-ttu-id="23358-123">つまり、処理する結果のセットが S 個あることを意味します。これらの結果の各セットには、結果セット、出力パラメーター、および通常 SQL ステートメントの 1 回の実行で返されるリターン コードがすべて含まれます。</span><span class="sxs-lookup"><span data-stu-id="23358-123">This means that there will be S sets of results to process, where each set of results comprises all of the result sets, output parameters, and return codes usually returned by a single execution of the SQL statement.</span></span>  
  
     <span data-ttu-id="23358-124">結果セットに計算行が含まれている場合、各計算行は個々の結果セットとして使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="23358-124">Note that when a result set contains compute rows, each compute row is made available as a separate result set.</span></span> <span data-ttu-id="23358-125">これらの計算結果セットは標準行内に点在し、標準行は複数の結果セットに分割されます。</span><span class="sxs-lookup"><span data-stu-id="23358-125">These compute result sets are interspersed within the normal rows and break normal rows into multiple result sets.</span></span>  
  
9. <span data-ttu-id="23358-126">必要に応じて、SQL_UNBIND を使用して [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) を呼び出し、バインドされた列バッファーを解放します。</span><span class="sxs-lookup"><span data-stu-id="23358-126">Optionally, call [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) with SQL_UNBIND to release any bound column buffers.</span></span>  
  
10. <span data-ttu-id="23358-127">別の結果セットが使用できる場合は、手順 6. に進みます。</span><span class="sxs-lookup"><span data-stu-id="23358-127">If another result set is available, go to Step 6.</span></span>  
  
     <span data-ttu-id="23358-128">手順 9. で、部分的に処理された結果セットで [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) を呼び出すと、残りの結果セットがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="23358-128">In Step 9, calling [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) on a partially processed result set clears the remainder of the result set.</span></span> <span data-ttu-id="23358-129">[SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) を呼び出してクリアする方法もあります。</span><span class="sxs-lookup"><span data-stu-id="23358-129">Another way to clear a partially processed result set is to call [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md).</span></span>  
  
     <span data-ttu-id="23358-130">使用するカーソルの種類を制御するには、SQL_ATTR_CURSOR_TYPE と SQL_ATTR_CONCURRENCY を設定するか、SQL_ATTR_CURSOR_SENSITIVITY と SQL_ATTR_CURSOR_SCROLLABLE を設定します。</span><span class="sxs-lookup"><span data-stu-id="23358-130">You can control the type of cursor used by setting either SQL_ATTR_CURSOR_TYPE and SQL_ATTR_CONCURRENCY, or by setting SQL_ATTR_CURSOR_SENSITIVITY and SQL_ATTR_CURSOR_SCROLLABLE.</span></span> <span data-ttu-id="23358-131">カーソルの動作を指定するこの 2 つの方法を組み合わせて実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="23358-131">You should not mix the two methods of specifying cursor behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23358-132">参照</span><span class="sxs-lookup"><span data-stu-id="23358-132">See Also</span></span>  
 [<span data-ttu-id="23358-133">カーソルの使用方法に関するトピック &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="23358-133">Using Cursors How-to Topics &#40;ODBC&#41;</span></span>](using-cursors-how-to-topics-odbc.md)  
  
  
