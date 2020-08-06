---
title: マイニングモデルのドリルスルーを有効にする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- drillthrough [Analysis Services]
ms.assetid: 4fa44f60-ef9a-4b59-98c0-c0baf1195c8e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0a6adfc389776f91132e527130f50f61c9783d9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632175"
---
# <a name="enable-drillthrough-for-a-mining-model"></a><span data-ttu-id="ed52a-102">マイニング モデルのドリルスルーの有効化</span><span class="sxs-lookup"><span data-stu-id="ed52a-102">Enable Drillthrough for a Mining Model</span></span>
  <span data-ttu-id="ed52a-103">マイニング モデルのドリルスルーを有効にした場合は、モデルの参照時に、モデルの作成に使用されたケースに関する詳細情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="ed52a-103">If you have enabled drillthrough for a mining model, when you browse the model you can retrieve detailed information about the cases that were used to create the model.</span></span> <span data-ttu-id="ed52a-104">この情報を表示するには、必要な権限があり、構造が既に処理されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed52a-104">To view this information, you must have the necessary permissions, and the structure must have already been processed.</span></span>  
  
 <span data-ttu-id="ed52a-105">**権限** モデル データや構造データのドリルスルーを行うユーザーは、マイニング モデルまたはマイニング構造に対する [AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl) 権限を持つロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed52a-105">**Permissions** For a user to drill through to either model data or structure data, the user must be a member of a role that has [AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl) permissions on the mining model or mining structure.</span></span> <span data-ttu-id="ed52a-106">ドリルスルー権限は、構造およびモデルで個別に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ed52a-106">Drillthrough permissions are set separately on the structure and model.</span></span>  
  
-   <span data-ttu-id="ed52a-107">モデルのドリルスルー権限があれば、構造で権限が与えられていない場合でも、モデルからドリルスルーを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ed52a-107">Drillthrough permissions on the model enable you to drill through from the model, even if you do not have permissions on the structure.</span></span>  
  
-   <span data-ttu-id="ed52a-108">構造のドリルスルー権限がある場合は、[StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) 関数を使用して、構造列をモデルからドリルスルー クエリに含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="ed52a-108">Drillthrough permissions on the structure provide the additional ability to include structure columns in drillthrough queries from the model, by using the [StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) function.</span></span> <span data-ttu-id="ed52a-109">また、[選択...] を使用して、構造内のトレーニングケースとテストケースに対してクエリを実行することもできます。から \<structure> 。CASE 構文。</span><span class="sxs-lookup"><span data-stu-id="ed52a-109">You can also query the training and test cases in the structure by using the SELECT... FROM \<structure>.CASES syntax.</span></span>  
  
 <span data-ttu-id="ed52a-110">**トレーニング ケースのキャッシュ** マイニング構造内のトレーニング ケースに関する情報が取得されることで、ドリルスルーが機能します。</span><span class="sxs-lookup"><span data-stu-id="ed52a-110">**Caching of training cases** Drillthrough works by retrieving information about the training cases in the mining structure.</span></span> <span data-ttu-id="ed52a-111">この情報は、構造が処理されるときにキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="ed52a-111">This information is cached when the structure is processed.</span></span> <span data-ttu-id="ed52a-112">そのため、<xref:Microsoft.AnalysisServices.MiningStructureCacheMode> プロパティを `ClearAfterProcessing` に変更して、キャッシュされたデータをすべて消去した場合、ドリルスルーは機能しません。</span><span class="sxs-lookup"><span data-stu-id="ed52a-112">Therefore, if you choose to clear all cached data by changing the <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> property to `ClearAfterProcessing`, drillthrough will not work.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ed52a-113">トレーニング ケースがキャッシュされていない場合、ケース データを表示するには、 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> プロパティを **KeepTrainingCases** に変更してからモデルを再処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed52a-113">If the training cases have not been cached, you must change the <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> property to **KeepTrainingCases** and then reprocess the model before you can view the case data.</span></span>  
  
 <span data-ttu-id="ed52a-114">詳細については、「 [ドリルスルー クエリ (データ マイニング)](drillthrough-queries-data-mining.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ed52a-114">For more information, see [Drillthrough Queries &#40;Data Mining&#41;](drillthrough-queries-data-mining.md).</span></span>  
  
### <a name="to-enable-drillthrough-on-a-mining-model"></a><span data-ttu-id="ed52a-115">マイニング モデルのドリルスルーを有効にするには</span><span class="sxs-lookup"><span data-stu-id="ed52a-115">To enable drillthrough on a mining model</span></span>  
  
1.  <span data-ttu-id="ed52a-116">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のデータ マイニング デザイナーの **[マイニング モデル]** タブで、ドリルスルーを有効にするマイニング モデルの名前を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ed52a-116">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], on the **Mining Models** tab of Data Mining Designer, right-click the name of the mining model on which you want to enable drillthrough, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="ed52a-117">[**プロパティ**] ウィンドウで、[ **allowdrillthrough スルー**] をクリックし、[ **True**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ed52a-117">In the **Properties** windows, click **AllowDrillthrough**, and select **True**.</span></span>  
  
3.  <span data-ttu-id="ed52a-118">**[マイニング モデル]** タブでモデルを右クリックし、 **[モデルの処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ed52a-118">In the **Mining Models** tab, right-click the model, and select **Process Model**.</span></span>  
  
### <a name="to-enable-caching-for-a-mining-structure"></a><span data-ttu-id="ed52a-119">マイニング構造のキャッシュを有効にするには</span><span class="sxs-lookup"><span data-stu-id="ed52a-119">To enable caching for a mining structure</span></span>  
  
1.  <span data-ttu-id="ed52a-120">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のデータ マイニング デザイナーの **[マイニング構造]** タブで、マイニング構造の名前を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="ed52a-120">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], on the **Mining Structure** tab of Data Mining Designer, right-click the name of the mining structure.</span></span>  
  
2.  <span data-ttu-id="ed52a-121">**[プロパティ]** ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="ed52a-121">Open the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="ed52a-122">**[プロパティ]** ウィンドウで、 **[CacheMode]** プロパティを探し、一覧から **[KeepTrainingCases]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ed52a-122">In the **Properties** window, locate the **CacheMode** property, and select **KeepTrainingCases** from the list.</span></span>  
  
4.  <span data-ttu-id="ed52a-123">**[データベース]** メニューの **[処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ed52a-123">On the **Database** menu, select **Process**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed52a-124">参照</span><span class="sxs-lookup"><span data-stu-id="ed52a-124">See Also</span></span>  
 [<span data-ttu-id="ed52a-125">ドリルスルー クエリ (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="ed52a-125">Drillthrough Queries &#40;Data Mining&#41;</span></span>](drillthrough-queries-data-mining.md)  
  
  
