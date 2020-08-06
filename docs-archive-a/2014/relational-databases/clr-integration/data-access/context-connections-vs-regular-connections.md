---
title: 標準接続とコンテキスト接続 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: a1dead02-be88-4b16-8cb2-db1284856764
author: rothja
ms.author: jroth
ms.openlocfilehash: ce531129099a8f4908bdc4b29920696d4ba3c505
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645666"
---
# <a name="regular-vs-context-connections"></a><span data-ttu-id="8e059-102">通常の接続とコンテキスト接続</span><span class="sxs-lookup"><span data-stu-id="8e059-102">Regular vs. Context Connections</span></span>
  <span data-ttu-id="8e059-103">リモート サーバーに接続している場合は、常に、コンテキスト接続ではなく通常の接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="8e059-103">If you are connecting to a remote server, always use regular connections rather than context connections.</span></span> <span data-ttu-id="8e059-104">ストアド プロシージャや関数を実行している同一サーバーに接続する必要がある場合は、ほとんどの場合、コンテキスト接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="8e059-104">If you need to connect to the same server on which the stored procedure or function is running, use the context connection in most cases.</span></span> <span data-ttu-id="8e059-105">コンテキスト接続には、同一のトランザクション領域で実行され、再認証が不要であるなどの利点があります。</span><span class="sxs-lookup"><span data-stu-id="8e059-105">This has benefits such as running in the same transaction space and not having to reauthenticate.</span></span>  
  
 <span data-ttu-id="8e059-106">また、コンテキスト接続を使用すると、通常、パフォーマンスが向上し、リソースの使用が抑えられます。</span><span class="sxs-lookup"><span data-stu-id="8e059-106">Additionally, using the context connection typically results in better performance and less resource usage.</span></span> <span data-ttu-id="8e059-107">コンテキスト接続はインプロセスのみの接続であるため、ネットワークプロトコルとトランスポート層をバイパスして Transact-sql ステートメントを送信し、結果を受け取ることによって、サーバーに直接接続できます。</span><span class="sxs-lookup"><span data-stu-id="8e059-107">The context connection is an in-process-only connection, so it can contact the server "directly" by bypassing the network protocol and transport layers to send Transact-SQL statements and receive results.</span></span> <span data-ttu-id="8e059-108">認証プロセスも同様に迂回されます。</span><span class="sxs-lookup"><span data-stu-id="8e059-108">The authentication process is bypassed, as well.</span></span> <span data-ttu-id="8e059-109">次の図に、`SqlClient` マネージド プロバイダーの主要なコンポーネントと、通常の接続を使用する場合とコンテキスト接続を使用する場合の、さまざまなコンポーネント相互の通信方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8e059-109">The following figure shows the primary components of the `SqlClient` managed provider, as well as how the different components interact with each other when using a regular connection, and when using the context connection.</span></span>  
  
 <span data-ttu-id="8e059-110">![コンテキストと通常の接続のコード パス](../../../database-engine/dev-guide/media/clrintdataaccess.gif "コンテキストと通常の接続のコード パス")</span><span class="sxs-lookup"><span data-stu-id="8e059-110">![Code paths of a context and a regular connnection.](../../../database-engine/dev-guide/media/clrintdataaccess.gif "Code paths of a context and a regular connnection.")</span></span>  
  
 <span data-ttu-id="8e059-111">コンテキスト接続で使用するコード パスは、通常の接続よりも短く、関連するコンポーネントの数も少ないので、サーバーへの要求とサーバーからの結果の取得が通常の接続よりも速くなることが期待できます。</span><span class="sxs-lookup"><span data-stu-id="8e059-111">The context connection follows a shorter code path and involves fewer components, so you can expect requests and results to get to and from the server faster than in a regular connection.</span></span> <span data-ttu-id="8e059-112">サーバーでのクエリの実行時間は、どちらの接続でも同じです。</span><span class="sxs-lookup"><span data-stu-id="8e059-112">Query execution time on the server is the same for context and regular connections.</span></span>  
  
 <span data-ttu-id="8e059-113">同じサーバーに対して通常の接続を別に開く必要が生じる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="8e059-113">There are some cases in which you may need to open a separate regular connection to the same server.</span></span> <span data-ttu-id="8e059-114">たとえば、コンテキスト接続の使用には、[通常の接続とコンテキスト接続に関する制限](context-connections-and-regular-connections-restrictions.md)事項で説明されているような制限があります。</span><span class="sxs-lookup"><span data-stu-id="8e059-114">For example, there are certain restrictions on using the context connection, described in [Restrictions on Regular and Context Connections](context-connections-and-regular-connections-restrictions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e059-115">参照</span><span class="sxs-lookup"><span data-stu-id="8e059-115">See Also</span></span>  
 [<span data-ttu-id="8e059-116">コンテキスト接続</span><span class="sxs-lookup"><span data-stu-id="8e059-116">Context Connection</span></span>](context-connection.md)  
  
  
