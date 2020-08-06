---
title: テキスト ボックス (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10134"
- sql12.rtp.rptdesigner.textproperties.general.f1
- "10120"
- sql12.rtp.rptdesigner.textboxproperties.general.f1
ms.assetid: df49e4e3-f279-4c63-a03b-b70c095f4ba2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f3bc9d9d645fe2a966197af9059eb90c64ce3954
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640608"
---
# <a name="text-boxes-report-builder-and-ssrs"></a><span data-ttu-id="c25ae-102">テキスト ボックス (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="c25ae-102">Text Boxes (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c25ae-103">テキスト ボックスといえば、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office PowerPoint のように領域にテキストを含むスタンド アロンのボックスを思い浮かべると思います。</span><span class="sxs-lookup"><span data-stu-id="c25ae-103">When you think of a text box, you probably think of a stand-alone box containing text on a surface like [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office PowerPoint.</span></span> <span data-ttu-id="c25ae-104">レポート ビルダーでは、同じように、タイトル、説明、およびラベルのリテラル テキスト、または式に基づく動的なテキストを表示できます。</span><span class="sxs-lookup"><span data-stu-id="c25ae-104">In Report Builder, some text boxes are like that, and they can display literal text for titles, descriptions, and labels, or dynamic text based on expressions.</span></span> <span data-ttu-id="c25ae-105">ただし、テーブルまたはマトリックス (Tablix データ領域) の各セルにはテキスト ボックスがあり、レポート内のスタンドアロン テキスト ボックスと同じ方法で書式設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="c25ae-105">But every cell in a table or matrix (a tablix data region) also contains a text box, which can be formatted in the same way as stand-alone text boxes in your report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c25ae-106">レポート デザイン画面またはレポート デザイン画面上のテキスト ボックスに、レポート データセットのフィールド値を直接ドラッグすると、レポートを実行する際に、結果セットの最初の値のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c25ae-106">If you drag a report dataset field value directly to the report design surface, or to a text box on the report design surface, you only see the first value in the result set when you run the report.</span></span> <span data-ttu-id="c25ae-107">フィールドのすべての値を表示するには、テーブルまたはマトリックスのセルにフィールドをドラッグする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c25ae-107">To see all the values for a field, you must drag the field to a cell in a table or matrix.</span></span> <span data-ttu-id="c25ae-108">この状態でレポートを実行すると、そのフィールドにすべての値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c25ae-108">That way, when you run the report, you will see all the values in that field.</span></span>  
  
 <span data-ttu-id="c25ae-109">自由形式レイアウトでテキストを繰り返し表示するには、一覧データ領域にテキスト ボックスを配置します。</span><span class="sxs-lookup"><span data-stu-id="c25ae-109">To show repeating text in a free-form layout, place a text box in a list data region.</span></span> <span data-ttu-id="c25ae-110">複数値に対し形式を繰り返す場合は、一覧を使用します。たとえば、各顧客につき 1 回繰り返される請求書フォームなどです。</span><span class="sxs-lookup"><span data-stu-id="c25ae-110">Use a list when you want to repeat a form for multiple values, for example, a customer invoice form repeated once for each customer.</span></span> <span data-ttu-id="c25ae-111">詳細については、「 [&#40;レポートビルダーと SSRS&#41;の一覧](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c25ae-111">For more information, see [Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="c25ae-112">テキスト ボックス レイアウト、および最後のテキスト ボックスの下の空白を制御するには、四角形のコンテナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="c25ae-112">Use a rectangle container when you want to control the text box layout and white space below the last text box.</span></span> <span data-ttu-id="c25ae-113">詳細については、「[四角形と線 &#40;レポート ビルダーおよび SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c25ae-113">For more information, see [Rectangles and Lines &#40;Report Builder and SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="c25ae-114">テキスト ボックス内で式を使用して、リテラル テキストを保持したり、データベースのフィールドを指定したり、データを計算したりできます。</span><span class="sxs-lookup"><span data-stu-id="c25ae-114">The expressions in a text box can contain literal text, point to a field in the database, or calculate data.</span></span> <span data-ttu-id="c25ae-115">すべての式はプレースホルダー テキストとして表示され、番号、色、および他の外観のプロパティを書式設定できます。</span><span class="sxs-lookup"><span data-stu-id="c25ae-115">All expressions are shown as placeholder text so that you can format numbers, colors, and other appearance properties.</span></span> <span data-ttu-id="c25ae-116">同じテキスト ボックス内でプレースホルダーをリテラル テキストと組み合わせることもできます。</span><span class="sxs-lookup"><span data-stu-id="c25ae-116">You can also combine placeholders with literal text in the same text box.</span></span>  
  
 <span data-ttu-id="c25ae-117">複数のフォント、色、スタイル、およびアクションを使用して、1 つのテキスト ボックスでテキストを書式設定できます。</span><span class="sxs-lookup"><span data-stu-id="c25ae-117">You can format text in any single text box with multiple fonts, colors, styles, and actions.</span></span> <span data-ttu-id="c25ae-118">詳細については、「 [テキストとプレースホルダーの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c25ae-118">For more information, see [Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="growing-and-shrinking-a-text-box"></a><a name="GrowShrinkTextBox"></a> <span data-ttu-id="c25ae-119">テキスト ボックスの拡張と圧縮</span><span class="sxs-lookup"><span data-stu-id="c25ae-119">Growing and Shrinking a Text Box</span></span>  
 <span data-ttu-id="c25ae-120">既定では、テキスト ボックスのサイズは固定されています。</span><span class="sxs-lookup"><span data-stu-id="c25ae-120">By default, text boxes are a fixed size.</span></span> <span data-ttu-id="c25ae-121">テキスト ボックスをその内容に応じて縦に縮小または拡張されるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="c25ae-121">You can allow a text box to shrink or expand vertically based on its contents.</span></span> <span data-ttu-id="c25ae-122">詳細については、「 [テキスト ボックスの拡大または縮小 &#40;レポート ビルダーおよび SSRS&#41;](allow-a-text-box-to-grow-or-shrink-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c25ae-122">For more information, see [Allow a Text Box to Grow or Shrink &#40;Report Builder and SSRS&#41;](allow-a-text-box-to-grow-or-shrink-report-builder-and-ssrs.md).</span></span>  
  
## <a name="orienting-a-text-box"></a><span data-ttu-id="c25ae-123">テキスト ボックスの向きの調整</span><span class="sxs-lookup"><span data-stu-id="c25ae-123">Orienting a Text Box</span></span>  
 <span data-ttu-id="c25ae-124">テキスト ボックスの向きを調整することによって、より読みやすいレポートを作成したり、ロケール特有のテキストの向きに対応したり、ページ サイズが固定された印刷レポートに合うようにより多くの列を調整したり、視覚的により優れたレポートを作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="c25ae-124">Orienting text boxes can help you create more readable reports, support locale-specific text orientation, fit more columns on a printed report that has fixed page size, and create reports with more graphical appeal.</span></span> <span data-ttu-id="c25ae-125">テキスト ボックスは、水平方向、垂直方向、または 270 度回転させて向きを調整できます。</span><span class="sxs-lookup"><span data-stu-id="c25ae-125">A text box can be oriented in different directions: horizontal, vertical, or rotated by 270 degrees.</span></span> <span data-ttu-id="c25ae-126">垂直オプションは、上から下に字を書く東アジアの言語で最も一般的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="c25ae-126">The vertical option is most commonly used for East Asian languages that are written top to bottom.</span></span> <span data-ttu-id="c25ae-127">大部分のレンダラーで、垂直オプションは、テキストが上から下に配置されるように (文字は横向きにならない) グリフの回転プロパティを処理します。</span><span class="sxs-lookup"><span data-stu-id="c25ae-127">In most renderers the vertical option handles the glyph rotation property so that the text is written top to bottom, but the characters are not on their sides.</span></span> <span data-ttu-id="c25ae-128">その他の言語の場合、垂直オプションおよび 270 度回転オプションではテキストは横向きに配置されます。</span><span class="sxs-lookup"><span data-stu-id="c25ae-128">For other languages, in the vertical and 270-degree options the text is written sideways.</span></span>  
  
 <span data-ttu-id="c25ae-129">リテラル テキスト、レポート データセットからのフィールド、または計算されたデータを含むテキスト ボックスに向きを適用できます。</span><span class="sxs-lookup"><span data-stu-id="c25ae-129">You can apply orientation to text boxes that contain literal text, fields from a report dataset, or calculated data.</span></span> <span data-ttu-id="c25ae-130">テキスト ボックスは、レポート本文、テーブルまたはマトリックス、レポート ヘッダーとフッターでスタンドアロンになることができます。</span><span class="sxs-lookup"><span data-stu-id="c25ae-130">The text box can be stand-alone in the report body, in a table or matrix, or in a report header and footer.</span></span>  
  
 <span data-ttu-id="c25ae-131">次の図は、月ごとにデータをグループ化するテーブル レポートの 3 つのバージョンを示しています。</span><span class="sxs-lookup"><span data-stu-id="c25ae-131">The following picture shows three versions of a table report that groups data by month.</span></span> <span data-ttu-id="c25ae-132">月の値を含むテキスト ボックスでは、異なるテキスト ボックスの向きが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c25ae-132">The text box that contains the month value uses a different text box orientation.</span></span>  
  
 <span data-ttu-id="c25ae-133">![rs_TextBoxOrientation](../media/rs-textboxorientation.gif "rs_TextBoxOrientation")</span><span class="sxs-lookup"><span data-stu-id="c25ae-133">![rs_TextBoxOrientation](../media/rs-textboxorientation.gif "rs_TextBoxOrientation")</span></span>  
  
 <span data-ttu-id="c25ae-134">方向はテキスト ボックスに対して設定されるため、そのテキスト ボックス内のすべてのテキストにその方向が適用されます。</span><span class="sxs-lookup"><span data-stu-id="c25ae-134">Orientation is set on the text box and applies to all the text in the box.</span></span> <span data-ttu-id="c25ae-135">テキスト ボックスの一部のみに異なる方向を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="c25ae-135">You cannot specify a different orientation for parts of the text box.</span></span>  
  
 <span data-ttu-id="c25ae-136">テキストの向きを変更する方法の詳細については、「[チュートリアル: テキストの書式設定 &#40;レポートビルダー&#41;](../tutorial-format-text-report-builder.md)」のテキストの回転に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c25ae-136">To quickly get started with changing text orientation, see the section on rotating text in the [Tutorial: Format Text &#40;Report Builder&#41;](../tutorial-format-text-report-builder.md).</span></span> <span data-ttu-id="c25ae-137">詳細については、「[テキストボックスの向きの設定 &#40;レポートビルダーと SSRS&#41;](set-text-box-orientation-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c25ae-137">For more information, see [Set Text Box Orientation &#40;Report Builder and SSRS&#41;](set-text-box-orientation-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="c25ae-138">操作方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="c25ae-138">How-To Topics</span></span>  
 [<span data-ttu-id="c25ae-139">テキスト ボックスの追加、移動、または削除 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c25ae-139">Add, Move, or Delete a Text Box &#40;Report Builder and SSRS&#41;</span></span>](add-move-or-delete-a-text-box-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="c25ae-140">テキスト ボックス内のテキストの書式設定 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c25ae-140">Format Text in a Text Box &#40;Report Builder and SSRS&#41;</span></span>](format-text-in-a-text-box-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="c25ae-141">テキスト ボックスの方向の設定 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c25ae-141">Set Text Box Orientation &#40;Report Builder and SSRS&#41;</span></span>](set-text-box-orientation-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="c25ae-142">テキスト ボックスの拡大または縮小 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c25ae-142">Allow a Text Box to Grow or Shrink &#40;Report Builder and SSRS&#41;</span></span>](allow-a-text-box-to-grow-or-shrink-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a><span data-ttu-id="c25ae-143">参照</span><span class="sxs-lookup"><span data-stu-id="c25ae-143">See Also</span></span>  
 <span data-ttu-id="c25ae-144">[レポートビルダーおよび SSRS&#41;&#40;のテキストとプレースホルダーの書式設定](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c25ae-144">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c25ae-145">数値と日付の書式設定 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c25ae-145">Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;</span></span>](formatting-numbers-and-dates-report-builder-and-ssrs.md)  
  
  
