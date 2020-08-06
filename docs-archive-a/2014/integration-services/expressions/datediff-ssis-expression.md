---
title: DATEDIFF (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- DATEDIFF statement
- dates [Integration Services], DATEDIFF
ms.assetid: 449b327f-47c7-4709-8bc6-4ee9a35cc330
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 33edf2a152f70bb8c5bbd1f69cb87354e099b246
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715601"
---
# <a name="datediff-ssis-expression"></a><span data-ttu-id="2fc4d-102">DATEDIFF (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="2fc4d-102">DATEDIFF (SSIS Expression)</span></span>
  <span data-ttu-id="2fc4d-103">指定された 2 つの日付間の差を、日付および時刻の単位で返します。</span><span class="sxs-lookup"><span data-stu-id="2fc4d-103">Returns the number of date and time boundaries crossed between two specified dates.</span></span> <span data-ttu-id="2fc4d-104">*datepart* パラメーターにより、差分を計算する基となる日付と時刻を指定します。</span><span class="sxs-lookup"><span data-stu-id="2fc4d-104">The *datepart* parameter identifies which date and time boundaries to compare.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fc4d-105">構文</span><span class="sxs-lookup"><span data-stu-id="2fc4d-105">Syntax</span></span>  
  
```  
  
DATEDIFF(datepart, startdate, endate)  
```  
  
## <a name="arguments"></a><span data-ttu-id="2fc4d-106">引数</span><span class="sxs-lookup"><span data-stu-id="2fc4d-106">Arguments</span></span>  
 <span data-ttu-id="2fc4d-107">*datepart*</span><span class="sxs-lookup"><span data-stu-id="2fc4d-107">*datepart*</span></span>  
 <span data-ttu-id="2fc4d-108">比較して値を返す日付の要素を指定するパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="2fc4d-108">Is the parameter that specifies which part of the date to compare and return a value for.</span></span>  
  
 <span data-ttu-id="2fc4d-109">*startdate*</span><span class="sxs-lookup"><span data-stu-id="2fc4d-109">*startdate*</span></span>  
 <span data-ttu-id="2fc4d-110">間隔の開始日です。</span><span class="sxs-lookup"><span data-stu-id="2fc4d-110">Is the start date of the interval.</span></span>  
  
 <span data-ttu-id="2fc4d-111">*endate*</span><span class="sxs-lookup"><span data-stu-id="2fc4d-111">*endate*</span></span>  
 <span data-ttu-id="2fc4d-112">間隔の終了日です。</span><span class="sxs-lookup"><span data-stu-id="2fc4d-112">Is the end date of the interval.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="2fc4d-113">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="2fc4d-113">Result Types</span></span>  
 <span data-ttu-id="2fc4d-114">DT_I4</span><span class="sxs-lookup"><span data-stu-id="2fc4d-114">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fc4d-115">解説</span><span class="sxs-lookup"><span data-stu-id="2fc4d-115">Remarks</span></span>  
 <span data-ttu-id="2fc4d-116">次の表に、式エバリュエーターで認識される日付要素 (datepart) と省略形を示します。</span><span class="sxs-lookup"><span data-stu-id="2fc4d-116">The following table lists the dateparts and abbreviations recognized by the expression evaluator.</span></span>  
  
|<span data-ttu-id="2fc4d-117">datepart</span><span class="sxs-lookup"><span data-stu-id="2fc4d-117">Datepart</span></span>|<span data-ttu-id="2fc4d-118">省略形</span><span class="sxs-lookup"><span data-stu-id="2fc4d-118">Abbreviations</span></span>|  
|--------------|-------------------|  
|<span data-ttu-id="2fc4d-119">年</span><span class="sxs-lookup"><span data-stu-id="2fc4d-119">Year</span></span>|<span data-ttu-id="2fc4d-120">yy、yyyy</span><span class="sxs-lookup"><span data-stu-id="2fc4d-120">yy, yyyy</span></span>|  
|<span data-ttu-id="2fc4d-121">Quarter</span><span class="sxs-lookup"><span data-stu-id="2fc4d-121">Quarter</span></span>|<span data-ttu-id="2fc4d-122">qq、q</span><span class="sxs-lookup"><span data-stu-id="2fc4d-122">qq, q</span></span>|  
|<span data-ttu-id="2fc4d-123">Month</span><span class="sxs-lookup"><span data-stu-id="2fc4d-123">Month</span></span>|<span data-ttu-id="2fc4d-124">mm、m</span><span class="sxs-lookup"><span data-stu-id="2fc4d-124">mm, m</span></span>|  
|<span data-ttu-id="2fc4d-125">Dayofyear</span><span class="sxs-lookup"><span data-stu-id="2fc4d-125">Dayofyear</span></span>|<span data-ttu-id="2fc4d-126">dy、y</span><span class="sxs-lookup"><span data-stu-id="2fc4d-126">dy, y</span></span>|  
|<span data-ttu-id="2fc4d-127">日</span><span class="sxs-lookup"><span data-stu-id="2fc4d-127">Day</span></span>|<span data-ttu-id="2fc4d-128">dd、d</span><span class="sxs-lookup"><span data-stu-id="2fc4d-128">dd, d</span></span>|  
|<span data-ttu-id="2fc4d-129">Week</span><span class="sxs-lookup"><span data-stu-id="2fc4d-129">Week</span></span>|<span data-ttu-id="2fc4d-130">wk、ww</span><span class="sxs-lookup"><span data-stu-id="2fc4d-130">wk, ww</span></span>|  
|<span data-ttu-id="2fc4d-131">平日</span><span class="sxs-lookup"><span data-stu-id="2fc4d-131">Weekday</span></span>|<span data-ttu-id="2fc4d-132">dw、w</span><span class="sxs-lookup"><span data-stu-id="2fc4d-132">dw, w</span></span>|  
|<span data-ttu-id="2fc4d-133">時</span><span class="sxs-lookup"><span data-stu-id="2fc4d-133">Hour</span></span>|<span data-ttu-id="2fc4d-134">Hh</span><span class="sxs-lookup"><span data-stu-id="2fc4d-134">Hh</span></span>|  
|<span data-ttu-id="2fc4d-135">分</span><span class="sxs-lookup"><span data-stu-id="2fc4d-135">Minute</span></span>|<span data-ttu-id="2fc4d-136">mi、n</span><span class="sxs-lookup"><span data-stu-id="2fc4d-136">mi, n</span></span>|  
|<span data-ttu-id="2fc4d-137">秒</span><span class="sxs-lookup"><span data-stu-id="2fc4d-137">Second</span></span>|<span data-ttu-id="2fc4d-138">ss、s</span><span class="sxs-lookup"><span data-stu-id="2fc4d-138">ss, s</span></span>|  
|<span data-ttu-id="2fc4d-139">Millisecond</span><span class="sxs-lookup"><span data-stu-id="2fc4d-139">Millisecond</span></span>|<span data-ttu-id="2fc4d-140">Ms</span><span class="sxs-lookup"><span data-stu-id="2fc4d-140">Ms</span></span>|  
  
 <span data-ttu-id="2fc4d-141">引数のいずれかが NULL の場合、DATEDIFF は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="2fc4d-141">DATEDIFF returns a null result if any argument is null.</span></span>  
  
 <span data-ttu-id="2fc4d-142">日付リテラルは、日付データ型のいずれかに明示的にキャストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="2fc4d-142">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="2fc4d-143">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fc4d-143">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="2fc4d-144">日付が有効でない場合、日付または時刻の単位が文字列でない場合、開始日が日付でない場合、または終了日が日付でない場合は、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="2fc4d-144">An error occurs if a date is not valid, if the date or time unit is not a string, if the start date is not a date, or if the end date is not a date.</span></span>  
  
 <span data-ttu-id="2fc4d-145">終了日が開始日よりも前の日付の場合、この関数は負の値を返します。</span><span class="sxs-lookup"><span data-stu-id="2fc4d-145">If the end date is earlier than the start date, the function returns a negative number.</span></span> <span data-ttu-id="2fc4d-146">開始日と終了日の日付が同一、または同じ間隔の範囲内である場合、この関数は 0 を返します。</span><span class="sxs-lookup"><span data-stu-id="2fc4d-146">If the start and end dates are equal or fall within the same interval, the function returns zero.</span></span>  
  
## <a name="ssis-expression-examples"></a><span data-ttu-id="2fc4d-147">SSIS 式の例</span><span class="sxs-lookup"><span data-stu-id="2fc4d-147">SSIS Expression Examples</span></span>  
 <span data-ttu-id="2fc4d-148">この例では、2 つの日付リテラル間の日数が計算されます。</span><span class="sxs-lookup"><span data-stu-id="2fc4d-148">This example calculates the number of days between two date literals.</span></span> <span data-ttu-id="2fc4d-149">日付が "mm/dd/yyyy" 形式の場合、7 が返されます。</span><span class="sxs-lookup"><span data-stu-id="2fc4d-149">If the date is in "mm/dd/yyyy" format, the function returns 7.</span></span>  
  
```  
DATEDIFF("dd", (DT_DBTIMESTAMP)"8/1/2003", (DT_DBTIMESTAMP)"8/8/2003")  
```  
  
 <span data-ttu-id="2fc4d-150">この例では、日付リテラルと現在の日付の間の月数が返されます。</span><span class="sxs-lookup"><span data-stu-id="2fc4d-150">This example returns the number of months between a date literal and the current date.</span></span>  
  
```  
DATEDIFF("mm", (DT_DBTIMESTAMP)"8/1/2003",GETDATE())  
```  
  
 <span data-ttu-id="2fc4d-151">この例では、 **ModifiedDate** 列の日付と、 **YearEndDate** 変数の日付の間の週数が返されます。</span><span class="sxs-lookup"><span data-stu-id="2fc4d-151">This example returns the number of weeks between the date in the **ModifiedDate** column and the **YearEndDate** variable.</span></span> <span data-ttu-id="2fc4d-152">**YearEndDate**にデータ型がある場合は `date` 、明示的なキャストは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="2fc4d-152">If **YearEndDate** has a `date` data type, no explicit casting is required.</span></span>  
  
```  
DATEDIFF("Week", ModifiedDate,@YearEndDate)  
```  
  
## <a name="see-also"></a><span data-ttu-id="2fc4d-153">参照</span><span class="sxs-lookup"><span data-stu-id="2fc4d-153">See Also</span></span>  
 <span data-ttu-id="2fc4d-154">[DATEADD &#40;SSIS 式&#41;](dateadd-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="2fc4d-154">[DATEADD &#40;SSIS Expression&#41;](dateadd-ssis-expression.md) </span></span>  
 <span data-ttu-id="2fc4d-155">[DATEPART &#40;SSIS 式&#41;](datepart-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="2fc4d-155">[DATEPART &#40;SSIS Expression&#41;](datepart-ssis-expression.md) </span></span>  
 <span data-ttu-id="2fc4d-156">[DAY &#40;SSIS 式&#41;](day-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="2fc4d-156">[DAY &#40;SSIS Expression&#41;](day-ssis-expression.md) </span></span>  
 <span data-ttu-id="2fc4d-157">[MONTH &#40;SSIS 式&#41;](month-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="2fc4d-157">[MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) </span></span>  
 <span data-ttu-id="2fc4d-158">[YEAR &#40;SSIS 式&#41;](year-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="2fc4d-158">[YEAR &#40;SSIS Expression&#41;](year-ssis-expression.md) </span></span>  
 [<span data-ttu-id="2fc4d-159">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="2fc4d-159">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
