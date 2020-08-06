---
title: IMultipleResults を使用した複数の結果セットの処理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- IMultipleResults interface
- multiple-rowset results
ms.assetid: 754d3f30-7d94-4b67-8dac-baf2699ce9c6
author: rothja
ms.author: jroth
ms.openlocfilehash: c7acac7e6ce75189e522b503707e101c0a13c345
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740885"
---
# <a name="using-imultipleresults-to-process-multiple-result-sets"></a><span data-ttu-id="b4f44-102">IMultipleResults を使用した複数の結果セットの処理</span><span class="sxs-lookup"><span data-stu-id="b4f44-102">Using IMultipleResults to Process Multiple Result Sets</span></span>
  <span data-ttu-id="b4f44-103">コンシューマーは、 **IMultipleResults**インターフェイスを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコマンド実行によって返される結果を処理します。</span><span class="sxs-lookup"><span data-stu-id="b4f44-103">Consumers use the **IMultipleResults** interface to process results returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider command execution.</span></span> <span data-ttu-id="b4f44-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーが実行するコマンドを送信すると、は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ステートメントを実行し、結果を返します。</span><span class="sxs-lookup"><span data-stu-id="b4f44-104">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider submits a command for execution, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executes the statements and returns any results.</span></span>  
  
 <span data-ttu-id="b4f44-105">クライアントはコマンドの実行結果をすべて処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4f44-105">A client must process all results from command execution.</span></span> <span data-ttu-id="b4f44-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーコマンドを実行すると、複数行セットオブジェクトが結果として生成される可能性があるため、 **IMultipleResults**インターフェイスを使用して、アプリケーションデータの取得がクライアントによって開始されるラウンドトリップを完了するようにします。</span><span class="sxs-lookup"><span data-stu-id="b4f44-106">Because the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider command execution can generate multiple-rowset objects as results, use the **IMultipleResults** interface to ensure that application data retrieval completes the client-initiated round trip.</span></span>  
  
 <span data-ttu-id="b4f44-107">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行すると複数の行セットが生成されます。行セットには、**OrderDetails** テーブルの行データを含むものや、COMPUTE BY 句の結果を含むものがあります。</span><span class="sxs-lookup"><span data-stu-id="b4f44-107">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement generates multiple rowsets, some containing row data from the **OrderDetails** table and some containing results of the COMPUTE BY clause:</span></span>  
  
