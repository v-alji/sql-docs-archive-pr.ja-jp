---
title: クエリの作成 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], creating
ms.assetid: 696a080d-848f-44d3-a918-e29bafaab85a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 52392adff03b27e1c4c19f354bc62c350cccf17a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631457"
---
# <a name="create-queries-visual-database-tools"></a><span data-ttu-id="be45b-102">クエリの作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="be45b-102">Create Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="be45b-103">クエリを使用すると、データベース内のテーブルおよびビューからデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="be45b-103">Queries allow you to retrieve data from the tables and views in your database.</span></span> <span data-ttu-id="be45b-104">クエリの作成と処理には、 **クエリおよびビュー デザイナー**を使用します。クエリおよびビュー デザイナーは、 [ダイアグラム ペイン](visual-database-tools.md)、 [SQL ペイン](sql-pane-visual-database-tools.md)、 [抽出条件ペイン](criteria-pane-visual-database-tools.md)、および [結果ペイン](results-pane-visual-database-tools.md)の 4 つのペインで構成されています。</span><span class="sxs-lookup"><span data-stu-id="be45b-104">You create and work with queries in **Query and View Designer**, which is composed of four panes: the [Diagram Pane](visual-database-tools.md), the [SQL Pane](sql-pane-visual-database-tools.md), the [Criteria Pane](criteria-pane-visual-database-tools.md), and the [Results Pane](results-pane-visual-database-tools.md).</span></span>  
  
### <a name="to-create-a-new-query"></a><span data-ttu-id="be45b-105">新しいクエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="be45b-105">To create a new query</span></span>  
  
1.  <span data-ttu-id="be45b-106">**オブジェクト エクスプローラー**で、問い合わせるデータベースの **[テーブル]** ノードを展開し、</span><span class="sxs-lookup"><span data-stu-id="be45b-106">In **Object Explorer**, expand the **Tables** node for the database you want to query.</span></span> <span data-ttu-id="be45b-107">問い合わせるテーブルを右クリックして、 **[テーブルを開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be45b-107">Right-click the table you want to query and click **Open Table**.</span></span>  
  
2.  <span data-ttu-id="be45b-108">クエリにテーブルを追加するには、[クエリ デザイナー] メニューの **[テーブルの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be45b-108">To add more tables to the query, on the Query Designer menu, select **Add Table**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="be45b-109">**ダイアグラム**ペイン、 **SQL**ペイン、 **抽出条件**ペイン、または **結果ペイン** が表示されない場合は、[クエリ デザイナー] メニューの **[ペイン]** をポイントして、開くペインをクリックします。</span><span class="sxs-lookup"><span data-stu-id="be45b-109">If you do not see the **Diagram**, **SQL**, **Criteria**, or **Results** panes, from the Query Designer menu, point to **Pane** and click the pane you want to open.</span></span>  
  
3.  <span data-ttu-id="be45b-110">**[テーブルの追加]** ダイアログ ボックスで、問い合わせるテーブルを選択し、テーブルごとに **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be45b-110">In the **Add Table** dialog box, select the tables you want to query and click **Add** for each one.</span></span>  
  
4.  <span data-ttu-id="be45b-111">問い合わせるすべてのテーブルを追加したら、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be45b-111">Once you have added all the tables you want to query, click **Close**.</span></span>  
  
     <span data-ttu-id="be45b-112">後でテーブルを追加するには、 **ダイアグラム** ペインの空の領域を右クリックし、ショートカット メニューの **[テーブルの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be45b-112">To add more tables later, right-click the open space in the **Diagram** pane and from the shortcut menu click **Add Table**.</span></span>  
  
5.  <span data-ttu-id="be45b-113">**ダイアグラム ペイン**で、問い合わせる各列のテーブル値オブジェクトのボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="be45b-113">In the **Diagram Pane**, check the boxes in the table-valued objects for each column you want to query.</span></span>  
  
6.  <span data-ttu-id="be45b-114">[クエリ デザイナー] メニューの **[SQL の実行]** をクリックして、クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="be45b-114">From the Query Designer menu, choose **Execute SQL** to run your query.</span></span>  
  
 <span data-ttu-id="be45b-115">より的確な結果を得るために、 **SQL ペイン** で SQL コードを変更するか、 **抽出条件ペイン**で並べ替え順序や列の別名などのオプションを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="be45b-115">To further refine your query, you can change the SQL code in the **SQL Pane** or choose options such as sort order and column aliases in the **Criteria Pane.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be45b-116">参照</span><span class="sxs-lookup"><span data-stu-id="be45b-116">See Also</span></span>  
 <span data-ttu-id="be45b-117">[Visual Database Tools&#41;&#40;クエリを保存する](save-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="be45b-117">[Save Queries &#40;Visual Database Tools&#41;](save-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="be45b-118">[Visual Database Tools &#40;クエリの種類&#41;](types-of-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="be45b-118">[Types of Queries &#40;Visual Database Tools&#41;](types-of-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="be45b-119">[Visual Database Tools &#40;検索条件を指定し&#41;](specify-search-criteria-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="be45b-119">[Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md) </span></span>  
 <span data-ttu-id="be45b-120">[Visual Database Tools &#40;クエリ結果の概要&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="be45b-120">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="be45b-121">クエリに関する基本操作の実行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="be45b-121">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
