---
title: テーブルの作成 (チュートリアル) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- creating tables
ms.assetid: 653f2dd3-36a2-4bd5-8703-71a57d244661
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c772f2527bd5ddb8a6759cbaa72d8aed9277f5cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642444"
---
# <a name="creating-a-table-tutorial"></a><span data-ttu-id="58101-102">テーブルの作成 (チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="58101-102">Creating a Table (Tutorial)</span></span>
  <span data-ttu-id="58101-103">テーブルを作成するには、テーブルの名前と、テーブル内の各列の名前とデータ型を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58101-103">To create a table, you must provide a name for the table, and the names and data types of each column in the table.</span></span> <span data-ttu-id="58101-104">また、各列でヌル値を許可するかどうかを指定することも推奨されます。</span><span class="sxs-lookup"><span data-stu-id="58101-104">It is also a good practice to indicate whether null values are allowed in each column.</span></span>  
  
 <span data-ttu-id="58101-105">ほとんどのテーブルに、テーブルの 1 つ以上の列で構成された主キーがあります。</span><span class="sxs-lookup"><span data-stu-id="58101-105">Most tables have a primary key, made up of one or more columns of the table.</span></span> <span data-ttu-id="58101-106">主キーは常に一意です。</span><span class="sxs-lookup"><span data-stu-id="58101-106">A primary key is always unique.</span></span> <span data-ttu-id="58101-107">[!INCLUDE[ssDE](../includes/ssde-md.md)] によって、主キーの値がテーブルで重複しないように制限されます。</span><span class="sxs-lookup"><span data-stu-id="58101-107">The [!INCLUDE[ssDE](../includes/ssde-md.md)] will enforce the restriction that any primary key value cannot be repeated in the table.</span></span>  
  
 <span data-ttu-id="58101-108">データ型のリストと、それぞれの説明のリンクについては、「[データ型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58101-108">For a list of data types and links for a description of each, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="58101-109">[!INCLUDE[ssDE](../includes/ssde-md.md)] は、大文字と小文字を区別するか区別しないかを設定してインストールできます。</span><span class="sxs-lookup"><span data-stu-id="58101-109">The [!INCLUDE[ssDE](../includes/ssde-md.md)] can be installed as case sensitive or non-case sensitive.</span></span> <span data-ttu-id="58101-110">大文字と小文字を区別するように設定して [!INCLUDE[ssDE](../includes/ssde-md.md)] をインストールした場合は、オブジェクト名を常に大文字か小文字に統一する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58101-110">If the [!INCLUDE[ssDE](../includes/ssde-md.md)] is installed as case sensitive, object names must always have the same case.</span></span> <span data-ttu-id="58101-111">たとえば、OrderData という名前のテーブルと、ORDERDATA という名前のテーブルは別のテーブルです。</span><span class="sxs-lookup"><span data-stu-id="58101-111">For example, a table named OrderData is a different table from a table named ORDERDATA.</span></span> <span data-ttu-id="58101-112">大文字と小文字を区別しないように設定して [!INCLUDE[ssDE](../includes/ssde-md.md)] をインストールした場合、この 2 つのテーブル名は同じテーブルと見なされるため、その名前は一度しか使用できません。</span><span class="sxs-lookup"><span data-stu-id="58101-112">If the [!INCLUDE[ssDE](../includes/ssde-md.md)] is installed as non-case sensitive, those two table names are considered to be the same table, and that name can only be used one time.</span></span>  
  
### <a name="to-create-a-database-to-contain-the-new-table"></a><span data-ttu-id="58101-113">新しいテーブルを含めるデータベースを作成するには</span><span class="sxs-lookup"><span data-stu-id="58101-113">To create a database to contain the new table</span></span>  
  
-   <span data-ttu-id="58101-114">クエリ エディター ウィンドウに次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="58101-114">Enter the following code into a Query Editor window.</span></span>  
  
    ```  
    USE master;  
    GO  
  
    --Delete the TestData database if it exists.  
    IF EXISTS(SELECT * from sys.databases WHERE name='TestData')  
    BEGIN  
        DROP DATABASE TestData;  
    END  
  
    --Create a new database called TestData.  
    CREATE DATABASE TestData;  
    Press the F5 key to execute the code and create the database.  
    ```  
  
### <a name="switch-the-query-editor-connection-to-the-testdata-database"></a><span data-ttu-id="58101-115">クエリ エディター接続から TestData データベースへの切り替え</span><span class="sxs-lookup"><span data-stu-id="58101-115">Switch the Query Editor connection to the TestData database</span></span>  
  
-   <span data-ttu-id="58101-116">接続を `TestData` データベースに変更するには、クエリ エディターのウィンドウで次のコードを入力して実行します。</span><span class="sxs-lookup"><span data-stu-id="58101-116">In a Query Editor window, type and execute the following code to change your connection to the `TestData` database.</span></span>  
  
    ```  
    USE TestData  
    GO  
    ```  
  
### <a name="to-create-a-table"></a><span data-ttu-id="58101-117">テーブルを作成するには</span><span class="sxs-lookup"><span data-stu-id="58101-117">To create a table</span></span>  
  
-   <span data-ttu-id="58101-118">クエリ エディターのウィンドウで、次のコードを入力して実行し、 `Products`という名前の単純なテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="58101-118">In a Query Editor window, type and execute the following code to create a simple table named `Products`.</span></span> <span data-ttu-id="58101-119">テーブルの列は `ProductID`、 `ProductName`、 `Price`、 `ProductDescription`という名前です。</span><span class="sxs-lookup"><span data-stu-id="58101-119">The columns in the table are named `ProductID`, `ProductName`, `Price`, and `ProductDescription`.</span></span> <span data-ttu-id="58101-120">`ProductID` 列がテーブルの主キーです。</span><span class="sxs-lookup"><span data-stu-id="58101-120">The `ProductID` column is the primary key of the table.</span></span> <span data-ttu-id="58101-121">`int`、 `varchar(25)`、 `money`、 `text` は、すべてデータ型です。</span><span class="sxs-lookup"><span data-stu-id="58101-121">`int`, `varchar(25)`, `money`, and `text` are all data types.</span></span> <span data-ttu-id="58101-122">行を挿入または変更するときにデータを入力しなくてもよい列は、 `Price` と `ProductionDescription` のみです。</span><span class="sxs-lookup"><span data-stu-id="58101-122">Only the `Price` and `ProductionDescription` columns can have no data when a row is inserted or changed.</span></span> <span data-ttu-id="58101-123">このステートメントには、スキーマというオプションの要素 (`dbo.`) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="58101-123">This statement contains an optional element (`dbo.`) called a schema.</span></span> <span data-ttu-id="58101-124">スキーマは、テーブルを所有するデータベース オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="58101-124">The schema is the database object that owns the table.</span></span> <span data-ttu-id="58101-125">管理者の場合は、 `dbo` が既定のスキーマです。</span><span class="sxs-lookup"><span data-stu-id="58101-125">If you are an administrator, `dbo` is the default schema.</span></span> <span data-ttu-id="58101-126">`dbo` はデータベース所有者を表します。</span><span class="sxs-lookup"><span data-stu-id="58101-126">`dbo` stands for database owner.</span></span>  
  
    ```  
    CREATE TABLE dbo.Products  
       (ProductID int PRIMARY KEY NOT NULL,  
        ProductName varchar(25) NOT NULL,  
        Price money NULL,  
        ProductDescription text NULL)  
    GO  
    ```  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="58101-127">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="58101-127">Next Task in Lesson</span></span>  
 [<span data-ttu-id="58101-128">テーブルのデータの挿入と更新 (チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="58101-128">Inserting and Updating Data in a Table &#40;Tutorial&#41;</span></span>](../t-sql/lesson-1-3-inserting-and-updating-data-in-a-table.md)  
  
## <a name="see-also"></a><span data-ttu-id="58101-129">参照</span><span class="sxs-lookup"><span data-stu-id="58101-129">See Also</span></span>  
 [<span data-ttu-id="58101-130">CREATE TABLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="58101-130">CREATE TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-table-transact-sql)  
  
  
