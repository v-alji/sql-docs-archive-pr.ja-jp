---
title: テーブルの自動結合 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- automatic joins
- joins [SQL Server], creating
- joins [SQL Server], automatic
ms.assetid: f152af82-bcb6-49ca-af19-48cdb7fc9ac6
author: stevestein
ms.author: sstein
ms.openlocfilehash: d05100f801d972759c1b5c105814f5cdbdccf84f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711441"
---
# <a name="join-tables-automatically-visual-database-tools"></a><span data-ttu-id="97fad-102">テーブルの自動結合 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="97fad-102">Join Tables Automatically (Visual Database Tools)</span></span>
  <span data-ttu-id="97fad-103">クエリに複数のテーブルを追加すると、 [クエリおよびビュー デザイナー](visual-database-tools.md) により、これらのテーブルが相互に関連しているかどうかの確認が行われます。</span><span class="sxs-lookup"><span data-stu-id="97fad-103">When you add two or more tables to a query, the [Query and View Designer](visual-database-tools.md) attempts to determine if they are related.</span></span> <span data-ttu-id="97fad-104">関連している場合は、テーブルまたはテーブル構造オブジェクトを示す四角形の間に、結合線が自動的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="97fad-104">If they are, the Query and View Designer automatically puts join lines between the rectangles representing the tables or table-structured objects.</span></span>  
  
 <span data-ttu-id="97fad-105">クエリおよびビュー デザイナーでは、次の場合にテーブルの結合が認識されます。</span><span class="sxs-lookup"><span data-stu-id="97fad-105">The Query and View Designer will recognize tables as joined if:</span></span>  
  
-   <span data-ttu-id="97fad-106">データベースにテーブルの関連を指定する情報がある場合。</span><span class="sxs-lookup"><span data-stu-id="97fad-106">The database contains information that specifies that the tables are related.</span></span>  
  
-   <span data-ttu-id="97fad-107">各テーブルの 1 つの列が、それぞれ同じ名前および同じデータ型を持っている場合。</span><span class="sxs-lookup"><span data-stu-id="97fad-107">If two columns, one in each table, have the same name and data type.</span></span> <span data-ttu-id="97fad-108">少なくとも一方のテーブルの列は、主キーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="97fad-108">The column must be a primary key in at least one of the tables.</span></span> <span data-ttu-id="97fad-109">たとえば、 `employee` テーブルおよび `jobs` テーブルを追加し、 `job_id` テーブルに `jobs` 列という主キーがあり、それぞれのテーブルに同じデータ型の `job_id` という列がある場合、これらのテーブルは自動的に結合されます。</span><span class="sxs-lookup"><span data-stu-id="97fad-109">For example, if you add `employee` and `jobs` tables, if the `job_id` column is the primary key in the `jobs` table, and if each table has a column called `job_id` with the same data type, the Query and View Designer will automatically join the tables.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="97fad-110">クエリおよびビュー デザイナーでは、同じ名前および同じデータ型の列の間で結合が 1 つだけ作成されます。</span><span class="sxs-lookup"><span data-stu-id="97fad-110">The Query and View Designer will create only one join based on columns with the same name and data type.</span></span> <span data-ttu-id="97fad-111">複数の結合が作成できる場合でも、クエリおよびビュー デザイナーは、最初に検出された一致列から結合を 1 つだけ作成します。</span><span class="sxs-lookup"><span data-stu-id="97fad-111">If more than one join is possible, the Query and View Designer stops after creating a join based on the first set of matching columns that it finds.</span></span>  
  
-   <span data-ttu-id="97fad-112">検索条件 (WHERE 句) が、実際には結合条件であると検出された場合。</span><span class="sxs-lookup"><span data-stu-id="97fad-112">The Query and View Designer detects that a search condition (a WHERE clause) is actually a join condition.</span></span> <span data-ttu-id="97fad-113">たとえば、 `employee` テーブルおよび `jobs`テーブルを追加し、両方のテーブルの `job_id` 列の値が一致する行を検索する検索条件を作成する場合があります。</span><span class="sxs-lookup"><span data-stu-id="97fad-113">For example, you might add the tables `employee` and `jobs`, then create a search condition that searches for the same value in the `job_id` column of both tables.</span></span> <span data-ttu-id="97fad-114">その場合、検索条件が結合になることが検出され、検索条件に基づいて結合条件が作成されます。</span><span class="sxs-lookup"><span data-stu-id="97fad-114">When you do, the Query and View Designer detects that the search condition results in a join, and then creates a join condition based on the search condition.</span></span>  
  
 <span data-ttu-id="97fad-115">クエリおよびビュー デザイナーによって作成された結合がクエリに適していない場合、結合の変更または削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="97fad-115">If the Query and View Designer has created a join that is not suitable to your query, you can modify the join or remove it.</span></span> <span data-ttu-id="97fad-116">詳しくは、「[結合演算子の変更 (Visual Database Tools)](modify-join-operators-visual-database-tools.md)」および「[結合の削除 (Visual Database Tools)](remove-joins-visual-database-tools.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="97fad-116">For details, see [Modify Join Operators &#40;Visual Database Tools&#41;](modify-join-operators-visual-database-tools.md) and [Remove Joins &#40;Visual Database Tools&#41;](remove-joins-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="97fad-117">クエリでテーブルが自動的に結合されない場合は、結合を手動で作成できます。</span><span class="sxs-lookup"><span data-stu-id="97fad-117">If the Query and View Designer does not automatically join the tables in your query, you can create a join yourself.</span></span> <span data-ttu-id="97fad-118">詳しくは、「[手動でのテーブルの結合 (Visual Database Tools)](join-tables-manually-visual-database-tools.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="97fad-118">For details, see [Join Tables Manually &#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97fad-119">参照</span><span class="sxs-lookup"><span data-stu-id="97fad-119">See Also</span></span>  
 <span data-ttu-id="97fad-120">[クエリおよびビューデザイナーが Visual Database Tools &#40;の結合を表す方法&#41;](how-the-query-and-view-designer-represents-joins-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="97fad-120">[How the Query and View Designer Represents Joins &#40;Visual Database Tools&#41;](how-the-query-and-view-designer-represents-joins-visual-database-tools.md) </span></span>  
 <span data-ttu-id="97fad-121">[クエリおよびビューのデザイン方法に関するトピック &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="97fad-121">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="97fad-122">結合を使用したクエリ (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="97fad-122">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
