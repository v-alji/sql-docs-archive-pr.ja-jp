---
title: 構造データでのドリルスルーの使用 (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a693979c-0564-4d6d-b35d-cbbc8f350469
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 49a1ced27150676def541548f47a90a3f847c8ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631378"
---
# <a name="using-drillthrough-on-structure-data-basic-data-mining-tutorial"></a><span data-ttu-id="ae4f5-102">構造データでのドリルスルーの使用 (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="ae4f5-102">Using Drillthrough on Structure Data (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="ae4f5-103">広告キャンペーンの一環として、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] は34-40 時代 (人口統計) の潜在顧客に郵便を送信します。</span><span class="sxs-lookup"><span data-stu-id="ae4f5-103">As part of their advertising campaign, [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] is sending a mailer to potential customers in the 34-40 age demographic.</span></span> <span data-ttu-id="ae4f5-104">マーケティング部門では、5 年以上前に [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] から自転車を購入した顧客にも宣伝リーフレットを送付することにしました。</span><span class="sxs-lookup"><span data-stu-id="ae4f5-104">The marketing department has decided that they would also like to send the mailer to the customers who purchased bikes from [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] more than five years ago.</span></span> <span data-ttu-id="ae4f5-105">このレッスンでは、古い型の自転車を購入した顧客を特定し、その連絡先情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="ae4f5-105">In this lesson you will identify customers with older bikes and retrieve their contact information.</span></span> <span data-ttu-id="ae4f5-106">この情報は、モデルではなく構造に含まれています。</span><span class="sxs-lookup"><span data-stu-id="ae4f5-106">This information is not included in the model, but is included in the structure.</span></span> <span data-ttu-id="ae4f5-107">連絡先情報を取得するには、まず構造に対してドリルスルーを有効にし、ドリルスルーを使用して対象とする顧客の名前と住所を明らかにします。</span><span class="sxs-lookup"><span data-stu-id="ae4f5-107">To retrieve the contact information you will first ensure that drillthrough is enabled for the structure and then you will use drillthrough to reveal the names and addresses of the targeted customers.</span></span>  
  
### <a name="to-enable-drillthrough-on-a-mining-model"></a><span data-ttu-id="ae4f5-108">マイニング モデルのドリルスルーを有効にするには</span><span class="sxs-lookup"><span data-stu-id="ae4f5-108">To enable drillthrough on a mining model</span></span>  
  
1.  <span data-ttu-id="ae4f5-109">の [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] データマイニングデザイナーの [**マイニングモデル**] タブで、 **TM_Decision_Tree**モデルを右クリックし、[**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ae4f5-109">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Mining Models** tab of Data Mining Designer, right-click the **TM_Decision_Tree** model, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="ae4f5-110">[プロパティ] ウィンドウで **[AllowDrillthrough]** をクリックし、 **[True]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ae4f5-110">In the Properties windows, click **AllowDrillthrough**, and select **True**.</span></span>  
  
3.  <span data-ttu-id="ae4f5-111">[マイニング モデル] タブでモデルを右クリックし、 **[モデルの処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae4f5-111">In the Mining Models tab, right-click the model, and select **Process Model**.</span></span>  
  
 <span data-ttu-id="ae4f5-112">詳細については、「[データマイニング &#40;のドリルスルークエリ](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)」を参照してください&#41;</span><span class="sxs-lookup"><span data-stu-id="ae4f5-112">For more information, see [Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)</span></span>  
  
### <a name="to-view-drillthrough-data-from-a-mining-model"></a><span data-ttu-id="ae4f5-113">マイニング モデルからのドリルスルー データを表示するには</span><span class="sxs-lookup"><span data-stu-id="ae4f5-113">To view drillthrough data from a mining model</span></span>  
  
1.  <span data-ttu-id="ae4f5-114">データ マイニング デザイナーで、 **[マイニング モデル ビューアー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae4f5-114">In Data Mining Designer, click the **Mining Model Viewer** tab.</span></span>  
  
2.  <span data-ttu-id="ae4f5-115">[**マイニングモデル**] ボックスの一覧から**TM_Decision_Tree**モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="ae4f5-115">Select the **TM_Decision_Tree** model from the **Mining Model** list.</span></span>  
  
3.  <span data-ttu-id="ae4f5-116">[**背景**値をに変更 `1` します。</span><span class="sxs-lookup"><span data-stu-id="ae4f5-116">Change the **Background** value to `1`.</span></span> <span data-ttu-id="ae4f5-117">これにより、自転車を購入した顧客に関するモデルの部分のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ae4f5-117">By doing this, you show only the part of the model that is related to customer who bought bikes.</span></span>  
  
4.  <span data-ttu-id="ae4f5-118">**[ビューアー]** ボックスの一覧の [Microsoft ツリー ビューアー] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae4f5-118">Select the Microsoft Tree viewer from the **Viewer** list.</span></span> <span data-ttu-id="ae4f5-119">これにより、ビューアーが強制的に新しいフィルター条件で更新されます。</span><span class="sxs-lookup"><span data-stu-id="ae4f5-119">This will force the viewer to refresh with the new filter conditions.</span></span> <span data-ttu-id="ae4f5-120">次に、 **Age >= 34 および <41**ノードを見つけ、ノードを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="ae4f5-120">Then, locate the **Age >=34 and <41** node and right-click the node.</span></span>  
  
5.  <span data-ttu-id="ae4f5-121">**[ドリルスルー]** をクリックし、 **[モデルおよび構造列]** をクリックして **[ドリルスルー]** ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="ae4f5-121">Select **Drill Through**, and then select **Model and Structure Columns** to open the **Drill Through** window.</span></span>  
  
6.  <span data-ttu-id="ae4f5-122">**[Structure.Date First Purchase]** 列までスクロールして、古い型の自転車の購入日を表示します。</span><span class="sxs-lookup"><span data-stu-id="ae4f5-122">Scroll to the **Structure.Date First Purchase** column to view the purchase dates for the older bikes.</span></span>  
  
7.  <span data-ttu-id="ae4f5-123">データをクリップボードにコピーするには、テーブル内の任意の行を右クリックして **[すべてコピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae4f5-123">To copy the data to the Clipboard, right-click any row in the table, and select **Copy All**.</span></span>  
  
 <span data-ttu-id="ae4f5-124">これで、「基本的なデータ マイニング チュートリアル」は終了です。</span><span class="sxs-lookup"><span data-stu-id="ae4f5-124">Congratulations, you have completed the basic data mining tutorial.</span></span> <span data-ttu-id="ae4f5-125">データ マイニング ツールの操作に慣れたら、「中級者向けデータ マイニング チュートリアル」も実行することをお勧めします。「中級者向けデータ マイニング チュートリアル」では、予測、マーケット バスケット分析、シーケンス クラスターの各モデルを作成する方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="ae4f5-125">Now that you are comfortable using the data mining tools, we recommend that you also complete the intermediate data mining tutorial, which demonstrates how to create models for forecasting, market basket analysis, and sequence clustering.</span></span>  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="ae4f5-126">このレッスンの前の作業</span><span class="sxs-lookup"><span data-stu-id="ae4f5-126">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="ae4f5-127">予測の作成 &#40;基本的なデータ マイニング チュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="ae4f5-127">Creating Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="ae4f5-128">参照</span><span class="sxs-lookup"><span data-stu-id="ae4f5-128">See Also</span></span>  
 [<span data-ttu-id="ae4f5-129">予測クエリ ビルダーを使用した予測クエリの作成</span><span class="sxs-lookup"><span data-stu-id="ae4f5-129">Create a Prediction Query Using the Prediction Query Builder</span></span>](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
