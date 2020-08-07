---
title: マイニングモデルの処理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], processing
ms.assetid: c2204472-c500-47a5-9afa-7ce2ca78b233
author: minewiskan
ms.author: owend
ms.openlocfilehash: c2fed5d72c677dc175f4c9681096d1859b30d829
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718950"
---
# <a name="process-a-mining-model"></a><span data-ttu-id="d7e0d-102">マイニング モデルの処理</span><span class="sxs-lookup"><span data-stu-id="d7e0d-102">Process a Mining Model</span></span>
  <span data-ttu-id="d7e0d-103">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のデータ マイニング デザイナーにある [マイニング モデル] タブを使用すると、特定のマイニング モデル構造に関連するマイニング モデルを処理したり、その構造に関連するすべてのモデルを処理したりできます。</span><span class="sxs-lookup"><span data-stu-id="d7e0d-103">In the Mining Models tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you can either process a specific mining model that is associated with a mining structure or you can process all the models that are associated with the structure.</span></span>  
  
 <span data-ttu-id="d7e0d-104">マイニング モデルは、次のツールを使用して処理できます。</span><span class="sxs-lookup"><span data-stu-id="d7e0d-104">You can process a mining model by using the following tools:</span></span>  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
 <span data-ttu-id="d7e0d-105">XMLA 処理コマンドを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d7e0d-105">You can also use an XMLA Process command.</span></span> <span data-ttu-id="d7e0d-106">詳細については、「 [&#40;Analysis Services&#41;を処理するためのツールと方法](../multidimensional-models/tools-and-approaches-for-processing-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7e0d-106">For more information, see  [Tools and Approaches for Processing &#40;Analysis Services&#41;](../multidimensional-models/tools-and-approaches-for-processing-analysis-services.md).</span></span>  
  
### <a name="process-a-single-mining-model-using-sql-server-data-tools"></a><span data-ttu-id="d7e0d-107">SQL Server データ ツールを使用した単一のマイニング モデルの処理</span><span class="sxs-lookup"><span data-stu-id="d7e0d-107">Process a single mining model using SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="d7e0d-108">データ マイニング デザイナーの **[マイニング モデル]** タブで、グリッドにある 1 つまたは複数のモデル列からマイニング モデルを 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="d7e0d-108">On the **Mining Models** tab of Data Mining Designer, select a mining model from the one or more columns of models in the grid.</span></span>  
  
2.  <span data-ttu-id="d7e0d-109">**[マイニング モデル]** メニューの **[モデルの処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7e0d-109">On the **Mining Model** menu, select **Process Model**.</span></span>  
  
     <span data-ttu-id="d7e0d-110">マイニング構造に変更を加えた場合は、モデルを処理する前に構造を再配置するように求められます。</span><span class="sxs-lookup"><span data-stu-id="d7e0d-110">If you made changes to the mining structure, you will be prompted to redeploy the structure before processing the model.</span></span> <span data-ttu-id="d7e0d-111">**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7e0d-111">Click **Yes**.</span></span>  
  
3.  <span data-ttu-id="d7e0d-112">[**マイニングモデルの処理- \<model> \*\* ] ダイアログボックスで、[**実行\*\*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7e0d-112">In the **Processing Mining Model - \<model>** dialog box, click **Run**.</span></span>  
  
     <span data-ttu-id="d7e0d-113">**[処理の進行状況]** ダイアログ ボックスが開き、モデル処理の詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d7e0d-113">The **Process Progress** dialog box opens to show the details of model processing.</span></span>  
  
4.  <span data-ttu-id="d7e0d-114">モデルの処理が問題なく終了したら、 **[処理の進行状況]** ダイアログ ボックスで **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7e0d-114">After the model has successfully completed processing, click **Close** in the **Process Progress** dialog box.</span></span>  
  
5.  <span data-ttu-id="d7e0d-115">[**マイニングモデルの処理- \<model> \*\* ] ダイアログボックスで [**閉じる\*\*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7e0d-115">Click **Close** in the **Processing Mining Model - \<model>** dialog box.</span></span>  
  
 <span data-ttu-id="d7e0d-116">そのマイニング構造と選択したマイニング モデルのみが処理されます。</span><span class="sxs-lookup"><span data-stu-id="d7e0d-116">Only the mining structure and the selected mining model have been processed.</span></span>  
  
### <a name="process-all-mining-models-that-are-associated-with-a-mining-structure"></a><span data-ttu-id="d7e0d-117">マイニング構造に関連するすべてのマイニング モデルの処理</span><span class="sxs-lookup"><span data-stu-id="d7e0d-117">Process all mining models that are associated with a mining structure</span></span>  
  
1.  <span data-ttu-id="d7e0d-118">データ マイニング デザイナーの **[マイニング モデル]** タブにある **[マイニング モデル]** メニューで **[マイニング構造および全モデルの処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7e0d-118">On the **Mining Models** tab of Data Mining Designer, select **Process Mining Structure and All Models** from the **Mining Model** menu.</span></span>  
  
2.  <span data-ttu-id="d7e0d-119">マイニング構造に変更を加えた場合は、モデルを処理する前に構造を再配置するように求められます。</span><span class="sxs-lookup"><span data-stu-id="d7e0d-119">If you made changes to the mining structure, you will be prompted to redeploy the structure before processing the models.</span></span> <span data-ttu-id="d7e0d-120">**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7e0d-120">Click **Yes**.</span></span>  
  
3.  <span data-ttu-id="d7e0d-121">[**マイニング構造の処理- \<structure> \*\* ] ダイアログボックスで、[**実行\*\*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7e0d-121">In the **Processing Mining Structure - \<structure>** dialog box, click **Run**.</span></span>  
  
4.  <span data-ttu-id="d7e0d-122">**[処理の進行状況]** ダイアログ ボックスが開き、モデル処理の詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d7e0d-122">The **Process Progress** dialog box opens to show the details of model processing.</span></span>  
  
5.  <span data-ttu-id="d7e0d-123">モデルの処理が問題なく終了したら、 **[処理の進行状況]** ダイアログ ボックスで **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7e0d-123">After the models have successfully completed processing, click **Close** in the **Process Progress** dialog box.</span></span>  
  
6.  <span data-ttu-id="d7e0d-124">[**処理 \<model> **中] ダイアログボックスで [**閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7e0d-124">Click **Close** in the **Processing \<model>** dialog box.</span></span>  
  
 <span data-ttu-id="d7e0d-125">マイニング構造および関連するすべてのマイニング モデルが処理されます。</span><span class="sxs-lookup"><span data-stu-id="d7e0d-125">The mining structure and all the associated mining models have been processed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7e0d-126">参照</span><span class="sxs-lookup"><span data-stu-id="d7e0d-126">See Also</span></span>  
 [<span data-ttu-id="d7e0d-127">マイニング モデル タスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="d7e0d-127">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
