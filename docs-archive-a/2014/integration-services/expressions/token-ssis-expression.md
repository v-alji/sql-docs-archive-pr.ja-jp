---
title: TOKEN (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9fdd06bf-5bc9-445c-95bf-709e0ca5989b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5c0598c3832e4bf6f838087be4fee541663c8bff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716453"
---
# <a name="token--ssis-expression"></a><span data-ttu-id="1ed70-102">TOKEN (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="1ed70-102">TOKEN  (SSIS Expression)</span></span>
  <span data-ttu-id="1ed70-103">文字列内のトークンを区切る指定された区切り記号、および返されるトークンを表すトークン数に基づいて、文字列からトークン (サブストリング) を返します。</span><span class="sxs-lookup"><span data-stu-id="1ed70-103">Returns a token (substring) from a string based on the specified delimiters that separate tokens in the string and the number of the token that denotes which token to be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ed70-104">構文</span><span class="sxs-lookup"><span data-stu-id="1ed70-104">Syntax</span></span>  
  
```  
TOKEN(character_expression, delimiter_string, occurrence)  
```  
  
## <a name="arguments"></a><span data-ttu-id="1ed70-105">引数</span><span class="sxs-lookup"><span data-stu-id="1ed70-105">Arguments</span></span>  
 <span data-ttu-id="1ed70-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="1ed70-106">*character_expression*</span></span>  
 <span data-ttu-id="1ed70-107">区切り記号で区切られたトークンを含む文字列です。</span><span class="sxs-lookup"><span data-stu-id="1ed70-107">A string that contains tokens separated by delimiters.</span></span>  
  
 <span data-ttu-id="1ed70-108">*delimiter_string*</span><span class="sxs-lookup"><span data-stu-id="1ed70-108">*delimiter_string*</span></span>  
 <span data-ttu-id="1ed70-109">区切り記号を含む文字列です。</span><span class="sxs-lookup"><span data-stu-id="1ed70-109">A string that contains delimiter characters.</span></span> <span data-ttu-id="1ed70-110">たとえば、"; ," には 3 つの区切り記号 (セミコロン、空白、コンマ) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1ed70-110">For example, "; ," contains three delimiter characters semi-colon, a blank space, and a comma.</span></span>  
  
 <span data-ttu-id="1ed70-111">*occurrence*</span><span class="sxs-lookup"><span data-stu-id="1ed70-111">*occurrence*</span></span>  
 <span data-ttu-id="1ed70-112">返されるトークンを指定する符号付きまたは符号なし整数。</span><span class="sxs-lookup"><span data-stu-id="1ed70-112">A signed or unsigned integer that specifies the token to be returned.</span></span> <span data-ttu-id="1ed70-113">たとえば、このパラメーターの値として 3 を指定すると、文字列内の 3 番目のトークンが返されます。</span><span class="sxs-lookup"><span data-stu-id="1ed70-113">For example, if you specify 3 as a value for this parameter, the third token in the string is returned.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="1ed70-114">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="1ed70-114">Result Types</span></span>  
 <span data-ttu-id="1ed70-115">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="1ed70-115">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ed70-116">解説</span><span class="sxs-lookup"><span data-stu-id="1ed70-116">Remarks</span></span>  
 <span data-ttu-id="1ed70-117">この関数は、<character_expression> 文字列を <delimiter_string> で指定された区切り記号で区切ったトークンのセットに分割した後、N 番目のトークンを返します。N は \<occurrence> パラメーターで指定されたトークンの発生回数です。</span><span class="sxs-lookup"><span data-stu-id="1ed70-117">This function splits up the <character_expression> string into a set of tokens separated by the delimiters specified in the <delimiter_string> and then returns the Nth token where N is the number of occurrence of the token specified by the \<occurrence> parameter.</span></span> <span data-ttu-id="1ed70-118">この関数のサンプルについては、「使用例」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ed70-118">See Examples section for sample usages of this function.</span></span>  
  
 <span data-ttu-id="1ed70-119">TOKEN 関数には次の解説が適用されます。</span><span class="sxs-lookup"><span data-stu-id="1ed70-119">The following remarks apply to the TOKEN function:</span></span>  
  
-   <span data-ttu-id="1ed70-120">区切り記号には 1 つ以上の区切り文字を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="1ed70-120">The delimiter string can contain one or more delimiter characters.</span></span>  
  
-   <span data-ttu-id="1ed70-121">\<occurrence> パラメーターの値が文字列内のトークンの合計数より大きい場合、この関数は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="1ed70-121">If the value of \<occurrence> parameter is higher than the total number of tokens in the string, the function returns NULL.</span></span>  
  
-   <span data-ttu-id="1ed70-122">先頭の区切り記号はスキップされます。</span><span class="sxs-lookup"><span data-stu-id="1ed70-122">Leading delimiters are skipped.</span></span>  
  
-   <span data-ttu-id="1ed70-123">TOKEN は、DT_WSTR データ型でのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="1ed70-123">TOKEN works only with the DT_WSTR data type.</span></span> <span data-ttu-id="1ed70-124">*character_expression* 引数が DT_STR データ型の文字列リテラルまたはデータ列である場合は、TOKEN による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="1ed70-124">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before TOKEN performs its operation.</span></span> <span data-ttu-id="1ed70-125">その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ed70-125">Other data types must be explicitly cast to the DT_WSTR data type.</span></span>  
  
-   <span data-ttu-id="1ed70-126">character_expression が NULL の場合、TOKEN は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="1ed70-126">TOKEN returns a null result if the character_expression is null.</span></span>  
  
-   <span data-ttu-id="1ed70-127">式のすべての引数で、変数および列を値として使用できます。</span><span class="sxs-lookup"><span data-stu-id="1ed70-127">You can use variables and columns as values of all arguments in the expression.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="1ed70-128">式の例</span><span class="sxs-lookup"><span data-stu-id="1ed70-128">Expression Examples</span></span>  
 <span data-ttu-id="1ed70-129">次の例では、TOKEN 関数は "a" を返します。</span><span class="sxs-lookup"><span data-stu-id="1ed70-129">In the following example, the TOKEN function returns "a".</span></span> <span data-ttu-id="1ed70-130">文字列 "a little white dog" には、区切り記号 " " (空白文字) で区切られた 4 つのトークン、"a"、"little"、"white"、"dog" があります。</span><span class="sxs-lookup"><span data-stu-id="1ed70-130">The string "a little white dog" has 4 tokens "a", "little", "white", "dog" separated by the delimiter " " (space character).</span></span> <span data-ttu-id="1ed70-131">2 番目の引数である区切り記号は、入力文字列をトークンに分割するときに使用される 1 つの区切り記号 (空白文字) のみを指定します。</span><span class="sxs-lookup"><span data-stu-id="1ed70-131">The second argument, a delimiter string, specifies only one delimiter, the space character, to be used in splitting the input string into tokens.</span></span> <span data-ttu-id="1ed70-132">最後の引数である 1 は、返される最初のトークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="1ed70-132">The last argument, 1, specifies that the first token to be returned.</span></span> <span data-ttu-id="1ed70-133">この文字列のサンプルでは、最初のトークンは "a" です。</span><span class="sxs-lookup"><span data-stu-id="1ed70-133">The first token is "a" in this sample string.</span></span>  
  
```  
TOKEN("a little white dog"," ",1)  
```  
  
 <span data-ttu-id="1ed70-134">次の例では、TOKEN 関数は "dog" を返します。</span><span class="sxs-lookup"><span data-stu-id="1ed70-134">In the following example, the TOKEN function returns "dog".</span></span> <span data-ttu-id="1ed70-135">この例では、5 つの区切り記号が指定されています。</span><span class="sxs-lookup"><span data-stu-id="1ed70-135">The delimiter string in this example contains 5 delimiters.</span></span> <span data-ttu-id="1ed70-136">入力文字列には 4 つのトークン ("a"、"little"、"white"、および "dog") が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1ed70-136">The input string contains 4 tokens: "a", "little", "white", "dog".</span></span>  
  
```  
TOKEN("a:little|white dog","| ,.:",4)  
```  
  
 <span data-ttu-id="1ed70-137">次の例では、TOKEN 関数は "" (空の文字列） を返します。これは、文字列に 99 のトークンがないためです。</span><span class="sxs-lookup"><span data-stu-id="1ed70-137">In the following example, the TOKEN function returns "" (an empty string) because there are no 99 tokens in the string.</span></span>  
  
```  
TOKEN("a little white dog"," ",99)  
```  
  
 <span data-ttu-id="1ed70-138">次の例では、TOKEN 関数は完全な文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="1ed70-138">In the following example, the TOKEN function returns the full string.</span></span> <span data-ttu-id="1ed70-139">関数は区切り記号に対応する入力文字列を解析しますが、文字列には区切り記号が含まれていないため、文字列全体を最初のトークンとして加算します。</span><span class="sxs-lookup"><span data-stu-id="1ed70-139">The function parses the input string for delimiters and since there are none in the string, it just adds the entire string as the first token.</span></span>  
  
```  
TOKEN("a little white dog","|",1)  
```  
  
 <span data-ttu-id="1ed70-140">次の例では、TOKEN 関数は "a" を返します。</span><span class="sxs-lookup"><span data-stu-id="1ed70-140">In the following example, the TOKEN function returns "a".</span></span> <span data-ttu-id="1ed70-141">先頭の空白文字はすべて無視されます。</span><span class="sxs-lookup"><span data-stu-id="1ed70-141">It ignores all the leading space characters.</span></span>  
  
```  
TOKEN("        a little white dog", " ", 1)  
```  
  
 <span data-ttu-id="1ed70-142">次の例では、TOKEN 関数は日付文字列から年を返します。</span><span class="sxs-lookup"><span data-stu-id="1ed70-142">In the following example, the TOKEN function returns the year from a date string.</span></span>  
  
```  
TOKEN("2009/01/01", "/"), 1  
```  
  
 <span data-ttu-id="1ed70-143">次の例では、TOKEN 関数は指定されたパスからファイル名を返します。</span><span class="sxs-lookup"><span data-stu-id="1ed70-143">In the following example, the TOKEN function returns the file name from the specified path.</span></span> <span data-ttu-id="1ed70-144">たとえば、User::Path の値が "c:\program files files\data\myfile.txt" の場合、TOKEN 関数は "myfile.txt" を返します。</span><span class="sxs-lookup"><span data-stu-id="1ed70-144">For example, if the value of User::Path is "c:\program files\data\myfile.txt", the TOKEN function returns "myfile.txt".</span></span> <span data-ttu-id="1ed70-145">TOKENCOUNT 関数は 4 を返し、TOKEN 関数は 4 番目のトークン "myfile.txt" を返します。</span><span class="sxs-lookup"><span data-stu-id="1ed70-145">The TOKENCOUNT function returns 4 and the TOKEN function return the 4th token, "myfile.txt".</span></span>  
  
```  
TOKEN(@[User::Path], "\\", TOKENCOUNT(@[User::Path], "\\"))  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ed70-146">参照</span><span class="sxs-lookup"><span data-stu-id="1ed70-146">See Also</span></span>  
 [<span data-ttu-id="1ed70-147">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="1ed70-147">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
