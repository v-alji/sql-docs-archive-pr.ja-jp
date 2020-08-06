---
title: フルテキスト インデックス作成ウィザードの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextindexingwizard.selecttablecolumns.f1
- sql12.swb.fulltextindexingwizard.welcome.f1
- sql12.swb.fulltextindexingwizard.selectacatalog.f1
- sql12.swb.fulltextindexingwizard.progress.f1
- sql12.swb.fulltextindexingwizard.selectorcreatepopschedules.f1
- sql12.swb.fulltextindexingwizard.selectatableorview.f1
- sql12.swb.fulltextindexingwizard.selectchangetracking.f1
- sql12.swb.fulltextindexingwizard.selectanindex.f1
- sql12.swb.fulltextindexingwizard.summary.f1
helpviewer_keywords:
- Full-Text Indexing Wizard
- full-text search [SQL Server], Full-Text Indexing Wizard
ms.assetid: 3e9d9605-6525-4781-9168-fdaa06db3459
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5ef8a23c4d85cbe47bf6bdb47eb3f45723f1559d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714101"
---
# <a name="use-the-full-text-indexing-wizard"></a><span data-ttu-id="ede8c-102">フルテキスト インデックス作成ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="ede8c-102">Use the Full-Text Indexing Wizard</span></span>
  <span data-ttu-id="ede8c-103">フルテキスト インデックス作成ウィザードを使用すると、フルテキスト インデックスを作成するために作られた一連の手順を実行できます。</span><span class="sxs-lookup"><span data-stu-id="ede8c-103">The Full-Text Indexing Wizard walks you through a series of steps designed to help you create a full-text index.</span></span>  
  
#### <a name="to-use-the-full-text-indexing-wizard"></a><span data-ttu-id="ede8c-104">フルテキスト インデックス作成ウィザードを使用するには</span><span class="sxs-lookup"><span data-stu-id="ede8c-104">To use the Full-Text Indexing wizard</span></span>  
  
