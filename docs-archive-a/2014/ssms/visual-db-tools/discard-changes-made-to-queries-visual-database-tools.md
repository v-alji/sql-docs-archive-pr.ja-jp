---
title: クエリに対する変更の破棄 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- reverting queries
- queries [SQL Server], discarding changes
- discarding query changes
ms.assetid: 7bb17ece-1222-4622-b476-5789d7641c64
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9ec712f0a8a708db79d054833180776d604e58dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644766"
---
# <a name="discard-changes-made-to-queries-visual-database-tools"></a><span data-ttu-id="49a7d-102">クエリに対する変更の破棄 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="49a7d-102">Discard Changes Made to Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="49a7d-103">変更を保存する前であれば、クエリ定義に対して行った変更を破棄できます。</span><span class="sxs-lookup"><span data-stu-id="49a7d-103">You can discard changes made to a query definition prior to saving them.</span></span> <span data-ttu-id="49a7d-104">いったん変更を保存すると、変更前の状態に戻すことはできなくなります。</span><span class="sxs-lookup"><span data-stu-id="49a7d-104">Once they have been saved, they cannot be returned to a previous state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="49a7d-105">結果ペインで値に行った変更を元に戻すには、レコードから移動する前に Esc キーを押します。</span><span class="sxs-lookup"><span data-stu-id="49a7d-105">To undo a change you've made to values in the Results pane, press the ESC key before you move off of the record.</span></span> <span data-ttu-id="49a7d-106">レコードから移動して、変更がデータベースにコミットされないという通知を受け取った場合も、Esc キーを押すことで前の値に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="49a7d-106">If you move off of a record and receive a notice that the changes will not be committed to the database you can also press the ESC key to revert to the previous value.</span></span>  
  
### <a name="to-discard-changes-made-to-a-query-definition"></a><span data-ttu-id="49a7d-107">クエリ定義に行った変更を破棄するには</span><span class="sxs-lookup"><span data-stu-id="49a7d-107">To discard changes made to a query definition</span></span>  
  
1.  <span data-ttu-id="49a7d-108">クエリを開いているクエリおよびビュー デザイナーで、 **[ファイル]** メニューの **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49a7d-108">With the query open in Query and View Designer, from the **File** menu, click **Close**.</span></span>  
  
2.  <span data-ttu-id="49a7d-109">**[Microsoft SQL Server Management Studio]** ダイアログ ボックスで **[いいえ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="49a7d-109">In the **Microsoft SQL Server Management Studio** dialog box, click **No**.</span></span>  
  
     <span data-ttu-id="49a7d-110">クエリの定義が前回保存した状態に戻ります。</span><span class="sxs-lookup"><span data-stu-id="49a7d-110">The query definition will return to the state it was in at the last save.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49a7d-111">参照</span><span class="sxs-lookup"><span data-stu-id="49a7d-111">See Also</span></span>  
 <span data-ttu-id="49a7d-112">[Visual Database Tools&#41;&#40;クエリを保存する](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="49a7d-112">[Save Queries &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="49a7d-113">[クエリおよびビューのデザイン方法に関するトピック &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="49a7d-113">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 <span data-ttu-id="49a7d-114">[Visual Database Tools &#40;クエリで基本的な操作を実行&#41;](perform-basic-operations-with-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="49a7d-114">[Perform Basic Operations with Queries &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="49a7d-115">結果ペインのデータの操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="49a7d-115">Work with Data in the Results Pane &#40;Visual Database Tools&#41;</span></span>](results-pane-visual-database-tools.md)  
  
  
