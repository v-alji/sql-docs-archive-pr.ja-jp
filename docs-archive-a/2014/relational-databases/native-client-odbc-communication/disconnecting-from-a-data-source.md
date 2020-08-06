---
title: データソースからの切断 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, connections
- data sources [SQL Server Native Client]
- disconnecting [ODBC]
- ODBC applications, disconnecting
- SQLDisconnect function
- ODBC applications, data sources
- connections [SQL Server Native Client]
- SQLFreeHandle function
- ODBC data sources, disconnecting
- SQL Server Native Client ODBC driver, data sources
- ODBC functions
- SQL Server Native Client ODBC driver, connections
ms.assetid: 65b0267d-b2ab-4a59-83f2-436d90cfbf79
author: rothja
ms.author: jroth
ms.openlocfilehash: 5db3b83ab65d854f3a4d2182d9a4a1314e097681
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640908"
---
# <a name="disconnecting-from-a-data-source"></a><span data-ttu-id="f5969-102">データ ソースからの切断</span><span class="sxs-lookup"><span data-stu-id="f5969-102">Disconnecting from a Data Source</span></span>
  <span data-ttu-id="f5969-103">アプリケーションでデータソースの使用が完了すると、 **Sqldisconnect**が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f5969-103">When an application has finished using a data source, it calls **SQLDisconnect**.</span></span> <span data-ttu-id="f5969-104">**Sqldisconnect**は、接続に割り当てられているすべてのステートメントを解放し、データソースからドライバーを切断します。</span><span class="sxs-lookup"><span data-stu-id="f5969-104">**SQLDisconnect** frees any statements that are allocated on the connection and disconnects the driver from the data source.</span></span> <span data-ttu-id="f5969-105">切断後、アプリケーションは[Sqlfreehandle](../native-client-odbc-api/sqlfreehandle.md)を呼び出して接続ハンドルを解放できます。</span><span class="sxs-lookup"><span data-stu-id="f5969-105">After disconnecting, the application can call [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) to free the connection handle.</span></span> <span data-ttu-id="f5969-106">終了する前に、アプリケーションは**Sqlfreehandle**を呼び出して環境ハンドルを解放します。</span><span class="sxs-lookup"><span data-stu-id="f5969-106">Before exiting, an application also calls **SQLFreeHandle** to free the environment handle.</span></span>  
  
 <span data-ttu-id="f5969-107">切断後は、割り当てられていた接続ハンドルを再利用して、別のデータ ソースに接続したり、同じデータ ソースに再接続したりできます。</span><span class="sxs-lookup"><span data-stu-id="f5969-107">After disconnecting, an application can reuse the allocated connection handle, either to connect to a different data source or reconnect to the same data source.</span></span> <span data-ttu-id="f5969-108">切断してから後で再接続するか、接続した状態を維持するかを決める際、アプリケーションの作成者は各操作の相対コストを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5969-108">The decision to remain connected instead of disconnecting and reconnecting later requires that the application writer consider the relative costs of each option.</span></span> <span data-ttu-id="f5969-109">接続メディアによっては、データ ソースに接続し、接続した状態を維持するのに比較的コストがかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f5969-109">Connecting to a data source and remaining connected can be relatively costly, depending on the connection medium.</span></span> <span data-ttu-id="f5969-110">両者を比較検討する場合は、アプリケーションで同じデータ ソースに追加操作が行われる可能性やタイミングについて想定することも必要です。</span><span class="sxs-lookup"><span data-stu-id="f5969-110">In making a trade-off, the application must also make assumptions about the probability and timing of additional operations on the same data source.</span></span> <span data-ttu-id="f5969-111">また、アプリケーションで複数の接続が必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="f5969-111">An application may also have to use more than one connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5969-112">参照</span><span class="sxs-lookup"><span data-stu-id="f5969-112">See Also</span></span>  
 [<span data-ttu-id="f5969-113">ODBC&#41;&#40;SQL Server との通信</span><span class="sxs-lookup"><span data-stu-id="f5969-113">Communicating with SQL Server &#40;ODBC&#41;</span></span>](communicating-with-sql-server-odbc.md)  
  
  
