---
title: CODEPOINT (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- CODEPOINT function
- leftmost character of expression
ms.assetid: 0783d05e-7f35-42fb-a2c4-9621c46effd6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bf05cc0838763ba9e22707af57892133d449da07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632017"
---
# <a name="codepoint-ssis-expression"></a><span data-ttu-id="f987a-102">CODEPOINT (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="f987a-102">CODEPOINT (SSIS Expression)</span></span>
  <span data-ttu-id="f987a-103">文字式の一番左の文字の Unicode コード ポイントを返します。</span><span class="sxs-lookup"><span data-stu-id="f987a-103">Returns the Unicode code point of the leftmost character of a character expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f987a-104">構文</span><span class="sxs-lookup"><span data-stu-id="f987a-104">Syntax</span></span>  
  
```  
  
CODEPOINT(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="f987a-105">引数</span><span class="sxs-lookup"><span data-stu-id="f987a-105">Arguments</span></span>  
 <span data-ttu-id="f987a-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="f987a-106">*character_expression*</span></span>  
 <span data-ttu-id="f987a-107">一番左の文字を評価する文字式です。</span><span class="sxs-lookup"><span data-stu-id="f987a-107">Is a character expression whose leftmost character will be evaluated.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f987a-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="f987a-108">Result Types</span></span>  
 <span data-ttu-id="f987a-109">DT_UI2</span><span class="sxs-lookup"><span data-stu-id="f987a-109">DT_UI2</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f987a-110">解説</span><span class="sxs-lookup"><span data-stu-id="f987a-110">Remarks</span></span>  
 <span data-ttu-id="f987a-111">*character_expression* は、DT_WSTR データ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="f987a-111">*character_expression* must have the DT_WSTR data type.</span></span>  
  
 <span data-ttu-id="f987a-112">*character_expression* が NULL または空の文字列の場合、CODEPOINT は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="f987a-112">CODEPOINT returns a null result if *character_expression* is null or an empty string.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="f987a-113">式の例</span><span class="sxs-lookup"><span data-stu-id="f987a-113">Expression Examples</span></span>  
 <span data-ttu-id="f987a-114">この例では、文字列リテラルを使用します。</span><span class="sxs-lookup"><span data-stu-id="f987a-114">This example uses a string literal.</span></span> <span data-ttu-id="f987a-115">返される結果は 77 で、Unicode コード ポイントは M です。</span><span class="sxs-lookup"><span data-stu-id="f987a-115">The return result is 77, the Unicode code point for M.</span></span>  
  
```  
CODEPOINT("Mountain Bike")  
```  
  
 <span data-ttu-id="f987a-116">この例では、変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="f987a-116">This example uses a variable.</span></span> <span data-ttu-id="f987a-117">**Name** が Touring Front Wheel の場合、返される結果は 84 で、Unicode コード ポイントは T です。</span><span class="sxs-lookup"><span data-stu-id="f987a-117">If **Name** is Touring Front Wheel, the return result is 84, the Unicode code point for T.</span></span>  
  
```  
CODEPOINT(@Name)  
```  
  
## <a name="see-also"></a><span data-ttu-id="f987a-118">参照</span><span class="sxs-lookup"><span data-stu-id="f987a-118">See Also</span></span>  
 [<span data-ttu-id="f987a-119">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="f987a-119">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
