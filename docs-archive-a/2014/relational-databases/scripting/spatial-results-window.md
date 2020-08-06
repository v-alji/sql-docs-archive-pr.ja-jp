---
title: '[空間結果] ウィンドウ'
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2d5a477-6496-4d01-adee-7322ebdfadf3
author: rothja
ms.author: jroth
ms.openlocfilehash: 5e018ec9f016dfc51ed1bb055ba94abf12bc878f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743185"
---
# <a name="spatial-results-window"></a><span data-ttu-id="d1c1f-102">[空間結果] ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="d1c1f-102">Spatial Results Window</span></span>
  <span data-ttu-id="d1c1f-103">**[空間結果]** ウィンドウには、空間データを表示するための視覚的なマッピング ツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d1c1f-103">The **Spatial results** window provides visual mapping tools for viewing spatial data.</span></span> <span data-ttu-id="d1c1f-104">空間結果を表示するには、geometry 型または geography 型のデータを含む空間列がクエリ結果に含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1c1f-104">To view spatial results, your query results must include a spatial column with either geometry or geography data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d1c1f-105">**[空間結果]** ウィンドウを使用できるのは、 **[結果]** ウィンドウ内のグリッドに結果が返される場合だけです。</span><span class="sxs-lookup"><span data-stu-id="d1c1f-105">The **Spatial results** window is only available if your results are returned to a grid in the **Results** window.</span></span> <span data-ttu-id="d1c1f-106">結果がテキストとして返されるように設定すると、このウィンドウは使用できません。</span><span class="sxs-lookup"><span data-stu-id="d1c1f-106">If you specify that your results are returned as text, this window is not available.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d1c1f-107">オプション</span><span class="sxs-lookup"><span data-stu-id="d1c1f-107">Options</span></span>  
 <span data-ttu-id="d1c1f-108">**[空間列の選択]**</span><span class="sxs-lookup"><span data-stu-id="d1c1f-108">**Select spatial column**</span></span>  
 <span data-ttu-id="d1c1f-109">クエリ結果の空間列から、表示する空間列を指定します。</span><span class="sxs-lookup"><span data-stu-id="d1c1f-109">Specify the spatial column you want to view from the spatial columns in the query results.</span></span> <span data-ttu-id="d1c1f-110">列は、一度に 1 つしか選択できません。</span><span class="sxs-lookup"><span data-stu-id="d1c1f-110">Only one column can be selected at a time.</span></span>  
  
 <span data-ttu-id="d1c1f-111">**[ラベル列の選択]**</span><span class="sxs-lookup"><span data-stu-id="d1c1f-111">**Select label column**</span></span>  
 <span data-ttu-id="d1c1f-112">クエリ結果に返された列から、空間データにラベルを付けるための空間列以外の列を指定します。</span><span class="sxs-lookup"><span data-stu-id="d1c1f-112">Specify the non-spatial column from the columns returned in the query results to label the spatial data.</span></span> <span data-ttu-id="d1c1f-113">列は、一度に 1 つしか選択できません。</span><span class="sxs-lookup"><span data-stu-id="d1c1f-113">Only one column can be selected at a time.</span></span>  
  
 <span data-ttu-id="d1c1f-114">クエリで Point インスタンスのみが返される場合は、このオプションを使用できません。</span><span class="sxs-lookup"><span data-stu-id="d1c1f-114">This option is not available when only point instances are returned in a query.</span></span>  
  
 <span data-ttu-id="d1c1f-115">**[投影の選択]**</span><span class="sxs-lookup"><span data-stu-id="d1c1f-115">**Select projection**</span></span>  
 <span data-ttu-id="d1c1f-116">geography 型のデータを、正距円筒図法、メルカトル図法、ロビンソン図法、ボンヌ図法という 4 つの投影法のいずれかで表示します。</span><span class="sxs-lookup"><span data-stu-id="d1c1f-116">Display geography data in one of four projections: Equirectangular, Mercator, Robinson, or Bonne.</span></span>  
  
 <span data-ttu-id="d1c1f-117">このオプションは、geometry 型のデータには使用できません。</span><span class="sxs-lookup"><span data-stu-id="d1c1f-117">This option is not available for geometry data.</span></span>  
  
 <span data-ttu-id="d1c1f-118">**[ズーム]**</span><span class="sxs-lookup"><span data-stu-id="d1c1f-118">**Zoom**</span></span>  
 <span data-ttu-id="d1c1f-119">指数スケール上でマップの表示を調整します。</span><span class="sxs-lookup"><span data-stu-id="d1c1f-119">Adjust the map display on an exponential scale.</span></span>  
  
 <span data-ttu-id="d1c1f-120">**[グリッド線の表示]**</span><span class="sxs-lookup"><span data-stu-id="d1c1f-120">**Show grid lines**</span></span>  
 <span data-ttu-id="d1c1f-121">座標グリッド線の表示と非表示を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="d1c1f-121">Toggle coordinate gridlines on or off.</span></span>  
  
 <span data-ttu-id="d1c1f-122">多角形の場合、ラベルが表示されるのは、図形がラベルのテキストを保持するのに十分な大きさの場合だけです。</span><span class="sxs-lookup"><span data-stu-id="d1c1f-122">For polygon shapes, the label is displayed only when the shape is large enough to hold the label text.</span></span> <span data-ttu-id="d1c1f-123">小さい図形にラベルを表示するには、ズームを調整します。</span><span class="sxs-lookup"><span data-stu-id="d1c1f-123">To display labels for small shapes, adjust the zoom.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d1c1f-124">Point インスタンスにラベルを付けることはできません。</span><span class="sxs-lookup"><span data-stu-id="d1c1f-124">Point instances cannot be labeled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1c1f-125">参照</span><span class="sxs-lookup"><span data-stu-id="d1c1f-125">See Also</span></span>  
 <span data-ttu-id="d1c1f-126">[オブジェクト エクスプローラーでの空間データの表示](view-spatial-data-in-object-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="d1c1f-126">[View Spatial Data in Object Explorer](view-spatial-data-in-object-explorer.md) </span></span>  
 <span data-ttu-id="d1c1f-127">[空間データ &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d1c1f-127">[Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md) </span></span>  
 <span data-ttu-id="d1c1f-128">[データベース エンジン クエリ エディター &#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="d1c1f-128">[Database Engine Query Editor &#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="d1c1f-129">クエリおよびテキスト エディター &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="d1c1f-129">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](query-and-text-editors-sql-server-management-studio.md)  
  
  
