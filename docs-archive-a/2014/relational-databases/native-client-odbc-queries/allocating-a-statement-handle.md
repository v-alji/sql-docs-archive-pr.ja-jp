---
title: ステートメントハンドルを割り当てる |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- statements [ODBC], statement handles
- ODBC applications, executing queries
- SQLGetStmtAttr function
- SQL Server Native Client ODBC driver, statements
- allocating statement handles
- ODBC applications, statements
- statement handles [ODBC]
- SQLAllocHandle function
ms.assetid: 9ee207f3-2667-45f5-87ca-e6efa1fd7a5c
author: rothja
ms.author: jroth
ms.openlocfilehash: fac0802b474f38f6a6c314dd727fa335d14598d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741985"
---
# <a name="allocating-a-statement-handle"></a><span data-ttu-id="3bf87-102">ステートメント ハンドルの割り当て</span><span class="sxs-lookup"><span data-stu-id="3bf87-102">Allocating a Statement Handle</span></span>
  <span data-ttu-id="3bf87-103">アプリケーションでステートメントを実行する前に、ステートメント ハンドルを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bf87-103">Before an application can execute a statement, it must allocate a statement handle.</span></span> <span data-ttu-id="3bf87-104">これを行うには、 *Handletype*パラメーターを SQL_HANDLE_STMT に設定し、 *InputHandle*をポイントするように**SQLAllocHandle**を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3bf87-104">It does this by calling **SQLAllocHandle** with the *HandleType* parameter set to SQL_HANDLE_STMT and *InputHandle* pointing to a connection handle.</span></span>  
  
 <span data-ttu-id="3bf87-105">ステートメント属性は、ステートメント ハンドルの特徴を表します。</span><span class="sxs-lookup"><span data-stu-id="3bf87-105">Statement attributes are characteristics of the statement handle.</span></span> <span data-ttu-id="3bf87-106">ブックマークやカーソルを使用してサンプル ステートメント属性を取り込み、ステートメントの結果セットと共に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="3bf87-106">Sample statement attributes can include using bookmarks and the kind of cursor to use with the statement's result set.</span></span> <span data-ttu-id="3bf87-107">ステートメント属性は[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)で設定され、それらの現在の設定は[SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md)を使用して取得されます。</span><span class="sxs-lookup"><span data-stu-id="3bf87-107">Statement attributes are set with [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md), and their current settings are retrieved by using [SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md).</span></span> <span data-ttu-id="3bf87-108">アプリケーションでステートメント属性を設定する必要はありません。すべてのステートメント属性には既定値があり、一部の属性は、ドライバー固有の属性になっています。</span><span class="sxs-lookup"><span data-stu-id="3bf87-108">There is no requirement that an application set any statement attributes; all statement attributes have defaults, and some are driver specific.</span></span>  
  
 <span data-ttu-id="3bf87-109">複数の ODBC ステートメント オプションと接続オプションを使用する場合は、注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="3bf87-109">Use caution in the use of several ODBC statement and connection options.</span></span> <span data-ttu-id="3bf87-110">*Foption*を SQL_ATTR_LOGIN_TIMEOUT に設定して[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)を呼び出すと、接続の確立を待機している間にアプリケーションが接続試行を待機する時間を制御します (0 は無限の待機を指定します)。</span><span class="sxs-lookup"><span data-stu-id="3bf87-110">Calling [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with *fOption* set to SQL_ATTR_LOGIN_TIMEOUT controls the time that an application waits for a connection attempt to time-out while waiting to establish a connection (0 specifies an infinite wait).</span></span> <span data-ttu-id="3bf87-111">応答時間が遅いサイトでは、この値を高く設定して、接続の完了までに十分な時間を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="3bf87-111">Sites that have slow response times can set this value high to make sure that connections have sufficient time to be completed.</span></span> <span data-ttu-id="3bf87-112">ただしこの間隔は、ドライバーが接続できない場合に、妥当な時間内にユーザーに応答できる程度に低く抑える必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bf87-112">However, the interval should always be low enough to give the user a response in a reasonable time if the driver cannot connect.</span></span>  
  
 <span data-ttu-id="3bf87-113">*Foption*を SQL_ATTR_QUERY_TIMEOUT に設定して**SQLSetStmtAttr**を呼び出すと、クエリのタイムアウト間隔が設定され、実行時間の長いクエリからサーバーとユーザーを保護できます。</span><span class="sxs-lookup"><span data-stu-id="3bf87-113">Calling **SQLSetStmtAttr** with *fOption* set to SQL_ATTR_QUERY_TIMEOUT sets a query time-out interval to help protect the server and the user from long-running queries.</span></span>  
  
 <span data-ttu-id="3bf87-114">*Foption*を SQL_ATTR_MAX_LENGTH に設定して**SQLSetStmtAttr**を呼び出すと、個々のステートメントが取得できる**テキスト**と**画像**データの量が制限されます。</span><span class="sxs-lookup"><span data-stu-id="3bf87-114">Calling **SQLSetStmtAttr** with *fOption* set to SQL_ATTR_MAX_LENGTH limits the amount of **text** and **image** data that an individual statement can retrieve.</span></span> <span data-ttu-id="3bf87-115">*Foption*を SQL_ATTR_MAX_ROWS に設定して**SQLSetStmtAttr**を呼び出すと、すべてのアプリケーションが必要とする場合に、行セットが最初の*n*行に制限されます。</span><span class="sxs-lookup"><span data-stu-id="3bf87-115">Calling **SQLSetStmtAttr** with *fOption* set to SQL_ATTR_MAX_ROWS also limits a rowset to the first *n* rows if that is all the application requires.</span></span> <span data-ttu-id="3bf87-116">SQL_ATTR_MAX_ROWS を設定すると、ドライバーがサーバーに対して SET ROWCOUNT ステートメントを実行することになります。</span><span class="sxs-lookup"><span data-stu-id="3bf87-116">Note that setting SQL_ATTR_MAX_ROWS causes the driver to issue a SET ROWCOUNT statement to the server.</span></span> <span data-ttu-id="3bf87-117">これ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、トリガーや更新プログラムを含むすべてのステートメントに影響します。</span><span class="sxs-lookup"><span data-stu-id="3bf87-117">This affects all [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] statements, including triggers and updates.</span></span>  
  
 <span data-ttu-id="3bf87-118">上記のオプションを設定するときは注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="3bf87-118">Use caution when you are setting these options.</span></span> <span data-ttu-id="3bf87-119">SQL_ATTR_MAX_LENGTH と SQL_ATTR_MAX_ROWS の場合、接続ハンドルのすべてのステートメント ハンドルが同じ設定になるようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3bf87-119">It is best if all statement handles on a connection handle have the same settings for SQL_ATTR_MAX_LENGTH and SQL_ATTR_MAX_ROWS.</span></span> <span data-ttu-id="3bf87-120">ドライバーが、あるステートメント ハンドルから、これらのオプションに異なる値を持つ別のステートメント ハンドルに切り替える場合、適切な SET TEXTSIZE ステートメントと SET ROWCOUNT ステートメントを生成して、設定を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bf87-120">If the driver switches from a statement handle to another with different values for these options, the driver must generate the appropriate SET TEXTSIZE and SET ROWCOUNT statements to change the settings.</span></span> <span data-ttu-id="3bf87-121">ユーザー SQL ステートメントには、バッチ内では先頭に含めなければならないステートメントを含めることができるので、ドライバーはユーザー SQL ステートメントと同じバッチ内にこれらのステートメントを配置することはできません。</span><span class="sxs-lookup"><span data-stu-id="3bf87-121">The driver cannot put these statements in the same batch as the user SQL statement because the user SQL statement can contain a statement that must be the first statement in a batch.</span></span> <span data-ttu-id="3bf87-122">ドライバーは SET TEXTSIZE ステートメントと SET ROWCOUNT ステートメントを別のバッチで送信する必要があります。その結果、サーバーに対する追加のラウンドトリップが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="3bf87-122">The driver must send the SET TEXTSIZE and SET ROWCOUNT statements in a separate batch, which automatically generates an additional roundtrip to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bf87-123">参照</span><span class="sxs-lookup"><span data-stu-id="3bf87-123">See Also</span></span>  
 [<span data-ttu-id="3bf87-124">ODBC&#41;&#40;クエリの実行</span><span class="sxs-lookup"><span data-stu-id="3bf87-124">Executing Queries &#40;ODBC&#41;</span></span>](executing-queries-odbc.md)  
  
  
