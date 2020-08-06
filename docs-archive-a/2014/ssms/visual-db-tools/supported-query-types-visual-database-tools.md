---
title: サポートされるクエリの種類 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Delete query
- queries [SQL Server], types
- Update query
- Query Designer [SQL Server], query types
- Criteria pane
- Insert Values query
- Select query
- Make Table query
- Insert Results query
- Diagram pane [Visual Database Tools]
- View Designer, query types
ms.assetid: 72b9116c-c128-4078-a78d-257a2955a3f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: b00b7018fc6d0b631696811bd1870e09842b4162
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720709"
---
# <a name="supported-query-types-visual-database-tools"></a><span data-ttu-id="2d1d3-102">サポートされるクエリの種類 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="2d1d3-102">Supported Query Types (Visual Database Tools)</span></span>
  <span data-ttu-id="2d1d3-103">[クエリおよびビュー デザイナー](visual-database-tools.md)のダイアグラム ペインと抽出条件ペイン (グラフィカルなペイン) では、次のクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2d1d3-103">You can create the following types of queries in the Diagram and Criteria panes (the graphical panes) of the [Query and View Designer](visual-database-tools.md):</span></span>  
  
-   <span data-ttu-id="2d1d3-104">**選択クエリ** 1 つ以上のテーブルまたはビューからデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="2d1d3-104">**Select query** Retrieves data from one or more tables or views.</span></span> <span data-ttu-id="2d1d3-105">このクエリは、SQL の SELECT ステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="2d1d3-105">This type of query creates an SQL SELECT statement.</span></span>  
  
-   <span data-ttu-id="2d1d3-106">**結果の挿入クエリ** あるテーブルの既存の行を別のテーブルにコピーして、新しい行を作成します。または、同じテーブルに行をコピーして新しい行を作成します。</span><span class="sxs-lookup"><span data-stu-id="2d1d3-106">**Insert Results** Creates new rows by copying existing rows from one table into another, or into the same table as new rows.</span></span> <span data-ttu-id="2d1d3-107">このクエリは、SQL の INSERT INTO...SELECT ステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="2d1d3-107">This type of query creates an SQL INSERT INTO...SELECT statement.</span></span>  
  
-   <span data-ttu-id="2d1d3-108">**値の挿入クエリ** 新しい行を作成し、指定された列に値を挿入します。</span><span class="sxs-lookup"><span data-stu-id="2d1d3-108">**Insert Values** Creates a new row and inserts values into specified columns.</span></span> <span data-ttu-id="2d1d3-109">このクエリは、SQL の INSERT INTO...VALUES ステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="2d1d3-109">This type of query creates an SQL INSERT INTO...VALUES statement.</span></span>  
  
-   <span data-ttu-id="2d1d3-110">**更新クエリ** テーブル内の 1 つ以上の既存の行にある特定の列の値を変更します。</span><span class="sxs-lookup"><span data-stu-id="2d1d3-110">**Update query** Changes the values of individual columns in one or more existing rows in a table.</span></span> <span data-ttu-id="2d1d3-111">このクエリは、SQL の UPDATE...SET ステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="2d1d3-111">This type of query creates an SQL UPDATE...SET statement.</span></span>  
  
-   <span data-ttu-id="2d1d3-112">**削除クエリ** テーブルから 1 つ以上の行を削除します。</span><span class="sxs-lookup"><span data-stu-id="2d1d3-112">**Delete query** Removes one or more rows from a table.</span></span> <span data-ttu-id="2d1d3-113">このクエリは、SQL の DELETE ステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="2d1d3-113">This type of query creates an SQL DELETE statement.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2d1d3-114">削除クエリは、テーブルから行全体を削除します。</span><span class="sxs-lookup"><span data-stu-id="2d1d3-114">A Delete query removes entire rows from the table.</span></span> <span data-ttu-id="2d1d3-115">特定のデータ列から値を削除する場合は、更新クエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="2d1d3-115">If you want to delete values from individual data columns, use an Update query.</span></span>  
  
-   <span data-ttu-id="2d1d3-116">**テーブルの作成クエリ** 新しいテーブルを作成し、クエリの結果をコピーしてテーブル内に行を作成します。</span><span class="sxs-lookup"><span data-stu-id="2d1d3-116">**Make Table query** Creates a new table and creates rows in it by copying the results of a query into it.</span></span> <span data-ttu-id="2d1d3-117">このクエリは、SQL の SELECT...INTO ステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="2d1d3-117">This type of query creates an SQL SELECT...INTO statement.</span></span>  
  
 <span data-ttu-id="2d1d3-118">クエリを作成するには、グラフィカルなペインを使用する方法だけでなく、UNION クエリなど、任意の SQL ステートメントを SQL ペインに入力して作成する方法があります。</span><span class="sxs-lookup"><span data-stu-id="2d1d3-118">In addition to the queries you can create using the graphical panes, you can enter any SQL statement into the SQL pane, such as Union queries.</span></span>  
  
 <span data-ttu-id="2d1d3-119">グラフィカルなペインで表示できない SQL ステートメントを使用してクエリを作成すると、グラフィカルなペインは淡色表示になります。これは、これらのペインに作成中のクエリが反映されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="2d1d3-119">When you create queries using SQL statements that cannot be represented in the graphical panes, the Query and View Designer dims those panes to indicate that they do not reflect the query you are creating.</span></span> <span data-ttu-id="2d1d3-120">ただし、これらのペインは淡色表示されていてもアクティブ状態なので、多くの場合、ペインに表示されているクエリを変更できます。</span><span class="sxs-lookup"><span data-stu-id="2d1d3-120">However, the dimmed panes are still active and, in many cases, you can make changes to the query in those panes.</span></span> <span data-ttu-id="2d1d3-121">変更の結果、グラフィカルなペインで表示できるクエリになった場合、ペインの淡色表示は解除されます。</span><span class="sxs-lookup"><span data-stu-id="2d1d3-121">If the changes you make result in a query that can be represented in the graphical panes, those panes are no longer dimmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d1d3-122">参照</span><span class="sxs-lookup"><span data-stu-id="2d1d3-122">See Also</span></span>  
 <span data-ttu-id="2d1d3-123">[クエリおよびビューのデザイン方法に関するトピック &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="2d1d3-123">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="2d1d3-124">クエリの種類 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="2d1d3-124">Types of Queries &#40;Visual Database Tools&#41;</span></span>](types-of-queries-visual-database-tools.md)  
  
  
