---
title: SIGN (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- positive values [Integration Services]
- SIGN function
- negative values
ms.assetid: 1547db08-4329-4781-91c2-36898ed71b15
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a34992b0029cd378274e38ce4e37fcd313d2b788
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716481"
---
# <a name="sign-ssis-expression"></a><span data-ttu-id="dc5dc-102">SIGN (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="dc5dc-102">SIGN (SSIS Expression)</span></span>
  <span data-ttu-id="dc5dc-103">数値式の符号として正 (+1)、負 (-1)、0 のいずれかを返します。</span><span class="sxs-lookup"><span data-stu-id="dc5dc-103">Returns the positive (+1), negative (-1), or zero (0) sign of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc5dc-104">構文</span><span class="sxs-lookup"><span data-stu-id="dc5dc-104">Syntax</span></span>  
  
```  
  
SIGN(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="dc5dc-105">引数</span><span class="sxs-lookup"><span data-stu-id="dc5dc-105">Arguments</span></span>  
 <span data-ttu-id="dc5dc-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="dc5dc-106">*numeric_expression*</span></span>  
 <span data-ttu-id="dc5dc-107">有効な符号付き数値式です。</span><span class="sxs-lookup"><span data-stu-id="dc5dc-107">Is a valid signed numeric expression.</span></span> <span data-ttu-id="dc5dc-108">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc5dc-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="dc5dc-109">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="dc5dc-109">Result Types</span></span>  
 <span data-ttu-id="dc5dc-110">DT_I4</span><span class="sxs-lookup"><span data-stu-id="dc5dc-110">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc5dc-111">解説</span><span class="sxs-lookup"><span data-stu-id="dc5dc-111">Remarks</span></span>  
 <span data-ttu-id="dc5dc-112">引数が NULL の場合、SIGN は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="dc5dc-112">SIGN returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="dc5dc-113">式の例</span><span class="sxs-lookup"><span data-stu-id="dc5dc-113">Expression Examples</span></span>  
 <span data-ttu-id="dc5dc-114">この例では、数値リテラルの符号を返します。</span><span class="sxs-lookup"><span data-stu-id="dc5dc-114">This example returns the sign of a numeric literal.</span></span> <span data-ttu-id="dc5dc-115">返される結果は -1 です。</span><span class="sxs-lookup"><span data-stu-id="dc5dc-115">The return result is -1.</span></span>  
  
```  
SIGN(-123.45)  
```  
  
 <span data-ttu-id="dc5dc-116">この例では、 **StandardCost** 列を **DealerPrice** 列から減算した結果の符号を返します。</span><span class="sxs-lookup"><span data-stu-id="dc5dc-116">This example returns the sign of the result of subtracting the **StandardCost** column from the **DealerPrice** column.</span></span>  
  
```  
SIGN(DealerPrice - StandardCost)  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc5dc-117">参照</span><span class="sxs-lookup"><span data-stu-id="dc5dc-117">See Also</span></span>  
 [<span data-ttu-id="dc5dc-118">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="dc5dc-118">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
