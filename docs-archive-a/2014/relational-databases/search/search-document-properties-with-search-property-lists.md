---
title: 検索プロパティ リストを使用したドキュメント プロパティの検索 | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- full-text search [SQL Server], properties
- search property lists [SQL Server]
- property searching [SQL Server], about
- full-text indexes [SQL Server], search property lists
- search property lists [SQL Server], about
- property searching [SQL Server]
ms.assetid: ffae5914-b1b2-4267-b927-37e8382e0a9e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 16ab59a9fcdab29c927cb624dabcdfa71eaae1e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719827"
---
# <a name="search-document-properties-with-search-property-lists"></a><span data-ttu-id="a1e5d-102">検索プロパティ リストを使用したドキュメント プロパティの検索</span><span class="sxs-lookup"><span data-stu-id="a1e5d-102">Search Document Properties with Search Property Lists</span></span>
  <span data-ttu-id="a1e5d-103">以前のバージョンでは、ドキュメント プロパティの内容はドキュメントの本文の内容と区別できませんでした。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-103">The content of document properties was previously indistinguishable from the content of the document body.</span></span> <span data-ttu-id="a1e5d-104">この制限により、フルテキスト クエリは、ドキュメント全体に対する汎用検索に制限されていました。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-104">This limitation restricted full-text queries to generic searches on whole documents.</span></span> <span data-ttu-id="a1e5d-105">しかし、現在のバージョンでは、`varbinary`、`varbinary(max)` (`FILESTREAM` を含む)、または `image` バイナリ データ列がサポートされているドキュメントの種類については、フルテキスト インデックスを構成することで、Author や Title などの特定のプロパティに対するプロパティ スコープの検索をサポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-105">Now, however, you can configure a full-text index to support property-scoped searching on particular properties, such as Author and Title, for supported document types in a `varbinary`, `varbinary(max)` (including `FILESTREAM`), or `image` binary data column.</span></span> <span data-ttu-id="a1e5d-106">この形式の検索を、 *プロパティ検索*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-106">This form of searching is known as *property searching*.</span></span>  
  
 <span data-ttu-id="a1e5d-107">特定の種類のドキュメントでプロパティ検索が可能かどうかは、対応する [フィルター](configure-and-manage-filters-for-search.md) (IFilter) によって異なります。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-107">The associated [filter](configure-and-manage-filters-for-search.md) (IFilter) determines whether property searching is possible on a specific type of document.</span></span> <span data-ttu-id="a1e5d-108">ドキュメントの種類によっては、ドキュメント本文の内容に加えて、そのドキュメントの種類に対して定義されている検索プロパティの一部またはすべてが、対応する IFilter によって抽出されます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-108">For some document types, the associated IFilter extracts some or all of the properties defined for that type of document, as well as the content of the document body.</span></span> <span data-ttu-id="a1e5d-109">フルテキスト インデックスの作成時に IFilter によって抽出されたプロパティに対してのみプロパティ検索をサポートするように、フルテキスト インデックスを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-109">You can configure a full-text index to support property searching only on properties that are extracted by an IFilter during full-text indexing.</span></span> <span data-ttu-id="a1e5d-110">さまざまなドキュメント プロパティを抽出する IFilter の一例として、Microsoft Office のドキュメントの種類 (.docx、.xlsx、.pptx など) に対応した IFilter があります。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-110">Among IFilters that extract a number of document properties are the IFilters for Microsoft Office document types (such as .docx, .xlsx, and .pptx).</span></span> <span data-ttu-id="a1e5d-111">一方、XML IFilter では、プロパティは生成されません。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-111">On the other hand, the XML IFilter does not emit properties.</span></span>  
  
##  <a name="how-full-text-search-works-with-search-properties"></a><a name="How_FTS_Works_with_search_properties"></a> <span data-ttu-id="a1e5d-112">検索プロパティのフルテキスト検索</span><span class="sxs-lookup"><span data-stu-id="a1e5d-112">How Full-Text Search Works with Search Properties</span></span>  
  
