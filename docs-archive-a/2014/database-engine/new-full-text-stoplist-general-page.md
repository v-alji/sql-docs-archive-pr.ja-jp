---
title: 新しいフルテキストストップリスト ([全般] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftstoplist.general.f1
ms.assetid: 97f8e82d-82ab-4525-91c9-1ee3ae217309
author: rothja
ms.author: jroth
ms.openlocfilehash: a6272fb570b85989f38c8187e29712966862710d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644630"
---
# <a name="new-full-text-stoplist-general-page"></a><span data-ttu-id="cb3b0-102">[新しいフルテキスト ストップリスト] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="cb3b0-102">New Full-Text Stoplist (General Page)</span></span>
  <span data-ttu-id="cb3b0-103">このダイアログ ボックスを使用すると、フルテキスト ストップリストを作成できます。</span><span class="sxs-lookup"><span data-stu-id="cb3b0-103">Use this dialog box to create a full-text stoplist.</span></span> <span data-ttu-id="cb3b0-104">*ストップリスト* とは、一般的に使用される単語のセットのことです。これらの単語は *ストップワード*と呼ばれ、ストップリストを使用するテーブルのフルテキスト インデックスから省略されます。</span><span class="sxs-lookup"><span data-stu-id="cb3b0-104">A *stoplist* is a set of commonly used words, called *stopwords*, that are omitted from full-text indexing for tables that use the stoplist.</span></span> <span data-ttu-id="cb3b0-105">詳細については、「 [フルテキスト検索に使用するストップワードとストップリストの構成と管理](../relational-databases/search/full-text-search.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb3b0-105">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](../relational-databases/search/full-text-search.md).</span></span>  
  
 <span data-ttu-id="cb3b0-106">**SQL Server Management Studio を使用してストップリストを作成するには**</span><span class="sxs-lookup"><span data-stu-id="cb3b0-106">**To use SQL Server Management Studio to create a stoplist**</span></span>  
  
-   [<span data-ttu-id="cb3b0-107">フルテキスト検索に使用するストップワードとストップリストの構成と管理</span><span class="sxs-lookup"><span data-stu-id="cb3b0-107">Configure and Manage Stopwords and Stoplists for Full-Text Search</span></span>](../relational-databases/search/full-text-search.md)  
  
## <a name="options"></a><span data-ttu-id="cb3b0-108">Options</span><span class="sxs-lookup"><span data-stu-id="cb3b0-108">Options</span></span>  
 <span data-ttu-id="cb3b0-109">**[フルテキスト ストップリスト名]**</span><span class="sxs-lookup"><span data-stu-id="cb3b0-109">**Full-text stoplist name**</span></span>  
 <span data-ttu-id="cb3b0-110">フルテキスト ストップリストの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="cb3b0-110">Enter the name of the full-text stoplist.</span></span>  
  
 <span data-ttu-id="cb3b0-111">**所有者**</span><span class="sxs-lookup"><span data-stu-id="cb3b0-111">**Owner**</span></span>  
 <span data-ttu-id="cb3b0-112">フルテキスト ストップリストの所有者を指定します。</span><span class="sxs-lookup"><span data-stu-id="cb3b0-112">Specify the owner of the full-text stoplist.</span></span> <span data-ttu-id="cb3b0-113">自分自身 (現在のユーザー) に所有権を割り当てる場合は、このフィールドを空のままにします。</span><span class="sxs-lookup"><span data-stu-id="cb3b0-113">If you want ownership to be assigned to yourself, that is, to the current user, leave this field empty.</span></span>  
  
 <span data-ttu-id="cb3b0-114">別のユーザーを指定するには、参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb3b0-114">To specify a different user, click the browse button.</span></span>  
  
### <a name="create-stoplist-options"></a><span data-ttu-id="cb3b0-115">ストップリスト作成オプション</span><span class="sxs-lookup"><span data-stu-id="cb3b0-115">Create stoplist options</span></span>  
 <span data-ttu-id="cb3b0-116">以下のいずれかの作成オプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb3b0-116">Click one of the following create options:</span></span>  
  
 <span data-ttu-id="cb3b0-117">**[空のストップリストを作成する]**</span><span class="sxs-lookup"><span data-stu-id="cb3b0-117">**Create an empty stoplist**</span></span>  
 <span data-ttu-id="cb3b0-118">新しいストップリストにストップワードは含まれません。</span><span class="sxs-lookup"><span data-stu-id="cb3b0-118">The new stoplist will not contain any stopwords.</span></span>  
  
 <span data-ttu-id="cb3b0-119">**[システム ストップリストから作成する]**</span><span class="sxs-lookup"><span data-stu-id="cb3b0-119">**Create from the system stoplist**</span></span>  
 <span data-ttu-id="cb3b0-120">[リソース データベース](../relational-databases/databases/resource-database.md)に既定で存在するストップリストから新しいストップリストを作成します。</span><span class="sxs-lookup"><span data-stu-id="cb3b0-120">The new stoplist is created from the stoplist that exists by default in the [Resource database](../relational-databases/databases/resource-database.md).</span></span>  
  
 <span data-ttu-id="cb3b0-121">**[既存のフルテキスト ストップリストから作成する]**</span><span class="sxs-lookup"><span data-stu-id="cb3b0-121">**Create from an existing full-text stoplist**</span></span>  
 <span data-ttu-id="cb3b0-122">既存のストップリストをコピーして新しいストップリストを作成します。</span><span class="sxs-lookup"><span data-stu-id="cb3b0-122">The new stoplist is created by copying an existing stoplist.</span></span>  
  
 <span data-ttu-id="cb3b0-123">**ソースデータベース**</span><span class="sxs-lookup"><span data-stu-id="cb3b0-123">**Source database**</span></span>  
 <span data-ttu-id="cb3b0-124">既存のストップリストが属しているデータベースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="cb3b0-124">Specifies the name of the database to which the existing stoplist belongs.</span></span> <span data-ttu-id="cb3b0-125">既定では、現在のデータベースが選択されています。</span><span class="sxs-lookup"><span data-stu-id="cb3b0-125">The current database is selected by default.</span></span> <span data-ttu-id="cb3b0-126">必要に応じて、リスト ボックスから別のデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="cb3b0-126">Optionally, select a different database from the list box.</span></span>  
  
 <span data-ttu-id="cb3b0-127">**[基になるストップリスト]**</span><span class="sxs-lookup"><span data-stu-id="cb3b0-127">**Source stoplist**</span></span>  
 <span data-ttu-id="cb3b0-128">既存のストップリストの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="cb3b0-128">Specifies the name of an existing stoplist.</span></span> <span data-ttu-id="cb3b0-129">利用可能なストップリストの一覧から、基になるストップリストを選択します。</span><span class="sxs-lookup"><span data-stu-id="cb3b0-129">From the list of available stoplists, select the one to use as the source.</span></span> <span data-ttu-id="cb3b0-130">利用可能なストップリストは、オブジェクト エクスプローラーに表示される順序で一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb3b0-130">The available stoplists are listed in the order in which they appear in Object Explorer.</span></span>  
  
 <span data-ttu-id="cb3b0-131">ソース ストップリストのストップワードに指定された言語が現在のデータベースに登録されていない場合、CREATE FULLTEXT STOPLIST は成功しますが、警告が表示され、対応するストップワードは追加されません。</span><span class="sxs-lookup"><span data-stu-id="cb3b0-131">If any languages specified in the stop words of the source stoplist are not registered in the current database, CREATE FULLTEXT STOPLIST succeeds, but warning(s) are returned and the corresponding stop words are not added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb3b0-132">参照</span><span class="sxs-lookup"><span data-stu-id="cb3b0-132">See Also</span></span>  
 <span data-ttu-id="cb3b0-133">[Transact-sql&#41;&#40;フルテキストストップリストの変更](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cb3b0-133">[ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql) </span></span>  
 <span data-ttu-id="cb3b0-134">[Transact-sql&#41;&#40;のフルテキストストップリストの作成](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cb3b0-134">[CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span></span>  
 <span data-ttu-id="cb3b0-135">[Transact-sql&#41;&#40;のフルテキストストップリストの削除](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cb3b0-135">[DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql) </span></span>  
 <span data-ttu-id="cb3b0-136">[フルテキスト検索のためのストップワードとストップリストの構成と管理](../relational-databases/search/full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="cb3b0-136">[Configure and Manage Stopwords and Stoplists for Full-Text Search](../relational-databases/search/full-text-search.md) </span></span>  
 [<span data-ttu-id="cb3b0-137">sys.fulltext_stoplists &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cb3b0-137">sys.fulltext_stoplists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)  
  
  
