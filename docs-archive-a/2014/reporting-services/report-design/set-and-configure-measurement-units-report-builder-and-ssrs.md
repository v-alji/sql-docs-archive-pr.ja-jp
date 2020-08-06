---
title: 測定単位の設定および構成 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a15a96c3-7d2c-433e-a440-4ea051e967a9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c01523dad9a96d2d45b96474d36873bac2484343
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631543"
---
# <a name="set-and-configure-measurement-units-report-builder-and-ssrs"></a><span data-ttu-id="8f265-102">測定単位の設定および構成 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="8f265-102">Set and Configure Measurement Units (Report Builder and SSRS)</span></span>
  <span data-ttu-id="8f265-103">インジケーターは、パーセンテージと数値の 2 つの測定単位を提供します。</span><span class="sxs-lookup"><span data-stu-id="8f265-103">Indicators provide two measurement units: percentage and numeric.</span></span> <span data-ttu-id="8f265-104">既定では、インジケーターは測定単位としてパーセンテージを使用するように構成されます。</span><span class="sxs-lookup"><span data-stu-id="8f265-104">By default, indicators are configured to use percentages as the measurement unit.</span></span> <span data-ttu-id="8f265-105">つまり、インジケーター セットの各アイコンに割り当てられたインジケーター値は、パーセンテージ範囲によって決まります。</span><span class="sxs-lookup"><span data-stu-id="8f265-105">This means that the indicator values assigned to each icon in the indicator set are determined by a percentage range.</span></span> <span data-ttu-id="8f265-106">パーセンテージ範囲は、インジケーター セット内のアイコン全体に均等に分割されます。</span><span class="sxs-lookup"><span data-stu-id="8f265-106">The percentage ranges are evenly divided across the icons in the indicator set.</span></span> <span data-ttu-id="8f265-107">各アイコンは、インジケーターの状態を表します。</span><span class="sxs-lookup"><span data-stu-id="8f265-107">Each icon represents an indicator state.</span></span> <span data-ttu-id="8f265-108">異なる開始パーセンテージと終了パーセンテージを指定することで、インジケーター セット内の各アイコンのパーセンテージを変更できます。</span><span class="sxs-lookup"><span data-stu-id="8f265-108">You can change the percentages for each icon in the indicator set by specifying different start and end percentages.</span></span> <span data-ttu-id="8f265-109">また、インジケーターはデータ内の最小値と最大値を自動的に検出します。</span><span class="sxs-lookup"><span data-stu-id="8f265-109">Indicators also automatically detect the minimum and maximum values in the data.</span></span>  
  
 <span data-ttu-id="8f265-110">さらに、測定単位を数値に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="8f265-110">You can change the measurement unit to be a numeric value.</span></span> <span data-ttu-id="8f265-111">その場合、データの最小値または最大値を指定せず、代わりにインジケーターで使用される各アイコンの開始値と終了値のみを指定します。</span><span class="sxs-lookup"><span data-stu-id="8f265-111">In this case, you do not specify minimum or maximum for the data; instead, you provide only the start and end values for each icon that the indicator uses.</span></span>  
  
 <span data-ttu-id="8f265-112">測定単位などのオプションは、式を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="8f265-112">Options such as measurement units can be set by using expressions.</span></span> <span data-ttu-id="8f265-113">詳細については、「[式 (レポート ビルダーおよび SSRS)](expressions-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f265-113">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-use-the-numeric-state-measurement-unit"></a><span data-ttu-id="8f265-114">数値の状態測定単位を使用するには</span><span class="sxs-lookup"><span data-stu-id="8f265-114">To use the numeric state measurement unit</span></span>  
  
1.  <span data-ttu-id="8f265-115">変更するインジケーターを右クリックし、 **[インジケーターのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8f265-115">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="8f265-116">左ペインの **[値と状態]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8f265-116">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="8f265-117">**[状態の単位]** の一覧で、 **[数値]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8f265-117">In the **States Measurement Unit** list, click **Numeric**.</span></span>  
  
     <span data-ttu-id="8f265-118">必要に応じて、 **[式]** ( *[fx]* ) ボタンをクリックし、オプションの値を設定する式を編集します。</span><span class="sxs-lookup"><span data-stu-id="8f265-118">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the value of the option.</span></span>  
  
4.  <span data-ttu-id="8f265-119">インジケーター セットのアイコンごとに、 **[開始]** および **[終了]** ボックスの値を更新します。</span><span class="sxs-lookup"><span data-stu-id="8f265-119">For each icon in the indicator set, update the values in the **Start** and **End** text boxes.</span></span>  
  
     <span data-ttu-id="8f265-120">必要に応じて、 **[式]** ( *[fx]* ) ボタンをクリックし、 **[開始]** および **[終了]** オプションの値を設定する式を編集します。</span><span class="sxs-lookup"><span data-stu-id="8f265-120">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the values of the **Start** and **End** options.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8f265-121">**[開始]** ボックスと **[終了]** ボックスの値は数値である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8f265-121">The values in the **Start** and **End** text boxes must be numeric.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-use-the-percentage-measurement-unit"></a><span data-ttu-id="8f265-122">パーセンテージの状態測定単位を使用するには</span><span class="sxs-lookup"><span data-stu-id="8f265-122">To use the percentage measurement unit</span></span>  
  
1.  <span data-ttu-id="8f265-123">変更するインジケーターを右クリックし、 **[インジケーターのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8f265-123">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="8f265-124">左ペインの **[値と状態]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8f265-124">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="8f265-125">**[状態の単位]** の一覧で、 **[パーセント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8f265-125">In the **States Measurement Unit** list, click **Percentage**.</span></span>  
  
     <span data-ttu-id="8f265-126">必要に応じて、 **[式]** ( *[fx]* ) ボタンをクリックし、オプションの値を設定する式を編集します。</span><span class="sxs-lookup"><span data-stu-id="8f265-126">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the value of the option.</span></span>  
  
4.  <span data-ttu-id="8f265-127">インジケーターが使用するデータの最小値と最大値を自動検出する代わりに、必要に応じて、 **[最小値]** および **[最大値]** オプションを変更して特定の値を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8f265-127">Optionally, change the **Minimum** and **Maximum** options to use specific values instead of automatically detecting the minimum and maximum values of the data that the indicator uses.</span></span> <span data-ttu-id="8f265-128">**[最小値]** は、 **[最大値]** より小さい値に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8f265-128">The value of **Minimum** must be smaller than the value of **Maximum**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8f265-129">最小値と最大値を明示的に設定すると、インジケーターはデータ内の実際の最小値と最大値に関係なく、設定した値の範囲を使用します。</span><span class="sxs-lookup"><span data-stu-id="8f265-129">If you explicitly set minimum and maximum values, that value range is used by the indicator regardless of the actual the minimum and maximum values in the data.</span></span> <span data-ttu-id="8f265-130">つまり、最小値より小さい値と最大値より大きい値は、レポートに表示するインジケーター アイコンを決定する評価から除外されます。</span><span class="sxs-lookup"><span data-stu-id="8f265-130">This means that values lower than the minimum and higher than the maximum are excluded from the evaluation that determine what indictor icon to show in the report.</span></span>  
  
     <span data-ttu-id="8f265-131">必要に応じて、 **[式]** ( *[fx]* ) ボタンをクリックし、オプションの値を設定する式を編集します。</span><span class="sxs-lookup"><span data-stu-id="8f265-131">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the values of the option.</span></span>  
  
5.  <span data-ttu-id="8f265-132">インジケーター セットのアイコンごとに、 **[開始]** および **[終了]** ボックスの値を更新します。</span><span class="sxs-lookup"><span data-stu-id="8f265-132">For each icon in the indicator set, update the values in the **Start** and **End** text boxes.</span></span>  
  
     <span data-ttu-id="8f265-133">必要に応じて、 **[式]** ( *[fx]* ) ボタンをクリックし、 **[開始]** および **[終了]** オプションの値を設定する式を編集します。</span><span class="sxs-lookup"><span data-stu-id="8f265-133">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the values of the **Start** and **End** options.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8f265-134">**[開始]** ボックスと **[終了]** ボックスの値は数値である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8f265-134">The values in the **Start** and **End** text boxes must be numeric.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8f265-135">参照</span><span class="sxs-lookup"><span data-stu-id="8f265-135">See Also</span></span>  
 [<span data-ttu-id="8f265-136">インジケーター &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8f265-136">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
