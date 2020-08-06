---
title: ODBC での行のブックマーク |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- ODBC cursors, scrolling rows
- bookmarks [ODBC]
ms.assetid: 9cfcd243-c9d4-4c2a-abc4-399dbabe5f6b
author: rothja
ms.author: jroth
ms.openlocfilehash: def05f478c16dcbcdc91771925a11b0b91da2e9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739924"
---
# <a name="bookmarking-rows-in-odbc"></a><span data-ttu-id="1e34e-102">ODBC での行のブックマーク</span><span class="sxs-lookup"><span data-stu-id="1e34e-102">Bookmarking Rows in ODBC</span></span>
  <span data-ttu-id="1e34e-103">ブックマークは、データ行の識別に使われる値です。</span><span class="sxs-lookup"><span data-stu-id="1e34e-103">A bookmark is a value used to identify a row of data.</span></span> <span data-ttu-id="1e34e-104">ブックマーク値の意味を解釈できるのは、ドライバーまたはデータ ソースのみです。</span><span class="sxs-lookup"><span data-stu-id="1e34e-104">The meaning of the bookmark value is known only to the driver or data source.</span></span> <span data-ttu-id="1e34e-105">たとえば、ブックマークは、行番号のような単純な値の場合も、ディスク アドレスのような複雑な値の場合もあります。</span><span class="sxs-lookup"><span data-stu-id="1e34e-105">For example, it might be as simple as a row number or as complex as a disk address.</span></span> <span data-ttu-id="1e34e-106">ODBC では、アプリケーションが特定の行のブックマークを要求し、これを保存し、カーソルに戻して行に返します。</span><span class="sxs-lookup"><span data-stu-id="1e34e-106">In ODBC, the application requests a bookmark for a particular row, stores it, and passes it back to the cursor to return to the row.</span></span>  
  
 <span data-ttu-id="1e34e-107">[Sqlfetchscroll](../native-client-odbc-api/sqlfetchscroll.md)を使用して行をフェッチする場合、アプリケーションでは開始行を選択するための基礎としてブックマークを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1e34e-107">When fetching rows with [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md), an application can use a bookmark as a basis for selecting the starting row.</span></span> <span data-ttu-id="1e34e-108">これは、現在のカーソルの位置に依存しないので、絶対アドレスの形式になります。</span><span class="sxs-lookup"><span data-stu-id="1e34e-108">This is a form of absolute addressing because it does not depend on the current cursor position.</span></span> <span data-ttu-id="1e34e-109">ブックマークが付けられた行までスクロールするには、アプリケーションは SQL_FETCH_BOOKMARK の*Fetchorientation*を使用して**sqlfetchscroll**を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1e34e-109">To scroll to a bookmarked row, the application calls **SQLFetchScroll** with a *FetchOrientation* of SQL_FETCH_BOOKMARK.</span></span> <span data-ttu-id="1e34e-110">この操作では、SQL_ATTR_FETCH_BOOKMARK_PTR オプション属性によって示されるブックマークを使用します。</span><span class="sxs-lookup"><span data-stu-id="1e34e-110">This operation uses the bookmark pointed to by the SQL_ATTR_FETCH_BOOKMARK_PTR option attribute.</span></span> <span data-ttu-id="1e34e-111">結果として、そのブックマークによって識別される行で始まる行セットが返されます。</span><span class="sxs-lookup"><span data-stu-id="1e34e-111">It returns the rowset starting with the row identified by that bookmark.</span></span> <span data-ttu-id="1e34e-112">アプリケーションでは、 **Sqlfetchscroll**の呼び出しの*fetchoffset*引数でこの操作のオフセットを指定できます。</span><span class="sxs-lookup"><span data-stu-id="1e34e-112">An application can specify an offset for this operation in the *FetchOffset* argument of the call to **SQLFetchScroll**.</span></span> <span data-ttu-id="1e34e-113">オフセットを指定すると、結果の行セットの最初の行は、ブックマークで識別される行番号に FetchOffset 引数の数を加算した結果によって決まります。</span><span class="sxs-lookup"><span data-stu-id="1e34e-113">When an offset is specified, the first row of the returned rowset is determined by adding the number in the FetchOffset argument to the number of the row identified by the bookmark.</span></span> <span data-ttu-id="1e34e-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、静的カーソルとキーセット カーソルに対してのみブックマークがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="1e34e-114">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver only supports bookmarks on static and keyset cursors.</span></span> <span data-ttu-id="1e34e-115">ブックマークが設定されている場合に動的カーソルが要求されると、代わりにキーセット カーソルが開かれます。</span><span class="sxs-lookup"><span data-stu-id="1e34e-115">If a dynamic cursor is requested when bookmarks are set on, a keyset cursor is opened instead.</span></span>  
  
 <span data-ttu-id="1e34e-116">ブックマークを**Sqlbulkoperations**関数と共に使用して、ブックマークで始まる一連の行に対して操作を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="1e34e-116">Bookmarks can also be used with the **SQLBulkOperations** function to perform operations on a set of rows starting at the bookmark.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e34e-117">参照</span><span class="sxs-lookup"><span data-stu-id="1e34e-117">See Also</span></span>  
 [<span data-ttu-id="1e34e-118">行のスクロールとフェッチ</span><span class="sxs-lookup"><span data-stu-id="1e34e-118">Scrolling and Fetching Rows</span></span>](../native-client-ole-db-rowsets/fetching-rows.md)  
  
  
