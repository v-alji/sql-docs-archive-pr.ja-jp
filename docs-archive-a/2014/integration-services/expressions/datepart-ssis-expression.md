---
title: DATEPART (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], DATEPART
- DATEPART function
ms.assetid: 3e590094-fc49-4144-805f-fdc1bf2fe509
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8aed7146c74c6738ba979f422bd65b7e1b539e15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715597"
---
# <a name="datepart-ssis-expression"></a><span data-ttu-id="ef60f-102">DATEPART (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="ef60f-102">DATEPART (SSIS Expression)</span></span>
  <span data-ttu-id="ef60f-103">ある日付の、特定の日付要素を整数で返します。</span><span class="sxs-lookup"><span data-stu-id="ef60f-103">Returns an integer representing a datepart of a date.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef60f-104">構文</span><span class="sxs-lookup"><span data-stu-id="ef60f-104">Syntax</span></span>  
  
```  
  
DATEPART(datepart, date)  
```  
  
## <a name="arguments"></a><span data-ttu-id="ef60f-105">引数</span><span class="sxs-lookup"><span data-stu-id="ef60f-105">Arguments</span></span>  
 <span data-ttu-id="ef60f-106">*datepart*</span><span class="sxs-lookup"><span data-stu-id="ef60f-106">*datepart*</span></span>  
 <span data-ttu-id="ef60f-107">新しい値を返す日付の要素を指定するパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="ef60f-107">Is the parameter that specifies for which part of the date to return a new value.</span></span>  
  
 <span data-ttu-id="ef60f-108">*date*</span><span class="sxs-lookup"><span data-stu-id="ef60f-108">*date*</span></span>  
 <span data-ttu-id="ef60f-109">有効な日付または日付形式の文字列を返す式です。</span><span class="sxs-lookup"><span data-stu-id="ef60f-109">Is an expression that returns a valid date or a string in date format.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="ef60f-110">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="ef60f-110">Result Types</span></span>  
 <span data-ttu-id="ef60f-111">DT_I4</span><span class="sxs-lookup"><span data-stu-id="ef60f-111">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef60f-112">解説</span><span class="sxs-lookup"><span data-stu-id="ef60f-112">Remarks</span></span>  
 <span data-ttu-id="ef60f-113">引数が NULL の場合、DATEPART は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="ef60f-113">DATEPART returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="ef60f-114">日付リテラルは、日付データ型のいずれかに明示的にキャストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef60f-114">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="ef60f-115">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef60f-115">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="ef60f-116">次の表に、式エバリュエーターで認識される日付要素 (datepart) と省略形を示します。</span><span class="sxs-lookup"><span data-stu-id="ef60f-116">The following table lists the dateparts and abbreviations recognized by the expression evaluator.</span></span> <span data-ttu-id="ef60f-117">日付要素の名前では大文字と小文字が区別されません。</span><span class="sxs-lookup"><span data-stu-id="ef60f-117">Datepart names are not case sensitive.</span></span>  
  
