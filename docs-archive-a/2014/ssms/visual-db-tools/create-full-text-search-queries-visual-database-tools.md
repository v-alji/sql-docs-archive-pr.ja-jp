---
title: フルテキスト検索クエリの作成 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CONTAINS predicate (Transact-SQL)
- queries [full-text search], creating
- full-text queries [SQL Server], creating
ms.assetid: 537fa556-390e-4c88-9b8e-679848d94abc
author: stevestein
ms.author: sstein
ms.openlocfilehash: f84ab465da0a1b7ac1da1211de1d5199fd28ee95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714969"
---
# <a name="create-full-text-search-queries-visual-database-tools"></a><span data-ttu-id="8c3c1-102">フルテキスト検索クエリの作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="8c3c1-102">Create Full-Text Search Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="8c3c1-103">フルテキスト検索は、CONTAINS 述語を使用して、特定の列内に指定したテキストを持つ行を探します。</span><span class="sxs-lookup"><span data-stu-id="8c3c1-103">Full-text searches use the CONTAINS predicate to locate rows that have specified text in a given column.</span></span> <span data-ttu-id="8c3c1-104">フルテキスト検索は、アクティブなフルテキスト インデックスが設定されている列でのみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="8c3c1-104">Full-Text searches are only possible on columns that have active full-text indexes.</span></span> <span data-ttu-id="8c3c1-105">現在アクティブなフルテキスト インデックスが設定されていない列に対して CONTAINS 句を使用すると、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="8c3c1-105">If you attempt to use the CONTAINS clause on a column that does not have a currently active full-text index, you will receive an error.</span></span> <span data-ttu-id="8c3c1-106">フルテキストインデックスと CONTAINS 句の詳細については、「[フルテキスト検索](../../relational-databases/search/full-text-search.md)」と「 [Transact-sql&#41;を含む &#40;](/sql/t-sql/queries/contains-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c3c1-106">For more information on full-text indexes and the CONTAINS clause, see [Full-Text Search](../../relational-databases/search/full-text-search.md) and [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql).</span></span>  
  
### <a name="to-create-a-full-text-search-query"></a><span data-ttu-id="8c3c1-107">フルテキスト検索クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="8c3c1-107">To create a full-text search query</span></span>  
  
1.  <span data-ttu-id="8c3c1-108">ソリューション エクスプローラーでクエリを開くか、新しいクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="8c3c1-108">Open a query from Solution Explorer or create a new one.</span></span>  
  
2.  <span data-ttu-id="8c3c1-109">クエリの WHERE 句で、CONTAINS 関数を使用してフルテキスト列を検索します。</span><span class="sxs-lookup"><span data-stu-id="8c3c1-109">In the WHERE clause of your query, use the CONTAINS function to search a full-text column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c3c1-110">参照</span><span class="sxs-lookup"><span data-stu-id="8c3c1-110">See Also</span></span>  
 <span data-ttu-id="8c3c1-111">[Visual Database Tools &#40;サポートされているクエリの種類&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="8c3c1-111">[Supported Query Types &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="8c3c1-112">[クエリおよびビューのデザイン方法に関するトピック &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="8c3c1-112">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="8c3c1-113">クエリに関する基本操作の実行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="8c3c1-113">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
