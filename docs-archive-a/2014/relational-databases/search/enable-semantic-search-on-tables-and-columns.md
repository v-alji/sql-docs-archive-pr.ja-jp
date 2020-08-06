---
title: テーブルおよび列に対するセマンティック検索の有効化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], enabling
ms.assetid: 895d220c-6749-4954-9dd3-2ea4c6a321ff
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f11ba654f7cc34f521990e8c420d41885d3c55b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717756"
---
# <a name="enable-semantic-search-on-tables-and-columns"></a><span data-ttu-id="1703f-102">テーブルおよび列に対するセマンティック検索の有効化</span><span class="sxs-lookup"><span data-stu-id="1703f-102">Enable Semantic Search on Tables and Columns</span></span>
  <span data-ttu-id="1703f-103">ドキュメントまたはテキストが格納されている選択した列に対して統計的セマンティック インデックス作成を有効または無効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1703f-103">Describes how to enable or disable statistical semantic indexing on selected columns that contain documents or text.</span></span>  
  
 <span data-ttu-id="1703f-104">統計的セマンティック検索では、フルテキスト検索によって作成されたインデックスを使用し、追加のインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1703f-104">Statistical Semantic Search uses the indexes that are created by Full-Text Search, and creates additional indexes.</span></span> <span data-ttu-id="1703f-105">このフルテキスト検索に対する依存関係があるため、新しいフルテキスト インデックスの定義や既存のフルテキスト インデックスの変更の際には、新しいセマンティック インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1703f-105">As a result of this dependency on full-text search, you create a new semantic index when you define a new full-text index, or when you alter an existing full-text index.</span></span> <span data-ttu-id="1703f-106">新しいセマンティック インデックスを作成するには、このトピックで説明するように、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用するか、または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のフルテキスト インデックス作成ウィザードおよびその他のダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="1703f-106">You can create a new semantic index by using [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, or by using the Full-Text Indexing Wizard and other dialog boxes in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], as described in this topic.</span></span>  
  
##  <a name="creating-a-semantic-index"></a><a name="BasicEnabling"></a><span data-ttu-id="1703f-107">セマンティックインデックスの作成</span><span class="sxs-lookup"><span data-stu-id="1703f-107">Creating a Semantic Index</span></span>  
  
###  <a name="requirements-and-restrictions-for-creating-a-semantic-index"></a><a name="reqenable"></a><span data-ttu-id="1703f-108">セマンティックインデックスを作成するための要件と制限</span><span class="sxs-lookup"><span data-stu-id="1703f-108">Requirements and Restrictions for Creating a Semantic Index</span></span>  
  
-   <span data-ttu-id="1703f-109">インデックスは、フルテキスト インデックス作成でサポートされる、テーブルおよびインデックス付きビューを含むいずれかのデータベース オブジェクトに作成できます。</span><span class="sxs-lookup"><span data-stu-id="1703f-109">You can create an index on any of the database objects that are supported for full-text indexing, including tables and indexed views.</span></span>  
  
-   <span data-ttu-id="1703f-110">特定の列のセマンティック インデックス作成を有効にするには、次の前提条件が満たされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1703f-110">Before you can enable semantic indexing for specific columns, the following prerequisites must exist:</span></span>  
  
    -   <span data-ttu-id="1703f-111">データベースのフルテキスト カタログが存在する。</span><span class="sxs-lookup"><span data-stu-id="1703f-111">A full-text catalog must exist for the database.</span></span>  
  
    -   <span data-ttu-id="1703f-112">テーブルにフルテキスト インデックスがある。</span><span class="sxs-lookup"><span data-stu-id="1703f-112">The table must have a full-text index.</span></span>  
  
    -   <span data-ttu-id="1703f-113">選択された列がフルテキスト インデックスに含まれている。</span><span class="sxs-lookup"><span data-stu-id="1703f-113">The selected columns must participate in the full-text index.</span></span>  
  
     <span data-ttu-id="1703f-114">これらのすべての要件は、同時に作成および有効化することができます。</span><span class="sxs-lookup"><span data-stu-id="1703f-114">You can create and enable all these requirements at the same time.</span></span>  
  
