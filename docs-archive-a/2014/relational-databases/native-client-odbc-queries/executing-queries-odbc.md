---
title: クエリの実行 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, executing queries
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
- SQL Server Native Client ODBC driver, queries
- queries [ODBC]
ms.assetid: d935bcba-8ce6-4159-8395-6c86431602ad
author: rothja
ms.author: jroth
ms.openlocfilehash: adc51186803148056401f58f1207d3e9a7abf9c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631873"
---
# <a name="executing-queries-odbc"></a><span data-ttu-id="01e25-102">クエリの実行 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="01e25-102">Executing Queries (ODBC)</span></span>
  <span data-ttu-id="01e25-103">ODBC アプリケーションでは、接続ハンドルを初期化してデータ ソースに接続した後、その接続ハンドルに 1 つ以上のステートメント ハンドルを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="01e25-103">After an ODBC application initializes a connection handle and connects with a data source, it allocates one or more statement handles on the connection handle.</span></span> <span data-ttu-id="01e25-104">その後、アプリケーションは [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ステートメントハンドルに対してステートメントを実行できます。</span><span class="sxs-lookup"><span data-stu-id="01e25-104">The application can then execute [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] statements on the statement handle.</span></span> <span data-ttu-id="01e25-105">次に、SQL ステートメントを実行するときの一般的な手順を示します。</span><span class="sxs-lookup"><span data-stu-id="01e25-105">The general sequence of events in executing an SQL statement is:</span></span>  
  
1.  <span data-ttu-id="01e25-106">必要なステートメント属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="01e25-106">Set any required statement attributes.</span></span>  
  
2.  <span data-ttu-id="01e25-107">ステートメントを構築します。</span><span class="sxs-lookup"><span data-stu-id="01e25-107">Construct the statement.</span></span>  
  
3.  <span data-ttu-id="01e25-108">ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="01e25-108">Execute the statement.</span></span>  
  
4.  <span data-ttu-id="01e25-109">任意の結果セットを取得します。</span><span class="sxs-lookup"><span data-stu-id="01e25-109">Retrieve any result sets.</span></span>  
  
 <span data-ttu-id="01e25-110">アプリケーションは、SQL ステートメントから返されたすべての結果セット内にあるすべての行を取得した後、同一ステートメント ハンドルで別のクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="01e25-110">After an application retrieves all the rows in all of the result sets returned by the SQL statement, it can execute another query on the same statement handle.</span></span> <span data-ttu-id="01e25-111">アプリケーションで、特定の結果セット内のすべての行を取得する必要がないと判断した場合は、 [Sqlmoreresults](../native-client-odbc-api/sqlmoreresults.md)または[sqlcloの](../native-client-odbc-api/sqlclosecursor.md)いずれかを呼び出すことによって、結果セットの残りの部分を取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="01e25-111">If an application determines that it is not required to retrieve all the rows in a particular result set, it can cancel the rest of the result set by calling either [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) or [SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md).</span></span>  
  
 <span data-ttu-id="01e25-112">ODBC アプリケーションで、異なるデータを使用して同じ SQL ステートメントを複数回実行する必要がある場合は、SQL ステートメントの構築時に、次のように疑問符 (?) で表されるパラメーター マーカーを使用します。</span><span class="sxs-lookup"><span data-stu-id="01e25-112">If, in an ODBC application, you must execute the same SQL statement multiple times with different data, use a parameter marker denoted by a question mark (?) in the construction of an SQL statement:</span></span>  
  
```  
INSERT INTO MyTable VALUES (?, ?, ?)  
```  
  
 <span data-ttu-id="01e25-113">その後、 [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md)を呼び出すことによって、各パラメーターマーカーをプログラム変数にバインドできます。</span><span class="sxs-lookup"><span data-stu-id="01e25-113">Each parameter marker can then be bound to a program variable by calling [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md).</span></span>  
  
 <span data-ttu-id="01e25-114">アプリケーションは、すべての SQL ステートメントの実行と結果セットの処理を完了後、ステートメント ハンドルを解放します。</span><span class="sxs-lookup"><span data-stu-id="01e25-114">After all SQL statements execute and their result sets process, the application frees the statement handle.</span></span>  
  
 <span data-ttu-id="01e25-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーでは、接続ハンドルごとに複数のステートメントハンドルがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="01e25-115">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports multiple statement handles per connection handle.</span></span> <span data-ttu-id="01e25-116">また、トランザクションは接続レベルで管理されます。これにより、1 つの接続ハンドルのすべてのステートメント ハンドルで実行されるすべての作業が、同一のトランザクションの一部として管理されます。</span><span class="sxs-lookup"><span data-stu-id="01e25-116">Transactions are managed at the connection level, so that all work performed on all statement handles on a single connection handle are managed as part of the same transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="01e25-117">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="01e25-117">In This Section</span></span>  
  
-   [<span data-ttu-id="01e25-118">ステートメント ハンドルの割り当て</span><span class="sxs-lookup"><span data-stu-id="01e25-118">Allocating a Statement Handle</span></span>](allocating-a-statement-handle.md)  
  
-   [<span data-ttu-id="01e25-119">ODBC&#41;&#40;SQL ステートメントの構築</span><span class="sxs-lookup"><span data-stu-id="01e25-119">Constructing an SQL Statement &#40;ODBC&#41;</span></span>](constructing-an-sql-statement-odbc.md)  
  
-   [<span data-ttu-id="01e25-120">カーソル用の SQL ステートメントの作成</span><span class="sxs-lookup"><span data-stu-id="01e25-120">Constructing SQL Statements for Cursors</span></span>](constructing-sql-statements-for-cursors.md)  
  
-   [<span data-ttu-id="01e25-121">ステートメント パラメーターの使用</span><span class="sxs-lookup"><span data-stu-id="01e25-121">Using Statement Parameters</span></span>](using-statement-parameters.md)  
  
-   [<span data-ttu-id="01e25-122">ODBC&#41;&#40;のステートメントの実行</span><span class="sxs-lookup"><span data-stu-id="01e25-122">Executing Statements &#40;ODBC&#41;</span></span>](executing-statements/executing-statements-odbc.md)  
  
-   [<span data-ttu-id="01e25-123">ステートメント ハンドルの解放</span><span class="sxs-lookup"><span data-stu-id="01e25-123">Freeing a Statement Handle</span></span>](freeing-a-statement-handle.md)  
  
## <a name="see-also"></a><span data-ttu-id="01e25-124">参照</span><span class="sxs-lookup"><span data-stu-id="01e25-124">See Also</span></span>  
 [<span data-ttu-id="01e25-125">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="01e25-125">SQL Server Native Client &#40;ODBC&#41;</span></span>](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
