---
title: 行セットのバインドの使用 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowset binding [ODBC]
ms.assetid: a7be05f0-6b11-4b53-9fbc-501e591eef09
author: rothja
ms.author: jroth
ms.openlocfilehash: e2e0671fd1140e72005cd1a7532ea581f077382f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630982"
---
# <a name="use-rowset-binding-odbc"></a><span data-ttu-id="15b40-102">行セットのバインドの使用 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="15b40-102">Use Rowset Binding (ODBC)</span></span>
    
### <a name="to-use-column-wise-binding"></a><span data-ttu-id="15b40-103">列方向のバインドを使用するには</span><span class="sxs-lookup"><span data-stu-id="15b40-103">To use column-wise binding</span></span>  
  
1.  <span data-ttu-id="15b40-104">バインドされた各列で、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="15b40-104">For each bound column, do the following:</span></span>  
  
    -   <span data-ttu-id="15b40-105">データ値を格納するための R 個以上の列バッファーの配列を割り当てます。R は行セット内の行の数です。</span><span class="sxs-lookup"><span data-stu-id="15b40-105">Allocate an array of R (or more) column buffers to store data values, where R is number of rows in the rowset.</span></span>  
  
    -   <span data-ttu-id="15b40-106">必要に応じて、データ長を格納するための R 個以上の列バッファーの配列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="15b40-106">Optionally, allocate an array of R (or more) column buffers to store data lengths.</span></span>  
  
    -   <span data-ttu-id="15b40-107">[SQLBindCol](../../native-client-odbc-api/sqlbindcol.md)を呼び出して、列のデータ値とデータ長の配列を行セットの列にバインドします。</span><span class="sxs-lookup"><span data-stu-id="15b40-107">Call [SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) to bind the column's data value and data length arrays to the column of the rowset.</span></span>  
  
2.  <span data-ttu-id="15b40-108">[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)を呼び出して、次の属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="15b40-108">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
    -   <span data-ttu-id="15b40-109">SQL_ATTR_ROW_ARRAY_SIZE を、行セットの行の数 (R) に設定します。</span><span class="sxs-lookup"><span data-stu-id="15b40-109">Set SQL_ATTR_ROW_ARRAY_SIZE to the number of rows in the rowset (R).</span></span>  
  
    -   <span data-ttu-id="15b40-110">SQL_ATTR_ROW_BIND_TYPE を SQL_BIND_BY_COLUMN に設定します。</span><span class="sxs-lookup"><span data-stu-id="15b40-110">Set SQL_ATTR_ROW_BIND_TYPE to SQL_BIND_BY_COLUMN.</span></span>  
  
    -   <span data-ttu-id="15b40-111">SQL_ATTR_ROWS FETCHED_PTR 属性を、フェッチされた行の数を格納する SQLUINTEGER 変数を指すように設定します。</span><span class="sxs-lookup"><span data-stu-id="15b40-111">Set the SQL_ATTR_ROWS FETCHED_PTR attribute to point to a SQLUINTEGER variable to hold the number of rows fetched.</span></span>  
  
    -   <span data-ttu-id="15b40-112">SQL_ATTR_ROW_STATUS_PTR を、行状態インジケーターを格納する SQLUSSMALLINT 変数の配列 [R] を指すように設定します。</span><span class="sxs-lookup"><span data-stu-id="15b40-112">Set SQL_ATTR_ROW_STATUS_PTR to point to an array[R] of SQLUSSMALLINT variables to hold the row-status indicators.</span></span>  
  
3.  <span data-ttu-id="15b40-113">ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="15b40-113">Execute the statement.</span></span>  
  
