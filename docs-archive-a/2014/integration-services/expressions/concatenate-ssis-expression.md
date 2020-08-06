---
title: + (連結) (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- concatenation [Integration Services]
- + (concatenate operator)
- concatenate operator (+)
ms.assetid: 0fed6334-7a4f-42dc-a611-191fcaa0e443
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1c01f82a50962f42862db836171b0ad683c97453
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716545"
---
# <a name="-concatenate-ssis-expression"></a><span data-ttu-id="30c8e-102">+ (連結) (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="30c8e-102">+ (Concatenate) (SSIS Expression)</span></span>
  <span data-ttu-id="30c8e-103">2 つの式を連結して 1 つの式にします。</span><span class="sxs-lookup"><span data-stu-id="30c8e-103">Concatenates two expressions into one expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30c8e-104">構文</span><span class="sxs-lookup"><span data-stu-id="30c8e-104">Syntax</span></span>  
  
```  
  
character_expression1 + character_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="30c8e-105">引数</span><span class="sxs-lookup"><span data-stu-id="30c8e-105">Arguments</span></span>  
 <span data-ttu-id="30c8e-106">*expression1、expression2*</span><span class="sxs-lookup"><span data-stu-id="30c8e-106">*expression1, expression2*</span></span>  
 <span data-ttu-id="30c8e-107">データ型が DT_STR、DT_WSTR、DT_TEXT、DT_NTEXT、または DT_IMAGE である、任意の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="30c8e-107">Is any valid DT_STR, DT_WSTR, DT_TEXT, DT_NTEXT, or DT_IMAGE data type expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="30c8e-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="30c8e-108">Result Types</span></span>  
 <span data-ttu-id="30c8e-109">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="30c8e-109">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30c8e-110">解説</span><span class="sxs-lookup"><span data-stu-id="30c8e-110">Remarks</span></span>  
 <span data-ttu-id="30c8e-111">この式では、DT_STR データ型および DT_WSTR データ型のいずれか一方、または両方を使用できます。</span><span class="sxs-lookup"><span data-stu-id="30c8e-111">The expression can use either or both of the DT_STR and DT_WSTR data types.</span></span>  
  
 <span data-ttu-id="30c8e-112">DT_STR データ型と DT_WSTR データ型を連結すると、DT_WSTR データ型の結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="30c8e-112">The concatenation of the DT_STR and DT_WSTR data types returns a result of the DT_WSTR type.</span></span> <span data-ttu-id="30c8e-113">文字列の長さは、元の文字列の長さを文字数で表した値の合計です。</span><span class="sxs-lookup"><span data-stu-id="30c8e-113">The length of the string is the sum of the lengths of the original strings expressed in characters.</span></span>  
  
 <span data-ttu-id="30c8e-114">文字列データ型 DT_STR および DT_WSTR、または Binary Large Object Block (BLOB) データ型 DT_TEXT、DT_NTEXT、および DT_IMAGE のデータのみが連結できます。</span><span class="sxs-lookup"><span data-stu-id="30c8e-114">Only data with the string data types DT_STR and DT_WSTR or the Binary Large Object Block (BLOB) data types DT_TEXT, DT_NTEXT, and DT_IMAGE can be concatenated.</span></span> <span data-ttu-id="30c8e-115">その他のデータ型は、これらのデータ型のいずれかに明示的に変換してから連結する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30c8e-115">Other data types must be explicitly converted to one of these data types before concatenation occurs.</span></span> <span data-ttu-id="30c8e-116">データ型間の有効なキャストについて詳しくは、「[Cast &#40;SSIS 式&#41;](cast-ssis-expression.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="30c8e-116">For more information about legal casts between data types, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="30c8e-117">両方の式のデータ型は同じであるか、または一方の式をもう一方の式のデータ型に暗黙的に変換できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="30c8e-117">Both expressions must be of the same data type, or one expression must be implicitly convertible to the data type of the other expression.</span></span> <span data-ttu-id="30c8e-118">たとえば、文字列 "Order date is" と列 **OrderDate** を連結する場合、 **OrderDate** の値は暗黙的に文字列データ型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="30c8e-118">For example, if the string "Order date is " and the column **OrderDate** are concatenated, the values in **OrderDate** are implicitly converted to a string data type.</span></span> <span data-ttu-id="30c8e-119">2 つの数値を連結するには、両方の数値を文字列データ型に明示的にキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="30c8e-119">To concatenate two numeric values, both numeric values must be explicitly cast to a string data type.</span></span>  
  
 <span data-ttu-id="30c8e-120">BLOB データ型を連結する場合、DT_TEXT、DT_NTEXT、または DT_IMAGE のいずれか 1 つのみを連結できます。</span><span class="sxs-lookup"><span data-stu-id="30c8e-120">A concatenation can use only one BLOB data type: DT_TEXT, DT_NTEXT, or DT_IMAGE.</span></span>  
  
 <span data-ttu-id="30c8e-121">要素のいずれかが NULL の場合、結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="30c8e-121">If either element is null, the result is null.</span></span>  
  
 <span data-ttu-id="30c8e-122">文字列リテラルは引用符で囲まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="30c8e-122">String literals must be enclosed in quotation marks.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="30c8e-123">式の例</span><span class="sxs-lookup"><span data-stu-id="30c8e-123">Expression Examples</span></span>  
 <span data-ttu-id="30c8e-124">この例では、 **FirstName** 列と **LastName** 列の値を連結し、値の間にスペースを挿入します。</span><span class="sxs-lookup"><span data-stu-id="30c8e-124">This example concatenates the values in the **FirstName** and **LastName** columns and inserts a space between them.</span></span>  
  
```  
FirstName + ' ' + LastName  
```  
  
 <span data-ttu-id="30c8e-125">この例では、変数 **ZIPCode** と変数 **ZIPCode+4**を連結します。</span><span class="sxs-lookup"><span data-stu-id="30c8e-125">This example concatenates the variables **ZIPCode** and **ZIPCode+4**.</span></span> <span data-ttu-id="30c8e-126">どちらの変数も文字列データ型です。</span><span class="sxs-lookup"><span data-stu-id="30c8e-126">Both variables have a string data type.</span></span> <span data-ttu-id="30c8e-127">**ZIPCode+4** は、変数名にプラス記号 (+) が含まれているため、角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="30c8e-127">**ZIPCode+4** must be enclosed in brackets because the variable name includes the + character.</span></span>  
  
```  
@ZIPCcode + "-" + @[ZipCode+4]  
```  
  
## <a name="see-also"></a><span data-ttu-id="30c8e-128">参照</span><span class="sxs-lookup"><span data-stu-id="30c8e-128">See Also</span></span>  
 <span data-ttu-id="30c8e-129">[演算子の優先順位と結合規則](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="30c8e-129">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="30c8e-130">演算子 &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="30c8e-130">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
