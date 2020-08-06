---
title: 照合順序とコードページ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c626dcac-0474-432d-acc0-cfa643345372
author: stevestein
ms.author: sstein
ms.openlocfilehash: ab904771fa8ac4acf25a624cbf3e1139f7e96434
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642325"
---
# <a name="collations-and-code-pages"></a><span data-ttu-id="538f3-102">照合順序とコード ページ</span><span class="sxs-lookup"><span data-stu-id="538f3-102">Collations and Code Pages</span></span>
  [!INCLUDE[hek_2](../includes/hek-2-md.md)] <span data-ttu-id="538f3-103">には、メモリ最適化テーブルの (var)char 型の列のサポートされているコード ページと、インデックスおよびネイティブ コンパイル ストアド プロシージャで使用されるサポートされている照合順序に関して制限事項があります。</span><span class="sxs-lookup"><span data-stu-id="538f3-103">has restrictions on supported code pages for (var)char columns in memory-optimized tables and supported collations used in indexes and natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="538f3-104">(var)char 値のコード ページにより、テーブルに格納されているバイト表現と文字との間のマッピングが決定されます。</span><span class="sxs-lookup"><span data-stu-id="538f3-104">The code page for a (var)char value determines the mapping between characters and the byte representation that is stored in the table.</span></span> <span data-ttu-id="538f3-105">たとえば、Windows の Latin 1 コード ページ (1252、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の既定値) の場合、文字 "a" はバイト 0x61 に対応します。</span><span class="sxs-lookup"><span data-stu-id="538f3-105">For example, with the Windows Latin 1 code page (1252; the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] default), the character 'a' corresponds to the byte 0x61.</span></span>  
  
 <span data-ttu-id="538f3-106">(var)char 値のコード ページは、値に関連付けられた照合順序によって決まります。</span><span class="sxs-lookup"><span data-stu-id="538f3-106">The code page of a (var)char value is determined by the collation associated with the value.</span></span> <span data-ttu-id="538f3-107">たとえば、照合順序 SQL_Latin1_General_CP1_CI_AS に関連付けられたコード ページは 1252 です。</span><span class="sxs-lookup"><span data-stu-id="538f3-107">For example, the collation SQL_Latin1_General_CP1_CI_AS has the associated code page 1252.</span></span>  
  
 <span data-ttu-id="538f3-108">値の照合順序は、データベースの照合順序から継承されるか、または COLLATE キーワードを使用して明示的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="538f3-108">The collation of a value is either inherited from the database collation, or can be specified explicitly using the COLLATE keyword.</span></span> <span data-ttu-id="538f3-109">データベースの照合順序は、データベースがメモリ最適化テーブルまたはネイティブ コンパイル ストアド プロシージャを含む場合は変更できません。</span><span class="sxs-lookup"><span data-stu-id="538f3-109">Database collation cannot be changed if the database contains memory-optimized tables or natively compiled stored procedures.</span></span> <span data-ttu-id="538f3-110">次の例では、データベースの照合順序を設定し、異なる照合順序を持つ列を含むテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="538f3-110">The following example sets the database collation and creates a table, which has a column with a different collation.</span></span> <span data-ttu-id="538f3-111">このデータベースでは、ラテン文字の大文字と小文字が区別されない照合順序が使用されます。</span><span class="sxs-lookup"><span data-stu-id="538f3-111">The database uses Latin case-insensitive collation.</span></span>  
  
 <span data-ttu-id="538f3-112">BIN2 照合順序が使用されている場合、インデックスは文字列型の列にのみ作成できます。</span><span class="sxs-lookup"><span data-stu-id="538f3-112">Indexes can only be created on string columns if they use a BIN2 collation.</span></span> <span data-ttu-id="538f3-113">LastName 変数では、BIN2 照合順序を使用しています。</span><span class="sxs-lookup"><span data-stu-id="538f3-113">The LastName variable uses BIN2 collation.</span></span> <span data-ttu-id="538f3-114">FirstName では、データベースの既定値である CI_AS (大文字と小文字を区別しない、アクセントを区別する) を使用しています。</span><span class="sxs-lookup"><span data-stu-id="538f3-114">FirstName uses the database default, which is CI_AS (case-insensitive, accent-sensitive).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="538f3-115">BIN2 照合順序を使用しないインデックス文字列の列に対して、order by や group by を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="538f3-115">You cannot use order by or group by on index string columns that do not use BIN2 collation.</span></span>  
  
