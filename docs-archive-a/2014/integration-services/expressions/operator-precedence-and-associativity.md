---
title: 演算子の優先順位と結合規則 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- associativity [Integration Services]
- precedence [Integration Services]
ms.assetid: 5094164f-dabc-45b5-b611-384feb2b3fe3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 90ec23f9e961cbe4df291b9670c09e51d5d8704b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718597"
---
# <a name="operator-precedence-and-associativity"></a><span data-ttu-id="2d2fa-102">演算子の優先順位と結合規則</span><span class="sxs-lookup"><span data-stu-id="2d2fa-102">Operator Precedence and Associativity</span></span>
  <span data-ttu-id="2d2fa-103">式エバリュエーターがサポートする演算子セット内の各演算子には、優先順位の階層内で指定された優先順位があり、演算子が評価される方向が含まれています。</span><span class="sxs-lookup"><span data-stu-id="2d2fa-103">Each operator in the set of operators that the expression evaluator supports has a designated precedence in the precedence hierarchy and includes a direction in which it is evaluated.</span></span> <span data-ttu-id="2d2fa-104">演算子の評価の方向は、演算子の結合規則と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="2d2fa-104">The direction of evaluation for an operator is operator associativity.</span></span> <span data-ttu-id="2d2fa-105">優先順位の高い演算子が先に評価されます。</span><span class="sxs-lookup"><span data-stu-id="2d2fa-105">Operators with higher precedence are evaluated before operators with lower precedence.</span></span> <span data-ttu-id="2d2fa-106">複合式に複数の演算子がある場合、演算子の優先順位により、操作が実行される順序が決定されます。</span><span class="sxs-lookup"><span data-stu-id="2d2fa-106">If a complex expression has multiple operators, operator precedence determines the order in which the operations are performed.</span></span> <span data-ttu-id="2d2fa-107">実行される順序により、結果の値は大きく変わります。</span><span class="sxs-lookup"><span data-stu-id="2d2fa-107">The order of execution can significantly affect the resulting value.</span></span> <span data-ttu-id="2d2fa-108">演算子の一部には、優先順位が同じものがあります。</span><span class="sxs-lookup"><span data-stu-id="2d2fa-108">Some operators have equal precedence.</span></span> <span data-ttu-id="2d2fa-109">式に複数の演算子が含まれており、その優先順位が同じ場合、それらの演算子は、左から右または右から左の方向に評価されます。</span><span class="sxs-lookup"><span data-stu-id="2d2fa-109">If an expression contains multiple operators of equal precedence, the operators are evaluated directionally, from left to right or right to left.</span></span>  
  
 <span data-ttu-id="2d2fa-110">次の表に、演算子の優先順位が高い順に一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="2d2fa-110">The following table lists the precedence of operators in order of high to low.</span></span> <span data-ttu-id="2d2fa-111">同じレベルの演算子の優先順位は、同じです。</span><span class="sxs-lookup"><span data-stu-id="2d2fa-111">Operators at the same level have equal precedence.</span></span>  
  
