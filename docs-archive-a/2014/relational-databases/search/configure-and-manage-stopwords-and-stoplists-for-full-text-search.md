---
title: フルテキスト検索に使用するストップワードとストップリストの構成と管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- stoplists [full-text search]
- full-text search [SQL Server], stoplists
- full-text search [SQL Server], noise words
- noise words [full-text search]
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 43b5ce7b-9f09-4443-8a5b-c3da6eb28bcc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 103b5024368c5ca239856580e9b45473aabf6a92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741749"
---
# <a name="configure-and-manage-stopwords-and-stoplists-for-full-text-search"></a><span data-ttu-id="ab3fa-102">フルテキスト検索に使用するストップワードとストップリストの構成と管理</span><span class="sxs-lookup"><span data-stu-id="ab3fa-102">Configure and Manage Stopwords and Stoplists for Full-Text Search</span></span>
  <span data-ttu-id="ab3fa-103">フルテキスト インデックスが肥大化するのを防ぐため、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、頻繁に出現する、検索に役立たない文字列を破棄するメカニズムがあります。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-103">To prevent a full-text index from becoming bloated, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has a mechanism that discards commonly occurring strings that do not help the search.</span></span> <span data-ttu-id="ab3fa-104">破棄されるこのような文字列を *ストップワード*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-104">These discarded strings are called *stopwords*.</span></span> <span data-ttu-id="ab3fa-105">インデックスの作成中、Full-Text Engine により、フルテキスト インデックスからストップワードが除外されます。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-105">During index creation, the Full-Text Engine omits stopwords from the full-text index.</span></span> <span data-ttu-id="ab3fa-106">つまり、フルテキスト クエリでは、ストップワードが検索されません。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-106">This means that full-text queries will not search on stopwords.</span></span>  
  
##  <a name="understanding-stopwords-and-stoplists"></a><a name="understand"></a><span data-ttu-id="ab3fa-107">ストップワードとストップリストについて</span><span class="sxs-lookup"><span data-stu-id="ab3fa-107">Understanding Stopwords and Stoplists</span></span>  
 <span data-ttu-id="ab3fa-108">ストップワードは、特定の言語で意味を持つ単語の場合や言語的な意味のない *トークン* の場合があります。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-108">A stopword can be a word with meaning in a specific language, or it can be a *token* that does not have linguistic meaning.</span></span> <span data-ttu-id="ab3fa-109">たとえば、英語では、"a"、"and"、"is"、"the" などの単語は、検索に役立たないことが知られているため、フルテキスト インデックスから除外されます。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-109">For example, in the English language, words such as "a," "and," "is," and "the" are left out of the full-text index since they are known to be useless to a search.</span></span>  
  
 <span data-ttu-id="ab3fa-110">含まれるストップワードは無視されますが、フルテキスト インデックスではその位置が考慮されます。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-110">Although it ignores the inclusion of stopwords, the full-text index does take into account their position.</span></span> <span data-ttu-id="ab3fa-111">たとえば、"Instructions are applicable to these Adventure Works Cycles models" という句があるとします。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-111">For example, consider the phrase, "Instructions are applicable to these Adventure Works Cycles models".</span></span> <span data-ttu-id="ab3fa-112">以下のテーブルは、句の中の語の位置を表しています。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-112">The following table depicts the position of the words in the phrase:</span></span>  
  
