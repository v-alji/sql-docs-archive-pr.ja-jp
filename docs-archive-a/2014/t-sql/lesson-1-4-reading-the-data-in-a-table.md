---
title: テーブルのデータの読み取り (チュートリアル) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- reading data in a table
ms.assetid: 532232c9-3d41-45cd-9150-de67a1cbfcf5
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4bdaaeeddf8f35792c536624abfe6ff11b2dbd2e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642441"
---
# <a name="reading-the-data-in-a-table-tutorial"></a><span data-ttu-id="3d1ca-102">テーブルのデータの読み取り (チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="3d1ca-102">Reading the Data in a Table (Tutorial)</span></span>
  <span data-ttu-id="3d1ca-103">テーブルのデータを読み取るには、SELECT ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="3d1ca-103">Use the SELECT statement to read the data in a table.</span></span> <span data-ttu-id="3d1ca-104">SELECT ステートメントは最も重要な [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントの 1 つで、構文には多くのバリエーションがあります。</span><span class="sxs-lookup"><span data-stu-id="3d1ca-104">The SELECT statement is one of the most important [!INCLUDE[tsql](../includes/tsql-md.md)] statements, and there are many variations in the syntax.</span></span> <span data-ttu-id="3d1ca-105">このチュートリアルでは、5 つの単純なバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="3d1ca-105">For this tutorial, you will work with five simple versions.</span></span>  
  
### <a name="to-read-the-data-in-a-table"></a><span data-ttu-id="3d1ca-106">テーブルのデータを読み取るには</span><span class="sxs-lookup"><span data-stu-id="3d1ca-106">To read the data in a table</span></span>  
  
1.  <span data-ttu-id="3d1ca-107">次のステートメントを入力して実行し、 `Products` テーブルのデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="3d1ca-107">Type and execute the following statements to read the data in the `Products` table.</span></span>  
  
    ```  
    -- The basic syntax for reading data from a single table  
    SELECT ProductID, ProductName, Price, ProductDescription  
        FROM dbo.Products  
    GO  
  
    ```  
  
2.  <span data-ttu-id="3d1ca-108">アスタリスクを使用すると、テーブルの列をすべて選択できます。</span><span class="sxs-lookup"><span data-stu-id="3d1ca-108">You can use an asterisk to select all the columns in the table.</span></span> <span data-ttu-id="3d1ca-109">これはアドホック クエリでよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="3d1ca-109">This is often used in ad hoc queries.</span></span> <span data-ttu-id="3d1ca-110">永続的なコード内では列一覧を指定して、新しい列が後からテーブルに追加された場合でも、予測された列がステートメントによって返されるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="3d1ca-110">You should provide the column list in you permanent code so that the statement will return the predicted columns, even if a new column is added to the table later.</span></span>  
  
    ```  
    -- Returns all columns in the table  
    -- Does not use the optional schema, dbo  
    SELECT * FROM Products  
    GO  
  
    ```  
  
3.  <span data-ttu-id="3d1ca-111">返す必要のない列は省略できます。</span><span class="sxs-lookup"><span data-stu-id="3d1ca-111">You can omit columns that you do not want to return.</span></span> <span data-ttu-id="3d1ca-112">列は、一覧内の順序で返されます。</span><span class="sxs-lookup"><span data-stu-id="3d1ca-112">The columns will be returned in the order that they are listed.</span></span>  
  
    ```  
    -- Returns only two of the columns from the table  
    SELECT ProductName, Price  
        FROM dbo.Products  
    GO  
  
    ```  
  
4.  <span data-ttu-id="3d1ca-113">ユーザーに返される行を制限するには、 `WHERE` 句を使用します。</span><span class="sxs-lookup"><span data-stu-id="3d1ca-113">Use a `WHERE` clause to limit the rows that are returned to the user.</span></span>  
  
    ```  
    -- Returns only two of the records in the table  
    SELECT ProductID, ProductName, Price, ProductDescription  
        FROM dbo.Products  
        WHERE ProductID < 60  
    GO  
  
    ```  
  
5.  <span data-ttu-id="3d1ca-114">列内の値は、列が返されたときに操作できます。</span><span class="sxs-lookup"><span data-stu-id="3d1ca-114">You can work with the values in the columns as they are returned.</span></span> <span data-ttu-id="3d1ca-115">次の例では、 `Price` 列に対して数学的演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="3d1ca-115">The following example performs a mathematical operation on the `Price` column.</span></span> <span data-ttu-id="3d1ca-116">このようにして変更された列には、 `AS` キーワードを使用して名前を指定しない限り、名前が付けられません。</span><span class="sxs-lookup"><span data-stu-id="3d1ca-116">Columns that have been changed in this way will not have a name unless you provide one by using the `AS` keyword.</span></span>  
  
    ```  
    -- Returns ProductName and the Price including a 7% tax  
    -- Provides the name CustomerPays for the calculated column  
    SELECT ProductName, Price * 1.07 AS CustomerPays  
        FROM dbo.Products  
    GO  
    ```  
  
## <a name="functions-that-are-useful-in-a-select-statement"></a><span data-ttu-id="3d1ca-117">SELECT ステートメント内で役に立つ関数</span><span class="sxs-lookup"><span data-stu-id="3d1ca-117">Functions That Are Useful in a SELECT Statement</span></span>  
 <span data-ttu-id="3d1ca-118">SELECT ステートメント内のデータの操作に使用できる関数の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d1ca-118">For information about some functions that you can use to work with data in SELECT statements, see the following topics:</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="3d1ca-119">文字列関数 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3d1ca-119">String Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/string-functions-transact-sql)|[<span data-ttu-id="3d1ca-120">日付と時刻のデータ型および関数 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3d1ca-120">Date and Time Data Types and Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)|  
|[<span data-ttu-id="3d1ca-121">数学関数 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3d1ca-121">Mathematical Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/mathematical-functions-transact-sql)|[<span data-ttu-id="3d1ca-122">テキスト関数とイメージ関数 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3d1ca-122">Text and Image Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/text-and-image-functions-textptr-transact-sql)|  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="3d1ca-123">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="3d1ca-123">Next Task in Lesson</span></span>  
 [<span data-ttu-id="3d1ca-124">要約 : データベース オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="3d1ca-124">Summary: Creating Database Objects</span></span>](lesson-1-5-summary-creating-database-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="3d1ca-125">参照</span><span class="sxs-lookup"><span data-stu-id="3d1ca-125">See Also</span></span>  
 [<span data-ttu-id="3d1ca-126">SELECT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3d1ca-126">SELECT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/select-transact-sql)  
  
  
