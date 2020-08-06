---
title: フルテキストストップリストのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftstoplistproperties.general.f1
- sql12.swb.fulltextsearch.ftstoplistproperties.schedule.f1
ms.assetid: 2e907f5b-0cf9-484a-afcf-a4e7f1e2f87f
author: rothja
ms.author: jroth
ms.openlocfilehash: 4ff27a1258d5164e3e93d34b6ff757993d6f6363
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645795"
---
# <a name="full-text-stoplist-properties"></a><span data-ttu-id="69145-102">[フルテキスト ストップリストのプロパティ]</span><span class="sxs-lookup"><span data-stu-id="69145-102">Full-Text Stoplist Properties</span></span>
  <span data-ttu-id="69145-103">このダイアログ ボックスを使用すると、個々のストップワードの追加や削除、特定の言語のすべてのストップワードの削除、および現在のストップリストのクリアを実行できます。</span><span class="sxs-lookup"><span data-stu-id="69145-103">Use this dialog box to add or delete individual stopwords, delete all stopwords for a specific language, or clear the current stoplist.</span></span> <span data-ttu-id="69145-104">ストップワードは、ストップリストで一般的に使用される単語です。</span><span class="sxs-lookup"><span data-stu-id="69145-104">A stopword is a commonly used word that is included in a stoplist.</span></span> <span data-ttu-id="69145-105">ストップリスト内のストップワードは、ストップリストを使用するテーブルのフルテキスト インデックスから省略されます。</span><span class="sxs-lookup"><span data-stu-id="69145-105">The stopwords in a stoplist are omitted from full-text indexing for tables that use the stoplist.</span></span> <span data-ttu-id="69145-106">詳細については、「 [フルテキスト検索に使用するストップワードとストップリストの構成と管理](../relational-databases/search/full-text-search.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69145-106">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](../relational-databases/search/full-text-search.md).</span></span>  
  
 <span data-ttu-id="69145-107">**SQL Server Management Studio を使用してストップリストのプロパティを変更するには**</span><span class="sxs-lookup"><span data-stu-id="69145-107">**To use SQL Server Management Studio to change stoplist properties**</span></span>  
  
-   [<span data-ttu-id="69145-108">フルテキスト検索に使用するストップワードとストップリストの構成と管理</span><span class="sxs-lookup"><span data-stu-id="69145-108">Configure and Manage Stopwords and Stoplists for Full-Text Search</span></span>](../relational-databases/search/full-text-search.md)  
  
## <a name="options"></a><span data-ttu-id="69145-109">Options</span><span class="sxs-lookup"><span data-stu-id="69145-109">Options</span></span>  
 <span data-ttu-id="69145-110">**操作**</span><span class="sxs-lookup"><span data-stu-id="69145-110">**Action**</span></span>  
 <span data-ttu-id="69145-111">実行するアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="69145-111">Specifies the action that you want to perform.</span></span>  
  
 <span data-ttu-id="69145-112">**[ストップワードの追加]**</span><span class="sxs-lookup"><span data-stu-id="69145-112">**Add stopword**</span></span>  
 <span data-ttu-id="69145-113">一般的に使用される単語をストップリストに追加します。</span><span class="sxs-lookup"><span data-stu-id="69145-113">Add a commonly used word to the stoplist.</span></span>  
  
 <span data-ttu-id="69145-114">**[ストップワードの削除]**</span><span class="sxs-lookup"><span data-stu-id="69145-114">**Delete stopword**</span></span>  
 <span data-ttu-id="69145-115">ストップリストからストップワードを削除します。</span><span class="sxs-lookup"><span data-stu-id="69145-115">Delete a stopword from the stoplist.</span></span>  
  
 <span data-ttu-id="69145-116">**[すべてのストップワードの削除]**</span><span class="sxs-lookup"><span data-stu-id="69145-116">**Delete all stopwords**</span></span>  
 <span data-ttu-id="69145-117">特定の言語のストップワードをすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="69145-117">Delete all the stopwords for a specific language.</span></span>  
  
 <span data-ttu-id="69145-118">**[ストップリストのクリア]**</span><span class="sxs-lookup"><span data-stu-id="69145-118">**Clear stoplist**</span></span>  
 <span data-ttu-id="69145-119">すべての言語のストップワードをすべて削除することによって、ストップリストをクリアします。</span><span class="sxs-lookup"><span data-stu-id="69145-119">Clear the stoplist by deleting all the stopwords for all languages.</span></span>  
  
 <span data-ttu-id="69145-120">**ストップワード**</span><span class="sxs-lookup"><span data-stu-id="69145-120">**Stopword**</span></span>  
 <span data-ttu-id="69145-121">**[ストップワードの追加]** または **[ストップワードの削除]** を選択した場合は、 **[ストップワード]** フィールドにストップワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="69145-121">If you selected **Add stopword** or **Delete stopword**, enter the stopword in the **Stopword** field.</span></span> <span data-ttu-id="69145-122">新しいストップワードは一意である、つまり、選択した言語のこのストップリストにまだ含まれていない必要があります。</span><span class="sxs-lookup"><span data-stu-id="69145-122">A new stopword must be unique; that is, not yet in this stoplist for the language that you select.</span></span>  
  
 <span data-ttu-id="69145-123">**[フルテキスト言語]**</span><span class="sxs-lookup"><span data-stu-id="69145-123">**Full-text language**</span></span>  
 <span data-ttu-id="69145-124">**[ストップワードの追加]**、 **[ストップワードの削除]**、または **[すべてのストップワードの削除]** を選択した場合は、このリスト ボックスから、操作対象のストップワードの言語を選択します。</span><span class="sxs-lookup"><span data-stu-id="69145-124">If you selected **Add stopword**, **Delete stopword**, or **Delete all stopwords**, select the language of the stopword or stopwords from the list box.</span></span> <span data-ttu-id="69145-125">このリスト ボックスには、サーバー インスタンスでサポートされているすべてのフルテキスト言語が表示されます。</span><span class="sxs-lookup"><span data-stu-id="69145-125">This lists all the full-text languages that are supported by the server instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69145-126">参照</span><span class="sxs-lookup"><span data-stu-id="69145-126">See Also</span></span>  
 <span data-ttu-id="69145-127">[fulltext_stopwords &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="69145-127">[sys.fulltext_stopwords &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql) </span></span>  
 <span data-ttu-id="69145-128">[fulltext_stoplists &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="69145-128">[sys.fulltext_stoplists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql) </span></span>  
 <span data-ttu-id="69145-129">[フルテキスト検索のためのストップワードとストップリストの構成と管理](../relational-databases/search/full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="69145-129">[Configure and Manage Stopwords and Stoplists for Full-Text Search](../relational-databases/search/full-text-search.md) </span></span>  
 <span data-ttu-id="69145-130">[Transact-sql&#41;&#40;フルテキストストップリストの変更](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="69145-130">[ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql) </span></span>  
 <span data-ttu-id="69145-131">[Transact-sql&#41;&#40;のフルテキストストップリストの作成](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="69145-131">[CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span></span>  
 [<span data-ttu-id="69145-132">DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="69145-132">DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)  
  
  
