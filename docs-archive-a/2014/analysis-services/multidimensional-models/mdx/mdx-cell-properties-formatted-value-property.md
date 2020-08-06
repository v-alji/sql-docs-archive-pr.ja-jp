---
title: FORMATED_VALUE の言語と FORMAT_STRING |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7534ff5f-954e-47d4-a2ed-4b5b8ccb30e6
author: minewiskan
ms.author: owend
ms.openlocfilehash: ba4aacbbd440da6048680054771c86c40ef96daa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631269"
---
# <a name="language-and-format_string-on-formated_value"></a><span data-ttu-id="7a6ab-102">FORMATED_VALUE の LANGUAGE と FORMAT_STRING</span><span class="sxs-lookup"><span data-stu-id="7a6ab-102">LANGUAGE and FORMAT_STRING on FORMATED_VALUE</span></span>
  <span data-ttu-id="7a6ab-103">FORMATTED_VALUE プロパティは、セルの VALUE、FORMAT_STRING、および LANGUAGE の各プロパティの相互作用に基づいて構築されます。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-103">The FORMATTED_VALUE property is built on the interactions of the VALUE, FORMAT_STRING and LANGUAGE properties of the cell.</span></span> <span data-ttu-id="7a6ab-104">このトピックではそのしくみについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-104">This topic explains how these properties interact to build the FORMATTED_VALUE property.</span></span>  
  
## <a name="value-format_string-language-properties"></a><span data-ttu-id="7a6ab-105">VALUE プロパティ、FORMAT_STRING プロパティ、LANGUAGE プロパティ</span><span class="sxs-lookup"><span data-stu-id="7a6ab-105">VALUE, FORMAT_STRING, LANGUAGE properties</span></span>  
 <span data-ttu-id="7a6ab-106">これらのプロパティを組み合わせて使用するための準備として、次の表に各プロパティの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-106">The following table explains what these properties are, to help prepare us to use them in combination.</span></span>  
  
 <span data-ttu-id="7a6ab-107">値</span><span class="sxs-lookup"><span data-stu-id="7a6ab-107">VALUE</span></span>  
 <span data-ttu-id="7a6ab-108">書式設定されていないセルの値。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-108">The unformatted value of the cell.</span></span>  
  
 <span data-ttu-id="7a6ab-109">FORMAT_STRING</span><span class="sxs-lookup"><span data-stu-id="7a6ab-109">FORMAT_STRING</span></span>  
 <span data-ttu-id="7a6ab-110">FORMATTED_VALUE プロパティを生成するためにセルの値に適用される書式設定テンプレート</span><span class="sxs-lookup"><span data-stu-id="7a6ab-110">The formatting template to be applied to the value of the cell to generate FORMATTED_VALUE property</span></span>  
  
 <span data-ttu-id="7a6ab-111">LANGUAGE</span><span class="sxs-lookup"><span data-stu-id="7a6ab-111">LANGUAGE</span></span>  
 <span data-ttu-id="7a6ab-112">ローカライズされたバージョンの FORMATTED_VALUE を生成するために FORMAT_STRING と共に適用されるロケールの指定</span><span class="sxs-lookup"><span data-stu-id="7a6ab-112">The locale specification to be applied alongside FORMAT_STRING to generate a localized version of FORMATTED_VALUE</span></span>  
  
