---
title: 式の追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a60ee091-b4ed-41e1-9b6a-032c316cd03f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 16f414bfad47ae92681de50eb576a6ac2cb3f5fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712734"
---
# <a name="add-an-expression-report-builder-and-ssrs"></a><span data-ttu-id="a03a9-102">式の追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="a03a9-102">Add an Expression (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a03a9-103">レポート アイテムのプロパティ、フィルター、グループ、並べ替え順、接続文字列、パラメーター値などを定義するために、レポートには随所に式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a03a9-103">Expressions are used throughout a report for defining report item properties, filters, groups, sort order, connection strings, and parameter values.</span></span> <span data-ttu-id="a03a9-104">式は等号 (=) で始まり、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="a03a9-104">Expressions begin with an equal sign (=) and are written in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].</span></span> <span data-ttu-id="a03a9-105">式は、評価結果とレポート レイアウト要素を組み合わせるレポート プロセッサによって実行時に評価されます。</span><span class="sxs-lookup"><span data-stu-id="a03a9-105">They are evaluated at run time by the report processor, which combines the evaluation result with report layout elements.</span></span>  
  
 <span data-ttu-id="a03a9-106">式には単純式と複合式があります。</span><span class="sxs-lookup"><span data-stu-id="a03a9-106">Expressions can be simple or complex.</span></span> <span data-ttu-id="a03a9-107">単純式は、組み込みコレクションの 1 つのアイテムを指します。</span><span class="sxs-lookup"><span data-stu-id="a03a9-107">Simple expression refer to a single item in a built-in collection.</span></span> <span data-ttu-id="a03a9-108">複合式には、定数、演算子、グローバル コレクションのアイテム、および関数呼び出しを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a03a9-108">Complex expressions can contain constants, operators, global collection items, and function calls.</span></span> <span data-ttu-id="a03a9-109">詳細については、「[式 (レポート ビルダーおよび SSRS)](expressions-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a03a9-109">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-expression-to-a-text-box"></a><span data-ttu-id="a03a9-110">テキスト ボックスに式を追加するには</span><span class="sxs-lookup"><span data-stu-id="a03a9-110">To add an expression to a text box</span></span>  
  
-   <span data-ttu-id="a03a9-111">**[デザイン]** ビューで、式を追加するデザイン画面のテキスト ボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a03a9-111">In **Design** view, click the text box on the design surface to which you want to add an expression.</span></span>  
  
    -   <span data-ttu-id="a03a9-112">単純式の場合、テキスト ボックスに式の表示テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="a03a9-112">For a simple expression, type the display text for the expression in the text box.</span></span> <span data-ttu-id="a03a9-113">たとえば、Sales データセット フィールドには、 `[Sales]`を入力します。</span><span class="sxs-lookup"><span data-stu-id="a03a9-113">For example, for the dataset field Sales, type `[Sales]`.</span></span>  
  
    -   <span data-ttu-id="a03a9-114">複合式の場合、テキスト ボックスを右クリックし、 **[式]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a03a9-114">For a complex expression, right-click the text box, and select **Expression**.</span></span> <span data-ttu-id="a03a9-115">**[式]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a03a9-115">The **Expression** dialog box opens.</span></span> <span data-ttu-id="a03a9-116">式ペインの '=' の後に式を入力するか、対話形式で式を作成し、[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a03a9-116">Type or interactively create your expression after the '=' in the expression pane, and then click OK.</span></span>  
  
         <span data-ttu-id="a03a9-117">式がデザイン画面に `<<Expr>>`として表示されます。</span><span class="sxs-lookup"><span data-stu-id="a03a9-117">The expression appears on the design surface as `<<Expr>>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a03a9-118">参照</span><span class="sxs-lookup"><span data-stu-id="a03a9-118">See Also</span></span>  
 <span data-ttu-id="a03a9-119">[テキストとプレースホルダーの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a03a9-119">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a03a9-120">[テキスト ボックス &#40;レポート ビルダーおよび SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a03a9-120">[Text Boxes &#40;Report Builder and SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a03a9-121">[レポートでの式の使用 (レポート ビルダーおよび SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a03a9-121">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a03a9-122">[フィルター式の例 &#40;レポート ビルダーおよび SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a03a9-122">[Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a03a9-123">[グループ式の例 &#40;レポート ビルダーおよび SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a03a9-123">[Group Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a03a9-124">[[式] ダイアログ ボックス &#40;レポート ビルダー&#41;](../expression-dialog-box-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="a03a9-124">[Expression Dialog Box &#40;Report Builder&#41;](../expression-dialog-box-report-builder.md) </span></span>  
 <span data-ttu-id="a03a9-125">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a03a9-125">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a03a9-126">レポートにコードを追加する &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a03a9-126">Add Code to a Report &#40;SSRS&#41;</span></span>](add-code-to-a-report-ssrs.md)  
  
  
