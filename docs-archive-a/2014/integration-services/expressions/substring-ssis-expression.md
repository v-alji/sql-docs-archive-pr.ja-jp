---
title: SUBSTRING (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SUBSTRING function
- part of expression returned [Integration Services]
ms.assetid: 3a46748a-f5f8-4a6c-9108-673666754068
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ba53676bc6d13ed34892f48fca3b70372cb30604
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716458"
---
# <a name="substring-ssis-expression"></a><span data-ttu-id="e1bfa-102">SUBSTRING (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="e1bfa-102">SUBSTRING (SSIS Expression)</span></span>
  <span data-ttu-id="e1bfa-103">指定された位置で始まり、かつ指定された長さを持つ文字式の一部を返します。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-103">Returns the part of a character expression that starts at the specified position and has the specified length.</span></span> <span data-ttu-id="e1bfa-104">*position* パラメーターと *length* パラメーターは整数に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-104">The *position* parameter and the *length* parameter must evaluate to integers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1bfa-105">構文</span><span class="sxs-lookup"><span data-stu-id="e1bfa-105">Syntax</span></span>  
  
```  
  
SUBSTRING(character_expression, position, length)  
```  
  
## <a name="arguments"></a><span data-ttu-id="e1bfa-106">引数</span><span class="sxs-lookup"><span data-stu-id="e1bfa-106">Arguments</span></span>  
 <span data-ttu-id="e1bfa-107">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="e1bfa-107">*character_expression*</span></span>  
 <span data-ttu-id="e1bfa-108">文字の抽出元となる文字式です。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-108">Is a character expression from which to extract characters.</span></span>  
  
 <span data-ttu-id="e1bfa-109">*position*</span><span class="sxs-lookup"><span data-stu-id="e1bfa-109">*position*</span></span>  
 <span data-ttu-id="e1bfa-110">部分文字列が始まる位置を指定する整数です。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-110">Is an integer that specifies where the substring begins.</span></span>  
  
 <span data-ttu-id="e1bfa-111">*length*</span><span class="sxs-lookup"><span data-stu-id="e1bfa-111">*length*</span></span>  
 <span data-ttu-id="e1bfa-112">部分文字列の長さを文字数として指定する整数です。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-112">Is an integer that specifies the length of the substring as number of characters.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e1bfa-113">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="e1bfa-113">Result Types</span></span>  
 <span data-ttu-id="e1bfa-114">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="e1bfa-114">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1bfa-115">解説</span><span class="sxs-lookup"><span data-stu-id="e1bfa-115">Remarks</span></span>  
 <span data-ttu-id="e1bfa-116">SUBSTRING は 1 から始まるインデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-116">SUBSTRING uses a one-based index.</span></span> <span data-ttu-id="e1bfa-117">*position* が 1 の場合、部分文字列は *character_expression*の最初の文字から始まります。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-117">If *position* is 1, the substring begins with the first character in *character_expression*.</span></span>  
  
 <span data-ttu-id="e1bfa-118">SUBSTRING は DT_WSTR データ型でのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-118">SUBSTRING works only with the DT_WSTR data type.</span></span> <span data-ttu-id="e1bfa-119">*character_expression* 引数が DT_STR データ型の文字列リテラルまたはデータ列である場合は、SUBSTRING による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-119">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before SUBSTRING performs its operation.</span></span> <span data-ttu-id="e1bfa-120">その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-120">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="e1bfa-121">詳しくは、「[Integration Services のデータ型](../data-flow/integration-services-data-types.md)」および「[Cast &#40;SSIS 式&#41;](cast-ssis-expression.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-121">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="e1bfa-122">引数が NULL の場合、SUBSTRING は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-122">SUBSTRING returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="e1bfa-123">式のすべての引数で、変数および列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-123">All arguments in the expression can use variables and columns.</span></span>  
  
 <span data-ttu-id="e1bfa-124">*length* 引数が文字列の長さを超える場合、</span><span class="sxs-lookup"><span data-stu-id="e1bfa-124">The *length* argument can exceed the length of the string.</span></span> <span data-ttu-id="e1bfa-125">この関数は残りの文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-125">In that case, the function returns the remainder of the string.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="e1bfa-126">式の例</span><span class="sxs-lookup"><span data-stu-id="e1bfa-126">Expression Examples</span></span>  
 <span data-ttu-id="e1bfa-127">この例では、文字列リテラルの 4 文字目から始まる 2 文字が返されます。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-127">This example returns two characters, beginning with character 4, from a string literal.</span></span> <span data-ttu-id="e1bfa-128">返される結果は "ph" です。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-128">The return result is "ph".</span></span>  
  
```  
SUBSTRING("elephant",4,2)  
```  
  
 <span data-ttu-id="e1bfa-129">この例では、4 文字目から始まる文字列リテラルの残りの部分が返されます。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-129">This example returns the remainder of a string literal, beginning at the fourth character.</span></span> <span data-ttu-id="e1bfa-130">返される結果は "phant" です。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-130">The return result is "phant".</span></span> <span data-ttu-id="e1bfa-131">*length* 引数が文字列の長さを超えても、エラーにはなりません。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-131">It is not an error for the *length* argument to exceed the length of the string.</span></span>  
  
```  
SUBSTRING ("elephant",4,50)  
```  
  
 <span data-ttu-id="e1bfa-132">この例では、 **MiddleName** 列の最初の文字が返されます。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-132">This example returns the first letter from the **MiddleName** column.</span></span>  
  
```  
SUBSTRING(MiddleName,1,1)  
```  
  
 <span data-ttu-id="e1bfa-133">この例では、 *position* 引数と *length* 引数に変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-133">This example uses variables in the *position* and *length* arguments.</span></span> <span data-ttu-id="e1bfa-134">**Start** が 1 で **Length** が 5 の場合、関数は **Name** 列の最初の 5 文字を返します。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-134">If **Start** is 1 and **Length** is 5, the function returns the first five characters in the **Name** column.</span></span>  
  
```  
SUBSTRING(Name,@Start,@Length)  
```  
  
 <span data-ttu-id="e1bfa-135">この例では、 **PostalCode** 変数の 6 文字目から始まる、最後の 4 文字が返されます。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-135">This example returns the last four characters from the **PostalCode** variable beginning at the sixth character.</span></span>  
  
```  
SUBSTRING (@PostalCode,6,4)  
```  
  
 <span data-ttu-id="e1bfa-136">この例では、文字列リテラルから長さ 0 の文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="e1bfa-136">This example returns a zero-length string from a string literal.</span></span>  
  
```  
SUBSTRING ("Redmond",4,0)  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1bfa-137">参照</span><span class="sxs-lookup"><span data-stu-id="e1bfa-137">See Also</span></span>  
 [<span data-ttu-id="e1bfa-138">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="e1bfa-138">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
