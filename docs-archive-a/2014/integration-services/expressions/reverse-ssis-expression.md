---
title: REVERSE (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- REVERSE function
- reverse character expressions
ms.assetid: bcebcc55-7247-4896-8f53-4d582d58cfb4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2ace136eed0abcb9df7b25d9370c46d7556c1d48
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716494"
---
# <a name="reverse-ssis-expression"></a><span data-ttu-id="a3f3c-102">REVERSE (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="a3f3c-102">REVERSE (SSIS Expression)</span></span>
  <span data-ttu-id="a3f3c-103">文字式を逆に並べ替えたものを返します。</span><span class="sxs-lookup"><span data-stu-id="a3f3c-103">Returns a character expression in reverse order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3f3c-104">構文</span><span class="sxs-lookup"><span data-stu-id="a3f3c-104">Syntax</span></span>  
  
```  
  
REVERSE(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="a3f3c-105">引数</span><span class="sxs-lookup"><span data-stu-id="a3f3c-105">Arguments</span></span>  
 <span data-ttu-id="a3f3c-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="a3f3c-106">*character_expression*</span></span>  
 <span data-ttu-id="a3f3c-107">逆に並べ替える対象となる文字式です。</span><span class="sxs-lookup"><span data-stu-id="a3f3c-107">Is a character expression to be reversed.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a3f3c-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="a3f3c-108">Result Types</span></span>  
 <span data-ttu-id="a3f3c-109">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="a3f3c-109">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3f3c-110">解説</span><span class="sxs-lookup"><span data-stu-id="a3f3c-110">Remarks</span></span>  
 <span data-ttu-id="a3f3c-111">*character_expression* 引数は、DT_WSTR データ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3f3c-111">The *character_expression* argument must have the DT_WSTR data type.</span></span>  
  
 <span data-ttu-id="a3f3c-112">*character_expression* が NULL の場合、REVERSE は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="a3f3c-112">REVERSE returns a null result if *character_expression* is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="a3f3c-113">式の例</span><span class="sxs-lookup"><span data-stu-id="a3f3c-113">Expression Examples</span></span>  
 <span data-ttu-id="a3f3c-114">この例では、文字列リテラルを使用します。</span><span class="sxs-lookup"><span data-stu-id="a3f3c-114">This example uses a string literal.</span></span> <span data-ttu-id="a3f3c-115">返される結果は "ekiB niatnuoM" です。</span><span class="sxs-lookup"><span data-stu-id="a3f3c-115">The return result is "ekiB niatnuoM".</span></span>  
  
```  
REVERSE("Mountain Bike")  
```  
  
 <span data-ttu-id="a3f3c-116">この例では、変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="a3f3c-116">This example uses a variable.</span></span> <span data-ttu-id="a3f3c-117">**Name** に Touring Bike が含まれる場合、返される結果は "ekiB gniruoT" です。</span><span class="sxs-lookup"><span data-stu-id="a3f3c-117">If **Name** contains Touring Bike, the return result is "ekiB gniruoT".</span></span>  
  
```  
REVERSE(@Name)  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3f3c-118">参照</span><span class="sxs-lookup"><span data-stu-id="a3f3c-118">See Also</span></span>  
 [<span data-ttu-id="a3f3c-119">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="a3f3c-119">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
