---
title: ピア ツー ピア トランザクション レプリケーション | Microsoft Docs
ms.custom: ''
ms.date: 08/29/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- bidirectional replication
- transactional replication, bidirectional replication
- bidirectional transactional replication
- transactional replication, peer-to-peer replication
- peer-to-peer transactional replication
ms.assetid: 23e7e8c1-002f-4e69-8c99-d63e4100de64
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f61db9a8e7cecb107fd1b27fae966d133e043c8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641593"
---
# <a name="peer-to-peer-transactional-replication"></a><span data-ttu-id="70f8e-102">@loopback_detection</span><span class="sxs-lookup"><span data-stu-id="70f8e-102">Peer-to-Peer Transactional Replication</span></span>
  <span data-ttu-id="70f8e-103">ピア ツー ピア レプリケーションは、データのコピーを複数のサーバー インスタンス ( *ノード*) で保持することにより、可用性の高いスケールアウト ソリューションを実現します。</span><span class="sxs-lookup"><span data-stu-id="70f8e-103">Peer-to-peer replication provides a scale-out and high-availability solution by maintaining copies of data across multiple server instances, also referred to as *nodes*.</span></span> <span data-ttu-id="70f8e-104">ピア ツー ピア レプリケーションはトランザクション レプリケーションを基礎としており、トランザクション的に一貫性のある変更がほぼリアルタイムで反映されます。</span><span class="sxs-lookup"><span data-stu-id="70f8e-104">Built on the foundation of transactional replication, peer-to-peer replication propagates transactionally consistent changes in near real-time.</span></span> <span data-ttu-id="70f8e-105">これにより、読み取り操作のスケールアウトを必要とするアプリケーションで、クライアントからの読み取りを複数のノードに分散することができます。</span><span class="sxs-lookup"><span data-stu-id="70f8e-105">This enables applications that require scale-out of read operations to distribute the reads from clients across multiple nodes.</span></span> <span data-ttu-id="70f8e-106">また、データがほぼリアルタイムで複数のノードに保持されるため、データの冗長性が実現され、データの可用性が向上します。</span><span class="sxs-lookup"><span data-stu-id="70f8e-106">Because data is maintained across the nodes in near real-time, peer-to-peer replication provides data redundancy, which increases the availability of data.</span></span>  
  
 <span data-ttu-id="70f8e-107">たとえば Web アプリケーションでは、</span><span class="sxs-lookup"><span data-stu-id="70f8e-107">Consider a Web application.</span></span> <span data-ttu-id="70f8e-108">ピア ツー ピア レプリケーションを利用すると次のようなメリットがあります。</span><span class="sxs-lookup"><span data-stu-id="70f8e-108">This can benefit from peer-to-peer replication in the following ways:</span></span>  
  
-   <span data-ttu-id="70f8e-109">カタログのクエリやその他の読み取りが複数のノードに分散されるため、</span><span class="sxs-lookup"><span data-stu-id="70f8e-109">Catalog queries and other reads are spread across multiple nodes.</span></span> <span data-ttu-id="70f8e-110">読み取りが増加してもパフォーマンスを維持できます。</span><span class="sxs-lookup"><span data-stu-id="70f8e-110">This enables performance to remain consistent as reads increase.</span></span>  
  
-   <span data-ttu-id="70f8e-111">システムのいずれかのノードに障害が発生した場合、アプリケーション層でそのノードへの書き込みを別のノードにリダイレクトできるため、</span><span class="sxs-lookup"><span data-stu-id="70f8e-111">If one of the nodes in the system fails, an application layer can redirect the writes for that node to another node.</span></span> <span data-ttu-id="70f8e-112">可用性が維持されます。</span><span class="sxs-lookup"><span data-stu-id="70f8e-112">This maintains availability.</span></span>  
  
