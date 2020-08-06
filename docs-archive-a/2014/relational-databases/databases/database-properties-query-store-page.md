---
title: '[データベースのプロパティ] ([クエリ ストア] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.databaseproperties.querystore.f1
ms.assetid: da47d75e-291a-4305-acef-4b0aaf5215da
author: stevestein
ms.author: sstein
ms.openlocfilehash: bab0d9b697e9ad9ec4b27f320d26b9b9edb5944e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718224"
---
# <a name="database-properties-query-store-page"></a><span data-ttu-id="7e5ff-102">データベースのプロパティ (クエリのストアのページ)</span><span class="sxs-lookup"><span data-stu-id="7e5ff-102">Database Properties (Query Store Page)</span></span>
  <span data-ttu-id="7e5ff-103">このページにはプリンシパル データベースからアクセスし、これを使用してデータベースのクエリのストアのプロパティを構成および変更します。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-103">Access this page from the principal database, and use it to configure and to modify the properties of the database query store.</span></span> <span data-ttu-id="7e5ff-104">これらのオプションは、 [ALTER DATABASE SET オプション](/sql/t-sql/statements/alter-database-transact-sql-set-options)を使用して構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-104">These options can also be configure by using the [ALTER DATABASE SET options](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span> <span data-ttu-id="7e5ff-105">クエリのストアの詳細については、「 [Monitoring Performance By Using the Query Store](../performance/monitoring-performance-by-using-the-query-store.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-105">For information about the query store, see [Monitoring Performance By Using the Query Store](../performance/monitoring-performance-by-using-the-query-store.md).</span></span>  
  
||  
|-|  
|<span data-ttu-id="7e5ff-106">**適用対象**: [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e5ff-106">**Applies to**: [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].</span></span>|  
  
## <a name="options"></a><span data-ttu-id="7e5ff-107">Options</span><span class="sxs-lookup"><span data-stu-id="7e5ff-107">Options</span></span>  
 <span data-ttu-id="7e5ff-108">有効化</span><span class="sxs-lookup"><span data-stu-id="7e5ff-108">Enable</span></span>  
 <span data-ttu-id="7e5ff-109">クエリのストアを有効化または無効化します。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-109">Enables and disables the query store.</span></span>  
  
 <span data-ttu-id="7e5ff-110">操作モード</span><span class="sxs-lookup"><span data-stu-id="7e5ff-110">Operation Mode</span></span>  
 <span data-ttu-id="7e5ff-111">有効な値は、READ_ONLY、READ_WRITE はします。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-111">Valid values are READ_ONLY and READ_WRITE.</span></span> <span data-ttu-id="7e5ff-112">READ_WRITE モードでは、クエリのストアでクエリ プランとランタイム実行の統計情報が収集および保持されます。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-112">In READ_WRITE mode, the query store collects and persists query plan and runtime execution statistics information.</span></span> <span data-ttu-id="7e5ff-113">READ_ONLY モードでは、クエリのストアから情報を読み取ることができますが、新しい情報は追加されません。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-113">In READ_ONLY mode, information can be read from the query store, but new information is not added.</span></span> <span data-ttu-id="7e5ff-114">クエリのストアの割り当て済み最大領域が不足すると、クエリのストアは操作モードを READ_ONLY にします。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-114">If the maximum allocated space of the query store has been exhausted, the query store will change its operation mode to READ_ONLY.</span></span>  
  
 <span data-ttu-id="7e5ff-115">操作モード (実際)</span><span class="sxs-lookup"><span data-stu-id="7e5ff-115">Operation Mode (Actual)</span></span>  
 <span data-ttu-id="7e5ff-116">クエリのストアの実際の操作モードを取得します。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-116">Gets the actual operation mode of the query store.</span></span>  
  
 <span data-ttu-id="7e5ff-117">操作モード (要求)</span><span class="sxs-lookup"><span data-stu-id="7e5ff-117">Operation Mode (Requested)</span></span>  
 <span data-ttu-id="7e5ff-118">クエリのストアの目的の操作モードを取得、および設定します。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-118">Gets and sets the desired operation mode of the query store.</span></span>  
  
 <span data-ttu-id="7e5ff-119">データ フラッシュ間隔 (分)</span><span class="sxs-lookup"><span data-stu-id="7e5ff-119">Data Flush Interval (Minutes)</span></span>  
 <span data-ttu-id="7e5ff-120">クエリ ストアに書き込まれるデータがディスクに永続化される頻度を決定します。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-120">Determines the frequency at which data written to the query store is persisted to disk.</span></span> <span data-ttu-id="7e5ff-121">パフォーマンスを最適化するため、クエリ ストアで収集したデータは非同期的にディスクに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-121">To optimize for performance, data collected by the query store is asynchronously written to the disk.</span></span> <span data-ttu-id="7e5ff-122">この非同期転送が発生する頻度が構成されます。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-122">The frequency at which this asynchronous transfer occurs is configured.</span></span>  
  
 <span data-ttu-id="7e5ff-123">統計情報の収集間隔</span><span class="sxs-lookup"><span data-stu-id="7e5ff-123">Statistics Collection Interval</span></span>  
 <span data-ttu-id="7e5ff-124">統計情報の収集間隔を取得、および設定します。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-124">Gets and sets the statistics collection interval value.</span></span>  
  
 <span data-ttu-id="7e5ff-125">最大サイズ (MB)</span><span class="sxs-lookup"><span data-stu-id="7e5ff-125">Max Size (MB)</span></span>  
 <span data-ttu-id="7e5ff-126">クエリのストアに割り当てられた合計領域を取得、および設定します。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-126">Gets and sets the total space allocated to the query store.</span></span>  
  
 <span data-ttu-id="7e5ff-127">古いクエリのしきい値 (日)</span><span class="sxs-lookup"><span data-stu-id="7e5ff-127">Stale Query Threshold (Days)</span></span>  
 <span data-ttu-id="7e5ff-128">古いクエリのしきい値を取得、および設定します。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-128">Gets and sets the stale query threshold.</span></span> <span data-ttu-id="7e5ff-129">STALE_QUERY_THRESHOLD_DAYS 引数を構成して、クエリのストア内にデータを保持する日数を指定します。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-129">Configure the STALE_QUERY_THRESHOLD_DAYS argument to specify the number of days to retain data in the query store.</span></span>  
  
 <span data-ttu-id="7e5ff-130">クエリ データの消去</span><span class="sxs-lookup"><span data-stu-id="7e5ff-130">Purge Query Data</span></span>  
 <span data-ttu-id="7e5ff-131">クエリ ストアの内容を削除します。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-131">Removes the contents of the query store.</span></span>  
  
 <span data-ttu-id="7e5ff-132">円グラフ</span><span class="sxs-lookup"><span data-stu-id="7e5ff-132">Pie Charts</span></span>  
 <span data-ttu-id="7e5ff-133">左側のグラフには、ディスク上のデータベース ファイルの合計消費量、およびクエリのストアのデータを格納するファイルの部分が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-133">The left chart shows the total database file consumption on the disk, and the portion of the file which is filled with the query store data.</span></span>  
  
 <span data-ttu-id="7e5ff-134">右側のグラフには、現在使用されているクエリのストアのクォータの部分が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-134">The right chart shows the portion of the query store quota which is currently used up.</span></span> <span data-ttu-id="7e5ff-135">クォータは、左側のグラフには表示されないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-135">Note that the quota is not shown in the left chart.</span></span> <span data-ttu-id="7e5ff-136">クォータが、データベースの現在のサイズを超える場合があります。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-136">The quota may exceed the current size of the database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e5ff-137">解説</span><span class="sxs-lookup"><span data-stu-id="7e5ff-137">Remarks</span></span>  
 <span data-ttu-id="7e5ff-138">クエリのストアの機能により、クエリ プランの選択やパフォーマンスに関する洞察が DBA に提供されます。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-138">The query store feature provides DBAs with insight on query plan choice and performance.</span></span> <span data-ttu-id="7e5ff-139">これにより、クエリ プランの変更によって生じるパフォーマンスの違いがすばやくわかるようになり、パフォーマンス上のトラブルシューティングを簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-139">It simplifies performance troubleshooting by enabling you to quickly find performance differences caused by changes in query plans.</span></span> <span data-ttu-id="7e5ff-140">この機能により、クエリ、プラン、ランタイム統計情報の履歴が自動的にキャプチャされ、レビュー用に保持されます。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-140">The feature automatically captures a history of queries, plans, and runtime statistics, and retains these for your review.</span></span> <span data-ttu-id="7e5ff-141">データは時間枠で区分されるため、データベースの使用パターンを表示して、サーバー上でクエリ プランが変わった時点を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-141">It separates data by time windows, allowing you to see database usage patterns and understand when query plan changes happened on the server.</span></span> <span data-ttu-id="7e5ff-142">クエリのストアは、クエリのストアのデータベース プロパティ ページを使用するか、 [ALTER DATABASE SET](/sql/t-sql/statements/alter-database-transact-sql-set-options) オプションを使用して構成できます。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-142">The query store can be configured by using this query store database property page, or by using the [ALTER DATABASE SET](/sql/t-sql/statements/alter-database-transact-sql-set-options) option.</span></span> <span data-ttu-id="7e5ff-143">クエリのストアは、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ダイアログ ボックスを使用して情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-143">The query store presents information by using a [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] dialog box.</span></span> <span data-ttu-id="7e5ff-144">クエリのストアの詳細については、「 [Monitoring Performance By Using the Query Store](../performance/monitoring-performance-by-using-the-query-store.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7e5ff-144">For more information about query store, see [Monitoring Performance By Using the Query Store](../performance/monitoring-performance-by-using-the-query-store.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e5ff-145">参照</span><span class="sxs-lookup"><span data-stu-id="7e5ff-145">See Also</span></span>  
 <span data-ttu-id="7e5ff-146">[クエリ ストアのストアド プロシージャ &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7e5ff-146">[Query Store Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="7e5ff-147">クエリ ストアのカタログ ビュー &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7e5ff-147">Query Store Catalog Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/query-store-catalog-views-transact-sql)  
  
  
