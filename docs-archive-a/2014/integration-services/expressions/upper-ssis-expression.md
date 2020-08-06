---
title: UPPER (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- UPPER function
- converting lowercase to uppercase
- uppercase characters [Integration Services]
- lowercase characters
ms.assetid: d33985f7-1048-4023-83e4-274090acda78
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 181e231d735a8e98cd2bce10c692e35668a686f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716433"
---
# <a name="upper-ssis-expression"></a><span data-ttu-id="2f58e-102">UPPER (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="2f58e-102">UPPER (SSIS Expression)</span></span>
  <span data-ttu-id="2f58e-103">小文字が大文字に変換された状態の文字式を返します。</span><span class="sxs-lookup"><span data-stu-id="2f58e-103">Returns a character expression after converting lowercase characters to uppercase characters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f58e-104">構文</span><span class="sxs-lookup"><span data-stu-id="2f58e-104">Syntax</span></span>  
  
```  
  
UPPER(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="2f58e-105">引数</span><span class="sxs-lookup"><span data-stu-id="2f58e-105">Arguments</span></span>  
 <span data-ttu-id="2f58e-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="2f58e-106">*character_expression*</span></span>  
 <span data-ttu-id="2f58e-107">大文字に変換する対象となる文字式です。</span><span class="sxs-lookup"><span data-stu-id="2f58e-107">Is a character expression to convert to uppercase characters.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="2f58e-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="2f58e-108">Result Types</span></span>  
 <span data-ttu-id="2f58e-109">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="2f58e-109">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f58e-110">解説</span><span class="sxs-lookup"><span data-stu-id="2f58e-110">Remarks</span></span>  
 <span data-ttu-id="2f58e-111">UPPER は、DT_WSTR データ型でのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="2f58e-111">UPPER works only with the DT_WSTR data type.</span></span> <span data-ttu-id="2f58e-112">*character_expression* 引数が DT_STR データ型の文字列リテラルまたはデータ列である場合は、UPPER による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="2f58e-112">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before UPPER performs its operation.</span></span> <span data-ttu-id="2f58e-113">その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f58e-113">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="2f58e-114">詳しくは、「[Integration Services のデータ型](../data-flow/integration-services-data-types.md)」および「[Cast &#40;SSIS 式&#41;](cast-ssis-expression.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2f58e-114">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="2f58e-115">引数が NULL の場合、UPPER は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="2f58e-115">UPPER returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="2f58e-116">式の例</span><span class="sxs-lookup"><span data-stu-id="2f58e-116">Expression Examples</span></span>  
 <span data-ttu-id="2f58e-117">この例では、文字列リテラルを大文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="2f58e-117">This example converts a string literal to uppercase characters.</span></span> <span data-ttu-id="2f58e-118">返される結果は "HELLO" です。</span><span class="sxs-lookup"><span data-stu-id="2f58e-118">The return result is "HELLO".</span></span>  
  
```  
UPPER("hello")  
```  
  
 <span data-ttu-id="2f58e-119">この例では、 **FirstName** 列の最初の文字を大文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="2f58e-119">This example converts the first character in the **FirstName** column to an uppercase character.</span></span> <span data-ttu-id="2f58e-120">**FirstName** が anna の場合、返される結果は "A" です。</span><span class="sxs-lookup"><span data-stu-id="2f58e-120">If **FirstName** is anna, the return result is "A".</span></span> <span data-ttu-id="2f58e-121">詳細については、「[SUBSTRING &#40;SSIS 式&#41;](substring-ssis-expression.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f58e-121">For more information, see [SUBSTRING &#40;SSIS Expression&#41;](substring-ssis-expression.md).</span></span>  
  
```  
UPPER(SUBSTRING(FirstName, 1, 1))  
```  
  
 <span data-ttu-id="2f58e-122">この例では、 **PostalCode** 変数の値を大文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="2f58e-122">This example converts the value in the **PostalCode** variable to uppercase characters.</span></span> <span data-ttu-id="2f58e-123">**PostalCode** が k4b1s2 の場合、返される結果は "K4B1S2" です。</span><span class="sxs-lookup"><span data-stu-id="2f58e-123">If **PostalCode** is k4b1s2, the return result is "K4B1S2".</span></span>  
  
```  
UPPER(@PostalCode)  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f58e-124">参照</span><span class="sxs-lookup"><span data-stu-id="2f58e-124">See Also</span></span>  
 <span data-ttu-id="2f58e-125">[LOWER &#40;SSIS 式&#41;](lower-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="2f58e-125">[LOWER &#40;SSIS Expression&#41;](lower-ssis-expression.md) </span></span>  
 [<span data-ttu-id="2f58e-126">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="2f58e-126">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
