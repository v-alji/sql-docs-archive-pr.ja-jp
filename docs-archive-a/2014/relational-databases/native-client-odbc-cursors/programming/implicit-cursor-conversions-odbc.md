---
title: 暗黙のカーソル変換 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, implicit cursor conversions
- implicit cursor conversions
- cursors [ODBC], implicit cursor conversions
ms.assetid: fe29a58d-8448-4512-9ffd-b414784ba338
author: rothja
ms.author: jroth
ms.openlocfilehash: ff8350c71a853e39ff1d35a1f3fba6e8e1944934
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643303"
---
# <a name="implicit-cursor-conversions-odbc"></a><span data-ttu-id="ae1b2-102">暗黙のカーソル変換 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="ae1b2-102">Implicit Cursor Conversions (ODBC)</span></span>
  <span data-ttu-id="ae1b2-103">アプリケーションでは、 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)を使用してカーソルの種類を要求した後、要求された種類のサーバーカーソルでサポートされていない SQL ステートメントを実行できます。</span><span class="sxs-lookup"><span data-stu-id="ae1b2-103">Applications can request a cursor type through [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) and then execute an SQL statement that is not supported by server cursors of the type requested.</span></span> <span data-ttu-id="ae1b2-104">**Sqlexecute**または**SQLExecDirect**を呼び出すと SQL_SUCCESS_WITH_INFO が返され、 **SQLGetDiagRec**はを返します。</span><span class="sxs-lookup"><span data-stu-id="ae1b2-104">A call to **SQLExecute** or **SQLExecDirect** returns SQL_SUCCESS_WITH_INFO and **SQLGetDiagRec** returns:</span></span>  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 <span data-ttu-id="ae1b2-105">アプリケーションでは、SQL_CURSOR_TYPE に設定された**SQLGetStmtOption**を呼び出すことによって現在使用されているカーソルの種類を特定できます。</span><span class="sxs-lookup"><span data-stu-id="ae1b2-105">The application can determine what type of cursor is now being used by calling **SQLGetStmtOption** set to SQL_CURSOR_TYPE.</span></span> <span data-ttu-id="ae1b2-106">カーソルの種類の変換は、1 つのステートメントにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="ae1b2-106">The cursor type conversion applies to only one statement.</span></span> <span data-ttu-id="ae1b2-107">次の**SQLExecDirect**または**sqlexecute**は、元のステートメントのカーソル設定を使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="ae1b2-107">The next **SQLExecDirect** or **SQLExecute** will be done using the original statement cursor settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae1b2-108">参照</span><span class="sxs-lookup"><span data-stu-id="ae1b2-108">See Also</span></span>  
 [<span data-ttu-id="ae1b2-109">ODBC&#41;&#40;のカーソルプログラミングの詳細</span><span class="sxs-lookup"><span data-stu-id="ae1b2-109">Cursor Programming Details &#40;ODBC&#41;</span></span>](cursor-programming-details-odbc.md)  
  
  
