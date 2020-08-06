---
title: シーケンスクラスターモデルの処理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4a7545fd-37a3-4766-ad59-0946f1bd3524
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9975105fb6779e150e3a498bc87654d21292a1b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720462"
---
# <a name="processing-the-sequence-clustering-model"></a><span data-ttu-id="38e9e-102">シーケンス クラスター モデルの処理</span><span class="sxs-lookup"><span data-stu-id="38e9e-102">Processing the Sequence Clustering Model</span></span>
  <span data-ttu-id="38e9e-103">新しいマイニング構造を作成したら、データ マイニング ソリューションに加えた変更を配置し、構造を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38e9e-103">After you create a new mining structure, you must deploy the changes that you made to the data mining solution, and then process the structure.</span></span> <span data-ttu-id="38e9e-104">新しい構造およびマイニング モデルの両方の処理が完了すると、マイニング モデルを参照できるようになります。</span><span class="sxs-lookup"><span data-stu-id="38e9e-104">After processing of both the new structure and the mining model is complete, you can browse the mining model.</span></span>  
  
 <span data-ttu-id="38e9e-105">新しいデータ マイニング構造を作成する際には、必ず処理が必要になります。</span><span class="sxs-lookup"><span data-stu-id="38e9e-105">Processing is always required when you create a new data mining structure.</span></span> <span data-ttu-id="38e9e-106">ただし、既存の構造に新しいマイニング モデルを追加する場合は、マイニング モデルのみを処理するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="38e9e-106">However, if you add a new mining model to an existing structure, you can process just the mining model.</span></span> <span data-ttu-id="38e9e-107">このシナリオでは、新しいマイニング構造とマイニング モデルを作成したので、構造とモデルの両方を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38e9e-107">In this scenario, because you have created a new mining structure and a new mining model, you must process both.</span></span>  
  
### <a name="to-process-the-mining-structure-and-model"></a><span data-ttu-id="38e9e-108">マイニング構造およびマイニング モデルを処理するには</span><span class="sxs-lookup"><span data-stu-id="38e9e-108">To process the mining structure and model</span></span>  
  
1.  <span data-ttu-id="38e9e-109">の [**マイニングモデル**] メニューで、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] [**マイニング構造とすべてのモデルの処理**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="38e9e-109">On the **Mining Model** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], select **Process Mining Structure and All Models**.</span></span>  
  
2.  <span data-ttu-id="38e9e-110">プロジェクトをビルドして配置するかどうかを確認する警告が表示されたら、[**はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38e9e-110">At the warning asking whether you want to build and deploy the project, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="38e9e-111">[**マイニング構造の処理-[リージョンを含むシーケンスクラスター** ] ダイアログボックスで、[**実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38e9e-111">In the **Process Mining Structure - Sequence Clustering with Region** dialog box, click **Run**.</span></span>  
  
     <span data-ttu-id="38e9e-112">[**処理の進行状況**] ダイアログボックスが開き、モデルの処理に関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="38e9e-112">The **Process Progress** dialog box opens to display information about model processing.</span></span> <span data-ttu-id="38e9e-113">新しい構造とモデルの処理には、時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="38e9e-113">Processing of the new structure and model might take some time.</span></span>  
  
4.  <span data-ttu-id="38e9e-114">処理が完了したら、[**閉じる**] をクリックして [**処理の進行状況**] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="38e9e-114">After processing is complete, click **Close** to exit the **Process Progress** dialog box.</span></span>  
  
5.  <span data-ttu-id="38e9e-115">もう一度 [**閉じる**] をクリックして、[**マイニング構造の処理-リージョンを含むシーケンスクラスター** ] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="38e9e-115">Click **Close** again to exit the **Process Mining Structure - Sequence Clustering with Region** dialog box.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="38e9e-116">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="38e9e-116">Next Task in Lesson</span></span>  
 [<span data-ttu-id="38e9e-117">シーケンスクラスターモデル &#40;中級者向けデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="38e9e-117">Exploring the Sequence Clustering Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="38e9e-118">参照</span><span class="sxs-lookup"><span data-stu-id="38e9e-118">See Also</span></span>  
 <span data-ttu-id="38e9e-119">[データマイニングデザイナー](../../2014/analysis-services/data-mining/data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="38e9e-119">[Data Mining Designer](../../2014/analysis-services/data-mining/data-mining-designer.md) </span></span>  
 <span data-ttu-id="38e9e-120">[Microsoft シーケンスクラスターアルゴリズム](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="38e9e-120">[Microsoft Sequence Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md) </span></span>  
 [<span data-ttu-id="38e9e-121">処理の要件および注意事項 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="38e9e-121">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
