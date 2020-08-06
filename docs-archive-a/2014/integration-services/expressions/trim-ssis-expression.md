---
title: TRIM (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- leading blanks
- TRIM function
- trailing blanks
ms.assetid: 7dd9081d-a3d4-483a-bf7e-bf2bd7692d39
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 42cef8a816f399e39ac99061f34c394156bde45f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716441"
---
# <a name="trim-ssis-expression"></a><span data-ttu-id="9c594-102">TRIM (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="9c594-102">TRIM (SSIS Expression)</span></span>
  <span data-ttu-id="9c594-103">先頭および末尾のスペースを削除した後の文字式を返します。</span><span class="sxs-lookup"><span data-stu-id="9c594-103">Returns a character expression after removing leading and trailing spaces.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9c594-104">TRIM では、タブや改行文字などの空白文字は削除されません。</span><span class="sxs-lookup"><span data-stu-id="9c594-104">TRIM does not remove white-space characters such as the tab or line feed characters.</span></span> <span data-ttu-id="9c594-105">Unicode には各種スペースを表すコード ポイントが用意されていますが、この関数では Unicode コード ポイント 0x0020 のみが認識されます。</span><span class="sxs-lookup"><span data-stu-id="9c594-105">Unicode provides code points for many different types of spaces, but this function recognizes only the Unicode code point 0x0020.</span></span> <span data-ttu-id="9c594-106">Unicode に変換される 2 バイト文字セット (DBCS) の文字列には、0x0020 以外のスペース文字が含まれる場合があり、このようなスペースはこの関数で削除できません。</span><span class="sxs-lookup"><span data-stu-id="9c594-106">When double-byte character set (DBCS) strings are converted to Unicode they may include space characters other than 0x0020 and the function cannot remove such spaces.</span></span> <span data-ttu-id="9c594-107">すべての種類のスペースを削除するには、スクリプト コンポーネントから実行するスクリプト内で、Microsoft Visual Basic .NET の Trim メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c594-107">To remove all kinds of spaces, you can use the Microsoft Visual Basic .NET Trim method in a script run from the Script component.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c594-108">構文</span><span class="sxs-lookup"><span data-stu-id="9c594-108">Syntax</span></span>  
  
```  
  
TRIM(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="9c594-109">引数</span><span class="sxs-lookup"><span data-stu-id="9c594-109">Arguments</span></span>  
 <span data-ttu-id="9c594-110">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="9c594-110">*character_expression*</span></span>  
 <span data-ttu-id="9c594-111">スペースを削除する対象となる文字式です。</span><span class="sxs-lookup"><span data-stu-id="9c594-111">Is a character expression from which to remove spaces.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9c594-112">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="9c594-112">Result Types</span></span>  
 <span data-ttu-id="9c594-113">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="9c594-113">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c594-114">解説</span><span class="sxs-lookup"><span data-stu-id="9c594-114">Remarks</span></span>  
 <span data-ttu-id="9c594-115">引数が NULL の場合、TRIM は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="9c594-115">TRIM returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="9c594-116">TRIM は、DT_WSTR データ型でのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="9c594-116">TRIM works only with the DT_WSTR data type.</span></span> <span data-ttu-id="9c594-117">*character_expression* 引数が DT_STR データ型の文字列リテラルまたはデータ列である場合は、TRIM による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="9c594-117">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before TRIM performs its operation.</span></span> <span data-ttu-id="9c594-118">その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c594-118">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="9c594-119">詳しくは、「[Integration Services のデータ型](../data-flow/integration-services-data-types.md)」および「[Cast &#40;SSIS 式&#41;](cast-ssis-expression.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9c594-119">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="9c594-120">式の例</span><span class="sxs-lookup"><span data-stu-id="9c594-120">Expression Examples</span></span>  
 <span data-ttu-id="9c594-121">この例では、文字列リテラルから先頭および末尾のスペースが削除されます。</span><span class="sxs-lookup"><span data-stu-id="9c594-121">This example removes leading and trailing spaces from a string literal.</span></span> <span data-ttu-id="9c594-122">返される結果は、"New York" です。</span><span class="sxs-lookup"><span data-stu-id="9c594-122">The return result is "New York".</span></span>  
  
```  
TRIM("   New York   ")  
```  
  
 <span data-ttu-id="9c594-123">この例では、 **FirstName** 列と **LastName** 列を連結した結果から、先頭および末尾のスペースが削除されます。</span><span class="sxs-lookup"><span data-stu-id="9c594-123">This example removes leading and trailing spaces from the result of concatenating the **FirstName** and **LastName** columns.</span></span> <span data-ttu-id="9c594-124">**FirstName** と **LastName** の間の空の文字列は、削除されません。</span><span class="sxs-lookup"><span data-stu-id="9c594-124">The empty string between **FirstName** and **LastName** is not removed.</span></span>  
  
```  
TRIM(FirstName + " "+ LastName)  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c594-125">参照</span><span class="sxs-lookup"><span data-stu-id="9c594-125">See Also</span></span>  
 <span data-ttu-id="9c594-126">[LTRIM (SSIS 式)](trim-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="9c594-126">[LTRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md) </span></span>  
 <span data-ttu-id="9c594-127">[RTRIM &#40;SSIS 式&#41;](rtrim-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="9c594-127">[RTRIM &#40;SSIS Expression&#41;](rtrim-ssis-expression.md) </span></span>  
 [<span data-ttu-id="9c594-128">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="9c594-128">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
