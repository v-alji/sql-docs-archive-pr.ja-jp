---
title: == (等しい) (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- equal operator (==)
- == (equal operator)
ms.assetid: 36fd2354-7b93-4c95-9cf3-51ee24568950
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 12f92a267543c366dee4905010aeb84d93c4f408
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716538"
---
# <a name="-equal-ssis-expression"></a><span data-ttu-id="38709-102">== (等しい) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="38709-102">== (Equal) (SSIS Expression)</span></span>
  <span data-ttu-id="38709-103">2 つの式が等しいかどうかを判別するための比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="38709-103">Performs a comparison to determine if two expressions are equal.</span></span> <span data-ttu-id="38709-104">式エバリュエーターは、比較の実行前にさまざまなデータ型を自動的に変換します。</span><span class="sxs-lookup"><span data-stu-id="38709-104">The expression evaluator automatically converts many data types before it performs the comparison.</span></span> <span data-ttu-id="38709-105">詳しくは、「 [式における Integration Services データ型](integration-services-data-types-in-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="38709-105">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
 <span data-ttu-id="38709-106">ただし、一部のデータ型では、式を正常に評価する前に明示的なキャストを含む必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="38709-106">However, some data types require that the expression include an explicit cast before the expression can be evaluated successfully.</span></span> <span data-ttu-id="38709-107">データ型間の有効なキャストについて詳しくは、「[Cast &#40;SSIS 式&#41;](cast-ssis-expression.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="38709-107">For more information about legal casts between data types, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38709-108">構文</span><span class="sxs-lookup"><span data-stu-id="38709-108">Syntax</span></span>  
  
```  
  
expression1 == expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="38709-109">引数</span><span class="sxs-lookup"><span data-stu-id="38709-109">Arguments</span></span>  
 <span data-ttu-id="38709-110">*expression1、expression2*</span><span class="sxs-lookup"><span data-stu-id="38709-110">*expression1, expression2*</span></span>  
 <span data-ttu-id="38709-111">任意の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="38709-111">Is any valid expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="38709-112">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="38709-112">Result Types</span></span>  
 <span data-ttu-id="38709-113">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="38709-113">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38709-114">解説</span><span class="sxs-lookup"><span data-stu-id="38709-114">Remarks</span></span>  
 <span data-ttu-id="38709-115">比較する式のいずれかが NULL の場合、比較結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="38709-115">If either expression in the comparison is null, the comparison result is null.</span></span> <span data-ttu-id="38709-116">両方の式が NULL の場合も、結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="38709-116">If both expressions are null, the result is null.</span></span>  
  
 <span data-ttu-id="38709-117">設定する式の *expression1* と *expression2*は、次のいずれかのルールに従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="38709-117">The expression set, *expression1* and *expression2*, must follow one of these rules:</span></span>  
  
-   <span data-ttu-id="38709-118">\**数値\*\*\*expression1* と *expression2* の両方が数値データ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="38709-118">**Numeric** Both *expression1* and *expression2* must be a numeric data type.</span></span> <span data-ttu-id="38709-119">データ型の積集合は、式エバリュエーターが実行する暗黙的な数値変換に関する規則で指定されているように、数値データ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="38709-119">The intersection of the data types must be a numeric data type, as specified in the rules about the implicit numeric conversions that the expression evaluator performs.</span></span> <span data-ttu-id="38709-120">2 つの数値データ型の積集合を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="38709-120">The intersection of the two numeric data types cannot be null.</span></span> <span data-ttu-id="38709-121">詳しくは、「 [式における Integration Services データ型](integration-services-data-types-in-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="38709-121">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
-   <span data-ttu-id="38709-122">\**文字\*\*\*expression1* と *expression2* は、どちらも DT_STR または DT_WSTR データ型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="38709-122">**Character** Both *expression1* and *expression2* must evaluate to either a DT_STR or a DT_WSTR data type.</span></span> <span data-ttu-id="38709-123">2 つの式が評価される文字列データ型は、異なっていてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="38709-123">The two expressions can evaluate to different string data types.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="38709-124">文字列の比較では、大文字と小文字、アクセント、かな、および文字幅が区別されます。</span><span class="sxs-lookup"><span data-stu-id="38709-124">String comparisons are case, accent, kana, and width-sensitive.</span></span>  
  
-   <span data-ttu-id="38709-125">\**日付、時刻、または日付/時刻\*\*\*expression1* と *expression2* は、どちらも DT_DBDATE、DT_DATE、DT_DBTIME、DT_DBTIME2、DT_DBTIMESTAMP、DT_DBTIMESTAMP2、DT_DBTIMESTAPMOFFSET、または DT_FILETIME のいずれかのデータ型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="38709-125">**Date, Time, or Date/Time** Both *expression1* and *expression2* must evaluate to one of the following data types: DT_DBDATE, DT_DATE, DT_DBTIME, DT_DBTIME2, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, DT_DBTIMESTAPMOFFSET, or DT_FILETIME.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="38709-126">時刻データ型に評価される式と、日付データ型または日付/時刻データ型に評価される式との間の比較はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="38709-126">The system does not support comparisons between an expression that evaluates to a time data type and an expression that evaluates to either a date or a date/time data type.</span></span> <span data-ttu-id="38709-127">システムによってエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="38709-127">The system generates an error.</span></span>  
  
     <span data-ttu-id="38709-128">式の比較の際は、次の変換規則が記載順に適用されます。</span><span class="sxs-lookup"><span data-stu-id="38709-128">When comparing the expressions, the system applies the following conversion rules in the order listed:</span></span>  
  
    -   <span data-ttu-id="38709-129">2 つの式が同じデータ型に評価される場合、そのデータ型の比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="38709-129">When the two expressions evaluate to the same data type, a comparison of that data type is performed.</span></span>  
  
    -   <span data-ttu-id="38709-130">一方の式が DT_DBTIMESTAMPOFFSET データ型の場合、もう一方の式が暗黙的に DT_DBTIMESTAMPOFFSET に変換され、DT_DBTIMESTAMPOFFSET の比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="38709-130">If one expression is a DT_DBTIMESTAMPOFFSET data type, the other expression is implicitly converted to DT_DBTIMESTAMPOFFSET and a DT_DBTIMESTAMPOFFSET comparison is performed.</span></span> <span data-ttu-id="38709-131">詳しくは、「 [式における Integration Services データ型](integration-services-data-types-in-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="38709-131">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
    -   <span data-ttu-id="38709-132">一方の式が DT_DBTIMESTAMP2 データ型の場合、もう一方の式が暗黙的に DT_DBTIMESTAMP2 に変換され、DT_DBTIMESTAMP2 の比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="38709-132">If one expression is a DT_DBTIMESTAMP2 data type, the other expression is implicitly converted to DT_DBTIMESTAMP2 and a DT_DBTIMESTAMP2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="38709-133">一方の式が DT_DBTIME2 データ型の場合、もう一方の式が暗黙的に DT_DBTIME2 に変換され、DT_DBTIME2 の比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="38709-133">If one expression is a DT_DBTIME2 data type, the other expression is implicitly converted to DT_DBTIME2, and a DT_DBTIME2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="38709-134">一方の式が DT_DBTIMESTAMPOFFSET、DT_DBTIMESTAMP2、DT_DBTIME2 のいずれの型でもない場合、両方の式が DT_DBTIMESTAMP データ型に変換されてから比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="38709-134">If one expression is of a type other than DT_DBTIMESTAMPOFFSET, DT_DBTIMESTAMP2, or DT_DBTIME2, the expressions are converted to the DT_DBTIMESTAMP data type before they are compared.</span></span>  
  
     <span data-ttu-id="38709-135">式の比較は、次の前提に基づいて実行されます。</span><span class="sxs-lookup"><span data-stu-id="38709-135">When comparing the expressions, the system makes the following assumptions:</span></span>  
  
    -   <span data-ttu-id="38709-136">それぞれの式のデータ型に秒の小数部が含まれている場合、秒の小数部の桁数が最も少ないデータ型の残りの桁の値は 0 と見なされます。</span><span class="sxs-lookup"><span data-stu-id="38709-136">If each expression is a data type that includes fractional seconds, the system assumes that the data type with the least number of digits for fractional seconds has zeros for the remaining digits.</span></span>  
  
    -   <span data-ttu-id="38709-137">それぞれの式が日付データ型であり、一方のみにタイム ゾーン オフセットがある場合、タイム ゾーン オフセットがない日付データ型は協定世界時 (UTC) と見なされます。</span><span class="sxs-lookup"><span data-stu-id="38709-137">If each expression is a date data type, but only one has a time zone offset, the system assumes that the date data type without the time zone offset is in Coordinated Universal Time (UTC).</span></span>  
  
-   <span data-ttu-id="38709-138">\**論理\*\*\*expression1* と *expression2* は、どちらもブール型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="38709-138">**Logical** Both *expression1* and *expression2* must evaluate to a Boolean.</span></span>  
  
-   <span data-ttu-id="38709-139">\**GUID\*\*\*expression1* と *expression2* は、どちらも DT_GUID データ型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="38709-139">**GUID** Both *expression1* and *expression2* must evaluate to the DT_GUID data type.</span></span>  
  
-   <span data-ttu-id="38709-140">\**バイナリ\*\*\*expression1* と *expression2* は、どちらも DT_BYTES データ型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="38709-140">**Binary** Both *expression1* and *expression2* must evaluate to the DT_BYTES data type.</span></span>  
  
-   <span data-ttu-id="38709-141">\**BLOB\*\*\*expression1* と *expression2* は、どちらも同じバイナリ ラージ オブジェクト ブロック (BLOB) データ型 (DT_TEXT、DT_NTEXT、または DT_IMAGE) に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="38709-141">**BLOB** Both *expression1* and *expression2* must evaluate to the same Binary Large Object Block (BLOB) data type: DT_TEXT, DT_NTEXT, or DT_IMAGE.</span></span>  
  
 <span data-ttu-id="38709-142">データ型について詳しくは、「 [Integration Services のデータ型](../data-flow/integration-services-data-types.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="38709-142">For more information about data types, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="38709-143">式の例</span><span class="sxs-lookup"><span data-stu-id="38709-143">Expression Examples</span></span>  
 <span data-ttu-id="38709-144">現在の日付が 2003 年 7 月 4 日の場合、この例の結果は TRUE に評価されます。</span><span class="sxs-lookup"><span data-stu-id="38709-144">This example evaluates to TRUE if the current date is July 4, 2003.</span></span> <span data-ttu-id="38709-145">詳しくは、「[GETDATE &#40;SSIS 式&#41;](getdate-ssis-expression.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="38709-145">For more information, see [GETDATE &#40;SSIS Expression&#41;](getdate-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="38709-146">"7/4/2003" == GETDATE()</span><span class="sxs-lookup"><span data-stu-id="38709-146">"7/4/2003" == GETDATE()</span></span>  
  
 <span data-ttu-id="38709-147">**ListPrice** 列の値が 500 の場合、この例の結果は TRUE に評価されます。</span><span class="sxs-lookup"><span data-stu-id="38709-147">This example evaluates to TRUE if the value in the **ListPrice** column is 500.</span></span>  
  
```  
ListPrice == 500  
```  
  
 <span data-ttu-id="38709-148">この例では、変数 **LPrice**を使用しています。</span><span class="sxs-lookup"><span data-stu-id="38709-148">This example uses the variable **LPrice**.</span></span> <span data-ttu-id="38709-149">**LPrice** の値が 500 の場合、この例の結果は TRUE に評価されます。</span><span class="sxs-lookup"><span data-stu-id="38709-149">It evaluates to TRUE if the value of **LPrice** is 500.</span></span> <span data-ttu-id="38709-150">式を正しく解析するには、この変数のデータ型が数値型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="38709-150">The data type of the variable must be numeric for the expression to parse successfully.</span></span>  
  
```  
@LPrice == 500  
```  
  
## <a name="see-also"></a><span data-ttu-id="38709-151">参照</span><span class="sxs-lookup"><span data-stu-id="38709-151">See Also</span></span>  
 <span data-ttu-id="38709-152">[\!= (等しくない) (SSIS 式)](equal-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="38709-152">[!= &#40;Unequal&#41; &#40;SSIS Expression&#41;](equal-ssis-expression.md) </span></span>  
 <span data-ttu-id="38709-153">[演算子の優先順位と結合規則](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="38709-153">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="38709-154">演算子 &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="38709-154">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
