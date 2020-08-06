---
title: LEN (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- LEN function
- number of characters
ms.assetid: d961398b-e4d0-4936-be17-8f4c5882a640
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8863864168295a3a9a924df588312ee65b6f7fa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639560"
---
# <a name="len-ssis-expression"></a><span data-ttu-id="6acff-102">LEN (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="6acff-102">LEN (SSIS Expression)</span></span>
  <span data-ttu-id="6acff-103">文字式の文字数を返します。</span><span class="sxs-lookup"><span data-stu-id="6acff-103">Returns the number of characters in a character expression.</span></span> <span data-ttu-id="6acff-104">文字列の先頭および末尾に空白が含まれる場合、この関数は、それらの空白をカウントに含めます。</span><span class="sxs-lookup"><span data-stu-id="6acff-104">If the string includes leading and trailing blanks, the function includes them in the count.</span></span> <span data-ttu-id="6acff-105">1 バイト文字の文字列と 2 バイト文字の文字列が同一の場合、LEN 関数は同一の値を返します。</span><span class="sxs-lookup"><span data-stu-id="6acff-105">LEN returns identical values for the same string of single and double byte characters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6acff-106">構文</span><span class="sxs-lookup"><span data-stu-id="6acff-106">Syntax</span></span>  
  
```  
  
LEN(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="6acff-107">引数</span><span class="sxs-lookup"><span data-stu-id="6acff-107">Arguments</span></span>  
 <span data-ttu-id="6acff-108">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="6acff-108">*character_expression*</span></span>  
 <span data-ttu-id="6acff-109">評価の対象となる式です。</span><span class="sxs-lookup"><span data-stu-id="6acff-109">Is the expression to evaluate.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="6acff-110">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="6acff-110">Result Types</span></span>  
 <span data-ttu-id="6acff-111">DT_I4</span><span class="sxs-lookup"><span data-stu-id="6acff-111">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6acff-112">解説</span><span class="sxs-lookup"><span data-stu-id="6acff-112">Remarks</span></span>  
 <span data-ttu-id="6acff-113">*character_expression* 引数には、DT_WSTR、DT_TEXT、DT_NTEXT、または DT_IMAGE データ型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6acff-113">The *character_expression* argument can be a DT_WSTR, DT_TEXT, DT_NTEXT, or DT_IMAGE data type.</span></span> <span data-ttu-id="6acff-114">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6acff-114">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="6acff-115">*character_expression* が DT_STR データ型の文字列リテラルまたはデータ列である場合は、LEN による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="6acff-115">If *character_expression* is a string literal or a data column with the DT_STR data type, it is implicitly cast to the DT_WSTR data type before LEN performs its operation.</span></span> <span data-ttu-id="6acff-116">その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="6acff-116">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="6acff-117">詳細については、「[Cast &#40;SSIS 式&#41;](cast-ssis-expression.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6acff-117">For more information, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="6acff-118">DT_TEXT、DT_NTEXT、DT_IMAGE などのバイナリ ラージ オブジェクト (BLOB) データ型に引数が渡された場合、LEN 関数はバイト カウントを返します。</span><span class="sxs-lookup"><span data-stu-id="6acff-118">If the argument passed to the LEN function has a Binary Large Object Block (BLOB) data type, such as DT_TEXT, DT_NTEXT, or DT_IMAGE, the function returns a byte count.</span></span>  
  
 <span data-ttu-id="6acff-119">引数が NULL の場合、LEN は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="6acff-119">LEN returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="6acff-120">式の例</span><span class="sxs-lookup"><span data-stu-id="6acff-120">Expression Examples</span></span>  
 <span data-ttu-id="6acff-121">この例は、文字列リテラルの長さを返します。</span><span class="sxs-lookup"><span data-stu-id="6acff-121">This example returns the length of a string literal.</span></span> <span data-ttu-id="6acff-122">返される結果は 12 です。</span><span class="sxs-lookup"><span data-stu-id="6acff-122">The return result is 12.</span></span>  
  
```  
LEN("Ball Bearing")  
```  
  
 <span data-ttu-id="6acff-123">この例は、 **FirstName** と **LastName** 列の値の長さの差を返します。</span><span class="sxs-lookup"><span data-stu-id="6acff-123">This example returns the difference between the length of values in the **FirstName** and **LastName** columns.</span></span>  
  
```  
LEN(FirstName) - LEN(LastName)  
```  
  
 <span data-ttu-id="6acff-124">システム変数 **MachineName**を使用して、コンピューター名の長さを返します。</span><span class="sxs-lookup"><span data-stu-id="6acff-124">Returns the length of a computer name using the System variable **MachineName**.</span></span>  
  
```  
LEN(@MachineName)  
```  
  
## <a name="see-also"></a><span data-ttu-id="6acff-125">参照</span><span class="sxs-lookup"><span data-stu-id="6acff-125">See Also</span></span>  
 [<span data-ttu-id="6acff-126">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="6acff-126">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
