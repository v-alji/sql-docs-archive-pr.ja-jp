---
title: 構文ペアの自動照合
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [SQL Server], delimiter highlighting
- IntelliSense [SQL Server], syntax pair matching
ms.assetid: bfc54cda-bfd6-4545-a5b9-f9db2ae13769
author: rothja
ms.author: jroth
ms.openlocfilehash: d1237eeb9aaec39e3210b00c880c0005ef3d95bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634920"
---
# <a name="automatic-matching-of-syntax-pairs"></a><span data-ttu-id="aa650-102">構文ペアの自動照合</span><span class="sxs-lookup"><span data-stu-id="aa650-102">Automatic Matching of Syntax Pairs</span></span>
  <span data-ttu-id="aa650-103">構文ペアの自動照合では、ペアでコーディングする必要がある構文要素が正しくペアになっているかどうかをすぐに検出します。</span><span class="sxs-lookup"><span data-stu-id="aa650-103">Automatic matching of syntax pairs gives you immediate feedback on whether syntax elements that must be coded in pairs are correctly paired.</span></span> <span data-ttu-id="aa650-104">この機能は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のクエリ エディターでは区切り記号の照合、Analysis Services の XMLA クエリ エディターでは中かっこの照合、MDX エディターと DMX エディターではかっこの照合として知られています。</span><span class="sxs-lookup"><span data-stu-id="aa650-104">This is known as delimiter matching in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor, brace matching in the Analysis Services XMLA Query Editor, and parenthesis matching in the MDX and DMX editors.</span></span>  
  
## <a name="database-engine-query-editor-delimiter-matching"></a><span data-ttu-id="aa650-105">データベース エンジンのクエリ エディターでの区切り記号の照合</span><span class="sxs-lookup"><span data-stu-id="aa650-105">Database Engine Query Editor Delimiter Matching</span></span>  
 <span data-ttu-id="aa650-106">[!INCLUDE[ssDE](../../includes/ssde-md.md)] のクエリ エディターでは、コード ブロックの境界を識別する区切り記号が照合されます。</span><span class="sxs-lookup"><span data-stu-id="aa650-106">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor matches the delimiters that identify the boundaries of code blocks.</span></span> <span data-ttu-id="aa650-107">照合は、次の 2 とおりの方法で行われます。</span><span class="sxs-lookup"><span data-stu-id="aa650-107">The matching is done in two ways:</span></span>  
  
-   <span data-ttu-id="aa650-108">ペアの 2 番目の区切り記号の入力が終了すると、ペアになる両方の区切り記号が強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa650-108">The editor highlights both delimiters in a pair when you finish typing the second delimiter in the pair.</span></span>  
  
-   <span data-ttu-id="aa650-109">ペアのいすれかの区切り記号にカーソルが置かれていれば、&lt;localizedText&gt;Ctrl&lt;/localizedText&gt; キーを押しながら &lt;localizedText&gt;]&lt;/localizedText&gt; キーを押すと、対応する区切り記号に移動できます。</span><span class="sxs-lookup"><span data-stu-id="aa650-109">Anytime the cursor is in one of the delimiters in a pair, you can use the CTRL+] keyboard shortcut to jump to the matching delimiter.</span></span>  
  
### <a name="delimiter-pairs"></a><span data-ttu-id="aa650-110">区切り記号のペア</span><span class="sxs-lookup"><span data-stu-id="aa650-110">Delimiter Pairs</span></span>  
 <span data-ttu-id="aa650-111">区切り記号の自動照合では、次の区切り記号のペアが認識されます。</span><span class="sxs-lookup"><span data-stu-id="aa650-111">Automatic delimiter matching recognizes the following sets of delimiters:</span></span>  
  
