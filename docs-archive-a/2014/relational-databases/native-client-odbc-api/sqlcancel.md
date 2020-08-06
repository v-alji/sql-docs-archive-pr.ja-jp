---
title: SQLCancel |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
author: rothja
ms.author: jroth
ms.openlocfilehash: dc3d86229501f80b25fb077788d1835a5f4f5c96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639957"
---
# <a name="sqlcancel"></a><span data-ttu-id="1d8fe-102">SQLCancel</span><span class="sxs-lookup"><span data-stu-id="1d8fe-102">SQLCancel</span></span>
  <span data-ttu-id="1d8fe-103">[SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516)のトピックでは、ODBC 2.x で、 `SQLCancel` ステートメントで処理が実行されていないときにアプリケーションがを呼び出すと、オプションと同じ効果があることが示されて `SQLCancel` います `SQLFreeStmt` `SQL_CLOSE` 。この動作は、完全を期すためだけに定義されており、アプリケーションは `SQLFreeStmt` `SQLCloseCursor` カーソルを閉じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d8fe-103">The [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) topic says that in ODBC 2.x, if an application calls `SQLCancel` when no processing is being done on the statement, `SQLCancel` has the same effect as `SQLFreeStmt` with the `SQL_CLOSE` option; this behavior is defined only for completeness and applications should call `SQLFreeStmt` or `SQLCloseCursor` to close cursors.</span></span> <span data-ttu-id="1d8fe-104">ただし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネイティブ クライアント アプリケーションで ODBC API バージョンを 3.5.x 以降に設定した場合も、`SQLCancel` 関数では、ODBC 2.x の動作が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1d8fe-104">But even if your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client application sets the ODBC API version to be 3.5.x or later, the `SQLCancel` function will use the ODBC 2.x behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d8fe-105">参照</span><span class="sxs-lookup"><span data-stu-id="1d8fe-105">See Also</span></span>  
 <span data-ttu-id="1d8fe-106">[SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) </span><span class="sxs-lookup"><span data-stu-id="1d8fe-106">[SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) </span></span>  
 [<span data-ttu-id="1d8fe-107">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="1d8fe-107">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
