---
title: 複数行セットの結果を生成するコマンド | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- SQL Server Native Client OLE DB provider, commands
- SQL Server Native Client OLE DB provider, multiple rowsets
- commands [OLE DB]
- multiple-rowset results
ms.assetid: 4567668d-35fd-4162-b61f-f7536862cdcb
author: rothja
ms.author: jroth
ms.openlocfilehash: 8b42a89c0b043e4c72e8b5634cf70e16b435167a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711913"
---
# <a name="commands-generating-multiple-rowset-results"></a><span data-ttu-id="c01c5-102">複数行セットの結果を生成するコマンド</span><span class="sxs-lookup"><span data-stu-id="c01c5-102">Commands Generating Multiple-Rowset Results</span></span>
  <span data-ttu-id="c01c5-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、ステートメントから複数の行セットを返すことができ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="c01c5-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider can return multiple rowsets from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] statements.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c01c5-104">のステートメントは、次の条件が満たされた場合に複数行セットの結果を返します。</span><span class="sxs-lookup"><span data-stu-id="c01c5-104">statements return multiple-rowset results under the following conditions:</span></span>  
  
-   <span data-ttu-id="c01c5-105">バッチにまとめられた SQL ステートメントが 1 つのコマンドとして実行される場合。</span><span class="sxs-lookup"><span data-stu-id="c01c5-105">Batched SQL statements are submitted as a single command.</span></span>  
  
-   <span data-ttu-id="c01c5-106">ストアド プロシージャが SQL ステートメントのバッチを実装している場合。</span><span class="sxs-lookup"><span data-stu-id="c01c5-106">Stored procedures implement a batch of SQL statements.</span></span>  
  
## <a name="batches"></a><span data-ttu-id="c01c5-107">バッチ</span><span class="sxs-lookup"><span data-stu-id="c01c5-107">Batches</span></span>  
 <span data-ttu-id="c01c5-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、SQL ステートメントのバッチ区切り記号としてセミコロン文字を認識します。</span><span class="sxs-lookup"><span data-stu-id="c01c5-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider recognizes the semicolon character as a batch delimiter for SQL statements:</span></span>  
  
```  
WCHAR*       wSQLString = L"SELECT * FROM Categories; "  
                          L"SELECT * FROM Products";  
```  
  
 <span data-ttu-id="c01c5-109">複数の SQL ステートメントを 1 つのバッチにまとめて送信する方が、各 SQL ステートメントを個別に実行するよりも効率的です。</span><span class="sxs-lookup"><span data-stu-id="c01c5-109">Sending multiple SQL statements in one batch is more efficient than executing each SQL statement separately.</span></span> <span data-ttu-id="c01c5-110">1 つのバッチを送信することで、クライアントからサーバーへのネットワーク ラウンド トリップが減少するためです。</span><span class="sxs-lookup"><span data-stu-id="c01c5-110">Sending one batch reduces the network round trips from the client to the server.</span></span>  
  
## <a name="stored-procedures"></a><span data-ttu-id="c01c5-111">ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="c01c5-111">Stored Procedures</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c01c5-112">は、ストアド プロシージャ内のステートメントごとに結果セットを返します。このため、大半の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャは複数の結果セットを返します。</span><span class="sxs-lookup"><span data-stu-id="c01c5-112">returns a result set for each statement in a stored procedure, so most [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures return multiple result sets.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c01c5-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c01c5-113">In This Section</span></span>  
  
-   [<span data-ttu-id="c01c5-114">IMultipleResults を使用した複数の結果セットの処理</span><span class="sxs-lookup"><span data-stu-id="c01c5-114">Using IMultipleResults to Process Multiple Result Sets</span></span>](using-imultipleresults-to-process-multiple-result-sets.md)  
  
## <a name="see-also"></a><span data-ttu-id="c01c5-115">参照</span><span class="sxs-lookup"><span data-stu-id="c01c5-115">See Also</span></span>  
 [<span data-ttu-id="c01c5-116">コマンド</span><span class="sxs-lookup"><span data-stu-id="c01c5-116">Commands</span></span>](commands.md)  
  
  