|<span data-ttu-id="aa650-112">開始区切り記号</span><span class="sxs-lookup"><span data-stu-id="aa650-112">Lead Delimiter</span></span>|<span data-ttu-id="aa650-113">終了区切り記号</span><span class="sxs-lookup"><span data-stu-id="aa650-113">Closing Delimiter</span></span>|  
|--------------------|-----------------------|  
|<span data-ttu-id="aa650-114">**(**</span><span class="sxs-lookup"><span data-stu-id="aa650-114">**(**</span></span>|<span data-ttu-id="aa650-115">**)**</span><span class="sxs-lookup"><span data-stu-id="aa650-115">**)**</span></span>|  
|<span data-ttu-id="aa650-116">**BEGIN**</span><span class="sxs-lookup"><span data-stu-id="aa650-116">**BEGIN**</span></span>|<span data-ttu-id="aa650-117">**END**</span><span class="sxs-lookup"><span data-stu-id="aa650-117">**END**</span></span>|  
|<span data-ttu-id="aa650-118">**BEGIN TRY**</span><span class="sxs-lookup"><span data-stu-id="aa650-118">**BEGIN TRY**</span></span>|<span data-ttu-id="aa650-119">**END TRY**</span><span class="sxs-lookup"><span data-stu-id="aa650-119">**END TRY**</span></span>|  
|<span data-ttu-id="aa650-120">**BEGIN CATCH**</span><span class="sxs-lookup"><span data-stu-id="aa650-120">**BEGIN CATCH**</span></span>|<span data-ttu-id="aa650-121">**END CATCH**</span><span class="sxs-lookup"><span data-stu-id="aa650-121">**END CATCH**</span></span>|  
  
 <span data-ttu-id="aa650-122">区切り記号の自動照合では、角かっこで囲まれた識別子 ([ObjectName]) や引用符で囲まれた識別子 ("ObjectName") は認識されません。</span><span class="sxs-lookup"><span data-stu-id="aa650-122">Automatic delimiter matching does not recognize the delimiters for bracketed identifiers ([ObjectName]), or quoted identifiers ("ObjectName").</span></span> <span data-ttu-id="aa650-123">ペアの照合では、文字列リテラル ('string') の単一引用符区切り記号は照合されません。文字列が区切られているかどうかが既に色分け表示されているためです。</span><span class="sxs-lookup"><span data-stu-id="aa650-123">Pair matching does not match the single quotation delimiters for string literals ('string') because color coding already gives a visual indication of whether the string has been delimited.</span></span>  
  
### <a name="delimiter-highlighting"></a><span data-ttu-id="aa650-124">区切り記号の強調表示</span><span class="sxs-lookup"><span data-stu-id="aa650-124">Delimiter Highlighting</span></span>  
 <span data-ttu-id="aa650-125">照合により、区切り記号のペアの開始要素と終了要素がどちらも強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa650-125">Matching highlights both the lead and closing element of a pair of delimiters.</span></span> <span data-ttu-id="aa650-126">これにより、コード ブロックを視覚的に認識し、対応していない区切り記号のペアを確認できます。</span><span class="sxs-lookup"><span data-stu-id="aa650-126">This lets you visually identify code blocks and check for mismatched pairs of delimiters.</span></span>  
  
 <span data-ttu-id="aa650-127">最後の文字を入力してペアが完成すると、区切り記号が強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa650-127">Delimiters are highlighted when you type the final letter that completes the pair.</span></span> <span data-ttu-id="aa650-128">たとえば、BEGIN の後に END を入力する BEGIN END ペアの場合、END の最後の文字を入力すると区切り記号が強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa650-128">For example, for a BEGIN END pair where you type BEGIN first followed by END, highlighting turns on when you type the final letter in END.</span></span> <span data-ttu-id="aa650-129">必ずしも、開始区切り記号を入力した後に終了区切り記号を入力すると強調表示されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="aa650-129">You do not have to type the lead delimiter followed by the closing delimiter to turn on highlighting.</span></span> <span data-ttu-id="aa650-130">最初に END を入力し、スクリプトを上にスクロールして、BEGIN を入力した場合、BEGIN の最後の文字を入力したときに区切り記号が強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa650-130">If you type END first, then scroll back up the script and type BEGIN, highlighting is turned on when you type the final letter in BEGIN.</span></span> <span data-ttu-id="aa650-131">最後に入力する文字は、区切り記号の最後の文字でなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="aa650-131">The final letter typed does not have to be the end letter in the delimiter.</span></span> <span data-ttu-id="aa650-132">たとえば、BEGIN のスペルを間違えて BEIN と入力した場合、最後に文字 G を挿入すると、BEGIN END のペアが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa650-132">For example, you could misspell BEGIN as BEIN, when you insert the final G the BEGIN END pair is highlighted.</span></span>  
  
 <span data-ttu-id="aa650-133">区切り記号のペアは、カーソルを移動するまで強調表示されたままです。</span><span class="sxs-lookup"><span data-stu-id="aa650-133">The delimiter pair remains highlighted until you move the cursor.</span></span> <span data-ttu-id="aa650-134">新しいカーソル位置が同じ区切り記号の中にあっても、カーソルを移動すると強調表示が解除されます。</span><span class="sxs-lookup"><span data-stu-id="aa650-134">The highlighting is turned off when the cursor is moved, even if the new cursor position remains in the same delimiter.</span></span> <span data-ttu-id="aa650-135">ペアのいずれかの任意の文字を削除してから再入力すると、再度強調表示することができます。</span><span class="sxs-lookup"><span data-stu-id="aa650-135">You can turn the highlighting back on by deleting and retyping any letter in either member of the pair.</span></span>  
  
