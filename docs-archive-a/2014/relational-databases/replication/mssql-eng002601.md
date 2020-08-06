---
title: MSSQL_ENG002601 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG002601 error
ms.assetid: 657c3ae6-9e4b-4c60-becc-4caf7435c1dc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c2e8340fef83749fd6d041af42566b10ed3542c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740833"
---
# <a name="mssql_eng002601"></a><span data-ttu-id="c30ac-102">MSSQL_ENG002601</span><span class="sxs-lookup"><span data-stu-id="c30ac-102">MSSQL_ENG002601</span></span>
    
## <a name="message-details"></a><span data-ttu-id="c30ac-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="c30ac-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c30ac-104">製品名</span><span class="sxs-lookup"><span data-stu-id="c30ac-104">Product Name</span></span>|<span data-ttu-id="c30ac-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c30ac-105">SQL Server</span></span>|  
|<span data-ttu-id="c30ac-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="c30ac-106">Event ID</span></span>|<span data-ttu-id="c30ac-107">2601</span><span class="sxs-lookup"><span data-stu-id="c30ac-107">2601</span></span>|  
|<span data-ttu-id="c30ac-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="c30ac-108">Event Source</span></span>|<span data-ttu-id="c30ac-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c30ac-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c30ac-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c30ac-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="c30ac-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="c30ac-111">Symbolic Name</span></span>|<span data-ttu-id="c30ac-112">該当なし</span><span class="sxs-lookup"><span data-stu-id="c30ac-112">N/A</span></span>|  
|<span data-ttu-id="c30ac-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="c30ac-113">Message Text</span></span>|<span data-ttu-id="c30ac-114">一意インデックス '%.\*ls' を含むオブジェクト '%.\*ls' には重複するキー行を挿入できません。</span><span class="sxs-lookup"><span data-stu-id="c30ac-114">Cannot insert duplicate key row in object '%.\*ls' with unique index '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c30ac-115">説明</span><span class="sxs-lookup"><span data-stu-id="c30ac-115">Explanation</span></span>  
 <span data-ttu-id="c30ac-116">このエラーは、データベースがレプリケートされたかどうかにかかわらず発生する一般エラーです。</span><span class="sxs-lookup"><span data-stu-id="c30ac-116">This is a general error that can be raised regardless of whether a database is replicated.</span></span> <span data-ttu-id="c30ac-117">レプリケートされたデータベースでは、このエラーは、一般に主キーがトポロジ間で適切に管理されなかった場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="c30ac-117">In replicated databases, the error is typically raised because primary keys have not been managed appropriately across the topology.</span></span> <span data-ttu-id="c30ac-118">分散環境では、主キー列などの一意の列に複数のノードで同じ値が挿入されないようにすることが不可欠です。</span><span class="sxs-lookup"><span data-stu-id="c30ac-118">In a distributed environment it is essential to ensure that the same value is not inserted into a primary key column or any other unique column at more than one node.</span></span> <span data-ttu-id="c30ac-119">以下のような原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="c30ac-119">Possible causes include the following:</span></span>  
  
-   <span data-ttu-id="c30ac-120">行の挿入と更新が複数のノードで行われた。</span><span class="sxs-lookup"><span data-stu-id="c30ac-120">Inserts and updates to a row are occurring at more than one node.</span></span> <span data-ttu-id="c30ac-121">マージ レプリケーションとトランザクション レプリケーションの更新可能なサブスクリプションには、どちらも競合を検出して解決する機能がありますが、それでも行を 1 つのノード上だけで挿入または更新することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="c30ac-121">Merge replication and updatable subscriptions for transactional replication both provide conflict detection and resolution, but it is still preferable to insert or update a given row at only one node.</span></span> <span data-ttu-id="c30ac-122">ピア ツー ピアのトランザクション レプリケーションでは、競合を検出し解決する機能はありません。挿入と更新をパーティション分割する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c30ac-122">Peer-to-peer transactional does not provide conflict detection and resolution; it requires that inserts and updates be partitioned.</span></span>  
  
-   <span data-ttu-id="c30ac-123">読み取り専用のサブスクライバーで行が挿入された。</span><span class="sxs-lookup"><span data-stu-id="c30ac-123">A row was inserted at a Subscriber that should be read-only.</span></span> <span data-ttu-id="c30ac-124">更新可能なサブスクリプションまたはピア ツー ピアのトランザクション レプリケーションを使用していない場合、スナップショット パブリケーションのサブスクライバーは、トランザクション パブリケーションのサブスクライバーと同様に、読み取り専用として扱われる必要があります。</span><span class="sxs-lookup"><span data-stu-id="c30ac-124">Subscribers to snapshot publications should be treated as read-only, as should Subscribers to transactional publications unless updatable subscriptions or peer-to-peer transactional replication is used.</span></span>  
  
-   <span data-ttu-id="c30ac-125">ID 列を持つテーブルが使用されているが、列が正しく管理されていない。</span><span class="sxs-lookup"><span data-stu-id="c30ac-125">A table with an identity column is being used, but the column is not managed appropriately.</span></span>  
  
