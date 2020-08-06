---
title: 結果ペインのデータの操作 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- queries [Visual Database Tools]
- result sets [SQL Server], queries
- Query Designer [SQL Server], Results pane
- results [SQL Server], query
- Visual Database Tools [SQL Server], queries
- queries [SQL Server], results
- Results pane
ms.assetid: 4f8a0080-91ef-4442-83ae-53be2f478c54
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1c914b924ee477c3a59d78ae3ec114c88497726a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641380"
---
# <a name="work-with-data-in-the-results-pane-visual-database-tools"></a><span data-ttu-id="3f402-102">結果ペインのデータの操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="3f402-102">Work with Data in the Results Pane (Visual Database Tools)</span></span>
  <span data-ttu-id="3f402-103">クエリまたはビューを実行すると、その結果が結果ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f402-103">After you run a query or view, the results are shown in the Results pane.</span></span> <span data-ttu-id="3f402-104">この結果に対して操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3f402-104">You can then work with those results.</span></span> <span data-ttu-id="3f402-105">たとえば、行の追加や削除、データの入力や変更ができるだけでなく、多数の結果セット間を簡単に移動できます。</span><span class="sxs-lookup"><span data-stu-id="3f402-105">For example, you can add and delete rows, input or change data, and easily navigate through large results sets.</span></span>  
  
 <span data-ttu-id="3f402-106">次に、問題を回避し、結果セットに対して効果的に操作を行うために役立つ情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3f402-106">The following information can help you avoid problems and work effectively with your results sets.</span></span>  
  
