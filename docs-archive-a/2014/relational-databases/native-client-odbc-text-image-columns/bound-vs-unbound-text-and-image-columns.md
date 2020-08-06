---
title: バインドされたテキストと画像の列 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: ffd3442e-d880-46e9-b848-2365a09a2406
author: rothja
ms.author: jroth
ms.openlocfilehash: 20a91d26ac8c2d1201386cb19bde13b49a3dbada
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741949"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a><span data-ttu-id="2af9c-102">バインドされた text、image 型の列とバインドされない text、image 型の列</span><span class="sxs-lookup"><span data-stu-id="2af9c-102">Bound vs. Unbound Text and Image Columns</span></span>
  <span data-ttu-id="2af9c-103">サーバーカーソルを使用する場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーは、 **sqlfetch**の実行時に、バインドされていない**text**、 **ntext**、または**image**型の列のデータを転送しないように最適化されています。</span><span class="sxs-lookup"><span data-stu-id="2af9c-103">When using server cursors, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver is optimized to not transmit the data for unbound **text**, **ntext**, or **image** columns at the time **SQLFetch** is performed.</span></span> <span data-ttu-id="2af9c-104">**Text**型、 **ntext**型、または**image**型のデータは、アプリケーションが列に対して[SQLGetData](../native-client-odbc-api/sqlgetdata.md)を発行するまで、実際にはサーバーから取得されません。</span><span class="sxs-lookup"><span data-stu-id="2af9c-104">The **text**, **ntext**, or **image** data is not actually retrieved from the server until the application issues [SQLGetData](../native-client-odbc-api/sqlgetdata.md) for the column.</span></span>  
  
 <span data-ttu-id="2af9c-105">ユーザーがカーソル内を上下にスクロールしている間に、 **text**、 **ntext**、または**image**データが表示されないように、多くのアプリケーションを記述できます。</span><span class="sxs-lookup"><span data-stu-id="2af9c-105">Many applications can be written so that no **text**, **ntext**, or **image** data is displayed while a user is simply scrolling up and down in a cursor.</span></span> <span data-ttu-id="2af9c-106">ユーザーが行を選択して詳細を取得すると、アプリケーションは**SQLGetData**を呼び出して、 **text**、 **ntext**、または**image**データを取得できます。</span><span class="sxs-lookup"><span data-stu-id="2af9c-106">When a user selects a row to get more detail, the application can then call **SQLGetData** to retrieve the **text**, **ntext**, or **image** data.</span></span> <span data-ttu-id="2af9c-107">これにより、ユーザーが選択していない行の**text**型、 **ntext**型、または**image**型のデータが転送されるのを防ぐことができるため、非常に大量のデータの転送を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="2af9c-107">This will prevent transmitting the **text**, **ntext**, or **image** data for any of the rows the user does not select, and can therefore prevent the transmission of very large amounts of data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2af9c-108">参照</span><span class="sxs-lookup"><span data-stu-id="2af9c-108">See Also</span></span>  
 <span data-ttu-id="2af9c-109">[Text 列と Image 列の管理](managing-text-and-image-columns.md) </span><span class="sxs-lookup"><span data-stu-id="2af9c-109">[Managing Text and Image Columns](managing-text-and-image-columns.md) </span></span>  
 [<span data-ttu-id="2af9c-110">カーソル動作</span><span class="sxs-lookup"><span data-stu-id="2af9c-110">Cursor Behaviors</span></span>](../native-client-odbc-cursors/cursor-behaviors.md)  
  
  
