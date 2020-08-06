---
title: ROUND (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- rounding expressions
- ROUND function [SSIS]
ms.assetid: 376f1947-4fc5-4611-ad86-823e4db1b468
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9d77045787eafbc3dd402db9982d8d7a98190bc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716486"
---
# <a name="round-ssis-expression"></a><span data-ttu-id="a3ac4-102">ROUND (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="a3ac4-102">ROUND (SSIS Expression)</span></span>
  <span data-ttu-id="a3ac4-103">指定された長さまたは有効桁数に丸めた数値式を返します。</span><span class="sxs-lookup"><span data-stu-id="a3ac4-103">Returns a numeric expression that is rounded to the specified length or precision.</span></span> <span data-ttu-id="a3ac4-104">length パラメーターは整数に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3ac4-104">The length parameter must evaluate to an integer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3ac4-105">構文</span><span class="sxs-lookup"><span data-stu-id="a3ac4-105">Syntax</span></span>  
  
```  
  
ROUND(numeric_expression,length)  
```  
  
## <a name="arguments"></a><span data-ttu-id="a3ac4-106">引数</span><span class="sxs-lookup"><span data-stu-id="a3ac4-106">Arguments</span></span>  
 <span data-ttu-id="a3ac4-107">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="a3ac4-107">*numeric_expression*</span></span>  
 <span data-ttu-id="a3ac4-108">有効な数値型の式です。</span><span class="sxs-lookup"><span data-stu-id="a3ac4-108">Is an expression of a valid numeric type.</span></span> <span data-ttu-id="a3ac4-109">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3ac4-109">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="a3ac4-110">*length*</span><span class="sxs-lookup"><span data-stu-id="a3ac4-110">*length*</span></span>  
 <span data-ttu-id="a3ac4-111">整数式です。</span><span class="sxs-lookup"><span data-stu-id="a3ac4-111">Is an integer expression.</span></span> <span data-ttu-id="a3ac4-112">*numeric_expression* の丸め結果とする有効桁数です。</span><span class="sxs-lookup"><span data-stu-id="a3ac4-112">It is the precision to which *numeric_expression* is rounded.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a3ac4-113">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="a3ac4-113">Result Types</span></span>  
 <span data-ttu-id="a3ac4-114">*numeric*_*expression.* と同じ型。</span><span class="sxs-lookup"><span data-stu-id="a3ac4-114">The same type as *numeric*_*expression.*</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3ac4-115">解説</span><span class="sxs-lookup"><span data-stu-id="a3ac4-115">Remarks</span></span>  
 <span data-ttu-id="a3ac4-116">*length* 引数は正の整数または 0 に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3ac4-116">The *length* argument must evaluate to a positive integer or zero.</span></span>  
  
 <span data-ttu-id="a3ac4-117">引数が NULL の場合、ROUND は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="a3ac4-117">ROUND returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="a3ac4-118">式の例</span><span class="sxs-lookup"><span data-stu-id="a3ac4-118">Expression Examples</span></span>  
 <span data-ttu-id="a3ac4-119">この例では、数値リテラルを 3 桁に丸めます。</span><span class="sxs-lookup"><span data-stu-id="a3ac4-119">These examples round numeric literals to a length of three.</span></span> <span data-ttu-id="a3ac4-120">最初の結果は 137.1570 を返し、次の結果は 137.1580 を返します。</span><span class="sxs-lookup"><span data-stu-id="a3ac4-120">The first return result is 137.1570, the second 137.1580.</span></span>  
  
```  
ROUND(137.1574,3)  
ROUND(137.1575,3)  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3ac4-121">参照</span><span class="sxs-lookup"><span data-stu-id="a3ac4-121">See Also</span></span>  
 [<span data-ttu-id="a3ac4-122">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="a3ac4-122">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
