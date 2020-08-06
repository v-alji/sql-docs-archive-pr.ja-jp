---
title: MSSQL_REPL027183 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL027183 error
ms.assetid: 52c271ac-1a0e-43d5-85d4-35886d1efd32
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4484318cd6ec6ff4f0b201be69dc9b7544dd2c2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741794"
---
# <a name="mssql_repl027183"></a><span data-ttu-id="f599f-102">MSSQL_REPL027183</span><span class="sxs-lookup"><span data-stu-id="f599f-102">MSSQL_REPL027183</span></span>
    
## <a name="message-details"></a><span data-ttu-id="f599f-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="f599f-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f599f-104">製品名</span><span class="sxs-lookup"><span data-stu-id="f599f-104">Product Name</span></span>|<span data-ttu-id="f599f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f599f-105">SQL Server</span></span>|  
|<span data-ttu-id="f599f-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="f599f-106">Event ID</span></span>|<span data-ttu-id="f599f-107">27183</span><span class="sxs-lookup"><span data-stu-id="f599f-107">27183</span></span>|  
|<span data-ttu-id="f599f-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="f599f-108">Event Source</span></span>|<span data-ttu-id="f599f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f599f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f599f-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f599f-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="f599f-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="f599f-111">Symbolic Name</span></span>||  
|<span data-ttu-id="f599f-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="f599f-112">Message Text</span></span>|<span data-ttu-id="f599f-113">マージ処理で、パラメーター化された行フィルターを使用して、アーティクル内の変更情報を列挙できませんでした。</span><span class="sxs-lookup"><span data-stu-id="f599f-113">The merge process failed to enumerate changes in articles with parameterized row filters.</span></span> <span data-ttu-id="f599f-114">このエラーが継続して発生する場合、このプロセスのクエリ タイムアウト値を増やし、パブリケーションの保有期間を減少し、パブリッシュされたテーブルのインデックスを強化してください。</span><span class="sxs-lookup"><span data-stu-id="f599f-114">If this failure continues, increase the query timeout for this process, reduce the retention period for the publication, and improve indexes on published tables.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f599f-115">説明</span><span class="sxs-lookup"><span data-stu-id="f599f-115">Explanation</span></span>  
 <span data-ttu-id="f599f-116">このエラーは、フィルター選択されたパブリケーションでの変更を処理中に、マージ エージェント タイムアウトになると発生します。</span><span class="sxs-lookup"><span data-stu-id="f599f-116">This error is raised if a Merge Agent timeout occurs while processing changes in a filtered publication.</span></span> <span data-ttu-id="f599f-117">このタイムアウトは、次のいずれかの問題点により生じた可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f599f-117">The timeout might be caused by one of the following issues:</span></span>  
  
-   <span data-ttu-id="f599f-118">事前計算済みパーティションの最適化の未使用</span><span class="sxs-lookup"><span data-stu-id="f599f-118">Not using the precomputed partitions optimization.</span></span>  
  
-   <span data-ttu-id="f599f-119">フィルター選択に使用される列のインデックスの断片化</span><span class="sxs-lookup"><span data-stu-id="f599f-119">Index fragmentation on columns used for filtering.</span></span>  
  
-   <span data-ttu-id="f599f-120">**MSmerge_tombstone**、 **MSmerge_contents**、 **MSmerge_genhistory**などの、大規模なマージ メタデータ テーブル</span><span class="sxs-lookup"><span data-stu-id="f599f-120">Large merge metadata tables, such as **MSmerge_tombstone**, **MSmerge_contents**, and **MSmerge_genhistory**.</span></span>  
  
-   <span data-ttu-id="f599f-121">一意キーで結合されていないフィルター選択されたテーブルや多くのテーブルを含む結合フィルター</span><span class="sxs-lookup"><span data-stu-id="f599f-121">Filtered tables that are not joined on a unique key and join filters that involve a large number of tables.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f599f-122">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="f599f-122">User Action</span></span>  
 <span data-ttu-id="f599f-123">この問題を解決するには:</span><span class="sxs-lookup"><span data-stu-id="f599f-123">To resolve the issue:</span></span>  
  
