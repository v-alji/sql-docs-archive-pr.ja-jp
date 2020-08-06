---
title: XML 列でのフルテキスト検索の使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xml columns [full-text search]
- indexes [full-text search]
ms.assetid: 8096cfc6-1836-4ed5-a769-a5d63b137171
author: rothja
ms.author: jroth
ms.openlocfilehash: 2b6b23933fde6a09d043c7055b0daa7c07035cdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713906"
---
# <a name="use-full-text-search-with-xml-columns"></a><span data-ttu-id="ab125-102">XML 列でのフルテキスト検索の使用</span><span class="sxs-lookup"><span data-stu-id="ab125-102">Use Full-Text Search with XML Columns</span></span>
  <span data-ttu-id="ab125-103">XML 列にフルテキスト インデックスを作成して XML 値のコンテンツにインデックスを設定できますが、XML マークアップは無視されます。</span><span class="sxs-lookup"><span data-stu-id="ab125-103">You can create a full-text index on XML columns that indexes the content of the XML values, but ignores the XML markup.</span></span> <span data-ttu-id="ab125-104">要素タグはトークンの境界として使用されます。</span><span class="sxs-lookup"><span data-stu-id="ab125-104">Element tags are used as token boundaries.</span></span> <span data-ttu-id="ab125-105">インデックスは次の項目に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ab125-105">The following items are indexed:</span></span>  
  
-   <span data-ttu-id="ab125-106">XML 要素のコンテンツ。</span><span class="sxs-lookup"><span data-stu-id="ab125-106">The content of XML elements.</span></span>  
  
-   <span data-ttu-id="ab125-107">最上位レベルの要素の XML 属性のコンテンツ (属性値が数値でない場合)。</span><span class="sxs-lookup"><span data-stu-id="ab125-107">The content of XML attributes of the top-level element only, unless those values are numeric values.</span></span>  
  
 <span data-ttu-id="ab125-108">可能であれば、次のようにしてフルテキスト検索と XML インデックスを組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="ab125-108">When possible, you can combine full-text search with XML index in the following way:</span></span>  
  
1.  <span data-ttu-id="ab125-109">まず、SQL フルテキスト検索を使用して、対象の XML 値をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="ab125-109">First, filter the XML values of interest by using SQL full-text search.</span></span>  
  
2.  <span data-ttu-id="ab125-110">次に、XML 列の XML インデックスを使用する XML 値にクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="ab125-110">Next, query those XML values that use XML index on the XML column.</span></span>  
  
## <a name="example-combining-full-text-search-with-xml-querying"></a><span data-ttu-id="ab125-111">例: フルテキスト検索と XML クエリの組み合わせ</span><span class="sxs-lookup"><span data-stu-id="ab125-111">Example: Combining Full-text Search with XML Querying</span></span>  
 <span data-ttu-id="ab125-112">XML 列でフルテキスト インデックスを作成した後、XML 値が書名に語 "custom" を含んでいることを次のクエリで確認します。</span><span class="sxs-lookup"><span data-stu-id="ab125-112">After the full-text index has been created on the XML column, the following query checks that an XML value contains the word "custom" in the title of a book:</span></span>  
  
