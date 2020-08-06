---
title: レポートまたはテキスト ボックスのロケールの設定 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- locales [Reporting Services]
ms.assetid: df115b01-184b-47f0-b5ec-0ad965ff9bee
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bb2b0cbd6e4216138520834216358ee455729386
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632895"
---
# <a name="set-the-locale-for-a-report-or-text-box-reporting-services"></a><span data-ttu-id="4be04-102">レポートまたはテキスト ボックスのロケールの設定 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="4be04-102">Set the Locale for a Report or Text Box (Reporting Services)</span></span>
  <span data-ttu-id="4be04-103">レポートまたはテキスト ボックスの **Language** プロパティでは、ローカル設定を指定します。ローカル設定は、言語や地域ごとに異なるレポート データ (日付、通貨、数値など) を表示するための既定の形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="4be04-103">The **Language** property on a report or a text box contains the locale setting, which determines the default formats for displaying report data that differ by language and region, for example, date, currency, or number values.</span></span> <span data-ttu-id="4be04-104">テキスト ボックスの **Language** プロパティは、レポートの **Language** プロパティをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="4be04-104">The **Language** property on a text box overrides the **Language** property on the report.</span></span> <span data-ttu-id="4be04-105">**Language**プロパティに値が指定されてない場合、Reporting Services は、パブリッシュされたレポートのレポート サーバーの OS のロケールか、またはレポート プレビューを行うレポート作成コンピューターのロケールを使用します。</span><span class="sxs-lookup"><span data-stu-id="4be04-105">If no value is specified for **Language**, Reporting Services uses the locale of the operating system on the report server for published reports or of the report authoring computer for report preview.</span></span>  
  
 <span data-ttu-id="4be04-106">HTML レポートの場合、既定の **Language** 値をオーバーライドし、ブラウザー クライアントの HTTP ヘッダーで指定している言語を使用できます。この操作を行うには、レポートまたはテキスト ボックスの **Language** プロパティの式で組み込みフィールド User!Language を使用します。</span><span class="sxs-lookup"><span data-stu-id="4be04-106">For HTML reports, you can override the default **Language** value and use the language specified by the HTTP header of the browser client by using the built-in field User!Language in an expression for the **Language** property of a report or a text box.</span></span>  
  
 <span data-ttu-id="4be04-107">レポートの **Language** プロパティを URL で指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="4be04-107">You can also specify the **Language** property for a report in a URL.</span></span> <span data-ttu-id="4be04-108">詳細については、「 [URL でレポート パラメーターの言語を設定する](../set-the-language-for-report-parameters-in-a-url.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4be04-108">For more information, see [Set the Language for Report Parameters in a URL](../set-the-language-for-report-parameters-in-a-url.md).</span></span>  
  
### <a name="to-set-the-locale-for-a-report"></a><span data-ttu-id="4be04-109">レポートのロケールを設定するには</span><span class="sxs-lookup"><span data-stu-id="4be04-109">To set the locale for a report</span></span>  
  
1.  <span data-ttu-id="4be04-110">デザイン ビューで、レポートのデザイン画面の外側をクリックして、レポートを選択します。</span><span class="sxs-lookup"><span data-stu-id="4be04-110">In Design view, click outside the report design surface to select the report.</span></span>  
  
2.  <span data-ttu-id="4be04-111">プロパティ ペインの **[Language]** プロパティで、レポートに使用する言語を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="4be04-111">In the Properties pane, for the **Language** property, type or select the language that you want to use for the report.</span></span>  
  
### <a name="to-set-the-locale-for-a-text-box"></a><span data-ttu-id="4be04-112">テキスト ボックスのロケールを設定するには</span><span class="sxs-lookup"><span data-stu-id="4be04-112">To set the locale for a text box</span></span>  
  
1.  <span data-ttu-id="4be04-113">デザイン ビューで、ロケール設定を適用するテキスト ボックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="4be04-113">In Design view, select the text box to which you want to apply the locale settings.</span></span>  
  
2.  <span data-ttu-id="4be04-114">プロパティ ペインで、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="4be04-114">In the Properties pane, do the following:</span></span>  
  
    -   <span data-ttu-id="4be04-115">**[Calendar]** プロパティで、日付に使用するカレンダーを入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="4be04-115">For the **Calendar** property, type or select the calendar that you want to use for dates.</span></span>  
  
    -   <span data-ttu-id="4be04-116">**[Direction]** プロパティで、テキストを記述する方向を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="4be04-116">For the **Direction** property, type or select the direction in which the text is written.</span></span>  
  
    -   <span data-ttu-id="4be04-117">**[Language]** プロパティで、テキスト ボックスに使用する言語を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="4be04-117">For the **Language** property, type or select the language that you want to use for the text box.</span></span> <span data-ttu-id="4be04-118">この値は、レポートの **Language** プロパティをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="4be04-118">This value overrides the **Language** property for the Report.</span></span>  
  
    -   <span data-ttu-id="4be04-119">**[NumeralLanguage]** プロパティで、テキスト ボックスの数字に使用する形式を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="4be04-119">For the **NumeralLanguage** property, type or select the format to use for numbers in the text box.</span></span>  
  
    -   <span data-ttu-id="4be04-120">**[NumeralVariant]** プロパティで、テキスト ボックスの数字に使用する形式の変化形を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="4be04-120">For the **NumeralVariant** property, type or select the variant of the format to use for numbers in the text box.</span></span>  
  
    -   <span data-ttu-id="4be04-121">**[UnicodeBiDi]** プロパティで、テキスト ボックスで使用する双方向の埋め込みレベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="4be04-121">For the **UnicodeBiDi** property, select the level of bidirectional embedding to use in the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4be04-122">参照</span><span class="sxs-lookup"><span data-stu-id="4be04-122">See Also</span></span>  
 [<span data-ttu-id="4be04-123">レポートでの式の使用 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="4be04-123">Expression Uses in Reports &#40;Report Builder and SSRS&#41;</span></span>](expression-uses-in-reports-report-builder-and-ssrs.md)  
  
  
