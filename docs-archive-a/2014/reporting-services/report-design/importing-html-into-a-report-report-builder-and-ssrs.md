---
title: レポートへの HTML のインポート (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: dd0410ea-8839-4e8c-9944-8cdfe5465591
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4f978e67c67556184012db6b809e4f5754f2374c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713854"
---
# <a name="importing-html-into-a-report-report-builder-and-ssrs"></a><span data-ttu-id="7f745-102">レポートへの HTML のインポート (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="7f745-102">Importing HTML into a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7f745-103">テキスト ボックスを使用すると、データセットのフィールドから取得した HTML 形式のテキストをレポートに挿入できます。</span><span class="sxs-lookup"><span data-stu-id="7f745-103">You can use a text box to insert HTML-formatted text that you have retrieved from a field in your dataset into a report.</span></span> <span data-ttu-id="7f745-104">正しい形式の HTML に評価される単純型または複合型の式のテキストを使用できます。</span><span class="sxs-lookup"><span data-stu-id="7f745-104">The text can come from any simple or complex expression that evaluates to correctly formatted HTML.</span></span> <span data-ttu-id="7f745-105">書式付きのテキストは、PDF などのサポートされている出力形式すべてにレンダリングできます。</span><span class="sxs-lookup"><span data-stu-id="7f745-105">Formatted text can be rendered to all supported output formats, including PDF.</span></span>  
  
 <span data-ttu-id="7f745-106">![rs_HTMLFormatting](../media/rs-htmlformatting.gif "rs_HTMLFormatting")</span><span class="sxs-lookup"><span data-stu-id="7f745-106">![rs_HTMLFormatting](../media/rs-htmlformatting.gif "rs_HTMLFormatting")</span></span>  
  
 <span data-ttu-id="7f745-107">この図では、レポート デザイン ビュー内の HTML 形式のテキストが示されています。これは、レポートの実行時にレンダリングされるテキストと同じです。</span><span class="sxs-lookup"><span data-stu-id="7f745-107">This illustration shows text with HTML formatting in report design view, and the same text as it is rendered when the report is run.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7f745-108">HTML マークアップが含まれたテキストをインポートする場合、データは必ず最初にテキスト ボックスによって解析される必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f745-108">When you import text that contains HTML markup, the data must always be parsed by the text box first.</span></span> <span data-ttu-id="7f745-109">サポートされているのは HTML タグのサブセットのみなので、レンダリングされたレポートに表示される HTML が元の HTML と異なる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="7f745-109">Because only a subset of HTML tags is supported, the HTML that is shown in the rendered report may differ from your original HTML.</span></span>  
  
 <span data-ttu-id="7f745-110">すぐに使用するには、「[チュートリアル: テキストの書式設定 &#40;レポート ビルダー&#41;](../tutorial-format-text-report-builder.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7f745-110">To quickly get started, see [Tutorial: Format Text &#40;Report Builder&#41;](../tutorial-format-text-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="supported-html-tags"></a><span data-ttu-id="7f745-111">サポートされる HTML タグ</span><span class="sxs-lookup"><span data-stu-id="7f745-111">Supported HTML Tags</span></span>  
 <span data-ttu-id="7f745-112">以下は、プレースホルダー テキストとして定義された場合に HTML として表示されるタグの全リストです。</span><span class="sxs-lookup"><span data-stu-id="7f745-112">The following is a complete list of tags that will render as HTML when defined as placeholder text:</span></span>  
  
-   <span data-ttu-id="7f745-113">ヘッダー、スタイル、およびブロック要素: \<H{n}> 、、 \<DIV> \<SPAN> 、 \<P> 、\<LI></span><span class="sxs-lookup"><span data-stu-id="7f745-113">Header, style and block elements: \<H{n}>, \<DIV>, \<SPAN>,\<P>, \<LI></span></span>  
  
 <span data-ttu-id="7f745-114">レポートの処理中、その他の HTML マークアップ タグはすべて無視されます。</span><span class="sxs-lookup"><span data-stu-id="7f745-114">Any other HTML markup tags will be ignored during report processing.</span></span> <span data-ttu-id="7f745-115">プレースホルダー テキスト内の式で表される HTML が整形式でない場合、プレースホルダーはプレーン テキストに変換されます。</span><span class="sxs-lookup"><span data-stu-id="7f745-115">If the HTML represented by the expression in the placeholder text is not well formed, the placeholder is rendered as plain text.</span></span> <span data-ttu-id="7f745-116">HTML タグの大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="7f745-116">All HTML tags are case-insensitive.</span></span>  
  
 <span data-ttu-id="7f745-117">テキスト ボックスに含まれているテキストが 1 ブロックだけの場合は、ブロック要素を定義するプレースホルダー内の HTML は正しくレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="7f745-117">If the text in your text box contains only one block of text, any HTML in the placeholder that defines block elements will render correctly.</span></span> <span data-ttu-id="7f745-118">しかし、テキスト ボックスに多数のテキスト ブロックがある場合は、HTML タグが無視され、テキストの構造はテキスト ブロックによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="7f745-118">However, if the text box has multiple blocks of text, the HTML tags are ignored and the structure of the text is defined by the blocks of text.</span></span>  
  
 <span data-ttu-id="7f745-119">テキストに複数のタグが定義され、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] で HTML と既存のレポート制約に競合が検出された場合は、一番内側の HTML タグのみが HTML として扱われます。</span><span class="sxs-lookup"><span data-stu-id="7f745-119">If more than one tag is defined for text, and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] detects a conflict between the HTML and existing report constraints, only the innermost HTML tag will be treated as HTML.</span></span>  
  
 <span data-ttu-id="7f745-120">リスト処理のタグを使用する場合、記号と番号のプレフィックスすべてのフォントとスタイルは、Arial black に修正されます。</span><span class="sxs-lookup"><span data-stu-id="7f745-120">When using the list handling tags, the font and style of all bullets and number prefixes will be fixed to Arial black.</span></span>  
  
 <span data-ttu-id="7f745-121">詳細については、「[レポートへの HTML の追加 &#40;レポート ビルダーおよび SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f745-121">For more information, see [Add HTML into a Report &#40;Report Builder and SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md).</span></span>  
  
## <a name="limitations-of-cascading-style-sheet-attributes"></a><span data-ttu-id="7f745-122">カスケード スタイル シート属性の制限</span><span class="sxs-lookup"><span data-stu-id="7f745-122">Limitations of Cascading Style Sheet Attributes</span></span>  
 <span data-ttu-id="7f745-123">カスケード スタイル シート (CSS) 属性を使用する場合、基本的なタグ セットのみが定義されます。</span><span class="sxs-lookup"><span data-stu-id="7f745-123">When using cascading style sheet (CSS) attributes, only a basic set of tags are defined.</span></span> <span data-ttu-id="7f745-124">サポートされている属性の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7f745-124">The following is a list of attributes that are supported:</span></span>  
  
-   <span data-ttu-id="7f745-125">テキストの配置、テキストのインデント</span><span class="sxs-lookup"><span data-stu-id="7f745-125">text-align, text-indent</span></span>  
  
-   <span data-ttu-id="7f745-126">font-family</span><span class="sxs-lookup"><span data-stu-id="7f745-126">font-family</span></span>  
  
-   <span data-ttu-id="7f745-127">font-size</span><span class="sxs-lookup"><span data-stu-id="7f745-127">font-size</span></span>  
  
    -   <span data-ttu-id="7f745-128">CSS の絶対的な長さ単位で表された有効な RDL サイズ値のみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7f745-128">Only valid RDL size values, in absolute CSS length units are supported.</span></span> <span data-ttu-id="7f745-129">サポートされる単位は、in、cm、mm、pt、および pc です。</span><span class="sxs-lookup"><span data-stu-id="7f745-129">Supported units are: in, cm, mm, pt, pc.</span></span>  
  
    -   <span data-ttu-id="7f745-130">CSS の相対的な長さ単位はサポートされず、無視されます。</span><span class="sxs-lookup"><span data-stu-id="7f745-130">Relative CSS length units are ignored and not supported.</span></span> <span data-ttu-id="7f745-131">サポートされない単位は、em、ex、px、%、rem などです。</span><span class="sxs-lookup"><span data-stu-id="7f745-131">Unsupported units include em, ex, px,%,rem.</span></span>  
  
-   <span data-ttu-id="7f745-132">color</span><span class="sxs-lookup"><span data-stu-id="7f745-132">color</span></span>  
  
-   <span data-ttu-id="7f745-133">埋め込み、埋め込みの下部、埋め込みの上部、埋め込みの右側、埋め込みの左</span><span class="sxs-lookup"><span data-stu-id="7f745-133">padding, padding-bottom, padding-top, padding-right, padding-left</span></span>  
  
-   <span data-ttu-id="7f745-134">フォントの太さ</span><span class="sxs-lookup"><span data-stu-id="7f745-134">font-weight</span></span>  
  
 <span data-ttu-id="7f745-135">以下は、CSS を使用するときの注意点です。</span><span class="sxs-lookup"><span data-stu-id="7f745-135">Here are some considerations for using CSS:</span></span>  
  
-   <span data-ttu-id="7f745-136">不正な HTML と同様に不正な CSS 値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="7f745-136">Malformed CSS values are ignored in the same way as malformed HTML.</span></span>  
  
-   <span data-ttu-id="7f745-137">同じタグに属性と CSS スタイル属性の両方がある場合は、CSS プロパティの方が優先順位が高くなります。</span><span class="sxs-lookup"><span data-stu-id="7f745-137">When both attribute and CSS style attributes exist in the same tag, the CSS property has a higher precedence.</span></span> <span data-ttu-id="7f745-138">たとえば、テキストがの場合、 **\<p style="text-align: right" align="left">** テキストの整列属性のみが適用され、テキストは右揃えになります。</span><span class="sxs-lookup"><span data-stu-id="7f745-138">For example, if your text is **\<p style="text-align: right" align="left">**, only the text-align attribute will be applied and the text will be right-aligned.</span></span>  
  
-   <span data-ttu-id="7f745-139">属性と CSS スタイルでは、プロパティが 2 回以上指定されている場合、最後のインスタンスのみが適用されます。</span><span class="sxs-lookup"><span data-stu-id="7f745-139">For attributes and CSS styles, if a property is specified more than once, only the last instance of the property is applied.</span></span> <span data-ttu-id="7f745-140">たとえば、テキストがの場合、 **\<p align="left" align="right">** テキストは右に配置されます。</span><span class="sxs-lookup"><span data-stu-id="7f745-140">For example, if your text is **\<p align="left" align="right">**, the text will be right-aligned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f745-141">参照</span><span class="sxs-lookup"><span data-stu-id="7f745-141">See Also</span></span>  
 [<span data-ttu-id="7f745-142">HTML での表示 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7f745-142">Rendering to HTML &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/rendering-to-html-report-builder-and-ssrs.md)  
  
  
