---
title: 構造に対してテストデータセットを指定する (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 75cd508f-b126-418b-848d-3c4c3e6c303f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c1430706a0ec2cd3ddc0eaee18d7001d05fefae1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631412"
---
# <a name="specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial"></a><span data-ttu-id="c76f8-102">構造のテスト データ セットの指定 (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="c76f8-102">Specifying a Testing Data Set for the Structure (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="c76f8-103">データ マイニング ウィザードの最後の数画面では、データをテスト セットとトレーニング セットに分割します。</span><span class="sxs-lookup"><span data-stu-id="c76f8-103">In the final few screens of the Data Mining Wizard you will split your data into a testing set and a training set.</span></span> <span data-ttu-id="c76f8-104">次に、構造に名前を付けて、モデルのドリルスルーを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c76f8-104">You will then name your structure and enable drillthrough on the model.</span></span>  
  
## <a name="specifying-a-testing-set"></a><span data-ttu-id="c76f8-105">テスト セットの指定</span><span class="sxs-lookup"><span data-stu-id="c76f8-105">Specifying a Testing Set</span></span>  
 <span data-ttu-id="c76f8-106">マイニング構造を作成する際にデータをトレーニング セットとテスト セットに分割すると、後で作成するマイニング モデルの精度を簡単に評価できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c76f8-106">Separating data into training and testing sets when you create a mining structure makes it possible to easily assess the accuracy of the mining models that you create later.</span></span> <span data-ttu-id="c76f8-107">テストセットの詳細については、「[データセットのトレーニングとテスト](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c76f8-107">For more information on testing sets, see [Training and Testing Data Sets](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md).</span></span>  
  
#### <a name="to-specify-the-testing-set"></a><span data-ttu-id="c76f8-108">テスト セットを指定するには</span><span class="sxs-lookup"><span data-stu-id="c76f8-108">To specify the testing set</span></span>  
  
1.  <span data-ttu-id="c76f8-109">[テスト**セットの作成**] ページで、**テスト用データの割合**を既定値のままにし `30` ます。</span><span class="sxs-lookup"><span data-stu-id="c76f8-109">On the **Create Testing Set** page, for **Percentage of data for testing**, leave the default value of `30`.</span></span>  
  
2.  <span data-ttu-id="c76f8-110">**[テストデータセット内のケースの最大数**] に、「」と入力 `1000` します。</span><span class="sxs-lookup"><span data-stu-id="c76f8-110">For **Maximum number of cases in testing data set**, type `1000`.</span></span>  
  
3.  <span data-ttu-id="c76f8-111">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c76f8-111">Click **Next**.</span></span>  
  
## <a name="specifying-drillthrough"></a><span data-ttu-id="c76f8-112">ドリルスルーの指定</span><span class="sxs-lookup"><span data-stu-id="c76f8-112">Specifying Drillthrough</span></span>  
 <span data-ttu-id="c76f8-113">ドリルスルーは、モデルおよび構造で有効にできます。</span><span class="sxs-lookup"><span data-stu-id="c76f8-113">Drillthrough can be enabled on models and on structures.</span></span> <span data-ttu-id="c76f8-114">このダイアログ ボックスのチェック ボックスを使って、該当するモデルに対するドリルスルーを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c76f8-114">The checkbox in this dialog box enables drillthrough on the named model.</span></span> <span data-ttu-id="c76f8-115">モデルの処理後は、モデルの作成に使用されたトレーニング データから、詳細情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="c76f8-115">After the model has been processed,  you will be able to retrieve detailed information from the training data that were used to create the model.</span></span>  
  
 <span data-ttu-id="c76f8-116">基になるマイニング構造もドリルスルーを許可するように構成されている場合は、モデル ケースとマイニング構造の両方から、詳細な情報 (マイニング モデルに含まれていなかった列など) を取得できます。</span><span class="sxs-lookup"><span data-stu-id="c76f8-116">If the underlying mining structure has also been configured to allow drillthrough, you can retrieve detailed information from both the model cases and the mining structure, including columns that were not included in the mining model.</span></span> <span data-ttu-id="c76f8-117">詳細については、「 [ドリルスルー クエリ (データ マイニング)](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c76f8-117">For more information, see [Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md).</span></span>  
  
#### <a name="to-name-the-model-and-structure-and-specify-drillthrough"></a><span data-ttu-id="c76f8-118">モデルおよび構造に名前を付けてドリルスルーを指定するには</span><span class="sxs-lookup"><span data-stu-id="c76f8-118">To name the model and structure and specify drillthrough</span></span>  
  
1.  <span data-ttu-id="c76f8-119">[**ウィザードの完了**] ページの [**マイニング構造名**] に「」と入力 `Targeted Mailing` します。</span><span class="sxs-lookup"><span data-stu-id="c76f8-119">On the **Completing the Wizard** page, in **Mining structure name**, type `Targeted Mailing`.</span></span>  
  
2.  <span data-ttu-id="c76f8-120">[**マイニングモデル名**] に「」と入力 `TM_Decision_Tree` します。</span><span class="sxs-lookup"><span data-stu-id="c76f8-120">In **Mining model name**, type `TM_Decision_Tree`.</span></span>  
  
3.  <span data-ttu-id="c76f8-121">[ドリルスルーを**許可する**] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="c76f8-121">Select the **Allow drill through** check box.</span></span>  
  
4.  <span data-ttu-id="c76f8-122">**プレビュー**ウィンドウを確認します。</span><span class="sxs-lookup"><span data-stu-id="c76f8-122">Review the **Preview** pane.</span></span> <span data-ttu-id="c76f8-123">[**キー**]、[**入力**]、または [**予測可能**] として選択した列のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c76f8-123">Notice that only those columns selected as **Key**, **Input** or **Predictable** are shown.</span></span> <span data-ttu-id="c76f8-124">選択した他の列 (AddressLine1 など) は、モデルの作成には使用されませんが、基になる構造で使用することができ、モデルを処理および配置した後でクエリすることができます。</span><span class="sxs-lookup"><span data-stu-id="c76f8-124">The other columns you selected (e.g., AddressLine1) are not used for building the model but will be available in the underlying structure, and can be queried after the model is processed and deployed.</span></span>  
  
5.  <span data-ttu-id="c76f8-125">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c76f8-125">Click **Finish**.</span></span>  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="c76f8-126">このレッスンの前の作業</span><span class="sxs-lookup"><span data-stu-id="c76f8-126">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="c76f8-127">データ型とコンテンツの種類の指定 &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="c76f8-127">Specifying the Data Type and Content Type &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="c76f8-128">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="c76f8-128">Next Lesson</span></span>  
 [<span data-ttu-id="c76f8-129">レッスン 3: モデルの追加と処理</span><span class="sxs-lookup"><span data-stu-id="c76f8-129">Lesson 3: Adding and Processing Models</span></span>](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
  
## <a name="see-also"></a><span data-ttu-id="c76f8-130">参照</span><span class="sxs-lookup"><span data-stu-id="c76f8-130">See Also</span></span>  
 <span data-ttu-id="c76f8-131">[マイニングモデルのドリルスルーを有効にする](../../2014/analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="c76f8-131">[Enable Drillthrough for a Mining Model](../../2014/analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md) </span></span>  
 <span data-ttu-id="c76f8-132">[データマイニング &#40;のドリルスルークエリ&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="c76f8-132">[Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md) </span></span>  
 [<span data-ttu-id="c76f8-133">データマイニング &#40;トレーニングウィザードを指定し&#41;</span><span class="sxs-lookup"><span data-stu-id="c76f8-133">Specify the Training Data &#40;Data Mining Wizard&#41;</span></span>](../../2014/analysis-services/specify-the-training-data-data-mining-wizard.md)  
  
  