4.  <span data-ttu-id="15b40-114">[Sqlfetch](https://go.microsoft.com/fwlink/?LinkId=58401)または[sqlfetchscroll](../../native-client-odbc-api/sqlfetchscroll.md)を呼び出すたびに R 行が取得され、データがバインドされた列に転送されます。</span><span class="sxs-lookup"><span data-stu-id="15b40-114">Each call to [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) or [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) retrieves R rows and transfers the data into the bound columns.</span></span>  
  
### <a name="to-use-row-wise-binding"></a><span data-ttu-id="15b40-115">行方向のバインドを使用するには</span><span class="sxs-lookup"><span data-stu-id="15b40-115">To use row-wise binding</span></span>  
  
1.  <span data-ttu-id="15b40-116">構造体の配列 [R] を割り当てます。この R は行セット内の行数です。</span><span class="sxs-lookup"><span data-stu-id="15b40-116">Allocate an array[R] of structures, where R is the number of rows in the rowset.</span></span> <span data-ttu-id="15b40-117">構造体には各列について 1 つの要素があり、各要素は 2 つの部分で構成されています。</span><span class="sxs-lookup"><span data-stu-id="15b40-117">The structure has one element for each column, and each element has two parts:</span></span>  
  
    -   <span data-ttu-id="15b40-118">最初の部分は、列データを格納する適切なデータ型の変数です。</span><span class="sxs-lookup"><span data-stu-id="15b40-118">The first part is a variable of the appropriate data type to hold the column data.</span></span>  
  
    -   <span data-ttu-id="15b40-119">2 つ目の部分は、列状態インジケーターを格納する SQLINTEGER 変数です。</span><span class="sxs-lookup"><span data-stu-id="15b40-119">The second part is a SQLINTEGER variable to hold the column status indicator.</span></span>  
  
2.  <span data-ttu-id="15b40-120">[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)を呼び出して、次の属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="15b40-120">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
    -   <span data-ttu-id="15b40-121">SQL_ATTR_ROW_ARRAY_SIZE を、行セットの行の数 (R) に設定します。</span><span class="sxs-lookup"><span data-stu-id="15b40-121">Set SQL_ATTR_ROW_ARRAY_SIZE to the number of rows in the rowset (R).</span></span>  
  
    -   <span data-ttu-id="15b40-122">SQL_ATTR_ROW_BIND_TYPE を、手順 1. で割り当てた構造体のサイズに設定します。</span><span class="sxs-lookup"><span data-stu-id="15b40-122">Set SQL_ATTR_ROW_BIND_TYPE to the size of the structure allocated in Step 1.</span></span>  
  
    -   <span data-ttu-id="15b40-123">SQL_ATTR_ROWS_FETCHED_PTR 属性を、フェッチされた行の数を格納する SQLUINTEGER 変数を指すように設定します。</span><span class="sxs-lookup"><span data-stu-id="15b40-123">Set the SQL_ATTR_ROWS_FETCHED_PTR attribute to point to a SQLUINTEGER variable to hold the number of rows fetched.</span></span>  
  
    -   <span data-ttu-id="15b40-124">SQL_ATTR_PARAMS_STATUS_PTR を、行状態インジケーターを格納する SQLUSSMALLINT 変数の配列 [R] を指すように設定します。</span><span class="sxs-lookup"><span data-stu-id="15b40-124">Set SQL_ATTR_PARAMS_STATUS_PTR to point to an array[R] of SQLUSSMALLINT variables to hold the row-status indicators.</span></span>  
  
3.  <span data-ttu-id="15b40-125">結果セットの各列に対して、 [SQLBindCol](../../native-client-odbc-api/sqlbindcol.md)を呼び出して、列のデータ値とデータ長のポインターが、手順 1. で割り当てられた構造体の配列の最初の要素にある変数を指すようにします。</span><span class="sxs-lookup"><span data-stu-id="15b40-125">For each column in the result set, call [SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) to point the data value and data length pointer of the column to their variables in the first element of the array of structures allocated in Step 1.</span></span>  
  
4.  <span data-ttu-id="15b40-126">ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="15b40-126">Execute the statement.</span></span>  
  
5.  <span data-ttu-id="15b40-127">[Sqlfetch](https://go.microsoft.com/fwlink/?LinkId=58401)または[sqlfetchscroll](../../native-client-odbc-api/sqlfetchscroll.md)を呼び出すたびに R 行が取得され、データがバインドされた列に転送されます。</span><span class="sxs-lookup"><span data-stu-id="15b40-127">Each call to [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) or [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) retrieves R rows and transfers the data into the bound columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15b40-128">参照</span><span class="sxs-lookup"><span data-stu-id="15b40-128">See Also</span></span>  
 <span data-ttu-id="15b40-129">[カーソルの使用方法に関するトピック &#40;ODBC&#41;](using-cursors-how-to-topics-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="15b40-129">[Using Cursors How-to Topics &#40;ODBC&#41;](using-cursors-how-to-topics-odbc.md) </span></span>  
 <span data-ttu-id="15b40-130">[カーソルの実装方法](../../native-client-odbc-cursors/implementation/how-cursors-are-implemented.md) </span><span class="sxs-lookup"><span data-stu-id="15b40-130">[How Cursors Are Implemented](../../native-client-odbc-cursors/implementation/how-cursors-are-implemented.md) </span></span>  
 [<span data-ttu-id="15b40-131">ODBC &#40;カーソルの使用&#41;</span><span class="sxs-lookup"><span data-stu-id="15b40-131">Use Cursors &#40;ODBC&#41;</span></span>](use-cursors-odbc.md)  
  
  
