---
title: 式を使用したインジケーターのサイズの指定 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ab0b86f1-4882-4258-a2b6-c612faecfa4b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b450abb957329b8dbaa4f7f0e4c963c5f63f06b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631520"
---
# <a name="specify-the-size-of-an-indicator-using-an-expression-report-builder-and-ssrs"></a><span data-ttu-id="1791a-102">式を使用したインジケーターのサイズの指定 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="1791a-102">Specify the Size of an Indicator Using an Expression (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1791a-103">インジケーターは、色、方向、形状のほか、サイズを変更して、視覚的効果を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="1791a-103">In addition to color, direction, and shape, you can use size to maximize the visual impact of indicators.</span></span>  
  
 <span data-ttu-id="1791a-104">インジケーターには、IndicatorStates という名前のインジケーターの状態のコレクションがあります。</span><span class="sxs-lookup"><span data-stu-id="1791a-104">An indicator has a collection of indicator states named IndicatorStates.</span></span> <span data-ttu-id="1791a-105">一般に、IndicatorStates コレクションには複数の状態があります。</span><span class="sxs-lookup"><span data-stu-id="1791a-105">The IndicatorStates collection typically have multiple states.</span></span> <span data-ttu-id="1791a-106">各状態は、コレクションのメンバーであり、アイコンで表示されます。</span><span class="sxs-lookup"><span data-stu-id="1791a-106">Each state is a member of the collection and is represented by an icon.</span></span> <span data-ttu-id="1791a-107">各状態をまとめて IndicatorStates コレクションが構成されます。</span><span class="sxs-lookup"><span data-stu-id="1791a-107">Together the states constitute the IndicatorsStates collection.</span></span>  
  
 <span data-ttu-id="1791a-108">アイコンのサイズを動的に構成するには、レポート ビルダーのプロパティ ペインにある IndicatorStates コレクションのメンバーのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="1791a-108">To dynamically configure the sizes of icons, you set properties of members of the IndicatorsStates collection in the Properties pane of Report Builder.</span></span> <span data-ttu-id="1791a-109">**プロパティ** ペインが表示されていない場合は、 **[表示]** タブをクリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1791a-109">If the **Properties** pane is not visible, click the **View** tab and select **Properties**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1791a-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]では、 **[プロパティ]** ウィンドウを使用して、メンバーのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="1791a-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you use the **Properties** window to set the member properties.</span></span> <span data-ttu-id="1791a-111">**[プロパティ]** ウィンドウが開いていない場合は、F4 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="1791a-111">If the **Properties** window is not open, press the F4 key.</span></span>  
  
 <span data-ttu-id="1791a-112">**プロパティ** ペインでは、インジケーターの IndicatorStates コレクションのプロパティにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1791a-112">The **Properties** pane provides access to the properties of the IndicatorStates collection of an indicator.</span></span> <span data-ttu-id="1791a-113">アイコンを異なるサイズになるように構成するには、式を使用して IndicatorStates コレクション メンバーの ScaleFactor プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="1791a-113">You configure the icons to be different sizes by setting the ScaleFactor property of the IndicatorStates collection members using an expression.</span></span> <span data-ttu-id="1791a-114">詳細については、「[式 (レポート ビルダーおよび SSRS)](expressions-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1791a-114">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="1791a-115">この手順で使用する式は、「 [インジケーター &#40;レポート ビルダーおよび SSRS&#41;](indicators-report-builder-and-ssrs.md)をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1791a-115">The expression used in this procedure was also used to generate the report with different sizes of indicators, shown in [Indicators &#40;Report Builder and SSRS&#41;](indicators-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-the-indicator-icon-size-using-an-expression"></a><span data-ttu-id="1791a-116">式を使用してインジケーターのアイコン サイズを指定するには</span><span class="sxs-lookup"><span data-stu-id="1791a-116">To specify the indicator icon size using an expression</span></span>  
  
1.  <span data-ttu-id="1791a-117">変更するインジケーターをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1791a-117">Click the indicator you want to change.</span></span>  
  
2.  <span data-ttu-id="1791a-118">プロパティ ペインで、IndicatorStates プロパティを探します。</span><span class="sxs-lookup"><span data-stu-id="1791a-118">In the Properties pane, locate the IndicatorStates property.</span></span>  
  
     <span data-ttu-id="1791a-119">プロパティ ペインがカテゴリごとに整理されている場合は、 **[状態]** カテゴリ内に IndicatorStates があります。</span><span class="sxs-lookup"><span data-stu-id="1791a-119">If the Properties pane is organized by category, you will find IndicatorStates in the **States** category.</span></span>  
  
3.  <span data-ttu-id="1791a-120">IndicatorStates の横にある参照ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1791a-120">Click the ellipsis **(...)** button next to IndicatorStates.</span></span> <span data-ttu-id="1791a-121">**[インジケーターの状態コレクション エディター]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="1791a-121">The **IndicatorState Collection Editor** dialog box opens.</span></span>  
  
     <span data-ttu-id="1791a-122">コレクションのメンバーをすべて選択します。</span><span class="sxs-lookup"><span data-stu-id="1791a-122">Select all members of the collection.</span></span>  
  
4.  <span data-ttu-id="1791a-123">**[プロパティの複数選択]** の一覧で、ScaleFactor の横にある下矢印をクリックし、 **[式]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1791a-123">In the **Multi-Select Properties** list, click the down arrow next to ScaleFactor and then click **Expression**.</span></span>  
  
5.  <span data-ttu-id="1791a-124">**[式]** ダイアログ ボックスで、式を作成します。</span><span class="sxs-lookup"><span data-stu-id="1791a-124">In the **Expression** dialog box write the expression.</span></span>  
  
     <span data-ttu-id="1791a-125">次のサンプル式では、 **SalesYTD** フィールドの値に基づいて、アイコンのサイズが異なります。</span><span class="sxs-lookup"><span data-stu-id="1791a-125">The following sample expression makes the icon a different size based on the value of the **SalesYTD** field.</span></span>  
  
     `=IIF(Fields!SalesYTD.value = 0,0,Fields!SalesYTD.value/Max(Fields!SalesYTD.value,"Indicator"))`  
  
     <span data-ttu-id="1791a-126">詳細については、「[式の例 &#40;レポート ビルダーおよび SSRS&#41;](expression-examples-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1791a-126">For more information, see [Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md).</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1791a-127">参照</span><span class="sxs-lookup"><span data-stu-id="1791a-127">See Also</span></span>  
 [<span data-ttu-id="1791a-128">インジケーター &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1791a-128">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
