---
title: セマンティック検索による類似および関連したドキュメントの取得 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], document similarity queries
ms.assetid: 9f527883-031b-442f-8e95-24bc0151ecbf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b11493b5b04fa9308e3afbe56176251225248338
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645478"
---
# <a name="find-similar-and-related-documents-with-semantic-search"></a><span data-ttu-id="1dc6a-102">セマンティック検索による類似および関連したドキュメントの取得</span><span class="sxs-lookup"><span data-stu-id="1dc6a-102">Find Similar and Related Documents with Semantic Search</span></span>
  <span data-ttu-id="1dc6a-103">統計的セマンティック インデックス作成用に構成されている列での、類似性または関連性のあるドキュメントやテキスト値の検索方法と、どのように類似または関連しているかという情報の検索方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1dc6a-103">Describes how to find similar or related documents or text values, and information about how they are similar or related, in columns that are configured for statistical semantic indexing.</span></span>  
  
##  <a name="finding-similar-or-related-documents"></a><a name="BasicsQuerySimilar"></a><span data-ttu-id="1dc6a-104">類似または関連するドキュメントの検索</span><span class="sxs-lookup"><span data-stu-id="1dc6a-104">Finding Similar or Related Documents</span></span>  
  
###  <a name="how-to-find-similar-or-related-documents-with-semanticsimilaritytable"></a><a name="HowToQuerySimilar"></a><span data-ttu-id="1dc6a-105">方法: SEMANTICSIMILARITYTABLE を使用して類似または関連するドキュメントを検索する</span><span class="sxs-lookup"><span data-stu-id="1dc6a-105">How To: Find Similar or Related Documents with SEMANTICSIMILARITYTABLE</span></span>  
 <span data-ttu-id="1dc6a-106">特定の列で類似または関連したドキュメントを識別するには、[semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql) 関数を使用してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="1dc6a-106">To identify similar or related documents in a specific column, query the function [semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql).</span></span>  
  
 <span data-ttu-id="1dc6a-107">**SEMANTICSIMILARITYTABLE** は、指定されたドキュメントに意味が似ているコンテンツを指定された列に持っている行 (0 行、1 行、または複数の行) から成るテーブルを返します。</span><span class="sxs-lookup"><span data-stu-id="1dc6a-107">**SEMANTICSIMILARITYTABLE** returns a table of zero, one, or more rows whose content in the specified column is semantically similar to the specified document.</span></span> <span data-ttu-id="1dc6a-108">この行セット関数は、標準のテーブル名のように、SELECT ステートメントの FROM 句で参照できます。</span><span class="sxs-lookup"><span data-stu-id="1dc6a-108">This rowset function can be referenced in the FROM clause of a SELECT statement like a regular table name.</span></span>  
  
 <span data-ttu-id="1dc6a-109">複数の列にわたって類似したドキュメントに対するクエリを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="1dc6a-109">You cannot query across columns for similar documents.</span></span> <span data-ttu-id="1dc6a-110">**SEMANTICSIMILARITYTABLE** 関数は、 **source_key** 引数によって識別されるソース列と同じ列からのみ結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="1dc6a-110">The **SEMANTICSIMILARITYTABLE** function only retrieves results from the same column as the source column, which is identified by the **source_key** argument.</span></span>  
  
 <span data-ttu-id="1dc6a-111">**SEMANTICSIMILARITYTABLE** 関数に必要なパラメーターの詳細や関数から返される結果のテーブルについては、「[semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1dc6a-111">For detailed information about the parameters required by the **SEMANTICSIMILARITYTABLE** function, and about the table of results that it returns, see [semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1dc6a-112">対象の列では、フルテキスト インデックスとセマンティック インデックスが有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1dc6a-112">The columns that you target must have full-text and semantic indexing enabled.</span></span>  
  
###  <a name="example-find-the-top-documents-that-are-similar-to-another-document"></a><a name="HowToIdentifySimilar"></a><span data-ttu-id="1dc6a-113">例: 別のドキュメントに類似している上位のドキュメントを検索する</span><span class="sxs-lookup"><span data-stu-id="1dc6a-113">Example: Find the Top Documents That Are Similar to Another Document</span></span>  
 <span data-ttu-id="1dc6a-114">次の例では、 *@CandidateID* AdventureWorks2012 サンプルデータベースの humanresources.employee テーブルから、によって指定された候補に類似する上位10の候補を取得します。</span><span class="sxs-lookup"><span data-stu-id="1dc6a-114">The following example retrieves the top 10 candidates who are similar to the candidate specified by *@CandidateID* from the HumanResources.JobCandidate table in the AdventureWorks2012 sample database.</span></span>  
  
```scr  
SELECT TOP(10) KEY_TBL.matched_document_key AS Candidate_ID  
FROM SEMANTICSIMILARITYTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume,  
    @CandidateID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
GO  
```  
  
##  <a name="finding-information-about-how-documents-are-similar-or-related"></a><a name="BasicsQuerySimilarity"></a><span data-ttu-id="1dc6a-115">ドキュメントが類似または関連しているかどうかに関する情報の検索</span><span class="sxs-lookup"><span data-stu-id="1dc6a-115">Finding Information about How Documents Are Similar or Related</span></span>  
  
###  <a name="how-to-find-information-about-how-documents-are-similar-or-related-with-semanticsimilaritydetailstable"></a><a name="HowToQuerySimilarity"></a><span data-ttu-id="1dc6a-116">方法: ドキュメントが類似しているか、SEMANTICSIMILARITYDETAILSTABLE と関連付けられているかに関する情報を検索する</span><span class="sxs-lookup"><span data-stu-id="1dc6a-116">How To: Find Information about How Documents Are Similar or Related with SEMANTICSIMILARITYDETAILSTABLE</span></span>  
 <span data-ttu-id="1dc6a-117">ドキュメントが類似または関連する原因となっているキー フレーズに関する情報を表示するには、[semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql) 関数を使用してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="1dc6a-117">To get information about the key phrases that make documents similar or related, you can query the function [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql).</span></span>  
  
 <span data-ttu-id="1dc6a-118">**SEMANTICSIMILARITYDETAILSTABLE** は、意味が似たコンテンツを持つ 2 つのドキュメント (ソース ドキュメントと一致するドキュメント) に共通するキー フレーズの 0 行、1 行、または複数の行から成るテーブルを返します。</span><span class="sxs-lookup"><span data-stu-id="1dc6a-118">**SEMANTICSIMILARITYDETAILSTABLE** returns a table of zero, one, or more rows of key phrases common across two documents (a source document and a matched document) whose content is semantically similar.</span></span> <span data-ttu-id="1dc6a-119">この行セット関数は、標準のテーブル名のように、SELECT ステートメントの FROM 句で参照できます。</span><span class="sxs-lookup"><span data-stu-id="1dc6a-119">This rowset function can be referenced in the FROM clause of a SELECT statement like a regular table name.</span></span>  
  
 <span data-ttu-id="1dc6a-120">**SEMANTICSIMILARITYDETAILTABLE** 関数に必要なパラメーターの詳細や関数から返される結果のテーブルについては、「[semanticsimilaritydetailtable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1dc6a-120">For detailed information about the parameters required by the **SEMANTICSIMILARITYDETAILSTABLE** function, and about the table of results that it returns, see [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1dc6a-121">対象の列では、フルテキスト インデックスとセマンティック インデックスが有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1dc6a-121">The columns that you target must have full-text and semantic indexing enabled.</span></span>  
  
###  <a name="example-find-the-top-key-phrases-that-are-similar-between-documents"></a><a name="HowToSimilarPhrases"></a><span data-ttu-id="1dc6a-122">例: ドキュメント間で類似している上位のキーフレーズを検索する</span><span class="sxs-lookup"><span data-stu-id="1dc6a-122">Example: Find the Top Key Phrases That Are Similar between Documents</span></span>  
 <span data-ttu-id="1dc6a-123">次の例では、AdventureWorks2012 サンプル データベースの **HumanResources.JobCandidate** テーブル内の指定された候補間で最も類似スコアが高い 5 つのキー フレーズを取得します。</span><span class="sxs-lookup"><span data-stu-id="1dc6a-123">The following example retrieves the 5 key phrases that have the highest similarity score between the specified candidates in **HumanResources.JobCandidate** table of the AdventureWorks2012 sample database.</span></span>  
  
```sql  
SELECT TOP(5) KEY_TBL.keyphrase, KEY_TBL.score  
FROM SEMANTICSIMILARITYDETAILSTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume, @CandidateID,  
    Resume, @MatchedID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
GO  
```  
  
  