|<span data-ttu-id="ab3fa-113">Word</span><span class="sxs-lookup"><span data-stu-id="ab3fa-113">Word</span></span>|<span data-ttu-id="ab3fa-114">[位置]</span><span class="sxs-lookup"><span data-stu-id="ab3fa-114">Position</span></span>|  
|----------|--------------|  
|<span data-ttu-id="ab3fa-115">Instructions</span><span class="sxs-lookup"><span data-stu-id="ab3fa-115">Instructions</span></span>|<span data-ttu-id="ab3fa-116">1</span><span class="sxs-lookup"><span data-stu-id="ab3fa-116">1</span></span>|  
|<span data-ttu-id="ab3fa-117">are</span><span class="sxs-lookup"><span data-stu-id="ab3fa-117">are</span></span>|<span data-ttu-id="ab3fa-118">2</span><span class="sxs-lookup"><span data-stu-id="ab3fa-118">2</span></span>|  
|<span data-ttu-id="ab3fa-119">applicable</span><span class="sxs-lookup"><span data-stu-id="ab3fa-119">applicable</span></span>|<span data-ttu-id="ab3fa-120">3</span><span class="sxs-lookup"><span data-stu-id="ab3fa-120">3</span></span>|  
|<span data-ttu-id="ab3fa-121">to</span><span class="sxs-lookup"><span data-stu-id="ab3fa-121">to</span></span>|<span data-ttu-id="ab3fa-122">4</span><span class="sxs-lookup"><span data-stu-id="ab3fa-122">4</span></span>|  
|<span data-ttu-id="ab3fa-123">these</span><span class="sxs-lookup"><span data-stu-id="ab3fa-123">these</span></span>|<span data-ttu-id="ab3fa-124">5</span><span class="sxs-lookup"><span data-stu-id="ab3fa-124">5</span></span>|  
|<span data-ttu-id="ab3fa-125">Adventure</span><span class="sxs-lookup"><span data-stu-id="ab3fa-125">Adventure</span></span>|<span data-ttu-id="ab3fa-126">6</span><span class="sxs-lookup"><span data-stu-id="ab3fa-126">6</span></span>|  
|<span data-ttu-id="ab3fa-127">Works</span><span class="sxs-lookup"><span data-stu-id="ab3fa-127">Works</span></span>|<span data-ttu-id="ab3fa-128">7</span><span class="sxs-lookup"><span data-stu-id="ab3fa-128">7</span></span>|  
|<span data-ttu-id="ab3fa-129">Cycles</span><span class="sxs-lookup"><span data-stu-id="ab3fa-129">Cycles</span></span>|<span data-ttu-id="ab3fa-130">8</span><span class="sxs-lookup"><span data-stu-id="ab3fa-130">8</span></span>|  
|<span data-ttu-id="ab3fa-131">モデル</span><span class="sxs-lookup"><span data-stu-id="ab3fa-131">models</span></span>|<span data-ttu-id="ab3fa-132">9</span><span class="sxs-lookup"><span data-stu-id="ab3fa-132">9</span></span>|  
  
 <span data-ttu-id="ab3fa-133">位置 2、4、および 5 にあるストップワード "are"、"to"、"these" は、フルテキスト インデックスから除外されます。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-133">The stopwords "are", "to", and "these" that are in positions 2, 4, and 5 are left out of the full-text index.</span></span> <span data-ttu-id="ab3fa-134">ただし、その位置情報は保持されるため、語句内の他の語の位置は変わりません。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-134">However, their positional information is maintained, thereby leaving the position of the other words in the phrase unaffected.</span></span>  
  
 <span data-ttu-id="ab3fa-135">ストップワードは、ストップリストと呼ばれるオブジェクトを使用してデータベースで管理されます。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-135">Stopwords are managed in databases using objects called stoplists.</span></span> <span data-ttu-id="ab3fa-136">*ストップリスト* は、フルテキスト インデックスに関連付けられている場合、そのインデックスのフルテキスト クエリに適用されるストップワードの一覧です。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-136">A *stoplist* is a list of stopwords that, when associated with a full-text index, is applied to full-text queries on that index.</span></span>  
  
  
##  <a name="creating-a-stoplist"></a><a name="creating"></a><span data-ttu-id="ab3fa-137">ストップリストの作成</span><span class="sxs-lookup"><span data-stu-id="ab3fa-137">Creating a Stoplist</span></span>  
 <span data-ttu-id="ab3fa-138">ストップリストは、次のいずれかの方法で作成できます。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-138">You can create a stoplist in any of the following ways:</span></span>  
  
-   <span data-ttu-id="ab3fa-139">システムに備わっているストップリストをデータベースで使用します。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-139">Using the system-supplied stoplist in the database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ab3fa-140">には、最も頻繁に使用するストップワードを含むシステム ストップリストが、サポート対象の言語ごとに用意されています。つまり、既定で、特定のワード ブレーカーに関連付けられている言語ごとにストップリストが用意されています。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-140">ships with a system stoplist that contains the most commonly used stopwords for each supported language, that is for every language that is associated with given word breakers by default.</span></span> <span data-ttu-id="ab3fa-141">システム ストップリストには、サポートされているすべての言語に対して一般的なストップワードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-141">The system stoplist contains common stopwords for all supported languages.</span></span>  <span data-ttu-id="ab3fa-142">システム ストップリストをコピーし、ストップワードを追加したり削除したりすることにより、そのコピーをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-142">You can copy the system stoplist, and customize your copy by adding and removing stopwords.</span></span>  
  
     <span data-ttu-id="ab3fa-143">システム ストップリストは [Resource](../databases/resource-database.md) データベースにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-143">The system stoplist is installed in the [Resource](../databases/resource-database.md) database.</span></span>  
  
