---
title: GETUTCDATE (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], GETUTCDATE
- current date
- UTC time
- GETUTCDATE function
ms.assetid: 2282339c-c24f-493e-8e66-181ea8af5ad0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4f157ab5641e521a42cb3c96c96446b31de5dfa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716533"
---
# <a name="getutcdate-ssis-expression"></a><span data-ttu-id="5ea79-102">GETUTCDATE (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="5ea79-102">GETUTCDATE (SSIS Expression)</span></span>
  <span data-ttu-id="5ea79-103">システムの現在の日付を、DT_DBTIMESTAMP 形式を使用して UTC 時刻 (世界協定時またはグリニッジ標準時) で返します。</span><span class="sxs-lookup"><span data-stu-id="5ea79-103">Returns the current date of the system in UTC time (Universal Time Coordinate or Greenwich Mean Time) using a DT_DBTIMESTAMP format.</span></span> <span data-ttu-id="5ea79-104">GETUTCDATE 関数に引数はありません。</span><span class="sxs-lookup"><span data-stu-id="5ea79-104">The GETUTCDATE function takes no arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ea79-105">構文</span><span class="sxs-lookup"><span data-stu-id="5ea79-105">Syntax</span></span>  
  
```  
  
GETUTCDATE()  
```  
  
## <a name="arguments"></a><span data-ttu-id="5ea79-106">引数</span><span class="sxs-lookup"><span data-stu-id="5ea79-106">Arguments</span></span>  
 <span data-ttu-id="5ea79-107">なし</span><span class="sxs-lookup"><span data-stu-id="5ea79-107">None</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="5ea79-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="5ea79-108">Result Types</span></span>  
 <span data-ttu-id="5ea79-109">DT_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="5ea79-109">DT_DBTIMESTAMP</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="5ea79-110">式の例</span><span class="sxs-lookup"><span data-stu-id="5ea79-110">Expression Examples</span></span>  
 <span data-ttu-id="5ea79-111">この例では、現在の日付の年が UTC 時刻で返されます。</span><span class="sxs-lookup"><span data-stu-id="5ea79-111">This example returns the year of the current date in UTC time.</span></span>  
  
```  
DATEPART("year",GETUTCDATE())  
```  
  
 <span data-ttu-id="5ea79-112">この例では、 **ModifiedDate** 列にある日付と現在の UTC 日付の間の日数が返されます。</span><span class="sxs-lookup"><span data-stu-id="5ea79-112">This example returns the number of days between a date in the **ModifiedDate** column and the current UTC date.</span></span>  
  
```  
DATEDIFF("dd",ModifiedDate,GETUTCDATE())  
```  
  
 <span data-ttu-id="5ea79-113">この例では、現在の UTC 日付に 3 か月追加した値が返されます。</span><span class="sxs-lookup"><span data-stu-id="5ea79-113">This example adds three months to the current UTC date.</span></span>  
  
```  
DATEADD("Month",3,GETUTCDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ea79-114">参照</span><span class="sxs-lookup"><span data-stu-id="5ea79-114">See Also</span></span>  
 <span data-ttu-id="5ea79-115">[GETDATE (SSIS 式)](getdate-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="5ea79-115">[GETDATE &#40;SSIS Expression&#41;](getdate-ssis-expression.md) </span></span>  
 [<span data-ttu-id="5ea79-116">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="5ea79-116">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
