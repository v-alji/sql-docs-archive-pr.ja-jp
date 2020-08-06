---
title: ネイティブコンパイルストアドプロシージャでサポートされるコンストラクト |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 05515013-28b5-4ccf-9a54-ae861448945b
author: rothja
ms.author: jroth
ms.openlocfilehash: 65e6e794c5858a68c4b2a9b298513911b487cf52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645071"
---
# <a name="supported-constructs-in-natively-compiled-stored-procedures"></a><span data-ttu-id="d20b0-102">ネイティブ コンパイル ストアド プロシージャ内でサポートされる構造</span><span class="sxs-lookup"><span data-stu-id="d20b0-102">Supported Constructs in Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="d20b0-103">このトピックには、ネイティブコンパイルストアドプロシージャでサポートされている機能の一覧が含まれています ([CREATE PROCEDURE &#40;transact-sql&#41;](/sql/t-sql/statements/create-procedure-transact-sql))。</span><span class="sxs-lookup"><span data-stu-id="d20b0-103">This topic contains a list of supported features for natively compiled stored procedures ([CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)):</span></span>  
  
-   [<span data-ttu-id="d20b0-104">ネイティブ コンパイル ストアド プロシージャでのプログラミング機能</span><span class="sxs-lookup"><span data-stu-id="d20b0-104">Programmability in Natively Compiled Stored Procedures</span></span>](#pncsp)  
  
-   [<span data-ttu-id="d20b0-105">サポートされる演算子</span><span class="sxs-lookup"><span data-stu-id="d20b0-105">Supported Operators</span></span>](#so)  
  
-   [<span data-ttu-id="d20b0-106">ネイティブ コンパイル ストアド プロシージャでの組み込み関数</span><span class="sxs-lookup"><span data-stu-id="d20b0-106">Built-in Functions in Natively Compiled Stored Procedures</span></span>](#bfncsp)  
  
-   [<span data-ttu-id="d20b0-107">ネイティブ コンパイル ストアド プロシージャでのクエリ対象領域</span><span class="sxs-lookup"><span data-stu-id="d20b0-107">Query Surface Area in Natively Compiled Stored Procedures</span></span>](#qsancsp)  
  
-   [<span data-ttu-id="d20b0-108">監査</span><span class="sxs-lookup"><span data-stu-id="d20b0-108">Auditing</span></span>](#auditing)  
  
-   [<span data-ttu-id="d20b0-109">テーブル ヒント、クエリ ヒント、および結合ヒント</span><span class="sxs-lookup"><span data-stu-id="d20b0-109">Table, Query, and Join Hints</span></span>](#tqh)  
  
-   [<span data-ttu-id="d20b0-110">並べ替えに関する制限事項</span><span class="sxs-lookup"><span data-stu-id="d20b0-110">Limitations on Sorting</span></span>](#los)  
  
 <span data-ttu-id="d20b0-111">ネイティブ コンパイル ストアド プロシージャでサポートされるデータ型については、「 [Supported Data Types](supported-data-types-for-in-memory-oltp.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d20b0-111">For information on data types supported in natively compiled stored procedures, see [Supported Data Types](supported-data-types-for-in-memory-oltp.md).</span></span>  
  
 <span data-ttu-id="d20b0-112">サポートされない構造に関する詳細と、ネイティブ コンパイル ストアド プロシージャのサポートされない一部の機能に対処する方法については、「 [Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d20b0-112">For complete information about unsupported constructs, and for information about how to work around some of the unsupported features in natively compiled stored procedures, see [Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md).</span></span> <span data-ttu-id="d20b0-113">サポートされていない機能の詳細については、「 [インメモリ OLTP でサポートされていない Transact-SQL の構造](transact-sql-constructs-not-supported-by-in-memory-oltp.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d20b0-113">For more information about unsupported features, see [Transact-SQL Constructs Not Supported by In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md).</span></span>  
  
##  <a name="programmability-in-natively-compiled-stored-procedures"></a><a name="pncsp"></a><span data-ttu-id="d20b0-114">ネイティブコンパイルストアドプロシージャでのプログラミング</span><span class="sxs-lookup"><span data-stu-id="d20b0-114">Programmability in Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="d20b0-115">サポート対象は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d20b0-115">The following are supported:</span></span>  
  
-   <span data-ttu-id="d20b0-116">BEGIN ATOMIC (ストアド プロシージャの外部レベル)、LANGUAGE、ISOLATION LEVEL、DATEFORMAT、および DATEFIRST。</span><span class="sxs-lookup"><span data-stu-id="d20b0-116">BEGIN ATOMIC (at the outer level of the stored procedure), LANGUAGE, ISOLATION LEVEL, DATEFORMAT, and DATEFIRST.</span></span>  
  
-   <span data-ttu-id="d20b0-117">NULL または NOT NULL としての変数の宣言。</span><span class="sxs-lookup"><span data-stu-id="d20b0-117">Declaring variables as NULL or NOT NULL.</span></span> <span data-ttu-id="d20b0-118">変数が NOT NULL として宣言されている場合、宣言には初期化子が必要です。</span><span class="sxs-lookup"><span data-stu-id="d20b0-118">If a variable is declared as NOT NULL, the declaration must have an initializer.</span></span> <span data-ttu-id="d20b0-119">変数が NOT NULL として宣言されていない場合、初期化子は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="d20b0-119">If a variable is not declared as NOT NULL, an initializer is optional.</span></span>  
  
-   <span data-ttu-id="d20b0-120">IF と WHILE</span><span class="sxs-lookup"><span data-stu-id="d20b0-120">IF and WHILE</span></span>  
  
-   <span data-ttu-id="d20b0-121">INSERT/UPDATE/DELETE</span><span class="sxs-lookup"><span data-stu-id="d20b0-121">INSERT/UPDATE/DELETE</span></span>  
  
     <span data-ttu-id="d20b0-122">サブクエリはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d20b0-122">Subqueries are not supported.</span></span> <span data-ttu-id="d20b0-123">WHERE または HAVING 句では、AND および BETWEEN がサポートされています。OR、NOT、および IN はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d20b0-123">In the WHERE or HAVING clause, AND and BETWEEN are supported; OR, NOT, and IN are not supported.</span></span>  
  
-   <span data-ttu-id="d20b0-124">メモリ最適化テーブル型とテーブル変数。</span><span class="sxs-lookup"><span data-stu-id="d20b0-124">Memory-optimized table types and table variables.</span></span>  
  
-   <span data-ttu-id="d20b0-125">RETURN</span><span class="sxs-lookup"><span data-stu-id="d20b0-125">RETURN</span></span>  
  
-   <span data-ttu-id="d20b0-126">SELECT</span><span class="sxs-lookup"><span data-stu-id="d20b0-126">SELECT</span></span>  
  
-   <span data-ttu-id="d20b0-127">SET</span><span class="sxs-lookup"><span data-stu-id="d20b0-127">SET</span></span>  
  
-   <span data-ttu-id="d20b0-128">TRY/CATCH/THROW</span><span class="sxs-lookup"><span data-stu-id="d20b0-128">TRY/CATCH/THROW</span></span>  
  
     <span data-ttu-id="d20b0-129">パフォーマンスを最適化するには、ネイティブ コンパイル ストアド プロシージャ全体に対して 1 つの TRY/CATCH ブロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="d20b0-129">To optimize performance, use a single TRY/CATCH block for an entire natively compiled stored procedure.</span></span>  
  
##  <a name="supported-operators"></a><a name="so"></a> <span data-ttu-id="d20b0-130">サポートされている演算子</span><span class="sxs-lookup"><span data-stu-id="d20b0-130">Supported Operators</span></span>  
 <span data-ttu-id="d20b0-131">サポートされている演算子は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d20b0-131">The following operators are supported.</span></span>  
  
-   <span data-ttu-id="d20b0-132">[Transact-sql&#41;&#40;の比較演算子](/sql/t-sql/language-elements/comparison-operators-transact-sql)(たとえば、>、 \<, > =、および <=) は、条件 (IF、WHILE) でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d20b0-132">[Comparison Operators &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/comparison-operators-transact-sql) (for example, >, \<, >=, and <=) are supported in conditionals (IF, WHILE).</span></span>  
  
-   <span data-ttu-id="d20b0-133">単項演算子 (+、-)。</span><span class="sxs-lookup"><span data-stu-id="d20b0-133">Unary operators (+, -).</span></span>  
  
-   <span data-ttu-id="d20b0-134">二項演算子 (\*、/、+、-、% (剰余))。</span><span class="sxs-lookup"><span data-stu-id="d20b0-134">Binary operators (\*, /, +, -, % (modulo)).</span></span>  
  
     <span data-ttu-id="d20b0-135">プラス演算子 (+) は、数値と文字列の両方でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d20b0-135">The plus operator (+) is supported on both numbers and strings.</span></span>  
  
-   <span data-ttu-id="d20b0-136">論理演算子 (AND、OR、NOT)。</span><span class="sxs-lookup"><span data-stu-id="d20b0-136">Logical operators (AND, OR, NOT).</span></span> <span data-ttu-id="d20b0-137">OR および NOT は、IF および WHILE ステートメントではサポートされていますが、WHERE または HAVING 句ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d20b0-137">OR and NOT are supported in IF and WHILE statements but not in WHERE or HAVING clauses.</span></span>  
  
-   <span data-ttu-id="d20b0-138">ビット演算子 ~、&、|、および ^</span><span class="sxs-lookup"><span data-stu-id="d20b0-138">Bitwise operators ~, &, |, and ^</span></span>  
  
##  <a name="built-in-functions-in-natively-compiled-stored-procedures"></a><a name="bfncsp"></a><span data-ttu-id="d20b0-139">ネイティブコンパイルストアドプロシージャの組み込み関数</span><span class="sxs-lookup"><span data-stu-id="d20b0-139">Built-in Functions in Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="d20b0-140">メモリ最適化テーブルの既定構造とネイティブ コンパイル ストアド プロシージャでは、次の関数がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="d20b0-140">The following functions are supported in default constraints on memory-optimized tables and in natively compiled stored procedures.</span></span>  
  
-   <span data-ttu-id="d20b0-141">数学関数: ACOS、ASIN、ATAN、ATN2、COS、COT、DEGREES、EXP、LOG、LOG10、PI、POWER、RADIANS、RAND、SIN、SQRT、SQUARE、および TAN</span><span class="sxs-lookup"><span data-stu-id="d20b0-141">Math Functions: ACOS, ASIN, ATAN, ATN2, COS, COT, DEGREES, EXP, LOG, LOG10, PI, POWER, RADIANS, RAND, SIN, SQRT, SQUARE, and TAN</span></span>  
  
-   <span data-ttu-id="d20b0-142">日付関数: CURRENT_TIMESTAMP、DATEADD、DATEDIFF、DATEFROMPARTS、DATEPART、DATETIME2FROMPARTS、DATETIMEFROMPARTS、DAY、EOMONTH、GETDATE、GETUTCDATE、MONTH、SMALLDATETIMEFROMPARTS、SYSDATETIME、SYSUTCDATETIME、および YEAR</span><span class="sxs-lookup"><span data-stu-id="d20b0-142">Date Functions: CURRENT_TIMESTAMP, DATEADD, DATEDIFF, DATEFROMPARTS, DATEPART, DATETIME2FROMPARTS, DATETIMEFROMPARTS, DAY, EOMONTH, GETDATE, GETUTCDATE, MONTH, SMALLDATETIMEFROMPARTS, SYSDATETIME, SYSUTCDATETIME, and YEAR.</span></span>  
  
-   <span data-ttu-id="d20b0-143">文字列関数: LEN、LTRIM、RTRIM、および SUBSTRING</span><span class="sxs-lookup"><span data-stu-id="d20b0-143">String Functions: LEN, LTRIM, RTRIM, and SUBSTRING</span></span>  
  
-   <span data-ttu-id="d20b0-144">ID 関数: SCOPE_IDENTITY</span><span class="sxs-lookup"><span data-stu-id="d20b0-144">Identity Function: SCOPE_IDENTITY</span></span>  
  
-   <span data-ttu-id="d20b0-145">NULL 関数: ISNULL</span><span class="sxs-lookup"><span data-stu-id="d20b0-145">NULL functions: ISNULL</span></span>  
  
-   <span data-ttu-id="d20b0-146">一意識別子関数: NEWID および NEWSEQUENTIALID</span><span class="sxs-lookup"><span data-stu-id="d20b0-146">Uniqueidentifier functions: NEWID and NEWSEQUENTIALID</span></span>  
  
-   <span data-ttu-id="d20b0-147">エラー関数: ERROR_LINE、ERROR_MESSAGE、ERROR_NUMBER、ERROR_PROCEDURE、ERROR_SEVERITY、および ERROR_STATE</span><span class="sxs-lookup"><span data-stu-id="d20b0-147">Error Functions: ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY, and ERROR_STATE</span></span>  
  
-   <span data-ttu-id="d20b0-148">変換: CAST および CONVERT。</span><span class="sxs-lookup"><span data-stu-id="d20b0-148">Conversions: CAST and CONVERT.</span></span> <span data-ttu-id="d20b0-149">Unicode 文字と非 Unicode 文字の文字列 (n(var)char および (var)char) の間の変換はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d20b0-149">Conversions between Unicode and non-Unicode character strings (n(var)char and (var)char) are not supported.</span></span>  
  
-   <span data-ttu-id="d20b0-150">システム関数: @@rowcount。</span><span class="sxs-lookup"><span data-stu-id="d20b0-150">System Functions: @@rowcount.</span></span> <span data-ttu-id="d20b0-151">ネイティブ コンパイル ストアド プロシージャ内のステートメントによって、@@rowcount が更新されます。ネイティブ コンパイル ストアド プロシージャ内で @@rowcount を使用し、ネイティブ コンパイル ストアド プロシージャ内で実行された最後のステートメントによる影響を受けた行の数を決定することができます。</span><span class="sxs-lookup"><span data-stu-id="d20b0-151">Statements inside natively compiled stored procedures update @@rowcount and you can use @@rowcount in a natively compiled stored procedure to determine the number of rows affected by the last statement executed within that natively compiled stored procedure.</span></span> <span data-ttu-id="d20b0-152">ただし、ネイティブ コンパイル ストアド プロシージャの実行の開始時および終了時に、@@rowcount は 0 にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="d20b0-152">However, @@rowcount is reset to 0 at the start and at the end of the execution of a natively compiled stored procedure.</span></span>  
  
##  <a name="query-surface-area-in-natively-compiled-stored-procedures"></a><a name="qsancsp"></a><span data-ttu-id="d20b0-153">ネイティブコンパイルストアドプロシージャのクエリ領域</span><span class="sxs-lookup"><span data-stu-id="d20b0-153">Query Surface Area in Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="d20b0-154">サポート対象は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d20b0-154">The following are supported:</span></span>  
  
-   <span data-ttu-id="d20b0-155">BETWEEN</span><span class="sxs-lookup"><span data-stu-id="d20b0-155">BETWEEN</span></span>  
  
-   <span data-ttu-id="d20b0-156">列名のエイリアス (AS または = 構文を使用)。</span><span class="sxs-lookup"><span data-stu-id="d20b0-156">Column name aliases (using either AS or = syntax).</span></span>  
  
-   <span data-ttu-id="d20b0-157">CROSS JOIN と INNER JOIN は、SELECT クエリでのみサポート。</span><span class="sxs-lookup"><span data-stu-id="d20b0-157">CROSS JOIN and INNER JOIN, supported only with SELECT queries.</span></span>  
  
-   <span data-ttu-id="d20b0-158">SELECT リストでは式がサポートされていますが、サポートされている演算子を使用する場合は、 [transact-sql&#41;句 &#40;](/sql/t-sql/queries/where-transact-sql)ます。</span><span class="sxs-lookup"><span data-stu-id="d20b0-158">Expressions are supported in SELECT list and [WHERE &#40;Transact-SQL&#41;](/sql/t-sql/queries/where-transact-sql) clause if they use a supported operator.</span></span> <span data-ttu-id="d20b0-159">現在サポートされている演算子の一覧については、「 [Supported Operators](#so) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d20b0-159">See [Supported Operators](#so) for the list of currently-supported operators.</span></span>  
  
-   <span data-ttu-id="d20b0-160">フィルター述語 IS [NOT] NULL</span><span class="sxs-lookup"><span data-stu-id="d20b0-160">Filter predicate IS [NOT] NULL</span></span>  
  
-   <span data-ttu-id="d20b0-161">FROM \<memory optimized table></span><span class="sxs-lookup"><span data-stu-id="d20b0-161">FROM \<memory optimized table></span></span>  
  
-   <span data-ttu-id="d20b0-162">[GROUP BY &#40;transact-sql&#41;](/sql/t-sql/queries/select-group-by-transact-sql)は、集計関数の AVG、COUNT、COUNT_BIG、MIN、MAX、および SUM と共にサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d20b0-162">[GROUP BY &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-group-by-transact-sql) is supported, along with the aggregate functions AVG, COUNT, COUNT_BIG, MIN, MAX, and SUM.</span></span> <span data-ttu-id="d20b0-163">MIN および MAX は、nvarchar、char、varchar、varchar、varbinary、および binary 型ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d20b0-163">MIN and MAX are not supported for types nvarchar, char, varchar, varchar, varbinary, and binary.</span></span> <span data-ttu-id="d20b0-164">Order by[句 &#40;transact-sql&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql)は group by &#40;でサポートされています。 order by リスト内の式が group by リストにそのまま表示される場合は、 [transact-sql&#41;](/sql/t-sql/queries/select-group-by-transact-sql)を使用します。</span><span class="sxs-lookup"><span data-stu-id="d20b0-164">[ORDER BY Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql) is supported with [GROUP BY &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-group-by-transact-sql) if an expression in the ORDER BY list appears verbatim in the GROUP BY list.</span></span> <span data-ttu-id="d20b0-165">たとえば、GROUP BY a + b ORDER BY a + b はサポートされますが、GROUP BY a, b ORDER BY a + b はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d20b0-165">For example, GROUP BY a + b ORDER BY a + b is supported, but GROUP BY a, b ORDER BY a + b is not.</span></span>  
  
-   <span data-ttu-id="d20b0-166">HAVING (WHERE 句と同じ式の制限が適用されます)。</span><span class="sxs-lookup"><span data-stu-id="d20b0-166">HAVING, subject to the same expression limitations as the WHERE clause.</span></span>  
  
-   <span data-ttu-id="d20b0-167">INSERT VALUES (ステートメントごとに 1 行) と INSERT SELECT</span><span class="sxs-lookup"><span data-stu-id="d20b0-167">INSERT VALUES (one row per statement) and INSERT SELECT</span></span>  
  
-   <span data-ttu-id="d20b0-168">ORDER BY <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d20b0-168">ORDER BY <sup>1</sup></span></span>  
  
-   <span data-ttu-id="d20b0-169">列を参照しない述語。</span><span class="sxs-lookup"><span data-stu-id="d20b0-169">Predicates not referencing a column.</span></span>  
  
-   <span data-ttu-id="d20b0-170">SELECT、UPDATE、および DELETE</span><span class="sxs-lookup"><span data-stu-id="d20b0-170">SELECT, UPDATE, and DELETE</span></span>  
  
-   <span data-ttu-id="d20b0-171">上位<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d20b0-171">TOP <sup>1</sup></span></span>  
  
-   <span data-ttu-id="d20b0-172">SELECT リストでの変数代入。</span><span class="sxs-lookup"><span data-stu-id="d20b0-172">Variable assignment in the SELECT list.</span></span>  
  
-   <span data-ttu-id="d20b0-173">どこ。。。そして</span><span class="sxs-lookup"><span data-stu-id="d20b0-173">WHERE ... AND</span></span>  
  
 <span data-ttu-id="d20b0-174"><sup>1</sup> ORDER BY と TOP はネイティブコンパイルストアドプロシージャでサポートされていますが、いくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="d20b0-174"><sup>1</sup> ORDER BY and TOP are supported in natively compiled stored procedures, with some restrictions:</span></span>  
  
-   <span data-ttu-id="d20b0-175">`DISTINCT` 句または `SELECT` 句での `ORDER BY` のサポートはありません。</span><span class="sxs-lookup"><span data-stu-id="d20b0-175">There is no support for `DISTINCT` in the `SELECT` or `ORDER BY` clause.</span></span>  
  
-   <span data-ttu-id="d20b0-176">`WITH TIES` 句での `PERCENT` または `TOP` のサポートはありません。</span><span class="sxs-lookup"><span data-stu-id="d20b0-176">There is no support for `WITH TIES` or `PERCENT` in the `TOP` clause.</span></span>  
  
-   <span data-ttu-id="d20b0-177">`TOP` と `ORDER BY` の組み合わせでは、`TOP` 句内で定数を使用するときに 8,192 を超える値はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d20b0-177">`TOP` combined with `ORDER BY` does not support more than 8,192 when using a constant in the `TOP` clause.</span></span> <span data-ttu-id="d20b0-178">クエリに結合または集計関数が含まれている場合は、この制限値がさらに小さくなる場合があります</span><span class="sxs-lookup"><span data-stu-id="d20b0-178">This limit may be lowered in case the query contains joins or aggregate functions.</span></span> <span data-ttu-id="d20b0-179">(たとえば、1 回の結合 (2 つのテーブル) では、制限値は 4,096 行です。</span><span class="sxs-lookup"><span data-stu-id="d20b0-179">(For example, with one join (two tables), the limit is 4,096 rows.</span></span> <span data-ttu-id="d20b0-180">2 回の結合 (3 つのテーブル) では、制限値は 2,730 行です)。</span><span class="sxs-lookup"><span data-stu-id="d20b0-180">With two joins (three tables), the limit is 2,730 rows.)</span></span>  
  
     <span data-ttu-id="d20b0-181">変数内に行の数を格納すると、8,192 より多くの結果を取得できます。</span><span class="sxs-lookup"><span data-stu-id="d20b0-181">You can obtain results greater than 8,192 by storing the number of rows in a variable:</span></span>  
  
    ```sql  
    DECLARE @v INT = 9000  
    SELECT TOP (@v) ... FROM ... ORDER BY ...  
    ```  
  
 <span data-ttu-id="d20b0-182">ただし、変数を使用する場合に比べて、`TOP` 句内で定数を使用する方がパフォーマンスが向上する結果になります。</span><span class="sxs-lookup"><span data-stu-id="d20b0-182">However, a constant in the `TOP` clause results in better performance compared to using a variable.</span></span>  
  
 <span data-ttu-id="d20b0-183">これらの制限は、インタープリターによって処理される [!INCLUDE[tsql](../../includes/tsql-md.md)] によるメモリ最適化テーブルへのアクセスには適用されません。</span><span class="sxs-lookup"><span data-stu-id="d20b0-183">These restrictions do not apply to interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] access on memory-optimized tables.</span></span>  
  
##  <a name="auditing"></a><a name="auditing"></a> <span data-ttu-id="d20b0-184">監査</span><span class="sxs-lookup"><span data-stu-id="d20b0-184">Auditing</span></span>  
 <span data-ttu-id="d20b0-185">プロシージャ レベルの監査はネイティブ コンパイル ストアド プロシージャでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d20b0-185">Procedure level auditing is supported in natively compiled stored procedures.</span></span> <span data-ttu-id="d20b0-186">ステートメント レベルの監査はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d20b0-186">Statement level auditing is not supported.</span></span>  
  
 <span data-ttu-id="d20b0-187">監査の詳細については、「 [サーバー監査の仕様およびデータベース監査の仕様を作成する方法](../security/auditing/create-a-server-audit-and-database-audit-specification.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d20b0-187">For more information about auditing, see [Create a Server Audit and Database Audit Specification](../security/auditing/create-a-server-audit-and-database-audit-specification.md).</span></span>  
  
##  <a name="table-query-and-join-hints"></a><a name="tqh"></a><span data-ttu-id="d20b0-188">テーブル、クエリ、および結合ヒント</span><span class="sxs-lookup"><span data-stu-id="d20b0-188">Table, Query, and Join Hints</span></span>  
 <span data-ttu-id="d20b0-189">サポート対象は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d20b0-189">The following are supported:</span></span>  
  
-   <span data-ttu-id="d20b0-190">テーブル ヒント構文またはクエリの [OPTION 句 &#40;Transact-SQL&#41;](/sql/t-sql/queries/option-clause-transact-sql) での INDEX、FORCESCAN、および FORCESEEK ヒント。</span><span class="sxs-lookup"><span data-stu-id="d20b0-190">INDEX, FORCESCAN, and FORCESEEK hints, either in table hints syntax or in [OPTION Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/option-clause-transact-sql) of the query.</span></span>  
  
-   <span data-ttu-id="d20b0-191">FORCE ORDER</span><span class="sxs-lookup"><span data-stu-id="d20b0-191">FORCE ORDER</span></span>  
  
-   <span data-ttu-id="d20b0-192">INNER LOOP JOIN</span><span class="sxs-lookup"><span data-stu-id="d20b0-192">INNER LOOP JOIN</span></span>  
  
-   <span data-ttu-id="d20b0-193">OPTIMIZE FOR</span><span class="sxs-lookup"><span data-stu-id="d20b0-193">OPTIMIZE FOR</span></span>  
  
 <span data-ttu-id="d20b0-194">詳細については、「 [transact-sql&#41;&#40;ヒント](/sql/t-sql/queries/hints-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d20b0-194">For more information, see [Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql).</span></span>  
  
##  <a name="limitations-on-sorting"></a><a name="los"></a> <span data-ttu-id="d20b0-195">並べ替えに関する制限事項</span><span class="sxs-lookup"><span data-stu-id="d20b0-195">Limitations on Sorting</span></span>  
 <span data-ttu-id="d20b0-196">[TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) および [ORDER BY 句 &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql) を使用するクエリでは、8,000 を超える行の並べ替えを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="d20b0-196">You can sort greater than 8,000 rows in a query that uses [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) and an [ORDER BY Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql).</span></span> <span data-ttu-id="d20b0-197">ただし、[ORDER BY 句 &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql) を使用しない場合、[TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) で並べ替えができる行数は最大で 8,000 です (結合がある場合は、より少ない行数になります)。</span><span class="sxs-lookup"><span data-stu-id="d20b0-197">However, without [ORDER BY Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql), [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) can sort up to 8,000 rows (fewer rows if there are joins).</span></span>  
  
 <span data-ttu-id="d20b0-198">クエリが [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) 演算子および [ORDER BY 句 &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql) を使用する場合、TOP 演算子には 8192 行まで指定できます。</span><span class="sxs-lookup"><span data-stu-id="d20b0-198">If your query uses both the [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) operator and an [ORDER BY Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql), you can specify up to 8192 rows for the TOP operator.</span></span> <span data-ttu-id="d20b0-199">8192 行を超える行を指定すると、エラー メッセージが表示されます: **メッセージ 41398、レベル 16、状態 1、プロシージャ *\<procedureName>* 、行 *\<lineNumber>* TOP 演算子は、最大 8192 行を返すことができます。 *\<number>* が要求されました。**</span><span class="sxs-lookup"><span data-stu-id="d20b0-199">If you specify more than 8192 rows you get the error message: **Msg 41398, Level 16, State 1, Procedure *\<procedureName>*, Line *\<lineNumber>* The TOP operator can return a maximum of 8192 rows; *\<number>* was requested.**</span></span>  
  
 <span data-ttu-id="d20b0-200">TOP 句がない場合は、ORDER BY で任意の数の行を並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="d20b0-200">If you do not have a TOP clause, you can sort any number of rows with ORDER BY.</span></span>  
  
 <span data-ttu-id="d20b0-201">ORDER BY 句を使用しない場合、TOP 演算子と共に任意の整数値を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d20b0-201">If you do not use an ORDER BY clause, you can use any integer value with the TOP operator.</span></span>  
  
 <span data-ttu-id="d20b0-202">TOP N = 8192 の例: コンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="d20b0-202">Example with TOP N = 8192: Compiles</span></span>  
  
```sql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8192 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 <span data-ttu-id="d20b0-203">TOP N > 8192 の例: コンパイルできません。</span><span class="sxs-lookup"><span data-stu-id="d20b0-203">Example with TOP N > 8192: Fails to compile.</span></span>  
  
```sql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8193 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 <span data-ttu-id="d20b0-204">8192 行の制限は、 `TOP N` が定数の場合に、前の例のように、 `N` にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="d20b0-204">The 8192 row limitation only applies to `TOP N` where `N` is a constant, as in the preceding examples.</span></span>  <span data-ttu-id="d20b0-205">8192 より大きな `N` が必要である場合は、値を変数に割り当て、 `TOP`と共にその変数を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="d20b0-205">If you need `N` greater than 8192 you can assign the value to a variable and use that variable with `TOP`.</span></span>  
  
 <span data-ttu-id="d20b0-206">変数を使用した例: コンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="d20b0-206">Example using a variable: Compiles</span></span>  
  
```sql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    DECLARE @v int = 8193   
    SELECT TOP (@v) ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 <span data-ttu-id="d20b0-207">**返される行に関する制限事項:** TOP 演算子から返される行数を減らせる可能性がある場合が 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="d20b0-207">**Limitations on rows returned:** There are two cases where that can potentially reduce the number of rows that can be returned by the TOP operator:</span></span>  
  
-   <span data-ttu-id="d20b0-208">クエリで JOIN を使用します。</span><span class="sxs-lookup"><span data-stu-id="d20b0-208">Using JOINs in the query.</span></span>  <span data-ttu-id="d20b0-209">制限における JOIN の影響は、クエリ プランによって異なります。</span><span class="sxs-lookup"><span data-stu-id="d20b0-209">The influence of JOINs on the limitation depends on the query plan.</span></span>  
  
-   <span data-ttu-id="d20b0-210">ORDER BY 句で集計関数または集計関数への参照を使用する。</span><span class="sxs-lookup"><span data-stu-id="d20b0-210">Using aggregate functions or references to aggregate functions in the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="d20b0-211">TOP N での最悪のケースでサポートされる最大 N を計算する式は次のとおりです: `N = floor ( 65536 / number_of_tables * 8 + total_size+of+aggs )`。</span><span class="sxs-lookup"><span data-stu-id="d20b0-211">The formula to calculate a worst case maximum supported N in TOP N is: `N = floor ( 65536 / number_of_tables * 8 + total_size+of+aggs )`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d20b0-212">参照</span><span class="sxs-lookup"><span data-stu-id="d20b0-212">See Also</span></span>  
 <span data-ttu-id="d20b0-213">[ネイティブ コンパイル ストアド プロシージャ](natively-compiled-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="d20b0-213">[Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md) </span></span>  
 [<span data-ttu-id="d20b0-214">ネイティブ コンパイル ストアド プロシージャの移行に関する問題</span><span class="sxs-lookup"><span data-stu-id="d20b0-214">Migration Issues for Natively Compiled Stored Procedures</span></span>](migration-issues-for-natively-compiled-stored-procedures.md)  
  
  