```sql  
CREATE DATABASE IMOLTP  
  
ALTER DATABASE IMOLTP ADD FILEGROUP IMOLTP_mod CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE IMOLTP ADD FILE( NAME = 'IMOLTP_mod' , FILENAME = 'c:\data\IMOLTP_mod') TO FILEGROUP IMOLTP_mod;  
--GO  
  
--  set the database collations  
ALTER DATABASE IMOLTP COLLATE Latin1_General_100_CI_AS  
GO  
  
--  
USE IMOLTP   
GO  
  
-- create a table with collation  
CREATE TABLE Employees (  
  EmployeeID int NOT NULL ,   
  LastName nvarchar(20) COLLATE Latin1_General_100_BIN2 NOT NULL INDEX IX_LastName NONCLUSTERED,   
  FirstName nvarchar(10) NOT NULL ,  
  CONSTRAINT PK_Employees PRIMARY KEY NONCLUSTERED HASH(EmployeeID)  WITH (BUCKET_COUNT=1024)  
) WITH (MEMORY_OPTIMIZED=ON, DURABILITY=SCHEMA_AND_DATA)  
GO  
```  
  
 <span data-ttu-id="538f3-116">メモリ最適化テーブルとネイティブ コンパイル ストアド プロシージャに対して、次の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="538f3-116">The following restrictions apply to memory-optimized tables and natively compiled stored procedures:</span></span>  
  
-   <span data-ttu-id="538f3-117">メモリ最適化テーブルの (var)char 型の列では、コード ページ 1252 照合順序を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="538f3-117">(var)char columns in memory-optimized tables must use code page 1252 collation.</span></span> <span data-ttu-id="538f3-118">この制限は、n(var)char 型の列には適用されません。</span><span class="sxs-lookup"><span data-stu-id="538f3-118">This restriction does not apply to n(var)char columns.</span></span> <span data-ttu-id="538f3-119">次のコードは、すべての 1252 照合順序を取得します。</span><span class="sxs-lookup"><span data-stu-id="538f3-119">The following code retrieves all 1252 collations:</span></span>  
  
    ```sql  
    -- all supported collations for (var)char columns in memory-optimized tables  
    select * from sys.fn_helpcollations()  
    where collationproperty(name, 'codepage') = 1252;  
    ```  
  
     <span data-ttu-id="538f3-120">ラテン文字以外の文字を格納する必要がある場合は、n(var)char 型の列を使用します。</span><span class="sxs-lookup"><span data-stu-id="538f3-120">If you need to store non-Latin characters, use n(var)char columns.</span></span>  
  
