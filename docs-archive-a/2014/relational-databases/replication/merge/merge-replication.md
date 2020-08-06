---
title: マージ レプリケーション | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], about merge replication
- merge replication [SQL Server replication]
ms.assetid: ff87c368-4c00-4e48-809d-ea752839551e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7feef9e4debc228d1685c664c072139d60b56c22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630945"
---
# <a name="merge-replication"></a><span data-ttu-id="e9019-102">マージ レプリケーション</span><span class="sxs-lookup"><span data-stu-id="e9019-102">Merge Replication</span></span>
  <span data-ttu-id="e9019-103">一般にマージ レプリケーションは、トランザクション レプリケーションと同様に、パブリケーションのデータベース オブジェクトとデータのスナップショットで開始されます。</span><span class="sxs-lookup"><span data-stu-id="e9019-103">Merge replication, like transactional replication, typically starts with a snapshot of the publication database objects and data.</span></span> <span data-ttu-id="e9019-104">その後にパブリッシャーとサブスクライバーで行われたデータおよびスキーマの変更は、トリガーを使って追跡されます。</span><span class="sxs-lookup"><span data-stu-id="e9019-104">Subsequent data changes and schema modifications made at the Publisher and Subscribers are tracked with triggers.</span></span> <span data-ttu-id="e9019-105">サブスクライバーは、ネットワークに接続されたときにパブリッシャーと同期して、前回の同期以降にパブリッシャーとサブスクライバーの間で変更されたすべての行を交換します。</span><span class="sxs-lookup"><span data-stu-id="e9019-105">The Subscriber synchronizes with the Publisher when connected to the network and exchanges all rows that have changed between the Publisher and Subscriber since the last time synchronization occurred.</span></span>

 <span data-ttu-id="e9019-106">マージ レプリケーションは、一般にサーバー対クライアント環境で使用されます。</span><span class="sxs-lookup"><span data-stu-id="e9019-106">Merge replication is typically used in server-to-client environments.</span></span> <span data-ttu-id="e9019-107">マージ レプリケーションは、以下の状況に適しています。</span><span class="sxs-lookup"><span data-stu-id="e9019-107">Merge replication is appropriate in any of the following situations:</span></span>

-   <span data-ttu-id="e9019-108">複数のサブスクライバーで別々の時刻に同じデータを更新し、それらの変更をパブリッシャーや他のサブスクライバーに反映する場合がある。</span><span class="sxs-lookup"><span data-stu-id="e9019-108">Multiple Subscribers might update the same data at various times and propagate those changes to the Publisher and to other Subscribers.</span></span>

-   <span data-ttu-id="e9019-109">サブスクライバーで、データを受信し、オフラインで変更を行い、後でパブリッシャーおよび他のサブスクライバーと変更を同期する必要がある。</span><span class="sxs-lookup"><span data-stu-id="e9019-109">Subscribers need to receive data, make changes offline, and later synchronize changes with the Publisher and other Subscribers.</span></span>

-   <span data-ttu-id="e9019-110">各サブスクライバーが、データの別々の部分を必要とする。</span><span class="sxs-lookup"><span data-stu-id="e9019-110">Each Subscriber requires a different partition of data.</span></span>

-   <span data-ttu-id="e9019-111">競合が発生する可能性があり、発生した場合にはそれを検出して解決できる必要がある。</span><span class="sxs-lookup"><span data-stu-id="e9019-111">Conflicts might occur and, when they do, you need the ability to detect and resolve them.</span></span>

