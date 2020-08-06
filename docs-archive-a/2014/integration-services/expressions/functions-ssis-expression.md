---
title: 関数 (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- functions [Integration Services]
- expressions [Integration Services], functions
- string functions
- SQL Server Integration Services, functions
- SSIS, functions
ms.assetid: e9a41a31-94f4-46a4-b737-c707dd59ce48
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 298085a1e3b9c292c9289415a4cb8a3c5adabea1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639566"
---
# <a name="functions-ssis-expression"></a><span data-ttu-id="2c6d4-102">関数 (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="2c6d4-102">Functions (SSIS Expression)</span></span>
  <span data-ttu-id="2c6d4-103">式言語には、式で使用するための関数セットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-103">The expression language includes a set of functions for use in expressions.</span></span> <span data-ttu-id="2c6d4-104">式で 1 つの関数を使用することもできますが、通常、式は関数と演算子を組み合わせて使用したり、複数の関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-104">An expression can use a single function, but typically an expression combines functions with operators and uses multiple functions.</span></span>  
  
 <span data-ttu-id="2c6d4-105">関数は、次の各グループに分類されます。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-105">The functions can be categorized into the following groups:</span></span>  
  
-   <span data-ttu-id="2c6d4-106">数学関数。パラメーターとして渡された数値型の入力値に基づいて計算を実行し、数値を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-106">Mathematical functions that perform calculations based on numeric input values provided as parameters to the functions and return numeric values.</span></span>  
  
-   <span data-ttu-id="2c6d4-107">文字列関数。文字列型または 16 進数の入力値に対して操作を実行し、文字列値または数値を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-107">String functions that perform operations on string or hexadecimal input values and return a string or numeric value.</span></span>  
  
-   <span data-ttu-id="2c6d4-108">日付関数および時刻関数。日時の値に対して操作を実行し、文字列、数値、または日時の値を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-108">Date and time functions that perform operations on date and time values and return string, numeric, or date and time values.</span></span>  
  
-   <span data-ttu-id="2c6d4-109">システム関数。式に関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-109">System functions that return information about an expression.</span></span>  
  
 <span data-ttu-id="2c6d4-110">式言語には、次の数学関数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-110">The expression language provides the following mathematical functions.</span></span>  
  
|<span data-ttu-id="2c6d4-111">Function</span><span class="sxs-lookup"><span data-stu-id="2c6d4-111">Function</span></span>|<span data-ttu-id="2c6d4-112">説明</span><span class="sxs-lookup"><span data-stu-id="2c6d4-112">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="2c6d4-113">ABS &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-113">ABS &#40;SSIS Expression&#41;</span></span>](abs-ssis-expression.md)|<span data-ttu-id="2c6d4-114">数値式の正の絶対値を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-114">Returns the absolute, positive value of a numeric expression.</span></span>|  
|[<span data-ttu-id="2c6d4-115">EXP &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-115">EXP &#40;SSIS Expression&#41;</span></span>](exp-ssis-expression.md)|<span data-ttu-id="2c6d4-116">指定した式の e を基数とする指数を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-116">Returns the exponent to base e of the specified expression.</span></span>|  
|[<span data-ttu-id="2c6d4-117">CEILING &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-117">CEILING &#40;SSIS Expression&#41;</span></span>](ceiling-ssis-expression.md)|<span data-ttu-id="2c6d4-118">数値式以上で最小の整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-118">Returns the smallest integer that is greater than or equal to a numeric expression.</span></span>|  
|[<span data-ttu-id="2c6d4-119">FLOOR &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-119">FLOOR &#40;SSIS Expression&#41;</span></span>](floor-ssis-expression.md)|<span data-ttu-id="2c6d4-120">数値式以下で最大の整数を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-120">Returns the largest integer that is less than or equal to a numeric expression.</span></span>|  
|[<span data-ttu-id="2c6d4-121">LN &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-121">LN &#40;SSIS Expression&#41;</span></span>](ln-ssis-expression.md)|<span data-ttu-id="2c6d4-122">数値式の自然対数を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-122">Returns the natural logarithm of a numeric expression.</span></span>|  
|[<span data-ttu-id="2c6d4-123">LOG &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-123">LOG &#40;SSIS Expression&#41;</span></span>](log-ssis-expression.md)|<span data-ttu-id="2c6d4-124">数値式の常用対数を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-124">Returns the base-10 logarithm of a numeric expression.</span></span>|  
|[<span data-ttu-id="2c6d4-125">POWER &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-125">POWER &#40;SSIS Expression&#41;</span></span>](power-ssis-expression.md)|<span data-ttu-id="2c6d4-126">指定された数値式の結果をべき乗値で返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-126">Returns the result of raising a numeric expression to a power.</span></span>|  
|[<span data-ttu-id="2c6d4-127">ROUND &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-127">ROUND &#40;SSIS Expression&#41;</span></span>](round-ssis-expression.md)|<span data-ttu-id="2c6d4-128">指定された長さまたは有効桁数に丸めた数値式を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-128">Returns a numeric expression that is rounded to the specified length or precision.</span></span> <span data-ttu-id="2c6d4-129">。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-129">.</span></span>|  
|[<span data-ttu-id="2c6d4-130">SIGN &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-130">SIGN &#40;SSIS Expression&#41;</span></span>](sign-ssis-expression.md)|<span data-ttu-id="2c6d4-131">数値式の符号として正 (+)、負 (-)、ゼロ (0) のいずれかを返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-131">Returns the positive (+), negative (-), or zero (0) sign of a numeric expression.</span></span>|  
|[<span data-ttu-id="2c6d4-132">SQUARE &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-132">SQUARE &#40;SSIS Expression&#41;</span></span>](square-ssis-expression.md)|<span data-ttu-id="2c6d4-133">数値式の 2 乗値を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-133">Returns the square of a numeric expression.</span></span>|  
|[<span data-ttu-id="2c6d4-134">SQRT &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-134">SQRT &#40;SSIS Expression&#41;</span></span>](sqrt-ssis-expression.md)|<span data-ttu-id="2c6d4-135">数値式の平方根を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-135">Returns the square root of a numeric expression.</span></span>|  
  
 <span data-ttu-id="2c6d4-136">式エバリュエーターには、次の文字列関数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-136">The expression evaluator provides the following string functions.</span></span>  
  
|<span data-ttu-id="2c6d4-137">Function</span><span class="sxs-lookup"><span data-stu-id="2c6d4-137">Function</span></span>|<span data-ttu-id="2c6d4-138">説明</span><span class="sxs-lookup"><span data-stu-id="2c6d4-138">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="2c6d4-139">CODEPOINT &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-139">CODEPOINT &#40;SSIS Expression&#41;</span></span>](codepoint-ssis-expression.md)|<span data-ttu-id="2c6d4-140">文字式の左端の文字の Unicode コード値を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-140">Returns the Unicode code value of the leftmost character of a character expression.</span></span>|  
|[<span data-ttu-id="2c6d4-141">FINDSTRING &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-141">FINDSTRING &#40;SSIS Expression&#41;</span></span>](findstring-ssis-expression.md)|<span data-ttu-id="2c6d4-142">文字式内のある文字列が指定回数目に検出された場所を、1 を基点とするインデックスで返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-142">Returns the one-based index of the specified occurrence of a character string within an expression.</span></span>|  
|[<span data-ttu-id="2c6d4-143">HEX &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-143">HEX &#40;SSIS Expression&#41;</span></span>](hex-ssis-expression.md)|<span data-ttu-id="2c6d4-144">整数の 16 進値を表す文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-144">Returns a string representing the hexadecimal value of an integer.</span></span>|  
|[<span data-ttu-id="2c6d4-145">LEN &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-145">LEN &#40;SSIS Expression&#41;</span></span>](len-ssis-expression.md)|<span data-ttu-id="2c6d4-146">文字式の文字数を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-146">Returns the number of characters in a character expression.</span></span>|  
|[<span data-ttu-id="2c6d4-147">LEFT &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-147">LEFT &#40;SSIS Expression&#41;</span></span>](left-ssis-expression.md)|<span data-ttu-id="2c6d4-148">指定された文字式の一番左の部分から指定された数の文字を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-148">Returns the specified number of characters from the leftmost portion of the given character expression.</span></span>|  
|[<span data-ttu-id="2c6d4-149">LOWER &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-149">LOWER &#40;SSIS Expression&#41;</span></span>](lower-ssis-expression.md)|<span data-ttu-id="2c6d4-150">大文字が小文字に変換された状態の文字式を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-150">Returns a character expression after converting uppercase characters to lowercase characters.</span></span>|  
|[<span data-ttu-id="2c6d4-151">LTRIM &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-151">LTRIM &#40;SSIS Expression&#41;</span></span>](trim-ssis-expression.md)|<span data-ttu-id="2c6d4-152">先頭のスペースを削除した後の文字式を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-152">Returns a character expression after removing leading spaces.</span></span>|  
|[<span data-ttu-id="2c6d4-153">REPLACE &#40;SSIS &#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-153">REPLACE &#40;SSIS Expression&#41;</span></span>](replace-ssis-expression.md)|<span data-ttu-id="2c6d4-154">式に含まれている文字列を別の文字列または空の文字列で置き換えた文字式を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-154">Returns a character expression after replacing a string within the expression with either a different string or an empty string.</span></span>|  
|[<span data-ttu-id="2c6d4-155">REPLICATE &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-155">REPLICATE &#40;SSIS Expression&#41;</span></span>](replicate-ssis-expression.md)|<span data-ttu-id="2c6d4-156">指定された回数だけレプリケートされた文字式を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-156">Returns a character expression, replicated a specified number of times.</span></span>|  
|[<span data-ttu-id="2c6d4-157">REVERSE &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-157">REVERSE &#40;SSIS Expression&#41;</span></span>](reverse-ssis-expression.md)|<span data-ttu-id="2c6d4-158">文字式を逆に並べ替えたものを返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-158">Returns a character expression in reverse order.</span></span>|  
|[<span data-ttu-id="2c6d4-159">RIGHT &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-159">RIGHT &#40;SSIS Expression&#41;</span></span>](right-ssis-expression.md)|<span data-ttu-id="2c6d4-160">指定された文字式の一番右の部分から指定された数の文字を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-160">Returns the specified number of characters from the rightmost portion of the given character expression.</span></span>|  
|[<span data-ttu-id="2c6d4-161">RTRIM &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-161">RTRIM &#40;SSIS Expression&#41;</span></span>](rtrim-ssis-expression.md)|<span data-ttu-id="2c6d4-162">末尾のスペースを削除した後の文字式を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-162">Returns a character expression after removing trailing spaces.</span></span>|  
|[<span data-ttu-id="2c6d4-163">SUBSTRING &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-163">SUBSTRING &#40;SSIS Expression&#41;</span></span>](substring-ssis-expression.md)|<span data-ttu-id="2c6d4-164">文字式の一部を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-164">Returns a part of a character expression.</span></span>|  
|[<span data-ttu-id="2c6d4-165">TRIM &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-165">TRIM &#40;SSIS Expression&#41;</span></span>](trim-ssis-expression.md)|<span data-ttu-id="2c6d4-166">先頭および末尾のスペースを削除した後の文字式を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-166">Returns a character expression after removing leading and trailing spaces.</span></span>|  
|[<span data-ttu-id="2c6d4-167">UPPER &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-167">UPPER &#40;SSIS Expression&#41;</span></span>](upper-ssis-expression.md)|<span data-ttu-id="2c6d4-168">小文字が大文字に変換された状態の文字式を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-168">Returns a character expression after converting lowercase characters to uppercase characters.</span></span>|  
  
 <span data-ttu-id="2c6d4-169">式エバリュエーターには、次の日付と時刻関数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-169">The expression evaluator provides the following date and time functions.</span></span>  
  
|<span data-ttu-id="2c6d4-170">Function</span><span class="sxs-lookup"><span data-stu-id="2c6d4-170">Function</span></span>|<span data-ttu-id="2c6d4-171">説明</span><span class="sxs-lookup"><span data-stu-id="2c6d4-171">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="2c6d4-172">DATEADD (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="2c6d4-172">DATEADD &#40;SSIS Expression&#41;</span></span>](dateadd-ssis-expression.md)|<span data-ttu-id="2c6d4-173">指定された日付に日付または期間を加えて、新しい DT_DBTIMESTAMP 値を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-173">Returns a new DT_DBTIMESTAMP value by adding a date or time interval to a specified date.</span></span>|  
|[<span data-ttu-id="2c6d4-174">DATEDIFF (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="2c6d4-174">DATEDIFF &#40;SSIS Expression&#41;</span></span>](datediff-ssis-expression.md)|<span data-ttu-id="2c6d4-175">指定された 2 つの日付間の差を、日付および時刻の単位で返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-175">Returns the number of date and time boundaries crossed between two specified dates.</span></span>|  
|[<span data-ttu-id="2c6d4-176">DATEPART (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="2c6d4-176">DATEPART &#40;SSIS Expression&#41;</span></span>](datepart-ssis-expression.md)|<span data-ttu-id="2c6d4-177">ある日付の、特定の日付要素を整数で返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-177">Returns an integer representing a datepart of a date.</span></span>|  
|[<span data-ttu-id="2c6d4-178">DAY (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="2c6d4-178">DAY &#40;SSIS Expression&#41;</span></span>](day-ssis-expression.md)|<span data-ttu-id="2c6d4-179">指定された日付の日を整数で返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-179">Returns an integer that represents the day of the specified date.</span></span>|  
|[<span data-ttu-id="2c6d4-180">GETDATE (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="2c6d4-180">GETDATE &#40;SSIS Expression&#41;</span></span>](getdate-ssis-expression.md)|<span data-ttu-id="2c6d4-181">システムの現在の日付を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-181">Returns the current date of the system.</span></span>|  
|[<span data-ttu-id="2c6d4-182">GETUTCDATE (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="2c6d4-182">GETUTCDATE &#40;SSIS Expression&#41;</span></span>](getutcdate-ssis-expression.md)|<span data-ttu-id="2c6d4-183">システムの現在の日付を UTC 時刻 (協定世界時またはグリニッジ標準時) で返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-183">Returns the current date of the system in UTC time (Universal Time Coordinate or Greenwich Mean Time).</span></span>|  
|[<span data-ttu-id="2c6d4-184">MONTH (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="2c6d4-184">MONTH &#40;SSIS Expression&#41;</span></span>](month-ssis-expression.md)|<span data-ttu-id="2c6d4-185">指定された日付の月を表す整数を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-185">Returns an integer that represents the month of the specified date.</span></span>|  
|[<span data-ttu-id="2c6d4-186">YEAR (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="2c6d4-186">YEAR &#40;SSIS Expression&#41;</span></span>](year-ssis-expression.md)|<span data-ttu-id="2c6d4-187">指定された日付の年を表す整数を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-187">Returns an integer that represents the year of the specified date.</span></span>|  
  
 <span data-ttu-id="2c6d4-188">式エバリュエーターには、次の NULL 関数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-188">The expression evaluator provides the following null functions.</span></span>  
  
|<span data-ttu-id="2c6d4-189">Function</span><span class="sxs-lookup"><span data-stu-id="2c6d4-189">Function</span></span>|<span data-ttu-id="2c6d4-190">説明</span><span class="sxs-lookup"><span data-stu-id="2c6d4-190">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="2c6d4-191">ISNULL &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-191">ISNULL &#40;SSIS Expression&#41;</span></span>](null-ssis-expression.md)|<span data-ttu-id="2c6d4-192">式が NULL かどうかに基づいてブール型の結果を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-192">Returns a Boolean result based on whether an expression is null.</span></span>|  
|[<span data-ttu-id="2c6d4-193">NULL &#40;SSIS 式&#41;</span><span class="sxs-lookup"><span data-stu-id="2c6d4-193">NULL &#40;SSIS Expression&#41;</span></span>](null-ssis-expression.md)|<span data-ttu-id="2c6d4-194">要求されたデータ型の NULL 値を返します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-194">Returns a null value of a requested data type.</span></span>|  
  
 <span data-ttu-id="2c6d4-195">式の名前は大文字で表示されますが、大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-195">Expression names are shown in uppercase characters, but expression names are not case-sensitive.</span></span> <span data-ttu-id="2c6d4-196">たとえば、"null" は "NULL" を使用した場合と同様に機能します。</span><span class="sxs-lookup"><span data-stu-id="2c6d4-196">For example, using "null" works as well as using "NULL".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c6d4-197">参照</span><span class="sxs-lookup"><span data-stu-id="2c6d4-197">See Also</span></span>  
 <span data-ttu-id="2c6d4-198">[演算子 &#40;SSIS 式&#41;](operators-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="2c6d4-198">[Operators &#40;SSIS Expression&#41;](operators-ssis-expression.md) </span></span>  
 <span data-ttu-id="2c6d4-199">[Integration Services 式の詳細の例](examples-of-advanced-integration-services-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="2c6d4-199">[Examples of Advanced Integration Services Expressions](examples-of-advanced-integration-services-expressions.md) </span></span>  
 [<span data-ttu-id="2c6d4-200">Integration Services &#40;SSIS&#41; 式</span><span class="sxs-lookup"><span data-stu-id="2c6d4-200">Integration Services &#40;SSIS&#41; Expressions</span></span>](integration-services-ssis-expressions.md)  
  
  