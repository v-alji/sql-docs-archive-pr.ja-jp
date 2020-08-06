---
title: ストアドプロシージャ呼び出しのバッチ化 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], batching
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- batches [ODBC]
- ODBC CALL escape sequence
ms.assetid: b7f53e11-15f0-4602-8134-b166160888f0
author: rothja
ms.author: jroth
ms.openlocfilehash: a0df58ce59853ee15b863cbc7bce34041c37fee4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741965"
---
# <a name="batching-stored-procedure-calls"></a><span data-ttu-id="3daff-102">ストアド プロシージャ呼び出しのバッチ化</span><span class="sxs-lookup"><span data-stu-id="3daff-102">Batching Stored Procedure Calls</span></span>
  <span data-ttu-id="3daff-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーでは、必要に応じてストアドプロシージャの呼び出しがサーバーに自動的にバッチ処理されます。</span><span class="sxs-lookup"><span data-stu-id="3daff-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver automatically batches stored procedure calls to the server when appropriate.</span></span> <span data-ttu-id="3daff-104">これが行われるのは、ODBC CALL エスケープ シーケンスが使用されている場合のみです。[!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE ステートメントでは、この処理は行われません。</span><span class="sxs-lookup"><span data-stu-id="3daff-104">The driver only does this when the ODBC CALL escape sequence is used; it does not do this for the [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE statement.</span></span> <span data-ttu-id="3daff-105">ストアド プロシージャ呼び出しをバッチにまとめると、サーバーとのやり取りの回数を削減できるので、パフォーマンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="3daff-105">Batching stored procedure calls can reduce the number of round trips to the server and significantly increase performance.</span></span>  
  
 <span data-ttu-id="3daff-106">複数の ODBC CALL エスケープ シーケンスを含むバッチを実行すると、ドライバーによりサーバーへのプロシージャ呼び出しがバッチにまとめられます。</span><span class="sxs-lookup"><span data-stu-id="3daff-106">The driver batches procedure calls to the server when you execute a batch that contains multiple ODBC CALL escape sequences.</span></span> <span data-ttu-id="3daff-107">また、ODBC CALL エスケープ シーケンスでバインドされたパラメーター配列を使用するときも、プロシージャ呼び出しがバッチにまとめられます。</span><span class="sxs-lookup"><span data-stu-id="3daff-107">It also batches procedure calls when bound parameter arrays are used with an ODBC CALL escape sequence.</span></span> <span data-ttu-id="3daff-108">たとえば、行方向または列方向のいずれかのパラメーターバインドを使用して、5つの要素を持つ配列を ODBC CALL SQL ステートメントのパラメーターにバインドする場合、 **Sqlexecute**または**SQLExecDirect**が呼び出されると、ドライバーは5つのプロシージャ呼び出しを含む単一のバッチをサーバーに送信します。</span><span class="sxs-lookup"><span data-stu-id="3daff-108">For example, if you use either row-wise or column-wise parameter binding to bind an array with five elements to the parameters of an ODBC CALL SQL statement, when **SQLExecute** or **SQLExecDirect** is called, the driver sends a single batch with five procedure calls to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3daff-109">参照</span><span class="sxs-lookup"><span data-stu-id="3daff-109">See Also</span></span>  
 [<span data-ttu-id="3daff-110">ストアド プロシージャの実行</span><span class="sxs-lookup"><span data-stu-id="3daff-110">Running Stored Procedures</span></span>](running-stored-procedures.md)  
  
  
