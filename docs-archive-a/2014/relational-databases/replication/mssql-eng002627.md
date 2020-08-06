---
title: MSSQL_ENG002627 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG002627 error
ms.assetid: 7f4136ac-3784-4a41-a98c-8a02308e4883
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cf481635d6a24570792c9da04fe71ebea885ce5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741802"
---
# <a name="mssql_eng002627"></a><span data-ttu-id="245ef-102">MSSQL_ENG002627</span><span class="sxs-lookup"><span data-stu-id="245ef-102">MSSQL_ENG002627</span></span>
    
## <a name="message-details"></a><span data-ttu-id="245ef-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="245ef-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="245ef-104">製品名</span><span class="sxs-lookup"><span data-stu-id="245ef-104">Product Name</span></span>|<span data-ttu-id="245ef-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="245ef-105">SQL Server</span></span>|  
|<span data-ttu-id="245ef-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="245ef-106">Event ID</span></span>|<span data-ttu-id="245ef-107">2627</span><span class="sxs-lookup"><span data-stu-id="245ef-107">2627</span></span>|  
|<span data-ttu-id="245ef-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="245ef-108">Event Source</span></span>|<span data-ttu-id="245ef-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="245ef-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="245ef-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="245ef-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="245ef-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="245ef-111">Symbolic Name</span></span>|<span data-ttu-id="245ef-112">該当なし</span><span class="sxs-lookup"><span data-stu-id="245ef-112">N/A</span></span>|  
|<span data-ttu-id="245ef-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="245ef-113">Message Text</span></span>|<span data-ttu-id="245ef-114">制約 '%.\*ls' の %ls 違反。</span><span class="sxs-lookup"><span data-stu-id="245ef-114">Violation of %ls constraint '%.\*ls'.</span></span> <span data-ttu-id="245ef-115">オブジェクト '%.\*ls' には重複したキーを挿入できません。") です。</span><span class="sxs-lookup"><span data-stu-id="245ef-115">Cannot insert duplicate key in object '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="245ef-116">説明</span><span class="sxs-lookup"><span data-stu-id="245ef-116">Explanation</span></span>  
 <span data-ttu-id="245ef-117">このエラーは、データベースがレプリケートされたかどうかにかかわらず発生する一般エラーです。</span><span class="sxs-lookup"><span data-stu-id="245ef-117">This is a general error that can be raised regardless of whether a database is replicated.</span></span> <span data-ttu-id="245ef-118">レプリケートされたデータベースでは、このエラーは、一般に主キーがトポロジ間で適切に管理されなかった場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="245ef-118">In replicated databases, the error is typically raised because primary keys have not been managed appropriately across the topology.</span></span> <span data-ttu-id="245ef-119">分散環境では、主キー列などの一意の列に複数のノードで同じ値が挿入されないようにすることが不可欠です。</span><span class="sxs-lookup"><span data-stu-id="245ef-119">In a distributed environment it is essential to ensure that the same value is not inserted into a primary key column or any other unique column at more than one node.</span></span> <span data-ttu-id="245ef-120">以下のような原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="245ef-120">Possible causes include the following:</span></span>  
  
-   <span data-ttu-id="245ef-121">行の挿入と更新が複数のノードで行われた。</span><span class="sxs-lookup"><span data-stu-id="245ef-121">Inserts and updates to a row are occurring at more than one node.</span></span> <span data-ttu-id="245ef-122">マージ レプリケーションとトランザクション レプリケーションの更新可能なサブスクリプションには、どちらも競合を検出して解決する機能がありますが、それでも行を 1 つのノード上だけで挿入または更新することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="245ef-122">Merge replication and updatable subscriptions for transactional replication both provide conflict detection and resolution, but it is still preferable to insert or update a given row at only one node.</span></span> <span data-ttu-id="245ef-123">ピア ツー ピアのトランザクション レプリケーションでは、競合を検出し解決する機能はありません。挿入と更新をパーティション分割する必要があります。</span><span class="sxs-lookup"><span data-stu-id="245ef-123">Peer-to-peer transactional does not provide conflict detection and resolution; it requires that inserts and updates be partitioned.</span></span>  
  