-   <span data-ttu-id="f599f-124">マージ エージェントの **-QueryTimeOut** パラメーターの値を大きくし、エラーの原因となっている根本的な問題に対処する間、処理を継続できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f599f-124">Increase the value of the **-QueryTimeOut** parameter for the Merge Agent to allow processing to continue while you address the underlying issues causing the error.</span></span> <span data-ttu-id="f599f-125">エージェント パラメーターは、エージェント プロファイルおよびコマンド ラインで指定できます。</span><span class="sxs-lookup"><span data-stu-id="f599f-125">Agent parameters can be specified in agent profiles and on the command line.</span></span> <span data-ttu-id="f599f-126">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f599f-126">For more information, see:</span></span>  
  
    -   [<span data-ttu-id="f599f-127">レプリケーション エージェント プロファイルの操作</span><span class="sxs-lookup"><span data-stu-id="f599f-127">Work with Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
    -   [<span data-ttu-id="f599f-128">レプリケーション エージェント コマンド プロンプト パラメーターを表示および変更する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="f599f-128">View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;</span></span>](agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   <span data-ttu-id="f599f-129">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md)に割り当てるメモリの最大容量と最小容量を設定する。</span><span class="sxs-lookup"><span data-stu-id="f599f-129">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
-   <span data-ttu-id="f599f-130">可能であれば、事前計算済みパーティションの最適化を使用します。</span><span class="sxs-lookup"><span data-stu-id="f599f-130">Use the precomputed partitions optimization if possible.</span></span> <span data-ttu-id="f599f-131">既定では、この最適化は、多くのパブリケーションの要件が満たされている場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="f599f-131">This optimization is used by default if a number of publication requirements are met.</span></span> <span data-ttu-id="f599f-132">これらの要件の詳細については、「[事前計算済みパーティションによるパラメーター化されたフィルターのパフォーマンス最適化](merge/parameterized-filters-optimize-for-precomputed-partitions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f599f-132">For more information about these requirements, see [Optimize Parameterized Filter Performance with Precomputed Partitions](merge/parameterized-filters-optimize-for-precomputed-partitions.md).</span></span> <span data-ttu-id="f599f-133">パブリケーションがこれらの要件を満たしていない場合は、パブリケーションを再設計することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="f599f-133">If the publication does not meet these requirements, consider redesigning the publication.</span></span>  
  
-   <span data-ttu-id="f599f-134">パブリケーションの保有期間をできる限り低い設定に指定します。保有期間に達するまで、レプリケーションはパブリケーション データベースおよびサブスクリプション データベースでメタデータをクリーンアップできません。</span><span class="sxs-lookup"><span data-stu-id="f599f-134">Specify the lowest setting possible for the publication retention period, because replication cannot clean up metadata in the publication and subscription databases until the retention period is reached.</span></span> <span data-ttu-id="f599f-135">詳細については、「 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f599f-135">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
-   <span data-ttu-id="f599f-136">マージ レプリケーションのメンテナンスの一環として、マージ レプリケーションに関連付けられたシステム テーブル **MSmerge_contents**、 **MSmerge_genhistory**、 **MSmerge_tombstone**、 **MSmerge_current_partition_mappings**、および **MSmerge_past_partition_mappings**の増大を必要に応じて確認します。</span><span class="sxs-lookup"><span data-stu-id="f599f-136">As part of maintenance for merge replication, occasionally check the growth of the system tables associated with merge replication: **MSmerge_contents**, **MSmerge_genhistory**, and **MSmerge_tombstone**, **MSmerge_current_partition_mappings**, and **MSmerge_past_partition_mappings**.</span></span> <span data-ttu-id="f599f-137">定期的にこれらのテーブルのインデックスを再設定します。</span><span class="sxs-lookup"><span data-stu-id="f599f-137">Periodically re-index these tables.</span></span> <span data-ttu-id="f599f-138">詳細については、「 [インデックスの再編成と再構築](../indexes/indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f599f-138">For more information, see [Reorganize and Rebuild Indexes](../indexes/indexes.md).</span></span>  
  
-   <span data-ttu-id="f599f-139">フィルター選択に使用する列のインデックスが適切であることを確認し、必要に応じてインデックスを再構築します。</span><span class="sxs-lookup"><span data-stu-id="f599f-139">Ensure that columns used for filtering are properly indexed and rebuild such indexes if necessary.</span></span> <span data-ttu-id="f599f-140">詳細については、「 [インデックスの再編成と再構築](../indexes/indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f599f-140">For more information, see [Reorganize and Rebuild Indexes](../indexes/indexes.md).</span></span>  
  
-   <span data-ttu-id="f599f-141">一意な列に基づく結合フィルターの **join_unique_key** プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="f599f-141">Set the **join_unique_key** property for join filters that are based on unique columns.</span></span> <span data-ttu-id="f599f-142">詳しくは、「 [Join Filters](merge/join-filters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f599f-142">For more information, see [Join Filters](merge/join-filters.md).</span></span>  
  
-   <span data-ttu-id="f599f-143">結合フィルター階層のテーブル数を制限します。</span><span class="sxs-lookup"><span data-stu-id="f599f-143">Limit the number of tables in the join filter hierarchy.</span></span> <span data-ttu-id="f599f-144">テーブルが 5 つ以上の結合フィルターを生成する場合は、小さなテーブル、変更されないテーブル、プライマリ参照テーブルはフィルター選択しないという別の解決策を検討してください。</span><span class="sxs-lookup"><span data-stu-id="f599f-144">If you are generating join filters of five or more tables, consider other solutions: do not filter tables that are small, not subject to change, or are primarily lookup tables.</span></span> <span data-ttu-id="f599f-145">結合フィルターは、サブスクリプション間でパーティション分割する必要のあるテーブル間でのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="f599f-145">Use join filters only between tables that must be partitioned among subscriptions.</span></span>  
  
-   <span data-ttu-id="f599f-146">同期を行うまでの間はフィルター選択されたテーブルへの変更を少なくするか、マージ エージェントをより頻繁に実行します。</span><span class="sxs-lookup"><span data-stu-id="f599f-146">Make a smaller number of changes on filtered tables between synchronizations, or run the Merge Agent more frequently.</span></span> <span data-ttu-id="f599f-147">同期処理のスケジュール設定の詳細については、「 [Specify Synchronization Schedules](specify-synchronization-schedules.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f599f-147">For more information about setting synchronization schedules, see [Specify Synchronization Schedules](specify-synchronization-schedules.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f599f-148">参照</span><span class="sxs-lookup"><span data-stu-id="f599f-148">See Also</span></span>  
 [<span data-ttu-id="f599f-149">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="f599f-149">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
