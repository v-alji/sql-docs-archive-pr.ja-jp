---
title: POWER (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- POWER function
ms.assetid: db48ae65-bfa6-4db1-8d3c-d0d4f8a399bc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e1f5742f482ae52620ec11d95b84cb3d06199fab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641743"
---
# <a name="power-ssis-expression"></a><span data-ttu-id="9428b-102">POWER (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="9428b-102">POWER (SSIS Expression)</span></span>
  <span data-ttu-id="9428b-103">指定された数値式の結果をべき乗値で返します。</span><span class="sxs-lookup"><span data-stu-id="9428b-103">Returns the result of raising a numeric expression to a power.</span></span> <span data-ttu-id="9428b-104">power パラメーターは整数に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="9428b-104">The power parameter must evaluate to an integer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9428b-105">構文</span><span class="sxs-lookup"><span data-stu-id="9428b-105">Syntax</span></span>  
  
```  
  
POWER(numeric_expression,power)  
```  
  
## <a name="arguments"></a><span data-ttu-id="9428b-106">引数</span><span class="sxs-lookup"><span data-stu-id="9428b-106">Arguments</span></span>  
 <span data-ttu-id="9428b-107">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="9428b-107">*numeric_expression*</span></span>  
 <span data-ttu-id="9428b-108">有効な数値式です。</span><span class="sxs-lookup"><span data-stu-id="9428b-108">Is a valid numeric expression.</span></span>  
  
 <span data-ttu-id="9428b-109">*power*</span><span class="sxs-lookup"><span data-stu-id="9428b-109">*power*</span></span>  
 <span data-ttu-id="9428b-110">有効な数値式です。</span><span class="sxs-lookup"><span data-stu-id="9428b-110">Is a valid numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9428b-111">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="9428b-111">Result Types</span></span>  
 <span data-ttu-id="9428b-112">DT_R8</span><span class="sxs-lookup"><span data-stu-id="9428b-112">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9428b-113">解説</span><span class="sxs-lookup"><span data-stu-id="9428b-113">Remarks</span></span>  
 <span data-ttu-id="9428b-114">*numeric_expression* 引数と *power* 引数は、べき乗値の計算前に DT_R8 データ型にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="9428b-114">The *numeric_expression* and *power* arguments are cast to the DT_R8 data type before the power is computed.</span></span> <span data-ttu-id="9428b-115">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9428b-115">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="9428b-116">*numeric_expression* が 0 に評価され、 *power* が負の値の場合、式エバリュエーターはエラーを返し、返される結果を NULL に設定します。</span><span class="sxs-lookup"><span data-stu-id="9428b-116">If *numeric_expression* evaluates to zero and *power* is negative, the expression evaluator returns an error and sets the return result to null.</span></span>  
  
 <span data-ttu-id="9428b-117">*numeric_expression* または *power* の結果が不確定に評価される場合、返される結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="9428b-117">If *numeric_expression* or *power* evaluate to indeterminate results, the return result is null.</span></span>  
  
 <span data-ttu-id="9428b-118">*power* 引数には小数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9428b-118">The *power* argument can be a fraction.</span></span> <span data-ttu-id="9428b-119">たとえば、power 引数として値 0.5 を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9428b-119">For example, you can use the value 0.5 as the power.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="9428b-120">式の例</span><span class="sxs-lookup"><span data-stu-id="9428b-120">Expression Examples</span></span>  
 <span data-ttu-id="9428b-121">この例では、数値リテラルを使用しています。</span><span class="sxs-lookup"><span data-stu-id="9428b-121">This example uses a numeric literal.</span></span> <span data-ttu-id="9428b-122">関数は、4 を 3 乗して 64 を返します。</span><span class="sxs-lookup"><span data-stu-id="9428b-122">The function raises 4 to the power of 3 and returns 64.</span></span>  
  
```  
POWER(4,3)  
```  
  
 <span data-ttu-id="9428b-123">この例では、 **Length** 列と **DimensionCount** 変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="9428b-123">This example uses the **Length** column and the **DimensionCount** variable.</span></span> <span data-ttu-id="9428b-124">**Length** が 8、 **DimensionCount** が 2 の場合、返される結果は 64 になります。</span><span class="sxs-lookup"><span data-stu-id="9428b-124">If **Length** is 8, and **DimensionCount** is 2, the return result is 64.</span></span>  
  
```  
POWER(Length, @DimensionCount)   
```  
  
## <a name="see-also"></a><span data-ttu-id="9428b-125">参照</span><span class="sxs-lookup"><span data-stu-id="9428b-125">See Also</span></span>  
 [<span data-ttu-id="9428b-126">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="9428b-126">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
