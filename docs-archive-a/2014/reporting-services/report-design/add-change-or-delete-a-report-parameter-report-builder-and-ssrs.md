---
title: レポート パラメーターの追加、変更、または削除 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d44a8e0a-10cf-4502-9391-09743ffc9bad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 231cd51d7ed0a481f004b39a2e8819df3fc33748
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640730"
---
# <a name="add-change-or-delete-a-report-parameter-report-builder-and-ssrs"></a><span data-ttu-id="e327e-102">レポート パラメーターの追加、変更、または削除 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="e327e-102">Add, Change, or Delete a Report Parameter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e327e-103">レポート パラメーターは、レポート データの選択、他のレポートとの関連付け、レポートの表示方法の変更などの用途に使用されます。</span><span class="sxs-lookup"><span data-stu-id="e327e-103">A report parameter provides a way to choose report data, connect related reports together, and vary the report presentation.</span></span> <span data-ttu-id="e327e-104">既定値や使用可能な値のリストを指定できるほか、ユーザーに選択内容を変更させることもできます。</span><span class="sxs-lookup"><span data-stu-id="e327e-104">You can provide a default value and a list of available values, and the user can change the selection.</span></span>  
  
 <span data-ttu-id="e327e-105">レポートをパブリッシュした後、レポート サーバーから、レポート パラメーターの各種プロパティ (既定値や使用可能な値など) を変更できます。</span><span class="sxs-lookup"><span data-stu-id="e327e-105">After you publish a report, you can change the default values, the available values, and other properties for a report parameter on the report server.</span></span> <span data-ttu-id="e327e-106">リンク レポートを作成して、既定のパラメーター値の複数のセットを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e327e-106">You can provide multiple sets of default parameter values by creating linked reports.</span></span> <span data-ttu-id="e327e-107">詳細については、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SQL Server オンライン ブック [にある](https://go.microsoft.com/fwlink/?linkid=120955)のマニュアルの「パブリッシュ済みレポートのパラメーター プロパティの設定」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e327e-107">For more information, see "Setting Parameter Properties for a Published Report" in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=120955).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-or-edit-a-report-parameter"></a><span data-ttu-id="e327e-108">レポート パラメーターを追加または編集するには</span><span class="sxs-lookup"><span data-stu-id="e327e-108">To add or edit a report parameter</span></span>  
  
