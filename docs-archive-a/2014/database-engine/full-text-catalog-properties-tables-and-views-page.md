---
title: '[フルテキストカタログのプロパティ] ([テーブルとビュー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.tablesviews.f1
ms.assetid: 2d45fcd2-0f0f-4167-9027-316d6696c106
author: rothja
ms.author: jroth
ms.openlocfilehash: eb4d968af6c550d19fbb8934b5d76a1bd63cb8da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740291"
---
# <a name="full-text-catalog-properties-tables-and-views-page"></a><span data-ttu-id="9b95e-102">[フルテキスト カタログのプロパティ] ([テーブルとビュー] ページ)</span><span class="sxs-lookup"><span data-stu-id="9b95e-102">Full-Text Catalog Properties (Tables and Views Page)</span></span>
  <span data-ttu-id="9b95e-103">このダイアログ ページを使用すると、フルテキスト カタログに割り当てられたテーブルおよびビューを表示したり、変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="9b95e-103">Use this dialog page to view or modify the tables and views that are assigned to the full-text catalog.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="9b95e-104">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="9b95e-104">UI element list</span></span>  
 <span data-ttu-id="9b95e-105">**[このデータベース内で対象になるすべてのテーブル/ビュー オブジェクト]**</span><span class="sxs-lookup"><span data-stu-id="9b95e-105">**All eligible table/view objects in this database**</span></span>  
 <span data-ttu-id="9b95e-106">一意のインデックスが定義されていて、まだフルテキスト カタログに割り当てられていないテーブルおよびビューを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9b95e-106">Lists the tables and views that have a unique index defined on them, but are not already a part of the full-text catalog.</span></span> <span data-ttu-id="9b95e-107">テーブルまたはビューを選択してカタログに割り当てるには、リストボックス内の項目を選択し、[->] ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="9b95e-107">To select a table or view and assign it to the catalog, select the items in the list box and press the "->" button.</span></span>  
  
 <span data-ttu-id="9b95e-108">**[カタログに割り当てられたテーブル/ビュー オブジェクト]**</span><span class="sxs-lookup"><span data-stu-id="9b95e-108">**Table/view objects assigned to the catalog**</span></span>  
 <span data-ttu-id="9b95e-109">現在フル テキスト カタログに割り当てられているテーブルおよびビューを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9b95e-109">Lists the tables and views that are currently assigned to the full-text catalog</span></span>  
  
## <a name="selected-object-properties"></a><span data-ttu-id="9b95e-110">[選択したオブジェクトのプロパティ]</span><span class="sxs-lookup"><span data-stu-id="9b95e-110">Selected Object Properties</span></span>  
 <span data-ttu-id="9b95e-111">**選択したオブジェクトのプロパティ**</span><span class="sxs-lookup"><span data-stu-id="9b95e-111">**Selected object properties**</span></span>  
 <span data-ttu-id="9b95e-112">カタログに割り当てられたオブジェクトのリスト ボックスで選択したオブジェクトのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="9b95e-112">Displays the properties of the selected object in the list box of objects assigned to the catalog.</span></span>  
  
 <span data-ttu-id="9b95e-113">**一意のインデックス**</span><span class="sxs-lookup"><span data-stu-id="9b95e-113">**Unique Index**</span></span>  
 <span data-ttu-id="9b95e-114">テーブルまたはビューの利用可能な一意インデックスを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9b95e-114">Lists the available unique indexes of the table or view.</span></span>  
  
 <span data-ttu-id="9b95e-115">**[テーブルのフルテキストを有効にする]**</span><span class="sxs-lookup"><span data-stu-id="9b95e-115">**Table is full-text enabled**</span></span>  
 <span data-ttu-id="9b95e-116">テーブルのフルテキスト インデックスを有効にする場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="9b95e-116">Select this check box to enable the full-text index on the table.</span></span> <span data-ttu-id="9b95e-117">フルテキスト インデックスを無効にする場合は、チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="9b95e-117">Clear the check box to disable the full-text index.</span></span>  
  
