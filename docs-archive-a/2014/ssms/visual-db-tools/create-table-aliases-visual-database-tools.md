---
title: テーブルの別名の作成 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- table aliases [SQL Server]
- aliases [SQL Server], tables
ms.assetid: 49e61e85-8abf-4ca7-8c70-7e9f8f1078bd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8f9e6269fe6e24e8d98922094e799fbf4b5af584
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641954"
---
# <a name="create-table-aliases-visual-database-tools"></a><span data-ttu-id="9a9bf-102">テーブルの別名の作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9a9bf-102">Create Table Aliases (Visual Database Tools)</span></span>
  <span data-ttu-id="9a9bf-103">別名を使用すると、テーブル名を使った操作が容易になります。</span><span class="sxs-lookup"><span data-stu-id="9a9bf-103">Aliases can make it easier to work with table names.</span></span> <span data-ttu-id="9a9bf-104">別名は、次の場合に使用すると便利です。</span><span class="sxs-lookup"><span data-stu-id="9a9bf-104">Using aliases is helpful when:</span></span>  
  
-   <span data-ttu-id="9a9bf-105">[SQL ペイン](visual-database-tools.md) のステートメントを短くして、読みやすくする場合。</span><span class="sxs-lookup"><span data-stu-id="9a9bf-105">You want to make the statement in the [SQL Pane](visual-database-tools.md) shorter and easier to read.</span></span>  
  
-   <span data-ttu-id="9a9bf-106">クエリでテーブル名を列名の修飾などに頻繁に参照する場合で、クエリの文字数を一定文字数にする場合。</span><span class="sxs-lookup"><span data-stu-id="9a9bf-106">You refer to the table name often in your query - such as in qualifying column names - and want to be sure you stay within a specific character-length limit for your query.</span></span> <span data-ttu-id="9a9bf-107">一部のデータベースでは、クエリの最大文字数が決まっています。</span><span class="sxs-lookup"><span data-stu-id="9a9bf-107">(Some databases impose a maximum length for queries.)</span></span>  
  
-   <span data-ttu-id="9a9bf-108">自己結合などで同一テーブルの複数のインスタンスを使用し、いずれかのインスタンスを参照する方法が必要な場合。</span><span class="sxs-lookup"><span data-stu-id="9a9bf-108">You are working with multiple instances of the same table (such as in a self-join) and need a way to refer to one instance or the other.</span></span>  
  
 <span data-ttu-id="9a9bf-109">たとえば、テーブル名 `"e"` _ `employee`に対して別名`information`を作成すると、クエリの残りの部分でテーブルを `"e"` として参照できます。</span><span class="sxs-lookup"><span data-stu-id="9a9bf-109">For example, you can create an alias `"e"` for a table name `employee`_`information`, and then refer to the table as `"e"` throughout the rest of the query.</span></span>  
  
### <a name="to-create-an-alias-for-a-table-or-table-valued-object"></a><span data-ttu-id="9a9bf-110">テーブルまたはテーブル値オブジェクトの別名を作成するには</span><span class="sxs-lookup"><span data-stu-id="9a9bf-110">To create an alias for a table or table-valued object</span></span>  
  
1.  <span data-ttu-id="9a9bf-111">クエリにテーブルまたはテーブル値オブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="9a9bf-111">Add the table or table-valued object to your query.</span></span>  
  
2.  <span data-ttu-id="9a9bf-112">**ダイアグラム ペイン**で、別名を作成するオブジェクトを右クリックし、ショートカット メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a9bf-112">In the **Diagram Pane**, right-click the object for which you want to create an alias, then select **Properties** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="9a9bf-113">**[プロパティ]** ウィンドウの **[エイリアス]** フィールドに別名を入力します。</span><span class="sxs-lookup"><span data-stu-id="9a9bf-113">In the **Properties** window, enter the alias in the **Alias** field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a9bf-114">参照</span><span class="sxs-lookup"><span data-stu-id="9a9bf-114">See Also</span></span>  
 <span data-ttu-id="9a9bf-115">[Visual Database Tools &#40;クエリにテーブルを追加する&#41;](add-tables-to-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="9a9bf-115">[Add Tables to Queries &#40;Visual Database Tools&#41;](add-tables-to-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="9a9bf-116">[クエリ結果の並べ替えとグループ化 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="9a9bf-116">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="9a9bf-117">[Visual Database Tools &#40;クエリ結果の概要&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="9a9bf-117">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="9a9bf-118">クエリに関する基本操作の実行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9a9bf-118">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
