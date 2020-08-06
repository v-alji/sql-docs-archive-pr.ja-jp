---
title: パブリケーション情報、トレーサートークン (トランザクションパブリケーション、SQL Server 2005 以降) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.tracertokens.f1
ms.assetid: a115ba95-17ae-45df-91bd-5a1a35f3745f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: af84ab9b9122a55367780976056ce95aa597f62a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721302"
---
# <a name="publication-information-tracer-tokens-transactional-publication-sql-server-2005-and-later"></a><span data-ttu-id="c166a-102">パブリケーション情報、トレーサー トークン (トランザクション パブリケーション、SQL Server 2005 以降)</span><span class="sxs-lookup"><span data-stu-id="c166a-102">Publication Information, Tracer Tokens (Transactional Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="c166a-103">**[トレーサー トークン]** タブを使用すると、接続の検証と、トランザクション レプリケーションを使用するシステムの待機時間を測定できます。</span><span class="sxs-lookup"><span data-stu-id="c166a-103">The **Tracer Tokens** tab allows you to validate connections and to measure the latency of a system that uses transactional replication.</span></span> <span data-ttu-id="c166a-104">トークン (小さなデータ) は、通常のレプリケートされたトランザクションのようにマークが付けられてパブリケーション データベースのトランザクション ログに書き込まれ、システムを介して送信されることで、次の計算が可能になります。</span><span class="sxs-lookup"><span data-stu-id="c166a-104">A token (a small amount of data) is written to the transaction log of the publication database, marked as though it were a typical replicated transaction, and sent through the system, allowing a calculation of:</span></span>  
  
-   <span data-ttu-id="c166a-105">パブリッシャーでコミットされるトランザクションと、ディストリビューターでディストリビューション データベース内に挿入される対応するコマンドの間での経過時間。</span><span class="sxs-lookup"><span data-stu-id="c166a-105">How much time elapses between a transaction being committed at the Publisher and the corresponding command being inserted in the distribution database at the Distributor.</span></span>  
  
-   <span data-ttu-id="c166a-106">ディストリビューション データベース内に挿入されるコマンドと、サブスクライバーでコミットされる対応するトランザクションの間での経過時間。</span><span class="sxs-lookup"><span data-stu-id="c166a-106">How much time elapses between a command being inserted in the distribution database and the corresponding transaction being committed at a Subscriber.</span></span>  
  
 <span data-ttu-id="c166a-107">これらの計算結果から、以下のようなさまざまな内容を特定できます。</span><span class="sxs-lookup"><span data-stu-id="c166a-107">From these calculations, you can answer a number of questions, including:</span></span>  
  
-   <span data-ttu-id="c166a-108">変更内容をパブリッシャーから受信するのに最も時間がかかるのはどのサブスクライバーか。</span><span class="sxs-lookup"><span data-stu-id="c166a-108">Which Subscribers take the longest to receive a change from the Publisher?</span></span>  
  
-   <span data-ttu-id="c166a-109">トレース トークンを受信することになっているサブスクライバーのうち、受信していないサブスクライバーがあるか。あるとすればどのサブスクライバーか。</span><span class="sxs-lookup"><span data-stu-id="c166a-109">Of the Subscribers expected to receive the tracer token, which, if any, have not received it?</span></span>  
  
