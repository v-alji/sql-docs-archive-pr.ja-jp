---
title: 詳細グループの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ef8efba-6d48-4aeb-a3b9-a02ba5a44614
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 24b1f6af1aaf336a69a0068636ced60c364e556d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640734"
---
# <a name="add-a-details-group-report-builder-and-ssrs"></a><span data-ttu-id="32cdb-102">詳細グループの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="32cdb-102">Add a Details Group (Report Builder and SSRS)</span></span>
  <span data-ttu-id="32cdb-103">レポート データセットの詳細データは、グループ式のないグループとして指定されます。</span><span class="sxs-lookup"><span data-stu-id="32cdb-103">The detail data from a report dataset is specified as a group with no group expression.</span></span> <span data-ttu-id="32cdb-104">マトリックスの詳細データを表示したり、表や一覧から削除した詳細データを再び追加したり、詳細グループを追加したりするときは、既存の Tablix データ領域に詳細グループを追加します。</span><span class="sxs-lookup"><span data-stu-id="32cdb-104">Add a detail group to an existing tablix data region when you want to display the detail data for a matrix, add back detail data that you have deleted from a table or list, or to add additional detail groups.</span></span> <span data-ttu-id="32cdb-105">グループの詳細については、「 [グループについて (レポート ビルダーおよび SSRS)](understanding-groups-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32cdb-105">For more information about groups, see [Understanding Groups &#40;Report Builder and SSRS&#41;](understanding-groups-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-details-group-to-a-tablix-data-region"></a><span data-ttu-id="32cdb-106">詳細グループを Tablix データ領域に追加するには</span><span class="sxs-lookup"><span data-stu-id="32cdb-106">To add a details group to a tablix data region</span></span>  
  
1.  <span data-ttu-id="32cdb-107">デザイン画面で、Tablix データ領域の任意の場所をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="32cdb-107">On the design surface, click anywhere in a tablix data region to select it.</span></span> <span data-ttu-id="32cdb-108">グループ化ペインに、選択したデータ領域の行グループと列グループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="32cdb-108">The Grouping pane displays the row and column groups for the selected data region.</span></span>  
  
2.  <span data-ttu-id="32cdb-109">[グループ化] ペインで、最も内側の子グループを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="32cdb-109">In the Grouping pane, right-click a group that is an innermost child group.</span></span> <span data-ttu-id="32cdb-110">**[グループの追加]** をクリックし、 **[子グループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="32cdb-110">Click **Add Group**, and then click **Child Group**.</span></span> <span data-ttu-id="32cdb-111">**[Tablix のグループ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="32cdb-111">The **Tablix Group** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="32cdb-112">**[グループ式]** で式を空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="32cdb-112">In **Group expression**, leave the expression blank.</span></span> <span data-ttu-id="32cdb-113">詳細グループには式がありません。</span><span class="sxs-lookup"><span data-stu-id="32cdb-113">A details group has no expression.</span></span>  
  
4.  <span data-ttu-id="32cdb-114">**[詳細データの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="32cdb-114">Select **Show detail data**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="32cdb-115">グループ化ペインで新しい詳細グループが子グループとして追加され、手順 1. で選択したグループの行ハンドルに詳細グループ アイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="32cdb-115">A new details group is added as a child group in the Grouping pane, and the row handle for the group you selected in step 1 displays the details group icon.</span></span> <span data-ttu-id="32cdb-116">Tablix データ領域に関する詳細については、「[Tablix データ領域のセル、行、および列 &#40;レポート ビルダーおよび SSRS&#41;](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32cdb-116">For more information about handles, see [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32cdb-117">参照</span><span class="sxs-lookup"><span data-stu-id="32cdb-117">See Also</span></span>  
 <span data-ttu-id="32cdb-118">[データ領域でのグループの追加または削除 &#40;レポート ビルダーおよび SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="32cdb-118">[Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="32cdb-119">[グループについて &#40;レポート ビルダーおよび SSRS&#41;](understanding-groups-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="32cdb-119">[Understanding Groups &#40;Report Builder and SSRS&#41;](understanding-groups-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="32cdb-120">[Tablix データ領域 &#40;レポート ビルダーおよび SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="32cdb-120">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="32cdb-121">[テーブル &#40;レポートビルダーと SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="32cdb-121">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="32cdb-122">[マトリックス &#40;レポートビルダーと SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="32cdb-122">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="32cdb-123">[&#40;レポートビルダーと SSRS の一覧を表示&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="32cdb-123">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="32cdb-124">テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="32cdb-124">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