## <a name="formatted_value-constructed"></a><span data-ttu-id="7a6ab-113">FORMATTED_VALUE の構築</span><span class="sxs-lookup"><span data-stu-id="7a6ab-113">FORMATTED_VALUE constructed</span></span>  
 <span data-ttu-id="7a6ab-114">FORMATTED_VALUE プロパティは、FORMAT_STRING プロパティで指定されている書式設定テンプレートを VALUE プロパティの値に適用することによって構築されます。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-114">The FORMATTED_VALUE property is constructed by using the value from the VALUE property and applying the format template specified in the FORMAT_STRING property to that value.</span></span> <span data-ttu-id="7a6ab-115">また、書式設定値が `named formatting literal` の場合は、LANGUAGE プロパティで指定されている言語の用法に従って FORMAT_STRING の出力が変更されます。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-115">In addition, whenever the formatting value is a `named formatting literal` the LANGUAGE property specification modifies the output of FORMAT_STRING to follow the language usage for the named formatting.</span></span> <span data-ttu-id="7a6ab-116">名前付き書式設定リテラルはすべてローカライズできるように定義されています。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-116">Named formatting literals are all defined in a way that can be localized.</span></span> <span data-ttu-id="7a6ab-117">たとえば `"General Date"` はローカライズ可能な指定ですが、 `"YYYY-MM-DD hh:nn:ss",` は、言語の指定に関係なくこの定義のとおりに日付を表示するように指定するテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-117">For example, `"General Date"` is a specification that can be localized, as opposed to the following template `"YYYY-MM-DD hh:nn:ss",` which states that the date is to be presented as defined by the template regardless of the language specification.</span></span>  
  
 <span data-ttu-id="7a6ab-118">FORMAT_STRING のテンプレートと LANGUAGE の指定が競合している場合は、FORMAT_STRING のテンプレートが LANGUAGE の指定をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-118">If there is a conflict between the FORMAT_STRING template and the LANGUAGE specification, the FORMAT_STRING template overrides the LANGUAGE specification.</span></span> <span data-ttu-id="7a6ab-119">たとえば、FORMAT_STRING="$ #0"、LANGUAGE=1034 (スペイン)、VALUE=123.456 の場合、書式設定テンプレートの値が言語の指定よりもオーバーライドされるため、FORMATTED_VALUE="€ 123" (予想される書式) ではなく FORMATTED_VALUE="$ 123" になります。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-119">For example, if FORMAT_STRING="$ #0" and LANGUAGE=1034 (Spain), and VALUE=123.456 then FORMATTED_VALUE="$ 123" instead of FORMATTED_VALUE="€ 123", the expected format is in Euros, because the value of the format template overrides the language specified.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="7a6ab-120">例</span><span class="sxs-lookup"><span data-stu-id="7a6ab-120">Examples</span></span>  
 <span data-ttu-id="7a6ab-121">以下の例は、LANGUAGE と FORMAT_STRING を組み合わせて使用した場合に得られる出力を示しています。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-121">The following examples show the output obtained when LANGUAGE is used in conjunction with FORMAT_STRING.</span></span>  
  
 <span data-ttu-id="7a6ab-122">1 つ目の例は数値の書式設定の例で、2 つ目の例は日付と時刻の値の書式設定の例です。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-122">The first example explains formatting numerical values; the second example explains formatting date and time values.</span></span>  
  
 <span data-ttu-id="7a6ab-123">それぞれの例について多次元式 (MDX) コードが示されています。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-123">For each example the Multidimensional Expressions (MDX) code is given.</span></span>  
  
 `with`  
  
 `member measures.A as 5040, FORMAT_STRING="Currency"`  
  
 `member measures.B as measures.A, LANGUAGE=1034`  
  
 `member measures.C as measures.A, LANGUAGE=1034 , FORMAT_STRING="$#,##0.00"`  
  
 `member measures.D as measures.A, FORMAT_STRING="Scientific"`  
  
 `member measures.E as measures.A, LANGUAGE=1034 , FORMAT_STRING="Scientific"`  
  
 `member measures.F as 0.5040, FORMAT_STRING="Percent"`  
  
 `member measures.G as measures.F, LANGUAGE=1034`  
  
 `member measures.H as 0, LANGUAGE=1034 , FORMAT_STRING="Yes/No"`  
  
 `member measures.I as 59, LANGUAGE=1034 , FORMAT_STRING="Yes/No"`  
  
 `member measures.J as 0, LANGUAGE=1034 , FORMAT_STRING="ON/OFF"`  
  
 `member measures.K as -312, LANGUAGE=1034 , FORMAT_STRING="ON/OFF"`  
  
 `Select {measures.A, measures.B, measures.C, measures.D, measures.E, measures.F, measures.G, measures.H, measures.I, measures.J, measures.K} on 0`  
  
 `from [Adventure Works]`  
  
 `cell properties VALUE, FORMAT_STRING, LANGUAGE, FORMATTED_VALUE`  
  
 <span data-ttu-id="7a6ab-124">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] を使用して上の MDX クエリをロケール 1033 のサーバーとクライアントで実行すると、結果 (置き換え後) は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-124">The results, transposed, when the above MDX query was run using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] over a server and client with locale 1033 are as follows:</span></span>  
  
