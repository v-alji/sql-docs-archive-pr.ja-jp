---
title: グラフでのグループの追加または削除 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0445b0ac-acae-4462-80fb-fe9735ac66db
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2ac558ccbd8855018877228b2b38debf769f1573
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739343"
---
# <a name="add-or-delete-a-group-in-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="da18a-102">グラフでのグループの追加または削除 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="da18a-102">Add or Delete a Group in a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="da18a-103">グラフデータ領域をクリックすると、**グラフデータ**ペインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="da18a-103">Click in the chart data region to display the **Chart Data** pane.</span></span> <span data-ttu-id="da18a-104">データセット フィールドを **[カテゴリ グループ]** 領域と **[系列グループ]** 領域にドラッグすると、グループが作成されます。</span><span class="sxs-lookup"><span data-stu-id="da18a-104">Create groups by dragging dataset fields to the **Category Groups** and **Series Groups** areas.</span></span> <span data-ttu-id="da18a-105">入れ子になったグループを追加するには、複数のフィールドを領域に追加します。</span><span class="sxs-lookup"><span data-stu-id="da18a-105">To add nested groups, add multiple fields to the area.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-parent-or-child-group-to-a-chart"></a><span data-ttu-id="da18a-106">親グループまたは子グループをグラフに追加するには</span><span class="sxs-lookup"><span data-stu-id="da18a-106">To add a parent or child group to a chart</span></span>  
  
1.  <span data-ttu-id="da18a-107">レポート デザイン画面で、グラフの任意の場所をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="da18a-107">On the report design surface, click anywhere in the chart to select it.</span></span> <span data-ttu-id="da18a-108">**グラフ データ** ペインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="da18a-108">The **Chart Data** pane appears.</span></span>  
  
2.  <span data-ttu-id="da18a-109">フィールドを、 **[レポート データ]** ウィンドウから **[カテゴリ グループ]** 領域または **[系列グループ]** 領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="da18a-109">Drag a field from the **Report Data** window to the **Category Groups** or **Series Groups** area.</span></span> <span data-ttu-id="da18a-110">親グループを追加するには、既存のグループの前にカーソルを移動します。</span><span class="sxs-lookup"><span data-stu-id="da18a-110">To add a parent group, position the cursor in front of an existing group.</span></span> <span data-ttu-id="da18a-111">子グループを追加するには、既存のグループを後にカーソルを移動します。</span><span class="sxs-lookup"><span data-stu-id="da18a-111">To add a child group, position the cursor after an existing group.</span></span>  
  
### <a name="to-edit-a-category-group-on-a-chart"></a><span data-ttu-id="da18a-112">グラフのカテゴリ グループを編集するには</span><span class="sxs-lookup"><span data-stu-id="da18a-112">To edit a category group on a chart</span></span>  
  
1.  <span data-ttu-id="da18a-113">レポート デザイン画面で、グラフの任意の場所をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="da18a-113">On the report design surface, click anywhere in the chart to select it.</span></span> <span data-ttu-id="da18a-114">**グラフ データ** ペインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="da18a-114">The **Chart Data** pane appears.</span></span>  
  
2.  <span data-ttu-id="da18a-115">**[カテゴリ グループ]** 領域内のグループを右クリックして、 **[カテゴリ グループのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="da18a-115">Right-click the group in the **Category Groups** area, and then click **Category Group Properties**.</span></span>  
  
3.  <span data-ttu-id="da18a-116">グループ式、フィルター、並べ替え式、およびグループ変数を追加または削除します。</span><span class="sxs-lookup"><span data-stu-id="da18a-116">Add or remove group expressions, filters, sort expressions, and group variables.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-a-series-group-on-a-chart"></a><span data-ttu-id="da18a-117">グラフの系列グループを編集するには</span><span class="sxs-lookup"><span data-stu-id="da18a-117">To edit a series group on a chart</span></span>  
  
1.  <span data-ttu-id="da18a-118">レポート デザイン画面で、グラフの任意の場所をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="da18a-118">On the report design surface, click anywhere in the chart to select it.</span></span> <span data-ttu-id="da18a-119">**グラフ データ** ペインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="da18a-119">The **Chart Data** pane appears.</span></span>  
  
2.  <span data-ttu-id="da18a-120">**[系列グループ]** 領域内のグループを右クリックし、 **[系列グループのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="da18a-120">Right-click the group in the **Series Groups** area, and then click **Series Group Properties**.</span></span>  
  
3.  <span data-ttu-id="da18a-121">グループ式、フィルター、並べ替え式、およびグループ変数を追加または削除します。</span><span class="sxs-lookup"><span data-stu-id="da18a-121">Add or remove group expressions, filters, sort expressions, and group variables.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-group-from-a-chart"></a><span data-ttu-id="da18a-122">グラフからグループを削除するには</span><span class="sxs-lookup"><span data-stu-id="da18a-122">To delete a group from a chart</span></span>  
  
1.  <span data-ttu-id="da18a-123">レポート デザイン画面で、グラフの任意の場所をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="da18a-123">On the report design surface, click anywhere in the chart to select it.</span></span> <span data-ttu-id="da18a-124">**グラフ データ** ペインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="da18a-124">The **Chart Data** pane appears.</span></span>  
  
2.  <span data-ttu-id="da18a-125">**[カテゴリ グループ]** 領域または **[系列グループ]** 領域内のグループを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="da18a-125">Right-click the group in the **Category Groups** or **Series Groups** area, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da18a-126">参照</span><span class="sxs-lookup"><span data-stu-id="da18a-126">See Also</span></span>  
 [<span data-ttu-id="da18a-127">グラフ &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="da18a-127">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
