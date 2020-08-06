---
title: セマンティクス検索の管理および監視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], managing
- semantic search [SQL Server], monitoring
ms.assetid: eb5c3b29-da70-42aa-aa97-7d35a3f1eb98
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 16e3af1d37f177dfe6d4e0cb090e7b8b0a4988d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717679"
---
# <a name="manage-and-monitor-semantic-search"></a><span data-ttu-id="abc06-102">セマンティクス検索の管理および監視</span><span class="sxs-lookup"><span data-stu-id="abc06-102">Manage and Monitor Semantic Search</span></span>
  <span data-ttu-id="abc06-103">セマンティック インデックス作成プロセスと、インデックスの管理および監視に関連するタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="abc06-103">Describes the process of semantic indexing and the tasks related to managing and monitoring the indexes.</span></span>  
  
##  <a name="how-to-check-the-status-of-semantic-indexing"></a><a name="HowToMonitorStatus"></a><span data-ttu-id="abc06-104">方法: セマンティックインデックス作成の状態を確認する</span><span class="sxs-lookup"><span data-stu-id="abc06-104">How To: Check the Status of Semantic Indexing</span></span>  
 <span data-ttu-id="abc06-105">**セマンティック インデックス作成の最初のフェーズは完了していますか?**</span><span class="sxs-lookup"><span data-stu-id="abc06-105">**Is the first phase of semantic indexing complete?**</span></span>  
 <span data-ttu-id="abc06-106">動的管理ビュー [sys.dm_fts_index_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql) に対してクエリを実行し、**status** 列と **status_description** 列を確認します。</span><span class="sxs-lookup"><span data-stu-id="abc06-106">Query the dynamic management view, [sys.dm_fts_index_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql), and check the **status** and **status_description** columns.</span></span>  
  
 <span data-ttu-id="abc06-107">インデックス作成の最初のフェーズでは、フルテキスト キーワード インデックスおよびセマンティック キー フレーズ インデックスの作成のほか、ドキュメンの類似性データの抽出が行われます。</span><span class="sxs-lookup"><span data-stu-id="abc06-107">The first phase of indexing includes the population of the full-text keyword index and the semantic key phrase index, as well as the extraction of document similarity data.</span></span>  
  
```sql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_index_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
 <span data-ttu-id="abc06-108">**セマンティック インデックス作成の 2 番目のフェーズは完了していますか?**</span><span class="sxs-lookup"><span data-stu-id="abc06-108">**Is the second phase of semantic indexing complete?**</span></span>  
 <span data-ttu-id="abc06-109">動的管理ビュー [sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql) に対してクエリを実行し、**status** 列と **status_description** 列を確認します。</span><span class="sxs-lookup"><span data-stu-id="abc06-109">Query the dynamic management view, [sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql), and check the **status** and **status_description** columns..</span></span>  
  
 <span data-ttu-id="abc06-110">インデックス作成の 2 番目のフェーズには、ドキュメントの類似性に関するセマンティック インデックスの作成が含まれます。</span><span class="sxs-lookup"><span data-stu-id="abc06-110">The second phase of indexing includes the population of the semantic document similarity index.</span></span>  
  
```wql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_semantic_similarity_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
##  <a name="how-to-check-the-size-of-the-semantic-indexes"></a><a name="HowToCheckSize"></a><span data-ttu-id="abc06-111">方法: セマンティックインデックスのサイズを確認する</span><span class="sxs-lookup"><span data-stu-id="abc06-111">How To: Check the Size of the Semantic Indexes</span></span>  
 <span data-ttu-id="abc06-112">**セマンティック キー フレーズ インデックスまたはドキュメントの類似性に関するセマンティック インデックスの論理サイズは?**</span><span class="sxs-lookup"><span data-stu-id="abc06-112">**What is the logical size of a semantic key phrase index or a semantic document similarity index?**</span></span>  
 <span data-ttu-id="abc06-113">動的管理ビュー [sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql) に対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="abc06-113">Query the dynamic management view, [sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql).</span></span>  
  
 <span data-ttu-id="abc06-114">論理サイズは、インデックス ページの数で表示されます。</span><span class="sxs-lookup"><span data-stu-id="abc06-114">The logical size is displayed in number of index pages.</span></span>  
  
```sql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_db_fts_index_physical_stats WHERE object_id = OBJECT_ID('table_name')  
GO  
```  
  
 <span data-ttu-id="abc06-115">**フルテキスト カタログのフルテキスト インデックスとセマンティック インデックスの合計サイズは?**</span><span class="sxs-lookup"><span data-stu-id="abc06-115">**What is the total size of the full-text and semantic indexes for a full-text catalog?**</span></span>  
 <span data-ttu-id="abc06-116">[FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) メタデータ関数の **IndexSize** プロパティに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="abc06-116">Query the **IndexSize** property of the [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) metadata function.</span></span>  
  