1.  <span data-ttu-id="ede8c-105">オブジェクト エクスプローラーで、フルテキスト インデックスを作成するテーブルを右クリックして **[フルテキスト インデックス]** をポイントし、 **[フルテキスト インデックスの定義]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede8c-105">In Object Explorer, right-click the table on which you want to create a full-text index, point to **Full-Text index**, and then click **Define Full-Text Index**.</span></span>  
  
     <span data-ttu-id="ede8c-106">**一意のインデックス**</span><span class="sxs-lookup"><span data-stu-id="ede8c-106">**Unique Index**</span></span>  
     <span data-ttu-id="ede8c-107">ドロップダウン リストからインデックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-107">Select an index from the drop down list.</span></span> <span data-ttu-id="ede8c-108">インデックスは、単一キー列の、一意で NULL 値が許容されないインデックスである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ede8c-108">The index must be a single-key-column, unique, non-nullable index.</span></span> <span data-ttu-id="ede8c-109">フルテキストの一意キーには、一番小さな一意キー インデックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-109">Select the smallest unique key index for the full-text unique key.</span></span> <span data-ttu-id="ede8c-110">最高のパフォーマンスを得るためには、クラスター化インデックスをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ede8c-110">For best performance, a clustered index is recommended.</span></span>  
  
     <span data-ttu-id="ede8c-111">**使用できる列**</span><span class="sxs-lookup"><span data-stu-id="ede8c-111">**Available Columns**</span></span>  
     <span data-ttu-id="ede8c-112">列をインデックスに含めるには、列名の横のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="ede8c-112">To include a column in the index, select the check box next to the column name.</span></span> <span data-ttu-id="ede8c-113">フルテキスト インデックス作成の対象ではない列は、グレー表示され、チェック ボックスはオフになっています。</span><span class="sxs-lookup"><span data-stu-id="ede8c-113">Columns that are not eligible for full-text indexing appear in grey with their check boxes disabled.</span></span>  
  
     <span data-ttu-id="ede8c-114">**ワードブレーカーの言語**</span><span class="sxs-lookup"><span data-stu-id="ede8c-114">**Language for Word Breaker**</span></span>  
     <span data-ttu-id="ede8c-115">ドロップダウン リストから言語を選択します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-115">Select a language from the drop-down list.</span></span> <span data-ttu-id="ede8c-116">この選択は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でインデックスに適したワード ブレーカーを識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ede8c-116">This choice will be used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to identify the correct word breakers for the index.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ede8c-117">は、ワード ブレーカーを使用してフルテキスト インデックス付きデータ内の単語の境界を識別します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-117">uses word breakers to identify word boundaries in the full-text indexed data.</span></span>  
  
     <span data-ttu-id="ede8c-118">**型の列**</span><span class="sxs-lookup"><span data-stu-id="ede8c-118">**Type Column**</span></span>  
     <span data-ttu-id="ede8c-119">フルテキスト インデックスの付いた列の文書型を保持する列の名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-119">Select the name of the column that holds the document type of column being full-text indexed.</span></span>  
  
     <span data-ttu-id="ede8c-120">[**型列**を有効にするのは、**使用できる列**の列の名前が `varbinary(max)` またはの場合のみです `image` 。</span><span class="sxs-lookup"><span data-stu-id="ede8c-120">The  **Type Column** is only enabled when the column named in the **Available Columns** column is of type `varbinary(max)` or `image`.</span></span>  
  
     <span data-ttu-id="ede8c-121">**統計的セマンティクス**</span><span class="sxs-lookup"><span data-stu-id="ede8c-121">**Statistical Semantics**</span></span>  
     <span data-ttu-id="ede8c-122">選択されている列に対するセマンティック インデックスを有効にするかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-122">Select whether to enable semantic indexing for the selected column.</span></span> <span data-ttu-id="ede8c-123">詳細については、「[セマンティック検索 &#40;SQL Server&#41;](semantic-search-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ede8c-123">For more information, see [Semantic Search &#40;SQL Server&#41;](semantic-search-sql-server.md).</span></span>  
  
     <span data-ttu-id="ede8c-124">**[統計的セマンティクス]** を選択する前に **[言語]** を選択した場合、選択した言語にセマンティック言語モデルが関連付けられていなければ、 **[統計的セマンティクス]** チェック ボックスは無効になります。</span><span class="sxs-lookup"><span data-stu-id="ede8c-124">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** checkbox is disabled.</span></span> <span data-ttu-id="ede8c-125">**[言語]** を選択する前に **[統計的セマンティクス]** を選択した場合、ドロップダウン コンボ ボックスで使用できる言語は、セマンティック言語モデルでサポートされているものだけに制限されます。</span><span class="sxs-lookup"><span data-stu-id="ede8c-125">If you select **Statistical Semantics** prior to selecting a **Language**, the languages available in the drop-down combo box will be restricted to those for which there is Semantic Language Model support.</span></span>  
  
2.  <span data-ttu-id="ede8c-126">変更追跡オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-126">Select the change tracking options.</span></span>  
  
     <span data-ttu-id="ede8c-127">**[自動]**</span><span class="sxs-lookup"><span data-stu-id="ede8c-127">**Automatically**</span></span>  
     <span data-ttu-id="ede8c-128">基底のデータの変更に合わせて自動的にフルテキスト インデックスが更新されるようにするには、このオプション ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede8c-128">Select this radio button to have the full-text index updated automatically as changes occur to the underlying data.</span></span>  
  
     <span data-ttu-id="ede8c-129">**で**</span><span class="sxs-lookup"><span data-stu-id="ede8c-129">**Manually**</span></span>  
     <span data-ttu-id="ede8c-130">基底のデータの変更に合わせて自動的にフルテキスト インデックスが更新されないようにするには、このオプション ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede8c-130">Select this radio button if you do not want the full-text index to be updated automatically as changes occur to the underlying data.</span></span> <span data-ttu-id="ede8c-131">基底のデータに対する変更は保持されます。</span><span class="sxs-lookup"><span data-stu-id="ede8c-131">Changes to the underlying data are maintained.</span></span> <span data-ttu-id="ede8c-132">ただし、変更をフルテキスト インデックスに適用するには、このプロセスを手動で開始またはスケジュール設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ede8c-132">However, to apply the changes to the full-text index you must start or schedule this process manually.</span></span>  
  
     <span data-ttu-id="ede8c-133">**[変更を追跡しない]**</span><span class="sxs-lookup"><span data-stu-id="ede8c-133">**Do not track changes**</span></span>  
     <span data-ttu-id="ede8c-134">基底のデータの変更に合わせてフルテキスト インデックスが更新されないようにするには、このオプション ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede8c-134">Select this radio button if you do not want the full-text index to be updated with changes to the underlying data.</span></span>  
  
     <span data-ttu-id="ede8c-135">**[インデックスの作成時にすべてのカタログの作成を開始する]**</span><span class="sxs-lookup"><span data-stu-id="ede8c-135">**Start full population when index is created**</span></span>  
     <span data-ttu-id="ede8c-136">このウィザードが正常終了したときにすべてのカタログの作成を開始するには、このオプション ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede8c-136">Select this radio button to kick off a full population at the successful completion of this wizard.</span></span> <span data-ttu-id="ede8c-137">この処理は、フルテキスト インデックス構造体をカタログに作成する処理と、フルテキスト インデックス データを格納する処理から構成されます。</span><span class="sxs-lookup"><span data-stu-id="ede8c-137">This will consist of creating the full-text index structure in the catalog and populating it with full-text indexed data.</span></span>  
  
3.  <span data-ttu-id="ede8c-138">カタログ、インデックス ファイル グループ、およびストップリストを選択します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-138">Select the catalog, index filegroup and stoplist.</span></span>  
  
     <span data-ttu-id="ede8c-139">**[フルテキスト カタログの選択]**</span><span class="sxs-lookup"><span data-stu-id="ede8c-139">**Select full-text catalog**</span></span>  
     <span data-ttu-id="ede8c-140">フルテキスト カタログを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-140">Select a full-text catalog from the list.</span></span> <span data-ttu-id="ede8c-141">データベースの既定のカタログが一覧の既定の選択項目となります。</span><span class="sxs-lookup"><span data-stu-id="ede8c-141">The default catalog for the database will be the selected item by default in the list.</span></span> <span data-ttu-id="ede8c-142">カタログが存在しない場合、一覧は無効になり、 **[カタログの新規作成]** チェック ボックスはオンのまま変更できなくなります。</span><span class="sxs-lookup"><span data-stu-id="ede8c-142">If no catalogs are available, the list will be disabled, and the **Create a new catalog** checkbox will be checked and disabled.</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="ede8c-143">**新しいカタログを作成する**</span><span class="sxs-lookup"><span data-stu-id="ede8c-143">**Create a new catalog**</span></span>|<span data-ttu-id="ede8c-144">新しいフルテキスト カタログを作成する場合は、オンにします。</span><span class="sxs-lookup"><span data-stu-id="ede8c-144">Select to create a new full-text catalog.</span></span>|  
  
     <span data-ttu-id="ede8c-145">**名前**</span><span class="sxs-lookup"><span data-stu-id="ede8c-145">**Name**</span></span>  
     <span data-ttu-id="ede8c-146">新しいフルテキスト カタログの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-146">Enter a name for the new full-text catalog.</span></span>  
  
     <span data-ttu-id="ede8c-147">**[既定のカタログとして設定する]**</span><span class="sxs-lookup"><span data-stu-id="ede8c-147">**Set as default catalog**</span></span>  
     <span data-ttu-id="ede8c-148">このカタログをこのデータベースの既定のカタログにする場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-148">Select to make the catalog the default for this database.</span></span>  
  
     <span data-ttu-id="ede8c-149">**[アクセントの区別]**</span><span class="sxs-lookup"><span data-stu-id="ede8c-149">**Accent sensitivity**</span></span>  
     <span data-ttu-id="ede8c-150">新しいカタログでアクセントが区別されるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-150">Specify whether the new catalog will be accent-sensitive or accent-insensitive.</span></span> <span data-ttu-id="ede8c-151">データベースでアクセントが区別される場合は、**[区別する]** が既定で選択されます。</span><span class="sxs-lookup"><span data-stu-id="ede8c-151">If the database is accent-sensitive, **Sensitive** will be selected by default.</span></span>  
  
     <span data-ttu-id="ede8c-152">**[インデックス ファイル グループの選択]**</span><span class="sxs-lookup"><span data-stu-id="ede8c-152">**Select index filegroup**</span></span>  
     <span data-ttu-id="ede8c-153">フルテキスト インデックスを作成するファイル グループを指定します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-153">Specify the filegroup on which to create the full-text index.</span></span>  
  
     <span data-ttu-id="ede8c-154">次のいずれかの値を選択します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-154">Select one of the following values:</span></span>  
  
    |<span data-ttu-id="ede8c-155">値</span><span class="sxs-lookup"><span data-stu-id="ede8c-155">Value</span></span>|<span data-ttu-id="ede8c-156">説明</span><span class="sxs-lookup"><span data-stu-id="ede8c-156">Description</span></span>|  
    |-----------|-----------------|  
    |**\<default>**|<span data-ttu-id="ede8c-157">テーブルまたはビューがパーティション分割されていない場合に、基になるテーブルまたはビューと同じファイル グループを使用するには、この値を選択します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-157">If the table or view is not partitioned, select to use the same filegroup as the underlying table or view.</span></span> <span data-ttu-id="ede8c-158">テーブルまたはビューがパーティション分割されている場合は、プライマリ ファイル グループが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ede8c-158">If the table or view is partitioned, the primary filegroup is used.</span></span>|  
    |<span data-ttu-id="ede8c-159">**PRIMARY**</span><span class="sxs-lookup"><span data-stu-id="ede8c-159">**PRIMARY**</span></span>|<span data-ttu-id="ede8c-160">新しいフルテキスト インデックスにプライマリ ファイル グループを使用する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-160">Select to use the primary filegroup for the new full-text index.</span></span>|  
    |<span data-ttu-id="ede8c-161">*ユーザー指定の既定のファイル グループ*</span><span class="sxs-lookup"><span data-stu-id="ede8c-161">*user-specified default filegroup*</span></span>|<span data-ttu-id="ede8c-162">ユーザー定義の既定のストップリストが存在する場合に、新しいフルテキスト インデックスにそのファイル グループを使用するには、一覧からそのストップリストの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-162">If a user-defined default stoplist exists, select its name from the list to use that filegroup for the new full-text index.</span></span>|  
  
     <span data-ttu-id="ede8c-163">**[フルテキスト ストップリストの選択]**</span><span class="sxs-lookup"><span data-stu-id="ede8c-163">**Select full-text stoplist**</span></span>  
     <span data-ttu-id="ede8c-164">フルテキスト インデックスに使用するストップリストを指定します。または、ストップリストの使用を無効にします。</span><span class="sxs-lookup"><span data-stu-id="ede8c-164">Specify a stoplist to use for the full-text index, or disable stoplist use.</span></span>  
  
     <span data-ttu-id="ede8c-165">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンでは、ストップワードが、ストップリストと呼ばれるオブジェクトを使用してデータベースで管理されます。</span><span class="sxs-lookup"><span data-stu-id="ede8c-165">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions, stopwords are managed in databases using objects called stoplists.</span></span> <span data-ttu-id="ede8c-166">*ストップリスト* は、フルテキスト インデックスに関連付けられている場合、そのインデックスのフルテキスト クエリに適用されるストップワードの一覧です。</span><span class="sxs-lookup"><span data-stu-id="ede8c-166">A *stoplist* is a list of stopwords that, when associated with a full-text index, is applied to full-text queries on that index.</span></span> <span data-ttu-id="ede8c-167">詳細については、「 [フルテキスト検索に使用するストップワードとストップリストの構成と管理](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ede8c-167">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).</span></span>  
  
     <span data-ttu-id="ede8c-168">次のいずれかの値を選択します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-168">Select one of the following values:</span></span>  
  
    |<span data-ttu-id="ede8c-169">値</span><span class="sxs-lookup"><span data-stu-id="ede8c-169">Value</span></span>|<span data-ttu-id="ede8c-170">説明</span><span class="sxs-lookup"><span data-stu-id="ede8c-170">Description</span></span>|  
    |-----------|-----------------|  
    |**\<system>**|<span data-ttu-id="ede8c-171">新しいフルテキスト インデックスに対してシステム ストップリストを使用する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-171">Select to use the system stoplist on the new full-text index.</span></span> <span data-ttu-id="ede8c-172">これは既定値です。</span><span class="sxs-lookup"><span data-stu-id="ede8c-172">This is the default</span></span>|  
    |**\<off>**|<span data-ttu-id="ede8c-173">新しいフルテキスト インデックスに対してストップリストを無効にする場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-173">Select to disable stoplists for the new full-text index.</span></span>|  
    |<span data-ttu-id="ede8c-174">*ユーザー定義のストップ リスト名*</span><span class="sxs-lookup"><span data-stu-id="ede8c-174">*user-defined-stoplist-name*</span></span>|<span data-ttu-id="ede8c-175">ユーザー定義のストップリストがデータベース上に作成されている場合は、その名前が一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="ede8c-175">The list displays the name of each user-defined stoplist, if any, that has been created on the database.</span></span> <span data-ttu-id="ede8c-176">その場合に、新しいフルテキスト インデックスに対して使用するユーザー定義のストップリストを選択します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-176">Select any user-defined stoplist to use for the new full-text index.</span></span>|  
  
4.  <span data-ttu-id="ede8c-177">必要に応じて、作成スケジュールを定義します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-177">Optionally, define the population schedule.</span></span> <span data-ttu-id="ede8c-178">インデックス作成操作は、後で実行するようにスケジュールされていない限り、即座に開始されます。</span><span class="sxs-lookup"><span data-stu-id="ede8c-178">Indexing operations will begin immediately unless they have been scheduled for future execution.</span></span> <span data-ttu-id="ede8c-179">スケジュールは即座に作成されますが、予定時刻になるまでは実行されません。</span><span class="sxs-lookup"><span data-stu-id="ede8c-179">Schedules will be created immediately, although they will not run until their scheduled time.</span></span>  
  
     <span data-ttu-id="ede8c-180">**[新しいテーブル スケジュール]**</span><span class="sxs-lookup"><span data-stu-id="ede8c-180">**New Table Schedule**</span></span>  
     <span data-ttu-id="ede8c-181">テーブルの作成スケジュールを定義します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-181">Define a population schedule for a table.</span></span>  
  
     <span data-ttu-id="ede8c-182">**[新しいカタログ スケジュール]**</span><span class="sxs-lookup"><span data-stu-id="ede8c-182">**New Catalog Schedule**</span></span>  
     <span data-ttu-id="ede8c-183">フルテキスト カタログの作成スケジュールを定義します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-183">Define a population schedule for a full-text catalog.</span></span>  
  
     <span data-ttu-id="ede8c-184">**[編集]**</span><span class="sxs-lookup"><span data-stu-id="ede8c-184">**Edit**</span></span>  
     <span data-ttu-id="ede8c-185">スケジュールを編集します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-185">Edit a schedule.</span></span>  
  
     <span data-ttu-id="ede8c-186">**削除**</span><span class="sxs-lookup"><span data-stu-id="ede8c-186">**Delete**</span></span>  
     <span data-ttu-id="ede8c-187">スケジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-187">Delete a schedule.</span></span>  
  
5.  <span data-ttu-id="ede8c-188">フルテキスト インデックス作成ウィザードの進行状況を表示または制御します。</span><span class="sxs-lookup"><span data-stu-id="ede8c-188">View or control the progress of the Full-Text Indexing Wizard.</span></span>  
  
     <span data-ttu-id="ede8c-189">**Stop**</span><span class="sxs-lookup"><span data-stu-id="ede8c-189">**Stop**</span></span>  
     <span data-ttu-id="ede8c-190">現在の操作を中断し、このセッション中にウィザードによって後続のフルテキスト操作が実行されないようにします。</span><span class="sxs-lookup"><span data-stu-id="ede8c-190">Interrupts the current operation and prevents subsequent full-text operations from being performed by the wizard during this session.</span></span>  
  
     <span data-ttu-id="ede8c-191">**Report**</span><span class="sxs-lookup"><span data-stu-id="ede8c-191">**Report**</span></span>  
     <span data-ttu-id="ede8c-192">すべての操作の実行が完了しているときにこのボタンをクリックすると、実行された操作に関するレポートにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ede8c-192">When all of the operations have finished executing, click this button to access a report on the operations performed.</span></span> <span data-ttu-id="ede8c-193">レポートは、表示したり、ファイルに保存したりできます。また、クリップボードにコピーしたり、電子メールで送信したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ede8c-193">You can view the report, print it to a file, copy it to the clipboard, or e-mail the report.</span></span>  
  
  
