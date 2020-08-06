---
title: 予測クエリビルダーを使用して予測クエリを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- prediction queries [Analysis Services]
- Mining Model Prediction [Analysis Services], prediction queries
ms.assetid: e02836e5-dd8c-4c97-a078-840ae79d3660
author: minewiskan
ms.author: owend
ms.openlocfilehash: 13f39de4085cb74949e9540570d574c09e72ee27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632792"
---
# <a name="create-a-prediction-query-using-the-prediction-query-builder"></a><span data-ttu-id="3a25e-102">予測クエリ ビルダーを使用した予測クエリの作成</span><span class="sxs-lookup"><span data-stu-id="3a25e-102">Create a Prediction Query Using the Prediction Query Builder</span></span>
  <span data-ttu-id="3a25e-103">予測クエリは、BI Development Studio でデータ マイニング ソリューションを構築しているときに作成できます。また、SQL Server Management Studio で既存のマイニング モデルを右クリックし、 **[予測クエリの作成]** オプションを選択して、作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="3a25e-103">You can create prediction queries either while you are building a data mining solution in BI Development Studio, or by right-clicking an existing mining model in SQL Server Management Studio, and then choosing the option, **Build Prediction Query**.</span></span>  
  
 <span data-ttu-id="3a25e-104">**予測クエリ ビルダー** には、次の 3 種類のデザイン モードがあります。これらのモードを切り替えるには、左上隅のアイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3a25e-104">The **Prediction Query Builder** has the following three design modes, which you can switch among by clicking the icons in the upper-left corner.</span></span>  
  
-   <span data-ttu-id="3a25e-105">**設計**</span><span class="sxs-lookup"><span data-stu-id="3a25e-105">**Design**</span></span>  
  
-   <span data-ttu-id="3a25e-106">**クエリ**</span><span class="sxs-lookup"><span data-stu-id="3a25e-106">**Query**</span></span>  
  
