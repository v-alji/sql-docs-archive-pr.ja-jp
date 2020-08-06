---
title: サーバー インスタンスでのフルテキスト検索の管理と監視 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], about
- full-text search [SQL Server], server management
ms.assetid: 2733ed78-6d33-4bf9-94da-60c3141b87c8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1ba4b2f081047f25fa775e0c8754caa4ce643e70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717691"
---
# <a name="manage-and-monitor-full-text-search-for-a-server-instance"></a><span data-ttu-id="905b7-102">サーバー インスタンスでのフルテキスト検索の管理と監視</span><span class="sxs-lookup"><span data-stu-id="905b7-102">Manage and Monitor Full-Text Search for a Server Instance</span></span>
  <span data-ttu-id="905b7-103">サーバー インスタンスのフルテキスト検索の管理には次の作業があります。</span><span class="sxs-lookup"><span data-stu-id="905b7-103">Full-text administration for a server instance includes:</span></span>  
  
-   <span data-ttu-id="905b7-104">FDHOST ランチャー サービス (MSSQLFDLauncher) の管理、サービス アカウント資格情報の変更時のフィルター デーモン ホスト プロセスの再起動、サーバー全体のフルテキスト プロパティの構成、フルテキスト カタログのバックアップなどのシステム管理作業。</span><span class="sxs-lookup"><span data-stu-id="905b7-104">System management tasks such as managing the FDHOST Launcher service (MSSQLFDLauncher), restarting filter daemon host process if you change the service account credentials, configuring server-wide full-text properties, and backing up full-text catalogs.</span></span> <span data-ttu-id="905b7-105">たとえば、サーバー レベルでは、サーバー インスタンス全体の既定の言語とは異なる、既定のフルテキスト言語を指定できます。</span><span class="sxs-lookup"><span data-stu-id="905b7-105">At the server level, for example, you can specify a default full-text language that differs from the default language of the server instance as a whole.</span></span>  
  
-   <span data-ttu-id="905b7-106">フルテキスト言語コンポーネント (ワード ブレーカーおよびステミング機能、類義語辞典ファイル、ストップワードおよびストップリスト) の構成。</span><span class="sxs-lookup"><span data-stu-id="905b7-106">Configuring full-text linguistic components (word breakers and stemmers, thesaurus file, and stopwords and stoplists).</span></span>  
  
-   <span data-ttu-id="905b7-107">フルテキスト検索を行うためのユーザー データベースの構成。</span><span class="sxs-lookup"><span data-stu-id="905b7-107">Configuring a user database for full-text search.</span></span> <span data-ttu-id="905b7-108">データベース用のフルテキスト カタログを 1 つ以上作成し、フルテキスト クエリを実行する各テーブルまたは各インデックス付きビューにフルテキスト インデックスを定義します。</span><span class="sxs-lookup"><span data-stu-id="905b7-108">This involves creating one or more full-text catalogs for the database and defining a full-text index on each table or indexed view on which you want to execute full-text queries.</span></span>  
  
##  <a name="viewing-or-changing-server-properties-for-full-text-search"></a><a name="props"></a> <span data-ttu-id="905b7-109">フルテキスト検索のサーバー プロパティを表示および変更する</span><span class="sxs-lookup"><span data-stu-id="905b7-109">Viewing or Changing Server Properties for Full-Text Search</span></span>  
 <span data-ttu-id="905b7-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスのフルテキスト プロパティは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で表示できます。</span><span class="sxs-lookup"><span data-stu-id="905b7-110">You can view the full-text properties of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-view-and-change-server-properties-for-full-text-search"></a><span data-ttu-id="905b7-111">フルテキスト検索のサーバー プロパティを表示および変更するには</span><span class="sxs-lookup"><span data-stu-id="905b7-111">To view and change server properties for full-text search</span></span>  
  
