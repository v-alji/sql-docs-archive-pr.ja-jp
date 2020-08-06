---
title: 除算 (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- / (divide)
- divide operator (/)
ms.assetid: 5bde9223-872d-443e-8a27-57735e1d8f3d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4541cd4601047770d1bf361077b1c474219e8833
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633219"
---
# <a name="divide-ssis-expression"></a><span data-ttu-id="78528-102">除算 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="78528-102">Divide (SSIS Expression)</span></span>
  <span data-ttu-id="78528-103">最初の数値式を 2 番目の数値式で除算します。</span><span class="sxs-lookup"><span data-stu-id="78528-103">Divides the first numeric expression by the second one.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78528-104">構文</span><span class="sxs-lookup"><span data-stu-id="78528-104">Syntax</span></span>  
  
```  
  
dividend / divisor  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="78528-105">引数</span><span class="sxs-lookup"><span data-stu-id="78528-105">Arguments</span></span>  
 <span data-ttu-id="78528-106">*dividend*</span><span class="sxs-lookup"><span data-stu-id="78528-106">*dividend*</span></span>  
 <span data-ttu-id="78528-107">除算される数値式です。</span><span class="sxs-lookup"><span data-stu-id="78528-107">Is the numeric expression to divide.</span></span> <span data-ttu-id="78528-108">*dividend* には、有効な任意の数値式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="78528-108">*dividend* can be any valid numeric expression.</span></span> <span data-ttu-id="78528-109">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78528-109">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="78528-110">*divisor*</span><span class="sxs-lookup"><span data-stu-id="78528-110">*divisor*</span></span>  
 <span data-ttu-id="78528-111">被除数を除算する数値式です。</span><span class="sxs-lookup"><span data-stu-id="78528-111">Is the numeric expression to divide the dividend by.</span></span> <span data-ttu-id="78528-112">*divisor* には、0 以外の有効な任意の数値式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="78528-112">*divisor* can be any valid numeric expression except zero.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="78528-113">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="78528-113">Result Types</span></span>  
 <span data-ttu-id="78528-114">2 つの引数のデータ型によって決まります。</span><span class="sxs-lookup"><span data-stu-id="78528-114">Determined by data types of the two arguments.</span></span> <span data-ttu-id="78528-115">詳しくは、「 [式における Integration Services データ型](integration-services-data-types-in-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="78528-115">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78528-116">解説</span><span class="sxs-lookup"><span data-stu-id="78528-116">Remarks</span></span>  
 <span data-ttu-id="78528-117">オペランドのいずれかが NULL の場合、結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="78528-117">If either operand is null, the result is null.</span></span>  
  
 <span data-ttu-id="78528-118">0 による除算は無効です。</span><span class="sxs-lookup"><span data-stu-id="78528-118">Dividing by zero is not legal.</span></span> <span data-ttu-id="78528-119">*divisor* サブ式の評価方法に応じて、次のいずれかのエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="78528-119">Depending on how the *divisor* subexpression is evaluated, one of following errors occurs:</span></span>  
  
-   <span data-ttu-id="78528-120">0 に評価される *divisor* サブ式が定数の場合、デザイン時にエラーが表示され、式は検証に失敗します。</span><span class="sxs-lookup"><span data-stu-id="78528-120">If the *divisor* subexpression that evaluates to zero is a constant, the error appears at design time, causing the expression to fail validation.</span></span>  
  
-   <span data-ttu-id="78528-121">0 に評価される *divisor* サブ式に、変数は含まれるが入力列は含まれない場合、式が属するコンポーネントは、パッケージの実行前に行われる事前検証に失敗します。</span><span class="sxs-lookup"><span data-stu-id="78528-121">If the *divisor* subexpression that evaluates to zero contains variables, but no input columns, the component to which the expression belongs fails the pre-execution validation that occurs before the package runs.</span></span>  
  
-   <span data-ttu-id="78528-122">0 に評価される *divisor* サブ式に入力列が含まれる場合、実行時にエラーが表示され、データ フロー コンポーネントのエラー フロー規則に応じて処理されます。</span><span class="sxs-lookup"><span data-stu-id="78528-122">If the *divisor* subexpression that evaluates to zero contains input columns, the error appears at run time and is handled according to the error flow rules of the data flow component.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="78528-123">式の例</span><span class="sxs-lookup"><span data-stu-id="78528-123">Expression Examples</span></span>  
 <span data-ttu-id="78528-124">この例では、2 つの数値リテラルを除算します。</span><span class="sxs-lookup"><span data-stu-id="78528-124">This example divides two numeric literals.</span></span>  
  
```  
25 / 5  
```  
  
 <span data-ttu-id="78528-125">この例では、 **ListPrice** 列の値を **StandardCost** 列の値で除算します。</span><span class="sxs-lookup"><span data-stu-id="78528-125">This example divides values in the **ListPrice** column by values in the **StandardCost** column.</span></span>  
  
```  
ListPrice / StandardCost  
```  
  
## <a name="see-also"></a><span data-ttu-id="78528-126">参照</span><span class="sxs-lookup"><span data-stu-id="78528-126">See Also</span></span>  
 <span data-ttu-id="78528-127">[演算子の優先順位と結合規則](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="78528-127">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="78528-128">演算子 &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="78528-128">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
