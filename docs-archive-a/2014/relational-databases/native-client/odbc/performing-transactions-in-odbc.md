---
title: ODBC でのトランザクション |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, transactions
- transactions [ODBC]
- ODBC, transactions
ms.assetid: c5a87fa5-827a-4e6f-a0d9-924bac881eb0
author: rothja
ms.author: jroth
ms.openlocfilehash: 386b248edfdb6e0ac5eb97b3aeb6c0bbc505a5a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633810"
---
# <a name="transactions-in-odbc"></a><span data-ttu-id="d4d3b-102">ODBC でのトランザクション</span><span class="sxs-lookup"><span data-stu-id="d4d3b-102">Transactions in ODBC</span></span>
  <span data-ttu-id="d4d3b-103">ODBC のトランザクションは接続レベルで管理されます。</span><span class="sxs-lookup"><span data-stu-id="d4d3b-103">Transactions in ODBC are managed at the connection level.</span></span> <span data-ttu-id="d4d3b-104">アプリケーションはトランザクションの完了時に、その接続のすべてのステートメント ハンドルで完了したすべての作業を、コミットまたはロールバックします。</span><span class="sxs-lookup"><span data-stu-id="d4d3b-104">When an application completes a transaction, it commits or rolls back all work completed through all statement handles on that connection.</span></span> <span data-ttu-id="d4d3b-105">トランザクションをコミットまたはロールバックするには、COMMIT または ROLLBACK ステートメントを送信するのではなく、アプリケーションで[SQLEndTran](../../native-client-odbc-api/sqlendtran.md)を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4d3b-105">To commit or roll back a transaction, applications should call [SQLEndTran](../../native-client-odbc-api/sqlendtran.md) instead of submitting a COMMIT or ROLLBACK statement.</span></span>  
  
 <span data-ttu-id="d4d3b-106">アプリケーションは、 [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md)を呼び出して、トランザクションを管理する2つの ODBC モードを切り替えます。</span><span class="sxs-lookup"><span data-stu-id="d4d3b-106">An application calls [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) to switch between the two ODBC modes of managing transactions:</span></span>  
  
-   <span data-ttu-id="d4d3b-107">自動コミット モード</span><span class="sxs-lookup"><span data-stu-id="d4d3b-107">Autocommit mode</span></span>  
  
     <span data-ttu-id="d4d3b-108">各ステートメントは、正常に完了したときに自動的にコミットされます。</span><span class="sxs-lookup"><span data-stu-id="d4d3b-108">Each statement is automatically committed when it is completed successfully.</span></span> <span data-ttu-id="d4d3b-109">自動コミット モードで実行するときは、他のトランザクション管理関数は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="d4d3b-109">When you run in autocommit mode, no other transaction management functions are required.</span></span>  
  
-   <span data-ttu-id="d4d3b-110">手動コミット モード</span><span class="sxs-lookup"><span data-stu-id="d4d3b-110">Manual-commit mode</span></span>  
  
     <span data-ttu-id="d4d3b-111">実行されたすべてのステートメントは、 **SQLEndTran**を呼び出すことによって明示的に停止されるまで、同じトランザクションに含まれます。</span><span class="sxs-lookup"><span data-stu-id="d4d3b-111">All executed statements are included in the same transaction until it is specifically stopped by calling **SQLEndTran**.</span></span>  
  
 <span data-ttu-id="d4d3b-112">自動コミット モードは、ODBC の既定のトランザクション モードです。</span><span class="sxs-lookup"><span data-stu-id="d4d3b-112">Autocommit mode is the default transaction mode for ODBC.</span></span> <span data-ttu-id="d4d3b-113">接続が確立されると、 **SQLSetConnectAttr**が呼び出され、自動コミットモードをオフに設定して手動コミットモードに切り替えるまで、自動コミットモードになります。</span><span class="sxs-lookup"><span data-stu-id="d4d3b-113">When a connection is made, it is in autocommit mode until **SQLSetConnectAttr** is called to switch to manual-commit mode by setting autocommit mode off.</span></span> <span data-ttu-id="d4d3b-114">アプリケーションが自動コミットを無効にすると、次にデータベースに送信されるステートメントでトランザクションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="d4d3b-114">When an application turns autocommit off, the next statement sent to the database starts a transaction.</span></span> <span data-ttu-id="d4d3b-115">その後、トランザクションは、アプリケーションが SQL_COMMIT オプションまたは SQL_ROLLBACK オプションを使用して**SQLEndTran**を呼び出すまで有効になります。</span><span class="sxs-lookup"><span data-stu-id="d4d3b-115">The transaction then remains in effect until the application calls **SQLEndTran** with either the SQL_COMMIT or SQL_ROLLBACK options.</span></span> <span data-ttu-id="d4d3b-116">**SQLEndTran**の後にデータベースに送信されるコマンドは、次のトランザクションを開始します。</span><span class="sxs-lookup"><span data-stu-id="d4d3b-116">The command sent to the database after **SQLEndTran** starts the next transaction.</span></span>  
  
 <span data-ttu-id="d4d3b-117">手動コミット モードから自動コミット モードに切り替えると、ドライバーは接続で現在開かれているすべてのトランザクションをコミットします。</span><span class="sxs-lookup"><span data-stu-id="d4d3b-117">If an application switches from manual-commit to autocommit mode, the driver commits any transactions currently open on the connection.</span></span>  
  
 <span data-ttu-id="d4d3b-118">ODBC アプリケーションで BEGIN TRANSACTION、COMMIT TRANSACTION、ROLLBACK TRANSACTION などの Transact-SQL トランザクション ステートメントを使用すると、ドライバーの動作が不確定になる可能性があるので、このような Transact-SQL トランザクション ステートメントは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="d4d3b-118">ODBC applications should not use Transact-SQL transaction statements such as BEGIN TRANSACTION, COMMIT TRANSACTION, or ROLLBACK TRANSACTION because this can cause indeterminate behavior in the driver.</span></span> <span data-ttu-id="d4d3b-119">ODBC アプリケーションは自動コミットモードで実行する必要があり、トランザクション管理関数やステートメントを使用したり、手動コミットモードで実行したり、ODBC **SQLEndTran**関数を使用してトランザクションをコミットまたはロールバックしたりする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4d3b-119">An ODBC application should run in autocommit mode and not use any transaction management functions or statements, or run in manual-commit mode and use the ODBC **SQLEndTran** function to either commit or roll back transactions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4d3b-120">参照</span><span class="sxs-lookup"><span data-stu-id="d4d3b-120">See Also</span></span>  
 [<span data-ttu-id="d4d3b-121">ODBC&#41;&#40;のトランザクションの実行</span><span class="sxs-lookup"><span data-stu-id="d4d3b-121">Performing Transactions &#40;ODBC&#41;</span></span>](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
