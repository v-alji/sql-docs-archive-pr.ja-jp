---
title: HEX (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- hexadecimal data
- HEX function
ms.assetid: f5d471ee-aeef-421c-b6e1-55b9676c3842
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 640ae38ec5d2cd5ffb448e9aebde5ba5ceba2684
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736631"
---
# <a name="hex-ssis-expression"></a><span data-ttu-id="66d6a-102">HEX (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="66d6a-102">HEX (SSIS Expression)</span></span>
  <span data-ttu-id="66d6a-103">整数の 16 進値を表す文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="66d6a-103">Returns a string representing the hexadecimal value of an integer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66d6a-104">構文</span><span class="sxs-lookup"><span data-stu-id="66d6a-104">Syntax</span></span>  
  
```  
  
HEX(integer_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="66d6a-105">引数</span><span class="sxs-lookup"><span data-stu-id="66d6a-105">Arguments</span></span>  
 <span data-ttu-id="66d6a-106">*integer_expression*</span><span class="sxs-lookup"><span data-stu-id="66d6a-106">*integer_expression*</span></span>  
 <span data-ttu-id="66d6a-107">符号付き整数または符号なし整数です。</span><span class="sxs-lookup"><span data-stu-id="66d6a-107">Is a signed or unsigned integer.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="66d6a-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="66d6a-108">Result Types</span></span>  
 <span data-ttu-id="66d6a-109">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="66d6a-109">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66d6a-110">解説</span><span class="sxs-lookup"><span data-stu-id="66d6a-110">Remarks</span></span>  
 <span data-ttu-id="66d6a-111">*integer_expression* が null の場合、HEX は null を返します。</span><span class="sxs-lookup"><span data-stu-id="66d6a-111">HEX returns null if *integer_expression* is null.</span></span>  
  
 <span data-ttu-id="66d6a-112">*integer_expression* 引数は整数に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="66d6a-112">The *integer_expression* argument must evaluate to an integer.</span></span> <span data-ttu-id="66d6a-113">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66d6a-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="66d6a-114">返される結果には、0x プレフィックスなどの修飾子は含まれません。</span><span class="sxs-lookup"><span data-stu-id="66d6a-114">The return result does not include qualifiers such as the 0x prefix.</span></span> <span data-ttu-id="66d6a-115">プレフィックスを含めるには、+ (連結) 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="66d6a-115">To include a prefix, use the + (Concatenate) operator.</span></span> <span data-ttu-id="66d6a-116">詳細については、「[+ &#40;連結&#41; &#40;SSIS 式&#41;](concatenate-ssis-expression.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66d6a-116">For more information, see [+ &#40;Concatenate&#41; &#40;SSIS Expression&#41;](concatenate-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="66d6a-117">HEX 表記法で使用される A から F の文字は、大文字で表示されます。</span><span class="sxs-lookup"><span data-stu-id="66d6a-117">The letters A - F, used in HEX notations, appear as uppercase characters.</span></span>  
  
 <span data-ttu-id="66d6a-118">整数データ型の結果の文字列の長さは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="66d6a-118">The length of the resulting string for integer data types is as follows:</span></span>  
  
-   <span data-ttu-id="66d6a-119">DT_I1 および DT_UI1 データ型は、最大長 2 の文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="66d6a-119">DT_I1 and DT_UI1 return a string with a maximum length of 2.</span></span>  
  
-   <span data-ttu-id="66d6a-120">DT_I2 および DT_UI2 データ型は、最大長 4 の文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="66d6a-120">DT_I2 and DT_UI2 return a string with a maximum length of 4.</span></span>  
  
-   <span data-ttu-id="66d6a-121">DT_I4 および DT_UI4 データ型は、最大長 8 の文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="66d6a-121">DT_I4 and DT_UI4 return a string with a maximum length of 8.</span></span>  
  
-   <span data-ttu-id="66d6a-122">DT_I8 および DT_UI8 データ型は、最大長 16 の文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="66d6a-122">DT_I8 and DT_UI8 return a string with a maximum length of 16.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="66d6a-123">式の例</span><span class="sxs-lookup"><span data-stu-id="66d6a-123">Expression Examples</span></span>  
 <span data-ttu-id="66d6a-124">この例では、数値リテラルを使用しています。</span><span class="sxs-lookup"><span data-stu-id="66d6a-124">This example uses a numeric literal.</span></span> <span data-ttu-id="66d6a-125">この関数は、値 190 を返します。</span><span class="sxs-lookup"><span data-stu-id="66d6a-125">The function returns the value 190.</span></span>  
  
```  
HEX(400)   
```  
  
 <span data-ttu-id="66d6a-126">この例では、 **ReorderPoint** 列を使用します。</span><span class="sxs-lookup"><span data-stu-id="66d6a-126">This example uses the **ReorderPoint** column.</span></span> <span data-ttu-id="66d6a-127">列のデータ型は `smallint` です。</span><span class="sxs-lookup"><span data-stu-id="66d6a-127">The column data type is `smallint`.</span></span> <span data-ttu-id="66d6a-128">**ReorderPoint** が 750 の場合、関数は 2EE を返します。</span><span class="sxs-lookup"><span data-stu-id="66d6a-128">If **ReorderPoint** is 750, the function returns 2EE.</span></span>  
  
```  
HEX(ReorderPoint)   
```  
  
 <span data-ttu-id="66d6a-129">この例では、システム変数 **LocaleID**を使用しています。</span><span class="sxs-lookup"><span data-stu-id="66d6a-129">This example uses **LocaleID**, a system variable.</span></span> <span data-ttu-id="66d6a-130">**LocaleID** が 1033 の場合、関数は 409 を返します。</span><span class="sxs-lookup"><span data-stu-id="66d6a-130">If **LocaleID** is 1033, the function returns 409.</span></span>  
  
```  
HEX(@LocaleID)  
```  
  
## <a name="see-also"></a><span data-ttu-id="66d6a-131">参照</span><span class="sxs-lookup"><span data-stu-id="66d6a-131">See Also</span></span>  
 [<span data-ttu-id="66d6a-132">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="66d6a-132">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
