---
title: 手動でのテーブルの結合 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- manual joins [SQL Server]
- joins [SQL Server], manual
- joins [SQL Server], creating
ms.assetid: 9c785356-646b-4c87-82d4-25efd6051d9d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 83f7615be3f5f18164dd3ca0f62ef6cbd9167be3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711442"
---
# <a name="join-tables-manually-visual-database-tools"></a><span data-ttu-id="5e473-102">手動でのテーブルの結合 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="5e473-102">Join Tables Manually (Visual Database Tools)</span></span>
  <span data-ttu-id="5e473-103">[クエリおよびビュー デザイナー](visual-database-tools.md) では、クエリに複数のテーブルを追加すると、共通データ、またはテーブルの関連付けに関するデータベース内に格納されている情報に基づいて、テーブルが結合されます。</span><span class="sxs-lookup"><span data-stu-id="5e473-103">When you add two (or more) tables to a query, the [Query and View Designer](visual-database-tools.md) attempts to join them based on common data or on information stored in the database about how tables are related.</span></span> <span data-ttu-id="5e473-104">詳しくは、「[テーブルの自動結合 (Visual Database Tools)](join-tables-automatically-visual-database-tools.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5e473-104">For details, see [Join Tables Automatically &#40;Visual Database Tools&#41;](join-tables-automatically-visual-database-tools.md).</span></span> <span data-ttu-id="5e473-105">ただし、クエリおよびビュー デザイナーでテーブルが自動的に結合されなかった場合、またはテーブル間の結合条件を追加作成する場合は、テーブルを手動で結合できます。</span><span class="sxs-lookup"><span data-stu-id="5e473-105">However, if the Query and View Designer has not joined the tables automatically, or if you want to create additional join conditions between tables, you can join tables manually.</span></span>  
  
 <span data-ttu-id="5e473-106">結合は、同じ情報を含む列だけでなく、任意の 2 つの列の比較に基づいて作成できます。</span><span class="sxs-lookup"><span data-stu-id="5e473-106">You can create joins based on comparisons between any two columns, not just columns that contain the same information.</span></span> <span data-ttu-id="5e473-107">たとえば、データベースに `titles` および `roysched`という 2 つのテーブルがある場合、 `ytd_sales` テーブルの `titles` 列の値と、 `lorange` テーブルの `hirange` 列および `roysched` 列の値とを比較できます。</span><span class="sxs-lookup"><span data-stu-id="5e473-107">For example, if your database contains two tables, `titles` and `roysched`, you can compare values in the `ytd_sales` column of the `titles` table against the `lorange` and `hirange` columns in the `roysched` table.</span></span> <span data-ttu-id="5e473-108">この結合を作成すると、本年度の売り上げが印税の支払いの上限と下限の範囲内にある書名を検索できます。</span><span class="sxs-lookup"><span data-stu-id="5e473-108">Creating this join would allow you to find titles for which the year-to-date sales falls between the low and high ranges for the royalty payments.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="5e473-109">結合の処理速度は、結合条件の列にインデックスが設定されている場合、最も速くなります。</span><span class="sxs-lookup"><span data-stu-id="5e473-109">Joins work fastest if the columns in the join condition have been indexed.</span></span> <span data-ttu-id="5e473-110">インデックスの設定されていない列を結合すると、場合によってはクエリの処理速度が遅くなります。</span><span class="sxs-lookup"><span data-stu-id="5e473-110">In some cases, joining on unindexed columns can result in a slow query.</span></span>  
  
### <a name="to-manually-join-tables-or-table-structured-objects"></a><span data-ttu-id="5e473-111">テーブルまたはテーブル構造オブジェクトを手動で結合するには</span><span class="sxs-lookup"><span data-stu-id="5e473-111">To manually join tables or table-structured objects</span></span>  
  
1.  <span data-ttu-id="5e473-112">結合するオブジェクトを [ダイアグラム ペイン](diagram-pane-visual-database-tools.md) に追加します。</span><span class="sxs-lookup"><span data-stu-id="5e473-112">Add to the [Diagram pane](diagram-pane-visual-database-tools.md) the objects you want to join.</span></span>  
  
2.  <span data-ttu-id="5e473-113">最初のテーブルまたはテーブル構造オブジェクトの結合列の名前をドラッグし、2 番目のテーブルまたはテーブル結合オブジェクトの関連する列にドロップします。</span><span class="sxs-lookup"><span data-stu-id="5e473-113">Drag the name of the join column in the first table or table-structured object and drop it onto the related column in the second table or table-structured object.</span></span> <span data-ttu-id="5e473-114">`text`、`ntext`、または i`mage` 型の列を結合することはできません。</span><span class="sxs-lookup"><span data-stu-id="5e473-114">You cannot base a join on `text`, `ntext`, or i`mage` columns.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5e473-115">結合列のデータ型は、同じ型か互換性のある型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e473-115">The join columns must be of the same (or compatible) data types.</span></span> <span data-ttu-id="5e473-116">たとえば、最初のテーブルの結合列が日付型の場合は、2 番目のテーブルの結合列も日付型としてください。</span><span class="sxs-lookup"><span data-stu-id="5e473-116">For example, if the join column in the first table is a date, you must relate it to a date column in the second table.</span></span> <span data-ttu-id="5e473-117">一方、最初の結合列が整数型の場合、関連付ける結合列も整数型である必要がありますが、サイズは異なってもかまいません。</span><span class="sxs-lookup"><span data-stu-id="5e473-117">On the other hand, if the first join column is an integer, the related join column must also be of an integer data type, but it can be a different size.</span></span> <span data-ttu-id="5e473-118">クエリおよびビュー デザイナーでは、結合の作成に使用した列のデータ型がチェックされることはありません。ただしデータ型に互換性がない場合、クエリの実行時にデータベースによってエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e473-118">The Query and View Designer will not check the data types of the columns you use to create a join, but when you execute the query, the database will display an error if the data types are not compatible.</span></span>  
  
3.  <span data-ttu-id="5e473-119">必要に応じて結合演算子を変更します。既定の演算子は等号 (=) です。</span><span class="sxs-lookup"><span data-stu-id="5e473-119">If necessary, change the join operator; by default, the operator is an equal sign (=).</span></span> <span data-ttu-id="5e473-120">詳細については、「[結合演算子の変更 (Visual Database Tools)](modify-join-operators-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e473-120">For details, see [Modify Join Operators &#40;Visual Database Tools&#41;](modify-join-operators-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="5e473-121">[SQL ペイン](sql-pane-visual-database-tools.md)のステートメントに INNER JOIN 句が追加されます。</span><span class="sxs-lookup"><span data-stu-id="5e473-121">The Query and View Designer adds an INNER JOIN clause to the SQL statement in the [SQL pane](sql-pane-visual-database-tools.md).</span></span> <span data-ttu-id="5e473-122">結合の種類を外部結合に変更できます。</span><span class="sxs-lookup"><span data-stu-id="5e473-122">You can change the type to an outer join.</span></span> <span data-ttu-id="5e473-123">詳細については、「[外部結合の作成 (Visual Database Tools)](create-outer-joins-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e473-123">For details see [Create Outer Joins &#40;Visual Database Tools&#41;](create-outer-joins-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e473-124">参照</span><span class="sxs-lookup"><span data-stu-id="5e473-124">See Also</span></span>  
 [<span data-ttu-id="5e473-125">結合を使用したクエリ (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="5e473-125">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
