---
title: 分散トランザクションの実行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, performing distributed transactions
- SQL Server Native Client ODBC driver, transactions
- distributed transactions [ODBC]
- transactions [ODBC]
- ODBC, transactions
ms.assetid: 2c17fba0-7a3c-453c-91b7-f801e7b39ccb
author: rothja
ms.author: jroth
ms.openlocfilehash: 9ec23fd1883749e35e67f888e26bdf031ccf7fb8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633813"
---
# <a name="performing-distributed-transactions"></a><span data-ttu-id="fbc1c-102">分散トランザクションの実行</span><span class="sxs-lookup"><span data-stu-id="fbc1c-102">Performing Distributed Transactions</span></span>
  <span data-ttu-id="fbc1c-103">Microsoft 分散トランザクション コーディネーター (MS DTC) により、アプリケーションで [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の複数のインスタンスにトランザクションを分散できるようになります。</span><span class="sxs-lookup"><span data-stu-id="fbc1c-103">The Microsoft Distributed Transaction Coordinator (MS DTC) allows applications to extend transactions across two or more instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fbc1c-104">また、Open Group DTP XA 標準に準拠するトランザクション マネージャーによって管理されるトランザクションに参加させることもできます。</span><span class="sxs-lookup"><span data-stu-id="fbc1c-104">It also allows applications to participate in transactions managed by transaction managers that comply with the Open Group DTP XA standard.</span></span>  
  
 <span data-ttu-id="fbc1c-105">通常、すべてのトランザクション管理コマンドは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーを経由してサーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="fbc1c-105">Normally, all transaction management commands are sent through the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver to the server.</span></span> <span data-ttu-id="fbc1c-106">アプリケーションは、自動コミットモードがオフになっている状態で[SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md)を呼び出すことによってトランザクションを開始します。</span><span class="sxs-lookup"><span data-stu-id="fbc1c-106">The application starts a transaction by calling [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) with the autocommit mode turned off.</span></span> <span data-ttu-id="fbc1c-107">次に、アプリケーションは、トランザクションを構成する更新を実行し、SQL_COMMIT または SQL_ROLLBACK オプションを使用して[SQLEndTran](../../native-client-odbc-api/sqlendtran.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="fbc1c-107">The application then performs the updates comprising the transaction and calls [SQLEndTran](../../native-client-odbc-api/sqlendtran.md) with either the SQL_COMMIT or SQL_ROLLBACK option.</span></span>  
  
 <span data-ttu-id="fbc1c-108">ただし、MS dtc を使用する場合、MS DTC はトランザクションマネージャーになり、アプリケーションは**SQLEndTran**を使用しなくなります。</span><span class="sxs-lookup"><span data-stu-id="fbc1c-108">When using MS DTC, however, MS DTC becomes the transaction manager and the application no longer uses **SQLEndTran**.</span></span>  
  
 <span data-ttu-id="fbc1c-109">分散トランザクションに参加しているときに 2 番目の分散トランザクションに参加すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは元の分散トランザクションへの参加を解除して、新しいトランザクションに参加します。</span><span class="sxs-lookup"><span data-stu-id="fbc1c-109">When enlisted in a distributed transaction, and then enlist in a second distributed transaction, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC Driver defects from the original distributed transaction and enlists in the new transaction.</span></span> <span data-ttu-id="fbc1c-110">詳細については、「 [DTC プログラマーズリファレンス](https://msdn.microsoft.com/library/ms686108\(VS.85\).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbc1c-110">For more information, see [DTC Programmer's Reference](https://msdn.microsoft.com/library/ms686108\(VS.85\).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbc1c-111">参照</span><span class="sxs-lookup"><span data-stu-id="fbc1c-111">See Also</span></span>  
 [<span data-ttu-id="fbc1c-112">ODBC&#41;&#40;のトランザクションの実行</span><span class="sxs-lookup"><span data-stu-id="fbc1c-112">Performing Transactions &#40;ODBC&#41;</span></span>](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
