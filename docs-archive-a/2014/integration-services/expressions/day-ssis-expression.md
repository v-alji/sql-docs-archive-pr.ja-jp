---
title: DAY (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- DAY function
- dates [Integration Services], DAY
ms.assetid: d8447187-49df-45b7-a98e-142ad44fd3e2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b7acac3f3949cbbd07adbe6382ea3d875f94cb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715593"
---
# <a name="day-ssis-expression"></a><span data-ttu-id="38148-102">DAY (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="38148-102">DAY (SSIS Expression)</span></span>
  <span data-ttu-id="38148-103">ある日付の、日の日付要素を表す整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="38148-103">Returns an integer that represents the day datepart of a date.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38148-104">構文</span><span class="sxs-lookup"><span data-stu-id="38148-104">Syntax</span></span>  
  
```  
  
DAY(date)  
```  
  
## <a name="arguments"></a><span data-ttu-id="38148-105">引数</span><span class="sxs-lookup"><span data-stu-id="38148-105">Arguments</span></span>  
 <span data-ttu-id="38148-106">*date*</span><span class="sxs-lookup"><span data-stu-id="38148-106">*date*</span></span>  
 <span data-ttu-id="38148-107">有効な日付または日付形式の文字列を返す式です。</span><span class="sxs-lookup"><span data-stu-id="38148-107">Is an expression that returns a valid date or a string in date format.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="38148-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="38148-108">Result Types</span></span>  
 <span data-ttu-id="38148-109">DT_I4</span><span class="sxs-lookup"><span data-stu-id="38148-109">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38148-110">解説</span><span class="sxs-lookup"><span data-stu-id="38148-110">Remarks</span></span>  
 <span data-ttu-id="38148-111">引数が NULL の場合、DAY は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="38148-111">DAY returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="38148-112">日付リテラルは、日付データ型のいずれかに明示的にキャストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="38148-112">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="38148-113">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38148-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="38148-114">日付リテラルが DT_DBTIMESTAMPOFFSET と DT_DBTIMESTAMP2 のいずれかの日付データ型に明示的にキャストされると、式の検証は失敗します。</span><span class="sxs-lookup"><span data-stu-id="38148-114">The expression fails to validate when a date literal is explicitly cast to one of these date data types: DT_DBTIMESTAMPOFFSET and DT_DBTIMESTAMP2.</span></span>  
  
 <span data-ttu-id="38148-115">DAY 関数を使用すると、DATEPART("DAY", date) 関数を使用する場合と同じ結果を、より簡単に取得できます。</span><span class="sxs-lookup"><span data-stu-id="38148-115">Using the DAY function is briefer but equivalent to using DATEPART("Day", date).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="38148-116">式の例</span><span class="sxs-lookup"><span data-stu-id="38148-116">Expression Examples</span></span>  
 <span data-ttu-id="38148-117">この例は、日付リテラルの日数を返します。</span><span class="sxs-lookup"><span data-stu-id="38148-117">This example returns the number of the day in a date literal.</span></span> <span data-ttu-id="38148-118">データ形式が "mm/dd/yyyy" 形式の場合、この例は 23 を返します。</span><span class="sxs-lookup"><span data-stu-id="38148-118">If the date format is in "mm/dd/yyyy" format, this example returns 23.</span></span>  
  
```  
DAY((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 <span data-ttu-id="38148-119">この例は、 **ModifiedDate** 列内の日を表す整数を返します。</span><span class="sxs-lookup"><span data-stu-id="38148-119">This example returns the integer that represents the day in the **ModifiedDate** column.</span></span>  
  
```  
DAY(ModifiedDate)  
```  
  
 <span data-ttu-id="38148-120">この例は、現在の日付の日を表す整数を返します。</span><span class="sxs-lookup"><span data-stu-id="38148-120">This example returns the integer that represents the day of the current date.</span></span>  
  
```  
DAY(GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="38148-121">参照</span><span class="sxs-lookup"><span data-stu-id="38148-121">See Also</span></span>  
 <span data-ttu-id="38148-122">[DATEADD &#40;SSIS 式&#41;](dateadd-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="38148-122">[DATEADD &#40;SSIS Expression&#41;](dateadd-ssis-expression.md) </span></span>  
 <span data-ttu-id="38148-123">[DATEDIFF &#40;SSIS 式&#41;](datediff-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="38148-123">[DATEDIFF &#40;SSIS Expression&#41;](datediff-ssis-expression.md) </span></span>  
 <span data-ttu-id="38148-124">[DATEPART &#40;SSIS 式&#41;](datepart-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="38148-124">[DATEPART &#40;SSIS Expression&#41;](datepart-ssis-expression.md) </span></span>  
 <span data-ttu-id="38148-125">[MONTH &#40;SSIS 式&#41;](month-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="38148-125">[MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) </span></span>  
 <span data-ttu-id="38148-126">[YEAR &#40;SSIS 式&#41;](year-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="38148-126">[YEAR &#40;SSIS Expression&#41;](year-ssis-expression.md) </span></span>  
 [<span data-ttu-id="38148-127">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="38148-127">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
