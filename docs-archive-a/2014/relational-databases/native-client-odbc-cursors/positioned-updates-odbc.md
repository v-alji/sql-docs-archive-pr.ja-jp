---
title: 位置指定更新 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- SQLSetPos function
- SQLSetCursorName function
- ODBC applications, cursors
- cursors [ODBC], positioned updates
- positioned updates [ODBC]
- ODBC cursors, positioned updates
ms.assetid: ff404e02-630f-474d-b5d4-06442b756991
author: rothja
ms.author: jroth
ms.openlocfilehash: 20272014e32632117e6282e5929d1d21789852df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634520"
---
# <a name="positioned-updates-odbc"></a><span data-ttu-id="8b0b7-102">位置指定更新 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="8b0b7-102">Positioned Updates (ODBC)</span></span>
  <span data-ttu-id="8b0b7-103">ODBC では、カーソルで位置指定更新を実行するために、次の 2 とおりの方法をサポートします。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-103">ODBC supports two methods for performing positioned updates in a cursor:</span></span>  
  
-   <span data-ttu-id="8b0b7-104">**SQLSetPos**</span><span class="sxs-lookup"><span data-stu-id="8b0b7-104">**SQLSetPos**</span></span>  
  
-   <span data-ttu-id="8b0b7-105">WHERE CURRENT OF 句</span><span class="sxs-lookup"><span data-stu-id="8b0b7-105">WHERE CURRENT OF clause</span></span>  
  
 <span data-ttu-id="8b0b7-106">最も一般的な方法は、 **SQLSetPos**を使用することです。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-106">The more common approach is to use **SQLSetPos**.</span></span> <span data-ttu-id="8b0b7-107">次のオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-107">It has the following options.</span></span>  
  
 <span data-ttu-id="8b0b7-108">SQL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8b0b7-108">SQL_POSITION</span></span>  
 <span data-ttu-id="8b0b7-109">現在の行セットの特定行にカーソルを位置付けます。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-109">Positions the cursor on a specific row in the current rowset.</span></span>  
  
 <span data-ttu-id="8b0b7-110">SQL_REFRESH</span><span class="sxs-lookup"><span data-stu-id="8b0b7-110">SQL_REFRESH</span></span>  
 <span data-ttu-id="8b0b7-111">カーソルが現在位置付けられている行から取り出した値で、結果セット列にバインドされているプログラム変数を更新します。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-111">Refreshes program variables bound to the result set columns with the values from the row the cursor is currently positioned on.</span></span>  
  
 <span data-ttu-id="8b0b7-112">SQL_UPDATE</span><span class="sxs-lookup"><span data-stu-id="8b0b7-112">SQL_UPDATE</span></span>  
 <span data-ttu-id="8b0b7-113">結果セット列にバインドされているプログラム変数に格納されている値で、カーソルの現在行を更新します。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-113">Updates the current row in the cursor with the values stored in the program variables bound to the result set columns.</span></span>  
  
 <span data-ttu-id="8b0b7-114">SQL_DELETE</span><span class="sxs-lookup"><span data-stu-id="8b0b7-114">SQL_DELETE</span></span>  
 <span data-ttu-id="8b0b7-115">カーソルの現在行を削除します。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-115">Deletes the current row in the cursor.</span></span>  
  
 <span data-ttu-id="8b0b7-116">**SQLSetPos**は、ステートメントハンドルカーソル属性がサーバーカーソルを使用するように設定されている場合に、任意のステートメントの結果セットと共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-116">**SQLSetPos** can be used with any statement result set when the statement handle cursor attributes are set to use server cursors.</span></span> <span data-ttu-id="8b0b7-117">結果セットの列を、プログラム変数にバインドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-117">The result set columns must be bound to program variables.</span></span> <span data-ttu-id="8b0b7-118">アプリケーションから行がフェッチされるとすぐに、 **SQLSetPos**(SQL_POSTION) を呼び出して、行にカーソルを置きます。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-118">As soon as the application has fetched a row it calls **SQLSetPos**(SQL_POSTION) to position the cursor on the row.</span></span> <span data-ttu-id="8b0b7-119">その後、アプリケーションは SQLSetPos(SQL_DELETE) を呼び出して現在行を削除するか、新しいデータ値をバインドされているプログラム変数に移動し、SQLSetPos(SQL_UPDATE) を呼び出して現在行を更新します。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-119">The application could then call SQLSetPos(SQL_DELETE) to delete the current row, or it can move new data values into the bound program variables and call SQLSetPos(SQL_UPDATE) to update the current row.</span></span>  
  
 <span data-ttu-id="8b0b7-120">アプリケーションは、 **SQLSetPos**を使用して行セット内の任意の行を更新または削除できます。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-120">Applications can update or delete any row in the rowset with **SQLSetPos**.</span></span> <span data-ttu-id="8b0b7-121">**SQLSetPos**の呼び出しは、SQL ステートメントの構築と実行に代わる便利な方法です。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-121">Calling **SQLSetPos** is a convenient alternative to constructing and executing an SQL statement.</span></span> <span data-ttu-id="8b0b7-122">**SQLSetPos**は現在の行セットに対して動作し、 [sqlfetchscroll](../native-client-odbc-api/sqlfetchscroll.md)の呼び出しの後にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-122">**SQLSetPos** operates on the current rowset and can be used only after a call to [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md).</span></span>  
  
 <span data-ttu-id="8b0b7-123">行セットサイズは、SQL_ATTR_ROW_ARRAY_SIZE の属性引数を使用して[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)を呼び出すことによって設定されます。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-123">Rowset size is set by a call to [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) with an attribute argument of SQL_ATTR_ROW_ARRAY_SIZE.</span></span> <span data-ttu-id="8b0b7-124">**SQLSetPos**は新しい行セットサイズを使用しますが、 **sqlfetch**または**sqlfetchscroll**を呼び出した後に限られます。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-124">**SQLSetPos** uses a new rowset size, but only after a call to **SQLFetch** or **SQLFetchScroll**.</span></span> <span data-ttu-id="8b0b7-125">たとえば、行セットのサイズが変更された場合、 **SQLSetPos**が呼び出され、 **Sqlfetch**または**sqlfetchscroll**が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-125">For example, if the rowset size is changed, **SQLSetPos** is called and then **SQLFetch** or **SQLFetchScroll** is called.</span></span> <span data-ttu-id="8b0b7-126">**SQLSetPos**の呼び出しでは、古い行セットサイズが使用されますが、 **sqlfetch**または**sqlfetchscroll**では新しい行セットサイズが使用されます。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-126">The call to **SQLSetPos** uses the old rowset size, but **SQLFetch** or **SQLFetchScroll** uses the new rowset size.</span></span>  
  
 <span data-ttu-id="8b0b7-127">行セット内の先頭行の行番号は 1 です。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-127">The first row in the rowset is row number 1.</span></span> <span data-ttu-id="8b0b7-128">**SQLSetPos**の RowNumber 引数は、行セット内の行を識別する必要があります。つまり、その値は、1から最後にフェッチされた行の数までの範囲で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-128">The RowNumber argument in **SQLSetPos** must identify a row in the rowset; that is, its value must be in the range between 1 and the number of rows that were most recently fetched.</span></span> <span data-ttu-id="8b0b7-129">この値には、行セット サイズよりも小さい値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-129">This may be less than the rowset size.</span></span> <span data-ttu-id="8b0b7-130">RowNumber が 0 の場合、操作は行セット内のすべての行に適用されます。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-130">If RowNumber is 0, the operation applies to every row in the rowset.</span></span>  
  
 <span data-ttu-id="8b0b7-131">**SQLSetPos**の削除操作により、データソースはテーブルの選択された1つ以上の行を削除します。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-131">The delete operation of **SQLSetPos** makes the data source delete one or more selected rows of a table.</span></span> <span data-ttu-id="8b0b7-132">**Sqlsetpos**を使用して行を削除するには、アプリケーションは、操作が SQL_DELETE に設定された**sqlsetpos**を呼び出し、RowNumber を削除する行の番号に設定します。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-132">To delete rows with **SQLSetPos**, the application calls **SQLSetPos** with Operation set to SQL_DELETE and RowNumber set to the number of the row to delete.</span></span> <span data-ttu-id="8b0b7-133">RowNumber が 0 の場合は、行セット内のすべての行が削除されます。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-133">If RowNumber is 0, all rows in the rowset are deleted.</span></span>  
  
 <span data-ttu-id="8b0b7-134">**SQLSetPos**が戻った後、削除された行が現在の行になり、その状態が SQL_ROW_DELETED になります。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-134">After **SQLSetPos** returns, the deleted row is the current row and its status is SQL_ROW_DELETED.</span></span> <span data-ttu-id="8b0b7-135">この行は、 [SQLGetData](../native-client-odbc-api/sqlgetdata.md)や**SQLSetPos**の呼び出しなど、その他の位置指定操作では使用できません。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-135">The row cannot be used in any additional positioned operations, such as calls to [SQLGetData](../native-client-odbc-api/sqlgetdata.md) or **SQLSetPos**.</span></span>  
  
 <span data-ttu-id="8b0b7-136">行セットのすべての行を削除すると (RowNumber は0に等しくなります)、アプリケーションでは、 **SQLSetPos**の更新操作と同様に、行操作配列を使用してドライバーが特定の行を削除できないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-136">When you delete all rows of the rowset (RowNumber is equal to 0), the application can prevent the driver from deleting certain rows by using the row operation array just like for the update operation of **SQLSetPos**.</span></span>  
  
 <span data-ttu-id="8b0b7-137">削除対象の各行は、行セット内に存在する行でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-137">Every row that is deleted should be a row that exists in the result set.</span></span> <span data-ttu-id="8b0b7-138">フェッチによってアプリケーション バッファーが設定され、行の状態配列が維持されている場合は、これら各行位置の行の状態値が SQL_ROW_DELETED、SQL_ROW_ERROR、または SQL_ROW_NOROW であってはなりません。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-138">If the application buffers were filled by fetching, and if a row status array has been maintained, its values at each of these row positions should not be SQL_ROW_DELETED, SQL_ROW_ERROR, or SQL_ROW_NOROW.</span></span>  
  
 <span data-ttu-id="8b0b7-139">位置指定更新は、UPDATE、DELETE、および INSERT の各ステートメントに WHERE CURRENT OF 句を使用することによっても実行できます。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-139">Positioned updates can also be performed using the WHERE CURRENT OF clause on UPDATE, DELETE, and INSERT statements.</span></span> <span data-ttu-id="8b0b7-140">の現在のの部分には、 [Sqlgetcursor name](../native-client-odbc-api/sqlgetcursorname.md)関数が呼び出されたとき、または**SQLSetCursorName**を呼び出して指定できる、ODBC によって生成されるカーソル名が必要です。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-140">WHERE CURRENT OF requires a cursor name that ODBC will generate when the [SQLGetCursorName](../native-client-odbc-api/sqlgetcursorname.md) function is called, or which you can specify by calling **SQLSetCursorName**.</span></span> <span data-ttu-id="8b0b7-141">次に、ODBC アプリケーションで WHERE CURRENT OF 更新の実行に使用する一般的な手順を示します。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-141">The following are general steps used to perform a WHERE CURRENT OF update in an ODBC application:</span></span>  
  
