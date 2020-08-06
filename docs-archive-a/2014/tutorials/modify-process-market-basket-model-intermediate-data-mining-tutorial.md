---
title: マーケットバスケットモデルの変更と処理 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b6019413-aebd-4ff7-831a-644572ad88b1
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 369de98e944c5ccf5d06ef61eaa16c06bb864e7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631421"
---
# <a name="modifying-and-processing-the-market-basket-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="e769a-102">マーケット バスケット モデルの変更と処理 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="e769a-102">Modifying and Processing the Market Basket Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="e769a-103">作成した association マイニングモデルを処理する前に、*サポート*と*確率*の2つのパラメーターの既定値を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e769a-103">Before you process the association mining model that you created, you must change the default values of two of the parameters: *Support* and *Probability*.</span></span>  
  
-   <span data-ttu-id="e769a-104">*サポート*は、ルールが有効と見なされる前に存在している必要があるケースの割合を定義します。</span><span class="sxs-lookup"><span data-stu-id="e769a-104">*Support* defines the percentage of cases in which a rule must exist before it is considered valid.</span></span> <span data-ttu-id="e769a-105">ここでは、1% 以上のケースでルールが検出される必要があるように指定します。</span><span class="sxs-lookup"><span data-stu-id="e769a-105">You will specify that a rule must be found in at least 1 percent of cases.</span></span>  
  
-   <span data-ttu-id="e769a-106">*確率*は、アソシエーションが有効と見なされるまでの確率を定義します。</span><span class="sxs-lookup"><span data-stu-id="e769a-106">*Probability* defines how likely an association must be before it is considered valid.</span></span> <span data-ttu-id="e769a-107">ここでは、確率が 10% 以上のアソシエーションを対象とします。</span><span class="sxs-lookup"><span data-stu-id="e769a-107">You will consider any association with a probability of at least 10 percent.</span></span>  
  
 <span data-ttu-id="e769a-108">サポートと確率の増減による影響の詳細については、「 [Microsoft アソシエーションアルゴリズムテクニカルリファレンス](../../2014/analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e769a-108">For more information about the effects of increasing or decreasing support and probability, see [Microsoft Association Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="e769a-109">**アソシエーション**マイニングモデルの構造とパラメーターを定義した後は、モデルを処理します。</span><span class="sxs-lookup"><span data-stu-id="e769a-109">After you have defined the structure and parameters for the **Association** mining model, you will process the model.</span></span>  
  
### <a name="to-adjust-the-parameters-of-the-association-model"></a><span data-ttu-id="e769a-110">Association モデルのパラメーターを調整するには</span><span class="sxs-lookup"><span data-stu-id="e769a-110">To adjust the parameters of the Association model</span></span>  
  
1.  <span data-ttu-id="e769a-111">データマイニングデザイナーの [**マイニングモデル**] タブを開きます。</span><span class="sxs-lookup"><span data-stu-id="e769a-111">Open the **Mining Models** tab of Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="e769a-112">デザイナーのグリッドで [ **Association** ] 列を右クリックし、[**アルゴリズムパラメーターの設定**] をクリックして [アルゴリズムパラメーター] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="e769a-112">Right-click the **Association** column in the grid in the designer and select **Set Algorithm Parameters to open the Algorithm Parameters** dialog box.</span></span>  
  
3.  <span data-ttu-id="e769a-113">[**アルゴリズムパラメーター** ] ダイアログボックスの [**値**] 列で、次のパラメーターを設定します。</span><span class="sxs-lookup"><span data-stu-id="e769a-113">In the **Value** column of the **Algorithm Parameters** dialog box, set the following parameters:</span></span>  
  
     <span data-ttu-id="e769a-114">MINIMUM_PROBABILITY = 0.1</span><span class="sxs-lookup"><span data-stu-id="e769a-114">MINIMUM_PROBABILITY = 0.1</span></span>  
  
     <span data-ttu-id="e769a-115">MINIMUM_SUPPORT = 0.01</span><span class="sxs-lookup"><span data-stu-id="e769a-115">MINIMUM_SUPPORT = 0.01</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-process-the-mining-model"></a><span data-ttu-id="e769a-116">マイニング モデルを処理するには</span><span class="sxs-lookup"><span data-stu-id="e769a-116">To process the mining model</span></span>  
  
1.  <span data-ttu-id="e769a-117">の [**マイニングモデル**] メニューで、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] [**マイニング構造とすべてのモデルの処理**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e769a-117">On the **Mining Model** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], select **Process Mining Structure and All Models.**</span></span>  
  
2.  <span data-ttu-id="e769a-118">プロジェクトをビルドして配置するかどうかを確認する警告が表示されたら、[**はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e769a-118">At the warning asking whether you want to build and deploy the project, click **Yes**.</span></span>  
  
     <span data-ttu-id="e769a-119">[**マイニング構造の処理-アソシエーション**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e769a-119">The **Process Mining Structure - Association** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="e769a-120">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e769a-120">Click **Run**.</span></span>  
  
     <span data-ttu-id="e769a-121">[**処理の進行状況**] ダイアログボックスが開き、モデルの処理に関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e769a-121">The **Process Progress** dialog box opens to display information about model processing.</span></span> <span data-ttu-id="e769a-122">新しい構造とモデルの処理には、時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="e769a-122">Processing of the new structure and model might take some time.</span></span>  
  
4.  <span data-ttu-id="e769a-123">処理が完了したら、[**閉じる**] をクリックして [**処理の進行状況**] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e769a-123">After processing is complete, click **Close** to exit the **Process Progress** dialog box.</span></span>  
  
5.  <span data-ttu-id="e769a-124">もう一度 [**閉じる**] をクリックして [**マイニング構造の処理-アソシエーション**] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e769a-124">Click **Close** again to exit the **Process Mining Structure - Association** dialog box.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="e769a-125">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="e769a-125">Next Task in Lesson</span></span>  
 [<span data-ttu-id="e769a-126">&#40;中級者向けデータマイニングチュートリアルに関するマーケットバスケットモデルの調査&#41;</span><span class="sxs-lookup"><span data-stu-id="e769a-126">Exploring the Market Basket Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-market-basket-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="e769a-127">参照</span><span class="sxs-lookup"><span data-stu-id="e769a-127">See Also</span></span>  
 [<span data-ttu-id="e769a-128">処理の要件および注意事項 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="e769a-128">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
