---
title: SQUARE (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQUARE
- square values
ms.assetid: cecf1bb2-3d55-40a6-9688-ed67bcc150b4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 09955e708aae707a88aa7821d2a72651a3a44d59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716469"
---
# <a name="square-ssis-expression"></a><span data-ttu-id="e5b5e-102">SQUARE (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="e5b5e-102">SQUARE (SSIS Expression)</span></span>
  <span data-ttu-id="e5b5e-103">数値式の 2 乗値を返します。</span><span class="sxs-lookup"><span data-stu-id="e5b5e-103">Returns the square of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5b5e-104">構文</span><span class="sxs-lookup"><span data-stu-id="e5b5e-104">Syntax</span></span>  
  
```  
  
SQUARE(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="e5b5e-105">引数</span><span class="sxs-lookup"><span data-stu-id="e5b5e-105">Arguments</span></span>  
 <span data-ttu-id="e5b5e-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="e5b5e-106">*numeric_expression*</span></span>  
 <span data-ttu-id="e5b5e-107">任意の数値データ型の数値式です。</span><span class="sxs-lookup"><span data-stu-id="e5b5e-107">Is a numeric expression of any numeric data type.</span></span> <span data-ttu-id="e5b5e-108">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5b5e-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e5b5e-109">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="e5b5e-109">Result Types</span></span>  
 <span data-ttu-id="e5b5e-110">DT_R8</span><span class="sxs-lookup"><span data-stu-id="e5b5e-110">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5b5e-111">解説</span><span class="sxs-lookup"><span data-stu-id="e5b5e-111">Remarks</span></span>  
 <span data-ttu-id="e5b5e-112">引数が NULL の場合、SQUARE は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="e5b5e-112">SQUARE returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="e5b5e-113">2 乗演算の前に、引数は DT_R8 データ型にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="e5b5e-113">The argument is cast to the DT_R8 data type before the square operation.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="e5b5e-114">式の例</span><span class="sxs-lookup"><span data-stu-id="e5b5e-114">Expression Examples</span></span>  
 <span data-ttu-id="e5b5e-115">この例では、12 の 2 乗が返されます。</span><span class="sxs-lookup"><span data-stu-id="e5b5e-115">This example returns the square of 12.</span></span> <span data-ttu-id="e5b5e-116">返される結果は 144 です。</span><span class="sxs-lookup"><span data-stu-id="e5b5e-116">The return result is 144.</span></span>  
  
```  
SQUARE(12)  
```  
  
 <span data-ttu-id="e5b5e-117">この例では、2 つの列の値を減算した結果の 2 乗が返されます。</span><span class="sxs-lookup"><span data-stu-id="e5b5e-117">This example returns the square of the result of subtracting values in two columns.</span></span> <span data-ttu-id="e5b5e-118">**Value1** が 12 で **Value2** が 4 の場合、SQUARE 関数は 64 を返します。</span><span class="sxs-lookup"><span data-stu-id="e5b5e-118">If **Value1** contains 12 and **Value2** contains 4, the SQUARE function returns 64.</span></span>  
  
```  
SQUARE(Value1 - Value2)  
```  
  
 <span data-ttu-id="e5b5e-119">この例では、SQUARE 関数を 2 つの変数に適用して、その合計の平方根を計算することにより、直角三角形の 3 番目の辺の長さが返されます。</span><span class="sxs-lookup"><span data-stu-id="e5b5e-119">This example returns the length of the third side of a right angle triangle by applying the SQUARE function to two variables and then calculating the square root of their sum.</span></span> <span data-ttu-id="e5b5e-120">**Side1** の値が 3、 **Side2** の値が 4 の場合、SQRT 関数は 5 を返します。</span><span class="sxs-lookup"><span data-stu-id="e5b5e-120">If **Side1** contains 3 and **Side2** contains 4, the SQRT function returns 5.</span></span>  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  <span data-ttu-id="e5b5e-121">式に含まれる変数名には、常にプレフィックス \@ を付けます。</span><span class="sxs-lookup"><span data-stu-id="e5b5e-121">In expressions, variable names always include the \@ prefix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5b5e-122">参照</span><span class="sxs-lookup"><span data-stu-id="e5b5e-122">See Also</span></span>  
 [<span data-ttu-id="e5b5e-123">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="e5b5e-123">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
