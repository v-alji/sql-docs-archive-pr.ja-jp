---
title: カーソルの動作 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- version-based optimistic concurrency
- cursors [ODBC], cursor behaviors
- ODBC applications, cursors
- SQL_ATTR_CURSOR_SENSITIVITY option
- SQL_ATTR_CURSOR_SCROLLABLE option
- sensitivity behavior of cursor
- ODBC cursors, cursor behaviors
ms.assetid: 742ddcd2-232b-4aa1-9212-027df120ad35
author: rothja
ms.author: jroth
ms.openlocfilehash: 89c7c4e9a8dcffe03dd12f8013d5ed43810547f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640904"
---
# <a name="cursor-behaviors"></a><span data-ttu-id="044f3-102">カーソル動作</span><span class="sxs-lookup"><span data-stu-id="044f3-102">Cursor Behaviors</span></span>
  <span data-ttu-id="044f3-103">ODBC では、カーソルのスクロールの可否と感度を設定することでカーソル動作を指定する、ISO オプションがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="044f3-103">ODBC supports the ISO options for specifying the behavior of cursors by specifying their scrollability and sensitivity.</span></span> <span data-ttu-id="044f3-104">これらの動作は、 [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)の呼び出しで SQL_ATTR_CURSOR_SCROLLABLE オプションと SQL_ATTR_CURSOR_SENSITIVITY オプションを設定することによって指定します。</span><span class="sxs-lookup"><span data-stu-id="044f3-104">These behaviors are specified by setting the SQL_ATTR_CURSOR_SCROLLABLE and SQL_ATTR_CURSOR_SENSITIVITY options on a call to [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md).</span></span> <span data-ttu-id="044f3-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、次の特性を持つサーバー カーソルを要求して、これらのオプションを実装します。</span><span class="sxs-lookup"><span data-stu-id="044f3-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver implements these options by requesting server cursors with the following characteristics.</span></span>  
  
|<span data-ttu-id="044f3-106">カーソル動作の設定</span><span class="sxs-lookup"><span data-stu-id="044f3-106">Cursor behavior settings</span></span>|<span data-ttu-id="044f3-107">要求されるサーバー カーソルの特性</span><span class="sxs-lookup"><span data-stu-id="044f3-107">Server cursor characteristics requested</span></span>|  
|------------------------------|---------------------------------------------|  
|<span data-ttu-id="044f3-108">SQL_SCROLLABLE と SQL_SENSITIVE</span><span class="sxs-lookup"><span data-stu-id="044f3-108">SQL_SCROLLABLE and SQL_SENSITIVE</span></span>|<span data-ttu-id="044f3-109">キーセット ドリブン カーソルとバージョンに基づくオプティミスティック コンカレンシー</span><span class="sxs-lookup"><span data-stu-id="044f3-109">Keyset-driven cursor and version-based optimistic concurrency</span></span>|  
|<span data-ttu-id="044f3-110">SQL_SCROLLABLE と SQL_INSENSITIVE</span><span class="sxs-lookup"><span data-stu-id="044f3-110">SQL_SCROLLABLE and SQL_INSENSITIVE</span></span>|<span data-ttu-id="044f3-111">静的カーソルと読み取り専用コンカレンシー</span><span class="sxs-lookup"><span data-stu-id="044f3-111">Static cursor and read-only concurrency</span></span>|  
|<span data-ttu-id="044f3-112">SQL_SCROLLABLE と SQL_UNSPECIFIED</span><span class="sxs-lookup"><span data-stu-id="044f3-112">SQL_SCROLLABLE and SQL_UNSPECIFIED</span></span>|<span data-ttu-id="044f3-113">静的カーソルと読み取り専用コンカレンシー</span><span class="sxs-lookup"><span data-stu-id="044f3-113">Static cursor and read-only concurrency</span></span>|  
|<span data-ttu-id="044f3-114">SQL_NONSCROLLABLE と SQL_SENSITIVE</span><span class="sxs-lookup"><span data-stu-id="044f3-114">SQL_NONSCROLLABLE and SQL_SENSITIVE</span></span>|<span data-ttu-id="044f3-115">順方向専用カーソルとバージョンに基づくオプティミスティック コンカレンシー</span><span class="sxs-lookup"><span data-stu-id="044f3-115">Forward-only cursor and version-based optimistic concurrency</span></span>|  
|<span data-ttu-id="044f3-116">SQL_NONSCROLLABLE と SQL_INSENSITIVE</span><span class="sxs-lookup"><span data-stu-id="044f3-116">SQL_NONSCROLLABLE and SQL_INSENSITIVE</span></span>|<span data-ttu-id="044f3-117">既定の結果セット (順方向専用、読み取り専用)</span><span class="sxs-lookup"><span data-stu-id="044f3-117">Default result set (forward-only, read-only)</span></span>|  
|<span data-ttu-id="044f3-118">SQL_NONSCROLLABLE と SQL_UNSPECIFIED</span><span class="sxs-lookup"><span data-stu-id="044f3-118">SQL_NONSCROLLABLE and SQL_UNSPECIFIED</span></span>|<span data-ttu-id="044f3-119">既定の結果セット (順方向専用、読み取り専用)</span><span class="sxs-lookup"><span data-stu-id="044f3-119">Default result set (forward-only, read-only)</span></span>|  
  
 <span data-ttu-id="044f3-120">バージョンベースのオプティミスティック同時実行制御には、基になるテーブルに**timestamp**列が必要です。</span><span class="sxs-lookup"><span data-stu-id="044f3-120">Version-based optimistic concurrency requires a **timestamp** column in the underlying table.</span></span> <span data-ttu-id="044f3-121">**Timestamp**列のないテーブルに対してバージョンベースのオプティミスティック同時実行制御が要求された場合、サーバーは値に基づくオプティミスティック同時実行制御を使用します。</span><span class="sxs-lookup"><span data-stu-id="044f3-121">If version-based optimistic concurrency control is requested on a table that does not have a **timestamp** column, the server uses values-based optimistic concurrency.</span></span>  
  