## <a name="options"></a><span data-ttu-id="c166a-110">Options</span><span class="sxs-lookup"><span data-stu-id="c166a-110">Options</span></span>  
 <span data-ttu-id="c166a-111">グリッドにデータを表示する方法を変更するには、グリッドを右クリックし、次のいずれかのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c166a-111">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="c166a-112">**[並べ替え]**: **[列の並べ替え]** ダイアログ ボックスで、1 つ以上の列を基準にして並べ替えを行います。</span><span class="sxs-lookup"><span data-stu-id="c166a-112">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="c166a-113">**[表示する列の選択]**: **[列の選択]** ダイアログ ボックスで、表示する列とその表示順序を選択します。</span><span class="sxs-lookup"><span data-stu-id="c166a-113">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="c166a-114">**[フィルター]**: **[フィルターの設定]** ダイアログ ボックスで、列の値に基づいてグリッドの行をフィルター選択します。</span><span class="sxs-lookup"><span data-stu-id="c166a-114">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="c166a-115">**[フィルターのクリア]**: グリッドのフィルター設定をすべてクリアします。</span><span class="sxs-lookup"><span data-stu-id="c166a-115">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="c166a-116">フィルター設定は各グリッドに固有です。</span><span class="sxs-lookup"><span data-stu-id="c166a-116">Filter settings are specific to each grid.</span></span> <span data-ttu-id="c166a-117">列の選択と並べ替えは、各パブリッシャーのパブリケーション グリッドなど、同じ種類のすべてのグリッドに適用されます。</span><span class="sxs-lookup"><span data-stu-id="c166a-117">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="c166a-118">**[トレーサーの挿入]**</span><span class="sxs-lookup"><span data-stu-id="c166a-118">**Insert Tracer**</span></span>  
 <span data-ttu-id="c166a-119">パブリッシャーでトランザクション ログ内のトレーサー トークンを挿入します。</span><span class="sxs-lookup"><span data-stu-id="c166a-119">Click to insert a tracer token in the transaction log at the Publisher.</span></span>  
  
 <span data-ttu-id="c166a-120">**[挿入された時間]**</span><span class="sxs-lookup"><span data-stu-id="c166a-120">**Time inserted**</span></span>  
 <span data-ttu-id="c166a-121">トレーサー トークンが挿入された時間を選択し、その時間の待機時間情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="c166a-121">Select a time at which a tracer token was inserted to display latency information from that time.</span></span> <span data-ttu-id="c166a-122">既定では、最新の時間の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c166a-122">By default, information from the most recent time is displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c166a-123">トレーサー トークン情報は、ディストリビューション データベースの履歴保持期間の制約を受けるその他の履歴データと同じ期間保持されます。</span><span class="sxs-lookup"><span data-stu-id="c166a-123">Tracer token information is retained for the same time period as other historical data, which is governed by the history retention period of the distribution database.</span></span> <span data-ttu-id="c166a-124">ディストリビューション データベースのプロパティの変更方法の詳細については、「[ディストリビューターとパブリッシャーのプロパティの表示および変更](view-and-modify-distributor-and-publisher-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c166a-124">For information about changing distribution database properties, see [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
 <span data-ttu-id="c166a-125">**[サブスクリプション]**</span><span class="sxs-lookup"><span data-stu-id="c166a-125">**Subscription**</span></span>  
 <span data-ttu-id="c166a-126">パブリケーションに対する各サブスクリプションの名前です。</span><span class="sxs-lookup"><span data-stu-id="c166a-126">The name of each subscription to the publication.</span></span>  
  
 <span data-ttu-id="c166a-127">**[パブリッシャーからディストリビューターまで]**</span><span class="sxs-lookup"><span data-stu-id="c166a-127">**Publisher to Distributor**</span></span>  
 <span data-ttu-id="c166a-128">パブリッシャーでコミットされるトランザクションと、ディストリビューターでディストリビューション データベース内に挿入される対応するコマンドの間での経過時間です。</span><span class="sxs-lookup"><span data-stu-id="c166a-128">The elapsed time between a transaction being committed at the Publisher and the corresponding command being inserted in the distribution database at the Distributor.</span></span> <span data-ttu-id="c166a-129">**[保留中]** の値は、トークンがまだディストリビューターに到達していないことを示します。</span><span class="sxs-lookup"><span data-stu-id="c166a-129">A value of **Pending** indicates that the token has not yet reached the Distributor.</span></span> <span data-ttu-id="c166a-130">保留中の状態が続く場合は、ログ リーダー エージェントが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c166a-130">If the pending state persists, ensure that the Log Reader Agent is running.</span></span>  
  
 <span data-ttu-id="c166a-131">**[ディストリビューターからサブスクライバーまで]**</span><span class="sxs-lookup"><span data-stu-id="c166a-131">**Distributor to Subscriber**</span></span>  
 <span data-ttu-id="c166a-132">ディストリビューション データベース内に挿入されるコマンドと、サブスクライバーでコミットされる対応するトランザクションの間での経過時間です。</span><span class="sxs-lookup"><span data-stu-id="c166a-132">The elapsed time between a command being inserted in the distribution database and the corresponding transaction being committed at a Subscriber.</span></span> <span data-ttu-id="c166a-133">**[保留中]** の値は、トークンがまだサブスクライバーに到達していないことを示します。</span><span class="sxs-lookup"><span data-stu-id="c166a-133">A value of **Pending** indicates that the token has not yet reached the Subscriber.</span></span> <span data-ttu-id="c166a-134">保留中の状態が続く場合は、ディストリビューション エージェントが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c166a-134">If the pending state persists, ensure that the Distribution Agent is running.</span></span>  
  
 <span data-ttu-id="c166a-135">**合計待機時間**</span><span class="sxs-lookup"><span data-stu-id="c166a-135">**Total Latency**</span></span>  
 <span data-ttu-id="c166a-136">パブリッシャーでコミットされるトランザクションと、サブスクライバーでコミットされる対応するトランザクションの間での経過時間です。</span><span class="sxs-lookup"><span data-stu-id="c166a-136">The elapsed time between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber.</span></span> <span data-ttu-id="c166a-137">これは、この時間にレプリケーション システムの端末間でサブスクライバーを待機する時間を表しています。</span><span class="sxs-lookup"><span data-stu-id="c166a-137">This represents the end-to-end latency of the replication system for this Subscriber at this time.</span></span> <span data-ttu-id="c166a-138">**[保留中]** の値は、トークンがまだサブスクライバーに到達していないことを示します。</span><span class="sxs-lookup"><span data-stu-id="c166a-138">A value of **Pending** indicates that the token has not yet reached the Subscriber.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c166a-139">参照</span><span class="sxs-lookup"><span data-stu-id="c166a-139">See Also</span></span>  
 <span data-ttu-id="c166a-140">[レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="c166a-140">[Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="c166a-141">[レプリケーションモニターを開始する](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="c166a-141">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="c166a-142">[トランザクションレプリケーションの待機時間を計測して接続を検証する](monitor/measure-latency-and-validate-connections-for-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="c166a-142">[Measure Latency and Validate Connections for Transactional Replication](monitor/measure-latency-and-validate-connections-for-transactional-replication.md) </span></span>  
 <span data-ttu-id="c166a-143">[レプリケーションモニターを使用したパフォーマンスの監視](monitor/monitor-performance-with-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="c166a-143">[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) </span></span>  
 <span data-ttu-id="c166a-144">[レプリケーションの監視](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="c166a-144">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="c166a-145">レプリケーション エージェントの概要</span><span class="sxs-lookup"><span data-stu-id="c166a-145">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
