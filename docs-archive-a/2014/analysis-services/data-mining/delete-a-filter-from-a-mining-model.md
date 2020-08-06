---
title: マイニングモデルからフィルターを削除する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- filters [Analysis Services]
ms.assetid: 91220b21-adbc-49a9-b200-8bf0a724eff1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 404c23c0e55bffba2ce8410c9c30d6ad1fa1991b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632785"
---
# <a name="delete-a-filter-from-a-mining-model"></a><span data-ttu-id="9211e-102">マイニング モデルからのフィルターの削除</span><span class="sxs-lookup"><span data-stu-id="9211e-102">Delete a Filter from a Mining Model</span></span>
  <span data-ttu-id="9211e-103">マイニング モデルに対するフィルターを作成する場合は、データ ソース ビュー内のデータのサブセットに対するモデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="9211e-103">When you create a filter on a mining model, you can create models on a subset of the data in the data source view.</span></span> <span data-ttu-id="9211e-104">フィルターは、元のデータのサブセットでモデルの精度をテストするためにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9211e-104">Filters are also useful for testing the accuracy of the model on a subset of the original data.</span></span>  
  
 <span data-ttu-id="9211e-105">ただし、ケースの完全なセットを再度表示する場合は、フィルターを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9211e-105">However, you must delete the filter if you want to view the complete set of cases again.</span></span> <span data-ttu-id="9211e-106">この手順では、フィルターの条件を削除する方法や、フィルターを完全に削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9211e-106">This procedure describes how to remove conditions on a filter, or delete the filter completely.</span></span>  
  
### <a name="to-delete-a-condition-from-a-filter-on-a-mining-model"></a><span data-ttu-id="9211e-107">マイニング モデルのフィルターから条件を削除するには</span><span class="sxs-lookup"><span data-stu-id="9211e-107">To delete a condition from a filter on a mining model</span></span>  
  
1.  <span data-ttu-id="9211e-108">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーで、フィルターを適用するマイニング モデルが含まれているマイニング構造をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9211e-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Solution Explorer, click the mining structure that contains the mining model you want to filter.</span></span>  
  
2.  <span data-ttu-id="9211e-109">**[マイニング モデル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9211e-109">Click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="9211e-110">モデルを選択し、右クリックしてショートカット メニューを開きます。</span><span class="sxs-lookup"><span data-stu-id="9211e-110">Select the model, and right-click to open the shortcut menu.</span></span>  
  
     <span data-ttu-id="9211e-111">または</span><span class="sxs-lookup"><span data-stu-id="9211e-111">-or-</span></span>  
  
     <span data-ttu-id="9211e-112">モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="9211e-112">Select the model.</span></span> <span data-ttu-id="9211e-113">**[マイニング モデル]** メニューの **[モデル フィルターの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9211e-113">On the **Mining Model** menu, select **Set Model Filter**.</span></span>  
  
4.  <span data-ttu-id="9211e-114">**[モデル フィルター]** ダイアログ ボックスで、削除する条件が含まれているグリッドの行を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="9211e-114">In the **Model Filter** dialog box, right-click the row in the grid that contains the condition you want to delete.</span></span>  
  
5.  <span data-ttu-id="9211e-115">**[削除]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9211e-115">Select **Delete**.</span></span>  
  
### <a name="to-clear-the-filter-on-a-mining-model-in-the-filter-editor-dialog-box"></a><span data-ttu-id="9211e-116">フィルター エディターのダイアログ ボックスからマイニング モデルのフィルターを消去するには</span><span class="sxs-lookup"><span data-stu-id="9211e-116">To clear the filter on a mining model in the Filter Editor dialog box</span></span>  
  
-   <span data-ttu-id="9211e-117">**[フィルター エディター]** ダイアログ ボックスで、グリッドの任意の行を右クリックし、 **[すべて削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9211e-117">In the **Filter Editor** dialog box, right-click any row in the grid, and select **Delete All**.</span></span>  
  
## <a name="working-with-model-filters-using-the-properties-window"></a><span data-ttu-id="9211e-118">[プロパティ] ウィンドウを使用したモデル フィルターの操作</span><span class="sxs-lookup"><span data-stu-id="9211e-118">Working with Model Filters Using the Properties Window</span></span>  
 <span data-ttu-id="9211e-119">フィルター全体を削除する場合、フィルター エディターのダイアログ ボックスを開く必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9211e-119">If you want to delete the whole filter, you do not need to open the filter editor dialog boxes.</span></span> <span data-ttu-id="9211e-120">作成したフィルター条件は、マイニング モデルの `Filter` プロパティで使用できます。</span><span class="sxs-lookup"><span data-stu-id="9211e-120">The filter conditions that you created are available in the `Filter` property of the mining model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9211e-121">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]ではマイニング モデルのプロパティを表示できますが [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ではできません。</span><span class="sxs-lookup"><span data-stu-id="9211e-121">You can view the properties of a mining model in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], but not in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-clear-the-filter-on-a-mining-model-in-solution-explorer"></a><span data-ttu-id="9211e-122">ソリューション エクスプローラーでマイニング モデルのフィルターを消去するには</span><span class="sxs-lookup"><span data-stu-id="9211e-122">To clear the filter on a mining model in Solution Explorer</span></span>  
  
1.  <span data-ttu-id="9211e-123">ソリューション エクスプローラーで、フィルターが含まれているマイニング モデルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9211e-123">In Solution Explorer, click the mining model that contains the filter.</span></span>  
  
2.  <span data-ttu-id="9211e-124">[**プロパティ**] ウィンドウで、プロパティのフィルターテキストを右クリック `Filter` し、[**すべて選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9211e-124">In the **Properties** window, right-click the filter text in the `Filter` property, and select **Select All**.</span></span>  
  
3.  <span data-ttu-id="9211e-125">BackSpace キーまたは Del キーを押します。</span><span class="sxs-lookup"><span data-stu-id="9211e-125">Press the Backspace or Delete key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9211e-126">参照</span><span class="sxs-lookup"><span data-stu-id="9211e-126">See Also</span></span>  
 <span data-ttu-id="9211e-127">[マイニングモデルからケースデータへのドリルスルー](drill-through-to-case-data-from-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="9211e-127">[Drill Through to Case Data from a Mining Model](drill-through-to-case-data-from-a-mining-model.md) </span></span>  
 <span data-ttu-id="9211e-128">[マイニングモデルタスクと操作方法](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="9211e-128">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="9211e-129">マイニング モデルのフィルター &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="9211e-129">Filters for Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-models-analysis-services-data-mining.md)  
  
  
