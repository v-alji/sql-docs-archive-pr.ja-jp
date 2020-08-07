---
title: NEAR による他の単語の近くにある単語の検索 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- word searches [full-text search]
- NEAR option [full-text search]
- phrase searches [full-text search]
- proximity searches [full-text search]
- full-text search [SQL Server], proximity searches
- full-text queries [SQL Server], proximity
- queries [full-text search], proximity
ms.assetid: 87520646-4865-49ae-8790-f766b80a41f3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8c2d187ea3ed951ac6f17eb4babc5f4f77451d4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719820"
---
# <a name="search-for-words-close-to-another-word-with-near"></a><span data-ttu-id="1a16f-102">NEAR による他の単語の近くにある単語の検索</span><span class="sxs-lookup"><span data-stu-id="1a16f-102">Search for Words Close to Another Word with NEAR</span></span>
  <span data-ttu-id="1a16f-103">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) 述語または [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 関数で近接語句 (NEAR) を使用すると、互いに似た単語や語句を検索できます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-103">You can use a proximity term (NEAR) in a [CONTAINS](/sql/t-sql/queries/contains-transact-sql) predicate or [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) function to search for words or phrases near one another.</span></span> <span data-ttu-id="1a16f-104">最初の検索語句と最後の検索語句を分離する非検索用語の最大数を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-104">You can also specify the maximum number of non-search terms that separate the first and last search terms.</span></span> <span data-ttu-id="1a16f-105">さらに、任意の順序で語や句を検索したり、指定した順序で語や句を検索したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-105">In addition, you can search for words or phrases in any order, or you can search for words and phrases in the order in which you specify them.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="1a16f-106">では、以前の[汎用近接語句](#Generic_NEAR)(現在は非推奨) と[カスタム近接語句](#Custom_NEAR)(の新機能) の両方がサポートされてい [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-106">supports both the earlier [generic proximity term](#Generic_NEAR), which is now deprecated, and the [custom proximity term](#Custom_NEAR), which is new in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span>  
  
##  <a name="the-custom-proximity-term"></a><a name="Custom_NEAR"></a><span data-ttu-id="1a16f-107">カスタム近接語句</span><span class="sxs-lookup"><span data-stu-id="1a16f-107">The Custom Proximity Term</span></span>  
 <span data-ttu-id="1a16f-108">カスタム近接語句では、次のような新しい機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-108">The custom proximity term introduces the following new capabilities:</span></span>  
  
-   <span data-ttu-id="1a16f-109">一致する順序で、最初と最後の検索語句を分離する非検索用語の最大数 ( *最大距離*) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-109">You can specify the maximum number of non-search terms, or *maximum distance*, that separates the first and last search terms in order to constitute a match.</span></span>  
  
-   <span data-ttu-id="1a16f-110">語句の最大数を指定する場合、検索語句が特定の順序で一致するように指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-110">If you specify the maximum number of terms, you can also specify that matches must contain the search terms in the specified order.</span></span>  
  
 <span data-ttu-id="1a16f-111">一致と見なされるには、文字列が次の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a16f-111">To qualify as a match, a string of text must:</span></span>  
  
-   <span data-ttu-id="1a16f-112">指定した検索語句のいずれかで始まり、他の指定した検索語句のいずれかで終わる。</span><span class="sxs-lookup"><span data-stu-id="1a16f-112">Start with one of the specified search terms and end with the one of the other specified search terms.</span></span>  
  
-   <span data-ttu-id="1a16f-113">指定したすべての検索語句を含む。</span><span class="sxs-lookup"><span data-stu-id="1a16f-113">Contain all of the specified search terms.</span></span>  
  
-   <span data-ttu-id="1a16f-114">ストップワードなど、最初の検索語句と最後の検索語句の間にある非検索用語の数は、最大距離以下である必要がある (指定した場合)。</span><span class="sxs-lookup"><span data-stu-id="1a16f-114">The number of non-search terms, including stopwords, that occur between the first and last search terms must be less than or equal to the maximum distance, if specified.</span></span>  
  
 <span data-ttu-id="1a16f-115">基本構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1a16f-115">The basic syntax is:</span></span>  
  
 <span data-ttu-id="1a16f-116">NEAR (</span><span class="sxs-lookup"><span data-stu-id="1a16f-116">NEAR (</span></span>  
  
 <span data-ttu-id="1a16f-117">{</span><span class="sxs-lookup"><span data-stu-id="1a16f-117">{</span></span>  
  
 <span data-ttu-id="1a16f-118">*search_term* [,...*n* ]</span><span class="sxs-lookup"><span data-stu-id="1a16f-118">*search_term* [ ,...*n* ]</span></span>  
  
 |  
  
 <span data-ttu-id="1a16f-119">(*search_term* [,...*n* ]) [、<maximum_distance> [、<match_order>]]</span><span class="sxs-lookup"><span data-stu-id="1a16f-119">(*search_term* [ ,...*n* ] ) [, <maximum_distance> [, <match_order> ] ]</span></span>  
  
 <span data-ttu-id="1a16f-120">}</span><span class="sxs-lookup"><span data-stu-id="1a16f-120">}</span></span>  
  
 <span data-ttu-id="1a16f-121">)</span><span class="sxs-lookup"><span data-stu-id="1a16f-121">)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1a16f-122"><custom_proximity_term> 構文の詳細については、「[CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a16f-122">For more information about the <custom_proximity_term> syntax, see [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql).</span></span>  
  
 <span data-ttu-id="1a16f-123">たとえば、次のように "Smith" から 2 つの語の範囲内にある "John" を検索できます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-123">For example, you could search for 'John' within two terms of 'Smith', as follows:</span></span>  
  
```  
CONTAINS(column_name, 'NEAR((John, Smith), 2)')  
```  
  
 <span data-ttu-id="1a16f-124">一致する文字列の例としては、"`John Jacob Smith`" や "`Smith, John`" などがあります。</span><span class="sxs-lookup"><span data-stu-id="1a16f-124">Some examples of strings that match are "`John Jacob Smith`" and "`Smith, John`".</span></span> <span data-ttu-id="1a16f-125">文字列"`John Jones knows Fred Smith`" は 3 つの非検索語句が間にあるので一致しません。</span><span class="sxs-lookup"><span data-stu-id="1a16f-125">The string "`John Jones knows Fred Smith`" contains three intervening non-search terms, so it is not a match.</span></span>  
  
 <span data-ttu-id="1a16f-126">指定した順序で語句を検索する必要がある場合は、例の近接語句を `NEAR((John, Smith),2, TRUE).` に変更します。これにより、"`John`" が "`Smith`" の前にある場合のみ、"`John`" から 2 語の範囲内にある "`Smith`" が検索されます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-126">To require that the terms be found in the specified order, you would change the example proximity term to `NEAR((John, Smith),2, TRUE).` This searches for "`John`" within two terms of "`Smith`" but only when "`John`" precedes "`Smith`".</span></span> <span data-ttu-id="1a16f-127">英語など、左から右に読む言語では、"`John Jacob Smith`" が一致する文字列です。</span><span class="sxs-lookup"><span data-stu-id="1a16f-127">In a language that reads from left to right, such as English, an example of a string that matches is "`John Jacob Smith`".</span></span>  
  
 <span data-ttu-id="1a16f-128">アラビア語、ヘブライ語など、右から左に読む言語では、フルテキスト エンジンは、指定した言語に逆の順序で適用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1a16f-128">Note that for a language that reads from right to left, such as Arabic or Hebrew, the Full-Text Engine applies the specified terms in reverse order.</span></span> <span data-ttu-id="1a16f-129">また、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のオブジェクト エクスプローラーは、右から左に読む言語では指定した語句の表示順序を自動的に逆にします。</span><span class="sxs-lookup"><span data-stu-id="1a16f-129">Also, Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] automatically reverses the display order of words specified in right-to-left languages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1a16f-130">詳細については、後の「[近接検索に関するその他の注意点](#Additional_Considerations)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a16f-130">For more information, see "[Additional Considerations about Proximity Searches](#Additional_Considerations)," later in this topic.</span></span>  
  
### <a name="how-maximum-distance-is-measured"></a><span data-ttu-id="1a16f-131">最大距離の測定方法</span><span class="sxs-lookup"><span data-stu-id="1a16f-131">How Maximum Distance Is Measured</span></span>  
 <span data-ttu-id="1a16f-132">10 や 25 など特定の最大距離を指定すると、指定した文字列の最初の検索語句と最後の検索語句の間にある、ストップワードなどの非検索語句の数が決定されます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-132">A specific maximum distance, such as 10 or 25, determines how many non-search terms, including stopwords, can occur between the first and last search terms in a given string.</span></span> <span data-ttu-id="1a16f-133">たとえば、 `NEAR((dogs, cats, "hunting mice"), 3)` は次の行を返します。ここでは、非検索語句の数は 3 つ ("`enjoy`"、"`but`"、および "`avoid`") です。</span><span class="sxs-lookup"><span data-stu-id="1a16f-133">For example, `NEAR((dogs, cats, "hunting mice"), 3)` would return the following row, in which the total number of non-search terms is three ("`enjoy`", "`but`", and "`avoid`"):</span></span>  
  
 <span data-ttu-id="1a16f-134">"`Cats` `enjoy` `hunting mice``, but avoid` `dogs``.`"</span><span class="sxs-lookup"><span data-stu-id="1a16f-134">"`Cats` `enjoy` `hunting mice``, but avoid` `dogs``.`"</span></span>  
  
 <span data-ttu-id="1a16f-135">同じ近接語句でも次の行は返しません。非検索語句が 4つ ("`enjoy`"、"`but`"、"`usually`"、および "`avoid`") であるため最大距離を超えているからです。</span><span class="sxs-lookup"><span data-stu-id="1a16f-135">The same proximity term would not return the following row, because the maximum distance is exceeded by the four non-search terms ("`enjoy`", "`but`", "`usually`", and "`avoid`"):</span></span>  
  
 <span data-ttu-id="1a16f-136">"`Cats` `enjoy` `hunting mice``, but usually avoid` `dogs``.`"</span><span class="sxs-lookup"><span data-stu-id="1a16f-136">"`Cats` `enjoy` `hunting mice``, but usually avoid` `dogs``.`"</span></span>  
  
### <a name="combining-a-custom-proximity-term-with-other-terms"></a><span data-ttu-id="1a16f-137">カスタム近接語句とその他の語句との組み合わせ</span><span class="sxs-lookup"><span data-stu-id="1a16f-137">Combining a Custom Proximity Term with Other Terms</span></span>  
 <span data-ttu-id="1a16f-138">カスタム近接語句とその他の語句とを組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-138">You can combine a custom proximity term with some other terms.</span></span> <span data-ttu-id="1a16f-139">AND (&)、OR (|)、または AND NOT (&!) を使用して、カスタム近接語句と他のカスタム近接語句、単純語句、またはプレフィックス語句を組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-139">You can use AND (&), OR (|), or AND NOT (&!) to combine a custom proximity term with another custom proximity term, a simple term, or a prefix term.</span></span> <span data-ttu-id="1a16f-140">例:</span><span class="sxs-lookup"><span data-stu-id="1a16f-140">For example:</span></span>  
  
-   <span data-ttu-id="1a16f-141">CONTAINS('NEAR((*term1*,*term2*),5) AND *term3*')</span><span class="sxs-lookup"><span data-stu-id="1a16f-141">CONTAINS('NEAR((*term1*,*term2*),5) AND *term3*')</span></span>  
  
-   <span data-ttu-id="1a16f-142">CONTAINS('NEAR((*term1*,*term2*),5) OR *term3*')</span><span class="sxs-lookup"><span data-stu-id="1a16f-142">CONTAINS('NEAR((*term1*,*term2*),5) OR *term3*')</span></span>  
  
-   <span data-ttu-id="1a16f-143">CONTAINS('NEAR((*term1*,*term2*),5) AND NOT *term3*')</span><span class="sxs-lookup"><span data-stu-id="1a16f-143">CONTAINS('NEAR((*term1*,*term2*),5) AND NOT *term3*')</span></span>  
  
-   <span data-ttu-id="1a16f-144">CONTAINS('NEAR((*term1*,*term2*),5) AND NEAR((*term3*,*term4*),2)')</span><span class="sxs-lookup"><span data-stu-id="1a16f-144">CONTAINS('NEAR((*term1*,*term2*),5) AND NEAR((*term3*,*term4*),2)')</span></span>  
  
-   <span data-ttu-id="1a16f-145">CONTAINS('NEAR((*term1*,*term2*),5) OR NEAR((*term3*,*term4*),2, TRUE)')</span><span class="sxs-lookup"><span data-stu-id="1a16f-145">CONTAINS('NEAR((*term1*,*term2*),5) OR NEAR((*term3*,*term4*),2, TRUE)')</span></span>  
  
 <span data-ttu-id="1a16f-146">たとえば、</span><span class="sxs-lookup"><span data-stu-id="1a16f-146">For example,</span></span>  
  
```  
CONTAINS(column_name, 'NEAR((term1, term2), 5, TRUE) AND term3')  
```  
  
 <span data-ttu-id="1a16f-147">カスタム近接語句を汎用近接語句 (*term1* NEAR *term2*)、生成語 (isabout...)、または重み付け語句 (フォーム...) と組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="1a16f-147">You cannot combine a custom proximity term with a generic proximity term (*term1* NEAR *term2*), a generation term (ISABOUT ...), or a weighted term (FORMSOF ...).</span></span>  
  
### <a name="example-using-the-custom-proximity-term"></a><span data-ttu-id="1a16f-148">例 : カスタム近接語句の使用</span><span class="sxs-lookup"><span data-stu-id="1a16f-148">Example: Using the Custom Proximity Term</span></span>  
 <span data-ttu-id="1a16f-149">次の例では、 `Production.Document` サンプル データベースの `AdventureWorks2012` テーブルを検索して、"reflector" という語を "bracket" と同一のドキュメント内に含むすべてのドキュメントの概要を検出します。</span><span class="sxs-lookup"><span data-stu-id="1a16f-149">The following example searches the `Production.Document` table of the `AdventureWorks2012` sample database for all document summaries that contain the word "reflector" in the same document as the word "bracket".</span></span>  
  
```  
SELECT DocumentNode, Title, DocumentSummary  
FROM Production.Document AS DocTable   
INNER JOIN CONTAINSTABLE(Production.Document, Document,  
  'NEAR(bracket, reflector)' ) AS KEY_TBL  
  ON DocTable.DocumentNode = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK > 50  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  

  
##  <a name="additional-considerations-for-proximity-searches"></a><a name="Additional_Considerations"></a><span data-ttu-id="1a16f-150">近接検索に関するその他の考慮事項</span><span class="sxs-lookup"><span data-stu-id="1a16f-150">Additional Considerations for Proximity Searches</span></span>  
 <span data-ttu-id="1a16f-151">このセクションでは、汎用およびカスタム近接検索の両方に影響する注意点について説明します。</span><span class="sxs-lookup"><span data-stu-id="1a16f-151">This section discusses consideration that affect both generic and custom proximity searches:</span></span>  
  
-   <span data-ttu-id="1a16f-152">検索語句の出現の重複</span><span class="sxs-lookup"><span data-stu-id="1a16f-152">Overlapping occurrences of search terms</span></span>  
  
     <span data-ttu-id="1a16f-153">すべての近接検索は、重複しない語句だけを常に検索します。</span><span class="sxs-lookup"><span data-stu-id="1a16f-153">All proximity searches always look for only non-overlapping occurrences.</span></span> <span data-ttu-id="1a16f-154">検索語句で重複する語句は、一致とは認識されません。</span><span class="sxs-lookup"><span data-stu-id="1a16f-154">Overlapping occurrences of search terms never qualify as matches.</span></span> <span data-ttu-id="1a16f-155">たとえば、最大距離が 2 語で`A`および`AA`をこの順序で検索する次の近接語句について検討してみます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-155">For example, consider the following proximity term, which searches "`A`" and "`AA`" in this order with a maximum distance of two terms:</span></span>  
  
    ```  
    CONTAINS(column_name, 'NEAR((A,AA),2, TRUE')  
    ```  
  
     <span data-ttu-id="1a16f-156">一致する語句としては、`AAA`、`A.AA`、および`A..AA`が考えられます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-156">The possible matches are as "`AAA`", "`A.AA`", and "`A..AA`".</span></span> <span data-ttu-id="1a16f-157">`AA`だけを含む行は一致しません。</span><span class="sxs-lookup"><span data-stu-id="1a16f-157">Rows containing just "`AA`" would not match.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1a16f-158">たとえば、 `NEAR("mountain bike", "bike trails")` または `(NEAR(comfort*, comfortable), 5)`などの重複する語句は指定できます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-158">You can specify terms that overlap, for example, `NEAR("mountain bike", "bike trails")` or `(NEAR(comfort*, comfortable), 5)`.</span></span> <span data-ttu-id="1a16f-159">重複する語句を指定すると、一致する可能性がある順列が増えることでクエリの複雑さが増大します。</span><span class="sxs-lookup"><span data-stu-id="1a16f-159">Specifying a overlapping terms increases the complexity of the query by increasing the possible match permutations.</span></span> <span data-ttu-id="1a16f-160">このような重複する語句を多数指定するとリソースが不足し、クエリが失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="1a16f-160">If you specify a large number of such overlapping terms, the query can run out of resources and fail.</span></span> <span data-ttu-id="1a16f-161">この現象が発生する場合は、クエリを簡略化してもう一度やり直してください。</span><span class="sxs-lookup"><span data-stu-id="1a16f-161">If this occurs, simplify the query and try again.</span></span>  
  
-   <span data-ttu-id="1a16f-162">汎用 NEAR もカスタム NEAR も、指定した最大距離に関係なく、語句間の絶対的な距離ではなく論理的な距離を示します。</span><span class="sxs-lookup"><span data-stu-id="1a16f-162">Both generic NEAR and custom NEAR (regardless of whether a maximum distance is specified) indicate the logical distance between terms, rather than the absolute distance between them.</span></span> <span data-ttu-id="1a16f-163">たとえば、段落内の別の語句や文に含まれている語は、同じ語句や文に含まれている語に比べて関連度が低いと想定されるため、実際の近接度に関係なく、より離れているものとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-163">For example, terms within different phrases or sentences within a paragraph are treated as farther apart than terms in the same phrase or sentence, regardless of their actual proximity, on the assumption that they are less related.</span></span> <span data-ttu-id="1a16f-164">同様に、別の段落にある語は、さらに離れているものとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-164">Likewise, terms in different paragraphs are treated as being even farther apart.</span></span> <span data-ttu-id="1a16f-165">一致する語句が、文、段落、または章の末尾にまで及ぶ場合、ドキュメントの順位付けに使用される間隔は、それぞれ 8、128、または 1024 ずつ増加します。</span><span class="sxs-lookup"><span data-stu-id="1a16f-165">If a match spans the end of a sentence, paragraph, or chapter, the gap used for ranking a document is increased by 8, 128, or 1024, respectively.</span></span>  
  
-   <span data-ttu-id="1a16f-166">CONTAINSTABLE 関数による順位付けへの近接語句の影響</span><span class="sxs-lookup"><span data-stu-id="1a16f-166">Impact of proximity terms on ranking by the CONTAINSTABLE function</span></span>  
  
     <span data-ttu-id="1a16f-167">NEAR を CONTAINSTABLE 関数で使用する場合は、ドキュメント内のその長さに関連する一致数と、各一致における最初の検索語句と最後の検索語句の間の距離が、各ドキュメントの順位付けに影響します。</span><span class="sxs-lookup"><span data-stu-id="1a16f-167">When NEAR is used in the CONTAINSTABLE function, the number of hits in a document relative to its length as well as the distance between the first and last search terms in each of the hits affects the ranking of each document.</span></span> <span data-ttu-id="1a16f-168">汎用近接語句では、たとえば、一致する検索語間の距離が 50 論理語より大きい場合、そのドキュメントについて返される順位は 0 になります。</span><span class="sxs-lookup"><span data-stu-id="1a16f-168">For a generic proximity term, if the matched search terms are >50 logical terms apart, the rank returned on a document is 0.</span></span> <span data-ttu-id="1a16f-169">最大距離として整数を指定しないカスタム近接語句では、間隔が 100 論理語より大きい一致のみを含むドキュメントは、順位 0 を取得します。</span><span class="sxs-lookup"><span data-stu-id="1a16f-169">For a custom proximity term that does not specify an integer as the maximum distance, a document that contains only hits whose gap is >100 logical terms will receive a ranking of 0.</span></span> <span data-ttu-id="1a16f-170">カスタム近接語句の順位付けの詳細については、「[RANK を使用して検索結果を制限する方法](limit-search-results-with-rank.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a16f-170">For more information about ranking of custom proximity searches, see [Limit Search Results with RANK](limit-search-results-with-rank.md).</span></span>  
  
-   <span data-ttu-id="1a16f-171">**transform noise words** サーバー オプション</span><span class="sxs-lookup"><span data-stu-id="1a16f-171">The **transform noise words** server option</span></span>  
  
     <span data-ttu-id="1a16f-172">**transform noise words[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の値は、ストップワードが近接検索で指定されている場合、** がストップワードを処理する方法に影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-172">The value of **transform noise words** impacts how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] treats stopwords if they are specified in proximity searches.</span></span> <span data-ttu-id="1a16f-173">詳細については、「 [transform noise words Server Configuration Option](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a16f-173">For more information, see [transform noise words Server Configuration Option](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md).</span></span>  
  

  
##  <a name="the-deprecated-generic-proximity-term"></a><a name="Generic_NEAR"></a><span data-ttu-id="1a16f-174">非推奨の汎用近接語句</span><span class="sxs-lookup"><span data-stu-id="1a16f-174">The Deprecated Generic Proximity Term</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]<span data-ttu-id="1a16f-175">[カスタム近接語句](#Custom_NEAR)を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1a16f-175">We recommend that you use the [custom proximity term](#Custom_NEAR).</span></span>  
  
 <span data-ttu-id="1a16f-176">汎用近接語句とは、検索用語の間で検索されない語句の数 ( *距離*) に関係なく、特定の用語がドキュメントで一致すればすべて返されることを示します。</span><span class="sxs-lookup"><span data-stu-id="1a16f-176">A generic proximity term indicates that the specified search terms must all occur in a document for a match to be returned, regardless of the number of non-search terms (the *distance*) between the search terms.</span></span> <span data-ttu-id="1a16f-177">基本構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1a16f-177">The basic syntax is:</span></span>  
  
 <span data-ttu-id="1a16f-178">{ *search_term* {NEAR | ~} *search_term* }[ ,...*n* ]</span><span class="sxs-lookup"><span data-stu-id="1a16f-178">{ *search_term* { NEAR | ~ } *search_term* } [ ,...*n* ]</span></span>  
  
 <span data-ttu-id="1a16f-179">たとえば、次の例では、"fox" という語と "chicken" という語が任意の順序で両方とも含まれる場合に一致として検出されます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-179">For example, in the following examples, the words 'fox' and 'chicken' must both appear, in either order, to produce a match:</span></span>  
  
-   `CONTAINS(column_name, 'fox NEAR chicken')`  
  
-   `CONTAINSTABLE(table_name, column_name, 'fox ~ chicken')`  
  
> [!NOTE]  
>  <span data-ttu-id="1a16f-180"><generic_proximity_term> 構文の詳細については、「[CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a16f-180">For information about the <generic_proximity_term> syntax, see [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql).</span></span>  
  
 <span data-ttu-id="1a16f-181">詳細については、後の「[近接検索に関するその他の注意点](#Additional_Considerations)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a16f-181">For more information, see "[Additional Considerations about Proximity Searches](#Additional_Considerations)," later in this topic.</span></span>  
  
### <a name="combining-a-generic-proximity-term-with-other-terms"></a><span data-ttu-id="1a16f-182">汎用近接語句とその他の語句との組み合わせ</span><span class="sxs-lookup"><span data-stu-id="1a16f-182">Combining a Generic Proximity Term with Other Terms</span></span>  
 <span data-ttu-id="1a16f-183">AND (&)、OR (|)、または AND NOT (&!) を使用して、汎用近接語句と他の汎用近接語句、単純語句、またはプレフィックス語句を組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-183">You can use AND (&), OR (|), or AND NOT (&!) to combine a generic proximity term with another generic proximity term, a simple term, or a prefix term.</span></span> <span data-ttu-id="1a16f-184">例:</span><span class="sxs-lookup"><span data-stu-id="1a16f-184">For example:</span></span>  
  
```  
CONTAINSTABLE (Production.ProductDescription,  
   Description,   
   '(light NEAR aluminum) OR  
   (lightweight NEAR aluminum)'  
)  
```  
  
 <span data-ttu-id="1a16f-185">汎用近接語句とカスタム近接語句 ( `NEAR((term1,term2),5)` 重み付け語句 (ISABOUT...)、または世代の用語 (フォーム...)) を組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="1a16f-185">You cannot combine a generic proximity term with a custom proximity term, such as `NEAR((term1,term2),5)`, a weighted term (ISABOUT ...), or a generational term (FORMSOF ...).</span></span>  
  
### <a name="example-using-the-generic-proximity-term"></a><span data-ttu-id="1a16f-186">例 : 汎用近接語句の使用</span><span class="sxs-lookup"><span data-stu-id="1a16f-186">Example: Using the Generic Proximity Term</span></span>  
 <span data-ttu-id="1a16f-187">次の例では、汎用近接語句を使用して、"reflector" という語と "bracket" という語を同一のドキュメント内で検索します。</span><span class="sxs-lookup"><span data-stu-id="1a16f-187">The following example uses the generic proximity term to search for the word "reflector" in the same document as the word "bracket".</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT DocumentNode, Title, DocumentSummary  
FROM Production.Document AS DocTable INNER JOIN  
  CONTAINSTABLE(Production.Document, Document,  
  '(reflector NEAR bracket)' ) AS KEY_TBL  
  ON DocTable.DocumentNode = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  
 <span data-ttu-id="1a16f-188">CONTAINSTABLE では用語の順序を逆に指定しても、同じ結果を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-188">Notice that you can also reverse the terms in CONTAINSTABLE to get the same result:</span></span>  
  
```  
CONTAINSTABLE(Production.Document, Document, '(bracket NEAR reflector)' ) AS KEY_TBL  
```  
  
 <span data-ttu-id="1a16f-189">前の例で NEAR キーワードの代わりにチルダ (~) を指定しても同じ結果を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-189">You can use the tilde character (~) in place of the NEAR keyword in the earlier query, and get the same results:</span></span>  
  
```  
CONTAINSTABLE(Production.Document, Document, '(reflector ~ bracket)' ) AS KEY_TBL  
```  
  
 <span data-ttu-id="1a16f-190">検索条件で 3 つ以上の語または句を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-190">More than two words or phrases can be specified in the search conditions.</span></span> <span data-ttu-id="1a16f-191">たとえば、次のように記述できます。</span><span class="sxs-lookup"><span data-stu-id="1a16f-191">For example, it is possible to write:</span></span>  
  
```  
CONTAINSTABLE(Production.Document, Document, '(reflector ~ bracket ~ installation)' ) AS KEY_TBL  
```  
  
 <span data-ttu-id="1a16f-192">これは、"reflector" という語が "bracket" と同じドキュメント内に含まれ、"bracket" という語が "installation" と同じドキュメント内に含まれる必要があることを意味しています。</span><span class="sxs-lookup"><span data-stu-id="1a16f-192">This means that "reflector" must be in the same document as "bracket", and "bracket" must be in the same document as "installation".</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="1a16f-193">参照</span><span class="sxs-lookup"><span data-stu-id="1a16f-193">See Also</span></span>  
 <span data-ttu-id="1a16f-194">[CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1a16f-194">[CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span></span>  
 <span data-ttu-id="1a16f-195">[フルテキスト検索でのクエリ](query-with-full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="1a16f-195">[Query with Full-Text Search](query-with-full-text-search.md) </span></span>  
 [<span data-ttu-id="1a16f-196">CONTAINS &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1a16f-196">CONTAINS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/contains-transact-sql)  
  
  
