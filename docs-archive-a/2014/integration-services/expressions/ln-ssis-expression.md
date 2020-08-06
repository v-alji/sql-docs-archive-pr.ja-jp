---
title: LN (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- LN function
- natural logarithm of expression [Integration Services]
ms.assetid: 55d7b657-b5fd-4753-9c81-54ed7575e720
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4c06d6e246cfa51f8e84eb93ab7eb73eab40c392
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642926"
---
# <a name="ln-ssis-expression"></a><span data-ttu-id="b1bee-102">LN (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="b1bee-102">LN (SSIS Expression)</span></span>
  <span data-ttu-id="b1bee-103">数値式の自然対数を返します。</span><span class="sxs-lookup"><span data-stu-id="b1bee-103">Returns the natural logarithm of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1bee-104">構文</span><span class="sxs-lookup"><span data-stu-id="b1bee-104">Syntax</span></span>  
  
```  
  
LN(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="b1bee-105">引数</span><span class="sxs-lookup"><span data-stu-id="b1bee-105">Arguments</span></span>  
 <span data-ttu-id="b1bee-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="b1bee-106">*numeric_expression*</span></span>  
 <span data-ttu-id="b1bee-107">0 でなく、かつ負の値でない有効な数値式です。</span><span class="sxs-lookup"><span data-stu-id="b1bee-107">Is a valid non-zero and non-negative numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="b1bee-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="b1bee-108">Result Types</span></span>  
 <span data-ttu-id="b1bee-109">DT_R8</span><span class="sxs-lookup"><span data-stu-id="b1bee-109">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1bee-110">解説</span><span class="sxs-lookup"><span data-stu-id="b1bee-110">Remarks</span></span>  
 <span data-ttu-id="b1bee-111">この数値式は、対数の計算前に DT_R8 データ型にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="b1bee-111">The numeric expression is cast to the DT_R8 data type before the logarithm is computed.</span></span> <span data-ttu-id="b1bee-112">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1bee-112">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="b1bee-113">*numeric_expression* が 0 または負の値に評価される場合、返される結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="b1bee-113">If *numeric_expression* evaluates to zero or a negative value, the return result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="b1bee-114">式の例</span><span class="sxs-lookup"><span data-stu-id="b1bee-114">Expression Examples</span></span>  
 <span data-ttu-id="b1bee-115">この例では、数値リテラルを使用しています。</span><span class="sxs-lookup"><span data-stu-id="b1bee-115">This example uses a numeric literal.</span></span> <span data-ttu-id="b1bee-116">この関数は、値 3.737766961828337 を返します。</span><span class="sxs-lookup"><span data-stu-id="b1bee-116">The function returns the value 3.737766961828337.</span></span>  
  
```  
LN(42)  
```  
  
 <span data-ttu-id="b1bee-117">この例では、列 **Length**を使用しています。</span><span class="sxs-lookup"><span data-stu-id="b1bee-117">This example uses the column **Length**.</span></span> <span data-ttu-id="b1bee-118">列の値が 53.99 の場合、この関数は 3.9887988442302 を返します。</span><span class="sxs-lookup"><span data-stu-id="b1bee-118">If the column value is 53.99, the function returns 3.9887988442302.</span></span>  
  
```  
LN(Length)   
```  
  
 <span data-ttu-id="b1bee-119">この例では、変数 **Length**を使用しています。</span><span class="sxs-lookup"><span data-stu-id="b1bee-119">This example uses the variable **Length**.</span></span> <span data-ttu-id="b1bee-120">変数は数値データ型である必要があります。または式に、数値データ型への明示的なキャストが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1bee-120">The variable must have a numeric data type or the expression must include an explicit cast to a numeric data type.</span></span> <span data-ttu-id="b1bee-121">**Length** が 234.567 の場合、関数は 5.45774126708797 を返します。</span><span class="sxs-lookup"><span data-stu-id="b1bee-121">If **Length** is 234.567, the function returns 5.45774126708797.</span></span>  
  
```  
LN(@Length)   
```  
  
## <a name="see-also"></a><span data-ttu-id="b1bee-122">参照</span><span class="sxs-lookup"><span data-stu-id="b1bee-122">See Also</span></span>  
 <span data-ttu-id="b1bee-123">[LOG (SSIS 式)](log-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="b1bee-123">[LOG &#40;SSIS Expression&#41;](log-ssis-expression.md) </span></span>  
 [<span data-ttu-id="b1bee-124">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="b1bee-124">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
