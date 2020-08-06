---
title: '!= (等しくない) (SSIS 式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- unequal operator (!=)
- '!= (not equal to)'
ms.assetid: fad20e85-c0e6-42bf-af70-2bc80ee09be5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: be3eadbac77d76a2b3aac9555d9f40cb56e38949
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716434"
---
# <a name="-unequal-ssis-expression"></a><span data-ttu-id="3f1a4-102">!= (等しくない) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="3f1a4-102">!= (Unequal) (SSIS Expression)</span></span>
  <span data-ttu-id="3f1a4-103">互換性のあるデータ型の 2 つの式が等しくないかどうかを判別するための比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-103">Performs a comparison to determine if two expressions with compatible data types are not equal.</span></span> <span data-ttu-id="3f1a4-104">式エバリュエーターは、比較の実行前にさまざまなデータ型を自動的に変換します。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-104">The expression evaluator automatically converts many data types before it performs the comparison.</span></span>  
  
 <span data-ttu-id="3f1a4-105">ただし、一部のデータ型では、式を正常に評価する前に明示的なキャストを含む必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-105">However, some data types require that the expression include an explicit cast before the expression can be evaluated successfully.</span></span> <span data-ttu-id="3f1a4-106">データ型間の有効なキャストについて詳しくは、「[Cast &#40;SSIS 式&#41;](cast-ssis-expression.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-106">For more information about legal casts between data types, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f1a4-107">構文</span><span class="sxs-lookup"><span data-stu-id="3f1a4-107">Syntax</span></span>  
  
