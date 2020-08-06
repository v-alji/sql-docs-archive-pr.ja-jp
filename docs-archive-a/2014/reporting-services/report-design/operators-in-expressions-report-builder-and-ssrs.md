---
title: 式で使用される演算子 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d22dc8b6-4353-40e7-91a1-65e8dae6325d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fa8042df39e535425a05414c1e39ee6a12ff2f39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640695"
---
# <a name="operators-in-expressions-report-builder-and-ssrs"></a><span data-ttu-id="edd6b-102">式で使用される演算子 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="edd6b-102">Operators in Expressions (Report Builder and SSRS)</span></span>
  <span data-ttu-id="edd6b-103">演算子は、式に含まれる 1 つ以上の項に適用される操作を表す記号です。</span><span class="sxs-lookup"><span data-stu-id="edd6b-103">An operator is a symbol that represents actions applied to one or more terms in an expression.</span></span> <span data-ttu-id="edd6b-104">式でサポートされている演算子のカテゴリには、算術、比較、連結、論理 (ビット)、およびビット シフトがあります。</span><span class="sxs-lookup"><span data-stu-id="edd6b-104">The following categories of operators are supported in an expression: arithmetic, comparison, concatenation, logical or bitwise, and bit shift.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="arithmetic"></a><span data-ttu-id="edd6b-105">算術</span><span class="sxs-lookup"><span data-stu-id="edd6b-105">Arithmetic</span></span>  
 <span data-ttu-id="edd6b-106">算術演算子は、1 つの式に含まれる 2 つの項に対して数学的な操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="edd6b-106">Arithmetic operators perform mathematical operations on two numeric terms in an expression.</span></span>  
  
|<span data-ttu-id="edd6b-107">演算子</span><span class="sxs-lookup"><span data-stu-id="edd6b-107">Operator</span></span>|<span data-ttu-id="edd6b-108">説明</span><span class="sxs-lookup"><span data-stu-id="edd6b-108">Description</span></span>|  
|--------------|-----------------|  
|^|<span data-ttu-id="edd6b-109">一方の数値をもう一方の数値で累乗します。</span><span class="sxs-lookup"><span data-stu-id="edd6b-109">Raises a number to the power of another number.</span></span>|  
|*|<span data-ttu-id="edd6b-110">2 つの値を乗算します。</span><span class="sxs-lookup"><span data-stu-id="edd6b-110">Multiplies two numbers.</span></span>|  
|/|<span data-ttu-id="edd6b-111">2 つの数値の商を計算し、結果を浮動小数点で返します。</span><span class="sxs-lookup"><span data-stu-id="edd6b-111">Divides two numbers and returns a floating-point result.</span></span>|  
|<span data-ttu-id="edd6b-112">\|2 つの数値の商を計算し、結果を整数で返します。</span><span class="sxs-lookup"><span data-stu-id="edd6b-112">\|Divides two numbers and returns an integer result.</span></span>|  
|<span data-ttu-id="edd6b-113">Mod</span><span class="sxs-lookup"><span data-stu-id="edd6b-113">Mod</span></span>|<span data-ttu-id="edd6b-114">除算による整数の剰余を返します。</span><span class="sxs-lookup"><span data-stu-id="edd6b-114">Returns the integer remainder of a division.</span></span> <span data-ttu-id="edd6b-115">たとえば、7 Mod 5 の場合、7 を 5 で割ると余りは 2 なので、7 Mod 5 = 2 となります。</span><span class="sxs-lookup"><span data-stu-id="edd6b-115">For example, 7 Mod 5 = 2 because the remainder of 7 divided by 5 is 2.</span></span>|  
|+|<span data-ttu-id="edd6b-116">2 つの数値を加算します。</span><span class="sxs-lookup"><span data-stu-id="edd6b-116">Adds two numbers together.</span></span>|  
|-|<span data-ttu-id="edd6b-117">2 つの数式の差を返すか、項が負の値であることを示します。</span><span class="sxs-lookup"><span data-stu-id="edd6b-117">Returns the difference between two numbers or indicates the negative value of a numeric term.</span></span>|  
  
