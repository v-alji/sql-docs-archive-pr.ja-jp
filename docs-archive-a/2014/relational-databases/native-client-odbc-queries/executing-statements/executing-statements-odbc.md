---
title: ステートメントの実行 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
author: rothja
ms.author: jroth
ms.openlocfilehash: 3066a09cb1f5e63105ca3ffe2441f19e4bbe0101
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631867"
---
# <a name="executing-statements-odbc"></a><span data-ttu-id="1b3b3-102">ステートメントの実行 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="1b3b3-102">Executing Statements (ODBC)</span></span>
  <span data-ttu-id="1b3b3-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーには、データベース内で SQL ステートメントを実行するためのさまざまな方法が用意されてい [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="1b3b3-103">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver offers a variety ways to execute SQL statements in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database:</span></span>  
  
-   <span data-ttu-id="1b3b3-104">直接実行</span><span class="sxs-lookup"><span data-stu-id="1b3b3-104">Direct execution</span></span>  
  
-   <span data-ttu-id="1b3b3-105">準備実行</span><span class="sxs-lookup"><span data-stu-id="1b3b3-105">Prepared execution</span></span>  
  
 <span data-ttu-id="1b3b3-106">直接実行では、ステートメントを含む文字列を作成 [!INCLUDE[tsql](../../../includes/tsql-md.md)] し、 **SQLExecDirect**関数を使用して実行するために送信します。</span><span class="sxs-lookup"><span data-stu-id="1b3b3-106">Direct execution involves building a character string containing a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement and submitting it for execution using the **SQLExecDirect** function.</span></span> <span data-ttu-id="1b3b3-107">準備実行では、[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを含む文字列を作成してから、そのステートメントを 2 段階に分けて実行します。</span><span class="sxs-lookup"><span data-stu-id="1b3b3-107">Prepared execution involves building a character string containing a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement and then executing it in two stages.</span></span> <span data-ttu-id="1b3b3-108">最初の段階では、 [SQLPrepare 関数](https://go.microsoft.com/fwlink/?LinkId=59360)関数を使用して、のステートメントの実行プランを解析およびコンパイルし [!INCLUDE[ssDE](../../../includes/ssde-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="1b3b3-108">The first stage uses the [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360) function to parse and compile the execution plan for the statement in the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span> <span data-ttu-id="1b3b3-109">2番目の段階では、 **Sqlexecute**関数を使用して、事前に準備された実行プランを実行します。</span><span class="sxs-lookup"><span data-stu-id="1b3b3-109">The second stage uses the **SQLExecute** function to execute the previously prepared execution plan.</span></span> <span data-ttu-id="1b3b3-110">この方法では、各実行にかかる解析とコンパイルのオーバーヘッドが抑制されます。</span><span class="sxs-lookup"><span data-stu-id="1b3b3-110">This saves the parsing and compiling overhead on each execution.</span></span> <span data-ttu-id="1b3b3-111">準備実行は、通常、同一のパラメーター化された SQL ステートメントを繰り返し実行するアプリケーションで使用されます。</span><span class="sxs-lookup"><span data-stu-id="1b3b3-111">Prepared execution is commonly used by applications to repeatedly execute the same, parameterized SQL statement.</span></span>  
  
 <span data-ttu-id="1b3b3-112">どちらの実行方法でも、[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントまたは SQL ステートメントのバッチを 1 つ実行でき、ステートメントからストアド プロシージャを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="1b3b3-112">Both direct and prepared execution can execute a single [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement or a batch of SQL statements, or they can call a stored procedure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1b3b3-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="1b3b3-113">In This Section</span></span>  
  
-   [<span data-ttu-id="1b3b3-114">直接実行</span><span class="sxs-lookup"><span data-stu-id="1b3b3-114">Direct Execution</span></span>](direct-execution.md)  
  
-   [<span data-ttu-id="1b3b3-115">準備実行</span><span class="sxs-lookup"><span data-stu-id="1b3b3-115">Prepared Execution</span></span>](prepared-execution.md)  
  
-   [<span data-ttu-id="1b3b3-116">手順</span><span class="sxs-lookup"><span data-stu-id="1b3b3-116">Procedures</span></span>](procedures.md)  
  
-   [<span data-ttu-id="1b3b3-117">ステートメントのバッチ</span><span class="sxs-lookup"><span data-stu-id="1b3b3-117">Batches of Statements</span></span>](batches-of-statements.md)  
  
-   [<span data-ttu-id="1b3b3-118">ISO オプションの効果</span><span class="sxs-lookup"><span data-stu-id="1b3b3-118">Effects of ISO Options</span></span>](effects-of-iso-options.md)  
  
## <a name="see-also"></a><span data-ttu-id="1b3b3-119">参照</span><span class="sxs-lookup"><span data-stu-id="1b3b3-119">See Also</span></span>  
 [<span data-ttu-id="1b3b3-120">ODBC&#41;&#40;クエリの実行</span><span class="sxs-lookup"><span data-stu-id="1b3b3-120">Executing Queries &#40;ODBC&#41;</span></span>](../executing-queries-odbc.md)  
  
  
