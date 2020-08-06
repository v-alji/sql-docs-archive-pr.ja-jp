---
title: DMX テンプレート |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2a577e52-821d-4bd3-ba35-075a6be285c9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 79c8615933baf4fa3d80974daae91b4d1c7fa101
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644215"
---
# <a name="dmx-templates"></a><span data-ttu-id="f952e-102">[DMX テンプレート]</span><span class="sxs-lookup"><span data-stu-id="f952e-102">DMX Templates</span></span>
  <span data-ttu-id="f952e-103">データ マイニング テンプレートは、高度なクエリをすばやく作成するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f952e-103">The data mining templates help you quickly build sophisticated queries.</span></span> <span data-ttu-id="f952e-104">DMX クエリの一般的な構文は詳しく解説されており、テンプレートを使用すると、引数とデータ ソースをクリックおよびポイントする方法でクエリを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="f952e-104">Although the general syntax for DMX queries is well documented, using the templates makes it easier to build queries by clicking and pointing to arguments and data sources.</span></span>  
  
## <a name="using-the-templates"></a><span data-ttu-id="f952e-105">テンプレートの使用</span><span class="sxs-lookup"><span data-stu-id="f952e-105">Using the Templates</span></span>  
  
1.  <span data-ttu-id="f952e-106">Excel 用のデータマイニングクライアントで、[**クエリ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f952e-106">In the Data Mining Client for Excel, click **Query**.</span></span>  
  
2.  <span data-ttu-id="f952e-107">ウィザードの [**開始**] ページで、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f952e-107">On the wizard **Start** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="f952e-108">ページで、[**モデル**] を選択し、[**詳細設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f952e-108">On the page, **Select Model**, click **Advanced**.</span></span>  
  
     <span data-ttu-id="f952e-109">**ヒント:** モデルに対して予測クエリを作成する場合は、まずモデルを選択し、[**詳細設定**] をクリックすると、モデル名を使用してテンプレートを事前に設定できます。</span><span class="sxs-lookup"><span data-stu-id="f952e-109">**Tip:** If you are going to create a prediction query on a model, you can select the model first, and then click **Advanced**, to prepopulate the template with the model name.</span></span>  
  
4.  <span data-ttu-id="f952e-110">**データマイニング詳細クエリエディター**で、[ **DMX テンプレート**] をクリックし、テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="f952e-110">In the **Data Mining Advanced Query Editor**, click **DMX Templates**, and select a template.</span></span>  
  
5.  <span data-ttu-id="f952e-111">Enter キーを押して、DMX クエリ ペインにテンプレートを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="f952e-111">Press ENTER to load the template into the DMX Query pane.</span></span>  
  
6.  <span data-ttu-id="f952e-112">テンプレート内でリンクのクリックを続け、ダイアログ ボックスが表示されたときに、適切な出力、モデル、またはパラメーターを選択します。</span><span class="sxs-lookup"><span data-stu-id="f952e-112">Continue clicking the links in the template, and as the dialog box appears, select an appropriate output, model, or parameter.</span></span>  
  
     <span data-ttu-id="f952e-113">予測クエリの場合、最初に入力データセットを選択し、次に列をマップします。</span><span class="sxs-lookup"><span data-stu-id="f952e-113">For prediction queries, choose the input dataset first, and then map the columns.</span></span>  
  
7.  <span data-ttu-id="f952e-114">[**クエリの編集**] をクリックしてテキストエディタービューに切り替え、クエリを手動で変更します。</span><span class="sxs-lookup"><span data-stu-id="f952e-114">Click **Edit Query** to switch to text editor view and manually change the query.</span></span>  
  
     <span data-ttu-id="f952e-115">ただし、クエリ エディターでの作業中にビューを切り替えた場合、それまでのビューに表示されていた情報はすべて消去されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f952e-115">Be aware, however, that if you switch views when working in the query editor, any information that you had in the previous view will be cleared.</span></span> <span data-ttu-id="f952e-116">ビューを切り替える前に、DMX ステートメントをコピーして別のファイルに貼り付けて、作業を保存してください。</span><span class="sxs-lookup"><span data-stu-id="f952e-116">Before changing views, save your work by copying and pasting the DMX statements to a separate file.</span></span>  
  
8.  <span data-ttu-id="f952e-117">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f952e-117">Click **Finish**.</span></span> <span data-ttu-id="f952e-118">[**変換先の選択**] ダイアログボックスで、結果を保存する場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="f952e-118">In the **Choose Destination** dialog  box, specify where you want the result saved.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
> [!NOTE]  
>  <span data-ttu-id="f952e-119">ステートメントを正常に実行した場合、サーバーに送信した DMX ステートメントも**トレース**ウィンドウに記録されます。</span><span class="sxs-lookup"><span data-stu-id="f952e-119">If you executed a statement successfully, the DMX statement that you sent to the server is also recorded in the **Trace** window.</span></span> <span data-ttu-id="f952e-120">トレース機能の使用方法の詳細については、「 [trace &#40;Data マイニング Client For Excel&#41;](trace-data-mining-client-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f952e-120">For more information about how to use the Trace feature, see [Trace &#40;Data Mining Client for Excel&#41;](trace-data-mining-client-for-excel.md).</span></span>  
  
 <span data-ttu-id="f952e-121">データマイニング詳細クエリエディターの使用方法の詳細については、「[クエリ &#40;SQL Server データマイニングアドイン&#41;](query-sql-server-data-mining-add-ins.md)および[高度なデータマイニングクエリエディター](advanced-data-mining-query-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f952e-121">For more information about how to use the Data Mining Advanced Query Editor, see [Query &#40;SQL Server Data Mining Add-ins&#41;](query-sql-server-data-mining-add-ins.md) and [Advanced Data Mining Query Editor](advanced-data-mining-query-editor.md).</span></span>  
  
## <a name="list-of-dmx-templates"></a><span data-ttu-id="f952e-122">DMX テンプレートの一覧</span><span class="sxs-lookup"><span data-stu-id="f952e-122">List of DMX Templates</span></span>  
 <span data-ttu-id="f952e-123">次の DMX テンプレートは、Excel 用のデータ マイニング クライアントに含まれています。</span><span class="sxs-lookup"><span data-stu-id="f952e-123">The following DMX templates are included in the Data Mining Client for Excel.</span></span>  
  
 <span data-ttu-id="f952e-124">**予測**</span><span class="sxs-lookup"><span data-stu-id="f952e-124">**Prediction**</span></span>  
  
 <span data-ttu-id="f952e-125">入れ子になったテーブルや外部データ ソースを使用するクエリなど、アドイン内のウィザードでサポートされていないクエリを含め、高度な予測クエリを作成するには、次のテンプレートを使用します。</span><span class="sxs-lookup"><span data-stu-id="f952e-125">Use these templates to create advanced prediction queries, including queries not supported by the wizards in the add-ins, such as queries that use nested tables or external data sources.</span></span>  
  
-   <span data-ttu-id="f952e-126">フィルター選択された予測</span><span class="sxs-lookup"><span data-stu-id="f952e-126">Filtered predictions</span></span>  
  
-   <span data-ttu-id="f952e-127">フィルター選択された入れ子になった予測</span><span class="sxs-lookup"><span data-stu-id="f952e-127">Filtered nested predictions</span></span>  
  
-   <span data-ttu-id="f952e-128">入れ子になった予測</span><span class="sxs-lookup"><span data-stu-id="f952e-128">Nested predictions</span></span>  
  
-   <span data-ttu-id="f952e-129">単一予測</span><span class="sxs-lookup"><span data-stu-id="f952e-129">Singleton predictions</span></span>  
  
-   <span data-ttu-id="f952e-130">標準予測</span><span class="sxs-lookup"><span data-stu-id="f952e-130">Standard predictions</span></span>  
  
-   <span data-ttu-id="f952e-131">時系列予測</span><span class="sxs-lookup"><span data-stu-id="f952e-131">Time series predictions</span></span>  
  
-   <span data-ttu-id="f952e-132">TOP 予測クエリ</span><span class="sxs-lookup"><span data-stu-id="f952e-132">TOP prediction query</span></span>  
  
-   <span data-ttu-id="f952e-133">入れ子になったテーブルでの TOP 予測クエリ</span><span class="sxs-lookup"><span data-stu-id="f952e-133">TOP prediction query on nested table</span></span>  
  
 <span data-ttu-id="f952e-134">**作成**</span><span class="sxs-lookup"><span data-stu-id="f952e-134">**Create**</span></span>  
  
 <span data-ttu-id="f952e-135">カスタム モデルおよびデータ構造を作成するには、これらのテンプレートを使用します。</span><span class="sxs-lookup"><span data-stu-id="f952e-135">Use these templates to build custom models or data structures.</span></span> <span data-ttu-id="f952e-136">ウィザードでサポートされているモデルに限定されません。接続先ののインスタンスでサポートされているデータマイニングアルゴリズム [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] (プラグインアルゴリズムを含む) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f952e-136">You are not limited to the models supported by the wizards - you can use any data mining algorithm supported by the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you are connected to, including plug-in algorithms.</span></span>  
  
-   <span data-ttu-id="f952e-137">マイニングモデル</span><span class="sxs-lookup"><span data-stu-id="f952e-137">Mining model</span></span>  
  
-   <span data-ttu-id="f952e-138">マイニング構造</span><span class="sxs-lookup"><span data-stu-id="f952e-138">Mining structure</span></span>  
  
-   <span data-ttu-id="f952e-139">提示されたデータを含むマイニング構造</span><span class="sxs-lookup"><span data-stu-id="f952e-139">Mining structure with holdout</span></span>  
  
-   <span data-ttu-id="f952e-140">一時的なモデル</span><span class="sxs-lookup"><span data-stu-id="f952e-140">Temporary model</span></span>  
  
-   <span data-ttu-id="f952e-141">一時的な構造</span><span class="sxs-lookup"><span data-stu-id="f952e-141">Temporary structure</span></span>  
  
 <span data-ttu-id="f952e-142">**モデルのプロパティ**</span><span class="sxs-lookup"><span data-stu-id="f952e-142">**Model Properties**</span></span>  
  
 <span data-ttu-id="f952e-143">モデルとトレーニング セットに関するメタデータを取得するクエリを作成するには、次のテンプレートを使用します。</span><span class="sxs-lookup"><span data-stu-id="f952e-143">Use these templates to create queries that get metadata about the model and the training set.</span></span> <span data-ttu-id="f952e-144">また、モデル コンテンツから詳細を取得することや、トレーニング データの統計プロファイルを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="f952e-144">You can also retrieve details from the model content, or get a statistical profile of the training data.</span></span>  
  
-   <span data-ttu-id="f952e-145">マイニングモデルコンテンツ</span><span class="sxs-lookup"><span data-stu-id="f952e-145">Mining model content</span></span>  
  
-   <span data-ttu-id="f952e-146">列の最小値と最大値</span><span class="sxs-lookup"><span data-stu-id="f952e-146">Minimum and maximum column values</span></span>  
  
-   <span data-ttu-id="f952e-147">マイニング構造のテスト/トレーニング ケース</span><span class="sxs-lookup"><span data-stu-id="f952e-147">Mining structure test/training cases</span></span>  
  
-   <span data-ttu-id="f952e-148">不連続列の値</span><span class="sxs-lookup"><span data-stu-id="f952e-148">Discrete column values</span></span>  
  
 <span data-ttu-id="f952e-149">**管理**</span><span class="sxs-lookup"><span data-stu-id="f952e-149">**Management**</span></span>  
  
 <span data-ttu-id="f952e-150">これらのテンプレートを使用して、モデルのインポートとエクスポート、モデルの削除、モデルやデータ構造の消去など、DMX でサポートされているあらゆる管理タスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="f952e-150">Use these templates to perform any management task supported by DMX, which includes importing and exporting models, deleting models, and clearing models or data structures.</span></span>  
  
-   <span data-ttu-id="f952e-151">マイニング モデルの消去</span><span class="sxs-lookup"><span data-stu-id="f952e-151">Clear mining model</span></span>  
  
-   <span data-ttu-id="f952e-152">構造とモデルの消去</span><span class="sxs-lookup"><span data-stu-id="f952e-152">Clear structure and models</span></span>  
  
-   <span data-ttu-id="f952e-153">マイニング構造の消去</span><span class="sxs-lookup"><span data-stu-id="f952e-153">Clear mining structure</span></span>  
  
-   <span data-ttu-id="f952e-154">マイニングモデルの削除</span><span class="sxs-lookup"><span data-stu-id="f952e-154">Delete mining model</span></span>  
  
-   <span data-ttu-id="f952e-155">マイニング構造の削除</span><span class="sxs-lookup"><span data-stu-id="f952e-155">Delete mining structure</span></span>  
  
-   <span data-ttu-id="f952e-156">マイニング モデル名の変更</span><span class="sxs-lookup"><span data-stu-id="f952e-156">Rename mining model</span></span>  
  
-   <span data-ttu-id="f952e-157">マイニング構造名の変更</span><span class="sxs-lookup"><span data-stu-id="f952e-157">Rename mining structure</span></span>  
  
-   <span data-ttu-id="f952e-158">マイニングモデルのトレーニング</span><span class="sxs-lookup"><span data-stu-id="f952e-158">Train mining model</span></span>  
  
-   <span data-ttu-id="f952e-159">入れ子になったマイニング構造のトレーニング</span><span class="sxs-lookup"><span data-stu-id="f952e-159">Train nested mining structure</span></span>  
  
-   <span data-ttu-id="f952e-160">マイニング構造のトレーニング</span><span class="sxs-lookup"><span data-stu-id="f952e-160">Train mining structure</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="f952e-161">必要条件</span><span class="sxs-lookup"><span data-stu-id="f952e-161">Requirements</span></span>  
 <span data-ttu-id="f952e-162">使用するテンプレートによっては、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーにアクセスしてクエリを実行するために管理権限が必要になります。</span><span class="sxs-lookup"><span data-stu-id="f952e-162">Depending on which template you are using, you might need administrative permissions to access the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server and execute the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f952e-163">参照</span><span class="sxs-lookup"><span data-stu-id="f952e-163">See Also</span></span>  
 [<span data-ttu-id="f952e-164">データ マイニング モデルの作成</span><span class="sxs-lookup"><span data-stu-id="f952e-164">Creating a Data Mining Model</span></span>](creating-a-data-mining-model.md)  
  
  
