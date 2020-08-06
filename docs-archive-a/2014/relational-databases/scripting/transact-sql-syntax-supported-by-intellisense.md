---
title: IntelliSense でサポートされている Transact-SQL 構文
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- Transact-SQL IntelliSense
- IntelliSense [SQL Server], Transact-SQL syntax
ms.assetid: 194e8f4f-fd7e-4f32-a169-f23531128004
author: rothja
ms.author: jroth
ms.openlocfilehash: b3d34fc79dd7817e64b34b61083415477860ce97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717787"
---
# <a name="transact-sql-syntax-supported-by-intellisense"></a><span data-ttu-id="7eb76-102">IntelliSense でサポートされている Transact-SQL 構文</span><span class="sxs-lookup"><span data-stu-id="7eb76-102">Transact-SQL Syntax Supported by IntelliSense</span></span>
  <span data-ttu-id="7eb76-103">このトピックでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] の IntelliSense でサポートされる [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]ステートメントと構文要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7eb76-103">This topic describes the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and syntax elements that are supported by IntelliSense in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="statements-supported-by-intellisense"></a><span data-ttu-id="7eb76-104">IntelliSense でサポートされるステートメント</span><span class="sxs-lookup"><span data-stu-id="7eb76-104">Statements Supported by IntelliSense</span></span>  
 <span data-ttu-id="7eb76-105">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の IntelliSense では、特に一般的な [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7eb76-105">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], IntelliSense supports only the most commonly used [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="7eb76-106">いくつかの一般的な [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターの状態が原因で IntelliSense が動作しなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7eb76-106">Some general [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor conditions might prevent IntelliSense from functioning.</span></span> <span data-ttu-id="7eb76-107">詳細については、「[IntelliSense のトラブルシューティング &#40;SQL Server Management Studio&#41;](troubleshooting-intellisense.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7eb76-107">For more information, see [Troubleshooting IntelliSense &#40;SQL Server Management Studio&#41;](troubleshooting-intellisense.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7eb76-108">IntelliSense は、暗号化されたデータベース オブジェクト (たとえば暗号化されたストアド プロシージャまたはユーザー定義関数) に対しては利用できません。</span><span class="sxs-lookup"><span data-stu-id="7eb76-108">IntelliSense is not available for encrypted database objects, such as encrypted stored procedures or user-defined functions.</span></span> <span data-ttu-id="7eb76-109">拡張されたストアド プロシージャおよび CLR 統合のユーザー定義型のパラメーターに対しては、パラメーターのヘルプおよびクイック ヒントを利用できません。</span><span class="sxs-lookup"><span data-stu-id="7eb76-109">Parameter help and Quick Info are not available for the parameters of extended stored procedures and CLR Integration user-defined types.</span></span>  
  
### <a name="select-statement"></a><span data-ttu-id="7eb76-110">SELECT ステートメント</span><span class="sxs-lookup"><span data-stu-id="7eb76-110">SELECT Statement</span></span>  
 <span data-ttu-id="7eb76-111">[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターでは、IntelliSense によって、SELECT ステートメント内の次の構文要素がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7eb76-111">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor provides IntelliSense support for the following syntax elements in the SELECT statement:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7eb76-112">SELECT</span><span class="sxs-lookup"><span data-stu-id="7eb76-112">SELECT</span></span>|<span data-ttu-id="7eb76-113">WHERE</span><span class="sxs-lookup"><span data-stu-id="7eb76-113">WHERE</span></span>|  
|<span data-ttu-id="7eb76-114">FROM</span><span class="sxs-lookup"><span data-stu-id="7eb76-114">FROM</span></span>|<span data-ttu-id="7eb76-115">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="7eb76-115">ORDER BY</span></span>|  
|<span data-ttu-id="7eb76-116">HAVING</span><span class="sxs-lookup"><span data-stu-id="7eb76-116">HAVING</span></span>|<span data-ttu-id="7eb76-117">UNION</span><span class="sxs-lookup"><span data-stu-id="7eb76-117">UNION</span></span>|  
|<span data-ttu-id="7eb76-118">FOR</span><span class="sxs-lookup"><span data-stu-id="7eb76-118">FOR</span></span>|<span data-ttu-id="7eb76-119">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="7eb76-119">GROUP BY</span></span>|  
|<span data-ttu-id="7eb76-120">TOP</span><span class="sxs-lookup"><span data-stu-id="7eb76-120">TOP</span></span>|<span data-ttu-id="7eb76-121">OPTION (hint)</span><span class="sxs-lookup"><span data-stu-id="7eb76-121">OPTION (hint)</span></span>|  
  
### <a name="additional-transact-sql-statements-that-are-supported"></a><span data-ttu-id="7eb76-122">サポートされているその他の Transact-SQL ステートメント</span><span class="sxs-lookup"><span data-stu-id="7eb76-122">Additional Transact-SQL Statements That Are Supported</span></span>  
 <span data-ttu-id="7eb76-123">[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターでは、IntelliSense によって、次の表に示す [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7eb76-123">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor also provides IntelliSense support for [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that are shown in the following table.</span></span>  
  
|<span data-ttu-id="7eb76-124">Transact-SQL ステートメント</span><span class="sxs-lookup"><span data-stu-id="7eb76-124">Transact-SQL statement</span></span>|<span data-ttu-id="7eb76-125">サポートされている構文</span><span class="sxs-lookup"><span data-stu-id="7eb76-125">Syntax supported</span></span>|  
|-----------------------------|----------------------|  
|[<span data-ttu-id="7eb76-126">INSERT</span><span class="sxs-lookup"><span data-stu-id="7eb76-126">INSERT</span></span>](/sql/t-sql/statements/insert-transact-sql)|<span data-ttu-id="7eb76-127">*execute_statement* 句を除くすべての構文。</span><span class="sxs-lookup"><span data-stu-id="7eb76-127">All syntax, except the *execute_statement* clause.</span></span>|  
|[<span data-ttu-id="7eb76-128">UPDATE</span><span class="sxs-lookup"><span data-stu-id="7eb76-128">UPDATE</span></span>](/sql/t-sql/queries/update-transact-sql)|<span data-ttu-id="7eb76-129">すべての構文。</span><span class="sxs-lookup"><span data-stu-id="7eb76-129">All syntax.</span></span>|  
|[<span data-ttu-id="7eb76-130">DELETE</span><span class="sxs-lookup"><span data-stu-id="7eb76-130">DELETE</span></span>](/sql/t-sql/statements/delete-transact-sql)|<span data-ttu-id="7eb76-131">すべての構文。</span><span class="sxs-lookup"><span data-stu-id="7eb76-131">All syntax.</span></span>|  
|[<span data-ttu-id="7eb76-132">DECLARE @local_variable</span><span class="sxs-lookup"><span data-stu-id="7eb76-132">DECLARE @local_variable</span></span>](/sql/t-sql/language-elements/declare-local-variable-transact-sql)|<span data-ttu-id="7eb76-133">すべての構文。</span><span class="sxs-lookup"><span data-stu-id="7eb76-133">All syntax.</span></span>|  
|[<span data-ttu-id="7eb76-134">一連@local_variable</span><span class="sxs-lookup"><span data-stu-id="7eb76-134">SET @local_variable</span></span>](/sql/t-sql/language-elements/set-local-variable-transact-sql)|<span data-ttu-id="7eb76-135">すべての構文。</span><span class="sxs-lookup"><span data-stu-id="7eb76-135">All syntax.</span></span>|  
|[<span data-ttu-id="7eb76-136">EXECUTE</span><span class="sxs-lookup"><span data-stu-id="7eb76-136">EXECUTE</span></span>](/sql/t-sql/language-elements/execute-transact-sql)|<span data-ttu-id="7eb76-137">ユーザー定義ストアド プロシージャ、システム ストアド プロシージャ、ユーザー定義関数、およびシステム関数の実行。</span><span class="sxs-lookup"><span data-stu-id="7eb76-137">Execution of user-defined stored procedures, system stored procedures, user-defined functions, and system functions.</span></span>|  
|[<span data-ttu-id="7eb76-138">CREATE TABLE</span><span class="sxs-lookup"><span data-stu-id="7eb76-138">CREATE TABLE</span></span>](/sql/t-sql/statements/create-table-transact-sql)|<span data-ttu-id="7eb76-139">すべての構文。</span><span class="sxs-lookup"><span data-stu-id="7eb76-139">All syntax.</span></span>|  
|[<span data-ttu-id="7eb76-140">CREATE VIEW</span><span class="sxs-lookup"><span data-stu-id="7eb76-140">CREATE VIEW</span></span>](/sql/t-sql/statements/create-view-transact-sql)|<span data-ttu-id="7eb76-141">すべての構文。</span><span class="sxs-lookup"><span data-stu-id="7eb76-141">All syntax.</span></span>|  
|[<span data-ttu-id="7eb76-142">CREATE PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="7eb76-142">CREATE PROCEDURE</span></span>](/sql/t-sql/statements/create-procedure-transact-sql)|<span data-ttu-id="7eb76-143">すべての構文。ただし、次の例外があります。</span><span class="sxs-lookup"><span data-stu-id="7eb76-143">All syntax, with the following exceptions:</span></span><br /><br /> <span data-ttu-id="7eb76-144">IntelliSense では EXTERNAL NAME 句をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="7eb76-144">There is no IntelliSense support for the EXTERNAL NAME clause.</span></span><br /><br /> <span data-ttu-id="7eb76-145">AS 句では、このトピックに記載されているステートメントと構文のみが IntelliSense によってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7eb76-145">In the AS clause, IntelliSense supports only the statements and syntax that are listed in this topic.</span></span>|  
|[<span data-ttu-id="7eb76-146">ALTER PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="7eb76-146">ALTER PROCEDURE</span></span>](/sql/t-sql/statements/alter-procedure-transact-sql)|<span data-ttu-id="7eb76-147">すべての構文。ただし、次の例外があります。</span><span class="sxs-lookup"><span data-stu-id="7eb76-147">All syntax, with the following exceptions:</span></span><br /><br /> <span data-ttu-id="7eb76-148">IntelliSense では EXTERNAL NAME 句をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="7eb76-148">There is no IntelliSense support for the EXTERNAL NAME clause.</span></span><br /><br /> <span data-ttu-id="7eb76-149">AS 句では、このトピックに記載されているステートメントと構文のみが IntelliSense によってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7eb76-149">In the AS clause, IntelliSense supports only the statements and syntax that are listed in this topic.</span></span>|  
|[<span data-ttu-id="7eb76-150">USE</span><span class="sxs-lookup"><span data-stu-id="7eb76-150">USE</span></span>](/sql/t-sql/language-elements/use-transact-sql)|<span data-ttu-id="7eb76-151">すべての構文。</span><span class="sxs-lookup"><span data-stu-id="7eb76-151">All syntax.</span></span>|  
  
## <a name="intellisense-in-supported-statements"></a><span data-ttu-id="7eb76-152">サポートされているステートメントでの IntelliSense</span><span class="sxs-lookup"><span data-stu-id="7eb76-152">IntelliSense in Supported Statements</span></span>  
 <span data-ttu-id="7eb76-153">次の構文要素は、サポートされている [!INCLUDE[ssDE](../../includes/ssde-md.md)] ステートメントのいずれかで使用されている場合、 [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリ エディターの IntelliSense によってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7eb76-153">IntelliSense in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor supports the following syntax elements when they are used in one of the supported [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
-   <span data-ttu-id="7eb76-154">すべての結合の種類 (APPLY など)。</span><span class="sxs-lookup"><span data-stu-id="7eb76-154">All join types, including APPLY</span></span>  
  
-   <span data-ttu-id="7eb76-155">PIVOT および UNPIVOT。</span><span class="sxs-lookup"><span data-stu-id="7eb76-155">PIVOT and UNPIVOT</span></span>  
  
-   <span data-ttu-id="7eb76-156">次のデータベース オブジェクトへの参照。</span><span class="sxs-lookup"><span data-stu-id="7eb76-156">References to the following database objects:</span></span>  
  
    -   <span data-ttu-id="7eb76-157">データベースおよびスキーマ</span><span class="sxs-lookup"><span data-stu-id="7eb76-157">Databases and schemas</span></span>  
  
    -   <span data-ttu-id="7eb76-158">テーブル、ビュー、テーブル値関数、およびテーブル式</span><span class="sxs-lookup"><span data-stu-id="7eb76-158">Tables, views, table-valued functions, and table expressions</span></span>  
  
    -   <span data-ttu-id="7eb76-159">[列]</span><span class="sxs-lookup"><span data-stu-id="7eb76-159">Columns</span></span>  
  
    -   <span data-ttu-id="7eb76-160">プロシージャおよびプロシージャ パラメーター</span><span class="sxs-lookup"><span data-stu-id="7eb76-160">Procedures and procedure parameters</span></span>  
  
    -   <span data-ttu-id="7eb76-161">スカラー関数およびスカラー式</span><span class="sxs-lookup"><span data-stu-id="7eb76-161">Scalar functions and scalar expressions</span></span>  
  
    -   <span data-ttu-id="7eb76-162">ローカル変数</span><span class="sxs-lookup"><span data-stu-id="7eb76-162">Local variables</span></span>  
  
    -   <span data-ttu-id="7eb76-163">共通テーブル式 (CTE)</span><span class="sxs-lookup"><span data-stu-id="7eb76-163">Common table expressions (CTE)</span></span>  
  
-   <span data-ttu-id="7eb76-164">スクリプトまたはバッチ内の CREATE ステートメントまたは ALTER ステートメントのみで参照されるデータベース オブジェクト。ただし、スクリプトまたはバッチがまだ実行されていないためデータベースには存在しません。</span><span class="sxs-lookup"><span data-stu-id="7eb76-164">Database objects that are referenced only in CREATE or ALTER statements in the script or batch, but which do not exist in the database because the script or batch has not yet been run.</span></span> <span data-ttu-id="7eb76-165">これらのオブジェクトを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7eb76-165">These objects are as follows:</span></span>  
  
    -   <span data-ttu-id="7eb76-166">スクリプトまたはバッチ内の CREATE TABLE ステートメントまたは CREATE PROCEDURE ステートメントで指定されているテーブルおよびプロシージャ。</span><span class="sxs-lookup"><span data-stu-id="7eb76-166">Tables and procedures that have been specified in a CREATE TABLE or CREATE PROCEDURE statement in the script or batch.</span></span>  
  
    -   <span data-ttu-id="7eb76-167">スクリプトまたはバッチ内の ALTER TABLE ステートメントまたは ALTER PROCEDURE ステートメントで指定されているテーブルおよびプロシージャに対する変更。</span><span class="sxs-lookup"><span data-stu-id="7eb76-167">Changes to tables and procedures that have been specified in an ALTER TABLE or ALTER PROCEDURE statement in the script or batch.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7eb76-168">IntelliSense は、CREATE VIEW ステートメントが実行されるまでは CREATE VIEW ステートメントの列に対して利用できません。</span><span class="sxs-lookup"><span data-stu-id="7eb76-168">IntelliSense is not available for the columns of a CREATE VIEW statement until the CREATE VIEW statement has been executed.</span></span>  
  
 <span data-ttu-id="7eb76-169">前に示した要素が他の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント内で使用されている場合、IntelliSense は提供されません。</span><span class="sxs-lookup"><span data-stu-id="7eb76-169">IntelliSense is not provided for the previously listed elements when they are used in other [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="7eb76-170">たとえば、SELECT ステートメント内で使用されている列名に対しては IntelliSense のサポートがありますが、CREATE FUNCTION ステートメント内で使用されている列に対してはサポートがありません。</span><span class="sxs-lookup"><span data-stu-id="7eb76-170">For example, there is IntelliSense support for column names that are used in a SELECT statement, but not for columns that are used in the CREATE FUNCTION statement.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7eb76-171">例</span><span class="sxs-lookup"><span data-stu-id="7eb76-171">Examples</span></span>  
 <span data-ttu-id="7eb76-172">[!INCLUDE[tsql](../../includes/tsql-md.md)] のスクリプトまたはバッチ内では、このトピックに記載されているステートメントと構文のみが [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターの IntelliSense によってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7eb76-172">Within a [!INCLUDE[tsql](../../includes/tsql-md.md)] script or batch, IntelliSense in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor supports only the statements and syntax that are listed in this topic.</span></span> <span data-ttu-id="7eb76-173">IntelliSense でサポートされるステートメントと構文要素を次の [!INCLUDE[tsql](../../includes/tsql-md.md)] のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="7eb76-173">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] code examples show what statements and syntax elements IntelliSense supports.</span></span> <span data-ttu-id="7eb76-174">たとえば、次のバッチにおいて、 `SELECT` ステートメントが単独で記述されているときは IntelliSense を利用できますが、 `SELECT` が `CREATE FUNCTION` ステートメントに含まれているときは IntelliSense を利用できません。</span><span class="sxs-lookup"><span data-stu-id="7eb76-174">For example, in the following batch, IntelliSense is available for the `SELECT` statement when it is coded by itself, but not when the `SELECT` is contained in a `CREATE FUNCTION` statement.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Name  
FROM Production.Product  
WHERE Name LIKE N'Road-250%' and Color = N'Red';  
GO  
CREATE FUNCTION Production.ufn_Red250 ()  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT Name  
    FROM AdventureWorks2012.Production.Product  
    WHERE Name LIKE N'Road-250%'  
      AND Color = N'Red'  
);GO  
```  
  
 <span data-ttu-id="7eb76-175">この機能は、CREATE PROCEDURE ステートメントまたは ALTER PROCEDURE ステートメントの AS 句に含まれる [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのセットにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="7eb76-175">This functionality also applies to the sets of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the AS clause of a CREATE PROCEDURE or ALTER PROCEDURE statement.</span></span>  
  
 <span data-ttu-id="7eb76-176">[!INCLUDE[tsql](../../includes/tsql-md.md)] のスクリプトまたはバッチ内では、IntelliSense によって、CREATE ステートメントまたは ALTER ステートメントに指定されているオブジェクトがサポートされます。ただし、これらのオブジェクトは、ステートメントが実行されていないためデータベースに存在しません。</span><span class="sxs-lookup"><span data-stu-id="7eb76-176">Within a [!INCLUDE[tsql](../../includes/tsql-md.md)] script or batch, IntelliSense supports objects that have been specified in a CREATE or ALTER statement; however, these objects do not exist in the database because the statements have not been executed.</span></span> <span data-ttu-id="7eb76-177">たとえば、クエリ エディターで次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="7eb76-177">For example, you might enter the following code in the Query Editor:</span></span>  
  
```  
USE MyTestDB;  
GO  
CREATE TABLE MyTable  
    (PrimaryKeyCol   INT PRIMARY KEY,  
    FirstNameCol      NVARCHAR(50),  
   LastNameCol       NVARCHAR(50));  
GO  
SELECT   
```  
  
 <span data-ttu-id="7eb76-178">スクリプトが実行されていないため `SELECT`が **に存在しない場合でも、** を入力すると、IntelliSense により、使用可能な要素として **PrimaryKeyCol**、 **FirstNameCol** 、および `MyTable` LastNameCol `MyTestDB`が選択リストに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7eb76-178">After you type `SELECT`, IntelliSense lists **PrimaryKeyCol**, **FirstNameCol**, and **LastNameCol** as possible elements in the select list, even if the script has not been executed and `MyTable` does not yet exist in `MyTestDB`.</span></span>  
  
  
