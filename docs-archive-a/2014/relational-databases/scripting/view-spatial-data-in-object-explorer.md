---
title: オブジェクト エクスプローラーでの空間データの表示
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 59cca562-e3f5-4257-b868-adcbcc0142cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 881adf69ee83ee4b7536afae0b190fbec90f132c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641584"
---
# <a name="view-spatial-data-in-object-explorer"></a><span data-ttu-id="b6c30-102">オブジェクト エクスプローラーでの空間データの表示</span><span class="sxs-lookup"><span data-stu-id="b6c30-102">View Spatial Data in Object Explorer</span></span>
  <span data-ttu-id="b6c30-103">クエリ エディターの **[空間結果]** ウィンドウには、 **[結果]** ウィンドウにグリッド形式で表示されるデータに加えて、空間データ結果を表示するための視覚的なマッピング ツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b6c30-103">The **Spatial results** window in Query Editor provides visual mapping tools for viewing spatial data results in addition to the data displayed in grid format in the **Results** window.</span></span> <span data-ttu-id="b6c30-104">**[空間結果]** ウィンドウに空間データを表示するには、geometry 型または geography 型のデータを含む空間データ列が少なくとも 1 つクエリ結果に含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6c30-104">To display spatial data in the **Spatial Results** window, your query results must contain at least one spatial data column with either geometry or geography data.</span></span>  
  
### <a name="to-view-spatial-data-in-the-spatial-results-window"></a><span data-ttu-id="b6c30-105">[空間結果] ウィンドウに空間データを表示するには</span><span class="sxs-lookup"><span data-stu-id="b6c30-105">To view spatial data in the Spatial results window</span></span>  
  
1.  <span data-ttu-id="b6c30-106">クエリ エディターで、 **[空間結果]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6c30-106">In Query Editor, click the **Spatial results** tab.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b6c30-107">クエリ結果に空間データが含まれていない場合、または結果がテキストとして返されるように指定した場合、このウィンドウは使用できません。</span><span class="sxs-lookup"><span data-stu-id="b6c30-107">This window is not available if your query results do not contain spatial data or if you specify that your results are returned as text.</span></span>  
  
2.  <span data-ttu-id="b6c30-108">**[空間列の選択]** の一覧から、表示する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="b6c30-108">Select the column you want to view from the **Select spatial column** list.</span></span> <span data-ttu-id="b6c30-109">テーブル内に空間列が 1 つしかない場合は、この列が一覧の既定のオプションです。</span><span class="sxs-lookup"><span data-stu-id="b6c30-109">If there is only one spatial column in your table, this column is the default option in the list.</span></span>  
  
3.  <span data-ttu-id="b6c30-110">**[ラベル列の選択]** の一覧から、データ ラベルとして使用する、空間列以外の列を選択します。</span><span class="sxs-lookup"><span data-stu-id="b6c30-110">Select the non-spatial column you want to use as data labels from the **Select label columns** list.</span></span>  
  
4.  <span data-ttu-id="b6c30-111">**[投影の選択]** の一覧から、geography 型のデータに使用する投影法を選択します。</span><span class="sxs-lookup"><span data-stu-id="b6c30-111">Select the projection you want for geography data from the **Select projection** list.</span></span> <span data-ttu-id="b6c30-112">既定の投影法は正距円筒図法です。その他に、メルカトル図法、ロビンソン図法、およびボンヌ図法という投影法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b6c30-112">The default projection is Equirectangular; other projections available are Mercator, Robinson, or Bonne.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b6c30-113">空間列に geometry 型のデータが含まれている場合、 **[投影の選択]** は使用できません。</span><span class="sxs-lookup"><span data-stu-id="b6c30-113">**Select projection** is not available if your spatial column contains geometry data.</span></span>  
  
5.  <span data-ttu-id="b6c30-114">**[ズーム]** スライダーを調整して、マップされた要素の視覚的なサイズを大きくします。</span><span class="sxs-lookup"><span data-stu-id="b6c30-114">Adjust the **Zoom** slider to increase the visual size of mapped elements.</span></span> <span data-ttu-id="b6c30-115">多角形の場合、ラベルが表示されるのは、図形がラベルのテキストを保持するのに十分な大きさの場合だけです。</span><span class="sxs-lookup"><span data-stu-id="b6c30-115">For polygon shapes, the label is visible only when the shape is large enough to hold the label text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6c30-116">参照</span><span class="sxs-lookup"><span data-stu-id="b6c30-116">See Also</span></span>  
 <span data-ttu-id="b6c30-117">[[空間結果] ウィンドウ](spatial-results-window.md) </span><span class="sxs-lookup"><span data-stu-id="b6c30-117">[Spatial Results Window](spatial-results-window.md) </span></span>  
 <span data-ttu-id="b6c30-118">[データベース エンジン クエリ エディター &#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="b6c30-118">[Database Engine Query Editor &#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="b6c30-119">クエリおよびテキスト エディター &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b6c30-119">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](query-and-text-editors-sql-server-management-studio.md)  
  
  
