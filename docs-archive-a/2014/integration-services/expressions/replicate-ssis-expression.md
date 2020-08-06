---
title: REPLICATE (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- REPLICATE function
ms.assetid: e7a37b93-6d1d-42d5-9a65-de1790abf6a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9502df5bc20c6ad85f1f98fb57fe6b3cf431cc20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716497"
---
# <a name="replicate-ssis-expression"></a><span data-ttu-id="253b9-102">REPLICATE (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="253b9-102">REPLICATE (SSIS Expression)</span></span>
  <span data-ttu-id="253b9-103">指定された回数だけレプリケートされた文字式を返します。</span><span class="sxs-lookup"><span data-stu-id="253b9-103">Returns a character expression that is replicated a number of times.</span></span> <span data-ttu-id="253b9-104">*times* 引数は整数に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="253b9-104">The *times* argument must evaluate to an integer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="253b9-105">REPLICATE 関数では長い文字列が使用される場合が多いため、式の長さに対する 4,000 文字の制限が発生する可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="253b9-105">The REPLICATE function frequently uses long strings, and therefore is more likely to incur the 4000-character limit on expression length.</span></span> <span data-ttu-id="253b9-106">式の評価結果が Integration Services データ型の DT_WSTR または DT_STR である場合、式は 4,000 文字に切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="253b9-106">If the evaluation result of an expression has the Integration Services data type DT_WSTR or DT_STR, the expression will be truncated at 4000 characters.</span></span> <span data-ttu-id="253b9-107">サブ式の結果のデータ型が DT_STR または DT_WSTR である場合、式全体の結果のデータ型に関係なく、そのサブ式も同様に 4,000 文字に切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="253b9-107">If the result type of a sub-expression is DT_STR or DT_WSTR, that sub-expression likewise will be truncated to 4000 characters, regardless of the overall expression result type.</span></span> <span data-ttu-id="253b9-108">切り捨ての結果を効率よく処理できる場合もあれば、結果により警告またはエラーが発生する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="253b9-108">The consequences of truncation can be handled gracefully or cause a warning or an error.</span></span> <span data-ttu-id="253b9-109">詳しくは、「[構文 &#40;SSIS&#41;](syntax-ssis.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="253b9-109">For more information, see [Syntax &#40;SSIS&#41;](syntax-ssis.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="253b9-110">構文</span><span class="sxs-lookup"><span data-stu-id="253b9-110">Syntax</span></span>  
  
```  
  
REPLICATE(character_expression,times)  
```  
  
## <a name="arguments"></a><span data-ttu-id="253b9-111">引数</span><span class="sxs-lookup"><span data-stu-id="253b9-111">Arguments</span></span>  
 <span data-ttu-id="253b9-112">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="253b9-112">*character_expression*</span></span>  
 <span data-ttu-id="253b9-113">レプリケートする文字式です。</span><span class="sxs-lookup"><span data-stu-id="253b9-113">Is a character expression to replicate.</span></span>  
  
 <span data-ttu-id="253b9-114">*times*</span><span class="sxs-lookup"><span data-stu-id="253b9-114">*times*</span></span>  
 <span data-ttu-id="253b9-115">*character_expression* がレプリケートされる回数を指定する整数式です。</span><span class="sxs-lookup"><span data-stu-id="253b9-115">Is an integer expression that specifies the number of times *character_expression* is replicated.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="253b9-116">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="253b9-116">Result Types</span></span>  
 <span data-ttu-id="253b9-117">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="253b9-117">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="253b9-118">解説</span><span class="sxs-lookup"><span data-stu-id="253b9-118">Remarks</span></span>  
 <span data-ttu-id="253b9-119">*times* が 0 の場合、関数は長さが 0 の文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="253b9-119">If *times* is zero, the function returns a zero-length string.</span></span>  
  
 <span data-ttu-id="253b9-120">*times* が負の値の場合、関数はエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="253b9-120">If *times* is a negative number, the function returns an error.</span></span>  
  
 <span data-ttu-id="253b9-121">*times* 引数には、変数や列も使用できます。</span><span class="sxs-lookup"><span data-stu-id="253b9-121">The *times* argument can also use variables and columns.</span></span>  
  
 <span data-ttu-id="253b9-122">REPLICATE は、DT_WSTR データ型でのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="253b9-122">REPLICATE works only with the DT_WSTR data type.</span></span> <span data-ttu-id="253b9-123">*character_expression* 引数が DT_STR データ型の文字列リテラルまたはデータ列である場合は、REPLICATE による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="253b9-123">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before REPLICATE performs its operation.</span></span> <span data-ttu-id="253b9-124">その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="253b9-124">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="253b9-125">詳しくは、「[Integration Services のデータ型](../data-flow/integration-services-data-types.md)」および「[Cast &#40;SSIS 式&#41;](cast-ssis-expression.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="253b9-125">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="253b9-126">引数のいずれかが NULL の場合、REPLICATE は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="253b9-126">REPLICATE returns a null result if either argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="253b9-127">式の例</span><span class="sxs-lookup"><span data-stu-id="253b9-127">Expression Examples</span></span>  
 <span data-ttu-id="253b9-128">この例では、文字列リテラルを 3 回レプリケートします。</span><span class="sxs-lookup"><span data-stu-id="253b9-128">This example replicates a string literal three times.</span></span> <span data-ttu-id="253b9-129">返される結果は、"Mountain BikeMountain BikeMountain Bike" です。</span><span class="sxs-lookup"><span data-stu-id="253b9-129">The return result is "Mountain BikeMountain BikeMountain Bike".</span></span>  
  
```  
REPLICATE("Mountain Bike", 3)  
```  
  
 <span data-ttu-id="253b9-130">この例では、 **Name** 列の値を変数 **Times** の値の回数だけレプリケートします。</span><span class="sxs-lookup"><span data-stu-id="253b9-130">This example replicates values in the **Name** column by the value in the **Times** variable.</span></span> <span data-ttu-id="253b9-131">**Times** が 3、 **Name** が Touring Front Wheel の場合、返される結果は "Touring Front WheelTouring Front WheelTouring Front Wheel" になります。</span><span class="sxs-lookup"><span data-stu-id="253b9-131">If **Times** is 3 and **Name** is Touring Front Wheel, the return result is Touring Front WheelTouring Front WheelTouring Front Wheel.</span></span>  
  
```  
REPLICATE(Name, @Times)  
```  
  
 <span data-ttu-id="253b9-132">この例では、変数 **Name** の値を **Times** 列の値の回数だけレプリケートします。</span><span class="sxs-lookup"><span data-stu-id="253b9-132">This example replicates the value in the **Name** variable by the value in the **Times** column.</span></span> <span data-ttu-id="253b9-133">**Times** の値は整数データ型でなく、式には整数データ型への明示的なキャストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="253b9-133">**Times** has a non-integer data type and the expression includes an explicit cast to an integer data type.</span></span> <span data-ttu-id="253b9-134">**Name** に Helmet が含まれ、 **Times** が 2 の場合、返される結果は "HelmetHelmet" になります。</span><span class="sxs-lookup"><span data-stu-id="253b9-134">If **Name** contains Helmet and **Times** is 2, the return result is "HelmetHelmet".</span></span>  
  
```  
REPLICATE(@Name, (DT_I4(Times))  
```  
  
## <a name="see-also"></a><span data-ttu-id="253b9-135">参照</span><span class="sxs-lookup"><span data-stu-id="253b9-135">See Also</span></span>  
 [<span data-ttu-id="253b9-136">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="253b9-136">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
