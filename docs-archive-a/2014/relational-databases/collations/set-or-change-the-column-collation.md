---
title: 列の照合順序の設定または変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tempdb database [SQL Server], collations
- collations [SQL Server], column
ms.assetid: d7a9638b-717c-4680-9b98-8849081e08be
author: stevestein
ms.author: sstein
ms.openlocfilehash: 05b8211569b6ce83faaec043e5eb527a60f0ddab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645661"
---
# <a name="set-or-change-the-column-collation"></a><span data-ttu-id="4fa41-102">列の照合順序の設定または変更</span><span class="sxs-lookup"><span data-stu-id="4fa41-102">Set or Change the Column Collation</span></span>
  <span data-ttu-id="4fa41-103">`char` 型、`varchar` 型、`text` 型、`nchar` 型、`nvarchar` 型、および `ntext` 型のデータのデータベース照合順序は、テーブルの列ごとに異なる照合順序を指定し、次のいずれかを使用することでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="4fa41-103">You can override the database collation for `char`, `varchar`, `text`, `nchar`, `nvarchar`, and `ntext` data by specifying a different collation for a specific column of a table and using one of the following:</span></span>  
  
-   <span data-ttu-id="4fa41-104">[CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) と [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)の COLLATE 句。</span><span class="sxs-lookup"><span data-stu-id="4fa41-104">The COLLATE clause of [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) and [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).</span></span> <span data-ttu-id="4fa41-105">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="4fa41-105">For example:</span></span>  
  
    ```  
    CREATE TABLE dbo.MyTable  
      (PrimaryKey   int PRIMARY KEY,  
       CharCol      varchar(10) COLLATE French_CI_AS NOT NULL  
      );  
    GO  
    ALTER TABLE dbo.MyTable ALTER COLUMN CharCol  
                varchar(10)COLLATE Latin1_General_CI_AS NOT NULL;  
    GO  
    ```  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="4fa41-106">.</span><span class="sxs-lookup"><span data-stu-id="4fa41-106">.</span></span> <span data-ttu-id="4fa41-107">詳細については、「 [照合順序と Unicode のサポート](collation-and-unicode-support.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4fa41-107">For more information, [Collation and Unicode Support](collation-and-unicode-support.md).</span></span>  
  
-   <span data-ttu-id="4fa41-108">`Column.Collation` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) でプロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="4fa41-108">Using the `Column.Collation` property in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO).</span></span>  
  
 <span data-ttu-id="4fa41-109">次のいずれかから現在参照されている列は、照合順序を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="4fa41-109">You cannot change the collation of a column that is currently referenced by any one of the following:</span></span>  
  
-   <span data-ttu-id="4fa41-110">計算列</span><span class="sxs-lookup"><span data-stu-id="4fa41-110">A computed column</span></span>  
  
-   <span data-ttu-id="4fa41-111">インデックス</span><span class="sxs-lookup"><span data-stu-id="4fa41-111">An index</span></span>  
  
-   <span data-ttu-id="4fa41-112">自動的に生成された、または CREATE STATISTICS ステートメントによって生成された分布統計情報</span><span class="sxs-lookup"><span data-stu-id="4fa41-112">Distribution statistics, either generated automatically or by the CREATE STATISTICS statement</span></span>  
  
-   <span data-ttu-id="4fa41-113">CHECK 制約</span><span class="sxs-lookup"><span data-stu-id="4fa41-113">A CHECK constraint</span></span>  
  
-   <span data-ttu-id="4fa41-114">FOREIGN KEY 制約</span><span class="sxs-lookup"><span data-stu-id="4fa41-114">A FOREIGN KEY constraint</span></span>  
  
 <span data-ttu-id="4fa41-115">**tempdb**を操作する場合、 [COLLATE](/sql/t-sql/statements/collations) 句に *database_default* オプションを指定することで、一時テーブルの列で、接続の現在のユーザー データベースでの既定の照合順序を **tempdb**の照合順序の代わりに使用するように指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="4fa41-115">When you work with **tempdb**, the [COLLATE](/sql/t-sql/statements/collations) clause includes a *database_default* option to specify that a column in a temporary table uses the collation default of the current user database for the connection instead of the collation of **tempdb**.</span></span>  
  
