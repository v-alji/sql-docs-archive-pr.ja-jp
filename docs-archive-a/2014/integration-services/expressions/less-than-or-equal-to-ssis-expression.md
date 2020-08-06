---
title: '&lt;= (以下) (SSIS 式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- <= (less than or equal to operator)
- less than or equal to operator (<=)
ms.assetid: 946c5630-dccf-4dae-9cfd-6ea823641ab2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c1c0b5ef0a8467cedbc5e390b42f3307cceb7c75
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639558"
---
# <a name="lt-less-than-or-equal-to-ssis-expression"></a><span data-ttu-id="d991f-102">&lt;= (以下) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="d991f-102">&lt;= (Less Than or Equal To) (SSIS Expression)</span></span>
  <span data-ttu-id="d991f-103">最初の式が 2 番目の式以下かどうかを判別するための比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="d991f-103">Performs a comparison to determine if the first expression is less than or equal to the second one.</span></span> <span data-ttu-id="d991f-104">式エバリュエーターは、比較の実行前にさまざまなデータ型を自動的に変換します。</span><span class="sxs-lookup"><span data-stu-id="d991f-104">The expression evaluator automatically converts many data types before it performs the comparison.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d991f-105">この演算子では、DT_TEXT、DT_NTEXT、または DT_IMAGE データ型を使用した比較はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d991f-105">This operator does not support comparisons that use the DT_TEXT, DT_NTEXT, or DT_IMAGE data types.</span></span>  
  
 <span data-ttu-id="d991f-106">ただし、一部のデータ型では、式を正常に評価する前に明示的なキャストを含む必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="d991f-106">However, some data types require that the expression include an explicit cast before the expression can be evaluated successfully.</span></span> <span data-ttu-id="d991f-107">データ型間の有効なキャストについて詳しくは、「[Cast &#40;SSIS 式&#41;](cast-ssis-expression.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d991f-107">For more information about legal casts between data types, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d991f-108">この演算子の 2 つの文字の間に、スペースはありません。</span><span class="sxs-lookup"><span data-stu-id="d991f-108">There are no spaces between the two characters in this operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d991f-109">構文</span><span class="sxs-lookup"><span data-stu-id="d991f-109">Syntax</span></span>  
  
```  
  
expression1 <= expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="d991f-110">引数</span><span class="sxs-lookup"><span data-stu-id="d991f-110">Arguments</span></span>  
 <span data-ttu-id="d991f-111">*expression1、expression2*</span><span class="sxs-lookup"><span data-stu-id="d991f-111">*expression1, expression2*</span></span>  
 <span data-ttu-id="d991f-112">任意の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="d991f-112">Is any valid expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="d991f-113">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="d991f-113">Result Types</span></span>  
 <span data-ttu-id="d991f-114">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="d991f-114">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d991f-115">解説</span><span class="sxs-lookup"><span data-stu-id="d991f-115">Remarks</span></span>  
 <span data-ttu-id="d991f-116">比較する式のいずれかが NULL の場合、比較結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="d991f-116">If either expression in the comparison is null, the comparison result is null.</span></span> <span data-ttu-id="d991f-117">両方の式が NULL の場合も、結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="d991f-117">If both expressions are null, the result is null.</span></span>  
  
 <span data-ttu-id="d991f-118">設定する式の *expression1* と *expression2*は、次のいずれかのルールに従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="d991f-118">The expression set, *expression1* and *expression2*, must follow one of these rules:</span></span>  
  
-   <span data-ttu-id="d991f-119">\**数値\*\*\*expression1* と *expression2* の両方が数値データ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d991f-119">**Numeric** Both *expression1* and *expression2* must be a numeric data type.</span></span> <span data-ttu-id="d991f-120">データ型の積集合は、式エバリュエーターが実行する暗黙的な数値変換に関する規則で指定されているように、数値データ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d991f-120">The intersection of the data types must be a numeric data type as specified in the rules about the implicit numeric conversions that the expression evaluator performs.</span></span> <span data-ttu-id="d991f-121">2 つの数値データ型の積集合を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d991f-121">The intersection of the two numeric data types cannot be null.</span></span> <span data-ttu-id="d991f-122">詳しくは、「 [式における Integration Services データ型](integration-services-data-types-in-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d991f-122">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
-   <span data-ttu-id="d991f-123">\**文字\*\*\*expression1* と *expression2* は、どちらも DT_STR または DT_WSTR データ型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="d991f-123">**Character** Both *expression1* and *expression2* must evaluate to either a DT_STR or a DT_WSTR data type.</span></span> <span data-ttu-id="d991f-124">2 つの式が評価される文字列データ型は、異なっていてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="d991f-124">The two expressions can evaluate to different string data types.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d991f-125">文字列の比較では、大文字と小文字、アクセント、かな、および文字幅が区別されます。</span><span class="sxs-lookup"><span data-stu-id="d991f-125">String comparisons are case, accent, kana, and width-sensitive.</span></span>  
  
-   <span data-ttu-id="d991f-126">\**日付、時刻、または日付/時刻\*\*\*expression1* と *expression2* は、どちらも DT_DBDATE、DT_DATE、DT_DBTIME、DT_DBTIME2、DT_DBTIMESTAMP、DT_DBTIMESTAMP2、DT_DBTIMESTAPMOFFSET、または DT_FILETIME のいずれかのデータ型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="d991f-126">**Date, Time, or Date/Time** Both *expression1* and *expression2* must evaluate to one of the following data types: DT_DBDATE, DT_DATE, DT_DBTIME, DT_DBTIME2, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, DT_DBTIMESTAPMOFFSET, or DT_FILETIME.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d991f-127">時刻データ型に評価される式と、日付データ型または日付/時刻データ型に評価される式との間の比較はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d991f-127">The system does not support comparisons between an expression that evaluates to a time data type and an expression that evaluates to either a date or a date/time data type.</span></span> <span data-ttu-id="d991f-128">システムによってエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="d991f-128">The system generates an error.</span></span>  
  
     <span data-ttu-id="d991f-129">式の比較の際は、次の変換規則が記載順に適用されます。</span><span class="sxs-lookup"><span data-stu-id="d991f-129">When comparing the expressions, the system applies the following conversion rules in the order listed:</span></span>  
  
    -   <span data-ttu-id="d991f-130">2 つの式が同じデータ型に評価される場合、そのデータ型の比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="d991f-130">When the two expressions evaluate to the same data type, a comparison of that data type is performed.</span></span>  
  
    -   <span data-ttu-id="d991f-131">一方の式が DT_DBTIMESTAMPOFFSET データ型の場合、もう一方の式が暗黙的に DT_DBTIMESTAMPOFFSET に変換され、DT_DBTIMESTAMPOFFSET の比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="d991f-131">If one expression is a DT_DBTIMESTAMPOFFSET data type, the other expression is implicitly converted to DT_DBTIMESTAMPOFFSET and a DT_DBTIMESTAMPOFFSET comparison is performed.</span></span> <span data-ttu-id="d991f-132">詳しくは、「 [式における Integration Services データ型](integration-services-data-types-in-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d991f-132">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
    -   <span data-ttu-id="d991f-133">一方の式が DT_DBTIMESTAMP2 データ型の場合、もう一方の式が暗黙的に DT_DBTIMESTAMP2 に変換され、DT_DBTIMESTAMP2 の比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="d991f-133">If one expression is a DT_DBTIMESTAMP2 data type, the other expression is implicitly converted to DT_DBTIMESTAMP2 and a DT_DBTIMESTAMP2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="d991f-134">一方の式が DT_DBTIME2 データ型の場合、もう一方の式が暗黙的に DT_DBTIME2 に変換され、DT_DBTIME2 の比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="d991f-134">If one expression is a DT_DBTIME2 data type, the other expression is implicitly converted to DT_DBTIME2, and a DT_DBTIME2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="d991f-135">一方の式が DT_DBTIMESTAMPOFFSET、DT_DBTIMESTAMP2、DT_DBTIME2 のいずれの型でもない場合、両方の式が DT_DBTIMESTAMP データ型に変換されてから比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="d991f-135">If one expression is of a type other than DT_DBTIMESTAMPOFFSET, DT_DBTIMESTAMP2, or DT_DBTIME2, the expressions are converted to the DT_DBTIMESTAMP data type before they are compared.</span></span>  
  
     <span data-ttu-id="d991f-136">式の比較は、次の前提に基づいて実行されます。</span><span class="sxs-lookup"><span data-stu-id="d991f-136">When comparing the expressions, the system makes the following assumptions:</span></span>  
  
    -   <span data-ttu-id="d991f-137">それぞれの式のデータ型に秒の小数部が含まれている場合、秒の小数部の桁数が最も少ないデータ型の残りの桁の値は 0 と見なされます。</span><span class="sxs-lookup"><span data-stu-id="d991f-137">If each expression is a data type that includes fractional seconds, the system assumes that the data type with the least number of digits for fractional seconds has zeros for the remaining digits.</span></span>  
  
    -   <span data-ttu-id="d991f-138">それぞれの式が日付データ型であり、一方のみにタイム ゾーン オフセットがある場合、タイム ゾーン オフセットがない日付データ型は協定世界時 (UTC) と見なされます。</span><span class="sxs-lookup"><span data-stu-id="d991f-138">If each expression is a date data type, but only one has a time zone offset, the system assumes that the date data type without the time zone offset is in Coordinated Universal Time (UTC).</span></span>  
  
 <span data-ttu-id="d991f-139">データ型について詳しくは、「 [Integration Services のデータ型](../data-flow/integration-services-data-types.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d991f-139">For more information about data types, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="d991f-140">式の例</span><span class="sxs-lookup"><span data-stu-id="d991f-140">Expression Examples</span></span>  
 <span data-ttu-id="d991f-141">現在の日付が 2003 年 7 月 4 日以降の場合、この例の結果は TRUE に評価されます。</span><span class="sxs-lookup"><span data-stu-id="d991f-141">This example evaluates to TRUE if the current date is July 4, 2003 or later.</span></span> <span data-ttu-id="d991f-142">詳しくは、「[GETDATE &#40;SSIS 式&#41;](getdate-ssis-expression.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d991f-142">For more information, see [GETDATE &#40;SSIS Expression&#41;](getdate-ssis-expression.md).</span></span>  
  
```  
"7/4/2003" <= GETDATE()  
```  
  
 <span data-ttu-id="d991f-143">**ListPrice** 列の値が 500 以下の場合、この例の結果は TRUE に評価されます。</span><span class="sxs-lookup"><span data-stu-id="d991f-143">This example evaluates to TRUE if the value in the **ListPrice** column is less than or equal to 500.</span></span>  
  
```  
ListPrice <= 500  
```  
  
 <span data-ttu-id="d991f-144">この例では変数 **LPrice** が評価され、値が 500 以下の場合、結果は TRUE に評価されます。</span><span class="sxs-lookup"><span data-stu-id="d991f-144">This example evaluates the variable **LPrice** and evaluates to TRUE if the value is less than or equal to 500.</span></span> <span data-ttu-id="d991f-145">式を解析するためには、 **LPrice** のデータ型は数値である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d991f-145">The data type of **LPrice** must be numeric in order for the expression to parse.</span></span>  
  
```  
@LPrice <= 500  
```  
  
## <a name="see-also"></a><span data-ttu-id="d991f-146">参照</span><span class="sxs-lookup"><span data-stu-id="d991f-146">See Also</span></span>  
 <span data-ttu-id="d991f-147">[&#62; &#40;より大きい&#41; &#40;SSIS 式&#41;](greater-than-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="d991f-147">[&#62; &#40;Greater Than&#41; &#40;SSIS Expression&#41;](greater-than-ssis-expression.md) </span></span>  
 <span data-ttu-id="d991f-148">[&#60; &#40;より小さい&#41; &#40;SSIS 式&#41;](less-than-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="d991f-148">[&#60; &#40;Less Than&#41; &#40;SSIS Expression&#41;](less-than-ssis-expression.md) </span></span>  
 <span data-ttu-id="d991f-149">[&#62;= &#40;以上&#41; &#40;SSIS 式&#41;](greater-than-or-equal-to-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="d991f-149">[&#62;= &#40;Greater Than or Equal To&#41; &#40;SSIS Expression&#41;](greater-than-or-equal-to-ssis-expression.md) </span></span>  
 <span data-ttu-id="d991f-150">[演算子の優先順位と結合規則](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="d991f-150">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="d991f-151">演算子 &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="d991f-151">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