-   <span data-ttu-id="3a25e-107">**結果**</span><span class="sxs-lookup"><span data-stu-id="3a25e-107">**Result**</span></span>  
  
 <span data-ttu-id="3a25e-108">**[デザイン]** モードでは予測クエリを作成できます。それには、入力データを選択し、そのデータをモデルにマップし、グリッドを使用して作成したステートメントに予測関数を追加します。</span><span class="sxs-lookup"><span data-stu-id="3a25e-108">**Design** mode lets you build a prediction query by choosing input data, mapping the data to the model, and then adding prediction functions into statements you build by using the grid.</span></span> <span data-ttu-id="3a25e-109">デザイン グリッドには、次の構成要素があります。</span><span class="sxs-lookup"><span data-stu-id="3a25e-109">The design grid contains these building blocks:</span></span>  
  
 <span data-ttu-id="3a25e-110">**ソース**</span><span class="sxs-lookup"><span data-stu-id="3a25e-110">**Source**</span></span>  
 <span data-ttu-id="3a25e-111">新しい列のソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="3a25e-111">Choose the source of the new column.</span></span> <span data-ttu-id="3a25e-112">マイニング モデル、データ ソース ビューに含まれる入力テーブル、予測関数、またはカスタマイズされた式からの列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="3a25e-112">You can use columns from the mining model, input tables included in the data source view, a prediction function, or a customized expression.</span></span>  
  
 <span data-ttu-id="3a25e-113">**フィールド**</span><span class="sxs-lookup"><span data-stu-id="3a25e-113">**Field**</span></span>  
 <span data-ttu-id="3a25e-114">**[ソース]** 列の選択に関連付けられている特定の列または関数を決定します。</span><span class="sxs-lookup"><span data-stu-id="3a25e-114">Determines the specific column or function that is associated with the selection in the **Source** column.</span></span>  
  
 <span data-ttu-id="3a25e-115">**Alias**</span><span class="sxs-lookup"><span data-stu-id="3a25e-115">**Alias**</span></span>  
 <span data-ttu-id="3a25e-116">結果セット内で列に付けられる名前を決定します。</span><span class="sxs-lookup"><span data-stu-id="3a25e-116">Determines how the column is to be named in the result set.</span></span>  
  
 <span data-ttu-id="3a25e-117">**表示**</span><span class="sxs-lookup"><span data-stu-id="3a25e-117">**Show**</span></span>  
 <span data-ttu-id="3a25e-118">**[ソース]** 列の選択項目を結果に表示するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="3a25e-118">Determines whether the selection in the **Source** column is displayed in the results.</span></span>  
  
 <span data-ttu-id="3a25e-119">**グループ**</span><span class="sxs-lookup"><span data-stu-id="3a25e-119">**Group**</span></span>  
 <span data-ttu-id="3a25e-120">**[ルールの適用条件]** 列と共に使用して、かっこで式をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="3a25e-120">Works with the **And/Or** column to group expressions together by using parentheses.</span></span> <span data-ttu-id="3a25e-121">たとえば、(expr1 or expr2) and expr3 のようになります。</span><span class="sxs-lookup"><span data-stu-id="3a25e-121">For example, (expr1 or expr2) and expr3.</span></span>  
  
 <span data-ttu-id="3a25e-122">**And/Or**</span><span class="sxs-lookup"><span data-stu-id="3a25e-122">**And/Or**</span></span>  
 <span data-ttu-id="3a25e-123">クエリでロジックを作成します。</span><span class="sxs-lookup"><span data-stu-id="3a25e-123">Creates logic in the query.</span></span> <span data-ttu-id="3a25e-124">たとえば、(expr1 or expr2) and expr3 のようになります。</span><span class="sxs-lookup"><span data-stu-id="3a25e-124">For example, (expr1 or expr2) and expr3.</span></span>  
  
 <span data-ttu-id="3a25e-125">**[条件と引数]**</span><span class="sxs-lookup"><span data-stu-id="3a25e-125">**Criteria/Argument**</span></span>  
 <span data-ttu-id="3a25e-126">列に適用される条件またはユーザー式を指定します。</span><span class="sxs-lookup"><span data-stu-id="3a25e-126">Specifies a condition or user expression that applies to the column.</span></span> <span data-ttu-id="3a25e-127">列をテーブルからセルにドラッグできます。</span><span class="sxs-lookup"><span data-stu-id="3a25e-127">You can drag columns from the tables to the cell.</span></span>  
  
 <span data-ttu-id="3a25e-128">**[クエリ]** モードには、データ マイニング拡張機能 (DMX) 言語や入力データとモデル列のビューを直接使用できるテキスト エディターが用意されています。</span><span class="sxs-lookup"><span data-stu-id="3a25e-128">**Query** mode provides a text editor that gives you direct access to the Data Mining Extensions (DMX) language, along with a view of the input data and model columns.</span></span> <span data-ttu-id="3a25e-129">**[クエリ]** モードを選択すると、クエリの定義に使用したグリッドが基本的なテキスト エディターに変わります。</span><span class="sxs-lookup"><span data-stu-id="3a25e-129">When you select **Query** mode, the grid that you used to define the query is replaced by a basic text editor.</span></span> <span data-ttu-id="3a25e-130">このエディターでは、作成したクエリのコピーと保存、既存の DMX クエリへの貼り付け、クリップボードからの貼り付け、実行が可能です。</span><span class="sxs-lookup"><span data-stu-id="3a25e-130">You can use this editor to copy and save queries you have composed, or to paste in existing DMX queries and from the Clipboard and run them.</span></span>  
  
 <span data-ttu-id="3a25e-131">**[結果]** ビューでは、現在のクエリを実行し、その結果をグリッドに表示できます。</span><span class="sxs-lookup"><span data-stu-id="3a25e-131">**Result** view runs the current query and displays the results in a grid.</span></span> <span data-ttu-id="3a25e-132">基になるデータが変更された場合に、クエリを再実行するには、ステータス バーの [再生] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3a25e-132">If the underlying data has changed and you want to rerun the query, click the Play button in the status bar</span></span>  
  
 <span data-ttu-id="3a25e-133">ビジュアル ツールとテキスト エディターを組み合わせて使用して、データ マイニング クエリをデザインできます。</span><span class="sxs-lookup"><span data-stu-id="3a25e-133">You can design a data mining query by using a combination of the visual tools and the text editor.</span></span> <span data-ttu-id="3a25e-134">テキスト エディターでクエリへの変更を入力して **[デザイン]** ビューに戻ると、変更はすべて失われ、クエリは予測クエリ ビルダーで作成した元のクエリに戻ります。このトピックでは、グラフィカル クエリ ビルダーの使用手順を示します。</span><span class="sxs-lookup"><span data-stu-id="3a25e-134">If you type changes to the query in the text editor and switch back to the **Design** view, all the changes are lost, and the query reverts to the original query created by Prediction Query Builder This topic walks you through use of the graphical query builder.</span></span>  
  
### <a name="to-create-a-prediction-query"></a><span data-ttu-id="3a25e-135">予測クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="3a25e-135">To create a prediction query</span></span>  
  
