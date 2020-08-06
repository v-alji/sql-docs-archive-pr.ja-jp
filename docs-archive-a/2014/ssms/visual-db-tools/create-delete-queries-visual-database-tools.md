---
title: 削除クエリの作成 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- row removal [SQL Server], Delete query
- Delete query
- queries [SQL Server], types
- removing rows
- removing data
- data deletions [SQL Server]
- deleting rows
- deleting data
ms.assetid: 0db3af43-1ec4-48c8-b769-2bb9c76d3434
author: stevestein
ms.author: sstein
ms.openlocfilehash: a76c3aaef623365e419f40f3058308f6217d75d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645290"
---
# <a name="create-delete-queries-visual-database-tools"></a><span data-ttu-id="7791f-102">削除クエリの作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="7791f-102">Create Delete Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="7791f-103">削除クエリを使用すると、テーブル内の行をすべて削除できます。</span><span class="sxs-lookup"><span data-stu-id="7791f-103">You can delete all rows in a table by using a Delete query.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7791f-104">テーブルから行をすべて削除すると、テーブルのデータは削除されますが、テーブル自体は削除されません。</span><span class="sxs-lookup"><span data-stu-id="7791f-104">Deleting all rows from a table clears the data in the table but does not delete the table itself.</span></span> <span data-ttu-id="7791f-105">データベースからテーブルを削除するには、オブジェクト エクスプローラーでテーブルを右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7791f-105">To delete a table from a database, right-click the table in Object Explorer and click **Delete**.</span></span>  
  
 <span data-ttu-id="7791f-106">削除クエリを作成すると、行の削除に使用できるオプションが抽出条件ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7791f-106">When you create a Delete query, the Criteria pane changes to reflect the options available for deleting rows.</span></span> <span data-ttu-id="7791f-107">削除クエリではデータが表示されないため、[出力]、[並べ替え]、および [並べ替え順序] の各列は削除されます。</span><span class="sxs-lookup"><span data-stu-id="7791f-107">Because you do not display data in a Delete query, the Output, Sort By, and Sort Order columns are removed.</span></span> <span data-ttu-id="7791f-108">さらに、テーブルまたはテーブル値オブジェクトを示す四角形内の列名の横のチェック ボックスが削除されます。列を個別に指定して削除することはできないためです。</span><span class="sxs-lookup"><span data-stu-id="7791f-108">In addition, the check boxes next to the column names in the rectangle representing the table or table-valued object are removed because you cannot specify individual columns to delete.</span></span>  
  
 <span data-ttu-id="7791f-109">クエリおよびビュー デザイナーで削除できない行がある場合、いずれの行も削除されず、データベースから削除できない情報を含む行を示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7791f-109">If the Query and View Designer can't delete one or more of the rows none of them will be deleted and you will receive a message telling you which row(s) contain information that can't be deleted from the database.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="7791f-110">削除クエリの実行アクションを元に戻すことはできません。</span><span class="sxs-lookup"><span data-stu-id="7791f-110">You cannot undo the action of executing a Delete query.</span></span> <span data-ttu-id="7791f-111">念のため、削除クエリを実行する前にデータをバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="7791f-111">As a precaution, back up your data before executing a Delete query.</span></span>  
  
### <a name="to-create-a-delete-query"></a><span data-ttu-id="7791f-112">削除クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="7791f-112">To create a Delete query</span></span>  
  
1.  <span data-ttu-id="7791f-113">行を削除するテーブルをダイアグラム ペインに追加します。</span><span class="sxs-lookup"><span data-stu-id="7791f-113">Add the table to delete rows from to the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="7791f-114">**[クエリ デザイナー]** メニューの **[クエリ タイプの変更]** をポイントし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7791f-114">From the **Query Designer** menu, point to **Change Type**, and then click **Delete**.</span></span> <span data-ttu-id="7791f-115">**メモ** 削除クエリを開始した時点でダイアグラム ペインに複数のテーブルが表示されている場合、行を削除するテーブルの名前を要求する [[テーブルの削除] ダイアログ ボックス](visual-database-tools.md) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7791f-115">**Note** If more than one table is displayed in the Diagram pane when you start the Delete query, the Query and View Designer displays the [Delete Table Dialog Box](visual-database-tools.md) to prompt you for the name of the table to delete rows from.</span></span>  
  
 <span data-ttu-id="7791f-116">削除クエリを実行しても、 [結果ペイン](results-pane-visual-database-tools.md)には結果が表示されません。</span><span class="sxs-lookup"><span data-stu-id="7791f-116">When you execute the Delete query, no results are reported in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="7791f-117">代わりに、削除された行数を示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7791f-117">Instead, a message appears indicating how many rows were deleted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7791f-118">参照</span><span class="sxs-lookup"><span data-stu-id="7791f-118">See Also</span></span>  
 <span data-ttu-id="7791f-119">[Visual Database Tools &#40;サポートされているクエリの種類&#41;](supported-query-types-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="7791f-119">[Supported Query Types &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="7791f-120">クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="7791f-120">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
