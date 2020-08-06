---
title: クエリへのテーブルの追加 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting tables
- adding tables
- queries [SQL Server], tables
ms.assetid: 6551aa7e-31a1-4636-852a-819bc53d658b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 572002bc913cc9916a75ce2b16c12064452d250f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641396"
---
# <a name="add-tables-to-queries-visual-database-tools"></a><span data-ttu-id="81e54-102">クエリへのテーブルの追加 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="81e54-102">Add Tables to Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="81e54-103">クエリを作成するとき、データを取得する基となるのは、テーブルまたはテーブル構造オブジェクト (ビューおよび特定のユーザー定義関数など) です。</span><span class="sxs-lookup"><span data-stu-id="81e54-103">When you create a query, you are retrieving data from a table or other objects structured like tables - views and certain user-defined functions.</span></span> <span data-ttu-id="81e54-104">クエリでこれらのオブジェクトを処理するには、 **ダイアグラム ペイン**にオブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="81e54-104">To work with any of these objects in your query, you add them to the **Diagram Pane**.</span></span>  
  
### <a name="to-add-a-table-or-table-valued-object-to-a-query"></a><span data-ttu-id="81e54-105">テーブルまたはテーブル値オブジェクトをクエリに追加するには</span><span class="sxs-lookup"><span data-stu-id="81e54-105">To add a table or table-valued object to a query</span></span>  
  
1.  <span data-ttu-id="81e54-106">クエリおよびビュー デザイナーの **ダイアグラム ペイン** で、背景を右クリックして、ショートカット メニューの **[テーブルの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81e54-106">In the **Diagram pane** of the Query and View Designer, right-click the background and choose **Add Table** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="81e54-107">**[テーブルの追加]** ダイアログ ボックスで、クエリに追加するオブジェクトの種類に相当するタブを選択します。</span><span class="sxs-lookup"><span data-stu-id="81e54-107">In the **Add Table** dialog box, select the tab for the type of object you want to add to the query.</span></span>  
  
3.  <span data-ttu-id="81e54-108">アイテムのリストで、追加する各アイテムをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="81e54-108">In the list of items, double-click each item you want to add.</span></span>  
  
4.  <span data-ttu-id="81e54-109">アイテムの追加が完了したら、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81e54-109">When you finish adding items, click **Close**.</span></span>  
  
     <span data-ttu-id="81e54-110">クエリおよびビュー デザイナーによって、 **ダイアグラム ペイン**、 **抽出条件ペイン**、および **SQL ペイン** が適宜更新されます。</span><span class="sxs-lookup"><span data-stu-id="81e54-110">The Query and View Designer updates the **Diagram Pane**, **Criteria Pane**, and **SQL Pane** accordingly.</span></span>  
  
 <span data-ttu-id="81e54-111">SQL ペインのステートメントでテーブルおよびビューを参照すると、テーブルおよびビューはクエリに自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="81e54-111">Tables and views are automatically added to the query when you reference them in the statement in the SQL pane.</span></span>  
  
 <span data-ttu-id="81e54-112">テーブルまたはテーブル値オブジェクトに対して十分なアクセス権がない場合、またはプロバイダーがこれらのオブジェクトに関する情報を返すことができない場合、クエリおよびビュー デザイナーにはこれらのオブジェクトのデータ列が表示されません。</span><span class="sxs-lookup"><span data-stu-id="81e54-112">The Query and View Designer will not display data columns for a table or table-structured object if you do not have sufficient access rights to it or if the provider cannot return information about it.</span></span> <span data-ttu-id="81e54-113">この場合、テーブルまたはテーブル値オブジェクトのタイトル バーおよび [\* (すべての列)] チェック ボックスだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="81e54-113">In such cases, only a title bar and the \* (All Columns) check box are displayed for the table or table-valued object.</span></span>  
  
### <a name="to-add-an-existing-query-to-a-new-query"></a><span data-ttu-id="81e54-114">新しいクエリに既存のクエリを追加するには</span><span class="sxs-lookup"><span data-stu-id="81e54-114">To add an existing query to a new query</span></span>  
  
1.  <span data-ttu-id="81e54-115">作成する新しいクエリに **SQL ペイン** が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="81e54-115">Make sure the **SQL Pane** is displayed in the new query you are creating.</span></span>  
  
2.  <span data-ttu-id="81e54-116">**SQL ペイン**で、FROM の後に () (かっこ) を入力します。</span><span class="sxs-lookup"><span data-stu-id="81e54-116">In the **SQL Pane**, type a right and left parentheses () after the word FROM.</span></span>  
  
3.  <span data-ttu-id="81e54-117">既存のクエリをクエリ デザイナーで開きます。</span><span class="sxs-lookup"><span data-stu-id="81e54-117">Open the Query Designer for the existing query.</span></span> <span data-ttu-id="81e54-118">この時点で 2 つのクエリ デザイナーが開いています。</span><span class="sxs-lookup"><span data-stu-id="81e54-118">(You now have two Query Designers open.)</span></span>  
  
4.  <span data-ttu-id="81e54-119">新しい外部クエリに含める既存のクエリ、つまり内部クエリの **SQL ペイン** を表示します。</span><span class="sxs-lookup"><span data-stu-id="81e54-119">Display the **SQL Pane** for the inner query - the existing query you are including in the new, outer query.</span></span>  
  
5.  <span data-ttu-id="81e54-120">**SQL ペイン**のすべてのテキストを選択し、クリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="81e54-120">Select all the text in the **SQL Pane**, and copy it to the Clipboard.</span></span>  
  
6.  <span data-ttu-id="81e54-121">新しいクエリの **SQL ペイン** の中をクリックし、追加したかっこの間にカーソルを移動し、クリップボードの内容を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="81e54-121">Click in the **SQL Pane** of the new query, situate the cursor between the parentheses you added, and paste the contents of the Clipboard.</span></span>  
  
7.  <span data-ttu-id="81e54-122">**SQL ペイン**の中で、右かっこの後に別名を追加します。</span><span class="sxs-lookup"><span data-stu-id="81e54-122">Still in the **SQL Pane**, add an alias after the right parenthesis.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e54-123">参照</span><span class="sxs-lookup"><span data-stu-id="81e54-123">See Also</span></span>  
 <span data-ttu-id="81e54-124">[Visual Database Tools &#40;テーブルの別名の作成&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="81e54-124">[Create Table Aliases &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="81e54-125">[クエリからテーブルを削除する &#40;Visual Database Tools&#41;](remove-tables-from-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="81e54-125">[Remove Tables from Queries &#40;Visual Database Tools&#41;](remove-tables-from-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="81e54-126">[Visual Database Tools &#40;検索条件を指定し&#41;](specify-search-criteria-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="81e54-126">[Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md) </span></span>  
 <span data-ttu-id="81e54-127">[Visual Database Tools &#40;クエリ結果の概要&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="81e54-127">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="81e54-128">クエリに関する基本操作の実行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="81e54-128">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
