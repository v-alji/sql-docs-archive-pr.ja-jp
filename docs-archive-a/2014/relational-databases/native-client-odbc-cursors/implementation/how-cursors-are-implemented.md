---
title: カーソルの実装方法Microsoft Docs
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
- cursors [ODBC], about ODBC cursors
ms.assetid: 2b1d7dd4-08a4-43fc-b3eb-70c183d0941f
author: rothja
ms.author: jroth
ms.openlocfilehash: 18995355b825d9cb1e62b4794429b5e98ef2b472
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634532"
---
# <a name="how-cursors-are-implemented"></a><span data-ttu-id="907e8-102">カーソルの実装方法</span><span class="sxs-lookup"><span data-stu-id="907e8-102">How Cursors Are Implemented</span></span>
  <span data-ttu-id="907e8-103">ODBC アプリケーションでは SQL ステートメントを実行する前に、1 つ以上のステートメント属性を設定することにより、カーソルの動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="907e8-103">ODBC applications control the behavior of a cursor by setting one or more statement attributes before executing an SQL statement.</span></span> <span data-ttu-id="907e8-104">ODBC には、カーソルの特性を指定する方法として、次の 2 つが用意されています。</span><span class="sxs-lookup"><span data-stu-id="907e8-104">ODBC has two different ways to specify the characteristics of a cursor:</span></span>  
  
-   <span data-ttu-id="907e8-105">カーソルの種類</span><span class="sxs-lookup"><span data-stu-id="907e8-105">Cursor type</span></span>  
  
     <span data-ttu-id="907e8-106">カーソルの種類は、 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)の SQL_ATTR_CURSOR_TYPE 属性を使用して設定します。</span><span class="sxs-lookup"><span data-stu-id="907e8-106">Cursor types are set using the SQL_ATTR_CURSOR_TYPE attribute of [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).</span></span> <span data-ttu-id="907e8-107">ODBC カーソルの種類には、順方向専用、静的、キーセット ドリブン、混合、および動的があります。</span><span class="sxs-lookup"><span data-stu-id="907e8-107">The ODBC cursor types are forward-only, static, keyset-driven, mixed, and dynamic.</span></span> <span data-ttu-id="907e8-108">カーソルの種類を設定することは、カーソルを指定するための ODBC 独自の方法でした。</span><span class="sxs-lookup"><span data-stu-id="907e8-108">Setting the cursor type was the original method of specifying cursors in ODBC.</span></span>  
  
-   <span data-ttu-id="907e8-109">カーソルの動作</span><span class="sxs-lookup"><span data-stu-id="907e8-109">Cursor behavior</span></span>  
  
     <span data-ttu-id="907e8-110">カーソルの動作は、 **SQLSetStmtAttr**の SQL_ATTR_CURSOR_SCROLLABLE と SQL_ATTR_CURSOR_SENSITIVITY 属性を使用して設定されます。</span><span class="sxs-lookup"><span data-stu-id="907e8-110">Cursor behavior is set using the SQL_ATTR_CURSOR_SCROLLABLE and SQL_ATTR_CURSOR_SENSITIVITY attributes of **SQLSetStmtAttr**.</span></span> <span data-ttu-id="907e8-111">これらの属性は、ISO 標準で DECLARE CURSOR ステートメント用に定義されている SCROLL キーワードと SENSITIVE キーワードをモデルにしたものです。</span><span class="sxs-lookup"><span data-stu-id="907e8-111">These attributes are modeled on the SCROLL and SENSITIVE keywords defined for the DECLARE CURSOR statement in ISO standards.</span></span> <span data-ttu-id="907e8-112">これら 2 つの ISO オプションは、ODBC Version 3.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="907e8-112">These two ISO options were introduced in ODBC version 3.0.</span></span>  
  
 <span data-ttu-id="907e8-113">ODBC カーソルの特性は、これら 2 つの方法のいずれかを使用して指定する必要がありますが、ODBC カーソルの種類を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="907e8-113">The characteristics of an ODBC cursor should be specified using either one or the other of these two methods, with the preference being to use the ODBC cursor types.</span></span>  
  
 <span data-ttu-id="907e8-114">ODBC アプリケーションではカーソルの種類を設定すること以外に、1 回のフェッチで返される行数、コンカレンシー オプション、トランザクション分離レベルなど、他のオプションも設定します。</span><span class="sxs-lookup"><span data-stu-id="907e8-114">In addition to setting the type of a cursor, ODBC applications also set other options, such as the number of rows returned on each fetch, concurrency options, and transaction isolation levels.</span></span> <span data-ttu-id="907e8-115">これらのオプションは、ODBC 形式のカーソル (順方向専用、静的、キーセット ドリブン、混合、および動的) または ISO 形式のカーソル (スクロール機能と感度) に対して設定できます。</span><span class="sxs-lookup"><span data-stu-id="907e8-115">These options can be set for either ODBC-style cursors (forward-only, static, keyset-driven, mixed, and dynamic) or ISO style cursors (scrollability and sensitivity).</span></span>  
  
 <span data-ttu-id="907e8-116">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーでは、さまざまな種類のカーソルを物理的に実装するいくつかの方法がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="907e8-116">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports several ways to physically implement the various types of cursors.</span></span> <span data-ttu-id="907e8-117">このドライバーでは、いくつかの種類のカーソルは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定の結果セットを使用して実装されます。また ODBC カーソル ライブラリを使用してサーバー カーソルとして実装される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="907e8-117">The driver implements some types of cursors using a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] default result set; it implements others as server cursors or by using the ODBC Cursor Library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="907e8-118">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="907e8-118">In This Section</span></span>  
  
-   [<span data-ttu-id="907e8-119">SQL Server の既定の結果セットの使用</span><span class="sxs-lookup"><span data-stu-id="907e8-119">Using SQL Server Default Result Sets</span></span>](using-sql-server-default-result-sets.md)  
  
-   [<span data-ttu-id="907e8-120">サーバー カーソルの使用</span><span class="sxs-lookup"><span data-stu-id="907e8-120">Using Server Cursors</span></span>](using-server-cursors.md)  
  
-   [<span data-ttu-id="907e8-121">ODBC カーソルライブラリ</span><span class="sxs-lookup"><span data-stu-id="907e8-121">ODBC Cursor Library</span></span>](odbc-cursor-library.md)  
  
## <a name="see-also"></a><span data-ttu-id="907e8-122">参照</span><span class="sxs-lookup"><span data-stu-id="907e8-122">See Also</span></span>  
 [<span data-ttu-id="907e8-123">ODBC&#41;&#40;カーソルの使用</span><span class="sxs-lookup"><span data-stu-id="907e8-123">Using Cursors &#40;ODBC&#41;</span></span>](../using-cursors-odbc.md)  
  
  
