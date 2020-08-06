---
title: '[フルテキストインデックスのプロパティ] ([全般] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.general.f1
ms.assetid: f4dff61c-8c2f-4ff9-abe4-70a34421448f
author: rothja
ms.author: jroth
ms.openlocfilehash: 61b9f2948df138c39230cf6f5787c395a364c695
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645803"
---
# <a name="full-text-index-properties-general-page"></a><span data-ttu-id="3ec95-102">[フルテキスト インデックスのプロパティ] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="3ec95-102">Full-Text Index Properties (General Page)</span></span>
  <span data-ttu-id="3ec95-103">**フルテキスト インデックスの変更可能なプロパティを表示または変更するには**</span><span class="sxs-lookup"><span data-stu-id="3ec95-103">**To view or change the modifiable properties of a full-text index**</span></span>  
  
-   [<span data-ttu-id="3ec95-104">フルテキスト インデックスの管理</span><span class="sxs-lookup"><span data-stu-id="3ec95-104">Manage Full-Text Indexes</span></span>](../relational-databases/indexes/indexes.md)  
  
## <a name="ui-element-list"></a><span data-ttu-id="3ec95-105">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="3ec95-105">UI element list</span></span>  
 <span data-ttu-id="3ec95-106">**フルテキストカタログ**</span><span class="sxs-lookup"><span data-stu-id="3ec95-106">**Full-Text Catalog**</span></span>  
 <span data-ttu-id="3ec95-107">フルテキスト インデックスが関連付けられているフルテキスト カタログの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="3ec95-107">Displays the name of the full-text catalog with which the full-text index is associated.</span></span>  
  
 <span data-ttu-id="3ec95-108">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="3ec95-108">**Database**</span></span>  
 <span data-ttu-id="3ec95-109">フルテキスト インデックスが存在するデータベースの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="3ec95-109">Displays the name of the database in which the full-text index resides.</span></span>  
  
 <span data-ttu-id="3ec95-110">**テーブル**</span><span class="sxs-lookup"><span data-stu-id="3ec95-110">**Table**</span></span>  
 <span data-ttu-id="3ec95-111">フルテキスト インデックスが定義されているテーブルの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="3ec95-111">Displays the name of the table on which the full-text index is defined.</span></span>  
  
 <span data-ttu-id="3ec95-112">**[フルテキスト インデックス キー]**</span><span class="sxs-lookup"><span data-stu-id="3ec95-112">**Full-Text Index Key**</span></span>  
 <span data-ttu-id="3ec95-113">フルテキスト インデックス キーの名前を表示します。フルテキスト インデックス キーは、テーブルの 1 つの列の一意インデックスです。</span><span class="sxs-lookup"><span data-stu-id="3ec95-113">Displays the name of the full-text index key, which is a unique index on a single column of the table.</span></span>  
  
 <span data-ttu-id="3ec95-114">**[テーブルのフルテキスト作成状態]**</span><span class="sxs-lookup"><span data-stu-id="3ec95-114">**Table Full-Text Populate Status**</span></span>  
 <span data-ttu-id="3ec95-115">フルテキスト インデックスが設定されたテーブルの作成状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="3ec95-115">Displays the population status of the full-text indexed table.</span></span>  
  
 <span data-ttu-id="3ec95-116">次のような値が考えられます。</span><span class="sxs-lookup"><span data-stu-id="3ec95-116">The possible values are as follows:</span></span>  
  
 <span data-ttu-id="3ec95-117">0 = アイドル状態</span><span class="sxs-lookup"><span data-stu-id="3ec95-117">0 = Idle.</span></span>  
  
 <span data-ttu-id="3ec95-118">1 = 全体を作成中</span><span class="sxs-lookup"><span data-stu-id="3ec95-118">1 = Full population is in progress.</span></span>  
  
 <span data-ttu-id="3ec95-119">2 = 増分作成中</span><span class="sxs-lookup"><span data-stu-id="3ec95-119">2 = Incremental population is in progress.</span></span>  
  
 <span data-ttu-id="3ec95-120">3 = 追跡した変更を伝達中</span><span class="sxs-lookup"><span data-stu-id="3ec95-120">3 = Propagation of tracked changes is in progress.</span></span>  
  
 <span data-ttu-id="3ec95-121">4 = 自動変更の追跡など、インデックスのバックグラウンド更新が進行中</span><span class="sxs-lookup"><span data-stu-id="3ec95-121">4 = Background update index is in progress, such as automatic change tracking.</span></span>  
  
 <span data-ttu-id="3ec95-122">5 = フルテキスト インデックス作成が絞り込みまたは停止された</span><span class="sxs-lookup"><span data-stu-id="3ec95-122">5 = Full-text indexing is throttled or paused.</span></span>  
  
 <span data-ttu-id="3ec95-123">**[アクティブなフルテキスト インデックス]**</span><span class="sxs-lookup"><span data-stu-id="3ec95-123">**Active Full-Text Index**</span></span>  
 <span data-ttu-id="3ec95-124">テーブルに有効なフルテキスト インデックスが作成されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="3ec95-124">Indicates whether the table has an active full-text index.</span></span>  
  
 <span data-ttu-id="3ec95-125">1 = True</span><span class="sxs-lookup"><span data-stu-id="3ec95-125">1 = True</span></span>  
  
 <span data-ttu-id="3ec95-126">0 = False</span><span class="sxs-lookup"><span data-stu-id="3ec95-126">0 = False</span></span>  
  
 <span data-ttu-id="3ec95-127">**[フルテキスト インデックス ファイル グループ]**</span><span class="sxs-lookup"><span data-stu-id="3ec95-127">**Full-Text Index Filegroup**</span></span>  
 <span data-ttu-id="3ec95-128">フルテキスト インデックスが属しているファイル グループ。</span><span class="sxs-lookup"><span data-stu-id="3ec95-128">The filegroup to which the full-text index belongs.</span></span>  
  
 <span data-ttu-id="3ec95-129">**フルテキスト インデックス ストップリスト**</span><span class="sxs-lookup"><span data-stu-id="3ec95-129">**Full-Text Index Stoplist**</span></span>  
 <span data-ttu-id="3ec95-130">フルテキスト インデックスに現在関連付けられているストップリスト。</span><span class="sxs-lookup"><span data-stu-id="3ec95-130">The stoplist that is currently associated with the full-text index.</span></span> <span data-ttu-id="3ec95-131">ストップリストは、 [ストップワード](../relational-databases/search/full-text-search.md)のリストです。</span><span class="sxs-lookup"><span data-stu-id="3ec95-131">A stoplist is a list of [stopwords](../relational-databases/search/full-text-search.md).</span></span> <span data-ttu-id="3ec95-132">フルテキスト インデックスに関連付けられているストップリストが存在する場合、ストップリストはそのインデックスのフルテキスト クエリに適用されます。</span><span class="sxs-lookup"><span data-stu-id="3ec95-132">The stoplist associated with a full-text index, if any, is applied to full-text queries on that index.</span></span> <span data-ttu-id="3ec95-133">インデックスからストップリストを削除するには、 **\<OFF>** 一覧から選択するか、別のストップリストを選択します。は **\<SYSTEM>** 、システムストップリストを示します。</span><span class="sxs-lookup"><span data-stu-id="3ec95-133">You can remove the stoplist from the index by selecting **\<OFF>** from the list, or you can select a different stoplist; **\<SYSTEM>** indicates the system stoplist.</span></span>  
  
 <span data-ttu-id="3ec95-134">**ストップリストを作成するには**</span><span class="sxs-lookup"><span data-stu-id="3ec95-134">**To create a stoplist**</span></span>  
  
