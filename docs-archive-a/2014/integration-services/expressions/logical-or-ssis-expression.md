---
title: '|| (論理 OR) (SSIS 式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- OR operator
- logical OR (||)
- '|| (logical OR)'
ms.assetid: a3c07c09-f121-4187-9617-b01adcf843c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 72d4a1c7b54856675f0faa7f5f58452cb8bca450
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713350"
---
# <a name="-logical-or-ssis-expression"></a><span data-ttu-id="dc3d2-102">|| (論理 OR) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="dc3d2-102">|| (Logical OR) (SSIS Expression)</span></span>
  <span data-ttu-id="dc3d2-103">論理 OR 演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="dc3d2-103">Performs a logical OR operation.</span></span> <span data-ttu-id="dc3d2-104">一方または両方の条件が TRUE の場合、式は TRUE に評価されます。</span><span class="sxs-lookup"><span data-stu-id="dc3d2-104">The expression evaluates to TRUE if one or both conditions are TRUE.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc3d2-105">構文</span><span class="sxs-lookup"><span data-stu-id="dc3d2-105">Syntax</span></span>  
  
```  
  
boolean_expression1 || boolean_expression2  
```  
  
## <a name="arguments"></a><span data-ttu-id="dc3d2-106">引数</span><span class="sxs-lookup"><span data-stu-id="dc3d2-106">Arguments</span></span>  
 <span data-ttu-id="dc3d2-107">*boolean_expression1, boolean_expression2*</span><span class="sxs-lookup"><span data-stu-id="dc3d2-107">*boolean_expression1, boolean_expression2*</span></span>  
 <span data-ttu-id="dc3d2-108">TRUE、FALSE、または NULL に評価される、任意の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="dc3d2-108">Is any valid expression that evaluates to TRUE, FALSE, or NULL.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="dc3d2-109">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="dc3d2-109">Result Types</span></span>  
 <span data-ttu-id="dc3d2-110">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="dc3d2-110">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc3d2-111">解説</span><span class="sxs-lookup"><span data-stu-id="dc3d2-111">Remarks</span></span>  
 <span data-ttu-id="dc3d2-112">次の表は、|| 演算子の結果を示します。</span><span class="sxs-lookup"><span data-stu-id="dc3d2-112">The following table shows the result of the || operator.</span></span>  
  
|<span data-ttu-id="dc3d2-113">結果</span><span class="sxs-lookup"><span data-stu-id="dc3d2-113">Result</span></span>|<span data-ttu-id="dc3d2-114">式</span><span class="sxs-lookup"><span data-stu-id="dc3d2-114">Expression</span></span>|<span data-ttu-id="dc3d2-115">式</span><span class="sxs-lookup"><span data-stu-id="dc3d2-115">Expression</span></span>|  
|------------|----------------|----------------|  
|<span data-ttu-id="dc3d2-116">TRUE</span><span class="sxs-lookup"><span data-stu-id="dc3d2-116">TRUE</span></span>|<span data-ttu-id="dc3d2-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="dc3d2-117">TRUE</span></span>|<span data-ttu-id="dc3d2-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="dc3d2-118">TRUE</span></span>|  
|<span data-ttu-id="dc3d2-119">TRUE</span><span class="sxs-lookup"><span data-stu-id="dc3d2-119">TRUE</span></span>|<span data-ttu-id="dc3d2-120">TRUE</span><span class="sxs-lookup"><span data-stu-id="dc3d2-120">TRUE</span></span>|<span data-ttu-id="dc3d2-121">FALSE</span><span class="sxs-lookup"><span data-stu-id="dc3d2-121">FALSE</span></span>|  
|<span data-ttu-id="dc3d2-122">FALSE</span><span class="sxs-lookup"><span data-stu-id="dc3d2-122">FALSE</span></span>|<span data-ttu-id="dc3d2-123">FALSE</span><span class="sxs-lookup"><span data-stu-id="dc3d2-123">FALSE</span></span>|<span data-ttu-id="dc3d2-124">FALSE</span><span class="sxs-lookup"><span data-stu-id="dc3d2-124">FALSE</span></span>|  
|<span data-ttu-id="dc3d2-125">NULL</span><span class="sxs-lookup"><span data-stu-id="dc3d2-125">NULL</span></span>|<span data-ttu-id="dc3d2-126">NULL</span><span class="sxs-lookup"><span data-stu-id="dc3d2-126">NULL</span></span>|<span data-ttu-id="dc3d2-127">NULL</span><span class="sxs-lookup"><span data-stu-id="dc3d2-127">NULL</span></span>|  
|<span data-ttu-id="dc3d2-128">TRUE</span><span class="sxs-lookup"><span data-stu-id="dc3d2-128">TRUE</span></span>|<span data-ttu-id="dc3d2-129">NULL</span><span class="sxs-lookup"><span data-stu-id="dc3d2-129">NULL</span></span>|<span data-ttu-id="dc3d2-130">TRUE</span><span class="sxs-lookup"><span data-stu-id="dc3d2-130">TRUE</span></span>|  
|<span data-ttu-id="dc3d2-131">NULL</span><span class="sxs-lookup"><span data-stu-id="dc3d2-131">NULL</span></span>|<span data-ttu-id="dc3d2-132">NULL</span><span class="sxs-lookup"><span data-stu-id="dc3d2-132">NULL</span></span>|<span data-ttu-id="dc3d2-133">FALSE</span><span class="sxs-lookup"><span data-stu-id="dc3d2-133">FALSE</span></span>|  
  
