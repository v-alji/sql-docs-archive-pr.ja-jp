---
title: 非同期モードと SQLCancel |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- asynchronous operations [SQL Server Native Client]
- SQLCancel function
- SQLSetConnectAttr function
- SQL Server Native Client, asynchronous operations
- ODBC functions
- ODBC applications, asynchronous operations
- SQL Server Native Client ODBC driver, asynchronous mode
ms.assetid: f31702a2-df76-4589-ac3b-da5412c03dc2
author: rothja
ms.author: jroth
ms.openlocfilehash: 9071c6821e6edeb577b639223e42899d2927bced
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643263"
---
# <a name="asynchronous-mode-and-sqlcancel"></a><span data-ttu-id="e4b55-102">非同期モードと SQLCancel</span><span class="sxs-lookup"><span data-stu-id="e4b55-102">Asynchronous Mode and SQLCancel</span></span>
  <span data-ttu-id="e4b55-103">ODBC 関数には、同期して動作する関数と非同期に動作する関数があります。</span><span class="sxs-lookup"><span data-stu-id="e4b55-103">Some ODBC functions can operate either synchronously or asynchronously.</span></span> <span data-ttu-id="e4b55-104">アプリケーションでは、ステートメント ハンドルまたは接続ハンドルのいずれかに対して非同期動作を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="e4b55-104">The application can enable asynchronous operations for either a statement handle or a connection handle.</span></span> <span data-ttu-id="e4b55-105">オプションが接続ハンドル用に設定されている場合、接続ハンドルのすべてのステートメント ハンドルに影響します。</span><span class="sxs-lookup"><span data-stu-id="e4b55-105">If the option is set for a connection handle, it affects all statement handles on the connection handle.</span></span> <span data-ttu-id="e4b55-106">アプリケーションで次のステートメントを使用すると、非同期動作を有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="e4b55-106">The application uses the following statements to enable or disable asynchronous operations:</span></span>  
  
```  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
```  
  
 <span data-ttu-id="e4b55-107">アプリケーションが同期モードで ODBC 関数を呼び出した場合、サーバーでのコマンドの実行が完了したことがドライバーに通知されるまでは、ドライバーからアプリケーションに制御が戻りません。</span><span class="sxs-lookup"><span data-stu-id="e4b55-107">When an application calls an ODBC function in synchronous mode, the driver does not return control to the application until it is notified that the server has completed the command.</span></span>  
  
 <span data-ttu-id="e4b55-108">非同期動作の場合は、ドライバーからサーバーにコマンドを送信する前でも、ドライバーからアプリケーションに直ちに制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="e4b55-108">When operating asynchronously, the driver immediately returns control to the application, even before sending the command to the server.</span></span> <span data-ttu-id="e4b55-109">ドライバーは、リターン コードを SQL_STILL_EXECUTING に設定します。</span><span class="sxs-lookup"><span data-stu-id="e4b55-109">The driver sets the return code to SQL_STILL_EXECUTING.</span></span> <span data-ttu-id="e4b55-110">アプリケーションでは他の作業を実行できます。</span><span class="sxs-lookup"><span data-stu-id="e4b55-110">The application can then perform other work.</span></span>  
  
 <span data-ttu-id="e4b55-111">アプリケーションでコマンドが完了したかどうかをテストするときは、ドライバーに対して同じ関数を同じパラメーターを指定して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e4b55-111">When the application tests for completion of the command, it makes the same function call with the same parameters to the driver.</span></span> <span data-ttu-id="e4b55-112">ドライバーがサーバーからまだ応答を受け取っていない場合、SQL_STILL_EXECUTING が再び返されます。</span><span class="sxs-lookup"><span data-stu-id="e4b55-112">If the driver has not yet received an answer from the server, it will again return SQL_STILL_EXECUTING.</span></span> <span data-ttu-id="e4b55-113">アプリケーションでは、リターン コードが SQL_STILL_EXECUTING 以外になるまで、定期的にコマンドをテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4b55-113">The application must test the command periodically until the return code is something other than SQL_STILL_EXECUTING.</span></span> <span data-ttu-id="e4b55-114">アプリケーションで他のリターン コードを受け取ると、それが SQL_ERROR であっても、コマンドが完了したことがわかります。</span><span class="sxs-lookup"><span data-stu-id="e4b55-114">When the application gets some other return code, even SQL_ERROR, it can determine that the command has completed.</span></span>  
  
 <span data-ttu-id="e4b55-115">コマンドが長時間未完了になることがあります。</span><span class="sxs-lookup"><span data-stu-id="e4b55-115">Sometimes a command is outstanding for a long time.</span></span> <span data-ttu-id="e4b55-116">アプリケーションが応答を待たずにコマンドをキャンセルする必要がある場合は、未解決のコマンドと同じステートメントハンドルを使用して**SQLCancel**を呼び出すことによって、この操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="e4b55-116">If the application needs to cancel the command without waiting for a reply, it can do so by calling **SQLCancel** with the same statement handle as the outstanding command.</span></span> <span data-ttu-id="e4b55-117">これは、 **SQLCancel**を使用する必要がある唯一の時間です。</span><span class="sxs-lookup"><span data-stu-id="e4b55-117">This is the only time **SQLCancel** should be used.</span></span> <span data-ttu-id="e4b55-118">一部のプログラマは、結果セットを使用して一部の処理を行ったときに、結果セットの残りの部分を取り消す必要がある場合に、 **SQLCancel**を使用します。</span><span class="sxs-lookup"><span data-stu-id="e4b55-118">Some programmers use **SQLCancel** when they have processed part way through a result set and want to cancel the rest of the result set.</span></span> <span data-ttu-id="e4b55-119">**SQLCancel**ではなく、未処理の結果セットの残りの部分を取り消すには、 [Sqlmoreresults](../../native-client-odbc-api/sqlmoreresults.md)または[sqlcloセキュリティー](../../native-client-odbc-api/sqlclosecursor.md)を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4b55-119">[SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) or [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) should be used to cancel the remainder of an outstanding result set, not **SQLCancel**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4b55-120">参照</span><span class="sxs-lookup"><span data-stu-id="e4b55-120">See Also</span></span>  
 [<span data-ttu-id="e4b55-121">SQL Server Native Client ODBC ドライバー アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="e4b55-121">Creating a SQL Server Native Client ODBC Driver Application</span></span>](creating-a-driver-application.md)  
  
  