## <a name="eligible-columns-grid"></a><span data-ttu-id="9b95e-118">[対象になる列] グリッド</span><span class="sxs-lookup"><span data-stu-id="9b95e-118">Eligible Columns Grid</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9b95e-119">**使用できる列**</span><span class="sxs-lookup"><span data-stu-id="9b95e-119">**Available Columns**</span></span>|<span data-ttu-id="9b95e-120">フルテキスト インデックス付きの列をすべて表示します。</span><span class="sxs-lookup"><span data-stu-id="9b95e-120">Displays all the columns that are full-text indexed.</span></span> <span data-ttu-id="9b95e-121">フルテキスト インデックスに列を追加する場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="9b95e-121">Select a check box to add a column to the full-text index.</span></span>|  
|<span data-ttu-id="9b95e-122">**ワードブレーカーの言語**</span><span class="sxs-lookup"><span data-stu-id="9b95e-122">**Language for Word Breaker**</span></span>|<span data-ttu-id="9b95e-123">ワード ブレーカーの言語を表示します。</span><span class="sxs-lookup"><span data-stu-id="9b95e-123">Displays the language of the word breaker.</span></span>|  
|<span data-ttu-id="9b95e-124">**[型列]**</span><span class="sxs-lookup"><span data-stu-id="9b95e-124">**Data Type Column**</span></span>|<span data-ttu-id="9b95e-125">列が列または列の場合は、[**使用できる列**の種類の一覧を保持するテーブル内の列の名前を一覧表示し `varbinary(max)` `image` ます。</span><span class="sxs-lookup"><span data-stu-id="9b95e-125">Lists the name of the column in the table that holds the document type of the column listed in **Available Columns** if the column is a `varbinary(max)` or `image` column.</span></span>|  
|<span data-ttu-id="9b95e-126">**統計的セマンティクス**</span><span class="sxs-lookup"><span data-stu-id="9b95e-126">**Statistical Semantics**</span></span>|<span data-ttu-id="9b95e-127">選択されている列に対するセマンティック インデックスを有効にするかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="9b95e-127">Select whether to enable semantic indexing for the selected column.</span></span> <span data-ttu-id="9b95e-128">詳細については、「[セマンティック検索 &#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b95e-128">For more information, see [Semantic Search &#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md).</span></span><br /><br /> <span data-ttu-id="9b95e-129">**[統計的セマンティクス]** を選択する前に **[言語]** を選択した場合、選択した言語にセマンティック言語モデルが関連付けられていなければ、 **[統計的セマンティクス]** チェック ボックスは無効になります。</span><span class="sxs-lookup"><span data-stu-id="9b95e-129">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** checkbox is disabled.</span></span> <span data-ttu-id="9b95e-130">**[言語]** を選択する前に **[統計的セマンティクス]** を選択した場合、ドロップダウン コンボ ボックスで使用できる言語は、セマンティック言語モデルでサポートされているものだけに制限されます。</span><span class="sxs-lookup"><span data-stu-id="9b95e-130">If you select **Statistical Semantics** prior to selecting a **Language**, the languages available in the drop-down combo box will be restricted to those for which there is Semantic Language Model support.</span></span>|  
  
## <a name="track-changes"></a><span data-ttu-id="9b95e-131">[変更の追跡]</span><span class="sxs-lookup"><span data-stu-id="9b95e-131">Track Changes</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9b95e-132">**自動**</span><span class="sxs-lookup"><span data-stu-id="9b95e-132">**Automatic**</span></span>|<span data-ttu-id="9b95e-133">基になるテーブル内のデータが変更、追加、または削除されると、フルテキスト インデックスは自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="9b95e-133">The full-text index is automatically updated when the data in the underlying table is modified, added, or deleted.</span></span>|  
|<span data-ttu-id="9b95e-134">**手動**</span><span class="sxs-lookup"><span data-stu-id="9b95e-134">**Manual**</span></span>|<span data-ttu-id="9b95e-135">インデックス付きデータのデータが変更、追加、または削除されると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は変更を追跡します。</span><span class="sxs-lookup"><span data-stu-id="9b95e-135">When data is modified, added, or deleted in the indexed data, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tracks the changes.</span></span> <span data-ttu-id="9b95e-136">**[手動]** による変更の追跡が選択されている場合、インデックスはこれらの変更によって自動的に更新されません。</span><span class="sxs-lookup"><span data-stu-id="9b95e-136">When **Manual** change tracking is in effect, the index is not automatically updated with these changes.</span></span> <span data-ttu-id="9b95e-137">代わりに、管理者は [ALTER FULLTEXT INDEX ... START UPDATE POPULATION](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ステートメントを使用して変更を手動で適用できます。</span><span class="sxs-lookup"><span data-stu-id="9b95e-137">Instead, an administrator can apply the changes manually by using an [ALTER FULLTEXT INDEX ... START UPDATE POPULATION](/sql/t-sql/statements/alter-fulltext-index-transact-sql) statement.</span></span>|  
|<span data-ttu-id="9b95e-138">**[変更を追跡しない]**</span><span class="sxs-lookup"><span data-stu-id="9b95e-138">**Do not track change**</span></span>|<span data-ttu-id="9b95e-139">このオプションが有効になっていると、カタログ内のインデックス付きデータへの変更は記録されません。</span><span class="sxs-lookup"><span data-stu-id="9b95e-139">With this option in effect, changes to the indexed data in the catalog are not recorded.</span></span> <span data-ttu-id="9b95e-140">管理者は、FULL POPULATION または INCREMENTAL POPULATION のいずれかで ALTER FULLTEXT INDEX を使用してインデックスを構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b95e-140">An administrator must build the index by using ALTER FULLTEXT INDEX with either FULL POPULATION or INCREMENTAL POPULATION.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9b95e-141">参照</span><span class="sxs-lookup"><span data-stu-id="9b95e-141">See Also</span></span>  
 <span data-ttu-id="9b95e-142">[CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9b95e-142">[CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) </span></span>  
 <span data-ttu-id="9b95e-143">[Transact-sql&#41;&#40;のフルテキストカタログの変更](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9b95e-143">[ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql) </span></span>  
 [<span data-ttu-id="9b95e-144">フルテキスト インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="9b95e-144">Populate Full-Text Indexes</span></span>](../relational-databases/indexes/indexes.md)  
  
  
