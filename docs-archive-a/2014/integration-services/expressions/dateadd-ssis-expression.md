---
title: DATEADD (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], DATEADD
- dates [Integration Services]
- DATEADD function
ms.assetid: fa5c37b1-2ddc-4857-8f8e-f6d5643b654f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9feb288318bdf9705928cb930f175f5c170c384e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736637"
---
# <a name="dateadd-ssis-expression"></a><span data-ttu-id="adfc3-102">DATEADD (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="adfc3-102">DATEADD (SSIS Expression)</span></span>
  <span data-ttu-id="adfc3-103">指定された日付要素に、日付または期間を示す数値を加算して、新しい DT_DBTIMESTAMP の値を返します。</span><span class="sxs-lookup"><span data-stu-id="adfc3-103">Returns a new DT_DBTIMESTAMP value after adding a number that represents a date or time interval to the specified datepart in a date.</span></span> <span data-ttu-id="adfc3-104">数値のパラメーターは整数に、日付のパラメーターは有効な日付に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="adfc3-104">The number parameter must evaluate to an integer, and the date parameter must evaluate to a valid date.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adfc3-105">構文</span><span class="sxs-lookup"><span data-stu-id="adfc3-105">Syntax</span></span>  
  
```  
  
DATEADD(datepart, number, date)  
```  
  
## <a name="arguments"></a><span data-ttu-id="adfc3-106">引数</span><span class="sxs-lookup"><span data-stu-id="adfc3-106">Arguments</span></span>  
 <span data-ttu-id="adfc3-107">*datepart*</span><span class="sxs-lookup"><span data-stu-id="adfc3-107">*datepart*</span></span>  
 <span data-ttu-id="adfc3-108">日付の要素のうち、数値を追加する部分を指定するパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="adfc3-108">Is the parameter that specifies which part of the date to add a number to.</span></span>  
  
 <span data-ttu-id="adfc3-109">*number*</span><span class="sxs-lookup"><span data-stu-id="adfc3-109">*number*</span></span>  
 <span data-ttu-id="adfc3-110">*datepart*に加算される値です。</span><span class="sxs-lookup"><span data-stu-id="adfc3-110">Is the value used to increment *datepart*.</span></span> <span data-ttu-id="adfc3-111">式が解析される際、値は既知の整数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="adfc3-111">The value must be an integer value that is known when the expression is parsed.</span></span>  
  
 <span data-ttu-id="adfc3-112">*date*</span><span class="sxs-lookup"><span data-stu-id="adfc3-112">*date*</span></span>  
 <span data-ttu-id="adfc3-113">有効な日付または日付形式の文字列を返す式です。</span><span class="sxs-lookup"><span data-stu-id="adfc3-113">Is an expression that returns a valid date or a string in date format.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="adfc3-114">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="adfc3-114">Result Types</span></span>  
 <span data-ttu-id="adfc3-115">DT_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="adfc3-115">DT_DBTIMESTAMP</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="adfc3-116">解説</span><span class="sxs-lookup"><span data-stu-id="adfc3-116">Remarks</span></span>  
 <span data-ttu-id="adfc3-117">次の表に、式エバリュエーターで認識される日付要素 (datepart) と省略形を示します。</span><span class="sxs-lookup"><span data-stu-id="adfc3-117">The following table lists the dateparts and abbreviations recognized by the expression evaluator.</span></span> <span data-ttu-id="adfc3-118">日付要素の名前では大文字と小文字が区別されません。</span><span class="sxs-lookup"><span data-stu-id="adfc3-118">Datepart names are not case sensitive.</span></span>  
  
