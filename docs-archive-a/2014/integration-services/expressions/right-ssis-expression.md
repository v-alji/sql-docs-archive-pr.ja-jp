---
title: RIGHT (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- RIGHT function
ms.assetid: 83e70e75-4be5-4783-a8cf-032f82afe16e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2584ee33ecbf0436c4e3dc6e92b957e60ae396ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716493"
---
# <a name="right-ssis-expression"></a><span data-ttu-id="cd329-102">RIGHT (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="cd329-102">RIGHT (SSIS Expression)</span></span>
  <span data-ttu-id="cd329-103">指定された文字式の一番右の部分から指定された数の文字を返します。</span><span class="sxs-lookup"><span data-stu-id="cd329-103">Returns the specified number of characters from the rightmost portion of the given character expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd329-104">構文</span><span class="sxs-lookup"><span data-stu-id="cd329-104">Syntax</span></span>  
  
```  
  
RIGHT(character_expression,integer_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="cd329-105">引数</span><span class="sxs-lookup"><span data-stu-id="cd329-105">Arguments</span></span>  
 <span data-ttu-id="cd329-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="cd329-106">*character_expression*</span></span>  
 <span data-ttu-id="cd329-107">文字の抽出元となる文字式です。</span><span class="sxs-lookup"><span data-stu-id="cd329-107">Is a character expression from which to extract characters.</span></span>  
  
 <span data-ttu-id="cd329-108">*integer_expression*</span><span class="sxs-lookup"><span data-stu-id="cd329-108">*integer_expression*</span></span>  
 <span data-ttu-id="cd329-109">返す文字の数を示す整数式です。</span><span class="sxs-lookup"><span data-stu-id="cd329-109">Is an integer expression that indicates the number of characters to be returned.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="cd329-110">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="cd329-110">Result Types</span></span>  
 <span data-ttu-id="cd329-111">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="cd329-111">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd329-112">解説</span><span class="sxs-lookup"><span data-stu-id="cd329-112">Remarks</span></span>  
 <span data-ttu-id="cd329-113">*integer_expression* が *character_expression*より長い場合、関数は *character_expression*を返します。</span><span class="sxs-lookup"><span data-stu-id="cd329-113">If *integer_expression* is greater than the length of *character_expression*, the function returns *character_expression*.</span></span>  
  
 <span data-ttu-id="cd329-114">*integer_expression* が 0 の場合、関数は長さが 0 の文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="cd329-114">If *integer_expression* is zero, the function returns a zero-length string.</span></span>  
  
 <span data-ttu-id="cd329-115">*integer_expression* が負の値の場合、関数はエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="cd329-115">If *integer_expression* is a negative number, the function returns an error.</span></span>  
  
 <span data-ttu-id="cd329-116">*integer_expression* 引数には、変数および列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="cd329-116">The *integer_expression* argument can take variables and columns.</span></span>  
  
 <span data-ttu-id="cd329-117">RIGHT は、DT_WSTR データ型でのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="cd329-117">RIGHT works only with the DT_WSTR data type.</span></span> <span data-ttu-id="cd329-118">*character_expression* 引数が DT_STR データ型の文字列リテラルまたはデータ列である場合は、RIGHT による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="cd329-118">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before RIGHT performs its operation.</span></span> <span data-ttu-id="cd329-119">その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd329-119">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="cd329-120">詳しくは、「[Integration Services のデータ型](../data-flow/integration-services-data-types.md)」および「[Cast &#40;SSIS 式&#41;](cast-ssis-expression.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cd329-120">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="cd329-121">引数のいずれかが NULL の場合、RIGHT は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="cd329-121">RIGHT returns a null result if either argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="cd329-122">式の例</span><span class="sxs-lookup"><span data-stu-id="cd329-122">Expression Examples</span></span>  
 <span data-ttu-id="cd329-123">次の例では、文字列リテラルを使用します。</span><span class="sxs-lookup"><span data-stu-id="cd329-123">The following example uses a string literal.</span></span> <span data-ttu-id="cd329-124">返される結果は `"Bike"`です。</span><span class="sxs-lookup"><span data-stu-id="cd329-124">The return result is `"Bike"`.</span></span>  
  
```  
RIGHT("Mountain Bike", 4)  
```  
  
 <span data-ttu-id="cd329-125">次の例では、 `Times` 列の右端からの文字が、 `Name` 変数で指定した文字数分返されます。</span><span class="sxs-lookup"><span data-stu-id="cd329-125">The following example returns the number of rightmost characters that is specified in the `Times` variable, from the `Name` column.</span></span> <span data-ttu-id="cd329-126">`Name` が `Touring Front Wheel` で `Times` が 5 の場合、返される結果は `"Wheel"`です。</span><span class="sxs-lookup"><span data-stu-id="cd329-126">If `Name` is `Touring Front Wheel` and `Times` is 5, the return result is `"Wheel"`.</span></span>  
  
```  
RIGHT(Name, @Times)  
```  
  
 <span data-ttu-id="cd329-127">次の例でも、 `Times` 列の右端からの文字が、 `Name` 変数で指定した文字数分返されます。</span><span class="sxs-lookup"><span data-stu-id="cd329-127">The following example also returns the number of rightmost characters that is specified in the `Times` variable, from the `Name` column.</span></span> <span data-ttu-id="cd329-128">`Times` の値は整数データ型でなく、式には DT_I2 データ型への明示的なキャストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cd329-128">`Times` has a noninteger data type and the expression includes an explicit cast to the DT_I2 data type.</span></span> <span data-ttu-id="cd329-129">`Name` が `Touring Front Wheel` で `Times` が `4.32`の場合、返される結果は `"heel"` です。これは、RIGHT 関数が値 4.32 を 4 に変換し、右端の 4 文字を返すためです。</span><span class="sxs-lookup"><span data-stu-id="cd329-129">If `Name` is `Touring Front Wheel` and `Times` is `4.32`, the return result is `"heel"` because the RIGHT function converts the value of 4.32 to 4, and then returns the rightmost four characters.</span></span>  
  
```  
RIGHT(Name, (DT_I2)@Times))  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd329-130">参照</span><span class="sxs-lookup"><span data-stu-id="cd329-130">See Also</span></span>  
 <span data-ttu-id="cd329-131">[LEFT &#40;SSIS 式&#41;](left-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="cd329-131">[LEFT &#40;SSIS Expression&#41;](left-ssis-expression.md) </span></span>  
 [<span data-ttu-id="cd329-132">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="cd329-132">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
