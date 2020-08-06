---
title: ステートメントのバッチ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statements [ODBC], batches
- batches [ODBC]
- ODBC applications, statements
- multiple statements, batches
- SQLMoreResults function
- SQLExecDirect function
ms.assetid: 057d7c1c-1428-4780-9447-a002ea741188
author: rothja
ms.author: jroth
ms.openlocfilehash: 4818b67766dafe851035041c8fd5137a0dfade73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631872"
---
# <a name="batches-of-statements"></a><span data-ttu-id="5af11-102">ステートメントのバッチ</span><span class="sxs-lookup"><span data-stu-id="5af11-102">Batches of Statements</span></span>
  <span data-ttu-id="5af11-103">ステートメントのバッチには [!INCLUDE[tsql](../../../includes/tsql-md.md)] 、2つ以上のステートメントが含まれています。セミコロン (;) は、 **SQLExecDirect**または[SQLPrepare 関数](https://go.microsoft.com/fwlink/?LinkId=59360)に渡される1つの文字列に組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="5af11-103">A batch of [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements contains two or more statements, separated by a semicolon (;), built into a single string passed to **SQLExecDirect** or [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360).</span></span> <span data-ttu-id="5af11-104">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="5af11-104">For example:</span></span>  
  
```  
SQLExecDirect(hstmt,   
    "SELECT * FROM Authors; SELECT * FROM Titles",  
    SQL_NTS);  
```  
  
 <span data-ttu-id="5af11-105">バッチでは、通常、ネットワーク トラフィックが削減されるので、複数のステートメントを個別に送信するよりも効率的になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5af11-105">Batches can be more efficient than submitting statements separately because network traffic is often reduced.</span></span> <span data-ttu-id="5af11-106">現在の結果セットが完成したときに、次の結果セットに配置するには、 [Sqlmoreresults](../../native-client-odbc-api/sqlmoreresults.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="5af11-106">Use [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) to get positioned on the next result set when finished with the current result set.</span></span>  
  
 <span data-ttu-id="5af11-107">行セットのサイズが 1 になっている、順方向専用かつ読み取り専用のカーソルの既定値に ODBC カーソル属性が設定されている場合は、常にバッチを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5af11-107">Batches can always be used when the ODBC cursor attributes are set to the defaults of a forward-only, read-only cursor with a rowset size of 1.</span></span>  
  
 <span data-ttu-id="5af11-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に対してサーバー カーソルを使用しているときにバッチを実行すると、サーバー カーソルが暗黙的に既定の結果セットに変換されます。</span><span class="sxs-lookup"><span data-stu-id="5af11-108">If a batch is executed when using server cursors against [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the server cursor is implicitly converted to a default result set.</span></span> <span data-ttu-id="5af11-109">**SQLExecDirect**または**sqlexecute**は SQL_SUCCESS_WITH_INFO を返し、 **SQLGetDiagRec**を呼び出すと次のように返されます。</span><span class="sxs-lookup"><span data-stu-id="5af11-109">**SQLExecDirect** or **SQLExecute** return SQL_SUCCESS_WITH_INFO, and a call to **SQLGetDiagRec** returns:</span></span>  
  
```  
szSqlState = "01S02", pfNativeError = 0  
szErrorMsg = "[Microsoft][SQL Server Native Server Native Client]Cursor type changed."  
```  
  
## <a name="see-also"></a><span data-ttu-id="5af11-110">参照</span><span class="sxs-lookup"><span data-stu-id="5af11-110">See Also</span></span>  
 [<span data-ttu-id="5af11-111">ODBC&#41;&#40;のステートメントの実行</span><span class="sxs-lookup"><span data-stu-id="5af11-111">Executing Statements &#40;ODBC&#41;</span></span>](executing-statements-odbc.md)  
  
  