|<span data-ttu-id="ef60f-118">datepart</span><span class="sxs-lookup"><span data-stu-id="ef60f-118">Datepart</span></span>|<span data-ttu-id="ef60f-119">省略形</span><span class="sxs-lookup"><span data-stu-id="ef60f-119">Abbreviations</span></span>|  
|--------------|-------------------|  
|<span data-ttu-id="ef60f-120">年</span><span class="sxs-lookup"><span data-stu-id="ef60f-120">Year</span></span>|<span data-ttu-id="ef60f-121">yy、yyyy</span><span class="sxs-lookup"><span data-stu-id="ef60f-121">yy, yyyy</span></span>|  
|<span data-ttu-id="ef60f-122">Quarter</span><span class="sxs-lookup"><span data-stu-id="ef60f-122">Quarter</span></span>|<span data-ttu-id="ef60f-123">qq、q</span><span class="sxs-lookup"><span data-stu-id="ef60f-123">qq, q</span></span>|  
|<span data-ttu-id="ef60f-124">Month</span><span class="sxs-lookup"><span data-stu-id="ef60f-124">Month</span></span>|<span data-ttu-id="ef60f-125">mm、m</span><span class="sxs-lookup"><span data-stu-id="ef60f-125">mm, m</span></span>|  
|<span data-ttu-id="ef60f-126">Dayofyear</span><span class="sxs-lookup"><span data-stu-id="ef60f-126">Dayofyear</span></span>|<span data-ttu-id="ef60f-127">dy、y</span><span class="sxs-lookup"><span data-stu-id="ef60f-127">dy, y</span></span>|  
|<span data-ttu-id="ef60f-128">日</span><span class="sxs-lookup"><span data-stu-id="ef60f-128">Day</span></span>|<span data-ttu-id="ef60f-129">dd、d</span><span class="sxs-lookup"><span data-stu-id="ef60f-129">dd, d</span></span>|  
|<span data-ttu-id="ef60f-130">Week</span><span class="sxs-lookup"><span data-stu-id="ef60f-130">Week</span></span>|<span data-ttu-id="ef60f-131">wk、ww</span><span class="sxs-lookup"><span data-stu-id="ef60f-131">wk, ww</span></span>|  
|<span data-ttu-id="ef60f-132">平日</span><span class="sxs-lookup"><span data-stu-id="ef60f-132">Weekday</span></span>|<span data-ttu-id="ef60f-133">dw</span><span class="sxs-lookup"><span data-stu-id="ef60f-133">dw</span></span>|  
|<span data-ttu-id="ef60f-134">時</span><span class="sxs-lookup"><span data-stu-id="ef60f-134">Hour</span></span>|<span data-ttu-id="ef60f-135">Hh</span><span class="sxs-lookup"><span data-stu-id="ef60f-135">Hh</span></span>|  
|<span data-ttu-id="ef60f-136">分</span><span class="sxs-lookup"><span data-stu-id="ef60f-136">Minute</span></span>|<span data-ttu-id="ef60f-137">mi、n</span><span class="sxs-lookup"><span data-stu-id="ef60f-137">mi, n</span></span>|  
|<span data-ttu-id="ef60f-138">秒</span><span class="sxs-lookup"><span data-stu-id="ef60f-138">Second</span></span>|<span data-ttu-id="ef60f-139">ss、s</span><span class="sxs-lookup"><span data-stu-id="ef60f-139">ss, s</span></span>|  
|<span data-ttu-id="ef60f-140">Millisecond</span><span class="sxs-lookup"><span data-stu-id="ef60f-140">Millisecond</span></span>|<span data-ttu-id="ef60f-141">Ms</span><span class="sxs-lookup"><span data-stu-id="ef60f-141">Ms</span></span>|  
  
## <a name="ssis-expression-examples"></a><span data-ttu-id="ef60f-142">SSIS 式の例</span><span class="sxs-lookup"><span data-stu-id="ef60f-142">SSIS Expression Examples</span></span>  
 <span data-ttu-id="ef60f-143">この例では、日付リテラル内の月を表す整数が返されます。</span><span class="sxs-lookup"><span data-stu-id="ef60f-143">This example returns the integer that represents the month in a date literal.</span></span> <span data-ttu-id="ef60f-144">データが mm/dd/yyyy 形式の場合、この例では 11 が返されます。</span><span class="sxs-lookup"><span data-stu-id="ef60f-144">If the date is in mm/dd/yyyy" format, this example returns 11.</span></span>  
  
```  
DATEPART("month", (DT_DBTIMESTAMP)"11/04/2002")  
```  
  
 <span data-ttu-id="ef60f-145">この例は、 **ModifiedDate** 列内の日を表す整数を返します。</span><span class="sxs-lookup"><span data-stu-id="ef60f-145">This example returns the integer that represents the day in the **ModifiedDate** column.</span></span>  
  
```  
DATEPART("dd", ModifiedDate)  
```  
  
 <span data-ttu-id="ef60f-146">この例では、現在の日付の年を表す整数が返されます。</span><span class="sxs-lookup"><span data-stu-id="ef60f-146">This example returns the integer that represents the year of the current date.</span></span>  
  
```  
DATEPART("yy",GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef60f-147">参照</span><span class="sxs-lookup"><span data-stu-id="ef60f-147">See Also</span></span>  
 <span data-ttu-id="ef60f-148">[DATEADD &#40;SSIS 式&#41;](dateadd-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="ef60f-148">[DATEADD &#40;SSIS Expression&#41;](dateadd-ssis-expression.md) </span></span>  
 <span data-ttu-id="ef60f-149">[DATEDIFF &#40;SSIS 式&#41;](datediff-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="ef60f-149">[DATEDIFF &#40;SSIS Expression&#41;](datediff-ssis-expression.md) </span></span>  
 <span data-ttu-id="ef60f-150">[DAY &#40;SSIS 式&#41;](day-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="ef60f-150">[DAY &#40;SSIS Expression&#41;](day-ssis-expression.md) </span></span>  
 <span data-ttu-id="ef60f-151">[MONTH &#40;SSIS 式&#41;](month-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="ef60f-151">[MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) </span></span>  
 <span data-ttu-id="ef60f-152">[YEAR &#40;SSIS 式&#41;](year-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="ef60f-152">[YEAR &#40;SSIS Expression&#41;](year-ssis-expression.md) </span></span>  
 [<span data-ttu-id="ef60f-153">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="ef60f-153">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