-   <span data-ttu-id="70f8e-113">ノードのメンテナンスやシステム全体のアップグレードが必要な場合も、それぞれのノードをオフラインにして再度システムに追加することができるため、アプリケーションの可用性に影響が及ぶことはありません。</span><span class="sxs-lookup"><span data-stu-id="70f8e-113">If a node requires maintenance or the whole system requires an upgrade, each node can be taken offline and added back to the system without affecting the availability of the application.</span></span>  
  
 <span data-ttu-id="70f8e-114">ピア ツー ピア レプリケーションでは、読み取り操作のスケール アウトは実現されますが、トポロジへの書き込みのパフォーマンスは 1 つのノードの場合と変わりません。</span><span class="sxs-lookup"><span data-stu-id="70f8e-114">Although peer-to-peer replication enables scaling out of read operations, write performance for the topology is like that for a single node.</span></span> <span data-ttu-id="70f8e-115">これは、すべての挿入、更新、および削除が、最終的にすべてのノードに反映されるためです。</span><span class="sxs-lookup"><span data-stu-id="70f8e-115">This is because ultimately all inserts, updates, and deletes are propagated to all nodes.</span></span> <span data-ttu-id="70f8e-116">特定のノードに変更が適用されたことをレプリケーションが認識するため、変更がノードを何度も循環することはありません。</span><span class="sxs-lookup"><span data-stu-id="70f8e-116">Replication recognizes when a change has been applied to a given node and prevents changes from cycling through the nodes more than one time.</span></span> <span data-ttu-id="70f8e-117">次のような理由から、各行の書き込み操作は 1 つのノードだけで実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="70f8e-117">We strongly recommend that write operations for each row be performed at only node, for the following reasons:</span></span>  
  
-   <span data-ttu-id="70f8e-118">行が複数のノードで変更されると、他のノードに反映される際に競合が発生したり、場合によっては更新データが失われたりする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="70f8e-118">If a row is modified at more than one node, it can cause a conflict or even a lost update when the row is propagated to other nodes.</span></span>  
  
