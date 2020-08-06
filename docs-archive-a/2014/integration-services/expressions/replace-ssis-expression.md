---
title: REPLACE (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- replacing string expression
- REPLACE function
ms.assetid: a6837043-ea70-4c6a-9c7a-6868b02b2adc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e483ba6c9c72cb777f2955929a717c6c2e17a8c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716502"
---
# <a name="replace-ssis-expression"></a><span data-ttu-id="fbb14-102">REPLACE (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="fbb14-102">REPLACE (SSIS Expression)</span></span>
  <span data-ttu-id="fbb14-103">式に含まれている文字列を別の文字列または空の文字列で置き換えた文字式を返します。</span><span class="sxs-lookup"><span data-stu-id="fbb14-103">Returns a character expression after replacing a character string within the expression with either a different character string or an empty string.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fbb14-104">REPLACE 関数では、長い文字列が頻繁に使用されます。</span><span class="sxs-lookup"><span data-stu-id="fbb14-104">The REPLACE function frequently uses long strings.</span></span> <span data-ttu-id="fbb14-105">切り捨ての結果を効率よく処理できる場合もあれば、結果により警告またはエラーが発生する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="fbb14-105">The consequences of truncation can be handled gracefully or cause a warning or an error.</span></span> <span data-ttu-id="fbb14-106">詳しくは、「[構文 &#40;SSIS&#41;](syntax-ssis.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fbb14-106">For more information, see [Syntax &#40;SSIS&#41;](syntax-ssis.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbb14-107">構文</span><span class="sxs-lookup"><span data-stu-id="fbb14-107">Syntax</span></span>  
  
```  
  
REPLACE(character_expression,searchstring,replacementstring)  
```  
  
## <a name="arguments"></a><span data-ttu-id="fbb14-108">引数</span><span class="sxs-lookup"><span data-stu-id="fbb14-108">Arguments</span></span>  
 <span data-ttu-id="fbb14-109">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="fbb14-109">*character_expression*</span></span>  
 <span data-ttu-id="fbb14-110">検索対象となる有効な文字式です。</span><span class="sxs-lookup"><span data-stu-id="fbb14-110">Is a valid character expression that the function searches.</span></span>  
  
 <span data-ttu-id="fbb14-111">*searchstring*</span><span class="sxs-lookup"><span data-stu-id="fbb14-111">*searchstring*</span></span>  
 <span data-ttu-id="fbb14-112">関数により検索される有効な文字式です。</span><span class="sxs-lookup"><span data-stu-id="fbb14-112">Is a valid character expression that the function attempts to locate.</span></span>  
  
 <span data-ttu-id="fbb14-113">*replacementstring*</span><span class="sxs-lookup"><span data-stu-id="fbb14-113">*replacementstring*</span></span>  
 <span data-ttu-id="fbb14-114">置換後の式となる有効な文字式です。</span><span class="sxs-lookup"><span data-stu-id="fbb14-114">Is a valid character expression that is the replacement expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="fbb14-115">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="fbb14-115">Result Types</span></span>  
 <span data-ttu-id="fbb14-116">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="fbb14-116">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbb14-117">解説</span><span class="sxs-lookup"><span data-stu-id="fbb14-117">Remarks</span></span>  
 <span data-ttu-id="fbb14-118">*searchstring* の長さを 0 にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="fbb14-118">The length of *searchstring* must not be zero.</span></span>  
  
 <span data-ttu-id="fbb14-119">*replacementstring* の長さは 0 にすることができます。</span><span class="sxs-lookup"><span data-stu-id="fbb14-119">The length of *replacementstring* may be zero.</span></span>  
  
 <span data-ttu-id="fbb14-120">*searchstring* 引数および *replacementstring* 引数には、変数と列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="fbb14-120">The *searchstring* and *replacementstring* arguments can use variables and columns.</span></span>  
  
 <span data-ttu-id="fbb14-121">REPLACE は、DT_WSTR データ型でのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="fbb14-121">REPLACE works only with the DT_WSTR data type.</span></span> <span data-ttu-id="fbb14-122">*character_expression1、character_expression2* 、および *character_expression3* 引数が DT_STR データ型の文字列リテラルまたはデータ列である場合は、REPLACE による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="fbb14-122">*character_expression1, character_expression2,* and *character_expression3* arguments that are string literals or data columns with the DT_STR data type are implicitly cast to the DT_WSTR data type before REPLACE performs its operation.</span></span> <span data-ttu-id="fbb14-123">その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbb14-123">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="fbb14-124">詳細については、「[Cast &#40;SSIS 式&#41;](cast-ssis-expression.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fbb14-124">For more information, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="fbb14-125">いずれかの引数が NULL の場合、REPLACE は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="fbb14-125">REPLACE returns a null result if any argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="fbb14-126">式の例</span><span class="sxs-lookup"><span data-stu-id="fbb14-126">Expression Examples</span></span>  
 <span data-ttu-id="fbb14-127">この例では、文字列リテラルを使用します。</span><span class="sxs-lookup"><span data-stu-id="fbb14-127">This example uses a string literal.</span></span> <span data-ttu-id="fbb14-128">返される結果は "All Terrain Bike" です。</span><span class="sxs-lookup"><span data-stu-id="fbb14-128">The return result is "All Terrain Bike".</span></span>  
  
```  
REPLACE("Mountain Bike", "Mountain","All Terrain")  
```  
  
 <span data-ttu-id="fbb14-129">この例では、 **Product** 列から文字列 "Bike" を削除します。</span><span class="sxs-lookup"><span data-stu-id="fbb14-129">This example removes the string "Bike" from the **Product** column.</span></span>  
  
```  
REPLACE(Product, "Bike","")  
```  
  
 <span data-ttu-id="fbb14-130">この例では、 **DaysToManufacture** 列の値を置換します。</span><span class="sxs-lookup"><span data-stu-id="fbb14-130">This example replaces values in the **DaysToManufacture** column.</span></span> <span data-ttu-id="fbb14-131">**DaysToManufacture** 列は整数データ型で、式の内部で DT_WSTR データ型にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="fbb14-131">The column has an integer data type and the expression includes casting **DaysToManufacture** to the DT_WSTR data type.</span></span>  
  
```  
REPLACE((DT_WSTR,8)DaysToManufacture,"6","5")  
```  
  
## <a name="see-also"></a><span data-ttu-id="fbb14-132">参照</span><span class="sxs-lookup"><span data-stu-id="fbb14-132">See Also</span></span>  
 <span data-ttu-id="fbb14-133">[SUBSTRING &#40;SSIS 式&#41;](substring-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="fbb14-133">[SUBSTRING &#40;SSIS Expression&#41;](substring-ssis-expression.md) </span></span>  
 [<span data-ttu-id="fbb14-134">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="fbb14-134">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
