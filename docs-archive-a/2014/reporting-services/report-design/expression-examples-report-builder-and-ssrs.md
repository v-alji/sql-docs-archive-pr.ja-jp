---
title: 式の例 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 03/08/2017
ms.openlocfilehash: c7ef06143dafdb5034d0f6202fdc16bc51f74ca8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634865"
---
# <a name="expression-examples-report-builder-and-ssrs"></a><span data-ttu-id="f0f09-102">式の例 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="f0f09-102">Expression Examples (Report Builder and SSRS)</span></span>

<span data-ttu-id="f0f09-103">レポートでは、内容と外観を制御するために式をよく使用します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-103">Expressions are used frequently in reports to control content and report appearance.</span></span> <span data-ttu-id="f0f09-104">式はで記述され [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 、組み込み関数のカスタムコード、レポート変数、グループ変数、およびユーザー定義変数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-104">Expressions are written in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], and can use built-in functions custom code, report and group variables, and user-defined variables.</span></span> <span data-ttu-id="f0f09-105">式は等号 (=) で始まります。</span><span class="sxs-lookup"><span data-stu-id="f0f09-105">Expressions begin with an equal sign (=).</span></span> <span data-ttu-id="f0f09-106">式エディターと使用できる参照の種類の詳細については、「[レポートでの式の使用 &#40;レポート ビルダーおよび SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)」および「[式の追加 &#40;レポート ビルダーおよび SSRS&#41;](add-an-expression-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f09-106">For more information about the expression editor and the types of references that you can include, see [Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md), and [Add an Expression &#40;Report Builder and SSRS&#41;](add-an-expression-report-builder-and-ssrs.md).</span></span>  

> [!IMPORTANT]  
>  <span data-ttu-id="f0f09-107">RDL サンドボックスが有効になっている場合は、レポートのパブリッシュ時に式のテキストで使用できる型およびメンバーが特定の型およびメンバーに制限されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-107">When RDL Sandboxing is enabled, only certain types and members can be used in expression text at report publish time.</span></span> <span data-ttu-id="f0f09-108">詳細については、 [「RDL サンドボックスの有効化と無効化」](../enable-and-disable-rdl-sandboxing.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f09-108">For more information, see [Enable and Disable RDL Sandboxing](../enable-and-disable-rdl-sandboxing.md).</span></span>  

<span data-ttu-id="f0f09-109">このトピックでは、レポート内で一般的なタスクに使用できる式の例を示します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-109">This topic provides examples of expressions that can be used for common tasks in a report.</span></span>  

-   <span data-ttu-id="f0f09-110">[Visual Basic の関数](#VisualBasicFunctions)[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] の日付関数、文字列関数、変換関数、および条件関数の例。</span><span class="sxs-lookup"><span data-stu-id="f0f09-110">[Visual Basic Functions](#VisualBasicFunctions) Examples for date, string, conversion and conditional [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions.</span></span>  

-   <span data-ttu-id="f0f09-111">[レポートの関数](#ReportFunctions) 集計および組み込みのレポート関数の例。</span><span class="sxs-lookup"><span data-stu-id="f0f09-111">[Report Functions](#ReportFunctions) Examples for aggregates and other built-in report functions.</span></span>  

-   <span data-ttu-id="f0f09-112">[レポート データの表示方法](#AppearanceofReportData) レポートの外観を変更する例。</span><span class="sxs-lookup"><span data-stu-id="f0f09-112">[Appearance of Report Data](#AppearanceofReportData) Examples for changing the appearance of a report.</span></span>  

-   <span data-ttu-id="f0f09-113">[プロパティ](#Properties) 形式または表示を制御するために、レポート アイテムのプロパティを設定する例。</span><span class="sxs-lookup"><span data-stu-id="f0f09-113">[Properties](#Properties) Examples for setting report item properties to control format or visibility.</span></span>  

-   <span data-ttu-id="f0f09-114">[パラメーター](#Parameters) 式の中でパラメーターを使用する例。</span><span class="sxs-lookup"><span data-stu-id="f0f09-114">[Parameters](#Parameters) Examples for using parameters in an expression.</span></span>  

-   <span data-ttu-id="f0f09-115">[カスタム コード](#CustomCode) 埋め込まれたカスタム コードの例。</span><span class="sxs-lookup"><span data-stu-id="f0f09-115">[Custom Code](#CustomCode) Examples of embedded custom code.</span></span>  

<span data-ttu-id="f0f09-116">特定用途ごとの式の例については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f09-116">For expression examples for specific uses, see the following topics:</span></span>  

-   [<span data-ttu-id="f0f09-117">グループ式の例 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f0f09-117">Group Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  

-   [<span data-ttu-id="f0f09-118">フィルター式の例 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f0f09-118">Filter Equation Examples &#40;Report Builder and SSRS&#41;</span></span>](filter-equation-examples-report-builder-and-ssrs.md)  

-   [<span data-ttu-id="f0f09-119">一般的に使用されるフィルター &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f0f09-119">Commonly Used Filters &#40;Report Builder and SSRS&#41;</span></span>](commonly-used-filters-report-builder-and-ssrs.md)  

-   [<span data-ttu-id="f0f09-120">レポート変数コレクションとグループ変数コレクションの参照 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f0f09-120">Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-report-and-group-variables-references-report-builder.md)  

<span data-ttu-id="f0f09-121">単純型と複合型の式、式を使用できる場所、式に使用できる参照の種類など、レポート式の詳細については、「 [式 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f09-121">For more information about simple and complex expressions, where you can use expressions, and the types of references that you can include in an expression, see topics under [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="f0f09-122">式が集計の計算のために評価されるコンテキストの詳細については、「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f09-122">For more information about the context in which expressions are evaluated for calculating aggregates, see [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  

<span data-ttu-id="f0f09-123">多数の関数および演算子がこのトピックでも式の例に使用されていますが、これらを使用して式を作成する方法をレポート作成のコンテキストで学習するには、「 [チュートリアル: 式の概要](../tutorial-introducing-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f09-123">To learn how to write expressions that use many of the functions and operators also used by expression examples in this topic, but in the context of writing a report, see [Tutorial: Introducing Expressions](../tutorial-introducing-expressions.md).</span></span>  

<span data-ttu-id="f0f09-124">式エディターには、組み込み関数を階層形式で表示できるビューが用意されています。</span><span class="sxs-lookup"><span data-stu-id="f0f09-124">The expression editor includes a hierarchical view of built-in functions.</span></span> <span data-ttu-id="f0f09-125">特定の関数を選択すると、[値] ペインにコード例が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-125">When you select the function, a code example appears in the Values pane.</span></span> <span data-ttu-id="f0f09-126">詳細については、レポートビルダー&#41;&#40;[[式] ダイアログボックス](../expression-dialog-box.md)または [[式] ダイアログボックス](../expression-dialog-box-report-builder.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f09-126">For more information, see the [Expression Dialog Box](../expression-dialog-box.md) or [Expression Dialog Box &#40;Report Builder&#41;](../expression-dialog-box-report-builder.md).</span></span>  

## <a name="functions"></a><span data-ttu-id="f0f09-127">関数</span><span class="sxs-lookup"><span data-stu-id="f0f09-127">Functions</span></span>  

<span data-ttu-id="f0f09-128">レポート内の多くの式には、関数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f0f09-128">Many expressions in a report contain functions.</span></span> <span data-ttu-id="f0f09-129">これらの関数を使用して、データの書式を設定し、ロジックを適用し、レポートのメタデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-129">You can format data, apply logic, and access report metadata using these functions.</span></span> <span data-ttu-id="f0f09-130">ランタイムライブラリの関数を使用する式 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 、 <xref:System.Convert> および名前空間と名前空間を作成でき <xref:System.Math> ます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-130">You can write expressions that use functions from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] run-time library, and from the <xref:System.Convert> and <xref:System.Math> namespaces.</span></span> <span data-ttu-id="f0f09-131">また、他のアセンブリまたはカスタム コードの関数への参照も追加できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-131">You can add references to functions from other assemblies or custom code.</span></span> <span data-ttu-id="f0f09-132">を含む、のクラスを使用することもでき [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.Text.RegularExpressions> ます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-132">You can also use classes from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], including <xref:System.Text.RegularExpressions>.</span></span>  

###  <a name="visual-basic-functions"></a><a name="VisualBasicFunctions"></a> <span data-ttu-id="f0f09-133">Visual Basic の関数</span><span class="sxs-lookup"><span data-stu-id="f0f09-133">Visual Basic Functions</span></span>  
<span data-ttu-id="f0f09-134">[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] の関数を使用して、テキスト ボックスに表示されるデータや、レポートのパラメーター、プロパティ、または他の領域に使用されるデータを操作できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-134">You can use [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions to manipulate the data that is displayed in text boxes or that is used for parameters, properties, or other areas of the report.</span></span> <span data-ttu-id="f0f09-135">ここでは、このような関数のうち、いくつかの例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-135">This section provides examples demonstrating some of these functions.</span></span> <span data-ttu-id="f0f09-136">各関数の詳細については、MSDN の「 [Visual Basic ランタイム ライブラリのメンバー](https://go.microsoft.com/fwlink/?LinkId=198941) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f09-136">For more information, see [Visual Basic Runtime Library Members](https://go.microsoft.com/fwlink/?LinkId=198941) on MSDN.</span></span>  

<span data-ttu-id="f0f09-137">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] には、日付固有の書式など、さまざまなカスタム書式が用意されています。</span><span class="sxs-lookup"><span data-stu-id="f0f09-137">The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] provides many custom format options, for example, for specific date formats.</span></span> <span data-ttu-id="f0f09-138">詳細については、MSDN の「 [型の書式設定](https://go.microsoft.com/fwlink/?LinkId=112024) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f09-138">For more information, see [Formatting Types](https://go.microsoft.com/fwlink/?LinkId=112024) on MSDN.</span></span>  

#### <a name="math-functions"></a><span data-ttu-id="f0f09-139">数値演算関数</span><span class="sxs-lookup"><span data-stu-id="f0f09-139">Math Functions</span></span>  

-   <span data-ttu-id="f0f09-140">`Round` 関数は、数値を最も近い整数に丸める場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-140">The `Round` function is useful to round numbers to the nearest integer.</span></span> <span data-ttu-id="f0f09-141">次の式は、1.3 を 1 に丸めます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-141">The following expression rounds a 1.3 to 1:</span></span>  

```  
= Round(1.3)  
```  

<span data-ttu-id="f0f09-142">Excel の `MRound` 関数のように、指定の倍数値に値を丸める式を記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-142">You can also write an expression to round a value to a multiple that you specify, similar to the `MRound` function in Excel.</span></span> <span data-ttu-id="f0f09-143">整数値を作成する係数で値を乗算し、その数値を丸め、同じ係数で除算します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-143">Multiply the value by a factor that creates an integer, round the number, and then divide by the same factor.</span></span> <span data-ttu-id="f0f09-144">たとえば、1.3 を最も近い 0.2 の倍数 (1.4) に丸めるには、次の式を使用します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-144">For example, to round 1.3 to the nearest multiple of .2 (1.4), use the following expression:</span></span>  

```  
= Round(1.3*5)/5  
```  

####  <a name="date-functions"></a><a name="DateFunctions"></a><span data-ttu-id="f0f09-145">日付関数</span><span class="sxs-lookup"><span data-stu-id="f0f09-145">Date Functions</span></span>  

-   <span data-ttu-id="f0f09-146">`Today` 関数は現在の日付を返します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-146">The `Today` function provides the current date.</span></span> <span data-ttu-id="f0f09-147">この式は、レポートに日付を表示するテキスト ボックス、または現在の日付に基づいてデータをフィルター処理するパラメーターに使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-147">This expression can be used in a text box to display the date on the report, or in a parameter to filter data based on the current date.</span></span>  

```  
=Today()  
```  

-   <span data-ttu-id="f0f09-148">`DateAdd` 関数は、1 つのパラメーターに基づいて日付の範囲を指定する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-148">The `DateAdd` function is useful for supplying a range of dates based on a single parameter.</span></span> <span data-ttu-id="f0f09-149">次の式では、 *StartDate*という名前のパラメーターで指定した日付の 6 か月後の日付が返されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-149">The following expression provides a date that is six months after the date from a parameter named *StartDate*.</span></span>  

```  
=DateAdd(DateInterval.Month, 6, Parameters!StartDate.Value)  
```  

-   <span data-ttu-id="f0f09-150">`Year` 関数は、特定の日付の年を表示します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-150">The `Year` function displays the year for a particular date.</span></span> <span data-ttu-id="f0f09-151">この関数を使用して、日付をグループ化したり、一連の日付のラベルとして年を表示したりできます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-151">You can use this to group dates together or to display the year as a label for a set of dates.</span></span> <span data-ttu-id="f0f09-152">次の式では、指定した販売注文日グループの年が返されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-152">This expression provides the year for a given group of sales order dates.</span></span> <span data-ttu-id="f0f09-153">また、`Month` 関数および他の関数を使用して、日付を操作することもできます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-153">The `Month` function and other functions can also be used to manipulate dates.</span></span> <span data-ttu-id="f0f09-154">詳細については、[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f09-154">For more information, see the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] documentation.</span></span>  

```  
=Year(Fields!OrderDate.Value)  
```  

-   <span data-ttu-id="f0f09-155">式の中で関数を組み合わせることで、形式をカスタマイズすることができます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-155">You can combine functions in an expression to customize the format.</span></span> <span data-ttu-id="f0f09-156">次の式は、"月-日-年" の日付の形式を "月-週番号" に変更します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-156">The following expression changes the format of a date in the form month-day-year to month-week-week number.</span></span> <span data-ttu-id="f0f09-157">たとえば、"12/23/2009" は "December Week 3" になります。</span><span class="sxs-lookup"><span data-stu-id="f0f09-157">For example, 12/23/2009 to December Week 3:</span></span>  

```  
=Format(Fields!MyDate.Value, "MMMM") & " Week " &   
(Int(DateDiff("d", DateSerial(Year(Fields!MyDate.Value),   
Month(Fields!MyDate.Value),1), Fields!FullDateAlternateKey.Value)/7)+1).ToString  
```  

<span data-ttu-id="f0f09-158">この式をデータセット内の計算フィールドとしてグラフで使用すると、各月の週ごとに値を集計できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-158">When used as a calculated field in a dataset, you can use this expression on a chart to aggregate values by week within each month.</span></span>  

-   <span data-ttu-id="f0f09-159">次の式は、SellStartDate の値を MMM-YY の書式で設定します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-159">The following expression formats the SellStartDate value as MMM-YY.</span></span> <span data-ttu-id="f0f09-160">SellStartDate フィールドは、datetime データ型です。</span><span class="sxs-lookup"><span data-stu-id="f0f09-160">SellStartDate field is a datetime data type.</span></span>  

```  
=FORMAT(Fields!SellStartDate.Value, "MMM-yy")  
```  

-   <span data-ttu-id="f0f09-161">次の式は、SellStartDate の値を dd/MM/yyyy の書式で設定します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-161">The following expression formats the SellStartDate value as dd/MM/yyyy.</span></span> <span data-ttu-id="f0f09-162">SellStartDate フィールドは、datetime データ型です。</span><span class="sxs-lookup"><span data-stu-id="f0f09-162">The SellStartDate field is a datetime data type.</span></span>  

```  
=FORMAT(Fields!SellStartDate.Value, "dd/MM/yyyy")  
```  

-   <span data-ttu-id="f0f09-163">`CDate` 関数は、値を日付に変換します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-163">The `CDate` function converts the value to a date.</span></span> <span data-ttu-id="f0f09-164">`Now` 関数は、使用中のシステムに応じて、現在の日付と時刻を含む日付値を返します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-164">The `Now` function returns a date value containing the current date and time according to your system.</span></span> <span data-ttu-id="f0f09-165">`DateDiff` は、2 つの日付値の間にある期間を数値で示す Long 値を返します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-165">`DateDiff` returns a Long value specifying the number of time intervals between two Date values.</span></span>  

<span data-ttu-id="f0f09-166">次の例では、今年の最初の日が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-166">The following example displays the start date of the current year</span></span>  

```  
=DateAdd(DateInterval.Year,DateDiff(DateInterval.Year,CDate("01/01/1900"),Now()),CDate("01/01/1900"))  
```  

-   <span data-ttu-id="f0f09-167">次の例では、現在の月に基づいて、前の月の最初の日が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-167">The following example displays the start date for the previous month based on the current month.</span></span>  

```  
=DateAdd(DateInterval.Month,DateDiff(DateInterval.Month,CDate("01/01/1900"),Now())-1,CDate("01/01/1900"))  
```  

-   <span data-ttu-id="f0f09-168">次の式は、SellStartDate と LastReceiptDate の間にある年数を生成します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-168">The following expression generates the interval years between SellStartDate and LastReceiptDate.</span></span> <span data-ttu-id="f0f09-169">これらのフィールドは、DataSet1 と DataSet2 の異なる 2 つのデータセットに含まれます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-169">These fields are in two different datasets, DataSet1 and DataSet2.</span></span> <span data-ttu-id="f0f09-170">集計関数である [First 関数 &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-first-function.md) は、DataSet1 にある SellStartDate の最初の値と、DataSet2 にある LastReceiptDate の最初の値を返します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-170">The [First Function &#40;Report Builder and SSRS&#41;](report-builder-functions-first-function.md), which is an aggregate function, returns the first value of SellStartDate in DataSet1 and the first value of LastReceiptDate in DataSet2.</span></span>  

```  
=DATEDIFF("yyyy", First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
```  

-   <span data-ttu-id="f0f09-171">`DatePart` 関数は、特定の日付値の指定されたコンポーネントを含む整数値を返します。次の式は、DataSet1 にある SellStartDate の最初の値の年を返します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-171">The `DatePart` function returns an Integer value containing the specified component of a given Date value.The following expression returns the year for the first value of the SellStartDate in DataSet1.</span></span> <span data-ttu-id="f0f09-172">レポートに複数のデータセットがあるため、データセット スコープが指定されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-172">The dataset scope is specified because there are multiple datasets in the report.</span></span>  

```  
=Datepart("yyyy", First(Fields!SellStartDate.Value, "DataSet1"))  

```  

-   <span data-ttu-id="f0f09-173">`DateSerial` 関数は、時間情報が午前 0 時に設定されている、指定の年月日を表す日付値を返します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-173">The `DateSerial` function returns a Date value representing a specified year, month, and day, with the time information set to midnight.</span></span> <span data-ttu-id="f0f09-174">次の例では、現在の月に基づいて、前の月の最終日が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-174">The following example displays the ending date for the prior month, based on the current month.</span></span>  

```  
=DateSerial(Year(Now()), Month(Now()), "1").AddDays(-1)  
```  

-   <span data-ttu-id="f0f09-175">次の式では、ユーザーによって選択された日付のパラメーター値に基づくさまざまな日付が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-175">The following expressions display various dates based on a date parameter value selected by the user.</span></span>  

|<span data-ttu-id="f0f09-176">例の説明</span><span class="sxs-lookup"><span data-stu-id="f0f09-176">Example Description</span></span>|<span data-ttu-id="f0f09-177">例</span><span class="sxs-lookup"><span data-stu-id="f0f09-177">Example</span></span>|  
|-------------------------|-------------|  
|<span data-ttu-id="f0f09-178">[昨日]</span><span class="sxs-lookup"><span data-stu-id="f0f09-178">Yesterday</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-1)`|  
|<span data-ttu-id="f0f09-179">2 日前</span><span class="sxs-lookup"><span data-stu-id="f0f09-179">Two Days Ago</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-2)`|  
|<span data-ttu-id="f0f09-180">1 か月前</span><span class="sxs-lookup"><span data-stu-id="f0f09-180">One Month Ago</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-1,Day(Parameters!TodaysDate.Value))`|  
|<span data-ttu-id="f0f09-181">2 か月前</span><span class="sxs-lookup"><span data-stu-id="f0f09-181">Two Months Ago</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-2,Day(Parameters!TodaysDate.Value))`|  
|<span data-ttu-id="f0f09-182">1 年前</span><span class="sxs-lookup"><span data-stu-id="f0f09-182">One Year Ago</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value)-1,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
|<span data-ttu-id="f0f09-183">2 年前</span><span class="sxs-lookup"><span data-stu-id="f0f09-183">Two Years Ago</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value)-2,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  

####  <a name="string-functions"></a><a name="StringFunctions"></a><span data-ttu-id="f0f09-184">文字列関数</span><span class="sxs-lookup"><span data-stu-id="f0f09-184">String Functions</span></span>  

-   <span data-ttu-id="f0f09-185">連結演算子および [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] の定数を使用して、複数のフィールドを組み合わせます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-185">Combine more than one field by using concatenation operators and [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] constants.</span></span> <span data-ttu-id="f0f09-186">次の式では、2 つのフィールドが、同じテキスト ボックス内の別々の行に返されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-186">The following expression returns two fields, each on a separate line in the same text box:</span></span>  

```  
=Fields!FirstName.Value & vbCrLf & Fields!LastName.Value   
```  

-   <span data-ttu-id="f0f09-187">`Format` 関数を使用して、文字列内の日付と数値の書式を設定します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-187">Format dates and numbers in a string with the `Format` function.</span></span> <span data-ttu-id="f0f09-188">次の式では、 *StartDate* パラメーターおよび *EndDate* パラメーターの値が長い日付形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-188">The following expression displays values of the *StartDate* and *EndDate* parameters in long date format:</span></span>  

```  
=Format(Parameters!StartDate.Value, "D") & " through " &  Format(Parameters!EndDate.Value, "D")    
```  

<span data-ttu-id="f0f09-189">テキストボックスに日付または数字のみが含まれている場合は、テキストボックス内の関数の代わりに書式を適用するために、テキストボックスの [書式] プロパティを使用する必要があり `Format` ます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-189">If the text box contains only a date or number, you should use the Format property of the text box to apply formatting instead of the `Format` function within the text box.</span></span>  

-   <span data-ttu-id="f0f09-190">`Right`、 `Len` 、および関数は、サブストリングを返す場合に便利です `InStr` 。たとえば、*ドメイン*のユーザー \\ *username*名をユーザー名のみにトリミングすることができます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-190">The `Right`, `Len`, and `InStr` functions are useful for returning a substring, for example, trimming *DOMAIN*\\*username* to just the user name.</span></span> <span data-ttu-id="f0f09-191">次の式では、\\User *というパラメーターで取得できる文字列のうち、円記号 (*) より右側の部分のみが返されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-191">The following expression returns the part of the string to the right of a backslash (\\) character from a parameter named *User*:</span></span>  

```  
=Right(Parameters!User.Value, Len(Parameters!User.Value) - InStr(Parameters!User.Value, "\"))  
```  

<span data-ttu-id="f0f09-192">次の式は、関数ではなくクラスのメンバーを使用して、前の式と同じ値になり [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.String> [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-192">The following expression results in the same value as the previous one, using members of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.String> class instead of [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions:</span></span>  

```  
=Parameters!User.Value.Substring(Parameters!User.Value.IndexOf("\")+1, Parameters!User.Value.Length-Parameters!User.Value.IndexOf("\")-1)  
```  

-   <span data-ttu-id="f0f09-193">複数の値を持つパラメーターから選択した値を表示します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-193">Display the selected values from a multivalue parameter.</span></span> <span data-ttu-id="f0f09-194">次の例では、関数を使用して、 `Join` *myselection*パラメーターの選択した値を1つの文字列に連結します。この文字列は、レポートアイテムのテキストボックスの値を表す式として設定できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-194">The following example uses the `Join` function to concatenate the selected values of the parameter *MySelection* into a single string that can be set as an expression for the value of a text box in a report item:</span></span>  

```  
= Join(Parameters!MySelection.Value)  
```  

<span data-ttu-id="f0f09-195">次の例では、前の例と同じ処理を行うだけでなく、選択した値のリストの前にテキスト文字列を表示します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-195">The following example does the same as the above example, as well as displays a text string prior to the list of selected values.</span></span>  

```  
="Report for " & JOIN(Parameters!MySelection.Value, " & ")  

```  

-   <span data-ttu-id="f0f09-196">`Regex`の関数は、 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.Text.RegularExpressions> 電話番号の書式設定など、既存の文字列の書式を変更する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="f0f09-196">The `Regex` functions from the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.Text.RegularExpressions> are useful for changing the format of existing strings, for example, formatting a telephone number.</span></span> <span data-ttu-id="f0f09-197">次の式では、関数を使用して、 `Replace` フィールド内の10桁の電話番号の形式を "*nnn* - *nnn* - *nnnn*" から "(*nnn*) *nnn* - *nnnn*" に変更しています。</span><span class="sxs-lookup"><span data-stu-id="f0f09-197">The following expression uses the `Replace` function to change the format of a ten-digit telephone number in a field from "*nnn*-*nnn*-*nnnn*" to "(*nnn*) *nnn*-*nnnn*":</span></span>  

```  
=System.Text.RegularExpressions.Regex.Replace(Fields!Phone.Value, "(\d{3})[ -.]*(\d{3})[ -.]*(\d{4})", "($1) $2-$3")  
```  

> [!NOTE]  
>  <span data-ttu-id="f0f09-198">Fields!Phone.Value に余分なスペースがないことと、データ型が <xref:System.String>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f09-198">Verify that the value for Fields!Phone.Value has no extra spaces and is of type <xref:System.String>.</span></span>  

#### <a name="lookup"></a><span data-ttu-id="f0f09-199">参照</span><span class="sxs-lookup"><span data-stu-id="f0f09-199">Lookup</span></span>  

-   <span data-ttu-id="f0f09-200">キー フィールドを指定することで、`Lookup` 関数を使用し、1 対 1 のリレーションシップ (キーと値のペアなど) の値をデータセットから取得することができます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-200">By specifying a key field, you can use the `Lookup` function to retrieve a value from a dataset for a one-to-one relationship, for example, a key-value pair.</span></span> <span data-ttu-id="f0f09-201">次の式では、入力された製品識別子に一致する製品名をデータセット ("Product") から取得し、表示します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-201">The following expression displays the product name from a dataset ("Product"), given the product identifier to match on:</span></span>  

```  
=Lookup(Fields!PID.Value, Fields!ProductID.Value, Fields!ProductName.Value, "Product")  
```  

#### <a name="lookupset"></a><span data-ttu-id="f0f09-202">LookupSet</span><span class="sxs-lookup"><span data-stu-id="f0f09-202">LookupSet</span></span>  

-   <span data-ttu-id="f0f09-203">キー フィールドを指定することで、`LookupSet` 関数を使用し、1 対多のリレーションシップの値のセットをデータセットから取得することができます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-203">By specifying a key field, you can use the `LookupSet` function to retrieve a set of values from a dataset for a one-to-many relationship.</span></span> <span data-ttu-id="f0f09-204">たとえば、1 人の個人が複数の電話番号を持っていることがあります。</span><span class="sxs-lookup"><span data-stu-id="f0f09-204">For example, a person can have multiple telephone numbers.</span></span> <span data-ttu-id="f0f09-205">次の例では、PhoneList データセットに個人識別子が含まれ、各行に電話番号が格納されているものとしています。</span><span class="sxs-lookup"><span data-stu-id="f0f09-205">In the following example, assume the dataset PhoneList contains a person identifier and a telephone number in each row.</span></span> <span data-ttu-id="f0f09-206">`LookupSet` は、値の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-206">`LookupSet` returns an array of values.</span></span> <span data-ttu-id="f0f09-207">次の例では、返された値を 1 つの文字列として結合し、ContactID で指定される個人の電話番号の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-207">The following expression combines the return values into a single string and displays the list of telephone numbers for the person specified by ContactID:</span></span>  

```  
=Join(LookupSet(Fields!ContactID.Value, Fields!PersonID.Value, Fields!PhoneNumber.Value, "PhoneList"),",")  
```  

####  <a name="conversion-functions"></a><a name="ConversionFunctions"></a><span data-ttu-id="f0f09-208">変換関数</span><span class="sxs-lookup"><span data-stu-id="f0f09-208">Conversion Functions</span></span>  
<span data-ttu-id="f0f09-209">[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] の関数を使用して、フィールドのデータ型を別のデータ型に変換することができます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-209">You can use [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions to convert a field from the one data type to a different data type.</span></span> <span data-ttu-id="f0f09-210">変換関数を使用すると、フィールドの既定のデータ型を、計算やテキストの連結に必要なデータ型に変換できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-210">Conversion functions can be used to convert the default data type for a field to the data type needed for calculations or to combine text.</span></span>  

-   <span data-ttu-id="f0f09-211">次の式では、フィルター式の [値] フィールドの [!INCLUDE[tsql](../../includes/tsql-md.md)] money データ型と比較するために、定数 500 を Decimal 型に変換します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-211">The following expression converts the constant 500 to type Decimal in order to compare it to a [!INCLUDE[tsql](../../includes/tsql-md.md)] money data type in the Value field for a filter expression.</span></span>  

```  
=CDec(500)  
```  

-   <span data-ttu-id="f0f09-212">次の式では、複数の値を持つパラメーター *MySelection*で選択された値の数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-212">The following expression displays the number of values selected for the multivalue parameter *MySelection*.</span></span>  

```  
=CStr(Parameters!MySelection.Count)  
```  

####  <a name="decision-functions"></a><a name="DecisionFunctions"></a> <span data-ttu-id="f0f09-213">決定関数</span><span class="sxs-lookup"><span data-stu-id="f0f09-213">Decision Functions</span></span>  

-   <span data-ttu-id="f0f09-214">`Iif` 関数では、式が True かどうかによって、2 つの値のいずれかが返されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-214">The `Iif` function returns one of two values depending on whether the expression is true or not.</span></span> <span data-ttu-id="f0f09-215">次の式では、`Iif` 関数を使用して、`LineTotal` の値が 100 を超える場合にブール値 `True` が返されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-215">The following expression uses the `Iif` function to return a Boolean value of `True` if the value of `LineTotal` exceeds 100.</span></span> <span data-ttu-id="f0f09-216">それ以外の場合は、`False` が返されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-216">Otherwise it returns `False`:</span></span>  

```  
=IIF(Fields!LineTotal.Value > 100, True, False)  
```  

-   <span data-ttu-id="f0f09-217">複数の `IIF` 関数 ("入れ子になった IIF" とも呼ばれます) を使用すると、`PctComplete` の値に応じて 3 つの値のいずれかを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-217">Use multiple `IIF` functions (also known as "nested IIFs") to return one of three values depending on the value of `PctComplete`.</span></span> <span data-ttu-id="f0f09-218">次の式をテキスト ボックスの塗りつぶしの色に使用すると、テキスト ボックスの値に応じて背景色を変更できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-218">The following expression can be placed in the fill color of a text box to change the background color depending on the value in the text box.</span></span>  

```  
=IIF(Fields!PctComplete.Value >= 10, "Green", IIF(Fields!PctComplete.Value >= 1, "Blue", "Red"))  
```  

<span data-ttu-id="f0f09-219">背景は、値が 10 以上の場合は緑色、1 ～ 9 の場合は青色、1 未満の場合は赤色になります。</span><span class="sxs-lookup"><span data-stu-id="f0f09-219">Values greater than or equal to 10 display with a green background, between 1 and 9 display with a blue background, and less than 1 display with a red background.</span></span>  

-   <span data-ttu-id="f0f09-220">同じ機能を実現するには、`Switch` 関数を使用するという方法もあります。</span><span class="sxs-lookup"><span data-stu-id="f0f09-220">A different way to get the same functionality uses the `Switch` function.</span></span> <span data-ttu-id="f0f09-221">`Switch` 関数は、検証する条件が 3 つ以上ある場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-221">The `Switch` function is useful when you have three or more conditions to test.</span></span> <span data-ttu-id="f0f09-222">`Switch` 関数は、True に評価される一連の式のうちの最初の式に関連付けられた値を返します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-222">The `Switch` function returns the value associated with the first expression in a series that evaluates to true:</span></span>  

```  
=Switch(Fields!PctComplete.Value >= 10, "Green", Fields!PctComplete.Value >= 1, "Blue", Fields!PctComplete.Value = 1, "Yellow", Fields!PctComplete.Value <= 0, "Red",)  
```  

<span data-ttu-id="f0f09-223">背景は、値が 10 以上の場合は緑色、1 ～ 9 の場合は青色、1 の場合は黄色、0 以下の場合は赤色になります。</span><span class="sxs-lookup"><span data-stu-id="f0f09-223">Values greater than or equal to 10 display with a green background, between 1 and 9 display with a blue background, equal to 1 display with a yellow background, and 0 or less display with a red background.</span></span>  

-   <span data-ttu-id="f0f09-224">`ImportantDate` フィールドの値を検証し、経過日数が 1 週間を超えている場合は "Red"、それ以外の場合は "Blue" を返します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-224">Test the value of the `ImportantDate` field and return "Red" if it is more than a week old, and "Blue" otherwise.</span></span> <span data-ttu-id="f0f09-225">この式を使用して、レポート アイテムに含まれるテキスト ボックスの Color プロパティを制御できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-225">This expression can be used to control the Color property of a text box in a report item:</span></span>  

```  
=IIF(DateDiff("d",Fields!ImportantDate.Value, Now())>7,"Red","Blue")  
```  

-   <span data-ttu-id="f0f09-226">`PhoneNumber` フィールドの値を検証し、値が `null` ([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] では `Nothing`) の場合は "No Value" を返し、それ以外の場合は電話番号の値を返します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-226">Test the value of the `PhoneNumber` field and return "No Value" if it is `null` (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]); otherwise return the phone number value.</span></span> <span data-ttu-id="f0f09-227">この式を使用して、レポート アイテムに含まれるテキスト ボックスの値を制御できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-227">This expression can be used to control the value of a text box in a report item.</span></span>  

```  
=IIF(Fields!PhoneNumber.Value Is Nothing,"No Value",Fields!PhoneNumber.Value)  
```  

-   <span data-ttu-id="f0f09-228">`Department` フィールドの値を検証し、サブレポート名または `null` ([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] では `Nothing`) を返します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-228">Test the value of the `Department` field and return either a subreport name or a `null` (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]).</span></span> <span data-ttu-id="f0f09-229">この式は、条件付きドリルスルー サブレポートで使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-229">This expression can be used for conditional drillthrough subreports.</span></span>  

```  
=IIF(Fields!Department.Value = "Development", "EmployeeReport", Nothing)  
```  

-   <span data-ttu-id="f0f09-230">フィールド値が NULL かどうかを検証します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-230">Test if a field value is null.</span></span> <span data-ttu-id="f0f09-231">この式を使用すると、画像レポート アイテムの `Hidden` プロパティを制御できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-231">This expression can be used to control the `Hidden` property of an image report item.</span></span> <span data-ttu-id="f0f09-232">次の例では、LargePhoto というフィールドの値が NULL でない場合にのみ、このフィールドで指定された画像が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-232">In the following example, the image specified by the field [LargePhoto] is displayed only if the value of the field is not null.</span></span>  

```  
=IIF(IsNothing(Fields!LargePhoto.Value),True,False)  
```  

-   <span data-ttu-id="f0f09-233">`MonthName` 関数は、指定した月に対応する月名を含む文字列値を返します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-233">The `MonthName` function returns a string value containing the name of the specified month.</span></span> <span data-ttu-id="f0f09-234">次の例では、フィールドに 0 という値が格納されている場合に、Month フィールドで NA と表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-234">The following example displays NA in the Month field when the field contains the value of 0.</span></span>  

```  
IIF(Fields!Month.Value=0,"NA",MonthName(IIF(Fields!Month.Value=0,1,Fields!Month.Value)))  

```  

###  <a name="report-functions"></a><a name="ReportFunctions"></a> <span data-ttu-id="f0f09-235">レポートの関数</span><span class="sxs-lookup"><span data-stu-id="f0f09-235">Report Functions</span></span>  
<span data-ttu-id="f0f09-236">レポートには、これ以外にも、レポート内のデータを操作するレポート関数への参照を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-236">In an expression, you can add a reference to additional report functions that manipulate data in a report.</span></span> <span data-ttu-id="f0f09-237">ここでは、このような関数のうち 2 つの例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-237">This section provides examples for two of these functions.</span></span> <span data-ttu-id="f0f09-238">レポートの関数と例の詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f09-238">For more information about report functions and examples, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  

#####  <a name="sum"></a><a name="Sum"></a><span data-ttu-id="f0f09-239">求め</span><span class="sxs-lookup"><span data-stu-id="f0f09-239">Sum</span></span>  

-   <span data-ttu-id="f0f09-240">`Sum` 関数を使用すると、グループまたはデータ領域内の値を合計できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-240">The `Sum` function can total the values in a group or data region.</span></span> <span data-ttu-id="f0f09-241">この関数は、グループのヘッダーまたはフッターで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-241">This function can be useful in the header or footer of a group.</span></span> <span data-ttu-id="f0f09-242">次の式では、Order グループまたは Order データ領域内のデータの合計が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-242">The following expression displays the sum of data in the Order group or data region:</span></span>  

```  
=Sum(Fields!LineTotal.Value, "Order")  
```  

-   <span data-ttu-id="f0f09-243">`Sum` 関数は、条件付き集計計算にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-243">You can also use the `Sum` function for conditional aggregate calculations.</span></span> <span data-ttu-id="f0f09-244">たとえば、データセットに State という名前のフィールドが存在し、Not Started、Started、Finished という値を設定できる場合、次の式をグループ ヘッダーで使用すると、値 Finished の合計のみが計算されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-244">For example, if a dataset has a field that is named State with possible values Not Started, Started, Finished, the following expression, when placed in a group header, calculates the aggregate sum for only the value Finished:</span></span>  

```  
=Sum(IIF(Fields!State.Value = "Finished", 1, 0))  
```  

#####  <a name="rownumber"></a><a name="RowNumber"></a><span data-ttu-id="f0f09-245">RowNumber</span><span class="sxs-lookup"><span data-stu-id="f0f09-245">RowNumber</span></span>  

-   <span data-ttu-id="f0f09-246">`RowNumber` 関数をデータ領域内のテキスト ボックスで使用すると、式が表示されるテキスト ボックスの各インスタンスの行数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-246">The `RowNumber` function, when used in a text box within a data region, displays the row number for each instance of the text box in which the expression appears.</span></span> <span data-ttu-id="f0f09-247">この関数は、テーブル内の行数を数える場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-247">This function can be useful to number rows in a table.</span></span> <span data-ttu-id="f0f09-248">また、行数に基づいた改ページの指定など、より複雑なタスクにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-248">It can also be useful for more complex tasks, such as providing page breaks based on number of rows.</span></span> <span data-ttu-id="f0f09-249">詳細については、このトピックの「 [改ページ](#PageBreaks) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f09-249">For more information, see [Page Breaks](#PageBreaks) in this topic.</span></span>  

<span data-ttu-id="f0f09-250">`RowNumber` に指定したスコープによって、どの時点で番号の再設定を開始するかが制御されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-250">The scope you specify for `RowNumber` controls when renumbering begins.</span></span> <span data-ttu-id="f0f09-251">この関数に `Nothing` キーワードを指定することで、最も外側のデータ領域内の最初の行からカウントが開始されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-251">The `Nothing` keyword indicates that the function will start counting at the first row in the outermost data region.</span></span> <span data-ttu-id="f0f09-252">入れ子になったデータ領域内でカウントを開始するには、データ領域の名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-252">To start counting within nested data regions, use the name of the data region.</span></span> <span data-ttu-id="f0f09-253">グループ内でカウントを開始するには、グループの名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-253">To start counting within a group, use the name of the group.</span></span>  

```  
=RowNumber(Nothing)  
```  

##  <a name="appearance-of-report-data"></a><a name="AppearanceofReportData"></a> <span data-ttu-id="f0f09-254">レポート データの表示方法</span><span class="sxs-lookup"><span data-stu-id="f0f09-254">Appearance of Report Data</span></span>  
<span data-ttu-id="f0f09-255">式を使用して、レポートにデータを表示する方法を操作できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-255">You can use expressions to manipulate how data appears on a report.</span></span> <span data-ttu-id="f0f09-256">たとえば、2 つのフィールドの値を 1 つのテキスト ボックスに表示したり、レポートに関する情報を表示したり、レポートに改ページを挿入する方法に影響を与えたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-256">For example, you can display the values of two fields in a single text box, display information about the report, or affect how page breaks are inserted in the report.</span></span>  

###  <a name="page-headers-and-footers"></a><a name="PageHeadersandFooters"></a><span data-ttu-id="f0f09-257">ページヘッダーとページフッター</span><span class="sxs-lookup"><span data-stu-id="f0f09-257">Page Headers and Footers</span></span>  
<span data-ttu-id="f0f09-258">レポートをデザインする場合、必要に応じてレポート名とページ番号をレポート フッターに表示できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-258">When designing a report, you may want to display the name of the report and page number in the report footer.</span></span> <span data-ttu-id="f0f09-259">この操作を行うには、以下の式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-259">To do this, you can use the following expressions:</span></span>  

-   <span data-ttu-id="f0f09-260">次の式では、レポート名、およびレポートが実行された時刻が返されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-260">The following expression provides the name of the report and the time it was run.</span></span> <span data-ttu-id="f0f09-261">この式は、レポート フッターまたはレポート本文のテキスト ボックスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-261">It can be placed in a text box in the report footer or in the body of the report.</span></span> <span data-ttu-id="f0f09-262">時間の書式は、 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の短い日付用の書式設定の文字列を使用して設定されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-262">The time is formatted with the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] formatting string for short date:</span></span>  

```  
=Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")  
```  

-   <span data-ttu-id="f0f09-263">次の式では、レポートのページ番号および全ページ数が返されます。この式は、レポートのフッター内のテキスト ボックスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-263">The following expression, placed in a text box in the footer of a report, provides page number and total pages in the report:</span></span>  

```  
=Globals.PageNumber & " of " & Globals.TotalPages  
```  

<span data-ttu-id="f0f09-264">以下の例では、ディレクトリの一覧の内容と同様に、ページ ヘッダーにページの最初と最後の値を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-264">The following examples describe how to display the first and last values from a page in the page header, similar to what you might find in a directory listing.</span></span> <span data-ttu-id="f0f09-265">この例では、 `LastName`という名前のテキスト ボックスを含むデータ領域を想定しています。</span><span class="sxs-lookup"><span data-stu-id="f0f09-265">The example assumes a data region that contains a text box named `LastName`.</span></span>  

-   <span data-ttu-id="f0f09-266">次の式は、ページ ヘッダーの左側にあるテキスト ボックスで使用されます。この式では、そのページの `LastName` テキスト ボックスの最初の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-266">The following expression, placed in a text box on the left side of the page header, provides the first value of the `LastName` text box on the page:</span></span>  

```  
=First(ReportItems("LastName").Value)  
```  

-   <span data-ttu-id="f0f09-267">次の式は、ページ ヘッダーの右側にあるテキスト ボックスで使用されます。この式では、そのページの `LastName` テキスト ボックスの最後の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-267">The following expression, placed in a text box on the right side of the page header, provides the last value of the `LastName` text box on the page:</span></span>  

```  
=Last(ReportItems("LastName").Value)  
```  

<span data-ttu-id="f0f09-268">次の例では、合計ページ数の表示方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-268">The following example describes how to display a page total.</span></span> <span data-ttu-id="f0f09-269">この例では、 `Cost`という名前のテキスト ボックスを含むデータ領域を想定しています。</span><span class="sxs-lookup"><span data-stu-id="f0f09-269">The example assumes a data region that contains a text box named `Cost`.</span></span>  

-   <span data-ttu-id="f0f09-270">次の式は、ページ ヘッダーまたはページ フッターで使用されます。この式では、 `Cost` テキスト ボックスの値の合計がそのページに返されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-270">The following expression, placed in the page header or footer, provides the sum of the values in the `Cost` text box for the page:</span></span>  

```  
=Sum(ReportItems("Cost").Value)  
```  

> [!NOTE]  
>  <span data-ttu-id="f0f09-271">ページ ヘッダーまたはページ フッターでは、1 つの式につき 1 つのレポート アイテムしか参照できません。</span><span class="sxs-lookup"><span data-stu-id="f0f09-271">You can refer to only one report item per expression in a page header or footer.</span></span> <span data-ttu-id="f0f09-272">また、ページ ヘッダーまたはページ フッターの式では、テキスト ボックスの名前を参照することはできますが、テキスト ボックス内の実際のデータ式は参照できません。</span><span class="sxs-lookup"><span data-stu-id="f0f09-272">Also, you can refer to the text box name, but not the actual data expression within the text box, in page header and footer expressions.</span></span>  

###  <a name="page-breaks"></a><a name="PageBreaks"></a> <span data-ttu-id="f0f09-273">改ページ</span><span class="sxs-lookup"><span data-stu-id="f0f09-273">Page Breaks</span></span>  
<span data-ttu-id="f0f09-274">レポートによっては、グループやレポート アイテムに改ページを設定せずに、またはグループやレポート アイテムの改ページに追加する形で、指定した行数の最後に改ページを挿入したい場合があります。</span><span class="sxs-lookup"><span data-stu-id="f0f09-274">In some reports, you may want to place a page break at the end of a specified number of rows instead of, or in addition to, on groups or report items.</span></span> <span data-ttu-id="f0f09-275">この操作を行うには、必要なグループや詳細レコードを含むグループを作成し、そのグループに改ページを追加した後、指定された行数でグループ化を行うグループ式を追加します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-275">To do this, create a group that contains the groups or detail records you want, add a page break to the group, and then add a group expression to group by a specified number of rows.</span></span>  

-   <span data-ttu-id="f0f09-276">次の式をグループ式で使用すると、25 行ごとに数値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-276">The following expression, when placed in the group expression, assigns a number to each set of 25 rows.</span></span> <span data-ttu-id="f0f09-277">グループに改ページが定義されている場合は、この式の結果として、25 行ごとに改ページが行われます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-277">When a page break is defined for the group, this expression results in a page break every 25 rows.</span></span>  

```  
=Ceiling(RowNumber(Nothing)/25)  
```  

<span data-ttu-id="f0f09-278">ユーザーが 1 ページあたりの行数の値を設定できるようにするには、 `RowsPerPage` という名前のパラメーターを作成し、次の式で示すように、そのパラメーターに基づいてグループ式を作成します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-278">To allow the user to set a value for the number of rows per page, create a parameter named `RowsPerPage` and base the group expression on the parameter, as shown in the following expression:</span></span>  

```  
=Ceiling(RowNumber(Nothing)/Parameters!RowsPerPage.Value)  
```  

<span data-ttu-id="f0f09-279">グループに改ページを設定する方法の詳細については、「[改ページの追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-page-break-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f09-279">For more information about setting page breaks for a group, see [Add a Page Break &#40;Report Builder and SSRS&#41;](add-a-page-break-report-builder-and-ssrs.md).</span></span>  

##  <a name="properties"></a><a name="Properties"></a> <span data-ttu-id="f0f09-280">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f0f09-280">Properties</span></span>  
<span data-ttu-id="f0f09-281">式は、テキスト ボックスにデータを表示するためだけに使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="f0f09-281">Expressions are not only used to display data in text boxes.</span></span> <span data-ttu-id="f0f09-282">レポート アイテムにプロパティを適用する方法を変更する場合にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-282">They can also be used to change how properties are applied to report items.</span></span> <span data-ttu-id="f0f09-283">レポート アイテムのスタイル情報を変更したり、情報の表示を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-283">You can change style information for a report item, or change its visibility.</span></span>  

###  <a name="formatting"></a><a name="Formatting"></a><span data-ttu-id="f0f09-284">書式設定</span><span class="sxs-lookup"><span data-stu-id="f0f09-284">Formatting</span></span>  

-   <span data-ttu-id="f0f09-285">テキスト ボックスの Color プロパティで次の式を使用すると、 `Profit` フィールドの値に応じてテキストの色が変更されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-285">The following expression, when used in the Color property of a text box, changes the color of the text depending on the value of the `Profit` field:</span></span>  

```  
=Iif(Fields!Profit.Value < 0, "Red", "Black")  
```  

<span data-ttu-id="f0f09-286">また、 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] のオブジェクト変数 `Me`を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-286">You can also use the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] object variable `Me`.</span></span> <span data-ttu-id="f0f09-287">この変数は、テキスト ボックスの値を参照するもう 1 つの手段です。</span><span class="sxs-lookup"><span data-stu-id="f0f09-287">This variable is another way of referring to the value of a text box.</span></span>  

`=Iif(Me.Value < 0, "Red", "Black")`  

-   <span data-ttu-id="f0f09-288">データ領域にあるレポート アイテムの BackgroundColor プロパティで次の式を使用すると、各行の背景色に薄緑色と白が交互に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-288">The following expression, when used in the BackgroundColor property of a report item in a data region, alternates the background color of each row between pale green and white:</span></span>  

```  
=Iif(RowNumber(Nothing) Mod 2, "PaleGreen", "White")  
```  

<span data-ttu-id="f0f09-289">特定のスコープに対して式を使用する場合は、次のように、集計関数に対してデータセットを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0f09-289">If you are using an expression for a specified scope, you may have to indicate the dataset for the aggregate function:</span></span>  

```  
=Iif(RowNumber("Employees") Mod 2, "PaleGreen", "White")  
```  

> [!NOTE]  
>  <span data-ttu-id="f0f09-290">使用できる色は、 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の KnownColor 列挙体の色です。</span><span class="sxs-lookup"><span data-stu-id="f0f09-290">Available colors come from the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] KnownColor enumeration.</span></span>  

### <a name="chart-colors"></a><span data-ttu-id="f0f09-291">グラフの色</span><span class="sxs-lookup"><span data-stu-id="f0f09-291">Chart Colors</span></span>  
<span data-ttu-id="f0f09-292">図形グラフの色を指定するには、色がデータ点にマップされる順序を制御するカスタム コードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-292">To specify colors for a Shape chart, you can use custom code to control the order that colors are mapped to data point values.</span></span> <span data-ttu-id="f0f09-293">これは複数のグラフで同じカテゴリ グループの色を統一するときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-293">This helps you use consistent colors for multiple charts that have the same category groups.</span></span> <span data-ttu-id="f0f09-294">詳細については、「[複数の図形グラフでの色の統一 &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f09-294">For more information, see [Specify Consistent Colors across Multiple Shape Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  

###  <a name="visibility"></a><a name="Visibility"></a><span data-ttu-id="f0f09-295">非</span><span class="sxs-lookup"><span data-stu-id="f0f09-295">Visibility</span></span>  
<span data-ttu-id="f0f09-296">レポート アイテムの表示プロパティを使用して、レポート内のアイテムの表示/非表示を切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-296">You can show and hide items in a report using the visibility properties for the report item.</span></span> <span data-ttu-id="f0f09-297">テーブルなどのデータ領域では、最初に、式の値に基づいて詳細行を非表示にできます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-297">In a data region such as a table, you can initially hide detail rows based on the value in an expression.</span></span>  

-   <span data-ttu-id="f0f09-298">グループ内の詳細行の初期表示に次の式を使用すると、 `PctQuota` フィールドで 90% を超えるすべての売上の詳細行が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-298">The following expression, when used for initial visibility of detail rows in a group, shows the detail rows for all sales exceeding 90 percent in the `PctQuota` field:</span></span>  

```  
=Iif(Fields!PctQuota.Value>.9, False, True)  
```  

-   <span data-ttu-id="f0f09-299">テーブルの Hidden プロパティに次の式を設定すると、テーブルの行数が 12 行を超えた場合にのみテーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-299">The following expression, when set in the Hidden property of a table, shows the table only if it has more than 12 rows:</span></span>  

```  
=IIF(CountRows()>12,false,true)  
```  

-   <span data-ttu-id="f0f09-300">次の式は、列のプロパティで設定した場合、データ `Hidden` ソースからデータが取得された後にレポートデータセットにフィールドが存在する場合にのみ、列を表示します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-300">The following expression, when set in the `Hidden` property of a column, shows the column only if the field exists in the report dataset after the data is retrieved from the data source:</span></span>  

```  
=IIF(Fields!Column_1.IsMissing, true, false)  
```  

###  <a name="urls"></a><a name="Hyperlinks"></a><span data-ttu-id="f0f09-301">ハイパーリンク</span><span class="sxs-lookup"><span data-stu-id="f0f09-301">URLs</span></span>  
<span data-ttu-id="f0f09-302">レポート データを使用して URL をカスタマイズできます。また、テキスト ボックスに対するアクションとして URL を追加するかどうかを、条件付きで制御することもできます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-302">You can customize URLs by using report data and also conditionally control whether URLs are added as an action for a text box.</span></span>  

-   <span data-ttu-id="f0f09-303">次の式をテキスト ボックスに対するアクションとして使用すると、URL パラメーターとしてデータセット フィールド `EmployeeID` を指定する、カスタマイズされた URL が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-303">The following expression, when used as an action on a text box, generates a customized URL that specifies the dataset field `EmployeeID` as a URL parameter.</span></span>  

```  
="http://adventure-works/MyInfo?ID=" & Fields!EmployeeID.Value  
```  

<span data-ttu-id="f0f09-304">詳細については、「[URL へのハイパーリンクの追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-hyperlink-to-a-url-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f09-304">For more information, see [Add a Hyperlink to a URL &#40;Report Builder and SSRS&#41;](add-a-hyperlink-to-a-url-report-builder-and-ssrs.md).</span></span>  

-   <span data-ttu-id="f0f09-305">次の式では、テキスト ボックス内に URL を追加するかどうかを、条件付きで制御します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-305">The following expression conditionally controls whether to add a URL in a text box.</span></span> <span data-ttu-id="f0f09-306">この式では、アクティブ URL をレポートに含めるかどうかをユーザーが決定できるように、 `IncludeURLs` という名前のパラメーターを使用しています。</span><span class="sxs-lookup"><span data-stu-id="f0f09-306">This expression depends on a parameter named `IncludeURLs` that allows a user to decide whether to include active URLs in a report.</span></span> <span data-ttu-id="f0f09-307">この式は、テキスト ボックスに対するアクションとして設定されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-307">This expression is set as an action on a text box.</span></span> <span data-ttu-id="f0f09-308">パラメーターを False に設定してからレポートを表示すると、ハイパーリンクなしでレポートを Microsoft Excel にエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-308">By setting the parameter to False and then viewing the report, you can export the report Microsoft Excel without hyperlinks.</span></span>  

```  
=IIF(Parameters!IncludeURLs.Value,"http://adventure-works.com/productcatalog",Nothing)  
```  

##  <a name="report-data"></a><a name="ReportData"></a><span data-ttu-id="f0f09-309">レポートデータ</span><span class="sxs-lookup"><span data-stu-id="f0f09-309">Report Data</span></span>  
<span data-ttu-id="f0f09-310">式を使用して、レポートで使用するデータを操作できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-310">Expressions can be used to manipulate the data that is used in the report.</span></span> <span data-ttu-id="f0f09-311">パラメーターおよび他のレポート情報を参照できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-311">You can refer to parameters and other report information.</span></span> <span data-ttu-id="f0f09-312">レポートのデータを取得するために使用されるクエリを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-312">You can even change the query that is used to retrieve data for the report.</span></span>  

###  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="f0f09-313">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f0f09-313">Parameters</span></span>  
<span data-ttu-id="f0f09-314">パラメーターの式を使用して、パラメーターの既定値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-314">You can use expressions in a parameter to vary the default value for the parameter.</span></span> <span data-ttu-id="f0f09-315">たとえば、パラメーターを使用して、レポートの実行に使用されるユーザー ID に基づき、特定のユーザーに合わせてデータをフィルター処理することができます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-315">For example, you can use a parameter to filter data to a particular user based on the user ID that is used to run the report.</span></span>  

-   <span data-ttu-id="f0f09-316">パラメーターの既定値として次の式を使用すると、レポートを実行するユーザーのユーザー ID が収集されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-316">The following expression, when used as the default value for a parameter, collects the user ID of the person running the report:</span></span>  

```  
=User!UserID  
```  

-   <span data-ttu-id="f0f09-317">レポートのクエリ パラメーター、フィルター式、テキスト ボックスなどの領域でパラメーターを参照するには、`Parameters` グローバル コレクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-317">To refer to a parameter in a query parameter, filter expression, text box, or other area of the report, use the `Parameters` global collection.</span></span> <span data-ttu-id="f0f09-318">この例では、パラメーターの名前が *Department*であることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="f0f09-318">This example assumes that the parameter is named *Department*:</span></span>  

```  
=Parameters!Department.Value  
```  

-   <span data-ttu-id="f0f09-319">パラメーターはレポート内に作成できますが、非表示に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-319">Parameters can be created in a report but set to hidden.</span></span> <span data-ttu-id="f0f09-320">レポート サーバーでレポートが実行される際、パラメーターがツール バーに表示されないため、レポートを表示するユーザーは既定値を変更できません。</span><span class="sxs-lookup"><span data-stu-id="f0f09-320">When the report runs on the report server, the parameter does not appear in the toolbar and the report reader cannot change the default value.</span></span> <span data-ttu-id="f0f09-321">既定値に設定された非表示パラメーターは、カスタム定数として使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-321">You can use a hidden parameter set to a default value as custom constant.</span></span> <span data-ttu-id="f0f09-322">この値は、フィールド式など、あらゆる式で使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-322">You can use this value in any expression, including a field expression.</span></span> <span data-ttu-id="f0f09-323">次の式では、 *ParameterField*という名前を持つパラメーターの既定値で指定されたフィールドを特定しています。</span><span class="sxs-lookup"><span data-stu-id="f0f09-323">The following expression identifies the field specified by the default parameter value for the parameter named *ParameterField*:</span></span>  

```  
=Fields(Parameters!ParameterField.Value).Value  
```  

## <a name="custom-code"></a><a name="CustomCode"></a><span data-ttu-id="f0f09-324">カスタムコード</span><span class="sxs-lookup"><span data-stu-id="f0f09-324">Custom Code</span></span>

<span data-ttu-id="f0f09-325">レポート内では、カスタム コードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-325">You can use custom code in a report.</span></span> <span data-ttu-id="f0f09-326">カスタム コードは、レポート内に埋め込むか、レポートで使用されるカスタム アセンブリに格納します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-326">Custom code is either embedded in a report or stored in a custom assembly which is used in the report.</span></span> <span data-ttu-id="f0f09-327">カスタム コードの詳細については、「[レポート デザイナーでカスタム コードやアセンブリを式から参照する &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f09-327">For more information about custom code, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  

### <a name="using-group-variables-for-custom-aggregation"></a><span data-ttu-id="f0f09-328">グループ変数を使用したカスタム集計</span><span class="sxs-lookup"><span data-stu-id="f0f09-328">Using Group Variables for Custom Aggregation</span></span>

<span data-ttu-id="f0f09-329">特定のグループ スコープ内のローカルなグループ変数の値を初期化し、その変数を式の中で参照することができます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-329">You can initialize the value for a group variable that is local to a particular group scope and then include a reference to that variable in expressions.</span></span> <span data-ttu-id="f0f09-330">カスタム コードでグループ変数を使用するシナリオとしては、カスタム集計の実装が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-330">One of the ways that you can use a group variable with custom code is to implement a custom aggregate.</span></span> <span data-ttu-id="f0f09-331">詳細については、「 [グループ変数を使ったカスタム集計 (Reporting Services 2008)](https://go.microsoft.com/fwlink/?LinkId=128714)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f09-331">For more information, see [Using Group Variables in Reporting Services 2008 for Custom Aggregation](https://go.microsoft.com/fwlink/?LinkId=128714).</span></span>  

<span data-ttu-id="f0f09-332">変数の詳細については、「 [レポート変数コレクションとグループ変数コレクションの参照 &#40;レポート ビルダーおよび SSRS&#41;](built-in-collections-report-and-group-variables-references-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f09-332">For more information about variables, see [Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;](built-in-collections-report-and-group-variables-references-report-builder.md).</span></span>  

## <a name="suppressing-null-or-zero-values-at-run-time"></a><span data-ttu-id="f0f09-333">実行時の NULL 値または 0 の非表示</span><span class="sxs-lookup"><span data-stu-id="f0f09-333">Suppressing Null or Zero Values at Run Time</span></span>

<span data-ttu-id="f0f09-334">式内の一部の値は、レポート処理時に NULL または未定義と評価されることがあります。</span><span class="sxs-lookup"><span data-stu-id="f0f09-334">Some values in an expression can evaluate to null or undefined at report processing time.</span></span> <span data-ttu-id="f0f09-335">その結果、実行時エラーが発生して、評価した式ではなく **#Error** がテキスト ボックスに表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="f0f09-335">This can create run-time errors that result in **#Error** displaying in the text box instead of the evaluated expression.</span></span> <span data-ttu-id="f0f09-336">`IIF` 関数は特にこの動作の影響を受けます。これは、If-Then-Else ステートメントとは異なり、`IIF` ステートメントの各部分 (関数呼び出しを含む) が、`true` であるか `false` であるかを検証するルーチンに渡される前に評価されるためです。</span><span class="sxs-lookup"><span data-stu-id="f0f09-336">The `IIF` function is particularly sensitive to this behavior because, unlike an If-Then-Else statement, each part of the `IIF` statement is evaluated (including function calls) before being passed to the routine that tests for `true` or `false`.</span></span> <span data-ttu-id="f0f09-337">`=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` ステートメントを実行すると、 **が NOTHING の場合は、表示されたレポートに** #Error `Fields!Sales.Value` と表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-337">The statement `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` generates **#Error** in the rendered report if `Fields!Sales.Value` is NOTHING.</span></span>  

<span data-ttu-id="f0f09-338">この状況を回避するには、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-338">To avoid this condition, use one of the following strategies:</span></span>  

-   <span data-ttu-id="f0f09-339">フィールド B の値が 0 または未定義の場合は、分子に 0、分母に 1 を設定します。それ以外の場合は、分子にフィールド A の値、分母にフィールド B の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-339">Set the numerator to 0 and the denominator to 1 if the value for field B is 0 or undefined; otherwise, set the numerator to the value for field A and the denominator to the value for field B.</span></span>  

```  
=IIF(Field!B.Value=0, 0, Field!A.Value / IIF(Field!B.Value =0, 1, Field!B.Value))  
```  

-   <span data-ttu-id="f0f09-340">カスタム コード関数を使用して、式の値を返します。</span><span class="sxs-lookup"><span data-stu-id="f0f09-340">Use a custom code function to return the value for the expression.</span></span> <span data-ttu-id="f0f09-341">次の例では、現在の値と前の値の差がパーセンテージで返されます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-341">The following example returns the percentage difference between a current value and a previous value.</span></span> <span data-ttu-id="f0f09-342">これを使用すると、任意の連続する 2 つの値の差を計算できます。また、最初の比較のエッジ ケース (前の値が存在しない場合) と、前の値または現在の値が `null` ([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] では `Nothing`) であるケースを処理できます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-342">This can be used to calculate the difference between any two successive values and it handles the edge case of the first comparison (when there is no previous value) and cases whether either the previous value or the current value is `null` (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]).</span></span>  

```  
Public Function GetDeltaPercentage(ByVal PreviousValue, ByVal CurrentValue) As Object  
     If IsNothing(PreviousValue) OR IsNothing(CurrentValue) Then  
          Return Nothing  
     Else if PreviousValue = 0 OR CurrentValue = 0 Then  
          Return Nothing  
     Else
          Return (CurrentValue - PreviousValue) / CurrentValue  
     End If  
End Function  
```  

<span data-ttu-id="f0f09-343">次の式に、"ColumnGroupByYear" コンテナーのテキスト ボックスからこのカスタム コードを呼び出す方法を示します (グループまたはデータ領域)。</span><span class="sxs-lookup"><span data-stu-id="f0f09-343">The following expression shows how to call this custom code from a text box, for the "ColumnGroupByYear" container (group or data region).</span></span>  

```  
=Code.GetDeltaPercentage(Previous(Sum(Fields!Sales.Value),"ColumnGroupByYear"), Sum(Fields!Sales.Value))  
```  

<span data-ttu-id="f0f09-344">実行時例外の発生はこのようにして防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="f0f09-344">This helps to avoid run-time exceptions.</span></span> <span data-ttu-id="f0f09-345">テキスト ボックスの `Color` プロパティで `=IIF(Me.Value < 0, "red", "black")` のような式を使用し、その値が 0 より大きいか小さいかの条件に基づいて、テキストを表示できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="f0f09-345">You can now use an expression like `=IIF(Me.Value < 0, "red", "black")` in the `Color` property of the text box to conditionally the display text based on whether the values are greater than or less than 0.</span></span>  

## <a name="see-also"></a><span data-ttu-id="f0f09-346">参照</span><span class="sxs-lookup"><span data-stu-id="f0f09-346">See Also</span></span>

- [<span data-ttu-id="f0f09-347">フィルター式の例 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f0f09-347">Filter Equation Examples &#40;Report Builder and SSRS&#41;</span></span>](filter-equation-examples-report-builder-and-ssrs.md)
- [<span data-ttu-id="f0f09-348">グループ式の例 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f0f09-348">Group Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)
- [<span data-ttu-id="f0f09-349">レポートでの式の使用 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="f0f09-349">Expression Uses in Reports &#40;Report Builder and SSRS&#41;</span></span>](expression-uses-in-reports-report-builder-and-ssrs.md)
- [<span data-ttu-id="f0f09-350">式 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f0f09-350">Expressions &#40;Report Builder and SSRS&#41;</span></span>](expressions-report-builder-and-ssrs.md)
- [<span data-ttu-id="f0f09-351">一般的に使用されるフィルター &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f0f09-351">Commonly Used Filters &#40;Report Builder and SSRS&#41;</span></span>](commonly-used-filters-report-builder-and-ssrs.md)