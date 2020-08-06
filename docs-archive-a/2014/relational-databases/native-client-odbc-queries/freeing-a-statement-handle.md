---
title: ステートメントハンドルを解放する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- reusing statement handles
- freeing statement handles
- statements [ODBC], statement handles
- SQLFreeStmt function
- ODBC applications, statements
- statement handles [ODBC]
ms.assetid: 96fdff84-0ca7-460a-a240-94ee826ea41c
author: rothja
ms.author: jroth
ms.openlocfilehash: 8d7a1e93d222e2b87058bc878f7eca85313b4108
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631858"
---
# <a name="freeing-a-statement-handle"></a><span data-ttu-id="543a3-102">ステートメント ハンドルの解放</span><span class="sxs-lookup"><span data-stu-id="543a3-102">Freeing a Statement Handle</span></span>
  <span data-ttu-id="543a3-103">ステートメント ハンドルは、削除して新しいハンドルを割り当てるよりも、再利用する方が効率的です。</span><span class="sxs-lookup"><span data-stu-id="543a3-103">It is more efficient to reuse statement handles than to drop them and allocate new ones.</span></span> <span data-ttu-id="543a3-104">アプリケーションでは、任意のステートメント ハンドルで新しい SQL ステートメントを実行する前に、現在のステートメント設定が適切であることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="543a3-104">Before executing a new SQL statement on a statement handle, applications should verify that the current statement settings are appropriate.</span></span> <span data-ttu-id="543a3-105">確認する設定には、ステートメント属性、パラメーター バインド、結果セットのバインドがあります。</span><span class="sxs-lookup"><span data-stu-id="543a3-105">These include statement attributes, parameter bindings, and result set bindings.</span></span> <span data-ttu-id="543a3-106">通常、古い SQL ステートメントのパラメーターと結果セットは、SQL_RESET_PARAMS と SQL_UNBIND のオプションで[SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md)を呼び出し、新しい sql ステートメントに対して再バインドすることによって、バインドを解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="543a3-106">Generally, parameters and result sets for the old SQL statement must be unbound by calling [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) with the SQL_RESET_PARAMS and SQL_UNBIND options and then re-bound for the new SQL statement.</span></span>  
  
 <span data-ttu-id="543a3-107">ステートメントを使用してアプリケーションが終了すると、 [Sqlfreehandle](../native-client-odbc-api/sqlfreehandle.md)を呼び出してステートメントを解放します。</span><span class="sxs-lookup"><span data-stu-id="543a3-107">When the application has finished using the statement, it calls [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) to free the statement.</span></span> <span data-ttu-id="543a3-108">**Sqldisconnect**は、接続上のすべてのステートメントを自動的に解放することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="543a3-108">Note that **SQLDisconnect** automatically frees all statements on a connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="543a3-109">参照</span><span class="sxs-lookup"><span data-stu-id="543a3-109">See Also</span></span>  
 [<span data-ttu-id="543a3-110">ODBC&#41;&#40;クエリの実行</span><span class="sxs-lookup"><span data-stu-id="543a3-110">Executing Queries &#40;ODBC&#41;</span></span>](executing-queries-odbc.md)  
  
  