1.  <span data-ttu-id="3a25e-136">データ マイニング デザイナーの **[マイニング モデル予測]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3a25e-136">Click the **Mining Model Prediction** tab in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="3a25e-137">**[マイニング モデル]** テーブルの **[モデルの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3a25e-137">Click **Select Model** on the **Mining Model** table.</span></span>  
  
     <span data-ttu-id="3a25e-138">**[マイニング モデルの選択]** ダイアログ ボックスが開き、現在のプロジェクトにあるすべてのマイニング構造が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3a25e-138">The **Select Mining Model** dialog box opens to show all the mining structures that exist in the current project.</span></span>  
  
3.  <span data-ttu-id="3a25e-139">予測を作成するモデルを選択して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3a25e-139">Select the model on which you want to create a prediction, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="3a25e-140">**[入力テーブルの選択]** テーブルで、 **[ケース テーブルの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3a25e-140">On the **Select Input Table(s)** table, click **Select Case Table**.</span></span>  
  
     <span data-ttu-id="3a25e-141">**[テーブルの選択]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="3a25e-141">The **Select Table** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="3a25e-142">**[データ ソース]** 一覧で、予測を作成するデータが含まれているデータ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="3a25e-142">In the **Data Source** list, select the data source that contains the data on which to create a prediction.</span></span>  
  
6.  <span data-ttu-id="3a25e-143">**[テーブル名またはビュー名]** ボックスで、予測を作成するデータが含まれているテーブルを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3a25e-143">In the **Table/View Name** box, select the table that contains the data on which to create a prediction, and then click **OK**.</span></span>  
  
     <span data-ttu-id="3a25e-144">入力テーブルを選択すると、列名に基づいてマイニング モデルと入力テーブルの間に既定のマッピングが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3a25e-144">After you select the input table, Prediction Query Builder creates a default mapping between the mining model and the input table, based on the names of the columns.</span></span> <span data-ttu-id="3a25e-145">マッピングを削除するには、 **[マイニング モデル]** テーブル内の列が **[入力テーブルの選択]** テーブル内のマップ先の列にリンクしている線をクリックして選択し、Del キーを押します。</span><span class="sxs-lookup"><span data-stu-id="3a25e-145">To delete a mapping, click to select the line that links the column in the **Mining Model** table to the mapped column in the **Select Input Table(s)** table, and then press DELETE.</span></span> <span data-ttu-id="3a25e-146">**[入力テーブルの選択]** テーブルの列をクリックし、 **[マイニング モデル]** テーブルの対応する列にドラッグして、マッピングを手動で作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="3a25e-146">You can also manually create mappings by clicking a column in the **Select Input Table(s)** table and dragging it onto the corresponding column in the **Mining Model** table.</span></span>  
  
7.  <span data-ttu-id="3a25e-147">次の 3 種類の情報を任意に組み合わせて、予測クエリ ビルダーのグリッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="3a25e-147">Add any combination of the following three types of information to the Prediction Query Builder grid:</span></span>  
  
    -   <span data-ttu-id="3a25e-148">**[マイニング モデル]** ボックスの予測可能列</span><span class="sxs-lookup"><span data-stu-id="3a25e-148">Predictable columns from the **Mining Model** box.</span></span>  
  
    -   <span data-ttu-id="3a25e-149">**[入力テーブルの選択]** ボックスの入力列の任意の組み合わせ</span><span class="sxs-lookup"><span data-stu-id="3a25e-149">Any combination of input columns from the **Select Input Table(s)** box.</span></span>  
  
    -   <span data-ttu-id="3a25e-150">予測関数</span><span class="sxs-lookup"><span data-stu-id="3a25e-150">Prediction functions</span></span>  
  
8.  <span data-ttu-id="3a25e-151">**[マイニング モデル予測]** タブのツール バーにある最初のボタンをクリックし、 **[結果]** を選択して、クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="3a25e-151">Run the query by clicking the first button on the toolbar of the **Mining Model Prediction** tab, and then selecting **Result**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a25e-152">参照</span><span class="sxs-lookup"><span data-stu-id="3a25e-152">See Also</span></span>  
 <span data-ttu-id="3a25e-153">[データマイニングデザイナーでの単一クエリの作成](create-a-singleton-query-in-the-data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="3a25e-153">[Create a Singleton Query in the Data Mining Designer](create-a-singleton-query-in-the-data-mining-designer.md) </span></span>  
 [<span data-ttu-id="3a25e-154">データマイニングクエリ</span><span class="sxs-lookup"><span data-stu-id="3a25e-154">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
