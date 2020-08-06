---
title: エラーとメッセージの処理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, about error handling
- errors [ODBC]
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], about messages
- ODBC error handling
- SQL_INVALID_HANDLE return code
- errors [ODBC], about error handling
- messages [ODBC]
ms.assetid: 74ea9630-e482-4a46-bb45-f5234f079b48
author: rothja
ms.author: jroth
ms.openlocfilehash: 4701b3224b87e7d19f1121f193d4be20f9d4c441
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714345"
---
# <a name="handling-errors-and-messages"></a><span data-ttu-id="c99bf-102">エラーとメッセージの処理</span><span class="sxs-lookup"><span data-stu-id="c99bf-102">Handling Errors and Messages</span></span>
  <span data-ttu-id="c99bf-103">アプリケーションで ODBC 関数を呼び出すときは、ドライバーが関数を実行して診断情報を 2 とおりの方法で返します。つまり、リターン コードで ODBC 関数が成功したか失敗したかを示し、診断レコードで関数の詳細な情報を伝えます。</span><span class="sxs-lookup"><span data-stu-id="c99bf-103">When an application calls an ODBC function, the driver executes the function and returns diagnostic information in two ways: A return code indicates the overall success or failure of an ODBC function, and diagnostic records provide detailed information about the function.</span></span> <span data-ttu-id="c99bf-104">診断レコードは、ヘッダー レコードと状態レコードから構成されます。</span><span class="sxs-lookup"><span data-stu-id="c99bf-104">Diagnostic records include a header record and status records.</span></span> <span data-ttu-id="c99bf-105">関数が成功した場合でも、少なくとも 1 つの診断レコード、つまりヘッダー レコードが返されます。</span><span class="sxs-lookup"><span data-stu-id="c99bf-105">At least one diagnostic record, the header record, is returned even if the function succeeds.</span></span>  
  
 <span data-ttu-id="c99bf-106">診断情報を開発時に使用すると、ハードコードした SQL ステートメントに存在する、無効なハンドルや構文エラーなどのプログラミング エラーを把握できます。</span><span class="sxs-lookup"><span data-stu-id="c99bf-106">Diagnostic information is used at development time to catch programming errors, such as invalid handles and syntax errors in hard-coded SQL statements.</span></span> <span data-ttu-id="c99bf-107">実行時に使用すると、ユーザーが入力した SQL ステートメントのデータの切り捨て、規則違反、構文エラーなどの実行時エラーや警告を確認できます。</span><span class="sxs-lookup"><span data-stu-id="c99bf-107">It is also used at run time to catch run-time errors and warnings, such as data truncation, rule violations, and syntax errors in SQL statements entered by the user.</span></span> <span data-ttu-id="c99bf-108">一般的に、プログラミング ロジックはリターン コードを基に組み立てます。</span><span class="sxs-lookup"><span data-stu-id="c99bf-108">Program logic is generally based on return codes.</span></span>  
  
 <span data-ttu-id="c99bf-109">たとえば、アプリケーションが**Sqlfetch**を呼び出して結果セットの行を取得すると、結果セットの末尾に到達したか (SQL_NO_DATA)、情報メッセージが返されたか (SQL_SUCCESS_WITH_INFO)、エラーが発生したか (SQL_ERROR) が返されます。</span><span class="sxs-lookup"><span data-stu-id="c99bf-109">For example, after an application calls **SQLFetch** to retrieve the rows in a result set, the return code indicates whether the end of the result set was reached (SQL_NO_DATA), if any informational messages were returned (SQL_SUCCESS_WITH_INFO), or if an error occurred (SQL_ERROR).</span></span>  
  
 <span data-ttu-id="c99bf-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーが SQL_SUCCESS 以外のものを返した場合、アプリケーションは、情報メッセージまたはエラーメッセージを取得するために**SQLGetDiagRec**を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="c99bf-110">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver returns anything other than SQL_SUCCESS, the application can call **SQLGetDiagRec** to retrieve any informational or error messages.</span></span> <span data-ttu-id="c99bf-111">複数のメッセージがある場合は、 **SQLGetDiagRec**を使用してメッセージセットを上下にスクロールします。</span><span class="sxs-lookup"><span data-stu-id="c99bf-111">Use **SQLGetDiagRec** to scroll up and down the message set if there is more than one message.</span></span>  
  
 <span data-ttu-id="c99bf-112">リターン コード SQL_INVALID_HANDLE は常にプログラミング エラーを示します。実行時にはこのコードが返されないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="c99bf-112">The return code SQL_INVALID_HANDLE always indicates a programming error and should never be encountered at run time.</span></span> <span data-ttu-id="c99bf-113">それ以外のリターン コードは実行時の情報を含んでいます。ただし、SQL_ERROR はプログラミング エラーを示す場合もあります。</span><span class="sxs-lookup"><span data-stu-id="c99bf-113">All other return codes provide run-time information, although SQL_ERROR may indicate a programming error.</span></span>  
  
 <span data-ttu-id="c99bf-114">元の [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネイティブ API である Db-library (C) を使用すると、アプリケーションは、エラーまたはメッセージを返すコールバックエラー処理関数およびメッセージ処理関数をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="c99bf-114">The original [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native API, DB-Library for C, allows an application to install callback error-handling and message-handling functions that return errors or messages.</span></span> <span data-ttu-id="c99bf-115">PRINT、RAISERROR、DBCC、SET など、一部の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントは、結果セットではなく DB-Library メッセージ ハンドラー関数に結果を返します。</span><span class="sxs-lookup"><span data-stu-id="c99bf-115">Some [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, such as PRINT, RAISERROR, DBCC, and SET, return their results to the DB-Library message handler function instead of to a result set.</span></span> <span data-ttu-id="c99bf-116">しかし、ODBC API にはそのようなコールバック機能がありません。</span><span class="sxs-lookup"><span data-stu-id="c99bf-116">However, the ODBC API has no such callback capability.</span></span> <span data-ttu-id="c99bf-117">から返されたメッセージが Native Client ODBC ドライバーによって検出されると [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、odbc リターンコードが SQL_SUCCESS_WITH_INFO または SQL_ERROR に設定され、そのメッセージが1つ以上の診断レコードとして返されます。</span><span class="sxs-lookup"><span data-stu-id="c99bf-117">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver detects messages coming back from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it sets the ODBC return code to SQL_SUCCESS_WITH_INFO or SQL_ERROR and returns the message as one or more diagnostic records.</span></span> <span data-ttu-id="c99bf-118">そのため、ODBC アプリケーションでは、これらのリターンコードを注意深くテストし、 **SQLGetDiagRec**を呼び出してメッセージデータを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c99bf-118">Therefore, an ODBC application must carefully test for these return codes and call **SQLGetDiagRec** to retrieve message data.</span></span>  
  
 <span data-ttu-id="c99bf-119">エラーのトレースの詳細については、「[データ アクセスのトレース](https://go.microsoft.com/fwlink/?LinkId=125805)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c99bf-119">For information about tracing errors, see [Data Access Tracing](https://go.microsoft.com/fwlink/?LinkId=125805).</span></span> <span data-ttu-id="c99bf-120">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] に追加されたエラーのトレースの機能強化については、「[拡張イベント ログの診断情報へのアクセス](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c99bf-120">For information about enhancements to error tracing added in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], see [Accessing Diagnostic Information in the Extended Events Log](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c99bf-121">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c99bf-121">In This Section</span></span>  
  
-   [<span data-ttu-id="c99bf-122">メッセージを生成するステートメントの処理</span><span class="sxs-lookup"><span data-stu-id="c99bf-122">Processing Statements That Generate Messages</span></span>](processing-statements-that-generate-messages.md)  
  
-   [<span data-ttu-id="c99bf-123">診断レコードと診断フィールド</span><span class="sxs-lookup"><span data-stu-id="c99bf-123">Diagnostic Records and Fields</span></span>](diagnostic-records-and-fields.md)  
  
-   [<span data-ttu-id="c99bf-124">ネイティブ エラー番号</span><span class="sxs-lookup"><span data-stu-id="c99bf-124">Native Error Numbers</span></span>](native-error-numbers.md)  
  
-   [<span data-ttu-id="c99bf-125">SQLSTATE &#40;ODBC エラーコード&#41;</span><span class="sxs-lookup"><span data-stu-id="c99bf-125">SQLSTATE &#40;ODBC Error Codes&#41;</span></span>](sqlstate-odbc-error-codes.md)  
  
-   [<span data-ttu-id="c99bf-126">エラー メッセージ</span><span class="sxs-lookup"><span data-stu-id="c99bf-126">Error Messages</span></span>](error-messages.md)  
  
## <a name="see-also"></a><span data-ttu-id="c99bf-127">参照</span><span class="sxs-lookup"><span data-stu-id="c99bf-127">See Also</span></span>  
 [<span data-ttu-id="c99bf-128">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="c99bf-128">SQL Server Native Client &#40;ODBC&#41;</span></span>](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
