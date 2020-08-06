---
title: 値の一致しない行を選択する方法 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search conditions [SQL Server], rows not matching value
- row not matching value [SQL Server]
- NOT operator [Visual Database Tools]
- search criteria [SQL Server], rows not matching value
ms.assetid: 19898578-7b2f-401c-bb8f-9f2a017efdf7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 412ec93cbfedc87e92da9e86c7e4c7455919722a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719317"
---
# <a name="select-rows-that-do-not-match-a-value-visual-database-tools"></a><span data-ttu-id="a9e82-102">値の一致しない行を選択する方法 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="a9e82-102">Select Rows That Do Not Match a Value (Visual Database Tools)</span></span>
  <span data-ttu-id="a9e82-103">値の一致しない行を検索するには、NOT 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="a9e82-103">To find rows that do not match a value, use the NOT operator.</span></span>  
  
### <a name="to-find-rows-that-do-not-match-a-value"></a><span data-ttu-id="a9e82-104">値の一致しない行を検索するには</span><span class="sxs-lookup"><span data-stu-id="a9e82-104">To find rows that do not match a value</span></span>  
  
1.  <span data-ttu-id="a9e82-105">検索条件で使用する列または式を追加していない場合は、列または式を [抽出条件ペイン](visual-database-tools.md)に追加します。</span><span class="sxs-lookup"><span data-stu-id="a9e82-105">If you have not done so already, add the columns or expressions that you want to use within your search condition to the [Criteria pane](visual-database-tools.md).</span></span>  
  
2.  <span data-ttu-id="a9e82-106">検索するデータ列または式を含む行を見つけ、 **[フィルター]** グリッド列に NOT 演算子とそれに続く検索値を入力します。</span><span class="sxs-lookup"><span data-stu-id="a9e82-106">Locate the row containing the data column or expression to search, and then in the **Filter** grid column, enter the NOT operator followed by a search value.</span></span>  
  
 <span data-ttu-id="a9e82-107">たとえば、 `products` テーブルから、製品コード列の値が "A" 以外の文字で始まるすべての行を検索するには、検索条件を次のようにします。</span><span class="sxs-lookup"><span data-stu-id="a9e82-107">For example, to find all the rows in a `products` table where the values in the product code column begin with a character other than "A," you can enter a search condition such as the following:</span></span>  
  
```  
NOT LIKE 'A%'  
```  
  
## <a name="see-also"></a><span data-ttu-id="a9e82-108">参照</span><span class="sxs-lookup"><span data-stu-id="a9e82-108">See Also</span></span>  
 <span data-ttu-id="a9e82-109">[Visual Database Tools &#40;検索値を入力するための規則&#41;](rules-for-entering-search-values-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="a9e82-109">[Rules for Entering Search Values &#40;Visual Database Tools&#41;](rules-for-entering-search-values-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="a9e82-110">検索基準の指定 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="a9e82-110">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