### <a name="internal-property-ids"></a><span data-ttu-id="a1e5d-113">内部プロパティ ID</span><span class="sxs-lookup"><span data-stu-id="a1e5d-113">Internal Property IDs</span></span>  
 <span data-ttu-id="a1e5d-114">Full-Text Engine は、登録されている各プロパティに対して内部プロパティ ID を適宜割り当てます。この内部プロパティ ID は、特定の検索リスト内のプロパティを一意に識別するためのもので、検索プロパティ リストで固有の ID になります。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-114">The Full-Text Engine arbitrarily assigns each registered property an internal property ID, which uniquely identifies the property in that particular search list and which is specific to that search property list.</span></span> <span data-ttu-id="a1e5d-115">また、1 つのプロパティを複数の検索プロパティ リストに追加した場合、その内部 ID がリスト間で異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-115">Therefore, if a property is added to multiple search property lists, its internal property ID is likely to differ between different lists.</span></span>  
  
 <span data-ttu-id="a1e5d-116">プロパティを検索リストに追加したときに、Full-Text Engine によって *内部プロパティ ID* がプロパティに適宜割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-116">When a property is registered for a search list, the Full-Text Engine arbitrarily assigns an *internal property ID* to the property.</span></span> <span data-ttu-id="a1e5d-117">この内部プロパティ ID は、該当する検索プロパティ リスト内のプロパティを一意に識別する整数です。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-117">The internal property ID is an integer that uniquely identifies the property in that search property list.</span></span>  
  
 <span data-ttu-id="a1e5d-118">次の図は、Title と Keywords の 2 つのプロパティを指定する検索プロパティ リストの論理的なビューを示しています。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-118">The following illustration shows a logical view of a search property list that specifies two properties, Title and Keywords.</span></span> <span data-ttu-id="a1e5d-119">Keywords のプロパティ リスト名は "Tags" です。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-119">The property-list name for Keywords is "Tags".</span></span> <span data-ttu-id="a1e5d-120">これらのプロパティは、F29F85E0-4FF9-1068-AB91-08002B27B3D9 という GUID を持つ同じプロパティ セットに属します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-120">These properties belong to the same property set, whose GUID is F29F85E0-4FF9-1068-AB91-08002B27B3D9.</span></span> <span data-ttu-id="a1e5d-121">Title のプロパティ整数識別子は 2、Tags (Keywords) のプロパティ整数識別子は 5 です。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-121">The property integer identifiers are 2 for Title and 5 for Tags (Keywords).</span></span> <span data-ttu-id="a1e5d-122">Full-Text Engine は、各プロパティを、検索プロパティ リストで一意となる内部プロパティ ID に適宜関連付けます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-122">The Full-Text Engine arbitrarily maps each property to an internal property ID that is unique to the search property list.</span></span> <span data-ttu-id="a1e5d-123">Title プロパティの内部プロパティ ID は 1、Tags プロパティの内部プロパティ ID は 2 になります。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-123">The internal property ID for the Title property is 1, and the internal property ID for the Tags property is 2.</span></span>  
  
 <span data-ttu-id="a1e5d-124">![検索プロパティ リストを内部テーブルにマッピングする](../../database-engine/media/ifts-spl-w-title-and-keywords.gif "検索プロパティ リストを内部テーブルにマッピングする")</span><span class="sxs-lookup"><span data-stu-id="a1e5d-124">![Mapping of search property list to internal table](../../database-engine/media/ifts-spl-w-title-and-keywords.gif "Mapping of search property list to internal table")</span></span>  
  
 <span data-ttu-id="a1e5d-125">内部プロパティ ID は、プロパティのプロパティ整数識別子とは異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-125">The internal property ID is likely to be different from the property integer identifier of the property.</span></span> <span data-ttu-id="a1e5d-126">特定のプロパティを複数の検索プロパティ リストに登録した場合、検索プロパティ リストごとに異なる内部プロパティ ID が割り当てられる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-126">If a given property is registered for multiple search property lists, a different internal property ID might be assigned for each search property list.</span></span> <span data-ttu-id="a1e5d-127">たとえば、ある検索プロパティ リストでは内部プロパティ ID が 4 である一方で、別の検索プロパティ リストでは内部プロパティ ID が 1 であったり 3 であったりする場合があります。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-127">For example, the internal property ID might be 4 in one search property list, 1 in another, 3 in another, and so on.</span></span> <span data-ttu-id="a1e5d-128">これに対し、プロパティ整数識別子はプロパティに固有な識別子であるため、プロパティがどこで使用されるかに関係なく同じ値になります。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-128">In contrast, the property integer identifier is intrinsic to the property, and it remains the same wherever the property is used.</span></span>  
  
  
  
