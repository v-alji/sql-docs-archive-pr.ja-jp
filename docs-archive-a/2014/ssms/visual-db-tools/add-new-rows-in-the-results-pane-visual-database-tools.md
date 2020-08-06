---
title: 結果ペインに新しい行を追加する (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- inserting rows
- Query Designer [SQL Server], Results pane
- Results pane
- adding rows
- row additions [SQL Server], Results pane
ms.assetid: 59891c84-3f54-4ab9-8b86-72c59627b480
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3137da106279e09305261c6c7cb7fd06d254b4fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634221"
---
# <a name="add-new-rows-in-the-results-pane-visual-database-tools"></a><span data-ttu-id="b674c-102">結果ペインに新しい行を追加する (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b674c-102">Add New Rows in the Results Pane (Visual Database Tools)</span></span>
  <span data-ttu-id="b674c-103">新しいデータを入力するか、メモ帳や Excel などのプログラムから新しいデータを貼り付けることで、新しいデータを追加できます。</span><span class="sxs-lookup"><span data-stu-id="b674c-103">You can add new data either by typing it in or by pasting it from another program such as Notepad or Excel.</span></span> <span data-ttu-id="b674c-104">行を貼り付ける場合は、貼り付けるデータの列の数と型が貼り付け先のテーブルと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="b674c-104">A row to be pasted must have exactly the same number and types of columns as the table into which you are pasting.</span></span> <span data-ttu-id="b674c-105">結果ペインには、一度に複数の行を貼り付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="b674c-105">You can paste multiple rows into the Results pane at once.</span></span>  
  
 <span data-ttu-id="b674c-106">データを入力する方法については、「[結果更新の規則 (Visual Database Tools)](visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b674c-106">For information about how to enter data see [Rules for Updating Results &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
### <a name="to-add-a-new-data-row"></a><span data-ttu-id="b674c-107">新しいデータ行を追加するには</span><span class="sxs-lookup"><span data-stu-id="b674c-107">To add a new data row</span></span>  
  
1.  <span data-ttu-id="b674c-108">結果ペインの 1 番下まで移動します。ここには、新しいデータ行の追加に使用できる空の行があります。</span><span class="sxs-lookup"><span data-stu-id="b674c-108">Navigate to the bottom of the Results pane, where a blank row is available for adding a new data row.</span></span>  
  
     <span data-ttu-id="b674c-109">すべての列の初期値は、 *NULL*になります。</span><span class="sxs-lookup"><span data-stu-id="b674c-109">The initial values for all columns will be *NULL*.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="b674c-110">最初の空の行に直接移動するには、結果ペインの下部にあるナビゲーション バーを使用します。</span><span class="sxs-lookup"><span data-stu-id="b674c-110">To go directly to the first empty row use the navigation bar at the bottom of the Results pane.</span></span>  
  
2.  <span data-ttu-id="b674c-111">クリップボードから行を貼り付ける場合は、新規の行の左側にあるボタンをクリックして新規の行を選択します。</span><span class="sxs-lookup"><span data-stu-id="b674c-111">If you are pasting rows from the Clipboard, select the new row by clicking the button to its left.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b674c-112">貼り付けた行に、データベースにコミットできないものがある場合は、コミットできなかった行を通知するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b674c-112">If one or more of the rows you're pasting can't be committed to the database you will receive a message telling you which row(s) couldn't be committed.</span></span>  
  
3.  <span data-ttu-id="b674c-113">新規の行にデータを入力します。</span><span class="sxs-lookup"><span data-stu-id="b674c-113">Enter the data for the new row.</span></span> <span data-ttu-id="b674c-114">データを貼り付ける場合は、 **[編集]** メニューの **[貼り付け]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b674c-114">If you are pasting, choose **Paste** from the **Edit** menu.</span></span>  
  
4.  <span data-ttu-id="b674c-115">その行から離れると、データがデータベースにコミットされます。</span><span class="sxs-lookup"><span data-stu-id="b674c-115">Leave that row to commit it to the database.</span></span>  
  
 <span data-ttu-id="b674c-116">行を保存するときにエラーが発生した場合は、クエリおよびビュー デザイナーによりメッセージが表示され、編集していた行に戻ります。</span><span class="sxs-lookup"><span data-stu-id="b674c-116">If an error occurs when you save the row the Query and View Designer displays a message and then returns you to the row you were editing.</span></span> <span data-ttu-id="b674c-117">この場合は、次のいずれかの操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b674c-117">You can then:</span></span>  
  
-   <span data-ttu-id="b674c-118">行にさらに編集を加えることにより、エラーの原因を取り除く。</span><span class="sxs-lookup"><span data-stu-id="b674c-118">Resolve the error by making further edits in the row.</span></span>  
  
-   <span data-ttu-id="b674c-119">Esc キーを押すことにより、編集を取り消す。</span><span class="sxs-lookup"><span data-stu-id="b674c-119">Cancel the edit by pressing ESC.</span></span> <span data-ttu-id="b674c-120">変更したセル内で Esc キーを押すと、そのセルに加えた変更だけが取り消されます。</span><span class="sxs-lookup"><span data-stu-id="b674c-120">If you press ESC while in a cell that you changed, the changes for that cell are canceled.</span></span> <span data-ttu-id="b674c-121">変更していないセル内で Esc キーを押すと、行全体に加えた変更が取り消されます。</span><span class="sxs-lookup"><span data-stu-id="b674c-121">If you press ESC while in a cell you have not changed, the changes for the entire row are canceled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b674c-122">参照</span><span class="sxs-lookup"><span data-stu-id="b674c-122">See Also</span></span>  
 <span data-ttu-id="b674c-123">[[結果] ウィンドウのデータを操作するには &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="b674c-123">[Work with Data in the Results Pane &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="b674c-124">クエリに関する基本操作の実行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b674c-124">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
