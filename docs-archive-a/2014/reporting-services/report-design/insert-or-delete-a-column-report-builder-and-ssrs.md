---
title: 列の挿入または削除 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e9db79e2-7e7d-4359-a706-cb746c94182a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9a6f782dbb6cc1024583926aafe4bab1cfe2d042
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739301"
---
# <a name="insert-or-delete-a-column-report-builder-and-ssrs"></a><span data-ttu-id="3fc36-102">列の挿入または削除 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="3fc36-102">Insert or Delete a Column (Report Builder and SSRS)</span></span>
  <span data-ttu-id="3fc36-103">Tablix データ領域では、列を追加したり削除したりできます。</span><span class="sxs-lookup"><span data-stu-id="3fc36-103">You can add or delete columns in a tablix data region.</span></span> <span data-ttu-id="3fc36-104">Tablix データ領域は、テーブル、マトリックス、一覧のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="3fc36-104">The tablix data region can be a table, a matrix, or a list.</span></span> <span data-ttu-id="3fc36-105">次の手順は、グラフおよびゲージのデータ領域には適用されません。</span><span class="sxs-lookup"><span data-stu-id="3fc36-105">The following procedures do not apply to the chart and gauge data regions.</span></span>  
  
 <span data-ttu-id="3fc36-106">Tablix データ領域では、グループに関連付けられている列 (グループ内の列)、またはグループに関連付けられていない列 (グループ外の列) を追加できます。</span><span class="sxs-lookup"><span data-stu-id="3fc36-106">In a tablix data region, you can add columns that are associated with a group (inside a group) or that are not associated with a group (outside a group).</span></span> <span data-ttu-id="3fc36-107">グループ内の列は、一意のグループ値ごとに 1 つ存在します。</span><span class="sxs-lookup"><span data-stu-id="3fc36-107">A column that is inside a group repeats once per unique group value.</span></span> <span data-ttu-id="3fc36-108">たとえば、グループ内の列の値が、色名を格納するデータ列に基づいている場合、色名ごとに 1 つの列が存在することになります。</span><span class="sxs-lookup"><span data-stu-id="3fc36-108">For example, a column inside a group based the value in a data column that contains color names, repeats once per distinct color name.</span></span> <span data-ttu-id="3fc36-109">入れ子にされているグループの場合は、子グループの外側、かつ、親グループの内側に列を配置できます。</span><span class="sxs-lookup"><span data-stu-id="3fc36-109">For nested groups, a column can be outside the child group but inside the parent group.</span></span> <span data-ttu-id="3fc36-110">この場合は、親グループ内の一意の値ごとに 1 つの行が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3fc36-110">In this case, the row repeats once for each unique value in the parent group.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-select-a-data-region-so-that-the-row-and-column-handles-appear"></a><span data-ttu-id="3fc36-111">行ハンドルと列ハンドルが表示されるようにデータ領域を選択するには</span><span class="sxs-lookup"><span data-stu-id="3fc36-111">To select a data region so that the row and column handles appear</span></span>  
  