-   <span data-ttu-id="ab3fa-144">指定した任意の言語について独自のストップリストを作成した後、ストップワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-144">Creating your own stoplist, and then adding stopwords to it for any language that you specify.</span></span> <span data-ttu-id="ab3fa-145">必要に応じて、ストップリストからストップワードを削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-145">You can also drop stopwords from your stoplist when necessary.</span></span>  
  
-   <span data-ttu-id="ab3fa-146">現在のサーバー インスタンスで他のデータベースの既存のカスタム ストップリストを使用して、必要に応じて、ストップワードを追加および削除します。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-146">Using an existing custom stoplist from any other database in the current server instance and then adding and dropping stopwords as necessary.</span></span>  
  
 <span data-ttu-id="ab3fa-147">**ストップリストを作成するには**</span><span class="sxs-lookup"><span data-stu-id="ab3fa-147">**To create a stoplist**</span></span>  
  
-   [<span data-ttu-id="ab3fa-148">CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ab3fa-148">CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)  
  
#### <a name="to-create-a-full-text-stoplist-in-management-studio"></a><span data-ttu-id="ab3fa-149">Management Studio でフルテキスト ストップリストを作成するには</span><span class="sxs-lookup"><span data-stu-id="ab3fa-149">To create a full-text stoplist in Management Studio</span></span>  
  
1.  <span data-ttu-id="ab3fa-150">オブジェクト エクスプローラーで、サーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-150">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="ab3fa-151">**[データベース]** を展開し、フルテキスト ストップリストを作成する対象のデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-151">Expand **Databases**, and then expand the database in which you want to create the full-text stoplist.</span></span>  
  
3.  <span data-ttu-id="ab3fa-152">**[ストレージ]** を展開し、 **[フルテキスト ストップリスト]** を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-152">Expand **Storage**, and then right-click **Full-Text Stoplists**.</span></span>  
  
4.  <span data-ttu-id="ab3fa-153">**[新しいフルテキスト ストップリスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-153">Select **New Full-Text Stoplist**.</span></span>  
  
5.  <span data-ttu-id="ab3fa-154">ストップリスト名を指定します。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-154">Specify the stoplist name.</span></span>  
  
6.  <span data-ttu-id="ab3fa-155">必要に応じて、他のユーザーをストップリストの所有者として指定します。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-155">Optionally, specify someone else as the stoplist owner.</span></span>  
  
7.  <span data-ttu-id="ab3fa-156">次に示すストップリスト作成オプションのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-156">Select one of the following create stoplist options:</span></span>  
  
    -   <span data-ttu-id="ab3fa-157">**[空のストップリストを作成する]**</span><span class="sxs-lookup"><span data-stu-id="ab3fa-157">**Create an empty stoplist**</span></span>  
  
    -   <span data-ttu-id="ab3fa-158">**[システム ストップリストから作成する]**</span><span class="sxs-lookup"><span data-stu-id="ab3fa-158">**Create from the system stoplist**</span></span>  
  
    -   <span data-ttu-id="ab3fa-159">**[既存のフルテキスト ストップリストから作成する]**</span><span class="sxs-lookup"><span data-stu-id="ab3fa-159">**Create from an existing full-text stoplist**</span></span>  
  
     <span data-ttu-id="ab3fa-160">詳細については、「[新しいフルテキスト ストップリスト &#40;[全般] ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-160">For more information, see [New Full-Text Stoplist &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="ab3fa-161">**ストップリストを削除するには**</span><span class="sxs-lookup"><span data-stu-id="ab3fa-161">**To drop a stoplist**</span></span>  
  
-   [<span data-ttu-id="ab3fa-162">DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ab3fa-162">DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)  
  
  
##  <a name="using-a-stoplist-in-full-text-queries"></a><a name="queries"></a><span data-ttu-id="ab3fa-163">フルテキストクエリでのストップリストの使用</span><span class="sxs-lookup"><span data-stu-id="ab3fa-163">Using a Stoplist in Full-Text Queries</span></span>  
 <span data-ttu-id="ab3fa-164">ストップリストをクエリで使用するには、ストップリストをフルテキスト インデックスに関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-164">To make use of a stoplist in queries, you must associate it with a full-text index.</span></span> <span data-ttu-id="ab3fa-165">インデックスの作成時にストップリストをフルテキスト インデックスにアタッチしたり、後でインデックスを変更してストップリストを追加したりできます。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-165">You can attach a stoplist to a full-text index when you create the index, or you can alter the index later to add a stoplist.</span></span>  
  
 <span data-ttu-id="ab3fa-166">**フルテキスト インデックスを作成してストップリストを関連付けるには**</span><span class="sxs-lookup"><span data-stu-id="ab3fa-166">**To create a full-text index and associate a stoplist with it**</span></span>  
  
-   [<span data-ttu-id="ab3fa-167">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ab3fa-167">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-index-transact-sql)  
  
 <span data-ttu-id="ab3fa-168">**既存のフルテキスト インデックスに対してストップリストの関連付けまたは関連付け解除を行うには**</span><span class="sxs-lookup"><span data-stu-id="ab3fa-168">**To associate or disassociate a stoplist with an existing full-text index**</span></span>  
  
-   [<span data-ttu-id="ab3fa-169">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ab3fa-169">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
 <span data-ttu-id="ab3fa-170">**ストップワードが原因でフルテキスト クエリのブール演算が失敗する場合に、エラー メッセージを非表示にするには**</span><span class="sxs-lookup"><span data-stu-id="ab3fa-170">**To suppress an error message if stopwords cause a Boolean operation on a full-text query to fail**</span></span>  
  
-   [<span data-ttu-id="ab3fa-171">transform noise words サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="ab3fa-171">transform noise words Server Configuration Option</span></span>](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md)  
  
  
##  <a name="viewing-stoplists-and-stoplist-metadata"></a><a name="viewing"></a><span data-ttu-id="ab3fa-172">ストップリストとストップリストメタデータの表示</span><span class="sxs-lookup"><span data-stu-id="ab3fa-172">Viewing Stoplists and Stoplist Metadata</span></span>  
 <span data-ttu-id="ab3fa-173">**ストップリストのすべてのストップワードを表示するには**</span><span class="sxs-lookup"><span data-stu-id="ab3fa-173">**To view all the stopwords of a stoplist**</span></span>  
  
-   [<span data-ttu-id="ab3fa-174">sys.fulltext_stopwords &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ab3fa-174">sys.fulltext_stopwords &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql)  
  
 <span data-ttu-id="ab3fa-175">**現在のデータベース内にあるすべてのストップリストに関する情報を取得するには**</span><span class="sxs-lookup"><span data-stu-id="ab3fa-175">**To get information about all the stoplists in the current database**</span></span>  
  
-   [<span data-ttu-id="ab3fa-176">sys.fulltext_stoplists &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ab3fa-176">sys.fulltext_stoplists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)  
  
-   [<span data-ttu-id="ab3fa-177">sys.fulltext_stopwords &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ab3fa-177">sys.fulltext_stopwords &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql)  
  
 <span data-ttu-id="ab3fa-178">**ワード ブレーカー、類語辞典、およびストップリストの組み合わせによるトークン化の結果を表示するには**</span><span class="sxs-lookup"><span data-stu-id="ab3fa-178">**To view the tokenization result of a word breaker, thesaurus, and stoplist combination**</span></span>  
  
-   [<span data-ttu-id="ab3fa-179">dm_fts_parser &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="ab3fa-179">sys.dm_fts_parser &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)  
  
  
##  <a name="changing-the-stopwords-in-a-stoplist"></a><a name="change"></a><span data-ttu-id="ab3fa-180">ストップリスト内のストップワードの変更</span><span class="sxs-lookup"><span data-stu-id="ab3fa-180">Changing the Stopwords in a Stoplist</span></span>  
 <span data-ttu-id="ab3fa-181">**ストップリストからストップワードを追加または削除するには**</span><span class="sxs-lookup"><span data-stu-id="ab3fa-181">**To add or drop stopwords from a stoplist**</span></span>  
  
-   [<span data-ttu-id="ab3fa-182">ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ab3fa-182">ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)  
  
#### <a name="to-change-the-stopwords-in-a-stoplist-in-management-studio"></a><span data-ttu-id="ab3fa-183">Management Studio でストップリスト内のストップワードを変更するには</span><span class="sxs-lookup"><span data-stu-id="ab3fa-183">To change the stopwords in a stoplist in Management Studio</span></span>  
  
1.  <span data-ttu-id="ab3fa-184">オブジェクト エクスプローラーで、サーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-184">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="ab3fa-185">**[データベース]** を展開し、データベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-185">Expand **Databases**, and then expand the database.</span></span>  
  
3.  <span data-ttu-id="ab3fa-186">**[ストレージ]** を展開し、 **[フルテキスト ストップリスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-186">Expand **Storage**, and then select **Full Text Stoplists**.</span></span>  
  
4.  <span data-ttu-id="ab3fa-187">プロパティを変更するストップリストを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-187">Right-click the stoplist whose properties you want to change, and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="ab3fa-188">[[フルテキスト ストップリストのプロパティ]](../../database-engine/full-text-stoplist-properties.md) ダイアログ ボックスで:</span><span class="sxs-lookup"><span data-stu-id="ab3fa-188">In the [Full-Text Stoplist Properties](../../database-engine/full-text-stoplist-properties.md) dialog box:</span></span>  
  
    1.  <span data-ttu-id="ab3fa-189">**[アクション]** ボックスの一覧で、 **[ストップワードの追加]**、 **[ストップワードの削除]**、 **[すべてのストップワードの削除]**、 **[ストップリストのクリア]** のいずれかのアクションを選択します。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-189">In the **Action** list box, select one of the following actions: **Add stopword**, **Delete stopword**, **Delete all stopwords**, or **Clear stoplist**.</span></span>  
  
    2.  <span data-ttu-id="ab3fa-190">選択したアクションに対して **[ストップワード]** ボックスが有効になっている場合は、単一のストップワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-190">If the **Stopword** text box is enabled for the selected action, enter a single stopword.</span></span> <span data-ttu-id="ab3fa-191">このストップワードは一意である必要があります。つまり、選択した言語で、このストップリストにまだ含まれていないものである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-191">This stopword must be unique; that is, not yet in this stoplist for the language that you select.</span></span>  
  
    3.  <span data-ttu-id="ab3fa-192">選択したアクションに対して **[フルテキスト言語]** ボックスの一覧が有効になっている場合は、言語を選択します。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-192">If the **Full-text language** list box is enabled for the selected action, select a language.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
##  <a name="upgrading-noise-words-from-sql-server-2005"></a><a name="upgrade"></a><span data-ttu-id="ab3fa-193">SQL Server 2005 からのノイズワードのアップグレード</span><span class="sxs-lookup"><span data-stu-id="ab3fa-193">Upgrading Noise Words from SQL Server 2005</span></span>  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] <span data-ttu-id="ab3fa-194">のノイズ ワードは、ストップワードになりました。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-194">noise words have been replaced by stopwords.</span></span> <span data-ttu-id="ab3fa-195">データベースが [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]からアップグレードされると、ノイズ ワード ファイルは使用されなくなります。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-195">When a database is upgraded from [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], the noise-word files are no longer used.</span></span> <span data-ttu-id="ab3fa-196">ただし、ノイズ ワード ファイルは FTDATA\ FTNoiseThesaurusBak フォルダーに保存され、後で更新する際、または対応するストップリストを作成する際に使用できます。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-196">However, the noise-word files are stored in the FTDATA\ FTNoiseThesaurusBak folder, and you can use them later when updating or building the corresponding stoplists.</span></span> <span data-ttu-id="ab3fa-197">ノイズ ワード ファイルをストップリストにアップグレードする方法の詳細については、「 [フルテキスト検索のアップグレード](upgrade-full-text-search.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab3fa-197">For information about upgrading noise-word files to stoplists, see [Upgrade Full-Text Search](upgrade-full-text-search.md).</span></span>  
  
  
  