### <a name="indexing-of-registered-properties"></a><span data-ttu-id="a1e5d-129">登録済みのプロパティのインデックスの作成</span><span class="sxs-lookup"><span data-stu-id="a1e5d-129">Indexing of Registered Properties</span></span>  
 <span data-ttu-id="a1e5d-130">フルテキスト インデックスが検索プロパティ リストに関連付けらた後で、プロパティに固有の検索語句のインデックスを作成するために、インデックスを再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-130">After a full-text index is associated with a search property list, the index must be repopulated to index property-specific search terms.</span></span> <span data-ttu-id="a1e5d-131">フルテキスト インデックスの作成中、すべてのプロパティの内容が他の内容と共にフルテキスト インデックスに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-131">During full-text indexing, the contents of all properties are stored in the full-text index along with other content.</span></span> <span data-ttu-id="a1e5d-132">登録されたプロパティに含まれている検索語句のインデックスを作成しているときには、フルテキスト インデクサーによって、対応する内部プロパティ ID も語句と共に格納されます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-132">However, when indexing a search term found in a registered property, the full-text indexer also stores the corresponding internal property ID with the term.</span></span> <span data-ttu-id="a1e5d-133">一方、プロパティが登録されていない場合、プロパティはドキュメントの本文の一部であるかのようにフルテキスト インデックスに格納され、内部プロパティ ID として値 0 が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-133">In contrast, if a property is not registered, it is stored in the full-text index as if it were part of the document body, and it has a value of zero for the internal property ID.</span></span>  
  
 <span data-ttu-id="a1e5d-134">次の図に、フルテキスト インデックスに示された検索語句の論理ビューを示します。このフルテキスト インデックスは、前の図に示した検索プロパティ リストに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-134">The following illustration shows a logical view of how search terms appear in a full-text index that is associated with the search property list shown in the preceding illustration.</span></span> <span data-ttu-id="a1e5d-135">サンプル ドキュメント Document 1 には、ドキュメントの本文に加えて、Title、Author、および Keywords の 3 つのプロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-135">A sample document, Document 1 contains three properties-Title, Author, and Keywords-as well as the document body.</span></span> <span data-ttu-id="a1e5d-136">検索プロパティ リストに指定されている Title と Keywords のプロパティの場合、検索語句がフルテキスト インデックスの対応する内部プロパティ ID に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-136">For the properties Title and Keywords, which are specified in the search property list, search terms are associated with their corresponding internal property IDs in the full-text index.</span></span> <span data-ttu-id="a1e5d-137">これに対し、Author プロパティの内容については、ドキュメントの本文の一部であるかのようにインデックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-137">In contrast, the content of the Author property is indexed as if it were part of the document body.</span></span> <span data-ttu-id="a1e5d-138">これは、プロパティを登録することにより、プロパティに格納されている内容の量に応じてフルテキスト インデックスのサイズが増加することを示しています。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-138">This means registering a property increases the size of the full-text index somewhat, depending on the amount of content stored in the property.</span></span>  
  
 <span data-ttu-id="a1e5d-139">![検索プロパティ リストを使用するフルテキスト インデックス](../../database-engine/media/ifts-spl-and-fti.gif "検索プロパティ リストを使用するフルテキスト インデックス")</span><span class="sxs-lookup"><span data-stu-id="a1e5d-139">![Full-text index that uses a search property list](../../database-engine/media/ifts-spl-and-fti.gif "Full-text index that uses a search property list")</span></span>  
  
 <span data-ttu-id="a1e5d-140">Title プロパティの検索語句 ("Favorite"、"Biking"、および "Trails") は、このインデックスの Title に割り当てられた内部プロパティ ID 値 1 に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-140">Search terms in the Title property-"Favorite," "Biking," and "Trails"-are associated with the internal property ID assigned to Title for this index, 1.</span></span> <span data-ttu-id="a1e5d-141">Keywords プロパティの検索語句 ("biking" および "mountain") は、このインデックスの Tags に割り当てられた内部プロパティ ID 値 2 に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-141">Search terms in the Keywords property-"biking" and "mountain"-are associated with the internal property ID assigned to Tags for this index, 2.</span></span> <span data-ttu-id="a1e5d-142">Author プロパティの検索語句 ("Jane" および "Doe") およびドキュメントの本文の検索語句の内部プロパティ ID は 0 です。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-142">For search terms n the Author property-"Jane" and "Doe"-and search terms in the document body, the internal property ID is 0.</span></span> <span data-ttu-id="a1e5d-143">ここで、"biking" という語句は、Title プロパティ、Keywords (Tags) プロパティ、およびドキュメントの本文に出現します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-143">Note that the term "biking" occurs in the Title property, in the Keywords (Tags) property, and in the document body.</span></span> <span data-ttu-id="a1e5d-144">Title プロパティまたは Keywords (Tags) プロパティに対して "biking" をプロパティ検索すると、このドキュメントが結果として返されます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-144">A property search for "biking" in the Title or Keywords (Tags) property would return this document in the results.</span></span> <span data-ttu-id="a1e5d-145">"biking" の汎用フルテキスト クエリを実行した場合も、プロパティ検索用にインデックスが構成されていないかのように、このドキュメントが返されます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-145">A generic full-text query for "biking" would also return this document, just as if the index were not configured for property searching.</span></span> <span data-ttu-id="a1e5d-146">Author プロパティに対して "biking" のプロパティ検索を実行した場合、このドキュメントは返されません。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-146">A property search for "biking" in the Author property would not return this document.</span></span>  
  
 <span data-ttu-id="a1e5d-147">プロパティスコープのフルテキスト クエリでは、フルテキスト インデックスの現在の検索プロパティ リストに登録されている内部プロパティ ID が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-147">A property-scoped full-text query uses the internal property IDs registered for the current search property list of the full-text index.</span></span>  
  
  
  
