---
title: セマンティック検索 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server]
- semantic search [SQL Server], overview
- statistical semantic search [SQL Server]
- statistical semantic search [SQL Server], overview
ms.assetid: cd8faa9d-07db-420d-93f4-a2ea7c974b97
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 91062864b77ba3c62a87d66b8ff93068f9c10c8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719808"
---
# <a name="semantic-search-sql-server"></a><span data-ttu-id="e654c-102">セマンティック検索 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e654c-102">Semantic Search (SQL Server)</span></span>
  <span data-ttu-id="e654c-103">統計的セマンティック検索では、統計的に関連性がある [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] キー フレーズ *を抽出してインデックスを作成することにより、* データベースに格納されている非構造化ドキュメントを深く解釈することができます。</span><span class="sxs-lookup"><span data-stu-id="e654c-103">Statistical Semantic Search provides deep insight into unstructured documents stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases by extracting and indexing statistically relevant *key phrases*.</span></span> <span data-ttu-id="e654c-104">次に、これらのキー フレーズを使用して、 *類似または関連ドキュメント*を特定してインデックスを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="e654c-104">Then it also uses these key phrases to identify and index *documents that are similar or related*.</span></span>  
  
 <span data-ttu-id="e654c-105">3 つの Transact-SQL 行セット関数を使用することにより、これらのセマンティック インデックスに対してクエリを実行して、結果を構造化データとして取得することができます。</span><span class="sxs-lookup"><span data-stu-id="e654c-105">You query these semantic indexes by using three Transact-SQL rowset functions to retrieve the results as structured data.</span></span>  
  
##  <a name="what-can-i-do-with-semantic-search"></a><a name="whatcanido"></a><span data-ttu-id="e654c-106">セマンティック検索でできること</span><span class="sxs-lookup"><span data-stu-id="e654c-106">What Can I Do with Semantic Search?</span></span>  
 <span data-ttu-id="e654c-107">セマンティック検索は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の既存のフルテキスト検索機能を基にして構築されていますが、キーワード検索を超える新しいシナリオにも対応できます。</span><span class="sxs-lookup"><span data-stu-id="e654c-107">Semantic search builds upon the existing full-text search feature in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but enables new scenarios that extend beyond keyword searches.</span></span> <span data-ttu-id="e654c-108">フルテキスト検索ではドキュメントの *単語* に対してクエリを実行しますが、セマンティック検索ではドキュメントの *意味* に対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="e654c-108">While full-text search lets you query the *words* in a document, semantic search lets you query the *meaning* of the document.</span></span> <span data-ttu-id="e654c-109">これによって、自動タグ抽出、関連性のあるコンテンツの検出、類似コンテンツにまたがる階層的なナビゲーションなどのソリューションが可能になりました。</span><span class="sxs-lookup"><span data-stu-id="e654c-109">Solutions that are now possible include automatic tag extraction, related content discovery, and hierarchical navigation across similar content.</span></span> <span data-ttu-id="e654c-110">たとえば、キー フレーズのインデックスに対してクエリを実行して、ドキュメントの編成またはコーパスに関する分類を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="e654c-110">For example, you can query the index of key phrases to build the taxonomy for an organization, or for a corpus of documents.</span></span> <span data-ttu-id="e654c-111">また、ドキュメントの類似性のインデックスに対してクエリを実行して、ジョブの説明に一致するレジュメを特定できます。</span><span class="sxs-lookup"><span data-stu-id="e654c-111">Or, you can query the document similarity index to identify resumes that match a job description.</span></span>  
  
 <span data-ttu-id="e654c-112">以降の例に、セマンティック検索の機能を示します。</span><span class="sxs-lookup"><span data-stu-id="e654c-112">The following examples demonstrate the capabilities of Semantic Search.</span></span>  
  
###  <a name="find-the-key-phrases-in-a-document"></a><a name="find1"></a><span data-ttu-id="e654c-113">ドキュメント内のキーフレーズを検索する</span><span class="sxs-lookup"><span data-stu-id="e654c-113">Find the Key Phrases in a Document</span></span>  
 <span data-ttu-id="e654c-114">次のクエリは、サンプル ドキュメントで識別されたキー フレーズを取得します。</span><span class="sxs-lookup"><span data-stu-id="e654c-114">The following query gets the key phrases that were identified in the sample document.</span></span> <span data-ttu-id="e654c-115">結果は、各キー フレーズの統計的有意性を順位付けするスコアの降順で表されます。</span><span class="sxs-lookup"><span data-stu-id="e654c-115">It presents the results in descending order by the score that ranks the statistical significance of each key phrase.</span></span> <span data-ttu-id="e654c-116">このクエリは、[semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql) 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e654c-116">This query calls the [semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql) function.</span></span>  
  
