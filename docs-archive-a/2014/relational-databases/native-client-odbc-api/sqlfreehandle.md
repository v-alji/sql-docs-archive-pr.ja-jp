---
title: SQLFreeHandle |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFreeHandle function
ms.assetid: d374e5c8-ed35-43bf-8dd6-c37e38d9b5f1
author: rothja
ms.author: jroth
ms.openlocfilehash: f51f031bec05715e0345507278113f4f16179a77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639478"
---
# <a name="sqlfreehandle"></a><span data-ttu-id="c0bbd-102">SQLFreeHandle</span><span class="sxs-lookup"><span data-stu-id="c0bbd-102">SQLFreeHandle</span></span>
  <span data-ttu-id="c0bbd-103">手動コミットモードでは、トランザクションが開いているステートメントハンドルで**Sqlfreehandle**を呼び出すと、データベースに対する保留中の変更がロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="c0bbd-103">In manual-commit mode, calling **SQLFreeHandle** on a statement handle with an open transaction causes a rollback of pending changes to the database.</span></span> <span data-ttu-id="c0bbd-104">ステートメントハンドルで**Sqlfreehandle**を呼び出すと、開いているカーソルが常に閉じられ、保留中の結果は破棄され、ステートメントハンドルに関連付けられているすべてのリソースが解放されます。</span><span class="sxs-lookup"><span data-stu-id="c0bbd-104">Calling **SQLFreeHandle** on a statement handle always closes any open cursors and discards pending results, freeing all resources associated with the statement handle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0bbd-105">参照</span><span class="sxs-lookup"><span data-stu-id="c0bbd-105">See Also</span></span>  
 <span data-ttu-id="c0bbd-106">[SQLFreeHandle 関数](https://go.microsoft.com/fwlink/?LinkId=59345) </span><span class="sxs-lookup"><span data-stu-id="c0bbd-106">[SQLFreeHandle Function](https://go.microsoft.com/fwlink/?LinkId=59345) </span></span>  
 [<span data-ttu-id="c0bbd-107">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="c0bbd-107">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
