---
title: 計算列のインデックス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- computed columns, index creation
- index creation [SQL Server], computed columns
- imprecise columns
- persisted computed columns
- precise [SQL Server]
ms.assetid: 8d17ac9c-f3af-4bbb-9cc1-5cf647e994c4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2ecbca9e7838c4c9395a8bcb6e11351c40f7037f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742061"
---
# <a name="indexes-on-computed-columns"></a><span data-ttu-id="cc549-102">計算列のインデックス</span><span class="sxs-lookup"><span data-stu-id="cc549-102">Indexes on Computed Columns</span></span>
  <span data-ttu-id="cc549-103">次の要件を満たしている限り、計算列にインデックスを定義できます。</span><span class="sxs-lookup"><span data-stu-id="cc549-103">You can define indexes on computed columns as long as the following requirements are met:</span></span>  
  
-   <span data-ttu-id="cc549-104">所有権の要件</span><span class="sxs-lookup"><span data-stu-id="cc549-104">Ownership requirements</span></span>  
  
-   <span data-ttu-id="cc549-105">決定性の要件</span><span class="sxs-lookup"><span data-stu-id="cc549-105">Determinism requirements</span></span>  
  
-   <span data-ttu-id="cc549-106">正確さの要件</span><span class="sxs-lookup"><span data-stu-id="cc549-106">Precision requirements</span></span>  
  
-   <span data-ttu-id="cc549-107">データ型の要件</span><span class="sxs-lookup"><span data-stu-id="cc549-107">Data type requirements</span></span>  
  
-   <span data-ttu-id="cc549-108">SET オプションの要件</span><span class="sxs-lookup"><span data-stu-id="cc549-108">SET option requirements</span></span>  
  
 <span data-ttu-id="cc549-109">**Ownership Requirements**</span><span class="sxs-lookup"><span data-stu-id="cc549-109">**Ownership Requirements**</span></span>  
  
 <span data-ttu-id="cc549-110">計算列のすべての関数参照の所有者がテーブルの所有者と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc549-110">All function references in the computed column must have the same owner as the table.</span></span>  
  
 <span data-ttu-id="cc549-111">**Determinism Requirements**</span><span class="sxs-lookup"><span data-stu-id="cc549-111">**Determinism Requirements**</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cc549-112">指定された一連の入力に対して式から必ず同じ結果が返される場合、その式は決定的です。</span><span class="sxs-lookup"><span data-stu-id="cc549-112">Expressions are deterministic if they always return the same result for a specified set of inputs.</span></span> <span data-ttu-id="cc549-113">**COLUMNPROPERTY** 関数の [IsDeterministic](/sql/t-sql/functions/columnproperty-transact-sql) プロパティは、 *computed_column_expression* が決定的であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="cc549-113">The **IsDeterministic** property of the [COLUMNPROPERTY](/sql/t-sql/functions/columnproperty-transact-sql) function reports whether a *computed_column_expression* is deterministic.</span></span>  
  
 <span data-ttu-id="cc549-114">*computed_column_expression* は、決定的である必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc549-114">The *computed_column_expression* must be deterministic.</span></span> <span data-ttu-id="cc549-115">次の 1 つ以上の条件に該当する場合、 *computed_column_expression* は決定的です。</span><span class="sxs-lookup"><span data-stu-id="cc549-115">A *computed_column_expression* is deterministic when one or more of the following is true:</span></span>  
  
