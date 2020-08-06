---
title: '- (減算) (SSIS 式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '- (subtract)'
- subtract operator (-)
ms.assetid: b48da086-37dd-460a-8a4b-912f52c9b158
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 79c47689baf47c33952c6b208ac622e9920d05fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716454"
---
# <a name="--subtract-ssis-expression"></a><span data-ttu-id="76bbc-102">- (減算) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="76bbc-102">- (Subtract) (SSIS Expression)</span></span>
  <span data-ttu-id="76bbc-103">最初の数値式から 2 番目の数値式を減算します。</span><span class="sxs-lookup"><span data-stu-id="76bbc-103">Subtracts the second numeric expression from the first one.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76bbc-104">構文</span><span class="sxs-lookup"><span data-stu-id="76bbc-104">Syntax</span></span>  
  
```  
  
numeric_expression1 - numeric_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="76bbc-105">引数</span><span class="sxs-lookup"><span data-stu-id="76bbc-105">Arguments</span></span>  
 <span data-ttu-id="76bbc-106">*numeric_expression1、numeric_expression2*</span><span class="sxs-lookup"><span data-stu-id="76bbc-106">*numeric_expression1, numeric_expression2*</span></span>  
 <span data-ttu-id="76bbc-107">数値データ型の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="76bbc-107">Is any valid expression of a numeric data type.</span></span> <span data-ttu-id="76bbc-108">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76bbc-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="76bbc-109">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="76bbc-109">Result Types</span></span>  
 <span data-ttu-id="76bbc-110">2 つの引数のデータ型によって決まります。</span><span class="sxs-lookup"><span data-stu-id="76bbc-110">Determined by the data types of the two arguments.</span></span> <span data-ttu-id="76bbc-111">詳しくは、「 [式における Integration Services データ型](integration-services-data-types-in-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="76bbc-111">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76bbc-112">解説</span><span class="sxs-lookup"><span data-stu-id="76bbc-112">Remarks</span></span>  
 <span data-ttu-id="76bbc-113">式が正しい順序で評価されるようにするために、マイナス単項式はかっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="76bbc-113">Enclose the minus unary expression in parenthesis to ensure that the expression is evaluated in the correct order</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76bbc-114">解説</span><span class="sxs-lookup"><span data-stu-id="76bbc-114">Remarks</span></span>  
 <span data-ttu-id="76bbc-115">オペランドのいずれかが NULL の場合、結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="76bbc-115">If either operand is null, the result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="76bbc-116">式の例</span><span class="sxs-lookup"><span data-stu-id="76bbc-116">Expression Examples</span></span>  
 <span data-ttu-id="76bbc-117">この例では、数値リテラルを減算します。</span><span class="sxs-lookup"><span data-stu-id="76bbc-117">This example subtracts numeric literals.</span></span>  
  
```  
5 - 6.09  
```  
  
 <span data-ttu-id="76bbc-118">この例では、 **ListPrice** 列の値から **StandardCost** 列の値を減算します。</span><span class="sxs-lookup"><span data-stu-id="76bbc-118">This example subtracts the value in the **StandardCost** column from the value in the **ListPrice** column.</span></span>  
  
```  
ListPrice - StandardCost  
```  
  
 <span data-ttu-id="76bbc-119">この例では、計算した値を **ListPrice** 列から減算します。</span><span class="sxs-lookup"><span data-stu-id="76bbc-119">This example subtracts a calculated value from the **ListPrice** column.</span></span> <span data-ttu-id="76bbc-120">変数 **Discount%** は、名前に % 文字が含まれているため、角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="76bbc-120">The variable **Discount%** must be enclosed in brackets because the name includes the % character.</span></span> <span data-ttu-id="76bbc-121">詳しくは、「[識別子 &#40;SSIS&#41;](identifiers-ssis.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="76bbc-121">For more information, see [Identifiers &#40;SSIS&#41;](identifiers-ssis.md).</span></span>  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## <a name="see-also"></a><span data-ttu-id="76bbc-122">参照</span><span class="sxs-lookup"><span data-stu-id="76bbc-122">See Also</span></span>  
 <span data-ttu-id="76bbc-123">[演算子の優先順位と結合規則](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="76bbc-123">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="76bbc-124">演算子 &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="76bbc-124">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