-   <span data-ttu-id="1703f-115">セマンティック インデックスは、フルテキスト インデックス作成でサポートされるいずれかのデータ型の列に作成できます。</span><span class="sxs-lookup"><span data-stu-id="1703f-115">You can create a semantic index on columns that have any of the data types that are supported for full-text indexing.</span></span> <span data-ttu-id="1703f-116">詳細については、「 [フルテキスト インデックスの作成と管理](create-and-manage-full-text-indexes.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1703f-116">For more information, see [Create and Manage Full-Text Indexes](create-and-manage-full-text-indexes.md).</span></span>  
  
-   <span data-ttu-id="1703f-117">`varbinary(max)` 列のフルテキスト インデックス作成でサポートされるいずれかのドキュメントの種類を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1703f-117">You can specify any document type that is supported for full-text indexing for `varbinary(max)` columns.</span></span> <span data-ttu-id="1703f-118">詳細については、このトピックの「 [方法: どのドキュメントの種類でインデックス作成ができるかを判断する](#doctypes) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1703f-118">For more information, see [How To: Determine Which Document Types Can Be Indexed](#doctypes) in this topic.</span></span>  
  
-   <span data-ttu-id="1703f-119">セマンティック インデックス作成では、選択した列に対し、キー フレーズのインデックスとドキュメントの類似性のインデックスの 2 種類のインデックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1703f-119">Semantic indexing creates two types of indexes for the columns that you select - an index of key phrases, and an index of document similarity.</span></span> <span data-ttu-id="1703f-120">セマンティック インデックス作成を有効にするときに 1 種類のインデックスだけを選択することはできません。</span><span class="sxs-lookup"><span data-stu-id="1703f-120">You cannot select only one type of index or the other when you enable semantic indexing.</span></span> <span data-ttu-id="1703f-121">ただし、これらの 2 つのインデックスに対するクエリは別々に実行できます。</span><span class="sxs-lookup"><span data-stu-id="1703f-121">However you can query these two indexes independently.</span></span> <span data-ttu-id="1703f-122">詳細については、「 [セマンティック検索を使用したドキュメント内のキー フレーズの検索](find-key-phrases-in-documents-with-semantic-search.md) 」および「 [セマンティック検索による類似および関連したドキュメントの検索](find-similar-and-related-documents-with-semantic-search.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1703f-122">For more information, see [Find Key Phrases in Documents with Semantic Search](find-key-phrases-in-documents-with-semantic-search.md) and [Find Similar and Related Documents with Semantic Search](find-similar-and-related-documents-with-semantic-search.md).</span></span>  
  
-   <span data-ttu-id="1703f-123">セマンティック インデックスの LCID を明示的に指定しない場合、セマンティック インデックス作成には主言語とそれに関連する言語統計のみが使用されます。</span><span class="sxs-lookup"><span data-stu-id="1703f-123">If you do not explicitly specify an LCID for a semantic index, then only the primary language and its associated language statistics are used for semantic indexing.</span></span>  
  
-   <span data-ttu-id="1703f-124">言語モデルを使用できない列に対して言語を指定した場合、インデックスの作成は失敗し、エラー メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="1703f-124">If you specify a language for a column for which the language model is not available, the creation of the index fails and returns an error message.</span></span>  
  
###  <a name="how-to-create-a-semantic-index-when-there-is-no-full-text-index"></a><a name="HowToEnableCreate"></a><span data-ttu-id="1703f-125">方法: フルテキストインデックスがない場合にセマンティックインデックスを作成する</span><span class="sxs-lookup"><span data-stu-id="1703f-125">How To: Create a Semantic Index When There Is No Full-Text Index</span></span>  
 <span data-ttu-id="1703f-126">**CREATE FULLTEXT INDEX** ステートメントを使用して新しいフルテキスト インデックスを作成する場合、列定義の一部としてキーワード **STATISTICAL_SEMANTICS** を指定すると、列レベルでのセマンティック インデックス作成を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="1703f-126">When you create a new full-text index with the **CREATE FULLTEXT INDEX** statement, you can enable semantic indexing at the column level by specifying the keyword **STATISTICAL_SEMANTICS** as part of the column definition.</span></span> <span data-ttu-id="1703f-127">また、フルテキスト インデックス作成ウィザードを使用して新しいフルテキスト インデックスを作成するときにセマンティック インデックス作成を有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="1703f-127">You can also enable semantic indexing when you use the Full-Text Indexing Wizard to create a new full-text index.</span></span>  
  
 <span data-ttu-id="1703f-128">**Transact-SQL を使用して新しいセマンティック インデックスを作成する**</span><span class="sxs-lookup"><span data-stu-id="1703f-128">**Create a new semantic index by using Transact-SQL**</span></span>  
 <span data-ttu-id="1703f-129">**CREATE FULLTEXT INDEX** ステートメントを呼び出し、セマンティック インデックスを作成するそれぞれの列に対して **STATISTICAL_SEMANTICS** を指定します。</span><span class="sxs-lookup"><span data-stu-id="1703f-129">Call the **CREATE FULLTEXT INDEX** statement and specify **STATISTICAL_SEMANTICS** for each column on which you want to create a semantic index.</span></span> <span data-ttu-id="1703f-130">このステートメントのすべてのオプションの詳細については、「[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1703f-130">For more information about all the options for this statement, see [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql).</span></span>  
  
 <span data-ttu-id="1703f-131">**例 1: 一意のインデックス、フルテキスト インデックス、およびセマンティック インデックスを作成する**</span><span class="sxs-lookup"><span data-stu-id="1703f-131">**Example 1: Create a unique index, full-text index, and semantic index**</span></span>  
  
 <span data-ttu-id="1703f-132">次の例では、既定のフルテキスト カタログ、 **ft**を作成します。次に、AdventureWorks2012 サンプル データベースの **HumanResources.JobCandidate** テーブルの **JobCandidateID** 列に一意のインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1703f-132">The following example creates a default full-text catalog, **ft**. The example then creates a unique index on the **JobCandidateID** column of the **HumanResources.JobCandidate** table of the AdventureWorks2012 sample database.</span></span> <span data-ttu-id="1703f-133">この一意のインデックスは、フルテキスト インデックスのキー列として必要です。</span><span class="sxs-lookup"><span data-stu-id="1703f-133">This unique index is required as the key column for a full-text index.</span></span> <span data-ttu-id="1703f-134">次に、 **Resume** 列にフルテキスト インデックスとセマンティック インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1703f-134">The example then creates a full-text index and a semantic index on the **Resume** column.</span></span>  
  
```sql  
CREATE FULLTEXT CATALOG ft AS DEFAULT  
GO  
  
CREATE UNIQUE INDEX ui_ukJobCand  
    ON HumanResources.JobCandidate(JobCandidateID)  
GO  
  
CREATE FULLTEXT INDEX ON HumanResources.JobCandidate  
    (Resume  
        Language 1033  
        Statistical_Semantics  
    )   
    KEY INDEX JobCandidateID   
    WITH STOPLIST = SYSTEM  
GO  
```  
  
 <span data-ttu-id="1703f-135">**例 2: インデックスの作成を遅延させて、いくつかの列でフルテキスト インデックスとセマンティック インデックスを作成する**</span><span class="sxs-lookup"><span data-stu-id="1703f-135">**Example 2: Create a full-text and semantic index on several columns with delayed index population**</span></span>  
  
 <span data-ttu-id="1703f-136">次の例では、AdventureWorks2012 サンプル データベースにフルテキスト カタログ **documents_catalog**を作成します。</span><span class="sxs-lookup"><span data-stu-id="1703f-136">The following example creates a full-text catalog, **documents_catalog**, in the AdventureWorks2012 sample database.</span></span> <span data-ttu-id="1703f-137">その後、この新しいカタログを使用するフルテキスト インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1703f-137">The example then creates a full-text index that uses this new catalog.</span></span> <span data-ttu-id="1703f-138">フルテキスト インデックスは、 **Production.Document**テーブルの **Title**、 **DocumentSummary** 、 **Document** の各列に作成します。セマンティック インデックスは、 **Document** 列にのみ作成します。</span><span class="sxs-lookup"><span data-stu-id="1703f-138">The full-text index is created on the **Title**, **DocumentSummary**, and **Document** columns of the **Production.Document** table, while the semantic index is only created on the **Document** column.</span></span> <span data-ttu-id="1703f-139">このフルテキスト インデックスは、新たに作成されたフルテキスト カタログおよび既存の一意なキー インデックス、 **PK_Document_DocumentID**を使用します。</span><span class="sxs-lookup"><span data-stu-id="1703f-139">This full-text index uses the newly-created full-text catalog and an existing unique key index, **PK_Document_DocumentID**.</span></span> <span data-ttu-id="1703f-140">推奨されているように、このインデックス キーは整数列、 **DocumentID**に作成されます。</span><span class="sxs-lookup"><span data-stu-id="1703f-140">As recommended, this index key is created on an integer column, **DocumentID**.</span></span> <span data-ttu-id="1703f-141">この例では、列のデータの言語である英語の LCID、1033 を指定します。</span><span class="sxs-lookup"><span data-stu-id="1703f-141">The example specifies the LCID for English, 1033, which is the language of the data in the columns.</span></span>  
  
 <span data-ttu-id="1703f-142">さらに、この例では、変更の追跡が OFF で、NO POPULATION を指定しています。</span><span class="sxs-lookup"><span data-stu-id="1703f-142">This example also specifies that change tracking is off with no population.</span></span> <span data-ttu-id="1703f-143">代わりに、 **ALTER FULLTEXT INDEX** ステートメントを指定して、後のピーク タイム以外の時間に新しいインデックスの完全作成を開始し、自動変更追跡を有効にしています。</span><span class="sxs-lookup"><span data-stu-id="1703f-143">Later, during off-peak hours, the example uses an **ALTER FULLTEXT INDEX** statement to start a full population on the new index and enable automatic change tracking.</span></span>  
  
```sql  
CREATE FULLTEXT CATALOG documents_catalog  
GO  
  
CREATE FULLTEXT INDEX ON Production.Document  
    (   
    Title  
        Language 1033,   
    DocumentSummary  
        Language 1033,   
    Document   
        TYPE COLUMN FileExtension  
        Language 1033  
        Statistical_Semantics  
    )  
    KEY INDEX PK_Document_DocumentID  
        ON documents_catalog  
        WITH CHANGE_TRACKING OFF, NO POPULATION  
GO  
```  
  
 <span data-ttu-id="1703f-144">後のピーク タイム以外の時間にインデックスを作成</span><span class="sxs-lookup"><span data-stu-id="1703f-144">Later, at an off-peak time, the index is populated:</span></span>  
  
```sql  
ALTER FULLTEXT INDEX ON Production.Document SET CHANGE_TRACKING AUTO  
GO  
```  
  
 <span data-ttu-id="1703f-145">**SQL Server Management Studio を使用して新しいセマンティック インデックスを作成する**</span><span class="sxs-lookup"><span data-stu-id="1703f-145">**Create a new semantic index by using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="1703f-146">フルテキスト インデックス作成ウィザードを実行し、セマンティック インデックスを作成するそれぞれの列に対し **[テーブル列の選択]** ページで **[統計的セマンティクス]** を有効にします。</span><span class="sxs-lookup"><span data-stu-id="1703f-146">Run the Full-Text Indexing Wizard and enable **Statistical Semantics** on the **Select Table Columns** page for each column on which you want to create a semantic index.</span></span> <span data-ttu-id="1703f-147">フルテキスト インデックス作成ウィザードの起動方法などの詳細については、「 [フルテキスト インデックス作成ウィザードの使用](use-the-full-text-indexing-wizard.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1703f-147">For more information, including information about how to start the Full-Text Indexing Wizard, see [Use the Full-Text Indexing Wizard](use-the-full-text-indexing-wizard.md).</span></span>  
  
###  <a name="how-to-create-a-semantic-index-when-there-is-an-existing-full-text-index"></a><a name="HowToEnableAlter"></a><span data-ttu-id="1703f-148">方法: 既存のフルテキストインデックスがある場合にセマンティックインデックスを作成する</span><span class="sxs-lookup"><span data-stu-id="1703f-148">How To: Create a Semantic Index When There Is an Existing Full-Text Index</span></span>  
 <span data-ttu-id="1703f-149">**ALTER FULLTEXT INDEX** ステートメントを使用して既存のフルテキスト インデックスを変更するとき、セマンティック インデックス作成を追加できます。</span><span class="sxs-lookup"><span data-stu-id="1703f-149">You can add semantic indexing when you alter an existing full-text index with the **ALTER FULLTEXT INDEX** statement.</span></span> <span data-ttu-id="1703f-150">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のさまざまなダイアログ ボックスを使用して、セマンティック インデックス作成を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="1703f-150">You can also add semantic indexing by using various dialog boxes in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="1703f-151">**Transact-SQL を使用してセマンティック インデックスを追加する**</span><span class="sxs-lookup"><span data-stu-id="1703f-151">**Add a semantic index by using Transact-SQL**</span></span>  
 <span data-ttu-id="1703f-152">セマンティック インデックスを追加するそれぞれの列に対し、次に示すオプションを指定して **ALTER FULLTEXT INDEX** ステートメントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1703f-152">Call the **ALTER FULLTEXT INDEX** statement with the options described below for each column on which you want to add a semantic index.</span></span> <span data-ttu-id="1703f-153">このステートメントのすべてのオプションの詳細については、「[ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1703f-153">For more information about all the options for this statement, see [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).</span></span>  
  
 <span data-ttu-id="1703f-154">特に指定しない限り、フルテキスト インデックスとセマンティック インデックスのどちらも **ALTER** 呼び出しの後に再作成されます。</span><span class="sxs-lookup"><span data-stu-id="1703f-154">Both full-text and semantic indexes are repopulated after a call to **ALTER**, unless you specify otherwise.</span></span>  
  
-   <span data-ttu-id="1703f-155">フルテキスト インデックス作成のみを列に追加するには、 **ADD** 構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="1703f-155">To add full-text indexing only to a column, use the **ADD** syntax.</span></span>  
  
-   <span data-ttu-id="1703f-156">フルテキスト インデックス作成とセマンティック インデックス作成の両方を列に追加するには、 **STATISTICAL_SEMANTICS** オプションを指定した **ADD** 構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="1703f-156">To add both full-text and semantic indexing to a column, use the **ADD** syntax with the **STATISTICAL_SEMANTICS** option.</span></span>  
  
-   <span data-ttu-id="1703f-157">フルテキスト インデックス作成が既に有効になっている列にセマンティック インデックス作成を追加するには、 **ADD STATISTICAL_SEMANTICS** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="1703f-157">To add semantic indexing to a column that is already enabled for full-text indexing, use the **ADD STATISTICAL_SEMANTICS** option.</span></span> <span data-ttu-id="1703f-158">1 つの **ALTER** ステートメントでは 1 つの列にのみセマンティック インデックス作成を追加できます。</span><span class="sxs-lookup"><span data-stu-id="1703f-158">You can only add semantic indexing to one column in a single **ALTER** statement.</span></span>  
  
 <span data-ttu-id="1703f-159">**例: フルテキスト インデックス作成が既に存在する列にセマンティック インデックス作成を追加する**</span><span class="sxs-lookup"><span data-stu-id="1703f-159">**Example: Add semantic indexing to a column that already has full-text indexing**</span></span>  
  
 <span data-ttu-id="1703f-160">次の例では、AdventureWorks2012 サンプル データベースの **Production.Document** テーブルの既存のフルテキスト インデックスを変更します。</span><span class="sxs-lookup"><span data-stu-id="1703f-160">The following example alters an existing full-text index on **Production.Document** table in AdventureWorks2012 sample database.</span></span> <span data-ttu-id="1703f-161">この例では、フルテキスト インデックスが既に存在している **Production.Document** テーブルの **Document** 列にセマンティック インデックスを追加します。</span><span class="sxs-lookup"><span data-stu-id="1703f-161">The example adds a semantic index on the **Document** column of the **Production.Document** table, which already has a full-text index.</span></span> <span data-ttu-id="1703f-162">この例では、インデックスが自動的に再作成されないように指定します。</span><span class="sxs-lookup"><span data-stu-id="1703f-162">The example specifies that the index will not be repopulated automatically.</span></span>  
  
```sql  
ALTER FULLTEXT INDEX ON Production.Document  
    ALTER COLUMN Document  
        ADD Statistical_Semantics  
    WITH NO POPULATION  
GO  
```  
  
 <span data-ttu-id="1703f-163">**SQL Server Management Studio を使用してセマンティック インデックスを追加する**</span><span class="sxs-lookup"><span data-stu-id="1703f-163">**Add a semantic index by using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="1703f-164">**[フルテキスト インデックスのプロパティ]** ダイアログ ボックスの **[フルテキスト インデックスの列]** ページで、セマンティック インデックス作成とフルテキスト インデックス作成が有効な列を変更できます。</span><span class="sxs-lookup"><span data-stu-id="1703f-164">You can change the columns that are enabled for semantic and full-text indexing on the **Full-Text Index Columns** page of the **Full-Text Index Properties** dialog box.</span></span> <span data-ttu-id="1703f-165">詳細については、「 [フルテキスト インデックスの管理](../../database-engine/manage-full-text-indexes.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1703f-165">For more information, see [Manage Full-Text Indexes](../../database-engine/manage-full-text-indexes.md).</span></span>  
  
###  <a name="requirements-and-restrictions-for-altering-an-existing-index"></a><a name="addreq"></a><span data-ttu-id="1703f-166">既存のインデックスを変更するための要件と制限</span><span class="sxs-lookup"><span data-stu-id="1703f-166">Requirements and Restrictions for Altering an Existing Index</span></span>  
  
-   <span data-ttu-id="1703f-167">インデックスの作成の進行中は既存のインデックスを変更できません。</span><span class="sxs-lookup"><span data-stu-id="1703f-167">You cannot alter an existing index while population of the index is in progress.</span></span> <span data-ttu-id="1703f-168">インデックスの作成の進行状況を監視する方法の詳細については、「 [セマンティクス検索の管理および監視](manage-and-monitor-semantic-search.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1703f-168">For more information on monitoring the progress of index population, see [Manage and Monitor Semantic Search](manage-and-monitor-semantic-search.md).</span></span>  
  
-   <span data-ttu-id="1703f-169">インデックス作成を列に追加する操作とこの列のインデックス作成を変更または削除する操作を **ALTER FULLTEXT INDEX** ステートメントの 1 回の呼び出しで行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="1703f-169">You cannot add indexing to a column, and alter or drop indexing for the same column, in a single call to the **ALTER FULLTEXT INDEX** statement.</span></span>  
  
##  <a name="dropping-a-semantic-index"></a><a name="dropping"></a><span data-ttu-id="1703f-170">セマンティックインデックスの削除</span><span class="sxs-lookup"><span data-stu-id="1703f-170">Dropping a Semantic Index</span></span>  
  
###  <a name="how-to-drop-a-semantic-index"></a><a name="drophow"></a><span data-ttu-id="1703f-171">方法: セマンティックインデックスを削除する</span><span class="sxs-lookup"><span data-stu-id="1703f-171">How to: Drop a Semantic Index</span></span>  
 <span data-ttu-id="1703f-172">**ALTER FULLTEXT INDEX** ステートメントを使用して既存のフルテキスト インデックスを変更するとき、セマンティック インデックス作成を削除できます。</span><span class="sxs-lookup"><span data-stu-id="1703f-172">You can drop semantic indexing when you alter an existing full-text index with the **ALTER FULLTEXT INDEX** statement.</span></span> <span data-ttu-id="1703f-173">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のさまざまなダイアログ ボックスを使用して、セマンティック インデックス作成を削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="1703f-173">You can also drop semantic indexing by using various dialog boxes in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="1703f-174">**Transact-SQL を使用してセマンティック インデックスを削除する**</span><span class="sxs-lookup"><span data-stu-id="1703f-174">**Drop a semantic index by using Transact-SQL**</span></span>  
 -   <span data-ttu-id="1703f-175">1 つまたは複数の列からセマンティック インデックス作成だけを削除するには、 **ALTER COLUMN** column_name **DROP STATISTICAL_SEMANTICS\*\*\*オプションを指定して、**\* ALTER FULLTEXT INDEX\*\* ステートメントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1703f-175">To drop semantic indexing only from a column or columns, call the **ALTER FULLTEXT INDEX** statement with the **ALTER COLUMN***column_name***DROP STATISTICAL_SEMANTICS** option.</span></span> <span data-ttu-id="1703f-176">1 つの **ALTER** ステートメントを使用して複数の列からインデックス作成を削除できます。</span><span class="sxs-lookup"><span data-stu-id="1703f-176">You can drop the indexing from multiple columns in a single **ALTER** statement.</span></span>  
  
    ```sql  
    USE database_name  
    GO  
  
    ALTER FULLTEXT INDEX  
        ALTER COLUMN column_name  
        DROP STATISTICAL_SEMANTICS  
    GO  
    ```  
  
-   <span data-ttu-id="1703f-177">列からフルテキストインデックス作成とセマンティックインデックス作成の両方を削除するには、alter **column***column_name***drop**オプションを指定して**alter フルテキストインデックス**ステートメントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1703f-177">To drop both full-text and semantic indexing from a column, call the **ALTER FULLTEXT INDEX** statement with the **ALTER COLUMN***column_name***DROP** option.</span></span>  
  
    ```sql  
    USE database_name  
    GO  
  
    ALTER FULLTEXT INDEX  
        ALTER COLUMN column_name  
        DROP  
    GO  
    ```  
  
 <span data-ttu-id="1703f-178">**SQL Server Management Studio を使用してセマンティック インデックスを削除する**</span><span class="sxs-lookup"><span data-stu-id="1703f-178">**Drop a semantic index by using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="1703f-179">**[フルテキスト インデックスのプロパティ]** ダイアログ ボックスの **[フルテキスト インデックスの列]** ページで、セマンティック インデックス作成とフルテキスト インデックス作成が有効な列を変更できます。</span><span class="sxs-lookup"><span data-stu-id="1703f-179">You can change the columns that are enabled for semantic and full-text indexing on the **Full-Text Index Columns** page of the **Full-Text Index Properties** dialog box.</span></span> <span data-ttu-id="1703f-180">詳細については、「 [フルテキスト インデックスの管理](../../database-engine/manage-full-text-indexes.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1703f-180">For more information, see [Manage Full-Text Indexes](../../database-engine/manage-full-text-indexes.md).</span></span>  
  
###  <a name="requirements-and-restrictions-for-dropping-a-semantic-index"></a><a name="dropreq"></a><span data-ttu-id="1703f-181">セマンティックインデックスを削除するための要件と制限</span><span class="sxs-lookup"><span data-stu-id="1703f-181">Requirements and Restrictions for Dropping a Semantic Index</span></span>  
  
-   <span data-ttu-id="1703f-182">セマンティック インデックス作成を保持しているときに列からフルテキスト インデックス作成を削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="1703f-182">You cannot drop full-text indexing from a column while retaining semantic indexing.</span></span> <span data-ttu-id="1703f-183">セマンティック インデックス作成は、ドキュメントの類似性の結果に関してフルテキスト インデックス作成に依存します。</span><span class="sxs-lookup"><span data-stu-id="1703f-183">Semantic indexing depends on full-text indexing for document similarity results.</span></span>  
  
-   <span data-ttu-id="1703f-184">セマンティック インデックス作成が有効になっていたテーブルの最後の列からセマンティック インデックス作成を削除するときは、 **NO POPULATION** オプションを指定できません。</span><span class="sxs-lookup"><span data-stu-id="1703f-184">You cannot specify the **NO POPULATION** option when you drop semantic indexing from the last column in a table for which semantic indexing was enabled.</span></span> <span data-ttu-id="1703f-185">以前にインデックスが作成された結果を削除するには、インデックス作成サイクルが必要になります。</span><span class="sxs-lookup"><span data-stu-id="1703f-185">A population cycle is required to remove the results that were indexed previously.</span></span>  
  
## <a name="checking-whether-semantic-search-is-enabled-on-database-objects"></a><span data-ttu-id="1703f-186">データベース オブジェクトでセマンティック検索が有効かどうかの確認</span><span class="sxs-lookup"><span data-stu-id="1703f-186">Checking Whether Semantic Search Is Enabled on Database Objects</span></span>  
  
###  <a name="how-to-check-whether-semantic-search-is-enabled-on-database-objects"></a><a name="HowToCheckEnabled"></a><span data-ttu-id="1703f-187">方法: データベースオブジェクトでセマンティック検索が有効になっているかどうかを確認する</span><span class="sxs-lookup"><span data-stu-id="1703f-187">How To: Check Whether Semantic Search Is Enabled on Database Objects</span></span>  
 <span data-ttu-id="1703f-188">**データベースに対してセマンティック検索が有効化されていますか?**</span><span class="sxs-lookup"><span data-stu-id="1703f-188">**Is semantic search enabled for a database?**</span></span>  
 <span data-ttu-id="1703f-189">[DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) メタデータ関数の **IsFullTextEnabled** プロパティのクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="1703f-189">Query the **IsFullTextEnabled** property of the [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) metadata function.</span></span>  
  
 <span data-ttu-id="1703f-190">戻り値 1 は、データベースに対してフルテキスト検索とセマンティック検索が有効化されていることを示します。戻り値 0 は、フルテキスト検索とセマンティック検索が有効化されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="1703f-190">A return value of 1 indicates that full-text search and semantic search are enabled for the database; a return value of 0 indicates that they are not enabled.</span></span>  
  
```sql  
SELECT DATABASEPROPERTYEX('database_name', 'IsFullTextEnabled')  
GO  
```  
  
 <span data-ttu-id="1703f-191">**テーブルに対してセマンティック検索が有効化されていますか?**</span><span class="sxs-lookup"><span data-stu-id="1703f-191">**Is semantic search enabled for a table?**</span></span>  
 <span data-ttu-id="1703f-192">[OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql) メタデータ関数の **TableFullTextSemanticExtraction** プロパティのクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="1703f-192">Query the **TableFullTextSemanticExtraction** property of the [OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql) metadata function.</span></span>  
  
 <span data-ttu-id="1703f-193">戻り値 1 は、テーブルに対してセマンティック検索が有効化されていることを示します。戻り値 0 は、セマンティック検索が有効化されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="1703f-193">A return value of 1 indicates that semantic search is enabled for the table; a return value of 0 indicates that it is not enabled.</span></span>  
  
```scr  
SELECT OBJECTPROPERTYEX(OBJECT_ID('table_name'), 'TableFullTextSemanticExtraction')  
GO  
```  
  
 <span data-ttu-id="1703f-194">**列に対してセマンティック検索が有効化されていますか?**</span><span class="sxs-lookup"><span data-stu-id="1703f-194">**Is semantic search enabled for a column?**</span></span>  
 <span data-ttu-id="1703f-195">特定の列に対して統計的セマンティック検索が有効化されているかどうかを確認するには、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="1703f-195">To determine whether semantic search is enabled for a specific column:</span></span>  
  
-   <span data-ttu-id="1703f-196">[COLUMNPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/columnproperty-transact-sql) メタデータ関数の **StatisticalSemantics** プロパティのクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="1703f-196">Query the **StatisticalSemantics** property of the [COLUMNPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/columnproperty-transact-sql) metadata function.</span></span>  
  
     <span data-ttu-id="1703f-197">戻り値 1 は、列に対してセマンティック検索が有効化されていることを示します。戻り値 0 は、セマンティック検索が有効化されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="1703f-197">A return value of 1 indicates that semantic search is enabled for the column; a return value of 0 indicates that it is not enabled.</span></span>  
  
    ```sql  
    SELECT COLUMNPROPERTY(OBJECT_ID('table_name'), 'column_name', 'StatisticalSemantics')  
    GO  
    ```  
  
-   <span data-ttu-id="1703f-198">フルテキスト インデックスのカタログ ビュー [sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql) のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="1703f-198">Query the catalog view [sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql) for the full-text index.</span></span>  
  
     <span data-ttu-id="1703f-199">**statistical_semantics** 列の値 1 は、指定された列に対してフルテキスト インデックス作成とセマンティック インデックス作成が有効になっていることを示します。</span><span class="sxs-lookup"><span data-stu-id="1703f-199">A value of 1 in the **statistical_semantics** column indicates that the specified column is enabled for semantic indexing in addition to full-text indexing.</span></span>  
  
    ```sql  
    SELECT * FROM sys.fulltext_index_columns WHERE object_id = OBJECT_ID('table_name')  
    GO  
    ```  
  
-   <span data-ttu-id="1703f-200">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]のオブジェクト エクスプローラーで、列を右クリックし、 **[プロパティ]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="1703f-200">In Object Explorer in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], right-click on a column and select **Properties**.</span></span> <span data-ttu-id="1703f-201">**[列のプロパティ]** ダイアログ ボックスの **[全般]** ページで、 **[統計的セマンティクス]** プロパティの値を確認します。</span><span class="sxs-lookup"><span data-stu-id="1703f-201">On the **General** page of the **Column Properties** dialog box, check the value of the **Statistical Semantics** property.</span></span>  
  
     <span data-ttu-id="1703f-202">値 True は、指定された列に対してフルテキスト インデックス作成とセマンティック インデックス作成が有効になっていることを示します。</span><span class="sxs-lookup"><span data-stu-id="1703f-202">A value of True indicates that the specified column is enabled for semantic indexing in addition to full-text indexing.</span></span>  
  
## <a name="determining-what-can-be-indexed-for-semantic-search"></a><span data-ttu-id="1703f-203">セマンティック検索用にインデックスを作成できる対象の確認</span><span class="sxs-lookup"><span data-stu-id="1703f-203">Determining What Can Be Indexed for Semantic Search</span></span>  
  
###  <a name="how-to-check-which-languages-are-supported-for-semantic-search"></a><a name="HowToCheckLanguages"></a><span data-ttu-id="1703f-204">方法: セマンティック検索でサポートされている言語を確認する</span><span class="sxs-lookup"><span data-stu-id="1703f-204">How To: Check Which Languages Are Supported for Semantic Search</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1703f-205">セマンティック インデックス作成は、フルテキスト インデックス作成ほどサポートされている言語が多くありません。</span><span class="sxs-lookup"><span data-stu-id="1703f-205">Fewer languages are supported for semantic indexing than for full-text indexing.</span></span> <span data-ttu-id="1703f-206">このため、フルテキスト検索用にインデックスを作成できる一方でセマンティック検索用にはインデックスを作成できない列が存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="1703f-206">As a result, there may be columns that you can index for full-text search, but not for semantic search.</span></span>  
  
 <span data-ttu-id="1703f-207">カタログ ビュー [sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql) のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="1703f-207">Query the catalog view [sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql).</span></span>  
  
```sql  
SELECT * FROM sys.fulltext_semantic_languages  
GO  
```  
  
 <span data-ttu-id="1703f-208">セマンティック インデックス作成でサポートされている言語は以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1703f-208">The following languages are supported for semantic indexing.</span></span> <span data-ttu-id="1703f-209">この一覧は、LCID の順に並べ替えたカタログ ビュー [sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql) の出力を表します。</span><span class="sxs-lookup"><span data-stu-id="1703f-209">This list represents the output of the catalog view [sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql), ordered by LCID.</span></span>  
  
|<span data-ttu-id="1703f-210">Language</span><span class="sxs-lookup"><span data-stu-id="1703f-210">Language</span></span>|<span data-ttu-id="1703f-211">LCID</span><span class="sxs-lookup"><span data-stu-id="1703f-211">LCID</span></span>|  
|--------------|----------|  
|<span data-ttu-id="1703f-212">ドイツ語</span><span class="sxs-lookup"><span data-stu-id="1703f-212">German</span></span>|<span data-ttu-id="1703f-213">1031</span><span class="sxs-lookup"><span data-stu-id="1703f-213">1031</span></span>|  
|<span data-ttu-id="1703f-214">英語 (米国)</span><span class="sxs-lookup"><span data-stu-id="1703f-214">English (US)</span></span>|<span data-ttu-id="1703f-215">1033</span><span class="sxs-lookup"><span data-stu-id="1703f-215">1033</span></span>|  
|<span data-ttu-id="1703f-216">フランス語</span><span class="sxs-lookup"><span data-stu-id="1703f-216">French</span></span>|<span data-ttu-id="1703f-217">1036</span><span class="sxs-lookup"><span data-stu-id="1703f-217">1036</span></span>|  
|<span data-ttu-id="1703f-218">イタリア語</span><span class="sxs-lookup"><span data-stu-id="1703f-218">Italian</span></span>|<span data-ttu-id="1703f-219">1040</span><span class="sxs-lookup"><span data-stu-id="1703f-219">1040</span></span>|  
|<span data-ttu-id="1703f-220">ポルトガル語 (ブラジル)</span><span class="sxs-lookup"><span data-stu-id="1703f-220">Portuguese (Brazil)</span></span>|<span data-ttu-id="1703f-221">1046</span><span class="sxs-lookup"><span data-stu-id="1703f-221">1046</span></span>|  
|<span data-ttu-id="1703f-222">ロシア語</span><span class="sxs-lookup"><span data-stu-id="1703f-222">Russian</span></span>|<span data-ttu-id="1703f-223">1049</span><span class="sxs-lookup"><span data-stu-id="1703f-223">1049</span></span>|  
|<span data-ttu-id="1703f-224">スウェーデン語</span><span class="sxs-lookup"><span data-stu-id="1703f-224">Swedish</span></span>|<span data-ttu-id="1703f-225">1053</span><span class="sxs-lookup"><span data-stu-id="1703f-225">1053</span></span>|  
|<span data-ttu-id="1703f-226">英語 (英国)</span><span class="sxs-lookup"><span data-stu-id="1703f-226">English (UK)</span></span>|<span data-ttu-id="1703f-227">2057</span><span class="sxs-lookup"><span data-stu-id="1703f-227">2057</span></span>|  
|<span data-ttu-id="1703f-228">ポルトガル語 (ポルトガル)</span><span class="sxs-lookup"><span data-stu-id="1703f-228">Portuguese (Portugal)</span></span>|<span data-ttu-id="1703f-229">2070</span><span class="sxs-lookup"><span data-stu-id="1703f-229">2070</span></span>|  
|<span data-ttu-id="1703f-230">スペイン語</span><span class="sxs-lookup"><span data-stu-id="1703f-230">Spanish</span></span>|<span data-ttu-id="1703f-231">3082</span><span class="sxs-lookup"><span data-stu-id="1703f-231">3082</span></span>|  
  
###  <a name="how-to-determine-which-document-types-can-be-indexed"></a><a name="doctypes"></a><span data-ttu-id="1703f-232">方法: インデックスを作成できるドキュメントの種類を確認する</span><span class="sxs-lookup"><span data-stu-id="1703f-232">How To: Determine Which Document Types Can Be Indexed</span></span>  
 <span data-ttu-id="1703f-233">カタログ ビュー [sys.fulltext_document_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="1703f-233">Query the catalog view [sys.fulltext_document_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql).</span></span>  
  
 <span data-ttu-id="1703f-234">インデックスの対象とするドキュメントの種類が、サポートされている種類の一覧に含まれていない場合は、追加のフィルターを探してダウンロードし、インストールしなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="1703f-234">If the document type that you want to index is not in the list of supported types, then you may have to locate, download, and install additional filters.</span></span> <span data-ttu-id="1703f-235">詳細については、「 [登録済みのフィルターおよびワード ブレーカーの表示または変更](view-or-change-registered-filters-and-word-breakers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1703f-235">For more information, see [View or Change Registered Filters and Word Breakers](view-or-change-registered-filters-and-word-breakers.md).</span></span>  
  
##  <a name="best-practice-consider-creating-a-separate-filegroup-for-the-full-text-and-semantic-indexes"></a><a name="BestPracticeFilegroup"></a><span data-ttu-id="1703f-236">ベストプラクティス: フルテキストインデックスとセマンティックインデックス用に別のファイルグループを作成することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="1703f-236">Best Practice: Consider Creating a Separate Filegroup for the Full-Text and Semantic Indexes</span></span>  
 <span data-ttu-id="1703f-237">ディスク領域の割り当てが問題となる場合は、フルテキスト インデックスとセマンティック インデックスに対して別個のファイル グループを作成することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="1703f-237">Consider creating a separate filegroup for the full-text and semantic indexes if disk space allocation is a concern.</span></span> <span data-ttu-id="1703f-238">セマンティック インデックスは、フルテキスト インデックスと同じファイル グループに作成されます。</span><span class="sxs-lookup"><span data-stu-id="1703f-238">The semantic indexes are created in the same filegroup as the full-text index.</span></span> <span data-ttu-id="1703f-239">完全に作成されたセマンティック インデックスには大量のデータが含まれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1703f-239">A fully populated semantic index may contain large amount of data.</span></span>  
  
##  <a name="BestPracticeUnderstand"></a>   
##  <a name="problem-searching-on-specific-column-returns-no-results"></a><a name="IssueNoResults"></a><span data-ttu-id="1703f-240">問題点: 特定の列を検索すると結果が返されない</span><span class="sxs-lookup"><span data-stu-id="1703f-240">Problem: Searching on Specific Column Returns No Results</span></span>  
 <span data-ttu-id="1703f-241">**Unicode 以外の LCID が Unicode 言語に指定されていませんか。**</span><span class="sxs-lookup"><span data-stu-id="1703f-241">**Was a non-Unicode LCID specified for a Unicode language?**</span></span>  
 <span data-ttu-id="1703f-242">Unicode の語のみを含む言語の LCID (たとえば、ロシア語の LCID 1049) を持つ非 Unicode 列型に対してセマンティック インデックス作成を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="1703f-242">It is possible to enable semantic indexing on a non-Unicode column type with an LCID for a language that only has Unicode words, such as LCID 1049 for Russian.</span></span> <span data-ttu-id="1703f-243">この場合、この列のセマンティック インデックスから結果が返されることはありません。</span><span class="sxs-lookup"><span data-stu-id="1703f-243">In this case, no results will ever be returned from the semantic indexes on this column.</span></span>  
  
  
