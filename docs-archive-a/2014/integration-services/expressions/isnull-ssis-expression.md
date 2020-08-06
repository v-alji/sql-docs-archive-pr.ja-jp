---
title: ISNULL (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- null values [Integration Services]
- ISNULL function
ms.assetid: 88dbf49e-1307-4dda-b9db-ff1632053550
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 51eda21b5c9b85c5f9cfd613d0d92df9729fe620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716509"
---
# <a name="isnull-ssis-expression"></a><span data-ttu-id="394ed-102">ISNULL (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="394ed-102">ISNULL (SSIS Expression)</span></span>
  <span data-ttu-id="394ed-103">式が NULL かどうかに基づいてブール型の結果を返します。</span><span class="sxs-lookup"><span data-stu-id="394ed-103">Returns a Boolean result based on whether an expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="394ed-104">構文</span><span class="sxs-lookup"><span data-stu-id="394ed-104">Syntax</span></span>  
  
```  
  
ISNULL(expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="394ed-105">引数</span><span class="sxs-lookup"><span data-stu-id="394ed-105">Arguments</span></span>  
 <span data-ttu-id="394ed-106">*式 (expression)*</span><span class="sxs-lookup"><span data-stu-id="394ed-106">*expression*</span></span>  
 <span data-ttu-id="394ed-107">任意のデータ型の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="394ed-107">Is a valid expression of any data type.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="394ed-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="394ed-108">Result Types</span></span>  
 <span data-ttu-id="394ed-109">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="394ed-109">DT_BOOL</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="394ed-110">式の例</span><span class="sxs-lookup"><span data-stu-id="394ed-110">Expression Examples</span></span>  
 <span data-ttu-id="394ed-111">この例では、 **DiscontinuedDate** 列に NULL 値が含まれる場合、TRUE を返します。</span><span class="sxs-lookup"><span data-stu-id="394ed-111">This example returns TRUE if the **DiscontinuedDate** column contains a null value.</span></span>  
  
```  
ISNULL(DiscontinuedDate)  
```  
  
 <span data-ttu-id="394ed-112">この例では、 **LastName** 列の値が NULL の場合、"Unknown last name" を返し、NULL でない場合は **LastName**の値を返します。</span><span class="sxs-lookup"><span data-stu-id="394ed-112">This example returns "Unknown last name" if the value in the **LastName** column is null, otherwise it returns the value in **LastName**.</span></span>  
  
```  
ISNULL(LastName)? "Unknown last name":LastName  
```  
  
 <span data-ttu-id="394ed-113">この例では、変数 **AddDays** の値に関係なく、 **DaysToManufacture**列が NULL の場合は常に TRUE を返します。</span><span class="sxs-lookup"><span data-stu-id="394ed-113">This example always returns TRUE if the **DaysToManufacture** column is null, regardless of the value of the variable **AddDays**.</span></span>  
  
```  
ISNULL(DaysToManufacture + @AddDays)  
```  
  
## <a name="see-also"></a><span data-ttu-id="394ed-114">参照</span><span class="sxs-lookup"><span data-stu-id="394ed-114">See Also</span></span>  
 <span data-ttu-id="394ed-115">[関数 &#40;SSIS 式&#41;](functions-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="394ed-115">[Functions &#40;SSIS Expression&#41;](functions-ssis-expression.md) </span></span>  
 [<span data-ttu-id="394ed-116">COALESCE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="394ed-116">COALESCE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/coalesce-transact-sql)  
  
  
