---
title: カーソル行セットサイズ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], rowset size
- ODBC cursors, rowset size
- rowsets [ODBC]
ms.assetid: 2febe2ae-fdc1-490e-a79f-c516bc8e7c3f
author: rothja
ms.author: jroth
ms.openlocfilehash: 83c4e55025e6e3724f354f022760b7ba1e2f10e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643297"
---
# <a name="cursor-rowset-size"></a><span data-ttu-id="87954-102">カーソルの行セット サイズ</span><span class="sxs-lookup"><span data-stu-id="87954-102">Cursor Rowset Size</span></span>
  <span data-ttu-id="87954-103">ODBC カーソルでは、一度にフェッチできる行数は制限されません。</span><span class="sxs-lookup"><span data-stu-id="87954-103">ODBC cursors are not limited to fetching one row at a time.</span></span> <span data-ttu-id="87954-104">**Sqlfetch**または[sqlfetchscroll](../../native-client-odbc-api/sqlfetchscroll.md)を呼び出すたびに、複数の行を取得できます。</span><span class="sxs-lookup"><span data-stu-id="87954-104">They can retrieve multiple rows in each call to **SQLFetch** or [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md).</span></span> <span data-ttu-id="87954-105">Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のようなクライアント/サーバー型のデータベースで作業しているときは、1 回に複数行を取得する方が効率的です。</span><span class="sxs-lookup"><span data-stu-id="87954-105">When you are working with a client/server database such as Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], it is more efficient to fetch several rows at a time.</span></span> <span data-ttu-id="87954-106">フェッチで返される行の数は行セットサイズと呼ばれ、 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)の SQL_ATTR_ROW_ARRAY_SIZE を使用して指定されます。</span><span class="sxs-lookup"><span data-stu-id="87954-106">The number of rows returned on a fetch is called the rowset size and is specified by using the SQL_ATTR_ROW_ARRAY_SIZE of [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).</span></span>  
  
```  
SQLUINTEGER uwRowsize;  
SQLSetStmtAttr(m_hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)uwRowsetSize, SQL_IS_UINTEGER);  
```  
  
 <span data-ttu-id="87954-107">行セット サイズが 2 以上のカーソルをブロック カーソルと呼びます。</span><span class="sxs-lookup"><span data-stu-id="87954-107">Cursors with a rowset size greater than 1 are called block cursors.</span></span>  
  
 <span data-ttu-id="87954-108">ブロック カーソルの結果セット列は、次の 2 つの方法でバインドできます。</span><span class="sxs-lookup"><span data-stu-id="87954-108">There are two options for binding result set columns for block cursors:</span></span>  
  
-   <span data-ttu-id="87954-109">列方向のバインド</span><span class="sxs-lookup"><span data-stu-id="87954-109">Column-wise binding</span></span>  
  
     <span data-ttu-id="87954-110">各列が変数の配列にバインドされます。</span><span class="sxs-lookup"><span data-stu-id="87954-110">Each column is bound to an array of variables.</span></span> <span data-ttu-id="87954-111">各配列には行セット サイズと同じ数の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="87954-111">Each array has the same number of elements as the rowset size.</span></span>  
  
-   <span data-ttu-id="87954-112">行方向のバインド</span><span class="sxs-lookup"><span data-stu-id="87954-112">Row-wise binding</span></span>  
  
     <span data-ttu-id="87954-113">1 行のすべての列のデータとインジケーターが含まれる構造体を使用して配列が構築されます。</span><span class="sxs-lookup"><span data-stu-id="87954-113">An array is built using structures that hold the data and indicators for all the columns in a row.</span></span> <span data-ttu-id="87954-114">この配列には行セット サイズと同じ数の構造体が含まれます。</span><span class="sxs-lookup"><span data-stu-id="87954-114">The array has the same number of structures as the rowset size.</span></span>  
  
 <span data-ttu-id="87954-115">列方向または行方向のバインドのいずれかを使用すると、 **Sqlfetch**または**sqlfetchscroll**を呼び出すたびに、バインドされた配列に、取得した行セットのデータが格納されます。</span><span class="sxs-lookup"><span data-stu-id="87954-115">When either column-wise or row-wise binding is used, each call to **SQLFetch** or **SQLFetchScroll** fills the bound arrays with data from the rowset retrieved.</span></span>  
  
 <span data-ttu-id="87954-116">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md)を使用して、ブロックカーソルから列データを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="87954-116">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md) can also be used to retrieve column data from a block cursor.</span></span> <span data-ttu-id="87954-117">**SQLGetData**は一度に1行ずつ動作するため、 **SQLGetData**を呼び出す前に**SQLSetPos**を呼び出して、行セット内の特定の行を現在の行として設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="87954-117">Because **SQLGetData** works one row at a time, **SQLSetPos** must be called to set a specific row in the rowset as the current row before calling **SQLGetData**.</span></span>  
  
 <span data-ttu-id="87954-118">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーでは、行セットを使用して結果セット全体をすばやく取得する最適化が提供されます。</span><span class="sxs-lookup"><span data-stu-id="87954-118">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver offers an optimization using rowsets to retrieve a whole result set quickly.</span></span> <span data-ttu-id="87954-119">この最適化を使用するには、 **SQLExecDirect**または**sqlexecute**が呼び出されたときに、カーソルの属性を既定値 (順方向専用、読み取り専用、行セットサイズ = 1) に設定します。</span><span class="sxs-lookup"><span data-stu-id="87954-119">To use this optimization, set the cursor attributes to their defaults (forward-only, read-only, rowset size = 1) at the time **SQLExecDirect** or **SQLExecute** is called.</span></span> <span data-ttu-id="87954-120">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーは、既定の結果セットを設定します。</span><span class="sxs-lookup"><span data-stu-id="87954-120">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver sets up a default result set.</span></span> <span data-ttu-id="87954-121">スクロールを使用しないでクライアントに結果を送信する場合は、既定の結果セットの方がサーバー カーソルよりも効率的です。</span><span class="sxs-lookup"><span data-stu-id="87954-121">This is more efficient than server cursors when transferring results to the client without scrolling.</span></span> <span data-ttu-id="87954-122">ステートメントを実行後、行セット サイズを増やし、列方向のバインドか行方向のバインドを使用します。</span><span class="sxs-lookup"><span data-stu-id="87954-122">After the statement has been executed, increase the rowset size and use either column-wise or row-wise binding.</span></span> <span data-ttu-id="87954-123">これにより、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 既定の結果セットを使用してクライアントに結果行を効率的に送信でき [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。一方、NATIVE client ODBC ドライバーでは、クライアントのネットワークバッファーから行を継続的にプルします。</span><span class="sxs-lookup"><span data-stu-id="87954-123">This lets [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] use a default result set to send result rows efficiently to the client, while the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver continuously pulls rows from the network buffers on the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87954-124">参照</span><span class="sxs-lookup"><span data-stu-id="87954-124">See Also</span></span>  
 [<span data-ttu-id="87954-125">カーソルのプロパティ</span><span class="sxs-lookup"><span data-stu-id="87954-125">Cursor Properties</span></span>](cursor-properties.md)  
  
  
