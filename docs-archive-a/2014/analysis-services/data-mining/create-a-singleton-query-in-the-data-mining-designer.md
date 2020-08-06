---
title: データマイニングデザイナーでの単一クエリの作成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- singleton queries [Analysis Services]
- Mining Model Prediction [Analysis Services], singleton queries
ms.assetid: 6cdca8a0-cf16-46eb-a652-0bff820625ab
author: minewiskan
ms.author: owend
ms.openlocfilehash: 07491924dbcf0bd35d049e6a7c290d49becfb45d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632790"
---
# <a name="create-a-singleton-query-in-the-data-mining-designer"></a><span data-ttu-id="76ffb-102">データ マイニング デザイナーでの単一クエリの作成</span><span class="sxs-lookup"><span data-stu-id="76ffb-102">Create a Singleton Query in the Data Mining Designer</span></span>
  <span data-ttu-id="76ffb-103">単一クエリは、1 つのケースに関する予測を作成する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="76ffb-103">A singleton query is useful if you want to create a prediction for a single case.</span></span> <span data-ttu-id="76ffb-104">単一クエリの詳細については、「 [データ マイニング クエリ](data-mining-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76ffb-104">For more information about singleton queries, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
 <span data-ttu-id="76ffb-105">データ マイニング デザイナーの **[マイニング モデル予測]** タブでは、多様なクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="76ffb-105">In the **Mining Model Prediction** tab of Data Mining Designer, you can create many different types of queries.</span></span> <span data-ttu-id="76ffb-106">デザイナーを使用するか、データ マイニング拡張機能 (DMX) ステートメントを入力することにより、クエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="76ffb-106">You can create a query by using the designer, or by typing Data Mining Extensions (DMX) statements.</span></span> <span data-ttu-id="76ffb-107">最初にデザイナーで作成したクエリを、DMX ステートメントを変更するか、WHERE 句や ORDER BY 句を追加することによって変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="76ffb-107">You can also start with the designer and modify the query that it creates by changing the DMX statements, or by adding a WHERE or ORDER BY clause.</span></span>  
  
 <span data-ttu-id="76ffb-108">クエリ デザイン ビューとクエリ テキスト ビューを切り替えるには、ツール バーの最初のボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="76ffb-108">To switch between the query design view and the query text view, click the first button on the toolbar.</span></span> <span data-ttu-id="76ffb-109">クエリ テキスト ビューでは、予測クエリ ビルダーによって作成される DMX コードを表示できます。</span><span class="sxs-lookup"><span data-stu-id="76ffb-109">When you are in the query text view, you can view the DMX code that Prediction Query Builder creates.</span></span> <span data-ttu-id="76ffb-110">また、クエリの実行、クエリの変更、および変更済みのクエリの実行も可能です。</span><span class="sxs-lookup"><span data-stu-id="76ffb-110">You can also run the query, modify the query, and run the modified query.</span></span> <span data-ttu-id="76ffb-111">ただし、クエリ デザイン ビューに戻ると、変更したクエリは保持されません。</span><span class="sxs-lookup"><span data-stu-id="76ffb-111">However, the modified query is not persisted if you switch back to the query design view.</span></span>  
  
 <span data-ttu-id="76ffb-112">次のコードは、メーリング対象モデル TM_Decision_Tree に対する単一クエリの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="76ffb-112">The following code shows an example of a singleton query against the targeted mailing model, TM_Decision_Tree.</span></span>  
  
```  
SELECT [Bike Buyer], PredictProbability([Bike Buyer]) as ProbableBuyer  
FROM [TM_Decision_Tree]  
NATURAL PREDICTION JOIN  
(SELECT '2' AS [Number Children At Home], '45' as [Age])  
AS [t]  
```  
  
 <span data-ttu-id="76ffb-113">以下の手順は、この予測クエリを作成する方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="76ffb-113">The following steps explain how to create this prediction query.</span></span>  
  
### <a name="to-create-a-singleton-query-by-using-the-data-mining-designer"></a><span data-ttu-id="76ffb-114">データ マイニング デザイナーを使用して単一クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="76ffb-114">To create a singleton query by using the Data Mining Designer</span></span>  
  
1.  <span data-ttu-id="76ffb-115">データ マイニング デザイナーの **[マイニング モデル予測]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="76ffb-115">Click the **Mining Model Prediction** tab in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="76ffb-116">**[マイニング モデル]** テーブルの **[モデルの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="76ffb-116">Click **Select Model** on the **Mining Model** table.</span></span>  
  
     <span data-ttu-id="76ffb-117">**[マイニング モデルの選択]** ダイアログ ボックスが開き、現在のプロジェクトにあるすべてのマイニング構造が表示されます。</span><span class="sxs-lookup"><span data-stu-id="76ffb-117">The **Select Mining Model** dialog box opens to show all the mining structures that exist in the current project.</span></span>  
  
     <span data-ttu-id="76ffb-118">予測の作成に使用するモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="76ffb-118">Select the model that you want to use for creating a prediction.</span></span>  
  
     <span data-ttu-id="76ffb-119">たとえば、このトピックの冒頭に示したサンプル コードを作成するには、TM_Decision_Tree を選択して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="76ffb-119">For example, to create the sample code shown at the start of this topic, select TM_Decision_Tree, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="76ffb-120">**[マイニング モデル予測]** タブのツール バー上の **[単一クエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="76ffb-120">Click **Singleton query** on the toolbar of the **Mining Model Prediction** tab.</span></span>  
  
     <span data-ttu-id="76ffb-121">**[単一クエリ入力]** テーブルがタブに表示され、テーブルの列が **[マイニング モデル]** テーブルの列に自動的にマップされます。</span><span class="sxs-lookup"><span data-stu-id="76ffb-121">The **Singleton Query Input** table appears on the tab, with the columns automatically mapped to the columns in the **Mining Model** table.</span></span>  
  
4.  <span data-ttu-id="76ffb-122">**[単一クエリ入力]** テーブルの **[値]** 列で、予測を作成するケースについて説明した値を選択します。</span><span class="sxs-lookup"><span data-stu-id="76ffb-122">On the **Singleton Query Input** table, select values in the **Value** column to describe the case for which you want to create a prediction.</span></span>  
  
     <span data-ttu-id="76ffb-123">たとえば、[ **Number Children At Home**] で [ **2** ] を選択し、「Age」と入力し `45` ます。 **Age**</span><span class="sxs-lookup"><span data-stu-id="76ffb-123">For example, select **2** for **Number Children At Home**, and then type `45` for **Age**.</span></span>  
  
5.  <span data-ttu-id="76ffb-124">[**マイニングモデル**] テーブルの予測可能列を、タブの下部にある [**ソース**] 列にドラッグします。必要に応じて、列の別名を入力できます。</span><span class="sxs-lookup"><span data-stu-id="76ffb-124">Drag a predictable column from the **Mining Model** table to the **Source** column at the bottom of the tab. Optionally, you can type an alias for the column.</span></span>  
  
     <span data-ttu-id="76ffb-125">たとえば、 **[Bike Buyer]** を **[変換元]** 列にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="76ffb-125">For example, drag **Bike Buyer** to the **Source** column.</span></span>  
  
6.  <span data-ttu-id="76ffb-126">クエリに関数を追加するには、 **[変換元]** 列のドロップダウン リストから **[予測関数]** または **[カスタム式]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="76ffb-126">Add any additional functions to the query by selecting **Prediction Function** or **Custom Expression** from the drop-down list in the **Source** column.</span></span>  
  
     <span data-ttu-id="76ffb-127">たとえば、 **[予測関数]** をクリックして **[PredictProbability]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="76ffb-127">For example, click **Prediction Function**, and select **PredictProbability**.</span></span>  
  
7.  <span data-ttu-id="76ffb-128">**PredictProbability** 行の **[条件と引数]** をクリックし、予測する列の名前と、必要に応じて予測する特定の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="76ffb-128">Click **Criteria/Argument** in the **PredictProbability** row, and type the name of the column to predict, and optionally a specific value to predict.</span></span>  
  
     <span data-ttu-id="76ffb-129">たとえば、「 `[Bike Buyer], 1`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="76ffb-129">For example, type `[Bike Buyer], 1`.</span></span>  
  
8.  <span data-ttu-id="76ffb-130">**PredictProbability** 行の **[別名]** ボックスをクリックし、新しい列を参照する名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="76ffb-130">Click the **Alias** box in the **PredictProbability** row, and type a name to refer to the new column.</span></span>  
  
     <span data-ttu-id="76ffb-131">たとえば、「 `ProbableBuyer`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="76ffb-131">For example, type `ProbableBuyer`.</span></span>  
  
9. <span data-ttu-id="76ffb-132">**[マイニング モデル予測]** タブのツール バー上の **[クエリ結果ビューに切り替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="76ffb-132">Click **Switch to query result view** on the toolbar of the **Mining Model Prediction** tab.</span></span>  
  
     <span data-ttu-id="76ffb-133">新しい画面が開き、クエリの結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="76ffb-133">A new screen opens to show the result of the query.</span></span> <span data-ttu-id="76ffb-134">作成した DMX ステートメントを表示するには、 **[SQL]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="76ffb-134">To view the DMX statement that you just created, click **SQL**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76ffb-135">参照</span><span class="sxs-lookup"><span data-stu-id="76ffb-135">See Also</span></span>  
 [<span data-ttu-id="76ffb-136">予測クエリ &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="76ffb-136">Prediction Queries &#40;Data Mining&#41;</span></span>](prediction-queries-data-mining.md)  
  
  
