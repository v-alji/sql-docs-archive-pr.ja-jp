---
title: フルテキスト検索の概要 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs [SQL Server], creating
- full-text indexes [SQL Server], creating
- full-text search [SQL Server], about
- full-text search [SQL Server], setting up
ms.assetid: 1fa628ba-0ee4-4d8f-b086-c4e52962ca4a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: eec806bffba330ac3ab995c1b3bfd3504589ecfd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714102"
---
# <a name="get-started-with-full-text-search"></a><span data-ttu-id="3fc87-102">フルテキスト検索の概要</span><span class="sxs-lookup"><span data-stu-id="3fc87-102">Get Started with Full-Text Search</span></span>
  <span data-ttu-id="3fc87-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータベースでは、フルテキストが既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="3fc87-103">Databases in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are full-text enabled by default.</span></span> <span data-ttu-id="3fc87-104">ただし、テーブルでフルテキスト インデックスを使用するには、Full-Text Engine を使用してアクセスするテーブルの列に対してフルテキスト インデックス作成機能をセットアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3fc87-104">However, to use a full-text index on a table, you must set up full-text indexing capability on the columns of the tables that you want to access using the Full-Text Engine.</span></span>  
  
##  <a name="configuring-a-database-for-full-text-search"></a><a name="configure"></a><span data-ttu-id="3fc87-105">フルテキスト検索のためのデータベースの構成</span><span class="sxs-lookup"><span data-stu-id="3fc87-105">Configuring a Database for Full-Text Search</span></span>  
 <span data-ttu-id="3fc87-106">どのシナリオでも、データベース管理者は次の基本的な手順を実行して、データベースでフルテキスト検索用のテーブル列を構成します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-106">For any scenario, a database administrator performs the following basic steps to configure table columns in a database for full-text search:</span></span>  
  
1.  <span data-ttu-id="3fc87-107">フルテキスト カタログを作成します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-107">Create a full-text catalog.</span></span>  
  
2.  <span data-ttu-id="3fc87-108">検索する各テーブルに、次の方法でフルテキスト インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-108">On each table that you want to search, create a full-text index by:</span></span>  
  
    1.  <span data-ttu-id="3fc87-109">フルテキスト インデックスに含めるテキスト列を特定します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-109">Identify each text columns that you want to include in the full-text index.</span></span>  
  
    2.  <span data-ttu-id="3fc87-110">バイナリデータ (、またはデータ) として格納されているドキュメントが特定の列に含まれている場合は、 `varbinary(max)` `image` インデックスを作成する列の各ドキュメントの型を識別するテーブル列 (*型列*) を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3fc87-110">If a given column contains documents stored as binary data (`varbinary(max)`, or `image` data), you must specify a table column (the *type column*) that identifies the type of each document in the column being indexed.</span></span>  
  
    3.  <span data-ttu-id="3fc87-111">列内のドキュメントに対してフルテキスト検索で使用される言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-111">Specify the language that you want full-text search to use on the documents in the column.</span></span>  
  
    4.  <span data-ttu-id="3fc87-112">ベース テーブルとその列での変更を追跡するためにフルテキスト インデックスで使用する変更追跡メカニズムを選択します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-112">Choose the change-tracking mechanism that you want to use on the full-text index to track changes in the base table and its columns.</span></span>  
  
 <span data-ttu-id="3fc87-113">フルテキスト検索では、ワード ブレーカー、ステマー、ストップワード (ノイズ ワードとも呼ばれます) を含んだストップリスト、類義語辞典ファイルの各*言語コンポーネント*を使用して、複数の言語がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="3fc87-113">Full-text search supports multiple languages through the use of the following *linguistic components*: word breakers and stemmers, stoplists that contain stopwords (also known as noise words), and thesaurus files.</span></span> <span data-ttu-id="3fc87-114">類義語辞典ファイルと (場合によって) ストップリストは、データベース管理者が構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3fc87-114">Thesaurus files and, in some cases, stoplists require configuration by a database administrator.</span></span> <span data-ttu-id="3fc87-115">特定の類義語辞典ファイルは、対応する言語を使用するすべてのフルテキスト インデックスをサポートし、特定のストップリストには任意の数のフルテキスト インデックスを関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="3fc87-115">A given thesaurus file supports all full-text indexes that use the corresponding language, and a given stoplist can be associated with as many full-text indexes as you want.</span></span>  
  
##  <a name="setting-up-a-full-text-catalog-and-index"></a><a name="setup"></a><span data-ttu-id="3fc87-116">フルテキストカタログとインデックスの設定</span><span class="sxs-lookup"><span data-stu-id="3fc87-116">Setting Up a Full-Text Catalog and Index</span></span>  
 <span data-ttu-id="3fc87-117">この作業には、次の基本的な手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3fc87-117">This involves the following basic steps:</span></span>  
  
