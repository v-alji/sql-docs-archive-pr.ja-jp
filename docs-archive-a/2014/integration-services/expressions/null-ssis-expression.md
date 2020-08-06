---
title: NULL (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- NULL function
- null values [Integration Services]
ms.assetid: df144237-3fbb-41ac-8624-efd92b6522b9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e14cd51b4e245ca6984a4c62eae2b9d5536ab1f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632016"
---
# <a name="null-ssis-expression"></a><span data-ttu-id="aad15-102">NULL (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="aad15-102">NULL (SSIS Expression)</span></span>
  <span data-ttu-id="aad15-103">要求されたデータ型の NULL 値を返します。</span><span class="sxs-lookup"><span data-stu-id="aad15-103">Returns a null value of a requested data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aad15-104">構文</span><span class="sxs-lookup"><span data-stu-id="aad15-104">Syntax</span></span>  
  
```  
  
NULL(typespec)  
```  
  
## <a name="arguments"></a><span data-ttu-id="aad15-105">引数</span><span class="sxs-lookup"><span data-stu-id="aad15-105">Arguments</span></span>  
 <span data-ttu-id="aad15-106">*typespec*</span><span class="sxs-lookup"><span data-stu-id="aad15-106">*typespec*</span></span>  
 <span data-ttu-id="aad15-107">有効なデータ型です。</span><span class="sxs-lookup"><span data-stu-id="aad15-107">Is a valid data type.</span></span> <span data-ttu-id="aad15-108">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aad15-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="aad15-109">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="aad15-109">Result Types</span></span>  
 <span data-ttu-id="aad15-110">NULL 値である任意の有効なデータ型です。</span><span class="sxs-lookup"><span data-stu-id="aad15-110">Any valid data type with a null value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aad15-111">解説</span><span class="sxs-lookup"><span data-stu-id="aad15-111">Remarks</span></span>  
 <span data-ttu-id="aad15-112">引数が NULL の場合、NULL 関数は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="aad15-112">NULL returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="aad15-113">一部のデータ型の NULL 値を要求する場合は、パラメーターが必要となります。</span><span class="sxs-lookup"><span data-stu-id="aad15-113">Parameters are required to request a null value for some data types.</span></span> <span data-ttu-id="aad15-114">次の表に、パラメーターが必要なデータ型とそのパラメーターの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="aad15-114">The following table lists these data types and their parameters.</span></span>  
  
|<span data-ttu-id="aad15-115">データ型</span><span class="sxs-lookup"><span data-stu-id="aad15-115">Data type</span></span>|<span data-ttu-id="aad15-116">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aad15-116">Parameter</span></span>|<span data-ttu-id="aad15-117">例</span><span class="sxs-lookup"><span data-stu-id="aad15-117">Example</span></span>|  
|---------------|---------------|-------------|  
|<span data-ttu-id="aad15-118">DT_STR</span><span class="sxs-lookup"><span data-stu-id="aad15-118">DT_STR</span></span>|<span data-ttu-id="aad15-119">*charcount*</span><span class="sxs-lookup"><span data-stu-id="aad15-119">*charcount*</span></span><br /><br /> <span data-ttu-id="aad15-120">*codepage*</span><span class="sxs-lookup"><span data-stu-id="aad15-120">*codepage*</span></span>|<span data-ttu-id="aad15-121">(DT_STR,30,1252) は、1252 コード ページを使用して、30 文字を DT_STR データ型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="aad15-121">(DT_STR,30,1252) casts 30 characters to the DT_STR data type using the 1252 code page.</span></span>|  
|<span data-ttu-id="aad15-122">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="aad15-122">DT_WSTR</span></span>|<span data-ttu-id="aad15-123">*charcount*</span><span class="sxs-lookup"><span data-stu-id="aad15-123">*charcount*</span></span>|<span data-ttu-id="aad15-124">(DT_WSTR,20) は、20 文字を DT_WSTR データ型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="aad15-124">(DT_WSTR,20) casts 20 characters to the DT_WSTR data type.</span></span>|  
|<span data-ttu-id="aad15-125">DT_BYTES</span><span class="sxs-lookup"><span data-stu-id="aad15-125">DT_BYTES</span></span>|<span data-ttu-id="aad15-126">*bytecount*</span><span class="sxs-lookup"><span data-stu-id="aad15-126">*bytecount*</span></span>|<span data-ttu-id="aad15-127">(DT_BYTES,50) は、50 バイトを DT_BYTES データ型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="aad15-127">(DT_BYTES,50) casts 50 bytes to the DT_BYTES data type.</span></span>|  
|<span data-ttu-id="aad15-128">DT_DECIMAL</span><span class="sxs-lookup"><span data-stu-id="aad15-128">DT_DECIMAL</span></span>|<span data-ttu-id="aad15-129">*scale*</span><span class="sxs-lookup"><span data-stu-id="aad15-129">*scale*</span></span>|<span data-ttu-id="aad15-130">(DT_DECIMAL,2) は、数値を小数点以下 2 桁の DT_DECIMAL データ型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="aad15-130">(DT_DECIMAL,2) casts a numeric value to the DT_DECIMAL data type using a scale of 2.</span></span>|  
|<span data-ttu-id="aad15-131">DT_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="aad15-131">DT_NUMERIC</span></span>|<span data-ttu-id="aad15-132">*有効桁数 (precision)*</span><span class="sxs-lookup"><span data-stu-id="aad15-132">*precision*</span></span><br /><br /> <span data-ttu-id="aad15-133">*scale*</span><span class="sxs-lookup"><span data-stu-id="aad15-133">*scale*</span></span>|<span data-ttu-id="aad15-134">(DT_NUMERIC,10,3) は、数値を有効桁数 10 桁で小数点以下 3 桁の DT_NUMERIC データ型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="aad15-134">(DT_NUMERIC,10,3) casts a numeric value to the DT_NUMERIC data type using a precision of 10 and a scale of 3.</span></span>|  
|<span data-ttu-id="aad15-135">DT_TEXT</span><span class="sxs-lookup"><span data-stu-id="aad15-135">DT_TEXT</span></span>|<span data-ttu-id="aad15-136">*codepage*</span><span class="sxs-lookup"><span data-stu-id="aad15-136">*codepage*</span></span>|<span data-ttu-id="aad15-137">(DT_TEXT,1252) は、1252 コード ページを使用して、値を DT_TEXT データ型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="aad15-137">(DT_TEXT,1252) casts a value to the DT_TEXT data type using the 1252 code page.</span></span>|  
  
## <a name="expression-examples"></a><span data-ttu-id="aad15-138">式の例</span><span class="sxs-lookup"><span data-stu-id="aad15-138">Expression Examples</span></span>  
 <span data-ttu-id="aad15-139">これらの例は、DT_STR、DT_DATE、および DT_BOOL データ型の NULL 値を返します。</span><span class="sxs-lookup"><span data-stu-id="aad15-139">These examples return the null value of the data types: DT_STR, DT_DATE, and DT_BOOL.</span></span>  
  
```  
NULL(DT_STR,10,1252)  
NULL(DT_DATE)  
NULL(DT_BOOL)  
```  
  
## <a name="see-also"></a><span data-ttu-id="aad15-140">参照</span><span class="sxs-lookup"><span data-stu-id="aad15-140">See Also</span></span>  
 <span data-ttu-id="aad15-141">[ISNULL &#40;SSIS 式&#41;](null-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="aad15-141">[ISNULL &#40;SSIS Expression&#41;](null-ssis-expression.md) </span></span>  
 [<span data-ttu-id="aad15-142">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="aad15-142">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
