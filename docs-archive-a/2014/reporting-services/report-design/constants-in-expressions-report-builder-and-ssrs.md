---
title: 式で使用される定数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b8ae650b-0f46-4848-b62b-15f8a40751b8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d95005a04482cb03d3bb3860aea695c7e7969255
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634903"
---
# <a name="constants-in-expressions-report-builder-and-ssrs"></a><span data-ttu-id="93da5-102">式で使用される定数 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="93da5-102">Constants in Expressions (Report Builder and SSRS)</span></span>
  <span data-ttu-id="93da5-103">定数は、リテラル テキストまたは定義済みのテキストです。</span><span class="sxs-lookup"><span data-stu-id="93da5-103">A constant consists of literal text or predefined text.</span></span> <span data-ttu-id="93da5-104">レポート プロセッサは定義済みの定数にアクセスできるので、このような定数を式に含めると、式が評価される前に、このような定数が表す値が式に代入されます。</span><span class="sxs-lookup"><span data-stu-id="93da5-104">The report processor has access to predefined constants so that when you include them in an expression, the values they represent are substituted in the expression before it is evaluated.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="literal-text"></a><span data-ttu-id="93da5-105">リテラル テキスト</span><span class="sxs-lookup"><span data-stu-id="93da5-105">Literal Text</span></span>  
 <span data-ttu-id="93da5-106">式の中では、リテラル テキストは二重引用符で囲まれたテキストです。</span><span class="sxs-lookup"><span data-stu-id="93da5-106">In an expression, literal text is text that is in double quotation marks.</span></span> <span data-ttu-id="93da5-107">テキストは、式の一部でない場合、二重引用符で囲まずにテキスト ボックスに直接入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="93da5-107">You can also type text directly into a text box without double quotation marks if it is not part of an expression.</span></span> <span data-ttu-id="93da5-108">テキスト ボックスの値が等号 (=) から始まっていなければ、テキストはリテラル テキストとして処理されます。</span><span class="sxs-lookup"><span data-stu-id="93da5-108">If the text box value does not begin with an equal sign (=), the text is treated as literal text.</span></span> <span data-ttu-id="93da5-109">次の表に、式内のリテラル テキストの例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="93da5-109">The following table shows several examples of literal text in an expression.</span></span>  
  
|<span data-ttu-id="93da5-110">常時</span><span class="sxs-lookup"><span data-stu-id="93da5-110">Constant</span></span>|<span data-ttu-id="93da5-111">表示テキスト</span><span class="sxs-lookup"><span data-stu-id="93da5-111">Display text</span></span>|<span data-ttu-id="93da5-112">式のテキスト</span><span class="sxs-lookup"><span data-stu-id="93da5-112">Expression text</span></span>|  
|--------------|------------------|---------------------|  
|<span data-ttu-id="93da5-113">Report run at:</span><span class="sxs-lookup"><span data-stu-id="93da5-113">Report run at:</span></span>|<\<Expr>>|`="Report run at: " & Globals!ExecutionTime`|  
|<span data-ttu-id="93da5-114">Adventure Works Cycles</span><span class="sxs-lookup"><span data-stu-id="93da5-114">Adventure Works Cycles</span></span>|<span data-ttu-id="93da5-115">Adventure Works Cycles</span><span class="sxs-lookup"><span data-stu-id="93da5-115">Adventure Works Cycles</span></span>|<span data-ttu-id="93da5-116">Adventure Works Cycles</span><span class="sxs-lookup"><span data-stu-id="93da5-116">Adventure Works Cycles</span></span>|  
|<span data-ttu-id="93da5-117">[角かっこで囲まれた表示テキスト]</span><span class="sxs-lookup"><span data-stu-id="93da5-117">[Bracketed display text]</span></span>|<span data-ttu-id="93da5-118">\\[角かっこで囲まれた表示テキスト\\]</span><span class="sxs-lookup"><span data-stu-id="93da5-118">\\[Bracketed display text\\]</span></span>|<span data-ttu-id="93da5-119">[角かっこで囲まれた表示テキスト]</span><span class="sxs-lookup"><span data-stu-id="93da5-119">[Bracketed display text]</span></span>|  
  
## <a name="rdl-constants"></a><span data-ttu-id="93da5-120">RDL 定数</span><span class="sxs-lookup"><span data-stu-id="93da5-120">RDL Constants</span></span>  
 <span data-ttu-id="93da5-121">レポート定義言語 (RDL) で定義されている定数は、式の中で使用できます。</span><span class="sxs-lookup"><span data-stu-id="93da5-121">You can use constants defined in Report Definition Language (RDL) in an expression.</span></span> <span data-ttu-id="93da5-122">**[式]** ダイアログ ボックスでは、特定の有効な値 (列挙型とも呼ばれます) のみを使用できるレポート プロパティの式を作成すると、定数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="93da5-122">In the **Expression** dialog box, constants appear when you create an expression for a report property that only accepts certain valid values, also known as enumerated types.</span></span> <span data-ttu-id="93da5-123">次の表に 2 つの例を示します。</span><span class="sxs-lookup"><span data-stu-id="93da5-123">The following table shows two examples.</span></span>  
  
