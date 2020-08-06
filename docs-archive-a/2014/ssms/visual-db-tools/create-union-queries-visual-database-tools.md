---
title: UNION クエリの作成 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], types
- UNION queries
- Select query
- combining query results
- merged SELECT query [SQL Server]
ms.assetid: b5aafb1d-e4ed-4922-b790-56abc5ec551a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3c10f39c3e44844c4ec8a6a2328c41ea2de350d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641953"
---
# <a name="create-union-queries-visual-database-tools"></a><span data-ttu-id="bd62d-102">UNION クエリの作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="bd62d-102">Create UNION Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="bd62d-103">UNION キーワードを使用すると、2 つの SELECT ステートメントの結果を、1 つのテーブルに表示できます。</span><span class="sxs-lookup"><span data-stu-id="bd62d-103">The UNION keyword enables you to include the results of two SELECT statements in one resulting table.</span></span> <span data-ttu-id="bd62d-104">いずれかの SELECT ステートメントから返された行がすべて組み合わされて、UNION 式の結果として表示されます。</span><span class="sxs-lookup"><span data-stu-id="bd62d-104">All rows returned from either SELECT statement are combined into the result of the UNION expression.</span></span> <span data-ttu-id="bd62d-105">例については、「 [SELECT の例 &#40;transact-sql&#41;](/sql/t-sql/queries/select-examples-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd62d-105">For examples, see [SELECT Examples &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-examples-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bd62d-106">ダイアグラム ペインに表示できるのは、1 つの SELECT 句だけです。</span><span class="sxs-lookup"><span data-stu-id="bd62d-106">The Diagram pane can only display one SELECT clause.</span></span> <span data-ttu-id="bd62d-107">したがって、UNION クエリを使用している場合、クエリ デザイナーにはテーブル操作ペインは表示されません。</span><span class="sxs-lookup"><span data-stu-id="bd62d-107">Therefore, when you are working with a UNION query, Query Designer hides the Table Operations pane.</span></span>  
  
### <a name="to-create-a-merged-select-query"></a><span data-ttu-id="bd62d-108">マージされた選択クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="bd62d-108">To create a Merged SELECT query</span></span>  
  
1.  <span data-ttu-id="bd62d-109">クエリを開くか、新規作成します。</span><span class="sxs-lookup"><span data-stu-id="bd62d-109">Open a query or create a new one.</span></span>  
  
2.  <span data-ttu-id="bd62d-110">SQL ペインに有効な UNION 式を入力します。</span><span class="sxs-lookup"><span data-stu-id="bd62d-110">In the SQL pane, type a valid UNION expression.</span></span>  
  
     <span data-ttu-id="bd62d-111">次の例は、有効な UNION 式です。</span><span class="sxs-lookup"><span data-stu-id="bd62d-111">The following example is a valid UNION expression.</span></span>  
  
    ```  
    SELECT ProductModelID, Name  
    FROM Production.ProductModel  
    UNION  
    SELECT ProductModelID, Name   
    FROM dbo.Gloves;  
    ```  
  
3.  <span data-ttu-id="bd62d-112">**[クエリ デザイナー]** メニューの **[SQL の実行]** をクリックして、クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="bd62d-112">On the **Query Designer** menu, click **Execute SQL** to run the query.</span></span>  
  
     <span data-ttu-id="bd62d-113">UNION クエリがクエリ デザイナーによって書式化されます。</span><span class="sxs-lookup"><span data-stu-id="bd62d-113">Your UNION query is now formatted by Query Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd62d-114">参照</span><span class="sxs-lookup"><span data-stu-id="bd62d-114">See Also</span></span>  
 <span data-ttu-id="bd62d-115">[Visual Database Tools &#40;サポートされているクエリの種類&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="bd62d-115">[Supported Query Types &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="bd62d-116">[クエリおよびビューのデザイン方法に関するトピック &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="bd62d-116">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 <span data-ttu-id="bd62d-117">[Visual Database Tools &#40;クエリで基本的な操作を実行&#41;](perform-basic-operations-with-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="bd62d-117">[Perform Basic Operations with Queries &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="bd62d-118">UNION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bd62d-118">UNION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/set-operators-union-transact-sql)  
  
  
