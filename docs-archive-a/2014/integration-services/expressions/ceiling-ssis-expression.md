---
title: CEILING (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- smallest integer great than or equal to expression
- CEILING function [SSIS]
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cd2f9f455226925d6bf00842e80a8713e6c72771
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645751"
---
# <a name="ceiling-ssis-expression"></a><span data-ttu-id="f8306-102">CEILING (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="f8306-102">CEILING (SSIS Expression)</span></span>
  <span data-ttu-id="f8306-103">数値式以上で最小の整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="f8306-103">Returns the smallest integer that is greater than or equal to a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8306-104">構文</span><span class="sxs-lookup"><span data-stu-id="f8306-104">Syntax</span></span>  
  
```  
  
CEILING(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="f8306-105">引数</span><span class="sxs-lookup"><span data-stu-id="f8306-105">Arguments</span></span>  
 <span data-ttu-id="f8306-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="f8306-106">*numeric_expression*</span></span>  
 <span data-ttu-id="f8306-107">有効な数値式です。</span><span class="sxs-lookup"><span data-stu-id="f8306-107">Is a valid numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f8306-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="f8306-108">Result Types</span></span>  
 <span data-ttu-id="f8306-109">関数に送信された数値式のデータ型です。</span><span class="sxs-lookup"><span data-stu-id="f8306-109">The data type of the numeric expression submitted to the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8306-110">解説</span><span class="sxs-lookup"><span data-stu-id="f8306-110">Remarks</span></span>  
 <span data-ttu-id="f8306-111">引数が NULL の場合、CEILING は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="f8306-111">CEILING returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="f8306-112">式の例</span><span class="sxs-lookup"><span data-stu-id="f8306-112">Expression Examples</span></span>  
 <span data-ttu-id="f8306-113">この例では、正の値、負の値、および 0 に CEILING 関数を適用します。</span><span class="sxs-lookup"><span data-stu-id="f8306-113">These examples apply the CEILING function to positive, negative, and zero values.</span></span>  
  
```  
CEILING(123.74)  
```  
  
 <span data-ttu-id="f8306-114">124.00 を返します。</span><span class="sxs-lookup"><span data-stu-id="f8306-114">Returns 124.00</span></span>  
  
```  
CEILING(-124.27)  
```  
  
 <span data-ttu-id="f8306-115">-124.00 を返します</span><span class="sxs-lookup"><span data-stu-id="f8306-115">Returns -124.00</span></span>  
  
```  
CEILING(0.00)  
```  
  
 <span data-ttu-id="f8306-116">0\.00 を返します。</span><span class="sxs-lookup"><span data-stu-id="f8306-116">Returns 0.00</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8306-117">参照</span><span class="sxs-lookup"><span data-stu-id="f8306-117">See Also</span></span>  
 <span data-ttu-id="f8306-118">[FLOOR &#40;SSIS 式&#41;](floor-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="f8306-118">[FLOOR &#40;SSIS Expression&#41;](floor-ssis-expression.md) </span></span>  
 [<span data-ttu-id="f8306-119">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="f8306-119">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
