---
title: セマンティック検索の DDL、関数、ストアド プロシージャ、およびビュー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], database objects
ms.assetid: 182f395f-3168-48a4-b723-ef4403544f9f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ce6c23f9a8ff1d0dac8986bf6b44c7725d4badc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719809"
---
# <a name="semantic-search-ddl-functions-stored-procedures-and-views"></a><span data-ttu-id="a4b97-102">セマンティック検索の DDL、関数、ストアド プロシージャ、およびビュー</span><span class="sxs-lookup"><span data-stu-id="a4b97-102">Semantic Search DDL, Functions, Stored Procedures, and Views</span></span>
  <span data-ttu-id="a4b97-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の統計的セマンティック検索をサポートする Transact-SQL ステートメントおよびデータベース オブジェクトの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="a4b97-103">Lists the Transact-SQL statements and the database objects that support statistical semantic search in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="a4b97-104">フルテキスト検索をサポートするステートメントおよびデータベース オブジェクトの一覧については、「 [フルテキスト検索の DDL、関数、ストアド プロシージャ、およびビュー](../views/views.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4b97-104">For the list of statements and database objects that support full-text search, see [Full-Text Search DDL, Functions, Stored Procedures, and Views](../views/views.md).</span></span>  
  
##  <a name="transact-sql-data-definition-language-ddl-statements"></a><a name="ddl"></a> <span data-ttu-id="a4b97-105">Transact-SQL データ定義言語 (DDL) ステートメント</span><span class="sxs-lookup"><span data-stu-id="a4b97-105">Transact-SQL Data Definition Language (DDL) Statements</span></span>  
  