```  
  
expression1 != expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="3f1a4-108">引数</span><span class="sxs-lookup"><span data-stu-id="3f1a4-108">Arguments</span></span>  
 <span data-ttu-id="3f1a4-109">*expression1、expression2*</span><span class="sxs-lookup"><span data-stu-id="3f1a4-109">*expression1, expression2*</span></span>  
 <span data-ttu-id="3f1a4-110">任意の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-110">Is any valid expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="3f1a4-111">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="3f1a4-111">Result Types</span></span>  
 <span data-ttu-id="3f1a4-112">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="3f1a4-112">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f1a4-113">解説</span><span class="sxs-lookup"><span data-stu-id="3f1a4-113">Remarks</span></span>  
 <span data-ttu-id="3f1a4-114">比較する式のいずれかが NULL の場合、比較結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-114">If either expression in the comparison is null, the comparison result is null.</span></span> <span data-ttu-id="3f1a4-115">両方の式が NULL の場合も、結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-115">If both expressions are null, the result is null.</span></span>  
  
 <span data-ttu-id="3f1a4-116">設定する式の *expression1* と *expression2*は、次のいずれかのルールに従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-116">The expression set, *expression1* and *expression2*, must follow one of these rules:</span></span>  
  
-   <span data-ttu-id="3f1a4-117">\**数値\*\*\*expression1* と *expression2* の両方が数値データ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-117">**Numeric** Both *expression1* and *expression2* must be a numeric data type.</span></span> <span data-ttu-id="3f1a4-118">データ型の積集合は、式エバリュエーターが実行する暗黙的な数値変換に関する規則で指定されているように、数値データ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-118">The intersection of the data types must be a numeric data type, as specified in the rules about the implicit numeric conversions that the expression evaluator performs.</span></span> <span data-ttu-id="3f1a4-119">2 つの数値データ型の積集合を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-119">The intersection of the two numeric data types cannot be null.</span></span> <span data-ttu-id="3f1a4-120">詳しくは、「 [式における Integration Services データ型](integration-services-data-types-in-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-120">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
-   <span data-ttu-id="3f1a4-121">\**文字\*\*\*expression1* と *expression2* は、どちらも DT_STR または DT_WSTR データ型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-121">**Character** Both *expression1* and *expression2* must evaluate to either a DT_STR or a DT_WSTR data type.</span></span> <span data-ttu-id="3f1a4-122">2 つの式が評価される文字列データ型は、異なっていてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-122">The two expressions can evaluate to different string data types.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3f1a4-123">文字列の比較では、大文字と小文字、アクセント、かな、および文字幅が区別されます。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-123">String comparisons are case, accent, kana, and width-sensitive.</span></span>  
  
-   <span data-ttu-id="3f1a4-124">\**日付、時刻、または日付/時刻\*\*\*expression1* と *expression2* は、どちらも DT_DBDATE、DT_DATE、DT_DBTIME、DT_DBTIME2、DT_DBTIMESTAMP、DT_DBTIMESTAMP2、DT_DBTIMESTAPMOFFSET、または DT_FILETIME のいずれかのデータ型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-124">**Date, Time, or Date/Time** Both *expression1* and *expression2* must evaluate to one of the following data types: DT_DBDATE, DT_DATE, DT_DBTIME, DT_DBTIME2, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, DT_DBTIMESTAPMOFFSET, or DT_FILETIME.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3f1a4-125">時刻データ型に評価される式と、日付データ型または日付/時刻データ型に評価される式との間の比較はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-125">The system does not support comparisons between an expression that evaluates to a time data type and an expression that evaluates to either a date or a date/time data type.</span></span> <span data-ttu-id="3f1a4-126">システムによってエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-126">The system generates an error.</span></span>  
  
     <span data-ttu-id="3f1a4-127">式の比較の際は、次の変換規則が記載順に適用されます。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-127">When comparing the expressions, the system applies the following conversion rules in the order listed:</span></span>  
  
    -   <span data-ttu-id="3f1a4-128">2 つの式が同じデータ型に評価される場合、そのデータ型の比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-128">When the two expressions evaluate to the same data type, a comparison of that data type is performed.</span></span>  
  
    -   <span data-ttu-id="3f1a4-129">一方の式が DT_DBTIMESTAMPOFFSET データ型の場合、もう一方の式が暗黙的に DT_DBTIMESTAMPOFFSET に変換され、DT_DBTIMESTAMPOFFSET の比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-129">If one expression is a DT_DBTIMESTAMPOFFSET data type, the other expression is implicitly converted to DT_DBTIMESTAMPOFFSET and a DT_DBTIMESTAMPOFFSET comparison is performed.</span></span> <span data-ttu-id="3f1a4-130">詳しくは、「 [式における Integration Services データ型](integration-services-data-types-in-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-130">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
    -   <span data-ttu-id="3f1a4-131">一方の式が DT_DBTIMESTAMP2 データ型の場合、もう一方の式が暗黙的に DT_DBTIMESTAMP2 に変換され、DT_DBTIMESTAMP2 の比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-131">If one expression is a DT_DBTIMESTAMP2 data type, the other expression is implicitly converted to DT_DBTIMESTAMP2 and a DT_DBTIMESTAMP2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="3f1a4-132">一方の式が DT_DBTIME2 データ型の場合、もう一方の式が暗黙的に DT_DBTIME2 に変換され、DT_DBTIME2 の比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-132">If one expression is a DT_DBTIME2 data type, the other expression is implicitly converted to DT_DBTIME2, and a DT_DBTIME2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="3f1a4-133">一方の式が DT_DBTIMESTAMPOFFSET、DT_DBTIMESTAMP2、DT_DBTIME2 のいずれの型でもない場合、両方の式が DT_DBTIMESTAMP データ型に変換されてから比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-133">If one expression is of a type other than DT_DBTIMESTAMPOFFSET, DT_DBTIMESTAMP2, or DT_DBTIME2, the expressions are converted to the DT_DBTIMESTAMP data type before they are compared.</span></span>  
  
     <span data-ttu-id="3f1a4-134">式の比較は、次の前提に基づいて実行されます。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-134">When comparing the expressions, the system makes the following assumptions:</span></span>  
  
    -   <span data-ttu-id="3f1a4-135">それぞれの式のデータ型に秒の小数部が含まれている場合、秒の小数部の桁数が最も少ないデータ型の残りの桁の値は 0 と見なされます。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-135">If each expression is a data type that includes fractional seconds, the system assumes that the data type with the least number of digits for fractional seconds has zeros for the remaining digits.</span></span>  
  
    -   <span data-ttu-id="3f1a4-136">それぞれの式が日付データ型であり、一方のみにタイム ゾーン オフセットがある場合、タイム ゾーン オフセットがない日付データ型は協定世界時 (UTC) と見なされます。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-136">If each expression is a date data type, but only one has a time zone offset, the system assumes that the date data type without the time zone offset is in Coordinated Universal Time (UTC).</span></span>  
  
-   <span data-ttu-id="3f1a4-137">\**論理\*\*\*expression1* と *expression2* は、どちらもブール型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-137">**Logical** Both *expression1* and *expression2* must evaluate to a Boolean.</span></span>  
  
-   <span data-ttu-id="3f1a4-138">\**GUID\*\*\*expression1* と *expression2* は、どちらも DT_GUID データ型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-138">**GUID** Both *expression1* and *expression2* must evaluate to the DT_GUID data type.</span></span>  
  
-   <span data-ttu-id="3f1a4-139">\**バイナリ\*\*\*expression1* と *expression2* は、どちらも DT_BYTES データ型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-139">**Binary** Both *expression1* and *expression2* must evaluate to the DT_BYTES data type.</span></span>  
  
-   <span data-ttu-id="3f1a4-140">\**BLOB\*\*\*expression1* と *expression2* は、どちらも同じバイナリ ラージ オブジェクト ブロック (BLOB) データ型 (DT_TEXT、DT_NTEXT、または DT_IMAGE) に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-140">**BLOB** Both *expression1* and *expression2* must evaluate to the same Binary Large Object Block (BLOB) data type: DT_TEXT, DT_NTEXT, or DT_IMAGE.</span></span>  
  
 <span data-ttu-id="3f1a4-141">データ型について詳しくは、「 [Integration Services のデータ型](../data-flow/integration-services-data-types.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-141">For more information about data types, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="3f1a4-142">式の例</span><span class="sxs-lookup"><span data-stu-id="3f1a4-142">Expression Examples</span></span>  
 <span data-ttu-id="3f1a4-143">現在の日付が 2003 年 7 月 4 日ではない場合にのみ、この例の結果は TRUE に評価されます。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-143">This example evaluates to TRUE only if the current date is not July 4, 2003.</span></span> <span data-ttu-id="3f1a4-144">詳しくは、「[GETDATE &#40;SSIS 式&#41;](getdate-ssis-expression.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-144">For more information, see [GETDATE &#40;SSIS Expression&#41;](getdate-ssis-expression.md).</span></span>  
  
```  
"7/4/2003" != GETDATE()  
```  
  
 <span data-ttu-id="3f1a4-145">**ListPrice** 列の値が 500 でない場合、この例の結果は TRUE に評価されます。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-145">This example evaluates to TRUE if the value in the **ListPrice** column is not 500.</span></span>  
  
```  
ListPrice != 500  
```  
  
 <span data-ttu-id="3f1a4-146">この例では、変数 **LPrice**を使用しています。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-146">This example uses the variable **LPrice**.</span></span> <span data-ttu-id="3f1a4-147">**LPrice** の値が 500 でない場合、この例の結果は TRUE に評価されます。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-147">It evaluates to TRUE if the value of **LPrice** is not 500.</span></span> <span data-ttu-id="3f1a4-148">式を解析するためには、この変数のデータ型は数値である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f1a4-148">The data type on the variable must be numeric in order for the expression to parse.</span></span>  
  
```  
@LPrice != 500  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f1a4-149">参照</span><span class="sxs-lookup"><span data-stu-id="3f1a4-149">See Also</span></span>  
 <span data-ttu-id="3f1a4-150">[== &#40;等しい&#41; &#40;SSIS 式&#41;](equal-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="3f1a4-150">[== &#40;Equal&#41; &#40;SSIS Expression&#41;](equal-ssis-expression.md) </span></span>  
 <span data-ttu-id="3f1a4-151">[演算子の優先順位と結合規則](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="3f1a4-151">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="3f1a4-152">演算子 &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="3f1a4-152">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
