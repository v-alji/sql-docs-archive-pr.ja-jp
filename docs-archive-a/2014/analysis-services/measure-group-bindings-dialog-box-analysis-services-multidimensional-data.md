---
title: '[メジャーグループのバインド] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.dimensionusage.definerelationship.measuregroupbindings.f1
helpviewer_keywords:
- Measure Group Bindings dialog box
ms.assetid: ed642780-5350-438e-af73-b9ceab3f876d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 78693901a5898b140d6efeed16b6f0eaa7577e69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741465"
---
# <a name="measure-group-bindings-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="62a54-102">[メジャー グループのバインド] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="62a54-102">Measure Group Bindings Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="62a54-103">**[リレーションシップの定義]** ダイアログ ボックスから **[メジャー グループのバインド]** ダイアログ ボックスを使用すると、通常のディメンション リレーションシップのキューブ ディメンションの非粒度属性とメジャー グループ内の列との間で、直接リレーションシップを作成したり変更したりできます。また、キューブ ディメンションの属性に NULL 処理オプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="62a54-103">Use the **Measure Group Bindings** dialog box to create and modify direct relationships between non-granularity attributes in a cube dimension and columns in a measure group for a regular dimension relationship, as well as to specify null processing options for any attribute in a cube dimension, from the **Define Relationship** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="62a54-104">Options</span><span class="sxs-lookup"><span data-stu-id="62a54-104">Options</span></span>  
 <span data-ttu-id="62a54-105">**[メジャー グループ テーブル]**</span><span class="sxs-lookup"><span data-stu-id="62a54-105">**Measure group table**</span></span>  
 <span data-ttu-id="62a54-106">選択したメジャー グループに対するファクト テーブルの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="62a54-106">Displays the name of the fact table for the selected measure group.</span></span>  
  
 <span data-ttu-id="62a54-107">**属性**</span><span class="sxs-lookup"><span data-stu-id="62a54-107">**Attributes**</span></span>  
 <span data-ttu-id="62a54-108">属性とディメンション テーブルのグリッドを表示します。</span><span class="sxs-lookup"><span data-stu-id="62a54-108">Displays a grid of attributes and dimension tables.</span></span> <span data-ttu-id="62a54-109">属性を選択し、 **[リレーションシップ]** でプロパティを作成、変更します。</span><span class="sxs-lookup"><span data-stu-id="62a54-109">Select an attribute to create or modify properties in **Relationship** for the selected attribute.</span></span> <span data-ttu-id="62a54-110">このグリッドには次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="62a54-110">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="62a54-111">オプション</span><span class="sxs-lookup"><span data-stu-id="62a54-111">Option</span></span>|<span data-ttu-id="62a54-112">定義</span><span class="sxs-lookup"><span data-stu-id="62a54-112">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="62a54-113">**属性名**</span><span class="sxs-lookup"><span data-stu-id="62a54-113">**Attribute Name**</span></span>|<span data-ttu-id="62a54-114">属性の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="62a54-114">Displays the name of the attribute.</span></span>|  
|<span data-ttu-id="62a54-115">**ディメンションテーブル**</span><span class="sxs-lookup"><span data-stu-id="62a54-115">**Dimension Table**</span></span>|<span data-ttu-id="62a54-116">属性が基づくディメンション テーブルの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="62a54-116">Displays the name of the dimension table on which the attribute is based.</span></span>|  
  
 <span data-ttu-id="62a54-117">**リレーションシップ**</span><span class="sxs-lookup"><span data-stu-id="62a54-117">**Relationship**</span></span>  
 <span data-ttu-id="62a54-118">選択した属性に対するディメンション テーブルの列と、選択したメジャー グループに対するファクト テーブルの列との間のリレーションシップのグリッド、およびリレーションシップの NULL 処理オプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="62a54-118">Displays a grid of relationships between dimension table columns for the selected attribute and fact table columns for the selected measure group as well as the null processing option for the relationship.</span></span> <span data-ttu-id="62a54-119">このグリッドには次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="62a54-119">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="62a54-120">オプション</span><span class="sxs-lookup"><span data-stu-id="62a54-120">Option</span></span>|<span data-ttu-id="62a54-121">定義</span><span class="sxs-lookup"><span data-stu-id="62a54-121">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="62a54-122">**[ディメンション列]**</span><span class="sxs-lookup"><span data-stu-id="62a54-122">**Dimension Columns**</span></span>|<span data-ttu-id="62a54-123">**[属性]** で選択した属性が基づくディメンション テーブルの列を表示します。</span><span class="sxs-lookup"><span data-stu-id="62a54-123">Displays the columns from the dimension table on which the attribute selected in **Attributes** is based.</span></span>|  
|<span data-ttu-id="62a54-124">**[メジャー グループ列]**</span><span class="sxs-lookup"><span data-stu-id="62a54-124">**Measure Group Columns**</span></span>|<span data-ttu-id="62a54-125">**[ディメンションから継承しました]** を選択してディメンションから継承されたメジャー グループのリレーションシップを使用するか、メジャー グループが基づくファクト テーブルの列を選択してリレーションシップを明示的に定義します。</span><span class="sxs-lookup"><span data-stu-id="62a54-125">Select either **Inherited from dimension** to use the measure group relationship inherited from the dimension, or select a column from the fact table on which the measure group is based to explicitly define a relationship.</span></span>|  
|<span data-ttu-id="62a54-126">**[NULL 処理]**</span><span class="sxs-lookup"><span data-stu-id="62a54-126">**Null Processing**</span></span>|<span data-ttu-id="62a54-127">属性に対する NULL 処理オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="62a54-127">Select a null processing option for the attribute.</span></span> <span data-ttu-id="62a54-128">NULL 処理オプションの詳細については、「[NullProcessing 要素 &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/nullprocessing-element-assl)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62a54-128">For more information about null processing options, see [NullProcessing Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/nullprocessing-element-assl).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62a54-129">参照</span><span class="sxs-lookup"><span data-stu-id="62a54-129">See Also</span></span>  
 <span data-ttu-id="62a54-130">[[リレーションシップの定義] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](define-relationship-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="62a54-130">[Define Relationship Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](define-relationship-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="62a54-131">多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;</span><span class="sxs-lookup"><span data-stu-id="62a54-131">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
