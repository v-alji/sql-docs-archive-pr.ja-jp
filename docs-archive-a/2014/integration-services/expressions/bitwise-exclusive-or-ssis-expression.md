---
title: ^ (ビット演算排他的 OR) (SSIS 式)| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- ^ (bitwise exclusive OR operator)
- bitwise exclusive OR (^)
ms.assetid: 6ac53cab-29c4-4835-9f87-371b058b2f38
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d86c3d810e9e5572af93c97f82c2275db2c979b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642935"
---
# <a name="-bitwise-exclusive-or-ssis-expression"></a><span data-ttu-id="717b6-102">^ (ビット演算排他的 OR) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="717b6-102">^ (Bitwise Exclusive OR) (SSIS Expression)</span></span>
  <span data-ttu-id="717b6-103">2 つの整数値の排他的 OR 演算をビット単位で実行します。</span><span class="sxs-lookup"><span data-stu-id="717b6-103">Performs a bitwise exclusive OR operation of two integer values.</span></span> <span data-ttu-id="717b6-104">最初のオペランドの各ビットを 2 番目のオペランドの対応するビットと比較します。</span><span class="sxs-lookup"><span data-stu-id="717b6-104">It compares each bit of its first operand to the corresponding bit of its second operand.</span></span> <span data-ttu-id="717b6-105">一方のビットが 0 でもう一方のビットが 1 の場合、対応する結果ビットは 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="717b6-105">If one bit is 0 and the other bit is 1, the corresponding result bit is set to 1.</span></span> <span data-ttu-id="717b6-106">両方のビットが 0、また両方のビットが 1 の場合、対応する結果ビットは 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="717b6-106">If both bits are 0 or both bits are 1, the corresponding result bit is set to 0.</span></span>  
  
 <span data-ttu-id="717b6-107">どちらの条件も符号付き整数データ型か、または、どちらの条件も符号なし整数データ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="717b6-107">Both conditions must be a signed integer data type or both conditions must be an unsigned integer data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="717b6-108">構文</span><span class="sxs-lookup"><span data-stu-id="717b6-108">Syntax</span></span>  
  