|<span data-ttu-id="a4b97-106">Object</span><span class="sxs-lookup"><span data-stu-id="a4b97-106">Object</span></span>|<span data-ttu-id="a4b97-107">詳細情報</span><span class="sxs-lookup"><span data-stu-id="a4b97-107">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="a4b97-108">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4b97-108">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-index-transact-sql)|[<span data-ttu-id="a4b97-109">テーブルおよび列に対するセマンティック検索の有効化</span><span class="sxs-lookup"><span data-stu-id="a4b97-109">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)|  
|[<span data-ttu-id="a4b97-110">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4b97-110">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-index-transact-sql)|[<span data-ttu-id="a4b97-111">テーブルおよび列に対するセマンティック検索の有効化</span><span class="sxs-lookup"><span data-stu-id="a4b97-111">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)|  
  
##  <a name="system-functions"></a><a name="func"></a> <span data-ttu-id="a4b97-112">システム関数</span><span class="sxs-lookup"><span data-stu-id="a4b97-112">System Functions</span></span>  
  
|<span data-ttu-id="a4b97-113">Object</span><span class="sxs-lookup"><span data-stu-id="a4b97-113">Object</span></span>|<span data-ttu-id="a4b97-114">詳細情報</span><span class="sxs-lookup"><span data-stu-id="a4b97-114">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="a4b97-115">semantickeyphrasetable &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4b97-115">semantickeyphrasetable &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql)|[<span data-ttu-id="a4b97-116">セマンティック検索を使用したドキュメント内のキー フレーズの検索</span><span class="sxs-lookup"><span data-stu-id="a4b97-116">Find Key Phrases in Documents with Semantic Search</span></span>](find-key-phrases-in-documents-with-semantic-search.md)|  
|[<span data-ttu-id="a4b97-117">semanticsimilaritydetailstable &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4b97-117">semanticsimilaritydetailstable &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql)|[<span data-ttu-id="a4b97-118">セマンティック検索による類似および関連したドキュメントの取得</span><span class="sxs-lookup"><span data-stu-id="a4b97-118">Find Similar and Related Documents with Semantic Search</span></span>](find-similar-and-related-documents-with-semantic-search.md)|  
|[<span data-ttu-id="a4b97-119">semanticsimilaritytable &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4b97-119">semanticsimilaritytable &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql)|[<span data-ttu-id="a4b97-120">セマンティック検索による類似および関連したドキュメントの取得</span><span class="sxs-lookup"><span data-stu-id="a4b97-120">Find Similar and Related Documents with Semantic Search</span></span>](find-similar-and-related-documents-with-semantic-search.md)|  
  
##  <a name="system-metadata-functions"></a><a name="meta"></a> <span data-ttu-id="a4b97-121">システム メタデータ関数</span><span class="sxs-lookup"><span data-stu-id="a4b97-121">System Metadata Functions</span></span>  
  
|<span data-ttu-id="a4b97-122">Object</span><span class="sxs-lookup"><span data-stu-id="a4b97-122">Object</span></span>|<span data-ttu-id="a4b97-123">詳細情報</span><span class="sxs-lookup"><span data-stu-id="a4b97-123">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="a4b97-124">COLUMNPROPERTY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4b97-124">COLUMNPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/columnproperty-transact-sql)|[<span data-ttu-id="a4b97-125">テーブルおよび列に対するセマンティック検索の有効化</span><span class="sxs-lookup"><span data-stu-id="a4b97-125">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)|  
|[<span data-ttu-id="a4b97-126">DATABASEPROPERTYEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4b97-126">DATABASEPROPERTYEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/databasepropertyex-transact-sql)|[<span data-ttu-id="a4b97-127">テーブルおよび列に対するセマンティック検索の有効化</span><span class="sxs-lookup"><span data-stu-id="a4b97-127">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)|  
|[<span data-ttu-id="a4b97-128">FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4b97-128">FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql)|[<span data-ttu-id="a4b97-129">セマンティック検索の管理および監視</span><span class="sxs-lookup"><span data-stu-id="a4b97-129">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
|[<span data-ttu-id="a4b97-130">INDEXPROPERTY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4b97-130">INDEXPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/indexproperty-transact-sql)|[<span data-ttu-id="a4b97-131">セマンティック検索の管理および監視</span><span class="sxs-lookup"><span data-stu-id="a4b97-131">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
|[<span data-ttu-id="a4b97-132">OBJECTPROPERTYEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4b97-132">OBJECTPROPERTYEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/objectproperty-transact-sql)|[<span data-ttu-id="a4b97-133">テーブルおよび列に対するセマンティック検索の有効化</span><span class="sxs-lookup"><span data-stu-id="a4b97-133">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)|  
|[<span data-ttu-id="a4b97-134">SERVERPROPERTY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4b97-134">SERVERPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)|[<span data-ttu-id="a4b97-135">セマンティック検索のインストールと構成</span><span class="sxs-lookup"><span data-stu-id="a4b97-135">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)|  
  
##  <a name="system-stored-procedures"></a><a name="sproc"></a> <span data-ttu-id="a4b97-136">システム ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="a4b97-136">System Stored Procedures</span></span>  
  
|<span data-ttu-id="a4b97-137">Object</span><span class="sxs-lookup"><span data-stu-id="a4b97-137">Object</span></span>|<span data-ttu-id="a4b97-138">詳細情報</span><span class="sxs-lookup"><span data-stu-id="a4b97-138">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="a4b97-139">sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4b97-139">sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql)|[<span data-ttu-id="a4b97-140">セマンティック検索のインストールと構成</span><span class="sxs-lookup"><span data-stu-id="a4b97-140">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)|  
|[<span data-ttu-id="a4b97-141">sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4b97-141">sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql)|[<span data-ttu-id="a4b97-142">セマンティック検索のインストールと構成</span><span class="sxs-lookup"><span data-stu-id="a4b97-142">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)|  
  
##  <a name="system-views---catalog-views"></a><a name="cv"></a> <span data-ttu-id="a4b97-143">システム ビュー - カタログ ビュー</span><span class="sxs-lookup"><span data-stu-id="a4b97-143">System Views - Catalog Views</span></span>  
  
|<span data-ttu-id="a4b97-144">Object</span><span class="sxs-lookup"><span data-stu-id="a4b97-144">Object</span></span>|<span data-ttu-id="a4b97-145">詳細情報</span><span class="sxs-lookup"><span data-stu-id="a4b97-145">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="a4b97-146">sys.fulltext_index_columns &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4b97-146">sys.fulltext_index_columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)|[<span data-ttu-id="a4b97-147">セマンティック検索の管理および監視</span><span class="sxs-lookup"><span data-stu-id="a4b97-147">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
|[<span data-ttu-id="a4b97-148">sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4b97-148">sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql)|[<span data-ttu-id="a4b97-149">セマンティック検索のインストールと構成</span><span class="sxs-lookup"><span data-stu-id="a4b97-149">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)|  
|[<span data-ttu-id="a4b97-150">sys.fulltext_semantic_languages &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4b97-150">sys.fulltext_semantic_languages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql)|[<span data-ttu-id="a4b97-151">セマンティック検索のインストールと構成</span><span class="sxs-lookup"><span data-stu-id="a4b97-151">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)|  
  
##  <a name="system-views---dynamic-management-views"></a><a name="dmv"></a> <span data-ttu-id="a4b97-152">システム ビュー - 動的管理ビュー</span><span class="sxs-lookup"><span data-stu-id="a4b97-152">System Views - Dynamic Management Views</span></span>  
  
|<span data-ttu-id="a4b97-153">Object</span><span class="sxs-lookup"><span data-stu-id="a4b97-153">Object</span></span>|<span data-ttu-id="a4b97-154">詳細情報</span><span class="sxs-lookup"><span data-stu-id="a4b97-154">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="a4b97-155">sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4b97-155">sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql)|[<span data-ttu-id="a4b97-156">セマンティック検索の管理および監視</span><span class="sxs-lookup"><span data-stu-id="a4b97-156">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
|[<span data-ttu-id="a4b97-157">sys.dm_fts_index_population &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4b97-157">sys.dm_fts_index_population &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)|[<span data-ttu-id="a4b97-158">セマンティック検索の管理および監視</span><span class="sxs-lookup"><span data-stu-id="a4b97-158">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
|[<span data-ttu-id="a4b97-159">sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4b97-159">sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql)|[<span data-ttu-id="a4b97-160">セマンティック検索の管理および監視</span><span class="sxs-lookup"><span data-stu-id="a4b97-160">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
  
## <a name="see-also"></a><span data-ttu-id="a4b97-161">参照</span><span class="sxs-lookup"><span data-stu-id="a4b97-161">See Also</span></span>  
 [<span data-ttu-id="a4b97-162">セマンティック検索の管理および監視</span><span class="sxs-lookup"><span data-stu-id="a4b97-162">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)  
  
  
