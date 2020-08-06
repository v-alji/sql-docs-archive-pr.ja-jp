---
title: 予測構造の変更 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1a6c138e-643b-4ae6-ad08-93631f149c20
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9acf410fe04c53493e559257832e5e21727bc45b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631418"
---
# <a name="modifying-the-forecasting-structure-intermediate-data-mining-tutorial"></a><span data-ttu-id="b8a1e-102">Forecasting 構造の変更 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="b8a1e-102">Modifying the Forecasting Structure (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="b8a1e-103">前の作業で作成したマイニング構造には予測モデルが 1 つ存在します。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-103">The mining structure that you created in the previous task contains a single forecasting model.</span></span> <span data-ttu-id="b8a1e-104">このモデルを処理して検証する前に、マイニング構造に少し手を加え、プロパティの 1 つを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-104">Before you process and explore the model, you must change its structure slightly and modify one of its properties.</span></span>  
  
## <a name="modifying-the-mining-structure"></a><span data-ttu-id="b8a1e-105">マイニング構造の修正</span><span class="sxs-lookup"><span data-stu-id="b8a1e-105">Modifying the Mining Structure</span></span>  
 <span data-ttu-id="b8a1e-106">マイニング構造を変更するには、データマイニングデザイナーの [**マイニング構造**] タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-106">You can change the mining structure by using the **Mining Structure** tab of Data Mining Designer.</span></span> <span data-ttu-id="b8a1e-107">データ マイニング ウィザードでモデルを作成するときは、ReportingDate 列、ModelRegion 列、Quantity 列の 3 つを使用しました。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-107">When you created the model with the Data Mining Wizard, you used three columns: ReportingDate, ModelRegion, and Quantity.</span></span> <span data-ttu-id="b8a1e-108">ただし、**予測**テーブルには、売上高の予測に使用できる amount 列も含まれています。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-108">However, the **Forecasting** table also contains an Amount column, which you can use to forecast the amount of sales.</span></span> <span data-ttu-id="b8a1e-109">[**マイニング構造**] タブを使用すると、データソースビューからマイニング構造にこの列を追加できます。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-109">By using the **Mining Structure** tab, you can add this column from the data source view to the mining structure.</span></span>  
  
#### <a name="to-add-the-amount-column-to-the-forecasting-mining-structure"></a><span data-ttu-id="b8a1e-110">Amount 列を予測マイニング構造に追加するには</span><span class="sxs-lookup"><span data-stu-id="b8a1e-110">To add the Amount column to the Forecasting mining structure</span></span>  
  
1.  <span data-ttu-id="b8a1e-111">データマイニングデザイナーの [**マイニング構造**] タブの [**データソースビュー** ] ペインで、vTimeSeries テーブルの Amount 列を選択します。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-111">On the **Mining Structure** tab of Data Mining Designer, in the **Data Source View** pane, select the Amount column in the vTimeSeries table.</span></span>  
  
2.  <span data-ttu-id="b8a1e-112">[**データソースビュー** ] ペインの [Amount] 列を、**予測**構造の列の一覧にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-112">Drag the Amount column from the **Data Source View** pane into the list of columns for the **Forecasting** structure.</span></span>  
  
     <span data-ttu-id="b8a1e-113">Amount 列が**予測**マイニング構造に含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-113">The Amount column is now included in the **Forecasting** mining structure.</span></span>  
  