## <a name="collations-and-text-columns"></a><span data-ttu-id="4fa41-116">照合順序と text 列</span><span class="sxs-lookup"><span data-stu-id="4fa41-116">Collations and text Columns</span></span>  
 <span data-ttu-id="4fa41-117">データベースの既定の照合順序のコード ページと異なる照合順序が設定された `text` 列では、値の挿入と更新が可能です。</span><span class="sxs-lookup"><span data-stu-id="4fa41-117">You can insert or update values in a `text` column whose collation is different from the code page of the default collation of the database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4fa41-118">により、値がこの列の照合順序に暗黙的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="4fa41-118">implicitly converts the values to the collation of the column.</span></span>  
  
## <a name="collations-and-tempdb"></a><span data-ttu-id="4fa41-119">照合順序と tempdb</span><span class="sxs-lookup"><span data-stu-id="4fa41-119">Collations and tempdb</span></span>  
 <span data-ttu-id="4fa41-120">**tempdb** データベースは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が起動されるたびに作成され、 **model** データベースと同じ既定の照合順序が設定されます。</span><span class="sxs-lookup"><span data-stu-id="4fa41-120">The **tempdb** database is built every time [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started and has the same default collation as the **model** database.</span></span> <span data-ttu-id="4fa41-121">これは、通常、インスタンスの既定の照合順序と同じになります。</span><span class="sxs-lookup"><span data-stu-id="4fa41-121">This is typically the same as the default collation of the instance.</span></span> <span data-ttu-id="4fa41-122">ユーザー データベースを作成して、 **model**と異なる既定の照合順序を指定すると、そのユーザー データベースでは **tempdb**と異なる既定の照合順序が使用されます。</span><span class="sxs-lookup"><span data-stu-id="4fa41-122">If you create a user database and specify a different default collation than **model**, the user database has a different default collation than **tempdb**.</span></span> <span data-ttu-id="4fa41-123">一時ストアド プロシージャや一時テーブルは、すべて **tempdb**内に作成および格納されます。</span><span class="sxs-lookup"><span data-stu-id="4fa41-123">All temporary stored procedures or temporary tables are created and stored in **tempdb**.</span></span> <span data-ttu-id="4fa41-124">その結果、一時テーブル内のすべての暗黙の列、および一時ストアド プロシージャ内で強制的に適用されるすべての既定の定数、変数、パラメーターでは、パーマネント テーブルやストアド プロシージャで作成される同等のオブジェクトとは異なる照合順序が指定されます。</span><span class="sxs-lookup"><span data-stu-id="4fa41-124">This means that all implicit columns in temporary tables and all coercible-default constants, variables, and parameters in temporary stored procedures have collations that are different from comparable objects created in permanent tables and stored procedures.</span></span>  
  
 <span data-ttu-id="4fa41-125">このため、ユーザー定義データベースとシステム データベース オブジェクトの照合順序の不一致による問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4fa41-125">This could lead to problems with a mismatch in collations between user-defined databases and system database objects.</span></span> <span data-ttu-id="4fa41-126">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスでは照合順序として Latin1_General_CS_AS が使用されていて、次のステートメントを実行するとします。</span><span class="sxs-lookup"><span data-stu-id="4fa41-126">For example, an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses the Latin1_General_CS_AS collation and you execute the following statements:</span></span>  
  
```  
CREATE DATABASE TestDB COLLATE Estonian_CS_AS;  
USE TestDB;  
CREATE TABLE TestPermTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
```  
  
 <span data-ttu-id="4fa41-127">このシステムでは、 **tempdb** データベースにコード ページ 1252 の Latin1_General_CS_AS 照合順序が使用され、 `TestDB` と `TestPermTab.Col1` にコード ページ 1257 の `Estonian_CS_AS` 照合順序が使用されることになります。</span><span class="sxs-lookup"><span data-stu-id="4fa41-127">In this system, the **tempdb** database uses the Latin1_General_CS_AS collation with code page 1252, and `TestDB` and `TestPermTab.Col1` use the `Estonian_CS_AS` collation with code page 1257.</span></span> <span data-ttu-id="4fa41-128">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="4fa41-128">For example:</span></span>  
  
```  
USE TestDB;  
GO  
-- Create a temporary table with the same column declarations  
-- as TestPermTab  
CREATE TABLE #TestTempTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
INSERT INTO #TestTempTab  
         SELECT * FROM TestPermTab;  
GO  
```  
  
 <span data-ttu-id="4fa41-129">上記の例では、 **tempdb** データベースで Latin1_General_CS_AS 照合順序が使用され、 `TestDB` と `TestTab.Col1` では `Estonian_CS_AS` 照合順序が使用されます。</span><span class="sxs-lookup"><span data-stu-id="4fa41-129">With the previous example, the **tempdb** database uses the Latin1_General_CS_AS collation, and `TestDB` and `TestTab.Col1` use the `Estonian_CS_AS` collation.</span></span> <span data-ttu-id="4fa41-130">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="4fa41-130">For example:</span></span>  
  
```  
SELECT * FROM TestPermTab AS a INNER JOIN #TestTempTab on a.Col1 = #TestTempTab.Col1;  
```  
  
 <span data-ttu-id="4fa41-131">**tempdb** ではサーバーの既定照合順序が使用され、 `TestPermTab.Col1` では異なる照合順序が使用されるので、"Cannot resolve collation conflict between 'Latin1_General_CI_AS_KS_WS' and 'Estonian_CS_AS' in equal to operation. " (equal to 操作の 'Latin1_General_CI_AS_KS_WS' と 'Estonian_CS_AS' 間での照合順序の競合を解決できません。) というエラーが SQL Server から返されます。</span><span class="sxs-lookup"><span data-stu-id="4fa41-131">Because **tempdb** uses the default server collation and `TestPermTab.Col1` uses a different collation, SQL Server returns this error: "Cannot resolve collation conflict between 'Latin1_General_CI_AS_KS_WS' and 'Estonian_CS_AS' in equal to operation."</span></span>  
  
 <span data-ttu-id="4fa41-132">このエラーを回避するには、次のいずれかを行います。</span><span class="sxs-lookup"><span data-stu-id="4fa41-132">To prevent the error, you can use one of the following alternatives:</span></span>  
  
-   <span data-ttu-id="4fa41-133">一時テーブル列で、 **tempdb**ではなく、ユーザー データベースの既定の照合順序を使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="4fa41-133">Specify that the temporary table column use the default collation of the user database, not **tempdb**.</span></span> <span data-ttu-id="4fa41-134">この措置によって、システムで必要とされる場合に、一時テーブルを複数のデータベース内で同様の形式が設定されたテーブルと併用できます。</span><span class="sxs-lookup"><span data-stu-id="4fa41-134">This enables the temporary table to work with similarly formatted tables in multiple databases, if that is required of your system.</span></span>  
  
    ```  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE database_default  
       );  
    ```  
  
-   <span data-ttu-id="4fa41-135">次のように、 `#TestTempTab` 列に正しい照合順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="4fa41-135">Specify the correct collation for the `#TestTempTab` column:</span></span>  
  
    ```  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE Estonian_CS_AS  
       );  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4fa41-136">参照</span><span class="sxs-lookup"><span data-stu-id="4fa41-136">See Also</span></span>  
 <span data-ttu-id="4fa41-137">[サーバーの照合順序を設定または変更する](set-or-change-the-server-collation.md) </span><span class="sxs-lookup"><span data-stu-id="4fa41-137">[Set or Change the Server Collation](set-or-change-the-server-collation.md) </span></span>  
 <span data-ttu-id="4fa41-138">[データベースの照合順序の設定または変更](set-or-change-the-database-collation.md) </span><span class="sxs-lookup"><span data-stu-id="4fa41-138">[Set or Change the Database Collation](set-or-change-the-database-collation.md) </span></span>  
 [<span data-ttu-id="4fa41-139">照合順序と Unicode のサポート</span><span class="sxs-lookup"><span data-stu-id="4fa41-139">Collation and Unicode Support</span></span>](collation-and-unicode-support.md)  
  
  
