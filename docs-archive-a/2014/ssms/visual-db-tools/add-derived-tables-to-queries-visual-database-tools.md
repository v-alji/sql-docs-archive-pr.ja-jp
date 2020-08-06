---
title: クエリへの派生テーブルの追加 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [Visual Database Tools]
- joins [SQL Server], derived tables
- table joins [SQL Server]
- derived tables
ms.assetid: 05f1ba1d-465f-4e36-84bb-21b963c9b8f9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 72169654b878f404950788b468bb6603035fd540
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634222"
---
# <a name="add-derived-tables-to-queries-visual-database-tools"></a><span data-ttu-id="1657a-102">クエリへの派生テーブルの追加 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="1657a-102">Add Derived Tables to Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="1657a-103">派生テーブルは、クエリのソース テーブルとして使用される結果セットです。</span><span class="sxs-lookup"><span data-stu-id="1657a-103">Derived tables are result sets used as table sources in a query.</span></span> <span data-ttu-id="1657a-104">**ダイアグラム ペイン**でクエリに派生テーブルを追加できます。</span><span class="sxs-lookup"><span data-stu-id="1657a-104">You can add a derived table to a query in the **Diagram Pane**.</span></span>  
  
### <a name="to-add-a-derived-table-to-a-query"></a><span data-ttu-id="1657a-105">クエリに派生テーブルを追加するには</span><span class="sxs-lookup"><span data-stu-id="1657a-105">To add a derived table to a query</span></span>  
  
1.  <span data-ttu-id="1657a-106">既存のクエリを開くか、新しいクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="1657a-106">Open an existing query or create a new query.</span></span>  
  
2.  <span data-ttu-id="1657a-107">**ダイアグラム ペイン** を右クリックし、 **[派生した新しいテーブルの追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1657a-107">Right-click the **Diagram Pane** and choose **Add New Derived Table**.</span></span>  
  
     <span data-ttu-id="1657a-108">derivedtbl_*N* という名前で新しいテーブルが追加され、派生テーブルの SELECT ステートメントがクエリの FROM 句に追加されます。</span><span class="sxs-lookup"><span data-stu-id="1657a-108">A new table with the name derivedtbl_*N* is added, and the derived table's SELECT statement is added to the query's FROM clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1657a-109">参照</span><span class="sxs-lookup"><span data-stu-id="1657a-109">See Also</span></span>  
 <span data-ttu-id="1657a-110">[Visual Database Tools &#40;クエリで基本的な操作を実行&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="1657a-110">[Perform Basic Operations with Queries &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="1657a-111">[Visual Database Tools &#40;クエリの作成&#41;](create-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="1657a-111">[Create Queries &#40;Visual Database Tools&#41;](create-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="1657a-112">[Visual Database Tools &#40;クエリを開く&#41;](open-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="1657a-112">[Open Queries &#40;Visual Database Tools&#41;](open-queries-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="1657a-113">SELECT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1657a-113">SELECT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/select-transact-sql)  
  
  
