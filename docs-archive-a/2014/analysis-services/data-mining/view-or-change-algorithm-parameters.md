---
title: アルゴリズムパラメーターを表示または変更する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- algorithms [data mining]
- mining models [Analysis Services], algorithms
ms.assetid: 151b899b-c27a-4a09-bcf5-5c9f0ec24168
author: minewiskan
ms.author: owend
ms.openlocfilehash: 30719cd50e0c473cf2aab5d9689d27dff4f26343
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639782"
---
# <a name="view-or-change-algorithm-parameters"></a><span data-ttu-id="3040f-102">アルゴリズム パラメーターの表示または変更</span><span class="sxs-lookup"><span data-stu-id="3040f-102">View or Change Algorithm Parameters</span></span>
  <span data-ttu-id="3040f-103">データ マイニング モデルをビルドするためのアルゴリズムで提供されているパラメーターを変更して、モデルの結果をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="3040f-103">You can change the parameters provided with the algorithms that you use to build data mining models to customize the results of the model.</span></span>  
  
 <span data-ttu-id="3040f-104">に用意されているアルゴリズムパラメーターは、モデルのプロパティだけでなく、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データの処理方法、グループ化方法、および表示方法を根本的に変更するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="3040f-104">The algorithm parameters provided in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] change much more than just properties on the model: they can be used to fundamentally alter the way that data is processed, grouped, and displayed.</span></span> <span data-ttu-id="3040f-105">たとえば、アルゴリズム パラメーターを使用すると、次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="3040f-105">For example, you can use algorithm parameters to do the following:</span></span>  
  
-   <span data-ttu-id="3040f-106">分析方法 (クラスタリング方法など) を変更する。</span><span class="sxs-lookup"><span data-stu-id="3040f-106">Change the method of analysis, such as the clustering method.</span></span>  
  
-   <span data-ttu-id="3040f-107">機能の選択動作を制御する。</span><span class="sxs-lookup"><span data-stu-id="3040f-107">Control feature selection behavior.</span></span>  
  
-   <span data-ttu-id="3040f-108">アイテムセットのサイズまたはルールの確率を指定する。</span><span class="sxs-lookup"><span data-stu-id="3040f-108">Specify the size of itemsets or the probability of rules.</span></span>  
  
-   <span data-ttu-id="3040f-109">デシジョン ツリーの分岐と深さを制御する。</span><span class="sxs-lookup"><span data-stu-id="3040f-109">Control branching and depth of decision trees.</span></span>  
  
-   <span data-ttu-id="3040f-110">シード値またはモデルの作成に使用される内部の提示されるセットのサイズを指定する。</span><span class="sxs-lookup"><span data-stu-id="3040f-110">Specify a seed value or the size of the internal holdout set used for model creation.</span></span>  
  
 <span data-ttu-id="3040f-111">それぞれのアルゴリズムで提供されるパラメーターは大きく異なります。各アルゴリズムに対して設定できるパラメーターの一覧については、「[データ マイニング アルゴリズム (Analysis Services - データ マイニング)](data-mining-algorithms-analysis-services-data-mining.md)」のテクニカル リファレンス トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3040f-111">The parameters provided for each algorithm vary greatly; for a list of the parameters that you can set for each algorithm, see the technical reference topics in this section: [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
### <a name="change-an-algorithm-parameter"></a><span data-ttu-id="3040f-112">アルゴリズム パラメーターを変更する</span><span class="sxs-lookup"><span data-stu-id="3040f-112">Change an algorithm parameter</span></span>  
  
1.  <span data-ttu-id="3040f-113">**のデータ マイニング デザイナーの** [マイニング モデル] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブで、アルゴリズムを調整するマイニング モデルのアルゴリズムの種類を右クリックし、 **[アルゴリズム パラメーターの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3040f-113">On the **Mining Models** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], right-click the algorithm type of the mining model for which you want to tune the algorithm, and select **Set Algorithm Parameters**.</span></span>  
  
     <span data-ttu-id="3040f-114">**[アルゴリズム パラメーター]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="3040f-114">The **Algorithm Parameters** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="3040f-115">**[値]** 列で、変更するアルゴリズムの新しい値を設定します。</span><span class="sxs-lookup"><span data-stu-id="3040f-115">In the **Value** column, set a new value for the algorithm that you want to change.</span></span>  
  
     <span data-ttu-id="3040f-116">**[値]** 列に値を入力しない場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではパラメーターの既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3040f-116">If you do not enter a value in the **Value** column, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses the default parameter value.</span></span> <span data-ttu-id="3040f-117">**[範囲]** 列には、入力可能な値が示されます。</span><span class="sxs-lookup"><span data-stu-id="3040f-117">The **Range** column describes the possible values that you can enter.</span></span>  
  
3.  <span data-ttu-id="3040f-118">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3040f-118">Click **OK**.</span></span>  
  
     <span data-ttu-id="3040f-119">アルゴリズム パラメーターが新しい値で設定されます。</span><span class="sxs-lookup"><span data-stu-id="3040f-119">The algorithm parameter is set with the new value.</span></span> <span data-ttu-id="3040f-120">パラメーターの変更は、マイニング モデルを再処理するまではマイニング モデルに反映されません。</span><span class="sxs-lookup"><span data-stu-id="3040f-120">The parameter change will not be reflected in the mining model until you reprocess the model.</span></span>  
  
### <a name="view-the-parameters-used-in-an-existing-model"></a><span data-ttu-id="3040f-121">既存のモデルで使用されているパラメーターを表示する</span><span class="sxs-lookup"><span data-stu-id="3040f-121">View the parameters used in an existing model</span></span>  
  
1.  <span data-ttu-id="3040f-122">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、DMX クエリ ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="3040f-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open a DMX Query window.</span></span>  
  
2.  <span data-ttu-id="3040f-123">次のようなクエリを入力します。</span><span class="sxs-lookup"><span data-stu-id="3040f-123">Type a query like this one:</span></span>  
  
    ```  
    select MINING_PARAMETERS   
    from $system.DMSCHEMA_MINING_MODELS  
    WHERE MODEL_NAME = '<model name>'  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3040f-124">参照</span><span class="sxs-lookup"><span data-stu-id="3040f-124">See Also</span></span>  
 [<span data-ttu-id="3040f-125">マイニング モデル タスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="3040f-125">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
