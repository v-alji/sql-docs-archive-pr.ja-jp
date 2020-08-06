---
title: '| (ビット演算包含的 OR) (SSIS 式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '| (bitwise inclusive OR)'
- bitwise inclusive OR (|)
ms.assetid: 4dce9eb2-3680-4adc-81a3-816ea52cef49
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 73d64886b433ffe5b4e06dc4870bbca06b2a53dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642928"
---
# <a name="-bitwise-inclusive-or-ssis-expression"></a><span data-ttu-id="947c9-102">| (ビット演算包含的 OR) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="947c9-102">| (Bitwise Inclusive OR) (SSIS Expression)</span></span>
  <span data-ttu-id="947c9-103">2 つの整数値の OR 演算をビット単位で実行します。</span><span class="sxs-lookup"><span data-stu-id="947c9-103">Performs a bitwise OR operation of two integer values.</span></span> <span data-ttu-id="947c9-104">最初のオペランドの各ビットを 2 番目のオペランドの対応するビットと比較します。</span><span class="sxs-lookup"><span data-stu-id="947c9-104">It compares each bit of its first operand to the corresponding bit of its second operand.</span></span> <span data-ttu-id="947c9-105">いずれかのビットが 1 の場合、対応する結果ビットは 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="947c9-105">If either bit is 1, the corresponding result bit is set to 1.</span></span> <span data-ttu-id="947c9-106">それ以外の場合、対応する結果ビットはゼロ (0) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="947c9-106">Otherwise, the corresponding result bit is set to zero (0).</span></span>  
  
 <span data-ttu-id="947c9-107">どちらの条件も符号付き整数データ型か、または、どちらの条件も符号なし整数データ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="947c9-107">Both conditions must be a signed integer data type or both conditions must be an unsigned integer data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="947c9-108">構文</span><span class="sxs-lookup"><span data-stu-id="947c9-108">Syntax</span></span>  
  
```  
  
integer_expression1 | integer_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="947c9-109">引数</span><span class="sxs-lookup"><span data-stu-id="947c9-109">Arguments</span></span>  
 <span data-ttu-id="947c9-110">*integer_expression1 ,integer_ expression2*</span><span class="sxs-lookup"><span data-stu-id="947c9-110">*integer_expression1 ,integer_ expression2*</span></span>  
 <span data-ttu-id="947c9-111">符号付きまたは符号なし整数データ型の任意の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="947c9-111">Is any valid expression of a signed or unsigned integer data type.</span></span> <span data-ttu-id="947c9-112">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="947c9-112">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="947c9-113">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="947c9-113">Result Types</span></span>  
 <span data-ttu-id="947c9-114">2 つの引数のデータ型によって決まります。</span><span class="sxs-lookup"><span data-stu-id="947c9-114">Determined by data types of the two arguments.</span></span> <span data-ttu-id="947c9-115">詳しくは、「 [式における Integration Services データ型](integration-services-data-types-in-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="947c9-115">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="947c9-116">解説</span><span class="sxs-lookup"><span data-stu-id="947c9-116">Remarks</span></span>  
 <span data-ttu-id="947c9-117">条件のいずれかが NULL の場合、式の結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="947c9-117">If either condition is null, the expression result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="947c9-118">式の例</span><span class="sxs-lookup"><span data-stu-id="947c9-118">Expression Examples</span></span>  
 <span data-ttu-id="947c9-119">この例では、変数 **NumberA** と **NumberB**間で包含的 OR 演算をビット単位で実行します。</span><span class="sxs-lookup"><span data-stu-id="947c9-119">This example performs a bitwise inclusive OR operation between the variables **NumberA** and **NumberB**.</span></span> <span data-ttu-id="947c9-120">**NumberA** には 3 (00000011) が、 **NumberB** には 9 (00001001) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="947c9-120">**NumberA** contains 3 (00000011) and **NumberB** contains 9 (00001001).</span></span>  
  
```  
@NumberA | @NumberB  
```  
  
 <span data-ttu-id="947c9-121">式は 11 (00001011) に評価されます。</span><span class="sxs-lookup"><span data-stu-id="947c9-121">The expression evaluates to 11 (00001011).</span></span>  
  
 <span data-ttu-id="947c9-122">00000011</span><span class="sxs-lookup"><span data-stu-id="947c9-122">00000011</span></span>  
  
 <span data-ttu-id="947c9-123">00001001</span><span class="sxs-lookup"><span data-stu-id="947c9-123">00001001</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="947c9-124">00001011</span><span class="sxs-lookup"><span data-stu-id="947c9-124">00001011</span></span>  
  
 <span data-ttu-id="947c9-125">この例では、 **ReorderPoint** 列と **SafetyStockLevel** 列の間でビット演算子包含的 OR を実行します。</span><span class="sxs-lookup"><span data-stu-id="947c9-125">This example performs a bitwise inclusive OR operation between the **ReorderPoint** and **SafetyStockLevel** columns.</span></span>  
  
```  
ReorderPoint | SafetyStockLevel  
```  
  
 <span data-ttu-id="947c9-126">**ReorderPoint** が 10 で **SafetyStockLevel** が 8 の場合、式は 10 (00001010) に評価されます。</span><span class="sxs-lookup"><span data-stu-id="947c9-126">If **ReorderPoint** is 10 and **SafetyStockLevel** is 8, the expression evaluates to 10 (00001010).</span></span>  
  
 <span data-ttu-id="947c9-127">00001010</span><span class="sxs-lookup"><span data-stu-id="947c9-127">00001010</span></span>  
  
 <span data-ttu-id="947c9-128">00001000</span><span class="sxs-lookup"><span data-stu-id="947c9-128">00001000</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="947c9-129">00001010</span><span class="sxs-lookup"><span data-stu-id="947c9-129">00001010</span></span>  
  
 <span data-ttu-id="947c9-130">この例では、2 つの整数間の包含的 OR 演算をビット単位で実行します。</span><span class="sxs-lookup"><span data-stu-id="947c9-130">This example performs a bitwise inclusive OR operation between two integers.</span></span>  
  
```  
3 | 5   
```  
  
 <span data-ttu-id="947c9-131">式は 7 (00001011) に評価されます。</span><span class="sxs-lookup"><span data-stu-id="947c9-131">The expression evaluates to 7 (00000111).</span></span>  
  
 <span data-ttu-id="947c9-132">00000011</span><span class="sxs-lookup"><span data-stu-id="947c9-132">00000011</span></span>  
  
 <span data-ttu-id="947c9-133">00000101</span><span class="sxs-lookup"><span data-stu-id="947c9-133">00000101</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="947c9-134">00000111</span><span class="sxs-lookup"><span data-stu-id="947c9-134">00000111</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="947c9-135">参照</span><span class="sxs-lookup"><span data-stu-id="947c9-135">See Also</span></span>  
 <span data-ttu-id="947c9-136">[&#124;&#124; (論理 OR) (SSIS 式)](logical-or-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="947c9-136">[&#124;&#124; &#40;Logical OR&#41; &#40;SSIS Expression&#41;](logical-or-ssis-expression.md) </span></span>  
 <span data-ttu-id="947c9-137">[^ &#40;ビット演算子排他的 OR&#41; &#40;SSIS 式&#41;](bitwise-exclusive-or-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="947c9-137">[^ &#40;Bitwise Exclusive OR&#41; &#40;SSIS Expression&#41;](bitwise-exclusive-or-ssis-expression.md) </span></span>  
 <span data-ttu-id="947c9-138">[演算子の優先順位と結合規則](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="947c9-138">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="947c9-139">演算子 &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="947c9-139">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