-   <span data-ttu-id="538f3-121">(n)(var)char 型の列のインデックスは、BIN2 照合順序でのみ指定できます (最初の例を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="538f3-121">Indexes on (n)(var)char columns can only be specified with BIN2 collations (see the first example).</span></span> <span data-ttu-id="538f3-122">次のクエリは、すべてのサポートされている BIN2 照合順序を取得します。</span><span class="sxs-lookup"><span data-stu-id="538f3-122">The following query retrieves all supported BIN2 collations:</span></span>  
  
    ```sql  
    -- all supported collations for indexes on memory-optimized tables and   
    -- comparison/sorting in natively compiled stored procedures  
    select * from sys.fn_helpcollations() where name like '%BIN2'  
    ```  
  
     <span data-ttu-id="538f3-123">解釈された [!INCLUDE[tsql](../includes/tsql-md.md)] を介してテーブルにアクセスする場合は、`COLLATE` キーワードを使用して、式または並べ替え操作による照合順序を変更できます。</span><span class="sxs-lookup"><span data-stu-id="538f3-123">If you access the table through interpreted [!INCLUDE[tsql](../includes/tsql-md.md)], you can use the `COLLATE` keyword to change the collation with expressions or sort operations.</span></span> <span data-ttu-id="538f3-124">この例については、最後の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="538f3-124">See the last example for a sample of this.</span></span>  
  
-   <span data-ttu-id="538f3-125">データベースの照合順序がコード ページ 1252 照合順序でない場合、ネイティブ コンパイル ストアド プロシージャは、パラメーター、ローカル変数、または (var)char 型の文字列定数を使用できません。</span><span class="sxs-lookup"><span data-stu-id="538f3-125">Natively compiled stored procedures cannot use parameters, local variables, or string constants of (var)char type if the database collation is not a code page 1252 collation.</span></span>  
  
-   <span data-ttu-id="538f3-126">ネイティブ コンパイル ストアド プロシージャ内のすべての式および並べ替え操作で BIN2 照合順序を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="538f3-126">All expressions and sort operations inside natively compiled stored procedures must use BIN2 collations.</span></span> <span data-ttu-id="538f3-127">これは、すべての比較および並べ替え操作が文字の Unicode コード ポイント (バイナリ表現) に基づいていることを表します。</span><span class="sxs-lookup"><span data-stu-id="538f3-127">The implication is that all comparisons and sort operations are based on the Unicode code points of the characters (binary representations).</span></span> <span data-ttu-id="538f3-128">たとえば、すべての並べ替えで大文字と小文字が区別されます ("Z" が "a" より前に来ます)。</span><span class="sxs-lookup"><span data-stu-id="538f3-128">For example all sorting is case sensitive ('Z' comes before 'a').</span></span> <span data-ttu-id="538f3-129">必要に応じて、解釈された [!INCLUDE[tsql](../includes/tsql-md.md)] を使用して、大文字と小文字が区別されない並べ替えと比較を行います。</span><span class="sxs-lookup"><span data-stu-id="538f3-129">If necessary, use interpreted [!INCLUDE[tsql](../includes/tsql-md.md)] for case-insensitive sorting and comparison.</span></span>  
  
-   <span data-ttu-id="538f3-130">ネイティブ コンパイル ストアド プロシージャ内では、UTF-16 データの切り捨てはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="538f3-130">Truncation of UTF-16 data is not supported inside natively compiled stored procedures.</span></span> <span data-ttu-id="538f3-131">つまり、照合順序に _SC プロパティがある場合 *、n (* var) char (*n*) 値を型 n (var) char (*i*) に変換することはできません  <  *n*。</span><span class="sxs-lookup"><span data-stu-id="538f3-131">This means that n(var)char(*n*) values cannot be converted to type n(var)char(*i*), if *i* < *n*, if the collation has _SC property.</span></span> <span data-ttu-id="538f3-132">たとえば、次の操作はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="538f3-132">For example, the following is not supported:</span></span>  
  
    ```sql  
    -- column definition using an _SC collation  
     c2 nvarchar(200) collate Latin1_General_100_CS_AS_SC not null   
    -- assignment to a smaller variable, requiring truncation  
     declare @c2 nvarchar(100) = '';  
     select @c2 = c2  
    ```  
  
     <span data-ttu-id="538f3-133">UTF-16 データを使った LEN、SUBSTRING、LTRIM、RTRIM などの文字列操作関数は、ネイティブ コンパイル ストアド プロシージャ内ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="538f3-133">String manipulation functions, such as LEN, SUBSTRING, LTRIM, and RTRIM with UTF-16 data are not supported inside natively compiled stored procedures.</span></span> <span data-ttu-id="538f3-134">_SC 照合順序を保持する n(var)char 値に対してこれらの文字列操作関数は使用できません。</span><span class="sxs-lookup"><span data-stu-id="538f3-134">You cannot use these string manipulation functions for n(var)char values that have an _SC collation.</span></span>  
  
     <span data-ttu-id="538f3-135">切り捨てを回避するのに十分な大きさの型を使用して、変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="538f3-135">Declare variables using types that are large enough to avoid truncation.</span></span>  
  
 <span data-ttu-id="538f3-136">次の例に、インメモリ OLTP での照合順序の制限の影響と回避策を示します。</span><span class="sxs-lookup"><span data-stu-id="538f3-136">The following example shows some of the implications and workarounds for the collation limitations in In-Memory OLTP.</span></span> <span data-ttu-id="538f3-137">この例では、前の例で指定した Employees テーブルを使用しています。</span><span class="sxs-lookup"><span data-stu-id="538f3-137">The example uses the Employees table specified above.</span></span> <span data-ttu-id="538f3-138">このサンプルでは、すべての従業員を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="538f3-138">This sample list all employees .</span></span> <span data-ttu-id="538f3-139">LastName については、バイナリ照合順序に基づいて、大文字の名前が小文字の名前の前に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="538f3-139">Notice that for LastName, due to the binary collation, the upper case names are sorted before lower case.</span></span> <span data-ttu-id="538f3-140">したがって、"Thomas" は "nolan" の前に来ます。これは、大文字のコード ポイントの方が小さいためです。</span><span class="sxs-lookup"><span data-stu-id="538f3-140">Therefore, 'Thomas' comes before 'nolan' because upper case characters have lower code points.</span></span> <span data-ttu-id="538f3-141">FirstName には、大文字と小文字が区別されない照合順序が設定されています。</span><span class="sxs-lookup"><span data-stu-id="538f3-141">FirstName has a case-insensitive collation.</span></span> <span data-ttu-id="538f3-142">したがって、並べ替えは、文字のコード ポイントではなくアルファベット順に基づいて行われます。</span><span class="sxs-lookup"><span data-stu-id="538f3-142">So, sorting is by letter of the alphabet, not code point of the characters.</span></span>  
  
```sql  
-- insert a number of values  
INSERT Employees VALUES (1,'thomas', 'john')  
INSERT Employees VALUES (2,'Thomas', 'rupert')  
INSERT Employees VALUES (3,'Thomas', 'Jack')  
INSERT Employees VALUES (4,'Thomas', 'annie')  
INSERT Employees VALUES (5,'nolan', 'John')  
GO  
  
-- ===========  
SELECT EmployeeID, LastName, FirstName FROM Employees  
ORDER BY LastName, FirstName  
GO  
  
-- ===========  
-- specify collation: sorting uses case-insensitive collation, thus 'nolan' comes before 'Thomas'  
SELECT * FROM Employees  
ORDER BY LastName COLLATE Latin1_General_100_CI_AS, FirstName  
GO  
  
-- ===========  
-- retrieve employee by Name  
-- must use BIN2 collation for comparison in natively compiled stored procedures  
CREATE PROCEDURE usp_EmployeeByName @LastName nvarchar(20), @FirstName nvarchar(10)  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
  LANGUAGE = N'us_english'  
)  
  SELECT EmployeeID, LastName, FirstName FROM dbo.Employees  
  WHERE   
    LastName = @LastName AND  
    FirstName COLLATE Latin1_General_100_BIN2 = @FirstName  
  
END  
GO  
  
-- this does not return any rows, as EmployeeID 1 has first name 'john', which is not equal to 'John' in a binary collation  
EXEC usp_EmployeeByName 'thomas', 'John'  
  
-- this retrieves EmployeeID 1  
EXEC usp_EmployeeByName 'thomas', 'john'  
```  
  
## <a name="see-also"></a><span data-ttu-id="538f3-143">参照</span><span class="sxs-lookup"><span data-stu-id="538f3-143">See Also</span></span>  
 [<span data-ttu-id="538f3-144">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="538f3-144">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
