---
title: MSSQLSERVER_1205 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1205 (Database Engine error)
ms.assetid: 9fe3f67c-df3c-4642-a3a4-ccc0e138b632
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b6afa81a05eea37bc67cd2e9ac2433b6c82f35b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631069"
---
# <a name="mssqlserver_1205"></a><span data-ttu-id="34aef-102">MSSQLSERVER_1205</span><span class="sxs-lookup"><span data-stu-id="34aef-102">MSSQLSERVER_1205</span></span>
    
## <a name="details"></a><span data-ttu-id="34aef-103">詳細</span><span class="sxs-lookup"><span data-stu-id="34aef-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="34aef-104">製品名</span><span class="sxs-lookup"><span data-stu-id="34aef-104">Product Name</span></span>|<span data-ttu-id="34aef-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="34aef-105">SQL Server</span></span>|  
|<span data-ttu-id="34aef-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="34aef-106">Event ID</span></span>|<span data-ttu-id="34aef-107">1205</span><span class="sxs-lookup"><span data-stu-id="34aef-107">1205</span></span>|  
|<span data-ttu-id="34aef-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="34aef-108">Event Source</span></span>|<span data-ttu-id="34aef-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="34aef-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="34aef-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="34aef-110">Component</span></span>|<span data-ttu-id="34aef-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="34aef-111">SQLEngine</span></span>|  
|<span data-ttu-id="34aef-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="34aef-112">Symbolic Name</span></span>|<span data-ttu-id="34aef-113">LK_VICTIM</span><span class="sxs-lookup"><span data-stu-id="34aef-113">LK_VICTIM</span></span>|  
|<span data-ttu-id="34aef-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="34aef-114">Message Text</span></span>|<span data-ttu-id="34aef-115">トランザクション (プロセス ID %d) が、%.\*ls 個のリソースで他のプロセスとデッドロックして、このトランザクションがそのデッドロックの対象となりました。</span><span class="sxs-lookup"><span data-stu-id="34aef-115">Transaction (Process ID %d) was deadlocked on %.\*ls resources with another process and has been chosen as the deadlock victim.</span></span> <span data-ttu-id="34aef-116">トランザクションを再実行してください。</span><span class="sxs-lookup"><span data-stu-id="34aef-116">Rerun the transaction.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="34aef-117">説明</span><span class="sxs-lookup"><span data-stu-id="34aef-117">Explanation</span></span>  
 <span data-ttu-id="34aef-118">個別のトランザクションで、競合する順序でリソースにアクセスすると、デッドロックが発生します。</span><span class="sxs-lookup"><span data-stu-id="34aef-118">Resources are accessed in conflicting order on separate transactions, causing a deadlock.</span></span> <span data-ttu-id="34aef-119">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="34aef-119">For example:</span></span>  
  
-   <span data-ttu-id="34aef-120">Transaction2 が **Table2.Row2** を更新している間に、Transaction1 が **Table1.Row1** を更新しました。</span><span class="sxs-lookup"><span data-stu-id="34aef-120">Transaction1 updates **Table1.Row1**, while Transaction2 updates **Table2.Row2**.</span></span>  
  
-   <span data-ttu-id="34aef-121">Transaction1 は **Table2.Row2** を更新しようとしましたが、Transaction2 のコミットがまだなので、ブロックされました。</span><span class="sxs-lookup"><span data-stu-id="34aef-121">Transaction1 tries to update **Table2.Row2** but is blocked because Transaction2 has not yet committed.</span></span>  
  
-   <span data-ttu-id="34aef-122">今度は Transaction2 が **Table1.Row1** を更新しようとしましたが、Transaction1 のコミットがまだなので、ブロックされました。</span><span class="sxs-lookup"><span data-stu-id="34aef-122">Transaction2 now tries to update **Table1.Row1** but is blocked because Transaction1 has not committed.</span></span>  
  
-   <span data-ttu-id="34aef-123">Transaction1 が Transaction2 の完了を待機していますが、Transaction2 は Transaction1 の完了を待機しているので、デッドロックが生じました。</span><span class="sxs-lookup"><span data-stu-id="34aef-123">A deadlock occurs because Transaction1 is waiting for Transaction2 to complete, but Transaction2 is waiting for Transaction1 to complete.</span></span>  
  
 <span data-ttu-id="34aef-124">このメッセージは、このデッドロックが検出され、"被害者" として関与しているトランザクションの 1 つが選択されると発行されます。その被害者のトランザクションはロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="34aef-124">The system will detect this deadlock and will choose one of the transactions involved as a 'victim' and will issue this message, rolling back the victim's transaction.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="34aef-125">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="34aef-125">User Action</span></span>  
 <span data-ttu-id="34aef-126">トランザクションを再実行します。</span><span class="sxs-lookup"><span data-stu-id="34aef-126">Execute the transaction again.</span></span> <span data-ttu-id="34aef-127">また、デッドロックを回避できるようにアプリケーションを修正します。</span><span class="sxs-lookup"><span data-stu-id="34aef-127">You can also revise the application to avoid deadlocks.</span></span> <span data-ttu-id="34aef-128">デッドロック対象として選択されたトランザクションは、再試行が可能です。同時に実行されている操作によって状況が異なりますが、再試行は成功する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="34aef-128">The transaction that was chosen as a victim can be retried and will likely succeed, depending on what operations are being executed simultaneously.</span></span>  
  
 <span data-ttu-id="34aef-129">デッドロックを回避するには、すべてのトランザクションから行に対するアクセスが、同じ順序 (**Table1** の次に **Table2** など) で行われるようにすることを検討します。こうすることで、ブロックが発生しても、デッドロックは発生しません。</span><span class="sxs-lookup"><span data-stu-id="34aef-129">To prevent or avoid deadlocks from occurring, consider having all transactions access rows in the same order (**Table1**, then **Table2**); this way, although blocking might occur, a deadlock will not occur.</span></span>  
  
  
