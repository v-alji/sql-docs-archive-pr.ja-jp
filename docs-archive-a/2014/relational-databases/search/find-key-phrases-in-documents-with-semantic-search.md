---
title: セマンティック検索を使用したドキュメント内のキー フレーズの検索 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], key phrase queries
ms.assetid: 6ee3676e-ed5d-43ec-aeca-1eed78967111
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8388fb704bf13f44d025e6e32a1450d537f61832
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714130"
---
# <a name="find-key-phrases-in-documents-with-semantic-search"></a><span data-ttu-id="cf133-102">セマンティック検索を使用したドキュメント内のキー フレーズの検索</span><span class="sxs-lookup"><span data-stu-id="cf133-102">Find Key Phrases in Documents with Semantic Search</span></span>
  <span data-ttu-id="cf133-103">統計的セマンティック インデックス作成用に構成されたドキュメントまたはテキスト列内のキー フレーズのクエリを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cf133-103">Describes how to find the key phrases in documents or text columns that are configured for statistical semantic indexing.</span></span>  
  
##  <a name="finding-key-phrases-in-documents"></a><a name="BasicsQueryKey"></a><span data-ttu-id="cf133-104">検索 (ドキュメント内のキーフレーズを)</span><span class="sxs-lookup"><span data-stu-id="cf133-104">Finding Key Phrases in Documents</span></span>  
  
###  <a name="how-to-find-the-key-phrases-in-documents-with-semantickeyphrasetable"></a><a name="howtofind"></a><span data-ttu-id="cf133-105">方法: SEMANTICKEYPHRASETABLE を使用してドキュメント内のキーフレーズを検索する</span><span class="sxs-lookup"><span data-stu-id="cf133-105">How to: Find the Key Phrases in Documents with SEMANTICKEYPHRASETABLE</span></span>  
 <span data-ttu-id="cf133-106">特定のドキュメントに含まれるキー フレーズや特定のキー フレーズを含むドキュメントを識別するには、[semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql) 関数を使用してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="cf133-106">To identify the key phrases in specific documents, or to identify documents that contain specific key phrases, query the function [semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql).</span></span>  
  
 <span data-ttu-id="cf133-107">SEMANTICKEYPHRASETABLE は、指定されたテーブル内の列に関連付けられているこれらのキー フレーズに対し、0 行以上の行を含むテーブルを返します。</span><span class="sxs-lookup"><span data-stu-id="cf133-107">SEMANTICKEYPHRASETABLE returns a table with zero, one, or more rows for those key phrases associated with columns in the specified table.</span></span> <span data-ttu-id="cf133-108">この行セット関数は、標準のテーブル名のように、SELECT ステートメントの FROM 句で参照できます。</span><span class="sxs-lookup"><span data-stu-id="cf133-108">This rowset function can be referenced in the FROM clause of a SELECT statement as if it were a regular table name.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cf133-109">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]では、セマンティック検索のためにインデックスが作成されるのは 1 つの単語のみです。複数の単語で構成されるフレーズ (ngrams) のインデックスは作成されません。</span><span class="sxs-lookup"><span data-stu-id="cf133-109">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], only single words are indexed for semantic search; multi-word phrases (ngrams) are not indexed.</span></span> <span data-ttu-id="cf133-110">また、1 つの単語のさまざまな形式は個別にインデックスが付けられます。たとえば、「computer」と「computers」は個別にインデックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="cf133-110">Also, various forms of the same word are indexed separately; for example, "computer" and "computers" are indexed separately.</span></span>  
  
 <span data-ttu-id="cf133-111">SEMANTICKEYPHRASETABLE 関数に必要なパラメーターの詳細や関数から返される結果のテーブルについては、[semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql) のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf133-111">For detailed information about the parameters required by the SEMANTICKEYPHRASETABLE function, and about the table of results that it returns, see [semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cf133-112">対象の列では、フルテキスト インデックスとセマンティック インデックスが有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf133-112">The columns that you target must have full-text and semantic indexing enabled.</span></span>  
  
###  <a name="example-1-find-the-top-key-phrases-in-a-specific-document"></a><a name="HowToTopPhrases"></a><span data-ttu-id="cf133-113">例 1: 特定のドキュメントに含まれる上位のキーフレーズを検索する</span><span class="sxs-lookup"><span data-stu-id="cf133-113">Example 1: Find the Top Key Phrases in a Specific Document</span></span>  
 <span data-ttu-id="cf133-114">次の例では、AdventureWorks サンプル データベースの Production.Document テーブルの Document 列にある、@DocumentId 変数で指定されたドキュメントから、上位 10 個のキー フレーズを取得します。</span><span class="sxs-lookup"><span data-stu-id="cf133-114">The following example retrieves the top 10 key phrases from the document specified by the @DocumentId variable in the Document column of the Production.Document table of the AdventureWorks sample database.</span></span> <span data-ttu-id="cf133-115">@DocumentId 変数は、フルテキスト インデックスのキー列の値を表します。</span><span class="sxs-lookup"><span data-stu-id="cf133-115">The @DocumentId variable represents a value from the key column of the full-text index.</span></span>  
  
```sql  
SELECT TOP(10) KEYP_TBL.keyphrase  
FROM SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document,  
    @DocumentId  
    ) AS KEYP_TBL  
ORDER BY KEYP_TBL.score DESC;  
GO  
```  
  
 <span data-ttu-id="cf133-116">**SEMANTICKEYPHRASETABLE** 関数は、テーブル スキャンではなくインデックス シークを使用してこれらの結果を効率的に取得します。</span><span class="sxs-lookup"><span data-stu-id="cf133-116">The **SEMANTICKEYPHRASETABLE** function retrieves these results efficiently by using an index seek instead of a table scan.</span></span>  
  
###  <a name="example-2-find-the-top-documents-that-contain-a-specific-key-phrase"></a><a name="HowToTopDocuments"></a><span data-ttu-id="cf133-117">例 2: 特定のキーフレーズを含む上位のドキュメントを検索する</span><span class="sxs-lookup"><span data-stu-id="cf133-117">Example 2: Find the Top Documents that Contain a Specific Key Phrase</span></span>  
 <span data-ttu-id="cf133-118">次の例では、AdventureWorks サンプル データベースの Production.Document テーブルの Document 列から、キー フレーズ "Bracket" を含む上位 25 個のドキュメントを取得します。</span><span class="sxs-lookup"><span data-stu-id="cf133-118">The following example retrieves the top 25 documents that contain the key phrase "Bracket" from the Document column of the Production.Document table of the AdventureWorks sample database.</span></span>  
  
```sql  
SELECT TOP (25) DOC_TBL.DocumentID, DOC_TBL.DocumentSummary  
FROM Production.Document AS DOC_TBL  
    INNER JOIN SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document  
    ) AS KEYP_TBL  
ON DOC_TBL.DocumentID = KEYP_TBL.document_key  
WHERE KEYP_TBL.keyphrase = 'Bracket'  
ORDER BY KEYP_TBL.Score DESC;  
GO  
```  
  
  
