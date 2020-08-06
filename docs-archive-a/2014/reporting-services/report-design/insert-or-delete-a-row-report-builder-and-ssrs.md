---
title: 行の挿入または削除 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b9642af3-b3ae-4f78-b0be-8f96b79fc313
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fdec24801d1fae3b95c7d75acb5a3add650d523b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739294"
---
# <a name="insert-or-delete-a-row-report-builder-and-ssrs"></a><span data-ttu-id="7314f-102">行の挿入または削除 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="7314f-102">Insert or Delete a Row (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7314f-103">Tablix データ領域では、行を追加したり削除したりできます。</span><span class="sxs-lookup"><span data-stu-id="7314f-103">You can add or delete rows in a tablix data region.</span></span> <span data-ttu-id="7314f-104">Tablix データ領域は、テーブル、マトリックス、一覧のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="7314f-104">The tablix data region can be a table, a matrix, or a list.</span></span> <span data-ttu-id="7314f-105">次の手順は、グラフおよびゲージのデータ領域には適用されません。</span><span class="sxs-lookup"><span data-stu-id="7314f-105">The following procedures do not apply to the chart and gauge data regions.</span></span>  
  
 <span data-ttu-id="7314f-106">Tablix データ領域では、グループに関連付けられている行 (グループ内の行)、または、グループに関連付けられていない行 (グループ外の行) を追加できます。</span><span class="sxs-lookup"><span data-stu-id="7314f-106">In a tablix data region, you can add rows that are associated with a group (inside a group) or that are not associated with a group (outside a group).</span></span> <span data-ttu-id="7314f-107">グループ内の行は、一意のグループ値ごとに 1 つ存在します。</span><span class="sxs-lookup"><span data-stu-id="7314f-107">A row that is inside a group repeats once per unique group value.</span></span> <span data-ttu-id="7314f-108">たとえば、グループ内の行が、色名を格納するデータ列の値に基づいている場合、色名ごとに 1 つの行が存在することになります。</span><span class="sxs-lookup"><span data-stu-id="7314f-108">For example, a row inside a group based on the value in a data column that contains color names, repeats once per distinct color name.</span></span> <span data-ttu-id="7314f-109">入れ子にされているグループの場合は、行を子グループの外側、かつ親グループの内側に置くことができます。</span><span class="sxs-lookup"><span data-stu-id="7314f-109">For nested groups, a row can be outside the child group but inside the parent group.</span></span> <span data-ttu-id="7314f-110">この場合は、親グループ内の一意の値ごとに 1 つの行が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7314f-110">In this case, the row repeats once for each unique value in the parent group.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-select-a-data-region-so-the-row-and-column-handles-appear"></a><span data-ttu-id="7314f-111">行ハンドルと列ハンドルが表示されるようにデータ領域を選択するには</span><span class="sxs-lookup"><span data-stu-id="7314f-111">To select a data region so the row and column handles appear</span></span>  
  
