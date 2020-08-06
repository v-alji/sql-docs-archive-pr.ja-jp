---
title: 演算子 (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS, operators
- SQL Server Integration Services, operators
- operators [Integration Services]
- expressions [Integration Services], operators
ms.assetid: 33df3a3d-1f5c-429b-a3b9-52b7d8689089
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 652f53ef639e63e4868dabeea3f49b9303336043
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736624"
---
# <a name="operators-ssis-expression"></a><span data-ttu-id="fd544-102">演算子 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="fd544-102">Operators (SSIS Expression)</span></span>
  <span data-ttu-id="fd544-103">このセクションでは、式の言語が提供する演算子、および式エバリュエーターが使用する演算子の優先順位と結合性について説明します。</span><span class="sxs-lookup"><span data-stu-id="fd544-103">This section describes the operators the expression language provides and the operator precedence and associativity that the expression evaluator uses.</span></span>  
  
 <span data-ttu-id="fd544-104">次の表に、演算子に関するこのセクションのトピックの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="fd544-104">The following table lists topics about operators in this section.</span></span>  
  
|<span data-ttu-id="fd544-105">演算子</span><span class="sxs-lookup"><span data-stu-id="fd544-105">Operator</span></span>|<span data-ttu-id="fd544-106">説明</span><span class="sxs-lookup"><span data-stu-id="fd544-106">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="fd544-107">キャスト (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="fd544-107">Cast &#40;SSIS Expression&#41;</span></span>](cast-ssis-expression.md)|<span data-ttu-id="fd544-108">式をあるデータ型から別のデータ型に変換します。</span><span class="sxs-lookup"><span data-stu-id="fd544-108">Converts an expression from one data type to a different data type.</span></span>|  
|[<span data-ttu-id="fd544-109">() (括弧) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="fd544-109">&#40;&#41; &#40;Parentheses&#41; &#40;SSIS Expression&#41;</span></span>](parentheses-ssis-expression.md)|<span data-ttu-id="fd544-110">式の評価順序を特定します。</span><span class="sxs-lookup"><span data-stu-id="fd544-110">Identifies the evaluation order of expressions.</span></span>|  
|[<span data-ttu-id="fd544-111">+ (加算) (SSIS)</span><span class="sxs-lookup"><span data-stu-id="fd544-111">+ &#40;Add&#41; &#40;SSIS&#41;</span></span>](add-ssis.md)|<span data-ttu-id="fd544-112">2 つの数値式を加算します。</span><span class="sxs-lookup"><span data-stu-id="fd544-112">Adds two numeric expressions.</span></span>|  
|[<span data-ttu-id="fd544-113">+ (連結) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="fd544-113">+ &#40;Concatenate&#41; &#40;SSIS Expression&#41;</span></span>](concatenate-ssis-expression.md)|<span data-ttu-id="fd544-114">2 つの式を連結します。</span><span class="sxs-lookup"><span data-stu-id="fd544-114">Concatenates two expressions.</span></span>|  
|[<span data-ttu-id="fd544-115">- (減算) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="fd544-115">- &#40;Subtract&#41; &#40;SSIS Expression&#41;</span></span>](subtract-ssis-expression.md)|<span data-ttu-id="fd544-116">最初の数値式から 2 番目の数値式を減算します。</span><span class="sxs-lookup"><span data-stu-id="fd544-116">Subtracts the second numeric expression from the first one.</span></span>|  
|[<span data-ttu-id="fd544-117">- (否定) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="fd544-117">- &#40;Negate&#41; &#40;SSIS Expression&#41;</span></span>](negate-ssis-expression.md)|<span data-ttu-id="fd544-118">数値式を負数化します。</span><span class="sxs-lookup"><span data-stu-id="fd544-118">Negates a numeric expression.</span></span>|  
|[<span data-ttu-id="fd544-119">\* (乗算) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="fd544-119">&#42; &#40;Multiply&#41; &#40;SSIS Expression&#41;</span></span>](multiply-ssis-expression.md)|<span data-ttu-id="fd544-120">2 つの数値式を乗算します。</span><span class="sxs-lookup"><span data-stu-id="fd544-120">Multiplies two numeric expressions.</span></span>|  
|[<span data-ttu-id="fd544-121">除算 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="fd544-121">Divide &#40;SSIS Expression&#41;</span></span>](divide-ssis-expression.md)|<span data-ttu-id="fd544-122">最初の数値式を 2 番目の数値式で除算します。</span><span class="sxs-lookup"><span data-stu-id="fd544-122">Divides the first numeric expression by the second one.</span></span>|  
|[<span data-ttu-id="fd544-123">(剰余) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="fd544-123">&#40;Modulo&#41; &#40;SSIS Expression&#41;</span></span>](modulo-ssis-expression.md)|<span data-ttu-id="fd544-124">最初の数値式を 2 番目の数値式で割った剰余を整数値で返します。</span><span class="sxs-lookup"><span data-stu-id="fd544-124">Provides the integer remainder after dividing the first numeric expression by the second one.</span></span>|  
|[<span data-ttu-id="fd544-125">&#124;&#124; (論理 OR) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="fd544-125">&#124;&#124; &#40;Logical OR&#41; &#40;SSIS Expression&#41;</span></span>](logical-or-ssis-expression.md)|<span data-ttu-id="fd544-126">論理 OR 演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="fd544-126">Performs a logical OR operation.</span></span>|  
|[<span data-ttu-id="fd544-127">&& (論理 AND) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="fd544-127">&& &#40;Logical AND&#41; &#40;SSIS Expression&#41;</span></span>](logical-and-ssis-expression.md)|<span data-ttu-id="fd544-128">論理 AND 演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="fd544-128">Performs a logical AND operation.</span></span>|  
|[<span data-ttu-id="fd544-129">\! &#40;論理 NOT&#41; &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="fd544-129">\! &#40;Logical NOT&#41; &#40;SSIS Expression&#41;</span></span>](logical-not-ssis-expression.md)|<span data-ttu-id="fd544-130">ブール型のオペランドを否定します。</span><span class="sxs-lookup"><span data-stu-id="fd544-130">Negates a Boolean operand.</span></span>|  
|[<span data-ttu-id="fd544-131">&#124; (ビット演算子包括的 OR) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="fd544-131">&#124; &#40;Bitwise Inclusive OR&#41; &#40;SSIS Expression&#41;</span></span>](bitwise-inclusive-or-ssis-expression.md)|<span data-ttu-id="fd544-132">2 つの整数値の OR 演算をビット単位で実行します。</span><span class="sxs-lookup"><span data-stu-id="fd544-132">Performs a bitwise OR operation of two integer values.</span></span>|  
|[<span data-ttu-id="fd544-133">^ (ビット演算子排他的 OR) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="fd544-133">^ &#40;Bitwise Exclusive OR&#41; &#40;SSIS Expression&#41;</span></span>](bitwise-exclusive-or-ssis-expression.md)|<span data-ttu-id="fd544-134">2 つの整数値の排他的 OR 演算をビット単位で実行します。</span><span class="sxs-lookup"><span data-stu-id="fd544-134">Performs a bitwise exclusive OR operation of two integer values.</span></span>|  
|[<span data-ttu-id="fd544-135">& (ビット演算子 AND) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="fd544-135">& &#40;Bitwise AND&#41; &#40;SSIS Expression&#41;</span></span>](bitwise-and-ssis-expression.md)|<span data-ttu-id="fd544-136">2 つの整数値の AND 演算をビット単位で実行します。</span><span class="sxs-lookup"><span data-stu-id="fd544-136">Performs a bitwise AND operation of two integer values.</span></span>|  
|[<span data-ttu-id="fd544-137">~ (ビット演算子 Not) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="fd544-137">~ &#40;Bitwise Not&#41; &#40;SSIS Expression&#41;</span></span>](bitwise-not-ssis-expression.md)|<span data-ttu-id="fd544-138">整数の否定のビット演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="fd544-138">Performs a bitwise negation of an integer.</span></span>|  
|[<span data-ttu-id="fd544-139">== &#40;等しい&#41; &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="fd544-139">== &#40;Equal&#41; &#40;SSIS Expression&#41;</span></span>](equal-ssis-expression.md)|<span data-ttu-id="fd544-140">2 つの式が等しいかどうかを判別するための比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="fd544-140">Performs a comparison to determine if two expressions are equal.</span></span>|  
|[<span data-ttu-id="fd544-141">\!= &#40;等しくない&#41; &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="fd544-141">\!= &#40;Unequal&#41; &#40;SSIS Expression&#41;</span></span>](unequal-ssis-expression.md)|<span data-ttu-id="fd544-142">2 つの式が等しくないかどうかを判別するための比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="fd544-142">Performs a comparison to determine if two expressions are not equal.</span></span>|  
|[<span data-ttu-id="fd544-143">&#62; &#40;より大きい&#41; &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="fd544-143">&#62; &#40;Greater Than&#41; &#40;SSIS Expression&#41;</span></span>](greater-than-ssis-expression.md)|<span data-ttu-id="fd544-144">最初の式が 2 番目の式より大きいかどうかを判別するための比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="fd544-144">Performs a comparison to determine if the first expression is greater than the second one.</span></span>|  
|[<span data-ttu-id="fd544-145">&#60; &#40;より小さい&#41; &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="fd544-145">&#60; &#40;Less Than&#41; &#40;SSIS Expression&#41;</span></span>](less-than-ssis-expression.md)|<span data-ttu-id="fd544-146">最初の式が 2 番目の式未満かどうかを判別するための比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="fd544-146">Performs a comparison to determine if the first expression is less than the second one.</span></span>|  
|[<span data-ttu-id="fd544-147">&#62;= &#40;以上&#41; &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="fd544-147">&#62;= &#40;Greater Than or Equal To&#41; &#40;SSIS Expression&#41;</span></span>](greater-than-or-equal-to-ssis-expression.md)|<span data-ttu-id="fd544-148">最初の式が 2 番目の式以上かどうかを判別するための比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="fd544-148">Performs a comparison to determine if the first expression is greater than or equal to the second one.</span></span>|  
|[<span data-ttu-id="fd544-149">&#60;= &#40;以下&#41; &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="fd544-149">&#60;= &#40;Less Than or Equal To&#41; &#40;SSIS Expression&#41;</span></span>](less-than-or-equal-to-ssis-expression.md)|<span data-ttu-id="fd544-150">最初の式が 2 番目の式以下かどうかを判別するための比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="fd544-150">Performs a comparison to determine if the first expression is less than or equal to the second one.</span></span>|  
|[<span data-ttu-id="fd544-151">? : &#40;条件&#41; &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="fd544-151">? : &#40;Conditional&#41; &#40;SSIS Expression&#41;</span></span>](conditional-ssis-expression.md)|<span data-ttu-id="fd544-152">ブール式の評価に基づいて 2 つの式のうちのいずれかの式を返します。</span><span class="sxs-lookup"><span data-stu-id="fd544-152">Returns one of two expressions based on the evaluation of a Boolean expression.</span></span>|  
  
 <span data-ttu-id="fd544-153">優先順位の階層内における各演算子の配置の詳細については、「 [演算子の優先順位と結合規則](operator-precedence-and-associativity.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd544-153">For information about the placement of each operator in the precedence hierarchy, see [Operator Precedence and Associativity](operator-precedence-and-associativity.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd544-154">参照</span><span class="sxs-lookup"><span data-stu-id="fd544-154">See Also</span></span>  
 <span data-ttu-id="fd544-155">[関数 &#40;SSIS 式&#41;](functions-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="fd544-155">[Functions &#40;SSIS Expression&#41;](functions-ssis-expression.md) </span></span>  
 <span data-ttu-id="fd544-156">[Integration Services 式の詳細の例](examples-of-advanced-integration-services-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="fd544-156">[Examples of Advanced Integration Services Expressions](examples-of-advanced-integration-services-expressions.md) </span></span>  
 [<span data-ttu-id="fd544-157">Integration Services &#40;SSIS&#41; 式</span><span class="sxs-lookup"><span data-stu-id="fd544-157">Integration Services &#40;SSIS&#41; Expressions</span></span>](integration-services-ssis-expressions.md)  
  
  
