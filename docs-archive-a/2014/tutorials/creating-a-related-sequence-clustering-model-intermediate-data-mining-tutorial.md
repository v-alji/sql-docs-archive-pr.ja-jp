---
title: 関連するシーケンスクラスターモデルの作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1fb4f5bc-1756-45ca-9cd7-411a8c5992a9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d015ed8a9887cb6164020806bf4136f58629ad11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719137"
---
# <a name="creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="a30ca-102">関連するシーケンス クラスター モデルの作成 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="a30ca-102">Creating a Related Sequence Clustering Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="a30ca-103">シーケンス クラスター モデルの検証により、Region や Income などの他の属性がモデルに大きな影響を与えていることがわかりました。そのため、シーケンスについての理解を深めるために、関連するシーケンス クラスター モデルを作成し、顧客の人口統計に関連する属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="a30ca-103">Through your exploration of the sequence clustering model, you learned that other attributes such as Region or Income have a strong effect on the models; therefore, to understand the sequences better, you will create a related sequence clustering model and remove the attributes related to customer demographics.</span></span>  
  
 <span data-ttu-id="a30ca-104">この作業では、地域別のシーケンス クラスター モデルのコピーを作成し、そのモデルからシーケンスに直接関連しない列を削除します。</span><span class="sxs-lookup"><span data-stu-id="a30ca-104">In this task, you will create a copy of the regional sequence clustering model, and then remove from the model any columns that are not directly related to the sequences.</span></span>  
  
 <span data-ttu-id="a30ca-105">新しいモデルには基になるマイニング モデルと同じすべての列が含まれますが、</span><span class="sxs-lookup"><span data-stu-id="a30ca-105">The new model will contain all the same columns as the mining model on which it is based.</span></span> <span data-ttu-id="a30ca-106">マイニング構造から列を削除する必要はありません。新しいマイニング モデルで列を無視するように指定するだけです。</span><span class="sxs-lookup"><span data-stu-id="a30ca-106">However, you do not need to remove the columns from the mining structure, only specify that the new mining model ignore the columns.</span></span>  
  
### <a name="to-make-a-copy-of-the-sequence-clustering-model"></a><span data-ttu-id="a30ca-107">シーケンス クラスター モデルのコピーを作成するには</span><span class="sxs-lookup"><span data-stu-id="a30ca-107">To make a copy of the sequence clustering model</span></span>  
  