## <a name="returning-the-results-set"></a><span data-ttu-id="3f402-107">結果セットを返す</span><span class="sxs-lookup"><span data-stu-id="3f402-107">Returning the results set</span></span>  
 <span data-ttu-id="3f402-108">結果はクエリまたはビューのいずれかから返すことができます。また、結果ペインだけを開くか、すべてのペインを開くかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="3f402-108">You can return results from either a query or a view and can choose whether to open just the results pane or all panes.</span></span> <span data-ttu-id="3f402-109">どちらの場合も、クエリまたはビューは、クエリおよびビュー デザイナーで開きます。</span><span class="sxs-lookup"><span data-stu-id="3f402-109">In either case the query or view will open in Query and View Designer.</span></span> <span data-ttu-id="3f402-110">異なるのは、前者の場合は結果ペインだけが表示された状態で開き、後者の場合は [オプション] ダイアログ ボックスで選択されたすべてのウィンドウと共に開くという点です。</span><span class="sxs-lookup"><span data-stu-id="3f402-110">The difference is that one opens with only the Results pane showing and the other opens with all windows that have been selected in the Options dialog box.</span></span> <span data-ttu-id="3f402-111">既定では 4 つのペイン (結果、SQL、ダイアグラム、および抽出条件) がすべて開きます。</span><span class="sxs-lookup"><span data-stu-id="3f402-111">The default is all four panes (Results, SQL, Diagram, and Criteria).</span></span>  
  
 <span data-ttu-id="3f402-112">詳細については、「[クエリを開く (Visual Database Tools)](visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f402-112">For more information see [Open Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="3f402-113">クエリまたはビューのデザインを変更して、別の結果セットを返すか、別の順序でレコードを返すようにするには、「[クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)](design-queries-and-views-how-to-topics-visual-database-tools.md)」に記載されたトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f402-113">To change the design of the query or view so it returns a different set of results or returns records in a different order see the topics listed in [Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="3f402-114">また、すべての結果セットを返すか、その一部を返すかを、次の 2 つの方法で決定できます。実行中にクエリを中止するか、返す結果の数をクエリ実行前に指定します。</span><span class="sxs-lookup"><span data-stu-id="3f402-114">You can also determine whether to return all or part of the results set in two ways--stop the query as it runs or choose how much of results to return before the query is run.</span></span>  
  
## <a name="navigating-in-the-results-pane"></a><span data-ttu-id="3f402-115">結果ペイン内を移動する</span><span class="sxs-lookup"><span data-stu-id="3f402-115">Navigating in the results pane</span></span>  
 <span data-ttu-id="3f402-116">結果ペインの下端にあるナビゲーション バーを使用すると、レコード間をすばやく移動できます。</span><span class="sxs-lookup"><span data-stu-id="3f402-116">You can quickly navigate through the records using the navigation bar at the bottom of the Results pane.</span></span>  
  
 <span data-ttu-id="3f402-117">最初のレコードと最後のレコードに移動するボタンや、次のレコードと前のレコードに移動するボタン、特定のレコードに移動するボタンがあります。</span><span class="sxs-lookup"><span data-stu-id="3f402-117">There are buttons for going to the first and last records, the next and previous records, and for going to a particular record.</span></span>  
  
 <span data-ttu-id="3f402-118">特定のレコードに移動するには、ナビゲーション バー内のテキスト ボックスに行番号を入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="3f402-118">To go to a particular record, type the number of the row in the text box in the navigation bar and then press ENTER.</span></span>  
  
 <span data-ttu-id="3f402-119">クエリおよびビュー デザイナーでキーボード ショートカットを使用する方法については、「[クエリおよびビュー デザイナーでの操作 (Visual Database Tools)](navigate-in-the-query-and-view-designer-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f402-119">For information about using keyboard shortcuts in the Query and View Designer see [Navigate in the Query and View Designer &#40;Visual Database Tools&#41;](navigate-in-the-query-and-view-designer-visual-database-tools.md).</span></span>  
  
## <a name="committing-changes-to-the-database"></a><span data-ttu-id="3f402-120">データベースに変更内容をコミットする</span><span class="sxs-lookup"><span data-stu-id="3f402-120">Committing changes to the database</span></span>  
 <span data-ttu-id="3f402-121">結果ペインは、オプティミスティック コンカレンシーを使用しているため、グリッドには、完全にライブのビューではなく、データベース内のデータのコピーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f402-121">The Results pane uses optimistic concurrency control so the grid shows a copy of the data in the database rather than an entirely live view.</span></span> <span data-ttu-id="3f402-122">この方法では、行から移動したときに初めて変更内容がデータベースにコミットされます。</span><span class="sxs-lookup"><span data-stu-id="3f402-122">This way changes are only committed to the database after you move off of a row.</span></span> <span data-ttu-id="3f402-123">これにより、複数のユーザーがデータベースに対して同時に操作を行うことが可能になります。</span><span class="sxs-lookup"><span data-stu-id="3f402-123">This allows more than one user to work with the database at the same time.</span></span> <span data-ttu-id="3f402-124">競合が発生した場合 (たとえば他のユーザーが同じ行を変更して先にデータベースにコミットした場合) は、競合が発生したことを通知すると共に解決策を提供するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f402-124">If there are conflicts (for example if another user changed the same row you changed and committed it to the database before you did) you will receive a message telling you of the conflict and offering resolutions.</span></span>  
  
## <a name="undo-changes-using-esc"></a><span data-ttu-id="3f402-125">Esc キーを使用して変更を元に戻す</span><span class="sxs-lookup"><span data-stu-id="3f402-125">Undo changes using ESC</span></span>  
 <span data-ttu-id="3f402-126">変更は、データベースにコミットされる前であれば、元に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="3f402-126">You can only undo a change if it hasn't yet been committed to the database.</span></span> <span data-ttu-id="3f402-127">レコードから移動していない場合、またはレコードから移動していても、変更がコミットされないことを示すエラー メッセージが表示された場合は、そのデータはコミットされていません。</span><span class="sxs-lookup"><span data-stu-id="3f402-127">The data is not committed if you haven't moved off of the record or if once you do move off the record you get an error message indicating the change won't be committed.</span></span> <span data-ttu-id="3f402-128">変更がコミットされていない場合は、Esc キーを使用して変更を元に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="3f402-128">If it hasn't been committed you can undo the change by using the ESC key.</span></span>  
  
 <span data-ttu-id="3f402-129">行内のすべての変更を元に戻すには、その行の編集していないセルに移動して Esc キーを押します。</span><span class="sxs-lookup"><span data-stu-id="3f402-129">To undo all changes in a row, move to a cell in that row that you have not edited and press the ESC key.</span></span>  
  
 <span data-ttu-id="3f402-130">編集した特定のセルに対する変更を元に戻すには、そのセルに移動して Esc キーを押します。</span><span class="sxs-lookup"><span data-stu-id="3f402-130">To undo changes to a particular cell that you have edited, move to that cell press the ESC key.</span></span>  
  
## <a name="adding-or-deleting-data-in-the-database"></a><span data-ttu-id="3f402-131">データベースのデータを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="3f402-131">Adding or deleting data in the database</span></span>  
 <span data-ttu-id="3f402-132">データベース デザインの動作を確認するために、データベースにサンプル データを追加する必要性が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3f402-132">To see how your database design is working you may need to add sample data to the database.</span></span> <span data-ttu-id="3f402-133">その場合は、結果ペインに直接データを入力するか、メモ帳や Excel など他のプログラムからデータをコピーして結果ペインに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="3f402-133">You can enter it into the results pane directly or you can copy it from another program, such as notepad or Excel, and paste it into the results pane.</span></span>  
  
 <span data-ttu-id="3f402-134">結果ペインに行をコピーできるだけでなく、新たなレコードの追加や、既存のレコードの変更または削除もできます。</span><span class="sxs-lookup"><span data-stu-id="3f402-134">In addition to copying rows into the Results pane you can add new records or modify or delete existing ones.</span></span> <span data-ttu-id="3f402-135">詳細については、「[結果ペインに新しい行を追加する (Visual Database Tools)](results-pane-visual-database-tools.md)」、「[結果ペイン内の行の削除 (Visual Database Tools)](delete-rows-in-the-results-pane-visual-database-tools.md)」、「[結果ペイン内の行の編集 (Visual Database Tools)](edit-rows-in-the-results-pane-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f402-135">For more information see [Add New Rows in the Results Pane &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md), [Delete Rows in the Results Pane &#40;Visual Database Tools&#41;](delete-rows-in-the-results-pane-visual-database-tools.md), and [Edit Rows in the Results Pane &#40;Visual Database Tools&#41;](edit-rows-in-the-results-pane-visual-database-tools.md).</span></span>  
  
## <a name="tips-for-working-with-null-values-and-empty-cells"></a><span data-ttu-id="3f402-136">NULL 値および空のセルに対する操作のヒント</span><span class="sxs-lookup"><span data-stu-id="3f402-136">Tips for working with NULL values and empty cells</span></span>  
 <span data-ttu-id="3f402-137">空の行をクリックして新たなレコードを追加する場合、すべての列の初期値は *NULL*です。</span><span class="sxs-lookup"><span data-stu-id="3f402-137">When you click on an empty row to add a new record, the initial value for all columns is *NULL*.</span></span> <span data-ttu-id="3f402-138">null 値が許可されている列であれば、そのままにしておくことができます。</span><span class="sxs-lookup"><span data-stu-id="3f402-138">If a column allows null values you can leave it as is.</span></span>  
  
 <span data-ttu-id="3f402-139">null 以外の値を null に置き換える場合は、大文字で NULL と入力します。</span><span class="sxs-lookup"><span data-stu-id="3f402-139">If you want to replace a non-null value with null, type NULL in capital letters.</span></span> <span data-ttu-id="3f402-140">結果ペインでは、それが文字列ではなく null 値であることを示すために、"NULL" が斜体で表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f402-140">The Results pane will give the word italic formatting to indicate that it is to be recognized as a null value rather than as a string.</span></span>  
  
 <span data-ttu-id="3f402-141">"null" という文字列を入力するには、引用符なしで文字を入力します。</span><span class="sxs-lookup"><span data-stu-id="3f402-141">To type in the string "null" type the letters without quotes.</span></span> <span data-ttu-id="3f402-142">文字のうち少なくとも 1 つが小文字であれば、その値は null 値ではなく文字列として扱われます。</span><span class="sxs-lookup"><span data-stu-id="3f402-142">As long as at least one of the letters is in lower case, the value will be treated as a string rather than a null value.</span></span>  
  
 <span data-ttu-id="3f402-143">データ型が binary である列の値には、既定で NULL 値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="3f402-143">Values for columns with a binary data type will have NULL values by default.</span></span> <span data-ttu-id="3f402-144">この値は、結果ペインで変更できません。</span><span class="sxs-lookup"><span data-stu-id="3f402-144">These values can't be changed in the Results pane.</span></span>  
  
 <span data-ttu-id="3f402-145">null を使用せずに空白を入力するには、既存のテキストを削除してそのセルから離れます。</span><span class="sxs-lookup"><span data-stu-id="3f402-145">To input an empty space instead of using null, delete the existing text and move off of the cell.</span></span>  
  
## <a name="validating-data"></a><span data-ttu-id="3f402-146">データの妥当性を検査する</span><span class="sxs-lookup"><span data-stu-id="3f402-146">Validating data</span></span>  
 <span data-ttu-id="3f402-147">クエリおよびビュー デザイナーでは、特定の種類のデータを列のプロパティと照合して検証できます。</span><span class="sxs-lookup"><span data-stu-id="3f402-147">The Query and View Designer can validate some kinds of data against the columns properties.</span></span> <span data-ttu-id="3f402-148">たとえば、"abc" という値を float 型の列に入力するとエラーが表示され、その変更がデータベースにコミットされません。</span><span class="sxs-lookup"><span data-stu-id="3f402-148">For example, if you enter "abc" into a column with a float data type, you will receive an error and the change will not be committed to the database.</span></span>  
  
 <span data-ttu-id="3f402-149">結果ペイン内で列のデータ型を確認するには、ダイアグラム ペインを開き、テーブルまたはテーブル値オブジェクト内の列名にマウスのカーソルを合わせるのが最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="3f402-149">The quickest way to see the data type of a column when you're in the Results pane is to open the Diagram pane and hover over the name of the column in the table or table-valued object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3f402-150">結果ペインに表示できる text 型データの最大長は 2,147,483,647 です。</span><span class="sxs-lookup"><span data-stu-id="3f402-150">The maximum length the Results pane can show for a text data type is 2,147,483,647.</span></span>  
  
## <a name="keeping-the-results-set-synchronized-with-the-query-definition"></a><span data-ttu-id="3f402-151">結果セットとクエリ定義を同期化する</span><span class="sxs-lookup"><span data-stu-id="3f402-151">Keeping the results set synchronized with the query definition</span></span>  
 <span data-ttu-id="3f402-152">クエリまたはビューの結果を操作していると、結果ペイン内のレコードがクエリ定義の同期化対象から外れてしまう場合があります。</span><span class="sxs-lookup"><span data-stu-id="3f402-152">While you're working on the results of a query or view it is possible for the records in the results pane to get out of synchronization with the queries definition.</span></span> <span data-ttu-id="3f402-153">たとえば、テーブル内の 5 列のうち 4 列についてクエリを実行し、ダイアグラム ペインを使用して 5 番目の列をクエリの定義に追加した場合、その 5 番目の列のデータは、結果ペインに自動的に追加されません。</span><span class="sxs-lookup"><span data-stu-id="3f402-153">For example, if you ran a query for four out of five columns in a table, then used the Diagram pane to add the fifth column to the definition of the query, that fifth column's data will not automatically be added to the results pane.</span></span> <span data-ttu-id="3f402-154">結果ペインに新たなクエリ定義を反映するには、再度クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="3f402-154">To make the results pane reflect the new query definition, run the query again.</span></span>  
  
 <span data-ttu-id="3f402-155">この現象が発生すると、ユーザーにわかるように、結果ペインの右下隅に警告アイコンと "クエリが変更されました。" というテキストが表示され、ペインの左上隅にも警告アイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f402-155">You can tell if this happens--an alert icon and the text "Query Changed" appears in the lower-right corner of the results pane and the icon is repeated in the upper-left corner of the pane.</span></span>  
  
## <a name="reconciling-changes-made-by-multiple-users"></a><span data-ttu-id="3f402-156">複数のユーザーによる変更を調整する</span><span class="sxs-lookup"><span data-stu-id="3f402-156">Reconciling changes made by multiple users</span></span>  
 <span data-ttu-id="3f402-157">クエリまたはビューの結果を操作していると、同じデータベースに対して操作を行っている別のユーザーがレコードを変更する場合があります。</span><span class="sxs-lookup"><span data-stu-id="3f402-157">While you're working on the results of a query or view it is possible fore the records to be changed by a different user who is also working with the database.</span></span>  
  
 <span data-ttu-id="3f402-158">この現象が発生すると、セルから離れて競合が起きた直後に、通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f402-158">If this happens you will receive a notice as soon as you move off of the cell with the conflict.</span></span> <span data-ttu-id="3f402-159">その際、他のユーザーの変更をオーバーライドするか、結果ペインを他のユーザーの変更に合わせて更新するか、発生した差異を調整せずに結果ペインの編集を続けるかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="3f402-159">You will then be able to override the other user's change, update your results pane with the other user's change, or keep editing your results pane without reconciling the differences.</span></span> <span data-ttu-id="3f402-160">差異を調整しない場合は、変更がデータベースにコミットされません。</span><span class="sxs-lookup"><span data-stu-id="3f402-160">If you choose not to reconcile the differences your changes will not be committed to the database.</span></span>  
  
## <a name="limitations-in-the-results-pane"></a><span data-ttu-id="3f402-161">結果ペインの制限</span><span class="sxs-lookup"><span data-stu-id="3f402-161">Limitations in the Results pane</span></span>  
  
### <a name="what-can-not-be-updated"></a><span data-ttu-id="3f402-162">更新できないもの</span><span class="sxs-lookup"><span data-stu-id="3f402-162">What can not be updated</span></span>  
 <span data-ttu-id="3f402-163">結果ペインのデータを正しく操作するために役立つヒントを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="3f402-163">These tips may help you work successfully with data in the Results pane.</span></span>  
  
-   <span data-ttu-id="3f402-164">複数のテーブルまたはビューの列を含むクエリは更新できません。</span><span class="sxs-lookup"><span data-stu-id="3f402-164">Queries that include columns from more than one table or view can't be updated.</span></span>  
  
-   <span data-ttu-id="3f402-165">ビューは、データベースの制約で許可されている場合に限り更新できます。</span><span class="sxs-lookup"><span data-stu-id="3f402-165">Views can only be updated if the database constraints allow it.</span></span>  
  
-   <span data-ttu-id="3f402-166">ストアド プロシージャから返された結果は更新できません。</span><span class="sxs-lookup"><span data-stu-id="3f402-166">Results returned by a stored procedure can't be updated.</span></span>  
  
-   <span data-ttu-id="3f402-167">GROUP BY 句、DISTINCT 句、または TO XML 句を使用したクエリまたはビューは更新できません。</span><span class="sxs-lookup"><span data-stu-id="3f402-167">Queries or views using the GROUP BY, DISTINCT, or TO XML clauses are not updatable.</span></span>  
  
-   <span data-ttu-id="3f402-168">テーブル値関数から返された結果は、一部の場合に限り更新できます。</span><span class="sxs-lookup"><span data-stu-id="3f402-168">Results returned by table-valued functions can only be updated in some cases.</span></span>  
  
-   <span data-ttu-id="3f402-169">クエリ内の式によって作成された列内のデータは更新できません。</span><span class="sxs-lookup"><span data-stu-id="3f402-169">Data in columns that result from an expression in the query.</span></span>  
  
-   <span data-ttu-id="3f402-170">プロバイダーが正しく変換できなかったデータは更新できません。</span><span class="sxs-lookup"><span data-stu-id="3f402-170">Data that was not successfully translated by the provider.</span></span>  
  
### <a name="what-can-not-be-represented-fully"></a><span data-ttu-id="3f402-171">完全に表現できないもの</span><span class="sxs-lookup"><span data-stu-id="3f402-171">What can not be represented fully</span></span>  
 <span data-ttu-id="3f402-172">データベースから結果ペインに返される内容は、使用しているデータ ソースのプロバイダーに大きく影響されます。</span><span class="sxs-lookup"><span data-stu-id="3f402-172">What is returned to the Results pane from the database is greatly controlled by the provider for the data source you are using.</span></span> <span data-ttu-id="3f402-173">結果ペインでは、必ずしもすべてのデータベース管理システムからのデータを解釈できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="3f402-173">The Results pane can't always translate the data from all database management systems.</span></span> <span data-ttu-id="3f402-174">結果ペインでデータを解釈できないケースを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="3f402-174">Here are come cases where this is so.</span></span>  
  
-   <span data-ttu-id="3f402-175">結果ペインで作業する場合、binary データ型は不便な場合が多く、ダウンロードに長時間かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3f402-175">Binary data types are often not useful for people working in the Results pane and they can take a very long time to download.</span></span> <span data-ttu-id="3f402-176">このため、binary データ型は *\<Binary data>* または *Null*と表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f402-176">So they are represented by *\<Binary data>* or *Null*.</span></span>  
  
-   <span data-ttu-id="3f402-177">有効桁数と小数点以下桁数が保持されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="3f402-177">Precision and scale can not always be preserved.</span></span> <span data-ttu-id="3f402-178">たとえば、結果ペインに表示できる有効桁数は 27 桁です。</span><span class="sxs-lookup"><span data-stu-id="3f402-178">For example, the Results pane supports a precision of 27.</span></span> <span data-ttu-id="3f402-179">これを超える有効桁数を持つデータ型のデータは、27 桁に切り捨てられるか、 *\<Unable to read data>* と表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f402-179">If data is of a data type with a greater precision, the data may be truncated or may be represented by *\<Unable to read data>*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f402-180">参照</span><span class="sxs-lookup"><span data-stu-id="3f402-180">See Also</span></span>  
 <span data-ttu-id="3f402-181">[Visual Database Tools &#40;クエリで基本的な操作を実行&#41;](perform-basic-operations-with-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3f402-181">[Perform Basic Operations with Queries &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="3f402-182">検索基準の指定 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="3f402-182">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