-   <span data-ttu-id="245ef-124">読み取り専用のサブスクライバーで行が挿入された。</span><span class="sxs-lookup"><span data-stu-id="245ef-124">A row was inserted at a Subscriber that should be read-only.</span></span> <span data-ttu-id="245ef-125">更新可能なサブスクリプションまたはピア ツー ピアのトランザクション レプリケーションを使用していない場合、スナップショット パブリケーションのサブスクライバーは、トランザクション パブリケーションのサブスクライバーと同様に、読み取り専用として扱われる必要があります。</span><span class="sxs-lookup"><span data-stu-id="245ef-125">Subscribers to snapshot publications should be treated as read-only, as should Subscribers to transactional publications unless updatable subscriptions or peer-to-peer transactional replication is used.</span></span>  
  
-   <span data-ttu-id="245ef-126">ID 列を持つテーブルが使用されているが、列が正しく管理されていない。</span><span class="sxs-lookup"><span data-stu-id="245ef-126">A table with an identity column is being used, but the column is not managed appropriately.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="245ef-127">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="245ef-127">User Action</span></span>  
 <span data-ttu-id="245ef-128">必要なアクションは、エラーが発生した原因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="245ef-128">The action required depends on the reason the error was raised:</span></span>  
  
-   <span data-ttu-id="245ef-129">行の挿入と更新が複数のノードで行われた。</span><span class="sxs-lookup"><span data-stu-id="245ef-129">Inserts and updates to a row are occurring at more than one node.</span></span>  
  
     <span data-ttu-id="245ef-130">使用するレプリケーションの種類にかかわらず、できる限り挿入と更新をパーティション分割することをお勧めします。これにより、競合の検出と対処に必要な処理を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="245ef-130">Regardless of the type of replication used, we recommend that you partition inserts and updates whenever possible, because this reduces the processing required for conflict detection and resolution.</span></span> <span data-ttu-id="245ef-131">ピア ツー ピアのトランザクション レプリケーションの場合は、挿入と更新のパーティション分割は必須です。</span><span class="sxs-lookup"><span data-stu-id="245ef-131">For peer-to-peer transactional replication, partitioning inserts and updates is required.</span></span> <span data-ttu-id="245ef-132">詳細については、「[ピア ツー ピア トランザクション レプリケーション](transactional/peer-to-peer-transactional-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="245ef-132">For more information, see [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md).</span></span>  
  
-   <span data-ttu-id="245ef-133">読み取り専用のサブスクライバーで行が挿入された。</span><span class="sxs-lookup"><span data-stu-id="245ef-133">A row was inserted at a Subscriber that should be read-only.</span></span>  
  
     <span data-ttu-id="245ef-134">マージ レプリケーション、更新可能なサブスクリプションを使用したトランザクション レプリケーション、またはピア ツー ピアのトランザクション レプリケーションを使用していない場合は、サブスクライバーで行を挿入または更新しないでください。</span><span class="sxs-lookup"><span data-stu-id="245ef-134">Do not insert or update rows at the Subscriber unless you are using merge replication, transactional replication with updatable subscriptions, or peer-to-peer transactional replication.</span></span>  
  
-   <span data-ttu-id="245ef-135">ID 列を持つテーブルが使用されているが、列が正しく管理されていない。</span><span class="sxs-lookup"><span data-stu-id="245ef-135">A table with an identity column is being used, but the column is not managed appropriately.</span></span>  
  
     <span data-ttu-id="245ef-136">マージ レプリケーションおよび更新可能なサブスクリプションを使用したトランザクション レプリケーションの場合は、ID 列はレプリケーションで自動的に管理してください。</span><span class="sxs-lookup"><span data-stu-id="245ef-136">For merge replication and transactional replication with updatable subscriptions, identity columns should be managed automatically by replication.</span></span> <span data-ttu-id="245ef-137">ピア ツー ピアのトランザクション レプリケーションの場合は、手動で管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="245ef-137">For peer-to-peer transactional replication, they must be managed manually.</span></span> <span data-ttu-id="245ef-138">詳細については、「[Replicate Identity Columns](publish/replicate-identity-columns.md)」 (ID 列のレプリケート) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="245ef-138">For more information, see [Replicate Identity Columns](publish/replicate-identity-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="245ef-139">参照</span><span class="sxs-lookup"><span data-stu-id="245ef-139">See Also</span></span>  
 <span data-ttu-id="245ef-140">[エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="245ef-140">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="245ef-141">[マージ レプリケーション](merge/merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="245ef-141">[Merge Replication](merge/merge-replication.md) </span></span>  
 <span data-ttu-id="245ef-142">[Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="245ef-142">[Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md) </span></span>  
 [<span data-ttu-id="245ef-143">Updatable Subscriptions for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="245ef-143">Updatable Subscriptions for Transactional Replication</span></span>](transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
