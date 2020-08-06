---
title: '[カレンダーの選択] (ディメンションウィザード)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.serverSpecialCalendars.f1
ms.assetid: 6e28a020-2586-4b13-9333-b499fb1b33af
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2048ee20dd91c942f01982d02f3265a6bad670dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641885"
---
# <a name="select-calendars-dimension-wizard"></a><span data-ttu-id="7924c-102">[カレンダーの選択] (ディメンション ウィザード)</span><span class="sxs-lookup"><span data-stu-id="7924c-102">Select Calendars (Dimension Wizard)</span></span>
  <span data-ttu-id="7924c-103">**[カレンダーの選択]** ページを使用すると、会計カレンダー、レポート カレンダー、製造カレンダー、ISO (国際標準化機構) 8601 カレンダーを表す階層を作成し、時間ディメンションに追加できます。</span><span class="sxs-lookup"><span data-stu-id="7924c-103">Use the **Select Calendars** page to create additional hierarchies representing fiscal, reporting, manufacturing, or International Standards Organization (ISO) 8601 calendars for the time dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7924c-104">このページは、 **[ディメンションの種類の選択]** ページで **[サーバー時間ディメンション]** を選択したか、 **[構築方法の選択]** ページで **[データ ソースを使用せずにディメンションを構築する]** を選択し、 **[ディメンションの種類の選択]** ページで **[時間ディメンション]** を選択した場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="7924c-104">This page will appear only if you have selected **Server time dimension** on the **Select the Dimension Type** page, or if you selected **Build the dimension without using a data source** on the **Dimension Definition** page and selected **Time dimension** on the **Select the Dimension Type** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7924c-105">Options</span><span class="sxs-lookup"><span data-stu-id="7924c-105">Options</span></span>  
 <span data-ttu-id="7924c-106">**[会計カレンダー]**</span><span class="sxs-lookup"><span data-stu-id="7924c-106">**Fiscal calendar**</span></span>  
 <span data-ttu-id="7924c-107">会計カレンダーに基づいて時間の階層を作成する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="7924c-107">Select to create a time hierarchy based on a fiscal calendar.</span></span>  
  
 <span data-ttu-id="7924c-108">**[開始する月日]**</span><span class="sxs-lookup"><span data-stu-id="7924c-108">**Start day and month**</span></span>  
 <span data-ttu-id="7924c-109">会計カレンダーが開始される月と日を選択します。</span><span class="sxs-lookup"><span data-stu-id="7924c-109">Select the day and month on which the fiscal calendar begins.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7924c-110">このオプションは、 **[会計カレンダー]** が選択されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="7924c-110">This option is available only when **Fiscal calendar** is selected.</span></span>  
  
 <span data-ttu-id="7924c-111">**[会計カレンダーの名前付け規則]**</span><span class="sxs-lookup"><span data-stu-id="7924c-111">**Fiscal calendar naming convention**</span></span>  
 <span data-ttu-id="7924c-112">会計カレンダーで使用される名前付け規則を選択します。</span><span class="sxs-lookup"><span data-stu-id="7924c-112">Select the naming convention used by the fiscal calendar.</span></span> <span data-ttu-id="7924c-113">**[暦年の名前]** または **[暦年の名前に 1 を加算]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7924c-113">Select either **Calendar year name** or **Calendar year name +1**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7924c-114">このオプションは、 **[会計カレンダー]** が選択されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="7924c-114">This option is available only when **Fiscal calendar** is selected.</span></span>  
  
 <span data-ttu-id="7924c-115">**[レポート (またはマーケティング) カレンダー]**</span><span class="sxs-lookup"><span data-stu-id="7924c-115">**Reporting (or marketing) calendar**</span></span>  
 <span data-ttu-id="7924c-116">レポート カレンダーに基づいて時間の階層を作成する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="7924c-116">Select to create a time hierarchy based on a reporting calendar.</span></span>  
  
 <span data-ttu-id="7924c-117">**[開始する月と週]**</span><span class="sxs-lookup"><span data-stu-id="7924c-117">**Start week and month**</span></span>  
 <span data-ttu-id="7924c-118">レポート カレンダーが開始される月と週を選択します。</span><span class="sxs-lookup"><span data-stu-id="7924c-118">Select the week and month on which the reporting calendar begins.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7924c-119">このオプションは、 **[レポート (またはマーケティング) カレンダー]** が選択されている場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="7924c-119">This option is available when **Reporting (or marketing) calendar** is selected.</span></span>  
  
 <span data-ttu-id="7924c-120">**[月単位の週のパターン]**</span><span class="sxs-lookup"><span data-stu-id="7924c-120">**Week by month pattern**</span></span>  
 <span data-ttu-id="7924c-121">レポート カレンダーで使用される月単位の週のパターンを選択します。</span><span class="sxs-lookup"><span data-stu-id="7924c-121">Select the week by month pattern used by the reporting calendar.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7924c-122">このオプションは、 **[レポート (またはマーケティング) カレンダー]** が選択されている場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="7924c-122">This option is available when **Reporting (or marketing) calendar** is selected.</span></span>  
  
 <span data-ttu-id="7924c-123">次の表に、[月単位の週のパターン] に指定できるオプションを示します。</span><span class="sxs-lookup"><span data-stu-id="7924c-123">The following table lists the options available for the week by month pattern.</span></span>  
  
