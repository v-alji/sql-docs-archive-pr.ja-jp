---
title: LOG (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- base-10 logarithms
- LOG function
ms.assetid: f7fccace-c178-4e13-bde9-7dc4ef1d98fa
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0de84c1a92f94507bcc69c47cc4d9b6cda50a4f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642922"
---
# <a name="log-ssis-expression"></a><span data-ttu-id="ebf74-102">LOG (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="ebf74-102">LOG (SSIS Expression)</span></span>
  <span data-ttu-id="ebf74-103">数値式の常用対数を返します。</span><span class="sxs-lookup"><span data-stu-id="ebf74-103">Returns the base-10 logarithm of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebf74-104">構文</span><span class="sxs-lookup"><span data-stu-id="ebf74-104">Syntax</span></span>  
  
```  
  
LOG(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="ebf74-105">引数</span><span class="sxs-lookup"><span data-stu-id="ebf74-105">Arguments</span></span>  
 <span data-ttu-id="ebf74-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="ebf74-106">*numeric_expression*</span></span>  
 <span data-ttu-id="ebf74-107">0 以外で負ではない有効な数値式です。</span><span class="sxs-lookup"><span data-stu-id="ebf74-107">Is a valid nonzero or nonnegative numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="ebf74-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="ebf74-108">Result Types</span></span>  
 <span data-ttu-id="ebf74-109">DT_R8</span><span class="sxs-lookup"><span data-stu-id="ebf74-109">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebf74-110">解説</span><span class="sxs-lookup"><span data-stu-id="ebf74-110">Remarks</span></span>  
 <span data-ttu-id="ebf74-111">この *数値式* は、対数の計算前に DT_R8 データ型にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="ebf74-111">The *numeric expression* is cast to the DT_R8 data type before the logarithm is computed.</span></span> <span data-ttu-id="ebf74-112">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebf74-112">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="ebf74-113">*numeric_expression* が 0 または負の値に評価される場合、返される結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="ebf74-113">If *numeric_expression* evaluates to zero or a negative value, the return result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="ebf74-114">式の例</span><span class="sxs-lookup"><span data-stu-id="ebf74-114">Expression Examples</span></span>  
 <span data-ttu-id="ebf74-115">この例では、数値リテラルを使用しています。</span><span class="sxs-lookup"><span data-stu-id="ebf74-115">This example uses a numeric literal.</span></span> <span data-ttu-id="ebf74-116">この関数は、値 1.988291341907488 を返します。</span><span class="sxs-lookup"><span data-stu-id="ebf74-116">The function returns the value 1.988291341907488.</span></span>  
  
```  
LOG(97.34)  
```  
  
 <span data-ttu-id="ebf74-117">この例では、列 **Length**を使用しています。</span><span class="sxs-lookup"><span data-stu-id="ebf74-117">This example uses the column **Length**.</span></span> <span data-ttu-id="ebf74-118">列の値が 101.24 の場合、この関数は 2.005352136486217 を返します。</span><span class="sxs-lookup"><span data-stu-id="ebf74-118">If the column is 101.24, the function returns 2.005352136486217.</span></span>  
  
```  
LOG(Length)   
```  
  
 <span data-ttu-id="ebf74-119">この例では、変数 **Length**を使用しています。</span><span class="sxs-lookup"><span data-stu-id="ebf74-119">This example uses the variable **Length**.</span></span> <span data-ttu-id="ebf74-120">変数は数値データ型である必要があります。または式に、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 数値データ型への明示的なキャストが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebf74-120">The variable must have a numeric data type or the expression must include an explicit cast to a numeric [!INCLUDE[ssIS](../../includes/ssis-md.md)] data type.</span></span> <span data-ttu-id="ebf74-121">**Length** が 234.567 の場合、関数は 2.370266913465859 を返します。</span><span class="sxs-lookup"><span data-stu-id="ebf74-121">If **Length** is 234.567, the function returns 2.370266913465859.</span></span>  
  
```  
LOG(@Length)   
```  
  
## <a name="see-also"></a><span data-ttu-id="ebf74-122">参照</span><span class="sxs-lookup"><span data-stu-id="ebf74-122">See Also</span></span>  
 <span data-ttu-id="ebf74-123">[EXP &#40;SSIS 式&#41;](exp-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="ebf74-123">[EXP &#40;SSIS Expression&#41;](exp-ssis-expression.md) </span></span>  
 <span data-ttu-id="ebf74-124">[LN &#40;SSIS 式&#41;](ln-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="ebf74-124">[LN &#40;SSIS Expression&#41;](ln-ssis-expression.md) </span></span>  
 [<span data-ttu-id="ebf74-125">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="ebf74-125">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
