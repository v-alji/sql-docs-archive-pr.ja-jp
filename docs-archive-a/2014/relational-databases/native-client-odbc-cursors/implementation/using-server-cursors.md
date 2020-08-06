---
title: サーバーカーソルを使用する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, cursors
- cursors [ODBC], server cursors
- ODBC cursors, server cursors
- server cursors [SQL Server]
ms.assetid: 8a6d99b7-10b8-4474-8639-4914b25ba170
author: rothja
ms.author: jroth
ms.openlocfilehash: e596af3c46849313d813ce2d7f1dab2a7425c090
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634523"
---
# <a name="using-server-cursors"></a><span data-ttu-id="2fee5-102">サーバー カーソルの使用</span><span class="sxs-lookup"><span data-stu-id="2fee5-102">Using Server Cursors</span></span>
  <span data-ttu-id="2fee5-103">ODBC アプリケーションで、ODBC カーソルの属性が既定値以外に設定されている場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーは、同じ種類の API サーバーカーソルを実装するようにサーバーに要求します。</span><span class="sxs-lookup"><span data-stu-id="2fee5-103">If an ODBC application sets any of the ODBC cursor attributes to anything other than the defaults, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver requests the server to implement an API server cursor of the same type.</span></span> <span data-ttu-id="2fee5-104">API サーバー カーソルを使用すると、クライアント側のメモリを解放でき、クライアントとサーバー間のネットワーク トラフィックを大幅に削減できます。</span><span class="sxs-lookup"><span data-stu-id="2fee5-104">Using API server cursors frees memory on the client and can significantly reduce network traffic between the client and server.</span></span>  
  
 <span data-ttu-id="2fee5-105">API サーバー カーソルの潜在的な欠点は、現時点では、すべての SQL ステートメントをサポートしているわけではないことです。</span><span class="sxs-lookup"><span data-stu-id="2fee5-105">A potential drawback of API server cursors is that they currently do not support all SQL statements.</span></span> <span data-ttu-id="2fee5-106">次の機能は、API サーバー カーソルでは実行できません。</span><span class="sxs-lookup"><span data-stu-id="2fee5-106">API server cursors cannot be used to execute:</span></span>  
  
-   <span data-ttu-id="2fee5-107">複数の結果セットを返すバッチまたはストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="2fee5-107">Batches or stored procedures that return multiple result sets.</span></span>  
  
-   <span data-ttu-id="2fee5-108">COMPUTE 句、COMPUTE BY 句、FOR BROWSE 句、または INTO 句を伴う SELECT ステートメント</span><span class="sxs-lookup"><span data-stu-id="2fee5-108">SELECT statements that contain COMPUTE, COMPUTE BY, FOR BROWSE, or INTO clauses.</span></span>  
  
-   <span data-ttu-id="2fee5-109">リモート ストアド プロシージャを参照する EXECUTE ステートメント</span><span class="sxs-lookup"><span data-stu-id="2fee5-109">An EXECUTE statement referencing a remote stored procedure.</span></span>  
  
 <span data-ttu-id="2fee5-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続している場合、サーバー カーソルを使用してこのような特性のステートメントを実行すると、カーソルは既定の結果セットに変換されます。</span><span class="sxs-lookup"><span data-stu-id="2fee5-110">When connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], executing a statement with these characteristics using a server cursor causes the cursor being converted to a default result set.</span></span> <span data-ttu-id="2fee5-111">以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に接続している場合は、エラーになります。</span><span class="sxs-lookup"><span data-stu-id="2fee5-111">When connected to earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], it causes an error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fee5-112">参照</span><span class="sxs-lookup"><span data-stu-id="2fee5-112">See Also</span></span>  
 [<span data-ttu-id="2fee5-113">カーソルの実装方法</span><span class="sxs-lookup"><span data-stu-id="2fee5-113">How Cursors Are Implemented</span></span>](how-cursors-are-implemented.md)  
  
  
