---
title: '[クエリの定義が異なります] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69639
- vdtsql.chm:69640
- vdt.dlgbox.querydefinitionsdiffer
ms.assetid: 90383473-2922-40e5-9682-3850849aa856
author: stevestein
ms.author: sstein
ms.openlocfilehash: b9a39d5d6b739fa4ab1a96ea95b513ecb7f6682f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720768"
---
# <a name="query-definitions-differ-dialog-box-visual-database-tools"></a><span data-ttu-id="c26d2-102">[クエリの定義が異なります] ダイアログ ボックス (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c26d2-102">Query Definitions Differ Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="c26d2-103">このダイアログ ボックスは、クエリがダイアグラム ペインおよび抽出条件ペインでグラフィカルに表示できず、SQL ペインでしか編集できないことを通知します。</span><span class="sxs-lookup"><span data-stu-id="c26d2-103">This dialog box notifies you that your query cannot be represented graphically in the Diagram and Criteria panes, and that you can edit your query only in the SQL pane.</span></span>  
  
 <span data-ttu-id="c26d2-104">SQL ペインで SQL ステートメントを入力または編集してから、別のペインに移動するか、クエリを検査するか、またはクエリを実行しようとしたときに、次の条件のいずれかが当てはまる場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c26d2-104">This dialog box may appear when you enter or edit an SQL statement in the SQL pane; you then move to another pane, verify the query, or attempt to execute the query; and one of the following conditions applies:</span></span>  
  
-   <span data-ttu-id="c26d2-105">SQL ステートメントが不完全であるか、構文エラーがある。</span><span class="sxs-lookup"><span data-stu-id="c26d2-105">The SQL statement is incomplete or contains one or more syntax errors.</span></span>  
  
-   <span data-ttu-id="c26d2-106">SQL ステートメントは有効だが、グラフィカル ペインでサポートされていない (Union クエリなど)。</span><span class="sxs-lookup"><span data-stu-id="c26d2-106">The SQL statement is valid but is not supported in the graphical panes (for example, a Union query).</span></span>  
  
-   <span data-ttu-id="c26d2-107">SQL ステートメントは有効だが、使用しているデータ接続に固有の構文が含まれている。</span><span class="sxs-lookup"><span data-stu-id="c26d2-107">The SQL statement is valid but contains syntax specific to the data connection you are using.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="c26d2-108">**[クエリ]** ツール バーの **[SQL 構文の確認]** ボタンを使用すると、ステートメントが有効かどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="c26d2-108">You can check whether a statement is valid using the **Verify SQL Statement** button on the **Query** toolbar.</span></span>  
  
 <span data-ttu-id="c26d2-109">ダイアログ ボックスには、SQL ステートメントが表示できない理由を示すメッセージが表示され、どのように処理するかの決定が求められます。</span><span class="sxs-lookup"><span data-stu-id="c26d2-109">The dialog box displays a message with the reason that the SQL statement cannot be represented, and then asks how you want to proceed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c26d2-110">ダイアグラム ペインおよび抽出条件ペインが非表示になっている場合、 **[クエリの定義が異なります]** ダイアログ ボックスは表示されません。</span><span class="sxs-lookup"><span data-stu-id="c26d2-110">The **Query Definitions Differ** dialog box does not appear if you have hidden the Diagram and Criteria panes.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c26d2-111">オプション</span><span class="sxs-lookup"><span data-stu-id="c26d2-111">Options</span></span>  
 <span data-ttu-id="c26d2-112">**[無視] ボタン**</span><span class="sxs-lookup"><span data-stu-id="c26d2-112">**Ignore Button**</span></span>  
 <span data-ttu-id="c26d2-113">SQL ステートメントを受け入れてさらに編集するか実行する場合は、このボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c26d2-113">Choose this button to specify that you want to accept the SQL statement, either to edit it further or to execute it.</span></span> <span data-ttu-id="c26d2-114">ステートメントを受け入れると、ダイアグラム ペインと抽出条件ペインが淡色表示になり、SQL ペインのステートメントを反映しないことが示されます。</span><span class="sxs-lookup"><span data-stu-id="c26d2-114">If you accept the statement, the Diagram and Criteria panes appear dimmed to indicate that they do not represent the statement in the SQL pane.</span></span>  
  
 <span data-ttu-id="c26d2-115">**[元に戻す] ボタン**</span><span class="sxs-lookup"><span data-stu-id="c26d2-115">**Undo Button**</span></span>  
 <span data-ttu-id="c26d2-116">SQL ペインへの変更を破棄する場合は、このボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="c26d2-116">Choose this button to discard your changes to the SQL pane.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c26d2-117">ステートメントが正しいにもかかわらずクエリおよびビュー デザイナーによってグラフィカルにサポートされない場合は、ダイアグラム ペインと抽出条件ペインには表示されませんが、実行することはできます。</span><span class="sxs-lookup"><span data-stu-id="c26d2-117">If the statement is correct but not supported graphically by the Query and View Designer, you can execute it even though it cannot be represented in the Diagram and Criteria panes.</span></span> <span data-ttu-id="c26d2-118">たとえば、Union クエリを入力した場合、ステートメントは実行できますが、他のペインには表示されません。</span><span class="sxs-lookup"><span data-stu-id="c26d2-118">For example, if you enter a Union query, the statement can be executed but not represented in the other panes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c26d2-119">参照</span><span class="sxs-lookup"><span data-stu-id="c26d2-119">See Also</span></span>  
 [<span data-ttu-id="c26d2-120">クエリおよびビュー デザイナー ツール (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c26d2-120">Query and View Designer Tools &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
