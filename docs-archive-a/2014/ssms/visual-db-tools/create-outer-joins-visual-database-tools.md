---
title: 外部結合の作成 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- outer joins
- joins [SQL Server], outer
ms.assetid: 18de47b1-f936-427d-b852-fe6d20334f71
author: stevestein
ms.author: sstein
ms.openlocfilehash: f02c0be049e2e75e1a657bb3c027d20430d562cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741529"
---
# <a name="create-outer-joins-visual-database-tools"></a><span data-ttu-id="e7f86-102">外部結合の作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e7f86-102">Create Outer Joins (Visual Database Tools)</span></span>
  <span data-ttu-id="e7f86-103">[クエリおよびビュー デザイナー](visual-database-tools.md) の既定では、テーブル間に内部結合が作成されます。</span><span class="sxs-lookup"><span data-stu-id="e7f86-103">By default, the [Query and View Designer](visual-database-tools.md) creates an inner join between tables.</span></span> <span data-ttu-id="e7f86-104">つまり、内部結合では、他方のテーブルの行と一致しない行は除外されます。</span><span class="sxs-lookup"><span data-stu-id="e7f86-104">Inner joins eliminate the rows that do not match with a row from the other table.</span></span> <span data-ttu-id="e7f86-105">これに対し、外部結合からは、FROM 句で指定された少なくとも 1 つのテーブルまたはビューにあり、任意の WHERE 検索条件または HAVING 検索条件を満たしているすべての行が返されます。</span><span class="sxs-lookup"><span data-stu-id="e7f86-105">Outer joins, however, return all rows from at least one of the tables or views mentioned in the FROM clause, as long as those rows meet any WHERE or HAVING search conditions.</span></span> <span data-ttu-id="e7f86-106">結合テーブルに一致しないデータ行を結果セットに含める場合は、外部結合を作成します。</span><span class="sxs-lookup"><span data-stu-id="e7f86-106">If you want to include data rows in the result set that do not have a match in the joined table, you can create an outer join.</span></span>  
  
 <span data-ttu-id="e7f86-107">外部結合を作成するときは、SQL ステートメントでのテーブルの表示順序 (SQL ペインに反映される) が重要です。</span><span class="sxs-lookup"><span data-stu-id="e7f86-107">When you create an outer join, the order in which tables appear in the SQL statement (as reflected in the SQL pane) is significant.</span></span> <span data-ttu-id="e7f86-108">最初に追加したテーブルは "左" テーブルに、次に追加したテーブルが "右" テーブルになります。</span><span class="sxs-lookup"><span data-stu-id="e7f86-108">The first table you add becomes the "left" table and the second table becomes the "right" table.</span></span> <span data-ttu-id="e7f86-109">( [ダイアグラム ペイン](diagram-pane-visual-database-tools.md) に実際に表示されるテーブルの順序は重要ではありません)。左外部結合または右外部結合とは、クエリにテーブルを追加した順序、および [SQL ペイン](sql-pane-visual-database-tools.md)の SQL ステートメントでテーブルが表示される順序を示します。</span><span class="sxs-lookup"><span data-stu-id="e7f86-109">(The actual order in which the tables appear in the [Diagram pane](diagram-pane-visual-database-tools.md) is not significant.) When you specify a left or right outer join, you are referring to the order in which the tables were added to the query and to the order in which they appear in the SQL statement in the [SQL pane](sql-pane-visual-database-tools.md).</span></span>  
  
### <a name="to-create-an-outer-join"></a><span data-ttu-id="e7f86-110">外部結合を作成するには</span><span class="sxs-lookup"><span data-stu-id="e7f86-110">To create an outer join</span></span>  
  
