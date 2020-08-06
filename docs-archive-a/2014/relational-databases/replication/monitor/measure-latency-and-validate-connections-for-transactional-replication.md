---
title: トランザクション レプリケーションの待機時間の計測および接続の検証 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, performance
- tracer tokens [SQL Server replication]
- latency [SQL Server replication]
- transactional replication, tracer tokens
- monitoring performance [SQL Server replication], tracer tokens
ms.assetid: 4addd426-7523-4067-8d7d-ca6bae4c9e34
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3ba1e5eddfdcffa5fbefdea323f110ba9d15ca8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634397"
---
# <a name="measure-latency-and-validate-connections-for-transactional-replication"></a><span data-ttu-id="33c03-102">トランザクション レプリケーションの待機時間の計測および接続の検証</span><span class="sxs-lookup"><span data-stu-id="33c03-102">Measure Latency and Validate Connections for Transactional Replication</span></span>
  <span data-ttu-id="33c03-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] でレプリケーション モニター、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用し、トランザクション レプリケーションの待機時間を計測して接続を検証する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="33c03-103">This topic describes how to measure latency and validate connections for transactional replication in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using Replication Monitor, [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span> <span data-ttu-id="33c03-104">トランザクション レプリケーションには、トレーサー トークン機能が用意されており、これによって簡単にトランザクション レプリケーション トポロジにおける待機時間を計測したり、パブリッシャー、ディストリビューター、およびサブスクライバーの間の接続を検証したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="33c03-104">Transactional replication provides the tracer token feature, which provides a convenient way to measure latency in transactional replication topologies and to validate the connections between the Publisher, Distributor and Subscribers.</span></span> <span data-ttu-id="33c03-105">トークン (小さなデータ) は、通常のレプリケートされたトランザクションのようにマークが付けられてパブリケーション データベースのトランザクション ログに書き込まれ、システムを介して送信されることで、次の計算が可能になります。</span><span class="sxs-lookup"><span data-stu-id="33c03-105">A token (a small amount of data) is written to the transaction log of the publication database, marked as though it were a typical replicated transaction, and sent through the system, allowing a calculation of:</span></span>  
  
-   <span data-ttu-id="33c03-106">パブリッシャーでコミットされるトランザクションと、ディストリビューターでディストリビューション データベース内に挿入される対応するコマンドの間での経過時間。</span><span class="sxs-lookup"><span data-stu-id="33c03-106">How much time elapses between a transaction being committed at the Publisher and the corresponding command being inserted in the distribution database at the Distributor.</span></span>  
  
-   <span data-ttu-id="33c03-107">ディストリビューション データベース内に挿入されるコマンドと、サブスクライバーでコミットされる対応するトランザクションの間での経過時間。</span><span class="sxs-lookup"><span data-stu-id="33c03-107">How much time elapses between a command being inserted in the distribution database and the corresponding transaction being committed at a Subscriber.</span></span>  
  
 <span data-ttu-id="33c03-108">これらの計算結果から、以下のようなさまざまな内容を特定できます。</span><span class="sxs-lookup"><span data-stu-id="33c03-108">From these calculations, you can answer a number of questions, including:</span></span>  
  
-   <span data-ttu-id="33c03-109">変更内容をパブリッシャーから受信するのに最も時間がかかるのはどのサブスクライバーか。</span><span class="sxs-lookup"><span data-stu-id="33c03-109">Which Subscribers take the longest to receive a change from the Publisher?</span></span>  
  