1.  <span data-ttu-id="e327e-109">**レポート データ** ペインで、 **[パラメーター]** ノードを右クリックし、 **[パラメーターの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e327e-109">In the **Report Data** pane, right-click the **Parameters** node and click **Add Parameter**.</span></span> <span data-ttu-id="e327e-110">**[レポート パラメーターのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e327e-110">The **Report Parameter Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="e327e-111">**[名前]** にパラメーターの名前を入力するか、既定の名前をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="e327e-111">In **Name**, type the name of the parameter or accept the default name.</span></span>  
  
3.  <span data-ttu-id="e327e-112">**[表示名]** に、レポートの実行時にパラメーター テキスト ボックスの隣に表示する文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="e327e-112">In **Prompt**, type the text that appears next to the parameter text box when the user runs the report.</span></span>  
  
4.  <span data-ttu-id="e327e-113">**[データ型]** で、パラメーター値のデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="e327e-113">In **Data type**, select the data type for the parameter value.</span></span>  
  
5.  <span data-ttu-id="e327e-114">空白の値を含めることができる場合は、 **[空白の値を許可]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="e327e-114">If the parameter can contain a blank value, select **Allow blank value**.</span></span>  
  
6.  <span data-ttu-id="e327e-115">パラメーターに NULL 値を含めることができる場合は、 **[NULL 値を許可]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="e327e-115">If the parameter can contain a null value, select **Allow null value**.</span></span>  
  
7.  <span data-ttu-id="e327e-116">パラメーターに複数の値を選択できるようにする場合は、 **[複数の値を許可]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e327e-116">To allow a user to select more than one value for the parameter, select **Allow multiple values**.</span></span>  
  
8.  <span data-ttu-id="e327e-117">表示オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="e327e-117">Set the visibility option.</span></span>  
  
    -   <span data-ttu-id="e327e-118">パラメーターをレポート上部のツール バーに表示する場合は、 **[表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e327e-118">To show the parameter on the toolbar at the top of the report, select **Visible**.</span></span>  
  
    -   <span data-ttu-id="e327e-119">パラメーターがツール バーに表示されないようにする場合は、 **[非表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e327e-119">To hide the parameter so that it does not display on the toolbar, select **Hidden**.</span></span>  
  
    -   <span data-ttu-id="e327e-120">レポートのパブリッシュ後はパラメーターを非表示にし、レポート サーバーで変更できないよう保護する場合は、 **[内部]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e327e-120">To hide the parameter and protect it from being modified on the report server after the report is published, select **Internal**.</span></span> <span data-ttu-id="e327e-121">レポート パラメーターは、レポート定義でのみ参照できます。</span><span class="sxs-lookup"><span data-stu-id="e327e-121">The report parameter can then only be viewed in the report definition.</span></span> <span data-ttu-id="e327e-122">このオプションを選択した場合は、既定値を設定するか、パラメーターで Null 値を許可するように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e327e-122">For this option, you must set a default value or allow the parameter to accept a null value.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-report-parameter"></a><span data-ttu-id="e327e-123">レポート パラメーターを削除するには</span><span class="sxs-lookup"><span data-stu-id="e327e-123">To delete a report parameter</span></span>  
  
1.  <span data-ttu-id="e327e-124">**レポート データ** ペインで **[パラメーター]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="e327e-124">In the **Report Data** pane, expand the **Parameters** node.</span></span>  
  
2.  <span data-ttu-id="e327e-125">レポート パラメーターを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e327e-125">Right-click the report parameter and click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e327e-126">参照</span><span class="sxs-lookup"><span data-stu-id="e327e-126">See Also</span></span>  
 <span data-ttu-id="e327e-127">[レポートパラメーターに使用できる値の追加、変更、または削除 &#40;レポートビルダーと SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md) </span><span class="sxs-lookup"><span data-stu-id="e327e-127">[Add, Change, or Delete Available Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md) </span></span>  
 <span data-ttu-id="e327e-128">[レポートパラメーターの既定値の追加、変更、または削除 &#40;レポートビルダーと SSRS&#41;](add-change-or-delete-default-values-for-a-report-parameter.md) </span><span class="sxs-lookup"><span data-stu-id="e327e-128">[Add, Change, or Delete Default Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-default-values-for-a-report-parameter.md) </span></span>  
 <span data-ttu-id="e327e-129">[レポートパラメーター &#40;レポートビルダーと SSRS の順序を変更&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e327e-129">[Change the Order of a Report Parameter &#40;Report Builder and SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e327e-130">[レポートパラメーター &#40;レポートビルダーとレポートデザイナー&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="e327e-130">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="e327e-131">[ダイアログボックス、ペイン、およびウィザードのヘルプのレポートビルダー](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="e327e-131">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="e327e-132">[カスケード型パラメーターをレポートに追加する &#40;レポートビルダーと SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e327e-132">[Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e327e-133">[チュートリアル: レポートへのパラメーターの追加 &#40;レポートビルダー&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="e327e-133">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 <span data-ttu-id="e327e-134">[チュートリアル &#40;レポートビルダー&#41;](../report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="e327e-134">[Tutorials &#40;Report Builder&#41;](../report-builder-tutorials.md) </span></span>  
 <span data-ttu-id="e327e-135">[データセットフィルター、データ領域フィルター、およびグループフィルターを追加 &#40;レポートビルダーと SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="e327e-135">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="e327e-136">[Parameters コレクションの参照 &#40;レポートビルダーと SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="e327e-136">[Parameters Collection References &#40;Report Builder and SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span></span>  
 [<span data-ttu-id="e327e-137">複数の値を持つパラメーターのレポートへの追加</span><span class="sxs-lookup"><span data-stu-id="e327e-137">Add a multi-value parameter to a Report</span></span>](add-a-multi-value-parameter-to-a-report.md)  
  
  