-   <span data-ttu-id="8b0b7-142">**SQLSetCursorName**を呼び出して、ステートメントハンドルのカーソル名を設定します。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-142">Call **SQLSetCursorName** to establish a cursor name for the statement handle.</span></span>  
  
-   <span data-ttu-id="8b0b7-143">FOR UPDATE OF 句を指定した SELECT ステートメントを作成し、実行します。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-143">Build a SELECT statement with a FOR UPDATE OF clause and execute it.</span></span>  
  
-   <span data-ttu-id="8b0b7-144">行を取得するには、 **Sqlfetchscroll**を呼び出して行セットまたは**sqlfetch**を取得します。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-144">Call **SQLFetchScroll** to retrieve a rowset or **SQLFetch** to retrieve a row.</span></span>  
  
-   <span data-ttu-id="8b0b7-145">**SQLSetPos** (SQL_POSITION) を呼び出して、行にカーソルを置きます。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-145">Call **SQLSetPos** (SQL_POSITION) to position the cursor on the row.</span></span>  
  
-   <span data-ttu-id="8b0b7-146">**SQLSetCursorName**で設定したカーソル名を使用して、WHERE CURRENT OF 句を指定した UPDATE ステートメントをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-146">Build and execute an UPDATE statement with a WHERE CURRENT OF clause using the cursor name set with **SQLSetCursorName**.</span></span>  
  
 <span data-ttu-id="8b0b7-147">または、SELECT ステートメントを実行する前に**SQLSetCursorName**を呼び出すのではなく、select ステートメントを実行した後に**Sqlgetカーソル名**を呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-147">Alternatively, you could call **SQLGetCursorName** after you execute the SELECT statement instead of calling **SQLSetCursorName** before executing the SELECT statement.</span></span> <span data-ttu-id="8b0b7-148">**SQLSetCursorName**を使用してカーソル名を設定しなかった場合、 **SQLGETCURSOR name**は ODBC によって割り当てられた既定のカーソル名を返します。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-148">**SQLGetCursorName** returns a default cursor name assigned by ODBC if you do not set a cursor name using **SQLSetCursorName**.</span></span>  
  
 <span data-ttu-id="8b0b7-149">サーバーカーソルを使用している場合は、 **SQLSetPos**を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-149">**SQLSetPos** is preferred over WHERE CURRENT OF when you are using server cursors.</span></span> <span data-ttu-id="8b0b7-150">ODBC カーソル ライブラリで静的で更新可能なカーソルを使用している場合、カーソル ライブラリは、基になるテーブルのキー値を指定した WHERE 句を追加することで、WHERE CURRENT OF 更新を実装します。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-150">If you are using a static, updatable cursor with the ODBC cursor library, the cursor library implements WHERE CURRENT OF updates by adding a WHERE clause with the key values for the underlying table.</span></span> <span data-ttu-id="8b0b7-151">テーブル内のキーが一意でない場合、意図しない更新が行われることがあります。</span><span class="sxs-lookup"><span data-stu-id="8b0b7-151">This can cause unintended updates if the keys in the table are not unique.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b0b7-152">参照</span><span class="sxs-lookup"><span data-stu-id="8b0b7-152">See Also</span></span>  
 [<span data-ttu-id="8b0b7-153">ODBC&#41;&#40;カーソルの使用</span><span class="sxs-lookup"><span data-stu-id="8b0b7-153">Using Cursors &#40;ODBC&#41;</span></span>](using-cursors-odbc.md)  
  
  
