---
title: カーソルトランザクション分離レベル |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- isolation levels [ODBC]
- ODBC applications, row versioning
- cursors [ODBC], isolation levels
- ODBC cursors, isolation levels
- row versioning [SQL Server], ODBC
ms.assetid: 0c6663a4-5a25-44aa-8fe4-e35af9bf4a83
author: rothja
ms.author: jroth
ms.openlocfilehash: 30f3dc8a9136a7cbe1d5897cb0bcc9fff8c35ab2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738364"
---
# <a name="cursor-transaction-isolation-level"></a><span data-ttu-id="18bb0-102">カーソルのトランザクション分離レベル</span><span class="sxs-lookup"><span data-stu-id="18bb0-102">Cursor Transaction Isolation Level</span></span>
  <span data-ttu-id="18bb0-103">カーソルのロック動作全体は、コンカレンシー属性とクライアントが設定したトランザクション分離レベルの相互作用の影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="18bb0-103">The complete locking behavior of cursors is based on an interaction between concurrency attributes and the transaction isolation level set by the client.</span></span> <span data-ttu-id="18bb0-104">ODBC クライアントでは、 [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) SQL_ATTR_TXN_ISOLATION または SQL_COPT_SS_TXN_ISOLATION 属性を使用してトランザクション分離レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="18bb0-104">ODBC clients set the transaction isolation level using the [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) SQL_ATTR_TXN_ISOLATION or SQL_COPT_SS_TXN_ISOLATION attributes.</span></span> <span data-ttu-id="18bb0-105">特定のカーソル環境のロック動作は、コンカレンシーのロック動作とトランザクション分離レベルのオプションを組み合わせることによって決まります。</span><span class="sxs-lookup"><span data-stu-id="18bb0-105">The locking behavior of a specific cursor environment is determined by combining the locking behaviors of the concurrency and transaction isolation level options.</span></span>  
  
 <span data-ttu-id="18bb0-106">Native Client ODBC ドライバーでは、次のカーソルトランザクション分離レベルがサポートされてい [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="18bb0-106">The following cursor transaction isolation levels are supported by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver:</span></span>  
  
-   <span data-ttu-id="18bb0-107">READ COMMITTED (SQL_TXN_READ_COMMITTED)</span><span class="sxs-lookup"><span data-stu-id="18bb0-107">Read committed (SQL_TXN_READ_COMMITTED)</span></span>  
  
-   <span data-ttu-id="18bb0-108">READ UNCOMMITTED (SQL_TXN_READ_UNCOMMITTED)</span><span class="sxs-lookup"><span data-stu-id="18bb0-108">Read uncommitted (SQL_TXN_READ_UNCOMMITTED)</span></span>  
  
-   <span data-ttu-id="18bb0-109">REPEATABLE READ (SQL_TXN_REPEATABLE_READ)</span><span class="sxs-lookup"><span data-stu-id="18bb0-109">Repeatable read (SQL_TXN_REPEATABLE_READ)</span></span>  
  
-   <span data-ttu-id="18bb0-110">SERIALIZABLE (SQL_TXN_SERIALIZABLE)</span><span class="sxs-lookup"><span data-stu-id="18bb0-110">Serializable (SQL_TXN_SERIALIZABLE)</span></span>  
  
-   <span data-ttu-id="18bb0-111">SNAPSHOT (SQL_TXN_SS_SNAPSHOT)</span><span class="sxs-lookup"><span data-stu-id="18bb0-111">Snapshot (SQL_TXN_SS_SNAPSHOT)</span></span>  
  
 <span data-ttu-id="18bb0-112">ODBC API では、追加のトランザクション分離レベルが指定されていますが、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] または Native CLIENT ODBC ドライバーではサポートされていないことに注意して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="18bb0-112">Note that the ODBC API specifies additional transaction isolation levels, but these are not supported by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18bb0-113">参照</span><span class="sxs-lookup"><span data-stu-id="18bb0-113">See Also</span></span>  
 [<span data-ttu-id="18bb0-114">カーソルのプロパティ</span><span class="sxs-lookup"><span data-stu-id="18bb0-114">Cursor Properties</span></span>](cursor-properties.md)  
  
  
