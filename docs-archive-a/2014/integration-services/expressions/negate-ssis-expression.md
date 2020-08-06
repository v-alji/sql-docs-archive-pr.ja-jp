---
title: '- (負数化) (SSIS 式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '- (negative)'
- negative operator (-)
ms.assetid: f0118dfc-aced-4de2-953e-5ebf9c962b8d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2a2d8ba292f2d24633598ab080ddf75ded5e8bd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720270"
---
# <a name="--negate-ssis-expression"></a><span data-ttu-id="18911-102">- (負数化) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="18911-102">- (Negate) (SSIS Expression)</span></span>
  <span data-ttu-id="18911-103">数値式を負数化します。</span><span class="sxs-lookup"><span data-stu-id="18911-103">Negates a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18911-104">構文</span><span class="sxs-lookup"><span data-stu-id="18911-104">Syntax</span></span>  
  
```  
  
-numeric_expression  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="18911-105">引数</span><span class="sxs-lookup"><span data-stu-id="18911-105">Arguments</span></span>  
 <span data-ttu-id="18911-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="18911-106">*numeric_expression*</span></span>  
 <span data-ttu-id="18911-107">任意の数値データ型の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="18911-107">Is any valid expression of any numeric data type.</span></span> <span data-ttu-id="18911-108">サポートされるデータ型は、符号付き数値データ型のみです。</span><span class="sxs-lookup"><span data-stu-id="18911-108">Only signed numeric data types are supported.</span></span> <span data-ttu-id="18911-109">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18911-109">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="18911-110">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="18911-110">Result Types</span></span>  
 <span data-ttu-id="18911-111">データ型を返す *numeric_expression*です。</span><span class="sxs-lookup"><span data-stu-id="18911-111">Returns the data type of *numeric_expression*.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="18911-112">式の例</span><span class="sxs-lookup"><span data-stu-id="18911-112">Expression Examples</span></span>  
 <span data-ttu-id="18911-113">この例では、変数 **Counter** の値を負数化して、数値リテラル 50 を加算します。</span><span class="sxs-lookup"><span data-stu-id="18911-113">This example negates the value of the **Counter** variable and adds the numeric literal 50.</span></span>  
  
```  
-@Counter + 50  
```  
  
## <a name="see-also"></a><span data-ttu-id="18911-114">参照</span><span class="sxs-lookup"><span data-stu-id="18911-114">See Also</span></span>  
 <span data-ttu-id="18911-115">[演算子の優先順位と結合規則](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="18911-115">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="18911-116">演算子 &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="18911-116">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
