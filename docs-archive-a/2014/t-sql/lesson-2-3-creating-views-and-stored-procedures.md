---
title: ビューとストアド プロシージャの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- creating views and stored procedures
ms.assetid: 53a0426d-07d8-4b7c-aa21-22632753bad8
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 76f6ecec446536191e8be4b05547ba5fd44c9d8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711410"
---
# <a name="creating-views-and-stored-procedures"></a><span data-ttu-id="12b8a-102">ビューとストアド プロシージャの作成</span><span class="sxs-lookup"><span data-stu-id="12b8a-102">Creating Views and Stored Procedures</span></span>
  <span data-ttu-id="12b8a-103">Mary が **TestData** データベースにアクセスできるようになったので、ビューやストアド プロシージャのようなデータベース オブジェクトを作成し、Mary にこれらのオブジェクトへのアクセス権を付与できます。</span><span class="sxs-lookup"><span data-stu-id="12b8a-103">Now that Mary can access the **TestData** database, you may want to create some database objects, such as a view and a stored procedure, and then grant Mary access to them.</span></span> <span data-ttu-id="12b8a-104">ビューは、格納された SELECT ステートメントで、ストアド プロシージャは、バッチとして実行される 1 つ以上の [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="12b8a-104">A view is a stored SELECT statement, and a stored procedure is one or more [!INCLUDE[tsql](../includes/tsql-md.md)] statements that execute as a batch.</span></span>  
  
 <span data-ttu-id="12b8a-105">ビューに対しては、テーブルと同じようにクエリが実行されます。パラメーターは使用できません。</span><span class="sxs-lookup"><span data-stu-id="12b8a-105">Views are queried like tables and do not accept parameters.</span></span> <span data-ttu-id="12b8a-106">ストアド プロシージャは、ビューよりも複雑です。</span><span class="sxs-lookup"><span data-stu-id="12b8a-106">Stored procedures are more complex than views.</span></span> <span data-ttu-id="12b8a-107">ストアド プロシージャは、入力と出力のパラメーターを指定でき、IF ステートメントや WHILE ステートメントなどの、コードの流れを制御するステートメントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="12b8a-107">Stored procedures can have both input and output parameters and can contain statements to control the flow of the code, such as IF and WHILE statements.</span></span> <span data-ttu-id="12b8a-108">データベース内でのすべての繰り返し操作には、ストアド プロシージャを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="12b8a-108">It is good programming practice to use stored procedures for all repetitive actions in the database.</span></span>  
  
 <span data-ttu-id="12b8a-109">この例では、CREATE VIEW を使用して、 **Products** テーブル内の 2 つの列だけを選択するビューを作成します。</span><span class="sxs-lookup"><span data-stu-id="12b8a-109">For this example, you will use CREATE VIEW to create a view that selects only two of the columns in the **Products** table.</span></span> <span data-ttu-id="12b8a-110">次に、CREATE PROCEDURE を使用して、価格のパラメーターを受け入れ、指定されたパラメーター値よりも価格が安い製品のみを返すストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="12b8a-110">Then, you will use CREATE PROCEDURE to create a stored procedure that accepts a price parameter and returns only those products that cost less than the specified parameter value.</span></span>  
  
### <a name="to-create-a-view"></a><span data-ttu-id="12b8a-111">ビューを作成するには</span><span class="sxs-lookup"><span data-stu-id="12b8a-111">To create a view</span></span>  
  
1.  <span data-ttu-id="12b8a-112">次のステートメントを実行して、SELECT ステートメントを実行する非常に単純なビューを作成し、製品の名前と価格をユーザーに返します。</span><span class="sxs-lookup"><span data-stu-id="12b8a-112">Execute the following statement to create a very simple view that executes a select statement, and returns the names and prices of our products to the user.</span></span>  
  
    ```  
    CREATE VIEW vw_Names  
       AS  
       SELECT ProductName, Price FROM Products;  
    GO  
  
    ```  
  
### <a name="test-the-view"></a><span data-ttu-id="12b8a-113">ビューのテスト</span><span class="sxs-lookup"><span data-stu-id="12b8a-113">Test the view</span></span>  
  
1.  <span data-ttu-id="12b8a-114">ビューはテーブルと同じように処理されます。</span><span class="sxs-lookup"><span data-stu-id="12b8a-114">Views are treated just like tables.</span></span> <span data-ttu-id="12b8a-115">ビューにアクセスするには `SELECT` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="12b8a-115">Use a `SELECT` statement to access a view.</span></span>  
  
    ```  
    SELECT * FROM vw_Names;  
    GO  
  
    ```  
  
### <a name="to-create-a-stored-procedure"></a><span data-ttu-id="12b8a-116">ストアド プロシージャを作成するには</span><span class="sxs-lookup"><span data-stu-id="12b8a-116">To create a stored procedure</span></span>  
  
1.  <span data-ttu-id="12b8a-117">次のステートメントでは、 `pr_Names`という名前のストアド プロシージャを作成し、 `@VarPrice` という名前の、 `money`データ型の入力パラメーターを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="12b8a-117">The following statement creates a stored procedure name `pr_Names`, accepts an input parameter named `@VarPrice` of data type `money`.</span></span> <span data-ttu-id="12b8a-118">このストアド プロシージャによって、 `Products less than` データ型から `money` 文字データ型に変更される入力パラメーターと連結されるステートメント `varchar(10)` が出力されます。</span><span class="sxs-lookup"><span data-stu-id="12b8a-118">The stored procedure prints the statement `Products less than` concatenated with the input parameter that is changed from the `money` data type into a `varchar(10)` character data type.</span></span> <span data-ttu-id="12b8a-119">次に、ビューに対して `SELECT` ステートメントが実行され、 `WHERE` 句の一部として入力パラメーターが渡されます。</span><span class="sxs-lookup"><span data-stu-id="12b8a-119">Then, the procedure executes a `SELECT` statement on the view, passing the input parameter as part of the `WHERE` clause.</span></span> <span data-ttu-id="12b8a-120">これによって、入力パラメーター値よりも価格が安い製品がすべて返されます。</span><span class="sxs-lookup"><span data-stu-id="12b8a-120">This returns all products that cost less than the input parameter value.</span></span>  
  
    ```  
    CREATE PROCEDURE pr_Names @VarPrice money  
       AS  
       BEGIN  
          -- The print statement returns text to the user  
          PRINT 'Products less than ' + CAST(@VarPrice AS varchar(10));  
          -- A second statement starts here  
          SELECT ProductName, Price FROM vw_Names  
                WHERE Price < @varPrice;  
       END  
    GO  
  
    ```  
  
### <a name="test-the-stored-procedure"></a><span data-ttu-id="12b8a-121">ストアド プロシージャのテスト</span><span class="sxs-lookup"><span data-stu-id="12b8a-121">Test the stored procedure</span></span>  
  
1.  <span data-ttu-id="12b8a-122">ストアド プロシージャをテストするには、次のステートメントを入力して実行します。</span><span class="sxs-lookup"><span data-stu-id="12b8a-122">To test the stored procedure, type and execute the following statement.</span></span> <span data-ttu-id="12b8a-123">このプロシージャによって、レッスン 1 で `Products` テーブルに入力した、価格が `10.00`より安い 2 つの製品の名前が返されます。</span><span class="sxs-lookup"><span data-stu-id="12b8a-123">The procedure should return the names of the two products entered into the `Products` table in Lesson 1 with a price that is less than `10.00`.</span></span>  
  
    ```  
    EXECUTE pr_Names 10.00;  
    GO  
  
    ```  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="12b8a-124">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="12b8a-124">Next Task in Lesson</span></span>  
 [<span data-ttu-id="12b8a-125">データベース オブジェクトへのアクセス権の付与</span><span class="sxs-lookup"><span data-stu-id="12b8a-125">Granting Access to a Database Object</span></span>](lesson-2-4-granting-access-to-a-database-object.md)  
  
## <a name="see-also"></a><span data-ttu-id="12b8a-126">参照</span><span class="sxs-lookup"><span data-stu-id="12b8a-126">See Also</span></span>  
 <span data-ttu-id="12b8a-127">[CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="12b8a-127">[CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) </span></span>  
 [<span data-ttu-id="12b8a-128">CREATE PROCEDURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="12b8a-128">CREATE PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-procedure-transact-sql)  
  
  
