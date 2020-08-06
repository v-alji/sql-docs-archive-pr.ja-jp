---
title: ~ (ビット演算 Not) (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: e4413ddd-0d0e-40c3-9c76-b5ce323218ec
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 75745a0650c1744064f2a671659879e11464514e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642927"
---
# <a name="-bitwise-not-ssis-expression"></a><span data-ttu-id="831a4-102">~ (ビット演算 Not) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="831a4-102">~ (Bitwise Not) (SSIS Expression)</span></span>
  <span data-ttu-id="831a4-103">整数の否定のビット演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="831a4-103">Performs a bitwise negation of an integer.</span></span> <span data-ttu-id="831a4-104">この演算子は、符号付きおよび符号なし整数データ型に適用できます。</span><span class="sxs-lookup"><span data-stu-id="831a4-104">This operator can be applied to signed and unsigned integer data types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="831a4-105">構文</span><span class="sxs-lookup"><span data-stu-id="831a4-105">Syntax</span></span>  
  
```  
  
~integer_expression  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="831a4-106">引数</span><span class="sxs-lookup"><span data-stu-id="831a4-106">Arguments</span></span>  
 <span data-ttu-id="831a4-107">*integer_expression*</span><span class="sxs-lookup"><span data-stu-id="831a4-107">*integer_expression*</span></span>  
 <span data-ttu-id="831a4-108">整数データ型の任意の有効な式を指定します。</span><span class="sxs-lookup"><span data-stu-id="831a4-108">Is any valid expression of an integer data type.</span></span> <span data-ttu-id="831a4-109">*integer*_*expression* は整数で、ビット演算用に 2 進数に変換されます。</span><span class="sxs-lookup"><span data-stu-id="831a4-109">*integer*_*expression* is an integer that is transformed into a binary number for the bitwise operation.</span></span> <span data-ttu-id="831a4-110">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="831a4-110">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="831a4-111">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="831a4-111">Result Types</span></span>  
 <span data-ttu-id="831a4-112">データ型を返す *integer_expression*です。</span><span class="sxs-lookup"><span data-stu-id="831a4-112">Returns the data type of *integer_expression.*</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="831a4-113">解説</span><span class="sxs-lookup"><span data-stu-id="831a4-113">Remarks</span></span>  
 <span data-ttu-id="831a4-114">なし</span><span class="sxs-lookup"><span data-stu-id="831a4-114">None</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="831a4-115">式の例</span><span class="sxs-lookup"><span data-stu-id="831a4-115">Expression Examples</span></span>  
 <span data-ttu-id="831a4-116">この例では、数値 170 (0000 0000 1010 1010) に対し、ビット演算 ~ (NOT) を実行します。</span><span class="sxs-lookup"><span data-stu-id="831a4-116">This example performs a bitwise ~ (NOT) operation on the number 170 (0000 0000 1010 1010).</span></span> <span data-ttu-id="831a4-117">この数値は符号付き整数です。</span><span class="sxs-lookup"><span data-stu-id="831a4-117">The number is a signed integer.</span></span>  
  
```  
  
~ 170  
```  
  
 <span data-ttu-id="831a4-118">式は -170 (1111111101010101) に評価されます。</span><span class="sxs-lookup"><span data-stu-id="831a4-118">The expression evaluates to -170 (1111111101010101).</span></span>  
  
 <span data-ttu-id="831a4-119">0000000010101010</span><span class="sxs-lookup"><span data-stu-id="831a4-119">0000000010101010</span></span>  
  
 ---------------------\-  
  
 <span data-ttu-id="831a4-120">1111111101010101</span><span class="sxs-lookup"><span data-stu-id="831a4-120">1111111101010101</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="831a4-121">参照</span><span class="sxs-lookup"><span data-stu-id="831a4-121">See Also</span></span>  
 <span data-ttu-id="831a4-122">[演算子の優先順位と結合規則](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="831a4-122">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="831a4-123">演算子 &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="831a4-123">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
