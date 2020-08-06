---
title: EXP (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- exponential functions
- EXP function
ms.assetid: 4cd96d3c-58c9-4a67-a6f6-b72758232912
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 150c92355ab3e0d3a028c98defe2e2fa9a1bf8ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641746"
---
# <a name="exp-ssis-expression"></a><span data-ttu-id="19e8f-102">EXP (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="19e8f-102">EXP (SSIS Expression)</span></span>
  <span data-ttu-id="19e8f-103">数値式の e を基数とする指数を返します。</span><span class="sxs-lookup"><span data-stu-id="19e8f-103">Returns the exponent to base e of a numeric expression.</span></span> <span data-ttu-id="19e8f-104">EXP 関数は LN 関数の逆関数であり、真数と呼ばれる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="19e8f-104">The EXP function complements the action of the LN function and is sometimes referred to as the antilogarithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19e8f-105">構文</span><span class="sxs-lookup"><span data-stu-id="19e8f-105">Syntax</span></span>  
  
```  
  
EXP(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="19e8f-106">引数</span><span class="sxs-lookup"><span data-stu-id="19e8f-106">Arguments</span></span>  
 <span data-ttu-id="19e8f-107">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="19e8f-107">*numeric_expression*</span></span>  
 <span data-ttu-id="19e8f-108">有効な数値式です。</span><span class="sxs-lookup"><span data-stu-id="19e8f-108">Is a valid numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="19e8f-109">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="19e8f-109">Result Types</span></span>  
 <span data-ttu-id="19e8f-110">DT_R8</span><span class="sxs-lookup"><span data-stu-id="19e8f-110">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19e8f-111">解説</span><span class="sxs-lookup"><span data-stu-id="19e8f-111">Remarks</span></span>  
 <span data-ttu-id="19e8f-112">数値式は、指数の計算前に DT_R8 データ型にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="19e8f-112">The numeric expression is cast to the DT_R8 data type before the exponent is computed.</span></span> <span data-ttu-id="19e8f-113">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19e8f-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="19e8f-114">返される結果は、常に正の数値です。</span><span class="sxs-lookup"><span data-stu-id="19e8f-114">The return result is always a positive number.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="19e8f-115">式の例</span><span class="sxs-lookup"><span data-stu-id="19e8f-115">Expression Examples</span></span>  
 <span data-ttu-id="19e8f-116">この例では、正の値、負の値、および 0 に、EXP 関数を適用します。</span><span class="sxs-lookup"><span data-stu-id="19e8f-116">These examples apply the EXP function to positive and negative values and to zero.</span></span>  
  
```  
EXP(74)  
```  
  
 <span data-ttu-id="19e8f-117">1\.373382979540176E+32 が返されます。</span><span class="sxs-lookup"><span data-stu-id="19e8f-117">Returns 1.373382979540176E+32.</span></span>  
  
```  
EXP(-27)  
```  
  
 <span data-ttu-id="19e8f-118">1\.879528816539083E-12 が返されます。</span><span class="sxs-lookup"><span data-stu-id="19e8f-118">Returns 1.879528816539083E-12.</span></span>  
  
```  
EXP(0)  
```  
  
 <span data-ttu-id="19e8f-119">1 が返されます。</span><span class="sxs-lookup"><span data-stu-id="19e8f-119">Returns 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19e8f-120">参照</span><span class="sxs-lookup"><span data-stu-id="19e8f-120">See Also</span></span>  
 <span data-ttu-id="19e8f-121">[LOG (SSIS 式)](log-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="19e8f-121">[LOG &#40;SSIS Expression&#41;](log-ssis-expression.md) </span></span>  
 [<span data-ttu-id="19e8f-122">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="19e8f-122">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