-   <span data-ttu-id="70f8e-119">変更がレプリケートされるときには常にある程度の遅延が生じます。</span><span class="sxs-lookup"><span data-stu-id="70f8e-119">There is always some latency involved when changes are replicated.</span></span> <span data-ttu-id="70f8e-120">最新の変更が直ちに反映される必要があるアプリケーションでは、複数のノードで動的に負荷を分散すると問題が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="70f8e-120">For applications that require the latest change to be seen immediately, dynamically load balancing the application across multiple nodes can be problematic.</span></span>  
  
 <span data-ttu-id="70f8e-121">ピア ツー ピア レプリケーションには、ピア ツー ピア トポロジの競合の検出を有効にするオプションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="70f8e-121">Peer-to-peer replication includes the option to enable conflict detection across a peer-to-peer topology.</span></span> <span data-ttu-id="70f8e-122">このオプションは、検出されない競合によって引き起こされる問題 (アプリケーションの動作の矛盾や更新データの喪失など) の防止に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="70f8e-122">This option helps prevent the issues that are caused from undetected conflicts, including inconsistent application behavior and lost updates.</span></span> <span data-ttu-id="70f8e-123">このオプションを有効にすると、競合する変更が、ディストリビューション エージェントの障害を引き起こす重大なエラーとして既定で扱われるようになります。</span><span class="sxs-lookup"><span data-stu-id="70f8e-123">By enabling this option, by default a conflicting change is treated as a critical error that causes the failure of the Distribution Agent.</span></span> <span data-ttu-id="70f8e-124">競合が発生した場合は、その競合が手動で解決されて、トポロジでデータの一貫性が確保されるまで、トポロジが一貫性のない状態のままになります。</span><span class="sxs-lookup"><span data-stu-id="70f8e-124">In the event of a conflict, the topology remains in an inconsistent state until the conflict is resolved manually and the data is made consistent across the topology.</span></span> <span data-ttu-id="70f8e-125">詳細については、「 [ピア ツー ピア レプリケーションにおける競合検出](peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70f8e-125">For more information, see [Conflict Detection in Peer-to-Peer Replication](peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70f8e-126">データの不整合が生じないようにするため、競合の検出を有効にしている場合でも、ピア ツー ピア トポロジで競合を発生させないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="70f8e-126">To avoid potential data inconsistency, make sure that you avoid conflicts in a peer-to-peer topology, even with conflict detection enabled.</span></span> <span data-ttu-id="70f8e-127">特定の行の書き込み操作が 1 つのノードだけで行われるようにするには、データにアクセスしてそのデータを変更するアプリケーションで、挿入、更新、および削除の各操作をパーティション分割する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70f8e-127">To ensure that write operations for a particular row are performed at only one node, applications that access and change data must partition insert, update, and delete operations.</span></span> <span data-ttu-id="70f8e-128">これにより、1 つのノードの特定の行に対する変更は、トポロジ内の他のすべてのノードと同期されてから、別のノードでその行が変更されるようになります。</span><span class="sxs-lookup"><span data-stu-id="70f8e-128">This partitioning ensures that modifications to a given row originating at one node are synchronized with all other nodes in the topology before the row is modified by a different node.</span></span> <span data-ttu-id="70f8e-129">競合の検出と解決のための高度な機能がアプリケーションに必要な場合は、マージ レプリケーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="70f8e-129">If an application requires sophisticated conflict detection and resolution capabilities, use merge replication.</span></span> <span data-ttu-id="70f8e-130">詳細については、「[Merge Replication](../merge/merge-replication.md)」 (マージ レプリケーション) と「[マージ レプリケーションの競合の検出と解決](../merge/advanced-merge-replication-conflict-detection-and-resolution.md)」 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70f8e-130">For more information, see [Merge Replication](../merge/merge-replication.md) and [Detect and Resolve Merge Replication Conflicts](../merge/advanced-merge-replication-conflict-detection-and-resolution.md).</span></span>  
  
## <a name="peer-to-peer-topologies"></a><span data-ttu-id="70f8e-131">ピア ツー ピア トポロジ</span><span class="sxs-lookup"><span data-stu-id="70f8e-131">Peer-to-Peer Topologies</span></span>  
 <span data-ttu-id="70f8e-132">次のシナリオは、ピア ツー ピア レプリケーションの典型的な使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="70f8e-132">The following scenarios illustrate typical uses for peer-to-peer replication.</span></span>  
  
### <a name="topology-that-has-two-participating-databases"></a><span data-ttu-id="70f8e-133">2 つの参加データベースがあるトポロジ</span><span class="sxs-lookup"><span data-stu-id="70f8e-133">Topology That Has Two Participating Databases</span></span>  
 <span data-ttu-id="70f8e-134">![2 つのノードによるピア ツー ピア レプリケーション](../media/repl-multinode-01.gif "2 つのノードによるピア ツー ピア レプリケーション")</span><span class="sxs-lookup"><span data-stu-id="70f8e-134">![Peer-to-peer replication, two nodes](../media/repl-multinode-01.gif "Peer-to-peer replication, two nodes")</span></span>  
  
 <span data-ttu-id="70f8e-135">上の図にはいずれも、2 つの参加データベースがあり、ユーザーのトラフィックは、アプリケーション サーバーを通じてデータベースに送信されています。</span><span class="sxs-lookup"><span data-stu-id="70f8e-135">Both of the preceding illustrations show two participating databases, with user traffic directed to the databases through an application server.</span></span> <span data-ttu-id="70f8e-136">この構成は、Web サイトからワークグループ アプリケーションまでさまざまなアプリケーションに使用でき、次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="70f8e-136">This configuration can be used for a variety of applications, from Web sites to workgroup applications, and provides the following benefits:</span></span>  
  
-   <span data-ttu-id="70f8e-137">読み取りが 2 つのサーバーに分散されるため、読み取りのパフォーマンスが向上する。</span><span class="sxs-lookup"><span data-stu-id="70f8e-137">Improved read performance, because reads are spread out over two servers.</span></span>  
  
-   <span data-ttu-id="70f8e-138">1 つのノードでメンテナンスが必要な場合や障害が発生した場合に高い可用性を実現する。</span><span class="sxs-lookup"><span data-stu-id="70f8e-138">Higher availability if maintenance is required or in case of failure at one node.</span></span>  
  
 <span data-ttu-id="70f8e-139">どちらの図でも、読み取り処理の負荷が参加データベース間で分散されていますが、更新の処理は次のように異なっています。</span><span class="sxs-lookup"><span data-stu-id="70f8e-139">In both illustrations, read activity is load-balanced between the participating databases, but updates are handled differently:</span></span>  
  
-   <span data-ttu-id="70f8e-140">左側の図では、更新は 2 つのサーバー間でパーティション分割されています。</span><span class="sxs-lookup"><span data-stu-id="70f8e-140">On the left, updates are partitioned between the two servers.</span></span> <span data-ttu-id="70f8e-141">たとえば、データベースに製品カタログが含まれている場合、カスタム アプリケーションでは、A ～ M で始まる製品名についてはノード **A** に更新を送信し、N ～ Z で始まる製品名についてはノード **B** に更新を送信するようにできます。その後、更新は他のノードにレプリケートされます。</span><span class="sxs-lookup"><span data-stu-id="70f8e-141">If the database contained a product catalog, you could, for example, have a custom application direct updates to node **A** for product names that start with A through M, and direct updates to node **B** for product names that start with N through Z. Updates are then replicated to the other node.</span></span>  
  
-   <span data-ttu-id="70f8e-142">右側の図では、すべての更新がノード **B** に送信されます。そこから、更新はノード **A** にレプリケートされます。**B** がメンテナンスなどの理由でオフラインになると、アプリケーション サーバーはすべての処理を **A** に送信できます。**B** がオンラインに戻ると、更新は B に送られて、アプリケーション サーバーはすべての更新を **B** に移動することも、**A** への送信を維持することもできます。</span><span class="sxs-lookup"><span data-stu-id="70f8e-142">On the right, all updates are directed to node **B**. From there, updates are replicated to node **A**. If **B** is offline (for example, for maintenance), the application server can direct all activity to **A**. When **B** is back online, updates can flow to it, and the application server can move all updates back to **B** or keep directing them to **A**.</span></span>  
  
 <span data-ttu-id="70f8e-143">ピア ツー ピア レプリケーションはどちらの方法もサポートしますが、右側の図にある中央の更新例は、標準トランザクション レプリケーションでも頻繁に使用されます。</span><span class="sxs-lookup"><span data-stu-id="70f8e-143">Peer-to-peer replication can support either approach, but the central update example on the right is also often used with standard transactional replication.</span></span>  
  
### <a name="topologies-that-have-three-or-more-participating-databases"></a><span data-ttu-id="70f8e-144">3 つ以上の参加データベースがあるトポロジ</span><span class="sxs-lookup"><span data-stu-id="70f8e-144">Topologies That Have Three or More Participating Databases</span></span>  
 <span data-ttu-id="70f8e-145">![分散した場所へのピア ツー ピア レプリケーション](../media/repl-multinode-02.gif "分散した場所へのピア ツー ピア レプリケーション")</span><span class="sxs-lookup"><span data-stu-id="70f8e-145">![Peer-to-peer replication to dispersed locations](../media/repl-multinode-02.gif "Peer-to-peer replication to dispersed locations")</span></span>  
  
 <span data-ttu-id="70f8e-146">この図は、ロサンゼルス、ロンドン、台北にオフィスを持つ、世界規模のソフトウェア サポート企業にデータを提供する 3 つの参加データベースを示しています。</span><span class="sxs-lookup"><span data-stu-id="70f8e-146">The preceding illustration shows three participating databases that provide data for a worldwide software support organization, with offices in Los Angeles, London, and Taipei.</span></span> <span data-ttu-id="70f8e-147">各オフィスのサポート エンジニアはカスタマー コールを受けて、各カスタマー コールに関する情報を入力および更新します。</span><span class="sxs-lookup"><span data-stu-id="70f8e-147">The support engineers at each office take customer calls and enter and update information about each customer call.</span></span> <span data-ttu-id="70f8e-148">3 つのオフィスの時間帯は 8 時間の時差があるため、勤務時間が重なることはありません。</span><span class="sxs-lookup"><span data-stu-id="70f8e-148">The time zones for the three offices are eight hours apart, so there is no overlap in the workday.</span></span> <span data-ttu-id="70f8e-149">台北オフィスが閉まるときに、ロンドン オフィスが開きます。</span><span class="sxs-lookup"><span data-stu-id="70f8e-149">As the Taipei office closes, the London office is opening for the day.</span></span> <span data-ttu-id="70f8e-150">1 つのオフィスが閉まっているときに 1 つのコールが進行している場合、コールは、次に開くオフィスの代表者に転送されます。</span><span class="sxs-lookup"><span data-stu-id="70f8e-150">If a call is still in progress as one office is closing, the call is transferred to a representative at the next office to open.</span></span>  
  
 <span data-ttu-id="70f8e-151">それぞれのオフィスにはデータベースとアプリケーション サーバーが 1 つずつあり、サポート エンジニアがカスタマー コールに関する情報を入力、更新する際に使用されています。</span><span class="sxs-lookup"><span data-stu-id="70f8e-151">Each location has a database and an application server, which are used by the support engineers as they enter and update information about customer calls.</span></span> <span data-ttu-id="70f8e-152">トポロジは時間でパーティション分割されるので、</span><span class="sxs-lookup"><span data-stu-id="70f8e-152">The topology is partitioned by time.</span></span> <span data-ttu-id="70f8e-153">現在営業中のノードでのみ更新が行われ、その更新は他の参加データベースに送られます。</span><span class="sxs-lookup"><span data-stu-id="70f8e-153">Therefore, updates occur only at the node that is currently open for business, and then the updates flow to the other participating databases.</span></span> <span data-ttu-id="70f8e-154">このトポロジには、次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="70f8e-154">This topology provides the following benefits:</span></span>  
  
-   <span data-ttu-id="70f8e-155">孤立せず独立性を維持。各オフィスはデータを個別に挿入、更新、または削除できますが、それらはすべて他の参加データベースにレプリケートされるため、データを共有することもできます。</span><span class="sxs-lookup"><span data-stu-id="70f8e-155">Independence without isolation: Each office can insert, update, or delete data independently but can also share the data because it is replicated to all other participating databases.</span></span>  
  
-   <span data-ttu-id="70f8e-156">参加データベースのいずれかで障害が発生したり、メンテナンスが行われている場合に高い可用性を実現。</span><span class="sxs-lookup"><span data-stu-id="70f8e-156">Higher availability in case of failure or to allow maintenance at one or more of the participating databases.</span></span>  
  
     <span data-ttu-id="70f8e-157">![3 つまたは 4 つのノードによるピア ツー ピア レプリケーション](../media/repl-multinode-04.gif "3 つまたは 4 つのノードによるピア ツー ピア レプリケーション")</span><span class="sxs-lookup"><span data-stu-id="70f8e-157">![Peer-to-peer replication, three and four nodes](../media/repl-multinode-04.gif "Peer-to-peer replication, three and four nodes")</span></span>  
  
 <span data-ttu-id="70f8e-158">この図は、3 つのノードで構成されるトポロジへの 1 つのノードの追加を示しています。</span><span class="sxs-lookup"><span data-stu-id="70f8e-158">The preceding illustration shows the addition of a node to the three-node topology.</span></span> <span data-ttu-id="70f8e-159">このシナリオでは、次のような場合にノードを追加できます。</span><span class="sxs-lookup"><span data-stu-id="70f8e-159">A node could be added in this scenario for the following reasons:</span></span>  
  
-   <span data-ttu-id="70f8e-160">別のオフィスが開いている場合。</span><span class="sxs-lookup"><span data-stu-id="70f8e-160">Because another office is opened.</span></span>  
  
-   <span data-ttu-id="70f8e-161">ディスク障害やその他の重大な障害が発生したときに、より高い可用性を提供してメンテナンスをサポートしたり、フォールト トレランスを強化する場合。</span><span class="sxs-lookup"><span data-stu-id="70f8e-161">To provide higher availability to support maintenance or increase fault tolerance if a disk failure or other major failure occurs.</span></span>  
  
 <span data-ttu-id="70f8e-162">3 つおよび 4 つのノードで構成されるトポロジはどちらも、すべてのデータベースが他のすべてのデータベースにパブリッシュおよびサブスクライブしていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="70f8e-162">Notice that in both the three- and four-node topologies, all databases publish and subscribe to all other databases.</span></span> <span data-ttu-id="70f8e-163">これにより、1 つ以上のノードでメンテナンスが必要な場合や障害が発生した場合に、最大限の可用性が実現されます。</span><span class="sxs-lookup"><span data-stu-id="70f8e-163">This provides maximum availability in case of maintenance needs or failure of one or more nodes.</span></span> <span data-ttu-id="70f8e-164">ノードを追加するときには、配置と管理のパフォーマンスおよび複雑さを考慮して可用性とスケーラビリティを調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70f8e-164">As nodes are added, you must balance availability and scalability needs against performance and the complexity of deployment and administration.</span></span>  
  
## <a name="configuring-peer-to-peer-replication"></a><span data-ttu-id="70f8e-165">ピア ツー ピア レプリケーションの構成</span><span class="sxs-lookup"><span data-stu-id="70f8e-165">Configuring Peer-to-Peer Replication</span></span>  
 <span data-ttu-id="70f8e-166">ピア ツー ピア レプリケーション トポロジの構成は、一連の標準トランザクション パブリケーションおよびサブスクリプションの構成とよく似ています。</span><span class="sxs-lookup"><span data-stu-id="70f8e-166">Configuring a peer-to-peer replication topology is very similar to configuring a series of standard transactional publications and subscriptions.</span></span> <span data-ttu-id="70f8e-167">次のトピックで説明する手順では、3 ノード システムの構成を説明しますが、これは上のピア ツー ピア トポロジを示す図の左側の構成と似ています。</span><span class="sxs-lookup"><span data-stu-id="70f8e-167">The steps described in the following topics show the configuration of a three-node system, similar to the configuration shown on the left in the previous illustration that shows peer-to-peer topology.</span></span>  
  
## <a name="considerations-for-using-peer-to-peer-replication"></a><span data-ttu-id="70f8e-168">ピア ツー ピア レプリケーションの使用に関する注意点</span><span class="sxs-lookup"><span data-stu-id="70f8e-168">Considerations for Using Peer-to-Peer Replication</span></span>  
 <span data-ttu-id="70f8e-169">ここでは、ピア ツー ピア レプリケーションを使用する際に考慮する必要がある情報とガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="70f8e-169">This section provides information and guidelines to consider when you use peer-to-peer replication.</span></span>  
  
### <a name="general-considerations"></a><span data-ttu-id="70f8e-170">一般的な考慮事項</span><span class="sxs-lookup"><span data-stu-id="70f8e-170">General Considerations</span></span>  
  
-   <span data-ttu-id="70f8e-171">ピア ツー ピア レプリケーションは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の Enterprise バージョンでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="70f8e-171">Peer-to-peer replication is available only in Enterprise versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="70f8e-172">ピア ツー ピア レプリケーションに参加するすべてのデータベースに、同一のスキーマとデータを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="70f8e-172">All databases that participate in peer-to-peer replication should contain identical schema and data:</span></span>  
  
    -   <span data-ttu-id="70f8e-173">オブジェクト名、オブジェクト スキーマ、およびパブリケーション名が同一である必要があります。</span><span class="sxs-lookup"><span data-stu-id="70f8e-173">Object names, object schema, and publication names should be identical.</span></span>  
  
    -   <span data-ttu-id="70f8e-174">パブリケーションで、スキーマ変更のレプリケートが許可されている</span><span class="sxs-lookup"><span data-stu-id="70f8e-174">Publications must allow schema changes to be replicated.</span></span> <span data-ttu-id="70f8e-175">(パブリケーション プロパティ **replicate_ddl** が既定の **1** に設定されている) 必要があります。詳細については、「[パブリケーション データベースでのスキーマの変更](../publish/make-schema-changes-on-publication-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70f8e-175">(This is a setting of **1** for the publication property **replicate_ddl**, which is the default setting.) For more information, see [Make Schema Changes on Publication Databases](../publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
    -   <span data-ttu-id="70f8e-176">行と列のフィルター処理はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="70f8e-176">Row and column filtering are not supported.</span></span>  
  
-   <span data-ttu-id="70f8e-177">ノードごとに独自のディストリビューション データベースを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="70f8e-177">We recommend that each node use its own distribution database.</span></span> <span data-ttu-id="70f8e-178">これにより、単一地点での失敗が発生する可能性を低減できます。</span><span class="sxs-lookup"><span data-stu-id="70f8e-178">This eliminates the potential of having a single point of failure.</span></span>  
  
-   <span data-ttu-id="70f8e-179">テーブルおよびその他のオブジェクトは、単一のパブリケーション データベース内の複数のピア ツー ピア パブリケーションに含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="70f8e-179">Tables and other objects cannot be included in multiple peer-to-peer publications in a single publication database.</span></span>  
  
-   <span data-ttu-id="70f8e-180">サブスクリプションを作成するには、パブリケーションをピア ツー ピア レプリケーションで有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="70f8e-180">A publication must be enabled for peer-to-peer replication before any subscriptions are created.</span></span>  
  
-   <span data-ttu-id="70f8e-181">サブスクリプションは、バックアップを使用するか、 **[レプリケーションのサポートのみ]** オプションで初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70f8e-181">Subscriptions must be initialized by using a backup or with the **'replication support only'** option.</span></span> <span data-ttu-id="70f8e-182">詳細については、「 [スナップショットを使用しないトランザクション サブスクリプションの初期化](../initialize-a-transactional-subscription-without-a-snapshot.md)を使用して、サブスクリプションを手動で初期化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="70f8e-182">For more information, see [Initialize a Transactional Subscription Without a Snapshot](../initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
-   <span data-ttu-id="70f8e-183">ID 列の使用はお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="70f8e-183">We do not recommend the use of identity columns.</span></span> <span data-ttu-id="70f8e-184">ID を使用する場合は、各参加データベースのテーブルに割り当てられた範囲を手動で管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70f8e-184">When using identities, you must manually manage the ranges assigned to the tables at each participating database.</span></span> <span data-ttu-id="70f8e-185">詳細については、「[Replicate Identity Columns](../publish/replicate-identity-columns.md)」 (ID 列のレプリケート) で、"Assigning Ranges for Manual Identity Range Management" (手動で ID 範囲を管理する場合の範囲の割り当て) セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="70f8e-185">For more information, see the section "Assigning Ranges for Manual Identity Range Management" in [Replicate Identity Columns](../publish/replicate-identity-columns.md).</span></span>  
  
### <a name="feature-restrictions"></a><span data-ttu-id="70f8e-186">機能の制限</span><span class="sxs-lookup"><span data-stu-id="70f8e-186">Feature Restrictions</span></span>  
 <span data-ttu-id="70f8e-187">ピア ツー ピア レプリケーションではトランザクション レプリケーションの主要な機能がサポートされていますが、次のオプションはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="70f8e-187">Peer-to-peer replication supports the core features of transactional replication, but does not support the following options:</span></span>  
  
-   <span data-ttu-id="70f8e-188">スナップショットを使用した初期化および再初期化</span><span class="sxs-lookup"><span data-stu-id="70f8e-188">Initialization and reinitialization with a snapshot.</span></span>  
  
-   <span data-ttu-id="70f8e-189">行と列のフィルター選択</span><span class="sxs-lookup"><span data-stu-id="70f8e-189">Row and column filters.</span></span>  
  
-   <span data-ttu-id="70f8e-190">timestamp 列</span><span class="sxs-lookup"><span data-stu-id="70f8e-190">Timestamp columns.</span></span>  
  
-   <span data-ttu-id="70f8e-191">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のパブリッシャーとサブスクライバー</span><span class="sxs-lookup"><span data-stu-id="70f8e-191">Non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Publishers and Subscribers.</span></span>  
  
-   <span data-ttu-id="70f8e-192">即時更新とキュー更新サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="70f8e-192">Immediate updating and queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="70f8e-193">匿名サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="70f8e-193">Anonymous subscriptions.</span></span>  
  
-   <span data-ttu-id="70f8e-194">部分サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="70f8e-194">Partial subscriptions.</span></span>  
  
-   <span data-ttu-id="70f8e-195">アタッチ可能なサブスクリプションと変換可能なサブスクリプション</span><span class="sxs-lookup"><span data-stu-id="70f8e-195">Attachable subscriptions and transformable subscriptions.</span></span> <span data-ttu-id="70f8e-196">(どちらも [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] では非推奨)</span><span class="sxs-lookup"><span data-stu-id="70f8e-196">(Both of these options were deprecated in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].)</span></span>  
  
-   <span data-ttu-id="70f8e-197">共有ディストリビューション エージェント</span><span class="sxs-lookup"><span data-stu-id="70f8e-197">Shared Distribution Agents.</span></span>  
  
-   <span data-ttu-id="70f8e-198">ディストリビューション エージェントのパラメーター **-SubscriptionStreams** とログ リーダー エージェントのパラメーター **-MaxCmdsInTran**</span><span class="sxs-lookup"><span data-stu-id="70f8e-198">The Distribution Agent parameter **-SubscriptionStreams** and the Log Reader Agent parameter **-MaxCmdsInTran**.</span></span>  
  
-   <span data-ttu-id="70f8e-199">アーティクルのプロパティ\*\* \@ destination_owner**および** \@ destination_table\*\*。</span><span class="sxs-lookup"><span data-stu-id="70f8e-199">The article properties **\@destination_owner** and **\@destination_table**.</span></span>  

-   <span data-ttu-id="70f8e-200">ピア ツー ピア トランザクション レプリケーションでは、ピア ツー ピア パブリケーションの一方向トランザクション サブスクリプションを作成できません</span><span class="sxs-lookup"><span data-stu-id="70f8e-200">Peer-to-Peer transactional replication does not support creating a one-way transactional subscription to a Peer-to-Peer publication</span></span>
  
 <span data-ttu-id="70f8e-201">次のプロパティには特別な注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="70f8e-201">The following properties have special considerations:</span></span>  
  
-   <span data-ttu-id="70f8e-202">パブリケーションプロパティ\*\* \@ allow_initialize_from_backup\*\*には値が必要です `true` 。</span><span class="sxs-lookup"><span data-stu-id="70f8e-202">The publication property **\@allow_initialize_from_backup** requires a value of `true`.</span></span>  
  
-   <span data-ttu-id="70f8e-203">アーティクルのプロパティ\*\* \@ replicate_ddl**には、の値が必要です `true` 。** \@ identityrangemanagementoption**には値が必要です `manual` 。および** \@ status**では、オプション**24\*\*が設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="70f8e-203">The article property **\@replicate_ddl** requires a value of `true`; **\@identityrangemanagementoption** requires a value of `manual`; and **\@status** requires that option **24** is set.</span></span>  
  
-   <span data-ttu-id="70f8e-204">アーティクルのプロパティ\*\* \@ ins_cmd**、 \*\* \@ del_cmd**、および\*\* \@ upd_cmd\*\*の値をに設定することはできません `SQL` 。</span><span class="sxs-lookup"><span data-stu-id="70f8e-204">The value for article properties **\@ins_cmd**, **\@del_cmd**, and **\@upd_cmd** cannot be set to `SQL`.</span></span>  
  
-   <span data-ttu-id="70f8e-205">サブスクリプションプロパティ\*\* \@ sync_type\*\*には、またはの値が必要です `none` `automatic` 。</span><span class="sxs-lookup"><span data-stu-id="70f8e-205">The subscription property **\@sync_type** requires a value of `none` or `automatic`.</span></span>  
  
### <a name="maintenance-considerations"></a><span data-ttu-id="70f8e-206">メンテナンスの注意事項</span><span class="sxs-lookup"><span data-stu-id="70f8e-206">Maintenance Considerations</span></span>  
 <span data-ttu-id="70f8e-207">次のアクションを実行する場合は、システムを停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70f8e-207">The following actions require the system to be quiesced.</span></span> <span data-ttu-id="70f8e-208">システムの停止を実行するには、すべてのノードのパブリッシュされたテーブルで処理を停止し、他のすべてのノードからのすべての変更を各ノードが受信しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="70f8e-208">This means stopping activity on published tables at all nodes and making sure that each node has received all changes from all other nodes.</span></span>  
  
-   <span data-ttu-id="70f8e-209">既存の [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] トポロジへのノードの追加</span><span class="sxs-lookup"><span data-stu-id="70f8e-209">Adding a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] node to an existing topology</span></span>  
  
