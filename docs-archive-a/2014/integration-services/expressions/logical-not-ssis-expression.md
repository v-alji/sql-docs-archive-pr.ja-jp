---
title: '! (論理 Not) (SSIS 式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logical Not (!)
- '! (logical Not)'
ms.assetid: d5c4d1e1-7be4-4d25-bcd9-5b6ddb53b3b3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1bbf313930575e864f1556952425567fca96db15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640164"
---
# <a name="-logical-not-ssis-expression"></a><span data-ttu-id="4d6df-103">!</span><span class="sxs-lookup"><span data-stu-id="4d6df-103">!</span></span> <span data-ttu-id="4d6df-104">(論理 Not) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="4d6df-104">(Logical Not) (SSIS Expression)</span></span>
  <span data-ttu-id="4d6df-105">ブール型のオペランドを否定します。</span><span class="sxs-lookup"><span data-stu-id="4d6df-105">Negates a Boolean operand.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d6df-106">!</span><span class="sxs-lookup"><span data-stu-id="4d6df-106">The !</span></span> <span data-ttu-id="4d6df-107">演算子は、他の演算子と組み合わせて使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="4d6df-107">operator cannot be used in conjunction with other operators.</span></span> <span data-ttu-id="4d6df-108">たとえば、!</span><span class="sxs-lookup"><span data-stu-id="4d6df-108">For example, you cannot combine the !</span></span> <span data-ttu-id="4d6df-109">演算子と > 演算子を組み合わせて !></span><span class="sxs-lookup"><span data-stu-id="4d6df-109">and the > operators into the !>.</span></span> <span data-ttu-id="4d6df-110">演算子にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="4d6df-110">operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d6df-111">構文</span><span class="sxs-lookup"><span data-stu-id="4d6df-111">Syntax</span></span>  
  
```  
  
!boolean_expression  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="4d6df-112">引数</span><span class="sxs-lookup"><span data-stu-id="4d6df-112">Arguments</span></span>  
 <span data-ttu-id="4d6df-113">*boolean_expression*</span><span class="sxs-lookup"><span data-stu-id="4d6df-113">*boolean_expression*</span></span>  
 <span data-ttu-id="4d6df-114">ブール型に評価される任意の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="4d6df-114">Is any valid expression that evaluates to a Boolean.</span></span> <span data-ttu-id="4d6df-115">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d6df-115">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="4d6df-116">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="4d6df-116">Result Types</span></span>  
 <span data-ttu-id="4d6df-117">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="4d6df-117">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d6df-118">解説</span><span class="sxs-lookup"><span data-stu-id="4d6df-118">Remarks</span></span>  
 <span data-ttu-id="4d6df-119">次の表は、!</span><span class="sxs-lookup"><span data-stu-id="4d6df-119">The following table shows the result of the !</span></span> <span data-ttu-id="4d6df-120">操作を完了するための次の手順について引き続き調査中です。</span><span class="sxs-lookup"><span data-stu-id="4d6df-120">operation.</span></span>  
  
|<span data-ttu-id="4d6df-121">元のブール式</span><span class="sxs-lookup"><span data-stu-id="4d6df-121">Original Boolean expression</span></span>|<span data-ttu-id="4d6df-122">! 演算子の適用後</span><span class="sxs-lookup"><span data-stu-id="4d6df-122">After applying the !</span></span> <span data-ttu-id="4d6df-123">operator</span><span class="sxs-lookup"><span data-stu-id="4d6df-123">operator</span></span>|  
|---------------------------------|------------------------------------|  
|<span data-ttu-id="4d6df-124">TRUE</span><span class="sxs-lookup"><span data-stu-id="4d6df-124">TRUE</span></span>|<span data-ttu-id="4d6df-125">FALSE</span><span class="sxs-lookup"><span data-stu-id="4d6df-125">FALSE</span></span>|  
|<span data-ttu-id="4d6df-126">NULL</span><span class="sxs-lookup"><span data-stu-id="4d6df-126">NULL</span></span>|<span data-ttu-id="4d6df-127">NULL</span><span class="sxs-lookup"><span data-stu-id="4d6df-127">NULL</span></span>|  
|<span data-ttu-id="4d6df-128">FALSE</span><span class="sxs-lookup"><span data-stu-id="4d6df-128">FALSE</span></span>|<span data-ttu-id="4d6df-129">TRUE</span><span class="sxs-lookup"><span data-stu-id="4d6df-129">TRUE</span></span>|  
  
## <a name="expression-examples"></a><span data-ttu-id="4d6df-130">式の例</span><span class="sxs-lookup"><span data-stu-id="4d6df-130">Expression Examples</span></span>  
 <span data-ttu-id="4d6df-131">**Color** 列の値が "red" の場合、この例は FALSE に評価されます。</span><span class="sxs-lookup"><span data-stu-id="4d6df-131">This example evaluates to FALSE if the **Color** column value is "red".</span></span>  
  
```  
!(Color == "red")  
```  
  
 <span data-ttu-id="4d6df-132">**MonthNumber** 変数の値が現在の月を示す整数と同じ場合、この例は TRUE に評価されます。</span><span class="sxs-lookup"><span data-stu-id="4d6df-132">This example evaluates to TRUE if the value of the **MonthNumber** variable is the same as the integer that represents the current month.</span></span> <span data-ttu-id="4d6df-133">詳細については、「[MONTH &#40;SSIS 式&#41;](month-ssis-expression.md)」および「[GETDATE &#40;SSIS 式&#41;](getdate-ssis-expression.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4d6df-133">For more information, see [MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) and [GETDATE &#40;SSIS Expression&#41;](getdate-ssis-expression.md).</span></span>  
  
```  
!(@MonthNumber != MONTH(GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d6df-134">参照</span><span class="sxs-lookup"><span data-stu-id="4d6df-134">See Also</span></span>  
 <span data-ttu-id="4d6df-135">[演算子の優先順位と結合規則](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="4d6df-135">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="4d6df-136">演算子 &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="4d6df-136">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