-   <span data-ttu-id="e9019-112">アプリケーションで、中間状態のデータにアクセスするのではなく、最終的な変更結果が必要である。</span><span class="sxs-lookup"><span data-stu-id="e9019-112">The application requires net data change rather than access to intermediate data states.</span></span> <span data-ttu-id="e9019-113">たとえば、サブスクライバーでパブリッシャーと同期する前に行が 5 回変更された場合、最終的な変更結果 (つまり、5 回目の値) を反映させるために、パブリッシャーでは 1 回だけ変更されます。</span><span class="sxs-lookup"><span data-stu-id="e9019-113">For example, if a row changes five times at a Subscriber before it synchronizes with a Publisher, the row will change only once at the Publisher to reflect the net data change (that is, the fifth value).</span></span>

 <span data-ttu-id="e9019-114">マージ レプリケーションでは、さまざまなサイトが自律的に動作し、更新内容が後で 1 つにマージされます。</span><span class="sxs-lookup"><span data-stu-id="e9019-114">Merge replication allows various sites to work autonomously and later merge updates into a single, uniform result.</span></span> <span data-ttu-id="e9019-115">更新は複数のノードで発生するため、パブリッシャーおよび複数のサブスクライバーで同じデータが更新されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="e9019-115">Because updates are made at more than one node, the same data may have been updated by the Publisher and by more than one Subscriber.</span></span> <span data-ttu-id="e9019-116">したがって、更新をマージする際に競合が発生する可能性があるため、マージ レプリケーションには競合を処理するいくつかの方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="e9019-116">Therefore, conflicts can occur when updates are merged and merge replication provides a number of ways to handle conflicts.</span></span>

 <span data-ttu-id="e9019-117">マージ レプリケーションは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] スナップショット エージェントおよびマージ エージェントによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="e9019-117">Merge replication is implemented by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Snapshot Agent and Merge Agent.</span></span> <span data-ttu-id="e9019-118">パブリケーションがフィルター選択されていない場合や静的フィルターを使用している場合、スナップショット エージェントでは 1 つのスナップショットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e9019-118">If the publication is unfiltered or uses static filters, the Snapshot Agent creates a single snapshot.</span></span> <span data-ttu-id="e9019-119">パブリケーションがパラメーター化されたフィルターを使用している場合、スナップショット エージェントではデータのパーティションごとに 1 つのスナップショットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e9019-119">If the publication uses parameterized filters, the Snapshot Agent creates a snapshot for each partition of data.</span></span> <span data-ttu-id="e9019-120">マージ エージェントは、初期スナップショットをサブスクライバーに適用します。</span><span class="sxs-lookup"><span data-stu-id="e9019-120">The Merge Agent applies the initial snapshots to the Subscribers.</span></span> <span data-ttu-id="e9019-121">また、初期スナップショットの作成後にパブリッシャーまたはサブスクライバーで発生したデータの増分変更がマージされ、ユーザーが構成したルールに従って競合を検出し、解決します。</span><span class="sxs-lookup"><span data-stu-id="e9019-121">It also merges incremental data changes that occurred at the Publisher or Subscribers after the initial snapshot was created, and detects and resolves any conflicts according to rules you configure.</span></span>

 <span data-ttu-id="e9019-122">変更を追跡するため、マージ レプリケーション (およびキュー更新サブスクリプションを使用したトランザクション レプリケーション) では、パブリッシュされたすべてのテーブルのすべての行を一意に識別できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9019-122">To track changes, merge replication (and transactional replication with queued updating subscriptions) must be able to uniquely identify every row in every published table.</span></span> <span data-ttu-id="e9019-123">マージ レプリケーションを実行するには、列 `rowguid` をすべてのテーブルに追加します。ただし、データ型が `uniqueidentifier` で `ROWGUIDCOL` プロパティが設定されている列が、テーブルに既にある場合を除きます (このような列がある場合は、その列が使用されます)。</span><span class="sxs-lookup"><span data-stu-id="e9019-123">To accomplish this merge replication adds the column `rowguid` to every table, unless the table already has a column of data type `uniqueidentifier` with the `ROWGUIDCOL` property set (in which case this column is used).</span></span> <span data-ttu-id="e9019-124">テーブルがパブリケーションから削除されると、`rowguid` 列も削除されます。既存の列を追跡に使用していた場合は、その列は削除されません。</span><span class="sxs-lookup"><span data-stu-id="e9019-124">If the table is dropped from the publication, the `rowguid` column is removed; if an existing column was used for tracking, the column is not removed.</span></span> <span data-ttu-id="e9019-125">フィルターには、レプリケーションで行の識別に使用される `rowguidcol` を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="e9019-125">A filter must not include the `rowguidcol` used by replication to identify rows.</span></span> <span data-ttu-id="e9019-126">`newid()` 列の既定値として `rowguid` 関数が使用されますが、必要に応じて各行に GUID を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e9019-126">The `newid()` function is provided as a default for the `rowguid` column, however customers can provide a guid for each row if needed.</span></span> <span data-ttu-id="e9019-127">ただし、値 00000000-0000-0000-0000-000000000000 は指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="e9019-127">However, do not provide value 00000000-0000-0000-0000-000000000000.</span></span>

 <span data-ttu-id="e9019-128">次の図は、マージ レプリケーションで使用されるコンポーネントを示しています。</span><span class="sxs-lookup"><span data-stu-id="e9019-128">The following diagram shows the components used in merge replication.</span></span>

 <span data-ttu-id="e9019-129">![マージ レプリケーション コンポーネントとデータ フロー](../media/merge.gif "マージ レプリケーション コンポーネントとデータ フロー")</span><span class="sxs-lookup"><span data-stu-id="e9019-129">![Merge replication components and data flow](../media/merge.gif "Merge replication components and data flow")</span></span>


