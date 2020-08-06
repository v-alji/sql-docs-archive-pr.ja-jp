---
title: 自己結合の手動作成 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- self-joins
- manual joins [SQL Server]
- joins [SQL Server], self
ms.assetid: 910ed516-cb84-481b-95d0-cba3e89afdba
author: stevestein
ms.author: sstein
ms.openlocfilehash: 31e125fdfe0f7f285ea679cfe85356d1aa10353a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641957"
---
# <a name="create-self-joins-manually-visual-database-tools"></a><span data-ttu-id="615ee-102">自己結合の手動作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="615ee-102">Create Self-Joins Manually (Visual Database Tools)</span></span>
  <span data-ttu-id="615ee-103">データベースでテーブルに再帰リレーションシップが設定されていなくても、テーブルをテーブル自身に結合できます。</span><span class="sxs-lookup"><span data-stu-id="615ee-103">You can join a table to itself even if the table does not have a reflexive relationship in the database.</span></span> <span data-ttu-id="615ee-104">たとえば、自己結合を使用して、同じ市に住む著者の組を検索できます。</span><span class="sxs-lookup"><span data-stu-id="615ee-104">For example, you can use a self-join to find pairs of authors living in the same city.</span></span>  
  
 <span data-ttu-id="615ee-105">他の結合と同様に、自己結合にも少なくとも 2 つのテーブルが必要です。</span><span class="sxs-lookup"><span data-stu-id="615ee-105">As with any join, a self-join requires at least two tables.</span></span> <span data-ttu-id="615ee-106">他の結合と異なる点は、クエリに他のテーブルを追加する代わりに、同じテーブルの 2 番目のインスタンスを追加する点です。</span><span class="sxs-lookup"><span data-stu-id="615ee-106">The difference is that, instead of adding a second table to the query, you add a second instance of the same table.</span></span> <span data-ttu-id="615ee-107">このように、テーブルの最初のインスタンスの列と 2 番目のインスタンスの同じ列を比較することによって、列の値を相互に比較できます。</span><span class="sxs-lookup"><span data-stu-id="615ee-107">That way, you can compare a column in the first instance of the table to the same column in the second instance, which allows you to compare the values in a column to each other.</span></span> <span data-ttu-id="615ee-108">テーブルの 2 番目のインスタンスには、 [クエリおよびビュー デザイナー](visual-database-tools.md) によって別名が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="615ee-108">The [Query and View Designer](visual-database-tools.md) assigns an alias to the second instance of the table.</span></span>  
  
 <span data-ttu-id="615ee-109">たとえば、自己結合を作成してバークレイに住む著者の組み合わせをすべて検索する場合は、テーブルの最初のインスタンスの `city` 列と 2 番目のインスタンスの `city` 列とを比較します。</span><span class="sxs-lookup"><span data-stu-id="615ee-109">For example, if you are creating a self-join to find all pairs of authors within Berkeley, you compare the `city` column in the first instance of the table against the `city` column in the second instance.</span></span> <span data-ttu-id="615ee-110">作成したクエリは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="615ee-110">The resulting query might look like the following:</span></span>  
  
```  
SELECT   
      authors.au_fname,   
      authors.au_lname,   
      authors1.au_fname AS Expr2,   
      authors1.au_lname AS Expr3  
   FROM   
      authors   
         INNER JOIN  
         authors authors1   
            ON authors.city   
             = authors1.city  
   WHERE  
      authors.city = 'Berkeley'  
```  
  
 <span data-ttu-id="615ee-111">自己結合の作成には、複数の結合条件が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="615ee-111">Creating a self-join often requires multiple join conditions.</span></span> <span data-ttu-id="615ee-112">その理由を理解するために、上記のクエリの結果を検討してみます。</span><span class="sxs-lookup"><span data-stu-id="615ee-112">To understand why, consider the result of the preceding query:</span></span>  
  
```  
Cheryl Carson       Cheryl Carson  
Abraham Bennet      Abraham Bennet  
Cheryl Carson       Abraham Bennet  
Abraham Bennet      Cheryl Carson  
```  
  
 <span data-ttu-id="615ee-113">最初の行は、Cheryl Carson が Cheryl Carson と同じ市に住んでいることを示すため、意味がありません。</span><span class="sxs-lookup"><span data-stu-id="615ee-113">The first row is useless; it indicates that Cheryl Carson lives in the same city as Cheryl Carson.</span></span> <span data-ttu-id="615ee-114">2 番目の行も同様に役に立ちません。</span><span class="sxs-lookup"><span data-stu-id="615ee-114">The second row is equally useless.</span></span> <span data-ttu-id="615ee-115">これらの無意味なデータを削除するために、2 つの著者名が違う著者を示す場合だけ結果行を残すように条件を追加します。</span><span class="sxs-lookup"><span data-stu-id="615ee-115">To eliminate this useless data, you add another condition retaining only those result rows in which the two author names describe different authors.</span></span> <span data-ttu-id="615ee-116">作成したクエリは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="615ee-116">The resulting query might look like this:</span></span>  
  
```  
SELECT   
      authors.au_fname,   
      authors.au_lname,   
      authors1.au_fname AS Expr2,   
      authors1.au_lname AS Expr3  
   FROM   
      authors   
         INNER JOIN  
         authors authors1   
            ON authors.city   
             = authors1.city  
            AND authors.au_id  
             <> authors1.au_id  
   WHERE  
      authors.city = 'Berkeley'  
```  
  
 <span data-ttu-id="615ee-117">結果セットは、次のように改善されます。</span><span class="sxs-lookup"><span data-stu-id="615ee-117">The result set is improved:</span></span>  
  