##  <a name="impact-of-enabling-property-searching"></a><a name="impact"></a> <span data-ttu-id="a1e5d-148">プロパティ検索を有効にした場合の影響</span><span class="sxs-lookup"><span data-stu-id="a1e5d-148">Impact of Enabling Property Searching</span></span>  
 <span data-ttu-id="a1e5d-149">1 つまたは複数のプロパティを対象とした検索をサポートするようにフルテキスト インデックスを構成すると、検索プロパティ リストに指定したプロパティの数および各プロパティの内容に応じて、インデックスのサイズが増加します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-149">Configuring a full-text index to support searching on one or more properties increases the size of the index somewhat, depending on the number of properties you specify in your search property list and on the content of each property.</span></span>  
  
 <span data-ttu-id="a1e5d-150">Microsoft Word の一般的なコーパス、Excel<sup>??</sup><sup>、および</sup><sup>PowerPoint の</sup>テスト</span><span class="sxs-lookup"><span data-stu-id="a1e5d-150">In testing typical corpuses of Microsoft Word<sup>??</sup>, Excel<sup>??</sup>, and PowerPoint<sup>??</sup></span></span> <span data-ttu-id="a1e5d-151">ドキュメントでは、一般的な検索プロパティにインデックスを作成するようにフルテキストインデックスを構成しました。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-151">documents, we configured a full-text index to index typical search properties.</span></span> <span data-ttu-id="a1e5d-152">これらのプロパティのインデックスを作成した結果、フルテキスト インデックスのサイズは約 5% 増加しました。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-152">Indexing these properties increased the size of the full-text index size by approximately 5 percent.</span></span> <span data-ttu-id="a1e5d-153">サイズの増加に関するこの概算値は、ほとんどのドキュメント コーパスに当てはまると考えられます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-153">We anticipate that this approximate size increase will to be typical for most document corpuses.</span></span> <span data-ttu-id="a1e5d-154">ただし、最終的には、サイズの増加量は、全体的なデータ量に関連する特定のドキュメント コーパス内のプロパティ データの量に依存します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-154">However, ultimately, the size increase will depend on the amount of property data in a given document corpus relative to the amount of overall data.</span></span>  
  
  
  
##  <a name="creating-a-search-property-list-and-enabling-property-search"></a><a name="creating"></a> <span data-ttu-id="a1e5d-155">検索プロパティ リストの作成とプロパティ検索の有効化</span><span class="sxs-lookup"><span data-stu-id="a1e5d-155">Creating a Search Property List and Enabling Property Search</span></span>  
  