1.  <span data-ttu-id="3fc87-118">フルテキスト インデックスを格納するフルテキスト カタログを作成する。</span><span class="sxs-lookup"><span data-stu-id="3fc87-118">Create a full-text catalog to store full-text indexes.</span></span>  
  
     <span data-ttu-id="3fc87-119">各フルテキスト インデックスは、フルテキスト カタログに属している必要があります。</span><span class="sxs-lookup"><span data-stu-id="3fc87-119">Each full-text index must belong to a full-text catalog.</span></span> <span data-ttu-id="3fc87-120">フルテキスト インデックスごとにテキスト カタログを作成するか、複数のフルテキスト インデックスを特定のカタログに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="3fc87-120">You can create a separate text catalog for each full-text index, or you can associate multiple full-text indexes with a given catalog.</span></span> <span data-ttu-id="3fc87-121">フルテキスト カタログは仮想オブジェクトであり、ファイル グループには属しません。</span><span class="sxs-lookup"><span data-stu-id="3fc87-121">A full-text catalog is a virtual object and does not belong to any filegroup.</span></span> <span data-ttu-id="3fc87-122">カタログは、フルテキスト インデックスのグループを指す論理的概念です。</span><span class="sxs-lookup"><span data-stu-id="3fc87-122">The catalog is a logical concept that refers to a group of full-text indexes.</span></span>  
  
2.  <span data-ttu-id="3fc87-123">テーブルまたはインデックス付きビューで、フルテキスト インデックスを作成する。</span><span class="sxs-lookup"><span data-stu-id="3fc87-123">Create a full-text index on the table or indexed view.</span></span>  
  
     <span data-ttu-id="3fc87-124">フルテキスト インデックスは、Full-Text Engine により構築および管理されるトークンベースの特殊な機能インデックスです。</span><span class="sxs-lookup"><span data-stu-id="3fc87-124">A full-text index is a special type of token-based functional index that is built and maintained by the Full-Text Engine.</span></span> <span data-ttu-id="3fc87-125">テーブルまたはビューにフルテキスト検索を作成するには、そのテーブルまたはビューに、単一列で非 NULL 値の一意なインデックスが作成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3fc87-125">To create full-text search on a table or view, it must have a unique, single-column, non-nullable index.</span></span> <span data-ttu-id="3fc87-126">Full-Text Engine では、テーブルの各行を一意の圧縮可能なキーにマップするために、この一意のインデックスが必要になります。</span><span class="sxs-lookup"><span data-stu-id="3fc87-126">The Full-Text Engine requires this unique index to map each row in the table to a unique, compressible key.</span></span> <span data-ttu-id="3fc87-127">フルテキスト インデックスには、`char`、`varchar`、`nchar`、`nvarchar`、`text`、`ntext`、`image`、`xml`、`varbinary`、`varbinary(max)` 型の列を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="3fc87-127">A full-text index can include `char`, `varchar`, `nchar`, `nvarchar`, `text`, `ntext`, `image`, `xml`, `varbinary`, and `varbinary(max)` columns.</span></span> <span data-ttu-id="3fc87-128">詳細については、「 [フルテキスト インデックスの作成と管理](create-and-manage-full-text-indexes.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3fc87-128">For more information, see [Create and Manage Full-Text Indexes](create-and-manage-full-text-indexes.md).</span></span>  
  
 <span data-ttu-id="3fc87-129">フルテキスト インデックスの作成について学習する前に、フルテキスト インデックスと標準の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インデックスの違いを見ることが重要です。</span><span class="sxs-lookup"><span data-stu-id="3fc87-129">Before learning about creating full-text indexes, it is important to consider how they differ from regular [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] indexes.</span></span> <span data-ttu-id="3fc87-130">次の表に、エディション間の違いを示します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-130">The following table lists the differences.</span></span>  
  
