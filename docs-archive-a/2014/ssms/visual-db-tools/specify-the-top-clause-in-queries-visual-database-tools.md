---
title: クエリでの TOP 句の指定 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- TOP clause, queries
- percentage of rows returned [SQL Server]
- number of rows
- search conditions [SQL Server], TOP clause
- restricting rows returned
- search criteria [SQL Server], limiting rows returned
- inspecting portion of results
- limiting rows returned
- search criteria [SQL Server], TOP clause
ms.assetid: ba7d7c10-9bb3-4d9b-90b0-5fa94ecae59b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8228779703b1bbe3753f1e2728e83b4b5c3a3d17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740649"
---
# <a name="specify-the-top-clause-in-queries-visual-database-tools"></a><span data-ttu-id="0838d-102">クエリでの TOP 句の指定 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="0838d-102">Specify the TOP Clause in Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="0838d-103">TOP 句は、クエリから最初の *n* 行または *n %* 行だけを返します。</span><span class="sxs-lookup"><span data-stu-id="0838d-103">The TOP clause returns only the first *n* or *n percent* rows from a query.</span></span> <span data-ttu-id="0838d-104">TOP 句は、すべてのクエリ結果を返すために必要なリソースを使用する前に、結果の一部を検査して、必要なクエリが実行されるかどうかを確認する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="0838d-104">The TOP clause is useful when you want to inspect a portion of your results to find out if your query does what you expect it to do, without taking the resources necessary to return all of the query results.</span></span>  
  
### <a name="to-specify-the-top-clause-in-queries"></a><span data-ttu-id="0838d-105">クエリで TOP 句を指定するには</span><span class="sxs-lookup"><span data-stu-id="0838d-105">To specify the TOP clause in queries</span></span>  
  
1.  <span data-ttu-id="0838d-106">ソリューション エクスプローラーでクエリを開くか、新しいクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="0838d-106">Open a query from Solution Explorer or create a new one.</span></span>  
  
2.  <span data-ttu-id="0838d-107">**[表示]** メニューの **[プロパティ ウィンドウ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0838d-107">From the **View** menu, click **Properties Window**.</span></span>  
  
3.  <span data-ttu-id="0838d-108">**[プロパティ ウィンドウ]** で、 **[Top の指定]** プロパティを検索して展開します。</span><span class="sxs-lookup"><span data-stu-id="0838d-108">In the **Properties Window**, locate and expand the **Top Specification** property.</span></span>  
  
4.  <span data-ttu-id="0838d-109">**[(Top)]** 子プロパティをクリックして、 **[はい]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="0838d-109">Click the **(Top)** child property and set it to **Yes**.</span></span>  
  
5.  <span data-ttu-id="0838d-110">**[式]** 子プロパティで、数値の結果を返す式を入力します ("10"、"2\*5" など)。</span><span class="sxs-lookup"><span data-stu-id="0838d-110">In the **Expression** child property, type an expression that has a numeric result (for example, "10" or "2\*5").</span></span>  
  
6.  <span data-ttu-id="0838d-111">**[PERCENT]** 子プロパティをクリックして、 **[式]** プロパティを、返されるすべての行のパーセントとして処理するか (はい)、返される行の絶対数として処理するか (いいえ) を指定します。</span><span class="sxs-lookup"><span data-stu-id="0838d-111">Click the **Percent** child property and indicate whether or not to treat the **Expression** property as a percentage of all rows returned (Yes) or as the absolute number of rows returned (No).</span></span>  
  
7.  <span data-ttu-id="0838d-112">クエリで ORDER BY 句が使用される場合は、 **[WITH TIES 使用]** 子プロパティをクリックして、グループの一部だけが含まれる場合にグループ内のすべての行を表示するときは **[はい]** 、行を切り捨てるときは **[いいえ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0838d-112">If your query uses the ORDER BY clause, click the **With Ties** child property and choose **Yes** to display all rows in a group if only part of the group is included or **No** to truncate them.</span></span>  
  
 <span data-ttu-id="0838d-113">上記の手順を実行していくと、TOP 句が SQL ペインに表示され、プロパティの現在の設定を反映するように変更されます。</span><span class="sxs-lookup"><span data-stu-id="0838d-113">As you work through the preceding procedure, notice that the TOP clause, displayed in the SQL pane, changes to reflect the current settings of the properties.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0838d-114">SQL ペインで TOP 句を編集することで、 **[Top の指定]** の子プロパティの値を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="0838d-114">You can also change the values of the child properties of the **Top Specification** by editing the TOP clause in the SQL pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0838d-115">参照</span><span class="sxs-lookup"><span data-stu-id="0838d-115">See Also</span></span>  
 <span data-ttu-id="0838d-116">[クエリおよびビューのデザイン方法に関するトピック &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="0838d-116">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="0838d-117">クエリのプロパティ (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="0838d-117">Query Properties &#40;Visual Database Tools&#41;</span></span>](query-properties-visual-database-tools.md)  
  
  
