---
title: '&amp; (ビット演算 AND) (SSIS 式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- AND, bitwise AND
- '& (bitwise AND)'
- bitwise AND (&)
ms.assetid: 06d2958e-66a5-44d8-8bc4-56209ebe1ff2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fbf3c8ffcef079e25c82478947bc3b92a6b4be93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642934"
---
# <a name="amp-bitwise-and-ssis-expression"></a><span data-ttu-id="4a2d7-102">&amp; (ビット演算 AND) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="4a2d7-102">&amp; (Bitwise AND) (SSIS Expression)</span></span>
  <span data-ttu-id="4a2d7-103">2 つの整数値の AND 演算をビット単位で実行します。</span><span class="sxs-lookup"><span data-stu-id="4a2d7-103">Performs a bitwise AND operation of two integer values.</span></span> <span data-ttu-id="4a2d7-104">最初のオペランドの各ビットを 2 番目のオペランドの対応するビットと比較します。</span><span class="sxs-lookup"><span data-stu-id="4a2d7-104">It compares each bit of its first operand to the corresponding bit of its second operand.</span></span> <span data-ttu-id="4a2d7-105">両方のビットが 1 の場合、対応する結果ビットは 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="4a2d7-105">If both bits are 1, the corresponding result bit is set to 1.</span></span> <span data-ttu-id="4a2d7-106">それ以外の場合、対応する結果ビットは 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="4a2d7-106">Otherwise, the corresponding result bit is set to 0.</span></span>  
  
 <span data-ttu-id="4a2d7-107">条件はいずれも符号付き整数型であるか、いずれも符号なし整数型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a2d7-107">Both conditions must be a signed integer type or both conditions must be an unsigned integer type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a2d7-108">構文</span><span class="sxs-lookup"><span data-stu-id="4a2d7-108">Syntax</span></span>  
  
```  
  
integer_expression1 & integer_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="4a2d7-109">引数</span><span class="sxs-lookup"><span data-stu-id="4a2d7-109">Arguments</span></span>  
 <span data-ttu-id="4a2d7-110">*integer_expression1、integer_ expression2*</span><span class="sxs-lookup"><span data-stu-id="4a2d7-110">*integer_expression1, integer_expression2*</span></span>  
 <span data-ttu-id="4a2d7-111">符号付きまたは符号なし整数データ型の任意の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="4a2d7-111">Is any valid expression of a signed or unsigned integer data type.</span></span> <span data-ttu-id="4a2d7-112">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a2d7-112">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="4a2d7-113">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="4a2d7-113">Result Types</span></span>  
 <span data-ttu-id="4a2d7-114">2 つの引数のデータ型によって決まります。</span><span class="sxs-lookup"><span data-stu-id="4a2d7-114">Determined by data types of the two arguments.</span></span> <span data-ttu-id="4a2d7-115">詳しくは、「 [式における Integration Services データ型](integration-services-data-types-in-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4a2d7-115">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a2d7-116">解説</span><span class="sxs-lookup"><span data-stu-id="4a2d7-116">Remarks</span></span>  
 <span data-ttu-id="4a2d7-117">条件のいずれかが NULL の場合、式の結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="4a2d7-117">If either condition is null, the expression result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="4a2d7-118">式の例</span><span class="sxs-lookup"><span data-stu-id="4a2d7-118">Expression Examples</span></span>  
 <span data-ttu-id="4a2d7-119">この例では、列 **NumberA** と **NumberB**の間でビット演算子 AND を実行します。</span><span class="sxs-lookup"><span data-stu-id="4a2d7-119">This example performs a bitwise AND operation between the columns **NumberA** and **NumberB**.</span></span> <span data-ttu-id="4a2d7-120">列**NumberA** には 3 (0000011) が含まれ、列 **NumberB** には 7 (00000111) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4a2d7-120">**NumberA** contains 3 (0000011) and column **NumberB** contains 7 (00000111).</span></span>  
  
```  
NumberA & NumberB  
```  
  
 <span data-ttu-id="4a2d7-121">式は 3 (00000011) に評価されます。</span><span class="sxs-lookup"><span data-stu-id="4a2d7-121">The expression evaluates to 3 (00000011).</span></span>  
  
 <span data-ttu-id="4a2d7-122">00000011</span><span class="sxs-lookup"><span data-stu-id="4a2d7-122">00000011</span></span>  
  
 <span data-ttu-id="4a2d7-123">00000111</span><span class="sxs-lookup"><span data-stu-id="4a2d7-123">00000111</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="4a2d7-124">00000011</span><span class="sxs-lookup"><span data-stu-id="4a2d7-124">00000011</span></span>  
  
 <span data-ttu-id="4a2d7-125">この例では、列 **ReorderPoint** と **SafetyStockLevel** の間でビット演算子 AND を実行します。</span><span class="sxs-lookup"><span data-stu-id="4a2d7-125">This example performs a bitwise AND operation between the **ReorderPoint** and **SafetyStockLevel** columns.</span></span>  
  
```  
ReorderPoint & SafetyStockLevel  
```  
  
 <span data-ttu-id="4a2d7-126">**ReorderPoint** が 10 で **SafetyStockLevel** が 8 の場合、式は 8 (00001000) に評価されます。</span><span class="sxs-lookup"><span data-stu-id="4a2d7-126">If **ReorderPoint** is 10 and **SafetyStockLevel** is 8, the expression evaluates to 8 (00001000).</span></span>  
  
 <span data-ttu-id="4a2d7-127">00001010</span><span class="sxs-lookup"><span data-stu-id="4a2d7-127">00001010</span></span>  
  
 <span data-ttu-id="4a2d7-128">00001000</span><span class="sxs-lookup"><span data-stu-id="4a2d7-128">00001000</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="4a2d7-129">00001000</span><span class="sxs-lookup"><span data-stu-id="4a2d7-129">00001000</span></span>  
  
 <span data-ttu-id="4a2d7-130">この例では、2 つの整数間でビット演算子 AND を実行します。</span><span class="sxs-lookup"><span data-stu-id="4a2d7-130">This example performs a bitwise AND operation between two integers.</span></span>  
  
```  
3 & 5   
```  
  
 <span data-ttu-id="4a2d7-131">式は 1 (00000001) に評価されます。</span><span class="sxs-lookup"><span data-stu-id="4a2d7-131">The expression evaluates to 1(00000001).</span></span>  
  
 <span data-ttu-id="4a2d7-132">00000011</span><span class="sxs-lookup"><span data-stu-id="4a2d7-132">00000011</span></span>  
  
 <span data-ttu-id="4a2d7-133">00000101</span><span class="sxs-lookup"><span data-stu-id="4a2d7-133">00000101</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="4a2d7-134">00000001</span><span class="sxs-lookup"><span data-stu-id="4a2d7-134">00000001</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a2d7-135">参照</span><span class="sxs-lookup"><span data-stu-id="4a2d7-135">See Also</span></span>  
 <span data-ttu-id="4a2d7-136">[&& (論理 AND) (SSIS 式)](logical-and-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="4a2d7-136">[&& &#40;Logical AND&#41; &#40;SSIS Expression&#41;](logical-and-ssis-expression.md) </span></span>  
 <span data-ttu-id="4a2d7-137">[演算子の優先順位と結合規則](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="4a2d7-137">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="4a2d7-138">演算子 &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="4a2d7-138">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
