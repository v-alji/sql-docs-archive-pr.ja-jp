---
title: クエリ条件の指定 (使用法に基づく最適化ウィザード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.usagebasedoptimizationwizard.specifyquerycriteria.f1
ms.assetid: 3193adc2-af9f-4234-a4cc-dea0c280a724
author: minewiskan
ms.author: owend
ms.openlocfilehash: f3b93034a089ff3121155e35de4cec96846824a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634076"
---
# <a name="specify-query-criteria-usage-based-optimization-wizard"></a><span data-ttu-id="c83db-102">[クエリ条件の指定] (使用法に基づく最適化ウィザード)</span><span class="sxs-lookup"><span data-stu-id="c83db-102">Specify Query Criteria (Usage-Based Optimization Wizard)</span></span>
  <span data-ttu-id="c83db-103">**[クエリ条件の指定]** ページを使用すると、最適化するクエリを特定するために 1 つ以上のフィルター オプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="c83db-103">Use the **Specify Query Criteria** page to choose one or more filter options in order to identify queries to optimize.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c83db-104">このページは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] がクエリ ログに接続できない場合は無効です。</span><span class="sxs-lookup"><span data-stu-id="c83db-104">This page is disabled if [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cannot connect to the query log.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c83db-105">Options</span><span class="sxs-lookup"><span data-stu-id="c83db-105">Options</span></span>  
 <span data-ttu-id="c83db-106">**[クエリ ログの統計]**</span><span class="sxs-lookup"><span data-stu-id="c83db-106">**Query log statistics**</span></span>  
 <span data-ttu-id="c83db-107">選択されたパーティションのクエリ ログに格納された、クエリに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="c83db-107">Displays information about the queries stored in the query log for the selected partitions.</span></span> <span data-ttu-id="c83db-108">以下の項目が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c83db-108">The following items are displayed:</span></span>  
  
|<span data-ttu-id="c83db-109">期間</span><span class="sxs-lookup"><span data-stu-id="c83db-109">Term</span></span>|<span data-ttu-id="c83db-110">定義</span><span class="sxs-lookup"><span data-stu-id="c83db-110">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="c83db-111">**[クエリの合計数]**</span><span class="sxs-lookup"><span data-stu-id="c83db-111">**Total queries**</span></span>|<span data-ttu-id="c83db-112">選択されたパーティションのクエリ ログに格納された、クエリの合計数を表示します。</span><span class="sxs-lookup"><span data-stu-id="c83db-112">Displays the total number of queries stored in the query log for the selected partitions.</span></span>|  
|<span data-ttu-id="c83db-113">**個別のクエリ**</span><span class="sxs-lookup"><span data-stu-id="c83db-113">**Distinct queries**</span></span>|<span data-ttu-id="c83db-114">選択されたパーティションのクエリ ログに格納された、異なるクエリの数を表示します。</span><span class="sxs-lookup"><span data-stu-id="c83db-114">Displays the number of distinct queries stored in the query log for the selected partitions.</span></span>|  
|<span data-ttu-id="c83db-115">**[個別のユーザー]**</span><span class="sxs-lookup"><span data-stu-id="c83db-115">**Distinct users**</span></span>|<span data-ttu-id="c83db-116">選択されたパーティションのクエリ ログに格納された、クエリに関連付けられた異なるユーザーの数を表示します。</span><span class="sxs-lookup"><span data-stu-id="c83db-116">Displays the total number of distinct users associated with queries stored in the query log for the selected partitions.</span></span>|  
|<span data-ttu-id="c83db-117">**平均応答時間**</span><span class="sxs-lookup"><span data-stu-id="c83db-117">**Average response time**</span></span>|<span data-ttu-id="c83db-118">選択されたパーティションのクエリ ログに格納された、クエリの平均応答時間を表示します。</span><span class="sxs-lookup"><span data-stu-id="c83db-118">Displays the average response time for queries stored in the query log for the selected partitions.</span></span>|  
  
 <span data-ttu-id="c83db-119">**[開始日]**</span><span class="sxs-lookup"><span data-stu-id="c83db-119">**Beginning date**</span></span>  
 <span data-ttu-id="c83db-120">開始する日および時刻に基づいてクエリ ログのクエリをフィルターします。</span><span class="sxs-lookup"><span data-stu-id="c83db-120">Filters queries in the query log based on a starting date and time.</span></span> <span data-ttu-id="c83db-121">日付をドロップダウン リストから選択するか入力します。</span><span class="sxs-lookup"><span data-stu-id="c83db-121">Choose or type a date in the dropdown list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c83db-122">**[終了日]** が選択されていない場合、このオプションで指定した日付および時刻以降のクエリ ログ内のすべてのクエリが対象になります。</span><span class="sxs-lookup"><span data-stu-id="c83db-122">If **Ending date** is not selected, all queries in the query log on or after the date and time specified for this option are considered.</span></span>  
  
 <span data-ttu-id="c83db-123">**[終了日]**</span><span class="sxs-lookup"><span data-stu-id="c83db-123">**Ending date**</span></span>  
 <span data-ttu-id="c83db-124">終了する日および時刻に基づいてクエリ ログのクエリをフィルターします。</span><span class="sxs-lookup"><span data-stu-id="c83db-124">Filters queries in the query log based on an ending date and time.</span></span> <span data-ttu-id="c83db-125">日付をドロップダウン リストから選択するか入力します。</span><span class="sxs-lookup"><span data-stu-id="c83db-125">Choose or type a date in the dropdown list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c83db-126">**[開始日]** が選択されていない場合、このオプションで指定した日付および時刻以前のクエリ ログ内のすべてのクエリが対象になります。</span><span class="sxs-lookup"><span data-stu-id="c83db-126">If **Beginning date** is not selected, all queries in the query log on or before the date and time specified for this option are considered.</span></span>  
  
 <span data-ttu-id="c83db-127">**ユーザー**</span><span class="sxs-lookup"><span data-stu-id="c83db-127">**Users**</span></span>  
 <span data-ttu-id="c83db-128">指定されたユーザーのセットに基づいてクエリ ログのクエリをフィルターします。</span><span class="sxs-lookup"><span data-stu-id="c83db-128">Filters queries in the query log based on a specified set of users.</span></span> <span data-ttu-id="c83db-129">**[...]** ボタンをクリックして **[ユーザーの選択]** ダイアログ ボックスを開き、クエリをフィルターする対象ユーザーを選択します。</span><span class="sxs-lookup"><span data-stu-id="c83db-129">Click the ellipsis (**...**) button to display the **User Selection** dialog box and choose users on which to filter queries.</span></span> <span data-ttu-id="c83db-130">**[ユーザーの選択]** ダイアログ ボックスの詳細については、[「[ユーザーの選択] ダイアログ ボックス (Analysis Services - 多次元データ)」](user-selection-dialog-box-analysis-services-multidimensional-data.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c83db-130">For more information about the **User Selection** dialog box, see [User Selection Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](user-selection-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="c83db-131">**[最も使用されるクエリ]**</span><span class="sxs-lookup"><span data-stu-id="c83db-131">**Most frequent queries**</span></span>  
 <span data-ttu-id="c83db-132">選択されたパーティションに対して、最も実行頻度の高いクエリの最大比率に基づいて、クエリ ログのクエリをフィルターします。</span><span class="sxs-lookup"><span data-stu-id="c83db-132">Filters queries in the query log based on the topmost percentage of the distinct queries most often run for the selected partitions.</span></span> <span data-ttu-id="c83db-133">テキスト ボックスで比率の値を選択するか、値を入力します。</span><span class="sxs-lookup"><span data-stu-id="c83db-133">Choose or type a percent value in the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c83db-134">参照</span><span class="sxs-lookup"><span data-stu-id="c83db-134">See Also</span></span>  
 <span data-ttu-id="c83db-135">[使用法に基づく最適化ウィザードの F1 ヘルプ](usage-based-optimization-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="c83db-135">[Usage-Based Optimization Wizard F1 Help](usage-based-optimization-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="c83db-136">Analysis Services のウィザード &#40;多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="c83db-136">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
