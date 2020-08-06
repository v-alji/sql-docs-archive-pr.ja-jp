---
title: 数値と日付の書式設定 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.placeholderproperties.number.f1
- sql12.rtp.rptdesigner.serieslabelproperties.number.f1
- "10127"
- sql12.rtp.rptdesigner.axisproperties.number.f1
- "10130"
- "10286"
- sql12.rtp.rptdesigner.textboxproperties.number.f1
- "10285"
ms.assetid: 6de1a725-9f06-4708-be26-2d55e442e344
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 597ff535e72bc174cc6f9bd5a226e95641ba8a4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711697"
---
# <a name="formatting-numbers-and-dates-report-builder-and-ssrs"></a><span data-ttu-id="5fa67-102">数値と日付の書式設定 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="5fa67-102">Formatting Numbers and Dates (Report Builder and SSRS)</span></span>
  <span data-ttu-id="5fa67-103">データ領域の数値と日付の書式を設定するには、対応するデータ領域の **[プロパティ]** ダイアログ ボックスの **[数値]** ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="5fa67-103">You can format numbers and dates in data regions by selecting a format from the **Number** page of the corresponding data region's **Properties** dialog box.</span></span>  
  
 <span data-ttu-id="5fa67-104">テキスト ボックスのレポート アイテム内の書式文字列を指定するには、書式を設定するアイテムを選択して右クリックし、 **[テキスト ボックスのプロパティ]** を選択してから **[数値]** をクリックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5fa67-104">To specify format strings within a text box report item, you need to select the item that you want to format, right-click, select **Text Box Properties**, and then click **Number**.</span></span> <span data-ttu-id="5fa67-105">テーブルまたはマトリックスのセルは個別のテキスト ボックスであるため、同じ方法でテーブル データ領域またはマトリックス データ領域の個別のセルを書式設定できます。</span><span class="sxs-lookup"><span data-stu-id="5fa67-105">You can format individual cells in a table or matrix data region in the same manner, because cells in a table or matrix are individual text boxes.</span></span>  
  
 <span data-ttu-id="5fa67-106">グラフ データ領域では、通常、カテゴリ軸 (x 軸) に日付が示され、値軸 (y 軸) に値が示されます。</span><span class="sxs-lookup"><span data-stu-id="5fa67-106">A chart data region commonly shows dates along the category (x) axis, and values along the value (y) axis.</span></span> <span data-ttu-id="5fa67-107">グラフの書式を指定するには、軸を右クリックし、 **[軸のプロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5fa67-107">To specify formatting in a chart, right-click an axis and select **Axis Properties**.</span></span> <span data-ttu-id="5fa67-108">値軸では、数値の書式しか指定できません。</span><span class="sxs-lookup"><span data-stu-id="5fa67-108">On the value axis, you can specify formats only for numbers.</span></span> <span data-ttu-id="5fa67-109">詳細については、「[グラフの軸ラベルの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fa67-109">For more information, see [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="5fa67-110">ゲージのデータ領域で書式を指定するには、ゲージのスケールを右クリックし、 **[放射状のスケールのプロパティ]** または **[線形スケールのプロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5fa67-110">To specify formatting in a Gauge data region, right-click the scale of the gauge and select **Radial Scale Properties** or **Linear Scale Properties**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5fa67-111">目的の書式設定オプションがグレー表示されている場合、その書式設定オプションと、データ ソースに設定されているフィールドのデータ型に互換性がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="5fa67-111">If some formatting options you want to use are grayed out, it means that those formatting options are not compatible the field's data type, which is set in the data source.</span></span> <span data-ttu-id="5fa67-112">たとえば、フィールドに格納されているデータが数値であっても、フィールドのデータ型が文字列である場合、通貨型や 10 進数型などの数値データ書式設定オプションを適用できません。</span><span class="sxs-lookup"><span data-stu-id="5fa67-112">For example, if the field contains number values but the field's data type is String, you cannot apply numerical data formatting options such as currency or decimals.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="considerations-for-formatting-numbers-and-dates"></a><span data-ttu-id="5fa67-113">数値および日付の書式設定に関する注意点</span><span class="sxs-lookup"><span data-stu-id="5fa67-113">Considerations for Formatting Numbers and Dates</span></span>  
 <span data-ttu-id="5fa67-114">レポートの数値および日付の書式を設定する前に、次のことを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="5fa67-114">Before you format numbers and dates in your report, consider the following:</span></span>  
  
-   <span data-ttu-id="5fa67-115">既定では、数値の書式はクライアント コンピューターのカルチャ設定を反映して設定されます。</span><span class="sxs-lookup"><span data-stu-id="5fa67-115">By default, numbers are formatted to reflect the cultural settings on the client computer.</span></span> <span data-ttu-id="5fa67-116">数値の表示方法を指定するために書式設定の文字列を使用すると、レポートを参照するユーザーの地域に関係なく、一貫した書式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5fa67-116">Use formatting strings to specify how numbers are displayed so that formatting is consistent regardless of where the person who is viewing the report is located.</span></span>  
  
-   <span data-ttu-id="5fa67-117">**[数値]** ページで指定された書式は、 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 標準の数値書式設定文字列のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="5fa67-117">The formats provided on the **Number** page are a subset of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] standard numeric format strings.</span></span> <span data-ttu-id="5fa67-118">ダイアログ ボックスに表示されないカスタム書式を使用して数値や日付の書式を設定するには、数値または日付の [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 書式設定文字列を使用します。</span><span class="sxs-lookup"><span data-stu-id="5fa67-118">To format a number or date using a custom format that is not shown in the dialog box, you can use any [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] format strings for numbers or dates.</span></span> <span data-ttu-id="5fa67-119">カスタム書式設定文字列の詳細については、MSDN のトピック「 [型の書式設定](https://go.microsoft.com/fwlink/?LinkId=112024) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fa67-119">For more information about custom format strings, see the [Formatting Types](https://go.microsoft.com/fwlink/?LinkId=112024) topic on MSDN.</span></span>  
  
-   <span data-ttu-id="5fa67-120">カスタム書式設定文字列が指定されている場合、既定のカルチャ固有の設定よりも優先度が高くなります。</span><span class="sxs-lookup"><span data-stu-id="5fa67-120">If a custom format string has been specified, it has a higher priority over default settings that are culture-specific.</span></span> <span data-ttu-id="5fa67-121">たとえば、カスタム書式設定文字列 "#,###" を設定して、数値 1234 を 1,234 と表すとします。</span><span class="sxs-lookup"><span data-stu-id="5fa67-121">For example, suppose you set a custom format string of "#,###" to show the number 1234 as 1,234.</span></span> <span data-ttu-id="5fa67-122">これは、米国のユーザーとヨーロッパのユーザーで意味が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5fa67-122">This may have different meaning to users in the United States than it does to users in Europe.</span></span> <span data-ttu-id="5fa67-123">カスタム書式設定を指定する前に、レポートを参照する異なるカルチャのユーザーに対して選択した書式設定がどのような影響を与えるか考慮するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="5fa67-123">Before you specify a custom format, consider how the format you choose will affect users of different cultures who may view the report.</span></span>  
  
-   <span data-ttu-id="5fa67-124">指定した書式設定文字列が正しくない場合、書式設定されたテキストは、書式設定をオーバーライドするリテラル文字列として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="5fa67-124">If you specify an invalid format string, the formatted text is interpreted as a literal string which overrides the formatting.</span></span>  
  
-   <span data-ttu-id="5fa67-125">同じテキスト ボックスで数字と文字が混在するテキストの書式を設定する場合、プレースホルダーを使用して、テキストの数値以外の部分とは別に数値の書式を設定します。</span><span class="sxs-lookup"><span data-stu-id="5fa67-125">If you are formatting a mix of numbers and characters in the same text box, consider using a placeholder to format the number separately from the rest of the text.</span></span> <span data-ttu-id="5fa67-126">詳細については、「 [テキストとプレースホルダーの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fa67-126">For more information, see [Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="5fa67-127">テキスト ボックスで Format プロパティについて指定された書式設定文字列が正しくない場合、書式設定文字列は無視されます。</span><span class="sxs-lookup"><span data-stu-id="5fa67-127">If an invalid format string is specified for the Format property on the text box, the format string is ignored.</span></span> <span data-ttu-id="5fa67-128">グラフまたはゲージで Format プロパティについて指定された書式設定文字列が正しくない場合、指定した書式設定文字列は文字列として解釈され、書式設定は適用されません。</span><span class="sxs-lookup"><span data-stu-id="5fa67-128">If an invalid format string is specified for the Format property on the chart or gauge, the format string that you specified is interpreted as a string and formatting is not applied.</span></span>  
  
-   <span data-ttu-id="5fa67-129">**[カテゴリ]** の **[通貨]** をクリックして、 **[値の表示単位]** をオンにすると、 **[千]** 、 **[百万]** 、または **[十億]** を選択し、財務上の形式を使用して数値を表示できます。</span><span class="sxs-lookup"><span data-stu-id="5fa67-129">If you select **Currency** under **Category** and you check **Show values in**, you can select **Thousands**, **Millions**, or **Billions** to display numbers using financial formats.</span></span> <span data-ttu-id="5fa67-130">たとえば、フィールド値が 1,789,905,394 の場合、 **[十億]** を選択して、小数点以下桁数を 2 桁に指定すると、レポートに表示される値は 1.78 です。</span><span class="sxs-lookup"><span data-stu-id="5fa67-130">For example, if the field value is 1,789,905,394 and you select **Billions** and specify 2 decimal places, the value displayed in the report is 1.78.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fa67-131">参照</span><span class="sxs-lookup"><span data-stu-id="5fa67-131">See Also</span></span>  
 <span data-ttu-id="5fa67-132">[テキストとプレースホルダーの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5fa67-132">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5fa67-133">[線、色、および画像の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5fa67-133">[Formatting Lines, Colors, and Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5fa67-134">[グラフの書式設定 (レポート ビルダーおよび SSRS)](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5fa67-134">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5fa67-135">[日付または通貨として軸ラベルを書式設定する &#40;レポート ビルダーおよび SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5fa67-135">[Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="5fa67-136">ゲージのスケールの書式設定 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="5fa67-136">Formatting Scales on a Gauge &#40;Report Builder and SSRS&#41;</span></span>](formatting-scales-on-a-gauge-report-builder-and-ssrs.md)  
  
  