|<span data-ttu-id="3fc87-131">フルテキスト インデックス</span><span class="sxs-lookup"><span data-stu-id="3fc87-131">Full-text indexes</span></span>|<span data-ttu-id="3fc87-132">標準の SQL Server インデックス</span><span class="sxs-lookup"><span data-stu-id="3fc87-132">Regular SQL Server indexes</span></span>|  
|------------------------|--------------------------------|  
|<span data-ttu-id="3fc87-133">1 つのテーブルに対し、1 つのフルテキスト インデックスしか使用できません。</span><span class="sxs-lookup"><span data-stu-id="3fc87-133">Only one full-text index allowed per table.</span></span>|<span data-ttu-id="3fc87-134">1 つのテーブルに対し、複数の標準インデックスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3fc87-134">Several regular indexes allowed per table.</span></span>|  
|<span data-ttu-id="3fc87-135">フルテキスト インデックスへのデータの追加は*作成*と呼ばれ、スケジュールによる要求または個別の要求のどちらかを通じて要求できます。または、新規データの追加と共に自動的に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3fc87-135">The addition of data to full-text indexes, called a *population*, can be requested through either a schedule or a specific request, or can occur automatically with the addition of new data.</span></span>|<span data-ttu-id="3fc87-136">関連するデータが挿入、更新、または削除されたときに、自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="3fc87-136">Updated automatically when the data upon which they are based is inserted, updated, or deleted.</span></span>|  
|<span data-ttu-id="3fc87-137">同じデータベース内で 1 つ以上のフルテキスト カタログにグループ化されます。</span><span class="sxs-lookup"><span data-stu-id="3fc87-137">Grouped within the same database into one or more full-text catalogs.</span></span>|<span data-ttu-id="3fc87-138">グループ化されません。</span><span class="sxs-lookup"><span data-stu-id="3fc87-138">Not grouped.</span></span>|  
  
  
##  <a name="choosing-options-for-a-full-text-index"></a><a name="options"></a><span data-ttu-id="3fc87-139">フルテキストインデックスのオプションの選択</span><span class="sxs-lookup"><span data-stu-id="3fc87-139">Choosing Options for a Full-Text Index</span></span>  
 <span data-ttu-id="3fc87-140">ここでは、次について説明します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-140">This section covers the following:</span></span>  
  
-   <span data-ttu-id="3fc87-141">列の言語の選択</span><span class="sxs-lookup"><span data-stu-id="3fc87-141">Choosing the column language</span></span>  
  
-   <span data-ttu-id="3fc87-142">フルテキスト インデックスのファイル グループの選択</span><span class="sxs-lookup"><span data-stu-id="3fc87-142">Choosing a filegroup for a full-text index</span></span>  
  
-   <span data-ttu-id="3fc87-143">フルテキスト カタログへのフルテキスト インデックスの割り当て</span><span class="sxs-lookup"><span data-stu-id="3fc87-143">Assigning the full-text index to a full-text catalog</span></span>  
  
-   <span data-ttu-id="3fc87-144">ストップリストとフルテキスト インデックスの関連付け</span><span class="sxs-lookup"><span data-stu-id="3fc87-144">Associating a stoplist with the full-text index</span></span>  
  
-   <span data-ttu-id="3fc87-145">フルテキスト インデックスの更新</span><span class="sxs-lookup"><span data-stu-id="3fc87-145">Updating a full-text index</span></span>  
  