-   <span data-ttu-id="70f8e-210">既存のパブリケーションへのアーティクルの追加</span><span class="sxs-lookup"><span data-stu-id="70f8e-210">Adding an article to an existing publication</span></span>  
  
-   <span data-ttu-id="70f8e-211">スキーマの変更</span><span class="sxs-lookup"><span data-stu-id="70f8e-211">Making schema changes</span></span>  
  
-   <span data-ttu-id="70f8e-212">バックアップからのノードの復元</span><span class="sxs-lookup"><span data-stu-id="70f8e-212">Restoring a node from a backup</span></span>  
  
 <span data-ttu-id="70f8e-213">詳細については、「[Quiesce a Replication Topology &#40;Replication Transact-SQL Programming&#41;](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)」と (レプリケーション トポロジの停止 (レプリケーション Transact-SQL プログラミング)) 「[Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](../administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)」 (ピア ツー ピア トポロジの管理 (レプリケーション Transact-SQL プログラミング)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70f8e-213">For more information, see [Quiesce a Replication Topology &#40;Replication Transact-SQL Programming&#41;](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md) and [Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](../administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md).</span></span>  
  
-   <span data-ttu-id="70f8e-214">ピア ツー ピア トポロジに新しいノードを追加する場合は、新しいノードの追加後に作成されたバックアップのみを使用して復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70f8e-214">If you add a new node to a peer-to-peer topology, you should restore only from backups that were created after the new node was added.</span></span>  
  
-   <span data-ttu-id="70f8e-215">ピア ツー ピア トポロジでは、サブスクリプションの再初期化を実行できません。</span><span class="sxs-lookup"><span data-stu-id="70f8e-215">You cannot reinitialize subscriptions in a peer-to-peer topology.</span></span> <span data-ttu-id="70f8e-216">ノードで新しいデータのコピーを確実に保持する必要がある場合は、そのノードでバックアップを復元してください。</span><span class="sxs-lookup"><span data-stu-id="70f8e-216">If you have to ensure that a node has a new copy of the data, restore a backup at the node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70f8e-217">参照</span><span class="sxs-lookup"><span data-stu-id="70f8e-217">See Also</span></span>  
 <span data-ttu-id="70f8e-218">[ピア ツー ピア トポロジの管理 &#40;レプリケーション Transact-SQL プログラミング&#41;](../administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span><span class="sxs-lookup"><span data-stu-id="70f8e-218">[Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](../administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span></span>  
 <span data-ttu-id="70f8e-219">[スナップショット レプリケーションおよびトランザクション レプリケーションのバックアップと復元の方式](../administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="70f8e-219">[Strategies for Backing Up and Restoring Snapshot and Transactional Replication](../administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md) </span></span>  
 [<span data-ttu-id="70f8e-220">トランザクション レプリケーションで使用するパブリケーションの種類</span><span class="sxs-lookup"><span data-stu-id="70f8e-220">Publication Types for Transactional Replication</span></span>](transactional-replication.md)  
  
  
