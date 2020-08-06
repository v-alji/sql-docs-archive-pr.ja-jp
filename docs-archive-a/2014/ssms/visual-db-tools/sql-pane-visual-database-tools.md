---
title: SQL ペイン (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Query Designer [SQL Server], SQL pane
- View Designer, SQL pane
- SQL pane [Visual Database Tools]
ms.assetid: dbabab18-0614-415b-a2ef-9bcd0d320d5c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3a87ec1d5517852fefb152e0ec7b3165fa32988b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711398"
---
# <a name="sql-pane-visual-database-tools"></a><span data-ttu-id="50533-102">SQL ペイン (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="50533-102">SQL Pane (Visual Database Tools)</span></span>
  <span data-ttu-id="50533-103">SQL ペインでは、任意の SQL ステートメントを作成できます。抽出条件ペインおよびダイアグラム ペインでも SQL ステートメントを作成できますが、どちらの場合も SQL ステートメントは SQL ペインに作成されます。</span><span class="sxs-lookup"><span data-stu-id="50533-103">You can use the SQL pane to create your own SQL statement, or you can use the Criteria pane and Diagram pane to create the statement, in which case the SQL statements will be created in the SQL pane.</span></span> <span data-ttu-id="50533-104">クエリを作成すると、SQL ペインは自動的に更新され、読みやすいように書式が変更されます。</span><span class="sxs-lookup"><span data-stu-id="50533-104">As you build your query, the SQL pane automatically updates and reformats for easy readability.</span></span>  
  
 <span data-ttu-id="50533-105">SQL ペインを開くには、まずクエリおよびビュー デザイナーを開きます。これには、サーバー エクスプローラーでデータベース オブジェクトを選択し、 **[データベース]** メニューの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50533-105">To open the SQL pane, first open Query and View Designer (with a database object selected in Server Explorer, from the **Database** menu, click **New Query**).</span></span> <span data-ttu-id="50533-106">次に、 **[クエリ デザイナー]** メニューの **[ペイン]** をポイントし、 **[SQL]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50533-106">Then from the **Query Designer** menu point to **Pane** and click **SQL**.</span></span>  
  
 <span data-ttu-id="50533-107">SQL ペインでは、次の作業を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="50533-107">In the SQL pane you can:</span></span>  
  
-   <span data-ttu-id="50533-108">SQL ステートメントを入力し、新しいクエリを作成する。</span><span class="sxs-lookup"><span data-stu-id="50533-108">Create new queries by entering SQL statements.</span></span>  
  
-   <span data-ttu-id="50533-109">ダイアグラム ペインおよび抽出条件ペインで行った設定に基づいてクエリおよびビュー デザイナーが作成した SQL ステートメントを変更する。</span><span class="sxs-lookup"><span data-stu-id="50533-109">Modify the SQL statement created by the Query and View Designer based on settings you make in the Diagram and Criteria panes.</span></span>  
  
-   <span data-ttu-id="50533-110">使用しているデータベース固有の機能を利用するステートメントを入力する。</span><span class="sxs-lookup"><span data-stu-id="50533-110">Enter statements that take advantage of features specific to the database you are using.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50533-111">使用しているデータベースでデータベース オブジェクトを識別する規則を確認してください。</span><span class="sxs-lookup"><span data-stu-id="50533-111">Be sure you know the rules for identifying database objects in the database you are using.</span></span> <span data-ttu-id="50533-112">詳細については、使用しているデータベース管理システムのマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="50533-112">For details, see the documentation for your database management system.</span></span>  
  
## <a name="statements-in-the-sql-pane"></a><span data-ttu-id="50533-113">SQL ペインにステートメントを入力する</span><span class="sxs-lookup"><span data-stu-id="50533-113">Statements in the SQL Pane</span></span>  
 <span data-ttu-id="50533-114">SQL ペインでは、現在のクエリを直接編集できます。</span><span class="sxs-lookup"><span data-stu-id="50533-114">You can edit the current query directly in the SQL pane.</span></span> <span data-ttu-id="50533-115">他のペインに移動すると、クエリおよびビュー デザイナーによってステートメントの書式が自動的に設定され、ステートメントに合わせてダイアグラム ペインと抽出条件ペインが変更されます。</span><span class="sxs-lookup"><span data-stu-id="50533-115">When you move to another pane, the Query and View Designer automatically formats your statement, and then changes the Diagram and Criteria panes to match your statement.</span></span>  
  
 <span data-ttu-id="50533-116">ダイアグラム ペインおよび抽出条件ペインが表示されていて、これらのペインでステートメントを表示できない場合、クエリおよびビュー デザイナーはエラーを表示します。この場合、次のいずれかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="50533-116">If your statement cannot be represented in the Diagram and Criteria panes, and if those panes are visible, Query and View Designer displays an error and then offers you two choices:</span></span>  
  
-   <span data-ttu-id="50533-117">ダイアグラム ペインおよび抽出条件ペインでステートメントを表示できなくても無視して作業を続ける。</span><span class="sxs-lookup"><span data-stu-id="50533-117">Ignore that the statement can not be represented in the Diagram and Criteria panes.</span></span>  
  
-   <span data-ttu-id="50533-118">表示できない変更を元に戻して、その前に変更を加えた後の SQL ステートメントに戻す。</span><span class="sxs-lookup"><span data-stu-id="50533-118">Undo the change that can not be represented and revert to the most recent version of the SQL statement.</span></span>  
  
 <span data-ttu-id="50533-119">ダイアグラム ペインおよび抽出条件ペインでステートメントを表示できなくても無視して作業を続けることを選択した場合、これらのペインは、SQL ペインの内容を反映できないことを示すため、淡色表示されます。</span><span class="sxs-lookup"><span data-stu-id="50533-119">If you choose to ignore that the statement can not be represented in the Diagram and Criteria panes, the Query and View Designer dims the other panes to indicate that they no longer reflect the contents of the SQL pane.</span></span>  
  
 <span data-ttu-id="50533-120">ステートメントの編集と実行は、他の SQL ステートメントと同じように実行できます。</span><span class="sxs-lookup"><span data-stu-id="50533-120">You can continue to edit the statement and execute it as you would any SQL statement.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50533-121">SQL ステートメントを入力した後に、ダイアグラム ペインと抽出条件ペインでクエリを変更した場合、クエリおよびビュー デザイナーでは SQL ステートメントのリビルドおよび再表示が行われます。</span><span class="sxs-lookup"><span data-stu-id="50533-121">If you enter an SQL statement, but then make further changes to the query by changing the Diagram and Criteria panes, the Query and View Designer rebuilds and redisplays the SQL statement.</span></span> <span data-ttu-id="50533-122">この処理の結果、最初に入力した SQL ステートメントとは異なるステートメントが作成されることがあります。ただし、ステートメントの実行結果は常に同じになります。</span><span class="sxs-lookup"><span data-stu-id="50533-122">In some cases, this action results in an SQL statement that is constructed differently from the one you originally entered (though it will always yield the same results).</span></span> <span data-ttu-id="50533-123">この現象は、AND または OR で連結された複数の句を含む検索条件がある場合によく発生します。</span><span class="sxs-lookup"><span data-stu-id="50533-123">This difference is particularly likely when you are working with search conditions that involve several clauses linked with AND and OR.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50533-124">参照</span><span class="sxs-lookup"><span data-stu-id="50533-124">See Also</span></span>  
 <span data-ttu-id="50533-125">[Visual Database Tools &#40;クエリの作成&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="50533-125">[Create Queries &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="50533-126">[Visual Database Tools &#40;クエリの実行&#41;](run-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="50533-126">[Run Queries &#40;Visual Database Tools&#41;](run-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="50533-127">[クエリおよびビューのデザイン方法に関するトピック &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="50533-127">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 <span data-ttu-id="50533-128">[ダイアグラムペイン &#40;Visual Database Tools&#41;](diagram-pane-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="50533-128">[Diagram Pane &#40;Visual Database Tools&#41;](diagram-pane-visual-database-tools.md) </span></span>  
 <span data-ttu-id="50533-129">[抽出条件ペイン &#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="50533-129">[Criteria Pane &#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="50533-130">結果ペイン (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="50533-130">Results Pane &#40;Visual Database Tools&#41;</span></span>](results-pane-visual-database-tools.md)  
  
  
