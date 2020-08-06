---
title: SQLEndTran |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLEndTran function
ms.assetid: 95cff841-c2d5-4e1e-a18d-f3d4696a5b85
author: rothja
ms.author: jroth
ms.openlocfilehash: e5d44756131b6133baec69e34da11055a965e2da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714342"
---
# <a name="sqlendtran"></a><span data-ttu-id="9b037-102">SQLEndTran</span><span class="sxs-lookup"><span data-stu-id="9b037-102">SQLEndTran</span></span>
  <span data-ttu-id="9b037-103">既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーは、 **SQLEndTran**が操作をコミットまたはロールバックするときに、ステートメントに関連付けられたカーソルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="9b037-103">By default, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver closes a statement's associated cursor when **SQLEndTran** commits or rolls back an operation.</span></span> <span data-ttu-id="9b037-104">サーバー カーソルは、静的カーソルでない限り、閉じられます。</span><span class="sxs-lookup"><span data-stu-id="9b037-104">Server cursors are closed unless they are static.</span></span> <span data-ttu-id="9b037-105">**SQLEndTran**が操作をコミットまたはロールバックする場合、ステートメントに関連付けられているカーソルの動作は、 [SQLSetConnectAttr](sqlsetconnectattr.md)によって設定される、ドライバー固有の ODBC 接続属性の値によって決定され SQL_COPT_SS_PRESERVE_CURSORS ます。</span><span class="sxs-lookup"><span data-stu-id="9b037-105">When **SQLEndTran** commits or rolls back an operation, the behavior of the statement's associated cursor is determined by the value of the driver-specific ODBC connection attribute SQL_COPT_SS_PRESERVE_CURSORS, set by [SQLSetConnectAttr](sqlsetconnectattr.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b037-106">参照</span><span class="sxs-lookup"><span data-stu-id="9b037-106">See Also</span></span>  
 <span data-ttu-id="9b037-107">[ODBC API の実装の詳細](odbc-api-implementation-details.md) </span><span class="sxs-lookup"><span data-stu-id="9b037-107">[ODBC API Implementation Details](odbc-api-implementation-details.md) </span></span>  
 [<span data-ttu-id="9b037-108">SQLEndTran 関数</span><span class="sxs-lookup"><span data-stu-id="9b037-108">SQLEndTran Function</span></span>](https://go.microsoft.com/fwlink/?LinkId=59342)  
  
  
