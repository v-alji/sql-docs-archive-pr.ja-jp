---
title: カーソルの同時実行 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- concurrency [ODBC]
- cursors [ODBC], concurrency
- ODBC cursors, concurrency
ms.assetid: 68228ece-cbf1-4f19-bfdc-053884c1af48
author: rothja
ms.author: jroth
ms.openlocfilehash: c47f24152978fedf8f2c3d49ec3b721969712814
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643305"
---
# <a name="cursor-concurrency-odbc"></a><span data-ttu-id="ca877-102">カーソル コンカレンシー (ODBC)</span><span class="sxs-lookup"><span data-stu-id="ca877-102">Cursor Concurrency (ODBC)</span></span>
  <span data-ttu-id="ca877-103">カーソル操作は、カーソルの種類と同様に、アプリケーションで設定されるコンカレンシー オプションの影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="ca877-103">Cursor operations, like cursor types, are affected by the concurrency options set by the application.</span></span> <span data-ttu-id="ca877-104">同時実行オプションは、 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)の SQL_ATTR_CONCURRENCY オプションを使用して設定します。</span><span class="sxs-lookup"><span data-stu-id="ca877-104">Concurrency options are set using the SQL_ATTR_CONCURRENCY option of [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).</span></span> <span data-ttu-id="ca877-105">コンカレンシーの種類は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ca877-105">The concurrency types are:</span></span>  
  
-   <span data-ttu-id="ca877-106">読み取り専用 (SQL_CONCUR_READONLY)</span><span class="sxs-lookup"><span data-stu-id="ca877-106">Read-only (SQL_CONCUR_READONLY)</span></span>  
  
-   <span data-ttu-id="ca877-107">値 (SQL_CONCUR_VALUES)</span><span class="sxs-lookup"><span data-stu-id="ca877-107">Values (SQL_CONCUR_VALUES)</span></span>  
  
-   <span data-ttu-id="ca877-108">行バージョン (SQL_CONCUR_ROWVER)</span><span class="sxs-lookup"><span data-stu-id="ca877-108">Row version (SQL_CONCUR_ROWVER)</span></span>  
  
-   <span data-ttu-id="ca877-109">ロック (SQL_CONCUR_LOCK)</span><span class="sxs-lookup"><span data-stu-id="ca877-109">Lock (SQL_CONCUR_LOCK)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca877-110">参照</span><span class="sxs-lookup"><span data-stu-id="ca877-110">See Also</span></span>  
 [<span data-ttu-id="ca877-111">カーソルのプロパティ</span><span class="sxs-lookup"><span data-stu-id="ca877-111">Cursor Properties</span></span>](cursor-properties.md)  
  
  
