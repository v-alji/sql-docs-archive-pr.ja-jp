---
title: トランザクションの有効期間 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
author: rothja
ms.author: jroth
ms.openlocfilehash: 8c00050ee323cade7493d44c4c296ba4ce6811e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742294"
---
# <a name="transaction-lifetimes"></a><span data-ttu-id="1df6a-102">トランザクションの有効期間</span><span class="sxs-lookup"><span data-stu-id="1df6a-102">Transaction Lifetimes</span></span>
  <span data-ttu-id="1df6a-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャで開始されるトランザクションとマネージド コードで開始されるトランザクションには重要な違いがあります。CLR (共通言語ランタイム) コードでは、CLR 呼び出しの開始時または終了時にトランザクションの状態を不安定にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="1df6a-103">There is an important difference between transactions started in [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures and those started in managed code: common language runtime (CLR) code cannot unbalance the transaction state on entry or exit of a CLR invocation.</span></span> <span data-ttu-id="1df6a-104">この違いにより、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="1df6a-104">Be aware of the following implications of this difference:</span></span>  
  
-   <span data-ttu-id="1df6a-105">CLR フレーム内部で開始されたトランザクションは、そのフレーム内でコミットまたはロールバックする必要があります。コミットまたはロールバックしなかった場合、そのフレームの終了時に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によりエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="1df6a-105">A transaction started inside a CLR frame must be committed or rolled back, or else [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generates an error when the frame is exited.</span></span>  
  
-   <span data-ttu-id="1df6a-106">CLR コード内部から外部のトランザクションをコミットまたはロールバックすることはできません。</span><span class="sxs-lookup"><span data-stu-id="1df6a-106">An outer transaction cannot be committed or rolled back inside the CLR code.</span></span>  
  
-   <span data-ttu-id="1df6a-107">同じプロシージャ内で開始されていないトランザクションをコミットしようとすると、実行時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="1df6a-107">An attempt to commit a transaction not started in the same procedure causes a run-time error.</span></span>  
  
-   <span data-ttu-id="1df6a-108">同じプロシージャ内で開始されていないトランザクションをロールバックしようとすると、トランザクションが応答を停止します (他の副作用操作が発生するのを防ぐことができます)。</span><span class="sxs-lookup"><span data-stu-id="1df6a-108">An attempt to roll back a transaction not started in the same procedure causes the transaction to stop responding (preventing any other side-effecting operation from happening).</span></span> <span data-ttu-id="1df6a-109">トランザクションは、CLR コードがスコープ外になるまで再開されません。</span><span class="sxs-lookup"><span data-stu-id="1df6a-109">The transaction discontinues until the CLR code goes out of scope.</span></span> <span data-ttu-id="1df6a-110">この動作は、プロシージャ内部でエラーを検出したときに、トランザクション全体を終了することが望ましい場合に役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="1df6a-110">Note that this can be useful when you detect an error inside your procedure and want to make sure the whole transaction terminates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1df6a-111">参照</span><span class="sxs-lookup"><span data-stu-id="1df6a-111">See Also</span></span>  
 [<span data-ttu-id="1df6a-112">CLR 統合とトランザクション</span><span class="sxs-lookup"><span data-stu-id="1df6a-112">CLR Integration and Transactions</span></span>](../native-client-ole-db-transactions/transactions.md)  
  
  
