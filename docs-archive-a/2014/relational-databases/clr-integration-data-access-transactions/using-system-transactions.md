---
title: Using system.string |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TransactionScope class
- Dispose method
- System.Transactions namespace
ms.assetid: 79656ce5-ce46-4c5e-9540-cf9869bd774b
author: rothja
ms.author: jroth
ms.openlocfilehash: 277edd75ea0437dc532ed5672e3c7b8a0569af8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742285"
---
# <a name="using-systemtransactions"></a><span data-ttu-id="03905-102">System.Transactions の使用</span><span class="sxs-lookup"><span data-stu-id="03905-102">Using System.Transactions</span></span>
  <span data-ttu-id="03905-103">`System.Transactions` 名前空間では、ADO.NET と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CLR (共通言語ランタイム) 統合に完全に統合される新しいトランザクション フレームワークが提供されます。</span><span class="sxs-lookup"><span data-stu-id="03905-103">The `System.Transactions` namespace provides a transaction framework that is fully integrated with ADO.NET and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] common language runtime (CLR) integration.</span></span> <span data-ttu-id="03905-104">`System.Transactions.TransactionScope` クラスでは、接続を分散トランザクションに暗黙的に参加させることで、コード ブロックがトランザクションのコード ブロックになります。</span><span class="sxs-lookup"><span data-stu-id="03905-104">The `System.Transactions.TransactionScope` class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="03905-105">`Complete` でマークされたコード ブロックの最後には、`TransactionScope` メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="03905-105">You must call the `Complete` method at the end of the code block marked by the `TransactionScope`.</span></span> <span data-ttu-id="03905-106">プログラムの実行がコード ブロックから離れる際には `Dispose` メソッドが呼び出され、このとき `Complete` メソッドが呼び出されなければ、トランザクションの続行が中止されます。</span><span class="sxs-lookup"><span data-stu-id="03905-106">The `Dispose` method is invoked when program execution leaves a code block, causing the transaction to be discontinued if the `Complete` method is not called.</span></span> <span data-ttu-id="03905-107">コードがスコープから離れるような例外がスローされると、このトランザクションは中止されたと見なされます。</span><span class="sxs-lookup"><span data-stu-id="03905-107">If an exception has been thrown that causes the code to leave scope, the transaction is considered to be discontinued.</span></span>  
  
 <span data-ttu-id="03905-108">`using` ブロックを使用することで、`Dispose` オブジェクトで `TransactionScope` ブロックの終了時に必ず `using` メソッドを呼び出すようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="03905-108">We recommend that you employ a `using` block to ensure that the `Dispose` method is called on the `TransactionScope` object when the `using` block is exited.</span></span> <span data-ttu-id="03905-109">`TransactionScope` の既定のタイムアウトは 1 分なので、保留中のトランザクションのコミットまたはロールバックに失敗すると、パフォーマンスが大幅に低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="03905-109">Failure to commit or roll back pending transactions can seriously degrade performance because the default time-out for the `TransactionScope` is one minute.</span></span> <span data-ttu-id="03905-110">`using` ステートメントを使用しない場合は、すべての処理を `Try` ブロックで実行し、 `Dispose` メソッドを `Finally` ブロック内で明示的に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="03905-110">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the `Dispose` method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="03905-111">`TransactionScope` 内で例外が発生すると、トランザクションには一貫性がないことを示すマークが付けられ、破棄されます。</span><span class="sxs-lookup"><span data-stu-id="03905-111">If an exception occurs within the `TransactionScope`, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="03905-112">`TransactionScope` が破棄されると、トランザクションはロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="03905-112">It is rolled back when the `TransactionScope` is disposed.</span></span> <span data-ttu-id="03905-113">例外が発生しない場合は、参加しているトランザクションがコミットされます。</span><span class="sxs-lookup"><span data-stu-id="03905-113">If no exception occurs, participating transactions commit.</span></span>  
  
 <span data-ttu-id="03905-114">`TransactionScope` は、ローカルおよびリモート データ ソース、または外部リソース マネージャーにアクセスするときのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="03905-114">`TransactionScope` should be used only when local and remote data sources or external resource managers are being accessed.</span></span> <span data-ttu-id="03905-115">これは、`TransactionScope` が常にトランザクションを昇格してしまうからです。コンテキスト接続内のみで使用した場合でさえ、そのようになります。</span><span class="sxs-lookup"><span data-stu-id="03905-115">This is because `TransactionScope` always causes transactions to promote, even if it is being used only within a context connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="03905-116">既定では、 `TransactionScope` クラスは、 `System.Transactions.Transaction.IsolationLevel` が `Serializable` であるトランザクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="03905-116">The `TransactionScope` class creates a transaction with a `System.Transactions.Transaction.IsolationLevel` of `Serializable` by default.</span></span> <span data-ttu-id="03905-117">使用しているアプリケーションによっては、アプリケーション内での競合を回避するために、分離レベルを低下させる必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="03905-117">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="03905-118">リモート サーバーに対する分散トランザクション内では、大量のデータベース リソースが消費されるため、更新、挿入、および削除だけを実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="03905-118">We recommend that you perform only updates, inserts, and deletes within distributed transactions against remote servers because they consume significant database resources.</span></span> <span data-ttu-id="03905-119">操作がローカル サーバーで実行される場合は、分散トランザクションは必要なく、ローカル トランザクションで十分です。</span><span class="sxs-lookup"><span data-stu-id="03905-119">If the operation is going to be performed on the local server, a distributed transaction is not necessary and a local transaction will suffice.</span></span> <span data-ttu-id="03905-120">SELECT ステートメントは、不必要にデータベース リソースをロックすることがあります。また、選択に多くのトランザクションを要する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="03905-120">SELECT statements may lock database resources unnecessarily, and in some scenarios it may be necessary to use transactions for selects.</span></span> <span data-ttu-id="03905-121">データベース以外の作業は、トランザクション処理を行う他のリソース マネージャーを必要とする場合を除き、トランザクションのスコープ外で行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="03905-121">Any non-database work should be done outside of the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="03905-122">トランザクションのスコープ内で例外が発生するとトランザクションのコミットは回避されますが、`TransactionScope` クラスには、トランザクションのスコープ外でユーザー コードによって行われた変更をロールバックする機能はありません。</span><span class="sxs-lookup"><span data-stu-id="03905-122">Although an exception within the scope of the transaction prevents the transaction from committing, the `TransactionScope` class has no provision for rolling back any changes your code has made outside of the scope of the transaction itself.</span></span> <span data-ttu-id="03905-123">トランザクションのロールバック時に操作が必要である場合は、`System.Transactions.IEnlistmentNotification` インターフェイスの独自の実装を作成し、明示的にトランザクションに参加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03905-123">If you need to take some action when the transaction is rolled back, you must write your own implementation of the `System.Transactions.IEnlistmentNotification` interface, and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03905-124">例</span><span class="sxs-lookup"><span data-stu-id="03905-124">Example</span></span>  
 <span data-ttu-id="03905-125">`System.Transactions` を使用するには、System.Transactions.dll ファイルへの参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="03905-125">To work with `System.Transactions`, you must have a reference to the System.Transactions.dll file.</span></span>  
  
 <span data-ttu-id="03905-126">次のコードでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 2 つの異なるインスタンスに対して昇格可能なトランザクションを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="03905-126">The following code demonstrates how to create a transaction that can be promoted against two different instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="03905-127">これらのインスタンスは、2 つの異なる `System.Data.SqlClient.SqlConnection` オブジェクトで表され、`TransactionScope` ブロックにラップされます。</span><span class="sxs-lookup"><span data-stu-id="03905-127">These instances are represented by two different `System.Data.SqlClient.SqlConnection` objects, which are wrapped in a `TransactionScope` block.</span></span> <span data-ttu-id="03905-128">このコードでは、`TransactionScope` ステートメントを使用して `using` ブロックを作成し、最初の接続を開きます。これにより、トランザクションは `TransactionScope` に自動参加します。</span><span class="sxs-lookup"><span data-stu-id="03905-128">The code creates the `TransactionScope` block with a `using` statement, and opens the first connection, which automatically enlists it in the `TransactionScope`.</span></span> <span data-ttu-id="03905-129">このトランザクションは、完全な分散トランザクションとしてではなく、最初に軽量のトランザクションとして参加します。</span><span class="sxs-lookup"><span data-stu-id="03905-129">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="03905-130">このコードでは、条件ロジックが存在することを前提としています (説明を簡単にするために、このロジックは省略しています)。</span><span class="sxs-lookup"><span data-stu-id="03905-130">The code assumes the existence of conditional logic (which has been omitted for brevity).</span></span> <span data-ttu-id="03905-131">必要な場合のみ 2 番目の接続を開き、`TransactionScope` に参加させます。</span><span class="sxs-lookup"><span data-stu-id="03905-131">It opens the second connection only if it is needed, enlisting it in the `TransactionScope`.</span></span> <span data-ttu-id="03905-132">2 番目の接続が開かれると、トランザクションは完全な分散トランザクションに自動的に昇格します。</span><span class="sxs-lookup"><span data-stu-id="03905-132">When the connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="03905-133">その後、`TransactionScope.Complete` を呼び出し、トランザクションをコミットします。</span><span class="sxs-lookup"><span data-stu-id="03905-133">The code then invokes `TransactionScope.Complete`, which commits the transaction.</span></span> <span data-ttu-id="03905-134">その接続の `using` ステートメントが終了すると、2 つの接続が破棄されます。</span><span class="sxs-lookup"><span data-stu-id="03905-134">The code disposes of the two connections when exiting the `using` statements for the connections.</span></span> <span data-ttu-id="03905-135">`TransactionScope.Dispose` の `TransactionScope` メソッドは、その `using` での `TransactionScope` ブロックの終了時に自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="03905-135">The `TransactionScope.Dispose` method for the `TransactionScope` is automatically called at the termination of the `using` block for the `TransactionScope`.</span></span> <span data-ttu-id="03905-136">`TransactionScope` ブロックのどこかで例外がスローされた場合は、`Complete` が呼び出されません。また、分散トランザクションは、`TransactionScope` が破棄される際にロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="03905-136">If an exception has been thrown at any point in the `TransactionScope` block, `Complete` does not get called, and the distributed transaction will roll back when the `TransactionScope` is disposed.</span></span>  
  
 <span data-ttu-id="03905-137">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="03905-137">Visual Basic</span></span>  
  
