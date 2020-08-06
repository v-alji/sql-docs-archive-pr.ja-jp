---
title: '? : (条件) (SSIS 式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- conditional operator (?:)
- '?: (conditional operator)'
ms.assetid: d38e6890-7338-4ce0-a837-2dbb41823a37
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e607f9ed495184ef47ac2e4f1139b9a9566055ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645192"
---
# <a name="--conditional-ssis-expression"></a><span data-ttu-id="76fef-103">?</span><span class="sxs-lookup"><span data-stu-id="76fef-103">?</span></span> <span data-ttu-id="76fef-104">: (条件) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="76fef-104">: (Conditional) (SSIS Expression)</span></span>
  <span data-ttu-id="76fef-105">ブール式の評価に基づいて 2 つの式のうちのいずれかの式を返します。</span><span class="sxs-lookup"><span data-stu-id="76fef-105">Returns one of two expressions based on the evaluation of a Boolean expression.</span></span> <span data-ttu-id="76fef-106">ブール式が TRUE に評価された場合、最初の式が評価対象となり、その結果が式の結果になります。</span><span class="sxs-lookup"><span data-stu-id="76fef-106">If the Boolean expression evaluates to TRUE, then the first expression is evaluated and the result is the expression result.</span></span> <span data-ttu-id="76fef-107">ブール式が FALSE に評価された場合、2 番目の式が評価対象となり、その結果が式の結果になります。</span><span class="sxs-lookup"><span data-stu-id="76fef-107">If the Boolean expression evaluates to FALSE then the second expression is evaluated and its result is the expression result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76fef-108">構文</span><span class="sxs-lookup"><span data-stu-id="76fef-108">Syntax</span></span>  
  
