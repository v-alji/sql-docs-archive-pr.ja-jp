---
title: SQL Server の既定の結果セットを使用する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- ODBC cursors, default result sets
- cursors [ODBC], default result sets
- default result sets
- result sets [ODBC], default
- ODBC applications, cursors
ms.assetid: ee1db3e5-60eb-4425-8a6b-977eeced3f98
author: rothja
ms.author: jroth
ms.openlocfilehash: 18cd10dd95329f68a42497d2bea5ce63f345ceff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634521"
---
# <a name="using-sql-server-default-result-sets"></a><span data-ttu-id="e606a-102">SQL Server の既定の結果セットの使用</span><span class="sxs-lookup"><span data-stu-id="e606a-102">Using SQL Server Default Result Sets</span></span>
  <span data-ttu-id="e606a-103">ODBC カーソルの既定の属性を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e606a-103">The default ODBC cursor attributes are:</span></span>  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_FORWARD_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_CONCURRENCY, SQL_CONCUR_READ_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 1, SQL_IS_INTEGER);  
```  
  
 <span data-ttu-id="e606a-104">これらの属性が既定値に設定されている場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーでは、既定の結果セットが使用され [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="e606a-104">Whenever these attributes are set to their defaults, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver uses a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] default result set.</span></span> <span data-ttu-id="e606a-105">既定の結果セットは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でサポートされるすべての SQL ステートメントに使用でき、結果セット全体をクライアントに転送する際の最も効率的な方法です。</span><span class="sxs-lookup"><span data-stu-id="e606a-105">Default result sets can be used for any SQL statement supported by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], and are the most efficient method of transferring an entire result set to the client.</span></span>  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]<span data-ttu-id="e606a-106">では、複数のアクティブな結果セット (MARS) のサポートが導入されました。アプリケーションは、接続ごとに複数のアクティブな既定の結果セットを持つことができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e606a-106">introduced support for multiple active result sets (MARS); applications can now have more than one active default result set per connection.</span></span> <span data-ttu-id="e606a-107">MARS は既定では有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="e606a-107">MARS is not enabled by default.</span></span>  
  
 <span data-ttu-id="e606a-108">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] より前のリリースでは、既定の結果セットは 1 つの接続における複数のアクティブなステートメントをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e606a-108">Before [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], default result sets did not support multiple active statements on the same connection.</span></span> <span data-ttu-id="e606a-109">SQL ステートメントが 1 つの接続で実行された後、サーバーは結果セットのすべての行が処理されるまで、その接続に対するクライアントからのコマンドを受け付けません (結果セットの残りの行の処理を取り消す要求は除きます)。</span><span class="sxs-lookup"><span data-stu-id="e606a-109">After an SQL statement is executed on a connection, the server does not accept commands (except a request to cancel the rest of the result set) from the client on that connection until all the rows in the result set have been processed.</span></span> <span data-ttu-id="e606a-110">部分的に処理された結果セットの残りの部分を取り消すには、 *Foption*パラメーターを SQL_CLOSE に設定して[sqlcloを](../../native-client-odbc-api/sqlclosecursor.md)呼び出すか、 [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e606a-110">To cancel the remainder of a partially processed result set, call [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) or [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) with the *fOption* parameter set to SQL_CLOSE.</span></span> <span data-ttu-id="e606a-111">部分的に処理された結果セットを完成させ、別の結果セットが存在するかどうかをテストするには、 [Sqlmoreresults](../../native-client-odbc-api/sqlmoreresults.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e606a-111">To finish a partially processed result set and test for the presence of another result set, call [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md).</span></span> <span data-ttu-id="e606a-112">既定の結果セットが完全に処理される前に ODBC アプリケーションが接続ハンドルに対してコマンドを試行した場合は SQL_ERROR が生成され、 **SQLGetDiagRec**を呼び出すとが返されます。</span><span class="sxs-lookup"><span data-stu-id="e606a-112">If an ODBC application attempts a command on a connection handle before a default result set has been completely processed, the call generates SQL_ERROR and a call to **SQLGetDiagRec** returns:</span></span>  
  
```  
szSqlState: "HY000", pfNativeError: 0  
szErrorMsg: "[Microsoft][SQL Server Native Client]  
                Connection is busy with results for another hstmt."  
```  
  
## <a name="see-also"></a><span data-ttu-id="e606a-113">参照</span><span class="sxs-lookup"><span data-stu-id="e606a-113">See Also</span></span>  
 [<span data-ttu-id="e606a-114">カーソルの実装方法</span><span class="sxs-lookup"><span data-stu-id="e606a-114">How Cursors Are Implemented</span></span>](how-cursors-are-implemented.md)  
  
  