## <a name="scrollability"></a><span data-ttu-id="044f3-122">スクロール可能</span><span class="sxs-lookup"><span data-stu-id="044f3-122">Scrollability</span></span>  
 <span data-ttu-id="044f3-123">SQL_ATTR_CURSOR_SCROLLABLE が SQL_SCROLLABLE に設定されている場合、カーソルは[Sqlfetchscroll](../native-client-odbc-api/sqlfetchscroll.md)の*fetchorientation*パラメーターのさまざまな値をすべてサポートします。</span><span class="sxs-lookup"><span data-stu-id="044f3-123">When SQL_ATTR_CURSOR_SCROLLABLE is set to SQL_SCROLLABLE, the cursor supports all the different values for the *FetchOrientation* parameter of [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md).</span></span> <span data-ttu-id="044f3-124">SQL_ATTR_CURSOR_SCROLLABLE が SQL_NONSCROLLABLE に設定されている場合、カーソルは SQL_FETCH_NEXT の*Fetchorientation*値のみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="044f3-124">When SQL_ATTR_CURSOR_SCROLLABLE is set to SQL_NONSCROLLABLE, the cursor only supports a *FetchOrientation* value of SQL_FETCH_NEXT.</span></span>  
  
## <a name="sensitivity"></a><span data-ttu-id="044f3-125">感度</span><span class="sxs-lookup"><span data-stu-id="044f3-125">Sensitivity</span></span>  
 <span data-ttu-id="044f3-126">SQL_ATTR_CURSOR_SENSITIVITY が SQL_SENSITIVE に設定されているとき、現在のユーザーが行ったデータ変更または他のユーザーがコミットしたデータ変更がカーソルに反映されます。</span><span class="sxs-lookup"><span data-stu-id="044f3-126">When SQL_ATTR_CURSOR_SENSITIVITY is set to SQL_SENSITIVE, the cursor reflects data modifications made by the current user or committed by other users.</span></span> <span data-ttu-id="044f3-127">SQL_ATTR_CURSOR_SENSITIVITY が SQL_INSENSITIVE に設定されているときは、データ変更がカーソルに反映されません。</span><span class="sxs-lookup"><span data-stu-id="044f3-127">When SQL_ATTR_CURSOR_SENSITIVITY is set to SQL_INSENSITIVE, the cursor does not reflect data modifications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="044f3-128">参照</span><span class="sxs-lookup"><span data-stu-id="044f3-128">See Also</span></span>  
 [<span data-ttu-id="044f3-129">ODBC&#41;&#40;カーソルの使用</span><span class="sxs-lookup"><span data-stu-id="044f3-129">Using Cursors &#40;ODBC&#41;</span></span>](using-cursors-odbc.md)  
  
  