-   [<span data-ttu-id="3ec95-135">フルテキスト検索に使用するストップワードとストップリストの構成と管理</span><span class="sxs-lookup"><span data-stu-id="3ec95-135">Configure and Manage Stopwords and Stoplists for Full-Text Search</span></span>](../relational-databases/search/full-text-search.md)  
  
 <span data-ttu-id="3ec95-136">**検索プロパティ リスト**</span><span class="sxs-lookup"><span data-stu-id="3ec95-136">**Search Property List**</span></span>  
 <span data-ttu-id="3ec95-137">現在、フルテキスト インデックスに関連付けられている検索プロパティ リストです (存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="3ec95-137">The search property list that is currently associated with the full-text index, if any.</span></span> <span data-ttu-id="3ec95-138">検索プロパティ リストは、作成時に関連付けられているフルテキスト インデックスに含められるドキュメント プロパティのセットを示します。</span><span class="sxs-lookup"><span data-stu-id="3ec95-138">A search property list specifies a set of document properties that are included in the associated full-text index when it is populated.</span></span> <span data-ttu-id="3ec95-139">詳細については、「 [検索プロパティ リストを使用したドキュメント プロパティの検索](../relational-databases/search/search-document-properties-with-search-property-lists.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ec95-139">For more information, see [Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md).</span></span>  
  
 <span data-ttu-id="3ec95-140">**\<Off>** 現在インデックスに関連付けられている検索プロパティリストがないことを示します。</span><span class="sxs-lookup"><span data-stu-id="3ec95-140">**\<Off>** indicates that there is currently no search property list associated with the index.</span></span> <span data-ttu-id="3ec95-141">一覧から選択することで、インデックスから現在の検索プロパティリストを削除でき **\<Off>** ます。または、一覧から別の検索プロパティリストを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="3ec95-141">You can remove the current search property list from the index by selecting **\<Off>** from the list, or you can select a different search property list from the list.</span></span> <span data-ttu-id="3ec95-142">現在のデータベースの検索プロパティ リストだけが、ここに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="3ec95-142">Only search property lists in the current database are listed here.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ec95-143">特定の検索プロパティ リストを同じデータベース内の複数のフルテキスト インデックスに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="3ec95-143">You can associate a given search property list with more than one full-text index in the same database.</span></span>  
  
 <span data-ttu-id="3ec95-144">**検索プロパティ リストを作成するには**</span><span class="sxs-lookup"><span data-stu-id="3ec95-144">**To create a search property list**</span></span>  
  
-   [<span data-ttu-id="3ec95-145">検索プロパティ リストを使用したドキュメント プロパティの検索</span><span class="sxs-lookup"><span data-stu-id="3ec95-145">Search Document Properties with Search Property Lists</span></span>](../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
 <span data-ttu-id="3ec95-146">**[テーブルのフルテキスト項目カウント]**</span><span class="sxs-lookup"><span data-stu-id="3ec95-146">**Table Full-Text Item Count**</span></span>  
 <span data-ttu-id="3ec95-147">フルテキスト インデックスが正常に作成された行の数を示します。</span><span class="sxs-lookup"><span data-stu-id="3ec95-147">Indicates the number of rows that were full-text indexed successfully.</span></span>  
  
 <span data-ttu-id="3ec95-148">このプロパティは、OBJECTPROPERTYEX [!INCLUDE[tsql](../includes/tsql-md.md)] 関数から返される `TableFulltextItemCount` プロパティに対応します。</span><span class="sxs-lookup"><span data-stu-id="3ec95-148">This property corresponds to the `TableFulltextItemCount` property returned by the OBJECTPROPERTYEX [!INCLUDE[tsql](../includes/tsql-md.md)] function.</span></span>  
  
 <span data-ttu-id="3ec95-149">**[テーブルの処理済みのフルテキスト ドキュメント]**</span><span class="sxs-lookup"><span data-stu-id="3ec95-149">**Table Full-Text Docs Processed**</span></span>  
 <span data-ttu-id="3ec95-150">フルテキスト インデックス作成の開始以降に処理された行数を表示します。</span><span class="sxs-lookup"><span data-stu-id="3ec95-150">Displays the number of rows that have been processed since the start of full-text indexing.</span></span> <span data-ttu-id="3ec95-151">フルテキスト検索用にインデックスが作成されるテーブルでは、1 行のすべての列が、インデックスが作成される 1 つのドキュメントの一部と見なされます。</span><span class="sxs-lookup"><span data-stu-id="3ec95-151">In a table that is being indexed for full-text search, all the columns of one row are considered as part of one document to be indexed.</span></span> <span data-ttu-id="3ec95-152">削除された行はカウントされません。</span><span class="sxs-lookup"><span data-stu-id="3ec95-152">Deleted rows are not counted.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3ec95-153">0</span><span class="sxs-lookup"><span data-stu-id="3ec95-153">0</span></span>|<span data-ttu-id="3ec95-154">フルテキスト インデックスの作成が完了し、アクティブな作成が存在しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="3ec95-154">Indicates that full-text indexing is completed and there is no active population.</span></span>|  
|<span data-ttu-id="3ec95-155">> 0</span><span class="sxs-lookup"><span data-stu-id="3ec95-155">> 0</span></span>|<span data-ttu-id="3ec95-156">アクティブな作成の場合は、作成、バックグラウンド インデックスの更新による変更の追跡の有効化 (変更の自動追跡など)、フルテキスト インデックス スキーマの変更、フルテキスト カタログの再構築、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]インスタンスの再起動などが実行された後に挿入操作や更新操作で処理されたドキュメントの数を示します。</span><span class="sxs-lookup"><span data-stu-id="3ec95-156">For an active population, indicates the number of documents processed by insert or update operations since any of the following: a population, enabling of change tracking with background update index population (such as auto change tracking), changing the full-text index schema, rebuilding the full-text catalog, restarting the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and so forth.</span></span>|  
  
 <span data-ttu-id="3ec95-157">**[テーブルのフルテキスト保留の変更]**</span><span class="sxs-lookup"><span data-stu-id="3ec95-157">**Table Full-Text Pending Changes**</span></span>  
 <span data-ttu-id="3ec95-158">変更の追跡が処理されていないエントリ数。</span><span class="sxs-lookup"><span data-stu-id="3ec95-158">Number of pending change tracking entries to process.</span></span>  
  
 <span data-ttu-id="3ec95-159">0 = 変更の追跡は有効でない</span><span class="sxs-lookup"><span data-stu-id="3ec95-159">0 = change tracking is not enabled.</span></span>  
  
 <span data-ttu-id="3ec95-160">NULL = テーブルにフルテキスト インデックスはない。</span><span class="sxs-lookup"><span data-stu-id="3ec95-160">NULL = Table does not have a full-text index.</span></span>  
  
 <span data-ttu-id="3ec95-161">**[テーブルのフルテキスト失敗カウント]**</span><span class="sxs-lookup"><span data-stu-id="3ec95-161">**Table Full-Text Fail Count**</span></span>  
 <span data-ttu-id="3ec95-162">フルテキスト検索でインデックスが作成されなかった行の数。</span><span class="sxs-lookup"><span data-stu-id="3ec95-162">The number of rows that full-text search did not index.</span></span>  
  
 <span data-ttu-id="3ec95-163">0 = 作成完了</span><span class="sxs-lookup"><span data-stu-id="3ec95-163">0 = The population has completed.</span></span>  
  
 <span data-ttu-id="3ec95-164">\>0 = 次のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="3ec95-164">\>0 = One of the following:</span></span>  
  
-   <span data-ttu-id="3ec95-165">完全、増分、または手動による変更追跡の作成開始以降に、インデックスが作成されなかったドキュメントの数。</span><span class="sxs-lookup"><span data-stu-id="3ec95-165">The number of documents that were not indexed since the start of full, incremental, or manual change tracking population.</span></span>  
  
-   <span data-ttu-id="3ec95-166">インデックスのバックグラウンド更新による変更追跡の場合、作成の開始または再開以降にインデックスが作成されなかった行数。</span><span class="sxs-lookup"><span data-stu-id="3ec95-166">For change tracking with background update index, the number of rows that were not indexed since the start of the population, or the restart of the population.</span></span> <span data-ttu-id="3ec95-167">これは、スキーマ変更、カタログの再構築、サーバーの再起動などにより発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="3ec95-167">This could be caused by a schema change, rebuild of the catalog, server restart, and so on</span></span>  
  
 <span data-ttu-id="3ec95-168">**フルテキスト インデックス有効**</span><span class="sxs-lookup"><span data-stu-id="3ec95-168">**Full-Text Indexing Enabled**</span></span>  
 <span data-ttu-id="3ec95-169">フルテキスト インデックスが有効かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="3ec95-169">Specifies whether full-text indexing is enabled.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3ec95-170">**True** にします</span><span class="sxs-lookup"><span data-stu-id="3ec95-170">**True**</span></span>|<span data-ttu-id="3ec95-171">Enabled</span><span class="sxs-lookup"><span data-stu-id="3ec95-171">Enabled</span></span>|  
|<span data-ttu-id="3ec95-172">**False**</span><span class="sxs-lookup"><span data-stu-id="3ec95-172">**False**</span></span>|<span data-ttu-id="3ec95-173">無効</span><span class="sxs-lookup"><span data-stu-id="3ec95-173">Disabled</span></span>|  
  
 <span data-ttu-id="3ec95-174">**変更の追跡**</span><span class="sxs-lookup"><span data-stu-id="3ec95-174">**Change Tracking**</span></span>  
 <span data-ttu-id="3ec95-175">テーブルで変更の追跡が有効になっているかどうかを示します。また、有効になっている場合は、変更の追跡の種類も示します。</span><span class="sxs-lookup"><span data-stu-id="3ec95-175">Specifies whether the table has full-text change-tracking enabled, and if so, what kind.</span></span> <span data-ttu-id="3ec95-176">フルテキスト変更の追跡では、フルテキスト インデックスの作成対象としてセットアップされたテーブルまたはインデックス付きビューで変更が加えられた行の記録が保持されます。</span><span class="sxs-lookup"><span data-stu-id="3ec95-176">Full-text change tracking maintains a record of the rows that have been modified in a table or indexed view that has been set up for full-text indexing.</span></span> <span data-ttu-id="3ec95-177">これらの変更は、フルテキスト インデックスに反映させることができます。</span><span class="sxs-lookup"><span data-stu-id="3ec95-177">These changes can be propagated to the full-text index.</span></span>  
  
 <span data-ttu-id="3ec95-178">**[変更の追跡]** の値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3ec95-178">The **Change Tracking** values are as follows:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3ec95-179">"**オフ**"</span><span class="sxs-lookup"><span data-stu-id="3ec95-179">**Off**</span></span>|<span data-ttu-id="3ec95-180">基になるデータに対する変更は、フルテキスト インデックスに反映されません。</span><span class="sxs-lookup"><span data-stu-id="3ec95-180">The full-text index is not updated with changes to the underlying data.</span></span>|  
|<span data-ttu-id="3ec95-181">**手動**</span><span class="sxs-lookup"><span data-stu-id="3ec95-181">**Manual**</span></span>|<span data-ttu-id="3ec95-182">フルテキスト インデックスは、基になるデータが変更されたときに自動的に更新されません。</span><span class="sxs-lookup"><span data-stu-id="3ec95-182">The full-text index is not updated automatically as changes occur to the underlying data.</span></span> <span data-ttu-id="3ec95-183">ただし、基になるデータに対する変更は保持されるため、SQL Server エージェントを使用して</span><span class="sxs-lookup"><span data-stu-id="3ec95-183">However, changes to the underlying data are maintained, and you can propagate them to the .</span></span> <span data-ttu-id="3ec95-184">定期的にフルテキスト インデックスに反映させたり、手動でフルテキスト インデックスに反映させたりできます。</span><span class="sxs-lookup"><span data-stu-id="3ec95-184">full-text index either on a schedule using SQL Server Agent or manually.</span></span>|  
|<span data-ttu-id="3ec95-185">**自動**</span><span class="sxs-lookup"><span data-stu-id="3ec95-185">**Automatic**</span></span>|<span data-ttu-id="3ec95-186">フルテキスト インデックスは、ベース テーブルの基になるデータが変更されたときに自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="3ec95-186">The full-text index is updated automatically as changes occur to the underlying data in the base table.</span></span>|  
  
 <span data-ttu-id="3ec95-187">**[インデックスを再作成する]**</span><span class="sxs-lookup"><span data-stu-id="3ec95-187">**Repopulate index**</span></span>  
 <span data-ttu-id="3ec95-188">ダイアログ ボックスを閉じたときにフルテキスト インデックスの作成を開始します。</span><span class="sxs-lookup"><span data-stu-id="3ec95-188">Click to start a population on the full-text index on exiting the dialog box.</span></span> <span data-ttu-id="3ec95-189">次のいずれかの種類の作成を選択します。</span><span class="sxs-lookup"><span data-stu-id="3ec95-189">Select one of the following types of population:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3ec95-190">**完全**</span><span class="sxs-lookup"><span data-stu-id="3ec95-190">**Full**</span></span>|<span data-ttu-id="3ec95-191">テーブルの完全作成中に、すべての行に対してインデックス エントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3ec95-191">During a full population of a table, index entries are built for all the rows.</span></span>|  
|<span data-ttu-id="3ec95-192">**増分**</span><span class="sxs-lookup"><span data-stu-id="3ec95-192">**Incremental**</span></span>|<span data-ttu-id="3ec95-193">増分作成では、前回の作成以降または前回の作成の実行中に追加、削除または変更された行のフルテキスト インデックスが更新されます。</span><span class="sxs-lookup"><span data-stu-id="3ec95-193">Incremental population updates the full-text index for rows added, deleted, or modified after the last population, or while the last population was in progress.</span></span> <span data-ttu-id="3ec95-194">増分作成を実行する場合は、ベース テーブルに `timestamp` データ型の列が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ec95-194">Performing an incremental population requires that the base table contain a column of the `timestamp` data type.</span></span>|  
|<span data-ttu-id="3ec95-195">**アップデート**</span><span class="sxs-lookup"><span data-stu-id="3ec95-195">**Update**</span></span>|<span data-ttu-id="3ec95-196">ベース テーブルのデータが変更されるたびに、フルテキスト インデックスが更新されます。</span><span class="sxs-lookup"><span data-stu-id="3ec95-196">The full-text index is updated whenever the data in the base table is modified.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ec95-197">参照</span><span class="sxs-lookup"><span data-stu-id="3ec95-197">See Also</span></span>  
 [<span data-ttu-id="3ec95-198">フルテキスト検索の概要</span><span class="sxs-lookup"><span data-stu-id="3ec95-198">Get Started with Full-Text Search</span></span>](../relational-databases/search/get-started-with-full-text-search.md)  
  
  
