---
title: SQLFetchScroll |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFetchScroll function
ms.assetid: 524a3985-a08d-4445-99e0-bb551a666615
author: rothja
ms.author: jroth
ms.openlocfilehash: eecf9714a97577ff490b642cee5b9c380333e40b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634535"
---
# <a name="sqlfetchscroll"></a><span data-ttu-id="e4f93-102">SQLFetchScroll</span><span class="sxs-lookup"><span data-stu-id="e4f93-102">SQLFetchScroll</span></span>
  <span data-ttu-id="e4f93-103">**Sqlfetchscroll**は、データの1つの行セットをアプリケーションに返します。</span><span class="sxs-lookup"><span data-stu-id="e4f93-103">**SQLFetchScroll** returns one row set of data to the application.</span></span> <span data-ttu-id="e4f93-104">行セットのサイズは[SQLSetStmtAttr](sqlsetstmtattr.md)を使用して設定されます。</span><span class="sxs-lookup"><span data-stu-id="e4f93-104">The size of the row set is set using [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span> <span data-ttu-id="e4f93-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーでは、定義済みのすべてのフェッチ命令 (SQL_FETCH_RELATIVE など) がサポートされていますが、次の制限があります。</span><span class="sxs-lookup"><span data-stu-id="e4f93-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports all defined fetch instructions (for example, SQL_FETCH_RELATIVE) with the following limitations:</span></span>  
  
-   <span data-ttu-id="e4f93-106">ステートメントに順方向専用カーソルを定義する場合は、SQL_FETCH_NEXT が必要です。他の形式でフェッチを試行すると、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="e4f93-106">If a forward-only cursor is defined for the statement, SQL_FETCH_NEXT is required and attempts to fetch in any other fashion will result in an error return.</span></span>  
  
-   <span data-ttu-id="e4f93-107">SQL_FETCH_BOOKMARK がサポートされるのは、静的カーソルとキーセット ドリブン カーソルに対してのみです。</span><span class="sxs-lookup"><span data-stu-id="e4f93-107">SQL_FETCH_BOOKMARK is supported for static and keyset-driven cursors only.</span></span>  
  
## <a name="sqlfetchscroll-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="e4f93-108">SQLFetchScroll による機能強化された日付と時刻のサポート</span><span class="sxs-lookup"><span data-stu-id="e4f93-108">SQLFetchScroll Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="e4f93-109">Date 型または time 型の結果列の値は、「 [SQL から C への変換](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)」で説明されているように変換されます。</span><span class="sxs-lookup"><span data-stu-id="e4f93-109">Result column values of date/time types are converted as described in [Conversions from SQL to C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).</span></span>  
  
 <span data-ttu-id="e4f93-110">詳細については、「[日付と時刻の機能強化 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4f93-110">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlfetchscroll-support-for-large-clr-udts"></a><span data-ttu-id="e4f93-111">SQLFetchScroll による大きな CLR UDT のサポート</span><span class="sxs-lookup"><span data-stu-id="e4f93-111">SQLFetchScroll Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="e4f93-112">**Sqlfetchscroll**は、大きな CLR ユーザー定義型 (udt) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="e4f93-112">**SQLFetchScroll** supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="e4f93-113">詳細については、「[大容量の CLR ユーザー定義型 &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4f93-113">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4f93-114">参照</span><span class="sxs-lookup"><span data-stu-id="e4f93-114">See Also</span></span>  
 <span data-ttu-id="e4f93-115">[SQLFetchScroll 関数](https://go.microsoft.com/fwlink/?LinkId=59343) </span><span class="sxs-lookup"><span data-stu-id="e4f93-115">[SQLFetchScroll Function](https://go.microsoft.com/fwlink/?LinkId=59343) </span></span>  
 [<span data-ttu-id="e4f93-116">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="e4f93-116">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
