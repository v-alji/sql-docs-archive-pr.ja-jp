---
title: '&amp;&amp; (論理 AND) (SSIS 式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '&& (logical AND)'
- AND, logical AND
- logical AND (&&)
ms.assetid: a8cb3517-d5d1-4861-9f04-905c719185ff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8d973d7d4e86f88f7ae88c820ed4e4a5c1ce526f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713349"
---
# <a name="ampamp-logical-and-ssis-expression"></a><span data-ttu-id="ba5fd-102">&amp;&amp; (論理 AND) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="ba5fd-102">&amp;&amp; (Logical AND) (SSIS Expression)</span></span>
  <span data-ttu-id="ba5fd-103">論理 AND 演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="ba5fd-103">Performs a logical AND operation.</span></span> <span data-ttu-id="ba5fd-104">両方の条件が TRUE の場合、式は TRUE に評価されます。</span><span class="sxs-lookup"><span data-stu-id="ba5fd-104">The expression evaluates to TRUE if all conditions are TRUE.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba5fd-105">構文</span><span class="sxs-lookup"><span data-stu-id="ba5fd-105">Syntax</span></span>  
  
```  
  
boolean_expression1 && boolean_expression2  
```  
  
## <a name="arguments"></a><span data-ttu-id="ba5fd-106">引数</span><span class="sxs-lookup"><span data-stu-id="ba5fd-106">Arguments</span></span>  
 <span data-ttu-id="ba5fd-107">*boolean _expression1, boolean_expression2*</span><span class="sxs-lookup"><span data-stu-id="ba5fd-107">*boolean _expression1, boolean_expression2*</span></span>  
 <span data-ttu-id="ba5fd-108">TRUE、FALSE、または NULL に評価される、任意の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="ba5fd-108">Is any valid expression that evaluates to TRUE, FALSE, or NULL.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="ba5fd-109">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="ba5fd-109">Result Types</span></span>  
 <span data-ttu-id="ba5fd-110">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="ba5fd-110">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba5fd-111">解説</span><span class="sxs-lookup"><span data-stu-id="ba5fd-111">Remarks</span></span>  
 <span data-ttu-id="ba5fd-112">次の表は、&& 演算子の結果を示します。</span><span class="sxs-lookup"><span data-stu-id="ba5fd-112">The following table shows the result of the && operator.</span></span>  
  
|<span data-ttu-id="ba5fd-113">結果</span><span class="sxs-lookup"><span data-stu-id="ba5fd-113">Result</span></span>|<span data-ttu-id="ba5fd-114">式</span><span class="sxs-lookup"><span data-stu-id="ba5fd-114">Expression</span></span>|<span data-ttu-id="ba5fd-115">式</span><span class="sxs-lookup"><span data-stu-id="ba5fd-115">Expression</span></span>|  
|------------|----------------|----------------|  
|<span data-ttu-id="ba5fd-116">TRUE</span><span class="sxs-lookup"><span data-stu-id="ba5fd-116">TRUE</span></span>|<span data-ttu-id="ba5fd-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="ba5fd-117">TRUE</span></span>|<span data-ttu-id="ba5fd-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="ba5fd-118">TRUE</span></span>|  
|<span data-ttu-id="ba5fd-119">FALSE</span><span class="sxs-lookup"><span data-stu-id="ba5fd-119">FALSE</span></span>|<span data-ttu-id="ba5fd-120">TRUE</span><span class="sxs-lookup"><span data-stu-id="ba5fd-120">TRUE</span></span>|<span data-ttu-id="ba5fd-121">FALSE</span><span class="sxs-lookup"><span data-stu-id="ba5fd-121">FALSE</span></span>|  
|<span data-ttu-id="ba5fd-122">FALSE</span><span class="sxs-lookup"><span data-stu-id="ba5fd-122">FALSE</span></span>|<span data-ttu-id="ba5fd-123">FALSE</span><span class="sxs-lookup"><span data-stu-id="ba5fd-123">FALSE</span></span>|<span data-ttu-id="ba5fd-124">FALSE</span><span class="sxs-lookup"><span data-stu-id="ba5fd-124">FALSE</span></span>|  
|<span data-ttu-id="ba5fd-125">NULL</span><span class="sxs-lookup"><span data-stu-id="ba5fd-125">NULL</span></span>|<span data-ttu-id="ba5fd-126">NULL</span><span class="sxs-lookup"><span data-stu-id="ba5fd-126">NULL</span></span>|<span data-ttu-id="ba5fd-127">NULL</span><span class="sxs-lookup"><span data-stu-id="ba5fd-127">NULL</span></span>|  
|<span data-ttu-id="ba5fd-128">NULL</span><span class="sxs-lookup"><span data-stu-id="ba5fd-128">NULL</span></span>|<span data-ttu-id="ba5fd-129">NULL</span><span class="sxs-lookup"><span data-stu-id="ba5fd-129">NULL</span></span>|<span data-ttu-id="ba5fd-130">TRUE</span><span class="sxs-lookup"><span data-stu-id="ba5fd-130">TRUE</span></span>|  
|<span data-ttu-id="ba5fd-131">FALSE</span><span class="sxs-lookup"><span data-stu-id="ba5fd-131">FALSE</span></span>|<span data-ttu-id="ba5fd-132">NULL</span><span class="sxs-lookup"><span data-stu-id="ba5fd-132">NULL</span></span>|<span data-ttu-id="ba5fd-133">FALSE</span><span class="sxs-lookup"><span data-stu-id="ba5fd-133">FALSE</span></span>|  
  
## <a name="expression-examples"></a><span data-ttu-id="ba5fd-134">式の例</span><span class="sxs-lookup"><span data-stu-id="ba5fd-134">Expression Examples</span></span>  
 <span data-ttu-id="ba5fd-135">この例では、 **StandardCost** 列と **ListPrice** 列を使用しています。</span><span class="sxs-lookup"><span data-stu-id="ba5fd-135">This example uses the **StandardCost** and the **ListPrice** columns.</span></span> <span data-ttu-id="ba5fd-136">**StandardCost** 列の値が 300 より小さく、かつ **ListPrice** 列の値が 500 より大きい場合、式は TRUE に評価されます。</span><span class="sxs-lookup"><span data-stu-id="ba5fd-136">The example evaluates to TRUE if the value of the **StandardCost** column is less than 300 and the **ListPrice** column is greater than 500.</span></span>  
  
```  
StandardCost < 300 && ListPrice > 500  
```  
  
 <span data-ttu-id="ba5fd-137">この例では、リテラルの代わりに変数 **SPrice** と **LPrice** を使用しています。</span><span class="sxs-lookup"><span data-stu-id="ba5fd-137">This example uses the variables **SPrice** and **LPrice** instead of literals.</span></span>  
  
```  
StandardCost < @SPrice && ListPrice > @LPrice  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba5fd-138">参照</span><span class="sxs-lookup"><span data-stu-id="ba5fd-138">See Also</span></span>  
 <span data-ttu-id="ba5fd-139">[& (ビット演算子 AND) (SSIS 式)](bitwise-and-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="ba5fd-139">[& &#40;Bitwise AND&#41; &#40;SSIS Expression&#41;](bitwise-and-ssis-expression.md) </span></span>  
 <span data-ttu-id="ba5fd-140">[演算子の優先順位と結合規則](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="ba5fd-140">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="ba5fd-141">演算子 &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="ba5fd-141">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