|<span data-ttu-id="7924c-124">値</span><span class="sxs-lookup"><span data-stu-id="7924c-124">Value</span></span>|<span data-ttu-id="7924c-125">説明</span><span class="sxs-lookup"><span data-stu-id="7924c-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7924c-126">**[週 445]**</span><span class="sxs-lookup"><span data-stu-id="7924c-126">**Week 445**</span></span>|<span data-ttu-id="7924c-127">四半期の 1 番目の月が 4 週、四半期の 2 番目の月が 4 週、四半期の 3 番目の月が 5 週になります。</span><span class="sxs-lookup"><span data-stu-id="7924c-127">The first month in the quarter has 4 weeks, the second month in the quarter has 4 weeks, and the third month in the quarter has 5 weeks.</span></span>|  
|<span data-ttu-id="7924c-128">**[週 454]**</span><span class="sxs-lookup"><span data-stu-id="7924c-128">**Week 454**</span></span>|<span data-ttu-id="7924c-129">四半期の 1 番目の月が 4 週、四半期の 2 番目の月が 5 週、四半期の 3 番目の月が 4 週になります。</span><span class="sxs-lookup"><span data-stu-id="7924c-129">The first month in the quarter has 4 weeks, the second month in the quarter has 5 weeks, and the third month in the quarter has 4 weeks.</span></span>|  
|<span data-ttu-id="7924c-130">**[週 544]**</span><span class="sxs-lookup"><span data-stu-id="7924c-130">**Week 544**</span></span>|<span data-ttu-id="7924c-131">四半期の 1 番目の月が 5 週、四半期の 2 番目の月が 4 週、四半期の 3 番目の月が 4 週になります。</span><span class="sxs-lookup"><span data-stu-id="7924c-131">The first month in the quarter has 5 weeks, the second month in the quarter has 4 weeks, and the third month in the quarter has 4 weeks.</span></span>|  
  
 <span data-ttu-id="7924c-132">**[製造カレンダー]**</span><span class="sxs-lookup"><span data-stu-id="7924c-132">**Manufacturing calendar**</span></span>  
 <span data-ttu-id="7924c-133">製造カレンダーに基づいて時間の階層を作成する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="7924c-133">Select to create a time hierarchy based on a manufacturing calendar.</span></span>  
  
 <span data-ttu-id="7924c-134">**[開始する月と週]**</span><span class="sxs-lookup"><span data-stu-id="7924c-134">**Start week and month**</span></span>  
 <span data-ttu-id="7924c-135">製造カレンダーが開始される月と週を選択します。</span><span class="sxs-lookup"><span data-stu-id="7924c-135">Select the week and month on which the manufacturing calendar begins.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7924c-136">このオプションは、 **[製造カレンダー]** が選択されている場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="7924c-136">This option is available when **Manufacturing calendar** is selected.</span></span>  
  
 <span data-ttu-id="7924c-137">**[追加期間を含む四半期]**</span><span class="sxs-lookup"><span data-stu-id="7924c-137">**Quarter with extra periods**</span></span>  
 <span data-ttu-id="7924c-138">追加期間を含む四半期を選択するか、入力します。</span><span class="sxs-lookup"><span data-stu-id="7924c-138">Select or type the quarter that will contain the extra periods.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7924c-139">このオプションは、 **[製造カレンダー]** が選択されている場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="7924c-139">This option is available when **Manufacturing calendar** is selected.</span></span>  
  
 <span data-ttu-id="7924c-140">**[ISO 8601 カレンダー]**</span><span class="sxs-lookup"><span data-stu-id="7924c-140">**ISO 8601 calendar**</span></span>  
 <span data-ttu-id="7924c-141">ISO 8601 カレンダーに基づく階層を作成する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="7924c-141">Select to create a hierarchy based on the ISO 8601 calendar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7924c-142">参照</span><span class="sxs-lookup"><span data-stu-id="7924c-142">See Also</span></span>  
 <span data-ttu-id="7924c-143">[ディメンションウィザードの F1 ヘルプ](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="7924c-143">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="7924c-144">[ディメンション &#40;Analysis Services-多次元データ&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7924c-144">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="7924c-145">多次元モデル内のディメンション</span><span class="sxs-lookup"><span data-stu-id="7924c-145">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
