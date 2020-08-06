---
title: '[フルテキスト インデックス] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.fulltextindex
ms.assetid: ef45b585-2567-4abe-b421-9fd0994e0146
author: stevestein
ms.author: sstein
ms.openlocfilehash: f98d3bf43707caedd8c9d0a01349f36d5a5bfbcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741505"
---
# <a name="full-text-index-dialog-box-visual-database-tools"></a><span data-ttu-id="a2fbd-102">[フルテキスト インデックス] ダイアログ ボックス (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="a2fbd-102">Full-Text Index Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="a2fbd-103">このダイアログ ボックスを使用すると、データベース テーブルのテキスト ベースの列に対するフルテキスト検索用にフルテキスト インデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-103">This dialog box allows you to create a full-text index, for full-text searches on text-based columns in your database tables.</span></span> <span data-ttu-id="a2fbd-104">フルテキスト インデックスは、通常のインデックスに基づくため、最初に通常のインデックスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-104">A full-text index relies on a regular index, so you must create that first.</span></span> <span data-ttu-id="a2fbd-105">通常のインデックスは、単一の非 null 列に作成する必要があります。大きな値を格納している列ではなく、小さな値を格納している列を選択するのが最も適切です。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-105">The regular index must be created on a single, non-null column; it is best to choose a column with small values rather than a column with large ones.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a2fbd-106">フルテキスト インデックスを作成する場合、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、Enterprise Manager などの外部ツールを使用して、あらかじめデータベースのフルテキスト カタログを作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-106">To create a full-text index, you must first create a full-text catalog for the database using an outside tool, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Enterprise Manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a2fbd-107">フルテキスト インデックスの機能は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで利用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-107">Full-text index functionality is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a2fbd-108">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-108">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a2fbd-109">オプション</span><span class="sxs-lookup"><span data-stu-id="a2fbd-109">Options</span></span>  
 <span data-ttu-id="a2fbd-110">**[選択されたフルテキスト インデックス]**</span><span class="sxs-lookup"><span data-stu-id="a2fbd-110">**Selected Full-Text Index**</span></span>  
 <span data-ttu-id="a2fbd-111">既存のフルテキスト インデックスを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-111">Lists existing full-text indexes.</span></span> <span data-ttu-id="a2fbd-112">インデックスを選択すると、右のグリッドにそのインデックスのプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-112">Select an index to show its properties in the grid to the right.</span></span> <span data-ttu-id="a2fbd-113">一覧が空の場合、テーブルにフルテキスト インデックスは定義されていません。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-113">If the list is empty, no full-text relationships have been defined for the table.</span></span>  
  
 <span data-ttu-id="a2fbd-114">**追加**</span><span class="sxs-lookup"><span data-stu-id="a2fbd-114">**Add**</span></span>  
 <span data-ttu-id="a2fbd-115">新しいフルテキスト インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-115">Create a new full-text index.</span></span>  
  
 <span data-ttu-id="a2fbd-116">**削除**</span><span class="sxs-lookup"><span data-stu-id="a2fbd-116">**Delete**</span></span>  
 <span data-ttu-id="a2fbd-117">**[選択されたフルテキスト インデックス]** ボックスの一覧で選択したフルテキスト インデックスを削除します。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-117">Delete the full-text index selected in the **Selected Full-Text Index** list.</span></span>  
  
 <span data-ttu-id="a2fbd-118">**[全般] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="a2fbd-118">**General Category**</span></span>  
 <span data-ttu-id="a2fbd-119">展開して **[列]** および **[フルテキスト カタログ名]** を表示します。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-119">When expanded, shows **Columns** and **Full-text Catalog Name**.</span></span>  
  
 <span data-ttu-id="a2fbd-120">**[列]**</span><span class="sxs-lookup"><span data-stu-id="a2fbd-120">**Columns**</span></span>  
 <span data-ttu-id="a2fbd-121">フルテキスト検索ができる列の名前を、コンマ区切りの一覧として表示します。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-121">Displays a comma-separated list of the names of full-text-searchable columns.</span></span> <span data-ttu-id="a2fbd-122">完全な一覧を表示するには、プロパティ フィールドの左側にある省略記号ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-122">To see the complete list, click the ellipsis button (**...**) to the left of the property field.</span></span>  
  
 <span data-ttu-id="a2fbd-123">**Full-Text Catalog Name**</span><span class="sxs-lookup"><span data-stu-id="a2fbd-123">**Full-Text Catalog Name**</span></span>  
 <span data-ttu-id="a2fbd-124">フルテキスト インデックスが格納されているフルテキスト カタログの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-124">Displays the name of the full-text catalog on which this full-text index is stored.</span></span> <span data-ttu-id="a2fbd-125">インデックスを別のカタログに格納するには、カタログ名をクリックし、ドロップダウン リストから別のカタログを選択します。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-125">To store the index on a different catalog, click the catalog name and choose another from the drop-down list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a2fbd-126">カタログは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または Enterprise Manager などの外部ツールで、あらかじめ作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-126">The catalog must be created first in an outside tool, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Enterprise Manager.</span></span>  
  
 <span data-ttu-id="a2fbd-127">**[IDENTITY] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="a2fbd-127">**Identity Category**</span></span>  
 <span data-ttu-id="a2fbd-128">展開してインデックスの名前フィールドを表示します。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-128">When expanded, shows the name field for this index.</span></span>  
  
 <span data-ttu-id="a2fbd-129">**Name**</span><span class="sxs-lookup"><span data-stu-id="a2fbd-129">**Name**</span></span>  
 <span data-ttu-id="a2fbd-130">システムが指定したフルテキスト インデックスの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-130">Displays the system-specified name for this full-text index.</span></span>  
  
 <span data-ttu-id="a2fbd-131">**[テーブル デザイナー] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="a2fbd-131">**Table Designer Category**</span></span>  
 <span data-ttu-id="a2fbd-132">展開してインデックスの実行方法を指定するプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-132">When expanded, shows properties that dictate how the index performs.</span></span>  
  
 <span data-ttu-id="a2fbd-133">**アクティブ**</span><span class="sxs-lookup"><span data-stu-id="a2fbd-133">**Active**</span></span>  
 <span data-ttu-id="a2fbd-134">該当するフルテキスト インデックスを使用して、フルテキスト検索を現在実行できるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-134">Indicates whether you can currently perform a full-text search using this full-text index.</span></span>  
  
 <span data-ttu-id="a2fbd-135">**[トラッキング設定の変更]**</span><span class="sxs-lookup"><span data-stu-id="a2fbd-135">**Change Tracking Setting**</span></span>  
 <span data-ttu-id="a2fbd-136">該当するインデックスの変更履歴の状態を示します。[手動]、[自動]、または [オフ]。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-136">Describes the status of change tracking for this index: Manual, Auto, or Off.</span></span>  
  
 <span data-ttu-id="a2fbd-137">**[クロールの完了]**</span><span class="sxs-lookup"><span data-stu-id="a2fbd-137">**Crawl Completed**</span></span>  
 <span data-ttu-id="a2fbd-138">最近のクロールが完了したかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-138">Shows whether the most recent crawl has been completed.</span></span> <span data-ttu-id="a2fbd-139">このプロパティ値が [いいえ] の場合、クロールは現在進行中です。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-139">If this property value is No, a crawl is currently in progress.</span></span>  
  
 <span data-ttu-id="a2fbd-140">**[現在または最近のクロールの終了日時]**</span><span class="sxs-lookup"><span data-stu-id="a2fbd-140">**End Date And Time Of Current Or Last Crawl**</span></span>  
 <span data-ttu-id="a2fbd-141">最近のクロールが終了した日時を表示します。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-141">Displays the date and time that the most recent crawl ended.</span></span>  
  
 <span data-ttu-id="a2fbd-142">**[現在または最近のクロール内のエラー]**</span><span class="sxs-lookup"><span data-stu-id="a2fbd-142">**Errors In Current Or Last Crawl**</span></span>  
 <span data-ttu-id="a2fbd-143">現在のクロールまたは最近のクロールで発生したエラーの数を表示します。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-143">Displays the number of errors in current or most recent crawl.</span></span>  
  
 <span data-ttu-id="a2fbd-144">**[インデックス バージョン]**</span><span class="sxs-lookup"><span data-stu-id="a2fbd-144">**Index Version**</span></span>  
 <span data-ttu-id="a2fbd-145">クロールが開始した時点での、テーブルのスキーマ バージョンを表示します。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-145">Displays the schema version of table at time the crawl started.</span></span>  
  
 <span data-ttu-id="a2fbd-146">**[現在または最近のクロール内の行]**</span><span class="sxs-lookup"><span data-stu-id="a2fbd-146">**Rows In Current Or Last Crawl**</span></span>  
 <span data-ttu-id="a2fbd-147">現在のクロールまたは最近のクロールで更新された行の数を表示します。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-147">Displays the number of rows updated in the current or most recent crawl.</span></span>  
  
 <span data-ttu-id="a2fbd-148">**[現在または最近のクロールの開始日時]**</span><span class="sxs-lookup"><span data-stu-id="a2fbd-148">**Start Date And Time Of Current Or Last Crawl**</span></span>  
 <span data-ttu-id="a2fbd-149">現在のクロールまたは最近のクロールが開始した日時を表示します。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-149">Displays the date and time that the current or most recent crawl started.</span></span>  
  
 <span data-ttu-id="a2fbd-150">**[次のクロールのタイムスタンプ]**</span><span class="sxs-lookup"><span data-stu-id="a2fbd-150">**Time Stamp For Next Crawl**</span></span>  
 <span data-ttu-id="a2fbd-151">次のクロールが開始する日時を表示します。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-151">Displays the date and time that the next crawl will start.</span></span>  
  
 <span data-ttu-id="a2fbd-152">**[現在または最近のクロールの種類]**</span><span class="sxs-lookup"><span data-stu-id="a2fbd-152">**Type Of Current Or Last Crawl**</span></span>  
 <span data-ttu-id="a2fbd-153">現在のクロールまたは最近のクロールの型を表示します。[空き領域なし]、[インクリメンタル]、[更新]、または [自動伝達]。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-153">Displays the type of the current or most recent crawl: Full, Incremental, Update, or Auto Propagation.</span></span>  
  
 <span data-ttu-id="a2fbd-154">**[一意のインデックス名]**</span><span class="sxs-lookup"><span data-stu-id="a2fbd-154">**Unique Index Name**</span></span>  
 <span data-ttu-id="a2fbd-155">一意の単一列インデックスを持つ、データベース内のすべての列の名前を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-155">Displays a list of all of the names of columns in this database that have unique single-column indexes.</span></span> <span data-ttu-id="a2fbd-156">これらの列は、フルテキスト インデックスの作成に使用できます。</span><span class="sxs-lookup"><span data-stu-id="a2fbd-156">These columns can be used to create a full-text index.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2fbd-157">参照</span><span class="sxs-lookup"><span data-stu-id="a2fbd-157">See Also</span></span>  
 <span data-ttu-id="a2fbd-158">[フルテキストインデックス作成ウィザードの使用](../../relational-databases/search/use-the-full-text-indexing-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="a2fbd-158">[Use the Full-Text Indexing Wizard](../../relational-databases/search/use-the-full-text-indexing-wizard.md) </span></span>  
 [<span data-ttu-id="a2fbd-159">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a2fbd-159">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-index-transact-sql)  
  
  
