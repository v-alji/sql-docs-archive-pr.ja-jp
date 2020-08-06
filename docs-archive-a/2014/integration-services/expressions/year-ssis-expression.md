---
title: YEAR (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], YEAR
- YEAR function
ms.assetid: 9d88dead-ace8-44b9-b8e2-916c1842e155
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 181375d489fbf7abf0718386efacf4167ba555d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643462"
---
# <a name="year-ssis-expression"></a><span data-ttu-id="dd51c-102">YEAR (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="dd51c-102">YEAR (SSIS Expression)</span></span>
  <span data-ttu-id="dd51c-103">ある日付の、年の日付要素を表す整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="dd51c-103">Returns an integer that represents the year datepart of a date.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd51c-104">構文</span><span class="sxs-lookup"><span data-stu-id="dd51c-104">Syntax</span></span>  
  
```  
  
YEAR(date)  
```  
  
## <a name="arguments"></a><span data-ttu-id="dd51c-105">引数</span><span class="sxs-lookup"><span data-stu-id="dd51c-105">Arguments</span></span>  
 <span data-ttu-id="dd51c-106">*date*</span><span class="sxs-lookup"><span data-stu-id="dd51c-106">*date*</span></span>  
 <span data-ttu-id="dd51c-107">任意の日付形式の日付です。</span><span class="sxs-lookup"><span data-stu-id="dd51c-107">Is a date in any date format.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="dd51c-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="dd51c-108">Result Types</span></span>  
 <span data-ttu-id="dd51c-109">DT_I4</span><span class="sxs-lookup"><span data-stu-id="dd51c-109">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd51c-110">解説</span><span class="sxs-lookup"><span data-stu-id="dd51c-110">Remarks</span></span>  
 <span data-ttu-id="dd51c-111">引数が NULL の場合、YEAR は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="dd51c-111">YEAR returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="dd51c-112">日付リテラルは、日付データ型のいずれかに明示的にキャストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd51c-112">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="dd51c-113">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd51c-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dd51c-114">日付リテラルが DT_DBTIMESTAMPOFFSET と DT_DBTIMESTAMP2 のいずれかの日付データ型に明示的にキャストされると、式の検証は失敗します。</span><span class="sxs-lookup"><span data-stu-id="dd51c-114">The expression fails to validate when a date literal is explicitly cast to one of these date data types: DT_DBTIMESTAMPOFFSET and DT_DBTIMESTAMP2.</span></span>  
  
 <span data-ttu-id="dd51c-115">YEAR 関数を使用すると、DATEPART("Year", date) 関数を使用する場合と同じ結果を、より簡単に取得できます。</span><span class="sxs-lookup"><span data-stu-id="dd51c-115">Using the YEAR function is briefer but equivalent to using the DATEPART("Year", date) function.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="dd51c-116">式の例</span><span class="sxs-lookup"><span data-stu-id="dd51c-116">Expression Examples</span></span>  
 <span data-ttu-id="dd51c-117">この例では、日付リテラルの年を表す数値が返されます。</span><span class="sxs-lookup"><span data-stu-id="dd51c-117">This example returns the number of the year in a date literal.</span></span> <span data-ttu-id="dd51c-118">データが mm/dd/yyyy 形式の場合、この例では "2002" が返されます。</span><span class="sxs-lookup"><span data-stu-id="dd51c-118">If the date is in mm/dd/yyyy format, this example returns "2002".</span></span>  
  
```  
YEAR((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 <span data-ttu-id="dd51c-119">この例では、 **ModifiedDate** 列内の年を表す整数が返されます。</span><span class="sxs-lookup"><span data-stu-id="dd51c-119">This example returns the integer that represents the year in the **ModifiedDate** column.</span></span>  
  
```  
YEAR(ModifiedDate)  
```  
  
 <span data-ttu-id="dd51c-120">この例では、現在の日付の年を表す整数が返されます。</span><span class="sxs-lookup"><span data-stu-id="dd51c-120">This example returns the integer that represents the year of the current date.</span></span>  
  
```  
YEAR(GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd51c-121">参照</span><span class="sxs-lookup"><span data-stu-id="dd51c-121">See Also</span></span>  
 <span data-ttu-id="dd51c-122">[DATEADD &#40;SSIS 式&#41;](dateadd-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="dd51c-122">[DATEADD &#40;SSIS Expression&#41;](dateadd-ssis-expression.md) </span></span>  
 <span data-ttu-id="dd51c-123">[DATEDIFF &#40;SSIS 式&#41;](datediff-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="dd51c-123">[DATEDIFF &#40;SSIS Expression&#41;](datediff-ssis-expression.md) </span></span>  
 <span data-ttu-id="dd51c-124">[DATEPART &#40;SSIS 式&#41;](datepart-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="dd51c-124">[DATEPART &#40;SSIS Expression&#41;](datepart-ssis-expression.md) </span></span>  
 <span data-ttu-id="dd51c-125">[DAY &#40;SSIS 式&#41;](day-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="dd51c-125">[DAY &#40;SSIS Expression&#41;](day-ssis-expression.md) </span></span>  
 <span data-ttu-id="dd51c-126">[MONTH &#40;SSIS 式&#41;](month-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="dd51c-126">[MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) </span></span>  
 [<span data-ttu-id="dd51c-127">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="dd51c-127">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