|<span data-ttu-id="7a6ab-125">メンバー</span><span class="sxs-lookup"><span data-stu-id="7a6ab-125">Member</span></span>|<span data-ttu-id="7a6ab-126">FORMATTED_VALUE</span><span class="sxs-lookup"><span data-stu-id="7a6ab-126">FORMATTED_VALUE</span></span>|<span data-ttu-id="7a6ab-127">説明</span><span class="sxs-lookup"><span data-stu-id="7a6ab-127">Explanation</span></span>|  
|------------|----------------------|-----------------|  
|<span data-ttu-id="7a6ab-128">A</span><span class="sxs-lookup"><span data-stu-id="7a6ab-128">A</span></span>|<span data-ttu-id="7a6ab-129">$5,040.00</span><span class="sxs-lookup"><span data-stu-id="7a6ab-129">$5,040.00</span></span>|<span data-ttu-id="7a6ab-130">FORMAT_STRING が `Currency` に設定され、LANGUAGE が `1033`に設定されています (システム ロケール値から継承)。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-130">FORMAT_STRING is set to `Currency` and LANGUAGE is `1033`, inherited from system locale value</span></span>|  
|<span data-ttu-id="7a6ab-131">B</span><span class="sxs-lookup"><span data-stu-id="7a6ab-131">B</span></span>|<span data-ttu-id="7a6ab-132">€5.040,00</span><span class="sxs-lookup"><span data-stu-id="7a6ab-132">€5.040,00</span></span>|<span data-ttu-id="7a6ab-133">FORMAT_STRING が `Currency` に設定され (A から継承)、LANGUAGE が明示的に `1034` (スペイン) に設定されています。したがって、ユーロ記号が使用され、小数点と桁の区切り文字も変わっています。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-133">FORMAT_STRING is set to `Currency` (inherited from A) and LANGUAGE is explicitly set to `1034` (Spain) hence the Euro sign, the different decimal separator and the different thousand separator.</span></span>|  
|<span data-ttu-id="7a6ab-134">C</span><span class="sxs-lookup"><span data-stu-id="7a6ab-134">C</span></span>|<span data-ttu-id="7a6ab-135">$5.040,00</span><span class="sxs-lookup"><span data-stu-id="7a6ab-135">$5.040,00</span></span>|<span data-ttu-id="7a6ab-136">FORMAT_STRING が `$#,##0.00` に設定されて、A から継承された Currency がオーバーライドされています。LANGUAGE は明示的に `1034` (スペイン) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-136">FORMAT_STRING is set to `$#,##0.00` an override to Currency, from A, and LANGUAGE is explicitly set to `1034` (Spain).</span></span> <span data-ttu-id="7a6ab-137">FORMAT_STRING プロパティで通貨記号が明示的に $ に設定されているため、FORMATTED_VALUE には $ 記号が付いています。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-137">Because the FORMAT_STRING property explicitly set the currency symbol to $, the FORMATTED_VALUE is presented with the $ sign.</span></span> <span data-ttu-id="7a6ab-138">一方、 `.` (ドット) と `,` (コンマ) はそれぞれ小数点区切り文字と桁区切り文字のプレースホルダーであるため、言語の指定の影響を受けます。したがって、小数点と桁の区切り文字がローカライズされた出力が生成されています。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-138">However, because `.` (dot) and `,` (comma) are placeholders for decimal separator and thousand separator respectively, the language specification affects them generating an output that is localized for decimal and thousand separators.</span></span>|  
|<span data-ttu-id="7a6ab-139">D</span><span class="sxs-lookup"><span data-stu-id="7a6ab-139">D</span></span>|<span data-ttu-id="7a6ab-140">5.04E+03</span><span class="sxs-lookup"><span data-stu-id="7a6ab-140">5.04E+03</span></span>|<span data-ttu-id="7a6ab-141">FORMAT_STRING が `Scientific` に設定され、LANGUAGE が `1033`に設定されています (システム ロケール値から継承)。したがって、小数点区切り文字が `.` (ドット) になっています。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-141">FORMAT_STRING is set to `Scientific` and LANGUAGE is set to `1033`, inherited from system locale value, hence `.` (dot) is the decimal separator.</span></span>|  
|<span data-ttu-id="7a6ab-142">E</span><span class="sxs-lookup"><span data-stu-id="7a6ab-142">E</span></span>|<span data-ttu-id="7a6ab-143">5,04E+03</span><span class="sxs-lookup"><span data-stu-id="7a6ab-143">5,04E+03</span></span>|<span data-ttu-id="7a6ab-144">FORMAT_STRING が `Scientific` に設定され、LANGUAGE が明示的に `1034,` に設定されています。したがって、小数点区切り文字が `,` (コンマ) になっています。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-144">FORMAT_STRING is set to `Scientific` and LANGUAGE is set explicitly to `1034,` hence `,` (comma) is the decimal separator.</span></span>|  
|<span data-ttu-id="7a6ab-145">F</span><span class="sxs-lookup"><span data-stu-id="7a6ab-145">F</span></span>|<span data-ttu-id="7a6ab-146">50.40%</span><span class="sxs-lookup"><span data-stu-id="7a6ab-146">50.40%</span></span>|<span data-ttu-id="7a6ab-147">FORMAT_STRING が `Percent` に設定され、LANGUAGE が `1033`に設定されています (システム ロケール値から継承)。したがって、小数点区切り文字が `.` (ドット) になっています。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-147">FORMAT_STRING is set to `Percent` and LANGUAGE is set to `1033`, inherited from system locale value, hence `.` (dot) is the decimal separator.</span></span><br /><br /> <span data-ttu-id="7a6ab-148">VALUE が 5040 から 0.5040 に変更されたことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-148">Note that VALUE was changed from 5040 to 0.5040</span></span>|  
|<span data-ttu-id="7a6ab-149">G</span><span class="sxs-lookup"><span data-stu-id="7a6ab-149">G</span></span>|<span data-ttu-id="7a6ab-150">50,40%</span><span class="sxs-lookup"><span data-stu-id="7a6ab-150">50,40%</span></span>|<span data-ttu-id="7a6ab-151">FORMAT_STRING が `Percent`に設定され (F から継承)、LANGUAGE が明示的に `1034` に設定されています。したがって、小数点区切り文字が `,` (コンマ) になっています。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-151">FORMAT_STRING is set to `Percent`, inherited from F, and LANGUAGE is set explicitly to `1034` hence `,` (comma) is the decimal separator.</span></span><br /><br /> <span data-ttu-id="7a6ab-152">VALUE が F の値から継承されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-152">Note that VALUE was inherited from F value.</span></span>|  
|<span data-ttu-id="7a6ab-153">H</span><span class="sxs-lookup"><span data-stu-id="7a6ab-153">H</span></span>|<span data-ttu-id="7a6ab-154">いいえ</span><span class="sxs-lookup"><span data-stu-id="7a6ab-154">No</span></span>|<span data-ttu-id="7a6ab-155">FORMAT_STRING が `YES/NO`に設定され、VALUE が 0 に設定され、LANGUAGE が明示的に `1034`に設定されています。英語の NO とスペイン語の NO は変わらないため、FORMATTED_VALUE には目に見える違いはありません。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-155">FORMAT_STRING is set to `YES/NO`, VALUE is set to 0 and LANGUAGE is set explicitly to `1034`; because there is no difference between English NO and Spanish NO the user sees no difference in the FORMATTED_VALUE.</span></span>|  
|<span data-ttu-id="7a6ab-156">I</span><span class="sxs-lookup"><span data-stu-id="7a6ab-156">I</span></span>|<span data-ttu-id="7a6ab-157">SI</span><span class="sxs-lookup"><span data-stu-id="7a6ab-157">SI</span></span>|<span data-ttu-id="7a6ab-158">FORMAT_STRING が `YES/NO`に設定され、VALUE が 59 に設定され、LANGUAGE が明示的に `1034`に設定されています。YES/NO の書式設定の定義ではゼロ (0) 以外の値はすべて YES になり、ここでは言語がスペイン語に設定されているため、FORMATTED_VALUE は SI になります。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-158">FORMAT_STRING is set to `YES/NO`, VALUE is set to 59 and LANGUAGE is set explicitly to `1034`; as defined for YES/NO formatting, any value different from zero (0) is a YES and because language is set to Spanish then the FORMATTED_VALUE is SI.</span></span>|  
|<span data-ttu-id="7a6ab-159">J</span><span class="sxs-lookup"><span data-stu-id="7a6ab-159">J</span></span>|<span data-ttu-id="7a6ab-160">Desactivado</span><span class="sxs-lookup"><span data-stu-id="7a6ab-160">Desactivado</span></span>|<span data-ttu-id="7a6ab-161">FORMAT_STRING が `ON/OFF`に設定され、VALUE が 0 に設定され、LANGUAGE が明示的に `1034`に設定されています。ON/OFF の書式設定の定義では値がゼロ (0) と等しい場合は OFF になり、ここでは言語がスペイン語に設定されているため、FORMATTED_VALUE は Desactivado になります。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-161">FORMAT_STRING is set to `ON/OFF`, VALUE is set to 0 and LANGUAGE is set explicitly to `1034`; as defined for ON/OFF formatting, any value equal to zero (0) is an OFF and because language is set to Spanish then the FORMATTED_VALUE is Desactivado.</span></span>|  
|<span data-ttu-id="7a6ab-162">K</span><span class="sxs-lookup"><span data-stu-id="7a6ab-162">K</span></span>|<span data-ttu-id="7a6ab-163">Activado</span><span class="sxs-lookup"><span data-stu-id="7a6ab-163">Activado</span></span>|<span data-ttu-id="7a6ab-164">FORMAT_STRING が `ON/OFF`に設定され、VALUE が -312 に設定され、LANGUAGE が明示的に `1034`に設定されています。ON/OFF の書式設定の定義ではゼロ (0) 以外の値はすべて ON になり、ここでは言語がスペイン語に設定されているため、FORMATTED_VALUE は Activado になります。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-164">FORMAT_STRING is set to `ON/OFF`, VALUE is set to -312 and LANGUAGE is set explicitly to `1034`; as defined for ON/OFF formatting, any value different from zero (0) is an ON and because language is set to Spanish then the FORMATTED_VALUE is Activado.</span></span>|  
  
 `with`  
  
 `member measures.A as 'CDate("1959-03-12 06:30")'`  
  
 `member measures.B as measures.A, FORMAT_STRING="Long Date"`  
  
 `member measures.C as measures.A, LANGUAGE=1034 , FORMAT_STRING="General Date"`  
  
 `member measures.D as measures.A, LANGUAGE=1034, FORMAT_STRING="Long Date"`  
  
 `member measures.E as measures.A, LANGUAGE=1041 , FORMAT_STRING="General Date"`  
  
 `member measures.F as measures.A, LANGUAGE=1041 , FORMAT_STRING="Long Date"`  
  
 `member measures.G as measures.A, FORMAT_STRING="Long Time"`  
  
 `member measures.H as measures.A, FORMAT_STRING="Short Time"`  
  
 `member measures.I as measures.A, LANGUAGE=1034 , FORMAT_STRING="Long Time"`  
  
 `member measures.J as measures.A, LANGUAGE=1034 , FORMAT_STRING="Short Time"`  
  
 `member measures.K as measures.A, LANGUAGE=1041 , FORMAT_STRING="Long Time"`  
  
 `member measures.L as measures.A, LANGUAGE=1041 , FORMAT_STRING="Short Time"`  
  
 `Select {measures.A, measures.B, measures.C, measures.D, measures.E, measures.F`  
  
 `, measures.G, measures.H, measures.I, measures.J, measures.K, measures.L} on 0`  
  
 `from [Adventure Works]`  
  
 `cell properties VALUE, FORMAT_STRING, LANGUAGE, FORMATTED_VALUE`  
  
 <span data-ttu-id="7a6ab-165">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] を使用して上の MDX クエリをロケール 1033 のサーバーとクライアントで実行すると、結果 (置き換え後) は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-165">The results, transposed, when the above MDX query was run using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] over a server and client with locale 1033 are as follows:</span></span>  
  