-   <span data-ttu-id="cc549-116">式で参照される関数が決定的かつ正確である場合。</span><span class="sxs-lookup"><span data-stu-id="cc549-116">All functions that are referenced by the expression are deterministic and precise.</span></span> <span data-ttu-id="cc549-117">このような関数には、ユーザー定義関数と組み込み関数の両方があります。</span><span class="sxs-lookup"><span data-stu-id="cc549-117">These functions include both user-defined and built-in functions.</span></span> <span data-ttu-id="cc549-118">詳細については、「 [決定的関数と非決定的関数](../user-defined-functions/deterministic-and-nondeterministic-functions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc549-118">For more information, see [Deterministic and Nondeterministic Functions](../user-defined-functions/deterministic-and-nondeterministic-functions.md).</span></span> <span data-ttu-id="cc549-119">計算列が PERSISTED の場合、関数は不正確になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cc549-119">Functions might be imprecise if the computed column is PERSISTED.</span></span> <span data-ttu-id="cc549-120">詳細については、このトピックの後半の「 [保存される計算列でのインデックスの作成](#BKMK_persisted) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc549-120">For more information, see [Creating Indexes on Persisted Computed Columns](#BKMK_persisted) later in this topic.</span></span>  
  
-   <span data-ttu-id="cc549-121">式で参照されるすべての列が計算列を含むテーブルの列である場合。</span><span class="sxs-lookup"><span data-stu-id="cc549-121">All columns that are referenced in the expression come from the table that contains the computed column.</span></span>  
  
-   <span data-ttu-id="cc549-122">列参照が複数の行からデータを取り出していない場合。</span><span class="sxs-lookup"><span data-stu-id="cc549-122">No column reference pulls data from multiple rows.</span></span> <span data-ttu-id="cc549-123">たとえば、SUM や AVG などの集計関数は複数の行のデータに依存して計算を行うので、 *computed_column_expression* は非決定的になります。</span><span class="sxs-lookup"><span data-stu-id="cc549-123">For example, aggregate functions such as SUM or AVG depend on data from multiple rows and would make a *computed_column_expression* nondeterministic.</span></span>  
  
-   <span data-ttu-id="cc549-124">*computed_column_expression* がシステム データ アクセスやユーザー データ アクセスを伴わない場合。</span><span class="sxs-lookup"><span data-stu-id="cc549-124">The *computed_column_expression* has no system data access or user data access.</span></span>  
  
 <span data-ttu-id="cc549-125">共通言語ランタイム (CLR) 式を含むすべての計算列は決定的であり、インデックスを作成する前に PERSISTED に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc549-125">Any computed column that contains a common language runtime (CLR) expression must be deterministic and marked PERSISTED before the column can be indexed.</span></span> <span data-ttu-id="cc549-126">CLR ユーザー定義型の式を、計算列の定義に使用できます。</span><span class="sxs-lookup"><span data-stu-id="cc549-126">CLR user-defined type expressions are allowed in computed column definitions.</span></span> <span data-ttu-id="cc549-127">計算列の型が CLR ユーザー定義型の場合、その型が比較可能である限り、計算列にインデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="cc549-127">Computed columns whose type is a CLR user-defined type can be indexed as long as the type is comparable.</span></span> <span data-ttu-id="cc549-128">詳細については、「 [CLR ユーザー定義型](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc549-128">For more information, see [CLR User-Defined Types](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cc549-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインデックス付き計算列で日付データ型の文字列リテラルを参照するときは、決定的な日付形式スタイルを使用して、そのリテラルを目的の日付型に明示的に変換することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cc549-129">When you refer to string literals of the date data type in indexed computed columns in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], we recommend that you explicitly convert the literal to the date type that you want by using a deterministic date format style.</span></span> <span data-ttu-id="cc549-130">決定的な日付形式の一覧については、「 [CAST および CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc549-130">For a list of the date format styles that are deterministic, see [CAST and CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span> <span data-ttu-id="cc549-131">日付データ型への文字列の暗黙的な変換が必要な式は、データベース互換性レベルが 80 以下に設定されている場合を除いて、非決定的であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="cc549-131">Expressions that involve implicit conversion of character strings to date data types are considered nondeterministic, unless the database compatibility level is set to 80 or earlier.</span></span> <span data-ttu-id="cc549-132">これは、サーバー セッションの [LANGUAGE](/sql/t-sql/statements/set-language-transact-sql) および [DATEFORMAT](/sql/t-sql/statements/set-dateformat-transact-sql) の設定によって結果が異なるためです。</span><span class="sxs-lookup"><span data-stu-id="cc549-132">This is because the results depend on the [LANGUAGE](/sql/t-sql/statements/set-language-transact-sql) and [DATEFORMAT](/sql/t-sql/statements/set-dateformat-transact-sql) settings of the server session.</span></span> <span data-ttu-id="cc549-133">たとえば、式 `CONVERT (datetime, '30 listopad 1996', 113)` では、言語が異なると文字列 '`30 listopad 1996`' が異なる月を意味するので、結果が LANGUAGE の設定によって異なります。</span><span class="sxs-lookup"><span data-stu-id="cc549-133">For example, the results of the expression `CONVERT (datetime, '30 listopad 1996', 113)` depend on the LANGUAGE setting because the string '`30 listopad 1996`' means different months in different languages.</span></span> <span data-ttu-id="cc549-134">同様に、式 `DATEADD(mm,3,'2000-12-01')`では、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] により、文字列 `'2000-12-01'` が DATEFORMAT の設定に基づいて解釈されます。</span><span class="sxs-lookup"><span data-stu-id="cc549-134">Similarly, in the expression `DATEADD(mm,3,'2000-12-01')`, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] interprets the string `'2000-12-01'` based on the DATEFORMAT setting.</span></span>  
>   
>  <span data-ttu-id="cc549-135">照合順序間で行われる Unicode 以外の文字データの暗黙的な変換も、互換性レベルが 80 以下の場合を除いて、非決定的であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="cc549-135">Implicit conversion of non-Unicode character data between collations is also considered nondeterministic, unless the compatibility level is set to 80 or earlier.</span></span>  
>   
>  <span data-ttu-id="cc549-136">データベース互換性レベルの設定が 90 の場合は、それらの式を含む計算列にインデックスを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="cc549-136">When the database compatibility level setting is 90, you cannot create indexes on computed columns that contain these expressions.</span></span> <span data-ttu-id="cc549-137">ただし、アップグレードされたデータベースから、このような式を含む既存の計算列をメンテナンスできます。</span><span class="sxs-lookup"><span data-stu-id="cc549-137">However, existing computed columns that contain these expressions from an upgraded database are maintainable.</span></span> <span data-ttu-id="cc549-138">文字列から日付への暗黙的な変換を行うインデックス付き計算列を使用する場合は、インデックスが破損しないように、データベースやアプリケーション内で LANGUAGE と DATEFORMAT の設定の一貫性を確保してください。</span><span class="sxs-lookup"><span data-stu-id="cc549-138">If you use indexed computed columns that contain implicit string to date conversions, to avoid possible index corruption, make sure that the LANGUAGE and DATEFORMAT settings are consistent in your databases and applications.</span></span>  
  
 <span data-ttu-id="cc549-139">**Precision Requirements**</span><span class="sxs-lookup"><span data-stu-id="cc549-139">**Precision Requirements**</span></span>  
  
 <span data-ttu-id="cc549-140">*computed_column_expression* は正確である必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc549-140">The *computed_column_expression* must be precise.</span></span> <span data-ttu-id="cc549-141">*computed_column_expression* は、次の 1 つ以上の条件に該当する場合は正確です。</span><span class="sxs-lookup"><span data-stu-id="cc549-141">A *computed_column_expression* is precise when one or more of the following is true:</span></span>  
  
-   <span data-ttu-id="cc549-142">`float` データ型または `real` データ型の式ではない。</span><span class="sxs-lookup"><span data-stu-id="cc549-142">It is not an expression of the `float` or `real` data types.</span></span>  
  
-   <span data-ttu-id="cc549-143">式の定義に `float` データ型や `real` データ型を使用していない。</span><span class="sxs-lookup"><span data-stu-id="cc549-143">It does not use a `float` or `real` data type in its definition.</span></span> <span data-ttu-id="cc549-144">たとえば、次のステートメントでは、列 `y` は `int` 型で決定的ですが、正確ではありません。</span><span class="sxs-lookup"><span data-stu-id="cc549-144">For example, in the following statement, column `y` is `int` and deterministic but not precise.</span></span>  
  
    ```  
    CREATE TABLE t2 (a int, b int, c int, x float,   
       y AS CASE x   
             WHEN 0 THEN a   
             WHEN 1 THEN b   
             ELSE c   
          END);  
    ```  
  
> [!NOTE]  
>  <span data-ttu-id="cc549-145">`float` 型や `real` 型の式はすべて不正確であると見なされ、インデックスのキーにできません。つまり、`float` 型または `real` 型の式はインデックス付きビューで使用できますが、キーとしては使用できません。</span><span class="sxs-lookup"><span data-stu-id="cc549-145">Any `float` or `real` expression is considered imprecise and cannot be a key of an index; a `float` or `real` expression can be used in an indexed view but not as a key.</span></span> <span data-ttu-id="cc549-146">このことは、計算列にも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="cc549-146">This is true also for computed columns.</span></span> <span data-ttu-id="cc549-147">`float` 型や `real` 型の任意の式が含まれている関数、式、またはユーザー定義関数はすべて不正確であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="cc549-147">Any function, expression, or user-defined function is considered imprecise if it contains any `float` or `real` expressions.</span></span> <span data-ttu-id="cc549-148">これには、論理式 (比較) も含まれます。</span><span class="sxs-lookup"><span data-stu-id="cc549-148">This includes logical ones (comparisons).</span></span>  
  
 <span data-ttu-id="cc549-149">COLUMNPROPERTY 関数の **IsPrecise** プロパティは、 *computed_column_expression* が正確であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="cc549-149">The **IsPrecise** property of the COLUMNPROPERTY function reports whether a *computed_column_expression* is precise.</span></span>  
  
 <span data-ttu-id="cc549-150">**Data Type Requirements**</span><span class="sxs-lookup"><span data-stu-id="cc549-150">**Data Type Requirements**</span></span>  
  
-   <span data-ttu-id="cc549-151">計算列に定義された*computed_column_expression*は、、 `text` `ntext` 、または `image` データ型に評価できません。</span><span class="sxs-lookup"><span data-stu-id="cc549-151">The *computed_column_expression* defined for the computed column cannot evaluate to the `text`, `ntext`, or `image` data types.</span></span>  
  
-   <span data-ttu-id="cc549-152">`image`、`ntext`、`text`、`varchar(max)`、`nvarchar(max)`、`varbinary(max)`、および `xml` データ型から派生した計算列には、計算列のデータ型をインデックス キー列として使用できる限り、インデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="cc549-152">Computed columns derived from `image`, `ntext`, `text`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, and `xml` data types can be indexed as long as the computed column data type is allowable as an index key column.</span></span>  
  
-   <span data-ttu-id="cc549-153">`image`、`ntext`、および `text` データ型から派生した計算列は、計算列のデータ型を非キー インデックス列として使用できる限り、非クラスター化インデックスの非キー列 (付加列) にすることができます。</span><span class="sxs-lookup"><span data-stu-id="cc549-153">Computed columns derived from `image`, `ntext`, and `text` data types can be nonkey (included) columns in a nonclustered index as long as the computed column data type is allowable as a nonkey index column.</span></span>  
  
 <span data-ttu-id="cc549-154">**SET Option Requirements**</span><span class="sxs-lookup"><span data-stu-id="cc549-154">**SET Option Requirements**</span></span>  
  
-   <span data-ttu-id="cc549-155">計算列を定義する CREATE TABLE ステートメントまたは ALTER TABLE ステートメントの実行時に、ANSI_NULLS 接続レベルのオプションが ON に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc549-155">The ANSI_NULLS connection-level option must be set to ON when the CREATE TABLE or ALTER TABLE statement that defines the computed column is executed.</span></span> <span data-ttu-id="cc549-156">[OBJECTPROPERTY](/sql/t-sql/functions/objectpropertyex-transact-sql) 関数の **IsAnsiNullsOn** プロパティは、このオプションが ON に設定されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="cc549-156">The [OBJECTPROPERTY](/sql/t-sql/functions/objectpropertyex-transact-sql) function reports whether the option is on through the **IsAnsiNullsOn** property.</span></span>  
  
-   <span data-ttu-id="cc549-157">インデックスを作成する接続、およびインデックス内の値を変更する INSERT、UPDATE、または DELETE ステートメントを実行するすべての接続では、SET オプションのうち 6 つを ON に設定し、1 つを OFF に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc549-157">The connection on which the index is created, and all connections trying INSERT, UPDATE, or DELETE statements that will change values in the index, must have six SET options set to ON and one option set to OFF.</span></span> <span data-ttu-id="cc549-158">これらのオプションの設定が同一ではない接続で実行されるすべての SELECT ステートメントでは、オプティマイザーにより計算列のインデックスが無視されます。</span><span class="sxs-lookup"><span data-stu-id="cc549-158">The optimizer ignores an index on a computed column for any SELECT statement executed by a connection that does not have these same option settings.</span></span>  
  
    -   <span data-ttu-id="cc549-159">NUMERIC_ROUNDABORT オプションは OFF に設定し、次のオプションは ON に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc549-159">The NUMERIC_ROUNDABORT option must be set to OFF, and the following options must be set to ON:</span></span>  
  
    -   <span data-ttu-id="cc549-160">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="cc549-160">ANSI_NULLS</span></span>  
  
    -   <span data-ttu-id="cc549-161">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="cc549-161">ANSI_PADDING</span></span>  
  
    -   <span data-ttu-id="cc549-162">ANSI_WARNINGS</span><span class="sxs-lookup"><span data-stu-id="cc549-162">ANSI_WARNINGS</span></span>  
  
    -   <span data-ttu-id="cc549-163">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="cc549-163">ARITHABORT</span></span>  
  
    -   <span data-ttu-id="cc549-164">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="cc549-164">CONCAT_NULL_YIELDS_NULL</span></span>  
  
    -   <span data-ttu-id="cc549-165">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="cc549-165">QUOTED_IDENTIFIER</span></span>  
  
     <span data-ttu-id="cc549-166">ANSI_WARNINGS を ON に設定すると、データベース互換性レベルが 90 以上に設定されている場合、暗黙的に ARITHABORT が ON に設定されます。</span><span class="sxs-lookup"><span data-stu-id="cc549-166">Setting ANSI_WARNINGS to ON implicitly sets ARITHABORT to ON when the database compatibility level is set to 90 or higher.</span></span>  
  
##  <a name="creating-indexes-on-persisted-computed-columns"></a><a name="BKMK_persisted"></a> <span data-ttu-id="cc549-167">保存される計算列でのインデックスの作成</span><span class="sxs-lookup"><span data-stu-id="cc549-167">Creating Indexes on Persisted Computed Columns</span></span>  
 <span data-ttu-id="cc549-168">決定的でも不正確である式を使用して定義されている計算列が CREATE TABLE ステートメントまたは ALTER TABLE ステートメントで PERSISTED に設定されている場合、計算列にインデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="cc549-168">You can create an index on a computed column that is defined with a deterministic, but imprecise, expression if the column is marked PERSISTED in the CREATE TABLE or ALTER TABLE statement.</span></span> <span data-ttu-id="cc549-169">つまり、は、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 列にインデックスを作成するとき、およびインデックスがクエリで参照されるときに、これらの永続化された値を使用します。</span><span class="sxs-lookup"><span data-stu-id="cc549-169">This means that the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] uses these persisted values when it creates an index on the column, and when the index is referenced in a query.</span></span> <span data-ttu-id="cc549-170">このオプションを使用すると [!INCLUDE[ssDE](../../../includes/dnprdnshort-md.md)] 、が決定的かつ正確である場合に、計算列にインデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="cc549-170">This option enables you to create an index on a computed column when [!INCLUDE[ssDE](../../../includes/dnprdnshort-md.md)], is both deterministic and precise.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="cc549-171">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="cc549-171">Related Content</span></span>  
 [<span data-ttu-id="cc549-172">COLUMNPROPERTY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc549-172">COLUMNPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/columnproperty-transact-sql)  
  
  
