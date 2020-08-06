---
title: ODBC カーソルで Autofetch を使用する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, autofetch
- autofetch option
- cursors [ODBC], autofetch
ms.assetid: 57bd55f4-8945-4d8d-9f58-d30c81d2a514
author: rothja
ms.author: jroth
ms.openlocfilehash: e3d9374cf9ceab4a7e73cc0059783486f2bf9c41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643304"
---
# <a name="using-autofetch-with-odbc-cursors"></a><span data-ttu-id="f3dbc-102">autofetch と ODBC カーソルの併用</span><span class="sxs-lookup"><span data-stu-id="f3dbc-102">Using Autofetch with ODBC Cursors</span></span>
  <span data-ttu-id="f3dbc-103">のインスタンスに接続している場合 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC ドライバーでは、任意のサーバーカーソルの種類を使用するときに autofetch オプションがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f3dbc-103">When connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports an autofetch option when using any server cursor type.</span></span> <span data-ttu-id="f3dbc-104">Autofetch では、カーソルを開く**Sqlexecute**または**SQLExecDirect**関数にも、暗黙的な[sqlfetchscroll](../../native-client-odbc-api/sqlfetchscroll.md)(SQL_FIRST) 関数があります。</span><span class="sxs-lookup"><span data-stu-id="f3dbc-104">With autofetch, the **SQLExecute** or **SQLExecDirect** function that opens the cursor also has an implicit [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md)(SQL_FIRST) function.</span></span> <span data-ttu-id="f3dbc-105">バインドされたアプリケーション変数に、最初の行セットを構成する行がステートメント実行の一環として返されるので、ネットワーク経由でのサーバーとのやり取りが減少します。</span><span class="sxs-lookup"><span data-stu-id="f3dbc-105">The rows comprising the first rowset are returned to the bound application variables as part of the statement execution, saving another roundtrip across the network to the server.</span></span> <span data-ttu-id="f3dbc-106">Autofetch オプションが有効になっている場合、 [SQLGetData](../../native-client-odbc-api/sqlgetdata.md)はサポートされません。結果セットの列をプログラム変数にバインドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3dbc-106">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md) is not supported when the autofetch option is enabled; the result set columns must be bound to program variables.</span></span>  
  
 <span data-ttu-id="f3dbc-107">アプリケーションでは、ドライバー固有の SQL_SOPT_SS_CURSOR_OPTIONS ステートメント属性を SQL_CO_AF に設定することにより autofetch を要求します。</span><span class="sxs-lookup"><span data-stu-id="f3dbc-107">Applications request autofetch by setting the driver-specific SQL_SOPT_SS_CURSOR_OPTIONS statement attribute to SQL_CO_AF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3dbc-108">参照</span><span class="sxs-lookup"><span data-stu-id="f3dbc-108">See Also</span></span>  
 [<span data-ttu-id="f3dbc-109">ODBC&#41;&#40;のカーソルプログラミングの詳細</span><span class="sxs-lookup"><span data-stu-id="f3dbc-109">Cursor Programming Details &#40;ODBC&#41;</span></span>](cursor-programming-details-odbc.md)  
  
  