```  
  
boolean_expression?expression1:expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="76fef-109">引数</span><span class="sxs-lookup"><span data-stu-id="76fef-109">Arguments</span></span>  
 <span data-ttu-id="76fef-110">*boolean_expression*</span><span class="sxs-lookup"><span data-stu-id="76fef-110">*boolean_expression*</span></span>  
 <span data-ttu-id="76fef-111">TRUE、FALSE、または NULL に評価される、任意の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="76fef-111">Is any valid expression that evaluates to TRUE, FALSE, or NULL.</span></span>  
  
 <span data-ttu-id="76fef-112">*expression1*</span><span class="sxs-lookup"><span data-stu-id="76fef-112">*expression1*</span></span>  
 <span data-ttu-id="76fef-113">任意の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="76fef-113">Is any valid expression.</span></span>  
  
 <span data-ttu-id="76fef-114">*expression2*</span><span class="sxs-lookup"><span data-stu-id="76fef-114">*expression2*</span></span>  
 <span data-ttu-id="76fef-115">任意の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="76fef-115">Is any valid expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="76fef-116">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="76fef-116">Result Types</span></span>  
 <span data-ttu-id="76fef-117">*expression1* または *expression2*のデータ型です。</span><span class="sxs-lookup"><span data-stu-id="76fef-117">The data type of *expression1* or *expression2*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76fef-118">解説</span><span class="sxs-lookup"><span data-stu-id="76fef-118">Remarks</span></span>  
 <span data-ttu-id="76fef-119">*boolean_expression* が NULL に評価された場合、式の結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="76fef-119">If the *boolean_expression* evaluates to NULL, the expression result is NULL.</span></span> <span data-ttu-id="76fef-120">選択された式 ( *expression1* または *expression2* のいずれか) が NULL の場合、結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="76fef-120">If a selected expression, either *expression1* or *expression2* is NULL, the result is NULL.</span></span> <span data-ttu-id="76fef-121">選択された式が NULL でなく、選択されていない式が NULL の場合、結果は選択された式の値になります。</span><span class="sxs-lookup"><span data-stu-id="76fef-121">If a selected expression is not NULL, but the one not selected is NULL, the result is the value of the selected expression.</span></span>  
  
 <span data-ttu-id="76fef-122">*expression1* と *expression2* のデータ型が同じ場合、結果はそのデータ型になります。</span><span class="sxs-lookup"><span data-stu-id="76fef-122">If *expression1* and *expression2* have the same data type, the result is that data type.</span></span> <span data-ttu-id="76fef-123">次の追加のルールが結果の型に適用されます。</span><span class="sxs-lookup"><span data-stu-id="76fef-123">The following additional rules apply to result types:</span></span>  
  
-   <span data-ttu-id="76fef-124">DT_TEXT データ型の場合、 *expression1* と *expression2* のコード ページが同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="76fef-124">The DT_TEXT data type requires that *expression1* and *expression2* have the same code page.</span></span>  
  
-   <span data-ttu-id="76fef-125">DT_BYTES データ型の場合、結果の長さは、長いほうの引数の長さと同じです。</span><span class="sxs-lookup"><span data-stu-id="76fef-125">The length of a result with the DT_BYTES data type is the length of the longer argument.</span></span>  
  
 <span data-ttu-id="76fef-126">式セットである *expression1* および *expression2*は、有効なデータ型および次のルールのいずれかに従って評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="76fef-126">The expression set, *expression1* and *expression2*, must evaluate to valid data types and follow one of these rules:</span></span>  
  
-   <span data-ttu-id="76fef-127">\**数値\*\*\*expression1* と *expression2* の両方が数値データ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="76fef-127">**Numeric** Both *expression1* and *expression2* must be a numeric data type.</span></span> <span data-ttu-id="76fef-128">データ型の積集合は、式エバリュエーターが実行する暗黙的な数値変換に関する規則で指定されているように、数値データ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="76fef-128">The intersection of the data types must be a numeric data type as specified in the rules about the implicit numeric conversions that the expression evaluator performs.</span></span> <span data-ttu-id="76fef-129">2 つの数値データ型の積集合を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="76fef-129">The intersection of the two numeric data types cannot be null.</span></span> <span data-ttu-id="76fef-130">詳しくは、「 [式における Integration Services データ型](integration-services-data-types-in-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="76fef-130">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
-   <span data-ttu-id="76fef-131">\**文字列\*\*\*expression1* と *expression2* は、どちらも DT_STR または DT_WSTR の文字列データ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="76fef-131">**String** Both *expression1* and *expression2* must be a string data type: DT_STR or DT_WSTR.</span></span> <span data-ttu-id="76fef-132">2 つの式が評価される文字列データ型は、異なっていてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="76fef-132">The two expressions can evaluate to different string data types.</span></span> <span data-ttu-id="76fef-133">DT_WSTR データ型の結果の長さは、長いほうの引数の長さと同じです。</span><span class="sxs-lookup"><span data-stu-id="76fef-133">The result has the DT_WSTR data type with a length of the longer argument.</span></span>  
  
-   <span data-ttu-id="76fef-134">\**日付、時刻、または日付/時刻\*\*\*expression1* と *expression2* は、どちらも DT_DBDATE、DT_DATE、DT_DBTIME、DT_DBTIME2、DT_DBTIMESTAMP、DT_DBTIMESTAMP2、DT_DBTIMESTAPMOFFSET、または DT_FILETIME のいずれかのデータ型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="76fef-134">**Date, Time, or Date/Time** Both *expression1* and *expression2* must evaluate to one of the following data types: DT_DBDATE, DT_DATE, DT_DBTIME, DT_DBTIME2, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, DT_DBTIMESTAPMOFFSET, or DT_FILETIME.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="76fef-135">時刻データ型に評価される式と、日付データ型または日付/時刻データ型に評価される式との間の比較はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="76fef-135">The system does not support comparisons between an expression that evaluates to a time data type and an expression that evaluates to either a date or a date/time data type.</span></span> <span data-ttu-id="76fef-136">システムによってエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="76fef-136">The system generates an error.</span></span>  
  
     <span data-ttu-id="76fef-137">式の比較の際は、次の変換規則が記載順に適用されます。</span><span class="sxs-lookup"><span data-stu-id="76fef-137">When comparing the expressions, the system applies the following conversion rules in the order listed:</span></span>  
  
    -   <span data-ttu-id="76fef-138">2 つの式が同じデータ型に評価される場合、そのデータ型の比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="76fef-138">When the two expressions evaluate to the same data type, a comparison of that data type is performed.</span></span>  
  
    -   <span data-ttu-id="76fef-139">一方の式が DT_DBTIMESTAMPOFFSET データ型の場合、もう一方の式が暗黙的に DT_DBTIMESTAMPOFFSET に変換され、DT_DBTIMESTAMPOFFSET の比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="76fef-139">If one expression is a DT_DBTIMESTAMPOFFSET data type, the other expression is implicitly converted to DT_DBTIMESTAMPOFFSET and a DT_DBTIMESTAMPOFFSET comparison is performed.</span></span> <span data-ttu-id="76fef-140">詳しくは、「 [式における Integration Services データ型](integration-services-data-types-in-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="76fef-140">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
    -   <span data-ttu-id="76fef-141">一方の式が DT_DBTIMESTAMP2 データ型の場合、もう一方の式が暗黙的に DT_DBTIMESTAMP2 に変換され、DT_DBTIMESTAMP2 の比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="76fef-141">If one expression is a DT_DBTIMESTAMP2 data type, the other expression is implicitly converted to DT_DBTIMESTAMP2 and a DT_DBTIMESTAMP2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="76fef-142">一方の式が DT_DBTIME2 データ型の場合、もう一方の式が暗黙的に DT_DBTIME2 に変換され、DT_DBTIME2 の比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="76fef-142">If one expression is a DT_DBTIME2 data type, the other expression is implicitly converted to DT_DBTIME2, and a DT_DBTIME2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="76fef-143">一方の式が DT_DBTIMESTAMPOFFSET、DT_DBTIMESTAMP2、DT_DBTIME2 のいずれの型でもない場合、両方の式が DT_DBTIMESTAMP データ型に変換されてから比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="76fef-143">If one expression is of a type other than DT_DBTIMESTAMPOFFSET, DT_DBTIMESTAMP2, or DT_DBTIME2, the expressions are converted to the DT_DBTIMESTAMP data type before they are compared.</span></span>  
  
     <span data-ttu-id="76fef-144">式の比較は、次の前提に基づいて実行されます。</span><span class="sxs-lookup"><span data-stu-id="76fef-144">When comparing the expressions, the system makes the following assumptions:</span></span>  
  
    -   <span data-ttu-id="76fef-145">それぞれの式のデータ型に秒の小数部が含まれている場合、秒の小数部の桁数が最も少ないデータ型の残りの桁の値は 0 と見なされます。</span><span class="sxs-lookup"><span data-stu-id="76fef-145">If each expression is a data type that includes fractional seconds, the system assumes that the data type with the least number of digits for fractional seconds has zeros for the remaining digits.</span></span>  
  
    -   <span data-ttu-id="76fef-146">それぞれの式が日付データ型であり、一方のみにタイム ゾーン オフセットがある場合、タイム ゾーン オフセットがない日付データ型は協定世界時 (UTC) と見なされます。</span><span class="sxs-lookup"><span data-stu-id="76fef-146">If each expression is a date data type, but only one has a time zone offset, the system assumes that the date data type without the time zone offset is in Coordinated Universal Time (UTC).</span></span>  
  
 <span data-ttu-id="76fef-147">データ型について詳しくは、「 [Integration Services のデータ型](../data-flow/integration-services-data-types.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="76fef-147">For more information about data types, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="76fef-148">式の例</span><span class="sxs-lookup"><span data-stu-id="76fef-148">Expression Examples</span></span>  
 <span data-ttu-id="76fef-149">この例では、条件に応じて `savannah` または `unknown`に評価される式を示しています。</span><span class="sxs-lookup"><span data-stu-id="76fef-149">This example shows an expression that conditionally evaluates to `savannah` or `unknown`.</span></span>  
  
```  
@AnimalName == "Elephant"? "savannah": "unknown"  
```  
  
 <span data-ttu-id="76fef-150">この例では、 **ListPrice** 列を参照する式を示しています。</span><span class="sxs-lookup"><span data-stu-id="76fef-150">This example shows an expression that references a **ListPrice** column.</span></span> <span data-ttu-id="76fef-151">**ListPrice** のデータ型は DT_CY です。</span><span class="sxs-lookup"><span data-stu-id="76fef-151">**ListPrice** has the DT_CY data type.</span></span> <span data-ttu-id="76fef-152">式は **ListPrice** に .2 または .1 のどちらかを条件に応じて乗算します。</span><span class="sxs-lookup"><span data-stu-id="76fef-152">The expression conditionally multiplies **ListPrice** by .2 or .1.</span></span>  
  
```  
ListPrice < 350.00 ? ListPrice * .2 : ListPrice * .1  
```  
  
## <a name="see-also"></a><span data-ttu-id="76fef-153">参照</span><span class="sxs-lookup"><span data-stu-id="76fef-153">See Also</span></span>  
 <span data-ttu-id="76fef-154">[演算子の優先順位と結合規則](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="76fef-154">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="76fef-155">演算子 &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="76fef-155">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
