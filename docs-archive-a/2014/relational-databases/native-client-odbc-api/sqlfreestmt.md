---
title: SQLFreeStmt |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
author: rothja
ms.author: jroth
ms.openlocfilehash: d38237b53ed994fd3272f9e129564320f88c6e37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639477"
---
# <a name="sqlfreestmt"></a><span data-ttu-id="9744a-102">SQLFreeStmt</span><span class="sxs-lookup"><span data-stu-id="9744a-102">SQLFreeStmt</span></span>
  <span data-ttu-id="9744a-103">**SQLFreeStmt**は、ODBC 3.0 以降では推奨されません。</span><span class="sxs-lookup"><span data-stu-id="9744a-103">**SQLFreeStmt** is not recommended in ODBC 3.0 and later.</span></span> <span data-ttu-id="9744a-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーでは、 **SQLFreeStmt**に対して定義されているすべての*オプション*値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9744a-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports all defined *Option* values for **SQLFreeStmt**.</span></span> <span data-ttu-id="9744a-105">ただし、 [Sqlcloセキュリティー](sqlclosecursor.md)、 [SQLBindParameter](sqlbindparameter.md)、 [SQLBindCol](sqlbindcol.md)、 **SQLSetDescField**、および[sqlfreehandle](sqlfreehandle.md)は、 **SQLFreeStmt**の関数を置き換えたり複製したりする必要があり、代わりに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9744a-105">However, [SQLCloseCursor](sqlclosecursor.md), [SQLBindParameter](sqlbindparameter.md), [SQLBindCol](sqlbindcol.md), **SQLSetDescField**, and [SQLFreeHandle](sqlfreehandle.md) replace or duplicate the function of **SQLFreeStmt** and should be used instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9744a-106">参照</span><span class="sxs-lookup"><span data-stu-id="9744a-106">See Also</span></span>  
 <span data-ttu-id="9744a-107">[SQLFreeStmt 関数](https://go.microsoft.com/fwlink/?LinkId=59346) </span><span class="sxs-lookup"><span data-stu-id="9744a-107">[SQLFreeStmt Function](https://go.microsoft.com/fwlink/?LinkId=59346) </span></span>  
 [<span data-ttu-id="9744a-108">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="9744a-108">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