### <a name="choosing-the-column-language"></a><span data-ttu-id="3fc87-146">列の言語の選択</span><span class="sxs-lookup"><span data-stu-id="3fc87-146">Choosing the Column Language</span></span>  
 <span data-ttu-id="3fc87-147">列の言語を選択する際の考慮点については、「[フルテキスト インデックス作成時の言語の選択](choose-a-language-when-creating-a-full-text-index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fc87-147">For information about things to consider when you are choosing the column language, see [Choose a Language When Creating a Full-Text Index](choose-a-language-when-creating-a-full-text-index.md).</span></span>  
  
### <a name="choosing-a-filegroup-for-a-full-text-index"></a><span data-ttu-id="3fc87-148">フルテキスト インデックスのファイル グループの選択</span><span class="sxs-lookup"><span data-stu-id="3fc87-148">Choosing a Filegroup for a Full-Text Index</span></span>  
 <span data-ttu-id="3fc87-149">フルテキスト インデックスの作成処理では、I/O が非常に集中します (高い頻度で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からデータを読み取り、フィルター選択されたデータをフルテキスト インデックスに反映するため)。</span><span class="sxs-lookup"><span data-stu-id="3fc87-149">The process of building a full-text index is fairly I/O intensive (on a high level, it consists of reading data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and then propagating the filtered data to the full-text index).</span></span> <span data-ttu-id="3fc87-150">I/O パフォーマンスの最大化に最適なデータベース ファイル グループにフルテキスト インデックスを配置するか、他のボリュームの別のファイル グループにフルテキスト インデックスを配置することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3fc87-150">As a best practice, locate a full-text index in the database filegroup that is best for maximizing I/O performance or locate the full-text indexes in a different filegroup on another volume.</span></span>  
  
 <span data-ttu-id="3fc87-151">管理のしやすさが重要である場合は、テーブル データと関連するフルテキスト カタログは同じファイル グループに格納することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3fc87-151">When ease of management is important to you, we recommend that you store table data and any affiliated full-text catalogs in the same filegroup.</span></span> <span data-ttu-id="3fc87-152">パフォーマンス上の理由から、別々のボリュームに格納されている別々のファイル グループにテーブル データとフルテキスト インデックスを配置して、I/O 並列処理を最大限に高めることが必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="3fc87-152">Sometimes, for performance reasons, you might want to have the table data and the full-text index in different filegroups that are stored on different volumes to maximize I/O parallelism.</span></span>  
  
  
### <a name="assigning-the-full-text-index-to-a-full-text-catalog"></a><span data-ttu-id="3fc87-153">フルテキスト カタログへのフルテキスト インデックスの割り当て</span><span class="sxs-lookup"><span data-stu-id="3fc87-153">Assigning the Full-Text Index to a Full-Text Catalog</span></span>  
 <span data-ttu-id="3fc87-154">フルテキスト カタログ内のテーブルに対するフルテキスト インデックスの割り当てを立案することは重要です。</span><span class="sxs-lookup"><span data-stu-id="3fc87-154">It is important to plan the placement of full-text indexes for tables in full-text catalogs.</span></span>  
  
 <span data-ttu-id="3fc87-155">変更が少ないテーブル、変更が多いテーブル、または特定の時間帯に頻繁に変更されるテーブルなど、同じ更新特性を持つテーブルは、同じフルテキスト カタログの下にまとめて関連付けることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3fc87-155">We recommend associating tables with the same update characteristics (such as small number of changes versus large number of changes, or tables that change frequently during a particular time of day) together under the same full-text catalog.</span></span> <span data-ttu-id="3fc87-156">フルテキスト カタログの作成スケジュールをセットアップすると、データベースの利用率が高いときでもデータベース サーバーのリソース使用に大きな影響を及ぼすことなく、フルテキスト インデックスとテーブルの同期が維持されるようになります。</span><span class="sxs-lookup"><span data-stu-id="3fc87-156">By setting up full-text catalog population schedules, full-text indexes stay synchronous with the tables without adversely affecting the resource usage of the database server during periods of high database activity.</span></span>  
  
 <span data-ttu-id="3fc87-157">フルテキスト カタログにテーブルを割り当てる際には、次のガイドラインを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="3fc87-157">When you assign a table to a full-text catalog, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="3fc87-158">常に、一意なフルテキスト キーに利用可能な最小の一意なインデックスを選択してください。</span><span class="sxs-lookup"><span data-stu-id="3fc87-158">Always select the smallest unique index available for your full-text unique key.</span></span> <span data-ttu-id="3fc87-159">(4 バイトの整数ベースのインデックスが最適です)。これにより、ファイルシステム内の Search サービスで必要とされるリソースが大幅に減少 [!INCLUDE[msCoName](../../includes/msconame-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-159">(A 4-byte, integer-based index is optimal.) This reduces the resources required by [!INCLUDE[msCoName](../../includes/msconame-md.md)] Search service in the file system significantly.</span></span> <span data-ttu-id="3fc87-160">主キーが大きい場合 (100 バイト以上)、テーブル内の他の一意なインデックスを選択するか、または他の一意なインデックスを作成して、フルテキスト インデックス用のキーにすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="3fc87-160">If the primary key is large (over 100 bytes), consider choosing another unique index in the table (or creating another unique index) as the full-text unique key.</span></span> <span data-ttu-id="3fc87-161">そうしないと、一意なフルテキスト キーのサイズが最大サイズ (900 バイト) を超えた場合、フルテキストの作成を続行できなくなります。</span><span class="sxs-lookup"><span data-stu-id="3fc87-161">Otherwise, if the full-text unique key size exceeds the maximum size allowed (900 bytes), full-text population will not be able to proceed.</span></span>  
  
-   <span data-ttu-id="3fc87-162">数百万の行を持つテーブルにインデックスを作成しようとしている場合、そのテーブル専用のフルテキスト カタログを割り当ててください。</span><span class="sxs-lookup"><span data-stu-id="3fc87-162">If you are indexing a table that has millions of rows, assign the table to its own full-text catalog.</span></span>  
  
-   <span data-ttu-id="3fc87-163">フルテキスト インデックスを作成するテーブル内の変更量だけではなく、そのテーブル内の行の総数についても考慮してください。</span><span class="sxs-lookup"><span data-stu-id="3fc87-163">Consider the amount of changes occurring in the tables being full-text indexed, as well as the total number of rows.</span></span> <span data-ttu-id="3fc87-164">変更される行と、最後にフルテキスト インデックスを作成したときにテーブル内に存在した行の総数が数百万行に及ぶ場合は、そのテーブルを専用のフルテキスト カタログに割り当ててください。</span><span class="sxs-lookup"><span data-stu-id="3fc87-164">If the total number of rows being changed, together with the numbers of rows in the table present during the last full-text population, represents millions of rows, assign the table to its own full-text catalog.</span></span>  
  
  
### <a name="associating-a-stoplist-with-the-full-text-index"></a><span data-ttu-id="3fc87-165">ストップリストとフルテキスト インデックスの関連付け</span><span class="sxs-lookup"><span data-stu-id="3fc87-165">Associating a Stoplist with the Full-Text Index</span></span>  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="3fc87-166">では、ストップリストが導入されています。</span><span class="sxs-lookup"><span data-stu-id="3fc87-166">introduces stoplists.</span></span> <span data-ttu-id="3fc87-167">*ストップリスト* は、ストップワード (ノイズ ワードとも呼ばれます) の一覧です。</span><span class="sxs-lookup"><span data-stu-id="3fc87-167">A *stoplist* is a list of stopwords, also known as noise words.</span></span> <span data-ttu-id="3fc87-168">ストップリストは各フルテキスト インデックスに関連付けられ、そのストップリスト内の単語がそのインデックスのフルテキスト クエリに適用されます。</span><span class="sxs-lookup"><span data-stu-id="3fc87-168">A stoplist is associated with each full-text index, and the words in that stoplist are applied to full-text queries on that index.</span></span> <span data-ttu-id="3fc87-169">既定では、システム ストップリストは、新しいフルテキスト インデックスに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="3fc87-169">By default, the system stoplist is associated with a new full-text index.</span></span> <span data-ttu-id="3fc87-170">ただし、独自のストップリストを作成して使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="3fc87-170">However, you can create and use your own stoplist instead.</span></span> <span data-ttu-id="3fc87-171">詳細については、「 [フルテキスト検索に使用するストップワードとストップリストの構成と管理](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fc87-171">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).</span></span>  
  
 <span data-ttu-id="3fc87-172">たとえば、次の[CREATE フルテキストストップリスト](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)ステートメントでは、 [!INCLUDE[tsql](../../../includes/tsql-md.md)] システムストップリストからコピーすることによって、myStoplist3 という名前の新しいフルテキストストップリストを作成します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-172">For example, the following [CREATE FULLTEXT STOPLIST](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement creates a new full-text stoplist named myStoplist3 by copying from the system stoplist:</span></span>  
  
```  
CREATE FULLTEXT STOPLIST myStoplist FROM SYSTEM STOPLIST;  
GO  
```  
  
 <span data-ttu-id="3fc87-173">次の[ALTER フルテキストストップリスト](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)ステートメントでは、 [!INCLUDE[tsql](../../../includes/tsql-md.md)] myStoplist という名前のストップリストを変更して、単語 ' En ' をスペイン語用に、次にフランス語用に追加します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-173">The following [ALTER FULLTEXT STOPLIST](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement alters a stoplist named myStoplist, adding the word 'en', first for Spanish and then for French:</span></span>  
  
```  
ALTER FULLTEXT STOPLIST MyStoplist ADD 'en' LANGUAGE 'Spanish';  
ALTER FULLTEXT STOPLIST MyStoplist ADD 'en' LANGUAGE 'French';  
GO  
```  
  
  
### <a name="updating-a-full-text-index"></a><span data-ttu-id="3fc87-174">フルテキスト インデックスの更新</span><span class="sxs-lookup"><span data-stu-id="3fc87-174">Updating a Full-Text Index</span></span>  
 <span data-ttu-id="3fc87-175">標準の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インデックスと同様に、フルテキスト インデックスは、関連付けられたテーブルの中でデータが変更されると、自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="3fc87-175">Like regular [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] indexes, full-text indexes can be automatically updated as data is modified in the associated tables.</span></span> <span data-ttu-id="3fc87-176">これは既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="3fc87-176">This is the default behavior.</span></span> <span data-ttu-id="3fc87-177">指定したスケジュール間隔または手動でフルテキスト インデックスを最新の状態に保つこともできます。</span><span class="sxs-lookup"><span data-stu-id="3fc87-177">Alternatively, you can keep your full-text indexes up-to-date manually or at specified scheduled intervals.</span></span> <span data-ttu-id="3fc87-178">フルテキスト インデックスの作成は時間とリソースの消費が大きいため、インデックスの更新は、通常、非同期プロセスで実行します。この非同期プロセスは、バックグラウンドで実行され、ベース テーブルの変更後にフルテキスト インデックスを最新の状態に維持します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-178">Populating a full-text index can be time-consuming and resource-intensive, therefore, index updating is usually performed as an asynchronous process that runs in the background and keeps the full-text index up to date after modifications in the base table.</span></span> <span data-ttu-id="3fc87-179">ベース テーブルのそれぞれの変更後すぐにフルテキスト インデックスを更新すると、リソースを大量に消費することがあります。</span><span class="sxs-lookup"><span data-stu-id="3fc87-179">Updating a full-text index immediately after each change in the base table can be resource-intensive.</span></span> <span data-ttu-id="3fc87-180">そのため、更新、挿入、または削除の率が非常に高い場合は、クエリのパフォーマンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3fc87-180">Therefore, if you have a very high update/insert/delete rate, you might experience some degradation in query performance.</span></span> <span data-ttu-id="3fc87-181">この問題が発生した場合、リソースについてクエリと競合しないよう、手動による変更追跡の更新をスケジュール設定して、適宜、大量の変更に対応することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="3fc87-181">If this occurs, consider scheduling manual change tracking updates to keep up with the numerous changes from time to time, rather than competing with queries for resources.</span></span>  
  
 <span data-ttu-id="3fc87-182">作成状態を監視するには、FULLTEXTCATALOGPROPERTY 関数または OBJECTPROPERTYEX 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-182">To monitor the population status, use either the FULLTEXTCATALOGPROPERTY or OBJECTPROPERTYEX functions.</span></span> <span data-ttu-id="3fc87-183">カタログ作成状態を取得するには、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-183">To get the catalog population status, run the following statement:</span></span>  
  
```  
SELECT FULLTEXTCATALOGPROPERTY('AdvWksDocFTCat', 'Populatestatus');  
```  
  
 <span data-ttu-id="3fc87-184">通常、カタログ全体の作成を実行している間は、結果として 1 が返されます。</span><span class="sxs-lookup"><span data-stu-id="3fc87-184">Typically, if a full population is in progress, the result returned is 1.</span></span>  
  
  
##  <a name="example-setting-up-full-text-search"></a><a name="example"></a><span data-ttu-id="3fc87-185">例: フルテキスト検索の設定</span><span class="sxs-lookup"><span data-stu-id="3fc87-185">Example: Setting Up Full-Text Search</span></span>  
 <span data-ttu-id="3fc87-186">次の 2 部構成の例では、AdventureWorks データベースに `AdvWksDocFTCat` という名前のフルテキスト カタログを作成し、次に、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] の `Document` テーブルにフルテキスト インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-186">The following two-part example creates a full-text catalog named `AdvWksDocFTCat` on the AdventureWorks database and then creates a full-text index on the `Document` table in [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span> <span data-ttu-id="3fc87-187">このステートメントによって、セットアップ時に指定した既定のディレクトリ内にフルテキスト カタログが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3fc87-187">This statement creates the full-text catalog in the default directory specified during setup.</span></span> <span data-ttu-id="3fc87-188">`AdvWksDocFTCat` というフォルダーが既定のディレクトリ内にあります。</span><span class="sxs-lookup"><span data-stu-id="3fc87-188">The folder named `AdvWksDocFTCat` is in the default directory.</span></span>  
  
1.  <span data-ttu-id="3fc87-189">`AdvWksDocFTCat`という名前のフルテキスト カタログを作成するために、この例では、 [CREATE FULLTEXT CATALOG](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-189">To create a full-text catalog named `AdvWksDocFTCat`, the example uses a [CREATE FULLTEXT CATALOG](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) statement:</span></span>  
  
    ```  
    USE AdventureWorks;  
    GO  
    CREATE FULLTEXT CATALOG AdvWksDocFTCat;  
    ```  
  
2.  <span data-ttu-id="3fc87-190">Document テーブルにフルテキスト インデックスを作成する前に、テーブルに一意の単一列で NULL 値にならないインデックスが含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-190">Before you can create a full-text index on the Document table, ensure that the table has a unique, single-column, non-nullable index.</span></span> <span data-ttu-id="3fc87-191">次の [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql) ステートメントでは、Document テーブルの DocumentID 列に、一意のインデックス `ui_ukDoc`を作成します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-191">The following [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql) statement creates a unique index, `ui_ukDoc`, on the DocumentID column of the Document table:</span></span>  
  
    ```  
    CREATE UNIQUE INDEX ui_ukDoc ON Production.Document(DocumentID);  
    ```  
  
3.  <span data-ttu-id="3fc87-192">一意のキーを作成したら、次の `Document` CREATE FULLTEXT INDEX [ステートメントを使用して、](/sql/t-sql/statements/create-fulltext-index-transact-sql) テーブルにフルテキスト インデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3fc87-192">After you have a unique key, you can create a full-text index on the `Document` table by using the following [CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) statement.</span></span>  
  
    ```  
    CREATE FULLTEXT INDEX ON Production.Document  
    (  
        Document                         --Full-text index column name   
            TYPE COLUMN FileExtension    --Name of column that contains file type information  
            Language 2057                 --2057 is the LCID for British English  
    )  
    KEY INDEX ui_ukDoc ON AdvWksDocFTCat --Unique index  
    WITH CHANGE_TRACKING AUTO            --Population type;  
    GO  
  
    ```  
  
     <span data-ttu-id="3fc87-193">この例で定義する TYPE COLUMN では、"Document" 列 (バイナリ型) の各行のドキュメント型が含まれる、テーブルの型列を指定します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-193">The TYPE COLUMN defined in this example specifies the type column in the table that contains the type of the document in each row of the column 'Document' (which is of binary type).</span></span> <span data-ttu-id="3fc87-194">Type 列には、ユーザーが指定したファイル拡張子 (".doc"、".xls" など) が、特定の行のドキュメントに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3fc87-194">The type column stores the user-supplied file extension-".doc", ".xls", and so on-of the document in a given row.</span></span> <span data-ttu-id="3fc87-195">Full-Text Engine では、特定の行のファイル拡張子を使用して、その行のデータを解析するために使用する正しいフィルターを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-195">The Full-Text Engine uses the file extension in a given row to invoke the correct filter to use for parsing the data in that row.</span></span> <span data-ttu-id="3fc87-196">その行のバイナリ データをフィルターが解析した後、指定されたワード ブレーカーがコンテンツを解析します (この例では、英語 (U.K.) のワード ブレーカーを使用します)。</span><span class="sxs-lookup"><span data-stu-id="3fc87-196">After the filter has parsed the binary data of the row, the specified word breaker will parse the content (in this example, the word breaker for British English is used).</span></span> <span data-ttu-id="3fc87-197">フィルター処理が行われるのは、インデックス作成時か、フルテキスト インデックスへの自動変更追跡が有効になっている場合にユーザーがベース テーブルで列を挿入または列を更新したときだけである点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="3fc87-197">Note that the filtering process happens only at indexing time or if a user inserts or updates a column in the base table while automatic change tracking is enabled for the full-text index.</span></span> <span data-ttu-id="3fc87-198">詳細については、「 [検索用フィルターの構成と管理](configure-and-manage-filters-for-search.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fc87-198">For more information, see [Configure and Manage Filters for Search](configure-and-manage-filters-for-search.md).</span></span>  
  
  
##  <a name="common-tasks"></a><a name="tasks"></a><span data-ttu-id="3fc87-199">一般的なタスク</span><span class="sxs-lookup"><span data-stu-id="3fc87-199">Common Tasks</span></span>  
  
### <a name="to-create-a-full-text-catalog"></a><span data-ttu-id="3fc87-200">フルテキスト カタログを作成するには</span><span class="sxs-lookup"><span data-stu-id="3fc87-200">To Create a Full-Text Catalog</span></span>  
  
-   [<span data-ttu-id="3fc87-201">CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3fc87-201">CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)  
  
-   [<span data-ttu-id="3fc87-202">フルテキスト カタログの作成と管理</span><span class="sxs-lookup"><span data-stu-id="3fc87-202">Create and Manage Full-Text Catalogs</span></span>](create-and-manage-full-text-catalogs.md)  
  
### <a name="to-view-the-indexes-of-a-table-or-view"></a><span data-ttu-id="3fc87-203">テーブル (またはビュー) のインデックスを表示するには</span><span class="sxs-lookup"><span data-stu-id="3fc87-203">To View the Indexes of a Table (or View)</span></span>  
  
-   [<span data-ttu-id="3fc87-204">sys.indexes &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3fc87-204">sys.indexes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)  
  
### <a name="to-create-a-unique-index"></a><span data-ttu-id="3fc87-205">一意のインデックスを作成するには</span><span class="sxs-lookup"><span data-stu-id="3fc87-205">To Create a Unique Index</span></span>  
  
-   [<span data-ttu-id="3fc87-206">CREATE INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3fc87-206">CREATE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
-   [<span data-ttu-id="3fc87-207">テーブル デザイナーを開く &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="3fc87-207">Open Table Designer &#40;Visual Database Tools&#41;</span></span>](../../ssms/visual-db-tools/visual-database-tools.md)  
  
### <a name="to-create-a-full-text-index"></a><span data-ttu-id="3fc87-208">フルテキスト インデックスを作成するには</span><span class="sxs-lookup"><span data-stu-id="3fc87-208">To Create a Full-Text Index</span></span>  
  
-   [<span data-ttu-id="3fc87-209">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3fc87-209">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-index-transact-sql)  
  
-   [<span data-ttu-id="3fc87-210">フルテキスト インデックスの作成と管理</span><span class="sxs-lookup"><span data-stu-id="3fc87-210">Create and Manage Full-Text Indexes</span></span>](create-and-manage-full-text-indexes.md)  
  
### <a name="to-view-information-about-a-full-text-index"></a><span data-ttu-id="3fc87-211">フルテキスト インデックスに関する情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="3fc87-211">To View Information about a Full-Text Index</span></span>  
  
|<span data-ttu-id="3fc87-212">カタログ ビューまたは動的管理ビュー</span><span class="sxs-lookup"><span data-stu-id="3fc87-212">Catalog or Dynamic Management View</span></span>|<span data-ttu-id="3fc87-213">説明</span><span class="sxs-lookup"><span data-stu-id="3fc87-213">Description</span></span>|  
|----------------------------------------|-----------------|  
|[<span data-ttu-id="3fc87-214">sys.fulltext_index_catalog_usages &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3fc87-214">sys.fulltext_index_catalog_usages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-catalog-usages-transact-sql)|<span data-ttu-id="3fc87-215">フルテキスト カタログからフルテキスト インデックスへの参照ごとに 1 行のデータを返します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-215">Returns a row for each full-text catalog to full-text index reference.</span></span>|  
|[<span data-ttu-id="3fc87-216">sys.fulltext_index_columns &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3fc87-216">sys.fulltext_index_columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)|<span data-ttu-id="3fc87-217">フルテキスト インデックスの一部となっている列ごとに 1 行のデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-217">Contains a row for each column that is part of a full-text index.</span></span>|  
|[<span data-ttu-id="3fc87-218">sys.fulltext_index_fragments &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3fc87-218">sys.fulltext_index_fragments &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-fragments-transact-sql)|<span data-ttu-id="3fc87-219">フルテキスト インデックスでは、フルテキスト インデックス フラグメントと呼ばれる内部テーブルを使用して逆インデックスのデータを保存します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-219">A fulltext index uses internal tables called full-text index fragments to store the inverted index data.</span></span> <span data-ttu-id="3fc87-220">このビューを使用すると、これらのフラグメントに関するメタデータをクエリできます。</span><span class="sxs-lookup"><span data-stu-id="3fc87-220">This view can be used to query the metadata about these fragments.</span></span> <span data-ttu-id="3fc87-221">このビューは、フルテキスト インデックスが含まれているすべてのテーブルのフルテキスト インデックス フラグメントごとに 1 行のデータを格納しています。</span><span class="sxs-lookup"><span data-stu-id="3fc87-221">This view contains a row for each full-text index fragment in every table that contains a full-text index.</span></span>|  
|[<span data-ttu-id="3fc87-222">sys.fulltext_indexes &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3fc87-222">sys.fulltext_indexes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql)|<span data-ttu-id="3fc87-223">表形式オブジェクトのフルテキスト インデックスごとに 1 行のデータを保持します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-223">Contains a row per full-text index of a tabular object.</span></span>|  
|[<span data-ttu-id="3fc87-224">sys.dm_fts_index_keywords &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3fc87-224">sys.dm_fts_index_keywords &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql)|<span data-ttu-id="3fc87-225">指定されたテーブルのフルテキスト インデックスのコンテンツに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-225">Returns information about the content of a full-text index for the specified table.</span></span>|  
|[<span data-ttu-id="3fc87-226">sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3fc87-226">sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql)|<span data-ttu-id="3fc87-227">指定されたテーブルについて、フルテキスト インデックスのドキュメント レベルのコンテンツに関連する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-227">Returns information about the document-level content of a full-text index for the specified table.</span></span> <span data-ttu-id="3fc87-228">個々のキーワードは、複数のドキュメントに出現する場合があります。</span><span class="sxs-lookup"><span data-stu-id="3fc87-228">A given keyword can appear in several documents.</span></span>|  
|[<span data-ttu-id="3fc87-229">sys.dm_fts_index_population &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3fc87-229">sys.dm_fts_index_population &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)|<span data-ttu-id="3fc87-230">現在実行中の、フルテキスト インデックス設定に関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="3fc87-230">Returns information about the full-text index populations currently in progress.</span></span>|  
  
  
## <a name="see-also"></a><span data-ttu-id="3fc87-231">参照</span><span class="sxs-lookup"><span data-stu-id="3fc87-231">See Also</span></span>  
 <span data-ttu-id="3fc87-232">[CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3fc87-232">[CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) </span></span>  
 <span data-ttu-id="3fc87-233">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3fc87-233">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span></span>  
 <span data-ttu-id="3fc87-234">[Transact-sql&#41;&#40;のフルテキストストップリストの作成](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3fc87-234">[CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span></span>  
 <span data-ttu-id="3fc87-235">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3fc87-235">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 <span data-ttu-id="3fc87-236">[フルテキスト インデックスの作成](populate-full-text-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="3fc87-236">[Populate Full-Text Indexes](populate-full-text-indexes.md) </span></span>  
 <span data-ttu-id="3fc87-237">[FULLTEXTCATALOGPROPERTY &#40;Transact-sql&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3fc87-237">[FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) </span></span>  
 [<span data-ttu-id="3fc87-238">OBJECTPROPERTYEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3fc87-238">OBJECTPROPERTYEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/objectproperty-transact-sql)  
  
  
