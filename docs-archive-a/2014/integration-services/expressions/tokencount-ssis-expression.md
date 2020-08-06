---
title: TOKENCOUNT (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1c0efed1-c2b3-4f20-a3a1-ad91283b7c0a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9068e4958570a0222bc8e1a4c90d34acc5bdf3dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716445"
---
# <a name="tokencount-ssis-expression"></a><span data-ttu-id="64d5b-102">TOKENCOUNT (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="64d5b-102">TOKENCOUNT (SSIS Expression)</span></span>
  <span data-ttu-id="64d5b-103">指定された区切り記号で区切られたトークンを含んでいる文字列内のトークン数を返します。</span><span class="sxs-lookup"><span data-stu-id="64d5b-103">Returns the number of tokens in a string that contains tokens separated by the specified delimiters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64d5b-104">構文</span><span class="sxs-lookup"><span data-stu-id="64d5b-104">Syntax</span></span>  
  
```  
TOKENCOUNT(character_expression, delimiter_string)  
```  
  
## <a name="arguments"></a><span data-ttu-id="64d5b-105">引数</span><span class="sxs-lookup"><span data-stu-id="64d5b-105">Arguments</span></span>  
 <span data-ttu-id="64d5b-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="64d5b-106">*character_expression*</span></span>  
 <span data-ttu-id="64d5b-107">区切り記号で区切られたトークンを含む文字列です。</span><span class="sxs-lookup"><span data-stu-id="64d5b-107">A string that contains tokens separated by delimiters.</span></span>  
  
 <span data-ttu-id="64d5b-108">*delimiter_string*</span><span class="sxs-lookup"><span data-stu-id="64d5b-108">*delimiter_string*</span></span>  
 <span data-ttu-id="64d5b-109">区切り記号を含む文字列です。</span><span class="sxs-lookup"><span data-stu-id="64d5b-109">A string that contains delimiter characters.</span></span> <span data-ttu-id="64d5b-110">たとえば、"; ," には 3 つの区切り記号 (セミコロン、空白、コンマ) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="64d5b-110">For example, "; ," contains three delimiter characters semi-colon, a blank space, and a comma.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="64d5b-111">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="64d5b-111">Result Types</span></span>  
 <span data-ttu-id="64d5b-112">DT_I4</span><span class="sxs-lookup"><span data-stu-id="64d5b-112">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64d5b-113">解説</span><span class="sxs-lookup"><span data-stu-id="64d5b-113">Remarks</span></span>  
 <span data-ttu-id="64d5b-114">TOKEN 関数には次の解説が適用されます。</span><span class="sxs-lookup"><span data-stu-id="64d5b-114">The following remarks apply to the TOKEN function:</span></span>  
  
-   <span data-ttu-id="64d5b-115">区切り記号には 1 つ以上の区切り文字を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="64d5b-115">The delimiter string can contain one or more delimiter characters.</span></span>  
  
-   <span data-ttu-id="64d5b-116">先頭の区切り記号はスキップされます。</span><span class="sxs-lookup"><span data-stu-id="64d5b-116">Leading delimiters are skipped.</span></span>  
  
-   <span data-ttu-id="64d5b-117">TOKENCOUNT は、DT_WSTR データ型でのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="64d5b-117">TOKENCOUNT works only with the DT_WSTR data type.</span></span> <span data-ttu-id="64d5b-118">*character_expression* 引数が DT_STR データ型の文字列リテラルまたはデータ列である場合は、TOKEN による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="64d5b-118">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before TOKEN performs its operation.</span></span> <span data-ttu-id="64d5b-119">その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="64d5b-119">Other data types must be explicitly cast to the DT_WSTR data type.</span></span>  
  
-   <span data-ttu-id="64d5b-120">character_expression が NULL の場合、TOKENCOUNT は 0 (ゼロ) を返します。</span><span class="sxs-lookup"><span data-stu-id="64d5b-120">TOKENCOUNT returns 0 (zero) if the character_expression is null.</span></span>  
  
-   <span data-ttu-id="64d5b-121">この式の引数として、変数と列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="64d5b-121">You can use variables and columns as arguments for this expression.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="64d5b-122">式の例</span><span class="sxs-lookup"><span data-stu-id="64d5b-122">Expression Examples</span></span>  
 <span data-ttu-id="64d5b-123">次の例では、TOKENCOUNT 関数は 3 を返します。これは、文字列に 3 つのトークン ("01"、"12"、および "2011") が含まれているためです。</span><span class="sxs-lookup"><span data-stu-id="64d5b-123">In the following example, the TOKENCOUNT function returns 3 because the string contains three tokens: "01", "12", "2011".</span></span>  
  
```  
TOKENCOUNT("01/12/2011", "/")  
```  
  
 <span data-ttu-id="64d5b-124">次の例では、TOKENCOUNT 関数は 4 を返します。これは、文字列に 4 つのトークン ("a"、"little"、"white"、および "dog") が含まれているためです。</span><span class="sxs-lookup"><span data-stu-id="64d5b-124">In the following example, the TOKENCOUNT function returns 4 because there are four tokens ("a", "little", "white", "dog").</span></span>  
  
```  
TOKENCOUNT("a little white dog"," ")  
```  
  
 <span data-ttu-id="64d5b-125">次の例では、TOKENCOUNT 関数は 1 を返します。</span><span class="sxs-lookup"><span data-stu-id="64d5b-125">In the following example, the TOKENCOUNT function returns 1.</span></span> <span data-ttu-id="64d5b-126">関数は区切り記号に対応する入力文字列を解析しますが、文字列には区切り記号が含まれていないため、文字列全体を最初のトークンとして加算します。</span><span class="sxs-lookup"><span data-stu-id="64d5b-126">The function parses the input string for delimiters and since there are none in the string, it just adds the entire string as the first token.</span></span>  
  
```  
TOKENCOUNT("a little white dog","|")  
```  
  
 <span data-ttu-id="64d5b-127">次の例では、TOKENCOUNT 関数は 4 を返します。</span><span class="sxs-lookup"><span data-stu-id="64d5b-127">In the following example, the TOKENCOUNT function returns 4.</span></span> <span data-ttu-id="64d5b-128">この例では、5 つの区切り記号が指定されています。</span><span class="sxs-lookup"><span data-stu-id="64d5b-128">The delimiter string in this example contains 5 delimiters.</span></span> <span data-ttu-id="64d5b-129">入力文字列には 4 つのトークン ("a"、"little"、"white"、および "dog") が含まれています。</span><span class="sxs-lookup"><span data-stu-id="64d5b-129">The input string contains 4 tokens: "a", "little", "white", "dog".</span></span>  
  
```  
TOKENCOUNT("a:little|white dog","| ,.:")  
```  
  
 <span data-ttu-id="64d5b-130">次の例では、TOKENCOUNT 関数は 4 を返します。</span><span class="sxs-lookup"><span data-stu-id="64d5b-130">In the following example, the TOKENCOUNT function returns 4.</span></span> <span data-ttu-id="64d5b-131">先頭の空白文字はすべて無視されます。</span><span class="sxs-lookup"><span data-stu-id="64d5b-131">It ignores all the leading space characters.</span></span>  
  
```  
TOKENCOUNT("        a little white dog", " ")  
```  
  
## <a name="see-also"></a><span data-ttu-id="64d5b-132">参照</span><span class="sxs-lookup"><span data-stu-id="64d5b-132">See Also</span></span>  
 [<span data-ttu-id="64d5b-133">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="64d5b-133">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
