---
title: '[アルゴリズムパラメーター] ダイアログボックス (マイニングモデルビュー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.models.algorithmparameters.f1
helpviewer_keywords:
- Algorithm Parameters dialog box
ms.assetid: 57f9f6f8-8ca4-4a6e-8f18-85f0571b7060
author: minewiskan
ms.author: owend
ms.openlocfilehash: 303d8b5bd3437690c65873e106a94cf2ce8eb9f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633679"
---
# <a name="algorithm-parameters-dialog-box-mining-models-view"></a><span data-ttu-id="86fcd-102">[アルゴリズム パラメーター] ダイアログ ボックス ([マイニング モデル] ビュー)</span><span class="sxs-lookup"><span data-stu-id="86fcd-102">Algorithm Parameters Dialog Box (Mining Models View)</span></span>
  <span data-ttu-id="86fcd-103">**[アルゴリズム パラメーター]** ダイアログ ボックスを使用すると、選択したモデルに固有のアルゴリズム パラメーターを調整できます。</span><span class="sxs-lookup"><span data-stu-id="86fcd-103">Use the **Algorithm Parameters** dialog box to adjust algorithm parameters that are specific to the selected model.</span></span> <span data-ttu-id="86fcd-104">アルゴリズム パラメーターを変更する場合、通常マイニング モデルの結果を変更します。</span><span class="sxs-lookup"><span data-stu-id="86fcd-104">When you change an algorithm parameter, you will usually change the results of the mining model.</span></span> <span data-ttu-id="86fcd-105">各パラメーターが結果にどのような影響を与えるかは、使用しているアルゴリズムおよびデータによって異なります。</span><span class="sxs-lookup"><span data-stu-id="86fcd-105">The way that each parameter affects the results depends on the algorithm you are using, and on your data.</span></span> <span data-ttu-id="86fcd-106">詳細については、「 [マイニング モデルとマイニング構造のカスタマイズ](data-mining/customize-mining-models-and-structure.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="86fcd-106">For more information, see [Customize Mining Models and Structure](data-mining/customize-mining-models-and-structure.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="86fcd-107">Options</span><span class="sxs-lookup"><span data-stu-id="86fcd-107">Options</span></span>  
 <span data-ttu-id="86fcd-108">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="86fcd-108">**Parameters**</span></span>  
 <span data-ttu-id="86fcd-109">選択されたマイニング モデルに使用できるパラメーターを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="86fcd-109">Lists the parameters that are available for the selected mining model.</span></span>  
  
 <span data-ttu-id="86fcd-110">次の表に、使用可能な列を説明します。</span><span class="sxs-lookup"><span data-stu-id="86fcd-110">The following list describes the available columns.</span></span>  
  
|<span data-ttu-id="86fcd-111">列</span><span class="sxs-lookup"><span data-stu-id="86fcd-111">Column</span></span>|<span data-ttu-id="86fcd-112">説明</span><span class="sxs-lookup"><span data-stu-id="86fcd-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="86fcd-113">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="86fcd-113">**Parameter**</span></span>|<span data-ttu-id="86fcd-114">パラメーターの名前の一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="86fcd-114">List the name of the parameter.</span></span>|  
|<span data-ttu-id="86fcd-115">**Value**</span><span class="sxs-lookup"><span data-stu-id="86fcd-115">**Value**</span></span>|<span data-ttu-id="86fcd-116">パラメーターの既定値を変更する場合にのみ値を入力します。</span><span class="sxs-lookup"><span data-stu-id="86fcd-116">Enter a value only if you want to change the default value of the parameter.</span></span>|  
|<span data-ttu-id="86fcd-117">**[Default]**</span><span class="sxs-lookup"><span data-stu-id="86fcd-117">**Default**</span></span>|<span data-ttu-id="86fcd-118">**[値]** 列に値が指定されていない場合にアルゴリズムが使用するパラメーターの既定値を示します。</span><span class="sxs-lookup"><span data-stu-id="86fcd-118">List the default value of the parameter that the algorithm will use if you do not supply a value in the **Value** column.</span></span>|  
|<span data-ttu-id="86fcd-119">**Range**</span><span class="sxs-lookup"><span data-stu-id="86fcd-119">**Range**</span></span>|<span data-ttu-id="86fcd-120">**[値]** 列に入力できる値の範囲を示します。</span><span class="sxs-lookup"><span data-stu-id="86fcd-120">List the range of possible values that you can enter into the **Value** column.</span></span> <span data-ttu-id="86fcd-121">範囲には、次のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="86fcd-121">The ranges can be one of the following:</span></span><br /><br /> <span data-ttu-id="86fcd-122">個別のリスト (1、2、3など)</span><span class="sxs-lookup"><span data-stu-id="86fcd-122">A discrete list, such as 1, 2, 3</span></span><br /><br /> <span data-ttu-id="86fcd-123">包括範囲 ([0, 100] など)</span><span class="sxs-lookup"><span data-stu-id="86fcd-123">An inclusive range, such as [0, 100]</span></span><br /><br /> <span data-ttu-id="86fcd-124">(0,...) などの排他的範囲</span><span class="sxs-lookup"><span data-stu-id="86fcd-124">An exclusive range, such as (0,...)</span></span><br /><br /> <span data-ttu-id="86fcd-125">[0,...) のような組み合わせ</span><span class="sxs-lookup"><span data-stu-id="86fcd-125">A combination, such as [0,...)</span></span>|  
  
 <span data-ttu-id="86fcd-126">**説明**</span><span class="sxs-lookup"><span data-stu-id="86fcd-126">**Description**</span></span>  
 <span data-ttu-id="86fcd-127">**[パラメーター]** の一覧で選択されたパラメーターを説明します。</span><span class="sxs-lookup"><span data-stu-id="86fcd-127">Describes the selected parameter in the **Parameters** list.</span></span>  
  
 <span data-ttu-id="86fcd-128">**[追加]**</span><span class="sxs-lookup"><span data-stu-id="86fcd-128">**Add**</span></span>  
 <span data-ttu-id="86fcd-129">このボタンをクリックして、アルゴリズム固有のその他のパラメーターを一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="86fcd-129">Click to add additional, algorithm specific-parameters to the list.</span></span> <span data-ttu-id="86fcd-130">パラメーターを追加した後で、正しい名前を **[パラメーター]** 列に入力し、 **[値]** 列に値を入力します。</span><span class="sxs-lookup"><span data-stu-id="86fcd-130">After adding the parameter, you can enter the correct name in the **Parameter** column and provide a value in the **Value** column.</span></span>  
  
 <span data-ttu-id="86fcd-131">**削除**</span><span class="sxs-lookup"><span data-stu-id="86fcd-131">**Remove**</span></span>  
 <span data-ttu-id="86fcd-132">このボタンをクリックして、カスタム パラメーターを一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="86fcd-132">Click to delete a custom parameter from the list.</span></span>  
  
 <span data-ttu-id="86fcd-133">標準の Analysis Services アルゴリズム パラメーターのいずれかを一覧から削除しても、パラメーターはモデルでそのまま使用されますが、そのパラメーターの既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="86fcd-133">If you delete one of the standard Analysis Services algorithm parameters from the list, the parameter will still be used in the model, but with the default values for that parameter.</span></span> <span data-ttu-id="86fcd-134">パラメーターは完全に削除されず、次にダイアログ ボックスを開いたときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="86fcd-134">The parameter is not permanently deleted and will appear the next time that you open the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86fcd-135">参照</span><span class="sxs-lookup"><span data-stu-id="86fcd-135">See Also</span></span>  
 <span data-ttu-id="86fcd-136">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="86fcd-136">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="86fcd-137">[マイニングモデルビュー &#40;データマイニングモデルデザイナー&#41;](mining-models-view-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="86fcd-137">[Mining Models View &#40;Data Mining Model Designer&#41;](mining-models-view-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="86fcd-138">データ マイニング オブジェクトの移動</span><span class="sxs-lookup"><span data-stu-id="86fcd-138">Moving Data Mining Objects</span></span>](data-mining/moving-data-mining-objects.md)  
  
  