## <a name="ssis-expression-examples"></a><span data-ttu-id="dc3d2-134">SSIS 式の例</span><span class="sxs-lookup"><span data-stu-id="dc3d2-134">SSIS Expression Examples</span></span>  
 <span data-ttu-id="dc3d2-135">この例では、 **StandardCost** 列と **ListPrice** 列を使用しています。</span><span class="sxs-lookup"><span data-stu-id="dc3d2-135">This example uses the **StandardCost** and **ListPrice** columns.</span></span> <span data-ttu-id="dc3d2-136">**StandardCost** 列の値が 300 より小さいか、または **ListPrice** 列の値が 500 より大きい場合、式は TRUE に評価されます。</span><span class="sxs-lookup"><span data-stu-id="dc3d2-136">The example evaluates to TRUE if the value of the **StandardCost** column is less than 300 or the **ListPrice** column is greater than 500.</span></span>  
  
```  
StandardCost < 300 || ListPrice > 500  
```  
  
 <span data-ttu-id="dc3d2-137">この例では、数値リテラルの代わりに変数 **SPrice** と **LPrice** を使用しています。</span><span class="sxs-lookup"><span data-stu-id="dc3d2-137">This example uses the variables **SPrice** and **LPrice** instead of numeric literals.</span></span>  
  
```  
StandardCost < @SPrice || ListPrice > @LPrice  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc3d2-138">参照</span><span class="sxs-lookup"><span data-stu-id="dc3d2-138">See Also</span></span>  
 <span data-ttu-id="dc3d2-139">[&#124; &#40;ビット演算包含的 OR&#41; &#40;SSIS 式&#41;](bitwise-inclusive-or-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="dc3d2-139">[&#124; &#40;Bitwise Inclusive OR&#41; &#40;SSIS Expression&#41;](bitwise-inclusive-or-ssis-expression.md) </span></span>  
 <span data-ttu-id="dc3d2-140">[^ &#40;ビット演算子排他的 OR&#41; &#40;SSIS 式&#41;](bitwise-exclusive-or-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="dc3d2-140">[^ &#40;Bitwise Exclusive OR&#41; &#40;SSIS Expression&#41;](bitwise-exclusive-or-ssis-expression.md) </span></span>  
 <span data-ttu-id="dc3d2-141">[演算子の優先順位と結合規則](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="dc3d2-141">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="dc3d2-142">演算子 &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="dc3d2-142">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
