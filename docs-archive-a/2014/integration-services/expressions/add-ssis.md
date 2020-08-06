---
title: + (加算) (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- + (add)
- add operator (+)
- adding expressions
ms.assetid: 44df4154-fed5-4e7f-9995-e703a0164f6a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fe1e8f2118e6328582cb24abfd44eef5f3b15f79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642939"
---
# <a name="-add-ssis"></a><span data-ttu-id="68e60-102">+ (加算) (SSIS)</span><span class="sxs-lookup"><span data-stu-id="68e60-102">+ (Add) (SSIS)</span></span>
  <span data-ttu-id="68e60-103">2 つの数値式を加算します。</span><span class="sxs-lookup"><span data-stu-id="68e60-103">Adds two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68e60-104">構文</span><span class="sxs-lookup"><span data-stu-id="68e60-104">Syntax</span></span>  
  
```  
  
numeric_expression1 + numeric_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="68e60-105">引数</span><span class="sxs-lookup"><span data-stu-id="68e60-105">Arguments</span></span>  
 <span data-ttu-id="68e60-106">*numeric_expression1、numeric_ expression2*</span><span class="sxs-lookup"><span data-stu-id="68e60-106">*numeric_expression1, numeric_ expression2*</span></span>  
 <span data-ttu-id="68e60-107">数値データ型の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="68e60-107">Is any valid expression of a numeric data type.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="68e60-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="68e60-108">Result Types</span></span>  
 <span data-ttu-id="68e60-109">2 つの引数のデータ型によって決まります。</span><span class="sxs-lookup"><span data-stu-id="68e60-109">Determined by data types of the two arguments.</span></span> <span data-ttu-id="68e60-110">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68e60-110">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68e60-111">解説</span><span class="sxs-lookup"><span data-stu-id="68e60-111">Remarks</span></span>  
 <span data-ttu-id="68e60-112">オペランドのいずれかが NULL の場合、結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="68e60-112">If either operand is null, the result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="68e60-113">式の例</span><span class="sxs-lookup"><span data-stu-id="68e60-113">Expression Examples</span></span>  
 <span data-ttu-id="68e60-114">この例では、数値リテラルを加算します。</span><span class="sxs-lookup"><span data-stu-id="68e60-114">This example adds numeric literals.</span></span>  
  
```  
5 + 6.09 + 7.0  
```  
  
 <span data-ttu-id="68e60-115">この例では、 **VacationHours** 列と **SickLeaveHours** 列の値を加算します。</span><span class="sxs-lookup"><span data-stu-id="68e60-115">This example adds values in the **VacationHours** and **SickLeaveHours** columns.</span></span>  
  
```  
VacationHours + SickLeaveHours  
```  
  
 <span data-ttu-id="68e60-116">この例では、計算した値を **StandardCost** 列に加算します。</span><span class="sxs-lookup"><span data-stu-id="68e60-116">This example adds a calculated value to the **StandardCost** column.</span></span> <span data-ttu-id="68e60-117">変数 **Profit%** は、名前に % 文字が含まれているため、角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="68e60-117">The variable **Profit%** must be enclosed in brackets because the name includes the % character.</span></span> <span data-ttu-id="68e60-118">詳しくは、「[識別子 &#40;SSIS&#41;](identifiers-ssis.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="68e60-118">For more information, see [Identifiers &#40;SSIS&#41;](identifiers-ssis.md).</span></span>  
  
```  
StandardCost + (StandardCost * @[Profit%])  
```  
  
## <a name="see-also"></a><span data-ttu-id="68e60-119">参照</span><span class="sxs-lookup"><span data-stu-id="68e60-119">See Also</span></span>  
 <span data-ttu-id="68e60-120">[演算子の優先順位と結合規則](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="68e60-120">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="68e60-121">演算子 &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="68e60-121">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
