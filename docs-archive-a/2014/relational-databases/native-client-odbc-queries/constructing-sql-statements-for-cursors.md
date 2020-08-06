---
title: カーソルの SQL ステートメントの構築 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], statement construction
- ODBC applications, cursors
- SQL Server Native Client ODBC driver, statements
- statements [ODBC], constructing
- ODBC applications, statements
- statements [ODBC], cursors
ms.assetid: 134003fd-9c93-4f5c-a988-045990933b80
author: rothja
ms.author: jroth
ms.openlocfilehash: b0fe0831b97c13c5d20067386f4e9d8c97ee19ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631875"
---
# <a name="constructing-sql-statements-for-cursors"></a><span data-ttu-id="28ddd-102">カーソル用の SQL ステートメントの作成</span><span class="sxs-lookup"><span data-stu-id="28ddd-102">Constructing SQL Statements for Cursors</span></span>
  <span data-ttu-id="28ddd-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT odbc ドライバーでは、odbc 仕様で定義されているカーソル機能を実装するために、サーバーカーソルを使用します。</span><span class="sxs-lookup"><span data-stu-id="28ddd-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver uses server cursors to implement the cursor functionality defined in the ODBC specification.</span></span> <span data-ttu-id="28ddd-104">ODBC アプリケーションでは、 [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)を使用して異なるステートメント属性を設定することによって、カーソル動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="28ddd-104">An ODBC application controls the cursor behavior by using [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) to set different statement attributes.</span></span> <span data-ttu-id="28ddd-105">次に、属性とその既定値を示します。</span><span class="sxs-lookup"><span data-stu-id="28ddd-105">These are the attributes and their defaults.</span></span>  
  