-   <span data-ttu-id="3fc36-112">[デザイン] ビューで、Tablix データ領域の左上隅をクリックすると、その上部および横に列ハンドルと行ハンドルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3fc36-112">In Design view, click the upper left corner of the tablix data region, so that column and row handles appear above and next to it.</span></span>  
  
     <span data-ttu-id="3fc36-113">データ領域の領域の詳細については、「 [&#40;レポートビルダーと SSRS&#41;の一覧](tables-matrices-and-lists-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fc36-113">For more information about data region areas, see [Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-insert-a-column-in-a-selected-data-region"></a><span data-ttu-id="3fc36-114">選択したデータ領域に列を挿入するには</span><span class="sxs-lookup"><span data-stu-id="3fc36-114">To insert a column in a selected data region</span></span>  
  
-   <span data-ttu-id="3fc36-115">列の挿入位置にある列ハンドルを右クリックし、 **[列の挿入]** をクリックして、 **[左]** または **[右]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fc36-115">Right-click a column handle where you want to insert a column, click **Insert Column**, and then click **Left** or **Right**.</span></span>  
  
     <span data-ttu-id="3fc36-116">-- または --</span><span class="sxs-lookup"><span data-stu-id="3fc36-116">-- or --</span></span>  
  
-   <span data-ttu-id="3fc36-117">データ領域で、行の挿入位置にあるセルを右クリックし、 **[列の挿入]** をクリックして、 **[左]** または **[右]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fc36-117">Right-click a cell in the data region where you want to insert a row, click **Insert Column**, and then click **Left** or **Right**.</span></span>  
  
### <a name="to-delete-a-column-from-a-selected-data-region"></a><span data-ttu-id="3fc36-118">選択したデータ領域から列を削除するには</span><span class="sxs-lookup"><span data-stu-id="3fc36-118">To delete a column from a selected data region</span></span>  
  
-   <span data-ttu-id="3fc36-119">削除する 1 つ以上の列を選択し、選択したいずれかの列のハンドルを右クリックして、 **[列の削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fc36-119">Select the column or columns that you want to delete, right-click the handle for one of the columns you selected, and then click **Delete Columns**.</span></span>  
  
     <span data-ttu-id="3fc36-120">-- または --</span><span class="sxs-lookup"><span data-stu-id="3fc36-120">-- or --</span></span>  
  
-   <span data-ttu-id="3fc36-121">データ領域で、列の削除位置にあるセルを右クリックして、 **[列の削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fc36-121">Right-click a cell in the data region where you want to delete a column, and then click **Delete Columns**.</span></span>  
  
### <a name="to-insert-a-column-in-a-group-in-a-selected-data-region"></a><span data-ttu-id="3fc36-122">選択したデータ領域のグループに列を挿入するには</span><span class="sxs-lookup"><span data-stu-id="3fc36-122">To insert a column in a group in a selected data region</span></span>  
  
-   <span data-ttu-id="3fc36-123">Tablix データ領域の列グループ領域で、列の挿入位置にある列グループ セルを右クリックし、 **[列の挿入]** をクリックした後、 **[左 - 外側のグループ]** 、 **[左 - 内側のグループ]** 、 **[右 - 内側のグループ]** 、または **[右 - 外側のグループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fc36-123">Right-click a column group cell in the column group area of a tablix data region where you want to insert a column, click **Insert Column**, and then click **Left - Outside Group**, **Left - Inside Group**, **Right - Inside Group**, or **Right - Outside Group**.</span></span>  
  
     <span data-ttu-id="3fc36-124">クリックした列グループのセルに対応するグループの内側または外側に列が追加されます。</span><span class="sxs-lookup"><span data-stu-id="3fc36-124">A column is added either inside or outside the group represented by the column group cell you clicked on.</span></span>  
  
### <a name="to-delete-a-column-from-a-group-in-a-selected-data-region"></a><span data-ttu-id="3fc36-125">選択したデータ領域のグループから列を削除するには</span><span class="sxs-lookup"><span data-stu-id="3fc36-125">To delete a column from a group in a selected data region</span></span>  
  
-   <span data-ttu-id="3fc36-126">Tablix データ領域の列グループ領域で、列の削除位置にある列グループ セルを右クリックし、 **[列の削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fc36-126">Right-click a column group cell in the column group area of a tablix data region where you want to delete a column, and then click **Delete Columns**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fc36-127">参照</span><span class="sxs-lookup"><span data-stu-id="3fc36-127">See Also</span></span>  
 <span data-ttu-id="3fc36-128">[グループについて &#40;レポート ビルダーおよび SSRS&#41;](understanding-groups-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3fc36-128">[Understanding Groups &#40;Report Builder and SSRS&#41;](understanding-groups-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3fc36-129">[Tablix データ領域 &#40;レポート ビルダーおよび SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3fc36-129">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3fc36-130">[テーブル &#40;レポート ビルダーおよび SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3fc36-130">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3fc36-131">[マトリックス &#40;レポート ビルダーおよび SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3fc36-131">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3fc36-132">[一覧 &#40;レポート ビルダーおよび SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3fc36-132">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="3fc36-133">一覧 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3fc36-133">Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
