---
title: クエリからのテーブルの削除 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- deleting tables
- removing tables
- dropping tables
- queries [SQL Server], tables
ms.assetid: 8fea0b4f-99b7-4050-8d6f-a97ffb839619
author: stevestein
ms.author: sstein
ms.openlocfilehash: fab5380e13742f3cd289ce17f26ad2e5fb9089ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640318"
---
# <a name="remove-tables-from-queries-visual-database-tools"></a><span data-ttu-id="39c05-102">クエリからのテーブルの削除 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="39c05-102">Remove Tables from Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="39c05-103">クエリからテーブルまたはテーブル値オブジェクトを削除できます。</span><span class="sxs-lookup"><span data-stu-id="39c05-103">You can remove a table - or any table-valued object - from the query.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="39c05-104">テーブルまたはテーブル値オブジェクトを削除しても、現在のクエリから削除されるだけです。データベースからは何も削除されません。</span><span class="sxs-lookup"><span data-stu-id="39c05-104">Removing a table or table-valued object does not delete anything from the database; it only removes it from the current query.</span></span> <span data-ttu-id="39c05-105">データベースからテーブルを削除する方法の詳細については、「[テーブルの削除 &#40;データベースエンジン&#41;](../../relational-databases/tables/delete-tables-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39c05-105">For details about removing a table from a database, see [Delete Tables &#40;Database Engine&#41;](../../relational-databases/tables/delete-tables-database-engine.md).</span></span>  
  
### <a name="to-remove-a-table-or-table-structured-object"></a><span data-ttu-id="39c05-106">テーブルまたはテーブル構造オブジェクトを削除するには</span><span class="sxs-lookup"><span data-stu-id="39c05-106">To remove a table or table-structured object</span></span>  
  
-   <span data-ttu-id="39c05-107">**ダイアグラム ペイン**で、テーブル、ビュー、ユーザー定義関数、シノニム、またはクエリを選択し、Del キーを押すか、オブジェクトを右クリックして、表示されるダイアログ ボックスの **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39c05-107">In the **Diagram Pane**, select the table, view, user-defined function, synonym, or query, and then press DELETE, or right-click the object and then choose **Remove** in the resulting dialog box.</span></span> <span data-ttu-id="39c05-108">同時に複数のオブジェクトを選択して削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="39c05-108">You can select and remove multiple objects at one time.</span></span>  
  
     <span data-ttu-id="39c05-109">または</span><span class="sxs-lookup"><span data-stu-id="39c05-109">-or-</span></span>  
  
-   <span data-ttu-id="39c05-110">**SQL ペイン**でオブジェクトへのすべての参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="39c05-110">Remove all references to the object in the **SQL Pane.**</span></span>  
  
 <span data-ttu-id="39c05-111">テーブルまたはテーブル値オブジェクトを削除すると、クエリおよびビュー デザイナーでは、そのテーブルまたはテーブル値オブジェクトを含む結合が自動的に削除され、これらのオブジェクトの列に対する参照も **SQL ペイン** および **抽出条件ペイン**から自動的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="39c05-111">When you remove a table or table-valued object, the Query and View Designer automatically removes joins that involve that table or table-valued object and removes references to the object's columns in the **SQL Pane** and **Criteria Pane**.</span></span> <span data-ttu-id="39c05-112">ただし、オブジェクトを含む複合式がクエリに含まれる場合、オブジェクトに対する参照がすべて削除されるまで、オブジェクトが自動的に削除されることはありません。</span><span class="sxs-lookup"><span data-stu-id="39c05-112">However, if the query contains complex expressions involving the object, the object is not automatically removed until all references to it are removed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39c05-113">参照</span><span class="sxs-lookup"><span data-stu-id="39c05-113">See Also</span></span>  
 <span data-ttu-id="39c05-114">[Visual Database Tools &#40;クエリにテーブルを追加する&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="39c05-114">[Add Tables to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="39c05-115">[Visual Database Tools &#40;テーブルの別名の作成&#41;](create-table-aliases-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="39c05-115">[Create Table Aliases &#40;Visual Database Tools&#41;](create-table-aliases-visual-database-tools.md) </span></span>  
 <span data-ttu-id="39c05-116">[Visual Database Tools &#40;検索条件を指定し&#41;](specify-search-criteria-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="39c05-116">[Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md) </span></span>  
 <span data-ttu-id="39c05-117">[Visual Database Tools &#40;クエリ結果の概要&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="39c05-117">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="39c05-118">クエリに関する基本操作の実行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="39c05-118">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