```  
SELECT OrderID, FullPrice = (UnitPrice * Quantity), Discount,  
    Discounted = UnitPrice * (1 - Discount) * Quantity  
FROM OrderDetails  
ORDER BY OrderID  
COMPUTE  
    SUM(UnitPrice * Quantity), SUM(UnitPrice * (1 - Discount) * Quantity)  
    BY OrderID  
```  
  
 <span data-ttu-id="b4f44-108">このテキストを含んだコマンドを実行し、返される結果のインターフェイスとして行セットを要求した場合、最初の行セットのみが返されます。</span><span class="sxs-lookup"><span data-stu-id="b4f44-108">If a consumer executes a command containing this text and requests a rowset as the returned results interface, only the first set of rows is returned.</span></span> <span data-ttu-id="b4f44-109">コンシューマーでは、返された行セットのすべての行を処理できます。</span><span class="sxs-lookup"><span data-stu-id="b4f44-109">The consumer may process all rows in the rowset returned.</span></span> <span data-ttu-id="b4f44-110">ただし、DBPROP_MULTIPLECONNECTIONS データソースプロパティが VARIANT_FALSE に設定されていて、その接続で MARS が有効になっていない場合は、コマンドが取り消されるまで、他のコマンドをセッションオブジェクトに対して実行することはできません ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは別の接続を作成しません)。</span><span class="sxs-lookup"><span data-stu-id="b4f44-110">But, if the DBPROP_MULTIPLECONNECTIONS data source property is set to VARIANT_FALSE, and MARS is not enabled on the connection, no other commands can be executed on the session object (the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider will not create another connection) until the command is canceled.</span></span> <span data-ttu-id="b4f44-111">MARS が接続で有効になっていない場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは DBPROP_MULTIPLECONNECTIONS が VARIANT_FALSE 場合に DB_E_OBJECTOPEN エラーを返し、アクティブなトランザクションがある場合は E_FAIL を返します。</span><span class="sxs-lookup"><span data-stu-id="b4f44-111">If MARS is not enabled on the connection, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns a DB_E_OBJECTOPEN error if DBPROP_MULTIPLECONNECTIONS is VARIANT_FALSE and returns E_FAIL if there is an active transaction.</span></span>  
  
 <span data-ttu-id="b4f44-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]また、 **IMultipleResults:: GetResults**を呼び出して次の結果セットを取得する前に、ストリーム出力パラメーターを使用していて、アプリケーションが返された出力パラメーター値をすべて使用していない場合は、Native Client OLE DB プロバイダーからも DB_E_OBJECTOPEN が返されます。</span><span class="sxs-lookup"><span data-stu-id="b4f44-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider will also return DB_E_OBJECTOPEN when using streamed output parameters and the application has not consumed all the returned output parameter values before calling **IMultipleResults::GetResults** to get the next result set.</span></span> <span data-ttu-id="b4f44-113">MARS が有効になっておらず、サーバーカーソルではない行セットを生成するコマンドを実行しているときに、接続がビジー状態になっていて、DBPROP_MULTIPLECONNECTIONS データソースプロパティが VARIANT_TRUE に設定されている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、同時実行コマンドオブジェクトをサポートするために追加の接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="b4f44-113">If MARS is not enabled and the connection is busy running a command that does not produce a rowset or that produces a rowset that is not a server cursor, and if the DBPROP_MULTIPLECONNECTIONS data source property is set to VARIANT_TRUE, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider creates additional connections to support concurrent command objects, unless a transaction is active, in which case it returns an error.</span></span> <span data-ttu-id="b4f44-114">トランザクションとロックは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって接続ごとに管理されます。</span><span class="sxs-lookup"><span data-stu-id="b4f44-114">Transactions and locking are managed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a per connection basis.</span></span> <span data-ttu-id="b4f44-115">他の接続が作成されている場合でも、個別の接続のコマンドはロックを共有しません。</span><span class="sxs-lookup"><span data-stu-id="b4f44-115">If a second connection is generated, the command on the separate connections does not share locks.</span></span> <span data-ttu-id="b4f44-116">コマンドによって要求された行にロックを設定することで、そのコマンドが別のコマンドによってブロックされないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4f44-116">Care must be taken to ensure that one command does not block another by holding locks on rows requested by the other command.</span></span> <span data-ttu-id="b4f44-117">MARS を有効にしている場合、その接続では複数のコマンドをアクティブにできます。明示的なトランザクションを使用している場合、すべてのコマンドが共通のトランザクションを共有します。</span><span class="sxs-lookup"><span data-stu-id="b4f44-117">If MARS is enabled, multiple commands can be active on the connections and if explicit transactions are being used, the commands all share a common transaction.</span></span>  
  
 <span data-ttu-id="b4f44-118">コマンドを取り消すには、[ISSAbort::Abort](../native-client-ole-db-interfaces/issabort-abort-ole-db.md) を使用するか、コマンド オブジェクトおよび派生行セットのすべての参照を解放します。</span><span class="sxs-lookup"><span data-stu-id="b4f44-118">The consumer can cancel the command either by using [ISSAbort::Abort](../native-client-ole-db-interfaces/issabort-abort-ole-db.md) or by releasing all references held on the command object and the derived rowset.</span></span>  
  
 <span data-ttu-id="b4f44-119">すべてのインスタンスで **IMultipleResults** を使用すると、コマンド実行の結果生成されたすべての行セットをコンシューマーが取得し、コマンド実行を取り消して他のコマンドのためにセッションを解放するタイミングを適切に判断できます。</span><span class="sxs-lookup"><span data-stu-id="b4f44-119">Using **IMultipleResults** in all instances allows the consumer to get all rowsets generated by command execution and allows consumers to appropriately determine when to cancel command execution and free a session object for use by other commands.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4f44-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] カーソルを使用するときは、コマンドを実行するとカーソルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b4f44-120">When you use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors, command execution creates the cursor.</span></span> <span data-ttu-id="b4f44-121">カーソルを作成するときに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は成功か失敗を返します。したがって、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへのラウンド トリップが完了するのはコマンドを実行した結果が返ってきたときです。</span><span class="sxs-lookup"><span data-stu-id="b4f44-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] returns success or failure on the cursor creation; therefore, the round trip to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is complete upon the return from command execution.</span></span> <span data-ttu-id="b4f44-122">その後、**GetNextRows** 呼び出しはそれぞれがラウンド トリップになります。</span><span class="sxs-lookup"><span data-stu-id="b4f44-122">Each **GetNextRows** call then becomes a round trip.</span></span> <span data-ttu-id="b4f44-123">このようなしくみによって、サーバー カーソルからのフェッチの結果である行セットを処理する、複数のアクティブなコマンド オブジェクトが存在できます。</span><span class="sxs-lookup"><span data-stu-id="b4f44-123">In this way, multiple active command objects can exist, each processing a rowset that is the result of a fetch from the server cursor.</span></span> <span data-ttu-id="b4f44-124">詳細については、「[行セットと SQL Server カーソル](../native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4f44-124">For more information, see [Rowsets and SQL Server Cursors](../native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4f44-125">参照</span><span class="sxs-lookup"><span data-stu-id="b4f44-125">See Also</span></span>  
 [<span data-ttu-id="b4f44-126">コマンド</span><span class="sxs-lookup"><span data-stu-id="b4f44-126">Commands</span></span>](commands.md)  
  
  