|<span data-ttu-id="28ddd-106">属性</span><span class="sxs-lookup"><span data-stu-id="28ddd-106">Attribute</span></span>|<span data-ttu-id="28ddd-107">Default</span><span class="sxs-lookup"><span data-stu-id="28ddd-107">Default</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="28ddd-108">SQL_ATTR_CONCURRENCY</span><span class="sxs-lookup"><span data-stu-id="28ddd-108">SQL_ATTR_CONCURRENCY</span></span>|<span data-ttu-id="28ddd-109">SQL_CONCUR_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="28ddd-109">SQL_CONCUR_READ_ONLY</span></span>|  
|<span data-ttu-id="28ddd-110">SQL_ATTR_CURSOR_TYPE</span><span class="sxs-lookup"><span data-stu-id="28ddd-110">SQL_ATTR_CURSOR_TYPE</span></span>|<span data-ttu-id="28ddd-111">SQL_CURSOR_FORWARD_ONLY</span><span class="sxs-lookup"><span data-stu-id="28ddd-111">SQL_CURSOR_FORWARD_ONLY</span></span>|  
|<span data-ttu-id="28ddd-112">SQL_ATTR_CURSOR_SCROLLABLE</span><span class="sxs-lookup"><span data-stu-id="28ddd-112">SQL_ATTR_CURSOR_SCROLLABLE</span></span>|<span data-ttu-id="28ddd-113">SQL_NONSCROLLABLE</span><span class="sxs-lookup"><span data-stu-id="28ddd-113">SQL_NONSCROLLABLE</span></span>|  
|<span data-ttu-id="28ddd-114">SQL_ATTR_CURSOR_SENSITIVITY</span><span class="sxs-lookup"><span data-stu-id="28ddd-114">SQL_ATTR_CURSOR_SENSITIVITY</span></span>|<span data-ttu-id="28ddd-115">SQL_UNSPECIFIED</span><span class="sxs-lookup"><span data-stu-id="28ddd-115">SQL_UNSPECIFIED</span></span>|  
|<span data-ttu-id="28ddd-116">SQL_ATTR_ROW_ARRAY_SIZE</span><span class="sxs-lookup"><span data-stu-id="28ddd-116">SQL_ATTR_ROW_ARRAY_SIZE</span></span>|<span data-ttu-id="28ddd-117">1</span><span class="sxs-lookup"><span data-stu-id="28ddd-117">1</span></span>|  
  
 <span data-ttu-id="28ddd-118">SQL ステートメントの実行時にこれらのオプションが既定値に設定されている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーは、サーバーカーソルを使用して結果セットを実装するのではなく、既定の結果セットを使用します。</span><span class="sxs-lookup"><span data-stu-id="28ddd-118">When these options are set to their defaults at the time an SQL statement is executed, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not use a server cursor to implement the result set; instead, it uses a default result set.</span></span> <span data-ttu-id="28ddd-119">SQL ステートメントの実行時に、これらのオプションのいずれかが既定値から変更された場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーは、サーバーカーソルを使用して結果セットを実装しようとします。</span><span class="sxs-lookup"><span data-stu-id="28ddd-119">If any of these options are changed from their defaults at the time an SQL statement is executed, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver attempts to use a server cursor to implement the result set.</span></span>  
  
 <span data-ttu-id="28ddd-120">既定の結果セットは、すべての [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントをサポートします。</span><span class="sxs-lookup"><span data-stu-id="28ddd-120">Default result sets support all of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="28ddd-121">既定の結果セットを使用するときに実行できる SQL ステートメントの種類に制限はありません。</span><span class="sxs-lookup"><span data-stu-id="28ddd-121">There are no restrictions on the types of SQL statements that can be executed when using a default result set.</span></span>  
  
 <span data-ttu-id="28ddd-122">サーバー カーソルはすべての [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントをサポートしているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="28ddd-122">Server cursors do not support all [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="28ddd-123">複数の結果セットを生成する SQL ステートメントはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="28ddd-123">Server cursors do not support any SQL statement that generates multiple result sets.</span></span>  
  
 <span data-ttu-id="28ddd-124">次に示す種類のステートメントは、サーバー カーソルではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="28ddd-124">The following types of statements are not supported by server cursors:</span></span>  
  
-   <span data-ttu-id="28ddd-125">バッチ</span><span class="sxs-lookup"><span data-stu-id="28ddd-125">Batches</span></span>  
  
     <span data-ttu-id="28ddd-126">2 つ以上の個別の SQL SELECT ステートメントから構成される SQL ステートメント。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="28ddd-126">SQL statements built from two or more individual SQL SELECT statements, for example:</span></span>  
  
    ```  
    SELECT * FROM Authors; SELECT * FROM Titles  
    ```  
  
-   <span data-ttu-id="28ddd-127">複数の SELECT ステートメントを含むストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="28ddd-127">Stored procedures with multiple SELECT statements</span></span>  
  
     <span data-ttu-id="28ddd-128">複数の SELECT ステートメントを含むストアド プロシージャを実行する SQL ステートメント。</span><span class="sxs-lookup"><span data-stu-id="28ddd-128">SQL statements that execute a stored procedure containing more than one SELECT statement.</span></span> <span data-ttu-id="28ddd-129">パラメーターまたは変数を設定する SELECT ステートメントも該当します。</span><span class="sxs-lookup"><span data-stu-id="28ddd-129">This includes SELECT statements that fill parameters or variables.</span></span>  
  
-   <span data-ttu-id="28ddd-130">キーワード</span><span class="sxs-lookup"><span data-stu-id="28ddd-130">Keywords</span></span>  
  
     <span data-ttu-id="28ddd-131">キーワード FOR BROWSE または INTO を伴う SELECT ステートメント。</span><span class="sxs-lookup"><span data-stu-id="28ddd-131">SQL statements containing the keywords FOR BROWSE, or INTO.</span></span>  
  
 <span data-ttu-id="28ddd-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で、上記の条件のいずれかに該当する SQL ステートメントをサーバー カーソルを使用して実行した場合、サーバー カーソルは暗黙的に既定の結果セットに変換されます。</span><span class="sxs-lookup"><span data-stu-id="28ddd-132">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], if an SQL statement that matches any of these conditions is executed with a server cursor, the server cursor is implicitly converted to a default result set.</span></span> <span data-ttu-id="28ddd-133">**SQLExecDirect**または**sqlexecute**が SQL_SUCCESS_WITH_INFO を返すと、カーソル属性が既定の設定に戻ります。</span><span class="sxs-lookup"><span data-stu-id="28ddd-133">After **SQLExecDirect** or **SQLExecute** returns SQL_SUCCESS_WITH_INFO, the cursor attributes will be set back to their default settings.</span></span>  
  
 <span data-ttu-id="28ddd-134">上記の分類に該当しない SQL ステートメントは、ステートメント属性の設定がどのようであっても実行できます。既定の結果セット、サーバー カーソルを問わず、どちらも正常に機能します。</span><span class="sxs-lookup"><span data-stu-id="28ddd-134">SQL statements that do not fit the categories above can be executed with any statement attribute settings; they work equally well with either a default result set or a server cursor.</span></span>  
  
## <a name="errors"></a><span data-ttu-id="28ddd-135">エラー</span><span class="sxs-lookup"><span data-stu-id="28ddd-135">Errors</span></span>  
 <span data-ttu-id="28ddd-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 以降のバージョンで複数の結果セットが生成されるステートメントを実行すると、SQL_SUCCESS_WITH INFO および次のメッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="28ddd-136">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 and later, an attempt to execute a statement that produces multiple result sets generates SQL_SUCCESS_WITH INFO and the following message:</span></span>  
  
```  
SqlState: 01S02"  
pfNative: 0  
szErrorMsgString: "[Microsoft][SQL Server Native Client][SQL Server]  
               Cursor type changed."  
```  
  
 <span data-ttu-id="28ddd-137">このメッセージを受信する ODBC アプリケーションは、 [SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md)を呼び出して、現在のカーソル設定を確認できます。</span><span class="sxs-lookup"><span data-stu-id="28ddd-137">ODBC applications receiving this message can call [SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md) to determine the current cursor settings.</span></span>  
  
 <span data-ttu-id="28ddd-138">サーバー カーソルを使用しているときに、複数の SELECT ステートメントから構成されるプロシージャを実行すると、次のエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="28ddd-138">An attempt to execute a procedure with multiple SELECT statements when using server cursors generates the following error:</span></span>  
  
```  
SqlState: 42000  
pfNative: 16937  
szErrorMsgString: [Microsoft][SQL Server Native Client][SQL Server]  
               A server cursor is not allowed on a stored procedure  
               with more than one SELECT statement in it. Use a  
               default result set or client cursor.  
```  
  
 <span data-ttu-id="28ddd-139">サーバー カーソルを使用しているときに、複数の SELECT ステートメントから構成されるバッチを実行すると、次のエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="28ddd-139">An attempt to execute a batch with multiple SELECT statements when using server cursors generates the following error:</span></span>  
  
```  
SqlState: 42000  
pfNative: 16938  
szErrorMsgString: [Microsoft][SQL Server Native Client][SQL Server]  
               sp_cursoropen. The statement parameter can only  
               be a single SELECT statement or a single stored   
               procedure.  
```  
  
 <span data-ttu-id="28ddd-140">ODBC アプリケーションで上記のエラーが発生した場合、カーソルのすべてのステートメント属性を既定値に戻してからステートメントを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="28ddd-140">ODBC applications receiving these errors must reset all the cursor statement attributes to their defaults before attempting to execute the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28ddd-141">参照</span><span class="sxs-lookup"><span data-stu-id="28ddd-141">See Also</span></span>  
 [<span data-ttu-id="28ddd-142">ODBC&#41;&#40;クエリの実行</span><span class="sxs-lookup"><span data-stu-id="28ddd-142">Executing Queries &#40;ODBC&#41;</span></span>](executing-queries-odbc.md)  
  
  