-   <span data-ttu-id="7314f-112">[デザイン] ビューで、Tablix データ領域の左上隅をクリックすると、その上部および横に列ハンドルと行ハンドルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7314f-112">In Design view, click the upper left corner of the tablix data region so that column and row handles appear above and next to it.</span></span>  
  
     <span data-ttu-id="7314f-113">データ領域の領域の詳細については、「 [&#40;レポートビルダーと SSRS&#41;の一覧](tables-matrices-and-lists-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7314f-113">For more information about data region areas, see [Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-insert-a-row-in-a-selected-data-region"></a><span data-ttu-id="7314f-114">選択したデータ領域に行を挿入するには</span><span class="sxs-lookup"><span data-stu-id="7314f-114">To insert a row in a selected data region</span></span>  
  
-   <span data-ttu-id="7314f-115">行の挿入位置にある行ハンドルを右クリックし、 **[行を挿入]** をクリックして、 **[上]** または **[下]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7314f-115">Right-click a row handle where you want to insert a row, click **Insert Row**, and then click **Above** or **Below**.</span></span>  
  
     <span data-ttu-id="7314f-116">\- - または -</span><span class="sxs-lookup"><span data-stu-id="7314f-116">\- or -</span></span>  
  
-   <span data-ttu-id="7314f-117">行の挿入位置にあるデータ領域のセルを右クリックし、 **[行を挿入]** をクリックし、 **[上]** または **[下]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7314f-117">Right-click a cell in the data region where you want to insert a row, click **Insert Row**, and then click **Above** or **Below**.</span></span>  
  
### <a name="to-delete-a-row-from-a-selected-data-region"></a><span data-ttu-id="7314f-118">選択したデータ領域から行を削除するには</span><span class="sxs-lookup"><span data-stu-id="7314f-118">To delete a row from a selected data region</span></span>  
  
-   <span data-ttu-id="7314f-119">削除する行を選択し、選択した行のうち 1 つのハンドルを右クリックして、 **[行の削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7314f-119">Select the row or rows that you want to delete, right-click the handle for one of the rows you selected, and then click **Delete Rows**.</span></span>  
  
     <span data-ttu-id="7314f-120">\- - または -</span><span class="sxs-lookup"><span data-stu-id="7314f-120">\- or -</span></span>  
  
-   <span data-ttu-id="7314f-121">行の削除位置にあるデータ領域のセルを右クリックし、 **[行の削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7314f-121">Right-click a cell in the data region where you want to delete a row, and then click **Delete Rows**.</span></span>  
  
### <a name="to-insert-a-row-in-a-group-in-a-selected-data-region"></a><span data-ttu-id="7314f-122">選択したデータ領域のグループに行を挿入するには</span><span class="sxs-lookup"><span data-stu-id="7314f-122">To insert a row in a group in a selected data region</span></span>  
  
-   <span data-ttu-id="7314f-123">Tablix データ領域の行グループ領域で、行の挿入位置の行グループのセルを右クリックし、 **[行を挿入]** をクリックした後、 **[上 - 外側のグループ]** 、 **[上 - 内側のグループ]** 、 **[下 - 内側のグループ]** 、または **[下 - 外側のグループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7314f-123">Right-click a row group cell in the row group area of a tablix data region where you want to insert a row, click **Insert Row**, and then click **Above - Outside Group**, **Above - Inside Group**, **Below - Inside Group**, or **Below - Outside Group**.</span></span>  
  
     <span data-ttu-id="7314f-124">クリックした行グループのセルに対応するグループの内側または外側に行が追加されます。</span><span class="sxs-lookup"><span data-stu-id="7314f-124">A row is added either inside or outside the group represented by the row group cell you clicked on.</span></span>  
  
### <a name="to-delete-a-row-from-a-group-in-a-selected-data-region"></a><span data-ttu-id="7314f-125">選択したデータ領域のグループから行を削除するには</span><span class="sxs-lookup"><span data-stu-id="7314f-125">To delete a row from a group in a selected data region</span></span>  
  
-   <span data-ttu-id="7314f-126">Tablix データ領域の行グループ領域で、行の削除位置にある行グループ セルを右クリックし、 **[行の削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7314f-126">Right-click a row group cell in the row group area of a tablix data region where you want to delete a row, and then click **Delete Rows**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7314f-127">参照</span><span class="sxs-lookup"><span data-stu-id="7314f-127">See Also</span></span>  
 <span data-ttu-id="7314f-128">[Tablix データ領域 &#40;レポート ビルダーおよび SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7314f-128">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7314f-129">[グループについて &#40;レポート ビルダーおよび SSRS&#41;](understanding-groups-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7314f-129">[Understanding Groups &#40;Report Builder and SSRS&#41;](understanding-groups-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7314f-130">[テーブル &#40;レポート ビルダーおよび SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7314f-130">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7314f-131">[マトリックス &#40;レポート ビルダーおよび SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7314f-131">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7314f-132">[一覧 &#40;レポート ビルダーおよび SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7314f-132">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7314f-133">一覧 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7314f-133">Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
