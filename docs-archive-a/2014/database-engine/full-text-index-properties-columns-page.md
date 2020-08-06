---
title: '[フルテキストインデックスのプロパティ] ([列] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.columns.f1
ms.assetid: 75e52edb-0d07-4393-9345-8b5af4561e35
author: rothja
ms.author: jroth
ms.openlocfilehash: f947af04463948ef551c6df866d5a306c248c6b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645806"
---
# <a name="full-text-index-properties-columns-page"></a><span data-ttu-id="c1ab8-102">[フルテキスト インデックスのプロパティ] ([列] ページ)</span><span class="sxs-lookup"><span data-stu-id="c1ab8-102">Full-Text Index Properties (Columns Page)</span></span>
  <span data-ttu-id="c1ab8-103">**フルテキスト インデックスのプロパティを表示または変更するには**</span><span class="sxs-lookup"><span data-stu-id="c1ab8-103">**To view or change the properties of a full-text index**</span></span>  
  
-   [<span data-ttu-id="c1ab8-104">フルテキスト インデックスの管理</span><span class="sxs-lookup"><span data-stu-id="c1ab8-104">Manage Full-Text Indexes</span></span>](../relational-databases/indexes/indexes.md)  
  
## <a name="ui-element-list"></a><span data-ttu-id="c1ab8-105">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="c1ab8-105">UI element list</span></span>  
 <span data-ttu-id="c1ab8-106">**[一意インデックス]**</span><span class="sxs-lookup"><span data-stu-id="c1ab8-106">**Unique index**</span></span>  
 <span data-ttu-id="c1ab8-107">ドロップダウン リストからインデックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="c1ab8-107">Select an index from the drop down list.</span></span> <span data-ttu-id="c1ab8-108">インデックスは、単一キー列の、一意で NULL 値が許容されないインデックスである必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1ab8-108">The index must be a single-key-column, unique, non-nullable index.</span></span>  
  
 <span data-ttu-id="c1ab8-109">**[フルテキスト インデックスを作成する対象になる列を選択]**</span><span class="sxs-lookup"><span data-stu-id="c1ab8-109">**Select the eligible columns that will be full-text indexed**</span></span>  
 <span data-ttu-id="c1ab8-110">このフルテキスト インデックスを作成できるテーブル列がグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1ab8-110">The grid displays the table columns that are available for this full-text index.</span></span> <span data-ttu-id="c1ab8-111">現在フルテキスト インデックスが作成されている列のチェック ボックスがオンになります。</span><span class="sxs-lookup"><span data-stu-id="c1ab8-111">Columns that are currently full-text indexed are checked.</span></span> <span data-ttu-id="c1ab8-112">必要に応じて、フルテキスト インデックスを作成する追加の列のチェック ボックスをオンにすることができます。</span><span class="sxs-lookup"><span data-stu-id="c1ab8-112">Optionally, you can check additional columns that you want to be full-text indexed.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c1ab8-113">[OK] をクリックする前に、少なくとも 1 つの列のチェック ボックスがオンになっていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c1ab8-113">Ensure that at least one column is checked before you click OK.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c1ab8-114">**使用できる列**</span><span class="sxs-lookup"><span data-stu-id="c1ab8-114">**Available Columns**</span></span>|<span data-ttu-id="c1ab8-115">列名。</span><span class="sxs-lookup"><span data-stu-id="c1ab8-115">The column name.</span></span>|  
|<span data-ttu-id="c1ab8-116">**ワードブレーカーの言語**</span><span class="sxs-lookup"><span data-stu-id="c1ab8-116">**Language for Word Breaker**</span></span>|<span data-ttu-id="c1ab8-117">すべてのフルテキスト インデックス データに対する言語分析を実行するワード ブレーカーおよびステミング機能を含む言語。</span><span class="sxs-lookup"><span data-stu-id="c1ab8-117">The language whose word breakers and stemmers perform linguistic analysis on all full-text indexed data.</span></span><br /><br /> <span data-ttu-id="c1ab8-118">詳細については、「[検索用のワードブレーカーとステミング機能の構成と管理](../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)」および「[フルテキストインデックス作成時の言語の選択](../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1ab8-118">For more information, see [Configure and Manage Word Breakers and Stemmers for Search](../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md) and [Choose a Language When Creating a Full-Text Index](../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md).</span></span>|  
|<span data-ttu-id="c1ab8-119">**Type**</span><span class="sxs-lookup"><span data-stu-id="c1ab8-119">**Type**</span></span>|<span data-ttu-id="c1ab8-120">選択された列のドキュメント型を保持するテーブル列の名前。</span><span class="sxs-lookup"><span data-stu-id="c1ab8-120">The name of the table column that holds the document type of the selected column.</span></span> <span data-ttu-id="c1ab8-121">これは、読み取り専用プロパティです。</span><span class="sxs-lookup"><span data-stu-id="c1ab8-121">This is a read-only property.</span></span>|  
|<span data-ttu-id="c1ab8-122">**統計的セマンティクス**</span><span class="sxs-lookup"><span data-stu-id="c1ab8-122">**Statistical Semantics**</span></span>|<span data-ttu-id="c1ab8-123">選択されている列に対するセマンティック インデックスを有効にするかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="c1ab8-123">Select whether to enable semantic indexing for the selected column.</span></span> <span data-ttu-id="c1ab8-124">詳細については、「[セマンティック検索 &#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1ab8-124">For more information, see [Semantic Search &#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md).</span></span><br /><br /> <span data-ttu-id="c1ab8-125">**[統計的セマンティクス]** を選択する前に **[言語]** を選択した場合、選択した言語にセマンティック言語モデルが関連付けられていなければ、 **[統計的セマンティクス]** チェック ボックスは無効になります。</span><span class="sxs-lookup"><span data-stu-id="c1ab8-125">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** checkbox is disabled.</span></span> <span data-ttu-id="c1ab8-126">**[言語]** を選択する前に **[統計的セマンティクス]** を選択した場合、ドロップダウン コンボ ボックスで使用できる言語は、セマンティック言語モデルでサポートされているものだけに制限されます。</span><span class="sxs-lookup"><span data-stu-id="c1ab8-126">If you select **Statistical Semantics** prior to selecting a **Language**, the languages available in the drop-down combo box will be restricted to those for which there is Semantic Language Model support.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c1ab8-127">参照</span><span class="sxs-lookup"><span data-stu-id="c1ab8-127">See Also</span></span>  
 [<span data-ttu-id="c1ab8-128">フルテキスト インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="c1ab8-128">Populate Full-Text Indexes</span></span>](../relational-databases/search/populate-full-text-indexes.md)  
  
  
