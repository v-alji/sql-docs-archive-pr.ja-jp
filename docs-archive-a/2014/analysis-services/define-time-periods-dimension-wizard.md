---
title: 時間間隔の定義 (ディメンションウィザード)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.timefrequency.f1
ms.assetid: 6bda6b7e-d306-4e68-9acb-84de8f44d1b4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 88b69eaa265b7a98f7d32063b602897d02016fa8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644692"
---
# <a name="define-time-periods-dimension-wizard"></a><span data-ttu-id="3bbc9-102">[時間間隔の定義] (ディメンション ウィザード)</span><span class="sxs-lookup"><span data-stu-id="3bbc9-102">Define Time Periods (Dimension Wizard)</span></span>
  <span data-ttu-id="3bbc9-103">**[時間間隔の定義]** ページを使用すると、時間ディメンションまたはサーバー時間ディメンションに含める暦年情報と時間頻度を定義できます。</span><span class="sxs-lookup"><span data-stu-id="3bbc9-103">Use the **Define Time Periods** page to define the calendar year information and time frequencies to include in the time dimension or server time dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3bbc9-104"> このページは、 **[ディメンションの種類の選択]** ページで **[サーバー時間ディメンション]** を選択したか、 **[構築方法の選択]** ページで **[データ ソースを使用せずにディメンションを構築する]** を選択し、 **[ディメンションの種類の選択]** ページで **[時間ディメンション]** を選択した場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="3bbc9-104">This page will appear only if you have selected **Server time dimension** on the **Select the Dimension Type** page, or if you selected **Build the dimension without using a data source** on the **Select Build Method** page and selected **Time dimension** on the **Select the Dimension Type** page.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3bbc9-105">このページでは、時間ディメンションの暦年を定義します。</span><span class="sxs-lookup"><span data-stu-id="3bbc9-105">This page is for defining the calendar year of a time dimension.</span></span> <span data-ttu-id="3bbc9-106">時間ディメンションに会計年度、製造年度、報告年度、ISO (国際標準化機構) 8601 年度を定義するには、 **[カレンダーの選択]** ページを使用してください。</span><span class="sxs-lookup"><span data-stu-id="3bbc9-106">To define a fiscal, manufacturing, reporting, or International Standards Organization (ISO) 8601 year for the time dimension, use the **Select Calendars** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3bbc9-107">Options</span><span class="sxs-lookup"><span data-stu-id="3bbc9-107">Options</span></span>  
 <span data-ttu-id="3bbc9-108">**[カレンダーの最初の日]**</span><span class="sxs-lookup"><span data-stu-id="3bbc9-108">**First calendar day**</span></span>  
 <span data-ttu-id="3bbc9-109">現在の年が開始する日を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="3bbc9-109">Type or select the day that begins the current year.</span></span>  
  
 <span data-ttu-id="3bbc9-110">**[カレンダーの最終日]**</span><span class="sxs-lookup"><span data-stu-id="3bbc9-110">**Last calendar day**</span></span>  
 <span data-ttu-id="3bbc9-111">現在の年が終了する日を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="3bbc9-111">Type or select the day that ends the current year.</span></span>  
  
 <span data-ttu-id="3bbc9-112">**[週の最初の曜日]**</span><span class="sxs-lookup"><span data-stu-id="3bbc9-112">**First day of the week**</span></span>  
 <span data-ttu-id="3bbc9-113">週の最初の曜日を選択します。</span><span class="sxs-lookup"><span data-stu-id="3bbc9-113">Select the day that begins a week.</span></span>  
  
 <span data-ttu-id="3bbc9-114">**[時間間隔]**</span><span class="sxs-lookup"><span data-stu-id="3bbc9-114">**Time periods**</span></span>  
 <span data-ttu-id="3bbc9-115">時間ディメンションの暦年の時間間隔を選択します。</span><span class="sxs-lookup"><span data-stu-id="3bbc9-115">Select the time periods for the calendar year of the time dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3bbc9-116">`Date` 時間間隔は必須です。</span><span class="sxs-lookup"><span data-stu-id="3bbc9-116">The `Date` time period is required.</span></span>  
  
 <span data-ttu-id="3bbc9-117">**[時間メンバー名の言語]**</span><span class="sxs-lookup"><span data-stu-id="3bbc9-117">**Language for time member names**</span></span>  
 <span data-ttu-id="3bbc9-118">時間ディメンションのメンバーの言語を選択します。</span><span class="sxs-lookup"><span data-stu-id="3bbc9-118">Select the language for the members in the time dimension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bbc9-119">参照</span><span class="sxs-lookup"><span data-stu-id="3bbc9-119">See Also</span></span>  
 <span data-ttu-id="3bbc9-120">[ディメンションウィザードの F1 ヘルプ](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="3bbc9-120">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="3bbc9-121">[ディメンション &#40;Analysis Services-多次元データ&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="3bbc9-121">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="3bbc9-122">[多次元モデル内のディメンション](multidimensional-models/dimensions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="3bbc9-122">[Dimensions in Multidimensional Models](multidimensional-models/dimensions-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="3bbc9-123">[[カレンダーの選択] &#40;ディメンションウィザード&#41;](select-calendars-dimension-wizard.md)</span><span class="sxs-lookup"><span data-stu-id="3bbc9-123">[Select Calendars &#40;Dimension Wizard&#41;](select-calendars-dimension-wizard.md)</span></span>  
  
  
