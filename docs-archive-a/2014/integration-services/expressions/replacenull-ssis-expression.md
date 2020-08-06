---
title: REPLACENULL (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 70db7832-b5a0-4db5-a8ad-42ad8630d8e8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f10bb6ef6102076fe7b1cc236461e2358ad96372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716501"
---
# <a name="replacenull-ssis-expression"></a><span data-ttu-id="9a388-102">REPLACENULL (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="9a388-102">REPLACENULL (SSIS Expression)</span></span>
  <span data-ttu-id="9a388-103">1 番目の式パラメーターの値が NULL の場合、2 番目の式パラメーターの値を返します。NULL でない場合は、1 番目の式の値を返します。</span><span class="sxs-lookup"><span data-stu-id="9a388-103">Returns the value of second expression parameter if the value of first expression parameter is NULL; otherwise, returns the value of first expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a388-104">構文</span><span class="sxs-lookup"><span data-stu-id="9a388-104">Syntax</span></span>  
  
```vb  
REPLACENULL(expression 1,expression 2)  
```  
  
## <a name="arguments"></a><span data-ttu-id="9a388-105">引数</span><span class="sxs-lookup"><span data-stu-id="9a388-105">Arguments</span></span>  
 <span data-ttu-id="9a388-106">*expression 1*</span><span class="sxs-lookup"><span data-stu-id="9a388-106">*expression 1*</span></span>  
 <span data-ttu-id="9a388-107">この式の結果が NULL かどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="9a388-107">The result of this expression is checked against NULL.</span></span>  
  
 <span data-ttu-id="9a388-108">*expression 2*</span><span class="sxs-lookup"><span data-stu-id="9a388-108">*expression 2*</span></span>  
 <span data-ttu-id="9a388-109">1 番目の式が NULL と評価される場合、この式の結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="9a388-109">The result of this expression is returned if the first expression evaluates to NULL.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9a388-110">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="9a388-110">Result Types</span></span>  
 <span data-ttu-id="9a388-111">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="9a388-111">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a388-112">解説</span><span class="sxs-lookup"><span data-stu-id="9a388-112">Remarks</span></span>  
  
-   <span data-ttu-id="9a388-113">*expression 2* の長さは 0 にできます。</span><span class="sxs-lookup"><span data-stu-id="9a388-113">The length of *expression 2* may be zero.</span></span>  
  
-   <span data-ttu-id="9a388-114">いずれかの引数が NULL の場合、REPLACENULL は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="9a388-114">REPLACENULL returns a null result if any argument is null.</span></span>  
  
-   <span data-ttu-id="9a388-115">BLOB 列 (DT_TEXT、DT_NTEXT、DT_IMAGE) は、いずれのパラメーターとしてもサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9a388-115">BLOB columns (DT_TEXT, DT_NTEXT, DT_IMAGE) are not supported for either parameter.</span></span>  
  
-   <span data-ttu-id="9a388-116">2 つの式は、戻り値の型が同じであるものと想定されています。</span><span class="sxs-lookup"><span data-stu-id="9a388-116">The two expressions are expected to have the same return type.</span></span> <span data-ttu-id="9a388-117">同じでない場合は、2 番目の式が 1 番目の式の戻り値の型にキャストされ、データ型に互換性がない場合はエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9a388-117">If they do not, the function attempts to cast the 2nd expression to the return type of the 1st expression, which may result in an error if the data types are incompatible.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="9a388-118">式の例</span><span class="sxs-lookup"><span data-stu-id="9a388-118">Expression Examples</span></span>  
 <span data-ttu-id="9a388-119">次の例では、データベース列の NULL 値を、文字列 (1900-01-01) に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="9a388-119">The following example replaces any NULL value in a database column with a string (1900-01-01).</span></span> <span data-ttu-id="9a388-120">この関数は、特に、NULL 値を他のなんらかの値に置き換える必要のある一般的な派生列パターンで使用されます。</span><span class="sxs-lookup"><span data-stu-id="9a388-120">This function is especially used in common Derived Column patterns where you want to replace NULL values with something else.</span></span>  
  
```  
REPLACENULL(MyColumn, "1900-01-01")  
```  
  
> [!NOTE]  
>  <span data-ttu-id="9a388-121">次の例では、 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]/[!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]で行われていた方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9a388-121">The following example shows how it was done in [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]/[!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)].</span></span>  
  
```  
(DT_DBTIMESTAMP) (ISNULL(MyColumn) ? "1900-01-01" : MyColumn)   
```  
  
  