1.  <span data-ttu-id="905b7-112">オブジェクト エクスプローラーでサーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="905b7-112">In Object Explorer, right-click a server, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="905b7-113">**[サーバーのプロパティ]** ダイアログ ボックスで、 **[詳細設定]** ページをクリックし、フルテキスト検索に関するサーバーの情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="905b7-113">In the **Server Properties** dialog box, click the **Advanced** page to view server information about full-text search.</span></span> <span data-ttu-id="905b7-114">フルテキスト プロパティは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="905b7-114">The full-text properties are as follows:</span></span>  
  
    -   <span data-ttu-id="905b7-115">**[既定のフルテキスト言語]**</span><span class="sxs-lookup"><span data-stu-id="905b7-115">**Default Full-Text Language**</span></span>  
  
         <span data-ttu-id="905b7-116">フルテキスト インデックス列に、既定の言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="905b7-116">Specifies a default language for full-text indexed columns.</span></span> <span data-ttu-id="905b7-117">フルテキスト インデックス データの言語の分析は、データの言語に依存します。</span><span class="sxs-lookup"><span data-stu-id="905b7-117">Linguistic analysis of full-text indexed data is dependent on the language of the data.</span></span> <span data-ttu-id="905b7-118">このオプションの既定値は、サーバーの言語です。</span><span class="sxs-lookup"><span data-stu-id="905b7-118">The default value of this option is the language of the server.</span></span> <span data-ttu-id="905b7-119">表示される設定に対応する言語については、「[sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="905b7-119">For the language that corresponds to the displayed setting, see [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql).</span></span>  
  
    -   <span data-ttu-id="905b7-120">**フルテキスト アップグレード オプション**</span><span class="sxs-lookup"><span data-stu-id="905b7-120">**Full-Text Upgrade Option**</span></span>  
  
         <span data-ttu-id="905b7-121">このサーバー プロパティは、データベースを [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] から新しいバージョンにアップグレードする際のフルテキスト インデックスの移行方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="905b7-121">This server property controls how full-text indexes are migrated when upgrading a database from [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] to a later version.</span></span> <span data-ttu-id="905b7-122">このプロパティは、データベースのインポート、データベース バックアップの復元、ファイル バックアップの復元、またはデータベース コピー ウィザードを使用したデータベースのコピーによってアップグレードする場合に適用されます。</span><span class="sxs-lookup"><span data-stu-id="905b7-122">This property applies to upgrading by attaching a database, restoring a database backup, restoring a file backup, or copying the database by using the Copy Database Wizard.</span></span>  
  
         <span data-ttu-id="905b7-123">選択肢は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="905b7-123">The alternatives are as follows:</span></span>  
  
         <span data-ttu-id="905b7-124">**[インポート]**</span><span class="sxs-lookup"><span data-stu-id="905b7-124">**Import**</span></span>  
         <span data-ttu-id="905b7-125">フルテキスト カタログがインポートされます。</span><span class="sxs-lookup"><span data-stu-id="905b7-125">Full-text catalogs are imported.</span></span> <span data-ttu-id="905b7-126">通常、インポートの方が再構築よりもかなり高速に処理されます。</span><span class="sxs-lookup"><span data-stu-id="905b7-126">Typically, import is significantly faster than rebuild.</span></span> <span data-ttu-id="905b7-127">たとえば、CPU を 1 つだけ使用している場合、インポートは、再構築の約 10 倍の速さで実行されます。</span><span class="sxs-lookup"><span data-stu-id="905b7-127">For example, when using only one CPU, import runs about 10 times faster than rebuild.</span></span> <span data-ttu-id="905b7-128">ただし、インポートされたフルテキスト カタログでは、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]で導入された新しい拡張機能であるワード ブレーカーが使用されません。そのため、最終的にはフルテキスト カタログの再構築が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="905b7-128">However, an imported full-text catalog does not use the new and enhanced word breakers introduced in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], so you might want to rebuild your full-text catalogs eventually.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="905b7-129">再構築はマルチスレッド モードで実行できます。10 を超える CPU が使用可能な場合に、再構築でそれらの CPU をすべて使用できるようにすると、再構築の方がインポートよりも高速に実行されることがあります。</span><span class="sxs-lookup"><span data-stu-id="905b7-129">Rebuild can run in multi-threaded mode, and if more than 10 CPUs are available, rebuild might run faster than import if you allow rebuild to use all of the CPUs.</span></span>  
  
         <span data-ttu-id="905b7-130">フルテキスト カタログが使用できない場合は、関連付けられたフルテキスト インデックスが再構築されます。</span><span class="sxs-lookup"><span data-stu-id="905b7-130">If a full-text catalog is not available, the associated full-text indexes are rebuilt.</span></span> <span data-ttu-id="905b7-131">このオプションは [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] データベースでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="905b7-131">This option is available for only [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] databases.</span></span>  
  
         <span data-ttu-id="905b7-132">**リビルド**</span><span class="sxs-lookup"><span data-stu-id="905b7-132">**Rebuild**</span></span>  
         <span data-ttu-id="905b7-133">フルテキスト カタログは、導入された新しい拡張機能であるワード ブレーカーを使用して再構築されます。</span><span class="sxs-lookup"><span data-stu-id="905b7-133">Full-text catalogs are rebuilt using the new and enhanced word breakers.</span></span> <span data-ttu-id="905b7-134">インデックスの再構築には時間がかかり、アップグレード後にかなりの量の CPU とメモリが必要になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="905b7-134">Rebuilding indexes can take awhile, and a significant amount of CPU and memory might be required after the upgrade.</span></span>  
  
         <span data-ttu-id="905b7-135">**リセット**</span><span class="sxs-lookup"><span data-stu-id="905b7-135">**Reset**</span></span>  
         <span data-ttu-id="905b7-136">フルテキスト カタログがリセットされます。</span><span class="sxs-lookup"><span data-stu-id="905b7-136">Full-text catalogs are reset.</span></span> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="905b7-137">のフルテキスト カタログ ファイルは削除されますが、フルテキスト カタログのメタデータおよびフルテキスト インデックスは保持されます。</span><span class="sxs-lookup"><span data-stu-id="905b7-137">full-text catalog files are removed, but the metadata for full-text catalogs and full-text indexes is retained.</span></span> <span data-ttu-id="905b7-138">アップグレード後、すべてのフルテキスト インデックスで変更の追跡は無効化されており、クロールは自動的には開始されません。</span><span class="sxs-lookup"><span data-stu-id="905b7-138">After being upgraded, all full-text indexes are disabled for change tracking and crawls are not started automatically.</span></span> <span data-ttu-id="905b7-139">アップグレードの完了後、手動で完全作成を実行するまで、カタログは空のままになります。</span><span class="sxs-lookup"><span data-stu-id="905b7-139">The catalog will remain empty until you manually issue a full population, after the upgrade completes.</span></span>  
  
         <span data-ttu-id="905b7-140">フルテキストアップグレードオプションの選択の詳細については、「[フルテキスト検索のアップグレード](upgrade-full-text-search.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="905b7-140">For information about choosing a full-text upgrade option, see [Upgrade Full-Text Search](upgrade-full-text-search.md).</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="905b7-141">フルテキスト アップグレード オプションは、[sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql) の **upgrade_option** 操作を使用して設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="905b7-141">The full-text upgrade option can also be set by using the [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)**upgrade_option** action.</span></span>  
  
##  <a name="viewing-additional-full-text-server-properties"></a><a name="metadata"></a> <span data-ttu-id="905b7-142">その他のフルテキスト サーバー プロパティの表示</span><span class="sxs-lookup"><span data-stu-id="905b7-142">Viewing Additional Full-Text Server Properties</span></span>  
 [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="905b7-143">関数を使用すると、フルテキスト検索のさまざまなサーバー レベルのプロパティの値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="905b7-143">functions can be used to obtain the value of various server-level properties of full-text search.</span></span> <span data-ttu-id="905b7-144">この情報は、フルテキスト検索の管理およびトラブルシューティングに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="905b7-144">This information is useful for administrating and troubleshooting full-text search.</span></span>  
  
 <span data-ttu-id="905b7-145">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サーバー インスタンスのフルテキスト プロパティと各プロパティに関連する [!INCLUDE[tsql](../../../includes/tsql-md.md)] 関数の一覧を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="905b7-145">The following table lists full-text properties of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server instance and their related [!INCLUDE[tsql](../../../includes/tsql-md.md)] functions.</span></span>  
  
|<span data-ttu-id="905b7-146">プロパティ</span><span class="sxs-lookup"><span data-stu-id="905b7-146">Property</span></span>|<span data-ttu-id="905b7-147">説明</span><span class="sxs-lookup"><span data-stu-id="905b7-147">Description</span></span>|<span data-ttu-id="905b7-148">Function</span><span class="sxs-lookup"><span data-stu-id="905b7-148">Function</span></span>|  
|--------------|-----------------|--------------|  
|`IsFullTextInstalled`|<span data-ttu-id="905b7-149">フルテキスト コンポーネントが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の現在のインスタンスと共にインストールされているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="905b7-149">Whether the full-text component is installed with the current instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|[<span data-ttu-id="905b7-150">FULLTEXTSERVICEPROPERTY</span><span class="sxs-lookup"><span data-stu-id="905b7-150">FULLTEXTSERVICEPROPERTY</span></span>](/sql/t-sql/functions/fulltextserviceproperty-transact-sql)<br /><br /> [<span data-ttu-id="905b7-151">SERVERPROPERTY</span><span class="sxs-lookup"><span data-stu-id="905b7-151">SERVERPROPERTY</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)|  
|`LoadOSResources`|<span data-ttu-id="905b7-152">オペレーティング システムのワード ブレーカーやフィルターが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに登録され、使用されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="905b7-152">Whether operating system word breakers and filters are registered and used with this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|<span data-ttu-id="905b7-153">FULLTEXTSERVICEPROPERTY</span><span class="sxs-lookup"><span data-stu-id="905b7-153">FULLTEXTSERVICEPROPERTY</span></span>|  
|`VerifySignature`|<span data-ttu-id="905b7-154">Full-Text Engine に署名付きバイナリのみを読み込むかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="905b7-154">Specifies whether only signed binaries are loaded by the Full-Text Engine.</span></span>|<span data-ttu-id="905b7-155">FULLTEXTSERVICEPROPERTY</span><span class="sxs-lookup"><span data-stu-id="905b7-155">FULLTEXTSERVICEPROPERTY</span></span>|  
  
##  <a name="monitoring-full-text-search-activity"></a><a name="monitor"></a><span data-ttu-id="905b7-156">フルテキスト検索の利用状況の監視</span><span class="sxs-lookup"><span data-stu-id="905b7-156">Monitoring Full-Text Search Activity</span></span>  
 <span data-ttu-id="905b7-157">サーバー インスタンスでのフルテキスト検索の実行状況を監視する場合は、以下の動的管理ビューと関数が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="905b7-157">Several dynamic management views and functions are useful monitoring full-text search activity on a server instance.</span></span>  
  
 <span data-ttu-id="905b7-158">**作成操作が進行中のフルテキスト カタログに関する情報を表示するには**</span><span class="sxs-lookup"><span data-stu-id="905b7-158">**To view information about the full-text catalogs with in-progress population activity**</span></span>  
  
-   [<span data-ttu-id="905b7-159">sys.dm_fts_active_catalogs &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="905b7-159">sys.dm_fts_active_catalogs &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-active-catalogs-transact-sql)  
  
 <span data-ttu-id="905b7-160">**フィルター デーモン ホスト プロセスの現在の実行状況を表示するには**</span><span class="sxs-lookup"><span data-stu-id="905b7-160">**To view current activity of a filter daemon host process**</span></span>  
  
-   [<span data-ttu-id="905b7-161">sys.dm_fts_fdhosts &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="905b7-161">sys.dm_fts_fdhosts &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-fdhosts-transact-sql)  
  
 <span data-ttu-id="905b7-162">**進行中のインデックス作成に関する情報を表示するには**</span><span class="sxs-lookup"><span data-stu-id="905b7-162">**To view information about in-progress index populations**</span></span>  
  
-   [<span data-ttu-id="905b7-163">sys.dm_fts_index_population &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="905b7-163">sys.dm_fts_index_population &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)  
  
 <span data-ttu-id="905b7-164">**クロールまたはクロール範囲の一部として使用される、メモリ プールのメモリ バッファーを表示するには**</span><span class="sxs-lookup"><span data-stu-id="905b7-164">**To view memory buffers in a memory pool that are used as part of a crawl or crawl range.**</span></span>  
  
-   [<span data-ttu-id="905b7-165">sys.dm_fts_memory_buffers &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="905b7-165">sys.dm_fts_memory_buffers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql)  
  
 <span data-ttu-id="905b7-166">**フルテキスト クロールまたはフルテキスト クロール範囲でフルテキスト Gatherer コンポーネントに使用できる共有メモリ プールを表示するには**</span><span class="sxs-lookup"><span data-stu-id="905b7-166">**To view the shared memory pools available to the full-text gatherer component for a full-text crawl or a full-text crawl range**</span></span>  
  
-   [<span data-ttu-id="905b7-167">sys.dm_fts_memory_pools &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="905b7-167">sys.dm_fts_memory_pools &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-pools-transact-sql)  
  
 <span data-ttu-id="905b7-168">**各フルテキスト インデックス バッチに関する情報を表示するには**</span><span class="sxs-lookup"><span data-stu-id="905b7-168">**To view information about each full-text indexing batch**</span></span>  
  
-   [<span data-ttu-id="905b7-169">sys.dm_fts_outstanding_batches &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="905b7-169">sys.dm_fts_outstanding_batches &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-outstanding-batches-transact-sql)  
  
 <span data-ttu-id="905b7-170">**進行中の作成に関連する特定の範囲についての情報を表示するには**</span><span class="sxs-lookup"><span data-stu-id="905b7-170">**To view information about the specific ranges related to an in-progress population**</span></span>  
  
-   [<span data-ttu-id="905b7-171">sys.dm_fts_population_ranges &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="905b7-171">sys.dm_fts_population_ranges &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-population-ranges-transact-sql)  
  
  
