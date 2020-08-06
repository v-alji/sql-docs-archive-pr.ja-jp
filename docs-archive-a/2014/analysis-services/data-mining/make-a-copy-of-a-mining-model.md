---
title: マイニングモデルのコピーを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], copying
- mining models [Analysis Services], creating
- mining models [Analysis Services], how-to topics
- copying mining models
ms.assetid: 7975bb02-f188-49a0-b7de-5b9b216254ad
author: minewiskan
ms.author: owend
ms.openlocfilehash: a05eb75210ce9f601aeca515cd299f4204908705
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631360"
---
# <a name="make-a-copy-of-a-mining-model"></a><span data-ttu-id="b16a9-102">マイニング モデルのコピーの作成</span><span class="sxs-lookup"><span data-stu-id="b16a9-102">Make a Copy of a Mining Model</span></span>
  <span data-ttu-id="b16a9-103">マイニング モデルのコピーの作成は、同じデータに基づいて複数のマイニング モデルをすばやく作成する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="b16a9-103">Creating a copy of a mining model is useful when you want to quickly create several mining models that are based on the same data.</span></span> <span data-ttu-id="b16a9-104">モデルをコピーした後で、パラメーターを変更したり、フィルターを追加したりすることで、新しいコピーを編集できます。</span><span class="sxs-lookup"><span data-stu-id="b16a9-104">After you copy the model, you can then edit the new copy by changing parameters or adding a filter.</span></span>  
  
 <span data-ttu-id="b16a9-105">たとえば、購入記録のテーブルにリンクされた Customers テーブルがある場合、コピーを作成して、年齢や地域などの属性でフィルター選択した顧客の統計区分ごとに別々のマイニング モデルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="b16a9-105">For example, if you have a Customers table that is linked to a table of purchases, you could create copies to generate separate mining models for each customer demographic, filtering on attributes such as age or region.</span></span>  
  
 <span data-ttu-id="b16a9-106">モデルのコンテンツ (グラフィカル表示やモデル パターンなど) をクリップボードにコピーして他のプログラムで使用する方法については、「 [マイニング モデルの表示のコピー](copy-a-view-of-a-mining-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b16a9-106">For information about how to copy the content of the model (such as the graphical representation or the model patterns) to the Clipboard for use in other programs, see [Copy a View of a Mining Model](copy-a-view-of-a-mining-model.md).</span></span>  
  
### <a name="to-create-a-related-mining-model"></a><span data-ttu-id="b16a9-107">関連マイニング モデルを作成するには</span><span class="sxs-lookup"><span data-stu-id="b16a9-107">To create a related mining model</span></span>  
  
1.  <span data-ttu-id="b16a9-108">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーで、マイニング モデルを含むマイニング構造をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b16a9-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Solution Explorer, click the mining structure that contains the mining model.</span></span>  
  
2.  <span data-ttu-id="b16a9-109">**[マイニング モデル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b16a9-109">Click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="b16a9-110">モデルを選択し、右クリックしてショートカット メニューを開きます。</span><span class="sxs-lookup"><span data-stu-id="b16a9-110">Select the model, and right-click to open the shortcut menu.</span></span>  
  
     <span data-ttu-id="b16a9-111">または</span><span class="sxs-lookup"><span data-stu-id="b16a9-111">-or-</span></span>  
  
     <span data-ttu-id="b16a9-112">モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b16a9-112">Select the model.</span></span> <span data-ttu-id="b16a9-113">**[マイニング モデル]** メニューの **[新しいマイニング モデル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b16a9-113">On the **Mining Model** menu, select **New Mining Model**.</span></span>  
  
4.  <span data-ttu-id="b16a9-114">新しいマイニング モデルの名前を入力し、アルゴリズムを選択します。</span><span class="sxs-lookup"><span data-stu-id="b16a9-114">Type a name for the new mining model, and select an algorithm.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-the-filter-on-the-copied-mining-model"></a><span data-ttu-id="b16a9-115">コピーされたマイニング モデルのフィルターを編集するには</span><span class="sxs-lookup"><span data-stu-id="b16a9-115">To edit the filter on the copied mining model</span></span>  
  
1.  <span data-ttu-id="b16a9-116">マイニング モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b16a9-116">Select the mining model.</span></span>  
  
2.  <span data-ttu-id="b16a9-117">[**プロパティ**] ウィンドウで、[**フィルター** ] プロパティのテキストボックスをクリックし、[ビルド **(...)** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b16a9-117">In the **Properties** window, click the text box for the **Filter** property, and the click the build **(...)** button.</span></span>  
  
3.  <span data-ttu-id="b16a9-118">フィルター条件を変更します。</span><span class="sxs-lookup"><span data-stu-id="b16a9-118">Change the filter conditions.</span></span>  
  
     <span data-ttu-id="b16a9-119">フィルター エディターのダイアログ ボックスの使用方法の詳細については、「 [マイニング モデルへのフィルターの適用](apply-a-filter-to-a-mining-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b16a9-119">For more information about how to use the filter editor dialog boxes, see [Apply a Filter to a Mining Model](apply-a-filter-to-a-mining-model.md).</span></span>  
  
4.  <span data-ttu-id="b16a9-120">[**プロパティ**] ウィンドウの `AlgorithmParameters` テキストボックスで、[ **setalgorithm パラメーター**] をクリックし、必要に応じてアルゴリズムパラメーターを変更します。</span><span class="sxs-lookup"><span data-stu-id="b16a9-120">In the **Properties** window, in the `AlgorithmParameters` text box, click **Setalgorithm parameters**, and change algorithm parameters, if desired.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b16a9-121">参照</span><span class="sxs-lookup"><span data-stu-id="b16a9-121">See Also</span></span>  
 <span data-ttu-id="b16a9-122">[マイニングモデルのフィルター &#40;Analysis Services データマイニング&#41;](mining-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="b16a9-122">[Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="b16a9-123">[マイニングモデルタスクと操作方法](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="b16a9-123">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="b16a9-124">マイニング モデルからのフィルターの削除</span><span class="sxs-lookup"><span data-stu-id="b16a9-124">Delete a Filter from a Mining Model</span></span>](delete-a-filter-from-a-mining-model.md)  
  
  
