---
title: FINDSTRING (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- FINDSTRING function
ms.assetid: c83cb1b1-3c52-4496-b518-4c9253b9336d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 72f2ff21cb179ce565e60c6550b8ecc2618a5adb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640165"
---
# <a name="findstring-ssis-expression"></a><span data-ttu-id="89e51-102">FINDSTRING (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="89e51-102">FINDSTRING (SSIS Expression)</span></span>
  <span data-ttu-id="89e51-103">文字式内の文字列のうち、指定された文字列が検出された場所を返します。</span><span class="sxs-lookup"><span data-stu-id="89e51-103">Returns the location of the specified occurrence of a string within a character expression.</span></span> <span data-ttu-id="89e51-104">返される結果は、1 を基点とする検出場所のインデックスです。</span><span class="sxs-lookup"><span data-stu-id="89e51-104">The return result is the one-based index of the occurrence.</span></span> <span data-ttu-id="89e51-105">文字列パラメーターは文字式に評価され、検出場所を示すパラメーターは整数に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="89e51-105">The string parameter must evaluate to a character expression, and the occurrence parameter must evaluate to an integer.</span></span> <span data-ttu-id="89e51-106">文字列が見つからない場合、戻り値は 0 になります。</span><span class="sxs-lookup"><span data-stu-id="89e51-106">If the string is not found, the return value is 0.</span></span> <span data-ttu-id="89e51-107">文字列の検出回数が、引数によって指定された数より少ない場合の戻り値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="89e51-107">If the string occurs fewer times than the occurrence argument specifies, the return value is 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89e51-108">構文</span><span class="sxs-lookup"><span data-stu-id="89e51-108">Syntax</span></span>  
  
```  
  
FINDSTRING(character_expression, searchstring, occurrence)  
```  
  
## <a name="arguments"></a><span data-ttu-id="89e51-109">引数</span><span class="sxs-lookup"><span data-stu-id="89e51-109">Arguments</span></span>  
 <span data-ttu-id="89e51-110">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="89e51-110">*character_expression*</span></span>  
 <span data-ttu-id="89e51-111">検索対象が含まれる文字列です。</span><span class="sxs-lookup"><span data-stu-id="89e51-111">Is the character string to search in.</span></span>  
  
 <span data-ttu-id="89e51-112">*searchstring*</span><span class="sxs-lookup"><span data-stu-id="89e51-112">*searchstring*</span></span>  
 <span data-ttu-id="89e51-113">検索する文字列です。</span><span class="sxs-lookup"><span data-stu-id="89e51-113">Is the character string to search for.</span></span>  
  
 <span data-ttu-id="89e51-114">*occurrence*</span><span class="sxs-lookup"><span data-stu-id="89e51-114">*occurrence*</span></span>  
 <span data-ttu-id="89e51-115">何回目に検出した *searchstring* の場所をレポートするかを指定する、符号付きまたは符号なし整数です。</span><span class="sxs-lookup"><span data-stu-id="89e51-115">Is a signed or unsigned integer specifying which occurrence of *searchstring* to report.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="89e51-116">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="89e51-116">Result Types</span></span>  
 <span data-ttu-id="89e51-117">DT_I4</span><span class="sxs-lookup"><span data-stu-id="89e51-117">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89e51-118">解説</span><span class="sxs-lookup"><span data-stu-id="89e51-118">Remarks</span></span>  
 <span data-ttu-id="89e51-119">FINDSTRING は DT_WSTR データ型でのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="89e51-119">FINDSTRING works only with the DT_WSTR data type.</span></span>  <span data-ttu-id="89e51-120">*character_expression* および *searchstring* 引数が DT_STR データ型の文字列リテラルまたはデータ列である場合は、FINDSTRING による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="89e51-120">*character_expression* and *searchstring* arguments that are string literals or data columns with the DT_STR data type are implicitly cast to the DT_WSTR data type before FINDSTRING performs its operation.</span></span> <span data-ttu-id="89e51-121">その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="89e51-121">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="89e51-122">詳しくは、「[Integration Services のデータ型](../data-flow/integration-services-data-types.md)」および「[Cast &#40;SSIS 式&#41;](cast-ssis-expression.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="89e51-122">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="89e51-123">FINDSTRING は、 *character_expression* または *searchstring* が null の場合は null を返します。</span><span class="sxs-lookup"><span data-stu-id="89e51-123">FINDSTRING returns null if either *character_expression* or *searchstring* are null.</span></span>  
  
 <span data-ttu-id="89e51-124">1 回目に検出された場所のインデックスを取得するには、 *occurrence* 引数の値に 1 を使用します。2 回目以降の検出場所のインデックスを取得する場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="89e51-124">Use a value of 1 in the *occurrence* argument to get the index of the first occurrence, 2 for the second occurrence and so forth.</span></span>  
  
 <span data-ttu-id="89e51-125">*occurrence* には、0 より大きい整数値を指定してください。</span><span class="sxs-lookup"><span data-stu-id="89e51-125">The *occurrence* must be an integer with a value greater than 0.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="89e51-126">式の例</span><span class="sxs-lookup"><span data-stu-id="89e51-126">Expression Examples</span></span>  
 <span data-ttu-id="89e51-127">この例では、文字列リテラルを使用します。</span><span class="sxs-lookup"><span data-stu-id="89e51-127">This example uses a string literal.</span></span> <span data-ttu-id="89e51-128">値 11 が返されます。</span><span class="sxs-lookup"><span data-stu-id="89e51-128">It returns the value 11.</span></span>  
  
```  
FINDSTRING("New York, NY, NY", "NY", 1)   
```  
  
 <span data-ttu-id="89e51-129">この例では、文字列リテラルを使用します。</span><span class="sxs-lookup"><span data-stu-id="89e51-129">This example uses a string literal.</span></span> <span data-ttu-id="89e51-130">文字列 "NY" は 2 回しか検出されないため、返される結果は 0 です。</span><span class="sxs-lookup"><span data-stu-id="89e51-130">Because the string "NY" occurs only two times, the return result is 0.</span></span>  
  
```  
FINDSTRING("New York, NY, NY", "NY", 3)   
```  
  
 <span data-ttu-id="89e51-131">この例では、 **Name** 列を使用します。</span><span class="sxs-lookup"><span data-stu-id="89e51-131">This example uses the **Name** column.</span></span> <span data-ttu-id="89e51-132">**Name** 列にある n の値の場所が返されます。</span><span class="sxs-lookup"><span data-stu-id="89e51-132">It returns the location of the value n in the **Name** column.</span></span> <span data-ttu-id="89e51-133">返される結果は、 **Name**の値によって異なります。</span><span class="sxs-lookup"><span data-stu-id="89e51-133">The return result varies depending on the value in **Name**.</span></span> <span data-ttu-id="89e51-134">**Name** に Anderson が含まれる場合は、次の関数では 8 が返されます。</span><span class="sxs-lookup"><span data-stu-id="89e51-134">If **Name** contains Anderson, the function returns 8.</span></span>  
  
```  
FINDSTRING(Name,"n", 2)   
```  
  
 <span data-ttu-id="89e51-135">この例では、 **Name** および **Size** 列を使用します。</span><span class="sxs-lookup"><span data-stu-id="89e51-135">This example uses the **Name** and **Size** columns.</span></span> <span data-ttu-id="89e51-136">**Name** 列にある **Size** の値の左端の文字の場所が返されます。</span><span class="sxs-lookup"><span data-stu-id="89e51-136">It returns the location of the leftmost character of the **Size** value in the **Name** column.</span></span> <span data-ttu-id="89e51-137">返される結果は、列の値によって異なります。</span><span class="sxs-lookup"><span data-stu-id="89e51-137">The return result varies depending on column values.</span></span> <span data-ttu-id="89e51-138">**Name** の値が Mountain,500Red,42 で **Size** の値が 42 の場合、17 が返されます。</span><span class="sxs-lookup"><span data-stu-id="89e51-138">If **Name** contains Mountain,500Red,42 and **Size** contains 42, the return result is 17.</span></span>  
  
```  
FINDSTRING(Name,Size,1)   
```  
  
## <a name="see-also"></a><span data-ttu-id="89e51-139">参照</span><span class="sxs-lookup"><span data-stu-id="89e51-139">See Also</span></span>  
 <span data-ttu-id="89e51-140">[REPLACE &#40;SSIS &#41;](replace-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="89e51-140">[REPLACE &#40;SSIS Expression&#41;](replace-ssis-expression.md) </span></span>  
 [<span data-ttu-id="89e51-141">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="89e51-141">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
