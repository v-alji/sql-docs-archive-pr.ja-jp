---
title: 競合回避モジュールの選択 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- default conflict resolver
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: b7dec3fa-d9d9-409d-b946-f9b9a3202829
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0db289e923cab72bf175b172f039ea228c991110
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633085"
---
# <a name="choose-a-resolver"></a><span data-ttu-id="e519b-102">競合回避モジュールの選択</span><span class="sxs-lookup"><span data-stu-id="e519b-102">Choose a Resolver</span></span>
  <span data-ttu-id="e519b-103">競合回避モジュールを選択するときには、アプリケーションでの競合解決の重要性、および既定の優先度ベースの競合回避モジュールを使用できるかどうか、アーティクル競合回避モジュールを使用する必要があるかどうかを考慮します。</span><span class="sxs-lookup"><span data-stu-id="e519b-103">When choosing a resolver, consider the importance of conflict resolution in your application and whether you can use the default priority-based conflict resolver or need to use an article resolver.</span></span>  
  
 <span data-ttu-id="e519b-104">データをパーティション分割するときに、複数のユーザーが同じパーティションに書き込まず、レプリケーション トポロジが基本構成 (1 つのパブリッシャーといくつかのサブスクライバー) に比較的従っている場合、競合は非常にまれであるか、またはまったく発生しません。</span><span class="sxs-lookup"><span data-stu-id="e519b-104">If your data is partitioned without multiple users writing to the same partitions, and your replication topology is relatively basic (one Publisher and a few Subscribers), conflicts should be rare or nonexistent.</span></span> <span data-ttu-id="e519b-105">このような環境では、複雑な競合解決方法が不要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e519b-105">In these environments, you probably do not need a complex conflict resolution strategy.</span></span> <span data-ttu-id="e519b-106">競合の解決に既定の設定を使用する方法、クライアント サブスクリプションを使用する方法、または最初の変更を優先する方法をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e519b-106">A strategy using the default settings for conflict resolution, using client subscriptions and a first change in wins policy, is recommended.</span></span> <span data-ttu-id="e519b-107">トポロジがより複雑な場合 (再パブリッシュ サブスクライバーを使用するなど) は、サーバー サブスクリプションに特定の優先度を指定する方が適切です。</span><span class="sxs-lookup"><span data-stu-id="e519b-107">If the topology is more complex (using republishing Subscribers, for example), server subscriptions with specific priorities might be more appropriate.</span></span>  
  
 <span data-ttu-id="e519b-108">アーティクル競合回避モジュールは、ビジネス上のニーズにより既定の競合回避モジュールより細かく調整されたソリューションが必要な場合にお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e519b-108">An article resolver is recommended if your business needs require a more finely tuned solution than is available with the default resolver.</span></span> <span data-ttu-id="e519b-109">アーティクル競合回避モジュールを使用する場合は、ビジネス ロジック ハンドラーを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e519b-109">If you choose to use an article resolver, it is recommended that you use a business logic handler.</span></span> <span data-ttu-id="e519b-110">詳細については、「[Execute Business Logic During Merge Synchronization](execute-business-logic-during-merge-synchronization.md)」(マージ同期中のビジネス ロジックの実行) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e519b-110">For more information, see [Execute Business Logic During Merge Synchronization](execute-business-logic-during-merge-synchronization.md).</span></span>  
  
 <span data-ttu-id="e519b-111">最終的に、既定の競合回避モジュールとアーティクル競合回避モジュールのどちらを使用するかは、アプリケーションのデータおよびビジネス ロジックのニーズによって異なります。</span><span class="sxs-lookup"><span data-stu-id="e519b-111">Ultimately, choosing whether to use the default resolver or an article resolver should be based on the data and the business logic needs of the application.</span></span> <span data-ttu-id="e519b-112">たとえば、異なるサブスクライバーでパーティション分割されていないテーブルに顧客の順位データを入力する従業員がさまざまなジョブ カテゴリ (支社長、工程管理者、販売スタッフ) にまたがっており、ジョブ カテゴリによってデータの優先度が決まるとします。</span><span class="sxs-lookup"><span data-stu-id="e519b-112">For example, consider employees who enter customer ranking data into a set of non-partitioned tables at different Subscribers; the employees span various job categories (branch managers, line managers, sales staff), and job category determines whose data should be given priority.</span></span> <span data-ttu-id="e519b-113">この場合、アーティクル競合回避モジュールを構築できます。このモジュールは、競合発生時に優先されるデータの判別に、アーティクルから得られたジョブ カテゴリ データを使用します。</span><span class="sxs-lookup"><span data-stu-id="e519b-113">In this case, an article resolver can be built that uses job category data from the article to determine the winner if a conflict occurs.</span></span>  
  
 <span data-ttu-id="e519b-114">競合がある程度の頻度で発生する場合、以下のように、競合解決方法の実装時に考慮しなければならないことがあります。</span><span class="sxs-lookup"><span data-stu-id="e519b-114">If conflicts are likely to occur with some frequency, here are the most important decisions you should consider when implementing a conflict resolution strategy.</span></span>  
  