1.  <span data-ttu-id="e7f86-111">結合を自動または手動で作成します。</span><span class="sxs-lookup"><span data-stu-id="e7f86-111">Create the join, either automatically or manually.</span></span> <span data-ttu-id="e7f86-112">詳細については、「[テーブルの自動結合 (Visual Database Tools)](join-tables-automatically-visual-database-tools.md)」または「[手動でのテーブルの結合 (Visual Database Tools)](join-tables-manually-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7f86-112">For details, see [Join Tables Automatically &#40;Visual Database Tools&#41;](join-tables-automatically-visual-database-tools.md) or [Join Tables Manually &#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md).</span></span>  
  
2.  <span data-ttu-id="e7f86-113">ダイアグラム ペインで結合線を選択し、 **[クエリ デザイナー]** メニューの **[\<tablename> からすべての行を選択]** をクリックして、結合する行が含まれるテーブルを結合するコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="e7f86-113">Select the join line in the Diagram pane, and then from the **Query Designer** menu, choose **Select All Rows from \<tablename>**, selecting the command that includes the table whose extra rows you want to include.</span></span>  
  
    -   <span data-ttu-id="e7f86-114">左外部結合を作成するには、最初のテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7f86-114">Choose the first table to create a left outer join.</span></span>  
  
    -   <span data-ttu-id="e7f86-115">右外部結合を作成するには、2 番目のテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7f86-115">Choose the second table to create a right outer join.</span></span>  
  
    -   <span data-ttu-id="e7f86-116">完全外部結合を作成するには、両方のテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7f86-116">Choose both tables to create a full outer join.</span></span>  
  
 <span data-ttu-id="e7f86-117">外部結合を指定すると、結合線が外部結合を示す線に変更されます。</span><span class="sxs-lookup"><span data-stu-id="e7f86-117">When you specify an outer join, the Query and View Designer modifies the join line to indicate an outer join.</span></span>  
  
 <span data-ttu-id="e7f86-118">さらに、SQL ペインの SQL ステートメントが変更され、次のステートメントのように結合の種類の変更が反映されます。</span><span class="sxs-lookup"><span data-stu-id="e7f86-118">In addition, the Query and View Designer modifies the SQL statement in the SQL pane to reflect the change in join type, as shown in the following statement:</span></span>  
  
```  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee LEFT OUTER JOIN jobs ON   
    employee.job_id = jobs.job_id  
```  
  
 <span data-ttu-id="e7f86-119">外部結合には不一致行が含まれるため、外部結合を使用すれば、外部キー制約に違反する行を検出することができます。</span><span class="sxs-lookup"><span data-stu-id="e7f86-119">Because an outer join includes unmatched rows, you can use it to find rows that violate foreign key constraints.</span></span> <span data-ttu-id="e7f86-120">そのためには、外部結合を作成し、最も右のテーブルの主キー列から NULL の行を検索する検索条件を追加します。</span><span class="sxs-lookup"><span data-stu-id="e7f86-120">To do so, you create an outer join and then add a search condition to find rows in which the primary key column of the rightmost table is null.</span></span> <span data-ttu-id="e7f86-121">たとえば、次の外部結合は、 `employee` テーブルに対応する行のない `jobs` テーブルの行を検索します。</span><span class="sxs-lookup"><span data-stu-id="e7f86-121">For example, the following outer join finds rows in the `employee` table that do not have corresponding rows in the `jobs` table:</span></span>  
  
```  
SELECT employee.emp_id, employee.job_id  
FROM employee LEFT OUTER JOIN jobs   
   ON employee.job_id = jobs.job_id  
WHERE (jobs.job_id IS NULL)  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7f86-122">参照</span><span class="sxs-lookup"><span data-stu-id="e7f86-122">See Also</span></span>  
 <span data-ttu-id="e7f86-123">[Visual Database Tools &#40;Join を使用したクエリ&#41;](query-with-joins-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="e7f86-123">[Query with Joins &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md) </span></span>  
 <span data-ttu-id="e7f86-124">[[結合] ダイアログ ボックス (Visual Database Tools)](join-dialog-box-visual-database-tools.md)</span><span class="sxs-lookup"><span data-stu-id="e7f86-124">[Join Dialog Box &#40;Visual Database Tools&#41;](join-dialog-box-visual-database-tools.md)</span></span>  
  
  
