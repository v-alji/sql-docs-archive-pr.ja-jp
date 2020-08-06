---
title: FLOOR (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- largest integer less than or equal to expression
- FLOOR function [SSIS]
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b638c9a7215d120c562e416cdecee463f031ad2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640166"
---
# <a name="floor-ssis-expression"></a><span data-ttu-id="f2677-102">FLOOR (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="f2677-102">FLOOR (SSIS Expression)</span></span>
  <span data-ttu-id="f2677-103">数値式以下で最大の整数を返します。</span><span class="sxs-lookup"><span data-stu-id="f2677-103">Returns the largest integer that is less than or equal to a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2677-104">構文</span><span class="sxs-lookup"><span data-stu-id="f2677-104">Syntax</span></span>  
  
```  
  
FLOOR(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="f2677-105">引数</span><span class="sxs-lookup"><span data-stu-id="f2677-105">Arguments</span></span>  
 <span data-ttu-id="f2677-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="f2677-106">*numeric_expression*</span></span>  
 <span data-ttu-id="f2677-107">有効な数値式です。</span><span class="sxs-lookup"><span data-stu-id="f2677-107">Is a valid numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f2677-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="f2677-108">Result Types</span></span>  
 <span data-ttu-id="f2677-109">引数の式の数値データ型です。</span><span class="sxs-lookup"><span data-stu-id="f2677-109">The numeric data type of the argument expression.</span></span> <span data-ttu-id="f2677-110">結果は、 *numeric_expression*と同じデータ型の、計算値の整数部分になります。</span><span class="sxs-lookup"><span data-stu-id="f2677-110">The result is the integer portion of the calculated value in the same data type as *numeric_expression.*</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2677-111">解説</span><span class="sxs-lookup"><span data-stu-id="f2677-111">Remarks</span></span>  
 <span data-ttu-id="f2677-112">引数が NULL の場合、FLOOR は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="f2677-112">FLOOR returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="f2677-113">式の例</span><span class="sxs-lookup"><span data-stu-id="f2677-113">Expression Examples</span></span>  
 <span data-ttu-id="f2677-114">次の例では、正の値、負の値、および 0 に FLOOR 関数を適用します。</span><span class="sxs-lookup"><span data-stu-id="f2677-114">These examples apply the FLOOR function to positive, negative, and zero values.</span></span>  
  
```  
FLOOR(123.45)  
```  
  
 <span data-ttu-id="f2677-115">123.00 を返します</span><span class="sxs-lookup"><span data-stu-id="f2677-115">Returns 123.00</span></span>  
  
```  
FLOOR(-123.45)  
```  
  
 <span data-ttu-id="f2677-116">-124.00 を返します</span><span class="sxs-lookup"><span data-stu-id="f2677-116">Returns -124.00</span></span>  
  
```  
FLOOR(0.00)  
```  
  
 <span data-ttu-id="f2677-117">0\.00 を返します。</span><span class="sxs-lookup"><span data-stu-id="f2677-117">Returns 0.00</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2677-118">参照</span><span class="sxs-lookup"><span data-stu-id="f2677-118">See Also</span></span>  
 <span data-ttu-id="f2677-119">[CEILING (SSIS 式)](ceiling-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="f2677-119">[CEILING &#40;SSIS Expression&#41;](ceiling-ssis-expression.md) </span></span>  
 [<span data-ttu-id="f2677-120">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="f2677-120">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
