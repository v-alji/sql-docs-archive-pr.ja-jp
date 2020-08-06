---
title: LOWER (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting uppercase to lowercase
- LOWER function
- uppercase characters [Integration Services]
- lowercase characters
ms.assetid: 109328e1-5604-40ff-895e-f2e7c13fff41
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 180be8f3cfb5a15eb0fcd6ddd3d63b09fe874af5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640163"
---
# <a name="lower-ssis-expression"></a><span data-ttu-id="70a4f-102">LOWER (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="70a4f-102">LOWER (SSIS Expression)</span></span>
  <span data-ttu-id="70a4f-103">大文字が小文字に変換された状態の文字式を返します。</span><span class="sxs-lookup"><span data-stu-id="70a4f-103">Returns a character expression after converting uppercase characters to lowercase characters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70a4f-104">構文</span><span class="sxs-lookup"><span data-stu-id="70a4f-104">Syntax</span></span>  
  
```  
  
LOWER(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="70a4f-105">引数</span><span class="sxs-lookup"><span data-stu-id="70a4f-105">Arguments</span></span>  
 <span data-ttu-id="70a4f-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="70a4f-106">*character_expression*</span></span>  
 <span data-ttu-id="70a4f-107">小文字に変換する文字式です。</span><span class="sxs-lookup"><span data-stu-id="70a4f-107">Is a character expression to convert to lowercase characters.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="70a4f-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="70a4f-108">Result Types</span></span>  
 <span data-ttu-id="70a4f-109">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="70a4f-109">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70a4f-110">解説</span><span class="sxs-lookup"><span data-stu-id="70a4f-110">Remarks</span></span>  
 <span data-ttu-id="70a4f-111">LOWER は DT_WSTR データ型でのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="70a4f-111">LOWER works only with the DT_WSTR data type.</span></span> <span data-ttu-id="70a4f-112">*character_expression* 引数が DT_STR データ型の文字列リテラルまたはデータ列である場合は、LOWER による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="70a4f-112">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before LOWER performs its operation.</span></span> <span data-ttu-id="70a4f-113">その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="70a4f-113">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="70a4f-114">詳しくは、「[Integration Services のデータ型](../data-flow/integration-services-data-types.md)」および「[Cast &#40;SSIS 式&#41;](cast-ssis-expression.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="70a4f-114">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="70a4f-115">引数が NULL の場合、LOWER は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="70a4f-115">LOWER returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="70a4f-116">式の例</span><span class="sxs-lookup"><span data-stu-id="70a4f-116">Expression Examples</span></span>  
 <span data-ttu-id="70a4f-117">この例では、文字列リテラルを小文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="70a4f-117">This example converts a string literal to lowercase characters.</span></span> <span data-ttu-id="70a4f-118">返される結果は "new york" です。</span><span class="sxs-lookup"><span data-stu-id="70a4f-118">The return result is "new york".</span></span>  
  
```  
LOWER("New York")  
```  
  
 <span data-ttu-id="70a4f-119">この例では、 **Color** 入力列の最初の文字を除くすべての文字を小文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="70a4f-119">This example converts all characters from the **Color** input column, except the first character, to lowercase characters.</span></span> <span data-ttu-id="70a4f-120">Color が YELLOW の場合、返される結果は "Yellow" です。</span><span class="sxs-lookup"><span data-stu-id="70a4f-120">If Color is YELLOW, the return result is "Yellow".</span></span> <span data-ttu-id="70a4f-121">詳細については、「[SUBSTRING &#40;SSIS 式&#41;](substring-ssis-expression.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70a4f-121">For more information, see [SUBSTRING &#40;SSIS Expression&#41;](substring-ssis-expression.md).</span></span>  
  
```  
LOWER(SUBSTRING(Color, 2, 15))  
```  
  
 <span data-ttu-id="70a4f-122">この例では、 **CityName** 変数の値を小文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="70a4f-122">This example converts the value in the **CityName** variable to lowercase characters.</span></span>  
  
```  
LOWER(@CityName)  
```  
  
## <a name="see-also"></a><span data-ttu-id="70a4f-123">参照</span><span class="sxs-lookup"><span data-stu-id="70a4f-123">See Also</span></span>  
 <span data-ttu-id="70a4f-124">[UPPER (SSIS 式)](upper-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="70a4f-124">[UPPER &#40;SSIS Expression&#41;](upper-ssis-expression.md) </span></span>  
 [<span data-ttu-id="70a4f-125">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="70a4f-125">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