```  
Using transScope As New TransactionScope()  
    Using connection1 As New SqlConnection(connectString1)  
        ' Opening connection1 automatically enlists it in the   
        ' TransactionScope as a lightweight transaction.  
        connection1.Open()  
  
        ' Do work in the first connection.  
  
        ' Assumes conditional logic in place where the second  
        ' connection will only be opened as needed.  
        Using connection2 As New SqlConnection(connectString2)  
            ' Open the second connection, which enlists the   
            ' second connection and promotes the transaction to  
            ' a full distributed transaction.  
            connection2.Open()  
  
            ' Do work in the second connection.  
  
        End Using  
    End Using  
  
    ' Commit the transaction.  
    transScope.Complete()  
End Using  
```  
  
 <span data-ttu-id="03905-138">C#</span><span class="sxs-lookup"><span data-stu-id="03905-138">C#</span></span>  
  
```  
using (TransactionScope transScope = new TransactionScope())  
{  
    using (SqlConnection connection1 = new   
       SqlConnection(connectString1))  
    {  
        // Opening connection1 automatically enlists it in the   
        // TransactionScope as a lightweight transaction.  
        connection1.Open();  
  
        // Do work in the first connection.  
  
        // Assumes conditional logic in place where the second  
        // connection will only be opened as needed.  
        using (SqlConnection connection2 = new   
            SqlConnection(connectString2))  
        {  
            // Open the second connection, which enlists the   
            // second connection and promotes the transaction to  
            // a full distributed transaction.   
            connection2.Open();  
  
            // Do work in the second connection.  
        }  
    }  
    //  The Complete method commits the transaction.  
    transScope.Complete();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="03905-139">参照</span><span class="sxs-lookup"><span data-stu-id="03905-139">See Also</span></span>  
 [<span data-ttu-id="03905-140">CLR 統合とトランザクション</span><span class="sxs-lookup"><span data-stu-id="03905-140">CLR Integration and Transactions</span></span>](../native-client-ole-db-transactions/transactions.md)  
  
  
