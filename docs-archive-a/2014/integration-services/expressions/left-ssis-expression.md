---
title: LEFT (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5634dbfb-740d-4c93-8fd5-2854cc741327
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7f21d134988414c7d8579d720877feec45383270
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644026"
---
# <a name="left-ssis-expression"></a><span data-ttu-id="96c22-102">LEFT (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="96c22-102">LEFT (SSIS Expression)</span></span>
  <span data-ttu-id="96c22-103">指定された文字式の一番左の部分から指定された数の文字を返します。</span><span class="sxs-lookup"><span data-stu-id="96c22-103">Returns the specified number of characters from the leftmost portion of the given character expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96c22-104">構文</span><span class="sxs-lookup"><span data-stu-id="96c22-104">Syntax</span></span>  
  
```  
  
LEFT(character_expression,number)  
```  
  
## <a name="arguments"></a><span data-ttu-id="96c22-105">引数</span><span class="sxs-lookup"><span data-stu-id="96c22-105">Arguments</span></span>  
 <span data-ttu-id="96c22-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="96c22-106">*character_expression*</span></span>  
 <span data-ttu-id="96c22-107">文字の抽出元となる文字式です。</span><span class="sxs-lookup"><span data-stu-id="96c22-107">Is a character expression from which to extract characters.</span></span>  
  
 <span data-ttu-id="96c22-108">*number*</span><span class="sxs-lookup"><span data-stu-id="96c22-108">*number*</span></span>  
 <span data-ttu-id="96c22-109">返す文字の数を示す整数式です。</span><span class="sxs-lookup"><span data-stu-id="96c22-109">Is an integer expression that indicates the number of characters to be returned.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="96c22-110">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="96c22-110">Result Types</span></span>  
 <span data-ttu-id="96c22-111">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="96c22-111">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96c22-112">解説</span><span class="sxs-lookup"><span data-stu-id="96c22-112">Remarks</span></span>  
 <span data-ttu-id="96c22-113">*number* が *character_expression*より長い場合、関数は *character_expression*を返します。</span><span class="sxs-lookup"><span data-stu-id="96c22-113">If *number* is greater than the length of *character_expression*, the function returns *character_expression*.</span></span>  
  
 <span data-ttu-id="96c22-114">*number* が 0 の場合、関数は長さが 0 の文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="96c22-114">If *number* is zero, the function returns a zero-length string.</span></span>  
  
 <span data-ttu-id="96c22-115">*number* が負の値の場合、関数はエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="96c22-115">If *number* is a negative number, the function returns an error.</span></span>  
  
 <span data-ttu-id="96c22-116">*number* 引数には、変数および列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="96c22-116">The *number* argument can take variables and columns.</span></span>  
  
 <span data-ttu-id="96c22-117">LEFT は、DT_WSTR データ型でのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="96c22-117">LEFT works only with the DT_WSTR data type.</span></span> <span data-ttu-id="96c22-118">*character_expression* 引数が DT_STR データ型の文字列リテラルまたはデータ列である場合は、LEFT による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="96c22-118">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before LEFT performs its operation.</span></span> <span data-ttu-id="96c22-119">その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="96c22-119">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="96c22-120">詳しくは、「[Integration Services のデータ型](../data-flow/integration-services-data-types.md)」および「[Cast &#40;SSIS 式&#41;](cast-ssis-expression.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="96c22-120">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="96c22-121">引数のいずれかが NULL の場合、LEFT は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="96c22-121">LEFT returns a null result if either argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="96c22-122">式の例</span><span class="sxs-lookup"><span data-stu-id="96c22-122">Expression Examples</span></span>  
 <span data-ttu-id="96c22-123">次の例では、文字列リテラルを使用します。</span><span class="sxs-lookup"><span data-stu-id="96c22-123">The following example uses a string literal.</span></span> <span data-ttu-id="96c22-124">返される結果は `"Mountain"`です。</span><span class="sxs-lookup"><span data-stu-id="96c22-124">The return result is `"Mountain"`.</span></span>  
  
```  
LEFT("Mountain Bike", 8)  
```  
  
## <a name="see-also"></a><span data-ttu-id="96c22-125">参照</span><span class="sxs-lookup"><span data-stu-id="96c22-125">See Also</span></span>  
 <span data-ttu-id="96c22-126">[RIGHT (SSIS 式)](right-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="96c22-126">[RIGHT &#40;SSIS Expression&#41;](right-ssis-expression.md) </span></span>  
 [<span data-ttu-id="96c22-127">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="96c22-127">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