### <a name="comparison"></a><span data-ttu-id="edd6b-118">比較</span><span class="sxs-lookup"><span data-stu-id="edd6b-118">Comparison</span></span>  
 <span data-ttu-id="edd6b-119">比較演算子は、2 つの式が同じかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="edd6b-119">Comparison operators test whether two expressions are the same.</span></span>  
  
|<span data-ttu-id="edd6b-120">演算子</span><span class="sxs-lookup"><span data-stu-id="edd6b-120">Operator</span></span>|<span data-ttu-id="edd6b-121">説明</span><span class="sxs-lookup"><span data-stu-id="edd6b-121">Description</span></span>|  
|--------------|-----------------|  
|<|<span data-ttu-id="edd6b-122">より小さい。</span><span class="sxs-lookup"><span data-stu-id="edd6b-122">Less than.</span></span>|  
|\<=|<span data-ttu-id="edd6b-123">以下。</span><span class="sxs-lookup"><span data-stu-id="edd6b-123">Less than or equal to.</span></span>|  
|>|<span data-ttu-id="edd6b-124">より大きい。</span><span class="sxs-lookup"><span data-stu-id="edd6b-124">Greater than.</span></span>|  
|>=|<span data-ttu-id="edd6b-125">以上。</span><span class="sxs-lookup"><span data-stu-id="edd6b-125">Greater than or equal to.</span></span>|  
|=|<span data-ttu-id="edd6b-126">等しい。</span><span class="sxs-lookup"><span data-stu-id="edd6b-126">Equal to.</span></span>|  
|<>|<span data-ttu-id="edd6b-127">等しくない。</span><span class="sxs-lookup"><span data-stu-id="edd6b-127">Not equal to.</span></span>|  
|<span data-ttu-id="edd6b-128">Like</span><span class="sxs-lookup"><span data-stu-id="edd6b-128">Like</span></span>|<span data-ttu-id="edd6b-129">指定された文字列が指定されたパターンと一致するかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="edd6b-129">Determines whether a specific character string matches a specified pattern.</span></span> <span data-ttu-id="edd6b-130">パターンは、標準の文字とワイルドカード文字を含むことができます。</span><span class="sxs-lookup"><span data-stu-id="edd6b-130">A pattern can include regular characters and wildcard characters.</span></span> <span data-ttu-id="edd6b-131">パターン検索時に、標準の文字は文字列に指定された文字と正確に一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="edd6b-131">During pattern matching, regular characters must exactly match the characters specified in the character string.</span></span> <span data-ttu-id="edd6b-132">しかし、ワイルドカード文字は文字列の任意の部分と一致することができます。</span><span class="sxs-lookup"><span data-stu-id="edd6b-132">However, wildcard characters can be matched with arbitrary fragments of the character string.</span></span> <span data-ttu-id="edd6b-133">= や != などの文字列比較演算子を使用する場合と比べて、ワイルドカード文字を使用する方がより柔軟に LIKE 演算子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="edd6b-133">Using wildcard characters makes the LIKE operator more flexible than using the = and != string comparison operators.</span></span><br /><br /> <span data-ttu-id="edd6b-134">ワイルドカードとして使用できる文字を次に示します。</span><span class="sxs-lookup"><span data-stu-id="edd6b-134">The following lists characters that can be used as wildcards:</span></span><br /><br /> <span data-ttu-id="edd6b-135">**%**: 0 個以上の文字からなる任意の文字列。</span><span class="sxs-lookup"><span data-stu-id="edd6b-135">**%**: Any string of zero or more characters.</span></span><br /><br /> <span data-ttu-id="edd6b-136">**_**: 任意の1文字。</span><span class="sxs-lookup"><span data-stu-id="edd6b-136">**_**: Any single character.</span></span><br /><br /> <span data-ttu-id="edd6b-137">**[]**: 指定された範囲 (たとえば [a-f]) またはセット (たとえば [aeiou]) 内の任意の1文字。</span><span class="sxs-lookup"><span data-stu-id="edd6b-137">**[ ]**: Any single character within the specified range (for example, [a-f]) or set (for example, [aeiou]).</span></span><br /><br /> <span data-ttu-id="edd6b-138">**[^]**: 指定された範囲 (たとえば [^ a-f]) またはセット (たとえば [^ aeiou]) 内にない任意の1文字です。</span><span class="sxs-lookup"><span data-stu-id="edd6b-138">**[^]**: Any single character not within the specified range (for example, [^a-f]) or set (for example, [^aeiou]).</span></span>|  
|<span data-ttu-id="edd6b-139">Is</span><span class="sxs-lookup"><span data-stu-id="edd6b-139">Is</span></span>|<span data-ttu-id="edd6b-140">2 つのオブジェクト参照を比較します。</span><span class="sxs-lookup"><span data-stu-id="edd6b-140">Compares two object references.</span></span>|  
  
