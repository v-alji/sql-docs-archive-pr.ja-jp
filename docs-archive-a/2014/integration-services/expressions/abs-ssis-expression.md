---
title: ABS (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- ABS function
- absolute positive value
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a2f429dda94282646ef769a1c393f9fa54b56e5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642941"
---
# <a name="abs-ssis-expression"></a><span data-ttu-id="670ea-102">ABS (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="670ea-102">ABS (SSIS Expression)</span></span>
  <span data-ttu-id="670ea-103">数値式の正の絶対値を返します。</span><span class="sxs-lookup"><span data-stu-id="670ea-103">Returns the absolute, positive value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="670ea-104">構文</span><span class="sxs-lookup"><span data-stu-id="670ea-104">Syntax</span></span>  
  
```  
  
ABS(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="670ea-105">引数</span><span class="sxs-lookup"><span data-stu-id="670ea-105">Arguments</span></span>  
 <span data-ttu-id="670ea-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="670ea-106">*numeric_expression*</span></span>  
 <span data-ttu-id="670ea-107">符号付きまたは符号なしの数値式です。</span><span class="sxs-lookup"><span data-stu-id="670ea-107">Is a signed or unsigned numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="670ea-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="670ea-108">Result Types</span></span>  
 <span data-ttu-id="670ea-109">関数に送信された数値式のデータ型です。</span><span class="sxs-lookup"><span data-stu-id="670ea-109">The data type of the numeric expression submitted to the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="670ea-110">解説</span><span class="sxs-lookup"><span data-stu-id="670ea-110">Remarks</span></span>  
 <span data-ttu-id="670ea-111">引数が NULL の場合、ABS は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="670ea-111">ABS returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="670ea-112">式の例</span><span class="sxs-lookup"><span data-stu-id="670ea-112">Expression Examples</span></span>  
 <span data-ttu-id="670ea-113">次の例では、正の数および負の数に ABS 関数を適用します。</span><span class="sxs-lookup"><span data-stu-id="670ea-113">These examples apply the ABS function to a positive and a negative number.</span></span> <span data-ttu-id="670ea-114">どちらも 1.23 を返します。</span><span class="sxs-lookup"><span data-stu-id="670ea-114">Both return 1.23.</span></span>  
  
```  
ABS(-1.23)  
ABS(1.23)  
```  
  
 <span data-ttu-id="670ea-115">この例では、変数 **HighTemperature** および **LowTempature**の値を減算する式に対して ABS 関数を適用します。</span><span class="sxs-lookup"><span data-stu-id="670ea-115">This example applies the ABS function to an expression that subtracts values in the variables **HighTemperature** and **LowTempature**.</span></span>  
  
```  
ABS(@HighTemperature - @LowTemperature)  
```  
  
## <a name="see-also"></a><span data-ttu-id="670ea-116">参照</span><span class="sxs-lookup"><span data-stu-id="670ea-116">See Also</span></span>  
 [<span data-ttu-id="670ea-117">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="670ea-117">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