|<span data-ttu-id="2d2fa-112">演算子記号</span><span class="sxs-lookup"><span data-stu-id="2d2fa-112">Operator symbol</span></span>|<span data-ttu-id="2d2fa-113">演算の種類</span><span class="sxs-lookup"><span data-stu-id="2d2fa-113">Type of Operation</span></span>|<span data-ttu-id="2d2fa-114">結合規則</span><span class="sxs-lookup"><span data-stu-id="2d2fa-114">Associativity</span></span>|  
|---------------------|-----------------------|-------------------|  
|<span data-ttu-id="2d2fa-115">( )</span><span class="sxs-lookup"><span data-stu-id="2d2fa-115">( )</span></span>|<span data-ttu-id="2d2fa-116">式</span><span class="sxs-lookup"><span data-stu-id="2d2fa-116">Expression</span></span>|<span data-ttu-id="2d2fa-117">左から右</span><span class="sxs-lookup"><span data-stu-id="2d2fa-117">Left to right</span></span>|  
|<span data-ttu-id="2d2fa-118">–、!、~</span><span class="sxs-lookup"><span data-stu-id="2d2fa-118">-, !, ~</span></span>|<span data-ttu-id="2d2fa-119">単項演算子</span><span class="sxs-lookup"><span data-stu-id="2d2fa-119">Unary</span></span>|<span data-ttu-id="2d2fa-120">右から左</span><span class="sxs-lookup"><span data-stu-id="2d2fa-120">Right to left</span></span>|  
|<span data-ttu-id="2d2fa-121">キャスト</span><span class="sxs-lookup"><span data-stu-id="2d2fa-121">casts</span></span>|<span data-ttu-id="2d2fa-122">単項演算子</span><span class="sxs-lookup"><span data-stu-id="2d2fa-122">Unary</span></span>|<span data-ttu-id="2d2fa-123">右から左</span><span class="sxs-lookup"><span data-stu-id="2d2fa-123">Right to left</span></span>|  
|<span data-ttu-id="2d2fa-124">\*、/、%</span><span class="sxs-lookup"><span data-stu-id="2d2fa-124">\*, / ,%</span></span>|<span data-ttu-id="2d2fa-125">乗算</span><span class="sxs-lookup"><span data-stu-id="2d2fa-125">Multiplicative</span></span>|<span data-ttu-id="2d2fa-126">左から右</span><span class="sxs-lookup"><span data-stu-id="2d2fa-126">Left to right</span></span>|  
|<span data-ttu-id="2d2fa-127">+、-</span><span class="sxs-lookup"><span data-stu-id="2d2fa-127">+, -</span></span>|<span data-ttu-id="2d2fa-128">加法</span><span class="sxs-lookup"><span data-stu-id="2d2fa-128">Additive</span></span>|<span data-ttu-id="2d2fa-129">左から右</span><span class="sxs-lookup"><span data-stu-id="2d2fa-129">Left to right</span></span>|  
|<span data-ttu-id="2d2fa-130">\<, >, \<=, >=</span><span class="sxs-lookup"><span data-stu-id="2d2fa-130">\<, >, \<=, >=</span></span>|<span data-ttu-id="2d2fa-131">リレーショナル</span><span class="sxs-lookup"><span data-stu-id="2d2fa-131">Relational</span></span>|<span data-ttu-id="2d2fa-132">左から右</span><span class="sxs-lookup"><span data-stu-id="2d2fa-132">Left to right</span></span>|  
|<span data-ttu-id="2d2fa-133">==、!=</span><span class="sxs-lookup"><span data-stu-id="2d2fa-133">==, !=</span></span>|<span data-ttu-id="2d2fa-134">等式</span><span class="sxs-lookup"><span data-stu-id="2d2fa-134">Equality</span></span>|<span data-ttu-id="2d2fa-135">左から右</span><span class="sxs-lookup"><span data-stu-id="2d2fa-135">Left to right</span></span>|  
|&|<span data-ttu-id="2d2fa-136">ビット演算子 AND</span><span class="sxs-lookup"><span data-stu-id="2d2fa-136">Bitwise AND</span></span>|<span data-ttu-id="2d2fa-137">左から右</span><span class="sxs-lookup"><span data-stu-id="2d2fa-137">Left to right</span></span>|  
|^|<span data-ttu-id="2d2fa-138">ビット演算子排他的 OR</span><span class="sxs-lookup"><span data-stu-id="2d2fa-138">Bitwise exclusive OR</span></span>|<span data-ttu-id="2d2fa-139">左から右</span><span class="sxs-lookup"><span data-stu-id="2d2fa-139">Left to right</span></span>|  
|<span data-ttu-id="2d2fa-140">&#124;</span><span class="sxs-lookup"><span data-stu-id="2d2fa-140">&#124;</span></span>|<span data-ttu-id="2d2fa-141">ビット演算子包含的 OR</span><span class="sxs-lookup"><span data-stu-id="2d2fa-141">Bitwise inclusive OR</span></span>|<span data-ttu-id="2d2fa-142">左から右</span><span class="sxs-lookup"><span data-stu-id="2d2fa-142">Left to right</span></span>|  
|&&|<span data-ttu-id="2d2fa-143">論理積</span><span class="sxs-lookup"><span data-stu-id="2d2fa-143">Logical AND</span></span>|<span data-ttu-id="2d2fa-144">左から右</span><span class="sxs-lookup"><span data-stu-id="2d2fa-144">Left to right</span></span>|  
|<span data-ttu-id="2d2fa-145">&#124;&#124;</span><span class="sxs-lookup"><span data-stu-id="2d2fa-145">&#124;&#124;</span></span>|<span data-ttu-id="2d2fa-146">論理和</span><span class="sxs-lookup"><span data-stu-id="2d2fa-146">Logical OR</span></span>|<span data-ttu-id="2d2fa-147">左から右</span><span class="sxs-lookup"><span data-stu-id="2d2fa-147">Left to right</span></span>|  
|<span data-ttu-id="2d2fa-148">?</span><span class="sxs-lookup"><span data-stu-id="2d2fa-148">?</span></span> <span data-ttu-id="2d2fa-149">:</span><span class="sxs-lookup"><span data-stu-id="2d2fa-149">:</span></span>|<span data-ttu-id="2d2fa-150">条件式</span><span class="sxs-lookup"><span data-stu-id="2d2fa-150">Conditional expression</span></span>|<span data-ttu-id="2d2fa-151">右から左</span><span class="sxs-lookup"><span data-stu-id="2d2fa-151">Right to left</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2d2fa-152">参照</span><span class="sxs-lookup"><span data-stu-id="2d2fa-152">See Also</span></span>  
 [<span data-ttu-id="2d2fa-153">演算子 &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2d2fa-153">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