```sql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'IndexSize')  
GO  
```  
  
 <span data-ttu-id="abc06-117">**フルテキスト カタログのフルテキスト インデックスおよびセマンティック インデックスでインデックス化されているアイテム数は?**</span><span class="sxs-lookup"><span data-stu-id="abc06-117">**How many items are indexed in the full-text and semantic indexes for a full-text catalog?**</span></span>  
 <span data-ttu-id="abc06-118">[FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) メタデータ関数の **ItemCount** プロパティに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="abc06-118">Query the **ItemCount** property of the [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) metadata function.</span></span>  
  
```sql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'ItemCount')  
GO  
```  
  
##  <a name="how-to-force-the-population-of-the-semantic-indexes"></a><a name="HowToForcePopulation"></a><span data-ttu-id="abc06-119">方法: セマンティックインデックスの作成を強制する</span><span class="sxs-lookup"><span data-stu-id="abc06-119">How To: Force the Population of the Semantic Indexes</span></span>  
 <span data-ttu-id="abc06-120">START/STOP/PAUSE 句または RESUME POPULATION 句を使用して、フルテキスト インデックスおよびセマンティック インデックスを強制的に作成できます (これらの句の構文と動作については、フルテキスト インデックスに関する説明に示されています)。</span><span class="sxs-lookup"><span data-stu-id="abc06-120">You can force the population of full-text and semantic indexes by using the START/STOP/PAUSE or RESUME POPULATION clause with the same syntax and behavior that is described for full-text indexes.</span></span> <span data-ttu-id="abc06-121">詳細については、「[ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)」および「[フルテキスト インデックスの作成](../indexes/indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abc06-121">For more information, see [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) and [Populate Full-Text Indexes](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="abc06-122">セマンティック インデックス作成はフルテキスト インデックス作成に依存しているため、セマンティック インデックスは関連するフルテキスト インデックスが作成されたときにのみ作成されます。</span><span class="sxs-lookup"><span data-stu-id="abc06-122">Since semantic indexing is dependent on full-text indexing, semantic indexes are only populated when the associated full-text indexes are populated.</span></span>  
  
 <span data-ttu-id="abc06-123">**例: フルテキスト インデックスとセマンティック インデックスの完全作成を開始する**</span><span class="sxs-lookup"><span data-stu-id="abc06-123">**Example: Start a full population of full-text and semantic indexes**</span></span>  
  
 <span data-ttu-id="abc06-124">次の例では、AdventureWorks2012 サンプル データベースの **Production.Document** テーブルの既存のフルテキスト インデックスを変更することにより、フルテキスト インデックスとセマンティック インデックスの両方の完全作成を開始します。</span><span class="sxs-lookup"><span data-stu-id="abc06-124">The following example starts full population of both full-text and semantic indexes by altering an existing full-text index on the **Production.Document** table in the AdventureWorks2012 sample database.</span></span>  
  
```vb  
USE AdventureWorks2012  
GO  
  
ALTER FULLTEXT INDEX ON Production.Document  
    START FULL POPULATION  
GO  
```  
  
##  <a name="how-to-disable-or-re-enable-semantic-indexing"></a><a name="HowToDisableIndexing"></a><span data-ttu-id="abc06-125">方法: セマンティックインデックス作成を無効化または再有効化する</span><span class="sxs-lookup"><span data-stu-id="abc06-125">How To: Disable or Re-enable Semantic Indexing</span></span>  
 <span data-ttu-id="abc06-126">ENABLE/DISABLE 句を使用して、フルテキスト インデックスまたはセマンティック インデックスの作成を有効または無効にすることができます (これらの句の構文と動作については、フルテキスト インデックスに関する説明に示されています)。</span><span class="sxs-lookup"><span data-stu-id="abc06-126">You can enable or disable full-text or semantic indexing by using the ENABLE/DISABLE clause with the same syntax and behavior that is described for full-text indexes.</span></span> <span data-ttu-id="abc06-127">詳細については、「 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abc06-127">For more information, see [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).</span></span>  
  
 <span data-ttu-id="abc06-128">セマンティック インデックスの作成が無効化または中断された後でもセマンティック データに対するクエリは正常に動作し、以前にインデックスが作成されたデータを返します。</span><span class="sxs-lookup"><span data-stu-id="abc06-128">When semantic indexing is disabled and suspended, queries over semantic data continue to work successfully and to return previously indexed data.</span></span> <span data-ttu-id="abc06-129">この動作は、フルテキスト検索の動作と一致しません。</span><span class="sxs-lookup"><span data-stu-id="abc06-129">This behavior is not consistent with the behavior of Full-Text Search.</span></span>  
  
```sql  
-- To disable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name DISABLE  
GO  
  
-- To re-enable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name ENABLE  
GO  
```  
  
##  <a name="phases-of-semantic-indexing"></a><a name="SemanticIndexing"></a><span data-ttu-id="abc06-130">セマンティックインデックス作成のフェーズ</span><span class="sxs-lookup"><span data-stu-id="abc06-130">Phases of Semantic Indexing</span></span>  
 <span data-ttu-id="abc06-131">セマンティック検索では、セマンティック検索が有効なそれぞれの列に対して、次の 2 種類のデータに関するインデックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="abc06-131">Semantic Search indexes two kinds of data for each column on which it is enabled:</span></span>  
  
1.  <span data-ttu-id="abc06-132">**キー フレーズ**</span><span class="sxs-lookup"><span data-stu-id="abc06-132">**Key phrases**</span></span>  
  
2.  <span data-ttu-id="abc06-133">**ドキュメントの類似性**</span><span class="sxs-lookup"><span data-stu-id="abc06-133">**Document similarity**</span></span>  
  
 <span data-ttu-id="abc06-134">セマンティック インデックス作成は、フルテキスト インデックス作成との関連において 2 つのフェーズで行われます。</span><span class="sxs-lookup"><span data-stu-id="abc06-134">Semantic indexing occurs in two phases, in conjunction with full-text indexing:</span></span>  
  
1.  <span data-ttu-id="abc06-135">**フェーズ 1:**</span><span class="sxs-lookup"><span data-stu-id="abc06-135">**Phase 1**.</span></span> <span data-ttu-id="abc06-136">フルテキスト キーワード インデックスとセマンティック キー フレーズ インデックスが同時に作成されます。</span><span class="sxs-lookup"><span data-stu-id="abc06-136">The full-text keyword index and the semantic key phrase index are populated in parallel at the same time.</span></span> <span data-ttu-id="abc06-137">ドキュメントの類似性に関するインデックスを作成するのに必要なデータもこのとき抽出されます。</span><span class="sxs-lookup"><span data-stu-id="abc06-137">The data required to index document similarity is also extracted at this time.</span></span>  
  
2.  <span data-ttu-id="abc06-138">**フェーズ 2:**</span><span class="sxs-lookup"><span data-stu-id="abc06-138">**Phase 2**.</span></span> <span data-ttu-id="abc06-139">ドキュメントの類似性に関するセマンティック インデックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="abc06-139">The semantic document similarity index is then populated.</span></span> <span data-ttu-id="abc06-140">このインデックスは、前のフェーズで作成された 2 つのインデックスに依存します。</span><span class="sxs-lookup"><span data-stu-id="abc06-140">This index depends on both indexes that were populated in the preceding phase.</span></span>  
  
##  <a name="BestPracticeUnderstand"></a>   
##  <a name="problem-semantic-indexes-are-not-populated"></a><a name="ProblemNotPopulated"></a><span data-ttu-id="abc06-141">問題: セマンティックインデックスが設定されない</span><span class="sxs-lookup"><span data-stu-id="abc06-141">Problem: Semantic Indexes Are Not Populated</span></span>  
 <span data-ttu-id="abc06-142">**関連するフルテキスト インデックスが作成されていますか?**</span><span class="sxs-lookup"><span data-stu-id="abc06-142">**Are the associated full-text indexes populated?**</span></span>  
 <span data-ttu-id="abc06-143">セマンティック インデックス作成はフルテキスト インデックス作成に依存しているため、セマンティック インデックスは関連するフルテキスト インデックスが作成されたときにのみ作成されます。</span><span class="sxs-lookup"><span data-stu-id="abc06-143">Since semantic indexing is dependent on full-text indexing, semantic indexes are only populated when the associated full-text indexes are populated.</span></span>  
  
 <span data-ttu-id="abc06-144">**フルテキスト検索およびセマンティック検索が適切にインストールおよび構成されていますか?**</span><span class="sxs-lookup"><span data-stu-id="abc06-144">**Are full-text search and semantic search properly installed and configured?**</span></span>  
 <span data-ttu-id="abc06-145">詳細については、「 [セマンティック検索のインストールと構成](install-and-configure-semantic-search.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abc06-145">For more information, see [Install and Configure Semantic Search](install-and-configure-semantic-search.md).</span></span>  
  
 <span data-ttu-id="abc06-146">**FDHOST サービスが使用できない状態ではありませんか? または、フルテキスト インデックス作成が失敗するそれ以外の原因はありませんか?**</span><span class="sxs-lookup"><span data-stu-id="abc06-146">**Is the FDHOST service not available, or is there another condition that would cause full-text indexing to fail?**</span></span>  
 <span data-ttu-id="abc06-147">詳細については、「 [フルテキスト インデックスの作成のトラブルシューティング](troubleshoot-full-text-indexing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abc06-147">For more information, see [Troubleshoot Full-Text Indexing](troubleshoot-full-text-indexing.md).</span></span>  
  
  
