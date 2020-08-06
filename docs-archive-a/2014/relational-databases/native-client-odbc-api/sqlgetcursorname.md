---
title: Sqlgetカーソル名 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetCursorName function
ms.assetid: 3a427a23-28ef-49aa-b9ec-6cab0914bdf3
author: rothja
ms.author: jroth
ms.openlocfilehash: 01ce6e42b4e8753d07309ec7ce298d4f743d4a6d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631006"
---
# <a name="sqlgetcursorname"></a><span data-ttu-id="1717a-102">SQLGetCursorName</span><span class="sxs-lookup"><span data-stu-id="1717a-102">SQLGetCursorName</span></span>
  <span data-ttu-id="1717a-103">アプリケーションでカーソル名が指定されていない場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーによって、カーソルの生成時にアプリケーション用に1つが生成されます。</span><span class="sxs-lookup"><span data-stu-id="1717a-103">If the application does not specify a cursor name, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver generates one for the application upon cursor generation.</span></span> <span data-ttu-id="1717a-104">アプリケーションでは、 **Sqlgetcursor name**を使用して、位置指定の UPDATE および DELETE ステートメントのドライバーで定義されたカーソル名を取得できます。</span><span class="sxs-lookup"><span data-stu-id="1717a-104">The application can use **SQLGetCursorName** to retrieve the driver-defined cursor name for positioned UPDATE and DELETE statements.</span></span> <span data-ttu-id="1717a-105">アプリケーションでは、位置指定データ操作ステートメントを利用するために**SQLSetCursorName**を呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1717a-105">The application does not need to call **SQLSetCursorName** to take advantage of positioned data manipulation statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1717a-106">参照</span><span class="sxs-lookup"><span data-stu-id="1717a-106">See Also</span></span>  
 <span data-ttu-id="1717a-107">[Sqlgetカーソル名関数](https://go.microsoft.com/fwlink/?LinkId=59349) </span><span class="sxs-lookup"><span data-stu-id="1717a-107">[SQLGetCursorName Function](https://go.microsoft.com/fwlink/?LinkId=59349) </span></span>  
 [<span data-ttu-id="1717a-108">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="1717a-108">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