```sql  
SET @Title = 'Sample Document.docx'  
  
SELECT @DocID = DocumentID  
    FROM Documents  
    WHERE DocumentTitle = @Title  
  
SELECT @Title AS Title, keyphrase, score  
    FROM SEMANTICKEYPHRASETABLE(Documents, *, @DocID)  
    ORDER BY score DESC  
  
```  
  
  
  
###  <a name="find-similar-or-related-documents"></a><a name="find2"></a><span data-ttu-id="e654c-117">類似または関連するドキュメントを検索する</span><span class="sxs-lookup"><span data-stu-id="e654c-117">Find Similar or Related Documents</span></span>  
 <span data-ttu-id="e654c-118">次のクエリは、サンプル ドキュメントに類似または関連すると識別されたドキュメントを取得します。</span><span class="sxs-lookup"><span data-stu-id="e654c-118">The following query gets the documents that were identified as similar or related to the sample document.</span></span> <span data-ttu-id="e654c-119">結果は、2 つのドキュメントの類似性を順位付けするスコアの降順で表されます。</span><span class="sxs-lookup"><span data-stu-id="e654c-119">It presents the results in descending order by the score that ranks the similarity of the 2 documents.</span></span> <span data-ttu-id="e654c-120">このクエリは、[semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql) 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e654c-120">This query calls the [semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql) function.</span></span>  
  
```vb  
SET @Title = 'Sample Document.docx'  
  
SELECT @DocID = DocumentID  
    FROM Documents  
    WHERE DocumentTitle = @Title  
  
SELECT @Title AS SourceTitle, DocumentTitle AS MatchedTitle,  
        DocumentID, score  
    FROM SEMANTICSIMILARITYTABLE(Documents, *, @DocID)  
    INNER JOIN Documents ON DocumentID = matched_document_key  
    ORDER BY score DESC  
  
```  
  
  
  
###  <a name="find-the-key-phrases-that-make-documents-similar-or-related"></a><a name="find3"></a><span data-ttu-id="e654c-121">ドキュメントが類似または関連していることを示すキーフレーズを見つける</span><span class="sxs-lookup"><span data-stu-id="e654c-121">Find the Key Phrases That Make Documents Similar or Related</span></span>  
 <span data-ttu-id="e654c-122">次のクエリは、2 つのサンプル ドキュメント間の類似性または関連性を示すキー フレーズを取得します。</span><span class="sxs-lookup"><span data-stu-id="e654c-122">The following query gets the key phrases that make the 2 sample documents similar or related to one another.</span></span> <span data-ttu-id="e654c-123">結果は、各キー フレーズの重みを順位付けするスコアの降順で表されます。</span><span class="sxs-lookup"><span data-stu-id="e654c-123">It presents the results in descending order by the score that ranks the weight of each key phrase.</span></span> <span data-ttu-id="e654c-124">このクエリは、[semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql) 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e654c-124">This query calls the [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql) function.</span></span>  
  
```sql  
SET @SourceTitle = 'first.docx'  
SET @MatchedTitle = 'second.docx'  
  
SELECT @SourceDocID = DocumentID FROM Documents WHERE DocumentTitle = @SourceTitle  
SELECT @MatchedDocID = DocumentID FROM Documents WHERE DocumentTitle = @MatchedTitle  
  
SELECT @SourceTitle AS SourceTitle, @MatchedTitle AS MatchedTitle, keyphrase, score  
    FROM semanticsimilaritydetailstable(Documents, DocumentContent,  
        @SourceDocID, DocumentContent, @MatchedDocID)  
    ORDER BY score DESC  
  
```  
  
  
  
