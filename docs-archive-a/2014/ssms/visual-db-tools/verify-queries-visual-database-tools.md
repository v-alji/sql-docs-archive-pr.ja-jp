---
title: クエリの検査 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:100644
helpviewer_keywords:
- verifying queries
- queries [SQL Server], verifying
- checking queries
ms.assetid: 1382c0c0-46dc-45f9-ab38-9bba1d347eea
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7bf24de9bdc0e8b7b7ceb33bb881812b180ce112
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641925"
---
# <a name="verify-queries-visual-database-tools"></a><span data-ttu-id="3e9ce-102">クエリの検査 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="3e9ce-102">Verify Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="3e9ce-103">問題を回避するために、作成したクエリを検証して、構文が正しいことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="3e9ce-103">To avoid problems, you can check the query you have built to ensure its syntax is correct.</span></span> <span data-ttu-id="3e9ce-104">このオプションは、 [SQL ペイン](visual-database-tools.md)にステートメントを入力する場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="3e9ce-104">This option is especially useful when you enter statements in the [SQL pane](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="3e9ce-105">次に、クエリの検査について注意が必要な点を挙げます。</span><span class="sxs-lookup"><span data-stu-id="3e9ce-105">Some notes to keep in mind about verifying queries:</span></span>  
  
-   <span data-ttu-id="3e9ce-106">**ダイアグラム ペイン** および **抽出条件ペイン**に表示できない場合でも、有効なステートメントは正しく検査されます。</span><span class="sxs-lookup"><span data-stu-id="3e9ce-106">A statement can be valid, and therefore be verified successfully, even if it cannot be represented in the **Diagram Pane** and **Criteria Pane**.</span></span>  
  
-   <span data-ttu-id="3e9ce-107">SQL 検査では SQL エラーのすべてが検出されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="3e9ce-107">SQL Verification can detect some, but not all SQL errors.</span></span> <span data-ttu-id="3e9ce-108">SQL 検査で検出されないエラーがクエリにある場合は、クエリを実行するときに、データベースによってエラーが検出されます。</span><span class="sxs-lookup"><span data-stu-id="3e9ce-108">If a query contains an error not detected during SQL verification, the database will detect the error when you run the query.</span></span>  
  
-   <span data-ttu-id="3e9ce-109">パラメーターを含むクエリは検査できません。</span><span class="sxs-lookup"><span data-stu-id="3e9ce-109">Queries that contain parameters cannot be verified.</span></span>  
  
### <a name="to-verify-an-sql-statement"></a><span data-ttu-id="3e9ce-110">SQL ステートメントを検査するには</span><span class="sxs-lookup"><span data-stu-id="3e9ce-110">To verify an SQL statement</span></span>  
  
-   <span data-ttu-id="3e9ce-111">**SQL ペイン**を右クリックし、ショートカット メニューの **[SQL 構文の確認]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3e9ce-111">Right-click in the **SQL Pane**, and select **Verify SQL Syntax** from the shortcut menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e9ce-112">参照</span><span class="sxs-lookup"><span data-stu-id="3e9ce-112">See Also</span></span>  
 <span data-ttu-id="3e9ce-113">[Visual Database Tools &#40;クエリの実行&#41;](run-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3e9ce-113">[Run Queries &#40;Visual Database Tools&#41;](run-queries-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="3e9ce-114">クエリに関する基本操作の実行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="3e9ce-114">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