```  
SELECT *   
FROM   T   
WHERE  CONTAINS(xCol,'custom')   
AND    xCol.exist('/book/title/text()[contains(.,"custom")]') =1  
```  
  
 <span data-ttu-id="ab125-113">**contains()** メソッドによって、フルテキスト インデックスを使用してドキュメントのどこかに語 "custom" を含んでいる XML 値をサブセットとして取り出します。</span><span class="sxs-lookup"><span data-stu-id="ab125-113">The **contains()** method uses the full-text index to subset the XML values that contain the word "custom" anywhere in the document.</span></span> <span data-ttu-id="ab125-114">**exist()** 句により、書名に語 "custom" が使用されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ab125-114">The **exist()** clause ensures that the word "custom" occurs in the title of a book.</span></span>  
  
 <span data-ttu-id="ab125-115">**contains()** を使用するフルテキスト検索と XQuery **contains()** は意味が異なります。</span><span class="sxs-lookup"><span data-stu-id="ab125-115">A full-text search that uses **contains()** and XQuery **contains()** has different semantics.</span></span> <span data-ttu-id="ab125-116">前者はステミングによるトークンの照合で、後者は部分文字列の照合です。</span><span class="sxs-lookup"><span data-stu-id="ab125-116">The latter is a substring match and the former is a token match that uses stemming.</span></span> <span data-ttu-id="ab125-117">したがって、書名に "run" が使用されている文字列を検索する場合、フルテキストの **contains()** と XQuery の **contains()** をいずれも満たす "run"、"runs"、および "running" が検出されます。</span><span class="sxs-lookup"><span data-stu-id="ab125-117">Therefore, if the search is for the string that has "run" in the title, the matches will include "run", "runs", and "running", because both the full-text **contains()** and the Xquery **contains()** are satisfied.</span></span> <span data-ttu-id="ab125-118">ただし、この例のクエリでは語 "customizable" が書名に使用されていても、XQuery の **contains()** は満たしますがフルテキストの **contains()** で失敗するので検出されません。</span><span class="sxs-lookup"><span data-stu-id="ab125-118">However, the query does not match the word "customizable" in the title in that the full-text **contains()** fails, but the Xquery **contains()** is satisfied.</span></span> <span data-ttu-id="ab125-119">一般に純粋な部分文字列の検索を行うには、フルテキストの **contains()** 句を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab125-119">Generally, for pure substring match, the full-text **contains()** clause should be removed.</span></span>  
  
 <span data-ttu-id="ab125-120">さらに、フルテキスト検索ではステマーが使用されますが、XQuery の **contains()** はリテラルの照合です。</span><span class="sxs-lookup"><span data-stu-id="ab125-120">Additionally, full-text search uses word stemming, but XQuery **contains()** is a literal match.</span></span> <span data-ttu-id="ab125-121">両者の違いを次の例で示します。</span><span class="sxs-lookup"><span data-stu-id="ab125-121">This difference is illustrated in the next example.</span></span>  
  
## <a name="example-full-text-search-on-xml-values-using-stemming"></a><span data-ttu-id="ab125-122">例: ステミングを使用した XML 値のフルテキスト検索</span><span class="sxs-lookup"><span data-stu-id="ab125-122">Example: Full-text Search on XML Values Using Stemming</span></span>  
 <span data-ttu-id="ab125-123">上記の例で行った XQuery **contains()** による確認は、通常は省略できません。</span><span class="sxs-lookup"><span data-stu-id="ab125-123">The XQuery **contains()** check that was performed in the previous example generally cannot be eliminated.</span></span> <span data-ttu-id="ab125-124">次のクエリについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="ab125-124">Consider this query:</span></span>  
  
```  
SELECT *   
FROM   T   
WHERE  CONTAINS(xCol,'run')   
```  
  
 <span data-ttu-id="ab125-125">ドキュメント内で語 "ran" が使用されていると、ステミングによりこの検索条件に一致します。</span><span class="sxs-lookup"><span data-stu-id="ab125-125">The word "ran" in the document matches the search condition because of stemming.</span></span> <span data-ttu-id="ab125-126">XQuery では検索コンテキストは確認されません。</span><span class="sxs-lookup"><span data-stu-id="ab125-126">Additionally, the search context is not checked by using XQuery.</span></span>  
  
 <span data-ttu-id="ab125-127">フルテキスト インデックスが作成されたリレーショナル列に AXSD を使用して XML を分解した場合、XML ビューに XPath クエリを実行しても基になるテーブルのフルテキスト検索は行われません。</span><span class="sxs-lookup"><span data-stu-id="ab125-127">When XML is decomposed into relational columns by using AXSD that are full-text indexed, XPath queries that occur over the XML view do not perform full-text search on the underlying tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab125-128">参照</span><span class="sxs-lookup"><span data-stu-id="ab125-128">See Also</span></span>  
 [<span data-ttu-id="ab125-129">XML インデックス &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ab125-129">XML Indexes &#40;SQL Server&#41;</span></span>](xml-indexes-sql-server.md)  
  
  