1.  <span data-ttu-id="a30ca-108">の [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] データマイニングデザイナーで、[**マイニングモデル**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a30ca-108">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in the Data Mining Designer, click the **Mining Models** tab.</span></span>  
  
2.  <span data-ttu-id="a30ca-109">コピーするモデルを右クリックし、[**新しいマイニングモデル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a30ca-109">Right-click the model you want to copy, and select **New Mining Model**.</span></span>  
  
3.  <span data-ttu-id="a30ca-110">[**新しいマイニングモデル**] ダイアログボックスで、モデル名を入力し、[Microsoft] を選択し `Sequence Clustering` ます。</span><span class="sxs-lookup"><span data-stu-id="a30ca-110">In the **New Mining Model** dialog box, type a model name, and select Microsoft `Sequence Clustering`.</span></span>  
  
     <span data-ttu-id="a30ca-111">このチュートリアルでは、という名前を入力し `Sequence Clustering` ます。</span><span class="sxs-lookup"><span data-stu-id="a30ca-111">For this tutorial, type the name `Sequence Clustering`.</span></span>  
  
4.  <span data-ttu-id="a30ca-112">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a30ca-112">Click **OK**.</span></span>  
  
### <a name="to-remove-columns-from-the-mining-model"></a><span data-ttu-id="a30ca-113">マイニング モデルから列を削除するには</span><span class="sxs-lookup"><span data-stu-id="a30ca-113">To remove columns from the mining model</span></span>  
  
1.  <span data-ttu-id="a30ca-114">[**マイニングモデル**] タブの [シーケンスクラスター] という名前の新しいモデルの列で、[**収入グループ**] 属性の行をクリックし、[**無視**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a30ca-114">In the **Mining Model** tab, in the column for the new model named Sequence Clustering, click the row for the **Income Group** attribute, and select **Ignore**.</span></span>  
  
2.  <span data-ttu-id="a30ca-115">属性**領域**に対してこの手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="a30ca-115">Repeat this step for the attribute **Region**.</span></span>  
  
3.  <span data-ttu-id="a30ca-116">テーブル名の横にあるプラス記号をクリックし**て、テーブル**を展開し、入れ子になったテーブルの列を表示します。</span><span class="sxs-lookup"><span data-stu-id="a30ca-116">Click the plus sign next to the table name, **v Assoc Seq Line Items**, to expand the table and view the columns from the nested table.</span></span>  
  
     <span data-ttu-id="a30ca-117">新しいモデルの列は、次の列だけになります。</span><span class="sxs-lookup"><span data-stu-id="a30ca-117">The new model should have only the following columns:</span></span>  
  
     <span data-ttu-id="a30ca-118">**注文番号キー**</span><span class="sxs-lookup"><span data-stu-id="a30ca-118">**Order NumberKey**</span></span>  
  
     <span data-ttu-id="a30ca-119">**行番号キー**</span><span class="sxs-lookup"><span data-stu-id="a30ca-119">**Line Number Key**</span></span>  
  
     <span data-ttu-id="a30ca-120">**モデル予測**</span><span class="sxs-lookup"><span data-stu-id="a30ca-120">**Model Predict**</span></span>  
  
### <a name="to-process-the-new-sequence-clustering-model"></a><span data-ttu-id="a30ca-121">新しいシーケンス クラスター モデルを処理するには</span><span class="sxs-lookup"><span data-stu-id="a30ca-121">To process the new sequence clustering model</span></span>  
  
1.  <span data-ttu-id="a30ca-122">[**マイニングモデル**] タブで、という名前の新しいモデルを右クリック `Sequence Clustering` し、[モデルの**処理**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a30ca-122">In the **Mining Model** tab, right-click the new model named `Sequence Clustering`, and select **Process Model**.</span></span>  
  
     <span data-ttu-id="a30ca-123">新しいマイニング モデルは処理済みの構造に基づく簡略化されたモデルであるため、構造を再処理する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a30ca-123">Because the new simplified mining model is based on a structure that has already been processed, you do not need to reprocess the structure.</span></span> <span data-ttu-id="a30ca-124">新しいマイニング モデルのみを処理できます。</span><span class="sxs-lookup"><span data-stu-id="a30ca-124">You can process just the new mining model.</span></span>  
  
2.  <span data-ttu-id="a30ca-125">[**はい**] をクリックして、更新されたデータマイニングプロジェクトをサーバーに配置します。</span><span class="sxs-lookup"><span data-stu-id="a30ca-125">Click **Yes** to deploy the updated data mining project to the server.</span></span>  
  
3.  <span data-ttu-id="a30ca-126">[**マイニングモデルの処理**] ダイアログボックスで、[**実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a30ca-126">In the **Process Mining Model** dialog box, click **Run**.</span></span>  
  
4.  <span data-ttu-id="a30ca-127">[**閉じる**] をクリックして [**処理の進行状況**] ダイアログボックスを閉じ、[**マイニングモデルの処理**] ダイアログボックスでもう一度 [**閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a30ca-127">Click **Close** to close the **Process Progress** dialog box, and then click **Close** again in the **Process Mining Model** dialog box.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="a30ca-128">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="a30ca-128">Next Task in Lesson</span></span>  
 [<span data-ttu-id="a30ca-129">シーケンスクラスターモデルでの予測の作成 &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="a30ca-129">Creating Predictions on a Sequence Clustering Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/create-predictions-on-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="a30ca-130">参照</span><span class="sxs-lookup"><span data-stu-id="a30ca-130">See Also</span></span>  
 [<span data-ttu-id="a30ca-131">処理の要件および注意事項 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="a30ca-131">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
