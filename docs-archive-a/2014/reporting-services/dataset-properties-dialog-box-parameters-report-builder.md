---
title: '[パラメーター] ([データセットのプロパティ] ダイアログボックス) (レポートビルダー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10023"
ms.assetid: 3a0672ad-c969-455b-b952-585164ce1dda
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ef038e7cbf113556b11af9a0e6c59aa190b2400b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645405"
---
# <a name="dataset-properties-dialog-box-parameters-report-builder"></a><span data-ttu-id="944f3-102">[パラメーター] ([データセットのプロパティ] ダイアログ ボックス) (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="944f3-102">Dataset Properties Dialog Box, Parameters (Report Builder)</span></span>
  <span data-ttu-id="944f3-103">[**データセットのプロパティ**] ダイアログボックスの [**パラメーター** ] を選択すると、クエリパラメーターの追加、変更、および削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="944f3-103">Select **Parameters** on the **Dataset Properties** dialog box to add, change, and delete query parameters.</span></span>  
  
 <span data-ttu-id="944f3-104">埋め込みデータセットの場合、オプションはレポート定義のデータセットに適用されます。</span><span class="sxs-lookup"><span data-stu-id="944f3-104">For an embedded dataset, options apply to the dataset in the report definition.</span></span>  
  
 <span data-ttu-id="944f3-105">共有データセットの場合、オプションはレポート サーバーの共有データセット定義に適用されます。</span><span class="sxs-lookup"><span data-stu-id="944f3-105">For a shared dataset, options apply to the shared dataset definition on the report server.</span></span>  
  
 <span data-ttu-id="944f3-106">詳細については、「[埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](report-data/embedded-and-shared-datasets-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="944f3-106">For more information, see [Embedded and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/embedded-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="944f3-107">Options</span><span class="sxs-lookup"><span data-stu-id="944f3-107">Options</span></span>  
 <span data-ttu-id="944f3-108">**追加**</span><span class="sxs-lookup"><span data-stu-id="944f3-108">**Add**</span></span>  
 <span data-ttu-id="944f3-109">一覧に新しいパラメーターを追加します。</span><span class="sxs-lookup"><span data-stu-id="944f3-109">Add a new parameter to the list.</span></span>  
  
 <span data-ttu-id="944f3-110">**削除**</span><span class="sxs-lookup"><span data-stu-id="944f3-110">**Delete**</span></span>  
 <span data-ttu-id="944f3-111">選択したパラメーターを一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="944f3-111">Remove the selected parameter from the list.</span></span>  
  
 <span data-ttu-id="944f3-112">**上矢印**</span><span class="sxs-lookup"><span data-stu-id="944f3-112">**Up arrow**</span></span>  
 <span data-ttu-id="944f3-113">選択したパラメーターを一覧内で上に移動します。</span><span class="sxs-lookup"><span data-stu-id="944f3-113">Move the selected parameter up in the list.</span></span>  
  
 <span data-ttu-id="944f3-114">**下方向キー**</span><span class="sxs-lookup"><span data-stu-id="944f3-114">**Down arrow**</span></span>  
 <span data-ttu-id="944f3-115">選択したパラメーターを一覧内で下に移動します。</span><span class="sxs-lookup"><span data-stu-id="944f3-115">Move the selected parameter down in the list.</span></span>  
  
 <span data-ttu-id="944f3-116">**パラメーター名**</span><span class="sxs-lookup"><span data-stu-id="944f3-116">**Parameter name**</span></span>  
 <span data-ttu-id="944f3-117">**[データセットのプロパティ]** ダイアログ ボックスの **[クエリ]** タブでデータセットに追加したクエリ パラメーターの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="944f3-117">Type the name of a query parameter that you added to the dataset on the **Query** tab of the **Dataset Properties** dialog box.</span></span>  
  
 <span data-ttu-id="944f3-118">**パラメーター値**</span><span class="sxs-lookup"><span data-stu-id="944f3-118">**Parameter value**</span></span>  
 <span data-ttu-id="944f3-119">埋め込みデータセットにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="944f3-119">For embedded datasets only.</span></span>  
  
 <span data-ttu-id="944f3-120">クエリ パラメーターの値を入力します。</span><span class="sxs-lookup"><span data-stu-id="944f3-120">Enter a value for the query parameter.</span></span> <span data-ttu-id="944f3-121">この値には、静的な値、またはレポート内のオブジェクトを参照するがレポート アイテムやフィールドは参照できない式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="944f3-121">This can be a static value or an expression that refers to an object within the report, but it cannot refer to any report items or fields.</span></span> <span data-ttu-id="944f3-122">既定では、 **[値]** に、レポート パラメーターを参照する式が設定されています。</span><span class="sxs-lookup"><span data-stu-id="944f3-122">By default, **Value** contains an expression that points to a report parameter.</span></span>  
  
 <span data-ttu-id="944f3-123">**既定値**</span><span class="sxs-lookup"><span data-stu-id="944f3-123">**Default value**</span></span>  
 <span data-ttu-id="944f3-124">共有データセットにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="944f3-124">For shared datasets only.</span></span>  
  
 <span data-ttu-id="944f3-125">既定値を指定する場合に、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="944f3-125">Select the check box to specify a default value.</span></span>  
  
 <span data-ttu-id="944f3-126">既定値を入力します。</span><span class="sxs-lookup"><span data-stu-id="944f3-126">Enter a default value.</span></span> <span data-ttu-id="944f3-127">この値には、静的な値か、レポート内のオブジェクトを参照する式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="944f3-127">This can be a static value or an expression that refers to an object within the report.</span></span> <span data-ttu-id="944f3-128">式は、レポート アイテム、レポート パラメーター、またはフィールドを参照できません。</span><span class="sxs-lookup"><span data-stu-id="944f3-128">The expression cannot refer to report items, report parameters, or fields.</span></span>  
  
 <span data-ttu-id="944f3-129">空白を指定するには、テキスト ボックスを空のままにします。</span><span class="sxs-lookup"><span data-stu-id="944f3-129">To specify a blank, leave the text box empty.</span></span>  
  
 <span data-ttu-id="944f3-130">NULL を指定するには、NULL 許容オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="944f3-130">To specify a null, select the Nullable option.</span></span>  
  
 <span data-ttu-id="944f3-131">**読み取り専用**</span><span class="sxs-lookup"><span data-stu-id="944f3-131">**Read Only**</span></span>  
 <span data-ttu-id="944f3-132">共有データセットにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="944f3-132">For shared datasets only.</span></span>  
  
 <span data-ttu-id="944f3-133">共有データセット定義でこのパラメーターを読み取り専用に指定する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="944f3-133">Select this option to mark this parameter read only in the shared dataset definition.</span></span> <span data-ttu-id="944f3-134">共有データセットがレポートに追加されると、パラメーターはプロパティに表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="944f3-134">When the shared dataset is added to a report, the parameter does not appear in the properties.</span></span> <span data-ttu-id="944f3-135">レポート サーバー上で共有データセットがキャッシュされると、値は変更できなくなります。</span><span class="sxs-lookup"><span data-stu-id="944f3-135">When the shared dataset is cached on the report server, the value cannot be changed.</span></span>  
  
 <span data-ttu-id="944f3-136">**NULL 値の使用**</span><span class="sxs-lookup"><span data-stu-id="944f3-136">**Nullable**</span></span>  
 <span data-ttu-id="944f3-137">共有データセットにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="944f3-137">For shared datasets only.</span></span>  
  
 <span data-ttu-id="944f3-138">NULL 値を許容する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="944f3-138">Select this option to allow a null value.</span></span>  
  
 <span data-ttu-id="944f3-139">**[クエリから省略]**</span><span class="sxs-lookup"><span data-stu-id="944f3-139">**Omit From Query**</span></span>  
 <span data-ttu-id="944f3-140">共有データセットにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="944f3-140">For shared datasets only.</span></span>  
  
 <span data-ttu-id="944f3-141">レポート パラメーターの参照が共有データセット フィルターの式に含まれ、クエリに含まれていない場合に、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="944f3-141">Select this option when a reference to a report parameter is in an expression in the shared dataset filter and not in the query.</span></span> <span data-ttu-id="944f3-142">このオプションを選択した場合、クエリの実行時にこのパラメーターの既定値を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="944f3-142">When you select this option, you do not need to specify a default value for this parameter when the query runs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="944f3-143">参照</span><span class="sxs-lookup"><span data-stu-id="944f3-143">See Also</span></span>  
 <span data-ttu-id="944f3-144">[ダイアログボックス、ペイン、およびウィザードのヘルプのレポートビルダー](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="944f3-144">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="944f3-145">[[クエリ &#40;レポートビルダー] ([データセットのプロパティ] ダイアログボックス)&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="944f3-145">[Dataset Properties Dialog Box, Query &#40;Report Builder&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md) </span></span>  
 <span data-ttu-id="944f3-146">[式 &#40;レポート ビルダーおよび SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="944f3-146">[Expressions &#40;Report Builder and SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="944f3-147">[チュートリアル: レポートへのパラメーターの追加 &#40;レポートビルダー&#41;](tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="944f3-147">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 <span data-ttu-id="944f3-148">[レポートパラメーター &#40;レポートビルダーとレポートデザイナー&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="944f3-148">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="944f3-149">[レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="944f3-149">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="944f3-150">[クエリデザイナー &#40;レポートビルダー&#41;](../../2014/reporting-services/query-designers-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="944f3-150">[Query Designers &#40;Report Builder&#41;](../../2014/reporting-services/query-designers-report-builder.md) </span></span>  
 <span data-ttu-id="944f3-151">[レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="944f3-151">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="944f3-152">共有データセットまたは埋め込みデータセットの作成 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="944f3-152">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
  