###  <a name="creating-a-search-property-list"></a><a name="creating_sub"></a><span data-ttu-id="a1e5d-156">検索プロパティリストの作成</span><span class="sxs-lookup"><span data-stu-id="a1e5d-156">Creating a Search Property List</span></span>  
 <span data-ttu-id="a1e5d-157">**Transact-SQL を使用して検索プロパティ リストを作成するには**</span><span class="sxs-lookup"><span data-stu-id="a1e5d-157">**To create a search property list with Transact-SQL**</span></span>  
  
 <span data-ttu-id="a1e5d-158">少なくともリストの名前を指定して、[CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-158">Use the [CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql) statement and provide at least a name the list.</span></span>  
  
##### <a name="to-create-a-search-property-list-in-management-studio"></a><span data-ttu-id="a1e5d-159">Management Studio で検索プロパティ リストを作成するには</span><span class="sxs-lookup"><span data-stu-id="a1e5d-159">To create a search property list in Management Studio</span></span>  
  
1.  <span data-ttu-id="a1e5d-160">オブジェクト エクスプローラーで、サーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-160">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="a1e5d-161">**[データベース]** を展開し、検索プロパティ リストを作成する対象のデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-161">Expand **Databases**, and then expand the database in which you want to create the search property list.</span></span>  
  
3.  <span data-ttu-id="a1e5d-162">**[ストレージ]** を展開し、 **[検索プロパティ リスト]** を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-162">Expand **Storage**, and then right-click **Search Property Lists**.</span></span>  
  
4.  <span data-ttu-id="a1e5d-163">**[新しい検索プロパティ リスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-163">Select **New Search Property List**.</span></span>  
  
5.  <span data-ttu-id="a1e5d-164">プロパティ リストの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-164">Specify the property list name.</span></span>  
  
6.  <span data-ttu-id="a1e5d-165">必要に応じて、他のユーザーをプロパティ リストの所有者として指定します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-165">Optionally, specify someone else as the property list owner.</span></span>  
  
7.  <span data-ttu-id="a1e5d-166">以下のオプションの 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-166">Select one of the following options:</span></span>  
  
    -   <span data-ttu-id="a1e5d-167">**[空の検索プロパティ リストを作成する]**</span><span class="sxs-lookup"><span data-stu-id="a1e5d-167">**Create an empty search property list**</span></span>  
  
    -   <span data-ttu-id="a1e5d-168">**[既存の検索プロパティ リストから作成する]**</span><span class="sxs-lookup"><span data-stu-id="a1e5d-168">**Create from an existing search property list**</span></span>  
  
     <span data-ttu-id="a1e5d-169">詳細については、「 [New Search Property List](../../database-engine/new-search-property-list.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-169">For more information, see [New Search Property List](../../database-engine/new-search-property-list.md).</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 
  
###  <a name="adding-properties-to-a-search-property-list"></a><a name="adding"></a><span data-ttu-id="a1e5d-170">検索プロパティリストへのプロパティの追加</span><span class="sxs-lookup"><span data-stu-id="a1e5d-170">Adding Properties to a Search Property List</span></span>  
 <span data-ttu-id="a1e5d-171">プロパティを検索するには、 *検索プロパティ リスト* を作成し、検索可能にする 1 つまたは複数のプロパティを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-171">Property searching requires creating a *search property list* and specifying one or more properties that you want to make searchable.</span></span> <span data-ttu-id="a1e5d-172">プロパティを検索プロパティ リストに追加すると、プロパティはその特定のリスト用に登録されます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-172">When you add a property to a search property list, the property is registered for that particular list.</span></span> <span data-ttu-id="a1e5d-173">プロパティを検索プロパティ リストに追加するには、次の値が必要です。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-173">To add a property to a search property list you need the following values:</span></span>  
  
-   <span data-ttu-id="a1e5d-174">プロパティ セット GUID</span><span class="sxs-lookup"><span data-stu-id="a1e5d-174">Property set GUID</span></span>  
  
     <span data-ttu-id="a1e5d-175">それぞれの検索プロパティは、関連するプロパティのグループを含む単一のプロパティ セットに属します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-175">Each search property belongs to single property set that contains a group of related properties.</span></span> <span data-ttu-id="a1e5d-176">それぞれのプロパティ セットは、グローバル一意識別子 (GUID) によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-176">Each property set is identified by a globally unique identifier (GUID).</span></span>  
  
-   <span data-ttu-id="a1e5d-177">プロパティ整数識別子</span><span class="sxs-lookup"><span data-stu-id="a1e5d-177">Property integer identifier</span></span>  
  
     <span data-ttu-id="a1e5d-178">それぞれの検索プロパティは、プロパティ セット内で一意な識別子を持っています。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-178">Each search property possesses an identifier that is unique within the property set.</span></span> <span data-ttu-id="a1e5d-179">特定のプロパティでは、識別子が整数または文字列である場合があります。ただし、フルテキスト検索では、整数識別子のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-179">Note that for a given property, the identifier could be either an integer or a string, however full-text search supports only integer identifiers.</span></span>  
  
-   <span data-ttu-id="a1e5d-180">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="a1e5d-180">Property name</span></span>  
  
     <span data-ttu-id="a1e5d-181">これは、プロパティを検索するフルテキスト クエリでユーザーが指定する名前です。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-181">This is the name that users will specify in full-text queries to search on the property.</span></span> <span data-ttu-id="a1e5d-182">プロパティ名の内部にはスペースを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-182">A property name can contain internal spaces.</span></span> <span data-ttu-id="a1e5d-183">最大長は 256 文字です。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-183">The maximum length is 256 characters.</span></span>  
  
     <span data-ttu-id="a1e5d-184">プロパティ名として、次のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-184">The property name can be any of the following:</span></span>  
  
    -   <span data-ttu-id="a1e5d-185">Windows の正規のプロパティ名 (`System.Author`、`System.Contact.HomeAddress` など)。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-185">The Windows canonical name of the property, such as `System.Author` or `System.Contact.HomeAddress`.</span></span>  
  
    -   <span data-ttu-id="a1e5d-186">ユーザーにとって覚えやすくわかりやすい名前。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-186">A user-friendly name that is easy for your users to remember.</span></span> <span data-ttu-id="a1e5d-187">いくつかのプロパティは "Author" や "Home Address" などの一般的なわかりやすい名前に関連付けられていますが、ユーザーにとって最も適した任意の名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-187">Some properties are associated with a well-known user-friendly name, such as "Author" or "Home Address," but you can specify whatever name is most appropriate to your users.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a1e5d-188">プロパティ セット GUID とプロパティ識別子の特定の組み合わせは、特定の検索プロパティ リスト内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-188">A given combination of property set GUID and property identifier must be unique in a given search property list.</span></span> <span data-ttu-id="a1e5d-189">これは、同じプロパティを別の名前または説明を使用して複数回追加できないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-189">This means that you cannot add the same property more than once with different names or descriptions.</span></span>  
  
-   <span data-ttu-id="a1e5d-190">プロパティの説明 (省略可能)</span><span class="sxs-lookup"><span data-stu-id="a1e5d-190">Property description (optional)</span></span>  
  
     <span data-ttu-id="a1e5d-191">検索プロパティを検索プロパティ リストに追加するとき、オプションで説明を記述できます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-191">When adding a search property to a search property list, you can supply an optional description.</span></span> <span data-ttu-id="a1e5d-192">たとえば、名前からはその内容がわかりにくいプロパティに関する情報を記述したり、プロパティのプロパティ セットに関する説明を記述したりできます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-192">For example, you might want to provide information about a property that is not evident from its name, or you might want to describe the property set of the property.</span></span>  
  
 <span data-ttu-id="a1e5d-193">**検索プロパティ リストの値を取得するには**</span><span class="sxs-lookup"><span data-stu-id="a1e5d-193">**To obtain values for a search property list**</span></span>  
  
 <span data-ttu-id="a1e5d-194">「 [検索プロパティのプロパティ セット GUID およびプロパティ整数 ID の取得](find-property-set-guids-and-property-integer-ids-for-search-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-194">See [Find Property Set GUIDs and Property Integer IDs for Search Properties](find-property-set-guids-and-property-integer-ids-for-search-properties.md).</span></span>  
  
 <span data-ttu-id="a1e5d-195">**Transact-SQL を使用してプロパティを検索プロパティ リストに追加するには**</span><span class="sxs-lookup"><span data-stu-id="a1e5d-195">**To add a property to a search property list with Transact-SQL**</span></span>  
  
 <span data-ttu-id="a1e5d-196">[ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql) ステートメントを、「[検索プロパティのプロパティ セット GUID およびプロパティ整数 ID の取得](find-property-set-guids-and-property-integer-ids-for-search-properties.md)」に説明されているいずれかの方法を使用して取得した値と共に使用します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-196">Use the [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql) statement with the values that you obtained by using one of the methods described in the topic, [Find Property Set GUIDs and Property Integer IDs for Search Properties](find-property-set-guids-and-property-integer-ids-for-search-properties.md).</span></span>  
  
 <span data-ttu-id="a1e5d-197">次の例では、これらの値を使用してプロパティを検索プロパティ リストに追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-197">The following example demonstrates the use of these values when adding a property to a search property list:</span></span>  
  
```  
ALTER SEARCH PROPERTY LIST DocumentTablePropertyList  
   ADD 'Title'  
   WITH ( PROPERTY_SET_GUID = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9', PROPERTY_INT_ID = 2,   
      PROPERTY_DESCRIPTION = 'System.Title - Title of the item.' );  
```  
  
 <span data-ttu-id="a1e5d-198">**Management Studio でプロパティを検索プロパティ リストに追加するには**</span><span class="sxs-lookup"><span data-stu-id="a1e5d-198">**To add a property to a search property list in Management Studio**</span></span>  
  
 <span data-ttu-id="a1e5d-199">**[検索プロパティ リストのプロパティ]** ダイアログ ボックスを使用して、検索プロパティを追加および削除します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-199">Use the **Search Property List Properties** dialog box to add and remove search properties.</span></span> <span data-ttu-id="a1e5d-200">オブジェクト エクスプローラーでは、関連するデータベースの **[ストレージ]** ノードの下に **[検索プロパティ リスト]** があります。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-200">You can find **Search Property Lists** in Object Explorer under the **Storage** node of the associated database.</span></span>  
  
  
  
###  <a name="associating-a-search-property-list-with-a-full-text-index"></a><a name="associating"></a><span data-ttu-id="a1e5d-201">検索プロパティリストとフルテキストインデックスの関連付け</span><span class="sxs-lookup"><span data-stu-id="a1e5d-201">Associating a Search Property List with a Full-Text Index</span></span>  
 <span data-ttu-id="a1e5d-202">検索プロパティ リストに登録されているプロパティを対象としたプロパティ検索をフルテキスト インデックスでサポートするためには、検索プロパティ リストとインデックスを関連付けた後、インデックスを再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-202">For a full-text index to support property searching on the properties that are registered for a search property list, you need to associate the search property list with the index and repopulate the index.</span></span> <span data-ttu-id="a1e5d-203">フルテキスト インデックスを再作成すると、登録された各プロパティに含まれている検索語句に対して、プロパティ固有のインデックス エントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-203">Repopulating the full-text index creates property-specific index entries for search terms in each of the registered properties.</span></span>  
  
 <span data-ttu-id="a1e5d-204">フルテキスト インデックスがこの検索プロパティ リストに関連付けられている限り、フルテキスト クエリで CONTAINS 述語の PROPERTY オプションを使用して、検索プロパティ リストに登録されているプロパティを対象に検索を実行できます。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-204">As long as the full-text index remains associated with this search property list, full-text query can use the PROPERTY option of the CONTAINS predicate to search on properties that are registered for that search property list.</span></span>  
  
 <span data-ttu-id="a1e5d-205">フルテキスト インデックスに関連付けられている検索プロパティ リストを変更した場合は、インデックスを一貫性のある状態に保つために、インデックスの再構築が必要になります。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-205">If you change the search property list associated with a full-text index, then the index must be rebuilt to bring it into a consistent state.</span></span> <span data-ttu-id="a1e5d-206">インデックスは即座に切り捨てられ、完全作成が実行されるまで空になります。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-206">The index is truncated immediately and is empty until the full population runs.</span></span> <span data-ttu-id="a1e5d-207">検索プロパティ リストの変更によってインデックスが再構築される場合の詳細については、「[ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)」の「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-207">For more information about when changing the search property list causes rebuilding the index, see "Remarks," in [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).</span></span>  
  
 <span data-ttu-id="a1e5d-208">**Transact-SQL を使用して検索プロパティ リストをフルテキスト インデックスに関連付けるには**</span><span class="sxs-lookup"><span data-stu-id="a1e5d-208">**To associate a search property list with a full-text index with Transact-SQL**</span></span>  
  
 <span data-ttu-id="a1e5d-209">[ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ステートメントを `SET SEARCH PROPERTY LIST = <property_list_name>` 句と共に使用します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-209">Use the [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) statement with the `SET SEARCH PROPERTY LIST = <property_list_name>` clause.</span></span>  
  
 <span data-ttu-id="a1e5d-210">**Management Studio を使用して検索プロパティ リストをフルテキスト インデックスに関連付けるには**</span><span class="sxs-lookup"><span data-stu-id="a1e5d-210">**To associate a search property list with a full-text index with Management Studio**</span></span>  
  
 <span data-ttu-id="a1e5d-211">**[フルテキスト インデックスのプロパティ]** ダイアログ ボックスの **[全般]** ページで、 **[検索プロパティ リスト]** の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-211">Specify a value for **Search Property List** on the **General** page of the **Full-Text Index Properties** dialog box.</span></span>  
  
  
  
##  <a name="querying-search-properties-with-contains"></a><a name="Ov_CONTAINS_using_PROPERTY"></a><span data-ttu-id="a1e5d-212">CONTAINS を使用した検索プロパティのクエリ</span><span class="sxs-lookup"><span data-stu-id="a1e5d-212">Querying Search Properties with CONTAINS</span></span>  
 <span data-ttu-id="a1e5d-213">プロパティ スコープのフルテキスト クエリのための [CONTAINS](/sql/t-sql/queries/contains-transact-sql) の基本的な構文を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-213">The basic [CONTAINS](/sql/t-sql/queries/contains-transact-sql) syntax for a property-scoped full-text query is as follows:</span></span>  
  
```sql  
SELECT column_name FROM table_name  
  WHERE CONTAINS ( PROPERTY ( column_name, 'property_name' ), '<contains_search_condition>' )  
```  
  
 <span data-ttu-id="a1e5d-214">たとえば、次のクエリは、 `Title`データベースの `Document` テーブルの `Production.Document` 列内で、インデックス化されたプロパティ `AdventureWorks` に対する検索を実行します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-214">For example, the following query searches on an indexed property, `Title`, in the `Document` column of the `Production.Document` table of the `AdventureWorks` database.</span></span> <span data-ttu-id="a1e5d-215">このクエリは、 `Title` という文字列が `Maintenance` プロパティに含まれているドキュメントのみを返します。 `Repair`</span><span class="sxs-lookup"><span data-stu-id="a1e5d-215">The query returns only documents whose `Title` property contains the string `Maintenance` or `Repair`</span></span>  
  
```  
USE AdventureWorks  
GO  
SELECT Document FROM Production.Document  
  WHERE CONTAINS ( PROPERTY ( Document, 'Title' ), 'Maintenance OR Repair')  
GO  
```  
  
 <span data-ttu-id="a1e5d-216">この例では、ドキュメントの IFilter で Title プロパティが抽出されること、Title プロパティが検索プロパティ リストに追加されること、および検索プロパティ リストがフルテキスト インデックスに関連付けられていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-216">This example assumes that the IFilter for the document extracts its Title property, that the Title property is added to the search property list, and that the search property list is associated with the full-text index.</span></span>  
  
  
  
##  <a name="managing-search-property-lists"></a><a name="managing"></a> <span data-ttu-id="a1e5d-217">検索プロパティ リストの管理</span><span class="sxs-lookup"><span data-stu-id="a1e5d-217">Managing Search Property Lists</span></span>  
  
###  <a name="viewing-and-changing-a-search-property-list"></a><a name="viewing"></a> <span data-ttu-id="a1e5d-218">検索プロパティ リストの表示および変更</span><span class="sxs-lookup"><span data-stu-id="a1e5d-218">Viewing and Changing a Search Property List</span></span>  
 <span data-ttu-id="a1e5d-219">**Transact-SQL を使用して検索プロパティ リストを変更するには**</span><span class="sxs-lookup"><span data-stu-id="a1e5d-219">**To change a search property list with Transact-SQL**</span></span>  
  
 <span data-ttu-id="a1e5d-220">[ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql) ステートメントを使用して、検索プロパティを追加または削除します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-220">Use the [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql) statement to add or remove search properties.</span></span>  
  
##### <a name="to-view-and-change-a-search-property-list-in-management-studio"></a><span data-ttu-id="a1e5d-221">Management Studio で検索プロパティ リストを表示および変更するには</span><span class="sxs-lookup"><span data-stu-id="a1e5d-221">To view and change a search property list in Management Studio</span></span>  
  
1.  <span data-ttu-id="a1e5d-222">オブジェクト エクスプローラーで、サーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-222">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="a1e5d-223">**[データベース]** を展開し、データベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-223">Expand **Databases**, and then expand the database.</span></span>  
  
3.  <span data-ttu-id="a1e5d-224">**[記憶域]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-224">Expand **Storage**.</span></span>  
  
4.  <span data-ttu-id="a1e5d-225">**[検索プロパティ リスト]** を展開して、検索プロパティ リストを表示します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-225">Expand **Search Property Lists** to display the search property lists.</span></span>  
  
5.  <span data-ttu-id="a1e5d-226">プロパティ リストを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-226">Right-click the property list, and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="a1e5d-227">**[検索プロパティ リスト エディター]** ダイアログ ボックスで、プロパティ グリッドを使用して、検索プロパティを追加または削除します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-227">In the **Search Property List Editor** dialog box, use the Properties grid to add or remove search properties:</span></span>  
  
    1.  <span data-ttu-id="a1e5d-228">ドキュメント プロパティを削除するには、プロパティの左側にある行ヘッダーをクリックして、Del キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-228">To remove a document property, click the row header to the left of the property, and press DEL .</span></span>  
  
    2.  <span data-ttu-id="a1e5d-229">ドキュメントプロパティを追加するには、一覧の一番下にある空の行をの右側にクリックし、 **\*** 新しいプロパティの値を入力します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-229">To add a document property, click in the empty row at the bottom of the list, to the right of the **\***, and enter the values for the new property.</span></span>  
  
         <span data-ttu-id="a1e5d-230">これらの値の詳細については、「 [検索プロパティ リスト エディター](../../database-engine/search-property-list-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-230">For information about these values, see [Search Property List Editor](../../database-engine/search-property-list-editor.md).</span></span> <span data-ttu-id="a1e5d-231">Microsoft によって定義されているプロパティのこれらの値を取得する方法については、「 [検索プロパティのプロパティ セット GUID およびプロパティ整数 ID の取得](find-property-set-guids-and-property-integer-ids-for-search-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-231">For information about how to obtain these values for properties defined by Microsoft, see [Find Property Set GUIDs and Property Integer IDs for Search Properties](find-property-set-guids-and-property-integer-ids-for-search-properties.md).</span></span> <span data-ttu-id="a1e5d-232">独立系ソフトウェア ベンダー (ISV) によって定義されたプロパティの詳細については、そのベンダーのマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-232">For information about properties defined by an independent software vendor (ISV), see the documentation of that vendor.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
###  <a name="deleting-a-search-property-list"></a><a name="deleting"></a> <span data-ttu-id="a1e5d-233">検索プロパティ リストの削除</span><span class="sxs-lookup"><span data-stu-id="a1e5d-233">Deleting a Search Property List</span></span>  
 <span data-ttu-id="a1e5d-234">リストがいずれかのフルテキスト インデックスに関連付けられている場合は、データベースからプロパティ リストを削除できません。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-234">You cannot drop a property list from a database while the list is associated with any full-text index.</span></span>  
  
 <span data-ttu-id="a1e5d-235">**Transact-SQL を使用して検索プロパティ リストを削除するには**</span><span class="sxs-lookup"><span data-stu-id="a1e5d-235">**To delete a search property list with Transact-SQL**</span></span>  
  
 <span data-ttu-id="a1e5d-236">[DROP SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-search-property-list-transact-sql) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-236">Use the [DROP SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-search-property-list-transact-sql) statement.</span></span>  
  
##### <a name="to-delete-a-search-property-list-in-management-studio"></a><span data-ttu-id="a1e5d-237">Management Studio で検索プロパティ リストを削除するには</span><span class="sxs-lookup"><span data-stu-id="a1e5d-237">To delete a search property list in Management Studio</span></span>  
  
1.  <span data-ttu-id="a1e5d-238">オブジェクト エクスプローラーで、サーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-238">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="a1e5d-239">**[データベース]** を展開し、データベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-239">Expand **Databases**, and then expand the database.</span></span>  
  
3.  <span data-ttu-id="a1e5d-240">**[ストレージ]** を展開し、 **[検索プロパティ リスト]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-240">Expand **Storage**, and then expand the **Search Property Lists** node.</span></span>  
  
4.  <span data-ttu-id="a1e5d-241">削除するプロパティ リストを右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a1e5d-241">Right-click the property list that you want to delete, and click **Delete**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

  
## <a name="see-also"></a><span data-ttu-id="a1e5d-242">参照</span><span class="sxs-lookup"><span data-stu-id="a1e5d-242">See Also</span></span>  
 <span data-ttu-id="a1e5d-243">[検索プロパティのプロパティセット Guid とプロパティ整数 Id を検索します](find-property-set-guids-and-property-integer-ids-for-search-properties.md) </span><span class="sxs-lookup"><span data-stu-id="a1e5d-243">[Find Property Set GUIDs and Property Integer IDs for Search Properties](find-property-set-guids-and-property-integer-ids-for-search-properties.md) </span></span>  
 [<span data-ttu-id="a1e5d-244">検索用フィルターの構成と管理</span><span class="sxs-lookup"><span data-stu-id="a1e5d-244">Configure and Manage Filters for Search</span></span>](configure-and-manage-filters-for-search.md)  
  
  
