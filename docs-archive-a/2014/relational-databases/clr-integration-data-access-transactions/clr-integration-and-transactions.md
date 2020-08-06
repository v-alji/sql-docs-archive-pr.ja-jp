---
title: CLR 統合とトランザクション |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- managed code [SQL Server], transactions
- common language runtime [SQL Server], transactions
- System.Transactions namespace
- transactions [CLR integration]
ms.assetid: 381d206e-06e2-48d0-8206-295fcf06ac98
author: rothja
ms.author: jroth
ms.openlocfilehash: de72a2113aeb568decbdc9b5ee0174160cc0d3ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742301"
---
# <a name="clr-integration-and-transactions"></a><span data-ttu-id="0d9b9-102">CLR 統合とトランザクション</span><span class="sxs-lookup"><span data-stu-id="0d9b9-102">CLR Integration and Transactions</span></span>
  <span data-ttu-id="0d9b9-103">`System.Transactions` 名前空間では、ADO.NET と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CLR (共通言語ランタイム) 統合に完全に統合される新しいトランザクション フレームワークが提供されます。</span><span class="sxs-lookup"><span data-stu-id="0d9b9-103">The `System.Transactions` namespace provides a transaction framework that is fully integrated with ADO.NET and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] common language runtime (CLR) integration.</span></span> <span data-ttu-id="0d9b9-104">`System.Transactions` と ADO.NET は連携し、マネージド アプリケーションでのローカル トランザクションや分散トランザクションの用途を拡張および単純化します。</span><span class="sxs-lookup"><span data-stu-id="0d9b9-104">`System.Transactions` and ADO.NET work together to extend and simplify the use of local and distributed transactions in managed applications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d9b9-105">CLR ユーザー定義プロシージャ (UDP) は、このプロシージャが実行されているサーバーへの接続 (ループバック接続) を確立して、同じトランザクションに参加することができません。</span><span class="sxs-lookup"><span data-stu-id="0d9b9-105">A CLR user-defined procedure (UDP) cannot establish a connection to the same server it is running on (a loopback connection) and enlist in the same transaction.</span></span> <span data-ttu-id="0d9b9-106">この操作を試みると、接続試行がブロックされ、制御は UDP に返されません。</span><span class="sxs-lookup"><span data-stu-id="0d9b9-106">If this is attempted, the connection attempt will be blocked and control will not be passed back to the UDP.</span></span> <span data-ttu-id="0d9b9-107">これにより、UDP でタイムアウト エラー (メッセージ 1206) が発生します。</span><span class="sxs-lookup"><span data-stu-id="0d9b9-107">This will result in a timeout error (Msg 1206) on the UDP.</span></span>  
  
 <span data-ttu-id="0d9b9-108">トランザクションと .NET Framework の詳細については、.NET Framework SDK の「トランザクションの実行」と「トランザクションの利用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d9b9-108">For more information about transactions and the .NET Framework, see "Performing Transactions" and "Leveraging Transactions" in the .NET Framework SDK.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0d9b9-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="0d9b9-109">In This Section</span></span>  
 [<span data-ttu-id="0d9b9-110">トランザクションの昇格</span><span class="sxs-lookup"><span data-stu-id="0d9b9-110">Transaction Promotion</span></span>](transaction-promotion.md)  
 <span data-ttu-id="0d9b9-111">トランザクションを昇格する機能とこの機能の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0d9b9-111">Describes the ability to promote transactions, and how to use this feature.</span></span>  
  
 [<span data-ttu-id="0d9b9-112">現在のトランザクションへのアクセス</span><span class="sxs-lookup"><span data-stu-id="0d9b9-112">Accessing the Current Transaction</span></span>](accessing-the-current-transaction.md)  
 <span data-ttu-id="0d9b9-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインプロセスで現在実行中のトランザクションにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0d9b9-113">Describes how to access a transaction currently running in-process on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="0d9b9-114">System.Transactions の使用</span><span class="sxs-lookup"><span data-stu-id="0d9b9-114">Using System.Transactions</span></span>](../native-client-ole-db-transactions/transactions.md)  
 <span data-ttu-id="0d9b9-115">マネージド アプリケーションでの `System.Transactions` API (アプリケーション プログラミング インターフェイス) の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0d9b9-115">Describes how to use the `System.Transactions` application programming interface (API) in your managed application.</span></span>  
  
 [<span data-ttu-id="0d9b9-116">トランザクションの有効期間</span><span class="sxs-lookup"><span data-stu-id="0d9b9-116">Transaction Lifetimes</span></span>](transaction-lifetimes.md)  
 <span data-ttu-id="0d9b9-117">[!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャで開始されたトランザクションと、CLR アプリケーションで開始されたトランザクションの有効期間の違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="0d9b9-117">Describes the difference in lifetime between transactions started in [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures and transactions started in CLR applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d9b9-118">参照</span><span class="sxs-lookup"><span data-stu-id="0d9b9-118">See Also</span></span>  
 [<span data-ttu-id="0d9b9-119">CLR データベース オブジェクトからのデータ アクセス</span><span class="sxs-lookup"><span data-stu-id="0d9b9-119">Data Access from CLR Database Objects</span></span>](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