|<span data-ttu-id="e519b-115">競合解決に際して考慮すべき問題</span><span class="sxs-lookup"><span data-stu-id="e519b-115">Conflict resolution issue</span></span>|<span data-ttu-id="e519b-116">推奨</span><span class="sxs-lookup"><span data-stu-id="e519b-116">Recommendation</span></span>|  
|-------------------------------|--------------------|  
|<span data-ttu-id="e519b-117">異なるジョブ カテゴリのユーザーに対して異なる優先度が必要な場合</span><span class="sxs-lookup"><span data-stu-id="e519b-117">Different categories of users require different priority values.</span></span>|<span data-ttu-id="e519b-118">既定の競合回避モジュールを使用して、異なる優先度値を持つサーバー サブスクリプションを作成する。</span><span class="sxs-lookup"><span data-stu-id="e519b-118">Use the default resolver and create server subscriptions with different priority values.</span></span><br /><br /> <span data-ttu-id="e519b-119">または</span><span class="sxs-lookup"><span data-stu-id="e519b-119">-Or-</span></span><br /><br /> <span data-ttu-id="e519b-120">アーティクル内の権限値の列を認識するアーティクル競合回避モジュールを使用して、競合を解決する。</span><span class="sxs-lookup"><span data-stu-id="e519b-120">Use an article resolver that recognizes an authority value column in the article to help resolve a conflict.</span></span>|  
|<span data-ttu-id="e519b-121">最初に変更されたデータが優先される競合解決方法が必要な場合</span><span class="sxs-lookup"><span data-stu-id="e519b-121">First change in wins conflict solution wanted.</span></span>|<span data-ttu-id="e519b-122">既定の競合回避モジュールを使用して、クライアント サブスクリプションを作成する。</span><span class="sxs-lookup"><span data-stu-id="e519b-122">Use the default resolver and create client subscriptions.</span></span>|  
|<span data-ttu-id="e519b-123">同じ行に対する変更の競合がない限り、複数のユーザーが同じデータ行を変更することを認める場合</span><span class="sxs-lookup"><span data-stu-id="e519b-123">Multiple users changing the same data row is acceptable, as long as no conflicting changes are made to the same column.</span></span>|<span data-ttu-id="e519b-124">既定の競合回避モジュール、または列レベルの追跡を有効にしたアーティクル競合回避モジュールを使用する。</span><span class="sxs-lookup"><span data-stu-id="e519b-124">Use either the default resolver or an article resolver with column-level tracking enabled.</span></span>|  
|<span data-ttu-id="e519b-125">行の値に対して複数の変更が発生したときに競合のフラグを付ける場合</span><span class="sxs-lookup"><span data-stu-id="e519b-125">Flag multiple changes to any value in a row as a conflict.</span></span>|<span data-ttu-id="e519b-126">既定の競合回避モジュール、または行レベルの追跡を有効にしたアーティクル競合回避モジュールを使用する。</span><span class="sxs-lookup"><span data-stu-id="e519b-126">Use either the default resolver or an article resolver with row-level tracking.</span></span>|  
|<span data-ttu-id="e519b-127">論理レコードの値に対して複数の変更が発生したときに競合のフラグを付ける場合</span><span class="sxs-lookup"><span data-stu-id="e519b-127">Flag multiple changes to any value in a logical record as a conflict.</span></span>|<span data-ttu-id="e519b-128">論理レコード レベルの追跡を有効にした既定の競合回避モジュールを使用する (論理レコード機能では、カスタム競合回避モジュールまたはビジネス ロジック ハンドラーはサポートされていません)。</span><span class="sxs-lookup"><span data-stu-id="e519b-128">Use the default resolver with logical record-level tracking (the logical records feature does not support custom resolvers or business logic handlers).</span></span>|  
|<span data-ttu-id="e519b-129">競合の結果データが元の競合データと異なっている必要がある場合</span><span class="sxs-lookup"><span data-stu-id="e519b-129">Conflict outcome data needs to be different from original conflict data.</span></span>|<span data-ttu-id="e519b-130">新しい値を計算するアーティクル競合回避モジュールを使用する。</span><span class="sxs-lookup"><span data-stu-id="e519b-130">Use an article resolver that calculates new values.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e519b-131">参照</span><span class="sxs-lookup"><span data-stu-id="e519b-131">See Also</span></span>  
 <span data-ttu-id="e519b-132">[Detecting and Resolving Conflicts in Logical Records](advanced-merge-replication-conflict-resolving-in-logical-record.md) </span><span class="sxs-lookup"><span data-stu-id="e519b-132">[Detecting and Resolving Conflicts in Logical Records](advanced-merge-replication-conflict-resolving-in-logical-record.md) </span></span>  
 <span data-ttu-id="e519b-133">[Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="e519b-133">[Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="e519b-134">データの再パブリッシュ</span><span class="sxs-lookup"><span data-stu-id="e519b-134">Republish Data</span></span>](../republish-data.md)  
  
  