|<span data-ttu-id="93da5-124">プロパティ</span><span class="sxs-lookup"><span data-stu-id="93da5-124">Property</span></span>|<span data-ttu-id="93da5-125">説明</span><span class="sxs-lookup"><span data-stu-id="93da5-125">Description</span></span>|<span data-ttu-id="93da5-126">値</span><span class="sxs-lookup"><span data-stu-id="93da5-126">Values</span></span>|  
|--------------|-----------------|------------|  
|<span data-ttu-id="93da5-127">TextAlign</span><span class="sxs-lookup"><span data-stu-id="93da5-127">TextAlign</span></span>|<span data-ttu-id="93da5-128">テキスト ボックス内でのテキストの配置に有効な値です。</span><span class="sxs-lookup"><span data-stu-id="93da5-128">Valid values for aligning text in a text box.</span></span>|<span data-ttu-id="93da5-129">General、Left、Center、Right</span><span class="sxs-lookup"><span data-stu-id="93da5-129">General, Left, Center, Right</span></span>|  
|<span data-ttu-id="93da5-130">BorderStyle</span><span class="sxs-lookup"><span data-stu-id="93da5-130">BorderStyle</span></span>|<span data-ttu-id="93da5-131">レポートに追加された線に有効な値です。</span><span class="sxs-lookup"><span data-stu-id="93da5-131">Valid values for a line added to a report.</span></span>|<span data-ttu-id="93da5-132">Default、None、Dotted、Dashed、Solid、Double、DashDot、DashDotdot</span><span class="sxs-lookup"><span data-stu-id="93da5-132">Default, None, Dotted, Dashed, Solid, Double, DashDot, DashDotdot</span></span>|  
  
## <a name="visual-basic-constants"></a><span data-ttu-id="93da5-133">Visual Basic 定数</span><span class="sxs-lookup"><span data-stu-id="93da5-133">Visual Basic Constants</span></span>  
 <span data-ttu-id="93da5-134">[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ランタイム ライブラリで定義されている定数を、式の中で使用できます。</span><span class="sxs-lookup"><span data-stu-id="93da5-134">You can use constants defined in the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] run-time library in an expression.</span></span> <span data-ttu-id="93da5-135">たとえば、定数 `DateInterval.Day` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="93da5-135">For example, you can use the constant `DateInterval.Day`.</span></span> <span data-ttu-id="93da5-136">2008 年 1 月 10 日の場合、次の関数を使用すると、数値 10 が返されます。</span><span class="sxs-lookup"><span data-stu-id="93da5-136">The following expression for the date January 10, 2008 returns the number 10:</span></span>  
  
 `=DatePart("d",Globals!ExecutionTime)`  
  
## <a name="clr-constants"></a><span data-ttu-id="93da5-137">CLR 定数</span><span class="sxs-lookup"><span data-stu-id="93da5-137">CLR Constants</span></span>  
 <span data-ttu-id="93da5-138">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の共通言語ランタイム (CLR) クラスで定義されている定数は、式の中で使用できます。</span><span class="sxs-lookup"><span data-stu-id="93da5-138">You can use constants defined in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] common language run-time (CLR) classes in an expression.</span></span> <span data-ttu-id="93da5-139">次の表に、システム定義色の例を示します。</span><span class="sxs-lookup"><span data-stu-id="93da5-139">The following table shows an example of a system-defined color.</span></span>  
  
|<span data-ttu-id="93da5-140">定数</span><span class="sxs-lookup"><span data-stu-id="93da5-140">Constant</span></span>|<span data-ttu-id="93da5-141">説明</span><span class="sxs-lookup"><span data-stu-id="93da5-141">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="93da5-142">MistyRose</span><span class="sxs-lookup"><span data-stu-id="93da5-142">MistyRose</span></span>|<span data-ttu-id="93da5-143">背景色に基づいたレポート プロパティの式を作成する場合は、色を名前で指定できます。</span><span class="sxs-lookup"><span data-stu-id="93da5-143">When you create an expression for a report property that is based on background color, you can specify a color by name.</span></span> <span data-ttu-id="93da5-144">有効な名前は、 **[式]** ダイアログ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="93da5-144">Valid names are listed in the **Expression** dialog box.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="93da5-145">参照</span><span class="sxs-lookup"><span data-stu-id="93da5-145">See Also</span></span>  
 <span data-ttu-id="93da5-146">[[式] ダイアログボックス](../expression-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="93da5-146">[Expression Dialog Box](../expression-dialog-box.md) </span></span>  
 <span data-ttu-id="93da5-147">[式 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="93da5-147">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="93da5-148">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="93da5-148">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="93da5-149">[式に含まれるデータ型 &#40;レポートビルダーと SSRS&#41;](data-types-in-expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="93da5-149">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](data-types-in-expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="93da5-150">[[式] ダイアログ ボックス &#40;レポート ビルダー&#41;](../expression-dialog-box-report-builder.md)</span><span class="sxs-lookup"><span data-stu-id="93da5-150">[Expression Dialog Box &#40;Report Builder&#41;](../expression-dialog-box-report-builder.md)</span></span>  
  
  
