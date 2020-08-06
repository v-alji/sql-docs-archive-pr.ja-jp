---
title: 重複する行の除外 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- row duplicates [SQL Server]
- duplicate rows
- row excluded in search [SQL Server]
- result sets [SQL Server], duplicate values
- excluding rows
ms.assetid: ab35a363-421d-4665-946b-ae3f6397af50
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3b396f2738f6895684d828884d4822ea9165e0a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644761"
---
# <a name="exclude-duplicate-rows-visual-database-tools"></a><span data-ttu-id="199ab-102">重複する行の除外 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="199ab-102">Exclude Duplicate Rows (Visual Database Tools)</span></span>
  <span data-ttu-id="199ab-103">結果セットに一意の値だけが必要な場合は、結果セットからの重複の削除を指定できます。</span><span class="sxs-lookup"><span data-stu-id="199ab-103">If you want to see only unique values in a result set, you can specify that you want to exclude duplicates from the result set.</span></span>  
  
### <a name="to-exclude-duplicate-rows-from-the-result-set"></a><span data-ttu-id="199ab-104">結果セットから重複行を削除するには</span><span class="sxs-lookup"><span data-stu-id="199ab-104">To exclude duplicate rows from the result set</span></span>  
  
1.  <span data-ttu-id="199ab-105">ダイアグラム ペインの背景を右クリックし、ショートカット メニューの **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="199ab-105">Right-click the background of the Diagram pane, then choose **Properties** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="199ab-106">プロパティ ウィンドウの **[一意の値]** をクリックし、値を **[はい]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="199ab-106">In the Property window, click **Distinct values** and set the value to **Yes**.</span></span>  
  
     <span data-ttu-id="199ab-107">SQL ステートメントの表示列の一覧の前にキーワード DISTINCT が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="199ab-107">The Query and View Designer inserts the keyword DISTINCT in front of the list of display columns in the SQL statement.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="199ab-108">DISTINCT キーワードを使用する場合、結果ペインで結果セットを変更できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="199ab-108">If you use the DISTINCT keyword you may not be able to modify the result set in the results pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="199ab-109">参照</span><span class="sxs-lookup"><span data-stu-id="199ab-109">See Also</span></span>  
 <span data-ttu-id="199ab-110">[Visual Database Tools &#40;検索条件を指定し&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="199ab-110">[Specify Search Criteria &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="199ab-111">クエリ結果の並べ替えおよびグループ化 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="199ab-111">Sort and Group Query Results &#40;Visual Database Tools&#41;</span></span>](sort-and-group-query-results-visual-database-tools.md)  
  
  