|<span data-ttu-id="adfc3-119">datepart</span><span class="sxs-lookup"><span data-stu-id="adfc3-119">Datepart</span></span>|<span data-ttu-id="adfc3-120">省略形</span><span class="sxs-lookup"><span data-stu-id="adfc3-120">Abbreviations</span></span>|  
|--------------|-------------------|  
|<span data-ttu-id="adfc3-121">年</span><span class="sxs-lookup"><span data-stu-id="adfc3-121">Year</span></span>|<span data-ttu-id="adfc3-122">yy、yyyy</span><span class="sxs-lookup"><span data-stu-id="adfc3-122">yy, yyyy</span></span>|  
|<span data-ttu-id="adfc3-123">Quarter</span><span class="sxs-lookup"><span data-stu-id="adfc3-123">Quarter</span></span>|<span data-ttu-id="adfc3-124">qq、q</span><span class="sxs-lookup"><span data-stu-id="adfc3-124">qq, q</span></span>|  
|<span data-ttu-id="adfc3-125">Month</span><span class="sxs-lookup"><span data-stu-id="adfc3-125">Month</span></span>|<span data-ttu-id="adfc3-126">mm、m</span><span class="sxs-lookup"><span data-stu-id="adfc3-126">mm, m</span></span>|  
|<span data-ttu-id="adfc3-127">Dayofyear</span><span class="sxs-lookup"><span data-stu-id="adfc3-127">Dayofyear</span></span>|<span data-ttu-id="adfc3-128">dy、y</span><span class="sxs-lookup"><span data-stu-id="adfc3-128">dy, y</span></span>|  
|<span data-ttu-id="adfc3-129">日</span><span class="sxs-lookup"><span data-stu-id="adfc3-129">Day</span></span>|<span data-ttu-id="adfc3-130">dd、d</span><span class="sxs-lookup"><span data-stu-id="adfc3-130">dd, d</span></span>|  
|<span data-ttu-id="adfc3-131">Week</span><span class="sxs-lookup"><span data-stu-id="adfc3-131">Week</span></span>|<span data-ttu-id="adfc3-132">wk、ww</span><span class="sxs-lookup"><span data-stu-id="adfc3-132">wk, ww</span></span>|  
|<span data-ttu-id="adfc3-133">平日</span><span class="sxs-lookup"><span data-stu-id="adfc3-133">Weekday</span></span>|<span data-ttu-id="adfc3-134">dw、w</span><span class="sxs-lookup"><span data-stu-id="adfc3-134">dw, w</span></span>|  
|<span data-ttu-id="adfc3-135">時</span><span class="sxs-lookup"><span data-stu-id="adfc3-135">Hour</span></span>|<span data-ttu-id="adfc3-136">Hh</span><span class="sxs-lookup"><span data-stu-id="adfc3-136">Hh</span></span>|  
|<span data-ttu-id="adfc3-137">分</span><span class="sxs-lookup"><span data-stu-id="adfc3-137">Minute</span></span>|<span data-ttu-id="adfc3-138">mi、n</span><span class="sxs-lookup"><span data-stu-id="adfc3-138">mi, n</span></span>|  
|<span data-ttu-id="adfc3-139">秒</span><span class="sxs-lookup"><span data-stu-id="adfc3-139">Second</span></span>|<span data-ttu-id="adfc3-140">ss、s</span><span class="sxs-lookup"><span data-stu-id="adfc3-140">ss, s</span></span>|  
|<span data-ttu-id="adfc3-141">Millisecond</span><span class="sxs-lookup"><span data-stu-id="adfc3-141">Millisecond</span></span>|<span data-ttu-id="adfc3-142">Ms</span><span class="sxs-lookup"><span data-stu-id="adfc3-142">Ms</span></span>|  
  
 <span data-ttu-id="adfc3-143">式が解析される際、 *number* 引数が使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="adfc3-143">The *number* argument must be available when the expression is parsed.</span></span> <span data-ttu-id="adfc3-144">引数には定数または変数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="adfc3-144">The argument can be a constant or a variable.</span></span> <span data-ttu-id="adfc3-145">式が解析される際に既知の値が提供されないため、列の値を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="adfc3-145">You cannot use column values because the values are not known when the expression is parsed.</span></span>  
  
 <span data-ttu-id="adfc3-146">*datepart* 引数は引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="adfc3-146">The *datepart* argument must be enclosed by quotation marks.</span></span>  
  
 <span data-ttu-id="adfc3-147">日付リテラルは、日付データ型のいずれかに明示的にキャストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="adfc3-147">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="adfc3-148">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="adfc3-148">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="adfc3-149">引数が NULL の場合、DATEADD は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="adfc3-149">DATEADD returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="adfc3-150">日付が無効の場合、日付または時間の単位が文字列でない場合、または増分が静的な整数でない場合は、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="adfc3-150">Errors occur if a date is invalid, if the date or time unit is not a string, or if the increment is not a static integer.</span></span>  
  
## <a name="ssis-expression-examples"></a><span data-ttu-id="adfc3-151">SSIS 式の例</span><span class="sxs-lookup"><span data-stu-id="adfc3-151">SSIS Expression Examples</span></span>  
 <span data-ttu-id="adfc3-152">この例では、現在の日付に 1 か月追加した値を返します。</span><span class="sxs-lookup"><span data-stu-id="adfc3-152">This example adds one month to the current date.</span></span>  
  
```  
DATEADD("Month", 1,GETDATE())  
```  
  
 <span data-ttu-id="adfc3-153">この例では、 **ModifiedDate** 列の日付に 21 日を追加します。</span><span class="sxs-lookup"><span data-stu-id="adfc3-153">This example adds 21 days to the dates in the **ModifiedDate** column.</span></span>  
  
```  
DATEADD("day", 21, ModifiedDate)  
```  
  
 <span data-ttu-id="adfc3-154">この例では、リテラルの日付に 2 年を追加します。</span><span class="sxs-lookup"><span data-stu-id="adfc3-154">This example adds 2 years to a literal date.</span></span>  
  
```  
DATEADD("yyyy", 2, (DT_DBTIMESTAMP)"8/6/2003")  
```  
  
## <a name="see-also"></a><span data-ttu-id="adfc3-155">参照</span><span class="sxs-lookup"><span data-stu-id="adfc3-155">See Also</span></span>  
 <span data-ttu-id="adfc3-156">[DATEDIFF &#40;SSIS 式&#41;](datediff-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="adfc3-156">[DATEDIFF &#40;SSIS Expression&#41;](datediff-ssis-expression.md) </span></span>  
 <span data-ttu-id="adfc3-157">[DATEPART &#40;SSIS 式&#41;](datepart-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="adfc3-157">[DATEPART &#40;SSIS Expression&#41;](datepart-ssis-expression.md) </span></span>  
 <span data-ttu-id="adfc3-158">[DAY &#40;SSIS 式&#41;](day-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="adfc3-158">[DAY &#40;SSIS Expression&#41;](day-ssis-expression.md) </span></span>  
 <span data-ttu-id="adfc3-159">[MONTH &#40;SSIS 式&#41;](month-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="adfc3-159">[MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) </span></span>  
 <span data-ttu-id="adfc3-160">[YEAR &#40;SSIS 式&#41;](year-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="adfc3-160">[YEAR &#40;SSIS Expression&#41;](year-ssis-expression.md) </span></span>  
 [<span data-ttu-id="adfc3-161">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="adfc3-161">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
