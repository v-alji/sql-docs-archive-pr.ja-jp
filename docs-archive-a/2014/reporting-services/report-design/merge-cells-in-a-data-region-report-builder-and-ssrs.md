---
title: データ領域内のセルの結合 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 43551300-89b2-4f4e-af09-69084324afaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c69ce8182bda3e0b644893e97b69280a003f5732
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719551"
---
# <a name="merge-cells-in-a-data-region-report-builder-and-ssrs"></a><span data-ttu-id="e5f43-102">データ領域内のセルの結合 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="e5f43-102">Merge Cells in a Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e5f43-103">データ領域内のセルを結合すると、セルとセルの合成や、データ領域の外観の向上のほか、複数の列グループおよび行グループにまたがるラベルの指定が可能になります。</span><span class="sxs-lookup"><span data-stu-id="e5f43-103">You can merge cells in a data region to combine cells, improve data region appearance, or provide spanning labels for column groups and row groups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e5f43-104">セルは、コーナー、列ヘッダー、グループ定義 (または行ヘッダー)、および本文など、データ領域の各領域内でのみ結合できます。</span><span class="sxs-lookup"><span data-stu-id="e5f43-104">Cells can only be merged within each area of a data region: corner, column headers, group definition (or row headers), and body.</span></span> <span data-ttu-id="e5f43-105">領域の境界を越えるセルを結合することはできません。</span><span class="sxs-lookup"><span data-stu-id="e5f43-105">You cannot merge cells that cross area boundaries.</span></span> <span data-ttu-id="e5f43-106">たとえば、データ領域のコーナー領域のセルと行グループ領域のセルを結合することはできません。</span><span class="sxs-lookup"><span data-stu-id="e5f43-106">For example, you cannot merge a cell in the data region corner area with a cell in the row group area.</span></span> <span data-ttu-id="e5f43-107">Tablix 領域の詳細については、「 [&#40;レポートビルダーと SSRS&#41;の一覧](tables-matrices-and-lists-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5f43-107">For more information about tablix areas, see [Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-merge-cells-in-a-data-region"></a><span data-ttu-id="e5f43-108">データ領域内のセルを結合するには</span><span class="sxs-lookup"><span data-stu-id="e5f43-108">To merge cells in a data region</span></span>  
  
1.  <span data-ttu-id="e5f43-109">レポート デザイン画面上のデータ領域で、結合する最初のセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5f43-109">In the data region on the report design surface, click the first cell to merge.</span></span> <span data-ttu-id="e5f43-110">マウスの左ボタンを押したまま垂直方向または水平方向にドラッグして、隣接するセルを選択します。</span><span class="sxs-lookup"><span data-stu-id="e5f43-110">Holding the left mouse button down, drag vertically or horizontally to select adjacent cells.</span></span> <span data-ttu-id="e5f43-111">選択したセルは強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="e5f43-111">The selected cells are highlighted.</span></span>  
  
2.  <span data-ttu-id="e5f43-112">選択したセルを右クリックし、 **[セルの結合]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e5f43-112">Right-click the selected cells and select **Merge Cells**.</span></span> <span data-ttu-id="e5f43-113">選択したセルが 1 つのセルに結合されます。</span><span class="sxs-lookup"><span data-stu-id="e5f43-113">The selected cells are combined into a single cell.</span></span>  
  
3.  <span data-ttu-id="e5f43-114">手順 1. と手順 2. を繰り返し、データ領域内で隣接する他のセルを結合します。</span><span class="sxs-lookup"><span data-stu-id="e5f43-114">Repeat steps 1 and 2 to merge other adjacent cells in a data region.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5f43-115">参照</span><span class="sxs-lookup"><span data-stu-id="e5f43-115">See Also</span></span>  
 <span data-ttu-id="e5f43-116">[Tablix データ領域 &#40;レポートビルダーと SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e5f43-116">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e5f43-117">[テーブル &#40;レポート ビルダーおよび SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e5f43-117">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e5f43-118">[マトリックス &#40;レポートビルダーと SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e5f43-118">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e5f43-119">[&#40;レポートビルダーと SSRS の一覧を表示&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e5f43-119">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e5f43-120">一覧 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e5f43-120">Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