### <a name="string-concatenation"></a><span data-ttu-id="edd6b-141">文字列連結</span><span class="sxs-lookup"><span data-stu-id="edd6b-141">String Concatenation</span></span>  
 <span data-ttu-id="edd6b-142">文字列連結では、式に含まれる 2 番目の文字列が 1 番目の文字列の最後に追加されます。</span><span class="sxs-lookup"><span data-stu-id="edd6b-142">String concatenation appends the second string to the first string in an expression.</span></span> <span data-ttu-id="edd6b-143">その他の文字列操作では、組み込み関数を使用してください。</span><span class="sxs-lookup"><span data-stu-id="edd6b-143">For other string operations, use built-in functions.</span></span>  
  
|<span data-ttu-id="edd6b-144">演算子</span><span class="sxs-lookup"><span data-stu-id="edd6b-144">Operator</span></span>|<span data-ttu-id="edd6b-145">説明</span><span class="sxs-lookup"><span data-stu-id="edd6b-145">Description</span></span>|  
|--------------|-----------------|  
|&|<span data-ttu-id="edd6b-146">2 つの文字列を連結します。</span><span class="sxs-lookup"><span data-stu-id="edd6b-146">Concatenates two strings</span></span>|  
|+|<span data-ttu-id="edd6b-147">2 つの文字列を連結します。</span><span class="sxs-lookup"><span data-stu-id="edd6b-147">Concatenates two strings</span></span>|  
  
### <a name="logical-and-bitwise"></a><span data-ttu-id="edd6b-148">論理演算子とビット演算子</span><span class="sxs-lookup"><span data-stu-id="edd6b-148">Logical and Bitwise</span></span>  
 <span data-ttu-id="edd6b-149">論理演算子およびビット演算子は、式に含まれる 2 つの整数項の間の論理操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="edd6b-149">Logical and bitwise operators perform logical manipulations between two integer terms in an expression.</span></span>  
  
