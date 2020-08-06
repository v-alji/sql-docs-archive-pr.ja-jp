---
title: 自己結合の自動作成 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- automatic joins
- self-joins
- joins [SQL Server], self
ms.assetid: f9ec90e8-3aad-415c-a5c4-8dfa9540e37f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a428a44d33b5990e849772b43841df472ca7f6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631455"
---
# <a name="create-self-joins-automatically-visual-database-tools"></a><span data-ttu-id="637b6-102">自己結合の自動作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="637b6-102">Create Self-Joins Automatically (Visual Database Tools)</span></span>
  <span data-ttu-id="637b6-103">データベースのテーブルに再帰リレーションシップが設定されている場合、テーブルをテーブル自身に自動的に結合できます。</span><span class="sxs-lookup"><span data-stu-id="637b6-103">If a table has a reflexive relationship in the database, you can join it to itself automatically.</span></span>  
  
### <a name="to-create-a-self-join-automatically"></a><span data-ttu-id="637b6-104">自己結合を自動作成するには</span><span class="sxs-lookup"><span data-stu-id="637b6-104">To create a self-join automatically</span></span>  
  
1.  <span data-ttu-id="637b6-105">処理するテーブルを [ダイアグラム ペイン](visual-database-tools.md) に追加します。</span><span class="sxs-lookup"><span data-stu-id="637b6-105">Add to the [Diagram pane](visual-database-tools.md) the table you want to work with.</span></span>  
  
2.  <span data-ttu-id="637b6-106">同じテーブルを再度追加します。ダイアグラム ペインに同じテーブルが 2 つ表示されます。</span><span class="sxs-lookup"><span data-stu-id="637b6-106">Add the same table again, so that the Diagram pane shows the same table twice within the Diagram pane.</span></span>  
  
     <span data-ttu-id="637b6-107">2 番目のインスタンスには、テーブル名の後に順序番号が付加された別名が、 [クエリおよびビュー デザイナー](query-and-view-designer-tools-visual-database-tools.md) により割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="637b6-107">The [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) assigns an alias to the second instance by adding a sequential number to the table name.</span></span> <span data-ttu-id="637b6-108">さらに、2 つの四角形の間に結合線が表示され、テーブルが 2 つの異なる方法でクエリに関連していることを示します。</span><span class="sxs-lookup"><span data-stu-id="637b6-108">In addition, the Query and View Designer creates a join line between the two rectangles representing the two different ways the table participates in the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="637b6-109">参照</span><span class="sxs-lookup"><span data-stu-id="637b6-109">See Also</span></span>  
 [<span data-ttu-id="637b6-110">結合を使用したクエリ (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="637b6-110">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