-   <span data-ttu-id="c30ac-126">マージ レプリケーションで、システム テーブル **MSmerge_contents**への挿入を行った。この場合、"一意なインデックス 'ucl1SycContents' を含むオブジェクト 'MSmerge_contents' には重複するキー列を挿入できません。" のようにエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c30ac-126">In merge replication, this error can also occur during an insert into the system table **MSmerge_contents**; the error raised is similar to: Cannot insert duplicate key row in object 'MSmerge_contents' with unique index 'ucl1SycContents.'</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c30ac-127">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="c30ac-127">User Action</span></span>  
 <span data-ttu-id="c30ac-128">必要なアクションは、エラーが発生した原因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="c30ac-128">The action required depends on the reason the error was raised:</span></span>  
  
-   <span data-ttu-id="c30ac-129">行の挿入と更新が複数のノードで行われた。</span><span class="sxs-lookup"><span data-stu-id="c30ac-129">Inserts and updates to a row are occurring at more than one node.</span></span>  
  
     <span data-ttu-id="c30ac-130">使用するレプリケーションの種類にかかわらず、できる限り挿入と更新をパーティション分割することをお勧めします。これにより、競合の検出と対処に必要な処理を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="c30ac-130">Regardless of the type of replication used, we recommend that you partition inserts and updates whenever possible, because this reduces the processing required for conflict detection and resolution.</span></span> <span data-ttu-id="c30ac-131">ピア ツー ピアのトランザクション レプリケーションの場合は、挿入と更新のパーティション分割は必須です。</span><span class="sxs-lookup"><span data-stu-id="c30ac-131">For peer-to-peer transactional replication, partitioning inserts and updates is required.</span></span> <span data-ttu-id="c30ac-132">詳細については、「[ピア ツー ピア トランザクション レプリケーション](transactional/peer-to-peer-transactional-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c30ac-132">For more information, see [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md).</span></span>  
  
-   <span data-ttu-id="c30ac-133">読み取り専用のサブスクライバーで行が挿入された。</span><span class="sxs-lookup"><span data-stu-id="c30ac-133">A row was inserted at a Subscriber that should be read-only.</span></span>  
  
     <span data-ttu-id="c30ac-134">マージ レプリケーション、更新可能なサブスクリプションを使用したトランザクション レプリケーション、またはピア ツー ピアのトランザクション レプリケーションを使用していない場合は、サブスクライバーで行を挿入または更新しないでください。</span><span class="sxs-lookup"><span data-stu-id="c30ac-134">Do not insert or update rows at the Subscriber unless you are using merge replication, transactional replication with updatable subscriptions, or peer-to-peer transactional replication.</span></span>  
  
-   <span data-ttu-id="c30ac-135">ID 列を持つテーブルが使用されているが、列が正しく管理されていない。</span><span class="sxs-lookup"><span data-stu-id="c30ac-135">A table with an identity column is being used, but the column is not managed appropriately.</span></span>  
  
     <span data-ttu-id="c30ac-136">マージ レプリケーションおよび更新可能なサブスクリプションを使用したトランザクション レプリケーションの場合は、ID 列はレプリケーションで自動的に管理してください。</span><span class="sxs-lookup"><span data-stu-id="c30ac-136">For merge replication and transactional replication with updatable subscriptions, identity columns should be managed automatically by replication.</span></span> <span data-ttu-id="c30ac-137">ピア ツー ピアのトランザクション レプリケーションの場合は、手動で管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c30ac-137">For peer-to-peer transactional replication, they must be managed manually.</span></span> <span data-ttu-id="c30ac-138">詳細については、「[Replicate Identity Columns](publish/replicate-identity-columns.md)」 (ID 列のレプリケート) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c30ac-138">For more information, see [Replicate Identity Columns](publish/replicate-identity-columns.md).</span></span>  
  
-   <span data-ttu-id="c30ac-139">システム テーブル **MSmerge_contents**への挿入時にエラーが発生する。</span><span class="sxs-lookup"><span data-stu-id="c30ac-139">The error occurs during an insert into the system table **MSmerge_contents**.</span></span>  
  
     <span data-ttu-id="c30ac-140">このエラーは、結合フィルター プロパティ **join_unique_key**の値が不適切なために発生します。</span><span class="sxs-lookup"><span data-stu-id="c30ac-140">This error can occur because of an incorrect value for the join filter property **join_unique_key**.</span></span> <span data-ttu-id="c30ac-141">このプロパティは、親テーブルの結合列が一意である場合にのみ、TRUE に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c30ac-141">This property should be set to TRUE only if the joined column in the parent table is unique.</span></span> <span data-ttu-id="c30ac-142">このプロパティが TRUE に設定されているにもかかわらず、結合列が一意でない場合は、このエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="c30ac-142">If the property is set to TRUE, but the column is not unique, this error is raised.</span></span> <span data-ttu-id="c30ac-143">このプロパティの設定の詳細については、「 [マージ アーティクル間の結合フィルターの定義および変更](publish/define-and-modify-a-join-filter-between-merge-articles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c30ac-143">For more information on setting this property, see [Define and Modify a Join Filter Between Merge Articles](publish/define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c30ac-144">参照</span><span class="sxs-lookup"><span data-stu-id="c30ac-144">See Also</span></span>  
 [<span data-ttu-id="c30ac-145">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="c30ac-145">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
