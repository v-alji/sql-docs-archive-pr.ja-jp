---
title: (剰余) (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '% (modulo operator)'
- remainder of division operation
- modulo operator (%)
ms.assetid: e2920821-2f5b-4c76-8db8-8b9eddf4606f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2e23152fca9c9f2c7c3ac11490a56b03d1a1f9dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640162"
---
# <a name="modulo-ssis-expression"></a><span data-ttu-id="96ebe-102">(剰余) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="96ebe-102">(Modulo) (SSIS Expression)</span></span>
  <span data-ttu-id="96ebe-103">最初の数値式を 2 番目の数値式で割った剰余を整数値で返します。</span><span class="sxs-lookup"><span data-stu-id="96ebe-103">Provides the integer remainder after dividing the first numeric expression by the second one.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96ebe-104">構文</span><span class="sxs-lookup"><span data-stu-id="96ebe-104">Syntax</span></span>  
  
```  
  
dividend % divisor  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="96ebe-105">引数</span><span class="sxs-lookup"><span data-stu-id="96ebe-105">Arguments</span></span>  
 <span data-ttu-id="96ebe-106">*dividend*</span><span class="sxs-lookup"><span data-stu-id="96ebe-106">*dividend*</span></span>  
 <span data-ttu-id="96ebe-107">除算される数値式です。</span><span class="sxs-lookup"><span data-stu-id="96ebe-107">Is the numeric expression to divide.</span></span> <span data-ttu-id="96ebe-108">*dividend* には、有効な任意の数値式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="96ebe-108">*dividend* can be any valid numeric expression.</span></span> <span data-ttu-id="96ebe-109">詳しくは、「 [Integration Services のデータ型](../data-flow/integration-services-data-types.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="96ebe-109">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md)</span></span>  
  
 <span data-ttu-id="96ebe-110">*divisor*</span><span class="sxs-lookup"><span data-stu-id="96ebe-110">*divisor*</span></span>  
 <span data-ttu-id="96ebe-111">被除数を除算する数値式です。</span><span class="sxs-lookup"><span data-stu-id="96ebe-111">Is the numeric expression to divide the dividend by.</span></span> <span data-ttu-id="96ebe-112">*divisor* には、0 以外の有効な任意の数値式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="96ebe-112">*divisor* can be any valid numeric expression except zero.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="96ebe-113">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="96ebe-113">Result Types</span></span>  
 <span data-ttu-id="96ebe-114">2 つの引数のデータ型によって決まります。</span><span class="sxs-lookup"><span data-stu-id="96ebe-114">Determined by data types of the two arguments.</span></span> <span data-ttu-id="96ebe-115">詳しくは、「 [式における Integration Services データ型](integration-services-data-types-in-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="96ebe-115">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96ebe-116">解説</span><span class="sxs-lookup"><span data-stu-id="96ebe-116">Remarks</span></span>  
 <span data-ttu-id="96ebe-117">両方の式は、符号付きまたは符号なし整数データ型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="96ebe-117">Both expressions must evaluate to signed or unsigned integer data types.</span></span>  
  
 <span data-ttu-id="96ebe-118">オペランドのいずれかが NULL の場合、結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="96ebe-118">If either operand is null, the result is null.</span></span>  
  
 <span data-ttu-id="96ebe-119">剰余 0 は無効です。</span><span class="sxs-lookup"><span data-stu-id="96ebe-119">Modulo zero is not legal.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="96ebe-120">式の例</span><span class="sxs-lookup"><span data-stu-id="96ebe-120">Expression Examples</span></span>  
 <span data-ttu-id="96ebe-121">この例では、2 つの数値リテラルから剰余を計算します。</span><span class="sxs-lookup"><span data-stu-id="96ebe-121">This example computes the modulus from two numeric literals.</span></span> <span data-ttu-id="96ebe-122">結果は 3 です。</span><span class="sxs-lookup"><span data-stu-id="96ebe-122">The result is 3.</span></span>  
  
```  
42 % 13  
```  
  
 <span data-ttu-id="96ebe-123">この例では、 **SalesQuota** 列と数値リテラルから剰余を計算します。</span><span class="sxs-lookup"><span data-stu-id="96ebe-123">This example computes the modulus from the **SalesQuota** column and a numeric literal.</span></span>  
  
```  
SalesQuota % 12  
```  
  
 <span data-ttu-id="96ebe-124">この例では、2 つの数値変数 **Sales$** と **Month**から剰余を計算します。</span><span class="sxs-lookup"><span data-stu-id="96ebe-124">This example computes the modulus from two numeric variables **Sales$** and **Month**.</span></span> <span data-ttu-id="96ebe-125">変数 **Sales$** は、名前に $ 文字が含まれているため、角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="96ebe-125">The variable **Sales$** must be enclosed in brackets because the name includes the $ character.</span></span> <span data-ttu-id="96ebe-126">詳しくは、「[識別子 &#40;SSIS&#41;](identifiers-ssis.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="96ebe-126">For more information, see [Identifiers &#40;SSIS&#41;](identifiers-ssis.md).</span></span>  
  
```  
@[Sales$] % @Month  
```  
  
 <span data-ttu-id="96ebe-127">この例では、剰余演算子を使用して、 **Value** 変数の値が偶数か奇数かを判別し、条件演算子を使用して結果を示す文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="96ebe-127">This example uses the modulo operator to determine if the value of the **Value** variable is even or odd, and uses the conditional operator to return a string that describes the result.</span></span> <span data-ttu-id="96ebe-128">詳しくは、「[? : &#40;条件&#41; &#40;SSIS 式&#41;](conditional-ssis-expression.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="96ebe-128">For more information, see [? : &#40;Conditional&#41; &#40;SSIS Expression&#41;](conditional-ssis-expression.md).</span></span>  
  
```  
@Value % 2 == 0? "even":"odd"  
```  
  
## <a name="see-also"></a><span data-ttu-id="96ebe-129">参照</span><span class="sxs-lookup"><span data-stu-id="96ebe-129">See Also</span></span>  
 <span data-ttu-id="96ebe-130">[演算子の優先順位と結合規則](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="96ebe-130">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="96ebe-131">演算子 &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="96ebe-131">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
