---
title: データソースビューの作成 (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c1e68a88-0f82-415d-becc-78d180d4f845
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 4582845c905ef95601cbff2c810633f0cc901e3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634744"
---
# <a name="creating-a-data-source-view-basic-data-mining-tutorial"></a><span data-ttu-id="81c6c-102">データ ソース ビューの作成 (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="81c6c-102">Creating a Data Source View (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="81c6c-103">データ ソース ビューは、データ ソース上に構築され、データのサブセットを定義します。このデータ ソース ビューを、マイニング構造で使用できます。</span><span class="sxs-lookup"><span data-stu-id="81c6c-103">A data source view is built on a data source and defines a subset of the data, which you can then use in your mining structures.</span></span> <span data-ttu-id="81c6c-104">また、データ ソース ビューを使用して、列の追加、計算列や集計の作成、および名前付きビューの追加を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="81c6c-104">You can also use the data source view to add columns, create calculated columns and aggregates, and add named views.</span></span> <span data-ttu-id="81c6c-105">データ ソース ビューを使用すると、プロジェクトに関連するデータの選択、テーブルどうしの関連付け、データの構造の変更などの操作を、元のデータ ソースを変更せずに実行できます。</span><span class="sxs-lookup"><span data-stu-id="81c6c-105">By using data source views, you can select the data that relates to your project, establish relationships between tables, and modify the structure of the data, without modifying the original data source.</span></span> <span data-ttu-id="81c6c-106">詳細については、 [「多次元モデルのデータ ソース ビュー」](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81c6c-106">For more information, see [Data Source Views in Multidimensional Models](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models).</span></span>  
  
### <a name="to-create-a-data-source-view"></a><span data-ttu-id="81c6c-107">データ ソース ビューを作成するには</span><span class="sxs-lookup"><span data-stu-id="81c6c-107">To create a data source view</span></span>  
  
1.  <span data-ttu-id="81c6c-108">**ソリューション エクスプローラー**で **[データ ソース ビュー]** を右クリックし、 **[新しいデータ ソース ビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81c6c-108">In **Solution Explorer**, right-click **Data Source Views**, and select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="81c6c-109">**[データ ソース ビュー ウィザードへようこそ]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81c6c-109">On the **Welcome to the Data Source View Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="81c6c-110">**[データ ソースの選択]** ページの **[リレーショナル データ ソース]** で、前回の作業で作成した [Adventure Works DW 2012] データ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="81c6c-110">On the **Select a Data Source** page, under **Relational data sources**, select the Adventure Works DW 2012 data source that you created in the last task.</span></span> <span data-ttu-id="81c6c-111">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81c6c-111">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="81c6c-112">新しいデータ ソースを作成する場合は、 **[データ ソース]** を右クリックし、 **[新しいデータ ソース]** をクリックして、データ ソース ウィザードを開始します。</span><span class="sxs-lookup"><span data-stu-id="81c6c-112">If you want to create a data source, right-click **Data Sources** and then click **New Data Source** to start the Data Source Wizard.</span></span>  
  
4.  <span data-ttu-id="81c6c-113">**[テーブルとビューの選択]** ページで次のオブジェクトを選択し、右矢印をクリックして、これらのオブジェクトを新しいデータ ソース ビューに追加します。</span><span class="sxs-lookup"><span data-stu-id="81c6c-113">On the **Select Tables and Views** page, select the following objects, and then click the right arrow to include them in the new data source view:</span></span>  
  
    -   <span data-ttu-id="81c6c-114">**[ProspectiveBuyer (dbo)]** : 自転車の購入見込み者のテーブル</span><span class="sxs-lookup"><span data-stu-id="81c6c-114">**ProspectiveBuyer (dbo)** - table of prospective bike buyers</span></span>  
  
    -   <span data-ttu-id="81c6c-115">**[vTargetMail (dbo)]** : 過去の自転車購入者に関する履歴データのビュー</span><span class="sxs-lookup"><span data-stu-id="81c6c-115">**vTargetMail (dbo)** - view of historical data about past bike buyers</span></span>  
  
5.  <span data-ttu-id="81c6c-116">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81c6c-116">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="81c6c-117">既定では、Adventure Works DW 2012 という名前のデータ ソース ビューが **[ウィザードの完了]** ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="81c6c-117">On the **Completing the Wizard** page, by default the data source view is named Adventure Works DW 2012.</span></span> <span data-ttu-id="81c6c-118">名前をに変更し、 `Targeted Mailing` [**完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81c6c-118">Change the name to `Targeted Mailing`, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="81c6c-119">新しいデータ ソース ビューが **[Targeted Mailing.dsv [Design]]** タブで開きます。</span><span class="sxs-lookup"><span data-stu-id="81c6c-119">The new data source view opens in the **Targeted Mailing.dsv [Design]** tab.</span></span>  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="81c6c-120">このレッスンの前の作業</span><span class="sxs-lookup"><span data-stu-id="81c6c-120">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="81c6c-121">データソースの作成 &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="81c6c-121">Creating a Data Source &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="81c6c-122">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="81c6c-122">Next Lesson</span></span>  
 [<span data-ttu-id="81c6c-123">レッスン 2: &#40;の基本的なデータマイニングチュートリアルでは、絞り込みメール配信構造の作成&#41;</span><span class="sxs-lookup"><span data-stu-id="81c6c-123">Lesson 2: Building a Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="81c6c-124">参照</span><span class="sxs-lookup"><span data-stu-id="81c6c-124">See Also</span></span>  
 [<span data-ttu-id="81c6c-125">データ ソース ビューの定義 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="81c6c-125">Defining a Data Source View &#40;Analysis Services&#41;</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/defining-a-data-source-view-analysis-services)  
  
  
