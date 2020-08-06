---
title: デザインペイン (マイニングモデル予測ビュー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.prediction.design.f1
ms.assetid: 17f24c8d-43cd-4f4d-83b3-a41ee8fbe8e8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 32ac73a2d6fde38d15d1f45a8439293695749ea4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716957"
---
# <a name="design-pane-mining-model-prediction-view"></a><span data-ttu-id="80791-102">[デザイン] ペイン ([マイニング モデル予測] ビュー)</span><span class="sxs-lookup"><span data-stu-id="80791-102">Design Pane (Mining Model Prediction View)</span></span>
  <span data-ttu-id="80791-103">**デザイン** ペインには、データ マイニング予測クエリ ビルダーがあり、これを利用してデータ マイニング予測クエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="80791-103">The **Design** pane contains the Prediction Query Builder, which you can use to build data mining predictions.</span></span> <span data-ttu-id="80791-104">データ ソース ビューから入力データのテーブルを使用する予測クエリを設計して一括予測を生成することも、個々の値を取得する単一予測クエリを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="80791-104">You can design prediction queries that use tables of input data from a data source view, to generate bulk predictions, or you can create singleton prediction queries, which let you provide individual values.</span></span>  
  
 <span data-ttu-id="80791-105">クエリを実行して結果を表示するには、クエリ結果ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="80791-105">To run the query and view the results, switch to query result view.</span></span>  
  
 <span data-ttu-id="80791-106">**クエリ** ビューには、予測クエリ ビルダーによって作成されたデータ マイニング拡張機能 (DMX) のクエリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="80791-106">The **Query** view displays the Data Mining Extensions (DMX) query that Prediction Query Builder creates.</span></span> <span data-ttu-id="80791-107">DMX に精通している場合には、このクエリをカスタマイズすることができます。</span><span class="sxs-lookup"><span data-stu-id="80791-107">If you are familiar with DMX, you can customize this query.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="80791-108">クエリに手動で何らかの変更を加えた場合、デザイン ビューに戻ると変更は失われます。</span><span class="sxs-lookup"><span data-stu-id="80791-108">If you make any manual changes to the query, your changes will be lost when you switch back to Design view.</span></span> <span data-ttu-id="80791-109">DMX クエリを保存するには、Windows クリップボードにクエリをコピーしてからテキスト ファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="80791-109">If you want to save the DMX query, you can copy the query to the Windows Clipboard and then paste it to a text file.</span></span>  
  
 <span data-ttu-id="80791-110">**詳細:** [データ マイニング クエリ](data-mining/data-mining-queries.md)</span><span class="sxs-lookup"><span data-stu-id="80791-110">**For More Information:** [Data Mining Queries](data-mining/data-mining-queries.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="80791-111">Options</span><span class="sxs-lookup"><span data-stu-id="80791-111">Options</span></span>  
 <span data-ttu-id="80791-112">**[クエリ結果ビューに切り替え]**</span><span class="sxs-lookup"><span data-stu-id="80791-112">**Switch to query result view**</span></span>  
 <span data-ttu-id="80791-113">クリックすると、ビューを順に **[デザイン]**、 **[クエリ]**、 **[結果]** ペインに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="80791-113">Click to switch between the **Design**, **Query**, and **Result** panes.</span></span> <span data-ttu-id="80791-114">**[結果]** ペインに切り替えると、クエリが実行されます。</span><span class="sxs-lookup"><span data-stu-id="80791-114">Switching to the **Result** pane runs the query.</span></span>  
  
 <span data-ttu-id="80791-115">**[クエリ結果の保存]**</span><span class="sxs-lookup"><span data-stu-id="80791-115">**Save the query result**</span></span>  
 <span data-ttu-id="80791-116">**[データ マイニングのクエリ結果を保存]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="80791-116">Opens the **Save Data Mining Query Result** dialog box.</span></span>  
  
 <span data-ttu-id="80791-117">**Singleton query**</span><span class="sxs-lookup"><span data-stu-id="80791-117">**Singleton query**</span></span>  
 <span data-ttu-id="80791-118">単一クエリの作成を有効にします。既知のデータのソースとしてテーブルを指定する代わりに、クエリに直接値を指定できるようになります。</span><span class="sxs-lookup"><span data-stu-id="80791-118">Enables creating a singleton query, in which you can provide values directly for the query instead of providing a table as the source of the known data.</span></span> <span data-ttu-id="80791-119">**[入力テーブルの選択]** テーブルは **[単一クエリ入力]** テーブルに置き換わります。</span><span class="sxs-lookup"><span data-stu-id="80791-119">The **Select Input Table(s)** table is replaced by a **Singleton Query Input** table.</span></span>  
  
 <span data-ttu-id="80791-120">**[クエリ結果を最新状態に更新します]**</span><span class="sxs-lookup"><span data-stu-id="80791-120">**Refresh query results**</span></span>  
 <span data-ttu-id="80791-121">予測クエリを再処理します。</span><span class="sxs-lookup"><span data-stu-id="80791-121">Reprocesses the prediction query.</span></span> <span data-ttu-id="80791-122">この操作は **[結果]** ペインでのみ行えます。</span><span class="sxs-lookup"><span data-stu-id="80791-122">This is enabled only in the **Result** pane.</span></span>  
  
 <span data-ttu-id="80791-123">**[マイニング モデル]**</span><span class="sxs-lookup"><span data-stu-id="80791-123">**Mining Model**</span></span>  
 <span data-ttu-id="80791-124">予測の基準として選択されているマイニング モデルを表示します。</span><span class="sxs-lookup"><span data-stu-id="80791-124">Displays the selected mining model on which you want to base predictions.</span></span>  
  
 <span data-ttu-id="80791-125">**[モデルの選択]**</span><span class="sxs-lookup"><span data-stu-id="80791-125">**Select Model**</span></span>  
 <span data-ttu-id="80791-126">**[マイニング モデルの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="80791-126">Opens the **Select Mining Model** dialog box.</span></span>  
  
 <span data-ttu-id="80791-127">**[入力テーブルの選択]**</span><span class="sxs-lookup"><span data-stu-id="80791-127">**Select Input Table(s)**</span></span>  
 <span data-ttu-id="80791-128">予測の基となる既知のデータが含まれている、選択された入力テーブルを表示します。</span><span class="sxs-lookup"><span data-stu-id="80791-128">Displays the selected input tables that contain known data on which to base the predictions.</span></span>  
  
 <span data-ttu-id="80791-129">**テーブルの削除**</span><span class="sxs-lookup"><span data-stu-id="80791-129">**Delete Table**</span></span>  
 <span data-ttu-id="80791-130">選択されたテーブルを削除します。</span><span class="sxs-lookup"><span data-stu-id="80791-130">Deletes the selected table.</span></span> <span data-ttu-id="80791-131">テーブルが選択されていない場合や存在しない場合には、このボタンは無効になります。</span><span class="sxs-lookup"><span data-stu-id="80791-131">This button is disabled if a table has not been selected or does not exist.</span></span>  
  
 <span data-ttu-id="80791-132">**[ケース テーブルの選択]**</span><span class="sxs-lookup"><span data-stu-id="80791-132">**Select Case Table**</span></span>  
 <span data-ttu-id="80791-133">**[テーブルの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="80791-133">Opens the **Select Table** dialog box.</span></span> <span data-ttu-id="80791-134">このボタンは、ケース テーブルが選択されていない場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="80791-134">This button appears only if a case table has not been selected.</span></span>  
  
 <span data-ttu-id="80791-135">**[入れ子になったテーブルの選択]**</span><span class="sxs-lookup"><span data-stu-id="80791-135">**Select Nested Table**</span></span>  
 <span data-ttu-id="80791-136">**[テーブルの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="80791-136">Opens the **Select Table** dialog box.</span></span> <span data-ttu-id="80791-137">このボタンは、ケース テーブルが選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="80791-137">This button appears only if a case table has been selected.</span></span> <span data-ttu-id="80791-138">関連付けられているマイニング構造に入れ子になったテーブルが含まれていない場合、このボタンは無効になります。</span><span class="sxs-lookup"><span data-stu-id="80791-138">If the associated mining structure does not contain a nested table, this button is disabled.</span></span>  
  
 <span data-ttu-id="80791-139">**[結合の変更]**</span><span class="sxs-lookup"><span data-stu-id="80791-139">**Modify Join**</span></span>  
 <span data-ttu-id="80791-140">**[入れ子になった結合の指定]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="80791-140">Opens the **Specify Nested Join** dialog box.</span></span> <span data-ttu-id="80791-141">このボタンは、入れ子になったテーブルが選択されている場合にのみアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="80791-141">This button is active only if the nested table is selected.</span></span>  
  
 <span data-ttu-id="80791-142">**[単一クエリ入力]**</span><span class="sxs-lookup"><span data-stu-id="80791-142">**Singleton Query input**</span></span>  
 <span data-ttu-id="80791-143">**[単一クエリ]** ボタンをクリックすると有効になります。</span><span class="sxs-lookup"><span data-stu-id="80791-143">Enabled when you select the **Singleton query** button.</span></span> <span data-ttu-id="80791-144">次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="80791-144">Contains the following columns:</span></span>  
  
|<span data-ttu-id="80791-145">値</span><span class="sxs-lookup"><span data-stu-id="80791-145">Value</span></span>|<span data-ttu-id="80791-146">説明</span><span class="sxs-lookup"><span data-stu-id="80791-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="80791-147">**[マイニング モデル列]**</span><span class="sxs-lookup"><span data-stu-id="80791-147">**Mining Model Column**</span></span>|<span data-ttu-id="80791-148">**[マイニング モデル]** テーブルで選択されているマイニング モデル内のマイニング モデル列が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="80791-148">Lists the mining model columns contained within the mining model that is selected in the **Mining Model** table.</span></span>|  
|<span data-ttu-id="80791-149">**Value**</span><span class="sxs-lookup"><span data-stu-id="80791-149">**Value**</span></span>|<span data-ttu-id="80791-150">選択したマイニング モデル列で可能な各状態を示した一覧から、値を選択します。</span><span class="sxs-lookup"><span data-stu-id="80791-150">Select a value from the list that contains each possible state of the selected mining model column.</span></span><br /><br /> <span data-ttu-id="80791-151">列が入れ子になったテーブルの列である場合、値のセルをクリックすると **[入れ子になったテーブルの入力]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="80791-151">If the column is a nested table column, clicking the value cell opens the **Nested Table Input** dialog box.</span></span>|  
  
 <span data-ttu-id="80791-152">**ソース**</span><span class="sxs-lookup"><span data-stu-id="80791-152">**Source**</span></span>  
 <span data-ttu-id="80791-153">列に使用するフィールドが含まれているソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="80791-153">Select the source that contains the field that you will use for the column.</span></span> <span data-ttu-id="80791-154">**[マイニング モデル]** で選択したマイニング モデル、 **[入力テーブルの選択]** で選択した入力テーブル、予測関数、カスタム式のいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="80791-154">You can either use the mining model that is selected in the **Mining Model** table, the input table or tables that are selected in the **Select Input Table(s)** table, a prediction function, or a custom expression.</span></span>  
  
 <span data-ttu-id="80791-155">マイニング モデルや入力テーブルを含むテーブルから列をドラッグして、セルに入力できます。</span><span class="sxs-lookup"><span data-stu-id="80791-155">Columns can be dragged from the tables containing the mining model and input tables onto the cell.</span></span>  
  
 <span data-ttu-id="80791-156">**フィールド**</span><span class="sxs-lookup"><span data-stu-id="80791-156">**Field**</span></span>  
 <span data-ttu-id="80791-157">ソース テーブルから派生した列の一覧から列を選択します。</span><span class="sxs-lookup"><span data-stu-id="80791-157">Select a column from the list of columns derived from the source table.</span></span> <span data-ttu-id="80791-158">**[ソース]** で **[予測関数]** を選択した場合、ここには選択したマイニング モデルで利用できる予測関数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="80791-158">If you selected **Prediction Function** in **Source**, this contains the prediction function available for the selected mining model.</span></span>  
  
 <span data-ttu-id="80791-159">**グループ**</span><span class="sxs-lookup"><span data-stu-id="80791-159">**Group**</span></span>  
 <span data-ttu-id="80791-160">式をグループ化するために **[ルールの適用条件]** 列と組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="80791-160">Use with the **And/Or** column to group expressions together.</span></span> <span data-ttu-id="80791-161">たとえば、「 `(expr1 Or expr2) And expr3` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="80791-161">For example, `(expr1 Or expr2) And expr3`.</span></span>  
  
 <span data-ttu-id="80791-162">**And/Or**</span><span class="sxs-lookup"><span data-stu-id="80791-162">**And/Or**</span></span>  
 <span data-ttu-id="80791-163">論理クエリを作成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="80791-163">Use to create a logical query.</span></span> <span data-ttu-id="80791-164">たとえば、「 `(expr1 Or expr2) And expr3` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="80791-164">For example, `(expr1 Or expr2) And expr3`.</span></span>  
  
 <span data-ttu-id="80791-165">**[条件と引数]**</span><span class="sxs-lookup"><span data-stu-id="80791-165">**Criteria/Argument**</span></span>  
 <span data-ttu-id="80791-166">列に適用する条件またはユーザー式を指定します。</span><span class="sxs-lookup"><span data-stu-id="80791-166">Specify a condition or user expression that applies to the column.</span></span> <span data-ttu-id="80791-167">マイニング モデルや入力テーブルを含むテーブルから列をドラッグして、セルに入力できます。</span><span class="sxs-lookup"><span data-stu-id="80791-167">Columns can be dragged from the tables containing the mining model and input tables onto the cell.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80791-168">参照</span><span class="sxs-lookup"><span data-stu-id="80791-168">See Also</span></span>  
 <span data-ttu-id="80791-169">[DMX&#41; ステートメントリファレンス &#40;データマイニング拡張機能](/sql/dmx/data-mining-extensions-dmx-statements) </span><span class="sxs-lookup"><span data-stu-id="80791-169">[Data Mining Extensions &#40;DMX&#41; Statement Reference](/sql/dmx/data-mining-extensions-dmx-statements) </span></span>  
 <span data-ttu-id="80791-170">[データマイニングクエリインターフェイス](data-mining/data-mining-query-tools.md) </span><span class="sxs-lookup"><span data-stu-id="80791-170">[Data Mining Query Interfaces](data-mining/data-mining-query-tools.md) </span></span>  
 [<span data-ttu-id="80791-171">予測クエリ ビルダー &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="80791-171">Prediction Query Builder &#40;Data Mining&#41;</span></span>](prediction-query-builder-data-mining.md)  
  
  