## <a name="modifying-the-columns-in-the-mining-model"></a><span data-ttu-id="b8a1e-114">マイニング モデルの列の変更</span><span class="sxs-lookup"><span data-stu-id="b8a1e-114">Modifying the Columns in the Mining Model</span></span>  
 <span data-ttu-id="b8a1e-115">マイニング構造に新しい列を追加したので、次は、マイニング モデルにおけるその列の使用方法を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-115">Because you added a new column to the structure, you must define how the model will use the column.</span></span> <span data-ttu-id="b8a1e-116">列を使用する方法は、データマイニングデザイナーの [**マイニングモデル**] タブで指定できます。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-116">You can specify how the column will be used on the **Mining Models** tab of Data Mining Designer.</span></span>  
  
 <span data-ttu-id="b8a1e-117">[**マイニングモデル**] タブには、マイニング構造に含まれる列がグリッドの [**構造**] 列に一覧表示され、モデルの名前を持つ列にマイニングモデルに含まれている列が一覧表示されます (この場合は [**予測**])。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-117">The **Mining Models** tab lists the columns that the mining structure contains in the **Structure** column of the grid, and lists the columns that the mining model contains in the column that has the name of the model, in this case **Forecasting**.</span></span> <span data-ttu-id="b8a1e-118">更新するには、列名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-118">Click the names of the columns to make modifications.</span></span> <span data-ttu-id="b8a1e-119">**予測**マイニングモデルでは、[Amount] 列が入力列として使用され、将来の売上を予測するためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-119">In the **Forecasting** mining model, the Amount column is used as an input column and is also used to forecast future sales.</span></span> <span data-ttu-id="b8a1e-120">したがって、入力列として、さらには予測可能列として使用できるように、この列のプロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-120">Therefore, you must set the properties of the column so that it can be used as both an input column and a predictable column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b8a1e-121">[**マイニングモデル**] タブでは、同じ構造に基づいて新しいモデルを作成することもできます。また、各モデルのアルゴリズムと列のプロパティを調整することもできます。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-121">In the **Mining Models** tab, you can also create new models based on the same structure, and you can adjust the algorithm and column properties for each model.</span></span> <span data-ttu-id="b8a1e-122">ただし、これらの変更を反映するには、モデルを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-122">However, you must process the model before these changes take effect.</span></span>  
  
#### <a name="to-define-how-the-amount-column-will-be-used"></a><span data-ttu-id="b8a1e-123">Amount 列の使用方法を定義するには</span><span class="sxs-lookup"><span data-stu-id="b8a1e-123">To define how the Amount column will be used</span></span>  
  
1.  <span data-ttu-id="b8a1e-124">[**マイニングモデル**] タブのグリッドの [**予測**] 列で、Amount 行のセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-124">In the **Forecasting** column of the grid on the **Mining Models** tab, click the cell in the Amount row.</span></span>  
  
2.  <span data-ttu-id="b8a1e-125">一覧から [ **Predict** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-125">Select **Predict** from the list.</span></span>  
  
     <span data-ttu-id="b8a1e-126">入力列および予測可能列として、Amount 列を使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-126">The Amount column is now both an input column and a predictable column.</span></span>  
  
 <span data-ttu-id="b8a1e-127">列を選択し、[**プロパティ**] ウィンドウを開くことで、個々の列のプロパティを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-127">You can also change the properties of individual columns by selecting the column and opening the **Properties** window.</span></span> <span data-ttu-id="b8a1e-128">[**プロパティ**] ウィンドウを開くには、列名を右クリックし、[**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-128">To open the **Properties** window, right-click the column name, and then select **Properties**.</span></span> <span data-ttu-id="b8a1e-129">各モデルの列内でプロパティを変更する場合は、そのモデルのプロパティのみを変更できます。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-129">If you change a property within the column for an individual model, you can change the properties only for that model.</span></span> <span data-ttu-id="b8a1e-130">ただし、**構造**列内のプロパティを変更すると、その変更は構造に関連付けられているすべてのモデルに影響を及ぼします。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-130">However, when you change a property within the **Structure** column, the change affects every model that is associated with the structure.</span></span> <span data-ttu-id="b8a1e-131">モデルまたは構造に変更を加えた場合は、必ず再処理して影響を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8a1e-131">Whenever you make changes to the model or structure, you must reprocess to see the effects.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="b8a1e-132">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="b8a1e-132">Next Task in Lesson</span></span>  
 [<span data-ttu-id="b8a1e-133">予測モデルのカスタマイズと処理 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="b8a1e-133">Customizing and Processing the Forecasting Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="b8a1e-134">参照</span><span class="sxs-lookup"><span data-stu-id="b8a1e-134">See Also</span></span>  
 <span data-ttu-id="b8a1e-135">[マイニング構造 &#40;Analysis Services-データマイニング&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="b8a1e-135">[Mining Structures &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="b8a1e-136">マイニング モデル (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="b8a1e-136">Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
  