```  
  
integer_expression1 ^ integer_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="717b6-109">引数</span><span class="sxs-lookup"><span data-stu-id="717b6-109">Arguments</span></span>  
 <span data-ttu-id="717b6-110">*integer_expression1、integer_ expression2*</span><span class="sxs-lookup"><span data-stu-id="717b6-110">*integer_expression1, integer_expression2*</span></span>  
 <span data-ttu-id="717b6-111">符号付きまたは符号なし整数データ型の任意の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="717b6-111">Is any valid expression of a signed or unsigned integer data type.</span></span> <span data-ttu-id="717b6-112">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="717b6-112">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="717b6-113">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="717b6-113">Result Types</span></span>  
 <span data-ttu-id="717b6-114">2 つの引数のデータ型によって決まります。</span><span class="sxs-lookup"><span data-stu-id="717b6-114">Determined by data types of the two arguments.</span></span> <span data-ttu-id="717b6-115">詳しくは、「 [式における Integration Services データ型](integration-services-data-types-in-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="717b6-115">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="717b6-116">解説</span><span class="sxs-lookup"><span data-stu-id="717b6-116">Remarks</span></span>  
 <span data-ttu-id="717b6-117">条件のいずれかが NULL の場合、式の結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="717b6-117">If either condition is null, the expression result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="717b6-118">式の例</span><span class="sxs-lookup"><span data-stu-id="717b6-118">Expression Examples</span></span>  
 <span data-ttu-id="717b6-119">この例では、変数 **NumberA** と **NumberB**間の排他的 OR 演算をビット単位で実行します。</span><span class="sxs-lookup"><span data-stu-id="717b6-119">This example performs a bitwise exclusive OR operation between variables **NumberA** and **NumberB**.</span></span> <span data-ttu-id="717b6-120">**NumberA** には 3 (00000011) が、 **NumberB** には 7 (00000111) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="717b6-120">**NumberA** contains 3 (00000011) and **NumberB** contains 7 (00000111).</span></span>  
  
```  
@NumberA ^ @NumberB  
```  
  
 <span data-ttu-id="717b6-121">式は 4 (00000100) に評価されます。</span><span class="sxs-lookup"><span data-stu-id="717b6-121">The expression evaluates to 4 (00000100).</span></span>  
  
 <span data-ttu-id="717b6-122">00000011</span><span class="sxs-lookup"><span data-stu-id="717b6-122">00000011</span></span>  
  
 <span data-ttu-id="717b6-123">00000111</span><span class="sxs-lookup"><span data-stu-id="717b6-123">00000111</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="717b6-124">00000100</span><span class="sxs-lookup"><span data-stu-id="717b6-124">00000100</span></span>  
  
 <span data-ttu-id="717b6-125">この例では、 **ReorderPoint** 列と **SafetyStockLevel** 列の間の排他的 OR 演算をビット単位で実行します。</span><span class="sxs-lookup"><span data-stu-id="717b6-125">This example performs a bitwise exclusive OR operation between the **ReorderPoint** and **SafetyStockLevel** columns.</span></span>  
  
```  
ReorderPoint ^ SafetyStockLevel  
```  
  
 <span data-ttu-id="717b6-126">**ReorderPoint** が 10 で **SafetyStockLevel** が 8 の場合、式は 2 (00000010) に評価されます。</span><span class="sxs-lookup"><span data-stu-id="717b6-126">If **ReorderPoint** is 10 and **SafetyStockLevel** is 8, the expression evaluates to 2 (00000010).</span></span>  
  
 <span data-ttu-id="717b6-127">00001010</span><span class="sxs-lookup"><span data-stu-id="717b6-127">00001010</span></span>  
  
 <span data-ttu-id="717b6-128">00001000</span><span class="sxs-lookup"><span data-stu-id="717b6-128">00001000</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="717b6-129">00000010</span><span class="sxs-lookup"><span data-stu-id="717b6-129">00000010</span></span>  
  
 <span data-ttu-id="717b6-130">この例では、2 つの整数間の排他的 OR 演算をビット単位で実行します。</span><span class="sxs-lookup"><span data-stu-id="717b6-130">This example performs a bitwise exclusive OR operation between two integers.</span></span>  
  
```  
3 ^ 5   
```  
  
 <span data-ttu-id="717b6-131">式は 6 (00000110) に評価されます。</span><span class="sxs-lookup"><span data-stu-id="717b6-131">The expression evaluates to 6 (00000110).</span></span>  
  
 <span data-ttu-id="717b6-132">00000011</span><span class="sxs-lookup"><span data-stu-id="717b6-132">00000011</span></span>  
  
 <span data-ttu-id="717b6-133">00000101</span><span class="sxs-lookup"><span data-stu-id="717b6-133">00000101</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="717b6-134">00000110</span><span class="sxs-lookup"><span data-stu-id="717b6-134">00000110</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="717b6-135">参照</span><span class="sxs-lookup"><span data-stu-id="717b6-135">See Also</span></span>  
 <span data-ttu-id="717b6-136">[&#124;&#124; (論理 OR) (SSIS 式)](logical-or-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="717b6-136">[&#124;&#124; &#40;Logical OR&#41; &#40;SSIS Expression&#41;](logical-or-ssis-expression.md) </span></span>  
 <span data-ttu-id="717b6-137">[&#124; &#40;ビット演算包含的 OR&#41; &#40;SSIS 式&#41;](bitwise-inclusive-or-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="717b6-137">[&#124; &#40;Bitwise Inclusive OR&#41; &#40;SSIS Expression&#41;](bitwise-inclusive-or-ssis-expression.md) </span></span>  
 <span data-ttu-id="717b6-138">[演算子の優先順位と結合規則](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="717b6-138">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="717b6-139">演算子 &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="717b6-139">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
