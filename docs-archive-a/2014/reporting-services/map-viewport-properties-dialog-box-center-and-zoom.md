---
title: '[中心とズーム] ([マップビューポートのプロパティ] ダイアログボックス)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapviewport.centerandzoom.f1
- "10506"
ms.assetid: 642a06f5-293f-48e0-97a6-1489dbefa719
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 913c00773abf71ca627b8cc2a94a873484e8ab30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634312"
---
# <a name="map-viewport-properties-dialog-box-center-and-zoom"></a><span data-ttu-id="ff1a4-102">[中心とズーム] ([マップ ビューポートのプロパティ] ダイアログ ボックス)</span><span class="sxs-lookup"><span data-stu-id="ff1a4-102">Map Viewport Properties Dialog Box, Center and Zoom</span></span>
  <span data-ttu-id="ff1a4-103">**[マップ ビューポートのプロパティ]** ダイアログ ボックスの **[中心とズーム]** を選択すると、マップの中心ビューおよび拡大 (縮小) 率を設定できます。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-103">Select **Center and Zoom** for the **Map Viewport Properties** dialog box to set the center view and zoom factor for a map.</span></span> <span data-ttu-id="ff1a4-104">マップのデータ ソースとレポートに含めるマップの境界を指定した後は、ビューの中心および拡大 (縮小) 率を指定して、さらにマップ表示を制御できます。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-104">After you specify a map data source and the boundaries of the map that you want to include in your report, you can specify the view center and the zoom factor to further control the map display.</span></span> <span data-ttu-id="ff1a4-105">中心とズーム値の指定方法により、使用できるオプションも異なります。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-105">Options change depending on which method you use to specify the center and zoom values.</span></span> <span data-ttu-id="ff1a4-106">**式** ([fx]) ボタンをクリックし、オプションの値を設定する式を編集します。\*\*</span><span class="sxs-lookup"><span data-stu-id="ff1a4-106">Click the **Expression** (*fx*) button to edit an expression that sets the value of the option.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ff1a4-107">Options</span><span class="sxs-lookup"><span data-stu-id="ff1a4-107">Options</span></span>  
 <span data-ttu-id="ff1a4-108">**[ビューの中心とズーム レベルを設定する]**</span><span class="sxs-lookup"><span data-stu-id="ff1a4-108">**Set a view center and zoom level**</span></span>  
 <span data-ttu-id="ff1a4-109">ビューの中心およびズーム レベルのカスタム値を指定します。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-109">Choose this option to specify custom values for the view center and the zoom level.</span></span>  
  
 <span data-ttu-id="ff1a4-110">**[マップ レイヤーが表示されるようにマップの中心を設定する]**</span><span class="sxs-lookup"><span data-stu-id="ff1a4-110">**Center map to show a map layer**</span></span>  
 <span data-ttu-id="ff1a4-111">レイヤーを指定し、ビューの中心を自動的にマップ データに設定します。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-111">Choose this option to specify a layer and automatically center the view on its map data.</span></span> <span data-ttu-id="ff1a4-112">たとえば、ビューの中心を LineLayer1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-112">For example, center the view on LineLayer1.</span></span>  
  
 <span data-ttu-id="ff1a4-113">**[埋め込みマップ要素が表示されるようにマップの中心を設定する]**</span><span class="sxs-lookup"><span data-stu-id="ff1a4-113">**Center map to show an embedded map element**</span></span>  
 <span data-ttu-id="ff1a4-114">ビューの中心を特定のデータバインド マップ要素に設定します。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-114">Choose this option to center the view on a specific data-bound map element.</span></span> <span data-ttu-id="ff1a4-115">このオプションを指定するには、空間データと分析データの間にリレーションシップが設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-115">The spatial data must have a relationship with analytical data to specify this option.</span></span>  
  
 <span data-ttu-id="ff1a4-116">たとえば、ビューの中心を、対応フィールドの名前が [City] で対応値が "Seattle" のマップ要素に設定します。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-116">For example, center the view on the map element where the name of the match field is [City] and the match value is "Seattle".</span></span>  
  
 <span data-ttu-id="ff1a4-117">**[すべてのデータバインド マップ要素が表示されるようにマップの中心を設定する]**</span><span class="sxs-lookup"><span data-stu-id="ff1a4-117">**Center map to show all data-bound map elements**</span></span>  
 <span data-ttu-id="ff1a4-118">ビューの中心をレイヤー内のすべてのマップ要素に設定します。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-118">Choose this option to center the view on all map elements in the layer.</span></span> <span data-ttu-id="ff1a4-119">このオプションを指定するには、空間データと分析データの間にリレーションシップが設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-119">The spatial data must have a relationship with analytical data to specify this option.</span></span>  
  
 <span data-ttu-id="ff1a4-120">たとえば、バブル サイズが人口に関連付けられている、市区町村を表示する多角形バブル レイヤーにビューの中心を設定します。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-120">For example, center the view on the polygon bubble layer that shows cities and the bubble size is related to population.</span></span> <span data-ttu-id="ff1a4-121">ビューポートの中心を計算するときに、人口値が一致する市区町村のみが含められます。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-121">Only those cities with a matching population value are included when calculating the center for the viewport.</span></span>  
  
 <span data-ttu-id="ff1a4-122">**[中心とズームのオプション]**</span><span class="sxs-lookup"><span data-stu-id="ff1a4-122">**Center and zoom options**</span></span>  
 <span data-ttu-id="ff1a4-123">ビューの中心およびズーム レベルを指定するオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-123">Select an option to specify the view center and zoom level.</span></span>  
  
 <span data-ttu-id="ff1a4-124">**[ビューの中心の X (%)]**</span><span class="sxs-lookup"><span data-stu-id="ff1a4-124">**View center (X) %**</span></span>  
 <span data-ttu-id="ff1a4-125">水平方向の座標。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-125">The horizontal coordinate.</span></span> <span data-ttu-id="ff1a4-126">既定値 (50%) の場合、</span><span class="sxs-lookup"><span data-stu-id="ff1a4-126">The default value, 50%.</span></span> <span data-ttu-id="ff1a4-127">水平方向の最小値および最大値の中間点にビューの中心が設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-127">centers the view at the midpoint between the minimum and maximum horizontal values.</span></span>  
  
 <span data-ttu-id="ff1a4-128">**[ビューの中心の Y (%)]**</span><span class="sxs-lookup"><span data-stu-id="ff1a4-128">**View center (Y) %**</span></span>  
 <span data-ttu-id="ff1a4-129">垂直方向の座標。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-129">The vertical coordinate.</span></span> <span data-ttu-id="ff1a4-130">既定値 (50%) の場合、垂直方向の最小値および最大値の中間点にビューの中心が設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-130">The default value, 50%, centers the view at the midpoint between the minimum and maximum vertical values.</span></span>  
  
 <span data-ttu-id="ff1a4-131">**[ズーム レベル (%)]**</span><span class="sxs-lookup"><span data-stu-id="ff1a4-131">**Zoom level (%)**</span></span>  
 <span data-ttu-id="ff1a4-132">拡大 (縮小) 率。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-132">The zoom factor.</span></span> <span data-ttu-id="ff1a4-133">既定値 (100%) は、拡大も縮小も行わないことを示します。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-133">The default value, 100%, indicates no magnification.</span></span>  
  
 <span data-ttu-id="ff1a4-134">**[このレイヤーにビューの中心を設定する]**</span><span class="sxs-lookup"><span data-stu-id="ff1a4-134">**Center view on this layer**</span></span>  
 <span data-ttu-id="ff1a4-135">レイヤー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-135">Specify the name of the layer.</span></span>  
  
 <span data-ttu-id="ff1a4-136">**[ビューの中央に配置するマップ要素の条件]**</span><span class="sxs-lookup"><span data-stu-id="ff1a4-136">**Center view on the map element that matches this condition**</span></span>  
 <span data-ttu-id="ff1a4-137">表示される読み取り専用フィールドは、マップ データと分析データを対応付けるために使用します。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-137">The read-only field that is displayed is used to match map data and analytical data.</span></span> <span data-ttu-id="ff1a4-138">対応付ける値を指定します。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-138">Specify the value that you want to match on.</span></span> <span data-ttu-id="ff1a4-139">このマップ要素にビューの中心が自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-139">The view automatically centers on this map element.</span></span> <span data-ttu-id="ff1a4-140">たとえば、NAME = TEXAS などです。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-140">For example, NAME = TEXAS.</span></span> <span data-ttu-id="ff1a4-141">既定では、条件のデータ型は文字列であり、対応付けの際に大文字と小文字は区別されます。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-141">By default, the data type for the condition is String and the match is case-sensitive.</span></span>  
  
 <span data-ttu-id="ff1a4-142">データ型が異なるフィールドを対応付けるには、このデータ型に評価される式を記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-142">To match on a field that has a different data type, you must write an expression that evaluates to that data type.</span></span> <span data-ttu-id="ff1a4-143">たとえば、整数として格納されている 5 桁の郵便番号が対応フィールドである場合、郵便番号 98053 を指定するには、=98053 という式を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff1a4-143">For example, if the match field is a 5 digit postal code that is stored as an integer, then to specify the postal code 98053, you must use the expression =98053.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff1a4-144">参照</span><span class="sxs-lookup"><span data-stu-id="ff1a4-144">See Also</span></span>  
 [<span data-ttu-id="ff1a4-145">マップ &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ff1a4-145">Maps &#40;Report Builder and SSRS&#41;</span></span>](report-design/maps-report-builder-and-ssrs.md)  
  
  