## <a name="analysis-services-xmla-query-editor-brace-matching"></a><span data-ttu-id="aa650-136">Analysis Services の XMLA クエリ エディターでの中かっこの照合</span><span class="sxs-lookup"><span data-stu-id="aa650-136">Analysis Services XMLA Query Editor Brace Matching</span></span>  
 <span data-ttu-id="aa650-137">XMLA クエリ エディターの中かっこの照合では、左中かっこと右中かっこが強調表示され、要素が閉じられたかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="aa650-137">The XMLA Query Editor brace matching shows if you have closed elements by highlighting opening and closing braces.</span></span> <span data-ttu-id="aa650-138">また、<localizedText>Ctrl</localizedText> キーを押しながら <localizedText>]</localizedText> キーを押して、中かっこから対応する中かっこに移動することもできます。</span><span class="sxs-lookup"><span data-stu-id="aa650-138">You can also use the CTRL+] keyboard shortcut to jump from one brace to the matching brace.</span></span>  
  
 <span data-ttu-id="aa650-139">XMLA クエリ エディターでは、次の用語に対して中かっこの照合が行われます。</span><span class="sxs-lookup"><span data-stu-id="aa650-139">The XMLA Query Editor does brace matching for the following terms:</span></span>  
  
-   <span data-ttu-id="aa650-140">照合の開始タグと終了タグ。</span><span class="sxs-lookup"><span data-stu-id="aa650-140">Matching start and end tags.</span></span>  
  
-   <span data-ttu-id="aa650-141">"" 山かっこの任意のペア \<" and "> 。</span><span class="sxs-lookup"><span data-stu-id="aa650-141">Any pair of "\<" and ">" angle brackets.</span></span>  
  
-   <span data-ttu-id="aa650-142">コメントの開始と終了。</span><span class="sxs-lookup"><span data-stu-id="aa650-142">Start and end of comments.</span></span>  
  
-   <span data-ttu-id="aa650-143">処理命令の開始と終了。</span><span class="sxs-lookup"><span data-stu-id="aa650-143">Start and end of processing instructions.</span></span>  
  
-   <span data-ttu-id="aa650-144">CDATA ブロックの開始と終了。</span><span class="sxs-lookup"><span data-stu-id="aa650-144">Start and end of CDATA blocks.</span></span>  
  
-   <span data-ttu-id="aa650-145">DTD 宣言の開始と終了。</span><span class="sxs-lookup"><span data-stu-id="aa650-145">Start and end of DTD declarations.</span></span>  
  
-   <span data-ttu-id="aa650-146">属性の開始引用符と終了引用符。</span><span class="sxs-lookup"><span data-stu-id="aa650-146">Opening and closing quotes on attributes.</span></span>  
  
## <a name="mdx-and-dmx-editor-parenthesis-matching"></a><span data-ttu-id="aa650-147">MDX エディターと DMX エディターでのかっこの照合</span><span class="sxs-lookup"><span data-stu-id="aa650-147">MDX and DMX Editor Parenthesis Matching</span></span>  
 <span data-ttu-id="aa650-148">多次元式 (MDX) エディターとデータ マイニング式 (DMX) のエディターでは、関数のかっこのペアが自動的に照合されます。</span><span class="sxs-lookup"><span data-stu-id="aa650-148">The Multi-Dimensional Expressions (MDX) and Data Mining Expressions (DMX) Editors automatically match parenthesis pairs in functions.</span></span>  
  
  
