---
title: '* (乗算) (SSIS 式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '* (multiply operator)'
- multiply operator (*)
ms.assetid: d457f052-ffbb-4485-833f-f4bed4349b69
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 16d8429a869b60be31a94244a2ce47d515770c6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640159"
---
# <a name="-multiply-ssis-expression"></a><span data-ttu-id="53e65-102">\* (乗算) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="53e65-102">\* (Multiply) (SSIS Expression)</span></span>
  <span data-ttu-id="53e65-103">2 つの数値式を乗算します。</span><span class="sxs-lookup"><span data-stu-id="53e65-103">Multiplies two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53e65-104">構文</span><span class="sxs-lookup"><span data-stu-id="53e65-104">Syntax</span></span>  
  
```  
  
numeric_expression1 * numeric_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="53e65-105">引数</span><span class="sxs-lookup"><span data-stu-id="53e65-105">Arguments</span></span>  
 <span data-ttu-id="53e65-106">*numeric_expression1、numeric_expression2*</span><span class="sxs-lookup"><span data-stu-id="53e65-106">*numeric_expression1, numeric_expression2*</span></span>  
 <span data-ttu-id="53e65-107">数値データ型の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="53e65-107">Is any valid expression of a numeric data type.</span></span> <span data-ttu-id="53e65-108">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53e65-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="53e65-109">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="53e65-109">Result Types</span></span>  
 <span data-ttu-id="53e65-110">2 つの引数のデータ型によって決まります。</span><span class="sxs-lookup"><span data-stu-id="53e65-110">Determined by data types of the two arguments.</span></span> <span data-ttu-id="53e65-111">詳しくは、「 [式における Integration Services データ型](integration-services-data-types-in-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="53e65-111">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53e65-112">解説</span><span class="sxs-lookup"><span data-stu-id="53e65-112">Remarks</span></span>  
 <span data-ttu-id="53e65-113">オペランドのいずれかが NULL の場合、結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="53e65-113">If either operand is null, the result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="53e65-114">式の例</span><span class="sxs-lookup"><span data-stu-id="53e65-114">Expression Examples</span></span>  
 <span data-ttu-id="53e65-115">この例では、数値リテラルを乗算します。</span><span class="sxs-lookup"><span data-stu-id="53e65-115">This example multiplies numeric literals.</span></span>  
  
```  
5 * 6.09  
```  
  
 <span data-ttu-id="53e65-116">この例では、 **ListPrice** 列の値に 10% を乗算します。</span><span class="sxs-lookup"><span data-stu-id="53e65-116">This example multiplies values in the **ListPrice** column by 10 percent.</span></span>  
  
```  
ListPrice * .10  
```  
  
 <span data-ttu-id="53e65-117">この例では、 **ListPrice** 列から式の結果を減算します。</span><span class="sxs-lookup"><span data-stu-id="53e65-117">This example subtracts the result of an expression from the **ListPrice** column.</span></span> <span data-ttu-id="53e65-118">変数 **Discount%** は、名前に % 文字が含まれているため、角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="53e65-118">The variable **Discount%** must be enclosed in brackets because the name includes the % character.</span></span> <span data-ttu-id="53e65-119">詳しくは、「[識別子 &#40;SSIS&#41;](identifiers-ssis.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="53e65-119">For more information, see [Identifiers &#40;SSIS&#41;](identifiers-ssis.md).</span></span>  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## <a name="see-also"></a><span data-ttu-id="53e65-120">参照</span><span class="sxs-lookup"><span data-stu-id="53e65-120">See Also</span></span>  
 <span data-ttu-id="53e65-121">[演算子の優先順位と結合規則](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="53e65-121">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="53e65-122">演算子 &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="53e65-122">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
