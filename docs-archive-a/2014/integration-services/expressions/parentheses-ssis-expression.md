---
title: () (かっこ) (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- () (parentheses operator)
- evaluation order [Integration Services]
- parentheses operator ()
ms.assetid: 931e10eb-1707-4121-b2f1-43565561119f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e390e10e485bd9cc22480300b6a9c33098bda8f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740158"
---
# <a name="-parentheses-ssis-expression"></a><span data-ttu-id="45bdb-102">() (かっこ) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="45bdb-102">() (Parentheses) (SSIS Expression)</span></span>
  <span data-ttu-id="45bdb-103">式の評価順序を特定します。</span><span class="sxs-lookup"><span data-stu-id="45bdb-103">Identifies the evaluation order of expressions.</span></span> <span data-ttu-id="45bdb-104">かっこで囲まれた式は、評価の優先順位が最も高くなります。</span><span class="sxs-lookup"><span data-stu-id="45bdb-104">Expressions enclosed in parentheses have the highest evaluation precedence.</span></span> <span data-ttu-id="45bdb-105">かっこで囲まれ、入れ子になっている式は、内側から外側の順に評価されます。</span><span class="sxs-lookup"><span data-stu-id="45bdb-105">Nested expressions enclosed in parentheses are evaluated in inner-to-outer order.</span></span>  
  
 <span data-ttu-id="45bdb-106">かっこは、複合式を理解しやすくするためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="45bdb-106">Parentheses are also used to make complex expressions easier to understand.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45bdb-107">構文</span><span class="sxs-lookup"><span data-stu-id="45bdb-107">Syntax</span></span>  
  
```  
  
(expression)  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="45bdb-108">引数</span><span class="sxs-lookup"><span data-stu-id="45bdb-108">Arguments</span></span>  
 <span data-ttu-id="45bdb-109">*式 (expression)*</span><span class="sxs-lookup"><span data-stu-id="45bdb-109">*expression*</span></span>  
 <span data-ttu-id="45bdb-110">任意の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="45bdb-110">Is any valid expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="45bdb-111">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="45bdb-111">Result Types</span></span>  
 <span data-ttu-id="45bdb-112">*expression*のデータ型。</span><span class="sxs-lookup"><span data-stu-id="45bdb-112">The data type of *expression*.</span></span> <span data-ttu-id="45bdb-113">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45bdb-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="45bdb-114">式の例</span><span class="sxs-lookup"><span data-stu-id="45bdb-114">Expression Examples</span></span>  
 <span data-ttu-id="45bdb-115">次の例では、かっこを使用して演算子の優先順位を変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="45bdb-115">This example shows how the use of parenthesis modifies the precedence of operators.</span></span> <span data-ttu-id="45bdb-116">最初の式は 100 と評価され、2 番目の式は 31 と評価されます。</span><span class="sxs-lookup"><span data-stu-id="45bdb-116">The first expression evaluates to 100, whereas the second one evaluates to 31.</span></span>  
  
```  
(5 + 5) * (4 + 6)  
5 + 5 * 4 + 6  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="45bdb-117">参照</span><span class="sxs-lookup"><span data-stu-id="45bdb-117">See Also</span></span>  
 <span data-ttu-id="45bdb-118">[演算子の優先順位と結合規則](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="45bdb-118">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="45bdb-119">演算子 &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="45bdb-119">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
