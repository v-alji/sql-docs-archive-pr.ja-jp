---
title: 結合の削除 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- removing joins
- joins [SQL Server], removing
- deleting joins
ms.assetid: ccc212a1-fd13-48d6-85e5-5ff310c34bbd
author: stevestein
ms.author: sstein
ms.openlocfilehash: b037e317b629671f6ec5ea1fa90edfca6fafa627
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630733"
---
# <a name="remove-joins-visual-database-tools"></a><span data-ttu-id="58d8b-102">結合の削除 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="58d8b-102">Remove Joins (Visual Database Tools)</span></span>
  <span data-ttu-id="58d8b-103">テーブルを内部結合または外部結合によって結合する必要がなくなった場合は、テーブル間の結合を削除できます。</span><span class="sxs-lookup"><span data-stu-id="58d8b-103">If you do not want tables to be joined via an inner join or an outer join, you can remove the join between them.</span></span> <span data-ttu-id="58d8b-104">たとえば、 [クエリおよびビュー デザイナー](visual-database-tools.md) が 2 つのテーブル間に自動的に作成した結合を削除できます。</span><span class="sxs-lookup"><span data-stu-id="58d8b-104">For example, you might remove a join that the [Query and View Designer](visual-database-tools.md) has been created automatically between two tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="58d8b-105">クエリから結合を削除しても、データベースで設定されている基底のリレーションシップは変更されません。</span><span class="sxs-lookup"><span data-stu-id="58d8b-105">Removing a join from a query does not alter the underlying relationship in the database.</span></span>  
  
 <span data-ttu-id="58d8b-106">結合した 2 つのテーブルがクエリの一部であり、テーブル間の結合条件をすべて削除した場合、クエリ結果は両テーブルの積、つまりクロス結合となります。</span><span class="sxs-lookup"><span data-stu-id="58d8b-106">If two joined tables are part of your query and you remove all join conditions between them, the resulting query becomes the product of both tables - that is, it becomes a CROSS JOIN.</span></span>  
  
### <a name="to-remove-a-join"></a><span data-ttu-id="58d8b-107">結合を削除するには</span><span class="sxs-lookup"><span data-stu-id="58d8b-107">To remove a join</span></span>  
  
-   <span data-ttu-id="58d8b-108">[ダイアグラム ペイン](diagram-pane-visual-database-tools.md)で、削除する結合線を選択し、Del キーを押します。</span><span class="sxs-lookup"><span data-stu-id="58d8b-108">In the [Diagram pane](diagram-pane-visual-database-tools.md), select the join line for the join to remove, and then press the DELETE key.</span></span> <span data-ttu-id="58d8b-109">同時に複数の結合線を選択して削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="58d8b-109">You can select and delete multiple join lines at one time.</span></span>  
  
 <span data-ttu-id="58d8b-110">クエリおよびビュー デザイナーが結合線を削除し、 [SQL ペイン](sql-pane-visual-database-tools.md)のステートメントを変更します。</span><span class="sxs-lookup"><span data-stu-id="58d8b-110">The Query and View Designer removes the join line and alters the statement in the [SQL pane](sql-pane-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58d8b-111">参照</span><span class="sxs-lookup"><span data-stu-id="58d8b-111">See Also</span></span>  
 <span data-ttu-id="58d8b-112">[Visual Database Tools &#40;テーブルを自動的に結合&#41;](join-tables-automatically-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="58d8b-112">[Join Tables Automatically &#40;Visual Database Tools&#41;](join-tables-automatically-visual-database-tools.md) </span></span>  
 <span data-ttu-id="58d8b-113">[Visual Database Tools &#40;テーブルを手動で結合&#41;](join-tables-manually-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="58d8b-113">[Join Tables Manually &#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="58d8b-114">結合を使用したクエリ (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="58d8b-114">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
