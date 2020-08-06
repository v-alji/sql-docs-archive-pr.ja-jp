---
title: GETDATE (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- current date
- GETDATE function
- dates [Integration Services], GETDATE
ms.assetid: 6d20ec93-3244-4d63-baf6-70eff7bd598c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0acb384a8c3c3dfdae55c7172f341f9e32765e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639565"
---
# <a name="getdate-ssis-expression"></a><span data-ttu-id="31307-102">GETDATE (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="31307-102">GETDATE (SSIS Expression)</span></span>
  <span data-ttu-id="31307-103">システムの現在の日付を、DT_DBTIMESTAMP 形式で返します。</span><span class="sxs-lookup"><span data-stu-id="31307-103">Returns the current date of the system in a DT_DBTIMESTAMP format.</span></span> <span data-ttu-id="31307-104">GETDATE 関数に引数はありません。</span><span class="sxs-lookup"><span data-stu-id="31307-104">The GETDATE function takes no arguments.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="31307-105">GETDATE 関数から返される結果の長さは 29 文字です。</span><span class="sxs-lookup"><span data-stu-id="31307-105">The length of the return result from the GETDATE function is 29 characters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31307-106">構文</span><span class="sxs-lookup"><span data-stu-id="31307-106">Syntax</span></span>  
  
```  
  
GETDATE()  
```  
  
## <a name="arguments"></a><span data-ttu-id="31307-107">引数</span><span class="sxs-lookup"><span data-stu-id="31307-107">Arguments</span></span>  
 <span data-ttu-id="31307-108">なし</span><span class="sxs-lookup"><span data-stu-id="31307-108">None</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="31307-109">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="31307-109">Result Types</span></span>  
 <span data-ttu-id="31307-110">DT_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="31307-110">DT_DBTIMESTAMP</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="31307-111">式の例</span><span class="sxs-lookup"><span data-stu-id="31307-111">Expression Examples</span></span>  
 <span data-ttu-id="31307-112">この例では、現在の日付の年が返されます。</span><span class="sxs-lookup"><span data-stu-id="31307-112">This example returns the year of the current date.</span></span>  
  
```  
DATEPART("year",GETDATE())  
```  
  
 <span data-ttu-id="31307-113">この例では、 **ModifiedDate** 列にある日付と現在の日付の間の日数が返されます。</span><span class="sxs-lookup"><span data-stu-id="31307-113">This example returns the number of days between a date in the **ModifiedDate** column and the current date.</span></span>  
  
```  
DATEDIFF("dd",ModifiedDate,GETDATE())  
```  
  
 <span data-ttu-id="31307-114">この例では、現在の日付に 3 か月追加した値が返されます。</span><span class="sxs-lookup"><span data-stu-id="31307-114">This example adds three months to the current date.</span></span>  
  
```  
DATEADD("Month",3,GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="31307-115">参照</span><span class="sxs-lookup"><span data-stu-id="31307-115">See Also</span></span>  
 <span data-ttu-id="31307-116">[GETUTCDATE (SSIS 式)](getutcdate-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="31307-116">[GETUTCDATE &#40;SSIS Expression&#41;](getutcdate-ssis-expression.md) </span></span>  
 [<span data-ttu-id="31307-117">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="31307-117">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
