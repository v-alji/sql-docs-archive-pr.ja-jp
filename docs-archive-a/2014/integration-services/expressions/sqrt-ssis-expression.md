---
title: SQRT (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQRT function
- square root of given expression
ms.assetid: 54a75389-c501-4e22-87b8-905f66d6a3a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9efa3f8da2e5280692aa65a25610211aba2fa40f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716473"
---
# <a name="sqrt-ssis-expression"></a><span data-ttu-id="2ca63-102">SQRT (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="2ca63-102">SQRT (SSIS Expression)</span></span>
  <span data-ttu-id="2ca63-103">数値式の平方根を返します。</span><span class="sxs-lookup"><span data-stu-id="2ca63-103">Returns the square root of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ca63-104">構文</span><span class="sxs-lookup"><span data-stu-id="2ca63-104">Syntax</span></span>  
  
```  
  
SQRT(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="2ca63-105">引数</span><span class="sxs-lookup"><span data-stu-id="2ca63-105">Arguments</span></span>  
 <span data-ttu-id="2ca63-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="2ca63-106">*numeric_expression*</span></span>  
 <span data-ttu-id="2ca63-107">任意の数値データ型の数値式です。</span><span class="sxs-lookup"><span data-stu-id="2ca63-107">Is a numeric expression of any numeric data type.</span></span> <span data-ttu-id="2ca63-108">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ca63-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="2ca63-109">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="2ca63-109">Result Types</span></span>  
 <span data-ttu-id="2ca63-110">DT_R8</span><span class="sxs-lookup"><span data-stu-id="2ca63-110">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ca63-111">解説</span><span class="sxs-lookup"><span data-stu-id="2ca63-111">Remarks</span></span>  
 <span data-ttu-id="2ca63-112">引数が NULL の場合、SQRT 関数は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="2ca63-112">SQRT returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="2ca63-113">引数が負の値の場合、SQRT 関数の処理は失敗します。</span><span class="sxs-lookup"><span data-stu-id="2ca63-113">SQRT fails if the argument is a negative value.</span></span>  
  
 <span data-ttu-id="2ca63-114">平方根演算の前に、引数は DT_R8 データ型にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="2ca63-114">The argument is cast to the DT_R8 data type before the square root operation.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="2ca63-115">式の例</span><span class="sxs-lookup"><span data-stu-id="2ca63-115">Expression Examples</span></span>  
 <span data-ttu-id="2ca63-116">この例では、数値リテラルの平方根が返されます。</span><span class="sxs-lookup"><span data-stu-id="2ca63-116">This example returns the square root of a numeric literal.</span></span> <span data-ttu-id="2ca63-117">返される結果は 12 です。</span><span class="sxs-lookup"><span data-stu-id="2ca63-117">The return result is 12.</span></span>  
  
```  
SQRT(144)  
```  
  
 <span data-ttu-id="2ca63-118">この例では、式の平方根、つまり、 **Value1** 列の値から **Value2** 列の値を減算した結果の値の平方根が返されます。</span><span class="sxs-lookup"><span data-stu-id="2ca63-118">This example returns the square root of an expression, the result of subtracting values in the **Value1** and **Value2** columns.</span></span>  
  
```  
SQRT(Value1 - Value2)  
```  
  
 <span data-ttu-id="2ca63-119">この例では、SQUARE 関数を 2 つの変数に適用して、その合計の平方根を計算することにより、直角三角形の 3 番目の辺の長さが返されます。</span><span class="sxs-lookup"><span data-stu-id="2ca63-119">This example returns the length of the third side of a right triangle by applying the SQUARE function to two variables and then calculating the square root of their sum.</span></span> <span data-ttu-id="2ca63-120">**Side1** の値が 3、 **Side2** の値が 4 の場合、SQRT 関数は 5 を返します。</span><span class="sxs-lookup"><span data-stu-id="2ca63-120">If **Side1** contains 3 and **Side2** contains 4, the SQRT function returns 5.</span></span>  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  <span data-ttu-id="2ca63-121">式に含まれる変数名には、常にプレフィックス \@ を付けます。</span><span class="sxs-lookup"><span data-stu-id="2ca63-121">In expressions, variable names always include the \@ prefix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ca63-122">参照</span><span class="sxs-lookup"><span data-stu-id="2ca63-122">See Also</span></span>  
 [<span data-ttu-id="2ca63-123">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="2ca63-123">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