|<span data-ttu-id="7a6ab-166">メンバー</span><span class="sxs-lookup"><span data-stu-id="7a6ab-166">Member</span></span>|<span data-ttu-id="7a6ab-167">FORMATTED_VALUE</span><span class="sxs-lookup"><span data-stu-id="7a6ab-167">FORMATTED_VALUE</span></span>|<span data-ttu-id="7a6ab-168">説明</span><span class="sxs-lookup"><span data-stu-id="7a6ab-168">Explanation</span></span>|  
|------------|----------------------|-----------------|  
|<span data-ttu-id="7a6ab-169">A</span><span class="sxs-lookup"><span data-stu-id="7a6ab-169">A</span></span>|<span data-ttu-id="7a6ab-170">3/12/1959 6:30:00 AM</span><span class="sxs-lookup"><span data-stu-id="7a6ab-170">3/12/1959 6:30:00 AM</span></span>|<span data-ttu-id="7a6ab-171">FORMAT_STRING が CDate() 式によって暗黙的に `General Date` に設定され、LANGUAGE が `1033` (英語) に設定されています (システム ロケール値から継承)。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-171">FORMAT_STRING is set implicitly to `General Date` by the CDate() expression and LANGUAGE is `1033` (English), inherited from system locale value</span></span>|  
|<span data-ttu-id="7a6ab-172">B</span><span class="sxs-lookup"><span data-stu-id="7a6ab-172">B</span></span>|<span data-ttu-id="7a6ab-173">Thursday, March 12, 1959</span><span class="sxs-lookup"><span data-stu-id="7a6ab-173">Thursday, March 12, 1959</span></span>|<span data-ttu-id="7a6ab-174">FORMAT_STRING が明示的に `Long Date` に設定され、LANGUAGE が `1033` (英語) に設定されています (システム ロケール値から継承)。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-174">FORMAT_STRING is set explicitly to `Long Date` and LANGUAGE is `1033` (English), inherited from system locale value</span></span>|  
|<span data-ttu-id="7a6ab-175">C</span><span class="sxs-lookup"><span data-stu-id="7a6ab-175">C</span></span>|<span data-ttu-id="7a6ab-176">12/03/1959 6:30:00</span><span class="sxs-lookup"><span data-stu-id="7a6ab-176">12/03/1959 6:30:00</span></span>|<span data-ttu-id="7a6ab-177">FORMAT_STRING が明示的に `General Date` に設定され、LANGUAGE が明示的に `1034` (スペイン語) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-177">FORMAT_STRING is set explicitly to `General Date` and LANGUAGE is explicitly `1034` (Spanish).</span></span><br /><br /> <span data-ttu-id="7a6ab-178">月と日の位置が米国の書式スタイルとは逆になっていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-178">Note that month and day are switched when compared to U.S. formatting style</span></span>|  
|<span data-ttu-id="7a6ab-179">D</span><span class="sxs-lookup"><span data-stu-id="7a6ab-179">D</span></span>|<span data-ttu-id="7a6ab-180">jueves, 12 de marzo de 1959</span><span class="sxs-lookup"><span data-stu-id="7a6ab-180">jueves, 12 de marzo de 1959</span></span>|<span data-ttu-id="7a6ab-181">FORMAT_STRING が明示的に `Long Date` に設定され、LANGUAGE が明示的に `1034` (スペイン語) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-181">FORMAT_STRING is set explicitly to `Long Date` and LANGUAGE is explicitly `1034` (Spanish).</span></span><br /><br /> <span data-ttu-id="7a6ab-182">月と曜日がスペイン語になっていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-182">Note that month and day of the week are worded in Spanish</span></span>|  
|<span data-ttu-id="7a6ab-183">E</span><span class="sxs-lookup"><span data-stu-id="7a6ab-183">E</span></span>|<span data-ttu-id="7a6ab-184">1959/03/12 6:30:00</span><span class="sxs-lookup"><span data-stu-id="7a6ab-184">1959/03/12 6:30:00</span></span>|<span data-ttu-id="7a6ab-185">FORMAT_STRING が明示的に `General Date` に設定され、LANGUAGE が明示的に `1041` (日本語) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-185">FORMAT_STRING is set explicitly to `General Date` and LANGUAGE is explicitly `1041` (Japanese).</span></span><br /><br /> <span data-ttu-id="7a6ab-186">日付の書式が "年/月/日 時:分:秒" になったことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-186">Note that the date is now formatted Year/Month/Day Hour:Minutes:Seconds</span></span>|  
|<span data-ttu-id="7a6ab-187">F</span><span class="sxs-lookup"><span data-stu-id="7a6ab-187">F</span></span>|<span data-ttu-id="7a6ab-188">1959年3月12日</span><span class="sxs-lookup"><span data-stu-id="7a6ab-188">1959年3月12日</span></span>|<span data-ttu-id="7a6ab-189">FORMAT_STRING が明示的に `Long Date` に設定され、LANGUAGE が明示的に `1041` (日本語) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-189">FORMAT_STRING is set explicitly to `Long Date` and LANGUAGE is explicitly `1041` (Japanese).</span></span>|  
|<span data-ttu-id="7a6ab-190">G</span><span class="sxs-lookup"><span data-stu-id="7a6ab-190">G</span></span>|<span data-ttu-id="7a6ab-191">6:30:00 AM</span><span class="sxs-lookup"><span data-stu-id="7a6ab-191">6:30:00 AM</span></span>|<span data-ttu-id="7a6ab-192">FORMAT_STRING が明示的に `Long Time` に設定され、LANGUAGE が `1033` (英語) に設定されています (システム ロケール値から継承)。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-192">FORMAT_STRING is set explicitly to `Long Time` and LANGUAGE is `1033` (English), inherited from system locale value.</span></span>|  
|<span data-ttu-id="7a6ab-193">H</span><span class="sxs-lookup"><span data-stu-id="7a6ab-193">H</span></span>|<span data-ttu-id="7a6ab-194">06:30</span><span class="sxs-lookup"><span data-stu-id="7a6ab-194">06:30</span></span>|<span data-ttu-id="7a6ab-195">FORMAT_STRING が明示的に `Short Time` に設定され、LANGUAGE が `1033` (英語) に設定されています (システム ロケール値から継承)。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-195">FORMAT_STRING is set explicitly to `Short Time` and LANGUAGE is `1033` (English), inherited from system locale value.</span></span>|  
|<span data-ttu-id="7a6ab-196">I</span><span class="sxs-lookup"><span data-stu-id="7a6ab-196">I</span></span>|<span data-ttu-id="7a6ab-197">6:30:00</span><span class="sxs-lookup"><span data-stu-id="7a6ab-197">6:30:00</span></span>|<span data-ttu-id="7a6ab-198">FORMAT_STRING が明示的に `Long Time` に設定され、LANGUAGE が明示的に `1034` (スペイン語) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-198">FORMAT_STRING is set explicitly to `Long Time` and LANGUAGE is set explicitly to `1034` (Spanish).</span></span>|  
|<span data-ttu-id="7a6ab-199">J</span><span class="sxs-lookup"><span data-stu-id="7a6ab-199">J</span></span>|<span data-ttu-id="7a6ab-200">06:30</span><span class="sxs-lookup"><span data-stu-id="7a6ab-200">06:30</span></span>|<span data-ttu-id="7a6ab-201">FORMAT_STRING が明示的に `Short Time` に設定され、LANGUAGE が明示的に `1034` (スペイン語) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-201">FORMAT_STRING is set explicitly to `Short Time` and LANGUAGE is set explicitly to `1034` (Spanish).</span></span>|  
|<span data-ttu-id="7a6ab-202">K</span><span class="sxs-lookup"><span data-stu-id="7a6ab-202">K</span></span>|<span data-ttu-id="7a6ab-203">6:30:00</span><span class="sxs-lookup"><span data-stu-id="7a6ab-203">6:30:00</span></span>|<span data-ttu-id="7a6ab-204">FORMAT_STRING が明示的に `Long Time` に設定され、LANGUAGE が明示的に `1041` (日本語) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-204">FORMAT_STRING is set explicitly to `Long Time` and LANGUAGE is set explicitly to `1041` (Japanese).</span></span>|  
|<span data-ttu-id="7a6ab-205">L</span><span class="sxs-lookup"><span data-stu-id="7a6ab-205">L</span></span>|<span data-ttu-id="7a6ab-206">06:30</span><span class="sxs-lookup"><span data-stu-id="7a6ab-206">06:30</span></span>|<span data-ttu-id="7a6ab-207">FORMAT_STRING が明示的に `Short Time` に設定され、LANGUAGE が明示的に `1041` (日本語) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="7a6ab-207">FORMAT_STRING is set explicitly to `Short Time` and LANGUAGE is set explicitly to `1041` (Japanese).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a6ab-208">参照</span><span class="sxs-lookup"><span data-stu-id="7a6ab-208">See Also</span></span>  
 <span data-ttu-id="7a6ab-209">[MDX&#41;&#40;のコンテンツの FORMAT_STRING](mdx-cell-properties-format-string-contents.md) </span><span class="sxs-lookup"><span data-stu-id="7a6ab-209">[FORMAT_STRING Contents &#40;MDX&#41;](mdx-cell-properties-format-string-contents.md) </span></span>  
 <span data-ttu-id="7a6ab-210">[MDX&#41;&#40;のセルプロパティの使用](mdx-cell-properties-using-cell-properties.md) </span><span class="sxs-lookup"><span data-stu-id="7a6ab-210">[Using Cell Properties &#40;MDX&#41;](mdx-cell-properties-using-cell-properties.md) </span></span>  
 <span data-ttu-id="7a6ab-211">[MDX&#41;&#40;のプロパティ値の作成と使用](../../creating-and-using-property-values-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="7a6ab-211">[Creating and Using Property Values &#40;MDX&#41;](../../creating-and-using-property-values-mdx.md) </span></span>  
 [<span data-ttu-id="7a6ab-212">MDX クエリの基礎 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7a6ab-212">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