|<span data-ttu-id="edd6b-150">演算子</span><span class="sxs-lookup"><span data-stu-id="edd6b-150">Operator</span></span>|<span data-ttu-id="edd6b-151">説明</span><span class="sxs-lookup"><span data-stu-id="edd6b-151">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="edd6b-152">And</span><span class="sxs-lookup"><span data-stu-id="edd6b-152">And</span></span>|<span data-ttu-id="edd6b-153">2 つのブール式の場合は論理積、2 つの数値式の場合はビットごとの積を求めます。</span><span class="sxs-lookup"><span data-stu-id="edd6b-153">Performs a logical conjunction on two Boolean expressions, or bitwise conjunction on two numeric expressions.</span></span>|  
|<span data-ttu-id="edd6b-154">Not</span><span class="sxs-lookup"><span data-stu-id="edd6b-154">Not</span></span>|<span data-ttu-id="edd6b-155">ブール式の場合は論理否定、数値式の場合はビットごとの否定を求めます。</span><span class="sxs-lookup"><span data-stu-id="edd6b-155">Performs logical negation on a Boolean expression, or bitwise negation on a numeric expression.</span></span>|  
|<span data-ttu-id="edd6b-156">または</span><span class="sxs-lookup"><span data-stu-id="edd6b-156">Or</span></span>|<span data-ttu-id="edd6b-157">2 つのブール式の場合は論理和、2 つの数値の場合はビットごとの和を求めます。</span><span class="sxs-lookup"><span data-stu-id="edd6b-157">Performs a logical disjunction on two Boolean expressions, or bitwise disjunction on two numeric values.</span></span>|  
|<span data-ttu-id="edd6b-158">Xor</span><span class="sxs-lookup"><span data-stu-id="edd6b-158">Xor</span></span>|<span data-ttu-id="edd6b-159">2 つのブール式の場合は排他的論理演算、2 つの数値式の場合はビットごとの排他を求めます。</span><span class="sxs-lookup"><span data-stu-id="edd6b-159">Performs a logical exclusion operation on two Boolean expressions, or a bitwise exclusion on two numeric expressions.</span></span>|  
|<span data-ttu-id="edd6b-160">AndAlso</span><span class="sxs-lookup"><span data-stu-id="edd6b-160">AndAlso</span></span>|<span data-ttu-id="edd6b-161">2 つの式の論理積を求めます。</span><span class="sxs-lookup"><span data-stu-id="edd6b-161">Performs logical conjunction on two expressions.</span></span>|  
|<span data-ttu-id="edd6b-162">OrElse</span><span class="sxs-lookup"><span data-stu-id="edd6b-162">OrElse</span></span>|<span data-ttu-id="edd6b-163">2 つの式の論理和を求めます。</span><span class="sxs-lookup"><span data-stu-id="edd6b-163">Performs logical disjunction on two expressions.</span></span>|  
  
### <a name="bit-shift"></a><span data-ttu-id="edd6b-164">ビット シフト</span><span class="sxs-lookup"><span data-stu-id="edd6b-164">Bit Shift</span></span>  
 <span data-ttu-id="edd6b-165">ビットごとの演算子は、式に含まれる 2 つの整数項の間のビット操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="edd6b-165">Bitwise operators perform bit manipulations between two integer terms in an expression.</span></span>  
  
|<span data-ttu-id="edd6b-166">演算子</span><span class="sxs-lookup"><span data-stu-id="edd6b-166">Operator</span></span>|<span data-ttu-id="edd6b-167">説明</span><span class="sxs-lookup"><span data-stu-id="edd6b-167">Description</span></span>|  
|--------------|-----------------|  
|<\<|<span data-ttu-id="edd6b-168">ビット パターン上で算術左シフトを実行します。</span><span class="sxs-lookup"><span data-stu-id="edd6b-168">Performs an arithmetic left-shift on a bit pattern.</span></span>|  
|>>|<span data-ttu-id="edd6b-169">ビット パターン上で算術右シフトを実行します。</span><span class="sxs-lookup"><span data-stu-id="edd6b-169">Performs an arithmetic right-shift on a bit pattern.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="edd6b-170">参照</span><span class="sxs-lookup"><span data-stu-id="edd6b-170">See Also</span></span>  
 <span data-ttu-id="edd6b-171">[[式] ダイアログ ボックス](../expression-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="edd6b-171">[Expression Dialog Box](../expression-dialog-box.md) </span></span>  
 <span data-ttu-id="edd6b-172">[式 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="edd6b-172">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="edd6b-173">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="edd6b-173">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="edd6b-174">[式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](data-types-in-expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="edd6b-174">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](data-types-in-expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="edd6b-175">[[式] ダイアログ ボックス &#40;レポート ビルダー&#41;](../expression-dialog-box-report-builder.md)</span><span class="sxs-lookup"><span data-stu-id="edd6b-175">[Expression Dialog Box &#40;Report Builder&#41;](../expression-dialog-box-report-builder.md)</span></span>  
  
  
