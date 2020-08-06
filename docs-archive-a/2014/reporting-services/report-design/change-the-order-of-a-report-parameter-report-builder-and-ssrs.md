---
title: レポート パラメーターの順序の変更 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: abd61e19-dba3-423c-a26c-e8bc43197d3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ad9dd25be7a87fee089a48849fcc716e682e4c64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737933"
---
# <a name="change-the-order-of-a-report-parameter-report-builder-and-ssrs"></a><span data-ttu-id="dfec5-102">レポート パラメーターの順序の変更 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="dfec5-102">Change the Order of a Report Parameter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="dfec5-103">従属パラメーターが、そのパラメーターが依存するパラメーターの前にリストされている場合、レポート パラメーターの順序を変更します。</span><span class="sxs-lookup"><span data-stu-id="dfec5-103">Change the order of report parameters when you have a dependent parameter that is listed before the parameter it is dependent on.</span></span> <span data-ttu-id="dfec5-104">カスケード型パラメーターがある場合や、パラメーターの既定値をユーザーに対して示してから他のパラメーターの値をユーザーが選択する場合に、パラメーターの順序は重要です。</span><span class="sxs-lookup"><span data-stu-id="dfec5-104">Parameter order is important when you have cascading parameters, or when you want to show users the default value for one parameter before they choose values for other parameters.</span></span> <span data-ttu-id="dfec5-105">従属レポート パラメーターには、既定値のクエリまたは有効値のクエリのいずれかの、クエリ パラメーターへの参照が含まれます。これは、レポート データ ペインのパラメーター リストでその後にあるレポート パラメーターを参照します。</span><span class="sxs-lookup"><span data-stu-id="dfec5-105">A dependent report parameter contains a reference, in either its default values query or valid values query, to a query parameter that points to a report parameter that is after it in the parameter list in the Report Data pane.</span></span>  
  
 <span data-ttu-id="dfec5-106">レポート ビューアー ツール バーにパラメーターを表示する順序は、レポート データ ペインのパラメーターの順序によって決まります。</span><span class="sxs-lookup"><span data-stu-id="dfec5-106">The order that you see parameters display on the report viewer toolbar is determined by the order of the parameters in the Report Data pane.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-order-of-report-parameters"></a><span data-ttu-id="dfec5-107">レポート パラメーターの表示順を変更するには</span><span class="sxs-lookup"><span data-stu-id="dfec5-107">To change the order of report parameters</span></span>  
  
1.  <span data-ttu-id="dfec5-108">レポート データ ペインで [パラメーター] ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="dfec5-108">In the Report Data pane, expand the Parameters node.</span></span>  
  
2.  <span data-ttu-id="dfec5-109">パラメーターをクリックし、レポートデータペインのツールバーにある上矢印ボタンと下矢印ボタンを使用して、パラメーターを一覧内で上または下に移動します。</span><span class="sxs-lookup"><span data-stu-id="dfec5-109">Click a parameter and use the up and down arrow buttons on the Report Data pane toolbar to move the parameter higher or lower in the list.</span></span> <span data-ttu-id="dfec5-110">次の図は、レポート ビルダーのレポート データ ペインを示しています。</span><span class="sxs-lookup"><span data-stu-id="dfec5-110">The following image shows the Report Data pane in Report Builder.</span></span>  
  
     <span data-ttu-id="dfec5-111">![レポート データ ペイン](../media/reportdatapane.png "レポート データ ペイン")</span><span class="sxs-lookup"><span data-stu-id="dfec5-111">![Report Data Pane](../media/reportdatapane.png "Report Data Pane")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfec5-112">参照</span><span class="sxs-lookup"><span data-stu-id="dfec5-112">See Also</span></span>  
 <span data-ttu-id="dfec5-113">[レポートパラメーター &#40;レポートビルダーとレポートデザイナー&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="dfec5-113">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="dfec5-114">[ダイアログボックス、ペイン、およびウィザードのヘルプのレポートビルダー](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="dfec5-114">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="dfec5-115">[カスケード型パラメーターをレポートに追加する &#40;レポートビルダーと SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dfec5-115">[Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="dfec5-116">[チュートリアル: レポートへのパラメーターの追加 &#40;レポートビルダー&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="dfec5-116">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 <span data-ttu-id="dfec5-117">[データセットフィルター、データ領域フィルター、およびグループフィルターを追加 &#40;レポートビルダーと SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="dfec5-117">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 [<span data-ttu-id="dfec5-118">Parameters コレクションの参照 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="dfec5-118">Parameters Collection References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-parameters-collection-references-report-builder.md)  
  
  