-   <span data-ttu-id="33c03-110">トレース トークンを受信することになっているサブスクライバーのうち、受信していないサブスクライバーがあるか。あるとすればどのサブスクライバーか。</span><span class="sxs-lookup"><span data-stu-id="33c03-110">Of the Subscribers expected to receive the tracer token, which, if any, have not received it?</span></span>  
  
 <span data-ttu-id="33c03-111">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="33c03-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="33c03-112">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="33c03-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="33c03-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="33c03-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   <span data-ttu-id="33c03-114">**接続の待機時間を計測して検証するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="33c03-114">**To measure latency and validate connections, using:**</span></span>  
  
     [<span data-ttu-id="33c03-115">SQL Server レプリケーション モニター</span><span class="sxs-lookup"><span data-stu-id="33c03-115">SQL Server Replication Monitor</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="33c03-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="33c03-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="33c03-117">レプリケーション管理オブジェクト (Replication Management Objects)</span><span class="sxs-lookup"><span data-stu-id="33c03-117">Replication Management Objects</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="33c03-118">はじめに</span><span class="sxs-lookup"><span data-stu-id="33c03-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="33c03-119">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="33c03-119">Limitations and Restrictions</span></span>  
 <span data-ttu-id="33c03-120">トレーサー トークンは、システムを停止する場合にも役立ちます。このとき、すべての処理を停止して、すべてのノードがすべての未処理の変更を受信したかどうかを検証します。</span><span class="sxs-lookup"><span data-stu-id="33c03-120">Tracer tokens can also be useful when quiescing a system, which involves stopping all activity and verifying that all nodes have received all outstanding changes.</span></span> <span data-ttu-id="33c03-121">詳細については、「[レプリケーション トポロジの停止 &#40;レプリケーション Transact-SQL プログラミング&#41;](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="33c03-121">For more information, see [Quiesce a Replication Topology &#40;Replication Transact-SQL Programming&#41;](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md).</span></span>  
  
 <span data-ttu-id="33c03-122">トレーサートークンを使用するには、特定のバージョンのを使用する必要があり [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="33c03-122">To use tracer tokens, you must use certain versions of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="33c03-123">ディストリビューターは以降である必要があり [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="33c03-123">The Distributor must be [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] or later.</span></span>  
  
-   <span data-ttu-id="33c03-124">パブリッシャーは [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降であるか、Oracle パブリッシャーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="33c03-124">The Publisher must be [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] or later or be an Oracle Publisher.</span></span>  
  
-   <span data-ttu-id="33c03-125">プッシュサブスクリプションの場合、トレーサートークンの統計情報は、サブスクライバーが7.0 以降の場合は、パブリッシャー、ディストリビューター、およびサブスクライバーから収集され [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="33c03-125">For push subscriptions, tracer token statistics are gathered from the Publisher, Distributor, and Subscribers if the Subscriber is [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 or later.</span></span>  
  
-   <span data-ttu-id="33c03-126">プル サブスクリプションでは、サブスクライバーが [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降である場合にのみ、トレーサー トークン統計がサブスクライバーから収集されます。</span><span class="sxs-lookup"><span data-stu-id="33c03-126">For pull subscriptions, tracer token statistics are gathered from Subscribers only if the Subscriber is [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] or later.</span></span> <span data-ttu-id="33c03-127">サブスクライバーが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 またはの場合 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] 、統計情報はパブリッシャーおよびディストリビューターからのみ収集されます。</span><span class="sxs-lookup"><span data-stu-id="33c03-127">If the Subscriber is [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)], statistics are gathered only from the Publisher and Distributor.</span></span>  
  
 <span data-ttu-id="33c03-128">その他にも、次のような問題点と制限事項について注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33c03-128">There are also a number of other issues and restrictions to be aware of:</span></span>  
  
-   <span data-ttu-id="33c03-129">トレーサー トークンを受信するには、サブスクリプションをアクティブにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="33c03-129">Subscriptions must be active to receive a tracer token.</span></span> <span data-ttu-id="33c03-130">サブスクリプションは、初期化されている場合はアクティブです。</span><span class="sxs-lookup"><span data-stu-id="33c03-130">A subscription is active if it has been initialized.</span></span>  
  
-   <span data-ttu-id="33c03-131">再初期化を行うと、関連するサブスクリプションに対する保留中のトレーサー トークンがすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="33c03-131">Reinitialization removes any pending tracer tokens for the relevant subscriptions.</span></span>  
  
-   <span data-ttu-id="33c03-132">サブスクライバーは、初期同期の完了後に作成されたトレーサー トークンのみを受信します。</span><span class="sxs-lookup"><span data-stu-id="33c03-132">Subscribers only receive tracer tokens that were created after their initial synchronization.</span></span>  
  
-   <span data-ttu-id="33c03-133">レーサ トークンは、再パブリッシュ サブスクライバーからは転送されません。</span><span class="sxs-lookup"><span data-stu-id="33c03-133">Tracer tokens are not forwarded by republishing Subscribers.</span></span>  
  
-   <span data-ttu-id="33c03-134">セカンダリにフェールオーバーした後、レプリケーション モニターは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のパブリッシング インスタンスの名前を調整できません。引き続き、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の元のプライマリ インスタンスの名前を使ってレプリケーション情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="33c03-134">After failover to a secondary, Replication Monitor is unable to adjust the name of the publishing instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and will continue to display replication information under the name of the original primary instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="33c03-135">フェールオーバー後は、トレーサー トークンはレプリケーション モニターを使用して入力できませんが、新しいパブリッシャーで [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して入力されたトレース トークンがレプリケーション モニターに表示されます。</span><span class="sxs-lookup"><span data-stu-id="33c03-135">After failover, a tracer token cannot be entered by using the Replication Monitor, however a tracer token entered on the new publisher by using [!INCLUDE[tsql](../../../includes/tsql-md.md)], is visible in Replication Monitor.</span></span>  
  
##  <a name="using-sql-server-replication-monitor"></a><a name="SSMSProcedure"></a> <span data-ttu-id="33c03-136">SQL Server レプリケーション モニターの使用</span><span class="sxs-lookup"><span data-stu-id="33c03-136">Using SQL Server Replication Monitor</span></span>  
 <span data-ttu-id="33c03-137">レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor](start-the-replication-monitor.md)」 (レプリケーション モニターの開始) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="33c03-137">For information about starting Replication Monitor, see [Start the Replication Monitor](start-the-replication-monitor.md).</span></span>  
  
#### <a name="to-insert-a-tracer-token-and-view-information-on-the-token"></a><span data-ttu-id="33c03-138">トレーサー トークンを挿入してトークンの情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="33c03-138">To insert a tracer token and view information on the token</span></span>  
  
1.  <span data-ttu-id="33c03-139">左ペインでパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="33c03-139">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="33c03-140">**[トレーサー トークン]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="33c03-140">Click the **Tracer Tokens** tab.</span></span>  
  
3.  <span data-ttu-id="33c03-141">**[トレーサーの挿入]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33c03-141">Click **Insert Tracer**.</span></span>  
  
4.  <span data-ttu-id="33c03-142">**[パブリッシャーからディストリビューターまで]** 列、 **[ディストリビューターからサブスクライバーまで]** 列、および **[合計待機時間]** 列で、トレーサー トークンの経過時間を表示します。</span><span class="sxs-lookup"><span data-stu-id="33c03-142">View elapsed time for the tracer token in the following columns: **Publisher to Distributor**, **Distributor to Subscriber**, **Total Latency**.</span></span> <span data-ttu-id="33c03-143">値が**Pending**の場合は、トークンが特定のポイントに到達していないことを示します。</span><span class="sxs-lookup"><span data-stu-id="33c03-143">A value of **Pending** indicates that the token has not reached a given point.</span></span>  
  
#### <a name="to-view-information-on-a-tracer-token-inserted-previously"></a><span data-ttu-id="33c03-144">以前に挿入したトレーサー トークンの情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="33c03-144">To view information on a tracer token inserted previously</span></span>  
  
1.  <span data-ttu-id="33c03-145">左ペインでパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="33c03-145">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="33c03-146">**[トレーサー トークン]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="33c03-146">Click the **Tracer Tokens** tab.</span></span>  
  
3.  <span data-ttu-id="33c03-147">**[挿入された時間]** ボックスで時間を選択します。</span><span class="sxs-lookup"><span data-stu-id="33c03-147">Select a time from the **Time inserted** drop-down list.</span></span>  
  
4.  <span data-ttu-id="33c03-148">**[パブリッシャーからディストリビューターまで]** 列、 **[ディストリビューターからサブスクライバーまで]** 列、および **[合計待機時間]** 列で、トレーサー トークンの経過時間を表示します。</span><span class="sxs-lookup"><span data-stu-id="33c03-148">View elapsed time for the tracer token in the following columns: **Publisher to Distributor**, **Distributor to Subscriber**, **Total Latency**.</span></span> <span data-ttu-id="33c03-149">値が**Pending**の場合は、トークンが特定のポイントに到達していないことを示します。</span><span class="sxs-lookup"><span data-stu-id="33c03-149">A value of **Pending** indicates that the token has not reached a given point.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="33c03-150">トレーサー トークン情報は、ディストリビューション データベースの履歴保持期間の制約を受けるその他の履歴データと同じ期間保持されます。</span><span class="sxs-lookup"><span data-stu-id="33c03-150">Tracer token information is retained for the same time period as other historical data, which is governed by the history retention period of the distribution database.</span></span> <span data-ttu-id="33c03-151">ディストリビューション データベースのプロパティの変更方法の詳細については、「[ディストリビューターとパブリッシャーのプロパティの表示および変更](../view-and-modify-distributor-and-publisher-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="33c03-151">For information about changing distribution database properties, see [View and Modify Distributor and Publisher Properties](../view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="33c03-152">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="33c03-152">Using Transact-SQL</span></span>  
  
#### <a name="to-post-a-tracer-token-to-a-transactional-publication"></a><span data-ttu-id="33c03-153">トレーサー トークンをトランザクション パブリケーションに通知するには</span><span class="sxs-lookup"><span data-stu-id="33c03-153">To post a tracer token to a transactional publication</span></span>  
  
1.  <span data-ttu-id="33c03-154">(省略可) パブリッシャー側のパブリケーション データベースに対して、[sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="33c03-154">(Optional) At the Publisher on the publication database, execute [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> <span data-ttu-id="33c03-155">パブリケーションが存在すること、および状態がアクティブであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="33c03-155">Verify that the publication exists and that the status is active.</span></span>  
  
2.  <span data-ttu-id="33c03-156">(省略可) パブリッシャー側のパブリケーション データベースに対して、[sp_helpsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="33c03-156">(Optional) At the Publisher on the publication database, execute [sp_helpsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).</span></span> <span data-ttu-id="33c03-157">サブスクリプションが存在すること、および状態がアクティブであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="33c03-157">Verify that the subscription exists and that the status is active.</span></span>  
  
3.  <span data-ttu-id="33c03-158">パブリッシャー側のパブリケーション データベースに対して、[sp_posttracertoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql) を実行して、**@publication** を指定します。</span><span class="sxs-lookup"><span data-stu-id="33c03-158">At the Publisher on the publication database, execute [sp_posttracertoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql), specifying **@publication**.</span></span> <span data-ttu-id="33c03-159">Output パラメーターの値を確認し **@tracer_token_id** ます。</span><span class="sxs-lookup"><span data-stu-id="33c03-159">Note the value of the **@tracer_token_id** output parameter.</span></span>  
  
#### <a name="to-determine-latency-and-validate-connections-for-a-transactional-publication"></a><span data-ttu-id="33c03-160">待機時間を決定し、トランザクション パブリケーションの接続を確認するには</span><span class="sxs-lookup"><span data-stu-id="33c03-160">To determine latency and validate connections for a transactional publication</span></span>  
  
1.  <span data-ttu-id="33c03-161">上述の手順を使用して、トレーサー トークンをパブリケーションに通知します。</span><span class="sxs-lookup"><span data-stu-id="33c03-161">Post a tracer token to the publication using the previous procedure.</span></span>  
  
2.  <span data-ttu-id="33c03-162">パブリッシャー側のパブリケーション データベースに対して、**@publication** を指定して、[sp_helptracertokens &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="33c03-162">At the Publisher on the publication database, execute [sp_helptracertokens &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql), specifying **@publication**.</span></span> <span data-ttu-id="33c03-163">パブリケーションに通知されたすべてのトレーサー トークンのリストが返されます。</span><span class="sxs-lookup"><span data-stu-id="33c03-163">This returns a list of all tracer tokens posted to the publication.</span></span> <span data-ttu-id="33c03-164">結果セットの目的の **tracer_id** を確認します。</span><span class="sxs-lookup"><span data-stu-id="33c03-164">Note the desired **tracer_id** in the result set.</span></span>  
  
3.  <span data-ttu-id="33c03-165">パブリッシャー側のパブリケーション データベースで、**@publication** を指定し、**@tracer_id** に手順 2 のトレーサー トークン ID を指定して、[sp_helptracertokenhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="33c03-165">At the Publisher on the publication database, execute [sp_helptracertokenhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql), specifying **@publication** and the tracer token ID from step 2 for **@tracer_id**.</span></span> <span data-ttu-id="33c03-166">選択したトレーサー トークンの待機情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="33c03-166">This returns latency information for the selected tracer token.</span></span>  
  
#### <a name="to-remove-tracer-tokens"></a><span data-ttu-id="33c03-167">トレーサー トークンを削除するには</span><span class="sxs-lookup"><span data-stu-id="33c03-167">To remove tracer tokens</span></span>  
  
1.  <span data-ttu-id="33c03-168">パブリッシャー側のパブリケーション データベースに対して、**@publication** を指定して、[sp_helptracertokens &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="33c03-168">At the Publisher on the publication database, execute [sp_helptracertokens &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql), specifying **@publication**.</span></span> <span data-ttu-id="33c03-169">パブリケーションに通知されたすべてのトレーサー トークンのリストが返されます。</span><span class="sxs-lookup"><span data-stu-id="33c03-169">This returns a list of all tracer tokens posted to the publication.</span></span> <span data-ttu-id="33c03-170">結果セットの削除するトレーサー トークンの **tracer_id** を確認します。</span><span class="sxs-lookup"><span data-stu-id="33c03-170">Note the **tracer_id** for the tracer token to delete in the result set.</span></span>  
  
2.  <span data-ttu-id="33c03-171">パブリッシャー側のパブリケーション データベースで、**@publication** を指定し、**@tracer_id** に手順 2 の削除するトレーサー トークン ID を指定して、[sp_deletetracertokenhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="33c03-171">At the Publisher on the publication database, execute [sp_deletetracertokenhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql), specifying **@publication** and the ID of the tracer to delete from step 2 for **@tracer_id**.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="33c03-172">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="33c03-172">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="33c03-173">次の例では、トレーサー トークン レコードを通知し、返された通知済みトレーサー トークンの ID を使用して待機時間情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="33c03-173">This example posts a tracer token record and uses the returned ID of the posted tracer token to view latency information.</span></span>  
  
 [!code-sql[HowTo#sp_tracertokens](../../../snippets/tsql/SQL15/replication/howto/tsql/createtracertokens.sql#sp_tracertokens)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="33c03-174">レプリケーション管理オブジェクト (RMO) の使用</span><span class="sxs-lookup"><span data-stu-id="33c03-174">Using Replication Management Objects (RMO)</span></span>  
  
#### <a name="to-post-a-tracer-token-to-a-transactional-publication"></a><span data-ttu-id="33c03-175">トレーサー トークンをトランザクション パブリケーションに通知するには</span><span class="sxs-lookup"><span data-stu-id="33c03-175">To post a tracer token to a transactional publication</span></span>  
  
1.  <span data-ttu-id="33c03-176"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="33c03-176">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="33c03-177"><xref:Microsoft.SqlServer.Replication.TransPublication> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="33c03-177">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPublication> class.</span></span>  
  
3.  <span data-ttu-id="33c03-178">パブリケーションの <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> プロパティおよび <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> プロパティを設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成した接続を設定します。</span><span class="sxs-lookup"><span data-stu-id="33c03-178">Set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="33c03-179"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="33c03-179">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="33c03-180">このメソッドが `false` を返す場合、手順 3. でパブリケーション プロパティを不適切に設定したか、パブリケーションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="33c03-180">If this method returns `false`, either the publication properties in step 3 were defined incorrectly or the publication does not exist.</span></span>  
  
5.  <span data-ttu-id="33c03-181"><xref:Microsoft.SqlServer.Replication.TransPublication.PostTracerToken%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="33c03-181">Call the <xref:Microsoft.SqlServer.Replication.TransPublication.PostTracerToken%2A> method.</span></span> <span data-ttu-id="33c03-182">このメソッドは、トレーサー トークンをパブリケーションのトランザクション ログに挿入します。</span><span class="sxs-lookup"><span data-stu-id="33c03-182">This method inserts a tracer token into the publication's transaction log.</span></span>  
  
#### <a name="to-determine-latency-and-validate-connections-for-a-transactional-publication"></a><span data-ttu-id="33c03-183">待機時間を決定し、トランザクション パブリケーションの接続を確認するには</span><span class="sxs-lookup"><span data-stu-id="33c03-183">To determine latency and validate connections for a transactional publication</span></span>  
  
1.  <span data-ttu-id="33c03-184"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、ディストリビューターへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="33c03-184">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="33c03-185"><xref:Microsoft.SqlServer.Replication.PublicationMonitor> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="33c03-185">Create an instance of the <xref:Microsoft.SqlServer.Replication.PublicationMonitor> class.</span></span>  
  
3.  <span data-ttu-id="33c03-186"><xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>、および <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> の各プロパティを設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成した接続を設定します。</span><span class="sxs-lookup"><span data-stu-id="33c03-186">Set the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> properties, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="33c03-187"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="33c03-187">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="33c03-188">このメソッドが `false` を返す場合は、手順 3. のパブリケーション モニター プロパティが正しく定義されていないか、またはパブリケーションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="33c03-188">If this method returns `false`, either the publication monitor properties in step 3 were defined incorrectly or the publication does not exist.</span></span>  
  
5.  <span data-ttu-id="33c03-189"><xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="33c03-189">Call the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> method.</span></span> <span data-ttu-id="33c03-190">返された <xref:System.Collections.ArrayList> オブジェクトを <xref:Microsoft.SqlServer.Replication.TracerToken> オブジェクトの配列にキャストします。</span><span class="sxs-lookup"><span data-stu-id="33c03-190">Cast the returned <xref:System.Collections.ArrayList> object to an array of <xref:Microsoft.SqlServer.Replication.TracerToken> objects.</span></span>  
  
6.  <span data-ttu-id="33c03-191"><xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokenHistory%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="33c03-191">Call the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokenHistory%2A> method.</span></span> <span data-ttu-id="33c03-192">手順 5. のトレーサー トークンに <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> の値を渡します。</span><span class="sxs-lookup"><span data-stu-id="33c03-192">Pass a value of <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> for a tracer token from step 5.</span></span> <span data-ttu-id="33c03-193">これにより、 <xref:System.Data.DataSet> オブジェクトとして選択したトレーサー トークンの待機時間情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="33c03-193">This returns latency information for the selected tracer token as a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="33c03-194">すべてのトレーサー トークン情報が返された場合、パブリッシャーとディストリビューターとの接続、およびディストリビューターとサブスクライバーの接続が両方とも存在し、レプリケーション トポロジは機能しています。</span><span class="sxs-lookup"><span data-stu-id="33c03-194">If all tracer token information is returned, the connection between the Publisher and Distributor and the connection between the Distributor and the Subscriber both exist and the replication topology is functioning.</span></span>  
  
#### <a name="to-remove-tracer-tokens"></a><span data-ttu-id="33c03-195">トレーサー トークンを削除するには</span><span class="sxs-lookup"><span data-stu-id="33c03-195">To remove tracer tokens</span></span>  
  
1.  <span data-ttu-id="33c03-196"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、ディストリビューターへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="33c03-196">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="33c03-197"><xref:Microsoft.SqlServer.Replication.PublicationMonitor> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="33c03-197">Create an instance of the <xref:Microsoft.SqlServer.Replication.PublicationMonitor> class.</span></span>  
  
3.  <span data-ttu-id="33c03-198"><xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>、および <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> の各プロパティを設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成した接続を設定します。</span><span class="sxs-lookup"><span data-stu-id="33c03-198">Set the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> properties, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="33c03-199"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="33c03-199">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="33c03-200">このメソッドが `false` を返す場合は、手順 3. のパブリケーション モニター プロパティが正しく定義されていないか、またはパブリケーションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="33c03-200">If this method returns `false`, either the publication monitor properties in step 3 were defined incorrectly or the publication does not exist.</span></span>  
  
5.  <span data-ttu-id="33c03-201"><xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="33c03-201">Call the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> method.</span></span> <span data-ttu-id="33c03-202">返された <xref:System.Collections.ArrayList> オブジェクトを <xref:Microsoft.SqlServer.Replication.TracerToken> オブジェクトの配列にキャストします。</span><span class="sxs-lookup"><span data-stu-id="33c03-202">Cast the returned <xref:System.Collections.ArrayList> object to an array of <xref:Microsoft.SqlServer.Replication.TracerToken> objects.</span></span>  
  
6.  <span data-ttu-id="33c03-203"><xref:Microsoft.SqlServer.Replication.PublicationMonitor.CleanUpTracerTokenHistory%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="33c03-203">Call the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.CleanUpTracerTokenHistory%2A> method.</span></span> <span data-ttu-id="33c03-204">次の値のいずれかを渡します。</span><span class="sxs-lookup"><span data-stu-id="33c03-204">Pass one of the following values:</span></span>  
  
    -   <span data-ttu-id="33c03-205">手順 5. のトレーサー トークンの <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> 。</span><span class="sxs-lookup"><span data-stu-id="33c03-205">The <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> for a tracer token from step 5.</span></span> <span data-ttu-id="33c03-206">これにより、選択したトークンの情報が削除されます。</span><span class="sxs-lookup"><span data-stu-id="33c03-206">This deletes information for a selected token.</span></span>  
  
    -   <span data-ttu-id="33c03-207"><xref:System.DateTime> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="33c03-207">A <xref:System.DateTime> object.</span></span> <span data-ttu-id="33c03-208">これにより、指定した日時より古いすべてのトークンの情報が削除されます。</span><span class="sxs-lookup"><span data-stu-id="33c03-208">This deletes information for all tokens older than the specified date and time.</span></span>  
  
###  <a name="PShellExample"></a>  