```  
Cheryl Carson       Abraham Bennet  
Abraham Bennet      Cheryl Carson  
```  
  
 <span data-ttu-id="615ee-118">しかしこの 2 つの結果行も冗長です。</span><span class="sxs-lookup"><span data-stu-id="615ee-118">But the two result rows are redundant.</span></span> <span data-ttu-id="615ee-119">最初の行は、Carson が Bennet と同じ市に住んでいることを示し、2 番目の行は、Bennet が Carson と同じ市に住んでいることを示しています。</span><span class="sxs-lookup"><span data-stu-id="615ee-119">The first says Carson lives in the same city as Bennet, and the second says the Bennet lives in the same city as Carson.</span></span> <span data-ttu-id="615ee-120">このような冗長を避けるには、2 番目の結合条件を "等しくない" から "小なり" に変更します。</span><span class="sxs-lookup"><span data-stu-id="615ee-120">To eliminate this redundancy, you can alter the second join condition from "not equals" to "less than."</span></span> <span data-ttu-id="615ee-121">作成したクエリは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="615ee-121">The resulting query might look like this:</span></span>  
  
```  
SELECT   
      authors.au_fname,   
      authors.au_lname,   
      authors1.au_fname AS Expr2,   
      authors1.au_lname AS Expr3  
   FROM   
      authors   
         INNER JOIN  
         authors authors1   
            ON authors.city   
             = authors1.city  
            AND authors.au_id  
             < authors1.au_id  
   WHERE  
      authors.city = 'Berkeley'  
```  
  
 <span data-ttu-id="615ee-122">結果セットは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="615ee-122">And the result set looks like this:</span></span>  
  
```  
Cheryl Carson       Abraham Bennet  
```  
  
### <a name="to-create-a-self-join-manually"></a><span data-ttu-id="615ee-123">自己結合を手動作成するには</span><span class="sxs-lookup"><span data-stu-id="615ee-123">To create a self-join manually</span></span>  
  
1.  <span data-ttu-id="615ee-124">処理するテーブルまたはテーブル値オブジェクトを [ダイアグラム ペイン](diagram-pane-visual-database-tools.md) に追加します。</span><span class="sxs-lookup"><span data-stu-id="615ee-124">Add to the [Diagram pane](diagram-pane-visual-database-tools.md) the table or table-valued object you want to work with.</span></span>  
  
2.  <span data-ttu-id="615ee-125">同じテーブルを再度追加します。ダイアグラム ペインに同じテーブルまたはテーブル値オブジェクトが 2 つ表示されます。</span><span class="sxs-lookup"><span data-stu-id="615ee-125">Add the same table again, so that the Diagram pane shows the same table or table-valued object twice within the Diagram pane.</span></span>  
  
     <span data-ttu-id="615ee-126">2 番目のインスタンスには、テーブル名の後に順序番号が付加された別名が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="615ee-126">The Query and View Designer assigns an alias to the second instance by adding a sequential number to the table name.</span></span> <span data-ttu-id="615ee-127">さらに、ダイアグラム ペインの中のテーブルまたはテーブル値オブジェクトの 2 つのインスタンスの間に結合線が表示されます。</span><span class="sxs-lookup"><span data-stu-id="615ee-127">In addition, the Query and View Designer creates a join line between the two occurrences of the table or table-valued object within the Diagram pane.</span></span>  
  
3.  <span data-ttu-id="615ee-128">結合線を右クリックし、ショートカット メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="615ee-128">Right-click the join line and choose **Properties** from the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="615ee-129">[プロパティ] ウィンドウの **[結合条件と種類]** をクリックし、プロパティの右側の省略記号 **[...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="615ee-129">In the Properties window click **Join Condition and Type** and click the **ellipses (...)** to the right of the property.</span></span>  
  
5.  <span data-ttu-id="615ee-130">[[結合]](join-dialog-box-visual-database-tools.md) ダイアログ ボックスで、主キー間の比較演算子を必要に応じて変更します。</span><span class="sxs-lookup"><span data-stu-id="615ee-130">In the [Join Dialog Box](join-dialog-box-visual-database-tools.md) change the comparison operator between the primary keys as required.</span></span> <span data-ttu-id="615ee-131">たとえば、演算子を小なり (<) に変更できます。</span><span class="sxs-lookup"><span data-stu-id="615ee-131">For example, you might change the operator to less than (<).</span></span>  
  
6.  <span data-ttu-id="615ee-132">テーブルまたはテーブル値オブジェクトの最初のインスタンスにある最初の結合列の名前をドラッグし、2 番目のインスタンスの対応する列にドロップして、追加の結合条件 (たとえば、authors.zip = authors1.zip) を作成します。</span><span class="sxs-lookup"><span data-stu-id="615ee-132">Create the additional join condition (for example, authors.zip = authors1.zip) by dragging the name of the primary join column in the first occurrence of the table or table-valued object and dropping it on the corresponding column in the second occurrence.</span></span>  
  
7.  <span data-ttu-id="615ee-133">出力列、検索条件、並べ替え順序など、クエリの他のオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="615ee-133">Specify other options for the query such as output columns, search conditions, and sort order.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="615ee-134">参照</span><span class="sxs-lookup"><span data-stu-id="615ee-134">See Also</span></span>  
 <span data-ttu-id="615ee-135">[Visual Database Tools &#40;自動的に自己結合を作成&#41;](create-self-joins-automatically-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="615ee-135">[Create Self-Joins Automatically &#40;Visual Database Tools&#41;](create-self-joins-automatically-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="615ee-136">結合を使用したクエリ (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="615ee-136">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