##  <a name="storing-documents-in-sql-server"></a><a name="store"></a><span data-ttu-id="e654c-125">SQL Server にドキュメントを格納する</span><span class="sxs-lookup"><span data-stu-id="e654c-125">Storing Documents in SQL Server</span></span>  
 <span data-ttu-id="e654c-126">セマンティック検索でドキュメントのインデックスを作成する前に、ドキュメントを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e654c-126">Before you can index documents with Semantic Search, you have to store the documents in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="e654c-127">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の FileTable の機能との組み合わせにより、構造化されていないファイルやドキュメントを、リレーショナル データベースの最上位レベルのオブジェクトにすることができます。</span><span class="sxs-lookup"><span data-stu-id="e654c-127">The FileTable feature in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] makes unstructured files and documents first-class citizens of the relational database.</span></span> <span data-ttu-id="e654c-128">その結果、データベース開発者は、Transact-SQL セットベースの操作で構造化データと共にドキュメントを操作できます。</span><span class="sxs-lookup"><span data-stu-id="e654c-128">As a result, database developers can manipulate documents together with structured data in Transact-SQL set-based operations.</span></span>  
  
 <span data-ttu-id="e654c-129">FileTable 機能の詳細については、「[FileTables &#40;SQL Server&#41;](../blob/filetables-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e654c-129">For more information about the FileTable feature, see [FileTables &#40;SQL Server&#41;](../blob/filetables-sql-server.md).</span></span> <span data-ttu-id="e654c-130">データベースへのドキュメントの保存の別のオプションである FILESTREAM 機能の詳細については、「[FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e654c-130">For information about the FILESTREAM feature, which is another option for storing documents in the database, see [FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md).</span></span>  
  
  
  
##  <a name="related-tasks"></a><a name="reltasks"></a> <span data-ttu-id="e654c-131">関連タスク</span><span class="sxs-lookup"><span data-stu-id="e654c-131">Related Tasks</span></span>  
 [<span data-ttu-id="e654c-132">セマンティック検索のインストールと構成</span><span class="sxs-lookup"><span data-stu-id="e654c-132">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)  
 <span data-ttu-id="e654c-133">統計的セマンティック検索の前提条件と、これらをインストールまたは確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e654c-133">Describes the prerequisites for statistical semantic search and how to install or check them.</span></span>  
  
 [<span data-ttu-id="e654c-134">テーブルおよび列に対するセマンティック検索の有効化</span><span class="sxs-lookup"><span data-stu-id="e654c-134">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)  
 <span data-ttu-id="e654c-135">ドキュメントまたはテキストが格納されている選択した列に対して統計的セマンティック インデックス作成を有効または無効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e654c-135">Describes how to enable or disable statistical semantic indexing on selected columns that contain documents or text.</span></span>  
  
 [<span data-ttu-id="e654c-136">セマンティック検索を使用したドキュメント内のキー フレーズの検索</span><span class="sxs-lookup"><span data-stu-id="e654c-136">Find Key Phrases in Documents with Semantic Search</span></span>](find-key-phrases-in-documents-with-semantic-search.md)  
 <span data-ttu-id="e654c-137">統計的セマンティック インデックス作成用に構成されたドキュメントまたはテキスト列内のキー フレーズのクエリを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e654c-137">Describes how to find the key phrases in documents or text columns that are configured for statistical semantic indexing.</span></span>  
  
 [<span data-ttu-id="e654c-138">セマンティック検索による類似および関連したドキュメントの取得</span><span class="sxs-lookup"><span data-stu-id="e654c-138">Find Similar and Related Documents with Semantic Search</span></span>](find-similar-and-related-documents-with-semantic-search.md)  
 <span data-ttu-id="e654c-139">統計的セマンティック インデックス作成用に構成されている列での、類似性または関連性のあるドキュメントやテキスト値の検索方法と、どのように類似または関連しているかという情報の検索方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e654c-139">Describes how to find similar or related documents or text values, and information about how they are similar or related, in columns that are configured for statistical semantic indexing.</span></span>  
  
 [<span data-ttu-id="e654c-140">セマンティック検索の管理および監視</span><span class="sxs-lookup"><span data-stu-id="e654c-140">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)  
 <span data-ttu-id="e654c-141">セマンティック インデックス作成プロセスと、インデックスの監視および管理に関連するタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e654c-141">Describes the process of semantic indexing and the tasks related to monitoring and managing the indexes.</span></span>  
  
##  <a name="related-content"></a><a name="relcontent"></a> <span data-ttu-id="e654c-142">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="e654c-142">Related Content</span></span>  
 [<span data-ttu-id="e654c-143">セマンティック検索の DDL、関数、ストアド プロシージャ、およびビュー</span><span class="sxs-lookup"><span data-stu-id="e654c-143">Semantic Search DDL, Functions, Stored Procedures, and Views</span></span>](../views/views.md)  
 <span data-ttu-id="e654c-144">統計的セマンティック検索をサポートするために追加または変更された Transact-SQL ステートメントおよび SQL Server データベース オブジェクトの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="e654c-144">Lists the Transact-SQL statements and the SQL Server database objects added or changed to support statistical semantic search.</span></span>  
  
  
