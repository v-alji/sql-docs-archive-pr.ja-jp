---
title: 複数の列でテーブルを結合する (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- multiple column joins
- joins [SQL Server], multiple columns
ms.assetid: 56a158bc-a42a-4b78-baad-4721d2d22cd3
author: stevestein
ms.author: sstein
ms.openlocfilehash: dda52fe27b2034242c8cbf458dd010240c792146
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641385"
---
# <a name="join-tables-on-multiple-columns-visual-database-tools"></a><span data-ttu-id="85799-102">複数の列でテーブルを結合する (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="85799-102">Join Tables on Multiple Columns (Visual Database Tools)</span></span>
  <span data-ttu-id="85799-103">テーブルの結合は、複数の列を使用して行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="85799-103">You can join tables with multiple columns.</span></span> <span data-ttu-id="85799-104">つまり、2 つのテーブルの行が複数の条件を満たす場合だけこれらのテーブルの行を対応させるクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="85799-104">That is, you can create a query that matches rows from the two tables only if they satisfy multiple conditions.</span></span> <span data-ttu-id="85799-105">データベースのリレーションシップによって、複数存在する外部キー列を他方のテーブルの複数列にわたる主キーと一致させる場合、このリレーションシップを使用して複数列結合を作成できます。</span><span class="sxs-lookup"><span data-stu-id="85799-105">If the database contains a relationship matching multiple foreign-key columns in one table to a multicolumn primary key in the other table, you can use this relationship to create a multicolumn join.</span></span> <span data-ttu-id="85799-106">詳しくは、「[テーブルの自動結合 (Visual Database Tools)](visual-database-tools.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="85799-106">For details, see [Join Tables Automatically &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="85799-107">複数列の外部キー リレーションシップがデータベースにない場合でも、この結合を手動で作成できます。</span><span class="sxs-lookup"><span data-stu-id="85799-107">Even if the database contains no multi-column foreign-key relationship, you can create the join manually.</span></span>  
  
### <a name="to-manually-create-a-multicolumn-join"></a><span data-ttu-id="85799-108">複数列結合を手動で作成するには</span><span class="sxs-lookup"><span data-stu-id="85799-108">To manually create a multicolumn join</span></span>  
  
1.  <span data-ttu-id="85799-109">結合するテーブルを [ダイアグラム ペイン](diagram-pane-visual-database-tools.md) に追加します。</span><span class="sxs-lookup"><span data-stu-id="85799-109">Add to the [Diagram pane](diagram-pane-visual-database-tools.md) the tables you want to join.</span></span>  
  
2.  <span data-ttu-id="85799-110">最初のテーブル ウィンドウの最初の結合列の名前をドラッグし、2 番目のテーブル ウィンドウの関連する列にドロップします。</span><span class="sxs-lookup"><span data-stu-id="85799-110">Drag the name of the first join column in the first table window and drop it onto the related column in the second table window.</span></span> <span data-ttu-id="85799-111">text 型、ntext 型、または image 型の列を結合することはできません。</span><span class="sxs-lookup"><span data-stu-id="85799-111">You cannot base a join on text, ntext, or image columns.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="85799-112">一般に、結合列のデータ型は、同じ型か互換性のある型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="85799-112">In general, the join columns must be of the same (or compatible) data types.</span></span> <span data-ttu-id="85799-113">たとえば、最初のテーブルの結合列が日付型の場合は、2 番目のテーブルの結合列も日付型としてください。</span><span class="sxs-lookup"><span data-stu-id="85799-113">For example, if the join column in the first table is a date, you must relate it to a date column in the second table.</span></span> <span data-ttu-id="85799-114">一方、最初の結合列が整数型の場合、関連付ける結合列も整数型である必要がありますが、サイズは異なってもかまいません。</span><span class="sxs-lookup"><span data-stu-id="85799-114">On the other hand, if the first join column is an integer, the related join column must also be of an integer data type, but it can be a different size.</span></span> <span data-ttu-id="85799-115">ただし、暗黙的なデータ型の変換により、見かけ上は互換性のない列を結合できる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="85799-115">However, there may be cases where implicit data type conversions can join seemingly incompatible columns will work.</span></span>  
    >   
    >  <span data-ttu-id="85799-116">[クエリおよびビュー デザイナー](query-and-view-designer-tools-visual-database-tools.md) では、結合の作成に使用した列のデータ型がチェックされることはありません。ただしデータ型に互換性がない場合、クエリの実行時にデータベースによってエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="85799-116">The [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) will not check the data types of the columns you use to create a join, but when you execute the query, the database will display an error if the data types are not compatible.</span></span>  
  
3.  <span data-ttu-id="85799-117">最初のテーブル ウィンドウの 2 番目の結合列の名前をドラッグし、2 番目のテーブル ウィンドウの関連する列にドロップします。</span><span class="sxs-lookup"><span data-stu-id="85799-117">Drag the name of the second join column in the first table window and drop it onto the related column in the second table window.</span></span>  
  
4.  <span data-ttu-id="85799-118">2 つのテーブルに結合列の対を追加するたびに、手順 3. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="85799-118">Repeat step 3 for each additional pair of join columns in the two tables.</span></span>  
  
5.  <span data-ttu-id="85799-119">クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="85799-119">Run the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85799-120">参照</span><span class="sxs-lookup"><span data-stu-id="85799-120">See Also</span></span>  
 [<span data-ttu-id="85799-121">結合を使用したクエリ (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="85799-121">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
